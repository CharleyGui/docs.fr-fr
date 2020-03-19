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
# <a name="anonymous-records"></a><span data-ttu-id="c31b7-103">Enregistrements anonymes</span><span class="sxs-lookup"><span data-stu-id="c31b7-103">Anonymous Records</span></span>

<span data-ttu-id="c31b7-104">Les enregistrements anonymes sont des agrégats simples de valeurs nommées qui n’ont pas besoin d’être déclarés avant utilisation.</span><span class="sxs-lookup"><span data-stu-id="c31b7-104">Anonymous records are simple aggregates of named values that don't need to be declared before use.</span></span> <span data-ttu-id="c31b7-105">Vous pouvez les déclarer comme des structs ou des types de référence.</span><span class="sxs-lookup"><span data-stu-id="c31b7-105">You can declare them as either structs or reference types.</span></span> <span data-ttu-id="c31b7-106">Ce sont des types de référence par défaut.</span><span class="sxs-lookup"><span data-stu-id="c31b7-106">They're reference types by default.</span></span>

## <a name="syntax"></a><span data-ttu-id="c31b7-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c31b7-107">Syntax</span></span>

<span data-ttu-id="c31b7-108">Les exemples suivants démontrent la syntaxe anonyme.</span><span class="sxs-lookup"><span data-stu-id="c31b7-108">The following examples demonstrate the anonymous record syntax.</span></span> <span data-ttu-id="c31b7-109">Articles délimités `[item]` en option.</span><span class="sxs-lookup"><span data-stu-id="c31b7-109">Items delimited as `[item]` are optional.</span></span>

```fsharp
// Construct an anonymous record
let value-name = [struct] {| Label1: Type1; Label2: Type2; ...|}

// Use an anonymous record as a type parameter
let value-name = Type-Name<[struct] {| Label1: Type1; Label2: Type2; ...|}>

// Define a parameter with an anonymous record as input
let function-name (arg-name: [struct] {| Label1: Type1; Label2: Type2; ...|}) ...
```

## <a name="basic-usage"></a><span data-ttu-id="c31b7-110">Utilisation de base</span><span class="sxs-lookup"><span data-stu-id="c31b7-110">Basic usage</span></span>

<span data-ttu-id="c31b7-111">Les enregistrements anonymes sont mieux considérés comme des types d’enregistrements F et qui n’ont pas besoin d’être déclarés avant l’instantanéisation.</span><span class="sxs-lookup"><span data-stu-id="c31b7-111">Anonymous records are best thought of as F# record types that don't need to be declared before instantiation.</span></span>

<span data-ttu-id="c31b7-112">Par exemple, voici comment vous pouvez interagir avec une fonction qui produit un enregistrement anonyme :</span><span class="sxs-lookup"><span data-stu-id="c31b7-112">For example, here how you can interact with a function that produces an anonymous record:</span></span>

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

<span data-ttu-id="c31b7-113">L’exemple suivant s’étend sur `printCircleStats` le précédent avec une fonction qui prend un dossier anonyme comme entrée:</span><span class="sxs-lookup"><span data-stu-id="c31b7-113">The following example expands on the previous one with a `printCircleStats` function that takes an anonymous record as input:</span></span>

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

<span data-ttu-id="c31b7-114">Appeler `printCircleStats` avec n’importe quel type d’enregistrement anonyme qui n’a pas la même «forme» que le type d’entrée ne sera pas compiler:</span><span class="sxs-lookup"><span data-stu-id="c31b7-114">Calling `printCircleStats` with any anonymous record type that doesn't have the same "shape" as the input type will fail to compile:</span></span>

```fsharp
printCircleStats r {| Diameter = 2.0; Area = 4.0; MyCircumference = 12.566371 |}
// Two anonymous record types have mismatched sets of field names
// '["Area"; "Circumference"; "Diameter"]' and '["Area"; "Diameter"; "MyCircumference"]'
```

## <a name="struct-anonymous-records"></a><span data-ttu-id="c31b7-115">Structurer des dossiers anonymes</span><span class="sxs-lookup"><span data-stu-id="c31b7-115">Struct anonymous records</span></span>

<span data-ttu-id="c31b7-116">Les enregistrements anonymes peuvent également être `struct` définis comme struct avec le mot clé facultatif.</span><span class="sxs-lookup"><span data-stu-id="c31b7-116">Anonymous records can also be defined as struct with the optional `struct` keyword.</span></span> <span data-ttu-id="c31b7-117">L’exemple suivant augmente le précédent en produisant et en consommant un enregistrement anonyme struct :</span><span class="sxs-lookup"><span data-stu-id="c31b7-117">The following example augments the previous one by producing and consuming a struct anonymous record:</span></span>

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

### <a name="structness-inference"></a><span data-ttu-id="c31b7-118">Inférence de structuration</span><span class="sxs-lookup"><span data-stu-id="c31b7-118">Structness inference</span></span>

<span data-ttu-id="c31b7-119">Les enregistrements anonymes Struct permettent également une « inférence de `struct` la structivité » lorsque vous n’avez pas besoin de spécifier le mot clé sur le site d’appel.</span><span class="sxs-lookup"><span data-stu-id="c31b7-119">Struct anonymous records also allow for "structness inference" where you do not need to specify the `struct` keyword at the call site.</span></span> <span data-ttu-id="c31b7-120">Dans cet exemple, vous `struct` élitez le mot clé lors de l’appel `printCircleStats`:</span><span class="sxs-lookup"><span data-stu-id="c31b7-120">In this example, you elide the `struct` keyword when calling `printCircleStats`:</span></span>

```fsharp

let printCircleStats r (stats: struct {| Area: float; Circumference: float; Diameter: float |}) =
    printfn "Circle with radius: %f has diameter %f, area %f, and circumference %f"
        r stats.Diameter stats.Area stats.Circumference

printCircleStats r {| Area = 4.0; Circumference = 12.6; Diameter = 12.6 |}
```

<span data-ttu-id="c31b7-121">Le modèle inverse `struct` - spécifiant quand le type d’entrée n’est pas un enregistrement anonyme structurant - ne sera pas compilé.</span><span class="sxs-lookup"><span data-stu-id="c31b7-121">The reverse pattern - specifying `struct` when the input type is not a struct anonymous record - will fail to compile.</span></span>

## <a name="embedding-anonymous-records-within-other-types"></a><span data-ttu-id="c31b7-122">Intégrer des dossiers anonymes dans d’autres types</span><span class="sxs-lookup"><span data-stu-id="c31b7-122">Embedding anonymous records within other types</span></span>

<span data-ttu-id="c31b7-123">Il est utile de déclarer [les syndicats discriminés](discriminated-unions.md) dont les cas sont des dossiers.</span><span class="sxs-lookup"><span data-stu-id="c31b7-123">It's useful to declare [discriminated unions](discriminated-unions.md) whose cases are records.</span></span> <span data-ttu-id="c31b7-124">Mais si les données dans les dossiers sont du même type que l’union discriminée, vous devez définir tous les types comme récursifs mutuellement.</span><span class="sxs-lookup"><span data-stu-id="c31b7-124">But if the data in the records is the same type as the discriminated union, you must define all types as mutually recursive.</span></span> <span data-ttu-id="c31b7-125">L’utilisation de dossiers anonymes évite cette restriction.</span><span class="sxs-lookup"><span data-stu-id="c31b7-125">Using anonymous records avoids this restriction.</span></span> <span data-ttu-id="c31b7-126">Ce qui suit est un type d’exemple et la fonction que le modèle correspond à celui-ci:</span><span class="sxs-lookup"><span data-stu-id="c31b7-126">What follows is an example type and function that pattern matches over it:</span></span>

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

## <a name="copy-and-update-expressions"></a><span data-ttu-id="c31b7-127">Copier et mettre à jour les expressions</span><span class="sxs-lookup"><span data-stu-id="c31b7-127">Copy and update expressions</span></span>

<span data-ttu-id="c31b7-128">Les documents anonymes prennent en charge la construction avec [des expressions de copie et de mise à jour.](copy-and-update-record-expressions.md)</span><span class="sxs-lookup"><span data-stu-id="c31b7-128">Anonymous records support construction with [copy and update expressions](copy-and-update-record-expressions.md).</span></span> <span data-ttu-id="c31b7-129">Par exemple, voici comment vous pouvez construire une nouvelle instance d’un enregistrement anonyme qui copie les données d’un enregistrement existant :</span><span class="sxs-lookup"><span data-stu-id="c31b7-129">For example, here's how you can construct a new instance of an anonymous record that copies an existing one's data:</span></span>

```fsharp
let data = {| X = 1; Y = 2 |}
let data' = {| data with Y = 3 |}
```

<span data-ttu-id="c31b7-130">Cependant, contrairement aux enregistrements nommés, les enregistrements anonymes vous permettent de construire des formulaires entièrement différents avec des expressions de copie et de mise à jour.</span><span class="sxs-lookup"><span data-stu-id="c31b7-130">However, unlike named records, anonymous records allow you to construct entirely different forms with copy and update expressions.</span></span> <span data-ttu-id="c31b7-131">L’exemple de suivi prend le même enregistrement anonyme de l’exemple précédent et l’étend dans un nouvel enregistrement anonyme:</span><span class="sxs-lookup"><span data-stu-id="c31b7-131">The follow example takes the same anonymous record from the previous example and expands it into a new anonymous record:</span></span>

```fsharp
let data = {| X = 1; Y = 2 |}
let expandedData = {| data with Z = 3 |} // Gives {| X=1; Y=2; Z=3 |}
```

<span data-ttu-id="c31b7-132">Il est également possible de construire des enregistrements anonymes à partir d’instances de documents nommés :</span><span class="sxs-lookup"><span data-stu-id="c31b7-132">It is also possible to construct anonymous records from instances of named records:</span></span>

```fsharp
type R = { X: int }
let data = { X = 1 }
let data' = {| data with Y = 2 |} // Gives {| X=1; Y=2 |}
```

<span data-ttu-id="c31b7-133">Vous pouvez également copier des données à et depuis et en référant des enregistrements anonymes :</span><span class="sxs-lookup"><span data-stu-id="c31b7-133">You can also copy data to and from reference and struct anonymous records:</span></span>

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

## <a name="properties-of-anonymous-records"></a><span data-ttu-id="c31b7-134">Propriétés de dossiers anonymes</span><span class="sxs-lookup"><span data-stu-id="c31b7-134">Properties of anonymous records</span></span>

<span data-ttu-id="c31b7-135">Les dossiers anonymes ont un certain nombre de caractéristiques qui sont essentielles pour bien comprendre comment ils peuvent être utilisés.</span><span class="sxs-lookup"><span data-stu-id="c31b7-135">Anonymous records have a number of characteristics that are essential to fully understanding how they can be used.</span></span>

### <a name="anonymous-records-are-nominal"></a><span data-ttu-id="c31b7-136">Les dossiers anonymes sont nominaux</span><span class="sxs-lookup"><span data-stu-id="c31b7-136">Anonymous records are nominal</span></span>

<span data-ttu-id="c31b7-137">Les dossiers anonymes sont [des types nominaux](https://en.wikipedia.org/wiki/Nominal_type_system).</span><span class="sxs-lookup"><span data-stu-id="c31b7-137">Anonymous records are [nominal types](https://en.wikipedia.org/wiki/Nominal_type_system).</span></span> <span data-ttu-id="c31b7-138">Ils sont mieux considérés comme des types [d’enregistrement](records.md) nommés (qui sont également nominaux) qui ne nécessitent pas une déclaration à l’avance.</span><span class="sxs-lookup"><span data-stu-id="c31b7-138">They are best thought as named [record](records.md) types (which are also nominal) that do not require an up-front declaration.</span></span>

<span data-ttu-id="c31b7-139">Prenons l’exemple suivant avec deux déclarations d’enregistrement anonymes :</span><span class="sxs-lookup"><span data-stu-id="c31b7-139">Consider the following example with two anonymous record declarations:</span></span>

```fsharp
let x = {| X = 1 |}
let y = {| Y = 1 |}
```

<span data-ttu-id="c31b7-140">Les `x` `y` valeurs et les valeurs ont des types différents et ne sont pas compatibles les unes avec les autres.</span><span class="sxs-lookup"><span data-stu-id="c31b7-140">The `x` and `y` values have different types and are not compatible with one another.</span></span> <span data-ttu-id="c31b7-141">Ils ne sont pas équatables et ils ne sont pas comparables.</span><span class="sxs-lookup"><span data-stu-id="c31b7-141">They are not equatable and they are not comparable.</span></span> <span data-ttu-id="c31b7-142">Pour illustrer cela, considérez un équivalent d’enregistrement nommé :</span><span class="sxs-lookup"><span data-stu-id="c31b7-142">To illustrate this, consider a named record equivalent:</span></span>

```fsharp
type X = { X: int }
type Y = { Y: int }

let x = { X = 1 }
let y = { Y = 1 }
```

<span data-ttu-id="c31b7-143">Il n’y a rien d’intrinsèquement différent dans les enregistrements anonymes par rapport à leurs équivalents d’enregistrement nommés en ce qui concerne l’équivalence de type ou la comparaison.</span><span class="sxs-lookup"><span data-stu-id="c31b7-143">There isn't anything inherently different about anonymous records when compared with their named record equivalents when concerning type equivalency or comparison.</span></span>

### <a name="anonymous-records-use-structural-equality-and-comparison"></a><span data-ttu-id="c31b7-144">Les documents anonymes utilisent l’égalité structurelle et la comparaison</span><span class="sxs-lookup"><span data-stu-id="c31b7-144">Anonymous records use structural equality and comparison</span></span>

<span data-ttu-id="c31b7-145">Comme les types d’enregistrements, les dossiers anonymes sont structurellement équatables et comparables.</span><span class="sxs-lookup"><span data-stu-id="c31b7-145">Like record types, anonymous records are structurally equatable and comparable.</span></span> <span data-ttu-id="c31b7-146">Cela n’est vrai que si tous les types de constituants sont en faveur de l’égalité et de la comparaison, comme avec les types de disques.</span><span class="sxs-lookup"><span data-stu-id="c31b7-146">This is only true if all constituent types support equality and comparison, like with record types.</span></span> <span data-ttu-id="c31b7-147">Pour soutenir l’égalité ou la comparaison, deux dossiers anonymes doivent avoir la même « forme ».</span><span class="sxs-lookup"><span data-stu-id="c31b7-147">To support equality or comparison, two anonymous records must have the same "shape".</span></span>

```fsharp
{| a = 1+1 |} = {| a = 2 |} // true
{| a = 1+1 |} > {| a = 1 |} // true

// error FS0001: Two anonymous record types have mismatched sets of field names '["a"]' and '["a"; "b"]'
{| a = 1 + 1 |} = {| a = 2;  b = 1|}
```

### <a name="anonymous-records-are-serializable"></a><span data-ttu-id="c31b7-148">Les dossiers anonymes sont sérialisables</span><span class="sxs-lookup"><span data-stu-id="c31b7-148">Anonymous records are serializable</span></span>

<span data-ttu-id="c31b7-149">Vous pouvez sérialiser des enregistrements anonymes comme vous le pouvez avec les enregistrements nommés.</span><span class="sxs-lookup"><span data-stu-id="c31b7-149">You can serialize anonymous records just as you can with named records.</span></span> <span data-ttu-id="c31b7-150">Voici un exemple en utilisant [Newtonsoft.Json](https://www.nuget.org/packages/Newtonsoft.Json/):</span><span class="sxs-lookup"><span data-stu-id="c31b7-150">Here is an example using [Newtonsoft.Json](https://www.nuget.org/packages/Newtonsoft.Json/):</span></span>

```fsharp
open Newtonsoft.Json

let phillip' = {| name="Phillip"; age=28 |}
let philStr = JsonConvert.SerializeObject(phillip')

let phillip = JsonConvert.DeserializeObject<{|name: string; age: int|}>(philStr)
printfn "Name: %s Age: %d" phillip.name phillip.age
```

<span data-ttu-id="c31b7-151">Les enregistrements anonymes sont utiles pour envoyer des données légères sur un réseau sans avoir besoin de définir un domaine pour vos types sérialisés/déséialisés à l’avance.</span><span class="sxs-lookup"><span data-stu-id="c31b7-151">Anonymous records are useful for sending lightweight data over a network without the need to define a domain for your serialized/deserialized types up front.</span></span>

### <a name="anonymous-records-interoperate-with-c-anonymous-types"></a><span data-ttu-id="c31b7-152">Les dossiers anonymes s’interopément avec les types d’anonymes C</span><span class="sxs-lookup"><span data-stu-id="c31b7-152">Anonymous records interoperate with C# anonymous types</span></span>

<span data-ttu-id="c31b7-153">Il est possible d’utiliser une API .NET qui nécessite l’utilisation de [types D.C. anonymes](../../csharp/programming-guide/classes-and-structs/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="c31b7-153">It is possible to use a .NET API that requires the use of [C# anonymous types](../../csharp/programming-guide/classes-and-structs/anonymous-types.md).</span></span> <span data-ttu-id="c31b7-154">Les types anonymes Cmd sont insignifiants à interopérer en utilisant des dossiers anonymes.</span><span class="sxs-lookup"><span data-stu-id="c31b7-154">C# anonymous types are trivial to interoperate with by using anonymous records.</span></span> <span data-ttu-id="c31b7-155">L’exemple suivant montre comment utiliser des dossiers anonymes pour appeler une surcharge [LINQ](../../csharp/programming-guide/concepts/linq/index.md) qui nécessite un type anonyme :</span><span class="sxs-lookup"><span data-stu-id="c31b7-155">The following example shows how to use anonymous records to call a [LINQ](../../csharp/programming-guide/concepts/linq/index.md) overload that requires an anonymous type:</span></span>

```fsharp
open System.Linq

let names = [ "Ana"; "Felipe"; "Emilia"]
let nameGrouping = names.Select(fun n -> {| Name = n; FirstLetter = n.[0] |})
for ng in nameGrouping do
    printfn "%s has first letter %c" ng.Name ng.FirstLetter
```

<span data-ttu-id="c31b7-156">Il existe une multitude d’autres API utilisées sur .NET qui nécessitent l’utilisation de la transmission dans un type anonyme.</span><span class="sxs-lookup"><span data-stu-id="c31b7-156">There are a multitude of other APIs used throughout .NET that require the use of passing in an anonymous type.</span></span> <span data-ttu-id="c31b7-157">Les dossiers anonymes sont votre outil pour travailler avec eux.</span><span class="sxs-lookup"><span data-stu-id="c31b7-157">Anonymous records are your tool for working with them.</span></span>

## <a name="limitations"></a><span data-ttu-id="c31b7-158">Limites</span><span class="sxs-lookup"><span data-stu-id="c31b7-158">Limitations</span></span>

<span data-ttu-id="c31b7-159">Les dossiers anonymes ont certaines restrictions dans leur utilisation.</span><span class="sxs-lookup"><span data-stu-id="c31b7-159">Anonymous records have some restrictions in their usage.</span></span> <span data-ttu-id="c31b7-160">Certains sont inhérents à leur conception, mais d’autres sont agréables à changer.</span><span class="sxs-lookup"><span data-stu-id="c31b7-160">Some are inherent to their design, but others are amenable to change.</span></span>

### <a name="limitations-with-pattern-matching"></a><span data-ttu-id="c31b7-161">Limitations avec l’appariement des motifs</span><span class="sxs-lookup"><span data-stu-id="c31b7-161">Limitations with pattern matching</span></span>

<span data-ttu-id="c31b7-162">Les dossiers anonymes ne prennent pas en charge l’appariement des motifs, contrairement aux enregistrements nommés.</span><span class="sxs-lookup"><span data-stu-id="c31b7-162">Anonymous records do not support pattern matching, unlike named records.</span></span> <span data-ttu-id="c31b7-163">Il y a trois raisons :</span><span class="sxs-lookup"><span data-stu-id="c31b7-163">There are three reasons:</span></span>

1. <span data-ttu-id="c31b7-164">Un modèle devrait rendre compte de chaque domaine d’un enregistrement anonyme, contrairement aux types d’enregistrement nommés.</span><span class="sxs-lookup"><span data-stu-id="c31b7-164">A pattern would have to account for every field of an anonymous record, unlike named record types.</span></span> <span data-ttu-id="c31b7-165">C’est parce que les dossiers anonymes ne prennent pas en charge le sous-typage structurel - ce sont des types nominaux.</span><span class="sxs-lookup"><span data-stu-id="c31b7-165">This is because anonymous records do not support structural subtyping – they are nominal types.</span></span>
2. <span data-ttu-id="c31b7-166">En raison de (1), il n’y a aucune capacité d’avoir des modèles supplémentaires dans une expression de correspondance de modèle, comme chaque modèle distinct impliquerait un type d’enregistrement anonyme différent.</span><span class="sxs-lookup"><span data-stu-id="c31b7-166">Because of (1), there is no ability to have additional patterns in a pattern match expression, as each distinct pattern would imply a different anonymous record type.</span></span>
3. <span data-ttu-id="c31b7-167">En raison de (3), tout modèle d’enregistrement anonyme serait plus verbeux que l’utilisation de la notation "point".</span><span class="sxs-lookup"><span data-stu-id="c31b7-167">Because of (3), any anonymous record pattern would be more verbose than the use of “dot” notation.</span></span>

<span data-ttu-id="c31b7-168">Il y a une suggestion de langage ouvert pour [permettre l’appariement des modèles dans des contextes limités.](https://github.com/fsharp/fslang-suggestions/issues/713)</span><span class="sxs-lookup"><span data-stu-id="c31b7-168">There is an open language suggestion to [allow pattern matching in limited contexts](https://github.com/fsharp/fslang-suggestions/issues/713).</span></span>

### <a name="limitations-with-mutability"></a><span data-ttu-id="c31b7-169">Limitations avec mutabilité</span><span class="sxs-lookup"><span data-stu-id="c31b7-169">Limitations with mutability</span></span>

<span data-ttu-id="c31b7-170">Il n’est pas actuellement possible `mutable` de définir un enregistrement anonyme avec des données.</span><span class="sxs-lookup"><span data-stu-id="c31b7-170">It is not currently possible to define an anonymous record with `mutable` data.</span></span> <span data-ttu-id="c31b7-171">Il existe une [suggestion en langage ouvert](https://github.com/fsharp/fslang-suggestions/issues/732) pour permettre des données mutables.</span><span class="sxs-lookup"><span data-stu-id="c31b7-171">There is an [open language suggestion](https://github.com/fsharp/fslang-suggestions/issues/732) to allow mutable data.</span></span>

### <a name="limitations-with-struct-anonymous-records"></a><span data-ttu-id="c31b7-172">Limitations avec la struction des dossiers anonymes</span><span class="sxs-lookup"><span data-stu-id="c31b7-172">Limitations with struct anonymous records</span></span>

<span data-ttu-id="c31b7-173">Il n’est pas possible de `IsByRefLike` `IsReadOnly`déclarer des documents anonymes structurants comme ou .</span><span class="sxs-lookup"><span data-stu-id="c31b7-173">It is not possible to declare struct anonymous records as `IsByRefLike` or `IsReadOnly`.</span></span> <span data-ttu-id="c31b7-174">Il y a une `IsByRefLike` suggestion `IsReadOnly` de [langage ouvert](https://github.com/fsharp/fslang-suggestions/issues/712) pour les dossiers anonymes et les dossiers.</span><span class="sxs-lookup"><span data-stu-id="c31b7-174">There is an [open language suggestion](https://github.com/fsharp/fslang-suggestions/issues/712) to for `IsByRefLike` and `IsReadOnly` anonymous records.</span></span>
