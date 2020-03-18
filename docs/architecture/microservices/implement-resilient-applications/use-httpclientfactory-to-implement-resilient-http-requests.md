---
title: Utilisez IHttpClientFactory pour mettre en œuvre des demandes HTTP résilientes
description: Apprenez à utiliser IHttpClientFactory, disponible depuis .NET Core 2.1, pour créer des `HttpClient` instances, ce qui vous facilite l’utilisation dans vos applications.
ms.date: 03/03/2020
ms.openlocfilehash: 088fb6c7e10ad656247ee4065da5c13d383b2cf7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78847217"
---
# <a name="use-ihttpclientfactory-to-implement-resilient-http-requests"></a>Utilisez IHttpClientFactory pour mettre en œuvre des demandes HTTP résilientes

<xref:System.Net.Http.IHttpClientFactory>est un contrat `DefaultHttpClientFactory`mis en œuvre par , une usine d’opinion, disponible depuis .NET Core 2.1, pour créer des <xref:System.Net.Http.HttpClient> instances à utiliser dans vos applications.

## <a name="issues-with-the-original-httpclient-class-available-in-net-core"></a>Problèmes liés à la classe HttpClient d’origine disponible dans .NET Core

La classe originale <xref:System.Net.Http.HttpClient> et bien connue peut être facilement utilisée, mais dans certains cas, elle n’est pas correctement utilisée par de nombreux développeurs.

Bien que cette `IDisposable`classe implémente, le `using` déclarant et l’instantané dans une déclaration n’est pas préférable parce que lorsque l’objet `HttpClient` est éliminé, la prise sous-jacente n’est pas immédiatement libérée, ce qui peut conduire à un problème _d’épuisement de prise._ Pour plus d’informations sur ce problème, voir le blog [que vous utilisez HttpClient mal et il est déstabilisant votre logiciel](https://aspnetmonsters.com/2016/08/2016-08-27-httpclientwrong/).

Par conséquent, `HttpClient` est destiné à être instancié une seule fois et réutilisé tout au long de la durée de vie d’une application. L’instanciation d’une classe `HttpClient` pour chaque demande épuise le nombre de sockets disponibles sous des charges élevées. Ce problème entraîne des erreurs `SocketException`. Les approches possibles pour résoudre ce problème sont basées sur la création de l’objet `HttpClient` singleton ou statique, comme expliqué dans cet [article Microsoft sur l’utilisation de HttpClient](../../../csharp/tutorials/console-webapiclient.md). Cela peut être une bonne solution pour les applications de console de courte durée ou similaires qui sont exécutés quelques fois par jour.

Un autre problème que les développeurs se `HttpClient` heurtent est lors de l’utilisation d’un exemple partagé de processus en cours d’exécution. Dans une situation où le HttpClient est instantané comme un singleton ou un objet statique, il ne parvient pas à gérer les changements DNS comme décrit dans ce [numéro](https://github.com/dotnet/corefx/issues/11224) du référentiel pointnet/corefx GitHub.

`HttpClient` Cependant, la question n’est pas vraiment avec en soi, mais avec le constructeur par défaut pour [HttpClient](https://docs.microsoft.com/dotnet/api/system.net.http.httpclient.-ctor?view=netcore-3.1#System_Net_Http_HttpClient__ctor), parce qu’il crée une nouvelle instance concrète de <xref:System.Net.Http.HttpMessageHandler>, qui est celui qui a des prises *d’épuisement* et DNS change les questions mentionnées ci-dessus.

Pour résoudre les problèmes mentionnés ci-dessus et pour rendre `HttpClient` les <xref:System.Net.Http.IHttpClientFactory> instances gérables, .NET `HttpClient` Core 2.1 a introduit l’interface qui peut être utilisée pour configurer et créer des instances dans une application via Dependency Injection (DI). Il fournit également des extensions pour Polly-basé middleware pour profiter de la délégation des gestionnaires dans HttpClient.

[Polly](http://www.thepollyproject.org/) est une bibliothèque de manutention de défauts transitoires qui aide les développeurs à ajouter de la résilience à leurs applications, en utilisant certaines stratégies prédéfinises d’une manière fluide et sans fil.

## <a name="benefits-of-using-ihttpclientfactory"></a>Avantages de l’utilisation d’IHttpClientFactory

La mise <xref:System.Net.Http.IHttpClientFactory>en œuvre <xref:System.Net.Http.IHttpMessageHandlerFactory>actuelle de , qui met également en œuvre , offre les avantages suivants:

- Fournit un emplacement central pour nommer `HttpClient` et configurer des objets logiques. Par exemple, vous pouvez configurer un client (Service Agent) qui est préconfiguré pour accéder à un microservice spécifique.
- Codifier le concept de middleware sortant en `HttpClient` déléguant les gestionnaires et en mettant en œuvre des moyens intermédiaires basés sur Polly pour tirer parti des politiques de Polly en matière de résilience.
- `HttpClient` intègre déjà le concept de délégation des gestionnaires qui pourraient être liés ensemble pour les requêtes HTTP sortantes. Vous pouvez enregistrer des clients HTTP dans l’usine et vous pouvez utiliser un gestionnaire Polly pour utiliser les politiques Polly pour Retry, CircuitBreakers, et ainsi de suite.
- Gérez la <xref:System.Net.Http.HttpMessageHandler> durée de vie pour éviter les `HttpClient` problèmes ou les problèmes mentionnés qui peuvent se produire lors de la gestion des vies vous-même.

> [!TIP]
> Les `HttpClient` cas injectés par DI, peuvent être éliminés en toute sécurité, parce que l’associé `HttpMessageHandler` est géré par l’usine. En fait, les `HttpClient` cas injectés sont *scoped* d’un point de vue DI.

> [!NOTE]
> La mise `IHttpClientFactory` `DefaultHttpClientFactory`en œuvre de ( `Microsoft.Extensions.DependencyInjection` ) est étroitement liée à la mise en œuvre DE DI dans le paquet NuGet. Pour plus d’informations sur l’utilisation d’autres conteneurs DI, voir cette [discussion GitHub](https://github.com/dotnet/extensions/issues/1345).

## <a name="multiple-ways-to-use-ihttpclientfactory"></a>Plusieurs façons d’utiliser IHttpClientFactory

Il existe diverses façons d’utiliser `IHttpClientFactory` dans votre application :

- Utilisation de base
- Utiliser des clients nommés
- Utiliser des clients typés
- Utiliser des clients générés

Par souci de brièveté, cette orientation montre `IHttpClientFactory`la façon la plus structurée d’utiliser, qui est d’utiliser des clients typés (modèle d’agent de service). Cependant, toutes les options sont documentées et sont actuellement répertoriées dans cet [article couvrant `IHttpClientFactory` l’utilisation](/aspnet/core/fundamentals/http-requests#consumption-patterns).

## <a name="how-to-use-typed-clients-with-ihttpclientfactory"></a>Comment utiliser les clients typés avec IHttpClientFactory

Mais qu’est-ce donc qu’un « client typé » ? C’est juste `HttpClient` un qui est pré-configuré pour une utilisation spécifique. Cette configuration peut inclure des valeurs spécifiques telles que le serveur de base, les en-têtes HTTP ou les temps d’arrêt.

Le diagramme suivant montre comment les clients typés sont utilisés avec `IHttpClientFactory` :

![Diagramme montrant comment les clients typés sont utilisés avec IHttpClientFactory.](./media/use-httpclientfactory-to-implement-resilient-http-requests/client-application-code.png)

**Figure 8-4**. Utilisation `IHttpClientFactory` avec des classes de clients typés.

Dans l’image `ClientService` ci-dessus, un (utilisé par `HttpClient` un contrôleur `IHttpClientFactory`ou un code client) utilise un créé par l’enregistrement . Cette usine assigne un d’une `HttpMessageHandler` piscine à la `HttpClient`. Le `HttpClient` peut être configuré avec les stratégies `IHttpClientFactory` de Polly lors <xref:Microsoft.Extensions.DependencyInjection.HttpClientFactoryServiceCollectionExtensions.AddHttpClient*>de l’enregistrement du conteneur DI avec la méthode d’extension .

Pour configurer la <xref:System.Net.Http.IHttpClientFactory> structure ci-dessus, `Microsoft.Extensions.Http` ajoutez votre application <xref:Microsoft.Extensions.DependencyInjection.HttpClientFactoryServiceCollectionExtensions.AddHttpClient*> en installant le paquet NuGet qui inclut la méthode d’extension pour <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection>. Cette méthode d’extension `DefaultHttpClientFactory` enregistre la classe interne à `IHttpClientFactory`utiliser comme un singleton pour l’interface . Elle définit une configuration temporaire pour <xref:Microsoft.Extensions.Http.HttpMessageHandlerBuilder>. Ce gestionnaire de messages (objet <xref:System.Net.Http.HttpMessageHandler>), obtenu à partir d’un pool, est utilisé par le `HttpClient` retourné à partir de la fabrique.

Dans le code suivant, vous pouvez voir comment utiliser `AddHttpClient()` pour enregistrer les clients typés (agents de service) qui ont besoin d’utiliser `HttpClient`.

```csharp
// Startup.cs
//Add http client services at ConfigureServices(IServiceCollection services)
services.AddHttpClient<ICatalogService, CatalogService>();
services.AddHttpClient<IBasketService, BasketService>();
services.AddHttpClient<IOrderingService, OrderingService>();
```

L’enregistrement des services à la clientèle `DefaultClientFactory` tel qu’indiqué dans le code précédent, fait de la création une norme `HttpClient` pour chaque service.

Vous pouvez également ajouter une configuration spécifique à l’instance dans l’enregistrement, par exemple, configurer l’adresse de base et ajouter des stratégies de résilience, comme indiqué dans le code suivant :

```csharp
services.AddHttpClient<ICatalogService, CatalogService>(client =>
{
    client.BaseAddress = new Uri(Configuration["BaseUrl"]);
})
    .AddPolicyHandler(GetRetryPolicy())
    .AddPolicyHandler(GetCircuitBreakerPolicy());
```

Juste pour l’exemple, vous pouvez voir l’une des stratégies ci-dessus dans le code suivant:

```csharp
static IAsyncPolicy<HttpResponseMessage> GetRetryPolicy()
{
    return HttpPolicyExtensions
        .HandleTransientHttpError()
        .OrResult(msg => msg.StatusCode == System.Net.HttpStatusCode.NotFound)
        .WaitAndRetryAsync(6, retryAttempt => TimeSpan.FromSeconds(Math.Pow(2, retryAttempt)));
}
```

Vous pouvez trouver plus de détails sur l’utilisation de Polly dans [l’article suivant](implement-http-call-retries-exponential-backoff-polly.md).

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

Comme étape précédente, vous devez avoir vos classes de clients typés définies, telles que les classes dans le code de l’échantillon, comme «BasketService», `HttpClient` «CatalogService», «OrderingService», etc - Un client typé est une classe qui accepte un objet (injecté par son constructeur) et l’utilise pour appeler un service HTTP à distance. Par exemple :

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

Le client typé (dans`CatalogService` l’exemple) est activé par DI (Dependency Injection), ce qui `HttpClient`signifie qu’il peut accepter tout service enregistré dans son constructeur, en plus de .

Un client typé est en effet un objet temporaire, ce qui signifie qu’une nouvelle instance est créée dès qu’elle est requise, et qu’il reçoit une nouvelle instance `HttpClient` chaque fois qu’il est construit. Cependant, `HttpMessageHandler` les objets dans la piscine sont les `HttpClient` objets qui sont réutilisés par plusieurs cas.

### <a name="use-your-typed-client-classes"></a>Utiliser les classes de client typé

Enfin, une fois que vos classes dactylographie sont mises en œuvre et les ont enregistrées et configurées avec, `AddHttpClient()`vous pouvez les utiliser partout où vous pouvez avoir des services injectés par DI. Par exemple, dans un code de page Razor ou un contrôleur d’une application web MVC, comme dans le code suivant d’eShopOnContainers :

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

Jusqu’à présent, le code montré est juste effectuer des demandes régulières Http, mais la «magie» vient dans les sections suivantes où, juste `HttpClient` en ajoutant des politiques et en déléguant les gestionnaires à vos clients personnalisés Typé, toutes les demandes HTTP à faire par se comporter en tenant compte des politiques résilientes telles que les retries avec backoff exponentiel, disjoncteurs, ou tout autre gestionnaire de délégation personnalisée pour implémenter des fonctionnalités de sécurité supplémentaires, comme l’utilisation de jetons auth, ou toute autre fonctionnalité personnalisée.

## <a name="additional-resources"></a>Ressources supplémentaires

- **Utilisation de HttpClientFactory dans .NET Core**  
  [https://docs.microsoft.com/aspnet/core/fundamentals/http-requests](/aspnet/core/fundamentals/http-requests)

- **Code source httpClientFactory `dotnet/extensions` dans le référentiel GitHub**  
  <https://github.com/dotnet/extensions/tree/master/src/HttpClientFactory>

- **Polly (Résilience .NET et bibliothèque de gestion des erreurs temporaires)**  
  <http://www.thepollyproject.org/>
  
- **Utilisation d’IHttpClientFactory sans injection de dépendance (problème GitHub)**  
  <https://github.com/dotnet/extensions/issues/1345>

>[!div class="step-by-step"]
>[Suivant précédent](implement-resilient-entity-framework-core-sql-connections.md)
>[Next](implement-http-call-retries-exponential-backoff-polly.md)
