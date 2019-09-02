---
title: Déboguer une application .NET pour Apache Spark sur Windows
description: Découvrez comment déboguer votre application .NET pour Apache Spark sur Windows.
ms.date: 08/15/2019
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: dcaca96f6eb871c15a37adc18190b073c63c8e93
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70206140"
---
# <a name="debug-a-net-for-apache-spark-application"></a>Déboguer une application .NET pour Apache Spark

Cette procédure indique les commandes que vous devez exécuter pour déboguer votre application .NET pour Apache Spark et du code Scala sur Windows.

## <a name="debug-your-application"></a>Déboguer votre application

Ouvrez une fenêtre d’invite de commandes et exécutez ceci :

```shell
spark-submit \
  --class org.apache.spark.deploy.dotnet.DotnetRunner \
  --master local \
  <path-to-microsoft-spark-jar> \
  debug
```

Quand vous exécutez la commande, vous voyez la sortie suivante :

```
***********************************************************************
* .NET Backend running debug mode. Press enter to exit *
***********************************************************************
```

Dans ce mode de débogage, `DotnetRunner` ne lance pas l’application .NET, mais attend qu’elle se connecte. Laissez ouverte la fenêtre d’invite de commandes.

Vous pouvez maintenant exécuter votre application .NET avec n’importe quel débogueur pour déboguer votre application.

## <a name="debug-scala-code"></a>Déboguer du code Scala

Si vous devez déboguer du code côté Scala, comme `DotnetRunner` ou `DotnetBackendHandler`, exécutez la commande suivante :

```shell
spark-submit \
  --driver-java-options -agentlib:jdwp=transport=dt_socket,server=y,suspend=n,address=5005 \
  --class org.apache.spark.deploy.dotnet.DotnetRunner \
  --master local \
  <path-to-microsoft-spark-jar> \
  <path-to-your-app-exe> <argument(s)-to-your-app>
```

Après avoir exécuté la commande, attachez un débogueur au processus en cours d’exécution avec [Intellij](https://www.jetbrains.com/help/idea/attaching-to-local-process.html).

## <a name="next-steps"></a>Étapes suivantes

* [Bien démarrer avec .NET pour Apache Spark](../tutorials/get-started.md)
* [Déployer une application .NET pour Apache Spark sur Azure HDInsight](../tutorials/hdinsight-deployment.md)
* [Déployer une application .NET pour Apache Spark sur Databricks](../tutorials/databricks-deployment.md)
* [Déployer une application .NET pour Apache Spark sur Amazon EMR Spark](../tutorials/amazon-emr-spark-deployment.md)
