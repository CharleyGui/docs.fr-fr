---
title: 'Nouveautés du guide F # 4,5-F #'
description: 'Profitez d’une vue d’ensemble des nouvelles fonctionnalités disponibles dans F # 4,5.'
ms.date: 11/27/2019
ms.openlocfilehash: 2c978c66a4bf231398508cbc1cbb8839228ea8e9
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2020
ms.locfileid: "84202350"
---
# <a name="whats-new-in-f-45"></a>Nouveautés de F # 4,5

F # 4,5 ajoute plusieurs améliorations au langage F #. La plupart de ces fonctionnalités ont été ajoutées ensemble pour vous permettre d’écrire du code efficace en F # tout en garantissant que ce code est sécurisé. Cela implique l’ajout de quelques concepts au langage et une quantité significative d’analyse du compilateur lors de l’utilisation de ces constructions.

## <a name="get-started"></a>Prendre en main

F # 4,5 est disponible dans toutes les distributions .NET Core et les outils Visual Studio. [Commencez à utiliser F #](../get-started/index.md) pour en savoir plus.

## <a name="span-and-byref-like-structs"></a>Structs et structs de type ByRef

Le <xref:System.Span%601> type introduit dans .net Core vous permet de représenter des mémoires tampons en mémoire d’une manière fortement typée, qui est désormais autorisée dans f # à partir de f # 4,5. L’exemple suivant montre comment vous pouvez réutiliser une fonction opérant sur un <xref:System.Span%601> avec différentes représentations de mémoire tampon :

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

Un aspect important de cette opération est que span et d’autres [structs de type ByRef](../language-reference/structures.md#byreflike-structs) ont une analyse statique très rigide effectuée par le compilateur, qui limitent leur utilisation de manière inattendue. Il s’agit du compromis fondamental entre les performances, l’expressivité et la sécurité introduites dans F # 4,5.

## <a name="revamped-byrefs"></a>Types ByRef remanié

Avant F # 4,5, [types ByRef](../language-reference/byrefs.md) en f # était risqué et incertain pour de nombreuses applications. Les problèmes de son autour de types ByRef ont été résolus dans F # 4,5 et la même analyse statique effectuée pour les structs de type span et de type ByRef a également été appliquée.

### <a name="inreft-and-outreft"></a>inref< t> et outref<>

Pour représenter la notion de pointeur managé en lecture seule, en écriture seule et en lecture/écriture, F # 4,5 introduit les `inref<'T>` types, `outref<'T>` pour représenter les pointeurs en lecture seule et en écriture seule, respectivement. Chacun a une sémantique différente. Par exemple, vous ne pouvez pas écrire dans `inref<'T>` :

```fsharp
let f (dt: inref<DateTime>) =
    dt <- DateTime.Now // ERROR - cannot write to an inref!
```

Par défaut, l’inférence de type déduira les pointeurs managés comme étant `inref<'T>` en ligne avec la nature immuable du code F #, sauf si un événement a déjà été déclaré comme mutable. Pour rendre un élément accessible en écriture, vous devez déclarer un type comme `mutable` avant de passer son adresse à une fonction ou un membre qui le manipule. Pour plus d’informations, consultez [types ByRef](../language-reference/byrefs.md).

## <a name="readonly-structs"></a>Structs en lecture seule

À compter de F # 4,5, vous pouvez annoter un struct avec <xref:System.Runtime.CompilerServices.IsReadOnlyAttribute> comme tel :

```fsharp
[<IsReadOnly; Struct>]
type S(count1: int, count2: int) =
    member x.Count1 = count1
    member x.Count2 = count2
```

Cela vous interdit de déclarer un membre mutable dans le struct et émet des métadonnées qui permettent à F # et C# de le traiter comme ReadOnly lorsqu’il est consommé à partir d’un assembly. Pour plus d’informations, consultez [ReadOnly, structs](../language-reference/structures.md#readonly-structs).

## <a name="void-pointers"></a>Pointeurs void

Le `voidptr` type est ajouté à F # 4,5, comme les fonctions suivantes :

* `NativePtr.ofVoidPtr`pour convertir un pointeur void en pointeur int natif
* `NativePtr.toVoidPtr`pour convertir un pointeur int natif en pointeur void

Cela est utile lors de l’interopérabilité avec un composant natif qui utilise des pointeurs void.

## <a name="the-match-keyword"></a>Le mot clé `match!`

Le `match!` mot clé améliore la mise en correspondance des modèles quand il se trouve à l’intérieur d’une expression de calcul :

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

Cela vous permet de raccourcir le code qui implique souvent des options de mixage (ou d’autres types) avec des expressions de calcul telles que Async. Pour plus d’informations, consultez [match !](../language-reference/computation-expressions.md#match).

## <a name="relaxed-upcasting-requirements-in-array-list-and-sequence-expressions"></a>Exigences en matière de conversion souple dans les expressions de tableau, de liste et de séquence

Le mélange de types où un peut hériter d’un autre dans un tableau, une liste et des expressions de séquence vous impose traditionnellement de convertir tout type dérivé en son type parent avec `:>` ou `upcast` . Cette procédure est maintenant assouplie, comme suit :

```fsharp
let x0 : obj list  = [ "a" ] // ok pre-F# 4.5
let x1 : obj list  = [ "a"; "b" ] // ok pre-F# 4.5
let x2 : obj list  = [ yield "a" :> obj ] // ok pre-F# 4.5

let x3 : obj list  = [ yield "a" ] // Now ok for F# 4.5, and can replace x2
```

## <a name="indentation-relaxation-for-array-and-list-expressions"></a>Assouplissement de la mise en retrait pour les expressions de tableau et de liste

Avant F # 4,5, vous deviez mettre en retrait excessivement les expressions de tableau et de liste quand elles sont passées en tant qu’arguments aux appels de méthode. Cela n’est plus nécessaire :

```fsharp
module NoExcessiveIndenting =
    System.Console.WriteLine(format="{0}", arg = [|
        "hello"
    |])
    System.Console.WriteLine([|
        "hello"
    |])
```
