---
title: Accès d'un membre partagé via une instance ; l'expression qualifiante ne sera pas évaluée
ms.date: 07/20/2015
f1_keywords:
- vbc42025
- BC42025
helpviewer_keywords:
- BC42025
ms.assetid: db3337e5-c349-42bf-86df-d9c1e00952a5
ms.openlocfilehash: 3174d463744303e8c90ed0b2e1a4d86ed08fbcfb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69947695"
---
# <a name="access-of-shared-member-through-an-instance-qualifying-expression-will-not-be-evaluated"></a>Accès d'un membre partagé via une instance ; l'expression qualifiante ne sera pas évaluée
Une variable d’instance d’une classe ou d’une structure est utilisée `Shared` pour accéder à une variable, une propriété, une procédure ou un événement défini dans cette classe ou structure. Cet avertissement peut également se produire si une variable d’instance est utilisée pour accéder à un membre implicitement partagé d’une classe ou d’une structure, par exemple une constante ou une énumération, ou une classe ou une structure imbriquée.  
  
 L’objectif du partage d’un membre est de créer une seule copie de ce membre et de rendre cette copie disponible pour chaque instance de la classe ou de la structure dans laquelle elle est déclarée. Elle est cohérente dans le but d’accéder `Shared` à un membre par le biais du nom de sa classe ou de sa structure, plutôt que par le biais d’une variable qui contient une instance individuelle de cette classe ou structure.  
  
 L’accès à `Shared` un membre via une variable d’instance peut rendre votre code plus difficile à comprendre en masquant le fait que le `Shared`membre est. En outre, si un tel accès fait partie d’une expression qui effectue d’autres actions, `Function` telles qu’une procédure qui retourne une instance du membre partagé, Visual Basic ignore l’expression et toutes les autres actions qu’il exécuterait autrement.  
  
 Pour plus d’informations et un exemple, consultez [Shared](../../../visual-basic/language-reference/modifiers/shared.md).  
  
 Par défaut, ce message est un avertissement. Pour plus d’informations sur le masquage des avertissements ou le traitement des avertissements en tant qu’erreurs, consultez [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID d’erreur :** BC42025  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
- Utilisez le nom de la classe ou de la structure qui `Shared` définit le membre pour y accéder, comme indiqué dans l’exemple suivant.  
  
```vb  
Public Class testClass  
    Public Shared Sub sayHello()  
        MsgBox("Hello")  
    End Sub  
End Class  
  
Module testModule  
    Public Sub Main()  
        ' Access a shared method through an instance variable.  
        ' This generates a warning.  
        Dim tc As New testClass  
        tc.sayHello()  
  
        ' Access a shared method by using the class name.  
        ' This does not generate a warning.  
        testClass.sayHello()  
    End Sub  
End Module  
```  
  
> [!NOTE]
> Soyez averti des effets de la portée lorsque deux éléments de programmation portent le même nom. Dans l’exemple précédent, si vous déclarez une instance à `Dim testClass as testClass = Nothing`l’aide de, le compilateur traite `testClass.sayHello()` un appel à comme un accès à la méthode via le nom de la classe, et aucun avertissement ne se produit.  
  
## <a name="see-also"></a>Voir aussi

- [Shared](../../../visual-basic/language-reference/modifiers/shared.md)
- [Étendue dans Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
