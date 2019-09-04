---
title: Déployer une application .NET pour Apache Spark sur Amazon EMR Spark
description: Découvrez comment déployer une application .NET pour Apache Spark sur Amazon EMR Spark.
ms.date: 05/17/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: bf52a53e8f282f55a0071deb266dabb798fa3348
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70254052"
---
# <a name="deploy-a-net-for-apache-spark-application-to-amazon-emr-spark"></a><span data-ttu-id="f1ca0-103">Déployer une application .NET pour Apache Spark sur Amazon EMR Spark</span><span class="sxs-lookup"><span data-stu-id="f1ca0-103">Deploy a .NET for Apache Spark application to Amazon EMR Spark</span></span>

<span data-ttu-id="f1ca0-104">Ce tutoriel explique comment déployer une application .NET pour Apache Spark sur Amazon EMR Spark.</span><span class="sxs-lookup"><span data-stu-id="f1ca0-104">This tutorial teaches how to deploy a .NET for Apache Spark application to Amazon EMR Spark.</span></span>

<span data-ttu-id="f1ca0-105">Ce tutoriel vous montre comment effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="f1ca0-105">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="f1ca0-106">Préparer Microsoft.Spark.Worker</span><span class="sxs-lookup"><span data-stu-id="f1ca0-106">Prepare Microsoft.Spark.Worker</span></span>
> * <span data-ttu-id="f1ca0-107">Publier votre application .NET Spark</span><span class="sxs-lookup"><span data-stu-id="f1ca0-107">Publish your Spark .NET app</span></span>
> * <span data-ttu-id="f1ca0-108">Déployer votre application sur Amazon EMR Spark</span><span class="sxs-lookup"><span data-stu-id="f1ca0-108">Deploy your app to Amazon EMR Spark</span></span>
> * <span data-ttu-id="f1ca0-109">Exécuter votre application</span><span class="sxs-lookup"><span data-stu-id="f1ca0-109">Run your app</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f1ca0-110">Prérequis</span><span class="sxs-lookup"><span data-stu-id="f1ca0-110">Prerequisites</span></span>

<span data-ttu-id="f1ca0-111">Avant de commencer, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="f1ca0-111">Before you start, do the following:</span></span>

* <span data-ttu-id="f1ca0-112">Téléchargez l’[interface CLI AWS](https://aws.amazon.com/cli/).</span><span class="sxs-lookup"><span data-stu-id="f1ca0-112">Download the [AWS CLI](https://aws.amazon.com/cli/).</span></span>
* <span data-ttu-id="f1ca0-113">Téléchargez [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) sur votre machine locale.</span><span class="sxs-lookup"><span data-stu-id="f1ca0-113">Download [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) to your local machine.</span></span> <span data-ttu-id="f1ca0-114">Il s’agit d’un script d’assistance que vous utilisez ultérieurement pour copier les fichiers dépendants de .NET pour Apache Spark dans les nœuds Worker de votre cluster Spark.</span><span class="sxs-lookup"><span data-stu-id="f1ca0-114">This is a helper script that you use later to copy .NET for Apache Spark dependent files into your Spark cluster's worker nodes.</span></span>

## <a name="prepare-worker-dependencies"></a><span data-ttu-id="f1ca0-115">Préparer les dépendances Worker</span><span class="sxs-lookup"><span data-stu-id="f1ca0-115">Prepare worker dependencies</span></span>

<span data-ttu-id="f1ca0-116">**Microsoft.Spark.Worker** est un composant back-end qui se trouve sur les nœuds Worker individuels de votre cluster Spark.</span><span class="sxs-lookup"><span data-stu-id="f1ca0-116">**Microsoft.Spark.Worker** is a backend component that lives on the individual worker nodes of your Spark cluster.</span></span> <span data-ttu-id="f1ca0-117">Quand vous voulez exécuter une fonction C# définie par l’utilisateur, Spark doit comprendre comment lancer le CLR .NET pour exécuter la fonction définie par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="f1ca0-117">When you want to execute a C# UDF (user-defined function), Spark needs to understand how to launch the .NET CLR to execute the UDF.</span></span> <span data-ttu-id="f1ca0-118">**Microsoft.Spark.Worker** fournit à Spark une collection de classes qui activent cette fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="f1ca0-118">**Microsoft.Spark.Worker** provides a collection of classes to Spark that enable this functionality.</span></span>

1. <span data-ttu-id="f1ca0-119">Sélectionnez une version netcoreapp Linux de [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases) à déployer sur votre cluster.</span><span class="sxs-lookup"><span data-stu-id="f1ca0-119">Select a [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases) Linux netcoreapp release to be deployed on your cluster.</span></span>

   <span data-ttu-id="f1ca0-120">Par exemple, si vous voulez `.NET for Apache Spark v0.1.0` avec `netcoreapp2.1`, vous devez télécharger [Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz](https://github.com/dotnet/spark/releases/download/v0.1.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz).</span><span class="sxs-lookup"><span data-stu-id="f1ca0-120">For example, if you want `.NET for Apache Spark v0.1.0` using `netcoreapp2.1`, you'd download [Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz](https://github.com/dotnet/spark/releases/download/v0.1.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz).</span></span>

2. <span data-ttu-id="f1ca0-121">Chargez `Microsoft.Spark.Worker.<release>.tar.gz` et [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) dans un système de fichiers distribués (par exemple S3) auquel votre cluster a accès.</span><span class="sxs-lookup"><span data-stu-id="f1ca0-121">Upload `Microsoft.Spark.Worker.<release>.tar.gz` and [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) to a distributed file system (e.g., S3) that your cluster has access to.</span></span>

## <a name="prepare-your-net-for-apache-spark-app"></a><span data-ttu-id="f1ca0-122">Préparer votre application .NET pour Apache Spark</span><span class="sxs-lookup"><span data-stu-id="f1ca0-122">Prepare your .NET for Apache Spark app</span></span>

1. <span data-ttu-id="f1ca0-123">Suivez le tutoriel [Prise en main](get-started.md) pour générer votre application.</span><span class="sxs-lookup"><span data-stu-id="f1ca0-123">Follow the [Get Started](get-started.md) tutorial to build your app.</span></span>

2. <span data-ttu-id="f1ca0-124">Publiez votre application .NET Spark en tant qu’application autonome.</span><span class="sxs-lookup"><span data-stu-id="f1ca0-124">Publish your Spark .NET app as self-contained.</span></span>

   <span data-ttu-id="f1ca0-125">Exécutez la commande suivante sur Linux.</span><span class="sxs-lookup"><span data-stu-id="f1ca0-125">Run the following command on Linux.</span></span>

   ```bash
   dotnet publish -c Release -f netcoreapp2.1 -r ubuntu.16.04-x64
   ```

3. <span data-ttu-id="f1ca0-126">Produisez `<your app>.zip` pour les fichiers publiés.</span><span class="sxs-lookup"><span data-stu-id="f1ca0-126">Produce `<your app>.zip` for the published files.</span></span>

   <span data-ttu-id="f1ca0-127">Exécutez la commande suivante sur Linux en utilisant `zip`.</span><span class="sxs-lookup"><span data-stu-id="f1ca0-127">Run the following command on Linux using `zip`.</span></span>

   ```bash
   zip -r <your app>.zip .
   ```

4. <span data-ttu-id="f1ca0-128">Chargez les éléments suivants sur un système de fichiers distribués (par exemple S3) auquel votre cluster a accès :</span><span class="sxs-lookup"><span data-stu-id="f1ca0-128">Upload the following items to a distributed file system (e.g., S3) that your cluster has access to:</span></span>

   * <span data-ttu-id="f1ca0-129">`microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar`: Ce fichier jar est inclus dans le package NuGet [Microsoft.Spark](https://www.nuget.org/packages/Microsoft.Spark/) et est colocalisé dans le répertoire de sortie de la génération de votre application.</span><span class="sxs-lookup"><span data-stu-id="f1ca0-129">`microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar`: This jar is included as part of the [Microsoft.Spark](https://www.nuget.org/packages/Microsoft.Spark/) NuGet package and is colocated in your app's build output directory.</span></span>
   * `<your app>.zip`
   * <span data-ttu-id="f1ca0-130">Les fichiers (comme les fichiers de dépendances ou les données communes accessibles à chaque worker) ou les assemblys (comme les DLL qui contiennent vos fonctions définies par l’utilisateur ou les bibliothèques dont dépend votre application) doivent être placés dans le répertoire de travail de chaque exécuteur.</span><span class="sxs-lookup"><span data-stu-id="f1ca0-130">Files (like dependency files or common data accessible to every worker) or assemblies (like DLLs that contain your user-defined functions or libraries that your app depends on) to be placed in the working directory of each executor.</span></span>

## <a name="deploy-to-amazon-emr-spark"></a><span data-ttu-id="f1ca0-131">Déployer sur Amazon EMR Spark</span><span class="sxs-lookup"><span data-stu-id="f1ca0-131">Deploy to Amazon EMR Spark</span></span>

<span data-ttu-id="f1ca0-132">[Amazon EMR](https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-what-is-emr.html) est une plateforme de cluster gérée qui simplifie l’exécution de frameworks Big Data sur AWS.</span><span class="sxs-lookup"><span data-stu-id="f1ca0-132">[Amazon EMR](https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-what-is-emr.html) is a managed cluster platform that simplifies running big data frameworks on AWS.</span></span>

> [!NOTE] 
> <span data-ttu-id="f1ca0-133">Amazon EMR Spark est basé sur Linux.</span><span class="sxs-lookup"><span data-stu-id="f1ca0-133">Amazon EMR Spark is Linux-based.</span></span> <span data-ttu-id="f1ca0-134">Par conséquent, si vous voulez déployer votre application sur Amazon EMR Spark, vérifiez que votre application est compatible avec .NET Standard et que vous utilisez le [compilateur .NET Core](https://dotnet.microsoft.com/download) pour compiler votre application.</span><span class="sxs-lookup"><span data-stu-id="f1ca0-134">Therefore, if you are interested in deploying your app to Amazon EMR Spark, make sure your app is .NET Standard compatible and that you use the [.NET Core compiler](https://dotnet.microsoft.com/download) to compile your app.</span></span>

### <a name="deploy-microsoftsparkworker"></a><span data-ttu-id="f1ca0-135">Déployer Microsoft.Spark.Worker</span><span class="sxs-lookup"><span data-stu-id="f1ca0-135">Deploy Microsoft.Spark.Worker</span></span>

<span data-ttu-id="f1ca0-136">Cette étape est nécessaire seulement lors de la création du cluster.</span><span class="sxs-lookup"><span data-stu-id="f1ca0-136">This step is only required at cluster creation.</span></span>

<span data-ttu-id="f1ca0-137">Exécutez `install-worker.sh` lors de la création du cluster en utilisant des [actions de démarrage](https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-plan-bootstrap.html).</span><span class="sxs-lookup"><span data-stu-id="f1ca0-137">Run `install-worker.sh` during cluster creation using [Bootstrap Actions](https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-plan-bootstrap.html).</span></span>

<span data-ttu-id="f1ca0-138">Exécutez la commande suivante sur Linux en utilisant AWS CLI.</span><span class="sxs-lookup"><span data-stu-id="f1ca0-138">Run the following command on Linux using AWS CLI.</span></span>

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

## <a name="run-your-app"></a><span data-ttu-id="f1ca0-139">Exécuter votre application</span><span class="sxs-lookup"><span data-stu-id="f1ca0-139">Run your app</span></span>

<span data-ttu-id="f1ca0-140">Il existe deux façons d’exécuter votre application dans Amazon EMR Spark : spark-submit et Amazon EMR Steps.</span><span class="sxs-lookup"><span data-stu-id="f1ca0-140">There are two ways to run your app in Amazon EMR Spark: spark-submit and Amazon EMR Steps.</span></span>

### <a name="use-spark-submit"></a><span data-ttu-id="f1ca0-141">Utiliser spark-submit</span><span class="sxs-lookup"><span data-stu-id="f1ca0-141">Use spark-submit</span></span>

<span data-ttu-id="f1ca0-142">Vous pouvez utiliser la commande [spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html) pour soumettre des travaux .NET pour Apache Spark à Amazon EMR Spark.</span><span class="sxs-lookup"><span data-stu-id="f1ca0-142">You can use the [spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html) command to submit .NET for Apache Spark jobs to Amazon EMR Spark.</span></span>

1. <span data-ttu-id="f1ca0-143">`ssh` dans un des nœuds du cluster.</span><span class="sxs-lookup"><span data-stu-id="f1ca0-143">`ssh` into one of the nodes in the cluster.</span></span>

2. <span data-ttu-id="f1ca0-144">Exécutez `spark-submit`.</span><span class="sxs-lookup"><span data-stu-id="f1ca0-144">Run `spark-submit`.</span></span>

   ```bash
   spark-submit \
   --master yarn \
   --class org.apache.spark.deploy.dotnet.DotnetRunner \
   --files <comma-separated list of assemblies that contain UDF definitions, if any> \
   s3://mybucket/<some dir>/microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar \
   s3://mybucket/<some dir>/<your app>.zip <your app> <app args>
   ```

### <a name="use-amazon-emr-steps"></a><span data-ttu-id="f1ca0-145">Utiliser Amazon EMR Steps</span><span class="sxs-lookup"><span data-stu-id="f1ca0-145">Use Amazon EMR Steps</span></span>

<span data-ttu-id="f1ca0-146">Vous pouvez utiliser [Amazon EMR Steps](https://docs.aws.amazon.com/emr/latest/ReleaseGuide/emr-spark-submit-step.html) pour soumettre des travaux au framework Spark installé sur le cluster EMR.</span><span class="sxs-lookup"><span data-stu-id="f1ca0-146">[Amazon EMR Steps](https://docs.aws.amazon.com/emr/latest/ReleaseGuide/emr-spark-submit-step.html) can be used to submit jobs to the Spark framework installed on the EMR cluster.</span></span>

<span data-ttu-id="f1ca0-147">Exécutez la commande suivante sur Linux en utilisant AWS CLI.</span><span class="sxs-lookup"><span data-stu-id="f1ca0-147">Run the following command on Linux using AWS CLI.</span></span>

```bash
aws emr add-steps \
--cluster-id j-xxxxxxxxxxxxx \
--steps Type=spark,Name="Spark Program",Args=[--master,yarn,--files,s3://mybucket/<some dir>/<udf assembly>,--class,org.apache.spark.deploy.dotnet.DotnetRunner,s3://mybucket/<some dir>/microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar,s3://mybucket/<some dir>/<your app>.zip,<your app>,<app arg 1>,<app arg 2>,...,<app arg n>],ActionOnFailure=CONTINUE
```

## <a name="next-steps"></a><span data-ttu-id="f1ca0-148">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="f1ca0-148">Next steps</span></span>

<span data-ttu-id="f1ca0-149">Dans ce tutoriel, vous avez déployé votre application .NET pour Apache Spark sur Amazon EMR Spark.</span><span class="sxs-lookup"><span data-stu-id="f1ca0-149">In this tutorial, you deployed your .NET for Apache Spark application to Amazon EMR Spark.</span></span> <span data-ttu-id="f1ca0-150">Pour des exemples de projets .NET pour Apache Spark, accédez à GitHub.</span><span class="sxs-lookup"><span data-stu-id="f1ca0-150">For .NET for Apache Spark example projects, continue to GitHub.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="f1ca0-151">Exemples .NET pour Apache Spark</span><span class="sxs-lookup"><span data-stu-id="f1ca0-151">.NET for Apache Spark samples</span></span>](https://github.com/dotnet/spark/tree/master/examples)
