---
title: Expressions différées
description: Découvrez comment F# les expressions tardives peuvent améliorer les performances de vos applications et bibliothèques.
ms.date: 03/13/2019
ms.openlocfilehash: 97429e9a4c3838cbaa2ead197db4443e0820e8b3
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630740"
---
# <a name="lazy-expressions"></a>Expressions différées

Les *expressions tardives* sont des expressions qui ne sont pas évaluées immédiatement, mais qui sont évaluées à la place lorsque le résultat est nécessaire. Cela peut contribuer à améliorer les performances de votre code.

## <a name="syntax"></a>Syntaxe

```fsharp
let identifier = lazy ( expression )
```

## <a name="remarks"></a>Notes

Dans la syntaxe précédente, l' *expression* est du code qui est évalué uniquement lorsqu’un résultat est requis, et l' *identificateur* est une valeur qui stocke le résultat. La valeur est de type [`Lazy<'T>`](https://msdn.microsoft.com/library/b29d0af5-6efb-4a55-a278-2662a4ecc489), où le type réel utilisé pour `'T` est déterminé à partir du résultat de l’expression.

Les expressions tardives vous permettent d’améliorer les performances en restreignant l’exécution d’une expression à des situations dans lesquelles un résultat est nécessaire.

Pour forcer l’exécution des expressions, vous appelez la méthode `Force`. `Force`entraîne l’exécution d’une seule opération. Les appels suivants `Force` pour retourner le même résultat, mais n’exécutent pas de code.

Le code suivant illustre l’utilisation d’expressions tardives et l’utilisation de `Force`. Dans ce code, le type de `result` est `Lazy<int>`, et la `Force` méthode retourne un `int`.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet73011.fs)]

L’évaluation différée, mais `Lazy` pas le type, est également utilisée pour les séquences. Pour plus d’informations, consultez [séquences](sequences.md).

## <a name="see-also"></a>Voir aussi

- [Informations de référence du langage F#](index.md)
- [Module LazyExtensions](https://msdn.microsoft.com/library/86671f40-84a0-402a-867d-ae596218d948)
