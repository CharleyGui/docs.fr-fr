---
title: Modèles d’orchestration - Applications sans serveur
description: Azure Fonctions durables pr
author: cecilphillip
ms.author: cephilli
ms.date: 06/26/2018
ms.openlocfilehash: 2bd81c29e727254af6c8ecf39ee4bfef1f39d009
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72522636"
---
# <a name="orchestration-patterns"></a>Modèles d’orchestration

Durable Functions facilite la création de flux de travail majestueux qui sont composés d’activités discrètes et de longue durée dans un environnement sans serveur. Étant donné que les fonctions durables peuvent suivre l’évolution de vos flux de travail et des points de contrôle périodiques de l’historique d’exécution, il se prête à la mise en œuvre de certains modèles intéressants.

## <a name="function-chaining"></a>Chaînage de fonctions

Dans un processus séquentiel typique, les activités doivent s’exécuter l’une après l’autre dans un ordre particulier. En option, l’activité à venir peut nécessiter une certaine sortie de la fonction précédente. Cette dépendance à l’ordre des activités crée une chaîne de fonctions d’exécution.

L’avantage d’utiliser les fonctions durables pour mettre en œuvre ce modèle de flux de travail vient de sa capacité à faire le contrôle. Si le serveur se bloque, que le réseau s’évanouit ou qu’un autre problème se produit, les fonctions durables peuvent reprendre à partir du dernier état connu et continuer à exécuter votre flux de travail même si c’est sur un autre serveur.

```csharp
[FunctionName("PlaceOrder")]
public static async Task<string> PlaceOrder([OrchestrationTrigger] DurableOrchestrationContext context)
{
    OrderRequestData orderData = context.GetInput<OrderRequestData>();

    await context.CallActivityAsync<bool>("CheckAndReserveInventory", orderData);
    await context.CallActivityAsync<bool>("ProcessPayment", orderData);

    string trackingNumber = await context.CallActivityAsync<string>("ScheduleShipping", orderData);
    await context.CallActivityAsync<string>("EmailCustomer", trackingNumber);

    return trackingNumber;
}
```

Dans l’échantillon de `CallActivityAsync` code précédent, la fonction est responsable de l’exécution d’une activité donnée sur une machine virtuelle dans le centre de données. Lorsque l’attente sera de retour et que la tâche sous-jacente sera terminée, l’exécution sera enregistrée au tableau d’histoire. Le code de la fonction orchestrateur peut faire usage de l’une des constructions familières de la Bibliothèque parallèle de tâches et des mots-clés async/await.

Le code suivant est un `ProcessPayment` exemple simplifié de ce à quoi la méthode peut ressembler :

```csharp
[FunctionName("ProcessPayment")]
public static bool ProcessPayment([ActivityTrigger] DurableActivityContext context)
{
    OrderRequestData orderData = context.GetInput<OrderRequestData>();

    ApplyCoupons(orderData);
    if(IssuePaymentRequest(orderData)) {
        return true;
    }

    return false;
}
```

## <a name="asynchronous-http-apis"></a>API HTTP asynchrone

Dans certains cas, les flux de travail peuvent contenir des activités qui prennent un délai relativement long. Imaginez un processus qui donne le coup d’envoi de la sauvegarde des fichiers multimédias dans le stockage blob. Selon la taille et la quantité des fichiers multimédias, ce processus de sauvegarde peut prendre des heures.

Dans ce scénario, la `DurableOrchestrationClient`capacité de «vérifier l’état d’un flux de travail en cours d’exécution devient utile. Lors de `HttpTrigger` l’utilisation d’un `CreateCheckStatusResponse` flux de travail pour `HttpResponseMessage`démarrer un flux de travail, la méthode peut être utilisée pour retourner une instance de . Cette réponse fournit au client un URI dans la charge utile qui peut être utilisée pour vérifier l’état du processus d’exécution.

```csharp
[FunctionName("OrderWorkflow")]
public static async Task<HttpResponseMessage> Run(
    [HttpTrigger(AuthorizationLevel.Function, "POST")]HttpRequestMessage req,
    [OrchestrationClient ] DurableOrchestrationClient orchestrationClient)
{
    OrderRequestData data = await req.Content.ReadAsAsync<OrderRequestData>();

    string instanceId = await orchestrationClient.StartNewAsync("PlaceOrder", data);

    return orchestrationClient.CreateCheckStatusResponse(req, instanceId);
}
```

Le résultat de l’échantillon ci-dessous montre la structure de la charge utile de réponse.

```json
{
    "id": "instanceId",
    "statusQueryGetUri": "http://host/statusUri",
    "sendEventPostUri": "http://host/eventUri",
    "terminatePostUri": "http://host/terminateUri"
}
```

À l’aide de votre client HTTP préféré, les demandes GET peuvent être faites à l’URI dans statusQueryGetUri pour inspecter l’état du flux de travail en cours d’exécution. La réponse de statut retournée doit ressembler au code suivant.

```json
{
    "runtimeStatus": "Running",
    "input": {
        "$type": "DurableFunctionsDemos.OrderRequestData, DurableFunctionsDemos"
    },
    "output": null,
    "createdTime": "2018-01-01T00:22:05Z",
    "lastUpdatedTime": "2018-01-01T00:22:09Z"
}
```

Au fur et à mesure que le processus se poursuivra, la réponse au statut changera pour **l’échec** ou **la fin**. Une fois la propriété de **sortie** de la charge utile qui sera complétée, elle contiendra toutes les données retournées.

## <a name="monitoring"></a>Surveillance

Pour des tâches récurrentes simples, `TimerTrigger` Azure Functions fournit le qui peut être programmé en fonction d’une expression CRON. La minuterie fonctionne bien pour des tâches simples et de courte durée, mais il peut y avoir des scénarios où une planification plus flexible est nécessaire. Ce scénario est lorsque le modèle de surveillance et les fonctions durables peuvent aider.

Les fonctions durables permettent des intervalles de planification flexibles, une gestion à vie et la création de processus de moniteur multiples à partir d’une seule fonction d’orchestration. Un cas d’utilisation pour cette fonctionnalité pourrait être de créer des observateurs pour les changements de prix des actions qui complètent une fois qu’un certain seuil est atteint.

```csharp
[FunctionName("CheckStockPrice")]
public static async Task CheckStockPrice([OrchestrationTrigger] DurableOrchestrationContext context)
{
    StockWatcherInfo stockInfo = context.GetInput<StockWatcherInfo>();
    const int checkIntervalSeconds = 120;
    StockPrice initialStockPrice = null;

    DateTime fireAt;
    DateTime exitTime = context.CurrentUtcDateTime.Add(stockInfo.TimeLimit);

    while (context.CurrentUtcDateTime < exitTime)
    {
        StockPrice currentStockPrice = await context.CallActivityAsync<StockPrice>("GetStockPrice", stockInfo);

        if (initialStockPrice == null)
        {
            initialStockPrice = currentStockPrice;
            fireAt = context.CurrentUtcDateTime.AddSeconds(checkIntervalSeconds);
            await context.CreateTimer(fireAt, CancellationToken.None);
            continue;
        }

        decimal percentageChange = (initialStockPrice.Price - currentStockPrice.Price) /
                               ((initialStockPrice.Price + currentStockPrice.Price) / 2);

        if (Math.Abs(percentageChange) >= stockInfo.PercentageChange)
        {
            // Change threshold detected
            await context.CallActivityAsync("NotifyStockPercentageChange", currentStockPrice);
            break;
        }

        // Sleep til next polling interval
        fireAt = context.CurrentUtcDateTime.AddSeconds(checkIntervalSeconds);
        await context.CreateTimer(fireAt, CancellationToken.None);
    }
}
```

`DurableOrchestrationContext`la `CreateTimer` méthode de l’action établit le calendrier de la prochaine invocation de la boucle pour vérifier les changements de cours de l’action. `DurableOrchestrationContext`a également `CurrentUtcDateTime` une propriété pour obtenir la valeur actuelle DateTime en UTC. Il est préférable d’utiliser `DateTime.UtcNow` cette propriété au lieu de parce qu’il est facilement moqué pour les tests.

## <a name="recommended-resources"></a>Ressources recommandées

- [Azure Durable Functions](https://docs.microsoft.com/azure/azure-functions/durable-functions-overview)
- [Tests unitaires dans .NET Core et .NET Standard](../../core/testing/index.md)

>[!div class="step-by-step"]
>[Suivant précédent](durable-azure-functions.md)
>[Next](serverless-business-scenarios.md)
