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
# <a name="deploy-a-net-for-apache-spark-application-to-amazon-emr-spark"></a><span data-ttu-id="50f21-103">Déployer une application .NET pour Apache Spark sur Amazon le Spark</span><span class="sxs-lookup"><span data-stu-id="50f21-103">Deploy a .NET for Apache Spark application to Amazon EMR Spark</span></span>

<span data-ttu-id="50f21-104">Ce didacticiel explique comment déployer une application .NET pour Apache Spark sur Amazon le Spark.</span><span class="sxs-lookup"><span data-stu-id="50f21-104">This tutorial teaches how to deploy a .NET for Apache Spark application to Amazon EMR Spark.</span></span>

<span data-ttu-id="50f21-105">Ce tutoriel vous montre comment effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="50f21-105">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="50f21-106">Préparer Microsoft. Spark. Worker</span><span class="sxs-lookup"><span data-stu-id="50f21-106">Prepare Microsoft.Spark.Worker</span></span>
> * <span data-ttu-id="50f21-107">Publier votre application Spark .NET</span><span class="sxs-lookup"><span data-stu-id="50f21-107">Publish your Spark .NET app</span></span>
> * <span data-ttu-id="50f21-108">Déployer votre application sur Amazon le Spark</span><span class="sxs-lookup"><span data-stu-id="50f21-108">Deploy your app to Amazon EMR Spark</span></span>
> * <span data-ttu-id="50f21-109">Exécuter votre application</span><span class="sxs-lookup"><span data-stu-id="50f21-109">Run your app</span></span>

## <a name="prerequisites"></a><span data-ttu-id="50f21-110">Prérequis</span><span class="sxs-lookup"><span data-stu-id="50f21-110">Prerequisites</span></span>

<span data-ttu-id="50f21-111">Avant de commencer, procédez comme suit:</span><span class="sxs-lookup"><span data-stu-id="50f21-111">Before you start, do the following:</span></span>

* <span data-ttu-id="50f21-112">Téléchargez l' [interface CLI AWS](https://aws.amazon.com/cli/).</span><span class="sxs-lookup"><span data-stu-id="50f21-112">Download the [AWS CLI](https://aws.amazon.com/cli/).</span></span>
* <span data-ttu-id="50f21-113">Téléchargez [install-Worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) sur votre ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="50f21-113">Download [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) to your local machine.</span></span> <span data-ttu-id="50f21-114">Il s’agit d’un script d’assistance que vous utilisez ultérieurement pour copier .NET pour Apache Spark fichiers dépendants dans les nœuds Worker du cluster Spark.</span><span class="sxs-lookup"><span data-stu-id="50f21-114">This is a helper script that you use later to copy .NET for Apache Spark dependent files into your Spark cluster's worker nodes.</span></span>

## <a name="prepare-worker-dependencies"></a><span data-ttu-id="50f21-115">Préparer les dépendances de Worker</span><span class="sxs-lookup"><span data-stu-id="50f21-115">Prepare worker dependencies</span></span>

<span data-ttu-id="50f21-116">**Microsoft. Spark. Worker** est un composant principal qui réside sur les nœuds Worker individuels de votre cluster Spark.</span><span class="sxs-lookup"><span data-stu-id="50f21-116">**Microsoft.Spark.Worker** is a backend component that lives on the individual worker nodes of your Spark cluster.</span></span> <span data-ttu-id="50f21-117">Lorsque vous souhaitez exécuter une C# fonction définie par l’utilisateur (UDF), Spark doit comprendre comment lancer le CLR .net pour exécuter l’UDF.</span><span class="sxs-lookup"><span data-stu-id="50f21-117">When you want to execute a C# UDF (user-defined function), Spark needs to understand how to launch the .NET CLR to execute the UDF.</span></span> <span data-ttu-id="50f21-118">**Microsoft. Spark. Worker** fournit une collection de classes à Spark qui activent cette fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="50f21-118">**Microsoft.Spark.Worker** provides a collection of classes to Spark that enable this functionality.</span></span>

1. <span data-ttu-id="50f21-119">Sélectionnez une version de netcoreapp de [Microsoft. Spark. Worker](https://github.com/dotnet/spark/releases) Linux à déployer sur votre cluster.</span><span class="sxs-lookup"><span data-stu-id="50f21-119">Select a [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases) Linux netcoreapp release to be deployed on your cluster.</span></span>

   <span data-ttu-id="50f21-120">Par exemple, si vous souhaitez `.NET for Apache Spark v0.1.0` utiliser `netcoreapp2.1`, vous devez télécharger [Microsoft. Spark. Worker. netcoreapp 2.1. Linux-x64-0.1.0. tar. gz](https://github.com/dotnet/spark/releases/download/v0.1.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz).</span><span class="sxs-lookup"><span data-stu-id="50f21-120">For example, if you want `.NET for Apache Spark v0.1.0` using `netcoreapp2.1`, you'd download [Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz](https://github.com/dotnet/spark/releases/download/v0.1.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz).</span></span>

2. <span data-ttu-id="50f21-121">Téléchargez `Microsoft.Spark.Worker.<release>.tar.gz` et [install-Worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) dans un système de fichiers distribués (par exemple, S3) auquel votre cluster a accès.</span><span class="sxs-lookup"><span data-stu-id="50f21-121">Upload `Microsoft.Spark.Worker.<release>.tar.gz` and [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) to a distributed file system (e.g., S3) that your cluster has access to.</span></span>

## <a name="prepare-your-net-for-apache-spark-app"></a><span data-ttu-id="50f21-122">Préparer votre application .NET pour Apache Spark</span><span class="sxs-lookup"><span data-stu-id="50f21-122">Prepare your .NET for Apache Spark app</span></span>

1. <span data-ttu-id="50f21-123">Suivez le didacticiel de [prise en main](get-started.md) pour créer votre application.</span><span class="sxs-lookup"><span data-stu-id="50f21-123">Follow the [Get Started](get-started.md) tutorial to build your app.</span></span>

2. <span data-ttu-id="50f21-124">Publiez votre application Spark .NET comme autonome.</span><span class="sxs-lookup"><span data-stu-id="50f21-124">Publish your Spark .NET app as self-contained.</span></span>

   <span data-ttu-id="50f21-125">Exécutez la commande suivante sur Linux.</span><span class="sxs-lookup"><span data-stu-id="50f21-125">Run the following command on Linux.</span></span>

   ```bash
   dotnet publish -c Release -f netcoreapp2.1 -r ubuntu.16.04-x64
   ```

3. <span data-ttu-id="50f21-126">Produit `<your app>.zip` pour les fichiers publiés.</span><span class="sxs-lookup"><span data-stu-id="50f21-126">Produce `<your app>.zip` for the published files.</span></span>

   <span data-ttu-id="50f21-127">Exécutez la commande suivante sur Linux à `zip`l’aide de.</span><span class="sxs-lookup"><span data-stu-id="50f21-127">Run the following command on Linux using `zip`.</span></span>

   ```bash
   zip -r <your app>.zip .
   ```

4. <span data-ttu-id="50f21-128">Chargez les éléments suivants dans un système de fichiers distribués (par exemple, S3) auquel votre cluster a accès:</span><span class="sxs-lookup"><span data-stu-id="50f21-128">Upload the following items to a distributed file system (e.g., S3) that your cluster has access to:</span></span>

   * <span data-ttu-id="50f21-129">`microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar`: Ce fichier jar est inclus dans le package NuGet [Microsoft. Spark](https://www.nuget.org/packages/Microsoft.Spark/) et colocalisé dans le répertoire de sortie de la génération de votre application.</span><span class="sxs-lookup"><span data-stu-id="50f21-129">`microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar`: This jar is included as part of the [Microsoft.Spark](https://www.nuget.org/packages/Microsoft.Spark/) NuGet package and is colocated in your app's build output directory.</span></span>
   * `<your app>.zip`
   * <span data-ttu-id="50f21-130">Les fichiers (comme les fichiers de dépendance ou les données communes accessibles à chaque Worker) ou les assemblys (comme les dll qui contiennent vos fonctions définies par l’utilisateur ou les bibliothèques dont dépend votre application) doivent être placés dans le répertoire de travail de chaque exécuteur.</span><span class="sxs-lookup"><span data-stu-id="50f21-130">Files (like dependency files or common data accessible to every worker) or assemblies (like DLLs that contain your user-defined functions or libraries that your app depends on) to be placed in the working directory of each executor.</span></span>

## <a name="deploy-to-amazon-emr-spark"></a><span data-ttu-id="50f21-131">Déployer sur Amazon le Spark</span><span class="sxs-lookup"><span data-stu-id="50f21-131">Deploy to Amazon EMR Spark</span></span>

<span data-ttu-id="50f21-132">[Amazon le](https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-what-is-emr.html) est une plate-forme de cluster gérée qui simplifie l’exécution de Big Data infrastructures sur AWS.</span><span class="sxs-lookup"><span data-stu-id="50f21-132">[Amazon EMR](https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-what-is-emr.html) is a managed cluster platform that simplifies running big data frameworks on AWS.</span></span>

> [!NOTE] 
> <span data-ttu-id="50f21-133">Amazon le Spark est basé sur Linux.</span><span class="sxs-lookup"><span data-stu-id="50f21-133">Amazon EMR Spark is Linux-based.</span></span> <span data-ttu-id="50f21-134">Par conséquent, si vous souhaitez déployer votre application sur Amazon le Spark, assurez-vous que votre application est .NET Standard compatible et que vous utilisez le [compilateur .net Core](https://dotnet.microsoft.com/download) pour compiler votre application.</span><span class="sxs-lookup"><span data-stu-id="50f21-134">Therefore, if you are interested in deploying your app to Amazon EMR Spark, make sure your app is .NET Standard compatible and that you use the [.NET Core compiler](https://dotnet.microsoft.com/download) to compile your app.</span></span>

### <a name="deploy-microsoftsparkworker"></a><span data-ttu-id="50f21-135">Déployer Microsoft. Spark. Worker</span><span class="sxs-lookup"><span data-stu-id="50f21-135">Deploy Microsoft.Spark.Worker</span></span>

<span data-ttu-id="50f21-136">Cette étape est requise uniquement lors de la création du cluster.</span><span class="sxs-lookup"><span data-stu-id="50f21-136">This step is only required at cluster creation.</span></span>

<span data-ttu-id="50f21-137">Exécution `install-worker.sh` lors de la création du cluster à l’aide des [actions de démarrage](https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-plan-bootstrap.html).</span><span class="sxs-lookup"><span data-stu-id="50f21-137">Run `install-worker.sh` during cluster creation using [Bootstrap Actions](https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-plan-bootstrap.html).</span></span>

<span data-ttu-id="50f21-138">Exécutez la commande suivante sur Linux à l’aide de l’interface CLI AWS.</span><span class="sxs-lookup"><span data-stu-id="50f21-138">Run the following command on Linux using AWS CLI.</span></span>

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

## <a name="run-your-app"></a><span data-ttu-id="50f21-139">Exécuter votre application</span><span class="sxs-lookup"><span data-stu-id="50f21-139">Run your app</span></span>

<span data-ttu-id="50f21-140">Il existe deux façons d’exécuter votre application dans Amazon le Spark: Spark-Submit et Amazon le.</span><span class="sxs-lookup"><span data-stu-id="50f21-140">There are two ways to run your app in Amazon EMR Spark: spark-submit and Amazon EMR Steps.</span></span>

### <a name="use-spark-submit"></a><span data-ttu-id="50f21-141">Utiliser Spark-Submit</span><span class="sxs-lookup"><span data-stu-id="50f21-141">Use spark-submit</span></span>

<span data-ttu-id="50f21-142">Vous pouvez utiliser la commande [Spark-Submit](https://spark.apache.org/docs/latest/submitting-applications.html) pour soumettre des travaux .net for Apache Spark à Amazon le Spark.</span><span class="sxs-lookup"><span data-stu-id="50f21-142">You can use the [spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html) command to submit .NET for Apache Spark jobs to Amazon EMR Spark.</span></span>

1. <span data-ttu-id="50f21-143">`ssh`dans l’un des nœuds du cluster.</span><span class="sxs-lookup"><span data-stu-id="50f21-143">`ssh` into one of the nodes in the cluster.</span></span>

2. <span data-ttu-id="50f21-144">Exécutez `spark-submit`.</span><span class="sxs-lookup"><span data-stu-id="50f21-144">Run `spark-submit`.</span></span>

   ```bash
   spark-submit \
   --master yarn \
   --class org.apache.spark.deploy.DotnetRunner \
   --files <comma-separated list of assemblies that contain UDF definitions, if any> \
   s3://mybucket/<some dir>/microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar \
   s3://mybucket/<some dir>/<your app>.zip <your app> <app args>
   ```

### <a name="use-amazon-emr-steps"></a><span data-ttu-id="50f21-145">Utiliser les étapes Amazon le</span><span class="sxs-lookup"><span data-stu-id="50f21-145">Use Amazon EMR Steps</span></span>

<span data-ttu-id="50f21-146">Vous pouvez utiliser les [étapes Amazon le](https://docs.aws.amazon.com/emr/latest/ReleaseGuide/emr-spark-submit-step.html) pour soumettre des travaux à l’infrastructure Spark installée sur le cluster le.</span><span class="sxs-lookup"><span data-stu-id="50f21-146">[Amazon EMR Steps](https://docs.aws.amazon.com/emr/latest/ReleaseGuide/emr-spark-submit-step.html) can be used to submit jobs to the Spark framework installed on the EMR cluster.</span></span>

<span data-ttu-id="50f21-147">Exécutez la commande suivante sur Linux à l’aide de l’interface CLI AWS.</span><span class="sxs-lookup"><span data-stu-id="50f21-147">Run the following command on Linux using AWS CLI.</span></span>

```bash
aws emr add-steps \
--cluster-id j-xxxxxxxxxxxxx \
--steps Type=spark,Name="Spark Program",Args=[--master,yarn,--files,s3://mybucket/<some dir>/<udf assembly>,--class,org.apache.spark.deploy.DotnetRunner,s3://mybucket/<some dir>/microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar,s3://mybucket/<some dir>/<your app>.zip,<your app>,<app arg 1>,<app arg 2>,...,<app arg n>],ActionOnFailure=CONTINUE
```

## <a name="next-steps"></a><span data-ttu-id="50f21-148">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="50f21-148">Next steps</span></span>

<span data-ttu-id="50f21-149">Dans ce didacticiel, vous avez déployé votre application .NET pour Apache Spark sur Amazon le Spark.</span><span class="sxs-lookup"><span data-stu-id="50f21-149">In this tutorial, you deployed your .NET for Apache Spark application to Amazon EMR Spark.</span></span> <span data-ttu-id="50f21-150">Pour .NET, pour les exemples de projets Apache Spark, passez à GitHub.</span><span class="sxs-lookup"><span data-stu-id="50f21-150">For .NET for Apache Spark example projects, continue to GitHub.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="50f21-151">Exemples .NET pour Apache Spark</span><span class="sxs-lookup"><span data-stu-id="50f21-151">.NET for Apache Spark samples</span></span>](https://github.com/dotnet/spark/tree/master/examples)
