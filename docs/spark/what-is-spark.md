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
# <a name="what-is-apache-spark"></a>Qu’est-ce qu’Apache Spark ?

[Apache Spark](https://spark.apache.org/) est un cadre de traitement parallèle open-source qui prend en charge le traitement de la mémoire pour augmenter les performances des applications qui analysent le Big Data. Les solutions Big Data sont conçues pour traiter des données trop grandes ou complexes pour les bases de données traditionnelles. Spark traite de grandes quantités de données dans la mémoire, ce qui est beaucoup plus rapide que les alternatives basées sur le disque.

## <a name="common-big-data-scenarios"></a>Scénarios communs de Big Data

Vous pouvez envisager une architecture big data si vous avez besoin de stocker et de traiter de grands volumes de données, de transformer des données non structurées ou de traiter les données de streaming. Spark est un moteur de traitement distribué à usage général qui peut être utilisé pour plusieurs scénarios big data.

### <a name="extract-transform-and-load-etl"></a>Extraire, transformer et charger (ETL)

[L’extraction,](/azure/architecture/data-guide/relational-data/etl) la transformation et la charge (ETL) sont le processus de collecte de données à partir d’une ou plusieurs sources, de modification des données et de transfert des données vers un nouveau magasin de données. Il existe plusieurs façons de transformer les données, notamment :

* Filtrage
* Tri
* Agrégation
* Jonction
* Nettoyage
* Déduplicating
* Validation

### <a name="real-time-data-stream-processing"></a>Traitement des flux de données en temps réel

Le streaming, ou en temps réel, les données sont des données en mouvement. La télémétrie des appareils IoT, des blogs et des flux de clics sont autant d’exemples de données de streaming. Les données en temps réel peuvent être traitées pour fournir des informations utiles, telles que l’analyse géospatiale, la surveillance à distance et la détection des anomalies. Tout comme les données relationnelles, vous pouvez filtrer, agréger et préparer des données de streaming avant de déplacer les données vers un évier de sortie. Apache Spark prend en charge [le traitement en temps réel du flux de données](/azure/architecture/data-guide/big-data/real-time-processing) via Spark [Streaming](https://spark.apache.org/streaming/).

### <a name="batch-processing"></a>Traitement par lots

[Le traitement par lots](/azure/architecture/data-guide/big-data/batch-processing) est le traitement des données volumineuses au repos. Vous pouvez filtrer, agréger et préparer de très grands ensembles de données en utilisant des travaux de longue durée en parallèle.

### <a name="machine-learning-through-mllib"></a>Apprentissage automatique par MLlib

L’apprentissage automatique est utilisé pour des problèmes d’analyse avancés. Votre ordinateur peut utiliser les données existantes pour prévoir ou prédire les comportements, les résultats et les tendances futurs. La bibliothèque d’apprentissage automatique d’Apache Spark, [MLlib](https://spark.apache.org/mllib/), contient plusieurs algorithmes et utilitaires d’apprentissage automatique.

### <a name="graph-processing-through-graphx"></a>Traitement graphique par GraphX

Un graphique est une collection de nœuds reliés par des bords. Vous pouvez utiliser une base de données graphique si vous avez des données hiérarchielles ou des données avec des relations interconnectées. Vous pouvez traiter ces données à l’aide de l’API [GraphX](https://spark.apache.org/graphx/) d’Apache Spark.

### <a name="sql-and-structured-data-processing-with-spark-sql"></a>SQL et traitement structuré des données avec Spark SQL

Si vous travaillez avec des données structurées (formatées), vous pouvez utiliser des requêtes SQL dans votre application Spark à l’aide [de Spark SQL](https://spark.apache.org/sql/).

## <a name="apache-spark-architecture"></a>Architecture Apache Spark

Apache Spark, qui utilise l’architecture de maître/ouvrier, a trois composants principaux : le conducteur, les exécuteurs testamentaires et le gestionnaire de cluster.

![Architecture Apache Spark](media/spark-architecture.png)

### <a name="driver"></a>Pilote

Le pilote se compose de votre programme, comme une application de console C, et d’une session Spark. La session Spark prend votre programme et le divise en tâches plus petites qui sont traitées par les exécuteurs testamentaires.

### <a name="executors"></a>Exécuteurs

Chaque exécuteur testamentaire, ou nœud de travailleur, reçoit une tâche du conducteur et exécute cette tâche. Les exécuteurs résident sur une entité connue sous le nom de cluster.

### <a name="cluster-manager"></a>Gestionnaire de cluster

Le gestionnaire du cluster communique avec le conducteur et les exécuteurs testamentaires pour :

* Gérer l’allocation des ressources
* Gérer la division des programmes
* Gérer l’exécution du programme

## <a name="language-support"></a>Support multilingue

Apache Spark prend en charge les langages de programmation suivants :

* Scala
* Python
* Java
* SQL
* R
* .NET

## <a name="spark-apis"></a>Spark API

Apache Spark prend en charge les API suivantes :

* [Spark Scala API](https://spark.apache.org/docs/2.2.0/api/scala/index.html)
* [Spark Java API](https://spark.apache.org/docs/2.2.0/api/java/index.html)
* [Spark Python API](https://spark.apache.org/docs/2.2.0/api/python/index.html)
* [Spark R API](https://spark.apache.org/docs/2.2.0/api/R/index.html)
* [Spark SQL](https://spark.apache.org/docs/latest/api/sql/index.html), fonctions intégrées

## <a name="next-steps"></a>Étapes suivantes

Découvrez comment vous pouvez utiliser Apache Spark dans votre application .NET. Avec .NET pour Apache Spark, les développeurs avec l’expérience .NET et la logique d’affaires peuvent écrire des requêtes big data dans C et F.
> [!div class="nextstepaction"]
> [Qu’est-ce que .NET pour Apache Spark](what-is-apache-spark-dotnet.md)
