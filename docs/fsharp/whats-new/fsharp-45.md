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
# <a name="whats-new-in-f-45"></a><span data-ttu-id="b24d3-103">Quoi de neuf dans F 4.5</span><span class="sxs-lookup"><span data-stu-id="b24d3-103">What's new in F# 4.5</span></span>

<span data-ttu-id="b24d3-104">F 4.5 ajoute de multiples améliorations à la langue F.</span><span class="sxs-lookup"><span data-stu-id="b24d3-104">F# 4.5 adds multiple improvements to the F# language.</span></span> <span data-ttu-id="b24d3-105">Beaucoup de ces fonctionnalités ont été ajoutées ensemble pour vous permettre d’écrire du code efficace dans F tout en vous assurant que ce code est sûr.</span><span class="sxs-lookup"><span data-stu-id="b24d3-105">Many of these features were added together to enable you to write efficient code in F# while also ensuring this code is safe.</span></span> <span data-ttu-id="b24d3-106">Cela signifie ajouter quelques concepts à la langue et une quantité importante d’analyse compilateur lors de l’utilisation de ces constructions.</span><span class="sxs-lookup"><span data-stu-id="b24d3-106">Doing so means adding a few concepts to the language and a significant amount of compiler analysis when using these constructs.</span></span>

## <a name="get-started"></a><span data-ttu-id="b24d3-107">Prise en main</span><span class="sxs-lookup"><span data-stu-id="b24d3-107">Get started</span></span>

<span data-ttu-id="b24d3-108">F 4.5 est disponible dans toutes les distributions .NET Core et l’outillage Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b24d3-108">F# 4.5 is available in all .NET Core distributions and Visual Studio tooling.</span></span> <span data-ttu-id="b24d3-109">[Commence avec F pour](../get-started/index.md) en savoir plus.</span><span class="sxs-lookup"><span data-stu-id="b24d3-109">[Get started with F#](../get-started/index.md) to learn more.</span></span>

## <a name="span-and-byref-like-structs"></a><span data-ttu-id="b24d3-110">Span et structs de la fe de byref</span><span class="sxs-lookup"><span data-stu-id="b24d3-110">Span and byref-like structs</span></span>

<span data-ttu-id="b24d3-111">Le <xref:System.Span%601> type introduit dans .NET Core vous permet de représenter les tampons dans la mémoire d’une manière fortement typée, qui est maintenant autorisé en F 'en commençant par F 4.5.</span><span class="sxs-lookup"><span data-stu-id="b24d3-111">The <xref:System.Span%601> type introduced in .NET Core allows you to represent buffers in memory in a strongly-typed manner, which is now allowed in F# starting with F# 4.5.</span></span> <span data-ttu-id="b24d3-112">L’exemple suivant montre comment vous pouvez réutilisation d’une fonction fonction fonctionnant sur un <xref:System.Span%601> avec différentes représentations tampons:</span><span class="sxs-lookup"><span data-stu-id="b24d3-112">The following example shows how you can re-use a function operating on a <xref:System.Span%601> with different buffer representations:</span></span>

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

<span data-ttu-id="b24d3-113">Un aspect important à cela est que Span et d’autres [structs byref-like](../language-reference/structures.md#byreflike-structs) ont une analyse statique très rigide effectuée par le compilateur qui limitent leur utilisation d’une manière que vous pourriez trouver inattendu.</span><span class="sxs-lookup"><span data-stu-id="b24d3-113">An important aspect to this is that Span and other [byref-like structs](../language-reference/structures.md#byreflike-structs) have very rigid static analysis performed by the compiler that restrict their usage in ways you might find to be unexpected.</span></span> <span data-ttu-id="b24d3-114">Il s’agit du compromis fondamental entre la performance, l’expressivité et la sécurité qui est introduite dans le F 4.5.</span><span class="sxs-lookup"><span data-stu-id="b24d3-114">This is the fundamental tradeoff between performance, expressiveness, and safety that is introduced in F# 4.5.</span></span>

## <a name="revamped-byrefs"></a><span data-ttu-id="b24d3-115">Remanié byrefs</span><span class="sxs-lookup"><span data-stu-id="b24d3-115">Revamped byrefs</span></span>

<span data-ttu-id="b24d3-116">Avant le F 4.5, [les Byrefs](../language-reference/byrefs.md) en F étaient dangereux et insensés pour de nombreuses applications.</span><span class="sxs-lookup"><span data-stu-id="b24d3-116">Prior to F# 4.5, [Byrefs](../language-reference/byrefs.md) in F# were unsafe and unsound for numerous applications.</span></span> <span data-ttu-id="b24d3-117">Les problèmes de solidité autour des byrefs ont été abordés dans le F 4.5 et la même analyse statique effectuée pour la durée et les structs de type byref a également été appliquée.</span><span class="sxs-lookup"><span data-stu-id="b24d3-117">Soundness issues around byrefs have been addressed in F# 4.5 and the same static analysis done for span and byref-like structs was also applied.</span></span>

### <a name="inreft-and-outreft"></a><span data-ttu-id="b24d3-118">inref<'> et outref<'></span><span class="sxs-lookup"><span data-stu-id="b24d3-118">inref<'T> and outref<'T></span></span>

<span data-ttu-id="b24d3-119">Pour représenter la notion d’un pointeur géré de lecture seulement, d’écrire seulement, `inref<'T>`et `outref<'T>` de lire/écrire, F 4.5 introduit les types de lecture seulement et d’écrire seulement, respectivement.</span><span class="sxs-lookup"><span data-stu-id="b24d3-119">To represent the notion of a read-only, write-only, and read/write managed pointer, F# 4.5 introduces the `inref<'T>`, `outref<'T>` types to represent read-only and write-only pointers, respectively.</span></span> <span data-ttu-id="b24d3-120">Chacun a une sémantique différente.</span><span class="sxs-lookup"><span data-stu-id="b24d3-120">Each have different semantics.</span></span> <span data-ttu-id="b24d3-121">Par exemple, vous ne `inref<'T>`pouvez pas écrire à un :</span><span class="sxs-lookup"><span data-stu-id="b24d3-121">For example, you cannot write to an `inref<'T>`:</span></span>

```fsharp
let f (dt: inref<DateTime>) =
    dt <- DateTime.Now // ERROR - cannot write to an inref!
```

<span data-ttu-id="b24d3-122">Par défaut, l’inférence de type `inref<'T>` infèrera les pointeurs gérés quant à la nature immuable du code F, à moins que quelque chose n’ait déjà été déclaré mutable.</span><span class="sxs-lookup"><span data-stu-id="b24d3-122">By default, type inference will infer managed pointers as `inref<'T>` to be in line with the immutable nature of F# code, unless something has already been declared as mutable.</span></span> <span data-ttu-id="b24d3-123">Pour rendre quelque chose de bref, vous devrez `mutable` déclarer un type comme avant de passer son adresse à une fonction ou un membre qui le manipule.</span><span class="sxs-lookup"><span data-stu-id="b24d3-123">To make something writable, you'll need to declare a type as `mutable` before passing its address to a function or member that manipulates it.</span></span> <span data-ttu-id="b24d3-124">Pour en savoir plus, voir [Byrefs](../language-reference/byrefs.md).</span><span class="sxs-lookup"><span data-stu-id="b24d3-124">To learn more, see [Byrefs](../language-reference/byrefs.md).</span></span>

## <a name="readonly-structs"></a><span data-ttu-id="b24d3-125">Restructurations de Readonly</span><span class="sxs-lookup"><span data-stu-id="b24d3-125">Readonly structs</span></span>

<span data-ttu-id="b24d3-126">En commençant par F 4.5, vous pouvez <xref:System.Runtime.CompilerServices.IsReadOnlyAttribute> annoter une structure avec en tant que telle:</span><span class="sxs-lookup"><span data-stu-id="b24d3-126">Starting with F# 4.5, you can annotate a struct with <xref:System.Runtime.CompilerServices.IsReadOnlyAttribute> as such:</span></span>

```fsharp
[<IsReadOnly; Struct>]
type S(count1: int, count2: int) =
    member x.Count1 = count1
    member x.Count2 = count2
```

<span data-ttu-id="b24d3-127">Cela vous empêche de déclarer un membre mutable dans la struction et émet des métadonnées qui permettent à F et CMD de le traiter comme l’airsible lorsqu’il est consommé à partir d’un assemblage.</span><span class="sxs-lookup"><span data-stu-id="b24d3-127">This disallows you from declaring a mutable member in the struct and emits metadata that allows F# and C# to treat it as readonly when consumed from an assembly.</span></span> <span data-ttu-id="b24d3-128">Pour en savoir plus, voir [ReadOnly structs](../language-reference/structures.md#readonly-structs).</span><span class="sxs-lookup"><span data-stu-id="b24d3-128">To learn more, see [ReadOnly structs](../language-reference/structures.md#readonly-structs).</span></span>

## <a name="void-pointers"></a><span data-ttu-id="b24d3-129">Pointeurs vides</span><span class="sxs-lookup"><span data-stu-id="b24d3-129">Void pointers</span></span>

<span data-ttu-id="b24d3-130">Le `voidptr` type est ajouté à F 4.5, de même que les fonctions suivantes :</span><span class="sxs-lookup"><span data-stu-id="b24d3-130">The `voidptr` type is added to F# 4.5, as are the following functions:</span></span>

* <span data-ttu-id="b24d3-131">`NativePtr.ofVoidPtr`pour convertir un pointeur vide en un pointeur int natif</span><span class="sxs-lookup"><span data-stu-id="b24d3-131">`NativePtr.ofVoidPtr` to convert a void pointer into a native int pointer</span></span>
* <span data-ttu-id="b24d3-132">`NativePtr.toVoidPtr`pour convertir un pointeur int natif à un pointeur vide</span><span class="sxs-lookup"><span data-stu-id="b24d3-132">`NativePtr.toVoidPtr` to convert a native int pointer to a void pointer</span></span>

<span data-ttu-id="b24d3-133">Ceci est utile lors de l’interopération avec un composant indigène qui fait usage de pointeurs vides.</span><span class="sxs-lookup"><span data-stu-id="b24d3-133">This is helpful when interoperating with a native component that makes use of void pointers.</span></span>

## <a name="the-match-keyword"></a><span data-ttu-id="b24d3-134">Le mot clé `match!`</span><span class="sxs-lookup"><span data-stu-id="b24d3-134">The `match!` keyword</span></span>

<span data-ttu-id="b24d3-135">Le `match!` mot clé améliore l’appariement du modèle à l’intérieur d’une expression de calcul :</span><span class="sxs-lookup"><span data-stu-id="b24d3-135">The `match!` keyword enhances pattern matching when inside a computation expression:</span></span>

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

<span data-ttu-id="b24d3-136">Cela vous permet de raccourcir le code qui implique souvent le mélange d’options (ou d’autres types) avec des expressions de calcul telles que l’async.</span><span class="sxs-lookup"><span data-stu-id="b24d3-136">This allows you to shorten code that often involves mixing options (or other types) with computation expressions such as async.</span></span> <span data-ttu-id="b24d3-137">Pour en savoir plus, voir [match!](../language-reference/computation-expressions.md#match).</span><span class="sxs-lookup"><span data-stu-id="b24d3-137">To learn more, see [match!](../language-reference/computation-expressions.md#match).</span></span>

## <a name="relaxed-upcasting-requirements-in-array-list-and-sequence-expressions"></a><span data-ttu-id="b24d3-138">Exigences de diffusion assouplies dans les expressions de tableau, de liste et de séquence</span><span class="sxs-lookup"><span data-stu-id="b24d3-138">Relaxed upcasting requirements in array, list, and sequence expressions</span></span>

<span data-ttu-id="b24d3-139">Les types de mélange où l’on peut hériter d’un autre à l’intérieur `:>` `upcast`de la gamme, la liste, et les expressions de séquence vous a traditionnellement exigé de upcast tout type dérivé à son type parent avec ou .</span><span class="sxs-lookup"><span data-stu-id="b24d3-139">Mixing types where one may inherit from another inside of array, list, and sequence expressions has traditionally required you to upcast any derived type to its parent type with `:>` or `upcast`.</span></span> <span data-ttu-id="b24d3-140">Ceci est maintenant détendu, démontré comme suit:</span><span class="sxs-lookup"><span data-stu-id="b24d3-140">This is now relaxed, demonstrated as follows:</span></span>

```fsharp
let x0 : obj list  = [ "a" ] // ok pre-F# 4.5
let x1 : obj list  = [ "a"; "b" ] // ok pre-F# 4.5
let x2 : obj list  = [ yield "a" :> obj ] // ok pre-F# 4.5

let x3 : obj list  = [ yield "a" ] // Now ok for F# 4.5, and can replace x2
```

## <a name="indentation-relaxation-for-array-and-list-expressions"></a><span data-ttu-id="b24d3-141">Relaxation d’indentation pour les expressions de tableau et de liste</span><span class="sxs-lookup"><span data-stu-id="b24d3-141">Indentation relaxation for array and list expressions</span></span>

<span data-ttu-id="b24d3-142">Avant F 4.5, vous aviez besoin de tableau excessivement en retrait et d’énumérer les expressions lorsqu’ils sont adoptés comme arguments aux appels de méthode.</span><span class="sxs-lookup"><span data-stu-id="b24d3-142">Prior to F# 4.5, you needed to excessively indent array and list expressions when passed as arguments to method calls.</span></span> <span data-ttu-id="b24d3-143">Ce n’est plus nécessaire :</span><span class="sxs-lookup"><span data-stu-id="b24d3-143">This is no longer required:</span></span>

```fsharp
module NoExcessiveIndenting =
    System.Console.WriteLine(format="{0}", arg = [|
        "hello"
    |])
    System.Console.WriteLine([|
        "hello"
    |])
```
