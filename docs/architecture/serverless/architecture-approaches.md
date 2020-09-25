---
title: Approches de l’architecture-applications sans serveur
description: Présentation des approches d’architecture permettant de créer des applications d’entreprise basées sur le Cloud, des architectures multicouches à des serveurs sans serveur.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 0ab84d1f3425c1fda787756b73fd8315fe6d4231
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91171973"
---
# <a name="architecture-approaches"></a><span data-ttu-id="7babb-103">Approches de l’architecture</span><span class="sxs-lookup"><span data-stu-id="7babb-103">Architecture approaches</span></span>

<span data-ttu-id="7babb-104">La compréhension des approches existantes de l’architecture des applications d’entreprise permet de clarifier le rôle joué par un sans serveur.</span><span class="sxs-lookup"><span data-stu-id="7babb-104">Understanding existing approaches to architecting enterprise apps helps clarify the role played by serverless.</span></span> <span data-ttu-id="7babb-105">Il existe de nombreuses approches et modèles qui ont évolué au fil des décennies du développement de logiciels, et ont tous leurs propres avantages et inconvénients.</span><span class="sxs-lookup"><span data-stu-id="7babb-105">There are many approaches and patterns that evolved over decades of software development, and all have their own pros and cons.</span></span> <span data-ttu-id="7babb-106">Dans de nombreux cas, la solution ultime peut ne pas impliquer une seule approche, mais peut intégrer plusieurs approches.</span><span class="sxs-lookup"><span data-stu-id="7babb-106">In many cases, the ultimate solution may not involve deciding on a single approach but may integrate several approaches.</span></span> <span data-ttu-id="7babb-107">Les scénarios de migration impliquent souvent un passage d’une approche d’architecture à une autre via une approche hybride.</span><span class="sxs-lookup"><span data-stu-id="7babb-107">Migration scenarios often involve shifting from one architecture approach to another through a hybrid approach.</span></span>

<span data-ttu-id="7babb-108">Ce chapitre fournit une vue d’ensemble des modèles d’architecture logique et physique pour les applications d’entreprise.</span><span class="sxs-lookup"><span data-stu-id="7babb-108">This chapter provides an overview of both logical and physical architecture patterns for enterprise applications.</span></span>

## <a name="architecture-patterns"></a><span data-ttu-id="7babb-109">Modèles d’architecture</span><span class="sxs-lookup"><span data-stu-id="7babb-109">Architecture patterns</span></span>

<span data-ttu-id="7babb-110">Les applications métier modernes suivent un large éventail de modèles d’architecture.</span><span class="sxs-lookup"><span data-stu-id="7babb-110">Modern business applications follow a variety of architecture patterns.</span></span> <span data-ttu-id="7babb-111">Cette section représente une étude des modèles courants.</span><span class="sxs-lookup"><span data-stu-id="7babb-111">This section represents a survey of common patterns.</span></span> <span data-ttu-id="7babb-112">Les modèles répertoriés ici ne sont pas nécessairement les meilleures pratiques, mais illustrent des approches différentes.</span><span class="sxs-lookup"><span data-stu-id="7babb-112">The patterns listed here aren't necessarily all best practices, but illustrate different approaches.</span></span>

<span data-ttu-id="7babb-113">Pour plus d’informations, consultez Guide de l' [architecture des applications Azure](/azure/architecture/guide/).</span><span class="sxs-lookup"><span data-stu-id="7babb-113">For more information, see [Azure application architecture guide](/azure/architecture/guide/).</span></span>

## <a name="monoliths"></a><span data-ttu-id="7babb-114">Monolithes</span><span class="sxs-lookup"><span data-stu-id="7babb-114">Monoliths</span></span>

<span data-ttu-id="7babb-115">De nombreuses applications professionnelles suivent un modèle monolithique.</span><span class="sxs-lookup"><span data-stu-id="7babb-115">Many business applications follow a monolith pattern.</span></span> <span data-ttu-id="7babb-116">Les applications héritées sont souvent implémentées en tant que monolithiques.</span><span class="sxs-lookup"><span data-stu-id="7babb-116">Legacy applications are often implemented as monoliths.</span></span> <span data-ttu-id="7babb-117">Dans le modèle monolithique, tous les problèmes d’application sont contenus dans un seul déploiement.</span><span class="sxs-lookup"><span data-stu-id="7babb-117">In the monolith pattern, all application concerns are contained in a single deployment.</span></span> <span data-ttu-id="7babb-118">Tout, de l’interface utilisateur aux appels de base de données, est inclus dans la même base de code.</span><span class="sxs-lookup"><span data-stu-id="7babb-118">Everything from user interface to database calls is included in the same codebase.</span></span>

![Architecture monolithique](./media/monolith-architecture.png)

<span data-ttu-id="7babb-120">L’approche monolithique présente plusieurs avantages.</span><span class="sxs-lookup"><span data-stu-id="7babb-120">There are several advantages to the monolith approach.</span></span> <span data-ttu-id="7babb-121">Il est souvent facile d’extraire une base de code unique et de commencer à travailler.</span><span class="sxs-lookup"><span data-stu-id="7babb-121">It's often easy to pull down a single code base and start working.</span></span> <span data-ttu-id="7babb-122">Le temps d’exécution de la rampe peut être inférieur, et la création d’environnements de test est aussi simple que la création d’une nouvelle copie.</span><span class="sxs-lookup"><span data-stu-id="7babb-122">Ramp up time may be less, and creating test environments is as simple as providing a new copy.</span></span> <span data-ttu-id="7babb-123">Le monolithe peut être conçu pour inclure plusieurs composants et applications.</span><span class="sxs-lookup"><span data-stu-id="7babb-123">The monolith may be designed to include multiple components and applications.</span></span>

<span data-ttu-id="7babb-124">Malheureusement, le modèle monolithique a tendance à s’arrêter à l’échelle.</span><span class="sxs-lookup"><span data-stu-id="7babb-124">Unfortunately, the monolith pattern tends to break down at scale.</span></span> <span data-ttu-id="7babb-125">Les inconvénients majeurs de l’approche monolithique sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="7babb-125">Major disadvantages of the monolith approach include:</span></span>

- <span data-ttu-id="7babb-126">Il est difficile de travailler en parallèle dans la même base de code.</span><span class="sxs-lookup"><span data-stu-id="7babb-126">Difficult to work in parallel in the same code base.</span></span>
- <span data-ttu-id="7babb-127">Toute modification, quel que soit son degré de simplicité, requiert le déploiement d’une nouvelle version de l’application entière.</span><span class="sxs-lookup"><span data-stu-id="7babb-127">Any change, no matter how trivial, requires deploying a new version of the entire application.</span></span>
- <span data-ttu-id="7babb-128">La refactorisation peut avoir un impact sur l’ensemble de l’application.</span><span class="sxs-lookup"><span data-stu-id="7babb-128">Refactoring potentially impacts the entire application.</span></span>
- <span data-ttu-id="7babb-129">Souvent, la seule solution à mettre à l’échelle consiste à créer plusieurs copies gourmandes en ressources du monolithique.</span><span class="sxs-lookup"><span data-stu-id="7babb-129">Often the only solution to scale is to create multiple, resource-intensive copies of the monolith.</span></span>
- <span data-ttu-id="7babb-130">À mesure que les systèmes sont développés ou que d’autres systèmes sont acquis, l’intégration peut être difficile.</span><span class="sxs-lookup"><span data-stu-id="7babb-130">As systems expand or other systems are acquired, integration can be difficult.</span></span>
- <span data-ttu-id="7babb-131">Il peut être difficile de tester en raison de la nécessité de configurer l’ensemble du monolithique.</span><span class="sxs-lookup"><span data-stu-id="7babb-131">It may be difficult to test due to the need to configure the entire monolith.</span></span>
- <span data-ttu-id="7babb-132">La réutilisation du code est délicate et souvent d’autres applications finissent par avoir leurs propres copies du code.</span><span class="sxs-lookup"><span data-stu-id="7babb-132">Code reuse is challenging and often other apps end up having their own copies of code.</span></span>

<span data-ttu-id="7babb-133">De nombreuses entreprises considèrent le cloud comme une opportunité de migrer des applications monolithiques et de les Refactoriser à des modèles plus utilisables.</span><span class="sxs-lookup"><span data-stu-id="7babb-133">Many businesses look to the cloud as an opportunity to migrate monolith applications and at the same time refactor them to more usable patterns.</span></span> <span data-ttu-id="7babb-134">Il est courant de décomposer les applications et les composants individuels pour leur permettre d’être gérés, déployés et mis à l’échelle séparément.</span><span class="sxs-lookup"><span data-stu-id="7babb-134">It's common to break out the individual applications and components to allow them to be maintained, deployed, and scaled separately.</span></span>

## <a name="n-layer-applications"></a><span data-ttu-id="7babb-135">Applications multicouches</span><span class="sxs-lookup"><span data-stu-id="7babb-135">N-Layer applications</span></span>

<span data-ttu-id="7babb-136">Logique d’application de partition d’application à N couches dans des couches spécifiques.</span><span class="sxs-lookup"><span data-stu-id="7babb-136">N-layer application partition application logic into specific layers.</span></span> <span data-ttu-id="7babb-137">Les couches les plus courantes sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="7babb-137">The most common layers include:</span></span>

- <span data-ttu-id="7babb-138">Interface utilisateur</span><span class="sxs-lookup"><span data-stu-id="7babb-138">User interface</span></span>
- <span data-ttu-id="7babb-139">Logique métier</span><span class="sxs-lookup"><span data-stu-id="7babb-139">Business logic</span></span>
- <span data-ttu-id="7babb-140">Accès aux données</span><span class="sxs-lookup"><span data-stu-id="7babb-140">Data access</span></span>

<span data-ttu-id="7babb-141">D’autres couches peuvent inclure des intergiciels (middleware), le traitement par lots et l’API.</span><span class="sxs-lookup"><span data-stu-id="7babb-141">Other layers may include middleware, batch processing, and API.</span></span> <span data-ttu-id="7babb-142">Il est important de noter que les couches sont logiques.</span><span class="sxs-lookup"><span data-stu-id="7babb-142">It's important to note the layers are logical.</span></span> <span data-ttu-id="7babb-143">Bien qu’elles soient développées de manière isolée, elles peuvent toutes être déployées sur la même plateforme cible.</span><span class="sxs-lookup"><span data-stu-id="7babb-143">Although they're developed in isolation, they may all be deployed to the same target platform.</span></span>

![Architecture à N couches](./media/n-layer-architecture.png)

<span data-ttu-id="7babb-145">L’approche multicouche présente plusieurs avantages, notamment :</span><span class="sxs-lookup"><span data-stu-id="7babb-145">There are several advantages to the N-Layer approach, including:</span></span>

- <span data-ttu-id="7babb-146">La refactorisation est isolée dans une couche.</span><span class="sxs-lookup"><span data-stu-id="7babb-146">Refactoring is isolated to a layer.</span></span>
- <span data-ttu-id="7babb-147">Les équipes peuvent créer, tester, déployer et gérer indépendamment des couches distinctes.</span><span class="sxs-lookup"><span data-stu-id="7babb-147">Teams can independently build, test, deploy, and maintain separate layers.</span></span>
- <span data-ttu-id="7babb-148">Les couches peuvent être échangées, par exemple la couche de données peut accéder à plusieurs bases de données sans nécessiter de modifications de la couche d’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="7babb-148">Layers can be swapped out, for example the data layer may access multiple databases without requiring changes to the UI layer.</span></span>

<span data-ttu-id="7babb-149">Sans serveur peut être utilisé pour implémenter une ou plusieurs couches.</span><span class="sxs-lookup"><span data-stu-id="7babb-149">Serverless may be used to implement one or more layers.</span></span>

## <a name="microservices"></a><span data-ttu-id="7babb-150">Microservices</span><span class="sxs-lookup"><span data-stu-id="7babb-150">Microservices</span></span>

<span data-ttu-id="7babb-151">Les architectures de **[microservices](/azure/architecture/guide/architecture-styles/microservices)** contiennent des caractéristiques communes qui incluent :</span><span class="sxs-lookup"><span data-stu-id="7babb-151">**[Microservices](/azure/architecture/guide/architecture-styles/microservices)** architectures contain common characteristics that include:</span></span>

- <span data-ttu-id="7babb-152">Les applications sont composées de plusieurs petits services.</span><span class="sxs-lookup"><span data-stu-id="7babb-152">Applications are composed of several small services.</span></span>
- <span data-ttu-id="7babb-153">Chaque service s’exécute dans son propre processus.</span><span class="sxs-lookup"><span data-stu-id="7babb-153">Each service runs in its own process.</span></span>
- <span data-ttu-id="7babb-154">Les services sont alignés autour des domaines d’entreprise.</span><span class="sxs-lookup"><span data-stu-id="7babb-154">Services are aligned around business domains.</span></span>
- <span data-ttu-id="7babb-155">Les services communiquent via des API légères, en utilisant généralement HTTP comme transport.</span><span class="sxs-lookup"><span data-stu-id="7babb-155">Services communicate over lightweight APIs, typically using HTTP as the transport.</span></span>
- <span data-ttu-id="7babb-156">Les services peuvent être déployés et mis à niveau indépendamment.</span><span class="sxs-lookup"><span data-stu-id="7babb-156">Services can be deployed and upgraded independently.</span></span>
- <span data-ttu-id="7babb-157">Les services ne sont pas dépendants d’un seul magasin de données.</span><span class="sxs-lookup"><span data-stu-id="7babb-157">Services aren't dependent on a single data store.</span></span>
- <span data-ttu-id="7babb-158">Le système est conçu en cas d’échec, et l’application peut toujours s’exécuter même lorsque certains services échouent.</span><span class="sxs-lookup"><span data-stu-id="7babb-158">The system is designed with failure in mind, and the app may still run even when certain services fail.</span></span>

<span data-ttu-id="7babb-159">Il n’est pas nécessaire que les microservices soient mutuellement exclusifs à d’autres approches d’architecture.</span><span class="sxs-lookup"><span data-stu-id="7babb-159">Microservices don't have to be mutually exclusive to other architecture approaches.</span></span> <span data-ttu-id="7babb-160">Par exemple, une architecture multiniveau peut utiliser des microservices pour la couche intermédiaire.</span><span class="sxs-lookup"><span data-stu-id="7babb-160">For example, an N-Tier architecture may use microservices for the middle tier.</span></span> <span data-ttu-id="7babb-161">Il est également possible d’implémenter des microservices de différentes façons, des répertoires virtuels sur les hôtes IIS aux conteneurs.</span><span class="sxs-lookup"><span data-stu-id="7babb-161">It's also possible to implement microservices in a variety of ways, from virtual directories on IIS hosts to containers.</span></span> <span data-ttu-id="7babb-162">Les caractéristiques des microservices les rendent particulièrement idéales pour les implémentations sans serveur.</span><span class="sxs-lookup"><span data-stu-id="7babb-162">The characteristics of microservices make them especially ideal for serverless implementations.</span></span>

![Architecture de microservices](./media/microservices-architecture.png)

<span data-ttu-id="7babb-164">Les avantages des architectures de microservices sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="7babb-164">The pros of microservices architectures include:</span></span>

- <span data-ttu-id="7babb-165">La refactorisation est souvent isolée dans un service unique.</span><span class="sxs-lookup"><span data-stu-id="7babb-165">Refactoring is often isolated to a single service.</span></span>
- <span data-ttu-id="7babb-166">Les services peuvent être mis à niveau indépendamment l’un de l’autre.</span><span class="sxs-lookup"><span data-stu-id="7babb-166">Services can be upgraded independently of each other.</span></span>
- <span data-ttu-id="7babb-167">La résilience et l’élasticité peuvent être réglées sur les demandes des services individuels.</span><span class="sxs-lookup"><span data-stu-id="7babb-167">Resiliency and elasticity can be tuned to the demands of individual services.</span></span>
- <span data-ttu-id="7babb-168">Le développement peut se faire en parallèle sur des plateformes et des équipes disparates.</span><span class="sxs-lookup"><span data-stu-id="7babb-168">Development can happen in parallel across disparate teams and platforms.</span></span>
- <span data-ttu-id="7babb-169">Il est plus facile d’écrire des tests complets pour les services isolés.</span><span class="sxs-lookup"><span data-stu-id="7babb-169">It's easier to write comprehensive tests for isolated services.</span></span>

<span data-ttu-id="7babb-170">Les microservices sont accompagnés de leurs propres défis, notamment :</span><span class="sxs-lookup"><span data-stu-id="7babb-170">Microservices come with their own challenges, including:</span></span>

- <span data-ttu-id="7babb-171">Déterminer quels services sont disponibles et comment les appeler.</span><span class="sxs-lookup"><span data-stu-id="7babb-171">Determining what services are available and how to call them.</span></span>
- <span data-ttu-id="7babb-172">Gestion du cycle de vie des services.</span><span class="sxs-lookup"><span data-stu-id="7babb-172">Managing the lifecycle of services.</span></span>
- <span data-ttu-id="7babb-173">Comprendre comment les services s’intègrent à l’ensemble de l’application.</span><span class="sxs-lookup"><span data-stu-id="7babb-173">Understanding how services fit together in the overall application.</span></span>
- <span data-ttu-id="7babb-174">Test complet du système des appels effectués sur des services disparates.</span><span class="sxs-lookup"><span data-stu-id="7babb-174">Full system testing of calls made across disparate services.</span></span>

<span data-ttu-id="7babb-175">En fin de compte, il existe des solutions pour répondre à tous ces défis, y compris pour tirer parti des avantages des services sans serveur décrits plus loin.</span><span class="sxs-lookup"><span data-stu-id="7babb-175">Ultimately there are solutions to address all of these challenges, including tapping into the benefits of serverless that are discussed later.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="7babb-176">[Précédent](index.md) 
> [Suivant](architecture-deployment-approaches.md)</span><span class="sxs-lookup"><span data-stu-id="7babb-176">[Previous](index.md)
[Next](architecture-deployment-approaches.md)</span></span>
