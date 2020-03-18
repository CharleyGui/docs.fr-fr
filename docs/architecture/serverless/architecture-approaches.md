---
title: Approches d’architecture - Applications sans serveur
description: Une introduction aux approches d’architecture pour la construction d’applications d’entreprise basées sur le cloud, des architectures de niveau N aux sans serveur.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 74de96bef48f16ced4adf82855a740aa0afcdf1d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72522895"
---
# <a name="architecture-approaches"></a><span data-ttu-id="c3da0-103">Approches de l’architecture</span><span class="sxs-lookup"><span data-stu-id="c3da0-103">Architecture approaches</span></span>

<span data-ttu-id="c3da0-104">Comprendre les approches existantes pour l’architecture des applications d’entreprise aide à clarifier le rôle joué par serverless.</span><span class="sxs-lookup"><span data-stu-id="c3da0-104">Understanding existing approaches to architecting enterprise apps helps clarify the role played by serverless.</span></span> <span data-ttu-id="c3da0-105">Il existe de nombreuses approches et modèles qui ont évolué au fil des décennies de développement de logiciels, et tous ont leurs propres avantages et inconvénients.</span><span class="sxs-lookup"><span data-stu-id="c3da0-105">There are many approaches and patterns that evolved over decades of software development, and all have their own pros and cons.</span></span> <span data-ttu-id="c3da0-106">Dans de nombreux cas, la solution ultime peut ne pas impliquer de décider d’une seule approche, mais peut intégrer plusieurs approches.</span><span class="sxs-lookup"><span data-stu-id="c3da0-106">In many cases, the ultimate solution may not involve deciding on a single approach but may integrate several approaches.</span></span> <span data-ttu-id="c3da0-107">Les scénarios de migration impliquent souvent le passage d’une approche d’architecture à une autre par une approche hybride.</span><span class="sxs-lookup"><span data-stu-id="c3da0-107">Migration scenarios often involve shifting from one architecture approach to another through a hybrid approach.</span></span>

<span data-ttu-id="c3da0-108">Ce chapitre donne un aperçu des modèles d’architecture logique et physique pour les applications d’entreprise.</span><span class="sxs-lookup"><span data-stu-id="c3da0-108">This chapter provides an overview of both logical and physical architecture patterns for enterprise applications.</span></span>

## <a name="architecture-patterns"></a><span data-ttu-id="c3da0-109">Modèles d’architecture</span><span class="sxs-lookup"><span data-stu-id="c3da0-109">Architecture patterns</span></span>

<span data-ttu-id="c3da0-110">Les applications commerciales modernes suivent une variété de modèles d’architecture.</span><span class="sxs-lookup"><span data-stu-id="c3da0-110">Modern business applications follow a variety of architecture patterns.</span></span> <span data-ttu-id="c3da0-111">Cette section représente une étude des tendances communes.</span><span class="sxs-lookup"><span data-stu-id="c3da0-111">This section represents a survey of common patterns.</span></span> <span data-ttu-id="c3da0-112">Les modèles énumérés ici ne sont pas nécessairement toutes les meilleures pratiques, mais illustrent des approches différentes.</span><span class="sxs-lookup"><span data-stu-id="c3da0-112">The patterns listed here aren't necessarily all best practices, but illustrate different approaches.</span></span>

<span data-ttu-id="c3da0-113">Pour plus d’informations, consultez [le guide d’architecture d’application Azure](https://docs.microsoft.com/azure/architecture/guide/).</span><span class="sxs-lookup"><span data-stu-id="c3da0-113">For more information, see [Azure application architecture guide](https://docs.microsoft.com/azure/architecture/guide/).</span></span>

## <a name="monoliths"></a><span data-ttu-id="c3da0-114">Monolithes</span><span class="sxs-lookup"><span data-stu-id="c3da0-114">Monoliths</span></span>

<span data-ttu-id="c3da0-115">Beaucoup d’applications d’affaires suivent un modèle de monolithe.</span><span class="sxs-lookup"><span data-stu-id="c3da0-115">Many business applications follow a monolith pattern.</span></span> <span data-ttu-id="c3da0-116">Les applications héritées sont souvent mises en œuvre comme monolithes.</span><span class="sxs-lookup"><span data-stu-id="c3da0-116">Legacy applications are often implemented as monoliths.</span></span> <span data-ttu-id="c3da0-117">Dans le modèle de monolithe, toutes les préoccupations d’application sont contenues dans un déploiement unique.</span><span class="sxs-lookup"><span data-stu-id="c3da0-117">In the monolith pattern, all application concerns are contained in a single deployment.</span></span> <span data-ttu-id="c3da0-118">Tout, de l’interface utilisateur aux appels de base de données, est inclus dans la même base de code.</span><span class="sxs-lookup"><span data-stu-id="c3da0-118">Everything from user interface to database calls is included in the same codebase.</span></span>

![Architecture monolithique](./media/monolith-architecture.png)

<span data-ttu-id="c3da0-120">Il y a plusieurs avantages à l’approche monolithe.</span><span class="sxs-lookup"><span data-stu-id="c3da0-120">There are several advantages to the monolith approach.</span></span> <span data-ttu-id="c3da0-121">Il est souvent facile de tirer vers le bas une base de code unique et commencer à travailler.</span><span class="sxs-lookup"><span data-stu-id="c3da0-121">It's often easy to pull down a single code base and start working.</span></span> <span data-ttu-id="c3da0-122">Le temps de montée en puissance peut être moins élevé, et la création d’environnements de test est aussi simple que de fournir une nouvelle copie.</span><span class="sxs-lookup"><span data-stu-id="c3da0-122">Ramp up time may be less, and creating test environments is as simple as providing a new copy.</span></span> <span data-ttu-id="c3da0-123">Le monolithe peut être conçu pour inclure plusieurs composants et applications.</span><span class="sxs-lookup"><span data-stu-id="c3da0-123">The monolith may be designed to include multiple components and applications.</span></span>

<span data-ttu-id="c3da0-124">Malheureusement, le motif monolithe a tendance à se décomposer à l’échelle.</span><span class="sxs-lookup"><span data-stu-id="c3da0-124">Unfortunately, the monolith pattern tends to break down at scale.</span></span> <span data-ttu-id="c3da0-125">Les principaux inconvénients de l’approche monolithique sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="c3da0-125">Major disadvantages of the monolith approach include:</span></span>

- <span data-ttu-id="c3da0-126">Difficile de travailler en parallèle dans la même base de code.</span><span class="sxs-lookup"><span data-stu-id="c3da0-126">Difficult to work in parallel in the same code base.</span></span>
- <span data-ttu-id="c3da0-127">Tout changement, aussi insignifiant soit-il, nécessite le déploiement d’une nouvelle version de l’ensemble de l’application.</span><span class="sxs-lookup"><span data-stu-id="c3da0-127">Any change, no matter how trivial, requires deploying a new version of the entire application.</span></span>
- <span data-ttu-id="c3da0-128">La refactoration pourrait avoir des répercussions sur l’ensemble de l’application.</span><span class="sxs-lookup"><span data-stu-id="c3da0-128">Refactoring potentially impacts the entire application.</span></span>
- <span data-ttu-id="c3da0-129">Souvent, la seule solution à l’échelle est de créer de multiples copies à forte intensité de ressources du monolithe.</span><span class="sxs-lookup"><span data-stu-id="c3da0-129">Often the only solution to scale is to create multiple, resource-intensive copies of the monolith.</span></span>
- <span data-ttu-id="c3da0-130">À mesure que les systèmes se développent ou que d’autres systèmes sont acquis, l’intégration peut être difficile.</span><span class="sxs-lookup"><span data-stu-id="c3da0-130">As systems expand or other systems are acquired, integration can be difficult.</span></span>
- <span data-ttu-id="c3da0-131">Il peut être difficile à tester en raison de la nécessité de configurer l’ensemble du monolithe.</span><span class="sxs-lookup"><span data-stu-id="c3da0-131">It may be difficult to test due to the need to configure the entire monolith.</span></span>
- <span data-ttu-id="c3da0-132">La réutilisation du code est difficile et souvent d’autres applications finissent par avoir leurs propres copies de code.</span><span class="sxs-lookup"><span data-stu-id="c3da0-132">Code reuse is challenging and often other apps end up having their own copies of code.</span></span>

<span data-ttu-id="c3da0-133">Beaucoup d’entreprises se tournent vers le cloud comme une occasion de migrer les applications monolithes et en même temps les refactorisent vers des modèles plus utilisables.</span><span class="sxs-lookup"><span data-stu-id="c3da0-133">Many businesses look to the cloud as an opportunity to migrate monolith applications and at the same time refactor them to more usable patterns.</span></span> <span data-ttu-id="c3da0-134">Il est courant d’éliminer les applications et composants individuels pour leur permettre d’être maintenus, déployés et mis à l’échelle séparément.</span><span class="sxs-lookup"><span data-stu-id="c3da0-134">It's common to break out the individual applications and components to allow them to be maintained, deployed, and scaled separately.</span></span>

## <a name="n-layer-applications"></a><span data-ttu-id="c3da0-135">Applications N-Layer</span><span class="sxs-lookup"><span data-stu-id="c3da0-135">N-Layer applications</span></span>

<span data-ttu-id="c3da0-136">Logique d’application de partition de couche N en couches spécifiques.</span><span class="sxs-lookup"><span data-stu-id="c3da0-136">N-layer application partition application logic into specific layers.</span></span> <span data-ttu-id="c3da0-137">Les couches les plus courantes sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="c3da0-137">The most common layers include:</span></span>

- <span data-ttu-id="c3da0-138">Interface utilisateur</span><span class="sxs-lookup"><span data-stu-id="c3da0-138">User interface</span></span>
- <span data-ttu-id="c3da0-139">Logique métier</span><span class="sxs-lookup"><span data-stu-id="c3da0-139">Business logic</span></span>
- <span data-ttu-id="c3da0-140">Accès aux données</span><span class="sxs-lookup"><span data-stu-id="c3da0-140">Data access</span></span>

<span data-ttu-id="c3da0-141">D’autres couches peuvent inclure middleware, traitement par lots, et API.</span><span class="sxs-lookup"><span data-stu-id="c3da0-141">Other layers may include middleware, batch processing, and API.</span></span> <span data-ttu-id="c3da0-142">Il est important de noter que les couches sont logiques.</span><span class="sxs-lookup"><span data-stu-id="c3da0-142">It's important to note the layers are logical.</span></span> <span data-ttu-id="c3da0-143">Bien qu’ils soient développés isolément, ils peuvent tous être déployés sur la même plate-forme cible.</span><span class="sxs-lookup"><span data-stu-id="c3da0-143">Although they're developed in isolation, they may all be deployed to the same target platform.</span></span>

![Architecture N-Layer](./media/n-layer-architecture.png)

<span data-ttu-id="c3da0-145">L’approche N-Layer présente plusieurs avantages, notamment :</span><span class="sxs-lookup"><span data-stu-id="c3da0-145">There are several advantages to the N-Layer approach, including:</span></span>

- <span data-ttu-id="c3da0-146">La refactoration est isolée jusqu’à une couche.</span><span class="sxs-lookup"><span data-stu-id="c3da0-146">Refactoring is isolated to a layer.</span></span>
- <span data-ttu-id="c3da0-147">Les équipes peuvent construire, tester, déployer et maintenir indépendamment des couches séparées.</span><span class="sxs-lookup"><span data-stu-id="c3da0-147">Teams can independently build, test, deploy, and maintain separate layers.</span></span>
- <span data-ttu-id="c3da0-148">Les couches peuvent être échangées, par exemple la couche de données peut accéder à plusieurs bases de données sans nécessiter de modifications de la couche d’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="c3da0-148">Layers can be swapped out, for example the data layer may access multiple databases without requiring changes to the UI layer.</span></span>

<span data-ttu-id="c3da0-149">Serverless peut être utilisé pour implémenter une ou plusieurs couches.</span><span class="sxs-lookup"><span data-stu-id="c3da0-149">Serverless may be used to implement one or more layers.</span></span>

## <a name="microservices"></a><span data-ttu-id="c3da0-150">Microservices</span><span class="sxs-lookup"><span data-stu-id="c3da0-150">Microservices</span></span>

<span data-ttu-id="c3da0-151">**[Les architectures de microservices](https://docs.microsoft.com/azure/architecture/guide/architecture-styles/microservices)** contiennent des caractéristiques communes qui comprennent :</span><span class="sxs-lookup"><span data-stu-id="c3da0-151">**[Microservices](https://docs.microsoft.com/azure/architecture/guide/architecture-styles/microservices)** architectures contain common characteristics that include:</span></span>

- <span data-ttu-id="c3da0-152">Les applications sont composées de plusieurs petits services.</span><span class="sxs-lookup"><span data-stu-id="c3da0-152">Applications are composed of several small services.</span></span>
- <span data-ttu-id="c3da0-153">Chaque service fonctionne dans son propre processus.</span><span class="sxs-lookup"><span data-stu-id="c3da0-153">Each service runs in its own process.</span></span>
- <span data-ttu-id="c3da0-154">Les services sont alignés sur les domaines d’activité.</span><span class="sxs-lookup"><span data-stu-id="c3da0-154">Services are aligned around business domains.</span></span>
- <span data-ttu-id="c3da0-155">Les services communiquent sur les API légères, généralement en utilisant HTTP comme transport.</span><span class="sxs-lookup"><span data-stu-id="c3da0-155">Services communicate over lightweight APIs, typically using HTTP as the transport.</span></span>
- <span data-ttu-id="c3da0-156">Les services peuvent être déployés et mis à niveau indépendamment.</span><span class="sxs-lookup"><span data-stu-id="c3da0-156">Services can be deployed and upgraded independently.</span></span>
- <span data-ttu-id="c3da0-157">Les services ne dépendent pas d’un seul magasin de données.</span><span class="sxs-lookup"><span data-stu-id="c3da0-157">Services aren't dependent on a single data store.</span></span>
- <span data-ttu-id="c3da0-158">Le système est conçu avec l’échec à l’esprit, et l’application peut encore fonctionner même lorsque certains services échouent.</span><span class="sxs-lookup"><span data-stu-id="c3da0-158">The system is designed with failure in mind, and the app may still run even when certain services fail.</span></span>

<span data-ttu-id="c3da0-159">Les microservices n’ont pas besoin d’être mutuellement exclusifs à d’autres approches d’architecture.</span><span class="sxs-lookup"><span data-stu-id="c3da0-159">Microservices don't have to be mutually exclusive to other architecture approaches.</span></span> <span data-ttu-id="c3da0-160">Par exemple, une architecture N-Tier peut utiliser des microservices pour le niveau intermédiaire.</span><span class="sxs-lookup"><span data-stu-id="c3da0-160">For example, an N-Tier architecture may use microservices for the middle tier.</span></span> <span data-ttu-id="c3da0-161">Il est également possible d’implémenter des microservices de diverses façons, des répertoires virtuels sur les hôtes DE l’IIS aux conteneurs.</span><span class="sxs-lookup"><span data-stu-id="c3da0-161">It's also possible to implement microservices in a variety of ways, from virtual directories on IIS hosts to containers.</span></span> <span data-ttu-id="c3da0-162">Les caractéristiques des microservices les rendent particulièrement idéales pour les implémentations sans serveur.</span><span class="sxs-lookup"><span data-stu-id="c3da0-162">The characteristics of microservices make them especially ideal for serverless implementations.</span></span>

![Architecture de microservices](./media/microservices-architecture.png)

<span data-ttu-id="c3da0-164">Les avantages des architectures de microservices incluent :</span><span class="sxs-lookup"><span data-stu-id="c3da0-164">The pros of microservices architectures include:</span></span>

- <span data-ttu-id="c3da0-165">La refactoration est souvent isolée à un seul service.</span><span class="sxs-lookup"><span data-stu-id="c3da0-165">Refactoring is often isolated to a single service.</span></span>
- <span data-ttu-id="c3da0-166">Les services peuvent être mis à niveau indépendamment les uns des autres.</span><span class="sxs-lookup"><span data-stu-id="c3da0-166">Services can be upgraded independently of each other.</span></span>
- <span data-ttu-id="c3da0-167">La résilience et l’élasticité peuvent être réglées aux exigences des services individuels.</span><span class="sxs-lookup"><span data-stu-id="c3da0-167">Resiliency and elasticity can be tuned to the demands of individual services.</span></span>
- <span data-ttu-id="c3da0-168">Le développement peut se faire en parallèle entre des équipes et des plates-formes disparates.</span><span class="sxs-lookup"><span data-stu-id="c3da0-168">Development can happen in parallel across disparate teams and platforms.</span></span>
- <span data-ttu-id="c3da0-169">Il est plus facile d’écrire des tests complets pour des services isolés.</span><span class="sxs-lookup"><span data-stu-id="c3da0-169">It's easier to write comprehensive tests for isolated services.</span></span>

<span data-ttu-id="c3da0-170">Les microservices présentent leurs propres défis, notamment :</span><span class="sxs-lookup"><span data-stu-id="c3da0-170">Microservices come with their own challenges, including:</span></span>

- <span data-ttu-id="c3da0-171">Déterminer quels services sont disponibles et comment les appeler.</span><span class="sxs-lookup"><span data-stu-id="c3da0-171">Determining what services are available and how to call them.</span></span>
- <span data-ttu-id="c3da0-172">Gérer le cycle de vie des services.</span><span class="sxs-lookup"><span data-stu-id="c3da0-172">Managing the lifecycle of services.</span></span>
- <span data-ttu-id="c3da0-173">Comprendre comment les services s’intègrent dans l’application globale.</span><span class="sxs-lookup"><span data-stu-id="c3da0-173">Understanding how services fit together in the overall application.</span></span>
- <span data-ttu-id="c3da0-174">Test complet du système des appels effectués dans des services disparates.</span><span class="sxs-lookup"><span data-stu-id="c3da0-174">Full system testing of calls made across disparate services.</span></span>

<span data-ttu-id="c3da0-175">En fin de compte, il existe des solutions pour relever tous ces défis, y compris en puisant dans les avantages de serverless qui sont discutés plus tard.</span><span class="sxs-lookup"><span data-stu-id="c3da0-175">Ultimately there are solutions to address all of these challenges, including tapping into the benefits of serverless that are discussed later.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="c3da0-176">[Suivant précédent](index.md)
>[Next](architecture-deployment-approaches.md)</span><span class="sxs-lookup"><span data-stu-id="c3da0-176">[Previous](index.md)
[Next](architecture-deployment-approaches.md)</span></span>
