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
# <a name="anonymous-records"></a><span data-ttu-id="36469-103">Enregistrements anonymes</span><span class="sxs-lookup"><span data-stu-id="36469-103">Anonymous Records</span></span>

<span data-ttu-id="36469-104">Des enregistrements anonymes sont des agrégats simples de valeurs nommées qui ne doivent être déclarées pour être utilisées.</span><span class="sxs-lookup"><span data-stu-id="36469-104">Anonymous records are simple aggregates of named values that don't need to be declared before use.</span></span> <span data-ttu-id="36469-105">Vous pouvez les déclarer en tant que types de structures ou de référence.</span><span class="sxs-lookup"><span data-stu-id="36469-105">You can declare them as either structs or reference types.</span></span> <span data-ttu-id="36469-106">Ils sont des types référence par défaut.</span><span class="sxs-lookup"><span data-stu-id="36469-106">They're reference types by default.</span></span>

## <a name="syntax"></a><span data-ttu-id="36469-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="36469-107">Syntax</span></span>

<span data-ttu-id="36469-108">Les exemples suivants illustrent la syntaxe de l’enregistrement anonyme.</span><span class="sxs-lookup"><span data-stu-id="36469-108">The following examples demonstrate the anonymous record syntax.</span></span> <span data-ttu-id="36469-109">Éléments délimité comme `[item]` sont facultatifs.</span><span class="sxs-lookup"><span data-stu-id="36469-109">Items delimited as `[item]` are optional.</span></span>

```fsharp
// Construct an anonymous record
let value-name = [struct] {| Label1: Type1; Label2: Type2; ...|}

// Use an anonymous record as a type parameter
let value-name = Type-Name<[struct] {| Label1: Type1; Label2: Type2; ...|}>

// Define a parameter with an anonymous record as input
let function-name (arg-name: [struct] {| Label1: Type1; Label2: Type2; ...|}) ...
```

## <a name="basic-usage"></a><span data-ttu-id="36469-110">Utilisation de base</span><span class="sxs-lookup"><span data-stu-id="36469-110">Basic usage</span></span>

<span data-ttu-id="36469-111">Des enregistrements anonymes sont plus considérés comme F# types d’enregistrements qui n’avez pas besoin d’être déclaré avant l’instanciation.</span><span class="sxs-lookup"><span data-stu-id="36469-111">Anonymous records are best thought of as F# record types that don't need to be declared before instantiation.</span></span>

<span data-ttu-id="36469-112">Par exemple, ici comment vous pouvez interagir avec une fonction qui génère un enregistrement anonyme :</span><span class="sxs-lookup"><span data-stu-id="36469-112">For example, here how you can interact with a function that produces an anonymous record:</span></span>

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

<span data-ttu-id="36469-113">L’exemple suivant développe sur la précédente avec un `printCircleStats` fonction qui prend un enregistrement anonyme en tant qu’entrée :</span><span class="sxs-lookup"><span data-stu-id="36469-113">The following example expands on the previous one with a `printCircleStats` function that takes an anonymous record as input:</span></span>

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

<span data-ttu-id="36469-114">L’appel `printCircleStats` avec n’importe quel type d’enregistrement anonyme n’ayant pas la même « forme » comme le type d’entrée ne parviendra pas à compiler :</span><span class="sxs-lookup"><span data-stu-id="36469-114">Calling `printCircleStats` with any anonymous record type that doesn't have the same "shape" as the input type will fail to compile:</span></span>

```fsharp
printCircleStats r {| Diameter = 2.0; Area = 4.0; MyCircumference = 12.566371 |}
// Two anonymous record types have mismatched sets of field names
// '["Area"; "Circumference"; "Diameter"]' and '["Area"; "Diameter"; "MyCircumference"]'
```

## <a name="struct-anonymous-records"></a><span data-ttu-id="36469-115">Structure des enregistrements anonymes</span><span class="sxs-lookup"><span data-stu-id="36469-115">Struct anonymous records</span></span>

<span data-ttu-id="36469-116">Des enregistrements anonymes peuvent également être définis comme struct avec le paramètre facultatif `struct` mot clé.</span><span class="sxs-lookup"><span data-stu-id="36469-116">Anonymous records can also be defined as struct with the optional `struct` keyword.</span></span> <span data-ttu-id="36469-117">L’exemple suivant étend l’en production et en consommant un enregistrement de struct anonyme :</span><span class="sxs-lookup"><span data-stu-id="36469-117">The following example augments the previous one by producing and consuming a struct anonymous record:</span></span>

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

### <a name="structness-inference"></a><span data-ttu-id="36469-118">Inférence de Structness</span><span class="sxs-lookup"><span data-stu-id="36469-118">Structness inference</span></span>

<span data-ttu-id="36469-119">Structure des enregistrements anonymes permettent également « structness inférence » où vous n’avez pas besoin de spécifier le `struct` mot clé sur le site d’appel.</span><span class="sxs-lookup"><span data-stu-id="36469-119">Struct anonymous records also allow for "structness inference" where you do not need to specify the `struct` keyword at the call site.</span></span> <span data-ttu-id="36469-120">Dans cet exemple, vous elide le `struct` mot clé lors de l’appel `printCircleStats`:</span><span class="sxs-lookup"><span data-stu-id="36469-120">In this example, you elide the `struct` keyword when calling `printCircleStats`:</span></span>

```fsharp

let printCircleStats r (stats: struct {| Area: float; Circumference: float; Diameter: float |}) =
    printfn "Circle with radius: %f has diameter %f, area %f, and circumference %f"
        r stats.Diameter stats.Area stats.Circumference

printCircleStats r {| Area = 4.0; Circumference = 12.6; Diameter = 12.6 |}
```

<span data-ttu-id="36469-121">L’inverse de modèle - spécifiant `struct` lorsque le type d’entrée n’est pas un enregistrement anonyme struct - compilation échouera.</span><span class="sxs-lookup"><span data-stu-id="36469-121">The reverse pattern - specifying `struct` when the input type is not a struct anonymous record - will fail to compile.</span></span>

## <a name="embedding-anonymous-records-within-other-types"></a><span data-ttu-id="36469-122">Incorporation des enregistrements anonymes avec d’autres types</span><span class="sxs-lookup"><span data-stu-id="36469-122">Embedding anonymous records within other types</span></span>

<span data-ttu-id="36469-123">Il est utile déclarer [unions discriminées](discriminated-unions.md) dont la casse est des enregistrements.</span><span class="sxs-lookup"><span data-stu-id="36469-123">It's useful to declare [discriminated unions](discriminated-unions.md) whose cases are records.</span></span> <span data-ttu-id="36469-124">Mais si les données dans les enregistrements sont du même type que l’union discriminée, vous devez définir tous les types en tant que mutuellement récursives.</span><span class="sxs-lookup"><span data-stu-id="36469-124">But if the data in the records is the same type as the discriminated union, you must define all types as mutually recursive.</span></span> <span data-ttu-id="36469-125">À l’aide des enregistrements anonymes permet d’éviter cette restriction.</span><span class="sxs-lookup"><span data-stu-id="36469-125">Using anonymous records avoids this restriction.</span></span> <span data-ttu-id="36469-126">Ce qui suit est un exemple type et la fonction de ce modèle correspond au dessus :</span><span class="sxs-lookup"><span data-stu-id="36469-126">What follows is an example type and function that pattern matches over it:</span></span>

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

## <a name="copy-and-update-expressions"></a><span data-ttu-id="36469-127">Copier et mettre à jour des expressions</span><span class="sxs-lookup"><span data-stu-id="36469-127">Copy and update expressions</span></span>

<span data-ttu-id="36469-128">Des enregistrements anonymes prennent en charge la construction avec [copier et mettre à jour des expressions](copy-and-update-record-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="36469-128">Anonymous records support construction with [copy and update expressions](copy-and-update-record-expressions.md).</span></span> <span data-ttu-id="36469-129">Par exemple, voici comment vous pouvez construire une nouvelle instance d’un enregistrement anonyme qui copie existante de données :</span><span class="sxs-lookup"><span data-stu-id="36469-129">For example, here's how you can construct a new instance of an anonymous record that copies an existing one's data:</span></span>

```fsharp
let data = {| X = 1; Y = 2 |}
let data' = {| data with Y = 3 |}
```

<span data-ttu-id="36469-130">Toutefois, contrairement aux enregistrements nommés, des enregistrements anonymes permettent construire des formes entièrement différentes par copie et de mettre à jour des expressions.</span><span class="sxs-lookup"><span data-stu-id="36469-130">However, unlike named records, anonymous records allow you to construct entirely different forms with copy and update expressions.</span></span> <span data-ttu-id="36469-131">L’exemple suivant prend le même enregistrement anonyme à partir de l’exemple précédent et développe dans un nouvel enregistrement anonyme :</span><span class="sxs-lookup"><span data-stu-id="36469-131">The follow example takes the same anonymous record from the previous example and expands it into a new anonymous record:</span></span>

```fsharp
let data = {| X = 1; Y = 2 |}
let expandedData = {| data with Z = 3 |} // Gives {| X=1; Y=2; Z=3 |}
```

<span data-ttu-id="36469-132">Il est également possible de construire des enregistrements anonymes à partir d’instances d’enregistrements nommés :</span><span class="sxs-lookup"><span data-stu-id="36469-132">It is also possible to construct anonymous records from instances of named records:</span></span>

```fsharp
type R = { X: int }
let data = { X = 1 }
let data' = {| data with Y = 2 |} // Gives {| X=1; Y=2 |}
```

<span data-ttu-id="36469-133">Vous pouvez également copier des données vers et à partir de la référence et la structure des enregistrements anonymes :</span><span class="sxs-lookup"><span data-stu-id="36469-133">You can also copy data to and from reference and struct anonymous records:</span></span>

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

## <a name="properties-of-anonymous-records"></a><span data-ttu-id="36469-134">Propriétés des enregistrements anonymes</span><span class="sxs-lookup"><span data-stu-id="36469-134">Properties of anonymous records</span></span>

<span data-ttu-id="36469-135">Des enregistrements anonymes ont un certain nombre de caractéristiques qui sont essentiels pour comprendre pleinement comment elles peuvent être utilisées.</span><span class="sxs-lookup"><span data-stu-id="36469-135">Anonymous records have a number of characteristics that are essential to fully understanding how they can be used.</span></span>

### <a name="anonymous-records-are-nominal"></a><span data-ttu-id="36469-136">Des enregistrements anonymes sont nominales</span><span class="sxs-lookup"><span data-stu-id="36469-136">Anonymous records are nominal</span></span>

<span data-ttu-id="36469-137">Des enregistrements anonymes sont [types nominaux](https://en.wikipedia.org/wiki/Nominal_type_system).</span><span class="sxs-lookup"><span data-stu-id="36469-137">Anonymous records are [nominal types](https://en.wikipedia.org/wiki/Nominal_type_system).</span></span> <span data-ttu-id="36469-138">Ils sont considéré comme nommé [enregistrement](records.md) types (qui sont également nominales) qui ne nécessitent pas une déclaration initiale.</span><span class="sxs-lookup"><span data-stu-id="36469-138">They are best thought as named [record](records.md) types (which are also nominal) that do not require an up-front declaration.</span></span>

<span data-ttu-id="36469-139">Prenons l’exemple suivant avec deux déclarations d’enregistrement anonyme :</span><span class="sxs-lookup"><span data-stu-id="36469-139">Consider the following example with two anonymous record declarations:</span></span>

```fsharp
let x = {| X = 1 |}
let y = {| Y = 1 |}
```

<span data-ttu-id="36469-140">Le `x` et `y` valeurs ont des types différents et ne sont pas compatibles entre eux.</span><span class="sxs-lookup"><span data-stu-id="36469-140">The `x` and `y` values have different types and are not compatible with one another.</span></span> <span data-ttu-id="36469-141">Ils ne sont pas comparables, et ils ne sont pas comparables.</span><span class="sxs-lookup"><span data-stu-id="36469-141">They are not equatable and they are not comparable.</span></span> <span data-ttu-id="36469-142">Pour illustrer ce propos, considérez un enregistrement nommé équivalents :</span><span class="sxs-lookup"><span data-stu-id="36469-142">To illustrate this, consider a named record equivalent:</span></span>

```fsharp
type X = { X: int }
type Y = { Y: int }

let x = { X = 1 }
let y = { Y = 1 }
```

<span data-ttu-id="36469-143">Il n’est pas quelque chose de différent, par nature, à propos des enregistrements anonymes par rapport à leurs équivalents d’enregistrement nommé lorsque concernant l’équivalence de type ou de comparaison.</span><span class="sxs-lookup"><span data-stu-id="36469-143">There isn't anything inherently different about anonymous records when compared with their named record equivalents when concerning type equivalency or comparison.</span></span>

### <a name="anonymous-records-use-structural-equality-and-comparison"></a><span data-ttu-id="36469-144">Des enregistrements anonymes, utilisez comparaison et égalité structurelle</span><span class="sxs-lookup"><span data-stu-id="36469-144">Anonymous records use structural equality and comparison</span></span>

<span data-ttu-id="36469-145">Comme les types d’enregistrements, enregistrements anonymes sont structurellement égaux et comparables.</span><span class="sxs-lookup"><span data-stu-id="36469-145">Like record types, anonymous records are structurally equatable and comparable.</span></span> <span data-ttu-id="36469-146">Cela est vrai uniquement si tous les types qui le composent prennent en charge l’égalité et comparaison, comme avec les types d’enregistrements.</span><span class="sxs-lookup"><span data-stu-id="36469-146">This is only true if all constituent types support equality and comparison, like with record types.</span></span> <span data-ttu-id="36469-147">Pour prendre en charge l’égalité ou comparaison, les deux enregistrements anonymes doivent avoir la même « forme ».</span><span class="sxs-lookup"><span data-stu-id="36469-147">To support equality or comparison, two anonymous records must have the same "shape".</span></span>

```fsharp
{| a = 1+1 |} = {| a = 2 |} // true
{| a = 1+1 |} > {| a = 1 |} // true

// error FS0001: Two anonymous record types have mismatched sets of field names '["a"]' and '["a"; "b"]'
{| a = 1 + 1 |} = {| a = 2;  b = 1|}
```

### <a name="anonymous-records-are-serializable"></a><span data-ttu-id="36469-148">Des enregistrements anonymes sont sérialisables</span><span class="sxs-lookup"><span data-stu-id="36469-148">Anonymous records are serializable</span></span>

<span data-ttu-id="36469-149">Vous pouvez sérialiser des enregistrements anonymes tout comme vous pouvez le faire avec les enregistrements nommés.</span><span class="sxs-lookup"><span data-stu-id="36469-149">You can serialize anonymous records just as you can with named records.</span></span> <span data-ttu-id="36469-150">Voici un exemple à l’aide de [Newtonsoft.Json](https://www.nuget.org/packages/Newtonsoft.Json/):</span><span class="sxs-lookup"><span data-stu-id="36469-150">Here is an example using [Newtonsoft.Json](https://www.nuget.org/packages/Newtonsoft.Json/):</span></span>

```fsharp
open Newtonsoft.Json

let phillip = {| name="Phillip"; age=28 |}
JsonConvert.SerializeObject(phillip)

let phillip = JsonConvert.DeserializeObject<{|name: string; age: int|}>(str)
printfn "Name: %s Age: %d" phillip.name phillip.age
```

<span data-ttu-id="36469-151">Des enregistrements anonymes sont utiles pour l’envoi de données léger sur un réseau sans la nécessité de définir un domaine pour vos types de sérialisation/désérialisation en amont.</span><span class="sxs-lookup"><span data-stu-id="36469-151">Anonymous records are useful for sending lightweight data over a network without the need to define a domain for your serialized/deserialized types up front.</span></span>

### <a name="anonymous-records-interoperate-with-c-anonymous-types"></a><span data-ttu-id="36469-152">Des enregistrements anonymes interopèrent avec C# types anonymes</span><span class="sxs-lookup"><span data-stu-id="36469-152">Anonymous records interoperate with C# anonymous types</span></span>

<span data-ttu-id="36469-153">Il est possible d’utiliser une API .NET qui nécessite l’utilisation de [ C# types anonymes](../../csharp/programming-guide/classes-and-structs/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="36469-153">It is possible to use a .NET API that requires the use of [C# anonymous types](../../csharp/programming-guide/classes-and-structs/anonymous-types.md).</span></span> <span data-ttu-id="36469-154">C#les types anonymes sont faciles à interagir avec à l’aide des enregistrements anonymes.</span><span class="sxs-lookup"><span data-stu-id="36469-154">C# anonymous types are trivial to interoperate with by using anonymous records.</span></span> <span data-ttu-id="36469-155">L’exemple suivant montre comment utiliser des enregistrements anonymes d’appeler un [LINQ](../../csharp/programming-guide/concepts/linq/index.md) surcharge qui nécessite un type anonyme :</span><span class="sxs-lookup"><span data-stu-id="36469-155">The following example shows how to use anonymous records to call a [LINQ](../../csharp/programming-guide/concepts/linq/index.md) overload that requires an anonymous type:</span></span>

```fsharp
open System.Linq

let names = [ "Ana"; "Felipe"; "Emilia"]
let nameGrouping = names.Select(fun n -> {| Name = n; FirstLetter = n.[0] |})
for ng in nameGrouping do
    printfn "%s has first letter %c" ng.Name ng.FirstLetter
```

<span data-ttu-id="36469-156">Il existe une multitude d’autres API utilisées dans .NET qui nécessitent l’utilisation de passage dans un type anonyme.</span><span class="sxs-lookup"><span data-stu-id="36469-156">There are a multitude of other APIs used throughout .NET that require the use of passing in an anonymous type.</span></span> <span data-ttu-id="36469-157">Des enregistrements anonymes sont votre outil de leur utilisation.</span><span class="sxs-lookup"><span data-stu-id="36469-157">Anonymous records are your tool for working with them.</span></span>

## <a name="limitations"></a><span data-ttu-id="36469-158">Limitations</span><span class="sxs-lookup"><span data-stu-id="36469-158">Limitations</span></span>

<span data-ttu-id="36469-159">Des enregistrements anonymes présentent quelques restrictions dans leur utilisation.</span><span class="sxs-lookup"><span data-stu-id="36469-159">Anonymous records have some restrictions in their usage.</span></span> <span data-ttu-id="36469-160">Certains sont inhérents à leur conception, mais d’autres sont faciles à modifier.</span><span class="sxs-lookup"><span data-stu-id="36469-160">Some are inherent to their design, but others are amenable to change.</span></span>

### <a name="limitations-with-pattern-matching"></a><span data-ttu-id="36469-161">Limitations de critères spéciaux</span><span class="sxs-lookup"><span data-stu-id="36469-161">Limitations with pattern matching</span></span>

<span data-ttu-id="36469-162">Des enregistrements anonymes ne gèrent pas de critères spéciaux, contrairement aux enregistrements nommés.</span><span class="sxs-lookup"><span data-stu-id="36469-162">Anonymous records do not support pattern matching, unlike named records.</span></span> <span data-ttu-id="36469-163">Il existe trois raisons :</span><span class="sxs-lookup"><span data-stu-id="36469-163">There are three reasons:</span></span>

1. <span data-ttu-id="36469-164">Un modèle aurait pour prendre en compte pour chaque champ d’un enregistrement anonyme, contrairement aux types d’enregistrements nommé.</span><span class="sxs-lookup"><span data-stu-id="36469-164">A pattern would have to account for every field of an anonymous record, unlike named record types.</span></span> <span data-ttu-id="36469-165">Il s’agit, car des enregistrements anonymes ne gèrent pas les sous-typage structurelle : ils sont des types nominaux.</span><span class="sxs-lookup"><span data-stu-id="36469-165">This is because anonymous records do not support structural subtyping – they are nominal types.</span></span>
2. <span data-ttu-id="36469-166">En raison de (1), il n’existe aucune possibilité d’avoir des modèles supplémentaires dans une expression de correspondance de modèle, car chaque modèle distinct nécessiterait un autre type anonyme.</span><span class="sxs-lookup"><span data-stu-id="36469-166">Because of (1), there is no ability to have additional patterns in a pattern match expression, as each distinct pattern would imply a different anonymous record type.</span></span>
3. <span data-ttu-id="36469-167">En raison de (3), n’importe quel modèle d’enregistrement anonyme serait plus détaillé que l’utilisation de la notation « point ».</span><span class="sxs-lookup"><span data-stu-id="36469-167">Because of (3), any anonymous record pattern would be more verbose than the use of “dot” notation.</span></span>

<span data-ttu-id="36469-168">Il existe une suggestion de langage open à [autoriser les critères spéciaux limitée dans les contextes](https://github.com/fsharp/fslang-suggestions/issues/713).</span><span class="sxs-lookup"><span data-stu-id="36469-168">There is an open language suggestion to [allow pattern matching in limited contexts](https://github.com/fsharp/fslang-suggestions/issues/713).</span></span>

### <a name="limitations-with-mutability"></a><span data-ttu-id="36469-169">Limitations avec la mutabilité</span><span class="sxs-lookup"><span data-stu-id="36469-169">Limitations with mutability</span></span>

<span data-ttu-id="36469-170">Il n’est pas encore possible de définir un enregistrement anonyme avec `mutable` données.</span><span class="sxs-lookup"><span data-stu-id="36469-170">It is not currently possible to define an anonymous record with `mutable` data.</span></span> <span data-ttu-id="36469-171">Il existe un [ouvrir suggestion de langage](https://github.com/fsharp/fslang-suggestions/issues/732) pour autoriser les données mutables.</span><span class="sxs-lookup"><span data-stu-id="36469-171">There is an [open language suggestion](https://github.com/fsharp/fslang-suggestions/issues/732) to allow mutable data.</span></span>

### <a name="limitations-with-struct-anonymous-records"></a><span data-ttu-id="36469-172">Limitations des enregistrements anonymes struct</span><span class="sxs-lookup"><span data-stu-id="36469-172">Limitations with struct anonymous records</span></span>

<span data-ttu-id="36469-173">Il n’est pas possible de déclarer des enregistrements anonymes sous la forme de struct `IsByRefLike` ou `IsReadOnly`.</span><span class="sxs-lookup"><span data-stu-id="36469-173">It is not possible to declare struct anonymous records as `IsByRefLike` or `IsReadOnly`.</span></span> <span data-ttu-id="36469-174">Il existe un [ouvrir suggestion de langage](https://github.com/fsharp/fslang-suggestions/issues/712) à pour `IsByRefLike` et `IsReadOnly` des enregistrements anonymes.</span><span class="sxs-lookup"><span data-stu-id="36469-174">There is an [open language suggestion](https://github.com/fsharp/fslang-suggestions/issues/712) to for `IsByRefLike` and `IsReadOnly` anonymous records.</span></span>
