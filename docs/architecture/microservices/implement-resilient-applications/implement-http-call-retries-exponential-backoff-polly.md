---
title: Implémenter de nouvelles tentatives d’appel HTTP avec interruption exponentielle avec Polly
description: Apprenez à gérer les échecs DE HTTP avec Polly et IHttpClientFactory.
ms.date: 03/03/2020
ms.openlocfilehash: 49396dd545a05699278254474c77acf1483e0e0c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78846794"
---
# <a name="implement-http-call-retries-with-exponential-backoff-with-ihttpclientfactory-and-polly-policies"></a><span data-ttu-id="3c5ae-103">Mettre en œuvre les retries d’appels HTTP avec des backoff exponentiels avec les politiques IHttpClientFactory et Polly</span><span class="sxs-lookup"><span data-stu-id="3c5ae-103">Implement HTTP call retries with exponential backoff with IHttpClientFactory and Polly policies</span></span>

<span data-ttu-id="3c5ae-104">L’approche recommandée pour les nouvelles tentatives avec interruption exponentielle est d’utiliser des bibliothèques .NET plus avancées telles que la [bibliothèque Polly](https://github.com/App-vNext/Polly) open source.</span><span class="sxs-lookup"><span data-stu-id="3c5ae-104">The recommended approach for retries with exponential backoff is to take advantage of more advanced .NET libraries like the open-source [Polly library](https://github.com/App-vNext/Polly).</span></span>

<span data-ttu-id="3c5ae-105">Polly est une bibliothèque .NET qui fournit des fonctionnalités de résilience et de gestion des erreurs temporaires.</span><span class="sxs-lookup"><span data-stu-id="3c5ae-105">Polly is a .NET library that provides resilience and transient-fault handling capabilities.</span></span> <span data-ttu-id="3c5ae-106">Vous pouvez implémenter ces fonctionnalités en appliquant des stratégies Polly comme Retry (Nouvelle tentative), Circuit Breaker (Disjoncteur), Bulkhead Isolation (Isolation par cloisonnement), Timeout (Délai d’attente) et Fallback (Alternative de repli).</span><span class="sxs-lookup"><span data-stu-id="3c5ae-106">You can implement those capabilities by applying Polly policies such as Retry, Circuit Breaker, Bulkhead Isolation, Timeout, and Fallback.</span></span> <span data-ttu-id="3c5ae-107">Polly targets .NET Framework 4.x and .NET Standard 1.0, 1.1, and 2.0 (which supports .NET Core).</span><span class="sxs-lookup"><span data-stu-id="3c5ae-107">Polly targets .NET Framework 4.x and .NET Standard 1.0, 1.1, and 2.0 (which supports .NET Core).</span></span>

<span data-ttu-id="3c5ae-108">Les étapes suivantes montrent comment vous pouvez utiliser `IHttpClientFactory`http retries avec Polly intégré dans , qui est expliqué dans la section précédente.</span><span class="sxs-lookup"><span data-stu-id="3c5ae-108">The following steps show how you can use Http retries with Polly integrated into `IHttpClientFactory`, which is explained in the previous section.</span></span>

<span data-ttu-id="3c5ae-109">**Référence des forfaits ASP.NET Core 3.1**</span><span class="sxs-lookup"><span data-stu-id="3c5ae-109">**Reference the ASP.NET Core 3.1 packages**</span></span>

<span data-ttu-id="3c5ae-110">`IHttpClientFactory`est disponible depuis .NET Core 2.1 mais nous vous recommandons d’utiliser les derniers paquets ASP.NET Core 3.1 de NuGet dans votre projet.</span><span class="sxs-lookup"><span data-stu-id="3c5ae-110">`IHttpClientFactory` is available since .NET Core 2.1 however we recommend you to use the latest ASP.NET Core 3.1 packages from NuGet in your project.</span></span> <span data-ttu-id="3c5ae-111">Vous avez généralement également besoin `Microsoft.Extensions.Http.Polly`de référencer le paquet d’extension .</span><span class="sxs-lookup"><span data-stu-id="3c5ae-111">You typically also need to reference the extension package `Microsoft.Extensions.Http.Polly`.</span></span>

<span data-ttu-id="3c5ae-112">**Configurer un client avec la politique Retry de Polly, en Startup**</span><span class="sxs-lookup"><span data-stu-id="3c5ae-112">**Configure a client with Polly's Retry policy, in Startup**</span></span>

<span data-ttu-id="3c5ae-113">Comme indiqué dans les sections précédentes, vous devez définir une configuration de client nommé ou typé HttpClient dans votre méthode Startup.ConfigureServices(...) standard, mais maintenant, vous ajoutez du code incrémentiel qui spécifie la stratégie pour les nouvelles tentatives Http avec interruption exponentielle, comme ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="3c5ae-113">As shown in previous sections, you need to define a named or typed client HttpClient configuration in your standard Startup.ConfigureServices(...) method, but now, you add incremental code specifying the policy for the Http retries with exponential backoff, as below:</span></span>

```csharp
//ConfigureServices()  - Startup.cs
services.AddHttpClient<IBasketService, BasketService>()
        .SetHandlerLifetime(TimeSpan.FromMinutes(5))  //Set lifetime to five minutes
        .AddPolicyHandler(GetRetryPolicy());
```

<span data-ttu-id="3c5ae-114">La méthode **AddPolicyHandler()** ajoute des stratégies aux objets `HttpClient` que vous utiliserez.</span><span class="sxs-lookup"><span data-stu-id="3c5ae-114">The **AddPolicyHandler()** method is what adds policies to the `HttpClient` objects you'll use.</span></span> <span data-ttu-id="3c5ae-115">Dans ce cas, il s’agit d’ajouter une politique de Polly pour Http Retries avec un backoff exponentiel.</span><span class="sxs-lookup"><span data-stu-id="3c5ae-115">In this case, it's adding a Polly's policy for Http Retries with exponential backoff.</span></span>

<span data-ttu-id="3c5ae-116">Afin de bénéficier d’une approche plus modulaire, la stratégie de nouvelle tentative Http peut être définie dans une méthode distincte dans le fichier `Startup.cs`, comme illustré par le code suivant :</span><span class="sxs-lookup"><span data-stu-id="3c5ae-116">To have a more modular approach, the Http Retry Policy can be defined in a separate method within the `Startup.cs` file, as shown in the following code:</span></span>

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

<span data-ttu-id="3c5ae-117">Avec Polly, vous pouvez définir une stratégie Retry en spécifiant le nombre de nouvelles tentatives, la configuration de l’interruption exponentielle et les actions à effectuer quand une exception HTTP se produit (par exemple, journaliser l’erreur).</span><span class="sxs-lookup"><span data-stu-id="3c5ae-117">With Polly, you can define a Retry policy with the number of retries, the exponential backoff configuration, and the actions to take when there's an HTTP exception, such as logging the error.</span></span> <span data-ttu-id="3c5ae-118">Dans ce cas, la stratégie est configurée pour essayer six fois avec une nouvelle tentative exponentielle commençant à deux secondes.</span><span class="sxs-lookup"><span data-stu-id="3c5ae-118">In this case, the policy is configured to try six times with an exponential retry, starting at two seconds.</span></span>

## <a name="add-a-jitter-strategy-to-the-retry-policy"></a><span data-ttu-id="3c5ae-119">Ajouter une stratégie d’instabilité à la stratégie de nouvelle tentative</span><span class="sxs-lookup"><span data-stu-id="3c5ae-119">Add a jitter strategy to the retry policy</span></span>

<span data-ttu-id="3c5ae-120">Une stratégie Nouvelle tentative standard peut avoir un impact sur votre système en cas de fort accès concurrentiel, de haute scalabilité et de contention élevée.</span><span class="sxs-lookup"><span data-stu-id="3c5ae-120">A regular Retry policy can impact your system in cases of high concurrency and scalability and under high contention.</span></span> <span data-ttu-id="3c5ae-121">Pour surmonter les pointes de nouvelles tentatives similaires provenant de nombreux clients en cas de pannes partielles, une solution de contournement efficace consiste à ajouter une stratégie d’instabilité à la stratégie/l’algorithme de nouvelle tentative.</span><span class="sxs-lookup"><span data-stu-id="3c5ae-121">To overcome peaks of similar retries coming from many clients in case of partial outages, a good workaround is to add a jitter strategy to the retry algorithm/policy.</span></span> <span data-ttu-id="3c5ae-122">Cela peut améliorer les performances globales du système de bout en bout en ajoutant le caractère aléatoire à l’interruption exponentielle.</span><span class="sxs-lookup"><span data-stu-id="3c5ae-122">This can improve the overall performance of the end-to-end system by adding randomness to the exponential backoff.</span></span> <span data-ttu-id="3c5ae-123">Les pointes sont alors réparties quand des problèmes surviennent.</span><span class="sxs-lookup"><span data-stu-id="3c5ae-123">This spreads out the spikes when issues arise.</span></span> <span data-ttu-id="3c5ae-124">Le principe est illustré par l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="3c5ae-124">The principle is illustrated by the following example:</span></span>

```csharp
Random jitterer = new Random();
var retryWithJitterPolicy = HttpPolicyExtensions
    .HandleTransientHttpError()
    .OrResult(msg => msg.StatusCode == System.Net.HttpStatusCode.NotFound)
    .WaitAndRetryAsync(6,    // exponential back-off plus some jitter
        retryAttempt => TimeSpan.FromSeconds(Math.Pow(2, retryAttempt))  
                      + TimeSpan.FromMilliseconds(jitterer.Next(0, 100))
    );
```

<span data-ttu-id="3c5ae-125">Polly fournit des algorithmes de gigue prêts à la production via le site Web du projet.</span><span class="sxs-lookup"><span data-stu-id="3c5ae-125">Polly provides production-ready jitter algorithms via the project website.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="3c5ae-126">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="3c5ae-126">Additional resources</span></span>

- <span data-ttu-id="3c5ae-127">**Modèle Nouvelle tentative**</span><span class="sxs-lookup"><span data-stu-id="3c5ae-127">**Retry pattern**</span></span>  
  [https://docs.microsoft.com/azure/architecture/patterns/retry](/azure/architecture/patterns/retry)

- <span data-ttu-id="3c5ae-128">**Polly et IHttpClientFactory**</span><span class="sxs-lookup"><span data-stu-id="3c5ae-128">**Polly and IHttpClientFactory**</span></span>  
  <https://github.com/App-vNext/Polly/wiki/Polly-and-HttpClientFactory>

- <span data-ttu-id="3c5ae-129">**Polly (Résilience .NET et bibliothèque de gestion des erreurs temporaires)**</span><span class="sxs-lookup"><span data-stu-id="3c5ae-129">**Polly (.NET resilience and transient-fault-handling library)**</span></span>  
  <https://github.com/App-vNext/Polly>

- <span data-ttu-id="3c5ae-130">**Polly: Retry avec Jitter**</span><span class="sxs-lookup"><span data-stu-id="3c5ae-130">**Polly: Retry with Jitter**</span></span>  
  <https://github.com/App-vNext/Polly/wiki/Retry-with-jitter>

- <span data-ttu-id="3c5ae-131">**Marc Brooker. Jitter: Améliorer les choses avec le hasard**</span><span class="sxs-lookup"><span data-stu-id="3c5ae-131">**Marc Brooker. Jitter: Making Things Better With Randomness**</span></span>  
  <https://brooker.co.za/blog/2015/03/21/backoff.html>

>[!div class="step-by-step"]
><span data-ttu-id="3c5ae-132">[Suivant précédent](use-httpclientfactory-to-implement-resilient-http-requests.md)
>[Next](implement-circuit-breaker-pattern.md)</span><span class="sxs-lookup"><span data-stu-id="3c5ae-132">[Previous](use-httpclientfactory-to-implement-resilient-http-requests.md)
[Next](implement-circuit-breaker-pattern.md)</span></span>
