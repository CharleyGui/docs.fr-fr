---
title: Procédures pas à pas et vue d’ensemble technique pour le démarrage
description: Moderniser des applications .NET existantes avec des conteneurs Cloud et Windows Azure | Procédures pas à pas et présentation technique de la prise en main
ms.date: 04/28/2018
ms.openlocfilehash: 98d33b13d2b28bfe1c35894df45e525cff0520c1
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91172142"
---
# <a name="walkthroughs-and-technical-get-started-overview"></a><span data-ttu-id="1f254-103">Procédures pas à pas et vue d’ensemble technique pour le démarrage</span><span class="sxs-lookup"><span data-stu-id="1f254-103">Walkthroughs and technical get started overview</span></span>

<span data-ttu-id="1f254-104">Pour limiter la taille de ce livre électronique, des documents techniques supplémentaires et des procédures pas à pas complètes ont été mis à disposition dans un référentiel GitHub.</span><span class="sxs-lookup"><span data-stu-id="1f254-104">To limit the size of this e-book, additional technical documentation and the full walkthroughs were made available in a GitHub repository.</span></span> <span data-ttu-id="1f254-105">La série de procédures pas à pas en ligne qui sont décrites dans ce chapitre décrit la configuration étape par étape des environnements multiples basés sur des conteneurs Windows et le déploiement sur Azure.</span><span class="sxs-lookup"><span data-stu-id="1f254-105">The online series of walkthroughs that is described in this chapter covers the step-by-step setup of the multiple environments that are based on Windows Containers, and deployment to Azure.</span></span>

<span data-ttu-id="1f254-106">Les sections suivantes expliquent ce que fait chaque procédure pas à pas, ses objectifs et sa vision de haut niveau, et fournit un diagramme des tâches impliquées.</span><span class="sxs-lookup"><span data-stu-id="1f254-106">The following sections explain what each walkthrough is about, its objectives and high-level vision, and provides a diagram of the tasks that are involved.</span></span> <span data-ttu-id="1f254-107">Vous pouvez vous procurer les procédures pas-à-pas dans le wiki *eShopModernizing* Apps GitHub référentiel à l’adresse <https://github.com/dotnet-architecture/eShopModernizing/wiki> .</span><span class="sxs-lookup"><span data-stu-id="1f254-107">You can get the walkthroughs themselves in the *eShopModernizing* apps GitHub repo wiki at <https://github.com/dotnet-architecture/eShopModernizing/wiki>.</span></span>

## <a name="technical-walkthrough-list"></a><span data-ttu-id="1f254-108">Liste des procédures pas à pas</span><span class="sxs-lookup"><span data-stu-id="1f254-108">Technical walkthrough list</span></span>

<span data-ttu-id="1f254-109">Les procédures pas à pas suivantes de prise en main fournissent des conseils techniques cohérents et complets pour les exemples d’applications que vous pouvez passer en utilisant des conteneurs, puis vous déplacer en utilisant plusieurs choix de déploiement dans Azure.</span><span class="sxs-lookup"><span data-stu-id="1f254-109">The following get-started walkthroughs provide consistent and comprehensive technical guidance for sample apps that you can lift and shift by using containers, and then move by using multiple deployment choices in Azure.</span></span>

<span data-ttu-id="1f254-110">Chacune des procédures pas à pas suivantes utilise les nouveaux exemples d’applications eShopLegacy et eShopModernizing, qui sont disponibles sur GitHub à l’adresse <https://github.com/dotnet-architecture/eShopModernizing> .</span><span class="sxs-lookup"><span data-stu-id="1f254-110">Each of the following walkthroughs uses the new sample eShopLegacy and eShopModernizing apps, which are available on GitHub at <https://github.com/dotnet-architecture/eShopModernizing>.</span></span>

- <span data-ttu-id="1f254-111">**Visite guidée des applications héritées eShop (applications de référence à moderniser)**</span><span class="sxs-lookup"><span data-stu-id="1f254-111">**Tour of eShop legacy apps (baseline apps to modernize)**</span></span>

- <span data-ttu-id="1f254-112">**Créer un conteneur pour vos applications Web ASP.NET existantes (WebForms & MVC) avec des conteneurs Windows**</span><span class="sxs-lookup"><span data-stu-id="1f254-112">**Containerize your existing ASP.NET web apps (WebForms & MVC) with Windows Containers**</span></span>

- <span data-ttu-id="1f254-113">**Emconteneurr vos services WCF existants (applications multiniveaux) avec des conteneurs Windows**</span><span class="sxs-lookup"><span data-stu-id="1f254-113">**Containerize your existing WCF services (N-Tier apps) with Windows Containers**</span></span>

- <span data-ttu-id="1f254-114">**Déployer votre application basée sur des conteneurs Windows sur des machines virtuelles Azure**</span><span class="sxs-lookup"><span data-stu-id="1f254-114">**Deploy your Windows Containers-based app to Azure VMs**</span></span>

- <span data-ttu-id="1f254-115">**Déployez vos applications basées sur des conteneurs Windows sur Kubernetes dans Azure Container Service**</span><span class="sxs-lookup"><span data-stu-id="1f254-115">**Deploy your Windows Containers-based apps to Kubernetes in Azure Container Service**</span></span>

## <a name="walkthrough-1-tour-of-eshop-legacy-apps"></a><span data-ttu-id="1f254-116">Procédure pas à pas 1 : présentation des applications héritées eShop</span><span class="sxs-lookup"><span data-stu-id="1f254-116">Walkthrough 1: Tour of eShop legacy apps</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="1f254-117">Disponibilité des procédures techniques</span><span class="sxs-lookup"><span data-stu-id="1f254-117">Technical walkthrough availability</span></span>

<span data-ttu-id="1f254-118">La procédure pas à pas complète technique est disponible dans le wiki eShopModernizing GitHub référentiel :</span><span class="sxs-lookup"><span data-stu-id="1f254-118">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

[<span data-ttu-id="1f254-119">procédures pas à pas du wiki eShopModernizing</span><span class="sxs-lookup"><span data-stu-id="1f254-119">eShopModernizing wiki walkthroughs</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki)

### <a name="overview"></a><span data-ttu-id="1f254-120">Vue d’ensemble</span><span class="sxs-lookup"><span data-stu-id="1f254-120">Overview</span></span>

<span data-ttu-id="1f254-121">Dans cette procédure pas à pas, vous pouvez explorer l’implémentation initiale de trois exemples d’applications héritées.</span><span class="sxs-lookup"><span data-stu-id="1f254-121">In this walkthrough, you can explore the initial implementation of three sample legacy applications.</span></span> <span data-ttu-id="1f254-122">Les deux premiers exemples d’applications Web ont une architecture monolithique et ont été créés à l’aide de ASP.NET classiques.</span><span class="sxs-lookup"><span data-stu-id="1f254-122">The first two sample web apps have a monolithic architecture, and were created by using classic ASP.NET.</span></span> <span data-ttu-id="1f254-123">Une application est basée sur ASP.NET 4. x MVC ; la seconde application est basée sur ASP.NET 4. x Web Forms.</span><span class="sxs-lookup"><span data-stu-id="1f254-123">One application is based on ASP.NET 4.x MVC; the second application is based on ASP.NET 4.x Web Forms.</span></span>
<span data-ttu-id="1f254-124">La troisième application est une application à trois niveaux composée par une application WinForms client et un service de Windows Communication Foundation côté serveur [(WCF)](../../framework/wcf/whats-wcf.md) .</span><span class="sxs-lookup"><span data-stu-id="1f254-124">The third app is a 3-Tier app composed by a client WinForms app and a server-side [Windows Communication Foundation (WCF)](../../framework/wcf/whats-wcf.md) service.</span></span>

<span data-ttu-id="1f254-125">Toutes ces applications sont disponibles sur le [EShopModernizing GitHub référentiel](https://github.com/dotnet-architecture/eShopModernizing).</span><span class="sxs-lookup"><span data-stu-id="1f254-125">All these applications are available at the [eShopModernizing GitHub repo](https://github.com/dotnet-architecture/eShopModernizing).</span></span>

### <a name="goals"></a><span data-ttu-id="1f254-126">Objectifs</span><span class="sxs-lookup"><span data-stu-id="1f254-126">Goals</span></span>

<span data-ttu-id="1f254-127">L’objectif principal de cette procédure pas à pas est simplement de se familiariser avec ces applications et avec leur code et leur configuration.</span><span class="sxs-lookup"><span data-stu-id="1f254-127">The main goal of this walkthrough is simply to get familiar with these apps, and with their code and configuration.</span></span> <span data-ttu-id="1f254-128">Vous pouvez configurer les applications afin qu’elles génèrent et utilisent des données fictives, sans utiliser la base de données SQL, à des fins de test.</span><span class="sxs-lookup"><span data-stu-id="1f254-128">You can configure the apps so that they generate and use mock data, without using the SQL database, for testing purposes.</span></span> <span data-ttu-id="1f254-129">Cette configuration facultative est basée sur l’injection de dépendances, de façon découplée.</span><span class="sxs-lookup"><span data-stu-id="1f254-129">This optional config is based on dependency injection, in a decoupled way.</span></span>

### <a name="scenario-1-aspnet-web-apps"></a><span data-ttu-id="1f254-130">Scénario 1 : applications Web ASP.NET</span><span class="sxs-lookup"><span data-stu-id="1f254-130">Scenario 1: ASP.NET Web apps</span></span>

<span data-ttu-id="1f254-131">La figure ci-dessous illustre le scénario simple des applications Web ASP.NET héritées d’origine.</span><span class="sxs-lookup"><span data-stu-id="1f254-131">The figure below shows the simple scenario of the original legacy ASP.NET web applications.</span></span>

![Scénario d’architecture simple des applications Web ASP.NET héritées d’origine](./media/image5-1.png)

<span data-ttu-id="1f254-133">Du point de vue d’un domaine d’entreprise, les deux applications offrent les mêmes fonctionnalités de gestion de catalogue.</span><span class="sxs-lookup"><span data-stu-id="1f254-133">From a business domain perspective, both apps offer the same catalog management features.</span></span> <span data-ttu-id="1f254-134">Les membres de l’équipe eShop Enterprise utilisent l’application pour afficher et modifier le catalogue de produits.</span><span class="sxs-lookup"><span data-stu-id="1f254-134">Members of the eShop enterprise team would use the app to view and edit the product catalog.</span></span>

<span data-ttu-id="1f254-135">La figure suivante montre les captures d’écran initiales de l’application.</span><span class="sxs-lookup"><span data-stu-id="1f254-135">The next figure shows the initial app screenshots.</span></span>

![Applications ASP.NET MVC et ASP.NET Web Forms (technologies existantes/héritées)](./media/image5-2.png)

<span data-ttu-id="1f254-137">Les dépendances dans ASP.NET 4. x ou les versions antérieures (pour MVC ou pour Web Forms) signifient que ces applications ne s’exécutent pas sur .NET Core, sauf si le code est entièrement réécrit à l’aide de ASP.NET Core MVC.</span><span class="sxs-lookup"><span data-stu-id="1f254-137">Dependencies in ASP.NET 4.x or earlier versions (either for MVC or for Web Forms) means that these applications won't run on .NET Core unless the code is fully rewritten by using ASP.NET Core MVC.</span></span>

### <a name="scenario-2-wcf-service-and-winforms-client-app-3-tier-app"></a><span data-ttu-id="1f254-138">Scénario 2 : service WCF et application cliente WinForms (application à 3 niveaux)</span><span class="sxs-lookup"><span data-stu-id="1f254-138">Scenario 2: WCF service and WinForms client app (3-Tier app)</span></span>

<span data-ttu-id="1f254-139">La figure ci-dessous illustre le scénario simple de l’application héritée à 3 couches d’origine.</span><span class="sxs-lookup"><span data-stu-id="1f254-139">The figure below shows the simple scenario of the original 3-Tier legacy application.</span></span>

![Scénario d’architecture simple de l’application à 3 niveaux héritée d’origine avec un service WCF et une application cliente WinForms](./media/image5-1.5.png)

### <a name="benefits"></a><span data-ttu-id="1f254-141">Avantages</span><span class="sxs-lookup"><span data-stu-id="1f254-141">Benefits</span></span>

<span data-ttu-id="1f254-142">Les avantages de cette procédure pas à pas sont simples : Familiarisez-vous avec le code et les applications initiales.</span><span class="sxs-lookup"><span data-stu-id="1f254-142">The benefits of this walkthrough are simple: Just get familiar with the code and initial apps.</span></span>

### <a name="next-steps"></a><span data-ttu-id="1f254-143">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="1f254-143">Next steps</span></span>

<span data-ttu-id="1f254-144">Explorez ce contenu plus en détail sur le wiki GitHub :</span><span class="sxs-lookup"><span data-stu-id="1f254-144">Explore this content more in-depth on the GitHub wiki:</span></span>

- [<span data-ttu-id="1f254-145">Présentation de la base de référence ASP.NET MVC et Web Forms les applications « héritées »</span><span class="sxs-lookup"><span data-stu-id="1f254-145">Tour on the baseline ASP.NET MVC and Web Forms "legacy" apps</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/01.-Tour-on-the-ASP.NET-MVC-and-WebForms-apps-implementation-code)
- [<span data-ttu-id="1f254-146">Visite guidée du service WCF de base et de l’application WinForms (3 niveaux) « hérité »</span><span class="sxs-lookup"><span data-stu-id="1f254-146">Tour on the baseline WCF service and WinForms (3-Tier) "legacy" app</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/21.-Tour-on-the-WCF-service-and-WinForms-apps)

## <a name="walkthrough-2-containerize-your-existing-net-applications-with-windows-containers"></a><span data-ttu-id="1f254-147">Procédure pas à pas 2 : mise en conteneur de vos applications .NET existantes avec des conteneurs Windows</span><span class="sxs-lookup"><span data-stu-id="1f254-147">Walkthrough 2: Containerize your existing .NET applications with Windows Containers</span></span>

### <a name="overview"></a><span data-ttu-id="1f254-148">Vue d’ensemble</span><span class="sxs-lookup"><span data-stu-id="1f254-148">Overview</span></span>

<span data-ttu-id="1f254-149">Utilisez des conteneurs Windows pour améliorer le déploiement d’applications .NET existantes, comme celles basées sur MVC, Web Forms ou WCF, dans des environnements de production, de développement et de test.</span><span class="sxs-lookup"><span data-stu-id="1f254-149">Use Windows Containers to improve deployment of existing .NET applications, like those based on MVC, Web Forms, or WCF, to production, development, and test environments.</span></span>

### <a name="goals"></a><span data-ttu-id="1f254-150">Objectifs</span><span class="sxs-lookup"><span data-stu-id="1f254-150">Goals</span></span>

<span data-ttu-id="1f254-151">L’objectif de cette procédure pas à pas est de vous montrer plusieurs options pour la mise en conteneur d’une application .NET Framework existante.</span><span class="sxs-lookup"><span data-stu-id="1f254-151">The goal of this walkthrough is to show you several options for containerizing an existing .NET Framework application.</span></span> <span data-ttu-id="1f254-152">Vous pouvez :</span><span class="sxs-lookup"><span data-stu-id="1f254-152">You can:</span></span>

- <span data-ttu-id="1f254-153">Conversez votre application à l’aide des [outils Visual studio 2017 pour l’ancrage](/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker) (visual studio 2017 ou versions ultérieures).</span><span class="sxs-lookup"><span data-stu-id="1f254-153">Containerize your application by using [Visual Studio 2017 Tools for Docker](/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker) (Visual Studio 2017 or later versions).</span></span>

- <span data-ttu-id="1f254-154">Conversez votre application en ajoutant manuellement un [fichier dockerfile](https://docs.docker.com/engine/reference/builder/), puis en utilisant l' [interface de commande](https://docs.docker.com/engine/reference/commandline/cli/)de l’ancrage.</span><span class="sxs-lookup"><span data-stu-id="1f254-154">Containerize your application by manually adding a [Dockerfile](https://docs.docker.com/engine/reference/builder/), and then using the [Docker CLI](https://docs.docker.com/engine/reference/commandline/cli/).</span></span>

- <span data-ttu-id="1f254-155">Conversez votre application à l’aide de l’outil [Img2Docker](https://github.com/docker/communitytools-image2docker-win) (outil open source de l’ancrage).</span><span class="sxs-lookup"><span data-stu-id="1f254-155">Containerize your application by using the [Img2Docker](https://github.com/docker/communitytools-image2docker-win) tool (an open-source tool from Docker).</span></span>

<span data-ttu-id="1f254-156">Cette procédure pas à pas se concentre sur l’approche outils Visual Studio 2017 pour l’ancrage, mais les deux autres approches sont assez similaires en ce qui concerne l’utilisation de fichiers dockerfile.</span><span class="sxs-lookup"><span data-stu-id="1f254-156">This walkthrough focuses on the Visual Studio 2017 Tools for Docker approach, but the other two approaches are fairly similar in regard to using Dockerfiles.</span></span>

### <a name="scenario-1-containerized-aspnet-web-apps"></a><span data-ttu-id="1f254-157">Scénario 1 : applications Web ASP.NET en conteneur</span><span class="sxs-lookup"><span data-stu-id="1f254-157">Scenario 1: Containerized ASP.NET web apps</span></span>

<span data-ttu-id="1f254-158">La figure ci-dessous illustre le scénario pour les applications Web Apps héritées eShop en conteneur.</span><span class="sxs-lookup"><span data-stu-id="1f254-158">Figure below shows the scenario for containerized eShop legacy web apps applications.</span></span>

![Diagramme d’architecture simplifié des applications ASP.NET en conteneur dans un environnement de développement](./media/image5-3.png)

### <a name="scenario-2-containerized-wcf-service"></a><span data-ttu-id="1f254-160">Scénario 2 : service WCF en conteneur</span><span class="sxs-lookup"><span data-stu-id="1f254-160">Scenario 2: Containerized WCF service</span></span>

<span data-ttu-id="1f254-161">La figure ci-dessous illustre le scénario d’une application à 3 niveaux avec un service WCF en conteneur.</span><span class="sxs-lookup"><span data-stu-id="1f254-161">Figure below shows the scenario for a 3-Tier app with a containerized WCF service.</span></span>

![Diagramme d’architecture simplifié du service WCF en conteneur dans un environnement de développement](./media/image5-3.5.png)

### <a name="benefits"></a><span data-ttu-id="1f254-163">Avantages</span><span class="sxs-lookup"><span data-stu-id="1f254-163">Benefits</span></span>

<span data-ttu-id="1f254-164">L’exécution de votre application monolithique dans un conteneur présente des avantages.</span><span class="sxs-lookup"><span data-stu-id="1f254-164">There are advantages to running your monolithic application in a container.</span></span> <span data-ttu-id="1f254-165">Tout d’abord, vous créez une image pour l’application.</span><span class="sxs-lookup"><span data-stu-id="1f254-165">First, you create an image for the application.</span></span> <span data-ttu-id="1f254-166">À partir de là, chaque déploiement s’exécute dans le même environnement.</span><span class="sxs-lookup"><span data-stu-id="1f254-166">From that point on, every deployment runs in the same environment.</span></span> <span data-ttu-id="1f254-167">Chaque conteneur utilise la même version du système d’exploitation, a la même version des dépendances installée, utilise la même version du .NET Framework et est généré à l’aide du même processus.</span><span class="sxs-lookup"><span data-stu-id="1f254-167">Every container uses the same OS version, has the same version of dependencies installed, uses the same .NET framework version, and is built by using the same process.</span></span> <span data-ttu-id="1f254-168">Fondamentalement, vous contrôlez les dépendances de votre application à l’aide d’une image d’ancrage.</span><span class="sxs-lookup"><span data-stu-id="1f254-168">Basically, you control the dependencies of your application by using a Docker image.</span></span> <span data-ttu-id="1f254-169">Les dépendances se déplacent avec l’application lorsque vous déployez les conteneurs.</span><span class="sxs-lookup"><span data-stu-id="1f254-169">The dependencies travel with the application when you deploy the containers.</span></span>

<span data-ttu-id="1f254-170">Un autre avantage est que les développeurs peuvent exécuter l’application dans l’environnement cohérent fourni par les conteneurs Windows.</span><span class="sxs-lookup"><span data-stu-id="1f254-170">An additional benefit is that developers can run the application in the consistent environment that's provided by Windows Containers.</span></span> <span data-ttu-id="1f254-171">Les problèmes qui apparaissent uniquement avec certaines versions peuvent être détectés immédiatement, au lieu de s’afficher dans un environnement intermédiaire ou de production.</span><span class="sxs-lookup"><span data-stu-id="1f254-171">Issues that appear only with certain versions can be spotted immediately, instead of surfacing in a staging or production environment.</span></span> <span data-ttu-id="1f254-172">Les différences dans les environnements de développement utilisés par les membres de l’équipe de développement sont moins importantes quand les applications s’exécutent dans des conteneurs.</span><span class="sxs-lookup"><span data-stu-id="1f254-172">Differences in development environments used by members of the development team matter less when applications run in containers.</span></span>

<span data-ttu-id="1f254-173">Les applications en conteneur ont également une courbe de montée en puissance parallèle.</span><span class="sxs-lookup"><span data-stu-id="1f254-173">Containerized applications also have a flatter scale-out curve.</span></span> <span data-ttu-id="1f254-174">Les applications en conteneur vous permettent d’avoir plus d’instances d’application et de service (basées sur des conteneurs) sur une machine virtuelle ou un ordinateur physique par rapport aux déploiements d’applications standard par ordinateur.</span><span class="sxs-lookup"><span data-stu-id="1f254-174">Containerized apps enable you to have more application and service instances (based on containers) in a VM or physical machine compared to regular application deployments per machine.</span></span> <span data-ttu-id="1f254-175">Cela se traduit par une densité plus élevée et moins de ressources requises, en particulier quand vous utilisez des orchestrateurs comme Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="1f254-175">This translates to higher density and fewer required resources, especially when you use orchestrators like Kubernetes.</span></span>

<span data-ttu-id="1f254-176">Dans les situations idéales, le conteneur ne nécessite pas d’apporter des modifications au code de l’application (C \# ).</span><span class="sxs-lookup"><span data-stu-id="1f254-176">Containerization, in ideal situations, does not require making any changes to the application code (C\#).</span></span> <span data-ttu-id="1f254-177">Dans la plupart des scénarios, vous avez simplement besoin des fichiers de métadonnées de déploiement de l’arrimeur (fichiers dockerfile et Docker Compose).</span><span class="sxs-lookup"><span data-stu-id="1f254-177">In most scenarios, you just need the Docker deployment metadata files (Dockerfiles and Docker Compose files).</span></span>

### <a name="next-steps"></a><span data-ttu-id="1f254-178">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="1f254-178">Next steps</span></span>

<span data-ttu-id="1f254-179">Explorez ce contenu plus en détail sur le wiki GitHub :</span><span class="sxs-lookup"><span data-stu-id="1f254-179">Explore this content more in-depth on the GitHub wiki:</span></span>

- [<span data-ttu-id="1f254-180">Comment converser le .NET Framework des applications Web avec des conteneurs et un dockers Windows</span><span class="sxs-lookup"><span data-stu-id="1f254-180">How to containerize the .NET Framework web apps with Windows Containers and Docker</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/02.-How-to-containerize-the-.NET-Framework-web-apps-with-Windows-Containers-and-Docker)
- [<span data-ttu-id="1f254-181">Ajout de la prise en charge de l’ancrage à un service WCF</span><span class="sxs-lookup"><span data-stu-id="1f254-181">Adding Docker Support to a WCF service</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/22.-Adding-Docker-Support)

## <a name="walkthrough-3-deploy-your-windows-containers-based-app-to-azure-vms"></a><span data-ttu-id="1f254-182">Procédure pas à pas 3 : déployer votre application basée sur des conteneurs Windows sur des machines virtuelles Azure</span><span class="sxs-lookup"><span data-stu-id="1f254-182">Walkthrough 3: Deploy your Windows Containers-based app to Azure VMs</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="1f254-183">Disponibilité des procédures techniques</span><span class="sxs-lookup"><span data-stu-id="1f254-183">Technical walkthrough availability</span></span>

<span data-ttu-id="1f254-184">La procédure pas à pas complète technique est disponible dans le wiki eShopModernizing GitHub référentiel : <https://github.com/dotnet-architecture/eShopModernizing/wiki/06.-Deploying-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)></span><span class="sxs-lookup"><span data-stu-id="1f254-184">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki: <https://github.com/dotnet-architecture/eShopModernizing/wiki/06.-Deploying-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)></span></span>

### <a name="overview"></a><span data-ttu-id="1f254-185">Vue d’ensemble</span><span class="sxs-lookup"><span data-stu-id="1f254-185">Overview</span></span>

<span data-ttu-id="1f254-186">Le déploiement sur un ordinateur hôte de station d’accueil sur une machine virtuelle Windows Server 2016 dans Azure vous permet de configurer rapidement des environnements de développement, de test et de mise en lots.</span><span class="sxs-lookup"><span data-stu-id="1f254-186">Deploying to a Docker host on a Windows Server 2016 Virtual Machine (VM) in Azure lets you quickly set up development/test/staging environments.</span></span> <span data-ttu-id="1f254-187">Il permet également aux testeurs ou aux utilisateurs professionnels de valider l’application.</span><span class="sxs-lookup"><span data-stu-id="1f254-187">It also gives you a common place for testers or business users to validate the app.</span></span> <span data-ttu-id="1f254-188">Les machines virtuelles peuvent également être des environnements de production IaaS (infrastructure as a service) valides.</span><span class="sxs-lookup"><span data-stu-id="1f254-188">VMs also can be valid Infrastructure as a Service (IaaS) production environments.</span></span>

### <a name="goals"></a><span data-ttu-id="1f254-189">Objectifs</span><span class="sxs-lookup"><span data-stu-id="1f254-189">Goals</span></span>

<span data-ttu-id="1f254-190">L’objectif de cette procédure pas à pas est de vous montrer les différentes possibilités dont vous disposez lorsque vous déployez des conteneurs Windows sur des machines virtuelles Azure basées sur Windows Server 2016 ou versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="1f254-190">The goal of this walkthrough is to show you the multiple alternatives you have when you deploy Windows Containers to Azure VMs that are based on Windows Server 2016 or later versions.</span></span>

### <a name="scenarios"></a><span data-ttu-id="1f254-191">Scénarios</span><span class="sxs-lookup"><span data-stu-id="1f254-191">Scenarios</span></span>

<span data-ttu-id="1f254-192">Plusieurs scénarios sont traités dans cette procédure pas à pas.</span><span class="sxs-lookup"><span data-stu-id="1f254-192">Several scenarios are covered in this walkthrough.</span></span>

#### <a name="scenario-a-deploy-to-an-azure-vm-from-a-dev-pc-through-docker-engine-connection"></a><span data-ttu-id="1f254-193">Scénario A : déployer sur une machine virtuelle Azure à partir d’un PC de développement via une connexion du moteur de l’ancrage</span><span class="sxs-lookup"><span data-stu-id="1f254-193">Scenario A: Deploy to an Azure VM from a dev PC through Docker Engine connection</span></span>

![Déployer sur une machine virtuelle Azure à partir d’un PC de développement via une connexion du moteur de l’ancrage](./media/image5-4.png)

<span data-ttu-id="1f254-195">**Figure 5-4.**</span><span class="sxs-lookup"><span data-stu-id="1f254-195">**Figure 5-4.**</span></span> <span data-ttu-id="1f254-196">Déployer sur une machine virtuelle Azure à partir d’un PC de développement via une connexion du moteur de l’ancrage</span><span class="sxs-lookup"><span data-stu-id="1f254-196">Deploy to an Azure VM from a dev PC through a Docker Engine connection</span></span>

#### <a name="scenario-b-deploy-to-an-azure-vm-through-a-docker-registry"></a><span data-ttu-id="1f254-197">Scénario B : déployer sur une machine virtuelle Azure par le biais d’un registre Dockr</span><span class="sxs-lookup"><span data-stu-id="1f254-197">Scenario B: Deploy to an Azure VM through a Docker Registry</span></span>

![Déployer sur une machine virtuelle Azure par le biais d’un registre Dockr](./media/image5-5.png)

<span data-ttu-id="1f254-199">**Figure 5-5.**</span><span class="sxs-lookup"><span data-stu-id="1f254-199">**Figure 5-5.**</span></span> <span data-ttu-id="1f254-200">Déployer sur une machine virtuelle Azure par le biais d’un registre Dockr</span><span class="sxs-lookup"><span data-stu-id="1f254-200">Deploy to an Azure VM through a Docker Registry</span></span>

#### <a name="scenario-c-deploy-to-an-azure-vm-from-cicd-pipelines-in-azure-devops-services"></a><span data-ttu-id="1f254-201">Scénario C : déployer sur une machine virtuelle Azure à partir de pipelines CI/CD dans Azure DevOps Services</span><span class="sxs-lookup"><span data-stu-id="1f254-201">Scenario C: Deploy to an Azure VM from CI/CD pipelines in Azure DevOps Services</span></span>

![Déployer sur une machine virtuelle Azure à partir de pipelines CI/CD dans Azure DevOps Services](./media/image5-6.png)

<span data-ttu-id="1f254-203">**Figure 5-6.**</span><span class="sxs-lookup"><span data-stu-id="1f254-203">**Figure 5-6.**</span></span> <span data-ttu-id="1f254-204">Déployer sur une machine virtuelle Azure à partir de pipelines CI/CD dans Azure DevOps Services</span><span class="sxs-lookup"><span data-stu-id="1f254-204">Deploy to an Azure VM from CI/CD pipelines in Azure DevOps Services</span></span>

### <a name="azure-vms-for-windows-containers"></a><span data-ttu-id="1f254-205">Machines virtuelles Azure pour les conteneurs Windows</span><span class="sxs-lookup"><span data-stu-id="1f254-205">Azure VMs for Windows Containers</span></span>

<span data-ttu-id="1f254-206">Les machines virtuelles Azure pour les conteneurs Windows sont des machines virtuelles basées sur Windows Server 2016, Windows 10 ou versions ultérieures, avec le moteur d’ancrage configuré.</span><span class="sxs-lookup"><span data-stu-id="1f254-206">Azure VMs for Windows Containers are VMs based on Windows Server 2016, Windows 10, or later versions, both with Docker Engine set up.</span></span> <span data-ttu-id="1f254-207">Dans la plupart des cas, Windows Server 2016 est utilisé dans les machines virtuelles Azure.</span><span class="sxs-lookup"><span data-stu-id="1f254-207">In most cases, Windows Server 2016 is used in the Azure VMs.</span></span>

<span data-ttu-id="1f254-208">Azure fournit actuellement une machine virtuelle nommée **Windows Server 2016 avec des conteneurs**.</span><span class="sxs-lookup"><span data-stu-id="1f254-208">Azure currently provides a VM named **Windows Server 2016 with Containers**.</span></span> <span data-ttu-id="1f254-209">Vous pouvez utiliser cette machine virtuelle pour essayer la nouvelle fonctionnalité de conteneur Windows Server, avec Windows Server Core ou Windows nano Server.</span><span class="sxs-lookup"><span data-stu-id="1f254-209">You can use this VM to try the new Windows Server Container feature, with either Windows Server Core or Windows Nano Server.</span></span> <span data-ttu-id="1f254-210">Les images du système d’exploitation du conteneur sont installées, puis la machine virtuelle est prête à être utilisée avec l’ancrage.</span><span class="sxs-lookup"><span data-stu-id="1f254-210">Container OS images are installed, and then the VM is ready to use with Docker.</span></span>

### <a name="benefits"></a><span data-ttu-id="1f254-211">Avantages</span><span class="sxs-lookup"><span data-stu-id="1f254-211">Benefits</span></span>

<span data-ttu-id="1f254-212">Bien que les conteneurs Windows puissent être déployés sur des machines virtuelles Windows Server 2016 locales, lorsque vous déployez sur Azure, vous disposez d’un moyen plus simple de commencer, avec des machines virtuelles de conteneur Windows Server prêtes à l’emploi.</span><span class="sxs-lookup"><span data-stu-id="1f254-212">Although Windows Containers can be deployed to on-premises Windows Server 2016 VMs, when you deploy to Azure, you get an easier way to get started, with ready-to-use Windows Server Container VMs.</span></span> <span data-ttu-id="1f254-213">Vous disposez également d’un emplacement en ligne commun qui est accessible aux testeurs et de l’extensibilité automatique par le biais de groupes de machines virtuelles identiques Azure.</span><span class="sxs-lookup"><span data-stu-id="1f254-213">You also get a common online location that's accessible to testers, and automatic scalability through Azure virtual machine scale sets.</span></span>

### <a name="next-steps"></a><span data-ttu-id="1f254-214">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="1f254-214">Next steps</span></span>

<span data-ttu-id="1f254-215">Explorez ce contenu plus en détail sur le wiki GitHub :</span><span class="sxs-lookup"><span data-stu-id="1f254-215">Explore this content more in-depth on the GitHub wiki:</span></span>

<https://github.com/dotnet-architecture/eShopModernizing/wiki/06.-Deploying-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)>

## <a name="walkthrough-4-deploy-your-windows-containers-based-apps-to-azure-container-instances-aci"></a><span data-ttu-id="1f254-216">Procédure pas à pas 4 : déployer vos applications basées sur des conteneurs Windows sur Azure Container Instances (ACI)</span><span class="sxs-lookup"><span data-stu-id="1f254-216">Walkthrough 4: Deploy your Windows Containers-based apps to Azure Container Instances (ACI)</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="1f254-217">Disponibilité des procédures techniques</span><span class="sxs-lookup"><span data-stu-id="1f254-217">Technical walkthrough availability</span></span>

<span data-ttu-id="1f254-218">La procédure pas à pas complète technique est disponible dans le wiki eShopModernizing GitHub référentiel :</span><span class="sxs-lookup"><span data-stu-id="1f254-218">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

<span data-ttu-id="1f254-219">[Déploiement des applications sur ACI (Azure Container Instances)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances))</span><span class="sxs-lookup"><span data-stu-id="1f254-219">[Deploying the Apps to ACI (Azure Container Instances)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances))</span></span>

### <a name="overview"></a><span data-ttu-id="1f254-220">Vue d’ensemble</span><span class="sxs-lookup"><span data-stu-id="1f254-220">Overview</span></span>

<span data-ttu-id="1f254-221">[Azure Container instances (ACI)](/azure/container-instances/) est le moyen le plus rapide de disposer d’un environnement de développement/test/intermédiaire de conteneurs dans lequel vous pouvez déployer des instances uniques de conteneurs.</span><span class="sxs-lookup"><span data-stu-id="1f254-221">[Azure Container Instances (ACI)](/azure/container-instances/) is the quickest way to have a Containers dev/test/staging environment where you can deploy single instances of containers.</span></span>

### <a name="goals"></a><span data-ttu-id="1f254-222">Objectifs</span><span class="sxs-lookup"><span data-stu-id="1f254-222">Goals</span></span>

<span data-ttu-id="1f254-223">Cette procédure pas à pas vous montre les principaux scénarios de déploiement de conteneurs Windows vers Azure Container Instances (ACI) et la façon dont vous pouvez déployer des applications eShopModernizing dans ACI.</span><span class="sxs-lookup"><span data-stu-id="1f254-223">This walkthrough shows you the main scenarios when deploying Windows Containers to Azure Container Instances (ACI) and how you can deploy eShopModernizing Apps into ACI.</span></span>

### <a name="scenarios"></a><span data-ttu-id="1f254-224">Scénarios</span><span class="sxs-lookup"><span data-stu-id="1f254-224">Scenarios</span></span>

<span data-ttu-id="1f254-225">Il peut y avoir des variantes relatives au déploiement des applications eShopModernizing dans ACI, telles que le déploiement d’une seule ou de toutes les applications (application MVC, application WebForms ou service WCF).</span><span class="sxs-lookup"><span data-stu-id="1f254-225">There can be variations about deploying the eShopModernizing apps into ACI such as deploying just one or all of the apps (MVC app, WebForms app or WCF service).</span></span> <span data-ttu-id="1f254-226">Dans le scénario suivant illustré ci-dessous, vous pouvez voir l’application MVC ASP.NET plus le conteneur SQL Server les deux étant déployés en tant que conteneurs dans ACI (Azure Container Instances).</span><span class="sxs-lookup"><span data-stu-id="1f254-226">In the following scenario shown below you can see the ASP.NET MVC app plus the SQL Server container both of them deployed as containers into ACI (Azure Container Instances).</span></span>

![Déployer dans ACI à partir d’un environnement de développement](./media/image5-3.5.6.png)

### <a name="benefits"></a><span data-ttu-id="1f254-228">Avantages</span><span class="sxs-lookup"><span data-stu-id="1f254-228">Benefits</span></span>

<span data-ttu-id="1f254-229">Azure Container Instances facilite la création et la gestion de conteneurs Docker dans Azure, sans avoir à approvisionner les machines virtuelles ou à adopter un service de niveau supérieur.</span><span class="sxs-lookup"><span data-stu-id="1f254-229">Azure Container Instances makes it easy to create and manage Docker containers in Azure, without having to provision virtual machines or adopt a higher-level service.</span></span> <span data-ttu-id="1f254-230">Avec ACI, vous pouvez déployer directement un conteneur Windows dans Azure et l’exposer à Internet avec un nom de domaine complet (FQDN) en quelques secondes (à condition que l’image de conteneur Windows soit prête dans un registre de station d’accueil, tel que Dockr Hub ou Azure Container Registry).</span><span class="sxs-lookup"><span data-stu-id="1f254-230">With ACI, you can directly deploy a Windows container in Azure and expose it to the internet with a fully qualified domain name (FQDN) in a matter of seconds (Provided that you have the Windows Container image ready in a Docker registry like Docker Hub or Azure Container Registry).</span></span>

### <a name="considerations"></a><span data-ttu-id="1f254-231">Considérations</span><span class="sxs-lookup"><span data-stu-id="1f254-231">Considerations</span></span>

<span data-ttu-id="1f254-232">Le déploiement de conteneurs Windows avec l’ensemble des .NET Framework/ASP.NET ou des SQL Server dans Azure Container Instances (ACI) n’est pas aussi rapide que le déploiement sur un hôte de l’arrimeur standard (comme un ordinateur Windows Server 2016 avec des conteneurs Windows), car l’image de l’arrimeur doit être téléchargée (extraite du registre de l’arrimeur) à chaque fois et la taille de la l’image de conteneur SQL (15,1 Go) et l’image de conteneur ASP.NET (13,9 Go) sont considérablement volumineuses, mais elles sont beaucoup moins chères que la maintenance de votre propre hôte de station d’accueil (Windows Server 2016 en ligne de façon permanente avec les conteneurs Windows dans Azure), ce qui signifie que en revanche, un bon choix pour les déploiements de production.</span><span class="sxs-lookup"><span data-stu-id="1f254-232">Deploying Windows Containers with either full .NET Framework / ASP.NET or SQL Server into Azure Container Instances (ACI) is not quite as fast as deploying to a regular Docker Host (like a Windows Server 2016 with Windows Containers) because the Docker image has to be downloaded (pulled from the Docker registry) every time and the sizes of the SQL container image (15.1 GB) and the ASP.NET container image (13.9 GB) are significantly large, however it is much cheaper than maintaining your own docker host (permanently on-line Windows Server 2016 with Windows Containers VM in Azure) not to mention a whole orchestrator like Kubernetes in Azure (AKS) which is, on the other hand, a great choice for production deployments.</span></span>

<span data-ttu-id="1f254-233">En guise de conclusion principale, l’utilisation de Azure Container Instances est une option très intéressante pour les scénarios de développement/test et pour les pipelines CI/CD.</span><span class="sxs-lookup"><span data-stu-id="1f254-233">As main conclusion, using Azure Container Instances is a very compelling option for Dev/Test scenarios and for CI/CD pipelines.</span></span>

### <a name="next-steps"></a><span data-ttu-id="1f254-234">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="1f254-234">Next steps</span></span>

<span data-ttu-id="1f254-235">Explorez ce contenu plus en détail sur le wiki GitHub :</span><span class="sxs-lookup"><span data-stu-id="1f254-235">Explore this content more in-depth on the GitHub wiki:</span></span>

[https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances))

## <a name="walkthrough-5-deploy-your-windows-containers-based-apps-to-kubernetes-in-azure-container-service"></a><span data-ttu-id="1f254-236">Procédure pas à pas 5 : déployer vos applications basées sur des conteneurs Windows sur Kubernetes dans Azure Container Service</span><span class="sxs-lookup"><span data-stu-id="1f254-236">Walkthrough 5: Deploy your Windows Containers-based apps to Kubernetes in Azure Container Service</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="1f254-237">Disponibilité des procédures techniques</span><span class="sxs-lookup"><span data-stu-id="1f254-237">Technical walkthrough availability</span></span>

<span data-ttu-id="1f254-238">La procédure pas à pas complète technique est disponible dans le wiki eShopModernizing GitHub référentiel :</span><span class="sxs-lookup"><span data-stu-id="1f254-238">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

<https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-CI-CD)>

### <a name="overview"></a><span data-ttu-id="1f254-239">Vue d’ensemble</span><span class="sxs-lookup"><span data-stu-id="1f254-239">Overview</span></span>

<span data-ttu-id="1f254-240">Une application basée sur des conteneurs Windows devra rapidement utiliser des plateformes, en se déplaçant encore plus loin des machines virtuelles IaaS.</span><span class="sxs-lookup"><span data-stu-id="1f254-240">An application that's based on Windows Containers will quickly need to use platforms, moving even further away from IaaS VMs.</span></span> <span data-ttu-id="1f254-241">Cela est nécessaire pour obtenir facilement une évolutivité élevée et une plus grande évolutivité automatisée, et pour une amélioration significative des déploiements et du contrôle de version automatisés.</span><span class="sxs-lookup"><span data-stu-id="1f254-241">This is needed to easily achieve high scalability and better automated scalability, and for a significant improvement in automated deployments and versioning.</span></span> <span data-ttu-id="1f254-242">Vous pouvez atteindre ces objectifs à l’aide d’Orchestrator [Kubernetes](https://kubernetes.io/), disponible dans [Azure Container Services](https://azure.microsoft.com/services/container-service/).</span><span class="sxs-lookup"><span data-stu-id="1f254-242">You can achieve these goals by using the orchestrator [Kubernetes](https://kubernetes.io/), available in [Azure Container Services](https://azure.microsoft.com/services/container-service/).</span></span>

### <a name="goals"></a><span data-ttu-id="1f254-243">Objectifs</span><span class="sxs-lookup"><span data-stu-id="1f254-243">Goals</span></span>

<span data-ttu-id="1f254-244">L’objectif de cette procédure pas à pas est d’apprendre à déployer une application basée sur un conteneur Windows dans Kubernetes (également appelé *K8s*) dans Azure Container service.</span><span class="sxs-lookup"><span data-stu-id="1f254-244">The goal of this walkthrough is to learn how to deploy a Windows Container–based application to Kubernetes (also called *K8s*) in Azure Container Service.</span></span> <span data-ttu-id="1f254-245">Le déploiement de Kubernetes à partir de zéro est un processus en deux étapes :</span><span class="sxs-lookup"><span data-stu-id="1f254-245">Deploying to Kubernetes from scratch is a two-step process:</span></span>

1. <span data-ttu-id="1f254-246">Déployez un cluster Kubernetes sur Azure Container Service.</span><span class="sxs-lookup"><span data-stu-id="1f254-246">Deploy a Kubernetes cluster to Azure Container Service.</span></span>

2. <span data-ttu-id="1f254-247">Déployez l’application et les ressources associées sur le cluster Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="1f254-247">Deploy the application and related resources to the Kubernetes cluster.</span></span>

### <a name="scenarios"></a><span data-ttu-id="1f254-248">Scénarios</span><span class="sxs-lookup"><span data-stu-id="1f254-248">Scenarios</span></span>

#### <a name="scenario-a-deploy-directly-to-a-kubernetes-cluster-from-a-dev-environment"></a><span data-ttu-id="1f254-249">Scénario A : déployer directement sur un cluster Kubernetes à partir d’un environnement de développement</span><span class="sxs-lookup"><span data-stu-id="1f254-249">Scenario A: Deploy directly to a Kubernetes cluster from a dev environment</span></span>

![Déployer directement sur un cluster Kubernetes à partir d’un environnement de développement](./media/image5-7.png)

<span data-ttu-id="1f254-251">**Figure 5-7.**</span><span class="sxs-lookup"><span data-stu-id="1f254-251">**Figure 5-7.**</span></span> <span data-ttu-id="1f254-252">Déployer directement sur un cluster Kubernetes à partir d’un environnement de développement</span><span class="sxs-lookup"><span data-stu-id="1f254-252">Deploy directly to a Kubernetes cluster from a development environment</span></span>

#### <a name="scenario-b-deploy-to-a-kubernetes-cluster-from-cicd-pipelines-in-azure-devops-services"></a><span data-ttu-id="1f254-253">Scénario B : déployer sur un cluster Kubernetes à partir de pipelines CI/CD dans Azure DevOps Services</span><span class="sxs-lookup"><span data-stu-id="1f254-253">Scenario B: Deploy to a Kubernetes cluster from CI/CD pipelines in Azure DevOps Services</span></span>

![Déployer sur un cluster Kubernetes à partir de pipelines CI/CD dans Azure DevOps Services](./media/image5-8.png)

<span data-ttu-id="1f254-255">**Figure 5-8.**</span><span class="sxs-lookup"><span data-stu-id="1f254-255">**Figure 5-8.**</span></span> <span data-ttu-id="1f254-256">Déployer sur un cluster Kubernetes à partir de pipelines CI/CD dans Azure DevOps Services</span><span class="sxs-lookup"><span data-stu-id="1f254-256">Deploy to a Kubernetes cluster from CI/CD pipelines in Azure DevOps Services</span></span>

### <a name="benefits"></a><span data-ttu-id="1f254-257">Avantages</span><span class="sxs-lookup"><span data-stu-id="1f254-257">Benefits</span></span>

<span data-ttu-id="1f254-258">Le déploiement sur un cluster dans Kubernetes présente de nombreux avantages.</span><span class="sxs-lookup"><span data-stu-id="1f254-258">There are many benefits to deploying to a cluster in Kubernetes.</span></span> <span data-ttu-id="1f254-259">L’avantage le plus important est que vous disposez d’un environnement prêt pour la production dans lequel vous pouvez monter en charge l’application en fonction du nombre d’instances de conteneur que vous souhaitez utiliser (extensibilité interne dans les nœuds existants) et en fonction du nombre de nœuds ou de machines virtuelles du cluster (extensibilité globale du cluster).</span><span class="sxs-lookup"><span data-stu-id="1f254-259">The biggest benefit is that you get a production-ready environment in which you can scale out the application based on the number of container instances you want to use (inner-scalability in the existing nodes), and based on the number of nodes or VMs in the cluster (global scalability of the cluster).</span></span>

<span data-ttu-id="1f254-260">Azure Container Service optimise les outils et technologies Open source populaires spécifiquement pour Azure.</span><span class="sxs-lookup"><span data-stu-id="1f254-260">Azure Container Service optimizes popular open-source tools and technologies specifically for Azure.</span></span> <span data-ttu-id="1f254-261">Vous bénéficiez d’une solution ouverte qui offre la portabilité, à la fois pour vos conteneurs et pour la configuration de votre application.</span><span class="sxs-lookup"><span data-stu-id="1f254-261">You get an open solution that offers portability, both for your containers and for your application configuration.</span></span> <span data-ttu-id="1f254-262">Vous sélectionnez la taille, le nombre d’hôtes et Orchestrator Tools-Container service gère tout le reste.</span><span class="sxs-lookup"><span data-stu-id="1f254-262">You select the size, the number of hosts, and the orchestrator tools-Container Service handles everything else.</span></span>

<span data-ttu-id="1f254-263">Avec Kubernetes, les développeurs peuvent progresser de la réflexion sur les machines physiques et virtuelles, à la planification d’une infrastructure centrée sur les conteneurs qui facilite les fonctionnalités suivantes, entre autres :</span><span class="sxs-lookup"><span data-stu-id="1f254-263">With Kubernetes, developers can progress from thinking about physical and virtual machines, to planning a container-centric infrastructure that facilitates the following capabilities, among others:</span></span>

- <span data-ttu-id="1f254-264">Applications basées sur plusieurs conteneurs</span><span class="sxs-lookup"><span data-stu-id="1f254-264">Applications based on multiple containers</span></span>

- <span data-ttu-id="1f254-265">Réplication des instances de conteneur et de la mise à l’échelle automatique horizontale</span><span class="sxs-lookup"><span data-stu-id="1f254-265">Replicating container instances and horizontal autoscaling</span></span>

- <span data-ttu-id="1f254-266">Attribution de noms et détection (par exemple, DNS interne)</span><span class="sxs-lookup"><span data-stu-id="1f254-266">Naming and discovering (for example, internal DNS)</span></span>

- <span data-ttu-id="1f254-267">Équilibrage des charges</span><span class="sxs-lookup"><span data-stu-id="1f254-267">Balancing loads</span></span>

- <span data-ttu-id="1f254-268">Mises à jour propagées</span><span class="sxs-lookup"><span data-stu-id="1f254-268">Rolling updates</span></span>

- <span data-ttu-id="1f254-269">Distribution de secrets</span><span class="sxs-lookup"><span data-stu-id="1f254-269">Distributing secrets</span></span>

- <span data-ttu-id="1f254-270">Vérifications de l’intégrité des applications</span><span class="sxs-lookup"><span data-stu-id="1f254-270">Application health checks</span></span>

### <a name="next-steps"></a><span data-ttu-id="1f254-271">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="1f254-271">Next steps</span></span>

<span data-ttu-id="1f254-272">Explorez ce contenu plus en détail sur le wiki GitHub : <https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-CI-CD)></span><span class="sxs-lookup"><span data-stu-id="1f254-272">Explore this content more in-depth on the GitHub wiki: <https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-CI-CD)></span></span>

## <a name="walkthrough-6-deploy-your-windows-containers-based-apps-to-azure-app-service-for-containers"></a><span data-ttu-id="1f254-273">Procédure pas à pas 6 : déployer vos applications basées sur des conteneurs Windows vers Azure App Service pour les conteneurs</span><span class="sxs-lookup"><span data-stu-id="1f254-273">Walkthrough 6: Deploy your Windows Containers-based apps to Azure App Service for Containers</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="1f254-274">Disponibilité des procédures techniques</span><span class="sxs-lookup"><span data-stu-id="1f254-274">Technical walkthrough availability</span></span>

<span data-ttu-id="1f254-275">La procédure pas à pas complète technique est disponible dans le wiki eShopModernizing GitHub référentiel :</span><span class="sxs-lookup"><span data-stu-id="1f254-275">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

<https://github.com/dotnet-architecture/eShopModernizing/wiki/Deploy-Windows-Container-to-Azure-App-Service>

### <a name="overview"></a><span data-ttu-id="1f254-276">Vue d’ensemble</span><span class="sxs-lookup"><span data-stu-id="1f254-276">Overview</span></span>

<span data-ttu-id="1f254-277">Une application en conteneur simple utilisant des conteneurs Windows peut facilement être déployée pour Azure App Service pour les conteneurs.</span><span class="sxs-lookup"><span data-stu-id="1f254-277">A simple containerized application using Windows Containers can easily be deployed to Azure App Service for Containers.</span></span> <span data-ttu-id="1f254-278">Il s’agit de l’approche recommandée pour la plupart des applications basées sur des conteneurs Windows.</span><span class="sxs-lookup"><span data-stu-id="1f254-278">This is the recommended approach for most Windows Container-based applications.</span></span>

### <a name="goals"></a><span data-ttu-id="1f254-279">Objectifs</span><span class="sxs-lookup"><span data-stu-id="1f254-279">Goals</span></span>

<span data-ttu-id="1f254-280">L’objectif de cette procédure pas à pas est d’apprendre à déployer une application basée sur un conteneur Windows pour Azure App Service pour les conteneurs à partir d’un registre (Hub ou Azure Container Registry).</span><span class="sxs-lookup"><span data-stu-id="1f254-280">The goal of this walkthrough is to learn how to deploy a Windows Container–based application to Azure App Service for Containers from a registry (Docker Hub or Azure Container Registry).</span></span>

### <a name="scenario"></a><span data-ttu-id="1f254-281">Scénario</span><span class="sxs-lookup"><span data-stu-id="1f254-281">Scenario</span></span>

![Déployer une application basée sur un conteneur Windows pour Azure App Service pour les conteneurs](./media/image5-11.png)

### <a name="benefits"></a><span data-ttu-id="1f254-283">Avantages</span><span class="sxs-lookup"><span data-stu-id="1f254-283">Benefits</span></span>

<span data-ttu-id="1f254-284">Le déploiement sur Azure App Service pour les conteneurs offre les avantages des conteneurs associés aux avantages PaaS de Azure App Service.</span><span class="sxs-lookup"><span data-stu-id="1f254-284">Deploying to Azure App Service for Containers offers the benefits of containers paired with the PaaS benefits of Azure App Service.</span></span> <span data-ttu-id="1f254-285">App service peut facilement être mis à l’échelle verticalement et horizontalement, et peut être configuré pour être mis à l’échelle automatiquement pour répondre aux demandes fluctuantes.</span><span class="sxs-lookup"><span data-stu-id="1f254-285">The app service can easily be scaled both vertically and horizontally, and can be configured to autoscale to meet changing demands.</span></span> <span data-ttu-id="1f254-286">Les mises à jour peuvent être effectuées sans temps d’arrêt et la configuration d’un déploiement continu à partir d’un registre est facilement configurée.</span><span class="sxs-lookup"><span data-stu-id="1f254-286">Updates can be performed with zero downtime and configuration of continuous deployment from a registry is easily configured as well.</span></span>

### <a name="next-steps"></a><span data-ttu-id="1f254-287">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="1f254-287">Next steps</span></span>

<span data-ttu-id="1f254-288">Explorez ce contenu plus en détail sur le wiki GitHub : <https://github.com/dotnet-architecture/eShopModernizing/wiki/Deploy-Windows-Container-to-Azure-App-Service></span><span class="sxs-lookup"><span data-stu-id="1f254-288">Explore this content more in-depth on the GitHub wiki: <https://github.com/dotnet-architecture/eShopModernizing/wiki/Deploy-Windows-Container-to-Azure-App-Service></span></span>

> [!div class="step-by-step"]
> <span data-ttu-id="1f254-289">[Précédent](modernize-existing-apps-to-cloud-optimized/migrate-to-hybrid-cloud-scenarios.md) 
>  [Suivant](conclusions.md)</span><span class="sxs-lookup"><span data-stu-id="1f254-289">[Previous](modernize-existing-apps-to-cloud-optimized/migrate-to-hybrid-cloud-scenarios.md)
[Next](conclusions.md)</span></span> <!-- Next Chapter -->
