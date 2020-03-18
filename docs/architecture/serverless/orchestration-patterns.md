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
# <a name="orchestration-patterns"></a><span data-ttu-id="3f768-103">Modèles d’orchestration</span><span class="sxs-lookup"><span data-stu-id="3f768-103">Orchestration patterns</span></span>

<span data-ttu-id="3f768-104">Durable Functions facilite la création de flux de travail majestueux qui sont composés d’activités discrètes et de longue durée dans un environnement sans serveur.</span><span class="sxs-lookup"><span data-stu-id="3f768-104">Durable Functions makes it easier to create stateful workflows that are composed of discrete, long running activities in a serverless environment.</span></span> <span data-ttu-id="3f768-105">Étant donné que les fonctions durables peuvent suivre l’évolution de vos flux de travail et des points de contrôle périodiques de l’historique d’exécution, il se prête à la mise en œuvre de certains modèles intéressants.</span><span class="sxs-lookup"><span data-stu-id="3f768-105">Since Durable Functions can track the progress of your workflows and periodically checkpoints the execution history, it lends itself to implementing some interesting patterns.</span></span>

## <a name="function-chaining"></a><span data-ttu-id="3f768-106">Chaînage de fonctions</span><span class="sxs-lookup"><span data-stu-id="3f768-106">Function chaining</span></span>

<span data-ttu-id="3f768-107">Dans un processus séquentiel typique, les activités doivent s’exécuter l’une après l’autre dans un ordre particulier.</span><span class="sxs-lookup"><span data-stu-id="3f768-107">In a typical sequential process, activities need to execute one after the other in a particular order.</span></span> <span data-ttu-id="3f768-108">En option, l’activité à venir peut nécessiter une certaine sortie de la fonction précédente.</span><span class="sxs-lookup"><span data-stu-id="3f768-108">Optionally, the upcoming activity may require some output from the previous function.</span></span> <span data-ttu-id="3f768-109">Cette dépendance à l’ordre des activités crée une chaîne de fonctions d’exécution.</span><span class="sxs-lookup"><span data-stu-id="3f768-109">This dependency on the ordering of activities creates a function chain of execution.</span></span>

<span data-ttu-id="3f768-110">L’avantage d’utiliser les fonctions durables pour mettre en œuvre ce modèle de flux de travail vient de sa capacité à faire le contrôle.</span><span class="sxs-lookup"><span data-stu-id="3f768-110">The benefit of using Durable Functions to implement this workflow pattern comes from its ability to do checkpointing.</span></span> <span data-ttu-id="3f768-111">Si le serveur se bloque, que le réseau s’évanouit ou qu’un autre problème se produit, les fonctions durables peuvent reprendre à partir du dernier état connu et continuer à exécuter votre flux de travail même si c’est sur un autre serveur.</span><span class="sxs-lookup"><span data-stu-id="3f768-111">If the server crashes, the network times out or some other issue occurs, Durable functions can resume from the last known state and continue running your workflow even if it's on another server.</span></span>

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

<span data-ttu-id="3f768-112">Dans l’échantillon de `CallActivityAsync` code précédent, la fonction est responsable de l’exécution d’une activité donnée sur une machine virtuelle dans le centre de données.</span><span class="sxs-lookup"><span data-stu-id="3f768-112">In the preceding code sample, the `CallActivityAsync` function is responsible for running a given activity on a virtual machine in the data center.</span></span> <span data-ttu-id="3f768-113">Lorsque l’attente sera de retour et que la tâche sous-jacente sera terminée, l’exécution sera enregistrée au tableau d’histoire.</span><span class="sxs-lookup"><span data-stu-id="3f768-113">When the await returns and the underlying Task completes, the execution will be recorded to the history table.</span></span> <span data-ttu-id="3f768-114">Le code de la fonction orchestrateur peut faire usage de l’une des constructions familières de la Bibliothèque parallèle de tâches et des mots-clés async/await.</span><span class="sxs-lookup"><span data-stu-id="3f768-114">The code in the orchestrator function can make use of any of the familiar constructs of the Task Parallel Library and the async/await keywords.</span></span>

<span data-ttu-id="3f768-115">Le code suivant est un `ProcessPayment` exemple simplifié de ce à quoi la méthode peut ressembler :</span><span class="sxs-lookup"><span data-stu-id="3f768-115">The following code is a simplified example of what the `ProcessPayment` method may look like:</span></span>

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

## <a name="asynchronous-http-apis"></a><span data-ttu-id="3f768-116">API HTTP asynchrone</span><span class="sxs-lookup"><span data-stu-id="3f768-116">Asynchronous HTTP APIs</span></span>

<span data-ttu-id="3f768-117">Dans certains cas, les flux de travail peuvent contenir des activités qui prennent un délai relativement long.</span><span class="sxs-lookup"><span data-stu-id="3f768-117">In some cases, workflows may contain activities that take a relatively long period of time to complete.</span></span> <span data-ttu-id="3f768-118">Imaginez un processus qui donne le coup d’envoi de la sauvegarde des fichiers multimédias dans le stockage blob.</span><span class="sxs-lookup"><span data-stu-id="3f768-118">Imagine a process that kicks off the backup of media files into blob storage.</span></span> <span data-ttu-id="3f768-119">Selon la taille et la quantité des fichiers multimédias, ce processus de sauvegarde peut prendre des heures.</span><span class="sxs-lookup"><span data-stu-id="3f768-119">Depending on the size and quantity of the media files, this backup process may take hours to complete.</span></span>

<span data-ttu-id="3f768-120">Dans ce scénario, la `DurableOrchestrationClient`capacité de «vérifier l’état d’un flux de travail en cours d’exécution devient utile.</span><span class="sxs-lookup"><span data-stu-id="3f768-120">In this scenario, the `DurableOrchestrationClient`'s ability to check the status of a running workflow becomes useful.</span></span> <span data-ttu-id="3f768-121">Lors de `HttpTrigger` l’utilisation d’un `CreateCheckStatusResponse` flux de travail pour `HttpResponseMessage`démarrer un flux de travail, la méthode peut être utilisée pour retourner une instance de .</span><span class="sxs-lookup"><span data-stu-id="3f768-121">When using an `HttpTrigger` to start a workflow, the `CreateCheckStatusResponse` method can be used to return an instance of `HttpResponseMessage`.</span></span> <span data-ttu-id="3f768-122">Cette réponse fournit au client un URI dans la charge utile qui peut être utilisée pour vérifier l’état du processus d’exécution.</span><span class="sxs-lookup"><span data-stu-id="3f768-122">This response provides the client with a URI in the payload that can be used to check the status of the running process.</span></span>

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

<span data-ttu-id="3f768-123">Le résultat de l’échantillon ci-dessous montre la structure de la charge utile de réponse.</span><span class="sxs-lookup"><span data-stu-id="3f768-123">The sample result below shows the structure of the response payload.</span></span>

```json
{
    "id": "instanceId",
    "statusQueryGetUri": "http://host/statusUri",
    "sendEventPostUri": "http://host/eventUri",
    "terminatePostUri": "http://host/terminateUri"
}
```

<span data-ttu-id="3f768-124">À l’aide de votre client HTTP préféré, les demandes GET peuvent être faites à l’URI dans statusQueryGetUri pour inspecter l’état du flux de travail en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="3f768-124">Using your preferred HTTP client, GET requests can be made to the URI in statusQueryGetUri to inspect the status of the running workflow.</span></span> <span data-ttu-id="3f768-125">La réponse de statut retournée doit ressembler au code suivant.</span><span class="sxs-lookup"><span data-stu-id="3f768-125">The returned status response should resemble the following code.</span></span>

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

<span data-ttu-id="3f768-126">Au fur et à mesure que le processus se poursuivra, la réponse au statut changera pour **l’échec** ou **la fin**.</span><span class="sxs-lookup"><span data-stu-id="3f768-126">As the process continues, the status response will change to either **Failed** or **Completed**.</span></span> <span data-ttu-id="3f768-127">Une fois la propriété de **sortie** de la charge utile qui sera complétée, elle contiendra toutes les données retournées.</span><span class="sxs-lookup"><span data-stu-id="3f768-127">On successful completion, the **output** property in the payload will contain any returned data.</span></span>

## <a name="monitoring"></a><span data-ttu-id="3f768-128">Surveillance</span><span class="sxs-lookup"><span data-stu-id="3f768-128">Monitoring</span></span>

<span data-ttu-id="3f768-129">Pour des tâches récurrentes simples, `TimerTrigger` Azure Functions fournit le qui peut être programmé en fonction d’une expression CRON.</span><span class="sxs-lookup"><span data-stu-id="3f768-129">For simple recurring tasks, Azure Functions provides the `TimerTrigger` that can be scheduled based on a CRON expression.</span></span> <span data-ttu-id="3f768-130">La minuterie fonctionne bien pour des tâches simples et de courte durée, mais il peut y avoir des scénarios où une planification plus flexible est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="3f768-130">The timer works well for simple, short-lived tasks, but there might be scenarios where more flexible scheduling is needed.</span></span> <span data-ttu-id="3f768-131">Ce scénario est lorsque le modèle de surveillance et les fonctions durables peuvent aider.</span><span class="sxs-lookup"><span data-stu-id="3f768-131">This scenario is when the monitoring pattern and Durable Functions can help.</span></span>

<span data-ttu-id="3f768-132">Les fonctions durables permettent des intervalles de planification flexibles, une gestion à vie et la création de processus de moniteur multiples à partir d’une seule fonction d’orchestration.</span><span class="sxs-lookup"><span data-stu-id="3f768-132">Durable Functions allows for flexible scheduling intervals, lifetime management, and the creation of multiple monitor processes from a single orchestration function.</span></span> <span data-ttu-id="3f768-133">Un cas d’utilisation pour cette fonctionnalité pourrait être de créer des observateurs pour les changements de prix des actions qui complètent une fois qu’un certain seuil est atteint.</span><span class="sxs-lookup"><span data-stu-id="3f768-133">One use case for this functionality might be to create watchers for stock price changes that complete once a certain threshold is met.</span></span>

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

<span data-ttu-id="3f768-134">`DurableOrchestrationContext`la `CreateTimer` méthode de l’action établit le calendrier de la prochaine invocation de la boucle pour vérifier les changements de cours de l’action.</span><span class="sxs-lookup"><span data-stu-id="3f768-134">`DurableOrchestrationContext`'s `CreateTimer` method sets up the schedule for the next invocation of the loop to check for stock price changes.</span></span> <span data-ttu-id="3f768-135">`DurableOrchestrationContext`a également `CurrentUtcDateTime` une propriété pour obtenir la valeur actuelle DateTime en UTC.</span><span class="sxs-lookup"><span data-stu-id="3f768-135">`DurableOrchestrationContext` also has a `CurrentUtcDateTime` property to get the current DateTime value in UTC.</span></span> <span data-ttu-id="3f768-136">Il est préférable d’utiliser `DateTime.UtcNow` cette propriété au lieu de parce qu’il est facilement moqué pour les tests.</span><span class="sxs-lookup"><span data-stu-id="3f768-136">It's better to use this property instead of `DateTime.UtcNow` because it's easily mocked for testing.</span></span>

## <a name="recommended-resources"></a><span data-ttu-id="3f768-137">Ressources recommandées</span><span class="sxs-lookup"><span data-stu-id="3f768-137">Recommended resources</span></span>

- [<span data-ttu-id="3f768-138">Azure Durable Functions</span><span class="sxs-lookup"><span data-stu-id="3f768-138">Azure Durable Functions</span></span>](https://docs.microsoft.com/azure/azure-functions/durable-functions-overview)
- [<span data-ttu-id="3f768-139">Tests unitaires dans .NET Core et .NET Standard</span><span class="sxs-lookup"><span data-stu-id="3f768-139">Unit Testing in .NET Core and .NET Standard</span></span>](../../core/testing/index.md)

>[!div class="step-by-step"]
><span data-ttu-id="3f768-140">[Suivant précédent](durable-azure-functions.md)
>[Next](serverless-business-scenarios.md)</span><span class="sxs-lookup"><span data-stu-id="3f768-140">[Previous](durable-azure-functions.md)
[Next](serverless-business-scenarios.md)</span></span>
