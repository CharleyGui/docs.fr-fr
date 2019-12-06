---
title: Envoyer un travail .NET pour Apache Spark à Databricks
description: Découvrez comment soumettre un travail .NET pour Apache Spark à Databricks à l’aide de Spark-Submit et Set jar.
ms.date: 12/05/2019
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 9cd3d40871d4600660957ec268f192ef3e045845
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74838350"
---
# <a name="submit-a-net-for-apache-spark-job-to-databricks"></a><span data-ttu-id="a3712-103">Envoyer un travail .NET pour Apache Spark à Databricks</span><span class="sxs-lookup"><span data-stu-id="a3712-103">Submit a .NET for Apache Spark job to Databricks</span></span>

<span data-ttu-id="a3712-104">Il existe deux façons de déployer votre .NET pour Apache Spark travail sur Databricks : `spark-submit` et Set jar.</span><span class="sxs-lookup"><span data-stu-id="a3712-104">There are two ways to deploy your .NET for Apache Spark job to Databricks: `spark-submit` and Set Jar.</span></span> 

## <a name="deploy-using-spark-submit"></a><span data-ttu-id="a3712-105">Déployer à l’aide de Spark-Submit</span><span class="sxs-lookup"><span data-stu-id="a3712-105">Deploy using spark-submit</span></span>

<span data-ttu-id="a3712-106">Vous pouvez utiliser la commande [Spark-Submit](https://spark.apache.org/docs/latest/submitting-applications.html) pour envoyer des travaux .net pour Apache Spark à Databricks.</span><span class="sxs-lookup"><span data-stu-id="a3712-106">You can use the [spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html) command to submit .NET for Apache Spark jobs to Databricks.</span></span> <span data-ttu-id="a3712-107">`spark-submit` autorise l’envoi uniquement à un cluster qui est créé à la demande.</span><span class="sxs-lookup"><span data-stu-id="a3712-107">`spark-submit` allows submission only to a cluster that gets created on-demand.</span></span>

1. <span data-ttu-id="a3712-108">Accédez à votre espace de travail Databricks et créez un travail.</span><span class="sxs-lookup"><span data-stu-id="a3712-108">Navigate to your Databricks Workspace and create a job.</span></span> <span data-ttu-id="a3712-109">Choisissez un titre pour votre travail, puis sélectionnez **configurer Spark-Submit**.</span><span class="sxs-lookup"><span data-stu-id="a3712-109">Choose a title for your job, and then select **Configure spark-submit**.</span></span> <span data-ttu-id="a3712-110">Collez les paramètres suivants dans la configuration du travail, puis sélectionnez **confirmer**.</span><span class="sxs-lookup"><span data-stu-id="a3712-110">Paste the following parameters in the job configuration, then select **Confirm**.</span></span>

    ```
    ["--files","/dbfs/<path-to>/<app assembly/file to deploy to worker>","--class","org.apache.spark.deploy.dotnet.DotnetRunner","/dbfs/<path-to>/microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar","/dbfs/<path-to>/<app name>.zip","<app bin name>","app arg1","app arg2"]
    ```

    > [!NOTE]
    > <span data-ttu-id="a3712-111">Mettez à jour le contenu du paramètre ci-dessus en fonction de vos fichiers et de votre configuration spécifiques.</span><span class="sxs-lookup"><span data-stu-id="a3712-111">Update the contents of the above parameter based on your specific files and configuration.</span></span> <span data-ttu-id="a3712-112">Par exemple, référencez la version du fichier jar Microsoft. Spark que vous avez chargée sur DBFS et utilisez le nom approprié de votre application et le fichier zip de l’application publiée.</span><span class="sxs-lookup"><span data-stu-id="a3712-112">For instance, reference the version of the Microsoft.Spark jar file that you uploaded to DBFS, and use the appropriate name of your app and published app zip file.</span></span>

2. <span data-ttu-id="a3712-113">Accédez à votre travail et sélectionnez **modifier** pour configurer le cluster de votre travail.</span><span class="sxs-lookup"><span data-stu-id="a3712-113">Navigate to your job and select **Edit** to configure your job's cluster.</span></span> <span data-ttu-id="a3712-114">Définissez la version de Databricks Runtime en fonction de la version de Apache Spark que vous souhaitez utiliser dans votre déploiement.</span><span class="sxs-lookup"><span data-stu-id="a3712-114">Set the Databricks Runtime Version based on the version of Apache Spark you wish to use in your deployment.</span></span> <span data-ttu-id="a3712-115">Sélectionnez ensuite les **Options avancées > les scripts init**et définissez le chemin d’accès du script init comme `dbfs:/spark-dotnet/db-init.sh`.</span><span class="sxs-lookup"><span data-stu-id="a3712-115">Then select **Advanced Options > Init Scripts**, and set Init Script Path as `dbfs:/spark-dotnet/db-init.sh`.</span></span> <span data-ttu-id="a3712-116">Sélectionnez **confirmer** pour confirmer vos paramètres de cluster.</span><span class="sxs-lookup"><span data-stu-id="a3712-116">Select **Confirm** to confirm your cluster settings.</span></span>

3. <span data-ttu-id="a3712-117">Accédez à votre travail et sélectionnez **Exécuter maintenant** pour exécuter votre travail sur le cluster Spark que vous venez de configurer.</span><span class="sxs-lookup"><span data-stu-id="a3712-117">Navigate to your job and select **Run Now** to run your job on your newly configured Spark cluster.</span></span> <span data-ttu-id="a3712-118">La création du cluster du travail prend quelques minutes.</span><span class="sxs-lookup"><span data-stu-id="a3712-118">It takes a few minutes for the job's cluster to be created.</span></span> <span data-ttu-id="a3712-119">Une fois créé, votre travail est envoyé.</span><span class="sxs-lookup"><span data-stu-id="a3712-119">Once it is created, your job will be submitted.</span></span> <span data-ttu-id="a3712-120">Vous pouvez afficher la sortie en sélectionnant **clusters** dans le menu de gauche de votre espace de travail Databricks, puis sélectionner **journaux du pilote**.</span><span class="sxs-lookup"><span data-stu-id="a3712-120">You can view the output by selecting **Clusters** from the left menu of your Databricks workspace, then select **Driver Logs**.</span></span>

## <a name="deploy-using-set-jar"></a><span data-ttu-id="a3712-121">Déployer à l’aide de Set jar</span><span class="sxs-lookup"><span data-stu-id="a3712-121">Deploy using Set Jar</span></span>

<span data-ttu-id="a3712-122">Vous pouvez également utiliser [Set jar](https://docs.microsoft.com/azure/databricks/jobs#--create-a-job) dans votre espace de travail Databricks pour envoyer des travaux .net pour Apache Spark à Databricks.</span><span class="sxs-lookup"><span data-stu-id="a3712-122">Alternatively, you can use [Set Jar](https://docs.microsoft.com/azure/databricks/jobs#--create-a-job) in your Databricks workspace to submit .NET for Apache Spark jobs to Databricks.</span></span> <span data-ttu-id="a3712-123">*Set jar* autorise l’envoi de travaux à un cluster actif existant.</span><span class="sxs-lookup"><span data-stu-id="a3712-123">*Set Jar* allows job submission to an existing active cluster.</span></span>

### <a name="one-time-setup"></a><span data-ttu-id="a3712-124">Installation unique</span><span class="sxs-lookup"><span data-stu-id="a3712-124">One-time setup</span></span>

1. <span data-ttu-id="a3712-125">Accédez à votre cluster Databricks et sélectionnez **travaux** dans le menu de gauche, puis **Set jar**.</span><span class="sxs-lookup"><span data-stu-id="a3712-125">Navigate to your Databricks cluster and select **Jobs** from the left-side menu, followed by **Set JAR**.</span></span>

2. <span data-ttu-id="a3712-126">Téléchargez le `microsoft-spark-<spark-version>-<spark-dotnet-version>.jar`approprié.</span><span class="sxs-lookup"><span data-stu-id="a3712-126">Upload the appropriate `microsoft-spark-<spark-version>-<spark-dotnet-version>.jar`.</span></span>

3. <span data-ttu-id="a3712-127">Modifiez les paramètres suivants pour inclure le nom correct de l’exécutable que vous avez publié à la place de `<your-app-name>`:</span><span class="sxs-lookup"><span data-stu-id="a3712-127">Modify the following parameters to include the correct name for the executable that you published in place of `<your-app-name>`:</span></span>

    ```
    Main Class: org.apache.spark.deploy.dotnet.DotnetRunner
    Arguments /dbfs/apps/<your-app-name>.zip <your-app-name>
    ```

4. <span data-ttu-id="a3712-128">Configurez le cluster pour qu’il pointe vers un cluster existant pour lequel vous avez déjà défini le script init.</span><span class="sxs-lookup"><span data-stu-id="a3712-128">Configure the cluster to point to an existing cluster for which you have already set the init script.</span></span>

### <a name="publish-and-run-your-app"></a><span data-ttu-id="a3712-129">Publier et exécuter votre application</span><span class="sxs-lookup"><span data-stu-id="a3712-129">Publish and run your app</span></span>

1. <span data-ttu-id="a3712-130">Vérifiez que vous avez publié votre application et que votre code d’application n’utilise pas `SparkSession.Stop()`.</span><span class="sxs-lookup"><span data-stu-id="a3712-130">Ensure you have published your app, and that your application code does not use `SparkSession.Stop()`.</span></span>

2. <span data-ttu-id="a3712-131">Utilisez [DATABRICKS CLI](https://docs.microsoft.com/azure/databricks/dev-tools/databricks-cli) pour charger votre application sur votre cluster Databricks.</span><span class="sxs-lookup"><span data-stu-id="a3712-131">Use [Databricks CLI](https://docs.microsoft.com/azure/databricks/dev-tools/databricks-cli) to upload your application to your Databricks cluster.</span></span> <span data-ttu-id="a3712-132">Par exemple, utilisez la commande suivante pour charger votre application publiée sur votre cluster :</span><span class="sxs-lookup"><span data-stu-id="a3712-132">For example, use the following command to upload your published app to your cluster:</span></span>

    ```console
    cd <path-to-your-app-publish-directory>
    databricks fs cp <your-app-name>.zip dbfs:/apps/<your-app-name>.zip
    ```

3. <span data-ttu-id="a3712-133">Si vous avez des fonctions définies par l’utilisateur dans votre application, les assemblys d’application, tels que les dll qui contiennent des fonctions définies par l’utilisateur ainsi que leurs dépendances, doivent être placés dans le répertoire de travail de chaque *Microsoft. Spark. Worker*.</span><span class="sxs-lookup"><span data-stu-id="a3712-133">If you have any user-defined functions in your app, the app assemblies, such as DLLs that contain user-defined functions along with their dependencies, need to be placed in the working directory of each *Microsoft.Spark.Worker*.</span></span>

    <span data-ttu-id="a3712-134">Chargez vos assemblys d’application sur votre cluster Databricks :</span><span class="sxs-lookup"><span data-stu-id="a3712-134">Upload your application assemblies to your Databricks cluster:</span></span>

    ```console
    cd <path-to-your-app-publish-directory>
    databricks fs cp <assembly>.dll dbfs:/apps/dependencies
    ```

    <span data-ttu-id="a3712-135">Supprimez les marques de commentaire et modifiez la section dépendances de l’application dans [DB-init.sh](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh) pour pointer vers le chemin de vos dépendances d’application.</span><span class="sxs-lookup"><span data-stu-id="a3712-135">Uncomment and modify the app dependencies section in [db-init.sh](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh) to point to your app dependencies path.</span></span> <span data-ttu-id="a3712-136">Ensuite, chargez le *DB-init.sh* mis à jour sur votre cluster :</span><span class="sxs-lookup"><span data-stu-id="a3712-136">Then, upload the updated *db-init.sh* to your cluster:</span></span>

    ```console
    cd <path-to-db-init-and-install-worker>
    databricks fs cp db-init.sh dbfs:/spark-dotnet/db-init.sh
    ```

4. <span data-ttu-id="a3712-137">Accédez à **cluster Databricks > travaux > [job-name] > exécuter maintenant** pour exécuter votre travail.</span><span class="sxs-lookup"><span data-stu-id="a3712-137">Navigate to **Databricks cluster > Jobs > [Job-name] > Run Now** to run your job.</span></span>

## <a name="next-steps"></a><span data-ttu-id="a3712-138">Étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="a3712-138">Next steps</span></span>

* [<span data-ttu-id="a3712-139">Bien démarrer avec .NET pour Apache Spark</span><span class="sxs-lookup"><span data-stu-id="a3712-139">Get started with .NET for Apache Spark</span></span>](../tutorials/get-started.md)
* [<span data-ttu-id="a3712-140">Déployer une application .NET pour Apache Spark sur Databricks</span><span class="sxs-lookup"><span data-stu-id="a3712-140">Deploy a .NET for Apache Spark application to Databricks</span></span>](../tutorials/databricks-deployment.md)
* [<span data-ttu-id="a3712-141">Documentation Azure Databricks</span><span class="sxs-lookup"><span data-stu-id="a3712-141">Azure Databricks Documentation</span></span>](https://docs.microsoft.com/azure/azure-databricks/)
