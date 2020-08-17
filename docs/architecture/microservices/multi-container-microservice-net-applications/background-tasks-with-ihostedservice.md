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
# <a name="implement-background-tasks-in-microservices-with-ihostedservice-and-the-backgroundservice-class"></a><span data-ttu-id="9e5f7-103">Implémenter des tâches en arrière-plan dans les microservices avec IHostedService et la classe BackgroundService</span><span class="sxs-lookup"><span data-stu-id="9e5f7-103">Implement background tasks in microservices with IHostedService and the BackgroundService class</span></span>

<span data-ttu-id="9e5f7-104">Les tâches en arrière-plan et les tâches planifiées sont des éléments que vous devrez peut-être utiliser dans n’importe quelle application, qu’elle respecte ou non le modèle d’architecture de microservices.</span><span class="sxs-lookup"><span data-stu-id="9e5f7-104">Background tasks and scheduled jobs are something you might need to use in any application, whether or not it follows the microservices architecture pattern.</span></span> <span data-ttu-id="9e5f7-105">La différence lors de l’utilisation d’une architecture de microservices est que vous pouvez implémenter la tâche en arrière-plan dans un processus/conteneur distinct pour l’hébergement, afin de pouvoir la mettre à l’échelle en fonction de vos besoins.</span><span class="sxs-lookup"><span data-stu-id="9e5f7-105">The difference when using a microservices architecture is that you can implement the background task in a separate process/container for hosting so you can scale it down/up based on your need.</span></span>

<span data-ttu-id="9e5f7-106">D’un point de vue générique, dans .NET Core, nous avons appelé les tâches de ce type *services hébergés*, car il s’agit de services/d’une logique que vous hébergez dans votre hôte/application/microservice.</span><span class="sxs-lookup"><span data-stu-id="9e5f7-106">From a generic point of view, in .NET Core we called these type of tasks *Hosted Services*, because they are services/logic that you host within your host/application/microservice.</span></span> <span data-ttu-id="9e5f7-107">Notez que dans ce cas, le service hébergé représente simplement une classe avec la logique de tâche en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="9e5f7-107">Note that in this case, the hosted service simply means a class with the background task logic.</span></span>

<span data-ttu-id="9e5f7-108">Depuis .NET Core 2.0, le framework fournit une nouvelle interface nommée <xref:Microsoft.Extensions.Hosting.IHostedService>, qui vous aide à implémenter facilement les services hébergés.</span><span class="sxs-lookup"><span data-stu-id="9e5f7-108">Since .NET Core 2.0, the framework provides a new interface named <xref:Microsoft.Extensions.Hosting.IHostedService> helping you to easily implement hosted services.</span></span> <span data-ttu-id="9e5f7-109">L’idée de base est que vous pouvez inscrire plusieurs tâches en arrière-plan (services hébergés) qui s’exécutent en arrière-plan pendant l’exécution de votre hôte ou hôte Web, comme illustré dans l’image 6-26.</span><span class="sxs-lookup"><span data-stu-id="9e5f7-109">The basic idea is that you can register multiple background tasks (hosted services) that run in the background while your web host or host is running, as shown in the image 6-26.</span></span>

![Diagramme comparant ASP.NET Core IWebHost et .NET Core IHost.](./media/background-tasks-with-ihostedservice/ihosted-service-webhost-vs-host.png)

<span data-ttu-id="9e5f7-111">**Figure 6-26.**</span><span class="sxs-lookup"><span data-stu-id="9e5f7-111">**Figure 6-26**.</span></span> <span data-ttu-id="9e5f7-112">Utilisation d’IHostedService dans un WebHost et un Host</span><span class="sxs-lookup"><span data-stu-id="9e5f7-112">Using IHostedService in a WebHost vs. a Host</span></span>

<span data-ttu-id="9e5f7-113">Prise en charge des ASP.NET Core 1. x et 2. x `IWebHost` pour les processus en arrière-plan dans les applications Web.</span><span class="sxs-lookup"><span data-stu-id="9e5f7-113">ASP.NET Core 1.x and 2.x support `IWebHost` for background processes in web apps.</span></span> <span data-ttu-id="9e5f7-114">.NET Core 2,1 et versions ultérieures prennent en charge `IHost` les processus en arrière-plan avec des applications de console simples.</span><span class="sxs-lookup"><span data-stu-id="9e5f7-114">.NET Core 2.1 and later versions support `IHost` for background processes with plain console apps.</span></span> <span data-ttu-id="9e5f7-115">Notez la différence faite entre `WebHost` et `Host`.</span><span class="sxs-lookup"><span data-stu-id="9e5f7-115">Note the difference made between `WebHost` and `Host`.</span></span>

<span data-ttu-id="9e5f7-116">Un `WebHost` (classe de base implémentant `IWebHost` ) dans ASP.net Core 2,0 est l’artefact d’infrastructure que vous utilisez pour fournir des fonctionnalités de serveur http à votre processus, par exemple quand vous implémentez une application Web MVC ou un service d’API Web.</span><span class="sxs-lookup"><span data-stu-id="9e5f7-116">A `WebHost` (base class implementing `IWebHost`) in ASP.NET Core 2.0 is the infrastructure artifact you use to provide HTTP server features to your process, such as when you're implementing an MVC web app or Web API service.</span></span> <span data-ttu-id="9e5f7-117">Il offre toutes les nouvelles opportunités en matière d’infrastructure dans ASP.NET Core, ce qui vous permet d’utiliser l’injection de dépendances, d’insérer des intergiciels dans le pipeline de demande et similaires.</span><span class="sxs-lookup"><span data-stu-id="9e5f7-117">It provides all the new infrastructure goodness in ASP.NET Core, enabling you to use dependency injection, insert middlewares in the request pipeline, and similar.</span></span> <span data-ttu-id="9e5f7-118">Le `WebHost` utilise les mêmes `IHostedServices` pour les tâches en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="9e5f7-118">The `WebHost` uses these very same `IHostedServices` for background tasks.</span></span>

<span data-ttu-id="9e5f7-119">Un `Host` (classe de base implémentant `IHost`) a été introduit dans .NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="9e5f7-119">A `Host` (base class implementing `IHost`) was introduced in .NET Core 2.1.</span></span> <span data-ttu-id="9e5f7-120">En fait, `Host` vous permet d’avoir une infrastructure similaire à celle que vous avez avec `WebHost` (injection de dépendances, services hébergés, etc.), mais dans ce cas précis, vous souhaitez simplement avoir un processus simple et plus léger en tant qu’hôte, sans lien avec les fonctionnalités MVC, d’API web ou de serveur HTTP.</span><span class="sxs-lookup"><span data-stu-id="9e5f7-120">Basically, a `Host` allows you to have a similar infrastructure than what you have with `WebHost` (dependency injection, hosted services, etc.), but in this case, you just want to have a simple and lighter process as the host, with nothing related to MVC, Web API or HTTP server features.</span></span>

<span data-ttu-id="9e5f7-121">Par conséquent, vous pouvez choisir et créer un processus hôte spécialisé avec `IHost` pour gérer les services hébergés et rien d’autre, tel qu’un microservice effectué uniquement pour héberger le `IHostedServices` , ou vous pouvez étendre une asp.net CORE existante `WebHost` , telle qu’une API Web ou une application MVC ASP.net CORE existante.</span><span class="sxs-lookup"><span data-stu-id="9e5f7-121">Therefore, you can choose and either create a specialized host-process with `IHost` to handle the hosted services and nothing else, such a microservice made just for hosting the `IHostedServices`, or you can alternatively extend an existing ASP.NET Core `WebHost`, such as an existing ASP.NET Core Web API or MVC app.</span></span>

<span data-ttu-id="9e5f7-122">Chaque approche a des avantages et des inconvénients selon vos besoins professionnels et de scalabilité.</span><span class="sxs-lookup"><span data-stu-id="9e5f7-122">Each approach has pros and cons depending on your business and scalability needs.</span></span> <span data-ttu-id="9e5f7-123">En gros, si vos tâches en arrière-plan n’ont rien à faire avec HTTP ( `IWebHost` ), vous devez utiliser `IHost` .</span><span class="sxs-lookup"><span data-stu-id="9e5f7-123">The bottom line is basically that if your background tasks have nothing to do with HTTP (`IWebHost`) you should use `IHost`.</span></span>

## <a name="registering-hosted-services-in-your-webhost-or-host"></a><span data-ttu-id="9e5f7-124">Inscription de services hébergés sur WebHost ou Host</span><span class="sxs-lookup"><span data-stu-id="9e5f7-124">Registering hosted services in your WebHost or Host</span></span>

<span data-ttu-id="9e5f7-125">Examinons plus en détail l' `IHostedService` interface, car son utilisation est assez similaire dans un `WebHost` ou dans un `Host` .</span><span class="sxs-lookup"><span data-stu-id="9e5f7-125">Let's drill down further on the `IHostedService` interface since its usage is pretty similar in a `WebHost` or in a `Host`.</span></span>

<span data-ttu-id="9e5f7-126">SignalR est un exemple d’artefact qui utilise des services hébergés, mais vous pouvez également l’employer pour des choses beaucoup plus simples, par exemple :</span><span class="sxs-lookup"><span data-stu-id="9e5f7-126">SignalR is one example of an artifact using hosted services, but you can also use it for much simpler things like:</span></span>

- <span data-ttu-id="9e5f7-127">Tâche en arrière-plan qui interroge une base de données à la recherche des changements survenus</span><span class="sxs-lookup"><span data-stu-id="9e5f7-127">A background task polling a database looking for changes.</span></span>
- <span data-ttu-id="9e5f7-128">Tâche planifiée qui met à jour un cache périodiquement</span><span class="sxs-lookup"><span data-stu-id="9e5f7-128">A scheduled task updating some cache periodically.</span></span>
- <span data-ttu-id="9e5f7-129">Implémentation de QueueBackgroundWorkItem qui permet l’exécution d’une tâche sur un thread d’arrière-plan</span><span class="sxs-lookup"><span data-stu-id="9e5f7-129">An implementation of QueueBackgroundWorkItem that allows a task to be executed on a background thread.</span></span>
- <span data-ttu-id="9e5f7-130">Traitement des messages d’une file d’attente de messages en arrière-plan d’une application web, avec un partage des services communs tels que `ILogger`</span><span class="sxs-lookup"><span data-stu-id="9e5f7-130">Processing messages from a message queue in the background of a web app while sharing common services such as `ILogger`.</span></span>
- <span data-ttu-id="9e5f7-131">Tâche en arrière-plan démarrée avec `Task.Run()`</span><span class="sxs-lookup"><span data-stu-id="9e5f7-131">A background task started with `Task.Run()`.</span></span>

<span data-ttu-id="9e5f7-132">Fondamentalement, vous pouvez décharger ces actions vers une tâche en arrière-plan qui implémente `IHostedService` .</span><span class="sxs-lookup"><span data-stu-id="9e5f7-132">You can basically offload any of those actions to a background task that implements `IHostedService`.</span></span>

<span data-ttu-id="9e5f7-133">La façon dont vous ajoutez un ou plusieurs `IHostedServices` à votre `WebHost` ou `Host` consiste à les inscrire à l’aide de la <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionHostedServiceExtensions.AddHostedService%2A>   méthode d’extension dans un ASP.net Core `WebHost` (ou dans un `Host` dans .net Core 2,1 et versions ultérieures).</span><span class="sxs-lookup"><span data-stu-id="9e5f7-133">The way you add one or multiple `IHostedServices` into your `WebHost` or `Host` is by registering them up through the <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionHostedServiceExtensions.AddHostedService%2A> extension method in an ASP.NET Core `WebHost` (or in a `Host` in .NET Core 2.1 and above).</span></span> <span data-ttu-id="9e5f7-134">En fait, vous devez inscrire les services hébergés dans la méthode `ConfigureServices()` bien connue de la classe `Startup`, comme dans le code suivant d’un WebHost ASP.NET classique.</span><span class="sxs-lookup"><span data-stu-id="9e5f7-134">Basically, you have to register the hosted services within the familiar `ConfigureServices()` method of the `Startup` class, as in the following code from a typical ASP.NET WebHost.</span></span>

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

<span data-ttu-id="9e5f7-135">Dans ce code, le service hébergé `GracePeriodManagerService` correspond au code réel du microservice de commandes d’eShopOnContainers, alors que les deux autres ne sont que deux exemples supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="9e5f7-135">In that code, the `GracePeriodManagerService` hosted service is real code from the Ordering business microservice in eShopOnContainers, while the other two are just two additional samples.</span></span>

<span data-ttu-id="9e5f7-136">L’exécution de la tâche en arrière-plan `IHostedService` est coordonnée avec la durée de vie de l’application (hôte ou microservice).</span><span class="sxs-lookup"><span data-stu-id="9e5f7-136">The `IHostedService` background task execution is coordinated with the lifetime of the application (host or microservice, for that matter).</span></span> <span data-ttu-id="9e5f7-137">Vous inscrivez des tâches quand l’application démarre, et vous pouvez effectuer des actions normales ou de nettoyage quand l’application s’arrête.</span><span class="sxs-lookup"><span data-stu-id="9e5f7-137">You register tasks when the application starts and you have the opportunity to do some graceful action or clean-up when the application is shutting down.</span></span>

<span data-ttu-id="9e5f7-138">Sans utiliser `IHostedService`, vous pouvez tout de même démarrer un thread d’arrière-plan pour exécuter une tâche.</span><span class="sxs-lookup"><span data-stu-id="9e5f7-138">Without using `IHostedService`, you could always start a background thread to run any task.</span></span> <span data-ttu-id="9e5f7-139">La différence est précisément au moment de l’arrêt de l’application lorsque ce thread est simplement supprimé sans avoir la possibilité d’exécuter des actions de nettoyage gracieuses.</span><span class="sxs-lookup"><span data-stu-id="9e5f7-139">The difference is precisely at the app's shutdown time when that thread would simply be killed without having the opportunity to run graceful clean-up actions.</span></span>

## <a name="the-ihostedservice-interface"></a><span data-ttu-id="9e5f7-140">Interface IHostedService</span><span class="sxs-lookup"><span data-stu-id="9e5f7-140">The IHostedService interface</span></span>

<span data-ttu-id="9e5f7-141">Quand vous inscrivez `IHostedService`, .NET Core appelle les méthodes `StartAsync()` et `StopAsync()` de votre type `IHostedService` durant le démarrage et l’arrêt de l’application, respectivement.</span><span class="sxs-lookup"><span data-stu-id="9e5f7-141">When you register an `IHostedService`, .NET Core will call the `StartAsync()` and `StopAsync()` methods of your `IHostedService` type during application start and stop respectively.</span></span> <span data-ttu-id="9e5f7-142">Pour plus d’informations, consultez [IHostedService interface](https://docs.microsoft.com/aspnet/core/fundamentals/host/hosted-services?view=aspnetcore-3.1&tabs=visual-studio#ihostedservice-interface) .</span><span class="sxs-lookup"><span data-stu-id="9e5f7-142">For more details, refer [IHostedService interface](https://docs.microsoft.com/aspnet/core/fundamentals/host/hosted-services?view=aspnetcore-3.1&tabs=visual-studio#ihostedservice-interface)</span></span>

<span data-ttu-id="9e5f7-143">Naturellement, vous pouvez créer plusieurs implémentations d’IHostedService et les inscrire auprès de la méthode `ConfigureService()` dans le conteneur d’injection de dépendances, comme nous l’avons déjà indiqué.</span><span class="sxs-lookup"><span data-stu-id="9e5f7-143">As you can imagine, you can create multiple implementations of IHostedService and register them at the `ConfigureService()` method into the DI container, as shown previously.</span></span> <span data-ttu-id="9e5f7-144">Tous ces services hébergés démarrent et s’arrêtent avec l’application/le microservice.</span><span class="sxs-lookup"><span data-stu-id="9e5f7-144">All those hosted services will be started and stopped along with the application/microservice.</span></span>

<span data-ttu-id="9e5f7-145">En tant que développeur, vous êtes responsable de la prise en charge de l’action d’arrêt ou de vos services quand la méthode `StopAsync()` est déclenchée par l’hôte.</span><span class="sxs-lookup"><span data-stu-id="9e5f7-145">As a developer, you are responsible for handling the stopping action of your services when `StopAsync()` method is triggered by the host.</span></span>

## <a name="implementing-ihostedservice-with-a-custom-hosted-service-class-deriving-from-the-backgroundservice-base-class"></a><span data-ttu-id="9e5f7-146">Implémentation d’IHostedService avec une classe de service hébergé personnalisé dérivant de la classe de base BackgroundService</span><span class="sxs-lookup"><span data-stu-id="9e5f7-146">Implementing IHostedService with a custom hosted service class deriving from the BackgroundService base class</span></span>

<span data-ttu-id="9e5f7-147">Vous pouvez donc créer entièrement votre classe de service hébergé personnalisé, et implémentez `IHostedService`, comme vous le faites quand vous utilisez .NET Core 2.0.</span><span class="sxs-lookup"><span data-stu-id="9e5f7-147">You could go ahead and create your custom hosted service class from scratch and implement the `IHostedService`, as you need to do when using .NET Core 2.0.</span></span>

<span data-ttu-id="9e5f7-148">Toutefois, comme la plupart des tâches en arrière-plan ont des besoins similaires en ce qui concerne la gestion des jetons d’annulation et d’autres opérations classiques, il existe une classe de base abstraite pratique, nommée `BackgroundService` (disponible depuis .NET Core 2.1).</span><span class="sxs-lookup"><span data-stu-id="9e5f7-148">However, since most background tasks will have similar needs in regard to the cancellation tokens management and other typical operations, there is a convenient abstract base class you can derive from, named `BackgroundService` (available since .NET Core 2.1).</span></span>

<span data-ttu-id="9e5f7-149">Cette classe fournit le travail principal nécessaire à la configuration de la tâche en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="9e5f7-149">That class provides the main work needed to set up the background task.</span></span>

<span data-ttu-id="9e5f7-150">Le code suivant est la classe de base BackgroundService abstraite implémentée dans .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9e5f7-150">The next code is the abstract BackgroundService base class as implemented in .NET Core.</span></span>

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

<span data-ttu-id="9e5f7-151">Quand vous effectuez une dérivation à partir de la classe de base abstraite précédente, grâce à l’implémentation héritée, vous devez simplement implémenter la méthode `ExecuteAsync()` dans votre propre classe de service hébergé personnalisé, comme dans le code simplifié suivant d’eShopOnContainers. Ce code interroge une base de données et publie des événements d’intégration dans le bus d’événements, le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="9e5f7-151">When deriving from the previous abstract base class, thanks to that inherited implementation, you just need to implement the `ExecuteAsync()` method in your own custom hosted service class, as in the following simplified code from eShopOnContainers which is polling a database and publishing integration events into the Event Bus when needed.</span></span>

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

<span data-ttu-id="9e5f7-152">Dans ce cas de figure spécifique à eShopOnContainers, le code exécute une méthode d’application qui interroge une table de base de données à la recherche de commandes ayant un état spécifique. Quand des changements sont appliqués, il publie les événements d’intégration via le bus d’événements (il peut s’agir de RabbitMQ ou d’Azure Service Bus).</span><span class="sxs-lookup"><span data-stu-id="9e5f7-152">In this specific case for eShopOnContainers, it's executing an application method that's querying a database table looking for orders with a specific state and when applying changes, it is publishing integration events through the event bus (underneath it can be using RabbitMQ or Azure Service Bus).</span></span>

<span data-ttu-id="9e5f7-153">Bien entendu, vous pouvez exécuter une autre tâche en arrière-plan à la place.</span><span class="sxs-lookup"><span data-stu-id="9e5f7-153">Of course, you could run any other business background task, instead.</span></span>

<span data-ttu-id="9e5f7-154">Par défaut, le jeton d’annulation est défini avec un délai d’expiration de 5 secondes, même si vous pouvez modifier cette valeur lors de `WebHost` la génération de votre à l’aide `UseShutdownTimeout` de l’extension de `IWebHostBuilder` .</span><span class="sxs-lookup"><span data-stu-id="9e5f7-154">By default, the cancellation token is set with a 5 seconds timeout, although you can change that value when building your `WebHost` using the `UseShutdownTimeout` extension of the `IWebHostBuilder`.</span></span> <span data-ttu-id="9e5f7-155">Cela signifie que notre service est censé être annulé dans les 5 secondes, sinon il est tué de manière brusque.</span><span class="sxs-lookup"><span data-stu-id="9e5f7-155">This means that our service is expected to cancel within 5 seconds otherwise it will be more abruptly killed.</span></span>

<span data-ttu-id="9e5f7-156">Le code suivant change ce délai en le portant à 10 secondes.</span><span class="sxs-lookup"><span data-stu-id="9e5f7-156">The following code would be changing that time to 10 seconds.</span></span>

```csharp
WebHost.CreateDefaultBuilder(args)
    .UseShutdownTimeout(TimeSpan.FromSeconds(10))
    ...
```

### <a name="summary-class-diagram"></a><span data-ttu-id="9e5f7-157">Diagramme de classes récapitulatif</span><span class="sxs-lookup"><span data-stu-id="9e5f7-157">Summary class diagram</span></span>

<span data-ttu-id="9e5f7-158">L’image suivante montre un résumé visuel des classes et des interfaces impliquées lors de l’implémentation de IHostedServices.</span><span class="sxs-lookup"><span data-stu-id="9e5f7-158">The following image shows a visual summary of the classes and interfaces involved when implementing IHostedServices.</span></span>

![Diagramme montrant que IWebHost et IHost peuvent héberger de nombreux services.](./media/background-tasks-with-ihostedservice/class-diagram-custom-ihostedservice.png)

<span data-ttu-id="9e5f7-160">**Figure 6-27.**</span><span class="sxs-lookup"><span data-stu-id="9e5f7-160">**Figure 6-27**.</span></span> <span data-ttu-id="9e5f7-161">Diagramme de classes montrant les multiples classes et interfaces liées à IHostedService</span><span class="sxs-lookup"><span data-stu-id="9e5f7-161">Class diagram showing the multiple classes and interfaces related to IHostedService</span></span>

<span data-ttu-id="9e5f7-162">Diagramme de classes : IWebHost et IHost peuvent héberger de nombreux services, qui héritent de BackgroundService, lequel implémente IHostedService.</span><span class="sxs-lookup"><span data-stu-id="9e5f7-162">Class diagram: IWebHost and IHost can host many services, which inherit from BackgroundService, which implements IHostedService.</span></span>

### <a name="deployment-considerations-and-takeaways"></a><span data-ttu-id="9e5f7-163">Éléments importants à retenir et considérations relatives au déploiement</span><span class="sxs-lookup"><span data-stu-id="9e5f7-163">Deployment considerations and takeaways</span></span>

<span data-ttu-id="9e5f7-164">Il est important de noter que la façon dont vous déployez votre `WebHost` ASP.NET Core ou votre `Host` .NET Core peut avoir un impact sur la solution finale.</span><span class="sxs-lookup"><span data-stu-id="9e5f7-164">It is important to note that the way you deploy your ASP.NET Core `WebHost` or .NET Core `Host` might impact the final solution.</span></span> <span data-ttu-id="9e5f7-165">Par exemple, si vous déployez votre `WebHost` sur IIS ou sur un Azure App Service normal, votre hôte peut être arrêté en raison des recyclages de pools d’applications.</span><span class="sxs-lookup"><span data-stu-id="9e5f7-165">For instance, if you deploy your `WebHost` on IIS or a regular Azure App Service, your host can be shut down because of app pool recycles.</span></span> <span data-ttu-id="9e5f7-166">Toutefois, si vous déployez votre hôte en tant que conteneur dans un orchestrateur comme Kubernetes, vous pouvez contrôler le nombre d’instances actives de votre hôte.</span><span class="sxs-lookup"><span data-stu-id="9e5f7-166">But if you are deploying your host as a container into an orchestrator like Kubernetes, you can control the assured number of live instances of your host.</span></span> <span data-ttu-id="9e5f7-167">En outre, vous pouvez envisager d’autres approches liées au cloud, spécialement conçues pour ces scénarios, par exemple Azure Functions.</span><span class="sxs-lookup"><span data-stu-id="9e5f7-167">In addition, you could consider other approaches in the cloud especially made for these scenarios, like Azure Functions.</span></span> <span data-ttu-id="9e5f7-168">Enfin, si vous avez besoin que le service soit exécuté tout le temps et si vous déployez sur un serveur Windows, vous pouvez utiliser un service Windows.</span><span class="sxs-lookup"><span data-stu-id="9e5f7-168">Finally, if you need the service to be running all the time and are deploying on a Windows Server you could use a Windows Service.</span></span>

<span data-ttu-id="9e5f7-169">Toutefois, même pour un `WebHost` déployé dans un pool d’applications, il existe des scénarios tels que le remplissage ou le vidage du cache en mémoire de l’application qui serait toujours applicable.</span><span class="sxs-lookup"><span data-stu-id="9e5f7-169">But even for a `WebHost` deployed into an app pool, there are scenarios like repopulating or flushing application's in-memory cache that would be still applicable.</span></span>

<span data-ttu-id="9e5f7-170">L' `IHostedService` interface offre un moyen pratique de démarrer des tâches en arrière-plan dans une application web ASP.net Core (dans .net core 2,0 et versions ultérieures) ou dans n’importe quel processus/hôte (à partir de .net core 2,1 avec `IHost` ).</span><span class="sxs-lookup"><span data-stu-id="9e5f7-170">The `IHostedService` interface provides a convenient way to start background tasks in an ASP.NET Core web application (in .NET Core 2.0 and later versions) or in any process/host (starting in .NET Core 2.1 with `IHost`).</span></span> <span data-ttu-id="9e5f7-171">Son principal avantage est l’opportunité que vous faites avec l’annulation appropriée pour nettoyer le code de vos tâches en arrière-plan lorsque l’ordinateur hôte est en cours d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="9e5f7-171">Its main benefit is the opportunity you get with the graceful cancellation to clean-up the code of your background tasks when the host itself is shutting down.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="9e5f7-172">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="9e5f7-172">Additional resources</span></span>

- <span data-ttu-id="9e5f7-173">**Création d’une tâche planifiée dans ASP.NET Core/standard 2,0** </span><span class="sxs-lookup"><span data-stu-id="9e5f7-173">**Building a scheduled task in ASP.NET Core/Standard 2.0** </span></span>\
  <https://blog.maartenballiauw.be/post/2017/08/01/building-a-scheduled-cache-updater-in-aspnet-core-2.html>

- <span data-ttu-id="9e5f7-174">**Implémentation de IHostedService dans ASP.NET Core 2,0** </span><span class="sxs-lookup"><span data-stu-id="9e5f7-174">**Implementing IHostedService in ASP.NET Core 2.0** </span></span>\
  <https://www.stevejgordon.co.uk/asp-net-core-2-ihostedservice>

- <span data-ttu-id="9e5f7-175">**Exemple GenericHost utilisant ASP.NET Core 2,1** </span><span class="sxs-lookup"><span data-stu-id="9e5f7-175">**GenericHost Sample using ASP.NET Core 2.1** </span></span>\
  <https://github.com/aspnet/Hosting/tree/release/2.1/samples/GenericHostSample>

> [!div class="step-by-step"]
> <span data-ttu-id="9e5f7-176">[Précédent](test-aspnet-core-services-web-apps.md) 
>  [Suivant](implement-api-gateways-with-ocelot.md)</span><span class="sxs-lookup"><span data-stu-id="9e5f7-176">[Previous](test-aspnet-core-services-web-apps.md)
[Next](implement-api-gateways-with-ocelot.md)</span></span>
