---
title: Procédures pas à pas et vue d’ensemble technique pour le démarrage
description: Moderniser des Applications .NET existantes avec le Cloud Azure et les conteneurs Windows | Procédures pas à pas et technique obtenir vue d’ensemble de prise en main
ms.date: 04/28/2018
ms.openlocfilehash: 0b0dbae999e31150a55368d669f718eea0925d51
ms.sourcegitcommit: 904b98d8d706f0e2d5ceaa00ce17ffbd92adfb88
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66758789"
---
# <a name="walkthroughs-and-technical-get-started-overview"></a><span data-ttu-id="ff335-103">Procédures pas à pas et vue d’ensemble technique pour le démarrage</span><span class="sxs-lookup"><span data-stu-id="ff335-103">Walkthroughs and technical get started overview</span></span>

<span data-ttu-id="ff335-104">Pour limiter la taille de ce livre électronique, documentation technique supplémentaire et les procédures pas à pas complète étaient mis à disposition dans un référentiel GitHub.</span><span class="sxs-lookup"><span data-stu-id="ff335-104">To limit the size of this e-book, additional technical documentation and the full walkthroughs were made available in a GitHub repository.</span></span> <span data-ttu-id="ff335-105">La série en ligne des procédures pas à pas qui est décrite dans ce chapitre décrit la configuration pas à pas des environnements multiples qui reposent sur les conteneurs Windows et le déploiement sur Azure.</span><span class="sxs-lookup"><span data-stu-id="ff335-105">The online series of walkthroughs that is described in this chapter covers the step-by-step setup of the multiple environments that are based on Windows Containers, and deployment to Azure.</span></span>

<span data-ttu-id="ff335-106">Les sections suivantes expliquent ce que chaque procédure pas à pas concerne, ses objectifs et la vision de haut niveau et fournit un diagramme des tâches qui sont impliqués.</span><span class="sxs-lookup"><span data-stu-id="ff335-106">The following sections explain what each walkthrough is about, its objectives and high-level vision, and provides a diagram of the tasks that are involved.</span></span> <span data-ttu-id="ff335-107">Vous pouvez obtenir les procédures pas à pas eux-mêmes dans le *eShopModernizing* applications wiki de référentiel GitHub à <https://github.com/dotnet-architecture/eShopModernizing/wiki>.</span><span class="sxs-lookup"><span data-stu-id="ff335-107">You can get the walkthroughs themselves in the *eShopModernizing* apps GitHub repo wiki at <https://github.com/dotnet-architecture/eShopModernizing/wiki>.</span></span>

## <a name="technical-walkthrough-list"></a><span data-ttu-id="ff335-108">Liste de présentation technique</span><span class="sxs-lookup"><span data-stu-id="ff335-108">Technical walkthrough list</span></span>

<span data-ttu-id="ff335-109">Les procédures de prise en main suivantes fournissent des conseils techniques cohérente et complète pour les exemples d’applications que vous pouvez de courbes d’élévation et shift en utilisant des conteneurs et ensuite déplacer à l’aide de plusieurs options de déploiement dans Azure.</span><span class="sxs-lookup"><span data-stu-id="ff335-109">The following get-started walkthroughs provide consistent and comprehensive technical guidance for sample apps that you can lift and shift by using containers, and then move by using multiple deployment choices in Azure.</span></span>

<span data-ttu-id="ff335-110">Chacune des procédures suivantes utilise les nouveaux exemples eShopLegacy et eShopModernizing d’applications, qui sont disponibles sur GitHub à l’adresse <https://github.com/dotnet-architecture/eShopModernizing>.</span><span class="sxs-lookup"><span data-stu-id="ff335-110">Each of the following walkthroughs uses the new sample eShopLegacy and eShopModernizing apps, which are available on GitHub at <https://github.com/dotnet-architecture/eShopModernizing>.</span></span>

- <span data-ttu-id="ff335-111">**Visite guidée d’eShop les applications héritées (applications de ligne de base à moderniser)**</span><span class="sxs-lookup"><span data-stu-id="ff335-111">**Tour of eShop legacy apps (baseline apps to modernize)**</span></span>

- <span data-ttu-id="ff335-112">**Conteneurisez vos applications web ASP.NET existantes (Web Forms et MVC) avec les conteneurs Windows**</span><span class="sxs-lookup"><span data-stu-id="ff335-112">**Containerize your existing ASP.NET web apps (WebForms & MVC) with Windows Containers**</span></span>

- <span data-ttu-id="ff335-113">**Conteneuriser vos services WCF existants (applications multicouches) avec les conteneurs Windows**</span><span class="sxs-lookup"><span data-stu-id="ff335-113">**Containerize your existing WCF services (N-Tier apps) with Windows Containers**</span></span>

- <span data-ttu-id="ff335-114">**Déployer votre application basée sur des conteneurs sur Windows sur les machines virtuelles Azure**</span><span class="sxs-lookup"><span data-stu-id="ff335-114">**Deploy your Windows Containers-based app to Azure VMs**</span></span>

- <span data-ttu-id="ff335-115">**Déployer vos applications de conteneurs Windows sur Kubernetes dans Azure Container Service**</span><span class="sxs-lookup"><span data-stu-id="ff335-115">**Deploy your Windows Containers-based apps to Kubernetes in Azure Container Service**</span></span>

## <a name="walkthrough-1-tour-of-eshop-legacy-apps"></a><span data-ttu-id="ff335-116">Procédure pas à pas 1 : Visite guidée des applications héritées eShop</span><span class="sxs-lookup"><span data-stu-id="ff335-116">Walkthrough 1: Tour of eShop legacy apps</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="ff335-117">Disponibilité de la procédure pas à pas techniques</span><span class="sxs-lookup"><span data-stu-id="ff335-117">Technical walkthrough availability</span></span>

<span data-ttu-id="ff335-118">La procédure pas à pas technique complète est disponible dans le wiki de référentiel GitHub eShopModernizing :</span><span class="sxs-lookup"><span data-stu-id="ff335-118">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

[<span data-ttu-id="ff335-119">eShopModernizing wiki walkthroughs</span><span class="sxs-lookup"><span data-stu-id="ff335-119">eShopModernizing wiki walkthroughs</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki)

### <a name="overview"></a><span data-ttu-id="ff335-120">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="ff335-120">Overview</span></span>

<span data-ttu-id="ff335-121">Dans cette procédure pas à pas, vous pouvez explorer l’implémentation initiale de trois exemples d’applications héritées.</span><span class="sxs-lookup"><span data-stu-id="ff335-121">In this walkthrough, you can explore the initial implementation of three sample legacy applications.</span></span> <span data-ttu-id="ff335-122">Les deux premiers exemples d’applications web ont une architecture monolithique et ont été créés à l’aide d’ASP.NET classique.</span><span class="sxs-lookup"><span data-stu-id="ff335-122">The first two sample web apps have a monolithic architecture, and were created by using classic ASP.NET.</span></span> <span data-ttu-id="ff335-123">Une application est basée sur ASP.NET 4.x MVC ; la deuxième application repose sur les Web Forms ASP.NET 4.x.</span><span class="sxs-lookup"><span data-stu-id="ff335-123">One application is based on ASP.NET 4.x MVC; the second application is based on ASP.NET 4.x Web Forms.</span></span>
<span data-ttu-id="ff335-124">L’application de tiers est une application à 3 couches composée par une application WinForms de client et une côté serveur [Windows Communication Foundation (WCF)](../../framework/wcf/whats-wcf.md) service.</span><span class="sxs-lookup"><span data-stu-id="ff335-124">The third app is a 3-Tier app composed by a client WinForms app and a server-side [Windows Communication Foundation (WCF)](../../framework/wcf/whats-wcf.md) service.</span></span>

<span data-ttu-id="ff335-125">Toutes ces applications sont disponibles sur le [eShopModernizing GitHub référentiel](https://github.com/dotnet-architecture/eShopModernizing).</span><span class="sxs-lookup"><span data-stu-id="ff335-125">All these applications are available at the [eShopModernizing GitHub repo](https://github.com/dotnet-architecture/eShopModernizing).</span></span>

### <a name="goals"></a><span data-ttu-id="ff335-126">Objectifs</span><span class="sxs-lookup"><span data-stu-id="ff335-126">Goals</span></span>

<span data-ttu-id="ff335-127">L’objectif principal de cette procédure pas à pas consiste simplement à vous familiariser avec ces applications et avec leur code et la configuration.</span><span class="sxs-lookup"><span data-stu-id="ff335-127">The main goal of this walkthrough is simply to get familiar with these apps, and with their code and configuration.</span></span> <span data-ttu-id="ff335-128">Vous pouvez configurer les applications afin qu’ils génèrent et utilisent des données fictives, sans l’aide de la base de données SQL, à des fins de test.</span><span class="sxs-lookup"><span data-stu-id="ff335-128">You can configure the apps so that they generate and use mock data, without using the SQL database, for testing purposes.</span></span> <span data-ttu-id="ff335-129">Cette configuration facultative est basée sur l’injection de dépendance, d’une manière découplée.</span><span class="sxs-lookup"><span data-stu-id="ff335-129">This optional config is based on dependency injection, in a decoupled way.</span></span>

### <a name="scenario-1-aspnet-web-apps"></a><span data-ttu-id="ff335-130">Scénario 1 : Applications Web ASP.NET</span><span class="sxs-lookup"><span data-stu-id="ff335-130">Scenario 1: ASP.NET Web apps</span></span>

<span data-ttu-id="ff335-131">La figure ci-dessous illustre un scénario simple des applications web ASP.NET hérités d’origine.</span><span class="sxs-lookup"><span data-stu-id="ff335-131">The figure below shows the simple scenario of the original legacy ASP.NET web applications.</span></span>

![Scénario d’architecture simple des applications web ASP.NET héritées d’origine](./media/image5-1.png)

<span data-ttu-id="ff335-133">À partir d’un point de vue commercial domaine, les deux applications offrent le même catalogue de fonctionnalités de gestion.</span><span class="sxs-lookup"><span data-stu-id="ff335-133">From a business domain perspective, both apps offer the same catalog management features.</span></span> <span data-ttu-id="ff335-134">Membres de l’équipe d’enterprise eShop peut utiliser l’application pour afficher et modifier le catalogue de produits.</span><span class="sxs-lookup"><span data-stu-id="ff335-134">Members of the eShop enterprise team would use the app to view and edit the product catalog.</span></span>

<span data-ttu-id="ff335-135">La figure suivante montre les captures d’écran de l’application initiale.</span><span class="sxs-lookup"><span data-stu-id="ff335-135">The next figure shows the initial app screenshots.</span></span>

![Applications ASP.NET MVC et Web Forms ASP.NET (technologies existantes/héritées)](./media/image5-2.png)

<span data-ttu-id="ff335-137">Dépendances dans ASP.NET 4.x ou une version antérieure (soit pour MVC ou Web Forms) signifie que ces applications ne s’exécute pas sur .NET Core, sauf si le code est entièrement réécrit à l’aide d’ASP.NET Core MVC.</span><span class="sxs-lookup"><span data-stu-id="ff335-137">Dependencies in ASP.NET 4.x or earlier versions (either for MVC or for Web Forms) means that these applications won’t run on .NET Core unless the code is fully rewritten by using ASP.NET Core MVC.</span></span>

### <a name="scenario-2-wcf-service-and-winforms-client-app-3-tier-app"></a><span data-ttu-id="ff335-138">Scénario 2 : Service WCF et WinForms client application (application de niveau 3)</span><span class="sxs-lookup"><span data-stu-id="ff335-138">Scenario 2: WCF service and WinForms client app (3-Tier app)</span></span>

<span data-ttu-id="ff335-139">La figure ci-dessous illustre un scénario simple de l’application héritée à 3 couches d’origine.</span><span class="sxs-lookup"><span data-stu-id="ff335-139">The figure below shows the simple scenario of the original 3-Tier legacy application.</span></span>

![Scénario d’architecture simple de l’application à 3 couches héritée d’origine avec un service WCF et d’une application cliente de WinForms](./media/image5-1.5.png)

### <a name="benefits"></a><span data-ttu-id="ff335-141">Avantages</span><span class="sxs-lookup"><span data-stu-id="ff335-141">Benefits</span></span>

<span data-ttu-id="ff335-142">Les avantages de cette procédure pas à pas sont simples : Simplement vous familiariser avec le code et les applications initiales.</span><span class="sxs-lookup"><span data-stu-id="ff335-142">The benefits of this walkthrough are simple: Just get familiar with the code and initial apps.</span></span>

### <a name="next-steps"></a><span data-ttu-id="ff335-143">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="ff335-143">Next steps</span></span>

<span data-ttu-id="ff335-144">Explorez ce contenu plus approfondi sur le wiki GitHub :</span><span class="sxs-lookup"><span data-stu-id="ff335-144">Explore this content more in-depth on the GitHub wiki:</span></span>

- [<span data-ttu-id="ff335-145">Visite guidée sur la ligne de base ASP.NET MVC et les applications Web Forms « héritées »</span><span class="sxs-lookup"><span data-stu-id="ff335-145">Tour on the baseline ASP.NET MVC and Web Forms “legacy” apps</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/01.-Tour-on-the-ASP.NET-MVC-and-WebForms-apps-implementation-code)
- [<span data-ttu-id="ff335-146">Visite sur le service WCF de base et l’application « héritée » de WinForms (niveau 3)</span><span class="sxs-lookup"><span data-stu-id="ff335-146">Tour on the baseline WCF service and WinForms (3-Tier) “legacy” app</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/21.-Tour-on-the-WCF-service-and-WinForms-apps)

## <a name="walkthrough-2-containerize-your-existing-net-applications-with-windows-containers"></a><span data-ttu-id="ff335-147">Procédure pas à pas 2 : Conteneurisez vos applications .NET existantes avec les conteneurs Windows</span><span class="sxs-lookup"><span data-stu-id="ff335-147">Walkthrough 2: Containerize your existing .NET applications with Windows Containers</span></span>

### <a name="overview"></a><span data-ttu-id="ff335-148">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="ff335-148">Overview</span></span>

<span data-ttu-id="ff335-149">Utiliser les conteneurs Windows pour améliorer le déploiement des applications .NET existantes, comme celles basées sur MVC, Web Forms ou WCF, à des environnements de test, de développement et de production.</span><span class="sxs-lookup"><span data-stu-id="ff335-149">Use Windows Containers to improve deployment of existing .NET applications, like those based on MVC, Web Forms, or WCF, to production, development, and test environments.</span></span>

### <a name="goals"></a><span data-ttu-id="ff335-150">Objectifs</span><span class="sxs-lookup"><span data-stu-id="ff335-150">Goals</span></span>

<span data-ttu-id="ff335-151">L’objectif de cette procédure pas à pas est de vous montrer plusieurs options pour conteneuriser une application .NET Framework existante.</span><span class="sxs-lookup"><span data-stu-id="ff335-151">The goal of this walkthrough is to show you several options for containerizing an existing .NET Framework application.</span></span> <span data-ttu-id="ff335-152">Vous pouvez :</span><span class="sxs-lookup"><span data-stu-id="ff335-152">You can:</span></span>

- <span data-ttu-id="ff335-153">Conteneurisez votre application à l’aide de [Visual Studio 2017 Tools pour Docker](/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker) (Visual Studio 2017 ou versions ultérieures).</span><span class="sxs-lookup"><span data-stu-id="ff335-153">Containerize your application by using [Visual Studio 2017 Tools for Docker](/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker) (Visual Studio 2017 or later versions).</span></span>

- <span data-ttu-id="ff335-154">Conteneurisez votre application en ajoutant manuellement un [Dockerfile](https://docs.docker.com/engine/reference/builder/), puis en utilisant le [Docker CLI](https://docs.docker.com/engine/reference/commandline/cli/).</span><span class="sxs-lookup"><span data-stu-id="ff335-154">Containerize your application by manually adding a [Dockerfile](https://docs.docker.com/engine/reference/builder/), and then using the [Docker CLI](https://docs.docker.com/engine/reference/commandline/cli/).</span></span>

- <span data-ttu-id="ff335-155">Conteneurisez votre application à l’aide de la [Img2Docker](https://github.com/docker/communitytools-image2docker-win) outil (outil open source à partir de Docker).</span><span class="sxs-lookup"><span data-stu-id="ff335-155">Containerize your application by using the [Img2Docker](https://github.com/docker/communitytools-image2docker-win) tool (an open-source tool from Docker).</span></span>

<span data-ttu-id="ff335-156">Cette procédure pas à pas se concentre sur Visual Studio 2017 Tools pour l’approche de Docker, mais les deux autres approches sont assez similaires en ce qui concerne l’utilisation des fichiers Dockerfile.</span><span class="sxs-lookup"><span data-stu-id="ff335-156">This walkthrough focuses on the Visual Studio 2017 Tools for Docker approach, but the other two approaches are fairly similar in regard to using Dockerfiles.</span></span>

### <a name="scenario-1-containerized-aspnet-web-apps"></a><span data-ttu-id="ff335-157">Scénario 1 : Applications web ASP.NET en conteneur</span><span class="sxs-lookup"><span data-stu-id="ff335-157">Scenario 1: Containerized ASP.NET web apps</span></span>

<span data-ttu-id="ff335-158">Figure ci-dessous illustre le scénario pour les applications d’applications en conteneur eShop web héritées.</span><span class="sxs-lookup"><span data-stu-id="ff335-158">Figure below shows the scenario for containerized eShop legacy web apps applications.</span></span>

![Diagramme d’architecture simplifiée en conteneur dans un environnement de développement des applications ASP.NET](./media/image5-3.png)

### <a name="scenario-2-containerized-wcf-service"></a><span data-ttu-id="ff335-160">Scénario 2 : Service WCF en conteneur</span><span class="sxs-lookup"><span data-stu-id="ff335-160">Scenario 2: Containerized WCF service</span></span>

<span data-ttu-id="ff335-161">La figure ci-dessous illustre le scénario pour une application à 3 niveaux avec un service WCF en conteneur.</span><span class="sxs-lookup"><span data-stu-id="ff335-161">Figure below shows the scenario for a 3-Tier app with a containerized WCF service.</span></span>

![Diagramme d’architecture du service WCF en conteneur dans un environnement de développement de simplifié](./media/image5-3.5.png)

### <a name="benefits"></a><span data-ttu-id="ff335-163">Avantages</span><span class="sxs-lookup"><span data-stu-id="ff335-163">Benefits</span></span>

<span data-ttu-id="ff335-164">Il existe des avantages à votre application monolithique en cours d’exécution dans un conteneur.</span><span class="sxs-lookup"><span data-stu-id="ff335-164">There are advantages to running your monolithic application in a container.</span></span> <span data-ttu-id="ff335-165">Tout d’abord, vous créez une image pour l’application.</span><span class="sxs-lookup"><span data-stu-id="ff335-165">First, you create an image for the application.</span></span> <span data-ttu-id="ff335-166">À ce stade, chaque déploiement s’exécute dans le même environnement.</span><span class="sxs-lookup"><span data-stu-id="ff335-166">From that point on, every deployment runs in the same environment.</span></span> <span data-ttu-id="ff335-167">Chaque conteneur utilise la même version du système d’exploitation, a la même version des dépendances installées, utilise la même version du .NET framework et est générée à l’aide du même processus.</span><span class="sxs-lookup"><span data-stu-id="ff335-167">Every container uses the same OS version, has the same version of dependencies installed, uses the same .NET framework version, and is built by using the same process.</span></span> <span data-ttu-id="ff335-168">En fait, contrôler les dépendances de votre application à l’aide d’une image Docker.</span><span class="sxs-lookup"><span data-stu-id="ff335-168">Basically, you control the dependencies of your application by using a Docker image.</span></span> <span data-ttu-id="ff335-169">Les dépendances se déplacent avec l’application lorsque vous déployez les conteneurs.</span><span class="sxs-lookup"><span data-stu-id="ff335-169">The dependencies travel with the application when you deploy the containers.</span></span>

<span data-ttu-id="ff335-170">Un autre avantage est que les développeurs peuvent exécuter l’application dans l’environnement cohérent qui est fournie par les conteneurs Windows.</span><span class="sxs-lookup"><span data-stu-id="ff335-170">An additional benefit is that developers can run the application in the consistent environment that's provided by Windows Containers.</span></span> <span data-ttu-id="ff335-171">Les problèmes qui apparaissent uniquement dans certaines versions peuvent être détectés immédiatement, au lieu d’exposer dans un environnement intermédiaire ou de production.</span><span class="sxs-lookup"><span data-stu-id="ff335-171">Issues that appear only with certain versions can be spotted immediately, instead of surfacing in a staging or production environment.</span></span> <span data-ttu-id="ff335-172">Différences dans les environnements de développement utilisés par les membres de l’équipe de développement ont moins d’importance lorsque les applications s’exécutent dans des conteneurs.</span><span class="sxs-lookup"><span data-stu-id="ff335-172">Differences in development environments used by members of the development team matter less when applications run in containers.</span></span>

<span data-ttu-id="ff335-173">Applications en conteneur ont également une courbe de montée en puissance flatter.</span><span class="sxs-lookup"><span data-stu-id="ff335-173">Containerized applications also have a flatter scale-out curve.</span></span> <span data-ttu-id="ff335-174">Applications en conteneur activent que vous disposiez de plusieurs instances d’application et service (basées sur les conteneurs) dans une machine virtuelle ou physique par rapport aux déploiements d’application normal par ordinateur.</span><span class="sxs-lookup"><span data-stu-id="ff335-174">Containerized apps enable you to have more application and service instances (based on containers) in a VM or physical machine compared to regular application deployments per machine.</span></span> <span data-ttu-id="ff335-175">Cela se traduit par densité plus élevée et moins requis ressources, notamment lorsque vous utilisez des orchestrateurs tels que Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="ff335-175">This translates to higher density and fewer required resources, especially when you use orchestrators like Kubernetes.</span></span>

<span data-ttu-id="ff335-176">Mise en conteneur, dans les situations idéales, ne nécessite pas d’apporter des modifications au code d’application (C\#).</span><span class="sxs-lookup"><span data-stu-id="ff335-176">Containerization, in ideal situations, does not require making any changes to the application code (C\#).</span></span> <span data-ttu-id="ff335-177">Dans la plupart des scénarios, vous devez simplement les fichiers de métadonnées de déploiement Docker (fichiers Dockerfile et Docker Compose).</span><span class="sxs-lookup"><span data-stu-id="ff335-177">In most scenarios, you just need the Docker deployment metadata files (Dockerfiles and Docker Compose files).</span></span>

### <a name="next-steps"></a><span data-ttu-id="ff335-178">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="ff335-178">Next steps</span></span>

<span data-ttu-id="ff335-179">Explorez ce contenu plus approfondi sur le wiki GitHub :</span><span class="sxs-lookup"><span data-stu-id="ff335-179">Explore this content more in-depth on the GitHub wiki:</span></span>

- [<span data-ttu-id="ff335-180">Comment conteneuriser les applications web de .NET Framework avec les conteneurs Windows et Docker</span><span class="sxs-lookup"><span data-stu-id="ff335-180">How to containerize the .NET Framework web apps with Windows Containers and Docker</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/02.-How-to-containerize-the-.NET-Framework-web-apps-with-Windows-Containers-and-Docker)
- [<span data-ttu-id="ff335-181">Ajout de prise en charge Docker à un service WCF</span><span class="sxs-lookup"><span data-stu-id="ff335-181">Adding Docker Support to a WCF service</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/22.-Adding-Docker-Support)

## <a name="walkthrough-3-deploy-your-windows-containers-based-app-to-azure-vms"></a><span data-ttu-id="ff335-182">Procédure pas à pas 3 : Déployer votre application basée sur des conteneurs sur Windows sur les machines virtuelles Azure</span><span class="sxs-lookup"><span data-stu-id="ff335-182">Walkthrough 3: Deploy your Windows Containers-based app to Azure VMs</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="ff335-183">Disponibilité de la procédure pas à pas techniques</span><span class="sxs-lookup"><span data-stu-id="ff335-183">Technical walkthrough availability</span></span>

<span data-ttu-id="ff335-184">La procédure pas à pas technique complète est disponible dans le wiki de référentiel GitHub eShopModernizing : <https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)></span><span class="sxs-lookup"><span data-stu-id="ff335-184">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki: <https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)></span></span>

### <a name="overview"></a><span data-ttu-id="ff335-185">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="ff335-185">Overview</span></span>

<span data-ttu-id="ff335-186">Déploiement sur un hôte Docker sur un serveur Windows Server 2016 Virtual Machine (VM) dans Azure vous permet de définir rapidement des environnements de développement/test ou de préproduction.</span><span class="sxs-lookup"><span data-stu-id="ff335-186">Deploying to a Docker host on a Windows Server 2016 Virtual Machine (VM) in Azure lets you quickly set up development/test/staging environments.</span></span> <span data-ttu-id="ff335-187">Il vous donne également un emplacement commun pour les testeurs ou aux utilisateurs professionnels valider l’application.</span><span class="sxs-lookup"><span data-stu-id="ff335-187">It also gives you a common place for testers or business users to validate the app.</span></span> <span data-ttu-id="ff335-188">Machines virtuelles peuvent également être Infrastructure valide comme un environnement de production du Service (IaaS).</span><span class="sxs-lookup"><span data-stu-id="ff335-188">VMs also can be valid Infrastructure as a Service (IaaS) production environments.</span></span>

### <a name="goals"></a><span data-ttu-id="ff335-189">Objectifs</span><span class="sxs-lookup"><span data-stu-id="ff335-189">Goals</span></span>

<span data-ttu-id="ff335-190">L’objectif de cette procédure pas à pas est de vous montrer les plusieurs alternatives que vous avez lorsque vous déployez les conteneurs Windows sur les machines virtuelles Azure qui sont basés sur Windows Server 2016 ou versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="ff335-190">The goal of this walkthrough is to show you the multiple alternatives you have when you deploy Windows Containers to Azure VMs that are based on Windows Server 2016 or later versions.</span></span>

### <a name="scenarios"></a><span data-ttu-id="ff335-191">Scénarios</span><span class="sxs-lookup"><span data-stu-id="ff335-191">Scenarios</span></span>

<span data-ttu-id="ff335-192">Plusieurs scénarios sont couverts dans cette procédure pas à pas.</span><span class="sxs-lookup"><span data-stu-id="ff335-192">Several scenarios are covered in this walkthrough.</span></span>

#### <a name="scenario-a-deploy-to-an-azure-vm-from-a-dev-pc-through-docker-engine-connection"></a><span data-ttu-id="ff335-193">Scénario a : Déployer sur une machine virtuelle Azure à partir d’un PC de développement via la connexion du moteur Docker</span><span class="sxs-lookup"><span data-stu-id="ff335-193">Scenario A: Deploy to an Azure VM from a dev PC through Docker Engine connection</span></span>

![Déployer sur une machine virtuelle Azure à partir d’un PC de développement via une connexion de moteur Docker](./media/image5-4.png)

<span data-ttu-id="ff335-195">**Figure 5-4.**</span><span class="sxs-lookup"><span data-stu-id="ff335-195">**Figure 5-4.**</span></span> <span data-ttu-id="ff335-196">Déployer sur une machine virtuelle Azure à partir d’un PC de développement via une connexion de moteur Docker</span><span class="sxs-lookup"><span data-stu-id="ff335-196">Deploy to an Azure VM from a dev PC through a Docker Engine connection</span></span>

#### <a name="scenario-b-deploy-to-an-azure-vm-through-a-docker-registry"></a><span data-ttu-id="ff335-197">Scénario b : Déployer sur une machine virtuelle Azure via un Registre Docker</span><span class="sxs-lookup"><span data-stu-id="ff335-197">Scenario B: Deploy to an Azure VM through a Docker Registry</span></span>

![Déployer sur une machine virtuelle Azure via un Registre Docker](./media/image5-5.png)

<span data-ttu-id="ff335-199">**Figure 5-5.**</span><span class="sxs-lookup"><span data-stu-id="ff335-199">**Figure 5-5.**</span></span> <span data-ttu-id="ff335-200">Déployer sur une machine virtuelle Azure via un Registre Docker</span><span class="sxs-lookup"><span data-stu-id="ff335-200">Deploy to an Azure VM through a Docker Registry</span></span>

#### <a name="scenario-c-deploy-to-an-azure-vm-from-cicd-pipelines-in-azure-devops-services"></a><span data-ttu-id="ff335-201">Scénario c : Déployer sur une machine virtuelle Azure à partir de pipelines CI/CD dans les Services Azure DevOps</span><span class="sxs-lookup"><span data-stu-id="ff335-201">Scenario C: Deploy to an Azure VM from CI/CD pipelines in Azure DevOps Services</span></span>

![Déployer sur une machine virtuelle Azure à partir de pipelines CI/CD dans les Services Azure DevOps](./media/image5-6.png)

<span data-ttu-id="ff335-203">**Figure 5-6.**</span><span class="sxs-lookup"><span data-stu-id="ff335-203">**Figure 5-6.**</span></span> <span data-ttu-id="ff335-204">Déployer sur une machine virtuelle Azure à partir de pipelines CI/CD dans les Services Azure DevOps</span><span class="sxs-lookup"><span data-stu-id="ff335-204">Deploy to an Azure VM from CI/CD pipelines in Azure DevOps Services</span></span>

### <a name="azure-vms-for-windows-containers"></a><span data-ttu-id="ff335-205">Machines virtuelles Azure pour les conteneurs Windows</span><span class="sxs-lookup"><span data-stu-id="ff335-205">Azure VMs for Windows Containers</span></span>

<span data-ttu-id="ff335-206">Machines virtuelles Azure pour les conteneurs Windows sont des machines virtuelles basées sur Windows Server 2016, Windows 10 ou versions ultérieures, à la fois avec le moteur Docker configuré.</span><span class="sxs-lookup"><span data-stu-id="ff335-206">Azure VMs for Windows Containers are VMs based on Windows Server 2016, Windows 10, or later versions, both with Docker Engine set up.</span></span> <span data-ttu-id="ff335-207">Dans la plupart des cas, Windows Server 2016 est utilisé dans les machines virtuelles Azure.</span><span class="sxs-lookup"><span data-stu-id="ff335-207">In most cases, Windows Server 2016 is used in the Azure VMs.</span></span>

<span data-ttu-id="ff335-208">Azure fournit actuellement une machine virtuelle nommée **Windows Server 2016 avec Containers**.</span><span class="sxs-lookup"><span data-stu-id="ff335-208">Azure currently provides a VM named **Windows Server 2016 with Containers**.</span></span> <span data-ttu-id="ff335-209">Vous pouvez utiliser cette machine virtuelle pour tester la nouvelle fonctionnalité de conteneur Windows Server, avec Windows Server Core ou Windows Nano Server.</span><span class="sxs-lookup"><span data-stu-id="ff335-209">You can use this VM to try the new Windows Server Container feature, with either Windows Server Core or Windows Nano Server.</span></span> <span data-ttu-id="ff335-210">Images de système d’exploitation de conteneur sont installés, et ensuite la machine virtuelle est prête à être utilisée avec Docker.</span><span class="sxs-lookup"><span data-stu-id="ff335-210">Container OS images are installed, and then the VM is ready to use with Docker.</span></span>

### <a name="benefits"></a><span data-ttu-id="ff335-211">Avantages</span><span class="sxs-lookup"><span data-stu-id="ff335-211">Benefits</span></span>

<span data-ttu-id="ff335-212">Bien que les conteneurs Windows peuvent être déployées sur site Windows Server 2016 les machines virtuelles, lorsque vous déployez sur Azure, vous obtenez un moyen plus simple de prise en main, prêt à l’emploi des machines virtuelles conteneur serveur Windows.</span><span class="sxs-lookup"><span data-stu-id="ff335-212">Although Windows Containers can be deployed to on-premises Windows Server 2016 VMs, when you deploy to Azure, you get an easier way to get started, with ready-to-use Windows Server Container VMs.</span></span> <span data-ttu-id="ff335-213">Vous obtenez également un emplacement en ligne commun qui est accessible à des testeurs et évolutivité automatique par le biais de machines virtuelles Azure identiques.</span><span class="sxs-lookup"><span data-stu-id="ff335-213">You also get a common online location that’s accessible to testers, and automatic scalability through Azure virtual machine scale sets.</span></span>

### <a name="next-steps"></a><span data-ttu-id="ff335-214">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="ff335-214">Next steps</span></span>

<span data-ttu-id="ff335-215">Explorez ce contenu plus approfondi sur le wiki GitHub :</span><span class="sxs-lookup"><span data-stu-id="ff335-215">Explore this content more in-depth on the GitHub wiki:</span></span>

<https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)>

## <a name="walkthrough-4-deploy-your-windows-containers-based-apps-to-azure-container-instances-aci"></a><span data-ttu-id="ff335-216">Procédure pas à pas 4 : Déployer vos applications de conteneurs Windows sur Azure Container Instances (ACI)</span><span class="sxs-lookup"><span data-stu-id="ff335-216">Walkthrough 4: Deploy your Windows Containers-based apps to Azure Container Instances (ACI)</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="ff335-217">Disponibilité de la procédure pas à pas techniques</span><span class="sxs-lookup"><span data-stu-id="ff335-217">Technical walkthrough availability</span></span>

<span data-ttu-id="ff335-218">La procédure pas à pas technique complète est disponible dans le wiki de référentiel GitHub eShopModernizing :</span><span class="sxs-lookup"><span data-stu-id="ff335-218">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

<span data-ttu-id="ff335-219">[Le déploiement des applications dans ACI (Azure Container Instances)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances))</span><span class="sxs-lookup"><span data-stu-id="ff335-219">[Deploying the Apps to ACI (Azure Container Instances)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances))</span></span>

### <a name="overview"></a><span data-ttu-id="ff335-220">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="ff335-220">Overview</span></span>

<span data-ttu-id="ff335-221">[Azure Container Instances (ACI)](https://docs.microsoft.com/azure/container-instances/) est le moyen le plus rapide dans un environnement de développement/test/préparation de conteneurs où vous pouvez déployer des instances uniques de conteneurs.</span><span class="sxs-lookup"><span data-stu-id="ff335-221">[Azure Container Instances (ACI)](https://docs.microsoft.com/azure/container-instances/) is the quickest way to have a Containers dev/test/staging environment where you can deploy single instances of containers.</span></span>

### <a name="goals"></a><span data-ttu-id="ff335-222">Objectifs</span><span class="sxs-lookup"><span data-stu-id="ff335-222">Goals</span></span>

<span data-ttu-id="ff335-223">Cette procédure pas à pas vous montre les principaux scénarios lors du déploiement de conteneurs de Windows sur Azure Container Instances (ACI) et comment vous pouvez déployer des applications d’eShopModernizing dans ACI.</span><span class="sxs-lookup"><span data-stu-id="ff335-223">This walkthrough shows you the main scenarios when deploying Windows Containers to Azure Container Instances (ACI) and how you can deploy eShopModernizing Apps into ACI.</span></span>

### <a name="scenarios"></a><span data-ttu-id="ff335-224">Scénarios</span><span class="sxs-lookup"><span data-stu-id="ff335-224">Scenarios</span></span>

<span data-ttu-id="ff335-225">Il peut y avoir des variations sur le déploiement des applications eShopModernizing dans ACI telles que le déploiement d’un ou toutes les applications (application MVC, Web Forms application ou service WCF).</span><span class="sxs-lookup"><span data-stu-id="ff335-225">There can be variations about deploying the eShopModernizing apps into ACI such as deploying just one or all of the apps (MVC app, WebForms app or WCF service).</span></span> <span data-ttu-id="ff335-226">Dans le scénario suivant, illustré ci-dessous, vous pouvez voir l’application MVC ASP.NET ainsi que le conteneur de SQL Server de ces deux valeurs déployés en tant que conteneurs dans ACI (Azure Container Instances).</span><span class="sxs-lookup"><span data-stu-id="ff335-226">In the following scenario shown below you can see the ASP.NET MVC app plus the SQL Server container both of them deployed as containers into ACI (Azure Container Instances).</span></span>

![Déployer sur ACI à partir d’un environnement de développement](./media/image5-3.5.6.png)

### <a name="benefits"></a><span data-ttu-id="ff335-228">Avantages</span><span class="sxs-lookup"><span data-stu-id="ff335-228">Benefits</span></span>

<span data-ttu-id="ff335-229">Azure Container Instances rend plus facile créer et gérer des conteneurs Docker dans Azure, sans avoir à approvisionner des machines virtuelles ou à adopter un service de niveau supérieur.</span><span class="sxs-lookup"><span data-stu-id="ff335-229">Azure Container Instances makes it easy to create and manage Docker containers in Azure, without having to provision virtual machines or adopt a higher-level service.</span></span> <span data-ttu-id="ff335-230">Avec ACI, vous pouvez directement déployer un conteneur Windows dans Azure et l’exposer sur internet avec un nom de domaine complet (FQDN) dans l’espace de quelques secondes (à condition que vous avez l’image de conteneur de Windows prêt dans un Registre Docker comme Docker Hub ou Azure Container Registre).</span><span class="sxs-lookup"><span data-stu-id="ff335-230">With ACI, you can directly deploy a Windows container in Azure and expose it to the internet with a fully qualified domain name (FQDN) in a matter of seconds (Provided that you have the Windows Container image ready in a Docker registry like Docker Hub or Azure Container Registry).</span></span>

### <a name="considerations"></a><span data-ttu-id="ff335-231">Éléments à prendre en considération</span><span class="sxs-lookup"><span data-stu-id="ff335-231">Considerations</span></span>

<span data-ttu-id="ff335-232">Le déploiement de conteneurs Windows avec le .NET Framework soit complet / ASP.NET ou SQL Server dans Azure Container Instances (ACI) n’est pas tout à fait aussi rapide que le déploiement sur un hôte Docker standard (par exemple, un serveur Windows Server 2016 avec les conteneurs Windows), car l’image Docker doit être téléchargés à chaque fois (extraites à partir du Registre Docker) et la taille de l’image de conteneur SQL (15.1 Go) et l’image de conteneur ASP.NET (13.9 Go) est importante, toutefois, il est beaucoup moins cher que la conservation de votre propre hôte docker (définitivement en ligne Windows Server 2016 avec la machine virtuelle de conteneurs Windows dans Azure) ne pas à mentionner un ensemble orchestrateur comme Kubernetes dans Azure (ACS) qui est, quant à eux, un excellent choix pour les déploiements de production.</span><span class="sxs-lookup"><span data-stu-id="ff335-232">Deploying Windows Containers with either full .NET Framework / ASP.NET or SQL Server into Azure Container Instances (ACI) is not quite as fast as deploying to a regular Docker Host (like a Windows Server 2016 with Windows Containers) because the Docker image has to be downloaded (pulled from the Docker registry) every time and the sizes of the SQL container image (15.1 GB) and the ASP.NET container image (13.9 GB) are significantly large, however it is much cheaper than maintaining your own docker host (permanently on-line Windows Server 2016 with Windows Containers VM in Azure) not to mention a whole orchestrator like Kubernetes in Azure (AKS) which is, on the other hand, a great choice for production deployments.</span></span>

<span data-ttu-id="ff335-233">En tant que principale conclusion, à l’aide d’Azure Container Instances est une option très intéressante pour les scénarios de développement/Test et pour les pipelines CI/CD.</span><span class="sxs-lookup"><span data-stu-id="ff335-233">As main conclusion, using Azure Container Instances is a very compelling option for Dev/Test scenarios and for CI/CD pipelines.</span></span>

## <a name="next-steps"></a><span data-ttu-id="ff335-234">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="ff335-234">Next steps</span></span>

<span data-ttu-id="ff335-235">Explorez ce contenu plus approfondi sur le wiki GitHub :</span><span class="sxs-lookup"><span data-stu-id="ff335-235">Explore this content more in-depth on the GitHub wiki:</span></span>

[https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances)TBD)

## <a name="walkthrough-5-deploy-your-windows-containers-based-apps-to-kubernetes-in-azure-container-service"></a><span data-ttu-id="ff335-236">Procédure pas à pas 5 : Déployer vos applications de conteneurs Windows sur Kubernetes dans Azure Container Service</span><span class="sxs-lookup"><span data-stu-id="ff335-236">Walkthrough 5: Deploy your Windows Containers-based apps to Kubernetes in Azure Container Service</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="ff335-237">Disponibilité de la procédure pas à pas techniques</span><span class="sxs-lookup"><span data-stu-id="ff335-237">Technical walkthrough availability</span></span>

<span data-ttu-id="ff335-238">La procédure pas à pas technique complète est disponible dans le wiki de référentiel GitHub eShopModernizing :</span><span class="sxs-lookup"><span data-stu-id="ff335-238">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

<https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD)>

### <a name="overview"></a><span data-ttu-id="ff335-239">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="ff335-239">Overview</span></span>

<span data-ttu-id="ff335-240">Une application qui repose sur les conteneurs Windows devra rapidement utilisent des plateformes, s’éloigner de davantage de machines virtuelles IaaS.</span><span class="sxs-lookup"><span data-stu-id="ff335-240">An application that's based on Windows Containers will quickly need to use platforms, moving even further away from IaaS VMs.</span></span> <span data-ttu-id="ff335-241">Cela est nécessaire pour facilement atteindre une haute évolutivité et mieux automatisée l’évolutivité et pour une amélioration significative d’automatisé de déploiements et le contrôle de version.</span><span class="sxs-lookup"><span data-stu-id="ff335-241">This is needed to easily achieve high scalability and better automated scalability, and for a significant improvement in automated deployments and versioning.</span></span> <span data-ttu-id="ff335-242">Vous pouvez atteindre ces objectifs à l’aide de l’orchestrateur [Kubernetes](https://kubernetes.io/), disponible dans [Azure Container Services](https://azure.microsoft.com/services/container-service/).</span><span class="sxs-lookup"><span data-stu-id="ff335-242">You can achieve these goals by using the orchestrator [Kubernetes](https://kubernetes.io/), available in [Azure Container Services](https://azure.microsoft.com/services/container-service/).</span></span>

### <a name="goals"></a><span data-ttu-id="ff335-243">Objectifs</span><span class="sxs-lookup"><span data-stu-id="ff335-243">Goals</span></span>

<span data-ttu-id="ff335-244">L’objectif de cette procédure pas à pas consiste à apprendre à déployer une application Windows conteneur sur Kubernetes (également appelé *K8s*) dans Azure Container Service.</span><span class="sxs-lookup"><span data-stu-id="ff335-244">The goal of this walkthrough is to learn how to deploy a Windows Container–based application to Kubernetes (also called *K8s*) in Azure Container Service.</span></span> <span data-ttu-id="ff335-245">Déploiement sur Kubernetes à partir de zéro est un processus en deux étapes :</span><span class="sxs-lookup"><span data-stu-id="ff335-245">Deploying to Kubernetes from scratch is a two-step process:</span></span>

1. <span data-ttu-id="ff335-246">Déployer un cluster Kubernetes sur Azure Container Service.</span><span class="sxs-lookup"><span data-stu-id="ff335-246">Deploy a Kubernetes cluster to Azure Container Service.</span></span>

2. <span data-ttu-id="ff335-247">Déployer l’application et les ressources associées au cluster Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="ff335-247">Deploy the application and related resources to the Kubernetes cluster.</span></span>

### <a name="scenarios"></a><span data-ttu-id="ff335-248">Scénarios</span><span class="sxs-lookup"><span data-stu-id="ff335-248">Scenarios</span></span>

#### <a name="scenario-a-deploy-directly-to-a-kubernetes-cluster-from-a-dev-environment"></a><span data-ttu-id="ff335-249">Scénario a : Déployer directement sur un cluster Kubernetes à partir d’un environnement de développement</span><span class="sxs-lookup"><span data-stu-id="ff335-249">Scenario A: Deploy directly to a Kubernetes cluster from a dev environment</span></span>

![Déployer directement sur un cluster Kubernetes à partir d’un environnement de développement](./media/image5-7.png)

<span data-ttu-id="ff335-251">**Figure 5-7.**</span><span class="sxs-lookup"><span data-stu-id="ff335-251">**Figure 5-7.**</span></span> <span data-ttu-id="ff335-252">Déployer directement sur un cluster Kubernetes à partir d’un environnement de développement</span><span class="sxs-lookup"><span data-stu-id="ff335-252">Deploy directly to a Kubernetes cluster from a development environment</span></span>

#### <a name="scenario-b-deploy-to-a-kubernetes-cluster-from-cicd-pipelines-in-azure-devops-services"></a><span data-ttu-id="ff335-253">Scénario b : Déployer sur un cluster Kubernetes à partir de pipelines CI/CD dans les Services Azure DevOps</span><span class="sxs-lookup"><span data-stu-id="ff335-253">Scenario B: Deploy to a Kubernetes cluster from CI/CD pipelines in Azure DevOps Services</span></span>

![Déployer sur un cluster Kubernetes à partir de pipelines CI/CD dans les Services Azure DevOps](./media/image5-8.png)

<span data-ttu-id="ff335-255">**Figure 5-8.**</span><span class="sxs-lookup"><span data-stu-id="ff335-255">**Figure 5-8.**</span></span> <span data-ttu-id="ff335-256">Déployer sur un cluster Kubernetes à partir de pipelines CI/CD dans les Services Azure DevOps</span><span class="sxs-lookup"><span data-stu-id="ff335-256">Deploy to a Kubernetes cluster from CI/CD pipelines in Azure DevOps Services</span></span>

### <a name="benefits"></a><span data-ttu-id="ff335-257">Avantages</span><span class="sxs-lookup"><span data-stu-id="ff335-257">Benefits</span></span>

<span data-ttu-id="ff335-258">Il existe de nombreux avantages pour le déploiement sur un cluster dans Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="ff335-258">There are many benefits to deploying to a cluster in Kubernetes.</span></span> <span data-ttu-id="ff335-259">Le principal avantage est que vous obtenez un environnement prêt pour la production dans lequel vous pouvez faire évoluer l’application en fonction du nombre d’instances de conteneur vous souhaitez utiliser (interne-extensibilité dans les nœuds existants) et en fonction du nombre de machines virtuelles ou des nœuds dans le cluster ( évolutivité globale du cluster).</span><span class="sxs-lookup"><span data-stu-id="ff335-259">The biggest benefit is that you get a production-ready environment in which you can scale out the application based on the number of container instances you want to use (inner-scalability in the existing nodes), and based on the number of nodes or VMs in the cluster (global scalability of the cluster).</span></span>

<span data-ttu-id="ff335-260">Azure Container Service optimise les technologies et outils open source populaires spécifiquement pour Azure.</span><span class="sxs-lookup"><span data-stu-id="ff335-260">Azure Container Service optimizes popular open-source tools and technologies specifically for Azure.</span></span> <span data-ttu-id="ff335-261">Vous obtenez une solution ouverte qui offre la portabilité, pour vos conteneurs et la configuration de votre application.</span><span class="sxs-lookup"><span data-stu-id="ff335-261">You get an open solution that offers portability, both for your containers and for your application configuration.</span></span> <span data-ttu-id="ff335-262">Vous sélectionnez la taille, le nombre d’hôtes, et l’outils d’orchestrator-Container Service gère tout le reste.</span><span class="sxs-lookup"><span data-stu-id="ff335-262">You select the size, the number of hosts, and the orchestrator tools-Container Service handles everything else.</span></span>

<span data-ttu-id="ff335-263">Avec Kubernetes, les développeurs peuvent progresser de réfléchir aux ordinateurs physiques et virtuels, à la planification d’une infrastructure orientée conteneur qui facilite les fonctionnalités suivantes, entre autres :</span><span class="sxs-lookup"><span data-stu-id="ff335-263">With Kubernetes, developers can progress from thinking about physical and virtual machines, to planning a container-centric infrastructure that facilitates the following capabilities, among others:</span></span>

- <span data-ttu-id="ff335-264">Applications basées sur plusieurs conteneurs</span><span class="sxs-lookup"><span data-stu-id="ff335-264">Applications based on multiple containers</span></span>

- <span data-ttu-id="ff335-265">Réplication des instances de conteneur et de mise à l’échelle horizontale</span><span class="sxs-lookup"><span data-stu-id="ff335-265">Replicating container instances and horizontal autoscaling</span></span>

- <span data-ttu-id="ff335-266">D’affectation de noms et de la découverte (par exemple, DNS interne)</span><span class="sxs-lookup"><span data-stu-id="ff335-266">Naming and discovering (for example, internal DNS)</span></span>

- <span data-ttu-id="ff335-267">L’équilibrage de charge</span><span class="sxs-lookup"><span data-stu-id="ff335-267">Balancing loads</span></span>

- <span data-ttu-id="ff335-268">Mises à jour propagées</span><span class="sxs-lookup"><span data-stu-id="ff335-268">Rolling updates</span></span>

- <span data-ttu-id="ff335-269">Distribution de clés secrètes</span><span class="sxs-lookup"><span data-stu-id="ff335-269">Distributing secrets</span></span>

- <span data-ttu-id="ff335-270">Vérifications d’intégrité de l’application</span><span class="sxs-lookup"><span data-stu-id="ff335-270">Application health checks</span></span>

## <a name="next-steps"></a><span data-ttu-id="ff335-271">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="ff335-271">Next steps</span></span>

<span data-ttu-id="ff335-272">Explorez ce contenu plus approfondi sur le wiki GitHub : <https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD)></span><span class="sxs-lookup"><span data-stu-id="ff335-272">Explore this content more in-depth on the GitHub wiki: <https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD)></span></span>

> [!div class="step-by-step"]
> <span data-ttu-id="ff335-273">[Précédent](lift-and-shift-existing-apps-devops/migrate-to-hybrid-cloud-scenarios.md)
> [Suivant](conclusions.md)</span><span class="sxs-lookup"><span data-stu-id="ff335-273">[Previous](lift-and-shift-existing-apps-devops/migrate-to-hybrid-cloud-scenarios.md)
[Next](conclusions.md)</span></span>
