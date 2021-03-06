---
title: Requêtes dans LINQ to Entities
ms.date: 03/30/2017
ms.assetid: c015a609-29eb-4e95-abb1-2ca721c6e2ad
ms.openlocfilehash: 561fa3217a80a8437b7c4d175d5a1156096ac241
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249557"
---
# <a name="queries-in-linq-to-entities"></a>Requêtes dans LINQ to Entities
Une requête est une expression qui récupère des données d'une source de données. En général, les requêtes sont exprimées dans un langage de requête spécialisé, tel que SQL pour les bases de données relationnelles et Xquery pour XML. Par conséquent, les développeurs ont dû apprendre un nouveau langage de requête pour chaque type de source de données ou format de données qu'ils interrogent. LINQ (Language-Integrated Query) propose un modèle cohérent plus simple qui permet d'utiliser des données de types de sources et de formats divers. Dans une requête LINQ, vous travaillez toujours avec des objets de programmation.  
  
 Une opération de requête LINQ se compose de trois actions : obtenir la ou les sources de données, créer la requête, puis exécuter cette dernière.  
  
 Les sources de données qui implémentent l'interface générique <xref:System.Collections.Generic.IEnumerable%601> ou l'interface générique <xref:System.Linq.IQueryable%601> peuvent être interrogées via LINQ. Les instances de la <xref:System.Data.Objects.ObjectQuery%601> classe générique, qui implémente l' <xref:System.Linq.IQueryable%601> interface générique, servent de source de données pour les requêtes de LINQ to Entities. La classe générique <xref:System.Data.Objects.ObjectQuery%601> représente une requête qui retourne une collection de zéro, un ou plusieurs objets typés. Vous pouvez également laisser le compilateur déduire le type d’une entité à l' C# aide `var` du mot clé (Dim dans Visual Basic).  
  
 Dans la requête, vous spécifiez exactement les informations que vous voulez récupérer à partir de la source de données. Une requête peut également spécifier la manière dont ces informations doivent être triées, regroupées et mises en forme avant d'être retournées. Dans LINQ, une requête est stockée dans une variable. Si la requête retourne une séquence de valeurs, la variable de requête doit elle-même être de type requêtable. Cette variable de requête n'effectue aucune action et ne retourne aucune donnée ; elle stocke uniquement les informations de requête. Une fois que vous avez créé une requête, vous devez l'exécuter pour extraire des données.  
  
## <a name="query-syntax"></a>Syntaxe de requête  
 Les requêtes LINQ to Entities peuvent être composées dans deux syntaxes différentes : la syntaxe d'expression de requête et la syntaxe de requête fondée sur une méthode. La syntaxe d’expression de requête C# est nouvelle dans 3,0 et Visual Basic 9,0, et elle se compose d’un ensemble de clauses écrites dans une syntaxe déclarative similaire à Transact-SQL ou XQuery. Toutefois, le .NET Framework common language runtime (CLR) ne peut pas lire la syntaxe de l’expression de requête proprement dite. Par conséquent, au moment de la compilation, les expressions de requête sont traduites en appels de méthodes pour que le CLR puisse les comprendre. Ces méthodes sont appelées *opérateurs de requête standard*. En tant que développeur, vous pouvez les appeler directement en utilisant la syntaxe de méthode plutôt que la syntaxe de requête. Pour plus d’informations, consultez [Syntaxe de requête et syntaxe de méthode dans LINQ](../../../../../csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md).  
  
### <a name="query-expression-syntax"></a>Syntaxe d'expression de requête  
 Les expressions de requête utilisent une syntaxe de requête déclarative. Cette syntaxe permet au développeur d'écrire des requêtes dans un langage de haut niveau formaté de façon similaire à Transact-SQL. En utilisant la syntaxe d'expression de requête, vous pouvez même effectuer des opérations de filtrage, de classement et de regroupement complexes sur des sources de données avec un minimum de code. Pour plus d’informations, les [opérations de requête de base (Visual Basic)](../../../../../visual-basic/programming-guide/concepts/linq/basic-query-operations.md). Pour obtenir des exemples d'utilisation de la syntaxe d'expression de requête, consultez les rubriques suivantes :  
  
- [Exemples de syntaxe d’expression de requête : Projection](query-expression-syntax-examples-projection.md)  
  
- [Exemples de syntaxe d’expression de requête : Filtration](query-expression-syntax-examples-filtering.md)  
  
- [Exemples de syntaxe d’expression de requête : Commandé](query-expression-syntax-examples-ordering.md)  
  
- [Exemples de syntaxe d’expression de requête : Opérateurs d’agrégation](query-expression-syntax-examples-aggregate-operators.md)  
  
- [Exemples de syntaxe d’expression de requête : Partitionnement](query-expression-syntax-examples-partitioning.md)  
  
- [Exemples de syntaxe d’expression de requête : Opérateurs de jointure](query-expression-syntax-examples-join-operators.md)  
  
- [Exemples de syntaxe d’expression de requête : Opérateurs d’élément](query-expression-syntax-examples-element-operators.md)  
  
- [Exemples de syntaxe d’expression de requête : Regroupement](query-expression-syntax-examples-grouping.md)  
  
- [Exemples de syntaxe d’expression de requête : Navigation dans les relations](query-expression-syntax-examples-navigating-relationships.md)  
  
### <a name="method-based-query-syntax"></a>Syntaxe de requête fondée sur une méthode  
 Une autre façon de composer des LINQ to Entities des requêtes consiste à utiliser des requêtes basées sur une méthode. La syntaxe de requête fondée sur une méthode est une séquence d’appels de méthode directe aux méthodes d’opérateur LINQ, passant des expressions lambda comme paramètres. Pour plus d’informations, consultez [Expressions lambda](../../../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md). Pour obtenir des exemples d'utilisation de la syntaxe fondée sur une méthode, consultez les rubriques suivantes :  
  
- [Exemples de syntaxe de requête fondée sur une méthode : Projection](method-based-query-syntax-examples-projection.md)  
  
- [Exemples de syntaxe de requête fondée sur une méthode : Filtration](method-based-query-syntax-examples-filtering.md)  
  
- [Exemples de syntaxe de requête fondée sur une méthode : Commandé](method-based-query-syntax-examples-ordering.md)  
  
- [Exemples de syntaxe de requête fondée sur une méthode : Opérateurs d’agrégation](method-based-query-syntax-examples-aggregate-operators.md)  
  
- [Exemples de syntaxe de requête fondée sur une méthode : Partitionnement](method-based-query-syntax-examples-partitioning.md)  
  
- [Exemples de syntaxe de requête fondée sur une méthode : Convertisseur](method-based-query-syntax-examples-conversion.md)  
  
- [Exemples de syntaxe de requête fondée sur une méthode : Opérateurs de jointure](method-based-query-syntax-examples-join-operators.md)  
  
- [Exemples de syntaxe de requête fondée sur une méthode : Opérateurs d’élément](method-based-query-syntax-examples-element-operators.md)  
  
- [Exemples de syntaxe de requête fondée sur une méthode : Regroupement](method-based-query-syntax-examples-grouping.md)  
  
- [Exemples de syntaxe de requête fondée sur une méthode : Navigation dans les relations](method-based-query-syntax-examples-navigating-relationships.md)  
  
## <a name="see-also"></a>Voir aussi

- [LINQ to Entities](linq-to-entities.md)
- [Bien démarrer avec LINQ en C#](../../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)
- [Bien démarrer avec LINQ en Visual Basic](../../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)
- [Entity Framework les options de fusion et les requêtes compilées](https://go.microsoft.com/fwlink/?LinkId=199591)
