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
# <a name="tutorial-measure-performance-using-eventcounters-in-net-core"></a>Didacticiel : mesurer les performances à l’aide de EventCounters dans .NET Core

**Cet article s’applique à : ✔️ le kit de** développement logiciel (SDK) .net Core 3,0 et versions ultérieures

Dans ce didacticiel, vous allez apprendre comment <xref:System.Diagnostics.Tracing.EventCounter> utiliser un pour mesurer les performances avec une fréquence élevée d’événements. Vous pouvez utiliser les [compteurs disponibles](available-counters.md) publiés par différents packages .net Core officiels, des fournisseurs tiers ou créer vos propres métriques de surveillance.

Ce didacticiel présente les procédures suivantes :

> [!div class="checklist"]
>
> - Implémentez un <xref:System.Diagnostics.Tracing.EventSource> .
> - Surveiller les compteurs avec [dotnet-Counters](dotnet-counters.md).

## <a name="prerequisites"></a>Conditions préalables requises

Le didacticiel utilise :

- [Kit de développement logiciel (SDK) .net Core 3,1](https://dotnet.microsoft.com/download/dotnet-core) ou version ultérieure.
- [dotnet-compteurs](dotnet-counters.md) pour surveiller les compteurs d’événements.
- Exemple d’application [cible de débogage](/samples/dotnet/samples/diagnostic-scenarios) à diagnostiquer.

## <a name="get-the-source"></a>Récupération de la source

L’exemple d’application sera utilisé comme base pour l’analyse. L' [exemple de référentiel ASP.net Core](/samples/dotnet/samples/diagnostic-scenarios) est disponible dans le navigateur d’exemples. Téléchargez le fichier zip, extrayez-le une fois téléchargé, puis ouvrez-le dans votre IDE favori. Générez et exécutez l’application pour vous assurer qu’elle fonctionne correctement, puis arrêtez l’application.

## <a name="implement-an-eventsource"></a>Implémenter une EventSource

Pour les événements qui se produisent toutes les quelques millisecondes, vous souhaiterez que la surcharge par événement soit faible (moins d’une milliseconde). Dans le cas contraire, l’impact sur les performances sera important. La journalisation d’un événement signifie que vous allez écrire des éléments sur le disque. Si le disque n’est pas assez rapide, vous perdez les événements. Vous avez besoin d’une solution autre que la journalisation de l’événement lui-même.

Lorsque vous traitez un grand nombre d’événements, le fait de connaître la mesure par événement n’est pas non plus utile. La plupart du temps, vous n’avez besoin que de quelques statistiques. Par conséquent, vous pouvez obtenir les statistiques dans le processus lui-même, puis écrire un événement une fois dans un moment pour signaler les statistiques, c’est ce que <xref:System.Diagnostics.Tracing.EventCounter> va faire.

Vous trouverez ci-dessous un exemple de la façon d’implémenter un <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> . Créez un nouveau fichier nommé *MinimalEventCounterSource.cs* et utilisez l’extrait de code comme source :

:::code language="csharp" source="snippets/EventCounters/MinimalEventCounterSource.cs":::

La <xref:System.Diagnostics.Tracing.EventSource.WriteEvent%2A?displayProperty=nameWithType> ligne est la <xref:System.Diagnostics.Tracing.EventSource> partie et ne fait pas partie de <xref:System.Diagnostics.Tracing.EventCounter> , elle a été écrite pour montrer que vous pouvez enregistrer un message avec le compteur d’événements.

## <a name="add-an-action-filter"></a>Ajouter un filtre d’action

L’exemple de code source est un projet ASP.NET Core. Vous pouvez ajouter un [filtre d’action](/aspnet/core/mvc/controllers/filters#action-filters) globalement qui journalise la durée totale de la demande. Créez un nouveau fichier nommé *LogRequestTimeFilterAttribute.cs* et utilisez le code suivant :

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

Le filtre d’action démarre un <xref:System.Diagnostics.Stopwatch> lorsque la requête commence et s’arrête une fois qu’elle est terminée, en capturant le temps écoulé. Le nombre total de millisecondes est enregistré dans l' `MinimalEventCounterSource` instance singleton. Pour appliquer ce filtre, vous devez l’ajouter à la collection de filtres. Dans le fichier *Startup.cs* , mettez à jour la `ConfigureServices` méthode dans inclure ce filtre.

```csharp
public void ConfigureServices(IServiceCollection services) =>
    services.AddControllers(options => options.Filters.Add<LogRequestTimeFilterAttribute>())
            .AddNewtonsoftJson();
```

## <a name="monitor-event-counter"></a>Analyser le compteur d’événements

Avec l’implémentation sur un <xref:System.Diagnostics.Tracing.EventSource> et le filtre d’action personnalisé, générez et lancez l’application.
Vous avez enregistré la mesure dans le <xref:System.Diagnostics.Tracing.EventCounter> , mais à moins que vous n’ayez accès aux statistiques de celle-ci, il n’est pas utile. Pour obtenir les statistiques, vous devez activer le <xref:System.Diagnostics.Tracing.EventCounter> en créant un minuteur qui se déclenche aussi souvent que vous le souhaitez pour les événements, ainsi qu’un écouteur pour capturer les événements. Pour ce faire, vous pouvez utiliser [dotnet-Counters](dotnet-counters.md).

Utilisez la commande [dotnet-Counters PS](dotnet-counters.md#dotnet-counters-ps) pour afficher la liste des processus .net qui peuvent être analysés.

```console
dotnet-counters ps
```

À l’aide de l’identificateur de processus à partir de la sortie de la `dotnet-counters ps` commande, vous pouvez commencer à surveiller le compteur d’événements avec la `dotnet-counters monitor` commande suivante :

```console
dotnet-counters monitor --process-id 2196 --counters Sample.EventCounter.Minimal,Microsoft.AspNetCore.Hosting[total-requests,requests-per-second],System.Runtime[cpu-usage]
```

Pendant l' `dotnet-counters monitor` exécution de la commande, maintenez la touche <kbd>F5</kbd> sur le navigateur pour commencer à émettre des demandes continues au `https://localhost:5001/api/values` point de terminaison. Après quelques secondes, arrêtez en appuyant sur <kbd>q</kbd>

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

La `dotnet-counters monitor` commande est très utile pour la surveillance active. Toutefois, vous souhaiterez peut-être collecter ces métriques de diagnostic pour le traitement et l’analyse. Pour ce faire, utilisez la `dotnet-counters collect` commande. La `collect` commande Switch est semblable à la `monitor` commande, mais accepte quelques paramètres supplémentaires. Vous pouvez spécifier le nom et le format de fichier de sortie souhaités. Pour un fichier JSON nommé *diagnostics.jssur* , utilisez la commande suivante :

```console
dotnet-counters collect --process-id 2196 --format json -o diagnostics.json --counters Sample.EventCounter.Minimal,Microsoft.AspNetCore.Hosting[total-requests,requests-per-second],System.Runtime[cpu-usage]
```

Là encore, pendant l’exécution de la commande, maintenez la touche <kbd>F5</kbd> sur le navigateur pour commencer à émettre des demandes continues au `https://localhost:5001/api/values` point de terminaison. Après quelques secondes, arrêtez en appuyant sur <kbd>q</kbd>. L' *diagnostics.jssur* le fichier est écrit. Toutefois, le fichier JSON écrit n’est pas mis en retrait. pour une meilleure lisibilité, elle est mise en retrait ici.

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

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [EventCounters](event-counters.md)
