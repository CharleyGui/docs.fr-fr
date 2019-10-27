---
title: Déployer une application .NET pour Apache Spark sur Azure HDInsight
description: Découvrez comment déployer une application .NET pour Apache Spark sur HDInsight.
ms.date: 05/17/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 2cb91032e0ce1d320b266772e8f9f1431df4a298
ms.sourcegitcommit: 9b2ef64c4fc10a4a10f28a223d60d17d7d249ee8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/26/2019
ms.locfileid: "72960996"
---
# <a name="tutorial-deploy-a-net-for-apache-spark-application-to-azure-hdinsight"></a>Didacticiel : déployer une application .NET pour Apache Spark sur Azure HDInsight

Ce didacticiel vous apprend à déployer votre .NET pour Apache Spark application dans le Cloud par le biais d’un cluster Azure HDInsight. HDInsight facilite la création et la configuration d’un cluster Spark dans Azure, car les clusters Spark dans HDInsight sont compatibles avec le stockage Azure et les Azure Data Lake Storage. 

Dans ce didacticiel, vous apprendrez à :

> [!div class="checklist"]
>
> * Accédez à vos comptes de stockage à l’aide de Explorateur Stockage Azure.
> * Créez un cluster Azure HDInsight.
> * Publiez votre application .NET pour Apache Spark.
> * Créez et exécutez une action de script HDInsight.
> * Exécutez un .NET pour Apache Spark application sur un cluster HDInsight.

## <a name="prerequisites"></a>Configuration requise

Avant de commencer, effectuez les tâches suivantes :

* Si vous n’avez pas d’abonnement Azure, créez un [compte gratuit](https://azure.microsoft.com/free/).
* Connectez-vous au [portail Azure](https://portal.azure.com/).
* Installez Explorateur Stockage Azure sur votre ordinateur [Windows](https://go.microsoft.com/fwlink/?LinkId=708343&clcid=0x409), [Linux](https://go.microsoft.com/fwlink/?LinkId=722418&clcid=0x409)ou [MacOS](https://go.microsoft.com/fwlink/?LinkId=708342&clcid=0x409) .
* Complétez le [.net pour Apache Spark-commencez dans](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) le didacticiel de 10 minutes.

## <a name="access-your-storage-accounts"></a>Accéder à vos comptes de stockage

1. Ouvrez Explorateur Stockage Azure.

2. Sélectionnez **Ajouter un compte** dans le menu de gauche, puis connectez-vous à votre compte Azure.

    ![Connectez-vous au compte Azure à partir de Explorateur Stockage](./media/hdinsight-deployment/signin-azure-storage-explorer.png)

   Une fois que vous êtes connecté, vous devez voir tous les comptes de stockage dont vous disposez et toutes les ressources que vous avez téléchargées sur vos comptes de stockage.

## <a name="create-an-hdinsight-cluster"></a>Créer un cluster HDInsight

> [!IMPORTANT]  
> La facturation des clusters HDInsight est calculée au prorata par minute, même si vous ne les utilisez pas. Veillez à supprimer votre cluster une fois que vous avez fini de l’utiliser. Pour plus d’informations, consultez la section [nettoyage des ressources](#clean-up-resources) de ce didacticiel.

1. Visitez le [portail Azure](https://portal.azure.com).

2. Sélectionnez **+ créer une ressource**. Ensuite, sélectionnez **HDInsight** dans la catégorie **Analytics** .

    ![Créer une ressource HDInsight à partir d’Portail Azure](./media/hdinsight-deployment/create-hdinsight-resource.png)

3. Sous **principes de base**, indiquez les valeurs suivantes :

    |Property  |Description  |
    |---------|---------|
    |Abonnement  | Dans la liste déroulante, choisissez l’un de vos abonnements Azure actifs. |
    |Groupe de ressources | Spécifiez si vous souhaitez créer un nouveau groupe de ressources ou utiliser un groupe existant. Un groupe de ressources est un conteneur qui contient les ressources associées à une solution Azure. |
    |Nom du cluster | Donnez un nom à votre cluster HDInsight Spark.|
    |Emplacement   | Sélectionnez un emplacement pour le groupe de ressources. Le modèle utilise cet emplacement pour créer le cluster et pour le stockage de cluster par défaut. |
    |Type de cluster| Sélectionnez **Spark** comme type de cluster.|
    |Version du cluster|Ce champ est rempli avec la version par défaut une fois que le type de cluster a été sélectionné. Sélectionnez une version 2,3 ou 2,4 de Spark.|
    |Nom d’utilisateur de connexion du cluster| Entrez le nom d’utilisateur de connexion du cluster.  Le nom par défaut est *admin*. |
    |Mot de passe de connexion du cluster| Entrez un mot de passe de connexion. |
    |Nom d’utilisateur Secure Shell (SSH)| Entrez le nom d’utilisateur SSH. Par défaut, ce compte partage le même mot de passe que le compte de *nom d’utilisateur de connexion au cluster* . |

4. Sélectionnez **suivant : stockage > >** pour accéder à la page de **stockage** . Sous **stockage**, indiquez les valeurs suivantes :

    |Property  |Description  |
    |---------|---------|
    |Type de stockage principal|Utilisez la valeur par défaut **stockage Azure**.|
    |Méthode de sélection|Utilisez la valeur par défaut **Sélectionner dans la liste**.|
    |Compte de stockage principal|Choisissez votre abonnement et l’un de vos comptes de stockage actifs au sein de cet abonnement.|
    |Conteneur|Ce conteneur est le conteneur d’objets BLOB spécifique dans votre compte de stockage où votre cluster recherche des fichiers pour exécuter votre application dans le Cloud. Vous pouvez lui attribuer un nom disponible.|

5. Sous **examiner + créer**, sélectionnez **créer**. La création du cluster prend environ 20 minutes. Le cluster doit être créé avant que vous puissiez passer à l’étape suivante.

## <a name="publish-your-app"></a>Publier une application

Ensuite, vous publiez le *mySparkApp* créé dans [.net pour Apache Spark-bien démarrer dans un didacticiel de 10 minutes](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) , qui donne à votre cluster Spark un accès à tous les fichiers dont il a besoin pour exécuter votre application. 

1. Exécutez les commandes suivantes pour publier le *mySparkApp*:

   **Sur Windows :**

   ```console
   cd mySparkApp
   dotnet publish -c Release -f netcoreapp3.0 -r ubuntu.16.04-x6
   ```

   **Sur Linux :**

   ```bash
   cd mySparkApp
   foo@bar:~/path/to/app$ dotnet publish -c Release -f netcoreapp3.0 -r ubuntu.16.04-x64
   ```

2. Effectuez les tâches suivantes pour compresser les fichiers de votre application publiée afin de pouvoir les télécharger facilement vers votre cluster HDInsight.

   **Sur Windows :**

   Accédez à *mySparkApp/bin/Release/netcoreapp 3.0/Ubuntu. 16.04-x64*. Ensuite, cliquez avec le bouton droit sur le dossier de **publication** et sélectionnez **Envoyer vers > dossier compressé (zippé)** . Nommez le nouveau dossier **Publish. zip**.

   **Sur Linux, exécutez la commande suivante :**

   ```bash
   zip -r publish.zip
   ```

## <a name="upload-files-to-azure"></a>Charger des fichiers dans Azure

Ensuite, vous utilisez la Explorateur Stockage Azure pour télécharger les cinq fichiers suivants dans le conteneur d’objets BLOB que vous avez choisi pour le stockage de votre cluster : 

* Microsoft. Spark. Worker
* install-worker.sh
* publier le fichier. zip
* Microsoft-Spark-2.3. x-0.3.0. jar
* Input. txt.

1. Ouvrez Explorateur Stockage Azure et accédez à votre compte de stockage dans le menu de gauche. Explorez le conteneur d’objets BLOB de votre cluster sous **conteneurs d’objets BLOB** dans votre compte de stockage.

2. *Microsoft. Spark. Worker* aide Apache Spark exécuter votre application, telle que les fonctions définies par l’utilisateur (UDF) que vous avez peut-être écrites. Téléchargez [Microsoft. Spark. Worker](https://github.com/dotnet/spark/releases/download/v0.3.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.3.0.tar.gz). Ensuite, sélectionnez **Télécharger** dans Explorateur stockage Azure pour charger le processus de travail.

   ![Télécharger des fichiers vers Explorateur Stockage Azure](./media/hdinsight-deployment/upload-files-to-storage.png)

3. Le *install-Worker.sh* est un script qui vous permet de copier .net pour Apache Spark fichiers dépendants dans les nœuds de votre cluster. 

   Créez un nouveau fichier nommé **install-Worker.sh** votre ordinateur local, puis collez le [contenu install-Worker.sh](https://raw.githubusercontent.com/dotnet/spark/master/deployment/install-worker.sh) situé sur GitHub. Ensuite, chargez *install-Worker.sh* dans votre conteneur d’objets BLOB.

4. Votre cluster a besoin du fichier publish. zip qui contient les fichiers publiés de votre application. Accédez à votre dossier publié, **mySparkApp/bin/Release/netcoreapp 3.0/Ubuntu. 16.04-x64**, puis recherchez **Publish. zip**. Ensuite, téléchargez le fichier *Publish. zip* dans votre conteneur d’objets BLOB.

5. Votre cluster a besoin du code d’application qui a été empaqueté dans un fichier jar. Accédez à votre dossier publié, **mySparkApp/bin/Release/netcoreapp 3.0/Ubuntu. 16.04-x64**, puis localisez **Microsoft-Spark-2.3. x-0.3.0. jar**. Ensuite, chargez le fichier jar dans votre conteneur d’objets BLOB.

   Il peut y avoir plusieurs fichiers. jar (pour les versions 2.3. x et 2.4. x de Spark). Vous devez choisir le fichier. jar qui correspond à la version de Spark que vous avez choisie lors de la création du cluster. Par exemple, choisissez *Microsoft-Spark-2.3. x-0.3.0. jar* si vous avez choisi Spark 2.3.2 lors de la création du cluster.

6. Votre cluster a besoin de l’entrée de votre application. Accédez à votre répertoire **mySparkApp** et recherchez **Input. txt**. Chargez votre fichier d’entrée dans le répertoire **User/sshuser** dans votre conteneur d’objets BLOB. Vous allez vous connecter à votre cluster via SSH, et ce dossier est l’emplacement où votre cluster recherche son entrée. Le fichier *Input. txt* est le seul fichier chargé dans un répertoire spécifique.

## <a name="run-the-hdinsight-script-action"></a>Exécuter l’action de script HDInsight

Une fois que votre cluster est en cours d’exécution et que vous avez téléchargé vos fichiers dans Azure, vous exécutez le script **install-Worker.sh** sur le cluster. 

1. Accédez à votre cluster HDInsight Spark dans Portail Azure, puis sélectionnez **actions de script**.

2. Sélectionnez **+ soumettre nouveau** et fournissez les valeurs suivantes :

   |Property  |Description  |
   |---------|---------|
   | Type de script |Personnalisé|
   | Name | Installer Worker|
   | URI de script bash |https://mystorageaccount.blob.core.windows.net/mycontainer/install-worker.sh </br> Pour confirmer cet URI, cliquez avec le bouton droit sur install-worker.sh dans Explorateur Stockage Azure, puis sélectionnez Propriétés. |
   | Type (s) de nœud| Collabor|
   | Paramètres | bleu </br> wasbs://mycontainer@myStorageAccount.blob.core.windows.net/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz </br> /usr/local/bin 

3. Sélectionnez **créer** pour soumettre votre script.

## <a name="run-your-app"></a>Exécuter votre application

1. Accédez à votre cluster HDInsight Spark dans Portail Azure, puis sélectionnez **SSH + connexion au cluster**.

2. Copiez les informations de connexion SSH et collez la connexion dans un terminal. Connectez-vous à votre cluster à l’aide du mot de passe que vous avez défini lors de la création du cluster. Vous devriez voir des messages vous préversant Ubuntu et Spark.

3. Utilisez la commande **Spark-Submit** pour exécuter votre application sur votre cluster HDInsight. N’oubliez pas de remplacer **mycontainer** et **mystorageaccount** dans l’exemple de script par les noms réels de votre conteneur d’objets BLOB et de votre compte de stockage.

   ```bash
   $SPARK_HOME/bin/spark-submit \
   --master yarn \
   --class org.apache.spark.deploy.DotnetRunner \
   wasbs://mycontainer@mystorageaccount.blob.core.windows.net/microsoft-spark-2.3.x-0.6.0.jar \
   wasbs://mycontainer@mystorageaccount.blob.core.windows.net/publish.zip mySparkApp
   ```

   Lorsque votre application s’exécute, vous voyez le même tableau de nombre de mots que l’exécution locale de prise en main écrite dans la console. Félicitations, vous avez exécuté votre première application .NET pour Apache Spark dans le Cloud !

## <a name="clean-up-resources"></a>Nettoyer les ressources

HDInsight enregistre vos données dans le stockage Azure, ce qui vous permet de supprimer en toute sécurité un cluster lorsqu’il n’est pas utilisé. Vous êtes également facturé pour un cluster HDInsight, même s’il n’est pas en cours d’utilisation. Étant donné que les frais pour le cluster sont beaucoup plus longs que les frais de stockage, il est utile de supprimer les clusters lorsqu’ils ne sont pas utilisés.

Vous pouvez également sélectionner le nom du groupe de ressources pour ouvrir la page groupe de ressources, puis sélectionner **supprimer le groupe de ressources**. En supprimant le groupe de ressources, vous supprimez le cluster HDInsight Spark et le compte de stockage par défaut.

## <a name="next-steps"></a>Étapes suivantes

Dans ce tutoriel, vous avez déployé votre application .NET pour Apache Spark sur Azure HDInsight. Pour plus d’informations sur HDInsight, consultez la documentation d’Azure HDInsight.

> [!div class="nextstepaction"]
> [Documentation Azure HDInsight](https://docs.microsoft.com/azure/hdinsight/)
