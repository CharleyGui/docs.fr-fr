---
title: 'Nouveautés du guide F # 5,0-F #'
description: 'Profitez d’une vue d’ensemble des nouvelles fonctionnalités disponibles dans F # 5,0.'
ms.date: 11/06/2020
ms.openlocfilehash: 0c4c9f42c63a1dc8c90213c43edbadd4061c132d
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94445831"
---
# <a name="whats-new-in-f-50"></a><span data-ttu-id="5f85f-103">Nouveautés de F # 5,0</span><span class="sxs-lookup"><span data-stu-id="5f85f-103">What's new in F# 5.0</span></span>

<span data-ttu-id="5f85f-104">F # 5,0 ajoute plusieurs améliorations au langage F # et F# Interactive.</span><span class="sxs-lookup"><span data-stu-id="5f85f-104">F# 5.0 adds several improvements to the F# language and F# Interactive.</span></span> <span data-ttu-id="5f85f-105">Il est publié avec **.net 5**.</span><span class="sxs-lookup"><span data-stu-id="5f85f-105">It is released with **.NET 5**.</span></span>

## <a name="get-started"></a><span data-ttu-id="5f85f-106">Prise en main</span><span class="sxs-lookup"><span data-stu-id="5f85f-106">Get started</span></span>

<span data-ttu-id="5f85f-107">F # 5,0 est disponible dans toutes les distributions .NET Core et les outils Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="5f85f-107">F# 5.0 is available in all .NET Core distributions and Visual Studio tooling.</span></span> <span data-ttu-id="5f85f-108">Pour plus d’informations, consultez la page [prise en main de F #](../get-started/index.md) pour en savoir plus.</span><span class="sxs-lookup"><span data-stu-id="5f85f-108">For more information, see [Get started with F#](../get-started/index.md) to learn more.</span></span>

## <a name="package-references-in-f-scripts"></a><span data-ttu-id="5f85f-109">Références de package dans les scripts F #</span><span class="sxs-lookup"><span data-stu-id="5f85f-109">Package references in F# scripts</span></span>

<span data-ttu-id="5f85f-110">F # 5 offre une prise en charge des références de package dans les scripts F # avec la `#r "nuget:..."` syntaxe.</span><span class="sxs-lookup"><span data-stu-id="5f85f-110">F# 5 brings support for package references in F# scripts with `#r "nuget:..."` syntax.</span></span> <span data-ttu-id="5f85f-111">Par exemple, considérez la référence de package suivante :</span><span class="sxs-lookup"><span data-stu-id="5f85f-111">For example, consider the following package reference:</span></span>

```fsharp
#r "nuget: Newtonsoft.Json"

open Newtonsoft.Json

let o = {| X = 2; Y = "Hello" |}

printfn "%s" (JsonConvert.SerializeObject o)
```

<span data-ttu-id="5f85f-112">Vous pouvez également fournir une version explicite après le nom du package comme suit :</span><span class="sxs-lookup"><span data-stu-id="5f85f-112">You can also supply an explicit version after the name of the package like this:</span></span>

```fsharp
#r "nuget: Newtonsoft.Json,11.0.1"
```

<span data-ttu-id="5f85f-113">Les références de package prennent en charge les packages avec des dépendances natives, telles que ML.NET.</span><span class="sxs-lookup"><span data-stu-id="5f85f-113">Package references support packages with native dependencies, such as ML.NET.</span></span>

<span data-ttu-id="5f85f-114">Les références de package prennent également en charge les packages avec des exigences spéciales relatives au référencement des s dépendants `.dll` .</span><span class="sxs-lookup"><span data-stu-id="5f85f-114">Package references also support packages with special requirements about referencing dependent `.dll`s.</span></span> <span data-ttu-id="5f85f-115">Par exemple, le package [FParsec](https://www.nuget.org/packages/FParsec/) utilisé pour exiger que les utilisateurs s’assurent manuellement que son dépendant `FParsecCS.dll` a été référencé avant `FParsec.dll` d’être référencé dans F# Interactive.</span><span class="sxs-lookup"><span data-stu-id="5f85f-115">For example, the [FParsec](https://www.nuget.org/packages/FParsec/) package used to require that users manually ensure that its dependent `FParsecCS.dll` was referenced first before `FParsec.dll` was referenced in F# Interactive.</span></span> <span data-ttu-id="5f85f-116">Ce n’est plus nécessaire et vous pouvez référencer le package comme suit :</span><span class="sxs-lookup"><span data-stu-id="5f85f-116">This is no longer needed, and you can reference the package as follows:</span></span>

```fsharp
#r "nuget: FParsec"

open FParsec

let test p str =
    match run p str with
    | Success(result, _, _)   -> printfn "Success: %A" result
    | Failure(errorMsg, _, _) -> printfn "Failure: %s" errorMsg

test pfloat "1.234"
```

<span data-ttu-id="5f85f-117">Pour plus d’informations sur les références de package, consultez le didacticiel [F# Interactive](../tutorials/fsharp-interactive/index.md) .</span><span class="sxs-lookup"><span data-stu-id="5f85f-117">For more information on package references, see the [F# Interactive](../tutorials/fsharp-interactive/index.md) tutorial.</span></span>

## <a name="string-interpolation"></a><span data-ttu-id="5f85f-118">Interpolation de chaîne</span><span class="sxs-lookup"><span data-stu-id="5f85f-118">String interpolation</span></span>

<span data-ttu-id="5f85f-119">Les chaînes interpolées F # sont assez similaires aux chaînes interpolées C# ou JavaScript, car elles vous permettent d’écrire du code dans des « trous » à l’intérieur d’un littéral de chaîne.</span><span class="sxs-lookup"><span data-stu-id="5f85f-119">F# interpolated strings are fairly similar to C# or JavaScript interpolated strings, in that they let you write code in "holes" inside of a string literal.</span></span> <span data-ttu-id="5f85f-120">Voici un exemple de base :</span><span class="sxs-lookup"><span data-stu-id="5f85f-120">Here's a basic example:</span></span>

```fsharp
let name = "Phillip"
let age = 29
printfn $"Name: {name}, Age: {age}"

printfn $"I think {3.0 + 0.14} is close to {System.Math.PI}!"
```

<span data-ttu-id="5f85f-121">Toutefois, les chaînes interpolées F # autorisent également les interpolations typées, tout comme la `sprintf` fonction, afin d’appliquer qu’une expression à l’intérieur d’un contexte interpolé est conforme à un type particulier.</span><span class="sxs-lookup"><span data-stu-id="5f85f-121">However, F# interpolated strings also allow for typed interpolations, just like the `sprintf` function, to enforce that an expression inside of an interpolated context conforms to a particular type.</span></span> <span data-ttu-id="5f85f-122">Elle utilise les mêmes spécificateurs de format.</span><span class="sxs-lookup"><span data-stu-id="5f85f-122">It uses the same format specifiers.</span></span>

```fsharp
let name = "Phillip"
let age = 29

printfn $"Name: %s{name}, Age: %d{age}"

// Error: type mismatch
printfn $"Name: %s{age}, Age: %d{name}"
```

<span data-ttu-id="5f85f-123">Dans l’exemple d’interpolation typée précédent, `%s` requiert que l’interpolation soit de type `string` , tandis que le `%d` requiert que l’interpolation soit un `integer` .</span><span class="sxs-lookup"><span data-stu-id="5f85f-123">In the preceding typed interpolation example, the `%s` requires the interpolation to be of type `string`, whereas the `%d` requires the interpolation to be an `integer`.</span></span>

<span data-ttu-id="5f85f-124">En outre, toute expression F # arbitraire (ou les expressions) peut être placée dans le côté d’un contexte d’interpolation.</span><span class="sxs-lookup"><span data-stu-id="5f85f-124">Additionally, any arbitrary F# expression (or expressions) can be placed in side of an interpolation context.</span></span> <span data-ttu-id="5f85f-125">Il est même possible d’écrire une expression plus complexe, comme ceci :</span><span class="sxs-lookup"><span data-stu-id="5f85f-125">It is even possible to write a more complicated expression, like so:</span></span>

```fsharp
let str =
    $"""The result of squaring each odd item in {[1..10]} is:
{
    let square x = x * x
    let isOdd x = x % 2 <> 0
    let oddSquares xs =
        xs
        |> List.filter isOdd
        |> List.map square
    oddSquares [1..10]
}
"""
```

<span data-ttu-id="5f85f-126">Toutefois, nous vous déconseillons de le faire trop en pratique.</span><span class="sxs-lookup"><span data-stu-id="5f85f-126">Although we don't recommend doing this too much in practice.</span></span>

## <a name="support-for-nameof"></a><span data-ttu-id="5f85f-127">Prise en charge de nameof</span><span class="sxs-lookup"><span data-stu-id="5f85f-127">Support for nameof</span></span>

<span data-ttu-id="5f85f-128">F # 5 prend en charge l' `nameof` opérateur, qui résout le symbole utilisé pour et produit son nom dans la source F #.</span><span class="sxs-lookup"><span data-stu-id="5f85f-128">F# 5 supports the `nameof` operator, which resolves the symbol it's being used for and produces its name in F# source.</span></span> <span data-ttu-id="5f85f-129">Cela est utile dans différents scénarios, tels que la journalisation, et protège votre journal des modifications dans le code source.</span><span class="sxs-lookup"><span data-stu-id="5f85f-129">This is useful in various scenarios, such as logging, and protects your logging against changes in source code.</span></span>

```fsharp
let months =
    [
        "January"; "February"; "March"; "April";
        "May"; "June"; "July"; "August"; "September";
        "October"; "November"; "December"
    ]

let lookupMonth month =
    if (month > 12 || month < 1) then
        invalidArg (nameof month) (sprintf "Value passed in was %d." month)

    months.[month-1]

printfn "%s" (lookupMonth 12)
printfn "%s" (lookupMonth 1)
printfn "%s" (lookupMonth 13)
```

<span data-ttu-id="5f85f-130">La dernière ligne lèvera une exception et « month » s’affichera dans le message d’erreur.</span><span class="sxs-lookup"><span data-stu-id="5f85f-130">The last line will throw an exception and "month" will be shown in the error message.</span></span>

<span data-ttu-id="5f85f-131">Vous pouvez prendre un nom de presque toutes les constructions F # :</span><span class="sxs-lookup"><span data-stu-id="5f85f-131">You can take a name of nearly every F# construct:</span></span>

```fsharp
module M =
    let f x = nameof x

printfn "%s" (M.f 12)
printfn "%s" (nameof M)
printfn "%s" (nameof M.f)
```

<span data-ttu-id="5f85f-132">Trois ajouts finaux sont des modifications apportées au fonctionnement des opérateurs : l’ajout du `nameof<'type-parameter>` formulaire pour les paramètres de type générique et la possibilité d’utiliser `nameof` comme modèle dans une expression de correspondance de modèle.</span><span class="sxs-lookup"><span data-stu-id="5f85f-132">Three final additions are changes to how operators work: the addition of the `nameof<'type-parameter>` form for generic type parameters, and the ability to use `nameof` as a pattern in a pattern match expression.</span></span>

<span data-ttu-id="5f85f-133">L’utilisation d’un nom d’opérateur donne sa chaîne source.</span><span class="sxs-lookup"><span data-stu-id="5f85f-133">Taking a name of an operator gives its source string.</span></span> <span data-ttu-id="5f85f-134">Si vous avez besoin du formulaire compilé, utilisez le nom compilé d’un opérateur :</span><span class="sxs-lookup"><span data-stu-id="5f85f-134">If you need the compiled form, use the compiled name of an operator:</span></span>

```fsharp
nameof(+) // "+"
nameof op_Addition // "op_Addition"
```

<span data-ttu-id="5f85f-135">L’utilisation du nom d’un paramètre de type requiert une syntaxe légèrement différente :</span><span class="sxs-lookup"><span data-stu-id="5f85f-135">Taking the name of a type parameter requires a slightly different syntax:</span></span>

```fsharp

type C<'TType> =
    member _.TypeName = nameof<'TType>
```

<span data-ttu-id="5f85f-136">Cela est similaire aux `typeof<'T>` opérateurs et `typedefof<'T>` .</span><span class="sxs-lookup"><span data-stu-id="5f85f-136">This is similar to the `typeof<'T>` and `typedefof<'T>` operators.</span></span>

<span data-ttu-id="5f85f-137">F # 5 ajoute également la prise en charge d’un `nameof` modèle qui peut être utilisé dans les `match` expressions :</span><span class="sxs-lookup"><span data-stu-id="5f85f-137">F# 5 also adds support for a `nameof` pattern that can be used in `match` expressions:</span></span>

```fsharp
[<Struct; IsByRefLike>]
type RecordedEvent = { EventType: string; Data: ReadOnlySpan<byte> }

type MyEvent =
    | AData of int
    | BData of string

let deserialize (e: RecordedEvent) : MyEvent =
    match e.EventType with
    | nameof AData -> AData (JsonSerializer.Deserialize<int> e.Data)
    | nameof BData -> BData (JsonSerializer.Deserialize<string> e.Data)
    | t -> failwithf "Invalid EventType: %s" t
```

<span data-ttu-id="5f85f-138">Le code précédent utilise « nameof » au lieu du littéral de chaîne dans l’expression de correspondance.</span><span class="sxs-lookup"><span data-stu-id="5f85f-138">The preceding code uses 'nameof' instead of the string literal in the match expression.</span></span>

## <a name="open-type-declarations"></a><span data-ttu-id="5f85f-139">Ouvrir les déclarations de type</span><span class="sxs-lookup"><span data-stu-id="5f85f-139">Open type declarations</span></span>

<span data-ttu-id="5f85f-140">F # 5 ajoute également la prise en charge des déclarations de type ouvert.</span><span class="sxs-lookup"><span data-stu-id="5f85f-140">F# 5 also adds support for open type declarations.</span></span> <span data-ttu-id="5f85f-141">Une déclaration de type ouverte est semblable à l’ouverture d’une classe statique en C#, sauf avec une syntaxe différente et un comportement légèrement différent pour l’adapter à la sémantique F #.</span><span class="sxs-lookup"><span data-stu-id="5f85f-141">An open type declaration is like opening a static class in C#, except with some different syntax and some slightly different behavior to fit F# semantics.</span></span>

<span data-ttu-id="5f85f-142">Avec les déclarations de type ouvert, vous pouvez `open` n’importe quel type pour exposer le contenu statique à l’intérieur de celui-ci.</span><span class="sxs-lookup"><span data-stu-id="5f85f-142">With open type declarations, you can `open` any type to expose static contents inside of it.</span></span> <span data-ttu-id="5f85f-143">En outre, vous pouvez `open` définir des unions et des enregistrements F # pour exposer leur contenu.</span><span class="sxs-lookup"><span data-stu-id="5f85f-143">Additionally, you can `open` F#-defined unions and records to expose their contents.</span></span> <span data-ttu-id="5f85f-144">Par exemple, cela peut être utile si une Union est définie dans un module et si vous souhaitez accéder à ses cas, mais ne souhaitez pas ouvrir le module entier.</span><span class="sxs-lookup"><span data-stu-id="5f85f-144">For example, this can be useful if you have a union defined in a module and want to access its cases, but don't want to open the entire module.</span></span>

```fsharp
open type System.Math

let x = Min(1.0, 2.0)

module M =
    type DU = A | B | C

    let someOtherFunction x = x + 1

// Open only the type inside the module
open type M.DU

printfn "%A" A
```

<span data-ttu-id="5f85f-145">Contrairement à C#, lorsque vous disposez `open type` de deux types qui exposent un membre portant le même nom, le membre du dernier type en cours de création `open` occulte l’autre nom.</span><span class="sxs-lookup"><span data-stu-id="5f85f-145">Unlike C#, when you `open type` on two types that expose a member with the same name, the member from the last type being `open`ed shadows the other name.</span></span> <span data-ttu-id="5f85f-146">Cela est cohérent avec la sémantique F # autour de l’occultation qui existe déjà.</span><span class="sxs-lookup"><span data-stu-id="5f85f-146">This is consistent with F# semantics around shadowing that exist already.</span></span>

## <a name="consistent-slicing-behavior-for-built-in-data-types"></a><span data-ttu-id="5f85f-147">Comportement de découpage cohérent pour les types de données intégrés</span><span class="sxs-lookup"><span data-stu-id="5f85f-147">Consistent slicing behavior for built-in data types</span></span>

<span data-ttu-id="5f85f-148">Comportement de découpage des types de `FSharp.Core` données intégrés (tableau, liste, chaîne, tableau 2D, tableau 3D, Tableau 4D) qui ne sont pas cohérents avant F # 5.</span><span class="sxs-lookup"><span data-stu-id="5f85f-148">Behavior for slicing the built-in `FSharp.Core` data types (array, list, string, 2D array, 3D array, 4D array) used to not be consistent prior to F# 5.</span></span> <span data-ttu-id="5f85f-149">Un comportement de cas d’arête a levé une exception et d’autres non.</span><span class="sxs-lookup"><span data-stu-id="5f85f-149">Some edge-case behavior threw an exception and some wouldn't.</span></span> <span data-ttu-id="5f85f-150">Dans F # 5, tous les types intégrés retournent désormais des tranches vides pour les tranches impossibles à générer :</span><span class="sxs-lookup"><span data-stu-id="5f85f-150">In F# 5, all built-in types now return empty slices for slices that are impossible to generate:</span></span>

```fsharp
let l = [ 1..10 ]
let a = [| 1..10 |]
let s = "hello!"

// Before: would return empty list
// F# 5: same
let emptyList = l.[-2..(-1)]

// Before: would throw exception
// F# 5: returns empty array
let emptyArray = a.[-2..(-1)]

// Before: would throw exception
// F# 5: returns empty string
let emptyString = s.[-2..(-1)]
```

## <a name="fixed-index-slices-for-3d-and-4d-arrays-in-fsharpcore"></a><span data-ttu-id="5f85f-151">Sections à index fixe pour les tableaux 3D et 4D dans FSharp. Core</span><span class="sxs-lookup"><span data-stu-id="5f85f-151">Fixed-index slices for 3D and 4D arrays in FSharp.Core</span></span>

<span data-ttu-id="5f85f-152">F # 5,0 offre une prise en charge du découpage avec un index fixe dans les types de tableau 3D et 4D intégrés.</span><span class="sxs-lookup"><span data-stu-id="5f85f-152">F# 5.0 brings support for slicing with a fixed index in the built-in 3D and 4D array types.</span></span>

<span data-ttu-id="5f85f-153">Pour illustrer cela, examinez le tableau 3D suivant :</span><span class="sxs-lookup"><span data-stu-id="5f85f-153">To illustrate this, consider the following 3D array:</span></span>

<span data-ttu-id="5f85f-154">*z = 0*</span><span class="sxs-lookup"><span data-stu-id="5f85f-154">*z = 0*</span></span>
|<span data-ttu-id="5f85f-155">x\y</span><span class="sxs-lookup"><span data-stu-id="5f85f-155">x\y</span></span>|<span data-ttu-id="5f85f-156">0</span><span class="sxs-lookup"><span data-stu-id="5f85f-156">0</span></span>|<span data-ttu-id="5f85f-157">1</span><span class="sxs-lookup"><span data-stu-id="5f85f-157">1</span></span>|
|---|-|-|
|<span data-ttu-id="5f85f-158">**0**</span><span class="sxs-lookup"><span data-stu-id="5f85f-158">**0**</span></span>|<span data-ttu-id="5f85f-159">0</span><span class="sxs-lookup"><span data-stu-id="5f85f-159">0</span></span>|<span data-ttu-id="5f85f-160">1</span><span class="sxs-lookup"><span data-stu-id="5f85f-160">1</span></span>|
|<span data-ttu-id="5f85f-161">**1**</span><span class="sxs-lookup"><span data-stu-id="5f85f-161">**1**</span></span>|<span data-ttu-id="5f85f-162">2</span><span class="sxs-lookup"><span data-stu-id="5f85f-162">2</span></span>|<span data-ttu-id="5f85f-163">3</span><span class="sxs-lookup"><span data-stu-id="5f85f-163">3</span></span>|

<span data-ttu-id="5f85f-164">*z = 1*</span><span class="sxs-lookup"><span data-stu-id="5f85f-164">*z = 1*</span></span>
|<span data-ttu-id="5f85f-165">x\y</span><span class="sxs-lookup"><span data-stu-id="5f85f-165">x\y</span></span>|<span data-ttu-id="5f85f-166">0</span><span class="sxs-lookup"><span data-stu-id="5f85f-166">0</span></span>|<span data-ttu-id="5f85f-167">1</span><span class="sxs-lookup"><span data-stu-id="5f85f-167">1</span></span>|
|---|-|-|
|<span data-ttu-id="5f85f-168">**0**</span><span class="sxs-lookup"><span data-stu-id="5f85f-168">**0**</span></span>|<span data-ttu-id="5f85f-169">4</span><span class="sxs-lookup"><span data-stu-id="5f85f-169">4</span></span>|<span data-ttu-id="5f85f-170">5</span><span class="sxs-lookup"><span data-stu-id="5f85f-170">5</span></span>|
|<span data-ttu-id="5f85f-171">**1**</span><span class="sxs-lookup"><span data-stu-id="5f85f-171">**1**</span></span>|<span data-ttu-id="5f85f-172">6</span><span class="sxs-lookup"><span data-stu-id="5f85f-172">6</span></span>|<span data-ttu-id="5f85f-173">7</span><span class="sxs-lookup"><span data-stu-id="5f85f-173">7</span></span>|

<span data-ttu-id="5f85f-174">Que se passe-t-il si vous souhaitez extraire la tranche `[| 4; 5 |]` du tableau ?</span><span class="sxs-lookup"><span data-stu-id="5f85f-174">What if you wanted to extract the slice `[| 4; 5 |]` from the array?</span></span> <span data-ttu-id="5f85f-175">C’est maintenant très simple !</span><span class="sxs-lookup"><span data-stu-id="5f85f-175">This is now very simple!</span></span>

```fsharp
// First, create a 3D array to slice

let dim = 2
let m = Array3D.zeroCreate<int> dim dim dim

let mutable count = 0

for z in 0..dim-1 do
    for y in 0..dim-1 do
        for x in 0..dim-1 do
            m.[x,y,z] <- count
            count <- count + 1

// Now let's get the [4;5] slice!
m.[*, 0, 1]
```

## <a name="applicative-computation-expressions"></a><span data-ttu-id="5f85f-176">Expressions de calcul applicative</span><span class="sxs-lookup"><span data-stu-id="5f85f-176">Applicative Computation Expressions</span></span>

<span data-ttu-id="5f85f-177">Les [expressions de calcul](../language-reference/computation-expressions.md) sont utilisées aujourd’hui pour modéliser les « calculs contextuels », ou dans une terminologie plus fonctionnelle, des calculs monadic.</span><span class="sxs-lookup"><span data-stu-id="5f85f-177">[Computation expressions (CEs)](../language-reference/computation-expressions.md) are used today to model "contextual computations", or in more functional programming friendly terminology, monadic computations.</span></span>

<span data-ttu-id="5f85f-178">F # 5 introduit les EC d’applicative, qui offrent un modèle de calcul différent.</span><span class="sxs-lookup"><span data-stu-id="5f85f-178">F# 5 introduces applicative CEs, which offer a different computational model.</span></span> <span data-ttu-id="5f85f-179">Les EC d’applicative permettent des calculs plus efficaces, à condition que chaque calcul soit indépendant et que ses résultats soient accumulés à la fin.</span><span class="sxs-lookup"><span data-stu-id="5f85f-179">Applicative CEs allow for more efficient computations provided that every computation is independent, and their results are accumulated at the end.</span></span> <span data-ttu-id="5f85f-180">Lorsque les calculs sont indépendants les uns des autres, ils sont également parallèless de manière triviale, ce qui permet aux auteurs CE d’écrire des bibliothèques plus efficaces.</span><span class="sxs-lookup"><span data-stu-id="5f85f-180">When computations are independent of one another, they are also trivially parallelizable, allowing CE authors to write more efficient libraries.</span></span> <span data-ttu-id="5f85f-181">Cet avantage est toutefois une restriction : les calculs qui dépendent de valeurs précédemment calculées ne sont pas autorisés.</span><span class="sxs-lookup"><span data-stu-id="5f85f-181">This benefit comes at a restriction, though: computations that depend on previously-computed values are not allowed.</span></span>

<span data-ttu-id="5f85f-182">L’exemple suivant montre un type applicative de base pour le `Result` type.</span><span class="sxs-lookup"><span data-stu-id="5f85f-182">The follow example shows a basic applicative CE for the `Result` type.</span></span>

```fsharp
// First, define a 'zip' function
module Result =
    let zip x1 x2 =
        match x1,x2 with
        | Ok x1res, Ok x2res -> Ok (x1res, x2res)
        | Error e, _ -> Error e
        | _, Error e -> Error e

// Next, define a builder with 'MergeSources' and 'BindReturn'
type ResultBuilder() =
    member _.MergeSources(t1: Result<'T,'U>, t2: Result<'T1,'U>) = Result.zip t1 t2
    member _.BindReturn(x: Result<'T,'U>, f) = Result.map f x

let result = ResultBuilder()

let run r1 r2 r3 =
    // And here is our applicative!
    let res1: Result<int, string> =
        result {
            let! a = r1
            and! b = r2
            and! c = r3
            return a + b - c
        }

    match res1 with
    | Ok x -> printfn "%s is: %d" (nameof res1) x
    | Error e -> printfn "%s is: %s" (nameof res1) e

let printApplicatives () =
    let r1 = Ok 2
    let r2 = Ok 3 // Error "fail!"
    let r3 = Ok 4

    run r1 r2 r3
    run r1 (Error "failure!") r3
```

<span data-ttu-id="5f85f-183">Si vous êtes un auteur de bibliothèque qui expose les EC dans leur bibliothèque aujourd’hui, vous devez prendre en compte certaines considérations supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="5f85f-183">If you're a library author who exposes CEs in their library today, there are some additional considerations you'll need to be aware of.</span></span>

## <a name="interfaces-can-be-implemeneted-at-different-generic-instantiations"></a><span data-ttu-id="5f85f-184">Les interfaces peuvent être implemeneted à différentes instanciations génériques</span><span class="sxs-lookup"><span data-stu-id="5f85f-184">Interfaces can be implemeneted at different generic instantiations</span></span>

<span data-ttu-id="5f85f-185">Vous pouvez désormais implémenter la même interface à différentes instanciations génériques :</span><span class="sxs-lookup"><span data-stu-id="5f85f-185">You can now implement the same interface at different generic instantiations:</span></span>

```fsharp
type IA<'T> =
    abstract member Get : unit -> 'T

type MyClass() =
    interface IA<int> with
        member x.Get() = 1
    interface IA<string> with
        member x.Get() = "hello"

let mc = MyClass()
let iaInt = mc :> IA<int>
let iaString = mc :> IA<string>

iaInt.Get() // 1
iaString.Get() // "hello"
```

## <a name="default-interface-member-consumption"></a><span data-ttu-id="5f85f-186">Consommation par défaut des membres d’interface</span><span class="sxs-lookup"><span data-stu-id="5f85f-186">Default interface member consumption</span></span>

<span data-ttu-id="5f85f-187">F # 5 vous permet [de consommer des interfaces avec les implémentations par défaut](../../csharp/tutorials/default-interface-methods-versions.md).</span><span class="sxs-lookup"><span data-stu-id="5f85f-187">F# 5 lets you consume [interfaces with default implementations](../../csharp/tutorials/default-interface-methods-versions.md).</span></span>

<span data-ttu-id="5f85f-188">Prenons l’exemple d’une interface définie en C#, comme suit :</span><span class="sxs-lookup"><span data-stu-id="5f85f-188">Consider an interface defined in C# like this:</span></span>

```csharp
using System;

namespace CSharp
{
    public interface MyDimasd
    {
        public int Z => 0;
    }
}
```

<span data-ttu-id="5f85f-189">Vous pouvez l’utiliser en F # par le biais de l’un des moyens standard d’implémenter une interface :</span><span class="sxs-lookup"><span data-stu-id="5f85f-189">You can consume it in F# through any of the standard means of implementing an interface:</span></span>

```fsharp
open CSharp

// You can implement the interface via a class
type MyType() =
    member _.M() = ()

    interface MyDim

let md = MyType() :> MyDim
printfn "DIM from C#: %d" md.Z

// You can also implement it via an object expression
let md' = { new MyDim }
printfn "DIM from C# but via Object Expression: %d" md'.Z
```

<span data-ttu-id="5f85f-190">Cela vous permet de tirer en toute sécurité du code C# et des composants .NET écrits en C# moderne lorsqu’ils s’attendent à ce que les utilisateurs soient en mesure d’utiliser une implémentation par défaut.</span><span class="sxs-lookup"><span data-stu-id="5f85f-190">This lets you safely take advantage of C# code and .NET components written in modern C# when they expect users to be able to consume a default implementation.</span></span>

## <a name="simplified-interop-with-nullable-value-types"></a><span data-ttu-id="5f85f-191">Interopérabilité simplifiée avec les types valeur Nullable</span><span class="sxs-lookup"><span data-stu-id="5f85f-191">Simplified interop with nullable value types</span></span>

<span data-ttu-id="5f85f-192">Les [types Nullable (valeur)](https://docs.microsoft.com/dotnet/api/system.nullable-1) (appelés types Nullable historiquement) ont longtemps été pris en charge par F #, mais l’interaction avec eux a traditionnellement été une douleur puisque vous auriez dû construire un `Nullable` `Nullable<SomeType>` Wrapper ou chaque fois que vous souhaitiez passer une valeur.</span><span class="sxs-lookup"><span data-stu-id="5f85f-192">[Nullable (value) types](https://docs.microsoft.com/dotnet/api/system.nullable-1) (called Nullable Types historically) have long been supported by F#, but interacting with them has traditionally been somewhat of a pain since you'd have to construct a `Nullable` or `Nullable<SomeType>` wrapper every time you wanted to pass a value.</span></span> <span data-ttu-id="5f85f-193">À présent, le compilateur convertit implicitement un type valeur en un `Nullable<ThatValueType>` si le type cible correspond à.</span><span class="sxs-lookup"><span data-stu-id="5f85f-193">Now the compiler will implicitly convert a value type into a `Nullable<ThatValueType>` if the target type matches.</span></span> <span data-ttu-id="5f85f-194">Le code suivant est désormais possible :</span><span class="sxs-lookup"><span data-stu-id="5f85f-194">The following code is now possible:</span></span>

```fsharp
#r "nuget: Microsoft.Data.Analysis"

open Microsoft.Data.Analysis

let dateTimes = PrimitiveDataFrameColumn<DateTime>("DateTimes")

// The following line used to fail to compile
dateTimes.Append(DateTime.Parse("2019/01/01"))

// The previous line is now equivalent to this line
dateTimes.Append(Nullable<DateTime>(DateTime.Parse("2019/01/01")))
```

## <a name="preview-reverse-indexes"></a><span data-ttu-id="5f85f-195">Aperçu : index inversés</span><span class="sxs-lookup"><span data-stu-id="5f85f-195">Preview: reverse indexes</span></span>

<span data-ttu-id="5f85f-196">F # 5 introduit également un aperçu pour autoriser les index inversés.</span><span class="sxs-lookup"><span data-stu-id="5f85f-196">F# 5 also introduces a preview for allowing reverse indexes.</span></span> <span data-ttu-id="5f85f-197">La syntaxe est `^idx`.</span><span class="sxs-lookup"><span data-stu-id="5f85f-197">The syntax is `^idx`.</span></span> <span data-ttu-id="5f85f-198">Voici comment vous pouvez obtenir une valeur d’élément 1 à partir de la fin d’une liste :</span><span class="sxs-lookup"><span data-stu-id="5f85f-198">Here’s how you can an element 1 value from the end of a list:</span></span>

```fsharp
let xs = [1..10]

// Get element 1 from the end:
xs.[^1]

// From the end slices

let lastTwoOldStyle = xs.[(xs.Length-2)..]

let lastTwoNewStyle = xs.[^1..]

lastTwoOldStyle = lastTwoNewStyle // true
```

<span data-ttu-id="5f85f-199">Vous pouvez également définir des index inverses pour vos propres types.</span><span class="sxs-lookup"><span data-stu-id="5f85f-199">You can also define reverse indexes for your own types.</span></span> <span data-ttu-id="5f85f-200">Pour ce faire, vous devez implémenter la méthode suivante :</span><span class="sxs-lookup"><span data-stu-id="5f85f-200">To do so, you’ll need to implement the following method:</span></span>

```fsharp
GetReverseIndex: dimension: int -> offset: int
```

<span data-ttu-id="5f85f-201">Voici un exemple pour le `Span<'T>` type :</span><span class="sxs-lookup"><span data-stu-id="5f85f-201">Here’s an example for the `Span<'T>` type:</span></span>

```fsharp
open System

type Span<'T> with
    member sp.GetSlice(startIdx, endIdx) =
        let s = defaultArg startIdx 0
        let e = defaultArg endIdx sp.Length
        sp.Slice(s, e - s)

    member sp.GetReverseIndex(_, offset: int) =
        sp.Length - offset

let printSpan (sp: Span<int>) =
    let arr = sp.ToArray()
    printfn "%A" arr

let run () =
    let sp = [| 1; 2; 3; 4; 5 |].AsSpan()

    // Pre-# 5.0 slicing on a Span<'T>
    printSpan sp.[0..] // [|1; 2; 3; 4; 5|]
    printSpan sp.[..3] // [|1; 2; 3|]
    printSpan sp.[1..3] // |2; 3|]

    // Same slices, but only using from-the-end index
    printSpan sp.[..^0] // [|1; 2; 3; 4; 5|]
    printSpan sp.[..^2] // [|1; 2; 3|]
    printSpan sp.[^4..^2] // [|2; 3|]

run() // Prints the same thing twice
```

## <a name="preview-overloads-of-custom-keywords-in-computation-expressions"></a><span data-ttu-id="5f85f-202">Aperçu : surcharges de mots clés personnalisés dans les expressions de calcul</span><span class="sxs-lookup"><span data-stu-id="5f85f-202">Preview: overloads of custom keywords in computation expressions</span></span>

<span data-ttu-id="5f85f-203">Les expressions de calcul sont une fonctionnalité puissante pour les auteurs de bibliothèques et de frameworks.</span><span class="sxs-lookup"><span data-stu-id="5f85f-203">Computation expressions are a powerful feature for library and framework authors.</span></span> <span data-ttu-id="5f85f-204">Elles vous permettent d’améliorer de façon considérable l’expressivité de vos composants en vous permettant de définir des membres connus et de former une DSL pour le domaine dans lequel vous travaillez.</span><span class="sxs-lookup"><span data-stu-id="5f85f-204">They allow you to greatly improve the expressiveness of your components by letting you define well-known members and form a DSL for the domain you're working in.</span></span>

<span data-ttu-id="5f85f-205">F # 5 ajoute la prise en charge de l’Aperçu pour la surcharge des opérations personnalisées dans les expressions de calcul.</span><span class="sxs-lookup"><span data-stu-id="5f85f-205">F# 5 adds preview support for overloading custom operations in Computation Expressions.</span></span> <span data-ttu-id="5f85f-206">Il permet d’écrire et d’utiliser le code suivant :</span><span class="sxs-lookup"><span data-stu-id="5f85f-206">It allows the following code to be writen and consumed:</span></span>

```fsharp
open System

type InputKind =
    | Text of placeholder:string option
    | Password of placeholder: string option

type InputOptions =
  { Label: string option
    Kind : InputKind
    Validators : (string -> bool) array }

type InputBuilder() =
    member t.Yield(_) =
      { Label = None
        Kind = Text None
        Validators = [||] }

    [<CustomOperation("text")>]
    member this.Text(io, ?placeholder) =
        { io with Kind = Text placeholder }

    [<CustomOperation("password")>]
    member this.Password(io, ?placeholder) =
        { io with Kind = Password placeholder }

    [<CustomOperation("label")>]
    member this.Label(io, label) =
        { io with Label = Some label }

    [<CustomOperation("with_validators")>]
    member this.Validators(io, [<ParamArray>] validators) =
        { io with Validators = validators }

let input = InputBuilder()

let name =
    input {
    label "Name"
    text
    with_validators
        (String.IsNullOrWhiteSpace >> not)
    }

let email =
    input {
    label "Email"
    text "Your email"
    with_validators
        (String.IsNullOrWhiteSpace >> not)
        (fun s -> s.Contains "@")
    }

let password =
    input {
    label "Password"
    password "Must contains at least 6 characters, one number and one uppercase"
    with_validators
        (String.exists Char.IsUpper)
        (String.exists Char.IsDigit)
        (fun s -> s.Length >= 6)
    }
```

<span data-ttu-id="5f85f-207">Avant cette modification, vous pouviez écrire le `InputBuilder` type tel quel, mais vous ne pouviez pas l’utiliser de la façon dont il est utilisé dans l’exemple.</span><span class="sxs-lookup"><span data-stu-id="5f85f-207">Prior to this change, you could write the `InputBuilder` type as it is, but you couldn't use it the way it's used in the example.</span></span> <span data-ttu-id="5f85f-208">Dans la mesure où les surcharges, les paramètres facultatifs et les `System.ParamArray` types Now sont autorisés, tout fonctionne comme prévu.</span><span class="sxs-lookup"><span data-stu-id="5f85f-208">Since overloads, optional parameters, and now `System.ParamArray` types are allowed, everything just works as you'd expect it to.</span></span>
