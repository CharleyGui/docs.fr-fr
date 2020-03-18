---
title: Quand ne pas déployer sur des conteneurs Windows
description: Moderniser les applications .NET existantes avec les conteneurs Azure Cloud et Windows (fr) Lorsque vous ne devez pas vous déployer dans les conteneurs Windows
ms.date: 04/28/2018
ms.openlocfilehash: 65e793b846b495e9a1be6db9ddfa38bbf0d49445
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "69577952"
---
# <a name="when-not-to-deploy-to-windows-containers"></a><span data-ttu-id="d1821-103">Quand ne pas déployer sur des conteneurs Windows</span><span class="sxs-lookup"><span data-stu-id="d1821-103">When not to deploy to Windows Containers</span></span>

<span data-ttu-id="d1821-104">Certaines technologies Windows ne sont pas prises en charge par Windows Containers.</span><span class="sxs-lookup"><span data-stu-id="d1821-104">Some Windows technologies are not supported by Windows Containers.</span></span> <span data-ttu-id="d1821-105">Dans ces cas, vous devez toujours migrer vers des magnétoscopes standards, généralement avec uniquement Windows et IIS.</span><span class="sxs-lookup"><span data-stu-id="d1821-105">In those cases, you still need to migrate to standards VMs, usually with just Windows and IIS.</span></span>

<span data-ttu-id="d1821-106">Cas non pris en charge dans windows Containers, en mai 2018 :</span><span class="sxs-lookup"><span data-stu-id="d1821-106">Cases not supported in Windows Containers, as of May 2018:</span></span>

- <span data-ttu-id="d1821-107">Microsoft Message Queuing (MSMQ) n’est actuellement disponible que dans les conteneurs Windows en fonction de windows Server v1803 version, mais pas dans toute autre version antérieure.</span><span class="sxs-lookup"><span data-stu-id="d1821-107">Microsoft Message Queuing (MSMQ) currently is only available in Windows Containers based on Windows Server v1803 release, but not in any other prior releases.</span></span>

  - [<span data-ttu-id="d1821-108">Forum de demande UserVoice</span><span class="sxs-lookup"><span data-stu-id="d1821-108">UserVoice request forum</span></span>](https://windowsserver.uservoice.com/forums/304624-containers/suggestions/15719031-create-base-container-image-with-msmq-server)

  - [<span data-ttu-id="d1821-109">Forum de discussion</span><span class="sxs-lookup"><span data-stu-id="d1821-109">Discussion forum</span></span>](https://social.msdn.microsoft.com/Forums/bce99a7d-aa60-44fa-a348-450855650810/msmqserver-is-it-supported?forum=windowscontainers)

- <span data-ttu-id="d1821-110">Microsoft Distributed Transaction Coordinator (MSDTC) n’est actuellement pas pris en charge dans windows Containers.</span><span class="sxs-lookup"><span data-stu-id="d1821-110">Microsoft Distributed Transaction Coordinator (MSDTC) currently is not supported in Windows Containers.</span></span>

  - [<span data-ttu-id="d1821-111">Numéro GitHub</span><span class="sxs-lookup"><span data-stu-id="d1821-111">GitHub issue</span></span>](https://github.com/MicrosoftDocs/Virtualization-Documentation/issues/494)

- <span data-ttu-id="d1821-112">Microsoft Office ne prend actuellement pas en charge les conteneurs.</span><span class="sxs-lookup"><span data-stu-id="d1821-112">Microsoft Office currently does not support containers.</span></span>

  - [<span data-ttu-id="d1821-113">Forum de demande UserVoice</span><span class="sxs-lookup"><span data-stu-id="d1821-113">UserVoice request forum</span></span>](https://windowsserver.uservoice.com/forums/304624-containers/suggestions/19686220-provide-office-support-for-containers)

- <span data-ttu-id="d1821-114">Les applications d’interface utilisateur (applications client avec une interface utilisateur visuelle) ne sont pas des scénarios pris en charge.</span><span class="sxs-lookup"><span data-stu-id="d1821-114">UI apps (client apps with a visual user interface) are not supported scenarios.</span></span>

- <span data-ttu-id="d1821-115">Les rôles d’infrastructure Windows (DNS, DHCP, DC, NTP, PRINT, serveur de fichiers, IAM, etc.) ne sont pas des scénarios pris en charge.</span><span class="sxs-lookup"><span data-stu-id="d1821-115">Windows infrastructure roles (DNS, DHCP, DC, NTP, PRINT, File server, IAM etc.) are not supported scenarios.</span></span>

<span data-ttu-id="d1821-116">Pour d’autres scénarios et demandes non pris en charge par la <https://windowsserver.uservoice.com/forums/304624-containers>communauté, consultez le forum UserVoice pour les conteneurs Windows : .</span><span class="sxs-lookup"><span data-stu-id="d1821-116">For additional not-supported scenarios and requests from the community, see the UserVoice forum for Windows Containers: <https://windowsserver.uservoice.com/forums/304624-containers>.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="d1821-117">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="d1821-117">Additional resources</span></span>

- <span data-ttu-id="d1821-118">**Machines et conteneurs virtuels en Azure**</span><span class="sxs-lookup"><span data-stu-id="d1821-118">**Virtual machines and containers in Azure**</span></span>

    <https://azure.microsoft.com/overview/containers/>

> [!div class="step-by-step"]
> <span data-ttu-id="d1821-119">[Suivant précédent](deploy-existing-net-apps-as-windows-containers.md)
> [Next](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)</span><span class="sxs-lookup"><span data-stu-id="d1821-119">[Previous](deploy-existing-net-apps-as-windows-containers.md)
[Next](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)</span></span>
