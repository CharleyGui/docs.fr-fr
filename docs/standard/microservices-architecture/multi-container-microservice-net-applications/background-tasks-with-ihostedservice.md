---
title: Implémenter des tâches en arrière-plan dans les microservices avec IHostedService et la classe BackgroundService
description: Architecture des microservices .NET pour les applications .NET conteneurisées | Comprendre les nouvelles options pour utiliser IHostedService et BackgroundService afin d’implémenter des tâches d’arrière-plan dans des microservices .NET Core.
ms.date: 01/07/2019
ms.openlocfilehash: 9203404c0b623570c2b089087b7ce5d676bba376
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/06/2019
ms.locfileid: "65062980"
---
# <a name="implement-background-tasks-in-microservices-with-ihostedservice-and-the-backgroundservice-class"></a><span data-ttu-id="8f099-103">Implémenter des tâches en arrière-plan dans les microservices avec IHostedService et la classe BackgroundService</span><span class="sxs-lookup"><span data-stu-id="8f099-103">Implement background tasks in microservices with IHostedService and the BackgroundService class</span></span>

<span data-ttu-id="8f099-104">Vous pouvez être amené à implémenter des tâches en arrière-plan et des travaux planifiés dans une application basée sur des microservices ou tout autre genre d’application.</span><span class="sxs-lookup"><span data-stu-id="8f099-104">Background tasks and scheduled jobs are something you might need to implement, eventually, in a microservice based application or in any kind of application.</span></span> <span data-ttu-id="8f099-105">Toutefois, il existe une certaine différence quand vous utilisez une architecture de microservices. Vous pouvez implémenter un processus/conteneur de microservice unique pour héberger ces tâches en arrière-plan et adapter l’architecture à vos besoins. Vous pouvez même vérifier que cette architecture exécute une seule instance de ce processus/conteneur de microservice.</span><span class="sxs-lookup"><span data-stu-id="8f099-105">The difference when using a microservices architecture is that you can implement a single microservice process/container for hosting these background tasks so you can scale it down/up as you need or you can even make sure that it runs a single instance of that microservice process/container.</span></span>

<span data-ttu-id="8f099-106">D’un point de vue générique, dans .NET Core, nous avons appelé les tâches de ce type *services hébergés*, car il s’agit de services/d’une logique que vous hébergez dans votre hôte/application/microservice.</span><span class="sxs-lookup"><span data-stu-id="8f099-106">From a generic point of view, in .NET Core we called these type of tasks *Hosted Services*, because they are services/logic that you host within your host/application/microservice.</span></span> <span data-ttu-id="8f099-107">Notez que dans ce cas, le service hébergé représente simplement une classe avec la logique de tâche en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="8f099-107">Note that in this case, the hosted service simply means a class with the background task logic.</span></span>

<span data-ttu-id="8f099-108">Depuis .NET Core 2.0, le framework fournit une nouvelle interface nommée <xref:Microsoft.Extensions.Hosting.IHostedService>, qui vous aide à implémenter facilement les services hébergés.</span><span class="sxs-lookup"><span data-stu-id="8f099-108">Since .NET Core 2.0, the framework provides a new interface named <xref:Microsoft.Extensions.Hosting.IHostedService> helping you to easily implement hosted services.</span></span> <span data-ttu-id="8f099-109">L’idée de base est que vous pouvez inscrire plusieurs tâches en arrière-plan (services hébergés), qui s’exécutent en arrière-plan pendant que votre hôte ou votre hôte web est en cours d’exécution, comme le montre l’image 6-26.</span><span class="sxs-lookup"><span data-stu-id="8f099-109">The basic idea is that you can register multiple background tasks (hosted services), that run in the background while your web host or host is running, as shown in the image 6-26.</span></span>

![ASP.NET Core 1.x et 2.x prend en charge IWebHost pour les processus en arrière-plan dans les applications web. .NET Core 2.1 prend en charge IHost pour les processus en arrière-plan avec les applications console simples.](./media/image26.png)

<span data-ttu-id="8f099-111">**Figure 6-26.**</span><span class="sxs-lookup"><span data-stu-id="8f099-111">**Figure 6-26**.</span></span> <span data-ttu-id="8f099-112">Utilisation d’IHostedService dans un WebHost et un Host</span><span class="sxs-lookup"><span data-stu-id="8f099-112">Using IHostedService in a WebHost vs. a Host</span></span>

<span data-ttu-id="8f099-113">Notez la différence faite entre `WebHost` et `Host`.</span><span class="sxs-lookup"><span data-stu-id="8f099-113">Note the difference made between `WebHost` and `Host`.</span></span>

<span data-ttu-id="8f099-114">En ASP.NET Core 2.0, `WebHost` (classe de base implémentant `IWebHost`) est l’artefact d’infrastructure qui vous permet de fournir des fonctionnalités de serveur HTTP à votre processus, par exemple si vous implémentez une application web MVC ou un service d’API web.</span><span class="sxs-lookup"><span data-stu-id="8f099-114">A `WebHost` (base class implementing `IWebHost`) in ASP.NET Core 2.0 is the infrastructure artifact you use to provide HTTP server features to your process, such as if you are implementing an MVC web app or Web API service.</span></span> <span data-ttu-id="8f099-115">Il fournit toute la qualité de l’infrastructure en ASP.NET Core, ce qui vous permet d’utiliser l’injection de dépendances, d’insérer des middlewares (intergiciels) dans le pipeline de requête, etc., et d’utiliser précisément les `IHostedServices` pour les tâches en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="8f099-115">It provides all the new infrastructure goodness in ASP.NET Core, enabling you to use dependency injection, insert middlewares in the request pipeline, etc. and precisely use these `IHostedServices` for background tasks.</span></span>

<span data-ttu-id="8f099-116">Un `Host` (classe de base implémentant `IHost`) a été introduit dans .NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="8f099-116">A `Host` (base class implementing `IHost`) was introduced in .NET Core 2.1.</span></span> <span data-ttu-id="8f099-117">En fait, `Host` vous permet d’avoir une infrastructure similaire à celle que vous avez avec `WebHost` (injection de dépendances, services hébergés, etc.), mais dans ce cas précis, vous souhaitez simplement avoir un processus simple et plus léger en tant qu’hôte, sans lien avec les fonctionnalités MVC, d’API web ou de serveur HTTP.</span><span class="sxs-lookup"><span data-stu-id="8f099-117">Basically, a `Host` allows you to have a similar infrastructure than what you have with `WebHost` (dependency injection, hosted services, etc.), but in this case, you just want to have a simple and lighter process as the host, with nothing related to MVC, Web API or HTTP server features.</span></span>

<span data-ttu-id="8f099-118">Ainsi, vous pouvez créer un processus hôte spécialisé avec IHost pour prendre en charge les services hébergés et rien d’autre, par exemple un microservice destiné uniquement à héberger `IHostedServices`, ou vous pouvez étendre un `WebHost` ASP.NET Core existant, par exemple une API web ou une application MVC ASP.NET Core existante.</span><span class="sxs-lookup"><span data-stu-id="8f099-118">Therefore, you can choose and either create a specialized host-process with IHost to handle the hosted services and nothing else, such a microservice made just for hosting the `IHostedServices`, or you can alternatively extend an existing ASP.NET Core `WebHost`, such as an existing ASP.NET Core Web API or MVC app.</span></span>

<span data-ttu-id="8f099-119">Chaque approche a des avantages et des inconvénients selon vos besoins professionnels et de scalabilité.</span><span class="sxs-lookup"><span data-stu-id="8f099-119">Each approach has pros and cons depending on your business and scalability needs.</span></span> <span data-ttu-id="8f099-120">En fin de compte, si vos tâches en arrière-plan n’ont rien à voir avec le protocole HTTP (IWebHost), utilisez IHost.</span><span class="sxs-lookup"><span data-stu-id="8f099-120">The bottom line is basically that if your background tasks have nothing to do with HTTP (IWebHost) you should use IHost.</span></span>

## <a name="registering-hosted-services-in-your-webhost-or-host"></a><span data-ttu-id="8f099-121">Inscription de services hébergés sur WebHost ou Host</span><span class="sxs-lookup"><span data-stu-id="8f099-121">Registering hosted services in your WebHost or Host</span></span>

<span data-ttu-id="8f099-122">Examinons plus en détail l’interface `IHostedService`, car son utilisation est assez similaire dans `WebHost` ou `Host`.</span><span class="sxs-lookup"><span data-stu-id="8f099-122">Let’s drill down further on the `IHostedService` interface since its usage is pretty similar in a `WebHost` or in a `Host`.</span></span>

<span data-ttu-id="8f099-123">SignalR est un exemple d’artefact qui utilise des services hébergés, mais vous pouvez également l’employer pour des choses beaucoup plus simples, par exemple :</span><span class="sxs-lookup"><span data-stu-id="8f099-123">SignalR is one example of an artifact using hosted services, but you can also use it for much simpler things like:</span></span>

- <span data-ttu-id="8f099-124">Tâche en arrière-plan qui interroge une base de données à la recherche des changements survenus</span><span class="sxs-lookup"><span data-stu-id="8f099-124">A background task polling a database looking for changes.</span></span>
- <span data-ttu-id="8f099-125">Tâche planifiée qui met à jour un cache périodiquement</span><span class="sxs-lookup"><span data-stu-id="8f099-125">A scheduled task updating some cache periodically.</span></span>
- <span data-ttu-id="8f099-126">Implémentation de QueueBackgroundWorkItem qui permet l’exécution d’une tâche sur un thread d’arrière-plan</span><span class="sxs-lookup"><span data-stu-id="8f099-126">An implementation of QueueBackgroundWorkItem that allows a task to be executed on a background thread.</span></span>
- <span data-ttu-id="8f099-127">Traitement des messages d’une file d’attente de messages en arrière-plan d’une application web, avec un partage des services communs tels que `ILogger`</span><span class="sxs-lookup"><span data-stu-id="8f099-127">Processing messages from a message queue in the background of a web app while sharing common services such as `ILogger`.</span></span>
- <span data-ttu-id="8f099-128">Tâche en arrière-plan démarrée avec `Task.Run()`</span><span class="sxs-lookup"><span data-stu-id="8f099-128">A background task started with `Task.Run()`.</span></span>

<span data-ttu-id="8f099-129">Vous pouvez tout simplement décharger l’une de ces actions vers une tâche en arrière-plan basée sur IHostedService.</span><span class="sxs-lookup"><span data-stu-id="8f099-129">You can basically offload any of those actions to a background task based on IHostedService.</span></span>

<span data-ttu-id="8f099-130">Pour ajouter un ou plusieurs `IHostedServices` dans `WebHost` ou `Host`, vous devez les inscrire via l’injection de dépendances standard dans un `WebHost` ASP.NET Core (ou dans `Host` au sein de NET Core versions 2.1 et supérieures).</span><span class="sxs-lookup"><span data-stu-id="8f099-130">The way you add one or multiple `IHostedServices` into your `WebHost` or `Host` is by registering them up through the standard DI (dependency injection) in an ASP.NET Core `WebHost` (or in a `Host` in .NET Core 2.1 and above).</span></span> <span data-ttu-id="8f099-131">En fait, vous devez inscrire les services hébergés dans la méthode `ConfigureServices()` bien connue de la classe `Startup`, comme dans le code suivant d’un WebHost ASP.NET classique.</span><span class="sxs-lookup"><span data-stu-id="8f099-131">Basically, you have to register the hosted services within the familiar `ConfigureServices()` method of the `Startup` class, as in the following code from a typical ASP.NET WebHost.</span></span>

```csharp
public IServiceProvider ConfigureServices(IServiceCollection services)
{
    //Other DI registrations;

    // Register Hosted Services
    services.AddSingleton<IHostedService, GracePeriodManagerService>();
    services.AddSingleton<IHostedService, MyHostedServiceB>();
    services.AddSingleton<IHostedService, MyHostedServiceC>();
    //...
}
```

<span data-ttu-id="8f099-132">Dans ce code, le service hébergé `GracePeriodManagerService` correspond au code réel du microservice de commandes d’eShopOnContainers, alors que les deux autres ne sont que deux exemples supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="8f099-132">In that code, the `GracePeriodManagerService` hosted service is real code from the Ordering business microservice in eShopOnContainers, while the other two are just two additional samples.</span></span>

<span data-ttu-id="8f099-133">L’exécution de la tâche en arrière-plan `IHostedService` est coordonnée avec la durée de vie de l’application (hôte ou microservice).</span><span class="sxs-lookup"><span data-stu-id="8f099-133">The `IHostedService` background task execution is coordinated with the lifetime of the application (host or microservice, for that matter).</span></span> <span data-ttu-id="8f099-134">Vous inscrivez des tâches quand l’application démarre, et vous pouvez effectuer des actions normales ou de nettoyage quand l’application s’arrête.</span><span class="sxs-lookup"><span data-stu-id="8f099-134">You register tasks when the application starts and you have the opportunity to do some graceful action or clean-up when the application is shutting down.</span></span>

<span data-ttu-id="8f099-135">Sans utiliser `IHostedService`, vous pouvez tout de même démarrer un thread d’arrière-plan pour exécuter une tâche.</span><span class="sxs-lookup"><span data-stu-id="8f099-135">Without using `IHostedService`, you could always start a background thread to run any task.</span></span> <span data-ttu-id="8f099-136">La différence se situe précisément au moment de l’arrêt de l’application, quand le thread est simplement tué sans avoir eu l’occasion d’exécuter des actions de nettoyage normales.</span><span class="sxs-lookup"><span data-stu-id="8f099-136">The difference is precisely at the app’s shutdown time when that thread would simply be killed without having the opportunity to run graceful clean-up actions.</span></span>

## <a name="the-ihostedservice-interface"></a><span data-ttu-id="8f099-137">Interface IHostedService</span><span class="sxs-lookup"><span data-stu-id="8f099-137">The IHostedService interface</span></span>

<span data-ttu-id="8f099-138">Quand vous inscrivez `IHostedService`, .NET Core appelle les méthodes `StartAsync()` et `StopAsync()` de votre type `IHostedService` durant le démarrage et l’arrêt de l’application, respectivement.</span><span class="sxs-lookup"><span data-stu-id="8f099-138">When you register an `IHostedService`, .NET Core will call the `StartAsync()` and `StopAsync()` methods of your `IHostedService` type during application start and stop respectively.</span></span> <span data-ttu-id="8f099-139">Plus précisément, le démarrage est appelé une fois que le serveur a démarré et que `IApplicationLifetime.ApplicationStarted` est déclenché.</span><span class="sxs-lookup"><span data-stu-id="8f099-139">Specifically, start is called after the server has started and `IApplicationLifetime.ApplicationStarted` is triggered.</span></span>

<span data-ttu-id="8f099-140">`IHostedService`, tel qu’il est défini en .NET Core, ressemble à ce qui suit.</span><span class="sxs-lookup"><span data-stu-id="8f099-140">The `IHostedService` as defined in .NET Core, looks like the following.</span></span>

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

<span data-ttu-id="8f099-141">Naturellement, vous pouvez créer plusieurs implémentations d’IHostedService et les inscrire auprès de la méthode `ConfigureService()` dans le conteneur d’injection de dépendances, comme nous l’avons déjà indiqué.</span><span class="sxs-lookup"><span data-stu-id="8f099-141">As you can imagine, you can create multiple implementations of IHostedService and register them at the `ConfigureService()` method into the DI container, as shown previously.</span></span> <span data-ttu-id="8f099-142">Tous ces services hébergés démarrent et s’arrêtent avec l’application/le microservice.</span><span class="sxs-lookup"><span data-stu-id="8f099-142">All those hosted services will be started and stopped along with the application/microservice.</span></span>

<span data-ttu-id="8f099-143">En tant que développeur, vous êtes responsable de la prise en charge de l’action d’arrêt ou de vos services quand la méthode `StopAsync()` est déclenchée par l’hôte.</span><span class="sxs-lookup"><span data-stu-id="8f099-143">As a developer, you are responsible for handling the stopping action of your services when `StopAsync()` method is triggered by the host.</span></span>

## <a name="implementing-ihostedservice-with-a-custom-hosted-service-class-deriving-from-the-backgroundservice-base-class"></a><span data-ttu-id="8f099-144">Implémentation d’IHostedService avec une classe de service hébergé personnalisé dérivant de la classe de base BackgroundService</span><span class="sxs-lookup"><span data-stu-id="8f099-144">Implementing IHostedService with a custom hosted service class deriving from the BackgroundService base class</span></span>

<span data-ttu-id="8f099-145">Vous pouvez donc créer entièrement votre classe de service hébergé personnalisé, et implémentez `IHostedService`, comme vous le faites quand vous utilisez .NET Core 2.0.</span><span class="sxs-lookup"><span data-stu-id="8f099-145">You could go ahead and create your custom hosted service class from scratch and implement the `IHostedService`, as you need to do when using .NET Core 2.0.</span></span>

<span data-ttu-id="8f099-146">Toutefois, comme la plupart des tâches en arrière-plan ont des besoins similaires en ce qui concerne la gestion des jetons d’annulation et d’autres opérations classiques, il existe une classe de base abstraite pratique, nommée `BackgroundService` (disponible depuis .NET Core 2.1).</span><span class="sxs-lookup"><span data-stu-id="8f099-146">However, since most background tasks will have similar needs in regard to the cancellation tokens management and other typical operations, there is a convenient abstract base class you can derive from, named `BackgroundService` (available since .NET Core 2.1).</span></span>

<span data-ttu-id="8f099-147">Cette classe fournit le travail principal nécessaire à la configuration de la tâche en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="8f099-147">That class provides the main work needed to set up the background task.</span></span>

<span data-ttu-id="8f099-148">Le code suivant est la classe de base BackgroundService abstraite implémentée dans .NET Core.</span><span class="sxs-lookup"><span data-stu-id="8f099-148">The next code is the abstract BackgroundService base class as implemented in .NET Core.</span></span>

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

<span data-ttu-id="8f099-149">Quand vous effectuez une dérivation à partir de la classe de base abstraite précédente, grâce à l’implémentation héritée, vous devez simplement implémenter la méthode `ExecuteAsync()` dans votre propre classe de service hébergé personnalisé, comme dans le code simplifié suivant d’eShopOnContainers. Ce code interroge une base de données et publie des événements d’intégration dans le bus d’événements, le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="8f099-149">When deriving from the previous abstract base class, thanks to that inherited implementation, you just need to implement the `ExecuteAsync()` method in your own custom hosted service class, as in the following simplified code from eShopOnContainers which is polling a database and publishing integration events into the Event Bus when needed.</span></span>

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
            // and publishing events into the Event Bus (RabbitMS / ServiceBus)
            CheckConfirmedGracePeriodOrders();

            await Task.Delay(_settings.CheckUpdateTime, stoppingToken);
        }

        _logger.LogDebug($"GracePeriod background task is stopping.");
    }

    .../...
}
```

<span data-ttu-id="8f099-150">Dans ce cas de figure spécifique à eShopOnContainers, le code exécute une méthode d’application qui interroge une table de base de données à la recherche de commandes ayant un état spécifique. Quand des changements sont appliqués, il publie les événements d’intégration via le bus d’événements (il peut s’agir de RabbitMQ ou d’Azure Service Bus).</span><span class="sxs-lookup"><span data-stu-id="8f099-150">In this specific case for eShopOnContainers, it's executing an application method that's querying a database table looking for orders with a specific state and when applying changes, it is publishing integration events through the event bus (underneath it can be using RabbitMQ or Azure Service Bus).</span></span>

<span data-ttu-id="8f099-151">Bien entendu, vous pouvez exécuter une autre tâche en arrière-plan à la place.</span><span class="sxs-lookup"><span data-stu-id="8f099-151">Of course, you could run any other business background task, instead.</span></span>

<span data-ttu-id="8f099-152">Par défaut, le jeton d’annulation est défini avec un délai d’expiration de 5 secondes. Toutefois, vous pouvez changer cette valeur quand vous générez votre `WebHost` à l’aide de l’extension `UseShutdownTimeout` de `IWebHostBuilder`.</span><span class="sxs-lookup"><span data-stu-id="8f099-152">By default, the cancellation token is set with a 5 second timeout, although you can change that value when building your `WebHost` using the `UseShutdownTimeout` extension of the `IWebHostBuilder`.</span></span> <span data-ttu-id="8f099-153">Cela signifie que notre service est censé être annulé dans les 5 secondes, sinon il est tué de manière brusque.</span><span class="sxs-lookup"><span data-stu-id="8f099-153">This means that our service is expected to cancel within 5 seconds otherwise it will be more abruptly killed.</span></span>

<span data-ttu-id="8f099-154">Le code suivant change ce délai en le portant à 10 secondes.</span><span class="sxs-lookup"><span data-stu-id="8f099-154">The following code would be changing that time to 10 seconds.</span></span>

```csharp
WebHost.CreateDefaultBuilder(args)
    .UseShutdownTimeout(TimeSpan.FromSeconds(10))
    ...
```

### <a name="summary-class-diagram"></a><span data-ttu-id="8f099-155">Diagramme de classes récapitulatif</span><span class="sxs-lookup"><span data-stu-id="8f099-155">Summary class diagram</span></span>

<span data-ttu-id="8f099-156">L’image suivante montre un récapitulatif visuel des classes et des interfaces impliquées dans l’implémentation d’IHostedServices.</span><span class="sxs-lookup"><span data-stu-id="8f099-156">The following image shows a visual summary of the classes and interfaced involved when implementing IHostedServices.</span></span>

![Diagramme de classes : IWebHost et IHost peuvent héberger de nombreux services, qui héritent de BackgroundService, lequel implémente IHostedService.](./media/image27.png)

<span data-ttu-id="8f099-158">**Figure 6-27.**</span><span class="sxs-lookup"><span data-stu-id="8f099-158">**Figure 6-27**.</span></span> <span data-ttu-id="8f099-159">Diagramme de classes montrant les multiples classes et interfaces liées à IHostedService</span><span class="sxs-lookup"><span data-stu-id="8f099-159">Class diagram showing the multiple classes and interfaces related to IHostedService</span></span>

### <a name="deployment-considerations-and-takeaways"></a><span data-ttu-id="8f099-160">Éléments importants à retenir et considérations relatives au déploiement</span><span class="sxs-lookup"><span data-stu-id="8f099-160">Deployment considerations and takeaways</span></span>

<span data-ttu-id="8f099-161">Il est important de noter que la façon dont vous déployez votre `WebHost` ASP.NET Core ou votre `Host` .NET Core peut avoir un impact sur la solution finale.</span><span class="sxs-lookup"><span data-stu-id="8f099-161">It is important to note that the way you deploy your ASP.NET Core `WebHost` or .NET Core `Host` might impact the final solution.</span></span> <span data-ttu-id="8f099-162">Par exemple, si vous déployez votre `WebHost` sur IIS ou sur un Azure App Service normal, votre hôte peut être arrêté en raison des recyclages de pools d’applications.</span><span class="sxs-lookup"><span data-stu-id="8f099-162">For instance, if you deploy your `WebHost` on IIS or a regular Azure App Service, your host can be shut down because of app pool recycles.</span></span> <span data-ttu-id="8f099-163">Mais si vous déployez votre hôte en tant que conteneur dans un orchestrateur comme Kubernetes ou Service Fabric, vous pouvez contrôler le nombre garanti d’instances dynamiques de l’hôte.</span><span class="sxs-lookup"><span data-stu-id="8f099-163">But if you are deploying your host as a container into an orchestrator like Kubernetes or Service Fabric, you can control the assured number of live instances of your host.</span></span> <span data-ttu-id="8f099-164">En outre, vous pouvez envisager d’autres approches liées au cloud, spécialement conçues pour ces scénarios, par exemple Azure Functions.</span><span class="sxs-lookup"><span data-stu-id="8f099-164">In addition, you could consider other approaches in the cloud especially made for these scenarios, like Azure Functions.</span></span> <span data-ttu-id="8f099-165">Enfin, si vous avez besoin que le service soit exécuté tout le temps et si vous déployez sur un serveur Windows, vous pouvez utiliser un service Windows.</span><span class="sxs-lookup"><span data-stu-id="8f099-165">Finally, if you need the service to be running all the time and are deploying on a Windows Server you could use a Windows Service.</span></span>

<span data-ttu-id="8f099-166">Toutefois, même pour un `WebHost` déployé dans un pool d’applications, il existe des scénarios tels que le repeuplement ou le vidage du cache en mémoire de l’application, qui sont toujours applicables.</span><span class="sxs-lookup"><span data-stu-id="8f099-166">But even for a `WebHost` deployed into an app pool, there are scenarios like repopulating or flushing application’s in-memory cache, that would be still applicable.</span></span>

<span data-ttu-id="8f099-167">L’interface `IHostedService` fournit un moyen pratique de démarrer des tâches en arrière-plan dans une application web ASP.NET Core (dans .NET Core 2.0) ou dans n’importe quel processus/hôte (à partir de .NET Core 2.1 avec `IHost`).</span><span class="sxs-lookup"><span data-stu-id="8f099-167">The `IHostedService` interface provides a convenient way to start background tasks in an ASP.NET Core web application (in .NET Core 2.0) or in any process/host (starting in .NET Core 2.1 with `IHost`).</span></span> <span data-ttu-id="8f099-168">Le principal avantage est le suivant : grâce à l’annulation normale, vous pouvez nettoyer le code de vos tâches en arrière-plan quand l’hôte s’arrête.</span><span class="sxs-lookup"><span data-stu-id="8f099-168">Its main benefit is the opportunity you get with the graceful cancellation to clean-up code of your background tasks when the host itself is shutting down.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="8f099-169">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="8f099-169">Additional resources</span></span>

- <span data-ttu-id="8f099-170">**Génération d’une tâche planifiée avec ASP.NET Core/Standard 2.0**</span><span class="sxs-lookup"><span data-stu-id="8f099-170">**Building a scheduled task in ASP.NET Core/Standard 2.0**</span></span> <br/>
    <https://blog.maartenballiauw.be/post/2017/08/01/building-a-scheduled-cache-updater-in-aspnet-core-2.html>

- <span data-ttu-id="8f099-171">**Implémentation d’IHostedService avec ASP.NET Core 2.0**</span><span class="sxs-lookup"><span data-stu-id="8f099-171">**Implementing IHostedService in ASP.NET Core 2.0**</span></span> <br/>
    <https://www.stevejgordon.co.uk/asp-net-core-2-ihostedservice>

- <span data-ttu-id="8f099-172">**Exemple GenericHost utilisant ASP.NET Core 2.1**</span><span class="sxs-lookup"><span data-stu-id="8f099-172">**GenericHost Sample using ASP.NET Core 2.1**</span></span> <br/>
    <https://github.com/aspnet/Hosting/tree/release/2.1/samples/GenericHostSample>

>[!div class="step-by-step"]
><span data-ttu-id="8f099-173">[Précédent](test-aspnet-core-services-web-apps.md)
>[Suivant](implement-api-gateways-with-ocelot.md)</span><span class="sxs-lookup"><span data-stu-id="8f099-173">[Previous](test-aspnet-core-services-web-apps.md)
[Next](implement-api-gateways-with-ocelot.md)</span></span>
