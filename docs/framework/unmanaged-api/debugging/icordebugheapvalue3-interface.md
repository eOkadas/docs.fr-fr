---
title: ICorDebugHeapValue3, interface
ms.date: 03/30/2017
api_name:
- ICorDebugHeapValue3
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapValue3
helpviewer_keywords:
- ICorDebugHeapValue3 interface [.NET Framework debugging]
ms.assetid: 9c421bb0-e647-4b2d-a986-f3d578cc7f20
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 24747ccea37707a474d8fff7844ee07301b8194a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69914887"
---
# <a name="icordebugheapvalue3-interface"></a>ICorDebugHeapValue3, interface
Expose les propriétés du verrou du moniteur d'objets. Cette interface étend les interfaces ICorDebugHeapValue et ICorDebugHeapValue2.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetThreadOwningMonitorLock, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue3-getthreadowningmonitorlock-method.md)|Retourne le thread managé qui détient le verrou du moniteur sur cet objet.|  
|[GetMonitorEventWaitList, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue3-getmonitoreventwaitlist-method.md)|Fournit une liste triée des threads mis en file d’attente sur l’événement associé à un verrou d’analyse.|  
  
## <a name="remarks"></a>Notes  
  
> [!NOTE]
> Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug. idl, CorDebug. h  
  
 **Bibliothèque** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Débogage](../../../../docs/framework/unmanaged-api/debugging/index.md)
