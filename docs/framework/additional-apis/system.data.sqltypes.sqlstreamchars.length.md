---
title: Propriété SqlStreamChars.Length (System.Data.SqlTypes)
author: douglaslMS
ms.author: douglasl
ms.date: 12/19/2018
ms.technology:
- dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Length
- System.Data.SqlTypes.SqlStreamChars.get_Length
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: ac6e6af9c9411ebc25039e0992133fae2b35ee23
ms.sourcegitcommit: a36cfc9dbbfc04bd88971f96e8a3f8e283c15d42
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/11/2019
ms.locfileid: "54221179"
---
# <a name="sqlstreamcharslength-property"></a><span data-ttu-id="0381a-102">Propriété de SqlStreamChars.Length</span><span class="sxs-lookup"><span data-stu-id="0381a-102">SqlStreamChars.Length Property</span></span>

<span data-ttu-id="0381a-103">En cas de substitution dans une classe dérivée, obtient la longueur du flux actuel.</span><span class="sxs-lookup"><span data-stu-id="0381a-103">When overridden in a derived class, gets the length of the current stream.</span></span> <span data-ttu-id="0381a-104">L’assembly qui contient cette propriété a une relation de friend avec SQLAccess.dll.</span><span class="sxs-lookup"><span data-stu-id="0381a-104">The assembly that contains this property has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="0381a-105">Il est prévu pour une utilisation par SQL Server.</span><span class="sxs-lookup"><span data-stu-id="0381a-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="0381a-106">Pour les autres bases de données, utilisez le mécanisme d’hébergement fourni par cette base de données.</span><span class="sxs-lookup"><span data-stu-id="0381a-106">For other databases, use the hosting mechanism provided by that database.</span></span>

## <a name="syntax"></a><span data-ttu-id="0381a-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0381a-107">Syntax</span></span>

```csharp
public abstract long Length { get; }
```

## <a name="property-value"></a><span data-ttu-id="0381a-108">Valeur de propriété</span><span class="sxs-lookup"><span data-stu-id="0381a-108">Property value</span></span>

<xref:System.Int64>\
<span data-ttu-id="0381a-109">Longueur du flux.</span><span class="sxs-lookup"><span data-stu-id="0381a-109">The length of the stream.</span></span>

## <a name="remarks"></a><span data-ttu-id="0381a-110">Notes</span><span class="sxs-lookup"><span data-stu-id="0381a-110">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="0381a-111">Le `SqlStreamChars.Length` propriété est privée et qu’il n’est pas destinée à être utilisé directement dans votre code.</span><span class="sxs-lookup"><span data-stu-id="0381a-111">The `SqlStreamChars.Length` property is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="0381a-112">Microsoft ne prend pas en charge l’utilisation de ce champ dans une application de production en toute circonstance.</span><span class="sxs-lookup"><span data-stu-id="0381a-112">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="0381a-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="0381a-113">Requirements</span></span>

<span data-ttu-id="0381a-114">**Espace de noms :** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="0381a-114">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="0381a-115">**Assembly :** System.Data (dans System.Data.dll)</span><span class="sxs-lookup"><span data-stu-id="0381a-115">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="0381a-116">**Versions du .NET framework :** Disponible à partir de 2.0.</span><span class="sxs-lookup"><span data-stu-id="0381a-116">**.NET Framework versions:** Available since 2.0.</span></span>