---
title: Mesurer les performances à l’aide de EventCounters dans .NET Core
description: Dans ce didacticiel, vous allez apprendre à mesurer les performances à l’aide de EventCounters.
ms.date: 08/07/2020
ms.topic: tutorial
ms.openlocfilehash: 2ed7f234b685dab91ab275105d26b474e3bd1a87
ms.sourcegitcommit: 3d6d6595a03915f617349781f455f838a44b0f44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/19/2020
ms.locfileid: "97700741"
---
# <a name="tutorial-measure-performance-using-eventcounters-in-net-core"></a><span data-ttu-id="5ffbd-103">Didacticiel : mesurer les performances à l’aide de EventCounters dans .NET Core</span><span class="sxs-lookup"><span data-stu-id="5ffbd-103">Tutorial: Measure performance using EventCounters in .NET Core</span></span>

<span data-ttu-id="5ffbd-104">**Cet article s’applique à : ✔️ le kit de** développement logiciel (SDK) .net Core 3,0 et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="5ffbd-104">**This article applies to: ✔️** .NET Core 3.0 SDK and later versions</span></span>

<span data-ttu-id="5ffbd-105">Dans ce didacticiel, vous allez apprendre comment <xref:System.Diagnostics.Tracing.EventCounter> utiliser un pour mesurer les performances avec une fréquence élevée d’événements.</span><span class="sxs-lookup"><span data-stu-id="5ffbd-105">In this tutorial, you'll learn how an <xref:System.Diagnostics.Tracing.EventCounter> can be used to measure performance with a high frequency of events.</span></span> <span data-ttu-id="5ffbd-106">Vous pouvez utiliser les [compteurs disponibles](available-counters.md) publiés par différents packages .net Core officiels, des fournisseurs tiers ou créer vos propres métriques de surveillance.</span><span class="sxs-lookup"><span data-stu-id="5ffbd-106">You can use the [available counters](available-counters.md) published by various official .NET Core packages, third-party providers, or create your own metrics for monitoring.</span></span>

<span data-ttu-id="5ffbd-107">Ce didacticiel présente les procédures suivantes :</span><span class="sxs-lookup"><span data-stu-id="5ffbd-107">In this tutorial, you will:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="5ffbd-108">Implémentez un <xref:System.Diagnostics.Tracing.EventSource> .</span><span class="sxs-lookup"><span data-stu-id="5ffbd-108">Implement an <xref:System.Diagnostics.Tracing.EventSource>.</span></span>
> - <span data-ttu-id="5ffbd-109">Surveiller les compteurs avec [dotnet-Counters](dotnet-counters.md).</span><span class="sxs-lookup"><span data-stu-id="5ffbd-109">Monitor counters with [dotnet-counters](dotnet-counters.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="5ffbd-110">Conditions préalables requises</span><span class="sxs-lookup"><span data-stu-id="5ffbd-110">Prerequisites</span></span>

<span data-ttu-id="5ffbd-111">Le didacticiel utilise :</span><span class="sxs-lookup"><span data-stu-id="5ffbd-111">The tutorial uses:</span></span>

- <span data-ttu-id="5ffbd-112">[Kit de développement logiciel (SDK) .net Core 3,1](https://dotnet.microsoft.com/download/dotnet-core) ou version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="5ffbd-112">[.NET Core 3.1 SDK](https://dotnet.microsoft.com/download/dotnet-core) or a later version.</span></span>
- <span data-ttu-id="5ffbd-113">[dotnet-compteurs](dotnet-counters.md) pour surveiller les compteurs d’événements.</span><span class="sxs-lookup"><span data-stu-id="5ffbd-113">[dotnet-counters](dotnet-counters.md) to monitor event counters.</span></span>
- <span data-ttu-id="5ffbd-114">Exemple d’application [cible de débogage](/samples/dotnet/samples/diagnostic-scenarios) à diagnostiquer.</span><span class="sxs-lookup"><span data-stu-id="5ffbd-114">A [sample debug target](/samples/dotnet/samples/diagnostic-scenarios) app to diagnose.</span></span>

## <a name="get-the-source"></a><span data-ttu-id="5ffbd-115">Récupération de la source</span><span class="sxs-lookup"><span data-stu-id="5ffbd-115">Get the source</span></span>

<span data-ttu-id="5ffbd-116">L’exemple d’application sera utilisé comme base pour l’analyse.</span><span class="sxs-lookup"><span data-stu-id="5ffbd-116">The sample application will be used as a basis for monitoring.</span></span> <span data-ttu-id="5ffbd-117">L' [exemple de référentiel ASP.net Core](/samples/dotnet/samples/diagnostic-scenarios) est disponible dans le navigateur d’exemples.</span><span class="sxs-lookup"><span data-stu-id="5ffbd-117">The [sample ASP.NET Core repository](/samples/dotnet/samples/diagnostic-scenarios) is available from the samples browser.</span></span> <span data-ttu-id="5ffbd-118">Téléchargez le fichier zip, extrayez-le une fois téléchargé, puis ouvrez-le dans votre IDE favori.</span><span class="sxs-lookup"><span data-stu-id="5ffbd-118">You download the zip file, extract it once downloaded, and open it in your favorite IDE.</span></span> <span data-ttu-id="5ffbd-119">Générez et exécutez l’application pour vous assurer qu’elle fonctionne correctement, puis arrêtez l’application.</span><span class="sxs-lookup"><span data-stu-id="5ffbd-119">Build and run the application to ensure that it works properly, then stop the application.</span></span>

## <a name="implement-an-eventsource"></a><span data-ttu-id="5ffbd-120">Implémenter une EventSource</span><span class="sxs-lookup"><span data-stu-id="5ffbd-120">Implement an EventSource</span></span>

<span data-ttu-id="5ffbd-121">Pour les événements qui se produisent toutes les quelques millisecondes, vous souhaiterez que la surcharge par événement soit faible (moins d’une milliseconde).</span><span class="sxs-lookup"><span data-stu-id="5ffbd-121">For events that happen every few milliseconds, you'll want the overhead per event to be low (less than a millisecond).</span></span> <span data-ttu-id="5ffbd-122">Dans le cas contraire, l’impact sur les performances sera important.</span><span class="sxs-lookup"><span data-stu-id="5ffbd-122">Otherwise, the impact on performance will be significant.</span></span> <span data-ttu-id="5ffbd-123">La journalisation d’un événement signifie que vous allez écrire des éléments sur le disque.</span><span class="sxs-lookup"><span data-stu-id="5ffbd-123">Logging an event means you're going to write something to disk.</span></span> <span data-ttu-id="5ffbd-124">Si le disque n’est pas assez rapide, vous perdez les événements.</span><span class="sxs-lookup"><span data-stu-id="5ffbd-124">If the disk is not fast enough, you will lose events.</span></span> <span data-ttu-id="5ffbd-125">Vous avez besoin d’une solution autre que la journalisation de l’événement lui-même.</span><span class="sxs-lookup"><span data-stu-id="5ffbd-125">You need a solution other than logging the event itself.</span></span>

<span data-ttu-id="5ffbd-126">Lorsque vous traitez un grand nombre d’événements, le fait de connaître la mesure par événement n’est pas non plus utile.</span><span class="sxs-lookup"><span data-stu-id="5ffbd-126">When dealing with a large number of events, knowing the measure per event is not useful either.</span></span> <span data-ttu-id="5ffbd-127">La plupart du temps, vous n’avez besoin que de quelques statistiques.</span><span class="sxs-lookup"><span data-stu-id="5ffbd-127">Most of the time all you need is just some statistics out of it.</span></span> <span data-ttu-id="5ffbd-128">Par conséquent, vous pouvez obtenir les statistiques dans le processus lui-même, puis écrire un événement une fois dans un moment pour signaler les statistiques, c’est ce que <xref:System.Diagnostics.Tracing.EventCounter> va faire.</span><span class="sxs-lookup"><span data-stu-id="5ffbd-128">So you could get the statistics within the process itself and then write an event once in a while to report the statistics, that's what <xref:System.Diagnostics.Tracing.EventCounter> will do.</span></span>

<span data-ttu-id="5ffbd-129">Vous trouverez ci-dessous un exemple de la façon d’implémenter un <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> .</span><span class="sxs-lookup"><span data-stu-id="5ffbd-129">Below is an example of how to implement an <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName>.</span></span> <span data-ttu-id="5ffbd-130">Créez un nouveau fichier nommé *MinimalEventCounterSource.cs* et utilisez l’extrait de code comme source :</span><span class="sxs-lookup"><span data-stu-id="5ffbd-130">Create a new file named *MinimalEventCounterSource.cs* and use the code snippet as its source:</span></span>

:::code language="csharp" source="snippets/EventCounters/MinimalEventCounterSource.cs":::

<span data-ttu-id="5ffbd-131">La <xref:System.Diagnostics.Tracing.EventSource.WriteEvent%2A?displayProperty=nameWithType> ligne est la <xref:System.Diagnostics.Tracing.EventSource> partie et ne fait pas partie de <xref:System.Diagnostics.Tracing.EventCounter> , elle a été écrite pour montrer que vous pouvez enregistrer un message avec le compteur d’événements.</span><span class="sxs-lookup"><span data-stu-id="5ffbd-131">The <xref:System.Diagnostics.Tracing.EventSource.WriteEvent%2A?displayProperty=nameWithType> line is the <xref:System.Diagnostics.Tracing.EventSource> part and is not part of <xref:System.Diagnostics.Tracing.EventCounter>, it was written to show that you can log a message together with the event counter.</span></span>

## <a name="add-an-action-filter"></a><span data-ttu-id="5ffbd-132">Ajouter un filtre d’action</span><span class="sxs-lookup"><span data-stu-id="5ffbd-132">Add an action filter</span></span>

<span data-ttu-id="5ffbd-133">L’exemple de code source est un projet ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="5ffbd-133">The sample source code is an ASP.NET Core project.</span></span> <span data-ttu-id="5ffbd-134">Vous pouvez ajouter un [filtre d’action](/aspnet/core/mvc/controllers/filters#action-filters) globalement qui journalise la durée totale de la demande.</span><span class="sxs-lookup"><span data-stu-id="5ffbd-134">You can add an [action filter](/aspnet/core/mvc/controllers/filters#action-filters) globally that will log the total request time.</span></span> <span data-ttu-id="5ffbd-135">Créez un nouveau fichier nommé *LogRequestTimeFilterAttribute.cs* et utilisez le code suivant :</span><span class="sxs-lookup"><span data-stu-id="5ffbd-135">Create a new file named *LogRequestTimeFilterAttribute.cs*, and use the following code:</span></span>

```csharp
using System.Diagnostics;
using Microsoft.AspNetCore.Http.Extensions;
using Microsoft.AspNetCore.Mvc.Filters;

namespace DiagnosticScenarios
{
    public class LogRequestTimeFilterAttribute : ActionFilterAttribute
    {
        readonly Stopwatch _stopwatch = new Stopwatch();

        public override void OnActionExecuting(ActionExecutingContext context) => _stopwatch.Start();

        public override void OnActionExecuted(ActionExecutedContext context)
        {
            _stopwatch.Stop();

            MinimalEventCounterSource.Log.Request(
                context.HttpContext.Request.GetDisplayUrl(), _stopwatch.ElapsedMilliseconds);
        }
    }
}
```

<span data-ttu-id="5ffbd-136">Le filtre d’action démarre un <xref:System.Diagnostics.Stopwatch> lorsque la requête commence et s’arrête une fois qu’elle est terminée, en capturant le temps écoulé.</span><span class="sxs-lookup"><span data-stu-id="5ffbd-136">The action filter starts a <xref:System.Diagnostics.Stopwatch> as the request begins, and stops after it has completed, capturing the elapsed time.</span></span> <span data-ttu-id="5ffbd-137">Le nombre total de millisecondes est enregistré dans l' `MinimalEventCounterSource` instance singleton.</span><span class="sxs-lookup"><span data-stu-id="5ffbd-137">The total milliseconds is logged to the `MinimalEventCounterSource` singleton instance.</span></span> <span data-ttu-id="5ffbd-138">Pour appliquer ce filtre, vous devez l’ajouter à la collection de filtres.</span><span class="sxs-lookup"><span data-stu-id="5ffbd-138">In order for this filter to be applied, you need to add it to the filters collection.</span></span> <span data-ttu-id="5ffbd-139">Dans le fichier *Startup.cs* , mettez à jour la `ConfigureServices` méthode dans inclure ce filtre.</span><span class="sxs-lookup"><span data-stu-id="5ffbd-139">In the *Startup.cs* file, update the `ConfigureServices` method in include this filter.</span></span>

```csharp
public void ConfigureServices(IServiceCollection services) =>
    services.AddControllers(options => options.Filters.Add<LogRequestTimeFilterAttribute>())
            .AddNewtonsoftJson();
```

## <a name="monitor-event-counter"></a><span data-ttu-id="5ffbd-140">Analyser le compteur d’événements</span><span class="sxs-lookup"><span data-stu-id="5ffbd-140">Monitor event counter</span></span>

<span data-ttu-id="5ffbd-141">Avec l’implémentation sur un <xref:System.Diagnostics.Tracing.EventSource> et le filtre d’action personnalisé, générez et lancez l’application.</span><span class="sxs-lookup"><span data-stu-id="5ffbd-141">With the implementation on an <xref:System.Diagnostics.Tracing.EventSource> and the custom action filter, build and launch the application.</span></span>
<span data-ttu-id="5ffbd-142">Vous avez enregistré la mesure dans le <xref:System.Diagnostics.Tracing.EventCounter> , mais à moins que vous n’ayez accès aux statistiques de celle-ci, il n’est pas utile.</span><span class="sxs-lookup"><span data-stu-id="5ffbd-142">You logged the metric to the <xref:System.Diagnostics.Tracing.EventCounter>, but unless you access the statistics from of it, it is not useful.</span></span> <span data-ttu-id="5ffbd-143">Pour obtenir les statistiques, vous devez activer le <xref:System.Diagnostics.Tracing.EventCounter> en créant un minuteur qui se déclenche aussi souvent que vous le souhaitez pour les événements, ainsi qu’un écouteur pour capturer les événements.</span><span class="sxs-lookup"><span data-stu-id="5ffbd-143">To get the statistics, you need to enable the <xref:System.Diagnostics.Tracing.EventCounter> by creating a timer that fires as frequently as you want the events, as well as a listener to capture the events.</span></span> <span data-ttu-id="5ffbd-144">Pour ce faire, vous pouvez utiliser [dotnet-Counters](dotnet-counters.md).</span><span class="sxs-lookup"><span data-stu-id="5ffbd-144">To do that, you can use [dotnet-counters](dotnet-counters.md).</span></span>

<span data-ttu-id="5ffbd-145">Utilisez la commande [dotnet-Counters PS](dotnet-counters.md#dotnet-counters-ps) pour afficher la liste des processus .net qui peuvent être analysés.</span><span class="sxs-lookup"><span data-stu-id="5ffbd-145">Use the [dotnet-counters ps](dotnet-counters.md#dotnet-counters-ps) command to display a list of .NET processes that can be monitored.</span></span>

```console
dotnet-counters ps
```

<span data-ttu-id="5ffbd-146">À l’aide de l’identificateur de processus à partir de la sortie de la `dotnet-counters ps` commande, vous pouvez commencer à surveiller le compteur d’événements avec la `dotnet-counters monitor` commande suivante :</span><span class="sxs-lookup"><span data-stu-id="5ffbd-146">Using the process identifier from the output of the `dotnet-counters ps` command, you can start monitoring the event counter with the following `dotnet-counters monitor` command:</span></span>

```console
dotnet-counters monitor --process-id 2196 --counters Sample.EventCounter.Minimal,Microsoft.AspNetCore.Hosting[total-requests,requests-per-second],System.Runtime[cpu-usage]
```

<span data-ttu-id="5ffbd-147">Pendant l' `dotnet-counters monitor` exécution de la commande, maintenez la touche <kbd>F5</kbd> sur le navigateur pour commencer à émettre des demandes continues au `https://localhost:5001/api/values` point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="5ffbd-147">While the `dotnet-counters monitor` command is running, hold <kbd>F5</kbd> on the browser to start issuing continuous requests to the `https://localhost:5001/api/values` endpoint.</span></span> <span data-ttu-id="5ffbd-148">Après quelques secondes, arrêtez en appuyant sur <kbd>q</kbd></span><span class="sxs-lookup"><span data-stu-id="5ffbd-148">After a few seconds stop by pressing <kbd>q</kbd></span></span>

```console
Press p to pause, r to resume, q to quit.
    Status: Running

[Microsoft.AspNetCore.Hosting]
    Request Rate / 1 sec                               9
    Total Requests                                   134
[System.Runtime]
    CPU Usage (%)                                     13
[Sample.EventCounter.Minimal]
    Request Processing Time (ms)                      34.5
```

<span data-ttu-id="5ffbd-149">La `dotnet-counters monitor` commande est très utile pour la surveillance active.</span><span class="sxs-lookup"><span data-stu-id="5ffbd-149">The `dotnet-counters monitor` command is great for active monitoring.</span></span> <span data-ttu-id="5ffbd-150">Toutefois, vous souhaiterez peut-être collecter ces métriques de diagnostic pour le traitement et l’analyse.</span><span class="sxs-lookup"><span data-stu-id="5ffbd-150">However, you may want to collect these diagnostic metrics for post processing and analysis.</span></span> <span data-ttu-id="5ffbd-151">Pour ce faire, utilisez la `dotnet-counters collect` commande.</span><span class="sxs-lookup"><span data-stu-id="5ffbd-151">For that, use the `dotnet-counters collect` command.</span></span> <span data-ttu-id="5ffbd-152">La `collect` commande Switch est semblable à la `monitor` commande, mais accepte quelques paramètres supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="5ffbd-152">The `collect` switch command is similar to the `monitor` command, but accepts a few additional parameters.</span></span> <span data-ttu-id="5ffbd-153">Vous pouvez spécifier le nom et le format de fichier de sortie souhaités.</span><span class="sxs-lookup"><span data-stu-id="5ffbd-153">You can specify the desired output file name and format.</span></span> <span data-ttu-id="5ffbd-154">Pour un fichier JSON nommé *diagnostics.jssur* , utilisez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="5ffbd-154">For a JSON file named *diagnostics.json* use the following command:</span></span>

```console
dotnet-counters collect --process-id 2196 --format json -o diagnostics.json --counters Sample.EventCounter.Minimal,Microsoft.AspNetCore.Hosting[total-requests,requests-per-second],System.Runtime[cpu-usage]
```

<span data-ttu-id="5ffbd-155">Là encore, pendant l’exécution de la commande, maintenez la touche <kbd>F5</kbd> sur le navigateur pour commencer à émettre des demandes continues au `https://localhost:5001/api/values` point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="5ffbd-155">Again, while the command is running, hold <kbd>F5</kbd> on the browser to start issuing continuous requests to the `https://localhost:5001/api/values` endpoint.</span></span> <span data-ttu-id="5ffbd-156">Après quelques secondes, arrêtez en appuyant sur <kbd>q</kbd>.</span><span class="sxs-lookup"><span data-stu-id="5ffbd-156">After a few seconds stop by pressing <kbd>q</kbd>.</span></span> <span data-ttu-id="5ffbd-157">L' *diagnostics.jssur* le fichier est écrit.</span><span class="sxs-lookup"><span data-stu-id="5ffbd-157">The *diagnostics.json* file is written.</span></span> <span data-ttu-id="5ffbd-158">Toutefois, le fichier JSON écrit n’est pas mis en retrait. pour une meilleure lisibilité, elle est mise en retrait ici.</span><span class="sxs-lookup"><span data-stu-id="5ffbd-158">The JSON file that is written is not indented, however; for readability it is indented here.</span></span>

```json
{
  "TargetProcess": "DiagnosticScenarios",
  "StartTime": "8/5/2020 3:02:45 PM",
  "Events": [
    {
      "timestamp": "2020-08-05 15:02:47Z",
      "provider": "System.Runtime",
      "name": "CPU Usage (%)",
      "counterType": "Metric",
      "value": 0
    },
    {
      "timestamp": "2020-08-05 15:02:47Z",
      "provider": "Microsoft.AspNetCore.Hosting",
      "name": "Request Rate / 1 sec",
      "counterType": "Rate",
      "value": 0
    },
    {
      "timestamp": "2020-08-05 15:02:47Z",
      "provider": "Microsoft.AspNetCore.Hosting",
      "name": "Total Requests",
      "counterType": "Metric",
      "value": 134
    },
    {
      "timestamp": "2020-08-05 15:02:47Z",
      "provider": "Sample.EventCounter.Minimal",
      "name": "Request Processing Time (ms)",
      "counterType": "Metric",
      "value": 0
    },
    {
      "timestamp": "2020-08-05 15:02:47Z",
      "provider": "System.Runtime",
      "name": "CPU Usage (%)",
      "counterType": "Metric",
      "value": 0
    },
    {
      "timestamp": "2020-08-05 15:02:48Z",
      "provider": "Microsoft.AspNetCore.Hosting",
      "name": "Request Rate / 1 sec",
      "counterType": "Rate",
      "value": 0
    },
    {
      "timestamp": "2020-08-05 15:02:48Z",
      "provider": "Microsoft.AspNetCore.Hosting",
      "name": "Total Requests",
      "counterType": "Metric",
      "value": 134
    },
    {
      "timestamp": "2020-08-05 15:02:48Z",
      "provider": "Sample.EventCounter.Minimal",
      "name": "Request Processing Time (ms)",
      "counterType": "Metric",
      "value": 0
    },
    {
      "timestamp": "2020-08-05 15:02:48Z",
      "provider": "System.Runtime",
      "name": "CPU Usage (%)",
      "counterType": "Metric",
      "value": 0
    },
    {
      "timestamp": "2020-08-05 15:02:50Z",
      "provider": "Microsoft.AspNetCore.Hosting",
      "name": "Request Rate / 1 sec",
      "counterType": "Rate",
      "value": 0
    },
    {
      "timestamp": "2020-08-05 15:02:50Z",
      "provider": "Microsoft.AspNetCore.Hosting",
      "name": "Total Requests",
      "counterType": "Metric",
      "value": 134
    },
    {
      "timestamp": "2020-08-05 15:02:50Z",
      "provider": "Sample.EventCounter.Minimal",
      "name": "Request Processing Time (ms)",
      "counterType": "Metric",
      "value": 0
    }
  ]
}
```

## <a name="next-steps"></a><span data-ttu-id="5ffbd-159">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="5ffbd-159">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="5ffbd-160">EventCounters</span><span class="sxs-lookup"><span data-stu-id="5ffbd-160">EventCounters</span></span>](event-counters.md)
