---
title: Déboguer une application .NET pour Apache Spark sur Windows
description: Découvrez comment déboguer votre application .NET pour Apache Spark sur Windows.
ms.date: 08/15/2019
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 098c7519fe99ef04773c5e4b81685ca0f06f1272
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74281526"
---
# <a name="debug-a-net-for-apache-spark-application"></a><span data-ttu-id="7ad7a-103">Déboguer une application .NET pour Apache Spark</span><span class="sxs-lookup"><span data-stu-id="7ad7a-103">Debug a .NET for Apache Spark application</span></span>

<span data-ttu-id="7ad7a-104">Cette procédure indique les commandes que vous devez exécuter pour déboguer votre application .NET pour Apache Spark et du code Scala sur Windows.</span><span class="sxs-lookup"><span data-stu-id="7ad7a-104">This how-to provides the commands you need to run to debug your .NET for Apache Spark application and Scala code on Windows.</span></span>

## <a name="debug-your-application"></a><span data-ttu-id="7ad7a-105">Déboguer votre application</span><span class="sxs-lookup"><span data-stu-id="7ad7a-105">Debug your application</span></span>

<span data-ttu-id="7ad7a-106">Ouvrez une fenêtre d’invite de commandes et exécutez ceci :</span><span class="sxs-lookup"><span data-stu-id="7ad7a-106">Open a new command prompt window, run the following:</span></span>

```shell
spark-submit \
  --class org.apache.spark.deploy.dotnet.DotnetRunner \
  --master local \
  <path-to-microsoft-spark-jar> \
  debug
```

<span data-ttu-id="7ad7a-107">Quand vous exécutez la commande, vous voyez la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="7ad7a-107">When you run the command, you see the following output:</span></span>

```console
***********************************************************************
* .NET Backend running debug mode. Press enter to exit *
***********************************************************************
```

<span data-ttu-id="7ad7a-108">Dans ce mode de débogage, `DotnetRunner` ne lance pas l’application .NET, mais attend qu’elle se connecte.</span><span class="sxs-lookup"><span data-stu-id="7ad7a-108">In this debug mode, `DotnetRunner` does not launch the .NET application, but it waits for it to connect.</span></span> <span data-ttu-id="7ad7a-109">Laissez ouverte la fenêtre d’invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="7ad7a-109">Leave this command prompt window open.</span></span>

<span data-ttu-id="7ad7a-110">Vous pouvez maintenant exécuter votre application .NET avec n’importe quel débogueur pour déboguer votre application.</span><span class="sxs-lookup"><span data-stu-id="7ad7a-110">Now you can run your .NET application with any debugger to debug your application.</span></span>

## <a name="debug-scala-code"></a><span data-ttu-id="7ad7a-111">Déboguer du code Scala</span><span class="sxs-lookup"><span data-stu-id="7ad7a-111">Debug Scala code</span></span>

<span data-ttu-id="7ad7a-112">Si vous devez déboguer du code côté Scala, comme `DotnetRunner` ou `DotnetBackendHandler`, exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="7ad7a-112">If you need to debug the Scala side code, such as `DotnetRunner` or `DotnetBackendHandler`, run the following command:</span></span>

```shell
spark-submit \
  --driver-java-options -agentlib:jdwp=transport=dt_socket,server=y,suspend=n,address=5005 \
  --class org.apache.spark.deploy.dotnet.DotnetRunner \
  --master local \
  <path-to-microsoft-spark-jar> \
  <path-to-your-app-exe> <argument(s)-to-your-app>
```

<span data-ttu-id="7ad7a-113">Après avoir exécuté la commande, attachez un débogueur au processus en cours d’exécution avec [Intellij](https://www.jetbrains.com/help/idea/attaching-to-local-process.html).</span><span class="sxs-lookup"><span data-stu-id="7ad7a-113">After you run the command, attach a debugger to the running process using [Intellij](https://www.jetbrains.com/help/idea/attaching-to-local-process.html).</span></span>

## <a name="next-steps"></a><span data-ttu-id="7ad7a-114">Étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="7ad7a-114">Next steps</span></span>

* [<span data-ttu-id="7ad7a-115">Bien démarrer avec .NET pour Apache Spark</span><span class="sxs-lookup"><span data-stu-id="7ad7a-115">Get started with .NET for Apache Spark</span></span>](../tutorials/get-started.md)
* [<span data-ttu-id="7ad7a-116">Déployer une application .NET pour Apache Spark sur Azure HDInsight</span><span class="sxs-lookup"><span data-stu-id="7ad7a-116">Deploy a .NET for Apache Spark application to Azure HDInsight</span></span>](../tutorials/hdinsight-deployment.md)
* [<span data-ttu-id="7ad7a-117">Déployer une application .NET pour Apache Spark sur Databricks</span><span class="sxs-lookup"><span data-stu-id="7ad7a-117">Deploy a .NET for Apache Spark application to Databricks</span></span>](../tutorials/databricks-deployment.md)
* [<span data-ttu-id="7ad7a-118">Déployer une application .NET pour Apache Spark sur Amazon EMR Spark</span><span class="sxs-lookup"><span data-stu-id="7ad7a-118">Deploy a .NET for Apache Spark application to Amazon EMR Spark</span></span>](../tutorials/amazon-emr-spark-deployment.md)
