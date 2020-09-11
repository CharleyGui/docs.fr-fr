---
title: Implémenter une méthode DisposeAsync
description: Découvrez comment implémenter des méthodes DisposeAsync et DisposeAsyncCore pour effectuer un nettoyage asynchrone des ressources.
author: IEvangelist
ms.author: dapine
ms.date: 09/10/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
helpviewer_keywords:
- DisposeAsync method
- garbage collection, DisposeAsync method
ms.openlocfilehash: 88adf9e484baa0e65e2ff093b4649cf35b8c86dc
ms.sourcegitcommit: 6d4ee46871deb9ea1e45bb5f3784474e240bbc26
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/11/2020
ms.locfileid: "90022907"
---
# <a name="implement-a-disposeasync-method"></a>Implémenter une méthode DisposeAsync

L' <xref:System.IAsyncDisposable?displayProperty=nameWithType> interface a été introduite dans le cadre de C# 8,0. Vous implémentez la <xref:System.IAsyncDisposable.DisposeAsync?displayProperty=nameWithType> méthode lorsque vous devez effectuer un nettoyage des ressources, comme vous le feriez lors de l' [implémentation d’une méthode dispose](implementing-dispose.md). Toutefois, l’une des principales différences est que cette implémentation autorise les opérations de nettoyage asynchrones. <xref:System.IAsyncDisposable.DisposeAsync>Retourne un <xref:System.Threading.Tasks.ValueTask> qui représente l’opération de suppression asynchrone.

C’est généralement le cas lors de l’implémentation de l' <xref:System.IAsyncDisposable> interface que les classes implémentent également l' <xref:System.IDisposable> interface. Un modèle d’implémentation correct de l' <xref:System.IAsyncDisposable> interface doit être préparé pour une suppression synchrone ou asynchrone. Toutes les instructions pour l’implémentation du modèle de suppression s’appliquent également à l’implémentation asynchrone. Cet article suppose que vous êtes déjà familiarisé avec l’implémentation d' [une méthode dispose](implementing-dispose.md).

## <a name="disposeasync-and-disposeasynccore"></a>DisposeAsync () et DisposeAsyncCore ()

L' <xref:System.IAsyncDisposable> interface déclare une méthode sans paramètre unique, <xref:System.IAsyncDisposable.DisposeAsync> . Toute classe non scellée doit avoir une `DisposeAsyncCore()` méthode supplémentaire qui retourne également un <xref:System.Threading.Tasks.ValueTask> .

- `public` <xref:System.IAsyncDisposable.DisposeAsync?displayProperty=nameWithType> Implémentation qui n’a aucun paramètre.
- Une `protected virtual ValueTask DisposeAsyncCore()` méthode dont la signature est :

  ```csharp
  protected virtual ValueTask DisposeAsyncCore()
  {
  }
  ```

### <a name="the-disposeasync-method"></a>Méthode DisposeAsync ()

La `public` méthode sans paramètre `DisposeAsync()` est appelée implicitement dans une `await using` instruction, et son objectif est de libérer des ressources non managées, d’effectuer un nettoyage général et d’indiquer que le finaliseur, s’il en existe un, ne doit pas être exécuté. La libération de la mémoire associée à un objet géré est toujours le domaine du [garbage collector](index.md). De ce fait, son implémentation standard est la suivante :

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

### <a name="the-disposeasynccore-method"></a>Méthode DisposeAsyncCore ()

La `DisposeAsyncCore()` méthode est conçue pour effectuer le nettoyage asynchrone des ressources managées ou pour les appels en cascade à `DisposeAsync()` . Il encapsule les opérations de nettoyage asynchrone courantes lorsqu’une sous-classe hérite d’une classe de base qui est une implémentation de <xref:System.IAsyncDisposable> . La `DisposeAsyncCore()` méthode `virtual` permet aux classes dérivées de définir un nettoyage supplémentaire dans leurs substitutions.

> [!TIP]
> Si une implémentation de <xref:System.IAsyncDisposable> est `sealed` , la `DisposeAsyncCore()` méthode n’est pas nécessaire et le nettoyage asynchrone peut être effectué directement dans la <xref:System.IAsyncDisposable.DisposeAsync?displayProperty=nameWithType> méthode.

## <a name="implement-the-async-dispose-pattern"></a>Implémenter le modèle de suppression asynchrone

Toutes les classes non-sealed doivent être considérées comme une classe de base potentielle, car elles peuvent être héritées. Si vous implémentez le modèle de suppression Async pour une classe de base potentielle quelconque, vous devez fournir la `protected virtual ValueTask DisposeAsyncCore()` méthode. Voici un exemple d’implémentation du modèle asynchrone dispose qui utilise un <xref:System.Text.Json.Utf8JsonWriter?displayProperty=nameWithType> .

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/disposeasync.cs":::

L’exemple précédent utilise <xref:System.Text.Json.Utf8JsonWriter> . Pour plus d’informations sur `System.Text.Json` , voir [How to migrate from Newtonsoft.Json to System.Text.Json](../serialization/system-text-json-migrate-from-newtonsoft-how-to.md).

## <a name="implement-both-dispose-and-async-dispose-patterns"></a>Implémenter à la fois les modèles dispose et Async

Vous devrez peut-être implémenter à la fois les <xref:System.IDisposable> <xref:System.IAsyncDisposable> interfaces et, en particulier lorsque votre portée de classe contient des instances de ces implémentations. Cela vous permet de vous assurer que vous pouvez nettoyer correctement les appels en cascade. Voici un exemple de classe qui implémente les deux interfaces et montre les recommandations appropriées pour le nettoyage.

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/dispose-and-disposeasync.cs":::

Les <xref:System.IDisposable.Dispose?displayProperty=nameWithType> <xref:System.IAsyncDisposable.DisposeAsync?displayProperty=nameWithType> implémentations et sont à la fois du code réutilisable simple. Les `Dispose(bool)` `DisposeAsyncCore()` méthodes et commencent par vérifier si `_disposed` est `true` et s’exécutent uniquement quand elle est `false` .

Dans la `Dispose(bool)` méthode de surcharge, l' <xref:System.IDisposable> instance est supprimée de manière conditionnelle, si ce n’est pas le cas `null` . L' <xref:System.IAsyncDisposable> instance est castée en tant que <xref:System.IDisposable> , et si elle ne l’est pas non plus, elle est également `null` supprimée. Les deux instances sont ensuite affectées à `null` .

Avec la `DisposeAsyncCore()` méthode, la même approche logique est suivie. Si l' <xref:System.IAsyncDisposable> instance n’est pas `null` , son appel à `DisposeAsync().ConfigureAwait(false)` est attendu. Si l' <xref:System.IDisposable> instance est également une implémentation de <xref:System.IAsyncDisposable> , elle est également supprimée de manière asynchrone. Les deux instances sont ensuite affectées à `null` .

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
