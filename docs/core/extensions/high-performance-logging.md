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
# <a name="high-performance-logging-in-net"></a><span data-ttu-id="9524c-103">Journalisation hautes performances dans .NET</span><span class="sxs-lookup"><span data-stu-id="9524c-103">High-performance logging in .NET</span></span>

<span data-ttu-id="9524c-104">La <xref:Microsoft.Extensions.Logging.LoggerMessage> classe expose les fonctionnalités permettant de créer des délégués pouvant être mis en cache qui nécessitent moins d’allocations d’objets et une surcharge de calcul réduite par rapport aux [méthodes d’extension du journal](xref:Microsoft.Extensions.Logging.LoggerExtensions), telles que <xref:Microsoft.Extensions.Logging.LoggerExtensions.LogInformation%2A> et <xref:Microsoft.Extensions.Logging.LoggerExtensions.LogDebug%2A> .</span><span class="sxs-lookup"><span data-stu-id="9524c-104">The <xref:Microsoft.Extensions.Logging.LoggerMessage> class exposes functionality to create cacheable delegates that require fewer object allocations and reduced computational overhead compared to [logger extension methods](xref:Microsoft.Extensions.Logging.LoggerExtensions), such as <xref:Microsoft.Extensions.Logging.LoggerExtensions.LogInformation%2A> and <xref:Microsoft.Extensions.Logging.LoggerExtensions.LogDebug%2A>.</span></span> <span data-ttu-id="9524c-105">Pour les scénarios de journalisation hautes performances, utilisez le modèle <xref:Microsoft.Extensions.Logging.LoggerMessage>.</span><span class="sxs-lookup"><span data-stu-id="9524c-105">For high-performance logging scenarios, use the <xref:Microsoft.Extensions.Logging.LoggerMessage> pattern.</span></span>

<span data-ttu-id="9524c-106"><xref:Microsoft.Extensions.Logging.LoggerMessage> procure les avantages suivants en termes de performances par rapport aux méthodes d’extension de journaliseur :</span><span class="sxs-lookup"><span data-stu-id="9524c-106"><xref:Microsoft.Extensions.Logging.LoggerMessage> provides the following performance advantages over Logger extension methods:</span></span>

- <span data-ttu-id="9524c-107">Les méthodes d’extension de journaliseur nécessitent la conversion (« boxing ») de types de valeur, tels que `int`, en `object`.</span><span class="sxs-lookup"><span data-stu-id="9524c-107">Logger extension methods require "boxing" (converting) value types, such as `int`, into `object`.</span></span> <span data-ttu-id="9524c-108">Utilisant des champs <xref:System.Action> statiques et des méthodes d’extension avec des paramètres fortement typés, le modèle <xref:Microsoft.Extensions.Logging.LoggerMessage> évite le boxing.</span><span class="sxs-lookup"><span data-stu-id="9524c-108">The <xref:Microsoft.Extensions.Logging.LoggerMessage> pattern avoids boxing by using static <xref:System.Action> fields and extension methods with strongly-typed parameters.</span></span>
- <span data-ttu-id="9524c-109">Les méthodes d’extension de journaliseur doivent analyser le modèle de message (chaîne de format nommé) chaque fois qu’un message de journal est écrit.</span><span class="sxs-lookup"><span data-stu-id="9524c-109">Logger extension methods must parse the message template (named format string) every time a log message is written.</span></span> <span data-ttu-id="9524c-110"><xref:Microsoft.Extensions.Logging.LoggerMessage> requiert l’analyse d’un modèle une seule fois quand le message est défini.</span><span class="sxs-lookup"><span data-stu-id="9524c-110"><xref:Microsoft.Extensions.Logging.LoggerMessage> only requires parsing a template once when the message is defined.</span></span>

<span data-ttu-id="9524c-111">L’exemple d’application illustre <xref:Microsoft.Extensions.Logging.LoggerMessage> des fonctionnalités avec un service Worker de traitement de la file d’attente prioritaire.</span><span class="sxs-lookup"><span data-stu-id="9524c-111">The sample app demonstrates <xref:Microsoft.Extensions.Logging.LoggerMessage> features with a priority queue processing worker service.</span></span> <span data-ttu-id="9524c-112">L’application traite les éléments de travail par ordre de priorité.</span><span class="sxs-lookup"><span data-stu-id="9524c-112">The app processes work items in priority order.</span></span> <span data-ttu-id="9524c-113">À mesure que ces opérations se produisent, des messages de journal sont générés à l’aide du modèle <xref:Microsoft.Extensions.Logging.LoggerMessage>.</span><span class="sxs-lookup"><span data-stu-id="9524c-113">As these operations occur, log messages are generated using the <xref:Microsoft.Extensions.Logging.LoggerMessage> pattern.</span></span>

## <a name="define-a-logger-message"></a><span data-ttu-id="9524c-114">Définir un message d’enregistreur d’événements</span><span class="sxs-lookup"><span data-stu-id="9524c-114">Define a logger message</span></span>

<span data-ttu-id="9524c-115">Utilisez [define (LogLevel, EventID, String)](xref:Microsoft.Extensions.Logging.LoggerMessage.Define%2A) pour créer un <xref:System.Action> délégué pour la journalisation d’un message.</span><span class="sxs-lookup"><span data-stu-id="9524c-115">Use [Define(LogLevel, EventId, String)](xref:Microsoft.Extensions.Logging.LoggerMessage.Define%2A) to create an <xref:System.Action> delegate for logging a message.</span></span> <span data-ttu-id="9524c-116">Les surcharges <xref:Microsoft.Extensions.Logging.LoggerMessage.Define%2A> permettent de passer jusqu’à six paramètres de type à une chaîne de format nommée (modèle).</span><span class="sxs-lookup"><span data-stu-id="9524c-116"><xref:Microsoft.Extensions.Logging.LoggerMessage.Define%2A> overloads permit passing up to six type parameters to a named format string (template).</span></span>

<span data-ttu-id="9524c-117">La chaîne fournie à la méthode <xref:Microsoft.Extensions.Logging.LoggerMessage.Define%2A> est un modèle et non pas une chaîne interpolée.</span><span class="sxs-lookup"><span data-stu-id="9524c-117">The string provided to the <xref:Microsoft.Extensions.Logging.LoggerMessage.Define%2A> method is a template and not an interpolated string.</span></span> <span data-ttu-id="9524c-118">Les espaces réservés sont remplis dans l’ordre dans lequel les types sont spécifiés.</span><span class="sxs-lookup"><span data-stu-id="9524c-118">Placeholders are filled in the order that the types are specified.</span></span> <span data-ttu-id="9524c-119">Les noms d’espace réservé dans le modèle doivent être descriptifs et cohérents d’un modèle à l’autre.</span><span class="sxs-lookup"><span data-stu-id="9524c-119">Placeholder names in the template should be descriptive and consistent across templates.</span></span> <span data-ttu-id="9524c-120">Ils servent de noms de propriété dans les données de journal structurées.</span><span class="sxs-lookup"><span data-stu-id="9524c-120">They serve as property names within structured log data.</span></span> <span data-ttu-id="9524c-121">Nous vous recommandons d’utiliser la [casse Pascal](../../standard/design-guidelines/capitalization-conventions.md) pour les noms d’espace réservé.</span><span class="sxs-lookup"><span data-stu-id="9524c-121">We recommend [Pascal casing](../../standard/design-guidelines/capitalization-conventions.md) for placeholder names.</span></span> <span data-ttu-id="9524c-122">Par exemple, `{Item}`, `{DateTime}`.</span><span class="sxs-lookup"><span data-stu-id="9524c-122">For example, `{Item}`, `{DateTime}`.</span></span>

<span data-ttu-id="9524c-123">Chaque message de journal est une <xref:System.Action> contenue dans un champ statique créé par [LoggerMessage.Define](xref:Microsoft.Extensions.Logging.LoggerMessage.Define%2A).</span><span class="sxs-lookup"><span data-stu-id="9524c-123">Each log message is an <xref:System.Action> held in a static field created by [LoggerMessage.Define](xref:Microsoft.Extensions.Logging.LoggerMessage.Define%2A).</span></span> <span data-ttu-id="9524c-124">Par exemple, l’exemple d’application crée un champ pour décrire un message de journal pour le traitement des éléments de travail :</span><span class="sxs-lookup"><span data-stu-id="9524c-124">For example, the sample app creates a field to describe a log message for the processing of work items:</span></span>

:::code language="csharp" source="snippets/configuration/worker-service-options/Extensions/LoggerExtensions.cs" id="FailedProcessingField":::

<span data-ttu-id="9524c-125">Pour l’<xref:System.Action>, spécifiez :</span><span class="sxs-lookup"><span data-stu-id="9524c-125">For the <xref:System.Action>, specify:</span></span>

- <span data-ttu-id="9524c-126">Le niveau du journal</span><span class="sxs-lookup"><span data-stu-id="9524c-126">The log level.</span></span>
- <span data-ttu-id="9524c-127">Un identificateur d’événement unique (<xref:Microsoft.Extensions.Logging.EventId>) avec le nom de la méthode d’extension statique</span><span class="sxs-lookup"><span data-stu-id="9524c-127">A unique event identifier (<xref:Microsoft.Extensions.Logging.EventId>) with the name of the static extension method.</span></span>
- <span data-ttu-id="9524c-128">Le modèle de message (chaîne de format nommée)</span><span class="sxs-lookup"><span data-stu-id="9524c-128">The message template (named format string).</span></span>

<span data-ttu-id="9524c-129">Comme les éléments de travail sont déplacés dans la file d’attente pour le traitement, l’application de service Worker définit :</span><span class="sxs-lookup"><span data-stu-id="9524c-129">As work items are dequeued for processing the worker service app sets the:</span></span>

- <span data-ttu-id="9524c-130">Le niveau de journal sur <xref:Microsoft.Extensions.Logging.LogLevel.Critical?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="9524c-130">Log level to <xref:Microsoft.Extensions.Logging.LogLevel.Critical?displayProperty=nameWithType>.</span></span>
- <span data-ttu-id="9524c-131">L’ID d’événement sur `13` avec le nom de la méthode `FailedToProcessWorkItem`</span><span class="sxs-lookup"><span data-stu-id="9524c-131">Event id to `13` with the name of the `FailedToProcessWorkItem` method.</span></span>
- <span data-ttu-id="9524c-132">Le modèle de message (chaîne de format nommée) sur une chaîne</span><span class="sxs-lookup"><span data-stu-id="9524c-132">Message template (named format string) to a string.</span></span>

:::code language="csharp" source="snippets/configuration/worker-service-options/Extensions/LoggerExtensions.cs" id="FailedProcessingAssignment":::

<span data-ttu-id="9524c-133">Des magasins de journalisation structurée peuvent utiliser le nom d’événement quand il est fourni avec l’ID d’événement pour enrichir la journalisation.</span><span class="sxs-lookup"><span data-stu-id="9524c-133">Structured logging stores may use the event name when it's supplied with the event id to enrich logging.</span></span> <span data-ttu-id="9524c-134">Par exemple, [Serilog](https://github.com/serilog/serilog-extensions-logging) utilise le nom d’événement.</span><span class="sxs-lookup"><span data-stu-id="9524c-134">For example, [Serilog](https://github.com/serilog/serilog-extensions-logging) uses the event name.</span></span>

<span data-ttu-id="9524c-135">L’<xref:System.Action> est appelée par le biais d’une méthode d’extension fortement typée.</span><span class="sxs-lookup"><span data-stu-id="9524c-135">The <xref:System.Action> is invoked through a strongly-typed extension method.</span></span> <span data-ttu-id="9524c-136">La `PriorityItemProcessed` méthode journalise un message chaque fois qu’un élément de travail est en cours de traitement.</span><span class="sxs-lookup"><span data-stu-id="9524c-136">The `PriorityItemProcessed` method logs a message every time a work item is being processed.</span></span> <span data-ttu-id="9524c-137">En revanche, `FailedToProcessWorkItem` est appelé quand (et si) une exception se produit :</span><span class="sxs-lookup"><span data-stu-id="9524c-137">Whereas, `FailedToProcessWorkItem` is called when (and if) an exception occurs:</span></span>

:::code language="csharp" source="snippets/configuration/worker-service-options/Worker.cs" range="18-39" highlight="15-18":::

<span data-ttu-id="9524c-138">Examinez la sortie de la console de l’application :</span><span class="sxs-lookup"><span data-stu-id="9524c-138">Inspect the app's console output:</span></span>

```console
crit: WorkerServiceOptions.Example.Worker[13]
      Epic failure processing item!
      System.Exception: Failed to verify communications.
         at WorkerServiceOptions.Example.Worker.ExecuteAsync(CancellationToken stoppingToken) in
         ..\Worker.cs:line 27
```

<span data-ttu-id="9524c-139">Pour passer des paramètres à un message de journal, définissez jusqu’à six types au moment de la création du champ statique.</span><span class="sxs-lookup"><span data-stu-id="9524c-139">To pass parameters to a log message, define up to six types when creating the static field.</span></span> <span data-ttu-id="9524c-140">L’exemple d’application enregistre les détails de l’élément de travail lors du traitement des éléments en définissant un `WorkItem` type pour le <xref:System.Action> champ :</span><span class="sxs-lookup"><span data-stu-id="9524c-140">The sample app logs the work item details when processing items by defining a `WorkItem` type for the <xref:System.Action> field:</span></span>

:::code language="csharp" source="snippets/configuration/worker-service-options/Extensions/LoggerExtensions.cs" id="ProcessingItemField":::

<span data-ttu-id="9524c-141">Le modèle de message de journal du délégué reçoit ses valeurs d’espace réservé des types fournis.</span><span class="sxs-lookup"><span data-stu-id="9524c-141">The delegate's log message template receives its placeholder values from the types provided.</span></span> <span data-ttu-id="9524c-142">L’exemple d’application définit un délégué pour ajouter un élément de travail où le paramètre d’élément est `WorkItem` :</span><span class="sxs-lookup"><span data-stu-id="9524c-142">The sample app defines a delegate for adding a work item where the item parameter is a `WorkItem`:</span></span>

:::code language="csharp" source="snippets/configuration/worker-service-options/Extensions/LoggerExtensions.cs" id="ProcessingItemAssignment":::

<span data-ttu-id="9524c-143">La méthode d’extension statique pour la journalisation qu’un élément de travail est en cours de traitement, `PriorityItemProcessed` , reçoit la valeur de l’argument d’élément de travail et la passe au <xref:System.Action> délégué :</span><span class="sxs-lookup"><span data-stu-id="9524c-143">The static extension method for logging that a work item is being processed, `PriorityItemProcessed`, receives the work item argument value and passes it to the <xref:System.Action> delegate:</span></span>

:::code language="csharp" source="snippets/configuration/worker-service-options/Extensions/LoggerExtensions.cs" id="ProcessingItemMethod":::

<span data-ttu-id="9524c-144">Dans la méthode du service Worker `ExecuteAsync` , `PriorityItemProcessed` est appelé pour enregistrer le message :</span><span class="sxs-lookup"><span data-stu-id="9524c-144">In the worker service's `ExecuteAsync` method, `PriorityItemProcessed` is called to log the message:</span></span>

:::code language="csharp" source="snippets/configuration/worker-service-options/Worker.cs" range="18-39" highlight="12":::

<span data-ttu-id="9524c-145">Examinez la sortie de la console de l’application :</span><span class="sxs-lookup"><span data-stu-id="9524c-145">Inspect the app's console output:</span></span>

```console
info: WorkerServiceOptions.Example.Worker[1]
      Processing priority item: Priority-Extreme (50db062a-9732-4418-936d-110549ad79e4): 'Verify communications'
```

## <a name="define-logger-message-scope"></a><span data-ttu-id="9524c-146">Définir la portée du message de l’enregistreur</span><span class="sxs-lookup"><span data-stu-id="9524c-146">Define logger message scope</span></span>

<span data-ttu-id="9524c-147">La méthode [DefineScope (String)](xref:Microsoft.Extensions.Logging.LoggerMessage.DefineScope%2A) crée un <xref:System.Func%601> délégué pour définir une [étendue de journal](logging.md#log-scopes).</span><span class="sxs-lookup"><span data-stu-id="9524c-147">The [DefineScope(string)](xref:Microsoft.Extensions.Logging.LoggerMessage.DefineScope%2A) method creates a <xref:System.Func%601> delegate for defining a [log scope](logging.md#log-scopes).</span></span> <span data-ttu-id="9524c-148">Les surcharges <xref:Microsoft.Extensions.Logging.LoggerMessage.DefineScope%2A> permettent de passer jusqu’à trois paramètres de type à une chaîne de format nommée (modèle).</span><span class="sxs-lookup"><span data-stu-id="9524c-148"><xref:Microsoft.Extensions.Logging.LoggerMessage.DefineScope%2A> overloads permit passing up to three type parameters to a named format string (template).</span></span>

<span data-ttu-id="9524c-149">Comme c’est le cas avec la méthode <xref:Microsoft.Extensions.Logging.LoggerMessage.Define%2A>, la chaîne fournie à la méthode <xref:Microsoft.Extensions.Logging.LoggerMessage.DefineScope%2A> est un modèle et non pas une chaîne interpolée.</span><span class="sxs-lookup"><span data-stu-id="9524c-149">As is the case with the <xref:Microsoft.Extensions.Logging.LoggerMessage.Define%2A> method, the string provided to the <xref:Microsoft.Extensions.Logging.LoggerMessage.DefineScope%2A> method is a template and not an interpolated string.</span></span> <span data-ttu-id="9524c-150">Les espaces réservés sont remplis dans l’ordre dans lequel les types sont spécifiés.</span><span class="sxs-lookup"><span data-stu-id="9524c-150">Placeholders are filled in the order that the types are specified.</span></span> <span data-ttu-id="9524c-151">Les noms d’espace réservé dans le modèle doivent être descriptifs et cohérents d’un modèle à l’autre.</span><span class="sxs-lookup"><span data-stu-id="9524c-151">Placeholder names in the template should be descriptive and consistent across templates.</span></span> <span data-ttu-id="9524c-152">Ils servent de noms de propriété dans les données de journal structurées.</span><span class="sxs-lookup"><span data-stu-id="9524c-152">They serve as property names within structured log data.</span></span> <span data-ttu-id="9524c-153">Nous vous recommandons d’utiliser la [casse Pascal](../../standard/design-guidelines/capitalization-conventions.md) pour les noms d’espace réservé.</span><span class="sxs-lookup"><span data-stu-id="9524c-153">We recommend [Pascal casing](../../standard/design-guidelines/capitalization-conventions.md) for placeholder names.</span></span> <span data-ttu-id="9524c-154">Par exemple, `{Item}`, `{DateTime}`.</span><span class="sxs-lookup"><span data-stu-id="9524c-154">For example, `{Item}`, `{DateTime}`.</span></span>

<span data-ttu-id="9524c-155">Définissez une [étendue de journal](logging.md#log-scopes) à appliquer à une série de messages de journal à l’aide de la méthode <xref:Microsoft.Extensions.Logging.LoggerMessage.DefineScope%2A>.</span><span class="sxs-lookup"><span data-stu-id="9524c-155">Define a [log scope](logging.md#log-scopes) to apply to a series of log messages using the <xref:Microsoft.Extensions.Logging.LoggerMessage.DefineScope%2A> method.</span></span> <span data-ttu-id="9524c-156">Activez `IncludeScopes` dans la section du journaliseur de console *d’appsettings.json* :</span><span class="sxs-lookup"><span data-stu-id="9524c-156">Enable `IncludeScopes` in the console logger section of *appsettings.json*:</span></span>

:::code language="json" source="snippets/configuration/worker-service-options/appsettings.json" highlight="3-5":::

<span data-ttu-id="9524c-157">Pour créer une étendue de journal, ajoutez un champ destiné à contenir un délégué <xref:System.Func%601> pour l’étendue.</span><span class="sxs-lookup"><span data-stu-id="9524c-157">To create a log scope, add a field to hold a <xref:System.Func%601> delegate for the scope.</span></span> <span data-ttu-id="9524c-158">L’exemple d’application crée un champ intitulé `_processingWorkScope` (*Internal/LoggerExtensions.cs*) :</span><span class="sxs-lookup"><span data-stu-id="9524c-158">The sample app creates a field called `_processingWorkScope` (*Internal/LoggerExtensions.cs*):</span></span>

:::code language="csharp" source="snippets/configuration/worker-service-options/Extensions/LoggerExtensions.cs" id="ProcessingWorkField":::

<span data-ttu-id="9524c-159">Utilisez <xref:Microsoft.Extensions.Logging.LoggerMessage.DefineScope%2A> pour créer le délégué.</span><span class="sxs-lookup"><span data-stu-id="9524c-159">Use <xref:Microsoft.Extensions.Logging.LoggerMessage.DefineScope%2A> to create the delegate.</span></span> <span data-ttu-id="9524c-160">Vous pouvez spécifier jusqu’à trois types à utiliser comme arguments de modèle quand le délégué est appelé.</span><span class="sxs-lookup"><span data-stu-id="9524c-160">Up to three types can be specified for use as template arguments when the delegate is invoked.</span></span> <span data-ttu-id="9524c-161">L’exemple d’application utilise un modèle de message qui comprend la date et l’heure de début du traitement :</span><span class="sxs-lookup"><span data-stu-id="9524c-161">The sample app uses a message template that includes the date time in which processing started:</span></span>

:::code language="csharp" source="snippets/configuration/worker-service-options/Extensions/LoggerExtensions.cs" id="ProcessingWorkAssignment":::

<span data-ttu-id="9524c-162">Fournissez une méthode d’extension statique pour le message de journal.</span><span class="sxs-lookup"><span data-stu-id="9524c-162">Provide a static extension method for the log message.</span></span> <span data-ttu-id="9524c-163">Incluez tous les paramètres de type pour les propriétés nommées qui s’affichent dans le modèle de message.</span><span class="sxs-lookup"><span data-stu-id="9524c-163">Include any type parameters for named properties that appear in the message template.</span></span> <span data-ttu-id="9524c-164">L’exemple d’application prend un `DateTime` pour un horodatage personnalisé à enregistrer et retourne `_processingWorkScope` :</span><span class="sxs-lookup"><span data-stu-id="9524c-164">The sample app takes in a `DateTime` for a custom time stamp to log and returns `_processingWorkScope`:</span></span>

:::code language="csharp" source="snippets/configuration/worker-service-options/Extensions/LoggerExtensions.cs" id="ProcessingWorkMethod":::

<span data-ttu-id="9524c-165">L’étendue inclut les appels d’extension de journalisation dans un bloc [using](../../csharp/language-reference/keywords/using-statement.md) :</span><span class="sxs-lookup"><span data-stu-id="9524c-165">The scope wraps the logging extension calls in a [using](../../csharp/language-reference/keywords/using-statement.md) block:</span></span>

:::code language="csharp" source="snippets/configuration/worker-service-options/Worker.cs" range="18-39" highlight="4":::

<span data-ttu-id="9524c-166">Examinez les messages de journal dans la sortie de la console de l’application.</span><span class="sxs-lookup"><span data-stu-id="9524c-166">Inspect the log messages in the app's console output.</span></span> <span data-ttu-id="9524c-167">Le résultat suivant montre l’ordre de priorité des messages de journal avec le message d’étendue du journal inclus :</span><span class="sxs-lookup"><span data-stu-id="9524c-167">The following result shows priority ordering of log messages with the log scope message included:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="9524c-168">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9524c-168">See also</span></span>

- [<span data-ttu-id="9524c-169">Journalisation dans .NET</span><span class="sxs-lookup"><span data-stu-id="9524c-169">Logging in .NET</span></span>](logging.md)
