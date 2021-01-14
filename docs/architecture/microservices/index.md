---
title: Microservices .NET. Architecture pour les applications .NET en conteneur
description: Architecture des microservices .NET pour les applications .NET en conteneur | Les microservices sont des services modulables qui peuvent se déployer indépendamment. Les conteneurs Docker (pour Linux et Windows) simplifient le déploiement et les tests en regroupant un service et ses dépendances dans une seule unité, laquelle est ensuite exécutée dans un environnement isolé.
ms.date: 01/13/2021
ms.openlocfilehash: a9017d2e9acbcbb861a35f0187632dc90c52e171
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/14/2021
ms.locfileid: "98188372"
---
# <a name="net-microservices-architecture-for-containerized-net-applications"></a><span data-ttu-id="9f761-105">Microservices .NET : Architecture pour les applications .NET en conteneur</span><span class="sxs-lookup"><span data-stu-id="9f761-105">.NET Microservices: Architecture for Containerized .NET Applications</span></span>

![Couverture de livre](./media/cover-small.png)

<span data-ttu-id="9f761-107">**Édition v 5.0** -mise à jour vers ASP.net Core 5,0</span><span class="sxs-lookup"><span data-stu-id="9f761-107">**EDITION v5.0** - Updated to ASP.NET Core 5.0</span></span>

<span data-ttu-id="9f761-108">Reportez-vous à [Journal des modifications](https://aka.ms/MicroservicesEbookChangelog) pour les mises à jour de livres et les contributions de la communauté.</span><span class="sxs-lookup"><span data-stu-id="9f761-108">Refer [changelog](https://aka.ms/MicroservicesEbookChangelog) for the book updates and community contributions.</span></span>

<span data-ttu-id="9f761-109">Ce guide est une introduction au développement d’applications basées sur les microservices et à la gestion de celles-ci au moyen de conteneurs.</span><span class="sxs-lookup"><span data-stu-id="9f761-109">This guide is an introduction to developing microservices-based applications and managing them using containers.</span></span> <span data-ttu-id="9f761-110">Il aborde les approches de conception et d’implémentation architecturales à l’aide de .NET et de conteneurs d’ancrage.</span><span class="sxs-lookup"><span data-stu-id="9f761-110">It discusses architectural design and implementation approaches using .NET and Docker containers.</span></span>

<span data-ttu-id="9f761-111">Pour faciliter la prise en main, ce guide met en lumière une application de référence en conteneur basée sur des microservices que vous pouvez explorer.</span><span class="sxs-lookup"><span data-stu-id="9f761-111">To make it easier to get started, the guide focuses on a reference containerized and microservice-based application that you can explore.</span></span> <span data-ttu-id="9f761-112">L’application de référence est disponible sur le dépôt GitHub [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers).</span><span class="sxs-lookup"><span data-stu-id="9f761-112">The reference application is available at the [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) GitHub repo.</span></span>

## <a name="action-links"></a><span data-ttu-id="9f761-113">Liens d'action</span><span class="sxs-lookup"><span data-stu-id="9f761-113">Action links</span></span>

- <span data-ttu-id="9f761-114">Ce livre électronique est également disponible au [Téléchargement](https://aka.ms/microservicesebook) au format PDF (version anglaise uniquement).</span><span class="sxs-lookup"><span data-stu-id="9f761-114">This e-book is also available in a PDF format (English version only) [Download](https://aka.ms/microservicesebook)</span></span>

- <span data-ttu-id="9f761-115">Clonez/dupliquez (fork) l’application de référence [eShopOnContainers sur GitHub](https://github.com/dotnet-architecture/eShopOnContainers)</span><span class="sxs-lookup"><span data-stu-id="9f761-115">Clone/Fork the reference application [eShopOnContainers on GitHub](https://github.com/dotnet-architecture/eShopOnContainers)</span></span>

- <span data-ttu-id="9f761-116">Regardez la [vidéo d’introduction sur Channel 9](https://aka.ms/microservices-video)</span><span class="sxs-lookup"><span data-stu-id="9f761-116">Watch the [introductory video on Channel 9](https://aka.ms/microservices-video)</span></span>

- <span data-ttu-id="9f761-117">Familiarisez-vous avec [l’architecture de microservices](https://aka.ms/MicroservicesArchitecture) immédiatement</span><span class="sxs-lookup"><span data-stu-id="9f761-117">Get to know the [Microservices Architecture](https://aka.ms/MicroservicesArchitecture) right away</span></span>

## <a name="introduction"></a><span data-ttu-id="9f761-118">Introduction</span><span class="sxs-lookup"><span data-stu-id="9f761-118">Introduction</span></span>

<span data-ttu-id="9f761-119">Les entreprises cherchent de plus en plus à réaliser des économies, à résoudre les problèmes de déploiement et à améliorer les opérations DevOps et de production en utilisant des conteneurs.</span><span class="sxs-lookup"><span data-stu-id="9f761-119">Enterprises are increasingly realizing cost savings, solving deployment problems, and improving DevOps and production operations by using containers.</span></span> <span data-ttu-id="9f761-120">Microsoft a fait preuve d’innovation dans le domaine des conteneurs pour Windows et Linux en créant des produits comme Azure Kubernetes Service et Azure Service Fabric et en formant des partenariats avec des acteurs phares du secteur tels que Docker, Mesosphere et Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="9f761-120">Microsoft has been releasing container innovations for Windows and Linux by creating products like Azure Kubernetes Service and Azure Service Fabric, and by partnering with industry leaders like Docker, Mesosphere, and Kubernetes.</span></span> <span data-ttu-id="9f761-121">Ces produits offrent aux entreprises des solutions de conteneur qui leur permettent de créer et déployer des applications à la vitesse et à l’échelle du cloud, indépendamment de la plateforme ou des outils qu’elles ont choisi d’utiliser.</span><span class="sxs-lookup"><span data-stu-id="9f761-121">These products deliver container solutions that help companies build and deploy applications at cloud speed and scale, whatever their choice of platform or tools.</span></span>

<span data-ttu-id="9f761-122">Docker est en passe de devenir de facto le standard dans le domaine du conteneur, recueillant l’adhésion des éditeurs les plus en vue dans les écosystèmes Windows et Linux.</span><span class="sxs-lookup"><span data-stu-id="9f761-122">Docker is becoming the de facto standard in the container industry, supported by the most significant vendors in the Windows and Linux ecosystems.</span></span> <span data-ttu-id="9f761-123">(Microsoft est l’un des principaux fournisseurs de Cloud qui prennent en charge l’arrimeur.) À l’avenir, l’arrimeur sera probablement omniprésent dans n’importe quel centre de l’environnement Cloud ou local.</span><span class="sxs-lookup"><span data-stu-id="9f761-123">(Microsoft is one of the main cloud vendors supporting Docker.) In the future, Docker will probably be ubiquitous in any datacenter in the cloud or on-premises.</span></span>

<span data-ttu-id="9f761-124">Par ailleurs, l’architecture de [microservices](https://martinfowler.com/articles/microservices.html) est une approche qui devient importante pour les applications stratégiques distribuées.</span><span class="sxs-lookup"><span data-stu-id="9f761-124">In addition, the [microservices](https://martinfowler.com/articles/microservices.html) architecture is emerging as an important approach for distributed mission-critical applications.</span></span> <span data-ttu-id="9f761-125">Dans une architecture basée sur les microservices, l’application repose sur un ensemble de services qui peuvent être développés, testés, déployés et versionnés de manière indépendante.</span><span class="sxs-lookup"><span data-stu-id="9f761-125">In a microservice-based architecture, the application is built on a collection of services that can be developed, tested, deployed, and versioned independently.</span></span>

## <a name="about-this-guide"></a><span data-ttu-id="9f761-126">À propos de ce guide</span><span class="sxs-lookup"><span data-stu-id="9f761-126">About this guide</span></span>

<span data-ttu-id="9f761-127">Ce guide est une introduction au développement d’applications basées sur les microservices et à la gestion de celles-ci au moyen de conteneurs.</span><span class="sxs-lookup"><span data-stu-id="9f761-127">This guide is an introduction to developing microservices-based applications and managing them using containers.</span></span> <span data-ttu-id="9f761-128">Il aborde les approches de conception et d’implémentation architecturales à l’aide de .NET et de conteneurs d’ancrage.</span><span class="sxs-lookup"><span data-stu-id="9f761-128">It discusses architectural design and implementation approaches using .NET and Docker containers.</span></span> <span data-ttu-id="9f761-129">Pour faciliter la prise en main des conteneurs et des microservices, ce guide met en lumière une application de référence en conteneur basée sur des microservices que vous pouvez explorer.</span><span class="sxs-lookup"><span data-stu-id="9f761-129">To make it easier to get started with containers and microservices, the guide focuses on a reference containerized and microservice-based application that you can explore.</span></span> <span data-ttu-id="9f761-130">L’exemple d’application est disponible sur le dépôt GitHub [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers).</span><span class="sxs-lookup"><span data-stu-id="9f761-130">The sample application is available at the [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) GitHub repo.</span></span>

<span data-ttu-id="9f761-131">Ce guide fournit des conseils d’architecture et de développement de base principalement au niveau de l’environnement de développement, et se concentre sur deux technologies : Ancrable et .NET.</span><span class="sxs-lookup"><span data-stu-id="9f761-131">This guide provides foundational development and architectural guidance primarily at a development environment level with a focus on two technologies: Docker and .NET.</span></span> <span data-ttu-id="9f761-132">Notre objectif est que vous lisiez ce guide en pensant à la conception de votre application sans vous polariser sur l’infrastructure (cloud ou locale) de votre environnement de production.</span><span class="sxs-lookup"><span data-stu-id="9f761-132">Our intention is that you read this guide when thinking about your application design without focusing on the infrastructure (cloud or on-premises) of your production environment.</span></span> <span data-ttu-id="9f761-133">Vous prendrez vos décisions concernant l’infrastructure plus tard, au moment de créer vos applications pour la production.</span><span class="sxs-lookup"><span data-stu-id="9f761-133">You will make decisions about your infrastructure later, when you create your production-ready applications.</span></span> <span data-ttu-id="9f761-134">Par conséquent, ce guide se veut neutre concernant l’infrastructure et davantage centré sur l’environnement de développement.</span><span class="sxs-lookup"><span data-stu-id="9f761-134">Therefore, this guide is intended to be infrastructure agnostic and more development-environment-centric.</span></span>

<span data-ttu-id="9f761-135">Après avoir examiné ce guide, votre prochaine étape consistera à vous familiariser avec les microservices prêts pour la production dans Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="9f761-135">After you have studied this guide, your next step would be to learn about production-ready microservices on Microsoft Azure.</span></span>

## <a name="version"></a><span data-ttu-id="9f761-136">Version</span><span class="sxs-lookup"><span data-stu-id="9f761-136">Version</span></span>

<span data-ttu-id="9f761-137">Ce guide a été révisé pour couvrir la version de **.net 5** , ainsi que de nombreuses mises à jour supplémentaires liées aux mêmes « vagues » de technologies (c’est-à-dire, Azure et des technologies tierces) qui coïncident avec la version .net 5.</span><span class="sxs-lookup"><span data-stu-id="9f761-137">This guide has been revised to cover **.NET 5** version along with many additional updates related to the same “wave” of technologies (that is, Azure and additional third-party technologies) coinciding in time with the .NET 5 release.</span></span> <span data-ttu-id="9f761-138">C’est la raison pour laquelle la version du livre a également été mise à jour vers la version **5,0**.</span><span class="sxs-lookup"><span data-stu-id="9f761-138">That’s why the book version has also been updated to version **5.0**.</span></span>

## <a name="what-this-guide-does-not-cover"></a><span data-ttu-id="9f761-139">Sujets non abordés dans ce guide</span><span class="sxs-lookup"><span data-stu-id="9f761-139">What this guide does not cover</span></span>

<span data-ttu-id="9f761-140">Ce guide ne traite pas du cycle de vie des applications, de DevOps, des pipelines CI/CD, ni du travail d’équipe.</span><span class="sxs-lookup"><span data-stu-id="9f761-140">This guide does not focus on the application lifecycle, DevOps, CI/CD pipelines, or team work.</span></span> <span data-ttu-id="9f761-141">Le guide complémentaire intitulé [Containerized Docker Application Lifecycle with Microsoft Platform and Tools](https://aka.ms/dockerlifecycleebook) (Cycle de vie des applications Docker en conteneur avec la plateforme et les outils Microsoft) porte essentiellement sur ce sujet.</span><span class="sxs-lookup"><span data-stu-id="9f761-141">The complementary guide [Containerized Docker Application Lifecycle with Microsoft Platform and Tools](https://aka.ms/dockerlifecycleebook) focuses on that subject.</span></span> <span data-ttu-id="9f761-142">Le présent guide ne fournit pas non plus de détails sur l’implémentation de l’infrastructure Azure, notamment sur les orchestrateurs spécifiques.</span><span class="sxs-lookup"><span data-stu-id="9f761-142">The current guide also does not provide implementation details on Azure infrastructure, such as information on specific orchestrators.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="9f761-143">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="9f761-143">Additional resources</span></span>

- <span data-ttu-id="9f761-144">**Containerized Docker Application Lifecycle with Microsoft Platform and Tools** (livre électronique téléchargeable)</span><span class="sxs-lookup"><span data-stu-id="9f761-144">**Containerized Docker Application Lifecycle with Microsoft Platform and Tools** (downloadable e-book)</span></span>  
    <https://aka.ms/dockerlifecycleebook>

## <a name="who-should-use-this-guide"></a><span data-ttu-id="9f761-145">Public visé par ce guide</span><span class="sxs-lookup"><span data-stu-id="9f761-145">Who should use this guide</span></span>

<span data-ttu-id="9f761-146">Nous avons rédigé ce guide à l’intention des développeurs et des architectes de solutions qui n’ont pas d’expérience en matière développement d’applications Docker et d’architecture basée sur les microservices.</span><span class="sxs-lookup"><span data-stu-id="9f761-146">We wrote this guide for developers and solution architects who are new to Docker-based application development and to microservices-based architecture.</span></span> <span data-ttu-id="9f761-147">Ce guide vous concerne si vous souhaitez apprendre à concevoir, concevoir et implémenter des applications de preuve de concept avec des technologies de développement Microsoft (avec une attention particulière sur .NET) et avec des conteneurs d’ancrage.</span><span class="sxs-lookup"><span data-stu-id="9f761-147">This guide is for you if you want to learn how to architect, design, and implement proof-of-concept applications with Microsoft development technologies (with special focus on .NET) and with Docker containers.</span></span>

<span data-ttu-id="9f761-148">Ce guide saura aussi vous intéresser si vous êtes un décideur technique, tel qu’un architecte d’entreprise, désireux d’avoir une vue d’ensemble de l’architecture et des technologies avant d’opter pour telle ou telle approche d’application distribuée nouvelle et moderne.</span><span class="sxs-lookup"><span data-stu-id="9f761-148">You will also find this guide useful if you are a technical decision maker, such as an enterprise architect, who wants an architecture and technology overview before you decide on what approach to select for new and modern distributed applications.</span></span>

### <a name="how-to-use-this-guide"></a><span data-ttu-id="9f761-149">Comment utiliser ce guide</span><span class="sxs-lookup"><span data-stu-id="9f761-149">How to use this guide</span></span>

<span data-ttu-id="9f761-150">La première partie de ce guide offre une présentation des conteneurs Docker, explique comment choisir entre .NET Core et le .NET Framework comme framework de développement et propose une vue d’ensemble des microservices.</span><span class="sxs-lookup"><span data-stu-id="9f761-150">The first part of this guide introduces Docker containers, discusses how to choose between .NET Core and the .NET Framework as a development framework, and provides an overview of microservices.</span></span> <span data-ttu-id="9f761-151">Ce contenu s’adresse aux architectes et aux décideurs techniques qui souhaitent obtenir une vue d’ensemble, mais qui n’ont pas besoin de s’attarder sur les détails d’implémentation de code.</span><span class="sxs-lookup"><span data-stu-id="9f761-151">This content is for architects and technical decision makers who want an overview but don't need to focus on code implementation details.</span></span>

<span data-ttu-id="9f761-152">La deuxième partie du guide commence par la section [Processus de développement des applications basées sur Docker](./docker-application-development-process/index.md).</span><span class="sxs-lookup"><span data-stu-id="9f761-152">The second part of the guide starts with the [Development process for Docker based applications](./docker-application-development-process/index.md) section.</span></span> <span data-ttu-id="9f761-153">Il se concentre sur les modèles de développement et de microservice pour implémenter des applications à l’aide de .NET Core et de Dockr.</span><span class="sxs-lookup"><span data-stu-id="9f761-153">It focuses on the development and microservice patterns for implementing applications using .NET Core and Docker.</span></span> <span data-ttu-id="9f761-154">Cette section intéressera plus particulièrement les développeurs et les architectes qui souhaitent se concentrer sur le code et les détails concernant les modèles et l’implémentation.</span><span class="sxs-lookup"><span data-stu-id="9f761-154">This section will be of most interest to developers and architects who want to focus on code and on patterns and implementation details.</span></span>

## <a name="related-microservice-and-container-based-reference-application-eshoponcontainers"></a><span data-ttu-id="9f761-155">Application de référence basée sur des conteneurs et des microservices : eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="9f761-155">Related microservice and container-based reference application: eShopOnContainers</span></span>

<span data-ttu-id="9f761-156">L’application eShopOnContainers est une application de référence Open source pour .NET et des microservices conçue pour être déployée à l’aide de conteneurs d’ancrage.</span><span class="sxs-lookup"><span data-stu-id="9f761-156">The eShopOnContainers application is an open-source reference app for .NET and microservices that is designed to be deployed using Docker containers.</span></span> <span data-ttu-id="9f761-157">L’application se compose de plusieurs sous-systèmes, y compris plusieurs serveurs frontaux d’interface utilisateur du magasin e-Store (une application Web MVC, un SPA Web et une application mobile native).</span><span class="sxs-lookup"><span data-stu-id="9f761-157">The application consists of multiple subsystems, including several e-store UI front-ends (a Web MVC app, a Web SPA, and a native mobile app).</span></span> <span data-ttu-id="9f761-158">Elle inclut aussi les microservices et les conteneurs backend pour toutes les opérations côté serveur nécessaires.</span><span class="sxs-lookup"><span data-stu-id="9f761-158">It also includes the back-end microservices and containers for all required server-side operations.</span></span>

<span data-ttu-id="9f761-159">L’objectif de l’application est de présenter des modèles architecturaux.</span><span class="sxs-lookup"><span data-stu-id="9f761-159">The purpose of the application is to showcase architectural patterns.</span></span> <span data-ttu-id="9f761-160">**IL NE S’AGIT PAS D’UN MODÈLE PRÊT POUR LA PRODUCTION** permettant de démarrer des applications réelles.</span><span class="sxs-lookup"><span data-stu-id="9f761-160">**IT IS NOT A PRODUCTION-READY TEMPLATE** to start real-world applications.</span></span> <span data-ttu-id="9f761-161">En fait, l’application est dans un État bêta permanent, car elle est également utilisée pour tester de nouvelles technologies potentiellement intéressantes lorsqu’elles s’affichent.</span><span class="sxs-lookup"><span data-stu-id="9f761-161">In fact, the application is in a permanent beta state, as it's also used to test new potentially interesting technologies as they show up.</span></span>

## <a name="send-us-your-feedback"></a><span data-ttu-id="9f761-162">Envoyez-nous vos commentaires !</span><span class="sxs-lookup"><span data-stu-id="9f761-162">Send us your feedback!</span></span>

<span data-ttu-id="9f761-163">Nous avons rédigé ce guide pour vous aider à comprendre l’architecture des applications en conteneur et des microservices dans .NET.</span><span class="sxs-lookup"><span data-stu-id="9f761-163">We wrote this guide to help you understand the architecture of containerized applications and microservices in .NET.</span></span> <span data-ttu-id="9f761-164">Le guide et l’application de référence associée étant voués à évoluer, nous faisons bon accueil à vos commentaires !</span><span class="sxs-lookup"><span data-stu-id="9f761-164">The guide and related reference application will be evolving, so we welcome your feedback!</span></span> <span data-ttu-id="9f761-165">Si vous avez des commentaires sur la façon dont ce guide peut être amélioré, envoyez vos commentaires à l’adresse <https://aka.ms/ebookfeedback> .</span><span class="sxs-lookup"><span data-stu-id="9f761-165">If you have comments about how this guide can be improved, submit feedback at <https://aka.ms/ebookfeedback>.</span></span>

## <a name="credits"></a><span data-ttu-id="9f761-166">Crédits</span><span class="sxs-lookup"><span data-stu-id="9f761-166">Credits</span></span>

<span data-ttu-id="9f761-167">Coauteurs :</span><span class="sxs-lookup"><span data-stu-id="9f761-167">Co-Authors:</span></span>

> <span data-ttu-id="9f761-168">**Cesar de la Torre**, chef de produit, équipe produit .NET, Microsoft Corp.</span><span class="sxs-lookup"><span data-stu-id="9f761-168">**Cesar de la Torre**, Sr. PM, .NET product team, Microsoft Corp.</span></span>
>
> <span data-ttu-id="9f761-169">**Bill Wagner**, développeur de contenu en chef, C+E, Microsoft Corp.</span><span class="sxs-lookup"><span data-stu-id="9f761-169">**Bill Wagner**, Sr. Content Developer, C+E, Microsoft Corp.</span></span>
>
> <span data-ttu-id="9f761-170">**Mike Rousos**, ingénieur logiciel principal, équipe DevDiv CAT, Microsoft</span><span class="sxs-lookup"><span data-stu-id="9f761-170">**Mike Rousos**, Principal Software Engineer, DevDiv CAT team, Microsoft</span></span>

<span data-ttu-id="9f761-171">Rédacteurs :</span><span class="sxs-lookup"><span data-stu-id="9f761-171">Editors:</span></span>

> <span data-ttu-id="9f761-172">**Mike Pope**</span><span class="sxs-lookup"><span data-stu-id="9f761-172">**Mike Pope**</span></span>
>
> <span data-ttu-id="9f761-173">**Steve Hoag**</span><span class="sxs-lookup"><span data-stu-id="9f761-173">**Steve Hoag**</span></span>

<span data-ttu-id="9f761-174">Participants et réviseurs :</span><span class="sxs-lookup"><span data-stu-id="9f761-174">Participants and reviewers:</span></span>

> <span data-ttu-id="9f761-175">**Jeffrey Richter**, ingénieur logiciel partenaire, équipe Azure, Microsoft</span><span class="sxs-lookup"><span data-stu-id="9f761-175">**Jeffrey Richter**, Partner Software Eng, Azure team, Microsoft</span></span>
>
> <span data-ttu-id="9f761-176">**Jimmy Bogard**, architecte en chef chez Headspring</span><span class="sxs-lookup"><span data-stu-id="9f761-176">**Jimmy Bogard**, Chief Architect at Headspring</span></span>
>
> <span data-ttu-id="9f761-177">**Udi Dahan**, fondateur et PDG, Particular Software</span><span class="sxs-lookup"><span data-stu-id="9f761-177">**Udi Dahan**, Founder & CEO, Particular Software</span></span>
>
> <span data-ttu-id="9f761-178">**Jimmy Nilsson**, co-fondateur et PDG de Factor10</span><span class="sxs-lookup"><span data-stu-id="9f761-178">**Jimmy Nilsson**, Co-founder and CEO of Factor10</span></span>
>
> <span data-ttu-id="9f761-179">**Glenn Condron**, gestionnaire de programmes en chef, équipe ASP.NET</span><span class="sxs-lookup"><span data-stu-id="9f761-179">**Glenn Condron**, Sr. Program Manager, ASP.NET team</span></span>
>
> <span data-ttu-id="9f761-180">**Mark Fussell**, responsable principal de la gestion de projets, équipe Azure Service Fabric, Microsoft</span><span class="sxs-lookup"><span data-stu-id="9f761-180">**Mark Fussell**, Principal PM Lead, Azure Service Fabric team, Microsoft</span></span>
>
> <span data-ttu-id="9f761-181">**Diego Vega**, responsable de la gestion de projets, équipe Entity Framework, Microsoft</span><span class="sxs-lookup"><span data-stu-id="9f761-181">**Diego Vega**, PM Lead, Entity Framework team, Microsoft</span></span>
>
> <span data-ttu-id="9f761-182">**Barry Dorrans**, gestionnaire de programmes de sécurité en chef</span><span class="sxs-lookup"><span data-stu-id="9f761-182">**Barry Dorrans**, Sr. Security Program Manager</span></span>
>
> <span data-ttu-id="9f761-183">**Rowan Miller**, gestionnaire de programmes en chef, Microsoft</span><span class="sxs-lookup"><span data-stu-id="9f761-183">**Rowan Miller**, Sr. Program Manager, Microsoft</span></span>
>
> <span data-ttu-id="9f761-184">**Ankit Asthana**, responsable principal de la gestion de projets, équipe .NET, Microsoft</span><span class="sxs-lookup"><span data-stu-id="9f761-184">**Ankit Asthana**, Principal PM Manager, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="9f761-185">**Scott Hunter**, chef de projet directeur partenaire, équipe .NET, Microsoft</span><span class="sxs-lookup"><span data-stu-id="9f761-185">**Scott Hunter**, Partner Director PM, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="9f761-186">**Nish Anil**, responsable de programme senior, équipe .NET, Microsoft</span><span class="sxs-lookup"><span data-stu-id="9f761-186">**Nish Anil**, Sr. Program Manager, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="9f761-187">**Dylan Reisenberger**, architecte et responsable de développement chez Polly</span><span class="sxs-lookup"><span data-stu-id="9f761-187">**Dylan Reisenberger**, Architect and Dev Lead at Polly</span></span>
>
> <span data-ttu-id="9f761-188">**Steve « ardalis » Smith** - Architecte et formateur logiciel - [Ardalis.com](https://ardalis.com)</span><span class="sxs-lookup"><span data-stu-id="9f761-188">**Steve "ardalis" Smith** - Software Architect and Trainer - [Ardalis.com](https://ardalis.com)</span></span>
>
> <span data-ttu-id="9f761-189">**Ian Cooper**, architecte développement chez Brighter</span><span class="sxs-lookup"><span data-stu-id="9f761-189">**Ian Cooper**, Coding Architect at Brighter</span></span>
>
> <span data-ttu-id="9f761-190">**Unai Zorrilla**, architecte et responsable de développement chez Plain Concepts</span><span class="sxs-lookup"><span data-stu-id="9f761-190">**Unai Zorrilla**, Architect and Dev Lead at Plain Concepts</span></span>
>
> <span data-ttu-id="9f761-191">**Eduard Tomas**, responsable de développement chez Plain Concepts</span><span class="sxs-lookup"><span data-stu-id="9f761-191">**Eduard Tomas**, Dev Lead at Plain Concepts</span></span>
>
> <span data-ttu-id="9f761-192">**Ramon Tomas**, développeur chez Plain Concepts</span><span class="sxs-lookup"><span data-stu-id="9f761-192">**Ramon Tomas**, Developer at Plain Concepts</span></span>
>
> <span data-ttu-id="9f761-193">**David Sanz**, développeur chez Plain Concepts</span><span class="sxs-lookup"><span data-stu-id="9f761-193">**David Sanz**, Developer at Plain Concepts</span></span>
>
> <span data-ttu-id="9f761-194">**Javier Valero**, chef des opérations chez Grupo Solutio</span><span class="sxs-lookup"><span data-stu-id="9f761-194">**Javier Valero**, Chief Operating Officer at Grupo Solutio</span></span>
>
> <span data-ttu-id="9f761-195">**Pierre Millet**, consultant en chef, Microsoft</span><span class="sxs-lookup"><span data-stu-id="9f761-195">**Pierre Millet**, Sr. Consultant, Microsoft</span></span>
>
> <span data-ttu-id="9f761-196">**Michael Friis**, chef de produit, Docker Inc.</span><span class="sxs-lookup"><span data-stu-id="9f761-196">**Michael Friis**, Product Manager, Docker Inc</span></span>
>
> <span data-ttu-id="9f761-197">**Charles Lowell**, ingénieur logiciel, équipe VS CAT, Microsoft</span><span class="sxs-lookup"><span data-stu-id="9f761-197">**Charles Lowell**, Software Engineer, VS CAT team, Microsoft</span></span>
>
> <span data-ttu-id="9f761-198">**Miguel Veloso**, ingénieur de développement logiciel chez des concepts simples</span><span class="sxs-lookup"><span data-stu-id="9f761-198">**Miguel Veloso**, Software Development Engineer at Plain Concepts</span></span>
>
> <span data-ttu-id="9f761-199">**Sumit Ghosh**, consultant principal chez Neudesic</span><span class="sxs-lookup"><span data-stu-id="9f761-199">**Sumit Ghosh**, Principal Consultant at Neudesic</span></span>

## <a name="copyright"></a><span data-ttu-id="9f761-200">Copyright</span><span class="sxs-lookup"><span data-stu-id="9f761-200">Copyright</span></span>

<span data-ttu-id="9f761-201">PUBLIÉ PAR</span><span class="sxs-lookup"><span data-stu-id="9f761-201">PUBLISHED BY</span></span>

<span data-ttu-id="9f761-202">Division Développeurs Microsoft, équipes produit .NET et Visual Studio</span><span class="sxs-lookup"><span data-stu-id="9f761-202">Microsoft Developer Division, .NET and Visual Studio product teams</span></span>

<span data-ttu-id="9f761-203">Division de Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="9f761-203">A division of Microsoft Corporation</span></span>

<span data-ttu-id="9f761-204">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="9f761-204">One Microsoft Way</span></span>

<span data-ttu-id="9f761-205">Redmond, Washington 98052-6399</span><span class="sxs-lookup"><span data-stu-id="9f761-205">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="9f761-206">Copyright © 2020 par Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="9f761-206">Copyright © 2020 by Microsoft Corporation</span></span>

<span data-ttu-id="9f761-207">Tous droits réservés.</span><span class="sxs-lookup"><span data-stu-id="9f761-207">All rights reserved.</span></span> <span data-ttu-id="9f761-208">Aucune partie du contenu de ce document ne peut être reproduite ou transmise sous quelque forme ou par quelque moyen que ce soit sans l’autorisation écrite de l’éditeur.</span><span class="sxs-lookup"><span data-stu-id="9f761-208">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="9f761-209">Ce document est fourni « en l’état » et exprime les points de vue et les opinions de son auteur.</span><span class="sxs-lookup"><span data-stu-id="9f761-209">This book is provided "as-is" and expresses the author's views and opinions.</span></span> <span data-ttu-id="9f761-210">Les points de vue, les opinions et les informations exprimés dans ce document, notamment l’URL et autres références à des sites web Internet, peuvent faire l’objet de modifications sans préavis.</span><span class="sxs-lookup"><span data-stu-id="9f761-210">The views, opinions and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="9f761-211"> Certains exemples sont fournis à titre indicatif uniquement et sont fictifs.</span><span class="sxs-lookup"><span data-stu-id="9f761-211">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="9f761-212">Toute association ou lien est purement involontaire ou fortuit.</span><span class="sxs-lookup"><span data-stu-id="9f761-212">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="9f761-213">Microsoft et les marques commerciales mentionnées dans la page web « Marques » sur <https://www.microsoft.com> sont des marques du groupe Microsoft.</span><span class="sxs-lookup"><span data-stu-id="9f761-213">Microsoft and the trademarks listed at <https://www.microsoft.com> on the "Trademarks" webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="9f761-214">Mac et macOS sont des marques commerciales d’Apple Inc.</span><span class="sxs-lookup"><span data-stu-id="9f761-214">Mac and macOS are trademarks of Apple Inc.</span></span>

<span data-ttu-id="9f761-215">Le logo de la baleine de l’arrimeur est une marque déposée de Dockr, Inc. utilisée par l’autorisation.</span><span class="sxs-lookup"><span data-stu-id="9f761-215">The Docker whale logo is a registered trademark of Docker, Inc. Used by permission.</span></span>

<span data-ttu-id="9f761-216">Toutes les autres marques et tous les autres logos sont la propriété de leurs propriétaires respectifs.</span><span class="sxs-lookup"><span data-stu-id="9f761-216">All other marks and logos are property of their respective owners.</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="9f761-217">Next</span><span class="sxs-lookup"><span data-stu-id="9f761-217">Next</span></span>](container-docker-introduction/index.md)
