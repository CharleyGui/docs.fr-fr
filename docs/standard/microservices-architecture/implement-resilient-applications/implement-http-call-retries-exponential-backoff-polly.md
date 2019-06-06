---
title: Implémenter de nouvelles tentatives d’appel HTTP avec interruption exponentielle avec Polly
description: Découvrez comment gérer les échecs HTTP avec Polly et HttpClientFactory.
ms.date: 01/07/2019
ms.openlocfilehash: aa500b5525eff9f0bbf91bf98de8945f7c84704f
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66301474"
---
# <a name="implement-http-call-retries-with-exponential-backoff-with-httpclientfactory-and-polly-policies"></a>Implémenter de nouvelles tentatives d’appel HTTP avec interruption exponentielle avec des stratégies Polly et HttpClientFactory

L’approche recommandée pour les nouvelles tentatives avec interruption exponentielle est d’utiliser des bibliothèques .NET plus avancées telles que la [bibliothèque Polly](https://github.com/App-vNext/Polly) open source.

Polly est une bibliothèque .NET qui fournit des fonctionnalités de résilience et de gestion des erreurs temporaires. Vous pouvez implémenter ces fonctionnalités en appliquant des stratégies Polly comme Retry (Nouvelle tentative), Circuit Breaker (Disjoncteur), Bulkhead Isolation (Isolation par cloisonnement), Timeout (Délai d’attente) et Fallback (Alternative de repli). Polly cible la bibliothèque .NET 4.x et .NET Standard 1.0 (qui prend en charge .NET Core).

Toutefois, il peut être complexe d’utiliser la bibliothèque de Polly avec votre propre code personnalisé avec HttpClient. Dans la version d’origine d’eShopOnContainers, il y avait un [module ResilientHttpClient](https://github.com/dotnet-architecture/eShopOnContainers/commit/0c317d56f3c8937f6823cf1b45f5683397274815#diff-e6532e623eb606a0f8568663403e3a10) basé sur Polly. Mais avec la version de [HttpClientFactory](use-httpclientfactory-to-implement-resilient-http-requests.md), la communication HTTP résiliente est devenue beaucoup plus simple à implémenter, si bien que ce bloc de construction a été déprécié dans eShopOnContainers. 

Les étapes suivantes montrent comment vous pouvez utiliser les nouvelles tentatives Http avec Polly intégré dans HttpClientFactory, ce qui est expliqué dans la section précédente.

**Référencer les packages ASP.NET Core 2.2**

`HttpClientFactory` est disponible depuis .NET Core 2.1. Toutefois nous vous recommandons d’utiliser les derniers packages ASP.NET Core 2.2 à partir de NuGet dans votre projet. Vous avez généralement besoin du métapackage `AspNetCore` et du package d’extension `Microsoft.Extensions.Http.Polly`.

**Configurer un client avec la stratégie de nouvelle tentative de Polly, dans Startup**

Comme indiqué dans les sections précédentes, vous devez définir une configuration de client nommé ou typé HttpClient dans votre méthode Startup.ConfigureServices(...) standard, mais maintenant, vous ajoutez du code incrémentiel qui spécifie la stratégie pour les nouvelles tentatives Http avec interruption exponentielle, comme ci-dessous :

```csharp
//ConfigureServices()  - Startup.cs
services.AddHttpClient<IBasketService, BasketService>()
        .SetHandlerLifetime(TimeSpan.FromMinutes(5))  //Set lifetime to five minutes
        .AddPolicyHandler(GetRetryPolicy());
```

La méthode **AddPolicyHandler()** ajoute des stratégies aux objets `HttpClient` que vous utiliserez. Dans ce cas, elle ajoute une stratégie de Polly pour les nouvelles tentatives Http avec interruption exponentielle.

Afin de bénéficier d’une approche plus modulaire, la stratégie de nouvelle tentative Http peut être définie dans une méthode distincte dans le fichier `Startup.cs`, comme illustré par le code suivant :

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

Avec Polly, vous pouvez définir une stratégie Retry en spécifiant le nombre de nouvelles tentatives, la configuration de l’interruption exponentielle et les actions à effectuer quand une exception HTTP se produit (par exemple, journaliser l’erreur). Dans ce cas, la stratégie est configurée pour essayer six fois avec une nouvelle tentative exponentielle commençant à deux secondes. 

Ainsi, elle effectue six tentatives et le nombre de secondes entre chaque tentative est exponentiel et commence à deux secondes.

## <a name="add-a-jitter-strategy-to-the-retry-policy"></a>Ajouter une stratégie d’instabilité à la stratégie de nouvelle tentative

Une stratégie Nouvelle tentative standard peut avoir un impact sur votre système en cas de fort accès concurrentiel, de haute scalabilité et de contention élevée. Pour surmonter les pointes de nouvelles tentatives similaires provenant de nombreux clients en cas de pannes partielles, une solution de contournement efficace consiste à ajouter une stratégie d’instabilité à la stratégie/l’algorithme de nouvelle tentative. Cela peut améliorer les performances globales du système de bout en bout en ajoutant le caractère aléatoire à l’interruption exponentielle. Les pointes sont alors réparties quand des problèmes surviennent. Quand vous utilisez une stratégie Polly brute, le code permettant d’implémenter l’instabilité peut ressembler à l’exemple suivant :

```csharp
Random jitterer = new Random(); 
Policy
  .Handle<HttpResponseException>() // etc
  .WaitAndRetry(5,    // exponential back-off plus some jitter
      retryAttempt => TimeSpan.FromSeconds(Math.Pow(2, retryAttempt))  
                    + TimeSpan.FromMilliseconds(jitterer.Next(0, 100)) 
  );
```

## <a name="additional-resources"></a>Ressources supplémentaires

- **Modèle Nouvelle tentative**  
  [https://docs.microsoft.com/azure/architecture/patterns/retry](/azure/architecture/patterns/retry)

- **Polly et HttpClientFactory**  
  <https://github.com/App-vNext/Polly/wiki/Polly-and-HttpClientFactory>

- **Polly (Résilience .NET et bibliothèque de gestion des erreurs temporaires)**  
  <https://github.com/App-vNext/Polly>

- **Marc Brooker. Jitter: Making Things Better With Randomness**  
  <https://brooker.co.za/blog/2015/03/21/backoff.html>

>[!div class="step-by-step"]
>[Précédent](explore-custom-http-call-retries-exponential-backoff.md)
>[Suivant](implement-circuit-breaker-pattern.md)
