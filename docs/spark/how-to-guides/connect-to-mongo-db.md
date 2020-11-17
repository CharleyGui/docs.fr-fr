---
title: Connectez .NET pour Apache Spark à MongoDB
description: Découvrez comment vous connecter à votre instance MongoDB à partir de votre application .NET pour Apache Spark.
ms.author: nidutta
author: Niharikadutta
ms.date: 10/09/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 945e494e8a027d438bf4659d989da6033a13f6f0
ms.sourcegitcommit: 34968a61e9bac0f6be23ed6ffb837f52d2390c85
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94687601"
---
# <a name="connect-net-for-apache-spark-to-mongodb"></a><span data-ttu-id="3a650-103">Connectez .NET pour Apache Spark à MongoDB</span><span class="sxs-lookup"><span data-stu-id="3a650-103">Connect .NET for Apache Spark to MongoDB</span></span>

<span data-ttu-id="3a650-104">Dans cet article, vous allez apprendre à vous connecter à une instance MongoDB à partir de votre application .NET pour Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="3a650-104">In this article, you learn how to connect to a MongoDB instance from your .NET for Apache Spark application.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="3a650-105">Prérequis</span><span class="sxs-lookup"><span data-stu-id="3a650-105">Prerequisites</span></span>

1. <span data-ttu-id="3a650-106">Avoir un serveur MongoDB opérationnel avec une [base de données et une collection](https://docs.mongodb.com/manual/core/databases-and-collections/) ajoutée (téléchargez [ce serveur de communauté](https://www.mongodb.com/try/download/community) pour un serveur local ou vous pouvez essayer [MongoDB Atlas](https://www.mongodb.com/cloud/atlas) pour un service Cloud MongoDB).</span><span class="sxs-lookup"><span data-stu-id="3a650-106">Have a MongoDB server up and running with a [database and some collection](https://docs.mongodb.com/manual/core/databases-and-collections/) added to it (Download [this community server](https://www.mongodb.com/try/download/community) for a local server or you can try [MongoDB Atlas](https://www.mongodb.com/cloud/atlas) for a cloud MongoDB service.)</span></span>

## <a name="set-up-your-mongodb-instance"></a><span data-ttu-id="3a650-107">Configurer votre instance MongoDB</span><span class="sxs-lookup"><span data-stu-id="3a650-107">Set up your MongoDB instance</span></span>

<span data-ttu-id="3a650-108">Pour que Apache Spark .NET puisse communiquer avec votre instance MongoDB, vous devez vous assurer qu’elle est correctement configurée en procédant comme suit :</span><span class="sxs-lookup"><span data-stu-id="3a650-108">In order to get .NET for Apache Spark to talk to your MongoDB instance you need to make sure it is set up correctly by doing the following:</span></span>

1. <span data-ttu-id="3a650-109">Créez un nom d’utilisateur et un mot de passe pour permettre à votre application de se connecter, et accordez à l’utilisateur les autorisations/rôles nécessaires à l’aide de la commande suivante via l’interpréteur de commandes Mongo :</span><span class="sxs-lookup"><span data-stu-id="3a650-109">Create a username and password for your application to connect through, and give the user the necessary permissions/roles using the following command through mongo shell:</span></span>

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

2. <span data-ttu-id="3a650-110">Assurez-vous que l’adresse IP de l’ordinateur sur lequel votre application .NET pour Apache Spark s’exécute est liste d’autorisation pour que le serveur MongoDB puisse se connecter à.</span><span class="sxs-lookup"><span data-stu-id="3a650-110">Make sure the IP address of the machine your .NET for Apache Spark application is running on is whitelisted for the MongoDB server to be able to connect to.</span></span> <span data-ttu-id="3a650-111">Vous pouvez vous reporter à [ce guide](https://docs.atlas.mongodb.com/security/add-ip-address-to-list/) pour savoir comment procéder.</span><span class="sxs-lookup"><span data-stu-id="3a650-111">You can refer to [this guide](https://docs.atlas.mongodb.com/security/add-ip-address-to-list/) to learn how to do that.</span></span>

## <a name="configure-your-net-for-apache-spark-application"></a><span data-ttu-id="3a650-112">Configurer votre application .NET pour Apache Spark</span><span class="sxs-lookup"><span data-stu-id="3a650-112">Configure your .NET for Apache Spark application</span></span>

1. <span data-ttu-id="3a650-113">Utilisez les variables suivantes pour configurer votre application pour communiquer avec l’instance MongoDB et lire à partir d’une collection.</span><span class="sxs-lookup"><span data-stu-id="3a650-113">Have the following variables set to configure your application to talk to the MongoDB instance and read from a collection.</span></span>
    1. <span data-ttu-id="3a650-114">**authURI**: « chaîne de connexion autorisant votre application à se connecter à l’instance MongoDB requise ».</span><span class="sxs-lookup"><span data-stu-id="3a650-114">**authURI**: "Connection string authorizing your application to connect to the required MongoDB instance".</span></span> <span data-ttu-id="3a650-115">Le format de est le suivant :</span><span class="sxs-lookup"><span data-stu-id="3a650-115">The format for that is as follows:</span></span>

        ```
        "mongodb+srv://<username>:<password>@<cluster_address>/<database>.<collection>"
        ```

    2. <span data-ttu-id="3a650-116">**nom d’utilisateur**: nom d’utilisateur du compte que vous avez créé à l’étape 1 de la section précédente</span><span class="sxs-lookup"><span data-stu-id="3a650-116">**username**: Username of the account you created in Step 1 of the previous section</span></span>
    3. <span data-ttu-id="3a650-117">**mot de passe**: mot de passe du compte d’utilisateur créé</span><span class="sxs-lookup"><span data-stu-id="3a650-117">**password**: Password of the user account created</span></span>
    4. <span data-ttu-id="3a650-118">**cluster_address**: nom d’hôte/adresse de votre cluster MongoDB</span><span class="sxs-lookup"><span data-stu-id="3a650-118">**cluster_address**: hostname/address of your MongoDB cluster</span></span>
    5. <span data-ttu-id="3a650-119">**base de données**: la base de données MongoDB à laquelle vous souhaitez vous connecter</span><span class="sxs-lookup"><span data-stu-id="3a650-119">**database**: The MongoDB database you want to connect to</span></span>
    6. <span data-ttu-id="3a650-120">**collection**: collection MongoDB que vous souhaitez lire.</span><span class="sxs-lookup"><span data-stu-id="3a650-120">**collection**: The MongoDB collection you want to read.</span></span> <span data-ttu-id="3a650-121">(Pour cet exemple, nous utilisons l' [`people.json`](https://github.com/apache/spark/blob/master/examples/src/main/resources/people.json) exemple de fichier standard fourni avec chaque installation Apache Spark.)</span><span class="sxs-lookup"><span data-stu-id="3a650-121">(For this example we use the standard [`people.json`](https://github.com/apache/spark/blob/master/examples/src/main/resources/people.json) example file provided with every Apache Spark installation.)</span></span>

2. <span data-ttu-id="3a650-122">Utilisez le `com.mongodb.spark.sql.DefaultSource` format `spark.Read()` comme indiqué ci-dessous dans un extrait de code simple :</span><span class="sxs-lookup"><span data-stu-id="3a650-122">Use the `com.mongodb.spark.sql.DefaultSource` format is `spark.Read()` as shown below in a simple code snippet:</span></span>

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

## <a name="run-your-application"></a><span data-ttu-id="3a650-123">Exécuter votre application</span><span class="sxs-lookup"><span data-stu-id="3a650-123">Run your application</span></span>

<span data-ttu-id="3a650-124">Pour exécuter votre application .NET pour Apache Spark, vous devez définir le module dans `mongo-spark-connector` le cadre de la définition de build dans votre projet Spark, à l’aide `libraryDependency` de dans `build.sbt` pour les projets SBT.</span><span class="sxs-lookup"><span data-stu-id="3a650-124">In order to run your .NET for Apache Spark application, you should define the `mongo-spark-connector` module as part of the build definition in your Spark project, using `libraryDependency` in `build.sbt` for sbt projects.</span></span> <span data-ttu-id="3a650-125">Pour les environnements Spark tels que `spark-submit` (ou `spark-shell` ), vous devez utiliser l' `--packages` option de ligne de commande comme suit :</span><span class="sxs-lookup"><span data-stu-id="3a650-125">For Spark environments such as `spark-submit` (or `spark-shell`) you should use the `--packages` command-line option like so:</span></span>

```bash
spark-submit --master local --packages org.mongodb.spark:mongo-spark-connector_2.12:3.0.0 --class org.apache.spark.deploy.dotnet.DotnetRunner microsoft-spark-<spark_majorversion-spark_minorversion>_<scala_majorversion.scala_minorversion>-<spark_dotnet_version>.jar yourApp.exe
```

> [!NOTE]
> <span data-ttu-id="3a650-126">Veillez à inclure la version du package conformément à la version de Spark en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="3a650-126">Make sure to include the package version in accordance with the version of Spark being run.</span></span>

<span data-ttu-id="3a650-127">Le résultat affiché est le tableau ( `df` ), comme indiqué ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="3a650-127">The result as displayed is the DataFrame (`df`) as shown below:</span></span>

```text
+--------------------+----+-------+
|                 _id| age|   name|
+--------------------+----+-------+
|[5f7c28438029a134...|null|Michael|
|[5f7c287f8029a134...|  30|   Andy|
|[5f7c289a8029a134...|  19| Justin|
+--------------------+----+-------+
```
