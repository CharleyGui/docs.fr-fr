---
title: 'Nouveautés du guide F # 5,0-F #'
description: 'Profitez d’une vue d’ensemble des nouvelles fonctionnalités disponibles dans F # 5,0.'
ms.date: 11/06/2020
ms.openlocfilehash: 29b5b110379dec476d7c0aa51540984acb25f26e
ms.sourcegitcommit: 30e9e11dfd90112b8eec6406186ba3533f21eba1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2020
ms.locfileid: "95098695"
---
# <a name="whats-new-in-f-50"></a>Nouveautés de F # 5,0

F # 5,0 ajoute plusieurs améliorations au langage F # et F# Interactive. Il est publié avec **.net 5**.

Vous pouvez télécharger le dernier Kit de développement logiciel (SDK) .NET à partir de la [page de téléchargements .net](https://dotnet.microsoft.com/download).

## <a name="get-started"></a>Bien démarrer

F # 5,0 est disponible dans toutes les distributions .NET Core et les outils Visual Studio. Pour plus d’informations, consultez la page [prise en main de F #](../get-started/index.md) pour en savoir plus.

## <a name="package-references-in-f-scripts"></a>Références de package dans les scripts F #

F # 5 offre une prise en charge des références de package dans les scripts F # avec la `#r "nuget:..."` syntaxe. Par exemple, considérez la référence de package suivante :

```fsharp
#r "nuget: Newtonsoft.Json"

open Newtonsoft.Json

let o = {| X = 2; Y = "Hello" |}

printfn "%s" (JsonConvert.SerializeObject o)
```

Vous pouvez également fournir une version explicite après le nom du package comme suit :

```fsharp
#r "nuget: Newtonsoft.Json,11.0.1"
```

Les références de package prennent en charge les packages avec des dépendances natives, telles que ML.NET.

Les références de package prennent également en charge les packages avec des exigences spéciales relatives au référencement des s dépendants `.dll` . Par exemple, le package [FParsec](https://www.nuget.org/packages/FParsec/) utilisé pour exiger que les utilisateurs s’assurent manuellement que son dépendant `FParsecCS.dll` a été référencé avant `FParsec.dll` d’être référencé dans F# Interactive. Ce n’est plus nécessaire et vous pouvez référencer le package comme suit :

```fsharp
#r "nuget: FParsec"

open FParsec

let test p str =
    match run p str with
    | Success(result, _, _)   -> printfn "Success: %A" result
    | Failure(errorMsg, _, _) -> printfn "Failure: %s" errorMsg

test pfloat "1.234"
```

Cette fonctionnalité implémente [les outils F # RFC FST-1027](https://github.com/fsharp/fslang-design/blob/master/tooling/FST-1027-fsi-references.md). Pour plus d’informations sur les références de package, consultez le didacticiel [F# Interactive](../tutorials/fsharp-interactive/index.md) .

## <a name="string-interpolation"></a>Interpolation de chaîne

Les chaînes interpolées F # sont assez similaires aux chaînes interpolées C# ou JavaScript, car elles vous permettent d’écrire du code dans des « trous » à l’intérieur d’un littéral de chaîne. Voici un exemple de base :

```fsharp
let name = "Phillip"
let age = 29
printfn $"Name: {name}, Age: {age}"

printfn $"I think {3.0 + 0.14} is close to {System.Math.PI}!"
```

Toutefois, les chaînes interpolées F # autorisent également les interpolations typées, tout comme la `sprintf` fonction, afin d’appliquer qu’une expression à l’intérieur d’un contexte interpolé est conforme à un type particulier. Elle utilise les mêmes spécificateurs de format.

```fsharp
let name = "Phillip"
let age = 29

printfn $"Name: %s{name}, Age: %d{age}"

// Error: type mismatch
printfn $"Name: %s{age}, Age: %d{name}"
```

Dans l’exemple d’interpolation typée précédent, `%s` requiert que l’interpolation soit de type `string` , tandis que le `%d` requiert que l’interpolation soit un `integer` .

En outre, toute expression F # arbitraire (ou les expressions) peut être placée dans le côté d’un contexte d’interpolation. Il est même possible d’écrire une expression plus complexe, comme ceci :

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

Toutefois, nous vous déconseillons de le faire trop en pratique.

Cette fonctionnalité implémente [F # RFC FS-1001](https://github.com/fsharp/fslang-design/blob/master/FSharp-5.0/FS-1001-StringInterpolation.md).

## <a name="support-for-nameof"></a>Prise en charge de nameof

F # 5 prend en charge l' `nameof` opérateur, qui résout le symbole utilisé pour et produit son nom dans la source F #. Cela est utile dans différents scénarios, tels que la journalisation, et protège votre journal des modifications dans le code source.

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

La dernière ligne lèvera une exception et « month » s’affichera dans le message d’erreur.

Vous pouvez prendre un nom de presque toutes les constructions F # :

```fsharp
module M =
    let f x = nameof x

printfn "%s" (M.f 12)
printfn "%s" (nameof M)
printfn "%s" (nameof M.f)
```

Trois ajouts finaux sont des modifications apportées au fonctionnement des opérateurs : l’ajout du `nameof<'type-parameter>` formulaire pour les paramètres de type générique et la possibilité d’utiliser `nameof` comme modèle dans une expression de correspondance de modèle.

L’utilisation d’un nom d’opérateur donne sa chaîne source. Si vous avez besoin du formulaire compilé, utilisez le nom compilé d’un opérateur :

```fsharp
nameof(+) // "+"
nameof op_Addition // "op_Addition"
```

L’utilisation du nom d’un paramètre de type requiert une syntaxe légèrement différente :

```fsharp
type C<'TType> =
    member _.TypeName = nameof<'TType>
```

Cela est similaire aux `typeof<'T>` opérateurs et `typedefof<'T>` .

F # 5 ajoute également la prise en charge d’un `nameof` modèle qui peut être utilisé dans les `match` expressions :

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

Le code précédent utilise « nameof » au lieu du littéral de chaîne dans l’expression de correspondance.

Cette fonctionnalité implémente [F # RFC FS-1003](https://github.com/fsharp/fslang-design/blob/master/FSharp-5.0/FS-1003-nameof-operator.md).

## <a name="open-type-declarations"></a>Ouvrir les déclarations de type

F # 5 ajoute également la prise en charge des déclarations de type ouvert. Une déclaration de type ouverte est semblable à l’ouverture d’une classe statique en C#, sauf avec une syntaxe différente et un comportement légèrement différent pour l’adapter à la sémantique F #.

Avec les déclarations de type ouvert, vous pouvez `open` n’importe quel type pour exposer le contenu statique à l’intérieur de celui-ci. En outre, vous pouvez `open` définir des unions et des enregistrements F # pour exposer leur contenu. Par exemple, cela peut être utile si une Union est définie dans un module et si vous souhaitez accéder à ses cas, mais ne souhaitez pas ouvrir le module entier.

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

Contrairement à C#, lorsque vous disposez `open type` de deux types qui exposent un membre portant le même nom, le membre du dernier type en cours de création `open` occulte l’autre nom. Cela est cohérent avec la sémantique F # autour de l’occultation qui existe déjà.

Cette fonctionnalité implémente [F # RFC FS-1068](https://github.com/fsharp/fslang-design/blob/master/FSharp-5.0/FS-1068-open-type-declaration.md).

## <a name="consistent-slicing-behavior-for-built-in-data-types"></a>Comportement de découpage cohérent pour les types de données intégrés

Comportement de découpage des types de `FSharp.Core` données intégrés (tableau, liste, chaîne, tableau 2D, tableau 3D, Tableau 4D) qui ne sont pas cohérents avant F # 5. Un comportement de cas d’arête a levé une exception et d’autres non. Dans F # 5, tous les types intégrés retournent désormais des tranches vides pour les tranches impossibles à générer :

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

Cette fonctionnalité implémente [F # RFC FS-1077](https://github.com/fsharp/fslang-design/blob/master/FSharp-5.0/FS-1077-tolerant-slicing.md).

## <a name="fixed-index-slices-for-3d-and-4d-arrays-in-fsharpcore"></a>Sections à index fixe pour les tableaux 3D et 4D dans FSharp. Core

F # 5,0 offre une prise en charge du découpage avec un index fixe dans les types de tableau 3D et 4D intégrés.

Pour illustrer cela, examinez le tableau 3D suivant :

*z = 0*
| x\y   | 0 | 1 |
|-------|---|---|
| **0** | 0 | 1 |
| **1** | 2 | 3 |

*z = 1*
| x\y   | 0 | 1 |
|-------|---|---|
| **0** | 4 | 5 |
| **1** | 6 | 7 |

Que se passe-t-il si vous souhaitez extraire la tranche `[| 4; 5 |]` du tableau ? C’est maintenant très simple !

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

Cette fonctionnalité implémente [F # RFC FS-1077b](https://github.com/fsharp/fslang-design/blob/master/FSharp-5.0/FS-1077-3d-4d-fixed-index-slicing.md).

## <a name="f-quotations-improvements"></a>Améliorations des guillemets F #

Les [citations de code](../language-reference/code-quotations.md) F # peuvent désormais conserver les informations de contrainte de type. Prenons l’exemple suivant :

```fsharp
open FSharp.Linq.RuntimeHelpers

let eval q = LeafExpressionConverter.EvaluateQuotation q

let inline negate x = -x
// val inline negate: x: ^a ->  ^a when  ^a : (static member ( ~- ) :  ^a ->  ^a)

<@ negate 1.0 @>  |> eval
```

La contrainte générée par la `inline` fonction est conservée dans le devis de code. Le `negate` formulaire entre guillemets de la fonction peut maintenant être évalué.

Cette fonctionnalité implémente [F # RFC FS-1071](https://github.com/fsharp/fslang-design/blob/master/FSharp-5.0/FS-1071-witness-passing-quotations.md).

## <a name="applicative-computation-expressions"></a>Expressions de calcul applicative

Les [expressions de calcul](../language-reference/computation-expressions.md) sont utilisées aujourd’hui pour modéliser les « calculs contextuels », ou dans une terminologie plus fonctionnelle, des calculs monadic.

F # 5 introduit les EC d’applicative, qui offrent un modèle de calcul différent. Les EC d’applicative permettent des calculs plus efficaces, à condition que chaque calcul soit indépendant et que ses résultats soient accumulés à la fin. Lorsque les calculs sont indépendants les uns des autres, ils sont également parallèless de manière triviale, ce qui permet aux auteurs CE d’écrire des bibliothèques plus efficaces. Cet avantage est toutefois une restriction : les calculs qui dépendent de valeurs calculées précédemment ne sont pas autorisés.

L’exemple suivant montre un type applicative de base pour le `Result` type.

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

Si vous êtes un auteur de bibliothèque qui expose les EC dans leur bibliothèque aujourd’hui, vous devez prendre en compte certaines considérations supplémentaires.

Cette fonctionnalité implémente [F # RFC FS-1063](https://github.com/fsharp/fslang-design/blob/master/FSharp-5.0/FS-1063-support-letbang-andbang-for-applicative-functors.md).

## <a name="interfaces-can-be-implemented-at-different-generic-instantiations"></a>Les interfaces peuvent être implémentées à différentes instanciations génériques

Vous pouvez désormais implémenter la même interface à différentes instanciations génériques :

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

Cette fonctionnalité implémente [F # RFC FS-1031](https://github.com/fsharp/fslang-design/blob/master/FSharp-5.0/FS-1031-Allow%20implementing%20the%20same%20interface%20at%20different%20generic%20instantiations%20in%20the%20same%20type.md).

## <a name="default-interface-member-consumption"></a>Consommation par défaut des membres d’interface

F # 5 vous permet [de consommer des interfaces avec les implémentations par défaut](../../csharp/tutorials/default-interface-methods-versions.md).

Prenons l’exemple d’une interface définie en C#, comme suit :

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

Vous pouvez l’utiliser en F # par le biais de l’un des moyens standard d’implémenter une interface :

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

Cela vous permet de tirer en toute sécurité du code C# et des composants .NET écrits en C# moderne lorsqu’ils s’attendent à ce que les utilisateurs soient en mesure d’utiliser une implémentation par défaut.

Cette fonctionnalité implémente [F # RFC FS-1074](https://github.com/fsharp/fslang-design/blob/master/FSharp-5.0/FS-1074-default-interface-member-consumption.md).

## <a name="simplified-interop-with-nullable-value-types"></a>Interopérabilité simplifiée avec les types valeur Nullable

Les [types Nullable (valeur)](https://docs.microsoft.com/dotnet/api/system.nullable-1) (appelés types Nullable historiquement) ont longtemps été pris en charge par F #, mais l’interaction avec eux a traditionnellement été une douleur puisque vous auriez dû construire un `Nullable` `Nullable<SomeType>` Wrapper ou chaque fois que vous souhaitiez passer une valeur. À présent, le compilateur convertit implicitement un type valeur en un `Nullable<ThatValueType>` si le type cible correspond à. Le code suivant est désormais possible :

```fsharp
#r "nuget: Microsoft.Data.Analysis"

open Microsoft.Data.Analysis

let dateTimes = PrimitiveDataFrameColumn<DateTime>("DateTimes")

// The following line used to fail to compile
dateTimes.Append(DateTime.Parse("2019/01/01"))

// The previous line is now equivalent to this line
dateTimes.Append(Nullable<DateTime>(DateTime.Parse("2019/01/01")))
```

Cette fonctionnalité implémente [F # RFC FS-1075](https://github.com/fsharp/fslang-design/blob/master/FSharp-5.0/FS-1075-nullable-interop.md).

## <a name="preview-reverse-indexes"></a>Aperçu : index inversés

F # 5 introduit également un aperçu pour autoriser les index inversés. La syntaxe est `^idx`. Voici comment vous pouvez obtenir une valeur d’élément 1 à partir de la fin d’une liste :

```fsharp
let xs = [1..10]

// Get element 1 from the end:
xs.[^1]

// From the end slices

let lastTwoOldStyle = xs.[(xs.Length-2)..]

let lastTwoNewStyle = xs.[^1..]

lastTwoOldStyle = lastTwoNewStyle // true
```

Vous pouvez également définir des index inverses pour vos propres types. Pour ce faire, vous devez implémenter la méthode suivante :

```fsharp
GetReverseIndex: dimension: int -> offset: int
```

Voici un exemple pour le `Span<'T>` type :

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

Cette fonctionnalité implémente [F # RFC FS-1076](https://github.com/fsharp/fslang-design/blob/master/preview/FS-1076-from-the-end-slicing.md).

## <a name="preview-overloads-of-custom-keywords-in-computation-expressions"></a>Aperçu : surcharges de mots clés personnalisés dans les expressions de calcul

Les expressions de calcul sont une fonctionnalité puissante pour les auteurs de bibliothèques et de frameworks. Elles vous permettent d’améliorer de façon considérable l’expressivité de vos composants en vous permettant de définir des membres connus et de former une DSL pour le domaine dans lequel vous travaillez.

F # 5 ajoute la prise en charge de l’Aperçu pour la surcharge des opérations personnalisées dans les expressions de calcul. Il permet l’écriture et la consommation du code suivant :

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

Avant cette modification, vous pouviez écrire le `InputBuilder` type tel quel, mais vous ne pouviez pas l’utiliser de la façon dont il est utilisé dans l’exemple. Dans la mesure où les surcharges, les paramètres facultatifs et les `System.ParamArray` types Now sont autorisés, tout fonctionne comme prévu.

Cette fonctionnalité implémente [F # RFC FS-1056](https://github.com/fsharp/fslang-design/blob/master/preview/FS-1056-allow-custom-operation-overloads.md).
