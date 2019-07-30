---
title: Fonctions inline
description: Découvrez comment utiliser F# des fonctions inline intégrées directement dans le code appelant.
ms.date: 05/16/2016
ms.openlocfilehash: 2830d1ada5b3005c3fcae975a44e85a7c84554f7
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630676"
---
# <a name="inline-functions"></a><span data-ttu-id="fb458-103">Fonctions inline</span><span class="sxs-lookup"><span data-stu-id="fb458-103">Inline Functions</span></span>

<span data-ttu-id="fb458-104">Les *fonctions inline* sont des fonctions qui sont intégrées directement dans le code appelant.</span><span class="sxs-lookup"><span data-stu-id="fb458-104">*Inline functions* are functions that are integrated directly into the calling code.</span></span>

## <a name="using-inline-functions"></a><span data-ttu-id="fb458-105">Utilisation de fonctions inline</span><span class="sxs-lookup"><span data-stu-id="fb458-105">Using Inline Functions</span></span>

<span data-ttu-id="fb458-106">Quand vous utilisez des paramètres de type statique, toutes les fonctions qui sont paramétrables par des paramètres de type doivent être Inline.</span><span class="sxs-lookup"><span data-stu-id="fb458-106">When you use static type parameters, any functions that are parameterized by type parameters must be inline.</span></span> <span data-ttu-id="fb458-107">Cela garantit que le compilateur peut résoudre ces paramètres de type.</span><span class="sxs-lookup"><span data-stu-id="fb458-107">This guarantees that the compiler can resolve these type parameters.</span></span> <span data-ttu-id="fb458-108">Lorsque vous utilisez des paramètres de type générique ordinaires, il n’existe aucune restriction de ce type.</span><span class="sxs-lookup"><span data-stu-id="fb458-108">When you use ordinary generic type parameters, there is no such restriction.</span></span>

<span data-ttu-id="fb458-109">Outre l’activation de l’utilisation de contraintes de membre, les fonctions inline peuvent être utiles pour optimiser le code.</span><span class="sxs-lookup"><span data-stu-id="fb458-109">Other than enabling the use of member constraints, inline functions can be helpful in optimizing code.</span></span> <span data-ttu-id="fb458-110">Toutefois, l’utilisation abusive des fonctions inline peut rendre votre code moins résistant aux modifications des optimisations du compilateur et à l’implémentation des fonctions de la bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="fb458-110">However, overuse of inline functions can cause your code to be less resistant to changes in compiler optimizations and the implementation of library functions.</span></span> <span data-ttu-id="fb458-111">Pour cette raison, vous devez éviter d’utiliser des fonctions inline pour l’optimisation, sauf si vous avez essayé toutes les autres techniques d’optimisation.</span><span class="sxs-lookup"><span data-stu-id="fb458-111">For this reason, you should avoid using inline functions for optimization unless you have tried all other optimization techniques.</span></span> <span data-ttu-id="fb458-112">La création d’une fonction ou d’une méthode en ligne peut parfois améliorer les performances, mais ce n’est pas toujours le cas.</span><span class="sxs-lookup"><span data-stu-id="fb458-112">Making a function or method inline can sometimes improve performance, but that is not always the case.</span></span> <span data-ttu-id="fb458-113">Par conséquent, vous devez également utiliser des mesures de performances pour vérifier que l’exécution d’une fonction inline donnée a un effet positif.</span><span class="sxs-lookup"><span data-stu-id="fb458-113">Therefore, you should also use performance measurements to verify that making any given function inline does in fact have a positive effect.</span></span>

<span data-ttu-id="fb458-114">Le `inline` modificateur peut être appliqué aux fonctions au niveau supérieur, au niveau du module ou au niveau de la méthode dans une classe.</span><span class="sxs-lookup"><span data-stu-id="fb458-114">The `inline` modifier can be applied to functions at the top level, at the module level, or at the method level in a class.</span></span>

<span data-ttu-id="fb458-115">L’exemple de code suivant illustre une fonction inline au niveau supérieur, une méthode d’instance inline et une méthode statique Inline.</span><span class="sxs-lookup"><span data-stu-id="fb458-115">The following code example illustrates an inline function at the top level, an inline instance method, and an inline static method.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet201.fs)]

## <a name="inline-functions-and-type-inference"></a><span data-ttu-id="fb458-116">Fonctions inline et inférence de type</span><span class="sxs-lookup"><span data-stu-id="fb458-116">Inline Functions and Type Inference</span></span>

<span data-ttu-id="fb458-117">La présence de `inline` affecte l’inférence de type.</span><span class="sxs-lookup"><span data-stu-id="fb458-117">The presence of `inline` affects type inference.</span></span> <span data-ttu-id="fb458-118">Cela est dû au fait que les fonctions inline peuvent avoir des paramètres de type résolus statiquement, alors que les fonctions non inline ne le peuvent pas.</span><span class="sxs-lookup"><span data-stu-id="fb458-118">This is because inline functions can have statically resolved type parameters, whereas non-inline functions cannot.</span></span> <span data-ttu-id="fb458-119">L’exemple de code suivant montre un cas `inline` dans lequel est utile, car vous utilisez une fonction qui a un paramètre de type résolu statiquement, l' `float` opérateur de conversion.</span><span class="sxs-lookup"><span data-stu-id="fb458-119">The following code example shows a case where `inline` is helpful because you are using a function that has a statically resolved type parameter, the `float` conversion operator.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet202.fs)]

<span data-ttu-id="fb458-120">Sans le `inline` modificateur, l’inférence de type force la fonction à prendre un type spécifique, dans `int`ce cas.</span><span class="sxs-lookup"><span data-stu-id="fb458-120">Without the `inline` modifier, type inference forces the function to take a specific type, in this case `int`.</span></span> <span data-ttu-id="fb458-121">Toutefois, avec `inline` le modificateur, la fonction est également déduite pour avoir un paramètre de type résolu statiquement.</span><span class="sxs-lookup"><span data-stu-id="fb458-121">But with the `inline` modifier, the function is also inferred to have a statically resolved type parameter.</span></span> <span data-ttu-id="fb458-122">Avec le `inline` modificateur, le type est déduit comme suit:</span><span class="sxs-lookup"><span data-stu-id="fb458-122">With the `inline` modifier, the type is inferred to be the following:</span></span>

```fsharp
^a -> unit when ^a : (static member op_Explicit : ^a -> float)
```

<span data-ttu-id="fb458-123">Cela signifie que la fonction accepte tout type qui prend en charge une conversion en **float**.</span><span class="sxs-lookup"><span data-stu-id="fb458-123">This means that the function accepts any type that supports a conversion to **float**.</span></span>

## <a name="see-also"></a><span data-ttu-id="fb458-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fb458-124">See also</span></span>

- [<span data-ttu-id="fb458-125">Fonctions</span><span class="sxs-lookup"><span data-stu-id="fb458-125">Functions</span></span>](index.md)
- [<span data-ttu-id="fb458-126">Contraintes</span><span class="sxs-lookup"><span data-stu-id="fb458-126">Constraints</span></span>](../generics/constraints.md)
- [<span data-ttu-id="fb458-127">Paramètres de type résolus statiquement</span><span class="sxs-lookup"><span data-stu-id="fb458-127">Statically Resolved Type Parameters</span></span>](../generics/statically-resolved-type-parameters.md)
