---
title: Fonctions Azure durables - Applications sans serveur
description: Les fonctions Azure durables prolongent le temps d’exécution azure Functions pour activer les flux de travail majestueux dans le code.
author: cecilphillip
ms.author: cephilli
ms.date: 06/26/2018
ms.openlocfilehash: 2c0ad086640409ac187c3aa882add4d6b39b6ff9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72522864"
---
# <a name="durable-azure-functions"></a>Fonctions Azure durables

Lors de la création d’applications sans serveur avec Azure Functions, vos opérations sont généralement conçues pour fonctionner de manière apatride. La raison de ce choix de conception est parce que comme la plate-forme échelles, il devient difficile de savoir quels serveurs le code est en cours d’exécution sur. Il devient également difficile de savoir combien de cas sont actifs à un moment donné. Cependant, il existe des catégories de demandes qui exigent que l’état actuel d’un processus soit connu. Considérez le processus de soumission d’une commande à une boutique en ligne. L’opération de caisse peut être un flux de travail qui est composé de multiples opérations qui ont besoin de connaître l’état du processus. Ces informations peuvent inclure l’inventaire du produit, si le client a des crédits sur son compte, ainsi que les résultats du traitement de la carte de crédit. Ces opérations pourraient facilement être leurs propres flux de travail internes ou même des services à partir de systèmes tiers.

Il existe aujourd’hui divers modèles qui aident à la coordination de l’état d’application entre les systèmes internes et externes. Il est courant de trouver des solutions qui reposent sur des systèmes de file d’attente centralisés, des magasins à valeur clé distribués ou des bases de données partagées pour gérer cet état. Cependant, il s’agit là de ressources supplémentaires qui doivent maintenant être mises à disposition et gérées. Dans un environnement sans serveur, votre code pourrait devenir lourd en essayant de coordonner avec ces ressources manuellement. Azure Functions offre une alternative pour créer des fonctions étatiques appelées Fonctions durables.

Fonctions durables est une extension de l’exécution Azure Functions qui permet la définition des flux de travail majestueux dans le code. En décomposant les flux de travail en activités, l’extension des fonctions durables peut gérer l’état, créer des points de contrôle de progression et gérer la distribution des appels de fonctions entre les serveurs. En arrière-plan, il utilise un compte De stockage Azure pour poursuivre l’historique d’exécution, planifier les fonctions d’activité et récupérer les réponses. Votre code sans serveur ne doit jamais interagir avec des informations persistantes dans ce compte de stockage, et n’est généralement pas quelque chose avec lequel les développeurs ont besoin d’interagir.

## <a name="triggering-a-stateful-workflow"></a>Déclenchement d’un flux de travail étatique

Les flux de travail d’état dans les fonctions durables peuvent être décomposés en deux composants intrinsèques ; l’orchestration et les déclencheurs d’activité. Les déclencheurs et les fixations sont des composants de base utilisés par Azure Functions pour permettre à vos fonctions sans serveur d’être notifiées au moment de démarrer, de recevoir des entrées et de retourner les résultats.

### <a name="working-with-the-orchestration-client"></a>Travailler avec le client Orchestration

Les orchestrations sont uniques par rapport à d’autres styles d’opérations déclenchées dans Azure Functions. Les fonctions durables permettent l’exécution de fonctions qui peuvent prendre des heures, voire des jours. Ce type de comportement vient avec la nécessité de vérifier l’état d’une orchestration en cours d’exécution, de manière préventive, ou d’envoyer des notifications d’événements externes.

Dans de tels cas, l’extension Des fonctions durables fournit la `DurableOrchestrationClient` classe qui vous permet d’interagir avec des fonctions orchestrées. Vous avez accès au client d’orchestration en utilisant la `OrchestrationClientAttribute` liaison. Généralement, vous incluriez cet attribut avec un `HttpTrigger` `ServiceBusTrigger`autre type de déclenchement, tel qu’un ou . Une fois que la fonction source a été déclenchée, le client d’orchestration peut être utilisé pour démarrer une fonction d’orchestrateur.

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

### <a name="the-orchestrator-function"></a>La fonction orchestrateur

Annoter une fonction avec l’OrchestrationTriggerAttribute dans Azure Functions marque qui fonctionnent comme une fonction d’orchestrateur. Il est responsable de la gestion des différentes activités qui composent votre flux de travail majestueux.

Les fonctions d’orchestrateur ne peuvent pas utiliser des fixations autres que l’OrchestrationTriggerAttribute. Cet attribut ne peut être utilisé qu’avec un type de paramètre durableOrchestrationContexte. Aucune autre entrée ne peut être utilisée puisque la désétérialisation des entrées dans la signature de la fonction n’est pas prise en charge. Pour obtenir des entrées fournies par le client\<\> d’orchestration, la méthode GetInput T doit être utilisée.

En outre, les types de retour des fonctions d’orchestration doivent être soit vide, tâche, ou une valeur sérialisable JSON.

> *Le code de traitement des erreurs a été laissé de côté pour la brièveté*

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

De multiples cas d’orchestration peuvent être lancés et en cours d’exécution en même temps. Appeler `StartNewAsync` la méthode `DurableOrchestrationClient` sur les lancements d’une nouvelle instance de l’orchestration. La méthode `Task<string>` renvoie un qui se termine lorsque l’orchestration a commencé. Une exception `TimeoutException` de type est lancée si l’orchestration n’a pas commencé dans les 30 secondes.

Le `Task<string>` devait `StartNewAsync` contenir l’ID unique de l’instance d’orchestration. Cette pièce d’identité d’instance peut être utilisée pour invoquer des opérations sur cette orchestration spécifique. L’orchestration peut être demandée pour l’état ou envoyé des notifications d’événement.

### <a name="the-activity-functions"></a>Les fonctions d’activité

Les fonctions d’activité sont les opérations discrètes qui se sont composées au sein d’une fonction d’orchestration pour créer le flux de travail. Voici où la plupart des travaux réels auraient lieu. Ils représentent la logique d’affaires, les processus de longue durée, et les pièces de puzzle à une solution plus grande.

Le `ActivityTriggerAttribute` est utilisé pour annoter `DurableActivityContext`un paramètre de fonction de type . L’utilisation de l’annotation informe le temps d’exécution que la fonction est destinée à être utilisée comme fonction d’activité. Les valeurs d’entrée aux fonctions d’activité sont récupérées à l’aide de la `GetInput<T>` méthode du `DurableActivityContext` paramètre.

Semblable aux fonctions d’orchestration, les types de fonctions d’activité de retour doivent être soit nuls, tâche, ou une valeur sérialisable JSON.

Toutes les exceptions non gérées qui sont jetés dans les fonctions d’activité seront envoyés à la fonction d’orchestrateur d’appel et présentés comme un `TaskFailedException`. À ce stade, l’erreur peut être attrapée et enregistrée dans l’orchestrateur, et l’activité peut être rejugée.

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

- [Fonctions durables](https://docs.microsoft.com/azure/azure-functions/durable-functions-overview)
- [Liaisons pour les fonctions durables](https://docs.microsoft.com/azure/azure-functions/durable-functions-bindings)
- [Gérer les instances dans les fonctions durables](https://docs.microsoft.com/azure/azure-functions/durable-functions-instance-management)

>[!div class="step-by-step"]
>[Suivant précédent](event-grid.md)
>[Next](orchestration-patterns.md)
