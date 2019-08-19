---
title: Déployer une application .NET pour Apache Spark sur Amazon le Spark
description: Découvrez comment déployer une application .NET pour Apache Spark sur Amazon le Spark.
ms.date: 05/17/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 5414bc20de3bb90a5d2144bd006d1b859e184a39
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2019
ms.locfileid: "69576926"
---
# <a name="deploy-a-net-for-apache-spark-application-to-amazon-emr-spark"></a>Déployer une application .NET pour Apache Spark sur Amazon le Spark

Ce didacticiel explique comment déployer une application .NET pour Apache Spark sur Amazon le Spark.

Ce tutoriel vous montre comment effectuer les opérations suivantes :

> [!div class="checklist"]
> * Préparer Microsoft. Spark. Worker
> * Publier votre application Spark .NET
> * Déployer votre application sur Amazon le Spark
> * Exécuter votre application

## <a name="prerequisites"></a>Prérequis

Avant de commencer, procédez comme suit:

* Téléchargez l' [interface CLI AWS](https://aws.amazon.com/cli/).
* Téléchargez [install-Worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) sur votre ordinateur local. Il s’agit d’un script d’assistance que vous utilisez ultérieurement pour copier .NET pour Apache Spark fichiers dépendants dans les nœuds Worker du cluster Spark.

## <a name="prepare-worker-dependencies"></a>Préparer les dépendances de Worker

**Microsoft. Spark. Worker** est un composant principal qui réside sur les nœuds Worker individuels de votre cluster Spark. Lorsque vous souhaitez exécuter une C# fonction définie par l’utilisateur (UDF), Spark doit comprendre comment lancer le CLR .net pour exécuter l’UDF. **Microsoft. Spark. Worker** fournit une collection de classes à Spark qui activent cette fonctionnalité.

1. Sélectionnez une version de netcoreapp de [Microsoft. Spark. Worker](https://github.com/dotnet/spark/releases) Linux à déployer sur votre cluster.

   Par exemple, si vous souhaitez `.NET for Apache Spark v0.1.0` utiliser `netcoreapp2.1`, vous devez télécharger [Microsoft. Spark. Worker. netcoreapp 2.1. Linux-x64-0.1.0. tar. gz](https://github.com/dotnet/spark/releases/download/v0.1.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz).

2. Téléchargez `Microsoft.Spark.Worker.<release>.tar.gz` et [install-Worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) dans un système de fichiers distribués (par exemple, S3) auquel votre cluster a accès.

## <a name="prepare-your-net-for-apache-spark-app"></a>Préparer votre application .NET pour Apache Spark

1. Suivez le didacticiel de [prise en main](get-started.md) pour créer votre application.

2. Publiez votre application Spark .NET comme autonome.

   Exécutez la commande suivante sur Linux.

   ```bash
   dotnet publish -c Release -f netcoreapp2.1 -r ubuntu.16.04-x64
   ```

3. Produit `<your app>.zip` pour les fichiers publiés.

   Exécutez la commande suivante sur Linux à `zip`l’aide de.

   ```bash
   zip -r <your app>.zip .
   ```

4. Chargez les éléments suivants dans un système de fichiers distribués (par exemple, S3) auquel votre cluster a accès:

   * `microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar`: Ce fichier jar est inclus dans le package NuGet [Microsoft. Spark](https://www.nuget.org/packages/Microsoft.Spark/) et colocalisé dans le répertoire de sortie de la génération de votre application.
   * `<your app>.zip`
   * Les fichiers (comme les fichiers de dépendance ou les données communes accessibles à chaque Worker) ou les assemblys (comme les dll qui contiennent vos fonctions définies par l’utilisateur ou les bibliothèques dont dépend votre application) doivent être placés dans le répertoire de travail de chaque exécuteur.

## <a name="deploy-to-amazon-emr-spark"></a>Déployer sur Amazon le Spark

[Amazon le](https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-what-is-emr.html) est une plate-forme de cluster gérée qui simplifie l’exécution de Big Data infrastructures sur AWS.

> [!NOTE] 
> Amazon le Spark est basé sur Linux. Par conséquent, si vous souhaitez déployer votre application sur Amazon le Spark, assurez-vous que votre application est .NET Standard compatible et que vous utilisez le [compilateur .net Core](https://dotnet.microsoft.com/download) pour compiler votre application.

### <a name="deploy-microsoftsparkworker"></a>Déployer Microsoft. Spark. Worker

Cette étape est requise uniquement lors de la création du cluster.

Exécution `install-worker.sh` lors de la création du cluster à l’aide des [actions de démarrage](https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-plan-bootstrap.html).

Exécutez la commande suivante sur Linux à l’aide de l’interface CLI AWS.

```bash
aws emr create-cluster \
--name "Test cluster" \
--release-label emr-5.23.0 \
--use-default-roles \
--ec2-attributes KeyName=myKey \
--applications Name=Spark \
--instance-count 3 \
--instance-type m1.medium \
--bootstrap-actions Path=s3://mybucket/<some dir>/install-worker.sh,Name="Install Microsoft.Spark.Worker",Args=["aws","s3://mybucket/<some dir>/Microsoft.Spark.Worker.<release>.tar.gz","/usr/local/bin"]
```

## <a name="run-your-app"></a>Exécuter votre application

Il existe deux façons d’exécuter votre application dans Amazon le Spark: Spark-Submit et Amazon le.

### <a name="use-spark-submit"></a>Utiliser Spark-Submit

Vous pouvez utiliser la commande [Spark-Submit](https://spark.apache.org/docs/latest/submitting-applications.html) pour soumettre des travaux .net for Apache Spark à Amazon le Spark.

1. `ssh`dans l’un des nœuds du cluster.

2. Exécutez `spark-submit`.

   ```bash
   spark-submit \
   --master yarn \
   --class org.apache.spark.deploy.DotnetRunner \
   --files <comma-separated list of assemblies that contain UDF definitions, if any> \
   s3://mybucket/<some dir>/microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar \
   s3://mybucket/<some dir>/<your app>.zip <your app> <app args>
   ```

### <a name="use-amazon-emr-steps"></a>Utiliser les étapes Amazon le

Vous pouvez utiliser les [étapes Amazon le](https://docs.aws.amazon.com/emr/latest/ReleaseGuide/emr-spark-submit-step.html) pour soumettre des travaux à l’infrastructure Spark installée sur le cluster le.

Exécutez la commande suivante sur Linux à l’aide de l’interface CLI AWS.

```bash
aws emr add-steps \
--cluster-id j-xxxxxxxxxxxxx \
--steps Type=spark,Name="Spark Program",Args=[--master,yarn,--files,s3://mybucket/<some dir>/<udf assembly>,--class,org.apache.spark.deploy.DotnetRunner,s3://mybucket/<some dir>/microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar,s3://mybucket/<some dir>/<your app>.zip,<your app>,<app arg 1>,<app arg 2>,...,<app arg n>],ActionOnFailure=CONTINUE
```

## <a name="next-steps"></a>Étapes suivantes

Dans ce didacticiel, vous avez déployé votre application .NET pour Apache Spark sur Amazon le Spark. Pour .NET, pour les exemples de projets Apache Spark, passez à GitHub.

> [!div class="nextstepaction"]
> [Exemples .NET pour Apache Spark](https://github.com/dotnet/spark/tree/master/examples)
