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
# <a name="orchestration-patterns"></a><span data-ttu-id="f0461-103">Modèles d’orchestration</span><span class="sxs-lookup"><span data-stu-id="f0461-103">Orchestration patterns</span></span>

<span data-ttu-id="f0461-104">Durable Functions facilite la création de flux de travail avec état composés d’activités discrètes, longues et exécutées dans un environnement sans serveur.</span><span class="sxs-lookup"><span data-stu-id="f0461-104">Durable Functions makes it easier to create stateful workflows that are composed of discrete, long running activities in a serverless environment.</span></span> <span data-ttu-id="f0461-105">Étant donné que Durable Functions pouvez suivre la progression de vos flux de travail et les points de contrôle périodiquement de l’historique d’exécution, il se prête à implémenter des modèles intéressants.</span><span class="sxs-lookup"><span data-stu-id="f0461-105">Since Durable Functions can track the progress of your workflows and periodically checkpoints the execution history, it lends itself to implementing some interesting patterns.</span></span>

## <a name="function-chaining"></a><span data-ttu-id="f0461-106">Chaînage de fonctions</span><span class="sxs-lookup"><span data-stu-id="f0461-106">Function chaining</span></span>

<span data-ttu-id="f0461-107">Dans un processus séquentiel classique, les activités doivent s’exécuter une après l’autre dans un ordre particulier.</span><span class="sxs-lookup"><span data-stu-id="f0461-107">In a typical sequential process, activities need to execute one after the other in a particular order.</span></span> <span data-ttu-id="f0461-108">Si vous le souhaitez, l’activité à venir peut nécessiter une sortie de la fonction précédente.</span><span class="sxs-lookup"><span data-stu-id="f0461-108">Optionally, the upcoming activity may require some output from the previous function.</span></span> <span data-ttu-id="f0461-109">Cette dépendance sur l’ordre des activités crée une chaîne de fonctions d’exécution.</span><span class="sxs-lookup"><span data-stu-id="f0461-109">This dependency on the ordering of activities creates a function chain of execution.</span></span>

<span data-ttu-id="f0461-110">L’avantage de l’utilisation de Durable Functions pour implémenter ce modèle de flux de travail vient de sa capacité à effectuer des points de contrôle.</span><span class="sxs-lookup"><span data-stu-id="f0461-110">The benefit of using Durable Functions to implement this workflow pattern comes from its ability to do checkpointing.</span></span> <span data-ttu-id="f0461-111">Si le serveur tombe en panne, le délai d’expiration du réseau ou un autre problème se produit, les fonctions durables peuvent reprendre à partir du dernier état connu et poursuivre l’exécution de votre flux de travail même si celui-ci se trouve sur un autre serveur.</span><span class="sxs-lookup"><span data-stu-id="f0461-111">If the server crashes, the network times out or some other issue occurs, Durable functions can resume from the last known state and continue running your workflow even if it's on another server.</span></span>

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

<span data-ttu-id="f0461-112">Dans l’exemple de code précédent, la `CallActivityAsync` fonction est chargée d’exécuter une activité donnée sur une machine virtuelle dans le centre de données.</span><span class="sxs-lookup"><span data-stu-id="f0461-112">In the preceding code sample, the `CallActivityAsync` function is responsible for running a given activity on a virtual machine in the data center.</span></span> <span data-ttu-id="f0461-113">Lorsque await retourne et que la tâche sous-jacente se termine, l’exécution est enregistrée dans la table d’historique.</span><span class="sxs-lookup"><span data-stu-id="f0461-113">When the await returns and the underlying Task completes, the execution will be recorded to the history table.</span></span> <span data-ttu-id="f0461-114">Le code de la fonction d’orchestrateur peut utiliser l’une des constructions familières de la bibliothèque parallèle de tâches et des mots clés Async/await.</span><span class="sxs-lookup"><span data-stu-id="f0461-114">The code in the orchestrator function can make use of any of the familiar constructs of the Task Parallel Library and the async/await keywords.</span></span>

<span data-ttu-id="f0461-115">Le code suivant est un exemple simplifié de ce à quoi la `ProcessPayment` méthode peut ressembler :</span><span class="sxs-lookup"><span data-stu-id="f0461-115">The following code is a simplified example of what the `ProcessPayment` method may look like:</span></span>

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

## <a name="asynchronous-http-apis"></a><span data-ttu-id="f0461-116">API HTTP asynchrones</span><span class="sxs-lookup"><span data-stu-id="f0461-116">Asynchronous HTTP APIs</span></span>

<span data-ttu-id="f0461-117">Dans certains cas, les flux de travail peuvent contenir des activités qui prennent une durée relativement longue.</span><span class="sxs-lookup"><span data-stu-id="f0461-117">In some cases, workflows may contain activities that take a relatively long period of time to complete.</span></span> <span data-ttu-id="f0461-118">Imaginez un processus qui lance la sauvegarde des fichiers multimédias dans le stockage d’objets BLOB.</span><span class="sxs-lookup"><span data-stu-id="f0461-118">Imagine a process that kicks off the backup of media files into blob storage.</span></span> <span data-ttu-id="f0461-119">Selon la taille et la quantité des fichiers multimédias, le processus de sauvegarde peut prendre plusieurs heures.</span><span class="sxs-lookup"><span data-stu-id="f0461-119">Depending on the size and quantity of the media files, this backup process may take hours to complete.</span></span>

<span data-ttu-id="f0461-120">Dans ce scénario, la `DurableOrchestrationClient` capacité de vérifier l’état d’un workflow en cours d’exécution devient utile.</span><span class="sxs-lookup"><span data-stu-id="f0461-120">In this scenario, the `DurableOrchestrationClient`'s ability to check the status of a running workflow becomes useful.</span></span> <span data-ttu-id="f0461-121">Lorsque vous utilisez un `HttpTrigger` pour démarrer un flux de travail, la `CreateCheckStatusResponse` méthode peut être utilisée pour retourner une instance de `HttpResponseMessage` .</span><span class="sxs-lookup"><span data-stu-id="f0461-121">When using an `HttpTrigger` to start a workflow, the `CreateCheckStatusResponse` method can be used to return an instance of `HttpResponseMessage`.</span></span> <span data-ttu-id="f0461-122">Cette réponse fournit au client un URI dans la charge utile qui peut être utilisé pour vérifier l’état du processus en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="f0461-122">This response provides the client with a URI in the payload that can be used to check the status of the running process.</span></span>

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

<span data-ttu-id="f0461-123">L’exemple de résultat ci-dessous montre la structure de la charge utile de la réponse.</span><span class="sxs-lookup"><span data-stu-id="f0461-123">The sample result below shows the structure of the response payload.</span></span>

```json
{
    "id": "instanceId",
    "statusQueryGetUri": "http://host/statusUri",
    "sendEventPostUri": "http://host/eventUri",
    "terminatePostUri": "http://host/terminateUri"
}
```

<span data-ttu-id="f0461-124">À l’aide de votre client HTTP préféré, vous pouvez obtenir des demandes d’accès à l’URI dans statusQueryGetUri pour inspecter l’état du flux de travail en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="f0461-124">Using your preferred HTTP client, GET requests can be made to the URI in statusQueryGetUri to inspect the status of the running workflow.</span></span> <span data-ttu-id="f0461-125">La réponse d’État renvoyée doit ressembler au code suivant.</span><span class="sxs-lookup"><span data-stu-id="f0461-125">The returned status response should resemble the following code.</span></span>

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

<span data-ttu-id="f0461-126">À mesure que le processus se poursuit, la réponse d’état passe à **échec** ou **terminé**.</span><span class="sxs-lookup"><span data-stu-id="f0461-126">As the process continues, the status response will change to either **Failed** or **Completed**.</span></span> <span data-ttu-id="f0461-127">En cas de réussite, la propriété de **sortie** de la charge utile contient toutes les données retournées.</span><span class="sxs-lookup"><span data-stu-id="f0461-127">On successful completion, the **output** property in the payload will contain any returned data.</span></span>

## <a name="monitoring"></a><span data-ttu-id="f0461-128">Surveillance</span><span class="sxs-lookup"><span data-stu-id="f0461-128">Monitoring</span></span>

<span data-ttu-id="f0461-129">Pour les tâches répétitives simples, Azure Functions fournit le `TimerTrigger` qui peut être planifié en fonction d’une expression cron.</span><span class="sxs-lookup"><span data-stu-id="f0461-129">For simple recurring tasks, Azure Functions provides the `TimerTrigger` that can be scheduled based on a CRON expression.</span></span> <span data-ttu-id="f0461-130">La minuterie fonctionne bien pour les tâches simples à courte durée de vie, mais il peut y avoir des scénarios dans lesquels une planification plus flexible est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="f0461-130">The timer works well for simple, short-lived tasks, but there might be scenarios where more flexible scheduling is needed.</span></span> <span data-ttu-id="f0461-131">Ce scénario se présente lorsque le modèle de surveillance et le Durable Functions peuvent vous aider.</span><span class="sxs-lookup"><span data-stu-id="f0461-131">This scenario is when the monitoring pattern and Durable Functions can help.</span></span>

<span data-ttu-id="f0461-132">Durable Functions permet des intervalles de planification flexibles, la gestion de la durée de vie et la création de plusieurs processus d’analyse à partir d’une seule fonction d’orchestration.</span><span class="sxs-lookup"><span data-stu-id="f0461-132">Durable Functions allows for flexible scheduling intervals, lifetime management, and the creation of multiple monitor processes from a single orchestration function.</span></span> <span data-ttu-id="f0461-133">Un cas d’utilisation de cette fonctionnalité peut consister à créer des observateurs pour les modifications de cours d’action qui se terminent une fois qu’un certain seuil est atteint.</span><span class="sxs-lookup"><span data-stu-id="f0461-133">One use case for this functionality might be to create watchers for stock price changes that complete once a certain threshold is met.</span></span>

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

<span data-ttu-id="f0461-134">`DurableOrchestrationContext`la `CreateTimer` méthode de définit la planification de l’appel suivant de la boucle pour vérifier les modifications du cours de l’action.</span><span class="sxs-lookup"><span data-stu-id="f0461-134">`DurableOrchestrationContext`'s `CreateTimer` method sets up the schedule for the next invocation of the loop to check for stock price changes.</span></span> <span data-ttu-id="f0461-135">`DurableOrchestrationContext` a également une `CurrentUtcDateTime` propriété pour obtenir la valeur DateTime actuelle en heure UTC.</span><span class="sxs-lookup"><span data-stu-id="f0461-135">`DurableOrchestrationContext` also has a `CurrentUtcDateTime` property to get the current DateTime value in UTC.</span></span> <span data-ttu-id="f0461-136">Il est préférable d’utiliser cette propriété au lieu de `DateTime.UtcNow` , car elle est facilement factice pour le test.</span><span class="sxs-lookup"><span data-stu-id="f0461-136">It's better to use this property instead of `DateTime.UtcNow` because it's easily mocked for testing.</span></span>

## <a name="recommended-resources"></a><span data-ttu-id="f0461-137">Ressources recommandées</span><span class="sxs-lookup"><span data-stu-id="f0461-137">Recommended resources</span></span>

- [<span data-ttu-id="f0461-138">Azure Durable Functions</span><span class="sxs-lookup"><span data-stu-id="f0461-138">Azure Durable Functions</span></span>](/azure/azure-functions/durable-functions-overview)
- [<span data-ttu-id="f0461-139">Tests unitaires dans .NET Core et .NET Standard</span><span class="sxs-lookup"><span data-stu-id="f0461-139">Unit Testing in .NET Core and .NET Standard</span></span>](../../core/testing/index.md)

>[!div class="step-by-step"]
><span data-ttu-id="f0461-140">[Précédent](durable-azure-functions.md) 
> [Suivant](serverless-business-scenarios.md)</span><span class="sxs-lookup"><span data-stu-id="f0461-140">[Previous](durable-azure-functions.md)
[Next](serverless-business-scenarios.md)</span></span>
