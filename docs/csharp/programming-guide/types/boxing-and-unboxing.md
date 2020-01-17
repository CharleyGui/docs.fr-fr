---
title: Boxing et unboxing - Guide de programmation C#
ms.date: 07/20/2015
f1_keywords:
- cs.boxing
helpviewer_keywords:
- C# language, boxing
- C# language, unboxing
- unboxing [C#]
- boxing [C#]
ms.assetid: 8da9bbf4-bce9-4b08-b2e5-f64c11c56514
ms.openlocfilehash: 32156ad0fe4b3dce4371fe757d15f5b8040aaf19
ms.sourcegitcommit: ed3f926b6cdd372037bbcc214dc8f08a70366390
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2020
ms.locfileid: "76115854"
---
# <a name="boxing-and-unboxing-c-programming-guide"></a><span data-ttu-id="4d166-102">Boxing et unboxing (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="4d166-102">Boxing and Unboxing (C# Programming Guide)</span></span>

<span data-ttu-id="4d166-103">Le boxing est la conversion d’un [type valeur](../../language-reference/keywords/value-types.md) en type `object` ou en un type interface implémenté par ce type valeur.</span><span class="sxs-lookup"><span data-stu-id="4d166-103">Boxing is the process of converting a [value type](../../language-reference/keywords/value-types.md) to the type `object` or to any interface type implemented by this value type.</span></span> <span data-ttu-id="4d166-104">Lorsque le common language runtime (CLR) convertit un type valeur, il encapsule la valeur à l’intérieur d’une instance <xref:System.Object?displayProperty=nameWithType> et la stocke sur le tas managé.</span><span class="sxs-lookup"><span data-stu-id="4d166-104">When the common language runtime (CLR) boxes a value type, it wraps the value inside a <xref:System.Object?displayProperty=nameWithType> instance and stores it on the managed heap.</span></span> <span data-ttu-id="4d166-105">L'unboxing extrait le type valeur de l'objet.</span><span class="sxs-lookup"><span data-stu-id="4d166-105">Unboxing extracts the value type from the object.</span></span> <span data-ttu-id="4d166-106">La conversion boxing est implicite ; la conversion unboxing est explicite.</span><span class="sxs-lookup"><span data-stu-id="4d166-106">Boxing is implicit; unboxing is explicit.</span></span> <span data-ttu-id="4d166-107">Le concept de boxing et de unboxing repose sur la vue unifiée par C# du système de type, dans lequel une valeur de n'importe quel type peut être traitée en tant qu'objet.</span><span class="sxs-lookup"><span data-stu-id="4d166-107">The concept of boxing and unboxing underlies the C# unified view of the type system in which a value of any type can be treated as an object.</span></span>

<span data-ttu-id="4d166-108">Dans l’exemple suivant, la variable de type entier `i` est convertie (*boxed*) et assignée à l’objet `o`.</span><span class="sxs-lookup"><span data-stu-id="4d166-108">In the following example, the integer variable `i` is *boxed* and assigned to object `o`.</span></span>

[!code-csharp[csProgGuideTypes#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#14)]

<span data-ttu-id="4d166-109">L’objet `o` peut ensuite être unboxed et assigné à la variable de type entier `i` :</span><span class="sxs-lookup"><span data-stu-id="4d166-109">The object `o` can then be unboxed and assigned to integer variable `i`:</span></span>

[!code-csharp[csProgGuideTypes#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#15)]

<span data-ttu-id="4d166-110">Les exemples suivants montrent comment le boxing est utilisé dans C#.</span><span class="sxs-lookup"><span data-stu-id="4d166-110">The following examples illustrate how boxing is used in C#.</span></span>

[!code-csharp[csProgGuideTypes#47](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#47)]

## <a name="performance"></a><span data-ttu-id="4d166-111">Performances</span><span class="sxs-lookup"><span data-stu-id="4d166-111">Performance</span></span>

<span data-ttu-id="4d166-112">Par rapport aux assignations simples, le boxing et l'unboxing sont des processus qui coûtent cher en calcul.</span><span class="sxs-lookup"><span data-stu-id="4d166-112">In relation to simple assignments, boxing and unboxing are computationally expensive processes.</span></span> <span data-ttu-id="4d166-113">Lorsqu'un type valeur est boxed, un nouvel objet doit être alloué et construit.</span><span class="sxs-lookup"><span data-stu-id="4d166-113">When a value type is boxed, a new object must be allocated and constructed.</span></span> <span data-ttu-id="4d166-114">À un degré moindre, le cast requis pour l'unboxing coûte également cher en calcul.</span><span class="sxs-lookup"><span data-stu-id="4d166-114">To a lesser degree, the cast required for unboxing is also expensive computationally.</span></span> <span data-ttu-id="4d166-115">Pour plus d’informations, consultez [Performances](../../../framework/performance/performance-tips.md).</span><span class="sxs-lookup"><span data-stu-id="4d166-115">For more information, see [Performance](../../../framework/performance/performance-tips.md).</span></span>

## <a name="boxing"></a><span data-ttu-id="4d166-116">Boxing</span><span class="sxs-lookup"><span data-stu-id="4d166-116">Boxing</span></span>

<span data-ttu-id="4d166-117">Le boxing est utilisé pour stocker des types valeur dans le tas rassemblé par garbage collection.</span><span class="sxs-lookup"><span data-stu-id="4d166-117">Boxing is used to store value types in the garbage-collected heap.</span></span> <span data-ttu-id="4d166-118">Le boxing est une conversion implicite d’un [type valeur](../../language-reference/keywords/value-types.md) en type `object` ou en un type interface implémenté par ce type valeur.</span><span class="sxs-lookup"><span data-stu-id="4d166-118">Boxing is an implicit conversion of a [value type](../../language-reference/keywords/value-types.md) to the type `object` or to any interface type implemented by this value type.</span></span> <span data-ttu-id="4d166-119">Le boxing d'un type valeur alloue une instance d'objet sur le tas et copie la valeur dans le nouvel objet.</span><span class="sxs-lookup"><span data-stu-id="4d166-119">Boxing a value type allocates an object instance on the heap and copies the value into the new object.</span></span>

<span data-ttu-id="4d166-120">Dans l'exemple suivant, une variable de type valeur est déclarée :</span><span class="sxs-lookup"><span data-stu-id="4d166-120">Consider the following declaration of a value-type variable:</span></span>

[!code-csharp[csProgGuideTypes#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#17)]

<span data-ttu-id="4d166-121">L'instruction ci-dessous réalise implicitement une opération de boxing sur la variable `i` :</span><span class="sxs-lookup"><span data-stu-id="4d166-121">The following statement implicitly applies the boxing operation on the variable `i`:</span></span>

[!code-csharp[csProgGuideTypes#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#18)]

<span data-ttu-id="4d166-122">Le résultat de cette instruction crée, sur la pile, un objet `o` qui fait référence à une valeur de type `int` sur le tas.</span><span class="sxs-lookup"><span data-stu-id="4d166-122">The result of this statement is creating an object reference `o`, on the stack, that references a value of the type `int`, on the heap.</span></span> <span data-ttu-id="4d166-123">Cette valeur est une copie de la valeur de type valeur qui a été assignée à la variable `i`.</span><span class="sxs-lookup"><span data-stu-id="4d166-123">This value is a copy of the value-type value assigned to the variable `i`.</span></span> <span data-ttu-id="4d166-124">La différence entre les deux variables, `i` et `o`, est illustrée dans l’image de conversion boxing ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="4d166-124">The difference between the two variables, `i` and `o`, is illustrated in the following image of boxing conversion:</span></span>

![Graphique illustrant la différence entre les variables i et o.](./media/boxing-and-unboxing/boxing-operation-i-o-variables.gif)

<span data-ttu-id="4d166-126">Il est également possible, mais jamais obligatoire, d'effectuer un boxing explicite comme dans l'exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="4d166-126">It is also possible to perform the boxing explicitly as in the following example, but explicit boxing is never required:</span></span>

[!code-csharp[csProgGuideTypes#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#19)]

## <a name="description"></a><span data-ttu-id="4d166-127">Description</span><span class="sxs-lookup"><span data-stu-id="4d166-127">Description</span></span>

<span data-ttu-id="4d166-128">Cet exemple utilise le boxing pour convertir une variable `i` (entier) en un objet `o`.</span><span class="sxs-lookup"><span data-stu-id="4d166-128">This example converts an integer variable `i` to an object `o` by using boxing.</span></span> <span data-ttu-id="4d166-129">Ensuite, la valeur `i` stockée dans la variable `123` est remplacée par la valeur `456`.</span><span class="sxs-lookup"><span data-stu-id="4d166-129">Then, the value stored in the variable `i` is changed from `123` to `456`.</span></span> <span data-ttu-id="4d166-130">L'exemple montre que le type valeur d'origine et que l'objet boxed utilisent des emplacements de mémoire distincts et peuvent, par conséquent, stocker des valeurs différentes.</span><span class="sxs-lookup"><span data-stu-id="4d166-130">The example shows that the original value type and the boxed object use separate memory locations, and therefore can store different values.</span></span>

## <a name="example"></a><span data-ttu-id="4d166-131">Exemple</span><span class="sxs-lookup"><span data-stu-id="4d166-131">Example</span></span>

[!code-csharp[csProgGuideTypes#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#16)]

## <a name="unboxing"></a><span data-ttu-id="4d166-132">Unboxing</span><span class="sxs-lookup"><span data-stu-id="4d166-132">Unboxing</span></span>

<span data-ttu-id="4d166-133">L’unboxing est une conversion explicite du type `object` en un [type valeur](../../language-reference/keywords/value-types.md), ou d’un type interface en un type valeur qui implémente l’interface.</span><span class="sxs-lookup"><span data-stu-id="4d166-133">Unboxing is an explicit conversion from the type `object` to a [value type](../../language-reference/keywords/value-types.md) or from an interface type to a value type that implements the interface.</span></span> <span data-ttu-id="4d166-134">Une opération d'unboxing comprend les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="4d166-134">An unboxing operation consists of:</span></span>

- <span data-ttu-id="4d166-135">Vérification de l'instance de l'objet pour s'assurer qu'il s'agit bien d'une valeur boxed du type valeur spécifié.</span><span class="sxs-lookup"><span data-stu-id="4d166-135">Checking the object instance to make sure that it is a boxed value of the given value type.</span></span>

- <span data-ttu-id="4d166-136">Copie de la valeur de l'instance dans la variable de type valeur.</span><span class="sxs-lookup"><span data-stu-id="4d166-136">Copying the value from the instance into the value-type variable.</span></span>

<span data-ttu-id="4d166-137">Les instructions suivantes expliquent les opérations de boxing et d'unboxing :</span><span class="sxs-lookup"><span data-stu-id="4d166-137">The following statements demonstrate both boxing and unboxing operations:</span></span>

[!code-csharp[csProgGuideTypes#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#21)]

<span data-ttu-id="4d166-138">L’illustration suivante montre le résultat de ces instructions :</span><span class="sxs-lookup"><span data-stu-id="4d166-138">The following figure demonstrates the result of the previous statements:</span></span>

![Image illustrant une conversion unboxing.](./media/boxing-and-unboxing/unboxing-conversion-operation.gif)

<span data-ttu-id="4d166-140">Pour que l'unboxing de types valeur réussisse au moment de l'exécution, l'élément qui est unboxed doit être une référence à un objet précédemment créé par boxing d'une instance de ce type valeur.</span><span class="sxs-lookup"><span data-stu-id="4d166-140">For the unboxing of value types to succeed at run time, the item being unboxed must be a reference to an object that was previously created by boxing an instance of that value type.</span></span> <span data-ttu-id="4d166-141">La tentative d'extraction de `null` provoque un <xref:System.NullReferenceException>.</span><span class="sxs-lookup"><span data-stu-id="4d166-141">Attempting to unbox `null` causes a <xref:System.NullReferenceException>.</span></span> <span data-ttu-id="4d166-142">La tentative d'extraction d'une référence vers un type de valeur incompatible provoque un <xref:System.InvalidCastException>.</span><span class="sxs-lookup"><span data-stu-id="4d166-142">Attempting to unbox a reference to an incompatible value type causes an <xref:System.InvalidCastException>.</span></span>

## <a name="example"></a><span data-ttu-id="4d166-143">Exemple</span><span class="sxs-lookup"><span data-stu-id="4d166-143">Example</span></span>

<span data-ttu-id="4d166-144">L'exemple suivant montre un cas d'unboxing non valide et l'`InvalidCastException` qui en résulte.</span><span class="sxs-lookup"><span data-stu-id="4d166-144">The following example demonstrates a case of invalid unboxing and the resulting `InvalidCastException`.</span></span> <span data-ttu-id="4d166-145">Avec `try` et `catch`, un message d'erreur est affiché lorsque l'erreur se produit.</span><span class="sxs-lookup"><span data-stu-id="4d166-145">Using `try` and `catch`, an error message is displayed when the error occurs.</span></span>

[!code-csharp[csProgGuideTypes#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#20)]

<span data-ttu-id="4d166-146">Sortie de ce programme :</span><span class="sxs-lookup"><span data-stu-id="4d166-146">This program outputs:</span></span>

`Specified cast is not valid. Error: Incorrect unboxing.`

<span data-ttu-id="4d166-147">Si vous modifiez l'instruction :</span><span class="sxs-lookup"><span data-stu-id="4d166-147">If you change the statement:</span></span>

```csharp
int j = (short) o;
```

<span data-ttu-id="4d166-148">à :</span><span class="sxs-lookup"><span data-stu-id="4d166-148">to:</span></span>

```csharp
int j = (int) o;
```

<span data-ttu-id="4d166-149">la conversion sera réalisée, avec le résultat suivant :</span><span class="sxs-lookup"><span data-stu-id="4d166-149">the conversion will be performed, and you will get the output:</span></span>

`Unboxing OK.`

## <a name="c-language-specification"></a><span data-ttu-id="4d166-150">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="4d166-150">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="related-sections"></a><span data-ttu-id="4d166-151">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="4d166-151">Related sections</span></span>

<span data-ttu-id="4d166-152">Pour plus d'informations, consultez .</span><span class="sxs-lookup"><span data-stu-id="4d166-152">For more information:</span></span>

- [<span data-ttu-id="4d166-153">Types référence</span><span class="sxs-lookup"><span data-stu-id="4d166-153">Reference Types</span></span>](../../language-reference/keywords/reference-types.md)

- [<span data-ttu-id="4d166-154">Types valeur</span><span class="sxs-lookup"><span data-stu-id="4d166-154">Value Types</span></span>](../../language-reference/keywords/value-types.md)

## <a name="see-also"></a><span data-ttu-id="4d166-155">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4d166-155">See also</span></span>

- [<span data-ttu-id="4d166-156">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="4d166-156">C# Programming Guide</span></span>](../index.md)
