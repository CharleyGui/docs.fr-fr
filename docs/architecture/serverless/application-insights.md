---
title: Applications Insights - Applications sans serveur
description: Application Insights est une plate-forme de diagnostic sans serveur qui permet aux développeurs de détecter, de trier et de diagnostiquer les problèmes dans les applications Web, les applications mobiles, les applications de bureau et les microservices.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 7c1013ac029645a2da44aaf1c3b6ba74ca3f3dde
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72522743"
---
# <a name="telemetry-with-application-insights"></a>Télémétrie avec Application Insights

[Application Insights](https://docs.microsoft.com/azure/application-insights) est une plate-forme de diagnostic sans serveur qui permet aux développeurs de détecter, de trier et de diagnostiquer les problèmes dans les applications Web, les applications mobiles, les applications de bureau et les microservices. Vous pouvez activer application Insights pour les applications de fonction simplement en renversant un interrupteur dans le portail. Application Insights fournit toutes ces fonctionnalités sans que vous ayez à configurer un serveur ou à configurer votre propre base de données. Toutes les capacités d’Application Insights sont fournies en tant que service qui s’intègre automatiquement à vos applications.

![Logo Application Insights](./media/application-insights-logo.png)

L’ajout d’informations d’application aux applications existantes est aussi simple que l’ajout d’une clé d’instrumentation aux paramètres de votre application. Avec Application Insights, vous pouvez :

- Créez des graphiques et des alertes personnalisés en fonction de mesures telles que le nombre d’invocations de fonction, le temps qu’il faut pour exécuter une fonction et des exceptions
- Analyser les défaillances et les exceptions au serveur
- Percer dans la performance par opération et mesurer le temps qu’il faut pour appeler les dépendances de tiers
- Surveillez l’utilisation, la mémoire et les tarifs du processeur sur tous les serveurs qui hébergent vos applications de fonction
- Afficher un flux en direct de mesures, y compris le nombre de demandes et la latence pour vos applications de fonction
- Utilisez [Analytics](https://docs.microsoft.com/azure/application-insights/app-insights-analytics) pour rechercher, interroger et créer des graphiques personnalisés sur vos données de fonction

![Metrics Explorer](./media/metrics-explorer.png)

En plus de la télémétrie intégrée, il est également possible de générer une télémétrie personnalisée. L’extrait de code suivant crée un client de télémétrie personnalisé à l’aide de l’ensemble de clé d’instrumentation pour l’application de fonction :

```csharp
public static TelemetryClient telemetry = new TelemetryClient()
{
    InstrumentationKey = Environment.GetEnvironmentVariable("APPINSIGHTS_INSTRUMENTATIONKEY")
};
```

Le code suivant mesure le temps qu’il faut pour insérer une nouvelle ligne dans une instance [de stockage de table Azure](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview) :

```csharp
var operation = TableOperation.Insert(entry);
var startTime = DateTime.UtcNow;
var timer = System.Diagnostics.Stopwatch.StartNew();
await table.ExecuteAsync(operation);
telemetry.TrackDependency("AzureTableStorageInsert", "Insert", startTime, timer.Elapsed, true);
```

Le graphique de performance qui en résulte est affiché :

![Télémétrie personnalisée](./media/custom-telemetry.png)

La télémétrie personnalisée révèle que le temps moyen d’insertion d’une nouvelle ligne est de 32,6 millisecondes.

Application Insights fournit un moyen puissant et pratique de enregistrer la télémétrie détaillée sur vos applications sans serveur. Vous avez le plein contrôle sur le niveau de traçage et d’enregistrement qui est fourni. Vous pouvez suivre les statistiques personnalisées telles que les événements, les dépendances et la vue de page. Enfin, les analyses puissantes vous permettent d’écrire des requêtes qui posent des questions importantes et génèrent des graphiques et des idées avancées.

Pour plus d’informations, consultez [Surveiller l’exécution des fonctions Azure](https://docs.microsoft.com/azure/azure-functions/functions-monitoring).

>[!div class="step-by-step"]
>[Suivant précédent](azure-functions.md)
>[Next](logic-apps.md)
