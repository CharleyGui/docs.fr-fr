---
title: Déboguer une application .NET pour Apache Spark sur Windows
description: Découvrez comment déboguer votre application .NET pour Apache Spark sur Windows.
ms.date: 01/29/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: dac6aed1f7faba7f07b722a6dac0da930ab9ec66
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79185806"
---
# <a name="debug-a-net-for-apache-spark-application"></a>Déboguer une application .NET pour Apache Spark

Cette façon de fournir les étapes pour déboiser votre .NET pour Apache Spark application sur Windows.

## <a name="debug-your-application"></a>Déboguer votre application

Ouvrez une nouvelle fenêtre d’invite de commande et exécutez la commande suivante :

```shell
spark-submit \
  --class org.apache.spark.deploy.dotnet.DotnetRunner \
  --master local \
  <path-to-microsoft-spark-jar> \
  debug
```

Quand vous exécutez la commande, vous voyez la sortie suivante :

```console
***********************************************************************
* .NET Backend running debug mode. Press enter to exit *
***********************************************************************
```

En mode débogé, DotnetRunner ne lance pas l’application .NET, mais attend plutôt que vous commenciez l’application .NET. Laissez cette fenêtre d’invitation de commande ouverte et démarrez votre application .NET par le biais de débbugger C pour déboquer votre application. Démarrez votre application .NET avec un débbugger CMD[(Visual Studio Debugger pour Windows/macOS](https://visualstudio.microsoft.com/vs/) ou [C’Debugger Extension in Visual Studio Code](https://code.visualstudio.com/Docs/editor/debugging)) pour déboiser votre application.

## <a name="debug-a-user-defined-function-udf"></a>Débogé d’une fonction définie par l’utilisateur (UDF)

> [!NOTE]
> Les fonctions définies par l’utilisateur ne sont prises en charge que sur Windows avec Visual Studio Debugger.

Avant `spark-submit`d’exécuter, définissez la variable d’environnement suivante :

```bat
set DOTNET_WORKER_DEBUG=1
```

Lorsque vous exécutez votre `Choose Just-In-Time Debugger` application Spark, une fenêtre apparaît. Choisissez un débbugger Visual Studio.

Le débbuggeur se cassera à l’endroit suivant dans [TaskRunner.cs](https://github.com/dotnet/spark/blob/5e9c08b430b4bc56b5f42252c4b73437377afaed/src/csharp/Microsoft.Spark.Worker/TaskRunner.cs#L52):

```csharp
if (EnvironmentUtils.GetEnvironmentVariableAsBool("DOTNET_WORKER_DEBUG"))
{
    Debugger.Launch(); // <-- The debugger will break here.
}
```

Naviguez vers le fichier *.cs* qui contient l’UDF que vous prévoyez de déboiffer, et [définissez un point d’arrêt](https://docs.microsoft.com/visualstudio/debugger/using-breakpoints?view=vs-2019). Le point d’arrêt dira `The breakpoint will not currently be hit` parce que le travailleur n’a pas chargé l’assemblage qui contient UDF encore.

Frappez `F5` pour continuer votre application et le point d’arrêt sera finalement touché.

> [!NOTE]
> La fenêtre Choisir Juste-à-Temps Debugger apparaît pour chaque tâche. Pour éviter les pop-ups excessifs, définissez le nombre d’exécuteurs à un faible nombre. Par exemple, vous pouvez utiliser **l’option --master local[1]** pour l’étincelle-soumettre pour définir le nombre de tâches à 1, qui lance une seule instance de débbugger.

## <a name="debug-scala-code"></a>Déboguer du code Scala

Si vous avez besoin de déboguer`DotnetRunner`le `DotnetBackendHandler`code côté Scala (, , etc.), vous pouvez utiliser la commande suivante et attacher un débbugger au processus d’exécution en utilisant [IntelliJ](https://www.jetbrains.com/help/idea/attaching-to-local-process.html):

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
