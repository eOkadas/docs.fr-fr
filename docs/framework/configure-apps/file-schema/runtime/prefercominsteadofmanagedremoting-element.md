---
title: Élément <PreferComInsteadOfManagedRemoting>
ms.date: 03/30/2017
helpviewer_keywords:
- <PreferComInsteadOfManagedRemoting> element
- PreferComInsteadOfManagedRemoting element
ms.assetid: a279a42a-c415-4e79-88cf-64244ebda613
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d793c8d84a15f554ada78f3c0dd1f0e936893fd4
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252406"
---
# <a name="prefercominsteadofmanagedremoting-element"></a>\<PreferComInsteadOfManagedRemoting >, élément
Spécifie si le runtime utilisera COM Interop au lieu de la communication à distance pour tous les appels au-delà des limites du domaine d’application.  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<> d’exécution**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<PreferComInsteadOfManagedRemoting>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<PreferComInsteadOfManagedRemoting enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`enabled`|Attribut requis.<br /><br /> Indique si le runtime utilisera COM Interop au lieu de la communication à distance au-delà des limites du domaine d’application.|  
  
## <a name="enabled-attribute"></a>Attribut enabled  
  
|Valeur|Description|  
|-----------|-----------------|  
|`false`|Le runtime utilise la communication à distance au-delà des limites du domaine d’application. Il s'agit de la valeur par défaut.|  
|`true`|Le runtime utilisera COM Interop à travers les limites du domaine d’application.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`runtime`|Contient des informations sur les liaisons d’assembly et l’opération garbage collection.|  
  
## <a name="remarks"></a>Notes  
 Lorsque vous affectez `enabled` à `true`l’attribut la valeur, le runtime se comporte comme suit :  
  
- Le runtime n’appelle pas [IUnknown :: QueryInterface](https://go.microsoft.com/fwlink/?LinkID=144867) pour une interface [IManagedObject](../../../unmanaged-api/hosting/imanagedobject-interface.md) lorsqu’une interface [IUnknown](https://go.microsoft.com/fwlink/?LinkId=148003) entre dans le domaine via une interface com. Au lieu de cela, il construit un wrapper RCW ( [Runtime Callable Wrapper](../../../../standard/native-interop/runtime-callable-wrapper.md) ) autour de l’objet.  
  
- Le runtime retourne E_NOINTERFACE lorsqu’il reçoit un `QueryInterface` appel pour une interface [IManagedObject](../../../unmanaged-api/hosting/imanagedobject-interface.md) pour tout [wrapper CCW (COM Callable Wrapper](../../../../standard/native-interop/com-callable-wrapper.md) ) qui a été créé dans ce domaine.  
  
 Ces deux comportements garantissent que tous les appels sur les interfaces COM entre les objets gérés au-delà des limites du domaine d’application utilisent COM et COM Interop au lieu de la communication à distance.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment spécifier que le runtime doit utiliser COM Interop à travers les limites d’isolation :  
  
```xml  
<configuration>  
  <runtime>  
    <PreferComInsteadOfManagedRemoting enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi

- [Schéma des paramètres d’exécution](index.md)
- [Schéma des fichiers de configuration](../index.md)
