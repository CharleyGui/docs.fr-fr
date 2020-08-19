---
title: Expressions différées
description: 'Découvrez comment les expressions tardives F # peuvent améliorer les performances de vos applications et bibliothèques.'
ms.date: 08/15/2020
ms.openlocfilehash: 71c466ca3b74c9e92b81a3c268e07438ec944905
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/18/2020
ms.locfileid: "88558086"
---
# <a name="lazy-expressions"></a>Expressions différées

Les *expressions tardives* sont des expressions qui ne sont pas évaluées immédiatement, mais qui sont évaluées à la place lorsque le résultat est nécessaire. Cela peut contribuer à améliorer les performances de votre code.

## <a name="syntax"></a>Syntaxe

```fsharp
let identifier = lazy ( expression )
```

## <a name="remarks"></a>Notes

Dans la syntaxe précédente, l' *expression* est du code qui est évalué uniquement lorsqu’un résultat est requis, et l' *identificateur* est une valeur qui stocke le résultat. La valeur est de type [`Lazy<'T>`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-lazy-1-0.html) , où le type réel utilisé pour `'T` est déterminé à partir du résultat de l’expression.

Les expressions tardives vous permettent d’améliorer les performances en restreignant l’exécution d’une expression à des situations dans lesquelles un résultat est nécessaire.

Pour forcer l’exécution des expressions, vous appelez la méthode `Force` . `Force` entraîne l’exécution d’une seule opération. Les appels suivants pour `Force` retourner le même résultat, mais n’exécutent pas de code.

Le code suivant illustre l’utilisation d’expressions tardives et l’utilisation de `Force` . Dans ce code, le type de `result` est `Lazy<int>` , et la `Force` méthode retourne un `int` .

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet73011.fs)]

L’évaluation différée, mais pas le `Lazy` type, est également utilisée pour les séquences. Pour plus d’informations, consultez [séquences](sequences.md).

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur le langage F #](index.md)
- [Module LazyExtensions](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-lazyextensions.html)
