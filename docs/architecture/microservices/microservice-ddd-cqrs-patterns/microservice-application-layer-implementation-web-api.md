---
title: Implémentation de la couche Application de microservices à l’aide de l’API web
description: Architecture de microservices .NET pour les applications .NET conteneurisées | Comprendre l’injection de dépendances et les modèles de médiateur, et leurs détails d’implémentation dans la couche Application de l’API web.
ms.date: 10/08/2018
ms.openlocfilehash: 08cb409b06a54c6b30afa393a817e14bd64fbcbf
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/25/2019
ms.locfileid: "73737529"
---
# <a name="implement-the-microservice-application-layer-using-the-web-api"></a><span data-ttu-id="701ff-103">Implémenter la couche Application des microservices avec l’API web</span><span class="sxs-lookup"><span data-stu-id="701ff-103">Implement the microservice application layer using the Web API</span></span>

## <a name="use-dependency-injection-to-inject-infrastructure-objects-into-your-application-layer"></a><span data-ttu-id="701ff-104">Utiliser l’injection de dépendances pour injecter des objets d’infrastructure dans votre couche Application</span><span class="sxs-lookup"><span data-stu-id="701ff-104">Use Dependency Injection to inject infrastructure objects into your application layer</span></span>

<span data-ttu-id="701ff-105">Comme mentionné précédemment, la couche Application peut être implémentée dans le cadre de l’artefact (assembly) que vous générez, comme dans un projet d’API web ou un projet d’application web MVC.</span><span class="sxs-lookup"><span data-stu-id="701ff-105">As mentioned previously, the application layer can be implemented as part of the artifact (assembly) you are building, such as within a Web API project or an MVC web app project.</span></span> <span data-ttu-id="701ff-106">Dans le cas d’un microservice généré avec ASP.NET Core, la couche Application correspond habituellement à la bibliothèque de votre API web.</span><span class="sxs-lookup"><span data-stu-id="701ff-106">In the case of a microservice built with ASP.NET Core, the application layer will usually be your Web API library.</span></span> <span data-ttu-id="701ff-107">Pour séparer ce qui vient d’ASP.NET Core (son infrastructure plus vos contrôleurs) de votre code de couche Application personnalisé, vous pouvez également placer votre couche Application dans une bibliothèque de classes distincte, mais ce n’est pas obligatoire.</span><span class="sxs-lookup"><span data-stu-id="701ff-107">If you want to separate what is coming from ASP.NET Core (its infrastructure plus your controllers) from your custom application layer code, you could also place your application layer in a separate class library, but that is optional.</span></span>

<span data-ttu-id="701ff-108">Par exemple, le code de la couche Application du microservice Ordering est directement implémenté dans le cadre du projet **Ordering.API** (un projet d’API web ASP.NET Core), comme le montre la figure 7-23.</span><span class="sxs-lookup"><span data-stu-id="701ff-108">For instance, the application layer code of the ordering microservice is directly implemented as part of the **Ordering.API** project (an ASP.NET Core Web API project), as shown in Figure 7-23.</span></span>

:::image type="complex" source="./media/microservice-application-layer-implementation-web-api/ordering-api-microservice.png" alt-text="Capture d’écran du microservice Ordering. API dans le Explorateur de solutions.":::
<span data-ttu-id="701ff-110">La vue Explorateur de solutions du microservice Ordering.API, montrant les sous-dossiers sous le dossier Application : Comportements, Commandes, DomainEventHandlers, IntegrationEvents, Modèles, Requêtes et Validations.</span><span class="sxs-lookup"><span data-stu-id="701ff-110">The Solution Explorer view of the Ordering.API microservice, showing the sub-folders under the Application folder: Behaviors, Commands, DomainEventHandlers, IntegrationEvents, Models, Queries and Validations.</span></span>
:::image-end:::

<span data-ttu-id="701ff-111">**Figure 7-23**.</span><span class="sxs-lookup"><span data-stu-id="701ff-111">**Figure 7-23**.</span></span> <span data-ttu-id="701ff-112">Couche Application dans le projet d’API web ASP.NET Core Ordering.API</span><span class="sxs-lookup"><span data-stu-id="701ff-112">The application layer in the Ordering.API ASP.NET Core Web API project</span></span>

<span data-ttu-id="701ff-113">ASP.NET Core inclut un simple [conteneur IoC intégré](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection) (représenté par l’interface IserviceProvider) qui prend en charge l’injection de constructeurs par défaut, et ASP.NET rend certains services disponibles par le biais de l’injection de dépendances.</span><span class="sxs-lookup"><span data-stu-id="701ff-113">ASP.NET Core includes a simple [built-in IoC container](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection) (represented by the IServiceProvider interface) that supports constructor injection by default, and ASP.NET makes certain services available through DI.</span></span> <span data-ttu-id="701ff-114">ASP.NET Core utilise le terme *service* pour tous les types que vous inscrivez, qui seront injectés par injection de dépendances.</span><span class="sxs-lookup"><span data-stu-id="701ff-114">ASP.NET Core uses the term *service* for any of the types you register that will be injected through DI.</span></span> <span data-ttu-id="701ff-115">Vous configurez les services du conteneur intégré dans la méthode ConfigureServices de la classe Startup de votre application.</span><span class="sxs-lookup"><span data-stu-id="701ff-115">You configure the built-in container's services in the ConfigureServices method in your application's Startup class.</span></span> <span data-ttu-id="701ff-116">Vos dépendances sont implémentées dans les services dont un type a besoin et que vous inscrivez dans le conteneur IoC.</span><span class="sxs-lookup"><span data-stu-id="701ff-116">Your dependencies are implemented in the services that a type needs and that you register in the IoC container.</span></span>

<span data-ttu-id="701ff-117">En règle générale, vous injectez des dépendances qui implémentent des objets d’infrastructure.</span><span class="sxs-lookup"><span data-stu-id="701ff-117">Typically, you want to inject dependencies that implement infrastructure objects.</span></span> <span data-ttu-id="701ff-118">Un dépôt est une dépendance type à injecter.</span><span class="sxs-lookup"><span data-stu-id="701ff-118">A very typical dependency to inject is a repository.</span></span> <span data-ttu-id="701ff-119">Mais vous pouvez injecter toutes vos autres dépendances d’infrastructure.</span><span class="sxs-lookup"><span data-stu-id="701ff-119">But you could inject any other infrastructure dependency that you may have.</span></span> <span data-ttu-id="701ff-120">Pour simplifier les implémentations, vous pouvez injecter directement votre objet de modèle Unité de travail (objet DbContext EF), car DBContext est également l’implémentation de vos objets de persistance d’infrastructure.</span><span class="sxs-lookup"><span data-stu-id="701ff-120">For simpler implementations, you could directly inject your Unit of Work pattern object (the EF DbContext object), because the DBContext is also the implementation of your infrastructure persistence objects.</span></span>

<span data-ttu-id="701ff-121">Dans l’exemple suivant, vous pouvez voir comment .NET Core injecte les objets de dépôt requis par le biais du constructeur.</span><span class="sxs-lookup"><span data-stu-id="701ff-121">In the following example, you can see how .NET Core is injecting the required repository objects through the constructor.</span></span> <span data-ttu-id="701ff-122">La classe est un gestionnaire de commandes, que nous allons expliquer dans la section suivante.</span><span class="sxs-lookup"><span data-stu-id="701ff-122">The class is a command handler, which we will cover in the next section.</span></span>

```csharp
public class CreateOrderCommandHandler
    : IAsyncRequestHandler<CreateOrderCommand, bool>
{
    private readonly IOrderRepository _orderRepository;
    private readonly IIdentityService _identityService;
    private readonly IMediator _mediator;

    // Using DI to inject infrastructure persistence Repositories
    public CreateOrderCommandHandler(IMediator mediator,
                                     IOrderRepository orderRepository,
                                     IIdentityService identityService)
    {
        _orderRepository = orderRepository ??
                          throw new ArgumentNullException(nameof(orderRepository));
        _identityService = identityService ??
                          throw new ArgumentNullException(nameof(identityService));
        _mediator = mediator ??
                                 throw new ArgumentNullException(nameof(mediator));
    }

    public async Task<bool> Handle(CreateOrderCommand message)
    {
        // Create the Order AggregateRoot
        // Add child entities and value objects through the Order aggregate root
        // methods and constructor so validations, invariants, and business logic
        // make sure that consistency is preserved across the whole aggregate
        var address = new Address(message.Street, message.City, message.State,
                                  message.Country, message.ZipCode);
        var order = new Order(message.UserId, address, message.CardTypeId,
                              message.CardNumber, message.CardSecurityNumber,
                              message.CardHolderName, message.CardExpiration);

        foreach (var item in message.OrderItems)
        {
            order.AddOrderItem(item.ProductId, item.ProductName, item.UnitPrice,
                               item.Discount, item.PictureUrl, item.Units);
        }

        _orderRepository.Add(order);

        return await _orderRepository.UnitOfWork
            .SaveEntitiesAsync();
    }
}
```

<span data-ttu-id="701ff-123">Elle utilise les dépôts injectés pour exécuter la transaction et rendre persistantes les modifications d’état.</span><span class="sxs-lookup"><span data-stu-id="701ff-123">The class uses the injected repositories to execute the transaction and persist the state changes.</span></span> <span data-ttu-id="701ff-124">Il importe peu que cette classe soit un gestionnaire de commandes, une méthode de contrôleur de l’API web ASP.NET Core ou un [service d’application DDD](https://lostechies.com/jimmybogard/2008/08/21/services-in-domain-driven-design/).</span><span class="sxs-lookup"><span data-stu-id="701ff-124">It does not matter whether that class is a command handler, an ASP.NET Core Web API controller method, or a [DDD Application Service](https://lostechies.com/jimmybogard/2008/08/21/services-in-domain-driven-design/).</span></span> <span data-ttu-id="701ff-125">Il s’agit en fin de compte d’une classe simple qui utilise des dépôts, des entités de domaine et une autre coordination des applications d’une manière similaire à un gestionnaire de commandes.</span><span class="sxs-lookup"><span data-stu-id="701ff-125">It is ultimately a simple class that uses repositories, domain entities, and other application coordination in a fashion similar to a command handler.</span></span> <span data-ttu-id="701ff-126">L’injection de dépendances fonctionne de la même manière pour toutes les classes mentionnées, comme dans l’exemple qui utilise l’injection de dépendances selon le constructeur.</span><span class="sxs-lookup"><span data-stu-id="701ff-126">Dependency Injection works the same way for all the mentioned classes, as in the example using DI based on the constructor.</span></span>

### <a name="register-the-dependency-implementation-types-and-interfaces-or-abstractions"></a><span data-ttu-id="701ff-127">Inscrire les types et les interfaces ou les abstractions d’implémentation des dépendances</span><span class="sxs-lookup"><span data-stu-id="701ff-127">Register the dependency implementation types and interfaces or abstractions</span></span>

<span data-ttu-id="701ff-128">Avant d’utiliser les objets injectés par le biais de constructeurs, vous devez savoir où inscrire les interfaces et classes qui produisent les objets injectés dans vos classes d’application par le biais de l’injection de dépendances.</span><span class="sxs-lookup"><span data-stu-id="701ff-128">Before you use the objects injected through constructors, you need to know where to register the interfaces and classes that produce the objects injected into your application classes through DI.</span></span> <span data-ttu-id="701ff-129">(Comme l’injection de dépendances basée sur le constructeur, comme indiqué précédemment.)</span><span class="sxs-lookup"><span data-stu-id="701ff-129">(Like DI based on the constructor, as shown previously.)</span></span>

#### <a name="use-the-built-in-ioc-container-provided-by-aspnet-core"></a><span data-ttu-id="701ff-130">Utiliser le conteneur IoC intégré fourni par ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="701ff-130">Use the built-in IoC container provided by ASP.NET Core</span></span>

<span data-ttu-id="701ff-131">Quand vous utilisez le conteneur IoC intégré fourni par ASP.NET Core, vous inscrivez les types à insérer dans la méthode ConfigureServices dans le fichier Startup.cs, comme dans le code suivant :</span><span class="sxs-lookup"><span data-stu-id="701ff-131">When you use the built-in IoC container provided by ASP.NET Core, you register the types you want to inject in the ConfigureServices method in the Startup.cs file, as in the following code:</span></span>

```csharp
// Registration of types into ASP.NET Core built-in container
public void ConfigureServices(IServiceCollection services)
{
    // Register out-of-the-box framework services.
    services.AddDbContext<CatalogContext>(c =>
    {
        c.UseSqlServer(Configuration["ConnectionString"]);
    },
    ServiceLifetime.Scoped
    );
    services.AddMvc();
    // Register custom application dependencies.
    services.AddScoped<IMyCustomRepository, MyCustomSQLRepository>();
}
```

<span data-ttu-id="701ff-132">Le modèle le plus courant pour inscrire des types dans un conteneur IoC consiste à inscrire une paire de types : une interface et sa classe d’implémentation associée.</span><span class="sxs-lookup"><span data-stu-id="701ff-132">The most common pattern when registering types in an IoC container is to register a pair of types—an interface and its related implementation class.</span></span> <span data-ttu-id="701ff-133">Ensuite, quand vous demandez un objet au conteneur IoC par le biais d’un constructeur, vous demandez un objet d’un certain type d’interface.</span><span class="sxs-lookup"><span data-stu-id="701ff-133">Then when you request an object from the IoC container through any constructor, you request an object of a certain type of interface.</span></span> <span data-ttu-id="701ff-134">Par exemple, dans l’exemple précédent, la dernière ligne indique que lorsqu’un des constructeurs dépendent d’IMyCustomRepository (interface ou abstraction), le conteneur IoC injecte une instance de la classe d’implémentation MyCustomSQLServerRepository.</span><span class="sxs-lookup"><span data-stu-id="701ff-134">For instance, in the previous example, the last line states that when any of your constructors have a dependency on IMyCustomRepository (interface or abstraction), the IoC container will inject an instance of the MyCustomSQLServerRepository implementation class.</span></span>

#### <a name="use-the-scrutor-library-for-automatic-types-registration"></a><span data-ttu-id="701ff-135">Utiliser la bibliothèque Scrutor pour l’inscription automatique des types</span><span class="sxs-lookup"><span data-stu-id="701ff-135">Use the Scrutor library for automatic types registration</span></span>

<span data-ttu-id="701ff-136">Quand vous utilisez l’injection de dépendances dans .NET Core, vous pouvez avoir envie d’analyser un assembly et d’inscrire automatiquement ses types par convention.</span><span class="sxs-lookup"><span data-stu-id="701ff-136">When using DI in .NET Core, you might want to be able to scan an assembly and automatically register its types by convention.</span></span> <span data-ttu-id="701ff-137">Cette fonctionnalité n’est pas disponible dans ASP.NET Core pour le moment.</span><span class="sxs-lookup"><span data-stu-id="701ff-137">This feature is not currently available in ASP.NET Core.</span></span> <span data-ttu-id="701ff-138">Toutefois, vous pouvez utiliser la bibliothèque [Scrutor](https://github.com/khellang/Scrutor) à la place.</span><span class="sxs-lookup"><span data-stu-id="701ff-138">However, you can use the [Scrutor](https://github.com/khellang/Scrutor) library for that.</span></span> <span data-ttu-id="701ff-139">Cette approche est pratique lorsque vous avez des dizaines de types à inscrire dans votre conteneur IoC.</span><span class="sxs-lookup"><span data-stu-id="701ff-139">This approach is convenient when you have dozens of types that need to be registered in your IoC container.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="701ff-140">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="701ff-140">Additional resources</span></span>

- <span data-ttu-id="701ff-141">**Matthew King. Inscription de services avec scrutor** </span><span class="sxs-lookup"><span data-stu-id="701ff-141">**Matthew King. Registering services with Scrutor** </span></span>\
  <https://www.mking.net/blog/registering-services-with-scrutor>

- <span data-ttu-id="701ff-142">**Kristian Hellang. Scrutor.**</span><span class="sxs-lookup"><span data-stu-id="701ff-142">**Kristian Hellang. Scrutor.**</span></span> <span data-ttu-id="701ff-143">Dépôt GitHub.</span><span class="sxs-lookup"><span data-stu-id="701ff-143">GitHub repo.</span></span> \
  <https://github.com/khellang/Scrutor>

#### <a name="use-autofac-as-an-ioc-container"></a><span data-ttu-id="701ff-144">Utiliser Autofac comme conteneur IoC</span><span class="sxs-lookup"><span data-stu-id="701ff-144">Use Autofac as an IoC container</span></span>

<span data-ttu-id="701ff-145">Vous pouvez également utiliser d’autres conteneurs IoC et les incorporer dans le pipeline ASP.NET Core, comme dans le microservice de passation de commandes dans eShopOnContainers, qui utilise [Autofac](https://autofac.org/).</span><span class="sxs-lookup"><span data-stu-id="701ff-145">You can also use additional IoC containers and plug them into the ASP.NET Core pipeline, as in the ordering microservice in eShopOnContainers, which uses [Autofac](https://autofac.org/).</span></span> <span data-ttu-id="701ff-146">Quand vous utilisez Autofac, vous inscrivez généralement les types par le biais de modules, ce qui vous permet de fractionner les types d’inscription entre plusieurs fichiers selon leur emplacement, tout comme vous pourriez distribuer les types d’application dans plusieurs bibliothèques de classes.</span><span class="sxs-lookup"><span data-stu-id="701ff-146">When using Autofac you typically register the types via modules, which allow you to split the registration types between multiple files depending on where your types are, just as you could have the application types distributed across multiple class libraries.</span></span>

<span data-ttu-id="701ff-147">Par exemple, voici le [module d’application Autofac](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Infrastructure/AutofacModules/ApplicationModule.cs) pour le projet d’[API web Ordering.API](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Services/Ordering/Ordering.API) avec les types que vous avez besoin d’injecter.</span><span class="sxs-lookup"><span data-stu-id="701ff-147">For example, the following is the [Autofac application module](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Infrastructure/AutofacModules/ApplicationModule.cs) for the [Ordering.API Web API](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Services/Ordering/Ordering.API) project with the types you will want to inject.</span></span>

```csharp
public class ApplicationModule : Autofac.Module
{
    public string QueriesConnectionString { get; }
    public ApplicationModule(string qconstr)
    {
        QueriesConnectionString = qconstr;
    }

    protected override void Load(ContainerBuilder builder)
    {
        builder.Register(c => new OrderQueries(QueriesConnectionString))
            .As<IOrderQueries>()
            .InstancePerLifetimeScope();
        builder.RegisterType<BuyerRepository>()
            .As<IBuyerRepository>()
            .InstancePerLifetimeScope();
        builder.RegisterType<OrderRepository>()
            .As<IOrderRepository>()
            .InstancePerLifetimeScope();
        builder.RegisterType<RequestManager>()
            .As<IRequestManager>()
            .InstancePerLifetimeScope();
   }
}
```

<span data-ttu-id="701ff-148">Autofac a également une fonctionnalité pour [analyser les assemblys et inscrire les types selon des conventions de nommage](https://autofac.readthedocs.io/en/latest/register/scanning.html).</span><span class="sxs-lookup"><span data-stu-id="701ff-148">Autofac also has a feature to [scan assemblies and register types by name conventions](https://autofac.readthedocs.io/en/latest/register/scanning.html).</span></span>

<span data-ttu-id="701ff-149">Le processus et les concepts d’inscription sont très similaires à la façon dont vous pouvez inscrire des types auprès du conteneur IoC ASP.NET Core intégré, mais la syntaxe avec Autofac est un peu différente.</span><span class="sxs-lookup"><span data-stu-id="701ff-149">The registration process and concepts are very similar to the way you can register types with the built-in ASP.NET Core IoC container, but the syntax when using Autofac is a bit different.</span></span>

<span data-ttu-id="701ff-150">Dans l’exemple de code, l’abstraction IOrderRepository est inscrite de concert avec la classe d’implémentation OrderRepository.</span><span class="sxs-lookup"><span data-stu-id="701ff-150">In the example code, the abstraction IOrderRepository is registered along with the implementation class OrderRepository.</span></span> <span data-ttu-id="701ff-151">Cela signifie que chaque fois qu’un constructeur déclare une dépendance par le biais de l’abstraction ou de l’interface IOrderRepository, le conteneur IoC injecte une instance de la classe OrderRepository.</span><span class="sxs-lookup"><span data-stu-id="701ff-151">This means that whenever a constructor is declaring a dependency through the IOrderRepository abstraction or interface, the IoC container will inject an instance of the OrderRepository class.</span></span>

<span data-ttu-id="701ff-152">Le type d’étendue d’instance détermine la façon dont une instance est partagée entre les demandes du même service ou de la même dépendance.</span><span class="sxs-lookup"><span data-stu-id="701ff-152">The instance scope type determines how an instance is shared between requests for the same service or dependency.</span></span> <span data-ttu-id="701ff-153">Lorsqu’une demande est effectuée pour une dépendance, le conteneur IoC peut retourner :</span><span class="sxs-lookup"><span data-stu-id="701ff-153">When a request is made for a dependency, the IoC container can return the following:</span></span>

- <span data-ttu-id="701ff-154">Une instance unique par étendue de durée de vie (désignée dans le conteneur IoC ASP.NET Core comme *délimitée*).</span><span class="sxs-lookup"><span data-stu-id="701ff-154">A single instance per lifetime scope (referred to in the ASP.NET Core IoC container as *scoped*).</span></span>

- <span data-ttu-id="701ff-155">Une nouvelle instance par dépendance (désignée dans le conteneur IoC ASP.NET Core comme *temporaire*).</span><span class="sxs-lookup"><span data-stu-id="701ff-155">A new instance per dependency (referred to in the ASP.NET Core IoC container as *transient*).</span></span>

- <span data-ttu-id="701ff-156">Une instance unique partagée entre tous les objets à l’aide du conteneur IoC (désignée dans le conteneur IoC ASP.NET Core comme *singleton*).</span><span class="sxs-lookup"><span data-stu-id="701ff-156">A single instance shared across all objects using the IoC container (referred to in the ASP.NET Core IoC container as *singleton*).</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="701ff-157">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="701ff-157">Additional resources</span></span>

- <span data-ttu-id="701ff-158">**Introduction à l’injection de dépendances dans ASP.NET Core** </span><span class="sxs-lookup"><span data-stu-id="701ff-158">**Introduction to Dependency Injection in ASP.NET Core** </span></span>\
  [https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection](/aspnet/core/fundamentals/dependency-injection)

- <span data-ttu-id="701ff-159">**Autofac.**</span><span class="sxs-lookup"><span data-stu-id="701ff-159">**Autofac.**</span></span> <span data-ttu-id="701ff-160">Documentation officielle.</span><span class="sxs-lookup"><span data-stu-id="701ff-160">Official documentation.</span></span> \
  <https://docs.autofac.org/en/latest/>

- <span data-ttu-id="701ff-161">**Comparing ASP.NET Core IoC container service lifetimes with Autofac IoC container instance scopes - Cesar de la Torre.**</span><span class="sxs-lookup"><span data-stu-id="701ff-161">**Comparing ASP.NET Core IoC container service lifetimes with Autofac IoC container instance scopes - Cesar de la Torre.**</span></span> \
  <https://devblogs.microsoft.com/cesardelatorre/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/>

## <a name="implement-the-command-and-command-handler-patterns"></a><span data-ttu-id="701ff-162">Implémenter les modèles Command (Commande) et Command Handler (Gestionnaire de commandes)</span><span class="sxs-lookup"><span data-stu-id="701ff-162">Implement the Command and Command Handler patterns</span></span>

<span data-ttu-id="701ff-163">Dans l’exemple d’injection de dépendances par le biais d’un constructeur mentionné dans la section précédente, le conteneur IoC injectait des dépôts par le biais d’un constructeur dans une classe.</span><span class="sxs-lookup"><span data-stu-id="701ff-163">In the DI-through-constructor example shown in the previous section, the IoC container was injecting repositories through a constructor in a class.</span></span> <span data-ttu-id="701ff-164">Mais où ont-ils été injectés exactement ?</span><span class="sxs-lookup"><span data-stu-id="701ff-164">But exactly where were they injected?</span></span> <span data-ttu-id="701ff-165">Dans une API web simple (par exemple le microservice Catalog dans eShopOnContainers), vous les injectez au niveau des contrôleurs MVC, dans un constructeur de contrôleur, dans le cadre du pipeline de requêtes d’ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="701ff-165">In a simple Web API (for example, the catalog microservice in eShopOnContainers), you inject them at the MVC controllers’ level, in a controller constructor, as part of the request pipeline of ASP.NET Core.</span></span> <span data-ttu-id="701ff-166">Toutefois, dans le code initial de cette section (la classe [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) du service Ordering.API dans eShopOnContainers), l’injection de dépendances s’effectue par le biais du constructeur d’un gestionnaire de commandes particulier.</span><span class="sxs-lookup"><span data-stu-id="701ff-166">However, in the initial code of this section (the [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) class from the Ordering.API service in eShopOnContainers), the injection of dependencies is done through the constructor of a particular command handler.</span></span> <span data-ttu-id="701ff-167">Expliquons ce qu’est un gestionnaire de commandes et pourquoi l’utiliser.</span><span class="sxs-lookup"><span data-stu-id="701ff-167">Let us explain what a command handler is and why you would want to use it.</span></span>

<span data-ttu-id="701ff-168">Le modèle Commande est intrinsèquement lié au modèle CQRS présenté précédemment dans le présent guide.</span><span class="sxs-lookup"><span data-stu-id="701ff-168">The Command pattern is intrinsically related to the CQRS pattern that was introduced earlier in this guide.</span></span> <span data-ttu-id="701ff-169">Le modèle CQRS a deux côtés.</span><span class="sxs-lookup"><span data-stu-id="701ff-169">CQRS has two sides.</span></span> <span data-ttu-id="701ff-170">Le premier côté concerne les requêtes, l’utilisation de requêtes simplifiées avec le micro ORM [Dapper](https://github.com/StackExchange/dapper-dot-net), précédemment décrit.</span><span class="sxs-lookup"><span data-stu-id="701ff-170">The first area is queries, using simplified queries with the [Dapper](https://github.com/StackExchange/dapper-dot-net) micro ORM, which was explained previously.</span></span> <span data-ttu-id="701ff-171">Le second côté concerne les commandes, qui sont le point de départ des transactions et le canal d’entrée depuis l’extérieur du service.</span><span class="sxs-lookup"><span data-stu-id="701ff-171">The second area is commands, which are the starting point for transactions, and the input channel from outside the service.</span></span>

<span data-ttu-id="701ff-172">Comme le montre la figure 7-24, le modèle se base sur l’acceptation des commandes du côté client, leur traitement en fonction des règles du modèle de domaine et enfin, sur la persistance des états avec les transactions.</span><span class="sxs-lookup"><span data-stu-id="701ff-172">As shown in Figure 7-24, the pattern is based on accepting commands from the client side, processing them based on the domain model rules, and finally persisting the states with transactions.</span></span>

![Diagramme montrant le workflow de haut niveau du client au niveau de la base de données.](./media/microservice-application-layer-implementation-web-api/high-level-writes-side.png)

<span data-ttu-id="701ff-174">**Figure 7-24**.</span><span class="sxs-lookup"><span data-stu-id="701ff-174">**Figure 7-24**.</span></span> <span data-ttu-id="701ff-175">Vue générale des commandes ou du « côté transactionnel » d’un modèle CQRS</span><span class="sxs-lookup"><span data-stu-id="701ff-175">High-level view of the commands or “transactional side” in a CQRS pattern</span></span>

<span data-ttu-id="701ff-176">La figure 7-24 montre que l’application d’interface utilisateur envoie une commande via l’API qui obtient une `CommandHandler`, qui dépend du modèle de domaine et de l’infrastructure, pour mettre à jour la base de données.</span><span class="sxs-lookup"><span data-stu-id="701ff-176">Figure 7-24 shows that the UI app sends a command through the API that gets to a `CommandHandler`, that depends on the Domain model and the Infrastructure, to update the database.</span></span>

### <a name="the-command-class"></a><span data-ttu-id="701ff-177">La classe de commande</span><span class="sxs-lookup"><span data-stu-id="701ff-177">The command class</span></span>

<span data-ttu-id="701ff-178">Une commande est une demande faite au système d’effectuer une action qui modifie son état.</span><span class="sxs-lookup"><span data-stu-id="701ff-178">A command is a request for the system to perform an action that changes the state of the system.</span></span> <span data-ttu-id="701ff-179">Les commandes sont impératives et doivent être traitées une seule fois.</span><span class="sxs-lookup"><span data-stu-id="701ff-179">Commands are imperative, and should be processed just once.</span></span>

<span data-ttu-id="701ff-180">Étant donné que les commandes sont impératives, leur nom commence généralement par un verbe (par exemple, « Create » ou « Update ») et elles peuvent inclure le type d’agrégat, comme CreateOrderCommand.</span><span class="sxs-lookup"><span data-stu-id="701ff-180">Since commands are imperatives, they are typically named with a verb in the imperative mood (for example, "create" or "update"), and they might include the aggregate type, such as CreateOrderCommand.</span></span> <span data-ttu-id="701ff-181">Contrairement à un événement, une commande n’est pas un fait passé ; il s’agit uniquement d’une demande qui peut donc être refusée.</span><span class="sxs-lookup"><span data-stu-id="701ff-181">Unlike an event, a command is not a fact from the past; it is only a request, and thus may be refused.</span></span>

<span data-ttu-id="701ff-182">Les commandes peuvent provenir de l’interface utilisateur après qu’un utilisateur a lancé une demande ou d’un gestionnaire de processus quand ce dernier indique à un agrégat d’exécuter une action.</span><span class="sxs-lookup"><span data-stu-id="701ff-182">Commands can originate from the UI as a result of a user initiating a request, or from a process manager when the process manager is directing an aggregate to perform an action.</span></span>

<span data-ttu-id="701ff-183">Une importante caractéristique d’une commande est qu’elle doit être traitée une seule fois par un seul récepteur.</span><span class="sxs-lookup"><span data-stu-id="701ff-183">An important characteristic of a command is that it should be processed just once by a single receiver.</span></span> <span data-ttu-id="701ff-184">En effet, une commande est une action ou transaction unique que vous voulez effectuer dans l’application.</span><span class="sxs-lookup"><span data-stu-id="701ff-184">This is because a command is a single action or transaction you want to perform in the application.</span></span> <span data-ttu-id="701ff-185">Par exemple, la même commande de création d’une commande ne doit pas être traitée plusieurs fois.</span><span class="sxs-lookup"><span data-stu-id="701ff-185">For example, the same order creation command should not be processed more than once.</span></span> <span data-ttu-id="701ff-186">Il s’agit d’une différence importante entre les commandes et les événements.</span><span class="sxs-lookup"><span data-stu-id="701ff-186">This is an important difference between commands and events.</span></span> <span data-ttu-id="701ff-187">Les événements peuvent être traités plusieurs fois, car de nombreux systèmes ou microservices peuvent s’y intéresser.</span><span class="sxs-lookup"><span data-stu-id="701ff-187">Events may be processed multiple times, because many systems or microservices might be interested in the event.</span></span>

<span data-ttu-id="701ff-188">De plus, il est important de traiter une commande une seule fois au cas où elle ne serait pas idempotente.</span><span class="sxs-lookup"><span data-stu-id="701ff-188">In addition, it is important that a command be processed only once in case the command is not idempotent.</span></span> <span data-ttu-id="701ff-189">Une commande est idempotente si elle peut être exécutée plusieurs fois sans que sont résultat ne soit modifié, soit en raison de sa nature, soit en raison de la manière dont le système la gère.</span><span class="sxs-lookup"><span data-stu-id="701ff-189">A command is idempotent if it can be executed multiple times without changing the result, either because of the nature of the command, or because of the way the system handles the command.</span></span>

<span data-ttu-id="701ff-190">Rendre vos commandes et mises à jour idempotentes est une bonne pratique si celle-ci est adaptée aux règles d’entreprise et aux invariants de votre domaine.</span><span class="sxs-lookup"><span data-stu-id="701ff-190">It is a good practice to make your commands and updates idempotent when it makes sense under your domain’s business rules and invariants.</span></span> <span data-ttu-id="701ff-191">Autrement dit, pour utiliser le même exemple, si pour une raison quelconque (logique de nouvelle tentative, piratage, etc.), la même commande CreateOrder atteint votre système plusieurs fois, vous devez être en mesure de l’identifier et de veiller à ne pas créer plusieurs commandes.</span><span class="sxs-lookup"><span data-stu-id="701ff-191">For instance, to use the same example, if for any reason (retry logic, hacking, etc.) the same CreateOrder command reaches your system multiple times, you should be able to identify it and ensure that you do not create multiple orders.</span></span> <span data-ttu-id="701ff-192">Pour cela, vous devez attacher une sorte d’identité dans les opérations et déterminer si la commande ou la mise à jour a déjà été traitée.</span><span class="sxs-lookup"><span data-stu-id="701ff-192">To do so, you need to attach some kind of identity in the operations and identify whether the command or update was already processed.</span></span>

<span data-ttu-id="701ff-193">Vous envoyez une commande à un seul récepteur ; vous ne publiez pas une commande.</span><span class="sxs-lookup"><span data-stu-id="701ff-193">You send a command to a single receiver; you do not publish a command.</span></span> <span data-ttu-id="701ff-194">La publication est destinée aux événements qui spécifient un fait : quelque chose s’est produit, qui peut intéresser les destinataires des événements.</span><span class="sxs-lookup"><span data-stu-id="701ff-194">Publishing is for events that state a fact—that something has happened and might be interesting for event receivers.</span></span> <span data-ttu-id="701ff-195">Dans le cas des événements, le serveur de publication n’a que faire de savoir quels récepteurs obtiennent l’événement ou ce qu’ils en font.</span><span class="sxs-lookup"><span data-stu-id="701ff-195">In the case of events, the publisher has no concerns about which receivers get the event or what they do it.</span></span> <span data-ttu-id="701ff-196">Mais les choses sont différentes pour les événements d’intégration ou de domaine déjà présentés dans les sections précédentes.</span><span class="sxs-lookup"><span data-stu-id="701ff-196">But domain or integration events are a different story already introduced in previous sections.</span></span>

<span data-ttu-id="701ff-197">Une commande est implémentée avec une classe qui contient des champs ou collections de données contenant toutes les informations nécessaires à son exécution.</span><span class="sxs-lookup"><span data-stu-id="701ff-197">A command is implemented with a class that contains data fields or collections with all the information that is needed in order to execute that command.</span></span> <span data-ttu-id="701ff-198">Une commande est un type spécial d’objet de transfert de données, particulièrement utilisé pour demander des modifications ou des transactions.</span><span class="sxs-lookup"><span data-stu-id="701ff-198">A command is a special kind of Data Transfer Object (DTO), one that is specifically used to request changes or transactions.</span></span> <span data-ttu-id="701ff-199">La commande elle-même se base sur les informations exactes nécessaires à son traitement et rien de plus.</span><span class="sxs-lookup"><span data-stu-id="701ff-199">The command itself is based on exactly the information that is needed for processing the command, and nothing more.</span></span>

<span data-ttu-id="701ff-200">L’exemple suivant illustre la classe `CreateOrderCommand` simplifiée.</span><span class="sxs-lookup"><span data-stu-id="701ff-200">The following example shows the simplified `CreateOrderCommand` class.</span></span> <span data-ttu-id="701ff-201">Il s’agit d’une commande immuable utilisée dans le microservice de passation de commandes dans eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="701ff-201">This is an immutable command that is used in the ordering microservice in eShopOnContainers.</span></span>

```csharp
// DDD and CQRS patterns comment
// Note that we recommend that you implement immutable commands
// In this case, immutability is achieved by having all the setters as private
// plus being able to update the data just once, when creating the object
// through the constructor.
// References on immutable commands:
// http://cqrs.nu/Faq
// https://docs.spine3.org/motivation/immutability.html
// http://blog.gauffin.org/2012/06/griffin-container-introducing-command-support/
// https://docs.microsoft.com/dotnet/csharp/programming-guide/classes-and-structs/how-to-implement-a-lightweight-class-with-auto-implemented-properties
[DataContract]
public class CreateOrderCommand
    :IAsyncRequest<bool>
{
    [DataMember]
    private readonly List<OrderItemDTO> _orderItems;
    [DataMember]
    public string City { get; private set; }
    [DataMember]
    public string Street { get; private set; }
    [DataMember]
    public string State { get; private set; }
    [DataMember]
    public string Country { get; private set; }
    [DataMember]
    public string ZipCode { get; private set; }
    [DataMember]
    public string CardNumber { get; private set; }
    [DataMember]
    public string CardHolderName { get; private set; }
    [DataMember]
    public DateTime CardExpiration { get; private set; }
    [DataMember]
    public string CardSecurityNumber { get; private set; }
    [DataMember]
    public int CardTypeId { get; private set; }
    [DataMember]
    public IEnumerable<OrderItemDTO> OrderItems => _orderItems;

    public CreateOrderCommand()
    {
        _orderItems = new List<OrderItemDTO>();
    }

    public CreateOrderCommand(List<BasketItem> basketItems, string city,
        string street,
        string state, string country, string zipcode,
        string cardNumber, string cardHolderName, DateTime cardExpiration,
        string cardSecurityNumber, int cardTypeId) : this()
    {
        _orderItems = MapToOrderItems(basketItems);
        City = city;
        Street = street;
        State = state;
        Country = country;
        ZipCode = zipcode;
        CardNumber = cardNumber;
        CardHolderName = cardHolderName;
        CardSecurityNumber = cardSecurityNumber;
        CardTypeId = cardTypeId;
        CardExpiration = cardExpiration;
    }

    public class OrderItemDTO
    {
        public int ProductId { get; set; }
        public string ProductName { get; set; }
        public decimal UnitPrice { get; set; }
        public decimal Discount { get; set; }
        public int Units { get; set; }
        public string PictureUrl { get; set; }
    }
}
```

<span data-ttu-id="701ff-202">En gros, la classe de commande contient toutes les données dont vous avez besoin pour effectuer une transaction commerciale à l’aide des objets du modèle de domaine.</span><span class="sxs-lookup"><span data-stu-id="701ff-202">Basically, the command class contains all the data you need for performing a business transaction by using the domain model objects.</span></span> <span data-ttu-id="701ff-203">Ainsi, les commandes sont simplement des structures de données qui contiennent des données en lecture seule, sans aucun comportement.</span><span class="sxs-lookup"><span data-stu-id="701ff-203">Thus, commands are simply data structures that contain read-only data, and no behavior.</span></span> <span data-ttu-id="701ff-204">Le nom de la commande indique son objectif.</span><span class="sxs-lookup"><span data-stu-id="701ff-204">The command’s name indicates its purpose.</span></span> <span data-ttu-id="701ff-205">Dans de nombreux langages, comme C#, les commandes sont représentées sous forme de classes, mais il ne s’agit pas de vraies classes au sens orienté objet.</span><span class="sxs-lookup"><span data-stu-id="701ff-205">In many languages like C#, commands are represented as classes, but they are not true classes in the real object-oriented sense.</span></span>

<span data-ttu-id="701ff-206">Autre caractéristique des commandes : elles sont immuables, car l’usage veut qu’elles soient traitées directement par le modèle de domaine.</span><span class="sxs-lookup"><span data-stu-id="701ff-206">As an additional characteristic, commands are immutable, because the expected usage is that they are processed directly by the domain model.</span></span> <span data-ttu-id="701ff-207">Elles n’ont pas besoin de changer au cours de leur durée de vie prévue.</span><span class="sxs-lookup"><span data-stu-id="701ff-207">They do not need to change during their projected lifetime.</span></span> <span data-ttu-id="701ff-208">Dans une classe C#, l’immuabilité implique d’éviter toute méthode setter ou autre méthode qui modifie l’état interne.</span><span class="sxs-lookup"><span data-stu-id="701ff-208">In a C# class, immutability can be achieved by not having any setters or other methods that change internal state.</span></span>

<span data-ttu-id="701ff-209">Gardez à l’esprit que si vous prévoyez ou que vous vous attendez à ce que les commandes subissent un processus de sérialisation/désérialisation, les propriétés doivent avoir une méthode setter privée et l’attribut `[DataMember]` (ou `[JsonProperty]`), sans quoi le désérialiseur ne peut pas reconstruire l’objet au niveau de la destination avec les valeurs nécessaires.</span><span class="sxs-lookup"><span data-stu-id="701ff-209">Bear in mind that if you intend or expect commands will be going through a serializing/deserializing process, the properties must have private setter, and the `[DataMember]` (or `[JsonProperty]`) attribute, otherwise the deserializer will not be able to reconstruct the object at destination with the required values.</span></span>

<span data-ttu-id="701ff-210">Par exemple, la classe de commande pour la création d’une commande est probablement similaire en termes de données à la commande que vous souhaitez créer, mais vous n’avez probablement pas besoin des mêmes attributs.</span><span class="sxs-lookup"><span data-stu-id="701ff-210">For example, the command class for creating an order is probably similar in terms of data to the order you want to create, but you probably do not need the same attributes.</span></span> <span data-ttu-id="701ff-211">Par exemple, `CreateOrderCommand` n’a pas d’ID de commande, car la commande n’a pas encore été créée.</span><span class="sxs-lookup"><span data-stu-id="701ff-211">For instance, `CreateOrderCommand` does not have an order ID, because the order has not been created yet.</span></span>

<span data-ttu-id="701ff-212">De nombreuses classes de commande peuvent être simples, car elles n’ont besoin que de quelques champs sur un état qui doit être modifié.</span><span class="sxs-lookup"><span data-stu-id="701ff-212">Many command classes can be simple, requiring only a few fields about some state that needs to be changed.</span></span> <span data-ttu-id="701ff-213">C’est le cas si vous passez simplement l’état d’une commande de « En cours » à « Payée » ou « Livrée » à l’aide d’une commande semblable à la suivante :</span><span class="sxs-lookup"><span data-stu-id="701ff-213">That would be the case if you are just changing the status of an order from “in process” to “paid” or “shipped” by using a command similar to the following:</span></span>

```csharp
[DataContract]
public class UpdateOrderStatusCommand
    :IAsyncRequest<bool>
{
    [DataMember]
    public string Status { get; private set; }

    [DataMember]
    public string OrderId { get; private set; }

    [DataMember]
    public string BuyerIdentityGuid { get; private set; }
}
```

<span data-ttu-id="701ff-214">Certains développeurs séparent leurs objets de demande d’interface utilisateur de leurs objets de transfert de données, mais il ne s’agit que d’une question de préférence.</span><span class="sxs-lookup"><span data-stu-id="701ff-214">Some developers make their UI request objects separate from their command DTOs, but that is just a matter of preference.</span></span> <span data-ttu-id="701ff-215">Cette séparation est fastidieuse et n’ajoute pas de valeur. Les objets ont presque exactement la même forme.</span><span class="sxs-lookup"><span data-stu-id="701ff-215">It is a tedious separation with not much added value, and the objects are almost exactly the same shape.</span></span> <span data-ttu-id="701ff-216">Par exemple, dans eShopOnContainers, certaines commandes viennent directement du côté client.</span><span class="sxs-lookup"><span data-stu-id="701ff-216">For instance, in eShopOnContainers, some commands come directly from the client side.</span></span>

### <a name="the-command-handler-class"></a><span data-ttu-id="701ff-217">La classe de gestionnaire de commandes</span><span class="sxs-lookup"><span data-stu-id="701ff-217">The Command Handler class</span></span>

<span data-ttu-id="701ff-218">Vous devez implémenter une classe de gestionnaire de commandes spécifique pour chaque commande.</span><span class="sxs-lookup"><span data-stu-id="701ff-218">You should implement a specific command handler class for each command.</span></span> <span data-ttu-id="701ff-219">Le modèle fonctionne ainsi et c’est là que vous allez utiliser l’objet de commande, les objets de domaine et les objets de dépôt d’infrastructure.</span><span class="sxs-lookup"><span data-stu-id="701ff-219">That is how the pattern works, and it is where you will use the command object, the domain objects, and the infrastructure repository objects.</span></span> <span data-ttu-id="701ff-220">Le gestionnaire de commandes est en fait le cœur de la couche Application en termes de CQRS et DDD.</span><span class="sxs-lookup"><span data-stu-id="701ff-220">The command handler is in fact the heart of the application layer in terms of CQRS and DDD.</span></span> <span data-ttu-id="701ff-221">Toutefois, toute la logique de domaine doit être contenue dans les classes de domaine : au sein des racines d’agrégat (entités racine), des entités enfants ou des [services de domaine](https://lostechies.com/jimmybogard/2008/08/21/services-in-domain-driven-design/), mais pas dans le gestionnaire de commandes, qui est une classe de la couche Application.</span><span class="sxs-lookup"><span data-stu-id="701ff-221">However, all the domain logic should be contained within the domain classes—within the aggregate roots (root entities), child entities, or [domain services](https://lostechies.com/jimmybogard/2008/08/21/services-in-domain-driven-design/), but not within the command handler, which is a class from the application layer.</span></span>

<span data-ttu-id="701ff-222">La classe du gestionnaire de commandes offre une base solide pour appliquer le principe de responsabilité unique mentionné dans une des sections précédentes.</span><span class="sxs-lookup"><span data-stu-id="701ff-222">The command handler class offers a strong stepping stone in the way to achieve the Single Responsibility Principle (SRP) mentioned in a previous section.</span></span>

<span data-ttu-id="701ff-223">Un gestionnaire de commandes reçoit une commande et obtient un résultat de l’agrégat qui est utilisé.</span><span class="sxs-lookup"><span data-stu-id="701ff-223">A command handler receives a command and obtains a result from the aggregate that is used.</span></span> <span data-ttu-id="701ff-224">Ce résultat doit être l’exécution correcte de la commande ou une exception.</span><span class="sxs-lookup"><span data-stu-id="701ff-224">The result should be either successful execution of the command, or an exception.</span></span> <span data-ttu-id="701ff-225">En cas d’exception, l’état du système ne doit pas changer.</span><span class="sxs-lookup"><span data-stu-id="701ff-225">In the case of an exception, the system state should be unchanged.</span></span>

<span data-ttu-id="701ff-226">Le gestionnaire de commandes suit généralement les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="701ff-226">The command handler usually takes the following steps:</span></span>

- <span data-ttu-id="701ff-227">Il reçoit l’objet de commande, comme un objet de transfert de données (de la part du [médiateur](https://en.wikipedia.org/wiki/Mediator_pattern) ou d’un autre objet d’infrastructure).</span><span class="sxs-lookup"><span data-stu-id="701ff-227">It receives the command object, like a DTO (from the [mediator](https://en.wikipedia.org/wiki/Mediator_pattern) or other infrastructure object).</span></span>

- <span data-ttu-id="701ff-228">Il vérifie que la commande est valide (si elle n’est pas validée par le médiateur).</span><span class="sxs-lookup"><span data-stu-id="701ff-228">It validates that the command is valid (if not validated by the mediator).</span></span>

- <span data-ttu-id="701ff-229">Il instancie l’instance racine de l’agrégat qui est la cible de la commande en cours.</span><span class="sxs-lookup"><span data-stu-id="701ff-229">It instantiates the aggregate root instance that is the target of the current command.</span></span>

- <span data-ttu-id="701ff-230">Il exécute la méthode sur l’instance racine de l’agrégat, pour obtenir les données nécessaires à partir de la commande.</span><span class="sxs-lookup"><span data-stu-id="701ff-230">It executes the method on the aggregate root instance, getting the required data from the command.</span></span>

- <span data-ttu-id="701ff-231">Il conserve le nouvel état de l’agrégat dans sa base de données correspondante.</span><span class="sxs-lookup"><span data-stu-id="701ff-231">It persists the new state of the aggregate to its related database.</span></span> <span data-ttu-id="701ff-232">Cette dernière opération correspond à la transaction réelle.</span><span class="sxs-lookup"><span data-stu-id="701ff-232">This last operation is the actual transaction.</span></span>

<span data-ttu-id="701ff-233">En règle générale, un gestionnaire de commandes s’occupe d’un seul agrégat piloté par sa racine d’agrégat (entité racine).</span><span class="sxs-lookup"><span data-stu-id="701ff-233">Typically, a command handler deals with a single aggregate driven by its aggregate root (root entity).</span></span> <span data-ttu-id="701ff-234">Si plusieurs agrégats doivent être concernés par la réception d’une commande unique, vous pouvez utiliser des événements de domaine pour propager des états ou des actions sur plusieurs agrégats.</span><span class="sxs-lookup"><span data-stu-id="701ff-234">If multiple aggregates should be impacted by the reception of a single command, you could use domain events to propagate states or actions across multiple aggregates.</span></span>

<span data-ttu-id="701ff-235">L’important ici est que, quand une commande est en cours de traitement, toute la logique de domaine soit à l’intérieur du modèle de domaine (les agrégats), entièrement encapsulée et prête pour les tests unitaires.</span><span class="sxs-lookup"><span data-stu-id="701ff-235">The important point here is that when a command is being processed, all the domain logic should be inside the domain model (the aggregates), fully encapsulated and ready for unit testing.</span></span> <span data-ttu-id="701ff-236">Le gestionnaire de commandes sert simplement de moyen d’obtenir le modèle de domaine auprès de la base de données et, pour finir, d’indiquer à la couche d’infrastructure (dépôts) de rendre les modifications persistantes quand le modèle est modifié.</span><span class="sxs-lookup"><span data-stu-id="701ff-236">The command handler just acts as a way to get the domain model from the database, and as the final step, to tell the infrastructure layer (repositories) to persist the changes when the model is changed.</span></span> <span data-ttu-id="701ff-237">L’avantage de cette approche est que vous pouvez refactoriser la logique de domaine dans un modèle de domaine isolé, entièrement encapsulé, riche et comportemental sans modifier le code dans les couches Application ou d’infrastructure, qui forment le niveau de raccordement (gestionnaires de commandes, API web, dépôts, etc.).</span><span class="sxs-lookup"><span data-stu-id="701ff-237">The advantage of this approach is that you can refactor the domain logic in an isolated, fully encapsulated, rich, behavioral domain model without changing code in the application or infrastructure layers, which are the plumbing level (command handlers, Web API, repositories, etc.).</span></span>

<span data-ttu-id="701ff-238">Lorsque les gestionnaires de commandes deviennent complexes, avec trop de logique, un « code smell » peut se produire.</span><span class="sxs-lookup"><span data-stu-id="701ff-238">When command handlers get complex, with too much logic, that can be a code smell.</span></span> <span data-ttu-id="701ff-239">Passez-les en revue et si vous trouvez la logique de domaine, refactorisez le code pour déplacer ce comportement de domaine vers les méthodes des objets de domaine (entité racine et enfant de l’agrégat).</span><span class="sxs-lookup"><span data-stu-id="701ff-239">Review them, and if you find domain logic, refactor the code to move that domain behavior to the methods of the domain objects (the aggregate root and child entity).</span></span>

<span data-ttu-id="701ff-240">En guise d’exemple de classe de gestionnaire de commandes, le code suivant montre la même `CreateOrderCommandHandler` classe que celle que vous avez vue au début de ce chapitre.</span><span class="sxs-lookup"><span data-stu-id="701ff-240">As an example of a command handler class, the following code shows the same `CreateOrderCommandHandler` class that you saw at the beginning of this chapter.</span></span> <span data-ttu-id="701ff-241">Nous voulons ici mettre en exergue la méthode Handle et les opérations effectuées avec les objets/agrégats du modèle de domaine.</span><span class="sxs-lookup"><span data-stu-id="701ff-241">In this case, we want to highlight the Handle method and the operations with the domain model objects/aggregates.</span></span>

```csharp
public class CreateOrderCommandHandler
    : IAsyncRequestHandler<CreateOrderCommand, bool>
{
    private readonly IOrderRepository _orderRepository;
    private readonly IIdentityService _identityService;
    private readonly IMediator _mediator;

    // Using DI to inject infrastructure persistence Repositories
    public CreateOrderCommandHandler(IMediator mediator,
                                     IOrderRepository orderRepository,
                                     IIdentityService identityService)
    {
        _orderRepository = orderRepository ??
                          throw new ArgumentNullException(nameof(orderRepository));
        _identityService = identityService ??
                          throw new ArgumentNullException(nameof(identityService));
        _mediator = mediator ??
                                 throw new ArgumentNullException(nameof(mediator));
    }

    public async Task<bool> Handle(CreateOrderCommand message)
    {
        // Create the Order AggregateRoot
        // Add child entities and value objects through the Order aggregate root
        // methods and constructor so validations, invariants, and business logic
        // make sure that consistency is preserved across the whole aggregate
        var address = new Address(message.Street, message.City, message.State,
                                  message.Country, message.ZipCode);
        var order = new Order(message.UserId, address, message.CardTypeId,
                              message.CardNumber, message.CardSecurityNumber,
                              message.CardHolderName, message.CardExpiration);

        foreach (var item in message.OrderItems)
        {
            order.AddOrderItem(item.ProductId, item.ProductName, item.UnitPrice,
                               item.Discount, item.PictureUrl, item.Units);
        }

        _orderRepository.Add(order);

        return await _orderRepository.UnitOfWork
            .SaveEntitiesAsync();
    }
}
```

<span data-ttu-id="701ff-242">Il s’agit des étapes supplémentaires que doit suivre un gestionnaire de commandes :</span><span class="sxs-lookup"><span data-stu-id="701ff-242">These are additional steps a command handler should take:</span></span>

- <span data-ttu-id="701ff-243">Utilisez les données de la commande pour utiliser les méthodes et le comportement de la racine d’agrégat.</span><span class="sxs-lookup"><span data-stu-id="701ff-243">Use the command’s data to operate with the aggregate root’s methods and behavior.</span></span>

- <span data-ttu-id="701ff-244">En interne dans les objets de domaine, déclenchez des événements de domaine pendant l’exécution de la transaction, en sachant que cette action est transparente du point de vue du gestionnaire de commandes.</span><span class="sxs-lookup"><span data-stu-id="701ff-244">Internally within the domain objects, raise domain events while the transaction is executed, but that is transparent from a command handler point of view.</span></span>

- <span data-ttu-id="701ff-245">Si le résultat de l’opération de l’agrégat a réussi, une fois la transaction terminée, déclenchez les événements d’intégration.</span><span class="sxs-lookup"><span data-stu-id="701ff-245">If the aggregate’s operation result is successful and after the transaction is finished, raise integration events.</span></span> <span data-ttu-id="701ff-246">(Ces derniers peuvent également être déclenchés par des classes d’infrastructure comme les dépôts.)</span><span class="sxs-lookup"><span data-stu-id="701ff-246">(These might also be raised by infrastructure classes like repositories.)</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="701ff-247">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="701ff-247">Additional resources</span></span>

- <span data-ttu-id="701ff-248">**Mark Seemann. Au niveau des limites, les applications ne sont pas orientées objet** </span><span class="sxs-lookup"><span data-stu-id="701ff-248">**Mark Seemann. At the Boundaries, Applications are Not Object-Oriented** </span></span>\
  <https://blog.ploeh.dk/2011/05/31/AttheBoundaries,ApplicationsareNotObject-Oriented/>

- <span data-ttu-id="701ff-249">**Commands and events** </span><span class="sxs-lookup"><span data-stu-id="701ff-249">**Commands and events** </span></span>\
  <https://cqrs.nu/Faq/commands-and-events>

- <span data-ttu-id="701ff-250">**What does a command handler do?**</span><span class="sxs-lookup"><span data-stu-id="701ff-250">**What does a command handler do?**</span></span> \
  <https://cqrs.nu/Faq/command-handlers>

- <span data-ttu-id="701ff-251">**Jimmy bogard. Modèles de commande de domaine : gestionnaires** </span><span class="sxs-lookup"><span data-stu-id="701ff-251">**Jimmy Bogard. Domain Command Patterns – Handlers** </span></span>\
  <https://jimmybogard.com/domain-command-patterns-handlers/>

- <span data-ttu-id="701ff-252">**Jimmy bogard. Modèles de commande de domaine-**  \ de validation</span><span class="sxs-lookup"><span data-stu-id="701ff-252">**Jimmy Bogard. Domain Command Patterns – Validation** \</span></span>
  <https://jimmybogard.com/domain-command-patterns-validation/>

## <a name="the-command-process-pipeline-how-to-trigger-a-command-handler"></a><span data-ttu-id="701ff-253">Pipeline du processus de commande : comment déclencher un gestionnaire de commandes</span><span class="sxs-lookup"><span data-stu-id="701ff-253">The Command process pipeline: how to trigger a command handler</span></span>

<span data-ttu-id="701ff-254">La question suivante a trait à la manière d’appeler un gestionnaire de commandes.</span><span class="sxs-lookup"><span data-stu-id="701ff-254">The next question is how to invoke a command handler.</span></span> <span data-ttu-id="701ff-255">Vous pouvez l’appeler manuellement à partir de chaque contrôleur ASP.NET Core connexe.</span><span class="sxs-lookup"><span data-stu-id="701ff-255">You could manually call it from each related ASP.NET Core controller.</span></span> <span data-ttu-id="701ff-256">Toutefois, cette approche paraît trop couplée et n’est donc pas idéale.</span><span class="sxs-lookup"><span data-stu-id="701ff-256">However, that approach would be too coupled and is not ideal.</span></span>

<span data-ttu-id="701ff-257">Les deux autres options principales, qui sont recommandées, sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="701ff-257">The other two main options, which are the recommended options, are:</span></span>

- <span data-ttu-id="701ff-258">Par le biais d’un artefact de modèle Médiateur en mémoire.</span><span class="sxs-lookup"><span data-stu-id="701ff-258">Through an in-memory Mediator pattern artifact.</span></span>

- <span data-ttu-id="701ff-259">Avec une file d’attente de messages asynchrones, entre les contrôleurs et les gestionnaires.</span><span class="sxs-lookup"><span data-stu-id="701ff-259">With an asynchronous message queue, in between controllers and handlers.</span></span>

### <a name="use-the-mediator-pattern-in-memory-in-the-command-pipeline"></a><span data-ttu-id="701ff-260">Utiliser le modèle de médiateur (en mémoire) dans le pipeline de commandes</span><span class="sxs-lookup"><span data-stu-id="701ff-260">Use the Mediator pattern (in-memory) in the command pipeline</span></span>

<span data-ttu-id="701ff-261">Comme le montre la figure 7-25, dans une approche CQRS, vous utilisez un médiateur intelligent, similaire à un bus en mémoire, suffisamment intelligent pour effectuer une redirection vers le gestionnaire de commandes approprié en fonction du type de commande ou d’objet de transfert de données reçu.</span><span class="sxs-lookup"><span data-stu-id="701ff-261">As shown in Figure 7-25, in a CQRS approach you use an intelligent mediator, similar to an in-memory bus, which is smart enough to redirect to the right command handler based on the type of the command or DTO being received.</span></span> <span data-ttu-id="701ff-262">Les flèches noires entre les composants représentent les dépendances entre les objets (dans de nombreux cas, injectées par injection de dépendances) avec leurs interactions associées.</span><span class="sxs-lookup"><span data-stu-id="701ff-262">The single black arrows between components represent the dependencies between objects (in many cases, injected through DI) with their related interactions.</span></span>

![Diagramme montrant un flot de données plus détaillé entre le client et la base de données.](./media/microservice-application-layer-implementation-web-api/mediator-cqrs-microservice.png)

<span data-ttu-id="701ff-264">**Figure 7-25**.</span><span class="sxs-lookup"><span data-stu-id="701ff-264">**Figure 7-25**.</span></span> <span data-ttu-id="701ff-265">Utilisation du modèle Médiateur dans le processus dans un microservice CQRS unique</span><span class="sxs-lookup"><span data-stu-id="701ff-265">Using the Mediator pattern in process in a single CQRS microservice</span></span>

<span data-ttu-id="701ff-266">Le diagramme ci-dessus montre un zoom avant à partir de l’image 7-24 : le contrôleur ASP.NET Core envoie la commande au pipeline de commande de médiateur, afin qu’ils obtiennent le gestionnaire approprié.</span><span class="sxs-lookup"><span data-stu-id="701ff-266">The above diagram shows a zoom-in from image 7-24: the ASP.NET Core controller sends the command to MediatR's command pipeline, so they get to the appropriate handler.</span></span>

<span data-ttu-id="701ff-267">L’utilisation du modèle Médiateur prend tout son sens dans les applications d’entreprise, où les demandes de traitement peuvent devenir compliquées.</span><span class="sxs-lookup"><span data-stu-id="701ff-267">The reason that using the Mediator pattern makes sense is that in enterprise applications, the processing requests can get complicated.</span></span> <span data-ttu-id="701ff-268">Vous avez besoin de pouvoir ajouter un nombre ouvert de problèmes transversaux comme la journalisation, les validations, l’audit et la sécurité.</span><span class="sxs-lookup"><span data-stu-id="701ff-268">You want to be able to add an open number of cross-cutting concerns like logging, validations, audit, and security.</span></span> <span data-ttu-id="701ff-269">Dans ce cas, vous pouvez compter sur un pipeline de médiateur (consultez [Modèle Médiateur](https://en.wikipedia.org/wiki/Mediator_pattern)) pour fournir un moyen à ces comportements supplémentaires ou problèmes transversaux.</span><span class="sxs-lookup"><span data-stu-id="701ff-269">In these cases, you can rely on a mediator pipeline (see [Mediator pattern](https://en.wikipedia.org/wiki/Mediator_pattern)) to provide a means for these extra behaviors or cross-cutting concerns.</span></span>

<span data-ttu-id="701ff-270">Un médiateur est un objet qui encapsule le « comment » de ce processus : il coordonne l’exécution en fonction de l’état, la façon dont un gestionnaire de commandes est appelé ou la charge utile que vous fournissez au gestionnaire.</span><span class="sxs-lookup"><span data-stu-id="701ff-270">A mediator is an object that encapsulates the “how” of this process: it coordinates execution based on state, the way a command handler is invoked, or the payload you provide to the handler.</span></span> <span data-ttu-id="701ff-271">Avec un composant médiateur, vous pouvez appliquer des problèmes transversaux de manière centralisée et transparente en appliquant des éléments décoratifs (ou [comportements de pipeline](https://github.com/jbogard/MediatR/wiki/Behaviors) depuis [MediatR 3](https://www.nuget.org/packages/MediatR/3.0.0)).</span><span class="sxs-lookup"><span data-stu-id="701ff-271">With a mediator component you can apply cross-cutting concerns in a centralized and transparent way by applying decorators (or [pipeline behaviors](https://github.com/jbogard/MediatR/wiki/Behaviors) since [MediatR 3](https://www.nuget.org/packages/MediatR/3.0.0)).</span></span> <span data-ttu-id="701ff-272">Pour plus d’informations, consultez le [modèle Élément décoratif](https://en.wikipedia.org/wiki/Decorator_pattern).</span><span class="sxs-lookup"><span data-stu-id="701ff-272">For more information, see the [Decorator pattern](https://en.wikipedia.org/wiki/Decorator_pattern).</span></span>

<span data-ttu-id="701ff-273">Les éléments décoratifs et les comportements sont similaires à la [programmation orientée aspect](https://en.wikipedia.org/wiki/Aspect-oriented_programming), uniquement appliquée à un pipeline de processus spécifique géré par le composant médiateur.</span><span class="sxs-lookup"><span data-stu-id="701ff-273">Decorators and behaviors are similar to [Aspect Oriented Programming (AOP)](https://en.wikipedia.org/wiki/Aspect-oriented_programming), only applied to a specific process pipeline managed by the mediator component.</span></span> <span data-ttu-id="701ff-274">Les aspects en programmation orientée aspect qui implémentent des problèmes transversaux sont appliqués selon les *tisseurs d’aspect* injectés au moment de la compilation ou en fonction de l’interception des appels d’objet.</span><span class="sxs-lookup"><span data-stu-id="701ff-274">Aspects in AOP that implement cross-cutting concerns are applied based on *aspect weavers* injected at compilation time or based on object call interception.</span></span> <span data-ttu-id="701ff-275">Les deux approches usuelles de la programmation orientée aspect sont parfois considérées comme « magiques », car il n’est pas facile de voir comment leur travail est effectué.</span><span class="sxs-lookup"><span data-stu-id="701ff-275">Both typical AOP approaches are sometimes said to work "like magic," because it is not easy to see how AOP does its work.</span></span> <span data-ttu-id="701ff-276">Lorsque qu’il s’agit de traiter des problèmes ou bogues graves, la programmation orientée aspect peut rendre le débogage difficile.</span><span class="sxs-lookup"><span data-stu-id="701ff-276">When dealing with serious issues or bugs, AOP can be difficult to debug.</span></span> <span data-ttu-id="701ff-277">En revanche, ces éléments décoratifs/comportements sont explicites et uniquement appliqués dans le contexte du médiateur, donc le débogage est beaucoup plus prévisible et facile.</span><span class="sxs-lookup"><span data-stu-id="701ff-277">On the other hand, these decorators/behaviors are explicit and applied only in the context of the mediator, so debugging is much more predictable and easy.</span></span>

<span data-ttu-id="701ff-278">Par exemple, dans le microservice de passation de commandes eShopOnContainers, nous avons implémenté deux exemples de comportements, une classe [LogBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/LoggingBehavior.cs) et une classe [ValidatorBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/ValidatorBehavior.cs).</span><span class="sxs-lookup"><span data-stu-id="701ff-278">For example, in the eShopOnContainers ordering microservice, we implemented two sample behaviors, a [LogBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/LoggingBehavior.cs) class and a [ValidatorBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/ValidatorBehavior.cs) class.</span></span> <span data-ttu-id="701ff-279">L’implémentation des comportements est expliquée dans la section suivante en illustrant la façon dont eShopOnContainers utilise les [comportements](https://github.com/jbogard/MediatR/wiki/Behaviors) [médiateurr 3](https://www.nuget.org/packages/MediatR/3.0.0) .</span><span class="sxs-lookup"><span data-stu-id="701ff-279">The implementation of the behaviors is explained in the next section by showing how eShopOnContainers uses [MediatR 3](https://www.nuget.org/packages/MediatR/3.0.0) [behaviors](https://github.com/jbogard/MediatR/wiki/Behaviors).</span></span>

### <a name="use-message-queues-out-of-proc-in-the-commands-pipeline"></a><span data-ttu-id="701ff-280">Utiliser de files d’attente de messages (hors processus) dans le pipeline de commandes</span><span class="sxs-lookup"><span data-stu-id="701ff-280">Use message queues (out-of-proc) in the command’s pipeline</span></span>

<span data-ttu-id="701ff-281">Un autre choix consiste à utiliser des messages asynchrones basés sur des services Broker ou des files d’attente de messages, comme le montre la figure 7-26.</span><span class="sxs-lookup"><span data-stu-id="701ff-281">Another choice is to use asynchronous messages based on brokers or message queues, as shown in Figure 7-26.</span></span> <span data-ttu-id="701ff-282">Vous pouvez aussi combiner cette option avec le composant médiateur juste avant le gestionnaire de commandes.</span><span class="sxs-lookup"><span data-stu-id="701ff-282">That option could also be combined with the mediator component right before the command handler.</span></span>

![Diagramme montrant le flux de données à l’aide d’une file d’attente de messages haute disponibilité.](./media/microservice-application-layer-implementation-web-api/add-ha-message-queue.png)

<span data-ttu-id="701ff-284">**Figure 7-26**.</span><span class="sxs-lookup"><span data-stu-id="701ff-284">**Figure 7-26**.</span></span> <span data-ttu-id="701ff-285">Utilisation de files d’attente de messages (communication hors processus et entre processus) avec des commandes CQRS</span><span class="sxs-lookup"><span data-stu-id="701ff-285">Using message queues (out of process and inter-process communication) with CQRS commands</span></span>

<span data-ttu-id="701ff-286">Le pipeline de commandes peut également être géré par une file d’attente à haute disponibilité pour délivrer les commandes au gestionnaire approprié.</span><span class="sxs-lookup"><span data-stu-id="701ff-286">Command's pipeline can also be handled by a high availability message queue to deliver the commands to the appropriate handler.</span></span> <span data-ttu-id="701ff-287">L’utilisation de files d’attente de messages pour accepter les commandes peut compliquer davantage votre pipeline de commande, car vous devez probablement diviser le pipeline en deux processus connectés par le biais de la file d’attente de messages externes.</span><span class="sxs-lookup"><span data-stu-id="701ff-287">Using message queues to accept the commands can further complicate your command’s pipeline, because you will probably need to split the pipeline into two processes connected through the external message queue.</span></span> <span data-ttu-id="701ff-288">Néanmoins, vous devez l’utiliser si vous avez besoin d’une meilleure scalabilité et de performances améliorées en fonction de la messagerie asynchrone.</span><span class="sxs-lookup"><span data-stu-id="701ff-288">Still, it should be used if you need to have improved scalability and performance based on asynchronous messaging.</span></span> <span data-ttu-id="701ff-289">Considérez que, dans le cas de la figure 7-26, le contrôleur envoie simplement le message de commande dans la file d’attente, puis retourne.</span><span class="sxs-lookup"><span data-stu-id="701ff-289">Consider that in the case of Figure 7-26, the controller just posts the command message into the queue and returns.</span></span> <span data-ttu-id="701ff-290">Ensuite, les gestionnaires de commandes traitent les messages à leur propre rythme.</span><span class="sxs-lookup"><span data-stu-id="701ff-290">Then the command handlers process the messages at their own pace.</span></span> <span data-ttu-id="701ff-291">C’est l’énorme avantage des files d’attente : elles peuvent agir en tant que mémoire tampon quand le besoin de scalabilité est considérable, par exemple pour des stocks ou tout autre scénario impliquant un volume élevé de données d’entrée.</span><span class="sxs-lookup"><span data-stu-id="701ff-291">That is a great benefit of queues: the message queue can act as a buffer in cases when hyper scalability is needed, such as for stocks or any other scenario with a high volume of ingress data.</span></span>

<span data-ttu-id="701ff-292">Toutefois, en raison de la nature asynchrone des files d’attente, vous devez déterminer comment communiquer avec l’application cliente à propos de la réussite ou de l’échec du processus de la commande.</span><span class="sxs-lookup"><span data-stu-id="701ff-292">However, because of the asynchronous nature of message queues, you need to figure out how to communicate with the client application about the success or failure of the command’s process.</span></span> <span data-ttu-id="701ff-293">En règle générale, vous ne devez jamais utiliser des commandes de type « déclencher et oublier ».</span><span class="sxs-lookup"><span data-stu-id="701ff-293">As a rule, you should never use “fire and forget” commands.</span></span> <span data-ttu-id="701ff-294">Chaque application métier doit savoir si une commande a été traitée correctement, ou au moins validée et acceptée.</span><span class="sxs-lookup"><span data-stu-id="701ff-294">Every business application needs to know if a command was processed successfully, or at least validated and accepted.</span></span>

<span data-ttu-id="701ff-295">Par conséquent, être en mesure de répondre au client après la validation d’un message de commande envoyé à une file d’attente asynchrone complexifie votre système, par rapport à un processus de commande in-process qui retourne le résultat de l’opération après avoir exécuté la transaction.</span><span class="sxs-lookup"><span data-stu-id="701ff-295">Thus, being able to respond to the client after validating a command message that was submitted to an asynchronous queue adds complexity to your system, as compared to an in-process command process that returns the operation’s result after running the transaction.</span></span> <span data-ttu-id="701ff-296">L’utilisation de files d’attente peut vous obliger à retourner le résultat du processus de commande par le biais d’autres messages de résultat d’opération, ce qui nécessite des composants supplémentaires et une communication personnalisée dans votre système.</span><span class="sxs-lookup"><span data-stu-id="701ff-296">Using queues, you might need to return the result of the command process through other operation result messages, which will require additional components and custom communication in your system.</span></span>

<span data-ttu-id="701ff-297">De plus, les commandes asynchrones sont des commandes unidirectionnelles, inutiles dans de nombreux cas, comme expliqué dans l’intéressant échange suivant entre Burtsev Alexey et Greg Young au cours d’une [conversation en ligne](https://groups.google.com/forum/#!msg/dddcqrs/xhJHVxDx2pM/WP9qP8ifYCwJ) :</span><span class="sxs-lookup"><span data-stu-id="701ff-297">Additionally, async commands are one-way commands, which in many cases might not be needed, as is explained in the following interesting exchange between Burtsev Alexey and Greg Young in an [online conversation](https://groups.google.com/forum/#!msg/dddcqrs/xhJHVxDx2pM/WP9qP8ifYCwJ):</span></span>

> <span data-ttu-id="701ff-298">\[Burtsev Alexey\] Je trouve beaucoup de code où les informaticiens utilisent une gestion de commandes asynchrone ou des messages de commande unidirectionnels sans aucune raison de le faire (ils n’effectuent pas une opération longue, ils n’exécutent pas du code asynchrone externe, ils ne franchissent même pas la limite de l’application pour utiliser un bus de messages).</span><span class="sxs-lookup"><span data-stu-id="701ff-298">\[Burtsev Alexey\] I find lots of code where people use async command handling or one way command messaging without any reason to do so (they are not doing some long operation, they are not executing external async code, they do not even cross application boundary to be using message bus).</span></span> <span data-ttu-id="701ff-299">Pourquoi introduisent-ils cette complexité inutile ?</span><span class="sxs-lookup"><span data-stu-id="701ff-299">Why do they introduce this unnecessary complexity?</span></span> <span data-ttu-id="701ff-300">En fait, je n’ai jamais vu un exemple de code CQRS avec des gestionnaires de commandes bloquants jusqu’à présent, même si cela fonctionnerait parfaitement dans la plupart des cas.</span><span class="sxs-lookup"><span data-stu-id="701ff-300">And actually, I haven't seen a CQRS code example with blocking command handlers so far, though it will work just fine in most cases.</span></span>
>
> <span data-ttu-id="701ff-301">\[Greg Young\] \[...\] une commande asynchrone n’existe pas ; Il s’agit en fait d’un autre événement.</span><span class="sxs-lookup"><span data-stu-id="701ff-301">\[Greg Young\] \[...\] an asynchronous command doesn't exist; it's actually another event.</span></span> <span data-ttu-id="701ff-302">Si je dois accepter ce que vous m’envoyez et déclencher un événement si je ne suis pas d’accord, alors ce n’est plus vous qui me dites de faire quelque chose, \[c’est-à-dire que ce n’est pas une commande\].</span><span class="sxs-lookup"><span data-stu-id="701ff-302">If I must accept what you send me and raise an event if I disagree, it's no longer you telling me to do something \[that is, it’s not a command\].</span></span> <span data-ttu-id="701ff-303">Mais vous qui me dites que quelque chose a été fait.</span><span class="sxs-lookup"><span data-stu-id="701ff-303">It's you telling me something has been done.</span></span> <span data-ttu-id="701ff-304">La différence peut sembler légère dans un premier temps, mais ses implications sont nombreuses.</span><span class="sxs-lookup"><span data-stu-id="701ff-304">This seems like a slight difference at first, but it has many implications.</span></span>

<span data-ttu-id="701ff-305">Les commandes asynchrones augmentent considérablement la complexité d’un système, car il n’existe aucun moyen simple d’indiquer des échecs.</span><span class="sxs-lookup"><span data-stu-id="701ff-305">Asynchronous commands greatly increase the complexity of a system, because there is no simple way to indicate failures.</span></span> <span data-ttu-id="701ff-306">Ainsi, les commandes asynchrones ne sont pas recommandées si ce n’est quand il existe des besoins de mise à l’échelle ou dans des cas spéciaux de communication des microservices internes par le biais d’une messagerie.</span><span class="sxs-lookup"><span data-stu-id="701ff-306">Therefore, asynchronous commands are not recommended other than when scaling requirements are needed or in special cases when communicating the internal microservices through messaging.</span></span> <span data-ttu-id="701ff-307">Le cas échéant, vous devez concevoir un système de création de rapports et de récupération distinct pour les échecs.</span><span class="sxs-lookup"><span data-stu-id="701ff-307">In those cases, you must design a separate reporting and recovery system for failures.</span></span>

<span data-ttu-id="701ff-308">Dans la version initiale d’eShopOnContainers, nous avons décidé d’utiliser un traitement des commandes synchrone, qui démarre à partir de requêtes HTTP et qui est piloté par le modèle Médiateur.</span><span class="sxs-lookup"><span data-stu-id="701ff-308">In the initial version of eShopOnContainers, we decided to use synchronous command processing, started from HTTP requests and driven by the Mediator pattern.</span></span> <span data-ttu-id="701ff-309">Ce traitement vous permet de retourner facilement la réussite ou l’échec du processus, comme dans l’implémentation [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs).</span><span class="sxs-lookup"><span data-stu-id="701ff-309">That easily allows you to return the success or failure of the process, as in the [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) implementation.</span></span>

<span data-ttu-id="701ff-310">Dans tous les cas, cette décision doit se baser sur les besoins d’entreprise liés à votre application ou microservice.</span><span class="sxs-lookup"><span data-stu-id="701ff-310">In any case, this should be a decision based on your application’s or microservice’s business requirements.</span></span>

## <a name="implement-the-command-process-pipeline-with-a-mediator-pattern-mediatr"></a><span data-ttu-id="701ff-311">Implémenter le pipeline du processus de commande avec un modèle de médiateur (MediatR)</span><span class="sxs-lookup"><span data-stu-id="701ff-311">Implement the command process pipeline with a mediator pattern (MediatR)</span></span>

<span data-ttu-id="701ff-312">À titre d’exemple d’implémentation, le présent guide propose d’utiliser le pipeline in-process basé sur le modèle Médiateur pour diriger l’ingestion des commandes et acheminer les commandes, dans la mémoire, vers les gestionnaires de commandes appropriés.</span><span class="sxs-lookup"><span data-stu-id="701ff-312">As a sample implementation, this guide proposes using the in-process pipeline based on the Mediator pattern to drive command ingestion and route commands, in memory, to the right command handlers.</span></span> <span data-ttu-id="701ff-313">Le guide propose également d’appliquer des [comportements](https://github.com/jbogard/MediatR/wiki/Behaviors) pour séparer les problèmes transversaux.</span><span class="sxs-lookup"><span data-stu-id="701ff-313">The guide also proposes applying [behaviors](https://github.com/jbogard/MediatR/wiki/Behaviors) in order to separate cross-cutting concerns.</span></span>

<span data-ttu-id="701ff-314">Pour l’implémentation dans .NET Core, il existe plusieurs bibliothèques open source disponibles qui implémentent le modèle Médiateur.</span><span class="sxs-lookup"><span data-stu-id="701ff-314">For implementation in .NET Core, there are multiple open-source libraries available that implement the Mediator pattern.</span></span> <span data-ttu-id="701ff-315">La bibliothèque utilisée dans ce guide est la bibliothèque open source [MediatR](https://github.com/jbogard/MediatR) (créée par Jimmy Bogard), mais vous pouvez utiliser une autre approche.</span><span class="sxs-lookup"><span data-stu-id="701ff-315">The library used in this guide is the [MediatR](https://github.com/jbogard/MediatR) open-source library (created by Jimmy Bogard), but you could use another approach.</span></span> <span data-ttu-id="701ff-316">MediatR est une petite bibliothèque simple qui vous permet de traiter les messages en mémoire comme une commande, tout en appliquant des éléments décoratifs ou des comportements.</span><span class="sxs-lookup"><span data-stu-id="701ff-316">MediatR is a small and simple library that allows you to process in-memory messages like a command, while applying decorators or behaviors.</span></span>

<span data-ttu-id="701ff-317">L’utilisation du modèle Médiateur vous aide à réduire le couplage et à isoler les problèmes du travail demandé, tout en vous connectant automatiquement au gestionnaire qui effectue ce travail (ici, les gestionnaires de commandes).</span><span class="sxs-lookup"><span data-stu-id="701ff-317">Using the Mediator pattern helps you to reduce coupling and to isolate the concerns of the requested work, while automatically connecting to the handler that performs that work—in this case, to command handlers.</span></span>

<span data-ttu-id="701ff-318">Jimmy Bogard a précisé une autre bonne raison d’utiliser le modèle Médiateur quand il a révisé ce guide :</span><span class="sxs-lookup"><span data-stu-id="701ff-318">Another good reason to use the Mediator pattern was explained by Jimmy Bogard when reviewing this guide:</span></span>

> <span data-ttu-id="701ff-319">Je pense qu’il est intéressant de mentionner les tests ici : le modèle ouvre une fenêtre cohérente sur le comportement de votre système.</span><span class="sxs-lookup"><span data-stu-id="701ff-319">I think it might be worth mentioning testing here – it provides a nice consistent window into the behavior of your system.</span></span> <span data-ttu-id="701ff-320">Demande, réponse. Nous avons constaté que cet aspect est très utile pour créer des tests qui se comportent de manière cohérente.</span><span class="sxs-lookup"><span data-stu-id="701ff-320">Request-in, response-out. We’ve found that aspect quite valuable in building consistently behaving tests.</span></span>

<span data-ttu-id="701ff-321">Tout d’abord, examinons un exemple de contrôleur WebAPI dans lequel vous utilisez en fait l’objet médiateur.</span><span class="sxs-lookup"><span data-stu-id="701ff-321">First, let’s look at a sample WebAPI controller where you actually would use the mediator object.</span></span> <span data-ttu-id="701ff-322">Si vous n’utilisez pas l’objet médiateur, vous devez injecter toutes les dépendances de ce contrôleur, comme un objet enregistreur d’événements et d’autres.</span><span class="sxs-lookup"><span data-stu-id="701ff-322">If you weren't using the mediator object, you'd need to inject all the dependencies for that controller, things like a logger object and others.</span></span> <span data-ttu-id="701ff-323">Ainsi, le constructeur est assez complexe.</span><span class="sxs-lookup"><span data-stu-id="701ff-323">Therefore, the constructor would be quite complicated.</span></span> <span data-ttu-id="701ff-324">En revanche, si vous utilisez l’objet médiateur, le constructeur de votre contrôleur peut être beaucoup plus simple, avec seulement quelques dépendances plutôt que de nombreuses dépendances si vous n’en avez qu’une par opération transversale, comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="701ff-324">On the other hand, if you use the mediator object, the constructor of your controller can be a lot simpler, with just a few dependencies instead of many dependencies if you had one per cross-cutting operation, as in the following example:</span></span>

```csharp
public class MyMicroserviceController : Controller
{
    public MyMicroserviceController(IMediator mediator,
                                    IMyMicroserviceQueries microserviceQueries)
    {
        // ...
    }
}
```

<span data-ttu-id="701ff-325">Vous pouvez voir que le médiateur fournit un constructeur de contrôleur d’API web propre et léger.</span><span class="sxs-lookup"><span data-stu-id="701ff-325">You can see that the mediator provides a clean and lean Web API controller constructor.</span></span> <span data-ttu-id="701ff-326">De plus, dans les méthodes du contrôleur, le code permettant d’envoyer une commande à l’objet médiateur occupe quasiment une seule ligne :</span><span class="sxs-lookup"><span data-stu-id="701ff-326">In addition, within the controller methods, the code to send a command to the mediator object is almost one line:</span></span>

```csharp
[Route("new")]
[HttpPost]
public async Task<IActionResult> ExecuteBusinessOperation([FromBody]RunOpCommand
                                                               runOperationCommand)
{
    var commandResult = await _mediator.SendAsync(runOperationCommand);

    return commandResult ? (IActionResult)Ok() : (IActionResult)BadRequest();
}
```

### <a name="implement-idempotent-commands"></a><span data-ttu-id="701ff-327">Implémenter des commandes idempotentes</span><span class="sxs-lookup"><span data-stu-id="701ff-327">Implement idempotent Commands</span></span>

<span data-ttu-id="701ff-328">Dans **eShopOnContainers**, un exemple plus avancé que le précédent envoie un objet CreateOrderCommand à partir du microservice Ordering.</span><span class="sxs-lookup"><span data-stu-id="701ff-328">In **eShopOnContainers**, a more advanced example than the above is submitting a CreateOrderCommand object from the Ordering microservice.</span></span> <span data-ttu-id="701ff-329">Toutefois, étant donné que le processus d’entreprise de commande est un peu plus complexe et, dans notre cas, il commence dans le microservice du panier, cette action consistant à soumettre l’objet CreateOrderCommand est effectuée à partir d’un gestionnaire d’événements d’intégration nommé [UserCheckoutAcceptedIntegrationEventHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/IntegrationEvents/EventHandling/UserCheckoutAcceptedIntegrationEventHandler.cs) au lieu d’un contrôleur WebAPI simple appelé à partir de l’application cliente, comme dans l’exemple plus simple précédent.</span><span class="sxs-lookup"><span data-stu-id="701ff-329">But since the Ordering business process is a bit more complex and, in our case, it actually starts in the Basket microservice, this action of submitting the CreateOrderCommand object is performed from an integration-event handler named [UserCheckoutAcceptedIntegrationEventHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/IntegrationEvents/EventHandling/UserCheckoutAcceptedIntegrationEventHandler.cs) instead of a simple WebAPI controller called from the client App as in the previous simpler example.</span></span>

<span data-ttu-id="701ff-330">Néanmoins, l’action d’envoi de la commande à MediatR est assez similaire, comme le montre le code suivant.</span><span class="sxs-lookup"><span data-stu-id="701ff-330">Nevertheless, the action of submitting the Command to MediatR is pretty similar, as shown in the following code.</span></span>

```csharp
var createOrderCommand = new CreateOrderCommand(eventMsg.Basket.Items,
                                                eventMsg.UserId, eventMsg.City,
                                                eventMsg.Street, eventMsg.State,
                                                eventMsg.Country, eventMsg.ZipCode,
                                                eventMsg.CardNumber,
                                                eventMsg.CardHolderName,
                                                eventMsg.CardExpiration,
                                                eventMsg.CardSecurityNumber,
                                                eventMsg.CardTypeId);

var requestCreateOrder = new IdentifiedCommand<CreateOrderCommand,bool>(createOrderCommand,
                                                                        eventMsg.RequestId);
result = await _mediator.Send(requestCreateOrder);
```

<span data-ttu-id="701ff-331">Toutefois, ce cas est aussi un peu plus avancé, car nous implémentons également des commandes idempotentes.</span><span class="sxs-lookup"><span data-stu-id="701ff-331">However, this case is also a little bit more advanced because we’re also implementing idempotent commands.</span></span> <span data-ttu-id="701ff-332">Le processus CreateOrderCommand doit être idempotent, donc si le même message est dupliqué par le biais du réseau, pour une raison quelconque, comme de nouvelles tentatives, la même commande commerciale n’est traitée qu’une seule fois.</span><span class="sxs-lookup"><span data-stu-id="701ff-332">The CreateOrderCommand process should be idempotent, so if the same message comes duplicated through the network, because of any reason, like retries, the same business order will be processed just once.</span></span>

<span data-ttu-id="701ff-333">Ceci est implémenté en wrappant la commande métier (dans ce cas CreateOrderCommand) et en l’incorporant dans une IdentifiedCommand générique suivi par un ID de chaque message arrivant sur le réseau et devant être idempotent.</span><span class="sxs-lookup"><span data-stu-id="701ff-333">This is implemented by wrapping the business command (in this case CreateOrderCommand) and embedding it into a generic IdentifiedCommand which is tracked by an ID of every message coming through the network that has to be idempotent.</span></span>

<span data-ttu-id="701ff-334">Dans le code ci-dessous, vous pouvez voir qu’IdentifiedCommand n’est rien d’autre qu’un objet de transfert de données avec un ID et l’objet commande métier inclus dans un wrapper.</span><span class="sxs-lookup"><span data-stu-id="701ff-334">In the code below, you can see that the IdentifiedCommand is nothing more than a DTO with and ID plus the wrapped business command object.</span></span>

```csharp
public class IdentifiedCommand<T, R> : IRequest<R>
    where T : IRequest<R>
{
    public T Command { get; }
    public Guid Id { get; }
    public IdentifiedCommand(T command, Guid id)
    {
        Command = command;
        Id = id;
    }
}
```

<span data-ttu-id="701ff-335">Ensuite, le CommandHandler de l’IdentifiedCommand nommé [IdentifiedCommandHandler.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Commands/IdentifiedCommandHandler.cs) vérifie en gros si l’ID qui arrive dans le message existe déjà dans une table.</span><span class="sxs-lookup"><span data-stu-id="701ff-335">Then the CommandHandler for the IdentifiedCommand named [IdentifiedCommandHandler.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Commands/IdentifiedCommandHandler.cs) will basically check if the ID coming as part of the message already exists in a table.</span></span> <span data-ttu-id="701ff-336">S’il existe déjà, cette commande n’est pas retraitée, donc elle se comporte comme une commande idempotente.</span><span class="sxs-lookup"><span data-stu-id="701ff-336">If it already exists, that command won’t be processed again, so it behaves as an idempotent command.</span></span> <span data-ttu-id="701ff-337">Ce code d’infrastructure est exécuté par l’appel de méthode `_requestManager.ExistAsync` ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="701ff-337">That infrastructure code is performed by the `_requestManager.ExistAsync` method call below.</span></span>

```csharp
// IdentifiedCommandHandler.cs
public class IdentifiedCommandHandler<T, R> :
                                   IAsyncRequestHandler<IdentifiedCommand<T, R>, R>
                                   where T : IRequest<R>
{
    private readonly IMediator _mediator;
    private readonly IRequestManager _requestManager;

    public IdentifiedCommandHandler(IMediator mediator,
                                    IRequestManager requestManager)
    {
        _mediator = mediator;
        _requestManager = requestManager;
    }

    protected virtual R CreateResultForDuplicateRequest()
    {
        return default(R);
    }

    public async Task<R> Handle(IdentifiedCommand<T, R> message)
    {
        var alreadyExists = await _requestManager.ExistAsync(message.Id);
        if (alreadyExists)
        {
            return CreateResultForDuplicateRequest();
        }
        else
        {
            await _requestManager.CreateRequestForCommandAsync<T>(message.Id);

            // Send the embedded business command to mediator
            // so it runs its related CommandHandler
            var result = await _mediator.Send(message.Command);

            return result;
        }
    }
}
```

<span data-ttu-id="701ff-338">Étant donné qu’IdentifiedCommand agit en tant qu’enveloppe de la commande métier, quand la commande métier a besoin d’être traitée parce qu’elle n’est pas un ID répété, alors cette commande métier interne est acceptée, puis renvoyée au médiateur, comme dans la dernière partie du code ci-dessus pendant l’exécution de `_mediator.Send(message.Command)`, à partir d’[IdentifiedCommandHandler.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Commands/IdentifiedCommandHandler.cs).</span><span class="sxs-lookup"><span data-stu-id="701ff-338">Since the IdentifiedCommand acts like a business command’s envelope, when the business command needs to be processed because it is not a repeated Id, then it takes that inner business command and re-submits it to Mediator, as in the last part of the code shown above when running `_mediator.Send(message.Command)`, from the [IdentifiedCommandHandler.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Commands/IdentifiedCommandHandler.cs).</span></span>

<span data-ttu-id="701ff-339">Ce faisant, le gestionnaire de commandes métier, dans ce cas [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs), qui exécute des transactions dans la base de données Ordering, est lié et exécuté, comme le montre le code suivant.</span><span class="sxs-lookup"><span data-stu-id="701ff-339">When doing that, it will link and run the business command handler, in this case, the [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) which is running transactions against the Ordering database, as shown in the following code.</span></span>

```csharp
// CreateOrderCommandHandler.cs
public class CreateOrderCommandHandler
                                   : IAsyncRequestHandler<CreateOrderCommand, bool>
{
    private readonly IOrderRepository _orderRepository;
    private readonly IIdentityService _identityService;
    private readonly IMediator _mediator;

    // Using DI to inject infrastructure persistence Repositories
    public CreateOrderCommandHandler(IMediator mediator,
                                     IOrderRepository orderRepository,
                                     IIdentityService identityService)
    {
        _orderRepository = orderRepository ??
                          throw new ArgumentNullException(nameof(orderRepository));
        _identityService = identityService ??
                          throw new ArgumentNullException(nameof(identityService));
        _mediator = mediator ??
                                 throw new ArgumentNullException(nameof(mediator));
    }

    public async Task<bool> Handle(CreateOrderCommand message)
    {
        // Add/Update the Buyer AggregateRoot
        var address = new Address(message.Street, message.City, message.State,
                                  message.Country, message.ZipCode);
        var order = new Order(message.UserId, address, message.CardTypeId,
                              message.CardNumber, message.CardSecurityNumber,
                              message.CardHolderName, message.CardExpiration);

        foreach (var item in message.OrderItems)
        {
            order.AddOrderItem(item.ProductId, item.ProductName, item.UnitPrice,
                               item.Discount, item.PictureUrl, item.Units);
        }

        _orderRepository.Add(order);

        return await _orderRepository.UnitOfWork
            .SaveEntitiesAsync();
    }
}
```

### <a name="register-the-types-used-by-mediatr"></a><span data-ttu-id="701ff-340">Inscrire les types utilisés par MediatR</span><span class="sxs-lookup"><span data-stu-id="701ff-340">Register the types used by MediatR</span></span>

<span data-ttu-id="701ff-341">Pour que MediatR ait connaissance de vos classes de gestionnaires de commandes, vous devez inscrire les classes du médiateur et les classes des gestionnaires de commandes dans votre conteneur IoC.</span><span class="sxs-lookup"><span data-stu-id="701ff-341">In order for MediatR to be aware of your command handler classes, you need to register the mediator classes and the command handler classes in your IoC container.</span></span> <span data-ttu-id="701ff-342">Par défaut, MediatR utilise Autofac en tant que conteneur IoC, mais vous pouvez également utiliser le conteneur IoC ASP.NET Core intégré ou tout autre conteneur pris en charge par MediatR.</span><span class="sxs-lookup"><span data-stu-id="701ff-342">By default, MediatR uses Autofac as the IoC container, but you can also use the built-in ASP.NET Core IoC container or any other container supported by MediatR.</span></span>

<span data-ttu-id="701ff-343">Le code suivant montre comment inscrire les types et commandes du médiateur quand vous utilisez des modules Autofac.</span><span class="sxs-lookup"><span data-stu-id="701ff-343">The following code shows how to register Mediator’s types and commands when using Autofac modules.</span></span>

```csharp
public class MediatorModule : Autofac.Module
{
    protected override void Load(ContainerBuilder builder)
    {
        builder.RegisterAssemblyTypes(typeof(IMediator).GetTypeInfo().Assembly)
            .AsImplementedInterfaces();

        // Register all the Command classes (they implement IAsyncRequestHandler)
        // in assembly holding the Commands
        builder.RegisterAssemblyTypes(
                              typeof(CreateOrderCommand).GetTypeInfo().Assembly).
                                   AsClosedTypesOf(typeof(IAsyncRequestHandler<,>));
        // Other types registration
        //...
    }
}
```

<span data-ttu-id="701ff-344">C’est là que « la magie opère » avec MediatR.</span><span class="sxs-lookup"><span data-stu-id="701ff-344">This is where “the magic happens” with MediatR.</span></span>

<span data-ttu-id="701ff-345">Étant donné que chaque gestionnaire de commandes implémente l’interface `IAsyncRequestHandler<T>` générique, quand vous inscrivez les assemblys, le code inscrit auprès de `RegisteredAssemblyTypes` tous les types marqués comme `IAsyncRequestHandler` pendant l’association des `CommandHandlers` à leurs `Commands`, grâce à la relation indiquée au niveau de la classe `CommandHandler`, comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="701ff-345">Because each command handler implements the generic `IAsyncRequestHandler<T>` interface, when registering the assemblies, the code registers with `RegisteredAssemblyTypes` all the types marked as `IAsyncRequestHandler` while relating the `CommandHandlers` with their `Commands`, thanks to the relationship stated at the `CommandHandler` class, as in the following example:</span></span>

```csharp
public class CreateOrderCommandHandler
  : IAsyncRequestHandler<CreateOrderCommand, bool>
{
```

<span data-ttu-id="701ff-346">Voici le code qui met en relation les commandes avec les gestionnaires de commandes.</span><span class="sxs-lookup"><span data-stu-id="701ff-346">That is the code that correlates commands with command handlers.</span></span> <span data-ttu-id="701ff-347">Le gestionnaire n’est qu’une simple classe, mais il hérite de `RequestHandler<T>`, où T est le type de commande, et MediatR vérifie qu’il est appelé avec la bonne charge utile (la commande).</span><span class="sxs-lookup"><span data-stu-id="701ff-347">The handler is just a simple class, but it inherits from `RequestHandler<T>`, where T is the command type, and MediatR makes sure it is invoked with the correct payload (the command).</span></span>

## <a name="apply-cross-cutting-concerns-when-processing-commands-with-the-behaviors-in-mediatr"></a><span data-ttu-id="701ff-348">Appliquer des préoccupations transversales lors du traitement des commandes avec les comportements dans MediatR</span><span class="sxs-lookup"><span data-stu-id="701ff-348">Apply cross-cutting concerns when processing commands with the Behaviors in MediatR</span></span>

<span data-ttu-id="701ff-349">Dernière chose : pouvoir appliquer des problèmes transversaux au pipeline médiateur.</span><span class="sxs-lookup"><span data-stu-id="701ff-349">There is one more thing: being able to apply cross-cutting concerns to the mediator pipeline.</span></span> <span data-ttu-id="701ff-350">Vous pouvez également voir, à la fin du code du module d’inscription Autofac, comment s’inscrit un type de comportement, et plus particulièrement, une classe LoggingBehavior personnalisée et une classe ValidatorBehavior.</span><span class="sxs-lookup"><span data-stu-id="701ff-350">You can also see at the end of the Autofac registration module code how it registers a behavior type, specifically, a custom LoggingBehavior class and a ValidatorBehavior class.</span></span> <span data-ttu-id="701ff-351">Vous pouvez cependant aussi ajouter d’autres comportements personnalisés.</span><span class="sxs-lookup"><span data-stu-id="701ff-351">But you could add other custom behaviors, too.</span></span>

```csharp
public class MediatorModule : Autofac.Module
{
    protected override void Load(ContainerBuilder builder)
    {
        builder.RegisterAssemblyTypes(typeof(IMediator).GetTypeInfo().Assembly)
            .AsImplementedInterfaces();

        // Register all the Command classes (they implement IAsyncRequestHandler)
        // in assembly holding the Commands
        builder.RegisterAssemblyTypes(
                              typeof(CreateOrderCommand).GetTypeInfo().Assembly).
                                   AsClosedTypesOf(typeof(IAsyncRequestHandler<,>));
        // Other types registration
        //...
        builder.RegisterGeneric(typeof(LoggingBehavior<,>)).
                                                   As(typeof(IPipelineBehavior<,>));
        builder.RegisterGeneric(typeof(ValidatorBehavior<,>)).
                                                   As(typeof(IPipelineBehavior<,>));
    }
}
```

<span data-ttu-id="701ff-352">Vous pouvez implémenter cette classe [LoggingBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/LoggingBehavior.cs) comme le code suivant, qui enregistre des informations sur le gestionnaire de commandes en cours d’exécution et sur sa réussite ou son échec.</span><span class="sxs-lookup"><span data-stu-id="701ff-352">That [LoggingBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/LoggingBehavior.cs) class can be implemented as the following code, which logs information about the command handler being executed and whether it was successful or not.</span></span>

```csharp
public class LoggingBehavior<TRequest, TResponse>
         : IPipelineBehavior<TRequest, TResponse>
{
    private readonly ILogger<LoggingBehavior<TRequest, TResponse>> _logger;
    public LoggingBehavior(ILogger<LoggingBehavior<TRequest, TResponse>> logger) =>
                                                                  _logger = logger;

    public async Task<TResponse> Handle(TRequest request,
                                        RequestHandlerDelegate<TResponse> next)
    {
        _logger.LogInformation($"Handling {typeof(TRequest).Name}");
        var response = await next();
        _logger.LogInformation($"Handled {typeof(TResponse).Name}");
        return response;
    }
}
```

<span data-ttu-id="701ff-353">En implémentant simplement cette classe de comportement et en l’inscrivant dans le pipeline (dans le MediatorModule plus haut), toutes les commandes traitées via MediatR consignent des informations sur l’exécution.</span><span class="sxs-lookup"><span data-stu-id="701ff-353">Just by implementing this behavior class and by registering it in the pipeline (in the MediatorModule above), all the commands processed through MediatR will be logging information about the execution.</span></span>

<span data-ttu-id="701ff-354">Le microservice de passation de commandes eShopOnContainers applique aussi un deuxième comportement pour les validations de base, la classe [ValidatorBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/ValidatorBehavior.cs) qui s’appuie sur la bibliothèque [FluentValidation](https://github.com/JeremySkinner/FluentValidation), comme le montre le code suivant :</span><span class="sxs-lookup"><span data-stu-id="701ff-354">The eShopOnContainers ordering microservice also applies a second behavior for basic validations, the [ValidatorBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/ValidatorBehavior.cs) class that relies on the [FluentValidation](https://github.com/JeremySkinner/FluentValidation) library, as shown in the following code:</span></span>

```csharp
public class ValidatorBehavior<TRequest, TResponse>
         : IPipelineBehavior<TRequest, TResponse>
{
    private readonly IValidator<TRequest>[] _validators;
    public ValidatorBehavior(IValidator<TRequest>[] validators) =>
                                                         _validators = validators;

    public async Task<TResponse> Handle(TRequest request,
                                        RequestHandlerDelegate<TResponse> next)
    {
        var failures = _validators
            .Select(v => v.Validate(request))
            .SelectMany(result => result.Errors)
            .Where(error => error != null)
            .ToList();

        if (failures.Any())
        {
            throw new OrderingDomainException(
                $"Command Validation Errors for type {typeof(TRequest).Name}",
                        new ValidationException("Validation exception", failures));
        }

        var response = await next();
        return response;
    }
}
```

<span data-ttu-id="701ff-355">Ce comportement déclenche ici une exception si la validation échoue, mais vous pouvez aussi retourner un objet résultant, qui contient le résultat de la commande si elle a réussi, ou les messages de validation si elle a échoué.</span><span class="sxs-lookup"><span data-stu-id="701ff-355">The behavior here is raising an exception if validation fails, but you could also return a result object, containing the command result if it succeeded or the validation messages in case it didn’t.</span></span> <span data-ttu-id="701ff-356">Ceci faciliterait probablement l’affichage des résultats de la validation à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="701ff-356">This would probably make it easier to display validation results to the user.</span></span>

<span data-ttu-id="701ff-357">Ensuite, en fonction de la bibliothèque [FluentValidation](https://github.com/JeremySkinner/FluentValidation), nous avons créé une validation pour les données transférées avec CreateOrderCommand, comme dans le code suivant :</span><span class="sxs-lookup"><span data-stu-id="701ff-357">Then, based on the [FluentValidation](https://github.com/JeremySkinner/FluentValidation) library, we created validation for the data passed with CreateOrderCommand, as in the following code:</span></span>

```csharp
public class CreateOrderCommandValidator : AbstractValidator<CreateOrderCommand>
{
    public CreateOrderCommandValidator()
    {
        RuleFor(command => command.City).NotEmpty();
        RuleFor(command => command.Street).NotEmpty();
        RuleFor(command => command.State).NotEmpty();
        RuleFor(command => command.Country).NotEmpty();
        RuleFor(command => command.ZipCode).NotEmpty();
        RuleFor(command => command.CardNumber).NotEmpty().Length(12, 19);
        RuleFor(command => command.CardHolderName).NotEmpty();
        RuleFor(command => command.CardExpiration).NotEmpty().Must(BeValidExpirationDate).WithMessage("Please specify a valid card expiration date");
        RuleFor(command => command.CardSecurityNumber).NotEmpty().Length(3);
        RuleFor(command => command.CardTypeId).NotEmpty();
        RuleFor(command => command.OrderItems).Must(ContainOrderItems).WithMessage("No order items found");
    }

    private bool BeValidExpirationDate(DateTime dateTime)
    {
        return dateTime >= DateTime.UtcNow;
    }

    private bool ContainOrderItems(IEnumerable<OrderItemDTO> orderItems)
    {
        return orderItems.Any();
    }
}

```

<span data-ttu-id="701ff-358">Vous pouvez créer des validations supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="701ff-358">You could create additional validations.</span></span> <span data-ttu-id="701ff-359">Il s’agit d’un moyen très propre et élégant d’implémenter vos validations de commande.</span><span class="sxs-lookup"><span data-stu-id="701ff-359">This is a very clean and elegant way to implement your command validations.</span></span>

<span data-ttu-id="701ff-360">De la même façon, vous pouvez implémenter d’autres comportements pour d’autres aspects ou problèmes transversaux que vous voulez appliquer aux commandes lorsque vous les gérez.</span><span class="sxs-lookup"><span data-stu-id="701ff-360">In a similar way, you could implement other behaviors for additional aspects or cross-cutting concerns that you want to apply to commands when handling them.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="701ff-361">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="701ff-361">Additional resources</span></span>

##### <a name="the-mediator-pattern"></a><span data-ttu-id="701ff-362">Le modèle Médiateur</span><span class="sxs-lookup"><span data-stu-id="701ff-362">The mediator pattern</span></span>

- <span data-ttu-id="701ff-363">**Mediator pattern** </span><span class="sxs-lookup"><span data-stu-id="701ff-363">**Mediator pattern** </span></span>\
  [https://en.wikipedia.org/wiki/Mediator\_pattern](https://en.wikipedia.org/wiki/Mediator_pattern)

##### <a name="the-decorator-pattern"></a><span data-ttu-id="701ff-364">Le modèle Élément décoratif</span><span class="sxs-lookup"><span data-stu-id="701ff-364">The decorator pattern</span></span>

- <span data-ttu-id="701ff-365">**Decorator pattern** </span><span class="sxs-lookup"><span data-stu-id="701ff-365">**Decorator pattern** </span></span>\
  [https://en.wikipedia.org/wiki/Decorator\_pattern](https://en.wikipedia.org/wiki/Decorator_pattern)

##### <a name="mediatr-jimmy-bogard"></a><span data-ttu-id="701ff-366">MediatR (Jimmy Bogard)</span><span class="sxs-lookup"><span data-stu-id="701ff-366">MediatR (Jimmy Bogard)</span></span>

- <span data-ttu-id="701ff-367">**MediatR.**</span><span class="sxs-lookup"><span data-stu-id="701ff-367">**MediatR.**</span></span> <span data-ttu-id="701ff-368">Dépôt GitHub.</span><span class="sxs-lookup"><span data-stu-id="701ff-368">GitHub repo.</span></span> \
  <https://github.com/jbogard/MediatR>

- <span data-ttu-id="701ff-369">**CQRS with MediatR and AutoMapper** </span><span class="sxs-lookup"><span data-stu-id="701ff-369">**CQRS with MediatR and AutoMapper** </span></span>\
  <https://lostechies.com/jimmybogard/2015/05/05/cqrs-with-mediatr-and-automapper/>

- <span data-ttu-id="701ff-370">**Put your controllers on a diet: POSTs and commands.**</span><span class="sxs-lookup"><span data-stu-id="701ff-370">**Put your controllers on a diet: POSTs and commands.**</span></span> \
  <https://lostechies.com/jimmybogard/2013/12/19/put-your-controllers-on-a-diet-posts-and-commands/>

- <span data-ttu-id="701ff-371">**Tackling cross-cutting concerns with a mediator pipeline** </span><span class="sxs-lookup"><span data-stu-id="701ff-371">**Tackling cross-cutting concerns with a mediator pipeline** </span></span>\
  <https://lostechies.com/jimmybogard/2014/09/09/tackling-cross-cutting-concerns-with-a-mediator-pipeline/>

- <span data-ttu-id="701ff-372">**CQRS and REST: the perfect match** </span><span class="sxs-lookup"><span data-stu-id="701ff-372">**CQRS and REST: the perfect match** </span></span>\
  <https://lostechies.com/jimmybogard/2016/06/01/cqrs-and-rest-the-perfect-match/>

- <span data-ttu-id="701ff-373">**MediatR Pipeline Examples** </span><span class="sxs-lookup"><span data-stu-id="701ff-373">**MediatR Pipeline Examples** </span></span>\
  <https://lostechies.com/jimmybogard/2016/10/13/mediatr-pipeline-examples/>

- <span data-ttu-id="701ff-374">**Vertical Slice Test Fixtures for MediatR and ASP.NET Core** </span><span class="sxs-lookup"><span data-stu-id="701ff-374">**Vertical Slice Test Fixtures for MediatR and ASP.NET Core** </span></span>\
  <https://lostechies.com/jimmybogard/2016/10/24/vertical-slice-test-fixtures-for-mediatr-and-asp-net-core/>

- <span data-ttu-id="701ff-375">**MediatR Extensions for Microsoft Dependency Injection Released** </span><span class="sxs-lookup"><span data-stu-id="701ff-375">**MediatR Extensions for Microsoft Dependency Injection Released** </span></span>\
  <https://lostechies.com/jimmybogard/2016/07/19/mediatr-extensions-for-microsoft-dependency-injection-released/>

##### <a name="fluent-validation"></a><span data-ttu-id="701ff-376">Validation fluide</span><span class="sxs-lookup"><span data-stu-id="701ff-376">Fluent validation</span></span>

- <span data-ttu-id="701ff-377">**Jeremy Skinner. FluentValidation.**</span><span class="sxs-lookup"><span data-stu-id="701ff-377">**Jeremy Skinner. FluentValidation.**</span></span> <span data-ttu-id="701ff-378">Dépôt GitHub.</span><span class="sxs-lookup"><span data-stu-id="701ff-378">GitHub repo.</span></span> \
  <https://github.com/JeremySkinner/FluentValidation>

> [!div class="step-by-step"]
> <span data-ttu-id="701ff-379">[Précédent](microservice-application-layer-web-api-design.md)
> [Suivant](../implement-resilient-applications/index.md)</span><span class="sxs-lookup"><span data-stu-id="701ff-379">[Previous](microservice-application-layer-web-api-design.md)
[Next](../implement-resilient-applications/index.md)</span></span>
