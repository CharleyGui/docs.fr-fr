---
title: 'Expressions conditionnelles: if... puis... tierce'
description: Apprenez à écrire des expressions conditionnelles F# dans pour exécuter différentes branches de code.
ms.date: 05/16/2016
ms.openlocfilehash: 825149bf296eded3cc2b4d8847ba4d82bea40cdc
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630391"
---
# <a name="conditional-expressions-ifthenelse"></a><span data-ttu-id="85ffb-103">Expressions conditionnelles:`if...then...else`</span><span class="sxs-lookup"><span data-stu-id="85ffb-103">Conditional Expressions: `if...then...else`</span></span>

<span data-ttu-id="85ffb-104">L' `if...then...else` expression exécute différentes branches de code et prend également une valeur différente selon l’expression booléenne donnée.</span><span class="sxs-lookup"><span data-stu-id="85ffb-104">The `if...then...else` expression runs different branches of code and also evaluates to a different value depending on the Boolean expression given.</span></span>

## <a name="syntax"></a><span data-ttu-id="85ffb-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="85ffb-105">Syntax</span></span>

```fsharp
if boolean-expression then expression1 [ else expression2 ]
```

## <a name="remarks"></a><span data-ttu-id="85ffb-106">Notes</span><span class="sxs-lookup"><span data-stu-id="85ffb-106">Remarks</span></span>

<span data-ttu-id="85ffb-107">Dans la syntaxe précédente, *expression1* s’exécute lorsque l’expression booléenne prend `true`la valeur; sinon, *Expression2* s’exécute.</span><span class="sxs-lookup"><span data-stu-id="85ffb-107">In the previous syntax, *expression1* runs when the Boolean expression evaluates to `true`; otherwise, *expression2* runs.</span></span>

<span data-ttu-id="85ffb-108">Contrairement à d’autres langages `if...then...else` , la construction est une expression, et non une instruction.</span><span class="sxs-lookup"><span data-stu-id="85ffb-108">Unlike in other languages, the `if...then...else` construct is an expression, not a statement.</span></span> <span data-ttu-id="85ffb-109">Cela signifie qu’elle génère une valeur, qui est la valeur de la dernière expression dans la branche qui s’exécute.</span><span class="sxs-lookup"><span data-stu-id="85ffb-109">That means that it produces a value, which is the value of the last expression in the branch that executes.</span></span> <span data-ttu-id="85ffb-110">Les types des valeurs produites dans chaque branche doivent correspondre.</span><span class="sxs-lookup"><span data-stu-id="85ffb-110">The types of the values produced in each branch must match.</span></span> <span data-ttu-id="85ffb-111">S’il n’existe aucune `else` branche explicite, son type `unit`est.</span><span class="sxs-lookup"><span data-stu-id="85ffb-111">If there is no explicit `else` branch, its type is `unit`.</span></span> <span data-ttu-id="85ffb-112">Par conséquent, si le type de `then` la branche est un type autre `unit`que, il doit exister `else` une branche avec le même type de retour.</span><span class="sxs-lookup"><span data-stu-id="85ffb-112">Therefore, if the type of the `then` branch is any type other than `unit`, there must be an `else` branch with the same return type.</span></span> <span data-ttu-id="85ffb-113">Lors du Chaînage `if...then...else` d’expressions, vous pouvez utiliser le mot `elif` clé à `else if`la place de; ils sont équivalents.</span><span class="sxs-lookup"><span data-stu-id="85ffb-113">When chaining `if...then...else` expressions together, you can use the keyword `elif` instead of `else if`; they are equivalent.</span></span>

## <a name="example"></a><span data-ttu-id="85ffb-114">Exemples</span><span class="sxs-lookup"><span data-stu-id="85ffb-114">Example</span></span>

<span data-ttu-id="85ffb-115">L’exemple suivant illustre l’utilisation de l' `if...then...else` expression.</span><span class="sxs-lookup"><span data-stu-id="85ffb-115">The following example illustrates how to use the `if...then...else` expression.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4501.fs)]

```
10 is less than 20
What is your name? John
How old are you? 9
You are only 9 years old and already learning F#? Wow!
```

## <a name="see-also"></a><span data-ttu-id="85ffb-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="85ffb-116">See also</span></span>

- [<span data-ttu-id="85ffb-117">Informations de référence du langage F#</span><span class="sxs-lookup"><span data-stu-id="85ffb-117">F# Language Reference</span></span>](index.md)
