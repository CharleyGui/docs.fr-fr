---
title: Scénarios de migration vers le cloud hybride
description: Moderniser les applications .NET existantes avec les conteneurs Azure Cloud et Windows (fr) Migrer vers des scénarios de cloud hybrides
ms.date: 04/30/2018
ms.openlocfilehash: dcbb799a45609f8bb811866c4041951abf1fda8b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937361"
---
# <a name="migrate-to-hybrid-cloud-scenarios"></a><span data-ttu-id="8aa30-103">Scénarios de migration vers le cloud hybride</span><span class="sxs-lookup"><span data-stu-id="8aa30-103">Migrate to hybrid cloud scenarios</span></span>

<span data-ttu-id="8aa30-104">Certaines organisations et entreprises ne peuvent pas migrer certaines de leurs applications vers des nuages publics comme Microsoft Azure ou tout autre cloud public en raison de la réglementation ou de leurs propres politiques.</span><span class="sxs-lookup"><span data-stu-id="8aa30-104">Some organizations and enterprises can't migrate some of their applications to public clouds like Microsoft Azure or any other public cloud due to regulations or their own policies.</span></span> <span data-ttu-id="8aa30-105">Cependant, il est probable que n’importe quelle organisation pourrait bénéficier d’avoir certaines de leurs applications dans le cloud public et d’autres applications sur place.</span><span class="sxs-lookup"><span data-stu-id="8aa30-105">However, it's likely that any organization might benefit from having some of their applications in the public cloud and other applications on-premises.</span></span> <span data-ttu-id="8aa30-106">Mais un environnement mixte peut conduire à une complexité excessive dans les environnements en raison de différentes plates-formes et technologies utilisées dans les nuages publics par rapport aux environnements sur place.</span><span class="sxs-lookup"><span data-stu-id="8aa30-106">But a mixed environment can lead to excessive complexity in environments due to different platforms and technologies used in public clouds versus on-premises environments.</span></span>

<span data-ttu-id="8aa30-107">Microsoft fournit la meilleure solution de cloud hybride, dans laquelle vous pouvez optimiser vos actifs existants sur place et dans le cloud public, tandis que vous assurez la cohérence dans un nuage hybride Azure.</span><span class="sxs-lookup"><span data-stu-id="8aa30-107">Microsoft provides the best hybrid cloud solution, one in which you can optimize your existing assets on-premises and in the public cloud, while you ensure consistency in an Azure hybrid cloud.</span></span> <span data-ttu-id="8aa30-108">Vous pouvez maximiser les compétences existantes et obtenir une approche flexible et unifiée pour construire des applications qui peuvent s’exécuter dans le cloud ou sur place, grâce à Azure Stack (sur place) et Azure (nuage public).</span><span class="sxs-lookup"><span data-stu-id="8aa30-108">You can maximize existing skills, and get a flexible, unified approach to building apps that can run in the cloud or on-premises, thanks to Azure Stack (on-premises) and Azure (public cloud).</span></span>

<span data-ttu-id="8aa30-109">En matière de sécurité, vous pouvez centraliser la gestion et la sécurité à travers votre cloud hybride.</span><span class="sxs-lookup"><span data-stu-id="8aa30-109">When it comes to security, you can centralize management and security across your hybrid cloud.</span></span> <span data-ttu-id="8aa30-110">Vous pouvez obtenir le contrôle de tous les actifs, de votre centre de données au cloud, en fournissant un seul signe sur les sites et les applications cloud.</span><span class="sxs-lookup"><span data-stu-id="8aa30-110">You can get control over all assets, from your datacenter to the cloud, by providing single sign-on to on-premises and cloud apps.</span></span> <span data-ttu-id="8aa30-111">Pour ce faire, vous étendez Active Directory à un cloud hybride et en utilisant la gestion de l’identité.</span><span class="sxs-lookup"><span data-stu-id="8aa30-111">You accomplish this by extending Active Directory to a hybrid cloud, and by using identity management.</span></span>

<span data-ttu-id="8aa30-112">Enfin, vous pouvez distribuer et analyser les données de manière transparente, utiliser les mêmes langages de requête pour les ressources cloud et sur site, et appliquer l’analyse et l’apprentissage profond en Azure pour enrichir vos données, quelle que soit leur source.</span><span class="sxs-lookup"><span data-stu-id="8aa30-112">Finally, you can distribute and analyze data seamlessly, use the same query languages for cloud and on-premises assets, and apply analytics and deep learning in Azure to enrich your data, regardless of its source.</span></span>

## <a name="azure-stack"></a><span data-ttu-id="8aa30-113">Azure Stack</span><span class="sxs-lookup"><span data-stu-id="8aa30-113">Azure Stack</span></span>

<span data-ttu-id="8aa30-114">Azure Stack est une plate-forme cloud hybride qui vous permet de fournir des services Azure à partir du centre de données de votre organisation.</span><span class="sxs-lookup"><span data-stu-id="8aa30-114">Azure Stack is a hybrid cloud platform that lets you deliver Azure services from your organization's datacenter.</span></span> <span data-ttu-id="8aa30-115">Azure Stack est conçu pour prendre en charge de nouvelles options pour vos applications modernes dans des scénarios clés, comme les environnements de bord et non connectés, ou répondre à des exigences spécifiques en matière de sécurité et de conformité.</span><span class="sxs-lookup"><span data-stu-id="8aa30-115">Azure Stack is designed to support new options for your modern applications in key scenarios, like edge and unconnected environments, or meeting specific security and compliance requirements.</span></span>

<span data-ttu-id="8aa30-116">La figure 4-13 montre un aperçu de la véritable plate-forme de cloud hybride que Microsoft offre.</span><span class="sxs-lookup"><span data-stu-id="8aa30-116">Figure 4-13 shows an overview of the true hybrid cloud platform that Microsoft offers.</span></span>

![Diagramme de la plate-forme cloud hybride Microsoft avec Azure Stack et Azure.](./media/migrate-to-hybrid-cloud-scenarios/microsoft-hybrid-cloud-platform.png)

<span data-ttu-id="8aa30-118">**Figure 4-13.**</span><span class="sxs-lookup"><span data-stu-id="8aa30-118">**Figure 4-13.**</span></span> <span data-ttu-id="8aa30-119">Plateforme cloud hybride Microsoft avec Azure Stack et Azure</span><span class="sxs-lookup"><span data-stu-id="8aa30-119">Microsoft hybrid cloud platform with Azure Stack and Azure</span></span>

<span data-ttu-id="8aa30-120">Azure Stack est proposé en deux options de déploiement, pour répondre à vos besoins :</span><span class="sxs-lookup"><span data-stu-id="8aa30-120">Azure Stack is offered in two deployment options, to meet your needs:</span></span>

- <span data-ttu-id="8aa30-121">Systèmes intégrés Azure Stack</span><span class="sxs-lookup"><span data-stu-id="8aa30-121">Azure Stack integrated systems</span></span>

- <span data-ttu-id="8aa30-122">Kit de développement Azure Stack</span><span class="sxs-lookup"><span data-stu-id="8aa30-122">Azure Stack Development Kit</span></span>

### <a name="azure-stack-integrated-systems"></a><span data-ttu-id="8aa30-123">Systèmes intégrés Azure Stack</span><span class="sxs-lookup"><span data-stu-id="8aa30-123">Azure Stack integrated systems</span></span>

<span data-ttu-id="8aa30-124">Les systèmes intégrés Azure Stack sont proposés par le biais d’un partenariat entre Microsoft et des partenaires matériels.</span><span class="sxs-lookup"><span data-stu-id="8aa30-124">Azure Stack integrated systems are offered through a partnership of Microsoft and hardware partners.</span></span> <span data-ttu-id="8aa30-125">Le partenariat crée une solution qui offre une innovation au rythme cloud qui est équilibrée avec simplicité dans la gestion.</span><span class="sxs-lookup"><span data-stu-id="8aa30-125">The partnership creates a solution that offers cloud-paced innovation that is balanced with simplicity in management.</span></span> <span data-ttu-id="8aa30-126">Azure Stack étant proposé en tant que système intégré de matériels et de logiciels, vous bénéficiez de la flexibilité et du contrôle adéquats, tout en adoptant l’innovation propre au cloud.</span><span class="sxs-lookup"><span data-stu-id="8aa30-126">Because Azure Stack is offered as an integrated system of hardware and software, you get the right amount of flexibility and control, while still adopting innovation from the cloud.</span></span> <span data-ttu-id="8aa30-127">Les systèmes intégrés Azure Stack varient en taille de 4 à 12 nœuds, et sont pris en charge conjointement par le partenaire matériel et Microsoft.</span><span class="sxs-lookup"><span data-stu-id="8aa30-127">Azure Stack integrated systems range in size from 4 to 12 nodes, and are jointly supported by the hardware partner and Microsoft.</span></span> <span data-ttu-id="8aa30-128">Utilisez les systèmes intégrés Azure Stack pour implémenter de nouveaux scénarios pour votre charge de travail de production.</span><span class="sxs-lookup"><span data-stu-id="8aa30-128">Use Azure Stack integrated systems to implement new scenarios for your production workloads.</span></span>

### <a name="azure-stack-development-kit"></a><span data-ttu-id="8aa30-129">Kit de développement Azure Stack</span><span class="sxs-lookup"><span data-stu-id="8aa30-129">Azure Stack Development Kit</span></span>

<span data-ttu-id="8aa30-130">Le Kit de développement Microsoft Azure Stack est un déploiement à un seul nœud d’Azure Stack qui vous permet de découvrir et d’évaluer Azure Stack.</span><span class="sxs-lookup"><span data-stu-id="8aa30-130">Microsoft Azure Stack Development Kit is a single-node deployment of Azure Stack, which you can use to evaluate and learn about Azure Stack.</span></span> <span data-ttu-id="8aa30-131">Vous pouvez également utiliser Azure Stack Development Kit en tant qu’environnement de développeur, où vous pouvez développer à l’aide d’API et d’outillage qui sont compatibles avec Azure.</span><span class="sxs-lookup"><span data-stu-id="8aa30-131">You can also use Azure Stack Development Kit as a developer environment, where you can develop using APIs and tooling that are consistent with Azure.</span></span> <span data-ttu-id="8aa30-132">Le Kit de développement Azure Stack n’est pas destiné à être utilisé en tant qu’environnement de production.</span><span class="sxs-lookup"><span data-stu-id="8aa30-132">Azure Stack Development Kit is not intended to be used as a production environment.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="8aa30-133">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="8aa30-133">Additional resources</span></span>

- <span data-ttu-id="8aa30-134">**Nuage hybride Azure**</span><span class="sxs-lookup"><span data-stu-id="8aa30-134">**Azure hybrid cloud**</span></span>

    <https://azure.microsoft.com/overview/hybrid-cloud/>

- <span data-ttu-id="8aa30-135">**Pile Azure**</span><span class="sxs-lookup"><span data-stu-id="8aa30-135">**Azure Stack**</span></span>

    <https://azure.microsoft.com/overview/azure-stack/>

- <span data-ttu-id="8aa30-136">**Comptes de service Active Directory pour les conteneurs Windows**</span><span class="sxs-lookup"><span data-stu-id="8aa30-136">**Active Directory Service Accounts for Windows Containers**</span></span>

    <https://docs.microsoft.com/virtualization/windowscontainers/manage-containers/manage-serviceaccounts>

- <span data-ttu-id="8aa30-137">**Créer un conteneur avec le support d’annuaire actif**</span><span class="sxs-lookup"><span data-stu-id="8aa30-137">**Create a container with Active Directory support**</span></span>

    <https://docs.microsoft.com/archive/blogs/containerstuff/create-a-container-with-active-directory-support>

- <span data-ttu-id="8aa30-138">**Licence Azure Hybrid Benefit**</span><span class="sxs-lookup"><span data-stu-id="8aa30-138">**Azure Hybrid Benefit licensing**</span></span>

    <https://azure.microsoft.com/pricing/hybrid-benefit/>

>[!div class="step-by-step"]
><span data-ttu-id="8aa30-139">[Suivant précédent](life-cycle-ci-cd-pipelines-devops-tools.md)
>[Next](../walkthroughs-technical-get-started-overview.md)</span><span class="sxs-lookup"><span data-stu-id="8aa30-139">[Previous](life-cycle-ci-cd-pipelines-devops-tools.md)
[Next](../walkthroughs-technical-get-started-overview.md)</span></span>
