---
title: terminaison d'association
ms.date: 03/30/2017
ms.assetid: 2c345213-0296-4d90-ac6d-cef179798a75
ms.openlocfilehash: 33cc2e10d9b72ef7f5f024905938c41fcc4a9755
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785042"
---
# <a name="association-end"></a>terminaison d'association
Une *terminaison d’association* identifie le [type d’entité](entity-type.md) sur une terminaison d’une [Association](association-type.md) et le nombre d’instances de type d’entité qui peuvent exister à cette terminaison d’une association. Les terminaisons d'association sont définies dans le cadre d'une association ; une association doit avoir exactement deux terminaisons d'association. Les [Propriétés de navigation](navigation-property.md) permettent de naviguer d’une terminaison d’association à l’autre.  
  
 Une définition de terminaison d'association contient les informations suivantes :  
  
- Un des types d'entité impliqués dans l'association. (Requis)  
  
    > [!NOTE]
    > Pour une association donnée, le type d'entité spécifié pour chaque terminaison d'association peut être le même. Ceci crée une association automatique.  
  
- [Multiplicité de terminaison d’association](association-end-multiplicity.md) qui indique le nombre d’instances de type d’entité qui peuvent être à une terminaison de l’Association. Une multiplicité de terminaison d’association peut avoir la valeur un (1), zéro ou un (0.. 1), ou plusieurs (\*).  
  
- Nom de la terminaison de l'association. (facultatif)  
  
- Informations sur les opérations effectuées sur la terminaison d'association, telles que CASCADE sur DELETE. (facultatif)  
  
## <a name="example"></a>Exemple  
 Le diagramme suivant montre un modèle conceptuel avec deux associations : `PublishedBy` et `WrittenBy`. Les terminaisons d'association pour l'association `PublishedBy` sont les types d'entité `Book` et `Publisher`. La multiplicité de la `Publisher` terminaison est un (1) et la multiplicité de la `Book` terminaison est plusieurs (\*), ce qui indique qu’un éditeur publie de nombreux livres et qu’un livre est publié par un serveur de publication.  
  
 ![Exemple de modèle avec trois types d’entité](./media/association-end/example-model-three-entity-types.gif)  
  
 Le Entity Framework ADO.NET utilise un langage spécifique à un domaine (DSL) appelé Conceptual Schema Definition Language ([CSDL](./ef/language-reference/csdl-specification.md)) pour définir des modèles conceptuels. Le CSDL suivant définit l'association `PublishedBy` présentée dans le diagramme ci-dessus. Notez que le type, le nom et la multiplicité de chaque terminaison d'association sont spécifiés par des attributs XML (`Type`, `Role` et `Multiplicity`, respectivement). Des informations facultatives sur les opérations effectuées sur une terminaison sont spécifiées dans un élément XML (`OnDelete`). Dans ce cas, si un éditeur est supprimé, tous les livres associés le sont aussi.  
  
 [!code-xml[EDM_Example_Model#AssociationEnd](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books3.edmx#associationend)]  
  
## <a name="see-also"></a>Voir aussi

- [Concepts clés d’Entity Data Model](entity-data-model-key-concepts.md)
- [Entity Data Model](entity-data-model.md)
