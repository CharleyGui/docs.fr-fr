---
title: Microservices .NET. Architecture pour les applications .NET en conteneur
description: Architecture des microservices .NET pour les applications .NET en conteneur | Les microservices sont des services modulables qui peuvent se déployer indépendamment. Les conteneurs Docker (pour Linux et Windows) simplifient le déploiement et les tests en regroupant un service et ses dépendances dans une seule unité, laquelle est ensuite exécutée dans un environnement isolé.
ms.date: 01/30/2020
ms.openlocfilehash: 9cdd5556f92e1acde540b647e7b68628a3ecf67f
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2020
ms.locfileid: "80988789"
---
# <a name="net-microservices-architecture-for-containerized-net-applications"></a><span data-ttu-id="01a9d-105">Microservices .NET : Architecture pour les applications .NET en conteneur</span><span class="sxs-lookup"><span data-stu-id="01a9d-105">.NET Microservices: Architecture for Containerized .NET Applications</span></span>

![Couverture de livre](./media/cover-small.png)

<span data-ttu-id="01a9d-107">**EDITION v3.1** - Mis à jour pour ASP.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="01a9d-107">**EDITION v3.1** - Updated to ASP.NET Core 3.1</span></span>

<span data-ttu-id="01a9d-108">Ce guide est une introduction au développement d’applications basées sur les microservices et à la gestion de celles-ci au moyen de conteneurs.</span><span class="sxs-lookup"><span data-stu-id="01a9d-108">This guide is an introduction to developing microservices-based applications and managing them using containers.</span></span> <span data-ttu-id="01a9d-109">Il traite de la conception architecturale et des approches d’implémentation utilisant .NET Core et les conteneurs Docker.</span><span class="sxs-lookup"><span data-stu-id="01a9d-109">It discusses architectural design and implementation approaches using .NET Core and Docker containers.</span></span>

<span data-ttu-id="01a9d-110">Pour faciliter la prise en main, ce guide met en lumière une application de référence en conteneur basée sur des microservices que vous pouvez explorer.</span><span class="sxs-lookup"><span data-stu-id="01a9d-110">To make it easier to get started, the guide focuses on a reference containerized and microservice-based application that you can explore.</span></span> <span data-ttu-id="01a9d-111">L’application de référence est disponible sur le dépôt GitHub [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers).</span><span class="sxs-lookup"><span data-stu-id="01a9d-111">The reference application is available at the [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) GitHub repo.</span></span>

## <a name="action-links"></a><span data-ttu-id="01a9d-112">Liens d'action</span><span class="sxs-lookup"><span data-stu-id="01a9d-112">Action links</span></span>

- <span data-ttu-id="01a9d-113">Cet e-book est également disponible en format PDF (version anglaise uniquement) [Télécharger](https://aka.ms/microservicesebook)</span><span class="sxs-lookup"><span data-stu-id="01a9d-113">This e-book is also available in a PDF format (English version only) [Download](https://aka.ms/microservicesebook)</span></span>

- <span data-ttu-id="01a9d-114">Clonez/dupliquez (fork) l’application de référence [eShopOnContainers sur GitHub](https://github.com/dotnet-architecture/eShopOnContainers)</span><span class="sxs-lookup"><span data-stu-id="01a9d-114">Clone/Fork the reference application [eShopOnContainers on GitHub](https://github.com/dotnet-architecture/eShopOnContainers)</span></span>

- <span data-ttu-id="01a9d-115">Regardez la [vidéo d’introduction sur Channel 9](https://aka.ms/microservices-video)</span><span class="sxs-lookup"><span data-stu-id="01a9d-115">Watch the [introductory video on Channel 9](https://aka.ms/microservices-video)</span></span>

- <span data-ttu-id="01a9d-116">Familiarisez-vous avec [l’architecture de microservices](https://aka.ms/MicroservicesArchitecture) immédiatement</span><span class="sxs-lookup"><span data-stu-id="01a9d-116">Get to know the [Microservices Architecture](https://aka.ms/MicroservicesArchitecture) right away</span></span>

## <a name="introduction"></a><span data-ttu-id="01a9d-117">Introduction</span><span class="sxs-lookup"><span data-stu-id="01a9d-117">Introduction</span></span>

<span data-ttu-id="01a9d-118">Les entreprises cherchent de plus en plus à réaliser des économies, à résoudre les problèmes de déploiement et à améliorer les opérations DevOps et de production en utilisant des conteneurs.</span><span class="sxs-lookup"><span data-stu-id="01a9d-118">Enterprises are increasingly realizing cost savings, solving deployment problems, and improving DevOps and production operations by using containers.</span></span> <span data-ttu-id="01a9d-119">Microsoft a fait preuve d’innovation dans le domaine des conteneurs pour Windows et Linux en créant des produits comme Azure Kubernetes Service et Azure Service Fabric et en formant des partenariats avec des acteurs phares du secteur tels que Docker, Mesosphere et Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="01a9d-119">Microsoft has been releasing container innovations for Windows and Linux by creating products like Azure Kubernetes Service and Azure Service Fabric, and by partnering with industry leaders like Docker, Mesosphere, and Kubernetes.</span></span> <span data-ttu-id="01a9d-120">Ces produits offrent aux entreprises des solutions de conteneur qui leur permettent de créer et déployer des applications à la vitesse et à l’échelle du cloud, indépendamment de la plateforme ou des outils qu’elles ont choisi d’utiliser.</span><span class="sxs-lookup"><span data-stu-id="01a9d-120">These products deliver container solutions that help companies build and deploy applications at cloud speed and scale, whatever their choice of platform or tools.</span></span>

<span data-ttu-id="01a9d-121">Docker est en passe de devenir de facto le standard dans le domaine du conteneur, recueillant l’adhésion des éditeurs les plus en vue dans les écosystèmes Windows et Linux.</span><span class="sxs-lookup"><span data-stu-id="01a9d-121">Docker is becoming the de facto standard in the container industry, supported by the most significant vendors in the Windows and Linux ecosystems.</span></span> <span data-ttu-id="01a9d-122">(Microsoft est l’un des principaux fournisseurs de cloud qui soutiennent Docker.) À l’avenir, Docker sera probablement omniprésent dans n’importe quel centre de données dans le nuage ou sur place.</span><span class="sxs-lookup"><span data-stu-id="01a9d-122">(Microsoft is one of the main cloud vendors supporting Docker.) In the future, Docker will probably be ubiquitous in any datacenter in the cloud or on-premises.</span></span>

<span data-ttu-id="01a9d-123">Par ailleurs, l’architecture de [microservices](https://martinfowler.com/articles/microservices.html) est une approche qui devient importante pour les applications stratégiques distribuées.</span><span class="sxs-lookup"><span data-stu-id="01a9d-123">In addition, the [microservices](https://martinfowler.com/articles/microservices.html) architecture is emerging as an important approach for distributed mission-critical applications.</span></span> <span data-ttu-id="01a9d-124">Dans une architecture basée sur les microservices, l’application repose sur un ensemble de services qui peuvent être développés, testés, déployés et versionnés de manière indépendante.</span><span class="sxs-lookup"><span data-stu-id="01a9d-124">In a microservice-based architecture, the application is built on a collection of services that can be developed, tested, deployed, and versioned independently.</span></span>

## <a name="about-this-guide"></a><span data-ttu-id="01a9d-125">À propos de ce guide</span><span class="sxs-lookup"><span data-stu-id="01a9d-125">About this guide</span></span>

<span data-ttu-id="01a9d-126">Ce guide est une introduction au développement d’applications basées sur les microservices et à la gestion de celles-ci au moyen de conteneurs.</span><span class="sxs-lookup"><span data-stu-id="01a9d-126">This guide is an introduction to developing microservices-based applications and managing them using containers.</span></span> <span data-ttu-id="01a9d-127">Il traite de la conception architecturale et des approches d’implémentation utilisant .NET Core et les conteneurs Docker.</span><span class="sxs-lookup"><span data-stu-id="01a9d-127">It discusses architectural design and implementation approaches using .NET Core and Docker containers.</span></span> <span data-ttu-id="01a9d-128">Pour faciliter la prise en main des conteneurs et des microservices, ce guide met en lumière une application de référence en conteneur basée sur des microservices que vous pouvez explorer.</span><span class="sxs-lookup"><span data-stu-id="01a9d-128">To make it easier to get started with containers and microservices, the guide focuses on a reference containerized and microservice-based application that you can explore.</span></span> <span data-ttu-id="01a9d-129">L’exemple d’application est disponible sur le dépôt GitHub [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers).</span><span class="sxs-lookup"><span data-stu-id="01a9d-129">The sample application is available at the [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) GitHub repo.</span></span>

<span data-ttu-id="01a9d-130">Ce guide livre des conseils de base en matière de développement et d’architecture au niveau de l’environnement de développement avec deux technologies mises en avant : Docker et .NET Core.</span><span class="sxs-lookup"><span data-stu-id="01a9d-130">This guide provides foundational development and architectural guidance primarily at a development environment level with a focus on two technologies: Docker and .NET Core.</span></span> <span data-ttu-id="01a9d-131">Notre objectif est que vous lisiez ce guide en pensant à la conception de votre application sans vous polariser sur l’infrastructure (cloud ou locale) de votre environnement de production.</span><span class="sxs-lookup"><span data-stu-id="01a9d-131">Our intention is that you read this guide when thinking about your application design without focusing on the infrastructure (cloud or on-premises) of your production environment.</span></span> <span data-ttu-id="01a9d-132">Vous prendrez vos décisions concernant l’infrastructure plus tard, au moment de créer vos applications pour la production.</span><span class="sxs-lookup"><span data-stu-id="01a9d-132">You will make decisions about your infrastructure later, when you create your production-ready applications.</span></span> <span data-ttu-id="01a9d-133">Par conséquent, ce guide se veut neutre concernant l’infrastructure et davantage centré sur l’environnement de développement.</span><span class="sxs-lookup"><span data-stu-id="01a9d-133">Therefore, this guide is intended to be infrastructure agnostic and more development-environment-centric.</span></span>

<span data-ttu-id="01a9d-134">Après avoir examiné ce guide, votre prochaine étape consistera à vous familiariser avec les microservices prêts pour la production dans Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="01a9d-134">After you have studied this guide, your next step would be to learn about production-ready microservices on Microsoft Azure.</span></span>

## <a name="version"></a><span data-ttu-id="01a9d-135">Version</span><span class="sxs-lookup"><span data-stu-id="01a9d-135">Version</span></span>

<span data-ttu-id="01a9d-136">Ce guide a été révisé pour couvrir **.NET Core 3.1** version avec de nombreuses mises à jour supplémentaires liées à la même "vague" de technologies (c’est-à-dire, Azure et d’autres technologies tierces) coïncidant à temps avec la version .NET Core 3.1.</span><span class="sxs-lookup"><span data-stu-id="01a9d-136">This guide has been revised to cover **.NET Core 3.1** version along with many additional updates related to the same “wave” of technologies (that is, Azure and additional third-party technologies) coinciding in time with the .NET Core 3.1 release.</span></span> <span data-ttu-id="01a9d-137">C’est pourquoi la version du livre a également été mise à jour à la version **3.1**.</span><span class="sxs-lookup"><span data-stu-id="01a9d-137">That’s why the book version has also been updated to version **3.1**.</span></span>

## <a name="what-this-guide-does-not-cover"></a><span data-ttu-id="01a9d-138">Sujets non abordés dans ce guide</span><span class="sxs-lookup"><span data-stu-id="01a9d-138">What this guide does not cover</span></span>

<span data-ttu-id="01a9d-139">Ce guide ne traite pas du cycle de vie des applications, de DevOps, des pipelines CI/CD, ni du travail d’équipe.</span><span class="sxs-lookup"><span data-stu-id="01a9d-139">This guide does not focus on the application lifecycle, DevOps, CI/CD pipelines, or team work.</span></span> <span data-ttu-id="01a9d-140">Le guide complémentaire intitulé [Containerized Docker Application Lifecycle with Microsoft Platform and Tools](https://aka.ms/dockerlifecycleebook) (Cycle de vie des applications Docker en conteneur avec la plateforme et les outils Microsoft) porte essentiellement sur ce sujet.</span><span class="sxs-lookup"><span data-stu-id="01a9d-140">The complementary guide [Containerized Docker Application Lifecycle with Microsoft Platform and Tools](https://aka.ms/dockerlifecycleebook) focuses on that subject.</span></span> <span data-ttu-id="01a9d-141">Le présent guide ne fournit pas non plus de détails sur l’implémentation de l’infrastructure Azure, notamment sur les orchestrateurs spécifiques.</span><span class="sxs-lookup"><span data-stu-id="01a9d-141">The current guide also does not provide implementation details on Azure infrastructure, such as information on specific orchestrators.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="01a9d-142">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="01a9d-142">Additional resources</span></span>

- <span data-ttu-id="01a9d-143">**Containerized Docker Application Lifecycle with Microsoft Platform and Tools** (livre électronique téléchargeable)</span><span class="sxs-lookup"><span data-stu-id="01a9d-143">**Containerized Docker Application Lifecycle with Microsoft Platform and Tools** (downloadable e-book)</span></span>  
    <https://aka.ms/dockerlifecycleebook>

## <a name="who-should-use-this-guide"></a><span data-ttu-id="01a9d-144">Public visé par ce guide</span><span class="sxs-lookup"><span data-stu-id="01a9d-144">Who should use this guide</span></span>

<span data-ttu-id="01a9d-145">Nous avons rédigé ce guide à l’intention des développeurs et des architectes de solutions qui n’ont pas d’expérience en matière développement d’applications Docker et d’architecture basée sur les microservices.</span><span class="sxs-lookup"><span data-stu-id="01a9d-145">We wrote this guide for developers and solution architects who are new to Docker-based application development and to microservices-based architecture.</span></span> <span data-ttu-id="01a9d-146">Ce guide s’adresse à vous si votre intention est d’apprendre à architecturer, concevoir et implémenter des applications de type preuve de concept avec les technologies de développement Microsoft (plus particulièrement .NET Core) et des conteneurs Docker.</span><span class="sxs-lookup"><span data-stu-id="01a9d-146">This guide is for you if you want to learn how to architect, design, and implement proof-of-concept applications with Microsoft development technologies (with special focus on .NET Core) and with Docker containers.</span></span>

<span data-ttu-id="01a9d-147">Ce guide saura aussi vous intéresser si vous êtes un décideur technique, tel qu’un architecte d’entreprise, désireux d’avoir une vue d’ensemble de l’architecture et des technologies avant d’opter pour telle ou telle approche d’application distribuée nouvelle et moderne.</span><span class="sxs-lookup"><span data-stu-id="01a9d-147">You will also find this guide useful if you are a technical decision maker, such as an enterprise architect, who wants an architecture and technology overview before you decide on what approach to select for new and modern distributed applications.</span></span>

### <a name="how-to-use-this-guide"></a><span data-ttu-id="01a9d-148">Comment utiliser ce guide</span><span class="sxs-lookup"><span data-stu-id="01a9d-148">How to use this guide</span></span>

<span data-ttu-id="01a9d-149">La première partie de ce guide offre une présentation des conteneurs Docker, explique comment choisir entre .NET Core et le .NET Framework comme framework de développement et propose une vue d’ensemble des microservices.</span><span class="sxs-lookup"><span data-stu-id="01a9d-149">The first part of this guide introduces Docker containers, discusses how to choose between .NET Core and the .NET Framework as a development framework, and provides an overview of microservices.</span></span> <span data-ttu-id="01a9d-150">Ce contenu s’adresse aux architectes et aux décideurs techniques qui souhaitent obtenir une vue d’ensemble, mais qui n’ont pas besoin de s’attarder sur les détails d’implémentation de code.</span><span class="sxs-lookup"><span data-stu-id="01a9d-150">This content is for architects and technical decision makers who want an overview but don't need to focus on code implementation details.</span></span>

<span data-ttu-id="01a9d-151">La deuxième partie du guide commence par la section [Processus de développement des applications basées sur Docker](./docker-application-development-process/index.md).</span><span class="sxs-lookup"><span data-stu-id="01a9d-151">The second part of the guide starts with the [Development process for Docker based applications](./docker-application-development-process/index.md) section.</span></span> <span data-ttu-id="01a9d-152">Elle porte essentiellement sur les modèles de développement et de microservices pour l’implémentation d’applications utilisant .NET Core et Docker.</span><span class="sxs-lookup"><span data-stu-id="01a9d-152">It focuses on development and microservice patterns for implementing applications using .NET Core and Docker.</span></span> <span data-ttu-id="01a9d-153">Cette section intéressera plus particulièrement les développeurs et les architectes qui souhaitent se concentrer sur le code et les détails concernant les modèles et l’implémentation.</span><span class="sxs-lookup"><span data-stu-id="01a9d-153">This section will be of most interest to developers and architects who want to focus on code and on patterns and implementation details.</span></span>

## <a name="related-microservice-and-container-based-reference-application-eshoponcontainers"></a><span data-ttu-id="01a9d-154">Application de référence basée sur des conteneurs et des microservices : eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="01a9d-154">Related microservice and container-based reference application: eShopOnContainers</span></span>

<span data-ttu-id="01a9d-155">L’application eShopOnContainers est une application de référence open source pour .NET Core et les microservices qui a été conçue pour être déployée en utilisant des conteneurs Docker.</span><span class="sxs-lookup"><span data-stu-id="01a9d-155">The eShopOnContainers application is an open-source reference app for .NET Core and microservices that is designed to be deployed using Docker containers.</span></span> <span data-ttu-id="01a9d-156">L’application est constituée de divers sous-systèmes, notamment de plusieurs frontends d’interface utilisateur d’e-store (une application MVC web, une application SPA web et une application mobile native).</span><span class="sxs-lookup"><span data-stu-id="01a9d-156">The application consists of multiple subsystems, including several e-store UI front ends (a Web MVC app, a Web SPA, and a native mobile app).</span></span> <span data-ttu-id="01a9d-157">Elle inclut aussi les microservices et les conteneurs backend pour toutes les opérations côté serveur nécessaires.</span><span class="sxs-lookup"><span data-stu-id="01a9d-157">It also includes the back-end microservices and containers for all required server-side operations.</span></span>

<span data-ttu-id="01a9d-158">L’objectif de l’application est de présenter des modèles architecturaux.</span><span class="sxs-lookup"><span data-stu-id="01a9d-158">The purpose of the application is to showcase architectural patterns.</span></span> <span data-ttu-id="01a9d-159">**IL NE S’AGIT PAS D’UN MODÈLE PRÊT POUR LA PRODUCTION** permettant de démarrer des applications réelles.</span><span class="sxs-lookup"><span data-stu-id="01a9d-159">**IT IS NOT A PRODUCTION-READY TEMPLATE** to start real-world applications.</span></span> <span data-ttu-id="01a9d-160">En fait, l’application est dans un état bêta permanent, car il est également utilisé pour tester de nouvelles technologies potentiellement intéressantes comme ils apparaissent.</span><span class="sxs-lookup"><span data-stu-id="01a9d-160">In fact, the application is in a permanent beta state, as it's also used to test new potentially interesting technologies as they show up.</span></span>

## <a name="send-us-your-feedback"></a><span data-ttu-id="01a9d-161">Envoyez-nous vos commentaires !</span><span class="sxs-lookup"><span data-stu-id="01a9d-161">Send us your feedback!</span></span>

<span data-ttu-id="01a9d-162">Nous avons rédigé ce guide pour vous aider à comprendre l’architecture des applications en conteneur et des microservices dans .NET.</span><span class="sxs-lookup"><span data-stu-id="01a9d-162">We wrote this guide to help you understand the architecture of containerized applications and microservices in .NET.</span></span> <span data-ttu-id="01a9d-163">Le guide et l’application de référence associée étant voués à évoluer, nous faisons bon accueil à vos commentaires !</span><span class="sxs-lookup"><span data-stu-id="01a9d-163">The guide and related reference application will be evolving, so we welcome your feedback!</span></span> <span data-ttu-id="01a9d-164">Si vous avez des commentaires sur la façon <https://aka.ms/ebookfeedback>dont ce guide peut être amélioré, soumettez des commentaires à .</span><span class="sxs-lookup"><span data-stu-id="01a9d-164">If you have comments about how this guide can be improved, submit feedback at <https://aka.ms/ebookfeedback>.</span></span>

## <a name="credits"></a><span data-ttu-id="01a9d-165">Crédits</span><span class="sxs-lookup"><span data-stu-id="01a9d-165">Credits</span></span>

<span data-ttu-id="01a9d-166">Coauteurs :</span><span class="sxs-lookup"><span data-stu-id="01a9d-166">Co-Authors:</span></span>

> <span data-ttu-id="01a9d-167">**Cesar de la Torre**, chef de produit, équipe produit .NET, Microsoft Corp.</span><span class="sxs-lookup"><span data-stu-id="01a9d-167">**Cesar de la Torre**, Sr. PM, .NET product team, Microsoft Corp.</span></span>
>
> <span data-ttu-id="01a9d-168">**Bill Wagner**, développeur de contenu en chef, C+E, Microsoft Corp.</span><span class="sxs-lookup"><span data-stu-id="01a9d-168">**Bill Wagner**, Sr. Content Developer, C+E, Microsoft Corp.</span></span>
>
> <span data-ttu-id="01a9d-169">**Mike Rousos**, ingénieur logiciel principal, équipe DevDiv CAT, Microsoft</span><span class="sxs-lookup"><span data-stu-id="01a9d-169">**Mike Rousos**, Principal Software Engineer, DevDiv CAT team, Microsoft</span></span>

<span data-ttu-id="01a9d-170">Rédacteurs :</span><span class="sxs-lookup"><span data-stu-id="01a9d-170">Editors:</span></span>

> <span data-ttu-id="01a9d-171">**Mike Pope**</span><span class="sxs-lookup"><span data-stu-id="01a9d-171">**Mike Pope**</span></span>
>
> <span data-ttu-id="01a9d-172">**Steve Hoag**</span><span class="sxs-lookup"><span data-stu-id="01a9d-172">**Steve Hoag**</span></span>

<span data-ttu-id="01a9d-173">Participants et réviseurs :</span><span class="sxs-lookup"><span data-stu-id="01a9d-173">Participants and reviewers:</span></span>

> <span data-ttu-id="01a9d-174">**Jeffrey Richter**, ingénieur logiciel partenaire, équipe Azure, Microsoft</span><span class="sxs-lookup"><span data-stu-id="01a9d-174">**Jeffrey Richter**, Partner Software Eng, Azure team, Microsoft</span></span>
>
> <span data-ttu-id="01a9d-175">**Jimmy Bogard**, architecte en chef chez Headspring</span><span class="sxs-lookup"><span data-stu-id="01a9d-175">**Jimmy Bogard**, Chief Architect at Headspring</span></span>
>
> <span data-ttu-id="01a9d-176">**Udi Dahan**, fondateur et PDG, Particular Software</span><span class="sxs-lookup"><span data-stu-id="01a9d-176">**Udi Dahan**, Founder & CEO, Particular Software</span></span>
>
> <span data-ttu-id="01a9d-177">**Jimmy Nilsson**, co-fondateur et PDG de Factor10</span><span class="sxs-lookup"><span data-stu-id="01a9d-177">**Jimmy Nilsson**, Co-founder and CEO of Factor10</span></span>
>
> <span data-ttu-id="01a9d-178">**Glenn Condron**, gestionnaire de programmes en chef, équipe ASP.NET</span><span class="sxs-lookup"><span data-stu-id="01a9d-178">**Glenn Condron**, Sr. Program Manager, ASP.NET team</span></span>
>
> <span data-ttu-id="01a9d-179">**Mark Fussell**, responsable principal de la gestion de projets, équipe Azure Service Fabric, Microsoft</span><span class="sxs-lookup"><span data-stu-id="01a9d-179">**Mark Fussell**, Principal PM Lead, Azure Service Fabric team, Microsoft</span></span>
>
> <span data-ttu-id="01a9d-180">**Diego Vega**, responsable de la gestion de projets, équipe Entity Framework, Microsoft</span><span class="sxs-lookup"><span data-stu-id="01a9d-180">**Diego Vega**, PM Lead, Entity Framework team, Microsoft</span></span>
>
> <span data-ttu-id="01a9d-181">**Barry Dorrans**, gestionnaire de programmes de sécurité en chef</span><span class="sxs-lookup"><span data-stu-id="01a9d-181">**Barry Dorrans**, Sr. Security Program Manager</span></span>
>
> <span data-ttu-id="01a9d-182">**Rowan Miller**, gestionnaire de programmes en chef, Microsoft</span><span class="sxs-lookup"><span data-stu-id="01a9d-182">**Rowan Miller**, Sr. Program Manager, Microsoft</span></span>
>
> <span data-ttu-id="01a9d-183">**Ankit Asthana**, responsable principal de la gestion de projets, équipe .NET, Microsoft</span><span class="sxs-lookup"><span data-stu-id="01a9d-183">**Ankit Asthana**, Principal PM Manager, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="01a9d-184">**Scott Hunter**, chef de projet directeur partenaire, équipe .NET, Microsoft</span><span class="sxs-lookup"><span data-stu-id="01a9d-184">**Scott Hunter**, Partner Director PM, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="01a9d-185">**Nish Anil**, responsable de programme senior, équipe .NET, Microsoft</span><span class="sxs-lookup"><span data-stu-id="01a9d-185">**Nish Anil**, Sr. Program Manager, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="01a9d-186">**Dylan Reisenberger**, architecte et responsable de développement chez Polly</span><span class="sxs-lookup"><span data-stu-id="01a9d-186">**Dylan Reisenberger**, Architect and Dev Lead at Polly</span></span>
>
> <span data-ttu-id="01a9d-187">**Steve « ardalis » Smith** - Architecte et formateur logiciel - [Ardalis.com](https://ardalis.com)</span><span class="sxs-lookup"><span data-stu-id="01a9d-187">**Steve "ardalis" Smith** - Software Architect and Trainer - [Ardalis.com](https://ardalis.com)</span></span>
>
> <span data-ttu-id="01a9d-188">**Ian Cooper**, architecte développement chez Brighter</span><span class="sxs-lookup"><span data-stu-id="01a9d-188">**Ian Cooper**, Coding Architect at Brighter</span></span>
>
> <span data-ttu-id="01a9d-189">**Unai Zorrilla**, architecte et responsable de développement chez Plain Concepts</span><span class="sxs-lookup"><span data-stu-id="01a9d-189">**Unai Zorrilla**, Architect and Dev Lead at Plain Concepts</span></span>
>
> <span data-ttu-id="01a9d-190">**Eduard Tomas**, responsable de développement chez Plain Concepts</span><span class="sxs-lookup"><span data-stu-id="01a9d-190">**Eduard Tomas**, Dev Lead at Plain Concepts</span></span>
>
> <span data-ttu-id="01a9d-191">**Ramon Tomas**, développeur chez Plain Concepts</span><span class="sxs-lookup"><span data-stu-id="01a9d-191">**Ramon Tomas**, Developer at Plain Concepts</span></span>
>
> <span data-ttu-id="01a9d-192">**David Sanz**, développeur chez Plain Concepts</span><span class="sxs-lookup"><span data-stu-id="01a9d-192">**David Sanz**, Developer at Plain Concepts</span></span>
>
> <span data-ttu-id="01a9d-193">**Javier Valero**, chef des opérations chez Grupo Solutio</span><span class="sxs-lookup"><span data-stu-id="01a9d-193">**Javier Valero**, Chief Operating Officer at Grupo Solutio</span></span>
>
> <span data-ttu-id="01a9d-194">**Pierre Millet**, consultant en chef, Microsoft</span><span class="sxs-lookup"><span data-stu-id="01a9d-194">**Pierre Millet**, Sr. Consultant, Microsoft</span></span>
>
> <span data-ttu-id="01a9d-195">**Michael Friis**, chef de produit, Docker Inc.</span><span class="sxs-lookup"><span data-stu-id="01a9d-195">**Michael Friis**, Product Manager, Docker Inc</span></span>
>
> <span data-ttu-id="01a9d-196">**Charles Lowell**, ingénieur logiciel, équipe VS CAT, Microsoft</span><span class="sxs-lookup"><span data-stu-id="01a9d-196">**Charles Lowell**, Software Engineer, VS CAT team, Microsoft</span></span>
>
> <span data-ttu-id="01a9d-197">**Miguel Veloso**, Ingénieur Développement Logiciel chez Plain Concepts</span><span class="sxs-lookup"><span data-stu-id="01a9d-197">**Miguel Veloso**, Software Development Engineer at Plain Concepts</span></span>

## <a name="copyright"></a><span data-ttu-id="01a9d-198">copyright</span><span class="sxs-lookup"><span data-stu-id="01a9d-198">Copyright</span></span>

<span data-ttu-id="01a9d-199">PUBLIÉ PAR</span><span class="sxs-lookup"><span data-stu-id="01a9d-199">PUBLISHED BY</span></span>

<span data-ttu-id="01a9d-200">Division Développeurs Microsoft, équipes produit .NET et Visual Studio</span><span class="sxs-lookup"><span data-stu-id="01a9d-200">Microsoft Developer Division, .NET and Visual Studio product teams</span></span>

<span data-ttu-id="01a9d-201">Division de Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="01a9d-201">A division of Microsoft Corporation</span></span>

<span data-ttu-id="01a9d-202">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="01a9d-202">One Microsoft Way</span></span>

<span data-ttu-id="01a9d-203">Redmond, Washington 98052-6399</span><span class="sxs-lookup"><span data-stu-id="01a9d-203">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="01a9d-204">Copyright © 2020 par Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="01a9d-204">Copyright © 2020 by Microsoft Corporation</span></span>

<span data-ttu-id="01a9d-205">Tous droits réservés.</span><span class="sxs-lookup"><span data-stu-id="01a9d-205">All rights reserved.</span></span> <span data-ttu-id="01a9d-206">Aucune partie du contenu de ce document ne peut être reproduite ou transmise sous quelque forme ou par quelque moyen que ce soit sans l’autorisation écrite de l’éditeur.</span><span class="sxs-lookup"><span data-stu-id="01a9d-206">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="01a9d-207">Ce document est fourni « en l’état » et exprime les points de vue et les opinions de son auteur.</span><span class="sxs-lookup"><span data-stu-id="01a9d-207">This book is provided "as-is" and expresses the author's views and opinions.</span></span> <span data-ttu-id="01a9d-208">Les points de vue, les opinions et les informations exprimés dans ce document, notamment l’URL et autres références à des sites web Internet, peuvent faire l’objet de modifications sans préavis.</span><span class="sxs-lookup"><span data-stu-id="01a9d-208">The views, opinions and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="01a9d-209"> Certains exemples sont fournis à titre indicatif uniquement et sont fictifs.</span><span class="sxs-lookup"><span data-stu-id="01a9d-209">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="01a9d-210">Toute association ou lien est purement involontaire ou fortuit.</span><span class="sxs-lookup"><span data-stu-id="01a9d-210">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="01a9d-211">Microsoft et les marques commerciales mentionnées dans la page web « Marques » sur <https://www.microsoft.com> sont des marques du groupe Microsoft.</span><span class="sxs-lookup"><span data-stu-id="01a9d-211">Microsoft and the trademarks listed at <https://www.microsoft.com> on the "Trademarks" webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="01a9d-212">Mac et macOS sont des marques commerciales d’Apple Inc.</span><span class="sxs-lookup"><span data-stu-id="01a9d-212">Mac and macOS are trademarks of Apple Inc.</span></span>

<span data-ttu-id="01a9d-213">Le logo de la baleine Docker est une marque déposée de Docker, Inc. Utilisée par permission.</span><span class="sxs-lookup"><span data-stu-id="01a9d-213">The Docker whale logo is a registered trademark of Docker, Inc. Used by permission.</span></span>

<span data-ttu-id="01a9d-214">Toutes les autres marques et tous les autres logos sont la propriété de leurs propriétaires respectifs.</span><span class="sxs-lookup"><span data-stu-id="01a9d-214">All other marks and logos are property of their respective owners.</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="01a9d-215">Suivant</span><span class="sxs-lookup"><span data-stu-id="01a9d-215">Next</span></span>](container-docker-introduction/index.md)
