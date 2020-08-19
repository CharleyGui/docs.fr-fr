---
title: Implémenter une méthode DisposeAsync
description: ''
author: IEvangelist
ms.author: dapine
ms.date: 06/02/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
helpviewer_keywords:
- DisposeAsync method
- garbage collection, DisposeAsync method
ms.openlocfilehash: 0f6370d37703509681dd9fb818af8e7e2f3a1085
ms.sourcegitcommit: cbb19e56d48cf88375d35d0c27554d4722761e0d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/19/2020
ms.locfileid: "88608080"
---
# <a name="implement-a-disposeasync-method"></a>Implémenter une méthode DisposeAsync

L' <xref:System.IAsyncDisposable?displayProperty=nameWithType> interface a été introduite dans le cadre de C# 8,0. Vous implémentez la <xref:System.IAsyncDisposable.DisposeAsync?displayProperty=nameWithType> méthode lorsque vous devez effectuer un nettoyage des ressources, comme vous le feriez lors de l' [implémentation d’une méthode dispose](implementing-dispose.md). Toutefois, l’une des principales différences est que cette implémentation autorise les opérations de nettoyage asynchrones. <xref:System.IAsyncDisposable.DisposeAsync>Retourne un <xref:System.Threading.Tasks.ValueTask> qui représente l’opération de suppression asynchrone.

Lors de l’implémentation de l' <xref:System.IAsyncDisposable> interface, les classes implémentent également l' <xref:System.IDisposable> interface. Un modèle d’implémentation correct de l' <xref:System.IAsyncDisposable> interface doit être préparé pour une suppression synchrone ou asynchrone. Toutes les instructions pour l’implémentation du modèle de suppression s’appliquent à l’implémentation asynchrone. Cet article suppose que vous êtes déjà familiarisé avec l’implémentation d' [une méthode dispose](implementing-dispose.md).

## <a name="disposeasync-and-disposeasynccore"></a>DisposeAsync () et DisposeAsyncCore ()

L' <xref:System.IAsyncDisposable> interface déclare une méthode sans paramètre unique, <xref:System.IAsyncDisposable.DisposeAsync> . Toute classe non scellée doit avoir une `DisposeAsyncCore()` méthode supplémentaire qui retourne également un <xref:System.Threading.Tasks.ValueTask> .

- `public` <xref:System.IAsyncDisposable.DisposeAsync?displayProperty=nameWithType> Implémentation qui n’a aucun paramètre.
- Une `protected virtual ValueTask DisposeAsyncCore()` méthode dont la signature est :

```csharp
protected virtual ValueTask DisposeAsyncCore()
{
}
```

La `DisposeAsyncCore()` méthode `virtual` permet aux classes dérivées de définir un nettoyage supplémentaire dans leurs substitutions.

### <a name="the-disposeasync-method"></a>Méthode DisposeAsync ()

La `public` méthode sans paramètre `DisposeAsync()` est appelée implicitement dans une `await using` instruction, et son objectif est de libérer des ressources non managées, d’effectuer un nettoyage général et d’indiquer que le finaliseur, le cas échéant, doit être exécuté. La libération de la mémoire associée à un objet géré est toujours le domaine du [garbage collector](index.md). De ce fait, son implémentation standard est la suivante :

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
> L’une des principales différences dans le modèle de suppression asynchrone par rapport au modèle de suppression est que l’appel de <xref:System.IAsyncDisposable.DisposeAsync> à la `Dispose(bool)` méthode de surcharge est donné `false` comme argument. Toutefois, lors de l’implémentation de la <xref:System.IDisposable.Dispose?displayProperty=nameWithType> méthode, `true` est passé. Cela permet de garantir l’équivalence fonctionnelle avec le modèle de suppression synchrone et de s’assurer que les chemins de code du finaliseur sont toujours appelés. En d’autres termes, la `DisposeAsyncCore()` méthode supprime les ressources managées de manière asynchrone, donc vous ne voulez pas les supprimer de manière synchrone. Par conséquent, appelez `Dispose(false)` au lieu de `Dispose(true)` .

## <a name="implement-the-async-dispose-pattern"></a>Implémenter le modèle de suppression asynchrone

Toutes les classes non-sealed doivent être considérées comme une classe de base potentielle, car elles peuvent être héritées. Si vous implémentez le modèle de suppression Async pour une classe de base potentielle quelconque, vous devez fournir la `protected virtual ValueTask DisposeAsyncCore()` méthode. Voici un exemple d’implémentation du modèle asynchrone dispose qui utilise un <xref:System.Text.Json.Utf8JsonWriter?displayProperty=nameWithType> .

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/disposeasync.cs":::

L’exemple précédent utilise <xref:System.Text.Json.Utf8JsonWriter> . Pour plus d’informations sur `System.Text.Json` , voir [How to migrate from Newtonsoft.Json to System.Text.Json](../serialization/system-text-json-migrate-from-newtonsoft-how-to.md).

## <a name="using-async-disposable"></a>Utilisation de Async jetable

Pour utiliser correctement un objet qui implémente l' <xref:System.IAsyncDisposable> interface, vous utilisez l' [expression await](../../csharp/language-reference/operators/await.md)et les mots clés [en](../../csharp/language-reference/keywords/using-statement.md) même temps. Prenons l’exemple suivant, où la `ExampleAsyncDisposable` classe est instanciée puis encapsulée dans une `await using` instruction.

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/proper-await-using.cs":::

> [!IMPORTANT]
> Utilisez la <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait(System.IAsyncDisposable,System.Boolean)> méthode d’extension de l' <xref:System.IAsyncDisposable> interface pour configurer la façon dont la continuation de la tâche est marshalée sur son contexte ou planificateur d’origine. Pour plus d’informations sur `ConfigureAwait` , consultez le [Forum aux questions ConfigureAwait](https://devblogs.microsoft.com/dotnet/configureawait-faq/).

Dans les situations où l’utilisation de `ConfigureAwait` n’est pas nécessaire, l' `await using` instruction peut être simplifiée comme suit :

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/await-using-non-configureawait.cs":::

En outre, il peut être écrit pour utiliser l’étendue implicite d’une [déclaration using](../../csharp/whats-new/csharp-8.md#using-declarations).

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/await-using-declaration.cs":::

## <a name="stacked-usings"></a>Utilisation empilée

Dans les situations où vous créez et utilisez plusieurs objets qui implémentent <xref:System.IAsyncDisposable> , il est possible que l’empilement `using` des instructions dans des conditions errantes puisse empêcher les appels à <xref:System.IAsyncDisposable.DisposeAsync> . Afin d’éviter tout problème potentiel, vous devez éviter l’empilement, et suivez plutôt le modèle d’exemple suivant :

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/stacked-await-usings.cs":::

## <a name="see-also"></a>Voir aussi

- <xref:System.IAsyncDisposable>
- <xref:System.IAsyncDisposable.DisposeAsync?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait(System.IAsyncDisposable,System.Boolean)>
