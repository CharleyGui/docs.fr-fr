---
title: Déboguer une application .NET pour Apache Spark sur Windows
description: Découvrez comment déboguer votre application .NET pour Apache Spark sur Windows.
ms.date: 06/25/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 249b4bccbf1378d8ef8c824f39151c33fb9f875a
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557149"
---
# <a name="debug-a-net-for-apache-spark-application"></a><span data-ttu-id="7df62-103">Déboguer une application .NET pour Apache Spark</span><span class="sxs-lookup"><span data-stu-id="7df62-103">Debug a .NET for Apache Spark application</span></span>

<span data-ttu-id="7df62-104">Cette procédure fournit les étapes permettant de déboguer votre application .NET pour Apache Spark sur Windows.</span><span class="sxs-lookup"><span data-stu-id="7df62-104">This how-to provides the steps to debug your .NET for Apache Spark application on Windows.</span></span>

[!INCLUDE [spark-preview-note](../../../includes/spark-preview-note.md)]

## <a name="debug-your-application"></a><span data-ttu-id="7df62-105">Déboguer votre application</span><span class="sxs-lookup"><span data-stu-id="7df62-105">Debug your application</span></span>

<span data-ttu-id="7df62-106">Ouvrez une nouvelle fenêtre d’invite de commandes et exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="7df62-106">Open a new command prompt window and run the following command:</span></span>

```shell
spark-submit \
  --class org.apache.spark.deploy.dotnet.DotnetRunner \
  --master local \
  <path-to-microsoft-spark-jar> \
  debug
```

<span data-ttu-id="7df62-107">Quand vous exécutez la commande, vous voyez la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="7df62-107">When you run the command, you see the following output:</span></span>

```console
***********************************************************************
* .NET Backend running debug mode. Press enter to exit *
***********************************************************************
```

<span data-ttu-id="7df62-108">En mode débogage, DotnetRunner ne lance pas l’application .NET, mais attend que vous démarriez l’application .NET.</span><span class="sxs-lookup"><span data-stu-id="7df62-108">In debug mode, DotnetRunner does not launch the .NET application, but instead waits for you to start the .NET app.</span></span> <span data-ttu-id="7df62-109">Laissez cette fenêtre d’invite de commandes ouverte et démarrez votre application .NET par le biais du débogueur C# pour déboguer votre application.</span><span class="sxs-lookup"><span data-stu-id="7df62-109">Leave this command prompt window open and start your .NET application through C# debugger to debug your application.</span></span> <span data-ttu-id="7df62-110">Démarrez votre application .NET avec un débogueur C# (débogueur Visual Studio pour l' [extension de débogueur](https://code.visualstudio.com/Docs/editor/debugging)[Windows/MacOS](https://visualstudio.microsoft.com/vs/) ou c# dans Visual Studio code) pour déboguer votre application.</span><span class="sxs-lookup"><span data-stu-id="7df62-110">Start your .NET application with a C# debugger ([Visual Studio Debugger for Windows/macOS](https://visualstudio.microsoft.com/vs/) or [C# Debugger Extension in Visual Studio Code](https://code.visualstudio.com/Docs/editor/debugging)) to debug your application.</span></span>

## <a name="debug-a-user-defined-function-udf"></a><span data-ttu-id="7df62-111">Déboguer une fonction définie par l’utilisateur (UDF)</span><span class="sxs-lookup"><span data-stu-id="7df62-111">Debug a user-defined function (UDF)</span></span>

> [!NOTE]
> <span data-ttu-id="7df62-112">Les fonctions définies par l’utilisateur sont uniquement prises en charge sur Windows avec le débogueur Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="7df62-112">User-defined functions are supported only on Windows with Visual Studio Debugger.</span></span>

<span data-ttu-id="7df62-113">Avant d’exécuter `spark-submit` , définissez la variable d’environnement suivante :</span><span class="sxs-lookup"><span data-stu-id="7df62-113">Before running `spark-submit`, set the following environment variable:</span></span>

```bat
set DOTNET_WORKER_DEBUG=1
```

<span data-ttu-id="7df62-114">Quand vous exécutez votre application Spark, une `Choose Just-In-Time Debugger` fenêtre s’affiche.</span><span class="sxs-lookup"><span data-stu-id="7df62-114">When you run your Spark application, a `Choose Just-In-Time Debugger` window will pop up.</span></span> <span data-ttu-id="7df62-115">Choisissez un débogueur Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="7df62-115">Choose a Visual Studio debugger.</span></span>

<span data-ttu-id="7df62-116">Le débogueur s’arrête à l’emplacement suivant dans [TaskRunner.cs](https://github.com/dotnet/spark/blob/5e9c08b430b4bc56b5f42252c4b73437377afaed/src/csharp/Microsoft.Spark.Worker/TaskRunner.cs#L52):</span><span class="sxs-lookup"><span data-stu-id="7df62-116">The debugger will break at the following location in [TaskRunner.cs](https://github.com/dotnet/spark/blob/5e9c08b430b4bc56b5f42252c4b73437377afaed/src/csharp/Microsoft.Spark.Worker/TaskRunner.cs#L52):</span></span>

```csharp
if (EnvironmentUtils.GetEnvironmentVariableAsBool("DOTNET_WORKER_DEBUG"))
{
    Debugger.Launch(); // <-- The debugger will break here.
}
```

<span data-ttu-id="7df62-117">Accédez au fichier *. cs* contenant l’UDF que vous envisagez de déboguer, puis [définissez un point d’arrêt](/visualstudio/debugger/using-breakpoints?view=vs-2019).</span><span class="sxs-lookup"><span data-stu-id="7df62-117">Navigate to the *.cs* file that contains the UDF that you plan to debug, and [set a breakpoint](/visualstudio/debugger/using-breakpoints?view=vs-2019).</span></span> <span data-ttu-id="7df62-118">Le point d’arrêt indique `The breakpoint will not currently be hit` que le thread de travail n’a pas encore chargé l’assembly qui contient la fonction définie par l’employé.</span><span class="sxs-lookup"><span data-stu-id="7df62-118">The breakpoint will say `The breakpoint will not currently be hit` because the worker hasn't loaded the assembly that contains UDF yet.</span></span>

<span data-ttu-id="7df62-119">Appuyez `F5` sur pour continuer votre application et le point d’arrêt finira par être atteint.</span><span class="sxs-lookup"><span data-stu-id="7df62-119">Hit `F5` to continue your application and the breakpoint will eventually be hit.</span></span>

> [!NOTE]
> <span data-ttu-id="7df62-120">La fenêtre choisir le débogueur juste-à-temps s’affiche pour chaque tâche.</span><span class="sxs-lookup"><span data-stu-id="7df62-120">The Choose Just-In-Time Debugger window pops up for each task.</span></span> <span data-ttu-id="7df62-121">Pour éviter des fenêtres contextuelles excessives, définissez le nombre d’exécuteurs sur un nombre faible.</span><span class="sxs-lookup"><span data-stu-id="7df62-121">To avoid excessive pop-ups, set the number of executors to a low number.</span></span> <span data-ttu-id="7df62-122">Par exemple, vous pouvez utiliser l’option **--Master local [1]** pour Spark-submit pour définir le nombre de tâches sur 1, ce qui lance une seule instance du débogueur.</span><span class="sxs-lookup"><span data-stu-id="7df62-122">For example, you can use the **--master local[1]** option for spark-submit to set the number of tasks to 1, which launches a single debugger instance.</span></span>

## <a name="debug-scala-code"></a><span data-ttu-id="7df62-123">Déboguer du code Scala</span><span class="sxs-lookup"><span data-stu-id="7df62-123">Debug Scala code</span></span>

<span data-ttu-id="7df62-124">Si vous avez besoin de déboguer le code scalaire ( `DotnetRunner` , `DotnetBackendHandler` , etc.), vous pouvez utiliser la commande suivante et attacher un débogueur au processus en cours d’exécution à l’aide de [IntelliJ](https://www.jetbrains.com/help/idea/attaching-to-local-process.html):</span><span class="sxs-lookup"><span data-stu-id="7df62-124">If you need to debug the Scala-side code (`DotnetRunner`, `DotnetBackendHandler`, etc.), you can use the following command and attach a debugger to the running process using [IntelliJ](https://www.jetbrains.com/help/idea/attaching-to-local-process.html):</span></span>

```shell
spark-submit \
  --driver-java-options -agentlib:jdwp=transport=dt_socket,server=y,suspend=n,address=5005 \
  --class org.apache.spark.deploy.dotnet.DotnetRunner \
  --master local \
  <path-to-microsoft-spark-jar> \
  <path-to-your-app-exe> <argument(s)-to-your-app>
```

<span data-ttu-id="7df62-125">Après avoir exécuté la commande, attachez un débogueur au processus en cours d’exécution avec [Intellij](https://www.jetbrains.com/help/idea/attaching-to-local-process.html).</span><span class="sxs-lookup"><span data-stu-id="7df62-125">After you run the command, attach a debugger to the running process using [Intellij](https://www.jetbrains.com/help/idea/attaching-to-local-process.html).</span></span>

## <a name="next-steps"></a><span data-ttu-id="7df62-126">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="7df62-126">Next steps</span></span>

* [<span data-ttu-id="7df62-127">Bien démarrer avec .NET pour Apache Spark</span><span class="sxs-lookup"><span data-stu-id="7df62-127">Get started with .NET for Apache Spark</span></span>](../tutorials/get-started.md)
* [<span data-ttu-id="7df62-128">Déployer une application .NET pour Apache Spark sur Azure HDInsight</span><span class="sxs-lookup"><span data-stu-id="7df62-128">Deploy a .NET for Apache Spark application to Azure HDInsight</span></span>](../tutorials/hdinsight-deployment.md)
* [<span data-ttu-id="7df62-129">Déployer une application .NET pour Apache Spark sur Databricks</span><span class="sxs-lookup"><span data-stu-id="7df62-129">Deploy a .NET for Apache Spark application to Databricks</span></span>](../tutorials/databricks-deployment.md)
* [<span data-ttu-id="7df62-130">Déployer une application .NET pour Apache Spark sur Amazon EMR Spark</span><span class="sxs-lookup"><span data-stu-id="7df62-130">Deploy a .NET for Apache Spark application to Amazon EMR Spark</span></span>](../tutorials/amazon-emr-spark-deployment.md)
