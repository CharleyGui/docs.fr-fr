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
# <a name="anonymous-records"></a><span data-ttu-id="068e9-103">Enregistrements anonymes</span><span class="sxs-lookup"><span data-stu-id="068e9-103">Anonymous Records</span></span>

<span data-ttu-id="068e9-104">Les enregistrements anonymes sont des agrégats simples de valeurs nommées qui n’ont pas besoin d’être déclarés avant leur utilisation.</span><span class="sxs-lookup"><span data-stu-id="068e9-104">Anonymous records are simple aggregates of named values that don't need to be declared before use.</span></span> <span data-ttu-id="068e9-105">Vous pouvez les déclarer comme des structs ou des types référence.</span><span class="sxs-lookup"><span data-stu-id="068e9-105">You can declare them as either structs or reference types.</span></span> <span data-ttu-id="068e9-106">Ils sont des types référence par défaut.</span><span class="sxs-lookup"><span data-stu-id="068e9-106">They're reference types by default.</span></span>

## <a name="syntax"></a><span data-ttu-id="068e9-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="068e9-107">Syntax</span></span>

<span data-ttu-id="068e9-108">Les exemples suivants illustrent la syntaxe d’enregistrement anonyme.</span><span class="sxs-lookup"><span data-stu-id="068e9-108">The following examples demonstrate the anonymous record syntax.</span></span> <span data-ttu-id="068e9-109">Les éléments délimités comme `[item]` sont facultatifs.</span><span class="sxs-lookup"><span data-stu-id="068e9-109">Items delimited as `[item]` are optional.</span></span>

```fsharp
// Construct an anonymous record
let value-name = [struct] {| Label1: Type1; Label2: Type2; ...|}

// Use an anonymous record as a type parameter
let value-name = Type-Name<[struct] {| Label1: Type1; Label2: Type2; ...|}>

// Define a parameter with an anonymous record as input
let function-name (arg-name: [struct] {| Label1: Type1; Label2: Type2; ...|}) ...
```

## <a name="basic-usage"></a><span data-ttu-id="068e9-110">Utilisation de base</span><span class="sxs-lookup"><span data-stu-id="068e9-110">Basic usage</span></span>

<span data-ttu-id="068e9-111">Il est préférable de considérer les enregistrements F# anonymes comme des types d’enregistrements qui n’ont pas besoin d’être déclarés avant l’instanciation.</span><span class="sxs-lookup"><span data-stu-id="068e9-111">Anonymous records are best thought of as F# record types that don't need to be declared before instantiation.</span></span>

<span data-ttu-id="068e9-112">Par exemple, ici, vous pouvez interagir avec une fonction qui produit un enregistrement anonyme :</span><span class="sxs-lookup"><span data-stu-id="068e9-112">For example, here how you can interact with a function that produces an anonymous record:</span></span>

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

<span data-ttu-id="068e9-113">L’exemple suivant développe le précédent avec une fonction `printCircleStats` qui accepte un enregistrement anonyme comme entrée :</span><span class="sxs-lookup"><span data-stu-id="068e9-113">The following example expands on the previous one with a `printCircleStats` function that takes an anonymous record as input:</span></span>

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

<span data-ttu-id="068e9-114">L’appel de `printCircleStats` avec un type d’enregistrement anonyme qui n’a pas la même « forme » comme type d’entrée ne peut pas être compilé :</span><span class="sxs-lookup"><span data-stu-id="068e9-114">Calling `printCircleStats` with any anonymous record type that doesn't have the same "shape" as the input type will fail to compile:</span></span>

```fsharp
printCircleStats r {| Diameter = 2.0; Area = 4.0; MyCircumference = 12.566371 |}
// Two anonymous record types have mismatched sets of field names
// '["Area"; "Circumference"; "Diameter"]' and '["Area"; "Diameter"; "MyCircumference"]'
```

## <a name="struct-anonymous-records"></a><span data-ttu-id="068e9-115">Structurer des enregistrements anonymes</span><span class="sxs-lookup"><span data-stu-id="068e9-115">Struct anonymous records</span></span>

<span data-ttu-id="068e9-116">Les enregistrements anonymes peuvent également être définis comme struct avec le mot clé facultatif `struct`.</span><span class="sxs-lookup"><span data-stu-id="068e9-116">Anonymous records can also be defined as struct with the optional `struct` keyword.</span></span> <span data-ttu-id="068e9-117">L’exemple suivant augmente le précédent en générant et en consommant un enregistrement anonyme de structure :</span><span class="sxs-lookup"><span data-stu-id="068e9-117">The following example augments the previous one by producing and consuming a struct anonymous record:</span></span>

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

### <a name="structness-inference"></a><span data-ttu-id="068e9-118">Inférence de la structure</span><span class="sxs-lookup"><span data-stu-id="068e9-118">Structness inference</span></span>

<span data-ttu-id="068e9-119">Les enregistrements anonymes de struct autorisent également l’inférence de la structure, où vous n’avez pas besoin de spécifier le mot clé `struct` sur le site d’appel.</span><span class="sxs-lookup"><span data-stu-id="068e9-119">Struct anonymous records also allow for "structness inference" where you do not need to specify the `struct` keyword at the call site.</span></span> <span data-ttu-id="068e9-120">Dans cet exemple, vous Elide le mot clé `struct` lors de l’appel de `printCircleStats`:</span><span class="sxs-lookup"><span data-stu-id="068e9-120">In this example, you elide the `struct` keyword when calling `printCircleStats`:</span></span>

```fsharp

let printCircleStats r (stats: struct {| Area: float; Circumference: float; Diameter: float |}) =
    printfn "Circle with radius: %f has diameter %f, area %f, and circumference %f"
        r stats.Diameter stats.Area stats.Circumference

printCircleStats r {| Area = 4.0; Circumference = 12.6; Diameter = 12.6 |}
```

<span data-ttu-id="068e9-121">Le modèle inverse, qui spécifie `struct` lorsque le type d’entrée n’est pas un enregistrement anonyme de struct, ne peut pas être compilé.</span><span class="sxs-lookup"><span data-stu-id="068e9-121">The reverse pattern - specifying `struct` when the input type is not a struct anonymous record - will fail to compile.</span></span>

## <a name="embedding-anonymous-records-within-other-types"></a><span data-ttu-id="068e9-122">Incorporation d’enregistrements anonymes dans d’autres types</span><span class="sxs-lookup"><span data-stu-id="068e9-122">Embedding anonymous records within other types</span></span>

<span data-ttu-id="068e9-123">Il est utile de déclarer des [unions discriminées](discriminated-unions.md) dont les cas sont des enregistrements.</span><span class="sxs-lookup"><span data-stu-id="068e9-123">It's useful to declare [discriminated unions](discriminated-unions.md) whose cases are records.</span></span> <span data-ttu-id="068e9-124">Toutefois, si les données des enregistrements sont du même type que l’union discriminée, vous devez définir tous les types comme étant mutuellement récursifs.</span><span class="sxs-lookup"><span data-stu-id="068e9-124">But if the data in the records is the same type as the discriminated union, you must define all types as mutually recursive.</span></span> <span data-ttu-id="068e9-125">L’utilisation d’enregistrements anonymes évite cette restriction.</span><span class="sxs-lookup"><span data-stu-id="068e9-125">Using anonymous records avoids this restriction.</span></span> <span data-ttu-id="068e9-126">Ce qui suit est un exemple de type et de fonction qui correspond au modèle :</span><span class="sxs-lookup"><span data-stu-id="068e9-126">What follows is an example type and function that pattern matches over it:</span></span>

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

## <a name="copy-and-update-expressions"></a><span data-ttu-id="068e9-127">Copier et mettre à jour des expressions</span><span class="sxs-lookup"><span data-stu-id="068e9-127">Copy and update expressions</span></span>

<span data-ttu-id="068e9-128">Les enregistrements anonymes prennent en charge la construction avec des [expressions de copie et de mise à jour](copy-and-update-record-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="068e9-128">Anonymous records support construction with [copy and update expressions](copy-and-update-record-expressions.md).</span></span> <span data-ttu-id="068e9-129">Par exemple, voici comment vous pouvez construire une nouvelle instance d’un enregistrement anonyme qui copie les données d’un existant :</span><span class="sxs-lookup"><span data-stu-id="068e9-129">For example, here's how you can construct a new instance of an anonymous record that copies an existing one's data:</span></span>

```fsharp
let data = {| X = 1; Y = 2 |}
let data' = {| data with Y = 3 |}
```

<span data-ttu-id="068e9-130">Toutefois, contrairement aux enregistrements nommés, les enregistrements anonymes vous permettent de construire des formulaires entièrement différents avec des expressions de copie et de mise à jour.</span><span class="sxs-lookup"><span data-stu-id="068e9-130">However, unlike named records, anonymous records allow you to construct entirely different forms with copy and update expressions.</span></span> <span data-ttu-id="068e9-131">L’exemple suivant prend le même enregistrement anonyme de l’exemple précédent et le développe dans un nouvel enregistrement anonyme :</span><span class="sxs-lookup"><span data-stu-id="068e9-131">The follow example takes the same anonymous record from the previous example and expands it into a new anonymous record:</span></span>

```fsharp
let data = {| X = 1; Y = 2 |}
let expandedData = {| data with Z = 3 |} // Gives {| X=1; Y=2; Z=3 |}
```

<span data-ttu-id="068e9-132">Il est également possible de construire des enregistrements anonymes à partir d’instances d’enregistrements nommés :</span><span class="sxs-lookup"><span data-stu-id="068e9-132">It is also possible to construct anonymous records from instances of named records:</span></span>

```fsharp
type R = { X: int }
let data = { X = 1 }
let data' = {| data with Y = 2 |} // Gives {| X=1; Y=2 |}
```

<span data-ttu-id="068e9-133">Vous pouvez également copier des données vers et depuis des enregistrements anonymes de référence et de structure :</span><span class="sxs-lookup"><span data-stu-id="068e9-133">You can also copy data to and from reference and struct anonymous records:</span></span>

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

## <a name="properties-of-anonymous-records"></a><span data-ttu-id="068e9-134">Propriétés des enregistrements anonymes</span><span class="sxs-lookup"><span data-stu-id="068e9-134">Properties of anonymous records</span></span>

<span data-ttu-id="068e9-135">Les enregistrements anonymes ont un certain nombre de caractéristiques qui sont essentielles pour comprendre parfaitement comment les utiliser.</span><span class="sxs-lookup"><span data-stu-id="068e9-135">Anonymous records have a number of characteristics that are essential to fully understanding how they can be used.</span></span>

### <a name="anonymous-records-are-nominal"></a><span data-ttu-id="068e9-136">Les enregistrements anonymes sont nominaux</span><span class="sxs-lookup"><span data-stu-id="068e9-136">Anonymous records are nominal</span></span>

<span data-ttu-id="068e9-137">Les enregistrements anonymes sont des [types nominaux](https://en.wikipedia.org/wiki/Nominal_type_system).</span><span class="sxs-lookup"><span data-stu-id="068e9-137">Anonymous records are [nominal types](https://en.wikipedia.org/wiki/Nominal_type_system).</span></span> <span data-ttu-id="068e9-138">Ils sont mieux considérés comme des types d' [enregistrements](records.md) nommés (qui sont également nominaux) qui ne nécessitent pas de déclaration initiale.</span><span class="sxs-lookup"><span data-stu-id="068e9-138">They are best thought as named [record](records.md) types (which are also nominal) that do not require an up-front declaration.</span></span>

<span data-ttu-id="068e9-139">Prenons l’exemple suivant avec deux déclarations d’enregistrement anonymes :</span><span class="sxs-lookup"><span data-stu-id="068e9-139">Consider the following example with two anonymous record declarations:</span></span>

```fsharp
let x = {| X = 1 |}
let y = {| Y = 1 |}
```

<span data-ttu-id="068e9-140">Les valeurs `x` et `y` ont des types différents et ne sont pas compatibles les unes avec les autres.</span><span class="sxs-lookup"><span data-stu-id="068e9-140">The `x` and `y` values have different types and are not compatible with one another.</span></span> <span data-ttu-id="068e9-141">Elles ne sont pas équivalentes et ne sont pas comparables.</span><span class="sxs-lookup"><span data-stu-id="068e9-141">They are not equatable and they are not comparable.</span></span> <span data-ttu-id="068e9-142">Pour illustrer cela, imaginez un enregistrement nommé équivalent :</span><span class="sxs-lookup"><span data-stu-id="068e9-142">To illustrate this, consider a named record equivalent:</span></span>

```fsharp
type X = { X: int }
type Y = { Y: int }

let x = { X = 1 }
let y = { Y = 1 }
```

<span data-ttu-id="068e9-143">Il n’existe pas de différences inhérentes par rapport aux enregistrements anonymes lorsqu’ils sont comparés à leurs équivalents d’enregistrement nommés lorsqu’ils concernent l’équivalence de type ou la comparaison.</span><span class="sxs-lookup"><span data-stu-id="068e9-143">There isn't anything inherently different about anonymous records when compared with their named record equivalents when concerning type equivalency or comparison.</span></span>

### <a name="anonymous-records-use-structural-equality-and-comparison"></a><span data-ttu-id="068e9-144">Les enregistrements anonymes utilisent l’égalité et la comparaison structurelles</span><span class="sxs-lookup"><span data-stu-id="068e9-144">Anonymous records use structural equality and comparison</span></span>

<span data-ttu-id="068e9-145">Comme les types d’enregistrements, les enregistrements anonymes sont structurellement équivalents et comparables.</span><span class="sxs-lookup"><span data-stu-id="068e9-145">Like record types, anonymous records are structurally equatable and comparable.</span></span> <span data-ttu-id="068e9-146">Cela est vrai uniquement si tous les types constitutifs prennent en charge l’égalité et la comparaison, comme avec les types d’enregistrements.</span><span class="sxs-lookup"><span data-stu-id="068e9-146">This is only true if all constituent types support equality and comparison, like with record types.</span></span> <span data-ttu-id="068e9-147">Pour prendre en charge l’égalité ou la comparaison, deux enregistrements anonymes doivent avoir la même « forme ».</span><span class="sxs-lookup"><span data-stu-id="068e9-147">To support equality or comparison, two anonymous records must have the same "shape".</span></span>

```fsharp
{| a = 1+1 |} = {| a = 2 |} // true
{| a = 1+1 |} > {| a = 1 |} // true

// error FS0001: Two anonymous record types have mismatched sets of field names '["a"]' and '["a"; "b"]'
{| a = 1 + 1 |} = {| a = 2;  b = 1|}
```

### <a name="anonymous-records-are-serializable"></a><span data-ttu-id="068e9-148">Les enregistrements anonymes sont sérialisables</span><span class="sxs-lookup"><span data-stu-id="068e9-148">Anonymous records are serializable</span></span>

<span data-ttu-id="068e9-149">Vous pouvez sérialiser des enregistrements anonymes de la même façon que vous le feriez avec des enregistrements nommés.</span><span class="sxs-lookup"><span data-stu-id="068e9-149">You can serialize anonymous records just as you can with named records.</span></span> <span data-ttu-id="068e9-150">Voici un exemple d’utilisation de [Newtonsoft. JSON](https://www.nuget.org/packages/Newtonsoft.Json/):</span><span class="sxs-lookup"><span data-stu-id="068e9-150">Here is an example using [Newtonsoft.Json](https://www.nuget.org/packages/Newtonsoft.Json/):</span></span>

```fsharp
open Newtonsoft.Json

let phillip' = {| name="Phillip"; age=28 |}
let philStr = JsonConvert.SerializeObject(phillip') 

let phillip = JsonConvert.DeserializeObject<{|name: string; age: int|}>(philStr)
printfn "Name: %s Age: %d" phillip.name phillip.age
```

<span data-ttu-id="068e9-151">Les enregistrements anonymes sont utiles pour envoyer des données légères sur un réseau sans avoir à définir un domaine pour vos types sérialisés/désérialisés à l’avance.</span><span class="sxs-lookup"><span data-stu-id="068e9-151">Anonymous records are useful for sending lightweight data over a network without the need to define a domain for your serialized/deserialized types up front.</span></span>

### <a name="anonymous-records-interoperate-with-c-anonymous-types"></a><span data-ttu-id="068e9-152">Les enregistrements anonymes interagissent avec les C# types anonymes</span><span class="sxs-lookup"><span data-stu-id="068e9-152">Anonymous records interoperate with C# anonymous types</span></span>

<span data-ttu-id="068e9-153">Il est possible d’utiliser une API .net qui requiert l’utilisation de [ C# types anonymes](../../csharp/programming-guide/classes-and-structs/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="068e9-153">It is possible to use a .NET API that requires the use of [C# anonymous types](../../csharp/programming-guide/classes-and-structs/anonymous-types.md).</span></span> <span data-ttu-id="068e9-154">C#les types anonymes sont trivials pour interagir avec à l’aide d’enregistrements anonymes.</span><span class="sxs-lookup"><span data-stu-id="068e9-154">C# anonymous types are trivial to interoperate with by using anonymous records.</span></span> <span data-ttu-id="068e9-155">L’exemple suivant montre comment utiliser des enregistrements anonymes pour appeler une surcharge [LINQ](../../csharp/programming-guide/concepts/linq/index.md) qui requiert un type anonyme :</span><span class="sxs-lookup"><span data-stu-id="068e9-155">The following example shows how to use anonymous records to call a [LINQ](../../csharp/programming-guide/concepts/linq/index.md) overload that requires an anonymous type:</span></span>

```fsharp
open System.Linq

let names = [ "Ana"; "Felipe"; "Emilia"]
let nameGrouping = names.Select(fun n -> {| Name = n; FirstLetter = n.[0] |})
for ng in nameGrouping do
    printfn "%s has first letter %c" ng.Name ng.FirstLetter
```

<span data-ttu-id="068e9-156">Il existe une multitude d’autres API utilisées dans .NET qui nécessitent l’utilisation du passage d’un type anonyme.</span><span class="sxs-lookup"><span data-stu-id="068e9-156">There are a multitude of other APIs used throughout .NET that require the use of passing in an anonymous type.</span></span> <span data-ttu-id="068e9-157">Les enregistrements anonymes sont un outil qui vous aide à les utiliser.</span><span class="sxs-lookup"><span data-stu-id="068e9-157">Anonymous records are your tool for working with them.</span></span>

## <a name="limitations"></a><span data-ttu-id="068e9-158">Limites</span><span class="sxs-lookup"><span data-stu-id="068e9-158">Limitations</span></span>

<span data-ttu-id="068e9-159">L’utilisation des enregistrements anonymes est soumise à certaines restrictions.</span><span class="sxs-lookup"><span data-stu-id="068e9-159">Anonymous records have some restrictions in their usage.</span></span> <span data-ttu-id="068e9-160">Certains sont inhérents à leur conception, mais d’autres sont susceptibles d’être modifiés.</span><span class="sxs-lookup"><span data-stu-id="068e9-160">Some are inherent to their design, but others are amenable to change.</span></span>

### <a name="limitations-with-pattern-matching"></a><span data-ttu-id="068e9-161">Limitations avec les critères spéciaux</span><span class="sxs-lookup"><span data-stu-id="068e9-161">Limitations with pattern matching</span></span>

<span data-ttu-id="068e9-162">Les enregistrements anonymes ne prennent pas en charge les critères spéciaux, contrairement aux enregistrements nommés.</span><span class="sxs-lookup"><span data-stu-id="068e9-162">Anonymous records do not support pattern matching, unlike named records.</span></span> <span data-ttu-id="068e9-163">Il y a trois raisons à cela :</span><span class="sxs-lookup"><span data-stu-id="068e9-163">There are three reasons:</span></span>

1. <span data-ttu-id="068e9-164">Un modèle devrait prendre en compte tous les champs d’un enregistrement anonyme, à la différence des types d’enregistrements nommés.</span><span class="sxs-lookup"><span data-stu-id="068e9-164">A pattern would have to account for every field of an anonymous record, unlike named record types.</span></span> <span data-ttu-id="068e9-165">Cela est dû au fait que les enregistrements anonymes ne prennent pas en charge le sous-typage structurel : il s’agit de types nominaux.</span><span class="sxs-lookup"><span data-stu-id="068e9-165">This is because anonymous records do not support structural subtyping – they are nominal types.</span></span>
2. <span data-ttu-id="068e9-166">En raison de (1), il n’est pas possible d’avoir des modèles supplémentaires dans une expression de correspondance de modèle, car chaque modèle distinct impliquerait un type d’enregistrement anonyme différent.</span><span class="sxs-lookup"><span data-stu-id="068e9-166">Because of (1), there is no ability to have additional patterns in a pattern match expression, as each distinct pattern would imply a different anonymous record type.</span></span>
3. <span data-ttu-id="068e9-167">En raison de (3), tout modèle d’enregistrement anonyme serait plus détaillé que l’utilisation de la notation « point ».</span><span class="sxs-lookup"><span data-stu-id="068e9-167">Because of (3), any anonymous record pattern would be more verbose than the use of “dot” notation.</span></span>

<span data-ttu-id="068e9-168">Une suggestion de langue ouverte permet d' [autoriser les critères spéciaux dans les contextes limités](https://github.com/fsharp/fslang-suggestions/issues/713).</span><span class="sxs-lookup"><span data-stu-id="068e9-168">There is an open language suggestion to [allow pattern matching in limited contexts](https://github.com/fsharp/fslang-suggestions/issues/713).</span></span>

### <a name="limitations-with-mutability"></a><span data-ttu-id="068e9-169">Limitations avec mutabilité</span><span class="sxs-lookup"><span data-stu-id="068e9-169">Limitations with mutability</span></span>

<span data-ttu-id="068e9-170">Il n’est actuellement pas possible de définir un enregistrement anonyme avec `mutable` données.</span><span class="sxs-lookup"><span data-stu-id="068e9-170">It is not currently possible to define an anonymous record with `mutable` data.</span></span> <span data-ttu-id="068e9-171">Il existe une [suggestion de langue ouverte](https://github.com/fsharp/fslang-suggestions/issues/732) pour autoriser les données mutables.</span><span class="sxs-lookup"><span data-stu-id="068e9-171">There is an [open language suggestion](https://github.com/fsharp/fslang-suggestions/issues/732) to allow mutable data.</span></span>

### <a name="limitations-with-struct-anonymous-records"></a><span data-ttu-id="068e9-172">Limitations des enregistrements anonymes de struct</span><span class="sxs-lookup"><span data-stu-id="068e9-172">Limitations with struct anonymous records</span></span>

<span data-ttu-id="068e9-173">Il n’est pas possible de déclarer des enregistrements anonymes de struct en tant que `IsByRefLike` ou `IsReadOnly`.</span><span class="sxs-lookup"><span data-stu-id="068e9-173">It is not possible to declare struct anonymous records as `IsByRefLike` or `IsReadOnly`.</span></span> <span data-ttu-id="068e9-174">Il existe une [suggestion de langue ouverte](https://github.com/fsharp/fslang-suggestions/issues/712) pour pour `IsByRefLike` et `IsReadOnly` des enregistrements anonymes.</span><span class="sxs-lookup"><span data-stu-id="068e9-174">There is an [open language suggestion](https://github.com/fsharp/fslang-suggestions/issues/712) to for `IsByRefLike` and `IsReadOnly` anonymous records.</span></span>
