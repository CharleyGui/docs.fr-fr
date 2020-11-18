---
title: Chaînes interpolées
description: 'En savoir plus sur les chaînes interpolées, une forme spéciale de chaîne qui vous permet d’incorporer des expressions F # directement à l’intérieur de celles-ci.'
ms.date: 11/12/2020
ms.openlocfilehash: a49d4e743306fd9bdabb1e019ec4e6c77e0e1f5a
ms.sourcegitcommit: 34968a61e9bac0f6be23ed6ffb837f52d2390c85
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94688601"
---
# <a name="interpolated-strings"></a>Chaînes interpolées

Les chaînes interpolées sont des [chaînes](strings.md) qui vous permettent d’incorporer des expressions F # dans celles-ci. Elles sont utiles dans un large éventail de scénarios où la valeur d’une chaîne peut changer selon le résultat d’une valeur ou d’une expression.

## <a name="syntax"></a>Syntaxe

```fsharp
$"string-text {expr}"
$"string-text %format-specifier{expr}"
$"""string-text {"embedded string literal"}"""
```

## <a name="remarks"></a>Notes

Les chaînes interpolées vous permettent d’écrire du code dans des « trous » à l’intérieur d’un littéral de chaîne. Voici un exemple de base :

```fsharp
let name = "Phillip"
let age = 30
printfn $"Name: {name}, Age: {age}"

printfn $"I think {3.0 + 0.14} is close to {System.Math.PI}!"
```

Le contenu entre chaque `{}` paire d’accolades peut être n’importe quelle expression F #.

Pour échapper à une `{}` paire d’accolades, écrivez deux d’entre eux comme suit :

```fsharp
let str = $"A pair of braces: {{}}"
// "A pair of braces: {}"
```

## <a name="typed-interpolated-strings"></a>Chaînes interpolées typées

Les chaînes interpolées peuvent également avoir des spécificateurs de format F # pour appliquer le type safe.

```fsharp
let name = "Phillip"
let age = 30

printfn $"Name: %s{name}, Age: %d{age}"

// Error: type mismatch
printfn $"Name: %s{age}, Age: %d{name}"
```

Dans l’exemple précédent, le code passe par erreur la `age` valeur où `name` doit être, et vice/versa. Étant donné que les chaînes interpolées utilisent des spécificateurs de format, il s’agit d’une erreur de compilation au lieu d’un bogue de Runtime discret.

Tous les spécificateurs de format couverts dans la [mise en forme de texte en clair](plaintext-formatting.md) sont valides dans une chaîne interpolée.

## <a name="verbatim-interpolated-strings"></a>Chaînes interpolées Verbatim

F # prend en charge les chaînes interpolées Verbatim avec des guillemets triples afin que vous puissiez incorporer des littéraux de chaîne.

```fsharp
let age = 30

printfn $"""Name: {"Phillip"}, Age: %d{age}"""
```

## <a name="aligning-expressions-in-interpolated-strings"></a>Alignement d’expressions dans des chaînes interpolées

Vous pouvez aligner les expressions à gauche ou à droite à l’intérieur des chaînes interpolées avec `|` et une spécification du nombre d’espaces. La chaîne interpolée suivante aligne les expressions de gauche et de droite à gauche et à droite, respectivement, sur 7 espaces.

```fsharp
printfn $"""|{"Left",-7}|{"Right",7}|"""
// |Left   |  Right|
```

## <a name="interpolated-strings-and-formattablestring-formatting"></a>Chaînes interpolées et `FormattableString` mise en forme

Vous pouvez également appliquer une mise en forme conforme aux règles pour <xref:System.FormattableString> :

```fsharp
let speedOfLight = 299792.458
printfn $"The speed of light is {speedOfLight:N3} km/s."
// "The speed of light is 299,792.458 km/s."
```

En outre, une chaîne interpolée peut également être typechecked comme un <xref:System.FormattableString> via une annotation de type :

```fsharp
let frmtStr = $"The speed of light is {speedOfLight:N3} km/s." : FormattableString
// Type: FormattableString
// The speed of light is 299,792.458 km/s.
```

Notez que l’annotation de type doit se trouver sur l’expression de chaîne interpolée elle-même. F # ne convertit pas implicitement une chaîne interpolée en <xref:System.FormattableString> .

## <a name="see-also"></a>Voir aussi

* [Chaînes](strings.md)
