---
description: async - Référence C#
title: async - Référence C#
ms.date: 05/22/2017
f1_keywords:
- async_CSharpKeyword
helpviewer_keywords:
- async keyword [C#]
- async method [C#]
- async [C#]
ms.assetid: 16f14f09-b2ce-42c7-a875-e4eca5d50674
ms.openlocfilehash: 78079d9940ea5363215411acea6b9ca269ff3ae1
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91160539"
---
# <a name="async-c-reference"></a><span data-ttu-id="6bd94-103">async (référence C#)</span><span class="sxs-lookup"><span data-stu-id="6bd94-103">async (C# Reference)</span></span>

<span data-ttu-id="6bd94-104">Utilisez le modificateur `async` pour spécifier qu’une méthode, une [expression lambda](../operators/lambda-expressions.md) ou une [méthode anonyme](../operators/delegate-operator.md) sont asynchrones.</span><span class="sxs-lookup"><span data-stu-id="6bd94-104">Use the `async` modifier to specify that a method, [lambda expression](../operators/lambda-expressions.md), or [anonymous method](../operators/delegate-operator.md) is asynchronous.</span></span> <span data-ttu-id="6bd94-105">Si vous utilisez ce modificateur sur une méthode ou une expression, il s’agit d’une *méthode async*.</span><span class="sxs-lookup"><span data-stu-id="6bd94-105">If you use this modifier on a method or expression, it's referred to as an *async method*.</span></span> <span data-ttu-id="6bd94-106">L’exemple suivant définit une méthode async nommée `ExampleMethodAsync` :</span><span class="sxs-lookup"><span data-stu-id="6bd94-106">The following example defines an async method named `ExampleMethodAsync`:</span></span>

```csharp
public async Task<int> ExampleMethodAsync()
{
    //...
}
```

<span data-ttu-id="6bd94-107">Si vous débutez en programmation asynchrone ou que vous ne comprenez pas comment une méthode Async utilise l' [ `await` opérateur](../operators/await.md) pour effectuer un travail potentiellement long sans bloquer le thread de l’appelant, lisez l’introduction de la [programmation asynchrone avec Async et await](../../programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="6bd94-107">If you're new to asynchronous programming or do not understand how an async method uses the [`await` operator](../operators/await.md) to do potentially long-running work without blocking the caller's thread, read the introduction in [Asynchronous programming with async and await](../../programming-guide/concepts/async/index.md).</span></span> <span data-ttu-id="6bd94-108">Le code suivant se trouve dans une méthode async et appelle la méthode <xref:System.Net.Http.HttpClient.GetStringAsync%2a?displayProperty=nameWithType> :</span><span class="sxs-lookup"><span data-stu-id="6bd94-108">The following code is found inside an async method and calls the <xref:System.Net.Http.HttpClient.GetStringAsync%2a?displayProperty=nameWithType> method:</span></span>

```csharp
string contents = await httpClient.GetStringAsync(requestUrl);
```

<span data-ttu-id="6bd94-109">Une méthode async s’exécute de façon synchrone jusqu’à ce qu’elle atteigne sa première expression `await`, où elle est suspendue jusqu’à ce que la tâche attendue soit terminée.</span><span class="sxs-lookup"><span data-stu-id="6bd94-109">An async method runs synchronously until it reaches its first `await` expression, at which point the method is suspended until the awaited task is complete.</span></span> <span data-ttu-id="6bd94-110">Dans le même temps, le contrôle retourne à l'appelant de la méthode, comme le montre l'exemple indiqué dans la section suivante.</span><span class="sxs-lookup"><span data-stu-id="6bd94-110">In the meantime, control returns to the caller of the method, as the example in the next section shows.</span></span>

<span data-ttu-id="6bd94-111">Si la méthode que le mot clé `async` modifie ne contient pas une expression ou une instruction `await`, la méthode s'exécute de façon synchrone.</span><span class="sxs-lookup"><span data-stu-id="6bd94-111">If the method that the `async` keyword modifies doesn't contain an `await` expression or statement, the method executes synchronously.</span></span> <span data-ttu-id="6bd94-112">Un avertissement du compilateur vous signale toutes les méthodes async qui ne contiennent pas d’instructions `await`, car cette situation peut indiquer une erreur.</span><span class="sxs-lookup"><span data-stu-id="6bd94-112">A compiler warning alerts you to any async methods that don't contain `await` statements, because that situation might indicate an error.</span></span> <span data-ttu-id="6bd94-113">Consultez [Avertissement du compilateur (niveau 1) CS4014](../compiler-messages/cs4014.md).</span><span class="sxs-lookup"><span data-stu-id="6bd94-113">See [Compiler Warning (level 1) CS4014](../compiler-messages/cs4014.md).</span></span>

 <span data-ttu-id="6bd94-114">Le mot clé `async` est contextuel, car il est un mot clé uniquement lorsqu'il modifie une méthode, une expression lambda ou une méthode anonyme.</span><span class="sxs-lookup"><span data-stu-id="6bd94-114">The `async` keyword is contextual in that it's a keyword only when it modifies a method, a lambda expression, or an anonymous method.</span></span> <span data-ttu-id="6bd94-115">Dans tous les autres contextes, il est interprété comme un identificateur.</span><span class="sxs-lookup"><span data-stu-id="6bd94-115">In all other contexts, it's interpreted as an identifier.</span></span>

## <a name="example"></a><span data-ttu-id="6bd94-116">Exemple</span><span class="sxs-lookup"><span data-stu-id="6bd94-116">Example</span></span>

<span data-ttu-id="6bd94-117">L'exemple suivant montre la structure et le flux de contrôle entre un gestionnaire d'événements asynchrones, `StartButton_Click`, et une méthode async, `ExampleMethodAsync`.</span><span class="sxs-lookup"><span data-stu-id="6bd94-117">The following example shows the structure and flow of control between an async event handler, `StartButton_Click`, and an async method, `ExampleMethodAsync`.</span></span> <span data-ttu-id="6bd94-118">Le résultat de la méthode async est le nombre de caractères d’une page web.</span><span class="sxs-lookup"><span data-stu-id="6bd94-118">The result from the async method is the number of characters of a web page.</span></span> <span data-ttu-id="6bd94-119">Le code convient pour une application WPF (Windows Presentation Foundation) ou une application du Windows Store que vous créez dans Visual Studio ; consultez les commentaires du code pour configurer l’application.</span><span class="sxs-lookup"><span data-stu-id="6bd94-119">The code is suitable for a Windows Presentation Foundation (WPF) app or Windows Store app that you create in Visual Studio; see the code comments for setting up the app.</span></span>

<span data-ttu-id="6bd94-120">Vous pouvez exécuter ce code dans Visual Studio en tant qu’application Windows Presentation Foundation (WPF) ou qu’application du Windows Store.</span><span class="sxs-lookup"><span data-stu-id="6bd94-120">You can run this code in Visual Studio as a Windows Presentation Foundation (WPF) app or a Windows Store app.</span></span> <span data-ttu-id="6bd94-121">Vous avez besoin d’un contrôle Button nommé `StartButton` et d’un contrôle Textbox nommé `ResultsTextBox`.</span><span class="sxs-lookup"><span data-stu-id="6bd94-121">You need a Button control named `StartButton` and a Textbox control named `ResultsTextBox`.</span></span> <span data-ttu-id="6bd94-122">N’oubliez pas de définir les noms et le gestionnaire afin d’obtenir un résultat semblable à ceci :</span><span class="sxs-lookup"><span data-stu-id="6bd94-122">Remember to set the names and handler so that you have something like this:</span></span>

```xaml
<Button Content="Button" HorizontalAlignment="Left" Margin="88,77,0,0" VerticalAlignment="Top" Width="75"
        Click="StartButton_Click" Name="StartButton"/>
<TextBox HorizontalAlignment="Left" Height="137" Margin="88,140,0,0" TextWrapping="Wrap"
         Text="&lt;Enter a URL&gt;" VerticalAlignment="Top" Width="310" Name="ResultsTextBox"/>
```

<span data-ttu-id="6bd94-123">Pour exécuter le code en tant qu’application WPF :</span><span class="sxs-lookup"><span data-stu-id="6bd94-123">To run the code as a WPF app:</span></span>

- <span data-ttu-id="6bd94-124">Collez ce code dans la classe `MainWindow` dans MainWindow.xaml.cs.</span><span class="sxs-lookup"><span data-stu-id="6bd94-124">Paste this code into the `MainWindow` class in MainWindow.xaml.cs.</span></span>
- <span data-ttu-id="6bd94-125">Ajoutez une référence à System.Net.Http.</span><span class="sxs-lookup"><span data-stu-id="6bd94-125">Add a reference to System.Net.Http.</span></span>
- <span data-ttu-id="6bd94-126">Ajoutez une directive `using` à System.Net.Http.</span><span class="sxs-lookup"><span data-stu-id="6bd94-126">Add a `using` directive for System.Net.Http.</span></span>

<span data-ttu-id="6bd94-127">Pour exécuter le code comme une application du Windows Store :</span><span class="sxs-lookup"><span data-stu-id="6bd94-127">To run the code as a Windows Store app:</span></span>

- <span data-ttu-id="6bd94-128">Collez ce code dans la classe `MainPage` dans MainPage.xaml.cs.</span><span class="sxs-lookup"><span data-stu-id="6bd94-128">Paste this code into the `MainPage` class in MainPage.xaml.cs.</span></span>
- <span data-ttu-id="6bd94-129">Ajouter des directives using pour System.Net.Http et System.Threading.Tasks.</span><span class="sxs-lookup"><span data-stu-id="6bd94-129">Add using directives for System.Net.Http and System.Threading.Tasks.</span></span>

[!code-csharp[wpf-async](../../../../samples/snippets/csharp/language-reference/keywords/async/wpf/mainwindow.xaml.cs#1)]

> [!IMPORTANT]
> <span data-ttu-id="6bd94-130">Pour plus d’informations sur les tâches et le code qui s’exécute en attendant une tâche, consultez [programmation asynchrone avec Async et await](../../programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="6bd94-130">For more information about tasks and the code that executes while waiting for a task, see [Asynchronous programming with async and await](../../programming-guide/concepts/async/index.md).</span></span> <span data-ttu-id="6bd94-131">Pour obtenir un exemple de console complet qui utilise des éléments semblables, consultez [traiter des tâches asynchrones telles qu’elles sont terminées (C#)](../../programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md).</span><span class="sxs-lookup"><span data-stu-id="6bd94-131">For a full console example that uses similar elements, see [Process asynchronous tasks as they complete (C#)](../../programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md).</span></span>

## <a name="return-types"></a><span data-ttu-id="6bd94-132">Types de retour</span><span class="sxs-lookup"><span data-stu-id="6bd94-132">Return Types</span></span>

<span data-ttu-id="6bd94-133">Une méthode async peut avoir les types de retour suivants :</span><span class="sxs-lookup"><span data-stu-id="6bd94-133">An async method can have the following return types:</span></span>

- <xref:System.Threading.Tasks.Task>
- <xref:System.Threading.Tasks.Task%601>
- <span data-ttu-id="6bd94-134">[void](../builtin-types/void.md).</span><span class="sxs-lookup"><span data-stu-id="6bd94-134">[void](../builtin-types/void.md).</span></span> <span data-ttu-id="6bd94-135">Les méthodes `async void` sont généralement déconseillées pour le code autre que les gestionnaires d’événements parce que les appelants ne peuvent pas `await` ces méthodes et doivent implémenter un mécanisme différent pour signaler les conditions d’erreur ou les complétions réussies.</span><span class="sxs-lookup"><span data-stu-id="6bd94-135">`async void` methods are generally discouraged for code other than event handlers because callers cannot `await` those methods and must implement a different mechanism to report successful completion or error conditions.</span></span>
- <span data-ttu-id="6bd94-136">À compter de C# 7.0, tout type ayant une méthode `GetAwaiter` accessible.</span><span class="sxs-lookup"><span data-stu-id="6bd94-136">Starting with C# 7.0, any type that has an accessible `GetAwaiter` method.</span></span> <span data-ttu-id="6bd94-137">Le type `System.Threading.Tasks.ValueTask<TResult>` est une implémentation de ce genre.</span><span class="sxs-lookup"><span data-stu-id="6bd94-137">The `System.Threading.Tasks.ValueTask<TResult>` type is one such implementation.</span></span> <span data-ttu-id="6bd94-138">Il est disponible en ajoutant le package NuGet `System.Threading.Tasks.Extensions`.</span><span class="sxs-lookup"><span data-stu-id="6bd94-138">It is available by adding the NuGet package `System.Threading.Tasks.Extensions`.</span></span>

<span data-ttu-id="6bd94-139">La méthode async ne peut déclarer aucun paramètre [in](./in-parameter-modifier.md), [ref](./ref.md) ou [out](./out-parameter-modifier.md), ni avoir une [valeur de retour de référence](../../programming-guide/classes-and-structs/ref-returns.md), mais elle peut appeler des méthodes qui ont ces paramètres.</span><span class="sxs-lookup"><span data-stu-id="6bd94-139">The async method can't declare any [in](./in-parameter-modifier.md), [ref](./ref.md) or [out](./out-parameter-modifier.md) parameters, nor can it have a [reference return value](../../programming-guide/classes-and-structs/ref-returns.md), but it can call methods that have such parameters.</span></span>

<span data-ttu-id="6bd94-140">Vous spécifiez `Task<TResult>` comme type de retour d’une méthode async si l’instruction [return](./return.md) de la méthode spécifie un opérande de type `TResult`.</span><span class="sxs-lookup"><span data-stu-id="6bd94-140">You specify `Task<TResult>` as the return type of an async method if the [return](./return.md) statement of the method specifies an operand of type `TResult`.</span></span> <span data-ttu-id="6bd94-141">Utilisez `Task` si aucune valeur significative n'est retournée lorsque la méthode est terminée.</span><span class="sxs-lookup"><span data-stu-id="6bd94-141">You use `Task` if no meaningful value is returned when the method is completed.</span></span> <span data-ttu-id="6bd94-142">En d'autres termes, un appel à la méthode retourne `Task`, mais lorsque `Task` est terminé, toute expression `await` qui attend `Task` prend la valeur `void`.</span><span class="sxs-lookup"><span data-stu-id="6bd94-142">That is, a call to the method returns a `Task`, but when the `Task` is completed, any `await` expression that's awaiting the `Task` evaluates to `void`.</span></span>

<span data-ttu-id="6bd94-143">Vous utilisez le type de retour `void` principalement pour définir les gestionnaires d'événements, qui ont besoin de ce type de retour.</span><span class="sxs-lookup"><span data-stu-id="6bd94-143">You use the `void` return type primarily to define event handlers, which require that return type.</span></span> <span data-ttu-id="6bd94-144">L'appelant d'une méthode async retournant `void` ne peut pas l'attendre et ne peut pas intercepter les exceptions levées par la méthode.</span><span class="sxs-lookup"><span data-stu-id="6bd94-144">The caller of a `void`-returning async method can't await it and can't catch exceptions that the method throws.</span></span>

<span data-ttu-id="6bd94-145">À partir de C# 7.0, vous retournez un autre type, en général un type valeur, qui a une méthode `GetAwaiter` permettant de limiter les allocations de mémoire dans les sections de code critiques pour les performances.</span><span class="sxs-lookup"><span data-stu-id="6bd94-145">Starting with C# 7.0, you return another type, typically a value type, that has a `GetAwaiter` method to minimize memory allocations in performance-critical sections of code.</span></span>

<span data-ttu-id="6bd94-146">Pour obtenir plus d’informations et des exemples, consultez [Types de retour Async](../../programming-guide/concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="6bd94-146">For more information and examples, see [Async Return Types](../../programming-guide/concepts/async/async-return-types.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="6bd94-147">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6bd94-147">See also</span></span>

- <xref:System.Runtime.CompilerServices.AsyncStateMachineAttribute>
- [<span data-ttu-id="6bd94-148">await</span><span class="sxs-lookup"><span data-stu-id="6bd94-148">await</span></span>](../operators/await.md)
- [<span data-ttu-id="6bd94-149">Programmation asynchrone avec Async et await</span><span class="sxs-lookup"><span data-stu-id="6bd94-149">Asynchronous programming with async and await</span></span>](../../programming-guide/concepts/async/index.md)
- [<span data-ttu-id="6bd94-150">Traiter les tâches asynchrones terminées</span><span class="sxs-lookup"><span data-stu-id="6bd94-150">Process asynchronous tasks as they complete</span></span>](../../programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md)
