---
title: Quand déployer des conteneurs Windows sur Azure Container Instances (ACI)
description: Moderniser des applications .NET existantes avec des conteneurs Cloud et Windows Azure | Quand déployer des conteneurs Windows sur Azure Container Instances (ACI)
ms.date: 04/29/2018
ms.openlocfilehash: 3b6ae1ced9c4e01f5ab400e2575947a396064ebd
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "69577932"
---
# <a name="when-to-deploy-windows-containers-to-azure-container-instances-aci"></a><span data-ttu-id="21075-103">Quand déployer des conteneurs Windows sur Azure Container Instances (ACI)</span><span class="sxs-lookup"><span data-stu-id="21075-103">When to deploy Windows Containers to Azure Container Instances (ACI)</span></span>

<span data-ttu-id="21075-104">Azure Container Instances proposition de valeur principale est que vous pouvez immédiatement déployer des conteneurs sur celui-ci et que vous n’avez pas besoin de gérer cet environnement, vous n’avez pas besoin de mettre à niveau/corriger le système d’exploitation sous-jacent ou les machines virtuelles, tout ce qui est transparent et que vous venez de déployer conteneurs dans un environnement prêt à l’emploi.</span><span class="sxs-lookup"><span data-stu-id="21075-104">Azure Container Instances main value proposition is that you can right away deploy containers to it and you don’t need to maintain that environment, you don’t need to upgrade/patch the underlying operating system or VMs, all that is transparent and you just deploy containers into a ready-to-use environment.</span></span>

<span data-ttu-id="21075-105">Les raisons et les scénarios dans lesquels vous souhaiteriez utiliser ACI sont similaires aux scénarios principaux lorsque vous utilisez des machines virtuelles Azure avec des conteneurs. fondamentalement, les principaux scénarios d’utilisation de Azure Container Instances sont les suivants:</span><span class="sxs-lookup"><span data-stu-id="21075-105">The reasons and scenarios when you would want to use ACI are similar to the main scenarios when you use Azure VMs with containers, so basically, the main scenarios for using Azure Container Instances are:</span></span>

- <span data-ttu-id="21075-106">**Scénarios de développement et de test**</span><span class="sxs-lookup"><span data-stu-id="21075-106">**Dev/Test scenarios**</span></span>
- <span data-ttu-id="21075-107">**Automatisation des tâches**</span><span class="sxs-lookup"><span data-stu-id="21075-107">**Task automation**</span></span>
- <span data-ttu-id="21075-108">**Agents CI/CD**</span><span class="sxs-lookup"><span data-stu-id="21075-108">**CI/CD agents**</span></span>
- <span data-ttu-id="21075-109">**Traitement par lots de petite/échelle**</span><span class="sxs-lookup"><span data-stu-id="21075-109">**Small/scale batch processing**</span></span>
- <span data-ttu-id="21075-110">**Applications Web simples**</span><span class="sxs-lookup"><span data-stu-id="21075-110">**Simple web apps**</span></span>

<span data-ttu-id="21075-111">Le scénario Web Apps simple est un scénario équitable pour ACI mais tient compte du fait que dans ACI, vous ne pouvez avoir qu’une seule instance de conteneur par image de conteneur, vous n’avez pas de haute disponibilité et n’avez qu’une évolutivité limitée.</span><span class="sxs-lookup"><span data-stu-id="21075-111">The simple web apps scenario is a fair scenario for ACI but take into account that since in ACI you can only have a single container instance per container image, you won’t have high availability and only have limited scalability.</span></span>

<span data-ttu-id="21075-112">Toutefois, même quand ACI est considéré comme une infrastructure, car elle fournit simplement des instances de conteneur uniques, il y a un avantage énorme par rapport aux machines virtuelles Azure classiques avec Windows Server.</span><span class="sxs-lookup"><span data-stu-id="21075-112">However, even when ACI is considered infrastructure because it just provides single container instances, there is a huge benefit compared to regular Azure VMs with Windows Server.</span></span> <span data-ttu-id="21075-113">Avec ACI, vous déployez simplement les conteneurs dans un environnement autonome et vous payez uniquement pour ces conteneurs.</span><span class="sxs-lookup"><span data-stu-id="21075-113">With ACI, you just deploy the containers into a self-maintained environment and you just pay for those containers.</span></span> <span data-ttu-id="21075-114">Vous n’avez pas besoin de gérer/mettre à jour/corriger les machines virtuelles. il s’agit donc d’une plateforme bien meilleure pour la plupart des scénarios dans lesquels vous pouvez utiliser des machines virtuelles avec des conteneurs.</span><span class="sxs-lookup"><span data-stu-id="21075-114">You don’t need to maintain/update/patch VMs, so it is a much better platform for most scenarios where you might be using VMs with containers.</span></span> <span data-ttu-id="21075-115">En utilisant ACI, vous déployez simplement un conteneur, il n’est pas nécessaire de créer un environnement de machine virtuelle que vous venez de déployer.</span><span class="sxs-lookup"><span data-stu-id="21075-115">Using ACI is straight forward, you just deploy a container, there’s no need to create a VM environment you just deploy containers.</span></span>

<span data-ttu-id="21075-116">Les principaux avantages de Azure Container Instances (ACI) sont les suivants:</span><span class="sxs-lookup"><span data-stu-id="21075-116">The main benefits of Azure Container Instances (ACI) are:</span></span>

- <span data-ttu-id="21075-117">Exécuter des conteneurs sans gérer les serveurs</span><span class="sxs-lookup"><span data-stu-id="21075-117">Run containers without managing servers</span></span>
- <span data-ttu-id="21075-118">Améliorez l’agilité avec les conteneurs à la demande</span><span class="sxs-lookup"><span data-stu-id="21075-118">Increase agility with containers on demand</span></span>
- <span data-ttu-id="21075-119">Déployez des conteneurs dans le Cloud avec une simplicité et une rapidité sans précédent, à l’aide d’une seule commande.</span><span class="sxs-lookup"><span data-stu-id="21075-119">Deploy containers to the cloud with unprecedented simplicity and speed—with a single command.</span></span>
- <span data-ttu-id="21075-120">Sécuriser les applications avec l’isolation hyperviseur</span><span class="sxs-lookup"><span data-stu-id="21075-120">Secure applications with hypervisor isolation</span></span>

<span data-ttu-id="21075-121">En bref, avec ACI, vous pouvez développer rapidement des applications sans avoir à gérer des machines virtuelles ou à apprendre de nouveaux outils.</span><span class="sxs-lookup"><span data-stu-id="21075-121">In short, with ACI you can develop apps fast without managing virtual machines or having to learn new tools.</span></span> <span data-ttu-id="21075-122">C’est simplement votre application, dans un conteneur, qui s’exécute dans le Cloud.</span><span class="sxs-lookup"><span data-stu-id="21075-122">It's just your application, in a container, running in the cloud.</span></span>

> [!div class="step-by-step"]
> <span data-ttu-id="21075-123">[Précédent](when-to-deploy-windows-containers-to-azure-vms-iaas-cloud.md)
> [Suivant](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)</span><span class="sxs-lookup"><span data-stu-id="21075-123">[Previous](when-to-deploy-windows-containers-to-azure-vms-iaas-cloud.md)
[Next](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)</span></span>
