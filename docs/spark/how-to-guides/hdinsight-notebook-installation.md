---
title: Installer .NET pour Apache Spark sur les ordinateurs portables Jupyter sur les clusters Azure HDInsight Spark
description: Découvrez comment installer .NET pour Apache Spark sur azure HDInsight’s Jupyter Notebooks.
ms.date: 03/13/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 953bffe5f6ec56cd0adf4224afd2eedfe0001aa9
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/17/2020
ms.locfileid: "81607413"
---
# <a name="install-net-for-apache-spark-on-jupyter-notebooks-on-azure-hdinsight-spark-clusters"></a><span data-ttu-id="33bfe-103">Installer .NET pour Apache Spark sur les ordinateurs portables Jupyter sur les clusters Azure HDInsight Spark</span><span class="sxs-lookup"><span data-stu-id="33bfe-103">Install .NET for Apache Spark on Jupyter notebooks on Azure HDInsight Spark clusters</span></span>

<span data-ttu-id="33bfe-104">Cet article vous apprend à installer .NET pour Apache Spark sur les ordinateurs portables Jupyter sur les clusters Azure HDInsight Spark.</span><span class="sxs-lookup"><span data-stu-id="33bfe-104">This article teaches you how to install .NET for Apache Spark on Jupyter notebooks on Azure HDInsight Spark clusters.</span></span> <span data-ttu-id="33bfe-105">Vous pouvez déployer .NET pour Apache Spark sur les clusters HDInsight Azure grâce à une combinaison de la ligne de commande et du portail Azure (pour plus d’informations, voir [comment déployer une application .NET pour Apache Spark à Azure HDInsight),](../tutorials/hdinsight-deployment.md)mais les ordinateurs portables offrent une expérience plus interactive et itérative.</span><span class="sxs-lookup"><span data-stu-id="33bfe-105">You can deploy .NET for Apache Spark on Azure HDInsight clusters through a combination of the command line and the Azure portal (for more information, see [how to deploy a .NET for Apache Spark application to Azure HDInsight](../tutorials/hdinsight-deployment.md)), but notebooks provide a more interactive and iterative experience.</span></span>

<span data-ttu-id="33bfe-106">Les clusters Azure HDInsight sont déjà livrés avec des ordinateurs portables Jupyter, donc tout ce que vous avez à faire est de configurer les ordinateurs portables Jupyter pour exécuter .NET pour Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="33bfe-106">Azure HDInsight clusters already come with Jupyter notebooks, so all you have to do is configure the Jupyter notebooks to run .NET for Apache Spark.</span></span> <span data-ttu-id="33bfe-107">Pour utiliser .NET pour Apache Spark dans vos ordinateurs portables Jupyter, un REPL C est nécessaire pour exécuter votre code CMD ligne par ligne et pour préserver l’état d’exécution si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="33bfe-107">To use .NET for Apache Spark in your Jupyter notebooks, a C# REPL is needed to execute your C# code line-by-line and to preserve execution state when necessary.</span></span> <span data-ttu-id="33bfe-108">[Essayez .NET](https://github.com/dotnet/try) a été intégré comme le REPL officiel .NET.</span><span class="sxs-lookup"><span data-stu-id="33bfe-108">[Try .NET](https://github.com/dotnet/try) has been integrated as the official .NET REPL.</span></span>

<span data-ttu-id="33bfe-109">Pour activer .NET pour Apache Spark grâce à l’expérience Jupyter Notebooks, vous devez suivre quelques étapes manuelles à travers [Ambari](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-manage-ambari) et soumettre des [actions de script](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux) sur le cluster HDInsight Spark.</span><span class="sxs-lookup"><span data-stu-id="33bfe-109">To enable .NET for Apache Spark through the Jupyter Notebooks experience, you need to follow a few manual steps through [Ambari](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-manage-ambari) and submit [script actions](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux) on the HDInsight Spark cluster.</span></span>

> [!NOTE]
> <span data-ttu-id="33bfe-110">Cette fonctionnalité est *expérimentale* et n’est pas prise en charge par l’équipe HDInsight Spark.</span><span class="sxs-lookup"><span data-stu-id="33bfe-110">This feature is *experimental* and is not supported by the HDInsight Spark team.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="33bfe-111">Prérequis</span><span class="sxs-lookup"><span data-stu-id="33bfe-111">Prerequisites</span></span>

<span data-ttu-id="33bfe-112">Si vous n’en avez pas déjà, créez un cluster [Azure HDInsight Spark.](https://docs.microsoft.com/azure/hdinsight/spark/apache-spark-jupyter-spark-sql-use-portal#create-an-apache-spark-cluster-in-hdinsight)</span><span class="sxs-lookup"><span data-stu-id="33bfe-112">If you don't already have one, create an [Azure HDInsight Spark](https://docs.microsoft.com/azure/hdinsight/spark/apache-spark-jupyter-spark-sql-use-portal#create-an-apache-spark-cluster-in-hdinsight) cluster.</span></span>

1. <span data-ttu-id="33bfe-113">Visitez le [portail Azure](https://portal.azure.com) et sélectionnez **- Créer une ressource**.</span><span class="sxs-lookup"><span data-stu-id="33bfe-113">Visit the [Azure portal](https://portal.azure.com) and select **+ Create a Resource**.</span></span>

1. <span data-ttu-id="33bfe-114">Créez une nouvelle ressource en cluster Azure HDInsight.</span><span class="sxs-lookup"><span data-stu-id="33bfe-114">Create a new Azure HDInsight cluster resource.</span></span> <span data-ttu-id="33bfe-115">Sélectionnez **Spark 2.4** et **HDI 4.0** lors de la création de grappes.</span><span class="sxs-lookup"><span data-stu-id="33bfe-115">Select **Spark 2.4** and **HDI 4.0** during cluster creation.</span></span>

## <a name="install-net-for-apache-spark"></a><span data-ttu-id="33bfe-116">Installer .NET pour Apache Spark</span><span class="sxs-lookup"><span data-stu-id="33bfe-116">Install .NET for Apache Spark</span></span>

<span data-ttu-id="33bfe-117">Dans le portail Azure, sélectionnez le **cluster HDInsight Spark** que vous avez créé dans l’étape précédente.</span><span class="sxs-lookup"><span data-stu-id="33bfe-117">In the Azure portal, select the **HDInsight Spark cluster** you created in the previous step.</span></span>

### <a name="stop-the-livy-server"></a><span data-ttu-id="33bfe-118">Arrêtez le serveur Livy</span><span class="sxs-lookup"><span data-stu-id="33bfe-118">Stop the Livy server</span></span>

1. <span data-ttu-id="33bfe-119">À partir du portail, sélectionnez **Aperçu,** puis sélectionnez **Ambari à la maison**.</span><span class="sxs-lookup"><span data-stu-id="33bfe-119">From the portal, select **Overview**, and then select **Ambari home**.</span></span> <span data-ttu-id="33bfe-120">Si vous êtes invité, entrez les identifiants de connexion pour le cluster.</span><span class="sxs-lookup"><span data-stu-id="33bfe-120">If prompted, enter the login credentials for the cluster.</span></span>

   ![Arrêter Livy Server](./media/hdinsight-notebook-installation/select-ambari.png)

2. <span data-ttu-id="33bfe-122">Sélectionnez **Spark2** dans le menu de navigation gauche, et sélectionnez **LIVY FOR SPARK2 SERVER**.</span><span class="sxs-lookup"><span data-stu-id="33bfe-122">Select **Spark2** from the left navigation menu, and select **LIVY FOR SPARK2 SERVER**.</span></span>

   ![Arrêter Livy Server](./media/hdinsight-notebook-installation/select-livyserver.png)

3. <span data-ttu-id="33bfe-124">Sélectionnez **hn0... hôte**.</span><span class="sxs-lookup"><span data-stu-id="33bfe-124">Select **hn0... host**.</span></span>

   ![Arrêter Livy Server](./media/hdinsight-notebook-installation/select-host.png)

4. <span data-ttu-id="33bfe-126">Sélectionnez l’ellipsis à côté de **Livy pour Spark2 Server** et sélectionnez **Stop**.</span><span class="sxs-lookup"><span data-stu-id="33bfe-126">Select the ellipsis next to **Livy for Spark2 Server** and select **Stop**.</span></span> <span data-ttu-id="33bfe-127">Lorsqu’on l’a invité, sélectionnez **OK** pour procéder.</span><span class="sxs-lookup"><span data-stu-id="33bfe-127">When prompted, select **OK** to proceed.</span></span>

   <span data-ttu-id="33bfe-128">Arrêtez Livy pour Spark2 Server.</span><span class="sxs-lookup"><span data-stu-id="33bfe-128">Stop Livy for Spark2 Server.</span></span>
   <span data-ttu-id="33bfe-129">![Arrêter Livy Server](./media/hdinsight-notebook-installation/stop-server.png)</span><span class="sxs-lookup"><span data-stu-id="33bfe-129">![Stop Livy Server](./media/hdinsight-notebook-installation/stop-server.png)</span></span>

5. <span data-ttu-id="33bfe-130">Répétez les étapes précédentes pour **hn1... hôte**.</span><span class="sxs-lookup"><span data-stu-id="33bfe-130">Repeat the previous steps for **hn1... host**.</span></span>

### <a name="submit-an-hdinsight-script-action"></a><span data-ttu-id="33bfe-131">Soumettre une action de script HDInsight</span><span class="sxs-lookup"><span data-stu-id="33bfe-131">Submit an HDInsight script action</span></span>

1. <span data-ttu-id="33bfe-132">Le `install-interactive-notebook.sh` est un script qui installe .NET pour Apache Spark et apporte des modifications à Apache Livy et sparkmagic.</span><span class="sxs-lookup"><span data-stu-id="33bfe-132">The `install-interactive-notebook.sh` is a script that installs .NET for Apache Spark and makes changes to Apache Livy and sparkmagic.</span></span> <span data-ttu-id="33bfe-133">Avant de soumettre une action de script à HDInsight, vous devez créer et télécharger `install-interactive-notebook.sh`.</span><span class="sxs-lookup"><span data-stu-id="33bfe-133">Before you submit a script action to HDInsight, you need to create and upload `install-interactive-notebook.sh`.</span></span>

   <span data-ttu-id="33bfe-134">Créez un nouveau fichier nommé **install-interactive-notebook.sh** dans votre ordinateur local et collez le contenu de [install-interactive-notebook.sh contenu](https://raw.githubusercontent.com/dotnet/spark/master/deployment/HDI-Spark/Notebooks/install-interactive-notebook.sh).</span><span class="sxs-lookup"><span data-stu-id="33bfe-134">Create a new file named **install-interactive-notebook.sh** in your local computer and paste the contents of [install-interactive-notebook.sh contents](https://raw.githubusercontent.com/dotnet/spark/master/deployment/HDI-Spark/Notebooks/install-interactive-notebook.sh).</span></span>

   <span data-ttu-id="33bfe-135">Téléchargez le script sur un [URI](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux#understand-script-actions) accessible à partir du cluster HDInsight.</span><span class="sxs-lookup"><span data-stu-id="33bfe-135">Upload the script to a [URI](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux#understand-script-actions) that's accessible from the HDInsight cluster.</span></span> <span data-ttu-id="33bfe-136">Par exemple : `https://<my storage account>.blob.core.windows.net/<my container>/<some dir>/install-interactive-notebook.sh`.</span><span class="sxs-lookup"><span data-stu-id="33bfe-136">For example, `https://<my storage account>.blob.core.windows.net/<my container>/<some dir>/install-interactive-notebook.sh`.</span></span>

2. <span data-ttu-id="33bfe-137">Exécutez `install-interactive-notebook.sh` sur le cluster en utilisant des [actions de script HDInsight](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux).</span><span class="sxs-lookup"><span data-stu-id="33bfe-137">Run `install-interactive-notebook.sh` on the cluster using [HDInsight Script Actions](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux).</span></span>

   <span data-ttu-id="33bfe-138">Retournez à votre cluster HDI dans le portail Azure et sélectionnez les **actions Script** des options de gauche.</span><span class="sxs-lookup"><span data-stu-id="33bfe-138">Return to your HDI cluster in the Azure portal, and select **Script actions** from the options on the left.</span></span> <span data-ttu-id="33bfe-139">Vous soumettez une action de script pour déployer le .NET pour Apache Spark REPL sur votre cluster HDInsight Spark.</span><span class="sxs-lookup"><span data-stu-id="33bfe-139">You submit one script action to deploy the .NET for Apache Spark REPL on your HDInsight Spark cluster.</span></span> <span data-ttu-id="33bfe-140">Utilisez les paramètres suivants :</span><span class="sxs-lookup"><span data-stu-id="33bfe-140">Use the following settings:</span></span>

   |<span data-ttu-id="33bfe-141">Propriété</span><span class="sxs-lookup"><span data-stu-id="33bfe-141">Property</span></span>  |<span data-ttu-id="33bfe-142">Description</span><span class="sxs-lookup"><span data-stu-id="33bfe-142">Description</span></span>  |
   |---------|---------|
   | <span data-ttu-id="33bfe-143">Type de script</span><span class="sxs-lookup"><span data-stu-id="33bfe-143">Script type</span></span> | <span data-ttu-id="33bfe-144">Custom</span><span class="sxs-lookup"><span data-stu-id="33bfe-144">Custom</span></span> |
   | <span data-ttu-id="33bfe-145">Nom</span><span class="sxs-lookup"><span data-stu-id="33bfe-145">Name</span></span> | <span data-ttu-id="33bfe-146">*Installer .NET pour Apache Spark Interactive Notebook Experience*</span><span class="sxs-lookup"><span data-stu-id="33bfe-146">*Install .NET for Apache Spark Interactive Notebook Experience*</span></span> |
   | <span data-ttu-id="33bfe-147">URI de script bash</span><span class="sxs-lookup"><span data-stu-id="33bfe-147">Bash script URI</span></span> | <span data-ttu-id="33bfe-148">URI vers lequel vous avez chargé `install-interactive-notebook.sh`.</span><span class="sxs-lookup"><span data-stu-id="33bfe-148">The URI to which you uploaded `install-interactive-notebook.sh`.</span></span> |
   | <span data-ttu-id="33bfe-149">Type(s) de nœud</span><span class="sxs-lookup"><span data-stu-id="33bfe-149">Node type(s)</span></span>| <span data-ttu-id="33bfe-150">Chef et travailleur</span><span class="sxs-lookup"><span data-stu-id="33bfe-150">Head and Worker</span></span> |
   | <span data-ttu-id="33bfe-151">Paramètres</span><span class="sxs-lookup"><span data-stu-id="33bfe-151">Parameters</span></span> | <span data-ttu-id="33bfe-152">.NET pour la version Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="33bfe-152">.NET for Apache Spark version.</span></span> <span data-ttu-id="33bfe-153">Vous pouvez vérifier [.NET pour apache Spark versions](https://github.com/dotnet/spark/releases).</span><span class="sxs-lookup"><span data-stu-id="33bfe-153">You can check [.NET for Apache Spark releases](https://github.com/dotnet/spark/releases).</span></span> <span data-ttu-id="33bfe-154">Par exemple, si vous voulez installer la version Sparkdotnet 0.6.0 alors il serait `0.6.0`.</span><span class="sxs-lookup"><span data-stu-id="33bfe-154">For example, if you want to install Sparkdotnet version 0.6.0 then it would be `0.6.0`.</span></span>

   <span data-ttu-id="33bfe-155">Passez à l’étape suivante lorsque les marques de contrôle vertes apparaissent à côté de l’état de l’action de script.</span><span class="sxs-lookup"><span data-stu-id="33bfe-155">Move to the next step when green checkmarks appear next to the status of the script action.</span></span>

### <a name="start-the-livy-server"></a><span data-ttu-id="33bfe-156">Démarrer le serveur Livy</span><span class="sxs-lookup"><span data-stu-id="33bfe-156">Start the Livy server</span></span>

<span data-ttu-id="33bfe-157">Suivez les instructions dans la section [serveur Stop Livy](#stop-the-livy-server) pour **démarrer** (plutôt que **d’arrêter**) le Livy pour Spark2 Server pour les hôtes **hn0** et **hn1**.</span><span class="sxs-lookup"><span data-stu-id="33bfe-157">Follow the instructions in the [Stop Livy server](#stop-the-livy-server) section to **Start** (rather than **Stop**) the Livy for Spark2 Server for hosts **hn0** and **hn1**.</span></span>

### <a name="set-up-spark-default-configurations"></a><span data-ttu-id="33bfe-158">Configurez des configurations par défaut Spark</span><span class="sxs-lookup"><span data-stu-id="33bfe-158">Set up Spark default configurations</span></span>

1. <span data-ttu-id="33bfe-159">À partir du portail, sélectionnez **Aperçu,** puis sélectionnez **Ambari à la maison**.</span><span class="sxs-lookup"><span data-stu-id="33bfe-159">From the portal, select **Overview**, and then select **Ambari home**.</span></span> <span data-ttu-id="33bfe-160">À l’invite (le cas échéant), entrez les informations d’identification du cluster.</span><span class="sxs-lookup"><span data-stu-id="33bfe-160">If prompted, enter the cluster login credentials for the cluster.</span></span>

2. <span data-ttu-id="33bfe-161">Sélectionnez **Spark2** et **CONFIGS**.</span><span class="sxs-lookup"><span data-stu-id="33bfe-161">Select **Spark2** and **CONFIGS**.</span></span> <span data-ttu-id="33bfe-162">Ensuite, sélectionnez **Custom spark2-defaults**.</span><span class="sxs-lookup"><span data-stu-id="33bfe-162">Then, select **Custom spark2-defaults**.</span></span>

   ![Définir Configs](./media/hdinsight-notebook-installation/spark-configs.png)

3. <span data-ttu-id="33bfe-164">Sélectionnez **Ajouter la propriété...** pour ajouter les paramètres par défaut Spark.</span><span class="sxs-lookup"><span data-stu-id="33bfe-164">Select **Add Property...** to add Spark default settings.</span></span>

   ![Ajouter une propriété](./media/hdinsight-notebook-installation/add-property.png)

   <span data-ttu-id="33bfe-166">Il y a trois propriétés individuelles.</span><span class="sxs-lookup"><span data-stu-id="33bfe-166">There are three individual properties.</span></span> <span data-ttu-id="33bfe-167">Ajoutez-les un à la fois en utilisant le type de propriété **TEXT** en mode Unique ajouter.</span><span class="sxs-lookup"><span data-stu-id="33bfe-167">Add them one at a time using the **TEXT** property type in Single property add mode.</span></span> <span data-ttu-id="33bfe-168">Vérifiez que vous n’avez pas d’espaces supplémentaires avant ou après l’une des clés/valeurs.</span><span class="sxs-lookup"><span data-stu-id="33bfe-168">Check that you don't have any extra spaces before or after any of the keys/values.</span></span>

   * <span data-ttu-id="33bfe-169">**Propriété 1**</span><span class="sxs-lookup"><span data-stu-id="33bfe-169">**Property 1**</span></span>
       * <span data-ttu-id="33bfe-170">Clé:&ensp;&ensp;`spark.dotnet.shell.command`</span><span class="sxs-lookup"><span data-stu-id="33bfe-170">Key:&ensp;&ensp;`spark.dotnet.shell.command`</span></span>
       * <span data-ttu-id="33bfe-171">Valeur: `/usr/share/dotnet-tools/dotnet-try,kernel-server,--default-kernel,csharp`</span><span class="sxs-lookup"><span data-stu-id="33bfe-171">Value: `/usr/share/dotnet-tools/dotnet-try,kernel-server,--default-kernel,csharp`</span></span>

   * <span data-ttu-id="33bfe-172">**Propriété 2** Utilisez la version de .NET pour Apache Spark que vous aviez inclus dans l’action de script précédente.</span><span class="sxs-lookup"><span data-stu-id="33bfe-172">**Property 2** Use the version of .NET for Apache Spark which you had included in the previous script action.</span></span>
       * <span data-ttu-id="33bfe-173">Clé:&ensp;&ensp;`spark.dotnet.packages`</span><span class="sxs-lookup"><span data-stu-id="33bfe-173">Key:&ensp;&ensp;`spark.dotnet.packages`</span></span>
       * <span data-ttu-id="33bfe-174">Valeur: `["nuget: Microsoft.Spark, 0.6.0", "nuget: Microsoft.Spark.Extensions.Delta, 0.6.0"]`</span><span class="sxs-lookup"><span data-stu-id="33bfe-174">Value: `["nuget: Microsoft.Spark, 0.6.0", "nuget: Microsoft.Spark.Extensions.Delta, 0.6.0"]`</span></span>

   * <span data-ttu-id="33bfe-175">**Propriété 3**</span><span class="sxs-lookup"><span data-stu-id="33bfe-175">**Property 3**</span></span>
       * <span data-ttu-id="33bfe-176">Clé:&ensp;&ensp;`spark.dotnet.interpreter`</span><span class="sxs-lookup"><span data-stu-id="33bfe-176">Key:&ensp;&ensp;`spark.dotnet.interpreter`</span></span>
       * <span data-ttu-id="33bfe-177">Valeur: `try`</span><span class="sxs-lookup"><span data-stu-id="33bfe-177">Value: `try`</span></span>

   <span data-ttu-id="33bfe-178">Par exemple, l’image suivante capture le paramètre pour l’ajout de la propriété 1 :</span><span class="sxs-lookup"><span data-stu-id="33bfe-178">For example, the following image captures the setting for adding property 1:</span></span>

   ![Définir Configs](./media/hdinsight-notebook-installation/add-sparkconfig.png)

   <span data-ttu-id="33bfe-180">Après l’ajout des trois propriétés, sélectionnez **SAVE**.</span><span class="sxs-lookup"><span data-stu-id="33bfe-180">After adding the three properties, select **SAVE**.</span></span> <span data-ttu-id="33bfe-181">Si vous voyez un écran d’avertissement des recommandations config, sélectionnez **PROCEED ANYWAY**.</span><span class="sxs-lookup"><span data-stu-id="33bfe-181">If you see a warning screen of config recommendations, select **PROCEED ANYWAY**.</span></span>

4. <span data-ttu-id="33bfe-182">Redémarrer les composants affectés.</span><span class="sxs-lookup"><span data-stu-id="33bfe-182">Restart affected components.</span></span>

   <span data-ttu-id="33bfe-183">Après l’ajout des nouvelles propriétés, vous devez redémarrer les composants qui ont été affectés par les changements.</span><span class="sxs-lookup"><span data-stu-id="33bfe-183">After adding the new properties, you need to restart components that were affected by the changes.</span></span> <span data-ttu-id="33bfe-184">En haut, sélectionnez **RESTART,** puis **redémarrez tous les touchés** à partir de la descente.</span><span class="sxs-lookup"><span data-stu-id="33bfe-184">At the top, select **RESTART**, and then **Restart All Affected** from the drop-down.</span></span>

   ![Définir Configs](./media/hdinsight-notebook-installation/restart-affected.png)

   <span data-ttu-id="33bfe-186">Lorsqu’on l’a invité, sélectionnez **CONFIRM RESTART ALL** pour continuer, puis cliquez sur **OK** pour terminer.</span><span class="sxs-lookup"><span data-stu-id="33bfe-186">When prompted, select **CONFIRM RESTART ALL** to continue, then click **OK** to finish.</span></span>

## <a name="submit-jobs-through-a-jupyter-notebook"></a><span data-ttu-id="33bfe-187">Soumettre des emplois par l’intermédiaire d’un carnet Jupyter</span><span class="sxs-lookup"><span data-stu-id="33bfe-187">Submit jobs through a Jupyter notebook</span></span>

<span data-ttu-id="33bfe-188">Après avoir terminé les étapes précédentes, vous pouvez maintenant soumettre votre .NET pour apache Spark emplois à travers les ordinateurs portables Jupyter.</span><span class="sxs-lookup"><span data-stu-id="33bfe-188">After finishing the previous steps, you can now submit your .NET for Apache Spark jobs through Jupyter notebooks.</span></span>

1. <span data-ttu-id="33bfe-189">Créez un nouveau .NET pour le carnet Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="33bfe-189">Create a new .NET for Apache Spark notebook.</span></span> <span data-ttu-id="33bfe-190">Lancez un ordinateur portable Jupyter depuis votre cluster HDI dans le portail Azure.</span><span class="sxs-lookup"><span data-stu-id="33bfe-190">Launch a Jupyter notebook from your HDI cluster in the Azure portal.</span></span>

   ![Lancement du carnet Jupyter](./media/hdinsight-notebook-installation/launch-notebook.png)

   <span data-ttu-id="33bfe-192">Ensuite, sélectionnez **New** > **.NET Spark (C)** pour créer un ordinateur portable.</span><span class="sxs-lookup"><span data-stu-id="33bfe-192">Then, select **New** > **.NET Spark (C#)** to create a notebook.</span></span>

   ![Jupyter Notebook](./media/hdinsight-notebook-installation/create-sparkdotnet-notebook.png)

2. <span data-ttu-id="33bfe-194">Soumettez des travaux en utilisant .NET pour Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="33bfe-194">Submit jobs using .NET for Apache Spark.</span></span>

   <span data-ttu-id="33bfe-195">Utilisez l’extrait de code suivant pour créer un DataFrame :</span><span class="sxs-lookup"><span data-stu-id="33bfe-195">Use the following code snippet to create a DataFrame:</span></span>

   ```csharp
   var df = spark.Range(0,5);
   df.Show();
   ```

   ![Soumettre Spark Job](./media/hdinsight-notebook-installation/create-df.png)

   <span data-ttu-id="33bfe-197">Utilisez l’extrait de code suivant pour enregistrer une fonction définie par l’utilisateur (UDF) et utiliser l’UDF avec DataFrames :</span><span class="sxs-lookup"><span data-stu-id="33bfe-197">Use the following code snippet to register a user-defined function (UDF) and use the UDF with DataFrames:</span></span>

   ```csharp
   var myawesomeudf = Udf<int, string>((id) => $"hello {id}");
   df.Select(myawesomeudf(df["id"])).Show();
   ```

   ![Soumettre Spark Job](./media/hdinsight-notebook-installation/run-udf.png)

## <a name="next-steps"></a><span data-ttu-id="33bfe-199">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="33bfe-199">Next steps</span></span>

* [<span data-ttu-id="33bfe-200">Déployer une application .NET pour Apache Spark sur Azure HDInsight</span><span class="sxs-lookup"><span data-stu-id="33bfe-200">Deploy a .NET for Apache Spark application to Azure HDInsight</span></span>](../tutorials/hdinsight-deployment.md)
* [<span data-ttu-id="33bfe-201">HDInsight Documentation</span><span class="sxs-lookup"><span data-stu-id="33bfe-201">HDInsight Documentation</span></span>](https://docs.microsoft.com/azure/hdinsight/)
