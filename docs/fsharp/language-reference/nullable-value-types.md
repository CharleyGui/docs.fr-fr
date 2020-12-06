---
title: Types valeur Nullable
description: 'Découvrez comment utiliser les types valeur Nullable, un moyen de représenter un type valeur qui peut également être null, en F #.'
ms.date: 11/19/2020
ms.openlocfilehash: da0cd85bd651db81ba98c02a9db31d92dc52a8c6
ms.sourcegitcommit: ecd9e9bb2225eb76f819722ea8b24988fe46f34c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2020
ms.locfileid: "96740405"
---
# <a name="nullable-value-types"></a>Types valeur Nullable

Un _type valeur Nullable_ `Nullable<'T>` représente tout type [struct](structures.md) qui peut également être `null` . Cela est utile lors de l’interaction avec des bibliothèques et des composants qui peuvent choisir de représenter ces genres de types, comme des entiers, avec une `null` valeur pour des raisons d’efficacité. Le type sous-jacent qui stocke cette construction est <xref:System.Nullable%601?displayProperty=nameWithType> .

## <a name="syntax"></a>Syntaxe

```fsharp
Nullable<'T>
Nullable value
```

## <a name="declare-and-assign-with-values"></a>Déclarer et assigner avec des valeurs

La déclaration d’un type valeur Nullable est semblable à la déclaration d’un type de type wrapper en F # :

```fsharp
open System

let x = 12
let nullableX = Nullable<int> x
```

Vous pouvez également Elide le paramètre de type générique et autoriser l’inférence de type à le résoudre :

```fsharp
open System

let x = 12
let nullableX = Nullable x
```

Pour assigner à un type valeur Nullable, vous devez également être explicite. Il n’existe pas de conversion implicite pour les types valeur Nullable définis en F # :

```fsharp
open System

let mutable x = Nullable 12
x <- Nullable 13
```

## <a name="assign-null"></a>Affecter une valeur null

Vous ne pouvez pas assigner directement `null` à un type valeur Nullable. À utiliser à la `Nullable()` place :

```fsharp
let mutable a = Nullable 42
a <- Nullable()
```

Cela est dû au fait que `Nullable<'T>` ne dispose pas `null` de la valeur appropriée.

## <a name="pass-and-assign-to-members"></a>Passer et assigner à des membres

La principale différence entre l’utilisation des membres et des valeurs F # est que les types valeur Nullable peuvent être implicitement déduits lorsque vous utilisez des membres. Considérez la méthode folling qui accepte un type valeur Nullable comme entrée :

```fsharp
type C() =
    member _.M(x: Nullable<int>) = x.HasValue
    member val NVT = Nullable 12 with get, set

let c = C()
c.M(12)
c.NVT <- 12
```

Dans l’exemple précédent, vous pouvez passer `12` à la méthode `M` . Vous pouvez également assigner `12` à la propriété auto `NVT` . Le compilateur F # convertit implicitement un appel ou une assignation comme suit lorsque le type cible correspond à l’entrée, si l’entrée peut être construite comme un type de valeur nullabel.

## <a name="examine-a-nullable-value-type-instance"></a>Examiner une instance de type valeur Nullable

Contrairement aux [options](options.md), qui sont une construction généralisée pour représenter une valeur possible, les types valeur Nullable ne sont pas utilisés avec les critères spéciaux. Au lieu de cela, vous devez utiliser une [`if`](conditional-expressions-if-then-else.md) expression et vérifier la `HasValue` propriété.

Pour obtenir la valeur sous-jacente, utilisez la `Value` propriété après une `HasValue` vérification, comme suit :

```fsharp
open System

let a = Nullable 42

if a.HasValue then
    printfn $"{a} is {a.Value}"
else
    printfn $"{a} has no value."
```

## <a name="nullable-operators"></a>Opérateurs Nullable

Les opérations sur les types valeur Nullable, telles que l’arithmétique ou la comparaison, peuvent nécessiter l’utilisation d' [opérateurs Nullable](symbol-and-operator-reference/nullable-operators.md).

Vous pouvez convertir un type valeur Nullable en un autre à l’aide des opérateurs de conversion de l' `FSharp.Linq` espace de noms :

```fsharp
open System
open FSharp.Linq

let nullableInt = Nullable 10
let nullableFloat = Nullable.float nullableInt
```

Vous pouvez également utiliser un opérateur non Nullable approprié pour effectuer une conversion vers un type primitif, ce qui risque d’être une exception s’il n’a pas de valeur :

```fsharp
open System
open FSharp.Linq

let nullableInt = Nullable 10
let nullableFloat = Nullable.float nullableInt

printfn $"value is %f{float nullableFloat}"
```

Vous pouvez également utiliser des opérateurs Nullable comme un raccourci pour vérifier `HasValue` et `Value` :

```fsharp
open System
open FSharp.Linq

let nullableInt = Nullable 10
let nullableFloat = Nullable.float nullableInt

let isBigger = nullableFloat ?> 1.0
let isBiggerLongForm = nullableFloat.HasValue && nullableFloat.Value > 1.0
```

La `?>` comparaison vérifie si le côté gauche est Nullable et s’il a une valeur uniquement si elle a une valeur. Elle est équivalente à la ligne qui la suit.

## <a name="see-also"></a>Voir aussi

- [Structures](structures.md)
- [Options F #](options.md)
