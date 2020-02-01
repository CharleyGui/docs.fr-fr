---
title: Déboguer une application .NET pour Apache Spark sur Windows
description: Découvrez comment déboguer votre application .NET pour Apache Spark sur Windows.
ms.date: 01/29/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 25f5291c47dc1cdf2668cb077fae7439e330cc1c
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "76919927"
---
# <a name="debug-a-net-for-apache-spark-application"></a>Déboguer une application .NET pour Apache Spark

Cette procédure fournit les étapes permettant de déboguer votre application .NET pour Apache Spark sur Windows.

## <a name="debug-your-application"></a>Déboguer votre application

Ouvrez une nouvelle fenêtre d’invite de commandes et exécutez la commande suivante :

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

En mode débogage, DotnetRunner ne lance pas l’application .NET, mais attend que vous démarriez l’application .NET. Laissez cette fenêtre d’invite de commandes ouverte et démarrez votre application C# .NET par le biais du débogueur pour déboguer votre application. Démarrez votre application .net à l' C# aide d’un débogueur (débogueur[Visual Studio pour Windows/MacOS](https://visualstudio.microsoft.com/vs/) ou [ C# extension du débogueur dans Visual Studio code](https://code.visualstudio.com/Docs/editor/debugging)) pour déboguer votre application.

## <a name="debug-a-user-defined-function-udf"></a>Déboguer une fonction définie par l’utilisateur (UDF)

> [!NOTE]
> Les fonctions définies par l’utilisateur sont uniquement prises en charge sur Windows avec le débogueur Visual Studio.

Avant d’exécuter `spark-submit`, définissez la variable d’environnement suivante :

```bat
set DOTNET_WORKER_DEBUG=1
```

Quand vous exécutez votre application Spark, une fenêtre de `Choose Just-In-Time Debugger` s’affiche. Choisissez un débogueur Visual Studio.

Le débogueur s’arrête à l’emplacement suivant dans [TaskRunner.cs](https://github.com/dotnet/spark/blob/5e9c08b430b4bc56b5f42252c4b73437377afaed/src/csharp/Microsoft.Spark.Worker/TaskRunner.cs#L52):

```csharp
if (EnvironmentUtils.GetEnvironmentVariableAsBool("DOTNET_WORKER_DEBUG"))
{
    Debugger.Launch(); // <-- The debugger will break here.
}
```

Accédez au fichier *. cs* contenant l’UDF que vous envisagez de déboguer, puis [définissez un point d’arrêt](https://docs.microsoft.com/visualstudio/debugger/using-breakpoints?view=vs-2019). Le point d’arrêt indique `The breakpoint will not currently be hit` car le Worker n’a pas encore chargé l’assembly qui contient la fonction définie par l’employé.

Appuyez sur `F5` pour continuer votre application et le point d’arrêt sera finalement atteint.

> [!NOTE] 
> La fenêtre choisir le débogueur juste-à-temps s’affiche pour chaque tâche. Pour éviter des fenêtres contextuelles excessives, définissez le nombre d’exécuteurs sur un nombre faible. Par exemple, vous pouvez utiliser l’option **--Master local [1]** pour Spark-submit pour définir le nombre de tâches sur 1, ce qui lance une seule instance du débogueur.

## <a name="debug-scala-code"></a>Déboguer du code Scala

Si vous avez besoin de déboguer le code scalaire (`DotnetRunner`, `DotnetBackendHandler`, etc.), vous pouvez utiliser la commande suivante et attacher un débogueur au processus en cours d’exécution à l’aide de [IntelliJ](https://www.jetbrains.com/help/idea/attaching-to-local-process.html):

```shell
spark-submit \
  --driver-java-options -agentlib:jdwp=transport=dt_socket,server=y,suspend=n,address=5005 \
  --class org.apache.spark.deploy.dotnet.DotnetRunner \
  --master local \
  <path-to-microsoft-spark-jar> \
  <path-to-your-app-exe> <argument(s)-to-your-app>
```

Après avoir exécuté la commande, attachez un débogueur au processus en cours d’exécution avec [Intellij](https://www.jetbrains.com/help/idea/attaching-to-local-process.html).

## <a name="next-steps"></a>Étapes suivantes :

* [Bien démarrer avec .NET pour Apache Spark](../tutorials/get-started.md)
* [Déployer une application .NET pour Apache Spark sur Azure HDInsight](../tutorials/hdinsight-deployment.md)
* [Déployer une application .NET pour Apache Spark sur Databricks](../tutorials/databricks-deployment.md)
* [Déployer une application .NET pour Apache Spark sur Amazon EMR Spark](../tutorials/amazon-emr-spark-deployment.md)
