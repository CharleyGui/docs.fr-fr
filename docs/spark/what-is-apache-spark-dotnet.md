---
title: Qu’est-ce que .NET pour Apache Spark ?
description: Découvrez .NET pour Apache Spark, un framework d’analytique Big Data gratuit, open source et multiplateforme, qui prend Spark partout où vous écrivez du code .NET.
author: mamccrea
ms.topic: overview
ms.date: 10/15/2019
ms.openlocfilehash: 12fccd478cedaccf455043feb3afa7b12221bf0e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73458205"
---
# <a name="what-is-net-for-apache-spark"></a><span data-ttu-id="36053-103">Qu’est-ce que .NET pour Apache Spark ?</span><span class="sxs-lookup"><span data-stu-id="36053-103">What is .NET for Apache Spark?</span></span>

<span data-ttu-id="36053-104">[Apache Spark](what-is-spark.md) est un moteur de traitement distribué à usage général pour l’analyse sur les grands ensembles de données - généralement des téraoctets ou des pétaoctets de données.</span><span class="sxs-lookup"><span data-stu-id="36053-104">[Apache Spark](what-is-spark.md) is a general-purpose distributed processing engine for analytics over large data sets - typically terabytes or petabytes of data.</span></span> <span data-ttu-id="36053-105">Avec .NET pour Apache Spark, le support gratuit, open-source et multi-plateforme .NET pour le cadre d’analyse de big data open-source populaire, vous pouvez maintenant ajouter la puissance d’Apache Spark à vos applications Big Data en utilisant des langues que vous connaissez déjà.</span><span class="sxs-lookup"><span data-stu-id="36053-105">With .NET for Apache Spark, the free, open-source, and cross-platform .NET Support for the popular open-source big data analytics framework, you can now add the power of Apache Spark to your big data applications using languages you already know.</span></span>

## <a name="why-choose-net-for-apache-spark"></a><span data-ttu-id="36053-106">Pourquoi choisir .NET pour Apache Spark?</span><span class="sxs-lookup"><span data-stu-id="36053-106">Why choose .NET for Apache Spark?</span></span>

<span data-ttu-id="36053-107">.NET pour Apache Spark permet aux développeurs avec une expérience .NET ou des bases de code de participer dans le monde de l’analyse des données volumineuses.</span><span class="sxs-lookup"><span data-stu-id="36053-107">.NET for Apache Spark empowers developers with .NET experience or code bases to participate in the world of big data analytics.</span></span> <span data-ttu-id="36053-108">.NET pour Apache Spark fournit des API de haute performance pour l’utilisation de Spark à partir de C et F.</span><span class="sxs-lookup"><span data-stu-id="36053-108">.NET for Apache Spark provides high performance APIs for using Spark from C# and F#.</span></span> <span data-ttu-id="36053-109">Avec C# et F#, vous pouvez accéder aux éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="36053-109">With C# and F#, you can access:</span></span>

* <span data-ttu-id="36053-110">DataFrame et SparkSQL pour travailler avec des données structurées.</span><span class="sxs-lookup"><span data-stu-id="36053-110">DataFrame and SparkSQL for working with structured data.</span></span>
* <span data-ttu-id="36053-111">Spark Structured Streaming pour l’utilisation de données en streaming.</span><span class="sxs-lookup"><span data-stu-id="36053-111">Spark Structured Streaming for working with streaming data.</span></span>
* <span data-ttu-id="36053-112">Spark SQL pour l’écriture de requêtes avec syntaxe SQL.</span><span class="sxs-lookup"><span data-stu-id="36053-112">Spark SQL for writing queries with SQL syntax.</span></span>
* <span data-ttu-id="36053-113">Intégration d’apprentissage automatique pour une formation et une prédiction plus rapides (c’est-à-dire, utilisez .NET pour Apache Spark aux côtés [de ML.NET).](https://dot.net/ml)</span><span class="sxs-lookup"><span data-stu-id="36053-113">Machine learning integration for faster training and prediction (that is, use .NET for Apache Spark alongside [ML.NET](https://dot.net/ml)).</span></span>

<span data-ttu-id="36053-114">.NET pour Apache Spark est conforme à .NET Standard, une spécification formelle des API .NET qui sont communes aux implémentations de .NET.</span><span class="sxs-lookup"><span data-stu-id="36053-114">.NET for Apache Spark is compliant with .NET Standard, a formal specification of .NET APIs that are common across .NET implementations.</span></span> <span data-ttu-id="36053-115">Cela signifie que vous pouvez utiliser .NET pour Apache Spark partout où vous écrivez du code .NET, ce qui vous permet de réutiliser l’ensemble des connaissances, des compétences, du code et des bibliothèques dont vous disposez déjà en tant que développeur .NET.</span><span class="sxs-lookup"><span data-stu-id="36053-115">This means you can use .NET for Apache Spark anywhere you write .NET code allowing you to reuse all the knowledge, skills, code, and libraries you already have as a .NET developer.</span></span>

<span data-ttu-id="36053-116">.NET pour Apache Spark s’exécute sur Windows, Linux et macOS avec .NET Core.</span><span class="sxs-lookup"><span data-stu-id="36053-116">.NET for Apache Spark runs on Windows, Linux, and macOS using .NET Core.</span></span> <span data-ttu-id="36053-117">Il s’exécute également sur Windows avec le .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="36053-117">It also runs on Windows using .NET Framework.</span></span> <span data-ttu-id="36053-118">Vous pouvez déployer vos applications sur tous les principaux fournisseurs cloud, notamment Azure HDInsight Spark, Amazon EMR Spark, Azure Databricks et Databricks sur AWS.</span><span class="sxs-lookup"><span data-stu-id="36053-118">You can deploy your applications to all major cloud providers including Azure HDInsight Spark, Amazon EMR Spark, Azure Databricks, and Databricks on AWS.</span></span>

## <a name="net-for-apache-spark-architecture"></a><span data-ttu-id="36053-119">.NET pour l’architecture Apache Spark</span><span class="sxs-lookup"><span data-stu-id="36053-119">.NET for Apache Spark architecture</span></span>

<span data-ttu-id="36053-120">La liaison linguistique C/F à Spark est écrite sur une nouvelle couche d’interop Spark qui offre une plus grande extensibility.</span><span class="sxs-lookup"><span data-stu-id="36053-120">The C#/ F# language binding to Spark is written on a new Spark interop layer which offers easier extensibility.</span></span> <span data-ttu-id="36053-121">Cette nouvelle couche d’interop Spark a été écrite en utilisant les meilleures pratiques pour l’extension de la langue et optimise pour l’interop et la performance.</span><span class="sxs-lookup"><span data-stu-id="36053-121">This new layer of Spark interop was written using the best practices for language extension and optimizes for interop and performance.</span></span> <span data-ttu-id="36053-122">À long terme, cette extensibility peut être utilisée pour ajouter un soutien pour d’autres langues dans Spark.</span><span class="sxs-lookup"><span data-stu-id="36053-122">Long term, this extensibility can be used for adding support for other languages in Spark.</span></span>

> [!div class="mx-imgBorder"]
> <span data-ttu-id="36053-123">![.NET pour l’architecture Apache Spark](media/dotnet-spark-architecture.png)</span><span class="sxs-lookup"><span data-stu-id="36053-123">![.NET for Apache Spark architecture](media/dotnet-spark-architecture.png)</span></span>

<span data-ttu-id="36053-124">Vous pouvez en apprendre davantage sur le soutien interop pour les extensions de langage Spark de [la proposition](https://issues.apache.org/jira/browse/SPARK-26257).</span><span class="sxs-lookup"><span data-stu-id="36053-124">You can learn about interop support for Spark language extensions from [the proposal](https://issues.apache.org/jira/browse/SPARK-26257).</span></span>

## <a name="net-for-apache-spark-performance"></a><span data-ttu-id="36053-125">.NET pour Apache Spark performance</span><span class="sxs-lookup"><span data-stu-id="36053-125">.NET for Apache Spark performance</span></span>

<span data-ttu-id="36053-126">Par rapport à Python et Scala en utilisant le [point de repère TPC-H](http://www.tpc.org/tpch/), .NET pour Apache Spark fonctionne bien dans la plupart des cas et est 2x plus rapide que Python lorsque les performances de fonction définies par l’utilisateur est critique.</span><span class="sxs-lookup"><span data-stu-id="36053-126">When compared against Python and Scala using the [TPC-H benchmark](http://www.tpc.org/tpch/), .NET for Apache Spark performs well in most cases and is 2x faster than Python when user-defined function performance is critical.</span></span> <span data-ttu-id="36053-127">Il y a un effort continu pour améliorer et évaluer le rendement.</span><span class="sxs-lookup"><span data-stu-id="36053-127">There is an ongoing effort to improve and benchmark performance.</span></span>

<span data-ttu-id="36053-128">Pour faire votre propre benchmarking, voir les repères disponibles sur le [.NET pour Apache Spark GitHub](https://github.com/dotnet/spark/tree/master/benchmark).</span><span class="sxs-lookup"><span data-stu-id="36053-128">To do your own benchmarking, see the benchmarks available on the [.NET for Apache Spark GitHub](https://github.com/dotnet/spark/tree/master/benchmark).</span></span>

## <a name="net-for-apache-spark-roadmap"></a><span data-ttu-id="36053-129">.NET pour apache Spark feuille de route</span><span class="sxs-lookup"><span data-stu-id="36053-129">.NET for Apache Spark roadmap</span></span>

<span data-ttu-id="36053-130">En savoir plus sur les plans à court et à long terme de la feuille de route officielle [.NET pour Apache Spark](https://github.com/dotnet/spark/blob/master/ROADMAP.md).</span><span class="sxs-lookup"><span data-stu-id="36053-130">Learn about short term and long term plans from the official [.NET for Apache Spark roadmap](https://github.com/dotnet/spark/blob/master/ROADMAP.md).</span></span>

## <a name="net-foundation"></a><span data-ttu-id="36053-131">.NET Foundation</span><span class="sxs-lookup"><span data-stu-id="36053-131">.NET Foundation</span></span>

<span data-ttu-id="36053-132">Le projet .NET pour Apache Spark fait partie de [.NET Foundation](https://www.dotnetfoundation.org/).</span><span class="sxs-lookup"><span data-stu-id="36053-132">The .NET for Apache Spark project is part of the [.NET Foundation](https://www.dotnetfoundation.org/).</span></span>

## <a name="contributions"></a><span data-ttu-id="36053-133">Contributions</span><span class="sxs-lookup"><span data-stu-id="36053-133">Contributions</span></span>

<span data-ttu-id="36053-134">L’équipe .NET pour Apache Spark encourage les contributions, à la fois sous la forme de problèmes et de demandes de tirage (pull requests) GitHub.</span><span class="sxs-lookup"><span data-stu-id="36053-134">The .NET for Apache Spark team encourages contributions, both GitHub issues and pull requests.</span></span> <span data-ttu-id="36053-135">Recherchez d’abord un [problème existant](https://github.com/dotnet/spark/issues).</span><span class="sxs-lookup"><span data-stu-id="36053-135">First, look for an [existing issue](https://github.com/dotnet/spark/issues).</span></span> <span data-ttu-id="36053-136">Si vous ne trouvez pas de problème existant, [ouvrez un nouveau problème](https://github.com/dotnet/spark/issues?utf8=%E2%9C%93&q=is%3Aissue+is%3Aopen+).</span><span class="sxs-lookup"><span data-stu-id="36053-136">If you can't find an existing issue, [open a new issue](https://github.com/dotnet/spark/issues?utf8=%E2%9C%93&q=is%3Aissue+is%3Aopen+).</span></span>

## <a name="next-steps"></a><span data-ttu-id="36053-137">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="36053-137">Next steps</span></span>

<span data-ttu-id="36053-138">Essayez .NET pour Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="36053-138">Try .NET for Apache Spark.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="36053-139">Tutorial: Démarrer avec .NET pour Apache Spark</span><span class="sxs-lookup"><span data-stu-id="36053-139">Tutorial: Get started with .NET for Apache Spark</span></span>](./tutorials/get-started.md)
