---
title: Envoyer un travail .NET pour Apache Spark à Azure HDInsight
description: Découvrez comment soumettre un travail .NET pour Apache Spark à Azure HDInsight à l’aide de Spark-Submit et d’Apache livy.
ms.date: 10/09/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: cb99cd8028d504924d2dd69910efed0065d0a2e2
ms.sourcegitcommit: b59237ca4ec763969a0dd775a3f8f39f8c59fe24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2020
ms.locfileid: "91954917"
---
# <a name="submit-a-net-for-apache-spark-job-to-azure-hdinsight"></a><span data-ttu-id="8f2e2-103">Envoyer un travail .NET pour Apache Spark à Azure HDInsight</span><span class="sxs-lookup"><span data-stu-id="8f2e2-103">Submit a .NET for Apache Spark job to Azure HDInsight</span></span>

<span data-ttu-id="8f2e2-104">Il existe deux façons de déployer votre .NET pour Apache Spark travail sur HDInsight : `spark-submit` et Apache livy.</span><span class="sxs-lookup"><span data-stu-id="8f2e2-104">There are two ways to deploy your .NET for Apache Spark job to HDInsight: `spark-submit` and Apache Livy.</span></span>

## <a name="deploy-using-spark-submit"></a><span data-ttu-id="8f2e2-105">Déployer à l’aide de Spark-Submit</span><span class="sxs-lookup"><span data-stu-id="8f2e2-105">Deploy using spark-submit</span></span>

<span data-ttu-id="8f2e2-106">Vous pouvez utiliser la commande [spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html) pour soumettre des travaux .NET pour Apache Spark à Azure HDInsight.</span><span class="sxs-lookup"><span data-stu-id="8f2e2-106">You can use the [spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html) command to submit .NET for Apache Spark jobs to Azure HDInsight.</span></span>

1. <span data-ttu-id="8f2e2-107">Accédez à votre cluster HDInsight Spark dans Portail Azure, puis sélectionnez **SSH + connexion au cluster**.</span><span class="sxs-lookup"><span data-stu-id="8f2e2-107">Navigate to your HDInsight Spark cluster in Azure portal, and then select **SSH + Cluster login**.</span></span>

2. <span data-ttu-id="8f2e2-108">Copiez les informations de connexion SSH et collez la connexion dans un terminal.</span><span class="sxs-lookup"><span data-stu-id="8f2e2-108">Copy the ssh login information and paste the login into a terminal.</span></span> <span data-ttu-id="8f2e2-109">Connectez-vous à votre cluster à l’aide du mot de passe que vous avez défini lors de la création du cluster.</span><span class="sxs-lookup"><span data-stu-id="8f2e2-109">Sign in to your cluster using the password you set during cluster creation.</span></span> <span data-ttu-id="8f2e2-110">Vous devriez voir des messages vous préversant Ubuntu et Spark.</span><span class="sxs-lookup"><span data-stu-id="8f2e2-110">You should see messages welcoming you to Ubuntu and Spark.</span></span>

3. <span data-ttu-id="8f2e2-111">Utilisez la commande **Spark-Submit** pour exécuter votre application sur votre cluster HDInsight.</span><span class="sxs-lookup"><span data-stu-id="8f2e2-111">Use the **spark-submit** command to run your app on your HDInsight cluster.</span></span> <span data-ttu-id="8f2e2-112">N’oubliez pas de remplacer **mycontainer** et **mystorageaccount** dans l’exemple de script par les noms réels de votre conteneur d’objets BLOB et de votre compte de stockage.</span><span class="sxs-lookup"><span data-stu-id="8f2e2-112">Remember to replace **mycontainer** and **mystorageaccount** in the example script with the actual names of your blob container and storage account.</span></span> <span data-ttu-id="8f2e2-113">Veillez également à remplacer `microsoft-spark-2.3.x-0.6.0.jar` par le fichier jar approprié que vous utilisez pour le déploiement.</span><span class="sxs-lookup"><span data-stu-id="8f2e2-113">Also, be sure to replace `microsoft-spark-2.3.x-0.6.0.jar` with the appropriate jar file you're using for deployment.</span></span> <span data-ttu-id="8f2e2-114">`2.3.x` représente la version de Apache Spark et `0.6.0` représente la version de [.net pour Apache Spark Worker](https://github.com/dotnet/spark/releases).</span><span class="sxs-lookup"><span data-stu-id="8f2e2-114">`2.3.x` represents the version of Apache Spark, and `0.6.0` represents the version of the [.NET for Apache Spark worker](https://github.com/dotnet/spark/releases).</span></span>

   ```bash
   $SPARK_HOME/bin/spark-submit \
   --master yarn \
   --class org.apache.spark.deploy.dotnet.DotnetRunner \
   wasbs://mycontainer@mystorageaccount.blob.core.windows.net/microsoft-spark-2.3.x-0.6.0.jar \
   wasbs://mycontainer@mystorageaccount.blob.core.windows.net/publish.zip mySparkApp
   ```

## <a name="deploy-using-apache-livy"></a><span data-ttu-id="8f2e2-115">Déployer à l’aide d’Apache livy</span><span class="sxs-lookup"><span data-stu-id="8f2e2-115">Deploy using Apache Livy</span></span>

<span data-ttu-id="8f2e2-116">Vous pouvez utiliser [Apache Livy](https://livy.incubator.apache.org/), l’API REST d’Apache Spark, pour soumettre des travaux .NET pour Apache Spark à un cluster Azure HDInsight Spark.</span><span class="sxs-lookup"><span data-stu-id="8f2e2-116">You can use [Apache Livy](https://livy.incubator.apache.org/), the Apache Spark REST API, to submit .NET for Apache Spark jobs to an Azure HDInsight Spark cluster.</span></span> <span data-ttu-id="8f2e2-117">Pour plus d’informations, consultez [Travaux à distance avec Apache Livy](/azure/hdinsight/spark/apache-spark-livy-rest-interface).</span><span class="sxs-lookup"><span data-stu-id="8f2e2-117">For more information, see [Remote jobs with Apache Livy](/azure/hdinsight/spark/apache-spark-livy-rest-interface).</span></span>

<span data-ttu-id="8f2e2-118">Vous pouvez exécuter la commande suivante sur Linux en utilisant `curl` :</span><span class="sxs-lookup"><span data-stu-id="8f2e2-118">You can run the following command on Linux using `curl`:</span></span>

```bash
curl -k -v -X POST "https://<your spark cluster>.azurehdinsight.net/livy/batches" \
-u "<hdinsight username>:<hdinsight password>" \
-H "Content-Type: application/json" \
-H "X-Requested-By: <hdinsight username>" \
-d @- << EOF
{
    "file":"abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar",
    "className":"org.apache.spark.deploy.dotnet.DotnetRunner",
    "files":["abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/<udf assembly>", "abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/<file>"],
    "args":["abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/<your app>.zip","<your app>","<app arg 1>","<app arg 2>,"...","<app arg n>"]
}
EOF
```

## <a name="next-steps"></a><span data-ttu-id="8f2e2-119">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="8f2e2-119">Next steps</span></span>

* [<span data-ttu-id="8f2e2-120">Bien démarrer avec .NET pour Apache Spark</span><span class="sxs-lookup"><span data-stu-id="8f2e2-120">Get started with .NET for Apache Spark</span></span>](../tutorials/get-started.md)
* [<span data-ttu-id="8f2e2-121">Déployer une application .NET pour Apache Spark sur Azure HDInsight</span><span class="sxs-lookup"><span data-stu-id="8f2e2-121">Deploy a .NET for Apache Spark application to Azure HDInsight</span></span>](../tutorials/hdinsight-deployment.md)
* [<span data-ttu-id="8f2e2-122">Documentation HDInsight</span><span class="sxs-lookup"><span data-stu-id="8f2e2-122">HDInsight Documentation</span></span>](/azure/hdinsight/)
