---
title: Qu’est-ce que .NET pour Apache Spark ?
description: Découvrez .NET pour Apache Spark, un framework d’analytique Big Data gratuit, open source et multiplateforme, qui prend Spark partout où vous écrivez du code .NET.
author: mamccrea
ms.topic: overview
ms.date: 10/09/2020
ms.openlocfilehash: 533a4d3b497ad499edcf3accf250477c03f98714
ms.sourcegitcommit: 34968a61e9bac0f6be23ed6ffb837f52d2390c85
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94688031"
---
# <a name="what-is-net-for-apache-spark"></a><span data-ttu-id="60507-103">Qu’est-ce que .NET pour Apache Spark ?</span><span class="sxs-lookup"><span data-stu-id="60507-103">What is .NET for Apache Spark?</span></span>

<span data-ttu-id="60507-104">[Apache Spark](what-is-spark.md) est un moteur de traitement distribué à usage général pour l’analyse de jeux de données volumineux, généralement des téraoctets ou des pétaoctets de données.</span><span class="sxs-lookup"><span data-stu-id="60507-104">[Apache Spark](what-is-spark.md) is a general-purpose distributed processing engine for analytics over large data sets - typically terabytes or petabytes of data.</span></span> <span data-ttu-id="60507-105">Avec .NET pour Apache Spark, la prise en charge libre, [Open source](https://github.com/dotnet/spark)et multiplateforme de .net pour l’infrastructure open source Big Data Analytics populaire, vous pouvez désormais ajouter la puissance de Apache Spark à vos applications Big Data à l’aide de langages que vous connaissez déjà.</span><span class="sxs-lookup"><span data-stu-id="60507-105">With .NET for Apache Spark, the free, [open-source](https://github.com/dotnet/spark), and cross-platform .NET Support for the popular open-source big data analytics framework, you can now add the power of Apache Spark to your big data applications using languages you already know.</span></span>

## <a name="why-choose-net-for-apache-spark"></a><span data-ttu-id="60507-106">Pourquoi choisir .NET pour la Apache Spark ?</span><span class="sxs-lookup"><span data-stu-id="60507-106">Why choose .NET for Apache Spark?</span></span>

<span data-ttu-id="60507-107">.NET pour Apache Spark offre aux développeurs une expérience .NET ou des bases de code pour participer au monde de Big Data Analytics.</span><span class="sxs-lookup"><span data-stu-id="60507-107">.NET for Apache Spark empowers developers with .NET experience or code bases to participate in the world of big data analytics.</span></span> <span data-ttu-id="60507-108">.NET pour Apache Spark fournit des API haute performance pour l’utilisation de Spark à partir de C# et de F #.</span><span class="sxs-lookup"><span data-stu-id="60507-108">.NET for Apache Spark provides high performance APIs for using Spark from C# and F#.</span></span> <span data-ttu-id="60507-109">Avec C# et F#, vous pouvez accéder aux éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="60507-109">With C# and F#, you can access:</span></span>

* <span data-ttu-id="60507-110">Tableau et SparkSQL pour l’utilisation de données structurées.</span><span class="sxs-lookup"><span data-stu-id="60507-110">DataFrame and SparkSQL for working with structured data.</span></span>
* <span data-ttu-id="60507-111">Spark Structured Streaming pour l’utilisation de données en streaming.</span><span class="sxs-lookup"><span data-stu-id="60507-111">Spark Structured Streaming for working with streaming data.</span></span>
* <span data-ttu-id="60507-112">Spark SQL pour l’écriture de requêtes avec la syntaxe SQL.</span><span class="sxs-lookup"><span data-stu-id="60507-112">Spark SQL for writing queries with SQL syntax.</span></span>
* <span data-ttu-id="60507-113">Intégration de machine learning pour une formation et une prédiction plus rapides (autrement dit, utilisez .NET pour Apache Spark avec [ml.net](https://dot.net/ml)).</span><span class="sxs-lookup"><span data-stu-id="60507-113">Machine learning integration for faster training and prediction (that is, use .NET for Apache Spark alongside [ML.NET](https://dot.net/ml)).</span></span>

<span data-ttu-id="60507-114">.NET pour Apache Spark est conforme à .NET Standard, une spécification formelle des API .NET qui sont communes aux implémentations de .NET.</span><span class="sxs-lookup"><span data-stu-id="60507-114">.NET for Apache Spark is compliant with .NET Standard, a formal specification of .NET APIs that are common across .NET implementations.</span></span> <span data-ttu-id="60507-115">Cela signifie que vous pouvez utiliser .NET pour Apache Spark partout où vous écrivez du code .NET, ce qui vous permet de réutiliser l’ensemble des connaissances, des compétences, du code et des bibliothèques dont vous disposez déjà en tant que développeur .NET.</span><span class="sxs-lookup"><span data-stu-id="60507-115">This means you can use .NET for Apache Spark anywhere you write .NET code allowing you to reuse all the knowledge, skills, code, and libraries you already have as a .NET developer.</span></span>

<span data-ttu-id="60507-116">.NET pour Apache Spark s’exécute sur Windows, Linux et macOS avec .NET Core.</span><span class="sxs-lookup"><span data-stu-id="60507-116">.NET for Apache Spark runs on Windows, Linux, and macOS using .NET Core.</span></span> <span data-ttu-id="60507-117">Il s’exécute également sur Windows avec le .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="60507-117">It also runs on Windows using .NET Framework.</span></span> <span data-ttu-id="60507-118">Vous pouvez déployer vos applications sur tous les principaux fournisseurs cloud, notamment Azure HDInsight Spark, Amazon EMR Spark, Azure Databricks et Databricks sur AWS.</span><span class="sxs-lookup"><span data-stu-id="60507-118">You can deploy your applications to all major cloud providers including Azure HDInsight Spark, Amazon EMR Spark, Azure Databricks, and Databricks on AWS.</span></span>

## <a name="net-for-apache-spark-architecture"></a><span data-ttu-id="60507-119">Architecture .NET pour Apache Spark</span><span class="sxs-lookup"><span data-stu-id="60507-119">.NET for Apache Spark architecture</span></span>

<span data-ttu-id="60507-120">La liaison de langage C#/F # à Spark est écrite sur une nouvelle couche d’interopérabilité Spark qui offre une extensibilité plus facile.</span><span class="sxs-lookup"><span data-stu-id="60507-120">The C#/ F# language binding to Spark is written on a new Spark interop layer which offers easier extensibility.</span></span> <span data-ttu-id="60507-121">Cette nouvelle couche de l’interopérabilité Spark a été écrite à l’aide des meilleures pratiques pour l’extension de langage et optimise l’interopérabilité et les performances.</span><span class="sxs-lookup"><span data-stu-id="60507-121">This new layer of Spark interop was written using the best practices for language extension and optimizes for interop and performance.</span></span> <span data-ttu-id="60507-122">À long terme, cette extensibilité peut être utilisée pour ajouter la prise en charge d’autres langues dans Spark.</span><span class="sxs-lookup"><span data-stu-id="60507-122">Long term, this extensibility can be used for adding support for other languages in Spark.</span></span>

> [!div class="mx-imgBorder"]
> <span data-ttu-id="60507-123">![Architecture .NET pour Apache Spark](media/dotnet-spark-architecture.png)</span><span class="sxs-lookup"><span data-stu-id="60507-123">![.NET for Apache Spark architecture](media/dotnet-spark-architecture.png)</span></span>

<span data-ttu-id="60507-124">Vous pouvez en savoir plus sur la prise en charge de l’interopérabilité pour les extensions de langage Spark à partir de [la proposition](https://issues.apache.org/jira/browse/SPARK-26257).</span><span class="sxs-lookup"><span data-stu-id="60507-124">You can learn about interop support for Spark language extensions from [the proposal](https://issues.apache.org/jira/browse/SPARK-26257).</span></span>

## <a name="net-for-apache-spark-performance"></a><span data-ttu-id="60507-125">.NET pour les performances de Apache Spark</span><span class="sxs-lookup"><span data-stu-id="60507-125">.NET for Apache Spark performance</span></span>

<span data-ttu-id="60507-126">En comparaison avec Python et Scala à l’aide du [test TPC-H](http://www.tpc.org/tpch/), .net pour Apache Spark fonctionne bien dans la plupart des cas et est 2x plus rapide que Python lorsque les performances des fonctions définies par l’utilisateur sont critiques.</span><span class="sxs-lookup"><span data-stu-id="60507-126">When compared against Python and Scala using the [TPC-H benchmark](http://www.tpc.org/tpch/), .NET for Apache Spark performs well in most cases and is 2x faster than Python when user-defined function performance is critical.</span></span> <span data-ttu-id="60507-127">Il existe un effort permanent pour améliorer et tester les performances.</span><span class="sxs-lookup"><span data-stu-id="60507-127">There is an ongoing effort to improve and benchmark performance.</span></span>

<span data-ttu-id="60507-128">Pour effectuer votre propre évaluation, consultez les bancs d’essai disponibles sur le [.net pour Apache Spark GitHub](https://github.com/dotnet/spark/tree/master/benchmark).</span><span class="sxs-lookup"><span data-stu-id="60507-128">To do your own benchmarking, see the benchmarks available on the [.NET for Apache Spark GitHub](https://github.com/dotnet/spark/tree/master/benchmark).</span></span>

## <a name="net-for-apache-spark-roadmap"></a><span data-ttu-id="60507-129">Feuille de route de .NET pour Apache Spark</span><span class="sxs-lookup"><span data-stu-id="60507-129">.NET for Apache Spark roadmap</span></span>

<span data-ttu-id="60507-130">En savoir plus sur les plans à long terme et à long terme de la feuille [de route officielle .net pour Apache Spark](https://github.com/dotnet/spark/blob/master/ROADMAP.md).</span><span class="sxs-lookup"><span data-stu-id="60507-130">Learn about short term and long term plans from the official [.NET for Apache Spark roadmap](https://github.com/dotnet/spark/blob/master/ROADMAP.md).</span></span>

## <a name="net-foundation"></a><span data-ttu-id="60507-131">.NET Foundation</span><span class="sxs-lookup"><span data-stu-id="60507-131">.NET Foundation</span></span>

<span data-ttu-id="60507-132">Le projet .NET pour Apache Spark fait partie de [.NET Foundation](https://www.dotnetfoundation.org/).</span><span class="sxs-lookup"><span data-stu-id="60507-132">The .NET for Apache Spark project is part of the [.NET Foundation](https://www.dotnetfoundation.org/).</span></span>

## <a name="contributions"></a><span data-ttu-id="60507-133">Contributions</span><span class="sxs-lookup"><span data-stu-id="60507-133">Contributions</span></span>

<span data-ttu-id="60507-134">L’équipe .NET pour Apache Spark encourage les contributions, à la fois sous la forme de problèmes et de demandes de tirage (pull requests) GitHub.</span><span class="sxs-lookup"><span data-stu-id="60507-134">The .NET for Apache Spark team encourages contributions, both GitHub issues and pull requests.</span></span> <span data-ttu-id="60507-135">Recherchez d’abord un [problème existant](https://github.com/dotnet/spark/issues).</span><span class="sxs-lookup"><span data-stu-id="60507-135">First, look for an [existing issue](https://github.com/dotnet/spark/issues).</span></span> <span data-ttu-id="60507-136">Si vous ne trouvez pas de problème existant, [ouvrez un nouveau problème](https://github.com/dotnet/spark/issues?utf8=%E2%9C%93&q=is%3Aissue+is%3Aopen+).</span><span class="sxs-lookup"><span data-stu-id="60507-136">If you can't find an existing issue, [open a new issue](https://github.com/dotnet/spark/issues?utf8=%E2%9C%93&q=is%3Aissue+is%3Aopen+).</span></span>

## <a name="next-steps"></a><span data-ttu-id="60507-137">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="60507-137">Next steps</span></span>

<span data-ttu-id="60507-138">Essayez .NET pour Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="60507-138">Try .NET for Apache Spark.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="60507-139">Didacticiel : prise en main de .NET pour Apache Spark</span><span class="sxs-lookup"><span data-stu-id="60507-139">Tutorial: Get started with .NET for Apache Spark</span></span>](./tutorials/get-started.md)
