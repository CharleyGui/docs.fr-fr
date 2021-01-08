---
title: Quand ne pas déployer sur des conteneurs Windows
description: Moderniser des applications .NET existantes avec des conteneurs Cloud et Windows Azure | Quand ne pas déployer sur des conteneurs Windows
ms.date: 12/21/2020
ms.openlocfilehash: 4eea24ab8deb3719c778b45b3ddc1309277a3f50
ms.sourcegitcommit: 5d9cee27d9ffe8f5670e5f663434511e81b8ac38
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98025171"
---
# <a name="when-not-to-deploy-to-windows-containers"></a><span data-ttu-id="fee30-103">Quand ne pas déployer sur des conteneurs Windows</span><span class="sxs-lookup"><span data-stu-id="fee30-103">When not to deploy to Windows Containers</span></span>

<span data-ttu-id="fee30-104">Certaines technologies Windows ne sont pas prises en charge par les conteneurs Windows.</span><span class="sxs-lookup"><span data-stu-id="fee30-104">Some Windows technologies are not supported by Windows Containers.</span></span> <span data-ttu-id="fee30-105">Dans ce cas, vous devez toujours migrer vers les machines virtuelles de normalisation, généralement avec uniquement Windows et IIS.</span><span class="sxs-lookup"><span data-stu-id="fee30-105">In those cases, you still need to migrate to the standards VMs, usually with just Windows and IIS.</span></span>

<span data-ttu-id="fee30-106">Les cas non pris en charge dans les conteneurs Windows, à compter du 2018 mai :</span><span class="sxs-lookup"><span data-stu-id="fee30-106">Cases not supported in Windows Containers, as of May 2018:</span></span>

- <span data-ttu-id="fee30-107">Microsoft Message Queuing (MSMQ) est actuellement disponible uniquement dans les conteneurs Windows basés sur Windows Server v1803 version, mais pas dans les versions antérieures.</span><span class="sxs-lookup"><span data-stu-id="fee30-107">Microsoft Message Queuing (MSMQ) currently is only available in Windows Containers based on Windows Server v1803 release, but not in any other prior releases.</span></span>

  - [<span data-ttu-id="fee30-108">Forum de demande UserVoice</span><span class="sxs-lookup"><span data-stu-id="fee30-108">UserVoice request forum</span></span>](https://windowsserver.uservoice.com/forums/304624-containers/suggestions/15719031-create-base-container-image-with-msmq-server)

  - [<span data-ttu-id="fee30-109">Forum de discussion</span><span class="sxs-lookup"><span data-stu-id="fee30-109">Discussion forum</span></span>](https://social.msdn.microsoft.com/Forums/bce99a7d-aa60-44fa-a348-450855650810/msmqserver-is-it-supported?forum=windowscontainers)

- <span data-ttu-id="fee30-110">Actuellement, Microsoft Distributed Transaction Coordinator (MSDTC) n’est pas pris en charge dans les conteneurs Windows.</span><span class="sxs-lookup"><span data-stu-id="fee30-110">Microsoft Distributed Transaction Coordinator (MSDTC) currently is not supported in Windows Containers.</span></span>

  - [<span data-ttu-id="fee30-111">Problème GitHub</span><span class="sxs-lookup"><span data-stu-id="fee30-111">GitHub issue</span></span>](https://github.com/MicrosoftDocs/Virtualization-Documentation/issues/494)

- <span data-ttu-id="fee30-112">Microsoft Office ne prend actuellement pas en charge les conteneurs.</span><span class="sxs-lookup"><span data-stu-id="fee30-112">Microsoft Office currently does not support containers.</span></span>

  - [<span data-ttu-id="fee30-113">Forum de demande UserVoice</span><span class="sxs-lookup"><span data-stu-id="fee30-113">UserVoice request forum</span></span>](https://windowsserver.uservoice.com/forums/304624-containers/suggestions/19686220-provide-office-support-for-containers)

- <span data-ttu-id="fee30-114">Les applications d’interface utilisateur (applications clientes avec une interface utilisateur visuelle) ne sont pas des scénarios pris en charge.</span><span class="sxs-lookup"><span data-stu-id="fee30-114">UI apps (client apps with a visual user interface) are not supported scenarios.</span></span>

- <span data-ttu-id="fee30-115">Les rôles d’infrastructure Windows (DNS, DHCP, DC, NTP, impression, serveur de fichiers, IAM, etc.) ne sont pas des scénarios pris en charge.</span><span class="sxs-lookup"><span data-stu-id="fee30-115">Windows infrastructure roles (DNS, DHCP, DC, NTP, PRINT, File server, IAM etc.) are not supported scenarios.</span></span>

<span data-ttu-id="fee30-116">Pour d’autres scénarios et demandes non pris en charge à partir de la Communauté, consultez le Forum UserVoice pour les conteneurs Windows : <https://windowsserver.uservoice.com/forums/304624-containers> .</span><span class="sxs-lookup"><span data-stu-id="fee30-116">For other nonsupported scenarios and requests from the community, see the UserVoice forum for Windows Containers: <https://windowsserver.uservoice.com/forums/304624-containers>.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="fee30-117">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="fee30-117">Additional resources</span></span>

- <span data-ttu-id="fee30-118">**Machines virtuelles et conteneurs dans Azure**</span><span class="sxs-lookup"><span data-stu-id="fee30-118">**Virtual machines and containers in Azure**</span></span>

    <https://azure.microsoft.com/overview/containers/>

> [!div class="step-by-step"]
> <span data-ttu-id="fee30-119">[Précédent](deploy-existing-net-apps-as-windows-containers.md) 
>  [Suivant](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)</span><span class="sxs-lookup"><span data-stu-id="fee30-119">[Previous](deploy-existing-net-apps-as-windows-containers.md)
[Next](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)</span></span>
