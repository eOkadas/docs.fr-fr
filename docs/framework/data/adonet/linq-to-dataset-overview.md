---
title: Vue d'ensemble de LINQ to DataSet
ms.date: 03/30/2017
ms.assetid: dc20a8fb-03f6-4b68-9c2b-7f7299e3070b
ms.openlocfilehash: de49febdc81eaf4f487423c5804d1e5cc897cdce
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794966"
---
# <a name="linq-to-dataset-overview"></a>Vue d'ensemble de LINQ to DataSet
<xref:System.Data.DataSet> Est l’un des composants les plus largement utilisés de ADO.net. Il s’agit d’un élément clé du modèle de programmation déconnecté sur lequel ADO.NET est basé. il vous permet de mettre en cache explicitement les données de différentes sources de données. Pour la couche Présentation, le <xref:System.Data.DataSet> est étroitement intégré aux contrôles d’interface utilisateur graphique pour la liaison de données. Pour la couche intermédiaire, il fournit un cache qui préserve la forme relationnelle de données et inclut des services simples et rapides de requête et de navigation dans la hiérarchie. Une technique courante utilisée pour réduire le nombre de requêtes sur une base de données consiste à <xref:System.Data.DataSet> utiliser pour la mise en cache dans la couche intermédiaire. Par exemple, considérez une application Web ASP.NET pilotée par les données. En général, une partie significative des données d'application ne change pas fréquemment et est commune à plusieurs sessions ou utilisateurs. Ces données peuvent être conservées en mémoire sur le serveur web, ce qui réduit le nombre de demandes adressées à la base de données et accélère les interactions de l’utilisateur. Un autre aspect utile du <xref:System.Data.DataSet> est qu’il permet à une application de placer des sous-ensembles de données d’une ou de plusieurs sources de données dans l’espace de l’application. L'application peut alors manipuler les données en mémoire, tout en conservant sa forme relationnelle.  
  
 Cependant, en dépit de son importance, le <xref:System.Data.DataSet> a des capacités de requête limitées. La méthode <xref:System.Data.DataTable.Select%2A> peut être utilisée pour le filtrage et le tri, et les méthodes <xref:System.Data.DataRow.GetChildRows%2A> et <xref:System.Data.DataRow.GetParentRow%2A> pour la navigation dans la hiérarchie. Pour toute opération plus complexe, cependant, le développeur doit écrire une requête personnalisée. Cela peut entraîner un dysfonctionnement des applications et les rendre difficiles à gérer.  
  
 LINQ to DataSet facilite et accélère l’interrogation de données mises en cache dans un <xref:System.Data.DataSet> objet. Ces requêtes sont exprimées dans le langage de programmation même, plutôt qu'en tant que littéraux de chaîne incorporés dans le code de l'application. Ainsi, les développeurs n'ont pas à apprendre de langage de requête spécifique. En outre, LINQ to DataSet permet aux développeurs Visual Studio de travailler de manière plus productive, car l’IDE de Visual Studio fournit la vérification de la syntaxe au moment de la compilation [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)], le typage statique et la prise en charge IntelliSense pour. LINQ to DataSet peut également être utilisé pour interroger des données qui ont été consolidées à partir d’une ou de plusieurs sources de données. Cela permet de réaliser plusieurs scénarios qui requièrent de la flexibilité dans la façon dont les données sont représentées et gérées. En particulier, les applications génériques de création de rapports, d'analyse et de business intelligence requièrent cette méthode de manipulation.  
  
## <a name="querying-datasets-using-linq-to-dataset"></a>Interrogation de DataSets à l'aide de LINQ to DataSet  
 Avant de pouvoir commencer à interroger <xref:System.Data.DataSet> un objet à l’aide de LINQ to DataSet, <xref:System.Data.DataSet>vous devez remplir le. Il existe plusieurs façons de charger des données dans <xref:System.Data.DataSet>un, par exemple à <xref:System.Data.Common.DataAdapter> l’aide de la classe ou [LINQ to SQL](./sql/linq/index.md). Une fois que les données ont été chargées dans un <xref:System.Data.DataSet> objet, vous pouvez commencer à les interroger. La formulation de requêtes à l’aide de [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] LINQ to DataSet est [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]semblable à l’utilisation de sur d’autres sources de données compatibles. [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]les <xref:System.Data.DataSet> <xref:System.Linq.Enumerable.GroupJoin%2A> requêtes peuvent être exécutées sur des tables uniques d’un ou sur plusieurs tables à l’aide des opérateurs de requête standard et. <xref:System.Linq.Enumerable.Join%2A>  
  
 [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]les requêtes sont prises en charge pour les <xref:System.Data.DataSet> objets typés et non typés. Si le schéma du <xref:System.Data.DataSet> est connu au moment du design de l'application, nous vous recommandons d'utiliser un <xref:System.Data.DataSet> typé. Dans un <xref:System.Data.DataSet>, les tables et lignes ont des membres typés pour chaque colonne, ce qui rend les requêtes plus simples et plus lisibles.  
  
 En plus des opérateurs de requête standard implémentés dans System. Core. dll, LINQ to DataSet ajoute <xref:System.Data.DataSet>plusieurs extensions spécifiques qui facilitent l’interrogation d’un ensemble d' <xref:System.Data.DataRow> objets. Ces extensions spécifiques à <xref:System.Data.DataSet> incluent des opérateurs pour comparer des séquences de lignes, ainsi que des méthodes qui fournissent l'accès aux valeurs de colonne d'un <xref:System.Data.DataRow>.  
  
## <a name="n-tier-applications-and-linq-to-dataset"></a>Applications multicouches et LINQ to DataSet  
 Les applications de données multicouches sont des applications centrées sur les données qui sont étagées en plusieurs couches logiques. Une application multicouche classique inclut une couche Présentation, une couche intermédiaire et une couche Données. La séparation des composants d'application en couches distinctes renforce la facilité de maintenance et l'évolutivité de l'application. Pour plus d’informations sur les applications de données multicouches, consultez [utiliser des jeux de données dans des applications multicouches](/visualstudio/data-tools/work-with-datasets-in-n-tier-applications).  
  
 Dans les applications multicouches, le <xref:System.Data.DataSet> est souvent utilisé dans la couche intermédiaire pour mettre en cache les informations pour une application Web. La fonctionnalité d’interrogation de LINQ to DataSet est implémentée à l’aide de méthodes d' <xref:System.Data.DataSet>extension et étend le ADO.NET 2,0 existant.  
  
## <a name="see-also"></a>Voir aussi

- [Interrogation de DataSets](querying-datasets-linq-to-dataset.md)
- [LINQ (Language-Integrated Query) - C#](../../../csharp/programming-guide/concepts/linq/index.md)
- [LINQ (Language-Integrated Query) - Visual Basic](../../../visual-basic/programming-guide/concepts/linq/index.md)
- [LINQ to SQL](./sql/linq/index.md)
