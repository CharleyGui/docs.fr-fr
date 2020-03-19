---
title: Enregistrements anonymes
description: Apprenez à utiliser la construction et l’utilisation d’Anonymous Records, une fonctionnalité linguistique qui aide à la manipulation des données.
ms.date: 06/12/2019
ms.openlocfilehash: ef3aa8fccdb6ff406542932816e4138040845a59
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187490"
---
# <a name="anonymous-records"></a>Enregistrements anonymes

Les enregistrements anonymes sont des agrégats simples de valeurs nommées qui n’ont pas besoin d’être déclarés avant utilisation. Vous pouvez les déclarer comme des structs ou des types de référence. Ce sont des types de référence par défaut.

## <a name="syntax"></a>Syntaxe

Les exemples suivants démontrent la syntaxe anonyme. Articles délimités `[item]` en option.

```fsharp
// Construct an anonymous record
let value-name = [struct] {| Label1: Type1; Label2: Type2; ...|}

// Use an anonymous record as a type parameter
let value-name = Type-Name<[struct] {| Label1: Type1; Label2: Type2; ...|}>

// Define a parameter with an anonymous record as input
let function-name (arg-name: [struct] {| Label1: Type1; Label2: Type2; ...|}) ...
```

## <a name="basic-usage"></a>Utilisation de base

Les enregistrements anonymes sont mieux considérés comme des types d’enregistrements F et qui n’ont pas besoin d’être déclarés avant l’instantanéisation.

Par exemple, voici comment vous pouvez interagir avec une fonction qui produit un enregistrement anonyme :

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

L’exemple suivant s’étend sur `printCircleStats` le précédent avec une fonction qui prend un dossier anonyme comme entrée:

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

Appeler `printCircleStats` avec n’importe quel type d’enregistrement anonyme qui n’a pas la même «forme» que le type d’entrée ne sera pas compiler:

```fsharp
printCircleStats r {| Diameter = 2.0; Area = 4.0; MyCircumference = 12.566371 |}
// Two anonymous record types have mismatched sets of field names
// '["Area"; "Circumference"; "Diameter"]' and '["Area"; "Diameter"; "MyCircumference"]'
```

## <a name="struct-anonymous-records"></a>Structurer des dossiers anonymes

Les enregistrements anonymes peuvent également être `struct` définis comme struct avec le mot clé facultatif. L’exemple suivant augmente le précédent en produisant et en consommant un enregistrement anonyme struct :

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

### <a name="structness-inference"></a>Inférence de structuration

Les enregistrements anonymes Struct permettent également une « inférence de `struct` la structivité » lorsque vous n’avez pas besoin de spécifier le mot clé sur le site d’appel. Dans cet exemple, vous `struct` élitez le mot clé lors de l’appel `printCircleStats`:

```fsharp

let printCircleStats r (stats: struct {| Area: float; Circumference: float; Diameter: float |}) =
    printfn "Circle with radius: %f has diameter %f, area %f, and circumference %f"
        r stats.Diameter stats.Area stats.Circumference

printCircleStats r {| Area = 4.0; Circumference = 12.6; Diameter = 12.6 |}
```

Le modèle inverse `struct` - spécifiant quand le type d’entrée n’est pas un enregistrement anonyme structurant - ne sera pas compilé.

## <a name="embedding-anonymous-records-within-other-types"></a>Intégrer des dossiers anonymes dans d’autres types

Il est utile de déclarer [les syndicats discriminés](discriminated-unions.md) dont les cas sont des dossiers. Mais si les données dans les dossiers sont du même type que l’union discriminée, vous devez définir tous les types comme récursifs mutuellement. L’utilisation de dossiers anonymes évite cette restriction. Ce qui suit est un type d’exemple et la fonction que le modèle correspond à celui-ci:

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

## <a name="copy-and-update-expressions"></a>Copier et mettre à jour les expressions

Les documents anonymes prennent en charge la construction avec [des expressions de copie et de mise à jour.](copy-and-update-record-expressions.md) Par exemple, voici comment vous pouvez construire une nouvelle instance d’un enregistrement anonyme qui copie les données d’un enregistrement existant :

```fsharp
let data = {| X = 1; Y = 2 |}
let data' = {| data with Y = 3 |}
```

Cependant, contrairement aux enregistrements nommés, les enregistrements anonymes vous permettent de construire des formulaires entièrement différents avec des expressions de copie et de mise à jour. L’exemple de suivi prend le même enregistrement anonyme de l’exemple précédent et l’étend dans un nouvel enregistrement anonyme:

```fsharp
let data = {| X = 1; Y = 2 |}
let expandedData = {| data with Z = 3 |} // Gives {| X=1; Y=2; Z=3 |}
```

Il est également possible de construire des enregistrements anonymes à partir d’instances de documents nommés :

```fsharp
type R = { X: int }
let data = { X = 1 }
let data' = {| data with Y = 2 |} // Gives {| X=1; Y=2 |}
```

Vous pouvez également copier des données à et depuis et en référant des enregistrements anonymes :

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

## <a name="properties-of-anonymous-records"></a>Propriétés de dossiers anonymes

Les dossiers anonymes ont un certain nombre de caractéristiques qui sont essentielles pour bien comprendre comment ils peuvent être utilisés.

### <a name="anonymous-records-are-nominal"></a>Les dossiers anonymes sont nominaux

Les dossiers anonymes sont [des types nominaux](https://en.wikipedia.org/wiki/Nominal_type_system). Ils sont mieux considérés comme des types [d’enregistrement](records.md) nommés (qui sont également nominaux) qui ne nécessitent pas une déclaration à l’avance.

Prenons l’exemple suivant avec deux déclarations d’enregistrement anonymes :

```fsharp
let x = {| X = 1 |}
let y = {| Y = 1 |}
```

Les `x` `y` valeurs et les valeurs ont des types différents et ne sont pas compatibles les unes avec les autres. Ils ne sont pas équatables et ils ne sont pas comparables. Pour illustrer cela, considérez un équivalent d’enregistrement nommé :

```fsharp
type X = { X: int }
type Y = { Y: int }

let x = { X = 1 }
let y = { Y = 1 }
```

Il n’y a rien d’intrinsèquement différent dans les enregistrements anonymes par rapport à leurs équivalents d’enregistrement nommés en ce qui concerne l’équivalence de type ou la comparaison.

### <a name="anonymous-records-use-structural-equality-and-comparison"></a>Les documents anonymes utilisent l’égalité structurelle et la comparaison

Comme les types d’enregistrements, les dossiers anonymes sont structurellement équatables et comparables. Cela n’est vrai que si tous les types de constituants sont en faveur de l’égalité et de la comparaison, comme avec les types de disques. Pour soutenir l’égalité ou la comparaison, deux dossiers anonymes doivent avoir la même « forme ».

```fsharp
{| a = 1+1 |} = {| a = 2 |} // true
{| a = 1+1 |} > {| a = 1 |} // true

// error FS0001: Two anonymous record types have mismatched sets of field names '["a"]' and '["a"; "b"]'
{| a = 1 + 1 |} = {| a = 2;  b = 1|}
```

### <a name="anonymous-records-are-serializable"></a>Les dossiers anonymes sont sérialisables

Vous pouvez sérialiser des enregistrements anonymes comme vous le pouvez avec les enregistrements nommés. Voici un exemple en utilisant [Newtonsoft.Json](https://www.nuget.org/packages/Newtonsoft.Json/):

```fsharp
open Newtonsoft.Json

let phillip' = {| name="Phillip"; age=28 |}
let philStr = JsonConvert.SerializeObject(phillip')

let phillip = JsonConvert.DeserializeObject<{|name: string; age: int|}>(philStr)
printfn "Name: %s Age: %d" phillip.name phillip.age
```

Les enregistrements anonymes sont utiles pour envoyer des données légères sur un réseau sans avoir besoin de définir un domaine pour vos types sérialisés/déséialisés à l’avance.

### <a name="anonymous-records-interoperate-with-c-anonymous-types"></a>Les dossiers anonymes s’interopément avec les types d’anonymes C

Il est possible d’utiliser une API .NET qui nécessite l’utilisation de [types D.C. anonymes](../../csharp/programming-guide/classes-and-structs/anonymous-types.md). Les types anonymes Cmd sont insignifiants à interopérer en utilisant des dossiers anonymes. L’exemple suivant montre comment utiliser des dossiers anonymes pour appeler une surcharge [LINQ](../../csharp/programming-guide/concepts/linq/index.md) qui nécessite un type anonyme :

```fsharp
open System.Linq

let names = [ "Ana"; "Felipe"; "Emilia"]
let nameGrouping = names.Select(fun n -> {| Name = n; FirstLetter = n.[0] |})
for ng in nameGrouping do
    printfn "%s has first letter %c" ng.Name ng.FirstLetter
```

Il existe une multitude d’autres API utilisées sur .NET qui nécessitent l’utilisation de la transmission dans un type anonyme. Les dossiers anonymes sont votre outil pour travailler avec eux.

## <a name="limitations"></a>Limites

Les dossiers anonymes ont certaines restrictions dans leur utilisation. Certains sont inhérents à leur conception, mais d’autres sont agréables à changer.

### <a name="limitations-with-pattern-matching"></a>Limitations avec l’appariement des motifs

Les dossiers anonymes ne prennent pas en charge l’appariement des motifs, contrairement aux enregistrements nommés. Il y a trois raisons :

1. Un modèle devrait rendre compte de chaque domaine d’un enregistrement anonyme, contrairement aux types d’enregistrement nommés. C’est parce que les dossiers anonymes ne prennent pas en charge le sous-typage structurel - ce sont des types nominaux.
2. En raison de (1), il n’y a aucune capacité d’avoir des modèles supplémentaires dans une expression de correspondance de modèle, comme chaque modèle distinct impliquerait un type d’enregistrement anonyme différent.
3. En raison de (3), tout modèle d’enregistrement anonyme serait plus verbeux que l’utilisation de la notation "point".

Il y a une suggestion de langage ouvert pour [permettre l’appariement des modèles dans des contextes limités.](https://github.com/fsharp/fslang-suggestions/issues/713)

### <a name="limitations-with-mutability"></a>Limitations avec mutabilité

Il n’est pas actuellement possible `mutable` de définir un enregistrement anonyme avec des données. Il existe une [suggestion en langage ouvert](https://github.com/fsharp/fslang-suggestions/issues/732) pour permettre des données mutables.

### <a name="limitations-with-struct-anonymous-records"></a>Limitations avec la struction des dossiers anonymes

Il n’est pas possible de `IsByRefLike` `IsReadOnly`déclarer des documents anonymes structurants comme ou . Il y a une `IsByRefLike` suggestion `IsReadOnly` de [langage ouvert](https://github.com/fsharp/fslang-suggestions/issues/712) pour les dossiers anonymes et les dossiers.
