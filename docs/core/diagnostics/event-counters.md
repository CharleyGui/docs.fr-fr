---
title: EventCounters dans .NET Core
description: Dans cet article, vous allez découvrir les EventCounters, comment les implémenter et comment les utiliser.
ms.date: 08/07/2020
ms.openlocfilehash: 843f1ec645bf7f52fd4f85e30d183e6e21fee5c6
ms.sourcegitcommit: 78eb25647b0c750cd80354ebd6ce83a60668e22c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2021
ms.locfileid: "99065062"
---
# <a name="eventcounters-in-net-core"></a>EventCounters dans .NET Core

**Cet article s’applique à : ✔️ le kit de** développement logiciel (SDK) .net Core 3,0 et versions ultérieures

EventCounters sont des API .NET Core utilisées pour la collecte des métriques de performances légère, multiplateforme et quasiment en temps réel. Les EventCounters ont été ajoutés comme une alternative multiplateforme aux « compteurs de performances » de l' .NET Framework sur Windows. Dans cet article, vous allez découvrir les EventCounters, comment les implémenter et comment les utiliser.

Le Runtime .NET Core et quelques bibliothèques .NET publient des informations de diagnostic de base à l’aide de EventCounters à partir de .NET Core 3,0. Outre les EventCounters fournies par le Runtime .NET, vous pouvez choisir d’implémenter votre propre EventCounters. EventCounters peut être utilisé pour effectuer le suivi de diverses mesures. En savoir plus à leur sujet dans le [EventCounters connu dans .net](available-counters.md)

EventCounters en direct dans le cadre d’un <xref:System.Diagnostics.Tracing.EventSource> objet et sont automatiquement poussés vers les outils d’écouteur régulièrement. Comme tous les autres événements sur un <xref:System.Diagnostics.Tracing.EventSource> , ils peuvent être utilisés à la fois en-proc et hors processus via <xref:System.Diagnostics.Tracing.EventListener> et [EventPipe](./eventpipe.md). Cet article se concentre sur les fonctionnalités inter-plateformes de EventCounters et exclut intentionnellement PerfView et ETW (Suivi d’v nements pour Windows), bien que les deux puissent être utilisés avec EventCounters.

![Image de diagramme in-proc et out-of-proc EventCounters](media/event-counters.svg)

## <a name="eventcounter-api-overview"></a>Vue d’ensemble de l’API EventCounter

Il existe deux catégories principales de compteurs. Certains compteurs correspondent aux valeurs « rate », telles que le nombre total d’exceptions, le nombre total de catalogues globaux et le nombre total de demandes. D’autres compteurs sont des valeurs « instantané », telles que l’utilisation du tas, l’utilisation du processeur et la taille de la plage de travail. Dans chacune de ces catégories de compteurs, il existe deux types de compteurs qui varient en fonction de la façon dont ils obtiennent leur valeur. Les compteurs d’interrogation récupèrent leur valeur via un rappel, et les compteurs sans interrogation ont leurs valeurs directement définies sur l’instance de compteur.

Les compteurs sont représentés par les implémentations suivantes :

* <xref:System.Diagnostics.Tracing.EventCounter>
* <xref:System.Diagnostics.Tracing.IncrementingEventCounter>
* <xref:System.Diagnostics.Tracing.IncrementingPollingCounter>
* <xref:System.Diagnostics.Tracing.PollingCounter>

Un écouteur d’événements spécifie la durée des intervalles de mesure. À la fin de chaque intervalle, une valeur est transmise à l’écouteur pour chaque compteur. Les implémentations d’un compteur déterminent les API et les calculs utilisés pour produire la valeur chaque intervalle.

1. <xref:System.Diagnostics.Tracing.EventCounter>Enregistre un ensemble de valeurs. La <xref:System.Diagnostics.Tracing.EventCounter.WriteMetric%2A?displayProperty=nameWithType> méthode ajoute une nouvelle valeur à l’ensemble. À chaque intervalle, un résumé statistique pour l’ensemble est calculé, par exemple, min, Max et Mean. L’outil [dotnet-Counters](dotnet-counters.md) affiche toujours la valeur moyenne. <xref:System.Diagnostics.Tracing.EventCounter>Est utile pour décrire un ensemble discret d’opérations. L’utilisation courante peut inclure la surveillance de la taille moyenne en octets d’opérations d’e/s récentes ou la valeur monétaire moyenne d’un ensemble de transactions financières.

1. <xref:System.Diagnostics.Tracing.IncrementingEventCounter>Enregistre un total cumulé pour chaque intervalle de temps. La <xref:System.Diagnostics.Tracing.IncrementingEventCounter.Increment%2A?displayProperty=nameWithType> méthode ajoute au total. Par exemple, si `Increment()` est appelé trois fois dans un intervalle avec des valeurs `1` , `2` et, `5` le total cumulé de `8` est signalé comme valeur de compteur pour cet intervalle. L’outil [dotnet-Counters](dotnet-counters.md) affiche le taux en tant que total/heure enregistré. <xref:System.Diagnostics.Tracing.IncrementingEventCounter>Est utile pour mesurer la fréquence d’exécution d’une action, comme le nombre de demandes traitées par seconde.

1. <xref:System.Diagnostics.Tracing.PollingCounter>Utilise un rappel pour déterminer la valeur qui est signalée. Avec chaque intervalle de temps, la fonction de rappel fournie par l’utilisateur est appelée et la valeur de retour est utilisée comme valeur de compteur. Un <xref:System.Diagnostics.Tracing.PollingCounter> peut être utilisé pour interroger une mesure à partir d’une source externe, par exemple pour obtenir les octets libres actuels sur un disque. Il peut également être utilisé pour signaler des statistiques personnalisées qui peuvent être calculées à la demande par une application. Les exemples incluent la création de rapports sur le 95e centile des latences de demandes récentes ou le taux d’accès actuel ou d’échec d’un cache.

1. <xref:System.Diagnostics.Tracing.IncrementingPollingCounter>Utilise un rappel pour déterminer la valeur d’incrément signalée. Avec chaque intervalle de temps, le rappel est appelé, puis la différence entre l’appel en cours et le dernier appel est la valeur signalée. L’outil [dotnet-Counters](dotnet-counters.md) affiche toujours la différence comme une vitesse, la valeur/l’heure indiquée. Ce compteur est utile lorsqu’il n’est pas possible d’appeler une API sur chaque occurrence, mais qu’il est possible d’interroger le nombre total d’occurrences. Par exemple, vous pouvez signaler le nombre d’octets écrits dans un fichier par seconde, même sans notification chaque fois qu’un octet est écrit.

## <a name="implement-an-eventsource"></a>Implémenter une EventSource

Le code suivant implémente un exemple <xref:System.Diagnostics.Tracing.EventSource> exposé comme fournisseur nommé `"Sample.EventCounter.Minimal"` . Cette source contient une <xref:System.Diagnostics.Tracing.EventCounter> durée de traitement de la demande de représentation. Ce compteur a un nom (autrement dit, son ID unique dans la source) et un nom d’affichage, tous deux utilisés par des outils d’écouteur tels que [dotnet-Counter](dotnet-counters.md).

:::code language="csharp" source="snippets/EventCounters/MinimalEventCounterSource.cs":::

Vous utilisez `dotnet-counters ps` pour afficher une liste de processus .net qui peuvent être analysés :

```console
dotnet-counters ps
   1398652 dotnet     C:\Program Files\dotnet\dotnet.exe
   1399072 dotnet     C:\Program Files\dotnet\dotnet.exe
   1399112 dotnet     C:\Program Files\dotnet\dotnet.exe
   1401880 dotnet     C:\Program Files\dotnet\dotnet.exe
   1400180 sample-counters C:\sample-counters\bin\Debug\netcoreapp3.1\sample-counters.exe
```

Transmettez le <xref:System.Diagnostics.Tracing.EventSource> nom à l' `--counters` option pour démarrer l’analyse de votre compteur :

```console
dotnet-counters monitor --process-id 1400180 --counters Sample.EventCounter.Minimal
```

L’exemple suivant illustre la sortie de l’analyse :

```console
Press p to pause, r to resume, q to quit.
    Status: Running

[Samples-EventCounterDemos-Minimal]
    Request Processing Time (ms)                            0.445
```

Appuyez sur <kbd>q</kbd> pour arrêter la commande d’analyse.

#### <a name="conditional-counters"></a>Compteurs conditionnels

Lors de l’implémentation d’un <xref:System.Diagnostics.Tracing.EventSource> , les compteurs conteneur peuvent être instanciés de manière conditionnelle lorsque la <xref:System.Diagnostics.Tracing.EventSource.OnEventCommand%2A?displayProperty=nameWithType> méthode est appelée avec une <xref:System.Diagnostics.Tracing.EventCommandEventArgs.Command> valeur `EventCommand.Enable` . Pour instancier en toute sécurité une instance de compteur uniquement si c’est `null` le cas, utilisez l' [opérateur d’assignation de fusion Null](../../csharp/language-reference/operators/null-coalescing-operator.md). En outre, les méthodes personnalisées peuvent évaluer la <xref:System.Diagnostics.DiagnosticSource.IsEnabled%2A> méthode pour déterminer si la source d’événements actuelle est activée ou non.

:::code language="csharp" source="snippets/EventCounters/ConditionalEventCounterSource.cs":::

> [!TIP]
> Les compteurs conditionnels sont des compteurs qui sont instanciés de manière conditionnelle, une micro-optimisation. Le runtime adopte ce modèle pour les scénarios où les compteurs ne sont normalement pas utilisés, pour économiser une fraction d’une milliseconde.

### <a name="net-core-runtime-example-counters"></a>Exemples de compteurs du Runtime .NET Core

Le Runtime .NET Core contient de nombreux exemples d’implémentations excellents. Voici l’implémentation du runtime pour le compteur qui effectue le suivi de la taille de la plage de travail de l’application.

```csharp
var workingSetCounter = new PollingCounter(
    "working-set",
    this,
    () => (double)(Environment.WorkingSet / 1_000_000))
{
    DisplayName = "Working Set",
    DisplayUnits = "MB"
};
```

Le <xref:System.Diagnostics.Tracing.PollingCounter> signale la quantité actuelle de mémoire physique mappée au processus (plage de travail) de l’application, car elle capture une mesure à un moment donné. Le rappel d’interrogation d’une valeur est l’expression lambda fournie, qui est simplement un appel à l' <xref:System.Environment.WorkingSet?displayProperty=fullName> API. <xref:System.Diagnostics.Tracing.DiagnosticCounter.DisplayName> et <xref:System.Diagnostics.Tracing.DiagnosticCounter.DisplayUnits> sont des propriétés facultatives qui peuvent être définies pour aider le côté client du compteur à afficher la valeur plus clairement. Par exemple, [dotnet-Counters](dotnet-counters.md) utilise ces propriétés pour afficher la version la plus conviviale des noms de compteurs.

> [!IMPORTANT]
> Les `DisplayName` Propriétés ne sont pas localisées.

Pour <xref:System.Diagnostics.Tracing.PollingCounter> , et <xref:System.Diagnostics.Tracing.IncrementingPollingCounter> , rien d’autre ne doit être fait. Ils interrogent les valeurs elles-mêmes à un intervalle demandé par le consommateur.

Voici un exemple de compteur d’exécution implémenté à l’aide de <xref:System.Diagnostics.Tracing.IncrementingPollingCounter> .

```csharp
var monitorContentionCounter = new IncrementingPollingCounter(
    "monitor-lock-contention-count",
    this,
    () => Monitor.LockContentionCount
)
{
    DisplayName = "Monitor Lock Contention Count",
    DisplayRateTimeScale = TimeSpan.FromSeconds(1)
};
```

<xref:System.Diagnostics.Tracing.IncrementingPollingCounter>Utilise l' <xref:System.Threading.Monitor.LockContentionCount?displayProperty=nameWithType> API pour signaler l’incrément du nombre total de conflits de verrouillage. La <xref:System.Diagnostics.Tracing.IncrementingPollingCounter.DisplayRateTimeScale> propriété est facultative, mais quand elle est utilisée, elle peut fournir une indication de l’intervalle de temps le plus approprié pour l’affichage du compteur. Par exemple, le nombre de conflits de verrouillage est mieux affiché en tant que _nombre par seconde_, donc sa <xref:System.Diagnostics.Tracing.IncrementingPollingCounter.DisplayRateTimeScale> valeur est définie sur une seconde. La vitesse d’affichage peut être ajustée pour différents types de compteurs de taux.

> [!NOTE]
> <xref:System.Diagnostics.Tracing.IncrementingPollingCounter.DisplayRateTimeScale>N’est _pas_ utilisé par [dotnet-Counters](dotnet-counters.md), et les écouteurs d’événements ne sont pas tenus de l’utiliser.

Il existe d’autres implémentations de compteur à utiliser comme référence dans le [Runtime .net](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Private.CoreLib/src/System/Diagnostics/Tracing/RuntimeEventSource.cs) référentiel.

## <a name="concurrency"></a>Accès concurrentiel

> [!TIP]
> L’API EventCounters ne garantit pas la sécurité des threads. Lorsque les délégués passés à <xref:System.Diagnostics.Tracing.PollingCounter> <xref:System.Diagnostics.Tracing.IncrementingPollingCounter> des instances ou sont appelés par plusieurs threads, il vous incombe de garantir la sécurité des threads des délégués.

Par exemple, considérez les éléments suivants pour effectuer le <xref:System.Diagnostics.Tracing.EventSource> suivi des demandes.

:::code language="csharp" source="snippets/EventCounters/RequestEventSource.cs":::

La `AddRequest()` méthode peut être appelée à partir d’un gestionnaire de requêtes et le `RequestRateCounter` interroge la valeur à l’intervalle spécifié par le consommateur du compteur. Toutefois, la `AddRequest()` méthode peut être appelée par plusieurs threads à la fois, en plaçant une condition de concurrence sur `_requestCount` . Une autre façon thread-safe d’incrémenter `_requestCount` est d’utiliser <xref:System.Threading.Interlocked.Increment%2A?displayProperty=nameWithType> .

```csharp
public void AddRequest() => Interlocked.Increment(ref _requestCount);
```

Pour éviter les lectures endommagées (sur les architectures 32 bits) de l' `long` utilisation du champ-Field `_requestCount` <xref:System.Threading.Interlocked.Read%2A?displayProperty=nameWithType> .

```csharp
_requestRateCounter = new IncrementingPollingCounter("request-rate", this, () => Interlocked.Read(ref _requestCount))
{
    DisplayName = "Request Rate",
    DisplayRateTimeScale = TimeSpan.FromSeconds(1)
};
```

## <a name="consume-eventcounters"></a>Consommer EventCounters

Il existe deux façons principales de consommer des EventCounters, soit in-proc, soit out-of-process. La consommation de EventCounters peut être distinguée en trois couches de technologies consommatrices différentes.

- Transport d’événements dans un flux brut via ETW ou EventPipe :
  - Les API ETW sont fournies avec le système d’exploitation Windows, et EventPipe sont accessibles en tant qu' [API .net](https://github.com/dotnet/diagnostics/blob/master/documentation/design-docs/diagnostics-client-library.md#1-attaching-to-a-process-and-dumping-out-all-the-runtime-gc-events-in-real-time-to-the-console)ou le [protocole IPC](https://github.com/dotnet/diagnostics/blob/master/documentation/design-docs/ipc-protocol.md)de diagnostic.
- Décodage du flux d’événements binaires en événements :
  - La [bibliothèque TraceEvent](https://www.nuget.org/packages/Microsoft.Diagnostics.Tracing.TraceEvent) gère à la fois les formats de flux ETW et EventPipe.
- Outils de ligne de commande et d’interface utilisateur graphique :
  - Outils tels que PerfView (ETW ou EventPipe), dotnet-Counters (EventPipe uniquement) et DOTNET-Monitor (EventPipe uniquement).

### <a name="consume-out-of-proc"></a>Consommer hors processus

L’utilisation de EventCounters out-of-proc est une approche très courante. Vous pouvez utiliser [dotnet-Counters](dotnet-counters.md) pour les utiliser de manière multiplateforme via un EventPipe. L' `dotnet-counters` outil est un outil global de l’interface CLI dotnet multiplateforme qui peut être utilisé pour analyser les valeurs de compteur. Pour savoir comment utiliser `dotnet-counters` pour surveiller vos compteurs, consultez [dotnet-Counters](dotnet-counters.md), ou utilisez le didacticiel [mesurer les performances à l’aide de EventCounters](event-counter-perf.md) .

#### <a name="dotnet-trace"></a>dotnet-trace

L' `dotnet-trace` outil peut être utilisé pour consommer les données de compteur via un EventPipe. Voici un exemple qui utilise `dotnet-trace` pour collecter des données de compteur.

```console
dotnet-trace collect --process-id <pid> Sample.EventCounter.Minimal:0:0:EventCounterIntervalSec=1
```

Pour plus d’informations sur la collecte des valeurs de compteur au fil du temps, consultez la documentation de [dotnet-trace](dotnet-trace.md#use-dotnet-trace-to-collect-counter-values-over-time) .

#### <a name="azure-application-insights"></a>Azure Application Insights

EventCounters peut être utilisé par Azure Monitor, plus particulièrement Azure Application Insights. Vous pouvez ajouter et supprimer des compteurs, et vous êtes libre de spécifier des compteurs personnalisés ou des compteurs connus. Pour plus d’informations, consultez [Personnalisation des compteurs à collecter](/azure/azure-monitor/app/eventcounters#customizing-counters-to-be-collected).

#### <a name="dotnet-monitor"></a>dotnet-Monitor

L' `dotnet-monitor` outil est un outil expérimental qui facilite l’accès aux informations de diagnostic dans un processus .net. L’outil sert de sur-ensemble de tous les outils de diagnostic. En plus des traces, il peut surveiller les métriques, collecter les vidages de la mémoire et collecter les vidages de la mémoire GC. Elle est distribuée à la fois comme un outil d’interface de commande et une image d’ancrage. Il expose une API REST, et la collection d’artefacts de diagnostic se produit par le biais d’appels REST.

Pour plus d’informations, consultez [Présentation de dotnet-Monitor, outil expérimental](https://devblogs.microsoft.com/dotnet/introducing-dotnet-monitor).

### <a name="consume-in-proc"></a>Utiliser in-proc

Vous pouvez utiliser les valeurs de compteur via l' <xref:System.Diagnostics.Tracing.EventListener> API. Un <xref:System.Diagnostics.Tracing.EventListener> est une méthode in-proc qui consiste à consommer les événements écrits par toutes les instances d’un <xref:System.Diagnostics.Tracing.EventSource> dans votre application. Pour plus d’informations sur l’utilisation de l' `EventListener` API, consultez <xref:System.Diagnostics.Tracing.EventListener> .

Tout d’abord, le <xref:System.Diagnostics.Tracing.EventSource> qui produit la valeur de compteur doit être activé. Substituez la <xref:System.Diagnostics.Tracing.EventListener.OnEventSourceCreated%2A?displayProperty=nameWithType> méthode pour obtenir une notification quand un <xref:System.Diagnostics.Tracing.EventSource> est créé, et si c’est le correct <xref:System.Diagnostics.Tracing.EventSource> avec votre EventCounters, vous pouvez appeler <xref:System.Diagnostics.Tracing.EventListener.EnableEvents%2A?displayProperty=nameWithType> dessus. Voici un exemple de remplacement :

:::code language="csharp" source="snippets/EventCounters/SimpleEventListener.cs" range="11-22":::

#### <a name="sample-code"></a>Exemple de code

Voici un exemple de <xref:System.Diagnostics.Tracing.EventListener> classe qui imprime tous les noms et valeurs de compteur à partir du Runtime .NET <xref:System.Diagnostics.Tracing.EventSource> , pour la publication de ses compteurs internes ( `System.Runtime` ) chaque seconde.

:::code language="csharp" source="snippets/EventCounters/SimpleEventListener.cs":::

Comme indiqué ci-dessus, vous _devez_ vous assurer que l' `"EventCounterIntervalSec"` argument est défini dans l' `filterPayload` argument lors de l’appel de <xref:System.Diagnostics.Tracing.EventListener.EnableEvents%2A> . Dans le cas contraire, les compteurs ne seront pas en mesure de vider les valeurs, car il ne sait pas à quel intervalle il doit être vidé.

## <a name="see-also"></a>Voir aussi

- [dotnet-counters](dotnet-counters.md)
- [dotnet-trace](dotnet-trace.md)
- <xref:System.Diagnostics.Tracing.EventCounter>
- <xref:System.Diagnostics.Tracing.EventListener>
- <xref:System.Diagnostics.Tracing.EventSource>
