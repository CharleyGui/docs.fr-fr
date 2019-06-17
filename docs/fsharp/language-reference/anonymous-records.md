---
title: Enregistrements anonymes
description: Découvrez comment utiliser la construction et utiliser des enregistrements anonymes, une fonctionnalité de langage qui facilite la manipulation de données.
ms.date: 06/12/2019
ms.openlocfilehash: e576210d4fb76ccfd09f8feb157ef4542aa94ccf
ms.sourcegitcommit: c4dfe37032c64a1fba2cc3d5947550d79f95e3b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/13/2019
ms.locfileid: "67041803"
---
# <a name="anonymous-records"></a>Enregistrements anonymes

Des enregistrements anonymes sont des agrégats simples de valeurs nommées qui ne doivent être déclarées pour être utilisées. Vous pouvez les déclarer en tant que types de structures ou de référence. Ils sont des types référence par défaut.

## <a name="syntax"></a>Syntaxe

Les exemples suivants illustrent la syntaxe de l’enregistrement anonyme. Éléments délimité comme `[item]` sont facultatifs.

```fsharp
// Construct an anonymous record
let value-name = [struct] {| Label1: Type1; Label2: Type2; ...|}

// Use an anonymous record as a type parameter
let value-name = Type-Name<[struct] {| Label1: Type1; Label2: Type2; ...|}>

// Define a parameter with an anonymous record as input
let function-name (arg-name: [struct] {| Label1: Type1; Label2: Type2; ...|}) ...
```

## <a name="basic-usage"></a>Utilisation de base

Des enregistrements anonymes sont plus considérés comme F# types d’enregistrements qui n’avez pas besoin d’être déclaré avant l’instanciation.

Par exemple, ici comment vous pouvez interagir avec une fonction qui génère un enregistrement anonyme :

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

L’exemple suivant développe sur la précédente avec un `printCircleStats` fonction qui prend un enregistrement anonyme en tant qu’entrée :

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

L’appel `printCircleStats` avec n’importe quel type d’enregistrement anonyme n’ayant pas la même « forme » comme le type d’entrée ne parviendra pas à compiler :

```fsharp
printCircleStats r {| Diameter = 2.0; Area = 4.0; MyCircumference = 12.566371 |}
// Two anonymous record types have mismatched sets of field names
// '["Area"; "Circumference"; "Diameter"]' and '["Area"; "Diameter"; "MyCircumference"]'
```

## <a name="struct-anonymous-records"></a>Structure des enregistrements anonymes

Des enregistrements anonymes peuvent également être définis comme struct avec le paramètre facultatif `struct` mot clé. L’exemple suivant étend l’en production et en consommant un enregistrement de struct anonyme :

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

### <a name="structness-inference"></a>Inférence de Structness

Structure des enregistrements anonymes permettent également « structness inférence » où vous n’avez pas besoin de spécifier le `struct` mot clé sur le site d’appel. Dans cet exemple, vous elide le `struct` mot clé lors de l’appel `printCircleStats`:

```fsharp

let printCircleStats r (stats: struct {| Area: float; Circumference: float; Diameter: float |}) =
    printfn "Circle with radius: %f has diameter %f, area %f, and circumference %f"
        r stats.Diameter stats.Area stats.Circumference

printCircleStats r {| Area = 4.0; Circumference = 12.6; Diameter = 12.6 |}
```

L’inverse de modèle - spécifiant `struct` lorsque le type d’entrée n’est pas un enregistrement anonyme struct - compilation échouera.

## <a name="embedding-anonymous-records-within-other-types"></a>Incorporation des enregistrements anonymes avec d’autres types

Il est utile déclarer [unions discriminées](discriminated-unions.md) dont la casse est des enregistrements. Mais si les données dans les enregistrements sont du même type que l’union discriminée, vous devez définir tous les types en tant que mutuellement récursives. À l’aide des enregistrements anonymes permet d’éviter cette restriction. Ce qui suit est un exemple type et la fonction de ce modèle correspond au dessus :

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

Des enregistrements anonymes prennent en charge la construction avec [copier et mettre à jour des expressions](copy-and-update-record-expressions.md). Par exemple, voici comment vous pouvez construire une nouvelle instance d’un enregistrement anonyme qui copie existante de données :

```fsharp
let data = {| X = 1; Y = 2 |}
let data' = {| data with Y = 3 |}
```

Toutefois, contrairement aux enregistrements nommés, des enregistrements anonymes permettent construire des formes entièrement différentes par copie et de mettre à jour des expressions. L’exemple suivant prend le même enregistrement anonyme à partir de l’exemple précédent et développe dans un nouvel enregistrement anonyme :

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

Vous pouvez également copier des données vers et à partir de la référence et la structure des enregistrements anonymes :

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

Des enregistrements anonymes ont un certain nombre de caractéristiques qui sont essentiels pour comprendre pleinement comment elles peuvent être utilisées.

### <a name="anonymous-records-are-nominal"></a>Des enregistrements anonymes sont nominales

Des enregistrements anonymes sont [types nominaux](https://en.wikipedia.org/wiki/Nominal_type_system). Ils sont considéré comme nommé [enregistrement](records.md) types (qui sont également nominales) qui ne nécessitent pas une déclaration initiale.

Prenons l’exemple suivant avec deux déclarations d’enregistrement anonyme :

```fsharp
let x = {| X = 1 |}
let y = {| Y = 1 |}
```

Le `x` et `y` valeurs ont des types différents et ne sont pas compatibles entre eux. Ils ne sont pas comparables, et ils ne sont pas comparables. Pour illustrer ce propos, considérez un enregistrement nommé équivalents :

```fsharp
type X = { X: int }
type Y = { Y: int }

let x = { X = 1 }
let y = { Y = 1 }
```

Il n’est pas quelque chose de différent, par nature, à propos des enregistrements anonymes par rapport à leurs équivalents d’enregistrement nommé lorsque concernant l’équivalence de type ou de comparaison.

### <a name="anonymous-records-use-structural-equality-and-comparison"></a>Des enregistrements anonymes, utilisez comparaison et égalité structurelle

Comme les types d’enregistrements, enregistrements anonymes sont structurellement égaux et comparables. Cela est vrai uniquement si tous les types qui le composent prennent en charge l’égalité et comparaison, comme avec les types d’enregistrements. Pour prendre en charge l’égalité ou comparaison, les deux enregistrements anonymes doivent avoir la même « forme ».

```fsharp
{| a = 1+1 |} = {| a = 2 |} // true
{| a = 1+1 |} > {| a = 1 |} // true

// error FS0001: Two anonymous record types have mismatched sets of field names '["a"]' and '["a"; "b"]'
{| a = 1 + 1 |} = {| a = 2;  b = 1|}
```

### <a name="anonymous-records-are-serializable"></a>Des enregistrements anonymes sont sérialisables

Vous pouvez sérialiser des enregistrements anonymes tout comme vous pouvez le faire avec les enregistrements nommés. Voici un exemple à l’aide de [Newtonsoft.Json](https://www.nuget.org/packages/Newtonsoft.Json/):

```fsharp
open Newtonsoft.Json

let phillip = {| name="Phillip"; age=28 |}
JsonConvert.SerializeObject(phillip)

let phillip = JsonConvert.DeserializeObject<{|name: string; age: int|}>(str)
printfn "Name: %s Age: %d" phillip.name phillip.age
```

Des enregistrements anonymes sont utiles pour l’envoi de données léger sur un réseau sans la nécessité de définir un domaine pour vos types de sérialisation/désérialisation en amont.

### <a name="anonymous-records-interoperate-with-c-anonymous-types"></a>Des enregistrements anonymes interopèrent avec C# types anonymes

Il est possible d’utiliser une API .NET qui nécessite l’utilisation de [ C# types anonymes](../../csharp/programming-guide/classes-and-structs/anonymous-types.md). C#les types anonymes sont faciles à interagir avec à l’aide des enregistrements anonymes. L’exemple suivant montre comment utiliser des enregistrements anonymes d’appeler un [LINQ](../../csharp/programming-guide/concepts/linq/index.md) surcharge qui nécessite un type anonyme :

```fsharp
open System.Linq

let names = [ "Ana"; "Felipe"; "Emilia"]
let nameGrouping = names.Select(fun n -> {| Name = n; FirstLetter = n.[0] |})
for ng in nameGrouping do
    printfn "%s has first letter %c" ng.Name ng.FirstLetter
```

Il existe une multitude d’autres API utilisées dans .NET qui nécessitent l’utilisation de passage dans un type anonyme. Des enregistrements anonymes sont votre outil de leur utilisation.

## <a name="limitations"></a>Limitations

Des enregistrements anonymes présentent quelques restrictions dans leur utilisation. Certains sont inhérents à leur conception, mais d’autres sont faciles à modifier.

### <a name="limitations-with-pattern-matching"></a>Limitations de critères spéciaux

Des enregistrements anonymes ne gèrent pas de critères spéciaux, contrairement aux enregistrements nommés. Il existe trois raisons :

1. Un modèle aurait pour prendre en compte pour chaque champ d’un enregistrement anonyme, contrairement aux types d’enregistrements nommé. Il s’agit, car des enregistrements anonymes ne gèrent pas les sous-typage structurelle : ils sont des types nominaux.
2. En raison de (1), il n’existe aucune possibilité d’avoir des modèles supplémentaires dans une expression de correspondance de modèle, car chaque modèle distinct nécessiterait un autre type anonyme.
3. En raison de (3), n’importe quel modèle d’enregistrement anonyme serait plus détaillé que l’utilisation de la notation « point ».

Il existe une suggestion de langage open à [autoriser les critères spéciaux limitée dans les contextes](https://github.com/fsharp/fslang-suggestions/issues/713).

### <a name="limitations-with-mutability"></a>Limitations avec la mutabilité

Il n’est pas encore possible de définir un enregistrement anonyme avec `mutable` données. Il existe un [ouvrir suggestion de langage](https://github.com/fsharp/fslang-suggestions/issues/732) pour autoriser les données mutables.

### <a name="limitations-with-struct-anonymous-records"></a>Limitations des enregistrements anonymes struct

Il n’est pas possible de déclarer des enregistrements anonymes sous la forme de struct `IsByRefLike` ou `IsReadOnly`. Il existe un [ouvrir suggestion de langage](https://github.com/fsharp/fslang-suggestions/issues/712) à pour `IsByRefLike` et `IsReadOnly` des enregistrements anonymes.
