---
title: Expressions de correspondance
description: Découvrez comment l' F# expression de correspondance fournit un contrôle de branchement basé sur la comparaison d’une expression avec un ensemble de modèles.
ms.date: 04/19/2018
ms.openlocfilehash: 222cb0604300039d86ed0c80293651631d212eb6
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627607"
---
# <a name="match-expressions"></a><span data-ttu-id="c8828-103">Expressions de correspondance</span><span class="sxs-lookup"><span data-stu-id="c8828-103">Match expressions</span></span>

<span data-ttu-id="c8828-104">L' `match` expression fournit un contrôle de branchement basé sur la comparaison d’une expression avec un ensemble de modèles.</span><span class="sxs-lookup"><span data-stu-id="c8828-104">The `match` expression provides branching control that is based on the comparison of an expression with a set of patterns.</span></span>

## <a name="syntax"></a><span data-ttu-id="c8828-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c8828-105">Syntax</span></span>

```fsharp
// Match expression.
match test-expression with
| pattern1 [ when condition ] -> result-expression1
| pattern2 [ when condition ] -> result-expression2
| ...

// Pattern matching function.
function
| pattern1 [ when condition ] -> result-expression1
| pattern2 [ when condition ] -> result-expression2
| ...
```

## <a name="remarks"></a><span data-ttu-id="c8828-106">Notes</span><span class="sxs-lookup"><span data-stu-id="c8828-106">Remarks</span></span>

<span data-ttu-id="c8828-107">Les expressions de critères spéciaux permettent une branche complexe basée sur la comparaison d’une expression de test avec un ensemble de modèles.</span><span class="sxs-lookup"><span data-stu-id="c8828-107">The pattern matching expressions allow for complex branching based on the comparison of a test expression with a set of patterns.</span></span> <span data-ttu-id="c8828-108">Dans l' `match` expression, l’expression de *test* est comparée à chaque modèle, et lorsqu’une correspondance est trouvée, l' *expression de résultat* correspondante est évaluée et la valeur résultante est retournée en tant que valeur de l’expression de correspondance.</span><span class="sxs-lookup"><span data-stu-id="c8828-108">In the `match` expression, the *test-expression* is compared with each pattern in turn, and when a match is found, the corresponding *result-expression* is evaluated and the resulting value is returned as the value of the match expression.</span></span>

<span data-ttu-id="c8828-109">La fonction de critères spéciaux indiquée dans la syntaxe précédente est une expression lambda dans laquelle les critères spéciaux sont exécutés immédiatement sur l’argument.</span><span class="sxs-lookup"><span data-stu-id="c8828-109">The pattern matching function shown in the previous syntax is a lambda expression in which pattern matching is performed immediately on the argument.</span></span> <span data-ttu-id="c8828-110">La fonction de critères spéciaux indiquée dans la syntaxe précédente est équivalente à ce qui suit.</span><span class="sxs-lookup"><span data-stu-id="c8828-110">The pattern matching function shown in the previous syntax is equivalent to the following.</span></span>

```fsharp
fun arg ->
    match arg with
    | pattern1 [ when condition ] -> result-expression1
    | pattern2 [ when condition ] -> result-expression2
    | ...
```

<span data-ttu-id="c8828-111">Pour plus d’informations sur les expressions lambda [, consultez Expressions lambda: `fun` Mot clé](./functions/lambda-expressions-the-fun-keyword.md).</span><span class="sxs-lookup"><span data-stu-id="c8828-111">For more information about lambda expressions, see [Lambda Expressions: The `fun` Keyword](./functions/lambda-expressions-the-fun-keyword.md).</span></span>

<span data-ttu-id="c8828-112">L’ensemble des modèles doit couvrir toutes les correspondances possibles de la variable d’entrée.</span><span class="sxs-lookup"><span data-stu-id="c8828-112">The whole set of patterns should cover all the possible matches of the input variable.</span></span> <span data-ttu-id="c8828-113">Souvent, vous utilisez le modèle de caractère`_`générique () comme dernier modèle pour faire correspondre toutes les valeurs d’entrée précédemment non appariées.</span><span class="sxs-lookup"><span data-stu-id="c8828-113">Frequently, you use the wildcard pattern (`_`) as the last pattern to match any previously unmatched input values.</span></span>

<span data-ttu-id="c8828-114">Le code suivant illustre quelques-unes des façons dont l' `match` expression est utilisée.</span><span class="sxs-lookup"><span data-stu-id="c8828-114">The following code illustrates some of the ways in which the `match` expression is used.</span></span> <span data-ttu-id="c8828-115">Pour obtenir une référence et des exemples de tous les modèles possibles qui peuvent être utilisés, consultez [critères spéciaux](pattern-matching.md).</span><span class="sxs-lookup"><span data-stu-id="c8828-115">For a reference and examples of all the possible patterns that can be used, see [Pattern Matching](pattern-matching.md).</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4601.fs)]

## <a name="guards-on-patterns"></a><span data-ttu-id="c8828-116">Gardes sur les modèles</span><span class="sxs-lookup"><span data-stu-id="c8828-116">Guards on patterns</span></span>

<span data-ttu-id="c8828-117">Vous pouvez utiliser une `when` clause pour spécifier une condition supplémentaire que la variable doit satisfaire pour correspondre à un modèle.</span><span class="sxs-lookup"><span data-stu-id="c8828-117">You can use a `when` clause to specify an additional condition that the variable must satisfy to match a pattern.</span></span> <span data-ttu-id="c8828-118">Une telle clause est appelée un *garde*.</span><span class="sxs-lookup"><span data-stu-id="c8828-118">Such a clause is referred to as a *guard*.</span></span> <span data-ttu-id="c8828-119">L’expression qui suit `when` le mot clé n’est pas évaluée, sauf si une correspondance est établie avec le modèle associé à cette protection.</span><span class="sxs-lookup"><span data-stu-id="c8828-119">The expression following the `when` keyword is not evaluated unless a match is made to the pattern associated with that guard.</span></span>

<span data-ttu-id="c8828-120">L’exemple suivant illustre l’utilisation d’un garde pour spécifier une plage numérique pour un modèle de variable.</span><span class="sxs-lookup"><span data-stu-id="c8828-120">The following example illustrates the use of a guard to specify a numeric range for a variable pattern.</span></span> <span data-ttu-id="c8828-121">Notez que plusieurs conditions sont combinées à l’aide d’opérateurs booléens.</span><span class="sxs-lookup"><span data-stu-id="c8828-121">Note that multiple conditions are combined by using Boolean operators.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4602.fs)]

<span data-ttu-id="c8828-122">Notez que les valeurs autres que les littéraux ne peuvent pas être utilisées dans le modèle, vous `when` devez utiliser une clause si vous devez comparer une partie de l’entrée à une valeur.</span><span class="sxs-lookup"><span data-stu-id="c8828-122">Note that because values other than literals cannot be used in the pattern, you must use a `when` clause if you have to compare some part of the input against a value.</span></span> <span data-ttu-id="c8828-123">Ceci est illustré dans le code suivant :</span><span class="sxs-lookup"><span data-stu-id="c8828-123">This is shown in the following code:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4603.fs)]

<span data-ttu-id="c8828-124">Notez que lorsqu’un modèle d’Union est couvert par une protection, la protection s’applique à **tous** les modèles, pas seulement au dernier.</span><span class="sxs-lookup"><span data-stu-id="c8828-124">Note that when a union pattern is covered by a guard, the guard applies to **all** of the patterns, not just the last one.</span></span> <span data-ttu-id="c8828-125">Par exemple, étant donné le code suivant, la `when a > 12` protection s’applique `A a` à `B a`la fois à et à:</span><span class="sxs-lookup"><span data-stu-id="c8828-125">For example, given the following code, the guard `when a > 12` applies to both `A a` and `B a`:</span></span>

```fsharp
type Union =
    | A of int
    | B of int

let foo() =
    let test = A 42
    match test with
    | A a
    | B a when a > 41 -> a // the guard applies to both patterns
    | _ -> 1

foo() // returns 42
```

## <a name="see-also"></a><span data-ttu-id="c8828-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c8828-126">See also</span></span>

- [<span data-ttu-id="c8828-127">Informations de référence du langage F#</span><span class="sxs-lookup"><span data-stu-id="c8828-127">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="c8828-128">Modèles actifs</span><span class="sxs-lookup"><span data-stu-id="c8828-128">Active Patterns</span></span>](active-patterns.md)
- [<span data-ttu-id="c8828-129">Critères spéciaux</span><span class="sxs-lookup"><span data-stu-id="c8828-129">Pattern Matching</span></span>](pattern-matching.md)
