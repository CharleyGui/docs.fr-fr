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
# <a name="use-ihttpclientfactory-to-implement-resilient-http-requests"></a><span data-ttu-id="0a844-103">Utilisez IHttpClientFactory pour mettre en œuvre des demandes HTTP résilientes</span><span class="sxs-lookup"><span data-stu-id="0a844-103">Use IHttpClientFactory to implement resilient HTTP requests</span></span>

<span data-ttu-id="0a844-104"><xref:System.Net.Http.IHttpClientFactory>est un contrat `DefaultHttpClientFactory`mis en œuvre par , une usine d’opinion, disponible depuis .NET Core 2.1, pour créer des <xref:System.Net.Http.HttpClient> instances à utiliser dans vos applications.</span><span class="sxs-lookup"><span data-stu-id="0a844-104"><xref:System.Net.Http.IHttpClientFactory> is a contract implemented by `DefaultHttpClientFactory`, an opinionated factory, available since .NET Core 2.1, for creating <xref:System.Net.Http.HttpClient> instances to be used in your applications.</span></span>

## <a name="issues-with-the-original-httpclient-class-available-in-net-core"></a><span data-ttu-id="0a844-105">Problèmes liés à la classe HttpClient d’origine disponible dans .NET Core</span><span class="sxs-lookup"><span data-stu-id="0a844-105">Issues with the original HttpClient class available in .NET Core</span></span>

<span data-ttu-id="0a844-106">La classe originale <xref:System.Net.Http.HttpClient> et bien connue peut être facilement utilisée, mais dans certains cas, elle n’est pas correctement utilisée par de nombreux développeurs.</span><span class="sxs-lookup"><span data-stu-id="0a844-106">The original and well-known <xref:System.Net.Http.HttpClient> class can be easily used, but in some cases, it isn't being properly used by many developers.</span></span>

<span data-ttu-id="0a844-107">Bien que cette `IDisposable`classe implémente, le `using` déclarant et l’instantané dans une déclaration n’est pas préférable parce que lorsque l’objet `HttpClient` est éliminé, la prise sous-jacente n’est pas immédiatement libérée, ce qui peut conduire à un problème _d’épuisement de prise._</span><span class="sxs-lookup"><span data-stu-id="0a844-107">While this class implements `IDisposable`, declaring and instantiating it within a `using` statement is not preferred because when the `HttpClient` object gets disposed of, the underlying socket is not immediately released, which can lead to a _socket exhaustion_ problem.</span></span> <span data-ttu-id="0a844-108">Pour plus d’informations sur ce problème, voir le blog [que vous utilisez HttpClient mal et il est déstabilisant votre logiciel](https://aspnetmonsters.com/2016/08/2016-08-27-httpclientwrong/).</span><span class="sxs-lookup"><span data-stu-id="0a844-108">For more information about this issue, see the blog post [You're using HttpClient wrong and it's destabilizing your software](https://aspnetmonsters.com/2016/08/2016-08-27-httpclientwrong/).</span></span>

<span data-ttu-id="0a844-109">Par conséquent, `HttpClient` est destiné à être instancié une seule fois et réutilisé tout au long de la durée de vie d’une application.</span><span class="sxs-lookup"><span data-stu-id="0a844-109">Therefore, `HttpClient` is intended to be instantiated once and reused throughout the life of an application.</span></span> <span data-ttu-id="0a844-110">L’instanciation d’une classe `HttpClient` pour chaque demande épuise le nombre de sockets disponibles sous des charges élevées.</span><span class="sxs-lookup"><span data-stu-id="0a844-110">Instantiating an `HttpClient` class for every request will exhaust the number of sockets available under heavy loads.</span></span> <span data-ttu-id="0a844-111">Ce problème entraîne des erreurs `SocketException`.</span><span class="sxs-lookup"><span data-stu-id="0a844-111">That issue will result in `SocketException` errors.</span></span> <span data-ttu-id="0a844-112">Les approches possibles pour résoudre ce problème sont basées sur la création de l’objet `HttpClient` singleton ou statique, comme expliqué dans cet [article Microsoft sur l’utilisation de HttpClient](../../../csharp/tutorials/console-webapiclient.md).</span><span class="sxs-lookup"><span data-stu-id="0a844-112">Possible approaches to solve that problem are based on the creation of the `HttpClient` object as singleton or static, as explained in this [Microsoft article on HttpClient usage](../../../csharp/tutorials/console-webapiclient.md).</span></span> <span data-ttu-id="0a844-113">Cela peut être une bonne solution pour les applications de console de courte durée ou similaires qui sont exécutés quelques fois par jour.</span><span class="sxs-lookup"><span data-stu-id="0a844-113">This can be a good solution for short-lived console apps or similar that are run a few times a day.</span></span>

<span data-ttu-id="0a844-114">Un autre problème que les développeurs se `HttpClient` heurtent est lors de l’utilisation d’un exemple partagé de processus en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="0a844-114">Another issue that developers run into is when using a shared instance of `HttpClient` in long running processes.</span></span> <span data-ttu-id="0a844-115">Dans une situation où le HttpClient est instantané comme un singleton ou un objet statique, il ne parvient pas à gérer les changements DNS comme décrit dans ce [numéro](https://github.com/dotnet/corefx/issues/11224) du référentiel pointnet/corefx GitHub.</span><span class="sxs-lookup"><span data-stu-id="0a844-115">In a situation where the HttpClient is instantiated as a singleton or a static object, it fails to handle the DNS changes as described in this [issue](https://github.com/dotnet/corefx/issues/11224) of the dotnet/corefx GitHub repository.</span></span>

<span data-ttu-id="0a844-116">`HttpClient` Cependant, la question n’est pas vraiment avec en soi, mais avec le constructeur par défaut pour [HttpClient](https://docs.microsoft.com/dotnet/api/system.net.http.httpclient.-ctor?view=netcore-3.1#System_Net_Http_HttpClient__ctor), parce qu’il crée une nouvelle instance concrète de <xref:System.Net.Http.HttpMessageHandler>, qui est celui qui a des prises *d’épuisement* et DNS change les questions mentionnées ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="0a844-116">However, the issue isn't really with `HttpClient` per se, but with the [default constructor for HttpClient](https://docs.microsoft.com/dotnet/api/system.net.http.httpclient.-ctor?view=netcore-3.1#System_Net_Http_HttpClient__ctor), because it creates a new concrete instance of <xref:System.Net.Http.HttpMessageHandler>, which is the one that has *sockets exhaustion* and DNS changes issues mentioned above.</span></span>

<span data-ttu-id="0a844-117">Pour résoudre les problèmes mentionnés ci-dessus et pour rendre `HttpClient` les <xref:System.Net.Http.IHttpClientFactory> instances gérables, .NET `HttpClient` Core 2.1 a introduit l’interface qui peut être utilisée pour configurer et créer des instances dans une application via Dependency Injection (DI).</span><span class="sxs-lookup"><span data-stu-id="0a844-117">To address the issues mentioned above and to make `HttpClient` instances manageable, .NET Core 2.1 introduced the <xref:System.Net.Http.IHttpClientFactory> interface which can be used to configure and create `HttpClient` instances in an app through Dependency Injection (DI).</span></span> <span data-ttu-id="0a844-118">Il fournit également des extensions pour Polly-basé middleware pour profiter de la délégation des gestionnaires dans HttpClient.</span><span class="sxs-lookup"><span data-stu-id="0a844-118">It also provides extensions for Polly-based middleware to take advantage of delegating handlers in HttpClient.</span></span>

<span data-ttu-id="0a844-119">[Polly](http://www.thepollyproject.org/) est une bibliothèque de manutention de défauts transitoires qui aide les développeurs à ajouter de la résilience à leurs applications, en utilisant certaines stratégies prédéfinises d’une manière fluide et sans fil.</span><span class="sxs-lookup"><span data-stu-id="0a844-119">[Polly](http://www.thepollyproject.org/) is a transient-fault-handling library that helps developers add resiliency to their applications, by using some pre-defined policies in a fluent and thread-safe manner.</span></span>

## <a name="benefits-of-using-ihttpclientfactory"></a><span data-ttu-id="0a844-120">Avantages de l’utilisation d’IHttpClientFactory</span><span class="sxs-lookup"><span data-stu-id="0a844-120">Benefits of using IHttpClientFactory</span></span>

<span data-ttu-id="0a844-121">La mise <xref:System.Net.Http.IHttpClientFactory>en œuvre <xref:System.Net.Http.IHttpMessageHandlerFactory>actuelle de , qui met également en œuvre , offre les avantages suivants:</span><span class="sxs-lookup"><span data-stu-id="0a844-121">The current implementation of <xref:System.Net.Http.IHttpClientFactory>, that also implements <xref:System.Net.Http.IHttpMessageHandlerFactory>, offers the following benefits:</span></span>

- <span data-ttu-id="0a844-122">Fournit un emplacement central pour nommer `HttpClient` et configurer des objets logiques.</span><span class="sxs-lookup"><span data-stu-id="0a844-122">Provides a central location for naming and configuring logical `HttpClient` objects.</span></span> <span data-ttu-id="0a844-123">Par exemple, vous pouvez configurer un client (Service Agent) qui est préconfiguré pour accéder à un microservice spécifique.</span><span class="sxs-lookup"><span data-stu-id="0a844-123">For example, you may configure a client (Service Agent) that's pre-configured to access a specific microservice.</span></span>
- <span data-ttu-id="0a844-124">Codifier le concept de middleware sortant en `HttpClient` déléguant les gestionnaires et en mettant en œuvre des moyens intermédiaires basés sur Polly pour tirer parti des politiques de Polly en matière de résilience.</span><span class="sxs-lookup"><span data-stu-id="0a844-124">Codify the concept of outgoing middleware via delegating handlers in `HttpClient` and implementing Polly-based middleware to take advantage of Polly's policies for resiliency.</span></span>
- <span data-ttu-id="0a844-125">`HttpClient` intègre déjà le concept de délégation des gestionnaires qui pourraient être liés ensemble pour les requêtes HTTP sortantes.</span><span class="sxs-lookup"><span data-stu-id="0a844-125">`HttpClient` already has the concept of delegating handlers that could be linked together for outgoing HTTP requests.</span></span> <span data-ttu-id="0a844-126">Vous pouvez enregistrer des clients HTTP dans l’usine et vous pouvez utiliser un gestionnaire Polly pour utiliser les politiques Polly pour Retry, CircuitBreakers, et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="0a844-126">You can register HTTP clients into the factory and you can use a Polly handler to use Polly policies for Retry, CircuitBreakers, and so on.</span></span>
- <span data-ttu-id="0a844-127">Gérez la <xref:System.Net.Http.HttpMessageHandler> durée de vie pour éviter les `HttpClient` problèmes ou les problèmes mentionnés qui peuvent se produire lors de la gestion des vies vous-même.</span><span class="sxs-lookup"><span data-stu-id="0a844-127">Manage the lifetime of <xref:System.Net.Http.HttpMessageHandler> to avoid the mentioned problems/issues that can occur when managing `HttpClient` lifetimes yourself.</span></span>

> [!TIP]
> <span data-ttu-id="0a844-128">Les `HttpClient` cas injectés par DI, peuvent être éliminés en toute sécurité, parce que l’associé `HttpMessageHandler` est géré par l’usine.</span><span class="sxs-lookup"><span data-stu-id="0a844-128">The `HttpClient` instances injected by DI, can be disposed of safely, because the associated `HttpMessageHandler` is managed by the factory.</span></span> <span data-ttu-id="0a844-129">En fait, les `HttpClient` cas injectés sont *scoped* d’un point de vue DI.</span><span class="sxs-lookup"><span data-stu-id="0a844-129">As a matter of fact, injected `HttpClient` instances are *Scoped* from a DI perspective.</span></span>

> [!NOTE]
> <span data-ttu-id="0a844-130">La mise `IHttpClientFactory` `DefaultHttpClientFactory`en œuvre de ( `Microsoft.Extensions.DependencyInjection` ) est étroitement liée à la mise en œuvre DE DI dans le paquet NuGet.</span><span class="sxs-lookup"><span data-stu-id="0a844-130">The implementation of `IHttpClientFactory` (`DefaultHttpClientFactory`) is tightly tied to the DI implementation in the `Microsoft.Extensions.DependencyInjection` NuGet package.</span></span> <span data-ttu-id="0a844-131">Pour plus d’informations sur l’utilisation d’autres conteneurs DI, voir cette [discussion GitHub](https://github.com/dotnet/extensions/issues/1345).</span><span class="sxs-lookup"><span data-stu-id="0a844-131">For more information about using other DI containers, see this [GitHub discussion](https://github.com/dotnet/extensions/issues/1345).</span></span>

## <a name="multiple-ways-to-use-ihttpclientfactory"></a><span data-ttu-id="0a844-132">Plusieurs façons d’utiliser IHttpClientFactory</span><span class="sxs-lookup"><span data-stu-id="0a844-132">Multiple ways to use IHttpClientFactory</span></span>

<span data-ttu-id="0a844-133">Il existe diverses façons d’utiliser `IHttpClientFactory` dans votre application :</span><span class="sxs-lookup"><span data-stu-id="0a844-133">There are several ways that you can use `IHttpClientFactory` in your application:</span></span>

- <span data-ttu-id="0a844-134">Utilisation de base</span><span class="sxs-lookup"><span data-stu-id="0a844-134">Basic usage</span></span>
- <span data-ttu-id="0a844-135">Utiliser des clients nommés</span><span class="sxs-lookup"><span data-stu-id="0a844-135">Use Named Clients</span></span>
- <span data-ttu-id="0a844-136">Utiliser des clients typés</span><span class="sxs-lookup"><span data-stu-id="0a844-136">Use Typed Clients</span></span>
- <span data-ttu-id="0a844-137">Utiliser des clients générés</span><span class="sxs-lookup"><span data-stu-id="0a844-137">Use Generated Clients</span></span>

<span data-ttu-id="0a844-138">Par souci de brièveté, cette orientation montre `IHttpClientFactory`la façon la plus structurée d’utiliser, qui est d’utiliser des clients typés (modèle d’agent de service).</span><span class="sxs-lookup"><span data-stu-id="0a844-138">For the sake of brevity, this guidance shows the most structured way to use `IHttpClientFactory`, which is to use Typed Clients (Service Agent pattern).</span></span> <span data-ttu-id="0a844-139">Cependant, toutes les options sont documentées et sont actuellement répertoriées dans cet [article couvrant `IHttpClientFactory` l’utilisation](/aspnet/core/fundamentals/http-requests#consumption-patterns).</span><span class="sxs-lookup"><span data-stu-id="0a844-139">However, all options are documented and are currently listed in this [article covering the `IHttpClientFactory` usage](/aspnet/core/fundamentals/http-requests#consumption-patterns).</span></span>

## <a name="how-to-use-typed-clients-with-ihttpclientfactory"></a><span data-ttu-id="0a844-140">Comment utiliser les clients typés avec IHttpClientFactory</span><span class="sxs-lookup"><span data-stu-id="0a844-140">How to use Typed Clients with IHttpClientFactory</span></span>

<span data-ttu-id="0a844-141">Mais qu’est-ce donc qu’un « client typé » ?</span><span class="sxs-lookup"><span data-stu-id="0a844-141">So, what's a "Typed Client"?</span></span> <span data-ttu-id="0a844-142">C’est juste `HttpClient` un qui est pré-configuré pour une utilisation spécifique.</span><span class="sxs-lookup"><span data-stu-id="0a844-142">It's just an `HttpClient` that's pre-configured for some specific use.</span></span> <span data-ttu-id="0a844-143">Cette configuration peut inclure des valeurs spécifiques telles que le serveur de base, les en-têtes HTTP ou les temps d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="0a844-143">This configuration can include specific values such as the base server, HTTP headers or time outs.</span></span>

<span data-ttu-id="0a844-144">Le diagramme suivant montre comment les clients typés sont utilisés avec `IHttpClientFactory` :</span><span class="sxs-lookup"><span data-stu-id="0a844-144">The following diagram shows how Typed Clients are used with `IHttpClientFactory`:</span></span>

![Diagramme montrant comment les clients typés sont utilisés avec IHttpClientFactory.](./media/use-httpclientfactory-to-implement-resilient-http-requests/client-application-code.png)

<span data-ttu-id="0a844-146">**Figure 8-4**.</span><span class="sxs-lookup"><span data-stu-id="0a844-146">**Figure 8-4**.</span></span> <span data-ttu-id="0a844-147">Utilisation `IHttpClientFactory` avec des classes de clients typés.</span><span class="sxs-lookup"><span data-stu-id="0a844-147">Using `IHttpClientFactory` with Typed Client classes.</span></span>

<span data-ttu-id="0a844-148">Dans l’image `ClientService` ci-dessus, un (utilisé par `HttpClient` un contrôleur `IHttpClientFactory`ou un code client) utilise un créé par l’enregistrement .</span><span class="sxs-lookup"><span data-stu-id="0a844-148">In the above image, a `ClientService` (used by a controller or client code) uses an `HttpClient` created by the registered `IHttpClientFactory`.</span></span> <span data-ttu-id="0a844-149">Cette usine assigne un d’une `HttpMessageHandler` piscine à la `HttpClient`.</span><span class="sxs-lookup"><span data-stu-id="0a844-149">This factory assigns an `HttpMessageHandler` from a pool to the `HttpClient`.</span></span> <span data-ttu-id="0a844-150">Le `HttpClient` peut être configuré avec les stratégies `IHttpClientFactory` de Polly lors <xref:Microsoft.Extensions.DependencyInjection.HttpClientFactoryServiceCollectionExtensions.AddHttpClient*>de l’enregistrement du conteneur DI avec la méthode d’extension .</span><span class="sxs-lookup"><span data-stu-id="0a844-150">The `HttpClient` can be configured with Polly's policies when registering the `IHttpClientFactory` in the DI container with the extension method <xref:Microsoft.Extensions.DependencyInjection.HttpClientFactoryServiceCollectionExtensions.AddHttpClient*>.</span></span>

<span data-ttu-id="0a844-151">Pour configurer la <xref:System.Net.Http.IHttpClientFactory> structure ci-dessus, `Microsoft.Extensions.Http` ajoutez votre application <xref:Microsoft.Extensions.DependencyInjection.HttpClientFactoryServiceCollectionExtensions.AddHttpClient*> en installant le paquet NuGet qui inclut la méthode d’extension pour <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection>.</span><span class="sxs-lookup"><span data-stu-id="0a844-151">To configure the above structure, add <xref:System.Net.Http.IHttpClientFactory> in your application by installing the `Microsoft.Extensions.Http` NuGet package that includes the <xref:Microsoft.Extensions.DependencyInjection.HttpClientFactoryServiceCollectionExtensions.AddHttpClient*> extension method for <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection>.</span></span> <span data-ttu-id="0a844-152">Cette méthode d’extension `DefaultHttpClientFactory` enregistre la classe interne à `IHttpClientFactory`utiliser comme un singleton pour l’interface .</span><span class="sxs-lookup"><span data-stu-id="0a844-152">This extension method registers the internal `DefaultHttpClientFactory` class to be used as a singleton for the interface `IHttpClientFactory`.</span></span> <span data-ttu-id="0a844-153">Elle définit une configuration temporaire pour <xref:Microsoft.Extensions.Http.HttpMessageHandlerBuilder>.</span><span class="sxs-lookup"><span data-stu-id="0a844-153">It defines a transient configuration for the <xref:Microsoft.Extensions.Http.HttpMessageHandlerBuilder>.</span></span> <span data-ttu-id="0a844-154">Ce gestionnaire de messages (objet <xref:System.Net.Http.HttpMessageHandler>), obtenu à partir d’un pool, est utilisé par le `HttpClient` retourné à partir de la fabrique.</span><span class="sxs-lookup"><span data-stu-id="0a844-154">This message handler (<xref:System.Net.Http.HttpMessageHandler> object), taken from a pool, is used by the `HttpClient` returned from the factory.</span></span>

<span data-ttu-id="0a844-155">Dans le code suivant, vous pouvez voir comment utiliser `AddHttpClient()` pour enregistrer les clients typés (agents de service) qui ont besoin d’utiliser `HttpClient`.</span><span class="sxs-lookup"><span data-stu-id="0a844-155">In the next code, you can see how `AddHttpClient()` can be used to register Typed Clients (Service Agents) that need to use `HttpClient`.</span></span>

```csharp
// Startup.cs
//Add http client services at ConfigureServices(IServiceCollection services)
services.AddHttpClient<ICatalogService, CatalogService>();
services.AddHttpClient<IBasketService, BasketService>();
services.AddHttpClient<IOrderingService, OrderingService>();
```

<span data-ttu-id="0a844-156">L’enregistrement des services à la clientèle `DefaultClientFactory` tel qu’indiqué dans le code précédent, fait de la création une norme `HttpClient` pour chaque service.</span><span class="sxs-lookup"><span data-stu-id="0a844-156">Registering the client services as shown in the previous code, makes the `DefaultClientFactory` create a standard `HttpClient` for each service.</span></span>

<span data-ttu-id="0a844-157">Vous pouvez également ajouter une configuration spécifique à l’instance dans l’enregistrement, par exemple, configurer l’adresse de base et ajouter des stratégies de résilience, comme indiqué dans le code suivant :</span><span class="sxs-lookup"><span data-stu-id="0a844-157">You could also add instance-specific configuration in the registration to, for example, configure the base address, and add some resiliency policies, as shown in the following code:</span></span>

```csharp
services.AddHttpClient<ICatalogService, CatalogService>(client =>
{
    client.BaseAddress = new Uri(Configuration["BaseUrl"]);
})
    .AddPolicyHandler(GetRetryPolicy())
    .AddPolicyHandler(GetCircuitBreakerPolicy());
```

<span data-ttu-id="0a844-158">Juste pour l’exemple, vous pouvez voir l’une des stratégies ci-dessus dans le code suivant:</span><span class="sxs-lookup"><span data-stu-id="0a844-158">Just for the example sake, you can see one of the above policies in the next code:</span></span>

```csharp
static IAsyncPolicy<HttpResponseMessage> GetRetryPolicy()
{
    return HttpPolicyExtensions
        .HandleTransientHttpError()
        .OrResult(msg => msg.StatusCode == System.Net.HttpStatusCode.NotFound)
        .WaitAndRetryAsync(6, retryAttempt => TimeSpan.FromSeconds(Math.Pow(2, retryAttempt)));
}
```

<span data-ttu-id="0a844-159">Vous pouvez trouver plus de détails sur l’utilisation de Polly dans [l’article suivant](implement-http-call-retries-exponential-backoff-polly.md).</span><span class="sxs-lookup"><span data-stu-id="0a844-159">You can find more details about using Polly in the [Next article](implement-http-call-retries-exponential-backoff-polly.md).</span></span>

### <a name="httpclient-lifetimes"></a><span data-ttu-id="0a844-160">Durées de vie de HttpClient</span><span class="sxs-lookup"><span data-stu-id="0a844-160">HttpClient lifetimes</span></span>

<span data-ttu-id="0a844-161">Chaque fois que vous obtenez un objet `HttpClient` à partir de `IHttpClientFactory`, une nouvelle instance est retournée.</span><span class="sxs-lookup"><span data-stu-id="0a844-161">Each time you get an `HttpClient` object from the `IHttpClientFactory`, a new instance is returned.</span></span> <span data-ttu-id="0a844-162">Mais chaque `HttpClient` utilise un `HttpMessageHandler` qui est mis en pool et réutilisé par `IHttpClientFactory` pour réduire la consommation de ressources, tant que la durée de vie du `HttpMessageHandler` n’a pas expiré.</span><span class="sxs-lookup"><span data-stu-id="0a844-162">But each `HttpClient` uses an `HttpMessageHandler` that's pooled and reused by the `IHttpClientFactory` to reduce resource consumption, as long as the `HttpMessageHandler`'s lifetime hasn't expired.</span></span>

<span data-ttu-id="0a844-163">Le regroupement de gestionnaires est souhaitable, car chaque gestionnaire gère généralement ses propres connexions HTTP sous-jacentes : créer plus de gestionnaires que nécessaire peut entraîner des délais dans la connexion.</span><span class="sxs-lookup"><span data-stu-id="0a844-163">Pooling of handlers is desirable as each handler typically manages its own underlying HTTP connections; creating more handlers than necessary can result in connection delays.</span></span> <span data-ttu-id="0a844-164">Certains gestionnaires conservent aussi les connexions indéfiniment ouvertes, ce qui peut empêcher le gestionnaire de réagir aux changements du DNS.</span><span class="sxs-lookup"><span data-stu-id="0a844-164">Some handlers also keep connections open indefinitely, which can prevent the handler from reacting to DNS changes.</span></span>

<span data-ttu-id="0a844-165">Les objets `HttpMessageHandler` du pool ont une durée de vie qui correspond à la durée pendant laquelle une instance `HttpMessageHandler` du pool peut être réutilisée.</span><span class="sxs-lookup"><span data-stu-id="0a844-165">The `HttpMessageHandler` objects in the pool have a lifetime that's the length of time that an `HttpMessageHandler` instance in the pool can be reused.</span></span> <span data-ttu-id="0a844-166">La valeur par défaut est de deux minutes, mais elle peut être remplacée pour chaque client typé.</span><span class="sxs-lookup"><span data-stu-id="0a844-166">The default value is two minutes, but it can be overridden per Typed Client.</span></span> <span data-ttu-id="0a844-167">Pour la remplacer, appelez `SetHandlerLifetime()` sur le <xref:Microsoft.Extensions.DependencyInjection.IHttpClientBuilder> qui est retourné lors de la création du client, comme indiqué dans le code suivant :</span><span class="sxs-lookup"><span data-stu-id="0a844-167">To override it, call `SetHandlerLifetime()` on the <xref:Microsoft.Extensions.DependencyInjection.IHttpClientBuilder> that's returned when creating the client, as shown in the following code:</span></span>

```csharp
//Set 5 min as the lifetime for the HttpMessageHandler objects in the pool used for the Catalog Typed Client
services.AddHttpClient<ICatalogService, CatalogService>()
    .SetHandlerLifetime(TimeSpan.FromMinutes(5));
```

<span data-ttu-id="0a844-168">Chaque client typé peut avoir sa propre valeur de durée de vie de gestionnaire configurée.</span><span class="sxs-lookup"><span data-stu-id="0a844-168">Each Typed Client can have its own configured handler lifetime value.</span></span> <span data-ttu-id="0a844-169">Définissez la durée de vie sur `InfiniteTimeSpan` pour désactiver l’expiration du gestionnaire.</span><span class="sxs-lookup"><span data-stu-id="0a844-169">Set the lifetime to `InfiniteTimeSpan` to disable handler expiry.</span></span>

### <a name="implement-your-typed-client-classes-that-use-the-injected-and-configured-httpclient"></a><span data-ttu-id="0a844-170">Implémenter les classes de client typé qui utilisent l’objet HttpClient injecté et configuré</span><span class="sxs-lookup"><span data-stu-id="0a844-170">Implement your Typed Client classes that use the injected and configured HttpClient</span></span>

<span data-ttu-id="0a844-171">Comme étape précédente, vous devez avoir vos classes de clients typés définies, telles que les classes dans le code de l’échantillon, comme «BasketService», `HttpClient` «CatalogService», «OrderingService», etc - Un client typé est une classe qui accepte un objet (injecté par son constructeur) et l’utilise pour appeler un service HTTP à distance.</span><span class="sxs-lookup"><span data-stu-id="0a844-171">As a previous step, you need to have your Typed Client classes defined, such as the classes in the sample code, like 'BasketService', 'CatalogService', 'OrderingService', etc. – A Typed Client is a class that accepts an `HttpClient` object (injected through its constructor) and uses it to call some remote HTTP service.</span></span> <span data-ttu-id="0a844-172">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="0a844-172">For example:</span></span>

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

<span data-ttu-id="0a844-173">Le client typé (dans`CatalogService` l’exemple) est activé par DI (Dependency Injection), ce qui `HttpClient`signifie qu’il peut accepter tout service enregistré dans son constructeur, en plus de .</span><span class="sxs-lookup"><span data-stu-id="0a844-173">The Typed Client (`CatalogService` in the example) is activated by DI (Dependency Injection), meaning that it can accept any registered service in its constructor, in addition to `HttpClient`.</span></span>

<span data-ttu-id="0a844-174">Un client typé est en effet un objet temporaire, ce qui signifie qu’une nouvelle instance est créée dès qu’elle est requise, et qu’il reçoit une nouvelle instance `HttpClient` chaque fois qu’il est construit.</span><span class="sxs-lookup"><span data-stu-id="0a844-174">A Typed Client is, effectively, a transient object, meaning that a new instance is created each time one is needed and it will receive a new `HttpClient` instance each time it's constructed.</span></span> <span data-ttu-id="0a844-175">Cependant, `HttpMessageHandler` les objets dans la piscine sont les `HttpClient` objets qui sont réutilisés par plusieurs cas.</span><span class="sxs-lookup"><span data-stu-id="0a844-175">However, the `HttpMessageHandler` objects in the pool are the objects that are reused by multiple `HttpClient` instances.</span></span>

### <a name="use-your-typed-client-classes"></a><span data-ttu-id="0a844-176">Utiliser les classes de client typé</span><span class="sxs-lookup"><span data-stu-id="0a844-176">Use your Typed Client classes</span></span>

<span data-ttu-id="0a844-177">Enfin, une fois que vos classes dactylographie sont mises en œuvre et les ont enregistrées et configurées avec, `AddHttpClient()`vous pouvez les utiliser partout où vous pouvez avoir des services injectés par DI.</span><span class="sxs-lookup"><span data-stu-id="0a844-177">Finally, once you have your typed classes implemented and have them registered and configured with `AddHttpClient()`, you can use them wherever you can have services injected by DI.</span></span> <span data-ttu-id="0a844-178">Par exemple, dans un code de page Razor ou un contrôleur d’une application web MVC, comme dans le code suivant d’eShopOnContainers :</span><span class="sxs-lookup"><span data-stu-id="0a844-178">For example, in a Razor page code or controller of an MVC web app, like in the following code from eShopOnContainers:</span></span>

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

<span data-ttu-id="0a844-179">Jusqu’à présent, le code montré est juste effectuer des demandes régulières Http, mais la «magie» vient dans les sections suivantes où, juste `HttpClient` en ajoutant des politiques et en déléguant les gestionnaires à vos clients personnalisés Typé, toutes les demandes HTTP à faire par se comporter en tenant compte des politiques résilientes telles que les retries avec backoff exponentiel, disjoncteurs, ou tout autre gestionnaire de délégation personnalisée pour implémenter des fonctionnalités de sécurité supplémentaires, comme l’utilisation de jetons auth, ou toute autre fonctionnalité personnalisée.</span><span class="sxs-lookup"><span data-stu-id="0a844-179">Up to this point, the code shown is just performing regular Http requests, but the 'magic' comes in the following sections where, just by adding policies and delegating handlers to your registered Typed Clients, all the HTTP requests to be done by `HttpClient` will behave taking into account resilient policies such as retries with exponential backoff, circuit breakers, or any other custom delegating handler to implement additional security features, like using auth tokens, or any other custom feature.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="0a844-180">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="0a844-180">Additional resources</span></span>

- <span data-ttu-id="0a844-181">**Utilisation de HttpClientFactory dans .NET Core**</span><span class="sxs-lookup"><span data-stu-id="0a844-181">**Using HttpClientFactory in .NET Core**</span></span>  
  [https://docs.microsoft.com/aspnet/core/fundamentals/http-requests](/aspnet/core/fundamentals/http-requests)

- <span data-ttu-id="0a844-182">**Code source httpClientFactory `dotnet/extensions` dans le référentiel GitHub**</span><span class="sxs-lookup"><span data-stu-id="0a844-182">**HttpClientFactory source code in the `dotnet/extensions` GitHub repository**</span></span>  
  <https://github.com/dotnet/extensions/tree/master/src/HttpClientFactory>

- <span data-ttu-id="0a844-183">**Polly (Résilience .NET et bibliothèque de gestion des erreurs temporaires)**</span><span class="sxs-lookup"><span data-stu-id="0a844-183">**Polly (.NET resilience and transient-fault-handling library)**</span></span>  
  <http://www.thepollyproject.org/>
  
- <span data-ttu-id="0a844-184">**Utilisation d’IHttpClientFactory sans injection de dépendance (problème GitHub)**</span><span class="sxs-lookup"><span data-stu-id="0a844-184">**Using IHttpClientFactory without dependency injection (GitHub issue)**</span></span>  
  <https://github.com/dotnet/extensions/issues/1345>

>[!div class="step-by-step"]
><span data-ttu-id="0a844-185">[Suivant précédent](implement-resilient-entity-framework-core-sql-connections.md)
>[Next](implement-http-call-retries-exponential-backoff-polly.md)</span><span class="sxs-lookup"><span data-stu-id="0a844-185">[Previous](implement-resilient-entity-framework-core-sql-connections.md)
[Next](implement-http-call-retries-exponential-backoff-polly.md)</span></span>
