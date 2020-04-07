---
title: Elasticsearch dans les applications cloud-native
description: Découvrez l’ajout de capacités de recherche élastique aux applications cloud-natives.
author: robvet
ms.date: 03/02/2020
ms.openlocfilehash: da6b9402cf266f5a298b05cf837805b2377bc75a
ms.sourcegitcommit: f87ad41b8e62622da126aa928f7640108c4eff98
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/07/2020
ms.locfileid: "80805565"
---
# <a name="elasticsearch-in-a-cloud-native-app"></a><span data-ttu-id="39f96-103">Elasticsearch dans une application cloud-native</span><span class="sxs-lookup"><span data-stu-id="39f96-103">Elasticsearch in a cloud-native app</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="39f96-104">Elasticsearch est un système de recherche et d’analyse distribué qui permet des capacités de recherche complexes à travers divers types de données.</span><span class="sxs-lookup"><span data-stu-id="39f96-104">Elasticsearch is a distributed search and analytics system that enables complex search capabilities across diverse types of data.</span></span> <span data-ttu-id="39f96-105">Il est open source et très populaire.</span><span class="sxs-lookup"><span data-stu-id="39f96-105">It's open source and widely popular.</span></span> <span data-ttu-id="39f96-106">Considérez comment les entreprises suivantes intègrent Elasticsearch dans leur application :</span><span class="sxs-lookup"><span data-stu-id="39f96-106">Consider how the following companies integrate Elasticsearch into their application:</span></span>

- <span data-ttu-id="39f96-107">[Wikipédia](https://blog.wikimedia.org/2014/01/06/wikimedia-moving-to-elasticsearch/) pour le texte intégral et la recherche incrémentale (recherche que vous tapez).</span><span class="sxs-lookup"><span data-stu-id="39f96-107">[Wikipedia](https://blog.wikimedia.org/2014/01/06/wikimedia-moving-to-elasticsearch/) for full-text and incremental (search as you type) searching.</span></span>
- <span data-ttu-id="39f96-108">[GitHub](https://www.elastic.co/customers/github) pour indexer et exposer plus de 8 millions de dépôts de code.</span><span class="sxs-lookup"><span data-stu-id="39f96-108">[GitHub](https://www.elastic.co/customers/github) to index and expose over 8 million code repositories.</span></span>  
- <span data-ttu-id="39f96-109">[Docker](https://www.elastic.co/customers/docker) pour rendre sa bibliothèque de conteneurs détectable.</span><span class="sxs-lookup"><span data-stu-id="39f96-109">[Docker](https://www.elastic.co/customers/docker) for making its container library discoverable.</span></span>

<span data-ttu-id="39f96-110">Elasticsearch est construit sur le moteur de recherche à texte complet [Apache Lucene.](https://lucene.apache.org/core/)</span><span class="sxs-lookup"><span data-stu-id="39f96-110">Elasticsearch is built on top of the [Apache Lucene](https://lucene.apache.org/core/) full-text search engine.</span></span> <span data-ttu-id="39f96-111">Lucene fournit l’indexation et la requête de documents haute performance.</span><span class="sxs-lookup"><span data-stu-id="39f96-111">Lucene provides high-performance document indexing and querying.</span></span> <span data-ttu-id="39f96-112">Il indexe les données avec un système d’indexation inversé - au lieu de cartographier les pages à des mots clés, il cartographie les mots clés à des pages comme un glossaire à la fin d’un livre.</span><span class="sxs-lookup"><span data-stu-id="39f96-112">It indexes data with an inverted indexing scheme – instead of mapping pages to keywords, it maps keywords to pages just like a glossary at the end of a book.</span></span> <span data-ttu-id="39f96-113">Lucene a de puissantes capacités de syntaxe de requête et peut interroger les données en :</span><span class="sxs-lookup"><span data-stu-id="39f96-113">Lucene has powerful query syntax capabilities and can query data by:</span></span>

- <span data-ttu-id="39f96-114">Terme (un mot complet)</span><span class="sxs-lookup"><span data-stu-id="39f96-114">Term (a full word)</span></span>
- <span data-ttu-id="39f96-115">Préfixe (commence-avec mot)</span><span class="sxs-lookup"><span data-stu-id="39f96-115">Prefix (starts-with word)</span></span>
- <span data-ttu-id="39f96-116">Wildcard (à\*l’aide de filtres " ou " ? "</span><span class="sxs-lookup"><span data-stu-id="39f96-116">Wildcard (using "\*" or "?" filters)</span></span>
- <span data-ttu-id="39f96-117">Phrase (une séquence de texte dans un document)</span><span class="sxs-lookup"><span data-stu-id="39f96-117">Phrase (a sequence of text in a document)</span></span>
- <span data-ttu-id="39f96-118">Valeur Boolean (recherches complexes combinant requêtes)</span><span class="sxs-lookup"><span data-stu-id="39f96-118">Boolean value (complex searches combining queries)</span></span>

<span data-ttu-id="39f96-119">Alors que Lucene fournit une plomberie de bas niveau pour la recherche, Elasticsearch fournit le serveur qui se trouve au-dessus de Lucene.</span><span class="sxs-lookup"><span data-stu-id="39f96-119">While Lucene provides low-level plumbing for searching, Elasticsearch provides the server that sits on top of Lucene.</span></span> <span data-ttu-id="39f96-120">Elasticsearch ajoute des fonctionnalités de plus haut niveau pour simplifier le travail Lucene, y compris une API RESTful pour accéder à la fonctionnalité d’indexation et de recherche de Lucene.</span><span class="sxs-lookup"><span data-stu-id="39f96-120">Elasticsearch adds higher-level functionality to simplify working Lucene, including a RESTful API to access Lucene's indexing and searching functionality.</span></span> <span data-ttu-id="39f96-121">Il fournit également une infrastructure distribuée capable d’évolutivité massive, de tolérance aux défauts et d’une grande disponibilité.</span><span class="sxs-lookup"><span data-stu-id="39f96-121">It also provides a distributed infrastructure capable of massive scalability, fault tolerance, and high availability.</span></span>

<span data-ttu-id="39f96-122">Pour les applications cloud-natives plus grandes avec des besoins de recherche complexes, Elasticsearch est disponible en tant que service géré en Azure.</span><span class="sxs-lookup"><span data-stu-id="39f96-122">For larger cloud-native applications with complex search requirements, Elasticsearch is available as managed service in Azure.</span></span> <span data-ttu-id="39f96-123">Le Microsoft Azure Marketplace propose des modèles préconfigurés que les développeurs peuvent utiliser pour déployer un cluster Elasticsearch sur Azure.</span><span class="sxs-lookup"><span data-stu-id="39f96-123">The Microsoft Azure Marketplace features preconfigured templates which developers can use to deploy an Elasticsearch cluster on Azure.</span></span>

<span data-ttu-id="39f96-124">Depuis Microsoft Azure Marketplace, les développeurs peuvent utiliser des modèles préconfigurés conçus pour déployer rapidement un cluster Elasticsearch sur Azure.</span><span class="sxs-lookup"><span data-stu-id="39f96-124">From the Microsoft Azure Marketplace, developers can use preconfigured templates built to quickly deploy an Elasticsearch cluster on Azure.</span></span> <span data-ttu-id="39f96-125">Grâce à l’offre gérée par Azure, vous pouvez déployer jusqu’à 50 nœuds de données, 20 nœuds de coordination et trois nœuds maîtres dédiés.</span><span class="sxs-lookup"><span data-stu-id="39f96-125">Using the Azure-managed offering, you can deploy up to 50 data nodes, 20 coordinating nodes, and three dedicated master nodes.</span></span>

## <a name="summary"></a><span data-ttu-id="39f96-126">Résumé</span><span class="sxs-lookup"><span data-stu-id="39f96-126">Summary</span></span>

<span data-ttu-id="39f96-127">Ce chapitre a présenté un regard détaillé sur les données des systèmes cloud-autochtones.</span><span class="sxs-lookup"><span data-stu-id="39f96-127">This chapter presented a detailed look at data in cloud-native systems.</span></span> <span data-ttu-id="39f96-128">Nous avons commencé par contraster le stockage de données dans des applications monolithiques avec des modèles de stockage de données dans les systèmes cloud-natifs.</span><span class="sxs-lookup"><span data-stu-id="39f96-128">We started by contrasting data storage in monolithic applications with data storage patterns in cloud-native systems.</span></span> <span data-ttu-id="39f96-129">Nous avons examiné les modèles de données mis en œuvre dans les systèmes natifs du cloud, y compris les requêtes inter-services, les transactions distribuées et les modèles pour traiter les systèmes à volume élevé.</span><span class="sxs-lookup"><span data-stu-id="39f96-129">We looked at data patterns implemented in cloud-native systems, including cross-service queries, distributed transactions, and patterns to deal with high-volume systems.</span></span> <span data-ttu-id="39f96-130">Nous avons contrasté SQL avec les données NoSQL.</span><span class="sxs-lookup"><span data-stu-id="39f96-130">We contrasted SQL with NoSQL data.</span></span> <span data-ttu-id="39f96-131">Nous avons examiné les options de stockage de données disponibles dans Azure qui incluent à la fois des options microsoft-centriques et open-source.</span><span class="sxs-lookup"><span data-stu-id="39f96-131">We looked at data storage options available in Azure that include both Microsoft-centric and open-source options.</span></span> <span data-ttu-id="39f96-132">Enfin, nous avons discuté de la mise en cache et de l’elasticsearch dans une application cloud-native.</span><span class="sxs-lookup"><span data-stu-id="39f96-132">Finally, we discussed caching and Elasticsearch in a cloud-native application.</span></span>

### <a name="references"></a><span data-ttu-id="39f96-133">References</span><span class="sxs-lookup"><span data-stu-id="39f96-133">References</span></span>

- [<span data-ttu-id="39f96-134">Modèle de séparation des responsabilités en matière de commande et de requête (CQRS)</span><span class="sxs-lookup"><span data-stu-id="39f96-134">Command and Query Responsibility Segregation (CQRS) pattern</span></span>](https://docs.microsoft.com/azure/architecture/patterns/cqrs)

- [<span data-ttu-id="39f96-135">Modèle d'approvisionnement en événements</span><span class="sxs-lookup"><span data-stu-id="39f96-135">Event Sourcing pattern</span></span>](https://docs.microsoft.com/azure/architecture/patterns/event-sourcing)

- [<span data-ttu-id="39f96-136">Pourquoi la partition RDBMS n’est-elle pas tolérante dans le théorème cap et pourquoi est-elle disponible ?</span><span class="sxs-lookup"><span data-stu-id="39f96-136">Why isn't RDBMS Partition Tolerant in CAP Theorem and why is it Available?</span></span>](https://stackoverflow.com/questions/36404765/why-isnt-rdbms-partition-tolerant-in-cap-theorem-and-why-is-it-available)

- [<span data-ttu-id="39f96-137">Vue matérialisée</span><span class="sxs-lookup"><span data-stu-id="39f96-137">Materialized View</span></span>](https://docs.microsoft.com/azure/architecture/patterns/materialized-view)

- [<span data-ttu-id="39f96-138">Tout ce que vous devez vraiment savoir sur les bases de données open source</span><span class="sxs-lookup"><span data-stu-id="39f96-138">All you really need to know about open source databases</span></span>](https://www.ibm.com/blogs/systems/all-you-really-need-to-know-about-open-source-databases/)

- [<span data-ttu-id="39f96-139">Modèle de transaction de compensation</span><span class="sxs-lookup"><span data-stu-id="39f96-139">Compensating Transaction pattern</span></span>](https://docs.microsoft.com/azure/architecture/patterns/compensating-transaction)

- [<span data-ttu-id="39f96-140">Modèle de saga</span><span class="sxs-lookup"><span data-stu-id="39f96-140">Saga Pattern</span></span>](https://microservices.io/patterns/data/saga.html)

- [<span data-ttu-id="39f96-141">Modèles saga Comment mettre en œuvre les transactions commerciales à l’aide de microservices</span><span class="sxs-lookup"><span data-stu-id="39f96-141">Saga Patterns | How to implement business transactions using microservices</span></span>](https://blog.couchbase.com/saga-pattern-implement-business-transactions-using-microservices-part/)

- [<span data-ttu-id="39f96-142">Modèle de transaction de compensation</span><span class="sxs-lookup"><span data-stu-id="39f96-142">Compensating Transaction pattern</span></span>](https://docs.microsoft.com/azure/architecture/patterns/compensating-transaction)

- [<span data-ttu-id="39f96-143">Se mettre derrière le 9-Ball: Cosmos DB niveaux de cohérence expliqué</span><span class="sxs-lookup"><span data-stu-id="39f96-143">Getting Behind the 9-Ball: Cosmos DB Consistency Levels Explained</span></span>](https://blog.jeremylikness.com/blog/2018-03-23_getting-behind-the-9ball-cosmosdb-consistency-levels/)

- [<span data-ttu-id="39f96-144">Explorer les différents types de bases de données NoSQL Partie II</span><span class="sxs-lookup"><span data-stu-id="39f96-144">Exploring the different types of NoSQL Databases Part II</span></span>](https://www.3pillarglobal.com/insights/exploring-the-different-types-of-nosql-databases)

- [<span data-ttu-id="39f96-145">Sur les bases de données RDBMS, NoSQL et NewSQL. Entrevue avec John Ryan</span><span class="sxs-lookup"><span data-stu-id="39f96-145">On RDBMS, NoSQL and NewSQL databases. Interview with John Ryan</span></span>](http://www.odbms.org/blog/2018/03/on-rdbms-nosql-and-newsql-databases-interview-with-john-ryan/)
  
- [<span data-ttu-id="39f96-146">SQL vs NoSQL vs NewSQL: La comparaison complète</span><span class="sxs-lookup"><span data-stu-id="39f96-146">SQL vs NoSQL vs NewSQL: The Full Comparison</span></span>](https://www.xenonstack.com/blog/sql-vs-nosql-vs-newsql/)

- [<span data-ttu-id="39f96-147">DASH: Quatre propriétés de bases de données Kubernetes-Native</span><span class="sxs-lookup"><span data-stu-id="39f96-147">DASH: Four Properties of Kubernetes-Native Databases</span></span>](https://thenewstack.io/dash-four-properties-of-kubernetes-native-databases/)

- [<span data-ttu-id="39f96-148">CafardDB</span><span class="sxs-lookup"><span data-stu-id="39f96-148">CockroachDB</span></span>](https://www.cockroachlabs.com/)

- [<span data-ttu-id="39f96-149">TiDB (TiDB)</span><span class="sxs-lookup"><span data-stu-id="39f96-149">TiDB</span></span>](https://pingcap.com/en/)

- [<span data-ttu-id="39f96-150">YugabyteDB</span><span class="sxs-lookup"><span data-stu-id="39f96-150">YugabyteDB</span></span>](https://www.yugabyte.com/)

- [<span data-ttu-id="39f96-151">Vitess Vitess</span><span class="sxs-lookup"><span data-stu-id="39f96-151">Vitess</span></span>](https://vitess.io/)

- [<span data-ttu-id="39f96-152">Elasticsearch: The Definitive Guide (Elasticsearch : le guide de référence)</span><span class="sxs-lookup"><span data-stu-id="39f96-152">Elasticsearch: The Definitive Guide</span></span>](http://shop.oreilly.com/product/0636920028505.do)
  
- [<span data-ttu-id="39f96-153">Introduction à Apache Lucene</span><span class="sxs-lookup"><span data-stu-id="39f96-153">Introduction to Apache Lucene</span></span>](https://www.baeldung.com/lucene)

>[!div class="step-by-step"]
><span data-ttu-id="39f96-154">[Suivant précédent](azure-caching.md)
>[Next](resiliency.md)</span><span class="sxs-lookup"><span data-stu-id="39f96-154">[Previous](azure-caching.md)
[Next](resiliency.md)</span></span> <!-- Next Chapter -->
