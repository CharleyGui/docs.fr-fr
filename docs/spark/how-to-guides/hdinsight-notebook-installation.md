---
title: Installer .NET pour Apache Spark sur des blocs-notes Jupyter sur des clusters Azure HDInsight Spark
description: Découvrez comment installer .NET pour Apache Spark sur les blocs-notes Jupyter d’Azure HDInsight.
ms.date: 06/25/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 8110b87991e2f0253257faf19f383dec6cbd3853
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557201"
---
# <a name="install-net-for-apache-spark-on-jupyter-notebooks-on-azure-hdinsight-spark-clusters"></a>Installer .NET pour Apache Spark sur des blocs-notes Jupyter sur des clusters Azure HDInsight Spark

Cet article explique comment installer .NET pour Apache Spark sur des blocs-notes Jupyter sur des clusters Azure HDInsight Spark. Vous pouvez déployer .NET pour Apache Spark sur les clusters Azure HDInsight à l’aide d’une combinaison de la ligne de commande et de la Portail Azure (pour plus d’informations, consultez [comment déployer une application .net pour Apache Spark sur Azure HDInsight](../tutorials/hdinsight-deployment.md)), mais les Notebooks offrent une expérience plus interactive et itérative.

Les clusters Azure HDInsight sont déjà fournis avec des blocs-notes Jupyter. il vous suffit de configurer les Notebooks Jupyter pour exécuter .NET pour Apache Spark. Pour utiliser .NET pour Apache Spark dans vos blocs-notes Jupyter, une réplication C# est nécessaire pour exécuter votre code C# ligne par ligne et pour conserver l’état d’exécution si nécessaire. [Essayez .net](https://github.com/dotnet/try) a été intégré en tant que repl .net officielle.

Pour activer .NET pour Apache Spark via l’expérience Notebook Jupyter, vous devez suivre quelques étapes manuelles via [ambari](/azure/hdinsight/hdinsight-hadoop-manage-ambari) et envoyer des [actions de script](/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux) sur le cluster HDInsight Spark.

> [!NOTE]
> Cette fonctionnalité est *expérimentale* et n’est pas prise en charge par l’équipe HDInsight Spark.

[!INCLUDE [spark-preview-note](../../../includes/spark-preview-note.md)]

## <a name="prerequisites"></a>Prérequis

Si vous n’en avez pas déjà un, créez un cluster [Azure HDInsight Spark](/azure/hdinsight/spark/apache-spark-jupyter-spark-sql-use-portal#create-an-apache-spark-cluster-in-hdinsight) .

1. Accédez au [portail Azure](https://portal.azure.com) et sélectionnez **+ créer une ressource**.

1. Créez une ressource de cluster Azure HDInsight. Sélectionnez **Spark 2,4** et **HDI 4,0** lors de la création du cluster.

## <a name="install-net-for-apache-spark"></a>Installer .NET pour Apache Spark

Dans le Portail Azure, sélectionnez le **cluster HDInsight Spark** que vous avez créé à l’étape précédente.

### <a name="stop-the-livy-server"></a>Arrêter le serveur livy

1. Dans le portail, sélectionnez **vue d’ensemble**, puis sélectionnez **ambari**. Si vous y êtes invité, entrez les informations d’identification de connexion du cluster.

   ![Arrêter le serveur livy Server](./media/hdinsight-notebook-installation/select-ambari.png)

2. Sélectionnez **Spark2** dans le menu de navigation de gauche, puis sélectionnez **LIVY pour Spark2 Server**.

   ![Arrêter le serveur livy Server](./media/hdinsight-notebook-installation/select-livyserver.png)

3. Sélectionner **HN0... hôte**.

   ![Arrêter le serveur livy Server](./media/hdinsight-notebook-installation/select-host.png)

4. Sélectionnez les points de suspension en regard de **livy pour Spark2 Server** , puis sélectionnez **arrêter**. Lorsque vous y êtes invité, sélectionnez **OK** pour continuer.

   Arrêtez livy pour le serveur Spark2.
   ![Arrêter le serveur livy Server](./media/hdinsight-notebook-installation/stop-server.png)

5. Répétez les étapes précédentes pour **HN1... hôte**.

### <a name="submit-an-hdinsight-script-action"></a>Envoyer une action de script HDInsight

1. Le `install-interactive-notebook.sh` est un script qui installe .net pour Apache Spark et apporte des modifications à Apache livy et sparkmagic. Avant d’envoyer une action de script à HDInsight, vous devez créer et charger `install-interactive-notebook.sh` .

   Créez un nouveau fichier nommé **install-interactive-Notebook.sh** sur votre ordinateur local et collez le contenu du [contenu de install-interactive-Notebook.sh](https://raw.githubusercontent.com/dotnet/spark/master/deployment/HDI-Spark/Notebooks/install-interactive-notebook.sh).

   Téléchargez le script vers un [URI](/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux#understand-script-actions) accessible à partir du cluster HDInsight. Par exemple : `https://<my storage account>.blob.core.windows.net/<my container>/<some dir>/install-interactive-notebook.sh`.

2. Exécutez `install-interactive-notebook.sh` sur le cluster en utilisant des [actions de script HDInsight](/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux).

   Revenez à votre cluster HDI dans le Portail Azure, puis sélectionnez **actions de script** dans les options de gauche. Vous envoyez une action de script pour déployer le .NET pour Apache Spark REPL sur votre cluster HDInsight Spark. Utilisez les paramètres suivants :

   |Propriété  |Description  |
   |---------|---------|
   | Type de script | Custom |
   | Name | *Installer .NET pour Apache Spark l’expérience du bloc-notes interactif* |
   | URI de script bash | URI vers lequel vous avez chargé `install-interactive-notebook.sh`. |
   | Type(s) de nœud| Tête et Worker |
   | Paramètres | .NET pour la version de Apache Spark. Vous pouvez vérifier [les versions de Apache Spark dans .net](https://github.com/dotnet/spark/releases). Par exemple, si vous souhaitez installer Sparkdotnet version 0.6.0, il s’agit de `0.6.0` .

   Passer à l’étape suivante quand des coches vertes s’affichent en regard de l’état de l’action de script.

### <a name="start-the-livy-server"></a>Démarrer le serveur livy

Suivez les instructions de la section [Stop livy Server](#stop-the-livy-server) pour **Démarrer** (au lieu d' **arrêter**) le livy pour Spark2 Server pour les hôtes **HN0** et **HN1**.

### <a name="set-up-spark-default-configurations"></a>Configurer des configurations Spark par défaut

1. Dans le portail, sélectionnez **vue d’ensemble**, puis sélectionnez **ambari**. À l’invite (le cas échéant), entrez les informations d’identification du cluster.

2. Sélectionnez **Spark2** et **configurations**. Ensuite, sélectionnez **Spark2 personnalisé-valeurs par défaut**.

   ![Définir les configurations](./media/hdinsight-notebook-installation/spark-configs.png)

3. Sélectionnez **Ajouter une propriété...** pour ajouter des paramètres Spark par défaut.

   ![Ajouter une propriété](./media/hdinsight-notebook-installation/add-property.png)

   Il existe trois propriétés individuelles. Ajoutez-les un par un à l’aide du type de propriété **Text** en mode d’ajout de propriété unique. Vérifiez que vous n’avez pas d’espace supplémentaire avant ou après les clés/valeurs.

   * **Propriété 1**
       * Essentiel&ensp;&ensp;`spark.dotnet.shell.command`
       * Valeur: `/usr/share/dotnet-tools/dotnet-try,kernel-server,--default-kernel,csharp`

   * **Propriété 2** Utilisez la version de .NET pour Apache Spark que vous avez incluse dans l’action de script précédente.
       * Essentiel&ensp;&ensp;`spark.dotnet.packages`
       * Valeur: `["nuget: Microsoft.Spark, 0.6.0", "nuget: Microsoft.Spark.Extensions.Delta, 0.6.0"]`

   * **Propriété 3**
       * Essentiel&ensp;&ensp;`spark.dotnet.interpreter`
       * Valeur: `try`

   Par exemple, l’image suivante capture le paramètre pour l’ajout de la propriété 1 :

   ![Définir les configurations](./media/hdinsight-notebook-installation/add-sparkconfig.png)

   Après avoir ajouté les trois propriétés, sélectionnez **Enregistrer**. Si vous voyez un écran d’avertissement des recommandations de configuration, sélectionnez **continuer quand même**.

4. Redémarrez les composants affectés.

   Après avoir ajouté les nouvelles propriétés, vous devez redémarrer les composants qui ont été affectés par les modifications. En haut, sélectionnez **redémarrer**, puis **Redémarrez tous les affectés** à partir de la liste déroulante.

   ![Définir les configurations](./media/hdinsight-notebook-installation/restart-affected.png)

   Lorsque vous y êtes invité, sélectionnez **confirmer redémarrer tout** pour continuer, puis cliquez sur **OK** pour terminer.

## <a name="submit-jobs-through-a-jupyter-notebook"></a>Envoyer des travaux par le biais d’un bloc-notes Jupyter

Une fois les étapes précédentes terminées, vous pouvez désormais envoyer votre .NET pour les tâches de Apache Spark via des blocs-notes Jupyter.

1. Créez un nouveau .NET pour Apache Spark bloc-notes. Lancez un bloc-notes Jupyter à partir de votre cluster HDI dans le Portail Azure.

   ![Lancer Jupyter Notebook](./media/hdinsight-notebook-installation/launch-notebook.png)

   Ensuite, sélectionnez **nouveau**  >  **.net Spark (C#)** pour créer un bloc-notes.

   ![Jupyter Notebook](./media/hdinsight-notebook-installation/create-sparkdotnet-notebook.png)

2. Envoyer des travaux à l’aide de .NET pour Apache Spark.

   Utilisez l’extrait de code suivant pour créer un tableau :

   ```csharp
   var df = spark.Range(0,5);
   df.Show();
   ```

   ![Envoyer le travail Spark](./media/hdinsight-notebook-installation/create-df.png)

   Utilisez l’extrait de code suivant pour inscrire une fonction définie par l’utilisateur et utiliser l’UDF avec trames :

   ```csharp
   var myawesomeudf = Udf<int, string>((id) => $"hello {id}");
   df.Select(myawesomeudf(df["id"])).Show();
   ```

   ![Envoyer le travail Spark](./media/hdinsight-notebook-installation/run-udf.png)

## <a name="next-steps"></a>Étapes suivantes

* [Déployer une application .NET pour Apache Spark sur Azure HDInsight](../tutorials/hdinsight-deployment.md)
* [Documentation HDInsight](/azure/hdinsight/)
