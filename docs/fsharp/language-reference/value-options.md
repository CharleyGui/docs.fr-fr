---
title: Options de valeurs
description: En savoir plus F# sur le type d’option de valeur, qui est une version struct du type d’option.
ms.date: 02/06/2019
ms.openlocfilehash: 4dc3f7217943345b7aaf1165fd648ab2e01bd727
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424017"
---
# <a name="value-options"></a><span data-ttu-id="bf7ee-103">Options de valeurs</span><span class="sxs-lookup"><span data-stu-id="bf7ee-103">Value Options</span></span>

<span data-ttu-id="bf7ee-104">Le type d’option de F# valeur dans est utilisé lorsque les deux circonstances suivantes détiennent :</span><span class="sxs-lookup"><span data-stu-id="bf7ee-104">The Value Option type in F# is used when the following two circumstances hold:</span></span>

1. <span data-ttu-id="bf7ee-105">Un scénario est approprié pour une [ F# option](options.md).</span><span class="sxs-lookup"><span data-stu-id="bf7ee-105">A scenario is appropriate for an [F# Option](options.md).</span></span>
2. <span data-ttu-id="bf7ee-106">L’utilisation d’un struct offre un avantage en matière de performances dans votre scénario.</span><span class="sxs-lookup"><span data-stu-id="bf7ee-106">Using a struct provides a performance benefit in your scenario.</span></span>

<span data-ttu-id="bf7ee-107">Les scénarios dépendants de la performance ne sont pas tous « résolus » en utilisant des structs.</span><span class="sxs-lookup"><span data-stu-id="bf7ee-107">Not all performance-sensitive scenarios are "solved" by using structs.</span></span> <span data-ttu-id="bf7ee-108">Vous devez prendre en compte le coût supplémentaire lié à la copie lorsque vous les utilisez au lieu de types référence.</span><span class="sxs-lookup"><span data-stu-id="bf7ee-108">You must consider the additional cost of copying when using them instead of reference types.</span></span> <span data-ttu-id="bf7ee-109">Toutefois, les F# grands programmes instancient généralement de nombreux types facultatifs qui transitent par des chemins d’accès à chaud. dans ce cas, les structs peuvent souvent améliorer les performances globales pendant la durée de vie d’un programme.</span><span class="sxs-lookup"><span data-stu-id="bf7ee-109">However, large F# programs commonly instantiate many optional types that flow through hot paths, and in such cases, structs can often yield better overall performance over the lifetime of a program.</span></span>

## <a name="definition"></a><span data-ttu-id="bf7ee-110">Définition</span><span class="sxs-lookup"><span data-stu-id="bf7ee-110">Definition</span></span>

<span data-ttu-id="bf7ee-111">L’option value est définie sous la forme d’une [union discriminée struct](discriminated-unions.md#struct-discriminated-unions) similaire au type d’option de référence.</span><span class="sxs-lookup"><span data-stu-id="bf7ee-111">Value Option is defined as a [struct discriminated union](discriminated-unions.md#struct-discriminated-unions) that is similar to the reference option type.</span></span> <span data-ttu-id="bf7ee-112">Sa définition peut être considérée de la façon suivante :</span><span class="sxs-lookup"><span data-stu-id="bf7ee-112">Its definition can be thought of this way:</span></span>

```fsharp
[<StructuralEquality; StructuralComparison>]
[<Struct>]
type ValueOption<'T> =
    | ValueNone
    | ValueSome of 'T
```

<span data-ttu-id="bf7ee-113">L’option value est conforme à l’égalité structurelle et à la comparaison.</span><span class="sxs-lookup"><span data-stu-id="bf7ee-113">Value Option conforms to structural equality and comparison.</span></span> <span data-ttu-id="bf7ee-114">La principale différence est que le nom compilé, le nom de type et les noms de cas indiquent tous qu’il s’agit d’un type valeur.</span><span class="sxs-lookup"><span data-stu-id="bf7ee-114">The main difference is that the compiled name, type name, and case names all indicate that it is a value type.</span></span>

## <a name="using-value-options"></a><span data-ttu-id="bf7ee-115">Utilisation des options de valeur</span><span class="sxs-lookup"><span data-stu-id="bf7ee-115">Using Value Options</span></span>

<span data-ttu-id="bf7ee-116">Les options de valeur sont utilisées de la même façon que les [options](options.md).</span><span class="sxs-lookup"><span data-stu-id="bf7ee-116">Value Options are used just like [Options](options.md).</span></span> <span data-ttu-id="bf7ee-117">`ValueSome` est utilisé pour indiquer qu’une valeur est présente, et `ValueNone` est utilisée lorsqu’une valeur n’est pas présente :</span><span class="sxs-lookup"><span data-stu-id="bf7ee-117">`ValueSome` is used to indicate that a value is present, and `ValueNone` is used when a value is not present:</span></span>

```fsharp
let tryParseDateTime (s: string) =
    match System.DateTime.TryParse(s) with
    | (true, dt) -> ValueSome dt
    | (false, _) -> ValueNone

let possibleDateString1 = "1990-12-25"
let possibleDateString2 = "This is not a date"

let result1 = tryParseDateTime possibleDateString1
let result2 = tryParseDateTime possibleDateString2

match (result1, result2) with
| ValueSome d1, ValueSome d2 -> printfn "Both are dates!"
| ValueSome d1, ValueNone -> printfn "Only the first is a date!"
| ValueNone, ValueSome d2 -> printfn "Only the second is a date!"
| ValueNone, ValueNone -> printfn "None of them are dates!"
```

<span data-ttu-id="bf7ee-118">Comme avec les [options](options.md), la Convention d’affectation de noms pour une fonction qui retourne `ValueOption` consiste à le préfixer avec `try`.</span><span class="sxs-lookup"><span data-stu-id="bf7ee-118">As with [Options](options.md), the naming convention for a function that returns `ValueOption` is to prefix it with `try`.</span></span>

## <a name="value-option-properties-and-methods"></a><span data-ttu-id="bf7ee-119">Propriétés et méthodes de l’option value</span><span class="sxs-lookup"><span data-stu-id="bf7ee-119">Value Option properties and methods</span></span>

<span data-ttu-id="bf7ee-120">Il existe une propriété pour les options de valeur pour l’instant : `Value`.</span><span class="sxs-lookup"><span data-stu-id="bf7ee-120">There is one property for Value Options at this time: `Value`.</span></span> <span data-ttu-id="bf7ee-121">Un <xref:System.InvalidOperationException> est déclenché si aucune valeur n’est présente lorsque cette propriété est appelée.</span><span class="sxs-lookup"><span data-stu-id="bf7ee-121">An <xref:System.InvalidOperationException> is raised if no value is present when this property is invoked.</span></span>

## <a name="value-option-functions"></a><span data-ttu-id="bf7ee-122">Fonctions de l’option value</span><span class="sxs-lookup"><span data-stu-id="bf7ee-122">Value Option functions</span></span>

<span data-ttu-id="bf7ee-123">Il existe actuellement une fonction liée à un module pour les options de valeur, `defaultValueArg`:</span><span class="sxs-lookup"><span data-stu-id="bf7ee-123">There is currently one module-bound function for Value Options, `defaultValueArg`:</span></span>

```fsharp
val defaultValueArg : arg:'T voption -> defaultValue:'T -> 'T
```

<span data-ttu-id="bf7ee-124">Comme avec la fonction `defaultArg`, `defaultValueArg` retourne la valeur sous-jacente de l’option de valeur donnée, le cas échéant. Sinon, elle retourne la valeur par défaut spécifiée.</span><span class="sxs-lookup"><span data-stu-id="bf7ee-124">As with the `defaultArg` function, `defaultValueArg` returns the underlying value of the given Value Option if it exists; otherwise, it returns the specified default value.</span></span>

<span data-ttu-id="bf7ee-125">À ce stade, il n’y a pas d’autres fonctions liées aux modules pour les options de valeur.</span><span class="sxs-lookup"><span data-stu-id="bf7ee-125">At this time, there are no other module-bound functions for Value Options.</span></span>

## <a name="see-also"></a><span data-ttu-id="bf7ee-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bf7ee-126">See also</span></span>

- [<span data-ttu-id="bf7ee-127">Options</span><span class="sxs-lookup"><span data-stu-id="bf7ee-127">Options</span></span>](options.md)
