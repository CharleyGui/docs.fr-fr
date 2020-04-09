---
title: Implémenter des tâches en arrière-plan dans les microservices avec IHostedService et la classe BackgroundService
description: Architecture des microservices .NET pour les applications .NET conteneurisées | Comprendre les nouvelles options pour utiliser IHostedService et BackgroundService afin d’implémenter des tâches d’arrière-plan dans des microservices .NET Core.
ms.date: 01/30/2020
ms.openlocfilehash: fd26d0444312d3525ad95b2273f28a6ceaa27911
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2020
ms.locfileid: "80988334"
---
# <a name="implement-background-tasks-in-microservices-with-ihostedservice-and-the-backgroundservice-class"></a><span data-ttu-id="9f363-103">Implémenter des tâches en arrière-plan dans les microservices avec IHostedService et la classe BackgroundService</span><span class="sxs-lookup"><span data-stu-id="9f363-103">Implement background tasks in microservices with IHostedService and the BackgroundService class</span></span>

<span data-ttu-id="9f363-104">Vous pouvez être amené à implémenter des tâches en arrière-plan et des travaux planifiés dans une application basée sur des microservices ou tout autre genre d’application.</span><span class="sxs-lookup"><span data-stu-id="9f363-104">Background tasks and scheduled jobs are something you might need to implement, eventually, in a microservice based application or in any kind of application.</span></span> <span data-ttu-id="9f363-105">Toutefois, il existe une certaine différence quand vous utilisez une architecture de microservices. Vous pouvez implémenter un processus/conteneur de microservice unique pour héberger ces tâches en arrière-plan et adapter l’architecture à vos besoins. Vous pouvez même vérifier que cette architecture exécute une seule instance de ce processus/conteneur de microservice.</span><span class="sxs-lookup"><span data-stu-id="9f363-105">The difference when using a microservices architecture is that you can implement a single microservice process/container for hosting these background tasks so you can scale it down/up as you need or you can even make sure that it runs a single instance of that microservice process/container.</span></span>

<span data-ttu-id="9f363-106">D’un point de vue générique, dans .NET Core, nous avons appelé les tâches de ce type *services hébergés*, car il s’agit de services/d’une logique que vous hébergez dans votre hôte/application/microservice.</span><span class="sxs-lookup"><span data-stu-id="9f363-106">From a generic point of view, in .NET Core we called these type of tasks *Hosted Services*, because they are services/logic that you host within your host/application/microservice.</span></span> <span data-ttu-id="9f363-107">Notez que dans ce cas, le service hébergé représente simplement une classe avec la logique de tâche en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="9f363-107">Note that in this case, the hosted service simply means a class with the background task logic.</span></span>

<span data-ttu-id="9f363-108">Depuis .NET Core 2.0, le framework fournit une nouvelle interface nommée <xref:Microsoft.Extensions.Hosting.IHostedService>, qui vous aide à implémenter facilement les services hébergés.</span><span class="sxs-lookup"><span data-stu-id="9f363-108">Since .NET Core 2.0, the framework provides a new interface named <xref:Microsoft.Extensions.Hosting.IHostedService> helping you to easily implement hosted services.</span></span> <span data-ttu-id="9f363-109">L’idée de base est que vous pouvez enregistrer plusieurs tâches d’arrière-plan (services hébergés) qui s’exécutent en arrière-plan pendant que votre hébergeur ou animateur est en cours d’exécution, comme indiqué dans l’image 6-26.</span><span class="sxs-lookup"><span data-stu-id="9f363-109">The basic idea is that you can register multiple background tasks (hosted services) that run in the background while your web host or host is running, as shown in the image 6-26.</span></span>

![Diagramme comparant ASP.NET Core IWebHost et .NET Core IHost.](./media/background-tasks-with-ihostedservice/ihosted-service-webhost-vs-host.png)

<span data-ttu-id="9f363-111">**Figure 6-26.**</span><span class="sxs-lookup"><span data-stu-id="9f363-111">**Figure 6-26**.</span></span> <span data-ttu-id="9f363-112">Utilisation d’IHostedService dans un WebHost et un Host</span><span class="sxs-lookup"><span data-stu-id="9f363-112">Using IHostedService in a WebHost vs. a Host</span></span>

<span data-ttu-id="9f363-113">ASP.NET support Core 1.x et 2.x `IWebHost` pour les processus d’arrière-plan dans les applications Web.</span><span class="sxs-lookup"><span data-stu-id="9f363-113">ASP.NET Core 1.x and 2.x support `IWebHost` for background processes in web apps.</span></span> <span data-ttu-id="9f363-114">.NET Core 2.1 et `IHost` les versions ultérieures prennent en charge les processus d’arrière-plan avec des applications de consoles simples.</span><span class="sxs-lookup"><span data-stu-id="9f363-114">.NET Core 2.1 and later versions support `IHost` for background processes with plain console apps.</span></span> <span data-ttu-id="9f363-115">Notez la différence faite entre `WebHost` et `Host`.</span><span class="sxs-lookup"><span data-stu-id="9f363-115">Note the difference made between `WebHost` and `Host`.</span></span>

<span data-ttu-id="9f363-116">Un `WebHost` (mise en `IWebHost`œuvre de classe de base) dans ASP.NET Core 2.0 est l’artefact d’infrastructure que vous utilisez pour fournir des fonctionnalités de serveur HTTP à votre processus, par exemple lorsque vous implémentez une application Web MVC ou un service d’API Web.</span><span class="sxs-lookup"><span data-stu-id="9f363-116">A `WebHost` (base class implementing `IWebHost`) in ASP.NET Core 2.0 is the infrastructure artifact you use to provide HTTP server features to your process, such as when you're implementing an MVC web app or Web API service.</span></span> <span data-ttu-id="9f363-117">Il fournit toute la nouvelle bonté d’infrastructure dans ASP.NET Core, vous permettant d’utiliser l’injection de dépendance, insérer des middlewares dans le pipeline de demande, et similaire.</span><span class="sxs-lookup"><span data-stu-id="9f363-117">It provides all the new infrastructure goodness in ASP.NET Core, enabling you to use dependency injection, insert middlewares in the request pipeline, and similar.</span></span> <span data-ttu-id="9f363-118">Les `WebHost` utilisations `IHostedServices` de la même chose pour les tâches de fond.</span><span class="sxs-lookup"><span data-stu-id="9f363-118">The `WebHost` uses these very same `IHostedServices` for background tasks.</span></span>

<span data-ttu-id="9f363-119">Un `Host` (classe de base implémentant `IHost`) a été introduit dans .NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="9f363-119">A `Host` (base class implementing `IHost`) was introduced in .NET Core 2.1.</span></span> <span data-ttu-id="9f363-120">En fait, `Host` vous permet d’avoir une infrastructure similaire à celle que vous avez avec `WebHost` (injection de dépendances, services hébergés, etc.), mais dans ce cas précis, vous souhaitez simplement avoir un processus simple et plus léger en tant qu’hôte, sans lien avec les fonctionnalités MVC, d’API web ou de serveur HTTP.</span><span class="sxs-lookup"><span data-stu-id="9f363-120">Basically, a `Host` allows you to have a similar infrastructure than what you have with `WebHost` (dependency injection, hosted services, etc.), but in this case, you just want to have a simple and lighter process as the host, with nothing related to MVC, Web API or HTTP server features.</span></span>

<span data-ttu-id="9f363-121">Par conséquent, vous pouvez choisir et soit `IHost` créer un hôte-processus spécialisé avec pour gérer les `IHostedServices`services hébergés et rien d’autre, `WebHost`un tel microservice fait juste pour l’hébergement de la , ou vous pouvez alternativement étendre un ASP.NET Core existant , comme une ASP.NET’application Web Web existante ou MVC app.</span><span class="sxs-lookup"><span data-stu-id="9f363-121">Therefore, you can choose and either create a specialized host-process with `IHost` to handle the hosted services and nothing else, such a microservice made just for hosting the `IHostedServices`, or you can alternatively extend an existing ASP.NET Core `WebHost`, such as an existing ASP.NET Core Web API or MVC app.</span></span>

<span data-ttu-id="9f363-122">Chaque approche a des avantages et des inconvénients selon vos besoins professionnels et de scalabilité.</span><span class="sxs-lookup"><span data-stu-id="9f363-122">Each approach has pros and cons depending on your business and scalability needs.</span></span> <span data-ttu-id="9f363-123">La ligne du bas est essentiellement que si vos`IWebHost`tâches d’arrière-plan n’ont rien à voir avec HTTP ( ) vous devriez utiliser `IHost`.</span><span class="sxs-lookup"><span data-stu-id="9f363-123">The bottom line is basically that if your background tasks have nothing to do with HTTP (`IWebHost`) you should use `IHost`.</span></span>

## <a name="registering-hosted-services-in-your-webhost-or-host"></a><span data-ttu-id="9f363-124">Inscription de services hébergés sur WebHost ou Host</span><span class="sxs-lookup"><span data-stu-id="9f363-124">Registering hosted services in your WebHost or Host</span></span>

<span data-ttu-id="9f363-125">Let’s drill down `IHostedService` plus loin sur l’interface `WebHost` puisque `Host`son utilisation est assez similaire dans un ou dans un .</span><span class="sxs-lookup"><span data-stu-id="9f363-125">Let's drill down further on the `IHostedService` interface since its usage is pretty similar in a `WebHost` or in a `Host`.</span></span>

<span data-ttu-id="9f363-126">SignalR est un exemple d’artefact qui utilise des services hébergés, mais vous pouvez également l’employer pour des choses beaucoup plus simples, par exemple :</span><span class="sxs-lookup"><span data-stu-id="9f363-126">SignalR is one example of an artifact using hosted services, but you can also use it for much simpler things like:</span></span>

- <span data-ttu-id="9f363-127">Tâche en arrière-plan qui interroge une base de données à la recherche des changements survenus</span><span class="sxs-lookup"><span data-stu-id="9f363-127">A background task polling a database looking for changes.</span></span>
- <span data-ttu-id="9f363-128">Tâche planifiée qui met à jour un cache périodiquement</span><span class="sxs-lookup"><span data-stu-id="9f363-128">A scheduled task updating some cache periodically.</span></span>
- <span data-ttu-id="9f363-129">Implémentation de QueueBackgroundWorkItem qui permet l’exécution d’une tâche sur un thread d’arrière-plan</span><span class="sxs-lookup"><span data-stu-id="9f363-129">An implementation of QueueBackgroundWorkItem that allows a task to be executed on a background thread.</span></span>
- <span data-ttu-id="9f363-130">Traitement des messages d’une file d’attente de messages en arrière-plan d’une application web, avec un partage des services communs tels que `ILogger`</span><span class="sxs-lookup"><span data-stu-id="9f363-130">Processing messages from a message queue in the background of a web app while sharing common services such as `ILogger`.</span></span>
- <span data-ttu-id="9f363-131">Tâche en arrière-plan démarrée avec `Task.Run()`</span><span class="sxs-lookup"><span data-stu-id="9f363-131">A background task started with `Task.Run()`.</span></span>

<span data-ttu-id="9f363-132">Vous pouvez essentiellement décharger l’une de ces `IHostedService`actions à une tâche de fond qui met en œuvre .</span><span class="sxs-lookup"><span data-stu-id="9f363-132">You can basically offload any of those actions to a background task that implements `IHostedService`.</span></span>

<span data-ttu-id="9f363-133">La façon dont vous `IHostedServices` ajoutez `WebHost` `Host` un ou plusieurs dans <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionHostedServiceExtensions.AddHostedService%2A>  votre ou est en les `WebHost` inscrivant `Host` par la méthode d’extension dans un noyau ASP.NET (ou dans un noyau en .NET 2.1 et ci-dessus).</span><span class="sxs-lookup"><span data-stu-id="9f363-133">The way you add one or multiple `IHostedServices` into your `WebHost` or `Host` is by registering them up through the <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionHostedServiceExtensions.AddHostedService%2A> extension method in an ASP.NET Core `WebHost` (or in a `Host` in .NET Core 2.1 and above).</span></span> <span data-ttu-id="9f363-134">En fait, vous devez inscrire les services hébergés dans la méthode `ConfigureServices()` bien connue de la classe `Startup`, comme dans le code suivant d’un WebHost ASP.NET classique.</span><span class="sxs-lookup"><span data-stu-id="9f363-134">Basically, you have to register the hosted services within the familiar `ConfigureServices()` method of the `Startup` class, as in the following code from a typical ASP.NET WebHost.</span></span>

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

<span data-ttu-id="9f363-135">Dans ce code, le service hébergé `GracePeriodManagerService` correspond au code réel du microservice de commandes d’eShopOnContainers, alors que les deux autres ne sont que deux exemples supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="9f363-135">In that code, the `GracePeriodManagerService` hosted service is real code from the Ordering business microservice in eShopOnContainers, while the other two are just two additional samples.</span></span>

<span data-ttu-id="9f363-136">L’exécution de la tâche en arrière-plan `IHostedService` est coordonnée avec la durée de vie de l’application (hôte ou microservice).</span><span class="sxs-lookup"><span data-stu-id="9f363-136">The `IHostedService` background task execution is coordinated with the lifetime of the application (host or microservice, for that matter).</span></span> <span data-ttu-id="9f363-137">Vous inscrivez des tâches quand l’application démarre, et vous pouvez effectuer des actions normales ou de nettoyage quand l’application s’arrête.</span><span class="sxs-lookup"><span data-stu-id="9f363-137">You register tasks when the application starts and you have the opportunity to do some graceful action or clean-up when the application is shutting down.</span></span>

<span data-ttu-id="9f363-138">Sans utiliser `IHostedService`, vous pouvez tout de même démarrer un thread d’arrière-plan pour exécuter une tâche.</span><span class="sxs-lookup"><span data-stu-id="9f363-138">Without using `IHostedService`, you could always start a background thread to run any task.</span></span> <span data-ttu-id="9f363-139">La différence est précisément à l’heure d’arrêt de l’application où ce thread serait tout simplement tué sans avoir la possibilité d’exécuter des actions de nettoyage gracieux.</span><span class="sxs-lookup"><span data-stu-id="9f363-139">The difference is precisely at the app's shutdown time when that thread would simply be killed without having the opportunity to run graceful clean-up actions.</span></span>

## <a name="the-ihostedservice-interface"></a><span data-ttu-id="9f363-140">Interface IHostedService</span><span class="sxs-lookup"><span data-stu-id="9f363-140">The IHostedService interface</span></span>

<span data-ttu-id="9f363-141">Quand vous inscrivez `IHostedService`, .NET Core appelle les méthodes `StartAsync()` et `StopAsync()` de votre type `IHostedService` durant le démarrage et l’arrêt de l’application, respectivement.</span><span class="sxs-lookup"><span data-stu-id="9f363-141">When you register an `IHostedService`, .NET Core will call the `StartAsync()` and `StopAsync()` methods of your `IHostedService` type during application start and stop respectively.</span></span> <span data-ttu-id="9f363-142">Plus précisément, le démarrage est appelé une fois que le serveur a démarré et que `IApplicationLifetime.ApplicationStarted` est déclenché.</span><span class="sxs-lookup"><span data-stu-id="9f363-142">Specifically, start is called after the server has started and `IApplicationLifetime.ApplicationStarted` is triggered.</span></span>

<span data-ttu-id="9f363-143">`IHostedService`, tel qu’il est défini en .NET Core, ressemble à ce qui suit.</span><span class="sxs-lookup"><span data-stu-id="9f363-143">The `IHostedService` as defined in .NET Core, looks like the following.</span></span>

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

<span data-ttu-id="9f363-144">Naturellement, vous pouvez créer plusieurs implémentations d’IHostedService et les inscrire auprès de la méthode `ConfigureService()` dans le conteneur d’injection de dépendances, comme nous l’avons déjà indiqué.</span><span class="sxs-lookup"><span data-stu-id="9f363-144">As you can imagine, you can create multiple implementations of IHostedService and register them at the `ConfigureService()` method into the DI container, as shown previously.</span></span> <span data-ttu-id="9f363-145">Tous ces services hébergés démarrent et s’arrêtent avec l’application/le microservice.</span><span class="sxs-lookup"><span data-stu-id="9f363-145">All those hosted services will be started and stopped along with the application/microservice.</span></span>

<span data-ttu-id="9f363-146">En tant que développeur, vous êtes responsable de la prise en charge de l’action d’arrêt ou de vos services quand la méthode `StopAsync()` est déclenchée par l’hôte.</span><span class="sxs-lookup"><span data-stu-id="9f363-146">As a developer, you are responsible for handling the stopping action of your services when `StopAsync()` method is triggered by the host.</span></span>

## <a name="implementing-ihostedservice-with-a-custom-hosted-service-class-deriving-from-the-backgroundservice-base-class"></a><span data-ttu-id="9f363-147">Implémentation d’IHostedService avec une classe de service hébergé personnalisé dérivant de la classe de base BackgroundService</span><span class="sxs-lookup"><span data-stu-id="9f363-147">Implementing IHostedService with a custom hosted service class deriving from the BackgroundService base class</span></span>

<span data-ttu-id="9f363-148">Vous pouvez donc créer entièrement votre classe de service hébergé personnalisé, et implémentez `IHostedService`, comme vous le faites quand vous utilisez .NET Core 2.0.</span><span class="sxs-lookup"><span data-stu-id="9f363-148">You could go ahead and create your custom hosted service class from scratch and implement the `IHostedService`, as you need to do when using .NET Core 2.0.</span></span>

<span data-ttu-id="9f363-149">Toutefois, comme la plupart des tâches en arrière-plan ont des besoins similaires en ce qui concerne la gestion des jetons d’annulation et d’autres opérations classiques, il existe une classe de base abstraite pratique, nommée `BackgroundService` (disponible depuis .NET Core 2.1).</span><span class="sxs-lookup"><span data-stu-id="9f363-149">However, since most background tasks will have similar needs in regard to the cancellation tokens management and other typical operations, there is a convenient abstract base class you can derive from, named `BackgroundService` (available since .NET Core 2.1).</span></span>

<span data-ttu-id="9f363-150">Cette classe fournit le travail principal nécessaire à la configuration de la tâche en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="9f363-150">That class provides the main work needed to set up the background task.</span></span>

<span data-ttu-id="9f363-151">Le code suivant est la classe de base BackgroundService abstraite implémentée dans .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9f363-151">The next code is the abstract BackgroundService base class as implemented in .NET Core.</span></span>

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

<span data-ttu-id="9f363-152">Quand vous effectuez une dérivation à partir de la classe de base abstraite précédente, grâce à l’implémentation héritée, vous devez simplement implémenter la méthode `ExecuteAsync()` dans votre propre classe de service hébergé personnalisé, comme dans le code simplifié suivant d’eShopOnContainers. Ce code interroge une base de données et publie des événements d’intégration dans le bus d’événements, le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="9f363-152">When deriving from the previous abstract base class, thanks to that inherited implementation, you just need to implement the `ExecuteAsync()` method in your own custom hosted service class, as in the following simplified code from eShopOnContainers which is polling a database and publishing integration events into the Event Bus when needed.</span></span>

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

<span data-ttu-id="9f363-153">Dans ce cas de figure spécifique à eShopOnContainers, le code exécute une méthode d’application qui interroge une table de base de données à la recherche de commandes ayant un état spécifique. Quand des changements sont appliqués, il publie les événements d’intégration via le bus d’événements (il peut s’agir de RabbitMQ ou d’Azure Service Bus).</span><span class="sxs-lookup"><span data-stu-id="9f363-153">In this specific case for eShopOnContainers, it's executing an application method that's querying a database table looking for orders with a specific state and when applying changes, it is publishing integration events through the event bus (underneath it can be using RabbitMQ or Azure Service Bus).</span></span>

<span data-ttu-id="9f363-154">Bien entendu, vous pouvez exécuter une autre tâche en arrière-plan à la place.</span><span class="sxs-lookup"><span data-stu-id="9f363-154">Of course, you could run any other business background task, instead.</span></span>

<span data-ttu-id="9f363-155">Par défaut, le jeton d’annulation est défini avec un délai d’expiration de 5 secondes. Toutefois, vous pouvez changer cette valeur quand vous générez votre `WebHost` à l’aide de l’extension `UseShutdownTimeout` de `IWebHostBuilder`.</span><span class="sxs-lookup"><span data-stu-id="9f363-155">By default, the cancellation token is set with a 5 second timeout, although you can change that value when building your `WebHost` using the `UseShutdownTimeout` extension of the `IWebHostBuilder`.</span></span> <span data-ttu-id="9f363-156">Cela signifie que notre service est censé être annulé dans les 5 secondes, sinon il est tué de manière brusque.</span><span class="sxs-lookup"><span data-stu-id="9f363-156">This means that our service is expected to cancel within 5 seconds otherwise it will be more abruptly killed.</span></span>

<span data-ttu-id="9f363-157">Le code suivant change ce délai en le portant à 10 secondes.</span><span class="sxs-lookup"><span data-stu-id="9f363-157">The following code would be changing that time to 10 seconds.</span></span>

```csharp
WebHost.CreateDefaultBuilder(args)
    .UseShutdownTimeout(TimeSpan.FromSeconds(10))
    ...
```

### <a name="summary-class-diagram"></a><span data-ttu-id="9f363-158">Diagramme de classes récapitulatif</span><span class="sxs-lookup"><span data-stu-id="9f363-158">Summary class diagram</span></span>

<span data-ttu-id="9f363-159">L’image suivante montre un résumé visuel des classes et des interfaces impliquées dans la mise en œuvre d’IHostedServices.</span><span class="sxs-lookup"><span data-stu-id="9f363-159">The following image shows a visual summary of the classes and interfaces involved when implementing IHostedServices.</span></span>

![Diagramme montrant que IWebHost et IHost peuvent héberger de nombreux services.](./media/background-tasks-with-ihostedservice/class-diagram-custom-ihostedservice.png)

<span data-ttu-id="9f363-161">**Figure 6-27.**</span><span class="sxs-lookup"><span data-stu-id="9f363-161">**Figure 6-27**.</span></span> <span data-ttu-id="9f363-162">Diagramme de classes montrant les multiples classes et interfaces liées à IHostedService</span><span class="sxs-lookup"><span data-stu-id="9f363-162">Class diagram showing the multiple classes and interfaces related to IHostedService</span></span>

<span data-ttu-id="9f363-163">Diagramme de classes : IWebHost et IHost peuvent héberger de nombreux services, qui héritent de BackgroundService, lequel implémente IHostedService.</span><span class="sxs-lookup"><span data-stu-id="9f363-163">Class diagram: IWebHost and IHost can host many services, which inherit from BackgroundService, which implements IHostedService.</span></span>

### <a name="deployment-considerations-and-takeaways"></a><span data-ttu-id="9f363-164">Éléments importants à retenir et considérations relatives au déploiement</span><span class="sxs-lookup"><span data-stu-id="9f363-164">Deployment considerations and takeaways</span></span>

<span data-ttu-id="9f363-165">Il est important de noter que la façon dont vous déployez votre `WebHost` ASP.NET Core ou votre `Host` .NET Core peut avoir un impact sur la solution finale.</span><span class="sxs-lookup"><span data-stu-id="9f363-165">It is important to note that the way you deploy your ASP.NET Core `WebHost` or .NET Core `Host` might impact the final solution.</span></span> <span data-ttu-id="9f363-166">Par exemple, si vous déployez votre `WebHost` sur IIS ou sur un Azure App Service normal, votre hôte peut être arrêté en raison des recyclages de pools d’applications.</span><span class="sxs-lookup"><span data-stu-id="9f363-166">For instance, if you deploy your `WebHost` on IIS or a regular Azure App Service, your host can be shut down because of app pool recycles.</span></span> <span data-ttu-id="9f363-167">Mais si vous déployez votre hôte comme un conteneur dans un orchestrateur comme Kubernetes, vous pouvez contrôler le nombre assuré d’instances en direct de votre hôte.</span><span class="sxs-lookup"><span data-stu-id="9f363-167">But if you are deploying your host as a container into an orchestrator like Kubernetes, you can control the assured number of live instances of your host.</span></span> <span data-ttu-id="9f363-168">En outre, vous pouvez envisager d’autres approches liées au cloud, spécialement conçues pour ces scénarios, par exemple Azure Functions.</span><span class="sxs-lookup"><span data-stu-id="9f363-168">In addition, you could consider other approaches in the cloud especially made for these scenarios, like Azure Functions.</span></span> <span data-ttu-id="9f363-169">Enfin, si vous avez besoin que le service soit exécuté tout le temps et si vous déployez sur un serveur Windows, vous pouvez utiliser un service Windows.</span><span class="sxs-lookup"><span data-stu-id="9f363-169">Finally, if you need the service to be running all the time and are deploying on a Windows Server you could use a Windows Service.</span></span>

<span data-ttu-id="9f363-170">Mais même `WebHost` pour un déploiement dans un pool d’applications, il existe des scénarios comme le repeuplement ou le cache de rinçage de l’application de rinçage qui serait toujours applicable.</span><span class="sxs-lookup"><span data-stu-id="9f363-170">But even for a `WebHost` deployed into an app pool, there are scenarios like repopulating or flushing application's in-memory cache that would be still applicable.</span></span>

<span data-ttu-id="9f363-171">L’interface `IHostedService` fournit un moyen pratique de commencer des tâches d’arrière-plan dans une application web ASP.NET Core (en .NET Core 2.0 `IHost`et versions ultérieures) ou dans n’importe quel processus / hôte (à partir de .NET Core 2.1 avec ).</span><span class="sxs-lookup"><span data-stu-id="9f363-171">The `IHostedService` interface provides a convenient way to start background tasks in an ASP.NET Core web application (in .NET Core 2.0 and later versions) or in any process/host (starting in .NET Core 2.1 with `IHost`).</span></span> <span data-ttu-id="9f363-172">Le principal avantage est le suivant : grâce à l’annulation normale, vous pouvez nettoyer le code de vos tâches en arrière-plan quand l’hôte s’arrête.</span><span class="sxs-lookup"><span data-stu-id="9f363-172">Its main benefit is the opportunity you get with the graceful cancellation to clean-up code of your background tasks when the host itself is shutting down.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="9f363-173">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="9f363-173">Additional resources</span></span>

- <span data-ttu-id="9f363-174">**Construire une tâche prévue dans ASP.NET Core/Standard 2.0** </span><span class="sxs-lookup"><span data-stu-id="9f363-174">**Building a scheduled task in ASP.NET Core/Standard 2.0** </span></span>\
  <https://blog.maartenballiauw.be/post/2017/08/01/building-a-scheduled-cache-updater-in-aspnet-core-2.html>

- <span data-ttu-id="9f363-175">**Mise en œuvre de IHostedService dans ASP.NET Core 2.0** </span><span class="sxs-lookup"><span data-stu-id="9f363-175">**Implementing IHostedService in ASP.NET Core 2.0** </span></span>\
  <https://www.stevejgordon.co.uk/asp-net-core-2-ihostedservice>

- <span data-ttu-id="9f363-176">**GenericHost Échantillon à l’aide de ASP.NET Core 2.1** </span><span class="sxs-lookup"><span data-stu-id="9f363-176">**GenericHost Sample using ASP.NET Core 2.1** </span></span>\
  <https://github.com/aspnet/Hosting/tree/release/2.1/samples/GenericHostSample>

> [!div class="step-by-step"]
> <span data-ttu-id="9f363-177">[Suivant précédent](test-aspnet-core-services-web-apps.md)
> [Next](implement-api-gateways-with-ocelot.md)</span><span class="sxs-lookup"><span data-stu-id="9f363-177">[Previous](test-aspnet-core-services-web-apps.md)
[Next](implement-api-gateways-with-ocelot.md)</span></span>
