---
title: 'Boucles : expression for...in'
description: Voir comment le F# ... dans, la construction de bouclage d’expression est utilisée pour itérer au sein des correspondances d’un modèle dans une collection énumérable.
ms.date: 05/16/2016
ms.openlocfilehash: 5a2ca59ca4199ece5d78010ff780e86ae2b25181
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71216446"
---
# <a name="loops-forin-expression"></a><span data-ttu-id="4fb09-103">Boucles : expression for...in</span><span class="sxs-lookup"><span data-stu-id="4fb09-103">Loops: for...in Expression</span></span>

<span data-ttu-id="4fb09-104">Cette construction de bouclage est utilisée pour itérer au sein des correspondances d’un modèle dans une collection énumérable, telle qu’une expression de plage, une séquence, une liste, un tableau ou une autre construction qui prend en charge l’énumération.</span><span class="sxs-lookup"><span data-stu-id="4fb09-104">This looping construct is used to iterate over the matches of a pattern in an enumerable collection such as a range expression, sequence, list, array, or other construct that supports enumeration.</span></span>

## <a name="syntax"></a><span data-ttu-id="4fb09-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4fb09-105">Syntax</span></span>

```fsharp
for pattern in enumerable-expression do
    body-expression
```

## <a name="remarks"></a><span data-ttu-id="4fb09-106">Notes</span><span class="sxs-lookup"><span data-stu-id="4fb09-106">Remarks</span></span>

<span data-ttu-id="4fb09-107">L' `for...in` expression peut être comparée à `for each` l’instruction dans d’autres langages .net, car elle est utilisée pour effectuer une boucle sur les valeurs dans une collection énumérable.</span><span class="sxs-lookup"><span data-stu-id="4fb09-107">The `for...in` expression can be compared to the `for each` statement in other .NET languages because it is used to loop over the values in an enumerable collection.</span></span> <span data-ttu-id="4fb09-108">Toutefois, `for...in` prend également en charge les critères spéciaux sur la collection au lieu d’une itération sur l’ensemble de la collection.</span><span class="sxs-lookup"><span data-stu-id="4fb09-108">However, `for...in` also supports pattern matching over the collection instead of just iteration over the whole collection.</span></span>

<span data-ttu-id="4fb09-109">L’expression énumérable peut être spécifiée en tant que collection énumérable ou, `..` à l’aide de l’opérateur, en tant que plage sur un type intégral.</span><span class="sxs-lookup"><span data-stu-id="4fb09-109">The enumerable expression can be specified as an enumerable collection or, by using the `..` operator, as a range on an integral type.</span></span> <span data-ttu-id="4fb09-110">Les collections énumérables incluent des listes, des séquences, des tableaux, des ensembles, des mappages, etc.</span><span class="sxs-lookup"><span data-stu-id="4fb09-110">Enumerable collections include lists, sequences, arrays, sets, maps, and so on.</span></span> <span data-ttu-id="4fb09-111">Tout type qui implémente `System.Collections.IEnumerable` peut être utilisé.</span><span class="sxs-lookup"><span data-stu-id="4fb09-111">Any type that implements `System.Collections.IEnumerable` can be used.</span></span>

<span data-ttu-id="4fb09-112">Lorsque vous exprimez une plage à `..` l’aide de l’opérateur, vous pouvez utiliser la syntaxe suivante.</span><span class="sxs-lookup"><span data-stu-id="4fb09-112">When you express a range by using the `..` operator, you can use the following syntax.</span></span>

<span data-ttu-id="4fb09-113">*Démarrer* ..</span><span class="sxs-lookup"><span data-stu-id="4fb09-113">*start* ..</span></span> <span data-ttu-id="4fb09-114">*terme*</span><span class="sxs-lookup"><span data-stu-id="4fb09-114">*finish*</span></span>

<span data-ttu-id="4fb09-115">Vous pouvez également utiliser une version qui comprend un incrément appelé *Skip*, comme dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="4fb09-115">You can also use a version that includes an increment called the *skip*, as in the following code.</span></span>

<span data-ttu-id="4fb09-116">*Démarrer* ..</span><span class="sxs-lookup"><span data-stu-id="4fb09-116">*start* ..</span></span> <span data-ttu-id="4fb09-117">*Ignorer* ..</span><span class="sxs-lookup"><span data-stu-id="4fb09-117">*skip* ..</span></span> <span data-ttu-id="4fb09-118">*terme*</span><span class="sxs-lookup"><span data-stu-id="4fb09-118">*finish*</span></span>

<span data-ttu-id="4fb09-119">Lorsque vous utilisez des plages intégrales et une variable de compteur simple en tant que modèle, le comportement standard consiste à incrémenter la variable de compteur de 1 à chaque itération, mais si la plage contient une valeur d’omission, le compteur est incrémenté par la valeur de saut.</span><span class="sxs-lookup"><span data-stu-id="4fb09-119">When you use integral ranges and a simple counter variable as a pattern, the typical behavior is to increment the counter variable by 1 on each iteration, but if the range includes a skip value, the counter is incremented by the skip value instead.</span></span>

<span data-ttu-id="4fb09-120">Les valeurs correspondantes dans le modèle peuvent également être utilisées dans l’expression de corps.</span><span class="sxs-lookup"><span data-stu-id="4fb09-120">Values matched in the pattern can also be used in the body expression.</span></span>

<span data-ttu-id="4fb09-121">Les exemples de code suivants illustrent l’utilisation `for...in` de l’expression.</span><span class="sxs-lookup"><span data-stu-id="4fb09-121">The following code examples illustrate the use of the `for...in` expression.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5201.fs)]

<span data-ttu-id="4fb09-122">La sortie est la suivante.</span><span class="sxs-lookup"><span data-stu-id="4fb09-122">The output is as follows.</span></span>

```console
1
5
100
450
788
```

<span data-ttu-id="4fb09-123">L’exemple suivant montre comment effectuer une boucle sur une séquence et comment utiliser un modèle de tuple à la place d’une variable simple.</span><span class="sxs-lookup"><span data-stu-id="4fb09-123">The following example shows how to loop over a sequence, and how to use a tuple pattern instead of a simple variable.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5202.fs)]

<span data-ttu-id="4fb09-124">La sortie est la suivante.</span><span class="sxs-lookup"><span data-stu-id="4fb09-124">The output is as follows.</span></span>

```console
1 squared is 1
2 squared is 4
3 squared is 9
4 squared is 16
5 squared is 25
6 squared is 36
7 squared is 49
8 squared is 64
9 squared is 81
10 squared is 100
```

<span data-ttu-id="4fb09-125">L’exemple suivant montre comment effectuer une boucle sur une plage d’entiers simple.</span><span class="sxs-lookup"><span data-stu-id="4fb09-125">The following example shows how to loop over a simple integer range.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5203.fs)]

<span data-ttu-id="4fb09-126">La sortie de function1 est la suivante.</span><span class="sxs-lookup"><span data-stu-id="4fb09-126">The output of function1 is as follows.</span></span>

```console
1 2 3 4 5 6 7 8 9 10
```

<span data-ttu-id="4fb09-127">L’exemple suivant montre comment effectuer une boucle sur une plage avec un saut de 2, qui comprend tous les autres éléments de la plage.</span><span class="sxs-lookup"><span data-stu-id="4fb09-127">The following example shows how to loop over a range with a skip of 2, which includes every other element of the range.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5204.fs)]

<span data-ttu-id="4fb09-128">La sortie de `function2` est la suivante.</span><span class="sxs-lookup"><span data-stu-id="4fb09-128">The output of `function2` is as follows.</span></span>

```console
1 3 5 7 9
```

<span data-ttu-id="4fb09-129">L’exemple suivant montre comment utiliser une plage de caractères.</span><span class="sxs-lookup"><span data-stu-id="4fb09-129">The following example shows how to use a character range.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5205.fs)]

<span data-ttu-id="4fb09-130">La sortie de `function3` est la suivante.</span><span class="sxs-lookup"><span data-stu-id="4fb09-130">The output of `function3` is as follows.</span></span>

```console
a b c d e f g h i j k l m n o p q r s t u v w x y z
```

<span data-ttu-id="4fb09-131">L’exemple suivant montre comment utiliser une valeur Skip négative pour une itération inverse.</span><span class="sxs-lookup"><span data-stu-id="4fb09-131">The following example shows how to use a negative skip value for a reverse iteration.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5208.fs)]

<span data-ttu-id="4fb09-132">La sortie de `function4` est la suivante.</span><span class="sxs-lookup"><span data-stu-id="4fb09-132">The output of `function4` is as follows.</span></span>

```console
10 9 8 7 6 5 4 3 2 1 ... Lift off!
```

<span data-ttu-id="4fb09-133">Le début et la fin de la plage peuvent également être des expressions, telles que des fonctions, comme dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="4fb09-133">The beginning and ending of the range can also be expressions, such as functions, as in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5206.fs)]

<span data-ttu-id="4fb09-134">La sortie de `function5` avec cette entrée est la suivante.</span><span class="sxs-lookup"><span data-stu-id="4fb09-134">The output of `function5` with this input is as follows.</span></span>

```console
2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18
```

<span data-ttu-id="4fb09-135">L’exemple suivant illustre l’utilisation d’un caractère générique (\_) lorsque l’élément n’est pas nécessaire dans la boucle.</span><span class="sxs-lookup"><span data-stu-id="4fb09-135">The next example shows the use of a wildcard character (\_) when the element is not needed in the loop.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5207.fs)]

<span data-ttu-id="4fb09-136">La sortie est la suivante.</span><span class="sxs-lookup"><span data-stu-id="4fb09-136">The output is as follows.</span></span>

```console
Number of elements in list1: 5
```

<span data-ttu-id="4fb09-137">`Note`Vous pouvez utiliser `for...in` dans les expressions de séquence et d’autres expressions de calcul, auquel cas une version personnalisée `for...in` de l’expression est utilisée.</span><span class="sxs-lookup"><span data-stu-id="4fb09-137">`Note` You can use `for...in` in sequence expressions and other computation expressions, in which case a customized version of the `for...in` expression is used.</span></span> <span data-ttu-id="4fb09-138">Pour plus d’informations, consultez [séquences](sequences.md), [flux de travail asynchrones](asynchronous-workflows.md) et [expressions de calcul](computation-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="4fb09-138">For more information, see [Sequences](sequences.md), [Asynchronous Workflows](asynchronous-workflows.md), and [Computation Expressions](computation-expressions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4fb09-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4fb09-139">See also</span></span>

- [<span data-ttu-id="4fb09-140">Informations de référence du langage F#</span><span class="sxs-lookup"><span data-stu-id="4fb09-140">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="4fb09-141">Boucles `for...to`Formule</span><span class="sxs-lookup"><span data-stu-id="4fb09-141">Loops: `for...to` Expression</span></span>](loops-for-to-expression.md)
- [<span data-ttu-id="4fb09-142">Boucles `while...do`Formule</span><span class="sxs-lookup"><span data-stu-id="4fb09-142">Loops: `while...do` Expression</span></span>](loops-while-do-expression.md)
