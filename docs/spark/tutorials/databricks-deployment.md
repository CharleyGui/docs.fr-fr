---
title: Déployer une application .NET pour Apache Spark sur Databricks
description: Découvrez comment déployer une application .NET pour Apache Spark sur Databricks.
ms.date: 01/23/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: c5308530831fa288bf637849c1342f51769c3ad4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "77503965"
---
# <a name="tutorial-deploy-a-net-for-apache-spark-application-to-databricks"></a><span data-ttu-id="6d41a-103">Tutorial: Déployer une application .NET pour Apache Spark à Databricks</span><span class="sxs-lookup"><span data-stu-id="6d41a-103">Tutorial: Deploy a .NET for Apache Spark application to Databricks</span></span>

<span data-ttu-id="6d41a-104">Ce tutoriel vous apprend à déployer votre application dans le cloud via Azure Databricks, une plate-forme d’analyse basée sur Apache Spark avec configuration en un seul clic, flux de travail simplifiés et espace de travail interactif qui permet la collaboration.</span><span class="sxs-lookup"><span data-stu-id="6d41a-104">This tutorial teaches you how to deploy your app to the cloud through Azure Databricks, an Apache Spark-based analytics platform with one-click setup, streamlined workflows, and interactive workspace that enables collaboration.</span></span>

<span data-ttu-id="6d41a-105">Dans ce tutoriel, vous allez apprendre à :</span><span class="sxs-lookup"><span data-stu-id="6d41a-105">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="6d41a-106">Créer un espace de travail Azure Databricks.</span><span class="sxs-lookup"><span data-stu-id="6d41a-106">Create an Azure Databricks workspace.</span></span>
> - <span data-ttu-id="6d41a-107">Publiez votre application .NET pour Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="6d41a-107">Publish your .NET for Apache Spark app.</span></span>
> - <span data-ttu-id="6d41a-108">Créez un emploi Spark et un cluster Spark.</span><span class="sxs-lookup"><span data-stu-id="6d41a-108">Create a Spark job and Spark cluster.</span></span>
> - <span data-ttu-id="6d41a-109">Exécutez votre application sur le cluster Spark.</span><span class="sxs-lookup"><span data-stu-id="6d41a-109">Run your app on the Spark cluster.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="6d41a-110">Conditions préalables requises</span><span class="sxs-lookup"><span data-stu-id="6d41a-110">Prerequisites</span></span>

<span data-ttu-id="6d41a-111">Avant de commencer, faites les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="6d41a-111">Before you start, do the following tasks:</span></span>

* <span data-ttu-id="6d41a-112">Si vous n’avez pas de compte Azure, créez un [compte gratuit](https://azure.microsoft.com/free/).</span><span class="sxs-lookup"><span data-stu-id="6d41a-112">If you don't have an Azure account, create a [free account](https://azure.microsoft.com/free/).</span></span>
* <span data-ttu-id="6d41a-113">Connectez-vous au [portail Azure](https://portal.azure.com/).</span><span class="sxs-lookup"><span data-stu-id="6d41a-113">Sign in to the [Azure portal](https://portal.azure.com/).</span></span>
* <span data-ttu-id="6d41a-114">Complétez le [.NET pour Apache Spark - Get Started in 10-Minutes](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) tutorial.</span><span class="sxs-lookup"><span data-stu-id="6d41a-114">Complete the [.NET for Apache Spark - Get Started in 10-Minutes](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) tutorial.</span></span>

## <a name="create-an-azure-databricks-workspace"></a><span data-ttu-id="6d41a-115">Créer un espace de travail Azure Databricks</span><span class="sxs-lookup"><span data-stu-id="6d41a-115">Create an Azure Databricks workspace</span></span>

> [!Note]
> <span data-ttu-id="6d41a-116">Ce didacticiel ne peut pas être suivi avec un **abonnement d’essai gratuit Azure**.</span><span class="sxs-lookup"><span data-stu-id="6d41a-116">This tutorial cannot be carried out using **Azure Free Trial Subscription**.</span></span>
> <span data-ttu-id="6d41a-117">Si vous avez un compte gratuit, accédez à votre profil et modifiez votre abonnement sur **Paiement à l’utilisation**.</span><span class="sxs-lookup"><span data-stu-id="6d41a-117">If you have a free account, go to your profile and change your subscription to **pay-as-you-go**.</span></span> <span data-ttu-id="6d41a-118">Pour plus d’informations, consultez la page [Compte Azure gratuit](https://azure.microsoft.com/free/).</span><span class="sxs-lookup"><span data-stu-id="6d41a-118">For more information, see [Azure free account](https://azure.microsoft.com/free/).</span></span> <span data-ttu-id="6d41a-119">Ensuite, [supprimez la limite de dépense](https://docs.microsoft.com/azure/billing/billing-spending-limit#why-you-might-want-to-remove-the-spending-limit), et [demandez une augmentation du quota](https://docs.microsoft.com/azure/azure-supportability/resource-manager-core-quotas-request) pour les processeurs virtuels dans votre région.</span><span class="sxs-lookup"><span data-stu-id="6d41a-119">Then, [remove the spending limit](https://docs.microsoft.com/azure/billing/billing-spending-limit#why-you-might-want-to-remove-the-spending-limit), and [request a quota increase](https://docs.microsoft.com/azure/azure-supportability/resource-manager-core-quotas-request) for vCPUs in your region.</span></span> <span data-ttu-id="6d41a-120">Lorsque vous créez votre espace de travail Azure Databricks, vous pouvez sélectionner le tarif **Version d’évaluation (Premium - 14 jours de DBU offerts)** pour donner à l’accès de l’espace de travail un accès gratuit aux DBU d’Azure Databricks pendant 14 jours.</span><span class="sxs-lookup"><span data-stu-id="6d41a-120">When you create your Azure Databricks workspace, you can select the **Trial (Premium - 14-Days Free DBUs)** pricing tier to give the workspace access to free Premium Azure Databricks DBUs for 14 days.</span></span>

<span data-ttu-id="6d41a-121">Dans cette section, vous créez un espace de travail Azure Databricks en utilisant le portail Azure.</span><span class="sxs-lookup"><span data-stu-id="6d41a-121">In this section, you create an Azure Databricks workspace using the Azure portal.</span></span>

1. <span data-ttu-id="6d41a-122">Dans le portail Azure, sélectionnez **Créer une ressource** > **Analytics** > **Azure Databricks**.</span><span class="sxs-lookup"><span data-stu-id="6d41a-122">In the Azure portal, select **Create a resource** > **Analytics** > **Azure Databricks**.</span></span>

   ![Créer une ressource Azure Databricks dans le portail Azure](./media/databricks-deployment/create-databricks-resource.png)

2. <span data-ttu-id="6d41a-124">Sous **Service Azure Databricks**, renseignez les valeurs pour créer un espace de travail Databricks.</span><span class="sxs-lookup"><span data-stu-id="6d41a-124">Under **Azure Databricks Service**, provide the values to create a Databricks workspace.</span></span>

    |<span data-ttu-id="6d41a-125">Propriété</span><span class="sxs-lookup"><span data-stu-id="6d41a-125">Property</span></span>  |<span data-ttu-id="6d41a-126">Description</span><span class="sxs-lookup"><span data-stu-id="6d41a-126">Description</span></span>  |
    |---------|---------|
    |<span data-ttu-id="6d41a-127">**Nom de l’espace de travail**</span><span class="sxs-lookup"><span data-stu-id="6d41a-127">**Workspace name**</span></span>     | <span data-ttu-id="6d41a-128">Fournissez un nom pour votre espace de travail Databricks.</span><span class="sxs-lookup"><span data-stu-id="6d41a-128">Provide a name for your Databricks workspace.</span></span>        |
    |<span data-ttu-id="6d41a-129">**Abonnement**</span><span class="sxs-lookup"><span data-stu-id="6d41a-129">**Subscription**</span></span>     | <span data-ttu-id="6d41a-130">Sélectionnez votre abonnement Azure dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="6d41a-130">From the drop-down, select your Azure subscription.</span></span>        |
    |<span data-ttu-id="6d41a-131">**Groupe de ressources**</span><span class="sxs-lookup"><span data-stu-id="6d41a-131">**Resource group**</span></span>     | <span data-ttu-id="6d41a-132">Indiquez si vous souhaitez créer un groupe de ressources Azure ou utiliser un groupe existant.</span><span class="sxs-lookup"><span data-stu-id="6d41a-132">Specify whether you want to create a new resource group or use an existing one.</span></span> <span data-ttu-id="6d41a-133">Un groupe de ressources est un conteneur réunissant les ressources associées d’une solution Azure.</span><span class="sxs-lookup"><span data-stu-id="6d41a-133">A resource group is a container that holds related resources for an Azure solution.</span></span> <span data-ttu-id="6d41a-134">Pour plus d’informations, consultez [Présentation des groupes de ressources Azure](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-overview).</span><span class="sxs-lookup"><span data-stu-id="6d41a-134">For more information, see [Azure Resource Group overview](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-overview).</span></span> |
    |<span data-ttu-id="6d41a-135">**Emplacement**</span><span class="sxs-lookup"><span data-stu-id="6d41a-135">**Location**</span></span>     | <span data-ttu-id="6d41a-136">Sélectionnez votre région préférée.</span><span class="sxs-lookup"><span data-stu-id="6d41a-136">Select your preferred region.</span></span> <span data-ttu-id="6d41a-137">Pour plus d’informations sur les régions disponibles, consultez [les services Azure disponibles par région](https://azure.microsoft.com/regions/services/).</span><span class="sxs-lookup"><span data-stu-id="6d41a-137">For information about available regions, see [Azure services available by region](https://azure.microsoft.com/regions/services/).</span></span>        |
    |<span data-ttu-id="6d41a-138">**Niveau de tarification**</span><span class="sxs-lookup"><span data-stu-id="6d41a-138">**Pricing Tier**</span></span>     |  <span data-ttu-id="6d41a-139">Choisissez **Standard**, **Premium** ou **Essai**.</span><span class="sxs-lookup"><span data-stu-id="6d41a-139">Choose between **Standard**, **Premium**, or **Trial**.</span></span> <span data-ttu-id="6d41a-140">Pour plus d’informations sur ces niveaux, consultez la [page de tarification Databricks](https://azure.microsoft.com/pricing/details/databricks/).</span><span class="sxs-lookup"><span data-stu-id="6d41a-140">For more information on these tiers, see [Databricks pricing page](https://azure.microsoft.com/pricing/details/databricks/).</span></span>       |
    |<span data-ttu-id="6d41a-141">**Réseau virtuel**</span><span class="sxs-lookup"><span data-stu-id="6d41a-141">**Virtual Network**</span></span>     |   <span data-ttu-id="6d41a-142">Non </span><span class="sxs-lookup"><span data-stu-id="6d41a-142">No</span></span>       |

3. <span data-ttu-id="6d41a-143">Sélectionnez **Créer**.</span><span class="sxs-lookup"><span data-stu-id="6d41a-143">Select **Create**.</span></span> <span data-ttu-id="6d41a-144">La création de l’espace de travail dure quelques minutes.</span><span class="sxs-lookup"><span data-stu-id="6d41a-144">The workspace creation takes a few minutes.</span></span> <span data-ttu-id="6d41a-145">Pendant la création de l'espace de travail, vous pouvez consulter l'état du déploiement dans **Notifications**.</span><span class="sxs-lookup"><span data-stu-id="6d41a-145">During workspace creation, you can view the deployment status in **Notifications**.</span></span>

## <a name="install-azure-databricks-tools"></a><span data-ttu-id="6d41a-146">Installer les outils Azure Databricks</span><span class="sxs-lookup"><span data-stu-id="6d41a-146">Install Azure Databricks tools</span></span>

<span data-ttu-id="6d41a-147">Vous pouvez utiliser le **CLI Databricks** pour vous connecter aux clusters Azure Databricks et télécharger des fichiers à partir de votre machine locale.</span><span class="sxs-lookup"><span data-stu-id="6d41a-147">You can use the **Databricks CLI** to connect to Azure Databricks clusters and upload files to them from your local machine.</span></span> <span data-ttu-id="6d41a-148">Databricks regroupe les fichiers d’accès via DBFS (Databricks File System).</span><span class="sxs-lookup"><span data-stu-id="6d41a-148">Databricks clusters access files through DBFS (Databricks File System).</span></span>

1. <span data-ttu-id="6d41a-149">Le Databricks CLI nécessite Python 3.6 ou plus.</span><span class="sxs-lookup"><span data-stu-id="6d41a-149">The Databricks CLI requires Python 3.6 or above.</span></span> <span data-ttu-id="6d41a-150">Si vous avez déjà Python installé, vous pouvez sauter cette étape.</span><span class="sxs-lookup"><span data-stu-id="6d41a-150">If you already have Python installed, you can skip this step.</span></span>

   <span data-ttu-id="6d41a-151">**Pour Windows:**</span><span class="sxs-lookup"><span data-stu-id="6d41a-151">**For Windows:**</span></span>

   [<span data-ttu-id="6d41a-152">Télécharger Python pour Windows</span><span class="sxs-lookup"><span data-stu-id="6d41a-152">Download Python for Windows</span></span>](https://www.python.org/ftp/python/3.7.4/python-3.7.4.exe)

   <span data-ttu-id="6d41a-153">**Pour Linux :** Python est préinstallé sur la plupart des distributions Linux.</span><span class="sxs-lookup"><span data-stu-id="6d41a-153">**For Linux:** Python comes preinstalled on most Linux distributions.</span></span> <span data-ttu-id="6d41a-154">Exécutez la commande suivante pour voir quelle version vous avez installée :</span><span class="sxs-lookup"><span data-stu-id="6d41a-154">Run the following command to see which version you have installed:</span></span>

   ```bash
   python3 --version
   ```

2. <span data-ttu-id="6d41a-155">Utilisez pip pour installer le Databricks CLI.</span><span class="sxs-lookup"><span data-stu-id="6d41a-155">Use pip to install the Databricks CLI.</span></span> <span data-ttu-id="6d41a-156">Python 3.4 et plus tard inclure pip par défaut.</span><span class="sxs-lookup"><span data-stu-id="6d41a-156">Python 3.4 and later include pip by default.</span></span> <span data-ttu-id="6d41a-157">Utilisez pip3 pour Python 3.</span><span class="sxs-lookup"><span data-stu-id="6d41a-157">Use pip3 for Python 3.</span></span> <span data-ttu-id="6d41a-158">Exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="6d41a-158">Run the following command:</span></span>

   ```bash
   pip3 install databricks-cli
   ```

3. <span data-ttu-id="6d41a-159">Une fois que vous avez installé le Databricks CLI, `databricks`ouvrez une nouvelle invite de commande et exécutez la commande .</span><span class="sxs-lookup"><span data-stu-id="6d41a-159">Once you've installed the Databricks CLI, open a new command prompt and run the command `databricks`.</span></span> <span data-ttu-id="6d41a-160">Si vous recevez un **'databricks' n’est pas reconnu comme une erreur de commande interne ou externe,** assurez-vous d’ouvrir une nouvelle invite de commande.</span><span class="sxs-lookup"><span data-stu-id="6d41a-160">If you receive a **'databricks' is not recognized as an internal or external command error**, make sure you opened a new command prompt.</span></span>

## <a name="set-up-azure-databricks"></a><span data-ttu-id="6d41a-161">Configurez Azure Databricks</span><span class="sxs-lookup"><span data-stu-id="6d41a-161">Set up Azure Databricks</span></span>

<span data-ttu-id="6d41a-162">Maintenant que vous avez installé le Databricks CLI, vous devez configurer les détails d’authentification.</span><span class="sxs-lookup"><span data-stu-id="6d41a-162">Now that you have the Databricks CLI installed, you need to set up authentication details.</span></span>

1. <span data-ttu-id="6d41a-163">Exécuter la commande `databricks configure --token`Databricks CLI .</span><span class="sxs-lookup"><span data-stu-id="6d41a-163">Run the Databricks CLI command `databricks configure --token`.</span></span>

2. <span data-ttu-id="6d41a-164">Après avoir exécuter la commande de configuration, vous êtes invité à entrer un hôte.</span><span class="sxs-lookup"><span data-stu-id="6d41a-164">After running the configure command, you are prompted to enter a host.</span></span> <span data-ttu-id="6d41a-165">Votre URL hôte utilise le format: **https://<-Location>.azuredatabricks.net**.</span><span class="sxs-lookup"><span data-stu-id="6d41a-165">Your host URL uses the format: **https://<\Location>.azuredatabricks.net**.</span></span> <span data-ttu-id="6d41a-166">Par exemple, si vous avez sélectionné **Eastus2** lors de la **https://eastus2.azuredatabricks.net**création du service Azure Databricks, l’hôte serait .</span><span class="sxs-lookup"><span data-stu-id="6d41a-166">For instance, if you selected **eastus2** during Azure Databricks Service creation, the host would be **https://eastus2.azuredatabricks.net**.</span></span>

3. <span data-ttu-id="6d41a-167">Après avoir entré votre hôte, vous êtes invité à entrer un jeton.</span><span class="sxs-lookup"><span data-stu-id="6d41a-167">After entering your host, you are prompted to enter a token.</span></span> <span data-ttu-id="6d41a-168">Dans le portail Azure, sélectionnez **Launch Workspace** pour lancer votre espace de travail Azure Databricks.</span><span class="sxs-lookup"><span data-stu-id="6d41a-168">In the Azure portal, select **Launch Workspace** to launch your Azure Databricks workspace.</span></span>

   ![Lancement de l’espace de travail Azure Databricks](./media/databricks-deployment/launch-databricks-workspace.png)

4. <span data-ttu-id="6d41a-170">Sur la page d’accueil de votre espace de travail, sélectionnez **Paramètres utilisateur**.</span><span class="sxs-lookup"><span data-stu-id="6d41a-170">On the home page of your workspace, select **User Settings**.</span></span>

   ![Paramètres utilisateur dans l’espace de travail Azure Databricks](./media/databricks-deployment/databricks-user-settings.png)

5. <span data-ttu-id="6d41a-172">Sur la page Paramètres utilisateur, vous pouvez générer un nouveau jeton.</span><span class="sxs-lookup"><span data-stu-id="6d41a-172">On the User Settings page, you can generate a new token.</span></span> <span data-ttu-id="6d41a-173">Copiez le jeton généré et collez-le de nouveau dans votre invite de commande.</span><span class="sxs-lookup"><span data-stu-id="6d41a-173">Copy the generated token and paste it back into your command prompt.</span></span>

   ![Générer un nouveau jeton d’accès dans l’espace de travail Azure Databricks](./media/databricks-deployment/generate-token.png)

<span data-ttu-id="6d41a-175">Vous devriez désormais pouvoir accéder à tous les clusters Azure Databricks que vous créez et téléchargez des fichiers sur le DBFS.</span><span class="sxs-lookup"><span data-stu-id="6d41a-175">You should now be able to access any Azure Databricks clusters you create and upload files to the DBFS.</span></span>

## <a name="download-worker-dependencies"></a><span data-ttu-id="6d41a-176">Télécharger les dépendances des travailleurs</span><span class="sxs-lookup"><span data-stu-id="6d41a-176">Download worker dependencies</span></span>

1. <span data-ttu-id="6d41a-177">Microsoft.Spark.Worker aide Apache Spark à exécuter votre application, telles que toutes les fonctions définies par l’utilisateur (UDF) que vous avez peut-être écrites.</span><span class="sxs-lookup"><span data-stu-id="6d41a-177">Microsoft.Spark.Worker helps Apache Spark execute your app, such as any user-defined functions (UDFs) you may have written.</span></span> <span data-ttu-id="6d41a-178">Télécharger [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases/download/v0.6.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz).</span><span class="sxs-lookup"><span data-stu-id="6d41a-178">Download [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases/download/v0.6.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz).</span></span>

2. <span data-ttu-id="6d41a-179">Le *install-worker.sh* est un script qui vous permet de copier .NET pour les fichiers dépendants Apache Spark dans les nœuds de votre cluster.</span><span class="sxs-lookup"><span data-stu-id="6d41a-179">The *install-worker.sh* is a script that lets you copy .NET for Apache Spark dependent files into the nodes of your cluster.</span></span>

   <span data-ttu-id="6d41a-180">Créez un nouveau fichier nommé **install-worker.sh** sur votre ordinateur local et collez le [contenu install-worker.sh](https://raw.githubusercontent.com/dotnet/spark/master/deployment/install-worker.sh) situé sur GitHub.</span><span class="sxs-lookup"><span data-stu-id="6d41a-180">Create a new file named **install-worker.sh** on your local computer, and paste the [install-worker.sh contents](https://raw.githubusercontent.com/dotnet/spark/master/deployment/install-worker.sh) located on GitHub.</span></span>

3. <span data-ttu-id="6d41a-181">Le *db-init.sh* est un script qui installe des dépendances sur votre cluster Databricks Spark.</span><span class="sxs-lookup"><span data-stu-id="6d41a-181">The *db-init.sh* is a script that installs dependencies onto your Databricks Spark cluster.</span></span>

   <span data-ttu-id="6d41a-182">Créez un nouveau fichier nommé **db-init.sh** sur votre ordinateur local et collez le [contenu db-init.sh](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh) situé sur GitHub.</span><span class="sxs-lookup"><span data-stu-id="6d41a-182">Create a new file named **db-init.sh** on your local computer, and paste the [db-init.sh contents](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh) located on GitHub.</span></span>

   <span data-ttu-id="6d41a-183">Dans le fichier que vous `DOTNET_SPARK_RELEASE` venez `https://github.com/dotnet/spark/releases/download/v0.6.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz`de créer, définissez la variable à .</span><span class="sxs-lookup"><span data-stu-id="6d41a-183">In the file you just created, set the `DOTNET_SPARK_RELEASE` variable to `https://github.com/dotnet/spark/releases/download/v0.6.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz`.</span></span> <span data-ttu-id="6d41a-184">Laissez le reste du *fichier db-init.sh* tel qu’il est.</span><span class="sxs-lookup"><span data-stu-id="6d41a-184">Leave the rest of the *db-init.sh* file as-is.</span></span>

> [!Note]
> <span data-ttu-id="6d41a-185">Si vous utilisez Windows, vérifiez que les fins de ligne de vos scripts *install-worker.sh* et *db-init.sh* sont de style Unix (LF).</span><span class="sxs-lookup"><span data-stu-id="6d41a-185">If you are using Windows, verify that the line-endings in your *install-worker.sh* and *db-init.sh* scripts are Unix-style (LF).</span></span> <span data-ttu-id="6d41a-186">Vous pouvez changer les terminaisons de ligne grâce à des éditeurs de texte comme NotepadMD et Atom.</span><span class="sxs-lookup"><span data-stu-id="6d41a-186">You can change line endings through text editors like Notepad++ and Atom.</span></span>

## <a name="publish-your-app"></a><span data-ttu-id="6d41a-187">Publier votre application</span><span class="sxs-lookup"><span data-stu-id="6d41a-187">Publish your app</span></span>

<span data-ttu-id="6d41a-188">Ensuite, vous publiez le *mySparkApp* créé dans le [.NET pour Apache Spark - Get Started in 10-Minutes](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) tutoriel pour s’assurer que votre cluster Spark a accès à tous les fichiers dont il a besoin pour exécuter votre application.</span><span class="sxs-lookup"><span data-stu-id="6d41a-188">Next, you publish the *mySparkApp* created in the [.NET for Apache Spark - Get Started in 10-Minutes](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) tutorial to ensure your Spark cluster has access to all the files it needs to run your app.</span></span>

1. <span data-ttu-id="6d41a-189">Exécutez les commandes suivantes pour publier le *mySparkApp*:</span><span class="sxs-lookup"><span data-stu-id="6d41a-189">Run the following commands to publish the *mySparkApp*:</span></span>

   ```dotnetcli
   cd mySparkApp
   dotnet publish -c Release -f netcoreapp3.0 -r ubuntu.16.04-x64
   ```

2. <span data-ttu-id="6d41a-190">Faites les tâches suivantes pour zip vos fichiers d’application publiés afin que vous puissiez facilement les télécharger sur votre cluster Databricks Spark.</span><span class="sxs-lookup"><span data-stu-id="6d41a-190">Do the following tasks to zip your published app files so that you can easily upload them to your Databricks Spark cluster.</span></span>

   <span data-ttu-id="6d41a-191">**Sur Windows:**</span><span class="sxs-lookup"><span data-stu-id="6d41a-191">**On Windows:**</span></span>

   <span data-ttu-id="6d41a-192">Naviguez vers mySparkApp/bin/Release/netcoreapp3.0/ubuntu.16.04-x64.</span><span class="sxs-lookup"><span data-stu-id="6d41a-192">Navigate to mySparkApp/bin/Release/netcoreapp3.0/ubuntu.16.04-x64.</span></span> <span data-ttu-id="6d41a-193">Ensuite, cliquez à droite sur le dossier **Publier** et sélectionnez **Envoyer à > dossier compressé (zippé).**</span><span class="sxs-lookup"><span data-stu-id="6d41a-193">Then, right-click on **Publish** folder and select **Send to > Compressed (zipped) folder**.</span></span> <span data-ttu-id="6d41a-194">Nommez le nouveau dossier **publish.zip**.</span><span class="sxs-lookup"><span data-stu-id="6d41a-194">Name the new folder **publish.zip**.</span></span>

   <span data-ttu-id="6d41a-195">**Sur Linux, exécutez la commande ci-dessous :**</span><span class="sxs-lookup"><span data-stu-id="6d41a-195">**On Linux, run the following command:**</span></span>

   ```bash
   zip -r publish.zip .
   ```

## <a name="upload-files"></a><span data-ttu-id="6d41a-196">Charger des fichiers</span><span class="sxs-lookup"><span data-stu-id="6d41a-196">Upload files</span></span>

<span data-ttu-id="6d41a-197">Dans cette section, vous téléchargez plusieurs fichiers sur DBFS afin que votre cluster dispose de tout ce dont il a besoin pour exécuter votre application dans le cloud.</span><span class="sxs-lookup"><span data-stu-id="6d41a-197">In this section, you upload several files to DBFS so that your cluster has everything it needs to run your app in the cloud.</span></span> <span data-ttu-id="6d41a-198">Chaque fois que vous téléchargez un fichier sur le DBFS, assurez-vous d’être dans l’annuaire où se trouve ce fichier sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="6d41a-198">Each time you upload a file to the DBFS, make sure you are in the directory where that file is located on your computer.</span></span>

1. <span data-ttu-id="6d41a-199">Exécutez les commandes suivantes pour télécharger le *db-init.sh*, *install-worker.sh*, et *Microsoft.Spark.Worker* à DBFS:</span><span class="sxs-lookup"><span data-stu-id="6d41a-199">Run the following commands to upload the *db-init.sh*, *install-worker.sh*, and *Microsoft.Spark.Worker* to DBFS:</span></span>

   ```console
   databricks fs cp db-init.sh dbfs:/spark-dotnet/db-init.sh
   databricks fs cp install-worker.sh dbfs:/spark-dotnet/install-worker.sh
   databricks fs cp Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz dbfs:/spark-dotnet/   Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz
   ```

2. <span data-ttu-id="6d41a-200">Exécutez les commandes suivantes pour télécharger les fichiers restants de votre cluster devra exécuter votre application: le dossier de publication zippé, *input.txt*, et *microsoft-spark-2.4.x-0.3.0.jar*.</span><span class="sxs-lookup"><span data-stu-id="6d41a-200">Run the following commands to upload the remaining files your cluster will need to run your app: the zipped publish folder, *input.txt*, and *microsoft-spark-2.4.x-0.3.0.jar*.</span></span>

   ```console
   cd mySparkApp
   databricks fs cp input.txt dbfs:/input.txt

   cd mySparkApp\bin\Release\netcoreapp3.0\ubuntu.16.04-x64 directory
   databricks fs cp mySparkApp.zip dbfs:/spark-dotnet/publish.zip
   databricks fs cp microsoft-spark-2.4.x-0.6.0.jar dbfs:/spark-dotnet/microsoft-spark-2.4.x-0.6.0.jar
   ```

## <a name="create-a-job"></a><span data-ttu-id="6d41a-201">Créer un travail</span><span class="sxs-lookup"><span data-stu-id="6d41a-201">Create a job</span></span>

<span data-ttu-id="6d41a-202">Votre application fonctionne sur Azure Databricks à travers un travail qui fonctionne **spark-submit**, qui est la commande que vous utilisez pour exécuter .NET pour les emplois Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="6d41a-202">Your app runs on Azure Databricks through a job that runs **spark-submit**, which is the command you use to run .NET for Apache Spark jobs.</span></span>

1. <span data-ttu-id="6d41a-203">Dans votre espace de travail Azure Databricks, sélectionnez l’icône **Jobs,** puis **créez l’emploi**.</span><span class="sxs-lookup"><span data-stu-id="6d41a-203">In your Azure Databricks Workspace, select the **Jobs** icon and then **+ Create Job**.</span></span>

   ![Créer un emploi Azure Databricks](./media/databricks-deployment/create-job.png)

2. <span data-ttu-id="6d41a-205">Choisissez un titre pour votre travail, puis **sélectionnez Configurer étincelle-soumettre**.</span><span class="sxs-lookup"><span data-stu-id="6d41a-205">Choose a title for your job, and then select **Configure spark-submit**.</span></span>

   ![Configurer l’étincelle-soumettre pour le travail Databricks](./media/databricks-deployment/configure-spark-submit.png)

3. <span data-ttu-id="6d41a-207">Coller les paramètres suivants dans la configuration du travail.</span><span class="sxs-lookup"><span data-stu-id="6d41a-207">Paste the following parameters in the job configuration.</span></span> <span data-ttu-id="6d41a-208">Ensuite, sélectionnez **Confirmer**.</span><span class="sxs-lookup"><span data-stu-id="6d41a-208">Then, select **Confirm**.</span></span>

   ```
   ["--class","org.apache.spark.deploy.dotnet.DotnetRunner","/dbfs/spark-dotnet/microsoft-spark-2.4.x-0.6.0.jar","/dbfs/spark-dotnet/publish.zip","mySparkApp"]
   ```

## <a name="create-a-cluster"></a><span data-ttu-id="6d41a-209">Créer un cluster</span><span class="sxs-lookup"><span data-stu-id="6d41a-209">Create a cluster</span></span>

1. <span data-ttu-id="6d41a-210">Naviguez dans votre travail et sélectionnez **Edit** pour configurer le cluster de votre travail.</span><span class="sxs-lookup"><span data-stu-id="6d41a-210">Navigate to your job and select **Edit** to configure your job's cluster.</span></span>

2. <span data-ttu-id="6d41a-211">Réglez votre cluster à **Spark 2.4.1**.</span><span class="sxs-lookup"><span data-stu-id="6d41a-211">Set your cluster to **Spark 2.4.1**.</span></span> <span data-ttu-id="6d41a-212">Ensuite, sélectionnez **Advanced Options** > **Init Scripts**.</span><span class="sxs-lookup"><span data-stu-id="6d41a-212">Then, select **Advanced Options** > **Init Scripts**.</span></span> <span data-ttu-id="6d41a-213">Définir Init Script `dbfs:/spark-dotnet/db-init.sh`Path comme .</span><span class="sxs-lookup"><span data-stu-id="6d41a-213">Set Init Script Path as `dbfs:/spark-dotnet/db-init.sh`.</span></span>

   ![Configurer le cluster d’étincelles dans Azure Databricks](./media/databricks-deployment/cluster-config.png)

3. <span data-ttu-id="6d41a-215">Sélectionnez **Confirmez** pour confirmer les paramètres de votre cluster.</span><span class="sxs-lookup"><span data-stu-id="6d41a-215">Select **Confirm** to confirm your cluster settings.</span></span>

## <a name="run-your-app"></a><span data-ttu-id="6d41a-216">Exécutez l'application.</span><span class="sxs-lookup"><span data-stu-id="6d41a-216">Run your app</span></span>

1. <span data-ttu-id="6d41a-217">Naviguez dans votre travail et sélectionnez **Run Now** pour exécuter votre travail sur votre cluster Spark nouvellement configuré.</span><span class="sxs-lookup"><span data-stu-id="6d41a-217">Navigate to your job and select **Run Now** to run your job on your newly configured Spark cluster.</span></span>

2. <span data-ttu-id="6d41a-218">Il faut quelques minutes pour que le cluster du travail crée.</span><span class="sxs-lookup"><span data-stu-id="6d41a-218">It takes a few minutes for the job's cluster to create.</span></span> <span data-ttu-id="6d41a-219">Une fois qu’il est créé, votre travail sera soumis, et vous pouvez afficher la sortie.</span><span class="sxs-lookup"><span data-stu-id="6d41a-219">Once it is created, your job will be submitted, and you can view the output.</span></span>

3. <span data-ttu-id="6d41a-220">Sélectionnez **des clusters** dans le menu gauche, puis le nom et l’exécution de votre travail.</span><span class="sxs-lookup"><span data-stu-id="6d41a-220">Select **Clusters** from the left menu, and then the name and run of your job.</span></span>

4. <span data-ttu-id="6d41a-221">Sélectionnez **les journaux de pilote** pour afficher la sortie de votre travail.</span><span class="sxs-lookup"><span data-stu-id="6d41a-221">Select **Driver Logs** to view the output of your job.</span></span> <span data-ttu-id="6d41a-222">Lorsque votre application termine l’exécution, vous voyez le même tableau de nombre de mots de la course locale de démarrage écrit à la console de sortie standard.</span><span class="sxs-lookup"><span data-stu-id="6d41a-222">When your app finishes executing, you see the same word count table from the getting started local run written to the standard output console.</span></span>

   ![Tableau de sortie d’emplois Azure Databricks](./media/databricks-deployment/table-output.png)

   <span data-ttu-id="6d41a-224">Félicitations, vous avez exécuté votre premier .NET pour Apache Spark application dans le nuage!</span><span class="sxs-lookup"><span data-stu-id="6d41a-224">Congratulations, you've run your first .NET for Apache Spark application in the cloud!</span></span>

## <a name="clean-up-resources"></a><span data-ttu-id="6d41a-225">Nettoyer les ressources</span><span class="sxs-lookup"><span data-stu-id="6d41a-225">Clean up resources</span></span>

<span data-ttu-id="6d41a-226">Si vous n’avez plus besoin de l’espace de travail Databricks, vous pouvez supprimer votre ressource Azure Databricks dans le portail Azure.</span><span class="sxs-lookup"><span data-stu-id="6d41a-226">If you no longer need the Databricks workspace, you can delete your Azure Databricks resource in the Azure portal.</span></span> <span data-ttu-id="6d41a-227">Vous pouvez également sélectionner le nom du groupe de ressources pour ouvrir la page du groupe de ressources, puis sélectionner **Supprimer le groupe de ressources**.</span><span class="sxs-lookup"><span data-stu-id="6d41a-227">You can also select the resource group name to open the resource group page, and then select **Delete resource group**.</span></span>

## <a name="next-steps"></a><span data-ttu-id="6d41a-228">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="6d41a-228">Next steps</span></span>

<span data-ttu-id="6d41a-229">Dans ce tutoriel, vous avez déployé votre application .NET pour Apache Spark sur Databricks.</span><span class="sxs-lookup"><span data-stu-id="6d41a-229">In this tutorial, you deployed your .NET for Apache Spark application to Databricks.</span></span> <span data-ttu-id="6d41a-230">Pour plus d’informations sur Databricks, consultez la documentation Azure Databricks.</span><span class="sxs-lookup"><span data-stu-id="6d41a-230">To learn more about Databricks, continue to the Azure Databricks Documentation.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="6d41a-231">Azure Databricks Documentation</span><span class="sxs-lookup"><span data-stu-id="6d41a-231">Azure Databricks Documentation</span></span>](https://docs.microsoft.com/azure/azure-databricks/)
