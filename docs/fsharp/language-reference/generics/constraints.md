---
title: Contraintes
description: En savoir F# plus sur les contraintes qui s’appliquent aux paramètres de type générique pour spécifier les conditions requises pour un argument de type dans un type ou une fonction générique.
ms.date: 05/16/2016
ms.openlocfilehash: 9912ba63138d893a7c616661dd2b1cbdbe51916c
ms.sourcegitcommit: 878ca7550b653114c3968ef8906da2b3e60e3c7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2019
ms.locfileid: "71736788"
---
# <a name="constraints"></a><span data-ttu-id="68642-103">Contraintes</span><span class="sxs-lookup"><span data-stu-id="68642-103">Constraints</span></span>

<span data-ttu-id="68642-104">Cette rubrique décrit les contraintes que vous pouvez appliquer aux paramètres de type générique pour spécifier les conditions requises pour un argument de type dans un type ou une fonction générique.</span><span class="sxs-lookup"><span data-stu-id="68642-104">This topic describes constraints that you can apply to generic type parameters to specify the requirements for a type argument in a generic type or function.</span></span>

## <a name="syntax"></a><span data-ttu-id="68642-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="68642-105">Syntax</span></span>

```fsharp
type-parameter-list when constraint1 [ and constraint2]
```

## <a name="remarks"></a><span data-ttu-id="68642-106">Notes</span><span class="sxs-lookup"><span data-stu-id="68642-106">Remarks</span></span>

<span data-ttu-id="68642-107">Vous pouvez appliquer plusieurs contraintes pour limiter les types qui peuvent être utilisés dans un type générique.</span><span class="sxs-lookup"><span data-stu-id="68642-107">There are several different constraints you can apply to limit the types that can be used in a generic type.</span></span> <span data-ttu-id="68642-108">Le tableau suivant répertorie et décrit ces contraintes.</span><span class="sxs-lookup"><span data-stu-id="68642-108">The following table lists and describes these constraints.</span></span>

|<span data-ttu-id="68642-109">Contrainte</span><span class="sxs-lookup"><span data-stu-id="68642-109">Constraint</span></span>|<span data-ttu-id="68642-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="68642-110">Syntax</span></span>|<span data-ttu-id="68642-111">Description</span><span class="sxs-lookup"><span data-stu-id="68642-111">Description</span></span>|
|----------|------|-----------|
|<span data-ttu-id="68642-112">Contrainte de type</span><span class="sxs-lookup"><span data-stu-id="68642-112">Type Constraint</span></span>|<span data-ttu-id="68642-113">*paramètre de type* : &gt; *type*</span><span class="sxs-lookup"><span data-stu-id="68642-113">*type-parameter* :&gt; *type*</span></span>|<span data-ttu-id="68642-114">Le type fourni doit être égal au ou dérivé du type spécifié, ou, si le type est une interface, le type fourni doit implémenter l’interface.</span><span class="sxs-lookup"><span data-stu-id="68642-114">The provided type must be equal to or derived from the type specified, or, if the type is an interface, the provided type must implement the interface.</span></span>|
|<span data-ttu-id="68642-115">Contrainte null</span><span class="sxs-lookup"><span data-stu-id="68642-115">Null Constraint</span></span>|<span data-ttu-id="68642-116">*paramètre de type* : null</span><span class="sxs-lookup"><span data-stu-id="68642-116">*type-parameter* : null</span></span>|<span data-ttu-id="68642-117">Le type fourni doit prendre en charge le littéral null.</span><span class="sxs-lookup"><span data-stu-id="68642-117">The provided type must support the null literal.</span></span> <span data-ttu-id="68642-118">Cela comprend tous les types d’objets .NET F# , mais pas les types de liste, de tuple, de fonction, de classe, d’enregistrement ou d’Union.</span><span class="sxs-lookup"><span data-stu-id="68642-118">This includes all .NET object types but not F# list, tuple, function, class, record, or union types.</span></span>|
|<span data-ttu-id="68642-119">Contrainte de membre explicite</span><span class="sxs-lookup"><span data-stu-id="68642-119">Explicit Member Constraint</span></span>|<span data-ttu-id="68642-120">[(]*paramètre de type* [ou... ou *paramètre de type*)] : (*signature de membre*)</span><span class="sxs-lookup"><span data-stu-id="68642-120">[(]*type-parameter* [or ... or *type-parameter*)] : (*member-signature*)</span></span>|<span data-ttu-id="68642-121">Au moins un des arguments de type fourni doit avoir un membre qui a la signature spécifiée ; non destiné à une utilisation courante.</span><span class="sxs-lookup"><span data-stu-id="68642-121">At least one of the type arguments provided must have a member that has the specified signature; not intended for common use.</span></span> <span data-ttu-id="68642-122">Les membres doivent être définis explicitement sur le type ou une partie d’une extension de type implicite comme des cibles valides pour une contrainte de membre explicite.</span><span class="sxs-lookup"><span data-stu-id="68642-122">Members must be either explicitly defined on the type or part of an implicit type extension to be valid targets for an Explicit Member Constraint.</span></span>|
|<span data-ttu-id="68642-123">Contrainte de constructeur</span><span class="sxs-lookup"><span data-stu-id="68642-123">Constructor Constraint</span></span>|<span data-ttu-id="68642-124">*paramètre de type* : (nouveau : unit-&gt; 'a)</span><span class="sxs-lookup"><span data-stu-id="68642-124">*type-parameter* : ( new : unit -&gt; 'a )</span></span>|<span data-ttu-id="68642-125">Le type fourni doit avoir un constructeur sans paramètre.</span><span class="sxs-lookup"><span data-stu-id="68642-125">The provided type must have a parameterless constructor.</span></span>|
|<span data-ttu-id="68642-126">Contrainte de type valeur</span><span class="sxs-lookup"><span data-stu-id="68642-126">Value Type Constraint</span></span>|<span data-ttu-id="68642-127">: struct</span><span class="sxs-lookup"><span data-stu-id="68642-127">: struct</span></span>|<span data-ttu-id="68642-128">Le type fourni doit être un type valeur .NET.</span><span class="sxs-lookup"><span data-stu-id="68642-128">The provided type must be a .NET value type.</span></span>|
|<span data-ttu-id="68642-129">Contrainte de type référence</span><span class="sxs-lookup"><span data-stu-id="68642-129">Reference Type Constraint</span></span>|<span data-ttu-id="68642-130">: non struct</span><span class="sxs-lookup"><span data-stu-id="68642-130">: not struct</span></span>|<span data-ttu-id="68642-131">Le type fourni doit être un type référence .NET.</span><span class="sxs-lookup"><span data-stu-id="68642-131">The provided type must be a .NET reference type.</span></span>|
|<span data-ttu-id="68642-132">Contrainte de type énumération</span><span class="sxs-lookup"><span data-stu-id="68642-132">Enumeration Type Constraint</span></span>|<span data-ttu-id="68642-133">: enum @ no__t-0 @no__t de*type sous-jacent*-2</span><span class="sxs-lookup"><span data-stu-id="68642-133">: enum&lt;*underlying-type*&gt;</span></span>|<span data-ttu-id="68642-134">Le type fourni doit être un type énuméré qui a le type sous-jacent spécifié ; non destiné à une utilisation courante.</span><span class="sxs-lookup"><span data-stu-id="68642-134">The provided type must be an enumerated type that has the specified underlying type; not intended for common use.</span></span>|
|<span data-ttu-id="68642-135">Déléguer la contrainte</span><span class="sxs-lookup"><span data-stu-id="68642-135">Delegate Constraint</span></span>|<span data-ttu-id="68642-136">: delegate&lt;*tuple-parameter-type*, *return-type*&gt;</span><span class="sxs-lookup"><span data-stu-id="68642-136">: delegate&lt;*tuple-parameter-type*, *return-type*&gt;</span></span>|<span data-ttu-id="68642-137">Le type fourni doit être un type délégué qui a les arguments et la valeur de retour spécifiés ; non destiné à une utilisation courante.</span><span class="sxs-lookup"><span data-stu-id="68642-137">The provided type must be a delegate type that has the specified arguments and return value; not intended for common use.</span></span>|
|<span data-ttu-id="68642-138">Contrainte de comparaison</span><span class="sxs-lookup"><span data-stu-id="68642-138">Comparison Constraint</span></span>|<span data-ttu-id="68642-139">: comparaison</span><span class="sxs-lookup"><span data-stu-id="68642-139">: comparison</span></span>|<span data-ttu-id="68642-140">Le type fourni doit prendre en charge la comparaison.</span><span class="sxs-lookup"><span data-stu-id="68642-140">The provided type must support comparison.</span></span>|
|<span data-ttu-id="68642-141">Contrainte d’égalité</span><span class="sxs-lookup"><span data-stu-id="68642-141">Equality Constraint</span></span>|<span data-ttu-id="68642-142">: égalité</span><span class="sxs-lookup"><span data-stu-id="68642-142">: equality</span></span>|<span data-ttu-id="68642-143">Le type fourni doit prendre en charge l’égalité.</span><span class="sxs-lookup"><span data-stu-id="68642-143">The provided type must support equality.</span></span>|
|<span data-ttu-id="68642-144">Contrainte non managée</span><span class="sxs-lookup"><span data-stu-id="68642-144">Unmanaged Constraint</span></span>|<span data-ttu-id="68642-145">: non managé</span><span class="sxs-lookup"><span data-stu-id="68642-145">: unmanaged</span></span>|<span data-ttu-id="68642-146">Le type fourni doit être un type non managé.</span><span class="sxs-lookup"><span data-stu-id="68642-146">The provided type must be an unmanaged type.</span></span> <span data-ttu-id="68642-147">Les types non managés sont soit certains types primitifs (`sbyte`, `byte`, `char`, `nativeint`, `unativeint`, `float32`, `float`, `int16`, `uint16`, `int32`, 0, 1, 2 ou 3), types énumération, 4 ou non générique structure dont les champs sont tous des types non managés.</span><span class="sxs-lookup"><span data-stu-id="68642-147">Unmanaged types are either certain primitive types (`sbyte`, `byte`, `char`, `nativeint`, `unativeint`, `float32`, `float`, `int16`, `uint16`, `int32`, `uint32`, `int64`, `uint64`, or `decimal`), enumeration types, `nativeptr<_>`, or a non-generic structure whose fields are all unmanaged types.</span></span>|

<span data-ttu-id="68642-148">Vous devez ajouter une contrainte lorsque votre code doit utiliser une fonctionnalité qui est disponible sur le type de contrainte, mais pas sur les types en général.</span><span class="sxs-lookup"><span data-stu-id="68642-148">You have to add a constraint when your code has to use a feature that is available on the constraint type but not on types in general.</span></span> <span data-ttu-id="68642-149">Par exemple, si vous utilisez la contrainte de type pour spécifier un type de classe, vous pouvez utiliser l’une des méthodes de cette classe dans la fonction ou le type générique.</span><span class="sxs-lookup"><span data-stu-id="68642-149">For example, if you use the type constraint to specify a class type, you can use any one of the methods of that class in the generic function or type.</span></span>

<span data-ttu-id="68642-150">La spécification de contraintes est parfois nécessaire lors de l’écriture explicite des paramètres de type, car sans contrainte, le compilateur n’a aucun moyen de vérifier que les fonctionnalités que vous utilisez seront disponibles sur tous les types susceptibles d’être fournis au moment de l’exécution pour le type paramètre.</span><span class="sxs-lookup"><span data-stu-id="68642-150">Specifying constraints is sometimes required when writing type parameters explicitly, because without a constraint, the compiler has no way of verifying that the features that you are using will be available on any type that might be supplied at run time for the type parameter.</span></span>

<span data-ttu-id="68642-151">Les contraintes les plus courantes que vous F# utilisez dans le code sont les contraintes de type qui spécifient des classes ou des interfaces de base.</span><span class="sxs-lookup"><span data-stu-id="68642-151">The most common constraints you use in F# code are type constraints that specify base classes or interfaces.</span></span> <span data-ttu-id="68642-152">Les autres contraintes sont utilisées par la F# bibliothèque pour implémenter certaines fonctionnalités, telles que la contrainte de membre explicite, qui est utilisée pour implémenter la surcharge d’opérateur pour les opérateurs arithmétiques, ou F# qui sont fournies principalement parce que prend en charge l’ensemble complet de contraintes qui est pris en charge par l’common language runtime.</span><span class="sxs-lookup"><span data-stu-id="68642-152">The other constraints are either used by the F# library to implement certain functionality, such as the explicit member constraint, which is used to implement operator overloading for arithmetic operators, or are provided mainly because F# supports the complete set of constraints that is supported by the common language runtime.</span></span>

<span data-ttu-id="68642-153">Pendant le processus d’inférence de type, certaines contraintes sont déduites automatiquement par le compilateur.</span><span class="sxs-lookup"><span data-stu-id="68642-153">During the type inference process, some constraints are inferred automatically by the compiler.</span></span> <span data-ttu-id="68642-154">Par exemple, si vous utilisez l’opérateur `+` dans une fonction, le compilateur déduit une contrainte de membre explicite sur les types de variable utilisés dans l’expression.</span><span class="sxs-lookup"><span data-stu-id="68642-154">For example, if you use the `+` operator in a function, the compiler infers an explicit member constraint on variable types that are used in the expression.</span></span>

<span data-ttu-id="68642-155">Le code suivant illustre certaines déclarations de contrainte :</span><span class="sxs-lookup"><span data-stu-id="68642-155">The following code illustrates some constraint declarations:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="68642-156">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="68642-156">See also</span></span>

- [<span data-ttu-id="68642-157">Génériques</span><span class="sxs-lookup"><span data-stu-id="68642-157">Generics</span></span>](index.md)
- [<span data-ttu-id="68642-158">Contraintes</span><span class="sxs-lookup"><span data-stu-id="68642-158">Constraints</span></span>](constraints.md)
