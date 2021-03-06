---
title: Fonction GetCurrentApartmentType (référence des API non managées)
description: La fonction GetCurrentApartmentType récupère le type de cloisonnement dans lequel l’appelant s’exécute.
ms.date: 11/06/2017
api_name:
- GetCurrentApartmentType
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetCurrentApartmentType
helpviewer_keywords:
- GetCurrentApartmentType function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ff64be47802a46979818ab54cc3efb4112dd05e0
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798614"
---
# <a name="getcurrentapartmenttype-function"></a>GetCurrentApartmentType fonction)
Récupère le type de cloisonnement dans lequel l’appelant s’exécute.   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetCurrentApartmentType (
   [in] int                   vFunc, 
   [in] IComThreadingInfo*    ptr, 
   [out] APTTYPE*             aptType
); 
```  

## <a name="parameters"></a>Paramètres

`vFunc`  
dans Ce paramètre n’est pas utilisé.

`ptr`  
dans Pointeur vers une instance [IComThreadingInfo](/windows/desktop/api/objidlbase/nn-objidlbase-icomthreadinginfo) .

`aptType`  
à Pointeur vers une valeur d’énumération [APTTYPE](/windows/win32/api/objidlbase/ne-objidlbase-apttype) qui indique le cloisonnement de l’appelant.

## <a name="return-value"></a>Valeur de retour

|Constante  |`Value`  |Description  |
|---------|---------|---------|
| `S_OK` | 0 | La fonction s’est terminée avec succès. |
| `E_FAIL` | 0x80000008 | L’appelant ne s’exécute pas dans un cloisonnement. |
  
## <a name="remarks"></a>Notes

Cette fonction encapsule un appel à la méthode [IComThreadingInfo :: GetCurrentApartmentType](/windows/desktop/api/objidlbase/nf-objidlbase-icomthreadinginfo-getcurrentapartmenttype) .

## <a name="requirements"></a>Configuration requise  
 **Plateformes** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** WMINet_Utils.idl  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Voir aussi

- [WMI et compteurs de performance (informations de référence sur les API non managées)](index.md)
