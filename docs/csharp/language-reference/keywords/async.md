---
title: async - Référence C#
ms.date: 05/22/2017
f1_keywords:
- async_CSharpKeyword
helpviewer_keywords:
- async keyword [C#]
- async method [C#]
- async [C#]
ms.assetid: 16f14f09-b2ce-42c7-a875-e4eca5d50674
ms.openlocfilehash: d2c1de12a0a836fd4a7962ebbfe890f21ea3d5a7
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88811728"
---
# <a name="async-c-reference"></a><span data-ttu-id="4c168-102">async (référence C#)</span><span class="sxs-lookup"><span data-stu-id="4c168-102">async (C# Reference)</span></span>

<span data-ttu-id="4c168-103">Utilisez le modificateur `async` pour spécifier qu’une méthode, une [expression lambda](../operators/lambda-expressions.md) ou une [méthode anonyme](../operators/delegate-operator.md) sont asynchrones.</span><span class="sxs-lookup"><span data-stu-id="4c168-103">Use the `async` modifier to specify that a method, [lambda expression](../operators/lambda-expressions.md), or [anonymous method](../operators/delegate-operator.md) is asynchronous.</span></span> <span data-ttu-id="4c168-104">Si vous utilisez ce modificateur sur une méthode ou une expression, il s’agit d’une *méthode async*.</span><span class="sxs-lookup"><span data-stu-id="4c168-104">If you use this modifier on a method or expression, it's referred to as an *async method*.</span></span> <span data-ttu-id="4c168-105">L’exemple suivant définit une méthode async nommée `ExampleMethodAsync` :</span><span class="sxs-lookup"><span data-stu-id="4c168-105">The following example defines an async method named `ExampleMethodAsync`:</span></span>

```csharp
public async Task<int> ExampleMethodAsync()
{
    //...
}
```

<span data-ttu-id="4c168-106">Si vous débutez en programmation asynchrone ou que vous ne comprenez pas comment une méthode Async utilise l' [ `await` opérateur](../operators/await.md) pour effectuer un travail potentiellement long sans bloquer le thread de l’appelant, lisez l’introduction de la [programmation asynchrone avec Async et await](../../programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="4c168-106">If you're new to asynchronous programming or do not understand how an async method uses the [`await` operator](../operators/await.md) to do potentially long-running work without blocking the caller's thread, read the introduction in [Asynchronous programming with async and await](../../programming-guide/concepts/async/index.md).</span></span> <span data-ttu-id="4c168-107">Le code suivant se trouve dans une méthode async et appelle la méthode <xref:System.Net.Http.HttpClient.GetStringAsync%2a?displayProperty=nameWithType> :</span><span class="sxs-lookup"><span data-stu-id="4c168-107">The following code is found inside an async method and calls the <xref:System.Net.Http.HttpClient.GetStringAsync%2a?displayProperty=nameWithType> method:</span></span>

```csharp
string contents = await httpClient.GetStringAsync(requestUrl);
```

<span data-ttu-id="4c168-108">Une méthode async s’exécute de façon synchrone jusqu’à ce qu’elle atteigne sa première expression `await`, où elle est suspendue jusqu’à ce que la tâche attendue soit terminée.</span><span class="sxs-lookup"><span data-stu-id="4c168-108">An async method runs synchronously until it reaches its first `await` expression, at which point the method is suspended until the awaited task is complete.</span></span> <span data-ttu-id="4c168-109">Dans le même temps, le contrôle retourne à l'appelant de la méthode, comme le montre l'exemple indiqué dans la section suivante.</span><span class="sxs-lookup"><span data-stu-id="4c168-109">In the meantime, control returns to the caller of the method, as the example in the next section shows.</span></span>

<span data-ttu-id="4c168-110">Si la méthode que le mot clé `async` modifie ne contient pas une expression ou une instruction `await`, la méthode s'exécute de façon synchrone.</span><span class="sxs-lookup"><span data-stu-id="4c168-110">If the method that the `async` keyword modifies doesn't contain an `await` expression or statement, the method executes synchronously.</span></span> <span data-ttu-id="4c168-111">Un avertissement du compilateur vous signale toutes les méthodes async qui ne contiennent pas d’instructions `await`, car cette situation peut indiquer une erreur.</span><span class="sxs-lookup"><span data-stu-id="4c168-111">A compiler warning alerts you to any async methods that don't contain `await` statements, because that situation might indicate an error.</span></span> <span data-ttu-id="4c168-112">Consultez [Avertissement du compilateur (niveau 1) CS4014](../compiler-messages/cs4014.md).</span><span class="sxs-lookup"><span data-stu-id="4c168-112">See [Compiler Warning (level 1) CS4014](../compiler-messages/cs4014.md).</span></span>

 <span data-ttu-id="4c168-113">Le mot clé `async` est contextuel, car il est un mot clé uniquement lorsqu'il modifie une méthode, une expression lambda ou une méthode anonyme.</span><span class="sxs-lookup"><span data-stu-id="4c168-113">The `async` keyword is contextual in that it's a keyword only when it modifies a method, a lambda expression, or an anonymous method.</span></span> <span data-ttu-id="4c168-114">Dans tous les autres contextes, il est interprété comme un identificateur.</span><span class="sxs-lookup"><span data-stu-id="4c168-114">In all other contexts, it's interpreted as an identifier.</span></span>

## <a name="example"></a><span data-ttu-id="4c168-115">Exemple</span><span class="sxs-lookup"><span data-stu-id="4c168-115">Example</span></span>
<span data-ttu-id="4c168-116">L'exemple suivant montre la structure et le flux de contrôle entre un gestionnaire d'événements asynchrones, `StartButton_Click`, et une méthode async, `ExampleMethodAsync`.</span><span class="sxs-lookup"><span data-stu-id="4c168-116">The following example shows the structure and flow of control between an async event handler, `StartButton_Click`, and an async method, `ExampleMethodAsync`.</span></span> <span data-ttu-id="4c168-117">Le résultat de la méthode async est le nombre de caractères d’une page web.</span><span class="sxs-lookup"><span data-stu-id="4c168-117">The result from the async method is the number of characters of a web page.</span></span> <span data-ttu-id="4c168-118">Le code convient pour une application WPF (Windows Presentation Foundation) ou une application du Windows Store que vous créez dans Visual Studio ; consultez les commentaires du code pour configurer l’application.</span><span class="sxs-lookup"><span data-stu-id="4c168-118">The code is suitable for a Windows Presentation Foundation (WPF) app or Windows Store app that you create in Visual Studio; see the code comments for setting up the app.</span></span>

<span data-ttu-id="4c168-119">Vous pouvez exécuter ce code dans Visual Studio en tant qu’application Windows Presentation Foundation (WPF) ou qu’application du Windows Store.</span><span class="sxs-lookup"><span data-stu-id="4c168-119">You can run this code in Visual Studio as a Windows Presentation Foundation (WPF) app or a Windows Store app.</span></span> <span data-ttu-id="4c168-120">Vous avez besoin d’un contrôle Button nommé `StartButton` et d’un contrôle Textbox nommé `ResultsTextBox`.</span><span class="sxs-lookup"><span data-stu-id="4c168-120">You need a Button control named `StartButton` and a Textbox control named `ResultsTextBox`.</span></span> <span data-ttu-id="4c168-121">N’oubliez pas de définir les noms et le gestionnaire afin d’obtenir un résultat semblable à ceci :</span><span class="sxs-lookup"><span data-stu-id="4c168-121">Remember to set the names and handler so that you have something like this:</span></span>

```xaml
<Button Content="Button" HorizontalAlignment="Left" Margin="88,77,0,0" VerticalAlignment="Top" Width="75"
        Click="StartButton_Click" Name="StartButton"/>
<TextBox HorizontalAlignment="Left" Height="137" Margin="88,140,0,0" TextWrapping="Wrap"
         Text="&lt;Enter a URL&gt;" VerticalAlignment="Top" Width="310" Name="ResultsTextBox"/>
```

<span data-ttu-id="4c168-122">Pour exécuter le code en tant qu’application WPF :</span><span class="sxs-lookup"><span data-stu-id="4c168-122">To run the code as a WPF app:</span></span>

- <span data-ttu-id="4c168-123">Collez ce code dans la classe `MainWindow` dans MainWindow.xaml.cs.</span><span class="sxs-lookup"><span data-stu-id="4c168-123">Paste this code into the `MainWindow` class in MainWindow.xaml.cs.</span></span>
- <span data-ttu-id="4c168-124">Ajoutez une référence à System.Net.Http.</span><span class="sxs-lookup"><span data-stu-id="4c168-124">Add a reference to System.Net.Http.</span></span>
- <span data-ttu-id="4c168-125">Ajoutez une directive `using` à System.Net.Http.</span><span class="sxs-lookup"><span data-stu-id="4c168-125">Add a `using` directive for System.Net.Http.</span></span>

<span data-ttu-id="4c168-126">Pour exécuter le code comme une application du Windows Store :</span><span class="sxs-lookup"><span data-stu-id="4c168-126">To run the code as a Windows Store app:</span></span>

- <span data-ttu-id="4c168-127">Collez ce code dans la classe `MainPage` dans MainPage.xaml.cs.</span><span class="sxs-lookup"><span data-stu-id="4c168-127">Paste this code into the `MainPage` class in MainPage.xaml.cs.</span></span>
- <span data-ttu-id="4c168-128">Ajouter des directives using pour System.Net.Http et System.Threading.Tasks.</span><span class="sxs-lookup"><span data-stu-id="4c168-128">Add using directives for System.Net.Http and System.Threading.Tasks.</span></span>

[!code-csharp[wpf-async](../../../../samples/snippets/csharp/language-reference/keywords/async/wpf/mainwindow.xaml.cs#1)]

> [!IMPORTANT]
> <span data-ttu-id="4c168-129">Pour plus d’informations sur les tâches et le code qui s’exécute en attendant une tâche, consultez [programmation asynchrone avec Async et await](../../programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="4c168-129">For more information about tasks and the code that executes while waiting for a task, see [Asynchronous programming with async and await](../../programming-guide/concepts/async/index.md).</span></span> <span data-ttu-id="4c168-130">Pour obtenir un exemple de console complet qui utilise des éléments semblables, consultez [traiter des tâches asynchrones telles qu’elles sont terminées (C#)](../../programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md).</span><span class="sxs-lookup"><span data-stu-id="4c168-130">For a full console example that uses similar elements, see [Process asynchronous tasks as they complete (C#)](../../programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md).</span></span>

## <a name="return-types"></a><span data-ttu-id="4c168-131">Types de retour</span><span class="sxs-lookup"><span data-stu-id="4c168-131">Return Types</span></span>
<span data-ttu-id="4c168-132">Une méthode async peut avoir les types de retour suivants :</span><span class="sxs-lookup"><span data-stu-id="4c168-132">An async method can have the following return types:</span></span>

- <xref:System.Threading.Tasks.Task>
- <xref:System.Threading.Tasks.Task%601>
- <span data-ttu-id="4c168-133">[void](../builtin-types/void.md).</span><span class="sxs-lookup"><span data-stu-id="4c168-133">[void](../builtin-types/void.md).</span></span> <span data-ttu-id="4c168-134">Les méthodes `async void` sont généralement déconseillées pour le code autre que les gestionnaires d’événements parce que les appelants ne peuvent pas `await` ces méthodes et doivent implémenter un mécanisme différent pour signaler les conditions d’erreur ou les complétions réussies.</span><span class="sxs-lookup"><span data-stu-id="4c168-134">`async void` methods are generally discouraged for code other than event handlers because callers cannot `await` those methods and must implement a different mechanism to report successful completion or error conditions.</span></span>
- <span data-ttu-id="4c168-135">À compter de C# 7.0, tout type ayant une méthode `GetAwaiter` accessible.</span><span class="sxs-lookup"><span data-stu-id="4c168-135">Starting with C# 7.0, any type that has an accessible `GetAwaiter` method.</span></span> <span data-ttu-id="4c168-136">Le type `System.Threading.Tasks.ValueTask<TResult>` est une implémentation de ce genre.</span><span class="sxs-lookup"><span data-stu-id="4c168-136">The `System.Threading.Tasks.ValueTask<TResult>` type is one such implementation.</span></span> <span data-ttu-id="4c168-137">Il est disponible en ajoutant le package NuGet `System.Threading.Tasks.Extensions`.</span><span class="sxs-lookup"><span data-stu-id="4c168-137">It is available by adding the NuGet package `System.Threading.Tasks.Extensions`.</span></span>

<span data-ttu-id="4c168-138">La méthode async ne peut déclarer aucun paramètre [in](./in-parameter-modifier.md), [ref](./ref.md) ou [out](./out-parameter-modifier.md), ni avoir une [valeur de retour de référence](../../programming-guide/classes-and-structs/ref-returns.md), mais elle peut appeler des méthodes qui ont ces paramètres.</span><span class="sxs-lookup"><span data-stu-id="4c168-138">The async method can't declare any [in](./in-parameter-modifier.md), [ref](./ref.md) or [out](./out-parameter-modifier.md) parameters, nor can it have a [reference return value](../../programming-guide/classes-and-structs/ref-returns.md), but it can call methods that have such parameters.</span></span>

<span data-ttu-id="4c168-139">Vous spécifiez `Task<TResult>` comme type de retour d’une méthode async si l’instruction [return](./return.md) de la méthode spécifie un opérande de type `TResult`.</span><span class="sxs-lookup"><span data-stu-id="4c168-139">You specify `Task<TResult>` as the return type of an async method if the [return](./return.md) statement of the method specifies an operand of type `TResult`.</span></span> <span data-ttu-id="4c168-140">Utilisez `Task` si aucune valeur significative n'est retournée lorsque la méthode est terminée.</span><span class="sxs-lookup"><span data-stu-id="4c168-140">You use `Task` if no meaningful value is returned when the method is completed.</span></span> <span data-ttu-id="4c168-141">En d'autres termes, un appel à la méthode retourne `Task`, mais lorsque `Task` est terminé, toute expression `await` qui attend `Task` prend la valeur `void`.</span><span class="sxs-lookup"><span data-stu-id="4c168-141">That is, a call to the method returns a `Task`, but when the `Task` is completed, any `await` expression that's awaiting the `Task` evaluates to `void`.</span></span>

<span data-ttu-id="4c168-142">Vous utilisez le type de retour `void` principalement pour définir les gestionnaires d'événements, qui ont besoin de ce type de retour.</span><span class="sxs-lookup"><span data-stu-id="4c168-142">You use the `void` return type primarily to define event handlers, which require that return type.</span></span> <span data-ttu-id="4c168-143">L'appelant d'une méthode async retournant `void` ne peut pas l'attendre et ne peut pas intercepter les exceptions levées par la méthode.</span><span class="sxs-lookup"><span data-stu-id="4c168-143">The caller of a `void`-returning async method can't await it and can't catch exceptions that the method throws.</span></span>

<span data-ttu-id="4c168-144">À partir de C# 7.0, vous retournez un autre type, en général un type valeur, qui a une méthode `GetAwaiter` permettant de limiter les allocations de mémoire dans les sections de code critiques pour les performances.</span><span class="sxs-lookup"><span data-stu-id="4c168-144">Starting with C# 7.0, you return another type, typically a value type, that has a `GetAwaiter` method to minimize memory allocations in performance-critical sections of code.</span></span>

<span data-ttu-id="4c168-145">Pour obtenir plus d’informations et des exemples, consultez [Types de retour Async](../../programming-guide/concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="4c168-145">For more information and examples, see [Async Return Types](../../programming-guide/concepts/async/async-return-types.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4c168-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4c168-146">See also</span></span>

- <xref:System.Runtime.CompilerServices.AsyncStateMachineAttribute>
- [<span data-ttu-id="4c168-147">await</span><span class="sxs-lookup"><span data-stu-id="4c168-147">await</span></span>](../operators/await.md)
- [<span data-ttu-id="4c168-148">Programmation asynchrone avec Async et Await</span><span class="sxs-lookup"><span data-stu-id="4c168-148">Asynchronous programming with async and await</span></span>](../../programming-guide/concepts/async/index.md)
- [<span data-ttu-id="4c168-149">Traiter les tâches asynchrones terminées</span><span class="sxs-lookup"><span data-stu-id="4c168-149">Process asynchronous tasks as they complete</span></span>](../../programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md)
