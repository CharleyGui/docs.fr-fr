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
# <a name="deploy-a-net-for-apache-spark-application-to-azure-hdinsight"></a>Déployer une application .NET pour Apache Spark sur Azure HDInsight

Ce tutoriel explique comment déployer une application .NET pour Apache Spark sur Azure HDInsight.

Dans ce didacticiel, vous apprendrez à :

> [!div class="checklist"]
> * Préparer Microsoft.Spark.Worker
> * Publier votre application .NET Spark
> * Déployer votre application sur Azure HDInsight
> * Exécuter votre application

## <a name="prerequisites"></a>Prérequis

Avant de commencer, procédez comme suit :

* Téléchargez l’[Explorateur Stockage Azure](https://azure.microsoft.com/features/storage-explorer/).
* Téléchargez [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) sur votre machine locale. Il s’agit d’un script d’assistance que vous utilisez ultérieurement pour copier les fichiers dépendants de .NET pour Apache Spark dans les nœuds Worker de votre cluster Spark.

## <a name="prepare-worker-dependencies"></a>Préparer les dépendances Worker

**Microsoft.Spark.Worker** est un composant back-end qui se trouve sur les nœuds Worker individuels de votre cluster Spark. Quand vous voulez exécuter une fonction C# définie par l’utilisateur, Spark doit comprendre comment lancer le CLR .NET pour exécuter la fonction définie par l’utilisateur. **Microsoft.Spark.Worker** fournit à Spark une collection de classes qui activent cette fonctionnalité.

1. Sélectionnez une version netcoreapp Linux de [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases) à déployer sur votre cluster.

   Par exemple, si vous voulez `.NET for Apache Spark v0.1.0` avec `netcoreapp2.1`, vous devez télécharger [Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz](https://github.com/dotnet/spark/releases/download/v0.1.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz).

2. Chargez `Microsoft.Spark.Worker.<release>.tar.gz` et [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) dans un système de fichiers distribués (par exemple HDFS, WASB, ADLS) auquel votre cluster a accès.

## <a name="prepare-your-net-for-apache-spark-app"></a>Préparer votre application .NET pour Apache Spark

1. Suivez le tutoriel [Prise en main](get-started.md) pour générer votre application.

2. Publiez votre application .NET Spark en tant qu’application autonome.

   Vous pouvez exécuter la commande suivante sur Linux.

   ```bash
   dotnet publish -c Release -f netcoreapp2.1 -r ubuntu.16.04-x64
   ```

3. Produisez `<your app>.zip` pour les fichiers publiés.

   Vous pouvez exécuter la commande suivante sur Linux en utilisant `zip`.

   ```bash
   zip -r <your app>.zip .
   ```

4. Chargez les éléments suivants sur un système de fichiers distribués (par exemple HDFS, WASB, ADLS) auquel votre cluster a accès :

   * `microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar`: Ce fichier jar est inclus dans le package NuGet [Microsoft.Spark](https://www.nuget.org/packages/Microsoft.Spark/) et est colocalisé dans le répertoire de sortie de la génération de votre application.
   * `<your app>.zip`
   * Les fichiers (comme les fichiers de dépendances ou les données communes accessibles à chaque Worker) ou les assemblys (comme les DLL qui contiennent vos fonctions définies par l’utilisateur ou les bibliothèques dont dépend votre `app`) doivent être placés dans le répertoire de travail de chaque exécuteur.

## <a name="deploy-to-azure-hdinsight-spark"></a>Déployer sur Azure HDInsight Spark

[Azure HDInsight Spark](https://docs.microsoft.com/azure/hdinsight/spark/apache-spark-overview) est l’implémentation Microsoft d’Apache Spark dans le cloud, qui permet aux utilisateurs de lancer et de configurer des clusters Spark dans Azure. Vous pouvez donc utiliser des clusters HDInsight Spark pour traiter vos données stockées dans [Stockage Azure](https://azure.microsoft.com/services/storage/) ou [Azure Data Lake Storage](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-use-data-lake-storage-gen2).

> [!NOTE]
> Azure HDInsight Spark est basé sur Linux. Si vous voulez déployer votre application sur Azure HDInsight Spark, vérifiez que votre application est compatible avec .NET Standard et que vous utilisez le [compilateur .NET Core](https://dotnet.microsoft.com/download) pour compiler votre application.

### <a name="deploy-microsoftsparkworker"></a>Déployer Microsoft.Spark.Worker

Cette étape n’est nécessaire qu’une seule fois pour votre cluster.

Exécutez `install-worker.sh` sur le cluster en utilisant des [actions de script HDInsight](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux).

|Paramètre|Value|
|-------|-----|
|Type de script|Personnalisé|
|Name|Installer Microsoft.Spark.Worker|
|URI de script bash|URI vers lequel vous avez chargé `install-worker.sh`. Par exemple, `abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/install-worker.sh`.|
|Type(s) de nœud|Worker|
|Paramètres|Paramètres de `install-worker.sh`. Par exemple, si vous avez chargé `install-worker.sh` dans Azure Data Lake Gen 2, il s’agit de `azure abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/Microsoft.Spark.Worker.<release>.tar.gz /usr/local/bin`.|

![Image d’action de script](./media/hdinsight-deployment/deployment-hdi-action-script.png)

## <a name="run-your-app"></a>Exécuter votre application

Vous pouvez soumettre votre travail à Azure HDInsight en utilisant `spark-submit` ou Apache Livy.

### <a name="use-spark-submit"></a>Utiliser spark-submit

Vous pouvez utiliser la commande [spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html) pour soumettre des travaux .NET pour Apache Spark à Azure HDInsight.
 
1. `ssh` dans un des nœuds principaux de votre cluster.

1. Exécutez `spark-submit` :

   ```bash
   spark-submit \
   --master yarn \
   --class org.apache.spark.deploy.DotnetRunner \
   --files <comma-separated list of assemblies that contain UDF definitions, if any> \
   abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar \
   abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/<your app>.zip <your app> <app arg 1> <app arg 2> ... <app arg n>
   ```

### <a name="use-apache-livy"></a>Utiliser Apache Livy

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
    "className":"org.apache.spark.deploy.DotnetRunner",
    "files":["abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/<udf assembly>", "abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/<file>"],
    "args":["abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/<your app>.zip","<your app>","<app arg 1>","<app arg 2>,"...","<app arg n>"]
}
EOF
```

## <a name="next-steps"></a>Étapes suivantes

Dans ce tutoriel, vous avez déployé votre application .NET pour Apache Spark sur Azure HDInsight. Pour plus d’informations sur HDInsight, consultez la documentation d’Azure HDInsight.

> [!div class="nextstepaction"]
> [Documentation Azure HDInsight](https://docs.microsoft.com/azure/hdinsight/)
