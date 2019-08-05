---
title: Utiliser HttpClientFactory pour implémenter des requêtes HTTP résilientes
description: Découvrez comment utiliser HttpClientFactory, disponible à partir de .NET Core 2.1, pour créer des instances `HttpClient`, ce qui facilite son utilisation dans vos applications.
ms.date: 01/07/2019
ms.openlocfilehash: 68c841a6ba69a94eff420233124cf00fec506502
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68674476"
---
# <a name="use-httpclientfactory-to-implement-resilient-http-requests"></a>Utiliser HttpClientFactory pour implémenter des requêtes HTTP résilientes

`HttpClientFactory` est une fabrique rigide, disponible depuis .NET Core 2.1, qui permet la création d’instances <xref:System.Net.Http.HttpClient> à utiliser dans vos applications.

## <a name="issues-with-the-original-httpclient-class-available-in-net-core"></a>Problèmes liés à la classe HttpClient d’origine disponible dans .NET Core

La classe [HttpClient](/dotnet/api/system.net.http.httpclient?view=netstandard-2.0) bien connue peut être facilement utilisée, mais il arrive parfois qu’elle ne soit pas correctement utilisée par de nombreux développeurs. 

Le premier problème, quand cette classe peut être supprimée, tient au fait que l’utiliser avec l’instruction `using` n’est pas le choix le plus judicieux, car même lorsque vous supprimez l’objet `HttpClient`, le socket sous-jacent n’est pas libéré immédiatement et peut entraîner un problème grave nommé « épuisement de sockets ». Pour plus d’informations sur ce problème, consultez le billet de blog [You’re using HttpClient wrong and it is destabilizing your software](https://aspnetmonsters.com/2016/08/2016-08-27-httpclientwrong/).

Par conséquent, `HttpClient` est destiné à être instancié une seule fois et réutilisé tout au long de la durée de vie d’une application. L’instanciation d’une classe `HttpClient` pour chaque demande épuise le nombre de sockets disponibles sous des charges élevées. Ce problème entraîne des erreurs `SocketException`. Les approches possibles pour résoudre ce problème sont basées sur la création de l’objet `HttpClient` singleton ou statique, comme expliqué dans cet [article Microsoft sur l’utilisation de HttpClient](/dotnet/csharp/tutorials/console-webapiclient). 

Toutefois, il existe un deuxième problème avec `HttpClient`, qui peut se poser lorsque vous l’utilisez en tant qu’objet singleton ou statique. Dans ce cas, un objet `HttpClient` singleton ou statique ne respecte pas les modifications DNS, comme expliqué dans ce [problème lié au dépôt GitHub de .NET Core](https://github.com/dotnet/corefx/issues/11224). 

Pour résoudre les problèmes précités et faciliter la gestion des instances `HttpClient`, .NET Core 2.1 introduit un nouveau `HttpClientFactory` qui peut également être utilisé pour implémenter des appels HTTP résilients en y intégrant Polly.   

## <a name="what-is-httpclientfactory"></a>Qu’est-ce que HttpClientFactory ?

`HttpClientFactory` a été conçu pour :

- Offrir un emplacement central pour nommer et configurer les clients HTTP logiques. Par exemple, vous pouvez configurer un client (Service Agent) qui est préconfiguré pour accéder à un microservice spécifique.
- Codifier le concept d’intergiciel (middleware) sortant via la délégation de gestionnaires dans `HttpClient` et l’implémentation d’un middleware basé sur Polly pour tirer parti des stratégies de Polly pour la résilience.
- `HttpClient` intègre déjà le concept de délégation des gestionnaires qui pourraient être liés ensemble pour les requêtes HTTP sortantes. Vous enregistrez les clients http dans la fabrique et vous pouvez utiliser un gestionnaire Polly qui permet d’utiliser des stratégies Polly pour des fonctionnalités telles que Retry (nouvelle tentative) ou CircuitBreaker (disjoncteur).
- Gérer la durée de vie de HttpClientMessageHandlers afin d’éviter les problèmes mentionnés qui peuvent se produire lorsque vous gérez vous-même les durées de vie de `HttpClient`. 

## <a name="multiple-ways-to-use-httpclientfactory"></a>Plusieurs façons d’utiliser HttpClientFactory

Il existe diverses façons d’utiliser `HttpClientFactory` dans votre application :

- Utiliser `HttpClientFactory` directement
- Utiliser des clients nommés
- Utiliser des clients typés
- Utiliser des clients générés

Pour ne pas être trop long, ce guide illustre la façon la plus structurée d’utiliser `HttpClientFactory`, qui consiste à utiliser les clients typés (modèle de Service Agent), mais toutes les options sont actuellement listées et documentées dans cet [article portant sur l’utilisation de HttpClientFactory ](/aspnet/core/fundamentals/http-requests?#consumption-patterns).  

## <a name="how-to-use-typed-clients-with-httpclientfactory"></a>Comment utiliser les clients typés avec HttpClientFactory

Mais qu’est-ce donc qu’un « client typé » ? Il s’agit tout simplement d’un `HttpClient` configuré lors de l’injection par le `DefaultHttpClientFactory`.

Le diagramme suivant montre comment les clients typés sont utilisés avec `HttpClientFactory` :

![Un ClientService (utilisé par un code client ou contrôleur) utilise un HttpClient créé par le IHttpClientFactory inscrit. Cette fabrique assigne au HttpClient un HttpMessageHandler à partir d’un pool qu’elle gère. Le HttpClient peut être configuré avec les stratégies de Polly lors de l’inscription du IHttpClientFactory dans le conteneur d’injection de dépendances avec la méthode d’extension AddHttpClient.](./media/image3.5.png)

**Figure 8-4**. Utilisation de HttpClientFactory avec des classes de client typé.

Tout d’abord, configurez `HttpClientFactory` dans votre application, ajoutez une référence au package `Microsoft.Extensions.Http` qui inclut la méthode d’extension `AddHttpClient()` pour `IServiceCollection`. Cette méthode d’extension enregistre le `DefaultHttpClientFactory` à utiliser comme singleton pour l’interface `IHttpClientFactory`. Elle définit une configuration temporaire pour `HttpMessageHandlerBuilder`. Ce gestionnaire de messages (objet `HttpMessageHandler`), obtenu à partir d’un pool, est utilisé par le `HttpClient` retourné à partir de la fabrique.

Dans le code suivant, vous pouvez voir comment utiliser `AddHttpClient()` pour enregistrer les clients typés (agents de service) qui ont besoin d’utiliser `HttpClient`.

```csharp
// Startup.cs
//Add http client services at ConfigureServices(IServiceCollection services) 
services.AddHttpClient<ICatalogService, CatalogService>();
services.AddHttpClient<IBasketService, BasketService>();
services.AddHttpClient<IOrderingService, OrderingService>();
```

L’inscription des services client comme indiqué dans le code précédent fait en sorte que `DefaultClientFactory` crée un `HttpClient` configuré spécialement pour chaque service, comme nous l’expliquerons dans le paragraphe suivant.

Avec la simple inscription de votre classe de service client avec `AddHttpClient()`, l’objet `HttpClient` qui est injecté dans votre classe utilise la configuration et les stratégies fournies lors de l’inscription. Dans les sections suivantes, vous verrez ces stratégies, telles que les nouvelles tentatives et les disjoncteurs de Polly.

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

Comme étape préliminaire, vous devez avoir défini vos classes de client typé, telles que les classes dans l’exemple de code, comme « BasketService », « CatalogService », « OrderingService », etc. Un client typé est une classe qui accepte un objet `HttpClient` (injecté par le biais de son constructeur) et l’utilise pour appeler un service HTTP distant. Par exemple :

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

Enfin, après avoir implémenté vos classes de type et les avoir enregistrées avec AddHttpClient(), vous pouvez les utiliser partout où vous pouvez avoir des services injectés par injection de dépendances, par exemple dans n’importe quel code de page Razor ou n’importe quel contrôleur d’une application web MVC, comme dans le code suivant à partir d’eShopOnContainers.

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

- **Utilisation de HttpClientFactory dans .NET Core**\
  [https://docs.microsoft.com/aspnet/core/fundamentals/http-requests?view=aspnetcore-2.1](/aspnet/core/fundamentals/http-requests?view=aspnetcore-2.1)

- **Dépôt GitHub de HttpClientFactory**\
  <https://github.com/aspnet/Extensions/tree/master/src/HttpClientFactory>

>[!div class="step-by-step"]
>[Précédent](explore-custom-http-call-retries-exponential-backoff.md)
>[Suivant](implement-http-call-retries-exponential-backoff-polly.md)
