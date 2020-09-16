---
title: Envoyer un travail .NET pour Apache Spark à Databricks
description: Découvrez comment soumettre un travail .NET pour Apache Spark à Databricks à l’aide de Spark-Submit et Set jar.
ms.date: 06/25/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 88dc321a08f805ef8c3bf8d4d01d32dd890548d2
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557175"
---
# <a name="submit-a-net-for-apache-spark-job-to-databricks"></a><span data-ttu-id="e336e-103">Envoyer un travail .NET pour Apache Spark à Databricks</span><span class="sxs-lookup"><span data-stu-id="e336e-103">Submit a .NET for Apache Spark job to Databricks</span></span>

<span data-ttu-id="e336e-104">Vous pouvez exécuter votre .NET pour les tâches Apache Spark sur les clusters Databricks, mais il n’est pas prêt à l’emploi.</span><span class="sxs-lookup"><span data-stu-id="e336e-104">You can run your .NET for Apache Spark jobs on Databricks clusters, but it is not available out-of-the-box.</span></span> <span data-ttu-id="e336e-105">Il existe deux façons de déployer votre .NET pour le travail de Apache Spark dans Databricks : et de définir le fichier `spark-submit` jar.</span><span class="sxs-lookup"><span data-stu-id="e336e-105">There are two ways to deploy your .NET for Apache Spark job to Databricks: `spark-submit` and Set Jar.</span></span>

[!INCLUDE [spark-preview-note](../../../includes/spark-preview-note.md)]

## <a name="deploy-using-spark-submit"></a><span data-ttu-id="e336e-106">Déployer à l’aide de Spark-Submit</span><span class="sxs-lookup"><span data-stu-id="e336e-106">Deploy using spark-submit</span></span>

<span data-ttu-id="e336e-107">Vous pouvez utiliser la commande [Spark-Submit](https://spark.apache.org/docs/latest/submitting-applications.html) pour envoyer des travaux .net pour Apache Spark à Databricks.</span><span class="sxs-lookup"><span data-stu-id="e336e-107">You can use the [spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html) command to submit .NET for Apache Spark jobs to Databricks.</span></span> <span data-ttu-id="e336e-108">`spark-submit` autorise l’envoi uniquement à un cluster qui est créé à la demande.</span><span class="sxs-lookup"><span data-stu-id="e336e-108">`spark-submit` allows submission only to a cluster that gets created on-demand.</span></span>

1. <span data-ttu-id="e336e-109">Accédez à votre espace de travail Databricks et créez un travail.</span><span class="sxs-lookup"><span data-stu-id="e336e-109">Navigate to your Databricks Workspace and create a job.</span></span> <span data-ttu-id="e336e-110">Choisissez un titre pour votre travail, puis sélectionnez **configurer Spark-Submit**.</span><span class="sxs-lookup"><span data-stu-id="e336e-110">Choose a title for your job, and then select **Configure spark-submit**.</span></span> <span data-ttu-id="e336e-111">Collez les paramètres suivants dans la configuration du travail, puis sélectionnez **confirmer**.</span><span class="sxs-lookup"><span data-stu-id="e336e-111">Paste the following parameters in the job configuration, then select **Confirm**.</span></span>

    ```
    ["--files","/dbfs/<path-to>/<app assembly/file to deploy to worker>","--class","org.apache.spark.deploy.dotnet.DotnetRunner","/dbfs/<path-to>/microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar","/dbfs/<path-to>/<app name>.zip","<app bin name>","app arg1","app arg2"]
    ```

    > [!NOTE]
    > <span data-ttu-id="e336e-112">Mettez à jour le contenu du paramètre ci-dessus en fonction de vos fichiers et de votre configuration spécifiques.</span><span class="sxs-lookup"><span data-stu-id="e336e-112">Update the contents of the above parameter based on your specific files and configuration.</span></span> <span data-ttu-id="e336e-113">Par exemple, référencez la version du fichier jar Microsoft. Spark que vous avez chargée sur DBFS et utilisez le nom approprié de votre application et le fichier zip de l’application publiée.</span><span class="sxs-lookup"><span data-stu-id="e336e-113">For instance, reference the version of the Microsoft.Spark jar file that you uploaded to DBFS, and use the appropriate name of your app and published app zip file.</span></span>

2. <span data-ttu-id="e336e-114">Accédez à votre travail et sélectionnez **modifier** pour configurer le cluster de votre travail.</span><span class="sxs-lookup"><span data-stu-id="e336e-114">Navigate to your job and select **Edit** to configure your job's cluster.</span></span> <span data-ttu-id="e336e-115">Définissez la version de Databricks Runtime en fonction de la version de Apache Spark que vous souhaitez utiliser dans votre déploiement.</span><span class="sxs-lookup"><span data-stu-id="e336e-115">Set the Databricks Runtime Version based on the version of Apache Spark you wish to use in your deployment.</span></span> <span data-ttu-id="e336e-116">Sélectionnez ensuite les **Options avancées > les scripts init**et définissez le chemin d’accès du script init sur `dbfs:/spark-dotnet/db-init.sh` .</span><span class="sxs-lookup"><span data-stu-id="e336e-116">Then select **Advanced Options > Init Scripts**, and set Init Script Path as `dbfs:/spark-dotnet/db-init.sh`.</span></span> <span data-ttu-id="e336e-117">Sélectionnez **confirmer** pour confirmer vos paramètres de cluster.</span><span class="sxs-lookup"><span data-stu-id="e336e-117">Select **Confirm** to confirm your cluster settings.</span></span>

3. <span data-ttu-id="e336e-118">Accédez à votre travail et sélectionnez **Exécuter maintenant** pour exécuter votre travail sur le cluster Spark que vous venez de configurer.</span><span class="sxs-lookup"><span data-stu-id="e336e-118">Navigate to your job and select **Run Now** to run your job on your newly configured Spark cluster.</span></span> <span data-ttu-id="e336e-119">La création du cluster du travail prend quelques minutes.</span><span class="sxs-lookup"><span data-stu-id="e336e-119">It takes a few minutes for the job's cluster to be created.</span></span> <span data-ttu-id="e336e-120">Une fois créé, votre travail est envoyé.</span><span class="sxs-lookup"><span data-stu-id="e336e-120">Once it is created, your job will be submitted.</span></span> <span data-ttu-id="e336e-121">Vous pouvez afficher la sortie en sélectionnant **clusters** dans le menu de gauche de votre espace de travail Databricks, puis sélectionner **journaux du pilote**.</span><span class="sxs-lookup"><span data-stu-id="e336e-121">You can view the output by selecting **Clusters** from the left menu of your Databricks workspace, then select **Driver Logs**.</span></span>

## <a name="deploy-using-set-jar"></a><span data-ttu-id="e336e-122">Déployer à l’aide de Set jar</span><span class="sxs-lookup"><span data-stu-id="e336e-122">Deploy using Set Jar</span></span>

<span data-ttu-id="e336e-123">Vous pouvez également utiliser [Set jar](/azure/databricks/jobs#--create-a-job) dans votre espace de travail Databricks pour envoyer des travaux .net pour Apache Spark à Databricks.</span><span class="sxs-lookup"><span data-stu-id="e336e-123">Alternatively, you can use [Set Jar](/azure/databricks/jobs#--create-a-job) in your Databricks workspace to submit .NET for Apache Spark jobs to Databricks.</span></span> <span data-ttu-id="e336e-124">*Set jar* autorise l’envoi de travaux à un cluster actif existant.</span><span class="sxs-lookup"><span data-stu-id="e336e-124">*Set Jar* allows job submission to an existing active cluster.</span></span>

### <a name="one-time-setup"></a><span data-ttu-id="e336e-125">Installation unique</span><span class="sxs-lookup"><span data-stu-id="e336e-125">One-time setup</span></span>

1. <span data-ttu-id="e336e-126">Accédez à votre cluster Databricks et sélectionnez **travaux** dans le menu de gauche, puis **Set jar**.</span><span class="sxs-lookup"><span data-stu-id="e336e-126">Navigate to your Databricks cluster and select **Jobs** from the left-side menu, followed by **Set JAR**.</span></span>

2. <span data-ttu-id="e336e-127">Téléchargez le approprié `microsoft-spark-<spark-version>-<spark-dotnet-version>.jar` .</span><span class="sxs-lookup"><span data-stu-id="e336e-127">Upload the appropriate `microsoft-spark-<spark-version>-<spark-dotnet-version>.jar`.</span></span>

3. <span data-ttu-id="e336e-128">Modifiez les paramètres suivants pour inclure le nom correct de l’exécutable que vous avez publié à la place de `<your-app-name>` :</span><span class="sxs-lookup"><span data-stu-id="e336e-128">Modify the following parameters to include the correct name for the executable that you published in place of `<your-app-name>`:</span></span>

    ```
    Main Class: org.apache.spark.deploy.dotnet.DotnetRunner
    Arguments /dbfs/apps/<your-app-name>.zip <your-app-name>
    ```

4. <span data-ttu-id="e336e-129">Configurez le cluster pour qu’il pointe vers un cluster existant pour lequel vous avez déjà défini le script init.</span><span class="sxs-lookup"><span data-stu-id="e336e-129">Configure the cluster to point to an existing cluster for which you have already set the init script.</span></span>

### <a name="publish-and-run-your-app"></a><span data-ttu-id="e336e-130">Publier et exécuter votre application</span><span class="sxs-lookup"><span data-stu-id="e336e-130">Publish and run your app</span></span>

1. <span data-ttu-id="e336e-131">Vérifiez que vous avez publié votre application et que le code de votre application n’utilise pas `SparkSession.Stop()` .</span><span class="sxs-lookup"><span data-stu-id="e336e-131">Ensure you have published your app, and that your application code does not use `SparkSession.Stop()`.</span></span>

2. <span data-ttu-id="e336e-132">Utilisez [DATABRICKS CLI](/azure/databricks/dev-tools/databricks-cli) pour charger votre application sur votre cluster Databricks.</span><span class="sxs-lookup"><span data-stu-id="e336e-132">Use [Databricks CLI](/azure/databricks/dev-tools/databricks-cli) to upload your application to your Databricks cluster.</span></span> <span data-ttu-id="e336e-133">Par exemple, utilisez la commande suivante pour charger votre application publiée sur votre cluster :</span><span class="sxs-lookup"><span data-stu-id="e336e-133">For example, use the following command to upload your published app to your cluster:</span></span>

    ```console
    cd <path-to-your-app-publish-directory>
    databricks fs cp <your-app-name>.zip dbfs:/apps/<your-app-name>.zip
    ```

3. <span data-ttu-id="e336e-134">Si vous avez des fonctions définies par l’utilisateur dans votre application, les assemblys d’application, tels que les dll qui contiennent des fonctions définies par l’utilisateur ainsi que leurs dépendances, doivent être placés dans le répertoire de travail de chaque *Microsoft. Spark. Worker*.</span><span class="sxs-lookup"><span data-stu-id="e336e-134">If you have any user-defined functions in your app, the app assemblies, such as DLLs that contain user-defined functions along with their dependencies, need to be placed in the working directory of each *Microsoft.Spark.Worker*.</span></span>

    <span data-ttu-id="e336e-135">Chargez vos assemblys d’application sur votre cluster Databricks :</span><span class="sxs-lookup"><span data-stu-id="e336e-135">Upload your application assemblies to your Databricks cluster:</span></span>

    ```console
    cd <path-to-your-app-publish-directory>
    databricks fs cp <assembly>.dll dbfs:/apps/dependencies
    ```

    <span data-ttu-id="e336e-136">Supprimez les marques de commentaire et modifiez la section dépendances de l’application dans [DB-init.sh](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh) pour pointer vers le chemin de vos dépendances d’application.</span><span class="sxs-lookup"><span data-stu-id="e336e-136">Uncomment and modify the app dependencies section in [db-init.sh](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh) to point to your app dependencies path.</span></span> <span data-ttu-id="e336e-137">Ensuite, chargez le *DB-init.sh* mis à jour sur votre cluster :</span><span class="sxs-lookup"><span data-stu-id="e336e-137">Then, upload the updated *db-init.sh* to your cluster:</span></span>

    ```console
    cd <path-to-db-init-and-install-worker>
    databricks fs cp db-init.sh dbfs:/spark-dotnet/db-init.sh
    ```

4. <span data-ttu-id="e336e-138">Accédez à **cluster Databricks > travaux > [job-name] > exécuter maintenant** pour exécuter votre travail.</span><span class="sxs-lookup"><span data-stu-id="e336e-138">Navigate to **Databricks cluster > Jobs > [Job-name] > Run Now** to run your job.</span></span>

## <a name="next-steps"></a><span data-ttu-id="e336e-139">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="e336e-139">Next steps</span></span>

* [<span data-ttu-id="e336e-140">Bien démarrer avec .NET pour Apache Spark</span><span class="sxs-lookup"><span data-stu-id="e336e-140">Get started with .NET for Apache Spark</span></span>](../tutorials/get-started.md)
* [<span data-ttu-id="e336e-141">Déployer une application .NET pour Apache Spark sur Databricks</span><span class="sxs-lookup"><span data-stu-id="e336e-141">Deploy a .NET for Apache Spark application to Databricks</span></span>](../tutorials/databricks-deployment.md)
* [<span data-ttu-id="e336e-142">Documentation Azure Databricks</span><span class="sxs-lookup"><span data-stu-id="e336e-142">Azure Databricks Documentation</span></span>](/azure/azure-databricks/)
