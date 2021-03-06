---
title: GUID_ManagedName, attribut
ms.date: 03/30/2017
api_name:
- GUID_ManagedName
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GUID_ManagedName
helpviewer_keywords:
- GUID_ManagedName attribute
ms.assetid: 11e18095-e444-47bc-aff6-b887ac5dc01e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f14d00f17a61576a50e26d3cbcf734a10ed3c03a
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70895018"
---
# <a name="guid_managedname-attribute"></a>GUID_ManagedName, attribut
Définit un attribut d’interface personnalisé qui spécifie le nom de l’espace de noms managé pour une bibliothèque COM (Component Object Model).  
  
## <a name="syntax"></a>Syntaxe  
  
```idl
[  
   custom(GUID_ManagedName, value)  
]  
```  
  
## <a name="parameters"></a>Paramètres  
 `value`  
 Nom de l’espace de noms managé pour la bibliothèque.  
  
## <a name="definition"></a>Définition  
 `GUID_ManagedName`est défini dans Cor. h comme suit :  
  
```cpp
// {0F21F359-AB84-41e8-9A78-36D110E6D2F9}  
EXTERN_GUID(GUID_ManagedName, 0xf21f359, 0xab84, 0x41e8, 0x9a, 0x78, 0x36, 0xd1, 0x10, 0xe6, 0xd2, 0xf9);  
```  
  
## <a name="remarks"></a>Notes  
 Un attribut d’interface personnalisé définit les métadonnées d’un objet dans la bibliothèque de types.  
  
 Utilisez <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2.GetCustData%2A?displayProperty=nameWithType> ou<xref:System.Runtime.InteropServices.ComTypes.ITypeLib2.GetCustData%2A?displayProperty=nameWithType> pour récupérer le nom managé de l’attribut.  
  
 Pour plus d’informations, consultez [attributs d’interface](/cpp/windows/attributes/interface-attributes) dans C++ la documentation de référence visuelle.  
  
## <a name="example"></a>Exemples  
 L’exemple suivant montre une définition de bibliothèque à `GUID_ManagedName` l’aide de l’attribut.  
  
```idl
[  
   ...  
   custom(GUID_ManagedName, Microsoft.VisualStudio.CommandBars.dll")  
]  
library Microsoft_VisualStudio_CommandBars  
{  
   ...  
}  
```  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** Cor. h
