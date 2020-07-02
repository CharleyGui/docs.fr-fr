---
title: Déployer une application .NET pour Apache Spark sur Amazon EMR Spark
description: Découvrez comment déployer une application .NET pour Apache Spark sur Amazon EMR Spark.
ms.date: 06/25/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: c6cf26044693c5d923d11e1bbc72232e7009fe73
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85618257"
---
# <a name="deploy-a-net-for-apache-spark-application-to-amazon-emr-spark"></a>Déployer une application .NET pour Apache Spark sur Amazon EMR Spark

Ce tutoriel explique comment déployer une application .NET pour Apache Spark sur Amazon EMR Spark.

Dans ce tutoriel, vous allez apprendre à :

> [!div class="checklist"]
>
> * Préparer Microsoft.Spark.Worker
> * Publier votre application .NET Spark
> * Déployer votre application sur Amazon EMR Spark
> * Exécutez l'application.

[!INCLUDE [spark-preview-note](../../../includes/spark-preview-note.md)]

## <a name="prerequisites"></a>Prérequis

Avant de commencer, procédez comme suit :

* Téléchargez l’[interface CLI AWS](https://aws.amazon.com/cli/).
* Téléchargez [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) sur votre machine locale. Il s’agit d’un script d’assistance que vous utilisez ultérieurement pour copier les fichiers dépendants de .NET pour Apache Spark dans les nœuds Worker de votre cluster Spark.

## <a name="prepare-worker-dependencies"></a>Préparer les dépendances Worker

**Microsoft. Spark. Worker** est un composant principal qui réside sur les nœuds Worker individuels de votre cluster Spark. Quand vous voulez exécuter une fonction C# définie par l’utilisateur, Spark doit comprendre comment lancer le CLR .NET pour exécuter la fonction définie par l’utilisateur. **Microsoft.Spark.Worker** fournit à Spark une collection de classes qui activent cette fonctionnalité.

1. Sélectionnez une version netcoreapp Linux de [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases) à déployer sur votre cluster.

   Par exemple, si vous voulez `.NET for Apache Spark v0.1.0` avec `netcoreapp2.1`, vous devez télécharger [Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz](https://github.com/dotnet/spark/releases/download/v0.1.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz).

2. Chargez `Microsoft.Spark.Worker.<release>.tar.gz` et [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) dans un système de fichiers distribués (par exemple S3) auquel votre cluster a accès.

## <a name="prepare-your-net-for-apache-spark-app"></a>Préparer votre application .NET pour Apache Spark

1. Suivez le tutoriel [Prise en main](get-started.md) pour générer votre application.

2. Publiez votre application .NET Spark en tant qu’application autonome.

   Exécutez la commande suivante sur Linux.

   ```dotnetcli
   dotnet publish -c Release -f netcoreapp2.1 -r ubuntu.16.04-x64
   ```

3. Produisez `<your app>.zip` pour les fichiers publiés.

   Exécutez la commande suivante sur Linux en utilisant `zip`.

   ```bash
   zip -r <your app>.zip .
   ```

4. Chargez les éléments suivants sur un système de fichiers distribués (par exemple S3) auquel votre cluster a accès :

   * `microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar`: Ce fichier jar est inclus dans le package NuGet [Microsoft. Spark](https://www.nuget.org/packages/Microsoft.Spark/) et colocalisé dans le répertoire de sortie de la génération de votre application.
   * `<your app>.zip`
   * Les fichiers (comme les fichiers de dépendances ou les données communes accessibles à chaque worker) ou les assemblys (comme les DLL qui contiennent vos fonctions définies par l’utilisateur ou les bibliothèques dont dépend votre application) doivent être placés dans le répertoire de travail de chaque exécuteur.

## <a name="deploy-to-amazon-emr-spark"></a>Déployer sur Amazon EMR Spark

[Amazon EMR](https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-what-is-emr.html) est une plateforme de cluster gérée qui simplifie l’exécution de frameworks Big Data sur AWS.

> [!NOTE]
> Amazon EMR Spark est basé sur Linux. Par conséquent, si vous voulez déployer votre application sur Amazon EMR Spark, vérifiez que votre application est compatible avec .NET Standard et que vous utilisez le [compilateur .NET Core](https://dotnet.microsoft.com/download) pour compiler votre application.

### <a name="deploy-microsoftsparkworker"></a>Déployer Microsoft.Spark.Worker

Cette étape est nécessaire seulement lors de la création du cluster.

Exécutez `install-worker.sh` lors de la création du cluster en utilisant des [actions de démarrage](https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-plan-bootstrap.html).

Exécutez la commande suivante sur Linux en utilisant AWS CLI.

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

## <a name="run-your-app"></a>Exécutez l'application.

Il existe deux façons d’exécuter votre application dans Amazon EMR Spark : spark-submit et Amazon EMR Steps.

### <a name="use-spark-submit"></a>Utiliser spark-submit

Vous pouvez utiliser la commande [spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html) pour soumettre des travaux .NET pour Apache Spark à Amazon EMR Spark.

1. `ssh` dans un des nœuds du cluster.

2. Exécutez `spark-submit`.

   ```bash
   spark-submit \
   --master yarn \
   --class org.apache.spark.deploy.dotnet.DotnetRunner \
   --files <comma-separated list of assemblies that contain UDF definitions, if any> \
   s3://mybucket/<some dir>/microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar \
   s3://mybucket/<some dir>/<your app>.zip <your app> <app args>
   ```

### <a name="use-amazon-emr-steps"></a>Utiliser Amazon EMR Steps

Vous pouvez utiliser [Amazon EMR Steps](https://docs.aws.amazon.com/emr/latest/ReleaseGuide/emr-spark-submit-step.html) pour soumettre des travaux au framework Spark installé sur le cluster EMR.

Exécutez la commande suivante sur Linux en utilisant AWS CLI.

```bash
aws emr add-steps \
--cluster-id j-xxxxxxxxxxxxx \
--steps Type=spark,Name="Spark Program",Args=[--master,yarn,--files,s3://mybucket/<some dir>/<udf assembly>,--class,org.apache.spark.deploy.dotnet.DotnetRunner,s3://mybucket/<some dir>/microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar,s3://mybucket/<some dir>/<your app>.zip,<your app>,<app arg 1>,<app arg 2>,...,<app arg n>],ActionOnFailure=CONTINUE
```

## <a name="next-steps"></a>Étapes suivantes

Dans ce tutoriel, vous avez déployé votre application .NET pour Apache Spark sur Amazon EMR Spark. Pour des exemples de projets .NET pour Apache Spark, accédez à GitHub.

> [!div class="nextstepaction"]
> [Exemples .NET pour Apache Spark](https://github.com/dotnet/spark/tree/master/examples)
