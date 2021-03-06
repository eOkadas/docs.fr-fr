---
title: <defaultFtpCachePolicy>, élément (paramètres réseau)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#defaultFtpCachePolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/requestCaching/defaultFtpCachePolicy
helpviewer_keywords:
- <defaultFtpCachePolicy> element
- defaultFtpCachePolicy element
ms.assetid: 0eb0c5cb-dd97-484d-8614-785e88877abb
ms.openlocfilehash: 7ff44f0251936d51b4e396c37c53322efa110227
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69659419"
---
# <a name="defaultftpcachepolicy-element-network-settings"></a>\<defaultFtpCachePolicy >, élément (paramètres réseau)
Indique si la mise en cache FTP est active et décrit la stratégie de mise en cache par défaut.  
  
 \<configuration>  
\<system.net>  
\<requestCaching>  
\<defaultFtpCachePolicy>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<defaultFtpCachePolicy  
  policyLevel="BypassCache|Default|CacheOnly|CacheIfAvailable|Revalidate|Reload|NoCacheNoStore|Revalidate"  
/>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`policyLevel`|Spécifie la stratégie de mise en cache FTP. La valeur par défaut est `Default`.|  
  
## <a name="policylevel-attribute"></a>policyLevel (attribut)  
  
|Valeur|Description|  
|-----------|-----------------|  
|`Default`|Retourne la ressource mise en cache si la ressource est actualisée, si la longueur du contenu est exacte et si les attributs d’expiration, de modification et de longueur du contenu sont présents.|  
|`BypassCache`|Retourne la ressource à partir du serveur.|  
|`CacheOnly`|Retourne la ressource mise en cache si la longueur du contenu est présente et correspond à la taille de l’entrée.|  
|`CacheIfAvailable`|Retourne la ressource mise en cache si la longueur du contenu est fournie et correspond à la taille de l’entrée; dans le cas contraire, la ressource est téléchargée à partir du serveur et est retournée à l’appelant.|  
|`Revalidate`|Retourne la ressource mise en cache si l’horodateur de la ressource mise en cache est le même que celui de la ressource sur le serveur; dans le cas contraire, la ressource est téléchargée à partir du serveur, stockée dans le cache et retournée à l’appelant.|  
|`Reload`|Télécharge la ressource à partir du serveur, la stocke dans le cache et retourne la ressource à l’appelant.|  
|`NoCacheNoStore`|Si une ressource mise en cache existe, elle est supprimée. La ressource est téléchargée à partir du serveur et est retournée à l’appelant.|  
|`Revalidate`|Satisfait une demande en utilisant la copie mise en cache de la ressource si l’horodatage est le même que celui de la ressource sur le serveur; dans le cas contraire, la ressource est téléchargée à partir du serveur, présentée à l’appelant et stockée dans le cache.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[requestCaching](requestcaching-element-network-settings.md)|Contrôle le mécanisme de mise en cache pour les demandes réseau.|  
  
## <a name="remarks"></a>Notes  
  
## <a name="example"></a>Exemples  
 L’exemple suivant montre comment spécifier une stratégie de mise en cache `NoCacheNoStore`FTP de.  
  
```xml  
<configuration>  
  <system.net>  
    <requestCaching>  
      <defaultFtpCachePolicy  
        policyLevel="NoCacheNoStore">  
      </defaultFtpCachePolicy>  
    </requestCaching>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Net.Cache>
- <xref:System.Net.WebRequest>
- <xref:System.Net.Cache.RequestCacheLevel>
- [Schéma des paramètres réseau](index.md)
