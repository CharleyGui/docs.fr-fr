---
title: Soumettez un .NET pour Apache Spark à Azure HDInsight
description: Apprenez à soumettre un .NET pour Apache Spark à Azure HDInsight à l’aide d’étincelles-soumettre et Apache Livy.
ms.date: 11/19/2019
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 83359f7f613b500a4ce121ce1612cda0ad1191ab
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79185800"
---
# <a name="submit-a-net-for-apache-spark-job-to-azure-hdinsight"></a><span data-ttu-id="b739a-103">Soumettez un .NET pour Apache Spark à Azure HDInsight</span><span class="sxs-lookup"><span data-stu-id="b739a-103">Submit a .NET for Apache Spark job to Azure HDInsight</span></span>

<span data-ttu-id="b739a-104">Il existe deux façons de déployer votre .NET pour `spark-submit` Apache Spark travail à HDInsight: et Apache Livy.</span><span class="sxs-lookup"><span data-stu-id="b739a-104">There are two ways to deploy your .NET for Apache Spark job to HDInsight: `spark-submit` and Apache Livy.</span></span>

## <a name="deploy-using-spark-submit"></a><span data-ttu-id="b739a-105">Déploiement à l’aide d’étincelles-soumettre</span><span class="sxs-lookup"><span data-stu-id="b739a-105">Deploy using spark-submit</span></span>

<span data-ttu-id="b739a-106">Vous pouvez utiliser la commande [spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html) pour soumettre des travaux .NET pour Apache Spark à Azure HDInsight.</span><span class="sxs-lookup"><span data-stu-id="b739a-106">You can use the [spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html) command to submit .NET for Apache Spark jobs to Azure HDInsight.</span></span>

1. <span data-ttu-id="b739a-107">Naviguez vers votre cluster HDInsight Spark dans le portail Azure, puis sélectionnez **la connexion SSH et Cluster**.</span><span class="sxs-lookup"><span data-stu-id="b739a-107">Navigate to your HDInsight Spark cluster in Azure portal, and then select **SSH + Cluster login**.</span></span>

2. <span data-ttu-id="b739a-108">Copiez les informations de connexion ssh et collez la connexion dans un terminal.</span><span class="sxs-lookup"><span data-stu-id="b739a-108">Copy the ssh login information and paste the login into a terminal.</span></span> <span data-ttu-id="b739a-109">Connectez-vous à votre cluster à l’aide du mot de passe que vous avez défini lors de la création du cluster.</span><span class="sxs-lookup"><span data-stu-id="b739a-109">Sign in to your cluster using the password you set during cluster creation.</span></span> <span data-ttu-id="b739a-110">Vous devriez voir des messages vous accueillant à Ubuntu et Spark.</span><span class="sxs-lookup"><span data-stu-id="b739a-110">You should see messages welcoming you to Ubuntu and Spark.</span></span>

3. <span data-ttu-id="b739a-111">Utilisez la commande **spark-submit** pour exécuter votre application sur votre cluster HDInsight.</span><span class="sxs-lookup"><span data-stu-id="b739a-111">Use the **spark-submit** command to run your app on your HDInsight cluster.</span></span> <span data-ttu-id="b739a-112">N’oubliez pas de remplacer **mycontainer** et **mystorageaccount** dans le script de l’exemple avec les noms réels de votre conteneur blob et compte de stockage.</span><span class="sxs-lookup"><span data-stu-id="b739a-112">Remember to replace **mycontainer** and **mystorageaccount** in the example script with the actual names of your blob container and storage account.</span></span> <span data-ttu-id="b739a-113">Aussi, assurez-vous `microsoft-spark-2.3.x-0.6.0.jar` de remplacer par le fichier de pot approprié que vous utilisez pour le déploiement.</span><span class="sxs-lookup"><span data-stu-id="b739a-113">Also, be sure to replace `microsoft-spark-2.3.x-0.6.0.jar` with the appropriate jar file you're using for deployment.</span></span> <span data-ttu-id="b739a-114">`2.3.x`représente la version d’Apache Spark, et `0.6.0` représente la version de la [.NET pour Apache Spark travailleur](https://github.com/dotnet/spark/releases).</span><span class="sxs-lookup"><span data-stu-id="b739a-114">`2.3.x` represents the version of Apache Spark, and `0.6.0` represents the version of the [.NET for Apache Spark worker](https://github.com/dotnet/spark/releases).</span></span>

   ```bash
   $SPARK_HOME/bin/spark-submit \
   --master yarn \
   --class org.apache.spark.deploy.dotnet.DotnetRunner \
   wasbs://mycontainer@mystorageaccount.blob.core.windows.net/microsoft-spark-2.3.x-0.6.0.jar \
   wasbs://mycontainer@mystorageaccount.blob.core.windows.net/publish.zip mySparkApp
   ```

## <a name="deploy-using-apache-livy"></a><span data-ttu-id="b739a-115">Déploiement à l’aide d’Apache Livy</span><span class="sxs-lookup"><span data-stu-id="b739a-115">Deploy using Apache Livy</span></span>

<span data-ttu-id="b739a-116">Vous pouvez utiliser [Apache Livy](https://livy.incubator.apache.org/), l’API REST d’Apache Spark, pour soumettre des travaux .NET pour Apache Spark à un cluster Azure HDInsight Spark.</span><span class="sxs-lookup"><span data-stu-id="b739a-116">You can use [Apache Livy](https://livy.incubator.apache.org/), the Apache Spark REST API, to submit .NET for Apache Spark jobs to an Azure HDInsight Spark cluster.</span></span> <span data-ttu-id="b739a-117">Pour plus d’informations, consultez [Travaux à distance avec Apache Livy](https://docs.microsoft.com/azure/hdinsight/spark/apache-spark-livy-rest-interface).</span><span class="sxs-lookup"><span data-stu-id="b739a-117">For more information, see [Remote jobs with Apache Livy](https://docs.microsoft.com/azure/hdinsight/spark/apache-spark-livy-rest-interface).</span></span>

<span data-ttu-id="b739a-118">Vous pouvez exécuter la commande suivante sur Linux en utilisant `curl` :</span><span class="sxs-lookup"><span data-stu-id="b739a-118">You can run the following command on Linux using `curl`:</span></span>

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

## <a name="next-steps"></a><span data-ttu-id="b739a-119">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="b739a-119">Next steps</span></span>

* [<span data-ttu-id="b739a-120">Bien démarrer avec .NET pour Apache Spark</span><span class="sxs-lookup"><span data-stu-id="b739a-120">Get started with .NET for Apache Spark</span></span>](../tutorials/get-started.md)
* [<span data-ttu-id="b739a-121">Déployer une application .NET pour Apache Spark sur Azure HDInsight</span><span class="sxs-lookup"><span data-stu-id="b739a-121">Deploy a .NET for Apache Spark application to Azure HDInsight</span></span>](../tutorials/hdinsight-deployment.md)
* [<span data-ttu-id="b739a-122">HDInsight Documentation</span><span class="sxs-lookup"><span data-stu-id="b739a-122">HDInsight Documentation</span></span>](https://docs.microsoft.com/azure/hdinsight/)
