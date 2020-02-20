---
title: Enregistrements anonymes
description: Apprenez à utiliser la construction et à utiliser des enregistrements anonymes, une fonctionnalité de langage qui facilite la manipulation des données.
ms.date: 06/12/2019
ms.openlocfilehash: 061fd3279c84b9a3161c687d9392947ee7ce9c83
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77453024"
---
# <a name="anonymous-records"></a>Enregistrements anonymes

Les enregistrements anonymes sont des agrégats simples de valeurs nommées qui n’ont pas besoin d’être déclarés avant leur utilisation. Vous pouvez les déclarer comme des structs ou des types référence. Ils sont des types référence par défaut.

## <a name="syntax"></a>Syntaxe

Les exemples suivants illustrent la syntaxe d’enregistrement anonyme. Les éléments délimités comme `[item]` sont facultatifs.

```fsharp
// Construct an anonymous record
let value-name = [struct] {| Label1: Type1; Label2: Type2; ...|}

// Use an anonymous record as a type parameter
let value-name = Type-Name<[struct] {| Label1: Type1; Label2: Type2; ...|}>

// Define a parameter with an anonymous record as input
let function-name (arg-name: [struct] {| Label1: Type1; Label2: Type2; ...|}) ...
```

## <a name="basic-usage"></a>Utilisation de base

Il est préférable de considérer les enregistrements F# anonymes comme des types d’enregistrements qui n’ont pas besoin d’être déclarés avant l’instanciation.

Par exemple, ici, vous pouvez interagir avec une fonction qui produit un enregistrement anonyme :

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

L’exemple suivant développe le précédent avec une fonction `printCircleStats` qui accepte un enregistrement anonyme comme entrée :

```fsharp
open System

let getCircleStats radius =
    let d = radius * 2.0
    let a = Math.PI * (radius ** 2.0)
    let c = 2.0 * Math.PI * radius

    {| Diameter = d; Area = a; Circumference = c |}

let printCircleStats r (stats: {| Area: float; Circumference: float; Diameter: float |}) =
    printfn "Circle with radius: %f has diameter %f, area %f, and circumference %f"
        r stats.Diameter stats.Area stats.Circumference

let r = 2.0
let stats = getCircleStats r
printCircleStats r stats
```

L’appel de `printCircleStats` avec un type d’enregistrement anonyme qui n’a pas la même « forme » comme type d’entrée ne peut pas être compilé :

```fsharp
printCircleStats r {| Diameter = 2.0; Area = 4.0; MyCircumference = 12.566371 |}
// Two anonymous record types have mismatched sets of field names
// '["Area"; "Circumference"; "Diameter"]' and '["Area"; "Diameter"; "MyCircumference"]'
```

## <a name="struct-anonymous-records"></a>Structurer des enregistrements anonymes

Les enregistrements anonymes peuvent également être définis comme struct avec le mot clé facultatif `struct`. L’exemple suivant augmente le précédent en générant et en consommant un enregistrement anonyme de structure :

```fsharp
open System

let getCircleStats radius =
    let d = radius * 2.0
    let a = Math.PI * (radius ** 2.0)
    let c = 2.0 * Math.PI * radius

    // Note that the keyword comes before the '{| |}' brace pair
    struct {| Area = a; Circumference = c; Diameter = d |}

// the 'struct' keyword also comes before the '{| |}' brace pair when declaring the parameter type
let printCircleStats r (stats: struct {| Area: float; Circumference: float; Diameter: float |}) =
    printfn "Circle with radius: %f has diameter %f, area %f, and circumference %f"
        r stats.Diameter stats.Area stats.Circumference

let r = 2.0
let stats = getCircleStats r
printCircleStats r stats
```

### <a name="structness-inference"></a>Inférence de la structure

Les enregistrements anonymes de struct autorisent également l’inférence de la structure, où vous n’avez pas besoin de spécifier le mot clé `struct` sur le site d’appel. Dans cet exemple, vous Elide le mot clé `struct` lors de l’appel de `printCircleStats`:

```fsharp

let printCircleStats r (stats: struct {| Area: float; Circumference: float; Diameter: float |}) =
    printfn "Circle with radius: %f has diameter %f, area %f, and circumference %f"
        r stats.Diameter stats.Area stats.Circumference

printCircleStats r {| Area = 4.0; Circumference = 12.6; Diameter = 12.6 |}
```

Le modèle inverse, qui spécifie `struct` lorsque le type d’entrée n’est pas un enregistrement anonyme de struct, ne peut pas être compilé.

## <a name="embedding-anonymous-records-within-other-types"></a>Incorporation d’enregistrements anonymes dans d’autres types

Il est utile de déclarer des [unions discriminées](discriminated-unions.md) dont les cas sont des enregistrements. Toutefois, si les données des enregistrements sont du même type que l’union discriminée, vous devez définir tous les types comme étant mutuellement récursifs. L’utilisation d’enregistrements anonymes évite cette restriction. Ce qui suit est un exemple de type et de fonction qui correspond au modèle :

```fsharp
type FullName = { FirstName: string; LastName: string }

// Note that using a named for Manager and Executive would require mutually recursive definitions.
type Employee =
    | Engineer of FullName
    | Manager of {| Name: FullName; Reports: Employee list |}
    | Executive of {| Name: FullName; Reports: Employee list; Assistant: Employee |}

let getFirstName e =
    match e with
    | Engineer fullName -> fullName.FirstName
    | Manager m -> m.Name.FirstName
    | Executive ex -> ex.Name.FirstName
```

## <a name="copy-and-update-expressions"></a>Copier et mettre à jour des expressions

Les enregistrements anonymes prennent en charge la construction avec des [expressions de copie et de mise à jour](copy-and-update-record-expressions.md). Par exemple, voici comment vous pouvez construire une nouvelle instance d’un enregistrement anonyme qui copie les données d’un existant :

```fsharp
let data = {| X = 1; Y = 2 |}
let data' = {| data with Y = 3 |}
```

Toutefois, contrairement aux enregistrements nommés, les enregistrements anonymes vous permettent de construire des formulaires entièrement différents avec des expressions de copie et de mise à jour. L’exemple suivant prend le même enregistrement anonyme de l’exemple précédent et le développe dans un nouvel enregistrement anonyme :

```fsharp
let data = {| X = 1; Y = 2 |}
let expandedData = {| data with Z = 3 |} // Gives {| X=1; Y=2; Z=3 |}
```

Il est également possible de construire des enregistrements anonymes à partir d’instances d’enregistrements nommés :

```fsharp
type R = { X: int }
let data = { X = 1 }
let data' = {| data with Y = 2 |} // Gives {| X=1; Y=2 |}
```

Vous pouvez également copier des données vers et depuis des enregistrements anonymes de référence et de structure :

```fsharp
// Copy data from a reference record into a struct anonymous record
type R1 = { X: int }
let r1 = { X = 1 }

let data1 = struct {| r1 with Y = 1 |}

// Copy data from a struct record into a reference anonymous record
[<Struct>]
type R2 = { X: int }
let r2 = { X = 1 }

let data2 = {| r1 with Y = 1 |}

// Copy the reference anonymous record data into a struct anonymous record
let data3 = struct {| data2 with Z = r2.X |}
```

## <a name="properties-of-anonymous-records"></a>Propriétés des enregistrements anonymes

Les enregistrements anonymes ont un certain nombre de caractéristiques qui sont essentielles pour comprendre parfaitement comment les utiliser.

### <a name="anonymous-records-are-nominal"></a>Les enregistrements anonymes sont nominaux

Les enregistrements anonymes sont des [types nominaux](https://en.wikipedia.org/wiki/Nominal_type_system). Ils sont mieux considérés comme des types d' [enregistrements](records.md) nommés (qui sont également nominaux) qui ne nécessitent pas de déclaration initiale.

Prenons l’exemple suivant avec deux déclarations d’enregistrement anonymes :

```fsharp
let x = {| X = 1 |}
let y = {| Y = 1 |}
```

Les valeurs `x` et `y` ont des types différents et ne sont pas compatibles les unes avec les autres. Elles ne sont pas équivalentes et ne sont pas comparables. Pour illustrer cela, imaginez un enregistrement nommé équivalent :

```fsharp
type X = { X: int }
type Y = { Y: int }

let x = { X = 1 }
let y = { Y = 1 }
```

Il n’existe pas de différences inhérentes par rapport aux enregistrements anonymes lorsqu’ils sont comparés à leurs équivalents d’enregistrement nommés lorsqu’ils concernent l’équivalence de type ou la comparaison.

### <a name="anonymous-records-use-structural-equality-and-comparison"></a>Les enregistrements anonymes utilisent l’égalité et la comparaison structurelles

Comme les types d’enregistrements, les enregistrements anonymes sont structurellement équivalents et comparables. Cela est vrai uniquement si tous les types constitutifs prennent en charge l’égalité et la comparaison, comme avec les types d’enregistrements. Pour prendre en charge l’égalité ou la comparaison, deux enregistrements anonymes doivent avoir la même « forme ».

```fsharp
{| a = 1+1 |} = {| a = 2 |} // true
{| a = 1+1 |} > {| a = 1 |} // true

// error FS0001: Two anonymous record types have mismatched sets of field names '["a"]' and '["a"; "b"]'
{| a = 1 + 1 |} = {| a = 2;  b = 1|}
```

### <a name="anonymous-records-are-serializable"></a>Les enregistrements anonymes sont sérialisables

Vous pouvez sérialiser des enregistrements anonymes de la même façon que vous le feriez avec des enregistrements nommés. Voici un exemple d’utilisation de [Newtonsoft. JSON](https://www.nuget.org/packages/Newtonsoft.Json/):

```fsharp
open Newtonsoft.Json

let phillip' = {| name="Phillip"; age=28 |}
let philStr = JsonConvert.SerializeObject(phillip') 

let phillip = JsonConvert.DeserializeObject<{|name: string; age: int|}>(philStr)
printfn "Name: %s Age: %d" phillip.name phillip.age
```

Les enregistrements anonymes sont utiles pour envoyer des données légères sur un réseau sans avoir à définir un domaine pour vos types sérialisés/désérialisés à l’avance.

### <a name="anonymous-records-interoperate-with-c-anonymous-types"></a>Les enregistrements anonymes interagissent avec les C# types anonymes

Il est possible d’utiliser une API .net qui requiert l’utilisation de [ C# types anonymes](../../csharp/programming-guide/classes-and-structs/anonymous-types.md). C#les types anonymes sont trivials pour interagir avec à l’aide d’enregistrements anonymes. L’exemple suivant montre comment utiliser des enregistrements anonymes pour appeler une surcharge [LINQ](../../csharp/programming-guide/concepts/linq/index.md) qui requiert un type anonyme :

```fsharp
open System.Linq

let names = [ "Ana"; "Felipe"; "Emilia"]
let nameGrouping = names.Select(fun n -> {| Name = n; FirstLetter = n.[0] |})
for ng in nameGrouping do
    printfn "%s has first letter %c" ng.Name ng.FirstLetter
```

Il existe une multitude d’autres API utilisées dans .NET qui nécessitent l’utilisation du passage d’un type anonyme. Les enregistrements anonymes sont un outil qui vous aide à les utiliser.

## <a name="limitations"></a>Limites

L’utilisation des enregistrements anonymes est soumise à certaines restrictions. Certains sont inhérents à leur conception, mais d’autres sont susceptibles d’être modifiés.

### <a name="limitations-with-pattern-matching"></a>Limitations avec les critères spéciaux

Les enregistrements anonymes ne prennent pas en charge les critères spéciaux, contrairement aux enregistrements nommés. Il y a trois raisons à cela :

1. Un modèle devrait prendre en compte tous les champs d’un enregistrement anonyme, à la différence des types d’enregistrements nommés. Cela est dû au fait que les enregistrements anonymes ne prennent pas en charge le sous-typage structurel : il s’agit de types nominaux.
2. En raison de (1), il n’est pas possible d’avoir des modèles supplémentaires dans une expression de correspondance de modèle, car chaque modèle distinct impliquerait un type d’enregistrement anonyme différent.
3. En raison de (3), tout modèle d’enregistrement anonyme serait plus détaillé que l’utilisation de la notation « point ».

Une suggestion de langue ouverte permet d' [autoriser les critères spéciaux dans les contextes limités](https://github.com/fsharp/fslang-suggestions/issues/713).

### <a name="limitations-with-mutability"></a>Limitations avec mutabilité

Il n’est actuellement pas possible de définir un enregistrement anonyme avec `mutable` données. Il existe une [suggestion de langue ouverte](https://github.com/fsharp/fslang-suggestions/issues/732) pour autoriser les données mutables.

### <a name="limitations-with-struct-anonymous-records"></a>Limitations des enregistrements anonymes de struct

Il n’est pas possible de déclarer des enregistrements anonymes de struct en tant que `IsByRefLike` ou `IsReadOnly`. Il existe une [suggestion de langue ouverte](https://github.com/fsharp/fslang-suggestions/issues/712) pour pour `IsByRefLike` et `IsReadOnly` des enregistrements anonymes.
