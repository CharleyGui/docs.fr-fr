---
title: Qu’est-ce qu’Apache Spark ?
description: Renseignez-vous sur Apache Spark et les scénarios big data.
ms.date: 10/15/2019
ms.topic: conceptual
ms.custom: mvc
ms.openlocfilehash: 653f355d09a045feabb3dee0f5737cb691cf2dc4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73458174"
---
# <a name="what-is-apache-spark"></a><span data-ttu-id="dc811-103">Qu’est-ce qu’Apache Spark ?</span><span class="sxs-lookup"><span data-stu-id="dc811-103">What is Apache Spark?</span></span>

<span data-ttu-id="dc811-104">[Apache Spark](https://spark.apache.org/) est un cadre de traitement parallèle open-source qui prend en charge le traitement de la mémoire pour augmenter les performances des applications qui analysent le Big Data.</span><span class="sxs-lookup"><span data-stu-id="dc811-104">[Apache Spark](https://spark.apache.org/) is an open-source parallel processing framework that supports in-memory processing to boost the performance of applications that analyze big data.</span></span> <span data-ttu-id="dc811-105">Les solutions Big Data sont conçues pour traiter des données trop grandes ou complexes pour les bases de données traditionnelles.</span><span class="sxs-lookup"><span data-stu-id="dc811-105">Big data solutions are designed to handle data that is too large or complex for traditional databases.</span></span> <span data-ttu-id="dc811-106">Spark traite de grandes quantités de données dans la mémoire, ce qui est beaucoup plus rapide que les alternatives basées sur le disque.</span><span class="sxs-lookup"><span data-stu-id="dc811-106">Spark processes large amounts of data in memory, which is much faster than disk-based alternatives.</span></span>

## <a name="common-big-data-scenarios"></a><span data-ttu-id="dc811-107">Scénarios communs de Big Data</span><span class="sxs-lookup"><span data-stu-id="dc811-107">Common big data scenarios</span></span>

<span data-ttu-id="dc811-108">Vous pouvez envisager une architecture big data si vous avez besoin de stocker et de traiter de grands volumes de données, de transformer des données non structurées ou de traiter les données de streaming.</span><span class="sxs-lookup"><span data-stu-id="dc811-108">You might consider a big data architecture if you need to store and process large volumes of data, transform unstructured data, or processes streaming data.</span></span> <span data-ttu-id="dc811-109">Spark est un moteur de traitement distribué à usage général qui peut être utilisé pour plusieurs scénarios big data.</span><span class="sxs-lookup"><span data-stu-id="dc811-109">Spark is a general-purpose distributed processing engine that can be used for several big data scenarios.</span></span>

### <a name="extract-transform-and-load-etl"></a><span data-ttu-id="dc811-110">Extraire, transformer et charger (ETL)</span><span class="sxs-lookup"><span data-stu-id="dc811-110">Extract, transform, and load (ETL)</span></span>

<span data-ttu-id="dc811-111">[L’extraction,](/azure/architecture/data-guide/relational-data/etl) la transformation et la charge (ETL) sont le processus de collecte de données à partir d’une ou plusieurs sources, de modification des données et de transfert des données vers un nouveau magasin de données.</span><span class="sxs-lookup"><span data-stu-id="dc811-111">[Extract, transform, and load (ETL)](/azure/architecture/data-guide/relational-data/etl) is the process of collecting data from one or multiple sources, modifying the data, and moving the data to a new data store.</span></span> <span data-ttu-id="dc811-112">Il existe plusieurs façons de transformer les données, notamment :</span><span class="sxs-lookup"><span data-stu-id="dc811-112">There are several ways to transform data, including:</span></span>

* <span data-ttu-id="dc811-113">Filtrage</span><span class="sxs-lookup"><span data-stu-id="dc811-113">Filtering</span></span>
* <span data-ttu-id="dc811-114">Tri</span><span class="sxs-lookup"><span data-stu-id="dc811-114">Sorting</span></span>
* <span data-ttu-id="dc811-115">Agrégation</span><span class="sxs-lookup"><span data-stu-id="dc811-115">Aggregating</span></span>
* <span data-ttu-id="dc811-116">Jonction</span><span class="sxs-lookup"><span data-stu-id="dc811-116">Joining</span></span>
* <span data-ttu-id="dc811-117">Nettoyage</span><span class="sxs-lookup"><span data-stu-id="dc811-117">Cleaning</span></span>
* <span data-ttu-id="dc811-118">Déduplicating</span><span class="sxs-lookup"><span data-stu-id="dc811-118">Deduplicating</span></span>
* <span data-ttu-id="dc811-119">Validation</span><span class="sxs-lookup"><span data-stu-id="dc811-119">Validating</span></span>

### <a name="real-time-data-stream-processing"></a><span data-ttu-id="dc811-120">Traitement des flux de données en temps réel</span><span class="sxs-lookup"><span data-stu-id="dc811-120">Real-time data stream processing</span></span>

<span data-ttu-id="dc811-121">Le streaming, ou en temps réel, les données sont des données en mouvement.</span><span class="sxs-lookup"><span data-stu-id="dc811-121">Streaming, or real-time, data is data in motion.</span></span> <span data-ttu-id="dc811-122">La télémétrie des appareils IoT, des blogs et des flux de clics sont autant d’exemples de données de streaming.</span><span class="sxs-lookup"><span data-stu-id="dc811-122">Telemetry from IoT devices, weblogs, and clickstreams are all examples of streaming data.</span></span> <span data-ttu-id="dc811-123">Les données en temps réel peuvent être traitées pour fournir des informations utiles, telles que l’analyse géospatiale, la surveillance à distance et la détection des anomalies.</span><span class="sxs-lookup"><span data-stu-id="dc811-123">Real-time data can be processed to provide useful information, such as geospatial analysis, remote monitoring, and anomaly detection.</span></span> <span data-ttu-id="dc811-124">Tout comme les données relationnelles, vous pouvez filtrer, agréger et préparer des données de streaming avant de déplacer les données vers un évier de sortie.</span><span class="sxs-lookup"><span data-stu-id="dc811-124">Just like relational data, you can filter, aggregate, and prepare streaming data before moving the data to an output sink.</span></span> <span data-ttu-id="dc811-125">Apache Spark prend en charge [le traitement en temps réel du flux de données](/azure/architecture/data-guide/big-data/real-time-processing) via Spark [Streaming](https://spark.apache.org/streaming/).</span><span class="sxs-lookup"><span data-stu-id="dc811-125">Apache Spark supports [real-time data stream processing](/azure/architecture/data-guide/big-data/real-time-processing) through [Spark Streaming](https://spark.apache.org/streaming/).</span></span>

### <a name="batch-processing"></a><span data-ttu-id="dc811-126">Traitement par lots</span><span class="sxs-lookup"><span data-stu-id="dc811-126">Batch processing</span></span>

<span data-ttu-id="dc811-127">[Le traitement par lots](/azure/architecture/data-guide/big-data/batch-processing) est le traitement des données volumineuses au repos.</span><span class="sxs-lookup"><span data-stu-id="dc811-127">[Batch processing](/azure/architecture/data-guide/big-data/batch-processing) is the processing of big data at rest.</span></span> <span data-ttu-id="dc811-128">Vous pouvez filtrer, agréger et préparer de très grands ensembles de données en utilisant des travaux de longue durée en parallèle.</span><span class="sxs-lookup"><span data-stu-id="dc811-128">You can filter, aggregate, and prepare very large datasets using long-running jobs in parallel.</span></span>

### <a name="machine-learning-through-mllib"></a><span data-ttu-id="dc811-129">Apprentissage automatique par MLlib</span><span class="sxs-lookup"><span data-stu-id="dc811-129">Machine learning through MLlib</span></span>

<span data-ttu-id="dc811-130">L’apprentissage automatique est utilisé pour des problèmes d’analyse avancés.</span><span class="sxs-lookup"><span data-stu-id="dc811-130">Machine learning is used for advanced analytical problems.</span></span> <span data-ttu-id="dc811-131">Votre ordinateur peut utiliser les données existantes pour prévoir ou prédire les comportements, les résultats et les tendances futurs.</span><span class="sxs-lookup"><span data-stu-id="dc811-131">Your computer can use existing data to forecast or predict future behaviors, outcomes, and trends.</span></span> <span data-ttu-id="dc811-132">La bibliothèque d’apprentissage automatique d’Apache Spark, [MLlib](https://spark.apache.org/mllib/), contient plusieurs algorithmes et utilitaires d’apprentissage automatique.</span><span class="sxs-lookup"><span data-stu-id="dc811-132">Apache Spark's machine learning library, [MLlib](https://spark.apache.org/mllib/), contains several machine learning algorithms and utilities.</span></span>

### <a name="graph-processing-through-graphx"></a><span data-ttu-id="dc811-133">Traitement graphique par GraphX</span><span class="sxs-lookup"><span data-stu-id="dc811-133">Graph processing through GraphX</span></span>

<span data-ttu-id="dc811-134">Un graphique est une collection de nœuds reliés par des bords.</span><span class="sxs-lookup"><span data-stu-id="dc811-134">A graph is a collection of nodes connected by edges.</span></span> <span data-ttu-id="dc811-135">Vous pouvez utiliser une base de données graphique si vous avez des données hiérarchielles ou des données avec des relations interconnectées.</span><span class="sxs-lookup"><span data-stu-id="dc811-135">You might use a graph database if you have hierarchial data or data with interconnected relationships.</span></span> <span data-ttu-id="dc811-136">Vous pouvez traiter ces données à l’aide de l’API [GraphX](https://spark.apache.org/graphx/) d’Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="dc811-136">You can process this data using Apache Spark's [GraphX](https://spark.apache.org/graphx/) API.</span></span>

### <a name="sql-and-structured-data-processing-with-spark-sql"></a><span data-ttu-id="dc811-137">SQL et traitement structuré des données avec Spark SQL</span><span class="sxs-lookup"><span data-stu-id="dc811-137">SQL and structured data processing with Spark SQL</span></span>

<span data-ttu-id="dc811-138">Si vous travaillez avec des données structurées (formatées), vous pouvez utiliser des requêtes SQL dans votre application Spark à l’aide [de Spark SQL](https://spark.apache.org/sql/).</span><span class="sxs-lookup"><span data-stu-id="dc811-138">If you're working with structured (formatted) data, you can use SQL queries in your Spark application using [Spark SQL](https://spark.apache.org/sql/).</span></span>

## <a name="apache-spark-architecture"></a><span data-ttu-id="dc811-139">Architecture Apache Spark</span><span class="sxs-lookup"><span data-stu-id="dc811-139">Apache Spark architecture</span></span>

<span data-ttu-id="dc811-140">Apache Spark, qui utilise l’architecture de maître/ouvrier, a trois composants principaux : le conducteur, les exécuteurs testamentaires et le gestionnaire de cluster.</span><span class="sxs-lookup"><span data-stu-id="dc811-140">Apache Spark, which uses the master/worker architecture, has three main components: the driver, executors, and cluster manager.</span></span>

![Architecture Apache Spark](media/spark-architecture.png)

### <a name="driver"></a><span data-ttu-id="dc811-142">Pilote</span><span class="sxs-lookup"><span data-stu-id="dc811-142">Driver</span></span>

<span data-ttu-id="dc811-143">Le pilote se compose de votre programme, comme une application de console C, et d’une session Spark.</span><span class="sxs-lookup"><span data-stu-id="dc811-143">The driver consists of your program, like a C# console app, and a Spark session.</span></span> <span data-ttu-id="dc811-144">La session Spark prend votre programme et le divise en tâches plus petites qui sont traitées par les exécuteurs testamentaires.</span><span class="sxs-lookup"><span data-stu-id="dc811-144">The Spark session takes your program and divides it into smaller tasks that are handled by the executors.</span></span>

### <a name="executors"></a><span data-ttu-id="dc811-145">Exécuteurs</span><span class="sxs-lookup"><span data-stu-id="dc811-145">Executors</span></span>

<span data-ttu-id="dc811-146">Chaque exécuteur testamentaire, ou nœud de travailleur, reçoit une tâche du conducteur et exécute cette tâche.</span><span class="sxs-lookup"><span data-stu-id="dc811-146">Each executor, or worker node, receives a task from the driver and executes that task.</span></span> <span data-ttu-id="dc811-147">Les exécuteurs résident sur une entité connue sous le nom de cluster.</span><span class="sxs-lookup"><span data-stu-id="dc811-147">The executors reside on an entity known as a cluster.</span></span>

### <a name="cluster-manager"></a><span data-ttu-id="dc811-148">Gestionnaire de cluster</span><span class="sxs-lookup"><span data-stu-id="dc811-148">Cluster manager</span></span>

<span data-ttu-id="dc811-149">Le gestionnaire du cluster communique avec le conducteur et les exécuteurs testamentaires pour :</span><span class="sxs-lookup"><span data-stu-id="dc811-149">The cluster manager communicates with both the driver and the executors to:</span></span>

* <span data-ttu-id="dc811-150">Gérer l’allocation des ressources</span><span class="sxs-lookup"><span data-stu-id="dc811-150">Manage resource allocation</span></span>
* <span data-ttu-id="dc811-151">Gérer la division des programmes</span><span class="sxs-lookup"><span data-stu-id="dc811-151">Manage program division</span></span>
* <span data-ttu-id="dc811-152">Gérer l’exécution du programme</span><span class="sxs-lookup"><span data-stu-id="dc811-152">Manage program execution</span></span>

## <a name="language-support"></a><span data-ttu-id="dc811-153">Support multilingue</span><span class="sxs-lookup"><span data-stu-id="dc811-153">Language support</span></span>

<span data-ttu-id="dc811-154">Apache Spark prend en charge les langages de programmation suivants :</span><span class="sxs-lookup"><span data-stu-id="dc811-154">Apache Spark supports the following programming languages:</span></span>

* <span data-ttu-id="dc811-155">Scala</span><span class="sxs-lookup"><span data-stu-id="dc811-155">Scala</span></span>
* <span data-ttu-id="dc811-156">Python</span><span class="sxs-lookup"><span data-stu-id="dc811-156">Python</span></span>
* <span data-ttu-id="dc811-157">Java</span><span class="sxs-lookup"><span data-stu-id="dc811-157">Java</span></span>
* <span data-ttu-id="dc811-158">SQL</span><span class="sxs-lookup"><span data-stu-id="dc811-158">SQL</span></span>
* <span data-ttu-id="dc811-159">R</span><span class="sxs-lookup"><span data-stu-id="dc811-159">R</span></span>
* <span data-ttu-id="dc811-160">.NET</span><span class="sxs-lookup"><span data-stu-id="dc811-160">.NET</span></span>

## <a name="spark-apis"></a><span data-ttu-id="dc811-161">Spark API</span><span class="sxs-lookup"><span data-stu-id="dc811-161">Spark APIs</span></span>

<span data-ttu-id="dc811-162">Apache Spark prend en charge les API suivantes :</span><span class="sxs-lookup"><span data-stu-id="dc811-162">Apache Spark supports the following APIs:</span></span>

* [<span data-ttu-id="dc811-163">Spark Scala API</span><span class="sxs-lookup"><span data-stu-id="dc811-163">Spark Scala API</span></span>](https://spark.apache.org/docs/2.2.0/api/scala/index.html)
* [<span data-ttu-id="dc811-164">Spark Java API</span><span class="sxs-lookup"><span data-stu-id="dc811-164">Spark Java API</span></span>](https://spark.apache.org/docs/2.2.0/api/java/index.html)
* [<span data-ttu-id="dc811-165">Spark Python API</span><span class="sxs-lookup"><span data-stu-id="dc811-165">Spark Python API</span></span>](https://spark.apache.org/docs/2.2.0/api/python/index.html)
* [<span data-ttu-id="dc811-166">Spark R API</span><span class="sxs-lookup"><span data-stu-id="dc811-166">Spark R API</span></span>](https://spark.apache.org/docs/2.2.0/api/R/index.html)
* <span data-ttu-id="dc811-167">[Spark SQL](https://spark.apache.org/docs/latest/api/sql/index.html), fonctions intégrées</span><span class="sxs-lookup"><span data-stu-id="dc811-167">[Spark SQL](https://spark.apache.org/docs/latest/api/sql/index.html), built-in functions</span></span>

## <a name="next-steps"></a><span data-ttu-id="dc811-168">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="dc811-168">Next steps</span></span>

<span data-ttu-id="dc811-169">Découvrez comment vous pouvez utiliser Apache Spark dans votre application .NET.</span><span class="sxs-lookup"><span data-stu-id="dc811-169">Learn how you can use Apache Spark in your .NET application.</span></span> <span data-ttu-id="dc811-170">Avec .NET pour Apache Spark, les développeurs avec l’expérience .NET et la logique d’affaires peuvent écrire des requêtes big data dans C et F.</span><span class="sxs-lookup"><span data-stu-id="dc811-170">With .NET for Apache Spark, developers with .NET experience and business logic can write big data queries in C# and F#.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="dc811-171">Qu’est-ce que .NET pour Apache Spark</span><span class="sxs-lookup"><span data-stu-id="dc811-171">What is .NET for Apache Spark</span></span>](what-is-apache-spark-dotnet.md)
