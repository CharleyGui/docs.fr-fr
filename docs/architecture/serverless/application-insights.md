---
title: Applications sans serveur Application Insights
description: Application Insights est une plateforme de diagnostic sans serveur qui permet aux développeurs de détecter, de trier et de diagnostiquer les problèmes dans les applications Web, les applications mobiles, les applications de bureau et les microservices.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 42791b052ebb068c9b7109291e66b30b47e5821f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91173319"
---
# <a name="telemetry-with-application-insights"></a>Télémétrie avec Application Insights

[Application Insights](/azure/application-insights) est une plateforme de diagnostic sans serveur qui permet aux développeurs de détecter, de trier et de diagnostiquer les problèmes dans les applications Web, les applications mobiles, les applications de bureau et les microservices. Vous pouvez activer Application Insights pour les applications de fonction simplement en basculant un commutateur dans le portail. Application Insights fournit toutes ces fonctionnalités sans avoir à configurer un serveur ou à configurer votre propre base de données. Toutes les fonctionnalités de Application Insights sont fournies en tant que service qui s’intègre automatiquement à vos applications.

![Logo Application Insights](./media/application-insights-logo.png)

L’ajout d’Application Insights à des applications existantes est aussi simple que l’ajout d’une clé d’instrumentation aux paramètres de votre application. Avec Application Insights vous pouvez :

- Créer des graphiques et des alertes personnalisés en fonction de métriques telles que le nombre d’appels de fonction, le temps nécessaire pour exécuter une fonction et les exceptions
- Analyser les échecs et les exceptions de serveur
- Explorez les performances par fonctionnement et mesurez le temps nécessaire pour appeler des dépendances tierces
- Surveiller l’utilisation du processeur, la mémoire et les débits sur tous les serveurs qui hébergent vos applications de fonction
- Afficher un flux Live de métriques, notamment le nombre de demandes et la latence de vos applications de fonction
- Utilisez [Analytics](/azure/application-insights/app-insights-analytics) pour rechercher, interroger et créer des graphiques personnalisés sur vos données de fonction

![Metrics Explorer](./media/metrics-explorer.png)

En plus des données de télémétrie intégrées, il est également possible de générer des données de télémétrie personnalisées. L’extrait de code suivant crée un client de télémétrie personnalisé à l’aide de la clé d’instrumentation définie pour l’application de fonction :

```csharp
public static TelemetryClient telemetry = new TelemetryClient()
{
    InstrumentationKey = Environment.GetEnvironmentVariable("APPINSIGHTS_INSTRUMENTATIONKEY")
};
```

Le code suivant mesure le temps nécessaire pour insérer une nouvelle ligne dans une instance de [stockage de table Azure](/azure/cosmos-db/table-storage-overview) :

```csharp
var operation = TableOperation.Insert(entry);
var startTime = DateTime.UtcNow;
var timer = System.Diagnostics.Stopwatch.StartNew();
await table.ExecuteAsync(operation);
telemetry.TrackDependency("AzureTableStorageInsert", "Insert", startTime, timer.Elapsed, true);
```

Le graphique de performances qui en résulte est affiché :

![Télémétrie personnalisée](./media/custom-telemetry.png)

La télémétrie personnalisée révèle que la durée moyenne d’insertion d’une nouvelle ligne est de 32,6 millisecondes.

Application Insights offre un moyen puissant et pratique de consigner des données de télémétrie détaillées sur vos applications sans serveur. Vous disposez d’un contrôle total sur le niveau de suivi et de journalisation fourni. Vous pouvez suivre des statistiques personnalisées telles que les événements, les dépendances et le mode page. Enfin, les analyses puissantes vous permettent d’écrire des requêtes qui posent des questions importantes et génèrent des graphiques et des Insights avancés.

Pour plus d’informations, consultez [Surveiller l’exécution des fonctions Azure](/azure/azure-functions/functions-monitoring).

>[!div class="step-by-step"]
>[Précédent](azure-functions.md) 
> [Suivant](logic-apps.md)
