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
# <a name="what-is-net-for-apache-spark"></a>Qu’est-ce que .NET pour Apache Spark ?

[Apache Spark](what-is-spark.md) est un moteur de traitement distribué à usage général pour l’analyse sur les grands ensembles de données - généralement des téraoctets ou des pétaoctets de données. Avec .NET pour Apache Spark, le support gratuit, open-source et multi-plateforme .NET pour le cadre d’analyse de big data open-source populaire, vous pouvez maintenant ajouter la puissance d’Apache Spark à vos applications Big Data en utilisant des langues que vous connaissez déjà.

## <a name="why-choose-net-for-apache-spark"></a>Pourquoi choisir .NET pour Apache Spark?

.NET pour Apache Spark permet aux développeurs avec une expérience .NET ou des bases de code de participer dans le monde de l’analyse des données volumineuses. .NET pour Apache Spark fournit des API de haute performance pour l’utilisation de Spark à partir de C et F. Avec C# et F#, vous pouvez accéder aux éléments suivants :

* DataFrame et SparkSQL pour travailler avec des données structurées.
* Spark Structured Streaming pour l’utilisation de données en streaming.
* Spark SQL pour l’écriture de requêtes avec syntaxe SQL.
* Intégration d’apprentissage automatique pour une formation et une prédiction plus rapides (c’est-à-dire, utilisez .NET pour Apache Spark aux côtés [de ML.NET).](https://dot.net/ml)

.NET pour Apache Spark est conforme à .NET Standard, une spécification formelle des API .NET qui sont communes aux implémentations de .NET. Cela signifie que vous pouvez utiliser .NET pour Apache Spark partout où vous écrivez du code .NET, ce qui vous permet de réutiliser l’ensemble des connaissances, des compétences, du code et des bibliothèques dont vous disposez déjà en tant que développeur .NET.

.NET pour Apache Spark s’exécute sur Windows, Linux et macOS avec .NET Core. Il s’exécute également sur Windows avec le .NET Framework. Vous pouvez déployer vos applications sur tous les principaux fournisseurs cloud, notamment Azure HDInsight Spark, Amazon EMR Spark, Azure Databricks et Databricks sur AWS.

## <a name="net-for-apache-spark-architecture"></a>.NET pour l’architecture Apache Spark

La liaison linguistique C/F à Spark est écrite sur une nouvelle couche d’interop Spark qui offre une plus grande extensibility. Cette nouvelle couche d’interop Spark a été écrite en utilisant les meilleures pratiques pour l’extension de la langue et optimise pour l’interop et la performance. À long terme, cette extensibility peut être utilisée pour ajouter un soutien pour d’autres langues dans Spark.

> [!div class="mx-imgBorder"]
> ![.NET pour l’architecture Apache Spark](media/dotnet-spark-architecture.png)

Vous pouvez en apprendre davantage sur le soutien interop pour les extensions de langage Spark de [la proposition](https://issues.apache.org/jira/browse/SPARK-26257).

## <a name="net-for-apache-spark-performance"></a>.NET pour Apache Spark performance

Par rapport à Python et Scala en utilisant le [point de repère TPC-H](http://www.tpc.org/tpch/), .NET pour Apache Spark fonctionne bien dans la plupart des cas et est 2x plus rapide que Python lorsque les performances de fonction définies par l’utilisateur est critique. Il y a un effort continu pour améliorer et évaluer le rendement.

Pour faire votre propre benchmarking, voir les repères disponibles sur le [.NET pour Apache Spark GitHub](https://github.com/dotnet/spark/tree/master/benchmark).

## <a name="net-for-apache-spark-roadmap"></a>.NET pour apache Spark feuille de route

En savoir plus sur les plans à court et à long terme de la feuille de route officielle [.NET pour Apache Spark](https://github.com/dotnet/spark/blob/master/ROADMAP.md).

## <a name="net-foundation"></a>.NET Foundation

Le projet .NET pour Apache Spark fait partie de [.NET Foundation](https://www.dotnetfoundation.org/).

## <a name="contributions"></a>Contributions

L’équipe .NET pour Apache Spark encourage les contributions, à la fois sous la forme de problèmes et de demandes de tirage (pull requests) GitHub. Recherchez d’abord un [problème existant](https://github.com/dotnet/spark/issues). Si vous ne trouvez pas de problème existant, [ouvrez un nouveau problème](https://github.com/dotnet/spark/issues?utf8=%E2%9C%93&q=is%3Aissue+is%3Aopen+).

## <a name="next-steps"></a>Étapes suivantes

Essayez .NET pour Apache Spark.
> [!div class="nextstepaction"]
> [Tutorial: Démarrer avec .NET pour Apache Spark](./tutorials/get-started.md)
