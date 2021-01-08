---
title: Journalisation hautes performances dans .NET
author: IEvangelist
description: Découvrez comment utiliser LoggerMessage pour créer des délégués pouvant être mis en cache et nécessitant moins d’allocations d’objets pour les scénarios de journalisation à hautes performances.
ms.author: dapine
ms.date: 01/04/2021
ms.openlocfilehash: 0031ff7a9f70cb0cf724fdf6dfa4fbe0a44af7c1
ms.sourcegitcommit: 5d9cee27d9ffe8f5670e5f663434511e81b8ac38
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98025443"
---
# <a name="high-performance-logging-in-net"></a>Journalisation hautes performances dans .NET

La <xref:Microsoft.Extensions.Logging.LoggerMessage> classe expose les fonctionnalités permettant de créer des délégués pouvant être mis en cache qui nécessitent moins d’allocations d’objets et une surcharge de calcul réduite par rapport aux [méthodes d’extension du journal](xref:Microsoft.Extensions.Logging.LoggerExtensions), telles que <xref:Microsoft.Extensions.Logging.LoggerExtensions.LogInformation%2A> et <xref:Microsoft.Extensions.Logging.LoggerExtensions.LogDebug%2A> . Pour les scénarios de journalisation hautes performances, utilisez le modèle <xref:Microsoft.Extensions.Logging.LoggerMessage>.

<xref:Microsoft.Extensions.Logging.LoggerMessage> procure les avantages suivants en termes de performances par rapport aux méthodes d’extension de journaliseur :

- Les méthodes d’extension de journaliseur nécessitent la conversion (« boxing ») de types de valeur, tels que `int`, en `object`. Utilisant des champs <xref:System.Action> statiques et des méthodes d’extension avec des paramètres fortement typés, le modèle <xref:Microsoft.Extensions.Logging.LoggerMessage> évite le boxing.
- Les méthodes d’extension de journaliseur doivent analyser le modèle de message (chaîne de format nommé) chaque fois qu’un message de journal est écrit. <xref:Microsoft.Extensions.Logging.LoggerMessage> requiert l’analyse d’un modèle une seule fois quand le message est défini.

L’exemple d’application illustre <xref:Microsoft.Extensions.Logging.LoggerMessage> des fonctionnalités avec un service Worker de traitement de la file d’attente prioritaire. L’application traite les éléments de travail par ordre de priorité. À mesure que ces opérations se produisent, des messages de journal sont générés à l’aide du modèle <xref:Microsoft.Extensions.Logging.LoggerMessage>.

## <a name="define-a-logger-message"></a>Définir un message d’enregistreur d’événements

Utilisez [define (LogLevel, EventID, String)](xref:Microsoft.Extensions.Logging.LoggerMessage.Define%2A) pour créer un <xref:System.Action> délégué pour la journalisation d’un message. Les surcharges <xref:Microsoft.Extensions.Logging.LoggerMessage.Define%2A> permettent de passer jusqu’à six paramètres de type à une chaîne de format nommée (modèle).

La chaîne fournie à la méthode <xref:Microsoft.Extensions.Logging.LoggerMessage.Define%2A> est un modèle et non pas une chaîne interpolée. Les espaces réservés sont remplis dans l’ordre dans lequel les types sont spécifiés. Les noms d’espace réservé dans le modèle doivent être descriptifs et cohérents d’un modèle à l’autre. Ils servent de noms de propriété dans les données de journal structurées. Nous vous recommandons d’utiliser la [casse Pascal](../../standard/design-guidelines/capitalization-conventions.md) pour les noms d’espace réservé. Par exemple, `{Item}`, `{DateTime}`.

Chaque message de journal est une <xref:System.Action> contenue dans un champ statique créé par [LoggerMessage.Define](xref:Microsoft.Extensions.Logging.LoggerMessage.Define%2A). Par exemple, l’exemple d’application crée un champ pour décrire un message de journal pour le traitement des éléments de travail :

:::code language="csharp" source="snippets/configuration/worker-service-options/Extensions/LoggerExtensions.cs" id="FailedProcessingField":::

Pour l’<xref:System.Action>, spécifiez :

- Le niveau du journal
- Un identificateur d’événement unique (<xref:Microsoft.Extensions.Logging.EventId>) avec le nom de la méthode d’extension statique
- Le modèle de message (chaîne de format nommée)

Comme les éléments de travail sont déplacés dans la file d’attente pour le traitement, l’application de service Worker définit :

- Le niveau de journal sur <xref:Microsoft.Extensions.Logging.LogLevel.Critical?displayProperty=nameWithType>
- L’ID d’événement sur `13` avec le nom de la méthode `FailedToProcessWorkItem`
- Le modèle de message (chaîne de format nommée) sur une chaîne

:::code language="csharp" source="snippets/configuration/worker-service-options/Extensions/LoggerExtensions.cs" id="FailedProcessingAssignment":::

Des magasins de journalisation structurée peuvent utiliser le nom d’événement quand il est fourni avec l’ID d’événement pour enrichir la journalisation. Par exemple, [Serilog](https://github.com/serilog/serilog-extensions-logging) utilise le nom d’événement.

L’<xref:System.Action> est appelée par le biais d’une méthode d’extension fortement typée. La `PriorityItemProcessed` méthode journalise un message chaque fois qu’un élément de travail est en cours de traitement. En revanche, `FailedToProcessWorkItem` est appelé quand (et si) une exception se produit :

:::code language="csharp" source="snippets/configuration/worker-service-options/Worker.cs" range="18-39" highlight="15-18":::

Examinez la sortie de la console de l’application :

```console
crit: WorkerServiceOptions.Example.Worker[13]
      Epic failure processing item!
      System.Exception: Failed to verify communications.
         at WorkerServiceOptions.Example.Worker.ExecuteAsync(CancellationToken stoppingToken) in
         ..\Worker.cs:line 27
```

Pour passer des paramètres à un message de journal, définissez jusqu’à six types au moment de la création du champ statique. L’exemple d’application enregistre les détails de l’élément de travail lors du traitement des éléments en définissant un `WorkItem` type pour le <xref:System.Action> champ :

:::code language="csharp" source="snippets/configuration/worker-service-options/Extensions/LoggerExtensions.cs" id="ProcessingItemField":::

Le modèle de message de journal du délégué reçoit ses valeurs d’espace réservé des types fournis. L’exemple d’application définit un délégué pour ajouter un élément de travail où le paramètre d’élément est `WorkItem` :

:::code language="csharp" source="snippets/configuration/worker-service-options/Extensions/LoggerExtensions.cs" id="ProcessingItemAssignment":::

La méthode d’extension statique pour la journalisation qu’un élément de travail est en cours de traitement, `PriorityItemProcessed` , reçoit la valeur de l’argument d’élément de travail et la passe au <xref:System.Action> délégué :

:::code language="csharp" source="snippets/configuration/worker-service-options/Extensions/LoggerExtensions.cs" id="ProcessingItemMethod":::

Dans la méthode du service Worker `ExecuteAsync` , `PriorityItemProcessed` est appelé pour enregistrer le message :

:::code language="csharp" source="snippets/configuration/worker-service-options/Worker.cs" range="18-39" highlight="12":::

Examinez la sortie de la console de l’application :

```console
info: WorkerServiceOptions.Example.Worker[1]
      Processing priority item: Priority-Extreme (50db062a-9732-4418-936d-110549ad79e4): 'Verify communications'
```

## <a name="define-logger-message-scope"></a>Définir la portée du message de l’enregistreur

La méthode [DefineScope (String)](xref:Microsoft.Extensions.Logging.LoggerMessage.DefineScope%2A) crée un <xref:System.Func%601> délégué pour définir une [étendue de journal](logging.md#log-scopes). Les surcharges <xref:Microsoft.Extensions.Logging.LoggerMessage.DefineScope%2A> permettent de passer jusqu’à trois paramètres de type à une chaîne de format nommée (modèle).

Comme c’est le cas avec la méthode <xref:Microsoft.Extensions.Logging.LoggerMessage.Define%2A>, la chaîne fournie à la méthode <xref:Microsoft.Extensions.Logging.LoggerMessage.DefineScope%2A> est un modèle et non pas une chaîne interpolée. Les espaces réservés sont remplis dans l’ordre dans lequel les types sont spécifiés. Les noms d’espace réservé dans le modèle doivent être descriptifs et cohérents d’un modèle à l’autre. Ils servent de noms de propriété dans les données de journal structurées. Nous vous recommandons d’utiliser la [casse Pascal](../../standard/design-guidelines/capitalization-conventions.md) pour les noms d’espace réservé. Par exemple, `{Item}`, `{DateTime}`.

Définissez une [étendue de journal](logging.md#log-scopes) à appliquer à une série de messages de journal à l’aide de la méthode <xref:Microsoft.Extensions.Logging.LoggerMessage.DefineScope%2A>. Activez `IncludeScopes` dans la section du journaliseur de console *d’appsettings.json* :

:::code language="json" source="snippets/configuration/worker-service-options/appsettings.json" highlight="3-5":::

Pour créer une étendue de journal, ajoutez un champ destiné à contenir un délégué <xref:System.Func%601> pour l’étendue. L’exemple d’application crée un champ intitulé `_processingWorkScope` (*Internal/LoggerExtensions.cs*) :

:::code language="csharp" source="snippets/configuration/worker-service-options/Extensions/LoggerExtensions.cs" id="ProcessingWorkField":::

Utilisez <xref:Microsoft.Extensions.Logging.LoggerMessage.DefineScope%2A> pour créer le délégué. Vous pouvez spécifier jusqu’à trois types à utiliser comme arguments de modèle quand le délégué est appelé. L’exemple d’application utilise un modèle de message qui comprend la date et l’heure de début du traitement :

:::code language="csharp" source="snippets/configuration/worker-service-options/Extensions/LoggerExtensions.cs" id="ProcessingWorkAssignment":::

Fournissez une méthode d’extension statique pour le message de journal. Incluez tous les paramètres de type pour les propriétés nommées qui s’affichent dans le modèle de message. L’exemple d’application prend un `DateTime` pour un horodatage personnalisé à enregistrer et retourne `_processingWorkScope` :

:::code language="csharp" source="snippets/configuration/worker-service-options/Extensions/LoggerExtensions.cs" id="ProcessingWorkMethod":::

L’étendue inclut les appels d’extension de journalisation dans un bloc [using](../../csharp/language-reference/keywords/using-statement.md) :

:::code language="csharp" source="snippets/configuration/worker-service-options/Worker.cs" range="18-39" highlight="4":::

Examinez les messages de journal dans la sortie de la console de l’application. Le résultat suivant montre l’ordre de priorité des messages de journal avec le message d’étendue du journal inclus :

```console
info: WorkerServiceOptions.Example.Worker[1]
      => Processing work, started at: 09/25/2020 14:30:45
      Processing priority item: Priority-Extreme (f5090ede-a337-4041-b914-f6bc0db5ae64): 'Verify communications'
info: Microsoft.Hosting.Lifetime[0]
      Application started. Press Ctrl+C to shut down.
info: Microsoft.Hosting.Lifetime[0]
      Hosting environment: Development
info: Microsoft.Hosting.Lifetime[0]
      Content root path: ..\worker-service-options
info: WorkerServiceOptions.Example.Worker[1]
      => Processing work, started at: 09/25/2020 14:30:45
      Processing priority item: Priority-High (496d440f-2007-4391-b179-09d75ab52373): 'Validate collection'
info: WorkerServiceOptions.Example.Worker[1]
      => Processing work, started at: 09/25/2020 14:30:45
      Processing priority item: Priority-Medium (dea9e3f4-d7df-46d2-b7cd-5e0232eb98a5): 'Propagate selections'
info: WorkerServiceOptions.Example.Worker[1]
      => Processing work, started at: 09/25/2020 14:30:45
      Processing priority item: Priority-Medium (089d7f0d-da72-4b55-92fe-57b147838056): 'Enter pooling [contention]'
info: WorkerServiceOptions.Example.Worker[1]
      => Processing work, started at: 09/25/2020 14:30:45
      Processing priority item: Priority-Low (6e68c4be-089f-4450-9080-1ea63fcbb686): 'Health check network'
info: WorkerServiceOptions.Example.Worker[1]
      => Processing work, started at: 09/25/2020 14:30:45
      Processing priority item: Priority-Deferred (6f324134-6bb6-455f-81d4-553ab307c421): 'Ping weather service'
info: WorkerServiceOptions.Example.Worker[1]
      => Processing work, started at: 09/25/2020 14:30:45
      Processing priority item: Priority-Deferred (37bf736c-7a26-4a2a-9e56-e89bcf3b8f35): 'Set process state'
```

## <a name="see-also"></a>Voir aussi

- [Journalisation dans .NET](logging.md)
