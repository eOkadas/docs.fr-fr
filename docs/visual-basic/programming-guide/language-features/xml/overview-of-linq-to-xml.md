---
title: Vue d'ensemble de LINQ to XML dans Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ to XML [Visual Basic], about LINQ to XML
- LINQ [Visual Basic], LINQ to XML
ms.assetid: 01c62a79-6d58-468e-84fb-039c05947701
ms.openlocfilehash: 5080efdf10a8e3b1f6815e836f9fffe968a8e4e0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69939258"
---
# <a name="overview-of-linq-to-xml-in-visual-basic"></a>Vue d'ensemble de LINQ to XML dans Visual Basic
Visual Basic prend en charge [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] les littéraux XML et les propriétés d’axe XML. Cela vous permet d’utiliser une syntaxe familière et pratique pour travailler avec du code XML dans votre code Visual Basic. Les *littéraux XML* vous permettent d’inclure du code XML directement dans votre code. Les *propriétés d’axe XML* vous permettent d’accéder à des nœuds enfants, des nœuds descendants et des attributs d’un littéral XML. Pour plus d’informations, consultez [vue d’ensemble des littéraux XML](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-overview.md) et [accès à XML dans Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md).  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]est une API de programmation XML en mémoire conçue spécifiquement pour tirer parti de [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]. Bien que vous puissiez appeler [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] les API directement, seule Visual Basic vous permet de déclarer des littéraux XML et d’accéder directement aux propriétés d’axe XML.  
  
> [!NOTE]
> Les littéraux XML et les propriétés d’axe XML ne sont pas pris en charge dans le code déclaratif d’une page ASP.NET. Pour utiliser Visual Basic fonctionnalités XML, placez votre code dans une page code-behind de votre application ASP.NET.  
  
 [Bouton de lecture](./media/overview-of-linq-to-xml/play-video-icon-example.gif) Pour des démonstrations vidéo connexes, consultez [Comment prendre en main LINQ to XML?](/aspnet/web-forms/videos/data-access/linq-videos-from-the-vb-team/how-do-i-get-started-with-linq-to-xml) et [comment créer des feuilles de calcul Excel à l’aide de LINQ to XML?](/aspnet/web-forms/videos/data-access/linq-videos-from-the-vb-team/how-do-i-create-excel-spreadsheets-using-linq-to-xml).   
  
## <a name="creating-xml"></a>Création de code XML  
 Il existe deux façons de créer des arborescences XML dans Visual Basic. Vous pouvez déclarer un littéral XML directement dans le code, ou vous pouvez utiliser [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] les API pour créer l’arborescence. Les deux processus permettent au code de refléter la structure finale de l’arborescence XML. Par exemple, l’exemple de code suivant crée un élément XML:  
  
 [!code-vb[VbXmlSamples#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples2.vb#5)]  
  
 Pour plus d’informations, consultez [création de code XML dans Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md).  
  
## <a name="accessing-and-navigating-xml"></a>Accès et navigation dans XML  
 Visual Basic fournit des propriétés d’axe XML pour accéder aux structures XML et les parcourir. Ces propriétés vous permettent d’accéder aux éléments et attributs XML en spécifiant les noms d’éléments enfants XML. Vous pouvez également appeler explicitement les méthodes pour [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] naviguer et localiser les éléments et les attributs. Par exemple, l’exemple de code suivant utilise des propriétés d’axe XML pour faire référence aux attributs et aux éléments enfants d’un élément XML. L’exemple de code utilise [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] une requête pour récupérer des éléments enfants et les générer en tant qu’éléments XML, en effectuant une transformation de manière efficace.  
  
 [!code-vb[VbXmlSamples#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples3.vb#8)]  
  
 Pour plus d’informations, consultez [accès au code XML dans Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md).  
  
## <a name="xml-namespaces"></a>Espaces de noms XML  
 Visual Basic vous permet de spécifier un alias pour un espace de noms XML global à `Imports` l’aide de l’instruction. L’exemple suivant montre comment utiliser l' `Imports` instruction pour importer un espace de noms XML:  
  
 [!code-vb[VbXMLSamples#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples1.vb#1)]  
  
 Vous pouvez utiliser un alias d’espace de noms XML lorsque vous accédez à des propriétés d’axe XML et déclarez des littéraux XML pour des éléments et des documents XML.  
  
 Vous pouvez récupérer un <xref:System.Xml.Linq.XNamespace> objet pour un préfixe d’espace de noms particulier à l’aide de l' [opérateur GetXmlNamespace](../../../../visual-basic/language-reference/operators/getxmlnamespace-operator.md).  
  
 Pour plus d’informations, consultez [instructions Imports (espace de noms XML)](../../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).  
  
### <a name="using-xml-namespaces-in-xml-literals"></a>Utilisation d’espaces de noms XML dans des littéraux XML  
 L’exemple suivant montre comment créer un <xref:System.Xml.Linq.XElement> objet qui utilise l’espace de noms `ns`global:  
  
 [!code-vb[VbXMLSamples#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples1.vb#2)]  
  
 Le compilateur de Visual Basic traduit les littéraux XML qui contiennent des alias d’espaces de noms XML en code équivalent qui utilise la notation XML pour l’utilisation d’espaces `xmlns` de noms XML, avec l’attribut. Une fois compilé, le code de l’exemple de la section précédente produit essentiellement le même code exécutable que l’exemple suivant:  
  
 [!code-vb[VbXMLSamples#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples1.vb#3)]  
  
### <a name="using-xml-namespaces-in-xml-axis-properties"></a>Utilisation d’espaces de noms XML dans les propriétés d’axe XML  
 Les espaces de noms XML déclarés dans les littéraux XML ne sont pas disponibles pour une utilisation dans les propriétés d’axe XML. Toutefois, les espaces de noms globaux peuvent être utilisés avec les propriétés d’axe XML. Utilisez un signe deux-points pour séparer le préfixe d’espace de noms XML du nom de l’élément local. Vous trouverez ci-dessous un exemple :  
  
 [!code-vb[VbXMLSamples#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples1.vb#4)]  
  
## <a name="see-also"></a>Voir aussi

- [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)
- [Création de code XML dans Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [Accès au code XML dans Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)
- [Manipulation de code XML dans Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)
