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
# <a name="lazy-expressions"></a><span data-ttu-id="9fd29-103">Expressions différées</span><span class="sxs-lookup"><span data-stu-id="9fd29-103">Lazy Expressions</span></span>

<span data-ttu-id="9fd29-104">Les *expressions tardives* sont des expressions qui ne sont pas évaluées immédiatement, mais qui sont évaluées à la place lorsque le résultat est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="9fd29-104">*Lazy expressions* are expressions that are not evaluated immediately, but are instead evaluated when the result is needed.</span></span> <span data-ttu-id="9fd29-105">Cela peut contribuer à améliorer les performances de votre code.</span><span class="sxs-lookup"><span data-stu-id="9fd29-105">This can help to improve the performance of your code.</span></span>

## <a name="syntax"></a><span data-ttu-id="9fd29-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9fd29-106">Syntax</span></span>

```fsharp
let identifier = lazy ( expression )
```

## <a name="remarks"></a><span data-ttu-id="9fd29-107">Notes</span><span class="sxs-lookup"><span data-stu-id="9fd29-107">Remarks</span></span>

<span data-ttu-id="9fd29-108">Dans la syntaxe précédente, l' *expression* est du code qui est évalué uniquement lorsqu’un résultat est requis, et l' *identificateur* est une valeur qui stocke le résultat.</span><span class="sxs-lookup"><span data-stu-id="9fd29-108">In the previous syntax, *expression* is code that is evaluated only when a result is required, and *identifier* is a value that stores the result.</span></span> <span data-ttu-id="9fd29-109">La valeur est de type [`Lazy<'T>`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-lazy-1-0.html) , où le type réel utilisé pour `'T` est déterminé à partir du résultat de l’expression.</span><span class="sxs-lookup"><span data-stu-id="9fd29-109">The value is of type [`Lazy<'T>`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-lazy-1-0.html), where the actual type that is used for `'T` is determined from the result of the expression.</span></span>

<span data-ttu-id="9fd29-110">Les expressions tardives vous permettent d’améliorer les performances en restreignant l’exécution d’une expression à des situations dans lesquelles un résultat est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="9fd29-110">Lazy expressions enable you to improve performance by restricting the execution of an expressions to only those situations in which a result is needed.</span></span>

<span data-ttu-id="9fd29-111">Pour forcer l’exécution des expressions, vous appelez la méthode `Force` .</span><span class="sxs-lookup"><span data-stu-id="9fd29-111">To force the expressions to be performed, you call the method `Force`.</span></span> <span data-ttu-id="9fd29-112">`Force` entraîne l’exécution d’une seule opération.</span><span class="sxs-lookup"><span data-stu-id="9fd29-112">`Force` causes the execution to be performed only one time.</span></span> <span data-ttu-id="9fd29-113">Les appels suivants pour `Force` retourner le même résultat, mais n’exécutent pas de code.</span><span class="sxs-lookup"><span data-stu-id="9fd29-113">Subsequent calls to `Force` return the same result, but do not execute any code.</span></span>

<span data-ttu-id="9fd29-114">Le code suivant illustre l’utilisation d’expressions tardives et l’utilisation de `Force` .</span><span class="sxs-lookup"><span data-stu-id="9fd29-114">The following code illustrates the use of lazy expressions and the use of `Force`.</span></span> <span data-ttu-id="9fd29-115">Dans ce code, le type de `result` est `Lazy<int>` , et la `Force` méthode retourne un `int` .</span><span class="sxs-lookup"><span data-stu-id="9fd29-115">In this code, the type of `result` is `Lazy<int>`, and the `Force` method returns an `int`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet73011.fs)]

<span data-ttu-id="9fd29-116">L’évaluation différée, mais pas le `Lazy` type, est également utilisée pour les séquences.</span><span class="sxs-lookup"><span data-stu-id="9fd29-116">Lazy evaluation, but not the `Lazy` type, is also used for sequences.</span></span> <span data-ttu-id="9fd29-117">Pour plus d’informations, consultez [séquences](sequences.md).</span><span class="sxs-lookup"><span data-stu-id="9fd29-117">For more information, see [Sequences](sequences.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9fd29-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9fd29-118">See also</span></span>

- [<span data-ttu-id="9fd29-119">Informations de référence sur le langage F #</span><span class="sxs-lookup"><span data-stu-id="9fd29-119">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="9fd29-120">Module LazyExtensions</span><span class="sxs-lookup"><span data-stu-id="9fd29-120">LazyExtensions module</span></span>](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-lazyextensions.html)
