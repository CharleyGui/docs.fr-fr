---
title: Déployer une application .NET pour Apache Spark sur Azure HDInsight
description: Découvrez comment déployer une application .NET pour Apache Spark sur HDInsight.
ms.date: 05/17/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 4769c194520790ce217d46d1d3197b20742d4f1a
ms.sourcegitcommit: ffd7dd79468a81bbb0d6449f6d65513e050c04c4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/21/2019
ms.locfileid: "69576946"
---
# <a name="deploy-a-net-for-apache-spark-application-to-azure-hdinsight"></a><span data-ttu-id="a19b4-103">Déployer une application .NET pour Apache Spark sur Azure HDInsight</span><span class="sxs-lookup"><span data-stu-id="a19b4-103">Deploy a .NET for Apache Spark application to Azure HDInsight</span></span>

<span data-ttu-id="a19b4-104">Ce tutoriel explique comment déployer une application .NET pour Apache Spark sur Azure HDInsight.</span><span class="sxs-lookup"><span data-stu-id="a19b4-104">This tutorial teaches how to deploy a .NET for Apache Spark application to Azure HDInsight.</span></span>

<span data-ttu-id="a19b4-105">Dans ce didacticiel, vous apprendrez à :</span><span class="sxs-lookup"><span data-stu-id="a19b4-105">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="a19b4-106">Préparer Microsoft.Spark.Worker</span><span class="sxs-lookup"><span data-stu-id="a19b4-106">Prepare Microsoft.Spark.Worker</span></span>
> * <span data-ttu-id="a19b4-107">Publier votre application .NET Spark</span><span class="sxs-lookup"><span data-stu-id="a19b4-107">Publish your Spark .NET app</span></span>
> * <span data-ttu-id="a19b4-108">Déployer votre application sur Azure HDInsight</span><span class="sxs-lookup"><span data-stu-id="a19b4-108">Deploy your app to Azure HDInsight</span></span>
> * <span data-ttu-id="a19b4-109">Exécuter votre application</span><span class="sxs-lookup"><span data-stu-id="a19b4-109">Run your app</span></span>

## <a name="prerequisites"></a><span data-ttu-id="a19b4-110">Prérequis</span><span class="sxs-lookup"><span data-stu-id="a19b4-110">Prerequisites</span></span>

<span data-ttu-id="a19b4-111">Avant de commencer, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="a19b4-111">Before you start, do the following:</span></span>

* <span data-ttu-id="a19b4-112">Téléchargez l’[Explorateur Stockage Azure](https://azure.microsoft.com/features/storage-explorer/).</span><span class="sxs-lookup"><span data-stu-id="a19b4-112">Download [Azure Storage Explorer](https://azure.microsoft.com/features/storage-explorer/).</span></span>
* <span data-ttu-id="a19b4-113">Téléchargez [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) sur votre machine locale.</span><span class="sxs-lookup"><span data-stu-id="a19b4-113">Download [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) to your local machine.</span></span> <span data-ttu-id="a19b4-114">Il s’agit d’un script d’assistance que vous utilisez ultérieurement pour copier les fichiers dépendants de .NET pour Apache Spark dans les nœuds Worker de votre cluster Spark.</span><span class="sxs-lookup"><span data-stu-id="a19b4-114">This is a helper script that you use later to copy .NET for Apache Spark dependent files into your Spark cluster's worker nodes.</span></span>

## <a name="prepare-worker-dependencies"></a><span data-ttu-id="a19b4-115">Préparer les dépendances Worker</span><span class="sxs-lookup"><span data-stu-id="a19b4-115">Prepare worker dependencies</span></span>

<span data-ttu-id="a19b4-116">**Microsoft.Spark.Worker** est un composant back-end qui se trouve sur les nœuds Worker individuels de votre cluster Spark.</span><span class="sxs-lookup"><span data-stu-id="a19b4-116">**Microsoft.Spark.Worker** is a backend component that lives on the individual worker nodes of your Spark cluster.</span></span> <span data-ttu-id="a19b4-117">Quand vous voulez exécuter une fonction C# définie par l’utilisateur, Spark doit comprendre comment lancer le CLR .NET pour exécuter la fonction définie par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="a19b4-117">When you want to execute a C# UDF (user-defined function), Spark needs to understand how to launch the .NET CLR to execute the UDF.</span></span> <span data-ttu-id="a19b4-118">**Microsoft.Spark.Worker** fournit à Spark une collection de classes qui activent cette fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="a19b4-118">**Microsoft.Spark.Worker** provides a collection of classes to Spark that enable this functionality.</span></span>

1. <span data-ttu-id="a19b4-119">Sélectionnez une version netcoreapp Linux de [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases) à déployer sur votre cluster.</span><span class="sxs-lookup"><span data-stu-id="a19b4-119">Select a [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases) Linux netcoreapp release to be deployed on your cluster.</span></span>

   <span data-ttu-id="a19b4-120">Par exemple, si vous voulez `.NET for Apache Spark v0.1.0` avec `netcoreapp2.1`, vous devez télécharger [Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz](https://github.com/dotnet/spark/releases/download/v0.1.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz).</span><span class="sxs-lookup"><span data-stu-id="a19b4-120">For example, if you want `.NET for Apache Spark v0.1.0` using `netcoreapp2.1`, you'd download [Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz](https://github.com/dotnet/spark/releases/download/v0.1.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz).</span></span>

2. <span data-ttu-id="a19b4-121">Chargez `Microsoft.Spark.Worker.<release>.tar.gz` et [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) dans un système de fichiers distribués (par exemple HDFS, WASB, ADLS) auquel votre cluster a accès.</span><span class="sxs-lookup"><span data-stu-id="a19b4-121">Upload `Microsoft.Spark.Worker.<release>.tar.gz` and [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) to a distributed file system (e.g., HDFS, WASB, ADLS) that your cluster has access to.</span></span>

## <a name="prepare-your-net-for-apache-spark-app"></a><span data-ttu-id="a19b4-122">Préparer votre application .NET pour Apache Spark</span><span class="sxs-lookup"><span data-stu-id="a19b4-122">Prepare your .NET for Apache Spark app</span></span>

1. <span data-ttu-id="a19b4-123">Suivez le tutoriel [Prise en main](get-started.md) pour générer votre application.</span><span class="sxs-lookup"><span data-stu-id="a19b4-123">Follow the [Get Started](get-started.md) tutorial to build your app.</span></span>

2. <span data-ttu-id="a19b4-124">Publiez votre application .NET Spark en tant qu’application autonome.</span><span class="sxs-lookup"><span data-stu-id="a19b4-124">Publish your Spark .NET app as self-contained.</span></span>

   <span data-ttu-id="a19b4-125">Vous pouvez exécuter la commande suivante sur Linux.</span><span class="sxs-lookup"><span data-stu-id="a19b4-125">You can run the following command on Linux.</span></span>

   ```bash
   dotnet publish -c Release -f netcoreapp2.1 -r ubuntu.16.04-x64
   ```

3. <span data-ttu-id="a19b4-126">Produisez `<your app>.zip` pour les fichiers publiés.</span><span class="sxs-lookup"><span data-stu-id="a19b4-126">Produce `<your app>.zip` for the published files.</span></span>

   <span data-ttu-id="a19b4-127">Vous pouvez exécuter la commande suivante sur Linux en utilisant `zip`.</span><span class="sxs-lookup"><span data-stu-id="a19b4-127">You can run the following command on Linux using `zip`.</span></span>

   ```bash
   zip -r <your app>.zip .
   ```

4. <span data-ttu-id="a19b4-128">Chargez les éléments suivants sur un système de fichiers distribués (par exemple HDFS, WASB, ADLS) auquel votre cluster a accès :</span><span class="sxs-lookup"><span data-stu-id="a19b4-128">Upload the following to a distributed file system (e.g., HDFS, WASB, ADLS) that your cluster has access to:</span></span>

   * <span data-ttu-id="a19b4-129">`microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar`: Ce fichier jar est inclus dans le package NuGet [Microsoft.Spark](https://www.nuget.org/packages/Microsoft.Spark/) et est colocalisé dans le répertoire de sortie de la génération de votre application.</span><span class="sxs-lookup"><span data-stu-id="a19b4-129">`microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar`: This jar is included as part of the [Microsoft.Spark](https://www.nuget.org/packages/Microsoft.Spark/) NuGet package and is colocated in your app's build output directory.</span></span>
   * `<your app>.zip`
   * <span data-ttu-id="a19b4-130">Les fichiers (comme les fichiers de dépendances ou les données communes accessibles à chaque Worker) ou les assemblys (comme les DLL qui contiennent vos fonctions définies par l’utilisateur ou les bibliothèques dont dépend votre `app`) doivent être placés dans le répertoire de travail de chaque exécuteur.</span><span class="sxs-lookup"><span data-stu-id="a19b4-130">Files (like dependency files or common data accessible to every worker) or Assemblies (like DLLs that contain your user-defined functions or libraries that your `app` depends on) to be placed in the working directory of each executor.</span></span>

## <a name="deploy-to-azure-hdinsight-spark"></a><span data-ttu-id="a19b4-131">Déployer sur Azure HDInsight Spark</span><span class="sxs-lookup"><span data-stu-id="a19b4-131">Deploy to Azure HDInsight Spark</span></span>

<span data-ttu-id="a19b4-132">[Azure HDInsight Spark](https://docs.microsoft.com/azure/hdinsight/spark/apache-spark-overview) est l’implémentation Microsoft d’Apache Spark dans le cloud, qui permet aux utilisateurs de lancer et de configurer des clusters Spark dans Azure.</span><span class="sxs-lookup"><span data-stu-id="a19b4-132">[Azure HDInsight Spark](https://docs.microsoft.com/azure/hdinsight/spark/apache-spark-overview) is the Microsoft implementation of Apache Spark in the cloud that allows users to launch and configure Spark clusters in Azure.</span></span> <span data-ttu-id="a19b4-133">Vous pouvez donc utiliser des clusters HDInsight Spark pour traiter vos données stockées dans [Stockage Azure](https://azure.microsoft.com/services/storage/) ou [Azure Data Lake Storage](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-use-data-lake-storage-gen2).</span><span class="sxs-lookup"><span data-stu-id="a19b4-133">You can use HDInsight Spark clusters to process your data stored in [Azure Storage](https://azure.microsoft.com/services/storage/) or [Azure Data Lake Storage](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-use-data-lake-storage-gen2).</span></span>

> [!NOTE]
> <span data-ttu-id="a19b4-134">Azure HDInsight Spark est basé sur Linux.</span><span class="sxs-lookup"><span data-stu-id="a19b4-134">Azure HDInsight Spark is Linux-based.</span></span> <span data-ttu-id="a19b4-135">Si vous voulez déployer votre application sur Azure HDInsight Spark, vérifiez que votre application est compatible avec .NET Standard et que vous utilisez le [compilateur .NET Core](https://dotnet.microsoft.com/download) pour compiler votre application.</span><span class="sxs-lookup"><span data-stu-id="a19b4-135">If you are interested in deploying your app to Azure HDInsight Spark, make sure your app is .NET Standard compatible and that you use the [.NET Core compiler](https://dotnet.microsoft.com/download) to compile your app.</span></span>

### <a name="deploy-microsoftsparkworker"></a><span data-ttu-id="a19b4-136">Déployer Microsoft.Spark.Worker</span><span class="sxs-lookup"><span data-stu-id="a19b4-136">Deploy Microsoft.Spark.Worker</span></span>

<span data-ttu-id="a19b4-137">Cette étape n’est nécessaire qu’une seule fois pour votre cluster.</span><span class="sxs-lookup"><span data-stu-id="a19b4-137">This step is only required once for your cluster.</span></span>

<span data-ttu-id="a19b4-138">Exécutez `install-worker.sh` sur le cluster en utilisant des [actions de script HDInsight](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux).</span><span class="sxs-lookup"><span data-stu-id="a19b4-138">Run `install-worker.sh` on the cluster using [HDInsight Script Actions](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux).</span></span>

|<span data-ttu-id="a19b4-139">Paramètre</span><span class="sxs-lookup"><span data-stu-id="a19b4-139">Setting</span></span>|<span data-ttu-id="a19b4-140">Value</span><span class="sxs-lookup"><span data-stu-id="a19b4-140">Value</span></span>|
|-------|-----|
|<span data-ttu-id="a19b4-141">Type de script</span><span class="sxs-lookup"><span data-stu-id="a19b4-141">Script type</span></span>|<span data-ttu-id="a19b4-142">Personnalisé</span><span class="sxs-lookup"><span data-stu-id="a19b4-142">Custom</span></span>|
|<span data-ttu-id="a19b4-143">Name</span><span class="sxs-lookup"><span data-stu-id="a19b4-143">Name</span></span>|<span data-ttu-id="a19b4-144">Installer Microsoft.Spark.Worker</span><span class="sxs-lookup"><span data-stu-id="a19b4-144">Install Microsoft.Spark.Worker</span></span>|
|<span data-ttu-id="a19b4-145">URI de script bash</span><span class="sxs-lookup"><span data-stu-id="a19b4-145">Bash script URI</span></span>|<span data-ttu-id="a19b4-146">URI vers lequel vous avez chargé `install-worker.sh`.</span><span class="sxs-lookup"><span data-stu-id="a19b4-146">The URI to which you uploaded `install-worker.sh`.</span></span> <span data-ttu-id="a19b4-147">Par exemple, `abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/install-worker.sh`.</span><span class="sxs-lookup"><span data-stu-id="a19b4-147">For example, `abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/install-worker.sh`</span></span>|
|<span data-ttu-id="a19b4-148">Type(s) de nœud</span><span class="sxs-lookup"><span data-stu-id="a19b4-148">Node type(s)</span></span>|<span data-ttu-id="a19b4-149">Worker</span><span class="sxs-lookup"><span data-stu-id="a19b4-149">Worker</span></span>|
|<span data-ttu-id="a19b4-150">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a19b4-150">Parameters</span></span>|<span data-ttu-id="a19b4-151">Paramètres de `install-worker.sh`.</span><span class="sxs-lookup"><span data-stu-id="a19b4-151">Parameters to `install-worker.sh`.</span></span> <span data-ttu-id="a19b4-152">Par exemple, si vous avez chargé `install-worker.sh` dans Azure Data Lake Gen 2, il s’agit de `azure abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/Microsoft.Spark.Worker.<release>.tar.gz /usr/local/bin`.</span><span class="sxs-lookup"><span data-stu-id="a19b4-152">For example, if you uploaded `install-worker.sh` to Azure Data Lake Gen 2 then it would be `azure abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/Microsoft.Spark.Worker.<release>.tar.gz /usr/local/bin`.</span></span>|

![Image d’action de script](./media/hdinsight-deployment/deployment-hdi-action-script.png)

## <a name="run-your-app"></a><span data-ttu-id="a19b4-154">Exécuter votre application</span><span class="sxs-lookup"><span data-stu-id="a19b4-154">Run your app</span></span>

<span data-ttu-id="a19b4-155">Vous pouvez soumettre votre travail à Azure HDInsight en utilisant `spark-submit` ou Apache Livy.</span><span class="sxs-lookup"><span data-stu-id="a19b4-155">You can submit your job to Azure HDInsight using `spark-submit` or Apache Livy.</span></span>

### <a name="use-spark-submit"></a><span data-ttu-id="a19b4-156">Utiliser spark-submit</span><span class="sxs-lookup"><span data-stu-id="a19b4-156">Use spark-submit</span></span>

<span data-ttu-id="a19b4-157">Vous pouvez utiliser la commande [spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html) pour soumettre des travaux .NET pour Apache Spark à Azure HDInsight.</span><span class="sxs-lookup"><span data-stu-id="a19b4-157">You can use the [spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html) command to submit .NET for Apache Spark jobs to Azure HDInsight.</span></span>
 
1. <span data-ttu-id="a19b4-158">`ssh` dans un des nœuds principaux de votre cluster.</span><span class="sxs-lookup"><span data-stu-id="a19b4-158">`ssh` into one of the head nodes in your cluster.</span></span>

1. <span data-ttu-id="a19b4-159">Exécutez `spark-submit` :</span><span class="sxs-lookup"><span data-stu-id="a19b4-159">Run `spark-submit`:</span></span>

   ```bash
   spark-submit \
   --master yarn \
   --class org.apache.spark.deploy.DotnetRunner \
   --files <comma-separated list of assemblies that contain UDF definitions, if any> \
   abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar \
   abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/<your app>.zip <your app> <app arg 1> <app arg 2> ... <app arg n>
   ```

### <a name="use-apache-livy"></a><span data-ttu-id="a19b4-160">Utiliser Apache Livy</span><span class="sxs-lookup"><span data-stu-id="a19b4-160">Use Apache Livy</span></span>

<span data-ttu-id="a19b4-161">Vous pouvez utiliser [Apache Livy](https://livy.incubator.apache.org/), l’API REST d’Apache Spark, pour soumettre des travaux .NET pour Apache Spark à un cluster Azure HDInsight Spark.</span><span class="sxs-lookup"><span data-stu-id="a19b4-161">You can use [Apache Livy](https://livy.incubator.apache.org/), the Apache Spark REST API, to submit .NET for Apache Spark jobs to an Azure HDInsight Spark cluster.</span></span> <span data-ttu-id="a19b4-162">Pour plus d’informations, consultez [Travaux à distance avec Apache Livy](https://docs.microsoft.com/azure/hdinsight/spark/apache-spark-livy-rest-interface).</span><span class="sxs-lookup"><span data-stu-id="a19b4-162">For more information, see [Remote jobs with Apache Livy](https://docs.microsoft.com/azure/hdinsight/spark/apache-spark-livy-rest-interface).</span></span>

<span data-ttu-id="a19b4-163">Vous pouvez exécuter la commande suivante sur Linux en utilisant `curl` :</span><span class="sxs-lookup"><span data-stu-id="a19b4-163">You can run the following command on Linux using `curl`:</span></span>

```bash
curl -k -v -X POST "https://<your spark cluster>.azurehdinsight.net/livy/batches" \
-u "<hdinsight username>:<hdinsight password>" \
-H "Content-Type: application/json" \
-H "X-Requested-By: <hdinsight username>" \
-d @- << EOF
{
    "file":"abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar",
    "className":"org.apache.spark.deploy.DotnetRunner",
    "files":["abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/<udf assembly>", "abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/<file>"],
    "args":["abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/<your app>.zip","<your app>","<app arg 1>","<app arg 2>,"...","<app arg n>"]
}
EOF
```

## <a name="next-steps"></a><span data-ttu-id="a19b4-164">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="a19b4-164">Next steps</span></span>

<span data-ttu-id="a19b4-165">Dans ce tutoriel, vous avez déployé votre application .NET pour Apache Spark sur Azure HDInsight.</span><span class="sxs-lookup"><span data-stu-id="a19b4-165">In this tutorial, you deployed your .NET for Apache Spark application to Azure HDInsight.</span></span> <span data-ttu-id="a19b4-166">Pour plus d’informations sur HDInsight, consultez la documentation d’Azure HDInsight.</span><span class="sxs-lookup"><span data-stu-id="a19b4-166">To learn more about HDInsight, continue to the Azure HDInsight Documentation.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="a19b4-167">Documentation Azure HDInsight</span><span class="sxs-lookup"><span data-stu-id="a19b4-167">Azure HDInsight Documentation</span></span>](https://docs.microsoft.com/azure/hdinsight/)
