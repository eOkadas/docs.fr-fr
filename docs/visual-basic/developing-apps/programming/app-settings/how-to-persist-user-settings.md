---
title: 'Procédure : rendre persistants les paramètres utilisateur en Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- My.Settings object [Visual Basic], persisting user settings
- persistence [Visual Basic], persisting user settings [Visual Basic]
- user settings [Visual Basic], persisting
ms.assetid: 0e5e6415-b6e2-4602-9be0-a65fa167d007
ms.openlocfilehash: 0683a5c359da1c4d082f7312c1ed8f43e1c151f3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968380"
---
# <a name="how-to-persist-user-settings-in-visual-basic"></a>Procédure : rendre persistants les paramètres utilisateur en Visual Basic
Vous pouvez utiliser la méthode `My.Settings.Save` pour rendre persistantes les modifications apportées aux paramètres utilisateur.  
  
 En règle générale, les applications sont conçues pour rendre persistantes les modifications apportées aux paramètres utilisateur quand l’application s’arrête. Cela est dû au fait que l’enregistrement des paramètres peut prendre, en fonction de plusieurs facteurs, plusieurs secondes.  
  
 Pour plus d’informations, consultez [My.Settings, objet](../../../../visual-basic/language-reference/objects/my-settings-object.md).  
  
> [!NOTE]
> Bien que vous puissiez modifier et enregistrer les valeurs des paramètres de portée utilisateur au moment de l’exécution, les paramètres de portée application sont en lecture seule et ne peuvent pas être modifiés par programmation. Vous pouvez changer les paramètres de portée application lors de la création de l’application, par l’intermédiaire du **Concepteur de projet**, ou en modifiant le fichier de configuration de l’application. Pour plus d’informations, consultez [Gestion des paramètres d’une application (.NET)](/visualstudio/ide/managing-application-settings-dotnet).  
  
## <a name="example"></a>Exemples  
 Cet exemple change la valeur du paramètre utilisateur `LastChanged` et enregistre cette modification en appelant la méthode `My.Settings.Save`.  
  
 [!code-vb[VbVbalrMyResources#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#5)]  
  
 Pour que cet exemple fonctionne, votre application doit avoir un paramètre utilisateur `LastChanged`, de type `Date`. Pour plus d'informations, consultez [Gestion des paramètres d’une application (.NET)](/visualstudio/ide/managing-application-settings-dotnet).  
  
## <a name="see-also"></a>Voir aussi

- [My.Settings (objet)](../../../../visual-basic/language-reference/objects/my-settings-object.md)
- [Guide pratique pour lire des paramètres d’application en Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)
- [Guide pratique pour modifier les paramètres utilisateur en Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)
- [Guide pratique pour créer des grilles de propriétés pour les paramètres utilisateur en Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)
- [Gestion des paramètres d’une application (.NET)](/visualstudio/ide/managing-application-settings-dotnet)
