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
# <a name="lazy-expressions"></a><span data-ttu-id="0eaaa-103">Expressions différées</span><span class="sxs-lookup"><span data-stu-id="0eaaa-103">Lazy Expressions</span></span>

<span data-ttu-id="0eaaa-104">Les *expressions tardives* sont des expressions qui ne sont pas évaluées immédiatement, mais qui sont évaluées à la place lorsque le résultat est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="0eaaa-104">*Lazy expressions* are expressions that are not evaluated immediately, but are instead evaluated when the result is needed.</span></span> <span data-ttu-id="0eaaa-105">Cela peut contribuer à améliorer les performances de votre code.</span><span class="sxs-lookup"><span data-stu-id="0eaaa-105">This can help to improve the performance of your code.</span></span>

## <a name="syntax"></a><span data-ttu-id="0eaaa-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0eaaa-106">Syntax</span></span>

```fsharp
let identifier = lazy ( expression )
```

## <a name="remarks"></a><span data-ttu-id="0eaaa-107">Notes</span><span class="sxs-lookup"><span data-stu-id="0eaaa-107">Remarks</span></span>

<span data-ttu-id="0eaaa-108">Dans la syntaxe précédente, l' *expression* est du code qui est évalué uniquement lorsqu’un résultat est requis, et l' *identificateur* est une valeur qui stocke le résultat.</span><span class="sxs-lookup"><span data-stu-id="0eaaa-108">In the previous syntax, *expression* is code that is evaluated only when a result is required, and *identifier* is a value that stores the result.</span></span> <span data-ttu-id="0eaaa-109">La valeur est de type [`Lazy<'T>`](https://msdn.microsoft.com/library/b29d0af5-6efb-4a55-a278-2662a4ecc489), où le type réel utilisé pour `'T` est déterminé à partir du résultat de l’expression.</span><span class="sxs-lookup"><span data-stu-id="0eaaa-109">The value is of type [`Lazy<'T>`](https://msdn.microsoft.com/library/b29d0af5-6efb-4a55-a278-2662a4ecc489), where the actual type that is used for `'T` is determined from the result of the expression.</span></span>

<span data-ttu-id="0eaaa-110">Les expressions tardives vous permettent d’améliorer les performances en restreignant l’exécution d’une expression à des situations dans lesquelles un résultat est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="0eaaa-110">Lazy expressions enable you to improve performance by restricting the execution of an expressions to only those situations in which a result is needed.</span></span>

<span data-ttu-id="0eaaa-111">Pour forcer l’exécution des expressions, vous appelez la méthode `Force`.</span><span class="sxs-lookup"><span data-stu-id="0eaaa-111">To force the expressions to be performed, you call the method `Force`.</span></span> <span data-ttu-id="0eaaa-112">`Force`entraîne l’exécution d’une seule opération.</span><span class="sxs-lookup"><span data-stu-id="0eaaa-112">`Force` causes the execution to be performed only one time.</span></span> <span data-ttu-id="0eaaa-113">Les appels suivants `Force` pour retourner le même résultat, mais n’exécutent pas de code.</span><span class="sxs-lookup"><span data-stu-id="0eaaa-113">Subsequent calls to `Force` return the same result, but do not execute any code.</span></span>

<span data-ttu-id="0eaaa-114">Le code suivant illustre l’utilisation d’expressions tardives et l’utilisation de `Force`.</span><span class="sxs-lookup"><span data-stu-id="0eaaa-114">The following code illustrates the use of lazy expressions and the use of `Force`.</span></span> <span data-ttu-id="0eaaa-115">Dans ce code, le type de `result` est `Lazy<int>`, et la `Force` méthode retourne un `int`.</span><span class="sxs-lookup"><span data-stu-id="0eaaa-115">In this code, the type of `result` is `Lazy<int>`, and the `Force` method returns an `int`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet73011.fs)]

<span data-ttu-id="0eaaa-116">L’évaluation différée, mais `Lazy` pas le type, est également utilisée pour les séquences.</span><span class="sxs-lookup"><span data-stu-id="0eaaa-116">Lazy evaluation, but not the `Lazy` type, is also used for sequences.</span></span> <span data-ttu-id="0eaaa-117">Pour plus d’informations, consultez [séquences](sequences.md).</span><span class="sxs-lookup"><span data-stu-id="0eaaa-117">For more information, see [Sequences](sequences.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0eaaa-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0eaaa-118">See also</span></span>

- [<span data-ttu-id="0eaaa-119">Informations de référence du langage F#</span><span class="sxs-lookup"><span data-stu-id="0eaaa-119">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="0eaaa-120">Module LazyExtensions</span><span class="sxs-lookup"><span data-stu-id="0eaaa-120">LazyExtensions module</span></span>](https://msdn.microsoft.com/library/86671f40-84a0-402a-867d-ae596218d948)
