---
title: Assignation des variables objets (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Nothing keyword [Visual Basic], object variable assignment
- object variables [Visual Basic], initializing
- variables [Visual Basic], initializing
- objects [Visual Basic], current instance
- object variables [Visual Basic], assigning
- variables [Visual Basic], object variables
- current instance [Visual Basic], defined
- variables [Visual Basic], assigning
- assignment statements [Visual Basic], object variable assignment
- Me keyword [Visual Basic], as object variable
ms.assetid: 3706811d-fd40-44fe-8727-d692e8e55d6d
ms.openlocfilehash: 59dea45511ba8d7d10c95cf17e47981124c532e4
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68631058"
---
# <a name="object-variable-assignment-visual-basic"></a>Assignation des variables objets (Visual Basic)

Vous utilisez une instruction d’assignation normale pour assigner un objet à une variable objet. Vous pouvez assigner une expression d’objet ou le mot clé [Nothing](../../../../visual-basic/language-reference/nothing.md) , comme l’illustre l’exemple suivant.

```vb
Dim thisObject As Object
' The following statement assigns an object reference.
thisObject = Form1
' The following statement discontinues association with any object.
thisObject = Nothing
```

`Nothing`signifie qu’aucun objet n’est actuellement assigné à la variable.

## <a name="initialization"></a>Initialisation

Lorsque votre code commence à s’exécuter, vos variables objet sont initialisées à `Nothing`. Ceux dont les déclarations incluent l’initialisation sont réinitialisés aux valeurs que vous spécifiez lors de l’exécution des instructions de déclaration.

Vous pouvez inclure l’initialisation dans votre déclaration à l’aide du mot clé [New](../../../../visual-basic/language-reference/operators/new-operator.md) . Les instructions de déclaration suivantes déclarent `testUri` des `ver` variables objets et leur assignent des objets spécifiques. Chacun utilise l’un des constructeurs surchargés de la classe appropriée pour initialiser l’objet.

```vb
Dim testUri As New System.Uri("https://www.microsoft.com")
Dim ver As New System.Version(6, 1, 0)
```

## <a name="disassociation"></a>Dissociation

La définition d’une variable `Nothing` objet pour interrompt l’Association de la variable avec un objet spécifique. Cela vous empêche de modifier accidentellement l’objet en modifiant la variable. Elle vous permet également de tester si la variable objet pointe vers un objet valide, comme le montre l’exemple suivant.

```vb
If otherObject IsNot Nothing Then
    ' otherObject refers to a valid object, so your code can use it.
End If
```

Si l’objet auquel votre variable fait référence se trouve dans une autre application, ce test ne peut pas déterminer si cette application s’est arrêtée ou si elle vient d’être invalidée par l’objet.

Une variable objet avec la valeur `Nothing` est également appelée *référence null*.

## <a name="current-instance"></a>Instance actuelle

L' *instance actuelle* d’un objet est celle dans laquelle le code est en cours d’exécution. Étant donné que tout le code s’exécute à l’intérieur d’une procédure, l’instance actuelle est celle dans laquelle la procédure a été appelée.

Le `Me` mot clé agit comme une variable objet qui fait référence à l’instance actuelle. Si une procédure n’est pas [partagée](../../../../visual-basic/language-reference/modifiers/shared.md), elle peut utiliser `Me` le mot clé pour obtenir un pointeur vers l’instance actuelle. Les procédures partagées ne peuvent pas être associées à une instance spécifique d’une classe.

L' `Me` utilisation de est particulièrement utile pour passer l’instance actuelle à une procédure d’un autre module. Supposons, par exemple, que vous ayez un certain nombre de documents XML et que vous souhaitiez ajouter du texte standard à tous. L’exemple suivant définit une procédure pour effectuer cette opération.

```vb
Sub addStandardText(XmlDoc As System.Xml.XmlDocument)
    XmlDoc.CreateTextNode("This text goes into every XML document.")
End Sub
```

Chaque objet de document XML peut ensuite appeler la procédure et passer son instance actuelle en tant qu’argument. Cela est illustré par l'exemple suivant.

```vb
addStandardText(Me)
```

## <a name="see-also"></a>Voir aussi

- [Variables objets](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [Déclaration des variables objets](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [Valeurs des variables objets](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
- [Guide pratique pour Déclarez une variable objet et assignez-lui un objet dans Visual Basic](../../../../visual-basic/programming-guide/language-features/variables/how-to-declare-an-object-variable-and-assign-an-object-to-it.md)
- [Guide pratique pour Faire en sorte qu’une variable objet ne fasse pas référence à une instance](../../../../visual-basic/programming-guide/language-features/variables/how-to-make-an-object-variable-not-refer-to-any-instance.md)
- [Me, My, MyBase et MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
