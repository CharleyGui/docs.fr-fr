---
title: Applications sans serveur Application Insights
description: Application Insights est une plateforme de diagnostic sans serveur qui permet aux développeurs de détecter, de trier et de diagnostiquer les problèmes dans les applications Web, les applications mobiles, les applications de bureau et les microservices.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 7c1013ac029645a2da44aaf1c3b6ba74ca3f3dde
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/08/2019
ms.locfileid: "72522743"
---
# <a name="telemetry-with-application-insights"></a><span data-ttu-id="c0d36-103">Télémétrie avec Application Insights</span><span class="sxs-lookup"><span data-stu-id="c0d36-103">Telemetry with Application Insights</span></span>

<span data-ttu-id="c0d36-104">[Application Insights](https://docs.microsoft.com/azure/application-insights) est une plateforme de diagnostic sans serveur qui permet aux développeurs de détecter, de trier et de diagnostiquer les problèmes dans les applications Web, les applications mobiles, les applications de bureau et les microservices.</span><span class="sxs-lookup"><span data-stu-id="c0d36-104">[Application Insights](https://docs.microsoft.com/azure/application-insights) is a serverless diagnostics platform that enables developers to detect, triage, and diagnose issues in web apps, mobile apps, desktop apps, and microservices.</span></span> <span data-ttu-id="c0d36-105">Vous pouvez activer Application Insights pour les applications de fonction simplement en basculant un commutateur dans le portail.</span><span class="sxs-lookup"><span data-stu-id="c0d36-105">You can turn on Application Insights for function apps simply by flipping a switch in the portal.</span></span> <span data-ttu-id="c0d36-106">Application Insights fournit toutes ces fonctionnalités sans avoir à configurer un serveur ou à configurer votre propre base de données.</span><span class="sxs-lookup"><span data-stu-id="c0d36-106">Application Insights provides all of these capabilities without you having to configure a server or set up your own database.</span></span> <span data-ttu-id="c0d36-107">Toutes les fonctionnalités de Application Insights sont fournies en tant que service qui s’intègre automatiquement à vos applications.</span><span class="sxs-lookup"><span data-stu-id="c0d36-107">All of Application Insights' capabilities are provided as a service that automatically integrates with your apps.</span></span>

![Logo Application Insights](./media/application-insights-logo.png)

<span data-ttu-id="c0d36-109">L’ajout d’Application Insights à des applications existantes est aussi simple que l’ajout d’une clé d’instrumentation aux paramètres de votre application.</span><span class="sxs-lookup"><span data-stu-id="c0d36-109">Adding Application Insights to existing apps is as easy as adding an instrumentation key to your application's settings.</span></span> <span data-ttu-id="c0d36-110">Avec Application Insights vous pouvez :</span><span class="sxs-lookup"><span data-stu-id="c0d36-110">With Application Insights you can:</span></span>

- <span data-ttu-id="c0d36-111">Créer des graphiques et des alertes personnalisés en fonction de métriques telles que le nombre d’appels de fonction, le temps nécessaire pour exécuter une fonction et les exceptions</span><span class="sxs-lookup"><span data-stu-id="c0d36-111">Create custom charts and alerts based on metrics such as number of function invocations, the time it takes to run a function, and exceptions</span></span>
- <span data-ttu-id="c0d36-112">Analyser les échecs et les exceptions de serveur</span><span class="sxs-lookup"><span data-stu-id="c0d36-112">Analyze failures and server exceptions</span></span>
- <span data-ttu-id="c0d36-113">Explorez les performances par fonctionnement et mesurez le temps nécessaire pour appeler des dépendances tierces</span><span class="sxs-lookup"><span data-stu-id="c0d36-113">Drill into performance by operation and measure the time it takes to call third-party dependencies</span></span>
- <span data-ttu-id="c0d36-114">Surveiller l’utilisation du processeur, la mémoire et les débits sur tous les serveurs qui hébergent vos applications de fonction</span><span class="sxs-lookup"><span data-stu-id="c0d36-114">Monitor CPU usage, memory, and rates across all servers that host your function apps</span></span>
- <span data-ttu-id="c0d36-115">Afficher un flux Live de métriques, notamment le nombre de demandes et la latence de vos applications de fonction</span><span class="sxs-lookup"><span data-stu-id="c0d36-115">View a live stream of metrics including request count and latency for your function apps</span></span>
- <span data-ttu-id="c0d36-116">Utilisez [Analytics](https://docs.microsoft.com/azure/application-insights/app-insights-analytics) pour rechercher, interroger et créer des graphiques personnalisés sur vos données de fonction</span><span class="sxs-lookup"><span data-stu-id="c0d36-116">Use [Analytics](https://docs.microsoft.com/azure/application-insights/app-insights-analytics) to search, query, and create custom charts over your function data</span></span>

![Metrics Explorer](./media/metrics-explorer.png)

<span data-ttu-id="c0d36-118">En plus des données de télémétrie intégrées, il est également possible de générer des données de télémétrie personnalisées.</span><span class="sxs-lookup"><span data-stu-id="c0d36-118">In addition to built-in telemetry, it's also possible to generate custom telemetry.</span></span> <span data-ttu-id="c0d36-119">L’extrait de code suivant crée un client de télémétrie personnalisé à l’aide de la clé d’instrumentation définie pour l’application de fonction :</span><span class="sxs-lookup"><span data-stu-id="c0d36-119">The following code snippet creates a custom telemetry client using the instrumentation key set for the function app:</span></span>

```csharp
public static TelemetryClient telemetry = new TelemetryClient()
{
    InstrumentationKey = Environment.GetEnvironmentVariable("APPINSIGHTS_INSTRUMENTATIONKEY")
};
```

<span data-ttu-id="c0d36-120">Le code suivant mesure le temps nécessaire pour insérer une nouvelle ligne dans une instance de [stockage de table Azure](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview) :</span><span class="sxs-lookup"><span data-stu-id="c0d36-120">The following code measures how long it takes to insert a new row into an [Azure Table Storage](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview) instance:</span></span>

```csharp
var operation = TableOperation.Insert(entry);
var startTime = DateTime.UtcNow;
var timer = System.Diagnostics.Stopwatch.StartNew();
await table.ExecuteAsync(operation);
telemetry.TrackDependency("AzureTableStorageInsert", "Insert", startTime, timer.Elapsed, true);
```

<span data-ttu-id="c0d36-121">Le graphique de performances qui en résulte est affiché :</span><span class="sxs-lookup"><span data-stu-id="c0d36-121">The resulting performance graph is shown:</span></span>

![Télémétrie personnalisée](./media/custom-telemetry.png)

<span data-ttu-id="c0d36-123">La télémétrie personnalisée révèle que la durée moyenne d’insertion d’une nouvelle ligne est de 32,6 millisecondes.</span><span class="sxs-lookup"><span data-stu-id="c0d36-123">The custom telemetry reveals the average time to insert a new row is 32.6 milliseconds.</span></span>

<span data-ttu-id="c0d36-124">Application Insights offre un moyen puissant et pratique de consigner des données de télémétrie détaillées sur vos applications sans serveur.</span><span class="sxs-lookup"><span data-stu-id="c0d36-124">Application Insights provides a powerful, convenient way to log detailed telemetry about your serverless applications.</span></span> <span data-ttu-id="c0d36-125">Vous disposez d’un contrôle total sur le niveau de suivi et de journalisation fourni.</span><span class="sxs-lookup"><span data-stu-id="c0d36-125">You have full control over the level of tracing and logging that is provided.</span></span> <span data-ttu-id="c0d36-126">Vous pouvez suivre des statistiques personnalisées telles que les événements, les dépendances et le mode page.</span><span class="sxs-lookup"><span data-stu-id="c0d36-126">You can track custom statistics such as events, dependencies, and page view.</span></span> <span data-ttu-id="c0d36-127">Enfin, les analyses puissantes vous permettent d’écrire des requêtes qui posent des questions importantes et génèrent des graphiques et des Insights avancés.</span><span class="sxs-lookup"><span data-stu-id="c0d36-127">Finally, the powerful analytics enable you to write queries that ask important questions and generate charts and advanced insights.</span></span>

<span data-ttu-id="c0d36-128">Pour plus d’informations, consultez [surveiller Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-monitoring).</span><span class="sxs-lookup"><span data-stu-id="c0d36-128">For more information, see [Monitor Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-monitoring).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="c0d36-129">[Précédent](azure-functions.md)
>[Suivant](logic-apps.md)</span><span class="sxs-lookup"><span data-stu-id="c0d36-129">[Previous](azure-functions.md)
[Next](logic-apps.md)</span></span>
