---
title: Déployer une application .NET pour Apache Spark sur Databricks
description: Découvrez comment déployer un .NET pour Apache Spark application sur Databricks.
ms.date: 05/17/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: ca9e93a413622c84325ca9fc8bac17268b990c5a
ms.sourcegitcommit: 127343afce8422bfa944c8b0c4ecc8f79f653255
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2019
ms.locfileid: "69576966"
---
# <a name="deploy-a-net-for-apache-spark-application-to-databricks"></a>Déployer une application .NET pour Apache Spark sur Databricks

Ce didacticiel explique comment déployer un .NET pour Apache Spark application sur Databricks.

Ce tutoriel vous montre comment effectuer les opérations suivantes :

> [!div class="checklist"]
> * Préparer Microsoft. Spark. Worker
> * Publier votre application Spark .NET
> * Déployer votre application sur Databricks
> * Exécuter votre application

## <a name="prerequisites"></a>Prérequis

Avant de commencer, procédez comme suit:

* Téléchargez l' [interface CLI Databricks](https://docs.databricks.com/user-guide/dev-tools/databricks-cli.html).
* Téléchargez [install-Worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) sur votre ordinateur local. Il s’agit d’un script d’assistance que vous utilisez ultérieurement pour copier .NET pour Apache Spark fichiers dépendants dans les nœuds Worker du cluster Spark.

## <a name="prepare-worker-dependencies"></a>Préparer les dépendances de Worker

**Microsoft. Spark. Worker** est un composant principal qui réside sur les nœuds Worker individuels de votre cluster Spark. Lorsque vous souhaitez exécuter une C# fonction définie par l’utilisateur (UDF), Spark doit comprendre comment lancer le CLR .net pour exécuter l’UDF. **Microsoft. Spark. Worker** fournit une collection de classes à Spark qui activent cette fonctionnalité.

1. Sélectionnez une version de netcoreapp de [Microsoft. Spark. Worker](https://github.com/dotnet/spark/releases) Linux à déployer sur votre cluster.

   Par exemple, si vous souhaitez `.NET for Apache Spark v0.1.0` utiliser `netcoreapp2.1`, vous devez télécharger [Microsoft. Spark. Worker. netcoreapp 2.1. Linux-x64-0.1.0. tar. gz](https://github.com/dotnet/spark/releases/download/v0.1.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz).

2. Téléchargez `Microsoft.Spark.Worker.<release>.tar.gz` et [install-Worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) dans un système de fichiers distribués (par exemple, dBFS) auquel votre cluster a accès.

## <a name="prepare-your-net-for-apache-spark-app"></a>Préparer votre application .NET pour Apache Spark

1. Suivez le didacticiel de [prise en main](get-started.md) pour créer votre application.

2. Publiez votre application Spark .NET comme autonome.

   Vous pouvez exécuter la commande suivante sur Linux.

   ```bash
   dotnet publish -c Release -f netcoreapp2.1 -r ubuntu.16.04-x64
   ```

3. Produit `<your app>.zip` pour les fichiers publiés.

   Vous pouvez exécuter la commande suivante sur Linux à `zip`l’aide de.

   ```bash
   zip -r <your app>.zip .
   ```

4. Téléchargez les éléments suivants dans un système de fichiers distribués (par exemple, DBFS) auquel votre cluster a accès:

   * `microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar`: Ce fichier jar est inclus dans le package NuGet [Microsoft. Spark](https://www.nuget.org/packages/Microsoft.Spark/) et colocalisé dans le répertoire de sortie de la génération de votre application.
   * `<your app>.zip`
   * Les fichiers (comme les fichiers de dépendance ou les données communes accessibles à chaque Worker) ou les assemblys (comme les dll qui contiennent vos fonctions définies par l’utilisateur ou les bibliothèques dont dépend votre application) doivent être placés dans le répertoire de travail de chaque exécuteur.

## <a name="deploy-to-databricks"></a>Déployer sur Databricks

[Databricks](https://databricks.com) est une plateforme qui fournit le traitement Big Data basé sur le Cloud à l’aide de Apache Spark.

> [!Note] 
> [Azure Databricks](https://azure.microsoft.com/services/databricks/) et [AWS Databricks](https://databricks.com/aws) sont basés sur Linux. Par conséquent, si vous souhaitez déployer votre application sur Databricks, assurez-vous que votre application est .NET Standard compatible et que vous utilisez le [compilateur .net Core](https://dotnet.microsoft.com/download) pour compiler votre application.

Databricks vous permet de soumettre .NET pour Apache Spark des applications à un cluster actif existant ou de créer un nouveau cluster chaque fois que vous lancez un travail. Pour ce faire, vous devez installer **Microsoft. Spark. Worker** avant d’envoyer un .net pour Apache Spark application.

### <a name="deploy-microsoftsparkworker"></a>Déployer Microsoft. Spark. Worker

Cette étape n’est requise qu’une seule fois pour un cluster.

1. Téléchargez [DB-init.sh](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh) et [install-Worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh
) sur votre ordinateur local.

2. Modifiez **DB-init.sh** pour qu’il pointe vers la version **Microsoft. Spark. Worker** que vous souhaitez télécharger et installer sur votre cluster.

3. Installez l' [interface CLI Databricks](https://docs.databricks.com/user-guide/dev-tools/databricks-cli.html).

4. Configurez les détails d' [authentification](https://docs.databricks.com/user-guide/dev-tools/databricks-cli.html#set-up-authentication) pour l’interface CLI Databricks.

5. Téléchargez les fichiers sur votre cluster Databricks à l’aide de la commande suivante:

   ```bash
   cd <path-to-db-init-and-install-worker>
   databricks fs cp db-init.sh dbfs:/spark-dotnet/db-init.sh
   databricks fs cp install-worker.sh dbfs:/spark-dotnet/install-worker.sh
   ```

6. Accédez à votre espace de travail Databricks. Sélectionnez **clusters** dans le menu de gauche, puis **créer un cluster**.

7. Après avoir configuré le cluster de manière appropriée, définissez le **script init** et créez le cluster.

   ![Image d’action de script](./media/databricks-deployment/deployment-databricks-init-script.png)

## <a name="run-your-app"></a>Exécuter votre application 

Vous pouvez utiliser `set JAR` ou `spark-submit` pour envoyer votre travail à Databricks.

### <a name="use-set-jar"></a>Utiliser SET JAR

[Set jar](https://docs.databricks.com/user-guide/jobs.html#create-a-job) vous permet de soumettre un travail à un cluster actif existant.

#### <a name="one-time-setup"></a>Configuration unique

1. Accédez à votre cluster Databricks et sélectionnez **travaux** dans le menu de gauche. Sélectionnez ensuite **Set jar**.

2. Téléchargez le fichier `microsoft-spark-<spark-version>-<spark-dotnet-version>.jar` approprié.

3. Définissez les paramètres de manière appropriée.

   ```
   Main Class: org.apache.spark.deploy.DotnetRunner
   Arguments /dbfs/apps/<your-app-name>.zip <your-app-main-class>
   ```
 
4. Configurez le **cluster** pour qu’il pointe vers le cluster existant pour lequel vous avez créé le **script init** pour dans la section précédente.

#### <a name="publish-and-run-your-app"></a>Publier et exécuter votre application

1. Utilisez l' [interface CLI Databricks](https://docs.databricks.com/user-guide/dev-tools/databricks-cli.html) pour charger votre application sur votre cluster Databricks.

      ```bash
      cd <path-to-your-app-publish-directory>
      databricks fs cp <your-app-name>.zip dbfs:/apps/<your-app-name>.zip
      ```

2. Cette étape est requise uniquement si vos assemblys d’application (par exemple, les dll qui contiennent des fonctions définies par l’utilisateur ainsi que leurs dépendances) doivent être placés dans le répertoire de travail de chaque **Microsoft. Spark. Worker**.

   - Charger vos assemblys d’application sur votre cluster Databricks
      
      ```bash
      cd <path-to-your-app-publish-directory>
      databricks fs cp <assembly>.dll dbfs:/apps/dependencies
      ```

   - Supprimez les marques de commentaire et modifiez la section dépendances de l’application dans [DB-init.sh](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh) pour pointer vers le chemin d’accès aux dépendances de votre application et téléchargez vers votre cluster Databricks.
   
      ```bash
      cd <path-to-db-init-and-install-worker>
      databricks fs cp db-init.sh dbfs:/spark-dotnet/db-init.sh
      ```
   
   - Redémarrez votre cluster.

3. Accédez à votre cluster Databricks dans votre espace de travail Databricks. Sous **travaux**, sélectionnez votre tâche, puis sélectionnez **Exécuter maintenant** pour exécuter votre travail.

### <a name="use-spark-submit"></a>Utiliser Spark-Submit

La commande [Spark-Submit](https://spark.apache.org/docs/latest/submitting-applications.html) vous permet d’envoyer un travail à un nouveau cluster.

1. [Créez un travail](https://docs.databricks.com/user-guide/jobs.html) et sélectionnez **configurer Spark-Submit**.

2. Configurez `spark-submit` avec les paramètres suivants:

      ```bash
      ["--files","/dbfs/<path-to>/<app assembly/file to deploy to worker>","--class","org.apache.spark.deploy.DotnetRunner","/dbfs/<path-to>/microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar","/dbfs/<path-to>/<app name>.zip","<app bin name>","app arg1","app arg2"]
      ```

3. Accédez à votre cluster Databricks dans votre espace de travail Databricks. Sous **travaux**, sélectionnez votre tâche, puis sélectionnez **Exécuter maintenant** pour exécuter votre travail.

## <a name="next-steps"></a>Étapes suivantes

Dans ce didacticiel, vous avez déployé votre application .NET pour Apache Spark sur Databricks. Pour en savoir plus sur Databricks, consultez la documentation Azure Databricks.

> [!div class="nextstepaction"]
> [Documentation Azure Databricks](https://docs.microsoft.com/azure/azure-databricks/)
