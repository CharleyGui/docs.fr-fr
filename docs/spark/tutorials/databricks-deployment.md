---
title: Déployer une application .NET pour Apache Spark sur Databricks
description: Découvrez comment déployer une application .NET pour Apache Spark sur Databricks.
ms.date: 05/17/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: f90d0fa4bdefe94dcf8390698e6445fad77a1bc2
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117933"
---
# <a name="deploy-a-net-for-apache-spark-application-to-databricks"></a><span data-ttu-id="75fee-103">Déployer une application .NET pour Apache Spark sur Databricks</span><span class="sxs-lookup"><span data-stu-id="75fee-103">Deploy a .NET for Apache Spark application to Databricks</span></span>

<span data-ttu-id="75fee-104">Ce tutoriel explique comment déployer une application .NET pour Apache Spark sur Databricks.</span><span class="sxs-lookup"><span data-stu-id="75fee-104">This tutorial teaches how to deploy a .NET for Apache Spark application to Databricks.</span></span>

<span data-ttu-id="75fee-105">Ce tutoriel vous montre comment effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="75fee-105">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="75fee-106">Préparer Microsoft.Spark.Worker</span><span class="sxs-lookup"><span data-stu-id="75fee-106">Prepare Microsoft.Spark.Worker</span></span>
> - <span data-ttu-id="75fee-107">Publier votre application .NET Spark</span><span class="sxs-lookup"><span data-stu-id="75fee-107">Publish your Spark .NET app</span></span>
> - <span data-ttu-id="75fee-108">Déployer votre application sur Databricks</span><span class="sxs-lookup"><span data-stu-id="75fee-108">Deploy your app to Databricks</span></span>
> - <span data-ttu-id="75fee-109">Exécuter votre application</span><span class="sxs-lookup"><span data-stu-id="75fee-109">Run your app</span></span>

## <a name="prerequisites"></a><span data-ttu-id="75fee-110">Prérequis</span><span class="sxs-lookup"><span data-stu-id="75fee-110">Prerequisites</span></span>

<span data-ttu-id="75fee-111">Avant de commencer, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="75fee-111">Before you start, do the following:</span></span>

- <span data-ttu-id="75fee-112">Téléchargez l’[interface CLI de Databricks](https://docs.databricks.com/user-guide/dev-tools/databricks-cli.html).</span><span class="sxs-lookup"><span data-stu-id="75fee-112">Download the [Databricks CLI](https://docs.databricks.com/user-guide/dev-tools/databricks-cli.html).</span></span>
- <span data-ttu-id="75fee-113">Téléchargez [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) sur votre machine locale.</span><span class="sxs-lookup"><span data-stu-id="75fee-113">Download [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) to your local machine.</span></span> <span data-ttu-id="75fee-114">Il s’agit d’un script d’assistance que vous utilisez ultérieurement pour copier les fichiers dépendants de .NET pour Apache Spark dans les nœuds Worker de votre cluster Spark.</span><span class="sxs-lookup"><span data-stu-id="75fee-114">This is a helper script that you use later to copy .NET for Apache Spark dependent files into your Spark cluster's worker nodes.</span></span>

## <a name="prepare-worker-dependencies"></a><span data-ttu-id="75fee-115">Préparer les dépendances Worker</span><span class="sxs-lookup"><span data-stu-id="75fee-115">Prepare worker dependencies</span></span>

<span data-ttu-id="75fee-116">**Microsoft.Spark.Worker** est un composant back-end qui se trouve sur les nœuds Worker individuels de votre cluster Spark.</span><span class="sxs-lookup"><span data-stu-id="75fee-116">**Microsoft.Spark.Worker** is a back-end component that lives on the individual worker nodes of your Spark cluster.</span></span> <span data-ttu-id="75fee-117">Quand vous voulez exécuter une fonction C# définie par l’utilisateur, Spark doit comprendre comment lancer le CLR .NET pour exécuter la fonction définie par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="75fee-117">When you want to execute a C# UDF (user-defined function), Spark needs to understand how to launch the .NET CLR to execute the UDF.</span></span> <span data-ttu-id="75fee-118">**Microsoft.Spark.Worker** fournit à Spark une collection de classes qui activent cette fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="75fee-118">**Microsoft.Spark.Worker** provides a collection of classes to Spark that enable this functionality.</span></span>

1. <span data-ttu-id="75fee-119">Sélectionnez une version netcoreapp Linux de [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases) à déployer sur votre cluster.</span><span class="sxs-lookup"><span data-stu-id="75fee-119">Select a [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases) Linux netcoreapp release to be deployed on your cluster.</span></span>

   <span data-ttu-id="75fee-120">Par exemple, si vous voulez `.NET for Apache Spark v0.1.0` avec `netcoreapp2.1`, vous devez télécharger [Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz](https://github.com/dotnet/spark/releases/download/v0.1.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz).</span><span class="sxs-lookup"><span data-stu-id="75fee-120">For example, if you want `.NET for Apache Spark v0.1.0` using `netcoreapp2.1`, you'd download [Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz](https://github.com/dotnet/spark/releases/download/v0.1.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz).</span></span>

2. <span data-ttu-id="75fee-121">Chargez `Microsoft.Spark.Worker.<release>.tar.gz` et [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) dans un système de fichiers distribués (par exemple DBFS) auquel votre cluster a accès.</span><span class="sxs-lookup"><span data-stu-id="75fee-121">Upload `Microsoft.Spark.Worker.<release>.tar.gz` and [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) to a distributed file system (for example, DBFS) that your cluster has access to.</span></span>

## <a name="prepare-your-net-for-apache-spark-app"></a><span data-ttu-id="75fee-122">Préparer votre application .NET pour Apache Spark</span><span class="sxs-lookup"><span data-stu-id="75fee-122">Prepare your .NET for Apache Spark app</span></span>

1. <span data-ttu-id="75fee-123">Suivez le tutoriel [Prise en main](get-started.md) pour générer votre application.</span><span class="sxs-lookup"><span data-stu-id="75fee-123">Follow the [Get Started](get-started.md) tutorial to build your app.</span></span>

2. <span data-ttu-id="75fee-124">Publiez votre application .NET Spark en tant qu’application autonome.</span><span class="sxs-lookup"><span data-stu-id="75fee-124">Publish your Spark .NET app as self-contained.</span></span>

   <span data-ttu-id="75fee-125">Vous pouvez exécuter la commande suivante sur Linux.</span><span class="sxs-lookup"><span data-stu-id="75fee-125">You can run the following command on Linux.</span></span>

   ```dotnetcli
   dotnet publish -c Release -f netcoreapp2.1 -r ubuntu.16.04-x64
   ```

3. <span data-ttu-id="75fee-126">Produisez `<your app>.zip` pour les fichiers publiés.</span><span class="sxs-lookup"><span data-stu-id="75fee-126">Produce `<your app>.zip` for the published files.</span></span>

   <span data-ttu-id="75fee-127">Vous pouvez exécuter la commande suivante sur Linux en utilisant `zip`.</span><span class="sxs-lookup"><span data-stu-id="75fee-127">You can run the following command on Linux using `zip`.</span></span>

   ```bash
   zip -r <your app>.zip .
   ```

4. <span data-ttu-id="75fee-128">Chargez les éléments suivants sur un système de fichiers distribués (par exemple DBFS) auquel votre cluster a accès :</span><span class="sxs-lookup"><span data-stu-id="75fee-128">Upload the following to a distributed file system (for example, DBFS) that your cluster has access to:</span></span>

   - <span data-ttu-id="75fee-129">`microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar`: Ce fichier jar est inclus dans le package NuGet [Microsoft.Spark](https://www.nuget.org/packages/Microsoft.Spark/) et est colocalisé dans le répertoire de sortie de la génération de votre application.</span><span class="sxs-lookup"><span data-stu-id="75fee-129">`microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar`: This jar is included as part of the [Microsoft.Spark](https://www.nuget.org/packages/Microsoft.Spark/) NuGet package and is colocated in your app's build output directory.</span></span>
   - `<your app>.zip`
   - <span data-ttu-id="75fee-130">Les fichiers (comme les fichiers de dépendances ou les données communes accessibles à chaque worker) ou les assemblys (comme les DLL qui contiennent vos fonctions définies par l’utilisateur ou les bibliothèques dont dépend votre application) doivent être placés dans le répertoire de travail de chaque exécuteur.</span><span class="sxs-lookup"><span data-stu-id="75fee-130">Files (like dependency files or common data accessible to every worker) or assemblies (like DLLs that contain your user-defined functions or libraries that your app depends on) to be placed in the working directory of each executor.</span></span>

## <a name="deploy-to-databricks"></a><span data-ttu-id="75fee-131">Déployer sur Databricks</span><span class="sxs-lookup"><span data-stu-id="75fee-131">Deploy to Databricks</span></span>

<span data-ttu-id="75fee-132">[Databricks](https://databricks.com) est une plateforme qui fournit un traitement Big Data dans le cloud avec Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="75fee-132">[Databricks](https://databricks.com) is a platform that provides cloud-based big data processing using Apache Spark.</span></span>

> [!Note] 
> <span data-ttu-id="75fee-133">[Azure Databricks](https://azure.microsoft.com/services/databricks/) et [AWS Databricks](https://databricks.com/aws) sont basés sur Linux.</span><span class="sxs-lookup"><span data-stu-id="75fee-133">[Azure Databricks](https://azure.microsoft.com/services/databricks/) and [AWS Databricks](https://databricks.com/aws) are Linux-based.</span></span> <span data-ttu-id="75fee-134">Par conséquent, si vous voulez déployer votre application sur Databricks, vérifiez que votre application est compatible avec .NET Standard et que vous utilisez le [compilateur .NET Core](https://dotnet.microsoft.com/download) pour compiler votre application.</span><span class="sxs-lookup"><span data-stu-id="75fee-134">Therefore, if you are interested in deploying your app to Databricks, make sure your app is .NET Standard compatible and that you use [.NET Core compiler](https://dotnet.microsoft.com/download) to compile your app.</span></span>

<span data-ttu-id="75fee-135">Databricks vous permet de soumettre des applications .NET pour Apache Spark à un cluster actif existant ou de créer un cluster chaque fois que vous lancez un travail.</span><span class="sxs-lookup"><span data-stu-id="75fee-135">Databricks allows you to submit .NET for Apache Spark apps to an existing active cluster or create a new cluster every time you launch a job.</span></span> <span data-ttu-id="75fee-136">Pour ce faire, vous devez installer **Microsoft.Spark.Worker** avant de soumettre une application .NET pour Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="75fee-136">This requires the **Microsoft.Spark.Worker** to be installed before you submit a .NET for Apache Spark app.</span></span>

### <a name="deploy-microsoftsparkworker"></a><span data-ttu-id="75fee-137">Déployer Microsoft.Spark.Worker</span><span class="sxs-lookup"><span data-stu-id="75fee-137">Deploy Microsoft.Spark.Worker</span></span>

<span data-ttu-id="75fee-138">Cette étape n’est nécessaire qu’une seule fois pour un cluster.</span><span class="sxs-lookup"><span data-stu-id="75fee-138">This step is only required once for a cluster.</span></span>

1. <span data-ttu-id="75fee-139">Téléchargez [db-init.sh](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh) et [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh
) sur votre machine locale.</span><span class="sxs-lookup"><span data-stu-id="75fee-139">Download [db-init.sh](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh) and [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh
) onto your local machine.</span></span>

2. <span data-ttu-id="75fee-140">Modifiez **db-init.sh** pour qu’il pointe vers la version de **Microsoft.Spark.Worker** que vous voulez télécharger et installer sur votre cluster.</span><span class="sxs-lookup"><span data-stu-id="75fee-140">Modify **db-init.sh** to point to the **Microsoft.Spark.Worker** release you want to download and install on your cluster.</span></span>

3. <span data-ttu-id="75fee-141">Installez l’[interface CLI de Databricks](https://docs.databricks.com/user-guide/dev-tools/databricks-cli.html).</span><span class="sxs-lookup"><span data-stu-id="75fee-141">Install the [Databricks CLI](https://docs.databricks.com/user-guide/dev-tools/databricks-cli.html).</span></span>

4. <span data-ttu-id="75fee-142">[Configurez les détails d’authentification](https://docs.databricks.com/user-guide/dev-tools/databricks-cli.html#set-up-authentication) pour l’interface CLI de Databricks.</span><span class="sxs-lookup"><span data-stu-id="75fee-142">[Setup authentication](https://docs.databricks.com/user-guide/dev-tools/databricks-cli.html#set-up-authentication) details for the Databricks CLI.</span></span>

5. <span data-ttu-id="75fee-143">Chargez les fichiers sur votre cluster Databricks en utilisant la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="75fee-143">Upload the files to your Databricks cluster using the following command:</span></span>

   ```bash
   cd <path-to-db-init-and-install-worker>
   databricks fs cp db-init.sh dbfs:/spark-dotnet/db-init.sh
   databricks fs cp install-worker.sh dbfs:/spark-dotnet/install-worker.sh
   ```

6. <span data-ttu-id="75fee-144">Accédez à votre espace de travail Databricks.</span><span class="sxs-lookup"><span data-stu-id="75fee-144">Go to your Databricks workspace.</span></span> <span data-ttu-id="75fee-145">Sélectionnez **Clusters** dans le menu de gauche, puis **Créer un cluster**.</span><span class="sxs-lookup"><span data-stu-id="75fee-145">Select **Clusters** from the left-side menu, and then select **Create Cluster**.</span></span>

7. <span data-ttu-id="75fee-146">Après avoir configuré le cluster de façon appropriée, définissez le **script d’initialisation** et créez le cluster.</span><span class="sxs-lookup"><span data-stu-id="75fee-146">After configuring the cluster appropriately, set the **Init Script** and create the cluster.</span></span>

   ![Image d’action de script](./media/databricks-deployment/deployment-databricks-init-script.png)

## <a name="run-your-app"></a><span data-ttu-id="75fee-148">Exécuter votre application</span><span class="sxs-lookup"><span data-stu-id="75fee-148">Run your app</span></span> 

<span data-ttu-id="75fee-149">Vous pouvez utiliser `set JAR` ou `spark-submit` pour soumettre votre travail à Databricks.</span><span class="sxs-lookup"><span data-stu-id="75fee-149">You can use `set JAR` or `spark-submit` to submit your job to Databricks.</span></span>

### <a name="use-set-jar"></a><span data-ttu-id="75fee-150">Utiliser Set JAR</span><span class="sxs-lookup"><span data-stu-id="75fee-150">Use Set JAR</span></span>

<span data-ttu-id="75fee-151">[Set JAR](https://docs.databricks.com/user-guide/jobs.html#create-a-job) vous permet de soumettre un travail à un cluster actif existant.</span><span class="sxs-lookup"><span data-stu-id="75fee-151">[Set JAR](https://docs.databricks.com/user-guide/jobs.html#create-a-job) allows you to submit a job to an existing active cluster.</span></span>

#### <a name="one-time-setup"></a><span data-ttu-id="75fee-152">Configuration unique</span><span class="sxs-lookup"><span data-stu-id="75fee-152">One-time setup</span></span>

1. <span data-ttu-id="75fee-153">Accédez à votre cluster Databricks et sélectionnez **Travaux** dans le menu de gauche.</span><span class="sxs-lookup"><span data-stu-id="75fee-153">Go to your Databricks cluster and select **Jobs** from the left-side menu.</span></span> <span data-ttu-id="75fee-154">Sélectionnez ensuite **Set JAR**.</span><span class="sxs-lookup"><span data-stu-id="75fee-154">Then select **Set JAR**.</span></span>

2. <span data-ttu-id="75fee-155">Chargez le fichier `microsoft-spark-<spark-version>-<spark-dotnet-version>.jar` approprié.</span><span class="sxs-lookup"><span data-stu-id="75fee-155">Upload the appropriate `microsoft-spark-<spark-version>-<spark-dotnet-version>.jar` file.</span></span>

3. <span data-ttu-id="75fee-156">Définissez les paramètres de façon appropriée.</span><span class="sxs-lookup"><span data-stu-id="75fee-156">Set the parameters appropriately.</span></span>

   ```
   Main Class: org.apache.spark.deploy.dotnet.DotnetRunner
   Arguments /dbfs/apps/<your-app-name>.zip <your-app-main-class>
   ```
 
4. <span data-ttu-id="75fee-157">Configurez le **cluster** pour qu’il pointe vers le cluster existant pour lequel vous avez créé le **script d’initialisation** dans la section précédente.</span><span class="sxs-lookup"><span data-stu-id="75fee-157">Configure the **Cluster** to point to the existing cluster you created the **Init Script** for in the previous section.</span></span>

#### <a name="publish-and-run-your-app"></a><span data-ttu-id="75fee-158">Publier et exécuter votre application</span><span class="sxs-lookup"><span data-stu-id="75fee-158">Publish and run your app</span></span>

1. <span data-ttu-id="75fee-159">Utilisez l’[interface CLI de Databricks](https://docs.databricks.com/user-guide/dev-tools/databricks-cli.html) pour charger votre application sur votre cluster Databricks.</span><span class="sxs-lookup"><span data-stu-id="75fee-159">Use the [Databricks CLI](https://docs.databricks.com/user-guide/dev-tools/databricks-cli.html) to upload your application to your Databricks cluster.</span></span>

      ```bash
      cd <path-to-your-app-publish-directory>
      databricks fs cp <your-app-name>.zip dbfs:/apps/<your-app-name>.zip
      ```

2. <span data-ttu-id="75fee-160">Cette étape est nécessaire seulement si les assemblys de votre application (par exemple des DLL contenant des fonctions définies par l’utilisateur ainsi que leurs dépendances) doivent être placés dans le répertoire de travail de chaque **Microsoft.Spark.Worker**.</span><span class="sxs-lookup"><span data-stu-id="75fee-160">This step is only required if your app assemblies (for example, DLLs that contain user-defined functions along with their dependencies) need to be placed in the working directory of each **Microsoft.Spark.Worker**.</span></span>

   - <span data-ttu-id="75fee-161">Charger les assemblys de votre application sur votre cluster Databricks</span><span class="sxs-lookup"><span data-stu-id="75fee-161">Upload your application assemblies to your Databricks cluster</span></span>
      
      ```bash
      cd <path-to-your-app-publish-directory>
      databricks fs cp <assembly>.dll dbfs:/apps/dependencies
      ```

   - <span data-ttu-id="75fee-162">Décommentez et modifiez la section des dépendances de l’application dans [db-init.sh](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh) pour la faire pointer vers le chemin des dépendances de votre application et la faire charger sur votre cluster Databricks.</span><span class="sxs-lookup"><span data-stu-id="75fee-162">Uncomment and modify the app dependencies section in [db-init.sh](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh) to point to your app dependencies path and upload to your Databricks cluster.</span></span>
   
      ```bash
      cd <path-to-db-init-and-install-worker>
      databricks fs cp db-init.sh dbfs:/spark-dotnet/db-init.sh
      ```
   
   - <span data-ttu-id="75fee-163">Redémarrez votre cluster.</span><span class="sxs-lookup"><span data-stu-id="75fee-163">Restart your cluster.</span></span>

3. <span data-ttu-id="75fee-164">Accédez à votre cluster Databricks dans votre espace de travail Databricks.</span><span class="sxs-lookup"><span data-stu-id="75fee-164">Go to your Databricks cluster in your Databricks workspace.</span></span> <span data-ttu-id="75fee-165">Sous **Travaux**, sélectionnez votre travail, puis sélectionnez **Exécuter maintenant** pour exécuter votre travail.</span><span class="sxs-lookup"><span data-stu-id="75fee-165">Under **Jobs**, select your job and then select **Run Now** to run your job.</span></span>

### <a name="use-spark-submit"></a><span data-ttu-id="75fee-166">Utiliser spark-submit</span><span class="sxs-lookup"><span data-stu-id="75fee-166">Use spark-submit</span></span>

<span data-ttu-id="75fee-167">La commande [spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html) vous permet de soumettre un travail à un nouveau cluster.</span><span class="sxs-lookup"><span data-stu-id="75fee-167">The [spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html) command allows you to submit a job to a new cluster.</span></span>

1. <span data-ttu-id="75fee-168">[Créez un travail](https://docs.databricks.com/user-guide/jobs.html) et sélectionnez **Configurer spark-submit**.</span><span class="sxs-lookup"><span data-stu-id="75fee-168">[Create a Job](https://docs.databricks.com/user-guide/jobs.html) and select **Configure spark-submit**.</span></span>

2. <span data-ttu-id="75fee-169">Configurez `spark-submit` avec les paramètres suivants :</span><span class="sxs-lookup"><span data-stu-id="75fee-169">Configure `spark-submit` with the following parameters:</span></span>

      ```bash
      ["--files","/dbfs/<path-to>/<app assembly/file to deploy to worker>","--class","org.apache.spark.deploy.dotnet.DotnetRunner","/dbfs/<path-to>/microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar","/dbfs/<path-to>/<app name>.zip","<app bin name>","app arg1","app arg2"]
      ```

3. <span data-ttu-id="75fee-170">Accédez à votre cluster Databricks dans votre espace de travail Databricks.</span><span class="sxs-lookup"><span data-stu-id="75fee-170">Go to your Databricks cluster in your Databricks workspace.</span></span> <span data-ttu-id="75fee-171">Sous **Travaux**, sélectionnez votre travail, puis sélectionnez **Exécuter maintenant** pour exécuter votre travail.</span><span class="sxs-lookup"><span data-stu-id="75fee-171">Under **Jobs**, select your job and then select **Run Now** to run your job.</span></span>

## <a name="next-steps"></a><span data-ttu-id="75fee-172">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="75fee-172">Next steps</span></span>

<span data-ttu-id="75fee-173">Dans ce tutoriel, vous avez déployé votre application .NET pour Apache Spark sur Databricks.</span><span class="sxs-lookup"><span data-stu-id="75fee-173">In this tutorial, you deployed your .NET for Apache Spark application to Databricks.</span></span> <span data-ttu-id="75fee-174">Pour plus d’informations sur Databricks, consultez la documentation Azure Databricks.</span><span class="sxs-lookup"><span data-stu-id="75fee-174">To learn more about Databricks, continue to the Azure Databricks Documentation.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="75fee-175">Documentation Azure Databricks</span><span class="sxs-lookup"><span data-stu-id="75fee-175">Azure Databricks Documentation</span></span>](https://docs.microsoft.com/azure/azure-databricks/)
