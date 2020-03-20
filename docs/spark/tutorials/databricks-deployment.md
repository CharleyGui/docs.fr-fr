---
title: Déployer une application .NET pour Apache Spark sur Databricks
description: Découvrez comment déployer une application .NET pour Apache Spark sur Databricks.
ms.date: 01/23/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: c5308530831fa288bf637849c1342f51769c3ad4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "77503965"
---
# <a name="tutorial-deploy-a-net-for-apache-spark-application-to-databricks"></a>Tutorial: Déployer une application .NET pour Apache Spark à Databricks

Ce tutoriel vous apprend à déployer votre application dans le cloud via Azure Databricks, une plate-forme d’analyse basée sur Apache Spark avec configuration en un seul clic, flux de travail simplifiés et espace de travail interactif qui permet la collaboration.

Dans ce tutoriel, vous allez apprendre à :

> [!div class="checklist"]
>
> - Créer un espace de travail Azure Databricks.
> - Publiez votre application .NET pour Apache Spark.
> - Créez un emploi Spark et un cluster Spark.
> - Exécutez votre application sur le cluster Spark.

## <a name="prerequisites"></a>Conditions préalables requises

Avant de commencer, faites les tâches suivantes :

* Si vous n’avez pas de compte Azure, créez un [compte gratuit](https://azure.microsoft.com/free/).
* Connectez-vous au [portail Azure](https://portal.azure.com/).
* Complétez le [.NET pour Apache Spark - Get Started in 10-Minutes](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) tutorial.

## <a name="create-an-azure-databricks-workspace"></a>Créer un espace de travail Azure Databricks

> [!Note]
> Ce didacticiel ne peut pas être suivi avec un **abonnement d’essai gratuit Azure**.
> Si vous avez un compte gratuit, accédez à votre profil et modifiez votre abonnement sur **Paiement à l’utilisation**. Pour plus d’informations, consultez la page [Compte Azure gratuit](https://azure.microsoft.com/free/). Ensuite, [supprimez la limite de dépense](https://docs.microsoft.com/azure/billing/billing-spending-limit#why-you-might-want-to-remove-the-spending-limit), et [demandez une augmentation du quota](https://docs.microsoft.com/azure/azure-supportability/resource-manager-core-quotas-request) pour les processeurs virtuels dans votre région. Lorsque vous créez votre espace de travail Azure Databricks, vous pouvez sélectionner le tarif **Version d’évaluation (Premium - 14 jours de DBU offerts)** pour donner à l’accès de l’espace de travail un accès gratuit aux DBU d’Azure Databricks pendant 14 jours.

Dans cette section, vous créez un espace de travail Azure Databricks en utilisant le portail Azure.

1. Dans le portail Azure, sélectionnez **Créer une ressource** > **Analytics** > **Azure Databricks**.

   ![Créer une ressource Azure Databricks dans le portail Azure](./media/databricks-deployment/create-databricks-resource.png)

2. Sous **Service Azure Databricks**, renseignez les valeurs pour créer un espace de travail Databricks.

    |Propriété  |Description  |
    |---------|---------|
    |**Nom de l’espace de travail**     | Fournissez un nom pour votre espace de travail Databricks.        |
    |**Abonnement**     | Sélectionnez votre abonnement Azure dans la liste déroulante.        |
    |**Groupe de ressources**     | Indiquez si vous souhaitez créer un groupe de ressources Azure ou utiliser un groupe existant. Un groupe de ressources est un conteneur réunissant les ressources associées d’une solution Azure. Pour plus d’informations, consultez [Présentation des groupes de ressources Azure](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-overview). |
    |**Emplacement**     | Sélectionnez votre région préférée. Pour plus d’informations sur les régions disponibles, consultez [les services Azure disponibles par région](https://azure.microsoft.com/regions/services/).        |
    |**Niveau de tarification**     |  Choisissez **Standard**, **Premium** ou **Essai**. Pour plus d’informations sur ces niveaux, consultez la [page de tarification Databricks](https://azure.microsoft.com/pricing/details/databricks/).       |
    |**Réseau virtuel**     |   Non        |

3. Sélectionnez **Créer**. La création de l’espace de travail dure quelques minutes. Pendant la création de l'espace de travail, vous pouvez consulter l'état du déploiement dans **Notifications**.

## <a name="install-azure-databricks-tools"></a>Installer les outils Azure Databricks

Vous pouvez utiliser le **CLI Databricks** pour vous connecter aux clusters Azure Databricks et télécharger des fichiers à partir de votre machine locale. Databricks regroupe les fichiers d’accès via DBFS (Databricks File System).

1. Le Databricks CLI nécessite Python 3.6 ou plus. Si vous avez déjà Python installé, vous pouvez sauter cette étape.

   **Pour Windows:**

   [Télécharger Python pour Windows](https://www.python.org/ftp/python/3.7.4/python-3.7.4.exe)

   **Pour Linux :** Python est préinstallé sur la plupart des distributions Linux. Exécutez la commande suivante pour voir quelle version vous avez installée :

   ```bash
   python3 --version
   ```

2. Utilisez pip pour installer le Databricks CLI. Python 3.4 et plus tard inclure pip par défaut. Utilisez pip3 pour Python 3. Exécutez la commande suivante :

   ```bash
   pip3 install databricks-cli
   ```

3. Une fois que vous avez installé le Databricks CLI, `databricks`ouvrez une nouvelle invite de commande et exécutez la commande . Si vous recevez un **'databricks' n’est pas reconnu comme une erreur de commande interne ou externe,** assurez-vous d’ouvrir une nouvelle invite de commande.

## <a name="set-up-azure-databricks"></a>Configurez Azure Databricks

Maintenant que vous avez installé le Databricks CLI, vous devez configurer les détails d’authentification.

1. Exécuter la commande `databricks configure --token`Databricks CLI .

2. Après avoir exécuter la commande de configuration, vous êtes invité à entrer un hôte. Votre URL hôte utilise le format: **https://<-Location>.azuredatabricks.net**. Par exemple, si vous avez sélectionné **Eastus2** lors de la **https://eastus2.azuredatabricks.net**création du service Azure Databricks, l’hôte serait .

3. Après avoir entré votre hôte, vous êtes invité à entrer un jeton. Dans le portail Azure, sélectionnez **Launch Workspace** pour lancer votre espace de travail Azure Databricks.

   ![Lancement de l’espace de travail Azure Databricks](./media/databricks-deployment/launch-databricks-workspace.png)

4. Sur la page d’accueil de votre espace de travail, sélectionnez **Paramètres utilisateur**.

   ![Paramètres utilisateur dans l’espace de travail Azure Databricks](./media/databricks-deployment/databricks-user-settings.png)

5. Sur la page Paramètres utilisateur, vous pouvez générer un nouveau jeton. Copiez le jeton généré et collez-le de nouveau dans votre invite de commande.

   ![Générer un nouveau jeton d’accès dans l’espace de travail Azure Databricks](./media/databricks-deployment/generate-token.png)

Vous devriez désormais pouvoir accéder à tous les clusters Azure Databricks que vous créez et téléchargez des fichiers sur le DBFS.

## <a name="download-worker-dependencies"></a>Télécharger les dépendances des travailleurs

1. Microsoft.Spark.Worker aide Apache Spark à exécuter votre application, telles que toutes les fonctions définies par l’utilisateur (UDF) que vous avez peut-être écrites. Télécharger [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases/download/v0.6.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz).

2. Le *install-worker.sh* est un script qui vous permet de copier .NET pour les fichiers dépendants Apache Spark dans les nœuds de votre cluster.

   Créez un nouveau fichier nommé **install-worker.sh** sur votre ordinateur local et collez le [contenu install-worker.sh](https://raw.githubusercontent.com/dotnet/spark/master/deployment/install-worker.sh) situé sur GitHub.

3. Le *db-init.sh* est un script qui installe des dépendances sur votre cluster Databricks Spark.

   Créez un nouveau fichier nommé **db-init.sh** sur votre ordinateur local et collez le [contenu db-init.sh](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh) situé sur GitHub.

   Dans le fichier que vous `DOTNET_SPARK_RELEASE` venez `https://github.com/dotnet/spark/releases/download/v0.6.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz`de créer, définissez la variable à . Laissez le reste du *fichier db-init.sh* tel qu’il est.

> [!Note]
> Si vous utilisez Windows, vérifiez que les fins de ligne de vos scripts *install-worker.sh* et *db-init.sh* sont de style Unix (LF). Vous pouvez changer les terminaisons de ligne grâce à des éditeurs de texte comme NotepadMD et Atom.

## <a name="publish-your-app"></a>Publier votre application

Ensuite, vous publiez le *mySparkApp* créé dans le [.NET pour Apache Spark - Get Started in 10-Minutes](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) tutoriel pour s’assurer que votre cluster Spark a accès à tous les fichiers dont il a besoin pour exécuter votre application.

1. Exécutez les commandes suivantes pour publier le *mySparkApp*:

   ```dotnetcli
   cd mySparkApp
   dotnet publish -c Release -f netcoreapp3.0 -r ubuntu.16.04-x64
   ```

2. Faites les tâches suivantes pour zip vos fichiers d’application publiés afin que vous puissiez facilement les télécharger sur votre cluster Databricks Spark.

   **Sur Windows:**

   Naviguez vers mySparkApp/bin/Release/netcoreapp3.0/ubuntu.16.04-x64. Ensuite, cliquez à droite sur le dossier **Publier** et sélectionnez **Envoyer à > dossier compressé (zippé).** Nommez le nouveau dossier **publish.zip**.

   **Sur Linux, exécutez la commande ci-dessous :**

   ```bash
   zip -r publish.zip .
   ```

## <a name="upload-files"></a>Charger des fichiers

Dans cette section, vous téléchargez plusieurs fichiers sur DBFS afin que votre cluster dispose de tout ce dont il a besoin pour exécuter votre application dans le cloud. Chaque fois que vous téléchargez un fichier sur le DBFS, assurez-vous d’être dans l’annuaire où se trouve ce fichier sur votre ordinateur.

1. Exécutez les commandes suivantes pour télécharger le *db-init.sh*, *install-worker.sh*, et *Microsoft.Spark.Worker* à DBFS:

   ```console
   databricks fs cp db-init.sh dbfs:/spark-dotnet/db-init.sh
   databricks fs cp install-worker.sh dbfs:/spark-dotnet/install-worker.sh
   databricks fs cp Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz dbfs:/spark-dotnet/   Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz
   ```

2. Exécutez les commandes suivantes pour télécharger les fichiers restants de votre cluster devra exécuter votre application: le dossier de publication zippé, *input.txt*, et *microsoft-spark-2.4.x-0.3.0.jar*.

   ```console
   cd mySparkApp
   databricks fs cp input.txt dbfs:/input.txt

   cd mySparkApp\bin\Release\netcoreapp3.0\ubuntu.16.04-x64 directory
   databricks fs cp mySparkApp.zip dbfs:/spark-dotnet/publish.zip
   databricks fs cp microsoft-spark-2.4.x-0.6.0.jar dbfs:/spark-dotnet/microsoft-spark-2.4.x-0.6.0.jar
   ```

## <a name="create-a-job"></a>Créer un travail

Votre application fonctionne sur Azure Databricks à travers un travail qui fonctionne **spark-submit**, qui est la commande que vous utilisez pour exécuter .NET pour les emplois Apache Spark.

1. Dans votre espace de travail Azure Databricks, sélectionnez l’icône **Jobs,** puis **créez l’emploi**.

   ![Créer un emploi Azure Databricks](./media/databricks-deployment/create-job.png)

2. Choisissez un titre pour votre travail, puis **sélectionnez Configurer étincelle-soumettre**.

   ![Configurer l’étincelle-soumettre pour le travail Databricks](./media/databricks-deployment/configure-spark-submit.png)

3. Coller les paramètres suivants dans la configuration du travail. Ensuite, sélectionnez **Confirmer**.

   ```
   ["--class","org.apache.spark.deploy.dotnet.DotnetRunner","/dbfs/spark-dotnet/microsoft-spark-2.4.x-0.6.0.jar","/dbfs/spark-dotnet/publish.zip","mySparkApp"]
   ```

## <a name="create-a-cluster"></a>Créer un cluster

1. Naviguez dans votre travail et sélectionnez **Edit** pour configurer le cluster de votre travail.

2. Réglez votre cluster à **Spark 2.4.1**. Ensuite, sélectionnez **Advanced Options** > **Init Scripts**. Définir Init Script `dbfs:/spark-dotnet/db-init.sh`Path comme .

   ![Configurer le cluster d’étincelles dans Azure Databricks](./media/databricks-deployment/cluster-config.png)

3. Sélectionnez **Confirmez** pour confirmer les paramètres de votre cluster.

## <a name="run-your-app"></a>Exécutez l'application.

1. Naviguez dans votre travail et sélectionnez **Run Now** pour exécuter votre travail sur votre cluster Spark nouvellement configuré.

2. Il faut quelques minutes pour que le cluster du travail crée. Une fois qu’il est créé, votre travail sera soumis, et vous pouvez afficher la sortie.

3. Sélectionnez **des clusters** dans le menu gauche, puis le nom et l’exécution de votre travail.

4. Sélectionnez **les journaux de pilote** pour afficher la sortie de votre travail. Lorsque votre application termine l’exécution, vous voyez le même tableau de nombre de mots de la course locale de démarrage écrit à la console de sortie standard.

   ![Tableau de sortie d’emplois Azure Databricks](./media/databricks-deployment/table-output.png)

   Félicitations, vous avez exécuté votre premier .NET pour Apache Spark application dans le nuage!

## <a name="clean-up-resources"></a>Nettoyer les ressources

Si vous n’avez plus besoin de l’espace de travail Databricks, vous pouvez supprimer votre ressource Azure Databricks dans le portail Azure. Vous pouvez également sélectionner le nom du groupe de ressources pour ouvrir la page du groupe de ressources, puis sélectionner **Supprimer le groupe de ressources**.

## <a name="next-steps"></a>Étapes suivantes

Dans ce tutoriel, vous avez déployé votre application .NET pour Apache Spark sur Databricks. Pour plus d’informations sur Databricks, consultez la documentation Azure Databricks.

> [!div class="nextstepaction"]
> [Azure Databricks Documentation](https://docs.microsoft.com/azure/azure-databricks/)
