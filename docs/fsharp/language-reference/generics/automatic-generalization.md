---
title: Généralisation automatique
description: Découvrez comment F# généralise automatiquement les arguments et les types de fonctions afin qu’ils fonctionnent avec plusieurs types dans la mesure du possible.
ms.date: 05/16/2016
ms.openlocfilehash: 501749a190d9770cbcd9848e3d528cba32fe6762
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630625"
---
# <a name="automatic-generalization"></a><span data-ttu-id="22a0c-103">Généralisation automatique</span><span class="sxs-lookup"><span data-stu-id="22a0c-103">Automatic Generalization</span></span>

<span data-ttu-id="22a0c-104">F#utilise l’inférence de type pour évaluer les types de fonctions et d’expressions.</span><span class="sxs-lookup"><span data-stu-id="22a0c-104">F# uses type inference to evaluate the types of functions and expressions.</span></span> <span data-ttu-id="22a0c-105">Cette rubrique décrit comment F# généralise automatiquement les arguments et les types de fonctions afin qu’ils fonctionnent avec plusieurs types lorsque cela est possible.</span><span class="sxs-lookup"><span data-stu-id="22a0c-105">This topic describes how F# automatically generalizes the arguments and types of functions so that they work with multiple types when this is possible.</span></span>

## <a name="automatic-generalization"></a><span data-ttu-id="22a0c-106">Généralisation automatique</span><span class="sxs-lookup"><span data-stu-id="22a0c-106">Automatic Generalization</span></span>

<span data-ttu-id="22a0c-107">Lorsqu' F# il exécute l’inférence de type sur une fonction, le compilateur détermine si un paramètre donné peut être générique.</span><span class="sxs-lookup"><span data-stu-id="22a0c-107">The F# compiler, when it performs type inference on a function, determines whether a given parameter can be generic.</span></span> <span data-ttu-id="22a0c-108">Le compilateur examine chaque paramètre et détermine si la fonction a une dépendance vis-à-vis du type spécifique de ce paramètre.</span><span class="sxs-lookup"><span data-stu-id="22a0c-108">The compiler examines each parameter and determines whether the function has a dependency on the specific type of that parameter.</span></span> <span data-ttu-id="22a0c-109">Si ce n’est pas le cas, le type est déduit comme étant générique.</span><span class="sxs-lookup"><span data-stu-id="22a0c-109">If it does not, the type is inferred to be generic.</span></span>

<span data-ttu-id="22a0c-110">L’exemple de code suivant illustre une fonction que le compilateur déduit comme étant générique.</span><span class="sxs-lookup"><span data-stu-id="22a0c-110">The following code example illustrates a function that the compiler infers to be generic.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet101.fs)]

<span data-ttu-id="22a0c-111">Le type est déduit comme étant `'a -> 'a -> 'a`.</span><span class="sxs-lookup"><span data-stu-id="22a0c-111">The type is inferred to be `'a -> 'a -> 'a`.</span></span>

<span data-ttu-id="22a0c-112">Le type indique qu’il s’agit d’une fonction qui accepte deux arguments du même type inconnu et retourne une valeur du même type.</span><span class="sxs-lookup"><span data-stu-id="22a0c-112">The type indicates that this is a function that takes two arguments of the same unknown type and returns a value of that same type.</span></span> <span data-ttu-id="22a0c-113">L’une des raisons pour lesquelles la fonction Previous peut être générique est que l’opérateur «supérieur à`>`» () est lui-même générique.</span><span class="sxs-lookup"><span data-stu-id="22a0c-113">One of the reasons that the previous function can be generic is that the greater-than operator (`>`) is itself generic.</span></span> <span data-ttu-id="22a0c-114">L’opérateur «supérieur à» possède la `'a -> 'a -> bool`signature.</span><span class="sxs-lookup"><span data-stu-id="22a0c-114">The greater-than operator has the signature `'a -> 'a -> bool`.</span></span> <span data-ttu-id="22a0c-115">Les opérateurs ne sont pas tous génériques, et si le code d’une fonction utilise un type de paramètre avec une fonction ou un opérateur non générique, ce type de paramètre ne peut pas être généralisé.</span><span class="sxs-lookup"><span data-stu-id="22a0c-115">Not all operators are generic, and if the code in a function uses a parameter type together with a non-generic function or operator, that parameter type cannot be generalized.</span></span>

<span data-ttu-id="22a0c-116">Étant `max` donné que est générique, il peut être utilisé avec des `int`types `float`tels que,, etc., comme indiqué dans les exemples suivants.</span><span class="sxs-lookup"><span data-stu-id="22a0c-116">Because `max` is generic, it can be used with types such as `int`, `float`, and so on, as shown in the following examples.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet102.fs)]

<span data-ttu-id="22a0c-117">Toutefois, les deux arguments doivent être du même type.</span><span class="sxs-lookup"><span data-stu-id="22a0c-117">However, the two arguments must be of the same type.</span></span> <span data-ttu-id="22a0c-118">La signature est `'a -> 'a -> 'a`, et `'a -> 'b -> 'a`non.</span><span class="sxs-lookup"><span data-stu-id="22a0c-118">The signature is `'a -> 'a -> 'a`, not `'a -> 'b -> 'a`.</span></span> <span data-ttu-id="22a0c-119">Par conséquent, le code suivant génère une erreur, car les types ne correspondent pas.</span><span class="sxs-lookup"><span data-stu-id="22a0c-119">Therefore, the following code produces an error because the types do not match.</span></span>

```fsharp
// Error: type mismatch.
let biggestIntFloat = max 2.0 3
```

<span data-ttu-id="22a0c-120">La `max` fonction fonctionne également avec tout type qui prend en charge l’opérateur supérieur à.</span><span class="sxs-lookup"><span data-stu-id="22a0c-120">The `max` function also works with any type that supports the greater-than operator.</span></span> <span data-ttu-id="22a0c-121">Par conséquent, vous pouvez également l’utiliser sur une chaîne, comme illustré dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="22a0c-121">Therefore, you could also use it on a string, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet104.fs)]

## <a name="value-restriction"></a><span data-ttu-id="22a0c-122">Restriction de valeur</span><span class="sxs-lookup"><span data-stu-id="22a0c-122">Value Restriction</span></span>

<span data-ttu-id="22a0c-123">Le compilateur effectue la généralisation automatique uniquement sur les définitions de fonctions complètes qui ont des arguments explicites, et sur les valeurs immuables simples.</span><span class="sxs-lookup"><span data-stu-id="22a0c-123">The compiler performs automatic generalization only on complete function definitions that have explicit arguments, and on simple immutable values.</span></span>

<span data-ttu-id="22a0c-124">Cela signifie que le compilateur émet une erreur si vous essayez de compiler du code qui n’est pas suffisamment restreint pour être un type spécifique, mais qui n’est pas généralisable.</span><span class="sxs-lookup"><span data-stu-id="22a0c-124">This means that the compiler issues an error if you try to compile code that is not sufficiently constrained to be a specific type, but is also not generalizable.</span></span> <span data-ttu-id="22a0c-125">Le message d’erreur de ce problème fait référence à cette restriction sur la généralisation automatique pour les valeurs comme *restriction de valeur*.</span><span class="sxs-lookup"><span data-stu-id="22a0c-125">The error message for this problem refers to this restriction on automatic generalization for values as the *value restriction*.</span></span>

<span data-ttu-id="22a0c-126">En général, l’erreur de restriction de valeur se produit lorsque vous souhaitez qu’une construction soit générique, mais que le compilateur ne dispose pas d’informations suffisantes pour la généraliser, ou lorsque vous omettez involontairement des informations de type suffisantes dans une construction non générique.</span><span class="sxs-lookup"><span data-stu-id="22a0c-126">Typically, the value restriction error occurs either when you want a construct to be generic but the compiler has insufficient information to generalize it, or when you unintentionally omit sufficient type information in a nongeneric construct.</span></span> <span data-ttu-id="22a0c-127">La solution à l’erreur de restriction de valeur consiste à fournir des informations plus explicites pour limiter plus complètement le problème d’inférence de type, de l’une des manières suivantes:</span><span class="sxs-lookup"><span data-stu-id="22a0c-127">The solution to the value restriction error is to provide more explicit information to more fully constrain the type inference problem, in one of the following ways:</span></span>

- <span data-ttu-id="22a0c-128">Contraindre un type à être non générique en ajoutant une annotation de type explicite à une valeur ou un paramètre.</span><span class="sxs-lookup"><span data-stu-id="22a0c-128">Constrain a type to be nongeneric by adding an explicit type annotation to a value or parameter.</span></span>

- <span data-ttu-id="22a0c-129">Si le problème est lié à l’utilisation d’une construction non généralisable pour définir une fonction générique, telle qu’une composition de fonction ou des arguments de fonction curryfiés appliqués de manière incomplète, essayez de réécrire la fonction comme une définition de fonction ordinaire.</span><span class="sxs-lookup"><span data-stu-id="22a0c-129">If the problem is using a nongeneralizable construct to define a generic function, such as a function composition or incompletely applied curried function arguments, try to rewrite the function as an ordinary function definition.</span></span>

- <span data-ttu-id="22a0c-130">Si le problème est une expression trop complexe pour être généralisée, transformez-la en fonction en ajoutant un paramètre supplémentaire inutilisé.</span><span class="sxs-lookup"><span data-stu-id="22a0c-130">If the problem is an expression that is too complex to be generalized, make it into a function by adding an extra, unused parameter.</span></span>

- <span data-ttu-id="22a0c-131">Ajoutez des paramètres de type générique explicites.</span><span class="sxs-lookup"><span data-stu-id="22a0c-131">Add explicit generic type parameters.</span></span> <span data-ttu-id="22a0c-132">Cette option est rarement utilisée.</span><span class="sxs-lookup"><span data-stu-id="22a0c-132">This option is rarely used.</span></span>

- <span data-ttu-id="22a0c-133">Les exemples de code suivants illustrent chacun de ces scénarios.</span><span class="sxs-lookup"><span data-stu-id="22a0c-133">The following code examples illustrate each of these scenarios.</span></span>

<span data-ttu-id="22a0c-134">Cas 1: Expression trop complexe.</span><span class="sxs-lookup"><span data-stu-id="22a0c-134">Case 1: Too complex an expression.</span></span> <span data-ttu-id="22a0c-135">Dans cet exemple, la liste `counter` est destinée à être `int option ref`, mais elle n’est pas définie comme une valeur immuable simple.</span><span class="sxs-lookup"><span data-stu-id="22a0c-135">In this example, the list `counter` is intended to be `int option ref`, but it is not defined as a simple immutable value.</span></span>

```fsharp
let counter = ref None
// Adding a type annotation fixes the problem:
let counter : int option ref = ref None
```

<span data-ttu-id="22a0c-136">Cas 2: Utilisation d’une construction non généralisable pour définir une fonction générique.</span><span class="sxs-lookup"><span data-stu-id="22a0c-136">Case 2: Using a nongeneralizable construct to define a generic function.</span></span> <span data-ttu-id="22a0c-137">Dans cet exemple, la construction est non généralisable, car elle implique une application partielle des arguments de fonction.</span><span class="sxs-lookup"><span data-stu-id="22a0c-137">In this example, the construct is nongeneralizable because it involves partial application of function arguments.</span></span>

```fsharp
let maxhash = max << hash
// The following is acceptable because the argument for maxhash is explicit:
let maxhash obj = (max << hash) obj
```

<span data-ttu-id="22a0c-138">Cas 3: Ajout d’un paramètre supplémentaire inutilisé.</span><span class="sxs-lookup"><span data-stu-id="22a0c-138">Case 3: Adding an extra, unused parameter.</span></span> <span data-ttu-id="22a0c-139">Étant donné que cette expression n’est pas assez simple pour la généralisation, le compilateur émet l’erreur de restriction de valeur.</span><span class="sxs-lookup"><span data-stu-id="22a0c-139">Because this expression is not simple enough for generalization, the compiler issues the value restriction error.</span></span>

```fsharp
let emptyList10 = Array.create 10 []
// Adding an extra (unused) parameter makes it a function, which is generalizable.
let emptyList10 () = Array.create 10 []
```

<span data-ttu-id="22a0c-140">Cas 4: Ajout de paramètres de type.</span><span class="sxs-lookup"><span data-stu-id="22a0c-140">Case 4: Adding type parameters.</span></span>

```fsharp
let arrayOf10Lists = Array.create 10 []
// Adding a type parameter and type annotation lets you write a generic value.
let arrayOf10Lists<'T> = Array.create 10 ([]:'T list)
```

<span data-ttu-id="22a0c-141">Dans le dernier cas, la valeur devient une fonction de type, qui peut être utilisée pour créer des valeurs de nombreux types différents, par exemple, comme suit:</span><span class="sxs-lookup"><span data-stu-id="22a0c-141">In the last case, the value becomes a type function, which may be used to create values of many different types, for example as follows:</span></span>

```fsharp
let intLists = arrayOf10Lists<int>
let floatLists = arrayOf10Lists<float>
```

## <a name="see-also"></a><span data-ttu-id="22a0c-142">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="22a0c-142">See also</span></span>

- [<span data-ttu-id="22a0c-143">Inférence de type</span><span class="sxs-lookup"><span data-stu-id="22a0c-143">Type Inference</span></span>](../type-inference.md)
- [<span data-ttu-id="22a0c-144">Génériques</span><span class="sxs-lookup"><span data-stu-id="22a0c-144">Generics</span></span>](index.md)
- [<span data-ttu-id="22a0c-145">Paramètres de type résolus statiquement</span><span class="sxs-lookup"><span data-stu-id="22a0c-145">Statically Resolved Type Parameters</span></span>](statically-resolved-type-parameters.md)
- [<span data-ttu-id="22a0c-146">Contraintes</span><span class="sxs-lookup"><span data-stu-id="22a0c-146">Constraints</span></span>](constraints.md)
