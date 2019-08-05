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
# <a name="use-httpclientfactory-to-implement-resilient-http-requests"></a><span data-ttu-id="2b020-103">Utiliser HttpClientFactory pour implémenter des requêtes HTTP résilientes</span><span class="sxs-lookup"><span data-stu-id="2b020-103">Use HttpClientFactory to implement resilient HTTP requests</span></span>

<span data-ttu-id="2b020-104">`HttpClientFactory` est une fabrique rigide, disponible depuis .NET Core 2.1, qui permet la création d’instances <xref:System.Net.Http.HttpClient> à utiliser dans vos applications.</span><span class="sxs-lookup"><span data-stu-id="2b020-104">`HttpClientFactory` is an opinionated factory, available since .NET Core 2.1, for creating <xref:System.Net.Http.HttpClient> instances to be used in your applications.</span></span>

## <a name="issues-with-the-original-httpclient-class-available-in-net-core"></a><span data-ttu-id="2b020-105">Problèmes liés à la classe HttpClient d’origine disponible dans .NET Core</span><span class="sxs-lookup"><span data-stu-id="2b020-105">Issues with the original HttpClient class available in .NET Core</span></span>

<span data-ttu-id="2b020-106">La classe [HttpClient](/dotnet/api/system.net.http.httpclient?view=netstandard-2.0) bien connue peut être facilement utilisée, mais il arrive parfois qu’elle ne soit pas correctement utilisée par de nombreux développeurs.</span><span class="sxs-lookup"><span data-stu-id="2b020-106">The original and well-known [HttpClient](/dotnet/api/system.net.http.httpclient?view=netstandard-2.0) class can be easily used, but in some cases, it isn't being properly used by many developers.</span></span> 

<span data-ttu-id="2b020-107">Le premier problème, quand cette classe peut être supprimée, tient au fait que l’utiliser avec l’instruction `using` n’est pas le choix le plus judicieux, car même lorsque vous supprimez l’objet `HttpClient`, le socket sous-jacent n’est pas libéré immédiatement et peut entraîner un problème grave nommé « épuisement de sockets ».</span><span class="sxs-lookup"><span data-stu-id="2b020-107">As a first issue, while this class is disposable, using it with the `using` statement is not the best choice because even when you dispose `HttpClient` object, the underlying socket is not immediately released and can cause a serious issue named ‘sockets exhaustion’.</span></span> <span data-ttu-id="2b020-108">Pour plus d’informations sur ce problème, consultez le billet de blog [You’re using HttpClient wrong and it is destabilizing your software](https://aspnetmonsters.com/2016/08/2016-08-27-httpclientwrong/).</span><span class="sxs-lookup"><span data-stu-id="2b020-108">For more information about this issue, see [You're using HttpClient wrong and it's destabilizing your software](https://aspnetmonsters.com/2016/08/2016-08-27-httpclientwrong/) blog post.</span></span>

<span data-ttu-id="2b020-109">Par conséquent, `HttpClient` est destiné à être instancié une seule fois et réutilisé tout au long de la durée de vie d’une application.</span><span class="sxs-lookup"><span data-stu-id="2b020-109">Therefore, `HttpClient` is intended to be instantiated once and reused throughout the life of an application.</span></span> <span data-ttu-id="2b020-110">L’instanciation d’une classe `HttpClient` pour chaque demande épuise le nombre de sockets disponibles sous des charges élevées.</span><span class="sxs-lookup"><span data-stu-id="2b020-110">Instantiating an `HttpClient` class for every request will exhaust the number of sockets available under heavy loads.</span></span> <span data-ttu-id="2b020-111">Ce problème entraîne des erreurs `SocketException`.</span><span class="sxs-lookup"><span data-stu-id="2b020-111">That issue will result in `SocketException` errors.</span></span> <span data-ttu-id="2b020-112">Les approches possibles pour résoudre ce problème sont basées sur la création de l’objet `HttpClient` singleton ou statique, comme expliqué dans cet [article Microsoft sur l’utilisation de HttpClient](/dotnet/csharp/tutorials/console-webapiclient).</span><span class="sxs-lookup"><span data-stu-id="2b020-112">Possible approaches to solve that problem are based on the creation of the `HttpClient` object as singleton or static, as explained in this [Microsoft article on HttpClient usage](/dotnet/csharp/tutorials/console-webapiclient).</span></span> 

<span data-ttu-id="2b020-113">Toutefois, il existe un deuxième problème avec `HttpClient`, qui peut se poser lorsque vous l’utilisez en tant qu’objet singleton ou statique.</span><span class="sxs-lookup"><span data-stu-id="2b020-113">But there’s a second issue with `HttpClient` that you can have when you use it as singleton or static object.</span></span> <span data-ttu-id="2b020-114">Dans ce cas, un objet `HttpClient` singleton ou statique ne respecte pas les modifications DNS, comme expliqué dans ce [problème lié au dépôt GitHub de .NET Core](https://github.com/dotnet/corefx/issues/11224).</span><span class="sxs-lookup"><span data-stu-id="2b020-114">In this case, a singleton or static `HttpClient` doesn't respect DNS changes, as explained in this [issue at the .NET Core GitHub repo](https://github.com/dotnet/corefx/issues/11224).</span></span> 

<span data-ttu-id="2b020-115">Pour résoudre les problèmes précités et faciliter la gestion des instances `HttpClient`, .NET Core 2.1 introduit un nouveau `HttpClientFactory` qui peut également être utilisé pour implémenter des appels HTTP résilients en y intégrant Polly.</span><span class="sxs-lookup"><span data-stu-id="2b020-115">To address those mentioned issues and make the management of `HttpClient` instances easier, .NET Core 2.1 introduced a new `HttpClientFactory` that can also be used to implement resilient HTTP calls by integrating Polly with it.</span></span>   

## <a name="what-is-httpclientfactory"></a><span data-ttu-id="2b020-116">Qu’est-ce que HttpClientFactory ?</span><span class="sxs-lookup"><span data-stu-id="2b020-116">What is HttpClientFactory</span></span>

<span data-ttu-id="2b020-117">`HttpClientFactory` a été conçu pour :</span><span class="sxs-lookup"><span data-stu-id="2b020-117">`HttpClientFactory` is designed to:</span></span>

- <span data-ttu-id="2b020-118">Offrir un emplacement central pour nommer et configurer les clients HTTP logiques.</span><span class="sxs-lookup"><span data-stu-id="2b020-118">Provide a central location for naming and configuring logical HttpClients.</span></span> <span data-ttu-id="2b020-119">Par exemple, vous pouvez configurer un client (Service Agent) qui est préconfiguré pour accéder à un microservice spécifique.</span><span class="sxs-lookup"><span data-stu-id="2b020-119">For example, you may configure a client (Service Agent) that's pre-configured to access a specific microservice.</span></span>
- <span data-ttu-id="2b020-120">Codifier le concept d’intergiciel (middleware) sortant via la délégation de gestionnaires dans `HttpClient` et l’implémentation d’un middleware basé sur Polly pour tirer parti des stratégies de Polly pour la résilience.</span><span class="sxs-lookup"><span data-stu-id="2b020-120">Codify the concept of outgoing middleware via delegating handlers in `HttpClient` and implementing Polly-based middleware to take advantage of Polly’s policies for resiliency.</span></span>
- <span data-ttu-id="2b020-121">`HttpClient` intègre déjà le concept de délégation des gestionnaires qui pourraient être liés ensemble pour les requêtes HTTP sortantes.</span><span class="sxs-lookup"><span data-stu-id="2b020-121">`HttpClient` already has the concept of delegating handlers that could be linked together for outgoing HTTP requests.</span></span> <span data-ttu-id="2b020-122">Vous enregistrez les clients http dans la fabrique et vous pouvez utiliser un gestionnaire Polly qui permet d’utiliser des stratégies Polly pour des fonctionnalités telles que Retry (nouvelle tentative) ou CircuitBreaker (disjoncteur).</span><span class="sxs-lookup"><span data-stu-id="2b020-122">You register http clients into the factory plus you can use a Polly handler that allows Polly policies to be used for Retry, CircuitBreakers, etc.</span></span>
- <span data-ttu-id="2b020-123">Gérer la durée de vie de HttpClientMessageHandlers afin d’éviter les problèmes mentionnés qui peuvent se produire lorsque vous gérez vous-même les durées de vie de `HttpClient`.</span><span class="sxs-lookup"><span data-stu-id="2b020-123">Manage the lifetime of HttpClientMessageHandlers to avoid the mentioned problems/issues that can occur when managing `HttpClient` lifetimes yourself.</span></span> 

## <a name="multiple-ways-to-use-httpclientfactory"></a><span data-ttu-id="2b020-124">Plusieurs façons d’utiliser HttpClientFactory</span><span class="sxs-lookup"><span data-stu-id="2b020-124">Multiple ways to use HttpClientFactory</span></span>

<span data-ttu-id="2b020-125">Il existe diverses façons d’utiliser `HttpClientFactory` dans votre application :</span><span class="sxs-lookup"><span data-stu-id="2b020-125">There are several ways that you can use `HttpClientFactory` in your application:</span></span>

- <span data-ttu-id="2b020-126">Utiliser `HttpClientFactory` directement</span><span class="sxs-lookup"><span data-stu-id="2b020-126">Use `HttpClientFactory` Directly</span></span>
- <span data-ttu-id="2b020-127">Utiliser des clients nommés</span><span class="sxs-lookup"><span data-stu-id="2b020-127">Use Named Clients</span></span>
- <span data-ttu-id="2b020-128">Utiliser des clients typés</span><span class="sxs-lookup"><span data-stu-id="2b020-128">Use Typed Clients</span></span>
- <span data-ttu-id="2b020-129">Utiliser des clients générés</span><span class="sxs-lookup"><span data-stu-id="2b020-129">Use Generated Clients</span></span>

<span data-ttu-id="2b020-130">Pour ne pas être trop long, ce guide illustre la façon la plus structurée d’utiliser `HttpClientFactory`, qui consiste à utiliser les clients typés (modèle de Service Agent), mais toutes les options sont actuellement listées et documentées dans cet [article portant sur l’utilisation de HttpClientFactory ](/aspnet/core/fundamentals/http-requests?#consumption-patterns).</span><span class="sxs-lookup"><span data-stu-id="2b020-130">For the sake of brevity, this guidance shows the most structured way to use `HttpClientFactory` that's to use Typed Clients (Service Agent pattern), but all options are documented and are currently listed in this [article covering HttpClientFactory usage](/aspnet/core/fundamentals/http-requests?#consumption-patterns).</span></span>  

## <a name="how-to-use-typed-clients-with-httpclientfactory"></a><span data-ttu-id="2b020-131">Comment utiliser les clients typés avec HttpClientFactory</span><span class="sxs-lookup"><span data-stu-id="2b020-131">How to use Typed Clients with HttpClientFactory</span></span>

<span data-ttu-id="2b020-132">Mais qu’est-ce donc qu’un « client typé » ?</span><span class="sxs-lookup"><span data-stu-id="2b020-132">So, what's a "Typed Client"?</span></span> <span data-ttu-id="2b020-133">Il s’agit tout simplement d’un `HttpClient` configuré lors de l’injection par le `DefaultHttpClientFactory`.</span><span class="sxs-lookup"><span data-stu-id="2b020-133">It's just an `HttpClient` that's configured upon injection by the `DefaultHttpClientFactory`.</span></span>

<span data-ttu-id="2b020-134">Le diagramme suivant montre comment les clients typés sont utilisés avec `HttpClientFactory` :</span><span class="sxs-lookup"><span data-stu-id="2b020-134">The following diagram shows how Typed Clients are used with `HttpClientFactory`:</span></span>

![Un ClientService (utilisé par un code client ou contrôleur) utilise un HttpClient créé par le IHttpClientFactory inscrit.](./media/image3.5.png)

<span data-ttu-id="2b020-138">**Figure 8-4**.</span><span class="sxs-lookup"><span data-stu-id="2b020-138">**Figure 8-4**.</span></span> <span data-ttu-id="2b020-139">Utilisation de HttpClientFactory avec des classes de client typé.</span><span class="sxs-lookup"><span data-stu-id="2b020-139">Using HttpClientFactory with Typed Client classes.</span></span>

<span data-ttu-id="2b020-140">Tout d’abord, configurez `HttpClientFactory` dans votre application, ajoutez une référence au package `Microsoft.Extensions.Http` qui inclut la méthode d’extension `AddHttpClient()` pour `IServiceCollection`.</span><span class="sxs-lookup"><span data-stu-id="2b020-140">First, setup `HttpClientFactory` in your application, adding a reference to the `Microsoft.Extensions.Http` package that includes the `AddHttpClient()` extension method for `IServiceCollection`.</span></span> <span data-ttu-id="2b020-141">Cette méthode d’extension enregistre le `DefaultHttpClientFactory` à utiliser comme singleton pour l’interface `IHttpClientFactory`.</span><span class="sxs-lookup"><span data-stu-id="2b020-141">This extension method registers the `DefaultHttpClientFactory` to be used as a singleton for the interface `IHttpClientFactory`.</span></span> <span data-ttu-id="2b020-142">Elle définit une configuration temporaire pour `HttpMessageHandlerBuilder`.</span><span class="sxs-lookup"><span data-stu-id="2b020-142">It defines a transient configuration for the `HttpMessageHandlerBuilder`.</span></span> <span data-ttu-id="2b020-143">Ce gestionnaire de messages (objet `HttpMessageHandler`), obtenu à partir d’un pool, est utilisé par le `HttpClient` retourné à partir de la fabrique.</span><span class="sxs-lookup"><span data-stu-id="2b020-143">This message handler (`HttpMessageHandler` object), taken from a pool, is used by the `HttpClient` returned from the factory.</span></span>

<span data-ttu-id="2b020-144">Dans le code suivant, vous pouvez voir comment utiliser `AddHttpClient()` pour enregistrer les clients typés (agents de service) qui ont besoin d’utiliser `HttpClient`.</span><span class="sxs-lookup"><span data-stu-id="2b020-144">In the next code, you can see how `AddHttpClient()` can be used to register Typed Clients (Service Agents) that need to use `HttpClient`.</span></span>

```csharp
// Startup.cs
//Add http client services at ConfigureServices(IServiceCollection services) 
services.AddHttpClient<ICatalogService, CatalogService>();
services.AddHttpClient<IBasketService, BasketService>();
services.AddHttpClient<IOrderingService, OrderingService>();
```

<span data-ttu-id="2b020-145">L’inscription des services client comme indiqué dans le code précédent fait en sorte que `DefaultClientFactory` crée un `HttpClient` configuré spécialement pour chaque service, comme nous l’expliquerons dans le paragraphe suivant.</span><span class="sxs-lookup"><span data-stu-id="2b020-145">Registering the client services as shown in the previous code, makes the `DefaultClientFactory` create an `HttpClient` configured specifically for each service, as we'll explain in the next paragraph.</span></span>

<span data-ttu-id="2b020-146">Avec la simple inscription de votre classe de service client avec `AddHttpClient()`, l’objet `HttpClient` qui est injecté dans votre classe utilise la configuration et les stratégies fournies lors de l’inscription.</span><span class="sxs-lookup"><span data-stu-id="2b020-146">Just by registering your client service class with `AddHttpClient()`, the `HttpClient` object that will be injected into your class will use the configuration and policies provided upon registration.</span></span> <span data-ttu-id="2b020-147">Dans les sections suivantes, vous verrez ces stratégies, telles que les nouvelles tentatives et les disjoncteurs de Polly.</span><span class="sxs-lookup"><span data-stu-id="2b020-147">In the next sections, you'll see those policies like Polly’s retries or circuit-breakers.</span></span>

### <a name="httpclient-lifetimes"></a><span data-ttu-id="2b020-148">Durées de vie de HttpClient</span><span class="sxs-lookup"><span data-stu-id="2b020-148">HttpClient lifetimes</span></span>

<span data-ttu-id="2b020-149">Chaque fois que vous obtenez un objet `HttpClient` à partir de `IHttpClientFactory`, une nouvelle instance est retournée.</span><span class="sxs-lookup"><span data-stu-id="2b020-149">Each time you get an `HttpClient` object from the `IHttpClientFactory`, a new instance is returned.</span></span> <span data-ttu-id="2b020-150">Mais chaque `HttpClient` utilise un `HttpMessageHandler` qui est mis en pool et réutilisé par `IHttpClientFactory` pour réduire la consommation de ressources, tant que la durée de vie du `HttpMessageHandler` n’a pas expiré.</span><span class="sxs-lookup"><span data-stu-id="2b020-150">But each `HttpClient` uses an `HttpMessageHandler` that's pooled and reused by the `IHttpClientFactory` to reduce resource consumption, as long as the `HttpMessageHandler`'s lifetime hasn't expired.</span></span>

<span data-ttu-id="2b020-151">Le regroupement de gestionnaires est souhaitable, car chaque gestionnaire gère généralement ses propres connexions HTTP sous-jacentes : créer plus de gestionnaires que nécessaire peut entraîner des délais dans la connexion.</span><span class="sxs-lookup"><span data-stu-id="2b020-151">Pooling of handlers is desirable as each handler typically manages its own underlying HTTP connections; creating more handlers than necessary can result in connection delays.</span></span> <span data-ttu-id="2b020-152">Certains gestionnaires conservent aussi les connexions indéfiniment ouvertes, ce qui peut empêcher le gestionnaire de réagir aux changements du DNS.</span><span class="sxs-lookup"><span data-stu-id="2b020-152">Some handlers also keep connections open indefinitely, which can prevent the handler from reacting to DNS changes.</span></span>

<span data-ttu-id="2b020-153">Les objets `HttpMessageHandler` du pool ont une durée de vie qui correspond à la durée pendant laquelle une instance `HttpMessageHandler` du pool peut être réutilisée.</span><span class="sxs-lookup"><span data-stu-id="2b020-153">The `HttpMessageHandler` objects in the pool have a lifetime that's the length of time that an `HttpMessageHandler` instance in the pool can be reused.</span></span> <span data-ttu-id="2b020-154">La valeur par défaut est de deux minutes, mais elle peut être remplacée pour chaque client typé.</span><span class="sxs-lookup"><span data-stu-id="2b020-154">The default value is two minutes, but it can be overridden per Typed Client.</span></span> <span data-ttu-id="2b020-155">Pour la remplacer, appelez `SetHandlerLifetime()` sur le `IHttpClientBuilder` qui est retourné lors de la création du client, comme indiqué dans le code suivant :</span><span class="sxs-lookup"><span data-stu-id="2b020-155">To override it, call `SetHandlerLifetime()` on the `IHttpClientBuilder` that's returned when creating the client, as shown in the following code:</span></span>

```csharp
//Set 5 min as the lifetime for the HttpMessageHandler objects in the pool used for the Catalog Typed Client 
services.AddHttpClient<ICatalogService, CatalogService>()
                 .SetHandlerLifetime(TimeSpan.FromMinutes(5));  
```

<span data-ttu-id="2b020-156">Chaque client typé peut avoir sa propre valeur de durée de vie de gestionnaire configurée.</span><span class="sxs-lookup"><span data-stu-id="2b020-156">Each Typed Client can have its own configured handler lifetime value.</span></span> <span data-ttu-id="2b020-157">Définissez la durée de vie sur `InfiniteTimeSpan` pour désactiver l’expiration du gestionnaire.</span><span class="sxs-lookup"><span data-stu-id="2b020-157">Set the lifetime to `InfiniteTimeSpan` to disable handler expiry.</span></span>

### <a name="implement-your-typed-client-classes-that-use-the-injected-and-configured-httpclient"></a><span data-ttu-id="2b020-158">Implémenter les classes de client typé qui utilisent l’objet HttpClient injecté et configuré</span><span class="sxs-lookup"><span data-stu-id="2b020-158">Implement your Typed Client classes that use the injected and configured HttpClient</span></span>

<span data-ttu-id="2b020-159">Comme étape préliminaire, vous devez avoir défini vos classes de client typé, telles que les classes dans l’exemple de code, comme « BasketService », « CatalogService », « OrderingService », etc. Un client typé est une classe qui accepte un objet `HttpClient` (injecté par le biais de son constructeur) et l’utilise pour appeler un service HTTP distant.</span><span class="sxs-lookup"><span data-stu-id="2b020-159">As a previous step, you need to have your Typed Client classes defined, such as the classes in the sample code, like ‘BasketService’, ‘CatalogService’, ‘OrderingService’, etc. – A Typed Client is a class that accepts an `HttpClient` object (injected through its constructor) and uses it to call some remote HTTP service.</span></span> <span data-ttu-id="2b020-160">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="2b020-160">For example:</span></span>

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

<span data-ttu-id="2b020-161">Le client typé (CatalogService dans cet exemple) est activé par l’injection de dépendances, ce qui signifie qu’il peut accepter n’importe quel service enregistré dans son constructeur, en plus de HttpClient.</span><span class="sxs-lookup"><span data-stu-id="2b020-161">The Typed Client (CatalogService in the example) is activated by DI (Dependency Injection), meaning that it can accept any registered service in its constructor, in addition to HttpClient.</span></span>

<span data-ttu-id="2b020-162">Un client typé est en effet un objet temporaire, ce qui signifie qu’une nouvelle instance est créée dès qu’elle est requise, et qu’il reçoit une nouvelle instance `HttpClient` chaque fois qu’il est construit.</span><span class="sxs-lookup"><span data-stu-id="2b020-162">A Typed Client is, effectively, a transient object, meaning that a new instance is created each time one is needed and it will receive a new `HttpClient` instance each time it's constructed.</span></span> <span data-ttu-id="2b020-163">Toutefois, les objets HttpMessageHandler figurant dans le pool sont les objets qui sont réutilisés par plusieurs requêtes Http.</span><span class="sxs-lookup"><span data-stu-id="2b020-163">However, the HttpMessageHandler objects in the pool are the objects that are reused by multiple Http requests.</span></span>

### <a name="use-your-typed-client-classes"></a><span data-ttu-id="2b020-164">Utiliser les classes de client typé</span><span class="sxs-lookup"><span data-stu-id="2b020-164">Use your Typed Client classes</span></span>

<span data-ttu-id="2b020-165">Enfin, après avoir implémenté vos classes de type et les avoir enregistrées avec AddHttpClient(), vous pouvez les utiliser partout où vous pouvez avoir des services injectés par injection de dépendances, par exemple dans n’importe quel code de page Razor ou n’importe quel contrôleur d’une application web MVC, comme dans le code suivant à partir d’eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="2b020-165">Finally, once you have your type classes implemented and have them registered with AddHttpClient(), you can use it anywhere you can have services injected by DI, for example in any Razor page code or any controller of an MVC web app, like in the following code from eShopOnContainers.</span></span>

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

<span data-ttu-id="2b020-166">Jusqu’à ce stade, le code indiqué effectue simplement des requêtes Http normales, mais la « magie » apparaît dans les sections suivantes où, en ajoutant simplement des stratégies et en délégant des gestionnaires pour vos clients typés inscrits, toutes les requêtes HTTP que `HttpClient` doit exécuter prennent en compte des stratégies résilientes telles que de nouvelles tentatives avec interruption exponentielle, des disjoncteurs ou n’importe quel autre gestionnaire de délégation personnalisé pour implémenter des fonctionnalités de sécurité supplémentaires, telles que l’utilisation de jetons d’authentification ou toute autre fonctionnalité personnalisée.</span><span class="sxs-lookup"><span data-stu-id="2b020-166">Up to this point, the code shown is just performing regular Http requests, but the ‘magic’ comes in the following sections where, just by adding policies and delegating handlers to your registered Typed Clients, all the HTTP requests to be done by `HttpClient` will behave taking into account resilient policies such as retries with exponential backoff, circuit breakers, or any other custom delegating handler to implement additional security features, like using auth tokens, or any other custom feature.</span></span> 

## <a name="additional-resources"></a><span data-ttu-id="2b020-167">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="2b020-167">Additional resources</span></span>

- <span data-ttu-id="2b020-168">**Utilisation de HttpClientFactory dans .NET Core**</span><span class="sxs-lookup"><span data-stu-id="2b020-168">**Using HttpClientFactory in .NET Core**</span></span>\
  [https://docs.microsoft.com/aspnet/core/fundamentals/http-requests?view=aspnetcore-2.1](/aspnet/core/fundamentals/http-requests?view=aspnetcore-2.1)

- <span data-ttu-id="2b020-169">**Dépôt GitHub de HttpClientFactory**</span><span class="sxs-lookup"><span data-stu-id="2b020-169">**HttpClientFactory GitHub repo**</span></span>\
  <https://github.com/aspnet/Extensions/tree/master/src/HttpClientFactory>

>[!div class="step-by-step"]
><span data-ttu-id="2b020-170">[Précédent](explore-custom-http-call-retries-exponential-backoff.md)
>[Suivant](implement-http-call-retries-exponential-backoff-polly.md)</span><span class="sxs-lookup"><span data-stu-id="2b020-170">[Previous](explore-custom-http-call-retries-exponential-backoff.md)
[Next](implement-http-call-retries-exponential-backoff-polly.md)</span></span>
