---
title: ICLRSyncManager::CreateRWLockOwnerIterator, méthode
ms.date: 03/30/2017
api_name:
- ICLRSyncManager.CreateRWLockOwnerIterator
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRSyncManager::CreateRWLockOwnerIterator
helpviewer_keywords:
- ICLRSyncManager::CreateRWLockOwnerIterator method [.NET Framework hosting]
- CreateRWLockOwnerIterator method [.NET Framework hosting]
ms.assetid: b5535b87-9439-424e-b9b3-7d6fafb9819e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 64179e132cfaffbb1fcdc2cd0a47bbcc11be2ff0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69943271"
---
# <a name="iclrsyncmanagercreaterwlockowneriterator-method"></a>ICLRSyncManager::CreateRWLockOwnerIterator, méthode
Demande que le common language runtime (CLR) crée un itérateur que l’hôte doit utiliser pour déterminer l’ensemble des tâches en attente sur un verrou de lecteur-writer.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CreateRWLockOwnerIterator (  
    [in]  SIZE_T    cookie,  
    [out] SIZE_T   *pIterator  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `cookie`  
 dans Cookie associé au verrou lecteur-writer souhaité.  
  
 `pIterator`  
 à Pointeur vers un itérateur qui peut être passé aux méthodes [GetRWLockOwnerNext,](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-getrwlockownernext-method.md) et [DeleteRWLockOwnerIterator,](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-deleterwlockowneriterator-method.md) .  
  
## <a name="return-value"></a>Valeur de retour  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`CreateRWLockOwnerIterator`retourné avec succès.|  
|HOST_E_CLRNOTAVAILABLE|Le CLR n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.|  
|HOST_E_TIMEOUT|Le délai d’attente de l’appel a expiré.|  
|HOST_E_NOT_OWNER|L’appelant ne possède pas le verrou.|  
|HOST_E_ABANDONED|Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.|  
|E_FAIL|Une défaillance catastrophique inconnue s’est produite. Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus. Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.|  
|HOST_E_INVALIDOPERATION|`CreateRWLockOwnerIterator`a été appelé sur un thread qui exécute actuellement du code managé.|  
  
## <a name="remarks"></a>Notes  
 En général, les `CreateRWLockOwnerIterator`hôtes `DeleteRWLockOwnerIterator`appellent les `GetRWLockOwnerNext` méthodes, et Pendant la détection des verrous mortels. L’hôte est chargé de s’assurer que le verrou lecteur-writer est toujours valide, car le CLR n’effectue aucune tentative de maintien du verrou de lecture-écriture. Plusieurs stratégies sont disponibles pour l’hôte afin de garantir la validité du verrou:  
  
- L’hôte peut bloquer les appels de version sur le verrou lecteur-writer (par exemple, [IHostSemaphore:: ReleaseSemaphore,](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-releasesemaphore-method.md)) tout en veillant à ce que ce bloc ne provoque pas d’interblocage.  
  
- L’hôte peut empêcher la sortie d’attendre l’objet d’événement associé au verrou lecteur-writer, ce qui garantit que ce bloc ne provoque pas d’interblocage.  
  
> [!NOTE]
> `CreateRWLockOwnerIterator`doit être appelé uniquement sur les threads qui exécutent actuellement du code non managé.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque** Inclus en tant que ressource dans MSCorEE. dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICLRSyncManager, interface](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [IHostSyncManager, interface](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
