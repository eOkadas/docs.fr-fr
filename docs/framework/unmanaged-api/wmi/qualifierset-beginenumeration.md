---
title: Fonction QualifierSet_BeginEnumeration (référence des API non managées)
description: La fonction QualifierSet_BeginEnumeration réinitialise un énumérateur des qualificateurs d’un objet.
ms.date: 11/06/2017
api_name:
- QualifierSet_BeginEnumeration
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_BeginEnumeration
helpviewer_keywords:
- QualifierSet_BeginEnumeration function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3b75c51ebddd78e447fed57b22a96c2d5c35004e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798348"
---
# <a name="qualifierset_beginenumeration-function"></a>QualifierSet_BeginEnumeration fonction)

Réinitialise un énumérateur des qualificateurs d’un objet au début de l’énumération.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT QualifierSet_BeginEnumeration (
   [in] int                  vFunc,
   [in] IWbemQualifierSet*   ptr,
   [in] LONG                 lFlags
);
```

## <a name="parameters"></a>Paramètres

`vFunc`\
dans Ce paramètre n’est pas utilisé.

`ptr`\
dans Pointeur vers une instance [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) .

`lFlags`\
dans Combinaison d’opérations de bits des indicateurs ou valeurs décrites dans la section [Notes](#remarks) qui spécifie les qualificateurs à inclure dans l’énumération.

## <a name="return-value"></a>Valeur de retour

Les valeurs suivantes retournées par cette fonction sont définies dans le fichier d’en-tête *WbemCli. h* , ou vous pouvez les définir comme des constantes dans votre code :

|Constante  |Valeur  |Description  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Le paramètre `lFlags` n’est pas valide. |
|`WBEM_E_UNEXPECTED` | 0x8004101d | Un deuxième appel à `QualifierSet_BeginEnumeration` a été effectué sans appel à. [`QualifierSet_EndEnumeration`](qualifierset-endenumeration.md) |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Mémoire disponible insuffisante pour commencer une nouvelle énumération. |
|`WBEM_S_NO_ERROR` | 0 | L’appel de la fonction a réussi.  |

## <a name="remarks"></a>Notes

Cette fonction encapsule un appel à la méthode [IWbemQualifierSet :: BeginEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-beginenumeration) .

Pour énumérer tous les qualificateurs d’un objet, cette méthode doit être appelée avant le premier appel à [QualifierSet_Next](qualifierset-next.md). L’ordre dans lequel les qualificateurs sont énumérés est toujours indifférent pour une énumération donnée.

Les indicateurs qui peuvent être passés en tant `lEnumFlags` qu’argument sont définis dans le fichier d’en-tête *WbemCli. h* , ou vous pouvez les définir comme des constantes dans votre code.

|Constante  |Valeur  |Description  |
|---------|---------|---------|
|  | 0 | Retourne les noms de tous les qualificateurs. |
| `WBEM_FLAG_LOCAL_ONLY` | 0x10 | Retourne uniquement les noms des qualificateurs spécifiques à la propriété ou à l’objet actuel. <br/> Pour une propriété : Retourne uniquement les qualificateurs spécifiques à la propriété (y compris les substitutions), et non les qualificateurs propagés à partir de la définition de classe. <br/> Pour une instance : Retourne uniquement des noms de qualificateurs spécifiques à l’instance. <br/> Pour une classe : Retourne uniquement les qualificateurs spécifiques à la classe qui est dérivée.
|`WBEM_FLAG_PROPAGATED_ONLY` | 0x20 | Retourne uniquement les noms des qualificateurs propagés à partir d’un autre objet. <br/> Pour une propriété : Retourne uniquement les qualificateurs propagés à cette propriété à partir de la définition de classe, et non ceux de la propriété elle-même. <br/> Pour une instance : Retourne uniquement les qualificateurs propagés à partir de la définition de classe. <br/> Pour une classe : Retourne uniquement les noms de qualificateur hérités des classes parentes. |

## <a name="requirements"></a>Configuration requise

**Plateformes** Consultez [Configuration requise](../../get-started/system-requirements.md).

**En-tête :** WMINet_Utils.idl

**Versions du .NET Framework :** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Voir aussi

- [WMI et compteurs de performance (informations de référence sur les API non managées)](index.md)
