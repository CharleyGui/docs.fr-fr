---
title: 'Nouveautés du guide F # 5,0-F #'
description: 'Profitez d’une vue d’ensemble des nouvelles fonctionnalités disponibles dans F # 5,0.'
ms.date: 11/06/2020
ms.openlocfilehash: 2384f1a75f5e708dc6f170d82fa15c5e0f54c85d
ms.sourcegitcommit: ecd9e9bb2225eb76f819722ea8b24988fe46f34c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2020
ms.locfileid: "96740183"
---
# <a name="whats-new-in-f-50"></a><span data-ttu-id="0c7c3-103">Nouveautés de F # 5,0</span><span class="sxs-lookup"><span data-stu-id="0c7c3-103">What's new in F# 5.0</span></span>

<span data-ttu-id="0c7c3-104">F # 5,0 ajoute plusieurs améliorations au langage F # et F# Interactive.</span><span class="sxs-lookup"><span data-stu-id="0c7c3-104">F# 5.0 adds several improvements to the F# language and F# Interactive.</span></span> <span data-ttu-id="0c7c3-105">Il est publié avec **.net 5**.</span><span class="sxs-lookup"><span data-stu-id="0c7c3-105">It is released with **.NET 5**.</span></span>

<span data-ttu-id="0c7c3-106">Vous pouvez télécharger le dernier Kit de développement logiciel (SDK) .NET à partir de la [page de téléchargements .net](https://dotnet.microsoft.com/download).</span><span class="sxs-lookup"><span data-stu-id="0c7c3-106">You can download the latest .NET SDK from the [.NET downloads page](https://dotnet.microsoft.com/download).</span></span>

## <a name="get-started"></a><span data-ttu-id="0c7c3-107">Bien démarrer</span><span class="sxs-lookup"><span data-stu-id="0c7c3-107">Get started</span></span>

<span data-ttu-id="0c7c3-108">F # 5,0 est disponible dans toutes les distributions .NET Core et les outils Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0c7c3-108">F# 5.0 is available in all .NET Core distributions and Visual Studio tooling.</span></span> <span data-ttu-id="0c7c3-109">Pour plus d’informations, consultez la page [prise en main de F #](../get-started/index.md) pour en savoir plus.</span><span class="sxs-lookup"><span data-stu-id="0c7c3-109">For more information, see [Get started with F#](../get-started/index.md) to learn more.</span></span>

## <a name="package-references-in-f-scripts"></a><span data-ttu-id="0c7c3-110">Références de package dans les scripts F #</span><span class="sxs-lookup"><span data-stu-id="0c7c3-110">Package references in F# scripts</span></span>

<span data-ttu-id="0c7c3-111">F # 5 offre une prise en charge des références de package dans les scripts F # avec la `#r "nuget:..."` syntaxe.</span><span class="sxs-lookup"><span data-stu-id="0c7c3-111">F# 5 brings support for package references in F# scripts with `#r "nuget:..."` syntax.</span></span> <span data-ttu-id="0c7c3-112">Par exemple, considérez la référence de package suivante :</span><span class="sxs-lookup"><span data-stu-id="0c7c3-112">For example, consider the following package reference:</span></span>

```fsharp
#r "nuget: Newtonsoft.Json"

open Newtonsoft.Json

let o = {| X = 2; Y = "Hello" |}

printfn $"{JsonConvert.SerializeObject o}"
```

<span data-ttu-id="0c7c3-113">Vous pouvez également fournir une version explicite après le nom du package comme suit :</span><span class="sxs-lookup"><span data-stu-id="0c7c3-113">You can also supply an explicit version after the name of the package like this:</span></span>

```fsharp
#r "nuget: Newtonsoft.Json,11.0.1"
```

<span data-ttu-id="0c7c3-114">Les références de package prennent en charge les packages avec des dépendances natives, telles que ML.NET.</span><span class="sxs-lookup"><span data-stu-id="0c7c3-114">Package references support packages with native dependencies, such as ML.NET.</span></span>

<span data-ttu-id="0c7c3-115">Les références de package prennent également en charge les packages avec des exigences spéciales relatives au référencement des s dépendants `.dll` .</span><span class="sxs-lookup"><span data-stu-id="0c7c3-115">Package references also support packages with special requirements about referencing dependent `.dll`s.</span></span> <span data-ttu-id="0c7c3-116">Par exemple, le package [FParsec](https://www.nuget.org/packages/FParsec/) utilisé pour exiger que les utilisateurs s’assurent manuellement que son dépendant `FParsecCS.dll` a été référencé avant `FParsec.dll` d’être référencé dans F# Interactive.</span><span class="sxs-lookup"><span data-stu-id="0c7c3-116">For example, the [FParsec](https://www.nuget.org/packages/FParsec/) package used to require that users manually ensure that its dependent `FParsecCS.dll` was referenced first before `FParsec.dll` was referenced in F# Interactive.</span></span> <span data-ttu-id="0c7c3-117">Ce n’est plus nécessaire et vous pouvez référencer le package comme suit :</span><span class="sxs-lookup"><span data-stu-id="0c7c3-117">This is no longer needed, and you can reference the package as follows:</span></span>

```fsharp
#r "nuget: FParsec"

open FParsec

let test p str =
    match run p str with
    | Success(result, _, _)   -> printfn $"Success: {result}"
    | Failure(errorMsg, _, _) -> printfn $"Failure: {errorMsg}"

test pfloat "1.234"
```

<span data-ttu-id="0c7c3-118">Cette fonctionnalité implémente [les outils F # RFC FST-1027](https://github.com/fsharp/fslang-design/blob/master/tooling/FST-1027-fsi-references.md).</span><span class="sxs-lookup"><span data-stu-id="0c7c3-118">This feature implements [F# Tooling RFC FST-1027](https://github.com/fsharp/fslang-design/blob/master/tooling/FST-1027-fsi-references.md).</span></span> <span data-ttu-id="0c7c3-119">Pour plus d’informations sur les références de package, consultez le didacticiel [F# Interactive](../tools/fsharp-interactive/index.md) .</span><span class="sxs-lookup"><span data-stu-id="0c7c3-119">For more information on package references, see the [F# Interactive](../tools/fsharp-interactive/index.md) tutorial.</span></span>

## <a name="string-interpolation"></a><span data-ttu-id="0c7c3-120">Interpolation de chaîne</span><span class="sxs-lookup"><span data-stu-id="0c7c3-120">String interpolation</span></span>

<span data-ttu-id="0c7c3-121">Les chaînes interpolées F # sont assez similaires aux chaînes interpolées C# ou JavaScript, car elles vous permettent d’écrire du code dans des « trous » à l’intérieur d’un littéral de chaîne.</span><span class="sxs-lookup"><span data-stu-id="0c7c3-121">F# interpolated strings are fairly similar to C# or JavaScript interpolated strings, in that they let you write code in "holes" inside of a string literal.</span></span> <span data-ttu-id="0c7c3-122">Voici un exemple de base :</span><span class="sxs-lookup"><span data-stu-id="0c7c3-122">Here's a basic example:</span></span>

```fsharp
let name = "Phillip"
let age = 29
printfn $"Name: {name}, Age: {age}"

printfn $"I think {3.0 + 0.14} is close to {System.Math.PI}!"
```

<span data-ttu-id="0c7c3-123">Toutefois, les chaînes interpolées F # autorisent également les interpolations typées, tout comme la `sprintf` fonction, afin d’appliquer qu’une expression à l’intérieur d’un contexte interpolé est conforme à un type particulier.</span><span class="sxs-lookup"><span data-stu-id="0c7c3-123">However, F# interpolated strings also allow for typed interpolations, just like the `sprintf` function, to enforce that an expression inside of an interpolated context conforms to a particular type.</span></span> <span data-ttu-id="0c7c3-124">Elle utilise les mêmes spécificateurs de format.</span><span class="sxs-lookup"><span data-stu-id="0c7c3-124">It uses the same format specifiers.</span></span>

```fsharp
let name = "Phillip"
let age = 29

printfn $"Name: %s{name}, Age: %d{age}"

// Error: type mismatch
printfn $"Name: %s{age}, Age: %d{name}"
```

<span data-ttu-id="0c7c3-125">Dans l’exemple d’interpolation typée précédent, `%s` requiert que l’interpolation soit de type `string` , tandis que le `%d` requiert que l’interpolation soit un `integer` .</span><span class="sxs-lookup"><span data-stu-id="0c7c3-125">In the preceding typed interpolation example, the `%s` requires the interpolation to be of type `string`, whereas the `%d` requires the interpolation to be an `integer`.</span></span>

<span data-ttu-id="0c7c3-126">En outre, toute expression F # arbitraire (ou les expressions) peut être placée dans le côté d’un contexte d’interpolation.</span><span class="sxs-lookup"><span data-stu-id="0c7c3-126">Additionally, any arbitrary F# expression (or expressions) can be placed in side of an interpolation context.</span></span> <span data-ttu-id="0c7c3-127">Il est même possible d’écrire une expression plus complexe, comme ceci :</span><span class="sxs-lookup"><span data-stu-id="0c7c3-127">It is even possible to write a more complicated expression, like so:</span></span>

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

<span data-ttu-id="0c7c3-128">Toutefois, nous vous déconseillons de le faire trop en pratique.</span><span class="sxs-lookup"><span data-stu-id="0c7c3-128">Although we don't recommend doing this too much in practice.</span></span>

<span data-ttu-id="0c7c3-129">Cette fonctionnalité implémente [F # RFC FS-1001](https://github.com/fsharp/fslang-design/blob/master/FSharp-5.0/FS-1001-StringInterpolation.md).</span><span class="sxs-lookup"><span data-stu-id="0c7c3-129">This feature implements [F# RFC FS-1001](https://github.com/fsharp/fslang-design/blob/master/FSharp-5.0/FS-1001-StringInterpolation.md).</span></span>

## <a name="support-for-nameof"></a><span data-ttu-id="0c7c3-130">Prise en charge de nameof</span><span class="sxs-lookup"><span data-stu-id="0c7c3-130">Support for nameof</span></span>

<span data-ttu-id="0c7c3-131">F # 5 prend en charge l' `nameof` opérateur, qui résout le symbole utilisé pour et produit son nom dans la source F #.</span><span class="sxs-lookup"><span data-stu-id="0c7c3-131">F# 5 supports the `nameof` operator, which resolves the symbol it's being used for and produces its name in F# source.</span></span> <span data-ttu-id="0c7c3-132">Cela est utile dans différents scénarios, tels que la journalisation, et protège votre journal des modifications dans le code source.</span><span class="sxs-lookup"><span data-stu-id="0c7c3-132">This is useful in various scenarios, such as logging, and protects your logging against changes in source code.</span></span>

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

printfn $"{lookupMonth 12}"
printfn $"{lookupMonth 1}"
printfn $"{lookupMonth 13}"
```

<span data-ttu-id="0c7c3-133">La dernière ligne lèvera une exception et « month » s’affichera dans le message d’erreur.</span><span class="sxs-lookup"><span data-stu-id="0c7c3-133">The last line will throw an exception and "month" will be shown in the error message.</span></span>

<span data-ttu-id="0c7c3-134">Vous pouvez prendre un nom de presque toutes les constructions F # :</span><span class="sxs-lookup"><span data-stu-id="0c7c3-134">You can take a name of nearly every F# construct:</span></span>

```fsharp
module M =
    let f x = nameof x

printfn $"{M.f 12}"
printfn $"{nameof M}"
printfn $"{nameof M.f}"
```

<span data-ttu-id="0c7c3-135">Trois ajouts finaux sont des modifications apportées au fonctionnement des opérateurs : l’ajout du `nameof<'type-parameter>` formulaire pour les paramètres de type générique et la possibilité d’utiliser `nameof` comme modèle dans une expression de correspondance de modèle.</span><span class="sxs-lookup"><span data-stu-id="0c7c3-135">Three final additions are changes to how operators work: the addition of the `nameof<'type-parameter>` form for generic type parameters, and the ability to use `nameof` as a pattern in a pattern match expression.</span></span>

<span data-ttu-id="0c7c3-136">L’utilisation d’un nom d’opérateur donne sa chaîne source.</span><span class="sxs-lookup"><span data-stu-id="0c7c3-136">Taking a name of an operator gives its source string.</span></span> <span data-ttu-id="0c7c3-137">Si vous avez besoin du formulaire compilé, utilisez le nom compilé d’un opérateur :</span><span class="sxs-lookup"><span data-stu-id="0c7c3-137">If you need the compiled form, use the compiled name of an operator:</span></span>

```fsharp
nameof(+) // "+"
nameof op_Addition // "op_Addition"
```

<span data-ttu-id="0c7c3-138">L’utilisation du nom d’un paramètre de type requiert une syntaxe légèrement différente :</span><span class="sxs-lookup"><span data-stu-id="0c7c3-138">Taking the name of a type parameter requires a slightly different syntax:</span></span>

```fsharp
type C<'TType> =
    member _.TypeName = nameof<'TType>
```

<span data-ttu-id="0c7c3-139">Cela est similaire aux `typeof<'T>` opérateurs et `typedefof<'T>` .</span><span class="sxs-lookup"><span data-stu-id="0c7c3-139">This is similar to the `typeof<'T>` and `typedefof<'T>` operators.</span></span>

<span data-ttu-id="0c7c3-140">F # 5 ajoute également la prise en charge d’un `nameof` modèle qui peut être utilisé dans les `match` expressions :</span><span class="sxs-lookup"><span data-stu-id="0c7c3-140">F# 5 also adds support for a `nameof` pattern that can be used in `match` expressions:</span></span>

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

<span data-ttu-id="0c7c3-141">Le code précédent utilise « nameof » au lieu du littéral de chaîne dans l’expression de correspondance.</span><span class="sxs-lookup"><span data-stu-id="0c7c3-141">The preceding code uses 'nameof' instead of the string literal in the match expression.</span></span>

<span data-ttu-id="0c7c3-142">Cette fonctionnalité implémente [F # RFC FS-1003](https://github.com/fsharp/fslang-design/blob/master/FSharp-5.0/FS-1003-nameof-operator.md).</span><span class="sxs-lookup"><span data-stu-id="0c7c3-142">This feature implements [F# RFC FS-1003](https://github.com/fsharp/fslang-design/blob/master/FSharp-5.0/FS-1003-nameof-operator.md).</span></span>

## <a name="open-type-declarations"></a><span data-ttu-id="0c7c3-143">Ouvrir les déclarations de type</span><span class="sxs-lookup"><span data-stu-id="0c7c3-143">Open type declarations</span></span>

<span data-ttu-id="0c7c3-144">F # 5 ajoute également la prise en charge des déclarations de type ouvert.</span><span class="sxs-lookup"><span data-stu-id="0c7c3-144">F# 5 also adds support for open type declarations.</span></span> <span data-ttu-id="0c7c3-145">Une déclaration de type ouverte est semblable à l’ouverture d’une classe statique en C#, sauf avec une syntaxe différente et un comportement légèrement différent pour l’adapter à la sémantique F #.</span><span class="sxs-lookup"><span data-stu-id="0c7c3-145">An open type declaration is like opening a static class in C#, except with some different syntax and some slightly different behavior to fit F# semantics.</span></span>

<span data-ttu-id="0c7c3-146">Avec les déclarations de type ouvert, vous pouvez `open` n’importe quel type pour exposer le contenu statique à l’intérieur de celui-ci.</span><span class="sxs-lookup"><span data-stu-id="0c7c3-146">With open type declarations, you can `open` any type to expose static contents inside of it.</span></span> <span data-ttu-id="0c7c3-147">En outre, vous pouvez `open` définir des unions et des enregistrements F # pour exposer leur contenu.</span><span class="sxs-lookup"><span data-stu-id="0c7c3-147">Additionally, you can `open` F#-defined unions and records to expose their contents.</span></span> <span data-ttu-id="0c7c3-148">Par exemple, cela peut être utile si une Union est définie dans un module et si vous souhaitez accéder à ses cas, mais ne souhaitez pas ouvrir le module entier.</span><span class="sxs-lookup"><span data-stu-id="0c7c3-148">For example, this can be useful if you have a union defined in a module and want to access its cases, but don't want to open the entire module.</span></span>

```fsharp
open type System.Math

let x = Min(1.0, 2.0)

module M =
    type DU = A | B | C

    let someOtherFunction x = x + 1

// Open only the type inside the module
open type M.DU

printfn $"{A}"
```

<span data-ttu-id="0c7c3-149">Contrairement à C#, lorsque vous disposez `open type` de deux types qui exposent un membre portant le même nom, le membre du dernier type en cours de création `open` occulte l’autre nom.</span><span class="sxs-lookup"><span data-stu-id="0c7c3-149">Unlike C#, when you `open type` on two types that expose a member with the same name, the member from the last type being `open`ed shadows the other name.</span></span> <span data-ttu-id="0c7c3-150">Cela est cohérent avec la sémantique F # autour de l’occultation qui existe déjà.</span><span class="sxs-lookup"><span data-stu-id="0c7c3-150">This is consistent with F# semantics around shadowing that exist already.</span></span>

<span data-ttu-id="0c7c3-151">Cette fonctionnalité implémente [F # RFC FS-1068](https://github.com/fsharp/fslang-design/blob/master/FSharp-5.0/FS-1068-open-type-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="0c7c3-151">This feature implements [F# RFC FS-1068](https://github.com/fsharp/fslang-design/blob/master/FSharp-5.0/FS-1068-open-type-declaration.md).</span></span>

## <a name="consistent-slicing-behavior-for-built-in-data-types"></a><span data-ttu-id="0c7c3-152">Comportement de découpage cohérent pour les types de données intégrés</span><span class="sxs-lookup"><span data-stu-id="0c7c3-152">Consistent slicing behavior for built-in data types</span></span>

<span data-ttu-id="0c7c3-153">Comportement de découpage des types de `FSharp.Core` données intégrés (tableau, liste, chaîne, tableau 2D, tableau 3D, Tableau 4D) qui ne sont pas cohérents avant F # 5.</span><span class="sxs-lookup"><span data-stu-id="0c7c3-153">Behavior for slicing the built-in `FSharp.Core` data types (array, list, string, 2D array, 3D array, 4D array) used to not be consistent prior to F# 5.</span></span> <span data-ttu-id="0c7c3-154">Un comportement de cas d’arête a levé une exception et d’autres non.</span><span class="sxs-lookup"><span data-stu-id="0c7c3-154">Some edge-case behavior threw an exception and some wouldn't.</span></span> <span data-ttu-id="0c7c3-155">Dans F # 5, tous les types intégrés retournent désormais des tranches vides pour les tranches impossibles à générer :</span><span class="sxs-lookup"><span data-stu-id="0c7c3-155">In F# 5, all built-in types now return empty slices for slices that are impossible to generate:</span></span>

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

<span data-ttu-id="0c7c3-156">Cette fonctionnalité implémente [F # RFC FS-1077](https://github.com/fsharp/fslang-design/blob/master/FSharp-5.0/FS-1077-tolerant-slicing.md).</span><span class="sxs-lookup"><span data-stu-id="0c7c3-156">This feature implements [F# RFC FS-1077](https://github.com/fsharp/fslang-design/blob/master/FSharp-5.0/FS-1077-tolerant-slicing.md).</span></span>

## <a name="fixed-index-slices-for-3d-and-4d-arrays-in-fsharpcore"></a><span data-ttu-id="0c7c3-157">Sections à index fixe pour les tableaux 3D et 4D dans FSharp. Core</span><span class="sxs-lookup"><span data-stu-id="0c7c3-157">Fixed-index slices for 3D and 4D arrays in FSharp.Core</span></span>

<span data-ttu-id="0c7c3-158">F # 5,0 offre une prise en charge du découpage avec un index fixe dans les types de tableau 3D et 4D intégrés.</span><span class="sxs-lookup"><span data-stu-id="0c7c3-158">F# 5.0 brings support for slicing with a fixed index in the built-in 3D and 4D array types.</span></span>

<span data-ttu-id="0c7c3-159">Pour illustrer cela, examinez le tableau 3D suivant :</span><span class="sxs-lookup"><span data-stu-id="0c7c3-159">To illustrate this, consider the following 3D array:</span></span>

<span data-ttu-id="0c7c3-160">*z = 0*</span><span class="sxs-lookup"><span data-stu-id="0c7c3-160">*z = 0*</span></span>
| <span data-ttu-id="0c7c3-161">x\y</span><span class="sxs-lookup"><span data-stu-id="0c7c3-161">x\y</span></span>   | <span data-ttu-id="0c7c3-162">0</span><span class="sxs-lookup"><span data-stu-id="0c7c3-162">0</span></span> | <span data-ttu-id="0c7c3-163">1</span><span class="sxs-lookup"><span data-stu-id="0c7c3-163">1</span></span> |
|-------|---|---|
| <span data-ttu-id="0c7c3-164">**0**</span><span class="sxs-lookup"><span data-stu-id="0c7c3-164">**0**</span></span> | <span data-ttu-id="0c7c3-165">0</span><span class="sxs-lookup"><span data-stu-id="0c7c3-165">0</span></span> | <span data-ttu-id="0c7c3-166">1</span><span class="sxs-lookup"><span data-stu-id="0c7c3-166">1</span></span> |
| <span data-ttu-id="0c7c3-167">**1**</span><span class="sxs-lookup"><span data-stu-id="0c7c3-167">**1**</span></span> | <span data-ttu-id="0c7c3-168">2</span><span class="sxs-lookup"><span data-stu-id="0c7c3-168">2</span></span> | <span data-ttu-id="0c7c3-169">3</span><span class="sxs-lookup"><span data-stu-id="0c7c3-169">3</span></span> |

<span data-ttu-id="0c7c3-170">*z = 1*</span><span class="sxs-lookup"><span data-stu-id="0c7c3-170">*z = 1*</span></span>
| <span data-ttu-id="0c7c3-171">x\y</span><span class="sxs-lookup"><span data-stu-id="0c7c3-171">x\y</span></span>   | <span data-ttu-id="0c7c3-172">0</span><span class="sxs-lookup"><span data-stu-id="0c7c3-172">0</span></span> | <span data-ttu-id="0c7c3-173">1</span><span class="sxs-lookup"><span data-stu-id="0c7c3-173">1</span></span> |
|-------|---|---|
| <span data-ttu-id="0c7c3-174">**0**</span><span class="sxs-lookup"><span data-stu-id="0c7c3-174">**0**</span></span> | <span data-ttu-id="0c7c3-175">4</span><span class="sxs-lookup"><span data-stu-id="0c7c3-175">4</span></span> | <span data-ttu-id="0c7c3-176">5</span><span class="sxs-lookup"><span data-stu-id="0c7c3-176">5</span></span> |
| <span data-ttu-id="0c7c3-177">**1**</span><span class="sxs-lookup"><span data-stu-id="0c7c3-177">**1**</span></span> | <span data-ttu-id="0c7c3-178">6</span><span class="sxs-lookup"><span data-stu-id="0c7c3-178">6</span></span> | <span data-ttu-id="0c7c3-179">7</span><span class="sxs-lookup"><span data-stu-id="0c7c3-179">7</span></span> |

<span data-ttu-id="0c7c3-180">Que se passe-t-il si vous souhaitez extraire la tranche `[| 4; 5 |]` du tableau ?</span><span class="sxs-lookup"><span data-stu-id="0c7c3-180">What if you wanted to extract the slice `[| 4; 5 |]` from the array?</span></span> <span data-ttu-id="0c7c3-181">C’est maintenant très simple !</span><span class="sxs-lookup"><span data-stu-id="0c7c3-181">This is now very simple!</span></span>

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

<span data-ttu-id="0c7c3-182">Cette fonctionnalité implémente [F # RFC FS-1077b](https://github.com/fsharp/fslang-design/blob/master/FSharp-5.0/FS-1077-3d-4d-fixed-index-slicing.md).</span><span class="sxs-lookup"><span data-stu-id="0c7c3-182">This feature implements [F# RFC FS-1077b](https://github.com/fsharp/fslang-design/blob/master/FSharp-5.0/FS-1077-3d-4d-fixed-index-slicing.md).</span></span>

## <a name="f-quotations-improvements"></a><span data-ttu-id="0c7c3-183">Améliorations des guillemets F #</span><span class="sxs-lookup"><span data-stu-id="0c7c3-183">F# quotations improvements</span></span>

<span data-ttu-id="0c7c3-184">Les [citations de code](../language-reference/code-quotations.md) F # peuvent désormais conserver les informations de contrainte de type.</span><span class="sxs-lookup"><span data-stu-id="0c7c3-184">F# [code quotations](../language-reference/code-quotations.md) now have the ability to retain type constraint information.</span></span> <span data-ttu-id="0c7c3-185">Prenons l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="0c7c3-185">Consider the following example:</span></span>

```fsharp
open FSharp.Linq.RuntimeHelpers

let eval q = LeafExpressionConverter.EvaluateQuotation q

let inline negate x = -x
// val inline negate: x: ^a ->  ^a when  ^a : (static member ( ~- ) :  ^a ->  ^a)

<@ negate 1.0 @>  |> eval
```

<span data-ttu-id="0c7c3-186">La contrainte générée par la `inline` fonction est conservée dans le devis de code.</span><span class="sxs-lookup"><span data-stu-id="0c7c3-186">The constraint generated by the `inline` function is retained in the code quotation.</span></span> <span data-ttu-id="0c7c3-187">Le `negate` formulaire quotated de la fonction peut maintenant être évalué.</span><span class="sxs-lookup"><span data-stu-id="0c7c3-187">The `negate` function's quotated form can now be evaluated.</span></span>

<span data-ttu-id="0c7c3-188">Cette fonctionnalité implémente [F # RFC FS-1071](https://github.com/fsharp/fslang-design/blob/master/FSharp-5.0/FS-1071-witness-passing-quotations.md).</span><span class="sxs-lookup"><span data-stu-id="0c7c3-188">This feature implements [F# RFC FS-1071](https://github.com/fsharp/fslang-design/blob/master/FSharp-5.0/FS-1071-witness-passing-quotations.md).</span></span>

## <a name="applicative-computation-expressions"></a><span data-ttu-id="0c7c3-189">Expressions de calcul applicative</span><span class="sxs-lookup"><span data-stu-id="0c7c3-189">Applicative Computation Expressions</span></span>

<span data-ttu-id="0c7c3-190">Les [expressions de calcul](../language-reference/computation-expressions.md) sont utilisées aujourd’hui pour modéliser les « calculs contextuels », ou dans une terminologie plus fonctionnelle, des calculs monadic.</span><span class="sxs-lookup"><span data-stu-id="0c7c3-190">[Computation expressions (CEs)](../language-reference/computation-expressions.md) are used today to model "contextual computations", or in more functional programming-friendly terminology, monadic computations.</span></span>

<span data-ttu-id="0c7c3-191">F # 5 introduit les EC d’applicative, qui offrent un modèle de calcul différent.</span><span class="sxs-lookup"><span data-stu-id="0c7c3-191">F# 5 introduces applicative CEs, which offer a different computational model.</span></span> <span data-ttu-id="0c7c3-192">Les EC d’applicative permettent des calculs plus efficaces, à condition que chaque calcul soit indépendant et que ses résultats soient accumulés à la fin.</span><span class="sxs-lookup"><span data-stu-id="0c7c3-192">Applicative CEs allow for more efficient computations provided that every computation is independent, and their results are accumulated at the end.</span></span> <span data-ttu-id="0c7c3-193">Lorsque les calculs sont indépendants les uns des autres, ils sont également parallèless de manière triviale, ce qui permet aux auteurs CE d’écrire des bibliothèques plus efficaces.</span><span class="sxs-lookup"><span data-stu-id="0c7c3-193">When computations are independent of one another, they are also trivially parallelizable, allowing CE authors to write more efficient libraries.</span></span> <span data-ttu-id="0c7c3-194">Cet avantage est toutefois une restriction : les calculs qui dépendent de valeurs calculées précédemment ne sont pas autorisés.</span><span class="sxs-lookup"><span data-stu-id="0c7c3-194">This benefit comes at a restriction, though: computations that depend on previously computed values are not allowed.</span></span>

<span data-ttu-id="0c7c3-195">L’exemple suivant montre un type applicative de base pour le `Result` type.</span><span class="sxs-lookup"><span data-stu-id="0c7c3-195">The follow example shows a basic applicative CE for the `Result` type.</span></span>

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
    | Ok x -> printfn $"{nameof res1} is: %d{x}"
    | Error e -> printfn $"{nameof res1} is: {e}"

let printApplicatives () =
    let r1 = Ok 2
    let r2 = Ok 3 // Error "fail!"
    let r3 = Ok 4

    run r1 r2 r3
    run r1 (Error "failure!") r3
```

<span data-ttu-id="0c7c3-196">Si vous êtes un auteur de bibliothèque qui expose les EC dans leur bibliothèque aujourd’hui, vous devez prendre en compte certaines considérations supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="0c7c3-196">If you're a library author who exposes CEs in their library today, there are some additional considerations you'll need to be aware of.</span></span>

<span data-ttu-id="0c7c3-197">Cette fonctionnalité implémente [F # RFC FS-1063](https://github.com/fsharp/fslang-design/blob/master/FSharp-5.0/FS-1063-support-letbang-andbang-for-applicative-functors.md).</span><span class="sxs-lookup"><span data-stu-id="0c7c3-197">This feature implements [F# RFC FS-1063](https://github.com/fsharp/fslang-design/blob/master/FSharp-5.0/FS-1063-support-letbang-andbang-for-applicative-functors.md).</span></span>

## <a name="interfaces-can-be-implemented-at-different-generic-instantiations"></a><span data-ttu-id="0c7c3-198">Les interfaces peuvent être implémentées à différentes instanciations génériques</span><span class="sxs-lookup"><span data-stu-id="0c7c3-198">Interfaces can be implemented at different generic instantiations</span></span>

<span data-ttu-id="0c7c3-199">Vous pouvez désormais implémenter la même interface à différentes instanciations génériques :</span><span class="sxs-lookup"><span data-stu-id="0c7c3-199">You can now implement the same interface at different generic instantiations:</span></span>

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

<span data-ttu-id="0c7c3-200">Cette fonctionnalité implémente [F # RFC FS-1031](https://github.com/fsharp/fslang-design/blob/master/FSharp-5.0/FS-1031-Allow%20implementing%20the%20same%20interface%20at%20different%20generic%20instantiations%20in%20the%20same%20type.md).</span><span class="sxs-lookup"><span data-stu-id="0c7c3-200">This feature implements [F# RFC FS-1031](https://github.com/fsharp/fslang-design/blob/master/FSharp-5.0/FS-1031-Allow%20implementing%20the%20same%20interface%20at%20different%20generic%20instantiations%20in%20the%20same%20type.md).</span></span>

## <a name="default-interface-member-consumption"></a><span data-ttu-id="0c7c3-201">Consommation par défaut des membres d’interface</span><span class="sxs-lookup"><span data-stu-id="0c7c3-201">Default interface member consumption</span></span>

<span data-ttu-id="0c7c3-202">F # 5 vous permet [de consommer des interfaces avec les implémentations par défaut](../../csharp/tutorials/default-interface-methods-versions.md).</span><span class="sxs-lookup"><span data-stu-id="0c7c3-202">F# 5 lets you consume [interfaces with default implementations](../../csharp/tutorials/default-interface-methods-versions.md).</span></span>

<span data-ttu-id="0c7c3-203">Prenons l’exemple d’une interface définie en C#, comme suit :</span><span class="sxs-lookup"><span data-stu-id="0c7c3-203">Consider an interface defined in C# like this:</span></span>

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

<span data-ttu-id="0c7c3-204">Vous pouvez l’utiliser en F # par le biais de l’un des moyens standard d’implémenter une interface :</span><span class="sxs-lookup"><span data-stu-id="0c7c3-204">You can consume it in F# through any of the standard means of implementing an interface:</span></span>

```fsharp
open CSharp

// You can implement the interface via a class
type MyType() =
    member _.M() = ()

    interface MyDim

let md = MyType() :> MyDim
printfn $"DIM from C#: %d{md.Z}"

// You can also implement it via an object expression
let md' = { new MyDim }
printfn $"DIM from C# but via Object Expression: %d{md'.Z}"
```

<span data-ttu-id="0c7c3-205">Cela vous permet de tirer en toute sécurité du code C# et des composants .NET écrits en C# moderne lorsqu’ils s’attendent à ce que les utilisateurs soient en mesure d’utiliser une implémentation par défaut.</span><span class="sxs-lookup"><span data-stu-id="0c7c3-205">This lets you safely take advantage of C# code and .NET components written in modern C# when they expect users to be able to consume a default implementation.</span></span>

<span data-ttu-id="0c7c3-206">Cette fonctionnalité implémente [F # RFC FS-1074](https://github.com/fsharp/fslang-design/blob/master/FSharp-5.0/FS-1074-default-interface-member-consumption.md).</span><span class="sxs-lookup"><span data-stu-id="0c7c3-206">This feature implements [F# RFC FS-1074](https://github.com/fsharp/fslang-design/blob/master/FSharp-5.0/FS-1074-default-interface-member-consumption.md).</span></span>

## <a name="simplified-interop-with-nullable-value-types"></a><span data-ttu-id="0c7c3-207">Interopérabilité simplifiée avec les types valeur Nullable</span><span class="sxs-lookup"><span data-stu-id="0c7c3-207">Simplified interop with nullable value types</span></span>

<span data-ttu-id="0c7c3-208">Les [types Nullable (valeur)](https://docs.microsoft.com/dotnet/api/system.nullable-1) (appelés types Nullable historiquement) ont longtemps été pris en charge par F #, mais l’interaction avec eux a traditionnellement été une douleur puisque vous auriez dû construire un `Nullable` `Nullable<SomeType>` Wrapper ou chaque fois que vous souhaitiez passer une valeur.</span><span class="sxs-lookup"><span data-stu-id="0c7c3-208">[Nullable (value) types](https://docs.microsoft.com/dotnet/api/system.nullable-1) (called Nullable Types historically) have long been supported by F#, but interacting with them has traditionally been somewhat of a pain since you'd have to construct a `Nullable` or `Nullable<SomeType>` wrapper every time you wanted to pass a value.</span></span> <span data-ttu-id="0c7c3-209">À présent, le compilateur convertit implicitement un type valeur en un `Nullable<ThatValueType>` si le type cible correspond à.</span><span class="sxs-lookup"><span data-stu-id="0c7c3-209">Now the compiler will implicitly convert a value type into a `Nullable<ThatValueType>` if the target type matches.</span></span> <span data-ttu-id="0c7c3-210">Le code suivant est désormais possible :</span><span class="sxs-lookup"><span data-stu-id="0c7c3-210">The following code is now possible:</span></span>

```fsharp
#r "nuget: Microsoft.Data.Analysis"

open Microsoft.Data.Analysis

let dateTimes = PrimitiveDataFrameColumn<DateTime>("DateTimes")

// The following line used to fail to compile
dateTimes.Append(DateTime.Parse("2019/01/01"))

// The previous line is now equivalent to this line
dateTimes.Append(Nullable<DateTime>(DateTime.Parse("2019/01/01")))
```

<span data-ttu-id="0c7c3-211">Cette fonctionnalité implémente [F # RFC FS-1075](https://github.com/fsharp/fslang-design/blob/master/FSharp-5.0/FS-1075-nullable-interop.md).</span><span class="sxs-lookup"><span data-stu-id="0c7c3-211">This feature implements [F# RFC FS-1075](https://github.com/fsharp/fslang-design/blob/master/FSharp-5.0/FS-1075-nullable-interop.md).</span></span>

## <a name="preview-reverse-indexes"></a><span data-ttu-id="0c7c3-212">Aperçu : index inversés</span><span class="sxs-lookup"><span data-stu-id="0c7c3-212">Preview: reverse indexes</span></span>

<span data-ttu-id="0c7c3-213">F # 5 introduit également un aperçu pour autoriser les index inversés.</span><span class="sxs-lookup"><span data-stu-id="0c7c3-213">F# 5 also introduces a preview for allowing reverse indexes.</span></span> <span data-ttu-id="0c7c3-214">La syntaxe est `^idx`.</span><span class="sxs-lookup"><span data-stu-id="0c7c3-214">The syntax is `^idx`.</span></span> <span data-ttu-id="0c7c3-215">Voici comment vous pouvez obtenir une valeur d’élément 1 à partir de la fin d’une liste :</span><span class="sxs-lookup"><span data-stu-id="0c7c3-215">Here's how you can an element 1 value from the end of a list:</span></span>

```fsharp
let xs = [1..10]

// Get element 1 from the end:
xs.[^1]

// From the end slices

let lastTwoOldStyle = xs.[(xs.Length-2)..]

let lastTwoNewStyle = xs.[^1..]

lastTwoOldStyle = lastTwoNewStyle // true
```

<span data-ttu-id="0c7c3-216">Vous pouvez également définir des index inverses pour vos propres types.</span><span class="sxs-lookup"><span data-stu-id="0c7c3-216">You can also define reverse indexes for your own types.</span></span> <span data-ttu-id="0c7c3-217">Pour ce faire, vous devez implémenter la méthode suivante :</span><span class="sxs-lookup"><span data-stu-id="0c7c3-217">To do so, you'll need to implement the following method:</span></span>

```fsharp
GetReverseIndex: dimension: int -> offset: int
```

<span data-ttu-id="0c7c3-218">Voici un exemple pour le `Span<'T>` type :</span><span class="sxs-lookup"><span data-stu-id="0c7c3-218">Here's an example for the `Span<'T>` type:</span></span>

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
    printfn $"{arr}"

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

<span data-ttu-id="0c7c3-219">Cette fonctionnalité implémente [F # RFC FS-1076](https://github.com/fsharp/fslang-design/blob/master/preview/FS-1076-from-the-end-slicing.md).</span><span class="sxs-lookup"><span data-stu-id="0c7c3-219">This feature implements [F# RFC FS-1076](https://github.com/fsharp/fslang-design/blob/master/preview/FS-1076-from-the-end-slicing.md).</span></span>

## <a name="preview-overloads-of-custom-keywords-in-computation-expressions"></a><span data-ttu-id="0c7c3-220">Aperçu : surcharges de mots clés personnalisés dans les expressions de calcul</span><span class="sxs-lookup"><span data-stu-id="0c7c3-220">Preview: overloads of custom keywords in computation expressions</span></span>

<span data-ttu-id="0c7c3-221">Les expressions de calcul sont une fonctionnalité puissante pour les auteurs de bibliothèques et de frameworks.</span><span class="sxs-lookup"><span data-stu-id="0c7c3-221">Computation expressions are a powerful feature for library and framework authors.</span></span> <span data-ttu-id="0c7c3-222">Elles vous permettent d’améliorer de façon considérable l’expressivité de vos composants en vous permettant de définir des membres connus et de former une DSL pour le domaine dans lequel vous travaillez.</span><span class="sxs-lookup"><span data-stu-id="0c7c3-222">They allow you to greatly improve the expressiveness of your components by letting you define well-known members and form a DSL for the domain you're working in.</span></span>

<span data-ttu-id="0c7c3-223">F # 5 ajoute la prise en charge de l’Aperçu pour la surcharge des opérations personnalisées dans les expressions de calcul.</span><span class="sxs-lookup"><span data-stu-id="0c7c3-223">F# 5 adds preview support for overloading custom operations in Computation Expressions.</span></span> <span data-ttu-id="0c7c3-224">Il permet l’écriture et la consommation du code suivant :</span><span class="sxs-lookup"><span data-stu-id="0c7c3-224">It allows the following code to be written and consumed:</span></span>

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

<span data-ttu-id="0c7c3-225">Avant cette modification, vous pouviez écrire le `InputBuilder` type tel quel, mais vous ne pouviez pas l’utiliser de la façon dont il est utilisé dans l’exemple.</span><span class="sxs-lookup"><span data-stu-id="0c7c3-225">Prior to this change, you could write the `InputBuilder` type as it is, but you couldn't use it the way it's used in the example.</span></span> <span data-ttu-id="0c7c3-226">Dans la mesure où les surcharges, les paramètres facultatifs et les `System.ParamArray` types Now sont autorisés, tout fonctionne comme prévu.</span><span class="sxs-lookup"><span data-stu-id="0c7c3-226">Since overloads, optional parameters, and now `System.ParamArray` types are allowed, everything just works as you'd expect it to.</span></span>

<span data-ttu-id="0c7c3-227">Cette fonctionnalité implémente [F # RFC FS-1056](https://github.com/fsharp/fslang-design/blob/master/preview/FS-1056-allow-custom-operation-overloads.md).</span><span class="sxs-lookup"><span data-stu-id="0c7c3-227">This feature implements [F# RFC FS-1056](https://github.com/fsharp/fslang-design/blob/master/preview/FS-1056-allow-custom-operation-overloads.md).</span></span>
