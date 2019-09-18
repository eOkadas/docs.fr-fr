---
title: 'Procédure : Charger et décharger des assemblys'
ms.date: 08/19/2019
ms.assetid: 6a4f490f-3576-471f-9533-003737cad4a3
ms.openlocfilehash: 77ea97c2fc324287e9c697d630def98241432c9f
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70973200"
---
# <a name="how-to-load-and-unload-assemblies"></a><span data-ttu-id="15ddf-102">Procédure : Charger et décharger des assemblys</span><span class="sxs-lookup"><span data-stu-id="15ddf-102">How to: Load and unload assemblies</span></span>
<span data-ttu-id="15ddf-103">Les assemblys référencés par votre programme sont automatiquement chargés par le common language runtime, mais il est également possible de charger dynamiquement des assemblys spécifiques dans le domaine d’application actuel.</span><span class="sxs-lookup"><span data-stu-id="15ddf-103">The assemblies referenced by your program will automatically be loaded by the common language runtime, but it is also possible to dynamically load specific assemblies into the current application domain.</span></span> <span data-ttu-id="15ddf-104">Pour plus d’informations, consultez [Guide pratique pour Charger des assemblys dans un domaine](../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)d’application.</span><span class="sxs-lookup"><span data-stu-id="15ddf-104">For more information, see [How to: Load assemblies into an application domain](../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md).</span></span>

<span data-ttu-id="15ddf-105">Dans .NET Framework, il n’existe aucun moyen de décharger un assembly individuel sans décharger tous les domaines d’application qui le contiennent.</span><span class="sxs-lookup"><span data-stu-id="15ddf-105">In .NET Framework, there is no way to unload an individual assembly without unloading all of the application domains that contain it.</span></span> <span data-ttu-id="15ddf-106">Même si l’assembly passe hors de portée, le fichier d’assembly proprement dit restera chargé jusqu’à ce que tous les domaines d’application qui le contiennent soient déchargés.</span><span class="sxs-lookup"><span data-stu-id="15ddf-106">Even if the assembly goes out of scope, the actual assembly file will remain loaded until all application domains that contain it are unloaded.</span></span> <span data-ttu-id="15ddf-107">Dans .net Core, la <xref:System.Runtime.Loader.AssemblyLoadContext?displayProperty=nameWithType> classe gère le déchargement des assemblys.</span><span class="sxs-lookup"><span data-stu-id="15ddf-107">In .NET Core, the <xref:System.Runtime.Loader.AssemblyLoadContext?displayProperty=nameWithType> class handles the unloading of assemblies.</span></span> <span data-ttu-id="15ddf-108">Pour plus d’informations, consultez [comment utiliser et déboguer l’inchargement d’assembly dans .net Core](unloadability.md).</span><span class="sxs-lookup"><span data-stu-id="15ddf-108">For more information, see [How to use and debug assembly unloadability in .NET Core](unloadability.md).</span></span>

## <a name="load-and-unload-assemblies"></a><span data-ttu-id="15ddf-109">Charger et décharger des assemblys</span><span class="sxs-lookup"><span data-stu-id="15ddf-109">Load and unload assemblies</span></span>

<span data-ttu-id="15ddf-110">Pour charger un assembly dans un domaine d’application, utilisez l’une des nombreuses méthodes de chargement contenues <xref:System.Reflection.Assembly>dans les classes <xref:System.AppDomain> et.</span><span class="sxs-lookup"><span data-stu-id="15ddf-110">To load an assembly into an application domain, use one of the several load methods contained in the classes <xref:System.AppDomain> and <xref:System.Reflection.Assembly>.</span></span> <span data-ttu-id="15ddf-111">Pour plus d’informations, consultez [Guide pratique pour Charger des assemblys dans un domaine](../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)d’application.</span><span class="sxs-lookup"><span data-stu-id="15ddf-111">For more information, see [How to: Load assemblies into an application domain](../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md).</span></span> <span data-ttu-id="15ddf-112">Notez que .NET Core ne prend en charge qu’un seul domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="15ddf-112">Note that .NET Core supports only a single application domain.</span></span> 

<span data-ttu-id="15ddf-113">Pour décharger un assembly dans le .NET Framework, vous devez décharger tous les domaines d’application qui le contiennent.</span><span class="sxs-lookup"><span data-stu-id="15ddf-113">To unload an assembly in the .NET Framework, you must unload all of the application domains that contain it.</span></span> <span data-ttu-id="15ddf-114">Pour décharger un domaine d’application <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> , utilisez la méthode.</span><span class="sxs-lookup"><span data-stu-id="15ddf-114">To unload an application domain, use the <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="15ddf-115">Pour plus d’informations, consultez [Guide pratique pour Décharger un](../../framework/app-domains/how-to-unload-an-application-domain.md)domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="15ddf-115">For more information, see [How to: Unload an application domain](../../framework/app-domains/how-to-unload-an-application-domain.md).</span></span>

<span data-ttu-id="15ddf-116">Si vous souhaitez décharger certains assemblys, mais pas d’autres dans une application .NET Framework, vous pouvez créer un nouveau domaine d’application, exécuter le code à l’intérieur de ce domaine, puis décharger ce domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="15ddf-116">If you want to unload some assemblies but not others in a .NET Framework application, consider creating a new application domain, executing the code inside that domain, and then unloading that application domain.</span></span> <span data-ttu-id="15ddf-117">Pour plus d'informations, voir [Procédure : Décharger un](../../framework/app-domains/how-to-unload-an-application-domain.md)domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="15ddf-117">For more information, see [How to: Unload an application domain](../../framework/app-domains/how-to-unload-an-application-domain.md).</span></span>  

## <a name="see-also"></a><span data-ttu-id="15ddf-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="15ddf-118">See also</span></span>

- [<span data-ttu-id="15ddf-119">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="15ddf-119">C# programming guide</span></span>](../../csharp/programming-guide/index.md)
- [<span data-ttu-id="15ddf-120">Concepts de programmation (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="15ddf-120">Programming concepts (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/index.md)
- [<span data-ttu-id="15ddf-121">Assemblys dans .NET</span><span class="sxs-lookup"><span data-stu-id="15ddf-121">Assemblies in .NET</span></span>](index.md)
- [<span data-ttu-id="15ddf-122">Guide pratique pour Charger des assemblys dans un domaine d’application</span><span class="sxs-lookup"><span data-stu-id="15ddf-122">How to: Load assemblies into an application domain</span></span>](../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)