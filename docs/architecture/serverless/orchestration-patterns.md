---
title: Modèles d’orchestration-applications sans serveur
description: Azure durable Functions PR
author: cecilphillip
ms.author: cephilli
ms.date: 06/26/2018
ms.openlocfilehash: 6c5f6aaedbc13c47289e102bb59f7b066525b107
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91171661"
---
# <a name="orchestration-patterns"></a>Modèles d’orchestration

Durable Functions facilite la création de flux de travail avec état composés d’activités discrètes, longues et exécutées dans un environnement sans serveur. Étant donné que Durable Functions pouvez suivre la progression de vos flux de travail et les points de contrôle périodiquement de l’historique d’exécution, il se prête à implémenter des modèles intéressants.

## <a name="function-chaining"></a>Chaînage de fonctions

Dans un processus séquentiel classique, les activités doivent s’exécuter une après l’autre dans un ordre particulier. Si vous le souhaitez, l’activité à venir peut nécessiter une sortie de la fonction précédente. Cette dépendance sur l’ordre des activités crée une chaîne de fonctions d’exécution.

L’avantage de l’utilisation de Durable Functions pour implémenter ce modèle de flux de travail vient de sa capacité à effectuer des points de contrôle. Si le serveur tombe en panne, le délai d’expiration du réseau ou un autre problème se produit, les fonctions durables peuvent reprendre à partir du dernier état connu et poursuivre l’exécution de votre flux de travail même si celui-ci se trouve sur un autre serveur.

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

Dans l’exemple de code précédent, la `CallActivityAsync` fonction est chargée d’exécuter une activité donnée sur une machine virtuelle dans le centre de données. Lorsque await retourne et que la tâche sous-jacente se termine, l’exécution est enregistrée dans la table d’historique. Le code de la fonction d’orchestrateur peut utiliser l’une des constructions familières de la bibliothèque parallèle de tâches et des mots clés Async/await.

Le code suivant est un exemple simplifié de ce à quoi la `ProcessPayment` méthode peut ressembler :

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

## <a name="asynchronous-http-apis"></a>API HTTP asynchrones

Dans certains cas, les flux de travail peuvent contenir des activités qui prennent une durée relativement longue. Imaginez un processus qui lance la sauvegarde des fichiers multimédias dans le stockage d’objets BLOB. Selon la taille et la quantité des fichiers multimédias, le processus de sauvegarde peut prendre plusieurs heures.

Dans ce scénario, la `DurableOrchestrationClient` capacité de vérifier l’état d’un workflow en cours d’exécution devient utile. Lorsque vous utilisez un `HttpTrigger` pour démarrer un flux de travail, la `CreateCheckStatusResponse` méthode peut être utilisée pour retourner une instance de `HttpResponseMessage` . Cette réponse fournit au client un URI dans la charge utile qui peut être utilisé pour vérifier l’état du processus en cours d’exécution.

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

L’exemple de résultat ci-dessous montre la structure de la charge utile de la réponse.

```json
{
    "id": "instanceId",
    "statusQueryGetUri": "http://host/statusUri",
    "sendEventPostUri": "http://host/eventUri",
    "terminatePostUri": "http://host/terminateUri"
}
```

À l’aide de votre client HTTP préféré, vous pouvez obtenir des demandes d’accès à l’URI dans statusQueryGetUri pour inspecter l’état du flux de travail en cours d’exécution. La réponse d’État renvoyée doit ressembler au code suivant.

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

À mesure que le processus se poursuit, la réponse d’état passe à **échec** ou **terminé**. En cas de réussite, la propriété de **sortie** de la charge utile contient toutes les données retournées.

## <a name="monitoring"></a>Surveillance

Pour les tâches répétitives simples, Azure Functions fournit le `TimerTrigger` qui peut être planifié en fonction d’une expression cron. La minuterie fonctionne bien pour les tâches simples à courte durée de vie, mais il peut y avoir des scénarios dans lesquels une planification plus flexible est nécessaire. Ce scénario se présente lorsque le modèle de surveillance et le Durable Functions peuvent vous aider.

Durable Functions permet des intervalles de planification flexibles, la gestion de la durée de vie et la création de plusieurs processus d’analyse à partir d’une seule fonction d’orchestration. Un cas d’utilisation de cette fonctionnalité peut consister à créer des observateurs pour les modifications de cours d’action qui se terminent une fois qu’un certain seuil est atteint.

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

`DurableOrchestrationContext`la `CreateTimer` méthode de définit la planification de l’appel suivant de la boucle pour vérifier les modifications du cours de l’action. `DurableOrchestrationContext` a également une `CurrentUtcDateTime` propriété pour obtenir la valeur DateTime actuelle en heure UTC. Il est préférable d’utiliser cette propriété au lieu de `DateTime.UtcNow` , car elle est facilement factice pour le test.

## <a name="recommended-resources"></a>Ressources recommandées

- [Azure Durable Functions](/azure/azure-functions/durable-functions-overview)
- [Tests unitaires dans .NET Core et .NET Standard](../../core/testing/index.md)

>[!div class="step-by-step"]
>[Précédent](durable-azure-functions.md) 
> [Suivant](serverless-business-scenarios.md)
