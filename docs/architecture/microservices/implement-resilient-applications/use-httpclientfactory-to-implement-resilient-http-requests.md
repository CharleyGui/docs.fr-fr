---
title: Utiliser HttpClientFactory pour implémenter des requêtes HTTP résilientes
description: Découvrez comment utiliser HttpClientFactory, disponible à partir de .NET Core 2.1, pour créer des instances `HttpClient`, ce qui facilite son utilisation dans vos applications.
ms.date: 08/08/2019
ms.openlocfilehash: 7028a23a8945802d7ec0129b70b2840d03acfba1
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/03/2020
ms.locfileid: "78241050"
---
# <a name="use-httpclientfactory-to-implement-resilient-http-requests"></a>Utiliser HttpClientFactory pour implémenter des requêtes HTTP résilientes

`HttpClientFactory` est une fabrique rigide, disponible depuis .NET Core 2.1, qui permet la création d’instances <xref:System.Net.Http.HttpClient> à utiliser dans vos applications.

## <a name="issues-with-the-original-httpclient-class-available-in-net-core"></a>Problèmes liés à la classe HttpClient d’origine disponible dans .NET Core

La classe d' <xref:System.Net.Http.HttpClient> d’origine et bien connue peut être facilement utilisée, mais dans certains cas, elle n’est pas utilisée correctement par de nombreux développeurs.

Le premier problème, quand cette classe peut être supprimée, tient au fait que l’utiliser avec l’instruction `using` n’est pas le choix le plus judicieux, car même lorsque vous supprimez l’objet `HttpClient`, le socket sous-jacent n’est pas libéré immédiatement et peut entraîner un problème grave nommé « épuisement de sockets ». Pour plus d’informations sur ce problème, consultez le billet de blog [You’re using HttpClient wrong and it is destabilizing your software](https://aspnetmonsters.com/2016/08/2016-08-27-httpclientwrong/).

Par conséquent, `HttpClient` est destiné à être instancié une seule fois et réutilisé tout au long de la durée de vie d’une application. L’instanciation d’une classe `HttpClient` pour chaque demande épuise le nombre de sockets disponibles sous des charges élevées. Ce problème entraîne des erreurs `SocketException`. Les approches possibles pour résoudre ce problème sont basées sur la création de l’objet `HttpClient` singleton ou statique, comme expliqué dans cet [article Microsoft sur l’utilisation de HttpClient](../../../csharp/tutorials/console-webapiclient.md).

Toutefois, il existe un deuxième problème avec `HttpClient`, qui peut se poser lorsque vous l’utilisez en tant qu’objet singleton ou statique. Dans ce cas, un singleton ou un `HttpClient` statique ne respecte pas les modifications DNS, comme expliqué dans ce [numéro](https://github.com/dotnet/corefx/issues/11224) dans le référentiel GitHub dotnet/corefx.

Pour résoudre les problèmes précités et faciliter la gestion des instances `HttpClient`, .NET Core 2.1 introduit un nouveau `HttpClientFactory` qui peut également être utilisé pour implémenter des appels HTTP résilients en y intégrant Polly.

[Polly](http://www.thepollyproject.org/) est une bibliothèque de gestion des erreurs temporaires qui permet aux développeurs d’ajouter de la résilience à leurs applications à l’aide de stratégies prédéfinies de façon Fluent et thread-safe.

## <a name="what-is-httpclientfactory"></a>Qu’est-ce que HttpClientFactory ?

`HttpClientFactory` a été conçu pour :

- Fournir un emplacement central pour nommer et configurer des objets de `HttpClient` logiques. Par exemple, vous pouvez configurer un client (Service Agent) qui est préconfiguré pour accéder à un microservice spécifique.
- Codifier le concept d’intergiciel (middleware) sortant via la délégation de gestionnaires dans `HttpClient` et l’implémentation d’un middleware basé sur Polly pour tirer parti des stratégies de Polly pour la résilience.
- `HttpClient` intègre déjà le concept de délégation des gestionnaires qui pourraient être liés ensemble pour les requêtes HTTP sortantes. Vous enregistrez des clients HTTP dans la fabrique et vous pouvez utiliser un gestionnaire Polly pour utiliser des stratégies Polly pour les nouvelles tentatives, CircuitBreakers, etc.
- Gérez la durée de vie des `HttpClientMessageHandlers` pour éviter les problèmes/problèmes mentionnés qui peuvent se produire lors de la gestion des durées de vie des `HttpClient`.

> [!NOTE]
> `HttpClientFactory` est étroitement lié à l’implémentation de l’injection de dépendances dans le package NuGet `Microsoft.Extensions.DependencyInjection`. Pour plus d’informations sur l’utilisation d’autres conteneurs d’injection de dépendances, consultez cette [discussion GitHub](https://github.com/dotnet/extensions/issues/1345).

## <a name="multiple-ways-to-use-httpclientfactory"></a>Plusieurs façons d’utiliser HttpClientFactory

Il existe diverses façons d’utiliser `HttpClientFactory` dans votre application :

- Utiliser `HttpClientFactory` directement
- Utiliser des clients nommés
- Utiliser des clients typés
- Utiliser des clients générés

Par souci de concision, ce guide présente la manière la plus structurée d’utiliser `HttpClientFactory`, qui consiste à utiliser des clients typés (modèle d’agent de service). Toutefois, toutes les options sont documentées et sont actuellement répertoriées dans cet [article concernant l’utilisation de HttpClientFactory](/aspnet/core/fundamentals/http-requests#consumption-patterns).

## <a name="how-to-use-typed-clients-with-httpclientfactory"></a>Comment utiliser les clients typés avec HttpClientFactory

Mais qu’est-ce donc qu’un « client typé » ? Il s’agit tout simplement d’un `HttpClient` configuré lors de l’injection par le `DefaultHttpClientFactory`.

Le diagramme suivant montre comment les clients typés sont utilisés avec `HttpClientFactory` :

![Diagramme montrant comment les clients typés sont utilisés avec HttpClientFactory.](./media/use-httpclientfactory-to-implement-resilient-http-requests/client-application-code.png)

**Figure 8-4**. Utilisation de HttpClientFactory avec des classes de client typé.

Dans l’image ci-dessus, un ClientService (utilisé par un contrôleur ou un code client) utilise un `HttpClient` créé par le `IHttpClientFactory`inscrit. Cette fabrique affecte le `HttpClient` un `HttpMessageHandler` à partir d’un pool qu’il gère. La `HttpClient` peut être configurée avec les stratégies de Polly lors de l’inscription de l' `IHttpClientFactory` dans le conteneur DI avec la méthode d’extension `AddHttpClient`.

Pour configurer la structure ci-dessus, ajoutez `HttpClientFactory` dans votre application en installant le package NuGet `Microsoft.Extensions.Http` qui comprend la méthode d’extension `AddHttpClient()` pour `IServiceCollection`. Cette méthode d’extension enregistre le `DefaultHttpClientFactory` à utiliser comme singleton pour l’interface `IHttpClientFactory`. Elle définit une configuration temporaire pour `HttpMessageHandlerBuilder`. Ce gestionnaire de messages (objet `HttpMessageHandler`), obtenu à partir d’un pool, est utilisé par le `HttpClient` retourné à partir de la fabrique.

Dans le code suivant, vous pouvez voir comment utiliser `AddHttpClient()` pour enregistrer les clients typés (agents de service) qui ont besoin d’utiliser `HttpClient`.

```csharp
// Startup.cs
//Add http client services at ConfigureServices(IServiceCollection services)
services.AddHttpClient<ICatalogService, CatalogService>();
services.AddHttpClient<IBasketService, BasketService>();
services.AddHttpClient<IOrderingService, OrderingService>();
```

L’inscription des services du client comme indiqué dans le code précédent, rend l' `DefaultClientFactory` créer un `HttpClient` standard pour chaque service.

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

Les objets `HttpMessageHandler` du pool ont une durée de vie qui correspond à la durée pendant laquelle une instance `HttpMessageHandler` du pool peut être réutilisée. La valeur par défaut est de deux minutes, mais elle peut être remplacée pour chaque client typé. Pour la remplacer, appelez `SetHandlerLifetime()` sur le `IHttpClientBuilder` qui est retourné lors de la création du client, comme indiqué dans le code suivant :

```csharp
//Set 5 min as the lifetime for the HttpMessageHandler objects in the pool used for the Catalog Typed Client
services.AddHttpClient<ICatalogService, CatalogService>()
    .SetHandlerLifetime(TimeSpan.FromMinutes(5));
```

Chaque client typé peut avoir sa propre valeur de durée de vie de gestionnaire configurée. Définissez la durée de vie sur `InfiniteTimeSpan` pour désactiver l’expiration du gestionnaire.

### <a name="implement-your-typed-client-classes-that-use-the-injected-and-configured-httpclient"></a>Implémenter les classes de client typé qui utilisent l’objet HttpClient injecté et configuré

Comme étape préliminaire, vous devez avoir défini vos classes de client typé, telles que les classes dans l’exemple de code, comme « BasketService », « CatalogService », « OrderingService », etc. Un client typé est une classe qui accepte un objet `HttpClient` (injecté par le biais de son constructeur) et l’utilise pour appeler un service HTTP distant. Par exemple :

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

Le client typé (CatalogService dans cet exemple) est activé par l’injection de dépendances, ce qui signifie qu’il peut accepter n’importe quel service enregistré dans son constructeur, en plus de HttpClient.

Un client typé est en effet un objet temporaire, ce qui signifie qu’une nouvelle instance est créée dès qu’elle est requise, et qu’il reçoit une nouvelle instance `HttpClient` chaque fois qu’il est construit. Toutefois, les objets HttpMessageHandler figurant dans le pool sont les objets qui sont réutilisés par plusieurs requêtes Http.

### <a name="use-your-typed-client-classes"></a>Utiliser les classes de client typé

Enfin, une fois que vos classes typées sont implémentées et que vous les avez enregistrées avec `AddHttpClient()`, vous pouvez les utiliser partout où vous pouvez avoir des services injectés par DI. Par exemple, dans un code de page Razor ou un contrôleur d’une application Web MVC, comme dans le code suivant de eShopOnContainers :

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

Jusqu’à ce stade, le code indiqué effectue simplement des requêtes Http normales, mais la « magie » apparaît dans les sections suivantes où, en ajoutant simplement des stratégies et en délégant des gestionnaires pour vos clients typés inscrits, toutes les requêtes HTTP que `HttpClient` doit exécuter prennent en compte des stratégies résilientes telles que de nouvelles tentatives avec interruption exponentielle, des disjoncteurs ou n’importe quel autre gestionnaire de délégation personnalisé pour implémenter des fonctionnalités de sécurité supplémentaires, telles que l’utilisation de jetons d’authentification ou toute autre fonctionnalité personnalisée.

## <a name="additional-resources"></a>Ressources supplémentaires

- **Utilisation de HttpClientFactory dans .NET Core**  
  [https://docs.microsoft.com/aspnet/core/fundamentals/http-requests](/aspnet/core/fundamentals/http-requests)

- **Code source HttpClientFactory dans le référentiel GitHub `dotnet/extensions`**  
  <https://github.com/dotnet/extensions/tree/master/src/HttpClientFactory>

- **Polly (Résilience .NET et bibliothèque de gestion des erreurs temporaires)**  
  <http://www.thepollyproject.org/>
  
- **Utilisation de HttpClientFactory sans injection de dépendance (problème GitHub)**  
  <https://github.com/dotnet/extensions/issues/1345>

>[!div class="step-by-step"]
>[Précédent](implement-resilient-entity-framework-core-sql-connections.md)
>[Suivant](implement-http-call-retries-exponential-backoff-polly.md)
