---
title: Implémenter des connexions SQL à Entity Framework Core résilientes
description: Découvrez comment implémenter des connexions SQL à Entity Framework Core résilientes. Cette technique est particulièrement importante lors de l’utilisation d’Azure SQL Database dans le cloud.
ms.date: 10/16/2018
ms.openlocfilehash: 7a047edca21d63a451e90f407b23f3358d461330
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/03/2020
ms.locfileid: "78241063"
---
# <a name="implement-resilient-entity-framework-core-sql-connections"></a><span data-ttu-id="b4ebc-104">Implémenter des connexions SQL à Entity Framework Core résilientes</span><span class="sxs-lookup"><span data-stu-id="b4ebc-104">Implement resilient Entity Framework Core SQL connections</span></span>

<span data-ttu-id="b4ebc-105">Pour Azure SQL DB, Entity Framework (EF) Core fournit déjà la logique de résilience et de nouvelle tentative de connexion de base de données interne.</span><span class="sxs-lookup"><span data-stu-id="b4ebc-105">For Azure SQL DB, Entity Framework (EF) Core already provides internal database connection resiliency and retry logic.</span></span> <span data-ttu-id="b4ebc-106">Par contre, vous devez autoriser la stratégie d’exécution d’Entity Framework pour chaque connexion <xref:Microsoft.EntityFrameworkCore.DbContext> si vous voulez avoir des [connexions EF Core résilientes](/ef/core/miscellaneous/connection-resiliency).</span><span class="sxs-lookup"><span data-stu-id="b4ebc-106">But you need to enable the Entity Framework execution strategy for each <xref:Microsoft.EntityFrameworkCore.DbContext> connection if you want to have [resilient EF Core connections](/ef/core/miscellaneous/connection-resiliency).</span></span>

<span data-ttu-id="b4ebc-107">Par exemple, le code suivant au niveau des connexions EF Core autorise les connexions SQL résilientes qui sont retentées si elles échouent.</span><span class="sxs-lookup"><span data-stu-id="b4ebc-107">For instance, the following code at the EF Core connection level enables resilient SQL connections that are retried if the connection fails.</span></span>

```csharp
// Startup.cs from any ASP.NET Core Web API
public class Startup
{
    // Other code ...
    public IServiceProvider ConfigureServices(IServiceCollection services)
    {
        // ...
        services.AddDbContext<CatalogContext>(options =>
        {
            options.UseSqlServer(Configuration["ConnectionString"],
            sqlServerOptionsAction: sqlOptions =>
            {
                sqlOptions.EnableRetryOnFailure(
                maxRetryCount: 10,
                maxRetryDelay: TimeSpan.FromSeconds(30),
                errorNumbersToAdd: null);
            });
        });
    }
//...
}
```

## <a name="execution-strategies-and-explicit-transactions-using-begintransaction-and-multiple-dbcontexts"></a><span data-ttu-id="b4ebc-108">Stratégies d’exécution et transactions explicites utilisant BeginTransaction et plusieurs DbContexts</span><span class="sxs-lookup"><span data-stu-id="b4ebc-108">Execution strategies and explicit transactions using BeginTransaction and multiple DbContexts</span></span>

<span data-ttu-id="b4ebc-109">Quand les nouvelles tentatives sont activées dans les connexions EF Core, chaque opération que vous effectuez avec EF Core devient sa propre opération de nouvelle tentative.</span><span class="sxs-lookup"><span data-stu-id="b4ebc-109">When retries are enabled in EF Core connections, each operation you perform using EF Core becomes its own retryable operation.</span></span> <span data-ttu-id="b4ebc-110">Chaque requête et chaque appel à `SaveChanges` sont retentés ensemble si un échec passager se produit.</span><span class="sxs-lookup"><span data-stu-id="b4ebc-110">Each query and each call to `SaveChanges` will be retried as a unit if a transient failure occurs.</span></span>

<span data-ttu-id="b4ebc-111">Toutefois, si votre code lance une transaction à l’aide de `BeginTransaction`, vous définissez votre propre groupe d’opérations qui doivent être traitées en tant qu’unité.</span><span class="sxs-lookup"><span data-stu-id="b4ebc-111">However, if your code initiates a transaction using `BeginTransaction`, you're defining your own group of operations that need to be treated as a unit.</span></span> <span data-ttu-id="b4ebc-112">Tous les éléments à l’intérieur de la transaction doivent être annulés en cas d’échec.</span><span class="sxs-lookup"><span data-stu-id="b4ebc-112">Everything inside the transaction has to be rolled back if a failure occurs.</span></span>

<span data-ttu-id="b4ebc-113">Si vous essayez d’exécuter cette transaction lors de l’utilisation d’une stratégie d’exécution EF (stratégie de nouvelle tentative) et que vous appelez `SaveChanges` à partir de plusieurs DbContexts, vous obtiendrez une exception semblable à celle-ci :</span><span class="sxs-lookup"><span data-stu-id="b4ebc-113">If you try to execute that transaction when using an EF execution strategy (retry policy) and you call `SaveChanges` from multiple DbContexts, you'll get an exception like this one:</span></span>

> <span data-ttu-id="b4ebc-114">System.InvalidOperationException : La stratégie d’exécution configurée « SqlServerRetryingExecutionStrategy » ne prend pas en charge les transactions lancées par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="b4ebc-114">System.InvalidOperationException: The configured execution strategy 'SqlServerRetryingExecutionStrategy' does not support user initiated transactions.</span></span> <span data-ttu-id="b4ebc-115">Utilisez la stratégie d’exécution retournée par « DbContext.Database.CreateExecutionStrategy() » pour exécuter toutes les opérations de la transaction en tant qu’ensemble pouvant être retenté.</span><span class="sxs-lookup"><span data-stu-id="b4ebc-115">Use the execution strategy returned by 'DbContext.Database.CreateExecutionStrategy()' to execute all the operations in the transaction as a retriable unit.</span></span>

<span data-ttu-id="b4ebc-116">La solution consiste à appeler manuellement la stratégie d’exécution EF avec un délégué représentant tout ce qui doit être exécuté.</span><span class="sxs-lookup"><span data-stu-id="b4ebc-116">The solution is to manually invoke the EF execution strategy with a delegate representing everything that needs to be executed.</span></span> <span data-ttu-id="b4ebc-117">En cas d’échec passager, la stratégie d’exécution appelle de nouveau le délégué.</span><span class="sxs-lookup"><span data-stu-id="b4ebc-117">If a transient failure occurs, the execution strategy will invoke the delegate again.</span></span> <span data-ttu-id="b4ebc-118">Par exemple, le code suivant montre comment elle est implémentée dans eShopOnContainers avec plusieurs DbContexts (\_catalogContext et IntegrationEventLogContext) quand un produit est mis à jour puis que l’objet ProductPriceChangedIntegrationEvent est enregistré, ce qui nécessite d’utiliser un autre DbContext.</span><span class="sxs-lookup"><span data-stu-id="b4ebc-118">For example, the following code show how it's implemented in eShopOnContainers with two multiple DbContexts (\_catalogContext and the IntegrationEventLogContext) when updating a product and then saving the ProductPriceChangedIntegrationEvent object, which needs to use a different DbContext.</span></span>

```csharp
public async Task<IActionResult> UpdateProduct(
    [FromBody]CatalogItem productToUpdate)
{
    // Other code ...

    var oldPrice = catalogItem.Price;
    var raiseProductPriceChangedEvent = oldPrice != productToUpdate.Price;

    // Update current product
    catalogItem = productToUpdate;

    // Save product's data and publish integration event through the Event Bus
    // if price has changed
    if (raiseProductPriceChangedEvent)
    {
        //Create Integration Event to be published through the Event Bus
        var priceChangedEvent = new ProductPriceChangedIntegrationEvent(
          catalogItem.Id, productToUpdate.Price, oldPrice);

       // Achieving atomicity between original Catalog database operation and the
       // IntegrationEventLog thanks to a local transaction
       await _catalogIntegrationEventService.SaveEventAndCatalogContextChangesAsync(
           priceChangedEvent);

       // Publish through the Event Bus and mark the saved event as published
       await _catalogIntegrationEventService.PublishThroughEventBusAsync(
           priceChangedEvent);
    }
    // Just save the updated product because the Product's Price hasn't changed.
    else
    {
        await _catalogContext.SaveChangesAsync();
    }
}
```

<span data-ttu-id="b4ebc-119">Le premier <xref:Microsoft.EntityFrameworkCore.DbContext> est `_catalogContext` et le second `DbContext` se trouve dans l’objet `_catalogIntegrationEventService`.</span><span class="sxs-lookup"><span data-stu-id="b4ebc-119">The first <xref:Microsoft.EntityFrameworkCore.DbContext> is `_catalogContext` and the second `DbContext` is within the `_catalogIntegrationEventService` object.</span></span> <span data-ttu-id="b4ebc-120">L’action de validation est effectuée sur tous les objets `DbContext` utilisant une stratégie d’exécution EF.</span><span class="sxs-lookup"><span data-stu-id="b4ebc-120">The Commit action is performed across all `DbContext` objects using an EF execution strategy.</span></span>

<span data-ttu-id="b4ebc-121">Pour obtenir cette validation `DbContext` multiple, `SaveEventAndCatalogContextChangesAsync` utilise une classe `ResilientTransaction`, comme indiqué dans le code suivant :</span><span class="sxs-lookup"><span data-stu-id="b4ebc-121">To achieve this multiple `DbContext` commit, the `SaveEventAndCatalogContextChangesAsync` uses a `ResilientTransaction` class, as shown in the following code:</span></span>

```csharp
public class CatalogIntegrationEventService : ICatalogIntegrationEventService
{
    //…
    public async Task SaveEventAndCatalogContextChangesAsync(
        IntegrationEvent evt)
    {
        // Use of an EF Core resiliency strategy when using multiple DbContexts
        // within an explicit BeginTransaction():
        // https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency
        await ResilientTransaction.New(_catalogContext).ExecuteAsync(async () =>
        {
            // Achieving atomicity between original catalog database
            // operation and the IntegrationEventLog thanks to a local transaction
            await _catalogContext.SaveChangesAsync();
            await _eventLogService.SaveEventAsync(evt,
                _catalogContext.Database.CurrentTransaction.GetDbTransaction());
        });
    }
}
```

<span data-ttu-id="b4ebc-122">La méthode `ResilientTransaction.ExecuteAsync` commence une transaction à partir du `DbContext` transmis (`_catalogContext`), fait en sorte que `EventLogService` utilise cette transaction pour enregistrer les modifications à partir de `IntegrationEventLogContext`, puis valide la transaction entière.</span><span class="sxs-lookup"><span data-stu-id="b4ebc-122">The `ResilientTransaction.ExecuteAsync` method basically begins a transaction from the passed `DbContext` (`_catalogContext`) and then makes the `EventLogService` use that transaction to save changes from the `IntegrationEventLogContext` and then commits the whole transaction.</span></span>

```csharp
public class ResilientTransaction
{
    private DbContext _context;
    private ResilientTransaction(DbContext context) =>
        _context = context ?? throw new ArgumentNullException(nameof(context));

    public static ResilientTransaction New (DbContext context) =>
        new ResilientTransaction(context);

    public async Task ExecuteAsync(Func<Task> action)
    {
        // Use of an EF Core resiliency strategy when using multiple DbContexts
        // within an explicit BeginTransaction():
        // https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency
        var strategy = _context.Database.CreateExecutionStrategy();
        await strategy.ExecuteAsync(async () =>
        {
            using (var transaction = _context.Database.BeginTransaction())
            {
                await action();
                transaction.Commit();
            }
        });
    }
}
```

## <a name="additional-resources"></a><span data-ttu-id="b4ebc-123">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="b4ebc-123">Additional resources</span></span>

- <span data-ttu-id="b4ebc-124">**Résilience des connexions et Interception des commandes avec EF dans une application ASP.NET MVC** </span><span class="sxs-lookup"><span data-stu-id="b4ebc-124">**Connection Resiliency and Command Interception with EF in an ASP.NET MVC Application** </span></span>\
  [https://docs.microsoft.com/aspnet/mvc/overview/getting-started/getting-started-with-ef-using-mvc/connection-resiliency-and-command-interception-with-the-entity-framework-in-an-asp-net-mvc-application](/aspnet/mvc/overview/getting-started/getting-started-with-ef-using-mvc/connection-resiliency-and-command-interception-with-the-entity-framework-in-an-asp-net-mvc-application)

- <span data-ttu-id="b4ebc-125">**Cesar de la Torre. Utilisation de connexions et de transactions Entity Framework Core SQL résilientes** </span><span class="sxs-lookup"><span data-stu-id="b4ebc-125">**Cesar de la Torre. Using Resilient Entity Framework Core SQL Connections and Transactions** </span></span>\
  <https://devblogs.microsoft.com/cesardelatorre/using-resilient-entity-framework-core-sql-connections-and-transactions-retries-with-exponential-backoff/>

>[!div class="step-by-step"]
><span data-ttu-id="b4ebc-126">[Précédent](implement-retries-exponential-backoff.md)
>[Suivant](use-httpclientfactory-to-implement-resilient-http-requests.md)</span><span class="sxs-lookup"><span data-stu-id="b4ebc-126">[Previous](implement-retries-exponential-backoff.md)
[Next](use-httpclientfactory-to-implement-resilient-http-requests.md)</span></span>
