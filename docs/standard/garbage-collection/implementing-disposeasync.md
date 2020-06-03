---
title: Implémenter une méthode DisposeAsync
description: ''
ms.date: 06/02/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
helpviewer_keywords:
- DisposeAsync method
- garbage collection, DisposeAsync method
ms.openlocfilehash: c4f541d5a4f5b5fd31b344a299789d86cd78424c
ms.sourcegitcommit: 5280b2aef60a1ed99002dba44e4b9e7f6c830604
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/03/2020
ms.locfileid: "84311013"
---
# <a name="implement-a-disposeasync-method"></a><span data-ttu-id="e180f-102">Implémenter une méthode DisposeAsync</span><span class="sxs-lookup"><span data-stu-id="e180f-102">Implement a DisposeAsync method</span></span>

<span data-ttu-id="e180f-103">L' <xref:System.IAsyncDisposable?displayProperty=nameWithType> interface a été introduite dans le cadre de C# 8,0.</span><span class="sxs-lookup"><span data-stu-id="e180f-103">The <xref:System.IAsyncDisposable?displayProperty=nameWithType> interface was introduced as part of C# 8.0.</span></span> <span data-ttu-id="e180f-104">Vous implémentez la <xref:System.IAsyncDisposable.DisposeAsync?displayProperty=nameWithType> méthode lorsque vous devez effectuer un nettoyage des ressources, comme vous le feriez lors de l' [implémentation d’une méthode dispose](implementing-dispose.md).</span><span class="sxs-lookup"><span data-stu-id="e180f-104">You implement the <xref:System.IAsyncDisposable.DisposeAsync?displayProperty=nameWithType> method when you need to perform resource cleanup, just as you would when [implementing a Dispose method](implementing-dispose.md).</span></span> <span data-ttu-id="e180f-105">Toutefois, l’une des principales différences est que cette implémentation autorise les opérations de nettoyage asynchrones.</span><span class="sxs-lookup"><span data-stu-id="e180f-105">One of the key differences however, is that this implementation allows for asynchronous cleanup operations.</span></span> <span data-ttu-id="e180f-106"><xref:System.IAsyncDisposable.DisposeAsync>Retourne un <xref:System.Threading.Tasks.ValueTask> qui représente l’opération de suppression asynchrone.</span><span class="sxs-lookup"><span data-stu-id="e180f-106">The <xref:System.IAsyncDisposable.DisposeAsync> returns a <xref:System.Threading.Tasks.ValueTask> that represents the asynchronous dispose operation.</span></span>

<span data-ttu-id="e180f-107">Lors de l’implémentation de l' <xref:System.IAsyncDisposable> interface, les classes implémentent également l' <xref:System.IDisposable> interface.</span><span class="sxs-lookup"><span data-stu-id="e180f-107">It is typical that when implementing the <xref:System.IAsyncDisposable> interface, classes will also implement the <xref:System.IDisposable> interface.</span></span> <span data-ttu-id="e180f-108">Un modèle d’implémentation correct de l' <xref:System.IAsyncDisposable> interface doit être préparé pour une suppression synchrone ou asynchrone.</span><span class="sxs-lookup"><span data-stu-id="e180f-108">A good implementation pattern of the <xref:System.IAsyncDisposable> interface is to be prepared for either synchronous, or asynchronous dispose.</span></span> <span data-ttu-id="e180f-109">Toutes les instructions pour l’implémentation du modèle de suppression s’appliquent à l’implémentation asynchrone.</span><span class="sxs-lookup"><span data-stu-id="e180f-109">All of the guidance for implementing the dispose pattern applies to the asynchronous implementation.</span></span> <span data-ttu-id="e180f-110">Cet article suppose que vous êtes déjà familiarisé avec l’implémentation d' [une méthode dispose](implementing-dispose.md).</span><span class="sxs-lookup"><span data-stu-id="e180f-110">This article assumes that you're already familiar with how to [implement a Dispose method](implementing-dispose.md).</span></span>

## <a name="disposeasync-and-disposeasynccore"></a><span data-ttu-id="e180f-111">DisposeAsync () et DisposeAsyncCore ()</span><span class="sxs-lookup"><span data-stu-id="e180f-111">DisposeAsync() and DisposeAsyncCore()</span></span>

<span data-ttu-id="e180f-112">L' <xref:System.IAsyncDisposable> interface déclare une méthode sans paramètre unique, <xref:System.IAsyncDisposable.DisposeAsync> .</span><span class="sxs-lookup"><span data-stu-id="e180f-112">The <xref:System.IAsyncDisposable> interface declares a single parameterless method, <xref:System.IAsyncDisposable.DisposeAsync>.</span></span> <span data-ttu-id="e180f-113">Toute classe non scellée doit avoir une `DisposeAsyncCore()` méthode supplémentaire qui retourne également un <xref:System.Threading.Tasks.ValueTask> .</span><span class="sxs-lookup"><span data-stu-id="e180f-113">Any non-sealed class should have an additional `DisposeAsyncCore()` method that also returns a <xref:System.Threading.Tasks.ValueTask>.</span></span>

- <span data-ttu-id="e180f-114">`public` <xref:System.IAsyncDisposable.DisposeAsync?displayProperty=nameWithType> Implémentation qui n’a aucun paramètre.</span><span class="sxs-lookup"><span data-stu-id="e180f-114">A `public` <xref:System.IAsyncDisposable.DisposeAsync?displayProperty=nameWithType> implementation that has no parameters.</span></span>
- <span data-ttu-id="e180f-115">Une `protected virtual ValueTask DisposeAsyncCore()` méthode dont la signature est :</span><span class="sxs-lookup"><span data-stu-id="e180f-115">A `protected virtual ValueTask DisposeAsyncCore()` method whose signature is:</span></span>

```csharp
protected virtual ValueTask DisposeAsyncCore()
{
}
```

<span data-ttu-id="e180f-116">La `DisposeAsyncCore()` méthode `virtual` permet aux classes dérivées de définir un nettoyage supplémentaire dans leurs substitutions.</span><span class="sxs-lookup"><span data-stu-id="e180f-116">The `DisposeAsyncCore()` method is `virtual` so that derived classes can define additional cleanup in their overrides.</span></span>

### <a name="the-disposeasync-method"></a><span data-ttu-id="e180f-117">Méthode DisposeAsync ()</span><span class="sxs-lookup"><span data-stu-id="e180f-117">The DisposeAsync() method</span></span>

<span data-ttu-id="e180f-118">La `public` méthode sans paramètre `DisposeAsync()` est appelée implicitement dans une `await using` instruction, et son objectif est de libérer des ressources non managées, d’effectuer un nettoyage général et d’indiquer que le finaliseur, le cas échéant, doit être exécuté.</span><span class="sxs-lookup"><span data-stu-id="e180f-118">The `public` parameterless `DisposeAsync()` method is called implicitly in an `await using` statement, and its purpose is to free unmanaged resources, perform general cleanup, and to indicate that the finalizer, if one is present, needn't run.</span></span> <span data-ttu-id="e180f-119">La libération de la mémoire associée à un objet géré est toujours le domaine du [garbage collector](index.md).</span><span class="sxs-lookup"><span data-stu-id="e180f-119">Freeing the memory associated with a managed object is always the domain of the [garbage collector](index.md).</span></span> <span data-ttu-id="e180f-120">De ce fait, son implémentation standard est la suivante :</span><span class="sxs-lookup"><span data-stu-id="e180f-120">Because of this, it has a standard implementation:</span></span>

```csharp
public async ValueTask DisposeAsync()
{
    // Perform async cleanup.
    await DisposeAsyncCore();

    // Dispose of managed resources.
    Dispose(false);
    // Suppress finalization.
    GC.SuppressFinalize(this);
}
```

> [!NOTE]
> <span data-ttu-id="e180f-121">L’une des principales différences dans le modèle de suppression asynchrone par rapport au modèle de suppression est que l’appel de <xref:System.IAsyncDisposable.DisposeAsync> à la `Dispose(bool)` méthode de surcharge est donné `false` comme argument.</span><span class="sxs-lookup"><span data-stu-id="e180f-121">One primary difference in the async dispose pattern compared to the dispose pattern, is that the call from <xref:System.IAsyncDisposable.DisposeAsync> to the `Dispose(bool)` overload method is given `false` as an argument.</span></span> <span data-ttu-id="e180f-122">Toutefois, lors de l’implémentation de la <xref:System.IDisposable.Dispose?displayProperty=nameWithType> méthode, `true` est passé.</span><span class="sxs-lookup"><span data-stu-id="e180f-122">When implementing the <xref:System.IDisposable.Dispose?displayProperty=nameWithType> method, however; `true` is passed instead.</span></span> <span data-ttu-id="e180f-123">Cela permet de garantir l’équivalence fonctionnelle avec le modèle de suppression synchrone et de s’assurer que les chemins de code du finaliseur sont toujours appelés.</span><span class="sxs-lookup"><span data-stu-id="e180f-123">This helps ensure functional equivalence with the synchronous dispose pattern, and further ensures that finalizer code paths still get invoked.</span></span> <span data-ttu-id="e180f-124">En d’autres termes, la `DisposeAsyncCore()` méthode supprime les ressources managées de manière asynchrone, donc vous ne voulez pas les supprimer de manière synchrone.</span><span class="sxs-lookup"><span data-stu-id="e180f-124">In other words, the `DisposeAsyncCore()` method will dispose of managed resources asynchronously, so you don't want to dispose of them synchronously as well.</span></span> <span data-ttu-id="e180f-125">Par conséquent, appelez `Dispose(false)` au lieu de `Dispose(true)` .</span><span class="sxs-lookup"><span data-stu-id="e180f-125">Therefore, call `Dispose(false)` instead of `Dispose(true)`.</span></span>

## <a name="implement-the-async-dispose-pattern"></a><span data-ttu-id="e180f-126">Implémenter le modèle de suppression asynchrone</span><span class="sxs-lookup"><span data-stu-id="e180f-126">Implement the async dispose pattern</span></span>

<span data-ttu-id="e180f-127">Toutes les classes non-sealed doivent être considérées comme une classe de base potentielle, car elles peuvent être héritées.</span><span class="sxs-lookup"><span data-stu-id="e180f-127">All non-sealed classes should be considered a potential base class, because they could be inherited.</span></span> <span data-ttu-id="e180f-128">Si vous implémentez le modèle de suppression Async pour une classe de base potentielle quelconque, vous devez fournir la `protected virtual ValueTask DisposeAsyncCore()` méthode.</span><span class="sxs-lookup"><span data-stu-id="e180f-128">If you implement the async dispose pattern for any potential base class, you must provide the `protected virtual ValueTask DisposeAsyncCore()` method.</span></span> <span data-ttu-id="e180f-129">Voici un exemple d’implémentation du modèle asynchrone dispose qui utilise un <xref:System.Text.Json.Utf8JsonWriter?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="e180f-129">Here is an example implementation of the async dispose pattern that uses a <xref:System.Text.Json.Utf8JsonWriter?displayProperty=nameWithType>.</span></span>

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/disposeasync.cs":::

<span data-ttu-id="e180f-130">L’exemple précédent utilisait <xref:System.Text.Json.Utf8JsonWriter> , pour plus d’informations sur `System.Text.Json` , consultez [migrer de Newtonsoft. JSON vers System. Text. JSON](../serialization/system-text-json-migrate-from-newtonsoft-how-to.md).</span><span class="sxs-lookup"><span data-stu-id="e180f-130">The previous example used the <xref:System.Text.Json.Utf8JsonWriter>, for more information on `System.Text.Json`, see, [migrate from Newtonsoft.Json to System.Text.Json](../serialization/system-text-json-migrate-from-newtonsoft-how-to.md).</span></span>

## <a name="using-async-disposable"></a><span data-ttu-id="e180f-131">Utilisation de Async jetable</span><span class="sxs-lookup"><span data-stu-id="e180f-131">Using async disposable</span></span>

<span data-ttu-id="e180f-132">Pour utiliser correctement un objet qui implémente l' <xref:System.IAsyncDisposable> interface, vous utilisez l' [expression await](../../csharp/language-reference/operators/await.md)et les mots clés [en](../../csharp/language-reference/keywords/using.md) même temps.</span><span class="sxs-lookup"><span data-stu-id="e180f-132">To properly consume an object that implements the <xref:System.IAsyncDisposable> interface, you use the [await](../../csharp/language-reference/operators/await.md), and [using](../../csharp/language-reference/keywords/using.md) keywords together.</span></span> <span data-ttu-id="e180f-133">Prenons l’exemple suivant, dans lequel la `ExampleAsyncDisposable` classe est instanciée, puis incluse dans un wrapper dans une `await using` instruction.</span><span class="sxs-lookup"><span data-stu-id="e180f-133">Consider the following example, where the `ExampleAsyncDisposable` class is instantiated, then wrapped in an `await using` statement.</span></span>

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/proper-await-using.cs":::

> [!IMPORTANT]
> <span data-ttu-id="e180f-134">Utilisez la <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait(System.IAsyncDisposable,System.Boolean)> méthode d’extension de l' <xref:System.IAsyncDisposable> interface pour configurer la façon dont la continuation de la tâche est marshalée sur son contexte ou planificateur d’origine.</span><span class="sxs-lookup"><span data-stu-id="e180f-134">Use the <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait(System.IAsyncDisposable,System.Boolean)> extension method of the <xref:System.IAsyncDisposable> interface to configure how the continuation of the task is marshalled on its original context or scheduler.</span></span> <span data-ttu-id="e180f-135">Pour plus d’informations sur `ConfigureAwait` , consultez le [Forum aux questions ConfigureAwait](https://devblogs.microsoft.com/dotnet/configureawait-faq/).</span><span class="sxs-lookup"><span data-stu-id="e180f-135">For more information on `ConfigureAwait`, see [ConfigureAwait FAQ](https://devblogs.microsoft.com/dotnet/configureawait-faq/).</span></span>

<span data-ttu-id="e180f-136">Dans les situations où l’utilisation de `ConfigureAwait` n’est pas nécessaire, l' `await using` instruction peut être simplifiée comme suit :</span><span class="sxs-lookup"><span data-stu-id="e180f-136">For situations where the usage of `ConfigureAwait` is not needed, the `await using` statement could be simplified as follows:</span></span>

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/await-using-non-configureawait.cs":::

<span data-ttu-id="e180f-137">En outre, il peut être écrit pour utiliser l’étendue implicite d’une [déclaration using](../../csharp/whats-new/csharp-8.md#using-declarations).</span><span class="sxs-lookup"><span data-stu-id="e180f-137">Furthermore, it could be written to use the implicit scoping of a [using declaration](../../csharp/whats-new/csharp-8.md#using-declarations).</span></span>

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/await-using-declaration.cs":::

## <a name="stacked-usings"></a><span data-ttu-id="e180f-138">Utilisation empilée</span><span class="sxs-lookup"><span data-stu-id="e180f-138">Stacked usings</span></span>

<span data-ttu-id="e180f-139">Dans les situations où vous créez et utilisez plusieurs objets qui implémentent <xref:System.IAsyncDisposable> , il est possible que l’empilement `using` des instructions dans des conditions errantes puisse empêcher les appels à <xref:System.IAsyncDisposable.DisposeAsync> .</span><span class="sxs-lookup"><span data-stu-id="e180f-139">In situations where you create and use multiple objects that implement <xref:System.IAsyncDisposable>, it's possible that stacking `using` statements in errant conditions could prevent calls to <xref:System.IAsyncDisposable.DisposeAsync>.</span></span> <span data-ttu-id="e180f-140">Afin d’éviter tout problème potentiel, vous devez éviter l’empilement, et suivez plutôt le modèle d’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="e180f-140">In order to help prevent potential concern, you should avoid stacking, and instead follow this example pattern:</span></span>

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/stacked-await-usings.cs":::

## <a name="see-also"></a><span data-ttu-id="e180f-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e180f-141">See also</span></span>

- <xref:System.IAsyncDisposable>
- <xref:System.IAsyncDisposable.DisposeAsync?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait(System.IAsyncDisposable,System.Boolean)>
