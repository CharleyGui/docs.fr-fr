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
# <a name="submit-a-net-for-apache-spark-job-to-azure-hdinsight"></a>Envoyer un travail .NET pour Apache Spark à Azure HDInsight

Il existe deux façons de déployer votre .NET pour Apache Spark travail sur HDInsight : `spark-submit` et Apache livy.

## <a name="deploy-using-spark-submit"></a>Déployer à l’aide de Spark-Submit

Vous pouvez utiliser la commande [spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html) pour soumettre des travaux .NET pour Apache Spark à Azure HDInsight.

1. Accédez à votre cluster HDInsight Spark dans Portail Azure, puis sélectionnez **SSH + connexion au cluster**.

2. Copiez les informations de connexion SSH et collez la connexion dans un terminal. Connectez-vous à votre cluster à l’aide du mot de passe que vous avez défini lors de la création du cluster. Vous devriez voir des messages vous préversant Ubuntu et Spark.

3. Utilisez la commande **Spark-Submit** pour exécuter votre application sur votre cluster HDInsight. N’oubliez pas de remplacer **mycontainer** et **mystorageaccount** dans l’exemple de script par les noms réels de votre conteneur d’objets BLOB et de votre compte de stockage. Veillez également à remplacer `microsoft-spark-2.3.x-0.6.0.jar` par le fichier jar approprié que vous utilisez pour le déploiement. `2.3.x` représente la version de Apache Spark et `0.6.0` représente la version de [.net pour Apache Spark Worker](https://github.com/dotnet/spark/releases).

   ```bash
   $SPARK_HOME/bin/spark-submit \
   --master yarn \
   --class org.apache.spark.deploy.dotnet.DotnetRunner \
   wasbs://mycontainer@mystorageaccount.blob.core.windows.net/microsoft-spark-2.3.x-0.6.0.jar \
   wasbs://mycontainer@mystorageaccount.blob.core.windows.net/publish.zip mySparkApp
   ```

## <a name="deploy-using-apache-livy"></a>Déployer à l’aide d’Apache livy

Vous pouvez utiliser [Apache Livy](https://livy.incubator.apache.org/), l’API REST d’Apache Spark, pour soumettre des travaux .NET pour Apache Spark à un cluster Azure HDInsight Spark. Pour plus d’informations, consultez [Travaux à distance avec Apache Livy](/azure/hdinsight/spark/apache-spark-livy-rest-interface).

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
* [Documentation HDInsight](/azure/hdinsight/)
