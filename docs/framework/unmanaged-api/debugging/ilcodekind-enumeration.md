---
title: ILCodeKind, énumération
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ILCodeKind
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: b91765e4-82db-46f9-a6dc-6b80610276af
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fea08331fffb85c91721d60764bae8bfe8b30e27
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70928815"
---
# <a name="ilcodekind-enumeration"></a>ILCodeKind, énumération
[Pris en charge dans .NET Framework 4.5.2 et ultérieur]  
  
 Fournit des valeurs qui spécifient si le débogueur peut accéder aux variables locales ou au code ajoutés dans l'instrumentation ReJIT du profileur.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
typedef enum ILCodeKind {  
   ILCODE_ORIGINAL_IL = 0x1,  
   ILCODE_REJIT_IL = 0x2,  
} ILCodeKind;  
```  
  
## <a name="members"></a>Membres  
  
|Nom de membre|Description|  
|-----------------|-----------------|  
|`ILCODE_ORIGINAL_IL`|Le débogueur n'a pas accès aux informations de l'instrumentation ReJIT.|  
|`ILCODE_REJIT_IL`|Le débogueur a accès aux informations de l'instrumentation ReJIT.|  
  
## <a name="remarks"></a>Notes  
 Un membre de l' `ILCodeKind` énumération peut être passé aux méthodes [enumeratelocalvariablesex,](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-enumeratelocalvariablesex-method.md) et [getlocalvariableex,](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-getlocalvariableex-method.md) pour déterminer si le débogueur peut accéder aux variables ajoutées dans l’instrumentation ReJIT du profileur, et au [ Méthode Getcodeex,](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-getcodeex-method.md) pour déterminer si le débogueur peut accéder au langage intermédiaire instrumenté.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug. idl, CorDebug. h  
  
 **Bibliothèque** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Énumérations de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
- [ICorDebugILFrame4, interface](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-interface.md)
- [ReJIT Guide pratique](https://blogs.msdn.microsoft.com/davbr/2011/10/12/rejit-a-how-to-guide/)
