---
title: Options de valeurs
description: En savoir plus F# sur le type d’option de valeur, qui est une version struct du type d’option.
ms.date: 12/04/2019
ms.openlocfilehash: 0e9882ab4acdf2757705ef6022516d3572d87ef2
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837114"
---
# <a name="value-options"></a><span data-ttu-id="d00e3-103">Options de valeurs</span><span class="sxs-lookup"><span data-stu-id="d00e3-103">Value Options</span></span>

<span data-ttu-id="d00e3-104">Le type d’option de F# valeur dans est utilisé lorsque les deux circonstances suivantes détiennent :</span><span class="sxs-lookup"><span data-stu-id="d00e3-104">The Value Option type in F# is used when the following two circumstances hold:</span></span>

1. <span data-ttu-id="d00e3-105">Un scénario est approprié pour une [ F# option](options.md).</span><span class="sxs-lookup"><span data-stu-id="d00e3-105">A scenario is appropriate for an [F# Option](options.md).</span></span>
2. <span data-ttu-id="d00e3-106">L’utilisation d’un struct offre un avantage en matière de performances dans votre scénario.</span><span class="sxs-lookup"><span data-stu-id="d00e3-106">Using a struct provides a performance benefit in your scenario.</span></span>

<span data-ttu-id="d00e3-107">Les scénarios dépendants de la performance ne sont pas tous « résolus » en utilisant des structs.</span><span class="sxs-lookup"><span data-stu-id="d00e3-107">Not all performance-sensitive scenarios are "solved" by using structs.</span></span> <span data-ttu-id="d00e3-108">Vous devez prendre en compte le coût supplémentaire lié à la copie lorsque vous les utilisez au lieu de types référence.</span><span class="sxs-lookup"><span data-stu-id="d00e3-108">You must consider the additional cost of copying when using them instead of reference types.</span></span> <span data-ttu-id="d00e3-109">Toutefois, les F# grands programmes instancient généralement de nombreux types facultatifs qui transitent par des chemins d’accès à chaud. dans ce cas, les structs peuvent souvent améliorer les performances globales pendant la durée de vie d’un programme.</span><span class="sxs-lookup"><span data-stu-id="d00e3-109">However, large F# programs commonly instantiate many optional types that flow through hot paths, and in such cases, structs can often yield better overall performance over the lifetime of a program.</span></span>

## <a name="definition"></a><span data-ttu-id="d00e3-110">Définition</span><span class="sxs-lookup"><span data-stu-id="d00e3-110">Definition</span></span>

<span data-ttu-id="d00e3-111">L’option value est définie sous la forme d’une [union discriminée struct](discriminated-unions.md#struct-discriminated-unions) similaire au type d’option de référence.</span><span class="sxs-lookup"><span data-stu-id="d00e3-111">Value Option is defined as a [struct discriminated union](discriminated-unions.md#struct-discriminated-unions) that is similar to the reference option type.</span></span> <span data-ttu-id="d00e3-112">Sa définition peut être considérée de la façon suivante :</span><span class="sxs-lookup"><span data-stu-id="d00e3-112">Its definition can be thought of this way:</span></span>

```fsharp
[<StructuralEquality; StructuralComparison>]
[<Struct>]
type ValueOption<'T> =
    | ValueNone
    | ValueSome of 'T
```

<span data-ttu-id="d00e3-113">L’option value est conforme à l’égalité structurelle et à la comparaison.</span><span class="sxs-lookup"><span data-stu-id="d00e3-113">Value Option conforms to structural equality and comparison.</span></span> <span data-ttu-id="d00e3-114">La principale différence est que le nom compilé, le nom de type et les noms de cas indiquent tous qu’il s’agit d’un type valeur.</span><span class="sxs-lookup"><span data-stu-id="d00e3-114">The main difference is that the compiled name, type name, and case names all indicate that it is a value type.</span></span>

## <a name="using-value-options"></a><span data-ttu-id="d00e3-115">Utilisation des options de valeur</span><span class="sxs-lookup"><span data-stu-id="d00e3-115">Using Value Options</span></span>

<span data-ttu-id="d00e3-116">Les options de valeur sont utilisées de la même façon que les [options](options.md).</span><span class="sxs-lookup"><span data-stu-id="d00e3-116">Value Options are used just like [Options](options.md).</span></span> <span data-ttu-id="d00e3-117">`ValueSome` est utilisé pour indiquer qu’une valeur est présente, et `ValueNone` est utilisée lorsqu’une valeur n’est pas présente :</span><span class="sxs-lookup"><span data-stu-id="d00e3-117">`ValueSome` is used to indicate that a value is present, and `ValueNone` is used when a value is not present:</span></span>

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

<span data-ttu-id="d00e3-118">Comme avec les [options](options.md), la Convention d’affectation de noms pour une fonction qui retourne `ValueOption` consiste à le préfixer avec `try`.</span><span class="sxs-lookup"><span data-stu-id="d00e3-118">As with [Options](options.md), the naming convention for a function that returns `ValueOption` is to prefix it with `try`.</span></span>

## <a name="value-option-properties-and-methods"></a><span data-ttu-id="d00e3-119">Propriétés et méthodes de l’option value</span><span class="sxs-lookup"><span data-stu-id="d00e3-119">Value Option properties and methods</span></span>

<span data-ttu-id="d00e3-120">Il existe une propriété pour les options de valeur pour l’instant : `Value`.</span><span class="sxs-lookup"><span data-stu-id="d00e3-120">There is one property for Value Options at this time: `Value`.</span></span> <span data-ttu-id="d00e3-121">Un <xref:System.InvalidOperationException> est déclenché si aucune valeur n’est présente lorsque cette propriété est appelée.</span><span class="sxs-lookup"><span data-stu-id="d00e3-121">An <xref:System.InvalidOperationException> is raised if no value is present when this property is invoked.</span></span>

## <a name="value-option-functions"></a><span data-ttu-id="d00e3-122">Fonctions de l’option value</span><span class="sxs-lookup"><span data-stu-id="d00e3-122">Value Option functions</span></span>

<span data-ttu-id="d00e3-123">Le module `ValueOption` dans FSharp. Core contient des fonctionnalités équivalentes à celles du module `Option`.</span><span class="sxs-lookup"><span data-stu-id="d00e3-123">The `ValueOption` module in FSharp.Core contains equivalent functionality to the `Option` module.</span></span> <span data-ttu-id="d00e3-124">Il existe quelques différences dans le nom, par exemple `defaultValueArg`:</span><span class="sxs-lookup"><span data-stu-id="d00e3-124">There are a few differences in name, such as `defaultValueArg`:</span></span>

```fsharp
val defaultValueArg : arg:'T voption -> defaultValue:'T -> 'T
```

<span data-ttu-id="d00e3-125">Cela se fait de la même façon que `defaultArg` dans le module `Option`, mais fonctionne à la place sur une option de valeur.</span><span class="sxs-lookup"><span data-stu-id="d00e3-125">This acts just like `defaultArg` in the `Option` module, but operates on a Value Option instead.</span></span>

## <a name="see-also"></a><span data-ttu-id="d00e3-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d00e3-126">See also</span></span>

- [<span data-ttu-id="d00e3-127">Options</span><span class="sxs-lookup"><span data-stu-id="d00e3-127">Options</span></span>](options.md)
