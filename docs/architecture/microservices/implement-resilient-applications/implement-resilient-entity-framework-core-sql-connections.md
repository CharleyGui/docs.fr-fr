---
title: Implémenter des connexions SQL à Entity Framework Core résilientes
description: Découvrez comment implémenter des connexions SQL à Entity Framework Core résilientes. Cette technique est particulièrement importante lors de l’utilisation d’Azure SQL Database dans le cloud.
ms.date: 10/16/2018
ms.openlocfilehash: cae3550ce301750949b042957d5d10f0167e614c
ms.sourcegitcommit: 88fbb019b84c2d044d11fb4f6004aec07f2b25b1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/05/2021
ms.locfileid: "97899559"
---
# <a name="implement-resilient-entity-framework-core-sql-connections"></a>Implémenter des connexions SQL à Entity Framework Core résilientes

Pour Azure SQL DB, Entity Framework (EF) Core fournit déjà la logique de résilience et de nouvelle tentative de connexion de base de données interne. Par contre, vous devez autoriser la stratégie d’exécution d’Entity Framework pour chaque connexion <xref:Microsoft.EntityFrameworkCore.DbContext> si vous voulez avoir des [connexions EF Core résilientes](/ef/core/miscellaneous/connection-resiliency).

Par exemple, le code suivant au niveau des connexions EF Core autorise les connexions SQL résilientes qui sont retentées si elles échouent.

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

## <a name="execution-strategies-and-explicit-transactions-using-begintransaction-and-multiple-dbcontexts"></a>Stratégies d’exécution et transactions explicites utilisant BeginTransaction et plusieurs DbContexts

Quand les nouvelles tentatives sont activées dans les connexions EF Core, chaque opération que vous effectuez avec EF Core devient sa propre opération de nouvelle tentative. Chaque requête et chaque appel à `SaveChanges` sont retentés ensemble si un échec passager se produit.

Toutefois, si votre code lance une transaction à l’aide de `BeginTransaction`, vous définissez votre propre groupe d’opérations qui doivent être traitées en tant qu’unité. Tous les éléments à l’intérieur de la transaction doivent être annulés en cas d’échec.

Si vous essayez d’exécuter cette transaction lors de l’utilisation d’une stratégie d’exécution EF (stratégie de nouvelle tentative) et que vous appelez `SaveChanges` à partir de plusieurs DbContexts, vous obtiendrez une exception semblable à celle-ci :

> System.InvalidOperationException : La stratégie d’exécution configurée « SqlServerRetryingExecutionStrategy » ne prend pas en charge les transactions lancées par l’utilisateur. Utilisez la stratégie d’exécution retournée par « DbContext.Database.CreateExecutionStrategy() » pour exécuter toutes les opérations de la transaction en tant qu’ensemble pouvant être retenté.

La solution consiste à appeler manuellement la stratégie d’exécution EF avec un délégué représentant tout ce qui doit être exécuté. En cas d’échec passager, la stratégie d’exécution appelle de nouveau le délégué. Par exemple, le code suivant montre comment elle est implémentée dans eShopOnContainers avec plusieurs DbContexts (\_catalogContext et IntegrationEventLogContext) quand un produit est mis à jour puis que l’objet ProductPriceChangedIntegrationEvent est enregistré, ce qui nécessite d’utiliser un autre DbContext.

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

Le premier <xref:Microsoft.EntityFrameworkCore.DbContext> est `_catalogContext` et le second `DbContext` se trouve dans l’objet `_catalogIntegrationEventService`. L’action de validation est effectuée sur tous les objets `DbContext` utilisant une stratégie d’exécution EF.

Pour obtenir cette validation `DbContext` multiple, `SaveEventAndCatalogContextChangesAsync` utilise une classe `ResilientTransaction`, comme indiqué dans le code suivant :

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

La méthode `ResilientTransaction.ExecuteAsync` commence une transaction à partir du `DbContext` transmis (`_catalogContext`), fait en sorte que `EventLogService` utilise cette transaction pour enregistrer les modifications à partir de `IntegrationEventLogContext`, puis valide la transaction entière.

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
            await using var transaction = await _context.Database.BeginTransactionAsync();
            await action();
            await transaction.CommitAsync();
        });
    }
}
```

## <a name="additional-resources"></a>Ressources supplémentaires

- **Résilience des connexions et interception des commandes avec EF dans une application ASP.NET MVC** \
  [https://docs.microsoft.com/aspnet/mvc/overview/getting-started/getting-started-with-ef-using-mvc/connection-resiliency-and-command-interception-with-the-entity-framework-in-an-asp-net-mvc-application](/aspnet/mvc/overview/getting-started/getting-started-with-ef-using-mvc/connection-resiliency-and-command-interception-with-the-entity-framework-in-an-asp-net-mvc-application)

- **Cesar de la Torre. Utilisation de connexions et de transactions Entity Framework Core SQL résilientes** \
  <https://devblogs.microsoft.com/cesardelatorre/using-resilient-entity-framework-core-sql-connections-and-transactions-retries-with-exponential-backoff/>

>[!div class="step-by-step"]
>[Précédent](implement-retries-exponential-backoff.md) 
> [Suivant](use-httpclientfactory-to-implement-resilient-http-requests.md)
