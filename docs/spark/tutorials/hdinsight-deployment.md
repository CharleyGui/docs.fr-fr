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
# <a name="tutorial-deploy-a-net-for-apache-spark-application-to-azure-hdinsight"></a>Tutorial: Déployer une application .NET pour Apache Spark à Azure HDInsight

Ce tutoriel vous apprend à déployer votre application .NET pour Apache Spark dans le cloud via un cluster Azure HDInsight. HDInsight facilite la création et la configuration d’un cluster Spark à Azure puisque les clusters Spark dans HDInsight sont compatibles avec Azure Storage et Azure Data Lake Storage.

Dans ce tutoriel, vous allez apprendre à :

> [!div class="checklist"]
>
> * Accédez à vos comptes de stockage en utilisant Azure Storage Explorer.
> * Créez un cluster Azure HDInsight.
> * Publiez votre application .NET pour Apache Spark.
> * Créez et exécutez une action de script HDInsight.
> * Exécutez une application .NET pour Apache Spark sur un cluster HDInsight.

## <a name="prerequisites"></a>Conditions préalables requises

Avant de commencer, faites les tâches suivantes :

* Si vous n’avez pas d’abonnement Azure, créez un [compte gratuit](https://azure.microsoft.com/free/).
* Connectez-vous au [portail Azure](https://portal.azure.com/).
* Installez Azure Storage Explorer sur votre [ordinateur Windows,](https://go.microsoft.com/fwlink/?LinkId=708343&clcid=0x409) [Linux](https://go.microsoft.com/fwlink/?LinkId=722418&clcid=0x409)ou [MacOS.](https://go.microsoft.com/fwlink/?LinkId=708342&clcid=0x409)
* Complétez le [.NET pour Apache Spark - Get Started in 10-Minutes](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) tutorial.

## <a name="access-your-storage-accounts"></a>Accédez à vos comptes de stockage

1. Ouvrez l’Explorateur de stockage Azure.

2. Sélectionnez **Ajouter le compte** sur le menu gauche et connectez-vous à votre compte Azure.

    ![Connectez-vous au compte Azure de Storage Explorer](./media/hdinsight-deployment/signin-azure-storage-explorer.png)

   Après votre connexion, vous devriez voir tous les comptes de stockage que vous avez et toutes les ressources que vous avez téléchargées sur vos comptes de stockage.

## <a name="create-an-hdinsight-cluster"></a>Création d'un cluster HDInsight

> [!IMPORTANT]
> La facturation des clusters HDInsight est prorated par minute, même si vous ne les utilisez pas. Veillez à supprimer votre cluster une fois que vous avez fini de l’utiliser. Pour plus d’informations, consultez la section [Ressources Nettoyage](#clean-up-resources) de ce tutoriel.

1. Visitez le [portail Azure](https://portal.azure.com).

2. Sélectionnez **et créez une ressource**. Ensuite, sélectionnez **HDInsight** de la catégorie **Analytics.**

    ![Créer la ressource HDInsight à partir du portail Azure](./media/hdinsight-deployment/create-hdinsight-resource.png)

3. Sous **Informations de base**, fournissez les valeurs suivantes :

    |Propriété  |Description  |
    |---------|---------|
    |Abonnement  | Dès le décrochage, choisissez l’un de vos abonnements Azure actifs. |
    |Resource group | Indiquez si vous souhaitez créer un groupe de ressources Azure ou utiliser un groupe existant. Un groupe de ressources est un conteneur réunissant les ressources associées d’une solution Azure. |
    |Nom du cluster | Attribuez un nom à votre cluster HDInsight Spark.|
    |Emplacement   | Sélectionnez l’emplacement du groupe de ressources. Le modèle utilise cet emplacement pour créer le cluster, ainsi que pour stocker le cluster par défaut. |
    |Type de cluster| Sélectionnez **Spark** comme type de cluster.|
    |Version du cluster|Ce champ s’autopeuplera avec la version par défaut une fois que le type de cluster a été sélectionné. Sélectionnez une version 2.3 ou 2.4 de Spark.|
    |Nom d’utilisateur de connexion au cluster| Entrez le nom d’utilisateur de connexion au cluster.  Le nom par défaut est *admin*. |
    |Mot de passe de connexion au cluster| Entrez n’importe quel mot de passe de connexion. |
    |Nom d’utilisateur SSH (Secure Shell)| Entrez le nom d’utilisateur SSH. Par défaut, ce compte a le même mot de passe que le compte *Nom d’utilisateur de connexion au cluster*. |

4. Sélectionnez **Suivant : Stockagez >>** pour continuer à la page de **stockage.** Sous **Stockage**, fournissez les valeurs suivantes :

    |Propriété  |Description  |
    |---------|---------|
    |Type de stockage principal|Utilisez la valeur par défaut : **Stockage Azure**.|
    |Méthode de sélection|Utilisez la valeur par défaut : **Sélectionner dans la liste**.|
    |Compte de stockage principal|Choisissez votre abonnement et l’un de vos comptes de stockage actifs au sein de cet abonnement.|
    |Conteneur|Ce conteneur est le conteneur blob spécifique dans votre compte de stockage où votre cluster recherche des fichiers pour exécuter votre application dans le cloud. Vous pouvez lui donner n’importe quel nom disponible.|

5. Sous **Vérifier + créer**, sélectionnez **Créer**. La création du cluster prend environ 20 minutes. Le cluster doit être créé avant de pouvoir passer à l’étape suivante.

## <a name="publish-your-app"></a>Publier votre application

Ensuite, vous publiez le *mySparkApp* créé dans le [.NET pour Apache Spark - Get Started in 10-Minutes](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) tutoriel, qui donne à votre cluster Spark accès à tous les fichiers dont il a besoin pour exécuter votre application.

1. Exécutez les commandes suivantes pour publier le *mySparkApp*:

   **Sur Windows:**

   ```dotnetcli
   cd mySparkApp
   dotnet publish -c Release -f netcoreapp3.0 -r ubuntu.16.04-x64
   ```

   **Sur Linux:**

   ```bash
   cd mySparkApp
   foo@bar:~/path/to/app$ dotnet publish -c Release -f netcoreapp3.0 -r ubuntu.16.04-x64
   ```

2. Faites les tâches suivantes pour zip vos fichiers d’application publiés afin que vous puissiez facilement les télécharger sur votre cluster HDInsight.

   **Sur Windows:**

   Naviguez vers *mySparkApp/bin/Release/netcoreapp3.0/ubuntu.16.04-x64*. Ensuite, cliquez à droite sur le dossier **Publier** et sélectionnez **Envoyer à > dossier compressé (zippé).** Nommez le nouveau dossier **publish.zip**.

   **Sur Linux, exécutez la commande ci-dessous :**

   ```bash
   zip -r publish.zip
   ```

## <a name="upload-files-to-azure"></a>Télécharger des fichiers sur Azure

Ensuite, vous utilisez l’Azure Storage Explorer pour télécharger les cinq fichiers suivants dans le conteneur blob que vous avez choisi pour le stockage de votre cluster :

* Microsoft.Spark.Travailleur
* install-worker.sh
* publish.zip
* microsoft-spark-2.3.x-0.3.0.jar
* input.txt.

1. Ouvrez Azure Storage Explorer et naviguez vers votre compte de stockage à partir du menu gauche. Forez-le vers le bas pour le conteneur blob pour votre cluster sous **des conteneurs Blob** dans votre compte de stockage.

2. *Microsoft.Spark.Worker* aide Apache Spark à exécuter votre application, telles que toutes les fonctions définies par l’utilisateur (UDF) que vous avez peut-être écrites. Télécharger [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases/download/v0.3.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.3.0.tar.gz). Ensuite, sélectionnez **Upload** dans Azure Storage Explorer pour télécharger le travailleur.

   ![Téléchargez des fichiers sur Azure Storage Explorer](./media/hdinsight-deployment/upload-files-to-storage.png)

3. Le *install-worker.sh* est un script qui vous permet de copier .NET pour les fichiers dépendants Apache Spark dans les nœuds de votre cluster.

   Créez un nouveau fichier nommé **install-worker.sh** votre ordinateur local et collez le [contenu install-worker.sh](https://raw.githubusercontent.com/dotnet/spark/master/deployment/install-worker.sh) situé sur GitHub. Ensuite, téléchargez *install-worker.sh* dans votre conteneur blob.

4. Votre cluster a besoin du fichier publish.zip qui contient les fichiers publiés par votre application. Naviguez vers votre dossier publié, **mySparkApp/bin/Release/netcoreapp3.0/ubuntu.16.04-x64**, et **localisez publish.zip**. Ensuite, téléchargez *publish.zip* sur votre conteneur blob.

5. Votre cluster a besoin du code d’application qui a été emballé dans un fichier de pot. Naviguez vers votre dossier publié, **mySparkApp/bin/Release/netcoreapp3.0/ubuntu.16.04-x64**, et localisez **microsoft-spark-2.3.x-0.3.0.jar**. Ensuite, téléchargez le fichier de pot sur votre conteneur blob.

   Il peut y avoir plusieurs fichiers .jar (pour les versions 2.3.x et 2.4.x de Spark). Vous devez choisir le fichier .jar qui correspond à la version de Spark que vous avez choisie lors de la création de cluster. Par exemple, choisissez *microsoft-spark-2.3.x-0.3.0.jar* si vous avez choisi Spark 2.3.2 lors de la création de cluster.

6. Votre cluster a besoin de l’entrée de votre application. Naviguez vers votre répertoire **mySparkApp** et **localisez input.txt**. Téléchargez votre fichier d’entrée dans **l’annuaire utilisateur/sshuser** dans votre conteneur blob. Vous vous connecterez à votre cluster par ssh, et ce dossier est l’endroit où votre cluster cherche son entrée. Le fichier *input.txt* est le seul fichier téléchargé sur un répertoire spécifique.

## <a name="run-the-hdinsight-script-action"></a>Exécuter l’action de script HDInsight

Une fois que votre cluster est en cours d’exécution et que vous avez téléchargé vos fichiers sur Azure, vous exécutez le **script install-worker.sh** sur le cluster.

1. Naviguez vers votre cluster HDInsight Spark dans le portail Azure, puis sélectionnez **les actions Script**.

2. Sélectionnez **et soumettez de nouvelles** valeurs et fournissez les valeurs suivantes :

   |Propriété  |Description  |
   |---------|---------|
   | Type de script |Custom|
   | Nom | Installer Le travailleur|
   | URI de script bash |https://mystorageaccount.blob.core.windows.net/mycontainer/install-worker.sh </br> Pour confirmer cette URI, cliquez à droite sur install-worker.sh dans Azure Storage Explorer et sélectionnez Propriétés. |
   | Type(s) de nœud| Worker|
   | Paramètres | azure </br> wasbs://mycontainer@myStorageAccount.blob.core.windows.net/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz </br> /usr/local/bin

3. Sélectionnez **Créer** pour soumettre votre script.

## <a name="run-your-app"></a>Exécutez l'application.

1. Naviguez vers votre cluster HDInsight Spark dans le portail Azure, puis sélectionnez **la connexion SSH et Cluster**.

2. Copiez les informations de connexion ssh et collez la connexion dans un terminal. Connectez-vous à votre cluster à l’aide du mot de passe que vous avez défini lors de la création du cluster. Vous devriez voir des messages vous accueillant à Ubuntu et Spark.

3. Utilisez la commande **spark-submit** pour exécuter votre application sur votre cluster HDInsight. N’oubliez pas de remplacer **mycontainer** et **mystorageaccount** dans le script de l’exemple avec les noms réels de votre conteneur blob et compte de stockage.

   ```bash
   $SPARK_HOME/bin/spark-submit \
   --master yarn \
   --class org.apache.spark.deploy.dotnet.DotnetRunner \
   wasbs://mycontainer@mystorageaccount.blob.core.windows.net/microsoft-spark-2.3.x-0.6.0.jar \
   wasbs://mycontainer@mystorageaccount.blob.core.windows.net/publish.zip mySparkApp
   ```

   Lorsque votre application s’exécute, vous voyez le même tableau de nombre de mots de la course locale de démarrage écrit à la console. Félicitations, vous avez exécuté votre premier .NET pour Apache Spark application dans le nuage!

## <a name="clean-up-resources"></a>Nettoyer les ressources

HDInsight enregistre vos données dans Azure Storage, de sorte que vous pouvez supprimer en toute sécurité un cluster lorsqu’il n’est pas utilisé. Vous devez également payer pour un cluster HDInsight, même lorsque vous ne l’utilisez pas. Étant donné que les frais pour le cluster sont bien plus élevés que les frais de stockage, économique, mieux vaut supprimer les clusters lorsqu’ils ne sont pas utilisés.

Vous pouvez également sélectionner le nom du groupe de ressources pour ouvrir la page du groupe de ressources, puis sélectionner **Supprimer le groupe de ressources**. En supprimant le groupe de ressources, vous supprimez le cluster HDInsight Spark et le compte de stockage par défaut.

## <a name="next-steps"></a>Étapes suivantes

Dans ce tutoriel, vous avez déployé votre application .NET pour Apache Spark sur Azure HDInsight. Pour plus d’informations sur HDInsight, consultez la documentation d’Azure HDInsight.

> [!div class="nextstepaction"]
> [Azure HDInsight Documentation](https://docs.microsoft.com/azure/hdinsight/)
