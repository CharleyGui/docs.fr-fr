---
title: Gestion des performances des applications-gRPC pour les développeurs WCF
description: La journalisation, les métriques et le suivi pour les applications ASP.NET Core gRPC.
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 6e4c32d057c1ac143e18a4a3ddc83dd8b1f62800
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184609"
---
# <a name="application-performance-management"></a>Gestion des performances des applications

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Dans les environnements de production modernes comme Kubernetes, il est très important de pouvoir surveiller les applications pour s’assurer qu’elles s’exécutent de manière optimale. Les problèmes tels que la journalisation et les métriques n’ont jamais été plus importants. ASP.NET Core, y compris gRPC, offre une prise en charge de première classe pour la production et la gestion des messages de journaux et des données de métriques, ainsi que *le suivi* des données. Cette section aborde ces sujets plus en détail.

## <a name="logging-vs-metrics"></a>Journalisation vs métriques

Avant de consulter les détails de l’implémentation, il est nécessaire de comprendre la différence entre la journalisation et les métriques.

La journalisation s’attache à des messages texte qui enregistrent des informations détaillées sur les événements qui se sont produits dans le système. Les messages de journal peuvent inclure des données d’exception telles que des traces de la pile ou des données structurées qui fournissent le contexte relatif au message. La sortie de journalisation est généralement écrite dans un magasin de texte pouvant faire l’objet d’une recherche.

Les métriques font référence à des données numériques conçues pour être agrégées et présentées à l’aide de graphiques et de graphiques dans un tableau de bord qui fournit une vue de l’intégrité et des performances globales d’une application. Les données de métriques peuvent également être utilisées pour déclencher des alertes automatisées lorsqu’un seuil est dépassé. La liste suivante présente quelques exemples de données de métriques :

- Temps nécessaire pour traiter les demandes.
- Nombre de demandes par seconde traitées par une instance d’un service.
- Nombre de demandes ayant échoué sur une instance.

## <a name="logging-in-aspnet-core-grpc"></a>Connexion ASP.NET Core gRPC

ASP.NET Core fournit une prise en charge intégrée de la journalisation, sous la forme du package NuGet [Microsoft. extensions. Logging](https://www.nuget.org/packages/Microsoft.Extensions.Logging) . Les principales parties de cette bibliothèque sont incluses dans le kit de développement logiciel (SDK) Web. il n’est donc pas nécessaire de l’installer manuellement. Par défaut, les messages de journal sont écrits dans la sortie standard (« console ») et dans tout débogueur attaché. Pour écrire des journaux dans des magasins de données externes persistants, vous devrez peut-être importer des [packages de récepteur de journalisation facultatifs](https://docs.microsoft.com/aspnet/core/fundamentals/logging/?view=aspnetcore-3.0#third-party-logging-providers).

Le ASP.NET Core Framework gRPC écrit des messages de journalisation de diagnostic détaillés dans cette structure de journalisation pour qu’ils puissent être traités/stockés avec les messages de votre application.

### <a name="produce-log-messages"></a>Produire des messages de journal

L’extension de journalisation est automatiquement inscrite auprès du système d’injection de dépendances de ASP.NET Core, ce qui vous permet de spécifier des journaux en tant que paramètre de constructeur sur les types de service gRPC.

```csharp
public class StockData : Stocks.StocksBase
{
    private readonly ILogger<StockData> _logger;

    public StockData(ILogger<StockData> logger)
    {
        _logger = logger;
    }
}
```

De nombreux messages de journal concernant les demandes, les exceptions, etc., sont fournis par les composants de l’infrastructure ASP.NET Core et gRPC. Ajoutez vos propres messages de journalisation pour fournir des détails et du contexte sur la logique d’application plutôt que sur des problèmes de niveau inférieur.

Pour plus d’informations sur l’écriture de messages de journal et sur les récepteurs de journalisation et les cibles disponibles, consultez l’article [journalisation dans .net Core et ASP.net Core](https://docs.microsoft.com/aspnet/core/fundamentals/logging/?view=aspnetcore-3.0) .

## <a name="metrics-in-aspnet-core-grpc"></a>Mesures dans ASP.NET Core gRPC

Le Runtime .net Core fournit un ensemble de composants pour émettre et observer des métriques qui incluent des API telles que <xref:System.Diagnostics.Tracing.EventSource> les <xref:System.Diagnostics.Tracing.EventCounter> classes et. Ces API peuvent être utilisées pour émettre des données numériques de base qui peuvent être consommées par des processus externes tels que l' [outil Global dotnet-Counters](https://github.com/dotnet/diagnostics/blob/master/documentation/dotnet-counters-instructions.md), ou suivi d’v nements pour Windows. Pour plus d’informations sur `EventCounter` l’utilisation de dans votre propre code, consultez le didacticiel de [Présentation de EventCounter](https://github.com/dotnet/corefx/blob/master/src/System.Diagnostics.Tracing/documentation/EventCounterTutorial.md) .

Pour les métriques plus avancées et l’écriture de données de métriques dans un plus grand nombre de magasins de données, il existe un excellent projet open source appelé [métriques](https://www.app-metrics.io)de l’application. Cette suite de bibliothèques fournit un ensemble complet de types pour instrumenter votre code. Il offre également des packages pour écrire des mesures dans différents types de cibles qui incluent des bases de données de série chronologique, telles que Prometheus et InfluxDB, [Azure application Insights](https://docs.microsoft.com/azure/azure-monitor/app/app-insights-overview), et bien plus encore. Le package NuGet [app. Metrics. AspNetCore. Mvc](https://www.nuget.org/packages/App.Metrics.AspNetCore.Mvc/) ajoute même un ensemble complet de métriques de base qui sont générées automatiquement par le biais de l’intégration avec l’infrastructure ASP.net Core, et le site Web fournit des [modèles](https://www.app-metrics.io/samples/grafana/) pour l’affichage de ces métriques. avec la plateforme de visualisation [Grafana](https://grafana.com/) .

Pour plus d’informations et pour obtenir de la documentation sur les métriques d’application, consultez le site Web [app-Metrics.IO](https://app-metrics.io) .

### <a name="produce-metrics"></a>Produire des métriques

La plupart des plateformes de métriques prennent en charge cinq types de métriques de base, décrits dans le tableau suivant :

| Type de métrique | Description |
| ----------- | ----------- |
| Counter     | Effectue le suivi de la fréquence des événements, tels que les demandes, les erreurs, etc. |
| Gabarit       | Enregistre une valeur unique qui change au fil du temps, par exemple des connexions actives. |
| Histogramme   | Mesure une distribution de valeurs à travers des limites arbitraires. Par exemple, un histogramme peut suivre la taille du jeu de données, en comptant le nombre d’enregistrements contenus < 10, le nombre de 11-100 et 101-1000, ainsi que les enregistrements > 1 000. |
| Tswtclmt       | Mesure le taux auquel un événement se produit dans différents intervalles de temps. |
| Minuterie       | Effectue le suivi de la durée des événements et de la vitesse à laquelle ils se produisent, stockés sous la forme d’un histogramme. |

À l’aide des *métriques*de l’application, une `IMetrics` interface peut être obtenue via l’injection de dépendances et utilisée pour enregistrer l’une de ces métriques pour un service gRPC. L’exemple suivant montre comment compter le nombre de `Get` demandes effectuées dans le temps :

```csharp
public class StockData : Stocks.StocksBase
{
    private static readonly CounterOptions GetRequestCounter = new CounterOptions
    {
        Name = "StockData_Get_Requests",
        MeasurementUnit = Unit.Calls
    };

    private readonly IStockRepository _repository;
    private readonly IMetrics _metrics;

    public StockData(IStockRepository repository, IMetrics metrics)
    {
        _repository = repository;
        _metrics = metrics;
    }

    public override async Task<GetResponse> Get(GetRequest request, ServerCallContext context)
    {
        _metrics.Measure.Counter.Increment(GetRequestCounter);

        // Serve request...
    }
}
```

### <a name="store-and-visualize-metrics-data"></a>Stocker et visualiser les données de métriques

La meilleure façon de stocker les données de métriques se trouve dans une *base de données de série chronologique*, une banque de données spécialisée conçue pour enregistrer des séries de données numériques marquées avec des horodateurs. Les bases de données les plus populaires sont [Prometheus](https://prometheus.io/) et [InfluxDB](https://www.influxdata.com/products/influxdb-overview/). Microsoft Azure fournit également un stockage de métriques dédié par le biais du service [Azure Monitor](https://docs.microsoft.com/azure/azure-monitor/overview) .

La solution actuelle de visualisation des données de métriques est [Grafana](https://grafana.com), qui fonctionne avec un large éventail de fournisseurs de stockage, y compris Azure Monitor, InfluxDB et Prometheus. L’image suivante montre un exemple de tableau de bord Grafana qui affiche les métriques de la maille du service Linkerd exécutant l’exemple StockData :

![Tableau de bord Grafana](media/application-performance-management/grafana-screenshot.png)

### <a name="metrics-based-alerting"></a>Alertes basées sur les métriques

La nature numérique des données de métriques signifie qu’elle est idéalement adaptée aux systèmes d’alerte, en avertissant les développeurs ou les ingénieurs du support technique lorsqu’une valeur se situe en dehors d’une tolérance définie. Les plateformes déjà mentionnées prennent en charge l’alerte par le biais d’une gamme d’options, notamment les e-mails, les SMS ou les visualisations dans le tableau de bord.

## <a name="distributed-tracing"></a>Traçage distribué

Le *traçage distribué* est un développement relativement récent dans le monitoring, qui vient de l’utilisation accrue des microservices et des architectures distribuées. Une seule demande provenant d’un navigateur client, d’une application ou d’un appareil peut être divisée en plusieurs étapes et sous-requêtes, et impliquer l’utilisation de nombreux services sur un réseau. Cela complique la mise en corrélation des messages du journal et des métriques avec la demande spécifique qui les a déclenchés. Le traçage distribué applique des identificateurs aux demandes qui autorisent la mise en corrélation des journaux et des métriques avec une opération particulière. Cela est similaire au [suivi de bout en bout de WCF](https://docs.microsoft.com/dotnet/framework/wcf/diagnostics/tracing/end-to-end-tracing), mais appliqué sur plusieurs plateformes.

Bien qu’il s’agisse toujours d’un domaine technologique balbutiante, le suivi distribué a augmenté rapidement en popularité et passe maintenant par un processus de normalisation. La Fondation Cloud Native Computing a créé la [norme Open Tracing](https://opentracing.io), qui tente de fournir des bibliothèques indépendantes du fournisseur pour travailler avec des serveurs principaux tels que [Jaeger](https://www.jaegertracing.io/) et l' [APM élastique](https://www.elastic.co/products/apm). En même temps, Google a créé le [projet OpenCensus](https://opencensus.io/) pour résoudre le même ensemble de problèmes. Ces deux projets sont maintenant fusionnés dans un nouveau projet, [OpenTelemetry](https://opentelemetry.io), qui a pour but d’être la norme du secteur.

### <a name="how-distributed-tracing-works"></a>Fonctionnement du traçage distribué

Le traçage distribué est basé sur le concept d' *étendues*: les opérations chronométrées qui font partie d’une seule *trace*, ce qui peut impliquer le traitement sur plusieurs nœuds d’un système. Lorsqu’une nouvelle opération est lancée, une trace est créée avec un identificateur unique. Pour chaque sous-opération, une étendue est créée avec son propre identificateur et identificateur de suivi. À mesure que la demande passe par le système, plusieurs composants peuvent créer des étendues *enfants* incluant l’identificateur de leur *parent*. Une étendue a un *contexte*, qui contient les identificateurs de trace et d’étendue, ainsi que des données utiles sous la forme de paires clé/valeur (appelées *bagages*).

### <a name="distributed-tracing-with-diagnosticsource"></a>Traçage distribué avec DiagnosticSource

.NET Core possède un module interne qui s’adapte bien aux traces et aux étendues distribuées : [DiagnosticSource](https://github.com/dotnet/corefx/blob/master/src/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md#diagnosticsource-users-guide). En plus de fournir un moyen simple de produire et de consommer les Diagnostics au sein d' `DiagnosticSource` un processus, le module a le concept d’une *activité*, qui est en fait une implémentation d’une trace distribuée ou d’une étendue dans une trace. Les éléments internes du module prennent en charge les activités parent/enfant, y compris l’allocation des identificateurs. Pour plus d’informations sur l' `Activity` utilisation du type, consultez le [Guide de l’utilisateur de l’activité sur GitHub](https://github.com/dotnet/corefx/blob/master/src/System.Diagnostics.DiagnosticSource/src/ActivityUserGuide.md#activity-user-guide)

Étant donné que DiagnosticSource fait partie de l’infrastructure de base, il est pris en charge par plusieurs <xref:System.Net.Http.HttpClient>composants principaux, y compris, Entity Framework Core et ASP.net Core, notamment la prise en charge explicite dans l’infrastructure gRPC. Lorsque ASP.NET Core reçoit une demande, il recherche une paire d’en-têtes HTTP correspondant à la norme du [contexte de trace W3C](https://www.w3.org/TR/trace-context) . Si les en-têtes sont trouvés, une activité est démarrée à l’aide des valeurs d’identité et du contexte des en-têtes. Si aucun en-tête n’est trouvé, une activité est démarrée avec des valeurs d’identité générées qui correspondent au format standard. Les diagnostics générés par l’infrastructure ou par le code d’application pendant la durée de vie de cette activité peuvent être marqués avec les identificateurs de trace et d’étendue. La `HttpClient` prise en charge s’étend davantage en vérifiant une activité en cours à chaque demande et en ajoutant automatiquement les en-têtes de trace à la demande sortante.

Les bibliothèques clientes et serveur de ASP.NET Core gRPC incluent une prise en charge explicite des DiagnosticSource et de l’activité, et vont créer des activités et appliquer et utiliser automatiquement les informations d’en-tête.

> [!NOTE]
> Tout cela se produit uniquement si un *écouteur* utilise les informations de diagnostic. S’il n’y a pas d’écouteur, aucun diagnostic n’est écrit et aucune activité n’est créée.

### <a name="add-your-own-diagnosticsources-and-activities"></a>Ajouter vos propres DiagnosticSources et activités

Bien qu’une bonne quantité de données soit générée automatiquement par ASP.net Core, y compris gRPC, ainsi que Entity Framework Core `HttpClient`et, vous souhaiterez peut-être ajouter vos propres Diagnostics ou créer des étendues explicites dans le code de votre application. Pour plus d’informations sur l’implémentation de vos propres Diagnostics, reportez-vous au Guide de l' [utilisateur DiagnosticSource](https://github.com/dotnet/corefx/blob/master/src/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md#instrumenting-with-diagnosticsourcediagnosticlistener) et au Guide de l’utilisateur de l' [activité](https://github.com/dotnet/corefx/blob/master/src/System.Diagnostics.DiagnosticSource/src/ActivityUserGuide.md#activity-usage) .

### <a name="store-distributed-trace-data"></a>Stocker les données de trace distribuées

Au moment de l’écriture, le projet OpenTelemetry est toujours en phase précoce et seuls les packages de qualité alpha sont disponibles pour les applications .NET. Le projet OpenTracing offre des bibliothèques plus matures, mais celles-ci seront remplacées par les bibliothèques OpenTelemetry à l’avenir.

L’API OpenTracing est décrite ci-dessous. Si vous préférez utiliser l’API OpenTelemetry plus récente dans votre application, reportez-vous au [référentiel du kit de développement logiciel (SDK) OpenTelemetry .net sur GitHub](https://github.com/open-telemetry/opentelemetry-dotnet).

#### <a name="use-the-opentracing-package-to-store-distributed-trace-data"></a>Utiliser le package OpenTracing pour stocker les données de trace distribuées

[Un package NuGet OpenTracing](https://www.nuget.org/packages/OpenTracing/) qui prend en charge tous les serveurs principaux conformes à OpenTracing (qui peuvent être utilisés indépendamment de `DiagnosticSource`). Il existe un package supplémentaire du projet contributions de l’API OpenTracing, [OpenTracing. contrib. Netcore](https://www.nuget.org/packages/OpenTracing.Contrib.NetCore/), qui ajoute `DiagnosticSource` un écouteur et écrit automatiquement des événements et des activités sur un serveur principal. L’activation de ce package est aussi simple que son installation à partir de NuGet et son ajout en `Startup` tant que service dans votre classe.

```csharp
public class Startup
{
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddOpenTracing();
    }
}
```

Le package OpenTracing est une couche d’abstraction et, en tant que tel, il requiert une implémentation propre à un serveur principal. Les implémentations de l’API OpenTracing sont disponibles pour les serveurs principaux Open source suivants.

| Name | Package | Site Web |
| ---- | ------- | -------- |
| Jaeger | [Jaeger](https://www.nuget.org/packages/Jaeger/) | [jaegertracing.io](https://jaegertracing.io) |
| APM élastique | [Élastique. APM. NetCoreAll](https://www.nuget.org/packages/Elastic.Apm.NetCoreAll/) | [elastic.co/products/apm](https://www.elastic.co/products/apm) |

Pour plus d’informations sur l’API OpenTracing pour .net, consultez les référentiels [OpenTracing pour C# ](https://github.com/opentracing/opentracing-csharp) et [OpenTracing C#contrib/.net Core](https://github.com/opentracing-contrib/csharp-netcore) sur GitHub.

>[!div class="step-by-step"]
>[Précédent](load-balancing.md)
>[Suivant](appendix.md)
