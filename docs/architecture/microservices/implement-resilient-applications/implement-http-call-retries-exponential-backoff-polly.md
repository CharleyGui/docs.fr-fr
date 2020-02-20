---
title: Implémenter de nouvelles tentatives d’appel HTTP avec interruption exponentielle avec Polly
description: Découvrez comment gérer les échecs HTTP avec Polly et HttpClientFactory.
ms.date: 01/30/2020
ms.openlocfilehash: 60943360c9674f93b246b37b2667b48dab659e0e
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77502665"
---
# <a name="implement-http-call-retries-with-exponential-backoff-with-httpclientfactory-and-polly-policies"></a><span data-ttu-id="5ac06-103">Implémenter de nouvelles tentatives d’appel HTTP avec interruption exponentielle avec des stratégies Polly et HttpClientFactory</span><span class="sxs-lookup"><span data-stu-id="5ac06-103">Implement HTTP call retries with exponential backoff with HttpClientFactory and Polly policies</span></span>

<span data-ttu-id="5ac06-104">L’approche recommandée pour les nouvelles tentatives avec interruption exponentielle est d’utiliser des bibliothèques .NET plus avancées telles que la [bibliothèque Polly](https://github.com/App-vNext/Polly) open source.</span><span class="sxs-lookup"><span data-stu-id="5ac06-104">The recommended approach for retries with exponential backoff is to take advantage of more advanced .NET libraries like the open-source [Polly library](https://github.com/App-vNext/Polly).</span></span>

<span data-ttu-id="5ac06-105">Polly est une bibliothèque .NET qui fournit des fonctionnalités de résilience et de gestion des erreurs temporaires.</span><span class="sxs-lookup"><span data-stu-id="5ac06-105">Polly is a .NET library that provides resilience and transient-fault handling capabilities.</span></span> <span data-ttu-id="5ac06-106">Vous pouvez implémenter ces fonctionnalités en appliquant des stratégies Polly comme Retry (Nouvelle tentative), Circuit Breaker (Disjoncteur), Bulkhead Isolation (Isolation par cloisonnement), Timeout (Délai d’attente) et Fallback (Alternative de repli).</span><span class="sxs-lookup"><span data-stu-id="5ac06-106">You can implement those capabilities by applying Polly policies such as Retry, Circuit Breaker, Bulkhead Isolation, Timeout, and Fallback.</span></span> <span data-ttu-id="5ac06-107">Polly cible les .NET Framework 4. x et .NET Standard 1,0, 1,1 et 2,0 (qui prend en charge .NET Core).</span><span class="sxs-lookup"><span data-stu-id="5ac06-107">Polly targets .NET Framework 4.x and .NET Standard 1.0, 1.1, and 2.0 (which supports .NET Core).</span></span>

<span data-ttu-id="5ac06-108">Toutefois, l’écriture de votre propre code personnalisé pour utiliser la bibliothèque Polly avec HttpClient peut être considérablement complexe.</span><span class="sxs-lookup"><span data-stu-id="5ac06-108">However, writing your own custom code to use Polly’s library with HttpClient can be significantly complex.</span></span> <span data-ttu-id="5ac06-109">Dans la version d’origine d’eShopOnContainers, il y avait un [module ResilientHttpClient](https://github.com/dotnet-architecture/eShopOnContainers/commit/0c317d56f3c8937f6823cf1b45f5683397274815#diff-e6532e623eb606a0f8568663403e3a10) basé sur Polly.</span><span class="sxs-lookup"><span data-stu-id="5ac06-109">In the original version of eShopOnContainers, there was a [ResilientHttpClient building-block](https://github.com/dotnet-architecture/eShopOnContainers/commit/0c317d56f3c8937f6823cf1b45f5683397274815#diff-e6532e623eb606a0f8568663403e3a10) based on Polly.</span></span> <span data-ttu-id="5ac06-110">Toutefois, avec la sortie de [HttpClientFactory](use-httpclientfactory-to-implement-resilient-http-requests.md), l’implémentation d’une communication http résiliente avec Polly est devenue nettement plus simple, de sorte que le bloc de construction était déconseillé de eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="5ac06-110">But with the release of [HttpClientFactory](use-httpclientfactory-to-implement-resilient-http-requests.md), implementing resilient HTTP communication with Polly has become much simpler, so that building-block was deprecated from eShopOnContainers.</span></span>

<span data-ttu-id="5ac06-111">Les étapes suivantes montrent comment vous pouvez utiliser les nouvelles tentatives Http avec Polly intégré dans HttpClientFactory, ce qui est expliqué dans la section précédente.</span><span class="sxs-lookup"><span data-stu-id="5ac06-111">The following steps show how you can use Http retries with Polly integrated into HttpClientFactory, which is explained in the previous section.</span></span>

<span data-ttu-id="5ac06-112">**Référencer les packages ASP.NET Core 3,1**</span><span class="sxs-lookup"><span data-stu-id="5ac06-112">**Reference the ASP.NET Core 3.1 packages**</span></span>

<span data-ttu-id="5ac06-113">`HttpClientFactory` est disponible depuis .NET Core 2,1. Toutefois, nous vous recommandons d’utiliser les derniers packages ASP.NET Core 3,1 de NuGet dans votre projet.</span><span class="sxs-lookup"><span data-stu-id="5ac06-113">`HttpClientFactory` is available since .NET Core 2.1 however we recommend you to use the latest ASP.NET Core 3.1 packages from NuGet in your project.</span></span> <span data-ttu-id="5ac06-114">En général, vous devez également référencer le package d’extension `Microsoft.Extensions.Http.Polly`.</span><span class="sxs-lookup"><span data-stu-id="5ac06-114">You typically also need to reference the extension package `Microsoft.Extensions.Http.Polly`.</span></span>

<span data-ttu-id="5ac06-115">**Configurer un client avec la stratégie de nouvelle tentative de Polly, dans Startup**</span><span class="sxs-lookup"><span data-stu-id="5ac06-115">**Configure a client with Polly’s Retry policy, in Startup**</span></span>

<span data-ttu-id="5ac06-116">Comme indiqué dans les sections précédentes, vous devez définir une configuration de client nommé ou typé HttpClient dans votre méthode Startup.ConfigureServices(...) standard, mais maintenant, vous ajoutez du code incrémentiel qui spécifie la stratégie pour les nouvelles tentatives Http avec interruption exponentielle, comme ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="5ac06-116">As shown in previous sections, you need to define a named or typed client HttpClient configuration in your standard Startup.ConfigureServices(...) method, but now, you add incremental code specifying the policy for the Http retries with exponential backoff, as below:</span></span>

```csharp
//ConfigureServices()  - Startup.cs
services.AddHttpClient<IBasketService, BasketService>()
        .SetHandlerLifetime(TimeSpan.FromMinutes(5))  //Set lifetime to five minutes
        .AddPolicyHandler(GetRetryPolicy());
```

<span data-ttu-id="5ac06-117">La méthode **AddPolicyHandler()** ajoute des stratégies aux objets `HttpClient` que vous utiliserez.</span><span class="sxs-lookup"><span data-stu-id="5ac06-117">The **AddPolicyHandler()** method is what adds policies to the `HttpClient` objects you'll use.</span></span> <span data-ttu-id="5ac06-118">Dans ce cas, elle ajoute une stratégie de Polly pour les nouvelles tentatives Http avec interruption exponentielle.</span><span class="sxs-lookup"><span data-stu-id="5ac06-118">In this case, it's adding a Polly’s policy for Http Retries with exponential backoff.</span></span>

<span data-ttu-id="5ac06-119">Afin de bénéficier d’une approche plus modulaire, la stratégie de nouvelle tentative Http peut être définie dans une méthode distincte dans le fichier `Startup.cs`, comme illustré par le code suivant :</span><span class="sxs-lookup"><span data-stu-id="5ac06-119">To have a more modular approach, the Http Retry Policy can be defined in a separate method within the `Startup.cs` file, as shown in the following code:</span></span>

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

<span data-ttu-id="5ac06-120">Avec Polly, vous pouvez définir une stratégie Retry en spécifiant le nombre de nouvelles tentatives, la configuration de l’interruption exponentielle et les actions à effectuer quand une exception HTTP se produit (par exemple, journaliser l’erreur).</span><span class="sxs-lookup"><span data-stu-id="5ac06-120">With Polly, you can define a Retry policy with the number of retries, the exponential backoff configuration, and the actions to take when there's an HTTP exception, such as logging the error.</span></span> <span data-ttu-id="5ac06-121">Dans ce cas, la stratégie est configurée pour essayer six fois avec une nouvelle tentative exponentielle commençant à deux secondes.</span><span class="sxs-lookup"><span data-stu-id="5ac06-121">In this case, the policy is configured to try six times with an exponential retry, starting at two seconds.</span></span>

## <a name="add-a-jitter-strategy-to-the-retry-policy"></a><span data-ttu-id="5ac06-122">Ajouter une stratégie d’instabilité à la stratégie de nouvelle tentative</span><span class="sxs-lookup"><span data-stu-id="5ac06-122">Add a jitter strategy to the retry policy</span></span>

<span data-ttu-id="5ac06-123">Une stratégie Nouvelle tentative standard peut avoir un impact sur votre système en cas de fort accès concurrentiel, de haute scalabilité et de contention élevée.</span><span class="sxs-lookup"><span data-stu-id="5ac06-123">A regular Retry policy can impact your system in cases of high concurrency and scalability and under high contention.</span></span> <span data-ttu-id="5ac06-124">Pour surmonter les pointes de nouvelles tentatives similaires provenant de nombreux clients en cas de pannes partielles, une solution de contournement efficace consiste à ajouter une stratégie d’instabilité à la stratégie/l’algorithme de nouvelle tentative.</span><span class="sxs-lookup"><span data-stu-id="5ac06-124">To overcome peaks of similar retries coming from many clients in case of partial outages, a good workaround is to add a jitter strategy to the retry algorithm/policy.</span></span> <span data-ttu-id="5ac06-125">Cela peut améliorer les performances globales du système de bout en bout en ajoutant le caractère aléatoire à l’interruption exponentielle.</span><span class="sxs-lookup"><span data-stu-id="5ac06-125">This can improve the overall performance of the end-to-end system by adding randomness to the exponential backoff.</span></span> <span data-ttu-id="5ac06-126">Les pointes sont alors réparties quand des problèmes surviennent.</span><span class="sxs-lookup"><span data-stu-id="5ac06-126">This spreads out the spikes when issues arise.</span></span> <span data-ttu-id="5ac06-127">Le principe est illustré dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="5ac06-127">The principle is illustrated by the following example:</span></span>

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

<span data-ttu-id="5ac06-128">Polly fournit des algorithmes d’instabilité prêts pour la production via le site Web du projet.</span><span class="sxs-lookup"><span data-stu-id="5ac06-128">Polly provides production-ready jitter algorithms via the project website.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="5ac06-129">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="5ac06-129">Additional resources</span></span>

- <span data-ttu-id="5ac06-130">**Modèle Nouvelle tentative**</span><span class="sxs-lookup"><span data-stu-id="5ac06-130">**Retry pattern**</span></span>  
  [https://docs.microsoft.com/azure/architecture/patterns/retry](/azure/architecture/patterns/retry)

- <span data-ttu-id="5ac06-131">**Polly et HttpClientFactory**</span><span class="sxs-lookup"><span data-stu-id="5ac06-131">**Polly and HttpClientFactory**</span></span>  
  <https://github.com/App-vNext/Polly/wiki/Polly-and-HttpClientFactory>

- <span data-ttu-id="5ac06-132">**Polly (Résilience .NET et bibliothèque de gestion des erreurs temporaires)**</span><span class="sxs-lookup"><span data-stu-id="5ac06-132">**Polly (.NET resilience and transient-fault-handling library)**</span></span>  
  <https://github.com/App-vNext/Polly>

- <span data-ttu-id="5ac06-133">**Polly : réessayer avec un bougé**</span><span class="sxs-lookup"><span data-stu-id="5ac06-133">**Polly: Retry with Jitter**</span></span>  
  <https://github.com/App-vNext/Polly/wiki/Retry-with-jitter>

- <span data-ttu-id="5ac06-134">**Marc Brooker. Gigue : améliorer les choses avec le caractère aléatoire**</span><span class="sxs-lookup"><span data-stu-id="5ac06-134">**Marc Brooker. Jitter: Making Things Better With Randomness**</span></span>  
  <https://brooker.co.za/blog/2015/03/21/backoff.html>

>[!div class="step-by-step"]
><span data-ttu-id="5ac06-135">[Précédent](explore-custom-http-call-retries-exponential-backoff.md)
>[Suivant](implement-circuit-breaker-pattern.md)</span><span class="sxs-lookup"><span data-stu-id="5ac06-135">[Previous](explore-custom-http-call-retries-exponential-backoff.md)
[Next](implement-circuit-breaker-pattern.md)</span></span>
