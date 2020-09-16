---
title: Envoyer un travail .NET pour Apache Spark à Databricks
description: Découvrez comment soumettre un travail .NET pour Apache Spark à Databricks à l’aide de Spark-Submit et Set jar.
ms.date: 06/25/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 88dc321a08f805ef8c3bf8d4d01d32dd890548d2
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557175"
---
# <a name="submit-a-net-for-apache-spark-job-to-databricks"></a>Envoyer un travail .NET pour Apache Spark à Databricks

Vous pouvez exécuter votre .NET pour les tâches Apache Spark sur les clusters Databricks, mais il n’est pas prêt à l’emploi. Il existe deux façons de déployer votre .NET pour le travail de Apache Spark dans Databricks : et de définir le fichier `spark-submit` jar.

[!INCLUDE [spark-preview-note](../../../includes/spark-preview-note.md)]

## <a name="deploy-using-spark-submit"></a>Déployer à l’aide de Spark-Submit

Vous pouvez utiliser la commande [Spark-Submit](https://spark.apache.org/docs/latest/submitting-applications.html) pour envoyer des travaux .net pour Apache Spark à Databricks. `spark-submit` autorise l’envoi uniquement à un cluster qui est créé à la demande.

1. Accédez à votre espace de travail Databricks et créez un travail. Choisissez un titre pour votre travail, puis sélectionnez **configurer Spark-Submit**. Collez les paramètres suivants dans la configuration du travail, puis sélectionnez **confirmer**.

    ```
    ["--files","/dbfs/<path-to>/<app assembly/file to deploy to worker>","--class","org.apache.spark.deploy.dotnet.DotnetRunner","/dbfs/<path-to>/microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar","/dbfs/<path-to>/<app name>.zip","<app bin name>","app arg1","app arg2"]
    ```

    > [!NOTE]
    > Mettez à jour le contenu du paramètre ci-dessus en fonction de vos fichiers et de votre configuration spécifiques. Par exemple, référencez la version du fichier jar Microsoft. Spark que vous avez chargée sur DBFS et utilisez le nom approprié de votre application et le fichier zip de l’application publiée.

2. Accédez à votre travail et sélectionnez **modifier** pour configurer le cluster de votre travail. Définissez la version de Databricks Runtime en fonction de la version de Apache Spark que vous souhaitez utiliser dans votre déploiement. Sélectionnez ensuite les **Options avancées > les scripts init**et définissez le chemin d’accès du script init sur `dbfs:/spark-dotnet/db-init.sh` . Sélectionnez **confirmer** pour confirmer vos paramètres de cluster.

3. Accédez à votre travail et sélectionnez **Exécuter maintenant** pour exécuter votre travail sur le cluster Spark que vous venez de configurer. La création du cluster du travail prend quelques minutes. Une fois créé, votre travail est envoyé. Vous pouvez afficher la sortie en sélectionnant **clusters** dans le menu de gauche de votre espace de travail Databricks, puis sélectionner **journaux du pilote**.

## <a name="deploy-using-set-jar"></a>Déployer à l’aide de Set jar

Vous pouvez également utiliser [Set jar](/azure/databricks/jobs#--create-a-job) dans votre espace de travail Databricks pour envoyer des travaux .net pour Apache Spark à Databricks. *Set jar* autorise l’envoi de travaux à un cluster actif existant.

### <a name="one-time-setup"></a>Installation unique

1. Accédez à votre cluster Databricks et sélectionnez **travaux** dans le menu de gauche, puis **Set jar**.

2. Téléchargez le approprié `microsoft-spark-<spark-version>-<spark-dotnet-version>.jar` .

3. Modifiez les paramètres suivants pour inclure le nom correct de l’exécutable que vous avez publié à la place de `<your-app-name>` :

    ```
    Main Class: org.apache.spark.deploy.dotnet.DotnetRunner
    Arguments /dbfs/apps/<your-app-name>.zip <your-app-name>
    ```

4. Configurez le cluster pour qu’il pointe vers un cluster existant pour lequel vous avez déjà défini le script init.

### <a name="publish-and-run-your-app"></a>Publier et exécuter votre application

1. Vérifiez que vous avez publié votre application et que le code de votre application n’utilise pas `SparkSession.Stop()` .

2. Utilisez [DATABRICKS CLI](/azure/databricks/dev-tools/databricks-cli) pour charger votre application sur votre cluster Databricks. Par exemple, utilisez la commande suivante pour charger votre application publiée sur votre cluster :

    ```console
    cd <path-to-your-app-publish-directory>
    databricks fs cp <your-app-name>.zip dbfs:/apps/<your-app-name>.zip
    ```

3. Si vous avez des fonctions définies par l’utilisateur dans votre application, les assemblys d’application, tels que les dll qui contiennent des fonctions définies par l’utilisateur ainsi que leurs dépendances, doivent être placés dans le répertoire de travail de chaque *Microsoft. Spark. Worker*.

    Chargez vos assemblys d’application sur votre cluster Databricks :

    ```console
    cd <path-to-your-app-publish-directory>
    databricks fs cp <assembly>.dll dbfs:/apps/dependencies
    ```

    Supprimez les marques de commentaire et modifiez la section dépendances de l’application dans [DB-init.sh](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh) pour pointer vers le chemin de vos dépendances d’application. Ensuite, chargez le *DB-init.sh* mis à jour sur votre cluster :

    ```console
    cd <path-to-db-init-and-install-worker>
    databricks fs cp db-init.sh dbfs:/spark-dotnet/db-init.sh
    ```

4. Accédez à **cluster Databricks > travaux > [job-name] > exécuter maintenant** pour exécuter votre travail.

## <a name="next-steps"></a>Étapes suivantes

* [Bien démarrer avec .NET pour Apache Spark](../tutorials/get-started.md)
* [Déployer une application .NET pour Apache Spark sur Databricks](../tutorials/databricks-deployment.md)
* [Documentation Azure Databricks](/azure/azure-databricks/)
