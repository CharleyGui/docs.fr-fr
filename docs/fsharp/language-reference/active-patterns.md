---
title: Modèles actifs
description: Découvrez comment utiliser des modèles actifs pour définir des partitions nommées qui subdivisent les F# données d’entrée dans le langage de programmation.
ms.date: 05/16/2016
ms.openlocfilehash: f5ed4a8600cba10d23d01628aba6ca07e543c586
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73425096"
---
# <a name="active-patterns"></a><span data-ttu-id="2399c-103">Modèles actifs</span><span class="sxs-lookup"><span data-stu-id="2399c-103">Active Patterns</span></span>

<span data-ttu-id="2399c-104">Les *modèles actifs* vous permettent de définir des partitions nommées qui subdivisent les données d’entrée, afin que vous puissiez utiliser ces noms dans une expression de critères spéciaux comme vous le feriez pour une union discriminée.</span><span class="sxs-lookup"><span data-stu-id="2399c-104">*Active patterns* enable you to define named partitions that subdivide input data, so that you can use these names in a pattern matching expression just as you would for a discriminated union.</span></span> <span data-ttu-id="2399c-105">Vous pouvez utiliser des modèles actifs pour décomposer des données de façon personnalisée pour chaque partition.</span><span class="sxs-lookup"><span data-stu-id="2399c-105">You can use active patterns to decompose data in a customized manner for each partition.</span></span>

## <a name="syntax"></a><span data-ttu-id="2399c-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2399c-106">Syntax</span></span>

```fsharp
// Active pattern of one choice.
let (|identifier|) [arguments] valueToMatch= expression

// Active Pattern with multiple choices.
// Uses a FSharp.Core.Choice<_,...,_> based on the number of case names. In F#, the limitation n <= 7 applies.
let (|identifer1|identifier2|...|) valueToMatch = expression

// Partial active pattern definition.
// Uses a FSharp.Core.option<_> to represent if the type is satisfied at the call site.
let (|identifier|_|) [arguments ] valueToMatch = expression
```

## <a name="remarks"></a><span data-ttu-id="2399c-107">Notes</span><span class="sxs-lookup"><span data-stu-id="2399c-107">Remarks</span></span>

<span data-ttu-id="2399c-108">Dans la syntaxe précédente, les identificateurs sont des noms de partitions des données d’entrée qui sont représentées par des *arguments*, ou, en d’autres termes, des noms pour les sous-ensembles de l’ensemble de toutes les valeurs des arguments.</span><span class="sxs-lookup"><span data-stu-id="2399c-108">In the previous syntax, the identifiers are names for partitions of the input data that is represented by *arguments*, or, in other words, names for subsets of the set of all values of the arguments.</span></span> <span data-ttu-id="2399c-109">Il peut y avoir jusqu’à sept partitions dans une définition de modèle actif.</span><span class="sxs-lookup"><span data-stu-id="2399c-109">There can be up to seven partitions in an active pattern definition.</span></span> <span data-ttu-id="2399c-110">L' *expression* décrit le formulaire dans lequel décomposer les données.</span><span class="sxs-lookup"><span data-stu-id="2399c-110">The *expression* describes the form into which to decompose the data.</span></span> <span data-ttu-id="2399c-111">Vous pouvez utiliser une définition de modèle actif pour définir les règles de détermination des partitions nommées auxquelles les valeurs fournies comme arguments appartiennent.</span><span class="sxs-lookup"><span data-stu-id="2399c-111">You can use an active pattern definition to define the rules for determining which of the named partitions the values given as arguments belong to.</span></span> <span data-ttu-id="2399c-112">Les symboles (| et |) sont appelés « *Banana clips* » et la fonction créée par ce type de liaison Let est appelée « module de *reconnaissance actif*».</span><span class="sxs-lookup"><span data-stu-id="2399c-112">The (| and |) symbols are referred to as *banana clips* and the function created by this type of let binding is called an *active recognizer*.</span></span>

<span data-ttu-id="2399c-113">Par exemple, considérez le modèle actif suivant avec un argument.</span><span class="sxs-lookup"><span data-stu-id="2399c-113">As an example, consider the following active pattern with an argument.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5001.fs)]

<span data-ttu-id="2399c-114">Vous pouvez utiliser le modèle actif dans une expression de critères spéciaux, comme dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="2399c-114">You can use the active pattern in a pattern matching expression, as in the following example.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5002.fs)]

<span data-ttu-id="2399c-115">Le résultat de ce programme est le suivant :</span><span class="sxs-lookup"><span data-stu-id="2399c-115">The output of this program is as follows:</span></span>

```console
7 is odd
11 is odd
32 is even
```

<span data-ttu-id="2399c-116">Une autre utilisation des modèles actifs consiste à décomposer les types de données de plusieurs façons, par exemple quand les mêmes données sous-jacentes ont différentes représentations possibles.</span><span class="sxs-lookup"><span data-stu-id="2399c-116">Another use of active patterns is to decompose data types in multiple ways, such as when the same underlying data has various possible representations.</span></span> <span data-ttu-id="2399c-117">Par exemple, un objet `Color` peut être décomposé dans une représentation RGB ou une représentation TSL.</span><span class="sxs-lookup"><span data-stu-id="2399c-117">For example, a `Color` object could be decomposed into an RGB representation or an HSB representation.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5003.fs)]

<span data-ttu-id="2399c-118">La sortie du programme ci-dessus est la suivante :</span><span class="sxs-lookup"><span data-stu-id="2399c-118">The output of the above program is as follows:</span></span>

```console
Red
 Red: 255 Green: 0 Blue: 0
 Hue: 360.000000 Saturation: 1.000000 Brightness: 0.500000
Black
 Red: 0 Green: 0 Blue: 0
 Hue: 0.000000 Saturation: 0.000000 Brightness: 0.000000
White
 Red: 255 Green: 255 Blue: 255
 Hue: 0.000000 Saturation: 0.000000 Brightness: 1.000000
Gray
 Red: 128 Green: 128 Blue: 128
 Hue: 0.000000 Saturation: 0.000000 Brightness: 0.501961
BlanchedAlmond
 Red: 255 Green: 235 Blue: 205
 Hue: 36.000000 Saturation: 1.000000 Brightness: 0.901961
```

<span data-ttu-id="2399c-119">En combinaison, ces deux méthodes d’utilisation des modèles actifs vous permettent de partitionner et de décomposer des données sous la forme appropriée et d’effectuer les calculs appropriés sur les données appropriées au format le plus pratique pour le calcul.</span><span class="sxs-lookup"><span data-stu-id="2399c-119">In combination, these two ways of using active patterns enable you to partition and decompose data into just the appropriate form and perform the appropriate computations on the appropriate data in the form most convenient for the computation.</span></span>

<span data-ttu-id="2399c-120">Les expressions de critères spéciaux qui en résultent permettent d’écrire des données de manière pratique et très lisible, ce qui simplifie considérablement le code d’analyse de données et de branchement potentiellement complexe.</span><span class="sxs-lookup"><span data-stu-id="2399c-120">The resulting pattern matching expressions enable data to be written in a convenient way that is very readable, greatly simplifying potentially complex branching and data analysis code.</span></span>

## <a name="partial-active-patterns"></a><span data-ttu-id="2399c-121">Modèles actifs partiels</span><span class="sxs-lookup"><span data-stu-id="2399c-121">Partial Active Patterns</span></span>

<span data-ttu-id="2399c-122">Parfois, vous devez partitionner uniquement une partie de l’espace d’entrée.</span><span class="sxs-lookup"><span data-stu-id="2399c-122">Sometimes, you need to partition only part of the input space.</span></span> <span data-ttu-id="2399c-123">Dans ce cas, vous écrivez un ensemble de modèles partiels, chacun d’entre eux correspondant à des entrées, mais ne parviennent pas à mettre en correspondance d’autres entrées.</span><span class="sxs-lookup"><span data-stu-id="2399c-123">In that case, you write a set of partial patterns each of which match some inputs but fail to match other inputs.</span></span> <span data-ttu-id="2399c-124">Les modèles actifs qui ne produisent pas toujours une valeur sont appelés *modèles actifs partiels*; elles ont une valeur de retour qui est un type d’option.</span><span class="sxs-lookup"><span data-stu-id="2399c-124">Active patterns that do not always produce a value are called *partial active patterns*; they have a return value that is an option type.</span></span> <span data-ttu-id="2399c-125">Pour définir un modèle actif partiel, vous utilisez un caractère générique (\_) à la fin de la liste de modèles à l’intérieur des éléments de la banane.</span><span class="sxs-lookup"><span data-stu-id="2399c-125">To define a partial active pattern, you use a wildcard character (\_) at the end of the list of patterns inside the banana clips.</span></span> <span data-ttu-id="2399c-126">Le code suivant illustre l’utilisation d’un modèle actif partiel.</span><span class="sxs-lookup"><span data-stu-id="2399c-126">The following code illustrates the use of a partial active pattern.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5004.fs)]

<span data-ttu-id="2399c-127">La sortie de l’exemple précédent est la suivante :</span><span class="sxs-lookup"><span data-stu-id="2399c-127">The output of the previous example is as follows:</span></span>

```console
1.100000 : Floating point
0 : Integer
0.000000 : Floating point
10 : Integer
Something else : Not matched.
```

<span data-ttu-id="2399c-128">Lorsque vous utilisez des modèles actifs partiels, les choix individuels peuvent être disjoints ou mutuellement exclusifs, mais ils n’ont pas besoin d’être.</span><span class="sxs-lookup"><span data-stu-id="2399c-128">When using partial active patterns, sometimes the individual choices can be disjoint or mutually exclusive, but they need not be.</span></span> <span data-ttu-id="2399c-129">Dans l’exemple suivant, le modèle Square et le cube pattern ne sont pas disjoint, car certains nombres sont à la fois des carrés et des cubes, par exemple 64.</span><span class="sxs-lookup"><span data-stu-id="2399c-129">In the following example, the pattern Square and the pattern Cube are not disjoint, because some numbers are both squares and cubes, such as 64.</span></span> <span data-ttu-id="2399c-130">Le programme suivant utilise le modèle et pour combiner les modèles de carré et de cube.</span><span class="sxs-lookup"><span data-stu-id="2399c-130">The following program uses the AND pattern to combine the Square and Cube patterns.</span></span> <span data-ttu-id="2399c-131">Il imprime tous les entiers jusqu’à 1000 qui sont tous deux des carrés et des cubes, ainsi que ceux qui ne sont que des cubes.</span><span class="sxs-lookup"><span data-stu-id="2399c-131">It print out all integers up to 1000 that are both squares and cubes, as well as those which are only cubes.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5005.fs)]

<span data-ttu-id="2399c-132">La sortie est la suivante :</span><span class="sxs-lookup"><span data-stu-id="2399c-132">The output is as follows:</span></span>

```console
1 is a cube and a square
8 is a cube
27 is a cube
64 is a cube and a square
125 is a cube
216 is a cube
343 is a cube
512 is a cube
729 is a cube and a square
1000 is a cube
```

## <a name="parameterized-active-patterns"></a><span data-ttu-id="2399c-133">Modèles actifs paramétrés</span><span class="sxs-lookup"><span data-stu-id="2399c-133">Parameterized Active Patterns</span></span>

<span data-ttu-id="2399c-134">Les modèles actifs prennent toujours au moins un argument pour l’élément qui est mis en correspondance, mais ils peuvent également prendre des arguments supplémentaires, auquel cas le *modèle actif paramétré* pour le nom s’applique.</span><span class="sxs-lookup"><span data-stu-id="2399c-134">Active patterns always take at least one argument for the item being matched, but they may take additional arguments as well, in which case the name *parameterized active pattern* applies.</span></span> <span data-ttu-id="2399c-135">Les arguments supplémentaires permettent à un modèle général d’être spécialisé.</span><span class="sxs-lookup"><span data-stu-id="2399c-135">Additional arguments allow a general pattern to be specialized.</span></span> <span data-ttu-id="2399c-136">Par exemple, les modèles actifs qui utilisent des expressions régulières pour analyser des chaînes incluent souvent l’expression régulière comme paramètre supplémentaire, comme dans le code suivant, qui utilise également le modèle actif partiel `Integer` défini dans l’exemple de code précédent.</span><span class="sxs-lookup"><span data-stu-id="2399c-136">For example, active patterns that use regular expressions to parse strings often include the regular expression as an extra parameter, as in the following code, which also uses the partial active pattern `Integer` defined in the previous code example.</span></span> <span data-ttu-id="2399c-137">Dans cet exemple, les chaînes qui utilisent des expressions régulières pour différents formats de date sont fournies pour personnaliser le modèle actif ParseRegex général.</span><span class="sxs-lookup"><span data-stu-id="2399c-137">In this example, strings that use regular expressions for various date formats are given to customize the general ParseRegex active pattern.</span></span> <span data-ttu-id="2399c-138">Le modèle actif entier est utilisé pour convertir les chaînes mises en correspondance en entiers qui peuvent être passés au constructeur DateTime.</span><span class="sxs-lookup"><span data-stu-id="2399c-138">The Integer active pattern is used to convert the matched strings into integers that can be passed to the DateTime constructor.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5006.fs)]

<span data-ttu-id="2399c-139">La sortie du code précédent est la suivante :</span><span class="sxs-lookup"><span data-stu-id="2399c-139">The output of the previous code is as follows:</span></span>

```console
12/22/2008 12:00:00 AM 1/1/2009 12:00:00 AM 1/15/2008 12:00:00 AM 12/28/1995 12:00:00 AM
```

<span data-ttu-id="2399c-140">Les modèles actifs ne sont pas limités uniquement aux expressions de critères spéciaux, vous pouvez également les utiliser dans les liaisons Let.</span><span class="sxs-lookup"><span data-stu-id="2399c-140">Active patterns are not restricted only to pattern matching expressions, you can also use them on let-bindings.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5007.fs)]

<span data-ttu-id="2399c-141">La sortie du code précédent est la suivante :</span><span class="sxs-lookup"><span data-stu-id="2399c-141">The output of the previous code is as follows:</span></span>

```console
Hello, random citizen!
Hello, George!
```

## <a name="see-also"></a><span data-ttu-id="2399c-142">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2399c-142">See also</span></span>

- [<span data-ttu-id="2399c-143">Informations de référence sur le langage F#</span><span class="sxs-lookup"><span data-stu-id="2399c-143">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="2399c-144">Expressions match</span><span class="sxs-lookup"><span data-stu-id="2399c-144">Match Expressions</span></span>](match-expressions.md)
