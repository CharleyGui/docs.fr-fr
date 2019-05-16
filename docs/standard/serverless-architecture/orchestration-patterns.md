---
title: Modèles d’orchestration - applications sans serveur
description: Demande de tirage de fonctions durables Azure
author: cecilphillip
ms.author: cephilli
ms.date: 06/26/2018
ms.openlocfilehash: 18e13c5355490ef4a019ceda459114bdb6bfd539
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65638806"
---
# <a name="orchestration-patterns"></a><span data-ttu-id="b7e3a-103">Modèles d’orchestration</span><span class="sxs-lookup"><span data-stu-id="b7e3a-103">Orchestration patterns</span></span>

<span data-ttu-id="b7e3a-104">Fonctions durables rend plus facile de créer des flux de travail avec état qui est composés d’activités discrètes, à long terme dans un environnement sans serveur.</span><span class="sxs-lookup"><span data-stu-id="b7e3a-104">Durable Functions makes it easier to create stateful workflows that are composed of discrete, long running activities in a serverless environment.</span></span> <span data-ttu-id="b7e3a-105">Dans la mesure où les fonctions durables peut suivre la progression de votre flux de travail et régulièrement des points de contrôle de l’historique d’exécution, il se prête à l’implémentation de certains modèles intéressants.</span><span class="sxs-lookup"><span data-stu-id="b7e3a-105">Since Durable Functions can track the progress of your workflows and periodically checkpoints the execution history, it lends itself to implementing some interesting patterns.</span></span>

## <a name="function-chaining"></a><span data-ttu-id="b7e3a-106">Chaînage de fonctions</span><span class="sxs-lookup"><span data-stu-id="b7e3a-106">Function chaining</span></span>

<span data-ttu-id="b7e3a-107">Dans un procédé séquentiel typique, les activités doivent exécuter l’une après l’autre dans un ordre particulier.</span><span class="sxs-lookup"><span data-stu-id="b7e3a-107">In a typical sequential process, activities need to execute one after the other in a particular order.</span></span> <span data-ttu-id="b7e3a-108">Si vous le souhaitez, l’activité à venir peut nécessiter une sortie à partir de la fonction précédente.</span><span class="sxs-lookup"><span data-stu-id="b7e3a-108">Optionally, the upcoming activity may require some output from the previous function.</span></span> <span data-ttu-id="b7e3a-109">Cette dépendance sur l’ordre des activités crée une chaîne de la fonction de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="b7e3a-109">This dependency on the ordering of activities creates a function chain of execution.</span></span>

<span data-ttu-id="b7e3a-110">L’avantage d’utiliser des fonctions durables pour implémenter ce modèle de flux de travail provient de sa capacité à faire des points de contrôle.</span><span class="sxs-lookup"><span data-stu-id="b7e3a-110">The benefit of using Durable Functions to implement this workflow pattern comes from its ability to do checkpointing.</span></span> <span data-ttu-id="b7e3a-111">Si le serveur tombe en panne, le réseau arrive à expiration ou un autre problème se produit, fonctions durables peuvent reprendre à partir du dernier état connu et continuer à exécuter votre flux de travail, même si elle est sur un autre serveur.</span><span class="sxs-lookup"><span data-stu-id="b7e3a-111">If the server crashes, the network times out or some other issue occurs, Durable functions can resume from the last known state and continue running your workflow even if it's on another server.</span></span>

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

<span data-ttu-id="b7e3a-112">Dans l’exemple de code précédent, le `CallActivityAsync` (fonction) est chargée d’exécuter une activité donnée sur une machine virtuelle dans le centre de données.</span><span class="sxs-lookup"><span data-stu-id="b7e3a-112">In the preceding code sample, the `CallActivityAsync` function is responsible for running a given activity on a virtual machine in the data center.</span></span> <span data-ttu-id="b7e3a-113">Lorsque l’expression await retourne et la tâche sous-jacente est terminée, l’exécution est enregistrée dans la table d’historique.</span><span class="sxs-lookup"><span data-stu-id="b7e3a-113">When the await returns and the underlying Task completes, the execution will be recorded to the history table.</span></span> <span data-ttu-id="b7e3a-114">Le code dans la fonction d’orchestrateur peut faire utiliser chacune des constructions familiers de la bibliothèque parallèle de tâches et les mots clés async/await.</span><span class="sxs-lookup"><span data-stu-id="b7e3a-114">The code in the orchestrator function can make use of any of the familiar constructs of the Task Parallel Library and the async/await keywords.</span></span>

<span data-ttu-id="b7e3a-115">Le code suivant est un exemple simplifié de ce à quoi le `ProcessPayment` méthode peut ressembler à :</span><span class="sxs-lookup"><span data-stu-id="b7e3a-115">The following code is a simplified example of what the `ProcessPayment` method may look like:</span></span>

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

## <a name="asynchronous-http-apis"></a><span data-ttu-id="b7e3a-116">API HTTP asynchrones</span><span class="sxs-lookup"><span data-stu-id="b7e3a-116">Asynchronous HTTP APIs</span></span>

<span data-ttu-id="b7e3a-117">Dans certains cas, les flux de travail peut-être contenir des activités qui prennent une relativement longue période de temps.</span><span class="sxs-lookup"><span data-stu-id="b7e3a-117">In some cases, workflows may contain activities that take a relatively long period of time to complete.</span></span> <span data-ttu-id="b7e3a-118">Imaginez un processus qui lance la sauvegarde du support de fichiers dans le stockage blob.</span><span class="sxs-lookup"><span data-stu-id="b7e3a-118">Imagine a process that kicks off the backup of media files into blob storage.</span></span> <span data-ttu-id="b7e3a-119">Selon la taille et la quantité des fichiers multimédias, ce processus de sauvegarde peut prendre des heures de travail.</span><span class="sxs-lookup"><span data-stu-id="b7e3a-119">Depending on the size and quantity of the media files, this backup process may take hours to complete.</span></span>

<span data-ttu-id="b7e3a-120">Dans ce scénario, le `DurableOrchestrationClient`de possibilité de vérifier l’état d’un workflow en cours d’exécution devient utile.</span><span class="sxs-lookup"><span data-stu-id="b7e3a-120">In this scenario, the `DurableOrchestrationClient`'s ability to check the status of a running workflow becomes useful.</span></span> <span data-ttu-id="b7e3a-121">Lorsque vous utilisez un `HttpTrigger` pour démarrer un flux de travail, le `CreateCheckStatusResponse` méthode peut être utilisée pour retourner une instance de `HttpResponseMessage`.</span><span class="sxs-lookup"><span data-stu-id="b7e3a-121">When using an `HttpTrigger` to start a workflow, the `CreateCheckStatusResponse` method can be used to return an instance of `HttpResponseMessage`.</span></span> <span data-ttu-id="b7e3a-122">Cette réponse fournit au client avec un URI dans la charge utile qui peut être utilisé pour vérifier l’état du processus en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="b7e3a-122">This response provides the client with a URI in the payload that can be used to check the status of the running process.</span></span>

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

<span data-ttu-id="b7e3a-123">Le résultat de l’exemple ci-dessous illustre la structure de la charge utile de réponse.</span><span class="sxs-lookup"><span data-stu-id="b7e3a-123">The sample result below shows the structure of the response payload.</span></span>

```json
{
    "id": "instanceId",
    "statusQueryGetUri": "http://host/statusUri",
    "sendEventPostUri": "http://host/eventUri",
    "terminatePostUri": "http://host/terminateUri"
}
```

<span data-ttu-id="b7e3a-124">À l’aide de votre client HTTP par défaut, les requêtes GET est possible à l’URI dans statusQueryGetUri pour inspecter l’état du flux de travail en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="b7e3a-124">Using your preferred HTTP client, GET requests can be made to the URI in statusQueryGetUri to inspect the status of the running workflow.</span></span> <span data-ttu-id="b7e3a-125">La réponse de l’état renvoyé doit ressembler au code suivant.</span><span class="sxs-lookup"><span data-stu-id="b7e3a-125">The returned status response should resemble the following code.</span></span>

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

<span data-ttu-id="b7e3a-126">À mesure que le processus, la réponse d’état sera alors soit **échec** ou **terminé**.</span><span class="sxs-lookup"><span data-stu-id="b7e3a-126">As the process continues, the status response will change to either **Failed** or **Completed**.</span></span> <span data-ttu-id="b7e3a-127">Opération réussie, le **sortie** propriété dans la charge utile contient les données retournées.</span><span class="sxs-lookup"><span data-stu-id="b7e3a-127">On successful completion, the **output** property in the payload will contain any returned data.</span></span>

## <a name="monitoring"></a><span data-ttu-id="b7e3a-128">Analyse</span><span class="sxs-lookup"><span data-stu-id="b7e3a-128">Monitoring</span></span>

<span data-ttu-id="b7e3a-129">Pour des tâches récurrentes simples, Azure Functions fournit le `TimerTrigger` qui peuvent être planifiés selon une expression CRON.</span><span class="sxs-lookup"><span data-stu-id="b7e3a-129">For simple recurring tasks, Azure Functions provides the `TimerTrigger` that can be scheduled based on a CRON expression.</span></span> <span data-ttu-id="b7e3a-130">Le minuteur fonctionne bien pour les tâches de courte durées, simples, mais il peut y avoir des scénarios où une planification plus flexible est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="b7e3a-130">The timer works well for simple, short-lived tasks, but there might be scenarios where more flexible scheduling is needed.</span></span> <span data-ttu-id="b7e3a-131">Ce scénario est lorsque le modèle de surveillance et les fonctions durables peuvent aider.</span><span class="sxs-lookup"><span data-stu-id="b7e3a-131">This scenario is when the monitoring pattern and Durable Functions can help.</span></span>

<span data-ttu-id="b7e3a-132">Fonctions durables permet des intervalles de planifications flexibles, la gestion de la durée de vie et la création de plusieurs processus d’analyse à partir d’une fonction d’orchestration unique.</span><span class="sxs-lookup"><span data-stu-id="b7e3a-132">Durable Functions allows for flexible scheduling intervals, lifetime management, and the creation of multiple monitor processes from a single orchestration function.</span></span> <span data-ttu-id="b7e3a-133">Un cas d’usage pour cette fonctionnalité peut consister à créer des observateurs pour les modifications de prix de l’action une fois remplies d’un certain seuil.</span><span class="sxs-lookup"><span data-stu-id="b7e3a-133">One use case for this functionality might be to create watchers for stock price changes that complete once a certain threshold is met.</span></span>

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

<span data-ttu-id="b7e3a-134">`DurableOrchestrationContext`de `CreateTimer` méthode configure la planification pour l’appel suivant de la boucle de vérifier les modifications de prix de l’action.</span><span class="sxs-lookup"><span data-stu-id="b7e3a-134">`DurableOrchestrationContext`'s `CreateTimer` method sets up the schedule for the next invocation of the loop to check for stock price changes.</span></span> <span data-ttu-id="b7e3a-135">`DurableOrchestrationContext` possède également un `CurrentUtcDateTime` propriété à obtenir la valeur de date/heure actuelle au format UTC.</span><span class="sxs-lookup"><span data-stu-id="b7e3a-135">`DurableOrchestrationContext` also has a `CurrentUtcDateTime` property to get the current DateTime value in UTC.</span></span> <span data-ttu-id="b7e3a-136">Il est préférable d’utiliser cette propriété au lieu de `DateTime.UtcNow` , car il est facilement simulée pour le test.</span><span class="sxs-lookup"><span data-stu-id="b7e3a-136">It's better to use this property instead of `DateTime.UtcNow` because it's easily mocked for testing.</span></span>

## <a name="recommended-resources"></a><span data-ttu-id="b7e3a-137">Ressources recommandées</span><span class="sxs-lookup"><span data-stu-id="b7e3a-137">Recommended resources</span></span>

* [<span data-ttu-id="b7e3a-138">Azure Functions Durable</span><span class="sxs-lookup"><span data-stu-id="b7e3a-138">Azure Durable Functions</span></span>](https://docs.microsoft.com/azure/azure-functions/durable-functions-overview)
* [<span data-ttu-id="b7e3a-139">Tests unitaires dans .NET Core et .NET Standard</span><span class="sxs-lookup"><span data-stu-id="b7e3a-139">Unit Testing in .NET Core and .NET Standard</span></span>](../../core/testing/index.md)

>[!div class="step-by-step"]
><span data-ttu-id="b7e3a-140">[Précédent](durable-azure-functions.md)
>[Suivant](serverless-business-scenarios.md)</span><span class="sxs-lookup"><span data-stu-id="b7e3a-140">[Previous](durable-azure-functions.md)
[Next](serverless-business-scenarios.md)</span></span>
