---
title: Installer .NET pour Apache Spark sur les ordinateurs portables Jupyter sur les clusters Azure HDInsight Spark
description: Découvrez comment installer .NET pour Apache Spark sur azure HDInsight’s Jupyter Notebooks.
ms.date: 03/13/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 32047efcde093a3752bdd59baa88896d1547b93e
ms.sourcegitcommit: 34dc3c0d0d0a1cc418abff259d9daa8078d00b81
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2020
ms.locfileid: "79546748"
---
# <a name="install-net-for-apache-spark-on-jupyter-notebooks-on-azure-hdinsight-spark-clusters"></a>Installer .NET pour Apache Spark sur les ordinateurs portables Jupyter sur les clusters Azure HDInsight Spark

Cet article vous apprend à installer .NET pour Apache Spark sur les ordinateurs portables Jupyter sur les clusters Azure HDInsight Spark. Vous pouvez déployer .NET pour Apache Spark sur les clusters HDInsight Azure grâce à une combinaison de la ligne de commande et du portail Azure (pour plus d’informations, voir [comment déployer une application .NET pour Apache Spark à Azure HDInsight),](../tutorials/hdinsight-deployment.md)mais les ordinateurs portables offrent une expérience plus interactive et itérative.

Les clusters Azure HDInsight sont déjà livrés avec des ordinateurs portables Jupyter, donc tout ce que vous avez à faire est de configurer les ordinateurs portables Jupyter pour exécuter .NET pour Apache Spark. Pour utiliser .NET pour Apache Spark dans vos ordinateurs portables Jupyter, un REPL C est nécessaire pour exécuter votre code CMD ligne par ligne et pour préserver l’état d’exécution si nécessaire. [Essayez .NET](https://github.com/dotnet/try) a été intégré comme le REPL officiel .NET.

Pour activer .NET pour Apache Spark grâce à l’expérience Jupyter Notebooks, vous devez suivre quelques étapes manuelles à travers [Ambari](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-manage-ambari) et soumettre des [actions de script](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux) sur le cluster HDInsight Spark.

> [!NOTE]
> Cette fonctionnalité est *expérimentale* et n’est pas prise en charge par l’équipe HDInsight Spark.

## <a name="prerequisites"></a>Conditions préalables requises

Si vous n’en avez pas déjà, créez un cluster [Azure HDInsight Spark.](https://docs.microsoft.com/azure/hdinsight/spark/apache-spark-jupyter-spark-sql-use-portal#create-an-hdinsight-spark-cluster)

1. Visitez le [portail Azure](https://portal.azure.com) et sélectionnez **- Créer une ressource**.

1. Créez une nouvelle ressource en cluster Azure HDInsight. Sélectionnez **Spark 2.4** et **HDI 4.0** lors de la création de grappes.

## <a name="install-net-for-apache-spark"></a>Installer .NET pour Apache Spark

Dans le portail Azure, sélectionnez le **cluster HDInsight Spark** que vous avez créé dans l’étape précédente.

### <a name="stop-the-livy-server"></a>Arrêtez le serveur Livy

1. À partir du portail, sélectionnez **Aperçu,** puis sélectionnez **Ambari à la maison**. Si vous êtes invité, entrez les identifiants de connexion pour le cluster.

   ![Arrêter Livy Server](./media/hdinsight-notebook-installation/select-ambari.png)

2. Sélectionnez **Spark2** dans le menu de navigation gauche, et sélectionnez **LIVY FOR SPARK2 SERVER**.

   ![Arrêter Livy Server](./media/hdinsight-notebook-installation/select-livyserver.png)

3. Sélectionnez **hn0... hôte**.

   ![Arrêter Livy Server](./media/hdinsight-notebook-installation/select-host.png)

4. Sélectionnez l’ellipsis à côté de **Livy pour Spark2 Server** et sélectionnez **Stop**. Lorsqu’on l’a invité, sélectionnez **OK** pour procéder.

   Arrêtez Livy pour Spark2 Server.
   ![Arrêter Livy Server](./media/hdinsight-notebook-installation/stop-server.png)

5. Répétez les étapes précédentes pour **hn1... hôte**.

### <a name="submit-an-hdinsight-script-action"></a>Soumettre une action de script HDInsight

1. Le `install-interactive-notebook.sh` est un script qui installe .NET pour Apache Spark et apporte des modifications à Apache Livy et sparkmagic. Avant de soumettre une action de script à HDInsight, vous devez créer et télécharger `install-interactive-notebook.sh`.

   Créez un nouveau fichier nommé **install-interactive-notebook.sh** dans votre ordinateur local et collez le contenu de [install-interactive-notebook.sh contenu](https://raw.githubusercontent.com/dotnet/spark/master/deployment/HDI-Spark/Notebooks/install-interactive-notebook.sh).

   Téléchargez le script sur un [URI](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux#understand-script-actions) accessible à partir du cluster HDInsight. Par exemple : `https://<my storage account>.blob.core.windows.net/<my container>/<some dir>/install-interactive-notebook.sh`.

2. Exécutez `install-interactive-notebook.sh` sur le cluster en utilisant des [actions de script HDInsight](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux).

   Retournez à votre cluster HDI dans le portail Azure et sélectionnez les **actions Script** des options de gauche. Vous soumettez une action de script pour déployer le .NET pour Apache Spark REPL sur votre cluster HDInsight Spark. Utilisez les paramètres suivants :

   |Propriété  |Description  |
   |---------|---------|
   | Type de script | Custom |
   | Nom | *Installer .NET pour Apache Spark Interactive Notebook Experience* |
   | URI de script bash | URI vers lequel vous avez chargé `install-interactive-notebook.sh`. |
   | Type(s) de nœud| Chef et travailleur |
   | Paramètres | .NET pour la version Apache Spark. Vous pouvez vérifier [.NET pour apache Spark versions](https://github.com/dotnet/spark/releases). Par exemple, si vous voulez installer la version Sparkdotnet 0.6.0 alors il serait `0.6.0`.

   Passez à l’étape suivante lorsque les marques de contrôle vertes apparaissent à côté de l’état de l’action de script.

### <a name="start-the-livy-server"></a>Démarrer le serveur Livy

Suivez les instructions dans la section [serveur Stop Livy](#stop-the-livy-server) pour **démarrer** (plutôt que **d’arrêter**) le Livy pour Spark2 Server pour les hôtes **hn0** et **hn1**.

### <a name="set-up-spark-default-configurations"></a>Configurez des configurations par défaut Spark

1. À partir du portail, sélectionnez **Aperçu,** puis sélectionnez **Ambari à la maison**. À l’invite (le cas échéant), entrez les informations d’identification du cluster.

2. Sélectionnez **Spark2** et **CONFIGS**. Ensuite, sélectionnez **Custom spark2-defaults**.

   ![Définir Configs](./media/hdinsight-notebook-installation/spark-configs.png)

3. Sélectionnez **Ajouter la propriété...** pour ajouter les paramètres par défaut Spark.

   ![Ajouter une propriété](./media/hdinsight-notebook-installation/add-property.png)

   Il y a trois propriétés individuelles. Ajoutez-les un à la fois en utilisant le type de propriété **TEXT** en mode Unique ajouter. Vérifiez que vous n’avez pas d’espaces supplémentaires avant ou après l’une des clés/valeurs.

   * **Propriété 1**
       * Clé:&ensp;&ensp;`spark.dotnet.shell.command`
       * Valeur: `/usr/share/dotnet-tools/dotnet-try,kernel-server,--default-kernel,csharp`

   * **Propriété 2** Utilisez la version de .NET pour Apache Spark que vous aviez inclus dans l’action de script précédente.
       * Clé:&ensp;&ensp;`spark.dotnet.packages`
       * Valeur: `["nuget: Microsoft.Spark, 0.6.0", "nuget: Microsoft.Spark.Extensions.Delta, 0.6.0"]`

   * **Propriété 3**
       * Clé:&ensp;&ensp;`spark.dotnet.interpreter`
       * Valeur: `try`

   Par exemple, l’image suivante capture le paramètre pour l’ajout de la propriété 1 :

   ![Définir Configs](./media/hdinsight-notebook-installation/add-sparkconfig.png)

   Après l’ajout des trois propriétés, sélectionnez **SAVE**. Si vous voyez un écran d’avertissement des recommandations config, sélectionnez **PROCEED ANYWAY**.

4. Redémarrer les composants affectés.

   Après l’ajout des nouvelles propriétés, vous devez redémarrer les composants qui ont été affectés par les changements. En haut, sélectionnez **RESTART,** puis **redémarrez tous les touchés** à partir de la descente.

   ![Définir Configs](./media/hdinsight-notebook-installation/restart-affected.png)

   Lorsqu’on l’a invité, sélectionnez **CONFIRM RESTART ALL** pour continuer, puis cliquez sur **OK** pour terminer.

## <a name="submit-jobs-through-a-jupyter-notebook"></a>Soumettre des emplois par l’intermédiaire d’un carnet Jupyter

Après avoir terminé les étapes précédentes, vous pouvez maintenant soumettre votre .NET pour apache Spark emplois à travers les ordinateurs portables Jupyter.

1. Créez un nouveau .NET pour le carnet Apache Spark. Lancez un ordinateur portable Jupyter depuis votre cluster HDI dans le portail Azure.

   ![Lancement du carnet Jupyter](./media/hdinsight-notebook-installation/launch-notebook.png)

   Ensuite, sélectionnez **New** > **.NET Spark (C)** pour créer un ordinateur portable.

   ![Jupyter Notebook](./media/hdinsight-notebook-installation/create-sparkdotnet-notebook.png)

2. Soumettez des travaux en utilisant .NET pour Apache Spark.

   Utilisez l’extrait de code suivant pour créer un DataFrame :

   ```csharp
   var df = spark.Range(0,5);
   df.Show();
   ```

   ![Soumettre Spark Job](./media/hdinsight-notebook-installation/create-df.png)

   Utilisez l’extrait de code suivant pour enregistrer une fonction définie par l’utilisateur (UDF) et utiliser l’UDF avec DataFrames :

   ```csharp
   var myawesomeudf = Udf<int, string>((id) => $"hello {id}");
   df.Select(myawesomeudf(df["id"])).Show();
   ```

   ![Soumettre Spark Job](./media/hdinsight-notebook-installation/run-udf.png)

## <a name="next-steps"></a>Étapes suivantes

* [Déployer une application .NET pour Apache Spark sur Azure HDInsight](../tutorials/hdinsight-deployment.md)
* [HDInsight Documentation](https://docs.microsoft.com/azure/hdinsight/)
