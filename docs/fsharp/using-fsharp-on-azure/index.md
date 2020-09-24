---
title: Utilisation de F# dans Azure
description: 'Guide d’utilisation des services Azure avec F #'
author: sylvanc
ms.date: 07/29/2020
ms.custom: devx-track-fsharp
ms.openlocfilehash: c3235db9274065f81e5476d8d0e06b99d7c987a0
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91100137"
---
# <a name="using-f-on-azure"></a>Utilisation de F# dans Azure

F# est un excellent langage pour la programmation dans le cloud. Fréquemment utilisé pour écrire des applications web, des services cloud et des microservices hébergés dans le cloud, il permet aussi de traiter des données scalables.

Vous trouverez dans les sections suivantes des ressources expliquant comment utiliser de nombreux services Azure avec F#.

> [!NOTE]
> Si un service Azure particulier ne figure pas dans cette documentation, consultez la documentation Azure Functions ou .NET pour ce service. Certains services Azure sont indépendants du langage et ne nécessitent aucune documentation spécifique au langage. Ces services ne sont pas listés ici.

## <a name="using-azure-virtual-machines-with-f"></a>Utilisation de Machines virtuelles Azure avec F\#

Azure prend en charge un large éventail de configurations de machine virtuelle. Pour plus d’informations, consultez [Machines virtuelles Linux et Azure](https://azure.microsoft.com/services/virtual-machines/).

Pour installer F# sur une machine virtuelle pour exécution, compilation et/ou création de scripts, consultez [Utilisation de F# sur Linux](https://fsharp.org/use/linux) et [Utilisation de F# sur Windows](https://fsharp.org/use/windows).

## <a name="using-azure-functions-with-f"></a>Utilisation d’Azure Functions avec F\#

[Azure Functions](https://azure.microsoft.com/services/functions/) est une solution permettant d’exécuter facilement de petits morceaux de code, ou « fonctions », dans le Cloud. Vous pouvez simplement écrire le code dont vous avez besoin pour le problème, sans vous soucier d’une application dans sa globalité ou de l’infrastructure pour l’exécuter. Les fonctions sont connectées à des événements dans le stockage Azure et à d’autres ressources hébergées dans le cloud. Les données sont acheminées aux fonctions F# par le biais d’arguments de fonction. Vous pouvez utiliser le langage de développement de votre choix, Azure se chargeant de la mise à l’échelle en fonction des besoins.

Azure Functions, qui prend en charge F# comme langage de première classe, exécute le code F# de manière efficace, réactive et scalable. Pour obtenir une documentation de référence sur l’utilisation de F# avec Azure Functions, consultez [Informations de référence pour les développeurs F# sur Azure Functions](/azure/azure-functions/functions-reference-fsharp).

Autres ressources relatives à l’utilisation d’Azure Functions et de F# :

* [Mettre à l’échelle Azure Functions en F # à l’aide de suave](https://blog.tamizhvendan.in/blog/2016/09/19/scale-up-azure-functions-in-f-number-using-suave/)
* [Comment créer une fonction Azure dans F #](https://www.mnie.me/azurefunctions)
* [Utilisation du fournisseur de type Azure avec Azure Functions](https://compositional-it.com/blog/2017/08-30-using-the-azure-type-provider-with-azure-functions/index.html)

## <a name="using-azure-storage-with-f"></a>Utilisation de Stockage Azure avec F\#

Stockage Azure est une couche de base de services de stockage pour les applications modernes qui s’appuient sur la durabilité, la disponibilité et la scalabilité afin de répondre aux besoins de leurs clients. Les programmes F # peuvent interagir directement avec les services de stockage Azure, à l’aide des techniques décrites dans les articles suivants.

* [Bien démarrer avec le stockage Blob Azure en F#](blob-storage.md)
* [Bien démarrer avec le stockage Fichier Azure en F#](file-storage.md)
* [Bien démarrer avec le stockage File d’attente Azure en F#](queue-storage.md)
* [Bien démarrer avec le stockage Table Azure en F#](table-storage.md)

Vous pouvez aussi utiliser Stockage Azure conjointement avec Azure Functions en remplaçant les appels d’API explicites par une configuration déclarative. Pour obtenir des exemples d’utilisation de F#, consultez [Déclencheurs et liaisons Azure Functions pour Stockage Azure](/azure/azure-functions/functions-bindings-storage).

## <a name="using-azure-app-service-with-f"></a>Utilisation d’Azure App Service avec F\#

[Azure App Service](https://azure.microsoft.com/services/app-service/) est une plateforme cloud qui permet de générer des applications web et mobiles performantes qui se connectent aux données en tout lieu, dans le cloud ou localement.

* [Exemple d’API web Azure F#](https://github.com/fsprojects/azure-webapi-example)
* [Hébergement de F# dans une application web sur Azure](https://github.com/isaacabraham/fsharp-demonstrator)

## <a name="using-apache-spark-with-f-on-azure-hdinsight-or-azure-databricks"></a>Utilisation de Apache Spark avec F # sur Azure HDInsight ou Azure Databricks

[Apache Spark pour Azure HDInsight](/azure/hdinsight/spark/apache-spark-overview) est une infrastructure de traitement open source qui exécute des applications d’analytique des données à grande échelle. [Azure Databricks](/azure/databricks/scenarios/what-is-azure-databricks) est une plateforme d’analytique basée sur Apache Spark et optimisée pour la plateforme de services cloud Microsoft Azure. Azure vous permet de déployer Apache Spark de manière simple et rentable. Développez votre application Spark en F # à l’aide [de .net pour Apache Spark](../../spark/what-is-apache-spark-dotnet.md), un ensemble de liaisons .net pour Apache Spark.

* [Exemples .NET pour Apache Spark F #](https://github.com/dotnet/spark/tree/master/examples/Microsoft.Spark.FSharp.Examples)
* [Installer des blocs-notes Jupyter .NET interactive dans Azure HDInsight](../../spark/how-to-guides/hdinsight-notebook-installation.md)
* [Envoyer des travaux de Apache Spark à Azure HDInsight](../../spark/how-to-guides/hdinsight-deploy-methods.md)
* [Envoyer des travaux de Apache Spark à Azure Databricks](../../spark/how-to-guides/databricks-deploy-methods.md)

## <a name="using-azure-cosmos-db-with-f"></a>Utilisation de Azure Cosmos DB avec F\#

[Azure Cosmos DB](https://azure.microsoft.com/services/cosmos-db) est un service NoSQL pour les applications hautement disponibles et distribuées dans le monde entier.

Azure Cosmos DB peut être utilisé avec F # de deux manières :

1. Par le biais de la création de F # Azure Functions qui réagissent ou entraînent des modifications dans les collections Azure Cosmos DB. Consultez [Azure Cosmos DB des liaisons pour Azure Functions](/azure/azure-functions/functions-bindings-cosmosdb)ou
2. En utilisant le [Kit de développement logiciel (SDK) .net Azure Cosmos DB pour l’API SQL](/azure/cosmos-db/sql-api-sdk-dotnet). Les exemples associés sont en C#.

## <a name="using-azure-event-hubs-with-f"></a>Utilisation d’Azure Event Hubs avec F\#

[Azure Event Hubs](https://azure.microsoft.com/services/event-hubs/) assure l’ingestion de la télémétrie à l’échelle du cloud à partir de sites web, d’applications et d’appareils.

Vous pouvez utiliser Azure DocumentDB avec F# de deux manières :

1. Soit en créant des fonctions Azure Functions en F# qui sont déclenchées par des événements. Consultez [Déclencheurs Azure Functions pour Event Hubs](/azure/azure-functions/functions-bindings-event-hubs).
2. Soit en utilisant le [SDK .NET pour Azure](/azure/event-hubs/event-hubs-csharp-ephcs-getstarted). Notez que ces exemples sont en C#.

## <a name="using-azure-notification-hubs-with-f"></a>Utilisation d’Azure Notification Hubs avec F\#

[Azure Notification Hubs](/azure/notification-hubs/) est une infrastructure Push multiplateforme avec montée en charge qui vous permet d’envoyer des notifications Push de n’importe quel backend (dans le cloud ou localement) vers toute plateforme mobile.

Vous pouvez utiliser Azure Notification Hubs avec F# de deux manières :

1. Soit en créant des fonctions Azure Functions en F# qui envoient les résultats à un hub de notification. Consultez [Déclencheurs de sortie Azure Function pour Notification Hubs](/azure/azure-functions/functions-bindings-notification-hubs).
2. Soit en utilisant le [SDK .NET pour Azure](/archive/blogs/azuremobile/push-notifications-using-notification-hub-and-net-backend). Notez que ces exemples sont en C#.

## <a name="implementing-webhooks-on-azure-with-f"></a>Implémentation de WebHooks sur Azure avec F\#

Un [Webhook](https://en.wikipedia.org/wiki/Webhook) est un rappel déclenché au moyen d’une requête web. Les Webhooks sont utilisés par des sites tels que GitHub pour signaler des événements.

Vous pouvez implémenter des Webhooks en F# et les héberger sur Azure par le biais d’une [fonction Azure Functions en F# avec une liaison Webhook](/azure/azure-functions/functions-bindings-http-webhook).

## <a name="using-webjobs-with-f"></a>Utilisation de Webjobs avec F\#

Les [Webjobs](/azure/app-service-web/web-sites-create-web-jobs) sont des programmes que vous pouvez exécuter dans votre application web App Service de trois façons : à la demande, en continu ou selon une planification.

[Exemple de Webjob en F# ](https://github.com/jrr/webjob-project-examples)

## <a name="implementing-timers-on-azure-with-f"></a>Implémentation de minuteries sur Azure avec F\#

Les déclencheurs de minuteur appellent des fonctions basées sur une planification ponctuelle ou périodique.

Vous pouvez implémenter des minuteries en F# et les héberger sur Azure par le biais d’une [fonction Azure Functions en F# avec un déclencheur de minuterie](/azure/azure-functions/functions-bindings-timer).

## <a name="deploying-and-managing-azure-resources-with-f-scripts"></a>Déploiement et gestion des ressources Azure avec des scripts F#

Vous pouvez déployer et gérer des machines virtuelles Azure par programmation à partir de scripts F# à l’aide de packages et d’API Microsoft.Azure.Management. Par exemple, consultez [Bien démarrer avec les bibliothèques de gestion pour .NET](/previous-versions/azure/dn722415(v=azure.100)) et [Utilisation d’Azure Resource Manager](/azure/azure-resource-manager/resource-manager-deployment-model).

De même, vous pouvez déployer et gérer d’autres ressources Azure à partir de scripts F# à l’aide des mêmes composants. Par exemple, vous pouvez créer des comptes de stockage, déployer des services Cloud Azure, créer des instances de Azure Cosmos DB et gérer des Notification Hubs Azure par programmation à partir de scripts F #.

Il est généralement inutile d’utiliser des scripts F# pour déployer et gérer des ressources. Par exemple, les ressources Azure peuvent également être déployées directement à partir des descriptions de modèle JSON, qui peuvent être paramétrables. Consultez [Modèles Azure Resource Manager](/azure/azure-resource-manager/resource-manager-template-best-practices), en particulier les exemples fournis tels que les [modèles de démarrage rapide Azure](https://azure.microsoft.com/resources/templates/).

## <a name="other-resources"></a>Autres ressources

* [Documentation complète sur tous les services Azure](/azure/)
