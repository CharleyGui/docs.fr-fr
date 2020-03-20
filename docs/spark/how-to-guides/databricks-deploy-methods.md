---
title: Soumettez un .NET pour Apache Spark à Databricks
description: Apprenez à soumettre un .NET pour apache Spark emploi à Databricks en utilisant spark-submit et Set Jar.
ms.date: 12/05/2019
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 65976f9095ecef66e0538c398492033c612c1430
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79187606"
---
# <a name="submit-a-net-for-apache-spark-job-to-databricks"></a>Soumettez un .NET pour Apache Spark à Databricks

Il existe deux façons de déployer votre .NET pour Apache Spark emploi à Databricks: `spark-submit` et Set Jar.

## <a name="deploy-using-spark-submit"></a>Déploiement à l’aide d’étincelles-soumettre

Vous pouvez utiliser la commande [spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html) pour soumettre .NET pour les emplois Apache Spark à Databricks. `spark-submit`ne permet la soumission qu’à un cluster qui est créé à la demande.

1. Naviguez vers votre espace de travail Databricks et créez un emploi. Choisissez un titre pour votre travail, puis **sélectionnez Configurer étincelle-soumettre**. Coller les paramètres suivants dans la configuration du travail, puis sélectionnez **Confirm**.

    ```
    ["--files","/dbfs/<path-to>/<app assembly/file to deploy to worker>","--class","org.apache.spark.deploy.dotnet.DotnetRunner","/dbfs/<path-to>/microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar","/dbfs/<path-to>/<app name>.zip","<app bin name>","app arg1","app arg2"]
    ```

    > [!NOTE]
    > Mettez à jour le contenu du paramètre ci-dessus en fonction de vos fichiers et configuration spécifiques. Par exemple, faites référence à la version du fichier de pot Microsoft.Spark que vous avez téléchargé sur DBFS, et utilisez le nom approprié de votre application et de votre fichier zip d’application publié.

2. Naviguez dans votre travail et sélectionnez **Edit** pour configurer le cluster de votre travail. Réglez la version Databricks Runtime en fonction de la version d’Apache Spark que vous souhaitez utiliser dans votre déploiement. Sélectionnez ensuite **Les options avancées > scripts Init**, `dbfs:/spark-dotnet/db-init.sh`et définissez Init Script Path comme . Sélectionnez **Confirmez** pour confirmer les paramètres de votre cluster.

3. Naviguez dans votre travail et sélectionnez **Run Now** pour exécuter votre travail sur votre cluster Spark nouvellement configuré. Il faut quelques minutes pour que le cluster du travail soit créé. Une fois qu’il sera créé, votre travail sera soumis. Vous pouvez afficher la sortie en sélectionnant des **clusters** à partir du menu gauche de votre espace de travail Databricks, puis sélectionnez **les journaux de pilote**.

## <a name="deploy-using-set-jar"></a>Déployer à l’aide de Set Jar

Alternativement, vous pouvez utiliser [Set Jar](https://docs.microsoft.com/azure/databricks/jobs#--create-a-job) dans votre espace de travail Databricks pour soumettre .NET pour apache Spark emplois à Databricks. *Set Jar* permet la soumission d’emploi à un cluster actif existant.

### <a name="one-time-setup"></a>Installation unique

1. Naviguez vers votre cluster Databricks et sélectionnez **des travaux** dans le menu gauche, suivi de **Set JAR**.

2. Téléchargez `microsoft-spark-<spark-version>-<spark-dotnet-version>.jar`le approprié .

3. Modifier les paramètres suivants pour inclure le nom correct pour `<your-app-name>`l’exécutable que vous avez publié à la place de :

    ```
    Main Class: org.apache.spark.deploy.dotnet.DotnetRunner
    Arguments /dbfs/apps/<your-app-name>.zip <your-app-name>
    ```

4. Configurez le cluster pour indiquer un cluster existant pour lequel vous avez déjà défini le script init.

### <a name="publish-and-run-your-app"></a>Publier et exécuter votre application

1. Assurez-vous d’avoir publié votre application et `SparkSession.Stop()`que votre code d’application n’utilise pas .

2. Utilisez [Databricks CLI](https://docs.microsoft.com/azure/databricks/dev-tools/databricks-cli) pour télécharger votre application sur votre cluster Databricks. Par exemple, utilisez la commande suivante pour télécharger votre application publiée sur votre cluster :

    ```console
    cd <path-to-your-app-publish-directory>
    databricks fs cp <your-app-name>.zip dbfs:/apps/<your-app-name>.zip
    ```

3. Si vous avez des fonctions définies par l’utilisateur dans votre application, les assemblages d’applications, tels que les DLL qui contiennent des fonctions définies par l’utilisateur avec leurs dépendances, doivent être placés dans l’annuaire de travail de chaque *Microsoft.Spark.Worker*.

    Téléchargez vos assemblages d’applications dans votre cluster Databricks :

    ```console
    cd <path-to-your-app-publish-directory>
    databricks fs cp <assembly>.dll dbfs:/apps/dependencies
    ```

    Désengagement et modifier la section dépendances de l’application dans [db-init.sh](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh) pour indiquer votre chemin de dépendance app. Ensuite, téléchargez les *db-init.sh* mises à jour sur votre cluster :

    ```console
    cd <path-to-db-init-and-install-worker>
    databricks fs cp db-init.sh dbfs:/spark-dotnet/db-init.sh
    ```

4. Naviguez vers **le cluster Databricks > Jobs > [nom d’emploi] > Exécuter maintenant** pour exécuter votre travail.

## <a name="next-steps"></a>Étapes suivantes

* [Bien démarrer avec .NET pour Apache Spark](../tutorials/get-started.md)
* [Déployer une application .NET pour Apache Spark sur Databricks](../tutorials/databricks-deployment.md)
* [Azure Databricks Documentation](https://docs.microsoft.com/azure/azure-databricks/)
