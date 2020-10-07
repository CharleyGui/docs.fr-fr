---
title: Utiliser IHttpClientFactory pour implémenter des requêtes HTTP résilientes
description: Découvrez comment utiliser IHttpClientFactory, disponible depuis .NET Core 2,1, pour la création d' `HttpClient` instances, ce qui vous permet de l’utiliser facilement dans vos applications.
ms.date: 08/31/2020
ms.openlocfilehash: 4ebb82395dd685d30846b3549b654abf7c41d43f
ms.sourcegitcommit: 636af37170ae75a11c4f7d1ecd770820e7dfe7bd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2020
ms.locfileid: "91804807"
---
# <a name="use-ihttpclientfactory-to-implement-resilient-http-requests"></a>Utiliser IHttpClientFactory pour implémenter des requêtes HTTP résilientes

<xref:System.Net.Http.IHttpClientFactory> est un contrat implémenté par `DefaultHttpClientFactory` , une fabrique consignes strictes, disponible depuis .net Core 2,1, pour la création d' <xref:System.Net.Http.HttpClient> instances à utiliser dans vos applications.

## <a name="issues-with-the-original-httpclient-class-available-in-net-core"></a>Problèmes liés à la classe HttpClient d’origine disponible dans .NET Core

La classe d’origine et la <xref:System.Net.Http.HttpClient> classe connue peuvent être facilement utilisées, mais dans certains cas, elle n’est pas utilisée correctement par de nombreux développeurs.

Bien que cette classe implémente `IDisposable` , la déclaration et l’instanciation dans une `using` instruction n’est pas recommandée, car lorsque l' `HttpClient` objet est supprimé, le Socket sous-jacent n’est pas libéré immédiatement, ce qui peut entraîner un problème d' _épuisement du socket_ . Pour plus d’informations sur ce problème, consultez le billet de blog [que vous utilisez httpclient incorrect et déstabiliser votre logiciel](https://aspnetmonsters.com/2016/08/2016-08-27-httpclientwrong/).

Par conséquent, `HttpClient` est destiné à être instancié une seule fois et réutilisé tout au long de la durée de vie d’une application. L’instanciation d’une classe `HttpClient` pour chaque demande épuise le nombre de sockets disponibles sous des charges élevées. Ce problème entraîne des erreurs `SocketException`. Les approches possibles pour résoudre ce problème sont basées sur la création de l’objet `HttpClient` singleton ou statique, comme expliqué dans cet [article Microsoft sur l’utilisation de HttpClient](../../../csharp/tutorials/console-webapiclient.md). Il peut s’agir d’une bonne solution pour les applications console à courte durée de vie ou similaire, qui s’exécutent plusieurs fois par jour.

L’utilisation d’une instance partagée de dans des processus de longue durée constitue un autre problème que les développeurs peuvent rencontrer `HttpClient` . Dans le cas où le HttpClient est instancié comme un singleton ou un objet statique, il ne parvient pas à gérer les modifications DNS comme décrit dans ce [numéro](https://github.com/dotnet/runtime/issues/18348) du référentiel dotnet/Runtime github.

Toutefois, le problème n’est pas vraiment avec `HttpClient` par se, mais avec le [constructeur par défaut pour httpclient](/dotnet/api/system.net.http.httpclient.-ctor?view=netcore-3.1#System_Net_Http_HttpClient__ctor), car il crée une nouvelle instance concrète de <xref:System.Net.Http.HttpMessageHandler> , qui est celle qui a des problèmes d' *épuisement des sockets* et des modifications DNS mentionnées ci-dessus.

Pour résoudre les problèmes mentionnés ci-dessus et rendre les `HttpClient` instances gérables, .net Core 2,1 <xref:System.Net.Http.IHttpClientFactory> a introduit l’interface qui peut être utilisée pour configurer et créer des `HttpClient` instances dans une application via l’injection de dépendances (di). Il fournit également des extensions pour l’intergiciel (middleware) basé sur Polly afin de tirer parti des gestionnaires de délégation dans HttpClient.

[Polly](http://www.thepollyproject.org/) est une bibliothèque de gestion des erreurs temporaires qui permet aux développeurs d’ajouter de la résilience à leurs applications à l’aide de stratégies prédéfinies de façon Fluent et thread-safe.

## <a name="benefits-of-using-ihttpclientfactory"></a>Avantages de l’utilisation de IHttpClientFactory

L’implémentation actuelle de <xref:System.Net.Http.IHttpClientFactory> , qui implémente également <xref:System.Net.Http.IHttpMessageHandlerFactory> , offre les avantages suivants :

- Fournit un emplacement central pour nommer et configurer des objets logiques `HttpClient` . Par exemple, vous pouvez configurer un client (Service Agent) qui est préconfiguré pour accéder à un microservice spécifique.
- Codifier le concept d’intergiciel (middleware sortant) via la délégation de gestionnaires dans et l’implémentation de l' `HttpClient` intergiciel (middleware) basé sur Polly pour tirer parti des stratégies de Polly pour la résilience.
- `HttpClient` intègre déjà le concept de délégation des gestionnaires qui pourraient être liés ensemble pour les requêtes HTTP sortantes. Vous pouvez inscrire des clients HTTP dans l’usine et utiliser un gestionnaire Polly pour utiliser des stratégies Polly pour les nouvelles tentatives, les CircuitBreakers, etc.
- Gérez la durée de vie de <xref:System.Net.Http.HttpMessageHandler> pour éviter les problèmes/problèmes mentionnés qui peuvent se produire lors de la gestion des `HttpClient` durées de vie vous-même.

> [!TIP]
> Les `HttpClient` instances injectées par di, peuvent être supprimées de manière sécurisée, car le associé `HttpMessageHandler` est géré par la fabrique. En fait, les instances injectées `HttpClient` sont *étendues* d’une perspective di.

> [!NOTE]
> L’implémentation de `IHttpClientFactory` ( `DefaultHttpClientFactory` ) est étroitement liée à l’implémentation de di dans le `Microsoft.Extensions.DependencyInjection` package NuGet. Pour plus d’informations sur l’utilisation d’autres conteneurs d’injection de données, consultez cette [discussion GitHub](https://github.com/dotnet/extensions/issues/1345).

## <a name="multiple-ways-to-use-ihttpclientfactory"></a>Plusieurs manières d’utiliser IHttpClientFactory

Il existe diverses façons d’utiliser `IHttpClientFactory` dans votre application :

- Utilisation de base
- Utiliser des clients nommés
- Utiliser des clients typés
- Utiliser des clients générés

Par souci de concision, ce guide présente la manière la plus structurée d’utiliser `IHttpClientFactory` , qui consiste à utiliser des clients typés (modèle de l’agent de service). Toutefois, toutes les options sont documentées et sont actuellement répertoriées dans cet [article pour couvrir l' `IHttpClientFactory` utilisation](/aspnet/core/fundamentals/http-requests#consumption-patterns).

## <a name="how-to-use-typed-clients-with-ihttpclientfactory"></a>Utilisation de clients typés avec IHttpClientFactory

Mais qu’est-ce donc qu’un « client typé » ? Il s’agit simplement d’un `HttpClient` qui est préconfiguré pour une utilisation spécifique. Cette configuration peut inclure des valeurs spécifiques telles que le serveur de base, des en-têtes HTTP ou des délais d’expiration.

Le diagramme suivant montre comment les clients typés sont utilisés avec `IHttpClientFactory` :

![Diagramme montrant comment les clients typés sont utilisés avec IHttpClientFactory.](./media/use-httpclientfactory-to-implement-resilient-http-requests/client-application-code.png)

**Figure 8-4**. Utilisation `IHttpClientFactory` de avec les classes clientes typées.

Dans l’image ci-dessus, une `ClientService` (utilisée par un contrôleur ou un code client) utilise un `HttpClient` créé par l’inscrit `IHttpClientFactory` . Cette fabrique assigne un `HttpMessageHandler` à partir d’un pool à `HttpClient` . Le `HttpClient` peut être configuré avec les stratégies de Polly lors de l’inscription du `IHttpClientFactory` dans le conteneur d’injection de règles avec la méthode d’extension <xref:Microsoft.Extensions.DependencyInjection.HttpClientFactoryServiceCollectionExtensions.AddHttpClient%2A> .

Pour configurer la structure ci-dessus, ajoutez-la <xref:System.Net.Http.IHttpClientFactory> dans votre application en installant le `Microsoft.Extensions.Http` package NuGet qui comprend la <xref:Microsoft.Extensions.DependencyInjection.HttpClientFactoryServiceCollectionExtensions.AddHttpClient%2A> méthode d’extension pour <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection> . Cette méthode d’extension inscrit la `DefaultHttpClientFactory` classe interne à utiliser comme singleton pour l’interface `IHttpClientFactory` . Elle définit une configuration temporaire pour <xref:Microsoft.Extensions.Http.HttpMessageHandlerBuilder>. Ce gestionnaire de messages (objet <xref:System.Net.Http.HttpMessageHandler>), obtenu à partir d’un pool, est utilisé par le `HttpClient` retourné à partir de la fabrique.

Dans le code suivant, vous pouvez voir comment utiliser `AddHttpClient()` pour enregistrer les clients typés (agents de service) qui ont besoin d’utiliser `HttpClient`.

```csharp
// Startup.cs
//Add http client services at ConfigureServices(IServiceCollection services)
services.AddHttpClient<ICatalogService, CatalogService>();
services.AddHttpClient<IBasketService, BasketService>();
services.AddHttpClient<IOrderingService, OrderingService>();
```

L’inscription des services du client comme indiqué dans le code précédent, `DefaultClientFactory` crée une norme `HttpClient` pour chaque service.

Vous pouvez également ajouter une configuration spécifique à l’instance dans l’inscription à, par exemple, configurer l’adresse de base et ajouter des stratégies de résilience, comme illustré dans le code suivant :

```csharp
services.AddHttpClient<ICatalogService, CatalogService>(client =>
{
    client.BaseAddress = new Uri(Configuration["BaseUrl"]);
})
    .AddPolicyHandler(GetRetryPolicy())
    .AddPolicyHandler(GetCircuitBreakerPolicy());
```

Pour les besoins de l’exemple, vous pouvez voir l’une des stratégies ci-dessus dans le code suivant :

```csharp
static IAsyncPolicy<HttpResponseMessage> GetRetryPolicy()
{
    return HttpPolicyExtensions
        .HandleTransientHttpError()
        .OrResult(msg => msg.StatusCode == System.Net.HttpStatusCode.NotFound)
        .WaitAndRetryAsync(6, retryAttempt => TimeSpan.FromSeconds(Math.Pow(2, retryAttempt)));
}
```

Vous trouverez plus d’informations sur l’utilisation de Polly dans l' [article suivant](implement-http-call-retries-exponential-backoff-polly.md).

### <a name="httpclient-lifetimes"></a>Durées de vie de HttpClient

Chaque fois que vous obtenez un objet `HttpClient` à partir de `IHttpClientFactory`, une nouvelle instance est retournée. Mais chaque `HttpClient` utilise un `HttpMessageHandler` qui est mis en pool et réutilisé par `IHttpClientFactory` pour réduire la consommation de ressources, tant que la durée de vie du `HttpMessageHandler` n’a pas expiré.

Le regroupement de gestionnaires est souhaitable, car chaque gestionnaire gère généralement ses propres connexions HTTP sous-jacentes : créer plus de gestionnaires que nécessaire peut entraîner des délais dans la connexion. Certains gestionnaires conservent aussi les connexions indéfiniment ouvertes, ce qui peut empêcher le gestionnaire de réagir aux changements du DNS.

Les objets `HttpMessageHandler` du pool ont une durée de vie qui correspond à la durée pendant laquelle une instance `HttpMessageHandler` du pool peut être réutilisée. La valeur par défaut est de deux minutes, mais elle peut être remplacée pour chaque client typé. Pour la remplacer, appelez `SetHandlerLifetime()` sur le <xref:Microsoft.Extensions.DependencyInjection.IHttpClientBuilder> qui est retourné lors de la création du client, comme indiqué dans le code suivant :

```csharp
//Set 5 min as the lifetime for the HttpMessageHandler objects in the pool used for the Catalog Typed Client
services.AddHttpClient<ICatalogService, CatalogService>()
    .SetHandlerLifetime(TimeSpan.FromMinutes(5));
```

Chaque client typé peut avoir sa propre valeur de durée de vie de gestionnaire configurée. Définissez la durée de vie sur `InfiniteTimeSpan` pour désactiver l’expiration du gestionnaire.

### <a name="implement-your-typed-client-classes-that-use-the-injected-and-configured-httpclient"></a>Implémenter les classes de client typé qui utilisent l’objet HttpClient injecté et configuré

Au cours d’une étape précédente, vous devez définir vos classes clientes typées, telles que les classes dans l’exemple de code, telles que « BasketService », « CatalogService », « OrderingService », etc. : un client typé est une classe qui accepte un `HttpClient` objet (injecté par le biais de son constructeur) et l’utilise pour appeler un service http distant. Par exemple :

```csharp
public class CatalogService : ICatalogService
{
    private readonly HttpClient _httpClient;
    private readonly string _remoteServiceBaseUrl;

    public CatalogService(HttpClient httpClient)
    {
        _httpClient = httpClient;
    }

    public async Task<Catalog> GetCatalogItems(int page, int take,
                                               int? brand, int? type)
    {
        var uri = API.Catalog.GetAllCatalogItems(_remoteServiceBaseUrl,
                                                 page, take, brand, type);

        var responseString = await _httpClient.GetStringAsync(uri);

        var catalog = JsonConvert.DeserializeObject<Catalog>(responseString);
        return catalog;
    }
}
```

Le client typé ( `CatalogService` dans l’exemple) est activé par di (injection de dépendances), ce qui signifie qu’il peut accepter n’importe quel service inscrit dans son constructeur, en plus de `HttpClient` .

Un client typé est effectivement un objet temporaire, ce qui signifie qu’une nouvelle instance est créée chaque fois qu’un est nécessaire. Elle reçoit une nouvelle `HttpClient` instance à chaque fois qu’elle est construite. Toutefois, les `HttpMessageHandler` objets du pool sont les objets réutilisés par plusieurs `HttpClient` instances.

### <a name="use-your-typed-client-classes"></a>Utiliser les classes de client typé

Enfin, une fois que vos classes typées sont implémentées, vous pouvez les enregistrer et les configurer avec `AddHttpClient()` . Après cela, vous pouvez les utiliser partout où des services sont injectés par DI. Par exemple, dans un code de page Razor ou un contrôleur d’une application Web MVC, comme dans le code suivant de eShopOnContainers :

```csharp
namespace Microsoft.eShopOnContainers.WebMVC.Controllers
{
    public class CatalogController : Controller
    {
        private ICatalogService _catalogSvc;

        public CatalogController(ICatalogService catalogSvc) =>
                                                           _catalogSvc = catalogSvc;

        public async Task<IActionResult> Index(int? BrandFilterApplied,
                                               int? TypesFilterApplied,
                                               int? page,
                                               [FromQuery]string errorMsg)
        {
            var itemsPage = 10;
            var catalog = await _catalogSvc.GetCatalogItems(page ?? 0,
                                                            itemsPage,
                                                            BrandFilterApplied,
                                                            TypesFilterApplied);
            //… Additional code
        }

        }
}
```

Jusqu’à présent, l’extrait de code ci-dessus ne montre que l’exemple d’exécution de requêtes HTTP normales. Mais le « Magic » se trouve dans les sections suivantes, où il montre comment toutes les requêtes HTTP effectuées par `HttpClient` , peuvent avoir des stratégies résilientes telles que les nouvelles tentatives avec interruption exponentielle, disjoncteurs, fonctionnalités de sécurité à l’aide de jetons d’authentification, voire d’autres fonctionnalités personnalisées. Toutes ces opérations peuvent être effectuées simplement en ajoutant des stratégies et en déléguant des gestionnaires à vos clients typés inscrits.

## <a name="additional-resources"></a>Ressources supplémentaires

- **Utilisation de HttpClientFactory dans .NET Core**  
  [https://docs.microsoft.com/aspnet/core/fundamentals/http-requests](/aspnet/core/fundamentals/http-requests)

- **Code source HttpClientFactory dans le `dotnet/extensions` référentiel GitHub**  
  <https://github.com/dotnet/extensions/tree/v3.1.8/src/HttpClientFactory>

- **Polly (Résilience .NET et bibliothèque de gestion des erreurs temporaires)**  
  <http://www.thepollyproject.org/>
  
- **Utilisation de IHttpClientFactory sans injection de dépendance (problème GitHub)**  
  <https://github.com/dotnet/extensions/issues/1345>

>[!div class="step-by-step"]
>[Précédent](implement-resilient-entity-framework-core-sql-connections.md) 
> [Suivant](implement-http-call-retries-exponential-backoff-polly.md)
