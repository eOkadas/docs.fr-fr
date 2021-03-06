---
title: Les tailles de tableau ne peuvent pas figurer dans les spécificateurs de type
ms.date: 07/20/2015
f1_keywords:
- vbc30638
- bc30638
helpviewer_keywords:
- BC30638
ms.assetid: 93b654f4-70fa-4a48-baed-ffae42075550
ms.openlocfilehash: 951f710160ae1023671773c21c73946f5ae94c2b
ms.sourcegitcommit: 463f3f050cecc0b6403e67f19a61f870fb8e7b7d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/26/2019
ms.locfileid: "68512759"
---
# <a name="array-bounds-cannot-appear-in-type-specifiers"></a>Les tailles de tableau ne peuvent pas figurer dans les spécificateurs de type

Les tailles de tableau ne peuvent pas être déclarées dans le cadre d’un spécificateur de type de données.

**ID d’erreur:** BC30638

## <a name="to-correct-this-error"></a>Pour corriger cette erreur

- Spécifiez la taille du tableau immédiatement après le nom de la variable au lieu de placer la taille du tableau après le type, comme indiqué dans l’exemple suivant.

  ```vb
  Dim Array(8) As Integer
  ```

- Définissez un tableau et initialisez-le avec le nombre d’éléments souhaité, comme indiqué dans l’exemple suivant.

  ```vb
  Dim Array2() As Integer = New Integer(8) {}
  ```

## <a name="see-also"></a>Voir aussi

- [Tableaux](../../../visual-basic/programming-guide/language-features/arrays/index.md)
