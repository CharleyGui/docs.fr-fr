---
title: Implémenter des tâches en arrière-plan dans les microservices avec IHostedService et la classe BackgroundService
description: Architecture des microservices .NET pour les applications .NET conteneurisées | Comprendre les nouvelles options pour utiliser IHostedService et BackgroundService afin d’implémenter des tâches d’arrière-plan dans des microservices .NET Core.
ms.date: 08/14/2020
ms.openlocfilehash: 4ab215f2196cd2e66b116465c3a582a9846c8066
ms.sourcegitcommit: 0100be20fcf23f61dab672deced70059ed71bb2e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88267995"
---
# <a name="implement-background-tasks-in-microservices-with-ihostedservice-and-the-backgroundservice-class"></a>Implémenter des tâches en arrière-plan dans les microservices avec IHostedService et la classe BackgroundService

Les tâches en arrière-plan et les tâches planifiées sont des éléments que vous devrez peut-être utiliser dans n’importe quelle application, qu’elle respecte ou non le modèle d’architecture de microservices. La différence lors de l’utilisation d’une architecture de microservices est que vous pouvez implémenter la tâche en arrière-plan dans un processus/conteneur distinct pour l’hébergement, afin de pouvoir la mettre à l’échelle en fonction de vos besoins.

D’un point de vue générique, dans .NET Core, nous avons appelé les tâches de ce type *services hébergés*, car il s’agit de services/d’une logique que vous hébergez dans votre hôte/application/microservice. Notez que dans ce cas, le service hébergé représente simplement une classe avec la logique de tâche en arrière-plan.

Depuis .NET Core 2.0, le framework fournit une nouvelle interface nommée <xref:Microsoft.Extensions.Hosting.IHostedService>, qui vous aide à implémenter facilement les services hébergés. L’idée de base est que vous pouvez inscrire plusieurs tâches en arrière-plan (services hébergés) qui s’exécutent en arrière-plan pendant l’exécution de votre hôte ou hôte Web, comme illustré dans l’image 6-26.

![Diagramme comparant ASP.NET Core IWebHost et .NET Core IHost.](./media/background-tasks-with-ihostedservice/ihosted-service-webhost-vs-host.png)

**Figure 6-26.** Utilisation d’IHostedService dans un WebHost et un Host

Prise en charge des ASP.NET Core 1. x et 2. x `IWebHost` pour les processus en arrière-plan dans les applications Web. .NET Core 2,1 et versions ultérieures prennent en charge `IHost` les processus en arrière-plan avec des applications de console simples. Notez la différence faite entre `WebHost` et `Host`.

Un `WebHost` (classe de base implémentant `IWebHost` ) dans ASP.net Core 2,0 est l’artefact d’infrastructure que vous utilisez pour fournir des fonctionnalités de serveur http à votre processus, par exemple quand vous implémentez une application Web MVC ou un service d’API Web. Il offre toutes les nouvelles opportunités en matière d’infrastructure dans ASP.NET Core, ce qui vous permet d’utiliser l’injection de dépendances, d’insérer des intergiciels dans le pipeline de demande et similaires. Le `WebHost` utilise les mêmes `IHostedServices` pour les tâches en arrière-plan.

Un `Host` (classe de base implémentant `IHost`) a été introduit dans .NET Core 2.1. En fait, `Host` vous permet d’avoir une infrastructure similaire à celle que vous avez avec `WebHost` (injection de dépendances, services hébergés, etc.), mais dans ce cas précis, vous souhaitez simplement avoir un processus simple et plus léger en tant qu’hôte, sans lien avec les fonctionnalités MVC, d’API web ou de serveur HTTP.

Par conséquent, vous pouvez choisir et créer un processus hôte spécialisé avec `IHost` pour gérer les services hébergés et rien d’autre, tel qu’un microservice effectué uniquement pour héberger le `IHostedServices` , ou vous pouvez étendre une asp.net CORE existante `WebHost` , telle qu’une API Web ou une application MVC ASP.net CORE existante.

Chaque approche a des avantages et des inconvénients selon vos besoins professionnels et de scalabilité. En gros, si vos tâches en arrière-plan n’ont rien à faire avec HTTP ( `IWebHost` ), vous devez utiliser `IHost` .

## <a name="registering-hosted-services-in-your-webhost-or-host"></a>Inscription de services hébergés sur WebHost ou Host

Examinons plus en détail l' `IHostedService` interface, car son utilisation est assez similaire dans un `WebHost` ou dans un `Host` .

SignalR est un exemple d’artefact qui utilise des services hébergés, mais vous pouvez également l’employer pour des choses beaucoup plus simples, par exemple :

- Tâche en arrière-plan qui interroge une base de données à la recherche des changements survenus
- Tâche planifiée qui met à jour un cache périodiquement
- Implémentation de QueueBackgroundWorkItem qui permet l’exécution d’une tâche sur un thread d’arrière-plan
- Traitement des messages d’une file d’attente de messages en arrière-plan d’une application web, avec un partage des services communs tels que `ILogger`
- Tâche en arrière-plan démarrée avec `Task.Run()`

Fondamentalement, vous pouvez décharger ces actions vers une tâche en arrière-plan qui implémente `IHostedService` .

La façon dont vous ajoutez un ou plusieurs `IHostedServices` à votre `WebHost` ou `Host` consiste à les inscrire à l’aide de la <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionHostedServiceExtensions.AddHostedService%2A>   méthode d’extension dans un ASP.net Core `WebHost` (ou dans un `Host` dans .net Core 2,1 et versions ultérieures). En fait, vous devez inscrire les services hébergés dans la méthode `ConfigureServices()` bien connue de la classe `Startup`, comme dans le code suivant d’un WebHost ASP.NET classique.

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

Sans utiliser `IHostedService`, vous pouvez tout de même démarrer un thread d’arrière-plan pour exécuter une tâche. La différence est précisément au moment de l’arrêt de l’application lorsque ce thread est simplement supprimé sans avoir la possibilité d’exécuter des actions de nettoyage gracieuses.

## <a name="the-ihostedservice-interface"></a>Interface IHostedService

Quand vous inscrivez `IHostedService`, .NET Core appelle les méthodes `StartAsync()` et `StopAsync()` de votre type `IHostedService` durant le démarrage et l’arrêt de l’application, respectivement. Pour plus d’informations, consultez [IHostedService interface](https://docs.microsoft.com/aspnet/core/fundamentals/host/hosted-services?view=aspnetcore-3.1&tabs=visual-studio#ihostedservice-interface) .

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
        // Constructor's parameters validations...
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

Par défaut, le jeton d’annulation est défini avec un délai d’expiration de 5 secondes, même si vous pouvez modifier cette valeur lors de `WebHost` la génération de votre à l’aide `UseShutdownTimeout` de l’extension de `IWebHostBuilder` . Cela signifie que notre service est censé être annulé dans les 5 secondes, sinon il est tué de manière brusque.

Le code suivant change ce délai en le portant à 10 secondes.

```csharp
WebHost.CreateDefaultBuilder(args)
    .UseShutdownTimeout(TimeSpan.FromSeconds(10))
    ...
```

### <a name="summary-class-diagram"></a>Diagramme de classes récapitulatif

L’image suivante montre un résumé visuel des classes et des interfaces impliquées lors de l’implémentation de IHostedServices.

![Diagramme montrant que IWebHost et IHost peuvent héberger de nombreux services.](./media/background-tasks-with-ihostedservice/class-diagram-custom-ihostedservice.png)

**Figure 6-27.** Diagramme de classes montrant les multiples classes et interfaces liées à IHostedService

Diagramme de classes : IWebHost et IHost peuvent héberger de nombreux services, qui héritent de BackgroundService, lequel implémente IHostedService.

### <a name="deployment-considerations-and-takeaways"></a>Éléments importants à retenir et considérations relatives au déploiement

Il est important de noter que la façon dont vous déployez votre `WebHost` ASP.NET Core ou votre `Host` .NET Core peut avoir un impact sur la solution finale. Par exemple, si vous déployez votre `WebHost` sur IIS ou sur un Azure App Service normal, votre hôte peut être arrêté en raison des recyclages de pools d’applications. Toutefois, si vous déployez votre hôte en tant que conteneur dans un orchestrateur comme Kubernetes, vous pouvez contrôler le nombre d’instances actives de votre hôte. En outre, vous pouvez envisager d’autres approches liées au cloud, spécialement conçues pour ces scénarios, par exemple Azure Functions. Enfin, si vous avez besoin que le service soit exécuté tout le temps et si vous déployez sur un serveur Windows, vous pouvez utiliser un service Windows.

Toutefois, même pour un `WebHost` déployé dans un pool d’applications, il existe des scénarios tels que le remplissage ou le vidage du cache en mémoire de l’application qui serait toujours applicable.

L' `IHostedService` interface offre un moyen pratique de démarrer des tâches en arrière-plan dans une application web ASP.net Core (dans .net core 2,0 et versions ultérieures) ou dans n’importe quel processus/hôte (à partir de .net core 2,1 avec `IHost` ). Son principal avantage est l’opportunité que vous faites avec l’annulation appropriée pour nettoyer le code de vos tâches en arrière-plan lorsque l’ordinateur hôte est en cours d’arrêt.

## <a name="additional-resources"></a>Ressources supplémentaires

- **Création d’une tâche planifiée dans ASP.NET Core/standard 2,0** \
  <https://blog.maartenballiauw.be/post/2017/08/01/building-a-scheduled-cache-updater-in-aspnet-core-2.html>

- **Implémentation de IHostedService dans ASP.NET Core 2,0** \
  <https://www.stevejgordon.co.uk/asp-net-core-2-ihostedservice>

- **Exemple GenericHost utilisant ASP.NET Core 2,1** \
  <https://github.com/aspnet/Hosting/tree/release/2.1/samples/GenericHostSample>

> [!div class="step-by-step"]
> [Précédent](test-aspnet-core-services-web-apps.md) 
>  [Suivant](implement-api-gateways-with-ocelot.md)
