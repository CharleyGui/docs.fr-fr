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
# <a name="deploy-a-net-for-apache-spark-application-to-azure-hdinsight"></a>Déployer une application .NET pour Apache Spark sur Azure HDInsight

Ce didacticiel explique comment déployer une application .NET pour Apache Spark sur Azure HDInsight.

Ce tutoriel vous montre comment effectuer les opérations suivantes :

> [!div class="checklist"]
> * Préparer Microsoft. Spark. Worker
> * Publier votre application Spark .NET
> * Déployer votre application sur Azure HDInsight
> * Exécuter votre application

## <a name="prerequisites"></a>Prérequis

Avant de commencer, procédez comme suit:

* Téléchargez [Explorateur stockage Azure](https://azure.microsoft.com/features/storage-explorer/).
* Téléchargez [install-Worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) sur votre ordinateur local. Il s’agit d’un script d’assistance que vous utilisez ultérieurement pour copier .NET pour Apache Spark fichiers dépendants dans les nœuds Worker du cluster Spark.

## <a name="prepare-worker-dependencies"></a>Préparer les dépendances de Worker

**Microsoft. Spark. Worker** est un composant principal qui réside sur les nœuds Worker individuels de votre cluster Spark. Lorsque vous souhaitez exécuter une C# fonction définie par l’utilisateur (UDF), Spark doit comprendre comment lancer le CLR .net pour exécuter l’UDF. **Microsoft. Spark. Worker** fournit une collection de classes à Spark qui activent cette fonctionnalité.

1. Sélectionnez une version de netcoreapp de [Microsoft. Spark. Worker](https://github.com/dotnet/spark/releases) Linux à déployer sur votre cluster.

   Par exemple, si vous souhaitez `.NET for Apache Spark v0.1.0` utiliser `netcoreapp2.1`, vous devez télécharger [Microsoft. Spark. Worker. netcoreapp 2.1. Linux-x64-0.1.0. tar. gz](https://github.com/dotnet/spark/releases/download/v0.1.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz).

2. Téléchargez `Microsoft.Spark.Worker.<release>.tar.gz` et [install-Worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) dans un système de fichiers distribués (par exemple, HDFS, WASB, ADLS) auquel votre cluster a accès.

## <a name="prepare-your-net-for-apache-spark-app"></a>Préparer votre application .NET pour Apache Spark

1. Suivez le didacticiel de [prise en main](get-started.md) pour créer votre application.

2. Publiez votre application Spark .NET comme autonome.

   Vous pouvez exécuter la commande suivante sur Linux.

   ```bash
   dotnet publish -c Release -f netcoreapp2.1 -r ubuntu.16.04-x64
   ```

3. Produit `<your app>.zip` pour les fichiers publiés.

   Vous pouvez exécuter la commande suivante sur Linux à `zip`l’aide de.

   ```bash
   zip -r <your app>.zip .
   ```

4. Chargez les éléments suivants dans un système de fichiers distribués (par exemple, HDFS, WASB, ADLS) auquel votre cluster a accès:

   * `microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar`: Ce fichier jar est inclus dans le package NuGet [Microsoft. Spark](https://www.nuget.org/packages/Microsoft.Spark/) et colocalisé dans le répertoire de sortie de la génération de votre application.
   * `<your app>.zip`
   * Les fichiers (comme les fichiers de dépendance ou les données communes accessibles à chaque Worker) ou les assemblys (comme les dll qui contiennent vos fonctions `app` définies par l’utilisateur ou les bibliothèques dont dépend votre dépend) doivent être placés dans le répertoire de travail de chaque exécuteur.

## <a name="deploy-to-azure-hdinsight-spark"></a>Déployer sur Azure HDInsight Spark

[Azure HDInsight Spark](https://docs.microsoft.com/azure/hdinsight/spark/apache-spark-overview) est l’implémentation Microsoft de Apache Spark dans le Cloud qui permet aux utilisateurs de lancer et de configurer des clusters Spark dans Azure. Vous pouvez utiliser des clusters HDInsight Spark pour traiter vos données stockées dans le [stockage Azure](https://azure.microsoft.com/services/storage/) ou [Azure Data Lake Storage](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-use-data-lake-storage-gen2).

> [!NOTE]
> Azure HDInsight Spark est basé sur Linux. Si vous souhaitez déployer votre application sur Azure HDInsight Spark, assurez-vous que votre application est .NET Standard compatible et que vous utilisez le [compilateur .net Core](https://dotnet.microsoft.com/download) pour compiler votre application.

### <a name="deploy-microsoftsparkworker"></a>Déployer Microsoft. Spark. Worker

Cette étape n’est requise qu’une seule fois pour votre cluster.

Exécutez `install-worker.sh` sur le cluster à l’aide des [actions de script HDInsight](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux).

|Paramètre|`Value`|
|-------|-----|
|Type de script|Personnalisé|
|Nom|Installer Microsoft. Spark. Worker|
|URI de script bash|URI vers lequel vous avez téléchargé `install-worker.sh`. Par exemple, `abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/install-worker.sh`.|
|Type (s) de nœud|Collabor|
|Paramètres|Paramètres de `install-worker.sh`. Par exemple, si vous avez chargé `install-worker.sh` dans Azure Data Lake Gen 2, il `azure abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/Microsoft.Spark.Worker.<release>.tar.gz /usr/local/bin`s’agit de.|

![Image d’action de script](./media/hdinsight-deployment/deployment-hdi-action-script.png)

## <a name="run-your-app"></a>Exécuter votre application

Vous pouvez soumettre votre travail à Azure HDInsight à `spark-submit` l’aide de ou d’Apache livy.

### <a name="use-spark-submit"></a>Utiliser Spark-Submit

Vous pouvez utiliser la commande [Spark-Submit](https://spark.apache.org/docs/latest/submitting-applications.html) pour soumettre des travaux .net pour Apache Spark à Azure HDInsight.
 
1. `ssh`dans l’un des nœuds principaux de votre cluster.

1. Exécutez `spark-submit`:

   ```bash
   spark-submit \
   --master yarn \
   --class org.apache.spark.deploy.DotnetRunner \
   --files <comma-separated list of assemblies that contain UDF definitions, if any> \
   abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar \
   abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/<your app>.zip <your app> <app arg 1> <app arg 2> ... <app arg n>
   ```

### <a name="use-apache-livy"></a>Utiliser Apache livy

Vous pouvez utiliser [Apache livy](https://livy.incubator.apache.org/), l’API REST Apache Spark, pour soumettre des travaux .net pour Apache Spark à un cluster Azure HDInsight Spark. Pour plus d’informations, consultez [tâches à distance avec Apache livy](https://docs.microsoft.com/azure/hdinsight/spark/apache-spark-livy-rest-interface).

Vous pouvez exécuter la commande suivante sur Linux à `curl`l’aide de:

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

## <a name="next-steps"></a>Étapes suivantes

Dans ce didacticiel, vous avez déployé votre application .NET pour Apache Spark sur Azure HDInsight. Pour en savoir plus sur HDInsight, consultez la documentation Azure HDInsight.

> [!div class="nextstepaction"]
> [Documentation Azure HDInsight](https://docs.microsoft.com/azure/hdinsight/)
