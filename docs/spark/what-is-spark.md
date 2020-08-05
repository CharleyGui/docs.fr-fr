---
title: Qu’est-ce qu’Apache Spark ?
description: En savoir plus sur les scénarios de Apache Spark et de Big Data.
ms.date: 10/15/2019
ms.topic: conceptual
ms.custom: mvc
ms.openlocfilehash: cde66c4084b7c86e1b78d89c2bad94402dbd7d60
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87555992"
---
# <a name="what-is-apache-spark"></a>Qu’est-ce qu’Apache Spark ?

[Apache Spark](https://spark.apache.org/) est une infrastructure de traitement parallèle Open source qui prend en charge le traitement en mémoire pour améliorer les performances des applications qui analysent les Big Data. Les solutions Big Data sont conçues pour gérer les données qui sont trop volumineuses ou complexes pour les bases de données traditionnelles. Spark traite de grandes quantités de données en mémoire, ce qui est beaucoup plus rapide que les alternatives sur disque.

## <a name="common-big-data-scenarios"></a>Scénarios de Big Data courants

Vous pouvez envisager une architecture Big Data si vous avez besoin de stocker et traiter de gros volumes de données, de transformer des données non structurées ou de traiter des données de streaming. Spark est un moteur de traitement distribué à usage général qui peut être utilisé pour plusieurs scénarios de Big Data.

### <a name="extract-transform-and-load-etl"></a>Extraire, transformer et charger (ETL)

L' [extraction, la transformation et le chargement (ETL)](/azure/architecture/data-guide/relational-data/etl) est le processus qui consiste à collecter des données à partir d’une ou plusieurs sources, à modifier les données et à déplacer les données vers un nouveau magasin de données. Il existe plusieurs façons de transformer des données, notamment :

* Filtrage
* Tri
* Agrégation
* Jonction
* Infection
* Déduplication
* Validation

### <a name="real-time-data-stream-processing"></a>Traitement du flux de données en temps réel

Les données en continu ou en temps réel sont des données en mouvement. La télémétrie des appareils IoT, Weblogs et parcours sont des exemples de données de streaming. Les données en temps réel peuvent être traitées pour fournir des informations utiles, telles que l’analyse géographique, la surveillance à distance et la détection d’anomalies. Tout comme les données relationnelles, vous pouvez filtrer, agréger et préparer les données de diffusion en continu avant de déplacer les données vers un récepteur de sortie. Apache Spark prend en charge [le traitement des flux de données en temps réel](/azure/architecture/data-guide/big-data/real-time-processing) via [Spark streaming](https://spark.apache.org/streaming/).

### <a name="batch-processing"></a>Traitement par lots

Le [traitement par lots](/azure/architecture/data-guide/big-data/batch-processing) est le traitement de Big Data au repos. Vous pouvez filtrer, agréger et préparer des jeux de données très volumineux à l’aide de travaux de longue durée en parallèle.

### <a name="machine-learning-through-mllib"></a>Machine learning via MLlib

Machine Learning est utilisé pour les problèmes analytiques avancés. Votre ordinateur peut utiliser les données existantes pour prévoir ou prédire les comportements, les résultats et les tendances futurs. La bibliothèque de Machine Learning de Apache Spark, [MLlib](https://spark.apache.org/mllib/), contient plusieurs algorithmes et utilitaires de machine learning.

### <a name="graph-processing-through-graphx"></a>Traitement des graphiques via GraphX

Un graphique est une collection de nœuds connectés par des bords. Vous pouvez utiliser une base de données de graphiques si vous avez des données ou des données Hierarchial avec des relations interconnectées. Vous pouvez traiter ces données à l’aide de l’API [graphx](https://spark.apache.org/graphx/) de Apache Spark.

### <a name="sql-and-structured-data-processing-with-spark-sql"></a>SQL et traitement des données structurées avec Spark SQL

Si vous utilisez des données structurées (formatées), vous pouvez utiliser des requêtes SQL dans votre application Spark à l’aide de [Spark SQL](https://spark.apache.org/sql/).

## <a name="apache-spark-architecture"></a>Architecture Apache Spark

Apache Spark, qui utilise l’architecture maître/travail, a trois composants principaux : le pilote, les exécuteurs et le gestionnaire de cluster.

![Architecture Apache Spark](media/spark-architecture.png)

### <a name="driver"></a>Pilote

Le pilote est constitué de votre programme, par exemple une application console C# et une session Spark. La session Spark prend votre programme et le divise en tâches plus petites gérées par les exécuteurs.

### <a name="executors"></a>Exécuteurs

Chaque exécuteur, ou nœud de travail, reçoit une tâche du pilote et exécute cette tâche. Les exécuteurs résident sur une entité appelée cluster.

### <a name="cluster-manager"></a>Gestionnaire de cluster

Le gestionnaire de cluster communique avec le pilote et les exécuteurs pour :

* Gérer l’allocation des ressources
* Gérer la Division du programme
* Gérer l’exécution du programme

## <a name="language-support"></a>Support multilingue

Apache Spark prend en charge les langages de programmation suivants :

* Scala
* Python
* Java
* SQL
* R
* Langages .NET (C#/F #)

## <a name="spark-apis"></a>API Spark

Apache Spark prend en charge les API suivantes :

* [API Scala Spark](https://spark.apache.org/docs/2.2.0/api/scala/index.html)
* [API Java Spark](https://spark.apache.org/docs/2.2.0/api/java/index.html)
* [API Python Spark](https://spark.apache.org/docs/2.2.0/api/python/index.html)
* [API R Spark](https://spark.apache.org/docs/2.2.0/api/R/index.html)
* [Spark SQL](https://spark.apache.org/docs/latest/api/sql/index.html), fonctions intégrées

## <a name="next-steps"></a>Étapes suivantes

Découvrez comment vous pouvez utiliser Apache Spark dans votre application .NET. Avec .NET pour Apache Spark, les développeurs disposant d’une expérience .NET et d’une logique métier peuvent écrire des requêtes Big Data en C# et F #.
> [!div class="nextstepaction"]
> [Qu’est-ce que .NET pour Apache Spark](what-is-apache-spark-dotnet.md)
