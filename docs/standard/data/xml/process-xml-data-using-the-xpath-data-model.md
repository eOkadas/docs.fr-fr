---
title: Traitement des données XML à l’aide du modèle de données XPath
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 536c6fce-1453-4654-9c72-bca54d47e081
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 67fbacd24b888b9c45072bcb34031f38adc118e3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54728396"
---
# <a name="process-xml-data-using-the-xpath-data-model"></a>Traitement des données XML à l’aide du modèle de données XPath
L'espace de noms <xref:System.Xml?displayProperty=nameWithType> offre une représentation par programme de documents XML, de fragments, de nœuds ou de collections de nœuds en mémoire à l'aide des classes <xref:System.Xml.XmlDocument> ou <xref:System.Xml.XPath.XPathDocument>.  
  
 La classe <xref:System.Xml.XPath.XPathDocument> fournit une représentation rapide, en lecture seule et en mémoire d’un document XML à l’aide du modèle de données XPath. La classe <xref:System.Xml.XmlDocument> offre une représentation en mémoire modifiable d'un document XML qui implémente les recommandations du W3C sur les modèles objet de document (DOM) niveaux 1 et 2 (noyau). Les deux classes implémentent l'interface <xref:System.Xml.XPath.IXPathNavigable> et retournent un objet <xref:System.Xml.XPath.XPathNavigator> utilisé pour sélectionner, évaluer, parcourir et, dans certains cas, modifier les données XML sous-jacentes.  
  
 Les sections suivantes décrivent les fonctionnalités de la classe <xref:System.Xml.XPath.XPathNavigator> en fonction de la classe qui la retourne.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Lecture de données XML à l’aide de XPathDocument et XmlDocument](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md)  
 Décrit comment créer un objet de classe <xref:System.Xml.XPath.XPathDocument> en lecture seule pour lire un document XML et un objet de classe <xref:System.Xml.XmlDocument> modifiable pour lire et modifier un document XML. Cette rubrique décrit également comment retourner un objet <xref:System.Xml.XPath.XPathNavigator> de chaque classe pour parcourir et modifier un document XML.  
  
 [Sélection, évaluation et mise en correspondance de données XML à l’aide de XPathNavigator](../../../../docs/standard/data/xml/selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md)  
 Décrit les méthodes de la classe <xref:System.Xml.XPath.XPathNavigator> utilisées pour sélectionner des nœuds dans un objet <xref:System.Xml.XPath.XPathDocument> ou <xref:System.Xml.XmlDocument> à l’aide de la requête XPath, pour évaluer et examiner les résultats d’une expression XPath et pour déterminer si un nœud d’un document XML correspond à une expression XPath donnée.  
  
 [Accès à des données XML à l’aide de XPathNavigator](../../../../docs/standard/data/xml/accessing-xml-data-using-xpathnavigator.md)  
 Décrit les méthodes de la classe <xref:System.Xml.XPath.XPathNavigator> utilisées pour parcourir des nœuds, extraire des données XML et accéder à des données XML fortement typées dans un objet <xref:System.Xml.XPath.XPathDocument> ou <xref:System.Xml.XmlDocument>.  
  
 [Modification de données XML à l’aide de XPathNavigator](../../../../docs/standard/data/xml/editing-xml-data-using-xpathnavigator.md)  
 Décrit les méthodes de la classe <xref:System.Xml.XPath.XPathNavigator> utilisées pour insérer, modifier et supprimer des nœuds et des valeurs d'un document XML contenu dans un objet <xref:System.Xml.XmlDocument>.  
  
 [Validation de schéma à l’aide de XPathNavigator](../../../../docs/standard/data/xml/schema-validation-using-xpathnavigator.md)  
 Décrit les méthodes de validation du contenu XML d'un objet <xref:System.Xml.XPath.XPathDocument> ou <xref:System.Xml.XmlDocument>.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [Traitement de données XML à l’aide du modèle DOM](../../../../docs/standard/data/xml/process-xml-data-using-the-dom-model.md)
