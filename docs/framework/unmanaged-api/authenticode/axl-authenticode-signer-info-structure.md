---
title: AXL_AUTHENTICODE_SIGNER_INFO, structure
ms.date: 03/30/2017
ms.assetid: 81c0f8b4-ce35-4716-8651-b642d40648a2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9aaa0258b53b6b39874c8c99c71ecf53cbdb8f97
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787077"
---
# <a name="axl_authenticode_signer_info-structure"></a>AXL_AUTHENTICODE_SIGNER_INFO, structure
Définit les informations du signataire Authenticode.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef struct _AXL_AUTHENTICODE_SIGNER_INFO {  
    DWORD cbSize;  
    HRESULT dwError;  
    ALG_ID algHash;  
    LPCWSTR pwszHash  
    LPCWSTR pwszDescription;  
    LPCWSTR pwszDescriptionUrl;  
    PCCERT_CHAIN_CONTEXT pChainContext  
} AXL_AUTHENTICODE_SIGNER_INFO, * PAXL_AUTHENTICODE_SIGNER_INFO;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`cbSize`|La taille de cette structure.|  
|`dwError`|Le code d’erreur.|  
|`algHash`|L'algorithme de hachage.|  
|`pwszHash`|Le hachage.|  
|`pwszDescription`|La description.|  
|`pwszDescriptionUrl`|L'URL de la description.|  
|`pChainContext`|Le contexte de chaîne du signataire. Consultez la structure [CERT_CONTEXT](/windows/win32/api/wincrypt/ns-wincrypt-cert_context) .|  
  
## <a name="see-also"></a>Voir aussi

- [Authenticode](index.md)
