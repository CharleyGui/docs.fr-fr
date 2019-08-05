---
title: Explorer de nouvelles tentatives d’appel HTTP personnalisé avec interruption exponentielle
description: Découvrez implémenter de nouvelles tentatives d’appel HTTP avec interruption exponentielle, à partir de zéro, pour gérer les scénarios de défaillance HTTP possibles.
ms.date: 10/16/2018
ms.openlocfilehash: 2b40b73a014faa87d4eb42192c72b5a9b6c8d4fa
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68674706"
---
# <a name="explore-custom-http-call-retries-with-exponential-backoff"></a>Explorer de nouvelles tentatives d’appel HTTP personnalisé avec interruption exponentielle

Pour créer des microservices résilients, vous devez traiter les scénarios possibles de défaillance HTTP. Une façon de gérer ces échecs, quoique déconseillée, consiste à créer votre propre implémentation de nouvelles tentatives avec interruption exponentielle.

**Remarque importante :** cette section montre comment créer votre propre code personnalisé pour implémenter les nouvelles tentatives d’appel HTTP. Toutefois, il est déconseillé de procéder seul et il est préférable d’utiliser des mécanismes plus puissants et fiables, mais simples d’utilisation, tels que `HttpClientFactory` avec Polly, disponible depuis la version .NET Core 2.1. Ces approches recommandées sont expliquées dans les sections suivantes.

Pour commencer, vous pouvez implémenter votre propre code avec une classe utilitaire pour l’interruption exponentielle comme dans [RetryWithExponentialBackoff.cs](https://gist.github.com/CESARDELATORRE/6d7f647b29e55fdc219ee1fd2babb260), et implémenter du code similaire à l’exemple ci-dessous.

```csharp
public sealed class RetryWithExponentialBackoff
{
    private readonly int maxRetries, delayMilliseconds, maxDelayMilliseconds;

    public RetryWithExponentialBackoff(int maxRetries = 50,
        int delayMilliseconds = 200,
        int maxDelayMilliseconds = 2000)
    {
        this.maxRetries = maxRetries;
        this.delayMilliseconds = delayMilliseconds;
        this.maxDelayMilliseconds = maxDelayMilliseconds;
    }

    public async Task RunAsync(Func<Task> func)
    {
        ExponentialBackoff backoff = new ExponentialBackoff(this.maxRetries,
            this.delayMilliseconds,
            this.maxDelayMilliseconds);
        retry:
        try
        {
            await func();
        }
        catch (Exception ex) when (ex is TimeoutException ||
            ex is System.Net.Http.HttpRequestException)
        {
            Debug.WriteLine("Exception raised is: " +
                ex.GetType().ToString() +
                " –Message: " + ex.Message +
                " -- Inner Message: " +
                ex.InnerException.Message);
            await backoff.Delay();
            goto retry;
        }
    }
}

public struct ExponentialBackoff
{
    private readonly int m_maxRetries, m_delayMilliseconds, m_maxDelayMilliseconds;
    private int m_retries, m_pow;

    public ExponentialBackoff(int maxRetries, int delayMilliseconds,
        int maxDelayMilliseconds)
    {
        m_maxRetries = maxRetries;
        m_delayMilliseconds = delayMilliseconds;
        m_maxDelayMilliseconds = maxDelayMilliseconds;
        m_retries = 0;
        m_pow = 1;
    }

    public Task Delay()
    {
        if (m_retries == m_maxRetries)
        {
            throw new TimeoutException("Max retry attempts exceeded.");
        }
        ++m_retries;
        if (m_retries < 31)
        {
            m_pow = m_pow << 1; // m_pow = Pow(2, m_retries - 1)
        }
        int delay = Math.Min(m_delayMilliseconds * (m_pow - 1) / 2,
            m_maxDelayMilliseconds);
        return Task.Delay(delay);
    }
}
```

L’utilisation de ce code dans une application C\# cliente (un autre microservice client d’API web, une application ASP.NET MVC ou même une application Xamarin C\#) est simple. L’exemple suivant montre comment implémenter ce code à l’aide de la classe HttpClient.

```csharp
public async Task<Catalog> GetCatalogItems(int page,int take, int? brand, int? type)
{
    _apiClient = new HttpClient();
    var itemsQs = $"items?pageIndex={page}&pageSize={take}";
    var filterQs = "";
    var catalogUrl = $"{_remoteServiceBaseUrl}items{filterQs}?pageIndex={page}&pageSize={take}";
    var dataString = "";
    //
    // Using HttpClient with Retry and Exponential Backoff
    //
    var retry = new RetryWithExponentialBackoff();
    await retry.RunAsync(async () =>
    {
        // work with HttpClient call
        dataString = await _apiClient.GetStringAsync(catalogUrl);
    });
    return JsonConvert.DeserializeObject<Catalog>(dataString);
}
```

N’oubliez pas que ce code est approprié uniquement comme preuve de concept. Les sections suivantes expliquent comment utiliser des approches plus sophistiquées mais plus simples, à l’aide de HttpClientFactory. HttpClientFactory est disponible depuis la version .NET Core 2.1 avec des bibliothèques à résilience éprouvée, comme Polly.

>[!div class="step-by-step"]
>[Précédent](implement-resilient-entity-framework-core-sql-connections.md)
>[Suivant](use-httpclientfactory-to-implement-resilient-http-requests.md)
