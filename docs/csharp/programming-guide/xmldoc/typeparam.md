---
title: <typeparam> - Guide de programmation C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- typeparam
helpviewer_keywords:
- <typeparam> C# XML tag
- typeparam C# XML tag
ms.assetid: 9b99d400-e911-4e55-99c6-64367c96aa4f
ms.openlocfilehash: ea48cf0cdfc2dc48ad29ab6219449f801739bc8f
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69587592"
---
# <a name="typeparam-c-programming-guide"></a>\<typeparam> (Guide de programmation C#)
## <a name="syntax"></a>Syntaxe  
  
```xml  
<typeparam name="name">description</typeparam>  
```  
  
## <a name="parameters"></a>Paramètres  
 `name`  
 Nom du paramètre de type. Mettez le nom entre guillemets doubles (" ").  
  
 `description`  
 Description du paramètre de type.  
  
## <a name="remarks"></a>Notes  
 La balise `<typeparam>` doit être utilisée dans le commentaire d’une déclaration de méthode ou de type générique pour décrire un paramètre de type. Ajoutez une balise pour chaque paramètre de type de la méthode et du type générique.  
  
 Pour plus d’informations, consultez la page [Génériques](../generics/index.md).  
  
 Le texte de la balise `<typeparam>` s’affiche dans IntelliSense, dans la [fenêtre Explorateur d’objets](/visualstudio/ide/viewing-the-structure-of-code#BKMK_ObjectBrowser) et dans le rapport web de commentaire de code.  
  
 Compilez avec [/doc](../../language-reference/compiler-options/doc-compiler-option.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.  
  
## <a name="example"></a>Exemples  
 [!code-csharp[csProgGuideDocComments#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#13)]  
  
## <a name="see-also"></a>Voir aussi

- [Référence C#](../../language-reference/index.md)
- [Guide de programmation C#](../index.md)
- [Balises recommandées pour les commentaires de documentation](./recommended-tags-for-documentation-comments.md)
