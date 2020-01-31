---
title: Elasticsearch dans les applications Cloud natives
description: En savoir plus sur l’ajout de fonctionnalités de recherche élastique aux applications Cloud natives.
author: robvet
ms.date: 01/22/2020
ms.openlocfilehash: 6ea237eddc89a8c6843d6b34b05b1b71515a99b6
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794876"
---
# <a name="elasticsearch-in-a-cloud-native-app"></a><span data-ttu-id="28c22-103">Elasticsearch dans une application Cloud Native</span><span class="sxs-lookup"><span data-stu-id="28c22-103">Elasticsearch in a cloud-native app</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="28c22-104">Elasticsearch est un système de recherche et d’analyse distribué qui permet des fonctionnalités de recherche complexes sur divers types de données.</span><span class="sxs-lookup"><span data-stu-id="28c22-104">Elasticsearch is a distributed search and analytics system that enables complex search capabilities across diverse types of data.</span></span> <span data-ttu-id="28c22-105">Il est open source et largement populaire.</span><span class="sxs-lookup"><span data-stu-id="28c22-105">It's open source and widely popular.</span></span> <span data-ttu-id="28c22-106">Prenez en compte la façon dont les entreprises suivantes intègrent Elasticsearch dans leur application :</span><span class="sxs-lookup"><span data-stu-id="28c22-106">Consider how the following companies integrate Elasticsearch into their application:</span></span>

- <span data-ttu-id="28c22-107">Recherche de texte intégral et de recherche incrémentielle (recherche au fur [et à mesure](https://blog.wikimedia.org/2014/01/06/wikimedia-moving-to-elasticsearch/) que vous tapez).</span><span class="sxs-lookup"><span data-stu-id="28c22-107">[Wikipedia](https://blog.wikimedia.org/2014/01/06/wikimedia-moving-to-elasticsearch/) for full-text and incremental (search as you type) searching.</span></span>
- <span data-ttu-id="28c22-108">[GitHub](https://www.elastic.co/customers/github) pour indexer et exposer plus de 8 millions référentiels de code.</span><span class="sxs-lookup"><span data-stu-id="28c22-108">[GitHub](https://www.elastic.co/customers/github) to index and expose over 8 million code repositories.</span></span>  
- <span data-ttu-id="28c22-109">[Ancrer](https://www.elastic.co/customers/docker) pour rendre sa bibliothèque de conteneurs détectable.</span><span class="sxs-lookup"><span data-stu-id="28c22-109">[Docker](https://www.elastic.co/customers/docker) for making its container library discoverable.</span></span>

<span data-ttu-id="28c22-110">Elasticsearch repose sur le moteur de recherche en texte intégral [Apache Lucene](https://lucene.apache.org/core/) .</span><span class="sxs-lookup"><span data-stu-id="28c22-110">Elasticsearch is built on top of the [Apache Lucene](https://lucene.apache.org/core/) full-text search engine.</span></span> <span data-ttu-id="28c22-111">Lucene fournit l’indexation et l’interrogation de documents à hautes performances.</span><span class="sxs-lookup"><span data-stu-id="28c22-111">Lucene provides high-performance document indexing and querying.</span></span> <span data-ttu-id="28c22-112">Il indexe les données avec un schéma d’indexation inversé : au lieu de mapper les pages aux mots clés, il mappe les mots clés aux pages comme un glossaire à la fin d’un livre.</span><span class="sxs-lookup"><span data-stu-id="28c22-112">It indexes data with an inverted indexing scheme – instead of mapping pages to keywords, it maps keywords to pages just like a glossary at the end of a book.</span></span> <span data-ttu-id="28c22-113">Lucene dispose de puissantes fonctionnalités de syntaxe de requête et peut interroger les données de la façon suivante :</span><span class="sxs-lookup"><span data-stu-id="28c22-113">Lucene has powerful query syntax capabilities and can query data by:</span></span>

- <span data-ttu-id="28c22-114">Terme (un mot complet)</span><span class="sxs-lookup"><span data-stu-id="28c22-114">Term (a full word)</span></span> 
- <span data-ttu-id="28c22-115">Préfixe (commençant par Word)</span><span class="sxs-lookup"><span data-stu-id="28c22-115">Prefix (starts-with word)</span></span>
- <span data-ttu-id="28c22-116">Caractère générique (à l’aide des filtres «\*» ou «  ? »)</span><span class="sxs-lookup"><span data-stu-id="28c22-116">Wildcard (using "\*" or "?" filters)</span></span>
- <span data-ttu-id="28c22-117">Expression (une séquence de texte dans un document)</span><span class="sxs-lookup"><span data-stu-id="28c22-117">Phrase (a sequence of text in a document)</span></span>
- <span data-ttu-id="28c22-118">Valeur booléenne (recherches complexes combinant des requêtes)</span><span class="sxs-lookup"><span data-stu-id="28c22-118">Boolean value (complex searches combining queries)</span></span>

<span data-ttu-id="28c22-119">Bien que Lucene fournisse des éléments de bas niveau pour la recherche, Elasticsearch fournit le serveur qui se trouve au-dessus de Lucene.</span><span class="sxs-lookup"><span data-stu-id="28c22-119">While Lucene provides low-level plumbing for searching, Elasticsearch provides the server that sits on top of Lucene.</span></span> <span data-ttu-id="28c22-120">Elasticsearch ajoute des fonctionnalités de niveau supérieur pour simplifier le travail Lucene, y compris une API RESTful pour accéder aux fonctionnalités d’indexation et de recherche de Lucene.</span><span class="sxs-lookup"><span data-stu-id="28c22-120">Elasticsearch adds higher-level functionality to simplify working Lucene, including a RESTful API to access Lucene’s indexing and searching functionality.</span></span> <span data-ttu-id="28c22-121">Il fournit également une infrastructure distribuée, capable d’évoluer massivement, de tolérance de panne et de haute disponibilité.</span><span class="sxs-lookup"><span data-stu-id="28c22-121">It also provides a distributed infrastructure capable of massive scalability, fault tolerance, and high availability.</span></span>

<span data-ttu-id="28c22-122">Pour les applications Cloud plus volumineuses avec des exigences de recherche complexes, Elasticsearch est disponible en tant que service géré dans Azure.</span><span class="sxs-lookup"><span data-stu-id="28c22-122">For larger cloud-native applications with complex search requirements, Elasticsearch is available as managed service in Azure.</span></span> <span data-ttu-id="28c22-123">Le Place de marché Microsoft Azure propose des modèles préconfigurés que les développeurs peuvent utiliser pour déployer un cluster Elasticsearch sur Azure.</span><span class="sxs-lookup"><span data-stu-id="28c22-123">The Microsoft Azure Marketplace features preconfigured templates which developers can use to deploy an Elasticsearch cluster on Azure.</span></span>

<span data-ttu-id="28c22-124">Du Place de marché Microsoft Azure, les développeurs peuvent utiliser des modèles préconfigurés pour déployer rapidement un cluster Elasticsearch sur Azure.</span><span class="sxs-lookup"><span data-stu-id="28c22-124">From the Microsoft Azure Marketplace, developers can use preconfigured templates built to quickly deploy an Elasticsearch cluster on Azure.</span></span> <span data-ttu-id="28c22-125">À l’aide de l’offre gérée par Azure, vous pouvez déployer jusqu’à 50 nœuds de données, 20 nœuds de coordination et trois nœuds principaux dédiés.</span><span class="sxs-lookup"><span data-stu-id="28c22-125">Using the Azure-managed offering, you can deploy up to 50 data nodes, 20 coordinating nodes, and three dedicated master nodes.</span></span>

## <a name="summary"></a><span data-ttu-id="28c22-126">Récapitulatif</span><span class="sxs-lookup"><span data-stu-id="28c22-126">Summary</span></span>

<span data-ttu-id="28c22-127">Ce chapitre a présenté une vue détaillée des données dans les systèmes Cloud natifs.</span><span class="sxs-lookup"><span data-stu-id="28c22-127">This chapter presented a detailed look at data in cloud-native systems.</span></span> <span data-ttu-id="28c22-128">Nous avons commencé par comparer le stockage des données dans les applications monolithiques avec les modèles de stockage des données dans les systèmes natifs du Cloud.</span><span class="sxs-lookup"><span data-stu-id="28c22-128">We started by contrasting data storage in monolithic applications with data storage patterns in cloud-native systems.</span></span> <span data-ttu-id="28c22-129">Nous avons examiné les modèles de données implémentés dans les systèmes Cloud natifs, notamment les requêtes entre services, les transactions distribuées et les modèles pour gérer les systèmes à volume élevé.</span><span class="sxs-lookup"><span data-stu-id="28c22-129">We looked at data patterns implemented in cloud-native systems, including cross-service queries, distributed transactions, and patterns to deal with high-volume systems.</span></span> <span data-ttu-id="28c22-130">Nous avons comparé SQL avec les données NoSQL.</span><span class="sxs-lookup"><span data-stu-id="28c22-130">We contrasted SQL with NoSQL data.</span></span> <span data-ttu-id="28c22-131">Nous avons examiné les options de stockage de données disponibles dans Azure qui incluent des options orientées Microsoft et open source.</span><span class="sxs-lookup"><span data-stu-id="28c22-131">We looked at data storage options available in Azure that include both Microsoft-centric and open-source options.</span></span> <span data-ttu-id="28c22-132">Enfin, nous avons abordé Caching et Elasticsearch dans une application Cloud native.</span><span class="sxs-lookup"><span data-stu-id="28c22-132">Finally, we discussed caching and Elasticsearch in a cloud-native application.</span></span>

### <a name="references"></a><span data-ttu-id="28c22-133">Références</span><span class="sxs-lookup"><span data-stu-id="28c22-133">References</span></span>

- [<span data-ttu-id="28c22-134">Modèle séparation des responsabilités en matière de commande et de requête (CQRS)</span><span class="sxs-lookup"><span data-stu-id="28c22-134">Command and Query Responsibility Segregation (CQRS) pattern</span></span>](https://docs.microsoft.com/azure/architecture/patterns/cqrs)

- [<span data-ttu-id="28c22-135">Modèle d’approvisionnement en événements</span><span class="sxs-lookup"><span data-stu-id="28c22-135">Event Sourcing pattern</span></span>](https://docs.microsoft.com/azure/architecture/patterns/event-sourcing)

- [<span data-ttu-id="28c22-136">SGBDR et bases de données NoSQL : vue d’ensemble</span><span class="sxs-lookup"><span data-stu-id="28c22-136">RDBMSs vs. NoSQL Databases: Overview</span></span>](https://maxivak.com/rdbms-vs-nosql-databases/)

- [<span data-ttu-id="28c22-137">Pourquoi la partition de SGBDR n’est-elle pas tolérante dans le CAP CAP et pourquoi est-elle disponible ?</span><span class="sxs-lookup"><span data-stu-id="28c22-137">Why isn't RDBMS Partition Tolerant in CAP Theorem and why is it Available?</span></span>](https://stackoverflow.com/questions/36404765/why-isnt-rdbms-partition-tolerant-in-cap-theorem-and-why-is-it-available)

- [<span data-ttu-id="28c22-138">Vue matérialisée</span><span class="sxs-lookup"><span data-stu-id="28c22-138">Materialized View</span></span>](https://docs.microsoft.com/azure/architecture/patterns/materialized-view)

- [<span data-ttu-id="28c22-139">Tout ce que vous devez savoir sur les bases de données Open source</span><span class="sxs-lookup"><span data-stu-id="28c22-139">All you really need to know about open source databases</span></span>](https://www.ibm.com/blogs/systems/all-you-really-need-to-know-about-open-source-databases/)

- [<span data-ttu-id="28c22-140">Modèle de transaction de compensation</span><span class="sxs-lookup"><span data-stu-id="28c22-140">Compensating Transaction pattern</span></span>](https://docs.microsoft.com/azure/architecture/patterns/compensating-transaction)

- [<span data-ttu-id="28c22-141">Modèle saga</span><span class="sxs-lookup"><span data-stu-id="28c22-141">Saga Pattern</span></span>](https://microservices.io/patterns/data/saga.html)

- [<span data-ttu-id="28c22-142">Modèles saga | Comment implémenter des transactions commerciales à l’aide de microservices</span><span class="sxs-lookup"><span data-stu-id="28c22-142">Saga Patterns | How to implement business transactions using microservices</span></span>](https://blog.couchbase.com/saga-pattern-implement-business-transactions-using-microservices-part/)

- [<span data-ttu-id="28c22-143">Modèle de transaction de compensation</span><span class="sxs-lookup"><span data-stu-id="28c22-143">Compensating Transaction pattern</span></span>](https://docs.microsoft.com/azure/architecture/patterns/compensating-transaction)

- [<span data-ttu-id="28c22-144">En arrière-plan des niveaux de cohérence 9 Ball : Cosmos DB expliqués</span><span class="sxs-lookup"><span data-stu-id="28c22-144">Getting Behind the 9-Ball: Cosmos DB Consistency Levels Explained</span></span>](https://blog.jeremylikness.com/blog/2018-03-23_getting-behind-the-9ball-cosmosdb-consistency-levels/)

- [<span data-ttu-id="28c22-145">Exploration des différents types de bases de données NoSQL, partie II</span><span class="sxs-lookup"><span data-stu-id="28c22-145">Exploring the different types of NoSQL Databases Part II</span></span>](https://www.3pillarglobal.com/insights/exploring-the-different-types-of-nosql-databases)

- [<span data-ttu-id="28c22-146">Sur les bases de données de SGBDR, NoSQL et NewSQL. Entretien avec John Ryan</span><span class="sxs-lookup"><span data-stu-id="28c22-146">On RDBMS, NoSQL and NewSQL databases. Interview with John Ryan</span></span>](http://www.odbms.org/blog/2018/03/on-rdbms-nosql-and-newsql-databases-interview-with-john-ryan/)
  
- [<span data-ttu-id="28c22-147">SQL vs NoSQL vs NewSQL : comparaison complète</span><span class="sxs-lookup"><span data-stu-id="28c22-147">SQL vs NoSQL vs NewSQL: The Full Comparison</span></span>](https://www.xenonstack.com/blog/sql-vs-nosql-vs-newsql/)

- [<span data-ttu-id="28c22-148">DASH : quatre propriétés des bases de données Kubernetes-natives</span><span class="sxs-lookup"><span data-stu-id="28c22-148">DASH: Four Properties of Kubernetes-Native Databases</span></span>](https://thenewstack.io/dash-four-properties-of-kubernetes-native-databases/)

- [<span data-ttu-id="28c22-149">CockroachDB</span><span class="sxs-lookup"><span data-stu-id="28c22-149">CockroachDB</span></span>](https://www.cockroachlabs.com/)

- [<span data-ttu-id="28c22-150">TiDB</span><span class="sxs-lookup"><span data-stu-id="28c22-150">TiDB</span></span>](https://pingcap.com/en/)

- [<span data-ttu-id="28c22-151">YugabyteDB</span><span class="sxs-lookup"><span data-stu-id="28c22-151">YugabyteDB</span></span>](https://www.yugabyte.com/)

- [<span data-ttu-id="28c22-152">Vitess</span><span class="sxs-lookup"><span data-stu-id="28c22-152">Vitess</span></span>](https://vitess.io/)

- [<span data-ttu-id="28c22-153">Elasticsearch : le guide définitif</span><span class="sxs-lookup"><span data-stu-id="28c22-153">Elasticsearch: The Definitive Guide</span></span>](http://shop.oreilly.com/product/0636920028505.do)
  
- [<span data-ttu-id="28c22-154">Présentation d’Apache Lucene</span><span class="sxs-lookup"><span data-stu-id="28c22-154">Introduction to Apache Lucene</span></span>](https://www.baeldung.com/lucene)

>[!div class="step-by-step"]
><span data-ttu-id="28c22-155">[Précédent](azure-caching.md)
>[Suivant](resiliency.md)</span><span class="sxs-lookup"><span data-stu-id="28c22-155">[Previous](azure-caching.md)
[Next](resiliency.md)</span></span> <!-- Next Chapter -->
