---
title: Soumettez un .NET pour Apache Spark à Databricks
description: Apprenez à soumettre un .NET pour apache Spark emploi à Databricks en utilisant spark-submit et Set Jar.
ms.date: 12/05/2019
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 65976f9095ecef66e0538c398492033c612c1430
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79187606"
---
# <a name="submit-a-net-for-apache-spark-job-to-databricks"></a><span data-ttu-id="fa835-103">Soumettez un .NET pour Apache Spark à Databricks</span><span class="sxs-lookup"><span data-stu-id="fa835-103">Submit a .NET for Apache Spark job to Databricks</span></span>

<span data-ttu-id="fa835-104">Il existe deux façons de déployer votre .NET pour Apache Spark emploi à Databricks: `spark-submit` et Set Jar.</span><span class="sxs-lookup"><span data-stu-id="fa835-104">There are two ways to deploy your .NET for Apache Spark job to Databricks: `spark-submit` and Set Jar.</span></span>

## <a name="deploy-using-spark-submit"></a><span data-ttu-id="fa835-105">Déploiement à l’aide d’étincelles-soumettre</span><span class="sxs-lookup"><span data-stu-id="fa835-105">Deploy using spark-submit</span></span>

<span data-ttu-id="fa835-106">Vous pouvez utiliser la commande [spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html) pour soumettre .NET pour les emplois Apache Spark à Databricks.</span><span class="sxs-lookup"><span data-stu-id="fa835-106">You can use the [spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html) command to submit .NET for Apache Spark jobs to Databricks.</span></span> <span data-ttu-id="fa835-107">`spark-submit`ne permet la soumission qu’à un cluster qui est créé à la demande.</span><span class="sxs-lookup"><span data-stu-id="fa835-107">`spark-submit` allows submission only to a cluster that gets created on-demand.</span></span>

1. <span data-ttu-id="fa835-108">Naviguez vers votre espace de travail Databricks et créez un emploi.</span><span class="sxs-lookup"><span data-stu-id="fa835-108">Navigate to your Databricks Workspace and create a job.</span></span> <span data-ttu-id="fa835-109">Choisissez un titre pour votre travail, puis **sélectionnez Configurer étincelle-soumettre**.</span><span class="sxs-lookup"><span data-stu-id="fa835-109">Choose a title for your job, and then select **Configure spark-submit**.</span></span> <span data-ttu-id="fa835-110">Coller les paramètres suivants dans la configuration du travail, puis sélectionnez **Confirm**.</span><span class="sxs-lookup"><span data-stu-id="fa835-110">Paste the following parameters in the job configuration, then select **Confirm**.</span></span>

    ```
    ["--files","/dbfs/<path-to>/<app assembly/file to deploy to worker>","--class","org.apache.spark.deploy.dotnet.DotnetRunner","/dbfs/<path-to>/microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar","/dbfs/<path-to>/<app name>.zip","<app bin name>","app arg1","app arg2"]
    ```

    > [!NOTE]
    > <span data-ttu-id="fa835-111">Mettez à jour le contenu du paramètre ci-dessus en fonction de vos fichiers et configuration spécifiques.</span><span class="sxs-lookup"><span data-stu-id="fa835-111">Update the contents of the above parameter based on your specific files and configuration.</span></span> <span data-ttu-id="fa835-112">Par exemple, faites référence à la version du fichier de pot Microsoft.Spark que vous avez téléchargé sur DBFS, et utilisez le nom approprié de votre application et de votre fichier zip d’application publié.</span><span class="sxs-lookup"><span data-stu-id="fa835-112">For instance, reference the version of the Microsoft.Spark jar file that you uploaded to DBFS, and use the appropriate name of your app and published app zip file.</span></span>

2. <span data-ttu-id="fa835-113">Naviguez dans votre travail et sélectionnez **Edit** pour configurer le cluster de votre travail.</span><span class="sxs-lookup"><span data-stu-id="fa835-113">Navigate to your job and select **Edit** to configure your job's cluster.</span></span> <span data-ttu-id="fa835-114">Réglez la version Databricks Runtime en fonction de la version d’Apache Spark que vous souhaitez utiliser dans votre déploiement.</span><span class="sxs-lookup"><span data-stu-id="fa835-114">Set the Databricks Runtime Version based on the version of Apache Spark you wish to use in your deployment.</span></span> <span data-ttu-id="fa835-115">Sélectionnez ensuite **Les options avancées > scripts Init**, `dbfs:/spark-dotnet/db-init.sh`et définissez Init Script Path comme .</span><span class="sxs-lookup"><span data-stu-id="fa835-115">Then select **Advanced Options > Init Scripts**, and set Init Script Path as `dbfs:/spark-dotnet/db-init.sh`.</span></span> <span data-ttu-id="fa835-116">Sélectionnez **Confirmez** pour confirmer les paramètres de votre cluster.</span><span class="sxs-lookup"><span data-stu-id="fa835-116">Select **Confirm** to confirm your cluster settings.</span></span>

3. <span data-ttu-id="fa835-117">Naviguez dans votre travail et sélectionnez **Run Now** pour exécuter votre travail sur votre cluster Spark nouvellement configuré.</span><span class="sxs-lookup"><span data-stu-id="fa835-117">Navigate to your job and select **Run Now** to run your job on your newly configured Spark cluster.</span></span> <span data-ttu-id="fa835-118">Il faut quelques minutes pour que le cluster du travail soit créé.</span><span class="sxs-lookup"><span data-stu-id="fa835-118">It takes a few minutes for the job's cluster to be created.</span></span> <span data-ttu-id="fa835-119">Une fois qu’il sera créé, votre travail sera soumis.</span><span class="sxs-lookup"><span data-stu-id="fa835-119">Once it is created, your job will be submitted.</span></span> <span data-ttu-id="fa835-120">Vous pouvez afficher la sortie en sélectionnant des **clusters** à partir du menu gauche de votre espace de travail Databricks, puis sélectionnez **les journaux de pilote**.</span><span class="sxs-lookup"><span data-stu-id="fa835-120">You can view the output by selecting **Clusters** from the left menu of your Databricks workspace, then select **Driver Logs**.</span></span>

## <a name="deploy-using-set-jar"></a><span data-ttu-id="fa835-121">Déployer à l’aide de Set Jar</span><span class="sxs-lookup"><span data-stu-id="fa835-121">Deploy using Set Jar</span></span>

<span data-ttu-id="fa835-122">Alternativement, vous pouvez utiliser [Set Jar](https://docs.microsoft.com/azure/databricks/jobs#--create-a-job) dans votre espace de travail Databricks pour soumettre .NET pour apache Spark emplois à Databricks.</span><span class="sxs-lookup"><span data-stu-id="fa835-122">Alternatively, you can use [Set Jar](https://docs.microsoft.com/azure/databricks/jobs#--create-a-job) in your Databricks workspace to submit .NET for Apache Spark jobs to Databricks.</span></span> <span data-ttu-id="fa835-123">*Set Jar* permet la soumission d’emploi à un cluster actif existant.</span><span class="sxs-lookup"><span data-stu-id="fa835-123">*Set Jar* allows job submission to an existing active cluster.</span></span>

### <a name="one-time-setup"></a><span data-ttu-id="fa835-124">Installation unique</span><span class="sxs-lookup"><span data-stu-id="fa835-124">One-time setup</span></span>

1. <span data-ttu-id="fa835-125">Naviguez vers votre cluster Databricks et sélectionnez **des travaux** dans le menu gauche, suivi de **Set JAR**.</span><span class="sxs-lookup"><span data-stu-id="fa835-125">Navigate to your Databricks cluster and select **Jobs** from the left-side menu, followed by **Set JAR**.</span></span>

2. <span data-ttu-id="fa835-126">Téléchargez `microsoft-spark-<spark-version>-<spark-dotnet-version>.jar`le approprié .</span><span class="sxs-lookup"><span data-stu-id="fa835-126">Upload the appropriate `microsoft-spark-<spark-version>-<spark-dotnet-version>.jar`.</span></span>

3. <span data-ttu-id="fa835-127">Modifier les paramètres suivants pour inclure le nom correct pour `<your-app-name>`l’exécutable que vous avez publié à la place de :</span><span class="sxs-lookup"><span data-stu-id="fa835-127">Modify the following parameters to include the correct name for the executable that you published in place of `<your-app-name>`:</span></span>

    ```
    Main Class: org.apache.spark.deploy.dotnet.DotnetRunner
    Arguments /dbfs/apps/<your-app-name>.zip <your-app-name>
    ```

4. <span data-ttu-id="fa835-128">Configurez le cluster pour indiquer un cluster existant pour lequel vous avez déjà défini le script init.</span><span class="sxs-lookup"><span data-stu-id="fa835-128">Configure the cluster to point to an existing cluster for which you have already set the init script.</span></span>

### <a name="publish-and-run-your-app"></a><span data-ttu-id="fa835-129">Publier et exécuter votre application</span><span class="sxs-lookup"><span data-stu-id="fa835-129">Publish and run your app</span></span>

1. <span data-ttu-id="fa835-130">Assurez-vous d’avoir publié votre application et `SparkSession.Stop()`que votre code d’application n’utilise pas .</span><span class="sxs-lookup"><span data-stu-id="fa835-130">Ensure you have published your app, and that your application code does not use `SparkSession.Stop()`.</span></span>

2. <span data-ttu-id="fa835-131">Utilisez [Databricks CLI](https://docs.microsoft.com/azure/databricks/dev-tools/databricks-cli) pour télécharger votre application sur votre cluster Databricks.</span><span class="sxs-lookup"><span data-stu-id="fa835-131">Use [Databricks CLI](https://docs.microsoft.com/azure/databricks/dev-tools/databricks-cli) to upload your application to your Databricks cluster.</span></span> <span data-ttu-id="fa835-132">Par exemple, utilisez la commande suivante pour télécharger votre application publiée sur votre cluster :</span><span class="sxs-lookup"><span data-stu-id="fa835-132">For example, use the following command to upload your published app to your cluster:</span></span>

    ```console
    cd <path-to-your-app-publish-directory>
    databricks fs cp <your-app-name>.zip dbfs:/apps/<your-app-name>.zip
    ```

3. <span data-ttu-id="fa835-133">Si vous avez des fonctions définies par l’utilisateur dans votre application, les assemblages d’applications, tels que les DLL qui contiennent des fonctions définies par l’utilisateur avec leurs dépendances, doivent être placés dans l’annuaire de travail de chaque *Microsoft.Spark.Worker*.</span><span class="sxs-lookup"><span data-stu-id="fa835-133">If you have any user-defined functions in your app, the app assemblies, such as DLLs that contain user-defined functions along with their dependencies, need to be placed in the working directory of each *Microsoft.Spark.Worker*.</span></span>

    <span data-ttu-id="fa835-134">Téléchargez vos assemblages d’applications dans votre cluster Databricks :</span><span class="sxs-lookup"><span data-stu-id="fa835-134">Upload your application assemblies to your Databricks cluster:</span></span>

    ```console
    cd <path-to-your-app-publish-directory>
    databricks fs cp <assembly>.dll dbfs:/apps/dependencies
    ```

    <span data-ttu-id="fa835-135">Désengagement et modifier la section dépendances de l’application dans [db-init.sh](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh) pour indiquer votre chemin de dépendance app.</span><span class="sxs-lookup"><span data-stu-id="fa835-135">Uncomment and modify the app dependencies section in [db-init.sh](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh) to point to your app dependencies path.</span></span> <span data-ttu-id="fa835-136">Ensuite, téléchargez les *db-init.sh* mises à jour sur votre cluster :</span><span class="sxs-lookup"><span data-stu-id="fa835-136">Then, upload the updated *db-init.sh* to your cluster:</span></span>

    ```console
    cd <path-to-db-init-and-install-worker>
    databricks fs cp db-init.sh dbfs:/spark-dotnet/db-init.sh
    ```

4. <span data-ttu-id="fa835-137">Naviguez vers **le cluster Databricks > Jobs > [nom d’emploi] > Exécuter maintenant** pour exécuter votre travail.</span><span class="sxs-lookup"><span data-stu-id="fa835-137">Navigate to **Databricks cluster > Jobs > [Job-name] > Run Now** to run your job.</span></span>

## <a name="next-steps"></a><span data-ttu-id="fa835-138">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="fa835-138">Next steps</span></span>

* [<span data-ttu-id="fa835-139">Bien démarrer avec .NET pour Apache Spark</span><span class="sxs-lookup"><span data-stu-id="fa835-139">Get started with .NET for Apache Spark</span></span>](../tutorials/get-started.md)
* [<span data-ttu-id="fa835-140">Déployer une application .NET pour Apache Spark sur Databricks</span><span class="sxs-lookup"><span data-stu-id="fa835-140">Deploy a .NET for Apache Spark application to Databricks</span></span>](../tutorials/databricks-deployment.md)
* [<span data-ttu-id="fa835-141">Azure Databricks Documentation</span><span class="sxs-lookup"><span data-stu-id="fa835-141">Azure Databricks Documentation</span></span>](https://docs.microsoft.com/azure/azure-databricks/)
