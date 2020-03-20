---
title: Déployer une application .NET pour Apache Spark sur Azure HDInsight
description: Découvrez comment déployer une application .NET pour Apache Spark sur HDInsight.
ms.date: 01/23/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 77b57463375c36444532bdd383ec4b3bfe3ab056
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "77504164"
---
# <a name="tutorial-deploy-a-net-for-apache-spark-application-to-azure-hdinsight"></a><span data-ttu-id="ffbdc-103">Tutorial: Déployer une application .NET pour Apache Spark à Azure HDInsight</span><span class="sxs-lookup"><span data-stu-id="ffbdc-103">Tutorial: Deploy a .NET for Apache Spark application to Azure HDInsight</span></span>

<span data-ttu-id="ffbdc-104">Ce tutoriel vous apprend à déployer votre application .NET pour Apache Spark dans le cloud via un cluster Azure HDInsight.</span><span class="sxs-lookup"><span data-stu-id="ffbdc-104">This tutorial teaches you how to deploy your .NET for Apache Spark app to the cloud through an Azure HDInsight cluster.</span></span> <span data-ttu-id="ffbdc-105">HDInsight facilite la création et la configuration d’un cluster Spark à Azure puisque les clusters Spark dans HDInsight sont compatibles avec Azure Storage et Azure Data Lake Storage.</span><span class="sxs-lookup"><span data-stu-id="ffbdc-105">HDInsight makes it easier to create and configure a Spark cluster in Azure since Spark clusters in HDInsight are compatible with Azure Storage and Azure Data Lake Storage.</span></span>

<span data-ttu-id="ffbdc-106">Dans ce tutoriel, vous allez apprendre à :</span><span class="sxs-lookup"><span data-stu-id="ffbdc-106">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="ffbdc-107">Accédez à vos comptes de stockage en utilisant Azure Storage Explorer.</span><span class="sxs-lookup"><span data-stu-id="ffbdc-107">Access your storage accounts using Azure Storage Explorer.</span></span>
> * <span data-ttu-id="ffbdc-108">Créez un cluster Azure HDInsight.</span><span class="sxs-lookup"><span data-stu-id="ffbdc-108">Create an Azure HDInsight cluster.</span></span>
> * <span data-ttu-id="ffbdc-109">Publiez votre application .NET pour Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="ffbdc-109">Publish your .NET for Apache Spark app.</span></span>
> * <span data-ttu-id="ffbdc-110">Créez et exécutez une action de script HDInsight.</span><span class="sxs-lookup"><span data-stu-id="ffbdc-110">Create and run an HDInsight script action.</span></span>
> * <span data-ttu-id="ffbdc-111">Exécutez une application .NET pour Apache Spark sur un cluster HDInsight.</span><span class="sxs-lookup"><span data-stu-id="ffbdc-111">Run a .NET for Apache Spark app on an HDInsight cluster.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ffbdc-112">Conditions préalables requises</span><span class="sxs-lookup"><span data-stu-id="ffbdc-112">Prerequisites</span></span>

<span data-ttu-id="ffbdc-113">Avant de commencer, faites les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="ffbdc-113">Before you start, do the following tasks:</span></span>

* <span data-ttu-id="ffbdc-114">Si vous n’avez pas d’abonnement Azure, créez un [compte gratuit](https://azure.microsoft.com/free/).</span><span class="sxs-lookup"><span data-stu-id="ffbdc-114">If you don't have an Azure subscription, create a [free account](https://azure.microsoft.com/free/).</span></span>
* <span data-ttu-id="ffbdc-115">Connectez-vous au [portail Azure](https://portal.azure.com/).</span><span class="sxs-lookup"><span data-stu-id="ffbdc-115">Sign in to the [Azure portal](https://portal.azure.com/).</span></span>
* <span data-ttu-id="ffbdc-116">Installez Azure Storage Explorer sur votre [ordinateur Windows,](https://go.microsoft.com/fwlink/?LinkId=708343&clcid=0x409) [Linux](https://go.microsoft.com/fwlink/?LinkId=722418&clcid=0x409)ou [MacOS.](https://go.microsoft.com/fwlink/?LinkId=708342&clcid=0x409)</span><span class="sxs-lookup"><span data-stu-id="ffbdc-116">Install Azure Storage Explorer on your [Windows](https://go.microsoft.com/fwlink/?LinkId=708343&clcid=0x409), [Linux](https://go.microsoft.com/fwlink/?LinkId=722418&clcid=0x409), or [MacOS](https://go.microsoft.com/fwlink/?LinkId=708342&clcid=0x409) computer.</span></span>
* <span data-ttu-id="ffbdc-117">Complétez le [.NET pour Apache Spark - Get Started in 10-Minutes](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) tutorial.</span><span class="sxs-lookup"><span data-stu-id="ffbdc-117">Complete the [.NET for Apache Spark - Get Started in 10-Minutes](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) tutorial.</span></span>

## <a name="access-your-storage-accounts"></a><span data-ttu-id="ffbdc-118">Accédez à vos comptes de stockage</span><span class="sxs-lookup"><span data-stu-id="ffbdc-118">Access your storage accounts</span></span>

1. <span data-ttu-id="ffbdc-119">Ouvrez l’Explorateur de stockage Azure.</span><span class="sxs-lookup"><span data-stu-id="ffbdc-119">Open Azure Storage Explorer.</span></span>

2. <span data-ttu-id="ffbdc-120">Sélectionnez **Ajouter le compte** sur le menu gauche et connectez-vous à votre compte Azure.</span><span class="sxs-lookup"><span data-stu-id="ffbdc-120">Select **Add Account** on the left menu, and sign in to your Azure account.</span></span>

    ![Connectez-vous au compte Azure de Storage Explorer](./media/hdinsight-deployment/signin-azure-storage-explorer.png)

   <span data-ttu-id="ffbdc-122">Après votre connexion, vous devriez voir tous les comptes de stockage que vous avez et toutes les ressources que vous avez téléchargées sur vos comptes de stockage.</span><span class="sxs-lookup"><span data-stu-id="ffbdc-122">After you sign in, you should see all storage accounts you have and any resources you have uploaded to your storage accounts.</span></span>

## <a name="create-an-hdinsight-cluster"></a><span data-ttu-id="ffbdc-123">Création d'un cluster HDInsight</span><span class="sxs-lookup"><span data-stu-id="ffbdc-123">Create an HDInsight cluster</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ffbdc-124">La facturation des clusters HDInsight est prorated par minute, même si vous ne les utilisez pas.</span><span class="sxs-lookup"><span data-stu-id="ffbdc-124">Billing for HDInsight clusters is prorated per minute, even if you're not using them.</span></span> <span data-ttu-id="ffbdc-125">Veillez à supprimer votre cluster une fois que vous avez fini de l’utiliser.</span><span class="sxs-lookup"><span data-stu-id="ffbdc-125">Be sure to delete your cluster after you have finished using it.</span></span> <span data-ttu-id="ffbdc-126">Pour plus d’informations, consultez la section [Ressources Nettoyage](#clean-up-resources) de ce tutoriel.</span><span class="sxs-lookup"><span data-stu-id="ffbdc-126">For more information, see the [Clean up resources](#clean-up-resources) section of this tutorial.</span></span>

1. <span data-ttu-id="ffbdc-127">Visitez le [portail Azure](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="ffbdc-127">Visit the [Azure portal](https://portal.azure.com).</span></span>

2. <span data-ttu-id="ffbdc-128">Sélectionnez **et créez une ressource**.</span><span class="sxs-lookup"><span data-stu-id="ffbdc-128">Select **+ Create a resource**.</span></span> <span data-ttu-id="ffbdc-129">Ensuite, sélectionnez **HDInsight** de la catégorie **Analytics.**</span><span class="sxs-lookup"><span data-stu-id="ffbdc-129">Then, select **HDInsight** from the **Analytics** category.</span></span>

    ![Créer la ressource HDInsight à partir du portail Azure](./media/hdinsight-deployment/create-hdinsight-resource.png)

3. <span data-ttu-id="ffbdc-131">Sous **Informations de base**, fournissez les valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="ffbdc-131">Under **Basics**, provide the following values:</span></span>

    |<span data-ttu-id="ffbdc-132">Propriété</span><span class="sxs-lookup"><span data-stu-id="ffbdc-132">Property</span></span>  |<span data-ttu-id="ffbdc-133">Description</span><span class="sxs-lookup"><span data-stu-id="ffbdc-133">Description</span></span>  |
    |---------|---------|
    |<span data-ttu-id="ffbdc-134">Abonnement</span><span class="sxs-lookup"><span data-stu-id="ffbdc-134">Subscription</span></span>  | <span data-ttu-id="ffbdc-135">Dès le décrochage, choisissez l’un de vos abonnements Azure actifs.</span><span class="sxs-lookup"><span data-stu-id="ffbdc-135">From the drop-down, choose one of your active Azure subscriptions.</span></span> |
    |<span data-ttu-id="ffbdc-136">Resource group</span><span class="sxs-lookup"><span data-stu-id="ffbdc-136">Resource group</span></span> | <span data-ttu-id="ffbdc-137">Indiquez si vous souhaitez créer un groupe de ressources Azure ou utiliser un groupe existant.</span><span class="sxs-lookup"><span data-stu-id="ffbdc-137">Specify whether you want to create a new resource group or use an existing one.</span></span> <span data-ttu-id="ffbdc-138">Un groupe de ressources est un conteneur réunissant les ressources associées d’une solution Azure.</span><span class="sxs-lookup"><span data-stu-id="ffbdc-138">A resource group is a container that holds related resources for an Azure solution.</span></span> |
    |<span data-ttu-id="ffbdc-139">Nom du cluster</span><span class="sxs-lookup"><span data-stu-id="ffbdc-139">Cluster name</span></span> | <span data-ttu-id="ffbdc-140">Attribuez un nom à votre cluster HDInsight Spark.</span><span class="sxs-lookup"><span data-stu-id="ffbdc-140">Give a name to your HDInsight Spark cluster.</span></span>|
    |<span data-ttu-id="ffbdc-141">Emplacement</span><span class="sxs-lookup"><span data-stu-id="ffbdc-141">Location</span></span>   | <span data-ttu-id="ffbdc-142">Sélectionnez l’emplacement du groupe de ressources.</span><span class="sxs-lookup"><span data-stu-id="ffbdc-142">Select a location for the resource group.</span></span> <span data-ttu-id="ffbdc-143">Le modèle utilise cet emplacement pour créer le cluster, ainsi que pour stocker le cluster par défaut.</span><span class="sxs-lookup"><span data-stu-id="ffbdc-143">The template uses this location for creating the cluster as well as for the default cluster storage.</span></span> |
    |<span data-ttu-id="ffbdc-144">Type de cluster</span><span class="sxs-lookup"><span data-stu-id="ffbdc-144">Cluster type</span></span>| <span data-ttu-id="ffbdc-145">Sélectionnez **Spark** comme type de cluster.</span><span class="sxs-lookup"><span data-stu-id="ffbdc-145">Select **Spark** as the cluster type.</span></span>|
    |<span data-ttu-id="ffbdc-146">Version du cluster</span><span class="sxs-lookup"><span data-stu-id="ffbdc-146">Cluster version</span></span>|<span data-ttu-id="ffbdc-147">Ce champ s’autopeuplera avec la version par défaut une fois que le type de cluster a été sélectionné.</span><span class="sxs-lookup"><span data-stu-id="ffbdc-147">This field will autopopulate with the default version once the cluster type has been selected.</span></span> <span data-ttu-id="ffbdc-148">Sélectionnez une version 2.3 ou 2.4 de Spark.</span><span class="sxs-lookup"><span data-stu-id="ffbdc-148">Select a 2.3 or 2.4 version of Spark.</span></span>|
    |<span data-ttu-id="ffbdc-149">Nom d’utilisateur de connexion au cluster</span><span class="sxs-lookup"><span data-stu-id="ffbdc-149">Cluster login username</span></span>| <span data-ttu-id="ffbdc-150">Entrez le nom d’utilisateur de connexion au cluster.</span><span class="sxs-lookup"><span data-stu-id="ffbdc-150">Enter the cluster login username.</span></span>  <span data-ttu-id="ffbdc-151">Le nom par défaut est *admin*.</span><span class="sxs-lookup"><span data-stu-id="ffbdc-151">The default name is *admin*.</span></span> |
    |<span data-ttu-id="ffbdc-152">Mot de passe de connexion au cluster</span><span class="sxs-lookup"><span data-stu-id="ffbdc-152">Cluster login password</span></span>| <span data-ttu-id="ffbdc-153">Entrez n’importe quel mot de passe de connexion.</span><span class="sxs-lookup"><span data-stu-id="ffbdc-153">Enter any login password.</span></span> |
    |<span data-ttu-id="ffbdc-154">Nom d’utilisateur SSH (Secure Shell)</span><span class="sxs-lookup"><span data-stu-id="ffbdc-154">Secure Shell (SSH) username</span></span>| <span data-ttu-id="ffbdc-155">Entrez le nom d’utilisateur SSH.</span><span class="sxs-lookup"><span data-stu-id="ffbdc-155">Enter the SSH username.</span></span> <span data-ttu-id="ffbdc-156">Par défaut, ce compte a le même mot de passe que le compte *Nom d’utilisateur de connexion au cluster*.</span><span class="sxs-lookup"><span data-stu-id="ffbdc-156">By default, this account shares the same password as the *Cluster Login username* account.</span></span> |

4. <span data-ttu-id="ffbdc-157">Sélectionnez **Suivant : Stockagez >>** pour continuer à la page de **stockage.**</span><span class="sxs-lookup"><span data-stu-id="ffbdc-157">Select **Next: Storage >>** to continue to the **Storage** page.</span></span> <span data-ttu-id="ffbdc-158">Sous **Stockage**, fournissez les valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="ffbdc-158">Under **Storage**, provide the following values:</span></span>

    |<span data-ttu-id="ffbdc-159">Propriété</span><span class="sxs-lookup"><span data-stu-id="ffbdc-159">Property</span></span>  |<span data-ttu-id="ffbdc-160">Description</span><span class="sxs-lookup"><span data-stu-id="ffbdc-160">Description</span></span>  |
    |---------|---------|
    |<span data-ttu-id="ffbdc-161">Type de stockage principal</span><span class="sxs-lookup"><span data-stu-id="ffbdc-161">Primary storage type</span></span>|<span data-ttu-id="ffbdc-162">Utilisez la valeur par défaut : **Stockage Azure**.</span><span class="sxs-lookup"><span data-stu-id="ffbdc-162">Use the default value **Azure Storage**.</span></span>|
    |<span data-ttu-id="ffbdc-163">Méthode de sélection</span><span class="sxs-lookup"><span data-stu-id="ffbdc-163">Selection method</span></span>|<span data-ttu-id="ffbdc-164">Utilisez la valeur par défaut : **Sélectionner dans la liste**.</span><span class="sxs-lookup"><span data-stu-id="ffbdc-164">Use the default value **Select from list**.</span></span>|
    |<span data-ttu-id="ffbdc-165">Compte de stockage principal</span><span class="sxs-lookup"><span data-stu-id="ffbdc-165">Primary storage account</span></span>|<span data-ttu-id="ffbdc-166">Choisissez votre abonnement et l’un de vos comptes de stockage actifs au sein de cet abonnement.</span><span class="sxs-lookup"><span data-stu-id="ffbdc-166">Choose your subscription and one of your active storage accounts within that subscription.</span></span>|
    |<span data-ttu-id="ffbdc-167">Conteneur</span><span class="sxs-lookup"><span data-stu-id="ffbdc-167">Container</span></span>|<span data-ttu-id="ffbdc-168">Ce conteneur est le conteneur blob spécifique dans votre compte de stockage où votre cluster recherche des fichiers pour exécuter votre application dans le cloud.</span><span class="sxs-lookup"><span data-stu-id="ffbdc-168">This container is the specific blob container in your storage account where your cluster looks for files to run your app in the cloud.</span></span> <span data-ttu-id="ffbdc-169">Vous pouvez lui donner n’importe quel nom disponible.</span><span class="sxs-lookup"><span data-stu-id="ffbdc-169">You can give it any available name.</span></span>|

5. <span data-ttu-id="ffbdc-170">Sous **Vérifier + créer**, sélectionnez **Créer**.</span><span class="sxs-lookup"><span data-stu-id="ffbdc-170">Under **Review + create**, select **Create**.</span></span> <span data-ttu-id="ffbdc-171">La création du cluster prend environ 20 minutes.</span><span class="sxs-lookup"><span data-stu-id="ffbdc-171">It takes about 20 minutes to create the cluster.</span></span> <span data-ttu-id="ffbdc-172">Le cluster doit être créé avant de pouvoir passer à l’étape suivante.</span><span class="sxs-lookup"><span data-stu-id="ffbdc-172">The cluster must be created before you can continue to the next step.</span></span>

## <a name="publish-your-app"></a><span data-ttu-id="ffbdc-173">Publier votre application</span><span class="sxs-lookup"><span data-stu-id="ffbdc-173">Publish your app</span></span>

<span data-ttu-id="ffbdc-174">Ensuite, vous publiez le *mySparkApp* créé dans le [.NET pour Apache Spark - Get Started in 10-Minutes](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) tutoriel, qui donne à votre cluster Spark accès à tous les fichiers dont il a besoin pour exécuter votre application.</span><span class="sxs-lookup"><span data-stu-id="ffbdc-174">Next, you publish the *mySparkApp* created in the [.NET for Apache Spark - Get Started in 10-Minutes](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) tutorial, which gives your Spark cluster access to all the files it needs to run your app.</span></span>

1. <span data-ttu-id="ffbdc-175">Exécutez les commandes suivantes pour publier le *mySparkApp*:</span><span class="sxs-lookup"><span data-stu-id="ffbdc-175">Run the following commands to publish the *mySparkApp*:</span></span>

   <span data-ttu-id="ffbdc-176">**Sur Windows:**</span><span class="sxs-lookup"><span data-stu-id="ffbdc-176">**On Windows:**</span></span>

   ```dotnetcli
   cd mySparkApp
   dotnet publish -c Release -f netcoreapp3.0 -r ubuntu.16.04-x64
   ```

   <span data-ttu-id="ffbdc-177">**Sur Linux:**</span><span class="sxs-lookup"><span data-stu-id="ffbdc-177">**On Linux:**</span></span>

   ```bash
   cd mySparkApp
   foo@bar:~/path/to/app$ dotnet publish -c Release -f netcoreapp3.0 -r ubuntu.16.04-x64
   ```

2. <span data-ttu-id="ffbdc-178">Faites les tâches suivantes pour zip vos fichiers d’application publiés afin que vous puissiez facilement les télécharger sur votre cluster HDInsight.</span><span class="sxs-lookup"><span data-stu-id="ffbdc-178">Do the following tasks to zip your published app files so that you can easily upload them to your HDInsight cluster.</span></span>

   <span data-ttu-id="ffbdc-179">**Sur Windows:**</span><span class="sxs-lookup"><span data-stu-id="ffbdc-179">**On Windows:**</span></span>

   <span data-ttu-id="ffbdc-180">Naviguez vers *mySparkApp/bin/Release/netcoreapp3.0/ubuntu.16.04-x64*.</span><span class="sxs-lookup"><span data-stu-id="ffbdc-180">Navigate to *mySparkApp/bin/Release/netcoreapp3.0/ubuntu.16.04-x64*.</span></span> <span data-ttu-id="ffbdc-181">Ensuite, cliquez à droite sur le dossier **Publier** et sélectionnez **Envoyer à > dossier compressé (zippé).**</span><span class="sxs-lookup"><span data-stu-id="ffbdc-181">Then, right-click on **Publish** folder and select **Send to > Compressed (zipped) folder**.</span></span> <span data-ttu-id="ffbdc-182">Nommez le nouveau dossier **publish.zip**.</span><span class="sxs-lookup"><span data-stu-id="ffbdc-182">Name the new folder **publish.zip**.</span></span>

   <span data-ttu-id="ffbdc-183">**Sur Linux, exécutez la commande ci-dessous :**</span><span class="sxs-lookup"><span data-stu-id="ffbdc-183">**On Linux, run the following command:**</span></span>

   ```bash
   zip -r publish.zip
   ```

## <a name="upload-files-to-azure"></a><span data-ttu-id="ffbdc-184">Télécharger des fichiers sur Azure</span><span class="sxs-lookup"><span data-stu-id="ffbdc-184">Upload files to Azure</span></span>

<span data-ttu-id="ffbdc-185">Ensuite, vous utilisez l’Azure Storage Explorer pour télécharger les cinq fichiers suivants dans le conteneur blob que vous avez choisi pour le stockage de votre cluster :</span><span class="sxs-lookup"><span data-stu-id="ffbdc-185">Next, you use the Azure Storage Explorer to upload the following five files to the blob container you chose for your cluster's storage:</span></span>

* <span data-ttu-id="ffbdc-186">Microsoft.Spark.Travailleur</span><span class="sxs-lookup"><span data-stu-id="ffbdc-186">Microsoft.Spark.Worker</span></span>
* <span data-ttu-id="ffbdc-187">install-worker.sh</span><span class="sxs-lookup"><span data-stu-id="ffbdc-187">install-worker.sh</span></span>
* <span data-ttu-id="ffbdc-188">publish.zip</span><span class="sxs-lookup"><span data-stu-id="ffbdc-188">publish.zip</span></span>
* <span data-ttu-id="ffbdc-189">microsoft-spark-2.3.x-0.3.0.jar</span><span class="sxs-lookup"><span data-stu-id="ffbdc-189">microsoft-spark-2.3.x-0.3.0.jar</span></span>
* <span data-ttu-id="ffbdc-190">input.txt.</span><span class="sxs-lookup"><span data-stu-id="ffbdc-190">input.txt.</span></span>

1. <span data-ttu-id="ffbdc-191">Ouvrez Azure Storage Explorer et naviguez vers votre compte de stockage à partir du menu gauche.</span><span class="sxs-lookup"><span data-stu-id="ffbdc-191">Open Azure Storage Explorer and navigate to your storage account from the left menu.</span></span> <span data-ttu-id="ffbdc-192">Forez-le vers le bas pour le conteneur blob pour votre cluster sous **des conteneurs Blob** dans votre compte de stockage.</span><span class="sxs-lookup"><span data-stu-id="ffbdc-192">Drill down to the blob container for your cluster under **Blob Containers** in your storage account.</span></span>

2. <span data-ttu-id="ffbdc-193">*Microsoft.Spark.Worker* aide Apache Spark à exécuter votre application, telles que toutes les fonctions définies par l’utilisateur (UDF) que vous avez peut-être écrites.</span><span class="sxs-lookup"><span data-stu-id="ffbdc-193">*Microsoft.Spark.Worker* helps Apache Spark execute your app, such as any user-defined functions (UDFs) you may have written.</span></span> <span data-ttu-id="ffbdc-194">Télécharger [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases/download/v0.3.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.3.0.tar.gz).</span><span class="sxs-lookup"><span data-stu-id="ffbdc-194">Download [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases/download/v0.3.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.3.0.tar.gz).</span></span> <span data-ttu-id="ffbdc-195">Ensuite, sélectionnez **Upload** dans Azure Storage Explorer pour télécharger le travailleur.</span><span class="sxs-lookup"><span data-stu-id="ffbdc-195">Then, select **Upload** in Azure Storage Explorer to upload the worker.</span></span>

   ![Téléchargez des fichiers sur Azure Storage Explorer](./media/hdinsight-deployment/upload-files-to-storage.png)

3. <span data-ttu-id="ffbdc-197">Le *install-worker.sh* est un script qui vous permet de copier .NET pour les fichiers dépendants Apache Spark dans les nœuds de votre cluster.</span><span class="sxs-lookup"><span data-stu-id="ffbdc-197">The *install-worker.sh* is a script that lets you copy .NET for Apache Spark dependent files into the nodes of your cluster.</span></span>

   <span data-ttu-id="ffbdc-198">Créez un nouveau fichier nommé **install-worker.sh** votre ordinateur local et collez le [contenu install-worker.sh](https://raw.githubusercontent.com/dotnet/spark/master/deployment/install-worker.sh) situé sur GitHub.</span><span class="sxs-lookup"><span data-stu-id="ffbdc-198">Create a new file named **install-worker.sh** your local computer, and paste the [install-worker.sh contents](https://raw.githubusercontent.com/dotnet/spark/master/deployment/install-worker.sh) located on GitHub.</span></span> <span data-ttu-id="ffbdc-199">Ensuite, téléchargez *install-worker.sh* dans votre conteneur blob.</span><span class="sxs-lookup"><span data-stu-id="ffbdc-199">Then, upload *install-worker.sh* to your blob container.</span></span>

4. <span data-ttu-id="ffbdc-200">Votre cluster a besoin du fichier publish.zip qui contient les fichiers publiés par votre application.</span><span class="sxs-lookup"><span data-stu-id="ffbdc-200">Your cluster needs the publish.zip file that contains your app's published files.</span></span> <span data-ttu-id="ffbdc-201">Naviguez vers votre dossier publié, **mySparkApp/bin/Release/netcoreapp3.0/ubuntu.16.04-x64**, et **localisez publish.zip**.</span><span class="sxs-lookup"><span data-stu-id="ffbdc-201">Navigate to your published folder, **mySparkApp/bin/Release/netcoreapp3.0/ubuntu.16.04-x64**, and locate **publish.zip**.</span></span> <span data-ttu-id="ffbdc-202">Ensuite, téléchargez *publish.zip* sur votre conteneur blob.</span><span class="sxs-lookup"><span data-stu-id="ffbdc-202">Then upload *publish.zip* to your blob container.</span></span>

5. <span data-ttu-id="ffbdc-203">Votre cluster a besoin du code d’application qui a été emballé dans un fichier de pot.</span><span class="sxs-lookup"><span data-stu-id="ffbdc-203">Your cluster needs the application code that was packaged into a jar file.</span></span> <span data-ttu-id="ffbdc-204">Naviguez vers votre dossier publié, **mySparkApp/bin/Release/netcoreapp3.0/ubuntu.16.04-x64**, et localisez **microsoft-spark-2.3.x-0.3.0.jar**.</span><span class="sxs-lookup"><span data-stu-id="ffbdc-204">Navigate to your published folder, **mySparkApp/bin/Release/netcoreapp3.0/ubuntu.16.04-x64**, and locate **microsoft-spark-2.3.x-0.3.0.jar**.</span></span> <span data-ttu-id="ffbdc-205">Ensuite, téléchargez le fichier de pot sur votre conteneur blob.</span><span class="sxs-lookup"><span data-stu-id="ffbdc-205">Then, upload the jar file to your blob container.</span></span>

   <span data-ttu-id="ffbdc-206">Il peut y avoir plusieurs fichiers .jar (pour les versions 2.3.x et 2.4.x de Spark).</span><span class="sxs-lookup"><span data-stu-id="ffbdc-206">There may be multiple .jar files (for versions 2.3.x and 2.4.x of Spark).</span></span> <span data-ttu-id="ffbdc-207">Vous devez choisir le fichier .jar qui correspond à la version de Spark que vous avez choisie lors de la création de cluster.</span><span class="sxs-lookup"><span data-stu-id="ffbdc-207">You need to choose the .jar file that matches the version of Spark you chose during cluster creation.</span></span> <span data-ttu-id="ffbdc-208">Par exemple, choisissez *microsoft-spark-2.3.x-0.3.0.jar* si vous avez choisi Spark 2.3.2 lors de la création de cluster.</span><span class="sxs-lookup"><span data-stu-id="ffbdc-208">For example, choose *microsoft-spark-2.3.x-0.3.0.jar* if you chose Spark 2.3.2 during cluster creation.</span></span>

6. <span data-ttu-id="ffbdc-209">Votre cluster a besoin de l’entrée de votre application.</span><span class="sxs-lookup"><span data-stu-id="ffbdc-209">Your cluster needs the input to your app.</span></span> <span data-ttu-id="ffbdc-210">Naviguez vers votre répertoire **mySparkApp** et **localisez input.txt**.</span><span class="sxs-lookup"><span data-stu-id="ffbdc-210">Navigate to your **mySparkApp** directory and locate **input.txt**.</span></span> <span data-ttu-id="ffbdc-211">Téléchargez votre fichier d’entrée dans **l’annuaire utilisateur/sshuser** dans votre conteneur blob.</span><span class="sxs-lookup"><span data-stu-id="ffbdc-211">Upload your input file to the **user/sshuser** directory in your blob container.</span></span> <span data-ttu-id="ffbdc-212">Vous vous connecterez à votre cluster par ssh, et ce dossier est l’endroit où votre cluster cherche son entrée.</span><span class="sxs-lookup"><span data-stu-id="ffbdc-212">You will be connecting to your cluster through ssh, and this folder is where your cluster looks for its input.</span></span> <span data-ttu-id="ffbdc-213">Le fichier *input.txt* est le seul fichier téléchargé sur un répertoire spécifique.</span><span class="sxs-lookup"><span data-stu-id="ffbdc-213">The *input.txt* file is the only file uploaded to a specific directory.</span></span>

## <a name="run-the-hdinsight-script-action"></a><span data-ttu-id="ffbdc-214">Exécuter l’action de script HDInsight</span><span class="sxs-lookup"><span data-stu-id="ffbdc-214">Run the HDInsight script action</span></span>

<span data-ttu-id="ffbdc-215">Une fois que votre cluster est en cours d’exécution et que vous avez téléchargé vos fichiers sur Azure, vous exécutez le **script install-worker.sh** sur le cluster.</span><span class="sxs-lookup"><span data-stu-id="ffbdc-215">Once your cluster is running and you've uploaded your files to Azure, you run the **install-worker.sh** script on the cluster.</span></span>

1. <span data-ttu-id="ffbdc-216">Naviguez vers votre cluster HDInsight Spark dans le portail Azure, puis sélectionnez **les actions Script**.</span><span class="sxs-lookup"><span data-stu-id="ffbdc-216">Navigate to your HDInsight Spark cluster in Azure portal, and then select **Script actions**.</span></span>

2. <span data-ttu-id="ffbdc-217">Sélectionnez **et soumettez de nouvelles** valeurs et fournissez les valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="ffbdc-217">Select **+ Submit new** and provide the following values:</span></span>

   |<span data-ttu-id="ffbdc-218">Propriété</span><span class="sxs-lookup"><span data-stu-id="ffbdc-218">Property</span></span>  |<span data-ttu-id="ffbdc-219">Description</span><span class="sxs-lookup"><span data-stu-id="ffbdc-219">Description</span></span>  |
   |---------|---------|
   | <span data-ttu-id="ffbdc-220">Type de script</span><span class="sxs-lookup"><span data-stu-id="ffbdc-220">Script type</span></span> |<span data-ttu-id="ffbdc-221">Custom</span><span class="sxs-lookup"><span data-stu-id="ffbdc-221">Custom</span></span>|
   | <span data-ttu-id="ffbdc-222">Nom</span><span class="sxs-lookup"><span data-stu-id="ffbdc-222">Name</span></span> | <span data-ttu-id="ffbdc-223">Installer Le travailleur</span><span class="sxs-lookup"><span data-stu-id="ffbdc-223">Install Worker</span></span>|
   | <span data-ttu-id="ffbdc-224">URI de script bash</span><span class="sxs-lookup"><span data-stu-id="ffbdc-224">Bash script URI</span></span> |https://mystorageaccount.blob.core.windows.net/mycontainer/install-worker.sh </br> <span data-ttu-id="ffbdc-225">Pour confirmer cette URI, cliquez à droite sur install-worker.sh dans Azure Storage Explorer et sélectionnez Propriétés.</span><span class="sxs-lookup"><span data-stu-id="ffbdc-225">To confirm this URI, right-click on install-worker.sh in Azure Storage Explorer and select Properties.</span></span> |
   | <span data-ttu-id="ffbdc-226">Type(s) de nœud</span><span class="sxs-lookup"><span data-stu-id="ffbdc-226">Node type(s)</span></span>| <span data-ttu-id="ffbdc-227">Worker</span><span class="sxs-lookup"><span data-stu-id="ffbdc-227">Worker</span></span>|
   | <span data-ttu-id="ffbdc-228">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ffbdc-228">Parameters</span></span> | <span data-ttu-id="ffbdc-229">azure</span><span class="sxs-lookup"><span data-stu-id="ffbdc-229">azure</span></span> </br> wasbs://mycontainer@myStorageAccount.blob.core.windows.net/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz </br> <span data-ttu-id="ffbdc-230">/usr/local/bin</span><span class="sxs-lookup"><span data-stu-id="ffbdc-230">/usr/local/bin</span></span>

3. <span data-ttu-id="ffbdc-231">Sélectionnez **Créer** pour soumettre votre script.</span><span class="sxs-lookup"><span data-stu-id="ffbdc-231">Select **Create** to submit your script.</span></span>

## <a name="run-your-app"></a><span data-ttu-id="ffbdc-232">Exécutez l'application.</span><span class="sxs-lookup"><span data-stu-id="ffbdc-232">Run your app</span></span>

1. <span data-ttu-id="ffbdc-233">Naviguez vers votre cluster HDInsight Spark dans le portail Azure, puis sélectionnez **la connexion SSH et Cluster**.</span><span class="sxs-lookup"><span data-stu-id="ffbdc-233">Navigate to your HDInsight Spark cluster in Azure portal, and then select **SSH + Cluster login**.</span></span>

2. <span data-ttu-id="ffbdc-234">Copiez les informations de connexion ssh et collez la connexion dans un terminal.</span><span class="sxs-lookup"><span data-stu-id="ffbdc-234">Copy the ssh login information and paste the login into a terminal.</span></span> <span data-ttu-id="ffbdc-235">Connectez-vous à votre cluster à l’aide du mot de passe que vous avez défini lors de la création du cluster.</span><span class="sxs-lookup"><span data-stu-id="ffbdc-235">Sign in to your cluster using the password you set during cluster creation.</span></span> <span data-ttu-id="ffbdc-236">Vous devriez voir des messages vous accueillant à Ubuntu et Spark.</span><span class="sxs-lookup"><span data-stu-id="ffbdc-236">You should see messages welcoming you to Ubuntu and Spark.</span></span>

3. <span data-ttu-id="ffbdc-237">Utilisez la commande **spark-submit** pour exécuter votre application sur votre cluster HDInsight.</span><span class="sxs-lookup"><span data-stu-id="ffbdc-237">Use the **spark-submit** command to run your app on your HDInsight cluster.</span></span> <span data-ttu-id="ffbdc-238">N’oubliez pas de remplacer **mycontainer** et **mystorageaccount** dans le script de l’exemple avec les noms réels de votre conteneur blob et compte de stockage.</span><span class="sxs-lookup"><span data-stu-id="ffbdc-238">Remember to replace **mycontainer** and **mystorageaccount** in the example script with the actual names of your blob container and storage account.</span></span>

   ```bash
   $SPARK_HOME/bin/spark-submit \
   --master yarn \
   --class org.apache.spark.deploy.dotnet.DotnetRunner \
   wasbs://mycontainer@mystorageaccount.blob.core.windows.net/microsoft-spark-2.3.x-0.6.0.jar \
   wasbs://mycontainer@mystorageaccount.blob.core.windows.net/publish.zip mySparkApp
   ```

   <span data-ttu-id="ffbdc-239">Lorsque votre application s’exécute, vous voyez le même tableau de nombre de mots de la course locale de démarrage écrit à la console.</span><span class="sxs-lookup"><span data-stu-id="ffbdc-239">When your app runs, you see the same word count table from the getting started local run written to the console.</span></span> <span data-ttu-id="ffbdc-240">Félicitations, vous avez exécuté votre premier .NET pour Apache Spark application dans le nuage!</span><span class="sxs-lookup"><span data-stu-id="ffbdc-240">Congratulations, you've run your first .NET for Apache Spark application in the cloud!</span></span>

## <a name="clean-up-resources"></a><span data-ttu-id="ffbdc-241">Nettoyer les ressources</span><span class="sxs-lookup"><span data-stu-id="ffbdc-241">Clean up resources</span></span>

<span data-ttu-id="ffbdc-242">HDInsight enregistre vos données dans Azure Storage, de sorte que vous pouvez supprimer en toute sécurité un cluster lorsqu’il n’est pas utilisé.</span><span class="sxs-lookup"><span data-stu-id="ffbdc-242">HDInsight saves your data in Azure Storage, so you can safely delete a cluster when it is not in use.</span></span> <span data-ttu-id="ffbdc-243">Vous devez également payer pour un cluster HDInsight, même lorsque vous ne l’utilisez pas.</span><span class="sxs-lookup"><span data-stu-id="ffbdc-243">You are also charged for an HDInsight cluster, even when it is not in use.</span></span> <span data-ttu-id="ffbdc-244">Étant donné que les frais pour le cluster sont bien plus élevés que les frais de stockage, économique, mieux vaut supprimer les clusters lorsqu’ils ne sont pas utilisés.</span><span class="sxs-lookup"><span data-stu-id="ffbdc-244">Since the charges for the cluster are many times more than the charges for storage, it makes economic sense to delete clusters when they are not in use.</span></span>

<span data-ttu-id="ffbdc-245">Vous pouvez également sélectionner le nom du groupe de ressources pour ouvrir la page du groupe de ressources, puis sélectionner **Supprimer le groupe de ressources**.</span><span class="sxs-lookup"><span data-stu-id="ffbdc-245">You can also select the resource group name to open the resource group page, and then select **Delete resource group**.</span></span> <span data-ttu-id="ffbdc-246">En supprimant le groupe de ressources, vous supprimez le cluster HDInsight Spark et le compte de stockage par défaut.</span><span class="sxs-lookup"><span data-stu-id="ffbdc-246">By deleting the resource group, you delete both the HDInsight Spark cluster, and the default storage account.</span></span>

## <a name="next-steps"></a><span data-ttu-id="ffbdc-247">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="ffbdc-247">Next steps</span></span>

<span data-ttu-id="ffbdc-248">Dans ce tutoriel, vous avez déployé votre application .NET pour Apache Spark sur Azure HDInsight.</span><span class="sxs-lookup"><span data-stu-id="ffbdc-248">In this tutorial, you deployed your .NET for Apache Spark application to Azure HDInsight.</span></span> <span data-ttu-id="ffbdc-249">Pour plus d’informations sur HDInsight, consultez la documentation d’Azure HDInsight.</span><span class="sxs-lookup"><span data-stu-id="ffbdc-249">To learn more about HDInsight, continue to the Azure HDInsight Documentation.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ffbdc-250">Azure HDInsight Documentation</span><span class="sxs-lookup"><span data-stu-id="ffbdc-250">Azure HDInsight Documentation</span></span>](https://docs.microsoft.com/azure/hdinsight/)
