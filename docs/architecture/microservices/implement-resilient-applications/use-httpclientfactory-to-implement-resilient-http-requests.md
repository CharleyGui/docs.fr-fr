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
# <a name="use-httpclientfactory-to-implement-resilient-http-requests"></a><span data-ttu-id="093cc-103">Utiliser HttpClientFactory pour implémenter des requêtes HTTP résilientes</span><span class="sxs-lookup"><span data-stu-id="093cc-103">Use HttpClientFactory to implement resilient HTTP requests</span></span>

<span data-ttu-id="093cc-104">`HttpClientFactory` est une fabrique rigide, disponible depuis .NET Core 2.1, qui permet la création d’instances <xref:System.Net.Http.HttpClient> à utiliser dans vos applications.</span><span class="sxs-lookup"><span data-stu-id="093cc-104">`HttpClientFactory` is an opinionated factory, available since .NET Core 2.1, for creating <xref:System.Net.Http.HttpClient> instances to be used in your applications.</span></span>

## <a name="issues-with-the-original-httpclient-class-available-in-net-core"></a><span data-ttu-id="093cc-105">Problèmes liés à la classe HttpClient d’origine disponible dans .NET Core</span><span class="sxs-lookup"><span data-stu-id="093cc-105">Issues with the original HttpClient class available in .NET Core</span></span>

<span data-ttu-id="093cc-106">La classe d' <xref:System.Net.Http.HttpClient> d’origine et bien connue peut être facilement utilisée, mais dans certains cas, elle n’est pas utilisée correctement par de nombreux développeurs.</span><span class="sxs-lookup"><span data-stu-id="093cc-106">The original and well-known <xref:System.Net.Http.HttpClient> class can be easily used, but in some cases, it isn't being properly used by many developers.</span></span>

<span data-ttu-id="093cc-107">Le premier problème, quand cette classe peut être supprimée, tient au fait que l’utiliser avec l’instruction `using` n’est pas le choix le plus judicieux, car même lorsque vous supprimez l’objet `HttpClient`, le socket sous-jacent n’est pas libéré immédiatement et peut entraîner un problème grave nommé « épuisement de sockets ».</span><span class="sxs-lookup"><span data-stu-id="093cc-107">As a first issue, while this class is disposable, using it with the `using` statement is not the best choice because even when you dispose `HttpClient` object, the underlying socket is not immediately released and can cause a serious issue named ‘sockets exhaustion’.</span></span> <span data-ttu-id="093cc-108">Pour plus d’informations sur ce problème, consultez le billet de blog [You’re using HttpClient wrong and it is destabilizing your software](https://aspnetmonsters.com/2016/08/2016-08-27-httpclientwrong/).</span><span class="sxs-lookup"><span data-stu-id="093cc-108">For more information about this issue, see [You're using HttpClient wrong and it's destabilizing your software](https://aspnetmonsters.com/2016/08/2016-08-27-httpclientwrong/) blog post.</span></span>

<span data-ttu-id="093cc-109">Par conséquent, `HttpClient` est destiné à être instancié une seule fois et réutilisé tout au long de la durée de vie d’une application.</span><span class="sxs-lookup"><span data-stu-id="093cc-109">Therefore, `HttpClient` is intended to be instantiated once and reused throughout the life of an application.</span></span> <span data-ttu-id="093cc-110">L’instanciation d’une classe `HttpClient` pour chaque demande épuise le nombre de sockets disponibles sous des charges élevées.</span><span class="sxs-lookup"><span data-stu-id="093cc-110">Instantiating an `HttpClient` class for every request will exhaust the number of sockets available under heavy loads.</span></span> <span data-ttu-id="093cc-111">Ce problème entraîne des erreurs `SocketException`.</span><span class="sxs-lookup"><span data-stu-id="093cc-111">That issue will result in `SocketException` errors.</span></span> <span data-ttu-id="093cc-112">Les approches possibles pour résoudre ce problème sont basées sur la création de l’objet `HttpClient` singleton ou statique, comme expliqué dans cet [article Microsoft sur l’utilisation de HttpClient](../../../csharp/tutorials/console-webapiclient.md).</span><span class="sxs-lookup"><span data-stu-id="093cc-112">Possible approaches to solve that problem are based on the creation of the `HttpClient` object as singleton or static, as explained in this [Microsoft article on HttpClient usage](../../../csharp/tutorials/console-webapiclient.md).</span></span>

<span data-ttu-id="093cc-113">Toutefois, il existe un deuxième problème avec `HttpClient`, qui peut se poser lorsque vous l’utilisez en tant qu’objet singleton ou statique.</span><span class="sxs-lookup"><span data-stu-id="093cc-113">But there’s a second issue with `HttpClient` that you can have when you use it as singleton or static object.</span></span> <span data-ttu-id="093cc-114">Dans ce cas, un singleton ou un `HttpClient` statique ne respecte pas les modifications DNS, comme expliqué dans ce [numéro](https://github.com/dotnet/corefx/issues/11224) dans le référentiel GitHub dotnet/corefx.</span><span class="sxs-lookup"><span data-stu-id="093cc-114">In this case, a singleton or static `HttpClient` doesn't respect DNS changes, as explained in this [issue](https://github.com/dotnet/corefx/issues/11224) at the dotnet/corefx GitHub repository.</span></span>

<span data-ttu-id="093cc-115">Pour résoudre les problèmes précités et faciliter la gestion des instances `HttpClient`, .NET Core 2.1 introduit un nouveau `HttpClientFactory` qui peut également être utilisé pour implémenter des appels HTTP résilients en y intégrant Polly.</span><span class="sxs-lookup"><span data-stu-id="093cc-115">To address those mentioned issues and make the management of `HttpClient` instances easier, .NET Core 2.1 introduced a new `HttpClientFactory` that can also be used to implement resilient HTTP calls by integrating Polly with it.</span></span>

<span data-ttu-id="093cc-116">[Polly](http://www.thepollyproject.org/) est une bibliothèque de gestion des erreurs temporaires qui permet aux développeurs d’ajouter de la résilience à leurs applications à l’aide de stratégies prédéfinies de façon Fluent et thread-safe.</span><span class="sxs-lookup"><span data-stu-id="093cc-116">[Polly](http://www.thepollyproject.org/) is transient-fault-handling library that helps developers add resiliency to their applications, by using some pre-defined policies in a fluent and thread-safe manner.</span></span>

## <a name="what-is-httpclientfactory"></a><span data-ttu-id="093cc-117">Qu’est-ce que HttpClientFactory ?</span><span class="sxs-lookup"><span data-stu-id="093cc-117">What is HttpClientFactory</span></span>

<span data-ttu-id="093cc-118">`HttpClientFactory` a été conçu pour :</span><span class="sxs-lookup"><span data-stu-id="093cc-118">`HttpClientFactory` is designed to:</span></span>

- <span data-ttu-id="093cc-119">Fournir un emplacement central pour nommer et configurer des objets de `HttpClient` logiques.</span><span class="sxs-lookup"><span data-stu-id="093cc-119">Provide a central location for naming and configuring logical `HttpClient` objects.</span></span> <span data-ttu-id="093cc-120">Par exemple, vous pouvez configurer un client (Service Agent) qui est préconfiguré pour accéder à un microservice spécifique.</span><span class="sxs-lookup"><span data-stu-id="093cc-120">For example, you may configure a client (Service Agent) that's pre-configured to access a specific microservice.</span></span>
- <span data-ttu-id="093cc-121">Codifier le concept d’intergiciel (middleware) sortant via la délégation de gestionnaires dans `HttpClient` et l’implémentation d’un middleware basé sur Polly pour tirer parti des stratégies de Polly pour la résilience.</span><span class="sxs-lookup"><span data-stu-id="093cc-121">Codify the concept of outgoing middleware via delegating handlers in `HttpClient` and implementing Polly-based middleware to take advantage of Polly’s policies for resiliency.</span></span>
- <span data-ttu-id="093cc-122">`HttpClient` intègre déjà le concept de délégation des gestionnaires qui pourraient être liés ensemble pour les requêtes HTTP sortantes.</span><span class="sxs-lookup"><span data-stu-id="093cc-122">`HttpClient` already has the concept of delegating handlers that could be linked together for outgoing HTTP requests.</span></span> <span data-ttu-id="093cc-123">Vous enregistrez des clients HTTP dans la fabrique et vous pouvez utiliser un gestionnaire Polly pour utiliser des stratégies Polly pour les nouvelles tentatives, CircuitBreakers, etc.</span><span class="sxs-lookup"><span data-stu-id="093cc-123">You register HTTP clients into the factory and you can use a Polly handler to use Polly policies for Retry, CircuitBreakers, and so on.</span></span>
- <span data-ttu-id="093cc-124">Gérez la durée de vie des `HttpClientMessageHandlers` pour éviter les problèmes/problèmes mentionnés qui peuvent se produire lors de la gestion des durées de vie des `HttpClient`.</span><span class="sxs-lookup"><span data-stu-id="093cc-124">Manage the lifetime of `HttpClientMessageHandlers` to avoid the mentioned problems/issues that can occur when managing `HttpClient` lifetimes yourself.</span></span>

> [!NOTE]
> <span data-ttu-id="093cc-125">`HttpClientFactory` est étroitement lié à l’implémentation de l’injection de dépendances dans le package NuGet `Microsoft.Extensions.DependencyInjection`.</span><span class="sxs-lookup"><span data-stu-id="093cc-125">`HttpClientFactory` is tightly tied to the dependency injection (DI) implementation in the `Microsoft.Extensions.DependencyInjection` NuGet package.</span></span> <span data-ttu-id="093cc-126">Pour plus d’informations sur l’utilisation d’autres conteneurs d’injection de dépendances, consultez cette [discussion GitHub](https://github.com/dotnet/extensions/issues/1345).</span><span class="sxs-lookup"><span data-stu-id="093cc-126">For more information about using other dependency injection containers, see this [GitHub discussion](https://github.com/dotnet/extensions/issues/1345).</span></span>

## <a name="multiple-ways-to-use-httpclientfactory"></a><span data-ttu-id="093cc-127">Plusieurs façons d’utiliser HttpClientFactory</span><span class="sxs-lookup"><span data-stu-id="093cc-127">Multiple ways to use HttpClientFactory</span></span>

<span data-ttu-id="093cc-128">Il existe diverses façons d’utiliser `HttpClientFactory` dans votre application :</span><span class="sxs-lookup"><span data-stu-id="093cc-128">There are several ways that you can use `HttpClientFactory` in your application:</span></span>

- <span data-ttu-id="093cc-129">Utiliser `HttpClientFactory` directement</span><span class="sxs-lookup"><span data-stu-id="093cc-129">Use `HttpClientFactory` Directly</span></span>
- <span data-ttu-id="093cc-130">Utiliser des clients nommés</span><span class="sxs-lookup"><span data-stu-id="093cc-130">Use Named Clients</span></span>
- <span data-ttu-id="093cc-131">Utiliser des clients typés</span><span class="sxs-lookup"><span data-stu-id="093cc-131">Use Typed Clients</span></span>
- <span data-ttu-id="093cc-132">Utiliser des clients générés</span><span class="sxs-lookup"><span data-stu-id="093cc-132">Use Generated Clients</span></span>

<span data-ttu-id="093cc-133">Par souci de concision, ce guide présente la manière la plus structurée d’utiliser `HttpClientFactory`, qui consiste à utiliser des clients typés (modèle d’agent de service).</span><span class="sxs-lookup"><span data-stu-id="093cc-133">For the sake of brevity, this guidance shows the most structured way to use `HttpClientFactory`, which is to use Typed Clients (Service Agent pattern).</span></span> <span data-ttu-id="093cc-134">Toutefois, toutes les options sont documentées et sont actuellement répertoriées dans cet [article concernant l’utilisation de HttpClientFactory](/aspnet/core/fundamentals/http-requests#consumption-patterns).</span><span class="sxs-lookup"><span data-stu-id="093cc-134">However, all options are documented and are currently listed in this [article covering HttpClientFactory usage](/aspnet/core/fundamentals/http-requests#consumption-patterns).</span></span>

## <a name="how-to-use-typed-clients-with-httpclientfactory"></a><span data-ttu-id="093cc-135">Comment utiliser les clients typés avec HttpClientFactory</span><span class="sxs-lookup"><span data-stu-id="093cc-135">How to use Typed Clients with HttpClientFactory</span></span>

<span data-ttu-id="093cc-136">Mais qu’est-ce donc qu’un « client typé » ?</span><span class="sxs-lookup"><span data-stu-id="093cc-136">So, what's a "Typed Client"?</span></span> <span data-ttu-id="093cc-137">Il s’agit tout simplement d’un `HttpClient` configuré lors de l’injection par le `DefaultHttpClientFactory`.</span><span class="sxs-lookup"><span data-stu-id="093cc-137">It's just an `HttpClient` that's configured upon injection by the `DefaultHttpClientFactory`.</span></span>

<span data-ttu-id="093cc-138">Le diagramme suivant montre comment les clients typés sont utilisés avec `HttpClientFactory` :</span><span class="sxs-lookup"><span data-stu-id="093cc-138">The following diagram shows how Typed Clients are used with `HttpClientFactory`:</span></span>

![Diagramme montrant comment les clients typés sont utilisés avec HttpClientFactory.](./media/use-httpclientfactory-to-implement-resilient-http-requests/client-application-code.png)

<span data-ttu-id="093cc-140">**Figure 8-4**.</span><span class="sxs-lookup"><span data-stu-id="093cc-140">**Figure 8-4**.</span></span> <span data-ttu-id="093cc-141">Utilisation de HttpClientFactory avec des classes de client typé.</span><span class="sxs-lookup"><span data-stu-id="093cc-141">Using HttpClientFactory with Typed Client classes.</span></span>

<span data-ttu-id="093cc-142">Dans l’image ci-dessus, un ClientService (utilisé par un contrôleur ou un code client) utilise un `HttpClient` créé par le `IHttpClientFactory`inscrit.</span><span class="sxs-lookup"><span data-stu-id="093cc-142">In the above image, a ClientService (used by a controller or client code) uses an `HttpClient` created by the registered `IHttpClientFactory`.</span></span> <span data-ttu-id="093cc-143">Cette fabrique affecte le `HttpClient` un `HttpMessageHandler` à partir d’un pool qu’il gère.</span><span class="sxs-lookup"><span data-stu-id="093cc-143">This factory assigns the `HttpClient` an `HttpMessageHandler` from a pool it manages.</span></span> <span data-ttu-id="093cc-144">La `HttpClient` peut être configurée avec les stratégies de Polly lors de l’inscription de l' `IHttpClientFactory` dans le conteneur DI avec la méthode d’extension `AddHttpClient`.</span><span class="sxs-lookup"><span data-stu-id="093cc-144">The `HttpClient` can be configured with Polly's policies when registering the `IHttpClientFactory` in the DI container with the extension method `AddHttpClient`.</span></span>

<span data-ttu-id="093cc-145">Pour configurer la structure ci-dessus, ajoutez `HttpClientFactory` dans votre application en installant le package NuGet `Microsoft.Extensions.Http` qui comprend la méthode d’extension `AddHttpClient()` pour `IServiceCollection`.</span><span class="sxs-lookup"><span data-stu-id="093cc-145">To configure the above structure, add `HttpClientFactory` in your application by installing the `Microsoft.Extensions.Http` NuGet package that includes the `AddHttpClient()` extension method for `IServiceCollection`.</span></span> <span data-ttu-id="093cc-146">Cette méthode d’extension enregistre le `DefaultHttpClientFactory` à utiliser comme singleton pour l’interface `IHttpClientFactory`.</span><span class="sxs-lookup"><span data-stu-id="093cc-146">This extension method registers the `DefaultHttpClientFactory` to be used as a singleton for the interface `IHttpClientFactory`.</span></span> <span data-ttu-id="093cc-147">Elle définit une configuration temporaire pour `HttpMessageHandlerBuilder`.</span><span class="sxs-lookup"><span data-stu-id="093cc-147">It defines a transient configuration for the `HttpMessageHandlerBuilder`.</span></span> <span data-ttu-id="093cc-148">Ce gestionnaire de messages (objet `HttpMessageHandler`), obtenu à partir d’un pool, est utilisé par le `HttpClient` retourné à partir de la fabrique.</span><span class="sxs-lookup"><span data-stu-id="093cc-148">This message handler (`HttpMessageHandler` object), taken from a pool, is used by the `HttpClient` returned from the factory.</span></span>

<span data-ttu-id="093cc-149">Dans le code suivant, vous pouvez voir comment utiliser `AddHttpClient()` pour enregistrer les clients typés (agents de service) qui ont besoin d’utiliser `HttpClient`.</span><span class="sxs-lookup"><span data-stu-id="093cc-149">In the next code, you can see how `AddHttpClient()` can be used to register Typed Clients (Service Agents) that need to use `HttpClient`.</span></span>

```csharp
// Startup.cs
//Add http client services at ConfigureServices(IServiceCollection services)
services.AddHttpClient<ICatalogService, CatalogService>();
services.AddHttpClient<IBasketService, BasketService>();
services.AddHttpClient<IOrderingService, OrderingService>();
```

<span data-ttu-id="093cc-150">L’inscription des services du client comme indiqué dans le code précédent, rend l' `DefaultClientFactory` créer un `HttpClient` standard pour chaque service.</span><span class="sxs-lookup"><span data-stu-id="093cc-150">Registering the client services as shown in the previous code, makes the `DefaultClientFactory` create a standard `HttpClient` for each service.</span></span>

<span data-ttu-id="093cc-151">Vous pouvez également ajouter une configuration spécifique à l’instance dans l’inscription à, par exemple, configurer l’adresse de base et ajouter des stratégies de résilience, comme illustré dans le code suivant :</span><span class="sxs-lookup"><span data-stu-id="093cc-151">You could also add instance-specific configuration in the registration to, for example, configure the base address, and add some resiliency policies, as shown in the following code:</span></span>

```csharp
services.AddHttpClient<ICatalogService, CatalogService>(client =>
{
    client.BaseAddress = new Uri(Configuration["BaseUrl"]);
})
    .AddPolicyHandler(GetRetryPolicy())
    .AddPolicyHandler(GetCircuitBreakerPolicy());
```

<span data-ttu-id="093cc-152">Pour les besoins de l’exemple, vous pouvez voir l’une des stratégies ci-dessus dans le code suivant :</span><span class="sxs-lookup"><span data-stu-id="093cc-152">Just for the example sake, you can see one of the above policies in the next code:</span></span>

```csharp
static IAsyncPolicy<HttpResponseMessage> GetRetryPolicy()
{
    return HttpPolicyExtensions
        .HandleTransientHttpError()
        .OrResult(msg => msg.StatusCode == System.Net.HttpStatusCode.NotFound)
        .WaitAndRetryAsync(6, retryAttempt => TimeSpan.FromSeconds(Math.Pow(2, retryAttempt)));
}
```

<span data-ttu-id="093cc-153">Vous trouverez plus d’informations sur l’utilisation de Polly dans l' [article suivant](implement-http-call-retries-exponential-backoff-polly.md).</span><span class="sxs-lookup"><span data-stu-id="093cc-153">You can find more details about using Polly in the [Next article](implement-http-call-retries-exponential-backoff-polly.md).</span></span>

### <a name="httpclient-lifetimes"></a><span data-ttu-id="093cc-154">Durées de vie de HttpClient</span><span class="sxs-lookup"><span data-stu-id="093cc-154">HttpClient lifetimes</span></span>

<span data-ttu-id="093cc-155">Chaque fois que vous obtenez un objet `HttpClient` à partir de `IHttpClientFactory`, une nouvelle instance est retournée.</span><span class="sxs-lookup"><span data-stu-id="093cc-155">Each time you get an `HttpClient` object from the `IHttpClientFactory`, a new instance is returned.</span></span> <span data-ttu-id="093cc-156">Mais chaque `HttpClient` utilise un `HttpMessageHandler` qui est mis en pool et réutilisé par `IHttpClientFactory` pour réduire la consommation de ressources, tant que la durée de vie du `HttpMessageHandler` n’a pas expiré.</span><span class="sxs-lookup"><span data-stu-id="093cc-156">But each `HttpClient` uses an `HttpMessageHandler` that's pooled and reused by the `IHttpClientFactory` to reduce resource consumption, as long as the `HttpMessageHandler`'s lifetime hasn't expired.</span></span>

<span data-ttu-id="093cc-157">Le regroupement de gestionnaires est souhaitable, car chaque gestionnaire gère généralement ses propres connexions HTTP sous-jacentes : créer plus de gestionnaires que nécessaire peut entraîner des délais dans la connexion.</span><span class="sxs-lookup"><span data-stu-id="093cc-157">Pooling of handlers is desirable as each handler typically manages its own underlying HTTP connections; creating more handlers than necessary can result in connection delays.</span></span> <span data-ttu-id="093cc-158">Certains gestionnaires conservent aussi les connexions indéfiniment ouvertes, ce qui peut empêcher le gestionnaire de réagir aux changements du DNS.</span><span class="sxs-lookup"><span data-stu-id="093cc-158">Some handlers also keep connections open indefinitely, which can prevent the handler from reacting to DNS changes.</span></span>

<span data-ttu-id="093cc-159">Les objets `HttpMessageHandler` du pool ont une durée de vie qui correspond à la durée pendant laquelle une instance `HttpMessageHandler` du pool peut être réutilisée.</span><span class="sxs-lookup"><span data-stu-id="093cc-159">The `HttpMessageHandler` objects in the pool have a lifetime that's the length of time that an `HttpMessageHandler` instance in the pool can be reused.</span></span> <span data-ttu-id="093cc-160">La valeur par défaut est de deux minutes, mais elle peut être remplacée pour chaque client typé.</span><span class="sxs-lookup"><span data-stu-id="093cc-160">The default value is two minutes, but it can be overridden per Typed Client.</span></span> <span data-ttu-id="093cc-161">Pour la remplacer, appelez `SetHandlerLifetime()` sur le `IHttpClientBuilder` qui est retourné lors de la création du client, comme indiqué dans le code suivant :</span><span class="sxs-lookup"><span data-stu-id="093cc-161">To override it, call `SetHandlerLifetime()` on the `IHttpClientBuilder` that's returned when creating the client, as shown in the following code:</span></span>

```csharp
//Set 5 min as the lifetime for the HttpMessageHandler objects in the pool used for the Catalog Typed Client
services.AddHttpClient<ICatalogService, CatalogService>()
    .SetHandlerLifetime(TimeSpan.FromMinutes(5));
```

<span data-ttu-id="093cc-162">Chaque client typé peut avoir sa propre valeur de durée de vie de gestionnaire configurée.</span><span class="sxs-lookup"><span data-stu-id="093cc-162">Each Typed Client can have its own configured handler lifetime value.</span></span> <span data-ttu-id="093cc-163">Définissez la durée de vie sur `InfiniteTimeSpan` pour désactiver l’expiration du gestionnaire.</span><span class="sxs-lookup"><span data-stu-id="093cc-163">Set the lifetime to `InfiniteTimeSpan` to disable handler expiry.</span></span>

### <a name="implement-your-typed-client-classes-that-use-the-injected-and-configured-httpclient"></a><span data-ttu-id="093cc-164">Implémenter les classes de client typé qui utilisent l’objet HttpClient injecté et configuré</span><span class="sxs-lookup"><span data-stu-id="093cc-164">Implement your Typed Client classes that use the injected and configured HttpClient</span></span>

<span data-ttu-id="093cc-165">Comme étape préliminaire, vous devez avoir défini vos classes de client typé, telles que les classes dans l’exemple de code, comme « BasketService », « CatalogService », « OrderingService », etc. Un client typé est une classe qui accepte un objet `HttpClient` (injecté par le biais de son constructeur) et l’utilise pour appeler un service HTTP distant.</span><span class="sxs-lookup"><span data-stu-id="093cc-165">As a previous step, you need to have your Typed Client classes defined, such as the classes in the sample code, like ‘BasketService’, ‘CatalogService’, ‘OrderingService’, etc. – A Typed Client is a class that accepts an `HttpClient` object (injected through its constructor) and uses it to call some remote HTTP service.</span></span> <span data-ttu-id="093cc-166">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="093cc-166">For example:</span></span>

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

<span data-ttu-id="093cc-167">Le client typé (CatalogService dans cet exemple) est activé par l’injection de dépendances, ce qui signifie qu’il peut accepter n’importe quel service enregistré dans son constructeur, en plus de HttpClient.</span><span class="sxs-lookup"><span data-stu-id="093cc-167">The Typed Client (CatalogService in the example) is activated by DI (Dependency Injection), meaning that it can accept any registered service in its constructor, in addition to HttpClient.</span></span>

<span data-ttu-id="093cc-168">Un client typé est en effet un objet temporaire, ce qui signifie qu’une nouvelle instance est créée dès qu’elle est requise, et qu’il reçoit une nouvelle instance `HttpClient` chaque fois qu’il est construit.</span><span class="sxs-lookup"><span data-stu-id="093cc-168">A Typed Client is, effectively, a transient object, meaning that a new instance is created each time one is needed and it will receive a new `HttpClient` instance each time it's constructed.</span></span> <span data-ttu-id="093cc-169">Toutefois, les objets HttpMessageHandler figurant dans le pool sont les objets qui sont réutilisés par plusieurs requêtes Http.</span><span class="sxs-lookup"><span data-stu-id="093cc-169">However, the HttpMessageHandler objects in the pool are the objects that are reused by multiple Http requests.</span></span>

### <a name="use-your-typed-client-classes"></a><span data-ttu-id="093cc-170">Utiliser les classes de client typé</span><span class="sxs-lookup"><span data-stu-id="093cc-170">Use your Typed Client classes</span></span>

<span data-ttu-id="093cc-171">Enfin, une fois que vos classes typées sont implémentées et que vous les avez enregistrées avec `AddHttpClient()`, vous pouvez les utiliser partout où vous pouvez avoir des services injectés par DI.</span><span class="sxs-lookup"><span data-stu-id="093cc-171">Finally, once you have your typed classes implemented and have them registered with `AddHttpClient()`, you can use them wherever you can have services injected by DI.</span></span> <span data-ttu-id="093cc-172">Par exemple, dans un code de page Razor ou un contrôleur d’une application Web MVC, comme dans le code suivant de eShopOnContainers :</span><span class="sxs-lookup"><span data-stu-id="093cc-172">For example, in a Razor page code or controller of an MVC web app, like in the following code from eShopOnContainers:</span></span>

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

<span data-ttu-id="093cc-173">Jusqu’à ce stade, le code indiqué effectue simplement des requêtes Http normales, mais la « magie » apparaît dans les sections suivantes où, en ajoutant simplement des stratégies et en délégant des gestionnaires pour vos clients typés inscrits, toutes les requêtes HTTP que `HttpClient` doit exécuter prennent en compte des stratégies résilientes telles que de nouvelles tentatives avec interruption exponentielle, des disjoncteurs ou n’importe quel autre gestionnaire de délégation personnalisé pour implémenter des fonctionnalités de sécurité supplémentaires, telles que l’utilisation de jetons d’authentification ou toute autre fonctionnalité personnalisée.</span><span class="sxs-lookup"><span data-stu-id="093cc-173">Up to this point, the code shown is just performing regular Http requests, but the ‘magic’ comes in the following sections where, just by adding policies and delegating handlers to your registered Typed Clients, all the HTTP requests to be done by `HttpClient` will behave taking into account resilient policies such as retries with exponential backoff, circuit breakers, or any other custom delegating handler to implement additional security features, like using auth tokens, or any other custom feature.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="093cc-174">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="093cc-174">Additional resources</span></span>

- <span data-ttu-id="093cc-175">**Utilisation de HttpClientFactory dans .NET Core**</span><span class="sxs-lookup"><span data-stu-id="093cc-175">**Using HttpClientFactory in .NET Core**</span></span>  
  [https://docs.microsoft.com/aspnet/core/fundamentals/http-requests](/aspnet/core/fundamentals/http-requests)

- <span data-ttu-id="093cc-176">**Code source HttpClientFactory dans le référentiel GitHub `dotnet/extensions`**</span><span class="sxs-lookup"><span data-stu-id="093cc-176">**HttpClientFactory source code in the `dotnet/extensions` GitHub repository**</span></span>  
  <https://github.com/dotnet/extensions/tree/master/src/HttpClientFactory>

- <span data-ttu-id="093cc-177">**Polly (Résilience .NET et bibliothèque de gestion des erreurs temporaires)**</span><span class="sxs-lookup"><span data-stu-id="093cc-177">**Polly (.NET resilience and transient-fault-handling library)**</span></span>  
  <http://www.thepollyproject.org/>
  
- <span data-ttu-id="093cc-178">**Utilisation de HttpClientFactory sans injection de dépendance (problème GitHub)**</span><span class="sxs-lookup"><span data-stu-id="093cc-178">**Using HttpClientFactory without dependency injection (GitHub issue)**</span></span>  
  <https://github.com/dotnet/extensions/issues/1345>

>[!div class="step-by-step"]
><span data-ttu-id="093cc-179">[Précédent](implement-resilient-entity-framework-core-sql-connections.md)
>[Suivant](implement-http-call-retries-exponential-backoff-polly.md)</span><span class="sxs-lookup"><span data-stu-id="093cc-179">[Previous](implement-resilient-entity-framework-core-sql-connections.md)
[Next](implement-http-call-retries-exponential-backoff-polly.md)</span></span>
