---
title: Déployer une application .NET pour Apache Spark sur Azure HDInsight
description: Découvrez comment déployer un .NET pour Apache Spark application sur HDInsight.
ms.date: 05/17/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 4769c194520790ce217d46d1d3197b20742d4f1a
ms.sourcegitcommit: ffd7dd79468a81bbb0d6449f6d65513e050c04c4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/21/2019
ms.locfileid: "69576946"
---
# <a name="deploy-a-net-for-apache-spark-application-to-azure-hdinsight"></a><span data-ttu-id="0312d-103">Déployer une application .NET pour Apache Spark sur Azure HDInsight</span><span class="sxs-lookup"><span data-stu-id="0312d-103">Deploy a .NET for Apache Spark application to Azure HDInsight</span></span>

<span data-ttu-id="0312d-104">Ce didacticiel explique comment déployer une application .NET pour Apache Spark sur Azure HDInsight.</span><span class="sxs-lookup"><span data-stu-id="0312d-104">This tutorial teaches how to deploy a .NET for Apache Spark application to Azure HDInsight.</span></span>

<span data-ttu-id="0312d-105">Ce tutoriel vous montre comment effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="0312d-105">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="0312d-106">Préparer Microsoft. Spark. Worker</span><span class="sxs-lookup"><span data-stu-id="0312d-106">Prepare Microsoft.Spark.Worker</span></span>
> * <span data-ttu-id="0312d-107">Publier votre application Spark .NET</span><span class="sxs-lookup"><span data-stu-id="0312d-107">Publish your Spark .NET app</span></span>
> * <span data-ttu-id="0312d-108">Déployer votre application sur Azure HDInsight</span><span class="sxs-lookup"><span data-stu-id="0312d-108">Deploy your app to Azure HDInsight</span></span>
> * <span data-ttu-id="0312d-109">Exécuter votre application</span><span class="sxs-lookup"><span data-stu-id="0312d-109">Run your app</span></span>

## <a name="prerequisites"></a><span data-ttu-id="0312d-110">Prérequis</span><span class="sxs-lookup"><span data-stu-id="0312d-110">Prerequisites</span></span>

<span data-ttu-id="0312d-111">Avant de commencer, procédez comme suit:</span><span class="sxs-lookup"><span data-stu-id="0312d-111">Before you start, do the following:</span></span>

* <span data-ttu-id="0312d-112">Téléchargez [Explorateur stockage Azure](https://azure.microsoft.com/features/storage-explorer/).</span><span class="sxs-lookup"><span data-stu-id="0312d-112">Download [Azure Storage Explorer](https://azure.microsoft.com/features/storage-explorer/).</span></span>
* <span data-ttu-id="0312d-113">Téléchargez [install-Worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) sur votre ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="0312d-113">Download [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) to your local machine.</span></span> <span data-ttu-id="0312d-114">Il s’agit d’un script d’assistance que vous utilisez ultérieurement pour copier .NET pour Apache Spark fichiers dépendants dans les nœuds Worker du cluster Spark.</span><span class="sxs-lookup"><span data-stu-id="0312d-114">This is a helper script that you use later to copy .NET for Apache Spark dependent files into your Spark cluster's worker nodes.</span></span>

## <a name="prepare-worker-dependencies"></a><span data-ttu-id="0312d-115">Préparer les dépendances de Worker</span><span class="sxs-lookup"><span data-stu-id="0312d-115">Prepare worker dependencies</span></span>

<span data-ttu-id="0312d-116">**Microsoft. Spark. Worker** est un composant principal qui réside sur les nœuds Worker individuels de votre cluster Spark.</span><span class="sxs-lookup"><span data-stu-id="0312d-116">**Microsoft.Spark.Worker** is a backend component that lives on the individual worker nodes of your Spark cluster.</span></span> <span data-ttu-id="0312d-117">Lorsque vous souhaitez exécuter une C# fonction définie par l’utilisateur (UDF), Spark doit comprendre comment lancer le CLR .net pour exécuter l’UDF.</span><span class="sxs-lookup"><span data-stu-id="0312d-117">When you want to execute a C# UDF (user-defined function), Spark needs to understand how to launch the .NET CLR to execute the UDF.</span></span> <span data-ttu-id="0312d-118">**Microsoft. Spark. Worker** fournit une collection de classes à Spark qui activent cette fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="0312d-118">**Microsoft.Spark.Worker** provides a collection of classes to Spark that enable this functionality.</span></span>

1. <span data-ttu-id="0312d-119">Sélectionnez une version de netcoreapp de [Microsoft. Spark. Worker](https://github.com/dotnet/spark/releases) Linux à déployer sur votre cluster.</span><span class="sxs-lookup"><span data-stu-id="0312d-119">Select a [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases) Linux netcoreapp release to be deployed on your cluster.</span></span>

   <span data-ttu-id="0312d-120">Par exemple, si vous souhaitez `.NET for Apache Spark v0.1.0` utiliser `netcoreapp2.1`, vous devez télécharger [Microsoft. Spark. Worker. netcoreapp 2.1. Linux-x64-0.1.0. tar. gz](https://github.com/dotnet/spark/releases/download/v0.1.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz).</span><span class="sxs-lookup"><span data-stu-id="0312d-120">For example, if you want `.NET for Apache Spark v0.1.0` using `netcoreapp2.1`, you'd download [Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz](https://github.com/dotnet/spark/releases/download/v0.1.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz).</span></span>

2. <span data-ttu-id="0312d-121">Téléchargez `Microsoft.Spark.Worker.<release>.tar.gz` et [install-Worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) dans un système de fichiers distribués (par exemple, HDFS, WASB, ADLS) auquel votre cluster a accès.</span><span class="sxs-lookup"><span data-stu-id="0312d-121">Upload `Microsoft.Spark.Worker.<release>.tar.gz` and [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) to a distributed file system (e.g., HDFS, WASB, ADLS) that your cluster has access to.</span></span>

## <a name="prepare-your-net-for-apache-spark-app"></a><span data-ttu-id="0312d-122">Préparer votre application .NET pour Apache Spark</span><span class="sxs-lookup"><span data-stu-id="0312d-122">Prepare your .NET for Apache Spark app</span></span>

1. <span data-ttu-id="0312d-123">Suivez le didacticiel de [prise en main](get-started.md) pour créer votre application.</span><span class="sxs-lookup"><span data-stu-id="0312d-123">Follow the [Get Started](get-started.md) tutorial to build your app.</span></span>

2. <span data-ttu-id="0312d-124">Publiez votre application Spark .NET comme autonome.</span><span class="sxs-lookup"><span data-stu-id="0312d-124">Publish your Spark .NET app as self-contained.</span></span>

   <span data-ttu-id="0312d-125">Vous pouvez exécuter la commande suivante sur Linux.</span><span class="sxs-lookup"><span data-stu-id="0312d-125">You can run the following command on Linux.</span></span>

   ```bash
   dotnet publish -c Release -f netcoreapp2.1 -r ubuntu.16.04-x64
   ```

3. <span data-ttu-id="0312d-126">Produit `<your app>.zip` pour les fichiers publiés.</span><span class="sxs-lookup"><span data-stu-id="0312d-126">Produce `<your app>.zip` for the published files.</span></span>

   <span data-ttu-id="0312d-127">Vous pouvez exécuter la commande suivante sur Linux à `zip`l’aide de.</span><span class="sxs-lookup"><span data-stu-id="0312d-127">You can run the following command on Linux using `zip`.</span></span>

   ```bash
   zip -r <your app>.zip .
   ```

4. <span data-ttu-id="0312d-128">Chargez les éléments suivants dans un système de fichiers distribués (par exemple, HDFS, WASB, ADLS) auquel votre cluster a accès:</span><span class="sxs-lookup"><span data-stu-id="0312d-128">Upload the following to a distributed file system (e.g., HDFS, WASB, ADLS) that your cluster has access to:</span></span>

   * <span data-ttu-id="0312d-129">`microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar`: Ce fichier jar est inclus dans le package NuGet [Microsoft. Spark](https://www.nuget.org/packages/Microsoft.Spark/) et colocalisé dans le répertoire de sortie de la génération de votre application.</span><span class="sxs-lookup"><span data-stu-id="0312d-129">`microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar`: This jar is included as part of the [Microsoft.Spark](https://www.nuget.org/packages/Microsoft.Spark/) NuGet package and is colocated in your app's build output directory.</span></span>
   * `<your app>.zip`
   * <span data-ttu-id="0312d-130">Les fichiers (comme les fichiers de dépendance ou les données communes accessibles à chaque Worker) ou les assemblys (comme les dll qui contiennent vos fonctions `app` définies par l’utilisateur ou les bibliothèques dont dépend votre dépend) doivent être placés dans le répertoire de travail de chaque exécuteur.</span><span class="sxs-lookup"><span data-stu-id="0312d-130">Files (like dependency files or common data accessible to every worker) or Assemblies (like DLLs that contain your user-defined functions or libraries that your `app` depends on) to be placed in the working directory of each executor.</span></span>

## <a name="deploy-to-azure-hdinsight-spark"></a><span data-ttu-id="0312d-131">Déployer sur Azure HDInsight Spark</span><span class="sxs-lookup"><span data-stu-id="0312d-131">Deploy to Azure HDInsight Spark</span></span>

<span data-ttu-id="0312d-132">[Azure HDInsight Spark](https://docs.microsoft.com/azure/hdinsight/spark/apache-spark-overview) est l’implémentation Microsoft de Apache Spark dans le Cloud qui permet aux utilisateurs de lancer et de configurer des clusters Spark dans Azure.</span><span class="sxs-lookup"><span data-stu-id="0312d-132">[Azure HDInsight Spark](https://docs.microsoft.com/azure/hdinsight/spark/apache-spark-overview) is the Microsoft implementation of Apache Spark in the cloud that allows users to launch and configure Spark clusters in Azure.</span></span> <span data-ttu-id="0312d-133">Vous pouvez utiliser des clusters HDInsight Spark pour traiter vos données stockées dans le [stockage Azure](https://azure.microsoft.com/services/storage/) ou [Azure Data Lake Storage](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-use-data-lake-storage-gen2).</span><span class="sxs-lookup"><span data-stu-id="0312d-133">You can use HDInsight Spark clusters to process your data stored in [Azure Storage](https://azure.microsoft.com/services/storage/) or [Azure Data Lake Storage](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-use-data-lake-storage-gen2).</span></span>

> [!NOTE]
> <span data-ttu-id="0312d-134">Azure HDInsight Spark est basé sur Linux.</span><span class="sxs-lookup"><span data-stu-id="0312d-134">Azure HDInsight Spark is Linux-based.</span></span> <span data-ttu-id="0312d-135">Si vous souhaitez déployer votre application sur Azure HDInsight Spark, assurez-vous que votre application est .NET Standard compatible et que vous utilisez le [compilateur .net Core](https://dotnet.microsoft.com/download) pour compiler votre application.</span><span class="sxs-lookup"><span data-stu-id="0312d-135">If you are interested in deploying your app to Azure HDInsight Spark, make sure your app is .NET Standard compatible and that you use the [.NET Core compiler](https://dotnet.microsoft.com/download) to compile your app.</span></span>

### <a name="deploy-microsoftsparkworker"></a><span data-ttu-id="0312d-136">Déployer Microsoft. Spark. Worker</span><span class="sxs-lookup"><span data-stu-id="0312d-136">Deploy Microsoft.Spark.Worker</span></span>

<span data-ttu-id="0312d-137">Cette étape n’est requise qu’une seule fois pour votre cluster.</span><span class="sxs-lookup"><span data-stu-id="0312d-137">This step is only required once for your cluster.</span></span>

<span data-ttu-id="0312d-138">Exécutez `install-worker.sh` sur le cluster à l’aide des [actions de script HDInsight](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux).</span><span class="sxs-lookup"><span data-stu-id="0312d-138">Run `install-worker.sh` on the cluster using [HDInsight Script Actions](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux).</span></span>

|<span data-ttu-id="0312d-139">Paramètre</span><span class="sxs-lookup"><span data-stu-id="0312d-139">Setting</span></span>|<span data-ttu-id="0312d-140">`Value`</span><span class="sxs-lookup"><span data-stu-id="0312d-140">Value</span></span>|
|-------|-----|
|<span data-ttu-id="0312d-141">Type de script</span><span class="sxs-lookup"><span data-stu-id="0312d-141">Script type</span></span>|<span data-ttu-id="0312d-142">Personnalisé</span><span class="sxs-lookup"><span data-stu-id="0312d-142">Custom</span></span>|
|<span data-ttu-id="0312d-143">Nom</span><span class="sxs-lookup"><span data-stu-id="0312d-143">Name</span></span>|<span data-ttu-id="0312d-144">Installer Microsoft. Spark. Worker</span><span class="sxs-lookup"><span data-stu-id="0312d-144">Install Microsoft.Spark.Worker</span></span>|
|<span data-ttu-id="0312d-145">URI de script bash</span><span class="sxs-lookup"><span data-stu-id="0312d-145">Bash script URI</span></span>|<span data-ttu-id="0312d-146">URI vers lequel vous avez téléchargé `install-worker.sh`.</span><span class="sxs-lookup"><span data-stu-id="0312d-146">The URI to which you uploaded `install-worker.sh`.</span></span> <span data-ttu-id="0312d-147">Par exemple, `abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/install-worker.sh`.</span><span class="sxs-lookup"><span data-stu-id="0312d-147">For example, `abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/install-worker.sh`</span></span>|
|<span data-ttu-id="0312d-148">Type (s) de nœud</span><span class="sxs-lookup"><span data-stu-id="0312d-148">Node type(s)</span></span>|<span data-ttu-id="0312d-149">Collabor</span><span class="sxs-lookup"><span data-stu-id="0312d-149">Worker</span></span>|
|<span data-ttu-id="0312d-150">Paramètres</span><span class="sxs-lookup"><span data-stu-id="0312d-150">Parameters</span></span>|<span data-ttu-id="0312d-151">Paramètres de `install-worker.sh`.</span><span class="sxs-lookup"><span data-stu-id="0312d-151">Parameters to `install-worker.sh`.</span></span> <span data-ttu-id="0312d-152">Par exemple, si vous avez chargé `install-worker.sh` dans Azure Data Lake Gen 2, il `azure abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/Microsoft.Spark.Worker.<release>.tar.gz /usr/local/bin`s’agit de.</span><span class="sxs-lookup"><span data-stu-id="0312d-152">For example, if you uploaded `install-worker.sh` to Azure Data Lake Gen 2 then it would be `azure abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/Microsoft.Spark.Worker.<release>.tar.gz /usr/local/bin`.</span></span>|

![Image d’action de script](./media/hdinsight-deployment/deployment-hdi-action-script.png)

## <a name="run-your-app"></a><span data-ttu-id="0312d-154">Exécuter votre application</span><span class="sxs-lookup"><span data-stu-id="0312d-154">Run your app</span></span>

<span data-ttu-id="0312d-155">Vous pouvez soumettre votre travail à Azure HDInsight à `spark-submit` l’aide de ou d’Apache livy.</span><span class="sxs-lookup"><span data-stu-id="0312d-155">You can submit your job to Azure HDInsight using `spark-submit` or Apache Livy.</span></span>

### <a name="use-spark-submit"></a><span data-ttu-id="0312d-156">Utiliser Spark-Submit</span><span class="sxs-lookup"><span data-stu-id="0312d-156">Use spark-submit</span></span>

<span data-ttu-id="0312d-157">Vous pouvez utiliser la commande [Spark-Submit](https://spark.apache.org/docs/latest/submitting-applications.html) pour soumettre des travaux .net pour Apache Spark à Azure HDInsight.</span><span class="sxs-lookup"><span data-stu-id="0312d-157">You can use the [spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html) command to submit .NET for Apache Spark jobs to Azure HDInsight.</span></span>
 
1. <span data-ttu-id="0312d-158">`ssh`dans l’un des nœuds principaux de votre cluster.</span><span class="sxs-lookup"><span data-stu-id="0312d-158">`ssh` into one of the head nodes in your cluster.</span></span>

1. <span data-ttu-id="0312d-159">Exécutez `spark-submit`:</span><span class="sxs-lookup"><span data-stu-id="0312d-159">Run `spark-submit`:</span></span>

   ```bash
   spark-submit \
   --master yarn \
   --class org.apache.spark.deploy.DotnetRunner \
   --files <comma-separated list of assemblies that contain UDF definitions, if any> \
   abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar \
   abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/<your app>.zip <your app> <app arg 1> <app arg 2> ... <app arg n>
   ```

### <a name="use-apache-livy"></a><span data-ttu-id="0312d-160">Utiliser Apache livy</span><span class="sxs-lookup"><span data-stu-id="0312d-160">Use Apache Livy</span></span>

<span data-ttu-id="0312d-161">Vous pouvez utiliser [Apache livy](https://livy.incubator.apache.org/), l’API REST Apache Spark, pour soumettre des travaux .net pour Apache Spark à un cluster Azure HDInsight Spark.</span><span class="sxs-lookup"><span data-stu-id="0312d-161">You can use [Apache Livy](https://livy.incubator.apache.org/), the Apache Spark REST API, to submit .NET for Apache Spark jobs to an Azure HDInsight Spark cluster.</span></span> <span data-ttu-id="0312d-162">Pour plus d’informations, consultez [tâches à distance avec Apache livy](https://docs.microsoft.com/azure/hdinsight/spark/apache-spark-livy-rest-interface).</span><span class="sxs-lookup"><span data-stu-id="0312d-162">For more information, see [Remote jobs with Apache Livy](https://docs.microsoft.com/azure/hdinsight/spark/apache-spark-livy-rest-interface).</span></span>

<span data-ttu-id="0312d-163">Vous pouvez exécuter la commande suivante sur Linux à `curl`l’aide de:</span><span class="sxs-lookup"><span data-stu-id="0312d-163">You can run the following command on Linux using `curl`:</span></span>

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

## <a name="next-steps"></a><span data-ttu-id="0312d-164">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="0312d-164">Next steps</span></span>

<span data-ttu-id="0312d-165">Dans ce didacticiel, vous avez déployé votre application .NET pour Apache Spark sur Azure HDInsight.</span><span class="sxs-lookup"><span data-stu-id="0312d-165">In this tutorial, you deployed your .NET for Apache Spark application to Azure HDInsight.</span></span> <span data-ttu-id="0312d-166">Pour en savoir plus sur HDInsight, consultez la documentation Azure HDInsight.</span><span class="sxs-lookup"><span data-stu-id="0312d-166">To learn more about HDInsight, continue to the Azure HDInsight Documentation.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="0312d-167">Documentation Azure HDInsight</span><span class="sxs-lookup"><span data-stu-id="0312d-167">Azure HDInsight Documentation</span></span>](https://docs.microsoft.com/azure/hdinsight/)
