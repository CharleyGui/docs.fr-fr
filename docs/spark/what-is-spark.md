---
title: Qu’est-ce que Apache Spark ?
description: En savoir plus sur les scénarios de Apache Spark et de Big Data.
ms.date: 10/15/2019
ms.topic: conceptual
ms.custom: mvc
ms.openlocfilehash: ccf41f08df3c68a039210320f14219e6b6229a64
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72396235"
---
# <a name="what-is-apache-spark"></a><span data-ttu-id="466ce-103">Qu’est-ce que Apache Spark ?</span><span class="sxs-lookup"><span data-stu-id="466ce-103">What is Apache Spark?</span></span>

<span data-ttu-id="466ce-104">[Apache Spark](https://spark.apache.org/) est une infrastructure de traitement parallèle Open source qui prend en charge le traitement en mémoire pour améliorer les performances des applications qui analysent les Big Data.</span><span class="sxs-lookup"><span data-stu-id="466ce-104">[Apache Spark](https://spark.apache.org/) is an open-source parallel processing framework that supports in-memory processing to boost the performance of applications that analyze big data.</span></span> <span data-ttu-id="466ce-105">Les solutions Big Data sont conçues pour gérer les données qui sont trop volumineuses ou complexes pour les bases de données traditionnelles.</span><span class="sxs-lookup"><span data-stu-id="466ce-105">Big data solutions are designed to handle data that is too large or complex for traditional databases.</span></span> <span data-ttu-id="466ce-106">Spark traite de grandes quantités de données en mémoire, ce qui est beaucoup plus rapide que les alternatives sur disque.</span><span class="sxs-lookup"><span data-stu-id="466ce-106">Spark processes large amounts of data in memory, which is much faster than disk-based alternatives.</span></span> 

## <a name="common-big-data-scenarios"></a><span data-ttu-id="466ce-107">Scénarios de Big Data courants</span><span class="sxs-lookup"><span data-stu-id="466ce-107">Common big data scenarios</span></span>

<span data-ttu-id="466ce-108">Vous pouvez envisager une architecture Big Data si vous avez besoin de stocker et traiter de gros volumes de données, de transformer des données non structurées ou de traiter des données de streaming.</span><span class="sxs-lookup"><span data-stu-id="466ce-108">You might consider a big data architecture if you need to store and process large volumes of data, transform unstructured data, or processes streaming data.</span></span> <span data-ttu-id="466ce-109">Spark est un moteur de traitement distribué à usage général qui peut être utilisé pour plusieurs scénarios de Big Data.</span><span class="sxs-lookup"><span data-stu-id="466ce-109">Spark is a general-purpose distributed processing engine that can be used for several big data scenarios.</span></span> 

### <a name="extract-transform-and-load-etl"></a><span data-ttu-id="466ce-110">Extraction, transformation et chargement (ETL)</span><span class="sxs-lookup"><span data-stu-id="466ce-110">Extract, transform, and load (ETL)</span></span>

<span data-ttu-id="466ce-111">L' [extraction, la transformation et le chargement (ETL)](/azure/architecture/data-guide/relational-data/etl) est le processus qui consiste à collecter des données à partir d’une ou plusieurs sources, à modifier les données et à déplacer les données vers un nouveau magasin de données.</span><span class="sxs-lookup"><span data-stu-id="466ce-111">[Extract, transform, and load (ETL)](/azure/architecture/data-guide/relational-data/etl) is the process of collecting data from one or multiple sources, modifying the data, and moving the data to a new data store.</span></span> <span data-ttu-id="466ce-112">Il existe plusieurs façons de transformer des données, notamment :</span><span class="sxs-lookup"><span data-stu-id="466ce-112">There are several ways to transform data, including:</span></span>

* <span data-ttu-id="466ce-113">Filtrage</span><span class="sxs-lookup"><span data-stu-id="466ce-113">Filtering</span></span>
* <span data-ttu-id="466ce-114">Tri</span><span class="sxs-lookup"><span data-stu-id="466ce-114">Sorting</span></span>
* <span data-ttu-id="466ce-115">Agrégation</span><span class="sxs-lookup"><span data-stu-id="466ce-115">Aggregating</span></span>
* <span data-ttu-id="466ce-116">Jointure</span><span class="sxs-lookup"><span data-stu-id="466ce-116">Joining</span></span>
* <span data-ttu-id="466ce-117">Infection</span><span class="sxs-lookup"><span data-stu-id="466ce-117">Cleaning</span></span>
* <span data-ttu-id="466ce-118">Déduplication</span><span class="sxs-lookup"><span data-stu-id="466ce-118">Deduplicating</span></span>
* <span data-ttu-id="466ce-119">Validation</span><span class="sxs-lookup"><span data-stu-id="466ce-119">Validating</span></span>

### <a name="real-time-data-stream-processing"></a><span data-ttu-id="466ce-120">Traitement du flux de données en temps réel</span><span class="sxs-lookup"><span data-stu-id="466ce-120">Real-time data stream processing</span></span>

<span data-ttu-id="466ce-121">Les données en continu ou en temps réel sont des données en mouvement.</span><span class="sxs-lookup"><span data-stu-id="466ce-121">Streaming, or real-time, data is data in motion.</span></span> <span data-ttu-id="466ce-122">La télémétrie des appareils IoT, Weblogs et parcours sont des exemples de données de streaming.</span><span class="sxs-lookup"><span data-stu-id="466ce-122">Telemetry from IoT devices, weblogs, and clickstreams are all examples of streaming data.</span></span> <span data-ttu-id="466ce-123">Les données en temps réel peuvent être traitées pour fournir des informations utiles, telles que l’analyse géographique, la surveillance à distance et la détection d’anomalies.</span><span class="sxs-lookup"><span data-stu-id="466ce-123">Real-time data can be processed to provide useful information, such as geospatial analysis, remote monitoring, and anomaly detection.</span></span> <span data-ttu-id="466ce-124">Tout comme les données relationnelles, vous pouvez filtrer, agréger et préparer les données de diffusion en continu avant de déplacer les données vers un récepteur de sortie.</span><span class="sxs-lookup"><span data-stu-id="466ce-124">Just like relational data, you can filter, aggregate, and prepare streaming data before moving the data to an output sink.</span></span> <span data-ttu-id="466ce-125">Apache Spark prend en charge [le traitement des flux de données en temps réel](/azure/architecture/data-guide/big-data/real-time-processing) via [Spark streaming](https://spark.apache.org/streaming/).</span><span class="sxs-lookup"><span data-stu-id="466ce-125">Apache Spark supports [real-time data stream processing](/azure/architecture/data-guide/big-data/real-time-processing) through [Spark Streaming](https://spark.apache.org/streaming/).</span></span> 

### <a name="batch-processing"></a><span data-ttu-id="466ce-126">Traitement par lots</span><span class="sxs-lookup"><span data-stu-id="466ce-126">Batch processing</span></span>

<span data-ttu-id="466ce-127">Le [traitement par lots](/azure/architecture/data-guide/big-data/batch-processing) est le traitement de Big Data au repos.</span><span class="sxs-lookup"><span data-stu-id="466ce-127">[Batch processing](/azure/architecture/data-guide/big-data/batch-processing) is the processing of big data at rest.</span></span> <span data-ttu-id="466ce-128">Vous pouvez filtrer, agréger et préparer des jeux de données très volumineux à l’aide de travaux de longue durée en parallèle.</span><span class="sxs-lookup"><span data-stu-id="466ce-128">You can filter, aggregate, and prepare very large datasets using long-running jobs in parallel.</span></span>

### <a name="machine-learning-through-mllib"></a><span data-ttu-id="466ce-129">Machine learning via MLlib</span><span class="sxs-lookup"><span data-stu-id="466ce-129">Machine learning through MLlib</span></span>

<span data-ttu-id="466ce-130">Machine Learning est utilisé pour les problèmes analytiques avancés.</span><span class="sxs-lookup"><span data-stu-id="466ce-130">Machine learning is used for advanced analytical problems.</span></span> <span data-ttu-id="466ce-131">Votre ordinateur peut utiliser les données existantes pour prévoir ou prédire les comportements, les résultats et les tendances futurs.</span><span class="sxs-lookup"><span data-stu-id="466ce-131">Your computer can use existing data to forecast or predict future behaviors, outcomes, and trends.</span></span> <span data-ttu-id="466ce-132">La bibliothèque de Machine Learning de Apache Spark, [MLlib](https://spark.apache.org/mllib/), contient plusieurs algorithmes et utilitaires de machine learning.</span><span class="sxs-lookup"><span data-stu-id="466ce-132">Apache Spark's machine learning library, [MLlib](https://spark.apache.org/mllib/), contains several machine learning algorithms and utilities.</span></span>

### <a name="graph-processing-through-graphx"></a><span data-ttu-id="466ce-133">Traitement des graphiques via GraphX</span><span class="sxs-lookup"><span data-stu-id="466ce-133">Graph processing through GraphX</span></span>

<span data-ttu-id="466ce-134">Un graphique est une collection de nœuds connectés par des bords.</span><span class="sxs-lookup"><span data-stu-id="466ce-134">A graph is a collection of nodes connected by edges.</span></span> <span data-ttu-id="466ce-135">Vous pouvez utiliser une base de données de graphiques si vous avez des données ou des données Hierarchial avec des relations interconnectées.</span><span class="sxs-lookup"><span data-stu-id="466ce-135">You might use a graph database if you have hierarchial data or data with interconnected relationships.</span></span> <span data-ttu-id="466ce-136">Vous pouvez traiter ces données à l’aide de l’API [graphx](https://spark.apache.org/graphx/) de Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="466ce-136">You can process this data using Apache Spark's [GraphX](https://spark.apache.org/graphx/) API.</span></span>

### <a name="sql-and-structured-data-processing-with-spark-sql"></a><span data-ttu-id="466ce-137">SQL et traitement des données structurées avec Spark SQL</span><span class="sxs-lookup"><span data-stu-id="466ce-137">SQL and structured data processing with Spark SQL</span></span>

<span data-ttu-id="466ce-138">Si vous utilisez des données structurées (formatées), vous pouvez utiliser des requêtes SQL dans votre application Spark à l’aide de [Spark SQL](https://spark.apache.org/sql/).</span><span class="sxs-lookup"><span data-stu-id="466ce-138">If you're working with structured (formatted) data, you can use SQL queries in your Spark application using [Spark SQL](https://spark.apache.org/sql/).</span></span>

## <a name="apache-spark-architecture"></a><span data-ttu-id="466ce-139">Architecture Apache Spark</span><span class="sxs-lookup"><span data-stu-id="466ce-139">Apache Spark architecture</span></span>

<span data-ttu-id="466ce-140">Apache Spark, qui utilise l’architecture maître/travail, a trois composants principaux : le pilote, les exécuteurs et le gestionnaire de cluster.</span><span class="sxs-lookup"><span data-stu-id="466ce-140">Apache Spark, which uses the master/worker architecture, has three main components: the driver, executors, and cluster manager.</span></span>

![Architecture Apache Spark](media/spark-architecture.png)

### <a name="driver"></a><span data-ttu-id="466ce-142">Pilote</span><span class="sxs-lookup"><span data-stu-id="466ce-142">Driver</span></span>

<span data-ttu-id="466ce-143">Le pilote est constitué de votre programme, par C# exemple une application console et une session Spark.</span><span class="sxs-lookup"><span data-stu-id="466ce-143">The driver consists of your program, like a C# console app, and a Spark session.</span></span> <span data-ttu-id="466ce-144">La session Spark prend votre programme et le divise en tâches plus petites gérées par les exécuteurs.</span><span class="sxs-lookup"><span data-stu-id="466ce-144">The Spark session takes your program and divides it into smaller tasks that are handled by the executors.</span></span>

### <a name="executors"></a><span data-ttu-id="466ce-145">Exécuteurs</span><span class="sxs-lookup"><span data-stu-id="466ce-145">Executors</span></span>

<span data-ttu-id="466ce-146">Chaque exécuteur, ou nœud de travail, reçoit une tâche du pilote et exécute cette tâche.</span><span class="sxs-lookup"><span data-stu-id="466ce-146">Each executor, or worker node, receives a task from the driver and executes that task.</span></span> <span data-ttu-id="466ce-147">Les exécuteurs résident sur une entité appelée cluster.</span><span class="sxs-lookup"><span data-stu-id="466ce-147">The executors reside on an entity known as a cluster.</span></span>

### <a name="cluster-manager"></a><span data-ttu-id="466ce-148">Gestionnaire de cluster</span><span class="sxs-lookup"><span data-stu-id="466ce-148">Cluster manager</span></span>

<span data-ttu-id="466ce-149">Le gestionnaire de cluster communique avec le pilote et les exécuteurs pour :</span><span class="sxs-lookup"><span data-stu-id="466ce-149">The cluster manager communicates with both the driver and the executors to:</span></span>

- <span data-ttu-id="466ce-150">Gérer l’allocation des ressources</span><span class="sxs-lookup"><span data-stu-id="466ce-150">Manage resource allocation</span></span>
- <span data-ttu-id="466ce-151">Gérer la Division du programme</span><span class="sxs-lookup"><span data-stu-id="466ce-151">Manage program division</span></span>
- <span data-ttu-id="466ce-152">Gérer l’exécution du programme</span><span class="sxs-lookup"><span data-stu-id="466ce-152">Manage program execution</span></span>

## <a name="language-support"></a><span data-ttu-id="466ce-153">Langages pris en charge</span><span class="sxs-lookup"><span data-stu-id="466ce-153">Language support</span></span>

<span data-ttu-id="466ce-154">Apache Spark prend en charge les langages de programmation suivants :</span><span class="sxs-lookup"><span data-stu-id="466ce-154">Apache Spark supports the following programming languages:</span></span>

- <span data-ttu-id="466ce-155">Scala</span><span class="sxs-lookup"><span data-stu-id="466ce-155">Scala</span></span>
- <span data-ttu-id="466ce-156">Python</span><span class="sxs-lookup"><span data-stu-id="466ce-156">Python</span></span>
- <span data-ttu-id="466ce-157">Java</span><span class="sxs-lookup"><span data-stu-id="466ce-157">Java</span></span>
- <span data-ttu-id="466ce-158">SQL</span><span class="sxs-lookup"><span data-stu-id="466ce-158">SQL</span></span>
- <span data-ttu-id="466ce-159">R</span><span class="sxs-lookup"><span data-stu-id="466ce-159">R</span></span>
- <span data-ttu-id="466ce-160">.NET</span><span class="sxs-lookup"><span data-stu-id="466ce-160">.NET</span></span>

## <a name="spark-apis"></a><span data-ttu-id="466ce-161">API Spark</span><span class="sxs-lookup"><span data-stu-id="466ce-161">Spark APIs</span></span>

<span data-ttu-id="466ce-162">Apache Spark prend en charge les API suivantes :</span><span class="sxs-lookup"><span data-stu-id="466ce-162">Apache Spark supports the following APIs:</span></span>

- [<span data-ttu-id="466ce-163">API Scala Spark</span><span class="sxs-lookup"><span data-stu-id="466ce-163">Spark Scala API</span></span>](https://spark.apache.org/docs/2.2.0/api/scala/index.html)
- [<span data-ttu-id="466ce-164">API Java Spark</span><span class="sxs-lookup"><span data-stu-id="466ce-164">Spark Java API</span></span>](https://spark.apache.org/docs/2.2.0/api/java/index.html)
- [<span data-ttu-id="466ce-165">API Python Spark</span><span class="sxs-lookup"><span data-stu-id="466ce-165">Spark Python API</span></span>](https://spark.apache.org/docs/2.2.0/api/python/index.html)
- [<span data-ttu-id="466ce-166">API R Spark</span><span class="sxs-lookup"><span data-stu-id="466ce-166">Spark R API</span></span>](https://spark.apache.org/docs/2.2.0/api/R/index.html)
- <span data-ttu-id="466ce-167">[Spark SQL](https://spark.apache.org/docs/latest/api/sql/index.html), fonctions intégrées</span><span class="sxs-lookup"><span data-stu-id="466ce-167">[Spark SQL](https://spark.apache.org/docs/latest/api/sql/index.html), built-in functions</span></span>

## <a name="next-steps"></a><span data-ttu-id="466ce-168">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="466ce-168">Next steps</span></span>

<span data-ttu-id="466ce-169">Découvrez comment vous pouvez utiliser Apache Spark dans votre application .NET.</span><span class="sxs-lookup"><span data-stu-id="466ce-169">Learn how you can use Apache Spark in your .NET application.</span></span> <span data-ttu-id="466ce-170">Avec .NET pour Apache Spark, les développeurs disposant d’une expérience .NET et d’une logique C# métier F#peuvent écrire des requêtes Big Data dans et.</span><span class="sxs-lookup"><span data-stu-id="466ce-170">With .NET for Apache Spark, developers with .NET experience and business logic can write big data queries in C# and F#.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="466ce-171">Qu’est-ce que .NET pour Apache Spark</span><span class="sxs-lookup"><span data-stu-id="466ce-171">What is .NET for Apache Spark</span></span>](what-is-apache-spark-dotnet.md)
