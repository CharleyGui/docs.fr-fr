---
title: Nouveautés de F# 4,5- F# Guide
description: Bénéficiez d’une vue d’ensemble des nouvelles F# fonctionnalités disponibles dans 4,5.
ms.date: 11/27/2019
ms.openlocfilehash: b699165125d345ad783b24da8a0a994cba72d4ba
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715686"
---
# <a name="whats-new-in-f-45"></a><span data-ttu-id="2013a-103">Nouveautés de F# 4,5</span><span class="sxs-lookup"><span data-stu-id="2013a-103">What's new in F# 4.5</span></span>

<span data-ttu-id="2013a-104">F#4,5 ajoute plusieurs améliorations au F# langage.</span><span class="sxs-lookup"><span data-stu-id="2013a-104">F# 4.5 adds multiple improvements to the F# language.</span></span> <span data-ttu-id="2013a-105">La plupart de ces fonctionnalités ont été ajoutées ensemble pour vous permettre d’écrire du F# code efficace dans tout en garantissant que ce code est sécurisé.</span><span class="sxs-lookup"><span data-stu-id="2013a-105">Many of these features were added together to enable you to write efficient code in F# while also ensuring this code is safe.</span></span> <span data-ttu-id="2013a-106">Cela implique l’ajout de quelques concepts au langage et une quantité significative d’analyse du compilateur lors de l’utilisation de ces constructions.</span><span class="sxs-lookup"><span data-stu-id="2013a-106">Doing so means adding a few concepts to the language and a significant amount of compiler analysis when using these constructs.</span></span>

## <a name="get-started"></a><span data-ttu-id="2013a-107">Prise en main</span><span class="sxs-lookup"><span data-stu-id="2013a-107">Get started</span></span>

<span data-ttu-id="2013a-108">F#4,5 est disponible dans toutes les distributions .NET Core et les outils Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2013a-108">F# 4.5 is available in all .NET Core distributions and Visual Studio tooling.</span></span> <span data-ttu-id="2013a-109">[Commencez avec F# ](../get-started/index.md) pour en savoir plus.</span><span class="sxs-lookup"><span data-stu-id="2013a-109">[Get started with F#](../get-started/index.md) to learn more.</span></span>

## <a name="span-and-byref-like-structs"></a><span data-ttu-id="2013a-110">Structs et structs de type ByRef</span><span class="sxs-lookup"><span data-stu-id="2013a-110">Span and byref-like structs</span></span>

<span data-ttu-id="2013a-111">Le type de <xref:System.Span%601> introduit dans .NET Core vous permet de représenter des mémoires tampons en mémoire d’une manière fortement typée, qui est F# désormais autorisée F# dans à partir de 4,5.</span><span class="sxs-lookup"><span data-stu-id="2013a-111">The <xref:System.Span%601> type introduced in .NET Core allows you to represent buffers in memory in a strongly-typed manner, which is now allowed in F# starting with F# 4.5.</span></span> <span data-ttu-id="2013a-112">L’exemple suivant montre comment vous pouvez réutiliser une fonction opérant sur un <xref:System.Span%601> avec différentes représentations de mémoire tampon :</span><span class="sxs-lookup"><span data-stu-id="2013a-112">The following example shows how you can re-use a function operating on a <xref:System.Span%601> with different buffer representations:</span></span>

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

<span data-ttu-id="2013a-113">Un aspect important de cette opération est que span et d’autres [structs de type ByRef](../language-reference/structures.md#byreflike-structs) ont une analyse statique très rigide effectuée par le compilateur, qui limitent leur utilisation de manière inattendue.</span><span class="sxs-lookup"><span data-stu-id="2013a-113">An important aspect to this is that Span and other [byref-like structs](../language-reference/structures.md#byreflike-structs) have very rigid static analysis performed by the compiler that restrict their usage in ways you might find to be unexpected.</span></span> <span data-ttu-id="2013a-114">Il s’agit du compromis fondamental entre les performances, l’expressivité et la sécurité introduites dans F# 4,5.</span><span class="sxs-lookup"><span data-stu-id="2013a-114">This is the fundamental tradeoff between performance, expressiveness, and safety that is introduced in F# 4.5.</span></span>

## <a name="revamped-byrefs"></a><span data-ttu-id="2013a-115">Types ByRef remanié</span><span class="sxs-lookup"><span data-stu-id="2013a-115">Revamped byrefs</span></span>

<span data-ttu-id="2013a-116">Avant le F# 4,5, [types ByRef](../language-reference/byrefs.md) dans F# était risqué et incertain pour de nombreuses applications.</span><span class="sxs-lookup"><span data-stu-id="2013a-116">Prior to F# 4.5, [Byrefs](../language-reference/byrefs.md) in F# were unsafe and unsound for numerous applications.</span></span> <span data-ttu-id="2013a-117">Les problèmes de la solidité autour de types ByRef F# ont été résolus dans 4,5 et la même analyse statique effectuée pour les structs de type span et ByRef a également été appliquée.</span><span class="sxs-lookup"><span data-stu-id="2013a-117">Soundness issues around byrefs have been addressed in F# 4.5 and the same static analysis done for span and byref-like structs was also applied.</span></span>

### <a name="inreft-and-outreft"></a><span data-ttu-id="2013a-118">inref < t > et outref < ></span><span class="sxs-lookup"><span data-stu-id="2013a-118">inref<'T> and outref<'T></span></span>

<span data-ttu-id="2013a-119">Pour représenter la notion de pointeur managé en lecture seule, en écriture seule et en lecture/écriture, F# 4,5 introduit les types de `inref<'T>`, `outref<'T>` pour représenter les pointeurs en lecture seule et en écriture seule, respectivement.</span><span class="sxs-lookup"><span data-stu-id="2013a-119">To represent the notion of a read-only, write-only, and read/write managed pointer, F# 4.5 introduces the `inref<'T>`, `outref<'T>` types to represent read-only and write-only pointers, respectively.</span></span> <span data-ttu-id="2013a-120">Chacun a une sémantique différente.</span><span class="sxs-lookup"><span data-stu-id="2013a-120">Each have different semantics.</span></span> <span data-ttu-id="2013a-121">Par exemple, vous ne pouvez pas écrire dans un `inref<'T>`:</span><span class="sxs-lookup"><span data-stu-id="2013a-121">For example, you cannot write to an `inref<'T>`:</span></span>

```fsharp
let f (dt: inref<DateTime>) =
    dt <- DateTime.Now // ERROR - cannot write to an inref!
```

<span data-ttu-id="2013a-122">Par défaut, l’inférence de type déduira les pointeurs managés comme `inref<'T>` pour être en ligne avec la nature F# immuable du code, sauf si un événement a déjà été déclaré comme mutable.</span><span class="sxs-lookup"><span data-stu-id="2013a-122">By default, type inference will infer managed pointers as `inref<'T>` to be in line with the immutable nature of F# code, unless something has already been declared as mutable.</span></span> <span data-ttu-id="2013a-123">Pour rendre un élément accessible en écriture, vous devez déclarer un type comme `mutable` avant de passer son adresse à une fonction ou un membre qui le manipule.</span><span class="sxs-lookup"><span data-stu-id="2013a-123">To make something writable, you'll need to declare a type as `mutable` before passing its address to a function or member that manipulates it.</span></span> <span data-ttu-id="2013a-124">Pour plus d’informations, consultez [types ByRef](../language-reference/byrefs.md).</span><span class="sxs-lookup"><span data-stu-id="2013a-124">To learn more, see [Byrefs](../language-reference/byrefs.md).</span></span>

## <a name="readonly-structs"></a><span data-ttu-id="2013a-125">Structs en lecture seule</span><span class="sxs-lookup"><span data-stu-id="2013a-125">Readonly structs</span></span>

<span data-ttu-id="2013a-126">À partir F# de 4,5, vous pouvez annoter un struct avec <xref:System.Runtime.CompilerServices.IsReadOnlyAttribute> comme suit :</span><span class="sxs-lookup"><span data-stu-id="2013a-126">Starting with F# 4.5, you can annotate a struct with <xref:System.Runtime.CompilerServices.IsReadOnlyAttribute> as such:</span></span>

```fsharp
[<IsReadOnly; Struct>]
type S(count1: int, count2: int) =
    member x.Count1 = count1
    member x.Count2 = count2
```

<span data-ttu-id="2013a-127">Cela vous interdit de déclarer un membre mutable dans le struct et émet des métadonnées qui autorisent F# et C# le traitent comme ReadOnly lorsqu’il est consommé à partir d’un assembly.</span><span class="sxs-lookup"><span data-stu-id="2013a-127">This disallows you from declaring a mutable member in the struct and emits metadata that allows F# and C# to treat it as readonly when consumed from an assembly.</span></span> <span data-ttu-id="2013a-128">Pour plus d’informations, consultez [ReadOnly, structs](../language-reference/structures.md#readonly-structs).</span><span class="sxs-lookup"><span data-stu-id="2013a-128">To learn more, see [ReadOnly structs](../language-reference/structures.md#readonly-structs).</span></span>

## <a name="void-pointers"></a><span data-ttu-id="2013a-129">Pointeurs void</span><span class="sxs-lookup"><span data-stu-id="2013a-129">Void pointers</span></span>

<span data-ttu-id="2013a-130">Le type de `voidptr` est ajouté F# à 4,5, comme les fonctions suivantes :</span><span class="sxs-lookup"><span data-stu-id="2013a-130">The `voidptr` type is added to F# 4.5, as are the following functions:</span></span>

* <span data-ttu-id="2013a-131">`NativePtr.ofVoidPtr` de convertir un pointeur void en pointeur int natif</span><span class="sxs-lookup"><span data-stu-id="2013a-131">`NativePtr.ofVoidPtr` to convert a void pointer into a native int pointer</span></span>
* <span data-ttu-id="2013a-132">`NativePtr.toVoidPtr` de convertir un pointeur int natif en pointeur void</span><span class="sxs-lookup"><span data-stu-id="2013a-132">`NativePtr.toVoidPtr` to convert a native int pointer to a void pointer</span></span>

<span data-ttu-id="2013a-133">Cela est utile lors de l’interopérabilité avec un composant natif qui utilise des pointeurs void.</span><span class="sxs-lookup"><span data-stu-id="2013a-133">This is helpful when interoperating with a native component that makes use of void pointers.</span></span>

## <a name="the-match-keyword"></a><span data-ttu-id="2013a-134">Le mot clé `match!`</span><span class="sxs-lookup"><span data-stu-id="2013a-134">The `match!` keyword</span></span>

<span data-ttu-id="2013a-135">Le mot clé `match!` améliore les critères spéciaux quand il se trouve à l’intérieur d’une expression de calcul :</span><span class="sxs-lookup"><span data-stu-id="2013a-135">The `match!` keyword enhances pattern matching when inside a computation expression:</span></span>

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

<span data-ttu-id="2013a-136">Cela vous permet de raccourcir le code qui implique souvent des options de mixage (ou d’autres types) avec des expressions de calcul telles que Async.</span><span class="sxs-lookup"><span data-stu-id="2013a-136">This allows you to shorten code that often involves mixing options (or other types) with computation expressions such as async.</span></span> <span data-ttu-id="2013a-137">Pour plus d’informations, consultez [match !](../language-reference/computation-expressions.md#match).</span><span class="sxs-lookup"><span data-stu-id="2013a-137">To learn more, see [match!](../language-reference/computation-expressions.md#match).</span></span>

## <a name="relaxed-upcasting-requirements-in-array-list-and-sequence-expressions"></a><span data-ttu-id="2013a-138">Exigences en matière de conversion souple dans les expressions de tableau, de liste et de séquence</span><span class="sxs-lookup"><span data-stu-id="2013a-138">Relaxed upcasting requirements in array, list, and sequence expressions</span></span>

<span data-ttu-id="2013a-139">Le mélange de types où un peut hériter d’un autre à l’intérieur d’une table, d’une liste et d’expressions de séquence vous impose traditionnellement de convertir tout type dérivé en son type parent avec `:>` ou `upcast`.</span><span class="sxs-lookup"><span data-stu-id="2013a-139">Mixing types where one may inherit from another inside of array, list, and sequence expressions has traditionally required you to upcast any derived type to its parent type with `:>` or `upcast`.</span></span> <span data-ttu-id="2013a-140">Cette procédure est maintenant assouplie, comme suit :</span><span class="sxs-lookup"><span data-stu-id="2013a-140">This is now relaxed, demonstrated as follows:</span></span>

```fsharp
let x0 : obj list  = [ "a" ] // ok pre-F# 4.5
let x1 : obj list  = [ "a"; "b" ] // ok pre-F# 4.5
let x2 : obj list  = [ yield "a" :> obj ] // ok pre-F# 4.5

let x3 : obj list  = [ yield "a" ] // Now ok for F# 4.5, and can replace x2
```

## <a name="indentation-relaxation-for-array-and-list-expressions"></a><span data-ttu-id="2013a-141">Assouplissement de la mise en retrait pour les expressions de tableau et de liste</span><span class="sxs-lookup"><span data-stu-id="2013a-141">Indentation relaxation for array and list expressions</span></span>

<span data-ttu-id="2013a-142">Avant le F# 4,5, vous deviez mettre en retrait excessivement les expressions de tableau et de liste quand elles sont passées en tant qu’arguments aux appels de méthode.</span><span class="sxs-lookup"><span data-stu-id="2013a-142">Prior to F# 4.5, you needed to excessively indent array and list expressions when passed as arguments to method calls.</span></span> <span data-ttu-id="2013a-143">Cela n’est plus nécessaire :</span><span class="sxs-lookup"><span data-stu-id="2013a-143">This is no longer required:</span></span>

```fsharp
module NoExcessiveIndenting = 
    System.Console.WriteLine(format="{0}", arg = [| 
        "hello"
    |])
    System.Console.WriteLine([|
        "hello"
    |])
```
