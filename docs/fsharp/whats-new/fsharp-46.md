---
title: Nouveautés de F# 4,6- F# Guide
description: Bénéficiez d’une vue d’ensemble des nouvelles F# fonctionnalités disponibles dans 4,6.
ms.date: 11/27/2019
ms.openlocfilehash: 620c1edd8ea212fee306a02d5844b6b322808251
ms.sourcegitcommit: 19014f9c081ca2ff19652ca12503828db8239d48
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/04/2020
ms.locfileid: "76980390"
---
# <a name="whats-new-in-f-46"></a>Nouveautés de F# 4,6

F#4,6 ajoute plusieurs améliorations au F# langage.

## <a name="get-started"></a>Prise en main

F#4,6 est disponible dans toutes les distributions .NET Core et les outils Visual Studio. [Commencez avec F# ](../get-started/index.md) pour en savoir plus.

## <a name="anonymous-records"></a>Enregistrements anonymes

Les [enregistrements anonymes](../language-reference/anonymous-records.md) sont un nouveau F# genre de type F# introduit dans 4,6. Il s’agit d’agrégats simples de valeurs nommées qui n’ont pas besoin d’être déclarées avant d’être utilisées. Vous pouvez les déclarer comme des structs ou des types référence. Ils sont des types référence par défaut.

```fsharp
open System

let getCircleStats radius =
    let d = radius * 2.0
    let a = Math.PI * (radius ** 2.0)
    let c = 2.0 * Math.PI * radius

    {| Diameter = d; Area = a; Circumference = c |}

let r = 2.0
let stats = getCircleStats r
printfn "Circle with radius: %f has diameter %f, area %f, and circumference %f"
    r stats.Diameter stats.Area stats.Circumference
```

Elles peuvent également être déclarées comme structs pour lorsque vous souhaitez regrouper des types valeur et fonctionner dans des scénarios de performances :

```fsharp
open System

let getCircleStats radius =
    let d = radius * 2.0
    let a = Math.PI * (radius ** 2.0)
    let c = 2.0 * Math.PI * radius

    struct {| Diameter = d; Area = a; Circumference = c |}

let r = 2.0
let stats = getCircleStats r
printfn "Circle with radius: %f has diameter %f, area %f, and circumference %f"
    r stats.Diameter stats.Area stats.Circumference
```

Elles sont très puissantes et peuvent être utilisées dans de nombreux scénarios. En savoir plus sur les [enregistrements anonymes](../language-reference/anonymous-records.md).

## <a name="valueoption-functions"></a>ValueOption, fonctions

Le type ValueOption ajouté dans F# 4,5 a désormais « parité de fonction liée au module » avec le type d’option. Voici quelques exemples les plus couramment utilisés :

```fsharp
// Multiply a value option by 2 if it has  value
let xOpt = ValueSome 99
let result = xOpt |> ValueOption.map (fun v -> v * 2)

// Reverse a string if it exists
let strOpt = ValueSome "Mirror image"
let reverse (str: string) =
    match str with
    | null
    | "" -> ValueNone
    | s ->
        str.ToCharArray()
        |> Array.rev
        |> string
        |> ValueSome

let reversedString = strOpt |> ValueOption.bind reverse
```

Cela permet l’utilisation de ValueOption comme option dans les scénarios où un type valeur améliore les performances.
