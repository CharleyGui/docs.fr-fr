---
title: Quand déployer des conteneurs Windows dans les instances de conteneurs Azure (ACI)
description: Moderniser les applications .NET existantes avec les conteneurs Azure Cloud et Windows (fr) Quand déployer des conteneurs Windows dans les instances de conteneurs Azure (ACI)
ms.date: 04/29/2018
ms.openlocfilehash: 6c889db6f0475f24a196144c7fb62faec4c173ed
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2020
ms.locfileid: "80989153"
---
# <a name="when-to-deploy-windows-containers-to-azure-container-instances-aci"></a><span data-ttu-id="18576-103">Quand déployer des conteneurs Windows dans les instances de conteneurs Azure (ACI)</span><span class="sxs-lookup"><span data-stu-id="18576-103">When to deploy Windows Containers to Azure Container Instances (ACI)</span></span>

<span data-ttu-id="18576-104">Azure Container Instances principale proposition de valeur est que vous pouvez immédiatement déployer des conteneurs à elle et vous n’avez pas besoin de maintenir cet environnement, vous n’avez pas besoin de mettre à niveau / patcher le système d’exploitation sous-jacent ou VMs, tout ce qui est transparent et vous venez de déployer des conteneurs dans un environnement prêt à l’emploi.</span><span class="sxs-lookup"><span data-stu-id="18576-104">Azure Container Instances main value proposition is that you can right away deploy containers to it and you don't need to maintain that environment, you don't need to upgrade/patch the underlying operating system or VMs, all that is transparent and you just deploy containers into a ready-to-use environment.</span></span>

<span data-ttu-id="18576-105">Les raisons et les scénarios lorsque vous souhaitez utiliser ACI sont similaires aux principaux scénarios lorsque vous utilisez des VM Azure avec des conteneurs, donc fondamentalement, les principaux scénarios pour l’utilisation azure Container Instances sont les suivantes:</span><span class="sxs-lookup"><span data-stu-id="18576-105">The reasons and scenarios when you would want to use ACI are similar to the main scenarios when you use Azure VMs with containers, so basically, the main scenarios for using Azure Container Instances are:</span></span>

- <span data-ttu-id="18576-106">**Scénarios Dev/Test**</span><span class="sxs-lookup"><span data-stu-id="18576-106">**Dev/Test scenarios**</span></span>
- <span data-ttu-id="18576-107">**Automatisation des tâches**</span><span class="sxs-lookup"><span data-stu-id="18576-107">**Task automation**</span></span>
- <span data-ttu-id="18576-108">**Agents CI/CD**</span><span class="sxs-lookup"><span data-stu-id="18576-108">**CI/CD agents**</span></span>
- <span data-ttu-id="18576-109">**Traitement par lots à petite échelle**</span><span class="sxs-lookup"><span data-stu-id="18576-109">**Small/scale batch processing**</span></span>
- <span data-ttu-id="18576-110">**Applications web simples**</span><span class="sxs-lookup"><span data-stu-id="18576-110">**Simple web apps**</span></span>

<span data-ttu-id="18576-111">Le scénario simple des applications Web est un scénario équitable pour ACI, mais prenez en compte que puisque dans ACI vous ne pouvez avoir qu’une seule instance de conteneur par image de conteneur, vous n’aurez pas une grande disponibilité et n’aurez qu’une évolutivité limitée.</span><span class="sxs-lookup"><span data-stu-id="18576-111">The simple web apps scenario is a fair scenario for ACI but take into account that since in ACI you can only have a single container instance per container image, you won't have high availability and only have limited scalability.</span></span>

<span data-ttu-id="18576-112">Cependant, même lorsque L’ACI est considérée comme une infrastructure parce qu’elle ne fournit que des instances de conteneur unique, il y a un énorme avantage par rapport aux VM Azure réguliers avec Windows Server.</span><span class="sxs-lookup"><span data-stu-id="18576-112">However, even when ACI is considered infrastructure because it just provides single container instances, there is a huge benefit compared to regular Azure VMs with Windows Server.</span></span> <span data-ttu-id="18576-113">Avec ACI, vous venez de déployer les conteneurs dans un environnement auto-entretenu et vous venez de payer pour ces conteneurs.</span><span class="sxs-lookup"><span data-stu-id="18576-113">With ACI, you just deploy the containers into a self-maintained environment and you just pay for those containers.</span></span> <span data-ttu-id="18576-114">Vous n’avez pas besoin de maintenir / mise à jour / patch VMs, il est donc une plate-forme beaucoup mieux pour la plupart des scénarios où vous pourriez utiliser des VM avec des conteneurs.</span><span class="sxs-lookup"><span data-stu-id="18576-114">You don't need to maintain/update/patch VMs, so it is a much better platform for most scenarios where you might be using VMs with containers.</span></span> <span data-ttu-id="18576-115">L’utilisation d’ACI est simple, vous venez de déployer un conteneur, il n’est pas nécessaire de créer un environnement VM que vous venez de déployer des conteneurs.</span><span class="sxs-lookup"><span data-stu-id="18576-115">Using ACI is straight forward, you just deploy a container, there's no need to create a VM environment you just deploy containers.</span></span>

<span data-ttu-id="18576-116">Les principaux avantages des instances de conteneurs Azure (ACI) sont :</span><span class="sxs-lookup"><span data-stu-id="18576-116">The main benefits of Azure Container Instances (ACI) are:</span></span>

- <span data-ttu-id="18576-117">Exécuter des conteneurs sans gérer les serveurs</span><span class="sxs-lookup"><span data-stu-id="18576-117">Run containers without managing servers</span></span>
- <span data-ttu-id="18576-118">Augmenter l’agilité avec les conteneurs à la demande</span><span class="sxs-lookup"><span data-stu-id="18576-118">Increase agility with containers on demand</span></span>
- <span data-ttu-id="18576-119">Déployez des conteneurs dans le nuage avec une simplicité et une vitesse sans précédent, avec une seule commande.</span><span class="sxs-lookup"><span data-stu-id="18576-119">Deploy containers to the cloud with unprecedented simplicity and speed—with a single command.</span></span>
- <span data-ttu-id="18576-120">Applications sécurisées avec isolement hyperviseur</span><span class="sxs-lookup"><span data-stu-id="18576-120">Secure applications with hypervisor isolation</span></span>

<span data-ttu-id="18576-121">En bref, avec ACI, vous pouvez développer des applications rapidement sans gérer les machines virtuelles ou d’avoir à apprendre de nouveaux outils.</span><span class="sxs-lookup"><span data-stu-id="18576-121">In short, with ACI you can develop apps fast without managing virtual machines or having to learn new tools.</span></span> <span data-ttu-id="18576-122">C’est juste votre application, dans un conteneur, en cours d’exécution dans le nuage.</span><span class="sxs-lookup"><span data-stu-id="18576-122">It's just your application, in a container, running in the cloud.</span></span>

> [!div class="step-by-step"]
> <span data-ttu-id="18576-123">[Suivant précédent](when-to-deploy-windows-containers-to-azure-vms-iaas-cloud.md)
> [Next](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)</span><span class="sxs-lookup"><span data-stu-id="18576-123">[Previous](when-to-deploy-windows-containers-to-azure-vms-iaas-cloud.md)
[Next](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)</span></span>
