---
title: Interface de IXCLRDataProcess
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess Interface
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess Interface
helpviewer.keywords:
- IXCLRDataProcess Interface [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 8c98dd42b4ac5593d96478c2286f49ad216a4bc1
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2019
ms.locfileid: "54416431"
---
# <a name="ixclrdataprocess-interface"></a><span data-ttu-id="38a1f-102">Interface de IXCLRDataProcess</span><span class="sxs-lookup"><span data-stu-id="38a1f-102">IXCLRDataProcess Interface</span></span>

<span data-ttu-id="38a1f-103">Fournit des méthodes pour obtenir des informations relatives à un processus.</span><span class="sxs-lookup"><span data-stu-id="38a1f-103">Provides methods for querying information about a process.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a><span data-ttu-id="38a1f-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="38a1f-104">Methods</span></span>

| <span data-ttu-id="38a1f-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="38a1f-105">Method</span></span>                                                                                                                                               | <span data-ttu-id="38a1f-106">Description</span><span class="sxs-lookup"><span data-stu-id="38a1f-106">Description</span></span>                                                                                     |
| ---------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- |
| [<span data-ttu-id="38a1f-107">GetAppDomainByUniqueId</span><span class="sxs-lookup"><span data-stu-id="38a1f-107">GetAppDomainByUniqueId</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdataprocess-getappdomainbyuniqueid-method.md)                       | <span data-ttu-id="38a1f-108">Obtient un `AppDomain` dans un processus par son id unique.</span><span class="sxs-lookup"><span data-stu-id="38a1f-108">Gets an `AppDomain` in a process by its unique id.</span></span>                                              |
| [<span data-ttu-id="38a1f-109">StartEnumModules</span><span class="sxs-lookup"><span data-stu-id="38a1f-109">StartEnumModules</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdataprocess-startenummodules-method.md)                                   | <span data-ttu-id="38a1f-110">Fournit un handle pour énumérer les modules d’un processus.</span><span class="sxs-lookup"><span data-stu-id="38a1f-110">Provides a handle to enumerate the modules of a process.</span></span>                                        |
| [<span data-ttu-id="38a1f-111">EnumModule</span><span class="sxs-lookup"><span data-stu-id="38a1f-111">EnumModule</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdataprocess-enummodule-method.md)                                               | <span data-ttu-id="38a1f-112">Énumère les modules de ce processus.</span><span class="sxs-lookup"><span data-stu-id="38a1f-112">Enumerates the modules of this process.</span></span>                                                         |
| [<span data-ttu-id="38a1f-113">EndEnumModules</span><span class="sxs-lookup"><span data-stu-id="38a1f-113">EndEnumModules</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdataprocess-endenummodules-method.md)                                       | <span data-ttu-id="38a1f-114">Libère les ressources utilisées par les itérateurs internes utilisés pendant l’énumération de module.</span><span class="sxs-lookup"><span data-stu-id="38a1f-114">Releases the resources used by internal iterators used during module enumeration.</span></span>               |
| [<span data-ttu-id="38a1f-115">StartEnumMethodInstancesByAddress</span><span class="sxs-lookup"><span data-stu-id="38a1f-115">StartEnumMethodInstancesByAddress</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdataprocess-startenummethodinstancesbyaddress-method.md) | <span data-ttu-id="38a1f-116">Fournit un handle pour énumérer les instances de la méthode de `AppDomain` en commençant à une adresse donnée.</span><span class="sxs-lookup"><span data-stu-id="38a1f-116">Provides a handle to enumerate the method instances of `AppDomain` starting at a given address.</span></span> |
| [<span data-ttu-id="38a1f-117">EnumMethodInstanceByAddress</span><span class="sxs-lookup"><span data-stu-id="38a1f-117">EnumMethodInstanceByAddress</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdataprocess-enummethodinstancebyaddress-method.md)             | <span data-ttu-id="38a1f-118">Énumère les instances de la méthode de ce processus, en commençant à un offset d’adresse.</span><span class="sxs-lookup"><span data-stu-id="38a1f-118">Enumerates the method instances of this process starting at an address offset.</span></span>                  |
| [<span data-ttu-id="38a1f-119">EndEnumMethodInstancesByAddress</span><span class="sxs-lookup"><span data-stu-id="38a1f-119">EndEnumMethodInstancesByAddress</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdataprocess-endenummethodinstancesbyaddress-method.md)     | <span data-ttu-id="38a1f-120">Libère les ressources utilisées par les itérateurs internes utilisés pendant l’énumération de l’instance.</span><span class="sxs-lookup"><span data-stu-id="38a1f-120">Releases the resources used by internal iterators used during instance enumeration.</span></span>             |

## <a name="remarks"></a><span data-ttu-id="38a1f-121">Notes</span><span class="sxs-lookup"><span data-stu-id="38a1f-121">Remarks</span></span>

<span data-ttu-id="38a1f-122">Cette interface réside dans le runtime et n’est pas exposée par le biais d’en-têtes ou les fichiers de bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="38a1f-122">This interface lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="38a1f-123">Toutefois, il est une interface COM qui dérive de `IUnknown` avec le GUID `5c552ab6-fc09-4cb3-8e36-22fa03c798b7` qui peuvent être obtenues via les mécanismes COM habituels.</span><span class="sxs-lookup"><span data-stu-id="38a1f-123">However, it's a COM interface that derives from `IUnknown` with GUID `5c552ab6-fc09-4cb3-8e36-22fa03c798b7` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="38a1f-124">Spécifications</span><span class="sxs-lookup"><span data-stu-id="38a1f-124">Requirements</span></span>

<span data-ttu-id="38a1f-125">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="38a1f-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>   
<span data-ttu-id="38a1f-126">**En-tête :** Aucun.</span><span class="sxs-lookup"><span data-stu-id="38a1f-126">**Header:** None</span></span>  
<span data-ttu-id="38a1f-127">**Bibliothèque :** Aucun.</span><span class="sxs-lookup"><span data-stu-id="38a1f-127">**Library:** None</span></span>  
<span data-ttu-id="38a1f-128">**Versions du .NET Framework :** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="38a1f-128">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="38a1f-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="38a1f-129">See Also</span></span>

- [<span data-ttu-id="38a1f-130">Débogage</span><span class="sxs-lookup"><span data-stu-id="38a1f-130">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="38a1f-131">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="38a1f-131">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)