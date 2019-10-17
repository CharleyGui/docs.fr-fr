---
title: Déployer une application .NET pour Apache Spark sur Databricks
description: Découvrez comment déployer une application .NET pour Apache Spark sur Databricks.
ms.date: 05/17/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 570f6bdb8eda462b815dfc7c45f6e9a3a515f0ad
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395880"
---
# <a name="deploy-a-net-for-apache-spark-application-to-databricks"></a>Déployer une application .NET pour Apache Spark sur Databricks

Ce tutoriel explique comment déployer une application .NET pour Apache Spark sur Databricks.

Dans ce didacticiel, vous apprendrez à :

> [!div class="checklist"]
>
> - Préparer Microsoft.Spark.Worker
> - Publier votre application .NET Spark
> - Déployer votre application sur Databricks
> - Exécuter votre application

## <a name="prerequisites"></a>Configuration requise

Avant de commencer, procédez comme suit :

- Téléchargez l’[interface CLI de Databricks](https://docs.databricks.com/user-guide/dev-tools/databricks-cli.html).
- Téléchargez [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) sur votre machine locale. Il s’agit d’un script d’assistance que vous utilisez ultérieurement pour copier les fichiers dépendants de .NET pour Apache Spark dans les nœuds Worker de votre cluster Spark.

## <a name="prepare-worker-dependencies"></a>Préparer les dépendances Worker

**Microsoft.Spark.Worker** est un composant back-end qui se trouve sur les nœuds Worker individuels de votre cluster Spark. Quand vous voulez exécuter une fonction C# définie par l’utilisateur, Spark doit comprendre comment lancer le CLR .NET pour exécuter la fonction définie par l’utilisateur. **Microsoft.Spark.Worker** fournit à Spark une collection de classes qui activent cette fonctionnalité.

1. Sélectionnez une version netcoreapp Linux de [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases) à déployer sur votre cluster.

   Par exemple, si vous voulez `.NET for Apache Spark v0.1.0` avec `netcoreapp2.1`, vous devez télécharger [Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz](https://github.com/dotnet/spark/releases/download/v0.1.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz).

2. Chargez `Microsoft.Spark.Worker.<release>.tar.gz` et [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) dans un système de fichiers distribués (par exemple DBFS) auquel votre cluster a accès.

## <a name="prepare-your-net-for-apache-spark-app"></a>Préparer votre application .NET pour Apache Spark

1. Suivez le tutoriel [Prise en main](get-started.md) pour générer votre application.

2. Publiez votre application .NET Spark en tant qu’application autonome.

   Vous pouvez exécuter la commande suivante sur Linux.

   ```dotnetcli
   dotnet publish -c Release -f netcoreapp2.1 -r ubuntu.16.04-x64
   ```

3. Produisez `<your app>.zip` pour les fichiers publiés.

   Vous pouvez exécuter la commande suivante sur Linux en utilisant `zip`.

   ```bash
   zip -r <your app>.zip .
   ```

4. Chargez les éléments suivants sur un système de fichiers distribués (par exemple DBFS) auquel votre cluster a accès :

   - `microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar` : ce fichier jar est inclus dans le package NuGet [Microsoft. Spark](https://www.nuget.org/packages/Microsoft.Spark/) et colocalisé dans le répertoire de sortie de génération de votre application.
   - `<your app>.zip`
   - Les fichiers (comme les fichiers de dépendances ou les données communes accessibles à chaque worker) ou les assemblys (comme les DLL qui contiennent vos fonctions définies par l’utilisateur ou les bibliothèques dont dépend votre application) doivent être placés dans le répertoire de travail de chaque exécuteur.

## <a name="deploy-to-databricks"></a>Déployer sur Databricks

[Databricks](https://databricks.com) est une plateforme qui fournit un traitement Big Data dans le cloud avec Apache Spark.

> [!NOTE]
> [Azure Databricks](https://azure.microsoft.com/services/databricks/) et [AWS Databricks](https://databricks.com/aws) sont basés sur Linux. Par conséquent, si vous voulez déployer votre application sur Databricks, vérifiez que votre application est compatible avec .NET Standard et que vous utilisez le [compilateur .NET Core](https://dotnet.microsoft.com/download) pour compiler votre application.

Databricks vous permet de soumettre des applications .NET pour Apache Spark à un cluster actif existant ou de créer un cluster chaque fois que vous lancez un travail. Pour ce faire, vous devez installer **Microsoft.Spark.Worker** avant de soumettre une application .NET pour Apache Spark.

### <a name="deploy-microsoftsparkworker"></a>Déployer Microsoft.Spark.Worker

Cette étape n’est nécessaire qu’une seule fois pour un cluster.

1. Téléchargez [db-init.sh](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh) et [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh
) sur votre machine locale.

2. Modifiez **db-init.sh** pour qu’il pointe vers la version de **Microsoft.Spark.Worker** que vous voulez télécharger et installer sur votre cluster.

3. Installez l’[interface CLI de Databricks](https://docs.databricks.com/user-guide/dev-tools/databricks-cli.html).

4. [Configurez les détails d’authentification](https://docs.databricks.com/user-guide/dev-tools/databricks-cli.html#set-up-authentication) pour l’interface CLI de Databricks.

5. Chargez les fichiers sur votre cluster Databricks en utilisant la commande suivante :

   ```bash
   cd <path-to-db-init-and-install-worker>
   databricks fs cp db-init.sh dbfs:/spark-dotnet/db-init.sh
   databricks fs cp install-worker.sh dbfs:/spark-dotnet/install-worker.sh
   ```

6. Accédez à votre espace de travail Databricks. Sélectionnez **Clusters** dans le menu de gauche, puis **Créer un cluster**.

7. Après avoir configuré le cluster de façon appropriée, définissez le **script d’initialisation** et créez le cluster.

   ![Image d’action de script](./media/databricks-deployment/deployment-databricks-init-script.png)

## <a name="run-your-app"></a>Exécuter votre application

Vous pouvez utiliser `set JAR` ou `spark-submit` pour soumettre votre travail à Databricks.

### <a name="use-set-jar"></a>Utiliser Set JAR

[Set JAR](https://docs.databricks.com/user-guide/jobs.html#create-a-job) vous permet de soumettre un travail à un cluster actif existant.

#### <a name="one-time-setup"></a>Configuration unique

1. Accédez à votre cluster Databricks et sélectionnez **Travaux** dans le menu de gauche. Sélectionnez ensuite **Set JAR**.

2. Chargez le fichier `microsoft-spark-<spark-version>-<spark-dotnet-version>.jar` approprié.

3. Définissez les paramètres de façon appropriée.

   | Paramètre   | valeur                                                |
   |-------------|------------------------------------------------------|
   | Classe principale  | org. Apache. Spark. deploy. dotnet. DotnetRunner          |
   | Arguments   | /dBFS/Apps/\<your-App-name >. zip \<your-App-main-Class > |

4. Configurez le **cluster** pour qu’il pointe vers le cluster existant pour lequel vous avez créé le **script d’initialisation** dans la section précédente.

#### <a name="publish-and-run-your-app"></a>Publier et exécuter votre application

1. Utilisez l’[interface CLI de Databricks](https://docs.databricks.com/user-guide/dev-tools/databricks-cli.html) pour charger votre application sur votre cluster Databricks.

    ```bash
    cd <path-to-your-app-publish-directory>
    databricks fs cp <your-app-name>.zip dbfs:/apps/<your-app-name>.zip
    ```

2. Cette étape est nécessaire seulement si les assemblys de votre application (par exemple des DLL contenant des fonctions définies par l’utilisateur ainsi que leurs dépendances) doivent être placés dans le répertoire de travail de chaque **Microsoft.Spark.Worker**.

   - Charger les assemblys de votre application sur votre cluster Databricks

      ```bash
      cd <path-to-your-app-publish-directory>
      databricks fs cp <assembly>.dll dbfs:/apps/dependencies
      ```

   - Décommentez et modifiez la section des dépendances de l’application dans [db-init.sh](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh) pour la faire pointer vers le chemin des dépendances de votre application et la faire charger sur votre cluster Databricks.

      ```bash
      cd <path-to-db-init-and-install-worker>
      databricks fs cp db-init.sh dbfs:/spark-dotnet/db-init.sh
      ```

   - Redémarrez votre cluster.

3. Accédez à votre cluster Databricks dans votre espace de travail Databricks. Sous **Travaux**, sélectionnez votre travail, puis sélectionnez **Exécuter maintenant** pour exécuter votre travail.

### <a name="use-spark-submit"></a>Utiliser spark-submit

La commande [spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html) vous permet de soumettre un travail à un nouveau cluster.

1. [Créez un travail](https://docs.databricks.com/user-guide/jobs.html) et sélectionnez **Configurer spark-submit**.

2. Configurez `spark-submit` avec les paramètres suivants :

    ```bash
    ["--files","/dbfs/<path-to>/<app assembly/file to deploy to worker>","--class","org.apache.spark.deploy.dotnet.DotnetRunner","/dbfs/<path-to>/microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar","/dbfs/<path-to>/<app name>.zip","<app bin name>","app arg1","app arg2"]
    ```

3. Accédez à votre cluster Databricks dans votre espace de travail Databricks. Sous **Travaux**, sélectionnez votre travail, puis sélectionnez **Exécuter maintenant** pour exécuter votre travail.

## <a name="next-steps"></a>Étapes suivantes

Dans ce tutoriel, vous avez déployé votre application .NET pour Apache Spark sur Databricks. Pour plus d’informations sur Databricks, consultez la documentation Azure Databricks.

> [!div class="nextstepaction"]
> [Documentation Azure Databricks](https://docs.microsoft.com/azure/azure-databricks/)
