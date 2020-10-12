---
title: Connectez .NET pour Apache Spark à Azure Event Hubs
description: Découvrez comment vous connecter à Azure Event Hub à partir de .NET local pour Apache Spark instance.
ms.date: 10/09/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 4de4836ba2b63429e29ae819afac09c7a3998480
ms.sourcegitcommit: b59237ca4ec763969a0dd775a3f8f39f8c59fe24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2020
ms.locfileid: "91954969"
---
# <a name="connect-net-for-apache-spark-to-azure-event-hubs"></a><span data-ttu-id="cd369-103">Connectez .NET pour Apache Spark à Azure Event Hubs</span><span class="sxs-lookup"><span data-stu-id="cd369-103">Connect .NET for Apache Spark to Azure Event Hubs</span></span>

<span data-ttu-id="cd369-104">Dans cet article, vous allez apprendre à connecter votre application [.net pour Apache Spark](https://github.com/dotnet/spark) avec Azure Event hubs pour lire et écrire des flux de Apache Kafka.</span><span class="sxs-lookup"><span data-stu-id="cd369-104">In this article, you will learn how to connect your [.NET for Apache Spark](https://github.com/dotnet/spark) application with Azure Event Hubs to read and write Apache Kafka streams.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="cd369-105">Prérequis</span><span class="sxs-lookup"><span data-stu-id="cd369-105">Prerequisites</span></span>

<span data-ttu-id="cd369-106">Préparez un espace de noms Event Hubs avec une Event Hub.</span><span class="sxs-lookup"><span data-stu-id="cd369-106">Have an Event Hubs Namespace ready with an event hub.</span></span> <span data-ttu-id="cd369-107">Pour obtenir un guide pas à pas, reportez-vous à [démarrage rapide : créer un Event Hub à l’aide de portail Azure](/azure/event-hubs/event-hubs-create).</span><span class="sxs-lookup"><span data-stu-id="cd369-107">For a step-by-step guide, refer to [Quickstart: Create an event hub using Azure portal](/azure/event-hubs/event-hubs-create).</span></span> <span data-ttu-id="cd369-108">Veillez à sélectionner le niveau tarifaire standard lors de la création de l’espace de noms Event Hub.</span><span class="sxs-lookup"><span data-stu-id="cd369-108">Make sure to select the Standard Pricing tier while creating the Event Hub Namespace.</span></span>

## <a name="what-is-azure-event-hubs"></a><span data-ttu-id="cd369-109">Qu’est-ce qu’Azure Event Hubs</span><span class="sxs-lookup"><span data-stu-id="cd369-109">What is Azure Event Hubs</span></span>

<span data-ttu-id="cd369-110">[Azure Event hubs](/azure/event-hubs/event-hubs-about) est une plateforme de diffusion en continu Big Data et un service d’ingestion d’événements.</span><span class="sxs-lookup"><span data-stu-id="cd369-110">[Azure Event Hubs](/azure/event-hubs/event-hubs-about) is a big-data streaming platform and event-ingestion service.</span></span> <span data-ttu-id="cd369-111">Il s’agit d’une plateforme PaaS (Platform-as-a-service) entièrement gérée qui peut s’intégrer facilement à [Apache Kafka](https://kafka.apache.org/) pour vous offrir l’expérience Kafka PaaS sans avoir à gérer, configurer ou exécuter vos propres clusters.</span><span class="sxs-lookup"><span data-stu-id="cd369-111">It is a fully managed Platform-as-a-Service (PaaS) that can easily integrate with [Apache Kafka](https://kafka.apache.org/) to give you the PaaS Kafka experience without having to manage, configure, or run your own clusters.</span></span>

## <a name="connect-your-application-to-azure-event-hubs"></a><span data-ttu-id="cd369-112">Connecter votre application à Azure Event Hubs</span><span class="sxs-lookup"><span data-stu-id="cd369-112">Connect your application to Azure Event Hubs</span></span>

1. <span data-ttu-id="cd369-113">Obtenez la chaîne de connexion Event Hubs et le nom de domaine complet (FQDN) pour une utilisation ultérieure.</span><span class="sxs-lookup"><span data-stu-id="cd369-113">Get the Event Hubs connection string and fully qualified domain name (FQDN) for later use.</span></span> <span data-ttu-id="cd369-114">Pour obtenir des instructions, consultez [Obtenir une chaîne de connexion Event Hubs](/azure/event-hubs/event-hubs-get-connection-string).</span><span class="sxs-lookup"><span data-stu-id="cd369-114">For instructions, see [Get an Event Hubs connection string](/azure/event-hubs/event-hubs-get-connection-string).</span></span>
2. <span data-ttu-id="cd369-115">Définissez les configurations suivantes avec les détails de votre espace de noms dans votre code pour commencer à lire à partir de Event Hubs pour Kafka :</span><span class="sxs-lookup"><span data-stu-id="cd369-115">Set the following configurations with details from your namespace in your code to start reading from Event Hubs for Kafka:</span></span>
    1. <span data-ttu-id="cd369-116">Mettez à jour **BOOTSTRAP_SERVERS** et **EH_SASL** dans votre application comme suit :</span><span class="sxs-lookup"><span data-stu-id="cd369-116">Update **BOOTSTRAP_SERVERS** and **EH_SASL** in your application like so:</span></span>

    ```csharp
    string BOOTSTRAP_SERVERS = "hostname:9093"; // 9093 is the port used to communicate with Event Hubs, see [troubleshooting guide](https://docs.microsoft.com/azure/event-hubs/troubleshooting-guide)
    string EH_SASL = "org.apache.kafka.common.security.plain.PlainLoginModule required username=\"$ConnectionString\" password=\"<CONNECTION_STRING>\";"; // Connection string obtained from Step 1
    ```

## <a name="read-from-azure-event-hub-stream"></a><span data-ttu-id="cd369-117">Lire à partir du flux Azure Event Hub</span><span class="sxs-lookup"><span data-stu-id="cd369-117">Read from Azure Event Hub stream</span></span>

<span data-ttu-id="cd369-118">Vous pouvez maintenant démarrer la diffusion en continu avec Event Hubs comme vous le feriez avec Kafka.</span><span class="sxs-lookup"><span data-stu-id="cd369-118">You can now start streaming with Event Hubs as you would with Kafka.</span></span> <span data-ttu-id="cd369-119">Exemple de code comme indiqué ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="cd369-119">Sample code as shown below:</span></span>

```csharp
SparkSession spark = SparkSession
    .Builder()
    .AppName("Connect Event Hub")
    .GetOrCreate();

DataFrame df = spark
    .ReadStream()
    .Format("kafka")
    .Option("kafka.bootstrap.servers", BOOTSTRAP_SERVERS)
    .Option("subscribe", "spark-test")
    .Option("kafka.sasl.mechanism", "PLAIN")
    .Option("kafka.security.protocol", "SASL_SSL")
    .Option("kafka.sasl.jaas.config", EH_SASL)
    .Option("kafka.request.timeout.ms", "60000")
    .Option("kafka.session.timeout.ms", "60000")
    .Option("failOnDataLoss", "false")
    .Load();

DataFrame dfWrite = df
    .WriteStream()
    .OutputMode("append")
    .Format("console")
    .Start();
```

## <a name="write-to-azure-event-hub-stream"></a><span data-ttu-id="cd369-120">Écrire dans le flux Azure Event Hub</span><span class="sxs-lookup"><span data-stu-id="cd369-120">Write to Azure Event Hub stream</span></span>

<span data-ttu-id="cd369-121">Vous pouvez également écrire dans Event Hubs de la même façon, comme indiqué ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="cd369-121">You can also write to Event Hubs in the same way, as shown below:</span></span>

```csharp
// df is the DataFrame to write

df.WriteStream()
    .Format("kafka")
    .Option("topic", topics)
    .Option("kafka.bootstrap.servers", BOOTSTRAP_SERVERS)
    .Option("kafka.sasl.mechanism", "PLAIN")
    .Option("kafka.security.protocol", "SASL_SSL")
    .Option("kafka.sasl.jaas.config", EH_SASL)
    .Option("checkpointLocation", "./checkpoint")
    .Start();
```

## <a name="run-your-application"></a><span data-ttu-id="cd369-122">Exécuter votre application</span><span class="sxs-lookup"><span data-stu-id="cd369-122">Run your application</span></span>

<span data-ttu-id="cd369-123">Pour exécuter votre application .NET pour Apache Spark, définissez le module dans `spark-sql-kafka-0-10` le cadre de la définition de build dans votre projet Spark, en utilisant `libraryDependency` in `build.sbt` pour les projets SBT.</span><span class="sxs-lookup"><span data-stu-id="cd369-123">In order to run your .NET for Apache Spark application, define the `spark-sql-kafka-0-10` module as part of the build definition in your Spark project, using `libraryDependency` in `build.sbt` for sbt projects.</span></span> <span data-ttu-id="cd369-124">Pour les environnements Spark tels que `spark-submit` (ou `spark-shell` ), utilisez l' `--packages` option de ligne de commande comme suit :</span><span class="sxs-lookup"><span data-stu-id="cd369-124">For Spark environments such as `spark-submit` (or `spark-shell`), use the `--packages` command-line option like so:</span></span>

```bash
spark-shell --packages org.apache.spark:spark-sql-kafka-0-10_2.12:2.4.5
```

> [!NOTE]
> <span data-ttu-id="cd369-125">Veillez à inclure la version du package conformément à la version de Spark en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="cd369-125">Make sure to include the package version in accordance with the version of Spark being run.</span></span>
