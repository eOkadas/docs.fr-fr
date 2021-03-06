---
title: <configSections>, élément de <configuration>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections
helpviewer_keywords:
- configSections Element
- <configSections> Element
ms.assetid: 9f963c1b-dc3f-4220-a8b6-2dd7a5a8e039
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: 31b53837e24029fc7ff0b576d95c0213041a434e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927672"
---
# <a name="configsections-element-for-configuration"></a>\<élément > configSections pour \<la configuration >

Contient la section de configuration et les déclarations d’espace de noms.

[ **\<configuration>** ](configuration-element.md)   
&nbsp;&nbsp; **\<configSections>**

## <a name="attributes"></a>Attributs

Aucun

## <a name="parent-element"></a>Élément parent

|     | Description |
| --- | ----------- |
| [ **\<configuration>** ](configuration-element.md) | Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework. |

## <a name="child-elements"></a>Éléments enfants

|     | Description |
| --- | ----------- |
| [ **\<section>** ](section-element.md) | Contient une déclaration de section de configuration. |
| [ **\<sectionGroup>** ](sectiongroup-element-for-configsections.md) | Définit un espace de noms pour les sections de configuration. |
| [ **\<remove>** ](remove-element-for-configsections.md) | Supprime un groupe de sections ou de sections prédéfini. |
| [ **\<clear>** ](clear-element-for-configsections.md) | Efface toutes les sections et tous les groupes de sections précédemment définis. |

## <a name="remarks"></a>Notes

Si cet élément se trouve dans un fichier de configuration, il doit s’agir du premier élément  **\<** enfant de l’élément de configuration >.

## <a name="example"></a>Exemples

L’exemple suivant montre comment définir une section de configuration et définir les paramètres de cette section:

```xml
<configuration>
  <configSections>
    <section name="sampleSection"
             type="System.Configuration.SingleTagSectionHandler" />
  </configSections>
  <sampleSection setting1="Value1" 
                 setting2="value two" 
                 setting3="third value" />
</configuration>
```

## <a name="configuration-file"></a>fichier de configuration

Cet élément peut être utilisé dans le fichier de configuration de l’application, le fichier de configuration de l’ordinateur (*machine. config*) et les fichiers *Web. config* qui ne sont pas au niveau du répertoire de l’application.

## <a name="see-also"></a>Voir aussi

- [Schéma du fichier de configuration pour le .NET Framework](index.md)
