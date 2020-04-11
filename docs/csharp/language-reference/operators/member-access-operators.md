---
title: Opérateurs et expressions d’accès aux membres - Référence C
description: Découvrez les opérateurs C# que vous pouvez utiliser pour accéder aux membres de type.
ms.date: 03/31/2020
author: pkulikov
f1_keywords:
- ._CSharpKeyword
- '[]_CSharpKeyword'
- ()_CSharpKeyword
- ^_CSharpKeyword
- .._CSharpKeyword
helpviewer_keywords:
- member access operators [C#]
- member access operator [C#]
- dot operator [C#]
- . operator [C#]
- subscript operator [C#]
- square brackets [] operator [C#]
- indexer operator [C#]
- '[] operator [C#]'
- null-conditional operators [C#]
- Elvis operator [C#]
- ?. operator [C#]
- ?[] operator [C#]
- invocation operator [C#]
- method call [C#]
- method invocation [C#]
- delegate invocation [C#]
- () operator [C#]
- ^ operator [C#]
- index from end operator [C#]
- hat operator [C#]
- .. operator [C#]
- range operator [C#]
ms.openlocfilehash: 90066b1e9c219f66fc0c76423679e81aa3fa6770
ms.sourcegitcommit: 43cbde34970f5f38f30c43cd63b9c7e2e83717ae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/11/2020
ms.locfileid: "81120980"
---
# <a name="member-access-operators-and-expressions-c-reference"></a><span data-ttu-id="2401b-103">Opérateurs et expressions d’accès aux membres (référence C)</span><span class="sxs-lookup"><span data-stu-id="2401b-103">Member access operators and expressions (C# reference)</span></span>

<span data-ttu-id="2401b-104">Vous pouvez utiliser les opérateurs et expressions suivants lorsque vous accédez à un membre type :</span><span class="sxs-lookup"><span data-stu-id="2401b-104">You can use the following operators and expressions when you access a type member:</span></span>

- <span data-ttu-id="2401b-105">(accès des membres) : accéder à un membre d’un espace de nom ou d’un type [ `.` ](#member-access-expression-)</span><span class="sxs-lookup"><span data-stu-id="2401b-105">[`.` (member access)](#member-access-expression-): to access a member of a namespace or a type</span></span>
- <span data-ttu-id="2401b-106">[(accès à l’élément de tableau ou à l’indexeur) : accéder à un élément de tableau ou à un indexeur de type `[]` ](#indexer-operator-)</span><span class="sxs-lookup"><span data-stu-id="2401b-106">[`[]` (array element or indexer access)](#indexer-operator-): to access an array element or a type indexer</span></span>
- <span data-ttu-id="2401b-107">[et `?[]` (opérateurs non conditionnels) : effectuer une opération d’accès à un membre ou à un élément uniquement si un opérande n’est pas `?.` ](#null-conditional-operators--and-)nul</span><span class="sxs-lookup"><span data-stu-id="2401b-107">[`?.` and `?[]` (null-conditional operators)](#null-conditional-operators--and-): to perform a member or element access operation only if an operand is non-null</span></span>
- <span data-ttu-id="2401b-108">(invocation) : appeler une méthode consultée ou invoquer un délégué [ `()` ](#invocation-expression-)</span><span class="sxs-lookup"><span data-stu-id="2401b-108">[`()` (invocation)](#invocation-expression-): to call an accessed method or invoke a delegate</span></span>
- <span data-ttu-id="2401b-109">[(index à partir de la fin) : indiquer que la position de l’élément est à partir de la fin d’une séquence `^` ](#index-from-end-operator-)</span><span class="sxs-lookup"><span data-stu-id="2401b-109">[`^` (index from end)](#index-from-end-operator-): to indicate that the element position is from the end of a sequence</span></span>
- <span data-ttu-id="2401b-110">(gamme) : pour spécifier une gamme d’indices que vous pouvez utiliser pour obtenir une gamme d’éléments séquences [ `..` ](#range-operator-)</span><span class="sxs-lookup"><span data-stu-id="2401b-110">[`..` (range)](#range-operator-): to specify a range of indices that you can use to obtain a range of sequence elements</span></span>

## <a name="member-access-expression-"></a><span data-ttu-id="2401b-111">Expression d’accès des membres .</span><span class="sxs-lookup"><span data-stu-id="2401b-111">Member access expression .</span></span>

<span data-ttu-id="2401b-112">Le jeton `.` sert à accéder à l’un des membres d’un espace de noms ou d’un type, comme le montrent les exemples suivants :</span><span class="sxs-lookup"><span data-stu-id="2401b-112">You use the `.` token to access a member of a namespace or a type, as the following examples demonstrate:</span></span>

- <span data-ttu-id="2401b-113">Utiliser `.` pour accéder à un espace nom imbriqué dans [ `using` ](../keywords/using-directive.md) un espace nom, comme le montre l’exemple suivant d’une directive :</span><span class="sxs-lookup"><span data-stu-id="2401b-113">Use `.` to access a nested namespace within a namespace, as the following example of a [`using` directive](../keywords/using-directive.md) shows:</span></span>

  [!code-csharp[nested namespaces](snippets/MemberAccessOperators.cs#NestedNamespace)]

- <span data-ttu-id="2401b-114">Utilisez `.` pour former un *nom qualifié* permettant d’accéder à un type dans un espace de noms, comme le montre le code suivant :</span><span class="sxs-lookup"><span data-stu-id="2401b-114">Use `.` to form a *qualified name* to access a type within a namespace, as the following code shows:</span></span>

  [!code-csharp[qualified name](snippets/MemberAccessOperators.cs#QualifiedName)]

  <span data-ttu-id="2401b-115">Utilisez [ `using` ](../keywords/using-directive.md) une directive pour rendre facultatif l’utilisation de noms qualifiés.</span><span class="sxs-lookup"><span data-stu-id="2401b-115">Use a [`using` directive](../keywords/using-directive.md) to make the use of qualified names optional.</span></span>

- <span data-ttu-id="2401b-116">Utilisez `.` pour accéder aux [membres de type](../../programming-guide/classes-and-structs/index.md#members), statiques et non statiques, comme le montre le code suivant :</span><span class="sxs-lookup"><span data-stu-id="2401b-116">Use `.` to access [type members](../../programming-guide/classes-and-structs/index.md#members), static and non-static, as the following code shows:</span></span>

  [!code-csharp-interactive[type members](snippets/MemberAccessOperators.cs#TypeMemberAccess)]

<span data-ttu-id="2401b-117">Vous pouvez également utiliser `.` pour accéder à une [méthode d’extension](../../programming-guide/classes-and-structs/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="2401b-117">You can also use `.` to access an [extension method](../../programming-guide/classes-and-structs/extension-methods.md).</span></span>

## <a name="indexer-operator-"></a><span data-ttu-id="2401b-118">Opérateur d’indexeur []</span><span class="sxs-lookup"><span data-stu-id="2401b-118">Indexer operator []</span></span>

<span data-ttu-id="2401b-119">Les crochets, `[]`, sont généralement utilisés pour l’accès à un élément tableau, indexeur ou pointeur.</span><span class="sxs-lookup"><span data-stu-id="2401b-119">Square brackets, `[]`, are typically used for array, indexer, or pointer element access.</span></span>

### <a name="array-access"></a><span data-ttu-id="2401b-120">Accès aux tableaux</span><span class="sxs-lookup"><span data-stu-id="2401b-120">Array access</span></span>

<span data-ttu-id="2401b-121">L’exemple suivant montre comment accéder à des éléments tableau :</span><span class="sxs-lookup"><span data-stu-id="2401b-121">The following example demonstrates how to access array elements:</span></span>

[!code-csharp-interactive[array access](snippets/MemberAccessOperators.cs#Arrays)]

<span data-ttu-id="2401b-122">Si un index de tableau est en dehors des limites de la dimension correspondante d’un tableau, une <xref:System.IndexOutOfRangeException> est levée.</span><span class="sxs-lookup"><span data-stu-id="2401b-122">If an array index is outside the bounds of the corresponding dimension of an array, an <xref:System.IndexOutOfRangeException> is thrown.</span></span>

<span data-ttu-id="2401b-123">Comme le montre l’exemple précédent, vous utilisez également des crochets quand vous déclarez un type tableau ou instanciez une instance de tableau.</span><span class="sxs-lookup"><span data-stu-id="2401b-123">As the preceding example shows, you also use square brackets when you declare an array type or instantiate an array instance.</span></span>

<span data-ttu-id="2401b-124">Pour plus d’informations sur les tableaux, consultez [Tableaux](../../programming-guide/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="2401b-124">For more information about arrays, see [Arrays](../../programming-guide/arrays/index.md).</span></span>

### <a name="indexer-access"></a><span data-ttu-id="2401b-125">Accès aux indexeurs</span><span class="sxs-lookup"><span data-stu-id="2401b-125">Indexer access</span></span>

<span data-ttu-id="2401b-126">L’exemple suivant utilise <xref:System.Collections.Generic.Dictionary%602> le type .NET pour démontrer l’accès à l’indexeur :</span><span class="sxs-lookup"><span data-stu-id="2401b-126">The following example uses the .NET <xref:System.Collections.Generic.Dictionary%602> type to demonstrate indexer access:</span></span>

[!code-csharp-interactive[indexer access](snippets/MemberAccessOperators.cs#Indexers)]

<span data-ttu-id="2401b-127">Les indexeurs vous permettent d’indexer des instances d’un type défini par l’utilisateur en procédant de la même façon que pour l’indexation de tableau.</span><span class="sxs-lookup"><span data-stu-id="2401b-127">Indexers allow you to index instances of a user-defined type in the similar way as array indexing.</span></span> <span data-ttu-id="2401b-128">Contrairement aux indices de tableau, qui doivent être integer, les paramètres de l’indexeur peuvent être déclarés être de n’importe quel type.</span><span class="sxs-lookup"><span data-stu-id="2401b-128">Unlike array indices, which must be integer, the indexer parameters can be declared to be of any type.</span></span>

<span data-ttu-id="2401b-129">Pour plus d’informations sur les indexeurs, consultez [Indexeurs](../../programming-guide/indexers/index.md).</span><span class="sxs-lookup"><span data-stu-id="2401b-129">For more information about indexers, see [Indexers](../../programming-guide/indexers/index.md).</span></span>

### <a name="other-usages-of-"></a><span data-ttu-id="2401b-130">Autres utilisations de []</span><span class="sxs-lookup"><span data-stu-id="2401b-130">Other usages of []</span></span>

<span data-ttu-id="2401b-131">Pour plus d’informations concernant l’accès à l’élément de pointeur, consultez la section [Opérateur d’accès à l’élément de pointeur []](pointer-related-operators.md#pointer-element-access-operator-) de l’article [Opérateurs associés au pointeur](pointer-related-operators.md).</span><span class="sxs-lookup"><span data-stu-id="2401b-131">For information about pointer element access, see the [Pointer element access operator []](pointer-related-operators.md#pointer-element-access-operator-) section of the [Pointer related operators](pointer-related-operators.md) article.</span></span>

<span data-ttu-id="2401b-132">Vous utilisez également des crochets pour spécifier des [attributs](../../programming-guide/concepts/attributes/index.md) :</span><span class="sxs-lookup"><span data-stu-id="2401b-132">You also use square brackets to specify [attributes](../../programming-guide/concepts/attributes/index.md):</span></span>

```csharp
[System.Diagnostics.Conditional("DEBUG")]
void TraceMethod() {}
```

## <a name="null-conditional-operators--and-"></a><span data-ttu-id="2401b-133">Opérateurs conditionnels Null ?.</span><span class="sxs-lookup"><span data-stu-id="2401b-133">Null-conditional operators ?.</span></span> <span data-ttu-id="2401b-134">et ?[]</span><span class="sxs-lookup"><span data-stu-id="2401b-134">and ?[]</span></span>

<span data-ttu-id="2401b-135">Disponible en C 6 et plus tard, un opérateur `?.`sans condition `?[]`applique un accès de [membre,](#member-access-expression-), ou [l’accès à l’élément](#indexer-operator-), , opération à son opérande seulement si cet opérand évalue à non-null; sinon, il `null`revient .</span><span class="sxs-lookup"><span data-stu-id="2401b-135">Available in C# 6 and later, a null-conditional operator applies a [member access](#member-access-expression-), `?.`, or [element access](#indexer-operator-), `?[]`, operation to its operand only if that operand evaluates to non-null; otherwise, it returns `null`.</span></span> <span data-ttu-id="2401b-136">C'est</span><span class="sxs-lookup"><span data-stu-id="2401b-136">That is,</span></span>

- <span data-ttu-id="2401b-137">Si `a` évalue `null`à , `a?.x` le `a?[x]` `null`résultat ou est .</span><span class="sxs-lookup"><span data-stu-id="2401b-137">If `a` evaluates to `null`, the result of `a?.x` or `a?[x]` is `null`.</span></span>
- <span data-ttu-id="2401b-138">Si `a` l’on évalue à non-null, le résultat `a?.x` ou `a?[x]` est le même que le résultat ou `a.x` `a[x]`, respectivement.</span><span class="sxs-lookup"><span data-stu-id="2401b-138">If `a` evaluates to non-null, the result of `a?.x` or `a?[x]` is the same as the result of `a.x` or `a[x]`, respectively.</span></span>

  > [!NOTE]
  > <span data-ttu-id="2401b-139">Si `a.x` `a[x]` ou jette une `a?.x` `a?[x]` exception, ou jetterait la `a`même exception pour non-null .</span><span class="sxs-lookup"><span data-stu-id="2401b-139">If `a.x` or `a[x]` throws an exception, `a?.x` or `a?[x]` would throw the same exception for non-null `a`.</span></span> <span data-ttu-id="2401b-140">Par exemple, `a` si est une instance `x` de tableau non-null et est en dehors des limites de `a`, `a?[x]` jetterait un <xref:System.IndexOutOfRangeException>.</span><span class="sxs-lookup"><span data-stu-id="2401b-140">For example, if `a` is a non-null array instance and `x` is outside the bounds of `a`, `a?[x]` would throw an <xref:System.IndexOutOfRangeException>.</span></span>

<span data-ttu-id="2401b-141">Les opérateurs conditionnels Null ont un effet de court-circuit.</span><span class="sxs-lookup"><span data-stu-id="2401b-141">The null-conditional operators are short-circuiting.</span></span> <span data-ttu-id="2401b-142">Autrement dit, si une opération dans une chaîne d’opérations d’accès au membre ou à l’élément conditionnelles retourne une valeur `null`, le reste de la chaîne ne s’exécute pas.</span><span class="sxs-lookup"><span data-stu-id="2401b-142">That is, if one operation in a chain of conditional member or element access operations returns `null`, the rest of the chain doesn't execute.</span></span> <span data-ttu-id="2401b-143">Dans l’exemple suivant, `B` n’est pas évalué si `A` prend la valeur `null` et `C` n’est pas évalué si `A` ou `B` prend la valeur `null` :</span><span class="sxs-lookup"><span data-stu-id="2401b-143">In the following example, `B` is not evaluated if `A` evaluates to `null` and `C` is not evaluated if `A` or `B` evaluates to `null`:</span></span>

```csharp
A?.B?.Do(C);
A?.B?[C];
```

<span data-ttu-id="2401b-144">L’exemple suivant illustre l’utilisation des opérateurs `?.` et `?[]` :</span><span class="sxs-lookup"><span data-stu-id="2401b-144">The following example demonstrates the usage of the `?.` and `?[]` operators:</span></span>

[!code-csharp-interactive[null-conditional operators](snippets/MemberAccessOperators.cs#NullConditional)]

<span data-ttu-id="2401b-145">L’exemple précédent utilise également [l’opérateur `??` de fusion nulle](null-coalescing-operator.md) pour spécifier une expression `null`alternative à évaluer au cas où le résultat d’une opération non conditionnelle est .</span><span class="sxs-lookup"><span data-stu-id="2401b-145">The preceding example also uses the [null-coalescing operator `??`](null-coalescing-operator.md) to specify an alternative expression to evaluate in case the result of a null-conditional operation is `null`.</span></span>

<span data-ttu-id="2401b-146">Si `a.x` `a[x]` ou est d’un type `T` `a?.x` de `a?[x]` valeur non-nullable , ou est du [type](../builtin-types/nullable-value-types.md) `T?`de valeur nulle correspondante .</span><span class="sxs-lookup"><span data-stu-id="2401b-146">If `a.x` or `a[x]` is of a non-nullable value type `T`, `a?.x` or `a?[x]` is of the corresponding [nullable value type](../builtin-types/nullable-value-types.md) `T?`.</span></span> <span data-ttu-id="2401b-147">Si vous avez besoin `T`d’une expression de type, appliquez l’opérateur `??` de fusion nulle à une expression non conditionnelle, comme le montre l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="2401b-147">If you need an expression of type `T`, apply the null-coalescing operator `??` to a null-conditional expression, as the following example shows:</span></span>

[!code-csharp-interactive[null-conditional with null-coalescing](snippets/MemberAccessOperators.cs#NullConditionalWithNullCoalescing)]

<span data-ttu-id="2401b-148">Dans l’exemple précédent, si vous `??` n’utilisez pas l’opérateur, `numbers?.Length < 2` évalue à `false` quand `numbers` est `null`.</span><span class="sxs-lookup"><span data-stu-id="2401b-148">In the preceding example, if you don't use the `??` operator, `numbers?.Length < 2` evaluates to `false` when `numbers` is `null`.</span></span>

<span data-ttu-id="2401b-149">L’opérateur d’accès aux membres conditionnels null `?.` est également appelé l’opérateur Elvis.</span><span class="sxs-lookup"><span data-stu-id="2401b-149">The null-conditional member access operator `?.` is also known as the Elvis operator.</span></span>

### <a name="thread-safe-delegate-invocation"></a><span data-ttu-id="2401b-150">Appel de délégué thread-safe</span><span class="sxs-lookup"><span data-stu-id="2401b-150">Thread-safe delegate invocation</span></span>

<span data-ttu-id="2401b-151">Utilisez l’opérateur `?.` pour vérifier si un délégué est non Null et l’appeler de manière thread-safe (par exemple, quand vous [déclenchez un événement](../../../standard/events/how-to-raise-and-consume-events.md)), comme illustré dans le code suivant :</span><span class="sxs-lookup"><span data-stu-id="2401b-151">Use the `?.` operator to check if a delegate is non-null and invoke it in a thread-safe way (for example, when you [raise an event](../../../standard/events/how-to-raise-and-consume-events.md)), as the following code shows:</span></span>

```csharp
PropertyChanged?.Invoke(…)
```

<span data-ttu-id="2401b-152">Ce code est équivalent au code suivant que vous utiliseriez dans C# 5 ou une version antérieure :</span><span class="sxs-lookup"><span data-stu-id="2401b-152">That code is equivalent to the following code that you would use in C# 5 or earlier:</span></span>

```csharp
var handler = this.PropertyChanged;
if (handler != null)
{
    handler(…);
}
```

## <a name="invocation-expression-"></a><span data-ttu-id="2401b-153">Expression d’invocation ()</span><span class="sxs-lookup"><span data-stu-id="2401b-153">Invocation expression ()</span></span>

<span data-ttu-id="2401b-154">Utilisez des parenthèses, `()`, pour appeler une [méthode](../../programming-guide/classes-and-structs/methods.md) ou un [délégué](../../programming-guide/delegates/index.md).</span><span class="sxs-lookup"><span data-stu-id="2401b-154">Use parentheses, `()`, to call a [method](../../programming-guide/classes-and-structs/methods.md) or invoke a [delegate](../../programming-guide/delegates/index.md).</span></span>

<span data-ttu-id="2401b-155">L’exemple suivant montre comment appeler une méthode, avec ou sans arguments, et un délégué :</span><span class="sxs-lookup"><span data-stu-id="2401b-155">The following example demonstrates how to call a method, with or without arguments, and invoke a delegate:</span></span>

[!code-csharp-interactive[invocation with ()](snippets/MemberAccessOperators.cs#Invocation)]

<span data-ttu-id="2401b-156">Vous utilisez également des parenthèses quand vous appelez un [constructeur](../../programming-guide/classes-and-structs/constructors.md) avec l’opérateur [`new`](new-operator.md).</span><span class="sxs-lookup"><span data-stu-id="2401b-156">You also use parentheses when you invoke a [constructor](../../programming-guide/classes-and-structs/constructors.md) with the [`new`](new-operator.md) operator.</span></span>

### <a name="other-usages-of-"></a><span data-ttu-id="2401b-157">Autres utilisations de ()</span><span class="sxs-lookup"><span data-stu-id="2401b-157">Other usages of ()</span></span>

<span data-ttu-id="2401b-158">Vous utilisez également des parenthèses pour ajuster l’ordre dans lequel évaluer les opérations dans une expression.</span><span class="sxs-lookup"><span data-stu-id="2401b-158">You also use parentheses to adjust the order in which to evaluate operations in an expression.</span></span> <span data-ttu-id="2401b-159">Pour plus d’informations, consultez [Opérateurs C#](index.md).</span><span class="sxs-lookup"><span data-stu-id="2401b-159">For more information, see [C# operators](index.md).</span></span>

<span data-ttu-id="2401b-160">[Les expressions cast](type-testing-and-cast.md#cast-expression), qui effectuent des conversions de type explicites, utilisent aussi des parenthèses.</span><span class="sxs-lookup"><span data-stu-id="2401b-160">[Cast expressions](type-testing-and-cast.md#cast-expression), which perform explicit type conversions, also use parentheses.</span></span>

## <a name="index-from-end-operator-"></a><span data-ttu-id="2401b-161">Indice de l’opérateur final</span><span class="sxs-lookup"><span data-stu-id="2401b-161">Index from end operator ^</span></span>

<span data-ttu-id="2401b-162">Disponible en C 8.0 et `^` plus tard, l’opérateur indique la position de l’élément à partir de la fin d’une séquence.</span><span class="sxs-lookup"><span data-stu-id="2401b-162">Available in C# 8.0 and later, the `^` operator indicates the element position from the end of a sequence.</span></span> <span data-ttu-id="2401b-163">Pour une séquence `length` `^n` de longueur, pointe `length - n` vers l’élément avec décalage dès le début d’une séquence.</span><span class="sxs-lookup"><span data-stu-id="2401b-163">For a sequence of length `length`, `^n` points to the element with offset `length - n` from the start of a sequence.</span></span> <span data-ttu-id="2401b-164">Par exemple, `^1` indique le dernier élément `^length` d’une séquence et pointe vers le premier élément d’une séquence.</span><span class="sxs-lookup"><span data-stu-id="2401b-164">For example, `^1` points to the last element of a sequence and `^length` points to the first element of a sequence.</span></span>

[!code-csharp[index from end](snippets/MemberAccessOperators.cs#IndexFromEnd)]

<span data-ttu-id="2401b-165">Comme le montre l’exemple <xref:System.Index?displayProperty=nameWithType> précédent, l’expression `^e` est du genre.</span><span class="sxs-lookup"><span data-stu-id="2401b-165">As the preceding example shows, expression `^e` is of the <xref:System.Index?displayProperty=nameWithType> type.</span></span> <span data-ttu-id="2401b-166">En `^e`expression , `e` le résultat de `int`doit être implicitement convertible à .</span><span class="sxs-lookup"><span data-stu-id="2401b-166">In expression `^e`, the result of `e` must be implicitly convertible to `int`.</span></span>

<span data-ttu-id="2401b-167">Vous pouvez également `^` utiliser l’opérateur avec l’opérateur [de la gamme](#range-operator-) pour créer une gamme d’indices.</span><span class="sxs-lookup"><span data-stu-id="2401b-167">You also can use the `^` operator with the [range operator](#range-operator-) to create a range of indices.</span></span> <span data-ttu-id="2401b-168">Pour plus d’informations, voir [Indices et gammes](../../tutorials/ranges-indexes.md).</span><span class="sxs-lookup"><span data-stu-id="2401b-168">For more information, see [Indices and ranges](../../tutorials/ranges-indexes.md).</span></span>

## <a name="range-operator-"></a><span data-ttu-id="2401b-169">Opérateur de gamme ..</span><span class="sxs-lookup"><span data-stu-id="2401b-169">Range operator ..</span></span>

<span data-ttu-id="2401b-170">Disponible en C 8.0 et `..` plus tard, l’opérateur spécifie le début et la fin d’une gamme d’indices comme ses opérands.</span><span class="sxs-lookup"><span data-stu-id="2401b-170">Available in C# 8.0 and later, the `..` operator specifies the start and end of a range of indices as its operands.</span></span> <span data-ttu-id="2401b-171">L’opéra de gauche est un début de gamme *inclusif.*</span><span class="sxs-lookup"><span data-stu-id="2401b-171">The left-hand operand is an *inclusive* start of a range.</span></span> <span data-ttu-id="2401b-172">L’opéra de droite est une fin *exclusive* d’une gamme.</span><span class="sxs-lookup"><span data-stu-id="2401b-172">The right-hand operand is an *exclusive* end of a range.</span></span> <span data-ttu-id="2401b-173">L’un ou l’autre des opérandes peut être un index dès le début ou à partir de la fin d’une séquence, comme le montre l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="2401b-173">Either of operands can be an index from the start or from the end of a sequence, as the following example shows:</span></span>

[!code-csharp[range examples](snippets/MemberAccessOperators.cs#Ranges)]

<span data-ttu-id="2401b-174">Comme le montre l’exemple <xref:System.Range?displayProperty=nameWithType> précédent, l’expression `a..b` est du genre.</span><span class="sxs-lookup"><span data-stu-id="2401b-174">As the preceding example shows, expression `a..b` is of the <xref:System.Range?displayProperty=nameWithType> type.</span></span> <span data-ttu-id="2401b-175">En `a..b`expression, les `a` `b` résultats et doivent `int` être <xref:System.Index>implicitement convertibles ou .</span><span class="sxs-lookup"><span data-stu-id="2401b-175">In expression `a..b`, the results of `a` and `b` must be implicitly convertible to `int` or <xref:System.Index>.</span></span>

<span data-ttu-id="2401b-176">Vous pouvez omettre l’un `..` des opérands de l’opérateur pour obtenir une gamme ouverte :</span><span class="sxs-lookup"><span data-stu-id="2401b-176">You can omit any of the operands of the `..` operator to obtain an open-ended range:</span></span>

- <span data-ttu-id="2401b-177">`a..`est équivalent à`a..^0`</span><span class="sxs-lookup"><span data-stu-id="2401b-177">`a..` is equivalent to `a..^0`</span></span>
- <span data-ttu-id="2401b-178">`..b`est équivalent à`0..b`</span><span class="sxs-lookup"><span data-stu-id="2401b-178">`..b` is equivalent to `0..b`</span></span>
- <span data-ttu-id="2401b-179">`..`est équivalent à`0..^0`</span><span class="sxs-lookup"><span data-stu-id="2401b-179">`..` is equivalent to `0..^0`</span></span>

[!code-csharp[ranges with omitted operands](snippets/MemberAccessOperators.cs#RangesOptional)]

<span data-ttu-id="2401b-180">Pour plus d’informations, voir [Indices et gammes](../../tutorials/ranges-indexes.md).</span><span class="sxs-lookup"><span data-stu-id="2401b-180">For more information, see [Indices and ranges](../../tutorials/ranges-indexes.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="2401b-181">Capacité de surcharge de l’opérateur</span><span class="sxs-lookup"><span data-stu-id="2401b-181">Operator overloadability</span></span>

<span data-ttu-id="2401b-182">Le `.` `()`, `^`, `..` et les opérateurs ne peuvent pas être surchargés.</span><span class="sxs-lookup"><span data-stu-id="2401b-182">The `.`, `()`, `^`, and `..` operators cannot be overloaded.</span></span> <span data-ttu-id="2401b-183">L’opérateur `[]` est également considéré comme un opérateur non surchargeable.</span><span class="sxs-lookup"><span data-stu-id="2401b-183">The `[]` operator is also considered a non-overloadable operator.</span></span> <span data-ttu-id="2401b-184">Utilisez des [indexeurs](../../programming-guide/indexers/index.md) pour prendre en charge l’indexation avec des types définis par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="2401b-184">Use [indexers](../../programming-guide/indexers/index.md) to support indexing with user-defined types.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="2401b-185">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="2401b-185">C# language specification</span></span>

<span data-ttu-id="2401b-186">Pour plus d’informations, consultez les sections suivantes de la [spécification du langage C#](~/_csharplang/spec/introduction.md) :</span><span class="sxs-lookup"><span data-stu-id="2401b-186">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="2401b-187">Accès aux membres</span><span class="sxs-lookup"><span data-stu-id="2401b-187">Member access</span></span>](~/_csharplang/spec/expressions.md#member-access)
- [<span data-ttu-id="2401b-188">Accès aux éléments</span><span class="sxs-lookup"><span data-stu-id="2401b-188">Element access</span></span>](~/_csharplang/spec/expressions.md#element-access)
- [<span data-ttu-id="2401b-189">Opérateur conditionnel Null</span><span class="sxs-lookup"><span data-stu-id="2401b-189">Null-conditional operator</span></span>](~/_csharplang/spec/expressions.md#null-conditional-operator)
- [<span data-ttu-id="2401b-190">Expressions d’appels</span><span class="sxs-lookup"><span data-stu-id="2401b-190">Invocation expressions</span></span>](~/_csharplang/spec/expressions.md#invocation-expressions)

<span data-ttu-id="2401b-191">Pour plus d’informations sur les indices et les plages, voir la [note de proposition de fonctionnalité](~/_csharplang/proposals/csharp-8.0/ranges.md).</span><span class="sxs-lookup"><span data-stu-id="2401b-191">For more information about indices and ranges, see the [feature proposal note](~/_csharplang/proposals/csharp-8.0/ranges.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2401b-192">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2401b-192">See also</span></span>

- [<span data-ttu-id="2401b-193">Référence C#</span><span class="sxs-lookup"><span data-stu-id="2401b-193">C# reference</span></span>](../index.md)
- [<span data-ttu-id="2401b-194">Opérateurs CMD</span><span class="sxs-lookup"><span data-stu-id="2401b-194">C# operators</span></span>](index.md)
- [<span data-ttu-id="2401b-195">?? (opérateur de fusion Null)</span><span class="sxs-lookup"><span data-stu-id="2401b-195">?? (null-coalescing operator)</span></span>](null-coalescing-operator.md)
- [<span data-ttu-id="2401b-196">:: (opérateur)</span><span class="sxs-lookup"><span data-stu-id="2401b-196">:: operator</span></span>](namespace-alias-qualifier.md)
