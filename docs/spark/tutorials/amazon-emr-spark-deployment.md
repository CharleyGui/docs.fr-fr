---
title: Déployer une application .NET pour Apache Spark sur Amazon EMR Spark
description: Découvrez comment déployer une application .NET pour Apache Spark sur Amazon EMR Spark.
ms.date: 10/09/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: dd1cfdf12266b55d9dbc0210479b89ba68c59a38
ms.sourcegitcommit: 34968a61e9bac0f6be23ed6ffb837f52d2390c85
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94688070"
---
# <a name="deploy-a-net-for-apache-spark-application-to-amazon-emr-spark"></a><span data-ttu-id="fd606-103">Déployer une application .NET pour Apache Spark sur Amazon EMR Spark</span><span class="sxs-lookup"><span data-stu-id="fd606-103">Deploy a .NET for Apache Spark application to Amazon EMR Spark</span></span>

<span data-ttu-id="fd606-104">Ce tutoriel explique comment déployer une application .NET pour Apache Spark sur Amazon EMR Spark.</span><span class="sxs-lookup"><span data-stu-id="fd606-104">This tutorial teaches how to deploy a .NET for Apache Spark application to Amazon EMR Spark.</span></span> <span data-ttu-id="fd606-105">[Amazon EMR](https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-what-is-emr.html) est une plateforme de cluster gérée qui simplifie l’exécution de frameworks Big Data sur AWS.</span><span class="sxs-lookup"><span data-stu-id="fd606-105">[Amazon EMR](https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-what-is-emr.html) is a managed cluster platform that simplifies running big data frameworks on AWS.</span></span>

<span data-ttu-id="fd606-106">Dans ce tutoriel, vous allez apprendre à :</span><span class="sxs-lookup"><span data-stu-id="fd606-106">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="fd606-107">Préparer Microsoft.Spark.Worker</span><span class="sxs-lookup"><span data-stu-id="fd606-107">Prepare Microsoft.Spark.Worker</span></span>
> * <span data-ttu-id="fd606-108">Publier votre application .NET Spark</span><span class="sxs-lookup"><span data-stu-id="fd606-108">Publish your Spark .NET app</span></span>
> * <span data-ttu-id="fd606-109">Déployer votre application sur Amazon EMR Spark</span><span class="sxs-lookup"><span data-stu-id="fd606-109">Deploy your app to Amazon EMR Spark</span></span>
> * <span data-ttu-id="fd606-110">Exécuter l’application</span><span class="sxs-lookup"><span data-stu-id="fd606-110">Run your app</span></span>

> [!Note]
> <span data-ttu-id="fd606-111">AWS le Spark est basé sur Linux.</span><span class="sxs-lookup"><span data-stu-id="fd606-111">AWS EMR Spark is Linux-based.</span></span> <span data-ttu-id="fd606-112">Par conséquent, si vous souhaitez déployer votre application sur AWS le Spark, assurez-vous que votre application est .NET Standard compatible et que vous utilisez le compilateur .NET Core pour compiler votre application.</span><span class="sxs-lookup"><span data-stu-id="fd606-112">Therefore, if you are interested in deploying your app to AWS EMR Spark, make sure your app is .NET Standard compatible and that you use .NET Core compiler to compile your app.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="fd606-113">Prérequis</span><span class="sxs-lookup"><span data-stu-id="fd606-113">Prerequisites</span></span>

<span data-ttu-id="fd606-114">Avant de commencer, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="fd606-114">Before you start, do the following:</span></span>

* <span data-ttu-id="fd606-115">Téléchargez l’[interface CLI AWS](https://aws.amazon.com/cli/).</span><span class="sxs-lookup"><span data-stu-id="fd606-115">Download the [AWS CLI](https://aws.amazon.com/cli/).</span></span>
* <span data-ttu-id="fd606-116">Téléchargez [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) sur votre machine locale.</span><span class="sxs-lookup"><span data-stu-id="fd606-116">Download [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) to your local machine.</span></span> <span data-ttu-id="fd606-117">Il s’agit d’un script d’assistance que vous utilisez ultérieurement pour copier les fichiers dépendants de .NET pour Apache Spark dans les nœuds Worker de votre cluster Spark.</span><span class="sxs-lookup"><span data-stu-id="fd606-117">This is a helper script that you use later to copy .NET for Apache Spark dependent files into your Spark cluster's worker nodes.</span></span>

## <a name="prepare-worker-dependencies"></a><span data-ttu-id="fd606-118">Préparer les dépendances Worker</span><span class="sxs-lookup"><span data-stu-id="fd606-118">Prepare worker dependencies</span></span>

<span data-ttu-id="fd606-119">**Microsoft. Spark. Worker** est un composant principal qui réside sur les nœuds Worker individuels de votre cluster Spark.</span><span class="sxs-lookup"><span data-stu-id="fd606-119">**Microsoft.Spark.Worker** is a backend component that lives on the individual worker nodes of your Spark cluster.</span></span> <span data-ttu-id="fd606-120">Lorsque vous souhaitez exécuter une fonction définie par l’utilisateur (UDF) C#, Spark doit comprendre comment lancer le CLR .NET pour exécuter l’UDF.</span><span class="sxs-lookup"><span data-stu-id="fd606-120">When you want to execute a C# UDF (User-Defined Function), Spark needs to understand how to launch the .NET CLR to execute the UDF.</span></span> <span data-ttu-id="fd606-121">**Microsoft.Spark.Worker** fournit à Spark une collection de classes qui activent cette fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="fd606-121">**Microsoft.Spark.Worker** provides a collection of classes to Spark that enable this functionality.</span></span>

1. <span data-ttu-id="fd606-122">Sélectionnez une version netcoreapp Linux de [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases) à déployer sur votre cluster.</span><span class="sxs-lookup"><span data-stu-id="fd606-122">Select a [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases) Linux netcoreapp release to be deployed on your cluster.</span></span>

   <span data-ttu-id="fd606-123">Par exemple, si vous souhaitez `.NET for Apache Spark v1.0.0` utiliser `netcoreapp3.1` , vous devez télécharger [Microsoft. Spark. Worker. netcoreapp 3.1. Linux-x64-1.0.0. tar. gz](https://github.com/dotnet/spark/releases/download/v1.0.0/Microsoft.Spark.Worker.netcoreapp3.1.linux-x64-1.0.0.tar.gz).</span><span class="sxs-lookup"><span data-stu-id="fd606-123">For example, if you want `.NET for Apache Spark v1.0.0` using `netcoreapp3.1`, you'd download [Microsoft.Spark.Worker.netcoreapp3.1.linux-x64-1.0.0.tar.gz](https://github.com/dotnet/spark/releases/download/v1.0.0/Microsoft.Spark.Worker.netcoreapp3.1.linux-x64-1.0.0.tar.gz).</span></span>

2. <span data-ttu-id="fd606-124">Chargez `Microsoft.Spark.Worker.<release>.tar.gz` et [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) dans un système de fichiers distribués (par exemple S3) auquel votre cluster a accès.</span><span class="sxs-lookup"><span data-stu-id="fd606-124">Upload `Microsoft.Spark.Worker.<release>.tar.gz` and [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) to a distributed file system (e.g., S3) that your cluster has access to.</span></span>

## <a name="prepare-your-net-for-apache-spark-app"></a><span data-ttu-id="fd606-125">Préparer votre application .NET pour Apache Spark</span><span class="sxs-lookup"><span data-stu-id="fd606-125">Prepare your .NET for Apache Spark app</span></span>

1. <span data-ttu-id="fd606-126">Suivez le tutoriel [Prise en main](get-started.md) pour générer votre application.</span><span class="sxs-lookup"><span data-stu-id="fd606-126">Follow the [Get Started](get-started.md) tutorial to build your app.</span></span>

2. <span data-ttu-id="fd606-127">Publiez votre application .NET Spark en tant qu’application autonome.</span><span class="sxs-lookup"><span data-stu-id="fd606-127">Publish your Spark .NET app as self-contained.</span></span>

   <span data-ttu-id="fd606-128">Exécutez la commande suivante sur Linux.</span><span class="sxs-lookup"><span data-stu-id="fd606-128">Run the following command on Linux.</span></span>

   ```dotnetcli
   dotnet publish -c Release -f netcoreapp3.1 -r ubuntu.16.04-x64
   ```

3. <span data-ttu-id="fd606-129">Produisez `<your app>.zip` pour les fichiers publiés.</span><span class="sxs-lookup"><span data-stu-id="fd606-129">Produce `<your app>.zip` for the published files.</span></span>

   <span data-ttu-id="fd606-130">Exécutez la commande suivante sur Linux en utilisant `zip`.</span><span class="sxs-lookup"><span data-stu-id="fd606-130">Run the following command on Linux using `zip`.</span></span>

   ```bash
   zip -r <your app>.zip .
   ```

4. <span data-ttu-id="fd606-131">Chargez les éléments suivants sur un système de fichiers distribués (par exemple S3) auquel votre cluster a accès :</span><span class="sxs-lookup"><span data-stu-id="fd606-131">Upload the following items to a distributed file system (e.g., S3) that your cluster has access to:</span></span>

   * <span data-ttu-id="fd606-132">`microsoft-spark-<spark_majorversion-spark_minorversion>_<scala_majorversion.scala_minorversion>-<spark_dotnet_version>.jar`: Ce fichier jar est inclus dans le package NuGet [Microsoft. Spark](https://www.nuget.org/packages/Microsoft.Spark/) et colocalisé dans le répertoire de sortie de la génération de votre application.</span><span class="sxs-lookup"><span data-stu-id="fd606-132">`microsoft-spark-<spark_majorversion-spark_minorversion>_<scala_majorversion.scala_minorversion>-<spark_dotnet_version>.jar`: This jar is included as part of the [Microsoft.Spark](https://www.nuget.org/packages/Microsoft.Spark/) NuGet package and is colocated in your app's build output directory.</span></span>
   * `<your app>.zip`
   * <span data-ttu-id="fd606-133">Les fichiers (comme les fichiers de dépendances ou les données communes accessibles à chaque worker) ou les assemblys (comme les DLL qui contiennent vos fonctions définies par l’utilisateur ou les bibliothèques dont dépend votre application) doivent être placés dans le répertoire de travail de chaque exécuteur.</span><span class="sxs-lookup"><span data-stu-id="fd606-133">Files (like dependency files or common data accessible to every worker) or assemblies (like DLLs that contain your user-defined functions or libraries that your app depends on) to be placed in the working directory of each executor.</span></span>

## <a name="deploy-to-amazon-emr-spark"></a><span data-ttu-id="fd606-134">Déployer sur Amazon EMR Spark</span><span class="sxs-lookup"><span data-stu-id="fd606-134">Deploy to Amazon EMR Spark</span></span>

<span data-ttu-id="fd606-135">[Amazon EMR](https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-what-is-emr.html) est une plateforme de cluster gérée qui simplifie l’exécution de frameworks Big Data sur AWS.</span><span class="sxs-lookup"><span data-stu-id="fd606-135">[Amazon EMR](https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-what-is-emr.html) is a managed cluster platform that simplifies running big data frameworks on AWS.</span></span>

> [!NOTE]
> <span data-ttu-id="fd606-136">Amazon EMR Spark est basé sur Linux.</span><span class="sxs-lookup"><span data-stu-id="fd606-136">Amazon EMR Spark is Linux-based.</span></span> <span data-ttu-id="fd606-137">Par conséquent, si vous voulez déployer votre application sur Amazon EMR Spark, vérifiez que votre application est compatible avec .NET Standard et que vous utilisez le [compilateur .NET Core](https://dotnet.microsoft.com/download) pour compiler votre application.</span><span class="sxs-lookup"><span data-stu-id="fd606-137">Therefore, if you are interested in deploying your app to Amazon EMR Spark, make sure your app is .NET Standard compatible and that you use the [.NET Core compiler](https://dotnet.microsoft.com/download) to compile your app.</span></span>

### <a name="deploy-microsoftsparkworker"></a><span data-ttu-id="fd606-138">Déployer Microsoft.Spark.Worker</span><span class="sxs-lookup"><span data-stu-id="fd606-138">Deploy Microsoft.Spark.Worker</span></span>

<span data-ttu-id="fd606-139">Cette étape est nécessaire seulement lors de la création du cluster.</span><span class="sxs-lookup"><span data-stu-id="fd606-139">This step is only required at cluster creation.</span></span>

<span data-ttu-id="fd606-140">Exécutez `install-worker.sh` lors de la création du cluster en utilisant des [actions de démarrage](https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-plan-bootstrap.html).</span><span class="sxs-lookup"><span data-stu-id="fd606-140">Run `install-worker.sh` during cluster creation using [Bootstrap Actions](https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-plan-bootstrap.html).</span></span>

<span data-ttu-id="fd606-141">Exécutez la commande suivante sur Linux en utilisant AWS CLI.</span><span class="sxs-lookup"><span data-stu-id="fd606-141">Run the following command on Linux using AWS CLI.</span></span>

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

## <a name="run-your-app"></a><span data-ttu-id="fd606-142">Exécuter l’application</span><span class="sxs-lookup"><span data-stu-id="fd606-142">Run your app</span></span>

<span data-ttu-id="fd606-143">Il existe deux façons d’exécuter votre application dans Amazon EMR Spark : spark-submit et Amazon EMR Steps.</span><span class="sxs-lookup"><span data-stu-id="fd606-143">There are two ways to run your app in Amazon EMR Spark: spark-submit and Amazon EMR Steps.</span></span>

### <a name="use-spark-submit"></a><span data-ttu-id="fd606-144">Utiliser spark-submit</span><span class="sxs-lookup"><span data-stu-id="fd606-144">Use spark-submit</span></span>

<span data-ttu-id="fd606-145">Vous pouvez utiliser la commande [spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html) pour soumettre des travaux .NET pour Apache Spark à Amazon EMR Spark.</span><span class="sxs-lookup"><span data-stu-id="fd606-145">You can use the [spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html) command to submit .NET for Apache Spark jobs to Amazon EMR Spark.</span></span>

1. <span data-ttu-id="fd606-146">`ssh` dans un des nœuds du cluster.</span><span class="sxs-lookup"><span data-stu-id="fd606-146">`ssh` into one of the nodes in the cluster.</span></span>

2. <span data-ttu-id="fd606-147">Exécutez `spark-submit`.</span><span class="sxs-lookup"><span data-stu-id="fd606-147">Run `spark-submit`.</span></span>

   ```bash
   spark-submit \
   --master yarn \
   --class org.apache.spark.deploy.dotnet.DotnetRunner \
   --files <comma-separated list of assemblies that contain UDF definitions, if any> \
   s3://mybucket/<some dir>/microsoft-spark-<spark_majorversion-spark_minorversion>_<scala_majorversion.scala_minorversion>-<spark_dotnet_version>.jar \
   s3://mybucket/<some dir>/<your app>.zip <your app> <app args>
   ```

### <a name="use-amazon-emr-steps"></a><span data-ttu-id="fd606-148">Utiliser Amazon EMR Steps</span><span class="sxs-lookup"><span data-stu-id="fd606-148">Use Amazon EMR Steps</span></span>

<span data-ttu-id="fd606-149">Vous pouvez utiliser [Amazon EMR Steps](https://docs.aws.amazon.com/emr/latest/ReleaseGuide/emr-spark-submit-step.html) pour soumettre des travaux au framework Spark installé sur le cluster EMR.</span><span class="sxs-lookup"><span data-stu-id="fd606-149">[Amazon EMR Steps](https://docs.aws.amazon.com/emr/latest/ReleaseGuide/emr-spark-submit-step.html) can be used to submit jobs to the Spark framework installed on the EMR cluster.</span></span>

<span data-ttu-id="fd606-150">Exécutez la commande suivante sur Linux en utilisant AWS CLI.</span><span class="sxs-lookup"><span data-stu-id="fd606-150">Run the following command on Linux using AWS CLI.</span></span>

```bash
aws emr add-steps \
--cluster-id j-xxxxxxxxxxxxx \
--steps Type=spark,Name="Spark Program",Args=[--master,yarn,--files,s3://mybucket/<some dir>/<udf assembly>,--class,org.apache.spark.deploy.dotnet.DotnetRunner,s3://mybucket/<some dir>/microsoft-spark-<spark_majorversion-spark_minorversion>_<scala_majorversion.scala_minorversion>-<spark_dotnet_version>.jar,s3://mybucket/<some dir>/<your app>.zip,<your app>,<app arg 1>,<app arg 2>,...,<app arg n>],ActionOnFailure=CONTINUE
```

## <a name="next-steps"></a><span data-ttu-id="fd606-151">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="fd606-151">Next steps</span></span>

<span data-ttu-id="fd606-152">Dans ce tutoriel, vous avez déployé votre application .NET pour Apache Spark sur Amazon EMR Spark.</span><span class="sxs-lookup"><span data-stu-id="fd606-152">In this tutorial, you deployed your .NET for Apache Spark application to Amazon EMR Spark.</span></span> <span data-ttu-id="fd606-153">Pour des exemples de projets .NET pour Apache Spark, accédez à GitHub.</span><span class="sxs-lookup"><span data-stu-id="fd606-153">For .NET for Apache Spark example projects, continue to GitHub.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="fd606-154">Exemples .NET pour Apache Spark</span><span class="sxs-lookup"><span data-stu-id="fd606-154">.NET for Apache Spark samples</span></span>](https://github.com/dotnet/spark/tree/master/examples)
