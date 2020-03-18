---
title: Procédures pas à pas et vue d’ensemble technique pour le démarrage
description: Moderniser les applications .NET existantes avec le cloud Azure et les conteneurs Windows (fr) Les procédures à pas et la technique commencent la vue d’ensemble
ms.date: 04/28/2018
ms.openlocfilehash: 190b33c4307b09bab0543d481e66ac9328074a0d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "69660883"
---
# <a name="walkthroughs-and-technical-get-started-overview"></a><span data-ttu-id="14d5c-103">Procédures pas à pas et vue d’ensemble technique pour le démarrage</span><span class="sxs-lookup"><span data-stu-id="14d5c-103">Walkthroughs and technical get started overview</span></span>

<span data-ttu-id="14d5c-104">Pour limiter la taille de ce livre électronique, des documents techniques supplémentaires et des procédures à pas complètes ont été mis à disposition dans un référentiel GitHub.</span><span class="sxs-lookup"><span data-stu-id="14d5c-104">To limit the size of this e-book, additional technical documentation and the full walkthroughs were made available in a GitHub repository.</span></span> <span data-ttu-id="14d5c-105">La série en ligne de procédures à pas décrites dans ce chapitre couvre la configuration étape par étape des différents environnements qui sont basés sur les conteneurs Windows, et le déploiement à Azure.</span><span class="sxs-lookup"><span data-stu-id="14d5c-105">The online series of walkthroughs that is described in this chapter covers the step-by-step setup of the multiple environments that are based on Windows Containers, and deployment to Azure.</span></span>

<span data-ttu-id="14d5c-106">Les sections suivantes expliquent ce qu’il s’agit, ses objectifs et sa vision de haut niveau, et fournit un diagramme des tâches qui sont impliquées.</span><span class="sxs-lookup"><span data-stu-id="14d5c-106">The following sections explain what each walkthrough is about, its objectives and high-level vision, and provides a diagram of the tasks that are involved.</span></span> <span data-ttu-id="14d5c-107">Vous pouvez obtenir les pas à pas eux-mêmes dans les applications <https://github.com/dotnet-architecture/eShopModernizing/wiki> *eShopModernizing* GitHub repo wiki à .</span><span class="sxs-lookup"><span data-stu-id="14d5c-107">You can get the walkthroughs themselves in the *eShopModernizing* apps GitHub repo wiki at <https://github.com/dotnet-architecture/eShopModernizing/wiki>.</span></span>

## <a name="technical-walkthrough-list"></a><span data-ttu-id="14d5c-108">Liste technique des pas à pas</span><span class="sxs-lookup"><span data-stu-id="14d5c-108">Technical walkthrough list</span></span>

<span data-ttu-id="14d5c-109">Les procédures à pas qui suivent fournissent des conseils techniques cohérents et complets pour les applications d’échantillons que vous pouvez soulever et déplacer à l’aide de conteneurs, puis se déplacer en utilisant plusieurs choix de déploiement en Azure.</span><span class="sxs-lookup"><span data-stu-id="14d5c-109">The following get-started walkthroughs provide consistent and comprehensive technical guidance for sample apps that you can lift and shift by using containers, and then move by using multiple deployment choices in Azure.</span></span>

<span data-ttu-id="14d5c-110">Chacune des procédures à pas suivantes utilise le nouvel exemple eShopLegacy et eShopModernizing <https://github.com/dotnet-architecture/eShopModernizing>applications, qui sont disponibles sur GitHub à .</span><span class="sxs-lookup"><span data-stu-id="14d5c-110">Each of the following walkthroughs uses the new sample eShopLegacy and eShopModernizing apps, which are available on GitHub at <https://github.com/dotnet-architecture/eShopModernizing>.</span></span>

- <span data-ttu-id="14d5c-111">**Visite des applications héritées d’eShop (applications de base pour moderniser)**</span><span class="sxs-lookup"><span data-stu-id="14d5c-111">**Tour of eShop legacy apps (baseline apps to modernize)**</span></span>

- <span data-ttu-id="14d5c-112">**Conteneurisez vos applications Web ASP.NET existantes (WebForms & MVC) avec des conteneurs Windows**</span><span class="sxs-lookup"><span data-stu-id="14d5c-112">**Containerize your existing ASP.NET web apps (WebForms & MVC) with Windows Containers**</span></span>

- <span data-ttu-id="14d5c-113">**Conteneurisez vos services WCF existants (applications N-Tier) avec des conteneurs Windows**</span><span class="sxs-lookup"><span data-stu-id="14d5c-113">**Containerize your existing WCF services (N-Tier apps) with Windows Containers**</span></span>

- <span data-ttu-id="14d5c-114">**Déployez votre application Windows Containers sur les VM Azure**</span><span class="sxs-lookup"><span data-stu-id="14d5c-114">**Deploy your Windows Containers-based app to Azure VMs**</span></span>

- <span data-ttu-id="14d5c-115">**Déployez vos applications basées sur les conteneurs Windows sur Kubernetes dans azure Container Service**</span><span class="sxs-lookup"><span data-stu-id="14d5c-115">**Deploy your Windows Containers-based apps to Kubernetes in Azure Container Service**</span></span>

## <a name="walkthrough-1-tour-of-eshop-legacy-apps"></a><span data-ttu-id="14d5c-116">Procédure pas à pas 1: Tour des applications héritées eShop</span><span class="sxs-lookup"><span data-stu-id="14d5c-116">Walkthrough 1: Tour of eShop legacy apps</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="14d5c-117">Disponibilité technique de procédure pas à pas</span><span class="sxs-lookup"><span data-stu-id="14d5c-117">Technical walkthrough availability</span></span>

<span data-ttu-id="14d5c-118">La procédure technique complète est disponible dans le wiki GitPo eShopModernizing :</span><span class="sxs-lookup"><span data-stu-id="14d5c-118">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

[<span data-ttu-id="14d5c-119">eShopModernizing wiki pas à pas</span><span class="sxs-lookup"><span data-stu-id="14d5c-119">eShopModernizing wiki walkthroughs</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki)

### <a name="overview"></a><span data-ttu-id="14d5c-120">Vue d’ensemble</span><span class="sxs-lookup"><span data-stu-id="14d5c-120">Overview</span></span>

<span data-ttu-id="14d5c-121">Dans cette procédure pas à pas, vous pouvez explorer la mise en œuvre initiale de trois applications héritées de l’échantillon.</span><span class="sxs-lookup"><span data-stu-id="14d5c-121">In this walkthrough, you can explore the initial implementation of three sample legacy applications.</span></span> <span data-ttu-id="14d5c-122">Les deux premières applications web d’échantillon ont une architecture monolithique, et ont été créées en utilisant des ASP.NET classiques.</span><span class="sxs-lookup"><span data-stu-id="14d5c-122">The first two sample web apps have a monolithic architecture, and were created by using classic ASP.NET.</span></span> <span data-ttu-id="14d5c-123">Une application est basée sur ASP.NET 4.x MVC; la deuxième application est basée sur ASP.NET 4.x Web Forms.</span><span class="sxs-lookup"><span data-stu-id="14d5c-123">One application is based on ASP.NET 4.x MVC; the second application is based on ASP.NET 4.x Web Forms.</span></span>
<span data-ttu-id="14d5c-124">La troisième application est une application à 3 niveaux composée par une application WinForms cliente et un service [de la Windows Communication Foundation (WCF)](../../framework/wcf/whats-wcf.md) côté serveur.</span><span class="sxs-lookup"><span data-stu-id="14d5c-124">The third app is a 3-Tier app composed by a client WinForms app and a server-side [Windows Communication Foundation (WCF)](../../framework/wcf/whats-wcf.md) service.</span></span>

<span data-ttu-id="14d5c-125">Toutes ces applications sont disponibles à [l’eShopModernizing GitHub repo](https://github.com/dotnet-architecture/eShopModernizing).</span><span class="sxs-lookup"><span data-stu-id="14d5c-125">All these applications are available at the [eShopModernizing GitHub repo](https://github.com/dotnet-architecture/eShopModernizing).</span></span>

### <a name="goals"></a><span data-ttu-id="14d5c-126">Objectifs</span><span class="sxs-lookup"><span data-stu-id="14d5c-126">Goals</span></span>

<span data-ttu-id="14d5c-127">L’objectif principal de cette procédure pas à pas est simplement de se familiariser avec ces applications, et avec leur code et leur configuration.</span><span class="sxs-lookup"><span data-stu-id="14d5c-127">The main goal of this walkthrough is simply to get familiar with these apps, and with their code and configuration.</span></span> <span data-ttu-id="14d5c-128">Vous pouvez configurer les applications afin qu’elles génèrent et utilisent des données fictives, sans utiliser la base de données SQL, à des fins de test.</span><span class="sxs-lookup"><span data-stu-id="14d5c-128">You can configure the apps so that they generate and use mock data, without using the SQL database, for testing purposes.</span></span> <span data-ttu-id="14d5c-129">Ce config optionnel est basé sur l’injection de dépendance, d’une manière découplée.</span><span class="sxs-lookup"><span data-stu-id="14d5c-129">This optional config is based on dependency injection, in a decoupled way.</span></span>

### <a name="scenario-1-aspnet-web-apps"></a><span data-ttu-id="14d5c-130">Scénario 1 : ASP.NET applications Web</span><span class="sxs-lookup"><span data-stu-id="14d5c-130">Scenario 1: ASP.NET Web apps</span></span>

<span data-ttu-id="14d5c-131">La figure ci-dessous montre le scénario simple de l’héritage original ASP.NET applications Web.</span><span class="sxs-lookup"><span data-stu-id="14d5c-131">The figure below shows the simple scenario of the original legacy ASP.NET web applications.</span></span>

![Scénario d’architecture simple de l’héritage original ASP.NET applications web](./media/image5-1.png)

<span data-ttu-id="14d5c-133">Du point de vue du domaine d’affaires, les deux applications offrent les mêmes fonctionnalités de gestion de catalogue.</span><span class="sxs-lookup"><span data-stu-id="14d5c-133">From a business domain perspective, both apps offer the same catalog management features.</span></span> <span data-ttu-id="14d5c-134">Les membres de l’équipe d’entreprise eShop utiliseraient l’application pour afficher et modifier le catalogue de produits.</span><span class="sxs-lookup"><span data-stu-id="14d5c-134">Members of the eShop enterprise team would use the app to view and edit the product catalog.</span></span>

<span data-ttu-id="14d5c-135">Le chiffre suivant montre les captures d’écran initiales de l’application.</span><span class="sxs-lookup"><span data-stu-id="14d5c-135">The next figure shows the initial app screenshots.</span></span>

![ASP.NET des applications MVC et ASP.NET Web Forms (technologies existantes/héritées)](./media/image5-2.png)

<span data-ttu-id="14d5c-137">Les dépendances dans ASP.NET versions 4.x ou antérieures (pour MVC ou pour les formulaires Web) signifient que ces applications ne s’exécuteront pas sur .NET Core à moins que le code ne soit entièrement réécrit en utilisant ASP.NET Core MVC.</span><span class="sxs-lookup"><span data-stu-id="14d5c-137">Dependencies in ASP.NET 4.x or earlier versions (either for MVC or for Web Forms) means that these applications won’t run on .NET Core unless the code is fully rewritten by using ASP.NET Core MVC.</span></span>

### <a name="scenario-2-wcf-service-and-winforms-client-app-3-tier-app"></a><span data-ttu-id="14d5c-138">Scénario 2 : service WCF et application client WinForms (application 3-Tier)</span><span class="sxs-lookup"><span data-stu-id="14d5c-138">Scenario 2: WCF service and WinForms client app (3-Tier app)</span></span>

<span data-ttu-id="14d5c-139">La figure ci-dessous montre le scénario simple de l’application originale de l’héritage à 3 niveaux.</span><span class="sxs-lookup"><span data-stu-id="14d5c-139">The figure below shows the simple scenario of the original 3-Tier legacy application.</span></span>

![Scénario d’architecture simple de l’application 3-Tier originale avec un service WCF et une application client WinForms](./media/image5-1.5.png)

### <a name="benefits"></a><span data-ttu-id="14d5c-141">Avantages</span><span class="sxs-lookup"><span data-stu-id="14d5c-141">Benefits</span></span>

<span data-ttu-id="14d5c-142">Les avantages de cette procédure pas à pas sont simples: Il suffit de se familiariser avec le code et les applications initiales.</span><span class="sxs-lookup"><span data-stu-id="14d5c-142">The benefits of this walkthrough are simple: Just get familiar with the code and initial apps.</span></span>

### <a name="next-steps"></a><span data-ttu-id="14d5c-143">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="14d5c-143">Next steps</span></span>

<span data-ttu-id="14d5c-144">Explorez ce contenu plus en profondeur sur le wiki GitHub :</span><span class="sxs-lookup"><span data-stu-id="14d5c-144">Explore this content more in-depth on the GitHub wiki:</span></span>

- [<span data-ttu-id="14d5c-145">Visite des applications « legacy » ASP.NET MVC et Web Forms</span><span class="sxs-lookup"><span data-stu-id="14d5c-145">Tour on the baseline ASP.NET MVC and Web Forms “legacy” apps</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/01.-Tour-on-the-ASP.NET-MVC-and-WebForms-apps-implementation-code)
- [<span data-ttu-id="14d5c-146">Visite du service WCF de base et de l’application « héritage » de WinForms (3-Tier)</span><span class="sxs-lookup"><span data-stu-id="14d5c-146">Tour on the baseline WCF service and WinForms (3-Tier) “legacy” app</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/21.-Tour-on-the-WCF-service-and-WinForms-apps)

## <a name="walkthrough-2-containerize-your-existing-net-applications-with-windows-containers"></a><span data-ttu-id="14d5c-147">Procédure pas à pas 2 : Conteneurisez vos applications .NET existantes avec des conteneurs Windows</span><span class="sxs-lookup"><span data-stu-id="14d5c-147">Walkthrough 2: Containerize your existing .NET applications with Windows Containers</span></span>

### <a name="overview"></a><span data-ttu-id="14d5c-148">Vue d’ensemble</span><span class="sxs-lookup"><span data-stu-id="14d5c-148">Overview</span></span>

<span data-ttu-id="14d5c-149">Utilisez Windows Containers pour améliorer le déploiement d’applications .NET existantes, comme celles basées sur MVC, Web Forms ou WCF, dans les environnements de production, de développement et de test.</span><span class="sxs-lookup"><span data-stu-id="14d5c-149">Use Windows Containers to improve deployment of existing .NET applications, like those based on MVC, Web Forms, or WCF, to production, development, and test environments.</span></span>

### <a name="goals"></a><span data-ttu-id="14d5c-150">Objectifs</span><span class="sxs-lookup"><span data-stu-id="14d5c-150">Goals</span></span>

<span data-ttu-id="14d5c-151">Le but de cette procédure pas à pas est de vous montrer plusieurs options pour la conteneurisation d’une application cadre .NET existante.</span><span class="sxs-lookup"><span data-stu-id="14d5c-151">The goal of this walkthrough is to show you several options for containerizing an existing .NET Framework application.</span></span> <span data-ttu-id="14d5c-152">Vous pouvez :</span><span class="sxs-lookup"><span data-stu-id="14d5c-152">You can:</span></span>

- <span data-ttu-id="14d5c-153">Conteneurisez votre application en utilisant [Visual Studio 2017 Tools for Docker](/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker) (Visual Studio 2017 ou versions ultérieures).</span><span class="sxs-lookup"><span data-stu-id="14d5c-153">Containerize your application by using [Visual Studio 2017 Tools for Docker](/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker) (Visual Studio 2017 or later versions).</span></span>

- <span data-ttu-id="14d5c-154">Conteneurisez votre application en ajoutant manuellement un [Dockerfile,](https://docs.docker.com/engine/reference/builder/)puis en utilisant le [Docker CLI](https://docs.docker.com/engine/reference/commandline/cli/).</span><span class="sxs-lookup"><span data-stu-id="14d5c-154">Containerize your application by manually adding a [Dockerfile](https://docs.docker.com/engine/reference/builder/), and then using the [Docker CLI](https://docs.docker.com/engine/reference/commandline/cli/).</span></span>

- <span data-ttu-id="14d5c-155">Conteneurisez votre application en utilisant l’outil [Img2Docker](https://github.com/docker/communitytools-image2docker-win) (un outil open-source de Docker).</span><span class="sxs-lookup"><span data-stu-id="14d5c-155">Containerize your application by using the [Img2Docker](https://github.com/docker/communitytools-image2docker-win) tool (an open-source tool from Docker).</span></span>

<span data-ttu-id="14d5c-156">Ce pas-là se concentre sur l’approche Visual Studio 2017 Tools for Docker, mais les deux autres approches sont assez similaires en ce qui concerne l’utilisation de Dockerfiles.</span><span class="sxs-lookup"><span data-stu-id="14d5c-156">This walkthrough focuses on the Visual Studio 2017 Tools for Docker approach, but the other two approaches are fairly similar in regard to using Dockerfiles.</span></span>

### <a name="scenario-1-containerized-aspnet-web-apps"></a><span data-ttu-id="14d5c-157">Scénario 1 : Applications Web ASP.NET conteneurisées</span><span class="sxs-lookup"><span data-stu-id="14d5c-157">Scenario 1: Containerized ASP.NET web apps</span></span>

<span data-ttu-id="14d5c-158">Figure ci-dessous montre le scénario pour les applications d’applications web héritées de containerized eShop.</span><span class="sxs-lookup"><span data-stu-id="14d5c-158">Figure below shows the scenario for containerized eShop legacy web apps applications.</span></span>

![Diagramme d’architecture simplifié des applications de ASP.NET conteneurisées dans un environnement de développement](./media/image5-3.png)

### <a name="scenario-2-containerized-wcf-service"></a><span data-ttu-id="14d5c-160">Scénario 2 : Service WCF conteneurisé</span><span class="sxs-lookup"><span data-stu-id="14d5c-160">Scenario 2: Containerized WCF service</span></span>

<span data-ttu-id="14d5c-161">Figure ci-dessous montre le scénario d’une application à 3 niveaux avec un service WCF conteneurisé.</span><span class="sxs-lookup"><span data-stu-id="14d5c-161">Figure below shows the scenario for a 3-Tier app with a containerized WCF service.</span></span>

![Diagramme d’architecture simplifié du service WCF conteneurisé dans un environnement de développement](./media/image5-3.5.png)

### <a name="benefits"></a><span data-ttu-id="14d5c-163">Avantages</span><span class="sxs-lookup"><span data-stu-id="14d5c-163">Benefits</span></span>

<span data-ttu-id="14d5c-164">Il y a des avantages à exécuter votre application monolithique dans un récipient.</span><span class="sxs-lookup"><span data-stu-id="14d5c-164">There are advantages to running your monolithic application in a container.</span></span> <span data-ttu-id="14d5c-165">Tout d’abord, vous créez une image pour l’application.</span><span class="sxs-lookup"><span data-stu-id="14d5c-165">First, you create an image for the application.</span></span> <span data-ttu-id="14d5c-166">À partir de ce moment, chaque déploiement se déroule dans le même environnement.</span><span class="sxs-lookup"><span data-stu-id="14d5c-166">From that point on, every deployment runs in the same environment.</span></span> <span data-ttu-id="14d5c-167">Chaque conteneur utilise la même version OS, a la même version de dépendances installées, utilise la même version cadre .NET, et est construit en utilisant le même processus.</span><span class="sxs-lookup"><span data-stu-id="14d5c-167">Every container uses the same OS version, has the same version of dependencies installed, uses the same .NET framework version, and is built by using the same process.</span></span> <span data-ttu-id="14d5c-168">Fondamentalement, vous contrôlez les dépendances de votre application en utilisant une image Docker.</span><span class="sxs-lookup"><span data-stu-id="14d5c-168">Basically, you control the dependencies of your application by using a Docker image.</span></span> <span data-ttu-id="14d5c-169">Les dépendances voyagent avec l’application lorsque vous déployez les conteneurs.</span><span class="sxs-lookup"><span data-stu-id="14d5c-169">The dependencies travel with the application when you deploy the containers.</span></span>

<span data-ttu-id="14d5c-170">Un avantage supplémentaire est que les développeurs peuvent exécuter l’application dans l’environnement cohérent qui est fourni par Windows Containers.</span><span class="sxs-lookup"><span data-stu-id="14d5c-170">An additional benefit is that developers can run the application in the consistent environment that's provided by Windows Containers.</span></span> <span data-ttu-id="14d5c-171">Les problèmes qui n’apparaissent qu’avec certaines versions peuvent être repérés immédiatement, au lieu de faire surface dans un environnement de mise en scène ou de production.</span><span class="sxs-lookup"><span data-stu-id="14d5c-171">Issues that appear only with certain versions can be spotted immediately, instead of surfacing in a staging or production environment.</span></span> <span data-ttu-id="14d5c-172">Les différences dans les environnements de développement utilisés par les membres de l’équipe de développement sont moins importantes lorsque les applications s’exécutent dans des conteneurs.</span><span class="sxs-lookup"><span data-stu-id="14d5c-172">Differences in development environments used by members of the development team matter less when applications run in containers.</span></span>

<span data-ttu-id="14d5c-173">Les applications conteneurisées ont également une courbe d’échelle plus plate.</span><span class="sxs-lookup"><span data-stu-id="14d5c-173">Containerized applications also have a flatter scale-out curve.</span></span> <span data-ttu-id="14d5c-174">Les applications conteneurisées vous permettent d’avoir plus d’instances d’application et de service (basées sur des conteneurs) dans une machine VM ou physique par rapport aux déploiements d’applications réguliers par machine.</span><span class="sxs-lookup"><span data-stu-id="14d5c-174">Containerized apps enable you to have more application and service instances (based on containers) in a VM or physical machine compared to regular application deployments per machine.</span></span> <span data-ttu-id="14d5c-175">Cela se traduit par une densité plus élevée et moins de ressources nécessaires, en particulier lorsque vous utilisez des orchestrateurs comme Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="14d5c-175">This translates to higher density and fewer required resources, especially when you use orchestrators like Kubernetes.</span></span>

<span data-ttu-id="14d5c-176">La conteneurisation, dans des situations idéales, ne nécessite\#aucune modification du code d’application (C ).</span><span class="sxs-lookup"><span data-stu-id="14d5c-176">Containerization, in ideal situations, does not require making any changes to the application code (C\#).</span></span> <span data-ttu-id="14d5c-177">Dans la plupart des scénarios, vous avez juste besoin des fichiers de métadonnées de déploiement Docker (fichiers Dockerfiles et Docker Compose).</span><span class="sxs-lookup"><span data-stu-id="14d5c-177">In most scenarios, you just need the Docker deployment metadata files (Dockerfiles and Docker Compose files).</span></span>

### <a name="next-steps"></a><span data-ttu-id="14d5c-178">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="14d5c-178">Next steps</span></span>

<span data-ttu-id="14d5c-179">Explorez ce contenu plus en profondeur sur le wiki GitHub :</span><span class="sxs-lookup"><span data-stu-id="14d5c-179">Explore this content more in-depth on the GitHub wiki:</span></span>

- [<span data-ttu-id="14d5c-180">Comment conteneuriser les applications Web .NET Framework avec Windows Containers et Docker</span><span class="sxs-lookup"><span data-stu-id="14d5c-180">How to containerize the .NET Framework web apps with Windows Containers and Docker</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/02.-How-to-containerize-the-.NET-Framework-web-apps-with-Windows-Containers-and-Docker)
- [<span data-ttu-id="14d5c-181">Ajout d’un soutien Docker à un service WCF</span><span class="sxs-lookup"><span data-stu-id="14d5c-181">Adding Docker Support to a WCF service</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/22.-Adding-Docker-Support)

## <a name="walkthrough-3-deploy-your-windows-containers-based-app-to-azure-vms"></a><span data-ttu-id="14d5c-182">Procédure pas à pas 3 : Déployez votre application Windows Containers sur les VM Azure</span><span class="sxs-lookup"><span data-stu-id="14d5c-182">Walkthrough 3: Deploy your Windows Containers-based app to Azure VMs</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="14d5c-183">Disponibilité technique de procédure pas à pas</span><span class="sxs-lookup"><span data-stu-id="14d5c-183">Technical walkthrough availability</span></span>

<span data-ttu-id="14d5c-184">La procédure technique complète est disponible dans le wiki GitPo eShopModernizing :<https://github.com/dotnet-architecture/eShopModernizing/wiki/06.-Deploying-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)></span><span class="sxs-lookup"><span data-stu-id="14d5c-184">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki: <https://github.com/dotnet-architecture/eShopModernizing/wiki/06.-Deploying-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)></span></span>

### <a name="overview"></a><span data-ttu-id="14d5c-185">Vue d’ensemble</span><span class="sxs-lookup"><span data-stu-id="14d5c-185">Overview</span></span>

<span data-ttu-id="14d5c-186">Le déploiement à un hôte Docker sur une machine virtuelle (VM) Windows Server 2016 dans Azure vous permet de configurer rapidement des environnements de développement/test/staging.</span><span class="sxs-lookup"><span data-stu-id="14d5c-186">Deploying to a Docker host on a Windows Server 2016 Virtual Machine (VM) in Azure lets you quickly set up development/test/staging environments.</span></span> <span data-ttu-id="14d5c-187">Il vous donne également un endroit commun pour les testeurs ou les utilisateurs professionnels pour valider l’application.</span><span class="sxs-lookup"><span data-stu-id="14d5c-187">It also gives you a common place for testers or business users to validate the app.</span></span> <span data-ttu-id="14d5c-188">Les VM peuvent également être des environnements de production d’infrastructure valides en tant que service (IaaS).</span><span class="sxs-lookup"><span data-stu-id="14d5c-188">VMs also can be valid Infrastructure as a Service (IaaS) production environments.</span></span>

### <a name="goals"></a><span data-ttu-id="14d5c-189">Objectifs</span><span class="sxs-lookup"><span data-stu-id="14d5c-189">Goals</span></span>

<span data-ttu-id="14d5c-190">Le but de cette procédure pas à pas est de vous montrer les multiples alternatives que vous avez lorsque vous déployez des conteneurs Windows dans les machines à sous Azure qui sont basées sur Windows Server 2016 ou les versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="14d5c-190">The goal of this walkthrough is to show you the multiple alternatives you have when you deploy Windows Containers to Azure VMs that are based on Windows Server 2016 or later versions.</span></span>

### <a name="scenarios"></a><span data-ttu-id="14d5c-191">Scénarios</span><span class="sxs-lookup"><span data-stu-id="14d5c-191">Scenarios</span></span>

<span data-ttu-id="14d5c-192">Plusieurs scénarios sont couverts dans cette procédure pas à pas.</span><span class="sxs-lookup"><span data-stu-id="14d5c-192">Several scenarios are covered in this walkthrough.</span></span>

#### <a name="scenario-a-deploy-to-an-azure-vm-from-a-dev-pc-through-docker-engine-connection"></a><span data-ttu-id="14d5c-193">Scénario A : Déploiement à une VM Azure à partir d’un PC dev via la connexion Docker Engine</span><span class="sxs-lookup"><span data-stu-id="14d5c-193">Scenario A: Deploy to an Azure VM from a dev PC through Docker Engine connection</span></span>

![Déployer sur une VM Azure à partir d’un PC dev via une connexion Docker Engine](./media/image5-4.png)

<span data-ttu-id="14d5c-195">**Figure 5-4.**</span><span class="sxs-lookup"><span data-stu-id="14d5c-195">**Figure 5-4.**</span></span> <span data-ttu-id="14d5c-196">Déployer sur une VM Azure à partir d’un PC dev via une connexion Docker Engine</span><span class="sxs-lookup"><span data-stu-id="14d5c-196">Deploy to an Azure VM from a dev PC through a Docker Engine connection</span></span>

#### <a name="scenario-b-deploy-to-an-azure-vm-through-a-docker-registry"></a><span data-ttu-id="14d5c-197">Scénario B : Déploiement à une VM Azure par le biais d’un registre Docker</span><span class="sxs-lookup"><span data-stu-id="14d5c-197">Scenario B: Deploy to an Azure VM through a Docker Registry</span></span>

![Déploiement à une VM Azure par le biais d’un registre Docker](./media/image5-5.png)

<span data-ttu-id="14d5c-199">**Figure 5-5.**</span><span class="sxs-lookup"><span data-stu-id="14d5c-199">**Figure 5-5.**</span></span> <span data-ttu-id="14d5c-200">Déploiement à une VM Azure par le biais d’un registre Docker</span><span class="sxs-lookup"><span data-stu-id="14d5c-200">Deploy to an Azure VM through a Docker Registry</span></span>

#### <a name="scenario-c-deploy-to-an-azure-vm-from-cicd-pipelines-in-azure-devops-services"></a><span data-ttu-id="14d5c-201">Scénario C : Déploiement à une VM Azure à partir des pipelines CI/CD dans Azure DevOps Services</span><span class="sxs-lookup"><span data-stu-id="14d5c-201">Scenario C: Deploy to an Azure VM from CI/CD pipelines in Azure DevOps Services</span></span>

![Déploiement dans une VM Azure à partir des pipelines CI/CD dans Azure DevOps Services](./media/image5-6.png)

<span data-ttu-id="14d5c-203">**Figure 5-6.**</span><span class="sxs-lookup"><span data-stu-id="14d5c-203">**Figure 5-6.**</span></span> <span data-ttu-id="14d5c-204">Déploiement dans une VM Azure à partir des pipelines CI/CD dans Azure DevOps Services</span><span class="sxs-lookup"><span data-stu-id="14d5c-204">Deploy to an Azure VM from CI/CD pipelines in Azure DevOps Services</span></span>

### <a name="azure-vms-for-windows-containers"></a><span data-ttu-id="14d5c-205">Sous-verre Azure pour les conteneurs Windows</span><span class="sxs-lookup"><span data-stu-id="14d5c-205">Azure VMs for Windows Containers</span></span>

<span data-ttu-id="14d5c-206">Les machines à sous Azure pour les conteneurs Windows sont des machines VM basées sur Windows Server 2016, Windows 10, ou des versions ultérieures, toutes deux avec Docker Engine mis en place.</span><span class="sxs-lookup"><span data-stu-id="14d5c-206">Azure VMs for Windows Containers are VMs based on Windows Server 2016, Windows 10, or later versions, both with Docker Engine set up.</span></span> <span data-ttu-id="14d5c-207">Dans la plupart des cas, Windows Server 2016 est utilisé dans les VM Azure.</span><span class="sxs-lookup"><span data-stu-id="14d5c-207">In most cases, Windows Server 2016 is used in the Azure VMs.</span></span>

<span data-ttu-id="14d5c-208">Azure fournit actuellement un VM nommé **Windows Server 2016 avec Conteneurs**.</span><span class="sxs-lookup"><span data-stu-id="14d5c-208">Azure currently provides a VM named **Windows Server 2016 with Containers**.</span></span> <span data-ttu-id="14d5c-209">Vous pouvez utiliser ce VM pour essayer la nouvelle fonctionnalité De conteneur Windows Server, avec Windows Server Core ou Windows Nano Server.</span><span class="sxs-lookup"><span data-stu-id="14d5c-209">You can use this VM to try the new Windows Server Container feature, with either Windows Server Core or Windows Nano Server.</span></span> <span data-ttu-id="14d5c-210">Les images de Container OS sont installées, puis la VM est prête à l’emploi avec Docker.</span><span class="sxs-lookup"><span data-stu-id="14d5c-210">Container OS images are installed, and then the VM is ready to use with Docker.</span></span>

### <a name="benefits"></a><span data-ttu-id="14d5c-211">Avantages</span><span class="sxs-lookup"><span data-stu-id="14d5c-211">Benefits</span></span>

<span data-ttu-id="14d5c-212">Bien que Windows Containers puisse être déployé sur place Windows Server 2016 VMs, lorsque vous vous déployez à Azure, vous obtenez un moyen plus facile de démarrer, avec des VM Windows Server contenants prêts à l’emploi.</span><span class="sxs-lookup"><span data-stu-id="14d5c-212">Although Windows Containers can be deployed to on-premises Windows Server 2016 VMs, when you deploy to Azure, you get an easier way to get started, with ready-to-use Windows Server Container VMs.</span></span> <span data-ttu-id="14d5c-213">Vous obtenez également un emplacement en ligne commun qui est accessible aux testeurs, et l’évolutivité automatique grâce à Azure ensembles de machines virtuelles.</span><span class="sxs-lookup"><span data-stu-id="14d5c-213">You also get a common online location that’s accessible to testers, and automatic scalability through Azure virtual machine scale sets.</span></span>

### <a name="next-steps"></a><span data-ttu-id="14d5c-214">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="14d5c-214">Next steps</span></span>

<span data-ttu-id="14d5c-215">Explorez ce contenu plus en profondeur sur le wiki GitHub :</span><span class="sxs-lookup"><span data-stu-id="14d5c-215">Explore this content more in-depth on the GitHub wiki:</span></span>

<https://github.com/dotnet-architecture/eShopModernizing/wiki/06.-Deploying-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)>

## <a name="walkthrough-4-deploy-your-windows-containers-based-apps-to-azure-container-instances-aci"></a><span data-ttu-id="14d5c-216">Procédure pas à pas 4 : Déployez vos applications basées sur des conteneurs Windows dans Azure Container Instances (ACI)</span><span class="sxs-lookup"><span data-stu-id="14d5c-216">Walkthrough 4: Deploy your Windows Containers-based apps to Azure Container Instances (ACI)</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="14d5c-217">Disponibilité technique de procédure pas à pas</span><span class="sxs-lookup"><span data-stu-id="14d5c-217">Technical walkthrough availability</span></span>

<span data-ttu-id="14d5c-218">La procédure technique complète est disponible dans le wiki GitPo eShopModernizing :</span><span class="sxs-lookup"><span data-stu-id="14d5c-218">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

<span data-ttu-id="14d5c-219">[Déploiement des applications à l’ACI (Azure Container Instances)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances))</span><span class="sxs-lookup"><span data-stu-id="14d5c-219">[Deploying the Apps to ACI (Azure Container Instances)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances))</span></span>

### <a name="overview"></a><span data-ttu-id="14d5c-220">Vue d’ensemble</span><span class="sxs-lookup"><span data-stu-id="14d5c-220">Overview</span></span>

<span data-ttu-id="14d5c-221">[Azure Container Instances (ACI)](https://docs.microsoft.com/azure/container-instances/) est le moyen le plus rapide d’avoir un environnement de test/de mise en scène de conteneurs où vous pouvez déployer des instances uniques de conteneurs.</span><span class="sxs-lookup"><span data-stu-id="14d5c-221">[Azure Container Instances (ACI)](https://docs.microsoft.com/azure/container-instances/) is the quickest way to have a Containers dev/test/staging environment where you can deploy single instances of containers.</span></span>

### <a name="goals"></a><span data-ttu-id="14d5c-222">Objectifs</span><span class="sxs-lookup"><span data-stu-id="14d5c-222">Goals</span></span>

<span data-ttu-id="14d5c-223">Ce pas-là vous montre les principaux scénarios lors du déploiement de conteneurs Windows dans Azure Container Instances (ACI) et comment vous pouvez déployer eShopModernizing Apps dans ACI.</span><span class="sxs-lookup"><span data-stu-id="14d5c-223">This walkthrough shows you the main scenarios when deploying Windows Containers to Azure Container Instances (ACI) and how you can deploy eShopModernizing Apps into ACI.</span></span>

### <a name="scenarios"></a><span data-ttu-id="14d5c-224">Scénarios</span><span class="sxs-lookup"><span data-stu-id="14d5c-224">Scenarios</span></span>

<span data-ttu-id="14d5c-225">Il peut y avoir des variations sur le déploiement des applications eShopModernizing dans ACI telles que le déploiement d’une seule ou l’autre des applications (application MVC, application WebForms ou service WCF).</span><span class="sxs-lookup"><span data-stu-id="14d5c-225">There can be variations about deploying the eShopModernizing apps into ACI such as deploying just one or all of the apps (MVC app, WebForms app or WCF service).</span></span> <span data-ttu-id="14d5c-226">Dans le scénario ci-dessous, vous pouvez voir l’application ASP.NET MVC ainsi que le conteneur SQL Server qui sont tous deux déployés sous forme de conteneurs dans ACI (Azure Container Instances).</span><span class="sxs-lookup"><span data-stu-id="14d5c-226">In the following scenario shown below you can see the ASP.NET MVC app plus the SQL Server container both of them deployed as containers into ACI (Azure Container Instances).</span></span>

![Déploiement à l’ACI à partir d’un environnement de développement](./media/image5-3.5.6.png)

### <a name="benefits"></a><span data-ttu-id="14d5c-228">Avantages</span><span class="sxs-lookup"><span data-stu-id="14d5c-228">Benefits</span></span>

<span data-ttu-id="14d5c-229">Azure Container Instances facilite la création et la gestion de conteneurs Docker dans Azure, sans avoir à approvisionner les machines virtuelles ou à adopter un service de niveau supérieur.</span><span class="sxs-lookup"><span data-stu-id="14d5c-229">Azure Container Instances makes it easy to create and manage Docker containers in Azure, without having to provision virtual machines or adopt a higher-level service.</span></span> <span data-ttu-id="14d5c-230">Avec ACI, vous pouvez déployer directement un conteneur Windows dans Azure et l’exposer à Internet avec un nom de domaine entièrement qualifié (FQDN) en quelques secondes (à condition que vous ayez l’image De conteneur Windows prêt dans un registre Docker comme Docker Hub ou Azure Container Registre).</span><span class="sxs-lookup"><span data-stu-id="14d5c-230">With ACI, you can directly deploy a Windows container in Azure and expose it to the internet with a fully qualified domain name (FQDN) in a matter of seconds (Provided that you have the Windows Container image ready in a Docker registry like Docker Hub or Azure Container Registry).</span></span>

### <a name="considerations"></a><span data-ttu-id="14d5c-231">Considérations</span><span class="sxs-lookup"><span data-stu-id="14d5c-231">Considerations</span></span>

<span data-ttu-id="14d5c-232">Déployer des conteneurs Windows avec un cadre .NET complet / ASP.NET ou SQL Server dans Azure Container Instances (ACI) n’est pas aussi rapide que le déploiement à un hôte Docker régulier (comme un serveur Windows 2016 avec des conteneurs Windows) parce que le L’image Docker doit être téléchargée (tirée du registre Docker) à chaque fois et les tailles de l’image de conteneur SQL (15,1 Go) et l’image de conteneur ASP.NET (13,9 Go) sont significativement grandes, cependant, il est beaucoup moins cher que de maintenir votre propre hôte docker (en ligne en permanence Windows Server 2016 avec Windows Containers VM en Azure) sans oublier tout un orchestrateur comme Kubernetes à Azure (AKS) qui est, d’autre part, un excellent choix pour les déploiements de production.</span><span class="sxs-lookup"><span data-stu-id="14d5c-232">Deploying Windows Containers with either full .NET Framework / ASP.NET or SQL Server into Azure Container Instances (ACI) is not quite as fast as deploying to a regular Docker Host (like a Windows Server 2016 with Windows Containers) because the Docker image has to be downloaded (pulled from the Docker registry) every time and the sizes of the SQL container image (15.1 GB) and the ASP.NET container image (13.9 GB) are significantly large, however it is much cheaper than maintaining your own docker host (permanently on-line Windows Server 2016 with Windows Containers VM in Azure) not to mention a whole orchestrator like Kubernetes in Azure (AKS) which is, on the other hand, a great choice for production deployments.</span></span>

<span data-ttu-id="14d5c-233">En conclusion principale, l’utilisation d’Azure Container Instances est une option très convaincante pour les scénarios Dev/Test et pour les pipelines CI/CD.</span><span class="sxs-lookup"><span data-stu-id="14d5c-233">As main conclusion, using Azure Container Instances is a very compelling option for Dev/Test scenarios and for CI/CD pipelines.</span></span>

## <a name="next-steps"></a><span data-ttu-id="14d5c-234">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="14d5c-234">Next steps</span></span>

<span data-ttu-id="14d5c-235">Explorez ce contenu plus en profondeur sur le wiki GitHub :</span><span class="sxs-lookup"><span data-stu-id="14d5c-235">Explore this content more in-depth on the GitHub wiki:</span></span>

[https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances))

## <a name="walkthrough-5-deploy-your-windows-containers-based-apps-to-kubernetes-in-azure-container-service"></a><span data-ttu-id="14d5c-236">Procédure pas à pas 5 : Déployez vos applications basées sur les conteneurs Windows vers Kubernetes dans le service de conteneurs Azure</span><span class="sxs-lookup"><span data-stu-id="14d5c-236">Walkthrough 5: Deploy your Windows Containers-based apps to Kubernetes in Azure Container Service</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="14d5c-237">Disponibilité technique de procédure pas à pas</span><span class="sxs-lookup"><span data-stu-id="14d5c-237">Technical walkthrough availability</span></span>

<span data-ttu-id="14d5c-238">La procédure technique complète est disponible dans le wiki GitPo eShopModernizing :</span><span class="sxs-lookup"><span data-stu-id="14d5c-238">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

<https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-CI-CD)>

### <a name="overview"></a><span data-ttu-id="14d5c-239">Vue d’ensemble</span><span class="sxs-lookup"><span data-stu-id="14d5c-239">Overview</span></span>

<span data-ttu-id="14d5c-240">Une application basée sur Windows Containers devra rapidement utiliser des plates-formes, s’éloignant encore plus des VM IaaS.</span><span class="sxs-lookup"><span data-stu-id="14d5c-240">An application that's based on Windows Containers will quickly need to use platforms, moving even further away from IaaS VMs.</span></span> <span data-ttu-id="14d5c-241">Cela est nécessaire pour atteindre facilement une grande évolutivité et une meilleure évolutivité automatisée, et pour une amélioration significative des déploiements automatisés et de la version.</span><span class="sxs-lookup"><span data-stu-id="14d5c-241">This is needed to easily achieve high scalability and better automated scalability, and for a significant improvement in automated deployments and versioning.</span></span> <span data-ttu-id="14d5c-242">Vous pouvez atteindre ces objectifs en utilisant l’orchestrateur [Kubernetes](https://kubernetes.io/), disponible dans [Azure Container Services](https://azure.microsoft.com/services/container-service/).</span><span class="sxs-lookup"><span data-stu-id="14d5c-242">You can achieve these goals by using the orchestrator [Kubernetes](https://kubernetes.io/), available in [Azure Container Services](https://azure.microsoft.com/services/container-service/).</span></span>

### <a name="goals"></a><span data-ttu-id="14d5c-243">Objectifs</span><span class="sxs-lookup"><span data-stu-id="14d5c-243">Goals</span></span>

<span data-ttu-id="14d5c-244">L’objectif de cette procédure pas à pas est d’apprendre à déployer une application basée sur windows Container à Kubernetes (également appelé *K8s*) dans Azure Container Service.</span><span class="sxs-lookup"><span data-stu-id="14d5c-244">The goal of this walkthrough is to learn how to deploy a Windows Container–based application to Kubernetes (also called *K8s*) in Azure Container Service.</span></span> <span data-ttu-id="14d5c-245">Le déploiement à Kubernetes à partir de zéro est un processus en deux étapes :</span><span class="sxs-lookup"><span data-stu-id="14d5c-245">Deploying to Kubernetes from scratch is a two-step process:</span></span>

1. <span data-ttu-id="14d5c-246">Déployez un cluster Kubernetes au service de conteneurs Azure.</span><span class="sxs-lookup"><span data-stu-id="14d5c-246">Deploy a Kubernetes cluster to Azure Container Service.</span></span>

2. <span data-ttu-id="14d5c-247">Déployez l’application et les ressources connexes au cluster Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="14d5c-247">Deploy the application and related resources to the Kubernetes cluster.</span></span>

### <a name="scenarios"></a><span data-ttu-id="14d5c-248">Scénarios</span><span class="sxs-lookup"><span data-stu-id="14d5c-248">Scenarios</span></span>

#### <a name="scenario-a-deploy-directly-to-a-kubernetes-cluster-from-a-dev-environment"></a><span data-ttu-id="14d5c-249">Scénario A : Déploiement directement sur un cluster Kubernetes à partir d’un environnement de dev</span><span class="sxs-lookup"><span data-stu-id="14d5c-249">Scenario A: Deploy directly to a Kubernetes cluster from a dev environment</span></span>

![Déploiement directement dans un cluster Kubernetes à partir d’un environnement de développement](./media/image5-7.png)

<span data-ttu-id="14d5c-251">**Figure 5-7.**</span><span class="sxs-lookup"><span data-stu-id="14d5c-251">**Figure 5-7.**</span></span> <span data-ttu-id="14d5c-252">Déploiement directement dans un cluster Kubernetes à partir d’un environnement de développement</span><span class="sxs-lookup"><span data-stu-id="14d5c-252">Deploy directly to a Kubernetes cluster from a development environment</span></span>

#### <a name="scenario-b-deploy-to-a-kubernetes-cluster-from-cicd-pipelines-in-azure-devops-services"></a><span data-ttu-id="14d5c-253">Scénario B : Déploiement dans un cluster Kubernetes à partir des pipelines CI/CD dans Azure DevOps Services</span><span class="sxs-lookup"><span data-stu-id="14d5c-253">Scenario B: Deploy to a Kubernetes cluster from CI/CD pipelines in Azure DevOps Services</span></span>

![Déploiement dans un cluster Kubernetes à partir des pipelines CI/CD dans Azure DevOps Services](./media/image5-8.png)

<span data-ttu-id="14d5c-255">**Figure 5-8.**</span><span class="sxs-lookup"><span data-stu-id="14d5c-255">**Figure 5-8.**</span></span> <span data-ttu-id="14d5c-256">Déploiement dans un cluster Kubernetes à partir des pipelines CI/CD dans Azure DevOps Services</span><span class="sxs-lookup"><span data-stu-id="14d5c-256">Deploy to a Kubernetes cluster from CI/CD pipelines in Azure DevOps Services</span></span>

### <a name="benefits"></a><span data-ttu-id="14d5c-257">Avantages</span><span class="sxs-lookup"><span data-stu-id="14d5c-257">Benefits</span></span>

<span data-ttu-id="14d5c-258">Le déploiement à un cluster à Kubernetes existe de nombreux avantages.</span><span class="sxs-lookup"><span data-stu-id="14d5c-258">There are many benefits to deploying to a cluster in Kubernetes.</span></span> <span data-ttu-id="14d5c-259">Le plus grand avantage est que vous obtenez un environnement prêt à la production dans lequel vous pouvez échelle de l’application en fonction du nombre d’instances de conteneurs que vous souhaitez utiliser (évolutivité intérieure dans les nœuds existants), et en fonction du nombre de nœuds ou de VM dans le cluster ( évolutivité globale du cluster).</span><span class="sxs-lookup"><span data-stu-id="14d5c-259">The biggest benefit is that you get a production-ready environment in which you can scale out the application based on the number of container instances you want to use (inner-scalability in the existing nodes), and based on the number of nodes or VMs in the cluster (global scalability of the cluster).</span></span>

<span data-ttu-id="14d5c-260">Azure Container Service optimise les outils et technologies open source populaires spécifiquement pour Azure.</span><span class="sxs-lookup"><span data-stu-id="14d5c-260">Azure Container Service optimizes popular open-source tools and technologies specifically for Azure.</span></span> <span data-ttu-id="14d5c-261">Vous obtenez une solution ouverte qui offre la portabilité, à la fois pour vos conteneurs et pour votre configuration d’application.</span><span class="sxs-lookup"><span data-stu-id="14d5c-261">You get an open solution that offers portability, both for your containers and for your application configuration.</span></span> <span data-ttu-id="14d5c-262">Vous sélectionnez la taille, le nombre d’hôtes et l’orchestrateur tools-Container Service gère tout le reste.</span><span class="sxs-lookup"><span data-stu-id="14d5c-262">You select the size, the number of hosts, and the orchestrator tools-Container Service handles everything else.</span></span>

<span data-ttu-id="14d5c-263">Avec Kubernetes, les développeurs peuvent passer de la réflexion sur les machines physiques et virtuelles à la planification d’une infrastructure centrée sur les conteneurs qui facilite les capacités suivantes, entre autres :</span><span class="sxs-lookup"><span data-stu-id="14d5c-263">With Kubernetes, developers can progress from thinking about physical and virtual machines, to planning a container-centric infrastructure that facilitates the following capabilities, among others:</span></span>

- <span data-ttu-id="14d5c-264">Applications basées sur plusieurs conteneurs</span><span class="sxs-lookup"><span data-stu-id="14d5c-264">Applications based on multiple containers</span></span>

- <span data-ttu-id="14d5c-265">Réplique des instances de conteneurs et autoscalage horizontal</span><span class="sxs-lookup"><span data-stu-id="14d5c-265">Replicating container instances and horizontal autoscaling</span></span>

- <span data-ttu-id="14d5c-266">Nommer et découvrir (par exemple, DNS interne)</span><span class="sxs-lookup"><span data-stu-id="14d5c-266">Naming and discovering (for example, internal DNS)</span></span>

- <span data-ttu-id="14d5c-267">Équilibrer les charges</span><span class="sxs-lookup"><span data-stu-id="14d5c-267">Balancing loads</span></span>

- <span data-ttu-id="14d5c-268">Mises à jour de roulement</span><span class="sxs-lookup"><span data-stu-id="14d5c-268">Rolling updates</span></span>

- <span data-ttu-id="14d5c-269">Distribuer des secrets</span><span class="sxs-lookup"><span data-stu-id="14d5c-269">Distributing secrets</span></span>

- <span data-ttu-id="14d5c-270">Vérifications de santé des demandes</span><span class="sxs-lookup"><span data-stu-id="14d5c-270">Application health checks</span></span>

## <a name="next-steps"></a><span data-ttu-id="14d5c-271">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="14d5c-271">Next steps</span></span>

<span data-ttu-id="14d5c-272">Explorez ce contenu plus en profondeur sur le wiki GitHub :<https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-CI-CD)></span><span class="sxs-lookup"><span data-stu-id="14d5c-272">Explore this content more in-depth on the GitHub wiki: <https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-CI-CD)></span></span>

## <a name="walkthrough-6-deploy-your-windows-containers-based-apps-to-azure-app-service-for-containers"></a><span data-ttu-id="14d5c-273">Procédure pas à pas 6 : Déployez vos applications basées sur les conteneurs Windows au service d’applications Azure pour les conteneurs</span><span class="sxs-lookup"><span data-stu-id="14d5c-273">Walkthrough 6: Deploy your Windows Containers-based apps to Azure App Service for Containers</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="14d5c-274">Disponibilité technique de procédure pas à pas</span><span class="sxs-lookup"><span data-stu-id="14d5c-274">Technical walkthrough availability</span></span>

<span data-ttu-id="14d5c-275">La procédure technique complète est disponible dans le wiki GitPo eShopModernizing :</span><span class="sxs-lookup"><span data-stu-id="14d5c-275">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

<https://github.com/dotnet-architecture/eShopModernizing/wiki/Deploy-Windows-Container-to-Azure-App-Service>

### <a name="overview"></a><span data-ttu-id="14d5c-276">Vue d’ensemble</span><span class="sxs-lookup"><span data-stu-id="14d5c-276">Overview</span></span>

<span data-ttu-id="14d5c-277">Une simple application conteneurisée utilisant des conteneurs Windows peut facilement être déployée sur Azure App Service for Containers.</span><span class="sxs-lookup"><span data-stu-id="14d5c-277">A simple containerized application using Windows Containers can easily be deployed to Azure App Service for Containers.</span></span> <span data-ttu-id="14d5c-278">Il s’agit de l’approche recommandée pour la plupart des applications basées sur les conteneurs Windows.</span><span class="sxs-lookup"><span data-stu-id="14d5c-278">This is the recommended approach for most Windows Container-based applications.</span></span>

### <a name="goals"></a><span data-ttu-id="14d5c-279">Objectifs</span><span class="sxs-lookup"><span data-stu-id="14d5c-279">Goals</span></span>

<span data-ttu-id="14d5c-280">L’objectif de cette procédure pas à pas est d’apprendre à déployer une application basée sur windows Container à Azure App Service for Containers à partir d’un registre (Docker Hub ou Azure Container Registry).</span><span class="sxs-lookup"><span data-stu-id="14d5c-280">The goal of this walkthrough is to learn how to deploy a Windows Container–based application to Azure App Service for Containers from a registry (Docker Hub or Azure Container Registry).</span></span>

### <a name="scenario"></a><span data-ttu-id="14d5c-281">Scénario</span><span class="sxs-lookup"><span data-stu-id="14d5c-281">Scenario</span></span>

![Déployer l’application Windows Container sur Azure App Service for Containers](./media/image5-11.png)

### <a name="benefits"></a><span data-ttu-id="14d5c-283">Avantages</span><span class="sxs-lookup"><span data-stu-id="14d5c-283">Benefits</span></span>

<span data-ttu-id="14d5c-284">Le déploiement au service d’applications Azure pour les conteneurs offre les avantages des conteneurs jumelés aux avantages PaaS du service d’application Azure.</span><span class="sxs-lookup"><span data-stu-id="14d5c-284">Deploying to Azure App Service for Containers offers the benefits of containers paired with the PaaS benefits of Azure App Service.</span></span> <span data-ttu-id="14d5c-285">Le service d’application peut facilement être mis à l’échelle verticalement et horizontalement, et peut être configuré à l’échelle automatique pour répondre aux demandes changeantes.</span><span class="sxs-lookup"><span data-stu-id="14d5c-285">The app service can easily be scaled both vertically and horizontally, and can be configured to autoscale to meet changing demands.</span></span> <span data-ttu-id="14d5c-286">Les mises à jour peuvent être effectuées avec zéro temps d’arrêt et la configuration du déploiement continu à partir d’un registre est facilement configurée ainsi.</span><span class="sxs-lookup"><span data-stu-id="14d5c-286">Updates can be performed with zero downtime and configuration of continuous deployment from a registry is easily configured as well.</span></span>

## <a name="next-steps"></a><span data-ttu-id="14d5c-287">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="14d5c-287">Next steps</span></span>

<span data-ttu-id="14d5c-288">Explorez ce contenu plus en profondeur sur le wiki GitHub :<https://github.com/dotnet-architecture/eShopModernizing/wiki/Deploy-Windows-Container-to-Azure-App-Service></span><span class="sxs-lookup"><span data-stu-id="14d5c-288">Explore this content more in-depth on the GitHub wiki: <https://github.com/dotnet-architecture/eShopModernizing/wiki/Deploy-Windows-Container-to-Azure-App-Service></span></span>

> [!div class="step-by-step"]
> <span data-ttu-id="14d5c-289">[Suivant précédent](modernize-existing-apps-to-cloud-optimized/migrate-to-hybrid-cloud-scenarios.md)
> [Next](conclusions.md)</span><span class="sxs-lookup"><span data-stu-id="14d5c-289">[Previous](modernize-existing-apps-to-cloud-optimized/migrate-to-hybrid-cloud-scenarios.md)
[Next](conclusions.md)</span></span> <!-- Next Chapter -->
