---
title: Byrefs
description: En savoir plus sur les types ByRef et de F#type ByRef dans, qui sont utilisés pour la programmation de bas niveau.
ms.date: 11/04/2019
ms.openlocfilehash: 2d98d325dc4ad26548fb2cc6aa5b872e152ee0a8
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2020
ms.locfileid: "77092786"
---
# <a name="byrefs"></a><span data-ttu-id="e60b9-103">Byrefs</span><span class="sxs-lookup"><span data-stu-id="e60b9-103">Byrefs</span></span>

<span data-ttu-id="e60b9-104">F#a deux domaines de fonctionnalités majeurs qui traitent de l’espace de la programmation de bas niveau :</span><span class="sxs-lookup"><span data-stu-id="e60b9-104">F# has two major feature areas that deal in the space of low-level programming:</span></span>

* <span data-ttu-id="e60b9-105">Les `byref`/`inref`/types de `outref`, qui sont des pointeurs managés.</span><span class="sxs-lookup"><span data-stu-id="e60b9-105">The `byref`/`inref`/`outref` types, which are managed pointers.</span></span> <span data-ttu-id="e60b9-106">Ils ont des restrictions sur l’utilisation afin que vous ne soyez pas en mesure de compiler un programme qui n’est pas valide au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="e60b9-106">They have restrictions on usage so that you cannot compile a program that is invalid at run time.</span></span>
* <span data-ttu-id="e60b9-107">Struct de type `byref`, qui est une [structure](structures.md) qui a une sémantique similaire et les mêmes restrictions au moment de la compilation que `byref<'T>`.</span><span class="sxs-lookup"><span data-stu-id="e60b9-107">A `byref`-like struct, which is a [structure](structures.md) that has similar semantics and the same compile-time restrictions as `byref<'T>`.</span></span> <span data-ttu-id="e60b9-108">Par exemple, <xref:System.Span%601>.</span><span class="sxs-lookup"><span data-stu-id="e60b9-108">One example is <xref:System.Span%601>.</span></span>

## <a name="syntax"></a><span data-ttu-id="e60b9-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e60b9-109">Syntax</span></span>

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

## <a name="byref-inref-and-outref"></a><span data-ttu-id="e60b9-110">ByRef, inref et outref</span><span class="sxs-lookup"><span data-stu-id="e60b9-110">Byref, inref, and outref</span></span>

<span data-ttu-id="e60b9-111">Il existe trois formes de `byref`:</span><span class="sxs-lookup"><span data-stu-id="e60b9-111">There are three forms of `byref`:</span></span>

* <span data-ttu-id="e60b9-112">`inref<'T>`, pointeur managé pour la lecture de la valeur sous-jacente.</span><span class="sxs-lookup"><span data-stu-id="e60b9-112">`inref<'T>`, a managed pointer for reading the underlying value.</span></span>
* <span data-ttu-id="e60b9-113">`outref<'T>`, pointeur managé pour l’écriture dans la valeur sous-jacente.</span><span class="sxs-lookup"><span data-stu-id="e60b9-113">`outref<'T>`, a managed pointer for writing to the underlying value.</span></span>
* <span data-ttu-id="e60b9-114">`byref<'T>`, pointeur managé pour la lecture et l’écriture de la valeur sous-jacente.</span><span class="sxs-lookup"><span data-stu-id="e60b9-114">`byref<'T>`, a managed pointer for reading and writing the underlying value.</span></span>

<span data-ttu-id="e60b9-115">Un `byref<'T>` peut être passé là où un `inref<'T>` est attendu.</span><span class="sxs-lookup"><span data-stu-id="e60b9-115">A `byref<'T>` can be passed where an `inref<'T>` is expected.</span></span> <span data-ttu-id="e60b9-116">De même, un `byref<'T>` peut être passé là où un `outref<'T>` est attendu.</span><span class="sxs-lookup"><span data-stu-id="e60b9-116">Similarly, a `byref<'T>` can be passed where an `outref<'T>` is expected.</span></span>

## <a name="using-byrefs"></a><span data-ttu-id="e60b9-117">Utilisation de types ByRef</span><span class="sxs-lookup"><span data-stu-id="e60b9-117">Using byrefs</span></span>

<span data-ttu-id="e60b9-118">Pour utiliser un `inref<'T>`, vous devez obtenir une valeur de pointeur avec `&`:</span><span class="sxs-lookup"><span data-stu-id="e60b9-118">To use a `inref<'T>`, you need to get a pointer value with `&`:</span></span>

```fsharp
open System

let f (dt: inref<DateTime>) =
    printfn "Now: %s" (dt.ToString())

let usage =
    let dt = DateTime.Now
    f &dt // Pass a pointer to 'dt'
```

<span data-ttu-id="e60b9-119">Pour écrire dans le pointeur à l’aide d’une `outref<'T>` ou d’un `byref<'T>`, vous devez également faire de la valeur que vous saisissez un pointeur vers `mutable`.</span><span class="sxs-lookup"><span data-stu-id="e60b9-119">To write to the pointer by using an `outref<'T>` or `byref<'T>`, you must also make the value you grab a pointer to `mutable`.</span></span>

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

<span data-ttu-id="e60b9-120">Si vous écrivez uniquement le pointeur au lieu de le lire, envisagez d’utiliser `outref<'T>` au lieu de `byref<'T>`.</span><span class="sxs-lookup"><span data-stu-id="e60b9-120">If you are only writing the pointer instead of reading it, consider using `outref<'T>` instead of `byref<'T>`.</span></span>

### <a name="inref-semantics"></a><span data-ttu-id="e60b9-121">Sémantique Inref</span><span class="sxs-lookup"><span data-stu-id="e60b9-121">Inref semantics</span></span>

<span data-ttu-id="e60b9-122">Examinons le code ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="e60b9-122">Consider the following code:</span></span>

```fsharp
let f (x: inref<SomeStruct>) = x.SomeField
```

<span data-ttu-id="e60b9-123">Sémantiquement, cela signifie ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="e60b9-123">Semantically, this means the following:</span></span>

* <span data-ttu-id="e60b9-124">Le détenteur du pointeur `x` ne peut l’utiliser que pour lire la valeur.</span><span class="sxs-lookup"><span data-stu-id="e60b9-124">The holder of the `x` pointer may only use it to read the value.</span></span>
* <span data-ttu-id="e60b9-125">Tout pointeur acquis pour `struct` champs imbriqués dans `SomeStruct` reçoit le `inref<_>`de type.</span><span class="sxs-lookup"><span data-stu-id="e60b9-125">Any pointer acquired to `struct` fields nested within `SomeStruct` are given type `inref<_>`.</span></span>

<span data-ttu-id="e60b9-126">Les éléments suivants sont également vrais :</span><span class="sxs-lookup"><span data-stu-id="e60b9-126">The following is also true:</span></span>

* <span data-ttu-id="e60b9-127">Il n’y a aucune implication que d’autres threads ou alias n’ont pas d’accès en écriture à `x`.</span><span class="sxs-lookup"><span data-stu-id="e60b9-127">There is no implication that other threads or aliases do not have write access to `x`.</span></span>
* <span data-ttu-id="e60b9-128">Il n’y a aucune implication que `SomeStruct` est immuable en raison de `x` en tant que `inref`.</span><span class="sxs-lookup"><span data-stu-id="e60b9-128">There is no implication that `SomeStruct` is immutable by virtue of `x` being an `inref`.</span></span>

<span data-ttu-id="e60b9-129">Toutefois, pour F# les **types de valeur** immuables, le pointeur `this` est déduit comme étant une `inref`.</span><span class="sxs-lookup"><span data-stu-id="e60b9-129">However, for F# value types that **are** immutable, the `this` pointer is inferred to be an `inref`.</span></span>

<span data-ttu-id="e60b9-130">Toutes ces règles signifient que le détenteur d’un pointeur de `inref` peut ne pas modifier le contenu immédiat de la mémoire vers laquelle pointe.</span><span class="sxs-lookup"><span data-stu-id="e60b9-130">All of these rules together mean that the holder of an `inref` pointer may not modify the immediate contents of the memory being pointed to.</span></span>

### <a name="outref-semantics"></a><span data-ttu-id="e60b9-131">Sémantique Outref</span><span class="sxs-lookup"><span data-stu-id="e60b9-131">Outref semantics</span></span>

<span data-ttu-id="e60b9-132">L’objectif de `outref<'T>` est d’indiquer que le pointeur doit uniquement être écrit dans.</span><span class="sxs-lookup"><span data-stu-id="e60b9-132">The purpose of `outref<'T>` is to indicate that the pointer should only be written to.</span></span> <span data-ttu-id="e60b9-133">De manière inattendue, `outref<'T>` permet de lire la valeur sous-jacente en dépit de son nom.</span><span class="sxs-lookup"><span data-stu-id="e60b9-133">Unexpectedly, `outref<'T>` permits reading the underlying value despite its name.</span></span> <span data-ttu-id="e60b9-134">À des fins de compatibilité.</span><span class="sxs-lookup"><span data-stu-id="e60b9-134">This is for compatibility purposes.</span></span> <span data-ttu-id="e60b9-135">Sémantiquement, `outref<'T>` n’est pas différent de `byref<'T>`.</span><span class="sxs-lookup"><span data-stu-id="e60b9-135">Semantically, `outref<'T>` is no different than `byref<'T>`.</span></span>

### <a name="interop-with-c"></a><span data-ttu-id="e60b9-136">Interopérabilité avec C\#</span><span class="sxs-lookup"><span data-stu-id="e60b9-136">Interop with C\#</span></span>

<span data-ttu-id="e60b9-137">C#prend en charge les mots clés `in ref` et `out ref`, en plus de `ref` retourne.</span><span class="sxs-lookup"><span data-stu-id="e60b9-137">C# supports the `in ref` and `out ref` keywords, in addition to `ref` returns.</span></span> <span data-ttu-id="e60b9-138">Le tableau suivant montre comment F# interprète les C# émissions :</span><span class="sxs-lookup"><span data-stu-id="e60b9-138">The following table shows how F# interprets what C# emits:</span></span>

|<span data-ttu-id="e60b9-139">C#composer</span><span class="sxs-lookup"><span data-stu-id="e60b9-139">C# construct</span></span>|<span data-ttu-id="e60b9-140">F#déduit</span><span class="sxs-lookup"><span data-stu-id="e60b9-140">F# infers</span></span>|
|------------|---------|
|<span data-ttu-id="e60b9-141">`ref` valeur de retour</span><span class="sxs-lookup"><span data-stu-id="e60b9-141">`ref` return value</span></span>|`outref<'T>`|
|<span data-ttu-id="e60b9-142">`ref readonly` valeur de retour</span><span class="sxs-lookup"><span data-stu-id="e60b9-142">`ref readonly` return value</span></span>|`inref<'T>`|
|<span data-ttu-id="e60b9-143">Paramètre `in ref`</span><span class="sxs-lookup"><span data-stu-id="e60b9-143">`in ref` parameter</span></span>|`inref<'T>`|
|<span data-ttu-id="e60b9-144">Paramètre `out ref`</span><span class="sxs-lookup"><span data-stu-id="e60b9-144">`out ref` parameter</span></span>|`outref<'T>`|

<span data-ttu-id="e60b9-145">Le tableau suivant répertorie F# les émissions :</span><span class="sxs-lookup"><span data-stu-id="e60b9-145">The following table shows what F# emits:</span></span>

|<span data-ttu-id="e60b9-146">F#composer</span><span class="sxs-lookup"><span data-stu-id="e60b9-146">F# construct</span></span>|<span data-ttu-id="e60b9-147">Construction émise</span><span class="sxs-lookup"><span data-stu-id="e60b9-147">Emitted construct</span></span>|
|------------|-----------------|
|<span data-ttu-id="e60b9-148">Argument `inref<'T>`</span><span class="sxs-lookup"><span data-stu-id="e60b9-148">`inref<'T>` argument</span></span>|<span data-ttu-id="e60b9-149">attribut `[In]` sur l’argument</span><span class="sxs-lookup"><span data-stu-id="e60b9-149">`[In]` attribute on argument</span></span>|
|<span data-ttu-id="e60b9-150">`inref<'T>` retourner</span><span class="sxs-lookup"><span data-stu-id="e60b9-150">`inref<'T>` return</span></span>|<span data-ttu-id="e60b9-151">`modreq` attribut sur la valeur</span><span class="sxs-lookup"><span data-stu-id="e60b9-151">`modreq` attribute on value</span></span>|
|<span data-ttu-id="e60b9-152">`inref<'T>` dans l’emplacement ou l’implémentation abstraits</span><span class="sxs-lookup"><span data-stu-id="e60b9-152">`inref<'T>` in abstract slot or implementation</span></span>|<span data-ttu-id="e60b9-153">`modreq` de l’argument ou du retour</span><span class="sxs-lookup"><span data-stu-id="e60b9-153">`modreq` on argument or return</span></span>|
|<span data-ttu-id="e60b9-154">Argument `outref<'T>`</span><span class="sxs-lookup"><span data-stu-id="e60b9-154">`outref<'T>` argument</span></span>|<span data-ttu-id="e60b9-155">attribut `[Out]` sur l’argument</span><span class="sxs-lookup"><span data-stu-id="e60b9-155">`[Out]` attribute on argument</span></span>|

### <a name="type-inference-and-overloading-rules"></a><span data-ttu-id="e60b9-156">Inférence de type et règles de surcharge</span><span class="sxs-lookup"><span data-stu-id="e60b9-156">Type inference and overloading rules</span></span>

<span data-ttu-id="e60b9-157">Un type de `inref<'T>` est déduit par le F# compilateur dans les cas suivants :</span><span class="sxs-lookup"><span data-stu-id="e60b9-157">An `inref<'T>` type is inferred by the F# compiler in the following cases:</span></span>

1. <span data-ttu-id="e60b9-158">Un paramètre .NET ou un type de retour qui a un attribut `IsReadOnly`.</span><span class="sxs-lookup"><span data-stu-id="e60b9-158">A .NET parameter or return type that has an `IsReadOnly` attribute.</span></span>
2. <span data-ttu-id="e60b9-159">Pointeur `this` sur un type struct qui n’a aucun champ mutable.</span><span class="sxs-lookup"><span data-stu-id="e60b9-159">The `this` pointer on a struct type that has no mutable fields.</span></span>
3. <span data-ttu-id="e60b9-160">Adresse d’un emplacement de mémoire dérivé d’un autre pointeur de `inref<_>`.</span><span class="sxs-lookup"><span data-stu-id="e60b9-160">The address of a memory location derived from another `inref<_>` pointer.</span></span>

<span data-ttu-id="e60b9-161">Quand une adresse implicite d’un `inref` est prise, une surcharge avec un argument de type `SomeType` est préférable à une surcharge avec un argument de type `inref<SomeType>`.</span><span class="sxs-lookup"><span data-stu-id="e60b9-161">When an implicit address of an `inref` is being taken, an overload with an argument of type `SomeType` is preferred to an overload with an argument of type `inref<SomeType>`.</span></span> <span data-ttu-id="e60b9-162">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="e60b9-162">For example:</span></span>

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

<span data-ttu-id="e60b9-163">Dans les deux cas, les surcharges qui prennent `System.DateTime` sont résolues, au lieu des surcharges qui prennent `inref<System.DateTime>`.</span><span class="sxs-lookup"><span data-stu-id="e60b9-163">In both cases, the overloads taking `System.DateTime` are resolved rather than the overloads taking `inref<System.DateTime>`.</span></span>

## <a name="byref-like-structs"></a><span data-ttu-id="e60b9-164">Structs de type ByRef</span><span class="sxs-lookup"><span data-stu-id="e60b9-164">Byref-like structs</span></span>

<span data-ttu-id="e60b9-165">Outre les `byref`/`inref`/`outref` trio, vous pouvez définir vos propres structs qui peuvent adhérer à une sémantique de type `byref`.</span><span class="sxs-lookup"><span data-stu-id="e60b9-165">In addition to the `byref`/`inref`/`outref` trio, you can define your own structs that can adhere to `byref`-like semantics.</span></span> <span data-ttu-id="e60b9-166">Cette opération s’effectue avec l’attribut <xref:System.Runtime.CompilerServices.IsByRefLikeAttribute> :</span><span class="sxs-lookup"><span data-stu-id="e60b9-166">This is done with the <xref:System.Runtime.CompilerServices.IsByRefLikeAttribute> attribute:</span></span>

```fsharp
open System
open System.Runtime.CompilerServices

[<IsByRefLike; Struct>]
type S(count1: Span<int>, count2: Span<int>) =
    member x.Count1 = count1
    member x.Count2 = count2
```

<span data-ttu-id="e60b9-167">`IsByRefLike` n’implique pas `Struct`.</span><span class="sxs-lookup"><span data-stu-id="e60b9-167">`IsByRefLike` does not imply `Struct`.</span></span> <span data-ttu-id="e60b9-168">Les deux doivent être présents sur le type.</span><span class="sxs-lookup"><span data-stu-id="e60b9-168">Both must be present on the type.</span></span>

<span data-ttu-id="e60b9-169">Un struct «`byref`-like » dans F# est un type valeur lié à la pile.</span><span class="sxs-lookup"><span data-stu-id="e60b9-169">A "`byref`-like" struct in F# is a stack-bound value type.</span></span> <span data-ttu-id="e60b9-170">Elle n’est jamais allouée sur le tas managé.</span><span class="sxs-lookup"><span data-stu-id="e60b9-170">It is never allocated on the managed heap.</span></span> <span data-ttu-id="e60b9-171">Un struct de type `byref`est utile pour la programmation hautes performances, car il est appliqué avec un ensemble de vérifications fortes sur la durée de vie et la non-capture.</span><span class="sxs-lookup"><span data-stu-id="e60b9-171">A `byref`-like struct is useful for high-performance programming, as it is enforced with set of strong checks about lifetime and non-capture.</span></span> <span data-ttu-id="e60b9-172">Les règles sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="e60b9-172">The rules are:</span></span>

* <span data-ttu-id="e60b9-173">Elles peuvent être utilisées en tant que paramètres de fonction, paramètres de méthode, variables locales, retours de méthode.</span><span class="sxs-lookup"><span data-stu-id="e60b9-173">They can be used as function parameters, method parameters, local variables, method returns.</span></span>
* <span data-ttu-id="e60b9-174">Ils ne peuvent pas être des membres statiques ou d’instance d’une classe ou d’un struct normal.</span><span class="sxs-lookup"><span data-stu-id="e60b9-174">They cannot be static or instance members of a class or normal struct.</span></span>
* <span data-ttu-id="e60b9-175">Ils ne peuvent pas être capturés par une construction de fermeture (méthodes`async` ou expressions lambda).</span><span class="sxs-lookup"><span data-stu-id="e60b9-175">They cannot be captured by any closure construct (`async` methods or lambda expressions).</span></span>
* <span data-ttu-id="e60b9-176">Ils ne peuvent pas être utilisés comme paramètre générique.</span><span class="sxs-lookup"><span data-stu-id="e60b9-176">They cannot be used as a generic parameter.</span></span>

<span data-ttu-id="e60b9-177">Ce dernier point est essentiel pour F# la programmation de style pipeline, car `|>` est une fonction générique qui paramètre ses types d’entrée.</span><span class="sxs-lookup"><span data-stu-id="e60b9-177">This last point is crucial for F# pipeline-style programming, as `|>` is a generic function that parameterizes its input types.</span></span> <span data-ttu-id="e60b9-178">Cette restriction peut être assouplie pour `|>` à l’avenir, car elle est inline et n’effectue aucun appel aux fonctions génériques non inline dans son corps.</span><span class="sxs-lookup"><span data-stu-id="e60b9-178">This restriction may be relaxed for `|>` in the future, as it is inline and does not make any calls to non-inlined generic functions in its body.</span></span>

<span data-ttu-id="e60b9-179">Bien que ces règles restreignent fortement l’utilisation, elles le font pour garantir la promesse de l’informatique hautes performances de manière sûre.</span><span class="sxs-lookup"><span data-stu-id="e60b9-179">Although these rules strongly restrict usage, they do so to fulfill the promise of high-performance computing in a safe manner.</span></span>

## <a name="byref-returns"></a><span data-ttu-id="e60b9-180">ByRef retourne</span><span class="sxs-lookup"><span data-stu-id="e60b9-180">Byref returns</span></span>

<span data-ttu-id="e60b9-181">Les retours F# ByRef des fonctions ou des membres peuvent être générés et consommés.</span><span class="sxs-lookup"><span data-stu-id="e60b9-181">Byref returns from F# functions or members can be produced and consumed.</span></span> <span data-ttu-id="e60b9-182">Lors de l’utilisation d’une méthode retournant un `byref`, la valeur est déréférencée implicitement.</span><span class="sxs-lookup"><span data-stu-id="e60b9-182">When consuming a `byref`-returning method, the value is implicitly dereferenced.</span></span> <span data-ttu-id="e60b9-183">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="e60b9-183">For example:</span></span>

```fsharp
let squareAndPrint (data : byref<int>) = 
    let squared = data*data    // data is implicitly dereferenced
    printfn "%d" squared
```

<span data-ttu-id="e60b9-184">Pour retourner une valeur ByRef, la variable qui contient la valeur doit être plus longue que la portée actuelle.</span><span class="sxs-lookup"><span data-stu-id="e60b9-184">To return a value byref, the variable that contains the value must live longer than the current scope.</span></span>
<span data-ttu-id="e60b9-185">En outre, pour retourner ByRef, utilisez `&value` (où la valeur est une variable qui dure plus longtemps que la portée actuelle).</span><span class="sxs-lookup"><span data-stu-id="e60b9-185">Also, to return byref, use `&value` (where value is a variable that lives longer than the current scope).</span></span>

```fsharp
let mutable sum = 0
let safeSum (bytes: Span<byte>) =
    for i in 0 .. bytes.Length - 1 do
        sum <- sum + int bytes.[i]
    &sum  // sum lives longer than the scope of this function.
```

<span data-ttu-id="e60b9-186">Pour éviter la déréférence implicite, par exemple passer une référence par le biais de plusieurs appels chaînés, utilisez `&x` (où `x` est la valeur).</span><span class="sxs-lookup"><span data-stu-id="e60b9-186">To avoid the implicit dereference, such as passing a reference through multiple chained calls, use `&x` (where `x` is the value).</span></span>

<span data-ttu-id="e60b9-187">Vous pouvez également assigner directement à un `byref`de retour.</span><span class="sxs-lookup"><span data-stu-id="e60b9-187">You can also directly assign to a return `byref`.</span></span> <span data-ttu-id="e60b9-188">Considérez le programme suivant (très impératif) :</span><span class="sxs-lookup"><span data-stu-id="e60b9-188">Consider the following (highly imperative) program:</span></span>

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

<span data-ttu-id="e60b9-189">Il s'agit de la sortie :</span><span class="sxs-lookup"><span data-stu-id="e60b9-189">This is the output:</span></span>

```console
Original sequence: 1 3 7 15 31 63 127 255 511 1023
New sequence:      1 3 7 30 31 63 127 255 511 1023
```

## <a name="scoping-for-byrefs"></a><span data-ttu-id="e60b9-190">Portée pour types ByRef</span><span class="sxs-lookup"><span data-stu-id="e60b9-190">Scoping for byrefs</span></span>

<span data-ttu-id="e60b9-191">Une valeur liée à un `let`ne peut pas avoir sa référence au-delà de la portée dans laquelle elle a été définie.</span><span class="sxs-lookup"><span data-stu-id="e60b9-191">A `let`-bound value cannot have its reference exceed the scope in which it was defined.</span></span> <span data-ttu-id="e60b9-192">Par exemple, les éléments suivants ne sont pas autorisés :</span><span class="sxs-lookup"><span data-stu-id="e60b9-192">For example, the following is disallowed:</span></span>

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

<span data-ttu-id="e60b9-193">Cela vous empêche d’obtenir des résultats différents selon que vous compilez avec des optimisations ou non.</span><span class="sxs-lookup"><span data-stu-id="e60b9-193">This prevents you from getting different results depending on if you compile with optimizations or not.</span></span>
