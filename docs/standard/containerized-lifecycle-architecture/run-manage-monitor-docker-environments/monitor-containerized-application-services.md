---
title: Superviser des services d’application conteneurisée
description: Découvrir certains aspects essentiels de la supervision des architectures de conteneur
ms.date: 02/15/2019
ms.openlocfilehash: e14553d510751d8a75020a1b6beb9fd7bc29596e
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/13/2019
ms.locfileid: "65641219"
---
# <a name="monitor-containerized-application-services"></a><span data-ttu-id="6950f-103">Superviser des services d’application conteneurisée</span><span class="sxs-lookup"><span data-stu-id="6950f-103">Monitor containerized application services</span></span>

<span data-ttu-id="6950f-104">Il est essentiel pour les applications divisées en plusieurs conteneurs et microservices de disposer d’un moyen de superviser et d’analyser le comportement de l’ensemble de l’application.</span><span class="sxs-lookup"><span data-stu-id="6950f-104">It's critical for applications split into multiple containers and microservices to have a way to monitor and analyze the behavior of the whole application.</span></span>

## <a name="azure-monitor"></a><span data-ttu-id="6950f-105">Azure Monitor</span><span class="sxs-lookup"><span data-stu-id="6950f-105">Azure Monitor</span></span>

<span data-ttu-id="6950f-106">[Azure Monitor](https://azure.microsoft.com/services/monitor/) est un service d’analyse extensible qui supervise votre application dynamique.</span><span class="sxs-lookup"><span data-stu-id="6950f-106">[Azure Monitor](https://azure.microsoft.com/services/monitor/) is an extensible analytics service that monitors your live application.</span></span> <span data-ttu-id="6950f-107">Il vous permet de détecter et de diagnostiquer les problèmes de performances, et de comprendre ce que font les utilisateurs avec votre application.</span><span class="sxs-lookup"><span data-stu-id="6950f-107">It helps you to detect and diagnose performance issues and to understand what users actually do with your app.</span></span> <span data-ttu-id="6950f-108">Il est conçu pour les développeurs, avec l’intention de vous aider à améliorer en permanence les performances et la facilité d’utilisation de vos services ou applications.</span><span class="sxs-lookup"><span data-stu-id="6950f-108">It's designed for developers, with the intent of helping you to continuously improve the performance and usability of your services or applications.</span></span> <span data-ttu-id="6950f-109">Azure Monitor fonctionne à la fois avec le web/les services et les applications autonomes sur un large éventail de plateformes comme .NET, Java, Node.js et de nombreuses autres plateformes, hébergées localement ou dans le cloud.</span><span class="sxs-lookup"><span data-stu-id="6950f-109">Azure Monitor works with both web/services and standalone apps on a wide variety of platforms like .NET, Java, Node.js and many other platforms, hosted on-premises or in the cloud.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="6950f-110">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="6950f-110">Additional resources</span></span>

- <span data-ttu-id="6950f-111">**Vue d’ensemble d’Azure Monitor** </span><span class="sxs-lookup"><span data-stu-id="6950f-111">**Overview of Azure Monitor** </span></span>\
  <https://docs.microsoft.com/azure/azure-monitor/overview>

- <span data-ttu-id="6950f-112">**Présentation d’Application Insights**</span><span class="sxs-lookup"><span data-stu-id="6950f-112">**What is Application Insights?**</span></span> \
  <https://docs.microsoft.com/azure/azure-monitor/app/app-insights-overview>

- <span data-ttu-id="6950f-113">**Que sont les métriques Azure Monitor ?**</span><span class="sxs-lookup"><span data-stu-id="6950f-113">**What is Azure Monitor Metrics?**</span></span> \
  <https://docs.microsoft.com/azure/azure-monitor/platform/data-platform-metrics>

- <span data-ttu-id="6950f-114">**Solution de supervision de conteneurs dans Azure Monitor** </span><span class="sxs-lookup"><span data-stu-id="6950f-114">**Container Monitoring solution in Azure Monitor** </span></span>\
  <https://docs.microsoft.com/azure/azure-monitor/insights/containers>

## <a name="security-and-backup-services"></a><span data-ttu-id="6950f-115">Services de sécurité et de sauvegarde</span><span class="sxs-lookup"><span data-stu-id="6950f-115">Security and backup services</span></span>

<span data-ttu-id="6950f-116">Il existe de nombreuses tâches d’assistance très détaillées que vous devez gérer afin de garantir que vos applications et votre infrastructure sont de haute qualité pour prendre en charge les besoins de l’entreprise. Comme la situation se complique dans le domaine des microservices, vous devez pouvoir disposer de vues aussi bien générales que détaillées quand vous devez prendre des mesures.</span><span class="sxs-lookup"><span data-stu-id="6950f-116">There are many support chores with lots of details that you have to handle to ensure your applications and infrastructure are in top notch condition to support business needs, and the situation becomes more complicated in the microservices realm, so you need a way to have both high-level and detailed views when you need to take action.</span></span>

<span data-ttu-id="6950f-117">Azure propose les outils nécessaires pour gérer et fournir une vue unifiée des quatre aspects essentiels de vos ressources cloud et locales :</span><span class="sxs-lookup"><span data-stu-id="6950f-117">Azure has the tools to manage and provide a unified view of four critical aspects of both your cloud and on-premises resources:</span></span>

- <span data-ttu-id="6950f-118">**Sécurité**.</span><span class="sxs-lookup"><span data-stu-id="6950f-118">**Security**.</span></span> <span data-ttu-id="6950f-119">Avec [Azure Security Center](https://azure.microsoft.com/services/security-center/).</span><span class="sxs-lookup"><span data-stu-id="6950f-119">With [Azure Security Center](https://azure.microsoft.com/services/security-center/).</span></span>
  - <span data-ttu-id="6950f-120">Obtenir une visibilité et un contrôle intégraux sur la sécurité de vos machines virtuelles, applications et charges de travail.</span><span class="sxs-lookup"><span data-stu-id="6950f-120">Get full visibility and control over the security of your virtual machines, apps, and workloads.</span></span>
  - <span data-ttu-id="6950f-121">Centraliser la gestion de vos stratégies de sécurité et intégrer des outils et processus existants.</span><span class="sxs-lookup"><span data-stu-id="6950f-121">Centralize the management of your security policies and integrate existing processes and tools.</span></span>
  - <span data-ttu-id="6950f-122">Détecter les menaces réelles avec l’analytique avancée.</span><span class="sxs-lookup"><span data-stu-id="6950f-122">Detect real threats with advanced analytics.</span></span>

- <span data-ttu-id="6950f-123">**Sauvegarde**.</span><span class="sxs-lookup"><span data-stu-id="6950f-123">**Backup**.</span></span> <span data-ttu-id="6950f-124">Avec la [Sauvegarde Azure](https://azure.microsoft.com/services/backup/).</span><span class="sxs-lookup"><span data-stu-id="6950f-124">With [Azure Backup](https://azure.microsoft.com/services/backup/).</span></span>
  - <span data-ttu-id="6950f-125">Éviter les interruptions d’activité coûteuses, répondre aux objectifs de conformité et protéger vos données contre les ransomwares et les erreurs humaines.</span><span class="sxs-lookup"><span data-stu-id="6950f-125">Avoid costly business disruptions, meet compliance goals, and protect your data against ransomware and human errors.</span></span>
  - <span data-ttu-id="6950f-126">Garder vos données de sauvegarde chiffrées pendant le transit et au repos.</span><span class="sxs-lookup"><span data-stu-id="6950f-126">Keep your backup data encrypted in transit and at rest.</span></span>
  - <span data-ttu-id="6950f-127">Garantir l’accès en fonction de l’authentification multifacteur pour empêcher toute utilisation non autorisée.</span><span class="sxs-lookup"><span data-stu-id="6950f-127">Ensure access based on multifactor authentication to prevent unauthorized use.</span></span>

- <span data-ttu-id="6950f-128">**Ressources locales**.</span><span class="sxs-lookup"><span data-stu-id="6950f-128">**On-premises resources**.</span></span> <span data-ttu-id="6950f-129">Avec [un cloud hybride véritablement cohérent](https://azure.microsoft.com/resources/truly-consistent-hybrid-cloud-with-microsoft-azure/).</span><span class="sxs-lookup"><span data-stu-id="6950f-129">With [a truly consistent hybrid cloud](https://azure.microsoft.com/resources/truly-consistent-hybrid-cloud-with-microsoft-azure/).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="6950f-130">[Précédent](manage-production-docker-environments.md)
>[Suivant](../key-takeaways/index.md)</span><span class="sxs-lookup"><span data-stu-id="6950f-130">[Previous](manage-production-docker-environments.md)
[Next](../key-takeaways/index.md)</span></span>
