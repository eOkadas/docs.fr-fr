---
title: -target:winmdobj (Options du compilateur C#)
ms.date: 07/20/2015
ms.assetid: 1819a045-659d-498a-9457-c466e902986f
ms.openlocfilehash: fe1332f9ed6de9c50c2509e29f22ed7c0e57ade9
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606358"
---
# <a name="-targetwinmdobj-c-compiler-options"></a>-target:winmdobj (Options du compilateur C#)
Si vous utilisez l’option du compilateur **-target:winmdobj**, le compilateur crée un fichier .winmdobj intermédiaire que vous pouvez convertir en fichier binaire (.winmd) Windows Runtime. Le fichier .winmd peut ensuite être consommé par des programmes JavaScript et C++, en plus des programmes en langage managé.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-target:winmdobj  
```  
  
## <a name="remarks"></a>Remarques  
 Le paramètre **winmdobj** signale au compilateur qu’un module intermédiaire est requis. En réponse, Visual Studio compile la bibliothèque de classes C# comme fichier .winmdobj. Le fichier .winmdobj peut ensuite être acheminé via l'outil d'exportation <xref:Microsoft.Build.Tasks.WinMDExp> pour produire un fichier de métadonnées Windows (.winmd). Le fichier .winmd contient à la fois le code de la bibliothèque d'origine et les métadonnées WinMD utilisées par JavaScript ou C++ et par le Windows Runtime.  
  
 La sortie d’un fichier qui est compilé à l’aide de l’option du compilateur **-target:winmdobj** est conçue pour être utilisée uniquement comme entrée pour l’outil d’exportation WimMDExp ; le fichier .winmdobj proprement dit n’est pas référencé directement.  
  
 À moins que vous n’utilisiez l’option [-out](./out-compiler-option.md), le fichier de sortie adopte le nom du premier fichier d’entrée. Une méthode [Main](../../programming-guide/main-and-command-args/index.md) n’est pas nécessaire.  
  
 Si vous spécifiez l’option -target:winmdobj à une invite de commandes, tous les fichiers jusqu’à l’option **-out** ou [-target:module](./target-module-compiler-option.md) suivante sont utilisés pour créer le programme Windows.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-ide-for-a-windows-store-app"></a>Pour définir cette option du compilateur dans l'IDE de Visual Studio pour une application Windows Store  
  
1. Dans l’**Explorateur de solutions**, ouvrez le menu contextuel de votre projet et choisissez **Propriétés**.  
  
2. Choisissez l’onglet **Application**.  
  
3. Dans la liste **Type de sortie**, choisissez **Fichier WinMD**.  
  
     L’option **Fichier WinMD** est disponible uniquement pour les modèles d’application [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)].  
  
 Pour plus d'informations sur la façon de définir cette option du compilateur par programme, consultez <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.  
  
## <a name="example"></a>Exemples  
 La commande suivante compile `filename.cs` dans un fichier .winmdobj intermédiaire.  
  
```console  
csc -target:winmdobj filename.cs  
```  
  
## <a name="see-also"></a>Voir aussi

- [-target (Options du compilateur C#)](./target-compiler-option.md)
- [Options du compilateur C#](./index.md)
