---
title: opérateur nameof - Référence C#
ms.custom: seodec18
ms.date: 07/12/2019
f1_keywords:
- nameof_CSharpKeyword
- nameof
helpviewer_keywords:
- nameof operator [C#]
ms.assetid: 33601bf3-cc2c-4496-846d-f9679bccf2a7
ms.openlocfilehash: 965b3e96a20906187df4c8693f050c550a747091
ms.sourcegitcommit: 09d699aca28ae9723399bbd9d3d44aa0cbd3848d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/19/2019
ms.locfileid: "68331439"
---
# <a name="nameof-operator-c-reference"></a>opérateur nameof (Référence C#)

L’opérateur `nameof` obtient le nom d’une variable, d’un type ou d’un membre en tant que constante de chaîne :

[!code-csharp-interactive[nameof operator](~/samples/csharp/language-reference/operators/NameOfOperator.cs#Examples)]

Comme le montre l’exemple précédent, dans le cas d’un type et d’un espace de noms, le nom produit n’est généralement pas [complet](~/_csharplang/spec/basic-concepts.md#fully-qualified-names).

L’opérateur `nameof` est évalué au moment de la compilation et n’a aucun effet au moment de l’exécution.

Vous pouvez utiliser l’opérateur `nameof` pour rendre le code de vérification des arguments plus gérable :

[!code-csharp[nameof and argument check](~/samples/csharp/language-reference/operators/NameOfOperator.cs#ExceptionMessage)]

L’opérateur `nameof` est disponible dans les versions 6 et ultérieures de C#.

## <a name="c-language-specification"></a>spécification du langage C#

Pour plus d’informations, voir la section [Expressions Nameof](~/_csharplang/spec/expressions.md#nameof-expressions) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur C#](../index.md)
- [Opérateurs C#](index.md)
