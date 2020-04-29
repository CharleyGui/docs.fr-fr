---
title: Utiliser IHttpClientFactory pour implémenter des requêtes HTTP résilientes
description: Découvrez comment utiliser IHttpClientFactory, disponible depuis .NET Core 2,1, pour la création `HttpClient` d’instances, ce qui vous permet de l’utiliser facilement dans vos applications.
ms.date: 03/03/2020
ms.openlocfilehash: ade26208a931faa456c8e267def2caef7a3f32de
ms.sourcegitcommit: 1cb64b53eb1f253e6a3f53ca9510ef0be1fd06fe
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/29/2020
ms.locfileid: "82507297"
---
# <a name="use-ihttpclientfactory-to-implement-resilient-http-requests"></a><span data-ttu-id="fc81f-103">Utiliser IHttpClientFactory pour implémenter des requêtes HTTP résilientes</span><span class="sxs-lookup"><span data-stu-id="fc81f-103">Use IHttpClientFactory to implement resilient HTTP requests</span></span>

<span data-ttu-id="fc81f-104"><xref:System.Net.Http.IHttpClientFactory>est un contrat implémenté par `DefaultHttpClientFactory`, une fabrique consignes strictes, disponible depuis .net Core 2,1, pour la <xref:System.Net.Http.HttpClient> création d’instances à utiliser dans vos applications.</span><span class="sxs-lookup"><span data-stu-id="fc81f-104"><xref:System.Net.Http.IHttpClientFactory> is a contract implemented by `DefaultHttpClientFactory`, an opinionated factory, available since .NET Core 2.1, for creating <xref:System.Net.Http.HttpClient> instances to be used in your applications.</span></span>

## <a name="issues-with-the-original-httpclient-class-available-in-net-core"></a><span data-ttu-id="fc81f-105">Problèmes liés à la classe HttpClient d’origine disponible dans .NET Core</span><span class="sxs-lookup"><span data-stu-id="fc81f-105">Issues with the original HttpClient class available in .NET Core</span></span>

<span data-ttu-id="fc81f-106">La classe d’origine et la <xref:System.Net.Http.HttpClient> classe connue peuvent être facilement utilisées, mais dans certains cas, elle n’est pas utilisée correctement par de nombreux développeurs.</span><span class="sxs-lookup"><span data-stu-id="fc81f-106">The original and well-known <xref:System.Net.Http.HttpClient> class can be easily used, but in some cases, it isn't being properly used by many developers.</span></span>

<span data-ttu-id="fc81f-107">`IDisposable`Bien que cette classe implémente, la déclaration et l’instanciation `using` dans une instruction n’est pas recommandée `HttpClient` , car lorsque l’objet est supprimé, le Socket sous-jacent n’est pas libéré immédiatement, ce qui peut entraîner un problème d' _épuisement du socket_ .</span><span class="sxs-lookup"><span data-stu-id="fc81f-107">While this class implements `IDisposable`, declaring and instantiating it within a `using` statement is not preferred because when the `HttpClient` object gets disposed of, the underlying socket is not immediately released, which can lead to a _socket exhaustion_ problem.</span></span> <span data-ttu-id="fc81f-108">Pour plus d’informations sur ce problème, consultez le billet de blog [que vous utilisez httpclient incorrect et déstabiliser votre logiciel](https://aspnetmonsters.com/2016/08/2016-08-27-httpclientwrong/).</span><span class="sxs-lookup"><span data-stu-id="fc81f-108">For more information about this issue, see the blog post [You're using HttpClient wrong and it's destabilizing your software](https://aspnetmonsters.com/2016/08/2016-08-27-httpclientwrong/).</span></span>

<span data-ttu-id="fc81f-109">Par conséquent, `HttpClient` est destiné à être instancié une seule fois et réutilisé tout au long de la durée de vie d’une application.</span><span class="sxs-lookup"><span data-stu-id="fc81f-109">Therefore, `HttpClient` is intended to be instantiated once and reused throughout the life of an application.</span></span> <span data-ttu-id="fc81f-110">L’instanciation d’une classe `HttpClient` pour chaque demande épuise le nombre de sockets disponibles sous des charges élevées.</span><span class="sxs-lookup"><span data-stu-id="fc81f-110">Instantiating an `HttpClient` class for every request will exhaust the number of sockets available under heavy loads.</span></span> <span data-ttu-id="fc81f-111">Ce problème entraîne des erreurs `SocketException`.</span><span class="sxs-lookup"><span data-stu-id="fc81f-111">That issue will result in `SocketException` errors.</span></span> <span data-ttu-id="fc81f-112">Les approches possibles pour résoudre ce problème sont basées sur la création de l’objet `HttpClient` singleton ou statique, comme expliqué dans cet [article Microsoft sur l’utilisation de HttpClient](../../../csharp/tutorials/console-webapiclient.md).</span><span class="sxs-lookup"><span data-stu-id="fc81f-112">Possible approaches to solve that problem are based on the creation of the `HttpClient` object as singleton or static, as explained in this [Microsoft article on HttpClient usage](../../../csharp/tutorials/console-webapiclient.md).</span></span> <span data-ttu-id="fc81f-113">Il peut s’agir d’une bonne solution pour les applications de console à courte durée de vie ou similaires qui sont exécutées plusieurs fois par jour.</span><span class="sxs-lookup"><span data-stu-id="fc81f-113">This can be a good solution for short-lived console apps or similar that are run a few times a day.</span></span>

<span data-ttu-id="fc81f-114">L’utilisation d’une instance partagée de dans des `HttpClient` processus de longue durée constitue un autre problème que les développeurs peuvent rencontrer.</span><span class="sxs-lookup"><span data-stu-id="fc81f-114">Another issue that developers run into is when using a shared instance of `HttpClient` in long running processes.</span></span> <span data-ttu-id="fc81f-115">Dans le cas où le HttpClient est instancié comme un singleton ou un objet statique, il ne parvient pas à gérer les modifications DNS comme décrit dans ce [numéro](https://github.com/dotnet/runtime/issues/18348) du référentiel dotnet/Runtime github.</span><span class="sxs-lookup"><span data-stu-id="fc81f-115">In a situation where the HttpClient is instantiated as a singleton or a static object, it fails to handle the DNS changes as described in this [issue](https://github.com/dotnet/runtime/issues/18348) of the dotnet/runtime GitHub repository.</span></span>

<span data-ttu-id="fc81f-116">Toutefois, le problème n’est pas `HttpClient` vraiment avec par se, mais avec le [constructeur par défaut pour httpclient](https://docs.microsoft.com/dotnet/api/system.net.http.httpclient.-ctor?view=netcore-3.1#System_Net_Http_HttpClient__ctor), car il crée une nouvelle <xref:System.Net.Http.HttpMessageHandler>instance concrète de, qui est celle qui a des problèmes d' *épuisement des sockets* et des modifications DNS mentionnées ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="fc81f-116">However, the issue isn't really with `HttpClient` per se, but with the [default constructor for HttpClient](https://docs.microsoft.com/dotnet/api/system.net.http.httpclient.-ctor?view=netcore-3.1#System_Net_Http_HttpClient__ctor), because it creates a new concrete instance of <xref:System.Net.Http.HttpMessageHandler>, which is the one that has *sockets exhaustion* and DNS changes issues mentioned above.</span></span>

<span data-ttu-id="fc81f-117">Pour résoudre les problèmes mentionnés ci-dessus et `HttpClient` rendre les instances gérables, .net Core 2,1 <xref:System.Net.Http.IHttpClientFactory> a introduit l’interface qui peut être utilisée pour `HttpClient` configurer et créer des instances dans une application via l’injection de dépendances (di).</span><span class="sxs-lookup"><span data-stu-id="fc81f-117">To address the issues mentioned above and to make `HttpClient` instances manageable, .NET Core 2.1 introduced the <xref:System.Net.Http.IHttpClientFactory> interface which can be used to configure and create `HttpClient` instances in an app through Dependency Injection (DI).</span></span> <span data-ttu-id="fc81f-118">Il fournit également des extensions pour l’intergiciel (middleware) basé sur Polly afin de tirer parti des gestionnaires de délégation dans HttpClient.</span><span class="sxs-lookup"><span data-stu-id="fc81f-118">It also provides extensions for Polly-based middleware to take advantage of delegating handlers in HttpClient.</span></span>

<span data-ttu-id="fc81f-119">[Polly](http://www.thepollyproject.org/) est une bibliothèque de gestion des erreurs temporaires qui permet aux développeurs d’ajouter de la résilience à leurs applications à l’aide de stratégies prédéfinies de façon Fluent et thread-safe.</span><span class="sxs-lookup"><span data-stu-id="fc81f-119">[Polly](http://www.thepollyproject.org/) is a transient-fault-handling library that helps developers add resiliency to their applications, by using some pre-defined policies in a fluent and thread-safe manner.</span></span>

## <a name="benefits-of-using-ihttpclientfactory"></a><span data-ttu-id="fc81f-120">Avantages de l’utilisation de IHttpClientFactory</span><span class="sxs-lookup"><span data-stu-id="fc81f-120">Benefits of using IHttpClientFactory</span></span>

<span data-ttu-id="fc81f-121">L’implémentation actuelle de <xref:System.Net.Http.IHttpClientFactory>, qui implémente également <xref:System.Net.Http.IHttpMessageHandlerFactory>, offre les avantages suivants :</span><span class="sxs-lookup"><span data-stu-id="fc81f-121">The current implementation of <xref:System.Net.Http.IHttpClientFactory>, that also implements <xref:System.Net.Http.IHttpMessageHandlerFactory>, offers the following benefits:</span></span>

- <span data-ttu-id="fc81f-122">Fournit un emplacement central pour nommer et configurer des objets `HttpClient` logiques.</span><span class="sxs-lookup"><span data-stu-id="fc81f-122">Provides a central location for naming and configuring logical `HttpClient` objects.</span></span> <span data-ttu-id="fc81f-123">Par exemple, vous pouvez configurer un client (Service Agent) qui est préconfiguré pour accéder à un microservice spécifique.</span><span class="sxs-lookup"><span data-stu-id="fc81f-123">For example, you may configure a client (Service Agent) that's pre-configured to access a specific microservice.</span></span>
- <span data-ttu-id="fc81f-124">Codifier le concept d’intergiciel (middleware sortant) via la délégation de gestionnaires `HttpClient` dans et l’implémentation de l’intergiciel (middleware) basé sur Polly pour tirer parti des stratégies de Polly pour la résilience.</span><span class="sxs-lookup"><span data-stu-id="fc81f-124">Codify the concept of outgoing middleware via delegating handlers in `HttpClient` and implementing Polly-based middleware to take advantage of Polly's policies for resiliency.</span></span>
- <span data-ttu-id="fc81f-125">`HttpClient` intègre déjà le concept de délégation des gestionnaires qui pourraient être liés ensemble pour les requêtes HTTP sortantes.</span><span class="sxs-lookup"><span data-stu-id="fc81f-125">`HttpClient` already has the concept of delegating handlers that could be linked together for outgoing HTTP requests.</span></span> <span data-ttu-id="fc81f-126">Vous pouvez inscrire des clients HTTP dans l’usine et utiliser un gestionnaire Polly pour utiliser des stratégies Polly pour les nouvelles tentatives, les CircuitBreakers, etc.</span><span class="sxs-lookup"><span data-stu-id="fc81f-126">You can register HTTP clients into the factory and you can use a Polly handler to use Polly policies for Retry, CircuitBreakers, and so on.</span></span>
- <span data-ttu-id="fc81f-127">Gérez la durée de <xref:System.Net.Http.HttpMessageHandler> vie de pour éviter les problèmes/problèmes mentionnés qui peuvent se `HttpClient` produire lors de la gestion des durées de vie vous-même.</span><span class="sxs-lookup"><span data-stu-id="fc81f-127">Manage the lifetime of <xref:System.Net.Http.HttpMessageHandler> to avoid the mentioned problems/issues that can occur when managing `HttpClient` lifetimes yourself.</span></span>

> [!TIP]
> <span data-ttu-id="fc81f-128">Les `HttpClient` instances injectées par di, peuvent être supprimées de manière sécurisée, car le associé `HttpMessageHandler` est géré par la fabrique.</span><span class="sxs-lookup"><span data-stu-id="fc81f-128">The `HttpClient` instances injected by DI, can be disposed of safely, because the associated `HttpMessageHandler` is managed by the factory.</span></span> <span data-ttu-id="fc81f-129">En fait, les `HttpClient` instances injectées sont *étendues* d’une perspective di.</span><span class="sxs-lookup"><span data-stu-id="fc81f-129">As a matter of fact, injected `HttpClient` instances are *Scoped* from a DI perspective.</span></span>

> [!NOTE]
> <span data-ttu-id="fc81f-130">L’implémentation de `IHttpClientFactory` (`DefaultHttpClientFactory`) est étroitement liée à l’implémentation de di dans le `Microsoft.Extensions.DependencyInjection` package NuGet.</span><span class="sxs-lookup"><span data-stu-id="fc81f-130">The implementation of `IHttpClientFactory` (`DefaultHttpClientFactory`) is tightly tied to the DI implementation in the `Microsoft.Extensions.DependencyInjection` NuGet package.</span></span> <span data-ttu-id="fc81f-131">Pour plus d’informations sur l’utilisation d’autres conteneurs d’injection de données, consultez cette [discussion GitHub](https://github.com/dotnet/extensions/issues/1345).</span><span class="sxs-lookup"><span data-stu-id="fc81f-131">For more information about using other DI containers, see this [GitHub discussion](https://github.com/dotnet/extensions/issues/1345).</span></span>

## <a name="multiple-ways-to-use-ihttpclientfactory"></a><span data-ttu-id="fc81f-132">Plusieurs manières d’utiliser IHttpClientFactory</span><span class="sxs-lookup"><span data-stu-id="fc81f-132">Multiple ways to use IHttpClientFactory</span></span>

<span data-ttu-id="fc81f-133">Il existe diverses façons d’utiliser `IHttpClientFactory` dans votre application :</span><span class="sxs-lookup"><span data-stu-id="fc81f-133">There are several ways that you can use `IHttpClientFactory` in your application:</span></span>

- <span data-ttu-id="fc81f-134">Utilisation de base</span><span class="sxs-lookup"><span data-stu-id="fc81f-134">Basic usage</span></span>
- <span data-ttu-id="fc81f-135">Utiliser des clients nommés</span><span class="sxs-lookup"><span data-stu-id="fc81f-135">Use Named Clients</span></span>
- <span data-ttu-id="fc81f-136">Utiliser des clients typés</span><span class="sxs-lookup"><span data-stu-id="fc81f-136">Use Typed Clients</span></span>
- <span data-ttu-id="fc81f-137">Utiliser des clients générés</span><span class="sxs-lookup"><span data-stu-id="fc81f-137">Use Generated Clients</span></span>

<span data-ttu-id="fc81f-138">Par souci de concision, ce guide présente la manière la plus structurée d' `IHttpClientFactory`utiliser, qui consiste à utiliser des clients typés (modèle de l’agent de service).</span><span class="sxs-lookup"><span data-stu-id="fc81f-138">For the sake of brevity, this guidance shows the most structured way to use `IHttpClientFactory`, which is to use Typed Clients (Service Agent pattern).</span></span> <span data-ttu-id="fc81f-139">Toutefois, toutes les options sont documentées et sont actuellement répertoriées dans cet [article pour couvrir l' `IHttpClientFactory` utilisation](/aspnet/core/fundamentals/http-requests#consumption-patterns).</span><span class="sxs-lookup"><span data-stu-id="fc81f-139">However, all options are documented and are currently listed in this [article covering the `IHttpClientFactory` usage](/aspnet/core/fundamentals/http-requests#consumption-patterns).</span></span>

## <a name="how-to-use-typed-clients-with-ihttpclientfactory"></a><span data-ttu-id="fc81f-140">Utilisation de clients typés avec IHttpClientFactory</span><span class="sxs-lookup"><span data-stu-id="fc81f-140">How to use Typed Clients with IHttpClientFactory</span></span>

<span data-ttu-id="fc81f-141">Mais qu’est-ce donc qu’un « client typé » ?</span><span class="sxs-lookup"><span data-stu-id="fc81f-141">So, what's a "Typed Client"?</span></span> <span data-ttu-id="fc81f-142">Il s’agit simplement `HttpClient` d’un qui est préconfiguré pour une utilisation spécifique.</span><span class="sxs-lookup"><span data-stu-id="fc81f-142">It's just an `HttpClient` that's pre-configured for some specific use.</span></span> <span data-ttu-id="fc81f-143">Cette configuration peut inclure des valeurs spécifiques telles que le serveur de base, des en-têtes HTTP ou des délais d’expiration.</span><span class="sxs-lookup"><span data-stu-id="fc81f-143">This configuration can include specific values such as the base server, HTTP headers or time outs.</span></span>

<span data-ttu-id="fc81f-144">Le diagramme suivant montre comment les clients typés sont utilisés avec `IHttpClientFactory` :</span><span class="sxs-lookup"><span data-stu-id="fc81f-144">The following diagram shows how Typed Clients are used with `IHttpClientFactory`:</span></span>

![Diagramme montrant comment les clients typés sont utilisés avec IHttpClientFactory.](./media/use-httpclientfactory-to-implement-resilient-http-requests/client-application-code.png)

<span data-ttu-id="fc81f-146">**Figure 8-4**.</span><span class="sxs-lookup"><span data-stu-id="fc81f-146">**Figure 8-4**.</span></span> <span data-ttu-id="fc81f-147">Utilisation `IHttpClientFactory` de avec les classes clientes typées.</span><span class="sxs-lookup"><span data-stu-id="fc81f-147">Using `IHttpClientFactory` with Typed Client classes.</span></span>

<span data-ttu-id="fc81f-148">Dans l’image ci-dessus `ClientService` , une (utilisée par un contrôleur ou un code client `HttpClient` ) utilise un créé `IHttpClientFactory`par l’inscrit.</span><span class="sxs-lookup"><span data-stu-id="fc81f-148">In the above image, a `ClientService` (used by a controller or client code) uses an `HttpClient` created by the registered `IHttpClientFactory`.</span></span> <span data-ttu-id="fc81f-149">Cette fabrique assigne un `HttpMessageHandler` à partir d’un pool `HttpClient`à.</span><span class="sxs-lookup"><span data-stu-id="fc81f-149">This factory assigns an `HttpMessageHandler` from a pool to the `HttpClient`.</span></span> <span data-ttu-id="fc81f-150">Le `HttpClient` peut être configuré avec les stratégies de Polly lors de `IHttpClientFactory` l’inscription du dans le conteneur d’injection <xref:Microsoft.Extensions.DependencyInjection.HttpClientFactoryServiceCollectionExtensions.AddHttpClient*>de règles avec la méthode d’extension.</span><span class="sxs-lookup"><span data-stu-id="fc81f-150">The `HttpClient` can be configured with Polly's policies when registering the `IHttpClientFactory` in the DI container with the extension method <xref:Microsoft.Extensions.DependencyInjection.HttpClientFactoryServiceCollectionExtensions.AddHttpClient*>.</span></span>

<span data-ttu-id="fc81f-151">Pour configurer la structure ci-dessus <xref:System.Net.Http.IHttpClientFactory> , ajoutez-la dans votre `Microsoft.Extensions.Http` application en installant le <xref:Microsoft.Extensions.DependencyInjection.HttpClientFactoryServiceCollectionExtensions.AddHttpClient*> package NuGet qui <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection>comprend la méthode d’extension pour.</span><span class="sxs-lookup"><span data-stu-id="fc81f-151">To configure the above structure, add <xref:System.Net.Http.IHttpClientFactory> in your application by installing the `Microsoft.Extensions.Http` NuGet package that includes the <xref:Microsoft.Extensions.DependencyInjection.HttpClientFactoryServiceCollectionExtensions.AddHttpClient*> extension method for <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection>.</span></span> <span data-ttu-id="fc81f-152">Cette méthode d’extension inscrit la classe `DefaultHttpClientFactory` interne à utiliser comme singleton pour l’interface `IHttpClientFactory`.</span><span class="sxs-lookup"><span data-stu-id="fc81f-152">This extension method registers the internal `DefaultHttpClientFactory` class to be used as a singleton for the interface `IHttpClientFactory`.</span></span> <span data-ttu-id="fc81f-153">Elle définit une configuration temporaire pour <xref:Microsoft.Extensions.Http.HttpMessageHandlerBuilder>.</span><span class="sxs-lookup"><span data-stu-id="fc81f-153">It defines a transient configuration for the <xref:Microsoft.Extensions.Http.HttpMessageHandlerBuilder>.</span></span> <span data-ttu-id="fc81f-154">Ce gestionnaire de messages (objet <xref:System.Net.Http.HttpMessageHandler>), obtenu à partir d’un pool, est utilisé par le `HttpClient` retourné à partir de la fabrique.</span><span class="sxs-lookup"><span data-stu-id="fc81f-154">This message handler (<xref:System.Net.Http.HttpMessageHandler> object), taken from a pool, is used by the `HttpClient` returned from the factory.</span></span>

<span data-ttu-id="fc81f-155">Dans le code suivant, vous pouvez voir comment utiliser `AddHttpClient()` pour enregistrer les clients typés (agents de service) qui ont besoin d’utiliser `HttpClient`.</span><span class="sxs-lookup"><span data-stu-id="fc81f-155">In the next code, you can see how `AddHttpClient()` can be used to register Typed Clients (Service Agents) that need to use `HttpClient`.</span></span>

```csharp
// Startup.cs
//Add http client services at ConfigureServices(IServiceCollection services)
services.AddHttpClient<ICatalogService, CatalogService>();
services.AddHttpClient<IBasketService, BasketService>();
services.AddHttpClient<IOrderingService, OrderingService>();
```

<span data-ttu-id="fc81f-156">L’inscription des services du client comme indiqué dans le code précédent, `DefaultClientFactory` crée une norme `HttpClient` pour chaque service.</span><span class="sxs-lookup"><span data-stu-id="fc81f-156">Registering the client services as shown in the previous code, makes the `DefaultClientFactory` create a standard `HttpClient` for each service.</span></span>

<span data-ttu-id="fc81f-157">Vous pouvez également ajouter une configuration spécifique à l’instance dans l’inscription à, par exemple, configurer l’adresse de base et ajouter des stratégies de résilience, comme illustré dans le code suivant :</span><span class="sxs-lookup"><span data-stu-id="fc81f-157">You could also add instance-specific configuration in the registration to, for example, configure the base address, and add some resiliency policies, as shown in the following code:</span></span>

```csharp
services.AddHttpClient<ICatalogService, CatalogService>(client =>
{
    client.BaseAddress = new Uri(Configuration["BaseUrl"]);
})
    .AddPolicyHandler(GetRetryPolicy())
    .AddPolicyHandler(GetCircuitBreakerPolicy());
```

<span data-ttu-id="fc81f-158">Pour les besoins de l’exemple, vous pouvez voir l’une des stratégies ci-dessus dans le code suivant :</span><span class="sxs-lookup"><span data-stu-id="fc81f-158">Just for the example sake, you can see one of the above policies in the next code:</span></span>

```csharp
static IAsyncPolicy<HttpResponseMessage> GetRetryPolicy()
{
    return HttpPolicyExtensions
        .HandleTransientHttpError()
        .OrResult(msg => msg.StatusCode == System.Net.HttpStatusCode.NotFound)
        .WaitAndRetryAsync(6, retryAttempt => TimeSpan.FromSeconds(Math.Pow(2, retryAttempt)));
}
```

<span data-ttu-id="fc81f-159">Vous trouverez plus d’informations sur l’utilisation de Polly dans l' [article suivant](implement-http-call-retries-exponential-backoff-polly.md).</span><span class="sxs-lookup"><span data-stu-id="fc81f-159">You can find more details about using Polly in the [Next article](implement-http-call-retries-exponential-backoff-polly.md).</span></span>

### <a name="httpclient-lifetimes"></a><span data-ttu-id="fc81f-160">Durées de vie de HttpClient</span><span class="sxs-lookup"><span data-stu-id="fc81f-160">HttpClient lifetimes</span></span>

<span data-ttu-id="fc81f-161">Chaque fois que vous obtenez un objet `HttpClient` à partir de `IHttpClientFactory`, une nouvelle instance est retournée.</span><span class="sxs-lookup"><span data-stu-id="fc81f-161">Each time you get an `HttpClient` object from the `IHttpClientFactory`, a new instance is returned.</span></span> <span data-ttu-id="fc81f-162">Mais chaque `HttpClient` utilise un `HttpMessageHandler` qui est mis en pool et réutilisé par `IHttpClientFactory` pour réduire la consommation de ressources, tant que la durée de vie du `HttpMessageHandler` n’a pas expiré.</span><span class="sxs-lookup"><span data-stu-id="fc81f-162">But each `HttpClient` uses an `HttpMessageHandler` that's pooled and reused by the `IHttpClientFactory` to reduce resource consumption, as long as the `HttpMessageHandler`'s lifetime hasn't expired.</span></span>

<span data-ttu-id="fc81f-163">Le regroupement de gestionnaires est souhaitable, car chaque gestionnaire gère généralement ses propres connexions HTTP sous-jacentes : créer plus de gestionnaires que nécessaire peut entraîner des délais dans la connexion.</span><span class="sxs-lookup"><span data-stu-id="fc81f-163">Pooling of handlers is desirable as each handler typically manages its own underlying HTTP connections; creating more handlers than necessary can result in connection delays.</span></span> <span data-ttu-id="fc81f-164">Certains gestionnaires conservent aussi les connexions indéfiniment ouvertes, ce qui peut empêcher le gestionnaire de réagir aux changements du DNS.</span><span class="sxs-lookup"><span data-stu-id="fc81f-164">Some handlers also keep connections open indefinitely, which can prevent the handler from reacting to DNS changes.</span></span>

<span data-ttu-id="fc81f-165">Les objets `HttpMessageHandler` du pool ont une durée de vie qui correspond à la durée pendant laquelle une instance `HttpMessageHandler` du pool peut être réutilisée.</span><span class="sxs-lookup"><span data-stu-id="fc81f-165">The `HttpMessageHandler` objects in the pool have a lifetime that's the length of time that an `HttpMessageHandler` instance in the pool can be reused.</span></span> <span data-ttu-id="fc81f-166">La valeur par défaut est de deux minutes, mais elle peut être remplacée pour chaque client typé.</span><span class="sxs-lookup"><span data-stu-id="fc81f-166">The default value is two minutes, but it can be overridden per Typed Client.</span></span> <span data-ttu-id="fc81f-167">Pour la remplacer, appelez `SetHandlerLifetime()` sur le <xref:Microsoft.Extensions.DependencyInjection.IHttpClientBuilder> qui est retourné lors de la création du client, comme indiqué dans le code suivant :</span><span class="sxs-lookup"><span data-stu-id="fc81f-167">To override it, call `SetHandlerLifetime()` on the <xref:Microsoft.Extensions.DependencyInjection.IHttpClientBuilder> that's returned when creating the client, as shown in the following code:</span></span>

```csharp
//Set 5 min as the lifetime for the HttpMessageHandler objects in the pool used for the Catalog Typed Client
services.AddHttpClient<ICatalogService, CatalogService>()
    .SetHandlerLifetime(TimeSpan.FromMinutes(5));
```

<span data-ttu-id="fc81f-168">Chaque client typé peut avoir sa propre valeur de durée de vie de gestionnaire configurée.</span><span class="sxs-lookup"><span data-stu-id="fc81f-168">Each Typed Client can have its own configured handler lifetime value.</span></span> <span data-ttu-id="fc81f-169">Définissez la durée de vie sur `InfiniteTimeSpan` pour désactiver l’expiration du gestionnaire.</span><span class="sxs-lookup"><span data-stu-id="fc81f-169">Set the lifetime to `InfiniteTimeSpan` to disable handler expiry.</span></span>

### <a name="implement-your-typed-client-classes-that-use-the-injected-and-configured-httpclient"></a><span data-ttu-id="fc81f-170">Implémenter les classes de client typé qui utilisent l’objet HttpClient injecté et configuré</span><span class="sxs-lookup"><span data-stu-id="fc81f-170">Implement your Typed Client classes that use the injected and configured HttpClient</span></span>

<span data-ttu-id="fc81f-171">Au cours d’une étape précédente, vous devez définir vos classes clientes typées, telles que les classes dans l’exemple de code, telles que « BasketService », « CatalogService », « OrderingService », etc. : un client typé est une `HttpClient` classe qui accepte un objet (injecté par le biais de son constructeur) et l’utilise pour appeler un service http distant.</span><span class="sxs-lookup"><span data-stu-id="fc81f-171">As a previous step, you need to have your Typed Client classes defined, such as the classes in the sample code, like 'BasketService', 'CatalogService', 'OrderingService', etc. – A Typed Client is a class that accepts an `HttpClient` object (injected through its constructor) and uses it to call some remote HTTP service.</span></span> <span data-ttu-id="fc81f-172">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="fc81f-172">For example:</span></span>

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

<span data-ttu-id="fc81f-173">Le client typé (`CatalogService` dans l’exemple) est activé par di (injection de dépendance), ce qui signifie qu’il peut accepter n’importe quel service inscrit dans son `HttpClient`constructeur, en plus de.</span><span class="sxs-lookup"><span data-stu-id="fc81f-173">The Typed Client (`CatalogService` in the example) is activated by DI (Dependency Injection), meaning that it can accept any registered service in its constructor, in addition to `HttpClient`.</span></span>

<span data-ttu-id="fc81f-174">Un client typé est en effet un objet temporaire, ce qui signifie qu’une nouvelle instance est créée dès qu’elle est requise, et qu’il reçoit une nouvelle instance `HttpClient` chaque fois qu’il est construit.</span><span class="sxs-lookup"><span data-stu-id="fc81f-174">A Typed Client is, effectively, a transient object, meaning that a new instance is created each time one is needed and it will receive a new `HttpClient` instance each time it's constructed.</span></span> <span data-ttu-id="fc81f-175">Toutefois, les `HttpMessageHandler` objets du pool sont les objets réutilisés par plusieurs `HttpClient` instances.</span><span class="sxs-lookup"><span data-stu-id="fc81f-175">However, the `HttpMessageHandler` objects in the pool are the objects that are reused by multiple `HttpClient` instances.</span></span>

### <a name="use-your-typed-client-classes"></a><span data-ttu-id="fc81f-176">Utiliser les classes de client typé</span><span class="sxs-lookup"><span data-stu-id="fc81f-176">Use your Typed Client classes</span></span>

<span data-ttu-id="fc81f-177">Enfin, une fois que vos classes typées sont implémentées et que vous les `AddHttpClient()`avez enregistrées et configurées avec, vous pouvez les utiliser partout où vous pouvez avoir des services injectés par di.</span><span class="sxs-lookup"><span data-stu-id="fc81f-177">Finally, once you have your typed classes implemented and have them registered and configured with `AddHttpClient()`, you can use them wherever you can have services injected by DI.</span></span> <span data-ttu-id="fc81f-178">Par exemple, dans un code de page Razor ou un contrôleur d’une application Web MVC, comme dans le code suivant de eShopOnContainers :</span><span class="sxs-lookup"><span data-stu-id="fc81f-178">For example, in a Razor page code or controller of an MVC web app, like in the following code from eShopOnContainers:</span></span>

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

<span data-ttu-id="fc81f-179">Jusqu’à présent, le code présenté effectue simplement des requêtes HTTP standard, mais le « Magic » est fourni dans les sections suivantes, où simplement en ajoutant des stratégies et en déléguant des gestionnaires à vos clients typés inscrits, toutes les requêtes HTTP à effectuer `HttpClient` par se comporteront en tenant compte des stratégies résilientes, telles que les nouvelles tentatives avec interruption exponentielle, disjoncteurs ou tout autre gestionnaire de délégation personnalisée pour implémenter des fonctionnalités de sécurité supplémentaires, comme l’utilisation de jetons d’authentification ou d’autres fonctionnalités personnalisées.</span><span class="sxs-lookup"><span data-stu-id="fc81f-179">Up to this point, the code shown is just performing regular Http requests, but the 'magic' comes in the following sections where, just by adding policies and delegating handlers to your registered Typed Clients, all the HTTP requests to be done by `HttpClient` will behave taking into account resilient policies such as retries with exponential backoff, circuit breakers, or any other custom delegating handler to implement additional security features, like using auth tokens, or any other custom feature.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="fc81f-180">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="fc81f-180">Additional resources</span></span>

- <span data-ttu-id="fc81f-181">**Utilisation de HttpClientFactory dans .NET Core**</span><span class="sxs-lookup"><span data-stu-id="fc81f-181">**Using HttpClientFactory in .NET Core**</span></span>  
  [https://docs.microsoft.com/aspnet/core/fundamentals/http-requests](/aspnet/core/fundamentals/http-requests)

- <span data-ttu-id="fc81f-182">**Code source HttpClientFactory dans le `dotnet/extensions` référentiel GitHub**</span><span class="sxs-lookup"><span data-stu-id="fc81f-182">**HttpClientFactory source code in the `dotnet/extensions` GitHub repository**</span></span>  
  <https://github.com/dotnet/extensions/tree/master/src/HttpClientFactory>

- <span data-ttu-id="fc81f-183">**Polly (Résilience .NET et bibliothèque de gestion des erreurs temporaires)**</span><span class="sxs-lookup"><span data-stu-id="fc81f-183">**Polly (.NET resilience and transient-fault-handling library)**</span></span>  
  <http://www.thepollyproject.org/>
  
- <span data-ttu-id="fc81f-184">**Utilisation de IHttpClientFactory sans injection de dépendance (problème GitHub)**</span><span class="sxs-lookup"><span data-stu-id="fc81f-184">**Using IHttpClientFactory without dependency injection (GitHub issue)**</span></span>  
  <https://github.com/dotnet/extensions/issues/1345>

>[!div class="step-by-step"]
><span data-ttu-id="fc81f-185">[Précédent](implement-resilient-entity-framework-core-sql-connections.md)
>[suivant](implement-http-call-retries-exponential-backoff-polly.md)</span><span class="sxs-lookup"><span data-stu-id="fc81f-185">[Previous](implement-resilient-entity-framework-core-sql-connections.md)
[Next](implement-http-call-retries-exponential-backoff-polly.md)</span></span>
