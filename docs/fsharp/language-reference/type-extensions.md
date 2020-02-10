---
title: Extensions de type
description: Découvrez comment F# les extensions de type vous permettent d’ajouter de nouveaux membres à un type d’objet précédemment défini.
ms.date: 02/05/2020
ms.openlocfilehash: 9ab3a007783f67fd8d80cff840ac3085fdcd60f7
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2020
ms.locfileid: "77092679"
---
# <a name="type-extensions"></a><span data-ttu-id="cc1b6-103">Extensions de type</span><span class="sxs-lookup"><span data-stu-id="cc1b6-103">Type extensions</span></span>

<span data-ttu-id="cc1b6-104">Les extensions de type (également appelées « _augmentations_») sont une famille de fonctionnalités qui vous permettent d’ajouter de nouveaux membres à un type d’objet précédemment défini.</span><span class="sxs-lookup"><span data-stu-id="cc1b6-104">Type extensions (also called _augmentations_) are a family of features that let you add new members to a previously defined object type.</span></span> <span data-ttu-id="cc1b6-105">Les trois fonctionnalités sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="cc1b6-105">The three features are:</span></span>

- <span data-ttu-id="cc1b6-106">Extensions de type intrinsèques</span><span class="sxs-lookup"><span data-stu-id="cc1b6-106">Intrinsic type extensions</span></span>
- <span data-ttu-id="cc1b6-107">Extensions de type facultatives</span><span class="sxs-lookup"><span data-stu-id="cc1b6-107">Optional type extensions</span></span>
- <span data-ttu-id="cc1b6-108">Méthodes d’extension</span><span class="sxs-lookup"><span data-stu-id="cc1b6-108">Extension methods</span></span>

<span data-ttu-id="cc1b6-109">Chaque peut être utilisé dans différents scénarios et présente des compromis différents.</span><span class="sxs-lookup"><span data-stu-id="cc1b6-109">Each can be used in different scenarios and has different tradeoffs.</span></span>

## <a name="syntax"></a><span data-ttu-id="cc1b6-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cc1b6-110">Syntax</span></span>

```fsharp
// Intrinsic and optional extensions
type typename with
    member self-identifier.member-name =
        body
    ...

// Extension methods
open System.Runtime.CompilerServices

[<Extension>]
type Extensions() =
    [<Extension>]
    static member self-identifier.extension-name (ty: typename, [args]) =
        body
    ...
```

## <a name="intrinsic-type-extensions"></a><span data-ttu-id="cc1b6-111">Extensions de type intrinsèques</span><span class="sxs-lookup"><span data-stu-id="cc1b6-111">Intrinsic type extensions</span></span>

<span data-ttu-id="cc1b6-112">Une extension de type intrinsèque est une extension de type qui étend un type défini par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="cc1b6-112">An intrinsic type extension is a type extension that extends a user-defined type.</span></span>

<span data-ttu-id="cc1b6-113">Les extensions de type intrinsèques doivent être définies dans le même fichier **et** dans le même espace de noms ou module que le type qu’elles étendent.</span><span class="sxs-lookup"><span data-stu-id="cc1b6-113">Intrinsic type extensions must be defined in the same file **and** in the same namespace or module as the type they're extending.</span></span> <span data-ttu-id="cc1b6-114">Toutes les autres définitions ont pour conséquence des [extensions de type facultatives](type-extensions.md#optional-type-extensions).</span><span class="sxs-lookup"><span data-stu-id="cc1b6-114">Any other definition will result in them being [optional type extensions](type-extensions.md#optional-type-extensions).</span></span>

<span data-ttu-id="cc1b6-115">Les extensions de type intrinsèques sont parfois un moyen plus clair de séparer les fonctionnalités de la déclaration de type.</span><span class="sxs-lookup"><span data-stu-id="cc1b6-115">Intrinsic type extensions are sometimes a cleaner way to separate functionality from the type declaration.</span></span> <span data-ttu-id="cc1b6-116">L’exemple suivant montre comment définir une extension de type intrinsèque :</span><span class="sxs-lookup"><span data-stu-id="cc1b6-116">The following example shows how to define an intrinsic type extension:</span></span>

```fsharp
namespace Example

type Variant =
    | Num of int
    | Str of string
  
module Variant =
    let print v =
        match v with
        | Num n -> printf "Num %d" n
        | Str s -> printf "Str %s" s

// Add a member to Variant as an extension
type Variant with
    member x.Print() = Variant.print x
```

<span data-ttu-id="cc1b6-117">L’utilisation d’une extension de type vous permet de séparer chacun des éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="cc1b6-117">Using a type extension allows you to separate each of the following:</span></span>

- <span data-ttu-id="cc1b6-118">Déclaration d’un type de `Variant`</span><span class="sxs-lookup"><span data-stu-id="cc1b6-118">The declaration of a `Variant` type</span></span>
- <span data-ttu-id="cc1b6-119">Fonctionnalité pour imprimer la classe `Variant` en fonction de sa « forme »</span><span class="sxs-lookup"><span data-stu-id="cc1b6-119">Functionality to print the `Variant` class depending on its "shape"</span></span>
- <span data-ttu-id="cc1b6-120">Un moyen d’accéder à la fonctionnalité d’impression avec la notation `.`de style objet</span><span class="sxs-lookup"><span data-stu-id="cc1b6-120">A way to access the printing functionality with object-style `.`-notation</span></span>

<span data-ttu-id="cc1b6-121">Il s’agit d’une alternative à la définition de tout en tant que membre sur `Variant`.</span><span class="sxs-lookup"><span data-stu-id="cc1b6-121">This is an alternative to defining everything as a member on `Variant`.</span></span> <span data-ttu-id="cc1b6-122">Bien qu’il ne s’agisse pas d’une approche fondamentalement meilleure, il peut s’agir d’une représentation plus claire des fonctionnalités dans certaines situations.</span><span class="sxs-lookup"><span data-stu-id="cc1b6-122">Although it is not an inherently better approach, it can be a cleaner representation of functionality in some situations.</span></span>

<span data-ttu-id="cc1b6-123">Les extensions de type intrinsèque sont compilées en tant que membres du type qu’elles augmentent et apparaissent sur le type quand le type est examiné par réflexion.</span><span class="sxs-lookup"><span data-stu-id="cc1b6-123">Intrinsic type extensions are compiled as members of the type they augment, and appear on the type when the type is examined by reflection.</span></span>

## <a name="optional-type-extensions"></a><span data-ttu-id="cc1b6-124">Extensions de type facultatives</span><span class="sxs-lookup"><span data-stu-id="cc1b6-124">Optional type extensions</span></span>

<span data-ttu-id="cc1b6-125">Une extension de type facultative est une extension qui apparaît à l’extérieur du module, de l’espace de noms ou de l’assembly d’origine du type en cours d’extension.</span><span class="sxs-lookup"><span data-stu-id="cc1b6-125">An optional type extension is an extension that appears outside the original module, namespace, or assembly of the type being extended.</span></span>

<span data-ttu-id="cc1b6-126">Les extensions de type facultatives sont utiles pour étendre un type que vous n’avez pas défini vous-même.</span><span class="sxs-lookup"><span data-stu-id="cc1b6-126">Optional type extensions are useful for extending a type that you have not defined yourself.</span></span> <span data-ttu-id="cc1b6-127">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="cc1b6-127">For example:</span></span>

```fsharp
module Extensions

type IEnumerable<'T> with
    /// Repeat each element of the sequence n times
    member xs.RepeatElements(n: int) =
        seq {
            for x in xs do
                for _ in 1 .. n -> x
        }
```

<span data-ttu-id="cc1b6-128">Vous pouvez maintenant accéder à `RepeatElements` comme s’il s’agissait d’un membre de <xref:System.Collections.Generic.IEnumerable%601> tant que le module `Extensions` est ouvert dans l’étendue dans laquelle vous travaillez.</span><span class="sxs-lookup"><span data-stu-id="cc1b6-128">You can now access `RepeatElements` as if it's a member of <xref:System.Collections.Generic.IEnumerable%601> as long as the `Extensions` module is opened in the scope that you are working in.</span></span>

<span data-ttu-id="cc1b6-129">Les extensions facultatives n’apparaissent pas sur le type étendu lorsqu’elles sont examinées par réflexion.</span><span class="sxs-lookup"><span data-stu-id="cc1b6-129">Optional extensions do not appear on the extended type when examined by reflection.</span></span> <span data-ttu-id="cc1b6-130">Les extensions facultatives doivent se trouver dans des modules, et elles sont uniquement dans la portée lorsque le module qui contient l’extension est ouvert ou est dans la portée.</span><span class="sxs-lookup"><span data-stu-id="cc1b6-130">Optional extensions must be in modules, and they're only in scope when the module that contains the extension is open or is otherwise in scope.</span></span>

<span data-ttu-id="cc1b6-131">Les membres d’extension facultatifs sont compilés en membres statiques pour lesquels l’instance de l’objet est passée implicitement en tant que premier paramètre.</span><span class="sxs-lookup"><span data-stu-id="cc1b6-131">Optional extension members are compiled to static members for which the object instance is passed implicitly as the first parameter.</span></span> <span data-ttu-id="cc1b6-132">Toutefois, ils agissent comme s’il s’agissait de membres d’instance ou de membres statiques en fonction de la façon dont ils sont déclarés.</span><span class="sxs-lookup"><span data-stu-id="cc1b6-132">However, they act as if they're instance members or static members according to how they're declared.</span></span>

<span data-ttu-id="cc1b6-133">Les membres d’extension facultatifs ne sont C# pas non plus visibles pour les consommateurs ou Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="cc1b6-133">Optional extension members are also not visible to C# or Visual Basic consumers.</span></span> <span data-ttu-id="cc1b6-134">Ils peuvent uniquement être consommés dans F# un autre code.</span><span class="sxs-lookup"><span data-stu-id="cc1b6-134">They can only be consumed in other F# code.</span></span>

## <a name="generic-limitation-of-intrinsic-and-optional-type-extensions"></a><span data-ttu-id="cc1b6-135">Limitation générique des extensions de type intrinsèques et facultatives</span><span class="sxs-lookup"><span data-stu-id="cc1b6-135">Generic limitation of intrinsic and optional type extensions</span></span>

<span data-ttu-id="cc1b6-136">Il est possible de déclarer une extension de type sur un type générique où la variable de type est contractionnelle.</span><span class="sxs-lookup"><span data-stu-id="cc1b6-136">It's possible to declare a type extension on a generic type where the type variable is constrained.</span></span> <span data-ttu-id="cc1b6-137">La spécification est que la contrainte de la déclaration d’extension correspond à la contrainte du type déclaré.</span><span class="sxs-lookup"><span data-stu-id="cc1b6-137">The requirement is that the constraint of the extension declaration matches the constraint of the declared type.</span></span>

<span data-ttu-id="cc1b6-138">Toutefois, même lorsque les contraintes sont mises en correspondance entre un type déclaré et une extension de type, il est possible qu’une contrainte soit déduite par le corps d’un membre étendu qui impose une exigence différente sur le paramètre de type que le type déclaré.</span><span class="sxs-lookup"><span data-stu-id="cc1b6-138">However, even when constraints are matched between a declared type and a type extension, it's possible for a constraint to be inferred by the body of an extended member that imposes a different requirement on the type parameter than the declared type.</span></span> <span data-ttu-id="cc1b6-139">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="cc1b6-139">For example:</span></span>

```fsharp
open System.Collections.Generic

// NOT POSSIBLE AND FAILS TO COMPILE!
//
// The member 'Sum' has a different requirement on 'T than the type IEnumerable<'T>
type IEnumerable<'T> with
    member this.Sum() = Seq.sum this
```

<span data-ttu-id="cc1b6-140">Il n’existe aucun moyen de faire en sorte que ce code fonctionne avec une extension de type facultative :</span><span class="sxs-lookup"><span data-stu-id="cc1b6-140">There is no way to get this code to work with an optional type extension:</span></span>

- <span data-ttu-id="cc1b6-141">Comme c’est le cas, le membre `Sum` a une contrainte différente sur `'T` (`static member get_Zero` et `static member (+)`) que celle définie par l’extension de type.</span><span class="sxs-lookup"><span data-stu-id="cc1b6-141">As is, the `Sum` member has a different constraint on `'T` (`static member get_Zero` and `static member (+)`) than what the type extension defines.</span></span>
- <span data-ttu-id="cc1b6-142">La modification de l’extension de type pour avoir la même contrainte que `Sum` ne correspondra plus à la contrainte définie sur `IEnumerable<'T>`.</span><span class="sxs-lookup"><span data-stu-id="cc1b6-142">Modifying the type extension to have the same constraint as `Sum` will no longer match the defined constraint on `IEnumerable<'T>`.</span></span>
- <span data-ttu-id="cc1b6-143">La modification de `member this.Sum` en `member inline this.Sum` génère une erreur indiquant que les contraintes de type ne correspondent pas.</span><span class="sxs-lookup"><span data-stu-id="cc1b6-143">Changing `member this.Sum` to `member inline this.Sum` will give an error that type constraints are mismatched.</span></span>

<span data-ttu-id="cc1b6-144">Les méthodes statiques qui sont souhaitées sont des méthodes statiques qui « flottent dans l’espace » et peuvent être présentées comme si elles étendaient un type.</span><span class="sxs-lookup"><span data-stu-id="cc1b6-144">What is desired are static methods that "float in space" and can be presented as if they're extending a type.</span></span> <span data-ttu-id="cc1b6-145">C’est là que les méthodes d’extension deviennent nécessaires.</span><span class="sxs-lookup"><span data-stu-id="cc1b6-145">This is where extension methods become necessary.</span></span>

## <a name="extension-methods"></a><span data-ttu-id="cc1b6-146">Méthodes d’extension</span><span class="sxs-lookup"><span data-stu-id="cc1b6-146">Extension methods</span></span>

<span data-ttu-id="cc1b6-147">Enfin, les méthodes d’extension (parfoisC# appelées « membres d’extension de style » F# ) peuvent être déclarées dans en tant que méthode de membre statique sur une classe.</span><span class="sxs-lookup"><span data-stu-id="cc1b6-147">Finally, extension methods (sometimes called "C# style extension members") can be declared in F# as a static member method on a class.</span></span>

<span data-ttu-id="cc1b6-148">Les méthodes d’extension sont utiles lorsque vous souhaitez définir des extensions sur un type générique qui contraignent la variable de type.</span><span class="sxs-lookup"><span data-stu-id="cc1b6-148">Extension methods are useful for when you wish to define extensions on a generic type that will constrain the type variable.</span></span> <span data-ttu-id="cc1b6-149">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="cc1b6-149">For example:</span></span>

```fsharp
namespace Extensions

open System.Runtime.CompilerServices

[<Extension>]
type IEnumerableExtensions =
    [<Extension>]
    static member inline Sum(xs: IEnumerable<'T>) = Seq.sum xs
```

<span data-ttu-id="cc1b6-150">Lorsqu’il est utilisé, ce code apparaît comme si `Sum` est défini sur <xref:System.Collections.Generic.IEnumerable%601>, tant que `Extensions` a été ouvert ou est dans l’étendue.</span><span class="sxs-lookup"><span data-stu-id="cc1b6-150">When used, this code will make it appear as if `Sum` is defined on <xref:System.Collections.Generic.IEnumerable%601>, so long as `Extensions` has been opened or is in scope.</span></span>

<span data-ttu-id="cc1b6-151">Pour que l’extension soit disponible pour le code VB.NET, un `ExtensionAttribute` supplémentaire est requis au niveau de l’assembly :</span><span class="sxs-lookup"><span data-stu-id="cc1b6-151">For the extension to be available to VB.NET code, an extra `ExtensionAttribute` is required at the assembly level:</span></span>

```fsharp
module AssemblyInfo
open System.Runtime.CompilerServices
[<assembly:Extension>]
do ()
```

## <a name="other-remarks"></a><span data-ttu-id="cc1b6-152">Autres remarques</span><span class="sxs-lookup"><span data-stu-id="cc1b6-152">Other remarks</span></span>

<span data-ttu-id="cc1b6-153">Les extensions de type ont également les attributs suivants :</span><span class="sxs-lookup"><span data-stu-id="cc1b6-153">Type extensions also have the following attributes:</span></span>

- <span data-ttu-id="cc1b6-154">Tout type accessible peut être étendu.</span><span class="sxs-lookup"><span data-stu-id="cc1b6-154">Any type that can be accessed can be extended.</span></span>
- <span data-ttu-id="cc1b6-155">Les extensions de type intrinsèques et facultatives peuvent définir _n’importe quel type de_ membre, pas seulement des méthodes.</span><span class="sxs-lookup"><span data-stu-id="cc1b6-155">Intrinsic and optional type extensions can define _any_ member type, not just methods.</span></span> <span data-ttu-id="cc1b6-156">Ainsi, les propriétés d’extension sont également possibles, par exemple.</span><span class="sxs-lookup"><span data-stu-id="cc1b6-156">So extension properties are also possible, for example.</span></span>
- <span data-ttu-id="cc1b6-157">Le jeton `self-identifier` dans la [syntaxe](type-extensions.md#syntax) représente l’instance du type appelé, tout comme les membres ordinaires.</span><span class="sxs-lookup"><span data-stu-id="cc1b6-157">The `self-identifier` token in the [syntax](type-extensions.md#syntax) represents the instance of the type being invoked, just like ordinary members.</span></span>
- <span data-ttu-id="cc1b6-158">Les membres étendus peuvent être des membres statiques ou d’instance.</span><span class="sxs-lookup"><span data-stu-id="cc1b6-158">Extended members can be static or instance members.</span></span>
- <span data-ttu-id="cc1b6-159">Les variables de type sur une extension de type doivent correspondre aux contraintes du type déclaré.</span><span class="sxs-lookup"><span data-stu-id="cc1b6-159">Type variables on a type extension must match the constraints of the declared type.</span></span>

<span data-ttu-id="cc1b6-160">Les limitations suivantes existent également pour les extensions de type :</span><span class="sxs-lookup"><span data-stu-id="cc1b6-160">The following limitations also exist for type extensions:</span></span>

- <span data-ttu-id="cc1b6-161">Les extensions de type ne prennent pas en charge les méthodes virtuelles ou abstraites.</span><span class="sxs-lookup"><span data-stu-id="cc1b6-161">Type extensions do not support virtual or abstract methods.</span></span>
- <span data-ttu-id="cc1b6-162">Les extensions de type ne prennent pas en charge les méthodes override comme augmentations.</span><span class="sxs-lookup"><span data-stu-id="cc1b6-162">Type extensions do not support override methods as augmentations.</span></span>
- <span data-ttu-id="cc1b6-163">Les extensions de type ne prennent pas en charge les [paramètres de type résolus statiquement](./generics/statically-resolved-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="cc1b6-163">Type extensions do not support [Statically Resolved Type Parameters](./generics/statically-resolved-type-parameters.md).</span></span>
- <span data-ttu-id="cc1b6-164">Les extensions de type facultatives ne prennent pas en charge les constructeurs comme augmentations.</span><span class="sxs-lookup"><span data-stu-id="cc1b6-164">Optional Type extensions do not support constructors as augmentations.</span></span>
- <span data-ttu-id="cc1b6-165">Les extensions de type ne peuvent pas être définies sur les [abréviations de type](type-abbreviations.md).</span><span class="sxs-lookup"><span data-stu-id="cc1b6-165">Type extensions cannot be defined on [type abbreviations](type-abbreviations.md).</span></span>
- <span data-ttu-id="cc1b6-166">Les extensions de type ne sont pas valides pour `byref<'T>` (bien qu’elles puissent être déclarées).</span><span class="sxs-lookup"><span data-stu-id="cc1b6-166">Type extensions are not valid for `byref<'T>` (though they can be declared).</span></span>
- <span data-ttu-id="cc1b6-167">Les extensions de type ne sont pas valides pour les attributs (bien qu’elles puissent être déclarées).</span><span class="sxs-lookup"><span data-stu-id="cc1b6-167">Type extensions are not valid for attributes (though they can be declared).</span></span>
- <span data-ttu-id="cc1b6-168">Vous pouvez définir des extensions qui surchargent d’autres méthodes du même nom F# , mais le compilateur donne la préférence aux méthodes non d’extension en cas d’appel ambigu.</span><span class="sxs-lookup"><span data-stu-id="cc1b6-168">You can define extensions that overload other methods of the same name, but the F# compiler gives preference to non-extension methods if there is an ambiguous call.</span></span>

<span data-ttu-id="cc1b6-169">Enfin, s’il existe plusieurs extensions de type intrinsèques pour un type, tous les membres doivent être uniques.</span><span class="sxs-lookup"><span data-stu-id="cc1b6-169">Finally, if multiple intrinsic type extensions exist for one type, all members must be unique.</span></span> <span data-ttu-id="cc1b6-170">Pour les extensions de type facultatives, les membres de différentes extensions de type du même type peuvent avoir le même nom.</span><span class="sxs-lookup"><span data-stu-id="cc1b6-170">For optional type extensions, members in different type extensions to the same type can have the same names.</span></span> <span data-ttu-id="cc1b6-171">Les erreurs d’ambiguïté se produisent uniquement si le code client ouvre deux portées différentes qui définissent les mêmes noms de membres.</span><span class="sxs-lookup"><span data-stu-id="cc1b6-171">Ambiguity errors occur only if client code opens two different scopes that define the same member names.</span></span>

## <a name="see-also"></a><span data-ttu-id="cc1b6-172">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cc1b6-172">See also</span></span>

- [<span data-ttu-id="cc1b6-173">Informations de référence sur le langage F#</span><span class="sxs-lookup"><span data-stu-id="cc1b6-173">F# Language Reference</span></span>](index.md)
- <span data-ttu-id="cc1b6-174">[Members](./members/index.md) (Membres)</span><span class="sxs-lookup"><span data-stu-id="cc1b6-174">[Members](./members/index.md)</span></span>
