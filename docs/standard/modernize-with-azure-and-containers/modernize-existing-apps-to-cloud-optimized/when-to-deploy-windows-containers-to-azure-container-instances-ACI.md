---
title: Quand déployer des conteneurs de Windows Azure Container Instances (ACI)
description: Moderniser des applications .NET existantes avec des conteneurs de Cloud Azure et Windows | Quand déployer des conteneurs de Windows Azure Container Instances (ACI)
ms.date: 04/29/2018
ms.openlocfilehash: 3b6ae1ced9c4e01f5ab400e2575947a396064ebd
ms.sourcegitcommit: 904b98d8d706f0e2d5ceaa00ce17ffbd92adfb88
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66758597"
---
# <a name="when-to-deploy-windows-containers-to-azure-container-instances-aci"></a><span data-ttu-id="f58a4-103">Quand déployer des conteneurs de Windows Azure Container Instances (ACI)</span><span class="sxs-lookup"><span data-stu-id="f58a4-103">When to deploy Windows Containers to Azure Container Instances (ACI)</span></span>

<span data-ttu-id="f58a4-104">Azure Container Instances proposition de valeur principale est que vous pouvez immédiatement déployer des conteneurs à celui-ci et que vous n’avez pas besoin de mettre à jour de cet environnement, vous n’avez pas besoin de mise à niveau/correction, le système d’exploitation ou les machines virtuelles, tout cela est transparent sous-jacente et que vous venez de déployer conteneurs dans un environnement prêt à l’emploi.</span><span class="sxs-lookup"><span data-stu-id="f58a4-104">Azure Container Instances main value proposition is that you can right away deploy containers to it and you don’t need to maintain that environment, you don’t need to upgrade/patch the underlying operating system or VMs, all that is transparent and you just deploy containers into a ready-to-use environment.</span></span>

<span data-ttu-id="f58a4-105">Les raisons et les scénarios lorsque vous souhaitez utiliser ACI sont similaires pour les principaux scénarios lorsque vous utilisez des machines virtuelles Azure avec des conteneurs, en gros, les principaux scénarios pour l’utilisation d’Azure Container Instances sont :</span><span class="sxs-lookup"><span data-stu-id="f58a4-105">The reasons and scenarios when you would want to use ACI are similar to the main scenarios when you use Azure VMs with containers, so basically, the main scenarios for using Azure Container Instances are:</span></span>

- <span data-ttu-id="f58a4-106">**Scénarios de développement/Test**</span><span class="sxs-lookup"><span data-stu-id="f58a4-106">**Dev/Test scenarios**</span></span>
- <span data-ttu-id="f58a4-107">**Automatisation des tâches**</span><span class="sxs-lookup"><span data-stu-id="f58a4-107">**Task automation**</span></span>
- <span data-ttu-id="f58a4-108">**Agents de CI/CD**</span><span class="sxs-lookup"><span data-stu-id="f58a4-108">**CI/CD agents**</span></span>
- <span data-ttu-id="f58a4-109">**Traitement par lots de petite/mise à l’échelle**</span><span class="sxs-lookup"><span data-stu-id="f58a4-109">**Small/scale batch processing**</span></span>
- <span data-ttu-id="f58a4-110">**Applications web simples**</span><span class="sxs-lookup"><span data-stu-id="f58a4-110">**Simple web apps**</span></span>

<span data-ttu-id="f58a4-111">Le scénario d’applications web simple est un scénario juste pour ACI mais prendre en compte qu’étant donné que dans ACI vous ne pouvez avoir qu’une instance de conteneur unique par l’image de conteneur, vous n’aurez pas une haute disponibilité et avez uniquement une évolutivité limitée.</span><span class="sxs-lookup"><span data-stu-id="f58a4-111">The simple web apps scenario is a fair scenario for ACI but take into account that since in ACI you can only have a single container instance per container image, you won’t have high availability and only have limited scalability.</span></span>

<span data-ttu-id="f58a4-112">Toutefois, même lorsque ACI est considérée comme l’infrastructure, car il fournit simplement des instances de conteneur unique, il est un énorme avantage par rapport à ceux des machines virtuelles Azure avec Windows Server.</span><span class="sxs-lookup"><span data-stu-id="f58a4-112">However, even when ACI is considered infrastructure because it just provides single container instances, there is a huge benefit compared to regular Azure VMs with Windows Server.</span></span> <span data-ttu-id="f58a4-113">Avec ACI, vous déployez simplement les conteneurs dans un environnement de mise à jour automatique, et vous payez uniquement pour ces conteneurs.</span><span class="sxs-lookup"><span data-stu-id="f58a4-113">With ACI, you just deploy the containers into a self-maintained environment and you just pay for those containers.</span></span> <span data-ttu-id="f58a4-114">Vous n’avez pas besoin mettre à jour/mise à jour/correctifs machines virtuelles, par conséquent, il est une meilleure plateforme pour la plupart des scénarios où vous pouvez utiliser des machines virtuelles avec des conteneurs.</span><span class="sxs-lookup"><span data-stu-id="f58a4-114">You don’t need to maintain/update/patch VMs, so it is a much better platform for most scenarios where you might be using VMs with containers.</span></span> <span data-ttu-id="f58a4-115">À l’aide d’ACI est très simple, vous déployez simplement un conteneur, il est inutile de créer un environnement de machine virtuelle que vous déployez simplement des conteneurs.</span><span class="sxs-lookup"><span data-stu-id="f58a4-115">Using ACI is straight forward, you just deploy a container, there’s no need to create a VM environment you just deploy containers.</span></span>

<span data-ttu-id="f58a4-116">Les principaux avantages d’Azure Container Instances (ACI) sont :</span><span class="sxs-lookup"><span data-stu-id="f58a4-116">The main benefits of Azure Container Instances (ACI) are:</span></span>

- <span data-ttu-id="f58a4-117">Exécuter des conteneurs sans gestion de serveurs</span><span class="sxs-lookup"><span data-stu-id="f58a4-117">Run containers without managing servers</span></span>
- <span data-ttu-id="f58a4-118">Augmenter l’agilité avec des conteneurs à la demande</span><span class="sxs-lookup"><span data-stu-id="f58a4-118">Increase agility with containers on demand</span></span>
- <span data-ttu-id="f58a4-119">Déployer des conteneurs vers le cloud avec une simplicité et une vitesse, avec une seule commande.</span><span class="sxs-lookup"><span data-stu-id="f58a4-119">Deploy containers to the cloud with unprecedented simplicity and speed—with a single command.</span></span>
- <span data-ttu-id="f58a4-120">Applications sécurisées avec l’isolation de l’hyperviseur</span><span class="sxs-lookup"><span data-stu-id="f58a4-120">Secure applications with hypervisor isolation</span></span>

<span data-ttu-id="f58a4-121">En bref, vous pouvez développer des applications avec ACI rapidement sans gestion d’ordinateurs virtuels ou de devoir apprendre de nouveaux outils.</span><span class="sxs-lookup"><span data-stu-id="f58a4-121">In short, with ACI you can develop apps fast without managing virtual machines or having to learn new tools.</span></span> <span data-ttu-id="f58a4-122">Il s’agit simplement votre application, dans un conteneur, en cours d’exécution dans le cloud.</span><span class="sxs-lookup"><span data-stu-id="f58a4-122">It's just your application, in a container, running in the cloud.</span></span>

> [!div class="step-by-step"]
> <span data-ttu-id="f58a4-123">[Précédent](when-to-deploy-windows-containers-to-azure-vms-iaas-cloud.md)
> [Suivant](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)</span><span class="sxs-lookup"><span data-stu-id="f58a4-123">[Previous](when-to-deploy-windows-containers-to-azure-vms-iaas-cloud.md)
[Next](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)</span></span>
