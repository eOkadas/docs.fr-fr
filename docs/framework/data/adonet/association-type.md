---
title: type d'association
ms.date: 03/30/2017
ms.assetid: 26c409f6-06e8-4441-ac78-1b1076a3c005
ms.openlocfilehash: e75037223b235cf09df0bca85c6a4feb0b340174
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786893"
---
# <a name="association-type"></a>type d'association
Un *type d’association* (également appelé Association) est le bloc de construction fondamental pour la description des relations dans le modèle EDM (Entity Data Model). Dans un modèle conceptuel, une association représente une relation entre deux [types d’entité](entity-type.md) (tels `Customer` que `Order`et). Dans une application, une instance d'une association représente une association spécifique (comme une association entre une instance de `Customer` et une instance d'`Order`). Les instances d’association sont regroupées logiquement dans un [ensemble d’associations](association-set.md).  
  
 Une définition d'association contient les informations suivantes :  
  
- Nom unique. (Requis)  
  
- Deux [terminaisons d’association](association-end.md), une pour chaque type d’entité dans la relation. (Requis)  
  
    > [!NOTE]
    > Une association ne peut pas représenter de relation entre plus de deux types d'entité. Toutefois, une association peut définir une relation réciproque en spécifiant le même type d'entité pour chacune de ses terminaisons d'association.  
  
- [Contrainte d’intégrité référentielle](referential-integrity-constraint.md). (facultatif)  
  
 Chaque terminaison d’association doit spécifier une [multiplicité de terminaison d’association](association-end-multiplicity.md) qui indique le nombre d’instances de type d’entité qui peuvent être à une terminaison de l’Association. Une multiplicité de terminaison d’association peut avoir la valeur un (1), zéro ou un (0.. 1), ou plusieurs (\*). Les instances de type d’entité à une terminaison d’une association sont accessibles via les [Propriétés de navigation](navigation-property.md) ou les clés étrangères si elles sont exposées sur un type d’entité. Pour plus d’informations, [consultez Entity Data Model : Clés](foreign-key-property.md)étrangères.  
  
## <a name="example"></a>Exemples  
 Le diagramme suivant montre un modèle conceptuel avec deux associations : `PublishedBy` et `WrittenBy`. Les terminaisons d'association pour l'association `PublishedBy` sont les types d'entité `Book` et `Publisher`. La multiplicité de la `Publisher` terminaison est un (1) et la multiplicité de la `Book` terminaison est plusieurs (\*), ce qui indique qu’un éditeur publie de nombreux livres et qu’un livre est publié par un serveur de publication.  
  
 ![Exemple de modèle avec trois types d’entité](./media/association-type/example-model-three-entity-types.gif)  
  
 Le [Entity Framework ADO.net](./ef/index.md) utilise un langage spécifique à un domaine (DSL) appelé Conceptual Schema Definition Language ([CSDL](./ef/language-reference/csdl-specification.md)) pour définir des modèles conceptuels. Le CSDL suivant définit l'association `PublishedBy` présentée dans le diagramme ci-dessus :  
  
 [!code-xml[EDM_Example_Model#AssociationExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#associationexample)]  
  
## <a name="see-also"></a>Voir aussi

- [Concepts clés d’Entity Data Model](entity-data-model-key-concepts.md)
- [Entity Data Model](entity-data-model.md)
