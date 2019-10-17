---
title: Déployer une application .NET pour Apache Spark sur Databricks
description: Découvrez comment déployer une application .NET pour Apache Spark sur Databricks.
ms.date: 05/17/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 570f6bdb8eda462b815dfc7c45f6e9a3a515f0ad
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395880"
---
# <a name="deploy-a-net-for-apache-spark-application-to-databricks"></a><span data-ttu-id="695aa-103">Déployer une application .NET pour Apache Spark sur Databricks</span><span class="sxs-lookup"><span data-stu-id="695aa-103">Deploy a .NET for Apache Spark application to Databricks</span></span>

<span data-ttu-id="695aa-104">Ce tutoriel explique comment déployer une application .NET pour Apache Spark sur Databricks.</span><span class="sxs-lookup"><span data-stu-id="695aa-104">This tutorial teaches how to deploy a .NET for Apache Spark application to Databricks.</span></span>

<span data-ttu-id="695aa-105">Dans ce didacticiel, vous apprendrez à :</span><span class="sxs-lookup"><span data-stu-id="695aa-105">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="695aa-106">Préparer Microsoft.Spark.Worker</span><span class="sxs-lookup"><span data-stu-id="695aa-106">Prepare Microsoft.Spark.Worker</span></span>
> - <span data-ttu-id="695aa-107">Publier votre application .NET Spark</span><span class="sxs-lookup"><span data-stu-id="695aa-107">Publish your Spark .NET app</span></span>
> - <span data-ttu-id="695aa-108">Déployer votre application sur Databricks</span><span class="sxs-lookup"><span data-stu-id="695aa-108">Deploy your app to Databricks</span></span>
> - <span data-ttu-id="695aa-109">Exécuter votre application</span><span class="sxs-lookup"><span data-stu-id="695aa-109">Run your app</span></span>

## <a name="prerequisites"></a><span data-ttu-id="695aa-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="695aa-110">Prerequisites</span></span>

<span data-ttu-id="695aa-111">Avant de commencer, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="695aa-111">Before you start, do the following:</span></span>

- <span data-ttu-id="695aa-112">Téléchargez l’[interface CLI de Databricks](https://docs.databricks.com/user-guide/dev-tools/databricks-cli.html).</span><span class="sxs-lookup"><span data-stu-id="695aa-112">Download the [Databricks CLI](https://docs.databricks.com/user-guide/dev-tools/databricks-cli.html).</span></span>
- <span data-ttu-id="695aa-113">Téléchargez [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) sur votre machine locale.</span><span class="sxs-lookup"><span data-stu-id="695aa-113">Download [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) to your local machine.</span></span> <span data-ttu-id="695aa-114">Il s’agit d’un script d’assistance que vous utilisez ultérieurement pour copier les fichiers dépendants de .NET pour Apache Spark dans les nœuds Worker de votre cluster Spark.</span><span class="sxs-lookup"><span data-stu-id="695aa-114">This is a helper script that you use later to copy .NET for Apache Spark dependent files into your Spark cluster's worker nodes.</span></span>

## <a name="prepare-worker-dependencies"></a><span data-ttu-id="695aa-115">Préparer les dépendances Worker</span><span class="sxs-lookup"><span data-stu-id="695aa-115">Prepare worker dependencies</span></span>

<span data-ttu-id="695aa-116">**Microsoft.Spark.Worker** est un composant back-end qui se trouve sur les nœuds Worker individuels de votre cluster Spark.</span><span class="sxs-lookup"><span data-stu-id="695aa-116">**Microsoft.Spark.Worker** is a back-end component that lives on the individual worker nodes of your Spark cluster.</span></span> <span data-ttu-id="695aa-117">Quand vous voulez exécuter une fonction C# définie par l’utilisateur, Spark doit comprendre comment lancer le CLR .NET pour exécuter la fonction définie par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="695aa-117">When you want to execute a C# UDF (user-defined function), Spark needs to understand how to launch the .NET CLR to execute the UDF.</span></span> <span data-ttu-id="695aa-118">**Microsoft.Spark.Worker** fournit à Spark une collection de classes qui activent cette fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="695aa-118">**Microsoft.Spark.Worker** provides a collection of classes to Spark that enable this functionality.</span></span>

1. <span data-ttu-id="695aa-119">Sélectionnez une version netcoreapp Linux de [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases) à déployer sur votre cluster.</span><span class="sxs-lookup"><span data-stu-id="695aa-119">Select a [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases) Linux netcoreapp release to be deployed on your cluster.</span></span>

   <span data-ttu-id="695aa-120">Par exemple, si vous voulez `.NET for Apache Spark v0.1.0` avec `netcoreapp2.1`, vous devez télécharger [Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz](https://github.com/dotnet/spark/releases/download/v0.1.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz).</span><span class="sxs-lookup"><span data-stu-id="695aa-120">For example, if you want `.NET for Apache Spark v0.1.0` using `netcoreapp2.1`, you'd download [Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz](https://github.com/dotnet/spark/releases/download/v0.1.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz).</span></span>

2. <span data-ttu-id="695aa-121">Chargez `Microsoft.Spark.Worker.<release>.tar.gz` et [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) dans un système de fichiers distribués (par exemple DBFS) auquel votre cluster a accès.</span><span class="sxs-lookup"><span data-stu-id="695aa-121">Upload `Microsoft.Spark.Worker.<release>.tar.gz` and [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) to a distributed file system (for example, DBFS) that your cluster has access to.</span></span>

## <a name="prepare-your-net-for-apache-spark-app"></a><span data-ttu-id="695aa-122">Préparer votre application .NET pour Apache Spark</span><span class="sxs-lookup"><span data-stu-id="695aa-122">Prepare your .NET for Apache Spark app</span></span>

1. <span data-ttu-id="695aa-123">Suivez le tutoriel [Prise en main](get-started.md) pour générer votre application.</span><span class="sxs-lookup"><span data-stu-id="695aa-123">Follow the [Get Started](get-started.md) tutorial to build your app.</span></span>

2. <span data-ttu-id="695aa-124">Publiez votre application .NET Spark en tant qu’application autonome.</span><span class="sxs-lookup"><span data-stu-id="695aa-124">Publish your Spark .NET app as self-contained.</span></span>

   <span data-ttu-id="695aa-125">Vous pouvez exécuter la commande suivante sur Linux.</span><span class="sxs-lookup"><span data-stu-id="695aa-125">You can run the following command on Linux.</span></span>

   ```dotnetcli
   dotnet publish -c Release -f netcoreapp2.1 -r ubuntu.16.04-x64
   ```

3. <span data-ttu-id="695aa-126">Produisez `<your app>.zip` pour les fichiers publiés.</span><span class="sxs-lookup"><span data-stu-id="695aa-126">Produce `<your app>.zip` for the published files.</span></span>

   <span data-ttu-id="695aa-127">Vous pouvez exécuter la commande suivante sur Linux en utilisant `zip`.</span><span class="sxs-lookup"><span data-stu-id="695aa-127">You can run the following command on Linux using `zip`.</span></span>

   ```bash
   zip -r <your app>.zip .
   ```

4. <span data-ttu-id="695aa-128">Chargez les éléments suivants sur un système de fichiers distribués (par exemple DBFS) auquel votre cluster a accès :</span><span class="sxs-lookup"><span data-stu-id="695aa-128">Upload the following to a distributed file system (for example, DBFS) that your cluster has access to:</span></span>

   - <span data-ttu-id="695aa-129">`microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar` : ce fichier jar est inclus dans le package NuGet [Microsoft. Spark](https://www.nuget.org/packages/Microsoft.Spark/) et colocalisé dans le répertoire de sortie de génération de votre application.</span><span class="sxs-lookup"><span data-stu-id="695aa-129">`microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar`: This jar is included as part of the [Microsoft.Spark](https://www.nuget.org/packages/Microsoft.Spark/) NuGet package and is colocated in your app's build output directory.</span></span>
   - `<your app>.zip`
   - <span data-ttu-id="695aa-130">Les fichiers (comme les fichiers de dépendances ou les données communes accessibles à chaque worker) ou les assemblys (comme les DLL qui contiennent vos fonctions définies par l’utilisateur ou les bibliothèques dont dépend votre application) doivent être placés dans le répertoire de travail de chaque exécuteur.</span><span class="sxs-lookup"><span data-stu-id="695aa-130">Files (like dependency files or common data accessible to every worker) or assemblies (like DLLs that contain your user-defined functions or libraries that your app depends on) to be placed in the working directory of each executor.</span></span>

## <a name="deploy-to-databricks"></a><span data-ttu-id="695aa-131">Déployer sur Databricks</span><span class="sxs-lookup"><span data-stu-id="695aa-131">Deploy to Databricks</span></span>

<span data-ttu-id="695aa-132">[Databricks](https://databricks.com) est une plateforme qui fournit un traitement Big Data dans le cloud avec Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="695aa-132">[Databricks](https://databricks.com) is a platform that provides cloud-based big data processing using Apache Spark.</span></span>

> [!NOTE]
> <span data-ttu-id="695aa-133">[Azure Databricks](https://azure.microsoft.com/services/databricks/) et [AWS Databricks](https://databricks.com/aws) sont basés sur Linux.</span><span class="sxs-lookup"><span data-stu-id="695aa-133">[Azure Databricks](https://azure.microsoft.com/services/databricks/) and [AWS Databricks](https://databricks.com/aws) are Linux-based.</span></span> <span data-ttu-id="695aa-134">Par conséquent, si vous voulez déployer votre application sur Databricks, vérifiez que votre application est compatible avec .NET Standard et que vous utilisez le [compilateur .NET Core](https://dotnet.microsoft.com/download) pour compiler votre application.</span><span class="sxs-lookup"><span data-stu-id="695aa-134">Therefore, if you are interested in deploying your app to Databricks, make sure your app is .NET Standard compatible and that you use [.NET Core compiler](https://dotnet.microsoft.com/download) to compile your app.</span></span>

<span data-ttu-id="695aa-135">Databricks vous permet de soumettre des applications .NET pour Apache Spark à un cluster actif existant ou de créer un cluster chaque fois que vous lancez un travail.</span><span class="sxs-lookup"><span data-stu-id="695aa-135">Databricks allows you to submit .NET for Apache Spark apps to an existing active cluster or create a new cluster every time you launch a job.</span></span> <span data-ttu-id="695aa-136">Pour ce faire, vous devez installer **Microsoft.Spark.Worker** avant de soumettre une application .NET pour Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="695aa-136">This requires the **Microsoft.Spark.Worker** to be installed before you submit a .NET for Apache Spark app.</span></span>

### <a name="deploy-microsoftsparkworker"></a><span data-ttu-id="695aa-137">Déployer Microsoft.Spark.Worker</span><span class="sxs-lookup"><span data-stu-id="695aa-137">Deploy Microsoft.Spark.Worker</span></span>

<span data-ttu-id="695aa-138">Cette étape n’est nécessaire qu’une seule fois pour un cluster.</span><span class="sxs-lookup"><span data-stu-id="695aa-138">This step is only required once for a cluster.</span></span>

1. <span data-ttu-id="695aa-139">Téléchargez [db-init.sh](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh) et [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh
) sur votre machine locale.</span><span class="sxs-lookup"><span data-stu-id="695aa-139">Download [db-init.sh](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh) and [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh
) onto your local machine.</span></span>

2. <span data-ttu-id="695aa-140">Modifiez **db-init.sh** pour qu’il pointe vers la version de **Microsoft.Spark.Worker** que vous voulez télécharger et installer sur votre cluster.</span><span class="sxs-lookup"><span data-stu-id="695aa-140">Modify **db-init.sh** to point to the **Microsoft.Spark.Worker** release you want to download and install on your cluster.</span></span>

3. <span data-ttu-id="695aa-141">Installez l’[interface CLI de Databricks](https://docs.databricks.com/user-guide/dev-tools/databricks-cli.html).</span><span class="sxs-lookup"><span data-stu-id="695aa-141">Install the [Databricks CLI](https://docs.databricks.com/user-guide/dev-tools/databricks-cli.html).</span></span>

4. <span data-ttu-id="695aa-142">[Configurez les détails d’authentification](https://docs.databricks.com/user-guide/dev-tools/databricks-cli.html#set-up-authentication) pour l’interface CLI de Databricks.</span><span class="sxs-lookup"><span data-stu-id="695aa-142">[Setup authentication](https://docs.databricks.com/user-guide/dev-tools/databricks-cli.html#set-up-authentication) details for the Databricks CLI.</span></span>

5. <span data-ttu-id="695aa-143">Chargez les fichiers sur votre cluster Databricks en utilisant la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="695aa-143">Upload the files to your Databricks cluster using the following command:</span></span>

   ```bash
   cd <path-to-db-init-and-install-worker>
   databricks fs cp db-init.sh dbfs:/spark-dotnet/db-init.sh
   databricks fs cp install-worker.sh dbfs:/spark-dotnet/install-worker.sh
   ```

6. <span data-ttu-id="695aa-144">Accédez à votre espace de travail Databricks.</span><span class="sxs-lookup"><span data-stu-id="695aa-144">Go to your Databricks workspace.</span></span> <span data-ttu-id="695aa-145">Sélectionnez **Clusters** dans le menu de gauche, puis **Créer un cluster**.</span><span class="sxs-lookup"><span data-stu-id="695aa-145">Select **Clusters** from the left-side menu, and then select **Create Cluster**.</span></span>

7. <span data-ttu-id="695aa-146">Après avoir configuré le cluster de façon appropriée, définissez le **script d’initialisation** et créez le cluster.</span><span class="sxs-lookup"><span data-stu-id="695aa-146">After configuring the cluster appropriately, set the **Init Script** and create the cluster.</span></span>

   ![Image d’action de script](./media/databricks-deployment/deployment-databricks-init-script.png)

## <a name="run-your-app"></a><span data-ttu-id="695aa-148">Exécuter votre application</span><span class="sxs-lookup"><span data-stu-id="695aa-148">Run your app</span></span>

<span data-ttu-id="695aa-149">Vous pouvez utiliser `set JAR` ou `spark-submit` pour soumettre votre travail à Databricks.</span><span class="sxs-lookup"><span data-stu-id="695aa-149">You can use `set JAR` or `spark-submit` to submit your job to Databricks.</span></span>

### <a name="use-set-jar"></a><span data-ttu-id="695aa-150">Utiliser Set JAR</span><span class="sxs-lookup"><span data-stu-id="695aa-150">Use Set JAR</span></span>

<span data-ttu-id="695aa-151">[Set JAR](https://docs.databricks.com/user-guide/jobs.html#create-a-job) vous permet de soumettre un travail à un cluster actif existant.</span><span class="sxs-lookup"><span data-stu-id="695aa-151">[Set JAR](https://docs.databricks.com/user-guide/jobs.html#create-a-job) allows you to submit a job to an existing active cluster.</span></span>

#### <a name="one-time-setup"></a><span data-ttu-id="695aa-152">Configuration unique</span><span class="sxs-lookup"><span data-stu-id="695aa-152">One-time setup</span></span>

1. <span data-ttu-id="695aa-153">Accédez à votre cluster Databricks et sélectionnez **Travaux** dans le menu de gauche.</span><span class="sxs-lookup"><span data-stu-id="695aa-153">Go to your Databricks cluster and select **Jobs** from the left-side menu.</span></span> <span data-ttu-id="695aa-154">Sélectionnez ensuite **Set JAR**.</span><span class="sxs-lookup"><span data-stu-id="695aa-154">Then select **Set JAR**.</span></span>

2. <span data-ttu-id="695aa-155">Chargez le fichier `microsoft-spark-<spark-version>-<spark-dotnet-version>.jar` approprié.</span><span class="sxs-lookup"><span data-stu-id="695aa-155">Upload the appropriate `microsoft-spark-<spark-version>-<spark-dotnet-version>.jar` file.</span></span>

3. <span data-ttu-id="695aa-156">Définissez les paramètres de façon appropriée.</span><span class="sxs-lookup"><span data-stu-id="695aa-156">Set the parameters appropriately.</span></span>

   | <span data-ttu-id="695aa-157">Paramètre</span><span class="sxs-lookup"><span data-stu-id="695aa-157">Parameter</span></span>   | <span data-ttu-id="695aa-158">valeur</span><span class="sxs-lookup"><span data-stu-id="695aa-158">Value</span></span>                                                |
   |-------------|------------------------------------------------------|
   | <span data-ttu-id="695aa-159">Classe principale</span><span class="sxs-lookup"><span data-stu-id="695aa-159">Main Class</span></span>  | <span data-ttu-id="695aa-160">org. Apache. Spark. deploy. dotnet. DotnetRunner</span><span class="sxs-lookup"><span data-stu-id="695aa-160">org.apache.spark.deploy.dotnet.DotnetRunner</span></span>          |
   | <span data-ttu-id="695aa-161">Arguments</span><span class="sxs-lookup"><span data-stu-id="695aa-161">Arguments</span></span>   | <span data-ttu-id="695aa-162">/dBFS/Apps/\<your-App-name >. zip \<your-App-main-Class ></span><span class="sxs-lookup"><span data-stu-id="695aa-162">/dbfs/apps/\<your-app-name>.zip \<your-app-main-class></span></span> |

4. <span data-ttu-id="695aa-163">Configurez le **cluster** pour qu’il pointe vers le cluster existant pour lequel vous avez créé le **script d’initialisation** dans la section précédente.</span><span class="sxs-lookup"><span data-stu-id="695aa-163">Configure the **Cluster** to point to the existing cluster you created the **Init Script** for in the previous section.</span></span>

#### <a name="publish-and-run-your-app"></a><span data-ttu-id="695aa-164">Publier et exécuter votre application</span><span class="sxs-lookup"><span data-stu-id="695aa-164">Publish and run your app</span></span>

1. <span data-ttu-id="695aa-165">Utilisez l’[interface CLI de Databricks](https://docs.databricks.com/user-guide/dev-tools/databricks-cli.html) pour charger votre application sur votre cluster Databricks.</span><span class="sxs-lookup"><span data-stu-id="695aa-165">Use the [Databricks CLI](https://docs.databricks.com/user-guide/dev-tools/databricks-cli.html) to upload your application to your Databricks cluster.</span></span>

    ```bash
    cd <path-to-your-app-publish-directory>
    databricks fs cp <your-app-name>.zip dbfs:/apps/<your-app-name>.zip
    ```

2. <span data-ttu-id="695aa-166">Cette étape est nécessaire seulement si les assemblys de votre application (par exemple des DLL contenant des fonctions définies par l’utilisateur ainsi que leurs dépendances) doivent être placés dans le répertoire de travail de chaque **Microsoft.Spark.Worker**.</span><span class="sxs-lookup"><span data-stu-id="695aa-166">This step is only required if your app assemblies (for example, DLLs that contain user-defined functions along with their dependencies) need to be placed in the working directory of each **Microsoft.Spark.Worker**.</span></span>

   - <span data-ttu-id="695aa-167">Charger les assemblys de votre application sur votre cluster Databricks</span><span class="sxs-lookup"><span data-stu-id="695aa-167">Upload your application assemblies to your Databricks cluster</span></span>

      ```bash
      cd <path-to-your-app-publish-directory>
      databricks fs cp <assembly>.dll dbfs:/apps/dependencies
      ```

   - <span data-ttu-id="695aa-168">Décommentez et modifiez la section des dépendances de l’application dans [db-init.sh](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh) pour la faire pointer vers le chemin des dépendances de votre application et la faire charger sur votre cluster Databricks.</span><span class="sxs-lookup"><span data-stu-id="695aa-168">Uncomment and modify the app dependencies section in [db-init.sh](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh) to point to your app dependencies path and upload to your Databricks cluster.</span></span>

      ```bash
      cd <path-to-db-init-and-install-worker>
      databricks fs cp db-init.sh dbfs:/spark-dotnet/db-init.sh
      ```

   - <span data-ttu-id="695aa-169">Redémarrez votre cluster.</span><span class="sxs-lookup"><span data-stu-id="695aa-169">Restart your cluster.</span></span>

3. <span data-ttu-id="695aa-170">Accédez à votre cluster Databricks dans votre espace de travail Databricks.</span><span class="sxs-lookup"><span data-stu-id="695aa-170">Go to your Databricks cluster in your Databricks workspace.</span></span> <span data-ttu-id="695aa-171">Sous **Travaux**, sélectionnez votre travail, puis sélectionnez **Exécuter maintenant** pour exécuter votre travail.</span><span class="sxs-lookup"><span data-stu-id="695aa-171">Under **Jobs**, select your job and then select **Run Now** to run your job.</span></span>

### <a name="use-spark-submit"></a><span data-ttu-id="695aa-172">Utiliser spark-submit</span><span class="sxs-lookup"><span data-stu-id="695aa-172">Use spark-submit</span></span>

<span data-ttu-id="695aa-173">La commande [spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html) vous permet de soumettre un travail à un nouveau cluster.</span><span class="sxs-lookup"><span data-stu-id="695aa-173">The [spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html) command allows you to submit a job to a new cluster.</span></span>

1. <span data-ttu-id="695aa-174">[Créez un travail](https://docs.databricks.com/user-guide/jobs.html) et sélectionnez **Configurer spark-submit**.</span><span class="sxs-lookup"><span data-stu-id="695aa-174">[Create a Job](https://docs.databricks.com/user-guide/jobs.html) and select **Configure spark-submit**.</span></span>

2. <span data-ttu-id="695aa-175">Configurez `spark-submit` avec les paramètres suivants :</span><span class="sxs-lookup"><span data-stu-id="695aa-175">Configure `spark-submit` with the following parameters:</span></span>

    ```bash
    ["--files","/dbfs/<path-to>/<app assembly/file to deploy to worker>","--class","org.apache.spark.deploy.dotnet.DotnetRunner","/dbfs/<path-to>/microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar","/dbfs/<path-to>/<app name>.zip","<app bin name>","app arg1","app arg2"]
    ```

3. <span data-ttu-id="695aa-176">Accédez à votre cluster Databricks dans votre espace de travail Databricks.</span><span class="sxs-lookup"><span data-stu-id="695aa-176">Go to your Databricks cluster in your Databricks workspace.</span></span> <span data-ttu-id="695aa-177">Sous **Travaux**, sélectionnez votre travail, puis sélectionnez **Exécuter maintenant** pour exécuter votre travail.</span><span class="sxs-lookup"><span data-stu-id="695aa-177">Under **Jobs**, select your job and then select **Run Now** to run your job.</span></span>

## <a name="next-steps"></a><span data-ttu-id="695aa-178">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="695aa-178">Next steps</span></span>

<span data-ttu-id="695aa-179">Dans ce tutoriel, vous avez déployé votre application .NET pour Apache Spark sur Databricks.</span><span class="sxs-lookup"><span data-stu-id="695aa-179">In this tutorial, you deployed your .NET for Apache Spark application to Databricks.</span></span> <span data-ttu-id="695aa-180">Pour plus d’informations sur Databricks, consultez la documentation Azure Databricks.</span><span class="sxs-lookup"><span data-stu-id="695aa-180">To learn more about Databricks, continue to the Azure Databricks Documentation.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="695aa-181">Documentation Azure Databricks</span><span class="sxs-lookup"><span data-stu-id="695aa-181">Azure Databricks Documentation</span></span>](https://docs.microsoft.com/azure/azure-databricks/)
