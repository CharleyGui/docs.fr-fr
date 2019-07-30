---
title: Paramètres de type résolus statiquement
description: Découvrez comment utiliser un F# paramètre de type résolu statiquement, qui est remplacé par un type réel au moment de la compilation plutôt qu’au moment de l’exécution.
ms.date: 05/16/2016
ms.openlocfilehash: 43ed79b6e5f43a499a27b05e26472b021c455e44
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630583"
---
# <a name="statically-resolved-type-parameters"></a><span data-ttu-id="acbf1-103">Paramètres de type résolus statiquement</span><span class="sxs-lookup"><span data-stu-id="acbf1-103">Statically Resolved Type Parameters</span></span>

<span data-ttu-id="acbf1-104">Un *paramètre de type résolu statiquement* est un paramètre de type qui est remplacé par un type réel au moment de la compilation plutôt qu’au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="acbf1-104">A *statically resolved type parameter* is a type parameter that is replaced with an actual type at compile time instead of at run time.</span></span> <span data-ttu-id="acbf1-105">Elles sont précédées d’un symbole de signe insertion (^).</span><span class="sxs-lookup"><span data-stu-id="acbf1-105">They are preceded by a caret (^) symbol.</span></span>

## <a name="syntax"></a><span data-ttu-id="acbf1-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="acbf1-106">Syntax</span></span>

```
ˆtype-parameter
```

## <a name="remarks"></a><span data-ttu-id="acbf1-107">Notes</span><span class="sxs-lookup"><span data-stu-id="acbf1-107">Remarks</span></span>

<span data-ttu-id="acbf1-108">Dans le F# langage, il existe deux genres distincts de paramètres de type.</span><span class="sxs-lookup"><span data-stu-id="acbf1-108">In the F# language, there are two distinct kinds of type parameters.</span></span> <span data-ttu-id="acbf1-109">Le premier type est le paramètre de type générique standard.</span><span class="sxs-lookup"><span data-stu-id="acbf1-109">The first kind is the standard generic type parameter.</span></span> <span data-ttu-id="acbf1-110">Celles-ci sont indiquées par une apostrophe ('), `'T` comme `'U`dans et.</span><span class="sxs-lookup"><span data-stu-id="acbf1-110">These are indicated by an apostrophe ('), as in `'T` and `'U`.</span></span> <span data-ttu-id="acbf1-111">Ils sont équivalents aux paramètres de type générique dans d’autres langages de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="acbf1-111">They are equivalent to generic type parameters in other .NET Framework languages.</span></span> <span data-ttu-id="acbf1-112">L’autre type est résolu statiquement et est indiqué par un symbole de signe insertion, comme `^T` dans `^U`et.</span><span class="sxs-lookup"><span data-stu-id="acbf1-112">The other kind is statically resolved and is indicated by a caret symbol, as in `^T` and `^U`.</span></span>

<span data-ttu-id="acbf1-113">Les paramètres de type résolus statiquement sont principalement utiles avec les contraintes de membre, qui sont des contraintes qui vous permettent de spécifier qu’un argument de type doit avoir un membre ou des membres particuliers pour être utilisé.</span><span class="sxs-lookup"><span data-stu-id="acbf1-113">Statically resolved type parameters are primarily useful in conjunction with member constraints, which are constraints that allow you to specify that a type argument must have a particular member or members in order to be used.</span></span> <span data-ttu-id="acbf1-114">Il n’existe aucun moyen de créer ce type de contrainte à l’aide d’un paramètre de type générique standard.</span><span class="sxs-lookup"><span data-stu-id="acbf1-114">There is no way to create this kind of constraint by using a regular generic type parameter.</span></span>

<span data-ttu-id="acbf1-115">Le tableau suivant récapitule les similitudes et les différences entre les deux genres de paramètres de type.</span><span class="sxs-lookup"><span data-stu-id="acbf1-115">The following table summarizes the similarities and differences between the two kinds of type parameters.</span></span>

|<span data-ttu-id="acbf1-116">Fonctionnalité</span><span class="sxs-lookup"><span data-stu-id="acbf1-116">Feature</span></span>|<span data-ttu-id="acbf1-117">Générique</span><span class="sxs-lookup"><span data-stu-id="acbf1-117">Generic</span></span>|<span data-ttu-id="acbf1-118">Résolu statiquement</span><span class="sxs-lookup"><span data-stu-id="acbf1-118">Statically resolved</span></span>|
|-------|-------|-------------------|
|<span data-ttu-id="acbf1-119">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="acbf1-119">Syntax</span></span>|<span data-ttu-id="acbf1-120">`'T`, `'U`</span><span class="sxs-lookup"><span data-stu-id="acbf1-120">`'T`, `'U`</span></span>|<span data-ttu-id="acbf1-121">`^T`, `^U`</span><span class="sxs-lookup"><span data-stu-id="acbf1-121">`^T`, `^U`</span></span>|
|<span data-ttu-id="acbf1-122">Temps de résolution</span><span class="sxs-lookup"><span data-stu-id="acbf1-122">Resolution time</span></span>|<span data-ttu-id="acbf1-123">En cours d’exécution</span><span class="sxs-lookup"><span data-stu-id="acbf1-123">Run time</span></span>|<span data-ttu-id="acbf1-124">Temps de compilation</span><span class="sxs-lookup"><span data-stu-id="acbf1-124">Compile time</span></span>|
|<span data-ttu-id="acbf1-125">Contraintes de membre</span><span class="sxs-lookup"><span data-stu-id="acbf1-125">Member constraints</span></span>|<span data-ttu-id="acbf1-126">Ne peut pas être utilisé avec des contraintes de membre.</span><span class="sxs-lookup"><span data-stu-id="acbf1-126">Cannot be used with member constraints.</span></span>|<span data-ttu-id="acbf1-127">Peut être utilisé avec des contraintes de membre.</span><span class="sxs-lookup"><span data-stu-id="acbf1-127">Can be used with member constraints.</span></span>|
|<span data-ttu-id="acbf1-128">Génération de code</span><span class="sxs-lookup"><span data-stu-id="acbf1-128">Code generation</span></span>|<span data-ttu-id="acbf1-129">Un type (ou une méthode) avec des paramètres de type générique standard entraîne la génération d’un type ou d’une méthode générique unique.</span><span class="sxs-lookup"><span data-stu-id="acbf1-129">A type (or method) with standard generic type parameters results in the generation of a single generic type or method.</span></span>|<span data-ttu-id="acbf1-130">Plusieurs instanciations de types et de méthodes sont générées, une pour chaque type requis.</span><span class="sxs-lookup"><span data-stu-id="acbf1-130">Multiple instantiations of types and methods are generated, one for each type that is needed.</span></span>|
|<span data-ttu-id="acbf1-131">Utiliser avec les types</span><span class="sxs-lookup"><span data-stu-id="acbf1-131">Use with types</span></span>|<span data-ttu-id="acbf1-132">Peut être utilisé sur les types.</span><span class="sxs-lookup"><span data-stu-id="acbf1-132">Can be used on types.</span></span>|<span data-ttu-id="acbf1-133">Ne peut pas être utilisé sur les types.</span><span class="sxs-lookup"><span data-stu-id="acbf1-133">Cannot be used on types.</span></span>|
|<span data-ttu-id="acbf1-134">Utiliser avec des fonctions inline</span><span class="sxs-lookup"><span data-stu-id="acbf1-134">Use with inline functions</span></span>|<span data-ttu-id="acbf1-135">Non.</span><span class="sxs-lookup"><span data-stu-id="acbf1-135">No.</span></span> <span data-ttu-id="acbf1-136">Une fonction inline ne peut pas être paramétrée avec un paramètre de type générique standard.</span><span class="sxs-lookup"><span data-stu-id="acbf1-136">An inline function cannot be parameterized with a standard generic type parameter.</span></span>|<span data-ttu-id="acbf1-137">Oui.</span><span class="sxs-lookup"><span data-stu-id="acbf1-137">Yes.</span></span> <span data-ttu-id="acbf1-138">Les paramètres de type résolus statiquement ne peuvent pas être utilisés sur des fonctions ou des méthodes qui ne sont pas Inline.</span><span class="sxs-lookup"><span data-stu-id="acbf1-138">Statically resolved type parameters cannot be used on functions or methods that are not inline.</span></span>|

<span data-ttu-id="acbf1-139">De F# nombreuses fonctions de bibliothèque principales, en particulier les opérateurs, ont des paramètres de type résolus statiquement.</span><span class="sxs-lookup"><span data-stu-id="acbf1-139">Many F# core library functions, especially operators, have statically resolved type parameters.</span></span> <span data-ttu-id="acbf1-140">Ces fonctions et opérateurs sont inline et produisent une génération de code efficace pour les calculs numériques.</span><span class="sxs-lookup"><span data-stu-id="acbf1-140">These functions and operators are inline, and result in efficient code generation for numeric computations.</span></span>

<span data-ttu-id="acbf1-141">Les méthodes inline et les fonctions qui utilisent des opérateurs, ou utilisent d’autres fonctions qui ont des paramètres de type résolus statiquement, peuvent également utiliser des paramètres de type résolus statiquement eux-mêmes.</span><span class="sxs-lookup"><span data-stu-id="acbf1-141">Inline methods and functions that use operators, or use other functions that have statically resolved type parameters, can also use statically resolved type parameters themselves.</span></span> <span data-ttu-id="acbf1-142">Souvent, l’inférence de type déduit que ces fonctions inline ont des paramètres de type résolus statiquement.</span><span class="sxs-lookup"><span data-stu-id="acbf1-142">Often, type inference infers such inline functions to have statically resolved type parameters.</span></span> <span data-ttu-id="acbf1-143">L’exemple suivant illustre une définition d’opérateur qui est déduite pour avoir un paramètre de type résolu statiquement.</span><span class="sxs-lookup"><span data-stu-id="acbf1-143">The following example illustrates an operator definition that is inferred to have a statically resolved type parameter.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet401.fs)]

<span data-ttu-id="acbf1-144">Le type résolu de `(+@)` est basé sur l’utilisation `(+)` de et `(*)`, les deux ayant provoqué l’inférence de type pour déduire les contraintes de membre sur les paramètres de type résolus statiquement.</span><span class="sxs-lookup"><span data-stu-id="acbf1-144">The resolved type of `(+@)` is based on the use of both `(+)` and `(*)`, both of which cause type inference to infer member constraints on the statically resolved type parameters.</span></span> <span data-ttu-id="acbf1-145">Le type résolu, comme indiqué dans l' F# interpréteur, est le suivant.</span><span class="sxs-lookup"><span data-stu-id="acbf1-145">The resolved type, as shown in the F# interpreter, is as follows.</span></span>

```fsharp
^a -> ^c -> ^d
when (^a or ^b) : (static member ( + ) : ^a * ^b -> ^d) and
(^a or ^c) : (static member ( * ) : ^a * ^c -> ^b)
```

<span data-ttu-id="acbf1-146">La sortie est la suivante.</span><span class="sxs-lookup"><span data-stu-id="acbf1-146">The output is as follows.</span></span>

```
2
1.500000
```

<span data-ttu-id="acbf1-147">À partir F# de 4,1, vous pouvez également spécifier des noms de types concrets dans des signatures de paramètre de type résolues statiquement.</span><span class="sxs-lookup"><span data-stu-id="acbf1-147">Starting with F# 4.1, you can also specify concrete type names in statically resolved type parameter signatures.</span></span>  <span data-ttu-id="acbf1-148">Dans les versions antérieures du langage, le nom de type pouvait être inféré en fait par le compilateur, mais il n’a pas pu être spécifié dans la signature.</span><span class="sxs-lookup"><span data-stu-id="acbf1-148">In previous versions of the language, the type name could actually be inferred by the compiler, but could not actually be specified in the signature.</span></span>  <span data-ttu-id="acbf1-149">À partir F# de 4,1, vous pouvez également spécifier des noms de types concrets dans des signatures de paramètre de type résolues statiquement.</span><span class="sxs-lookup"><span data-stu-id="acbf1-149">As of F# 4.1, you may also specify concrete type names in statically resolved type parameter signatures.</span></span> <span data-ttu-id="acbf1-150">Voici un exemple :</span><span class="sxs-lookup"><span data-stu-id="acbf1-150">Here's an example:</span></span>

```fsharp
let inline konst x _ = x

type CFunctor() = 
    static member inline fmap (f: ^a -> ^b, a: ^a list) = List.map f a
    static member inline fmap (f: ^a -> ^b, a: ^a option) =
        match a with
        | None -> None
        | Some x -> Some (f x)

    // default implementation of replace
    static member inline replace< ^a, ^b, ^c, ^d, ^e when ^a :> CFunctor and (^a or ^d): (static member fmap: (^b -> ^c) * ^d -> ^e) > (a, f) =
        ((^a or ^d) : (static member fmap : (^b -> ^c) * ^d -> ^e) (konst a, f))

    // call overridden replace if present
    static member inline replace< ^a, ^b, ^c when ^b: (static member replace: ^a * ^b -> ^c)>(a: ^a, f: ^b) =
        (^b : (static member replace: ^a * ^b -> ^c) (a, f))

let inline replace_instance< ^a, ^b, ^c, ^d when (^a or ^c): (static member replace: ^b * ^c -> ^d)> (a: ^b, f: ^c) =
        ((^a or ^c): (static member replace: ^b * ^c -> ^d) (a, f))

// Note the concrete type 'CFunctor' specified in the signature
let inline replace (a: ^a) (f: ^b): ^a0 when (CFunctor or  ^b): (static member replace: ^a *  ^b ->  ^a0) =
    replace_instance<CFunctor, _, _, _> (a, f)
```

## <a name="see-also"></a><span data-ttu-id="acbf1-151">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="acbf1-151">See also</span></span>

- [<span data-ttu-id="acbf1-152">Génériques</span><span class="sxs-lookup"><span data-stu-id="acbf1-152">Generics</span></span>](index.md)
- [<span data-ttu-id="acbf1-153">Inférence de type</span><span class="sxs-lookup"><span data-stu-id="acbf1-153">Type Inference</span></span>](../type-inference.md)
- [<span data-ttu-id="acbf1-154">Généralisation automatique</span><span class="sxs-lookup"><span data-stu-id="acbf1-154">Automatic Generalization</span></span>](automatic-generalization.md)
- [<span data-ttu-id="acbf1-155">Contraintes</span><span class="sxs-lookup"><span data-stu-id="acbf1-155">Constraints</span></span>](constraints.md)
- [<span data-ttu-id="acbf1-156">Fonctions inline</span><span class="sxs-lookup"><span data-stu-id="acbf1-156">Inline Functions</span></span>](../functions/inline-functions.md)
