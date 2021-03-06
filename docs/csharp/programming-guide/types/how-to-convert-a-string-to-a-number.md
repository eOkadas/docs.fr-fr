---
title: 'Procédure : Convertir une chaîne en nombre - Guide de programmation C#'
ms.custom: seodec18
ms.date: 02/11/2019
helpviewer_keywords:
- conversions [C#]
- conversions [C#], string to int
- converting strings to int [C#]
- strings [C#], converting to int
ms.assetid: 467b9979-86ee-4afd-b734-30299cda91e3
ms.openlocfilehash: 377074bf09cf1e24ec022cee506588a9dcb8cb80
ms.sourcegitcommit: 77e33b682db39955e331b8e8eda4ef1925a24e78
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2019
ms.locfileid: "70133702"
---
# <a name="how-to-convert-a-string-to-a-number-c-programming-guide"></a>Procédure : Convertir une chaîne en nombre (Guide de programmation C#)

Vous pouvez convertir une [chaîne](../../language-reference/keywords/string.md) en nombre en appelant la méthode `Parse` ou `TryParse` des différents types numériques (`int`, `long`, `double`, etc.), ou bien en utilisant des méthodes dans la classe <xref:System.Convert?displayProperty=nameWithType>.  
  
 Si vous avez une chaîne, il est légèrement plus efficace et direct d’appeler une méthode `TryParse` (par exemple [`int.TryParse("11", out number)`](xref:System.Int32.TryParse%2A)) ou une méthode `Parse` (par exemple, [`var number = int.Parse("11")`](xref:System.Int32.Parse%2A)).  L'utilisation d'une méthode <xref:System.Convert> s'avère plus utile pour les objets généraux qui implémentent <xref:System.IConvertible>.  
  
 Vous pouvez utiliser les méthodes `Parse` ou `TryParse` sur le type numérique que doit contenir la chaîne, notamment le type <xref:System.Int32?displayProperty=nameWithType>.  La méthode <xref:System.Convert.ToInt32%2A?displayProperty=nameWithType> utilise <xref:System.Int32.Parse%2A> en interne.  La méthode `Parse` retourne le nombre converti ; la méthode `TryParse` retourne une valeur <xref:System.Boolean> qui indique si la conversion a réussi et retourne le nombre converti dans un [`out`paramètre](../../language-reference/keywords/out.md). Si le format de la chaîne n’est pas valide, `Parse` lève une exception, tandis que `TryParse` retourne [false](../../language-reference/keywords/false-literal.md). Lorsque vous appelez une méthode `Parse`, vous devez toujours utiliser la gestion des exceptions pour intercepter une <xref:System.FormatException> si l’opération d’analyse échoue.  
  
## <a name="calling-the-parse-and-tryparse-methods"></a>Appel des méthodes Parse et TryParse

Les méthodes `Parse` et `TryParse` ignorent l’espace blanc au début et à la fin de la chaîne, mais tous les autres caractères doivent être des caractères qui forment le type numérique approprié (`int`, `long`, `ulong`, `float`, `decimal`, etc.).  La présence d’un espace blanc dans la chaîne qui forme le nombre génère une erreur.  Par exemple, vous pouvez utiliser `decimal.TryParse` pour analyser « 10 », « 10.3 », « 10 », mais vous ne pouvez pas utiliser cette méthode pour analyser 10 à partir de « 10X », « 1 0 » (notez l’espace incorporé), « 10 .3 » (notez l’espace incorporé), « 10e1 » (`float.TryParse` fonctionne ici), et ainsi de suite. Par ailleurs, une chaîne dont la valeur est `null` ou <xref:System.String.Empty?displayProperty=nameWithType> ne parvient pas à effectuer une analyse. Vous pouvez rechercher une chaîne Null ou vide avant de tenter de l’analyser en appelant la méthode <xref:System.String.IsNullOrEmpty%2A?displayProperty=nameWithType>. 

L’exemple suivant illustre des appels à `Parse` et à `TryParse` qui ont réussi ou échoué.  
  
[!code-csharp[Parse and TryParse](~/samples/snippets/csharp/programming-guide/string-to-number/parse-tryparse/program.cs)]  

L’exemple suivant illustre une approche de l’analyse d’une chaîne prévoyant d’inclure des caractères numériques de début (y compris des caractères hexadécimaux) et des caractères non numériques de fin. Il attribue dès le début des caractères valides à une nouvelle chaîne avant d’appeler la méthode <xref:System.Int32.TryParse%2A>. Étant donné que les chaînes à analyser contiennent un petit nombre de caractères, l’exemple appelle la méthode <xref:System.String.Concat%2A?displayProperty=nameWithType> pour attribuer des caractères valides à une nouvelle chaîne. Pour une chaîne plus grande, la classe <xref:System.Text.StringBuilder> peut être utilisée à la place. 
  
[!code-csharp[Removing invalid characters](~/samples/snippets/csharp/programming-guide/string-to-number/parse-tryparse2/program.cs)]  

## <a name="calling-the-convert-methods"></a>Appel des méthodes de conversion

Le tableau suivant répertorie quelques unes des méthodes de la classe <xref:System.Convert> que vous pouvez utiliser pour convertir une chaîne en nombre.  
  
|Type numérique|Méthode|  
|------------------|------------|  
|`decimal`|<xref:System.Convert.ToDecimal%28System.String%29>|  
|`float`|<xref:System.Convert.ToSingle%28System.String%29>|  
|`double`|<xref:System.Convert.ToDouble%28System.String%29>|  
|`short`|<xref:System.Convert.ToInt16%28System.String%29>|  
|`int`|<xref:System.Convert.ToInt32%28System.String%29>|  
|`long`|<xref:System.Convert.ToInt64%28System.String%29>|  
|`ushort`|<xref:System.Convert.ToUInt16%28System.String%29>|  
|`uint`|<xref:System.Convert.ToUInt32%28System.String%29>|  
|`ulong`|<xref:System.Convert.ToUInt64%28System.String%29>|  
  
 L’exemple suivant appelle la méthode <xref:System.Convert.ToInt32%28System.String%29?displayProperty=nameWithType> pour convertir une entrée de type chaîne en [int](../../language-reference/builtin-types/integral-numeric-types.md). L’exemple intercepte les deux exceptions les plus communes qui peuvent être levées par cette méthode, <xref:System.FormatException> et <xref:System.OverflowException>. Si le nombre obtenu peut être incrémenté sans dépasser <xref:System.Int32.MaxValue?displayProperty=nameWithType>, l’exemple ajoute 1 au résultat et affiche la sortie.  
  
[!code-csharp[Parsing with Convert methods](~/samples/snippets/csharp/programming-guide/string-to-number/convert/program.cs)]  
  
## <a name="see-also"></a>Voir aussi

- [Types](./index.md)
- [Guide pratique pour déterminer si une chaîne représente une valeur numérique](../strings/how-to-determine-whether-a-string-represents-a-numeric-value.md)
- [Exemple : utilitaire de mise en forme .NET Core WinForms (C#)](https://docs.microsoft.com/samples/dotnet/samples/winforms-formatting-utility-cs)
