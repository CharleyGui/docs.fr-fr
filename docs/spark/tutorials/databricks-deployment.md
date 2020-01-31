---
title: Déployer une application .NET pour Apache Spark sur Databricks
description: Découvrez comment déployer une application .NET pour Apache Spark sur Databricks.
ms.date: 01/23/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: a117d85ab911b380598c93417f6ff95661ab864c
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868029"
---
# <a name="tutorial-deploy-a-net-for-apache-spark-application-to-databricks"></a><span data-ttu-id="30f77-103">Didacticiel : déployer une application .NET pour Apache Spark sur Databricks</span><span class="sxs-lookup"><span data-stu-id="30f77-103">Tutorial: Deploy a .NET for Apache Spark application to Databricks</span></span>

<span data-ttu-id="30f77-104">Ce didacticiel vous apprend à déployer votre application dans le Cloud par le biais de Azure Databricks, une plateforme d’analytique basée sur Apache Spark avec une configuration en un clic, des workflows rationalisés et un espace de travail interactif qui permet la collaboration.</span><span class="sxs-lookup"><span data-stu-id="30f77-104">This tutorial teaches you how to deploy your app to the cloud through Azure Databricks, an Apache Spark-based analytics platform with one-click setup, streamlined workflows, and interactive workspace that enables collaboration.</span></span>

<span data-ttu-id="30f77-105">Dans ce didacticiel, vous apprendrez à :</span><span class="sxs-lookup"><span data-stu-id="30f77-105">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="30f77-106">Créer un espace de travail Azure Databricks.</span><span class="sxs-lookup"><span data-stu-id="30f77-106">Create an Azure Databricks workspace.</span></span>
> - <span data-ttu-id="30f77-107">Publiez votre application .NET pour Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="30f77-107">Publish your .NET for Apache Spark app.</span></span>
> - <span data-ttu-id="30f77-108">Créez un travail Spark et un cluster Spark.</span><span class="sxs-lookup"><span data-stu-id="30f77-108">Create a Spark job and Spark cluster.</span></span>
> - <span data-ttu-id="30f77-109">Exécutez votre application sur le cluster Spark.</span><span class="sxs-lookup"><span data-stu-id="30f77-109">Run your app on the Spark cluster.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="30f77-110">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="30f77-110">Prerequisites</span></span>

<span data-ttu-id="30f77-111">Avant de commencer, effectuez les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="30f77-111">Before you start, do the following tasks:</span></span>

* <span data-ttu-id="30f77-112">Si vous n’avez pas de compte Azure, créez un [compte gratuit](https://azure.microsoft.com/free/).</span><span class="sxs-lookup"><span data-stu-id="30f77-112">If you don't have an Azure account, create a [free account](https://azure.microsoft.com/free/).</span></span>
* <span data-ttu-id="30f77-113">Connectez-vous au [portail Azure](https://portal.azure.com/).</span><span class="sxs-lookup"><span data-stu-id="30f77-113">Sign in to the [Azure portal](https://portal.azure.com/).</span></span>
* <span data-ttu-id="30f77-114">Complétez le [.net pour Apache Spark-commencez dans](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) le didacticiel de 10 minutes.</span><span class="sxs-lookup"><span data-stu-id="30f77-114">Complete the [.NET for Apache Spark - Get Started in 10-Minutes](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) tutorial.</span></span>

## <a name="create-an-azure-databricks-workspace"></a><span data-ttu-id="30f77-115">Créer un espace de travail Azure Databricks</span><span class="sxs-lookup"><span data-stu-id="30f77-115">Create an Azure Databricks workspace</span></span>

> [!Note]
> <span data-ttu-id="30f77-116">Ce didacticiel ne peut pas être exécuté à l’aide **d’un abonnement d’essai gratuit Azure**.</span><span class="sxs-lookup"><span data-stu-id="30f77-116">This tutorial cannot be carried out using **Azure Free Trial Subscription**.</span></span>
> <span data-ttu-id="30f77-117">Si vous disposez d’un compte gratuit, accédez à votre profil et modifiez votre abonnement en **paiement à l’accès**.</span><span class="sxs-lookup"><span data-stu-id="30f77-117">If you have a free account, go to your profile and change your subscription to **pay-as-you-go**.</span></span> <span data-ttu-id="30f77-118">Pour plus d’informations, consultez [compte gratuit Azure](https://azure.microsoft.com/free/).</span><span class="sxs-lookup"><span data-stu-id="30f77-118">For more information, see [Azure free account](https://azure.microsoft.com/free/).</span></span> <span data-ttu-id="30f77-119">Ensuite, [supprimez la limite de dépense](https://docs.microsoft.com/azure/billing/billing-spending-limit#why-you-might-want-to-remove-the-spending-limit)et [demandez une augmentation du quota](https://docs.microsoft.com/azure/azure-supportability/resource-manager-core-quotas-request) pour processeurs virtuels dans votre région.</span><span class="sxs-lookup"><span data-stu-id="30f77-119">Then, [remove the spending limit](https://docs.microsoft.com/azure/billing/billing-spending-limit#why-you-might-want-to-remove-the-spending-limit), and [request a quota increase](https://docs.microsoft.com/azure/azure-supportability/resource-manager-core-quotas-request) for vCPUs in your region.</span></span> <span data-ttu-id="30f77-120">Lorsque vous créez votre espace de travail Azure Databricks, vous pouvez sélectionner le niveau tarifaire **d’essai (version d’évaluation gratuite de 14 jours)** pour permettre à l’espace de travail d’accéder à la version gratuite Premium Azure Databricks DBUs pendant 14 jours.</span><span class="sxs-lookup"><span data-stu-id="30f77-120">When you create your Azure Databricks workspace, you can select the **Trial (Premium - 14-Days Free DBUs)** pricing tier to give the workspace access to free Premium Azure Databricks DBUs for 14 days.</span></span>

<span data-ttu-id="30f77-121">Dans cette section, vous allez créer un espace de travail Azure Databricks à l’aide de l’Portail Azure.</span><span class="sxs-lookup"><span data-stu-id="30f77-121">In this section, you create an Azure Databricks workspace using the Azure portal.</span></span>

1. <span data-ttu-id="30f77-122">Dans le Portail Azure, sélectionnez **créer une ressource** > **analytique** > **Azure Databricks**.</span><span class="sxs-lookup"><span data-stu-id="30f77-122">In the Azure portal, select **Create a resource** > **Analytics** > **Azure Databricks**.</span></span>

   ![Créer une ressource Azure Databricks dans Portail Azure](./media/databricks-deployment/create-databricks-resource.png)

2. <span data-ttu-id="30f77-124">Sous **Azure Databricks service**, fournissez les valeurs pour créer un espace de travail Databricks.</span><span class="sxs-lookup"><span data-stu-id="30f77-124">Under **Azure Databricks Service**, provide the values to create a Databricks workspace.</span></span>

    |<span data-ttu-id="30f77-125">Les</span><span class="sxs-lookup"><span data-stu-id="30f77-125">Property</span></span>  |<span data-ttu-id="30f77-126">Description</span><span class="sxs-lookup"><span data-stu-id="30f77-126">Description</span></span>  |
    |---------|---------|
    |<span data-ttu-id="30f77-127">**Nom de l’espace de travail**</span><span class="sxs-lookup"><span data-stu-id="30f77-127">**Workspace name**</span></span>     | <span data-ttu-id="30f77-128">Donnez un nom à votre espace de travail Databricks.</span><span class="sxs-lookup"><span data-stu-id="30f77-128">Provide a name for your Databricks workspace.</span></span>        |
    |<span data-ttu-id="30f77-129">**Abonnement**</span><span class="sxs-lookup"><span data-stu-id="30f77-129">**Subscription**</span></span>     | <span data-ttu-id="30f77-130">Dans la liste déroulante, sélectionnez votre abonnement Azure.</span><span class="sxs-lookup"><span data-stu-id="30f77-130">From the drop-down, select your Azure subscription.</span></span>        |
    |<span data-ttu-id="30f77-131">**Groupe de ressources**</span><span class="sxs-lookup"><span data-stu-id="30f77-131">**Resource group**</span></span>     | <span data-ttu-id="30f77-132">Spécifiez si vous souhaitez créer un nouveau groupe de ressources ou utiliser un groupe existant.</span><span class="sxs-lookup"><span data-stu-id="30f77-132">Specify whether you want to create a new resource group or use an existing one.</span></span> <span data-ttu-id="30f77-133">Un groupe de ressources est un conteneur qui contient les ressources associées à une solution Azure.</span><span class="sxs-lookup"><span data-stu-id="30f77-133">A resource group is a container that holds related resources for an Azure solution.</span></span> <span data-ttu-id="30f77-134">Pour plus d’informations, consultez [vue d’ensemble du groupe de ressources Azure](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-overview).</span><span class="sxs-lookup"><span data-stu-id="30f77-134">For more information, see [Azure Resource Group overview](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-overview).</span></span> |
    |<span data-ttu-id="30f77-135">**Emplacement**</span><span class="sxs-lookup"><span data-stu-id="30f77-135">**Location**</span></span>     | <span data-ttu-id="30f77-136">Sélectionnez la région de votre choix.</span><span class="sxs-lookup"><span data-stu-id="30f77-136">Select your preferred region.</span></span> <span data-ttu-id="30f77-137">Pour plus d’informations sur les régions disponibles, consultez [services Azure disponibles par région](https://azure.microsoft.com/regions/services/).</span><span class="sxs-lookup"><span data-stu-id="30f77-137">For information about available regions, see [Azure services available by region](https://azure.microsoft.com/regions/services/).</span></span>        |
    |<span data-ttu-id="30f77-138">**Niveau tarifaire**</span><span class="sxs-lookup"><span data-stu-id="30f77-138">**Pricing Tier**</span></span>     |  <span data-ttu-id="30f77-139">Choisissez entre **standard**, **Premium**ou **version d’évaluation**.</span><span class="sxs-lookup"><span data-stu-id="30f77-139">Choose between **Standard**, **Premium**, or **Trial**.</span></span> <span data-ttu-id="30f77-140">Pour plus d’informations sur ces niveaux, consultez la [page de tarification Databricks](https://azure.microsoft.com/pricing/details/databricks/).</span><span class="sxs-lookup"><span data-stu-id="30f77-140">For more information on these tiers, see [Databricks pricing page](https://azure.microsoft.com/pricing/details/databricks/).</span></span>       |
    |<span data-ttu-id="30f77-141">**Réseau virtuel**</span><span class="sxs-lookup"><span data-stu-id="30f77-141">**Virtual Network**</span></span>     |   <span data-ttu-id="30f77-142">Non</span><span class="sxs-lookup"><span data-stu-id="30f77-142">No</span></span>       |

3. <span data-ttu-id="30f77-143">Sélectionnez **Créer**.</span><span class="sxs-lookup"><span data-stu-id="30f77-143">Select **Create**.</span></span> <span data-ttu-id="30f77-144">La création de l’espace de travail prend quelques minutes.</span><span class="sxs-lookup"><span data-stu-id="30f77-144">The workspace creation takes a few minutes.</span></span> <span data-ttu-id="30f77-145">Pendant la création de l’espace de travail, vous pouvez afficher l’état du déploiement dans les **notifications**.</span><span class="sxs-lookup"><span data-stu-id="30f77-145">During workspace creation, you can view the deployment status in **Notifications**.</span></span>

## <a name="install-azure-databricks-tools"></a><span data-ttu-id="30f77-146">Installer Azure Databricks Tools</span><span class="sxs-lookup"><span data-stu-id="30f77-146">Install Azure Databricks tools</span></span>

<span data-ttu-id="30f77-147">Vous pouvez utiliser l' **interface CLI Databricks** pour vous connecter à des clusters Azure Databricks et charger des fichiers à partir de votre ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="30f77-147">You can use the **Databricks CLI** to connect to Azure Databricks clusters and upload files to them from your local machine.</span></span> <span data-ttu-id="30f77-148">Les clusters Databricks accèdent aux fichiers via le système de fichiers DBFS (Databricks).</span><span class="sxs-lookup"><span data-stu-id="30f77-148">Databricks clusters access files through DBFS (Databricks File System).</span></span>

1. <span data-ttu-id="30f77-149">L’interface CLI Databricks nécessite python 3,6 ou version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="30f77-149">The Databricks CLI requires Python 3.6 or above.</span></span> <span data-ttu-id="30f77-150">Si vous avez déjà installé python, vous pouvez ignorer cette étape.</span><span class="sxs-lookup"><span data-stu-id="30f77-150">If you already have Python installed, you can skip this step.</span></span>

   <span data-ttu-id="30f77-151">**Pour Windows :**</span><span class="sxs-lookup"><span data-stu-id="30f77-151">**For Windows:**</span></span>

   [<span data-ttu-id="30f77-152">Télécharger python pour Windows</span><span class="sxs-lookup"><span data-stu-id="30f77-152">Download Python for Windows</span></span>](https://www.python.org/ftp/python/3.7.4/python-3.7.4.exe)

   <span data-ttu-id="30f77-153">**Pour Linux :** Python est préinstallé sur la plupart des distributions Linux.</span><span class="sxs-lookup"><span data-stu-id="30f77-153">**For Linux:** Python comes preinstalled on most Linux distributions.</span></span> <span data-ttu-id="30f77-154">Exécutez la commande suivante pour déterminer la version que vous avez installée :</span><span class="sxs-lookup"><span data-stu-id="30f77-154">Run the following command to see which version you have installed:</span></span>

   ```bash
   python3 --version
   ```

2. <span data-ttu-id="30f77-155">Utilisez PIP pour installer l’interface de commande de Databricks.</span><span class="sxs-lookup"><span data-stu-id="30f77-155">Use pip to install the Databricks CLI.</span></span> <span data-ttu-id="30f77-156">Python 3,4 et versions ultérieures incluent PIP par défaut.</span><span class="sxs-lookup"><span data-stu-id="30f77-156">Python 3.4 and later include pip by default.</span></span> <span data-ttu-id="30f77-157">Utilisez PIP3 pour Python 3.</span><span class="sxs-lookup"><span data-stu-id="30f77-157">Use pip3 for Python 3.</span></span> <span data-ttu-id="30f77-158">Exécutez la commande suivante : .</span><span class="sxs-lookup"><span data-stu-id="30f77-158">Run the following command:</span></span>

   ```bash
   pip3 install databricks-cli
   ```

3. <span data-ttu-id="30f77-159">Une fois que vous avez installé l’interface de ligne de commande Databricks, ouvrez une nouvelle invite de commandes et exécutez la commande `databricks`.</span><span class="sxs-lookup"><span data-stu-id="30f77-159">Once you've installed the Databricks CLI, open a new command prompt and run the command `databricks`.</span></span> <span data-ttu-id="30f77-160">Si vous recevez un **« databricks » n’est pas reconnu comme une erreur de commande interne ou externe**, veillez à ouvrir une nouvelle invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="30f77-160">If you receive a **'databricks' is not recognized as an internal or external command error**, make sure you opened a new command prompt.</span></span>

## <a name="set-up-azure-databricks"></a><span data-ttu-id="30f77-161">Configurer Azure Databricks</span><span class="sxs-lookup"><span data-stu-id="30f77-161">Set up Azure Databricks</span></span>

<span data-ttu-id="30f77-162">Maintenant que l’interface CLI Databricks est installée, vous devez configurer les détails de l’authentification.</span><span class="sxs-lookup"><span data-stu-id="30f77-162">Now that you have the Databricks CLI installed, you need to set up authentication details.</span></span>

1. <span data-ttu-id="30f77-163">Exécutez la commande CLI Databricks `databricks configure --token`.</span><span class="sxs-lookup"><span data-stu-id="30f77-163">Run the Databricks CLI command `databricks configure --token`.</span></span>

2. <span data-ttu-id="30f77-164">Après avoir exécuté la commande configurer, vous êtes invité à entrer un ordinateur hôte.</span><span class="sxs-lookup"><span data-stu-id="30f77-164">After running the configure command, you are prompted to enter a host.</span></span> <span data-ttu-id="30f77-165">Votre URL d’hôte utilise le format : **https://< \Location >. azuredatabricks. net**.</span><span class="sxs-lookup"><span data-stu-id="30f77-165">Your host URL uses the format: **https://<\Location>.azuredatabricks.net**.</span></span> <span data-ttu-id="30f77-166">Par exemple, si vous avez sélectionné **eastus2** lors de la création du service Azure Databricks, l’hôte est **https://eastus2.azuredatabricks.net** .</span><span class="sxs-lookup"><span data-stu-id="30f77-166">For instance, if you selected **eastus2** during Azure Databricks Service creation, the host would be **https://eastus2.azuredatabricks.net**.</span></span>

3. <span data-ttu-id="30f77-167">Après avoir entré votre hôte, vous êtes invité à entrer un jeton.</span><span class="sxs-lookup"><span data-stu-id="30f77-167">After entering your host, you are prompted to enter a token.</span></span> <span data-ttu-id="30f77-168">Dans le Portail Azure, sélectionnez **lancer l’espace de travail** pour lancer votre Azure Databricks espace de travail.</span><span class="sxs-lookup"><span data-stu-id="30f77-168">In the Azure portal, select **Launch Workspace** to launch your Azure Databricks workspace.</span></span>

   ![Lancer Azure Databricks espace de travail](./media/databricks-deployment/launch-databricks-workspace.png)

4. <span data-ttu-id="30f77-170">Sur la page d’hébergement de votre espace de travail, sélectionnez **paramètres utilisateur**.</span><span class="sxs-lookup"><span data-stu-id="30f77-170">On the home page of your workspace, select **User Settings**.</span></span>

   ![Paramètres utilisateur dans Azure Databricks espace de travail](./media/databricks-deployment/databricks-user-settings.png)

5. <span data-ttu-id="30f77-172">Sur la page Paramètres utilisateur, vous pouvez générer un nouveau jeton.</span><span class="sxs-lookup"><span data-stu-id="30f77-172">On the User Settings page, you can generate a new token.</span></span> <span data-ttu-id="30f77-173">Copiez le jeton généré et collez-le à nouveau dans votre invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="30f77-173">Copy the generated token and paste it back into your command prompt.</span></span>

   ![Générer un nouveau jeton d’accès dans Azure Databricks espace de travail](./media/databricks-deployment/generate-token.png)

<span data-ttu-id="30f77-175">Vous devez maintenant être en mesure d’accéder à tous les clusters de Azure Databricks que vous créez et que vous chargez dans le fichier DBFS.</span><span class="sxs-lookup"><span data-stu-id="30f77-175">You should now be able to access any Azure Databricks clusters you create and upload files to the DBFS.</span></span>

## <a name="download-worker-dependencies"></a><span data-ttu-id="30f77-176">Télécharger les dépendances de Worker</span><span class="sxs-lookup"><span data-stu-id="30f77-176">Download worker dependencies</span></span>

1. <span data-ttu-id="30f77-177">Microsoft. Spark. Worker aide Apache Spark exécuter votre application, telle que les fonctions définies par l’utilisateur (UDF) que vous avez peut-être écrites.</span><span class="sxs-lookup"><span data-stu-id="30f77-177">Microsoft.Spark.Worker helps Apache Spark execute your app, such as any user-defined functions (UDFs) you may have written.</span></span> <span data-ttu-id="30f77-178">Téléchargez [Microsoft. Spark. Worker](https://github.com/dotnet/spark/releases/download/v0.6.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz).</span><span class="sxs-lookup"><span data-stu-id="30f77-178">Download [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases/download/v0.6.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz).</span></span>

2. <span data-ttu-id="30f77-179">Le *install-Worker.sh* est un script qui vous permet de copier .net pour Apache Spark fichiers dépendants dans les nœuds de votre cluster.</span><span class="sxs-lookup"><span data-stu-id="30f77-179">The *install-worker.sh* is a script that lets you copy .NET for Apache Spark dependent files into the nodes of your cluster.</span></span>

   <span data-ttu-id="30f77-180">Créez un nouveau fichier nommé **install-Worker.sh** sur votre ordinateur local, puis collez le [contenu install-Worker.sh](https://raw.githubusercontent.com/dotnet/spark/master/deployment/install-worker.sh) situé sur GitHub.</span><span class="sxs-lookup"><span data-stu-id="30f77-180">Create a new file named **install-worker.sh** on your local computer, and paste the [install-worker.sh contents](https://raw.githubusercontent.com/dotnet/spark/master/deployment/install-worker.sh) located on GitHub.</span></span>

3. <span data-ttu-id="30f77-181">Le *DB-init.sh* est un script qui installe des dépendances sur votre cluster Databricks Spark.</span><span class="sxs-lookup"><span data-stu-id="30f77-181">The *db-init.sh* is a script that installs dependencies onto your Databricks Spark cluster.</span></span>

   <span data-ttu-id="30f77-182">Créez un nouveau fichier nommé **DB-init.sh** sur votre ordinateur local, puis collez le [contenu DB-init.sh](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh) situé sur GitHub.</span><span class="sxs-lookup"><span data-stu-id="30f77-182">Create a new file named **db-init.sh** on your local computer, and paste the [db-init.sh contents](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh) located on GitHub.</span></span>

   <span data-ttu-id="30f77-183">Dans le fichier que vous venez de créer, affectez à la variable `DOTNET_SPARK_RELEASE` la valeur `https://github.com/dotnet/spark/releases/download/v0.6.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz`.</span><span class="sxs-lookup"><span data-stu-id="30f77-183">In the file you just created, set the `DOTNET_SPARK_RELEASE` variable to `https://github.com/dotnet/spark/releases/download/v0.6.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz`.</span></span> <span data-ttu-id="30f77-184">Laissez le reste du fichier *DB-init.sh* tel quel.</span><span class="sxs-lookup"><span data-stu-id="30f77-184">Leave the rest of the *db-init.sh* file as-is.</span></span>

> [!Note]
> <span data-ttu-id="30f77-185">Si vous utilisez Windows, vérifiez que les fins de ligne dans vos scripts *install-Worker.sh* et *DB-init.sh* sont de type UNIX (LF).</span><span class="sxs-lookup"><span data-stu-id="30f77-185">If you are using Windows, verify that the line-endings in your *install-worker.sh* and *db-init.sh* scripts are Unix-style (LF).</span></span> <span data-ttu-id="30f77-186">Vous pouvez modifier les fins de ligne à l’aide d’éditeurs de texte tels que Notepad + + et Atom.</span><span class="sxs-lookup"><span data-stu-id="30f77-186">You can change line endings through text editors like Notepad++ and Atom.</span></span>

## <a name="publish-your-app"></a><span data-ttu-id="30f77-187">Publier une application</span><span class="sxs-lookup"><span data-stu-id="30f77-187">Publish your app</span></span>

<span data-ttu-id="30f77-188">Ensuite, vous publiez le *mySparkApp* créé dans [.net pour Apache Spark-bien démarrer dans](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) un didacticiel de 10 minutes pour vous assurer que votre cluster Spark a accès à tous les fichiers dont il a besoin pour exécuter votre application.</span><span class="sxs-lookup"><span data-stu-id="30f77-188">Next, you publish the *mySparkApp* created in the [.NET for Apache Spark - Get Started in 10-Minutes](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) tutorial to ensure your Spark cluster has access to all the files it needs to run your app.</span></span>

1. <span data-ttu-id="30f77-189">Exécutez les commandes suivantes pour publier le *mySparkApp*:</span><span class="sxs-lookup"><span data-stu-id="30f77-189">Run the following commands to publish the *mySparkApp*:</span></span>

   <span data-ttu-id="30f77-190">**Sur Windows :**</span><span class="sxs-lookup"><span data-stu-id="30f77-190">**On Windows:**</span></span>

   ```console
   cd mySparkApp
   dotnet publish -c Release -f netcoreapp3.0 -r ubuntu.16.04-x64
   ```

   <span data-ttu-id="30f77-191">**Sur Linux :**</span><span class="sxs-lookup"><span data-stu-id="30f77-191">**On Linux:**</span></span>

   ```bash
   cd mySparkApp
   dotnet publish -c Release -f netcoreapp3.0 -r ubuntu.16.04-x64
   ```

2. <span data-ttu-id="30f77-192">Effectuez les tâches suivantes pour compresser les fichiers de votre application publiée afin de pouvoir les télécharger facilement vers votre cluster Databricks Spark.</span><span class="sxs-lookup"><span data-stu-id="30f77-192">Do the following tasks to zip your published app files so that you can easily upload them to your Databricks Spark cluster.</span></span>

   <span data-ttu-id="30f77-193">**Sur Windows :**</span><span class="sxs-lookup"><span data-stu-id="30f77-193">**On Windows:**</span></span>

   <span data-ttu-id="30f77-194">Accédez à mySparkApp/bin/Release/netcoreapp 3.0/Ubuntu. 16.04-x64.</span><span class="sxs-lookup"><span data-stu-id="30f77-194">Navigate to mySparkApp/bin/Release/netcoreapp3.0/ubuntu.16.04-x64.</span></span> <span data-ttu-id="30f77-195">Ensuite, cliquez avec le bouton droit sur le dossier de **publication** et sélectionnez **Envoyer vers > dossier compressé (zippé)** .</span><span class="sxs-lookup"><span data-stu-id="30f77-195">Then, right-click on **Publish** folder and select **Send to > Compressed (zipped) folder**.</span></span> <span data-ttu-id="30f77-196">Nommez le nouveau dossier **Publish. zip**.</span><span class="sxs-lookup"><span data-stu-id="30f77-196">Name the new folder **publish.zip**.</span></span>

   <span data-ttu-id="30f77-197">**Sur Linux, exécutez la commande suivante :**</span><span class="sxs-lookup"><span data-stu-id="30f77-197">**On Linux, run the following command:**</span></span>

   ```bash
   zip -r publish.zip .
   ```

## <a name="upload-files"></a><span data-ttu-id="30f77-198">Charger des fichiers</span><span class="sxs-lookup"><span data-stu-id="30f77-198">Upload files</span></span>

<span data-ttu-id="30f77-199">Dans cette section, vous téléchargez plusieurs fichiers sur DBFS afin que votre cluster dispose de tout ce dont il a besoin pour exécuter votre application dans le Cloud.</span><span class="sxs-lookup"><span data-stu-id="30f77-199">In this section, you upload several files to DBFS so that your cluster has everything it needs to run your app in the cloud.</span></span> <span data-ttu-id="30f77-200">Chaque fois que vous chargez un fichier sur le DBFS, vérifiez que vous vous trouvez dans le répertoire où se trouve ce fichier sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="30f77-200">Each time you upload a file to the DBFS, make sure you are in the directory where that file is located on your computer.</span></span>

1. <span data-ttu-id="30f77-201">Exécutez les commandes suivantes pour télécharger *DB-init.sh*, *install-Worker.sh*et *Microsoft. Spark. Worker* vers dBFS :</span><span class="sxs-lookup"><span data-stu-id="30f77-201">Run the following commands to upload the *db-init.sh*, *install-worker.sh*, and *Microsoft.Spark.Worker* to DBFS:</span></span>

   ```console
   databricks fs cp db-init.sh dbfs:/spark-dotnet/db-init.sh
   databricks fs cp install-worker.sh dbfs:/spark-dotnet/install-worker.sh
   databricks fs cp Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz dbfs:/spark-dotnet/   Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz
   ```

2. <span data-ttu-id="30f77-202">Exécutez les commandes suivantes pour télécharger les fichiers restants dont votre cluster a besoin pour exécuter votre application : le dossier de publication compressé, *Input. txt*et *Microsoft-Spark-2.4. x-0.3.0. jar*.</span><span class="sxs-lookup"><span data-stu-id="30f77-202">Run the following commands to upload the remaining files your cluster will need to run your app: the zipped publish folder, *input.txt*, and *microsoft-spark-2.4.x-0.3.0.jar*.</span></span>

   ```console
   cd mySparkApp
   databricks fs cp input.txt dbfs:/input.txt

   cd mySparkApp\bin\Release\netcoreapp3.0\ubuntu.16.04-x64 directory
   databricks fs cp mySparkApp.zip dbfs:/spark-dotnet/publish.zip
   databricks fs cp microsoft-spark-2.4.x-0.6.0.jar dbfs:/spark-dotnet/microsoft-spark-2.4.x-0.6.0.jar
   ```

## <a name="create-a-job"></a><span data-ttu-id="30f77-203">Créer un travail</span><span class="sxs-lookup"><span data-stu-id="30f77-203">Create a job</span></span>

<span data-ttu-id="30f77-204">Votre application s’exécute sur Azure Databricks par le biais d’un travail qui exécute **Spark-Submit**, qui est la commande que vous utilisez pour exécuter .net pour les tâches de Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="30f77-204">Your app runs on Azure Databricks through a job that runs **spark-submit**, which is the command you use to run .NET for Apache Spark jobs.</span></span>

1. <span data-ttu-id="30f77-205">Dans votre espace de travail Azure Databricks, sélectionnez l’icône **travaux** , puis **+ créer une tâche**.</span><span class="sxs-lookup"><span data-stu-id="30f77-205">In your Azure Databricks Workspace, select the **Jobs** icon and then **+ Create Job**.</span></span>

   ![Créer un travail de Azure Databricks](./media/databricks-deployment/create-job.png)

2. <span data-ttu-id="30f77-207">Choisissez un titre pour votre travail, puis sélectionnez **configurer Spark-Submit**.</span><span class="sxs-lookup"><span data-stu-id="30f77-207">Choose a title for your job, and then select **Configure spark-submit**.</span></span>

   ![Configurer Spark-submit pour la tâche Databricks](./media/databricks-deployment/configure-spark-submit.png)

3. <span data-ttu-id="30f77-209">Collez les paramètres suivants dans la configuration du travail.</span><span class="sxs-lookup"><span data-stu-id="30f77-209">Paste the following parameters in the job configuration.</span></span> <span data-ttu-id="30f77-210">Ensuite, sélectionnez **confirmer**.</span><span class="sxs-lookup"><span data-stu-id="30f77-210">Then, select **Confirm**.</span></span>

   ```
   ["--class","org.apache.spark.deploy.dotnet.DotnetRunner","/dbfs/spark-dotnet/microsoft-spark-2.4.x-0.6.0.jar","/dbfs/spark-dotnet/publish.zip","mySparkApp"]
   ```

## <a name="create-a-cluster"></a><span data-ttu-id="30f77-211">Créer un cluster</span><span class="sxs-lookup"><span data-stu-id="30f77-211">Create a cluster</span></span>

1. <span data-ttu-id="30f77-212">Accédez à votre travail et sélectionnez **modifier** pour configurer le cluster de votre travail.</span><span class="sxs-lookup"><span data-stu-id="30f77-212">Navigate to your job and select **Edit** to configure your job's cluster.</span></span>

2. <span data-ttu-id="30f77-213">Définissez votre cluster sur **Spark 2.4.1**.</span><span class="sxs-lookup"><span data-stu-id="30f77-213">Set your cluster to **Spark 2.4.1**.</span></span> <span data-ttu-id="30f77-214">Ensuite, sélectionnez **Options avancées** > les **scripts init**.</span><span class="sxs-lookup"><span data-stu-id="30f77-214">Then, select **Advanced Options** > **Init Scripts**.</span></span> <span data-ttu-id="30f77-215">Définissez le chemin d’accès du script init en tant que `dbfs:/spark-dotnet/db-init.sh`.</span><span class="sxs-lookup"><span data-stu-id="30f77-215">Set Init Script Path as `dbfs:/spark-dotnet/db-init.sh`.</span></span>

   ![Configurer le cluster Spark dans Azure Databricks](./media/databricks-deployment/cluster-config.png)

3. <span data-ttu-id="30f77-217">Sélectionnez **confirmer** pour confirmer vos paramètres de cluster.</span><span class="sxs-lookup"><span data-stu-id="30f77-217">Select **Confirm** to confirm your cluster settings.</span></span>

## <a name="run-your-app"></a><span data-ttu-id="30f77-218">Exécuter votre application</span><span class="sxs-lookup"><span data-stu-id="30f77-218">Run your app</span></span>

1. <span data-ttu-id="30f77-219">Accédez à votre travail et sélectionnez **Exécuter maintenant** pour exécuter votre travail sur le cluster Spark que vous venez de configurer.</span><span class="sxs-lookup"><span data-stu-id="30f77-219">Navigate to your job and select **Run Now** to run your job on your newly configured Spark cluster.</span></span>

2. <span data-ttu-id="30f77-220">La création du cluster du travail prend quelques minutes.</span><span class="sxs-lookup"><span data-stu-id="30f77-220">It takes a few minutes for the job's cluster to create.</span></span> <span data-ttu-id="30f77-221">Une fois créée, votre travail est envoyé et vous pouvez afficher la sortie.</span><span class="sxs-lookup"><span data-stu-id="30f77-221">Once it is created, your job will be submitted, and you can view the output.</span></span>

3. <span data-ttu-id="30f77-222">Sélectionnez **clusters** dans le menu de gauche, puis le nom et l’exécution de votre travail.</span><span class="sxs-lookup"><span data-stu-id="30f77-222">Select **Clusters** from the left menu, and then the name and run of your job.</span></span>

4. <span data-ttu-id="30f77-223">Sélectionnez **journaux des pilotes** pour afficher la sortie de votre travail.</span><span class="sxs-lookup"><span data-stu-id="30f77-223">Select **Driver Logs** to view the output of your job.</span></span> <span data-ttu-id="30f77-224">À la fin de l’exécution de votre application, vous voyez le même tableau de nombre de mots de la série mise en route locale exécutée dans la console de sortie standard.</span><span class="sxs-lookup"><span data-stu-id="30f77-224">When your app finishes executing, you see the same word count table from the getting started local run written to the standard output console.</span></span>

   ![Table de sortie de la tâche de Azure Databricks](./media/databricks-deployment/table-output.png)

   <span data-ttu-id="30f77-226">Félicitations, vous avez exécuté votre première application .NET pour Apache Spark dans le Cloud !</span><span class="sxs-lookup"><span data-stu-id="30f77-226">Congratulations, you've run your first .NET for Apache Spark application in the cloud!</span></span>

## <a name="clean-up-resources"></a><span data-ttu-id="30f77-227">Nettoyer les ressources</span><span class="sxs-lookup"><span data-stu-id="30f77-227">Clean up resources</span></span>

<span data-ttu-id="30f77-228">Si vous n’avez plus besoin de l’espace de travail Databricks, vous pouvez supprimer votre ressource Azure Databricks dans le Portail Azure.</span><span class="sxs-lookup"><span data-stu-id="30f77-228">If you no longer need the Databricks workspace, you can delete your Azure Databricks resource in the Azure portal.</span></span> <span data-ttu-id="30f77-229">Vous pouvez également sélectionner le nom du groupe de ressources pour ouvrir la page groupe de ressources, puis sélectionner **supprimer le groupe de ressources**.</span><span class="sxs-lookup"><span data-stu-id="30f77-229">You can also select the resource group name to open the resource group page, and then select **Delete resource group**.</span></span>

## <a name="next-steps"></a><span data-ttu-id="30f77-230">Étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="30f77-230">Next steps</span></span>

<span data-ttu-id="30f77-231">Dans ce tutoriel, vous avez déployé votre application .NET pour Apache Spark sur Databricks.</span><span class="sxs-lookup"><span data-stu-id="30f77-231">In this tutorial, you deployed your .NET for Apache Spark application to Databricks.</span></span> <span data-ttu-id="30f77-232">Pour plus d’informations sur Databricks, consultez la documentation Azure Databricks.</span><span class="sxs-lookup"><span data-stu-id="30f77-232">To learn more about Databricks, continue to the Azure Databricks Documentation.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="30f77-233">Documentation Azure Databricks</span><span class="sxs-lookup"><span data-stu-id="30f77-233">Azure Databricks Documentation</span></span>](https://docs.microsoft.com/azure/azure-databricks/)
