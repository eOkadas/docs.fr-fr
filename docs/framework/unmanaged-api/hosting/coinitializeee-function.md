---
title: CoInitializeEE, fonction
ms.date: 03/30/2017
api_name:
- CoInitializeEE
api_location:
- mscoree.dll
- mscorsvr.dll
api_type:
- DLLExport
f1_keywords:
- CoInitializeEE
helpviewer_keywords:
- CoInitializeEE function [.NET Framework hosting]
ms.assetid: 7e42a928-5068-4ba6-b8c3-806551a01fa8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 72b95b634ffc352b7fad006e0ccd68e6e159dee9
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779107"
---
# <a name="coinitializeee-function"></a>CoInitializeEE, fonction
Garantit que le moteur d’exécution du common language runtime est chargé dans un processus. Cette fonction est déconseillée dans le .NET Framework 4. Utilisez le [ICLRRuntimeHost::Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) méthode à la place.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CoInitializeEE (  
   [in] DWORD fFlags  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `fFlags`  
 [in] Parmi les [COINITIEE](../../../../docs/framework/unmanaged-api/metadata/coinitiee-enumeration.md) constantes d’énumération.  
  
## <a name="return-value"></a>Valeur de retour  
 Cette méthode retourne des codes d’erreur COM standard, tel que défini dans Winerror.h et les valeurs dans le tableau suivant.  
  
|Code de retour|Description|  
|-----------------|-----------------|  
|S_OK|Le moteur d’exécution a été chargé avec succès.|  
|S_FALSE|Le moteur d’exécution est déjà chargé.|  
|E_FAIL|Le moteur d’exécution n’a pas pu être chargé.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode charge le moteur d’exécution s’il n’a pas été chargé précédemment.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Cor.h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Fonctions statiques globales des métadonnées](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
