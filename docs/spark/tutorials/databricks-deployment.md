---
title: Déployer une application .NET pour Apache Spark sur Databricks
description: Découvrez comment déployer un .NET pour Apache Spark application sur Databricks.
ms.date: 05/17/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: ca9e93a413622c84325ca9fc8bac17268b990c5a
ms.sourcegitcommit: 127343afce8422bfa944c8b0c4ecc8f79f653255
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2019
ms.locfileid: "69576966"
---
# <a name="deploy-a-net-for-apache-spark-application-to-databricks"></a><span data-ttu-id="41f1b-103">Déployer une application .NET pour Apache Spark sur Databricks</span><span class="sxs-lookup"><span data-stu-id="41f1b-103">Deploy a .NET for Apache Spark application to Databricks</span></span>

<span data-ttu-id="41f1b-104">Ce didacticiel explique comment déployer un .NET pour Apache Spark application sur Databricks.</span><span class="sxs-lookup"><span data-stu-id="41f1b-104">This tutorial teaches how to deploy a .NET for Apache Spark application to Databricks.</span></span>

<span data-ttu-id="41f1b-105">Ce tutoriel vous montre comment effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="41f1b-105">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="41f1b-106">Préparer Microsoft. Spark. Worker</span><span class="sxs-lookup"><span data-stu-id="41f1b-106">Prepare Microsoft.Spark.Worker</span></span>
> * <span data-ttu-id="41f1b-107">Publier votre application Spark .NET</span><span class="sxs-lookup"><span data-stu-id="41f1b-107">Publish your Spark .NET app</span></span>
> * <span data-ttu-id="41f1b-108">Déployer votre application sur Databricks</span><span class="sxs-lookup"><span data-stu-id="41f1b-108">Deploy your app to Databricks</span></span>
> * <span data-ttu-id="41f1b-109">Exécuter votre application</span><span class="sxs-lookup"><span data-stu-id="41f1b-109">Run your app</span></span>

## <a name="prerequisites"></a><span data-ttu-id="41f1b-110">Prérequis</span><span class="sxs-lookup"><span data-stu-id="41f1b-110">Prerequisites</span></span>

<span data-ttu-id="41f1b-111">Avant de commencer, procédez comme suit:</span><span class="sxs-lookup"><span data-stu-id="41f1b-111">Before you start, do the following:</span></span>

* <span data-ttu-id="41f1b-112">Téléchargez l' [interface CLI Databricks](https://docs.databricks.com/user-guide/dev-tools/databricks-cli.html).</span><span class="sxs-lookup"><span data-stu-id="41f1b-112">Download the [Databricks CLI](https://docs.databricks.com/user-guide/dev-tools/databricks-cli.html).</span></span>
* <span data-ttu-id="41f1b-113">Téléchargez [install-Worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) sur votre ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="41f1b-113">Download [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) to your local machine.</span></span> <span data-ttu-id="41f1b-114">Il s’agit d’un script d’assistance que vous utilisez ultérieurement pour copier .NET pour Apache Spark fichiers dépendants dans les nœuds Worker du cluster Spark.</span><span class="sxs-lookup"><span data-stu-id="41f1b-114">This is a helper script that you use later to copy .NET for Apache Spark dependent files into your Spark cluster's worker nodes.</span></span>

## <a name="prepare-worker-dependencies"></a><span data-ttu-id="41f1b-115">Préparer les dépendances de Worker</span><span class="sxs-lookup"><span data-stu-id="41f1b-115">Prepare worker dependencies</span></span>

<span data-ttu-id="41f1b-116">**Microsoft. Spark. Worker** est un composant principal qui réside sur les nœuds Worker individuels de votre cluster Spark.</span><span class="sxs-lookup"><span data-stu-id="41f1b-116">**Microsoft.Spark.Worker** is a back-end component that lives on the individual worker nodes of your Spark cluster.</span></span> <span data-ttu-id="41f1b-117">Lorsque vous souhaitez exécuter une C# fonction définie par l’utilisateur (UDF), Spark doit comprendre comment lancer le CLR .net pour exécuter l’UDF.</span><span class="sxs-lookup"><span data-stu-id="41f1b-117">When you want to execute a C# UDF (user-defined function), Spark needs to understand how to launch the .NET CLR to execute the UDF.</span></span> <span data-ttu-id="41f1b-118">**Microsoft. Spark. Worker** fournit une collection de classes à Spark qui activent cette fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="41f1b-118">**Microsoft.Spark.Worker** provides a collection of classes to Spark that enable this functionality.</span></span>

1. <span data-ttu-id="41f1b-119">Sélectionnez une version de netcoreapp de [Microsoft. Spark. Worker](https://github.com/dotnet/spark/releases) Linux à déployer sur votre cluster.</span><span class="sxs-lookup"><span data-stu-id="41f1b-119">Select a [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases) Linux netcoreapp release to be deployed on your cluster.</span></span>

   <span data-ttu-id="41f1b-120">Par exemple, si vous souhaitez `.NET for Apache Spark v0.1.0` utiliser `netcoreapp2.1`, vous devez télécharger [Microsoft. Spark. Worker. netcoreapp 2.1. Linux-x64-0.1.0. tar. gz](https://github.com/dotnet/spark/releases/download/v0.1.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz).</span><span class="sxs-lookup"><span data-stu-id="41f1b-120">For example, if you want `.NET for Apache Spark v0.1.0` using `netcoreapp2.1`, you'd download [Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz](https://github.com/dotnet/spark/releases/download/v0.1.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz).</span></span>

2. <span data-ttu-id="41f1b-121">Téléchargez `Microsoft.Spark.Worker.<release>.tar.gz` et [install-Worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) dans un système de fichiers distribués (par exemple, dBFS) auquel votre cluster a accès.</span><span class="sxs-lookup"><span data-stu-id="41f1b-121">Upload `Microsoft.Spark.Worker.<release>.tar.gz` and [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) to a distributed file system (for example, DBFS) that your cluster has access to.</span></span>

## <a name="prepare-your-net-for-apache-spark-app"></a><span data-ttu-id="41f1b-122">Préparer votre application .NET pour Apache Spark</span><span class="sxs-lookup"><span data-stu-id="41f1b-122">Prepare your .NET for Apache Spark app</span></span>

1. <span data-ttu-id="41f1b-123">Suivez le didacticiel de [prise en main](get-started.md) pour créer votre application.</span><span class="sxs-lookup"><span data-stu-id="41f1b-123">Follow the [Get Started](get-started.md) tutorial to build your app.</span></span>

2. <span data-ttu-id="41f1b-124">Publiez votre application Spark .NET comme autonome.</span><span class="sxs-lookup"><span data-stu-id="41f1b-124">Publish your Spark .NET app as self-contained.</span></span>

   <span data-ttu-id="41f1b-125">Vous pouvez exécuter la commande suivante sur Linux.</span><span class="sxs-lookup"><span data-stu-id="41f1b-125">You can run the following command on Linux.</span></span>

   ```bash
   dotnet publish -c Release -f netcoreapp2.1 -r ubuntu.16.04-x64
   ```

3. <span data-ttu-id="41f1b-126">Produit `<your app>.zip` pour les fichiers publiés.</span><span class="sxs-lookup"><span data-stu-id="41f1b-126">Produce `<your app>.zip` for the published files.</span></span>

   <span data-ttu-id="41f1b-127">Vous pouvez exécuter la commande suivante sur Linux à `zip`l’aide de.</span><span class="sxs-lookup"><span data-stu-id="41f1b-127">You can run the following command on Linux using `zip`.</span></span>

   ```bash
   zip -r <your app>.zip .
   ```

4. <span data-ttu-id="41f1b-128">Téléchargez les éléments suivants dans un système de fichiers distribués (par exemple, DBFS) auquel votre cluster a accès:</span><span class="sxs-lookup"><span data-stu-id="41f1b-128">Upload the following to a distributed file system (for example, DBFS) that your cluster has access to:</span></span>

   * <span data-ttu-id="41f1b-129">`microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar`: Ce fichier jar est inclus dans le package NuGet [Microsoft. Spark](https://www.nuget.org/packages/Microsoft.Spark/) et colocalisé dans le répertoire de sortie de la génération de votre application.</span><span class="sxs-lookup"><span data-stu-id="41f1b-129">`microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar`: This jar is included as part of the [Microsoft.Spark](https://www.nuget.org/packages/Microsoft.Spark/) NuGet package and is colocated in your app's build output directory.</span></span>
   * `<your app>.zip`
   * <span data-ttu-id="41f1b-130">Les fichiers (comme les fichiers de dépendance ou les données communes accessibles à chaque Worker) ou les assemblys (comme les dll qui contiennent vos fonctions définies par l’utilisateur ou les bibliothèques dont dépend votre application) doivent être placés dans le répertoire de travail de chaque exécuteur.</span><span class="sxs-lookup"><span data-stu-id="41f1b-130">Files (like dependency files or common data accessible to every worker) or assemblies (like DLLs that contain your user-defined functions or libraries that your app depends on) to be placed in the working directory of each executor.</span></span>

## <a name="deploy-to-databricks"></a><span data-ttu-id="41f1b-131">Déployer sur Databricks</span><span class="sxs-lookup"><span data-stu-id="41f1b-131">Deploy to Databricks</span></span>

<span data-ttu-id="41f1b-132">[Databricks](https://databricks.com) est une plateforme qui fournit le traitement Big Data basé sur le Cloud à l’aide de Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="41f1b-132">[Databricks](https://databricks.com) is a platform that provides cloud-based big data processing using Apache Spark.</span></span>

> [!Note] 
> <span data-ttu-id="41f1b-133">[Azure Databricks](https://azure.microsoft.com/services/databricks/) et [AWS Databricks](https://databricks.com/aws) sont basés sur Linux.</span><span class="sxs-lookup"><span data-stu-id="41f1b-133">[Azure Databricks](https://azure.microsoft.com/services/databricks/) and [AWS Databricks](https://databricks.com/aws) are Linux-based.</span></span> <span data-ttu-id="41f1b-134">Par conséquent, si vous souhaitez déployer votre application sur Databricks, assurez-vous que votre application est .NET Standard compatible et que vous utilisez le [compilateur .net Core](https://dotnet.microsoft.com/download) pour compiler votre application.</span><span class="sxs-lookup"><span data-stu-id="41f1b-134">Therefore, if you are interested in deploying your app to Databricks, make sure your app is .NET Standard compatible and that you use [.NET Core compiler](https://dotnet.microsoft.com/download) to compile your app.</span></span>

<span data-ttu-id="41f1b-135">Databricks vous permet de soumettre .NET pour Apache Spark des applications à un cluster actif existant ou de créer un nouveau cluster chaque fois que vous lancez un travail.</span><span class="sxs-lookup"><span data-stu-id="41f1b-135">Databricks allows you to submit .NET for Apache Spark apps to an existing active cluster or create a new cluster every time you launch a job.</span></span> <span data-ttu-id="41f1b-136">Pour ce faire, vous devez installer **Microsoft. Spark. Worker** avant d’envoyer un .net pour Apache Spark application.</span><span class="sxs-lookup"><span data-stu-id="41f1b-136">This requires the **Microsoft.Spark.Worker** to be installed before you submit a .NET for Apache Spark app.</span></span>

### <a name="deploy-microsoftsparkworker"></a><span data-ttu-id="41f1b-137">Déployer Microsoft. Spark. Worker</span><span class="sxs-lookup"><span data-stu-id="41f1b-137">Deploy Microsoft.Spark.Worker</span></span>

<span data-ttu-id="41f1b-138">Cette étape n’est requise qu’une seule fois pour un cluster.</span><span class="sxs-lookup"><span data-stu-id="41f1b-138">This step is only required once for a cluster.</span></span>

1. <span data-ttu-id="41f1b-139">Téléchargez [DB-init.sh](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh) et [install-Worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh
) sur votre ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="41f1b-139">Download [db-init.sh](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh) and [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh
) onto your local machine.</span></span>

2. <span data-ttu-id="41f1b-140">Modifiez **DB-init.sh** pour qu’il pointe vers la version **Microsoft. Spark. Worker** que vous souhaitez télécharger et installer sur votre cluster.</span><span class="sxs-lookup"><span data-stu-id="41f1b-140">Modify **db-init.sh** to point to the **Microsoft.Spark.Worker** release you want to download and install on your cluster.</span></span>

3. <span data-ttu-id="41f1b-141">Installez l' [interface CLI Databricks](https://docs.databricks.com/user-guide/dev-tools/databricks-cli.html).</span><span class="sxs-lookup"><span data-stu-id="41f1b-141">Install the [Databricks CLI](https://docs.databricks.com/user-guide/dev-tools/databricks-cli.html).</span></span>

4. <span data-ttu-id="41f1b-142">Configurez les détails d' [authentification](https://docs.databricks.com/user-guide/dev-tools/databricks-cli.html#set-up-authentication) pour l’interface CLI Databricks.</span><span class="sxs-lookup"><span data-stu-id="41f1b-142">[Setup authentication](https://docs.databricks.com/user-guide/dev-tools/databricks-cli.html#set-up-authentication) details for the Databricks CLI.</span></span>

5. <span data-ttu-id="41f1b-143">Téléchargez les fichiers sur votre cluster Databricks à l’aide de la commande suivante:</span><span class="sxs-lookup"><span data-stu-id="41f1b-143">Upload the files to your Databricks cluster using the following command:</span></span>

   ```bash
   cd <path-to-db-init-and-install-worker>
   databricks fs cp db-init.sh dbfs:/spark-dotnet/db-init.sh
   databricks fs cp install-worker.sh dbfs:/spark-dotnet/install-worker.sh
   ```

6. <span data-ttu-id="41f1b-144">Accédez à votre espace de travail Databricks.</span><span class="sxs-lookup"><span data-stu-id="41f1b-144">Go to your Databricks workspace.</span></span> <span data-ttu-id="41f1b-145">Sélectionnez **clusters** dans le menu de gauche, puis **créer un cluster**.</span><span class="sxs-lookup"><span data-stu-id="41f1b-145">Select **Clusters** from the left-side menu, and then select **Create Cluster**.</span></span>

7. <span data-ttu-id="41f1b-146">Après avoir configuré le cluster de manière appropriée, définissez le **script init** et créez le cluster.</span><span class="sxs-lookup"><span data-stu-id="41f1b-146">After configuring the cluster appropriately, set the **Init Script** and create the cluster.</span></span>

   ![Image d’action de script](./media/databricks-deployment/deployment-databricks-init-script.png)

## <a name="run-your-app"></a><span data-ttu-id="41f1b-148">Exécuter votre application</span><span class="sxs-lookup"><span data-stu-id="41f1b-148">Run your app</span></span> 

<span data-ttu-id="41f1b-149">Vous pouvez utiliser `set JAR` ou `spark-submit` pour envoyer votre travail à Databricks.</span><span class="sxs-lookup"><span data-stu-id="41f1b-149">You can use `set JAR` or `spark-submit` to submit your job to Databricks.</span></span>

### <a name="use-set-jar"></a><span data-ttu-id="41f1b-150">Utiliser SET JAR</span><span class="sxs-lookup"><span data-stu-id="41f1b-150">Use Set JAR</span></span>

<span data-ttu-id="41f1b-151">[Set jar](https://docs.databricks.com/user-guide/jobs.html#create-a-job) vous permet de soumettre un travail à un cluster actif existant.</span><span class="sxs-lookup"><span data-stu-id="41f1b-151">[Set JAR](https://docs.databricks.com/user-guide/jobs.html#create-a-job) allows you to submit a job to an existing active cluster.</span></span>

#### <a name="one-time-setup"></a><span data-ttu-id="41f1b-152">Configuration unique</span><span class="sxs-lookup"><span data-stu-id="41f1b-152">One-time setup</span></span>

1. <span data-ttu-id="41f1b-153">Accédez à votre cluster Databricks et sélectionnez **travaux** dans le menu de gauche.</span><span class="sxs-lookup"><span data-stu-id="41f1b-153">Go to your Databricks cluster and select **Jobs** from the left-side menu.</span></span> <span data-ttu-id="41f1b-154">Sélectionnez ensuite **Set jar**.</span><span class="sxs-lookup"><span data-stu-id="41f1b-154">Then select **Set JAR**.</span></span>

2. <span data-ttu-id="41f1b-155">Téléchargez le fichier `microsoft-spark-<spark-version>-<spark-dotnet-version>.jar` approprié.</span><span class="sxs-lookup"><span data-stu-id="41f1b-155">Upload the appropriate `microsoft-spark-<spark-version>-<spark-dotnet-version>.jar` file.</span></span>

3. <span data-ttu-id="41f1b-156">Définissez les paramètres de manière appropriée.</span><span class="sxs-lookup"><span data-stu-id="41f1b-156">Set the parameters appropriately.</span></span>

   ```
   Main Class: org.apache.spark.deploy.DotnetRunner
   Arguments /dbfs/apps/<your-app-name>.zip <your-app-main-class>
   ```
 
4. <span data-ttu-id="41f1b-157">Configurez le **cluster** pour qu’il pointe vers le cluster existant pour lequel vous avez créé le **script init** pour dans la section précédente.</span><span class="sxs-lookup"><span data-stu-id="41f1b-157">Configure the **Cluster** to point to the existing cluster you created the **Init Script** for in the previous section.</span></span>

#### <a name="publish-and-run-your-app"></a><span data-ttu-id="41f1b-158">Publier et exécuter votre application</span><span class="sxs-lookup"><span data-stu-id="41f1b-158">Publish and run your app</span></span>

1. <span data-ttu-id="41f1b-159">Utilisez l' [interface CLI Databricks](https://docs.databricks.com/user-guide/dev-tools/databricks-cli.html) pour charger votre application sur votre cluster Databricks.</span><span class="sxs-lookup"><span data-stu-id="41f1b-159">Use the [Databricks CLI](https://docs.databricks.com/user-guide/dev-tools/databricks-cli.html) to upload your application to your Databricks cluster.</span></span>

      ```bash
      cd <path-to-your-app-publish-directory>
      databricks fs cp <your-app-name>.zip dbfs:/apps/<your-app-name>.zip
      ```

2. <span data-ttu-id="41f1b-160">Cette étape est requise uniquement si vos assemblys d’application (par exemple, les dll qui contiennent des fonctions définies par l’utilisateur ainsi que leurs dépendances) doivent être placés dans le répertoire de travail de chaque **Microsoft. Spark. Worker**.</span><span class="sxs-lookup"><span data-stu-id="41f1b-160">This step is only required if your app assemblies (for example, DLLs that contain user-defined functions along with their dependencies) need to be placed in the working directory of each **Microsoft.Spark.Worker**.</span></span>

   - <span data-ttu-id="41f1b-161">Charger vos assemblys d’application sur votre cluster Databricks</span><span class="sxs-lookup"><span data-stu-id="41f1b-161">Upload your application assemblies to your Databricks cluster</span></span>
      
      ```bash
      cd <path-to-your-app-publish-directory>
      databricks fs cp <assembly>.dll dbfs:/apps/dependencies
      ```

   - <span data-ttu-id="41f1b-162">Supprimez les marques de commentaire et modifiez la section dépendances de l’application dans [DB-init.sh](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh) pour pointer vers le chemin d’accès aux dépendances de votre application et téléchargez vers votre cluster Databricks.</span><span class="sxs-lookup"><span data-stu-id="41f1b-162">Uncomment and modify the app dependencies section in [db-init.sh](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh) to point to your app dependencies path and upload to your Databricks cluster.</span></span>
   
      ```bash
      cd <path-to-db-init-and-install-worker>
      databricks fs cp db-init.sh dbfs:/spark-dotnet/db-init.sh
      ```
   
   - <span data-ttu-id="41f1b-163">Redémarrez votre cluster.</span><span class="sxs-lookup"><span data-stu-id="41f1b-163">Restart your cluster.</span></span>

3. <span data-ttu-id="41f1b-164">Accédez à votre cluster Databricks dans votre espace de travail Databricks.</span><span class="sxs-lookup"><span data-stu-id="41f1b-164">Go to your Databricks cluster in your Databricks workspace.</span></span> <span data-ttu-id="41f1b-165">Sous **travaux**, sélectionnez votre tâche, puis sélectionnez **Exécuter maintenant** pour exécuter votre travail.</span><span class="sxs-lookup"><span data-stu-id="41f1b-165">Under **Jobs**, select your job and then select **Run Now** to run your job.</span></span>

### <a name="use-spark-submit"></a><span data-ttu-id="41f1b-166">Utiliser Spark-Submit</span><span class="sxs-lookup"><span data-stu-id="41f1b-166">Use spark-submit</span></span>

<span data-ttu-id="41f1b-167">La commande [Spark-Submit](https://spark.apache.org/docs/latest/submitting-applications.html) vous permet d’envoyer un travail à un nouveau cluster.</span><span class="sxs-lookup"><span data-stu-id="41f1b-167">The [spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html) command allows you to submit a job to a new cluster.</span></span>

1. <span data-ttu-id="41f1b-168">[Créez un travail](https://docs.databricks.com/user-guide/jobs.html) et sélectionnez **configurer Spark-Submit**.</span><span class="sxs-lookup"><span data-stu-id="41f1b-168">[Create a Job](https://docs.databricks.com/user-guide/jobs.html) and select **Configure spark-submit**.</span></span>

2. <span data-ttu-id="41f1b-169">Configurez `spark-submit` avec les paramètres suivants:</span><span class="sxs-lookup"><span data-stu-id="41f1b-169">Configure `spark-submit` with the following parameters:</span></span>

      ```bash
      ["--files","/dbfs/<path-to>/<app assembly/file to deploy to worker>","--class","org.apache.spark.deploy.DotnetRunner","/dbfs/<path-to>/microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar","/dbfs/<path-to>/<app name>.zip","<app bin name>","app arg1","app arg2"]
      ```

3. <span data-ttu-id="41f1b-170">Accédez à votre cluster Databricks dans votre espace de travail Databricks.</span><span class="sxs-lookup"><span data-stu-id="41f1b-170">Go to your Databricks cluster in your Databricks workspace.</span></span> <span data-ttu-id="41f1b-171">Sous **travaux**, sélectionnez votre tâche, puis sélectionnez **Exécuter maintenant** pour exécuter votre travail.</span><span class="sxs-lookup"><span data-stu-id="41f1b-171">Under **Jobs**, select your job and then select **Run Now** to run your job.</span></span>

## <a name="next-steps"></a><span data-ttu-id="41f1b-172">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="41f1b-172">Next steps</span></span>

<span data-ttu-id="41f1b-173">Dans ce didacticiel, vous avez déployé votre application .NET pour Apache Spark sur Databricks.</span><span class="sxs-lookup"><span data-stu-id="41f1b-173">In this tutorial, you deployed your .NET for Apache Spark application to Databricks.</span></span> <span data-ttu-id="41f1b-174">Pour en savoir plus sur Databricks, consultez la documentation Azure Databricks.</span><span class="sxs-lookup"><span data-stu-id="41f1b-174">To learn more about Databricks, continue to the Azure Databricks Documentation.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="41f1b-175">Documentation Azure Databricks</span><span class="sxs-lookup"><span data-stu-id="41f1b-175">Azure Databricks Documentation</span></span>](https://docs.microsoft.com/azure/azure-databricks/)
