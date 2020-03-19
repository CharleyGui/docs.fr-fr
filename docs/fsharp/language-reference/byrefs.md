---
title: Byrefs
description: Renseignez-vous sur les types byref et byref-like dans F, qui sont utilisés pour la programmation de bas niveau.
ms.date: 11/04/2019
ms.openlocfilehash: 527f465ee87fe153a2deae1306b6730531dc4123
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187052"
---
# <a name="byrefs"></a><span data-ttu-id="7e5dc-103">Byrefs</span><span class="sxs-lookup"><span data-stu-id="7e5dc-103">Byrefs</span></span>

<span data-ttu-id="7e5dc-104">FMD dispose de deux domaines d’envergure majeurs qui traitent dans l’espace de la programmation de bas niveau :</span><span class="sxs-lookup"><span data-stu-id="7e5dc-104">F# has two major feature areas that deal in the space of low-level programming:</span></span>

* <span data-ttu-id="7e5dc-105">`byref` / Les `inref` / types, qui sont des pointeurs `outref` gérés.</span><span class="sxs-lookup"><span data-stu-id="7e5dc-105">The `byref`/`inref`/`outref` types, which are managed pointers.</span></span> <span data-ttu-id="7e5dc-106">Ils ont des restrictions sur l’utilisation de sorte que vous ne pouvez pas compiler un programme qui est invalide au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="7e5dc-106">They have restrictions on usage so that you cannot compile a program that is invalid at run time.</span></span>
* <span data-ttu-id="7e5dc-107">Une `byref`struct-like, qui est une [structure](structures.md) qui a la sémantique `byref<'T>`similaire et les mêmes restrictions de temps de compilation que .</span><span class="sxs-lookup"><span data-stu-id="7e5dc-107">A `byref`-like struct, which is a [structure](structures.md) that has similar semantics and the same compile-time restrictions as `byref<'T>`.</span></span> <span data-ttu-id="7e5dc-108">Un exemple <xref:System.Span%601>est .</span><span class="sxs-lookup"><span data-stu-id="7e5dc-108">One example is <xref:System.Span%601>.</span></span>

## <a name="syntax"></a><span data-ttu-id="7e5dc-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7e5dc-109">Syntax</span></span>

```fsharp
// Byref types as parameters
let f (x: byref<'T>) = ()
let g (x: inref<'T>) = ()
let h (x: outref<'T>) = ()

// Calling a function with a byref parameter
let mutable x = 3
f &x

// Declaring a byref-like struct
open System.Runtime.CompilerServices

[<Struct; IsByRefLike>]
type S(count1: int, count2: int) =
    member x.Count1 = count1
    member x.Count2 = count2
```

## <a name="byref-inref-and-outref"></a><span data-ttu-id="7e5dc-110">Byref, inref, et outref</span><span class="sxs-lookup"><span data-stu-id="7e5dc-110">Byref, inref, and outref</span></span>

<span data-ttu-id="7e5dc-111">Il existe trois `byref`formes de :</span><span class="sxs-lookup"><span data-stu-id="7e5dc-111">There are three forms of `byref`:</span></span>

* <span data-ttu-id="7e5dc-112">`inref<'T>`, un pointeur géré pour lire la valeur sous-jacente.</span><span class="sxs-lookup"><span data-stu-id="7e5dc-112">`inref<'T>`, a managed pointer for reading the underlying value.</span></span>
* <span data-ttu-id="7e5dc-113">`outref<'T>`, un pointeur géré pour écrire à la valeur sous-jacente.</span><span class="sxs-lookup"><span data-stu-id="7e5dc-113">`outref<'T>`, a managed pointer for writing to the underlying value.</span></span>
* <span data-ttu-id="7e5dc-114">`byref<'T>`, un pointeur géré pour lire et écrire la valeur sous-jacente.</span><span class="sxs-lookup"><span data-stu-id="7e5dc-114">`byref<'T>`, a managed pointer for reading and writing the underlying value.</span></span>

<span data-ttu-id="7e5dc-115">A `byref<'T>` peut être `inref<'T>` passé là où on s’attend à un.</span><span class="sxs-lookup"><span data-stu-id="7e5dc-115">A `byref<'T>` can be passed where an `inref<'T>` is expected.</span></span> <span data-ttu-id="7e5dc-116">De même, un `byref<'T>` peut `outref<'T>` être passé là où on s’attend à un.</span><span class="sxs-lookup"><span data-stu-id="7e5dc-116">Similarly, a `byref<'T>` can be passed where an `outref<'T>` is expected.</span></span>

## <a name="using-byrefs"></a><span data-ttu-id="7e5dc-117">Utilisation de byrefs</span><span class="sxs-lookup"><span data-stu-id="7e5dc-117">Using byrefs</span></span>

<span data-ttu-id="7e5dc-118">Pour utiliser `inref<'T>`un , vous devez `&`obtenir une valeur pointeur avec :</span><span class="sxs-lookup"><span data-stu-id="7e5dc-118">To use a `inref<'T>`, you need to get a pointer value with `&`:</span></span>

```fsharp
open System

let f (dt: inref<DateTime>) =
    printfn "Now: %s" (dt.ToString())

let usage =
    let dt = DateTime.Now
    f &dt // Pass a pointer to 'dt'
```

<span data-ttu-id="7e5dc-119">Pour écrire au pointeur `outref<'T>` `byref<'T>`en utilisant un ou , vous `mutable`devez également faire la valeur que vous prenez un pointeur à .</span><span class="sxs-lookup"><span data-stu-id="7e5dc-119">To write to the pointer by using an `outref<'T>` or `byref<'T>`, you must also make the value you grab a pointer to `mutable`.</span></span>

```fsharp
open System

let f (dt: byref<DateTime>) =
    printfn "Now: %s" (dt.ToString())
    dt <- DateTime.Now

// Make 'dt' mutable
let mutable dt = DateTime.Now

// Now you can pass the pointer to 'dt'
f &dt
```

<span data-ttu-id="7e5dc-120">Si vous n’écrivez que le pointeur au lieu de le lire, envisager d’utiliser `outref<'T>` au lieu de `byref<'T>`.</span><span class="sxs-lookup"><span data-stu-id="7e5dc-120">If you are only writing the pointer instead of reading it, consider using `outref<'T>` instead of `byref<'T>`.</span></span>

### <a name="inref-semantics"></a><span data-ttu-id="7e5dc-121">Sémantique inref</span><span class="sxs-lookup"><span data-stu-id="7e5dc-121">Inref semantics</span></span>

<span data-ttu-id="7e5dc-122">Examinons le code ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="7e5dc-122">Consider the following code:</span></span>

```fsharp
let f (x: inref<SomeStruct>) = x.SomeField
```

<span data-ttu-id="7e5dc-123">Semantically, cela signifie ce qui suit:</span><span class="sxs-lookup"><span data-stu-id="7e5dc-123">Semantically, this means the following:</span></span>

* <span data-ttu-id="7e5dc-124">Le titulaire `x` du pointeur ne peut l’utiliser que pour lire la valeur.</span><span class="sxs-lookup"><span data-stu-id="7e5dc-124">The holder of the `x` pointer may only use it to read the value.</span></span>
* <span data-ttu-id="7e5dc-125">Tout pointeur `struct` acquis aux `SomeStruct` champs imbriqués à l’intérieur sont donnés type `inref<_>`.</span><span class="sxs-lookup"><span data-stu-id="7e5dc-125">Any pointer acquired to `struct` fields nested within `SomeStruct` are given type `inref<_>`.</span></span>

<span data-ttu-id="7e5dc-126">Ce qui suit est également vrai:</span><span class="sxs-lookup"><span data-stu-id="7e5dc-126">The following is also true:</span></span>

* <span data-ttu-id="7e5dc-127">Il n’y a aucune implication que d’autres `x`fils ou alias n’ont pas l’accès d’écriture à .</span><span class="sxs-lookup"><span data-stu-id="7e5dc-127">There is no implication that other threads or aliases do not have write access to `x`.</span></span>
* <span data-ttu-id="7e5dc-128">Il n’y `SomeStruct` a aucune implication `x` qui `inref`est immuable en vertu d’être un .</span><span class="sxs-lookup"><span data-stu-id="7e5dc-128">There is no implication that `SomeStruct` is immutable by virtue of `x` being an `inref`.</span></span>

<span data-ttu-id="7e5dc-129">Cependant, pour les types **are** de valeur F `this` ' qui sont immuables, le pointeur est déduit d’être un `inref`.</span><span class="sxs-lookup"><span data-stu-id="7e5dc-129">However, for F# value types that **are** immutable, the `this` pointer is inferred to be an `inref`.</span></span>

<span data-ttu-id="7e5dc-130">Toutes ces règles ensemble signifient `inref` que le titulaire d’un pointeur ne peut pas modifier le contenu immédiat de la mémoire pointée vers.</span><span class="sxs-lookup"><span data-stu-id="7e5dc-130">All of these rules together mean that the holder of an `inref` pointer may not modify the immediate contents of the memory being pointed to.</span></span>

### <a name="outref-semantics"></a><span data-ttu-id="7e5dc-131">Sémantique Outref</span><span class="sxs-lookup"><span data-stu-id="7e5dc-131">Outref semantics</span></span>

<span data-ttu-id="7e5dc-132">Le but `outref<'T>` est d’indiquer que le pointeur ne doit être écrit à.</span><span class="sxs-lookup"><span data-stu-id="7e5dc-132">The purpose of `outref<'T>` is to indicate that the pointer should only be written to.</span></span> <span data-ttu-id="7e5dc-133">De façon `outref<'T>` inattendue, permet de lire la valeur sous-jacente malgré son nom.</span><span class="sxs-lookup"><span data-stu-id="7e5dc-133">Unexpectedly, `outref<'T>` permits reading the underlying value despite its name.</span></span> <span data-ttu-id="7e5dc-134">C’est à des fins de compatibilité.</span><span class="sxs-lookup"><span data-stu-id="7e5dc-134">This is for compatibility purposes.</span></span> <span data-ttu-id="7e5dc-135">Semantically, `outref<'T>` n’est `byref<'T>`pas différent de .</span><span class="sxs-lookup"><span data-stu-id="7e5dc-135">Semantically, `outref<'T>` is no different than `byref<'T>`.</span></span>

### <a name="interop-with-c"></a><span data-ttu-id="7e5dc-136">Interop avec C\#</span><span class="sxs-lookup"><span data-stu-id="7e5dc-136">Interop with C\#</span></span>

<span data-ttu-id="7e5dc-137">CMD prend `in ref` `out ref` en charge les `ref` mots clés et les mots clés, en plus des retours.</span><span class="sxs-lookup"><span data-stu-id="7e5dc-137">C# supports the `in ref` and `out ref` keywords, in addition to `ref` returns.</span></span> <span data-ttu-id="7e5dc-138">Le tableau suivant montre comment le FMD interprète ce que le CMD émet :</span><span class="sxs-lookup"><span data-stu-id="7e5dc-138">The following table shows how F# interprets what C# emits:</span></span>

|<span data-ttu-id="7e5dc-139">Construction de C</span><span class="sxs-lookup"><span data-stu-id="7e5dc-139">C# construct</span></span>|<span data-ttu-id="7e5dc-140">Infère les infères</span><span class="sxs-lookup"><span data-stu-id="7e5dc-140">F# infers</span></span>|
|------------|---------|
|<span data-ttu-id="7e5dc-141">`ref`valeur de retour</span><span class="sxs-lookup"><span data-stu-id="7e5dc-141">`ref` return value</span></span>|`outref<'T>`|
|<span data-ttu-id="7e5dc-142">`ref readonly`valeur de retour</span><span class="sxs-lookup"><span data-stu-id="7e5dc-142">`ref readonly` return value</span></span>|`inref<'T>`|
|<span data-ttu-id="7e5dc-143">Paramètre `in ref`</span><span class="sxs-lookup"><span data-stu-id="7e5dc-143">`in ref` parameter</span></span>|`inref<'T>`|
|<span data-ttu-id="7e5dc-144">Paramètre `out ref`</span><span class="sxs-lookup"><span data-stu-id="7e5dc-144">`out ref` parameter</span></span>|`outref<'T>`|

<span data-ttu-id="7e5dc-145">Le tableau suivant montre ce que le FMD émet :</span><span class="sxs-lookup"><span data-stu-id="7e5dc-145">The following table shows what F# emits:</span></span>

|<span data-ttu-id="7e5dc-146">Construction de F</span><span class="sxs-lookup"><span data-stu-id="7e5dc-146">F# construct</span></span>|<span data-ttu-id="7e5dc-147">Construction émise</span><span class="sxs-lookup"><span data-stu-id="7e5dc-147">Emitted construct</span></span>|
|------------|-----------------|
|<span data-ttu-id="7e5dc-148">Argument `inref<'T>`</span><span class="sxs-lookup"><span data-stu-id="7e5dc-148">`inref<'T>` argument</span></span>|<span data-ttu-id="7e5dc-149">`[In]`attribut sur l’argumentation</span><span class="sxs-lookup"><span data-stu-id="7e5dc-149">`[In]` attribute on argument</span></span>|
|<span data-ttu-id="7e5dc-150">`inref<'T>`Retour</span><span class="sxs-lookup"><span data-stu-id="7e5dc-150">`inref<'T>` return</span></span>|<span data-ttu-id="7e5dc-151">`modreq`attribut sur la valeur</span><span class="sxs-lookup"><span data-stu-id="7e5dc-151">`modreq` attribute on value</span></span>|
|<span data-ttu-id="7e5dc-152">`inref<'T>`dans la fente abstraite ou la mise en œuvre</span><span class="sxs-lookup"><span data-stu-id="7e5dc-152">`inref<'T>` in abstract slot or implementation</span></span>|<span data-ttu-id="7e5dc-153">`modreq`sur l’argumentation ou le retour</span><span class="sxs-lookup"><span data-stu-id="7e5dc-153">`modreq` on argument or return</span></span>|
|<span data-ttu-id="7e5dc-154">Argument `outref<'T>`</span><span class="sxs-lookup"><span data-stu-id="7e5dc-154">`outref<'T>` argument</span></span>|<span data-ttu-id="7e5dc-155">`[Out]`attribut sur l’argumentation</span><span class="sxs-lookup"><span data-stu-id="7e5dc-155">`[Out]` attribute on argument</span></span>|

### <a name="type-inference-and-overloading-rules"></a><span data-ttu-id="7e5dc-156">Règles d’inférence et de surcharge de type</span><span class="sxs-lookup"><span data-stu-id="7e5dc-156">Type inference and overloading rules</span></span>

<span data-ttu-id="7e5dc-157">Un `inref<'T>` type est déduit par le compilateur F dans les cas suivants :</span><span class="sxs-lookup"><span data-stu-id="7e5dc-157">An `inref<'T>` type is inferred by the F# compiler in the following cases:</span></span>

1. <span data-ttu-id="7e5dc-158">Un paramètre .NET ou `IsReadOnly` un type de retour qui a un attribut.</span><span class="sxs-lookup"><span data-stu-id="7e5dc-158">A .NET parameter or return type that has an `IsReadOnly` attribute.</span></span>
2. <span data-ttu-id="7e5dc-159">Le `this` pointeur sur un type de struct qui n’a pas de champs mutables.</span><span class="sxs-lookup"><span data-stu-id="7e5dc-159">The `this` pointer on a struct type that has no mutable fields.</span></span>
3. <span data-ttu-id="7e5dc-160">L’adresse d’un emplacement `inref<_>` de mémoire dérivé d’un autre pointeur.</span><span class="sxs-lookup"><span data-stu-id="7e5dc-160">The address of a memory location derived from another `inref<_>` pointer.</span></span>

<span data-ttu-id="7e5dc-161">Lorsqu’une adresse `inref` implicite d’un est prise, une `SomeType` surcharge avec un argument de `inref<SomeType>`type est préférable à une surcharge avec un argument de type .</span><span class="sxs-lookup"><span data-stu-id="7e5dc-161">When an implicit address of an `inref` is being taken, an overload with an argument of type `SomeType` is preferred to an overload with an argument of type `inref<SomeType>`.</span></span> <span data-ttu-id="7e5dc-162">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="7e5dc-162">For example:</span></span>

```fsharp
type C() =
    static member M(x: System.DateTime) = x.AddDays(1.0)
    static member M(x: inref<System.DateTime>) = x.AddDays(2.0)
    static member M2(x: System.DateTime, y: int) = x.AddDays(1.0)
    static member M2(x: inref<System.DateTime>, y: int) = x.AddDays(2.0)

let res = System.DateTime.Now
let v =  C.M(res)
let v2 =  C.M2(res, 4)
```

<span data-ttu-id="7e5dc-163">Dans les deux cas, `System.DateTime` les surcharges de prise `inref<System.DateTime>`sont résolues plutôt que les surcharges prenant .</span><span class="sxs-lookup"><span data-stu-id="7e5dc-163">In both cases, the overloads taking `System.DateTime` are resolved rather than the overloads taking `inref<System.DateTime>`.</span></span>

## <a name="byref-like-structs"></a><span data-ttu-id="7e5dc-164">Les structs de byref</span><span class="sxs-lookup"><span data-stu-id="7e5dc-164">Byref-like structs</span></span>

<span data-ttu-id="7e5dc-165">En plus `byref` / `inref` / `outref` du trio, vous pouvez définir vos propres `byref`structs qui peuvent adhérer à -comme la sémantique.</span><span class="sxs-lookup"><span data-stu-id="7e5dc-165">In addition to the `byref`/`inref`/`outref` trio, you can define your own structs that can adhere to `byref`-like semantics.</span></span> <span data-ttu-id="7e5dc-166">Ceci est fait <xref:System.Runtime.CompilerServices.IsByRefLikeAttribute> avec l’attribut:</span><span class="sxs-lookup"><span data-stu-id="7e5dc-166">This is done with the <xref:System.Runtime.CompilerServices.IsByRefLikeAttribute> attribute:</span></span>

```fsharp
open System
open System.Runtime.CompilerServices

[<IsByRefLike; Struct>]
type S(count1: Span<int>, count2: Span<int>) =
    member x.Count1 = count1
    member x.Count2 = count2
```

<span data-ttu-id="7e5dc-167">`IsByRefLike`n’implique `Struct`pas .</span><span class="sxs-lookup"><span data-stu-id="7e5dc-167">`IsByRefLike` does not imply `Struct`.</span></span> <span data-ttu-id="7e5dc-168">Les deux doivent être présents sur le type.</span><span class="sxs-lookup"><span data-stu-id="7e5dc-168">Both must be present on the type.</span></span>

<span data-ttu-id="7e5dc-169">Une`byref`struction «-comme » dans le F est un type de valeur lié à la pile.</span><span class="sxs-lookup"><span data-stu-id="7e5dc-169">A "`byref`-like" struct in F# is a stack-bound value type.</span></span> <span data-ttu-id="7e5dc-170">Il n’est jamais alloué sur le tas géré.</span><span class="sxs-lookup"><span data-stu-id="7e5dc-170">It is never allocated on the managed heap.</span></span> <span data-ttu-id="7e5dc-171">Une `byref`structure comme est utile pour la programmation haute performance, car elle est appliquée avec un ensemble de contrôles forts sur la durée de vie et la non-capture.</span><span class="sxs-lookup"><span data-stu-id="7e5dc-171">A `byref`-like struct is useful for high-performance programming, as it is enforced with set of strong checks about lifetime and non-capture.</span></span> <span data-ttu-id="7e5dc-172">Les règles sont les suivante :</span><span class="sxs-lookup"><span data-stu-id="7e5dc-172">The rules are:</span></span>

* <span data-ttu-id="7e5dc-173">Ils peuvent être utilisés comme paramètres de fonction, paramètres de méthode, variables locales, retours de méthode.</span><span class="sxs-lookup"><span data-stu-id="7e5dc-173">They can be used as function parameters, method parameters, local variables, method returns.</span></span>
* <span data-ttu-id="7e5dc-174">Ils ne peuvent pas être statiques ou des membres d’instance d’une classe ou d’une struct normale.</span><span class="sxs-lookup"><span data-stu-id="7e5dc-174">They cannot be static or instance members of a class or normal struct.</span></span>
* <span data-ttu-id="7e5dc-175">Ils ne peuvent pas être`async` capturés par une construction de fermeture (méthodes ou expressions lambda).</span><span class="sxs-lookup"><span data-stu-id="7e5dc-175">They cannot be captured by any closure construct (`async` methods or lambda expressions).</span></span>
* <span data-ttu-id="7e5dc-176">Ils ne peuvent pas être utilisés comme paramètre générique.</span><span class="sxs-lookup"><span data-stu-id="7e5dc-176">They cannot be used as a generic parameter.</span></span>

<span data-ttu-id="7e5dc-177">Ce dernier point est crucial pour la `|>` programmation de type pipeline F, tout comme une fonction générique qui paramélise ses types d’entrées.</span><span class="sxs-lookup"><span data-stu-id="7e5dc-177">This last point is crucial for F# pipeline-style programming, as `|>` is a generic function that parameterizes its input types.</span></span> <span data-ttu-id="7e5dc-178">Cette restriction peut `|>` être assouplie pour l’avenir, car elle est en ligne et ne fait pas d’appels à des fonctions génériques non-inlined dans son corps.</span><span class="sxs-lookup"><span data-stu-id="7e5dc-178">This restriction may be relaxed for `|>` in the future, as it is inline and does not make any calls to non-inlined generic functions in its body.</span></span>

<span data-ttu-id="7e5dc-179">Bien que ces règles restreignent fortement l’utilisation, elles le font pour remplir la promesse d’informatique de haute performance d’une manière sûre.</span><span class="sxs-lookup"><span data-stu-id="7e5dc-179">Although these rules strongly restrict usage, they do so to fulfill the promise of high-performance computing in a safe manner.</span></span>

## <a name="byref-returns"></a><span data-ttu-id="7e5dc-180">Byref revient</span><span class="sxs-lookup"><span data-stu-id="7e5dc-180">Byref returns</span></span>

<span data-ttu-id="7e5dc-181">Les retours byref des fonctions de F ou des membres peuvent être produits et consommés.</span><span class="sxs-lookup"><span data-stu-id="7e5dc-181">Byref returns from F# functions or members can be produced and consumed.</span></span> <span data-ttu-id="7e5dc-182">Lors de `byref`la consommation d’une méthode de retour, la valeur est implicitement déreférée.</span><span class="sxs-lookup"><span data-stu-id="7e5dc-182">When consuming a `byref`-returning method, the value is implicitly dereferenced.</span></span> <span data-ttu-id="7e5dc-183">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="7e5dc-183">For example:</span></span>

```fsharp
let squareAndPrint (data : byref<int>) =
    let squared = data*data    // data is implicitly dereferenced
    printfn "%d" squared
```

<span data-ttu-id="7e5dc-184">Pour retourner une valeur byref, la variable qui contient la valeur doit vivre plus longtemps que la portée actuelle.</span><span class="sxs-lookup"><span data-stu-id="7e5dc-184">To return a value byref, the variable that contains the value must live longer than the current scope.</span></span>
<span data-ttu-id="7e5dc-185">En outre, pour revenir `&value` byref, l’utilisation (où la valeur est une variable qui vit plus longtemps que la portée actuelle).</span><span class="sxs-lookup"><span data-stu-id="7e5dc-185">Also, to return byref, use `&value` (where value is a variable that lives longer than the current scope).</span></span>

```fsharp
let mutable sum = 0
let safeSum (bytes: Span<byte>) =
    for i in 0 .. bytes.Length - 1 do
        sum <- sum + int bytes.[i]
    &sum  // sum lives longer than the scope of this function.
```

<span data-ttu-id="7e5dc-186">Pour éviter la déreférence implicite, comme passer une référence `&x` par `x` plusieurs appels enchaînés, utilisez (où est la valeur).</span><span class="sxs-lookup"><span data-stu-id="7e5dc-186">To avoid the implicit dereference, such as passing a reference through multiple chained calls, use `&x` (where `x` is the value).</span></span>

<span data-ttu-id="7e5dc-187">Vous pouvez également attribuer `byref`directement à un retour .</span><span class="sxs-lookup"><span data-stu-id="7e5dc-187">You can also directly assign to a return `byref`.</span></span> <span data-ttu-id="7e5dc-188">Considérez le programme suivant (hautement impératif) :</span><span class="sxs-lookup"><span data-stu-id="7e5dc-188">Consider the following (highly imperative) program:</span></span>

```fsharp
type C() =
    let mutable nums = [| 1; 3; 7; 15; 31; 63; 127; 255; 511; 1023 |]

    override _.ToString() = String.Join(' ', nums)

    member _.FindLargestSmallerThan(target: int) =
        let mutable ctr = nums.Length - 1

        while ctr > 0 && nums.[ctr] >= target do ctr <- ctr - 1

        if ctr > 0 then &nums.[ctr] else &nums.[0]

[<EntryPoint>]
let main argv =
    let c = C()
    printfn "Original sequence: %s" (c.ToString())

    let v = &c.FindLargestSmallerThan 16

    v <- v*2 // Directly assign to the byref return

    printfn "New sequence:      %s" (c.ToString())

    0 // return an integer exit code
```

<span data-ttu-id="7e5dc-189">Il s'agit de la sortie :</span><span class="sxs-lookup"><span data-stu-id="7e5dc-189">This is the output:</span></span>

```console
Original sequence: 1 3 7 15 31 63 127 255 511 1023
New sequence:      1 3 7 30 31 63 127 255 511 1023
```

## <a name="scoping-for-byrefs"></a><span data-ttu-id="7e5dc-190">Scoping for byrefs</span><span class="sxs-lookup"><span data-stu-id="7e5dc-190">Scoping for byrefs</span></span>

<span data-ttu-id="7e5dc-191">Une `let`valeur liée ne peut pas avoir sa référence supérieure à la portée dans laquelle elle a été définie.</span><span class="sxs-lookup"><span data-stu-id="7e5dc-191">A `let`-bound value cannot have its reference exceed the scope in which it was defined.</span></span> <span data-ttu-id="7e5dc-192">Par exemple, ce qui suit est refusé :</span><span class="sxs-lookup"><span data-stu-id="7e5dc-192">For example, the following is disallowed:</span></span>

```fsharp
let test2 () =
    let x = 12
    &x // Error: 'x' exceeds its defined scope!

let test () =
    let x =
        let y = 1
        &y // Error: `y` exceeds its defined scope!
    ()
```

<span data-ttu-id="7e5dc-193">Cela vous empêche d’obtenir des résultats différents en fonction de si vous compilez avec des optimisations ou non.</span><span class="sxs-lookup"><span data-stu-id="7e5dc-193">This prevents you from getting different results depending on if you compile with optimizations or not.</span></span>
