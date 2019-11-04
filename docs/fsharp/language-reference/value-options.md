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

Il existe actuellement une fonction liée à un module pour les options de valeur, `defaultValueArg`:

```fsharp
val defaultValueArg : arg:'T voption -> defaultValue:'T -> 'T
```

Comme avec la fonction `defaultArg`, `defaultValueArg` retourne la valeur sous-jacente de l’option de valeur donnée, le cas échéant. Sinon, elle retourne la valeur par défaut spécifiée.

À ce stade, il n’y a pas d’autres fonctions liées aux modules pour les options de valeur.

## <a name="see-also"></a>Voir aussi

- [Options](options.md)
