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
# <a name="telemetry-with-application-insights"></a><span data-ttu-id="044d2-103">Télémétrie avec Application Insights</span><span class="sxs-lookup"><span data-stu-id="044d2-103">Telemetry with Application Insights</span></span>

<span data-ttu-id="044d2-104">[Application Insights](https://docs.microsoft.com/azure/application-insights) est une plate-forme de diagnostic sans serveur qui permet aux développeurs de détecter, de trier et de diagnostiquer les problèmes dans les applications Web, les applications mobiles, les applications de bureau et les microservices.</span><span class="sxs-lookup"><span data-stu-id="044d2-104">[Application Insights](https://docs.microsoft.com/azure/application-insights) is a serverless diagnostics platform that enables developers to detect, triage, and diagnose issues in web apps, mobile apps, desktop apps, and microservices.</span></span> <span data-ttu-id="044d2-105">Vous pouvez activer application Insights pour les applications de fonction simplement en renversant un interrupteur dans le portail.</span><span class="sxs-lookup"><span data-stu-id="044d2-105">You can turn on Application Insights for function apps simply by flipping a switch in the portal.</span></span> <span data-ttu-id="044d2-106">Application Insights fournit toutes ces fonctionnalités sans que vous ayez à configurer un serveur ou à configurer votre propre base de données.</span><span class="sxs-lookup"><span data-stu-id="044d2-106">Application Insights provides all of these capabilities without you having to configure a server or set up your own database.</span></span> <span data-ttu-id="044d2-107">Toutes les capacités d’Application Insights sont fournies en tant que service qui s’intègre automatiquement à vos applications.</span><span class="sxs-lookup"><span data-stu-id="044d2-107">All of Application Insights' capabilities are provided as a service that automatically integrates with your apps.</span></span>

![Logo Application Insights](./media/application-insights-logo.png)

<span data-ttu-id="044d2-109">L’ajout d’informations d’application aux applications existantes est aussi simple que l’ajout d’une clé d’instrumentation aux paramètres de votre application.</span><span class="sxs-lookup"><span data-stu-id="044d2-109">Adding Application Insights to existing apps is as easy as adding an instrumentation key to your application's settings.</span></span> <span data-ttu-id="044d2-110">Avec Application Insights, vous pouvez :</span><span class="sxs-lookup"><span data-stu-id="044d2-110">With Application Insights you can:</span></span>

- <span data-ttu-id="044d2-111">Créez des graphiques et des alertes personnalisés en fonction de mesures telles que le nombre d’invocations de fonction, le temps qu’il faut pour exécuter une fonction et des exceptions</span><span class="sxs-lookup"><span data-stu-id="044d2-111">Create custom charts and alerts based on metrics such as number of function invocations, the time it takes to run a function, and exceptions</span></span>
- <span data-ttu-id="044d2-112">Analyser les défaillances et les exceptions au serveur</span><span class="sxs-lookup"><span data-stu-id="044d2-112">Analyze failures and server exceptions</span></span>
- <span data-ttu-id="044d2-113">Percer dans la performance par opération et mesurer le temps qu’il faut pour appeler les dépendances de tiers</span><span class="sxs-lookup"><span data-stu-id="044d2-113">Drill into performance by operation and measure the time it takes to call third-party dependencies</span></span>
- <span data-ttu-id="044d2-114">Surveillez l’utilisation, la mémoire et les tarifs du processeur sur tous les serveurs qui hébergent vos applications de fonction</span><span class="sxs-lookup"><span data-stu-id="044d2-114">Monitor CPU usage, memory, and rates across all servers that host your function apps</span></span>
- <span data-ttu-id="044d2-115">Afficher un flux en direct de mesures, y compris le nombre de demandes et la latence pour vos applications de fonction</span><span class="sxs-lookup"><span data-stu-id="044d2-115">View a live stream of metrics including request count and latency for your function apps</span></span>
- <span data-ttu-id="044d2-116">Utilisez [Analytics](https://docs.microsoft.com/azure/application-insights/app-insights-analytics) pour rechercher, interroger et créer des graphiques personnalisés sur vos données de fonction</span><span class="sxs-lookup"><span data-stu-id="044d2-116">Use [Analytics](https://docs.microsoft.com/azure/application-insights/app-insights-analytics) to search, query, and create custom charts over your function data</span></span>

![Metrics Explorer](./media/metrics-explorer.png)

<span data-ttu-id="044d2-118">En plus de la télémétrie intégrée, il est également possible de générer une télémétrie personnalisée.</span><span class="sxs-lookup"><span data-stu-id="044d2-118">In addition to built-in telemetry, it's also possible to generate custom telemetry.</span></span> <span data-ttu-id="044d2-119">L’extrait de code suivant crée un client de télémétrie personnalisé à l’aide de l’ensemble de clé d’instrumentation pour l’application de fonction :</span><span class="sxs-lookup"><span data-stu-id="044d2-119">The following code snippet creates a custom telemetry client using the instrumentation key set for the function app:</span></span>

```csharp
public static TelemetryClient telemetry = new TelemetryClient()
{
    InstrumentationKey = Environment.GetEnvironmentVariable("APPINSIGHTS_INSTRUMENTATIONKEY")
};
```

<span data-ttu-id="044d2-120">Le code suivant mesure le temps qu’il faut pour insérer une nouvelle ligne dans une instance [de stockage de table Azure](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview) :</span><span class="sxs-lookup"><span data-stu-id="044d2-120">The following code measures how long it takes to insert a new row into an [Azure Table Storage](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview) instance:</span></span>

```csharp
var operation = TableOperation.Insert(entry);
var startTime = DateTime.UtcNow;
var timer = System.Diagnostics.Stopwatch.StartNew();
await table.ExecuteAsync(operation);
telemetry.TrackDependency("AzureTableStorageInsert", "Insert", startTime, timer.Elapsed, true);
```

<span data-ttu-id="044d2-121">Le graphique de performance qui en résulte est affiché :</span><span class="sxs-lookup"><span data-stu-id="044d2-121">The resulting performance graph is shown:</span></span>

![Télémétrie personnalisée](./media/custom-telemetry.png)

<span data-ttu-id="044d2-123">La télémétrie personnalisée révèle que le temps moyen d’insertion d’une nouvelle ligne est de 32,6 millisecondes.</span><span class="sxs-lookup"><span data-stu-id="044d2-123">The custom telemetry reveals the average time to insert a new row is 32.6 milliseconds.</span></span>

<span data-ttu-id="044d2-124">Application Insights fournit un moyen puissant et pratique de enregistrer la télémétrie détaillée sur vos applications sans serveur.</span><span class="sxs-lookup"><span data-stu-id="044d2-124">Application Insights provides a powerful, convenient way to log detailed telemetry about your serverless applications.</span></span> <span data-ttu-id="044d2-125">Vous avez le plein contrôle sur le niveau de traçage et d’enregistrement qui est fourni.</span><span class="sxs-lookup"><span data-stu-id="044d2-125">You have full control over the level of tracing and logging that is provided.</span></span> <span data-ttu-id="044d2-126">Vous pouvez suivre les statistiques personnalisées telles que les événements, les dépendances et la vue de page.</span><span class="sxs-lookup"><span data-stu-id="044d2-126">You can track custom statistics such as events, dependencies, and page view.</span></span> <span data-ttu-id="044d2-127">Enfin, les analyses puissantes vous permettent d’écrire des requêtes qui posent des questions importantes et génèrent des graphiques et des idées avancées.</span><span class="sxs-lookup"><span data-stu-id="044d2-127">Finally, the powerful analytics enable you to write queries that ask important questions and generate charts and advanced insights.</span></span>

<span data-ttu-id="044d2-128">Pour plus d’informations, consultez [Surveiller l’exécution des fonctions Azure](https://docs.microsoft.com/azure/azure-functions/functions-monitoring).</span><span class="sxs-lookup"><span data-stu-id="044d2-128">For more information, see [Monitor Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-monitoring).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="044d2-129">[Suivant précédent](azure-functions.md)
>[Next](logic-apps.md)</span><span class="sxs-lookup"><span data-stu-id="044d2-129">[Previous](azure-functions.md)
[Next](logic-apps.md)</span></span>
