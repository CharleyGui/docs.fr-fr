---
title: Fonctions Azure durables-applications sans serveur
description: Les fonctions Azure durables étendent le runtime Azure Functions pour activer les flux de travail avec état dans le code.
author: cecilphillip
ms.author: cephilli
ms.date: 06/26/2018
ms.openlocfilehash: 2c0ad086640409ac187c3aa882add4d6b39b6ff9
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/08/2019
ms.locfileid: "72522864"
---
# <a name="durable-azure-functions"></a>Fonctions Azure durables

Lorsque vous créez des applications sans serveur avec Azure Functions, vos opérations sont généralement conçues pour s’exécuter sans État. La raison de ce choix de conception est que, à mesure que la plateforme évolue, il devient difficile de savoir quels serveurs le code s’exécute. Il devient également difficile de savoir combien d’instances sont actives à un point donné. Toutefois, il existe des classes d’applications qui requièrent que l’état actuel d’un processus soit connu. Envisagez le processus d’envoi d’une commande à un magasin en ligne. L’opération d’extraction peut être un flux de travail composé de plusieurs opérations qui doivent connaître l’état du processus. Ces informations peuvent inclure l’inventaire des produits, si le client a un crédit sur son compte, ainsi que les résultats du traitement de la carte de crédit. Ces opérations peuvent facilement être leurs propres flux de travail internes, voire des services de systèmes tiers.

Il existe aujourd’hui plusieurs modèles qui facilitent la coordination de l’état des applications entre les systèmes internes et externes. Il est courant de rencontrer des solutions qui s’appuient sur des systèmes de mise en file d’attente centralisés, des magasins de valeurs de clés distribuées ou des bases de données partagées pour gérer cet État. Toutefois, il s’agit de toutes les ressources supplémentaires qui doivent à présent être approvisionnées et gérées. Dans un environnement sans serveur, votre code pourrait devenir fastidieux à tenter de coordonner manuellement ces ressources. Azure Functions offre une alternative à la création de fonctions avec état appelées Durable Functions.

Durable Functions est une extension du runtime Azure Functions qui permet la définition de flux de travail avec état dans le code. En décomposant les workflows en activités, l’extension de Durable Functions peut gérer l’État, créer des points de contrôle de progression et gérer la distribution des appels de fonction sur les serveurs. En arrière-plan, il utilise un compte de stockage Azure pour conserver l’historique d’exécution, planifier les fonctions d’activité et récupérer les réponses. Votre code sans serveur ne doit jamais interagir avec les informations persistantes dans ce compte de stockage, et n’est généralement pas un outil avec lequel les développeurs doivent interagir.

## <a name="triggering-a-stateful-workflow"></a>Déclenchement d’un flux de travail avec état

Les flux de travail avec état dans Durable Functions peuvent être divisés en deux composants intrinsèques ; déclencheurs d’activité et d’orchestration. Les déclencheurs et les liaisons sont des composants principaux utilisés par Azure Functions pour permettre à vos fonctions sans serveur d’être notifiées quand Démarrer, recevoir une entrée et retourner des résultats.

### <a name="working-with-the-orchestration-client"></a>Utilisation du client d’orchestration

Les orchestrations sont uniques par rapport aux autres styles d’opérations déclenchées dans Azure Functions. Durable Functions permet l’exécution de fonctions qui peuvent prendre plusieurs heures, voire plusieurs jours. Ce type de comportement est fourni avec la nécessité de vérifier l’état d’une orchestration en cours d’exécution, de terminer de manière préventive ou d’envoyer des notifications d’événements externes.

Dans ce cas, l’extension Durable Functions fournit la classe `DurableOrchestrationClient` qui vous permet d’interagir avec les fonctions orchestrées. Vous accédez au client d’orchestration à l’aide de la liaison de `OrchestrationClientAttribute`. En règle générale, vous incluez cet attribut avec un autre type de déclencheur, tel qu’un `HttpTrigger` ou `ServiceBusTrigger`. Une fois la fonction source déclenchée, le client d’orchestration peut être utilisé pour démarrer une fonction d’orchestrateur.

```csharp
[FunctionName("KickOff")]
public static async Task<HttpResponseMessage> Run(
    [HttpTrigger(AuthorizationLevel.Function, "POST")]HttpRequestMessage req,
    [OrchestrationClient ] DurableOrchestrationClient<orchestrationClient>)
{
    OrderRequestData data = await req.Content.ReadAsAsync<OrderRequestData>();

    string instanceId = await orchestrationClient.StartNewAsync("PlaceOrder", data);

    return orchestrationClient.CreateCheckStatusResponse(req, instanceId);
}
```

### <a name="the-orchestrator-function"></a>La fonction d’orchestrateur

L’annotation d’une fonction avec le OrchestrationTriggerAttribute dans Azure Functions marque cette fonction comme une fonction d’orchestrateur. Il est responsable de la gestion des différentes activités qui composent votre flux de travail avec état.

Les fonctions d’orchestrateur ne peuvent pas utiliser des liaisons autres que OrchestrationTriggerAttribute. Cet attribut peut uniquement être utilisé avec un type de paramètre DurableOrchestrationContext. Aucune autre entrée ne peut être utilisée, car la désérialisation des entrées dans la signature de la fonction n’est pas prise en charge. Pour récupérer les entrées fournies par le client d’orchestration, vous devez utiliser la méthode GetInput \<T \>.

En outre, les types de retour des fonctions d’orchestration doivent être void, Task ou une valeur sérialisable JSON.

> *Le code de gestion des erreurs a été omis par souci de concision*

```csharp
[FunctionName("PlaceOrder")]
public static async Task<string> PlaceOrder([OrchestrationTrigger] DurableOrchestrationContext context)
{
    OrderRequestData orderData = context.GetInput<OrderRequestData>();

    await context.CallActivityAsync<bool>("CheckAndReserveInventory", orderData);
    await context.CallActivityAsync<string>("ProcessPayment", orderData);

    string trackingNumber = await context.CallActivityAsync<string>("ScheduleShipping", orderData);
    await context.CallActivityAsync<string>("EmailCustomer", trackingNumber);

    return trackingNumber;
}
```

Plusieurs instances d’une orchestration peuvent être démarrées et exécutées en même temps. L’appel de la méthode `StartNewAsync` sur le `DurableOrchestrationClient` lance une nouvelle instance de l’orchestration. La méthode retourne un `Task<string>` qui se termine lorsque l’orchestration a démarré. Une exception de type `TimeoutException` est levée si l’orchestration n’a pas démarré dans les 30 secondes.

Le `Task<string>` terminé de `StartNewAsync` doit contenir l’ID unique de l’instance d’orchestration. Cet ID d’instance peut être utilisé pour appeler des opérations sur cette orchestration spécifique. L’orchestration peut être interrogée pour obtenir l’État ou envoyer des notifications d’événements.

### <a name="the-activity-functions"></a>Fonctions d’activité

Les fonctions d’activité sont les opérations discrètes qui sont composées ensemble au sein d’une fonction d’orchestration pour créer le flux de travail. C’est ici qu’intervient la plupart des tâches réelles. Elles représentent la logique métier, les processus à long terme et les éléments de puzzle à une plus grande solution.

Le `ActivityTriggerAttribute` est utilisé pour annoter un paramètre de fonction de type `DurableActivityContext`. L’utilisation de l’annotation indique au runtime que la fonction est destinée à être utilisée en tant que fonction d’activité. Les valeurs d’entrée des fonctions d’activité sont extraites à l’aide de la méthode `GetInput<T>` du paramètre `DurableActivityContext`.

Comme pour les fonctions d’orchestration, les types de retour des fonctions d’activité doivent être void, Task ou une valeur sérialisable JSON.

Toutes les exceptions non gérées qui sont levées dans les fonctions d’activité sont envoyées à la fonction d’orchestrateur appelant et présentées sous la forme d’un `TaskFailedException`. À ce stade, l’erreur peut être interceptée et consignée dans l’orchestrateur, et l’activité peut être retentée.

```csharp
[FunctionName("CheckAndReserveInventory")]
public static bool CheckAndReserveInventory([ActivityTrigger] DurableActivityContext context)
{
    OrderRequestData orderData = context.GetInput<OrderRequestData>();

    // Connect to inventory system and try to reserve items
    return true;
}
```

## <a name="recommended-resources"></a>Ressources recommandées

- [Durable Functions](https://docs.microsoft.com/azure/azure-functions/durable-functions-overview)
- [Liaisons pour Durable Functions](https://docs.microsoft.com/azure/azure-functions/durable-functions-bindings)
- [Gérer les instances dans Durable Functions](https://docs.microsoft.com/azure/azure-functions/durable-functions-instance-management)

>[!div class="step-by-step"]
>[Précédent](event-grid.md)
>[Suivant](orchestration-patterns.md)
