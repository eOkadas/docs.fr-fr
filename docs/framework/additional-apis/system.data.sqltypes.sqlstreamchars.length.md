---
title: Propriété SqlStreamChars.Length (System.Data.SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/19/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Length
- System.Data.SqlTypes.SqlStreamChars.get_Length
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 8f318f593237dc555d546858152bb03546c8306b
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65634455"
---
# <a name="sqlstreamcharslength-property"></a>Propriété de SqlStreamChars.Length

En cas de substitution dans une classe dérivée, obtient la longueur du flux actuel. L’assembly qui contient cette propriété a une relation de friend avec SQLAccess.dll. Il est prévu pour une utilisation par SQL Server. Pour les autres bases de données, utilisez le mécanisme d’hébergement fourni par cette base de données.

## <a name="syntax"></a>Syntaxe

```csharp
public abstract long Length { get; }
```

## <a name="property-value"></a>Valeur de propriété

<xref:System.Int64>\
Longueur du flux.

## <a name="remarks"></a>Notes

> [!WARNING]
> Le `SqlStreamChars.Length` propriété est privée et qu’il n’est pas destinée à être utilisé directement dans votre code.
>
> Microsoft ne prend pas en charge l’utilisation de ce champ dans une application de production en toute circonstance.

## <a name="requirements"></a>Configuration requise

**Espace de noms :** <xref:System.Data.SqlTypes>

**Assembly :** System.Data (dans System.Data.dll)

**Versions du .NET framework :** Disponible à partir de 2.0.
