---
title: Azure Event Grid - Applications sans serveur
description: Azure Event Grid est une solution sans serveur pour la livraison d’événements fiable et le routage à grande échelle sur un modèle de pay-per-event.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 3c577139c12567e762aabd58c9dc29457fa37aa1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72522717"
---
# <a name="event-grid"></a>Event Grid

[Azure Event Grid](/azure/event-grid/overview) fournit une infrastructure sans serveur pour les applications basées sur les événements. Vous pouvez publier sur Event Grid à partir de n’importe quelle source et consommer des messages à partir de n’importe quelle plate-forme. Event Grid bénéficie également d’un soutien intégré pour les événements des ressources Azure pour rationaliser l’intégration avec vos applications. Par exemple, vous pouvez vous abonner à des événements de stockage blob pour aviser votre application lorsqu’un fichier est téléchargé. Votre application peut ensuite publier un message personnalisé sur la grille d’événements qui est consommé par d’autres applications cloud ou sur site. Event Grid a été construit pour gérer de manière fiable l’échelle massive. Vous bénéficiez des avantages de la publication et de l’abonnement aux messages sans frais généraux de la mise en place de l’infrastructure nécessaire.

![Logo Event Grid](./media/event-grid-logo.png)

Les principales caractéristiques de la grille d’événements sont les suivantes :

- Itinéraire d’événements entièrement géré.
- Livraison d’événements en temps quasi réel à l’échelle.
- Couverture large à l’intérieur et à l’extérieur d’Azure.

## <a name="scenarios"></a>Scénarios

Event Grid aborde plusieurs scénarios différents. Cette section couvre trois des plus courantes.

### <a name="ops-automation"></a>Automatisation des opérations

![Automatisation des opérations](./media/ops-automation.png)

Event Grid peut aider à accélérer l’automatisation et simplifier l’application des politiques en avisant [Azure Automation](https://docs.microsoft.com/azure/automation) lorsque l’infrastructure est mise à disposition.

### <a name="application-integration"></a>Intégration d’applications

![Intégration d’applications](./media/app-integration.png)

Vous pouvez utiliser Event Grid pour connecter votre application à d’autres services. À l’aide de protocoles HTTP standard, même les applications héritées peuvent être facilement modifiées pour publier des messages Event Grid. Des crochets Web sont disponibles pour d’autres services et plates-formes pour consommer les messages Event Grid.

### <a name="serverless-apps"></a>Applications serverless

![Applications serverless](./media/serverless-apps.png)

Event Grid peut déclencher azure Functions, Logic Apps, ou votre propre code personnalisé. Un avantage majeur de l’utilisation de Event Grid est qu’il utilise un mécanisme *de poussée* pour envoyer des messages lorsque des événements se produisent. L’architecture push consomme moins de ressources et d’échelles mieux que les mécanismes *de vote.* Les sondages doivent vérifier les mises à jour d’un intervalle régulier.

## <a name="event-grid-vs-other-azure-messaging-services"></a>Event Grid vs autres services de messagerie Azure

Azure fournit plusieurs services de messagerie, y compris [Event Hubs](https://docs.microsoft.com/azure/event-hubs) et [Service Bus](https://docs.microsoft.com/azure/service-bus-messaging). Chacun est conçu pour traiter un ensemble spécifique de cas d’utilisation. Le diagramme suivant fournit une vue d’ensemble de haut niveau des différences entre les services.

![Comparaison de messagerie Azure](./media/azure-messaging-services.png)

Pour une comparaison plus approfondie, voir [comparer les services](https://docs.microsoft.com/azure/event-grid/compare-messaging-services)de messagerie .

## <a name="performance-targets"></a>Cibles de performance

En utilisant Event Grid, vous pouvez profiter des garanties de performances suivantes :

- Sous-deuxième latence de bout en bout dans le 99e percentile.
- Disponibilité de 99,99 %.
- 10 millions d’événements par seconde par région.
- 100 millions d’abonnements par région.
- Latence éditeur de 50 ms.
- 24 heures de réessayer avec un back-off exponentiel pour une livraison garantie dans la fenêtre d’un jour.
- Échec régional transparent.

## <a name="event-grid-schema"></a>Schéma Event Grid

Event Grid utilise un schéma standard pour envelopper les événements personnalisés. Le schéma est comme une enveloppe qui enveloppe votre élément de données personnalisé. Voici un exemple de message Event Grid :

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

Tout sur le message `data` est standard, sauf la propriété. Vous pouvez inspecter le `eventType` `dataVersion` message et utiliser la partie personnalisée de la charge utile et la dé-sérialiser.

## <a name="azure-resources"></a>Ressources Azure

Un avantage majeur de l’utilisation de Event Grid est les messages automatiques produits par Azure. Dans Azure, les ressources publient automatiquement sur un *sujet* qui vous permet de vous abonner à divers événements. Le tableau suivant répertorie les types de ressources, les types de messages et les événements qui sont disponibles automatiquement.

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
| Hubs d'événements | Microsoft.EventHub.CaptureFileCreated Microsoft.EventHub.CaptureFileCreated Microsoft.EventHub.CaptureFileCreated Microsoft. | Surélevé lorsqu’un fichier de capture est créé.
| IoT Hub | Microsoft.Devices.DeviceCreated | Publié quand un appareil est inscrit auprès d’un hub IoT. |
| | Microsoft.Devices.DeviceDeleted | Publié quand un appareil est supprimé d’un hub IoT. |
| Groupes de ressources | Microsoft.Resources.ResourceWriteSuccess | Déclenché quand une opération de création ou de mise à jour de ressource réussit. |
| | Microsoft.Resources.ResourceWriteFailure | Déclenché quand une opération de création ou de mise à jour de ressource échoue. |
| | Microsoft.Resources.ResourceWriteCancel | Déclenché quand une opération de création ou de mise à jour de ressource est annulée. |
| | Microsoft.Resources.ResourceDeleteSuccess | Déclenché quand une opération de suppression de ressource réussit. |
| | Microsoft.Resources.ResourceDeleteFailure | Déclenché quand une opération de suppression de ressource échoue. |
| | Microsoft.Resources.ResourceDeleteCancel | Déclenché quand une opération de suppression de ressource est annulée. Cet événement se produit lorsque le déploiement d’un modèle est annulé. |

Pour plus d’informations, voir [le schéma d’événements Azure Event Grid](https://docs.microsoft.com/azure/event-grid/event-schema).

Vous pouvez accéder à Event Grid à partir de n’importe quel type d’application, même celui qui fonctionne sur place.

## <a name="conclusion"></a>Conclusion

Dans ce chapitre, vous avez appris sur la plate-forme Azure sans serveur qui est composé de fonctions Azure, applications logiques, et Event Grid. Vous pouvez utiliser ces ressources pour créer une architecture d’application entièrement sans serveur, ou créer une solution hybride qui interagit avec d’autres ressources cloud et serveurs sur site. Combiné avec une plate-forme de données sans serveur comme [Azure SQL](https://docs.microsoft.com/azure/sql-database) ou [CosmosDB](https://docs.microsoft.com/azure/cosmos-db/introduction), vous pouvez construire des applications natives cloud entièrement gérées.

## <a name="recommended-resources"></a>Ressources recommandées

- [Plans de service App](https://docs.microsoft.com/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview)
- [Application Insights](https://docs.microsoft.com/azure/application-insights)
- [Application Insights Analytics](https://docs.microsoft.com/azure/application-insights/app-insights-analytics)
- [Azure: Apportez votre application au cloud avec des fonctions Azure sans serveur](https://channel9.msdn.com/events/Connect/2017/E102)
- [Grille d’événements Azure](https://docs.microsoft.com/azure/event-grid/overview)
- [Schéma d’événement Azure Event Grid](https://docs.microsoft.com/azure/event-grid/event-schema)
- [Azure Event Hubs](https://docs.microsoft.com/azure/event-hubs)
- [Documentation Azure Functions](https://docs.microsoft.com/azure/azure-functions)
- [Concepts des déclencheurs et liaisons Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-triggers-bindings)
- [Applications Azure Logic](https://docs.microsoft.com/azure/logic-apps)
- [Azure Service Bus](https://docs.microsoft.com/azure/service-bus-messaging)
- [Stockage de table Azure](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview)
- [Comparez les fonctions 1.x et 2.x](https://docs.microsoft.com/azure/azure-functions/functions-versions)
- [Connexion aux sources de données locales avec la passerelle de données locale Azure](https://docs.microsoft.com/azure/analysis-services/analysis-services-gateway)
- [Créer votre première fonction à l’aide du Portail Azure](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function)
- [Créez votre première fonction à l’aide d’Azure CLI](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function-azure-cli)
- [Créer votre première fonction à l’aide de Visual Studio](https://docs.microsoft.com/azure/azure-functions/functions-create-your-first-function-visual-studio)
- [Langues supportées fonctions](https://docs.microsoft.com/azure/azure-functions/supported-languages)
- [Superviser Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-monitoring)
- [Utilisation d’Azure Functions Proxies](https://docs.microsoft.com/azure/azure-functions/functions-proxies)

>[!div class="step-by-step"]
>[Suivant précédent](logic-apps.md)
>[Next](durable-azure-functions.md)
