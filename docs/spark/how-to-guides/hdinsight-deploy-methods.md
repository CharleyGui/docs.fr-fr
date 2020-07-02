---
title: Envoyer un travail .NET pour Apache Spark à Azure HDInsight
description: Découvrez comment soumettre un travail .NET pour Apache Spark à Azure HDInsight à l’aide de Spark-Submit et d’Apache livy.
ms.date: 06/25/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 50611b1f62934a446e5b80a8c53698efe23cd1fc
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617689"
---
# <a name="submit-a-net-for-apache-spark-job-to-azure-hdinsight"></a>Envoyer un travail .NET pour Apache Spark à Azure HDInsight

Il existe deux façons de déployer votre .NET pour Apache Spark travail sur HDInsight : `spark-submit` et Apache livy.

[!INCLUDE [spark-preview-note](../../../includes/spark-preview-note.md)]

## <a name="deploy-using-spark-submit"></a>Déployer à l’aide de Spark-Submit

Vous pouvez utiliser la commande [spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html) pour soumettre des travaux .NET pour Apache Spark à Azure HDInsight.

1. Accédez à votre cluster HDInsight Spark dans Portail Azure, puis sélectionnez **SSH + connexion au cluster**.

2. Copiez les informations de connexion SSH et collez la connexion dans un terminal. Connectez-vous à votre cluster à l’aide du mot de passe que vous avez défini lors de la création du cluster. Vous devriez voir des messages vous préversant Ubuntu et Spark.

3. Utilisez la commande **Spark-Submit** pour exécuter votre application sur votre cluster HDInsight. N’oubliez pas de remplacer **mycontainer** et **mystorageaccount** dans l’exemple de script par les noms réels de votre conteneur d’objets BLOB et de votre compte de stockage. Veillez également à remplacer `microsoft-spark-2.3.x-0.6.0.jar` par le fichier jar approprié que vous utilisez pour le déploiement. `2.3.x`représente la version de Apache Spark et `0.6.0` représente la version de [.net pour Apache Spark Worker](https://github.com/dotnet/spark/releases).

   ```bash
   $SPARK_HOME/bin/spark-submit \
   --master yarn \
   --class org.apache.spark.deploy.dotnet.DotnetRunner \
   wasbs://mycontainer@mystorageaccount.blob.core.windows.net/microsoft-spark-2.3.x-0.6.0.jar \
   wasbs://mycontainer@mystorageaccount.blob.core.windows.net/publish.zip mySparkApp
   ```

## <a name="deploy-using-apache-livy"></a>Déployer à l’aide d’Apache livy

Vous pouvez utiliser [Apache Livy](https://livy.incubator.apache.org/), l’API REST d’Apache Spark, pour soumettre des travaux .NET pour Apache Spark à un cluster Azure HDInsight Spark. Pour plus d’informations, consultez [Travaux à distance avec Apache Livy](https://docs.microsoft.com/azure/hdinsight/spark/apache-spark-livy-rest-interface).

Vous pouvez exécuter la commande suivante sur Linux en utilisant `curl` :

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

## <a name="next-steps"></a>Étapes suivantes

* [Bien démarrer avec .NET pour Apache Spark](../tutorials/get-started.md)
* [Déployer une application .NET pour Apache Spark sur Azure HDInsight](../tutorials/hdinsight-deployment.md)
* [Documentation HDInsight](https://docs.microsoft.com/azure/hdinsight/)
