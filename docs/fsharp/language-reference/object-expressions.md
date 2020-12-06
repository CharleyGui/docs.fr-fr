---
title: Expressions d'objet
description: 'Apprenez à utiliser des expressions d’objet F # lorsque vous souhaitez éviter le code supplémentaire et la surcharge nécessaires à la création d’un nouveau type nommé.'
ms.date: 02/08/2019
ms.openlocfilehash: 8a3e40b7833b551eefb95ec62b935acd1ba7b1f9
ms.sourcegitcommit: ecd9e9bb2225eb76f819722ea8b24988fe46f34c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2020
ms.locfileid: "96740300"
---
# <a name="object-expressions"></a>Expressions d'objet

Une *expression d’objet* est une expression qui crée une nouvelle instance d’un type d’objet anonyme créé dynamiquement qui est basé sur un type de base, une interface ou un ensemble d’interfaces existant.

## <a name="syntax"></a>Syntaxe

```fsharp
// When typename is a class:
{ new typename [type-params]arguments with
    member-definitions
    [ additional-interface-definitions ]
}
// When typename is not a class:
{ new typename [generic-type-args] with
    member-definitions
    [ additional-interface-definitions ]
}
```

## <a name="remarks"></a>Notes

Dans la syntaxe précédente, *TypeName* représente un type de classe ou d’interface existant. *type-params* décrit les paramètres de type générique facultatifs. Les *arguments* sont utilisés uniquement pour les types de classe, qui requièrent des paramètres de constructeur. Les *définitions de membres* sont des substitutions de méthodes de classe de base ou des implémentations de méthodes abstraites à partir d’une classe de base ou d’une interface.

L’exemple suivant illustre plusieurs types différents d’expressions d’objet.

```fsharp
// This object expression specifies a System.Object but overrides the
// ToString method.
let obj1 = { new System.Object() with member x.ToString() = "F#" }
printfn $"{obj1}"

// This object expression implements the IFormattable interface.
let delimiter(delim1: string, delim2: string, value: string) =
    { new System.IFormattable with
        member x.ToString(format: string, provider: System.IFormatProvider) =
            if format = "D" then
                delim1 + value + delim2
            else
                value }

let obj2 = delimiter("{","}", "Bananas!");

printfn "%A" (System.String.Format("{0:D}", obj2))

// Define two interfaces
type IFirst =
  abstract F : unit -> unit
  abstract G : unit -> unit

type ISecond =
  inherit IFirst
  abstract H : unit -> unit
  abstract J : unit -> unit

// This object expression implements both interfaces.
let implementer() =
    { new ISecond with
        member this.H() = ()
        member this.J() = ()
      interface IFirst with
        member this.F() = ()
        member this.G() = () }
```

## <a name="using-object-expressions"></a>Utilisation d’expressions d’objet

Vous utilisez des expressions d’objet lorsque vous souhaitez éviter le code et la surcharge supplémentaires requis pour créer un nouveau type nommé. Si vous utilisez des expressions d’objet pour réduire le nombre de types créés dans un programme, vous pouvez réduire le nombre de lignes de code et empêcher la prolifération inutile des types. Au lieu de créer de nombreux types juste pour gérer des situations spécifiques, vous pouvez utiliser une expression d’objet qui personnalise un type existant ou fournit une implémentation appropriée d’une interface pour le cas spécifique.

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur le langage F #](index.md)
