---
title: Structures
description: En savoir plus F# sur la structure, un type d’objet compact est souvent plus efficace qu’une classe pour les types avec une petite quantité de données et un comportement simple.
ms.date: 05/16/2016
ms.openlocfilehash: 1e9652cc4776e4d1d52eb20e41b6dd87a6c5ba05
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/28/2019
ms.locfileid: "70106826"
---
# <a name="structures"></a><span data-ttu-id="179aa-103">Structures</span><span class="sxs-lookup"><span data-stu-id="179aa-103">Structures</span></span>

<span data-ttu-id="179aa-104">Une *structure* est un type d’objet compact qui peut être plus efficace qu’une classe pour les types qui ont une petite quantité de données et un comportement simple.</span><span class="sxs-lookup"><span data-stu-id="179aa-104">A *structure* is a compact object type that can be more efficient than a class for types that have a small amount of data and simple behavior.</span></span>

## <a name="syntax"></a><span data-ttu-id="179aa-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="179aa-105">Syntax</span></span>

```fsharp
[ attributes ]
type [accessibility-modifier] type-name =
    struct
        type-definition-elements-and-members
    end
// or
[ attributes ]
[<StructAttribute>]
type [accessibility-modifier] type-name =
    type-definition-elements-and-members
```

## <a name="remarks"></a><span data-ttu-id="179aa-106">Notes</span><span class="sxs-lookup"><span data-stu-id="179aa-106">Remarks</span></span>

<span data-ttu-id="179aa-107">Les structures sont des *types valeur*, ce qui signifie qu’elles sont stockées directement sur la pile ou, lorsqu’elles sont utilisées en tant que champs ou éléments de tableau, inline dans le type parent.</span><span class="sxs-lookup"><span data-stu-id="179aa-107">Structures are *value types*, which means that they are stored directly on the stack or, when they are used as fields or array elements, inline in the parent type.</span></span> <span data-ttu-id="179aa-108">Contrairement aux classes et aux enregistrements, les structures ont une sémantique de passage par valeur.</span><span class="sxs-lookup"><span data-stu-id="179aa-108">Unlike classes and records, structures have pass-by-value semantics.</span></span> <span data-ttu-id="179aa-109">Cela signifie qu'elles sont principalement utilisées pour les petits volumes de données qui sont fréquemment sollicités et copiés.</span><span class="sxs-lookup"><span data-stu-id="179aa-109">This means that they are useful primarily for small aggregates of data that are accessed and copied frequently.</span></span>

<span data-ttu-id="179aa-110">Dans la syntaxe précédente, deux formes sont présentes.</span><span class="sxs-lookup"><span data-stu-id="179aa-110">In the previous syntax, two forms are shown.</span></span> <span data-ttu-id="179aa-111">La première n'est pas la syntaxe simplifiée, mais elle est néanmoins fréquemment utilisée, car quand vous employez les mots clés `struct` et `end`, vous pouvez omettre l'attribut `StructAttribute` qui apparaît dans la seconde forme.</span><span class="sxs-lookup"><span data-stu-id="179aa-111">The first is not the lightweight syntax, but it is nevertheless frequently used because, when you use the `struct` and `end` keywords, you can omit the `StructAttribute` attribute, which appears in the second form.</span></span> <span data-ttu-id="179aa-112">Vous pouvez abréger `StructAttribute` en `Struct`.</span><span class="sxs-lookup"><span data-stu-id="179aa-112">You can abbreviate `StructAttribute` to just `Struct`.</span></span>

<span data-ttu-id="179aa-113">Les *éléments Type-Definition-Elements-et-members* dans la syntaxe précédente représentent des déclarations et des définitions de membre.</span><span class="sxs-lookup"><span data-stu-id="179aa-113">The *type-definition-elements-and-members* in the previous syntax represents member declarations and definitions.</span></span> <span data-ttu-id="179aa-114">Les structures peuvent avoir des constructeurs et des champs modifiables et non modifiables, et peuvent déclarer des membres et des implémentations d'interface.</span><span class="sxs-lookup"><span data-stu-id="179aa-114">Structures can have constructors and mutable and immutable fields, and they can declare members and interface implementations.</span></span> <span data-ttu-id="179aa-115">Pour plus d’informations, consultez [membres](./members/index.md).</span><span class="sxs-lookup"><span data-stu-id="179aa-115">For more information, see [Members](./members/index.md).</span></span>

<span data-ttu-id="179aa-116">Les structures ne peuvent pas participer à l’héritage, ne peuvent pas contenir les liaisons `let` ou `do`, et ne peuvent pas comporter de manière récursive les champs de leur propre type (bien qu’elles puissent contenir des cellules de référence qui référencent leur propre type).</span><span class="sxs-lookup"><span data-stu-id="179aa-116">Structures cannot participate in inheritance, cannot contain `let` or `do` bindings, and cannot recursively contain fields of their own type (although they can contain reference cells that reference their own type).</span></span>

<span data-ttu-id="179aa-117">Étant donné que les structures n’autorisent pas les liaisons `let`, vous devez déclarer leurs champs à l’aide du mot clé `val`.</span><span class="sxs-lookup"><span data-stu-id="179aa-117">Because structures do not allow `let` bindings, you must declare fields in structures by using the `val` keyword.</span></span> <span data-ttu-id="179aa-118">Le mot clé `val` définit un champ et son type, mais n'autorise pas l'initialisation.</span><span class="sxs-lookup"><span data-stu-id="179aa-118">The `val` keyword defines a field and its type but does not allow initialization.</span></span> <span data-ttu-id="179aa-119">À la place, les déclarations `val` sont initialisées à la valeur zéro ou null.</span><span class="sxs-lookup"><span data-stu-id="179aa-119">Instead, `val` declarations are initialized to zero or null.</span></span> <span data-ttu-id="179aa-120">Pour cette raison, les structures ayant un constructeur implicite (c’est-à-dire les paramètres qui sont fournis immédiatement après le nom de la structure dans la déclaration) requièrent que les déclarations `val` soient annotées avec l’attribut `DefaultValue`.</span><span class="sxs-lookup"><span data-stu-id="179aa-120">For this reason, structures that have an implicit constructor (that is, parameters that are given immediately after the structure name in the declaration) require that `val` declarations be annotated with the `DefaultValue` attribute.</span></span> <span data-ttu-id="179aa-121">Les structures ayant un constructeur défini prennent toujours en charge l'initialisation à zéro.</span><span class="sxs-lookup"><span data-stu-id="179aa-121">Structures that have a defined constructor still support zero-initialization.</span></span> <span data-ttu-id="179aa-122">Par conséquent, l'attribut `DefaultValue` est une déclaration selon laquelle une telle valeur égale à zéro est valide pour le champ.</span><span class="sxs-lookup"><span data-stu-id="179aa-122">Therefore, the `DefaultValue` attribute is a declaration that such a zero value is valid for the field.</span></span> <span data-ttu-id="179aa-123">Les constructeurs implicites pour les structures n'exécutent aucune action, car les liaisons `let` et `do` ne sont pas autorisées sur le type, mais les valeurs de paramètre de constructeur implicite passées sont disponibles en tant que champs privés.</span><span class="sxs-lookup"><span data-stu-id="179aa-123">Implicit constructors for structures do not perform any actions because `let` and `do` bindings aren’t allowed on the type, but the implicit constructor parameter values passed in are available as private fields.</span></span>

<span data-ttu-id="179aa-124">Les constructeurs explicites peuvent impliquer l'initialisation des valeurs de champ.</span><span class="sxs-lookup"><span data-stu-id="179aa-124">Explicit constructors might involve initialization of field values.</span></span> <span data-ttu-id="179aa-125">Quand une structure a un constructeur explicite, elle prend toujours en charge l'initialisation à zéro ; toutefois, vous n'utilisez pas l'attribut `DefaultValue` sur les déclarations `val`, car il est en conflit avec le constructeur explicite.</span><span class="sxs-lookup"><span data-stu-id="179aa-125">When you have a structure that has an explicit constructor, it still supports zero-initialization; however, you do not use the `DefaultValue` attribute on the `val` declarations because it conflicts with the explicit constructor.</span></span> <span data-ttu-id="179aa-126">Pour plus d’informations `val` sur les déclarations [, consultez champs explicites: `val` Mot clé](./members/explicit-fields-the-val-keyword.md).</span><span class="sxs-lookup"><span data-stu-id="179aa-126">For more information about `val` declarations, see [Explicit Fields: The `val` Keyword](./members/explicit-fields-the-val-keyword.md).</span></span>

<span data-ttu-id="179aa-127">Les attributs et les modificateurs d'accessibilité sont autorisés sur les structures et suivent les mêmes règles que celles des autres types.</span><span class="sxs-lookup"><span data-stu-id="179aa-127">Attributes and accessibility modifiers are allowed on structures, and follow the same rules as those for other types.</span></span> <span data-ttu-id="179aa-128">Pour plus d’informations, consultez [attributs](attributes.md) et [Access Control](access-control.md).</span><span class="sxs-lookup"><span data-stu-id="179aa-128">For more information, see [Attributes](attributes.md) and [Access Control](access-control.md).</span></span>

<span data-ttu-id="179aa-129">Les exemples de code suivants illustrent des définitions de structure.</span><span class="sxs-lookup"><span data-stu-id="179aa-129">The following code examples illustrate structure definitions.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2501.fs)]

## <a name="byreflike-structs"></a><span data-ttu-id="179aa-130">Structs ByRefLike</span><span class="sxs-lookup"><span data-stu-id="179aa-130">ByRefLike structs</span></span>

<span data-ttu-id="179aa-131">Vous pouvez définir vos propres structs qui peuvent adhérer à `byref`des sémantiques de type: pour plus d’informations, consultez [types ByRef](byrefs.md) .</span><span class="sxs-lookup"><span data-stu-id="179aa-131">You can define your own structs that can adhere to `byref`-like semantics: see [Byrefs](byrefs.md) for more information.</span></span> <span data-ttu-id="179aa-132">Cette opération s’effectue avec <xref:System.Runtime.CompilerServices.IsByRefLikeAttribute> l’attribut:</span><span class="sxs-lookup"><span data-stu-id="179aa-132">This is done with the <xref:System.Runtime.CompilerServices.IsByRefLikeAttribute> attribute:</span></span>

```fsharp
open System
open System.Runtime.CompilerServices

[<IsByRefLike; Struct>]
type S(count1: Span<int>, count2: Span<int>) =
    member x.Count1 = count1
    member x.Count2 = count2
```

<span data-ttu-id="179aa-133">`IsByRefLike`n’implique `Struct`pas.</span><span class="sxs-lookup"><span data-stu-id="179aa-133">`IsByRefLike` does not imply `Struct`.</span></span> <span data-ttu-id="179aa-134">Les deux doivent être présents sur le type.</span><span class="sxs-lookup"><span data-stu-id="179aa-134">Both must be present on the type.</span></span>

<span data-ttu-id="179aa-135">Un struct`byref`«-like» dans F# est un type valeur lié à la pile.</span><span class="sxs-lookup"><span data-stu-id="179aa-135">A "`byref`-like" struct in F# is a stack-bound value type.</span></span> <span data-ttu-id="179aa-136">Elle n’est jamais allouée sur le tas managé.</span><span class="sxs-lookup"><span data-stu-id="179aa-136">It is never allocated on the managed heap.</span></span> <span data-ttu-id="179aa-137">Un `byref`struct de type like est utile pour la programmation hautes performances, car il est appliqué avec un ensemble de vérifications fortes sur la durée de vie et la non-capture.</span><span class="sxs-lookup"><span data-stu-id="179aa-137">A `byref`-like struct is useful for high-performance programming, as it is enforced with set of strong checks about lifetime and non-capture.</span></span> <span data-ttu-id="179aa-138">Les règles sont les suivantes:</span><span class="sxs-lookup"><span data-stu-id="179aa-138">The rules are:</span></span>

- <span data-ttu-id="179aa-139">Elles peuvent être utilisées en tant que paramètres de fonction, paramètres de méthode, variables locales, retours de méthode.</span><span class="sxs-lookup"><span data-stu-id="179aa-139">They can be used as function parameters, method parameters, local variables, method returns.</span></span>
- <span data-ttu-id="179aa-140">Ils ne peuvent pas être des membres statiques ou d’instance d’une classe ou d’un struct normal.</span><span class="sxs-lookup"><span data-stu-id="179aa-140">They cannot be static or instance members of a class or normal struct.</span></span>
- <span data-ttu-id="179aa-141">Ils ne peuvent pas être capturés par une`async` construction de fermeture (méthodes ou expressions lambda).</span><span class="sxs-lookup"><span data-stu-id="179aa-141">They cannot be captured by any closure construct (`async` methods or lambda expressions).</span></span>
- <span data-ttu-id="179aa-142">Ils ne peuvent pas être utilisés comme paramètre générique.</span><span class="sxs-lookup"><span data-stu-id="179aa-142">They cannot be used as a generic parameter.</span></span>

<span data-ttu-id="179aa-143">Bien que ces règles restreignent fortement l’utilisation, elles le font pour garantir la promesse de l’informatique hautes performances de manière sûre.</span><span class="sxs-lookup"><span data-stu-id="179aa-143">Although these rules very strongly restrict usage, they do so to fulfill the promise of high-performance computing in a safe manner.</span></span>

## <a name="readonly-structs"></a><span data-ttu-id="179aa-144">Structs en lecture seule</span><span class="sxs-lookup"><span data-stu-id="179aa-144">ReadOnly structs</span></span>

<span data-ttu-id="179aa-145">Vous pouvez annoter des structs <xref:System.Runtime.CompilerServices.IsReadOnlyAttribute> avec l’attribut.</span><span class="sxs-lookup"><span data-stu-id="179aa-145">You can annotate structs with the <xref:System.Runtime.CompilerServices.IsReadOnlyAttribute> attribute.</span></span> <span data-ttu-id="179aa-146">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="179aa-146">For example:</span></span>

```fsharp
[<IsReadOnly; Struct>]
type S(count1: int, count2: int) =
    member x.Count1 = count1
    member x.Count2 = count2
```

<span data-ttu-id="179aa-147">`IsReadOnly`n’implique `Struct`pas.</span><span class="sxs-lookup"><span data-stu-id="179aa-147">`IsReadOnly` does not imply `Struct`.</span></span> <span data-ttu-id="179aa-148">Vous devez ajouter les deux pour avoir `IsReadOnly` un struct.</span><span class="sxs-lookup"><span data-stu-id="179aa-148">You must add both to have an `IsReadOnly` struct.</span></span>

<span data-ttu-id="179aa-149">L’utilisation de cet attribut émet des F# métadonnées C# permettant de les traiter `inref<'T>` comme `in ref`et, respectivement.</span><span class="sxs-lookup"><span data-stu-id="179aa-149">Use of this attribute emits metadata letting F# and C# know to treat it as `inref<'T>` and `in ref`, respectively.</span></span>

<span data-ttu-id="179aa-150">La définition d’une valeur mutable à l’intérieur d’un struct ReadOnly génère une erreur.</span><span class="sxs-lookup"><span data-stu-id="179aa-150">Defining a mutable value inside of a readonly struct produces an error.</span></span>

## <a name="struct-records-and-discriminated-unions"></a><span data-ttu-id="179aa-151">Enregistrements de struct et unions discriminées</span><span class="sxs-lookup"><span data-stu-id="179aa-151">Struct Records and Discriminated Unions</span></span>

<span data-ttu-id="179aa-152">Vous pouvez représenter des [enregistrements](records.md) et des [unions discriminées](discriminated-unions.md) comme des `[<Struct>]` structs avec l’attribut.</span><span class="sxs-lookup"><span data-stu-id="179aa-152">You can represent [Records](records.md) and [Discriminated Unions](discriminated-unions.md) as structs with the `[<Struct>]` attribute.</span></span>  <span data-ttu-id="179aa-153">Pour en savoir plus, consultez chaque article.</span><span class="sxs-lookup"><span data-stu-id="179aa-153">See each article to learn more.</span></span>

## <a name="see-also"></a><span data-ttu-id="179aa-154">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="179aa-154">See also</span></span>

- [<span data-ttu-id="179aa-155">Informations de référence du langage F#</span><span class="sxs-lookup"><span data-stu-id="179aa-155">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="179aa-156">Classes</span><span class="sxs-lookup"><span data-stu-id="179aa-156">Classes</span></span>](classes.md)
- [<span data-ttu-id="179aa-157">Enregistrements</span><span class="sxs-lookup"><span data-stu-id="179aa-157">Records</span></span>](records.md)
- [<span data-ttu-id="179aa-158">Membres</span><span class="sxs-lookup"><span data-stu-id="179aa-158">Members</span></span>](./members/index.md)
