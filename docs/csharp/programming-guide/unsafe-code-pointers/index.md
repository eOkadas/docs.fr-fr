---
title: Pointeurs et code unsafe - Guide de programmation C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- security [C#], type safety
- C# language, unsafe code
- type safety [C#]
- unsafe keyword [C#]
- unsafe code [C#]
- C# language, pointers
- pointers [C#], about pointers
ms.assetid: b0fcca10-a92d-4f2a-835b-b0ccae6739ee
ms.openlocfilehash: 99f0b925a37bff8b6ab1ff46e9ce2f0ea0a38aed
ms.sourcegitcommit: ffd7dd79468a81bbb0d6449f6d65513e050c04c4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/21/2019
ms.locfileid: "65959481"
---
# <a name="unsafe-code-and-pointers-c-programming-guide"></a>Pointeurs et code unsafe (Guide de programmation C#)

Pour conserver la sécurité des types, par défaut, C# ne prend pas en charge les opérations arithmétiques sur les pointeurs. Cependant, en utilisant le mot clé [unsafe](../../language-reference/keywords/unsafe.md), vous pouvez définir un contexte non sécurisé dans lequel des pointeurs peuvent être utilisés. Pour en savoir plus sur les pointeurs, consultez la rubrique [Types de pointeur](pointer-types.md).  
  
> [!NOTE]
> Dans le common language runtime (CLR), le code non sécurisé est appelé « code non vérifiable ». Le code non sécurisé en C# n’est pas nécessairement dangereux : il s’agit simplement de code dont la sécurité ne peut pas être vérifiée par le CLR. Le CLR exécute du code non sécurisé seulement s’il se trouve dans un assembly entièrement fiable. Si vous utilisez du code non sécurisé, il vous incombe de vérifier que votre code n’introduit pas de risques de sécurité ni d’erreurs de pointeur.  
  
## <a name="unsafe-code-overview"></a>Vue d’ensemble du code unsafe

Le code non sécurisé a les propriétés suivantes :

- Les méthodes, les types et les blocs de code peuvent être définis comme non sécurisés.

- Dans certains cas, le code non sécurisé peut augmenter les performances d’une application en supprimant les vérifications des limites des tableaux.

- Du code non sécurisé est obligatoire quand vous appelez des fonctions natives nécessitant des pointeurs.

- L’utilisation de code non sécurisé introduit des risques pour la sécurité et la stabilité.

- Le code qui contient des blocs unsafe doit être compilé avec l’option de compilateur [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md).
  
## <a name="related-sections"></a>Rubriques connexes

Pour plus d'informations, voir :

- [Types de pointeur](pointer-types.md)

- [Mémoires tampons de taille fixe](fixed-size-buffers.md)

## <a name="c-language-specification"></a>spécification du langage C#

Pour en savoir plus, consultez la rubrique [Code unsafe](~/_csharplang/spec/unsafe-code.md) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).
  
## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../index.md)
- [unsafe](../../language-reference/keywords/unsafe.md)
