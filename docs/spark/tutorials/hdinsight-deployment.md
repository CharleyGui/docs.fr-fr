---
title: Déployer une application .NET pour Apache Spark sur Azure HDInsight
description: Découvrez comment déployer une application .NET pour Apache Spark sur HDInsight.
ms.date: 01/23/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 6b8dbe395a5db9631433a5821f5ef2b9ade556f6
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895696"
---
# <a name="tutorial-deploy-a-net-for-apache-spark-application-to-azure-hdinsight"></a><span data-ttu-id="79cbc-103">Didacticiel : déployer une application .NET pour Apache Spark sur Azure HDInsight</span><span class="sxs-lookup"><span data-stu-id="79cbc-103">Tutorial: Deploy a .NET for Apache Spark application to Azure HDInsight</span></span>

<span data-ttu-id="79cbc-104">Ce didacticiel vous apprend à déployer votre .NET pour Apache Spark application dans le Cloud par le biais d’un cluster Azure HDInsight.</span><span class="sxs-lookup"><span data-stu-id="79cbc-104">This tutorial teaches you how to deploy your .NET for Apache Spark app to the cloud through an Azure HDInsight cluster.</span></span> <span data-ttu-id="79cbc-105">HDInsight facilite la création et la configuration d’un cluster Spark dans Azure, car les clusters Spark dans HDInsight sont compatibles avec le stockage Azure et les Azure Data Lake Storage.</span><span class="sxs-lookup"><span data-stu-id="79cbc-105">HDInsight makes it easier to create and configure a Spark cluster in Azure since Spark clusters in HDInsight are compatible with Azure Storage and Azure Data Lake Storage.</span></span>

<span data-ttu-id="79cbc-106">Dans ce tutoriel, vous allez apprendre à :</span><span class="sxs-lookup"><span data-stu-id="79cbc-106">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="79cbc-107">Accédez à vos comptes de stockage à l’aide de Explorateur Stockage Azure.</span><span class="sxs-lookup"><span data-stu-id="79cbc-107">Access your storage accounts using Azure Storage Explorer.</span></span>
> * <span data-ttu-id="79cbc-108">Créez un cluster Azure HDInsight.</span><span class="sxs-lookup"><span data-stu-id="79cbc-108">Create an Azure HDInsight cluster.</span></span>
> * <span data-ttu-id="79cbc-109">Publiez votre application .NET pour Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="79cbc-109">Publish your .NET for Apache Spark app.</span></span>
> * <span data-ttu-id="79cbc-110">Créez et exécutez une action de script HDInsight.</span><span class="sxs-lookup"><span data-stu-id="79cbc-110">Create and run an HDInsight script action.</span></span>
> * <span data-ttu-id="79cbc-111">Exécutez un .NET pour Apache Spark application sur un cluster HDInsight.</span><span class="sxs-lookup"><span data-stu-id="79cbc-111">Run a .NET for Apache Spark app on an HDInsight cluster.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="79cbc-112">Prérequis</span><span class="sxs-lookup"><span data-stu-id="79cbc-112">Prerequisites</span></span>

<span data-ttu-id="79cbc-113">Avant de commencer, effectuez les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="79cbc-113">Before you start, do the following tasks:</span></span>

* <span data-ttu-id="79cbc-114">Si vous n’avez pas d’abonnement Azure, créez un [compte gratuit](https://azure.microsoft.com/free/dotnet/).</span><span class="sxs-lookup"><span data-stu-id="79cbc-114">If you don't have an Azure subscription, create a [free account](https://azure.microsoft.com/free/dotnet/).</span></span>
* <span data-ttu-id="79cbc-115">Connectez-vous au [portail Azure](https://portal.azure.com/).</span><span class="sxs-lookup"><span data-stu-id="79cbc-115">Sign in to the [Azure portal](https://portal.azure.com/).</span></span>
* <span data-ttu-id="79cbc-116">Installez Explorateur Stockage Azure sur votre ordinateur [Windows](https://go.microsoft.com/fwlink/?LinkId=708343&clcid=0x409), [Linux](https://go.microsoft.com/fwlink/?LinkId=722418&clcid=0x409)ou [MacOS](https://go.microsoft.com/fwlink/?LinkId=708342&clcid=0x409) .</span><span class="sxs-lookup"><span data-stu-id="79cbc-116">Install Azure Storage Explorer on your [Windows](https://go.microsoft.com/fwlink/?LinkId=708343&clcid=0x409), [Linux](https://go.microsoft.com/fwlink/?LinkId=722418&clcid=0x409), or [MacOS](https://go.microsoft.com/fwlink/?LinkId=708342&clcid=0x409) computer.</span></span>
* <span data-ttu-id="79cbc-117">Complétez le [.net pour Apache Spark-commencez dans](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) le didacticiel de 10 minutes.</span><span class="sxs-lookup"><span data-stu-id="79cbc-117">Complete the [.NET for Apache Spark - Get Started in 10-Minutes](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) tutorial.</span></span>

## <a name="access-your-storage-accounts"></a><span data-ttu-id="79cbc-118">Accéder à vos comptes de stockage</span><span class="sxs-lookup"><span data-stu-id="79cbc-118">Access your storage accounts</span></span>

1. <span data-ttu-id="79cbc-119">Ouvrez l’Explorateur de stockage Azure.</span><span class="sxs-lookup"><span data-stu-id="79cbc-119">Open Azure Storage Explorer.</span></span>

2. <span data-ttu-id="79cbc-120">Sélectionnez **Ajouter un compte** dans le menu de gauche, puis connectez-vous à votre compte Azure.</span><span class="sxs-lookup"><span data-stu-id="79cbc-120">Select **Add Account** on the left menu, and sign in to your Azure account.</span></span>

    ![Connectez-vous au compte Azure à partir de Explorateur Stockage](./media/hdinsight-deployment/signin-azure-storage-explorer.png)

   <span data-ttu-id="79cbc-122">Une fois que vous êtes connecté, vous devez voir tous les comptes de stockage dont vous disposez et toutes les ressources que vous avez téléchargées sur vos comptes de stockage.</span><span class="sxs-lookup"><span data-stu-id="79cbc-122">After you sign in, you should see all storage accounts you have and any resources you have uploaded to your storage accounts.</span></span>

## <a name="create-an-hdinsight-cluster"></a><span data-ttu-id="79cbc-123">Création d'un cluster HDInsight</span><span class="sxs-lookup"><span data-stu-id="79cbc-123">Create an HDInsight cluster</span></span>

> [!IMPORTANT]
> <span data-ttu-id="79cbc-124">La facturation des clusters HDInsight est calculée au prorata par minute, même si vous ne les utilisez pas.</span><span class="sxs-lookup"><span data-stu-id="79cbc-124">Billing for HDInsight clusters is prorated per minute, even if you're not using them.</span></span> <span data-ttu-id="79cbc-125">Veillez à supprimer votre cluster une fois que vous avez fini de l’utiliser.</span><span class="sxs-lookup"><span data-stu-id="79cbc-125">Be sure to delete your cluster after you have finished using it.</span></span> <span data-ttu-id="79cbc-126">Pour plus d’informations, consultez la section [nettoyage des ressources](#clean-up-resources) de ce didacticiel.</span><span class="sxs-lookup"><span data-stu-id="79cbc-126">For more information, see the [Clean up resources](#clean-up-resources) section of this tutorial.</span></span>

1. <span data-ttu-id="79cbc-127">Visitez le [portail Azure](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="79cbc-127">Visit the [Azure portal](https://portal.azure.com).</span></span>

2. <span data-ttu-id="79cbc-128">Sélectionnez **+ créer une ressource**.</span><span class="sxs-lookup"><span data-stu-id="79cbc-128">Select **+ Create a resource**.</span></span> <span data-ttu-id="79cbc-129">Ensuite, sélectionnez **HDInsight** dans la catégorie **Analytics** .</span><span class="sxs-lookup"><span data-stu-id="79cbc-129">Then, select **HDInsight** from the **Analytics** category.</span></span>

    ![Créer une ressource HDInsight à partir d’Portail Azure](./media/hdinsight-deployment/create-hdinsight-resource.png)

3. <span data-ttu-id="79cbc-131">Sous **Informations de base**, fournissez les valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="79cbc-131">Under **Basics**, provide the following values:</span></span>

    |<span data-ttu-id="79cbc-132">Propriété</span><span class="sxs-lookup"><span data-stu-id="79cbc-132">Property</span></span>  |<span data-ttu-id="79cbc-133">Description</span><span class="sxs-lookup"><span data-stu-id="79cbc-133">Description</span></span>  |
    |---------|---------|
    |<span data-ttu-id="79cbc-134">Abonnement</span><span class="sxs-lookup"><span data-stu-id="79cbc-134">Subscription</span></span>  | <span data-ttu-id="79cbc-135">Dans la liste déroulante, choisissez l’un de vos abonnements Azure actifs.</span><span class="sxs-lookup"><span data-stu-id="79cbc-135">From the drop-down, choose one of your active Azure subscriptions.</span></span> |
    |<span data-ttu-id="79cbc-136">Resource group</span><span class="sxs-lookup"><span data-stu-id="79cbc-136">Resource group</span></span> | <span data-ttu-id="79cbc-137">Indiquez si vous souhaitez créer un groupe de ressources Azure ou utiliser un groupe existant.</span><span class="sxs-lookup"><span data-stu-id="79cbc-137">Specify whether you want to create a new resource group or use an existing one.</span></span> <span data-ttu-id="79cbc-138">Un groupe de ressources est un conteneur réunissant les ressources associées d’une solution Azure.</span><span class="sxs-lookup"><span data-stu-id="79cbc-138">A resource group is a container that holds related resources for an Azure solution.</span></span> |
    |<span data-ttu-id="79cbc-139">Nom du cluster</span><span class="sxs-lookup"><span data-stu-id="79cbc-139">Cluster name</span></span> | <span data-ttu-id="79cbc-140">Attribuez un nom à votre cluster HDInsight Spark.</span><span class="sxs-lookup"><span data-stu-id="79cbc-140">Give a name to your HDInsight Spark cluster.</span></span>|
    |<span data-ttu-id="79cbc-141">Emplacement</span><span class="sxs-lookup"><span data-stu-id="79cbc-141">Location</span></span>   | <span data-ttu-id="79cbc-142">Sélectionnez l’emplacement du groupe de ressources.</span><span class="sxs-lookup"><span data-stu-id="79cbc-142">Select a location for the resource group.</span></span> <span data-ttu-id="79cbc-143">Le modèle utilise cet emplacement pour créer le cluster, ainsi que pour stocker le cluster par défaut.</span><span class="sxs-lookup"><span data-stu-id="79cbc-143">The template uses this location for creating the cluster as well as for the default cluster storage.</span></span> |
    |<span data-ttu-id="79cbc-144">Type de cluster</span><span class="sxs-lookup"><span data-stu-id="79cbc-144">Cluster type</span></span>| <span data-ttu-id="79cbc-145">Sélectionnez **Spark** comme type de cluster.</span><span class="sxs-lookup"><span data-stu-id="79cbc-145">Select **Spark** as the cluster type.</span></span>|
    |<span data-ttu-id="79cbc-146">Version du cluster</span><span class="sxs-lookup"><span data-stu-id="79cbc-146">Cluster version</span></span>|<span data-ttu-id="79cbc-147">Ce champ est rempli avec la version par défaut une fois que le type de cluster a été sélectionné.</span><span class="sxs-lookup"><span data-stu-id="79cbc-147">This field will autopopulate with the default version once the cluster type has been selected.</span></span> <span data-ttu-id="79cbc-148">Sélectionnez une version 2,3 ou 2,4 de Spark.</span><span class="sxs-lookup"><span data-stu-id="79cbc-148">Select a 2.3 or 2.4 version of Spark.</span></span>|
    |<span data-ttu-id="79cbc-149">Nom d’utilisateur de connexion au cluster</span><span class="sxs-lookup"><span data-stu-id="79cbc-149">Cluster login username</span></span>| <span data-ttu-id="79cbc-150">Entrez le nom d’utilisateur de connexion au cluster.</span><span class="sxs-lookup"><span data-stu-id="79cbc-150">Enter the cluster login username.</span></span>  <span data-ttu-id="79cbc-151">Le nom par défaut est *admin*.</span><span class="sxs-lookup"><span data-stu-id="79cbc-151">The default name is *admin*.</span></span> |
    |<span data-ttu-id="79cbc-152">Mot de passe de connexion au cluster</span><span class="sxs-lookup"><span data-stu-id="79cbc-152">Cluster login password</span></span>| <span data-ttu-id="79cbc-153">Entrez un mot de passe de connexion.</span><span class="sxs-lookup"><span data-stu-id="79cbc-153">Enter any login password.</span></span> |
    |<span data-ttu-id="79cbc-154">Nom d’utilisateur SSH (Secure Shell)</span><span class="sxs-lookup"><span data-stu-id="79cbc-154">Secure Shell (SSH) username</span></span>| <span data-ttu-id="79cbc-155">Entrez le nom d’utilisateur SSH.</span><span class="sxs-lookup"><span data-stu-id="79cbc-155">Enter the SSH username.</span></span> <span data-ttu-id="79cbc-156">Par défaut, ce compte a le même mot de passe que le compte *Nom d’utilisateur de connexion au cluster*.</span><span class="sxs-lookup"><span data-stu-id="79cbc-156">By default, this account shares the same password as the *Cluster Login username* account.</span></span> |

4. <span data-ttu-id="79cbc-157">Sélectionnez **suivant : stockage >>** pour accéder à la page de **stockage** .</span><span class="sxs-lookup"><span data-stu-id="79cbc-157">Select **Next: Storage >>** to continue to the **Storage** page.</span></span> <span data-ttu-id="79cbc-158">Sous **Stockage**, fournissez les valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="79cbc-158">Under **Storage**, provide the following values:</span></span>

    |<span data-ttu-id="79cbc-159">Propriété</span><span class="sxs-lookup"><span data-stu-id="79cbc-159">Property</span></span>  |<span data-ttu-id="79cbc-160">Description</span><span class="sxs-lookup"><span data-stu-id="79cbc-160">Description</span></span>  |
    |---------|---------|
    |<span data-ttu-id="79cbc-161">Type de stockage principal</span><span class="sxs-lookup"><span data-stu-id="79cbc-161">Primary storage type</span></span>|<span data-ttu-id="79cbc-162">Utilisez la valeur par défaut : **Stockage Azure**.</span><span class="sxs-lookup"><span data-stu-id="79cbc-162">Use the default value **Azure Storage**.</span></span>|
    |<span data-ttu-id="79cbc-163">Méthode de sélection</span><span class="sxs-lookup"><span data-stu-id="79cbc-163">Selection method</span></span>|<span data-ttu-id="79cbc-164">Utilisez la valeur par défaut : **Sélectionner dans la liste**.</span><span class="sxs-lookup"><span data-stu-id="79cbc-164">Use the default value **Select from list**.</span></span>|
    |<span data-ttu-id="79cbc-165">Compte de stockage principal</span><span class="sxs-lookup"><span data-stu-id="79cbc-165">Primary storage account</span></span>|<span data-ttu-id="79cbc-166">Choisissez votre abonnement et l’un de vos comptes de stockage actifs au sein de cet abonnement.</span><span class="sxs-lookup"><span data-stu-id="79cbc-166">Choose your subscription and one of your active storage accounts within that subscription.</span></span>|
    |<span data-ttu-id="79cbc-167">Conteneur</span><span class="sxs-lookup"><span data-stu-id="79cbc-167">Container</span></span>|<span data-ttu-id="79cbc-168">Ce conteneur est le conteneur d’objets BLOB spécifique dans votre compte de stockage où votre cluster recherche des fichiers pour exécuter votre application dans le Cloud.</span><span class="sxs-lookup"><span data-stu-id="79cbc-168">This container is the specific blob container in your storage account where your cluster looks for files to run your app in the cloud.</span></span> <span data-ttu-id="79cbc-169">Vous pouvez lui attribuer un nom disponible.</span><span class="sxs-lookup"><span data-stu-id="79cbc-169">You can give it any available name.</span></span>|

5. <span data-ttu-id="79cbc-170">Sous **Vérifier + créer**, sélectionnez **Créer**.</span><span class="sxs-lookup"><span data-stu-id="79cbc-170">Under **Review + create**, select **Create**.</span></span> <span data-ttu-id="79cbc-171">La création du cluster prend environ 20 minutes.</span><span class="sxs-lookup"><span data-stu-id="79cbc-171">It takes about 20 minutes to create the cluster.</span></span> <span data-ttu-id="79cbc-172">Le cluster doit être créé avant que vous puissiez passer à l’étape suivante.</span><span class="sxs-lookup"><span data-stu-id="79cbc-172">The cluster must be created before you can continue to the next step.</span></span>

## <a name="publish-your-app"></a><span data-ttu-id="79cbc-173">Publier votre application</span><span class="sxs-lookup"><span data-stu-id="79cbc-173">Publish your app</span></span>

<span data-ttu-id="79cbc-174">Ensuite, vous publiez le *mySparkApp* créé dans [.net pour Apache Spark-bien démarrer dans un didacticiel de 10 minutes](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) , qui donne à votre cluster Spark un accès à tous les fichiers dont il a besoin pour exécuter votre application.</span><span class="sxs-lookup"><span data-stu-id="79cbc-174">Next, you publish the *mySparkApp* created in the [.NET for Apache Spark - Get Started in 10-Minutes](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) tutorial, which gives your Spark cluster access to all the files it needs to run your app.</span></span>

1. <span data-ttu-id="79cbc-175">Exécutez les commandes suivantes pour publier le *mySparkApp*:</span><span class="sxs-lookup"><span data-stu-id="79cbc-175">Run the following commands to publish the *mySparkApp*:</span></span>

   <span data-ttu-id="79cbc-176">**Sur Windows :**</span><span class="sxs-lookup"><span data-stu-id="79cbc-176">**On Windows:**</span></span>

   ```dotnetcli
   cd mySparkApp
   dotnet publish -c Release -f netcoreapp3.0 -r ubuntu.16.04-x64
   ```

   <span data-ttu-id="79cbc-177">**Sur Linux :**</span><span class="sxs-lookup"><span data-stu-id="79cbc-177">**On Linux:**</span></span>

   ```bash
   cd mySparkApp
   foo@bar:~/path/to/app$ dotnet publish -c Release -f netcoreapp3.0 -r ubuntu.16.04-x64
   ```

2. <span data-ttu-id="79cbc-178">Effectuez les tâches suivantes pour compresser les fichiers de votre application publiée afin de pouvoir les télécharger facilement vers votre cluster HDInsight.</span><span class="sxs-lookup"><span data-stu-id="79cbc-178">Do the following tasks to zip your published app files so that you can easily upload them to your HDInsight cluster.</span></span>

   <span data-ttu-id="79cbc-179">**Sur Windows :**</span><span class="sxs-lookup"><span data-stu-id="79cbc-179">**On Windows:**</span></span>

   <span data-ttu-id="79cbc-180">Accédez à *mySparkApp/bin/Release/netcoreapp 3.0/Ubuntu. 16.04-x64*.</span><span class="sxs-lookup"><span data-stu-id="79cbc-180">Navigate to *mySparkApp/bin/Release/netcoreapp3.0/ubuntu.16.04-x64*.</span></span> <span data-ttu-id="79cbc-181">Ensuite, cliquez avec le bouton droit sur le dossier de **publication** et sélectionnez **Envoyer vers > dossier compressé (zippé)**.</span><span class="sxs-lookup"><span data-stu-id="79cbc-181">Then, right-click on **Publish** folder and select **Send to > Compressed (zipped) folder**.</span></span> <span data-ttu-id="79cbc-182">Nommez le nouveau dossier **Publish. zip**.</span><span class="sxs-lookup"><span data-stu-id="79cbc-182">Name the new folder **publish.zip**.</span></span>

   <span data-ttu-id="79cbc-183">**Sur Linux, exécutez la commande ci-dessous :**</span><span class="sxs-lookup"><span data-stu-id="79cbc-183">**On Linux, run the following command:**</span></span>

   ```bash
   zip -r publish.zip
   ```

## <a name="upload-files-to-azure"></a><span data-ttu-id="79cbc-184">Charger des fichiers dans Azure</span><span class="sxs-lookup"><span data-stu-id="79cbc-184">Upload files to Azure</span></span>

<span data-ttu-id="79cbc-185">Ensuite, vous utilisez la Explorateur Stockage Azure pour télécharger les cinq fichiers suivants dans le conteneur d’objets BLOB que vous avez choisi pour le stockage de votre cluster :</span><span class="sxs-lookup"><span data-stu-id="79cbc-185">Next, you use the Azure Storage Explorer to upload the following five files to the blob container you chose for your cluster's storage:</span></span>

* <span data-ttu-id="79cbc-186">Microsoft. Spark. Worker</span><span class="sxs-lookup"><span data-stu-id="79cbc-186">Microsoft.Spark.Worker</span></span>
* <span data-ttu-id="79cbc-187">install-worker.sh</span><span class="sxs-lookup"><span data-stu-id="79cbc-187">install-worker.sh</span></span>
* <span data-ttu-id="79cbc-188">publier le fichier. zip</span><span class="sxs-lookup"><span data-stu-id="79cbc-188">publish.zip</span></span>
* <span data-ttu-id="79cbc-189">Microsoft-Spark-2.3. x-0.3.0. jar</span><span class="sxs-lookup"><span data-stu-id="79cbc-189">microsoft-spark-2.3.x-0.3.0.jar</span></span>
* <span data-ttu-id="79cbc-190">Input. txt.</span><span class="sxs-lookup"><span data-stu-id="79cbc-190">input.txt.</span></span>

1. <span data-ttu-id="79cbc-191">Ouvrez Explorateur Stockage Azure et accédez à votre compte de stockage dans le menu de gauche.</span><span class="sxs-lookup"><span data-stu-id="79cbc-191">Open Azure Storage Explorer and navigate to your storage account from the left menu.</span></span> <span data-ttu-id="79cbc-192">Explorez le conteneur d’objets BLOB de votre cluster sous **conteneurs d’objets BLOB** dans votre compte de stockage.</span><span class="sxs-lookup"><span data-stu-id="79cbc-192">Drill down to the blob container for your cluster under **Blob Containers** in your storage account.</span></span>

2. <span data-ttu-id="79cbc-193">*Microsoft. Spark. Worker* aide Apache Spark exécuter votre application, telle que les fonctions définies par l’utilisateur (UDF) que vous avez peut-être écrites.</span><span class="sxs-lookup"><span data-stu-id="79cbc-193">*Microsoft.Spark.Worker* helps Apache Spark execute your app, such as any user-defined functions (UDFs) you may have written.</span></span> <span data-ttu-id="79cbc-194">Téléchargez [Microsoft. Spark. Worker](https://github.com/dotnet/spark/releases/download/v0.3.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.3.0.tar.gz).</span><span class="sxs-lookup"><span data-stu-id="79cbc-194">Download [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases/download/v0.3.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.3.0.tar.gz).</span></span> <span data-ttu-id="79cbc-195">Ensuite, sélectionnez **Télécharger** dans Explorateur stockage Azure pour charger le processus de travail.</span><span class="sxs-lookup"><span data-stu-id="79cbc-195">Then, select **Upload** in Azure Storage Explorer to upload the worker.</span></span>

   ![Télécharger des fichiers vers Explorateur Stockage Azure](./media/hdinsight-deployment/upload-files-to-storage.png)

3. <span data-ttu-id="79cbc-197">Le *install-Worker.sh* est un script qui vous permet de copier .net pour Apache Spark fichiers dépendants dans les nœuds de votre cluster.</span><span class="sxs-lookup"><span data-stu-id="79cbc-197">The *install-worker.sh* is a script that lets you copy .NET for Apache Spark dependent files into the nodes of your cluster.</span></span>

   <span data-ttu-id="79cbc-198">Créez un nouveau fichier nommé **install-Worker.sh** votre ordinateur local, puis collez le [contenu install-Worker.sh](https://raw.githubusercontent.com/dotnet/spark/master/deployment/install-worker.sh) situé sur GitHub.</span><span class="sxs-lookup"><span data-stu-id="79cbc-198">Create a new file named **install-worker.sh** your local computer, and paste the [install-worker.sh contents](https://raw.githubusercontent.com/dotnet/spark/master/deployment/install-worker.sh) located on GitHub.</span></span> <span data-ttu-id="79cbc-199">Ensuite, chargez *install-Worker.sh* dans votre conteneur d’objets BLOB.</span><span class="sxs-lookup"><span data-stu-id="79cbc-199">Then, upload *install-worker.sh* to your blob container.</span></span>

4. <span data-ttu-id="79cbc-200">Votre cluster a besoin du fichier publish. zip qui contient les fichiers publiés de votre application.</span><span class="sxs-lookup"><span data-stu-id="79cbc-200">Your cluster needs the publish.zip file that contains your app's published files.</span></span> <span data-ttu-id="79cbc-201">Accédez à votre dossier publié, **mySparkApp/bin/Release/netcoreapp 3.0/Ubuntu. 16.04-x64**, puis recherchez **Publish. zip**.</span><span class="sxs-lookup"><span data-stu-id="79cbc-201">Navigate to your published folder, **mySparkApp/bin/Release/netcoreapp3.0/ubuntu.16.04-x64**, and locate **publish.zip**.</span></span> <span data-ttu-id="79cbc-202">Ensuite, téléchargez le fichier *Publish. zip* dans votre conteneur d’objets BLOB.</span><span class="sxs-lookup"><span data-stu-id="79cbc-202">Then upload *publish.zip* to your blob container.</span></span>

5. <span data-ttu-id="79cbc-203">Votre cluster a besoin du code d’application qui a été empaqueté dans un fichier jar.</span><span class="sxs-lookup"><span data-stu-id="79cbc-203">Your cluster needs the application code that was packaged into a jar file.</span></span> <span data-ttu-id="79cbc-204">Accédez à votre dossier publié, **mySparkApp/bin/Release/netcoreapp 3.0/Ubuntu. 16.04-x64**, puis localisez **Microsoft-Spark-2.3. x-0.3.0. jar**.</span><span class="sxs-lookup"><span data-stu-id="79cbc-204">Navigate to your published folder, **mySparkApp/bin/Release/netcoreapp3.0/ubuntu.16.04-x64**, and locate **microsoft-spark-2.3.x-0.3.0.jar**.</span></span> <span data-ttu-id="79cbc-205">Ensuite, chargez le fichier jar dans votre conteneur d’objets BLOB.</span><span class="sxs-lookup"><span data-stu-id="79cbc-205">Then, upload the jar file to your blob container.</span></span>

   <span data-ttu-id="79cbc-206">Il peut y avoir plusieurs fichiers. jar (pour les versions 2.3. x et 2.4. x de Spark).</span><span class="sxs-lookup"><span data-stu-id="79cbc-206">There may be multiple .jar files (for versions 2.3.x and 2.4.x of Spark).</span></span> <span data-ttu-id="79cbc-207">Vous devez choisir le fichier. jar qui correspond à la version de Spark que vous avez choisie lors de la création du cluster.</span><span class="sxs-lookup"><span data-stu-id="79cbc-207">You need to choose the .jar file that matches the version of Spark you chose during cluster creation.</span></span> <span data-ttu-id="79cbc-208">Par exemple, choisissez *Microsoft-Spark-2.3. x-0.3.0. jar* si vous avez choisi Spark 2.3.2 lors de la création du cluster.</span><span class="sxs-lookup"><span data-stu-id="79cbc-208">For example, choose *microsoft-spark-2.3.x-0.3.0.jar* if you chose Spark 2.3.2 during cluster creation.</span></span>

6. <span data-ttu-id="79cbc-209">Votre cluster a besoin de l’entrée de votre application.</span><span class="sxs-lookup"><span data-stu-id="79cbc-209">Your cluster needs the input to your app.</span></span> <span data-ttu-id="79cbc-210">Accédez à votre répertoire **mySparkApp** et recherchez **Input. txt**.</span><span class="sxs-lookup"><span data-stu-id="79cbc-210">Navigate to your **mySparkApp** directory and locate **input.txt**.</span></span> <span data-ttu-id="79cbc-211">Chargez votre fichier d’entrée dans le répertoire **User/sshuser** dans votre conteneur d’objets BLOB.</span><span class="sxs-lookup"><span data-stu-id="79cbc-211">Upload your input file to the **user/sshuser** directory in your blob container.</span></span> <span data-ttu-id="79cbc-212">Vous allez vous connecter à votre cluster via SSH, et ce dossier est l’emplacement où votre cluster recherche son entrée.</span><span class="sxs-lookup"><span data-stu-id="79cbc-212">You will be connecting to your cluster through ssh, and this folder is where your cluster looks for its input.</span></span> <span data-ttu-id="79cbc-213">Le fichier *Input. txt* est le seul fichier chargé dans un répertoire spécifique.</span><span class="sxs-lookup"><span data-stu-id="79cbc-213">The *input.txt* file is the only file uploaded to a specific directory.</span></span>

## <a name="run-the-hdinsight-script-action"></a><span data-ttu-id="79cbc-214">Exécuter l’action de script HDInsight</span><span class="sxs-lookup"><span data-stu-id="79cbc-214">Run the HDInsight script action</span></span>

<span data-ttu-id="79cbc-215">Une fois que votre cluster est en cours d’exécution et que vous avez téléchargé vos fichiers dans Azure, vous exécutez le script **install-Worker.sh** sur le cluster.</span><span class="sxs-lookup"><span data-stu-id="79cbc-215">Once your cluster is running and you've uploaded your files to Azure, you run the **install-worker.sh** script on the cluster.</span></span>

1. <span data-ttu-id="79cbc-216">Accédez à votre cluster HDInsight Spark dans Portail Azure, puis sélectionnez **actions de script**.</span><span class="sxs-lookup"><span data-stu-id="79cbc-216">Navigate to your HDInsight Spark cluster in Azure portal, and then select **Script actions**.</span></span>

2. <span data-ttu-id="79cbc-217">Sélectionnez **+ soumettre nouveau** et fournissez les valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="79cbc-217">Select **+ Submit new** and provide the following values:</span></span>

   |<span data-ttu-id="79cbc-218">Propriété</span><span class="sxs-lookup"><span data-stu-id="79cbc-218">Property</span></span>  |<span data-ttu-id="79cbc-219">Description</span><span class="sxs-lookup"><span data-stu-id="79cbc-219">Description</span></span>  |
   |---------|---------|
   | <span data-ttu-id="79cbc-220">Type de script</span><span class="sxs-lookup"><span data-stu-id="79cbc-220">Script type</span></span> |<span data-ttu-id="79cbc-221">Personnalisé</span><span class="sxs-lookup"><span data-stu-id="79cbc-221">Custom</span></span>|
   | <span data-ttu-id="79cbc-222">Nom</span><span class="sxs-lookup"><span data-stu-id="79cbc-222">Name</span></span> | <span data-ttu-id="79cbc-223">Installer Worker</span><span class="sxs-lookup"><span data-stu-id="79cbc-223">Install Worker</span></span>|
   | <span data-ttu-id="79cbc-224">URI de script bash</span><span class="sxs-lookup"><span data-stu-id="79cbc-224">Bash script URI</span></span> |https://mystorageaccount.blob.core.windows.net/mycontainer/install-worker.sh </br> <span data-ttu-id="79cbc-225">Pour confirmer cet URI, cliquez avec le bouton droit sur install-worker.sh dans Explorateur Stockage Azure, puis sélectionnez Propriétés.</span><span class="sxs-lookup"><span data-stu-id="79cbc-225">To confirm this URI, right-click on install-worker.sh in Azure Storage Explorer and select Properties.</span></span> |
   | <span data-ttu-id="79cbc-226">Type(s) de nœud</span><span class="sxs-lookup"><span data-stu-id="79cbc-226">Node type(s)</span></span>| <span data-ttu-id="79cbc-227">Worker</span><span class="sxs-lookup"><span data-stu-id="79cbc-227">Worker</span></span>|
   | <span data-ttu-id="79cbc-228">Paramètres</span><span class="sxs-lookup"><span data-stu-id="79cbc-228">Parameters</span></span> | <span data-ttu-id="79cbc-229">azure</span><span class="sxs-lookup"><span data-stu-id="79cbc-229">azure</span></span> </br> wasbs://mycontainer@myStorageAccount.blob.core.windows.net/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz </br> <span data-ttu-id="79cbc-230">/usr/local/bin</span><span class="sxs-lookup"><span data-stu-id="79cbc-230">/usr/local/bin</span></span>

3. <span data-ttu-id="79cbc-231">Sélectionnez **créer** pour soumettre votre script.</span><span class="sxs-lookup"><span data-stu-id="79cbc-231">Select **Create** to submit your script.</span></span>

## <a name="run-your-app"></a><span data-ttu-id="79cbc-232">Exécutez l'application.</span><span class="sxs-lookup"><span data-stu-id="79cbc-232">Run your app</span></span>

1. <span data-ttu-id="79cbc-233">Accédez à votre cluster HDInsight Spark dans Portail Azure, puis sélectionnez **SSH + connexion au cluster**.</span><span class="sxs-lookup"><span data-stu-id="79cbc-233">Navigate to your HDInsight Spark cluster in Azure portal, and then select **SSH + Cluster login**.</span></span>

2. <span data-ttu-id="79cbc-234">Copiez les informations de connexion SSH et collez la connexion dans un terminal.</span><span class="sxs-lookup"><span data-stu-id="79cbc-234">Copy the ssh login information and paste the login into a terminal.</span></span> <span data-ttu-id="79cbc-235">Connectez-vous à votre cluster à l’aide du mot de passe que vous avez défini lors de la création du cluster.</span><span class="sxs-lookup"><span data-stu-id="79cbc-235">Sign in to your cluster using the password you set during cluster creation.</span></span> <span data-ttu-id="79cbc-236">Vous devriez voir des messages vous préversant Ubuntu et Spark.</span><span class="sxs-lookup"><span data-stu-id="79cbc-236">You should see messages welcoming you to Ubuntu and Spark.</span></span>

3. <span data-ttu-id="79cbc-237">Utilisez la commande **Spark-Submit** pour exécuter votre application sur votre cluster HDInsight.</span><span class="sxs-lookup"><span data-stu-id="79cbc-237">Use the **spark-submit** command to run your app on your HDInsight cluster.</span></span> <span data-ttu-id="79cbc-238">N’oubliez pas de remplacer **mycontainer** et **mystorageaccount** dans l’exemple de script par les noms réels de votre conteneur d’objets BLOB et de votre compte de stockage.</span><span class="sxs-lookup"><span data-stu-id="79cbc-238">Remember to replace **mycontainer** and **mystorageaccount** in the example script with the actual names of your blob container and storage account.</span></span>

   ```bash
   $SPARK_HOME/bin/spark-submit \
   --master yarn \
   --class org.apache.spark.deploy.dotnet.DotnetRunner \
   wasbs://mycontainer@mystorageaccount.blob.core.windows.net/microsoft-spark-2.3.x-0.6.0.jar \
   wasbs://mycontainer@mystorageaccount.blob.core.windows.net/publish.zip mySparkApp
   ```

   <span data-ttu-id="79cbc-239">Lorsque votre application s’exécute, vous voyez le même tableau de nombre de mots que l’exécution locale de prise en main écrite dans la console.</span><span class="sxs-lookup"><span data-stu-id="79cbc-239">When your app runs, you see the same word count table from the getting started local run written to the console.</span></span> <span data-ttu-id="79cbc-240">Félicitations, vous avez exécuté votre première application .NET pour Apache Spark dans le Cloud !</span><span class="sxs-lookup"><span data-stu-id="79cbc-240">Congratulations, you've run your first .NET for Apache Spark application in the cloud!</span></span>

## <a name="clean-up-resources"></a><span data-ttu-id="79cbc-241">Nettoyer les ressources</span><span class="sxs-lookup"><span data-stu-id="79cbc-241">Clean up resources</span></span>

<span data-ttu-id="79cbc-242">HDInsight enregistre vos données dans le stockage Azure, ce qui vous permet de supprimer en toute sécurité un cluster lorsqu’il n’est pas utilisé.</span><span class="sxs-lookup"><span data-stu-id="79cbc-242">HDInsight saves your data in Azure Storage, so you can safely delete a cluster when it is not in use.</span></span> <span data-ttu-id="79cbc-243">Vous devez également payer pour un cluster HDInsight, même lorsque vous ne l’utilisez pas.</span><span class="sxs-lookup"><span data-stu-id="79cbc-243">You are also charged for an HDInsight cluster, even when it is not in use.</span></span> <span data-ttu-id="79cbc-244">Étant donné que les frais pour le cluster sont bien plus élevés que les frais de stockage, économique, mieux vaut supprimer les clusters lorsqu’ils ne sont pas utilisés.</span><span class="sxs-lookup"><span data-stu-id="79cbc-244">Since the charges for the cluster are many times more than the charges for storage, it makes economic sense to delete clusters when they are not in use.</span></span>

<span data-ttu-id="79cbc-245">Vous pouvez également sélectionner le nom du groupe de ressources pour ouvrir la page du groupe de ressources, puis sélectionner **Supprimer le groupe de ressources**.</span><span class="sxs-lookup"><span data-stu-id="79cbc-245">You can also select the resource group name to open the resource group page, and then select **Delete resource group**.</span></span> <span data-ttu-id="79cbc-246">En supprimant le groupe de ressources, vous supprimez le cluster HDInsight Spark et le compte de stockage par défaut.</span><span class="sxs-lookup"><span data-stu-id="79cbc-246">By deleting the resource group, you delete both the HDInsight Spark cluster, and the default storage account.</span></span>

## <a name="next-steps"></a><span data-ttu-id="79cbc-247">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="79cbc-247">Next steps</span></span>

<span data-ttu-id="79cbc-248">Dans ce tutoriel, vous avez déployé votre application .NET pour Apache Spark sur Azure HDInsight.</span><span class="sxs-lookup"><span data-stu-id="79cbc-248">In this tutorial, you deployed your .NET for Apache Spark application to Azure HDInsight.</span></span> <span data-ttu-id="79cbc-249">Pour plus d’informations sur HDInsight, consultez la documentation d’Azure HDInsight.</span><span class="sxs-lookup"><span data-stu-id="79cbc-249">To learn more about HDInsight, continue to the Azure HDInsight Documentation.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="79cbc-250">Documentation Azure HDInsight</span><span class="sxs-lookup"><span data-stu-id="79cbc-250">Azure HDInsight Documentation</span></span>](https://docs.microsoft.com/azure/hdinsight/)
