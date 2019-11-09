---
title: Scénarios de migration vers le cloud hybride
description: Moderniser des applications .NET existantes avec des conteneurs Cloud et Windows Azure | Migrer vers des scénarios de Cloud hybride
ms.date: 04/30/2018
ms.openlocfilehash: 4348a9b538042fee7ebd9c08f480491f17425937
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/08/2019
ms.locfileid: "72394542"
---
# <a name="migrate-to-hybrid-cloud-scenarios"></a><span data-ttu-id="52950-103">Scénarios de migration vers le cloud hybride</span><span class="sxs-lookup"><span data-stu-id="52950-103">Migrate to hybrid cloud scenarios</span></span>

<span data-ttu-id="52950-104">Certaines organisations et entreprises ne peuvent pas migrer certaines de leurs applications vers des clouds publics comme Microsoft Azure ou tout autre cloud public en raison de réglementations ou de leurs propres stratégies.</span><span class="sxs-lookup"><span data-stu-id="52950-104">Some organizations and enterprises can't migrate some of their applications to public clouds like Microsoft Azure or any other public cloud due to regulations or their own policies.</span></span> <span data-ttu-id="52950-105">Toutefois, il est probable qu’une organisation puisse tirer parti de certaines de ses applications dans le cloud public et d’autres applications locales.</span><span class="sxs-lookup"><span data-stu-id="52950-105">However, it's likely that any organization might benefit from having some of their applications in the public cloud and other applications on-premises.</span></span> <span data-ttu-id="52950-106">Toutefois, un environnement mixte peut entraîner une complexité excessive dans les environnements en raison des différentes plateformes et technologies utilisées dans les clouds publics et les environnements locaux.</span><span class="sxs-lookup"><span data-stu-id="52950-106">But a mixed environment can lead to excessive complexity in environments due to different platforms and technologies used in public clouds versus on-premises environments.</span></span>

<span data-ttu-id="52950-107">Microsoft fournit la meilleure solution de Cloud hybride, dans laquelle vous pouvez optimiser vos ressources existantes localement et dans le cloud public, tout en garantissant la cohérence dans un Cloud hybride Azure.</span><span class="sxs-lookup"><span data-stu-id="52950-107">Microsoft provides the best hybrid cloud solution, one in which you can optimize your existing assets on-premises and in the public cloud, while you ensure consistency in an Azure hybrid cloud.</span></span> <span data-ttu-id="52950-108">Vous pouvez optimiser vos compétences existantes et bénéficier d’une approche unifiée et flexible de la création d’applications qui peuvent s’exécuter dans le Cloud ou localement, grâce à Azure Stack (sur site) et Azure (cloud public).</span><span class="sxs-lookup"><span data-stu-id="52950-108">You can maximize existing skills, and get a flexible, unified approach to building apps that can run in the cloud or on-premises, thanks to Azure Stack (on-premises) and Azure (public cloud).</span></span>

<span data-ttu-id="52950-109">En matière de sécurité, vous pouvez centraliser la gestion et la sécurité dans votre Cloud hybride.</span><span class="sxs-lookup"><span data-stu-id="52950-109">When it comes to security, you can centralize management and security across your hybrid cloud.</span></span> <span data-ttu-id="52950-110">Vous pouvez contrôler toutes les ressources, de votre centre de donnée vers le Cloud, en fournissant une authentification unique aux applications locales et Cloud.</span><span class="sxs-lookup"><span data-stu-id="52950-110">You can get control over all assets, from your datacenter to the cloud, by providing single sign-on to on-premises and cloud apps.</span></span> <span data-ttu-id="52950-111">Pour ce faire, vous étendez Active Directory à un Cloud hybride et à l’aide de la gestion des identités.</span><span class="sxs-lookup"><span data-stu-id="52950-111">You accomplish this by extending Active Directory to a hybrid cloud, and by using identity management.</span></span>

<span data-ttu-id="52950-112">Enfin, vous pouvez distribuer et analyser les données en toute transparence, utiliser les mêmes langages de requête pour les ressources Cloud et locales, et appliquer des analyses et une formation profonde dans Azure pour enrichir vos données, quelle que soit leur source.</span><span class="sxs-lookup"><span data-stu-id="52950-112">Finally, you can distribute and analyze data seamlessly, use the same query languages for cloud and on-premises assets, and apply analytics and deep learning in Azure to enrich your data, regardless of its source.</span></span>

## <a name="azure-stack"></a><span data-ttu-id="52950-113">Azure Stack</span><span class="sxs-lookup"><span data-stu-id="52950-113">Azure Stack</span></span>

<span data-ttu-id="52950-114">Azure Stack est une plateforme Cloud hybride qui vous permet de fournir des services Azure à partir du centre de donnes de votre organisation.</span><span class="sxs-lookup"><span data-stu-id="52950-114">Azure Stack is a hybrid cloud platform that lets you deliver Azure services from your organization's datacenter.</span></span> <span data-ttu-id="52950-115">Azure Stack est conçu pour prendre en charge de nouvelles options pour vos applications modernes dans des scénarios clés, tels que des environnements Edge et non connectés, ou pour répondre à des exigences spécifiques en matière de sécurité et de conformité.</span><span class="sxs-lookup"><span data-stu-id="52950-115">Azure Stack is designed to support new options for your modern applications in key scenarios, like edge and unconnected environments, or meeting specific security and compliance requirements.</span></span>

<span data-ttu-id="52950-116">La figure 4-13 montre une vue d’ensemble de la véritable plateforme Cloud hybride offerte par Microsoft.</span><span class="sxs-lookup"><span data-stu-id="52950-116">Figure 4-13 shows an overview of the true hybrid cloud platform that Microsoft offers.</span></span>

![Diagramme de la plateforme Cloud hybride Microsoft avec Azure Stack et Azure.](./media/migrate-to-hybrid-cloud-scenarios/microsoft-hybrid-cloud-platform.png)

<span data-ttu-id="52950-118">**Figure 4-13.**</span><span class="sxs-lookup"><span data-stu-id="52950-118">**Figure 4-13.**</span></span> <span data-ttu-id="52950-119">Plateforme Cloud hybride Microsoft avec Azure Stack et Azure</span><span class="sxs-lookup"><span data-stu-id="52950-119">Microsoft hybrid cloud platform with Azure Stack and Azure</span></span>

<span data-ttu-id="52950-120">Azure Stack est proposé dans deux options de déploiement pour répondre à vos besoins :</span><span class="sxs-lookup"><span data-stu-id="52950-120">Azure Stack is offered in two deployment options, to meet your needs:</span></span>

- <span data-ttu-id="52950-121">Systèmes intégrés Azure Stack</span><span class="sxs-lookup"><span data-stu-id="52950-121">Azure Stack integrated systems</span></span>

- <span data-ttu-id="52950-122">Kit de développement Azure Stack</span><span class="sxs-lookup"><span data-stu-id="52950-122">Azure Stack Development Kit</span></span>

### <a name="azure-stack-integrated-systems"></a><span data-ttu-id="52950-123">Systèmes intégrés Azure Stack</span><span class="sxs-lookup"><span data-stu-id="52950-123">Azure Stack integrated systems</span></span>

<span data-ttu-id="52950-124">Azure Stack systèmes intégrés sont proposés par le biais d’un partenariat entre Microsoft et des partenaires matériels.</span><span class="sxs-lookup"><span data-stu-id="52950-124">Azure Stack integrated systems are offered through a partnership of Microsoft and hardware partners.</span></span> <span data-ttu-id="52950-125">Le partenariat crée une solution qui offre une innovation à l’rythme du Cloud qui est équilibrée par la simplicité de la gestion.</span><span class="sxs-lookup"><span data-stu-id="52950-125">The partnership creates a solution that offers cloud-paced innovation that is balanced with simplicity in management.</span></span> <span data-ttu-id="52950-126">Étant donné que Azure Stack est proposé en tant que système intégré de matériel et de logiciels, vous bénéficiez de la flexibilité et du contrôle appropriés, tout en adoptant l’innovation à partir du Cloud.</span><span class="sxs-lookup"><span data-stu-id="52950-126">Because Azure Stack is offered as an integrated system of hardware and software, you get the right amount of flexibility and control, while still adopting innovation from the cloud.</span></span> <span data-ttu-id="52950-127">Azure Stack systèmes intégrés ont une taille comprise entre 4 et 12 nœuds et sont pris en charge conjointement par le partenaire matériel et Microsoft.</span><span class="sxs-lookup"><span data-stu-id="52950-127">Azure Stack integrated systems range in size from 4 to 12 nodes, and are jointly supported by the hardware partner and Microsoft.</span></span> <span data-ttu-id="52950-128">Utilisez Azure Stack systèmes intégrés pour implémenter de nouveaux scénarios pour vos charges de travail de production.</span><span class="sxs-lookup"><span data-stu-id="52950-128">Use Azure Stack integrated systems to implement new scenarios for your production workloads.</span></span>

### <a name="azure-stack-development-kit"></a><span data-ttu-id="52950-129">Kit de développement Azure Stack</span><span class="sxs-lookup"><span data-stu-id="52950-129">Azure Stack Development Kit</span></span>

<span data-ttu-id="52950-130">Microsoft Azure Stack Kit de développement est un déploiement à un seul nœud de Azure Stack, que vous pouvez utiliser pour évaluer et découvrir les Azure Stack.</span><span class="sxs-lookup"><span data-stu-id="52950-130">Microsoft Azure Stack Development Kit is a single-node deployment of Azure Stack, which you can use to evaluate and learn about Azure Stack.</span></span> <span data-ttu-id="52950-131">Vous pouvez également utiliser Kit de développement Azure Stack en tant qu’environnement de développement, où vous pouvez développer à l’aide d’API et d’outils qui sont cohérents avec Azure.</span><span class="sxs-lookup"><span data-stu-id="52950-131">You can also use Azure Stack Development Kit as a developer environment, where you can develop using APIs and tooling that are consistent with Azure.</span></span> <span data-ttu-id="52950-132">Kit de développement Azure Stack n’est pas destiné à être utilisé en tant qu’environnement de production.</span><span class="sxs-lookup"><span data-stu-id="52950-132">Azure Stack Development Kit is not intended to be used as a production environment.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="52950-133">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="52950-133">Additional resources</span></span>

- <span data-ttu-id="52950-134">**Cloud hybride Azure**</span><span class="sxs-lookup"><span data-stu-id="52950-134">**Azure hybrid cloud**</span></span>

    <https://azure.microsoft.com/overview/hybrid-cloud/>

- <span data-ttu-id="52950-135">**Azure Stack**</span><span class="sxs-lookup"><span data-stu-id="52950-135">**Azure Stack**</span></span>

    <https://azure.microsoft.com/overview/azure-stack/>

- <span data-ttu-id="52950-136">**Active Directory les comptes de service pour les conteneurs Windows**</span><span class="sxs-lookup"><span data-stu-id="52950-136">**Active Directory Service Accounts for Windows Containers**</span></span>

    <https://docs.microsoft.com/virtualization/windowscontainers/manage-containers/manage-serviceaccounts>

- <span data-ttu-id="52950-137">**Créer un conteneur avec prise en charge de Active Directory**</span><span class="sxs-lookup"><span data-stu-id="52950-137">**Create a container with Active Directory support**</span></span>

    <https://blogs.msdn.microsoft.com/containerstuff/2017/01/30/create-a-container-with-active-directory-support/>

- <span data-ttu-id="52950-138">**Licences Azure Hybrid Benefit**</span><span class="sxs-lookup"><span data-stu-id="52950-138">**Azure Hybrid Benefit licensing**</span></span>

    <https://azure.microsoft.com/pricing/hybrid-benefit/>

>[!div class="step-by-step"]
><span data-ttu-id="52950-139">[Précédent](life-cycle-ci-cd-pipelines-devops-tools.md)
>[Suivant](../walkthroughs-technical-get-started-overview.md)</span><span class="sxs-lookup"><span data-stu-id="52950-139">[Previous](life-cycle-ci-cd-pipelines-devops-tools.md)
[Next](../walkthroughs-technical-get-started-overview.md)</span></span>
