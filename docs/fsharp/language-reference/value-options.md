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
# <a name="value-options"></a>Options de valeurs

Le type d’option de F# valeur dans est utilisé lorsque les deux circonstances suivantes détiennent :

1. Un scénario est approprié pour une [ F# option](options.md).
2. L’utilisation d’un struct offre un avantage en matière de performances dans votre scénario.

Les scénarios dépendants de la performance ne sont pas tous « résolus » en utilisant des structs. Vous devez prendre en compte le coût supplémentaire lié à la copie lorsque vous les utilisez au lieu de types référence. Toutefois, les F# grands programmes instancient généralement de nombreux types facultatifs qui transitent par des chemins d’accès à chaud. dans ce cas, les structs peuvent souvent améliorer les performances globales pendant la durée de vie d’un programme.

## <a name="definition"></a>Définition

L’option value est définie sous la forme d’une [union discriminée struct](discriminated-unions.md#struct-discriminated-unions) similaire au type d’option de référence. Sa définition peut être considérée de la façon suivante :

```fsharp
[<StructuralEquality; StructuralComparison>]
[<Struct>]
type ValueOption<'T> =
    | ValueNone
    | ValueSome of 'T
```

L’option value est conforme à l’égalité structurelle et à la comparaison. La principale différence est que le nom compilé, le nom de type et les noms de cas indiquent tous qu’il s’agit d’un type valeur.

## <a name="using-value-options"></a>Utilisation des options de valeur

Les options de valeur sont utilisées de la même façon que les [options](options.md). `ValueSome` est utilisé pour indiquer qu’une valeur est présente, et `ValueNone` est utilisée lorsqu’une valeur n’est pas présente :

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

Comme avec les [options](options.md), la Convention d’affectation de noms pour une fonction qui retourne `ValueOption` consiste à le préfixer avec `try`.

## <a name="value-option-properties-and-methods"></a>Propriétés et méthodes de l’option value

Il existe une propriété pour les options de valeur pour l’instant : `Value`. Un <xref:System.InvalidOperationException> est déclenché si aucune valeur n’est présente lorsque cette propriété est appelée.

## <a name="value-option-functions"></a>Fonctions de l’option value

Le module `ValueOption` dans FSharp. Core contient des fonctionnalités équivalentes à celles du module `Option`. Il existe quelques différences dans le nom, par exemple `defaultValueArg`:

```fsharp
val defaultValueArg : arg:'T voption -> defaultValue:'T -> 'T
```

Cela se fait de la même façon que `defaultArg` dans le module `Option`, mais fonctionne à la place sur une option de valeur.

## <a name="see-also"></a>Voir aussi

- [Options](options.md)
