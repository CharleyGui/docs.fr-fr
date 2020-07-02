---
title: Installer .NET pour Apache Spark sur des blocs-notes Jupyter sur des clusters Azure HDInsight Spark
description: Découvrez comment installer .NET pour Apache Spark sur les blocs-notes Jupyter d’Azure HDInsight.
ms.date: 06/25/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 14babf7a551192b286f309393e3bbff25d4745d5
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617741"
---
# <a name="install-net-for-apache-spark-on-jupyter-notebooks-on-azure-hdinsight-spark-clusters"></a><span data-ttu-id="aa3cf-103">Installer .NET pour Apache Spark sur des blocs-notes Jupyter sur des clusters Azure HDInsight Spark</span><span class="sxs-lookup"><span data-stu-id="aa3cf-103">Install .NET for Apache Spark on Jupyter notebooks on Azure HDInsight Spark clusters</span></span>

<span data-ttu-id="aa3cf-104">Cet article explique comment installer .NET pour Apache Spark sur des blocs-notes Jupyter sur des clusters Azure HDInsight Spark.</span><span class="sxs-lookup"><span data-stu-id="aa3cf-104">This article teaches you how to install .NET for Apache Spark on Jupyter notebooks on Azure HDInsight Spark clusters.</span></span> <span data-ttu-id="aa3cf-105">Vous pouvez déployer .NET pour Apache Spark sur les clusters Azure HDInsight à l’aide d’une combinaison de la ligne de commande et de la Portail Azure (pour plus d’informations, consultez [comment déployer une application .net pour Apache Spark sur Azure HDInsight](../tutorials/hdinsight-deployment.md)), mais les Notebooks offrent une expérience plus interactive et itérative.</span><span class="sxs-lookup"><span data-stu-id="aa3cf-105">You can deploy .NET for Apache Spark on Azure HDInsight clusters through a combination of the command line and the Azure portal (for more information, see [how to deploy a .NET for Apache Spark application to Azure HDInsight](../tutorials/hdinsight-deployment.md)), but notebooks provide a more interactive and iterative experience.</span></span>

<span data-ttu-id="aa3cf-106">Les clusters Azure HDInsight sont déjà fournis avec des blocs-notes Jupyter. il vous suffit de configurer les Notebooks Jupyter pour exécuter .NET pour Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="aa3cf-106">Azure HDInsight clusters already come with Jupyter notebooks, so all you have to do is configure the Jupyter notebooks to run .NET for Apache Spark.</span></span> <span data-ttu-id="aa3cf-107">Pour utiliser .NET pour Apache Spark dans vos blocs-notes Jupyter, une réplication C# est nécessaire pour exécuter votre code C# ligne par ligne et pour conserver l’état d’exécution si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="aa3cf-107">To use .NET for Apache Spark in your Jupyter notebooks, a C# REPL is needed to execute your C# code line-by-line and to preserve execution state when necessary.</span></span> <span data-ttu-id="aa3cf-108">[Essayez .net](https://github.com/dotnet/try) a été intégré en tant que repl .net officielle.</span><span class="sxs-lookup"><span data-stu-id="aa3cf-108">[Try .NET](https://github.com/dotnet/try) has been integrated as the official .NET REPL.</span></span>

<span data-ttu-id="aa3cf-109">Pour activer .NET pour Apache Spark via l’expérience Notebook Jupyter, vous devez suivre quelques étapes manuelles via [ambari](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-manage-ambari) et envoyer des [actions de script](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux) sur le cluster HDInsight Spark.</span><span class="sxs-lookup"><span data-stu-id="aa3cf-109">To enable .NET for Apache Spark through the Jupyter Notebooks experience, you need to follow a few manual steps through [Ambari](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-manage-ambari) and submit [script actions](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux) on the HDInsight Spark cluster.</span></span>

> [!NOTE]
> <span data-ttu-id="aa3cf-110">Cette fonctionnalité est *expérimentale* et n’est pas prise en charge par l’équipe HDInsight Spark.</span><span class="sxs-lookup"><span data-stu-id="aa3cf-110">This feature is *experimental* and is not supported by the HDInsight Spark team.</span></span>

[!INCLUDE [spark-preview-note](../../../includes/spark-preview-note.md)]

## <a name="prerequisites"></a><span data-ttu-id="aa3cf-111">Prérequis</span><span class="sxs-lookup"><span data-stu-id="aa3cf-111">Prerequisites</span></span>

<span data-ttu-id="aa3cf-112">Si vous n’en avez pas déjà un, créez un cluster [Azure HDInsight Spark](https://docs.microsoft.com/azure/hdinsight/spark/apache-spark-jupyter-spark-sql-use-portal#create-an-apache-spark-cluster-in-hdinsight) .</span><span class="sxs-lookup"><span data-stu-id="aa3cf-112">If you don't already have one, create an [Azure HDInsight Spark](https://docs.microsoft.com/azure/hdinsight/spark/apache-spark-jupyter-spark-sql-use-portal#create-an-apache-spark-cluster-in-hdinsight) cluster.</span></span>

1. <span data-ttu-id="aa3cf-113">Accédez au [portail Azure](https://portal.azure.com) et sélectionnez **+ créer une ressource**.</span><span class="sxs-lookup"><span data-stu-id="aa3cf-113">Visit the [Azure portal](https://portal.azure.com) and select **+ Create a Resource**.</span></span>

1. <span data-ttu-id="aa3cf-114">Créez une ressource de cluster Azure HDInsight.</span><span class="sxs-lookup"><span data-stu-id="aa3cf-114">Create a new Azure HDInsight cluster resource.</span></span> <span data-ttu-id="aa3cf-115">Sélectionnez **Spark 2,4** et **HDI 4,0** lors de la création du cluster.</span><span class="sxs-lookup"><span data-stu-id="aa3cf-115">Select **Spark 2.4** and **HDI 4.0** during cluster creation.</span></span>

## <a name="install-net-for-apache-spark"></a><span data-ttu-id="aa3cf-116">Installer .NET pour Apache Spark</span><span class="sxs-lookup"><span data-stu-id="aa3cf-116">Install .NET for Apache Spark</span></span>

<span data-ttu-id="aa3cf-117">Dans le Portail Azure, sélectionnez le **cluster HDInsight Spark** que vous avez créé à l’étape précédente.</span><span class="sxs-lookup"><span data-stu-id="aa3cf-117">In the Azure portal, select the **HDInsight Spark cluster** you created in the previous step.</span></span>

### <a name="stop-the-livy-server"></a><span data-ttu-id="aa3cf-118">Arrêter le serveur livy</span><span class="sxs-lookup"><span data-stu-id="aa3cf-118">Stop the Livy server</span></span>

1. <span data-ttu-id="aa3cf-119">Dans le portail, sélectionnez **vue d’ensemble**, puis sélectionnez **ambari**.</span><span class="sxs-lookup"><span data-stu-id="aa3cf-119">From the portal, select **Overview**, and then select **Ambari home**.</span></span> <span data-ttu-id="aa3cf-120">Si vous y êtes invité, entrez les informations d’identification de connexion du cluster.</span><span class="sxs-lookup"><span data-stu-id="aa3cf-120">If prompted, enter the login credentials for the cluster.</span></span>

   ![Arrêter le serveur livy Server](./media/hdinsight-notebook-installation/select-ambari.png)

2. <span data-ttu-id="aa3cf-122">Sélectionnez **Spark2** dans le menu de navigation de gauche, puis sélectionnez **LIVY pour Spark2 Server**.</span><span class="sxs-lookup"><span data-stu-id="aa3cf-122">Select **Spark2** from the left navigation menu, and select **LIVY FOR SPARK2 SERVER**.</span></span>

   ![Arrêter le serveur livy Server](./media/hdinsight-notebook-installation/select-livyserver.png)

3. <span data-ttu-id="aa3cf-124">Sélectionner **HN0... hôte**.</span><span class="sxs-lookup"><span data-stu-id="aa3cf-124">Select **hn0... host**.</span></span>

   ![Arrêter le serveur livy Server](./media/hdinsight-notebook-installation/select-host.png)

4. <span data-ttu-id="aa3cf-126">Sélectionnez les points de suspension en regard de **livy pour Spark2 Server** , puis sélectionnez **arrêter**.</span><span class="sxs-lookup"><span data-stu-id="aa3cf-126">Select the ellipsis next to **Livy for Spark2 Server** and select **Stop**.</span></span> <span data-ttu-id="aa3cf-127">Lorsque vous y êtes invité, sélectionnez **OK** pour continuer.</span><span class="sxs-lookup"><span data-stu-id="aa3cf-127">When prompted, select **OK** to proceed.</span></span>

   <span data-ttu-id="aa3cf-128">Arrêtez livy pour le serveur Spark2.</span><span class="sxs-lookup"><span data-stu-id="aa3cf-128">Stop Livy for Spark2 Server.</span></span>
   <span data-ttu-id="aa3cf-129">![Arrêter le serveur livy Server](./media/hdinsight-notebook-installation/stop-server.png)</span><span class="sxs-lookup"><span data-stu-id="aa3cf-129">![Stop Livy Server](./media/hdinsight-notebook-installation/stop-server.png)</span></span>

5. <span data-ttu-id="aa3cf-130">Répétez les étapes précédentes pour **HN1... hôte**.</span><span class="sxs-lookup"><span data-stu-id="aa3cf-130">Repeat the previous steps for **hn1... host**.</span></span>

### <a name="submit-an-hdinsight-script-action"></a><span data-ttu-id="aa3cf-131">Envoyer une action de script HDInsight</span><span class="sxs-lookup"><span data-stu-id="aa3cf-131">Submit an HDInsight script action</span></span>

1. <span data-ttu-id="aa3cf-132">Le `install-interactive-notebook.sh` est un script qui installe .net pour Apache Spark et apporte des modifications à Apache livy et sparkmagic.</span><span class="sxs-lookup"><span data-stu-id="aa3cf-132">The `install-interactive-notebook.sh` is a script that installs .NET for Apache Spark and makes changes to Apache Livy and sparkmagic.</span></span> <span data-ttu-id="aa3cf-133">Avant d’envoyer une action de script à HDInsight, vous devez créer et charger `install-interactive-notebook.sh` .</span><span class="sxs-lookup"><span data-stu-id="aa3cf-133">Before you submit a script action to HDInsight, you need to create and upload `install-interactive-notebook.sh`.</span></span>

   <span data-ttu-id="aa3cf-134">Créez un nouveau fichier nommé **install-interactive-Notebook.sh** sur votre ordinateur local et collez le contenu du [contenu de install-interactive-Notebook.sh](https://raw.githubusercontent.com/dotnet/spark/master/deployment/HDI-Spark/Notebooks/install-interactive-notebook.sh).</span><span class="sxs-lookup"><span data-stu-id="aa3cf-134">Create a new file named **install-interactive-notebook.sh** in your local computer and paste the contents of [install-interactive-notebook.sh contents](https://raw.githubusercontent.com/dotnet/spark/master/deployment/HDI-Spark/Notebooks/install-interactive-notebook.sh).</span></span>

   <span data-ttu-id="aa3cf-135">Téléchargez le script vers un [URI](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux#understand-script-actions) accessible à partir du cluster HDInsight.</span><span class="sxs-lookup"><span data-stu-id="aa3cf-135">Upload the script to a [URI](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux#understand-script-actions) that's accessible from the HDInsight cluster.</span></span> <span data-ttu-id="aa3cf-136">Par exemple : `https://<my storage account>.blob.core.windows.net/<my container>/<some dir>/install-interactive-notebook.sh`.</span><span class="sxs-lookup"><span data-stu-id="aa3cf-136">For example, `https://<my storage account>.blob.core.windows.net/<my container>/<some dir>/install-interactive-notebook.sh`.</span></span>

2. <span data-ttu-id="aa3cf-137">Exécutez `install-interactive-notebook.sh` sur le cluster en utilisant des [actions de script HDInsight](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux).</span><span class="sxs-lookup"><span data-stu-id="aa3cf-137">Run `install-interactive-notebook.sh` on the cluster using [HDInsight Script Actions](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux).</span></span>

   <span data-ttu-id="aa3cf-138">Revenez à votre cluster HDI dans le Portail Azure, puis sélectionnez **actions de script** dans les options de gauche.</span><span class="sxs-lookup"><span data-stu-id="aa3cf-138">Return to your HDI cluster in the Azure portal, and select **Script actions** from the options on the left.</span></span> <span data-ttu-id="aa3cf-139">Vous envoyez une action de script pour déployer le .NET pour Apache Spark REPL sur votre cluster HDInsight Spark.</span><span class="sxs-lookup"><span data-stu-id="aa3cf-139">You submit one script action to deploy the .NET for Apache Spark REPL on your HDInsight Spark cluster.</span></span> <span data-ttu-id="aa3cf-140">Utilisez les paramètres suivants :</span><span class="sxs-lookup"><span data-stu-id="aa3cf-140">Use the following settings:</span></span>

   |<span data-ttu-id="aa3cf-141">Propriété</span><span class="sxs-lookup"><span data-stu-id="aa3cf-141">Property</span></span>  |<span data-ttu-id="aa3cf-142">Description</span><span class="sxs-lookup"><span data-stu-id="aa3cf-142">Description</span></span>  |
   |---------|---------|
   | <span data-ttu-id="aa3cf-143">Type de script</span><span class="sxs-lookup"><span data-stu-id="aa3cf-143">Script type</span></span> | <span data-ttu-id="aa3cf-144">Personnalisé</span><span class="sxs-lookup"><span data-stu-id="aa3cf-144">Custom</span></span> |
   | <span data-ttu-id="aa3cf-145">Nom</span><span class="sxs-lookup"><span data-stu-id="aa3cf-145">Name</span></span> | <span data-ttu-id="aa3cf-146">*Installer .NET pour Apache Spark l’expérience du bloc-notes interactif*</span><span class="sxs-lookup"><span data-stu-id="aa3cf-146">*Install .NET for Apache Spark Interactive Notebook Experience*</span></span> |
   | <span data-ttu-id="aa3cf-147">URI de script bash</span><span class="sxs-lookup"><span data-stu-id="aa3cf-147">Bash script URI</span></span> | <span data-ttu-id="aa3cf-148">URI vers lequel vous avez chargé `install-interactive-notebook.sh`.</span><span class="sxs-lookup"><span data-stu-id="aa3cf-148">The URI to which you uploaded `install-interactive-notebook.sh`.</span></span> |
   | <span data-ttu-id="aa3cf-149">Type(s) de nœud</span><span class="sxs-lookup"><span data-stu-id="aa3cf-149">Node type(s)</span></span>| <span data-ttu-id="aa3cf-150">Tête et Worker</span><span class="sxs-lookup"><span data-stu-id="aa3cf-150">Head and Worker</span></span> |
   | <span data-ttu-id="aa3cf-151">Paramètres</span><span class="sxs-lookup"><span data-stu-id="aa3cf-151">Parameters</span></span> | <span data-ttu-id="aa3cf-152">.NET pour la version de Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="aa3cf-152">.NET for Apache Spark version.</span></span> <span data-ttu-id="aa3cf-153">Vous pouvez vérifier [les versions de Apache Spark dans .net](https://github.com/dotnet/spark/releases).</span><span class="sxs-lookup"><span data-stu-id="aa3cf-153">You can check [.NET for Apache Spark releases](https://github.com/dotnet/spark/releases).</span></span> <span data-ttu-id="aa3cf-154">Par exemple, si vous souhaitez installer Sparkdotnet version 0.6.0, il s’agit de `0.6.0` .</span><span class="sxs-lookup"><span data-stu-id="aa3cf-154">For example, if you want to install Sparkdotnet version 0.6.0 then it would be `0.6.0`.</span></span>

   <span data-ttu-id="aa3cf-155">Passer à l’étape suivante quand des coches vertes s’affichent en regard de l’état de l’action de script.</span><span class="sxs-lookup"><span data-stu-id="aa3cf-155">Move to the next step when green checkmarks appear next to the status of the script action.</span></span>

### <a name="start-the-livy-server"></a><span data-ttu-id="aa3cf-156">Démarrer le serveur livy</span><span class="sxs-lookup"><span data-stu-id="aa3cf-156">Start the Livy server</span></span>

<span data-ttu-id="aa3cf-157">Suivez les instructions de la section [Stop livy Server](#stop-the-livy-server) pour **Démarrer** (au lieu d' **arrêter**) le livy pour Spark2 Server pour les hôtes **HN0** et **HN1**.</span><span class="sxs-lookup"><span data-stu-id="aa3cf-157">Follow the instructions in the [Stop Livy server](#stop-the-livy-server) section to **Start** (rather than **Stop**) the Livy for Spark2 Server for hosts **hn0** and **hn1**.</span></span>

### <a name="set-up-spark-default-configurations"></a><span data-ttu-id="aa3cf-158">Configurer des configurations Spark par défaut</span><span class="sxs-lookup"><span data-stu-id="aa3cf-158">Set up Spark default configurations</span></span>

1. <span data-ttu-id="aa3cf-159">Dans le portail, sélectionnez **vue d’ensemble**, puis sélectionnez **ambari**.</span><span class="sxs-lookup"><span data-stu-id="aa3cf-159">From the portal, select **Overview**, and then select **Ambari home**.</span></span> <span data-ttu-id="aa3cf-160">À l’invite (le cas échéant), entrez les informations d’identification du cluster.</span><span class="sxs-lookup"><span data-stu-id="aa3cf-160">If prompted, enter the cluster login credentials for the cluster.</span></span>

2. <span data-ttu-id="aa3cf-161">Sélectionnez **Spark2** et **configurations**.</span><span class="sxs-lookup"><span data-stu-id="aa3cf-161">Select **Spark2** and **CONFIGS**.</span></span> <span data-ttu-id="aa3cf-162">Ensuite, sélectionnez **Spark2 personnalisé-valeurs par défaut**.</span><span class="sxs-lookup"><span data-stu-id="aa3cf-162">Then, select **Custom spark2-defaults**.</span></span>

   ![Définir les configurations](./media/hdinsight-notebook-installation/spark-configs.png)

3. <span data-ttu-id="aa3cf-164">Sélectionnez **Ajouter une propriété...** pour ajouter des paramètres Spark par défaut.</span><span class="sxs-lookup"><span data-stu-id="aa3cf-164">Select **Add Property...** to add Spark default settings.</span></span>

   ![Ajouter une propriété](./media/hdinsight-notebook-installation/add-property.png)

   <span data-ttu-id="aa3cf-166">Il existe trois propriétés individuelles.</span><span class="sxs-lookup"><span data-stu-id="aa3cf-166">There are three individual properties.</span></span> <span data-ttu-id="aa3cf-167">Ajoutez-les un par un à l’aide du type de propriété **Text** en mode d’ajout de propriété unique.</span><span class="sxs-lookup"><span data-stu-id="aa3cf-167">Add them one at a time using the **TEXT** property type in Single property add mode.</span></span> <span data-ttu-id="aa3cf-168">Vérifiez que vous n’avez pas d’espace supplémentaire avant ou après les clés/valeurs.</span><span class="sxs-lookup"><span data-stu-id="aa3cf-168">Check that you don't have any extra spaces before or after any of the keys/values.</span></span>

   * <span data-ttu-id="aa3cf-169">**Propriété 1**</span><span class="sxs-lookup"><span data-stu-id="aa3cf-169">**Property 1**</span></span>
       * <span data-ttu-id="aa3cf-170">Essentiel&ensp;&ensp;`spark.dotnet.shell.command`</span><span class="sxs-lookup"><span data-stu-id="aa3cf-170">Key:&ensp;&ensp;`spark.dotnet.shell.command`</span></span>
       * <span data-ttu-id="aa3cf-171">Valeur: `/usr/share/dotnet-tools/dotnet-try,kernel-server,--default-kernel,csharp`</span><span class="sxs-lookup"><span data-stu-id="aa3cf-171">Value: `/usr/share/dotnet-tools/dotnet-try,kernel-server,--default-kernel,csharp`</span></span>

   * <span data-ttu-id="aa3cf-172">**Propriété 2** Utilisez la version de .NET pour Apache Spark que vous avez incluse dans l’action de script précédente.</span><span class="sxs-lookup"><span data-stu-id="aa3cf-172">**Property 2** Use the version of .NET for Apache Spark which you had included in the previous script action.</span></span>
       * <span data-ttu-id="aa3cf-173">Essentiel&ensp;&ensp;`spark.dotnet.packages`</span><span class="sxs-lookup"><span data-stu-id="aa3cf-173">Key:&ensp;&ensp;`spark.dotnet.packages`</span></span>
       * <span data-ttu-id="aa3cf-174">Valeur: `["nuget: Microsoft.Spark, 0.6.0", "nuget: Microsoft.Spark.Extensions.Delta, 0.6.0"]`</span><span class="sxs-lookup"><span data-stu-id="aa3cf-174">Value: `["nuget: Microsoft.Spark, 0.6.0", "nuget: Microsoft.Spark.Extensions.Delta, 0.6.0"]`</span></span>

   * <span data-ttu-id="aa3cf-175">**Propriété 3**</span><span class="sxs-lookup"><span data-stu-id="aa3cf-175">**Property 3**</span></span>
       * <span data-ttu-id="aa3cf-176">Essentiel&ensp;&ensp;`spark.dotnet.interpreter`</span><span class="sxs-lookup"><span data-stu-id="aa3cf-176">Key:&ensp;&ensp;`spark.dotnet.interpreter`</span></span>
       * <span data-ttu-id="aa3cf-177">Valeur: `try`</span><span class="sxs-lookup"><span data-stu-id="aa3cf-177">Value: `try`</span></span>

   <span data-ttu-id="aa3cf-178">Par exemple, l’image suivante capture le paramètre pour l’ajout de la propriété 1 :</span><span class="sxs-lookup"><span data-stu-id="aa3cf-178">For example, the following image captures the setting for adding property 1:</span></span>

   ![Définir les configurations](./media/hdinsight-notebook-installation/add-sparkconfig.png)

   <span data-ttu-id="aa3cf-180">Après avoir ajouté les trois propriétés, sélectionnez **Enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="aa3cf-180">After adding the three properties, select **SAVE**.</span></span> <span data-ttu-id="aa3cf-181">Si vous voyez un écran d’avertissement des recommandations de configuration, sélectionnez **continuer quand même**.</span><span class="sxs-lookup"><span data-stu-id="aa3cf-181">If you see a warning screen of config recommendations, select **PROCEED ANYWAY**.</span></span>

4. <span data-ttu-id="aa3cf-182">Redémarrez les composants affectés.</span><span class="sxs-lookup"><span data-stu-id="aa3cf-182">Restart affected components.</span></span>

   <span data-ttu-id="aa3cf-183">Après avoir ajouté les nouvelles propriétés, vous devez redémarrer les composants qui ont été affectés par les modifications.</span><span class="sxs-lookup"><span data-stu-id="aa3cf-183">After adding the new properties, you need to restart components that were affected by the changes.</span></span> <span data-ttu-id="aa3cf-184">En haut, sélectionnez **redémarrer**, puis **Redémarrez tous les affectés** à partir de la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="aa3cf-184">At the top, select **RESTART**, and then **Restart All Affected** from the drop-down.</span></span>

   ![Définir les configurations](./media/hdinsight-notebook-installation/restart-affected.png)

   <span data-ttu-id="aa3cf-186">Lorsque vous y êtes invité, sélectionnez **confirmer redémarrer tout** pour continuer, puis cliquez sur **OK** pour terminer.</span><span class="sxs-lookup"><span data-stu-id="aa3cf-186">When prompted, select **CONFIRM RESTART ALL** to continue, then click **OK** to finish.</span></span>

## <a name="submit-jobs-through-a-jupyter-notebook"></a><span data-ttu-id="aa3cf-187">Envoyer des travaux par le biais d’un bloc-notes Jupyter</span><span class="sxs-lookup"><span data-stu-id="aa3cf-187">Submit jobs through a Jupyter notebook</span></span>

<span data-ttu-id="aa3cf-188">Une fois les étapes précédentes terminées, vous pouvez désormais envoyer votre .NET pour les tâches de Apache Spark via des blocs-notes Jupyter.</span><span class="sxs-lookup"><span data-stu-id="aa3cf-188">After finishing the previous steps, you can now submit your .NET for Apache Spark jobs through Jupyter notebooks.</span></span>

1. <span data-ttu-id="aa3cf-189">Créez un nouveau .NET pour Apache Spark bloc-notes.</span><span class="sxs-lookup"><span data-stu-id="aa3cf-189">Create a new .NET for Apache Spark notebook.</span></span> <span data-ttu-id="aa3cf-190">Lancez un bloc-notes Jupyter à partir de votre cluster HDI dans le Portail Azure.</span><span class="sxs-lookup"><span data-stu-id="aa3cf-190">Launch a Jupyter notebook from your HDI cluster in the Azure portal.</span></span>

   ![Lancer Jupyter Notebook](./media/hdinsight-notebook-installation/launch-notebook.png)

   <span data-ttu-id="aa3cf-192">Ensuite, sélectionnez **nouveau**  >  **.net Spark (C#)** pour créer un bloc-notes.</span><span class="sxs-lookup"><span data-stu-id="aa3cf-192">Then, select **New** > **.NET Spark (C#)** to create a notebook.</span></span>

   ![Jupyter Notebook](./media/hdinsight-notebook-installation/create-sparkdotnet-notebook.png)

2. <span data-ttu-id="aa3cf-194">Envoyer des travaux à l’aide de .NET pour Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="aa3cf-194">Submit jobs using .NET for Apache Spark.</span></span>

   <span data-ttu-id="aa3cf-195">Utilisez l’extrait de code suivant pour créer un tableau :</span><span class="sxs-lookup"><span data-stu-id="aa3cf-195">Use the following code snippet to create a DataFrame:</span></span>

   ```csharp
   var df = spark.Range(0,5);
   df.Show();
   ```

   ![Envoyer le travail Spark](./media/hdinsight-notebook-installation/create-df.png)

   <span data-ttu-id="aa3cf-197">Utilisez l’extrait de code suivant pour inscrire une fonction définie par l’utilisateur et utiliser l’UDF avec trames :</span><span class="sxs-lookup"><span data-stu-id="aa3cf-197">Use the following code snippet to register a user-defined function (UDF) and use the UDF with DataFrames:</span></span>

   ```csharp
   var myawesomeudf = Udf<int, string>((id) => $"hello {id}");
   df.Select(myawesomeudf(df["id"])).Show();
   ```

   ![Envoyer le travail Spark](./media/hdinsight-notebook-installation/run-udf.png)

## <a name="next-steps"></a><span data-ttu-id="aa3cf-199">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="aa3cf-199">Next steps</span></span>

* [<span data-ttu-id="aa3cf-200">Déployer une application .NET pour Apache Spark sur Azure HDInsight</span><span class="sxs-lookup"><span data-stu-id="aa3cf-200">Deploy a .NET for Apache Spark application to Azure HDInsight</span></span>](../tutorials/hdinsight-deployment.md)
* [<span data-ttu-id="aa3cf-201">Documentation HDInsight</span><span class="sxs-lookup"><span data-stu-id="aa3cf-201">HDInsight Documentation</span></span>](https://docs.microsoft.com/azure/hdinsight/)
