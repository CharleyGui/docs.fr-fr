---
title: Envoyer un travail .NET pour Apache Spark à Azure HDInsight
description: Découvrez comment soumettre un travail .NET pour Apache Spark à Azure HDInsight à l’aide de Spark-Submit et d’Apache livy.
ms.date: 10/09/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 74be4ecf33a9a881633da0630fa1c1a4bf0b19c6
ms.sourcegitcommit: 34968a61e9bac0f6be23ed6ffb837f52d2390c85
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94688161"
---
# <a name="submit-a-net-for-apache-spark-job-to-azure-hdinsight"></a><span data-ttu-id="f4f90-103">Envoyer un travail .NET pour Apache Spark à Azure HDInsight</span><span class="sxs-lookup"><span data-stu-id="f4f90-103">Submit a .NET for Apache Spark job to Azure HDInsight</span></span>

<span data-ttu-id="f4f90-104">Il existe deux façons de déployer votre .NET pour Apache Spark travail sur HDInsight : `spark-submit` et Apache livy.</span><span class="sxs-lookup"><span data-stu-id="f4f90-104">There are two ways to deploy your .NET for Apache Spark job to HDInsight: `spark-submit` and Apache Livy.</span></span>

## <a name="deploy-using-spark-submit"></a><span data-ttu-id="f4f90-105">Déployer à l’aide de Spark-Submit</span><span class="sxs-lookup"><span data-stu-id="f4f90-105">Deploy using spark-submit</span></span>

<span data-ttu-id="f4f90-106">Vous pouvez utiliser la commande [spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html) pour soumettre des travaux .NET pour Apache Spark à Azure HDInsight.</span><span class="sxs-lookup"><span data-stu-id="f4f90-106">You can use the [spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html) command to submit .NET for Apache Spark jobs to Azure HDInsight.</span></span>

1. <span data-ttu-id="f4f90-107">Accédez à votre cluster HDInsight Spark dans Portail Azure, puis sélectionnez **SSH + connexion au cluster**.</span><span class="sxs-lookup"><span data-stu-id="f4f90-107">Navigate to your HDInsight Spark cluster in Azure portal, and then select **SSH + Cluster login**.</span></span>

2. <span data-ttu-id="f4f90-108">Copiez les informations de connexion SSH et collez la connexion dans un terminal.</span><span class="sxs-lookup"><span data-stu-id="f4f90-108">Copy the ssh login information and paste the login into a terminal.</span></span> <span data-ttu-id="f4f90-109">Connectez-vous à votre cluster à l’aide du mot de passe que vous avez défini lors de la création du cluster.</span><span class="sxs-lookup"><span data-stu-id="f4f90-109">Sign in to your cluster using the password you set during cluster creation.</span></span> <span data-ttu-id="f4f90-110">Vous devriez voir des messages vous préversant Ubuntu et Spark.</span><span class="sxs-lookup"><span data-stu-id="f4f90-110">You should see messages welcoming you to Ubuntu and Spark.</span></span>

3. <span data-ttu-id="f4f90-111">Utilisez la commande **Spark-Submit** pour exécuter votre application sur votre cluster HDInsight.</span><span class="sxs-lookup"><span data-stu-id="f4f90-111">Use the **spark-submit** command to run your app on your HDInsight cluster.</span></span> <span data-ttu-id="f4f90-112">N’oubliez pas de remplacer **mycontainer** et **mystorageaccount** dans l’exemple de script par les noms réels de votre conteneur d’objets BLOB et de votre compte de stockage.</span><span class="sxs-lookup"><span data-stu-id="f4f90-112">Remember to replace **mycontainer** and **mystorageaccount** in the example script with the actual names of your blob container and storage account.</span></span> <span data-ttu-id="f4f90-113">N’oubliez pas également de remplacer le fichier jar Microsoft-Spark par la version Spark et .NET pour Apache Spark utilisé.</span><span class="sxs-lookup"><span data-stu-id="f4f90-113">Also remember to replace the microsoft-spark jar with the version of Spark and .NET for Apache Spark being used.</span></span>

   ```bash
   $SPARK_HOME/bin/spark-submit \
   --master yarn \
   --class org.apache.spark.deploy.dotnet.DotnetRunner \
   wasbs://mycontainer@mystorageaccount.blob.core.windows.net/microsoft-spark-<spark_majorversion-spark_minorversion>_<scala_majorversion.scala_minorversion>-<spark_dotnet_version>.jar \
   wasbs://mycontainer@mystorageaccount.blob.core.windows.net/publish.zip mySparkApp
   ```

## <a name="deploy-using-apache-livy"></a><span data-ttu-id="f4f90-114">Déployer à l’aide d’Apache livy</span><span class="sxs-lookup"><span data-stu-id="f4f90-114">Deploy using Apache Livy</span></span>

<span data-ttu-id="f4f90-115">Vous pouvez utiliser [Apache Livy](https://livy.incubator.apache.org/), l’API REST d’Apache Spark, pour soumettre des travaux .NET pour Apache Spark à un cluster Azure HDInsight Spark.</span><span class="sxs-lookup"><span data-stu-id="f4f90-115">You can use [Apache Livy](https://livy.incubator.apache.org/), the Apache Spark REST API, to submit .NET for Apache Spark jobs to an Azure HDInsight Spark cluster.</span></span> <span data-ttu-id="f4f90-116">Pour plus d’informations, consultez [Travaux à distance avec Apache Livy](/azure/hdinsight/spark/apache-spark-livy-rest-interface).</span><span class="sxs-lookup"><span data-stu-id="f4f90-116">For more information, see [Remote jobs with Apache Livy](/azure/hdinsight/spark/apache-spark-livy-rest-interface).</span></span>

<span data-ttu-id="f4f90-117">Vous pouvez exécuter la commande suivante sur Linux en utilisant `curl` :</span><span class="sxs-lookup"><span data-stu-id="f4f90-117">You can run the following command on Linux using `curl`:</span></span>

```bash
curl -k -v -X POST "https://<your spark cluster>.azurehdinsight.net/livy/batches" \
-u "<hdinsight username>:<hdinsight password>" \
-H "Content-Type: application/json" \
-H "X-Requested-By: <hdinsight username>" \
-d @- << EOF
{
    "file":"abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/microsoft-spark-<spark_majorversion-spark_minorversion>_<scala_majorversion.scala_minorversion>-<spark_dotnet_version>.jar",
    "className":"org.apache.spark.deploy.dotnet.DotnetRunner",
    "files":["abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/<udf assembly>", "abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/<file>"],
    "args":["abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/<your app>.zip","<your app>","<app arg 1>","<app arg 2>,"...","<app arg n>"]
}
EOF
```

## <a name="next-steps"></a><span data-ttu-id="f4f90-118">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="f4f90-118">Next steps</span></span>

* [<span data-ttu-id="f4f90-119">Bien démarrer avec .NET pour Apache Spark</span><span class="sxs-lookup"><span data-stu-id="f4f90-119">Get started with .NET for Apache Spark</span></span>](../tutorials/get-started.md)
* [<span data-ttu-id="f4f90-120">Déployer une application .NET pour Apache Spark sur Azure HDInsight</span><span class="sxs-lookup"><span data-stu-id="f4f90-120">Deploy a .NET for Apache Spark application to Azure HDInsight</span></span>](../tutorials/hdinsight-deployment.md)
* [<span data-ttu-id="f4f90-121">Documentation HDInsight</span><span class="sxs-lookup"><span data-stu-id="f4f90-121">HDInsight Documentation</span></span>](/azure/hdinsight/)
