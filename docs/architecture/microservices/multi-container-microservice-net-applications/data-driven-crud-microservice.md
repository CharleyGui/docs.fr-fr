---
title: Création d’un microservice CRUD simple piloté par les données
description: Architecture des microservices .NET pour les applications .NET en conteneur | Comprendre la création d’un microservice CRUD simple (piloté par les données) dans le contexte d’une application de microservices.
ms.date: 08/14/2020
ms.openlocfilehash: 056ba37965cf831e0fb176eb585042c440530c6b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91172363"
---
# <a name="creating-a-simple-data-driven-crud-microservice"></a><span data-ttu-id="b08ef-103">Création d’un microservice CRUD simple piloté par les données</span><span class="sxs-lookup"><span data-stu-id="b08ef-103">Creating a simple data-driven CRUD microservice</span></span>

<span data-ttu-id="b08ef-104">Cette section explique comment créer un microservice simple devant effectuer des opérations de création, de lecture, de mise à jour et de suppression (CRUD) dans une source de données.</span><span class="sxs-lookup"><span data-stu-id="b08ef-104">This section outlines how to create a simple microservice that performs create, read, update, and delete (CRUD) operations on a data source.</span></span>

## <a name="designing-a-simple-crud-microservice"></a><span data-ttu-id="b08ef-105">Conception d’un microservice CRUD simple</span><span class="sxs-lookup"><span data-stu-id="b08ef-105">Designing a simple CRUD microservice</span></span>

<span data-ttu-id="b08ef-106">La conception de ce type de microservice en conteneur est très simple.</span><span class="sxs-lookup"><span data-stu-id="b08ef-106">From a design point of view, this type of containerized microservice is very simple.</span></span> <span data-ttu-id="b08ef-107">Le problème est peut-être simple à résoudre, ou l’implémentation n’est peut-être qu’une preuve de concept.</span><span class="sxs-lookup"><span data-stu-id="b08ef-107">Perhaps the problem to solve is simple, or perhaps the implementation is only a proof of concept.</span></span>

![Diagramme montrant un modèle de conception interne de microservice CRUD simple.](./media/data-driven-crud-microservice/internal-design-simple-crud-microservices.png)

<span data-ttu-id="b08ef-109">**Figure 6-4**.</span><span class="sxs-lookup"><span data-stu-id="b08ef-109">**Figure 6-4**.</span></span> <span data-ttu-id="b08ef-110">Conception interne de microservices CRUD simples</span><span class="sxs-lookup"><span data-stu-id="b08ef-110">Internal design for simple CRUD microservices</span></span>

<span data-ttu-id="b08ef-111">Il peut s’agir, par exemple, du microservice de catalogue de l’exemple d’application eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="b08ef-111">An example of this kind of simple data-drive service is the catalog microservice from the eShopOnContainers sample application.</span></span> <span data-ttu-id="b08ef-112">Ce type de service implémente toutes ses fonctionnalités dans un même projet d’API web ASP.NET Core, qui comprend des classes pour son modèle de données, sa logique métier et son code d’accès aux données.</span><span class="sxs-lookup"><span data-stu-id="b08ef-112">This type of service implements all its functionality in a single ASP.NET Core Web API project that includes classes for its data model, its business logic, and its data access code.</span></span> <span data-ttu-id="b08ef-113">Il stocke également ses données associées dans une base de données qui exécute SQL Server (comme autre conteneur à des fins de développement ou de test). Toutefois, il peut aussi s’agir d’un hôte SQL Server normal, comme illustré dans la figure 6-5.</span><span class="sxs-lookup"><span data-stu-id="b08ef-113">It also stores its related data in a database running in SQL Server (as another container for dev/test purposes), but could also be any regular SQL Server host, as shown in Figure 6-5.</span></span>

![Diagramme montrant un conteneur de microservice CRUD piloté par les données.](./media/data-driven-crud-microservice/simple-data-driven-crud-microservice.png)

<span data-ttu-id="b08ef-115">**Figure 6-5.**</span><span class="sxs-lookup"><span data-stu-id="b08ef-115">**Figure 6-5**.</span></span> <span data-ttu-id="b08ef-116">Conception d’un microservice CRUD simple piloté par les données</span><span class="sxs-lookup"><span data-stu-id="b08ef-116">Simple data-driven/CRUD microservice design</span></span>

<span data-ttu-id="b08ef-117">Le diagramme précédent montre le microservice de catalogue logique, qui comprend sa base de données de catalogue, qui peut être ou non dans le même hôte de station d’accueil.</span><span class="sxs-lookup"><span data-stu-id="b08ef-117">The previous diagram shows the logical Catalog microservice, that includes its Catalog database, which can be or not in the same Docker host.</span></span> <span data-ttu-id="b08ef-118">Le fait de disposer de la base de données dans le même hôte de station d’accueil peut être idéal pour le développement, mais pas pour la production.</span><span class="sxs-lookup"><span data-stu-id="b08ef-118">Having the database in the same Docker host might be good for development, but not for production.</span></span> <span data-ttu-id="b08ef-119">Lorsque vous développez ce type de service, vous avez seulement besoin [d’ASP.NET Core](/aspnet/core/) et d’une API ou d’un outil ORM d’accès aux données, comme, par exemple, [Entity Framework Core](/ef/core/index).</span><span class="sxs-lookup"><span data-stu-id="b08ef-119">When you are developing this kind of service, you only need [ASP.NET Core](/aspnet/core/) and a data-access API or ORM like [Entity Framework Core](/ef/core/index).</span></span> <span data-ttu-id="b08ef-120">Vous pouvez également générer automatiquement des métadonnées [Swagger](https://swagger.io/) par le biais de [Swashbuckle](https://github.com/domaindrivendev/Swashbuckle.AspNetCore), afin de fournir une description de votre service, comme l’explique la section suivante.</span><span class="sxs-lookup"><span data-stu-id="b08ef-120">You could also generate [Swagger](https://swagger.io/) metadata automatically through [Swashbuckle](https://github.com/domaindrivendev/Swashbuckle.AspNetCore) to provide a description of what your service offers, as explained in the next section.</span></span>

<span data-ttu-id="b08ef-121">Notez que les serveurs de base de données, tels que SQL Server, qui sont situés dans un conteneur Docker constituent la solution idéale pour les environnements de développement. En effet, vous pouvez utiliser directement toutes vos dépendances, sans avoir à provisionner une base de données locale ou cloud.</span><span class="sxs-lookup"><span data-stu-id="b08ef-121">Note that running a database server like SQL Server within a Docker container is great for development environments, because you can have all your dependencies up and running without needing to provision a database in the cloud or on-premises.</span></span> <span data-ttu-id="b08ef-122">Ceci est très utile lorsque vous effectuez des tests d’intégration.</span><span class="sxs-lookup"><span data-stu-id="b08ef-122">This is very convenient when running integration tests.</span></span> <span data-ttu-id="b08ef-123">Toutefois, pour les environnements de production, l’exécution d’un serveur de base de données dans un conteneur est déconseillée, car elle ne permet pas d’obtenir une haute disponibilité.</span><span class="sxs-lookup"><span data-stu-id="b08ef-123">However, for production environments, running a database server in a container is not recommended, because you usually do not get high availability with that approach.</span></span> <span data-ttu-id="b08ef-124">Pour un environnement de production Azure, il est recommandé d’utiliser Azure SQL DB ou une autre technologie de base de données capable de fournir une haute disponibilité et une scalabilité importante.</span><span class="sxs-lookup"><span data-stu-id="b08ef-124">For a production environment in Azure, it is recommended that you use Azure SQL DB or any other database technology that can provide high availability and high scalability.</span></span> <span data-ttu-id="b08ef-125">Par exemple, pour une approche NoSQL, vous pouvez utiliser CosmosDB.</span><span class="sxs-lookup"><span data-stu-id="b08ef-125">For example, for a NoSQL approach, you might choose CosmosDB.</span></span>

<span data-ttu-id="b08ef-126">Enfin, en modifiant les fichiers de métadonnées Dockerfile et docker-compose.yml, vous pouvez configurer la création de l’image de ce conteneur, c’est-à-dire, quelle image de base elle va utiliser, ainsi que les paramètres de conception, tels que le nom interne et externe, et les ports TCP.</span><span class="sxs-lookup"><span data-stu-id="b08ef-126">Finally, by editing the Dockerfile and docker-compose.yml metadata files, you can configure how the image of this container will be created—what base image it will use, plus design settings such as internal and external names and TCP ports.</span></span>

## <a name="implementing-a-simple-crud-microservice-with-aspnet-core"></a><span data-ttu-id="b08ef-127">Implémentation d’un microservice CRUD simple avec ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="b08ef-127">Implementing a simple CRUD microservice with ASP.NET Core</span></span>

<span data-ttu-id="b08ef-128">Pour implémenter un microservice CRUD simple à l’aide de .NET Core et de Visual Studio, commencez par créer un projet d’API web ASP.NET Core simple (et s’exécutant sur .NET Core pour qu’il puisse s’exécuter sur un hôte Docker Linux), comme indiqué dans la figure 6-6.</span><span class="sxs-lookup"><span data-stu-id="b08ef-128">To implement a simple CRUD microservice using .NET Core and Visual Studio, you start by creating a simple ASP.NET Core Web API project (running on .NET Core so it can run on a Linux Docker host), as shown in Figure 6-6.</span></span>

![Capture d’écran de Visual Studio montrant la configuration du projet.](./media/data-driven-crud-microservice/create-asp-net-core-web-api-project.png)

<span data-ttu-id="b08ef-130">**Figure 6-6.**</span><span class="sxs-lookup"><span data-stu-id="b08ef-130">**Figure 6-6**.</span></span> <span data-ttu-id="b08ef-131">Création d’un projet d’API Web ASP.NET Core dans Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="b08ef-131">Creating an ASP.NET Core Web API project in Visual Studio 2019</span></span>

<span data-ttu-id="b08ef-132">Pour créer un projet d’API web ASP.NET Core, commencez par sélectionner une application web ASP.NET Core, puis sélectionnez le type d’API.</span><span class="sxs-lookup"><span data-stu-id="b08ef-132">To create an ASP.NET Core Web API Project, first select an ASP.NET Core Web Application and then select the API type.</span></span> <span data-ttu-id="b08ef-133">Après avoir créé le projet, vous pouvez implémenter vos contrôleurs MVC comme vous le feriez dans n’importe quel autre projet d’API web, à l’aide de l’API Entity Framework ou d’une autre API.</span><span class="sxs-lookup"><span data-stu-id="b08ef-133">After creating the project, you can implement your MVC controllers as you would in any other Web API project, using the Entity Framework API or other API.</span></span> <span data-ttu-id="b08ef-134">Dans un nouveau projet d’API web, vous pouvez voir que la seule dépendance de ce microservice se trouve au niveau d’ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="b08ef-134">In a new Web API project, you can see that the only dependency you have in that microservice is on ASP.NET Core itself.</span></span> <span data-ttu-id="b08ef-135">En interne, au sein de la dépendance *Microsoft. AspNetCore. All* , elle référence Entity Framework et de nombreux autres packages NuGet .net Core, comme illustré dans la figure 6-7.</span><span class="sxs-lookup"><span data-stu-id="b08ef-135">Internally, within the *Microsoft.AspNetCore.All* dependency, it is referencing Entity Framework and many other .NET Core NuGet packages, as shown in Figure 6-7.</span></span>

![Capture d’écran de VS montrant les dépendances NuGet de Catalog. API.](./media/data-driven-crud-microservice/simple-crud-web-api-microservice-dependencies.png)

<span data-ttu-id="b08ef-137">**Figure 6-7.**</span><span class="sxs-lookup"><span data-stu-id="b08ef-137">**Figure 6-7**.</span></span> <span data-ttu-id="b08ef-138">Dépendances d’un microservice d’API web CRUD simple</span><span class="sxs-lookup"><span data-stu-id="b08ef-138">Dependencies in a simple CRUD Web API microservice</span></span>

<span data-ttu-id="b08ef-139">Le projet d’API comprend des références au package NuGet Microsoft. AspNetCore. app, qui comprend des références à tous les packages essentiels.</span><span class="sxs-lookup"><span data-stu-id="b08ef-139">The API project includes references to Microsoft.AspNetCore.App NuGet package, that includes references to all essential packages.</span></span> <span data-ttu-id="b08ef-140">Il peut également contenir d’autres packages.</span><span class="sxs-lookup"><span data-stu-id="b08ef-140">It could include some other packages as well.</span></span>

### <a name="implementing-crud-web-api-services-with-entity-framework-core"></a><span data-ttu-id="b08ef-141">Implémentation de services d’API web CRUD avec Entity Framework Core</span><span class="sxs-lookup"><span data-stu-id="b08ef-141">Implementing CRUD Web API services with Entity Framework Core</span></span>

<span data-ttu-id="b08ef-142">Entity Framework (EF) Core est une version légère, extensible et multiplateforme de la technologie d’accès aux données Entity Framework populaire.</span><span class="sxs-lookup"><span data-stu-id="b08ef-142">Entity Framework (EF) Core is a lightweight, extensible, and cross-platform version of the popular Entity Framework data access technology.</span></span> <span data-ttu-id="b08ef-143">Entity Framework Core est un outil de mappage objet-relationnel (ORM) qui permet aux développeurs .NET d’utiliser une base de données avec des objets .NET.</span><span class="sxs-lookup"><span data-stu-id="b08ef-143">EF Core is an object-relational mapper (ORM) that enables .NET developers to work with a database using .NET objects.</span></span>

<span data-ttu-id="b08ef-144">Le microservice de catalogue utilise Entity Framework et le fournisseur SQL Server, car sa base de données est exécutée dans un conteneur avec l’image SQL Server pour Linux Docker.</span><span class="sxs-lookup"><span data-stu-id="b08ef-144">The catalog microservice uses EF and the SQL Server provider because its database is running in a container with the SQL Server for Linux Docker image.</span></span> <span data-ttu-id="b08ef-145">Toutefois, la base de données peut être déployée sur n’importe quel serveur SQL Server (instance locale Windows ou Azure SQL DB).</span><span class="sxs-lookup"><span data-stu-id="b08ef-145">However, the database could be deployed into any SQL Server, such as Windows on-premises or Azure SQL DB.</span></span> <span data-ttu-id="b08ef-146">La seule chose que vous devez modifier est la chaîne de connexion située dans le microservice de l’API web ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="b08ef-146">The only thing you would need to change is the connection string in the ASP.NET Web API microservice.</span></span>

#### <a name="the-data-model"></a><span data-ttu-id="b08ef-147">Modèle de données</span><span class="sxs-lookup"><span data-stu-id="b08ef-147">The data model</span></span>

<span data-ttu-id="b08ef-148">Avec Entity Framework Core, l’accès aux données est effectué à l’aide d’un modèle.</span><span class="sxs-lookup"><span data-stu-id="b08ef-148">With EF Core, data access is performed by using a model.</span></span> <span data-ttu-id="b08ef-149">Un modèle est composé de classes d’entité (modèle de domaine) et d’un contexte dérivé (DbContext) qui représente une session avec la base de données, ce qui vous permet d’interroger et d’enregistrer des données.</span><span class="sxs-lookup"><span data-stu-id="b08ef-149">A model is made up of (domain model) entity classes and a derived context (DbContext) that represents a session with the database, allowing you to query and save data.</span></span> <span data-ttu-id="b08ef-150">Vous pouvez générer un modèle à partir d’une base de données existante, coder manuellement un modèle pour qu’il corresponde à votre base de données ou utiliser la technique de migrations d’EF pour créer une base de données à partir de votre modèle, à l’aide de l’approche code First (qui facilite l’évolution de la base de données à mesure que votre modèle évolue dans le temps).</span><span class="sxs-lookup"><span data-stu-id="b08ef-150">You can generate a model from an existing database, manually code a model to match your database, or use EF migrations technique to create a database from your model, using the code-first approach (that makes it easy to evolve the database as your model changes over time).</span></span> <span data-ttu-id="b08ef-151">Pour le microservice de catalogue, la dernière approche a été utilisée.</span><span class="sxs-lookup"><span data-stu-id="b08ef-151">For the catalog microservice, the last approach has been used.</span></span> <span data-ttu-id="b08ef-152">Vous pouvez voir un exemple de la classe d’entité CatalogItem dans l’exemple de code suivant, qui est une classe d’entité [POCO](https://en.wikipedia.org/wiki/Plain_Old_CLR_Object).</span><span class="sxs-lookup"><span data-stu-id="b08ef-152">You can see an example of the CatalogItem entity class in the following code example, which is a simple Plain Old CLR Object ([POCO](https://en.wikipedia.org/wiki/Plain_Old_CLR_Object)) entity class.</span></span>

```csharp
public class CatalogItem
{
    public int Id { get; set; }
    public string Name { get; set; }
    public string Description { get; set; }
    public decimal Price { get; set; }
    public string PictureFileName { get; set; }
    public string PictureUri { get; set; }
    public int CatalogTypeId { get; set; }
    public CatalogType CatalogType { get; set; }
    public int CatalogBrandId { get; set; }
    public CatalogBrand CatalogBrand { get; set; }
    public int AvailableStock { get; set; }
    public int RestockThreshold { get; set; }
    public int MaxStockThreshold { get; set; }

    public bool OnReorder { get; set; }
    public CatalogItem() { }

    // Additional code ...
}
```

<span data-ttu-id="b08ef-153">Vous avez également besoin d’un DbContext qui représente une session pour la base de données.</span><span class="sxs-lookup"><span data-stu-id="b08ef-153">You also need a DbContext that represents a session with the database.</span></span> <span data-ttu-id="b08ef-154">Pour le microservice de catalogue, la classe CatalogContext est dérivée de la classe de base DbContext, comme le montre l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="b08ef-154">For the catalog microservice, the CatalogContext class derives from the DbContext base class, as shown in the following example:</span></span>

```csharp
public class CatalogContext : DbContext
{
    public CatalogContext(DbContextOptions<CatalogContext> options) : base(options)
    { }
    public DbSet<CatalogItem> CatalogItems { get; set; }
    public DbSet<CatalogBrand> CatalogBrands { get; set; }
    public DbSet<CatalogType> CatalogTypes { get; set; }

    // Additional code ...
}
```

<span data-ttu-id="b08ef-155">Vous pouvez avoir d’autres implémentations `DbContext`.</span><span class="sxs-lookup"><span data-stu-id="b08ef-155">You can have additional `DbContext` implementations.</span></span> <span data-ttu-id="b08ef-156">Par exemple, dans l’exemple de microservice Catalog.API, il existe un deuxième `DbContext` nommé `CatalogContextSeed` où des exemples de données sont automatiquement ajoutés lors du premier accès à la base de données.</span><span class="sxs-lookup"><span data-stu-id="b08ef-156">For example, in the sample Catalog.API microservice, there's a second `DbContext` named `CatalogContextSeed` where it automatically populates the sample data the first time it tries to access the database.</span></span> <span data-ttu-id="b08ef-157">Cette méthode est utile pour les données de démonstration et pour les scénarios de tests automatisés.</span><span class="sxs-lookup"><span data-stu-id="b08ef-157">This method is useful for demo data and for automated testing scenarios, as well.</span></span>

<span data-ttu-id="b08ef-158">Dans le `DbContext`, utilisez la méthode `OnModelCreating` pour personnaliser les mappages d’entités objet/base de données et d’autres [points d’extensibilité EF](https://devblogs.microsoft.com/dotnet/implementing-seeding-custom-conventions-and-interceptors-in-ef-core-1-0/).</span><span class="sxs-lookup"><span data-stu-id="b08ef-158">Within the `DbContext`, you use the `OnModelCreating` method to customize object/database entity mappings and other [EF extensibility points](https://devblogs.microsoft.com/dotnet/implementing-seeding-custom-conventions-and-interceptors-in-ef-core-1-0/).</span></span>

##### <a name="querying-data-from-web-api-controllers"></a><span data-ttu-id="b08ef-159">Interrogation des données à partir de contrôleurs d’API web</span><span class="sxs-lookup"><span data-stu-id="b08ef-159">Querying data from Web API controllers</span></span>

<span data-ttu-id="b08ef-160">Les instances des classes d’entité sont généralement récupérées dans la base de données à l’aide de LINQ, comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="b08ef-160">Instances of your entity classes are typically retrieved from the database using Language Integrated Query (LINQ), as shown in the following example:</span></span>

```csharp
[Route("api/v1/[controller]")]
public class CatalogController : ControllerBase
{
    private readonly CatalogContext _catalogContext;
    private readonly CatalogSettings _settings;
    private readonly ICatalogIntegrationEventService _catalogIntegrationEventService;

    public CatalogController(
        CatalogContext context,
        IOptionsSnapshot<CatalogSettings> settings,
        ICatalogIntegrationEventService catalogIntegrationEventService)
    {
        _catalogContext = context ?? throw new ArgumentNullException(nameof(context));
        _catalogIntegrationEventService = catalogIntegrationEventService
            ?? throw new ArgumentNullException(nameof(catalogIntegrationEventService));

        _settings = settings.Value;
        context.ChangeTracker.QueryTrackingBehavior = QueryTrackingBehavior.NoTracking;
    }

    // GET api/v1/[controller]/items[?pageSize=3&pageIndex=10]
    [HttpGet]
    [Route("items")]
    [ProducesResponseType(typeof(PaginatedItemsViewModel<CatalogItem>), (int)HttpStatusCode.OK)]
    [ProducesResponseType(typeof(IEnumerable<CatalogItem>), (int)HttpStatusCode.OK)]
    [ProducesResponseType((int)HttpStatusCode.BadRequest)]
    public async Task<IActionResult> ItemsAsync(
        [FromQuery]int pageSize = 10,
        [FromQuery]int pageIndex = 0,
        string ids = null)
    {
        if (!string.IsNullOrEmpty(ids))
        {
            var items = await GetItemsByIdsAsync(ids);

            if (!items.Any())
            {
                return BadRequest("ids value invalid. Must be comma-separated list of numbers");
            }

            return Ok(items);
        }

        var totalItems = await _catalogContext.CatalogItems
            .LongCountAsync();

        var itemsOnPage = await _catalogContext.CatalogItems
            .OrderBy(c => c.Name)
            .Skip(pageSize * pageIndex)
            .Take(pageSize)
            .ToListAsync();

        itemsOnPage = ChangeUriPlaceholder(itemsOnPage);

        var model = new PaginatedItemsViewModel<CatalogItem>(
            pageIndex, pageSize, totalItems, itemsOnPage);

        return Ok(model);
    }
    //...
}
```

##### <a name="saving-data"></a><span data-ttu-id="b08ef-161">Enregistrement des données</span><span class="sxs-lookup"><span data-stu-id="b08ef-161">Saving data</span></span>

<span data-ttu-id="b08ef-162">Les données sont créées, supprimées et modifiées dans la base de données à l’aide d’instances de vos classes d’entité.</span><span class="sxs-lookup"><span data-stu-id="b08ef-162">Data is created, deleted, and modified in the database using instances of your entity classes.</span></span> <span data-ttu-id="b08ef-163">Vous pouvez ajouter du code similaire à celui de l’exemple codé en dur suivant (il s’agit ici de données fictives) dans vos contrôleurs d’API web.</span><span class="sxs-lookup"><span data-stu-id="b08ef-163">You could add code like the following hard-coded example (mock data, in this case) to your Web API controllers.</span></span>

```csharp
var catalogItem = new CatalogItem() {CatalogTypeId=2, CatalogBrandId=2,
                                     Name="Roslyn T-Shirt", Price = 12};
_context.Catalog.Add(catalogItem);
_context.SaveChanges();
```

##### <a name="dependency-injection-in-aspnet-core-and-web-api-controllers"></a><span data-ttu-id="b08ef-164">Injection de dépendances dans ASP.NET Core et dans les contrôleurs d’API web</span><span class="sxs-lookup"><span data-stu-id="b08ef-164">Dependency Injection in ASP.NET Core and Web API controllers</span></span>

<span data-ttu-id="b08ef-165">Dans ASP.NET Core, vous pouvez utiliser une injection de dépendances prête à l’emploi.</span><span class="sxs-lookup"><span data-stu-id="b08ef-165">In ASP.NET Core you can use Dependency Injection (DI) out of the box.</span></span> <span data-ttu-id="b08ef-166">Il n’est pas nécessaire de configurer un conteneur IoC tiers. Toutefois, si vous le souhaitez, vous pouvez connecter votre conteneur IoC par défaut à l’infrastructure ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="b08ef-166">You do not need to set up a third-party Inversion of Control (IoC) container, although you can plug your preferred IoC container into the ASP.NET Core infrastructure if you want.</span></span> <span data-ttu-id="b08ef-167">Dans ce cas, vous pouvez injecter directement le DBContext Entity Framework (et autres dépôts) via le constructeur de contrôleur.</span><span class="sxs-lookup"><span data-stu-id="b08ef-167">In this case, it means that you can directly inject the required EF DBContext or additional repositories through the controller constructor.</span></span>

<span data-ttu-id="b08ef-168">Dans la `CatalogController` classe mentionnée précédemment, `CatalogContext` (qui hérite de `DbContext` ) le type est injecté avec les autres objets requis dans le `CatalogController()` constructeur.</span><span class="sxs-lookup"><span data-stu-id="b08ef-168">In the `CatalogController` class mentioned earlier, `CatalogContext` (which inherits from `DbContext`) type is injected along with the other required objects in the `CatalogController()` constructor.</span></span>

<span data-ttu-id="b08ef-169">L’un des éléments importants à configurer pour le projet d’API web est l’inscription de la classe DbContext auprès du conteneur IoC du service.</span><span class="sxs-lookup"><span data-stu-id="b08ef-169">An important configuration to set up in the Web API project is the DbContext class registration into the service's IoC container.</span></span> <span data-ttu-id="b08ef-170">En général, vous le faites dans la `Startup` classe en appelant la `services.AddDbContext<CatalogContext>()` méthode à l’intérieur de la `ConfigureServices()` méthode, comme illustré dans l’exemple **simplifié** suivant :</span><span class="sxs-lookup"><span data-stu-id="b08ef-170">You typically do so in the `Startup` class by calling the `services.AddDbContext<CatalogContext>()` method inside the `ConfigureServices()` method, as shown in the following **simplified** example:</span></span>

```csharp
public void ConfigureServices(IServiceCollection services)
{
    // Additional code...
    services.AddDbContext<CatalogContext>(options =>
    {
        options.UseSqlServer(Configuration["ConnectionString"],
        sqlServerOptionsAction: sqlOptions =>
        {
            sqlOptions.MigrationsAssembly(
                typeof(Startup).GetTypeInfo().Assembly.GetName().Name);

           //Configuring Connection Resiliency:
           sqlOptions.
               EnableRetryOnFailure(maxRetryCount: 5,
               maxRetryDelay: TimeSpan.FromSeconds(30),
               errorNumbersToAdd: null);

       });

       // Changing default behavior when client evaluation occurs to throw.
       // Default in EFCore would be to log warning when client evaluation is done.
       options.ConfigureWarnings(warnings => warnings.Throw(
           RelationalEventId.QueryClientEvaluationWarning));
   });

  //...
}
```

### <a name="additional-resources"></a><span data-ttu-id="b08ef-171">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="b08ef-171">Additional resources</span></span>

- <span data-ttu-id="b08ef-172">**Interrogation des données** </span><span class="sxs-lookup"><span data-stu-id="b08ef-172">**Querying Data** </span></span>\
  [https://docs.microsoft.com/ef/core/querying/index](/ef/core/querying/index)

- <span data-ttu-id="b08ef-173">**Enregistrement des données** </span><span class="sxs-lookup"><span data-stu-id="b08ef-173">**Saving Data** </span></span>\
  [https://docs.microsoft.com/ef/core/saving/index](/ef/core/saving/index)

## <a name="the-db-connection-string-and-environment-variables-used-by-docker-containers"></a><span data-ttu-id="b08ef-174">Chaîne de connexion de la base de données et variables d’environnement utilisées par les conteneurs Docker</span><span class="sxs-lookup"><span data-stu-id="b08ef-174">The DB connection string and environment variables used by Docker containers</span></span>

<span data-ttu-id="b08ef-175">Vous pouvez utiliser les paramètres ASP.NET Core et ajouter une propriété ConnectionString à votre fichier settings.json, comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="b08ef-175">You can use the ASP.NET Core settings and add a ConnectionString property to your settings.json file as shown in the following example:</span></span>

```json
{
    "ConnectionString": "Server=tcp:127.0.0.1,5433;Initial Catalog=Microsoft.eShopOnContainers.Services.CatalogDb;User Id=sa;Password=Pass@word",
    "ExternalCatalogBaseUrl": "http://localhost:5101",
    "Logging": {
        "IncludeScopes": false,
        "LogLevel": {
            "Default": "Debug",
            "System": "Information",
            "Microsoft": "Information"
        }
    }
}
```

<span data-ttu-id="b08ef-176">Le fichier settings.json peut avoir des valeurs par défaut pour la propriété ConnectionString ou pour toute autre propriété.</span><span class="sxs-lookup"><span data-stu-id="b08ef-176">The settings.json file can have default values for the ConnectionString property or for any other property.</span></span> <span data-ttu-id="b08ef-177">Toutefois, ces propriétés seront remplacées par les valeurs des variables d’environnement que vous spécifiez dans le fichier docker-compose.override.yml lors de l’utilisation de Docker.</span><span class="sxs-lookup"><span data-stu-id="b08ef-177">However, those properties will be overridden by the values of environment variables that you specify in the docker-compose.override.yml file, when using Docker.</span></span>

<span data-ttu-id="b08ef-178">Dans les fichiers docker-compose.yml ou docker-compose.override.yml, vous pouvez initialiser les variables d’environnement pour que Docker les configure comme des variables d’environnement du système d’exploitation, comme indiqué dans le fichier docker-compose.override.yml suivant (dans cet exemple, un retour automatique à la ligne est effectué pour la chaîne de connexion et les autres lignes, mais ce ne sera pas le cas dans votre propre fichier).</span><span class="sxs-lookup"><span data-stu-id="b08ef-178">From your docker-compose.yml or docker-compose.override.yml files, you can initialize those environment variables so that Docker will set them up as OS environment variables for you, as shown in the following docker-compose.override.yml file (the connection string and other lines wrap in this example, but it would not wrap in your own file).</span></span>

```yml
# docker-compose.override.yml

#
catalog-api:
  environment:
    - ConnectionString=Server=sqldata;Database=Microsoft.eShopOnContainers.Services.CatalogDb;User Id=sa;Password=Pass@word
    # Additional environment variables for this service
  ports:
    - "5101:80"
```

<span data-ttu-id="b08ef-179">Les fichiers docker-compose.yml situés au niveau de la solution non seulement sont plus flexibles que les fichiers de configuration situés au niveau du projet ou microservice, mais ils sont aussi plus sécurisés si vous remplacez les variables d’environnement déclarées dans les fichiers docker-compose par des valeurs définies dans vos outils de déploiement (par exemple, dans les tâches de déploiement Azure DevOps Services Docker).</span><span class="sxs-lookup"><span data-stu-id="b08ef-179">The docker-compose.yml files at the solution level are not only more flexible than configuration files at the project or microservice level, but also more secure if you override the environment variables declared at the docker-compose files with values set from your deployment tools, like from Azure DevOps Services Docker deployment tasks.</span></span>

<span data-ttu-id="b08ef-180">Enfin, vous pouvez obtenir cette valeur à partir de votre code à l’aide de Configuration\["ConnectionString"\], comme illustré dans la méthode ConfigureServices de l’exemple de code précédent.</span><span class="sxs-lookup"><span data-stu-id="b08ef-180">Finally, you can get that value from your code by using Configuration\["ConnectionString"\], as shown in the ConfigureServices method in an earlier code example.</span></span>

<span data-ttu-id="b08ef-181">Toutefois, pour les environnements de production, vous pouvez explorer d’autres moyens de stocker des secrets, comme les chaînes de connexion.</span><span class="sxs-lookup"><span data-stu-id="b08ef-181">However, for production environments, you might want to explore additional ways on how to store secrets like the connection strings.</span></span> <span data-ttu-id="b08ef-182">Un excellent moyen de gérer les secrets d’application consiste à utiliser [Azure Key Vault](https://azure.microsoft.com/services/key-vault/).</span><span class="sxs-lookup"><span data-stu-id="b08ef-182">An excellent way to manage application secrets is using [Azure Key Vault](https://azure.microsoft.com/services/key-vault/).</span></span>

<span data-ttu-id="b08ef-183">Azure Key Vault permet de stocker et de protéger les clés de chiffrement et les secrets utilisés par vos applications et services cloud.</span><span class="sxs-lookup"><span data-stu-id="b08ef-183">Azure Key Vault helps to store and safeguard cryptographic keys and secrets used by your cloud applications and services.</span></span> <span data-ttu-id="b08ef-184">Une clé secrète est tout ce sur quoi vous voulez exercer un contrôle strict, comme des clés API, des chaînes de connexion, des mots de passe, etc. Un contrôle strict inclut l’utilisation de la journalisation, la définition d’une expiration, la gestion de l’accès, *entre autres*.</span><span class="sxs-lookup"><span data-stu-id="b08ef-184">A secret is anything you want to keep strict control of, like API keys, connection strings, passwords, etc. and strict control includes usage logging, setting expiration, managing access, *among others*.</span></span>

<span data-ttu-id="b08ef-185">Azure Key Vault permet un niveau de contrôle très détaillé de l’utilisation des secrets d’application sans qu’il soit nécessaire d’en informer qui que ce soit.</span><span class="sxs-lookup"><span data-stu-id="b08ef-185">Azure Key Vault allows a very detailed control level of the application secrets usage without the need to let anyone know them.</span></span> <span data-ttu-id="b08ef-186">Les secrets peuvent même être utilisés en alternance pour renforcer la sécurité sans perturber le développement ou le fonctionnement.</span><span class="sxs-lookup"><span data-stu-id="b08ef-186">The secrets can even be rotated for enhanced security without disrupting development or operations.</span></span>

<span data-ttu-id="b08ef-187">Les applications doivent être inscrites dans le service Active Directory de l’organisation, afin d’elles puissent utiliser le coffre de clés.</span><span class="sxs-lookup"><span data-stu-id="b08ef-187">Applications have to be registered in the organization's Active Directory, so they can use the Key Vault.</span></span>

<span data-ttu-id="b08ef-188">Pour plus d’informations, consultez la *documentation relative aux concepts des coffres de clés*.</span><span class="sxs-lookup"><span data-stu-id="b08ef-188">You can check the *Key Vault Concepts documentation* for more details.</span></span>

### <a name="implementing-versioning-in-aspnet-web-apis"></a><span data-ttu-id="b08ef-189">Implémentation de la gestion de version dans les API web ASP.NET</span><span class="sxs-lookup"><span data-stu-id="b08ef-189">Implementing versioning in ASP.NET Web APIs</span></span>

<span data-ttu-id="b08ef-190">L’évolution des exigences métier peut entraîner l’ajout de collections de ressources, le changement des relations entre les ressources et la modification de la structure des données contenues dans ces ressources.</span><span class="sxs-lookup"><span data-stu-id="b08ef-190">As business requirements change, new collections of resources may be added, the relationships between resources might change, and the structure of the data in resources might be amended.</span></span> <span data-ttu-id="b08ef-191">La modification d’une API web pour s’adapter aux nouvelles exigences est un processus relativement simple. Toutefois, vous devez prendre en compte les conséquences d’une telle modification sur l’utilisation de l’API web par les applications clientes.</span><span class="sxs-lookup"><span data-stu-id="b08ef-191">Updating a Web API to handle new requirements is a relatively straightforward process, but you must consider the effects that such changes will have on client applications consuming the Web API.</span></span> <span data-ttu-id="b08ef-192">Bien que le développeur qui conçoit et implémente une API Web ait un contrôle total sur cette API, le développeur n’a pas le même degré de contrôle sur les applications clientes qui peuvent être créées par des organisations tierces opérant à distance.</span><span class="sxs-lookup"><span data-stu-id="b08ef-192">Although the developer designing and implementing a Web API has full control over that API, the developer does not have the same degree of control over client applications that might be built by third-party organizations operating remotely.</span></span>

<span data-ttu-id="b08ef-193">La gestion de version permet à une API web d’indiquer les fonctionnalités et les ressources qu’elle expose.</span><span class="sxs-lookup"><span data-stu-id="b08ef-193">Versioning enables a Web API to indicate the features and resources that it exposes.</span></span> <span data-ttu-id="b08ef-194">Une application cliente peut ensuite envoyer des requêtes à une version précise d’une fonctionnalité ou d’une ressource.</span><span class="sxs-lookup"><span data-stu-id="b08ef-194">A client application can then submit requests to a specific version of a feature or resource.</span></span> <span data-ttu-id="b08ef-195">Il existe plusieurs méthodes pour implémenter la gestion de version :</span><span class="sxs-lookup"><span data-stu-id="b08ef-195">There are several approaches to implement versioning:</span></span>

- <span data-ttu-id="b08ef-196">Contrôle de version d’URI</span><span class="sxs-lookup"><span data-stu-id="b08ef-196">URI versioning</span></span>

- <span data-ttu-id="b08ef-197">Contrôle de version de chaîne de requête</span><span class="sxs-lookup"><span data-stu-id="b08ef-197">Query string versioning</span></span>

- <span data-ttu-id="b08ef-198">Contrôle de version d’en-tête</span><span class="sxs-lookup"><span data-stu-id="b08ef-198">Header versioning</span></span>

<span data-ttu-id="b08ef-199">La gestion des versions de chaîne de requête et d’URI sont les plus simples à implémenter.</span><span class="sxs-lookup"><span data-stu-id="b08ef-199">Query string and URI versioning are the simplest to implement.</span></span> <span data-ttu-id="b08ef-200">La gestion des versions d’en-tête est une bonne méthode.</span><span class="sxs-lookup"><span data-stu-id="b08ef-200">Header versioning is a good approach.</span></span> <span data-ttu-id="b08ef-201">Toutefois, le contrôle de version d’en-tête n’est pas aussi explicite et simple que le contrôle de version d’URI.</span><span class="sxs-lookup"><span data-stu-id="b08ef-201">However, header versioning is not as explicit and straightforward as URI versioning.</span></span> <span data-ttu-id="b08ef-202">Étant donné que la gestion des versions d’URI est la plus simple et la plus explicite, c’est elle qu’utilise l’exemple d’application eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="b08ef-202">Because URL versioning is the simplest and most explicit, the eShopOnContainers sample application uses URI versioning.</span></span>

<span data-ttu-id="b08ef-203">Avec la gestion des versions d’URI (comme dans l’exemple d’application eShopOnContainers), chaque fois que vous modifiez l’API web ou que vous modifiez le schéma des ressources, vous ajoutez un numéro de version à l’URI de chaque ressource.</span><span class="sxs-lookup"><span data-stu-id="b08ef-203">With URI versioning, as in the eShopOnContainers sample application, each time you modify the Web API or change the schema of resources, you add a version number to the URI for each resource.</span></span> <span data-ttu-id="b08ef-204">Les URI existants continuent de fonctionner comme avant, en retournant des ressources conformes au schéma de la version demandée.</span><span class="sxs-lookup"><span data-stu-id="b08ef-204">Existing URIs should continue to operate as before, returning resources that conform to the schema that matches the requested version.</span></span>

<span data-ttu-id="b08ef-205">Comme le montre l’exemple de code suivant, la version peut être définie à l’aide de l’attribut Route dans le contrôleur d’API web, ce qui rend la version explicite dans l’URI (v1, dans le cas présent).</span><span class="sxs-lookup"><span data-stu-id="b08ef-205">As shown in the following code example, the version can be set by using the Route attribute in the Web API controller, which makes the version explicit in the URI (v1 in this case).</span></span>

```csharp
[Route("api/v1/[controller]")]
public class CatalogController : ControllerBase
{
    // Implementation ...
```

<span data-ttu-id="b08ef-206">Ce mécanisme de gestion de version est simple et dépend du serveur qui achemine la demande vers le point de terminaison approprié.</span><span class="sxs-lookup"><span data-stu-id="b08ef-206">This versioning mechanism is simple and depends on the server routing the request to the appropriate endpoint.</span></span> <span data-ttu-id="b08ef-207">Toutefois, pour une gestion de version plus sophistiquée et pour une utilisation optimale avec REST, vous devez utiliser des hypermédias et implémenter [HATEOAS](/azure/architecture/best-practices/api-design#use-hateoas-to-enable-navigation-to-related-resources).</span><span class="sxs-lookup"><span data-stu-id="b08ef-207">However, for a more sophisticated versioning and the best method when using REST, you should use hypermedia and implement [HATEOAS (Hypertext as the Engine of Application State)](/azure/architecture/best-practices/api-design#use-hateoas-to-enable-navigation-to-related-resources).</span></span>

### <a name="additional-resources"></a><span data-ttu-id="b08ef-208">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="b08ef-208">Additional resources</span></span>

- <span data-ttu-id="b08ef-209">**Scott Hanselman. Le contrôle de version de l’API Web RESTful ASP.NET Core simplifié** </span><span class="sxs-lookup"><span data-stu-id="b08ef-209">**Scott Hanselman. ASP.NET Core RESTful Web API versioning made easy** </span></span>\
  <https://www.hanselman.com/blog/ASPNETCoreRESTfulWebAPIVersioningMadeEasy.aspx>

- <span data-ttu-id="b08ef-210">**Contrôle de version d’une API Web RESTful** </span><span class="sxs-lookup"><span data-stu-id="b08ef-210">**Versioning a RESTful web API** </span></span>\
  <https://docs.microsoft.com/azure/architecture/best-practices/api-design#versioning-a-restful-web-api>

- <span data-ttu-id="b08ef-211">**Champ Roy. Contrôle de version, hypermédia et REST** </span><span class="sxs-lookup"><span data-stu-id="b08ef-211">**Roy Fielding. Versioning, Hypermedia, and REST** </span></span>\
  <https://www.infoq.com/articles/roy-fielding-on-versioning>

## <a name="generating-swagger-description-metadata-from-your-aspnet-core-web-api"></a><span data-ttu-id="b08ef-212">Génération de métadonnées de description Swagger à partir de votre API web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="b08ef-212">Generating Swagger description metadata from your ASP.NET Core Web API</span></span>

<span data-ttu-id="b08ef-213">[Swagger](https://swagger.io/) est un framework open source couramment utilisé qui s’appuie sur un large écosystème d’outils permettant de concevoir, de générer, de documenter et de consommer vos API RESTful.</span><span class="sxs-lookup"><span data-stu-id="b08ef-213">[Swagger](https://swagger.io/) is a commonly used open source framework backed by a large ecosystem of tools that helps you design, build, document, and consume your RESTful APIs.</span></span> <span data-ttu-id="b08ef-214">C’est désormais une référence dans le domaine des métadonnées de description d’API.</span><span class="sxs-lookup"><span data-stu-id="b08ef-214">It is becoming the standard for the APIs description metadata domain.</span></span> <span data-ttu-id="b08ef-215">Vous devez inclure des métadonnées de description Swagger avec tout type de microservice, soit des microservices pilotés par les données, soit des microservices pilotés par domaine plus avancés (comme expliqué dans la section suivante).</span><span class="sxs-lookup"><span data-stu-id="b08ef-215">You should include Swagger description metadata with any kind of microservice, either data-driven microservices or more advanced domain-driven microservices (as explained in the following section).</span></span>

<span data-ttu-id="b08ef-216">Le principal intérêt de Swagger est la spécification Swagger, c’est-à-dire les métadonnées de description d’API contenues dans un fichier JSON ou YAML.</span><span class="sxs-lookup"><span data-stu-id="b08ef-216">The heart of Swagger is the Swagger specification, which is API description metadata in a JSON or YAML file.</span></span> <span data-ttu-id="b08ef-217">La spécification crée le contrat RESTful pour votre API, en détaillant toutes ses ressources et opérations dans un format lisible par l’homme et par la machine, pour un développement, une découverte et une intégration facilités.</span><span class="sxs-lookup"><span data-stu-id="b08ef-217">The specification creates the RESTful contract for your API, detailing all its resources and operations in both a human- and machine-readable format for easy development, discovery, and integration.</span></span>

<span data-ttu-id="b08ef-218">Cette spécification est la base de la spécification OpenAPI (OAS). Elle a été développée par une communauté ouverte, transparente et collaborative pour normaliser la façon dont les interfaces RESTful sont définies.</span><span class="sxs-lookup"><span data-stu-id="b08ef-218">The specification is the basis of the OpenAPI Specification (OAS) and is developed in an open, transparent, and collaborative community to standardize the way RESTful interfaces are defined.</span></span>

<span data-ttu-id="b08ef-219">La spécification permet de définir la façon dont un service peut être découvert et la façon dont ses fonctionnalités sont comprises.</span><span class="sxs-lookup"><span data-stu-id="b08ef-219">The specification defines the structure for how a service can be discovered and how its capabilities understood.</span></span> <span data-ttu-id="b08ef-220">Pour plus d’informations, notamment sur l’éditeur web Swagger, et pour obtenir les exemples de spécifications Swagger d’entreprises comme Spotify, Uber, Slack et Microsoft, consultez le site Swagger (<https://swagger.io>).</span><span class="sxs-lookup"><span data-stu-id="b08ef-220">For more information, including a web editor and examples of Swagger specifications from companies like Spotify, Uber, Slack, and Microsoft, see the Swagger site (<https://swagger.io>).</span></span>

### <a name="why-use-swagger"></a><span data-ttu-id="b08ef-221">Pourquoi utiliser Swagger ?</span><span class="sxs-lookup"><span data-stu-id="b08ef-221">Why use Swagger?</span></span>

<span data-ttu-id="b08ef-222">Voici pourquoi il est utile de générer des métadonnées Swagger pour votre API.</span><span class="sxs-lookup"><span data-stu-id="b08ef-222">The main reasons to generate Swagger metadata for your APIs are the following.</span></span>

<span data-ttu-id="b08ef-223">**Les autres produits peuvent consommer et intégrer automatiquement vos API**.</span><span class="sxs-lookup"><span data-stu-id="b08ef-223">**Ability for other products to automatically consume and integrate your APIs**.</span></span> <span data-ttu-id="b08ef-224">Swagger est pris en charge par des dizaines de produits et [d’outils professionnels](https://swagger.io/commercial-tools/), ainsi que par un grand nombre de [bibliothèques et de frameworks](https://swagger.io/open-source-integrations/).</span><span class="sxs-lookup"><span data-stu-id="b08ef-224">Dozens of products and [commercial tools](https://swagger.io/commercial-tools/) and many [libraries and frameworks](https://swagger.io/open-source-integrations/) support Swagger.</span></span> <span data-ttu-id="b08ef-225">Microsoft propose des produits et des outils de niveau supérieur qui peuvent consommer automatiquement les API Swagger, comme celles qui suivent :</span><span class="sxs-lookup"><span data-stu-id="b08ef-225">Microsoft has high-level products and tools that can automatically consume Swagger-based APIs, such as the following:</span></span>

- <span data-ttu-id="b08ef-226">[Rest](https://github.com/Azure/AutoRest).</span><span class="sxs-lookup"><span data-stu-id="b08ef-226">[AutoRest](https://github.com/Azure/AutoRest).</span></span> <span data-ttu-id="b08ef-227">Vous pouvez générer automatiquement des classes client .NET pour appeler Swagger.</span><span class="sxs-lookup"><span data-stu-id="b08ef-227">You can automatically generate .NET client classes for calling Swagger.</span></span> <span data-ttu-id="b08ef-228">Cet outil peut être utilisé à partir de l’interface CLI. En outre, il s’intègre à Visual Studio pour une utilisation facilitée via l’interface utilisateur graphique.</span><span class="sxs-lookup"><span data-stu-id="b08ef-228">This tool can be used from the CLI and it also integrates with Visual Studio for easy use through the GUI.</span></span>

- <span data-ttu-id="b08ef-229">[Microsoft Flow](https://flow.microsoft.com/).</span><span class="sxs-lookup"><span data-stu-id="b08ef-229">[Microsoft Flow](https://flow.microsoft.com/).</span></span> <span data-ttu-id="b08ef-230">Vous pouvez [utiliser et intégrer votre API](https://flow.microsoft.com/blog/integrating-custom-api/) automatiquement dans un flux de travail Microsoft Flow de haut niveau, sans avoir de compétences en programmation.</span><span class="sxs-lookup"><span data-stu-id="b08ef-230">You can automatically [use and integrate your API](https://flow.microsoft.com/blog/integrating-custom-api/) into a high-level Microsoft Flow workflow, with no programming skills required.</span></span>

- <span data-ttu-id="b08ef-231">[Microsoft PowerApps](https://powerapps.microsoft.com/).</span><span class="sxs-lookup"><span data-stu-id="b08ef-231">[Microsoft PowerApps](https://powerapps.microsoft.com/).</span></span> <span data-ttu-id="b08ef-232">Vous pouvez consommer automatiquement votre API à partir [d’applications mobiles PowerApps](https://powerapps.microsoft.com/blog/register-and-use-custom-apis-in-powerapps/) créées dans [PowerApps Studio](https://powerapps.microsoft.com/build-powerapps/), sans avoir de compétences en programmation.</span><span class="sxs-lookup"><span data-stu-id="b08ef-232">You can automatically consume your API from [PowerApps mobile apps](https://powerapps.microsoft.com/blog/register-and-use-custom-apis-in-powerapps/) built with [PowerApps Studio](https://powerapps.microsoft.com/build-powerapps/), with no programming skills required.</span></span>

- <span data-ttu-id="b08ef-233">[Applications logiques Azure App Service](/azure/app-service-logic/app-service-logic-what-are-logic-apps).</span><span class="sxs-lookup"><span data-stu-id="b08ef-233">[Azure App Service Logic Apps](/azure/app-service-logic/app-service-logic-what-are-logic-apps).</span></span> <span data-ttu-id="b08ef-234">Vous pouvez [utiliser et intégrer votre API dans une application logique Azure App Service](/azure/app-service-logic/app-service-logic-custom-hosted-api) automatiquement, sans avoir de compétences en programmation.</span><span class="sxs-lookup"><span data-stu-id="b08ef-234">You can automatically [use and integrate your API into an Azure App Service Logic App](/azure/app-service-logic/app-service-logic-custom-hosted-api), with no programming skills required.</span></span>

<span data-ttu-id="b08ef-235">**Vous pouvez générer automatiquement la documentation de l’API**.</span><span class="sxs-lookup"><span data-stu-id="b08ef-235">**Ability to automatically generate API documentation**.</span></span> <span data-ttu-id="b08ef-236">Lorsque vous créez des API RESTful à grande échelle, telles que des applications de microservice complexes, vous devez gérer de nombreux points de terminaison avec les différents modèles de données utilisés dans les charges utiles de demande et de réponse.</span><span class="sxs-lookup"><span data-stu-id="b08ef-236">When you create large-scale RESTful APIs, such as complex microservice-based applications, you need to handle many endpoints with different data models used in the request and response payloads.</span></span> <span data-ttu-id="b08ef-237">Une documentation appropriée et un explorateur d’API solide (comme ceux fournis par Swagger) sont essentiels au succès de votre API et à son adoption par les développeurs.</span><span class="sxs-lookup"><span data-stu-id="b08ef-237">Having proper documentation and having a solid API explorer, as you get with Swagger, is key for the success of your API and adoption by developers.</span></span>

<span data-ttu-id="b08ef-238">Les métadonnées Swagger sont utilisées par Microsoft Flow, PowerApps et Azure Logic Apps pour comprendre comment utiliser les API et s’y connecter.</span><span class="sxs-lookup"><span data-stu-id="b08ef-238">Swagger's metadata is what Microsoft Flow, PowerApps, and Azure Logic Apps use to understand how to use APIs and connect to them.</span></span>

<span data-ttu-id="b08ef-239">Il existe plusieurs options pour automatiser la génération de métadonnées Swagger pour les applications API REST ASP.NET Core, sous la forme de pages d’aide de l’API fonctionnelles, en fonction de *swagger-ui*.</span><span class="sxs-lookup"><span data-stu-id="b08ef-239">There are several options to automate Swagger metadata generation for ASP.NET Core REST API applications, in the form of functional API help pages, based on *swagger-ui*.</span></span>

<span data-ttu-id="b08ef-240">La meilleure connaissance est probablement [Swashbuckle](https://github.com/domaindrivendev/Swashbuckle.AspNetCore) qui est actuellement utilisé dans [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) . nous aborderons en détail ce guide, mais il est également possible d’utiliser [NSwag](https://github.com/RSuter/NSwag), qui peut générer des clients de machine à écrire et \# d’API C, ainsi que \# des contrôleurs c, d’une spécification Swagger ou openapi et même en analysant le fichier. dll qui contient les contrôleurs, à l’aide de [NSwagStudio](https://github.com/RSuter/NSwag/wiki/NSwagStudio).</span><span class="sxs-lookup"><span data-stu-id="b08ef-240">Probably the best know is [Swashbuckle](https://github.com/domaindrivendev/Swashbuckle.AspNetCore) which is currently used in [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) and we'll cover in some detail in this guide but there's also the option to use [NSwag](https://github.com/RSuter/NSwag), which can generate Typescript and C\# API clients, as well as C\# controllers, from a Swagger or OpenAPI specification and even by scanning the .dll that contains the controllers, using [NSwagStudio](https://github.com/RSuter/NSwag/wiki/NSwagStudio).</span></span>

### <a name="how-to-automate-api-swagger-metadata-generation-with-the-swashbuckle-nuget-package"></a><span data-ttu-id="b08ef-241">Comment automatiser la génération de métadonnées d’API Swagger avec le package NuGet Swashbuckle</span><span class="sxs-lookup"><span data-stu-id="b08ef-241">How to automate API Swagger metadata generation with the Swashbuckle NuGet package</span></span>

<span data-ttu-id="b08ef-242">La génération manuelle de métadonnées Swagger (dans un fichier JSON ou YAML) peut être fastidieuse.</span><span class="sxs-lookup"><span data-stu-id="b08ef-242">Generating Swagger metadata manually (in a JSON or YAML file) can be tedious work.</span></span> <span data-ttu-id="b08ef-243">Toutefois, vous pouvez automatiser la découverte d’API des services d’API web ASP.NET à l’aide du [package NuGet Swashbuckle](https://aka.ms/swashbuckledotnetcore) afin de générer dynamiquement les métadonnées d’API Swagger.</span><span class="sxs-lookup"><span data-stu-id="b08ef-243">However, you can automate API discovery of ASP.NET Web API services by using the [Swashbuckle NuGet package](https://aka.ms/swashbuckledotnetcore) to dynamically generate Swagger API metadata.</span></span>

<span data-ttu-id="b08ef-244">Swashbuckle génère automatiquement les métadonnées Swagger pour vos projets d’API web ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="b08ef-244">Swashbuckle automatically generates Swagger metadata for your ASP.NET Web API projects.</span></span> <span data-ttu-id="b08ef-245">Il prend en charge les projets d’API web ASP.NET Core et l’API web ASP.NET traditionnelle, ainsi que toutes les autres versions, telles qu’Azure API App, Azure Mobile App ou les microservices Azure Service Fabric reposant sur ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="b08ef-245">It supports ASP.NET Core Web API projects and the traditional ASP.NET Web API and any other flavor, such as Azure API App, Azure Mobile App, Azure Service Fabric microservices based on ASP.NET.</span></span> <span data-ttu-id="b08ef-246">Il prend également en charge les API web simples déployées dans des conteneurs, comme l’application de référence.</span><span class="sxs-lookup"><span data-stu-id="b08ef-246">It also supports plain Web API deployed on containers, as in for the reference application.</span></span>

<span data-ttu-id="b08ef-247">Swashbuckle associe l’explorateur d’API et Swagger (ou [swagger-ui](https://github.com/swagger-api/swagger-ui)) pour fournir aux utilisateurs de votre API des fonctionnalités avancées de découverte et de documentation.</span><span class="sxs-lookup"><span data-stu-id="b08ef-247">Swashbuckle combines API Explorer and Swagger or [swagger-ui](https://github.com/swagger-api/swagger-ui) to provide a rich discovery and documentation experience for your API consumers.</span></span> <span data-ttu-id="b08ef-248">Outre son moteur de génération de métadonnées Swagger, Swashbuckle contient également une version intégrée de swagger-ui, qu’il fournit automatiquement après son installation.</span><span class="sxs-lookup"><span data-stu-id="b08ef-248">In addition to its Swagger metadata generator engine, Swashbuckle also contains an embedded version of swagger-ui, which it will automatically serve up once Swashbuckle is installed.</span></span>

<span data-ttu-id="b08ef-249">Cela signifie que vous pouvez compléter votre API avec une interface utilisateur de découverte pour aider les développeurs à utiliser votre API.</span><span class="sxs-lookup"><span data-stu-id="b08ef-249">This means you can complement your API with a nice discovery UI to help developers to use your API.</span></span> <span data-ttu-id="b08ef-250">Elle nécessite très peu de code et de maintenance, car elle est générée automatiquement, ce qui vous permet de vous concentrer sur la création de votre API.</span><span class="sxs-lookup"><span data-stu-id="b08ef-250">It requires a very small amount of code and maintenance because it is automatically generated, allowing you to focus on building your API.</span></span> <span data-ttu-id="b08ef-251">Le résultat de l’explorateur d’API ressemble à celui de la figure 6-8.</span><span class="sxs-lookup"><span data-stu-id="b08ef-251">The result for the API Explorer looks like Figure 6-8.</span></span>

![Capture d’écran de l’Explorateur d’API Swagger affichant l’API eShopOContainers.](./media/data-driven-crud-microservice/swagger-metadata-eshoponcontainers-catalog-microservice.png)

<span data-ttu-id="b08ef-253">**Figure 6-8.**</span><span class="sxs-lookup"><span data-stu-id="b08ef-253">**Figure 6-8**.</span></span> <span data-ttu-id="b08ef-254">L’explorateur d’API Swashbuckle basé sur les métadonnées Swagger - Microservice de catalogue eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="b08ef-254">Swashbuckle API Explorer based on Swagger metadata—eShopOnContainers catalog microservice</span></span>

<span data-ttu-id="b08ef-255">La documentation sur les API d’interface utilisateur Swagger générées par Swashbuckle contient toutes les actions publiées.</span><span class="sxs-lookup"><span data-stu-id="b08ef-255">The Swashbuckle generated Swagger UI API documentation includes all published actions.</span></span> <span data-ttu-id="b08ef-256">L’explorateur d’API n’est pas le plus important ici.</span><span class="sxs-lookup"><span data-stu-id="b08ef-256">The API explorer is not the most important thing here.</span></span> <span data-ttu-id="b08ef-257">Une fois que votre API web peut se décrire dans les métadonnées Swagger, elle peut être utilisée facilement dans les outils Swagger, y compris dans les générateurs de code de classe proxy client qui peuvent cibler plusieurs plateformes.</span><span class="sxs-lookup"><span data-stu-id="b08ef-257">Once you have a Web API that can describe itself in Swagger metadata, your API can be used seamlessly from Swagger-based tools, including client proxy-class code generators that can target many platforms.</span></span> <span data-ttu-id="b08ef-258">Par exemple, [AutoRest](https://github.com/Azure/AutoRest) génère automatiquement des classes client .NET.</span><span class="sxs-lookup"><span data-stu-id="b08ef-258">For example, as mentioned, [AutoRest](https://github.com/Azure/AutoRest) automatically generates .NET client classes.</span></span> <span data-ttu-id="b08ef-259">Toutefois, d’autres outils comme [swagger-codegen](https://github.com/swagger-api/swagger-codegen) sont également disponibles, et permettent la génération automatique de code pour les bibliothèques clientes d’API, pour les stubs serveur et pour la documentation.</span><span class="sxs-lookup"><span data-stu-id="b08ef-259">But additional tools like [swagger-codegen](https://github.com/swagger-api/swagger-codegen) are also available, which allow code generation of API client libraries, server stubs, and documentation automatically.</span></span>

<span data-ttu-id="b08ef-260">Actuellement, Swashbuckle est constitué de cinq packages NuGet internes sous le [Swashbuckle. AspNetCore](https://www.nuget.org/packages/Swashbuckle.AspNetCore) de niveau supérieur pour les applications ASP.net core.</span><span class="sxs-lookup"><span data-stu-id="b08ef-260">Currently, Swashbuckle consists of five internal NuGet packages under the high-level metapackage [Swashbuckle.AspNetCore](https://www.nuget.org/packages/Swashbuckle.AspNetCore) for ASP.NET Core applications.</span></span>

<span data-ttu-id="b08ef-261">Après avoir installé ces packages NuGet dans votre projet d’API Web, vous devez configurer Swagger dans la classe Startup, comme dans le code **simplifié** suivant :</span><span class="sxs-lookup"><span data-stu-id="b08ef-261">After you have installed these NuGet packages in your Web API project, you need to configure Swagger in the Startup class, as in the following **simplified** code:</span></span>

```csharp
public class Startup
{
    public IConfigurationRoot Configuration { get; }
    // Other startup code...

    public void ConfigureServices(IServiceCollection services)
    {
        // Other ConfigureServices() code...

        // Add framework services.
        services.AddSwaggerGen(options =>
        {
            options.DescribeAllEnumsAsStrings();
            options.SwaggerDoc("v1", new OpenApiInfo
            {
                Title = "eShopOnContainers - Catalog HTTP API",
                Version = "v1",
                Description = "The Catalog Microservice HTTP API. This is a Data-Driven/CRUD microservice sample"
            });
        });

        // Other ConfigureServices() code...
    }

    public void Configure(IApplicationBuilder app,
        IHostingEnvironment env,
        ILoggerFactory loggerFactory)
    {
        // Other Configure() code...
        // ...
        app.UseSwagger()
            .UseSwaggerUI(c =>
            {
                c.SwaggerEndpoint("/swagger/v1/swagger.json", "My API V1");
            });
    }
}
```

<span data-ttu-id="b08ef-262">Après cela, vous pouvez démarrer votre application et parcourir les points de terminaison JSON et d’interface utilisateur Swagger suivants à l’aide d’URL de ce type :</span><span class="sxs-lookup"><span data-stu-id="b08ef-262">Once this is done, you can start your application and browse the following Swagger JSON and UI endpoints using URLs like these:</span></span>

```console
  http://<your-root-url>/swagger/v1/swagger.json

  http://<your-root-url>/swagger/
```

<span data-ttu-id="b08ef-263">Vous avez déjà vu l’interface utilisateur générée par Swashbuckle pour une URL telle que `http://<your-root-url>/swagger`.</span><span class="sxs-lookup"><span data-stu-id="b08ef-263">You previously saw the generated UI created by Swashbuckle for a URL like `http://<your-root-url>/swagger`.</span></span> <span data-ttu-id="b08ef-264">Dans la figure 6-9, vous pouvez également voir comment tester une méthode d’API.</span><span class="sxs-lookup"><span data-stu-id="b08ef-264">In Figure 6-9 you can also see how you can test any API method.</span></span>

![Capture d’écran de l’interface utilisateur Swagger montrant les outils de test disponibles.](./media/data-driven-crud-microservice/swashbuckle-ui-testing.png)

<span data-ttu-id="b08ef-266">**Figure 6-9.**</span><span class="sxs-lookup"><span data-stu-id="b08ef-266">**Figure 6-9**.</span></span> <span data-ttu-id="b08ef-267">Interface utilisateur Swashbuckle UI testant la méthode d’API Catalog/Items</span><span class="sxs-lookup"><span data-stu-id="b08ef-267">Swashbuckle UI testing the Catalog/Items API method</span></span>

<span data-ttu-id="b08ef-268">Le détail de l’API d’interface utilisateur Swagger montre un exemple de la réponse et peut être utilisé pour exécuter la véritable API, ce qui est idéal pour la découverte des développeurs.</span><span class="sxs-lookup"><span data-stu-id="b08ef-268">The Swagger UI API detail shows a sample of the response and can be used to execute the real API, which is great for developer discovery.</span></span> <span data-ttu-id="b08ef-269">La figure 6-10 montre les métadonnées JSON Swagger générées à partir du microservice eShopOnContainers (utilisé par les outils ci-dessous) quand `http://<your-root-url>/swagger/v1/swagger.json` est demandé avec [Postman](https://www.getpostman.com/).</span><span class="sxs-lookup"><span data-stu-id="b08ef-269">Figure 6-10 shows the Swagger JSON metadata generated from the eShopOnContainers microservice (which is what the tools use underneath) when you request `http://<your-root-url>/swagger/v1/swagger.json` using [Postman](https://www.getpostman.com/).</span></span>

![Capture d’écran d’un exemple d’interface utilisateur de publication montrant les métadonnées JSON Swagger.](./media/data-driven-crud-microservice/swagger-json-metadata.png)

<span data-ttu-id="b08ef-271">**Figure 6-10.**</span><span class="sxs-lookup"><span data-stu-id="b08ef-271">**Figure 6-10**.</span></span> <span data-ttu-id="b08ef-272">Métadonnées JSON Swagger</span><span class="sxs-lookup"><span data-stu-id="b08ef-272">Swagger JSON metadata</span></span>

<span data-ttu-id="b08ef-273">C’est aussi simple que cela.</span><span class="sxs-lookup"><span data-stu-id="b08ef-273">It is that simple.</span></span> <span data-ttu-id="b08ef-274">Et parce qu’elles sont générées automatiquement, les métadonnées Swagger grandissent à mesure que vous ajoutez des fonctionnalités à votre API.</span><span class="sxs-lookup"><span data-stu-id="b08ef-274">And because it is automatically generated, the Swagger metadata will grow when you add more functionality to your API.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="b08ef-275">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="b08ef-275">Additional resources</span></span>

- <span data-ttu-id="b08ef-276">**API Web ASP.NET les pages d’aide à l’aide de Swagger** </span><span class="sxs-lookup"><span data-stu-id="b08ef-276">**ASP.NET Web API Help Pages using Swagger** </span></span>\
  [https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger](/aspnet/core/tutorials/web-api-help-pages-using-swagger)

- <span data-ttu-id="b08ef-277">**Prise en main de Swashbuckle et ASP.NET Core** </span><span class="sxs-lookup"><span data-stu-id="b08ef-277">**Get started with Swashbuckle and ASP.NET Core** </span></span>\
  [https://docs.microsoft.com/aspnet/core/tutorials/getting-started-with-swashbuckle](/aspnet/core/tutorials/getting-started-with-swashbuckle)

- <span data-ttu-id="b08ef-278">**Prise en main de NSwag et ASP.NET Core** </span><span class="sxs-lookup"><span data-stu-id="b08ef-278">**Get started with NSwag and ASP.NET Core** </span></span>\
  [https://docs.microsoft.com/aspnet/core/tutorials/getting-started-with-nswag](/aspnet/core/tutorials/getting-started-with-nswag)

> [!div class="step-by-step"]
> <span data-ttu-id="b08ef-279">[Précédent](microservice-application-design.md) 
>  [Suivant](multi-container-applications-docker-compose.md)</span><span class="sxs-lookup"><span data-stu-id="b08ef-279">[Previous](microservice-application-design.md)
[Next](multi-container-applications-docker-compose.md)</span></span>
