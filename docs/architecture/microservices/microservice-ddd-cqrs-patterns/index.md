---
title: Lutte contre la complexité d’entreprise dans un microservice disposant des modèles DDD et CQRS
description: Architecture des Microservices .NET pour les applications .NET en conteneur | Comprendre comment gérer des scénarios professionnels complexes en appliquant modèles DDD et CQRS
ms.date: 10/08/2018
ms.openlocfilehash: 852073548a66fbe568fc5c2531342db944d5a8b0
ms.sourcegitcommit: ee5b798427f81237a3c23d1fd81fff7fdc21e8d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/28/2020
ms.locfileid: "84144641"
---
# <a name="tackle-business-complexity-in-a-microservice-with-ddd-and-cqrs-patterns"></a><span data-ttu-id="03cec-103">Lutter contre la complexité d’entreprise dans un microservice disposant des modèles DDD et CQRS</span><span class="sxs-lookup"><span data-stu-id="03cec-103">Tackle Business Complexity in a Microservice with DDD and CQRS Patterns</span></span>

<span data-ttu-id="03cec-104">*Concevoir un modèle de domaine pour chaque microservice ou contexte délimité qui reflète la compréhension du domaine d’entreprise.*</span><span class="sxs-lookup"><span data-stu-id="03cec-104">*Design a domain model for each microservice or Bounded Context that reflects understanding of the business domain.*</span></span>

<span data-ttu-id="03cec-105">Cette section s’intéresse à des microservices plus avancés que vous implémentez quand vous avez besoin de vous attaquer à des sous-systèmes ou microservices complexes relevant de la connaissance d’experts du domaine avec des règles d’entreprise en constante évolution.</span><span class="sxs-lookup"><span data-stu-id="03cec-105">This section focuses on more advanced microservices that you implement when you need to tackle complex subsystems, or microservices derived from the knowledge of domain experts with ever-changing business rules.</span></span> <span data-ttu-id="03cec-106">Les modèles d’architecture utilisés dans cette section sont basés sur les approches de la conception pilotée par domaine (DDD, Domain-Driven Design) et de la séparation des responsabilités dans les commandes et requêtes (CQRS, Command and Query Responsibility Segregation), comme illustré dans la figure 7-1.</span><span class="sxs-lookup"><span data-stu-id="03cec-106">The architecture patterns used in this section are based on domain-driven design (DDD) and Command and Query Responsibility Segregation (CQRS) approaches, as illustrated in Figure 7-1.</span></span>

:::image type="complex" source="./media/index/internal-versus-external-architecture.png" alt-text="Diagramme comparant les modèles d’architecture externes et internes.":::
<span data-ttu-id="03cec-108">Différence entre une architecture externe (modèles de microservices, passerelles d’API, communications résilientes, pub/sub, etc.) et une architecture interne (modèles pilotés par les données/CRUD, DDD, injection de dépendances, multiples bibliothèques, etc.)</span><span class="sxs-lookup"><span data-stu-id="03cec-108">Difference between external architecture: microservice patterns, API gateways, resilient communications, pub/sub, etc., and internal architecture: data driven/CRUD, DDD patterns, dependency injection, multiple libraries, etc.</span></span>
:::image-end:::

<span data-ttu-id="03cec-109">**Figure 7-1**.</span><span class="sxs-lookup"><span data-stu-id="03cec-109">**Figure 7-1**.</span></span> <span data-ttu-id="03cec-110">Modèles d’architecture de microservice externe ou interne pour chaque microservice</span><span class="sxs-lookup"><span data-stu-id="03cec-110">External microservice architecture versus internal architecture patterns for each microservice</span></span>

<span data-ttu-id="03cec-111">Toutefois, la plupart des techniques liées aux microservices pilotés par des données, comme la manière d’implémenter un service API Web ASP.NET Core ou d’exposer des métadonnées Swagger avec Swashbuckle ou NSwag, sont également applicables aux microservices plus avancés implémentés en interne avec des modèles DDD.</span><span class="sxs-lookup"><span data-stu-id="03cec-111">However, most of the techniques for data driven microservices, such as how to implement an ASP.NET Core Web API service or how to expose Swagger metadata with Swashbuckle or NSwag, are also applicable to the more advanced microservices implemented internally with DDD patterns.</span></span> <span data-ttu-id="03cec-112">Cette section est une extension des sections précédentes, car la plupart des pratiques expliquées précédemment s’appliquent également ici ou à tout type de microservice.</span><span class="sxs-lookup"><span data-stu-id="03cec-112">This section is an extension of the previous sections, because most of the practices explained earlier also apply here or for any kind of microservice.</span></span>

<span data-ttu-id="03cec-113">Tout d’abord, cette section fournit des détails sur les modèles CQRS simplifiés utilisés dans l’application de référence eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="03cec-113">This section first provides details on the simplified CQRS patterns used in the eShopOnContainers reference application.</span></span> <span data-ttu-id="03cec-114">Ensuite, vous obtiendrez une vue d’ensemble des techniques DDD qui vous permettent de rechercher des modèles courants que vous pouvez réutiliser dans vos applications.</span><span class="sxs-lookup"><span data-stu-id="03cec-114">Later, you will get an overview of the DDD techniques that enable you to find common patterns that you can reuse in your applications.</span></span>

<span data-ttu-id="03cec-115">DDD est un large sujet avec un ensemble complet de ressources d’apprentissage.</span><span class="sxs-lookup"><span data-stu-id="03cec-115">DDD is a large topic with a rich set of resources for learning.</span></span> <span data-ttu-id="03cec-116">Vous pouvez commencer avec des ouvrages comme [Domain-Driven Design](https://domainlanguage.com/ddd/) d’Eric Evans et d’autres documents de Vaughn Vernon, Jimmy Nilsson, Greg Young, Udi Dahan, Jimmy Bogard et de nombreux autres experts en DDD/CQRS.</span><span class="sxs-lookup"><span data-stu-id="03cec-116">You can start with books like [Domain-Driven Design](https://domainlanguage.com/ddd/) by Eric Evans and additional materials from Vaughn Vernon, Jimmy Nilsson, Greg Young, Udi Dahan, Jimmy Bogard, and many other DDD/CQRS experts.</span></span> <span data-ttu-id="03cec-117">Mais avant tout, vous devez essayer d’apprendre à appliquer des techniques DDD à partir des conversations, tableaux blancs et sessions de modélisation que vous tenez avec des experts de votre domaine d’entreprise concret.</span><span class="sxs-lookup"><span data-stu-id="03cec-117">But most of all you need to try to learn how to apply DDD techniques from the conversations, whiteboarding, and domain modeling sessions with the experts in your concrete business domain.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="03cec-118">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="03cec-118">Additional resources</span></span>

##### <a name="ddd-domain-driven-design"></a><span data-ttu-id="03cec-119">DDD (Domain-Driven Design)</span><span class="sxs-lookup"><span data-stu-id="03cec-119">DDD (Domain-Driven Design)</span></span>

- <span data-ttu-id="03cec-120">**Eric Evans. Langue du domaine** </span><span class="sxs-lookup"><span data-stu-id="03cec-120">**Eric Evans. Domain Language** </span></span>\
  <https://domainlanguage.com/>

- <span data-ttu-id="03cec-121">**Martin Fowler. Conception pilotée par le domaine** </span><span class="sxs-lookup"><span data-stu-id="03cec-121">**Martin Fowler. Domain-Driven Design** </span></span>\
  <https://martinfowler.com/tags/domain%20driven%20design.html>

- <span data-ttu-id="03cec-122">**Jimmy bogard. Renforcement de votre domaine : une introduction** </span><span class="sxs-lookup"><span data-stu-id="03cec-122">**Jimmy Bogard. Strengthening your domain: a primer** </span></span>\
  <https://lostechies.com/jimmybogard/2010/02/04/strengthening-your-domain-a-primer/>

##### <a name="ddd-books"></a><span data-ttu-id="03cec-123">Ouvrages DDD</span><span class="sxs-lookup"><span data-stu-id="03cec-123">DDD books</span></span>

- <span data-ttu-id="03cec-124">**Eric Evans. Conception pilotée par domaine : la complexité du cœur du logiciel** </span><span class="sxs-lookup"><span data-stu-id="03cec-124">**Eric Evans. Domain-Driven Design: Tackling Complexity in the Heart of Software** </span></span>\
  <https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/>

- <span data-ttu-id="03cec-125">**Eric Evans. Référence de conception pilotée par domaine : définitions et résumés de modèles** </span><span class="sxs-lookup"><span data-stu-id="03cec-125">**Eric Evans. Domain-Driven Design Reference: Definitions and Pattern Summaries** </span></span>\
  <https://www.amazon.com/Domain-Driven-Design-Reference-Definitions-2014-09-22/dp/B01N8YB4ZO/>

- <span data-ttu-id="03cec-126">**Vaughn Vernon. Implémentation de la conception pilotée par le domaine** </span><span class="sxs-lookup"><span data-stu-id="03cec-126">**Vaughn Vernon. Implementing Domain-Driven Design** </span></span>\
  <https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/>

- <span data-ttu-id="03cec-127">**Vaughn Vernon. Conception pilotée par le domaine distillée** </span><span class="sxs-lookup"><span data-stu-id="03cec-127">**Vaughn Vernon. Domain-Driven Design Distilled** </span></span>\
  <https://www.amazon.com/Domain-Driven-Design-Distilled-Vaughn-Vernon/dp/0134434420/>

- <span data-ttu-id="03cec-128">**Jimmy Nilsson. Application de la conception et des modèles pilotés par domaine** </span><span class="sxs-lookup"><span data-stu-id="03cec-128">**Jimmy Nilsson. Applying Domain-Driven Design and Patterns** </span></span>\
  <https://www.amazon.com/Applying-Domain-Driven-Design-Patterns-Examples/dp/0321268202/>

- <span data-ttu-id="03cec-129">**Cesar de la Torre. Guide d’architecture orientée domaine N à couches avec .NET** </span><span class="sxs-lookup"><span data-stu-id="03cec-129">**Cesar de la Torre. N-Layered Domain-Oriented Architecture Guide with .NET** </span></span>\
  <https://www.amazon.com/N-Layered-Domain-Oriented-Architecture-Guide-NET/dp/8493903612/>

- <span data-ttu-id="03cec-130">**Avram et Floyd Marinescu. Conception pilotée par domaine rapide** </span><span class="sxs-lookup"><span data-stu-id="03cec-130">**Abel Avram and Floyd Marinescu. Domain-Driven Design Quickly** </span></span>\
  <https://www.amazon.com/Domain-Driven-Design-Quickly-Abel-Avram/dp/1411609255/>

- <span data-ttu-id="03cec-131">**Scott Millett, ajustement Nick-modèles, principes et pratiques de conception pilotée par le domaine** </span><span class="sxs-lookup"><span data-stu-id="03cec-131">**Scott Millett, Nick Tune - Patterns, Principles, and Practices of Domain-Driven Design** </span></span>\
  <https://www.wiley.com/Patterns%2C+Principles%2C+and+Practices+of+Domain+Driven+Design-p-9781118714706>

##### <a name="ddd-training"></a><span data-ttu-id="03cec-132">Formation DDD</span><span class="sxs-lookup"><span data-stu-id="03cec-132">DDD training</span></span>

- <span data-ttu-id="03cec-133">**Julie Lerman et Steve Smith. Notions de base de la conception pilotée par domaine** </span><span class="sxs-lookup"><span data-stu-id="03cec-133">**Julie Lerman and Steve Smith. Domain-Driven Design Fundamentals** </span></span>\
  <https://bit.ly/PS-DDD>

>[!div class="step-by-step"]
><span data-ttu-id="03cec-134">[Précédent](../multi-container-microservice-net-applications/implement-api-gateways-with-ocelot.md) 
> [Suivant](apply-simplified-microservice-cqrs-ddd-patterns.md)</span><span class="sxs-lookup"><span data-stu-id="03cec-134">[Previous](../multi-container-microservice-net-applications/implement-api-gateways-with-ocelot.md)
[Next](apply-simplified-microservice-cqrs-ddd-patterns.md)</span></span>
