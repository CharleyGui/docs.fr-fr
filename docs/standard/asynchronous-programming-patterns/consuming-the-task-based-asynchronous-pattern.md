---
title: Utilisation du modèle asynchrone basé sur les tâches
description: Apprenez à utiliser le modèle asynchrone basé sur des tâches (TAP) quand vous travaillez avec des opérations asynchrones.
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- .NET and TAP
- asynchronous design patterns, .NET
- TAP, .NET support for
- Task-based Asynchronous Pattern, .NET support for
- .NET, asynchronous design patterns
ms.assetid: 033cf871-ae24-433d-8939-7a3793e547bf
ms.openlocfilehash: 4a2715ab6572c33a1564986c5cfda112d5fa11db
ms.sourcegitcommit: 4a938327bad8b2e20cabd0f46a9dc50882596f13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/28/2020
ms.locfileid: "92888865"
---
# <a name="consuming-the-task-based-asynchronous-pattern"></a><span data-ttu-id="4cac9-103">Utilisation du modèle asynchrone basé sur les tâches</span><span class="sxs-lookup"><span data-stu-id="4cac9-103">Consuming the Task-based Asynchronous Pattern</span></span>

<span data-ttu-id="4cac9-104">Lorsque vous utilisez le modèle asynchrone basé sur les tâches (TAP) pour travailler avec des opérations asynchrones, vous pouvez utiliser des rappels pour terminer l’attente sans blocage.</span><span class="sxs-lookup"><span data-stu-id="4cac9-104">When you use the Task-based Asynchronous Pattern (TAP) to work with asynchronous operations, you can use callbacks to achieve waiting without blocking.</span></span> <span data-ttu-id="4cac9-105">Pour les tâches, vous pouvez faire de même à l’aide de méthodes telles que <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4cac9-105">For tasks, this is achieved through methods such as <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="4cac9-106">La prise en charge asynchrone basée sur le langage masque les rappels en permettant aux opérations asynchrones d’être attendues dans le flux de contrôle normal, et le code généré par le compilateur fournit cette même prise en charge au niveau de l’API.</span><span class="sxs-lookup"><span data-stu-id="4cac9-106">Language-based asynchronous support hides callbacks by allowing asynchronous operations to be awaited within normal control flow, and compiler-generated code provides this same API-level support.</span></span>

## <a name="suspending-execution-with-await"></a><span data-ttu-id="4cac9-107">Suspension de l’exécution avec Await</span><span class="sxs-lookup"><span data-stu-id="4cac9-107">Suspending Execution with Await</span></span>

<span data-ttu-id="4cac9-108">Vous pouvez utiliser le mot clé [await](../../csharp/language-reference/operators/await.md) en C# et l' [opérateur await](../../visual-basic/language-reference/operators/await-operator.md) dans Visual Basic pour attendre de façon asynchrone <xref:System.Threading.Tasks.Task> les objets await et <xref:System.Threading.Tasks.Task%601> .</span><span class="sxs-lookup"><span data-stu-id="4cac9-108">You can use the [await](../../csharp/language-reference/operators/await.md) keyword in C# and the [Await Operator](../../visual-basic/language-reference/operators/await-operator.md) in Visual Basic to asynchronously await <xref:System.Threading.Tasks.Task> and <xref:System.Threading.Tasks.Task%601> objects.</span></span> <span data-ttu-id="4cac9-109">Quand vous attendez une <xref:System.Threading.Tasks.Task>, l’expression `await` est de type `void`.</span><span class="sxs-lookup"><span data-stu-id="4cac9-109">When you're awaiting a <xref:System.Threading.Tasks.Task>, the `await` expression is of type `void`.</span></span> <span data-ttu-id="4cac9-110">Quand vous attendez une <xref:System.Threading.Tasks.Task%601>, l’expression `await` est de type `TResult`.</span><span class="sxs-lookup"><span data-stu-id="4cac9-110">When you're awaiting a <xref:System.Threading.Tasks.Task%601>, the `await` expression is of type `TResult`.</span></span> <span data-ttu-id="4cac9-111">Une expression `await` doit se produire dans le corps d’une méthode asynchrone.</span><span class="sxs-lookup"><span data-stu-id="4cac9-111">An `await` expression must occur inside the body of an asynchronous method.</span></span> <span data-ttu-id="4cac9-112">(Ces fonctionnalités de langage ont été introduites dans .NET Framework 4,5.)</span><span class="sxs-lookup"><span data-stu-id="4cac9-112">(These language features were introduced in .NET Framework 4.5.)</span></span>

 <span data-ttu-id="4cac9-113">En arrière-plan, la fonctionnalité await installe un rappel sur la tâche à l’aide d’une continuation.</span><span class="sxs-lookup"><span data-stu-id="4cac9-113">Under the covers, the await functionality installs a callback on the task by using a continuation.</span></span>  <span data-ttu-id="4cac9-114">Ce rappel reprend la méthode asynchrone au point d’interruption.</span><span class="sxs-lookup"><span data-stu-id="4cac9-114">This callback resumes the asynchronous method at the point of suspension.</span></span> <span data-ttu-id="4cac9-115">Quand la méthode asynchrone est reprise, si l’opération attendue s’est terminée correctement et est une <xref:System.Threading.Tasks.Task%601>, son `TResult` est retourné.</span><span class="sxs-lookup"><span data-stu-id="4cac9-115">When the asynchronous method is resumed, if the awaited operation completed successfully and was a <xref:System.Threading.Tasks.Task%601>, its `TResult` is returned.</span></span>  <span data-ttu-id="4cac9-116">Si la <xref:System.Threading.Tasks.Task> ou <xref:System.Threading.Tasks.Task%601> attendue s’est terminée dans l’état <xref:System.Threading.Tasks.TaskStatus.Canceled>, une exception <xref:System.OperationCanceledException> est levée.</span><span class="sxs-lookup"><span data-stu-id="4cac9-116">If the <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601> that was awaited ended in the <xref:System.Threading.Tasks.TaskStatus.Canceled> state, an <xref:System.OperationCanceledException> exception is thrown.</span></span>  <span data-ttu-id="4cac9-117">Si la <xref:System.Threading.Tasks.Task> ou <xref:System.Threading.Tasks.Task%601> attendue s’est terminée dans l’état <xref:System.Threading.Tasks.TaskStatus.Faulted>, l’exception qui a entraîné l’erreur est levée.</span><span class="sxs-lookup"><span data-stu-id="4cac9-117">If the <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601> that was awaited ended in the <xref:System.Threading.Tasks.TaskStatus.Faulted> state, the exception that caused it to fault is thrown.</span></span> <span data-ttu-id="4cac9-118">Une `Task` peut échouer à cause de plusieurs exceptions, mais seule une de ces exceptions est propagée.</span><span class="sxs-lookup"><span data-stu-id="4cac9-118">A `Task` can fault as a result of multiple exceptions, but only one of these exceptions is propagated.</span></span> <span data-ttu-id="4cac9-119">Toutefois, la propriété <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> retourne une exception <xref:System.AggregateException> qui contient toutes les erreurs.</span><span class="sxs-lookup"><span data-stu-id="4cac9-119">However, the <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> property returns an <xref:System.AggregateException> exception that contains all the errors.</span></span>

 <span data-ttu-id="4cac9-120">Si un contexte de synchronisation ( <xref:System.Threading.SynchronizationContext> objet) est associé au thread qui exécutait la méthode asynchrone au moment de la suspension (par exemple, si la <xref:System.Threading.SynchronizationContext.Current%2A?displayProperty=nameWithType> propriété n’est pas `null` ), la méthode asynchrone reprend sur ce même contexte de synchronisation à l’aide de la <xref:System.Threading.SynchronizationContext.Post%2A> méthode du contexte.</span><span class="sxs-lookup"><span data-stu-id="4cac9-120">If a synchronization context (<xref:System.Threading.SynchronizationContext> object) is associated with the thread that was executing the asynchronous method at the time of suspension (for example, if the <xref:System.Threading.SynchronizationContext.Current%2A?displayProperty=nameWithType> property is not `null`), the asynchronous method resumes on that same synchronization context by using the context's <xref:System.Threading.SynchronizationContext.Post%2A> method.</span></span> <span data-ttu-id="4cac9-121">Dans le cas contraire, elle s’appuie sur le planificateur de tâches (objet <xref:System.Threading.Tasks.TaskScheduler>) qui était en cours au moment de la suspension.</span><span class="sxs-lookup"><span data-stu-id="4cac9-121">Otherwise, it relies on the task scheduler (<xref:System.Threading.Tasks.TaskScheduler> object) that was current at the time of suspension.</span></span> <span data-ttu-id="4cac9-122">En général, il s’agit du planificateur de tâches par défaut (<xref:System.Threading.Tasks.TaskScheduler.Default%2A?displayProperty=nameWithType>), qui cible le pool de threads.</span><span class="sxs-lookup"><span data-stu-id="4cac9-122">Typically, this is the default task scheduler (<xref:System.Threading.Tasks.TaskScheduler.Default%2A?displayProperty=nameWithType>), which targets the thread pool.</span></span> <span data-ttu-id="4cac9-123">Le planificateur de tâches détermine si l’opération asynchrone attendue doit reprendre où elle s’est terminée ou si la reprise doit être planifiée.</span><span class="sxs-lookup"><span data-stu-id="4cac9-123">This task scheduler determines whether the awaited asynchronous operation should resume where it completed or whether the resumption should be scheduled.</span></span> <span data-ttu-id="4cac9-124">Le planificateur par défaut permet généralement à la continuation de s’exécuter sur le thread qui a effectué l’opération attendue.</span><span class="sxs-lookup"><span data-stu-id="4cac9-124">The default scheduler typically allows the continuation to run on the thread that the awaited operation completed.</span></span>

 <span data-ttu-id="4cac9-125">Lorsqu’une méthode asynchrone est appelée, elle exécute simultanément le corps de la fonction jusqu'à la première expression await sur une instance prenant en charge await qui n’est pas encore terminée. À ce moment, l’appel retourne à l’appelant.</span><span class="sxs-lookup"><span data-stu-id="4cac9-125">When an asynchronous method is called, it synchronously executes the body of the function up until the first await expression on an awaitable instance that has not yet completed, at which point the invocation returns to the caller.</span></span> <span data-ttu-id="4cac9-126">Si la méthode asynchrone ne retourne pas `void`, un objet <xref:System.Threading.Tasks.Task> ou <xref:System.Threading.Tasks.Task%601> est retourné pour représenter le calcul en cours.</span><span class="sxs-lookup"><span data-stu-id="4cac9-126">If the asynchronous method does not return `void`, a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601> object is returned to represent the ongoing computation.</span></span> <span data-ttu-id="4cac9-127">Dans une méthode asynchrone non void, si une instruction de retour est rencontrée ou si la fin du corps de la méthode est atteinte, la tâche est terminée dans l’état final <xref:System.Threading.Tasks.TaskStatus.RanToCompletion>.</span><span class="sxs-lookup"><span data-stu-id="4cac9-127">In a non-void asynchronous method, if a return statement is encountered or the end of the method body is reached, the task is completed in the <xref:System.Threading.Tasks.TaskStatus.RanToCompletion> final state.</span></span> <span data-ttu-id="4cac9-128">Si une exception non gérée cause la sortie du contrôle du corps de la méthode asynchrone, la tâche se termine dans l’état <xref:System.Threading.Tasks.TaskStatus.Faulted>.</span><span class="sxs-lookup"><span data-stu-id="4cac9-128">If an unhandled exception causes control to leave the body of the asynchronous method, the task ends in the <xref:System.Threading.Tasks.TaskStatus.Faulted> state.</span></span> <span data-ttu-id="4cac9-129">S’il s’agit d’une exception <xref:System.OperationCanceledException>, la tâche se termine dans l’état <xref:System.Threading.Tasks.TaskStatus.Canceled>.</span><span class="sxs-lookup"><span data-stu-id="4cac9-129">If that exception is an <xref:System.OperationCanceledException>, the task instead ends in the <xref:System.Threading.Tasks.TaskStatus.Canceled> state.</span></span> <span data-ttu-id="4cac9-130">De cette manière, la publication du résultat ou de l’exception a finalement lieu.</span><span class="sxs-lookup"><span data-stu-id="4cac9-130">In this manner, the result or exception is eventually published.</span></span>

 <span data-ttu-id="4cac9-131">Il existe plusieurs variations importantes de ce comportement.</span><span class="sxs-lookup"><span data-stu-id="4cac9-131">There are several important variations of this behavior.</span></span>  <span data-ttu-id="4cac9-132">Pour des raisons de performances, si une tâche est déjà terminée au moment où la tâche est attendue avec await, le contrôle n’est pas transmis et la fonction continue à s’exécuter.</span><span class="sxs-lookup"><span data-stu-id="4cac9-132">For performance reasons, if a task has already completed by the time the task is awaited, control is not yielded, and the function continues to execute.</span></span>  <span data-ttu-id="4cac9-133">En outre, le retour au contexte d’origine n’est pas toujours souhaitable et ce comportement peut être modifié. Cette opération est décrite plus en détail dans la section suivante.</span><span class="sxs-lookup"><span data-stu-id="4cac9-133">Additionally, returning to the original context isn't always the desired behavior and can be changed; this is described in more detail in the next section.</span></span>

### <a name="configuring-suspension-and-resumption-with-yield-and-configureawait"></a><span data-ttu-id="4cac9-134">Configuration de la suspension et de la reprise avec Yield et ConfigureAwait</span><span class="sxs-lookup"><span data-stu-id="4cac9-134">Configuring Suspension and Resumption with Yield and ConfigureAwait</span></span>
 <span data-ttu-id="4cac9-135">Plusieurs méthodes fournissent davantage de contrôle sur l’exécution d’une méthode asynchrone.</span><span class="sxs-lookup"><span data-stu-id="4cac9-135">Several methods provide more control over an asynchronous method's execution.</span></span> <span data-ttu-id="4cac9-136">Par exemple, vous pouvez utiliser la méthode <xref:System.Threading.Tasks.Task.Yield%2A?displayProperty=nameWithType> pour introduire un point de transmission dans la méthode asynchrone :</span><span class="sxs-lookup"><span data-stu-id="4cac9-136">For example, you can use the <xref:System.Threading.Tasks.Task.Yield%2A?displayProperty=nameWithType> method to introduce a yield point into the asynchronous method:</span></span>

```csharp
public class Task : …
{
    public static YieldAwaitable Yield();
    …
}
```

 <span data-ttu-id="4cac9-137">Cela équivaut à la publication asynchrone ou à la replanification vers le contexte actuel.</span><span class="sxs-lookup"><span data-stu-id="4cac9-137">This is equivalent to asynchronously posting or scheduling back to the current context.</span></span>

```csharp
Task.Run(async delegate
{
    for(int i=0; i<1000000; i++)
    {
        await Task.Yield(); // fork the continuation into a separate work item
        ...
    }
});
```

 <span data-ttu-id="4cac9-138">Vous pouvez également utiliser la méthode <xref:System.Threading.Tasks.Task.ConfigureAwait%2A?displayProperty=nameWithType> pour mieux contrôler la suspension et la reprise dans une méthode asynchrone.</span><span class="sxs-lookup"><span data-stu-id="4cac9-138">You can also use the <xref:System.Threading.Tasks.Task.ConfigureAwait%2A?displayProperty=nameWithType> method for better control over suspension and resumption in an asynchronous method.</span></span>  <span data-ttu-id="4cac9-139">Comme mentionné précédemment, par défaut, le contexte actuel est capturé au moment où une méthode asynchrone est interrompue, et ce contexte capturé est utilisé pour appeler la continuation de la méthode asynchrone lors de la reprise.</span><span class="sxs-lookup"><span data-stu-id="4cac9-139">As mentioned previously, by default, the current context is captured at the time an asynchronous  method is suspended, and that captured context is used to invoke the asynchronous  method's continuation upon resumption.</span></span>  <span data-ttu-id="4cac9-140">Dans de nombreux cas, il s’agit du comportement exact que vous souhaitez.</span><span class="sxs-lookup"><span data-stu-id="4cac9-140">In many cases, this is the exact behavior you want.</span></span>  <span data-ttu-id="4cac9-141">Dans d’autres cas, vous pouvez ne pas vous soucier du contexte de continuation, et vous pouvez obtenir de meilleures performances en évitant d’effectuer ces publications vers le contexte d’origine.</span><span class="sxs-lookup"><span data-stu-id="4cac9-141">In other cases, you may not care about the continuation context, and you can achieve better performance by avoiding such posts back to the original context.</span></span>  <span data-ttu-id="4cac9-142">Pour ce faire, utilisez la méthode <xref:System.Threading.Tasks.Task.ConfigureAwait%2A?displayProperty=nameWithType> pour informer l’opération await de ne pas capturer et reprendre sur le contexte, mais plutôt de poursuivre l’exécution quand l’opération asynchrone attendue est terminée :</span><span class="sxs-lookup"><span data-stu-id="4cac9-142">To enable this, use the <xref:System.Threading.Tasks.Task.ConfigureAwait%2A?displayProperty=nameWithType> method to inform the await operation not to capture and resume on the context, but to continue execution wherever the asynchronous operation that was being awaited completed:</span></span>

```csharp
await someTask.ConfigureAwait(continueOnCapturedContext:false);
```

## <a name="canceling-an-asynchronous-operation"></a><span data-ttu-id="4cac9-143">Annulation d'une opération asynchrone</span><span class="sxs-lookup"><span data-stu-id="4cac9-143">Canceling an Asynchronous Operation</span></span>

<span data-ttu-id="4cac9-144">À partir de .NET Framework 4, les méthodes TAP qui prennent en charge l’annulation fournissent au moins une surcharge qui accepte un jeton d’annulation ( <xref:System.Threading.CancellationToken> objet).</span><span class="sxs-lookup"><span data-stu-id="4cac9-144">Starting with .NET Framework 4, TAP methods that support cancellation provide at least one overload that accepts a cancellation token (<xref:System.Threading.CancellationToken> object).</span></span>

 <span data-ttu-id="4cac9-145">Un jeton d’annulation est créé via une source de jeton d’annulation (objet <xref:System.Threading.CancellationTokenSource>).</span><span class="sxs-lookup"><span data-stu-id="4cac9-145">A cancellation token is created through a cancellation token source (<xref:System.Threading.CancellationTokenSource> object).</span></span>  <span data-ttu-id="4cac9-146">La propriété de la source <xref:System.Threading.CancellationTokenSource.Token%2A> retourne le jeton d’annulation qui sera signalé lorsque la méthode de la source sera <xref:System.Threading.CancellationTokenSource.Cancel%2A> appelée.</span><span class="sxs-lookup"><span data-stu-id="4cac9-146">The source's <xref:System.Threading.CancellationTokenSource.Token%2A> property returns the cancellation token that will be signaled when the source's <xref:System.Threading.CancellationTokenSource.Cancel%2A> method is called.</span></span>  <span data-ttu-id="4cac9-147">Par exemple, si vous souhaitez télécharger une seule page Web et que vous souhaitez être en mesure d’annuler l’opération, vous créez un <xref:System.Threading.CancellationTokenSource> objet, vous transmettez son jeton à la méthode TAP, puis vous appelez la méthode de la source <xref:System.Threading.CancellationTokenSource.Cancel%2A> lorsque vous êtes prêt à annuler l’opération :</span><span class="sxs-lookup"><span data-stu-id="4cac9-147">For example, if you want to download a single webpage and you want to be able to cancel the operation, you create a <xref:System.Threading.CancellationTokenSource> object, pass its token to the TAP method, and then call the source's <xref:System.Threading.CancellationTokenSource.Cancel%2A> method when you're ready to cancel the operation:</span></span>

```csharp
var cts = new CancellationTokenSource();
string result = await DownloadStringAsync(url, cts.Token);
… // at some point later, potentially on another thread
cts.Cancel();
```

 <span data-ttu-id="4cac9-148">Pour annuler plusieurs appels asynchrones, vous pouvez passer le même jeton pour tous les appels :</span><span class="sxs-lookup"><span data-stu-id="4cac9-148">To cancel multiple asynchronous invocations, you can pass the same token to all invocations:</span></span>

```csharp
var cts = new CancellationTokenSource();
    IList<string> results = await Task.WhenAll(from url in urls select DownloadStringAsync(url, cts.Token));
    // at some point later, potentially on another thread
    …
    cts.Cancel();
```

 <span data-ttu-id="4cac9-149">Ou bien, vous pouvez passer le même jeton à un sous-ensemble sélectif d’opérations :</span><span class="sxs-lookup"><span data-stu-id="4cac9-149">Or, you can pass the same token to a selective subset of operations:</span></span>

```csharp
var cts = new CancellationTokenSource();
    byte [] data = await DownloadDataAsync(url, cts.Token);
    await SaveToDiskAsync(outputPath, data, CancellationToken.None);
    … // at some point later, potentially on another thread
    cts.Cancel();
```

 <span data-ttu-id="4cac9-150">Les demandes d’annulation peuvent être lancées à partir de n’importe quel thread.</span><span class="sxs-lookup"><span data-stu-id="4cac9-150">Cancellation requests may be initiated from any thread.</span></span>

 <span data-ttu-id="4cac9-151">Vous pouvez passer la valeur <xref:System.Threading.CancellationToken.None%2A?displayProperty=nameWithType> à toute méthode qui accepte les jetons d’annulation pour indiquer que l’annulation ne sera jamais demandée.</span><span class="sxs-lookup"><span data-stu-id="4cac9-151">You can pass the <xref:System.Threading.CancellationToken.None%2A?displayProperty=nameWithType> value to any method that accepts a cancellation token to indicate that cancellation will never be requested.</span></span>  <span data-ttu-id="4cac9-152">La propriété <xref:System.Threading.CancellationToken.CanBeCanceled%2A?displayProperty=nameWithType> retourne alors `false`, et la méthode appelée peut optimiser en conséquence.</span><span class="sxs-lookup"><span data-stu-id="4cac9-152">This causes the <xref:System.Threading.CancellationToken.CanBeCanceled%2A?displayProperty=nameWithType> property to return `false`, and the called method can optimize accordingly.</span></span>  <span data-ttu-id="4cac9-153">À des fins de test, vous pouvez également transmettre un jeton pré-annulation instancié à l’aide du constructeur qui accepte une valeur booléenne pour indiquer si le jeton doit démarrer dans un état non annulable ou déjà annulé.</span><span class="sxs-lookup"><span data-stu-id="4cac9-153">For testing purposes, you can also pass in a pre-canceled cancellation token that is instantiated by using the constructor that accepts a Boolean value to indicate whether the token should start in an already-canceled or not-cancelable state.</span></span>

 <span data-ttu-id="4cac9-154">Cette approche de l’annulation présente plusieurs avantages :</span><span class="sxs-lookup"><span data-stu-id="4cac9-154">This approach to cancellation has several advantages:</span></span>

- <span data-ttu-id="4cac9-155">Vous pouvez passer le même jeton d’annulation à n’importe quel nombre d’opérations asynchrones ou synchrones.</span><span class="sxs-lookup"><span data-stu-id="4cac9-155">You can pass the same cancellation token to any number of asynchronous and synchronous operations.</span></span>

- <span data-ttu-id="4cac9-156">La même demande d’annulation peut être déployée vers n’importe quel nombre d’écouteurs.</span><span class="sxs-lookup"><span data-stu-id="4cac9-156">The same cancellation request may be proliferated to any number of listeners.</span></span>

- <span data-ttu-id="4cac9-157">Le développeur de l’API asynchrone a le contrôle complet de la possibilité de demander l’annulation et du timing de la prise d’effet.</span><span class="sxs-lookup"><span data-stu-id="4cac9-157">The developer of the asynchronous API is in complete control of whether cancellation may be requested and when it may take effect.</span></span>

- <span data-ttu-id="4cac9-158">Le code qui utilise l’API peut déterminer de manière sélective les appels asynchrones qui seront transmis aux demandes d’annulation.</span><span class="sxs-lookup"><span data-stu-id="4cac9-158">The code that consumes the API may selectively determine the asynchronous invocations that cancellation requests will be propagated to.</span></span>

## <a name="monitoring-progress"></a><span data-ttu-id="4cac9-159">Contrôle de la progression</span><span class="sxs-lookup"><span data-stu-id="4cac9-159">Monitoring Progress</span></span>
 <span data-ttu-id="4cac9-160">Certaines méthodes asynchrones exposent la progression via une interface de progression transmise à la méthode asynchrone.</span><span class="sxs-lookup"><span data-stu-id="4cac9-160">Some asynchronous methods expose progress through a progress interface passed into the asynchronous method.</span></span>  <span data-ttu-id="4cac9-161">Par exemple, considérez une fonction qui télécharge de façon asynchrone une chaîne de texte et, en cours de route, génère des mises à jour de progression qui incluent le pourcentage du téléchargement effectué jusqu’à présent.</span><span class="sxs-lookup"><span data-stu-id="4cac9-161">For example, consider a function that asynchronously downloads a string of text, and along the way raises progress updates that include the percentage of the download that has completed thus far.</span></span>  <span data-ttu-id="4cac9-162">Cette méthode peut être utilisée dans une application Windows Presentation Foundation (WPF), comme suit :</span><span class="sxs-lookup"><span data-stu-id="4cac9-162">Such a method could be consumed in a Windows Presentation Foundation (WPF) application as follows:</span></span>

```csharp
private async void btnDownload_Click(object sender, RoutedEventArgs e)
{
    btnDownload.IsEnabled = false;
    try
    {
        txtResult.Text = await DownloadStringAsync(txtUrl.Text,
            new Progress<int>(p => pbDownloadProgress.Value = p));
    }
    finally { btnDownload.IsEnabled = true; }
}
```

<a name="combinators"></a>
## <a name="using-the-built-in-task-based-combinators"></a><span data-ttu-id="4cac9-163">Utilisation des combinateurs intégrés sur les tâches</span><span class="sxs-lookup"><span data-stu-id="4cac9-163">Using the Built-in Task-based Combinators</span></span>
 <span data-ttu-id="4cac9-164">L’espace de noms <xref:System.Threading.Tasks> inclut plusieurs méthodes de composition et d’utilisation des tâches.</span><span class="sxs-lookup"><span data-stu-id="4cac9-164">The <xref:System.Threading.Tasks> namespace includes several methods for composing and working with tasks.</span></span>

### <a name="taskrun"></a><span data-ttu-id="4cac9-165">Task.Run</span><span class="sxs-lookup"><span data-stu-id="4cac9-165">Task.Run</span></span>
 <span data-ttu-id="4cac9-166">La classe <xref:System.Threading.Tasks.Task> inclut plusieurs méthodes <xref:System.Threading.Tasks.Task.Run%2A> qui vous permettent de décharger facilement du travail en tant que <xref:System.Threading.Tasks.Task> ou <xref:System.Threading.Tasks.Task%601> dans le pool de threads, par exemple :</span><span class="sxs-lookup"><span data-stu-id="4cac9-166">The <xref:System.Threading.Tasks.Task> class includes several <xref:System.Threading.Tasks.Task.Run%2A> methods that let you easily offload work as a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601> to the thread pool, for example:</span></span>

```csharp
public async void button1_Click(object sender, EventArgs e)
{
    textBox1.Text = await Task.Run(() =>
    {
        // … do compute-bound work here
        return answer;
    });
}
```

 <span data-ttu-id="4cac9-167">Certaines de ces méthodes <xref:System.Threading.Tasks.Task.Run%2A>, telles que la surcharge <xref:System.Threading.Tasks.Task.Run%28System.Func%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType>, existent en tant que raccourcis pour la méthode <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4cac9-167">Some of these <xref:System.Threading.Tasks.Task.Run%2A> methods, such as the <xref:System.Threading.Tasks.Task.Run%28System.Func%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType> overload, exist as shorthand for the <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> method.</span></span>  <span data-ttu-id="4cac9-168">D’autres surcharges, telles que <xref:System.Threading.Tasks.Task.Run%28System.Func%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType>, vous permettent d’utiliser await dans le travail déchargé, par exemple :</span><span class="sxs-lookup"><span data-stu-id="4cac9-168">Other overloads, such as <xref:System.Threading.Tasks.Task.Run%28System.Func%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType>, enable you to use await within the offloaded work, for example:</span></span>

```csharp
public async void button1_Click(object sender, EventArgs e)
{
    pictureBox1.Image = await Task.Run(async() =>
    {
        using(Bitmap bmp1 = await DownloadFirstImageAsync())
        using(Bitmap bmp2 = await DownloadSecondImageAsync())
        return Mashup(bmp1, bmp2);
    });
}
```

 <span data-ttu-id="4cac9-169">D’un point de vue logique, ces surcharges reviennent à utiliser la méthode <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> conjointement avec la méthode d’extension <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> dans la bibliothèque parallèle de tâches.</span><span class="sxs-lookup"><span data-stu-id="4cac9-169">Such overloads are logically equivalent to using the <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> method in conjunction with the <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> extension method in the Task Parallel Library.</span></span>

### <a name="taskfromresult"></a><span data-ttu-id="4cac9-170">Task.FromResult</span><span class="sxs-lookup"><span data-stu-id="4cac9-170">Task.FromResult</span></span>
 <span data-ttu-id="4cac9-171">Utilisez la méthode <xref:System.Threading.Tasks.Task.FromResult%2A> dans les scénarios où les données peuvent être déjà disponibles et doivent simplement être retournées par une méthode retournant des tâches élevée dans une <xref:System.Threading.Tasks.Task%601> :</span><span class="sxs-lookup"><span data-stu-id="4cac9-171">Use the <xref:System.Threading.Tasks.Task.FromResult%2A> method in scenarios where data may already be available and just needs to be returned from a task-returning method lifted into a <xref:System.Threading.Tasks.Task%601>:</span></span>

```csharp
public Task<int> GetValueAsync(string key)
{
    int cachedValue;
    return TryGetCachedValue(out cachedValue) ?
        Task.FromResult(cachedValue) :
        GetValueAsyncInternal();
}

private async Task<int> GetValueAsyncInternal(string key)
{
    …
}
```

### <a name="taskwhenall"></a><span data-ttu-id="4cac9-172">Task.WhenAll</span><span class="sxs-lookup"><span data-stu-id="4cac9-172">Task.WhenAll</span></span>
 <span data-ttu-id="4cac9-173">Utilisez la méthode <xref:System.Threading.Tasks.Task.WhenAll%2A> pour attendre de façon asynchrone plusieurs opérations asynchrones représentées en tant que tâches.</span><span class="sxs-lookup"><span data-stu-id="4cac9-173">Use the <xref:System.Threading.Tasks.Task.WhenAll%2A> method to asynchronously wait on multiple asynchronous operations that are represented as tasks.</span></span>  <span data-ttu-id="4cac9-174">La méthode a plusieurs surcharges qui prennent en charge un ensemble de tâches non génériques ou un ensemble non uniforme de tâches génériques (par exemple, l’attente asynchrone de plusieurs opérations qui retournent void, ou l’attente asynchrone de plusieurs méthodes retournant des valeurs où chaque valeur peut avoir un type différent) ou prennent en charge un ensemble uniforme de tâches génériques (comme l’attente asynchrone de plusieurs méthodes retournant `TResult`).</span><span class="sxs-lookup"><span data-stu-id="4cac9-174">The method has multiple overloads that support a set of non-generic tasks or a non-uniform set of generic tasks (for example, asynchronously waiting for multiple void-returning operations, or asynchronously waiting for multiple value-returning methods where each value may have a different type) and to support a uniform set of generic tasks (such as asynchronously waiting for multiple `TResult`-returning methods).</span></span>

 <span data-ttu-id="4cac9-175">Supposons que vous souhaitez envoyer des messages électroniques à plusieurs clients.</span><span class="sxs-lookup"><span data-stu-id="4cac9-175">Let's say you want to send email messages to several customers.</span></span> <span data-ttu-id="4cac9-176">Vous pouvez superposer l’envoi des messages afin de ne pas attendre la fin de l’envoi d’un message avant d’envoyer le suivant.</span><span class="sxs-lookup"><span data-stu-id="4cac9-176">You can overlap sending the messages so you're not waiting for one message to complete before sending the next.</span></span> <span data-ttu-id="4cac9-177">Vous saurez également quand les opérations d’envoi se sont terminées et si des erreurs se sont produites :</span><span class="sxs-lookup"><span data-stu-id="4cac9-177">You can also find out when the send operations have completed and whether any errors have occurred:</span></span>

```csharp
IEnumerable<Task> asyncOps = from addr in addrs select SendMailAsync(addr);
await Task.WhenAll(asyncOps);
```

 <span data-ttu-id="4cac9-178">Ce code ne gère pas explicitement les exceptions qui peuvent se produire, mais laisse les exceptions propager le `await` sur la tâche obtenue à partir de <xref:System.Threading.Tasks.Task.WhenAll%2A>.</span><span class="sxs-lookup"><span data-stu-id="4cac9-178">This code doesn't explicitly handle exceptions that may occur, but lets exceptions propagate out of the `await` on the resulting task from <xref:System.Threading.Tasks.Task.WhenAll%2A>.</span></span>  <span data-ttu-id="4cac9-179">Pour gérer les exceptions, vous pouvez utiliser le code suivant :</span><span class="sxs-lookup"><span data-stu-id="4cac9-179">To handle the exceptions, you can use code such as the following:</span></span>

```csharp
IEnumerable<Task> asyncOps = from addr in addrs select SendMailAsync(addr);
try
{
    await Task.WhenAll(asyncOps);
}
catch(Exception exc)
{
    ...
}
```

 <span data-ttu-id="4cac9-180">Dans ce cas, si une opération asynchrone échoue, toutes les exceptions sont consolidées dans une exception <xref:System.AggregateException>, qui est stockée dans la <xref:System.Threading.Tasks.Task> retournée par la méthode <xref:System.Threading.Tasks.Task.WhenAll%2A>.</span><span class="sxs-lookup"><span data-stu-id="4cac9-180">In this case, if any asynchronous operation fails, all the exceptions will be consolidated in an <xref:System.AggregateException> exception, which is stored in the <xref:System.Threading.Tasks.Task> that is returned from the <xref:System.Threading.Tasks.Task.WhenAll%2A> method.</span></span>  <span data-ttu-id="4cac9-181">Toutefois, une seul de ces exceptions est propagée par le mot-clé `await`.</span><span class="sxs-lookup"><span data-stu-id="4cac9-181">However, only one of those exceptions is propagated by the `await` keyword.</span></span>  <span data-ttu-id="4cac9-182">Si vous souhaitez examiner toutes les exceptions, vous pouvez réécrire le code précédent comme suit :</span><span class="sxs-lookup"><span data-stu-id="4cac9-182">If you want to examine all the exceptions, you can rewrite the previous code as follows:</span></span>

```csharp
Task [] asyncOps = (from addr in addrs select SendMailAsync(addr)).ToArray();
try
{
    await Task.WhenAll(asyncOps);
}
catch(Exception exc)
{
    foreach(Task faulted in asyncOps.Where(t => t.IsFaulted))
    {
        … // work with faulted and faulted.Exception
    }
}
```

 <span data-ttu-id="4cac9-183">Prenons un exemple de téléchargement de plusieurs fichiers à partir du web de manière asynchrone.</span><span class="sxs-lookup"><span data-stu-id="4cac9-183">Let's consider an example of downloading multiple files from the web asynchronously.</span></span>  <span data-ttu-id="4cac9-184">Dans ce cas, toutes les opérations asynchrones ont des types de résultats homogènes, et il est facile d’accéder aux résultats :</span><span class="sxs-lookup"><span data-stu-id="4cac9-184">In this case, all the asynchronous operations have homogeneous result types, and it's easy to access the results:</span></span>

```csharp
string [] pages = await Task.WhenAll(
    from url in urls select DownloadStringAsync(url));
```

 <span data-ttu-id="4cac9-185">Vous pouvez utiliser les mêmes techniques de gestion des exceptions que celles évoquées dans le scénario précédent qui retournait void :</span><span class="sxs-lookup"><span data-stu-id="4cac9-185">You can use the same exception-handling techniques we discussed in the previous void-returning scenario:</span></span>

```csharp
Task<string> [] asyncOps =
    (from url in urls select DownloadStringAsync(url)).ToArray();
try
{
    string [] pages = await Task.WhenAll(asyncOps);
    ...
}
catch(Exception exc)
{
    foreach(Task<string> faulted in asyncOps.Where(t => t.IsFaulted))
    {
        … // work with faulted and faulted.Exception
    }
}
```

### <a name="taskwhenany"></a><span data-ttu-id="4cac9-186">Task.WhenAny</span><span class="sxs-lookup"><span data-stu-id="4cac9-186">Task.WhenAny</span></span>
 <span data-ttu-id="4cac9-187">Vous pouvez utiliser la méthode <xref:System.Threading.Tasks.Task.WhenAny%2A> pour attendre de façon asynchrone qu’une seule des multiples opérations asynchrones représentées en tant que tâches soit effectuée.</span><span class="sxs-lookup"><span data-stu-id="4cac9-187">You can use the <xref:System.Threading.Tasks.Task.WhenAny%2A> method to asynchronously wait for just one of multiple asynchronous operations represented as tasks to complete.</span></span>  <span data-ttu-id="4cac9-188">Cette méthode couvre quatre principaux cas d’utilisation :</span><span class="sxs-lookup"><span data-stu-id="4cac9-188">This method serves four primary use cases:</span></span>

- <span data-ttu-id="4cac9-189">Redondance : Exécution d’une opération plusieurs fois et sélection de celle qui se termine en premier (par exemple, en contactant plusieurs services web de cotation boursière qui produiront un résultat unique et en sélectionnant celui qui se terminera le plus rapidement).</span><span class="sxs-lookup"><span data-stu-id="4cac9-189">Redundancy:  Performing an operation multiple times and selecting the one that completes first (for example, contacting multiple stock quote web services that will produce a single result and selecting the one that completes the fastest).</span></span>

- <span data-ttu-id="4cac9-190">Entrelacement : Lancement de plusieurs opérations, en attendant que toutes se terminent, mais en traitant chacune lors de leur achèvement.</span><span class="sxs-lookup"><span data-stu-id="4cac9-190">Interleaving:  Launching multiple operations and waiting for all of them to complete, but processing them as they complete.</span></span>

- <span data-ttu-id="4cac9-191">Limitation : Autorisation du lancement de nouvelles opérations lorsque d’autres se terminent.</span><span class="sxs-lookup"><span data-stu-id="4cac9-191">Throttling:  Allowing additional operations to begin as others complete.</span></span>  <span data-ttu-id="4cac9-192">Il s’agit d’une extension de l’entrelacement.</span><span class="sxs-lookup"><span data-stu-id="4cac9-192">This is an extension of the interleaving scenario.</span></span>

- <span data-ttu-id="4cac9-193">Interruption anticipée : par exemple, une opération représentée par la tâche t1 peut être regroupée dans une tâche <xref:System.Threading.Tasks.Task.WhenAny%2A> avec une autre tâche t2, et vous pouvez attendre la tâche <xref:System.Threading.Tasks.Task.WhenAny%2A>.</span><span class="sxs-lookup"><span data-stu-id="4cac9-193">Early bailout:  For example, an operation represented by task t1 can be grouped in a <xref:System.Threading.Tasks.Task.WhenAny%2A> task with another task t2, and you can wait on the <xref:System.Threading.Tasks.Task.WhenAny%2A> task.</span></span> <span data-ttu-id="4cac9-194">La tâche t2 peut représenter un délai d’attente, une annulation ou un autre signal qui provoque l’achèvement de la tâche <xref:System.Threading.Tasks.Task.WhenAny%2A> avant la fin de t1.</span><span class="sxs-lookup"><span data-stu-id="4cac9-194">Task t2 could represent a time-out, or cancellation, or some other signal that causes the <xref:System.Threading.Tasks.Task.WhenAny%2A> task to complete before t1 completes.</span></span>

#### <a name="redundancy"></a><span data-ttu-id="4cac9-195">Redondance</span><span class="sxs-lookup"><span data-stu-id="4cac9-195">Redundancy</span></span>
 <span data-ttu-id="4cac9-196">Prenons un cas où vous souhaitez prendre une décision sur la nécessité d’acheter une action.</span><span class="sxs-lookup"><span data-stu-id="4cac9-196">Consider a case where you want to make a decision about whether to buy a stock.</span></span>  <span data-ttu-id="4cac9-197">Il existe plusieurs services de recommandation de cotation boursière auxquels vous faites confiance, mais selon la charge quotidienne, chaque service peut avoir des lenteurs à des moments différents.</span><span class="sxs-lookup"><span data-stu-id="4cac9-197">There are several stock recommendation web services that you trust, but depending on daily load, each service can end up being slow at different times.</span></span>  <span data-ttu-id="4cac9-198">Vous pouvez utiliser la méthode <xref:System.Threading.Tasks.Task.WhenAny%2A> pour recevoir une notification quand une opération est terminée :</span><span class="sxs-lookup"><span data-stu-id="4cac9-198">You can use the <xref:System.Threading.Tasks.Task.WhenAny%2A> method to receive a notification when any operation completes:</span></span>

```csharp
var recommendations = new List<Task<bool>>()
{
    GetBuyRecommendation1Async(symbol),
    GetBuyRecommendation2Async(symbol),
    GetBuyRecommendation3Async(symbol)
};
Task<bool> recommendation = await Task.WhenAny(recommendations);
if (await recommendation) BuyStock(symbol);
```

 <span data-ttu-id="4cac9-199">Contrairement à <xref:System.Threading.Tasks.Task.WhenAll%2A>, qui retourne les résultats non encapsulés de toutes les tâches qui se sont terminées avec succès, <xref:System.Threading.Tasks.Task.WhenAny%2A> retourne la tâche qui s’est terminée.</span><span class="sxs-lookup"><span data-stu-id="4cac9-199">Unlike <xref:System.Threading.Tasks.Task.WhenAll%2A>, which returns the unwrapped results of all tasks that completed successfully, <xref:System.Threading.Tasks.Task.WhenAny%2A> returns the task that completed.</span></span> <span data-ttu-id="4cac9-200">Si une tâche échoue, il est important de savoir qu’elle a échoué et, si une tâche réussit, il est important de connaître la tâche à laquelle la valeur de retour est associée.</span><span class="sxs-lookup"><span data-stu-id="4cac9-200">If a task fails, it's important to know that it failed, and if a task succeeds, it's important to know which task the return value is associated with.</span></span>  <span data-ttu-id="4cac9-201">Par conséquent, vous devez accéder au résultat de la tâche retournée ou l’attendre davantage, comme le montre cet exemple.</span><span class="sxs-lookup"><span data-stu-id="4cac9-201">Therefore, you need to access the result of the returned task, or further await it, as  this example shows.</span></span>

 <span data-ttu-id="4cac9-202">Tout comme avec <xref:System.Threading.Tasks.Task.WhenAll%2A>, vous devez être en mesure de prendre en compte les exceptions.</span><span class="sxs-lookup"><span data-stu-id="4cac9-202">As with <xref:System.Threading.Tasks.Task.WhenAll%2A>, you have to be able to accommodate exceptions.</span></span>  <span data-ttu-id="4cac9-203">Étant donné que vous recevez la tâche terminée, vous pouvez attendre la tâche retournée pour propager les erreurs, et utiliser `try/catch` dessus comme nécessaire, par exemple :</span><span class="sxs-lookup"><span data-stu-id="4cac9-203">Because you receive the completed task back, you can await the returned task to have errors propagated, and `try/catch` them appropriately; for example:</span></span>

```csharp
Task<bool> [] recommendations = …;
while(recommendations.Count > 0)
{
    Task<bool> recommendation = await Task.WhenAny(recommendations);
    try
    {
        if (await recommendation) BuyStock(symbol);
        break;
    }
    catch(WebException exc)
    {
        recommendations.Remove(recommendation);
    }
}
```

 <span data-ttu-id="4cac9-204">En outre, même si une première tâche se termine avec succès, les tâches suivantes peuvent échouer.</span><span class="sxs-lookup"><span data-stu-id="4cac9-204">Additionally, even if a first task completes successfully, subsequent tasks may fail.</span></span>  <span data-ttu-id="4cac9-205">À ce stade, vous disposez de plusieurs options pour la gestion des exceptions : vous pouvez attendre que toutes les tâches lancées soient terminées, auquel cas vous pouvez utiliser la méthode <xref:System.Threading.Tasks.Task.WhenAll%2A>, ou vous pouvez décider que toutes les exceptions sont importantes et doivent être journalisées.</span><span class="sxs-lookup"><span data-stu-id="4cac9-205">At this point, you have several options for dealing with exceptions:  You can wait until all the launched tasks have completed, in which case you can use the <xref:System.Threading.Tasks.Task.WhenAll%2A> method, or you can decide that all exceptions are important and must be logged.</span></span>  <span data-ttu-id="4cac9-206">Dans ce cas, vous pouvez utiliser les continuations de recevoir une notification lorsque des tâches se sont terminées de manière asynchrone :</span><span class="sxs-lookup"><span data-stu-id="4cac9-206">For this, you can use continuations to receive a notification when tasks have completed asynchronously:</span></span>

```csharp
foreach(Task recommendation in recommendations)
{
    var ignored = recommendation.ContinueWith(
        t => { if (t.IsFaulted) Log(t.Exception); });
}
```

 <span data-ttu-id="4cac9-207">ou :</span><span class="sxs-lookup"><span data-stu-id="4cac9-207">or:</span></span>

```csharp
foreach(Task recommendation in recommendations)
{
    var ignored = recommendation.ContinueWith(
        t => Log(t.Exception), TaskContinuationOptions.OnlyOnFaulted);
}
```

 <span data-ttu-id="4cac9-208">ou même :</span><span class="sxs-lookup"><span data-stu-id="4cac9-208">or even:</span></span>

```csharp
private static async void LogCompletionIfFailed(IEnumerable<Task> tasks)
{
    foreach(var task in tasks)
    {
        try { await task; }
        catch(Exception exc) { Log(exc); }
    }
}
…
LogCompletionIfFailed(recommendations);
```

 <span data-ttu-id="4cac9-209">Enfin, vous souhaiterez peut-être annuler toutes les opérations restantes :</span><span class="sxs-lookup"><span data-stu-id="4cac9-209">Finally, you may want to cancel all the remaining operations:</span></span>

```csharp
var cts = new CancellationTokenSource();
var recommendations = new List<Task<bool>>()
{
    GetBuyRecommendation1Async(symbol, cts.Token),
    GetBuyRecommendation2Async(symbol, cts.Token),
    GetBuyRecommendation3Async(symbol, cts.Token)
};

Task<bool> recommendation = await Task.WhenAny(recommendations);
cts.Cancel();
if (await recommendation) BuyStock(symbol);
```

#### <a name="interleaving"></a><span data-ttu-id="4cac9-210">Entrelacement</span><span class="sxs-lookup"><span data-stu-id="4cac9-210">Interleaving</span></span>
 <span data-ttu-id="4cac9-211">Prenons un cas où vous téléchargez des images à partir du web et traitez chaque image (par exemple, en ajoutant l’image à un contrôle d’interface utilisateur).</span><span class="sxs-lookup"><span data-stu-id="4cac9-211">Consider a case where you're downloading images from the web and processing each image (for example, adding the image to a UI control).</span></span> <span data-ttu-id="4cac9-212">Vous traitez les images de manière séquentielle sur le thread d’interface utilisateur, mais vous souhaitez télécharger les images aussi simultanément que possible.</span><span class="sxs-lookup"><span data-stu-id="4cac9-212">You process the images sequentially on the UI thread, but want to download the images as concurrently as possible.</span></span> <span data-ttu-id="4cac9-213">En outre, vous ne souhaitez pas ajouter les images à l’interface utilisateur tant qu’elles ne sont pas téléchargées.</span><span class="sxs-lookup"><span data-stu-id="4cac9-213">Also, you don't want to hold up adding the images to the UI until they're all downloaded.</span></span> <span data-ttu-id="4cac9-214">Au lieu de cela, vous devez les ajouter à mesure qu’ils se terminent.</span><span class="sxs-lookup"><span data-stu-id="4cac9-214">Instead, you want to add them as they complete.</span></span>

```csharp
List<Task<Bitmap>> imageTasks =
    (from imageUrl in urls select GetBitmapAsync(imageUrl)).ToList();
while(imageTasks.Count > 0)
{
    try
    {
        Task<Bitmap> imageTask = await Task.WhenAny(imageTasks);
        imageTasks.Remove(imageTask);

        Bitmap image = await imageTask;
        panel.AddImage(image);
    }
    catch{}
}
```

 <span data-ttu-id="4cac9-215">Vous pouvez également appliquer l’entrelacement à un scénario qui implique un traitement intensif par calcul sur le <xref:System.Threading.ThreadPool> des images téléchargées, par exemple :</span><span class="sxs-lookup"><span data-stu-id="4cac9-215">You can also apply interleaving to a scenario that involves computationally intensive processing on the <xref:System.Threading.ThreadPool> of the downloaded images; for example:</span></span>

```csharp
List<Task<Bitmap>> imageTasks =
    (from imageUrl in urls select GetBitmapAsync(imageUrl)
         .ContinueWith(t => ConvertImage(t.Result)).ToList();
while(imageTasks.Count > 0)
{
    try
    {
        Task<Bitmap> imageTask = await Task.WhenAny(imageTasks);
        imageTasks.Remove(imageTask);

        Bitmap image = await imageTask;
        panel.AddImage(image);
    }
    catch{}
}
```

#### <a name="throttling"></a><span data-ttu-id="4cac9-216">Limitation</span><span class="sxs-lookup"><span data-stu-id="4cac9-216">Throttling</span></span>
 <span data-ttu-id="4cac9-217">Prenons l’exemple de l’entrelacement, sauf qu’ici l’utilisateur télécharge tant d’images que les téléchargements doivent être limités. Par exemple, vous ne souhaitez qu’un certain nombre de téléchargements simultanés.</span><span class="sxs-lookup"><span data-stu-id="4cac9-217">Consider the interleaving example, except that the user is downloading so many images that the downloads have to be throttled; for example, you want only a specific number of downloads to happen concurrently.</span></span> <span data-ttu-id="4cac9-218">Pour ce faire, vous pouvez démarrer un sous-ensemble d’opérations asynchrones.</span><span class="sxs-lookup"><span data-stu-id="4cac9-218">To achieve this, you can start a subset of the asynchronous operations.</span></span>  <span data-ttu-id="4cac9-219">Lorsque les opérations sont terminées, vous pouvez démarrer des opérations supplémentaires pour prendre leur place :</span><span class="sxs-lookup"><span data-stu-id="4cac9-219">As operations complete, you can start additional operations to take their place:</span></span>

```csharp
const int CONCURRENCY_LEVEL = 15;
Uri [] urls = …;
int nextIndex = 0;
var imageTasks = new List<Task<Bitmap>>();
while(nextIndex < CONCURRENCY_LEVEL && nextIndex < urls.Length)
{
    imageTasks.Add(GetBitmapAsync(urls[nextIndex]));
    nextIndex++;
}

while(imageTasks.Count > 0)
{
    try
    {
        Task<Bitmap> imageTask = await Task.WhenAny(imageTasks);
        imageTasks.Remove(imageTask);

        Bitmap image = await imageTask;
        panel.AddImage(image);
    }
    catch(Exception exc) { Log(exc); }

    if (nextIndex < urls.Length)
    {
        imageTasks.Add(GetBitmapAsync(urls[nextIndex]));
        nextIndex++;
    }
}
```

#### <a name="early-bailout"></a><span data-ttu-id="4cac9-220">Interruption anticipée</span><span class="sxs-lookup"><span data-stu-id="4cac9-220">Early Bailout</span></span>
 <span data-ttu-id="4cac9-221">Supposons que vous attendez de façon asynchrone qu’une opération se termine tout en répondant simultanément à la demande d’annulation d’un utilisateur (par exemple, l’utilisateur a cliqué sur un bouton Annuler).</span><span class="sxs-lookup"><span data-stu-id="4cac9-221">Consider that you're waiting asynchronously for an operation to complete while simultaneously responding to a user's cancellation request (for example, the user clicked a cancel button).</span></span> <span data-ttu-id="4cac9-222">Le code suivant illustre ce scénario :</span><span class="sxs-lookup"><span data-stu-id="4cac9-222">The following code illustrates this scenario:</span></span>

```csharp
private CancellationTokenSource m_cts;

public void btnCancel_Click(object sender, EventArgs e)
{
    if (m_cts != null) m_cts.Cancel();
}

public async void btnRun_Click(object sender, EventArgs e)
{
    m_cts = new CancellationTokenSource();
    btnRun.Enabled = false;
    try
    {
        Task<Bitmap> imageDownload = GetBitmapAsync(txtUrl.Text);
        await UntilCompletionOrCancellation(imageDownload, m_cts.Token);
        if (imageDownload.IsCompleted)
        {
            Bitmap image = await imageDownload;
            panel.AddImage(image);
        }
        else imageDownload.ContinueWith(t => Log(t));
    }
    finally { btnRun.Enabled = true; }
}

private static async Task UntilCompletionOrCancellation(
    Task asyncOp, CancellationToken ct)
{
    var tcs = new TaskCompletionSource<bool>();
    using(ct.Register(() => tcs.TrySetResult(true)))
        await Task.WhenAny(asyncOp, tcs.Task);
    return asyncOp;
}
```

 <span data-ttu-id="4cac9-223">Cette implémentation réactive l’interface utilisateur dès que vous décidez de quitter la procédure, mais n’annule pas les opérations asynchrones sous-jacentes.</span><span class="sxs-lookup"><span data-stu-id="4cac9-223">This implementation re-enables the user interface as soon as you decide to bail out, but doesn't cancel the underlying asynchronous operations.</span></span> <span data-ttu-id="4cac9-224">Une autre solution consiste à annuler les opérations en attente lorsque vous décidez de les abandonner, mais pas de rétablir l’interface utilisateur jusqu’à ce que les opérations se terminent, éventuellement en raison de la fin précoce de la demande d’annulation :</span><span class="sxs-lookup"><span data-stu-id="4cac9-224">Another alternative would be to cancel the pending operations when you decide to bail out, but not reestablish the user interface until the operations complete, potentially due to ending early due to the cancellation request:</span></span>

```csharp
private CancellationTokenSource m_cts;

public async void btnRun_Click(object sender, EventArgs e)
{
    m_cts = new CancellationTokenSource();

    btnRun.Enabled = false;
    try
    {
        Task<Bitmap> imageDownload = GetBitmapAsync(txtUrl.Text, m_cts.Token);
        await UntilCompletionOrCancellation(imageDownload, m_cts.Token);
        Bitmap image = await imageDownload;
        panel.AddImage(image);
    }
    catch(OperationCanceledException) {}
    finally { btnRun.Enabled = true; }
}
```

 <span data-ttu-id="4cac9-225">Un autre exemple d’interruption anticipée impliquerait l’utilisation de la méthode <xref:System.Threading.Tasks.Task.WhenAny%2A> conjointement avec la méthode <xref:System.Threading.Tasks.Task.Delay%2A>, comme décrit dans la section suivante.</span><span class="sxs-lookup"><span data-stu-id="4cac9-225">Another example of early bailout involves using the <xref:System.Threading.Tasks.Task.WhenAny%2A> method in conjunction with the <xref:System.Threading.Tasks.Task.Delay%2A> method, as discussed in the next section.</span></span>

### <a name="taskdelay"></a><span data-ttu-id="4cac9-226">Task.Delay</span><span class="sxs-lookup"><span data-stu-id="4cac9-226">Task.Delay</span></span>
 <span data-ttu-id="4cac9-227">Vous pouvez utiliser la <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> méthode pour introduire des pauses dans l’exécution d’une méthode asynchrone.</span><span class="sxs-lookup"><span data-stu-id="4cac9-227">You can use the <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> method to introduce pauses into an asynchronous method's execution.</span></span>  <span data-ttu-id="4cac9-228">Cela est utile pour de nombreux types de fonctionnalités, notamment la création de boucles d’interrogation et le retardement du traitement des entrées d’utilisateur pour une période prédéterminée.</span><span class="sxs-lookup"><span data-stu-id="4cac9-228">This is useful for many kinds of functionality, including building polling loops and delaying the handling of user input for a predetermined period of time.</span></span>  <span data-ttu-id="4cac9-229">La méthode <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> peut également être utile si elle est combinée avec <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> pour implémenter des délais d’attente.</span><span class="sxs-lookup"><span data-stu-id="4cac9-229">The <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> method can also be useful in combination with <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> for implementing time-outs on awaits.</span></span>

 <span data-ttu-id="4cac9-230">Si une tâche qui fait partie d’une opération asynchrone plus grande (par exemple, un service Web ASP.NET) prend trop de temps pour s’exécuter, l’opération globale peut en pâtir, en particulier si elle ne se termine pas.</span><span class="sxs-lookup"><span data-stu-id="4cac9-230">If a task that's part of a larger asynchronous operation (for example, an ASP.NET web service) takes too long to complete, the overall operation could suffer, especially if it fails to ever complete.</span></span>  <span data-ttu-id="4cac9-231">Pour cette raison, il est important de pouvoir dépasser le délai d’attente lors de l’attente d’une opération asynchrone.</span><span class="sxs-lookup"><span data-stu-id="4cac9-231">For this reason, it's important to be able to time out when waiting on an asynchronous operation.</span></span>  <span data-ttu-id="4cac9-232">Les méthodes synchrones <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Task.WaitAll%2A?displayProperty=nameWithType> et <xref:System.Threading.Tasks.Task.WaitAny%2A?displayProperty=nameWithType> acceptent des valeurs de délai d’attente, à la différence des méthodes <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A?displayProperty=nameWithType>/<xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> correspondantes et des méthodes <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>/<xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> mentionnées précédemment qui n’en acceptent pas.</span><span class="sxs-lookup"><span data-stu-id="4cac9-232">The synchronous <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Task.WaitAll%2A?displayProperty=nameWithType>, and <xref:System.Threading.Tasks.Task.WaitAny%2A?displayProperty=nameWithType> methods accept time-out values, but the corresponding <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A?displayProperty=nameWithType>/<xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> and the previously mentioned <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>/<xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> methods do not.</span></span>  <span data-ttu-id="4cac9-233">Vous pouvez, à la place, utiliser <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> et <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> conjointement pour implémenter un délai d’attente.</span><span class="sxs-lookup"><span data-stu-id="4cac9-233">Instead, you can use <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> in combination to implement a time-out.</span></span>

 <span data-ttu-id="4cac9-234">Par exemple, dans votre application d’interface utilisateur, supposons que vous souhaitez télécharger une image et désactivez l’interface utilisateur pendant le téléchargement de l’image.</span><span class="sxs-lookup"><span data-stu-id="4cac9-234">For example, in your UI application, let's say that you want to download an image and disable the UI while the image is downloading.</span></span> <span data-ttu-id="4cac9-235">Toutefois, si le téléchargement est trop long, vous souhaitez réactiver l’interface utilisateur et ignorer le téléchargement :</span><span class="sxs-lookup"><span data-stu-id="4cac9-235">However, if the download takes too long, you want to re-enable the UI and discard the download:</span></span>

```csharp
public async void btnDownload_Click(object sender, EventArgs e)
{
    btnDownload.Enabled = false;
    try
    {
        Task<Bitmap> download = GetBitmapAsync(url);
        if (download == await Task.WhenAny(download, Task.Delay(3000)))
        {
            Bitmap bmp = await download;
            pictureBox.Image = bmp;
            status.Text = "Downloaded";
        }
        else
        {
            pictureBox.Image = null;
            status.Text = "Timed out";
            var ignored = download.ContinueWith(
                t => Trace("Task finally completed"));
        }
    }
    finally { btnDownload.Enabled = true; }
}
```

 <span data-ttu-id="4cac9-236">La même règle s’applique à plusieurs téléchargements, car <xref:System.Threading.Tasks.Task.WhenAll%2A> retourne une tâche :</span><span class="sxs-lookup"><span data-stu-id="4cac9-236">The same applies to multiple downloads, because <xref:System.Threading.Tasks.Task.WhenAll%2A> returns a task:</span></span>

```csharp
public async void btnDownload_Click(object sender, RoutedEventArgs e)
{
    btnDownload.Enabled = false;
    try
    {
        Task<Bitmap[]> downloads =
            Task.WhenAll(from url in urls select GetBitmapAsync(url));
        if (downloads == await Task.WhenAny(downloads, Task.Delay(3000)))
        {
            foreach(var bmp in downloads.Result) panel.AddImage(bmp);
            status.Text = "Downloaded";
        }
        else
        {
            status.Text = "Timed out";
            downloads.ContinueWith(t => Log(t));
        }
    }
    finally { btnDownload.Enabled = true; }
}
```

## <a name="building-task-based-combinators"></a><span data-ttu-id="4cac9-237">Création de combinateurs basés sur les tâches</span><span class="sxs-lookup"><span data-stu-id="4cac9-237">Building Task-based Combinators</span></span>
 <span data-ttu-id="4cac9-238">Une tâche étant en mesure de représenter une opération asynchrone et de fournir des fonctions synchrones et asynchrones pour effectuer la liaison avec l’opération, récupérer ses résultats et ainsi de suite, vous pouvez créer des bibliothèques utiles de combinateurs qui composent les tâches pour créer des modèles plus grands.</span><span class="sxs-lookup"><span data-stu-id="4cac9-238">Because a task is able to completely represent an asynchronous operation and provide synchronous and asynchronous capabilities for joining with the operation, retrieving its results, and so on, you can build useful libraries of combinators that compose tasks to build larger patterns.</span></span> <span data-ttu-id="4cac9-239">Comme indiqué dans la section précédente, .NET comprend plusieurs combinateurs intégrés, mais vous pouvez également créer votre propre combinateur.</span><span class="sxs-lookup"><span data-stu-id="4cac9-239">As discussed in the previous section, .NET includes several built-in combinators, but you can also build your own.</span></span> <span data-ttu-id="4cac9-240">Les sections suivantes fournissent plusieurs exemples de types et méthodes de combinateurs potentiels.</span><span class="sxs-lookup"><span data-stu-id="4cac9-240">The following sections provide several examples of potential combinator methods and types.</span></span>

### <a name="retryonfault"></a><span data-ttu-id="4cac9-241">RetryOnFault</span><span class="sxs-lookup"><span data-stu-id="4cac9-241">RetryOnFault</span></span>
 <span data-ttu-id="4cac9-242">Dans de nombreuses situations, vous souhaiterez peut-être retenter une opération si une tentative précédente échoue.</span><span class="sxs-lookup"><span data-stu-id="4cac9-242">In many situations, you may want to retry an operation if a previous attempt fails.</span></span>  <span data-ttu-id="4cac9-243">Pour le code synchrone, vous pouvez créer une méthode d’assistance telle que `RetryOnFault` dans l’exemple suivant pour y parvenir :</span><span class="sxs-lookup"><span data-stu-id="4cac9-243">For synchronous code, you might build a helper method such as `RetryOnFault` in the following example to accomplish this:</span></span>

```csharp
public static T RetryOnFault<T>(
    Func<T> function, int maxTries)
{
    for(int i=0; i<maxTries; i++)
    {
        try { return function(); }
        catch { if (i == maxTries-1) throw; }
    }
    return default(T);
}
```

 <span data-ttu-id="4cac9-244">Vous pouvez créer une méthode d’assistance presque identique pour les opérations asynchrones qui sont implémentées avec TAP et donc renvoyer des tâches :</span><span class="sxs-lookup"><span data-stu-id="4cac9-244">You can build an almost identical helper method for asynchronous operations that are implemented with TAP and thus return tasks:</span></span>

```csharp
public static async Task<T> RetryOnFault<T>(
    Func<Task<T>> function, int maxTries)
{
    for(int i=0; i<maxTries; i++)
    {
        try { return await function().ConfigureAwait(false); }
        catch { if (i == maxTries-1) throw; }
    }
    return default(T);
}
```

 <span data-ttu-id="4cac9-245">Vous pouvez ensuite utiliser ce combinateur pour encoder les nouvelles tentatives dans la logique de l’application ; par exemple :</span><span class="sxs-lookup"><span data-stu-id="4cac9-245">You can then use this combinator to encode retries into the application's logic; for example:</span></span>

```csharp
// Download the URL, trying up to three times in case of failure
string pageContents = await RetryOnFault(
    () => DownloadStringAsync(url), 3);
```

 <span data-ttu-id="4cac9-246">Vous pouvez étendre la fonction `RetryOnFault`.</span><span class="sxs-lookup"><span data-stu-id="4cac9-246">You could extend the `RetryOnFault` function further.</span></span> <span data-ttu-id="4cac9-247">Par exemple, la fonction peut accepter une autre `Func<Task>` qui sera appelée entre chaque tentative pour déterminer quand recommencer l’opération, par exemple :</span><span class="sxs-lookup"><span data-stu-id="4cac9-247">For example, the function could accept another `Func<Task>` that will be invoked between retries to determine when to try the operation again; for example:</span></span>

```csharp
public static async Task<T> RetryOnFault<T>(
    Func<Task<T>> function, int maxTries, Func<Task> retryWhen)
{
    for(int i=0; i<maxTries; i++)
    {
        try { return await function().ConfigureAwait(false); }
        catch { if (i == maxTries-1) throw; }
        await retryWhen().ConfigureAwait(false);
    }
    return default(T);
}
```

 <span data-ttu-id="4cac9-248">Vous pouvez ensuite utiliser la fonction comme suit pour attendre une seconde avant de recommencer l’opération :</span><span class="sxs-lookup"><span data-stu-id="4cac9-248">You could then use the function as follows to wait for a second before retrying the operation:</span></span>

```csharp
// Download the URL, trying up to three times in case of failure,
// and delaying for a second between retries
string pageContents = await RetryOnFault(
    () => DownloadStringAsync(url), 3, () => Task.Delay(1000));
```

### <a name="needonlyone"></a><span data-ttu-id="4cac9-249">NeedOnlyOne</span><span class="sxs-lookup"><span data-stu-id="4cac9-249">NeedOnlyOne</span></span>
 <span data-ttu-id="4cac9-250">Parfois, vous pouvez tirer parti de la redondance pour améliorer la latence et les chances de réussite d’une opération.</span><span class="sxs-lookup"><span data-stu-id="4cac9-250">Sometimes, you can take advantage of redundancy to improve an operation's latency and chances for success.</span></span>  <span data-ttu-id="4cac9-251">Supposons que nous avons plusieurs services web qui fournissent des cotations boursières, mais qu’à différents moments de la journée, chaque service peut fournir différents niveaux de qualité et de réactivité.</span><span class="sxs-lookup"><span data-stu-id="4cac9-251">Consider multiple web services that provide stock quotes, but at various times of the day, each service may provide different levels of quality and response times.</span></span>  <span data-ttu-id="4cac9-252">Pour faire face à ces variations, vous pouvez émettre des demandes pour tous les services web et, dès que vous obtenez une réponse à partir d’un d’entre eux, annuler les demandes restantes.</span><span class="sxs-lookup"><span data-stu-id="4cac9-252">To deal with these fluctuations, you may issue requests to all the web services, and as soon as you get a response from one, cancel the remaining requests.</span></span>  <span data-ttu-id="4cac9-253">Vous pouvez implémenter une fonction d’assistance pour faciliter l’implémentation de ce modèle commun de lancement de plusieurs opérations, d’attente qu’une d’entre elles se termine et d’annulation du reste.</span><span class="sxs-lookup"><span data-stu-id="4cac9-253">You can implement a helper function to make it easier to implement this common pattern of launching multiple operations, waiting for any, and then canceling the rest.</span></span> <span data-ttu-id="4cac9-254">La fonction `NeedOnlyOne` dans l’exemple suivant illustre ce scénario :</span><span class="sxs-lookup"><span data-stu-id="4cac9-254">The `NeedOnlyOne` function in the following example illustrates this scenario:</span></span>

```csharp
public static async Task<T> NeedOnlyOne(
    params Func<CancellationToken,Task<T>> [] functions)
{
    var cts = new CancellationTokenSource();
    var tasks = (from function in functions
                 select function(cts.Token)).ToArray();
    var completed = await Task.WhenAny(tasks).ConfigureAwait(false);
    cts.Cancel();
    foreach(var task in tasks)
    {
        var ignored = task.ContinueWith(
            t => Log(t), TaskContinuationOptions.OnlyOnFaulted);
    }
    return completed;
}
```

 <span data-ttu-id="4cac9-255">Vous pouvez ensuite utiliser cette fonction comme suit :</span><span class="sxs-lookup"><span data-stu-id="4cac9-255">You can then use this function as follows:</span></span>

```csharp
double currentPrice = await NeedOnlyOne(
    ct => GetCurrentPriceFromServer1Async("msft", ct),
    ct => GetCurrentPriceFromServer2Async("msft", ct),
    ct => GetCurrentPriceFromServer3Async("msft", ct));
```

### <a name="interleaved-operations"></a><span data-ttu-id="4cac9-256">Opérations entrelacées</span><span class="sxs-lookup"><span data-stu-id="4cac9-256">Interleaved Operations</span></span>
 <span data-ttu-id="4cac9-257">Il existe un problème de performances potentiel lié à l’utilisation <xref:System.Threading.Tasks.Task.WhenAny%2A> de la méthode pour prendre en charge un scénario d’entrelacement lorsque vous travaillez avec de grands ensembles de tâches.</span><span class="sxs-lookup"><span data-stu-id="4cac9-257">There is a potential performance problem with using the <xref:System.Threading.Tasks.Task.WhenAny%2A> method to support an interleaving scenario when you're working with large sets of tasks.</span></span> <span data-ttu-id="4cac9-258">Chaque appel à <xref:System.Threading.Tasks.Task.WhenAny%2A> entraîne une continuation enregistrée avec chaque tâche.</span><span class="sxs-lookup"><span data-stu-id="4cac9-258">Every call to <xref:System.Threading.Tasks.Task.WhenAny%2A> results in a continuation being registered with each task.</span></span> <span data-ttu-id="4cac9-259">Pour N nombre de tâches, cela entraîne la création de continuations O (N<sup>2</sup>) au cours de la durée de vie de l’opération d’entrelacement.</span><span class="sxs-lookup"><span data-stu-id="4cac9-259">For N number of tasks, this results in O(N<sup>2</sup>) continuations created over the lifetime of the interleaving operation.</span></span> <span data-ttu-id="4cac9-260">Si vous utilisez un grand nombre de tâches, vous pouvez utiliser un combinateur ( `Interleaved` dans l’exemple suivant) pour résoudre le problème de performances :</span><span class="sxs-lookup"><span data-stu-id="4cac9-260">If you're working with a large set of tasks, you can use a combinator (`Interleaved` in the following example) to address the performance issue:</span></span>

```csharp
static IEnumerable<Task<T>> Interleaved<T>(IEnumerable<Task<T>> tasks)
{
    var inputTasks = tasks.ToList();
    var sources = (from _ in Enumerable.Range(0, inputTasks.Count)
                   select new TaskCompletionSource<T>()).ToList();
    int nextTaskIndex = -1;
    foreach (var inputTask in inputTasks)
    {
        inputTask.ContinueWith(completed =>
        {
            var source = sources[Interlocked.Increment(ref nextTaskIndex)];
            if (completed.IsFaulted)
                source.TrySetException(completed.Exception.InnerExceptions);
            else if (completed.IsCanceled)
                source.TrySetCanceled();
            else
                source.TrySetResult(completed.Result);
        }, CancellationToken.None,
           TaskContinuationOptions.ExecuteSynchronously,
           TaskScheduler.Default);
    }
    return from source in sources
           select source.Task;
}
```

 <span data-ttu-id="4cac9-261">Vous pouvez ensuite utiliser le combinateur pour traiter les résultats des tâches terminées ; par exemple :</span><span class="sxs-lookup"><span data-stu-id="4cac9-261">You can then use the combinator to process the results of tasks as they complete; for example:</span></span>

```csharp
IEnumerable<Task<int>> tasks = ...;
foreach(var task in Interleaved(tasks))
{
    int result = await task;
    …
}
```

### <a name="whenallorfirstexception"></a><span data-ttu-id="4cac9-262">WhenAllOrFirstException</span><span class="sxs-lookup"><span data-stu-id="4cac9-262">WhenAllOrFirstException</span></span>
 <span data-ttu-id="4cac9-263">Dans certains scénarios de dispersion/regroupement, vous souhaiterez attendre toutes les tâches dans un jeu, à moins qu’une d’elles rencontre une erreur, auquel cas vous souhaiterez cesser d’attendre dès que l’exception se produit.</span><span class="sxs-lookup"><span data-stu-id="4cac9-263">In certain scatter/gather scenarios, you might want to wait for all tasks in a set, unless one of them faults, in which case you want to stop waiting as soon as the exception occurs.</span></span>  <span data-ttu-id="4cac9-264">Vous pouvez accomplir cela avec une méthode de combinateur comme `WhenAllOrFirstException` dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="4cac9-264">You can accomplish that with a combinator method such as `WhenAllOrFirstException` in the following example:</span></span>

```csharp
public static Task<T[]> WhenAllOrFirstException<T>(IEnumerable<Task<T>> tasks)
{
    var inputs = tasks.ToList();
    var ce = new CountdownEvent(inputs.Count);
    var tcs = new TaskCompletionSource<T[]>();

    Action<Task> onCompleted = (Task completed) =>
    {
        if (completed.IsFaulted)
            tcs.TrySetException(completed.Exception.InnerExceptions);
        if (ce.Signal() && !tcs.Task.IsCompleted)
            tcs.TrySetResult(inputs.Select(t => t.Result).ToArray());
    };

    foreach (var t in inputs) t.ContinueWith(onCompleted);
    return tcs.Task;
}
```

## <a name="building-task-based-data-structures"></a><span data-ttu-id="4cac9-265">Création de structures de données basées sur les tâches</span><span class="sxs-lookup"><span data-stu-id="4cac9-265">Building Task-based Data Structures</span></span>
 <span data-ttu-id="4cac9-266">Outre la possibilité de générer des combinateurs basés sur des tâches personnalisés, le fait de disposer d’une structure de données dans <xref:System.Threading.Tasks.Task> et <xref:System.Threading.Tasks.Task%601> qui représente à la fois les résultats d’une opération asynchrone et la synchronisation nécessaire pour la joindre en fait un type puissant sur lequel créer des structures de données personnalisées à utiliser dans des scénarios asynchrones.</span><span class="sxs-lookup"><span data-stu-id="4cac9-266">In addition to the ability to build custom task-based combinators, having a data structure in <xref:System.Threading.Tasks.Task> and <xref:System.Threading.Tasks.Task%601> that represents both the results of an asynchronous operation and the necessary synchronization to join with it makes it a powerful type on which to build custom data structures to be used in asynchronous scenarios.</span></span>

### <a name="asynccache"></a><span data-ttu-id="4cac9-267">AsyncCache</span><span class="sxs-lookup"><span data-stu-id="4cac9-267">AsyncCache</span></span>
 <span data-ttu-id="4cac9-268">Un aspect important d’une tâche est qu’elle peut être remise à plusieurs consommateurs, qui peuvent tous utiliser await dessus, enregistrer des continuations de registre dessus, obtenir ses résultats ou exceptions (dans le cas de <xref:System.Threading.Tasks.Task%601>), et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="4cac9-268">One important aspect of a task is that it may be handed out to multiple consumers, all of whom may await it, register continuations with it, get its result or exceptions (in the case of <xref:System.Threading.Tasks.Task%601>), and so on.</span></span>  <span data-ttu-id="4cac9-269">Cela permet d’utiliser parfaitement <xref:System.Threading.Tasks.Task> et <xref:System.Threading.Tasks.Task%601> dans une infrastructure de mise en cache asynchrone.</span><span class="sxs-lookup"><span data-stu-id="4cac9-269">This makes <xref:System.Threading.Tasks.Task> and <xref:System.Threading.Tasks.Task%601> perfectly suited to be used in an asynchronous caching infrastructure.</span></span>  <span data-ttu-id="4cac9-270">Voici un exemple de cache asynchrone petit mais puissant basé sur <xref:System.Threading.Tasks.Task%601> :</span><span class="sxs-lookup"><span data-stu-id="4cac9-270">Here's an example of a small but powerful asynchronous cache built on top of <xref:System.Threading.Tasks.Task%601>:</span></span>

```csharp
public class AsyncCache<TKey, TValue>
{
    private readonly Func<TKey, Task<TValue>> _valueFactory;
    private readonly ConcurrentDictionary<TKey, Lazy<Task<TValue>>> _map;

    public AsyncCache(Func<TKey, Task<TValue>> valueFactory)
    {
        if (valueFactory == null) throw new ArgumentNullException("loader");
        _valueFactory = valueFactory;
        _map = new ConcurrentDictionary<TKey, Lazy<Task<TValue>>>();
    }

    public Task<TValue> this[TKey key]
    {
        get
        {
            if (key == null) throw new ArgumentNullException("key");
            return _map.GetOrAdd(key, toAdd =>
                new Lazy<Task<TValue>>(() => _valueFactory(toAdd))).Value;
        }
    }
}
```

 <span data-ttu-id="4cac9-271">La [classe \<TKey,TValue> classe asynccache](https://devblogs.microsoft.com/pfxteam/parallelextensionsextras-tour-12-asynccache/) accepte comme délégué à son constructeur une fonction qui prend un `TKey` et retourne un <xref:System.Threading.Tasks.Task%601> .</span><span class="sxs-lookup"><span data-stu-id="4cac9-271">The [AsyncCache\<TKey,TValue>](https://devblogs.microsoft.com/pfxteam/parallelextensionsextras-tour-12-asynccache/) class accepts as a delegate to its constructor a function that takes a `TKey` and returns a <xref:System.Threading.Tasks.Task%601>.</span></span>  <span data-ttu-id="4cac9-272">Toutes les valeurs précédemment accessibles à partir du cache sont stockées dans le dictionnaire interne, et `AsyncCache` garantit qu’une seule tâche est générée par clé, même en cas d’accès simultané au cache.</span><span class="sxs-lookup"><span data-stu-id="4cac9-272">Any previously accessed values from the cache are stored in the internal dictionary, and the `AsyncCache` ensures that only one task is generated per key, even if the cache is accessed concurrently.</span></span>

 <span data-ttu-id="4cac9-273">Par exemple, vous pouvez créer un cache de pages web téléchargées :</span><span class="sxs-lookup"><span data-stu-id="4cac9-273">For example, you can build a cache for downloaded web pages:</span></span>

```csharp
private AsyncCache<string,string> m_webPages =
    new AsyncCache<string,string>(DownloadStringAsync);
```

 <span data-ttu-id="4cac9-274">Vous pouvez ensuite utiliser ce cache dans les méthodes asynchrones chaque fois que vous avez besoin du contenu d’une page web.</span><span class="sxs-lookup"><span data-stu-id="4cac9-274">You can then use this cache in asynchronous methods whenever you need the contents of a web page.</span></span> <span data-ttu-id="4cac9-275">La `AsyncCache` classe garantit que vous téléchargez le moins de pages possible et met en cache les résultats.</span><span class="sxs-lookup"><span data-stu-id="4cac9-275">The `AsyncCache` class ensures that you're downloading as few pages as possible, and caches the results.</span></span>

```csharp
private async void btnDownload_Click(object sender, RoutedEventArgs e)
{
    btnDownload.IsEnabled = false;
    try
    {
        txtContents.Text = await m_webPages["https://www.microsoft.com"];
    }
    finally { btnDownload.IsEnabled = true; }
}
```

### <a name="asyncproducerconsumercollection"></a><span data-ttu-id="4cac9-276">AsyncProducerConsumerCollection</span><span class="sxs-lookup"><span data-stu-id="4cac9-276">AsyncProducerConsumerCollection</span></span>
 <span data-ttu-id="4cac9-277">Vous pouvez également utiliser des tâches pour créer des structures de données pour la coordination des activités asynchrones.</span><span class="sxs-lookup"><span data-stu-id="4cac9-277">You can also use tasks to build data structures for coordinating asynchronous activities.</span></span>  <span data-ttu-id="4cac9-278">Considérez un des modèles de conception parallèle classiques : le modèle producteur/consommateur.</span><span class="sxs-lookup"><span data-stu-id="4cac9-278">Consider one of the classic parallel design patterns: producer/consumer.</span></span>  <span data-ttu-id="4cac9-279">Dans ce modèle, les producteurs génèrent des données qui sont utilisées par les consommateurs, et les producteurs et les consommateurs peuvent s’exécuter en parallèle.</span><span class="sxs-lookup"><span data-stu-id="4cac9-279">In this pattern, producers generate data that is consumed by consumers, and the producers and consumers may run in parallel.</span></span> <span data-ttu-id="4cac9-280">Par exemple, le consommateur traite l’élément 1, qui a été généré précédemment par un producteur qui produit maintenant l’élément 2.</span><span class="sxs-lookup"><span data-stu-id="4cac9-280">For example, the consumer processes item 1, which was previously generated by a producer who is now producing item 2.</span></span>  <span data-ttu-id="4cac9-281">Dans le modèle producteur/consommateur, vous avez toujours besoin d’une structure de données pour stocker les données créées par les producteurs afin que les consommateurs puissent être informés des nouvelles données et le trouver lorsqu’elles sont disponibles.</span><span class="sxs-lookup"><span data-stu-id="4cac9-281">For the producer/consumer pattern, you invariably need some data structure to store the work created by producers so that the consumers may be notified of new data and find it when available.</span></span>

 <span data-ttu-id="4cac9-282">Voici une structure de données simple, basée sur des tâches, qui permet d’utiliser des méthodes asynchrones en tant que producteurs et consommateurs :</span><span class="sxs-lookup"><span data-stu-id="4cac9-282">Here's a simple data structure, built on top of tasks, that enables asynchronous methods to be used as producers and consumers:</span></span>

```csharp
public class AsyncProducerConsumerCollection<T>
{
    private readonly Queue<T> m_collection = new Queue<T>();
    private readonly Queue<TaskCompletionSource<T>> m_waiting =
        new Queue<TaskCompletionSource<T>>();

    public void Add(T item)
    {
        TaskCompletionSource<T> tcs = null;
        lock (m_collection)
        {
            if (m_waiting.Count > 0) tcs = m_waiting.Dequeue();
            else m_collection.Enqueue(item);
        }
        if (tcs != null) tcs.TrySetResult(item);
    }

    public Task<T> Take()
    {
        lock (m_collection)
        {
            if (m_collection.Count > 0)
            {
                return Task.FromResult(m_collection.Dequeue());
            }
            else
            {
                var tcs = new TaskCompletionSource<T>();
                m_waiting.Enqueue(tcs);
                return tcs.Task;
            }
        }
    }
}
```

 <span data-ttu-id="4cac9-283">Avec cette structure de données en place, vous pouvez écrire le code suivant :</span><span class="sxs-lookup"><span data-stu-id="4cac9-283">With that data structure in place, you can write code such as the following:</span></span>

```csharp
private static AsyncProducerConsumerCollection<int> m_data = …;
…
private static async Task ConsumerAsync()
{
    while(true)
    {
        int nextItem = await m_data.Take();
        ProcessNextItem(nextItem);
    }
}
…
private static void Produce(int data)
{
    m_data.Add(data);
}
```

<span data-ttu-id="4cac9-284">L’espace de noms <xref:System.Threading.Tasks.Dataflow> inclut le type <xref:System.Threading.Tasks.Dataflow.BufferBlock%601>, que vous pouvez utiliser de manière similaire, mais sans avoir à créer de type de collection personnalisé :</span><span class="sxs-lookup"><span data-stu-id="4cac9-284">The <xref:System.Threading.Tasks.Dataflow> namespace includes the <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> type, which you can use in a similar manner, but without having to build a custom collection type:</span></span>

```csharp
private static BufferBlock<int> m_data = …;
…
private static async Task ConsumerAsync()
{
    while(true)
    {
        int nextItem = await m_data.ReceiveAsync();
        ProcessNextItem(nextItem);
    }
}
…
private static void Produce(int data)
{
    m_data.Post(data);
}
```

> [!NOTE]
> <span data-ttu-id="4cac9-285">L' <xref:System.Threading.Tasks.Dataflow> espace de noms est disponible sous la forme d’un package NuGet.</span><span class="sxs-lookup"><span data-stu-id="4cac9-285">The <xref:System.Threading.Tasks.Dataflow> namespace is available as a NuGet package.</span></span> <span data-ttu-id="4cac9-286">Pour installer l’assembly qui contient l' <xref:System.Threading.Tasks.Dataflow> espace de noms, ouvrez votre projet dans Visual Studio, choisissez **gérer les packages NuGet** dans le menu projet et recherchez en ligne le `System.Threading.Tasks.Dataflow` Package.</span><span class="sxs-lookup"><span data-stu-id="4cac9-286">To install the assembly that contains the <xref:System.Threading.Tasks.Dataflow> namespace, open your project in Visual Studio, choose **Manage NuGet Packages** from the Project menu, and search online for the `System.Threading.Tasks.Dataflow` package.</span></span>

## <a name="see-also"></a><span data-ttu-id="4cac9-287">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4cac9-287">See also</span></span>

- [<span data-ttu-id="4cac9-288">Modèle asynchrone basé sur les tâches (TAP, Task-based Asynchronous Pattern)</span><span class="sxs-lookup"><span data-stu-id="4cac9-288">Task-based Asynchronous Pattern (TAP)</span></span>](task-based-asynchronous-pattern-tap.md)
- [<span data-ttu-id="4cac9-289">Implémentation du modèle asynchrone basé sur des tâches</span><span class="sxs-lookup"><span data-stu-id="4cac9-289">Implementing the Task-based Asynchronous Pattern</span></span>](implementing-the-task-based-asynchronous-pattern.md)
- [<span data-ttu-id="4cac9-290">Interopérabilité avec d’autres types et modèles asynchrones</span><span class="sxs-lookup"><span data-stu-id="4cac9-290">Interop with Other Asynchronous Patterns and Types</span></span>](interop-with-other-asynchronous-patterns-and-types.md)
