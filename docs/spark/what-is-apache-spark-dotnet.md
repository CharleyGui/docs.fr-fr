---
title: Qu’est-ce que .NET pour Apache Spark ?
description: Découvrez .NET pour Apache Spark, un framework d’analytique Big Data gratuit, open source et multiplateforme, qui prend Spark partout où vous écrivez du code .NET.
author: mamccrea
ms.topic: overview
ms.date: 10/15/2019
ms.openlocfilehash: c31b50a20ac08bcde077e1e85ee915435a99fc28
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395873"
---
# <a name="what-is-net-for-apache-spark"></a>Qu’est-ce que .NET pour Apache Spark ?

[Apache Spark](what-is-spark.md) est un moteur de traitement distribué à usage général pour l’analyse de jeux de données volumineux, généralement des téraoctets ou des pétaoctets de données. Avec .NET pour Apache Spark, la prise en charge libre, open source et multiplateforme de .NET pour l’infrastructure Open source Big Data Analytics populaire, vous pouvez désormais ajouter la puissance de Apache Spark à vos applications Big Data à l’aide de langages que vous connaissez déjà.

## <a name="why-choose-net-for-apache-spark"></a>Pourquoi choisir .NET pour la Apache Spark ?

.NET pour Apache Spark offre aux développeurs une expérience .NET ou des bases de code pour participer au monde de Big Data Analytics. .NET pour Apache Spark fournit des API haute performance pour l’utilisation C# de F#Spark à partir de et. Avec C# et F#, vous pouvez accéder aux éléments suivants :

* Tableau et SparkSQL pour l’utilisation de données structurées
* Spark Structured streaming pour travailler avec des données de streaming
* Spark SQL pour l’écriture de requêtes avec la syntaxe SQL
* Intégration de machine learning pour une formation et une prédiction plus rapides (par exemple, utilisation de .NET pour Apache Spark avec [ml.net](http://dot.net/ml))

.NET pour Apache Spark est conforme à .NET Standard, une spécification formelle des API .NET qui sont communes aux implémentations de .NET. Cela signifie que vous pouvez utiliser .NET pour Apache Spark partout où vous écrivez du code .NET, ce qui vous permet de réutiliser l’ensemble des connaissances, des compétences, du code et des bibliothèques dont vous disposez déjà en tant que développeur .NET.

.NET pour Apache Spark s’exécute sur Windows, Linux et macOS avec .NET Core. Il s’exécute également sur Windows avec le .NET Framework. Vous pouvez déployer vos applications sur tous les principaux fournisseurs cloud, notamment Azure HDInsight Spark, Amazon EMR Spark, Azure Databricks et Databricks sur AWS.

## <a name="net-for-apache-spark-architecture"></a>Architecture .NET pour Apache Spark

La C#liaison F# /langue à Spark est écrite sur une nouvelle couche d’interopérabilité Spark qui offre une extensibilité plus facile. Cette nouvelle couche de l’interopérabilité Spark a été écrite à l’aide des meilleures pratiques pour l’extension de langage et optimise l’interopérabilité et les performances. À long terme, cette extensibilité peut être utilisée pour ajouter la prise en charge d’autres langues dans Spark.

> [!div class="mx-imgBorder"]
> ![.NET pour Apache Spark architecture @ no__t-1

Vous pouvez en savoir plus sur la prise en charge de l’interopérabilité pour les extensions de langage Spark à partir de [la proposition](https://issues.apache.org/jira/browse/SPARK-26257).

## <a name="net-for-apache-spark-performance"></a>.NET pour les performances de Apache Spark

En comparaison avec Python et Scala à l’aide du [test TPC-H](http://www.tpc.org/tpch/), .net pour Apache Spark fonctionne bien dans la plupart des cas et est 2x plus rapide que Python lorsque les performances des fonctions définies par l’utilisateur sont critiques. Il existe un effort permanent pour améliorer et tester les performances. 

Pour effectuer votre propre évaluation, consultez les bancs d’essai disponibles sur le [.net pour Apache Spark GitHub](https://github.com/dotnet/spark/tree/master/benchmark).

## <a name="net-for-apache-spark-roadmap"></a>Feuille de route de .NET pour Apache Spark

En savoir plus sur les plans à long terme et à long terme de la feuille [de route officielle .net pour Apache Spark](https://github.com/dotnet/spark/blob/master/ROADMAP.md).

## <a name="net-foundation"></a>.NET Foundation

Le projet .NET pour Apache Spark fait partie de [.NET Foundation](https://www.dotnetfoundation.org/).

## <a name="contributions"></a>Contributions

L’équipe .NET pour Apache Spark encourage les contributions, à la fois sous la forme de problèmes et de demandes de tirage (pull requests) GitHub. Recherchez d’abord un [problème existant](https://github.com/dotnet/spark/issues). Si vous ne trouvez pas de problème existant, [ouvrez un nouveau problème](https://github.com/dotnet/spark/issues?utf8=%E2%9C%93&q=is%3Aissue+is%3Aopen+).

## <a name="next-steps"></a>Étapes suivantes

Essayez .NET pour Apache Spark.
> [!div class="nextstepaction"]
> [Didacticiel : prise en main de .NET pour Apache Spark](./tutorials/get-started.md)
