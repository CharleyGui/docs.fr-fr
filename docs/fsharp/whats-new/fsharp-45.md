---
title: Quoi de neuf dans le guide F 4.5 - Guide de F
description: Obtenez un aperçu des nouvelles fonctionnalités disponibles dans le F 4.5.
ms.date: 11/27/2019
ms.openlocfilehash: 560e3dd941f79b76d3b864ba0f6560be154ebc1a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186134"
---
# <a name="whats-new-in-f-45"></a>Quoi de neuf dans F 4.5

F 4.5 ajoute de multiples améliorations à la langue F. Beaucoup de ces fonctionnalités ont été ajoutées ensemble pour vous permettre d’écrire du code efficace dans F tout en vous assurant que ce code est sûr. Cela signifie ajouter quelques concepts à la langue et une quantité importante d’analyse compilateur lors de l’utilisation de ces constructions.

## <a name="get-started"></a>Prise en main

F 4.5 est disponible dans toutes les distributions .NET Core et l’outillage Visual Studio. [Commence avec F pour](../get-started/index.md) en savoir plus.

## <a name="span-and-byref-like-structs"></a>Span et structs de la fe de byref

Le <xref:System.Span%601> type introduit dans .NET Core vous permet de représenter les tampons dans la mémoire d’une manière fortement typée, qui est maintenant autorisé en F 'en commençant par F 4.5. L’exemple suivant montre comment vous pouvez réutilisation d’une fonction fonction fonctionnant sur un <xref:System.Span%601> avec différentes représentations tampons:

```fsharp
let safeSum (bytes: Span<byte>) =
    let mutable sum = 0
    for i in 0 .. bytes.Length - 1 do
        sum <- sum + int bytes.[i]
    sum

// managed memory
let arrayMemory = Array.zeroCreate<byte>(100)
let arraySpan = new Span<byte>(arrayMemory)

safeSum(arraySpan) |> printfn "res = %d"

// native memory
let nativeMemory = Marshal.AllocHGlobal(100);
let nativeSpan = new Span<byte>(nativeMemory.ToPointer(), 100)

safeSum(nativeSpan) |> printfn "res = %d"
Marshal.FreeHGlobal(nativeMemory)

// stack memory
let mem = NativePtr.stackalloc<byte>(100)
let mem2 = mem |> NativePtr.toVoidPtr
let stackSpan = Span<byte>(mem2, 100)

safeSum(stackSpan) |> printfn "res = %d"
```

Un aspect important à cela est que Span et d’autres [structs byref-like](../language-reference/structures.md#byreflike-structs) ont une analyse statique très rigide effectuée par le compilateur qui limitent leur utilisation d’une manière que vous pourriez trouver inattendu. Il s’agit du compromis fondamental entre la performance, l’expressivité et la sécurité qui est introduite dans le F 4.5.

## <a name="revamped-byrefs"></a>Remanié byrefs

Avant le F 4.5, [les Byrefs](../language-reference/byrefs.md) en F étaient dangereux et insensés pour de nombreuses applications. Les problèmes de solidité autour des byrefs ont été abordés dans le F 4.5 et la même analyse statique effectuée pour la durée et les structs de type byref a également été appliquée.

### <a name="inreft-and-outreft"></a>inref<'> et outref<'>

Pour représenter la notion d’un pointeur géré de lecture seulement, d’écrire seulement, `inref<'T>`et `outref<'T>` de lire/écrire, F 4.5 introduit les types de lecture seulement et d’écrire seulement, respectivement. Chacun a une sémantique différente. Par exemple, vous ne `inref<'T>`pouvez pas écrire à un :

```fsharp
let f (dt: inref<DateTime>) =
    dt <- DateTime.Now // ERROR - cannot write to an inref!
```

Par défaut, l’inférence de type `inref<'T>` infèrera les pointeurs gérés quant à la nature immuable du code F, à moins que quelque chose n’ait déjà été déclaré mutable. Pour rendre quelque chose de bref, vous devrez `mutable` déclarer un type comme avant de passer son adresse à une fonction ou un membre qui le manipule. Pour en savoir plus, voir [Byrefs](../language-reference/byrefs.md).

## <a name="readonly-structs"></a>Restructurations de Readonly

En commençant par F 4.5, vous pouvez <xref:System.Runtime.CompilerServices.IsReadOnlyAttribute> annoter une structure avec en tant que telle:

```fsharp
[<IsReadOnly; Struct>]
type S(count1: int, count2: int) =
    member x.Count1 = count1
    member x.Count2 = count2
```

Cela vous empêche de déclarer un membre mutable dans la struction et émet des métadonnées qui permettent à F et CMD de le traiter comme l’airsible lorsqu’il est consommé à partir d’un assemblage. Pour en savoir plus, voir [ReadOnly structs](../language-reference/structures.md#readonly-structs).

## <a name="void-pointers"></a>Pointeurs vides

Le `voidptr` type est ajouté à F 4.5, de même que les fonctions suivantes :

* `NativePtr.ofVoidPtr`pour convertir un pointeur vide en un pointeur int natif
* `NativePtr.toVoidPtr`pour convertir un pointeur int natif à un pointeur vide

Ceci est utile lors de l’interopération avec un composant indigène qui fait usage de pointeurs vides.

## <a name="the-match-keyword"></a>Le mot clé `match!`

Le `match!` mot clé améliore l’appariement du modèle à l’intérieur d’une expression de calcul :

```fsharp
// Code that returns an asynchronous option
let checkBananaAsync (s: string) =
    async {
        if s = "banana" then
            return Some s
        else
            return None
    }

// Now you can use 'match!'
let funcWithString (s: string) =
    async {
        match! checkBananaAsync s with
        | Some bananaString -> printfn "It's banana!"
        | None -> printfn "%s" s
}
```

Cela vous permet de raccourcir le code qui implique souvent le mélange d’options (ou d’autres types) avec des expressions de calcul telles que l’async. Pour en savoir plus, voir [match!](../language-reference/computation-expressions.md#match).

## <a name="relaxed-upcasting-requirements-in-array-list-and-sequence-expressions"></a>Exigences de diffusion assouplies dans les expressions de tableau, de liste et de séquence

Les types de mélange où l’on peut hériter d’un autre à l’intérieur `:>` `upcast`de la gamme, la liste, et les expressions de séquence vous a traditionnellement exigé de upcast tout type dérivé à son type parent avec ou . Ceci est maintenant détendu, démontré comme suit:

```fsharp
let x0 : obj list  = [ "a" ] // ok pre-F# 4.5
let x1 : obj list  = [ "a"; "b" ] // ok pre-F# 4.5
let x2 : obj list  = [ yield "a" :> obj ] // ok pre-F# 4.5

let x3 : obj list  = [ yield "a" ] // Now ok for F# 4.5, and can replace x2
```

## <a name="indentation-relaxation-for-array-and-list-expressions"></a>Relaxation d’indentation pour les expressions de tableau et de liste

Avant F 4.5, vous aviez besoin de tableau excessivement en retrait et d’énumérer les expressions lorsqu’ils sont adoptés comme arguments aux appels de méthode. Ce n’est plus nécessaire :

```fsharp
module NoExcessiveIndenting =
    System.Console.WriteLine(format="{0}", arg = [|
        "hello"
    |])
    System.Console.WriteLine([|
        "hello"
    |])
```
