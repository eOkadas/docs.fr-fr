---
title: Tableaux de paramètres (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- parameter arrays [Visual Basic], about parameter arrays
- ParamArray keyword [Visual Basic], parameter arrays
- Visual Basic code, procedures
- parameters [Visual Basic], parameter arrays
- arguments [Visual Basic], parameter arrays
- procedures [Visual Basic], indefinite number of argument values
- arrays [Visual Basic], parameter arrays
ms.assetid: c43edfae-9114-4096-9ebc-8c5c957a1067
ms.openlocfilehash: 5a2813b81490e7c2fcf1abcf5fd36ca89d9d7929
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933861"
---
# <a name="parameter-arrays-visual-basic"></a>Tableaux de paramètres (Visual Basic)
En règle générale, vous ne pouvez pas appeler une procédure avec plus d’arguments que la déclaration de procédure ne le spécifie. Lorsque vous avez besoin d’un nombre indéfini d’arguments, vous pouvez déclarer un *tableau de paramètres*, ce qui permet à une procédure d’accepter un tableau de valeurs pour un paramètre. Vous n’avez pas besoin de connaître le nombre d’éléments dans le tableau de paramètres lorsque vous définissez la procédure. La taille du tableau est déterminée individuellement par chaque appel à la procédure.  
  
## <a name="declaring-a-paramarray"></a>Déclaration d’un ParamArray  
 Vous utilisez le mot clé [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) pour désigner un tableau de paramètres dans la liste de paramètres. Les règles suivantes s'appliquent :  
  
- Une procédure ne peut définir qu’un seul tableau de paramètres, et doit être le dernier paramètre de la définition de la procédure.  
  
- Le tableau de paramètres doit être passé par valeur. Il est recommandé d’inclure explicitement le mot clé [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) dans la définition de la procédure.  
  
- Le tableau de paramètres est automatiquement facultatif. Sa valeur par défaut est un tableau unidimensionnel vide du type d’élément du tableau de paramètres.  
  
- Tous les paramètres qui précèdent le tableau de paramètres doivent être requis. Le tableau de paramètres doit être le seul paramètre facultatif.  
  
## <a name="calling-a-paramarray"></a>Appel d’un ParamArray  
 Quand vous appelez une procédure qui définit un tableau de paramètres, vous pouvez fournir l’argument de l’une des manières suivantes:  
  
- Rien: vous pouvez omettre l’argument [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) . Dans ce cas, un tableau vide est passé à la procédure. Vous pouvez également transmettre le mot clé [Nothing](../../../../visual-basic/language-reference/nothing.md) , avec le même effet.  
  
- Liste d’un nombre arbitraire d’arguments, séparés par des virgules. Le type de données de chaque argument doit être implicitement convertible en `ParamArray` type d’élément.  
  
- Tableau avec le même type d’élément que le type d’élément du tableau de paramètres.  
  
 Dans tous les cas, le code de la procédure traite le tableau de paramètres comme un tableau unidimensionnel avec des éléments du même type de données `ParamArray` que le type de données.  
  
> [!IMPORTANT]
> Chaque fois que vous traitez un tableau qui peut être indéfiniment volumineux, il existe un risque de surexécution de la capacité interne de votre application. Si vous acceptez un tableau de paramètres, vous devez tester la taille du tableau auquel le code appelant est passé. Prenez les mesures appropriées si elle est trop volumineuse pour votre application. Pour plus d’informations, consultez [Tableaux](../../../../visual-basic/programming-guide/language-features/arrays/index.md).  
  
## <a name="example"></a>Exemples  
 L’exemple suivant définit et appelle la fonction `calcSum`. Le `ParamArray` modificateur du paramètre `args` permet à la fonction d’accepter un nombre variable d’arguments.  
  
 [!code-vb[VbVbalrStatements#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#26)]  
  
 L’exemple suivant définit une procédure avec un tableau de paramètres et renvoie les valeurs de tous les éléments de tableau passés au tableau de paramètres.  
  
 [!code-vb[VbVbcnProcedures#48](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#48)]  
  
 [!code-vb[VbVbcnProcedures#49](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#49)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualBasic.Information.UBound%2A>
- [Procédures](./index.md)
- [Paramètres et arguments d’une procédure](./procedure-parameters-and-arguments.md)
- [Passage d’un argument par valeur et par référence](./passing-arguments-by-value-and-by-reference.md)
- [Passage des arguments par position et par nom](./passing-arguments-by-position-and-by-name.md)
- [Paramètres facultatifs](./optional-parameters.md)
- [Surcharge de procédure](./procedure-overloading.md)
- [Tableaux](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [Facultatif](../../../../visual-basic/language-reference/modifiers/optional.md)
