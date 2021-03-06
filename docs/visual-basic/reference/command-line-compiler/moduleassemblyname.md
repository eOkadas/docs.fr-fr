---
title: -moduleassemblyname
ms.date: 03/13/2018
helpviewer_keywords:
- moduleassemblyname compiler option [Visual Basic]
- /moduleassemblyname compiler option [Visual Basic]
- -moduleassemblyname compiler option [Visual Basic]
ms.assetid: 013a57b6-f425-4dd3-b333-512d72c42f55
ms.openlocfilehash: dc4c0336c8a67a1b4e70f71ba5f5406da1fbb2ff
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70972373"
---
# <a name="-moduleassemblyname"></a>-moduleassemblyname
Spécifie le nom de l’assembly dont ce module doit faire partie.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-moduleassemblyname:assembly_name  
```  
  
## <a name="arguments"></a>Arguments  
  
|Terme|Définition|  
|---|---|  
|`assembly_name`|Nom de l’assembly dont ce module fera partie.|  
  
## <a name="remarks"></a>Notes  
 Le compilateur traite l' `-moduleassemblyname` option uniquement si l' `-target:module` option a été spécifiée. Le compilateur crée alors un module. Le module créé par le compilateur est valide uniquement pour l’assembly spécifié avec `-moduleassemblyname` l’option. Si vous placez le module dans un assembly différent, des erreurs d’exécution se produisent.  
  
 L' `-moduleassemblyname` option est requise uniquement lorsque les conditions suivantes sont remplies :  
  
- Un type de données dans le module a besoin d' `Friend` accéder à un type dans un assembly référencé.  
  
- L’assembly référencé a accordé un accès d’assembly friend à l’assembly dans lequel le module sera généré.  
  
 Pour plus d’informations sur la création d’un module, consultez [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md). Pour plus d’informations sur les assemblys friend, consultez [assemblys friend](../../../standard/assembly/friend.md).  
  
> [!NOTE]
> L' `-moduleassemblyname` option n’est pas disponible dans l’environnement de développement Visual Studio ; elle est disponible uniquement quand vous compilez à partir d’une invite de commandes.  
  
## <a name="see-also"></a>Voir aussi

- [Guide pratique pour générer un assembly multifichier](../../../framework/app-domains/build-multifile-assembly.md)
- [Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [-cible (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)
- [-main](../../../visual-basic/reference/command-line-compiler/main.md)
- [-Reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)
- [-addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)
- [Assemblys dans .NET](../../../standard/assembly/index.md)
- [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [Assemblys friend](../../../standard/assembly/friend.md)
