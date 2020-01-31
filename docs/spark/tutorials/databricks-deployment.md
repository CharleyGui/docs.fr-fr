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
# <a name="tutorial-deploy-a-net-for-apache-spark-application-to-databricks"></a>Didacticiel : déployer une application .NET pour Apache Spark sur Databricks

Ce didacticiel vous apprend à déployer votre application dans le Cloud par le biais de Azure Databricks, une plateforme d’analytique basée sur Apache Spark avec une configuration en un clic, des workflows rationalisés et un espace de travail interactif qui permet la collaboration.

Dans ce didacticiel, vous apprendrez à :

> [!div class="checklist"]
>
> - Créer un espace de travail Azure Databricks.
> - Publiez votre application .NET pour Apache Spark.
> - Créez un travail Spark et un cluster Spark.
> - Exécutez votre application sur le cluster Spark.

## <a name="prerequisites"></a>Prerequisites

Avant de commencer, effectuez les tâches suivantes :

* Si vous n’avez pas de compte Azure, créez un [compte gratuit](https://azure.microsoft.com/free/).
* Connectez-vous au [portail Azure](https://portal.azure.com/).
* Complétez le [.net pour Apache Spark-commencez dans](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) le didacticiel de 10 minutes.

## <a name="create-an-azure-databricks-workspace"></a>Créer un espace de travail Azure Databricks

> [!Note]
> Ce didacticiel ne peut pas être exécuté à l’aide **d’un abonnement d’essai gratuit Azure**.
> Si vous disposez d’un compte gratuit, accédez à votre profil et modifiez votre abonnement en **paiement à l’accès**. Pour plus d’informations, consultez [compte gratuit Azure](https://azure.microsoft.com/free/). Ensuite, [supprimez la limite de dépense](https://docs.microsoft.com/azure/billing/billing-spending-limit#why-you-might-want-to-remove-the-spending-limit)et [demandez une augmentation du quota](https://docs.microsoft.com/azure/azure-supportability/resource-manager-core-quotas-request) pour processeurs virtuels dans votre région. Lorsque vous créez votre espace de travail Azure Databricks, vous pouvez sélectionner le niveau tarifaire **d’essai (version d’évaluation gratuite de 14 jours)** pour permettre à l’espace de travail d’accéder à la version gratuite Premium Azure Databricks DBUs pendant 14 jours.

Dans cette section, vous allez créer un espace de travail Azure Databricks à l’aide de l’Portail Azure.

1. Dans le Portail Azure, sélectionnez **créer une ressource** > **analytique** > **Azure Databricks**.

   ![Créer une ressource Azure Databricks dans Portail Azure](./media/databricks-deployment/create-databricks-resource.png)

2. Sous **Azure Databricks service**, fournissez les valeurs pour créer un espace de travail Databricks.

    |Les  |Description  |
    |---------|---------|
    |**Nom de l’espace de travail**     | Donnez un nom à votre espace de travail Databricks.        |
    |**Abonnement**     | Dans la liste déroulante, sélectionnez votre abonnement Azure.        |
    |**Groupe de ressources**     | Spécifiez si vous souhaitez créer un nouveau groupe de ressources ou utiliser un groupe existant. Un groupe de ressources est un conteneur qui contient les ressources associées à une solution Azure. Pour plus d’informations, consultez [vue d’ensemble du groupe de ressources Azure](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-overview). |
    |**Emplacement**     | Sélectionnez la région de votre choix. Pour plus d’informations sur les régions disponibles, consultez [services Azure disponibles par région](https://azure.microsoft.com/regions/services/).        |
    |**Niveau tarifaire**     |  Choisissez entre **standard**, **Premium**ou **version d’évaluation**. Pour plus d’informations sur ces niveaux, consultez la [page de tarification Databricks](https://azure.microsoft.com/pricing/details/databricks/).       |
    |**Réseau virtuel**     |   Non       |

3. Sélectionnez **Créer**. La création de l’espace de travail prend quelques minutes. Pendant la création de l’espace de travail, vous pouvez afficher l’état du déploiement dans les **notifications**.

## <a name="install-azure-databricks-tools"></a>Installer Azure Databricks Tools

Vous pouvez utiliser l' **interface CLI Databricks** pour vous connecter à des clusters Azure Databricks et charger des fichiers à partir de votre ordinateur local. Les clusters Databricks accèdent aux fichiers via le système de fichiers DBFS (Databricks).

1. L’interface CLI Databricks nécessite python 3,6 ou version ultérieure. Si vous avez déjà installé python, vous pouvez ignorer cette étape.

   **Pour Windows :**

   [Télécharger python pour Windows](https://www.python.org/ftp/python/3.7.4/python-3.7.4.exe)

   **Pour Linux :** Python est préinstallé sur la plupart des distributions Linux. Exécutez la commande suivante pour déterminer la version que vous avez installée :

   ```bash
   python3 --version
   ```

2. Utilisez PIP pour installer l’interface de commande de Databricks. Python 3,4 et versions ultérieures incluent PIP par défaut. Utilisez PIP3 pour Python 3. Exécutez la commande suivante : .

   ```bash
   pip3 install databricks-cli
   ```

3. Une fois que vous avez installé l’interface de ligne de commande Databricks, ouvrez une nouvelle invite de commandes et exécutez la commande `databricks`. Si vous recevez un **« databricks » n’est pas reconnu comme une erreur de commande interne ou externe**, veillez à ouvrir une nouvelle invite de commandes.

## <a name="set-up-azure-databricks"></a>Configurer Azure Databricks

Maintenant que l’interface CLI Databricks est installée, vous devez configurer les détails de l’authentification.

1. Exécutez la commande CLI Databricks `databricks configure --token`.

2. Après avoir exécuté la commande configurer, vous êtes invité à entrer un ordinateur hôte. Votre URL d’hôte utilise le format : **https://< \Location >. azuredatabricks. net**. Par exemple, si vous avez sélectionné **eastus2** lors de la création du service Azure Databricks, l’hôte est **https://eastus2.azuredatabricks.net** .

3. Après avoir entré votre hôte, vous êtes invité à entrer un jeton. Dans le Portail Azure, sélectionnez **lancer l’espace de travail** pour lancer votre Azure Databricks espace de travail.

   ![Lancer Azure Databricks espace de travail](./media/databricks-deployment/launch-databricks-workspace.png)

4. Sur la page d’hébergement de votre espace de travail, sélectionnez **paramètres utilisateur**.

   ![Paramètres utilisateur dans Azure Databricks espace de travail](./media/databricks-deployment/databricks-user-settings.png)

5. Sur la page Paramètres utilisateur, vous pouvez générer un nouveau jeton. Copiez le jeton généré et collez-le à nouveau dans votre invite de commandes.

   ![Générer un nouveau jeton d’accès dans Azure Databricks espace de travail](./media/databricks-deployment/generate-token.png)

Vous devez maintenant être en mesure d’accéder à tous les clusters de Azure Databricks que vous créez et que vous chargez dans le fichier DBFS.

## <a name="download-worker-dependencies"></a>Télécharger les dépendances de Worker

1. Microsoft. Spark. Worker aide Apache Spark exécuter votre application, telle que les fonctions définies par l’utilisateur (UDF) que vous avez peut-être écrites. Téléchargez [Microsoft. Spark. Worker](https://github.com/dotnet/spark/releases/download/v0.6.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz).

2. Le *install-Worker.sh* est un script qui vous permet de copier .net pour Apache Spark fichiers dépendants dans les nœuds de votre cluster.

   Créez un nouveau fichier nommé **install-Worker.sh** sur votre ordinateur local, puis collez le [contenu install-Worker.sh](https://raw.githubusercontent.com/dotnet/spark/master/deployment/install-worker.sh) situé sur GitHub.

3. Le *DB-init.sh* est un script qui installe des dépendances sur votre cluster Databricks Spark.

   Créez un nouveau fichier nommé **DB-init.sh** sur votre ordinateur local, puis collez le [contenu DB-init.sh](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh) situé sur GitHub.

   Dans le fichier que vous venez de créer, affectez à la variable `DOTNET_SPARK_RELEASE` la valeur `https://github.com/dotnet/spark/releases/download/v0.6.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz`. Laissez le reste du fichier *DB-init.sh* tel quel.

> [!Note]
> Si vous utilisez Windows, vérifiez que les fins de ligne dans vos scripts *install-Worker.sh* et *DB-init.sh* sont de type UNIX (LF). Vous pouvez modifier les fins de ligne à l’aide d’éditeurs de texte tels que Notepad + + et Atom.

## <a name="publish-your-app"></a>Publier une application

Ensuite, vous publiez le *mySparkApp* créé dans [.net pour Apache Spark-bien démarrer dans](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) un didacticiel de 10 minutes pour vous assurer que votre cluster Spark a accès à tous les fichiers dont il a besoin pour exécuter votre application.

1. Exécutez les commandes suivantes pour publier le *mySparkApp*:

   **Sur Windows :**

   ```console
   cd mySparkApp
   dotnet publish -c Release -f netcoreapp3.0 -r ubuntu.16.04-x64
   ```

   **Sur Linux :**

   ```bash
   cd mySparkApp
   dotnet publish -c Release -f netcoreapp3.0 -r ubuntu.16.04-x64
   ```

2. Effectuez les tâches suivantes pour compresser les fichiers de votre application publiée afin de pouvoir les télécharger facilement vers votre cluster Databricks Spark.

   **Sur Windows :**

   Accédez à mySparkApp/bin/Release/netcoreapp 3.0/Ubuntu. 16.04-x64. Ensuite, cliquez avec le bouton droit sur le dossier de **publication** et sélectionnez **Envoyer vers > dossier compressé (zippé)** . Nommez le nouveau dossier **Publish. zip**.

   **Sur Linux, exécutez la commande suivante :**

   ```bash
   zip -r publish.zip .
   ```

## <a name="upload-files"></a>Charger des fichiers

Dans cette section, vous téléchargez plusieurs fichiers sur DBFS afin que votre cluster dispose de tout ce dont il a besoin pour exécuter votre application dans le Cloud. Chaque fois que vous chargez un fichier sur le DBFS, vérifiez que vous vous trouvez dans le répertoire où se trouve ce fichier sur votre ordinateur.

1. Exécutez les commandes suivantes pour télécharger *DB-init.sh*, *install-Worker.sh*et *Microsoft. Spark. Worker* vers dBFS :

   ```console
   databricks fs cp db-init.sh dbfs:/spark-dotnet/db-init.sh
   databricks fs cp install-worker.sh dbfs:/spark-dotnet/install-worker.sh
   databricks fs cp Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz dbfs:/spark-dotnet/   Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz
   ```

2. Exécutez les commandes suivantes pour télécharger les fichiers restants dont votre cluster a besoin pour exécuter votre application : le dossier de publication compressé, *Input. txt*et *Microsoft-Spark-2.4. x-0.3.0. jar*.

   ```console
   cd mySparkApp
   databricks fs cp input.txt dbfs:/input.txt

   cd mySparkApp\bin\Release\netcoreapp3.0\ubuntu.16.04-x64 directory
   databricks fs cp mySparkApp.zip dbfs:/spark-dotnet/publish.zip
   databricks fs cp microsoft-spark-2.4.x-0.6.0.jar dbfs:/spark-dotnet/microsoft-spark-2.4.x-0.6.0.jar
   ```

## <a name="create-a-job"></a>Créer un travail

Votre application s’exécute sur Azure Databricks par le biais d’un travail qui exécute **Spark-Submit**, qui est la commande que vous utilisez pour exécuter .net pour les tâches de Apache Spark.

1. Dans votre espace de travail Azure Databricks, sélectionnez l’icône **travaux** , puis **+ créer une tâche**.

   ![Créer un travail de Azure Databricks](./media/databricks-deployment/create-job.png)

2. Choisissez un titre pour votre travail, puis sélectionnez **configurer Spark-Submit**.

   ![Configurer Spark-submit pour la tâche Databricks](./media/databricks-deployment/configure-spark-submit.png)

3. Collez les paramètres suivants dans la configuration du travail. Ensuite, sélectionnez **confirmer**.

   ```
   ["--class","org.apache.spark.deploy.dotnet.DotnetRunner","/dbfs/spark-dotnet/microsoft-spark-2.4.x-0.6.0.jar","/dbfs/spark-dotnet/publish.zip","mySparkApp"]
   ```

## <a name="create-a-cluster"></a>Créer un cluster

1. Accédez à votre travail et sélectionnez **modifier** pour configurer le cluster de votre travail.

2. Définissez votre cluster sur **Spark 2.4.1**. Ensuite, sélectionnez **Options avancées** > les **scripts init**. Définissez le chemin d’accès du script init en tant que `dbfs:/spark-dotnet/db-init.sh`.

   ![Configurer le cluster Spark dans Azure Databricks](./media/databricks-deployment/cluster-config.png)

3. Sélectionnez **confirmer** pour confirmer vos paramètres de cluster.

## <a name="run-your-app"></a>Exécuter votre application

1. Accédez à votre travail et sélectionnez **Exécuter maintenant** pour exécuter votre travail sur le cluster Spark que vous venez de configurer.

2. La création du cluster du travail prend quelques minutes. Une fois créée, votre travail est envoyé et vous pouvez afficher la sortie.

3. Sélectionnez **clusters** dans le menu de gauche, puis le nom et l’exécution de votre travail.

4. Sélectionnez **journaux des pilotes** pour afficher la sortie de votre travail. À la fin de l’exécution de votre application, vous voyez le même tableau de nombre de mots de la série mise en route locale exécutée dans la console de sortie standard.

   ![Table de sortie de la tâche de Azure Databricks](./media/databricks-deployment/table-output.png)

   Félicitations, vous avez exécuté votre première application .NET pour Apache Spark dans le Cloud !

## <a name="clean-up-resources"></a>Nettoyer les ressources

Si vous n’avez plus besoin de l’espace de travail Databricks, vous pouvez supprimer votre ressource Azure Databricks dans le Portail Azure. Vous pouvez également sélectionner le nom du groupe de ressources pour ouvrir la page groupe de ressources, puis sélectionner **supprimer le groupe de ressources**.

## <a name="next-steps"></a>Étapes suivantes :

Dans ce tutoriel, vous avez déployé votre application .NET pour Apache Spark sur Databricks. Pour plus d’informations sur Databricks, consultez la documentation Azure Databricks.

> [!div class="nextstepaction"]
> [Documentation Azure Databricks](https://docs.microsoft.com/azure/azure-databricks/)
