---
title: Niveaux d’accessibilité - Référence C#
ms.custom: seodec18
ms.date: 12/06/2017
helpviewer_keywords:
- access modifiers [C#], accessibility levels
- accessibility levels
ms.assetid: dc083921-0073-413e-8936-a613e8bb7df4
ms.openlocfilehash: 2d6605a305e5003e19f4fe1dd260746302691215
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602389"
---
# <a name="accessibility-levels-c-reference"></a>Niveaux d’accessibilité (référence C#)

Utilisez les modificateurs d’accès `public`, `protected`, `internal` ou `private` pour spécifier l’un des niveaux d’accessibilité déclarés ci-dessous pour les membres.  
  
|Accessibilité déclarée|Signification|  
|----------------------------|-------------|  
|[`public`](public.md)|L’accès n’est pas limité.|  
|[`protected`](protected.md)|L’accès est limité à la classe conteneur ou aux types dérivés de la classe conteneur.|  
|[`internal`](internal.md)|L’accès est limité à l’assembly actuel.|  
|[`protected internal`](protected-internal.md)|L’accès est limité à l’assembly actuel ou aux types dérivés de la classe conteneur.|  
|[`private`](private.md)|L’accès est limité au type conteneur.|  
|[`private protected`](private-protected.md)|L’accès est limité à la classe conteneur ou aux types dérivés de la classe conteneur dans l’assembly actuel. Disponible depuis C# 7.2. |  
  
 Vous ne pouvez spécifier qu’un seul modificateur d’accès pour un membre ou un type, sauf si vous utilisez les combinaisons `protected internal` ou `private protected`.  
  
 Les modificateurs d’accès ne sont pas autorisés sur les espaces de noms. Les espaces de noms ne présentent aucune limitation d’accès.  
  
 Selon le contexte dans lequel une déclaration de membre est effectuée, seules certaines accessibilités déclarées sont autorisées. Si aucun modificateur d’accès n’est spécifié dans une déclaration de membre, une accessibilité par défaut est utilisée.  
  
 Les types de premier niveau, qui ne sont pas imbriqués dans d’autres types, peuvent uniquement avoir une accessibilité `internal` ou `public`. L’accessibilité par défaut de ces types est `internal`.  
  
 Les types imbriqués, qui sont membres d’autres types, peuvent avoir les accessibilités déclarées indiquées dans le tableau suivant.  
  
|Membres de|Accessibilité par défaut du membre|Accessibilité déclarée du membre autorisée|  
|----------------|----------------------------------|--------------------------------------------------|  
|`enum`|`public`|Aucun.|  
|`class`|`private`|`public`<br /><br /> `protected`<br /><br /> `internal`<br /><br /> `private`<br /><br /> `protected internal` <br /><br />`private protected`|  
|`interface`|`public`|Aucun.|  
|`struct`|`private`|`public`<br /><br /> `internal`<br /><br /> `private`|  
  
 L’accessibilité d’un type imbriqué dépend de son [domaine d’accessibilité](./accessibility-domain.md), qui est déterminé à la fois par l’accessibilité déclarée du membre et par le domaine d’accessibilité du type conteneur immédiat. Toutefois, le domaine d'accessibilité d'un type imbriqué ne peut pas dépasser celui du type conteneur.  
  
## <a name="c-language-specification"></a>Spécification du langage C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Référence C#](../index.md)
- [Guide de programmation C#](../../programming-guide/index.md)
- [Mots clés C#](./index.md)
- [Modificateurs d’accès](./access-modifiers.md)
- [Domaine d’accessibilité](./accessibility-domain.md)
- [Limitations sur l’utilisation des niveaux d’accessibilité](./restrictions-on-using-accessibility-levels.md)
- [Modificateurs d’accès](../../programming-guide/classes-and-structs/access-modifiers.md)
- [public](./public.md)
- [private](./private.md)
- [protected](./protected.md)
- [internal](./internal.md)
