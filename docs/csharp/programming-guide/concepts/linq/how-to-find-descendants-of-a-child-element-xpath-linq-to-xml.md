---
title: 'Procédure : Rechercher les descendants d’un élément enfant (XPath-LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: 505b7512-bb8b-4f85-abbf-491f039c961e
ms.openlocfilehash: f17d723aa03c45daa4e7e741ea6b14c637537ccf
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253700"
---
# <a name="how-to-find-descendants-of-a-child-element-xpath-linq-to-xml-c"></a>Procédure : Rechercher les descendants d’un élément enfant (XPath-LINQ to XML) (C#)
Cette rubrique montre comment obtenir les éléments descendants d'un élément enfant avec un nom particulier.  
  
 L’expression XPath est la suivante :  
  
 `./Paragraph//Text/text()`  
  
## <a name="example"></a>Exemple  
 Cet exemple simule les problèmes d'extraction de texte à partir d'une représentation XML d'un document de traitement de texte. Il sélectionne tout d'abord tous les éléments `Paragraph`, puis il sélectionne tous les éléments descendants `Text` de chaque élément `Paragraph`. Il ne sélectionne pas `Text`les éléments descendants de`Comment` l'élément.  
  
```csharp  
XElement root = XElement.Parse(  
@"<Root>  
  <Paragraph>  
    <Text>This is the start of</Text>  
  </Paragraph>  
  <Comment>  
    <Text>This comment is not part of the paragraph text.</Text>  
  </Comment>  
  <Paragraph>  
    <Annotation Emphasis='true'>  
      <Text> a sentence.</Text>  
    </Annotation>  
  </Paragraph>  
  <Paragraph>  
    <Text>  This is a second sentence.</Text>  
  </Paragraph>  
</Root>");  
  
// LINQ to XML query  
string str1 =  
    root  
    .Elements("Paragraph")  
    .Descendants("Text")  
    .Select(s => s.Value)  
    .Aggregate(  
        new StringBuilder(),  
        (s, i) => s.Append(i),  
        s => s.ToString()  
    );  
  
// XPath expression  
string str2 =  
    ((IEnumerable)root.XPathEvaluate("./Paragraph//Text/text()"))  
    .Cast<XText>()  
    .Select(s => s.Value)  
    .Aggregate(  
        new StringBuilder(),  
        (s, i) => s.Append(i),  
        s => s.ToString()  
    );  
  
if (str1 == str2)  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
Console.WriteLine(str2);  
```  
  
 Cet exemple génère la sortie suivante :  
  
```output  
Results are identical  
This is the start of a sentence.  This is a second sentence.  
```  
  