---
title: <clear>, élément de <configSections>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: 77f1d761-ff45-4001-8f36-3a3e5c41fa63
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: c06fca8b83638fb47bedb21863cb9b200cd211f3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927727"
---
# <a name="clear-element-for-configsections"></a>\<Clear > élément pour \<configSections >

Efface toutes les sections et tous les groupes de sections précédemment définis.

[ **\<configuration>** ](configuration-element.md)   
&nbsp;&nbsp;[ **\<configSections>** ](configsections-element-for-configuration.md)   
&nbsp;&nbsp;&nbsp;&nbsp; **\<clear>**

## <a name="syntax"></a>Syntaxe

```xml
<clear/>
```

## <a name="attribute"></a>Attribut

|           | Description |
| --------- | ----------- |
| **name**  | Attribut requis.<br><br>Spécifie le nom de la section ou du groupe de sections à supprimer. |

## <a name="parent-element"></a>Élément parent

|     | Description |
| --- | ----------- |
| [élément  **>\<configSections**](configsections-element-for-configuration.md) | Contient la section de configuration et les déclarations d’espace de noms. |

## <a name="child-elements"></a>Éléments enfants

Aucun

## <a name="remarks"></a>Notes

L’élément clear > supprime tous les sections et groupes de section de votre application qui ont été définis précédemment dans le fichier de configuration actuel ou à un niveau supérieur dans la hiérarchie des fichiers de configuration.  **\<**

## <a name="example"></a>Exemples

Cet exemple définit un fichier de configuration d’ordinateur et un fichier de configuration d’application et montre comment utiliser l'  **\<élément clear >** dans un fichier de configuration d’application pour effacer les sections précédemment définies dans la configuration de l’ordinateur. txt.

Le code de fichier de configuration d’ordinateur suivant déclare deux sections,  **\<sampleSection >** et  **\<anotherSampleSection >** , qui sont lues avant le fichier de configuration de l’application:

```xml
<!-- Machine.config file -->
<configuration>
  <configSections>
    <section name="sampleSection"
             type="System.Configuration.SingleTagSectionHandler" />
    <section name="anotherSampleSection"
             type="System.Configuration.NameValueSectionHandler" />
  </configSections>
  <sampleSection setting1="Value1" 
                 setting2="value two" 
                 setting3="third value" />
</configuration>
```

Le code de fichier de configuration d’application suivant efface toutes les sections déclarées précédemment. L’application ne peut pas utiliser ou récupérer les paramètres de l’une des sections qui ont été déclarées dans le fichier de configuration de l’ordinateur. Toutefois, il peut utiliser les paramètres de  **\<anotherSection >** , car il vient après l'  **\<élément clear >** .

```xml
<!-- Application configuration file -->
<configuration>
  <configSections>
    <clear/>
    <section name="anotherSection"
             type="System.Configuration.NameValueSectionHandler" />
  </configSections>
  <anotherSection setting1="Value1" 
                 setting2="value two" 
                 setting3="third value" />
</configuration>
```

## <a name="configuration-file"></a>fichier de configuration

Cet élément peut être utilisé dans le fichier de configuration de l’application, le fichier de configuration de l’ordinateur (*machine. config*) et les fichiers *Web. config* qui ne sont pas au niveau du répertoire de l’application.

## <a name="see-also"></a>Voir aussi

- [Schéma du fichier de configuration pour le .NET Framework](index.md)
