---
title: Contraintes
description: En savoir plus sur F# contraintes qui s’appliquent aux paramètres de type générique pour spécifier la configuration requise pour un argument de type dans un type générique ou une fonction.
ms.date: 05/16/2016
ms.openlocfilehash: 1bf5c6fc4df6c8f2f7f969bd13030172c6b8aab9
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65645280"
---
# <a name="constraints"></a><span data-ttu-id="d0195-103">Contraintes</span><span class="sxs-lookup"><span data-stu-id="d0195-103">Constraints</span></span>

<span data-ttu-id="d0195-104">Cette rubrique décrit les contraintes que vous pouvez appliquer à générique paramètres pour spécifier la configuration requise pour un argument de type dans un type générique ou une fonction de type.</span><span class="sxs-lookup"><span data-stu-id="d0195-104">This topic describes constraints that you can apply to generic type parameters to specify the requirements for a type argument in a generic type or function.</span></span>

## <a name="syntax"></a><span data-ttu-id="d0195-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d0195-105">Syntax</span></span>

```fsharp
type-parameter-list when constraint1 [ and constraint2]
```

## <a name="remarks"></a><span data-ttu-id="d0195-106">Notes</span><span class="sxs-lookup"><span data-stu-id="d0195-106">Remarks</span></span>

<span data-ttu-id="d0195-107">Il existe plusieurs contraintes différentes que vous pouvez appliquer pour limiter les types qui peuvent être utilisés dans un type générique.</span><span class="sxs-lookup"><span data-stu-id="d0195-107">There are several different constraints you can apply to limit the types that can be used in a generic type.</span></span> <span data-ttu-id="d0195-108">Le tableau suivant répertorie et décrit ces contraintes.</span><span class="sxs-lookup"><span data-stu-id="d0195-108">The following table lists and describes these constraints.</span></span>

|<span data-ttu-id="d0195-109">Contrainte</span><span class="sxs-lookup"><span data-stu-id="d0195-109">Constraint</span></span>|<span data-ttu-id="d0195-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d0195-110">Syntax</span></span>|<span data-ttu-id="d0195-111">Description</span><span class="sxs-lookup"><span data-stu-id="d0195-111">Description</span></span>|
|----------|------|-----------|
|<span data-ttu-id="d0195-112">Contrainte de type</span><span class="sxs-lookup"><span data-stu-id="d0195-112">Type Constraint</span></span>|<span data-ttu-id="d0195-113">*paramètre de type* :&gt; *type*</span><span class="sxs-lookup"><span data-stu-id="d0195-113">*type-parameter* :&gt; *type*</span></span>|<span data-ttu-id="d0195-114">Le type fourni doit être égal à ou dérivé du type spécifié ou, si le type est une interface, le type fourni doit implémenter l’interface.</span><span class="sxs-lookup"><span data-stu-id="d0195-114">The provided type must be equal to or derived from the type specified, or, if the type is an interface, the provided type must implement the interface.</span></span>|
|<span data-ttu-id="d0195-115">Contrainte Null</span><span class="sxs-lookup"><span data-stu-id="d0195-115">Null Constraint</span></span>|<span data-ttu-id="d0195-116">*paramètre de type* : null</span><span class="sxs-lookup"><span data-stu-id="d0195-116">*type-parameter* : null</span></span>|<span data-ttu-id="d0195-117">Le type fourni doit prendre en charge le littéral null.</span><span class="sxs-lookup"><span data-stu-id="d0195-117">The provided type must support the null literal.</span></span> <span data-ttu-id="d0195-118">Cela inclut tous les types d’objets .NET, mais pas F# liste, tuple, function, classe, enregistrement ou les types d’union.</span><span class="sxs-lookup"><span data-stu-id="d0195-118">This includes all .NET object types but not F# list, tuple, function, class, record, or union types.</span></span>|
|<span data-ttu-id="d0195-119">Contrainte de membre explicite</span><span class="sxs-lookup"><span data-stu-id="d0195-119">Explicit Member Constraint</span></span>|<span data-ttu-id="d0195-120">[()]*paramètre de type* [ou... ou *paramètre de type*)] : (*signature de membre*)</span><span class="sxs-lookup"><span data-stu-id="d0195-120">[(]*type-parameter* [or ... or *type-parameter*)] : (*member-signature*)</span></span>|<span data-ttu-id="d0195-121">Au moins un des arguments de type fournis doit avoir un membre qui a la signature spécifiée ; pas prévu pour une utilisation courante.</span><span class="sxs-lookup"><span data-stu-id="d0195-121">At least one of the type arguments provided must have a member that has the specified signature; not intended for common use.</span></span> <span data-ttu-id="d0195-122">Membres doivent être soit explicitement définies sur le type ou une partie d’une extension de type implicite pour être des cibles valides pour une contrainte de membre explicite.</span><span class="sxs-lookup"><span data-stu-id="d0195-122">Members must be either explicitly defined on the type or part of an implicit type extension to be valid targets for an Explicit Member Constraint.</span></span>|
|<span data-ttu-id="d0195-123">Contrainte de constructeur</span><span class="sxs-lookup"><span data-stu-id="d0195-123">Constructor Constraint</span></span>|<span data-ttu-id="d0195-124">*paramètre de type* : (nouveau : unité -&gt; ' un)</span><span class="sxs-lookup"><span data-stu-id="d0195-124">*type-parameter* : ( new : unit -&gt; 'a )</span></span>|<span data-ttu-id="d0195-125">Le type fourni doit avoir un constructeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="d0195-125">The provided type must have a default constructor.</span></span>|
|<span data-ttu-id="d0195-126">Contrainte de Type valeur</span><span class="sxs-lookup"><span data-stu-id="d0195-126">Value Type Constraint</span></span>|<span data-ttu-id="d0195-127">: struct</span><span class="sxs-lookup"><span data-stu-id="d0195-127">: struct</span></span>|<span data-ttu-id="d0195-128">Le type fourni doit être un type valeur .NET.</span><span class="sxs-lookup"><span data-stu-id="d0195-128">The provided type must be a .NET value type.</span></span>|
|<span data-ttu-id="d0195-129">Contrainte de Type référence</span><span class="sxs-lookup"><span data-stu-id="d0195-129">Reference Type Constraint</span></span>|<span data-ttu-id="d0195-130">: pas de struct</span><span class="sxs-lookup"><span data-stu-id="d0195-130">: not struct</span></span>|<span data-ttu-id="d0195-131">Le type fourni doit être un type référence .NET.</span><span class="sxs-lookup"><span data-stu-id="d0195-131">The provided type must be a .NET reference type.</span></span>|
|<span data-ttu-id="d0195-132">Contrainte de Type énumération</span><span class="sxs-lookup"><span data-stu-id="d0195-132">Enumeration Type Constraint</span></span>|<span data-ttu-id="d0195-133">: enum&lt;*underlying-type*&gt;</span><span class="sxs-lookup"><span data-stu-id="d0195-133">: enum&lt;*underlying-type*&gt;</span></span>|<span data-ttu-id="d0195-134">Le type fourni doit être un type énuméré qui a le type sous-jacent spécifié ; pas prévu pour une utilisation courante.</span><span class="sxs-lookup"><span data-stu-id="d0195-134">The provided type must be an enumerated type that has the specified underlying type; not intended for common use.</span></span>|
|<span data-ttu-id="d0195-135">Contrainte de délégué</span><span class="sxs-lookup"><span data-stu-id="d0195-135">Delegate Constraint</span></span>|<span data-ttu-id="d0195-136">: delegate&lt;*tuple-parameter-type*, *return-type*&gt;</span><span class="sxs-lookup"><span data-stu-id="d0195-136">: delegate&lt;*tuple-parameter-type*, *return-type*&gt;</span></span>|<span data-ttu-id="d0195-137">Le type fourni doit être un type délégué qui a les arguments spécifiés et retourner la valeur ; pas prévu pour une utilisation courante.</span><span class="sxs-lookup"><span data-stu-id="d0195-137">The provided type must be a delegate type that has the specified arguments and return value; not intended for common use.</span></span>|
|<span data-ttu-id="d0195-138">Contrainte de comparaison</span><span class="sxs-lookup"><span data-stu-id="d0195-138">Comparison Constraint</span></span>|<span data-ttu-id="d0195-139">: comparaison</span><span class="sxs-lookup"><span data-stu-id="d0195-139">: comparison</span></span>|<span data-ttu-id="d0195-140">Le type fourni doit prendre en charge la comparaison.</span><span class="sxs-lookup"><span data-stu-id="d0195-140">The provided type must support comparison.</span></span>|
|<span data-ttu-id="d0195-141">Contrainte d’égalité</span><span class="sxs-lookup"><span data-stu-id="d0195-141">Equality Constraint</span></span>|<span data-ttu-id="d0195-142">: l’égalité</span><span class="sxs-lookup"><span data-stu-id="d0195-142">: equality</span></span>|<span data-ttu-id="d0195-143">Le type fourni doit prendre en charge l’égalité.</span><span class="sxs-lookup"><span data-stu-id="d0195-143">The provided type must support equality.</span></span>|
|<span data-ttu-id="d0195-144">Contrainte non managée</span><span class="sxs-lookup"><span data-stu-id="d0195-144">Unmanaged Constraint</span></span>|<span data-ttu-id="d0195-145">: non managé</span><span class="sxs-lookup"><span data-stu-id="d0195-145">: unmanaged</span></span>|<span data-ttu-id="d0195-146">Le type fourni doit être un type non managé.</span><span class="sxs-lookup"><span data-stu-id="d0195-146">The provided type must be an unmanaged type.</span></span> <span data-ttu-id="d0195-147">Les types non managés sont soit certains types primitifs (`sbyte`, `byte`, `char`, `nativeint`, `unativeint`, `float32`, `float`, `int16`, `uint16`, `int32`, `uint32`, `int64`, `uint64`, ou `decimal`), types énumération, `nativeptr<_>`, ou une structure non générique dont les champs sont tous les types non managés.</span><span class="sxs-lookup"><span data-stu-id="d0195-147">Unmanaged types are either certain primitive types (`sbyte`, `byte`, `char`, `nativeint`, `unativeint`, `float32`, `float`, `int16`, `uint16`, `int32`, `uint32`, `int64`, `uint64`, or `decimal`), enumeration types, `nativeptr<_>`, or a non-generic structure whose fields are all unmanaged types.</span></span>|

<span data-ttu-id="d0195-148">Vous devez ajouter une contrainte lorsque votre code doit utiliser une fonctionnalité qui est disponible sur le type de contrainte, mais pas sur les types en général.</span><span class="sxs-lookup"><span data-stu-id="d0195-148">You have to add a constraint when your code has to use a feature that is available on the constraint type but not on types in general.</span></span> <span data-ttu-id="d0195-149">Par exemple, si vous utilisez la contrainte de type pour spécifier un type de classe, vous pouvez utiliser l’une des méthodes de cette classe dans la fonction générique ou d’un type.</span><span class="sxs-lookup"><span data-stu-id="d0195-149">For example, if you use the type constraint to specify a class type, you can use any one of the methods of that class in the generic function or type.</span></span>

<span data-ttu-id="d0195-150">Spécification de contraintes est parfois nécessaire lors de l’écriture des paramètres de type explicitement, parce que sans une contrainte, le compilateur n’a aucun moyen de vérifier que les fonctionnalités que vous utilisez seront disponibles sur n’importe quel type qui peut être fourni au moment de l’exécution pour le type paramètre.</span><span class="sxs-lookup"><span data-stu-id="d0195-150">Specifying constraints is sometimes required when writing type parameters explicitly, because without a constraint, the compiler has no way of verifying that the features that you are using will be available on any type that might be supplied at run time for the type parameter.</span></span>

<span data-ttu-id="d0195-151">Les contraintes plus courantes que vous utilisez dans F# code sont les contraintes de type qui spécifient des interfaces ou classes de base.</span><span class="sxs-lookup"><span data-stu-id="d0195-151">The most common constraints you use in F# code are type constraints that specify base classes or interfaces.</span></span> <span data-ttu-id="d0195-152">Les autres contraintes sont utilisés par le F# bibliothèque pour implémenter certaines fonctionnalités, telles que la contrainte de membre explicite, ce qui est utilisée pour implémenter la surcharge d’opérateur pour les opérateurs arithmétiques, ou est fournie principalement parce que F# prend en charge l’ensemble complet des contraintes qui est pris en charge par le common language runtime.</span><span class="sxs-lookup"><span data-stu-id="d0195-152">The other constraints are either used by the F# library to implement certain functionality, such as the explicit member constraint, which is used to implement operator overloading for arithmetic operators, or are provided mainly because F# supports the complete set of constraints that is supported by the common language runtime.</span></span>

<span data-ttu-id="d0195-153">Pendant le processus d’inférence de type, certaines contraintes sont déduits automatiquement par le compilateur.</span><span class="sxs-lookup"><span data-stu-id="d0195-153">During the type inference process, some constraints are inferred automatically by the compiler.</span></span> <span data-ttu-id="d0195-154">Par exemple, si vous utilisez le `+` opérateur dans une fonction, le compilateur déduit une contrainte de membre explicite sur les types de variables qui sont utilisés dans l’expression.</span><span class="sxs-lookup"><span data-stu-id="d0195-154">For example, if you use the `+` operator in a function, the compiler infers an explicit member constraint on variable types that are used in the expression.</span></span>

<span data-ttu-id="d0195-155">Le code suivant illustre quelques déclarations de contrainte.</span><span class="sxs-lookup"><span data-stu-id="d0195-155">The following code illustrates some constraint declarations.</span></span>

```fsharp
// Base Type Constraint
type Class1<'T when 'T :> System.Exception> =
class end

// Interface Type Constraint
type Class2<'T when 'T :> System.IComparable> = 
class end

// Null constraint
type Class3<'T when 'T : null> =
class end

// Member constraint with static member
type Class4<'T when 'T : (static member staticMethod1 : unit -> 'T) > =
class end

// Member constraint with instance member
type Class5<'T when 'T : (member Method1 : 'T -> int)> =
class end

// Member constraint with property
type Class6<'T when 'T : (member Property1 : int)> =
class end

// Constructor constraint
type Class7<'T when 'T : (new : unit -> 'T)>() =
member val Field = new 'T()

// Reference type constraint
type Class8<'T when 'T : not struct> =
class end

// Enumeration constraint with underlying value specified
type Class9<'T when 'T : enum<uint32>> =
class end

// 'T must implement IComparable, or be an array type with comparable
// elements, or be System.IntPtr or System.UIntPtr. Also, 'T must not have
// the NoComparison attribute.
type Class10<'T when 'T : comparison> =
class end

// 'T must support equality. This is true for any type that does not
// have the NoEquality attribute.
type Class11<'T when 'T : equality> =
class end

type Class12<'T when 'T : delegate<obj * System.EventArgs, unit>> =
class end

type Class13<'T when 'T : unmanaged> =
class end

// Member constraints with two type parameters
// Most often used with static type parameters in inline functions
let inline add(value1 : ^T when ^T : (static member (+) : ^T * ^T -> ^T), value2: ^T) =
value1 + value2

// ^T and ^U must support operator +
let inline heterogenousAdd(value1 : ^T when (^T or ^U) : (static member (+) : ^T * ^U -> ^T), value2 : ^U) =
value1 + value2

// If there are multiple constraints, use the and keyword to separate them.
type Class14<'T,'U when 'T : equality and 'U : equality> =
class end
```

## <a name="see-also"></a><span data-ttu-id="d0195-156">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d0195-156">See also</span></span>

- [<span data-ttu-id="d0195-157">Génériques</span><span class="sxs-lookup"><span data-stu-id="d0195-157">Generics</span></span>](index.md)
- [<span data-ttu-id="d0195-158">Contraintes</span><span class="sxs-lookup"><span data-stu-id="d0195-158">Constraints</span></span>](constraints.md)
