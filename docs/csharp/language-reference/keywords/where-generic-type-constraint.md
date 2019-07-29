---
title: where (contrainte de type générique) - Référence C#
ms.custom: seodec18
ms.date: 04/12/2018
f1_keywords:
- whereconstraint
- whereconstraint_CSharpKeyword
helpviewer_keywords:
- where (generic type constraint) [C#]
ms.openlocfilehash: bccc22f5362b22540dadf08e6b21a07cbc578327
ms.sourcegitcommit: 1e7ac70be1b4d89708c0d9552897515f2cbf52c4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68433864"
---
# <a name="where-generic-type-constraint-c-reference"></a><span data-ttu-id="99f18-102">where (contrainte de type générique) (Référence C#)</span><span class="sxs-lookup"><span data-stu-id="99f18-102">where (generic type constraint) (C# Reference)</span></span>

<span data-ttu-id="99f18-103">La clause `where` dans une définition générique spécifie des contraintes sur les types qui sont utilisés comme arguments pour les paramètres de type d’un type générique, d’une méthode, d’un délégué ou d’une fonction locale.</span><span class="sxs-lookup"><span data-stu-id="99f18-103">The `where` clause in a generic definition specifies constraints on the types that are used as arguments for type parameters in a generic type, method, delegate, or local function.</span></span> <span data-ttu-id="99f18-104">Les contraintes peuvent spécifier des interfaces ou des classes de base, ou nécessiter un type générique comme référence, valeur ou type non managé.</span><span class="sxs-lookup"><span data-stu-id="99f18-104">Constraints can specify interfaces, base classes, or require a generic type to be a reference, value or unmanaged type.</span></span> <span data-ttu-id="99f18-105">Elles déclarent des fonctionnalités que l’argument de type doit posséder.</span><span class="sxs-lookup"><span data-stu-id="99f18-105">They declare capabilities that the type argument must possess.</span></span>

<span data-ttu-id="99f18-106">Vous pouvez, par exemple, déclarer une classe générique, `MyGenericClass`, de telle sorte que le paramètre de type `T` implémente l’interface <xref:System.IComparable%601> :</span><span class="sxs-lookup"><span data-stu-id="99f18-106">For example, you can declare a generic class, `MyGenericClass`, such that the type parameter `T` implements the <xref:System.IComparable%601> interface:</span></span>

[!code-csharp[using an interface constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#1)]

> [!NOTE]
> <span data-ttu-id="99f18-107">Pour plus d’informations sur la clause where dans une expression de requête, consultez [where, clause](where-clause.md).</span><span class="sxs-lookup"><span data-stu-id="99f18-107">For more information on the where clause in a query expression, see [where clause](where-clause.md).</span></span>

<span data-ttu-id="99f18-108">La clause `where` peut également inclure une contrainte de classe de base.</span><span class="sxs-lookup"><span data-stu-id="99f18-108">The `where` clause can also include a base class constraint.</span></span> <span data-ttu-id="99f18-109">La contrainte de classe de base indique qu’un type à utiliser comme argument de type pour ce type générique a la classe spécifiée comme classe de base (ou est la classe de base) à utiliser comme argument de type pour ce type générique.</span><span class="sxs-lookup"><span data-stu-id="99f18-109">The base class constraint states that a type to be used as a type argument for that generic type has the specified class as a base class (or is that base class) to be used as a type argument for that generic type.</span></span> <span data-ttu-id="99f18-110">Si la contrainte de classe de base est utilisée, elle doit apparaître avant toute autre contrainte sur ce paramètre de type.</span><span class="sxs-lookup"><span data-stu-id="99f18-110">If the base class constraint is used, it must appear before any other constraints on that type parameter.</span></span> <span data-ttu-id="99f18-111">Certains types ne sont pas autorisés comme contrainte de classe de base : <xref:System.Object>, <xref:System.Array> et <xref:System.ValueType>.</span><span class="sxs-lookup"><span data-stu-id="99f18-111">Some types are disallowed as a base class constraint: <xref:System.Object>, <xref:System.Array>, and <xref:System.ValueType>.</span></span> <span data-ttu-id="99f18-112">Avant C# 7.3, <xref:System.Enum>, <xref:System.Delegate> et <xref:System.MulticastDelegate> n’étaient pas non plus autorisés comme contraintes de classe de base.</span><span class="sxs-lookup"><span data-stu-id="99f18-112">Prior to C# 7.3, <xref:System.Enum>, <xref:System.Delegate>, and <xref:System.MulticastDelegate> were also disallowed as base class constraints.</span></span> <span data-ttu-id="99f18-113">L’exemple suivant montre les types qui peuvent maintenant être spécifiés comme classe de base :</span><span class="sxs-lookup"><span data-stu-id="99f18-113">The following example shows the types that can now be specified as a base class:</span></span>

[!code-csharp[using an interface constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#2)]

<span data-ttu-id="99f18-114">La clause `where` peut spécifier que le type est une `class` ou un `struct`.</span><span class="sxs-lookup"><span data-stu-id="99f18-114">The `where` clause can specify that the type is a `class` or a `struct`.</span></span> <span data-ttu-id="99f18-115">La contrainte `struct` supprime la nécessité de spécifier une contrainte de classe de base de `System.ValueType`.</span><span class="sxs-lookup"><span data-stu-id="99f18-115">The `struct` constraint removes the need to specify a base class constraint of `System.ValueType`.</span></span> <span data-ttu-id="99f18-116">Le type `System.ValueType` ne doit pas être utilisé comme contrainte de classe de base.</span><span class="sxs-lookup"><span data-stu-id="99f18-116">The `System.ValueType` type may not be used as a base class constraint.</span></span> <span data-ttu-id="99f18-117">L’exemple suivant montre les contraintes `class` et `struct` :</span><span class="sxs-lookup"><span data-stu-id="99f18-117">The following example shows both the `class` and `struct` constraints:</span></span>

[!code-csharp[using the class and struct constraints](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#3)]

<span data-ttu-id="99f18-118">La clause `where` peut aussi inclure une contrainte `unmanaged`.</span><span class="sxs-lookup"><span data-stu-id="99f18-118">The `where` clause may also include an `unmanaged` constraint.</span></span> <span data-ttu-id="99f18-119">La contrainte `unmanaged` limite le paramètre de type aux types connus sous le nom de [types non managés](../builtin-types/unmanaged-types.md).</span><span class="sxs-lookup"><span data-stu-id="99f18-119">The `unmanaged` constraint limits the type parameter to types known as [unmanaged types](../builtin-types/unmanaged-types.md).</span></span> <span data-ttu-id="99f18-120">La contrainte `unmanaged` facilite l’écriture de code interop de bas niveau en C#.</span><span class="sxs-lookup"><span data-stu-id="99f18-120">The `unmanaged` constraint makes it easier to write low-level interop code in C#.</span></span> <span data-ttu-id="99f18-121">Cette contrainte permet des routines réutilisables sur tous les types non managés.</span><span class="sxs-lookup"><span data-stu-id="99f18-121">This constraint enables reusable routines across all unmanaged types.</span></span> <span data-ttu-id="99f18-122">La contrainte `unmanaged` ne peut pas être combinée avec la contrainte `class` ou `struct`.</span><span class="sxs-lookup"><span data-stu-id="99f18-122">The `unmanaged` constraint can't be combined with the `class` or `struct` constraint.</span></span> <span data-ttu-id="99f18-123">La contrainte `unmanaged` exige que le type doit être un `struct` :</span><span class="sxs-lookup"><span data-stu-id="99f18-123">The `unmanaged` constraint enforces that the type must be a `struct`:</span></span>

[!code-csharp[using the unmanaged constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#4)]

<span data-ttu-id="99f18-124">La clause `where` peut également inclure une contrainte de constructeur, `new()`.</span><span class="sxs-lookup"><span data-stu-id="99f18-124">The `where` clause may also include a constructor constraint, `new()`.</span></span> <span data-ttu-id="99f18-125">Cette contrainte permet de créer une instance d’un paramètre de type à l’aide de l’opérateur `new`.</span><span class="sxs-lookup"><span data-stu-id="99f18-125">That constraint makes it possible to create an instance of a type parameter using the `new` operator.</span></span> <span data-ttu-id="99f18-126">La [contrainte new()](new-constraint.md) fait savoir au compilateur que tout argument de type fourni doit avoir un constructeur accessible sans paramètre, ou par défaut.</span><span class="sxs-lookup"><span data-stu-id="99f18-126">The [new() Constraint](new-constraint.md) lets the compiler know that any type argument supplied must have an accessible parameterless--or default-- constructor.</span></span> <span data-ttu-id="99f18-127">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="99f18-127">For example:</span></span>

[!code-csharp[using the new constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#5)]

<span data-ttu-id="99f18-128">La contrainte `new()` apparaît en dernier dans la clause `where`.</span><span class="sxs-lookup"><span data-stu-id="99f18-128">The `new()` constraint appears last in the `where` clause.</span></span> <span data-ttu-id="99f18-129">La contrainte `new()` ne peut pas être combinée avec les contraintes `struct` ou `unmanaged`.</span><span class="sxs-lookup"><span data-stu-id="99f18-129">The `new()` constraint can't be combined with the `struct` or `unmanaged` constraints.</span></span> <span data-ttu-id="99f18-130">Tous les types répondant à ces contraintes doivent avoir un constructeur sans paramètre accessible, ce qui rend la contrainte `new()` redondante.</span><span class="sxs-lookup"><span data-stu-id="99f18-130">All types satisfying those constraints must have an accessible parameterless constructor, making the `new()` constraint redundant.</span></span>

<span data-ttu-id="99f18-131">Avec plusieurs paramètres de type, utilisez une clause `where` pour chaque paramètre de type, par exemple :</span><span class="sxs-lookup"><span data-stu-id="99f18-131">With multiple type parameters, use one `where` clause for each type parameter, for example:</span></span>

[!code-csharp[using multiple where constraints](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#6)]

<span data-ttu-id="99f18-132">Vous pouvez également joindre des contraintes aux paramètres de type des méthodes génériques, comme montré dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="99f18-132">You can also attach constraints to type parameters of generic methods, as shown in the following example:</span></span>

[!code-csharp[where constraints with generic methods](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#7)]

<span data-ttu-id="99f18-133">Notez que la syntaxe décrivant les contraintes de paramètre de type sur les délégués est la même que celle des méthodes :</span><span class="sxs-lookup"><span data-stu-id="99f18-133">Notice that the syntax to describe type parameter constraints on delegates is the same as that of methods:</span></span>

[!code-csharp[where constraints with generic methods](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#8)]

<span data-ttu-id="99f18-134">Pour plus d’informations sur les délégués génériques, consultez [Délégués génériques](../../../csharp/programming-guide/generics/generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="99f18-134">For information on generic delegates, see [Generic Delegates](../../../csharp/programming-guide/generics/generic-delegates.md).</span></span>

<span data-ttu-id="99f18-135">Pour plus d’informations sur la syntaxe et l’utilisation de contraintes, consultez [Contraintes sur les paramètres de type](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="99f18-135">For details on the syntax and use of constraints, see [Constraints on Type Parameters](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="99f18-136">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="99f18-136">C# language specification</span></span>

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="99f18-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="99f18-137">See also</span></span>

- [<span data-ttu-id="99f18-138">Référence C#</span><span class="sxs-lookup"><span data-stu-id="99f18-138">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="99f18-139">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="99f18-139">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="99f18-140">Introduction aux génériques</span><span class="sxs-lookup"><span data-stu-id="99f18-140">Introduction to Generics</span></span>](../../../csharp/programming-guide/generics/index.md)
- [<span data-ttu-id="99f18-141">new, contrainte</span><span class="sxs-lookup"><span data-stu-id="99f18-141">new Constraint</span></span>](../../../csharp/language-reference/keywords/new-constraint.md)
- [<span data-ttu-id="99f18-142">Contraintes sur les paramètres de type</span><span class="sxs-lookup"><span data-stu-id="99f18-142">Constraints on Type Parameters</span></span>](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md)
