---
title: Connectez .NET pour Apache Spark à MongoDB
description: Découvrez comment vous connecter à votre instance MongoDB à partir de votre application .NET pour Apache Spark.
ms.date: 10/09/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 4cb78998ddb54621a84e9d224a814047e3c40246
ms.sourcegitcommit: eb7e87496f42361b1da98562dd75b516c9d58bbc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/09/2020
ms.locfileid: "91877899"
---
# <a name="connect-net-for-apache-spark-to-mongodb"></a>Connectez .NET pour Apache Spark à MongoDB

Dans cet article, vous allez apprendre à vous connecter à une instance MongoDB à partir de votre application .NET pour Apache Spark.

## <a name="prerequisites"></a>Prérequis

1. Avoir un serveur MongoDB opérationnel avec une [base de données et une collection](https://docs.mongodb.com/manual/core/databases-and-collections/) ajoutée (téléchargez [ce serveur de communauté](https://www.mongodb.com/try/download/community) pour un serveur local ou vous pouvez essayer [MongoDB Atlas](https://www.mongodb.com/cloud/atlas) pour un service Cloud MongoDB).

## <a name="set-up-your-mongodb-instance"></a>Configurer votre instance MongoDB

Pour que Apache Spark .NET puisse communiquer avec votre instance MongoDB, vous devez vous assurer qu’elle est correctement configurée en procédant comme suit :

1. Créez un nom d’utilisateur et un mot de passe pour permettre à votre application de se connecter, et accordez à l’utilisateur les autorisations/rôles nécessaires à l’aide de la commande suivante via l’interpréteur de commandes Mongo :

    ```bash
    use database
    db.createUser(
      {
        user: "mySparkUser",
        pwd: "<password>",
        roles: [ { role: "userAdminAnyDatabase", db: "admin" }, "readWriteAnyDatabase" ]
      }
    )
    ```

2. Assurez-vous que l’adresse IP de l’ordinateur sur lequel votre application .NET pour Apache Spark s’exécute est liste d’autorisation pour que le serveur MongoDB puisse se connecter à. Vous pouvez vous reporter à [ce guide](https://docs.atlas.mongodb.com/security/add-ip-address-to-list/) pour savoir comment procéder.

## <a name="configure-your-net-for-apache-spark-application"></a>Configurer votre application .NET pour Apache Spark

1. Utilisez les variables suivantes pour configurer votre application pour communiquer avec l’instance MongoDB et lire à partir d’une collection.
    1. **authURI**: « chaîne de connexion autorisant votre application à se connecter à l’instance MongoDB requise ». Le format de est le suivant :

        ```
        "mongodb+srv://<username>:<password>@<cluster_address>/<database>.<collection>"
        ```

    2. **nom d’utilisateur**: nom d’utilisateur du compte que vous avez créé à l’étape 1 de la section précédente
    3. **mot de passe**: mot de passe du compte d’utilisateur créé
    4. **cluster_address**: nom d’hôte/adresse de votre cluster MongoDB
    5. **base de données**: la base de données MongoDB à laquelle vous souhaitez vous connecter
    6. **collection**: collection MongoDB que vous souhaitez lire. (Pour cet exemple, nous utilisons l' [`people.json`](https://github.com/apache/spark/blob/master/examples/src/main/resources/people.json) exemple de fichier standard fourni avec chaque installation Apache Spark.)

2. Utilisez le `com.mongodb.spark.sql.DefaultSource` format `spark.Read()` comme indiqué ci-dessous dans un extrait de code simple :

    ```csharp
    class Program
    {
        static void Main()
        {
            var authURI = "mongodb+srv://<username>:<password>@<cluster_address>/<database>.<collection>?retryWrites=true&w=majority";
            SparkSession spark = SparkSession
                .Builder()
                .AppName("Connect to Mongo DB example")
                .Config("spark.mongodb.input.uri", authURI)
                .GetOrCreate();

            DataFrame df = spark.Read().Format("com.mongodb.spark.sql.DefaultSource").Load();
            df.PrintSchema();
            df.Show();
            spark.Stop();
        }
    }
    ```

## <a name="run-your-application"></a>Exécuter votre application

Pour exécuter votre application .NET pour Apache Spark, vous devez définir le module dans `mongo-spark-connector` le cadre de la définition de build dans votre projet Spark, à l’aide `libraryDependency` de dans `build.sbt` pour les projets SBT. Pour les environnements Spark tels que `spark-submit` (ou `spark-shell` ), vous devez utiliser l' `--packages` option de ligne de commande comme suit :

```bash
spark-submit --master local --packages org.mongodb.spark:mongo-spark-connector_2.12:3.0.0 --class org.apache.spark.deploy.dotnet.DotnetRunner microsoft-spark-<version>.jar yourApp.exe
```

> [!NOTE]
> Veillez à inclure la version du package conformément à la version de Spark en cours d’exécution.

Le résultat affiché est le tableau ( `df` ), comme indiqué ci-dessous :

```text
+--------------------+----+-------+
|                 _id| age|   name|
+--------------------+----+-------+
|[5f7c28438029a134...|null|Michael|
|[5f7c287f8029a134...|  30|   Andy|
|[5f7c289a8029a134...|  19| Justin|
+--------------------+----+-------+
```
