---
title: Injection de dépendances dans .NET
description: Découvrez comment .NET implémente l’injection de dépendances et comment l’utiliser.
author: IEvangelist
ms.author: dapine
ms.date: 10/28/2020
ms.topic: overview
ms.openlocfilehash: 2199f51ab13bedd50af747ce33ceee7b6eaefd8f
ms.sourcegitcommit: b1442669f1982d3a1cb18ea35b5acfb0fc7d93e4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93063146"
---
# <a name="dependency-injection-in-net"></a><span data-ttu-id="c479f-103">Injection de dépendances dans .NET</span><span class="sxs-lookup"><span data-stu-id="c479f-103">Dependency injection in .NET</span></span>

<span data-ttu-id="c479f-104">.NET prend en charge le modèle de conception de logiciels d’injection de dépendances, qui est une technique permettant d’obtenir une [inversion de contrôle (IOC, inversion of Control)](../../architecture/modern-web-apps-azure/architectural-principles.md#dependency-inversion) entre les classes et leurs dépendances.</span><span class="sxs-lookup"><span data-stu-id="c479f-104">.NET supports the dependency injection (DI) software design pattern, which is a technique for achieving [Inversion of Control (IoC)](../../architecture/modern-web-apps-azure/architectural-principles.md#dependency-inversion) between classes and their dependencies.</span></span> <span data-ttu-id="c479f-105">L’injection de dépendances dans .NET est un [citoyen de première classe](https://en.wikipedia.org/wiki/First-class_citizen), avec la configuration, la journalisation et le modèle d’options.</span><span class="sxs-lookup"><span data-stu-id="c479f-105">Dependency injection in .NET is a [first-class citizen](https://en.wikipedia.org/wiki/First-class_citizen), along with configuration, logging, and the options pattern.</span></span>

<span data-ttu-id="c479f-106">Une *dépendance* est un objet dont dépend un autre objet.</span><span class="sxs-lookup"><span data-stu-id="c479f-106">A *dependency* is an object that another object depends on.</span></span> <span data-ttu-id="c479f-107">Examinez la `MessageWriter` classe suivante avec une `Write` méthode dont dépendent d’autres classes :</span><span class="sxs-lookup"><span data-stu-id="c479f-107">Examine the following `MessageWriter` class with a `Write` method that other classes depend on:</span></span>

```csharp
public class MessageWriter
{
    public void Write(string message)
    {
        Console.WriteLine($"MessageWriter.Write(message: \"{message}\")");
    }
}
```

<span data-ttu-id="c479f-108">Une classe peut créer une instance de la `MessageWriter` classe pour utiliser sa `Write` méthode.</span><span class="sxs-lookup"><span data-stu-id="c479f-108">A class can create an instance of the `MessageWriter` class to make use of its `Write` method.</span></span> <span data-ttu-id="c479f-109">Dans l’exemple suivant, la `MessageWriter` classe est une dépendance de la `Worker` classe :</span><span class="sxs-lookup"><span data-stu-id="c479f-109">In the following example, the `MessageWriter` class is a dependency of the `Worker` class:</span></span>

```csharp
public class Worker : BackgroundService
{
    private readonly MessageWriter _messageWriter = new MessageWriter();

    protected override async Task ExecuteAsync(CancellationToken stoppingToken)
    {
        while (!stoppingToken.IsCancellationRequested)
        {
            _messageWriter.Write($"Worker running at: {DateTimeOffset.Now}");
            await Task.Delay(1000, stoppingToken);
        }
    }
}
```

<span data-ttu-id="c479f-110">La classe crée et dépend directement de la `MessageWriter` classe.</span><span class="sxs-lookup"><span data-stu-id="c479f-110">The class creates and directly depends on the `MessageWriter` class.</span></span> <span data-ttu-id="c479f-111">Les dépendances codées en dur, comme dans l’exemple précédent, sont problématiques et doivent être évitées pour les raisons suivantes :</span><span class="sxs-lookup"><span data-stu-id="c479f-111">Hard-coded dependencies, such as in the previous example, are problematic and should be avoided for the following reasons:</span></span>

- <span data-ttu-id="c479f-112">Pour remplacer `MessageWriter` par une implémentation différente, vous `MessageService` devez modifier la classe.</span><span class="sxs-lookup"><span data-stu-id="c479f-112">To replace `MessageWriter` with a different implementation, the `MessageService` class must be modified.</span></span>
- <span data-ttu-id="c479f-113">Si `MessageWriter` a des dépendances, ils doivent également être configurés par la `MessageService` classe.</span><span class="sxs-lookup"><span data-stu-id="c479f-113">If `MessageWriter` has dependencies, they must also be configured by the `MessageService` class.</span></span> <span data-ttu-id="c479f-114">Dans un grand projet comportant plusieurs classes dépendant de `MessageWriter`, le code de configuration est disséminé dans l’application.</span><span class="sxs-lookup"><span data-stu-id="c479f-114">In a large project with multiple classes depending on `MessageWriter`, the configuration code becomes scattered across the app.</span></span>
- <span data-ttu-id="c479f-115">Cette implémentation complique le test unitaire.</span><span class="sxs-lookup"><span data-stu-id="c479f-115">This implementation is difficult to unit test.</span></span> <span data-ttu-id="c479f-116">L’application doit utiliser une classe `MessageWriter` fictive ou stub, ce qui est impossible avec cette approche.</span><span class="sxs-lookup"><span data-stu-id="c479f-116">The app should use a mock or stub `MessageWriter` class, which isn't possible with this approach.</span></span>

<span data-ttu-id="c479f-117">L’injection de dépendances résout ces problèmes via :</span><span class="sxs-lookup"><span data-stu-id="c479f-117">Dependency injection addresses these problems through:</span></span>

- <span data-ttu-id="c479f-118">L’utilisation d’une interface ou classe de base pour extraire l’implémentation des dépendances.</span><span class="sxs-lookup"><span data-stu-id="c479f-118">The use of an interface or base class to abstract the dependency implementation.</span></span>
- <span data-ttu-id="c479f-119">L’inscription de la dépendance dans un conteneur de service.</span><span class="sxs-lookup"><span data-stu-id="c479f-119">Registration of the dependency in a service container.</span></span> <span data-ttu-id="c479f-120">.NET fournit un conteneur de service intégré, <xref:System.IServiceProvider> .</span><span class="sxs-lookup"><span data-stu-id="c479f-120">.NET provides a built-in service container, <xref:System.IServiceProvider>.</span></span> <span data-ttu-id="c479f-121">Les services sont généralement inscrits au démarrage de l’application et ajoutés à un <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection> .</span><span class="sxs-lookup"><span data-stu-id="c479f-121">Services are typically registered at the app's start-up, and appended to an <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection>.</span></span> <span data-ttu-id="c479f-122">Une fois tous les services ajoutés, vous utilisez <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionContainerBuilderExtensions.BuildServiceProvider%2A> pour créer le conteneur de service.</span><span class="sxs-lookup"><span data-stu-id="c479f-122">Once all services are added, you use <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionContainerBuilderExtensions.BuildServiceProvider%2A> to create the service container.</span></span>
- <span data-ttu-id="c479f-123">*Injection* du service dans le constructeur de la classe où il est utilisé.</span><span class="sxs-lookup"><span data-stu-id="c479f-123">*Injection* of the service into the constructor of the class where it's used.</span></span> <span data-ttu-id="c479f-124">Le framework prend la responsabilité de la création d’une instance de la dépendance et de sa suppression lorsqu’elle n’est plus nécessaire.</span><span class="sxs-lookup"><span data-stu-id="c479f-124">The framework takes on the responsibility of creating an instance of the dependency and disposing of it when it's no longer needed.</span></span>

<span data-ttu-id="c479f-125">Par exemple, l' `IMessageWriter` interface définit la `Write` méthode :</span><span class="sxs-lookup"><span data-stu-id="c479f-125">As an example, the `IMessageWriter` interface defines the `Write` method:</span></span>

:::code language="csharp" source="snippets/configuration/dependency-injection/IMessageWriter.cs":::

<span data-ttu-id="c479f-126">Cette interface est implémentée par un type concret, `MessageWriter` :</span><span class="sxs-lookup"><span data-stu-id="c479f-126">This interface is implemented by a concrete type, `MessageWriter`:</span></span>

:::code language="csharp" source="snippets/configuration/dependency-injection/MessageWriter.cs":::

<span data-ttu-id="c479f-127">L’exemple de code inscrit le `IMessageWriter` service avec le type concret `MessageWriter` .</span><span class="sxs-lookup"><span data-stu-id="c479f-127">The sample code registers the `IMessageWriter` service with the concrete type `MessageWriter`.</span></span> <span data-ttu-id="c479f-128">La <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionServiceExtensions.AddScoped%2A> méthode enregistre le service avec une durée de vie limitée, la durée de vie d’une requête unique.</span><span class="sxs-lookup"><span data-stu-id="c479f-128">The <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionServiceExtensions.AddScoped%2A> method registers the service with a scoped lifetime, the lifetime of a single request.</span></span> <span data-ttu-id="c479f-129">Les [durées de vie du service](#service-lifetimes) sont décrites plus loin dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="c479f-129">[Service lifetimes](#service-lifetimes) are described later in this topic.</span></span>

:::code language="csharp" source="snippets/configuration/dependency-injection/Program.cs" highlight="16":::

<span data-ttu-id="c479f-130">Dans l’exemple d’application, le `IMessageWriter` service est demandé et utilisé pour appeler la `Write` méthode :</span><span class="sxs-lookup"><span data-stu-id="c479f-130">In the sample app, the `IMessageWriter` service is requested and used to call the `Write` method:</span></span>

:::code language="csharp" source="snippets/configuration/dependency-injection/Worker.cs":::

<span data-ttu-id="c479f-131">En utilisant le modèle DI, le service Worker :</span><span class="sxs-lookup"><span data-stu-id="c479f-131">By using the DI pattern, the worker service:</span></span>

- <span data-ttu-id="c479f-132">N’utilise pas le type concret `MessageWriter` , mais uniquement l' `IMessageWriter` interface qui l’implémente.</span><span class="sxs-lookup"><span data-stu-id="c479f-132">Doesn't use the concrete type `MessageWriter`, only the `IMessageWriter` interface that implements it.</span></span> <span data-ttu-id="c479f-133">Cela facilite la modification de l’implémentation que le contrôleur utilise sans modifier le contrôleur.</span><span class="sxs-lookup"><span data-stu-id="c479f-133">That makes it easy to change the implementation that the controller uses without modifying the controller.</span></span>
- <span data-ttu-id="c479f-134">Ne crée pas d’instance de `MessageWriter` , elle est créée par le conteneur di.</span><span class="sxs-lookup"><span data-stu-id="c479f-134">Doesn't create an instance of `MessageWriter`, it's created by the DI container.</span></span>

<span data-ttu-id="c479f-135">L’implémentation de l' `IMessageWriter` interface peut être améliorée à l’aide de l’API de journalisation intégrée :</span><span class="sxs-lookup"><span data-stu-id="c479f-135">The implementation of the `IMessageWriter` interface can be improved by using the built-in logging API:</span></span>

:::code language="csharp" source="snippets/configuration/dependency-injection/LoggingMessageWriter.cs":::

<span data-ttu-id="c479f-136">La méthode mise à jour `ConfigureServices` inscrit la nouvelle `IMessageWriter` implémentation :</span><span class="sxs-lookup"><span data-stu-id="c479f-136">The updated `ConfigureServices` method registers the new `IMessageWriter` implementation:</span></span>

```csharp
static IHostBuilder CreateHostBuilder(string[] args) =>
    Host.CreateDefaultBuilder(args)
        .ConfigureServices((_, services) =>
            services.AddHostedService<Worker>()
                    .AddScoped<IMessageWriter, LoggingMessageWriter>());
```

<span data-ttu-id="c479f-137">`LoggingMessageWriter` dépend de <xref:Microsoft.Extensions.Logging.ILogger%601> , qu’il demande dans le constructeur.</span><span class="sxs-lookup"><span data-stu-id="c479f-137">`LoggingMessageWriter` depends on <xref:Microsoft.Extensions.Logging.ILogger%601>, which it requests in the constructor.</span></span> <span data-ttu-id="c479f-138">`ILogger<TCategoryName>` est un [service fourni par le Framework](#framework-provided-services).</span><span class="sxs-lookup"><span data-stu-id="c479f-138">`ILogger<TCategoryName>` is a [framework-provided service](#framework-provided-services).</span></span>

<span data-ttu-id="c479f-139">Il n’est pas rare que l’injection de dépendances soit utilisée de manière chaînée.</span><span class="sxs-lookup"><span data-stu-id="c479f-139">It's not unusual to use dependency injection in a chained fashion.</span></span> <span data-ttu-id="c479f-140">Dans ce cas, chaque dépendance demandée demande à son tour ses propres dépendances.</span><span class="sxs-lookup"><span data-stu-id="c479f-140">Each requested dependency in turn requests its own dependencies.</span></span> <span data-ttu-id="c479f-141">Le conteneur résout les dépendances dans le graphique et retourne le service entièrement résolu.</span><span class="sxs-lookup"><span data-stu-id="c479f-141">The container resolves the dependencies in the graph and returns the fully resolved service.</span></span> <span data-ttu-id="c479f-142">L’ensemble collectif de dépendances qui doivent être résolues est généralement appelé *arborescence des dépendances* , *graphique de dépendance* ou *graphique d’objet* .</span><span class="sxs-lookup"><span data-stu-id="c479f-142">The collective set of dependencies that must be resolved is typically referred to as a *dependency tree* , *dependency graph* , or *object graph* .</span></span>

<span data-ttu-id="c479f-143">Le conteneur se résout `ILogger<TCategoryName>` en tirant parti de [types ouverts (génériques)](/dotnet/csharp/language-reference/language-specification/types#open-and-closed-types), ce qui évite d’avoir à inscrire chaque [type construit (Générique)](/dotnet/csharp/language-reference/language-specification/types#constructed-types).</span><span class="sxs-lookup"><span data-stu-id="c479f-143">The container resolves `ILogger<TCategoryName>` by taking advantage of [(generic) open types](/dotnet/csharp/language-reference/language-specification/types#open-and-closed-types), eliminating the need to register every [(generic) constructed type](/dotnet/csharp/language-reference/language-specification/types#constructed-types).</span></span>

<span data-ttu-id="c479f-144">Dans la terminologie d’injection de dépendances, un service :</span><span class="sxs-lookup"><span data-stu-id="c479f-144">In dependency injection terminology, a service:</span></span>

- <span data-ttu-id="c479f-145">Est généralement un objet qui fournit un service à d’autres objets, tels que le `IMessageWriter` service.</span><span class="sxs-lookup"><span data-stu-id="c479f-145">Is typically an object that provides a service to other objects, such as the `IMessageWriter` service.</span></span>
- <span data-ttu-id="c479f-146">N’est pas associé à un service Web, bien que le service puisse utiliser un service Web.</span><span class="sxs-lookup"><span data-stu-id="c479f-146">Is not related to a web service, although the service may use a web service.</span></span>

<span data-ttu-id="c479f-147">Le Framework fournit un système de journalisation robuste.</span><span class="sxs-lookup"><span data-stu-id="c479f-147">The framework provides a robust logging system.</span></span> <span data-ttu-id="c479f-148">Les `IMessageWriter` implémentations présentées dans les exemples précédents ont été écrites pour illustrer la di de base, et non pour implémenter la journalisation.</span><span class="sxs-lookup"><span data-stu-id="c479f-148">The `IMessageWriter` implementations shown in the preceding examples were written to demonstrate basic DI, not to implement logging.</span></span> <span data-ttu-id="c479f-149">La plupart des applications n’ont pas besoin d’écrire des enregistreurs.</span><span class="sxs-lookup"><span data-stu-id="c479f-149">Most apps shouldn't need to write loggers.</span></span> <span data-ttu-id="c479f-150">Le code suivant illustre l’utilisation de la journalisation par défaut, qui nécessite uniquement l' `Worker` inscription de dans `ConfigureServices` en tant que service hébergé <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionHostedServiceExtensions.AddHostedService%2A> :</span><span class="sxs-lookup"><span data-stu-id="c479f-150">The following code demonstrates using the default logging, which only requires the `Worker` to be registered in `ConfigureServices` as a hosted service <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionHostedServiceExtensions.AddHostedService%2A>:</span></span>

```csharp
public class Worker : BackgroundService
{
    private readonly ILogger<Worker> _logger;

    public Worker(ILogger<Worker> logger) =>
        _logger = logger;

    protected override async Task ExecuteAsync(CancellationToken stoppingToken)
    {
        while (!stoppingToken.IsCancellationRequested)
        {
            _logger.LogInformation("Worker running at: {time}", DateTimeOffset.Now);
            await Task.Delay(1000, stoppingToken);
        }
    }
}
```

<span data-ttu-id="c479f-151">À l’aide du code précédent, il n’est pas nécessaire de mettre à jour `ConfigureServices` , car la journalisation est assurée par l’infrastructure.</span><span class="sxs-lookup"><span data-stu-id="c479f-151">Using the preceding code, there is no need to update `ConfigureServices`, because logging is provided by the framework.</span></span>

## <a name="register-groups-of-services-with-extension-methods"></a><span data-ttu-id="c479f-152">Inscrire des groupes de services avec des méthodes d’extension</span><span class="sxs-lookup"><span data-stu-id="c479f-152">Register groups of services with extension methods</span></span>

<span data-ttu-id="c479f-153">Les extensions Microsoft utilisent une convention pour l’enregistrement d’un groupe de services connexes.</span><span class="sxs-lookup"><span data-stu-id="c479f-153">Microsoft Extensions uses a convention for registering a group of related services.</span></span> <span data-ttu-id="c479f-154">La Convention consiste à utiliser une `Add{GROUP_NAME}` méthode d’extension unique pour inscrire tous les services requis par une fonctionnalité de l’infrastructure.</span><span class="sxs-lookup"><span data-stu-id="c479f-154">The convention is to use a single `Add{GROUP_NAME}` extension method to register all of the services required by a framework feature.</span></span> <span data-ttu-id="c479f-155">Par exemple, la <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.AddOptions%2A> méthode d’extension inscrit tous les services requis pour l’utilisation des options.</span><span class="sxs-lookup"><span data-stu-id="c479f-155">For example, the <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.AddOptions%2A> extension method registers all of the services required for using options.</span></span>

## <a name="framework-provided-services"></a><span data-ttu-id="c479f-156">Services fournis par le framework</span><span class="sxs-lookup"><span data-stu-id="c479f-156">Framework-provided services</span></span>

<span data-ttu-id="c479f-157">La `ConfigureServices` méthode enregistre les services utilisés par l’application, y compris les fonctionnalités de plateforme.</span><span class="sxs-lookup"><span data-stu-id="c479f-157">The `ConfigureServices` method registers services that the app uses, including platform features.</span></span> <span data-ttu-id="c479f-158">Initialement, le `IServiceCollection` fourni pour `ConfigureServices` possède des services définis par l’infrastructure en fonction de la [façon dont l’hôte a été configuré](generic-host.md#host-configuration).</span><span class="sxs-lookup"><span data-stu-id="c479f-158">Initially, the `IServiceCollection` provided to `ConfigureServices` has services defined by the framework depending on [how the host was configured](generic-host.md#host-configuration).</span></span> <span data-ttu-id="c479f-159">Pour les applications basées sur les modèles .NET, le Framework inscrit des centaines de services.</span><span class="sxs-lookup"><span data-stu-id="c479f-159">For apps based on the .NET templates, the framework registers hundreds of services.</span></span>

<span data-ttu-id="c479f-160">Le tableau suivant répertorie un petit exemple de ces services inscrits au Framework :</span><span class="sxs-lookup"><span data-stu-id="c479f-160">The following table lists a small sample of these framework-registered services:</span></span>

| <span data-ttu-id="c479f-161">Type de service</span><span class="sxs-lookup"><span data-stu-id="c479f-161">Service Type</span></span>                                                                       | <span data-ttu-id="c479f-162">Durée de vie</span><span class="sxs-lookup"><span data-stu-id="c479f-162">Lifetime</span></span>  |
|------------------------------------------------------------------------------------|-----------|
| <xref:Microsoft.Extensions.Hosting.IHostApplicationLifetime>                       | <span data-ttu-id="c479f-163">Singleton</span><span class="sxs-lookup"><span data-stu-id="c479f-163">Singleton</span></span> |
| <xref:Microsoft.Extensions.Logging.ILogger%601?displayProperty=fullName>           | <span data-ttu-id="c479f-164">Singleton</span><span class="sxs-lookup"><span data-stu-id="c479f-164">Singleton</span></span> |
| <xref:Microsoft.Extensions.Logging.ILoggerFactory?displayProperty=fullName>        | <span data-ttu-id="c479f-165">Singleton</span><span class="sxs-lookup"><span data-stu-id="c479f-165">Singleton</span></span> |
| <xref:Microsoft.Extensions.ObjectPool.ObjectPoolProvider?displayProperty=fullName> | <span data-ttu-id="c479f-166">Singleton</span><span class="sxs-lookup"><span data-stu-id="c479f-166">Singleton</span></span> |
| <xref:Microsoft.Extensions.Options.IConfigureOptions%601?displayProperty=fullName> | <span data-ttu-id="c479f-167">Temporaire</span><span class="sxs-lookup"><span data-stu-id="c479f-167">Transient</span></span> |
| <xref:Microsoft.Extensions.Options.IOptions%601?displayProperty=fullName>          | <span data-ttu-id="c479f-168">Singleton</span><span class="sxs-lookup"><span data-stu-id="c479f-168">Singleton</span></span> |
| <xref:System.Diagnostics.DiagnosticListener?displayProperty=fullName>              | <span data-ttu-id="c479f-169">Singleton</span><span class="sxs-lookup"><span data-stu-id="c479f-169">Singleton</span></span> |
| <xref:System.Diagnostics.DiagnosticSource?displayProperty=fullName>                | <span data-ttu-id="c479f-170">Singleton</span><span class="sxs-lookup"><span data-stu-id="c479f-170">Singleton</span></span> |

## <a name="service-lifetimes"></a><span data-ttu-id="c479f-171">Durées de service</span><span class="sxs-lookup"><span data-stu-id="c479f-171">Service lifetimes</span></span>

<span data-ttu-id="c479f-172">Les services peuvent être enregistrés avec l’une des durées de vie suivantes :</span><span class="sxs-lookup"><span data-stu-id="c479f-172">Services can be registered with one of the following lifetimes:</span></span>

- <span data-ttu-id="c479f-173">Temporaire</span><span class="sxs-lookup"><span data-stu-id="c479f-173">Transient</span></span>
- <span data-ttu-id="c479f-174">Délimité</span><span class="sxs-lookup"><span data-stu-id="c479f-174">Scoped</span></span>
- <span data-ttu-id="c479f-175">Singleton</span><span class="sxs-lookup"><span data-stu-id="c479f-175">Singleton</span></span>

<span data-ttu-id="c479f-176">Les sections suivantes décrivent chacune des durées de vie précédentes.</span><span class="sxs-lookup"><span data-stu-id="c479f-176">The following sections describe each of the preceding lifetimes.</span></span> <span data-ttu-id="c479f-177">Choisissez une durée de vie appropriée pour chaque service inscrit.</span><span class="sxs-lookup"><span data-stu-id="c479f-177">Choose an appropriate lifetime for each registered service.</span></span>

### <a name="transient"></a><span data-ttu-id="c479f-178">Temporaire</span><span class="sxs-lookup"><span data-stu-id="c479f-178">Transient</span></span>

<span data-ttu-id="c479f-179">Des services à durée de vie temporaire (Transient) sont créés chaque fois qu’ils sont demandés à partir du conteneur de service.</span><span class="sxs-lookup"><span data-stu-id="c479f-179">Transient lifetime services are created each time they're requested from the service container.</span></span> <span data-ttu-id="c479f-180">Cette durée de vie convient parfaitement aux services légers et sans état.</span><span class="sxs-lookup"><span data-stu-id="c479f-180">This lifetime works best for lightweight, stateless services.</span></span> <span data-ttu-id="c479f-181">Inscrire des services temporaires avec <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionServiceExtensions.AddTransient%2A> .</span><span class="sxs-lookup"><span data-stu-id="c479f-181">Register transient services with <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionServiceExtensions.AddTransient%2A>.</span></span>

<span data-ttu-id="c479f-182">Dans les applications qui traitent les demandes, les services transitoires sont supprimés à la fin de la demande.</span><span class="sxs-lookup"><span data-stu-id="c479f-182">In apps that process requests, transient services are disposed at the end of the request.</span></span>

### <a name="scoped"></a><span data-ttu-id="c479f-183">Délimité</span><span class="sxs-lookup"><span data-stu-id="c479f-183">Scoped</span></span>

<span data-ttu-id="c479f-184">Pour les applications Web, une durée de vie limitée indique que les services sont créés une seule fois par demande du client (connexion).</span><span class="sxs-lookup"><span data-stu-id="c479f-184">For web applications a scoped lifetime indicates that services are created once per client request (connection).</span></span> <span data-ttu-id="c479f-185">Inscrire les services délimités avec <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionServiceExtensions.AddScoped%2A> .</span><span class="sxs-lookup"><span data-stu-id="c479f-185">Register scoped services with <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionServiceExtensions.AddScoped%2A>.</span></span>

<span data-ttu-id="c479f-186">Dans les applications qui traitent les requêtes, les services délimités sont supprimés à la fin de la demande.</span><span class="sxs-lookup"><span data-stu-id="c479f-186">In apps that process requests, scoped services are disposed at the end of the request.</span></span>

<span data-ttu-id="c479f-187">Lors de l’utilisation de Entity Framework Core, la <xref:Microsoft.Extensions.DependencyInjection.EntityFrameworkServiceCollectionExtensions.AddDbContext%2A> méthode d’extension inscrit les `DbContext` types avec une durée de vie limitée par défaut.</span><span class="sxs-lookup"><span data-stu-id="c479f-187">When using Entity Framework Core, the <xref:Microsoft.Extensions.DependencyInjection.EntityFrameworkServiceCollectionExtensions.AddDbContext%2A> extension method registers `DbContext` types with a scoped lifetime by default.</span></span>

> [!NOTE]
> <span data-ttu-id="c479f-188">Do \* **not** _ résoudre un service étendu à partir d’un singleton et veiller à ne pas le faire indirectement, par exemple via un service temporaire.</span><span class="sxs-lookup"><span data-stu-id="c479f-188">Do \* **not** _ resolve a scoped service from a singleton and be careful not to do so indirectly, for example, through a transient service.</span></span> <span data-ttu-id="c479f-189">L’état du service risque de ne pas être correct lors du traitement des requêtes suivantes.</span><span class="sxs-lookup"><span data-stu-id="c479f-189">It may cause the service to have incorrect state when processing subsequent requests.</span></span> <span data-ttu-id="c479f-190">Il convient d’effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="c479f-190">It's fine to:</span></span>
>
> - <span data-ttu-id="c479f-191">Résoudre un service Singleton à partir d’un service délimité ou étendu.</span><span class="sxs-lookup"><span data-stu-id="c479f-191">Resolve a singleton service from a scoped or transient service.</span></span>
> - <span data-ttu-id="c479f-192">Résoudre un service étendu à partir d’un autre service étendu ou temporaire.</span><span class="sxs-lookup"><span data-stu-id="c479f-192">Resolve a scoped service from another scoped or transient service.</span></span>

<span data-ttu-id="c479f-193">Par défaut, dans l’environnement de développement, la résolution d’un service à partir d’un autre service avec une durée de vie plus longue lève une exception.</span><span class="sxs-lookup"><span data-stu-id="c479f-193">By default, in the development environment, resolving a service from another service with a longer lifetime throws an exception.</span></span> <span data-ttu-id="c479f-194">Pour plus d’informations, consultez [Validation de l’étendue](#scope-validation).</span><span class="sxs-lookup"><span data-stu-id="c479f-194">For more information, see [Scope validation](#scope-validation).</span></span>

### <a name="singleton"></a><span data-ttu-id="c479f-195">Singleton</span><span class="sxs-lookup"><span data-stu-id="c479f-195">Singleton</span></span>

<span data-ttu-id="c479f-196">Les services de durée de vie Singleton sont créés :</span><span class="sxs-lookup"><span data-stu-id="c479f-196">Singleton lifetime services are created either:</span></span>

- <span data-ttu-id="c479f-197">La première fois qu’ils sont demandés.</span><span class="sxs-lookup"><span data-stu-id="c479f-197">The first time they're requested.</span></span>
- <span data-ttu-id="c479f-198">Par le développeur, lors de la fourniture d’une instance d’implémentation directement au conteneur.</span><span class="sxs-lookup"><span data-stu-id="c479f-198">By the developer, when providing an implementation instance directly to the container.</span></span> <span data-ttu-id="c479f-199">Cette approche est rarement nécessaire.</span><span class="sxs-lookup"><span data-stu-id="c479f-199">This approach is rarely needed.</span></span>

<span data-ttu-id="c479f-200">Chaque demande ultérieure de l’implémentation de service à partir du conteneur d’injection de dépendances utilise la même instance.</span><span class="sxs-lookup"><span data-stu-id="c479f-200">Every subsequent request of the service implementation from the dependency injection container uses the same instance.</span></span> <span data-ttu-id="c479f-201">Si l’application requiert un comportement Singleton, autorisez le conteneur de service à gérer la durée de vie du service.</span><span class="sxs-lookup"><span data-stu-id="c479f-201">If the app requires singleton behavior, allow the service container to manage the service's lifetime.</span></span> <span data-ttu-id="c479f-202">N’implémentez pas le modèle de conception Singleton et fournissez du code pour supprimer le singleton.</span><span class="sxs-lookup"><span data-stu-id="c479f-202">Don't implement the singleton design pattern and provide code to dispose of the singleton.</span></span> <span data-ttu-id="c479f-203">Les services ne doivent jamais être supprimés par du code qui a résolu le service à partir du conteneur.</span><span class="sxs-lookup"><span data-stu-id="c479f-203">Services should never be disposed by code that resolved the service from the container.</span></span> <span data-ttu-id="c479f-204">Si un type ou une fabrique est inscrit en tant que singleton, le conteneur supprime automatiquement le singleton.</span><span class="sxs-lookup"><span data-stu-id="c479f-204">If a type or factory is registered as a singleton, the container disposes the singleton automatically.</span></span>

<span data-ttu-id="c479f-205">Inscrire des services Singleton avec <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionServiceExtensions.AddSingleton%2A> .</span><span class="sxs-lookup"><span data-stu-id="c479f-205">Register singleton services with <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionServiceExtensions.AddSingleton%2A>.</span></span> <span data-ttu-id="c479f-206">Les services Singleton doivent être thread-safe et sont souvent utilisés dans les services sans État.</span><span class="sxs-lookup"><span data-stu-id="c479f-206">Singleton services must be thread safe and are often used in stateless services.</span></span>

<span data-ttu-id="c479f-207">Dans les applications qui traitent les requêtes, les services Singleton sont supprimés lorsque le <xref:Microsoft.Extensions.DependencyInjection.ServiceProvider> est supprimé lors de l’arrêt de l’application.</span><span class="sxs-lookup"><span data-stu-id="c479f-207">In apps that process requests, singleton services are disposed when the <xref:Microsoft.Extensions.DependencyInjection.ServiceProvider> is disposed on application shutdown.</span></span> <span data-ttu-id="c479f-208">Étant donné que la mémoire n’est pas libérée tant que l’application n’est pas arrêtée, envisagez d’utiliser la mémoire avec un service Singleton.</span><span class="sxs-lookup"><span data-stu-id="c479f-208">Because memory is not released until the app is shut down, consider memory use with a singleton service.</span></span>

> [!WARNING]
> <span data-ttu-id="c479f-209">Ne résolvez _*_pas_*_ un service étendu à partir d’un singleton.</span><span class="sxs-lookup"><span data-stu-id="c479f-209">Do _*_not_*_ resolve a scoped service from a singleton.</span></span> <span data-ttu-id="c479f-210">L’état du service risque de ne pas être correct lors du traitement des requêtes suivantes.</span><span class="sxs-lookup"><span data-stu-id="c479f-210">It may cause the service to have incorrect state when processing subsequent requests.</span></span> <span data-ttu-id="c479f-211">Il est parfait de résoudre un service Singleton à partir d’un service étendu ou temporaire.</span><span class="sxs-lookup"><span data-stu-id="c479f-211">It's fine to resolve a singleton service from a scoped or transient service.</span></span>

## <a name="service-registration-methods"></a><span data-ttu-id="c479f-212">Méthodes d’inscription du service</span><span class="sxs-lookup"><span data-stu-id="c479f-212">Service registration methods</span></span>

<span data-ttu-id="c479f-213">Le Framework fournit des méthodes d’extension d’inscription de service qui sont utiles dans des scénarios spécifiques :</span><span class="sxs-lookup"><span data-stu-id="c479f-213">The framework provides service registration extension methods that are useful in specific scenarios:</span></span>

| <span data-ttu-id="c479f-214">Méthode</span><span class="sxs-lookup"><span data-stu-id="c479f-214">Method</span></span> | <span data-ttu-id="c479f-215">Automatique</span><span class="sxs-lookup"><span data-stu-id="c479f-215">Automatic</span></span><br><span data-ttu-id="c479f-216">object</span><span class="sxs-lookup"><span data-stu-id="c479f-216">object</span></span><br><span data-ttu-id="c479f-217">suppression</span><span class="sxs-lookup"><span data-stu-id="c479f-217">disposal</span></span> | <span data-ttu-id="c479f-218">Multiple</span><span class="sxs-lookup"><span data-stu-id="c479f-218">Multiple</span></span><br><span data-ttu-id="c479f-219">implémentations</span><span class="sxs-lookup"><span data-stu-id="c479f-219">implementations</span></span> | <span data-ttu-id="c479f-220">Passage d’args</span><span class="sxs-lookup"><span data-stu-id="c479f-220">Pass args</span></span> |
|--|:-:|:-:|:-:|
| `Add{LIFETIME}<{SERVICE}, {IMPLEMENTATION}>()`<br><br><span data-ttu-id="c479f-221">Exemple :</span><span class="sxs-lookup"><span data-stu-id="c479f-221">Example:</span></span><br><br>`services.AddSingleton<IMyDep, MyDep>();` | <span data-ttu-id="c479f-222">Oui</span><span class="sxs-lookup"><span data-stu-id="c479f-222">Yes</span></span> | <span data-ttu-id="c479f-223">Oui</span><span class="sxs-lookup"><span data-stu-id="c479f-223">Yes</span></span> | <span data-ttu-id="c479f-224">Non</span><span class="sxs-lookup"><span data-stu-id="c479f-224">No</span></span> |
| `Add{LIFETIME}<{SERVICE}>(sp => new {IMPLEMENTATION})`<br><br><span data-ttu-id="c479f-225">Exemples :</span><span class="sxs-lookup"><span data-stu-id="c479f-225">Examples:</span></span><br><br>`services.AddSingleton<IMyDep>(sp => new MyDep());`<br>`services.AddSingleton<IMyDep>(sp => new MyDep(99));` | <span data-ttu-id="c479f-226">Oui</span><span class="sxs-lookup"><span data-stu-id="c479f-226">Yes</span></span> | <span data-ttu-id="c479f-227">Oui</span><span class="sxs-lookup"><span data-stu-id="c479f-227">Yes</span></span> | <span data-ttu-id="c479f-228">Oui</span><span class="sxs-lookup"><span data-stu-id="c479f-228">Yes</span></span> |
| `Add{LIFETIME}<{IMPLEMENTATION}>()`<br><br><span data-ttu-id="c479f-229">Exemple :</span><span class="sxs-lookup"><span data-stu-id="c479f-229">Example:</span></span><br><br>`services.AddSingleton<MyDep>();` | <span data-ttu-id="c479f-230">Oui</span><span class="sxs-lookup"><span data-stu-id="c479f-230">Yes</span></span> | <span data-ttu-id="c479f-231">Non</span><span class="sxs-lookup"><span data-stu-id="c479f-231">No</span></span> | <span data-ttu-id="c479f-232">Non</span><span class="sxs-lookup"><span data-stu-id="c479f-232">No</span></span> |
| `AddSingleton<{SERVICE}>(new {IMPLEMENTATION})`<br><br><span data-ttu-id="c479f-233">Exemples :</span><span class="sxs-lookup"><span data-stu-id="c479f-233">Examples:</span></span><br><br>`services.AddSingleton<IMyDep>(new MyDep());`<br>`services.AddSingleton<IMyDep>(new MyDep(99));` | <span data-ttu-id="c479f-234">Non</span><span class="sxs-lookup"><span data-stu-id="c479f-234">No</span></span> | <span data-ttu-id="c479f-235">Oui</span><span class="sxs-lookup"><span data-stu-id="c479f-235">Yes</span></span> | <span data-ttu-id="c479f-236">Oui</span><span class="sxs-lookup"><span data-stu-id="c479f-236">Yes</span></span> |
| `AddSingleton(new {IMPLEMENTATION})`<br><br><span data-ttu-id="c479f-237">Exemples :</span><span class="sxs-lookup"><span data-stu-id="c479f-237">Examples:</span></span><br><br>`services.AddSingleton(new MyDep());`<br>`services.AddSingleton(new MyDep(99));` | <span data-ttu-id="c479f-238">Non</span><span class="sxs-lookup"><span data-stu-id="c479f-238">No</span></span> | <span data-ttu-id="c479f-239">Non</span><span class="sxs-lookup"><span data-stu-id="c479f-239">No</span></span> | <span data-ttu-id="c479f-240">Oui</span><span class="sxs-lookup"><span data-stu-id="c479f-240">Yes</span></span> |

<span data-ttu-id="c479f-241">Pour plus d’informations sur la suppression de type, consultez la section [Suppression des services](dependency-injection-guidelines.md#disposal-of-services).</span><span class="sxs-lookup"><span data-stu-id="c479f-241">For more information on type disposal, see the [Disposal of services](dependency-injection-guidelines.md#disposal-of-services) section.</span></span>

<span data-ttu-id="c479f-242">L’inscription d’un service avec un seul type d’implémentation équivaut à inscrire ce service avec le même type de service et l’implémentation.</span><span class="sxs-lookup"><span data-stu-id="c479f-242">Registering a service with only an implementation type is equivalent to registering that service with the same implementation and service type.</span></span> <span data-ttu-id="c479f-243">C’est pourquoi plusieurs implémentations d’un service ne peuvent pas être inscrites à l’aide des méthodes qui n’acceptent pas un type de service explicite.</span><span class="sxs-lookup"><span data-stu-id="c479f-243">This is why multiple implementations of a service cannot be registered using the methods that don't take an explicit service type.</span></span> <span data-ttu-id="c479f-244">Ces méthodes peuvent inscrire plusieurs _instances \* d’un service, mais elles auront toutes le même type d' *implémentation* .</span><span class="sxs-lookup"><span data-stu-id="c479f-244">These methods can register multiple _instances\* of a service, but they will all have the same *implementation* type.</span></span>

<span data-ttu-id="c479f-245">L’une des méthodes d’inscription de service ci-dessus peut être utilisée pour inscrire plusieurs instances de service du même type de service.</span><span class="sxs-lookup"><span data-stu-id="c479f-245">Any of the above service registration methods can be used to register multiple service instances of the same service type.</span></span> <span data-ttu-id="c479f-246">Dans l’exemple suivant, `AddSingleton` est appelé deux fois avec `IMessageWriter` comme type de service.</span><span class="sxs-lookup"><span data-stu-id="c479f-246">In the following example, `AddSingleton` is called twice with `IMessageWriter` as the service type.</span></span> <span data-ttu-id="c479f-247">Le deuxième appel à `AddSingleton` remplace le précédent lorsqu’il est résolu en tant que `IMessageWriter` et ajoute au précédent lorsque plusieurs services sont résolus via `IEnumerable<IMessageWriter>` .</span><span class="sxs-lookup"><span data-stu-id="c479f-247">The second call to `AddSingleton` overrides the previous one when resolved as `IMessageWriter` and adds to the previous one when multiple services are resolved via `IEnumerable<IMessageWriter>`.</span></span> <span data-ttu-id="c479f-248">Les services s’affichent dans l’ordre dans lequel ils ont été inscrits lorsqu’ils sont résolus via `IEnumerable<{SERVICE}>` .</span><span class="sxs-lookup"><span data-stu-id="c479f-248">Services appear in the order they were registered when resolved via `IEnumerable<{SERVICE}>`.</span></span>

:::code language="csharp" source="snippets/configuration/console-di-ienumerable/Program.cs" highlight="19-24":::

<span data-ttu-id="c479f-249">L’exemple de code source précédent inscrit deux implémentations du `IMessageWriter` .</span><span class="sxs-lookup"><span data-stu-id="c479f-249">The preceding sample source code registers two implementations of the `IMessageWriter`.</span></span>

:::code language="csharp" source="snippets/configuration/console-di-ienumerable/ExampleService.cs" highlight="9-18":::

<span data-ttu-id="c479f-250">`ExampleService`Définit deux paramètres de constructeur, un unique `IMessageWriter` et un `IEnumerable<IMessageWriter>` .</span><span class="sxs-lookup"><span data-stu-id="c479f-250">The `ExampleService` defines two constructor parameters; a single `IMessageWriter`, and an `IEnumerable<IMessageWriter>`.</span></span> <span data-ttu-id="c479f-251">Le seul `IMessageWriter` est le dernier implémentation à être enregistré, tandis que `IEnumerable<IMessageWriter>` représente toutes les implémentations inscrites.</span><span class="sxs-lookup"><span data-stu-id="c479f-251">The single `IMessageWriter` is the last implemenation to have been registered, whereas the `IEnumerable<IMessageWriter>` represents all registered implementations.</span></span>

<span data-ttu-id="c479f-252">Le Framework fournit également des `TryAdd{LIFETIME}` méthodes d’extension, qui inscrivent le service uniquement si aucune implémentation n’est déjà inscrite.</span><span class="sxs-lookup"><span data-stu-id="c479f-252">The framework also provides `TryAdd{LIFETIME}` extension methods, which register the service only if there isn't already an implementation registered.</span></span>

<span data-ttu-id="c479f-253">Dans l’exemple suivant, l’appel à `AddSingleton` s’inscrit `ConsoleMessageWriter` en tant qu’implémentation de `IMessageWriter` .</span><span class="sxs-lookup"><span data-stu-id="c479f-253">In the following example, the call to `AddSingleton` registers `ConsoleMessageWriter` as an implementation for `IMessageWriter`.</span></span> <span data-ttu-id="c479f-254">L’appel à n' `TryAddSingleton` a aucun effet, car `IMessageWriter` a déjà une implémentation inscrite :</span><span class="sxs-lookup"><span data-stu-id="c479f-254">The call to `TryAddSingleton` has no effect because `IMessageWriter` already has a registered implementation:</span></span>

```csharp
services.AddSingleton<IMessageWriter, ConsoleMessageWriter>();
services.TryAddSingleton<IMessageWriter, LoggingMessageWriter>();
```

<span data-ttu-id="c479f-255">Le n' `TryAddSingleton` a aucun effet, car il a déjà été ajouté et le « try » échoue.</span><span class="sxs-lookup"><span data-stu-id="c479f-255">The `TryAddSingleton` has no effect, as it was already added and the "try" will fail.</span></span> <span data-ttu-id="c479f-256">Le `ExampleService` déclarerait les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="c479f-256">The `ExampleService` would assert the following:</span></span>

```csharp
public class ExampleService
{
    public ExampleService(
        IMessageWriter messageWriter,
        IEnumerable<IMessageWriter> messageWriters)
    {
        Trace.Assert(messageWriter is ConsoleMessageWriter);
        Trace.Assert(messageWriters.Single() is ConsoleMessageWriter);
    }
}
```

<span data-ttu-id="c479f-257">Pour plus d'informations, consultez les pages suivantes :</span><span class="sxs-lookup"><span data-stu-id="c479f-257">For more information, see:</span></span>

- <xref:Microsoft.Extensions.DependencyInjection.Extensions.ServiceCollectionDescriptorExtensions.TryAdd%2A>
- <xref:Microsoft.Extensions.DependencyInjection.Extensions.ServiceCollectionDescriptorExtensions.TryAddTransient%2A>
- <xref:Microsoft.Extensions.DependencyInjection.Extensions.ServiceCollectionDescriptorExtensions.TryAddScoped%2A>
- <xref:Microsoft.Extensions.DependencyInjection.Extensions.ServiceCollectionDescriptorExtensions.TryAddSingleton%2A>

<span data-ttu-id="c479f-258">Les méthodes [TryAddEnumerable (ServiceDescriptor)](xref:Microsoft.Extensions.DependencyInjection.Extensions.ServiceCollectionDescriptorExtensions.TryAddEnumerable%2A) inscrivent le service uniquement s’il n’existe pas déjà une implémentation *du même type* .</span><span class="sxs-lookup"><span data-stu-id="c479f-258">The [TryAddEnumerable(ServiceDescriptor)](xref:Microsoft.Extensions.DependencyInjection.Extensions.ServiceCollectionDescriptorExtensions.TryAddEnumerable%2A) methods register the service only if there isn't already an implementation *of the same type* .</span></span> <span data-ttu-id="c479f-259">Plusieurs services sont résolus par le biais de `IEnumerable<{SERVICE}>`.</span><span class="sxs-lookup"><span data-stu-id="c479f-259">Multiple services are resolved via `IEnumerable<{SERVICE}>`.</span></span> <span data-ttu-id="c479f-260">Lors de l’inscription des services, ajoutez une instance si l’un des mêmes types n’a pas déjà été ajouté.</span><span class="sxs-lookup"><span data-stu-id="c479f-260">When registering services, add an instance if one of the same types hasn't already been added.</span></span> <span data-ttu-id="c479f-261">Les auteurs de bibliothèque utilisent `TryAddEnumerable` pour éviter d’inscrire plusieurs copies d’une implémentation dans le conteneur.</span><span class="sxs-lookup"><span data-stu-id="c479f-261">Library authors use `TryAddEnumerable` to avoid registering multiple copies of an implementation in the container.</span></span>

<span data-ttu-id="c479f-262">Dans l’exemple suivant, le premier appel à `TryAddEnumerable` s’inscrit `MessageWriter` en tant qu’implémentation pour `IMessageWriter1` .</span><span class="sxs-lookup"><span data-stu-id="c479f-262">In the following example, the first call to `TryAddEnumerable` registers `MessageWriter` as an implementation for `IMessageWriter1`.</span></span> <span data-ttu-id="c479f-263">Le deuxième appel s’inscrit `MessageWriter` pour `IMessageWriter2` .</span><span class="sxs-lookup"><span data-stu-id="c479f-263">The second call registers `MessageWriter` for `IMessageWriter2`.</span></span> <span data-ttu-id="c479f-264">Le troisième appel n’a aucun effet, car `IMessageWriter1` a déjà une implémentation inscrite de `MessageWriter` :</span><span class="sxs-lookup"><span data-stu-id="c479f-264">The third call has no effect because `IMessageWriter1` already has a registered implementation of `MessageWriter`:</span></span>

```csharp
public interface IMessageWriter1 { }
public interface IMessageWriter2 { }

public class MessageWriter : IMessageWriter1, IMessageWriter2
{
}

services.TryAddEnumerable(ServiceDescriptor.Singleton<IMessageWriter1, MessageWriter>());
services.TryAddEnumerable(ServiceDescriptor.Singleton<IMessageWriter2, MessageWriter>());
services.TryAddEnumerable(ServiceDescriptor.Singleton<IMessageWriter1, MessageWriter>());
```

<span data-ttu-id="c479f-265">L’inscription de service est généralement indépendante de l’ordre, sauf lors de l’inscription de plusieurs implémentations du même type.</span><span class="sxs-lookup"><span data-stu-id="c479f-265">Service registration is generally order independent except when registering multiple implementations of the same type.</span></span>

<span data-ttu-id="c479f-266">`IServiceCollection` est une collection d' <xref:Microsoft.Extensions.DependencyInjection.ServiceDescriptor> objets.</span><span class="sxs-lookup"><span data-stu-id="c479f-266">`IServiceCollection` is a collection of <xref:Microsoft.Extensions.DependencyInjection.ServiceDescriptor> objects.</span></span> <span data-ttu-id="c479f-267">L’exemple suivant montre comment inscrire un service en créant et en ajoutant un `ServiceDescriptor` :</span><span class="sxs-lookup"><span data-stu-id="c479f-267">The following example shows how to register a service by creating and adding a `ServiceDescriptor`:</span></span>

```csharp
string secretKey = Configuration["SecretKey"];
var descriptor = new ServiceDescriptor(
    typeof(IMessageWriter),
    _ => new DefaultMessageWriter(secretKey),
    ServiceLifetime.Transient);

services.Add(descriptor);
```

<span data-ttu-id="c479f-268">Les `Add{LIFETIME}` méthodes intégrées utilisent la même approche.</span><span class="sxs-lookup"><span data-stu-id="c479f-268">The built-in `Add{LIFETIME}` methods use the same approach.</span></span> <span data-ttu-id="c479f-269">Par exemple, consultez le [code source AddScoped](https://github.com/dotnet/extensions/blob/v3.1.8/src/DependencyInjection/DI.Abstractions/src/ServiceCollectionServiceExtensions.cs#L216-L237).</span><span class="sxs-lookup"><span data-stu-id="c479f-269">For example, see the [AddScoped source code](https://github.com/dotnet/extensions/blob/v3.1.8/src/DependencyInjection/DI.Abstractions/src/ServiceCollectionServiceExtensions.cs#L216-L237).</span></span>

### <a name="constructor-injection-behavior"></a><span data-ttu-id="c479f-270">Comportement d’injection de constructeurs</span><span class="sxs-lookup"><span data-stu-id="c479f-270">Constructor injection behavior</span></span>

<span data-ttu-id="c479f-271">Les services peuvent être résolus à l’aide de :</span><span class="sxs-lookup"><span data-stu-id="c479f-271">Services can be resolved by using:</span></span>

- <xref:System.IServiceProvider>
- <span data-ttu-id="c479f-272"><xref:Microsoft.Extensions.DependencyInjection.ActivatorUtilities>:</span><span class="sxs-lookup"><span data-stu-id="c479f-272"><xref:Microsoft.Extensions.DependencyInjection.ActivatorUtilities>:</span></span>
  - <span data-ttu-id="c479f-273">Crée des objets qui ne sont pas inscrits dans le conteneur.</span><span class="sxs-lookup"><span data-stu-id="c479f-273">Creates objects that aren't registered in the container.</span></span>
  - <span data-ttu-id="c479f-274">Utilisé avec certaines fonctionnalités de l’infrastructure.</span><span class="sxs-lookup"><span data-stu-id="c479f-274">Used with some framework features.</span></span>

<span data-ttu-id="c479f-275">Les constructeurs peuvent accepter des arguments qui ne sont pas fournis par l’injection de dépendances, mais les arguments doivent affecter des valeurs par défaut.</span><span class="sxs-lookup"><span data-stu-id="c479f-275">Constructors can accept arguments that aren't provided by dependency injection, but the arguments must assign default values.</span></span>

<span data-ttu-id="c479f-276">Lorsque des services sont résolus par `IServiceProvider` ou `ActivatorUtilities`, l’injection de constructeurs exige un constructeur *public* .</span><span class="sxs-lookup"><span data-stu-id="c479f-276">When services are resolved by `IServiceProvider` or `ActivatorUtilities`, constructor injection requires a *public* constructor.</span></span>

<span data-ttu-id="c479f-277">Lorsque des services sont résolus par `ActivatorUtilities`, l’injection de constructeurs exige qu’un seul constructeur applicable existe.</span><span class="sxs-lookup"><span data-stu-id="c479f-277">When services are resolved by `ActivatorUtilities`, constructor injection requires that only one applicable constructor exists.</span></span> <span data-ttu-id="c479f-278">Les surcharges de constructeurs sont prises en charge, mais une seule peut exister dont les arguments peuvent tous être satisfaits par l’injection de dépendances.</span><span class="sxs-lookup"><span data-stu-id="c479f-278">Constructor overloads are supported, but only one overload can exist whose arguments can all be fulfilled by dependency injection.</span></span>

## <a name="scope-validation"></a><span data-ttu-id="c479f-279">Validation de l’étendue</span><span class="sxs-lookup"><span data-stu-id="c479f-279">Scope validation</span></span>

<span data-ttu-id="c479f-280">Lorsque l’application s’exécute dans l' `Development` environnement et appelle [CreateDefaultBuilder](generic-host.md#default-builder-settings) pour générer l’hôte, le fournisseur de services par défaut effectue des vérifications pour vérifier que :</span><span class="sxs-lookup"><span data-stu-id="c479f-280">When the app runs in the `Development` environment and calls [CreateDefaultBuilder](generic-host.md#default-builder-settings) to build the host, the default service provider performs checks to verify that:</span></span>

- <span data-ttu-id="c479f-281">Les services délimités ne sont pas résolus à partir du fournisseur de services racine.</span><span class="sxs-lookup"><span data-stu-id="c479f-281">Scoped services aren't resolved from the root service provider.</span></span>
- <span data-ttu-id="c479f-282">Les services délimités ne sont pas injectés dans les singletons.</span><span class="sxs-lookup"><span data-stu-id="c479f-282">Scoped services aren't injected into singletons.</span></span>

<span data-ttu-id="c479f-283">Le fournisseur de services racine est créé quand <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionContainerBuilderExtensions.BuildServiceProvider%2A> est appelé.</span><span class="sxs-lookup"><span data-stu-id="c479f-283">The root service provider is created when <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionContainerBuilderExtensions.BuildServiceProvider%2A> is called.</span></span> <span data-ttu-id="c479f-284">La durée de vie du fournisseur de services racine correspond à la durée de vie de l’application lorsque le fournisseur démarre avec l’application et est supprimée lorsque l’application s’arrête.</span><span class="sxs-lookup"><span data-stu-id="c479f-284">The root service provider's lifetime corresponds to the app's lifetime when the provider starts with the app and is disposed when the app shuts down.</span></span>

<span data-ttu-id="c479f-285">Les services Scoped sont supprimés par le conteneur qui les a créés.</span><span class="sxs-lookup"><span data-stu-id="c479f-285">Scoped services are disposed by the container that created them.</span></span> <span data-ttu-id="c479f-286">Si un service étendu est créé dans le conteneur racine, la durée de vie du service est effectivement promue en Singleton, car il est supprimé uniquement par le conteneur racine lorsque l’application s’arrête.</span><span class="sxs-lookup"><span data-stu-id="c479f-286">If a scoped service is created in the root container, the service's lifetime is effectively promoted to singleton because it's only disposed by the root container when the app shuts down.</span></span> <span data-ttu-id="c479f-287">La validation des étendues du service permet de traiter ces situations quand `BuildServiceProvider` est appelé.</span><span class="sxs-lookup"><span data-stu-id="c479f-287">Validating service scopes catches these situations when `BuildServiceProvider` is called.</span></span>

## <a name="see-also"></a><span data-ttu-id="c479f-288">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c479f-288">See also</span></span>

- [<span data-ttu-id="c479f-289">Utiliser l’injection de dépendances dans .NET</span><span class="sxs-lookup"><span data-stu-id="c479f-289">Use dependency injection in .NET</span></span>](dependency-injection-usage.md)
- [<span data-ttu-id="c479f-290">Recommandations relatives à l’injection de dépendances</span><span class="sxs-lookup"><span data-stu-id="c479f-290">Dependency injection guidelines</span></span>](dependency-injection-guidelines.md)
- [<span data-ttu-id="c479f-291">Injection de dépendances dans ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="c479f-291">Dependency injection in ASP.NET Core</span></span>](/aspnet/core/fundamentals/dependency-injection)
- [<span data-ttu-id="c479f-292">Modèles de conférence norvégiens pour le développement d’applications DI</span><span class="sxs-lookup"><span data-stu-id="c479f-292">NDC Conference Patterns for DI app development</span></span>](https://www.youtube.com/watch?v=x-C-CNBVTaY)
- [<span data-ttu-id="c479f-293">Principe des dépendances explicites</span><span class="sxs-lookup"><span data-stu-id="c479f-293">Explicit dependencies principle</span></span>](../../architecture/modern-web-apps-azure/architectural-principles.md#explicit-dependencies)
- [<span data-ttu-id="c479f-294">Inversion des conteneurs de contrôle et le modèle d’injection de dépendances (Martin Fowler)</span><span class="sxs-lookup"><span data-stu-id="c479f-294">Inversion of control containers and the dependency injection pattern (Martin Fowler)</span></span>](https://www.martinfowler.com/articles/injection.html)
- <span data-ttu-id="c479f-295">Les bogues DI doivent être créés dans [github.com/dotnet/extensions](https://github.com/dotnet/extensions/issues) référentiel</span><span class="sxs-lookup"><span data-stu-id="c479f-295">DI bugs should be created in the [github.com/dotnet/extensions](https://github.com/dotnet/extensions/issues) repo</span></span>
