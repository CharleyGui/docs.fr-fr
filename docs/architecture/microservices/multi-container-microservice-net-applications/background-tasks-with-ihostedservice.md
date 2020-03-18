---
title: Implémenter des tâches en arrière-plan dans les microservices avec IHostedService et la classe BackgroundService
description: Architecture des microservices .NET pour les applications .NET conteneurisées | Comprendre les nouvelles options pour utiliser IHostedService et BackgroundService afin d’implémenter des tâches d’arrière-plan dans des microservices .NET Core.
ms.date: 01/30/2020
ms.openlocfilehash: fab67c816e90c69a4d593422b4974cb9b8819807
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77502315"
---
# <a name="implement-background-tasks-in-microservices-with-ihostedservice-and-the-backgroundservice-class"></a>Implémenter des tâches en arrière-plan dans les microservices avec IHostedService et la classe BackgroundService

Vous pouvez être amené à implémenter des tâches en arrière-plan et des travaux planifiés dans une application basée sur des microservices ou tout autre genre d’application. Toutefois, il existe une certaine différence quand vous utilisez une architecture de microservices. Vous pouvez implémenter un processus/conteneur de microservice unique pour héberger ces tâches en arrière-plan et adapter l’architecture à vos besoins. Vous pouvez même vérifier que cette architecture exécute une seule instance de ce processus/conteneur de microservice.

D’un point de vue générique, dans .NET Core, nous avons appelé les tâches de ce type *services hébergés*, car il s’agit de services/d’une logique que vous hébergez dans votre hôte/application/microservice. Notez que dans ce cas, le service hébergé représente simplement une classe avec la logique de tâche en arrière-plan.

Depuis .NET Core 2.0, le framework fournit une nouvelle interface nommée <xref:Microsoft.Extensions.Hosting.IHostedService>, qui vous aide à implémenter facilement les services hébergés. L’idée de base est que vous pouvez enregistrer plusieurs tâches d’arrière-plan (services hébergés) qui s’exécutent en arrière-plan pendant que votre hébergeur ou animateur est en cours d’exécution, comme indiqué dans l’image 6-26.

![Diagramme comparant ASP.NET Core IWebHost et .NET Core IHost.](./media/background-tasks-with-ihostedservice/ihosted-service-webhost-vs-host.png)

**Figure 6-26.** Utilisation d’IHostedService dans un WebHost et un Host

ASP.NET support Core 1.x et 2.x `IWebHost` pour les processus d’arrière-plan dans les applications Web. .NET Core 2.1 et `IHost` les versions ultérieures prennent en charge les processus d’arrière-plan avec des applications de consoles simples. Notez la différence faite entre `WebHost` et `Host`.

Un `WebHost` (mise en `IWebHost`œuvre de classe de base) dans ASP.NET Core 2.0 est l’artefact d’infrastructure que vous utilisez pour fournir des fonctionnalités de serveur HTTP à votre processus, par exemple lorsque vous implémentez une application Web MVC ou un service d’API Web. Il fournit toute la nouvelle bonté d’infrastructure dans ASP.NET Core, vous permettant d’utiliser l’injection de dépendance, insérer des middlewares dans le pipeline de demande, et similaire. Les `WebHost` utilisations `IHostedServices` de la même chose pour les tâches de fond.

Un `Host` (classe de base implémentant `IHost`) a été introduit dans .NET Core 2.1. En fait, `Host` vous permet d’avoir une infrastructure similaire à celle que vous avez avec `WebHost` (injection de dépendances, services hébergés, etc.), mais dans ce cas précis, vous souhaitez simplement avoir un processus simple et plus léger en tant qu’hôte, sans lien avec les fonctionnalités MVC, d’API web ou de serveur HTTP.

Par conséquent, vous pouvez choisir et soit `IHost` créer un hôte-processus spécialisé avec pour gérer les `IHostedServices`services hébergés et rien d’autre, `WebHost`un tel microservice fait juste pour l’hébergement de la , ou vous pouvez alternativement étendre un ASP.NET Core existant , comme une ASP.NET’application Web Web existante ou MVC app.

Chaque approche a des avantages et des inconvénients selon vos besoins professionnels et de scalabilité. La ligne du bas est essentiellement que si vos`IWebHost`tâches d’arrière-plan n’ont rien à voir avec HTTP ( ) vous devriez utiliser `IHost`.

## <a name="registering-hosted-services-in-your-webhost-or-host"></a>Inscription de services hébergés sur WebHost ou Host

Examinons plus en détail l’interface `IHostedService`, car son utilisation est assez similaire dans `WebHost` ou `Host`.

SignalR est un exemple d’artefact qui utilise des services hébergés, mais vous pouvez également l’employer pour des choses beaucoup plus simples, par exemple :

- Tâche en arrière-plan qui interroge une base de données à la recherche des changements survenus
- Tâche planifiée qui met à jour un cache périodiquement
- Implémentation de QueueBackgroundWorkItem qui permet l’exécution d’une tâche sur un thread d’arrière-plan
- Traitement des messages d’une file d’attente de messages en arrière-plan d’une application web, avec un partage des services communs tels que `ILogger`
- Tâche en arrière-plan démarrée avec `Task.Run()`

Vous pouvez essentiellement décharger l’une de ces `IHostedService`actions à une tâche de fond qui met en œuvre .

La façon dont vous `IHostedServices` ajoutez `WebHost` `Host` un ou plusieurs dans <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionHostedServiceExtensions.AddHostedService%2A>  votre ou est en les `WebHost` inscrivant `Host` par la méthode d’extension dans un noyau ASP.NET (ou dans un noyau en .NET 2.1 et ci-dessus). En fait, vous devez inscrire les services hébergés dans la méthode `ConfigureServices()` bien connue de la classe `Startup`, comme dans le code suivant d’un WebHost ASP.NET classique.

```csharp
public IServiceProvider ConfigureServices(IServiceCollection services)
{
    //Other DI registrations;

    // Register Hosted Services
    services.AddHostedService<GracePeriodManagerService>();
    services.AddHostedService<MyHostedServiceB>();
    services.AddHostedService<MyHostedServiceC>();
    //...
}
```

Dans ce code, le service hébergé `GracePeriodManagerService` correspond au code réel du microservice de commandes d’eShopOnContainers, alors que les deux autres ne sont que deux exemples supplémentaires.

L’exécution de la tâche en arrière-plan `IHostedService` est coordonnée avec la durée de vie de l’application (hôte ou microservice). Vous inscrivez des tâches quand l’application démarre, et vous pouvez effectuer des actions normales ou de nettoyage quand l’application s’arrête.

Sans utiliser `IHostedService`, vous pouvez tout de même démarrer un thread d’arrière-plan pour exécuter une tâche. La différence se situe précisément au moment de l’arrêt de l’application, quand le thread est simplement tué sans avoir eu l’occasion d’exécuter des actions de nettoyage normales.

## <a name="the-ihostedservice-interface"></a>Interface IHostedService

Quand vous inscrivez `IHostedService`, .NET Core appelle les méthodes `StartAsync()` et `StopAsync()` de votre type `IHostedService` durant le démarrage et l’arrêt de l’application, respectivement. Plus précisément, le démarrage est appelé une fois que le serveur a démarré et que `IApplicationLifetime.ApplicationStarted` est déclenché.

`IHostedService`, tel qu’il est défini en .NET Core, ressemble à ce qui suit.

```csharp
namespace Microsoft.Extensions.Hosting
{
    //
    // Summary:
    //     Defines methods for objects that are managed by the host.
    public interface IHostedService
    {
        //
        // Summary:
        // Triggered when the application host is ready to start the service.
        Task StartAsync(CancellationToken cancellationToken);
        //
        // Summary:
        // Triggered when the application host is performing a graceful shutdown.
        Task StopAsync(CancellationToken cancellationToken);
    }
}
```

Naturellement, vous pouvez créer plusieurs implémentations d’IHostedService et les inscrire auprès de la méthode `ConfigureService()` dans le conteneur d’injection de dépendances, comme nous l’avons déjà indiqué. Tous ces services hébergés démarrent et s’arrêtent avec l’application/le microservice.

En tant que développeur, vous êtes responsable de la prise en charge de l’action d’arrêt ou de vos services quand la méthode `StopAsync()` est déclenchée par l’hôte.

## <a name="implementing-ihostedservice-with-a-custom-hosted-service-class-deriving-from-the-backgroundservice-base-class"></a>Implémentation d’IHostedService avec une classe de service hébergé personnalisé dérivant de la classe de base BackgroundService

Vous pouvez donc créer entièrement votre classe de service hébergé personnalisé, et implémentez `IHostedService`, comme vous le faites quand vous utilisez .NET Core 2.0.

Toutefois, comme la plupart des tâches en arrière-plan ont des besoins similaires en ce qui concerne la gestion des jetons d’annulation et d’autres opérations classiques, il existe une classe de base abstraite pratique, nommée `BackgroundService` (disponible depuis .NET Core 2.1).

Cette classe fournit le travail principal nécessaire à la configuration de la tâche en arrière-plan.

Le code suivant est la classe de base BackgroundService abstraite implémentée dans .NET Core.

```csharp
// Copyright (c) .NET Foundation. Licensed under the Apache License, Version 2.0.
/// <summary>
/// Base class for implementing a long running <see cref="IHostedService"/>.
/// </summary>
public abstract class BackgroundService : IHostedService, IDisposable
{
    private Task _executingTask;
    private readonly CancellationTokenSource _stoppingCts =
                                                   new CancellationTokenSource();

    protected abstract Task ExecuteAsync(CancellationToken stoppingToken);

    public virtual Task StartAsync(CancellationToken cancellationToken)
    {
        // Store the task we're executing
        _executingTask = ExecuteAsync(_stoppingCts.Token);

        // If the task is completed then return it,
        // this will bubble cancellation and failure to the caller
        if (_executingTask.IsCompleted)
        {
            return _executingTask;
        }

        // Otherwise it's running
        return Task.CompletedTask;
    }

    public virtual async Task StopAsync(CancellationToken cancellationToken)
    {
        // Stop called without start
        if (_executingTask == null)
        {
            return;
        }

        try
        {
            // Signal cancellation to the executing method
            _stoppingCts.Cancel();
        }
        finally
        {
            // Wait until the task completes or the stop token triggers
            await Task.WhenAny(_executingTask, Task.Delay(Timeout.Infinite,
                                                          cancellationToken));
        }

    }

    public virtual void Dispose()
    {
        _stoppingCts.Cancel();
    }
}
```

Quand vous effectuez une dérivation à partir de la classe de base abstraite précédente, grâce à l’implémentation héritée, vous devez simplement implémenter la méthode `ExecuteAsync()` dans votre propre classe de service hébergé personnalisé, comme dans le code simplifié suivant d’eShopOnContainers. Ce code interroge une base de données et publie des événements d’intégration dans le bus d’événements, le cas échéant.

```csharp
public class GracePeriodManagerService : BackgroundService
{
    private readonly ILogger<GracePeriodManagerService> _logger;
    private readonly OrderingBackgroundSettings _settings;

    private readonly IEventBus _eventBus;

    public GracePeriodManagerService(IOptions<OrderingBackgroundSettings> settings,
                                     IEventBus eventBus,
                                     ILogger<GracePeriodManagerService> logger)
    {
        //Constructor’s parameters validations...
    }

    protected override async Task ExecuteAsync(CancellationToken stoppingToken)
    {
        _logger.LogDebug($"GracePeriodManagerService is starting.");

        stoppingToken.Register(() =>
            _logger.LogDebug($" GracePeriod background task is stopping."));

        while (!stoppingToken.IsCancellationRequested)
        {
            _logger.LogDebug($"GracePeriod task doing background work.");

            // This eShopOnContainers method is querying a database table
            // and publishing events into the Event Bus (RabbitMQ / ServiceBus)
            CheckConfirmedGracePeriodOrders();

            await Task.Delay(_settings.CheckUpdateTime, stoppingToken);
        }

        _logger.LogDebug($"GracePeriod background task is stopping.");
    }

    .../...
}
```

Dans ce cas de figure spécifique à eShopOnContainers, le code exécute une méthode d’application qui interroge une table de base de données à la recherche de commandes ayant un état spécifique. Quand des changements sont appliqués, il publie les événements d’intégration via le bus d’événements (il peut s’agir de RabbitMQ ou d’Azure Service Bus).

Bien entendu, vous pouvez exécuter une autre tâche en arrière-plan à la place.

Par défaut, le jeton d’annulation est défini avec un délai d’expiration de 5 secondes. Toutefois, vous pouvez changer cette valeur quand vous générez votre `WebHost` à l’aide de l’extension `UseShutdownTimeout` de `IWebHostBuilder`. Cela signifie que notre service est censé être annulé dans les 5 secondes, sinon il est tué de manière brusque.

Le code suivant change ce délai en le portant à 10 secondes.

```csharp
WebHost.CreateDefaultBuilder(args)
    .UseShutdownTimeout(TimeSpan.FromSeconds(10))
    ...
```

### <a name="summary-class-diagram"></a>Diagramme de classes récapitulatif

L’image suivante montre un résumé visuel des classes et des interfaces impliquées dans la mise en œuvre d’IHostedServices.

![Diagramme montrant que IWebHost et IHost peuvent héberger de nombreux services.](./media/background-tasks-with-ihostedservice/class-diagram-custom-ihostedservice.png)

**Figure 6-27.** Diagramme de classes montrant les multiples classes et interfaces liées à IHostedService

Diagramme de classes : IWebHost et IHost peuvent héberger de nombreux services, qui héritent de BackgroundService, lequel implémente IHostedService.

### <a name="deployment-considerations-and-takeaways"></a>Éléments importants à retenir et considérations relatives au déploiement

Il est important de noter que la façon dont vous déployez votre `WebHost` ASP.NET Core ou votre `Host` .NET Core peut avoir un impact sur la solution finale. Par exemple, si vous déployez votre `WebHost` sur IIS ou sur un Azure App Service normal, votre hôte peut être arrêté en raison des recyclages de pools d’applications. Mais si vous déployez votre hôte comme un conteneur dans un orchestrateur comme Kubernetes, vous pouvez contrôler le nombre assuré d’instances en direct de votre hôte. En outre, vous pouvez envisager d’autres approches liées au cloud, spécialement conçues pour ces scénarios, par exemple Azure Functions. Enfin, si vous avez besoin que le service soit exécuté tout le temps et si vous déployez sur un serveur Windows, vous pouvez utiliser un service Windows.

Mais même `WebHost` pour un déploiement dans un pool d’applications, il existe des scénarios comme le repeuplement ou le cache de rinçage de l’application de rinçage qui serait toujours applicable.

L’interface `IHostedService` fournit un moyen pratique de commencer des tâches d’arrière-plan dans une application web ASP.NET Core (en .NET Core 2.0 `IHost`et versions ultérieures) ou dans n’importe quel processus / hôte (à partir de .NET Core 2.1 avec ). Le principal avantage est le suivant : grâce à l’annulation normale, vous pouvez nettoyer le code de vos tâches en arrière-plan quand l’hôte s’arrête.

## <a name="additional-resources"></a>Ressources supplémentaires

- **Construire une tâche prévue dans ASP.NET Core/Standard 2.0** \
  <https://blog.maartenballiauw.be/post/2017/08/01/building-a-scheduled-cache-updater-in-aspnet-core-2.html>

- **Mise en œuvre de IHostedService dans ASP.NET Core 2.0** \
  <https://www.stevejgordon.co.uk/asp-net-core-2-ihostedservice>

- **GenericHost Échantillon à l’aide de ASP.NET Core 2.1** \
  <https://github.com/aspnet/Hosting/tree/release/2.1/samples/GenericHostSample>

>[!div class="step-by-step"]
>[Suivant précédent](test-aspnet-core-services-web-apps.md)
>[Next](implement-api-gateways-with-ocelot.md)
