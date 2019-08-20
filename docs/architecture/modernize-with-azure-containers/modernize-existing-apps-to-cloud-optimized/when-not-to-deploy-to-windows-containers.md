---
title: Quand ne pas déployer sur des conteneurs Windows
description: Moderniser des applications .NET existantes avec des conteneurs Cloud et Windows Azure | Quand ne pas déployer sur des conteneurs Windows
ms.date: 04/28/2018
ms.openlocfilehash: 65e793b846b495e9a1be6db9ddfa38bbf0d49445
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "69577952"
---
# <a name="when-not-to-deploy-to-windows-containers"></a><span data-ttu-id="fafa1-103">Quand ne pas déployer sur des conteneurs Windows</span><span class="sxs-lookup"><span data-stu-id="fafa1-103">When not to deploy to Windows Containers</span></span>

<span data-ttu-id="fafa1-104">Certaines technologies Windows ne sont pas prises en charge par les conteneurs Windows.</span><span class="sxs-lookup"><span data-stu-id="fafa1-104">Some Windows technologies are not supported by Windows Containers.</span></span> <span data-ttu-id="fafa1-105">Dans ce cas, vous devez toujours migrer vers des machines virtuelles standard, généralement avec Windows et IIS uniquement.</span><span class="sxs-lookup"><span data-stu-id="fafa1-105">In those cases, you still need to migrate to standards VMs, usually with just Windows and IIS.</span></span>

<span data-ttu-id="fafa1-106">Les cas non pris en charge dans les conteneurs Windows, à compter du 2018 mai:</span><span class="sxs-lookup"><span data-stu-id="fafa1-106">Cases not supported in Windows Containers, as of May 2018:</span></span>

- <span data-ttu-id="fafa1-107">Microsoft Message Queuing (MSMQ) est actuellement disponible uniquement dans les conteneurs Windows basés sur Windows Server v1803 version, mais pas dans les versions antérieures.</span><span class="sxs-lookup"><span data-stu-id="fafa1-107">Microsoft Message Queuing (MSMQ) currently is only available in Windows Containers based on Windows Server v1803 release, but not in any other prior releases.</span></span>

  - [<span data-ttu-id="fafa1-108">Forum de demande UserVoice</span><span class="sxs-lookup"><span data-stu-id="fafa1-108">UserVoice request forum</span></span>](https://windowsserver.uservoice.com/forums/304624-containers/suggestions/15719031-create-base-container-image-with-msmq-server)

  - [<span data-ttu-id="fafa1-109">Forum de discussion</span><span class="sxs-lookup"><span data-stu-id="fafa1-109">Discussion forum</span></span>](https://social.msdn.microsoft.com/Forums/bce99a7d-aa60-44fa-a348-450855650810/msmqserver-is-it-supported?forum=windowscontainers)

- <span data-ttu-id="fafa1-110">Actuellement, Microsoft Distributed Transaction Coordinator (MSDTC) n’est pas pris en charge dans les conteneurs Windows.</span><span class="sxs-lookup"><span data-stu-id="fafa1-110">Microsoft Distributed Transaction Coordinator (MSDTC) currently is not supported in Windows Containers.</span></span>

  - [<span data-ttu-id="fafa1-111">Problème GitHub</span><span class="sxs-lookup"><span data-stu-id="fafa1-111">GitHub issue</span></span>](https://github.com/MicrosoftDocs/Virtualization-Documentation/issues/494)

- <span data-ttu-id="fafa1-112">Microsoft Office ne prend actuellement pas en charge les conteneurs.</span><span class="sxs-lookup"><span data-stu-id="fafa1-112">Microsoft Office currently does not support containers.</span></span>

  - [<span data-ttu-id="fafa1-113">Forum de demande UserVoice</span><span class="sxs-lookup"><span data-stu-id="fafa1-113">UserVoice request forum</span></span>](https://windowsserver.uservoice.com/forums/304624-containers/suggestions/19686220-provide-office-support-for-containers)

- <span data-ttu-id="fafa1-114">Les applications d’interface utilisateur (applications clientes avec une interface utilisateur visuelle) ne sont pas des scénarios pris en charge.</span><span class="sxs-lookup"><span data-stu-id="fafa1-114">UI apps (client apps with a visual user interface) are not supported scenarios.</span></span>

- <span data-ttu-id="fafa1-115">Les rôles d’infrastructure Windows (DNS, DHCP, DC, NTP, impression, serveur de fichiers, IAM, etc.) ne sont pas des scénarios pris en charge.</span><span class="sxs-lookup"><span data-stu-id="fafa1-115">Windows infrastructure roles (DNS, DHCP, DC, NTP, PRINT, File server, IAM etc.) are not supported scenarios.</span></span>

<span data-ttu-id="fafa1-116">Pour obtenir des scénarios et des demandes supplémentaires non pris en charge par la Communauté, consultez le Forum UserVoice <https://windowsserver.uservoice.com/forums/304624-containers>pour les conteneurs Windows:.</span><span class="sxs-lookup"><span data-stu-id="fafa1-116">For additional not-supported scenarios and requests from the community, see the UserVoice forum for Windows Containers: <https://windowsserver.uservoice.com/forums/304624-containers>.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="fafa1-117">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="fafa1-117">Additional resources</span></span>

- <span data-ttu-id="fafa1-118">**Machines virtuelles et conteneurs dans Azure**</span><span class="sxs-lookup"><span data-stu-id="fafa1-118">**Virtual machines and containers in Azure**</span></span>

    <https://azure.microsoft.com/overview/containers/>

> [!div class="step-by-step"]
> <span data-ttu-id="fafa1-119">[Précédent](deploy-existing-net-apps-as-windows-containers.md)
> [Suivant](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)</span><span class="sxs-lookup"><span data-stu-id="fafa1-119">[Previous](deploy-existing-net-apps-as-windows-containers.md)
[Next](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)</span></span>