---
title: Types flexibles
description: Découvrez comment utiliser F# l’annotation de type flexible, qui indique qu’un paramètre, une variable ou une valeur a un type qui est compatible avec un type spécifié.
ms.date: 05/16/2016
ms.openlocfilehash: 43caa6cd35630df648beda5cc43cffae2ecd6f6a
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630263"
---
# <a name="flexible-types"></a><span data-ttu-id="51c76-103">Types flexibles</span><span class="sxs-lookup"><span data-stu-id="51c76-103">Flexible Types</span></span>

<span data-ttu-id="51c76-104">Une *annotation de type flexible* indique qu’un paramètre, une variable ou une valeur a un type qui est compatible avec un type spécifié, où la compatibilité est déterminée par la position dans une hiérarchie orientée objet de classes ou d’interfaces.</span><span class="sxs-lookup"><span data-stu-id="51c76-104">A *flexible type annotation* indicates that a parameter, variable, or value has a type that is compatible with a specified type, where compatibility is determined by position in an object-oriented hierarchy of classes or interfaces.</span></span> <span data-ttu-id="51c76-105">Les types flexibles sont particulièrement utiles lorsque la conversion automatique en types plus hauts dans la hiérarchie de types ne se produit pas, mais que vous souhaitez toujours permettre à votre fonctionnalité de fonctionner avec n’importe quel type dans la hiérarchie ou dans tout type qui implémente une interface.</span><span class="sxs-lookup"><span data-stu-id="51c76-105">Flexible types are useful specifically when the automatic conversion to types higher in the type hierarchy does not occur but you still want to enable your functionality to work with any type in the hierarchy or any type that implements an interface.</span></span>

## <a name="syntax"></a><span data-ttu-id="51c76-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="51c76-106">Syntax</span></span>

```fsharp
#type
```

## <a name="remarks"></a><span data-ttu-id="51c76-107">Notes</span><span class="sxs-lookup"><span data-stu-id="51c76-107">Remarks</span></span>

<span data-ttu-id="51c76-108">Dans la syntaxe précédente, *type* représente un type de base ou une interface.</span><span class="sxs-lookup"><span data-stu-id="51c76-108">In the previous syntax, *type* represents a base type or an interface.</span></span>

<span data-ttu-id="51c76-109">Un type flexible est équivalent à un type générique qui a une contrainte qui limite les types autorisés aux types qui sont compatibles avec le type de base ou d’interface.</span><span class="sxs-lookup"><span data-stu-id="51c76-109">A flexible type is equivalent to a generic type that has a constraint that limits the allowed types to types that are compatible with the base or interface type.</span></span> <span data-ttu-id="51c76-110">Autrement dit, les deux lignes de code suivantes sont équivalentes.</span><span class="sxs-lookup"><span data-stu-id="51c76-110">That is, the following two lines of code are equivalent.</span></span>

```fsharp
#SomeType

'T when 'T :> SomeType
```

<span data-ttu-id="51c76-111">Les types flexibles sont utiles dans plusieurs types de situations.</span><span class="sxs-lookup"><span data-stu-id="51c76-111">Flexible types are useful in several types of situations.</span></span> <span data-ttu-id="51c76-112">Par exemple, lorsque vous avez une fonction d’ordre supérieur (une fonction qui prend une fonction comme argument), il est souvent utile que la fonction retourne un type flexible.</span><span class="sxs-lookup"><span data-stu-id="51c76-112">For example, when you have a higher order function (a function that takes a function as an argument), it is often useful to have the function return a flexible type.</span></span> <span data-ttu-id="51c76-113">Dans l’exemple suivant, l’utilisation d’un type flexible avec un argument de séquence `iterate2` dans permet à la fonction d’ordre supérieur d’utiliser des fonctions qui génèrent des séquences, des tableaux, des listes et tout autre type énumérable.</span><span class="sxs-lookup"><span data-stu-id="51c76-113">In the following example, the use of a flexible type with a sequence argument in `iterate2` enables the higher order function to work with functions that generate sequences, arrays, lists, and any other enumerable type.</span></span>

<span data-ttu-id="51c76-114">Considérez les deux fonctions suivantes, dont l’une retourne une séquence, l’autre qui retourne un type flexible.</span><span class="sxs-lookup"><span data-stu-id="51c76-114">Consider the following two functions, one of which returns a sequence, the other of which returns a flexible type.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4101.fs)]

<span data-ttu-id="51c76-115">En guise d’autre exemple, considérez la fonction de bibliothèque [Seq. Concat](https://msdn.microsoft.com/library/2eeb69a9-fc2f-4b7d-8dee-101fa2b00712) :</span><span class="sxs-lookup"><span data-stu-id="51c76-115">As another example, consider the [Seq.concat](https://msdn.microsoft.com/library/2eeb69a9-fc2f-4b7d-8dee-101fa2b00712) library function:</span></span>

```fsharp
val concat: sequences:seq<#seq<'T>> -> seq<'T>
```

<span data-ttu-id="51c76-116">Vous pouvez passer les séquences énumérables suivantes à cette fonction:</span><span class="sxs-lookup"><span data-stu-id="51c76-116">You can pass any of the following enumerable sequences to this function:</span></span>

- <span data-ttu-id="51c76-117">Liste de listes</span><span class="sxs-lookup"><span data-stu-id="51c76-117">A list of lists</span></span>
- <span data-ttu-id="51c76-118">Liste de tableaux</span><span class="sxs-lookup"><span data-stu-id="51c76-118">A list of arrays</span></span>
- <span data-ttu-id="51c76-119">Tableau de listes</span><span class="sxs-lookup"><span data-stu-id="51c76-119">An array of lists</span></span>
- <span data-ttu-id="51c76-120">Tableau de séquences</span><span class="sxs-lookup"><span data-stu-id="51c76-120">An array of sequences</span></span>
- <span data-ttu-id="51c76-121">Toute autre combinaison de séquences énumérables</span><span class="sxs-lookup"><span data-stu-id="51c76-121">Any other combination of enumerable sequences</span></span>

<span data-ttu-id="51c76-122">Le code suivant utilise `Seq.concat` pour illustrer les scénarios que vous pouvez prendre en charge à l’aide de types flexibles.</span><span class="sxs-lookup"><span data-stu-id="51c76-122">The following code uses `Seq.concat` to demonstrate the scenarios that you can support by using flexible types.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4102.fs)]

<span data-ttu-id="51c76-123">La sortie est la suivante.</span><span class="sxs-lookup"><span data-stu-id="51c76-123">The output is as follows.</span></span>

```
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
```

<span data-ttu-id="51c76-124">Dans F#, comme dans d’autres langages orientés objet, il existe des contextes dans lesquels les types dérivés ou les types qui implémentent les interfaces sont convertis automatiquement en type de base ou en type d’interface.</span><span class="sxs-lookup"><span data-stu-id="51c76-124">In F#, as in other object-oriented languages, there are contexts in which derived types or types that implement interfaces are automatically converted to a base type or interface type.</span></span> <span data-ttu-id="51c76-125">Ces conversions automatiques se produisent dans les arguments directs, mais pas lorsque le type est en position subordonnée, dans le cadre d’un type plus complexe, tel qu’un type de retour d’un type de fonction, ou en tant qu’argument de type.</span><span class="sxs-lookup"><span data-stu-id="51c76-125">These automatic conversions occur in direct arguments, but not when the type is in a subordinate position, as part of a more complex type such as a return type of a function type, or as a type argument.</span></span> <span data-ttu-id="51c76-126">Par conséquent, la notation de type flexible est surtout utile lorsque le type auquel vous l’appliquez fait partie d’un type plus complexe.</span><span class="sxs-lookup"><span data-stu-id="51c76-126">Thus, the flexible type notation is primarily useful when the type you are applying it to is part of a more complex type.</span></span>

## <a name="see-also"></a><span data-ttu-id="51c76-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="51c76-127">See also</span></span>

- [<span data-ttu-id="51c76-128">Informations de référence du langage F#</span><span class="sxs-lookup"><span data-stu-id="51c76-128">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="51c76-129">Génériques</span><span class="sxs-lookup"><span data-stu-id="51c76-129">Generics</span></span>](./generics/index.md)
