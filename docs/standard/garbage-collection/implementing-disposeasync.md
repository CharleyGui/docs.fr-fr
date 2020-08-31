---
title: Implémenter une méthode DisposeAsync
description: Découvrez comment implémenter des méthodes DisposeAsync et DisposeAsyncCore pour effectuer un nettoyage asynchrone des ressources.
author: IEvangelist
ms.author: dapine
ms.date: 08/25/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
helpviewer_keywords:
- DisposeAsync method
- garbage collection, DisposeAsync method
ms.openlocfilehash: 268cea7584040ad92e2da75e5e03112480cda93c
ms.sourcegitcommit: 2560a355c76b0a04cba0d34da870df9ad94ceca3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/28/2020
ms.locfileid: "89053176"
---
# <a name="implement-a-disposeasync-method"></a><span data-ttu-id="80b80-103">Implémenter une méthode DisposeAsync</span><span class="sxs-lookup"><span data-stu-id="80b80-103">Implement a DisposeAsync method</span></span>

<span data-ttu-id="80b80-104">L' <xref:System.IAsyncDisposable?displayProperty=nameWithType> interface a été introduite dans le cadre de C# 8,0.</span><span class="sxs-lookup"><span data-stu-id="80b80-104">The <xref:System.IAsyncDisposable?displayProperty=nameWithType> interface was introduced as part of C# 8.0.</span></span> <span data-ttu-id="80b80-105">Vous implémentez la <xref:System.IAsyncDisposable.DisposeAsync?displayProperty=nameWithType> méthode lorsque vous devez effectuer un nettoyage des ressources, comme vous le feriez lors de l' [implémentation d’une méthode dispose](implementing-dispose.md).</span><span class="sxs-lookup"><span data-stu-id="80b80-105">You implement the <xref:System.IAsyncDisposable.DisposeAsync?displayProperty=nameWithType> method when you need to perform resource cleanup, just as you would when [implementing a Dispose method](implementing-dispose.md).</span></span> <span data-ttu-id="80b80-106">Toutefois, l’une des principales différences est que cette implémentation autorise les opérations de nettoyage asynchrones.</span><span class="sxs-lookup"><span data-stu-id="80b80-106">One of the key differences however, is that this implementation allows for asynchronous cleanup operations.</span></span> <span data-ttu-id="80b80-107"><xref:System.IAsyncDisposable.DisposeAsync>Retourne un <xref:System.Threading.Tasks.ValueTask> qui représente l’opération de suppression asynchrone.</span><span class="sxs-lookup"><span data-stu-id="80b80-107">The <xref:System.IAsyncDisposable.DisposeAsync> returns a <xref:System.Threading.Tasks.ValueTask> that represents the asynchronous dispose operation.</span></span>

<span data-ttu-id="80b80-108">C’est généralement le cas lors de l’implémentation de l' <xref:System.IAsyncDisposable> interface que les classes implémentent également l' <xref:System.IDisposable> interface.</span><span class="sxs-lookup"><span data-stu-id="80b80-108">It is typical when implementing the <xref:System.IAsyncDisposable> interface that classes will also implement the <xref:System.IDisposable> interface.</span></span> <span data-ttu-id="80b80-109">Un modèle d’implémentation correct de l' <xref:System.IAsyncDisposable> interface doit être préparé pour une suppression synchrone ou asynchrone.</span><span class="sxs-lookup"><span data-stu-id="80b80-109">A good implementation pattern of the <xref:System.IAsyncDisposable> interface is to be prepared for either synchronous, or asynchronous dispose.</span></span> <span data-ttu-id="80b80-110">Toutes les instructions pour l’implémentation du modèle de suppression s’appliquent également à l’implémentation asynchrone.</span><span class="sxs-lookup"><span data-stu-id="80b80-110">All of the guidance for implementing the dispose pattern also applies to the asynchronous implementation.</span></span> <span data-ttu-id="80b80-111">Cet article suppose que vous êtes déjà familiarisé avec l’implémentation d' [une méthode dispose](implementing-dispose.md).</span><span class="sxs-lookup"><span data-stu-id="80b80-111">This article assumes that you're already familiar with how to [implement a Dispose method](implementing-dispose.md).</span></span>

## <a name="disposeasync-and-disposeasynccore"></a><span data-ttu-id="80b80-112">DisposeAsync () et DisposeAsyncCore ()</span><span class="sxs-lookup"><span data-stu-id="80b80-112">DisposeAsync() and DisposeAsyncCore()</span></span>

<span data-ttu-id="80b80-113">L' <xref:System.IAsyncDisposable> interface déclare une méthode sans paramètre unique, <xref:System.IAsyncDisposable.DisposeAsync> .</span><span class="sxs-lookup"><span data-stu-id="80b80-113">The <xref:System.IAsyncDisposable> interface declares a single parameterless method, <xref:System.IAsyncDisposable.DisposeAsync>.</span></span> <span data-ttu-id="80b80-114">Toute classe non scellée doit avoir une `DisposeAsyncCore()` méthode supplémentaire qui retourne également un <xref:System.Threading.Tasks.ValueTask> .</span><span class="sxs-lookup"><span data-stu-id="80b80-114">Any non-sealed class should have an additional `DisposeAsyncCore()` method that also returns a <xref:System.Threading.Tasks.ValueTask>.</span></span>

- <span data-ttu-id="80b80-115">`public` <xref:System.IAsyncDisposable.DisposeAsync?displayProperty=nameWithType> Implémentation qui n’a aucun paramètre.</span><span class="sxs-lookup"><span data-stu-id="80b80-115">A `public` <xref:System.IAsyncDisposable.DisposeAsync?displayProperty=nameWithType> implementation that has no parameters.</span></span>
- <span data-ttu-id="80b80-116">Une `protected virtual ValueTask DisposeAsyncCore()` méthode dont la signature est :</span><span class="sxs-lookup"><span data-stu-id="80b80-116">A `protected virtual ValueTask DisposeAsyncCore()` method whose signature is:</span></span>

  ```csharp
  protected virtual ValueTask DisposeAsyncCore()
  {
  }
  ```

### <a name="the-disposeasync-method"></a><span data-ttu-id="80b80-117">Méthode DisposeAsync ()</span><span class="sxs-lookup"><span data-stu-id="80b80-117">The DisposeAsync() method</span></span>

<span data-ttu-id="80b80-118">La `public` méthode sans paramètre `DisposeAsync()` est appelée implicitement dans une `await using` instruction, et son objectif est de libérer des ressources non managées, d’effectuer un nettoyage général et d’indiquer que le finaliseur, s’il en existe un, ne doit pas être exécuté.</span><span class="sxs-lookup"><span data-stu-id="80b80-118">The `public` parameterless `DisposeAsync()` method is called implicitly in an `await using` statement, and its purpose is to free unmanaged resources, perform general cleanup, and to indicate that the finalizer, if one is present, need not run.</span></span> <span data-ttu-id="80b80-119">La libération de la mémoire associée à un objet géré est toujours le domaine du [garbage collector](index.md).</span><span class="sxs-lookup"><span data-stu-id="80b80-119">Freeing the memory associated with a managed object is always the domain of the [garbage collector](index.md).</span></span> <span data-ttu-id="80b80-120">De ce fait, son implémentation standard est la suivante :</span><span class="sxs-lookup"><span data-stu-id="80b80-120">Because of this, it has a standard implementation:</span></span>

```csharp
public async ValueTask DisposeAsync()
{
    // Perform async cleanup.
    await DisposeAsyncCore();

    // Dispose of unmanaged resources.
    Dispose(false);
    // Suppress finalization.
    GC.SuppressFinalize(this);
}
```

> [!NOTE]
> <span data-ttu-id="80b80-121">L’une des principales différences dans le modèle de suppression asynchrone par rapport au modèle de suppression est que l’appel de <xref:System.IAsyncDisposable.DisposeAsync> à la `Dispose(bool)` méthode de surcharge est donné `false` comme argument.</span><span class="sxs-lookup"><span data-stu-id="80b80-121">One primary difference in the async dispose pattern compared to the dispose pattern, is that the call from <xref:System.IAsyncDisposable.DisposeAsync> to the `Dispose(bool)` overload method is given `false` as an argument.</span></span> <span data-ttu-id="80b80-122">Toutefois, lors de l’implémentation de la <xref:System.IDisposable.Dispose?displayProperty=nameWithType> méthode, `true` est passé.</span><span class="sxs-lookup"><span data-stu-id="80b80-122">When implementing the <xref:System.IDisposable.Dispose?displayProperty=nameWithType> method, however; `true` is passed instead.</span></span> <span data-ttu-id="80b80-123">Cela permet de garantir l’équivalence fonctionnelle avec le modèle de suppression synchrone et de s’assurer que les chemins de code du finaliseur sont toujours appelés.</span><span class="sxs-lookup"><span data-stu-id="80b80-123">This helps ensure functional equivalence with the synchronous dispose pattern, and further ensures that finalizer code paths still get invoked.</span></span> <span data-ttu-id="80b80-124">En d’autres termes, la `DisposeAsyncCore()` méthode supprime les ressources managées de manière asynchrone, donc vous ne voulez pas les supprimer de manière synchrone.</span><span class="sxs-lookup"><span data-stu-id="80b80-124">In other words, the `DisposeAsyncCore()` method will dispose of managed resources asynchronously, so you don't want to dispose of them synchronously as well.</span></span> <span data-ttu-id="80b80-125">Par conséquent, appelez `Dispose(false)` au lieu de `Dispose(true)` .</span><span class="sxs-lookup"><span data-stu-id="80b80-125">Therefore, call `Dispose(false)` instead of `Dispose(true)`.</span></span>

### <a name="the-disposeasynccore-method"></a><span data-ttu-id="80b80-126">Méthode DisposeAsyncCore ()</span><span class="sxs-lookup"><span data-stu-id="80b80-126">The DisposeAsyncCore() method</span></span>

<span data-ttu-id="80b80-127">La `DisposeAsyncCore()` méthode est conçue pour effectuer le nettoyage asynchrone des ressources managées ou pour les appels en cascade à `DisposeAsync()` .</span><span class="sxs-lookup"><span data-stu-id="80b80-127">The `DisposeAsyncCore()` method is intended to perform the asynchronous cleanup of managed resources or for cascading calls to `DisposeAsync()`.</span></span> <span data-ttu-id="80b80-128">Il encapsule les opérations de nettoyage asynchrone courantes lorsqu’une sous-classe hérite d’une classe de base qui est une implémentation de <xref:System.IAsyncDisposable> .</span><span class="sxs-lookup"><span data-stu-id="80b80-128">It encapsulates the common asynchronous cleanup operations when a subclass inherits a base class that is an implementation of <xref:System.IAsyncDisposable>.</span></span> <span data-ttu-id="80b80-129">La `DisposeAsyncCore()` méthode `virtual` permet aux classes dérivées de définir un nettoyage supplémentaire dans leurs substitutions.</span><span class="sxs-lookup"><span data-stu-id="80b80-129">The `DisposeAsyncCore()` method is `virtual` so that derived classes can define additional cleanup in their overrides.</span></span>

> [!TIP]
> <span data-ttu-id="80b80-130">Si une implémentation de <xref:System.IAsyncDisposable> est `sealed` , la `DisposeAsyncCore()` méthode n’est pas nécessaire et le nettoyage asynchrone peut être effectué directement dans la <xref:System.IAsyncDisposable.DisposeAsync?displayProperty=nameWithType> méthode.</span><span class="sxs-lookup"><span data-stu-id="80b80-130">If an implementation of <xref:System.IAsyncDisposable> is `sealed`, the `DisposeAsyncCore()` method is not needed, and the asynchronous cleanup can be performed directly in the <xref:System.IAsyncDisposable.DisposeAsync?displayProperty=nameWithType> method.</span></span>

## <a name="implement-the-async-dispose-pattern"></a><span data-ttu-id="80b80-131">Implémenter le modèle de suppression asynchrone</span><span class="sxs-lookup"><span data-stu-id="80b80-131">Implement the async dispose pattern</span></span>

<span data-ttu-id="80b80-132">Toutes les classes non-sealed doivent être considérées comme une classe de base potentielle, car elles peuvent être héritées.</span><span class="sxs-lookup"><span data-stu-id="80b80-132">All non-sealed classes should be considered a potential base class, because they could be inherited.</span></span> <span data-ttu-id="80b80-133">Si vous implémentez le modèle de suppression Async pour une classe de base potentielle quelconque, vous devez fournir la `protected virtual ValueTask DisposeAsyncCore()` méthode.</span><span class="sxs-lookup"><span data-stu-id="80b80-133">If you implement the async dispose pattern for any potential base class, you must provide the `protected virtual ValueTask DisposeAsyncCore()` method.</span></span> <span data-ttu-id="80b80-134">Voici un exemple d’implémentation du modèle asynchrone dispose qui utilise un <xref:System.Text.Json.Utf8JsonWriter?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="80b80-134">Here is an example implementation of the async dispose pattern that uses a <xref:System.Text.Json.Utf8JsonWriter?displayProperty=nameWithType>.</span></span>

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/disposeasync.cs":::

<span data-ttu-id="80b80-135">L’exemple précédent utilise <xref:System.Text.Json.Utf8JsonWriter> .</span><span class="sxs-lookup"><span data-stu-id="80b80-135">The preceding example uses the <xref:System.Text.Json.Utf8JsonWriter>.</span></span> <span data-ttu-id="80b80-136">Pour plus d’informations sur `System.Text.Json` , voir [How to migrate from Newtonsoft.Json to System.Text.Json](../serialization/system-text-json-migrate-from-newtonsoft-how-to.md).</span><span class="sxs-lookup"><span data-stu-id="80b80-136">For more information about `System.Text.Json`, see [How to migrate from Newtonsoft.Json to System.Text.Json](../serialization/system-text-json-migrate-from-newtonsoft-how-to.md).</span></span>

## <a name="using-async-disposable"></a><span data-ttu-id="80b80-137">Utilisation de Async jetable</span><span class="sxs-lookup"><span data-stu-id="80b80-137">Using async disposable</span></span>

<span data-ttu-id="80b80-138">Pour utiliser correctement un objet qui implémente l' <xref:System.IAsyncDisposable> interface, vous utilisez l' [expression await](../../csharp/language-reference/operators/await.md)et les mots clés [en](../../csharp/language-reference/keywords/using-statement.md) même temps.</span><span class="sxs-lookup"><span data-stu-id="80b80-138">To properly consume an object that implements the <xref:System.IAsyncDisposable> interface, you use the [await](../../csharp/language-reference/operators/await.md), and [using](../../csharp/language-reference/keywords/using-statement.md) keywords together.</span></span> <span data-ttu-id="80b80-139">Prenons l’exemple suivant, où la `ExampleAsyncDisposable` classe est instanciée puis encapsulée dans une `await using` instruction.</span><span class="sxs-lookup"><span data-stu-id="80b80-139">Consider the following example, where the `ExampleAsyncDisposable` class is instantiated and then wrapped in an `await using` statement.</span></span>

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/proper-await-using.cs":::

> [!IMPORTANT]
> <span data-ttu-id="80b80-140">Utilisez la <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait(System.IAsyncDisposable,System.Boolean)> méthode d’extension de l' <xref:System.IAsyncDisposable> interface pour configurer la façon dont la continuation de la tâche est marshalée sur son contexte ou planificateur d’origine.</span><span class="sxs-lookup"><span data-stu-id="80b80-140">Use the <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait(System.IAsyncDisposable,System.Boolean)> extension method of the <xref:System.IAsyncDisposable> interface to configure how the continuation of the task is marshalled on its original context or scheduler.</span></span> <span data-ttu-id="80b80-141">Pour plus d’informations sur `ConfigureAwait` , consultez le [Forum aux questions ConfigureAwait](https://devblogs.microsoft.com/dotnet/configureawait-faq/).</span><span class="sxs-lookup"><span data-stu-id="80b80-141">For more information on `ConfigureAwait`, see [ConfigureAwait FAQ](https://devblogs.microsoft.com/dotnet/configureawait-faq/).</span></span>

<span data-ttu-id="80b80-142">Dans les situations où l’utilisation de `ConfigureAwait` n’est pas nécessaire, l' `await using` instruction peut être simplifiée comme suit :</span><span class="sxs-lookup"><span data-stu-id="80b80-142">For situations where the usage of `ConfigureAwait` is not needed, the `await using` statement could be simplified as follows:</span></span>

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/await-using-non-configureawait.cs":::

<span data-ttu-id="80b80-143">En outre, il peut être écrit pour utiliser l’étendue implicite d’une [déclaration using](../../csharp/whats-new/csharp-8.md#using-declarations).</span><span class="sxs-lookup"><span data-stu-id="80b80-143">Furthermore, it could be written to use the implicit scoping of a [using declaration](../../csharp/whats-new/csharp-8.md#using-declarations).</span></span>

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/await-using-declaration.cs":::

## <a name="stacked-usings"></a><span data-ttu-id="80b80-144">Utilisation empilée</span><span class="sxs-lookup"><span data-stu-id="80b80-144">Stacked usings</span></span>

<span data-ttu-id="80b80-145">Dans les situations où vous créez et utilisez plusieurs objets qui implémentent <xref:System.IAsyncDisposable> , il est possible que l’empilement `using` des instructions dans des conditions errantes puisse empêcher les appels à <xref:System.IAsyncDisposable.DisposeAsync> .</span><span class="sxs-lookup"><span data-stu-id="80b80-145">In situations where you create and use multiple objects that implement <xref:System.IAsyncDisposable>, it's possible that stacking `using` statements in errant conditions could prevent calls to <xref:System.IAsyncDisposable.DisposeAsync>.</span></span> <span data-ttu-id="80b80-146">Afin d’éviter tout problème potentiel, vous devez éviter l’empilement, et suivez plutôt le modèle d’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="80b80-146">In order to help prevent potential concern, you should avoid stacking, and instead follow this example pattern:</span></span>

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/stacked-await-usings.cs":::

## <a name="see-also"></a><span data-ttu-id="80b80-147">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="80b80-147">See also</span></span>

- <xref:System.IAsyncDisposable>
- <xref:System.IAsyncDisposable.DisposeAsync?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait(System.IAsyncDisposable,System.Boolean)>
