---
title: Applications sans serveur Azure Event Grid
description: Azure Event Grid est une solution sans serveur pour la remise d’événements fiable et le routage à grande échelle sur un modèle de paiement à l’événement.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 04/06/2020
ms.openlocfilehash: 408e1b9cd1b1e5316c7c6a17bb1b0c76a38f9e11
ms.sourcegitcommit: 8b02d42f93adda304246a47f49f6449fc74a3af4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/24/2020
ms.locfileid: "82135709"
---
# <a name="event-grid"></a>Event Grid

[Azure Event Grid](/azure/event-grid/overview) fournit une infrastructure sans serveur pour les applications basées sur les événements. Vous pouvez publier sur Event Grid à partir de n’importe quelle source et utiliser des messages de n’importe quelle plateforme. Event Grid offre également une prise en charge intégrée des événements des ressources Azure pour simplifier l’intégration avec vos applications. Par exemple, vous pouvez vous abonner à des événements de stockage d’objets BLOB pour notifier votre application quand un fichier est chargé. Votre application peut ensuite publier un message de grille d’événements personnalisé qui est consommé par d’autres applications Cloud ou locales. Event Grid a été conçu pour gérer de manière fiable une grande échelle. Vous bénéficiez des avantages de la publication et de l’abonnement aux messages sans la surcharge liée à la configuration de l’infrastructure nécessaire.

![Logo Event Grid](./media/event-grid-logo.png)

Les principales fonctionnalités d’Event Grid sont les suivantes :

- Routage d’événements entièrement géré.
- Livraison d’événements presque en temps réel à l’échelle.
- Couverture étendue à l’intérieur et à l’extérieur d’Azure.

## <a name="scenarios"></a>Scénarios

Event Grid résout plusieurs scénarios différents. Cette section couvre les trois des plus courants.

### <a name="ops-automation"></a>Automatisation des opérations

![Automatisation des opérations](./media/ops-automation.png)

Event Grid pouvez accélérer l’automatisation et simplifier l’application des stratégies en avertissant [Azure Automation](https://docs.microsoft.com/azure/automation) quand l’infrastructure est approvisionnée.

### <a name="application-integration"></a>Intégration d’applications

![Intégration d’applications](./media/app-integration.png)

Vous pouvez utiliser Event Grid pour connecter votre application à d’autres services. À l’aide des protocoles HTTP standard, même les applications héritées peuvent être facilement modifiées pour publier des messages Event Grid. Des webhooks sont disponibles pour d’autres services et plateformes pour utiliser des messages Event Grid.

### <a name="serverless-apps"></a>Applications serverless

![Applications serverless](./media/serverless-apps.png)

Event Grid pouvez déclencher Azure Functions, Logic Apps ou votre propre code personnalisé. L’un des principaux avantages de l’utilisation de Event Grid est qu’elle utilise un mécanisme *Push* pour envoyer des messages lorsque des événements se produisent. L’architecture Push consomme moins de ressources et évolue mieux que les mécanismes d' *interrogation* . L’interrogation doit vérifier les mises à jour à intervalles réguliers.

## <a name="event-grid-vs-other-azure-messaging-services"></a>Event Grid et d’autres services de messagerie Azure

Azure fournit plusieurs services de messagerie, y compris [Event hubs](https://docs.microsoft.com/azure/event-hubs) et [service bus](https://docs.microsoft.com/azure/service-bus-messaging). Chaque est conçu pour répondre à un ensemble spécifique de cas d’usage. Le diagramme suivant fournit une vue d’ensemble des différences entre les services.

![Comparaison de la messagerie Azure](./media/azure-messaging-services.png)

Pour une comparaison plus détaillée, consultez comparer les [services de messagerie](https://docs.microsoft.com/azure/event-grid/compare-messaging-services).

## <a name="performance-targets"></a>Cibles de performance

À l’aide de Event Grid vous pouvez tirer parti des garanties de performances suivantes :

- Latence de bout en bout sous-seconde dans le 99e centile.
- Disponibilité de 99,99 %.
- 10 millions événements par seconde par région.
- 100 millions abonnements par région.
- 50-latence MS Publisher.
- nouvelle tentative de 24 heures avec interruption exponentielle pour la livraison garantie dans la fenêtre de 1 jour.
- Basculement régional transparent.

## <a name="event-grid-schema"></a>Schéma Event Grid

Event Grid utilise un schéma standard pour encapsuler les événements personnalisés. Le schéma est comme une enveloppe qui encapsule votre élément de données personnalisé. Voici un exemple Event Grid message :

```json
[{
    "id": "03e24f21-a955-43cc-8921-1f61a6081ce0",
    "eventType": "myCustomEvent",
    "subject": "foo/bar/12",
    "eventTime": "2018-09-22T10:36:01+00:00",
    "data": {
        "favoriteColor": "blue",
        "favoriteAnimal": "panther",
        "favoritePlanet": "Jupiter"
    },
    "dataVersion": "1.0"
}]
```

Tout ce qui concerne le message est standard `data` , à l’exception de la propriété. Vous pouvez inspecter le message et utiliser `eventType` et `dataVersion` pour désérialiser la partie personnalisée de la charge utile.

## <a name="azure-resources"></a>Ressources Azure

L’un des principaux avantages de l’utilisation de Event Grid est l’automatisation des messages générés par Azure. Dans Azure, les ressources publient automatiquement sur une *rubrique* qui vous permet de vous abonner à différents événements. Le tableau suivant répertorie les types de ressources, les types de messages et les événements qui sont disponibles automatiquement.

| Ressource Azure | Type d'événement | Description |
| -------------- | ---------- | ----------- |
| Abonnement Azure | Microsoft.Resources.ResourceWriteSuccess | Déclenché quand une opération de création ou de mise à jour de ressource réussit. |
| | Microsoft.Resources.ResourceWriteFailure | Déclenché quand une opération de création ou de mise à jour de ressource échoue. |
| | Microsoft.Resources.ResourceWriteCancel | Déclenché quand une opération de création ou de mise à jour de ressource est annulée. |
|  | Microsoft.Resources.ResourceDeleteSuccess | Déclenché quand une opération de suppression de ressource réussit. |
|  | Microsoft.Resources.ResourceDeleteFailure | Déclenché quand une opération de suppression de ressource échoue. |
| | Microsoft.Resources.ResourceDeleteCancel | Déclenché quand une opération de suppression de ressource est annulée. Cet événement se produit lorsque le déploiement d’un modèle est annulé. |
| Stockage d'objets blob | Microsoft.Storage.BlobCreated | Déclenché lorsqu’un objet blob est créé. |
| | Microsoft.Storage.BlobDeleted | Déclenché lorsqu’un objet blob est supprimé. |
| Hubs d'événements | Microsoft. EventHub. CaptureFileCreated | Déclenché lors de la création d’un fichier de capture.
| IoT Hub | Microsoft.Devices.DeviceCreated | Publié quand un appareil est inscrit auprès d’un hub IoT. |
| | Microsoft.Devices.DeviceDeleted | Publié quand un appareil est supprimé d’un hub IoT. |
| Groupes de ressources | Microsoft.Resources.ResourceWriteSuccess | Déclenché quand une opération de création ou de mise à jour de ressource réussit. |
| | Microsoft.Resources.ResourceWriteFailure | Déclenché quand une opération de création ou de mise à jour de ressource échoue. |
| | Microsoft.Resources.ResourceWriteCancel | Déclenché quand une opération de création ou de mise à jour de ressource est annulée. |
| | Microsoft.Resources.ResourceDeleteSuccess | Déclenché quand une opération de suppression de ressource réussit. |
| | Microsoft.Resources.ResourceDeleteFailure | Déclenché quand une opération de suppression de ressource échoue. |
| | Microsoft.Resources.ResourceDeleteCancel | Déclenché quand une opération de suppression de ressource est annulée. Cet événement se produit lorsque le déploiement d’un modèle est annulé. |

Pour plus d’informations, consultez [Azure Event Grid le schéma d’événement](https://docs.microsoft.com/azure/event-grid/event-schema).

Vous pouvez accéder à Event Grid à partir de n’importe quel type d’application, même s’il s’exécute en local.

## <a name="conclusion"></a>Conclusion

Dans ce chapitre, vous avez découvert la plateforme sans serveur Azure composée de Azure Functions, Logic Apps et Event Grid. Vous pouvez utiliser ces ressources pour créer une architecture d’application entièrement sans serveur, ou créer une solution hybride qui interagit avec d’autres ressources Cloud et serveurs locaux. Combiné à une plateforme de données sans serveur telle qu' [Azure SQL](https://docs.microsoft.com/azure/sql-database) ou [CosmosDB](https://docs.microsoft.com/azure/cosmos-db/introduction), vous pouvez créer des applications Cloud natives entièrement gérées.

## <a name="recommended-resources"></a>Ressources recommandées

- [Plans App service](https://docs.microsoft.com/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview)
- [Application Insights](https://docs.microsoft.com/azure/application-insights)
- [Application Insights Analytics](https://docs.microsoft.com/azure/application-insights/app-insights-analytics)
- [Azure : mettez votre application dans le Cloud avec des Azure Functions sans serveur](https://channel9.msdn.com/events/Connect/2017/E102)
- [Azure Event Grid](https://docs.microsoft.com/azure/event-grid/overview)
- [Schéma d’événement Azure Event Grid](https://docs.microsoft.com/azure/event-grid/event-schema)
- [Azure Event Hubs](https://docs.microsoft.com/azure/event-hubs)
- [Documentation sur Azure Functions](https://docs.microsoft.com/azure/azure-functions)
- [Concepts des déclencheurs et liaisons Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-triggers-bindings)
- [Azure Logic Apps](https://docs.microsoft.com/azure/logic-apps)
- [Azure Service Bus](https://docs.microsoft.com/azure/service-bus-messaging)
- [Stockage de tables Azure](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview)
- [Connexion aux sources de données locales avec la passerelle de données locale Azure](https://docs.microsoft.com/azure/analysis-services/analysis-services-gateway)
- [Créer votre première fonction à l’aide du Portail Azure](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function)
- [Créez votre première fonction à l’aide d’Azure CLI](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function-azure-cli)
- [Créer votre première fonction à l’aide de Visual Studio](https://docs.microsoft.com/azure/azure-functions/functions-create-your-first-function-visual-studio)
- [Fonctions prises en charge par les fonctions](https://docs.microsoft.com/azure/azure-functions/supported-languages)
- [Superviser Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-monitoring)

>[!div class="step-by-step"]
>[Précédent](logic-apps.md)
>[suivant](durable-azure-functions.md)
