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
# <a name="connect-net-for-apache-spark-to-azure-event-hubs"></a>Connectez .NET pour Apache Spark à Azure Event Hubs

Dans cet article, vous allez apprendre à connecter votre application [.net pour Apache Spark](https://github.com/dotnet/spark) avec Azure Event hubs pour lire et écrire des flux de Apache Kafka.

## <a name="prerequisites"></a>Prérequis

Préparez un espace de noms Event Hubs avec une Event Hub. Pour obtenir un guide pas à pas, reportez-vous à [démarrage rapide : créer un Event Hub à l’aide de portail Azure](/azure/event-hubs/event-hubs-create). Veillez à sélectionner le niveau tarifaire standard lors de la création de l’espace de noms Event Hub.

## <a name="what-is-azure-event-hubs"></a>Qu’est-ce qu’Azure Event Hubs

[Azure Event hubs](/azure/event-hubs/event-hubs-about) est une plateforme de diffusion en continu Big Data et un service d’ingestion d’événements. Il s’agit d’une plateforme PaaS (Platform-as-a-service) entièrement gérée qui peut s’intégrer facilement à [Apache Kafka](https://kafka.apache.org/) pour vous offrir l’expérience Kafka PaaS sans avoir à gérer, configurer ou exécuter vos propres clusters.

## <a name="connect-your-application-to-azure-event-hubs"></a>Connecter votre application à Azure Event Hubs

1. Obtenez la chaîne de connexion Event Hubs et le nom de domaine complet (FQDN) pour une utilisation ultérieure. Pour obtenir des instructions, consultez [Obtenir une chaîne de connexion Event Hubs](/azure/event-hubs/event-hubs-get-connection-string).
2. Définissez les configurations suivantes avec les détails de votre espace de noms dans votre code pour commencer à lire à partir de Event Hubs pour Kafka :
    1. Mettez à jour **BOOTSTRAP_SERVERS** et **EH_SASL** dans votre application comme suit :

    ```csharp
    string BOOTSTRAP_SERVERS = "hostname:9093"; // 9093 is the port used to communicate with Event Hubs, see [troubleshooting guide](https://docs.microsoft.com/azure/event-hubs/troubleshooting-guide)
    string EH_SASL = "org.apache.kafka.common.security.plain.PlainLoginModule required username=\"$ConnectionString\" password=\"<CONNECTION_STRING>\";"; // Connection string obtained from Step 1
    ```

## <a name="read-from-azure-event-hub-stream"></a>Lire à partir du flux Azure Event Hub

Vous pouvez maintenant démarrer la diffusion en continu avec Event Hubs comme vous le feriez avec Kafka. Exemple de code comme indiqué ci-dessous :

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

## <a name="write-to-azure-event-hub-stream"></a>Écrire dans le flux Azure Event Hub

Vous pouvez également écrire dans Event Hubs de la même façon, comme indiqué ci-dessous :

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

## <a name="run-your-application"></a>Exécuter votre application

Pour exécuter votre application .NET pour Apache Spark, définissez le module dans `spark-sql-kafka-0-10` le cadre de la définition de build dans votre projet Spark, en utilisant `libraryDependency` in `build.sbt` pour les projets SBT. Pour les environnements Spark tels que `spark-submit` (ou `spark-shell` ), utilisez l' `--packages` option de ligne de commande comme suit :

```bash
spark-shell --packages org.apache.spark:spark-sql-kafka-0-10_2.12:2.4.5
```

> [!NOTE]
> Veillez à inclure la version du package conformément à la version de Spark en cours d’exécution.
