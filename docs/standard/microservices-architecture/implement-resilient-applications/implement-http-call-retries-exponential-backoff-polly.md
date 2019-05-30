---
title: Implémenter de nouvelles tentatives d’appel HTTP avec interruption exponentielle avec Polly
description: Découvrez comment gérer les échecs HTTP avec Polly et HttpClientFactory.
ms.date: 01/07/2019
ms.openlocfilehash: 9ffb0d918dc2efdc41d6c2db2e2141d14061b687
ms.sourcegitcommit: 7e129d879ddb42a8b4334eee35727afe3d437952
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66053113"
---
# <a name="implement-http-call-retries-with-exponential-backoff-with-httpclientfactory-and-polly-policies"></a><span data-ttu-id="14ddd-103">Implémenter de nouvelles tentatives d’appel HTTP avec interruption exponentielle avec des stratégies Polly et HttpClientFactory</span><span class="sxs-lookup"><span data-stu-id="14ddd-103">Implement HTTP call retries with exponential backoff with HttpClientFactory and Polly policies</span></span>

<span data-ttu-id="14ddd-104">L’approche recommandée pour les nouvelles tentatives avec interruption exponentielle est d’utiliser des bibliothèques .NET plus avancées telles que la [bibliothèque Polly](https://github.com/App-vNext/Polly) open source.</span><span class="sxs-lookup"><span data-stu-id="14ddd-104">The recommended approach for retries with exponential backoff is to take advantage of more advanced .NET libraries like the open-source [Polly library](https://github.com/App-vNext/Polly).</span></span>

<span data-ttu-id="14ddd-105">Polly est une bibliothèque .NET qui fournit des fonctionnalités de résilience et de gestion des erreurs temporaires.</span><span class="sxs-lookup"><span data-stu-id="14ddd-105">Polly is a .NET library that provides resilience and transient-fault handling capabilities.</span></span> <span data-ttu-id="14ddd-106">Vous pouvez implémenter ces fonctionnalités en appliquant des stratégies Polly comme Retry (Nouvelle tentative), Circuit Breaker (Disjoncteur), Bulkhead Isolation (Isolation par cloisonnement), Timeout (Délai d’attente) et Fallback (Alternative de repli).</span><span class="sxs-lookup"><span data-stu-id="14ddd-106">You can implement those capabilities by applying Polly policies such as Retry, Circuit Breaker, Bulkhead Isolation, Timeout, and Fallback.</span></span> <span data-ttu-id="14ddd-107">Polly cible la bibliothèque .NET 4.x et .NET Standard 1.0 (qui prend en charge .NET Core).</span><span class="sxs-lookup"><span data-stu-id="14ddd-107">Polly targets .NET 4.x and the .NET Standard Library 1.0 (which supports .NET Core).</span></span>

<span data-ttu-id="14ddd-108">Toutefois, il peut être complexe d’utiliser la bibliothèque de Polly avec votre propre code personnalisé avec HttpClient.</span><span class="sxs-lookup"><span data-stu-id="14ddd-108">However, using Polly’s library with your own custom code with HttpClient can be significantly complex.</span></span> <span data-ttu-id="14ddd-109">Dans la version d’origine d’eShopOnContainers, il y avait un [module ResilientHttpClient](https://github.com/dotnet-architecture/eShopOnContainers/commit/0c317d56f3c8937f6823cf1b45f5683397274815#diff-e6532e623eb606a0f8568663403e3a10) basé sur Polly.</span><span class="sxs-lookup"><span data-stu-id="14ddd-109">In the original version of eShopOnContainers, there was a [ResilientHttpClient building-block](https://github.com/dotnet-architecture/eShopOnContainers/commit/0c317d56f3c8937f6823cf1b45f5683397274815#diff-e6532e623eb606a0f8568663403e3a10) based on Polly.</span></span> <span data-ttu-id="14ddd-110">Mais avec la version de [HttpClientFactory](use-httpclientfactory-to-implement-resilient-http-requests.md), la communication HTTP résiliente est devenue beaucoup plus simple à implémenter, si bien que ce bloc de construction a été déprécié dans eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="14ddd-110">But with the release of [HttpClientFactory](use-httpclientfactory-to-implement-resilient-http-requests.md), resilient HTTP communication has become much simpler to implement, so that building-block was deprecated from eShopOnContainers.</span></span> 

<span data-ttu-id="14ddd-111">Les étapes suivantes montrent comment vous pouvez utiliser les nouvelles tentatives Http avec Polly intégré dans HttpClientFactory, ce qui est expliqué dans la section précédente.</span><span class="sxs-lookup"><span data-stu-id="14ddd-111">The following steps show how you can use Http retries with Polly integrated into HttpClientFactory, which is explained in the previous section.</span></span>

<span data-ttu-id="14ddd-112">**Référencer les packages ASP.NET Core 2.2**</span><span class="sxs-lookup"><span data-stu-id="14ddd-112">**Reference the ASP.NET Core 2.2 packages**</span></span>

<span data-ttu-id="14ddd-113">`HttpClientFactory` est disponible depuis .NET Core 2.1. Toutefois nous vous recommandons d’utiliser les derniers packages ASP.NET Core 2.2 à partir de NuGet dans votre projet.</span><span class="sxs-lookup"><span data-stu-id="14ddd-113">`HttpClientFactory` is available since .NET Core 2.1 however we recommend you to use the latest ASP.NET Core 2.2 packages from NuGet in your project.</span></span> <span data-ttu-id="14ddd-114">Vous avez généralement besoin du métapackage `AspNetCore` et du package d’extension `Microsoft.Extensions.Http.Polly`.</span><span class="sxs-lookup"><span data-stu-id="14ddd-114">You typically need the `AspNetCore` metapackage, and the extension package `Microsoft.Extensions.Http.Polly`.</span></span>

<span data-ttu-id="14ddd-115">**Configurer un client avec la stratégie de nouvelle tentative de Polly, dans Startup**</span><span class="sxs-lookup"><span data-stu-id="14ddd-115">**Configure a client with Polly’s Retry policy, in Startup**</span></span>

<span data-ttu-id="14ddd-116">Comme indiqué dans les sections précédentes, vous devez définir une configuration de client nommé ou typé HttpClient dans votre méthode Startup.ConfigureServices(...) standard, mais maintenant, vous ajoutez du code incrémentiel qui spécifie la stratégie pour les nouvelles tentatives Http avec interruption exponentielle, comme ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="14ddd-116">As shown in previous sections, you need to define a named or typed client HttpClient configuration in your standard Startup.ConfigureServices(...) method, but now, you add incremental code specifying the policy for the Http retries with exponential backoff, as below:</span></span>

```csharp
//ConfigureServices()  - Startup.cs
services.AddHttpClient<IBasketService, BasketService>()
        .SetHandlerLifetime(TimeSpan.FromMinutes(5))  //Set lifetime to five minutes
        .AddPolicyHandler(GetRetryPolicy());
```

<span data-ttu-id="14ddd-117">La méthode **AddPolicyHandler()** ajoute des stratégies aux objets `HttpClient` que vous utiliserez.</span><span class="sxs-lookup"><span data-stu-id="14ddd-117">The **AddPolicyHandler()** method is what adds policies to the `HttpClient` objects you'll use.</span></span> <span data-ttu-id="14ddd-118">Dans ce cas, elle ajoute une stratégie de Polly pour les nouvelles tentatives Http avec interruption exponentielle.</span><span class="sxs-lookup"><span data-stu-id="14ddd-118">In this case, it's adding a Polly’s policy for Http Retries with exponential backoff.</span></span>

<span data-ttu-id="14ddd-119">Afin de bénéficier d’une approche plus modulaire, la stratégie de nouvelle tentative Http peut être définie dans une méthode distincte dans le fichier `Startup.cs`, comme illustré par le code suivant :</span><span class="sxs-lookup"><span data-stu-id="14ddd-119">To have a more modular approach, the Http Retry Policy can be defined in a separate method within the `Startup.cs` file, as shown in the following code:</span></span>

```csharp
static IAsyncPolicy<HttpResponseMessage> GetRetryPolicy()
{
    return HttpPolicyExtensions
        .HandleTransientHttpError()
        .OrResult(msg => msg.StatusCode == System.Net.HttpStatusCode.NotFound)
        .WaitAndRetryAsync(6, retryAttempt => TimeSpan.FromSeconds(Math.Pow(2,
                                                                    retryAttempt)));
}
```

<span data-ttu-id="14ddd-120">Avec Polly, vous pouvez définir une stratégie Retry en spécifiant le nombre de nouvelles tentatives, la configuration de l’interruption exponentielle et les actions à effectuer quand une exception HTTP se produit (par exemple, journaliser l’erreur).</span><span class="sxs-lookup"><span data-stu-id="14ddd-120">With Polly, you can define a Retry policy with the number of retries, the exponential backoff configuration, and the actions to take when there's an HTTP exception, such as logging the error.</span></span> <span data-ttu-id="14ddd-121">Dans ce cas, la stratégie est configurée pour essayer six fois avec une nouvelle tentative exponentielle commençant à deux secondes.</span><span class="sxs-lookup"><span data-stu-id="14ddd-121">In this case, the policy is configured to try six times with an exponential retry, starting at two seconds.</span></span> 

<span data-ttu-id="14ddd-122">Ainsi, elle effectue six tentatives et le nombre de secondes entre chaque tentative est exponentiel et commence à deux secondes.</span><span class="sxs-lookup"><span data-stu-id="14ddd-122">so it will try six times and the seconds between each retry will be exponential, starting on two seconds.</span></span>

## <a name="add-a-jitter-strategy-to-the-retry-policy"></a><span data-ttu-id="14ddd-123">Ajouter une stratégie d’instabilité à la stratégie de nouvelle tentative</span><span class="sxs-lookup"><span data-stu-id="14ddd-123">Add a jitter strategy to the retry policy</span></span>

<span data-ttu-id="14ddd-124">Une stratégie Nouvelle tentative standard peut avoir un impact sur votre système en cas de fort accès concurrentiel, de haute scalabilité et de contention élevée.</span><span class="sxs-lookup"><span data-stu-id="14ddd-124">A regular Retry policy can impact your system in cases of high concurrency and scalability and under high contention.</span></span> <span data-ttu-id="14ddd-125">Pour surmonter les pointes de nouvelles tentatives similaires provenant de nombreux clients en cas de pannes partielles, une solution de contournement efficace consiste à ajouter une stratégie d’instabilité à la stratégie/l’algorithme de nouvelle tentative.</span><span class="sxs-lookup"><span data-stu-id="14ddd-125">To overcome peaks of similar retries coming from many clients in case of partial outages, a good workaround is to add a jitter strategy to the retry algorithm/policy.</span></span> <span data-ttu-id="14ddd-126">Cela peut améliorer les performances globales du système de bout en bout en ajoutant le caractère aléatoire à l’interruption exponentielle.</span><span class="sxs-lookup"><span data-stu-id="14ddd-126">This can improve the overall performance of the end-to-end system by adding randomness to the exponential backoff.</span></span> <span data-ttu-id="14ddd-127">Les pointes sont alors réparties quand des problèmes surviennent.</span><span class="sxs-lookup"><span data-stu-id="14ddd-127">This spreads out the spikes when issues arise.</span></span> <span data-ttu-id="14ddd-128">Quand vous utilisez une stratégie Polly brute, le code permettant d’implémenter l’instabilité peut ressembler à l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="14ddd-128">When you use a plain Polly policy, code to implement jitter could look like the following example:</span></span>

```csharp
Random jitterer = new Random(); 
Policy
  .Handle<HttpResponseException>() // etc
  .WaitAndRetry(5,    // exponential back-off plus some jitter
      retryAttempt => TimeSpan.FromSeconds(Math.Pow(2, retryAttempt))  
                    + TimeSpan.FromMilliseconds(jitterer.Next(0, 100)) 
  );
```

## <a name="additional-resources"></a><span data-ttu-id="14ddd-129">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="14ddd-129">Additional resources</span></span>

- <span data-ttu-id="14ddd-130">**Modèle Nouvelle tentative**\\</span><span class="sxs-lookup"><span data-stu-id="14ddd-130">**Retry pattern**\\</span></span>
  [https://docs.microsoft.com/azure/architecture/patterns/retry](/azure/architecture/patterns/retry)

- <span data-ttu-id="14ddd-131">**Polly et HttpClientFactory**\\</span><span class="sxs-lookup"><span data-stu-id="14ddd-131">**Polly and HttpClientFactory**\\</span></span>
  <https://github.com/App-vNext/Polly/wiki/Polly-and-HttpClientFactory>

- <span data-ttu-id="14ddd-132">**Polly (Résilience .NET et bibliothèque de gestion des erreurs temporaires)**\\</span><span class="sxs-lookup"><span data-stu-id="14ddd-132">**Polly (.NET resilience and transient-fault-handling library)**\\</span></span>
  <https://github.com/App-vNext/Polly>

- <span data-ttu-id="14ddd-133">**Marc Brooker. Jitter: Making Things Better With Randomness**\\</span><span class="sxs-lookup"><span data-stu-id="14ddd-133">**Marc Brooker. Jitter: Making Things Better With Randomness**\\</span></span>
  <https://brooker.co.za/blog/2015/03/21/backoff.html>

>[!div class="step-by-step"]
><span data-ttu-id="14ddd-134">[Précédent](explore-custom-http-call-retries-exponential-backoff.md)
>[Suivant](implement-circuit-breaker-pattern.md)</span><span class="sxs-lookup"><span data-stu-id="14ddd-134">[Previous](explore-custom-http-call-retries-exponential-backoff.md)
[Next](implement-circuit-breaker-pattern.md)</span></span>
