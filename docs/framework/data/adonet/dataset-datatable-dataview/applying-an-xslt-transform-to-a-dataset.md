---
title: Application d'une transformation XSLT à un DataSet
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 09f2e4ee-1d08-4ba8-8936-83394fee319d
ms.openlocfilehash: d9767844400d67e81c7065148b22c62352af0428
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784787"
---
# <a name="applying-an-xslt-transform-to-a-dataset"></a>Application d'une transformation XSLT à un DataSet
La méthode **WriteXml** de <xref:System.Data.DataSet> vous permet d’écrire le contenu d’un **DataSet** sous forme de données XML. La tâche qui suit généralement consiste à transformer ce XML en un autre format à l'aide de transformations XSL (XSLT). Toutefois, la synchronisation d’un DataSet <xref:System.Xml.XmlDataDocument> avec un objet vous permet d’appliquer une feuille de style XSLT au contenu d’un **DataSet** sans avoir à écrire d’abord le contenu du **DataSet** sous forme de données XML à l’aide de **WriteXml**.  
  
 L’exemple suivant remplit un **DataSet** avec des tables et des relations, synchronise le **DataSet** avec un **XmlDataDocument**, puis écrit une partie du **DataSet** sous la forme d’un fichier HTML à l’aide d’une feuille de style XSLT. Le contenu de la feuille de style XSLT vous est présenté ci-après.  
  
```xml  
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">  
  
<xsl:template match="CustomerOrders">  
  <HTML>  
  <STYLE>  
  BODY {font-family:verdana;font-size:9pt}  
  TD   {font-size:8pt}  
  </STYLE>  
    <BODY>  
    <TABLE BORDER="1">  
      <xsl:apply-templates select="Customers"/>  
    </TABLE>  
    </BODY>  
  </HTML>  
</xsl:template>  
  
<xsl:template match="Customers">  
    <TR><TD>  
      <xsl:value-of select="ContactName"/>, <xsl:value-of select="Phone"/><BR/>  
    </TD></TR>  
      <xsl:apply-templates select="Orders"/>  
</xsl:template>  
  
<xsl:template match="Orders">  
  <TABLE BORDER="1">  
    <TR><TD valign="top"><B>Order:</B></TD><TD valign="top"><xsl:value-of select="OrderID"/></TD></TR>  
    <TR><TD valign="top"><B>Date:</B></TD><TD valign="top"><xsl:value-of select="OrderDate"/></TD></TR>  
    <TR><TD valign="top"><B>Ship To:</B></TD>  
        <TD valign="top"><xsl:value-of select="ShipName"/><BR/>  
        <xsl:value-of select="ShipAddress"/><BR/>  
        <xsl:value-of select="ShipCity"/>, <xsl:value-of select="ShipRegion"/>  <xsl:value-of select="ShipPostalCode"/><BR/>  
        <xsl:value-of select="ShipCountry"/></TD></TR>  
  </TABLE>  
</xsl:template>  
  
</xsl:stylesheet>  
```  
  
 Le code suivant remplit le **DataSet** et applique la feuille de style XSLT.  
  
> [!NOTE]
> Si vous appliquez une feuille de style XSLT à un **jeu de données** qui contient des relations, vous obtiendrez de meilleures performances si vous affectez <xref:System.Data.DataRelation> la valeur **true** à la propriété **Nested** de chaque relation imbriquée. Cela vous permet d'utiliser les feuilles de style XSLT qui implémentent un traitement naturel vertical pour naviguer dans la hiérarchie et transformer les données, au lieu de recourir aux axes de localisation XPath exigeants en performances (par exemple, frère précédent et frère suivant dans les expressions de test de nœud de feuille de style) pour y naviguer. Pour plus d’informations sur les relations imbriquées, consultez [imbrication de DataRelations](nesting-datarelations.md).  
  
```vb  
' Assumes connection is a valid SqlConnection.  
Dim dataSet As DataSet = New DataSet("CustomerOrders")  
  
Dim customerAdapter As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT * FROM Customers", connection)  
customerAdapter.Fill(dataSet, "Customers")  
  
Dim orderAdapter As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT * FROM Orders", connection)  
orderAdapter.Fill(dataSet, "Orders")  
  
connection.Close()  
  
dataSet.Relations.Add("CustOrders", _  
dataSet.Tables("Customers").Columns("CustomerID"), _  
dataSet.Tables("Orders").Columns("CustomerID")).Nested = true  
  
Dim xmlDoc As XmlDataDocument = New XmlDataDocument(dataSet)   
  
Dim xslTran As XslTransform = New XslTransform  
xslTran.Load("transform.xsl")  
  
Dim writer As XmlTextWriter = New XmlTextWriter( _  
  "xslt_output.html", System.Text.Encoding.UTF8)  
  
xslTran.Transform(xmlDoc, Nothing, writer)  
writer.Close()  
```  
  
```csharp  
// Assumes connection is a valid SqlConnection.  
connection.Open();  
  
DataSet custDS = new DataSet("CustomerDataSet");  
  
SqlDataAdapter customerAdapter = new SqlDataAdapter(  
  "SELECT * FROM Customers", connection);  
customerAdapter.Fill(custDS, "Customers");  
  
SqlDataAdapter orderAdapter = new SqlDataAdapter(  
  "SELECT * FROM Orders", connection);  
orderAdapter.Fill(custDS, "Orders");  
  
connection.Close();  
  
custDS.Relations.Add("CustOrders",  
  custDS.Tables["Customers"].Columns["CustomerID"],  
                     custDS.Tables["Orders"].Columns["CustomerID"]).Nested = true;  
  
XmlDataDocument xmlDoc = new XmlDataDocument(custDS);   
  
XslTransform xslTran = new XslTransform();  
xslTran.Load("transform.xsl");  
  
XmlTextWriter writer = new XmlTextWriter("xslt_output.html",   
  System.Text.Encoding.UTF8);  
  
xslTran.Transform(xmlDoc, null, writer);  
writer.Close();  
```  
  
## <a name="see-also"></a>Voir aussi

- [Synchronisation DataSet et XmlDataDocument](dataset-and-xmldatadocument-synchronization.md)
- [Vue d’ensemble d’ADO.NET](../ado-net-overview.md)
