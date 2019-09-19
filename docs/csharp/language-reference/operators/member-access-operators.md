---
title: Opérateurs d’accès aux membres - Référence C#
description: Découvrez les opérateurs C# que vous pouvez utiliser pour accéder aux membres de type.
ms.date: 09/18/2019
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
ms.openlocfilehash: 45af31d10d77f4c63b27b34595b97fdd11ef95a1
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71116129"
---
# <a name="member-access-operators-c-reference"></a><span data-ttu-id="301eb-103">Opérateurs d’accès aux membres (référence C#)</span><span class="sxs-lookup"><span data-stu-id="301eb-103">Member access operators (C# reference)</span></span>

<span data-ttu-id="301eb-104">Vous pouvez utiliser les opérateurs suivants quand vous accédez à un membre de type :</span><span class="sxs-lookup"><span data-stu-id="301eb-104">You might use the following operators when you access a type member:</span></span>

- <span data-ttu-id="301eb-105">[`.` (accès aux membres)](#member-access-operator-) : accédez à un membre d’un espace de noms ou d’un type</span><span class="sxs-lookup"><span data-stu-id="301eb-105">[`.` (member access)](#member-access-operator-): to access a member of a namespace or a type</span></span>
- <span data-ttu-id="301eb-106">[`[]` (accès à un indexeur ou à un élément de tableau)](#indexer-operator-) : pour accéder à un élément de tableau ou à un indexeur de type</span><span class="sxs-lookup"><span data-stu-id="301eb-106">[`[]` (array element or indexer access)](#indexer-operator-): to access an array element or a type indexer</span></span>
- <span data-ttu-id="301eb-107">[`?.` et `?[]` (opérateurs conditionnels Null)](#null-conditional-operators--and-) : pour effectuer une opération d’accès à un membre ou élément uniquement si un opérande est non Null</span><span class="sxs-lookup"><span data-stu-id="301eb-107">[`?.` and `?[]` (null-conditional operators)](#null-conditional-operators--and-): to perform a member or element access operation only if an operand is non-null</span></span>
- <span data-ttu-id="301eb-108">[`()` (appel) ](#invocation-operator-) : pour appeler une méthode sollicitée ou appeler un délégué</span><span class="sxs-lookup"><span data-stu-id="301eb-108">[`()` (invocation)](#invocation-operator-): to call an accessed method or invoke a delegate</span></span>
- <span data-ttu-id="301eb-109">[(index à partir de la fin) : pour indiquer que la position de l’élément est à partir de la fin d’une séquence `^` ](#index-from-end-operator-)</span><span class="sxs-lookup"><span data-stu-id="301eb-109">[`^` (index from end)](#index-from-end-operator-): to indicate that the element position is from the end of a sequence</span></span>
- <span data-ttu-id="301eb-110">(plage) : pour spécifier une plage d’index que vous pouvez utiliser pour obtenir une plage d’éléments de séquence [ `..` ](#range-operator-)</span><span class="sxs-lookup"><span data-stu-id="301eb-110">[`..` (range)](#range-operator-): to specify a range of indices that you can use to obtain a range of sequence elements</span></span>

## <a name="member-access-operator-"></a><span data-ttu-id="301eb-111">Opérateur d’accès aux membres .</span><span class="sxs-lookup"><span data-stu-id="301eb-111">Member access operator .</span></span>

<span data-ttu-id="301eb-112">Le jeton `.` sert à accéder à l’un des membres d’un espace de noms ou d’un type, comme le montrent les exemples suivants :</span><span class="sxs-lookup"><span data-stu-id="301eb-112">You use the `.` token to access a member of a namespace or a type, as the following examples demonstrate:</span></span>

- <span data-ttu-id="301eb-113">Utilisez `.` pour accéder à un espace de noms imbriqué dans un autre, comme le montre l’exemple suivant avec la [directive `using`](../keywords/using-directive.md) :</span><span class="sxs-lookup"><span data-stu-id="301eb-113">Use `.` to access a nested namespace within a namespace, as the following example of a [`using` directive](../keywords/using-directive.md) shows:</span></span>

  [!code-csharp[nested namespaces](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#NestedNamespace)]

- <span data-ttu-id="301eb-114">Utilisez `.` pour former un *nom qualifié* permettant d’accéder à un type dans un espace de noms, comme le montre le code suivant :</span><span class="sxs-lookup"><span data-stu-id="301eb-114">Use `.` to form a *qualified name* to access a type within a namespace, as the following code shows:</span></span>

  [!code-csharp[qualified name](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#QualifiedName)]

  <span data-ttu-id="301eb-115">Utilisez une [directive `using`](../keywords/using-directive.md) pour rendre facultative l’utilisation de noms qualifiés.</span><span class="sxs-lookup"><span data-stu-id="301eb-115">Use a [`using` directive](../keywords/using-directive.md) to make the use of qualified names optional.</span></span>

- <span data-ttu-id="301eb-116">Utilisez `.` pour accéder aux [membres de type](../../programming-guide/classes-and-structs/index.md#members), statiques et non statiques, comme le montre le code suivant :</span><span class="sxs-lookup"><span data-stu-id="301eb-116">Use `.` to access [type members](../../programming-guide/classes-and-structs/index.md#members), static and non-static, as the following code shows:</span></span>

  [!code-csharp-interactive[type members](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#TypeMemberAccess)]

<span data-ttu-id="301eb-117">Vous pouvez également utiliser `.` pour accéder à une [méthode d’extension](../../programming-guide/classes-and-structs/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="301eb-117">You can also use `.` to access an [extension method](../../programming-guide/classes-and-structs/extension-methods.md).</span></span>

## <a name="indexer-operator-"></a><span data-ttu-id="301eb-118">Opérateur d’indexeur []</span><span class="sxs-lookup"><span data-stu-id="301eb-118">Indexer operator []</span></span>

<span data-ttu-id="301eb-119">Les crochets, `[]`, sont généralement utilisés pour l’accès à un élément tableau, indexeur ou pointeur.</span><span class="sxs-lookup"><span data-stu-id="301eb-119">Square brackets, `[]`, are typically used for array, indexer, or pointer element access.</span></span>

### <a name="array-access"></a><span data-ttu-id="301eb-120">Accès aux tableaux</span><span class="sxs-lookup"><span data-stu-id="301eb-120">Array access</span></span>

<span data-ttu-id="301eb-121">L’exemple suivant montre comment accéder à des éléments tableau :</span><span class="sxs-lookup"><span data-stu-id="301eb-121">The following example demonstrates how to access array elements:</span></span>

[!code-csharp-interactive[array access](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#Arrays)]

<span data-ttu-id="301eb-122">Si un index de tableau est en dehors des limites de la dimension correspondante d’un tableau, une <xref:System.IndexOutOfRangeException> est levée.</span><span class="sxs-lookup"><span data-stu-id="301eb-122">If an array index is outside the bounds of the corresponding dimension of an array, an <xref:System.IndexOutOfRangeException> is thrown.</span></span>

<span data-ttu-id="301eb-123">Comme le montre l’exemple précédent, vous utilisez également des crochets quand vous déclarez un type tableau ou instanciez une instance de tableau.</span><span class="sxs-lookup"><span data-stu-id="301eb-123">As the preceding example shows, you also use square brackets when you declare an array type or instantiate an array instance.</span></span>

<span data-ttu-id="301eb-124">Pour plus d’informations sur les tableaux, consultez [Tableaux](../../programming-guide/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="301eb-124">For more information about arrays, see [Arrays](../../programming-guide/arrays/index.md).</span></span>

### <a name="indexer-access"></a><span data-ttu-id="301eb-125">Accès aux indexeurs</span><span class="sxs-lookup"><span data-stu-id="301eb-125">Indexer access</span></span>

<span data-ttu-id="301eb-126">L’exemple suivant utilise le type .NET <xref:System.Collections.Generic.Dictionary%602> afin d’illustrer l’accès aux indexeurs :</span><span class="sxs-lookup"><span data-stu-id="301eb-126">The following example uses .NET <xref:System.Collections.Generic.Dictionary%602> type to demonstrate indexer access:</span></span>

[!code-csharp-interactive[indexer access](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#Indexers)]

<span data-ttu-id="301eb-127">Les indexeurs vous permettent d’indexer des instances d’un type défini par l’utilisateur en procédant de la même façon que pour l’indexation de tableau.</span><span class="sxs-lookup"><span data-stu-id="301eb-127">Indexers allow you to index instances of a user-defined type in the similar way as array indexing.</span></span> <span data-ttu-id="301eb-128">Contrairement aux index de tableau, qui doivent être des entiers, les arguments d’indexeur peuvent être déclarés comme étant de n’importe quel type.</span><span class="sxs-lookup"><span data-stu-id="301eb-128">Unlike array indices, which must be integer, the indexer arguments can be declared to be of any type.</span></span>

<span data-ttu-id="301eb-129">Pour plus d’informations sur les indexeurs, consultez [Indexeurs](../../programming-guide/indexers/index.md).</span><span class="sxs-lookup"><span data-stu-id="301eb-129">For more information about indexers, see [Indexers](../../programming-guide/indexers/index.md).</span></span>

### <a name="other-usages-of-"></a><span data-ttu-id="301eb-130">Autres utilisations de []</span><span class="sxs-lookup"><span data-stu-id="301eb-130">Other usages of []</span></span>

<span data-ttu-id="301eb-131">Pour plus d’informations concernant l’accès à l’élément de pointeur, consultez la section [Opérateur d’accès à l’élément de pointeur []](pointer-related-operators.md#pointer-element-access-operator-) de l’article [Opérateurs associés au pointeur](pointer-related-operators.md).</span><span class="sxs-lookup"><span data-stu-id="301eb-131">For information about pointer element access, see the [Pointer element access operator []](pointer-related-operators.md#pointer-element-access-operator-) section of the [Pointer related operators](pointer-related-operators.md) article.</span></span>

<span data-ttu-id="301eb-132">Vous utilisez également des crochets pour spécifier des [attributs](../../programming-guide/concepts/attributes/index.md) :</span><span class="sxs-lookup"><span data-stu-id="301eb-132">You also use square brackets to specify [attributes](../../programming-guide/concepts/attributes/index.md):</span></span>

```csharp
[System.Diagnostics.Conditional("DEBUG")]
void TraceMethod() {}
```

## <a name="null-conditional-operators--and-"></a><span data-ttu-id="301eb-133">Opérateurs conditionnels Null ?.</span><span class="sxs-lookup"><span data-stu-id="301eb-133">Null-conditional operators ?.</span></span> <span data-ttu-id="301eb-134">et ?[]</span><span class="sxs-lookup"><span data-stu-id="301eb-134">and ?[]</span></span>

<span data-ttu-id="301eb-135">Disponible dans C# 6 et versions ultérieures, un opérateur conditionnel Null applique une opération d’accès aux membres, `?.`, ou d’accès aux éléments, `?[]`, à son opérande uniquement si ce dernier a une valeur non Null.</span><span class="sxs-lookup"><span data-stu-id="301eb-135">Available in C# 6 and later, a null-conditional operator applies a member access, `?.`, or element access, `?[]`, operation to its operand only if that operand evaluates to non-null.</span></span> <span data-ttu-id="301eb-136">Si l’opérande a la valeur `null`, le résultat de l’application de l’opérateur est `null`.</span><span class="sxs-lookup"><span data-stu-id="301eb-136">If the operand evaluates to `null`, the result of applying the operator is `null`.</span></span> <span data-ttu-id="301eb-137">L’opérateur d’accès aux membres conditionnels null `?.` est également appelé l’opérateur Elvis.</span><span class="sxs-lookup"><span data-stu-id="301eb-137">The null-conditional member access operator `?.` is also known as the Elvis operator.</span></span>

<span data-ttu-id="301eb-138">Les opérateurs conditionnels Null ont un effet de court-circuit.</span><span class="sxs-lookup"><span data-stu-id="301eb-138">The null-conditional operators are short-circuiting.</span></span> <span data-ttu-id="301eb-139">Autrement dit, si une opération dans une chaîne d’opérations d’accès au membre ou à l’élément conditionnelles retourne une valeur `null`, le reste de la chaîne ne s’exécute pas.</span><span class="sxs-lookup"><span data-stu-id="301eb-139">That is, if one operation in a chain of conditional member or element access operations returns `null`, the rest of the chain doesn't execute.</span></span> <span data-ttu-id="301eb-140">Dans l’exemple suivant, `B` n’est pas évalué si `A` prend la valeur `null` et `C` n’est pas évalué si `A` ou `B` prend la valeur `null` :</span><span class="sxs-lookup"><span data-stu-id="301eb-140">In the following example, `B` is not evaluated if `A` evaluates to `null` and `C` is not evaluated if `A` or `B` evaluates to `null`:</span></span>

```csharp
A?.B?.Do(C);
A?.B?[C];
```

<span data-ttu-id="301eb-141">L’exemple suivant illustre l’utilisation des opérateurs `?.` et `?[]` :</span><span class="sxs-lookup"><span data-stu-id="301eb-141">The following example demonstrates the usage of the `?.` and `?[]` operators:</span></span>

[!code-csharp-interactive[null-conditional operators](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#NullConditional)]

<span data-ttu-id="301eb-142">L’exemple précédent illustre également l’utilisation de l’[opérateur de fusion Null](null-coalescing-operator.md).</span><span class="sxs-lookup"><span data-stu-id="301eb-142">The preceding example also shows the usage of the [null-coalescing operator](null-coalescing-operator.md).</span></span> <span data-ttu-id="301eb-143">Vous pouvez utiliser l’opérateur de fusion Null pour fournir une autre expression à évaluer au cas où le résultat de l’opération conditionnelle Null serait `null`.</span><span class="sxs-lookup"><span data-stu-id="301eb-143">You might use the null-coalescing operator to provide an alternative expression to evaluate in case the result of the null-conditional operation is `null`.</span></span>

### <a name="thread-safe-delegate-invocation"></a><span data-ttu-id="301eb-144">Appel de délégué thread-safe</span><span class="sxs-lookup"><span data-stu-id="301eb-144">Thread-safe delegate invocation</span></span>

<span data-ttu-id="301eb-145">Utilisez l’opérateur `?.` pour vérifier si un délégué est non Null et l’appeler de manière thread-safe (par exemple, quand vous [déclenchez un événement](../../../standard/events/how-to-raise-and-consume-events.md)), comme illustré dans le code suivant :</span><span class="sxs-lookup"><span data-stu-id="301eb-145">Use the `?.` operator to check if a delegate is non-null and invoke it in a thread-safe way (for example, when you [raise an event](../../../standard/events/how-to-raise-and-consume-events.md)), as the following code shows:</span></span>

```csharp
PropertyChanged?.Invoke(…)
```

<span data-ttu-id="301eb-146">Ce code est équivalent au code suivant que vous utiliseriez dans C# 5 ou une version antérieure :</span><span class="sxs-lookup"><span data-stu-id="301eb-146">That code is equivalent to the following code that you would use in C# 5 or earlier:</span></span>

```csharp
var handler = this.PropertyChanged;
if (handler != null)
{
    handler(…);
}
```

## <a name="invocation-operator-"></a><span data-ttu-id="301eb-147">Opérateur d’appel ()</span><span class="sxs-lookup"><span data-stu-id="301eb-147">Invocation operator ()</span></span>

<span data-ttu-id="301eb-148">Utilisez des parenthèses, `()`, pour appeler une [méthode](../../programming-guide/classes-and-structs/methods.md) ou un [délégué](../../programming-guide/delegates/index.md).</span><span class="sxs-lookup"><span data-stu-id="301eb-148">Use parentheses, `()`, to call a [method](../../programming-guide/classes-and-structs/methods.md) or invoke a [delegate](../../programming-guide/delegates/index.md).</span></span>

<span data-ttu-id="301eb-149">L’exemple suivant montre comment appeler une méthode, avec ou sans arguments, et un délégué :</span><span class="sxs-lookup"><span data-stu-id="301eb-149">The following example demonstrates how to call a method, with or without arguments, and invoke a delegate:</span></span>

[!code-csharp-interactive[invocation with ()](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#Invocation)]

<span data-ttu-id="301eb-150">Vous utilisez également des parenthèses quand vous appelez un [constructeur](../../programming-guide/classes-and-structs/constructors.md) avec l’opérateur [`new`](new-operator.md).</span><span class="sxs-lookup"><span data-stu-id="301eb-150">You also use parentheses when you invoke a [constructor](../../programming-guide/classes-and-structs/constructors.md) with the [`new`](new-operator.md) operator.</span></span>

### <a name="other-usages-of-"></a><span data-ttu-id="301eb-151">Autres utilisations de ()</span><span class="sxs-lookup"><span data-stu-id="301eb-151">Other usages of ()</span></span>

<span data-ttu-id="301eb-152">Vous utilisez également des parenthèses pour ajuster l’ordre dans lequel évaluer les opérations dans une expression.</span><span class="sxs-lookup"><span data-stu-id="301eb-152">You also use parentheses to adjust the order in which to evaluate operations in an expression.</span></span> <span data-ttu-id="301eb-153">Pour plus d’informations, consultez [Opérateurs C#](index.md).</span><span class="sxs-lookup"><span data-stu-id="301eb-153">For more information, see [C# operators](index.md).</span></span>

<span data-ttu-id="301eb-154">[Les expressions cast](type-testing-and-cast.md#cast-operator-), qui effectuent des conversions de type explicites, utilisent aussi des parenthèses.</span><span class="sxs-lookup"><span data-stu-id="301eb-154">[Cast expressions](type-testing-and-cast.md#cast-operator-), which perform explicit type conversions, also use parentheses.</span></span>

## <a name="index-from-end-operator-"></a><span data-ttu-id="301eb-155">Index de fin d’opérateur ^</span><span class="sxs-lookup"><span data-stu-id="301eb-155">Index from end operator ^</span></span>

<span data-ttu-id="301eb-156">Disponible dans C# 8,0 et versions ultérieures `^` , l’opérateur indique la position de l’élément à partir de la fin d’une séquence.</span><span class="sxs-lookup"><span data-stu-id="301eb-156">Available in C# 8.0 and later, the `^` operator indicates the element position from the end of a sequence.</span></span> <span data-ttu-id="301eb-157">Pour une séquence de longueur `length`, `^n` pointe vers l’élément avec décalage `length - n` à partir du début d’une séquence.</span><span class="sxs-lookup"><span data-stu-id="301eb-157">For a sequence of length `length`, `^n` points to the element with offset `length - n` from the start of a sequence.</span></span> <span data-ttu-id="301eb-158">Par exemple, `^1` pointe vers le dernier élément d’une séquence et `^length` pointe vers le premier élément d’une séquence.</span><span class="sxs-lookup"><span data-stu-id="301eb-158">For example, `^1` points to the last element of a sequence and `^length` points to the first element of a sequence.</span></span>

[!code-csharp[index from end](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#IndexFromEnd)]

<span data-ttu-id="301eb-159">Comme le montre l’exemple précédent, `^e` expression est <xref:System.Index?displayProperty=nameWithType> du type.</span><span class="sxs-lookup"><span data-stu-id="301eb-159">As the preceding example shows, expression `^e` is of the <xref:System.Index?displayProperty=nameWithType> type.</span></span> <span data-ttu-id="301eb-160">Dans Expression `^e`, le résultat de `e` doit être implicitement convertible en `int`.</span><span class="sxs-lookup"><span data-stu-id="301eb-160">In expression `^e`, the result of `e` must be implicitly convertible to `int`.</span></span>

<span data-ttu-id="301eb-161">Vous pouvez également utiliser l' `^` opérateur avec l' [opérateur Range](#range-operator-) pour créer une plage d’index.</span><span class="sxs-lookup"><span data-stu-id="301eb-161">You also can use the `^` operator with the [range operator](#range-operator-) to create a range of indices.</span></span> <span data-ttu-id="301eb-162">Pour plus d’informations, consultez [index et plages](../../tutorials/ranges-indexes.md).</span><span class="sxs-lookup"><span data-stu-id="301eb-162">For more information, see [Indices and ranges](../../tutorials/ranges-indexes.md).</span></span>

## <a name="range-operator-"></a><span data-ttu-id="301eb-163">Opérateur de plage..</span><span class="sxs-lookup"><span data-stu-id="301eb-163">Range operator ..</span></span>

<span data-ttu-id="301eb-164">Disponible dans C# 8,0 et versions ultérieures `..` , l’opérateur spécifie le début et la fin d’une plage d’index comme opérandes.</span><span class="sxs-lookup"><span data-stu-id="301eb-164">Available in C# 8.0 and later, the `..` operator specifies the start and end of a range of indices as its operands.</span></span> <span data-ttu-id="301eb-165">L’opérande de gauche est un début *inclusif* d’une plage.</span><span class="sxs-lookup"><span data-stu-id="301eb-165">The left-hand operand is an *inclusive* start of a range.</span></span> <span data-ttu-id="301eb-166">L’opérande de droite est une extrémité *exclusive* d’une plage.</span><span class="sxs-lookup"><span data-stu-id="301eb-166">The right-hand operand is an *exclusive* end of a range.</span></span> <span data-ttu-id="301eb-167">L’un ou l’autre des opérandes peut être un index à partir du début ou de la fin d’une séquence, comme le montre l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="301eb-167">Either of operands can be an index from the start or from the end of a sequence, as the following example shows:</span></span>

[!code-csharp[range examples](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#Ranges)]

<span data-ttu-id="301eb-168">Comme le montre l’exemple précédent, `a..b` expression est <xref:System.Range?displayProperty=nameWithType> du type.</span><span class="sxs-lookup"><span data-stu-id="301eb-168">As the preceding example shows, expression `a..b` is of the <xref:System.Range?displayProperty=nameWithType> type.</span></span> <span data-ttu-id="301eb-169">Dans Expression `a..b`, les résultats de `a` et `b` doivent être implicitement convertibles `int` en <xref:System.Index>ou.</span><span class="sxs-lookup"><span data-stu-id="301eb-169">In expression `a..b`, the results of `a` and `b` must be implicitly convertible to `int` or <xref:System.Index>.</span></span>

<span data-ttu-id="301eb-170">Vous pouvez omettre l’un des opérandes de l' `..` opérateur pour obtenir une plage ouverte :</span><span class="sxs-lookup"><span data-stu-id="301eb-170">You can omit any of the operands of the `..` operator to obtain an open-ended range:</span></span>

- <span data-ttu-id="301eb-171">`a..`équivaut à`a..^0`</span><span class="sxs-lookup"><span data-stu-id="301eb-171">`a..` is equivalent to `a..^0`</span></span>
- <span data-ttu-id="301eb-172">`..b`équivaut à`0..b`</span><span class="sxs-lookup"><span data-stu-id="301eb-172">`..b` is equivalent to `0..b`</span></span>
- <span data-ttu-id="301eb-173">`..`équivaut à`0..^0`</span><span class="sxs-lookup"><span data-stu-id="301eb-173">`..` is equivalent to `0..^0`</span></span>

[!code-csharp[ranges with omitted operands](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#RangesOptional)]

<span data-ttu-id="301eb-174">Pour plus d’informations, consultez [index et plages](../../tutorials/ranges-indexes.md).</span><span class="sxs-lookup"><span data-stu-id="301eb-174">For more information, see [Indices and ranges](../../tutorials/ranges-indexes.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="301eb-175">Capacité de surcharge de l’opérateur</span><span class="sxs-lookup"><span data-stu-id="301eb-175">Operator overloadability</span></span>

<span data-ttu-id="301eb-176">Les `.`opérateurs `()` ,,et`..` ne peuvent pas être surchargés. `^`</span><span class="sxs-lookup"><span data-stu-id="301eb-176">The `.`, `()`, `^`, and `..` operators cannot be overloaded.</span></span> <span data-ttu-id="301eb-177">L’opérateur `[]` est également considéré comme un opérateur non surchargeable.</span><span class="sxs-lookup"><span data-stu-id="301eb-177">The `[]` operator is also considered a non-overloadable operator.</span></span> <span data-ttu-id="301eb-178">Utilisez des [indexeurs](../../programming-guide/indexers/index.md) pour prendre en charge l’indexation avec des types définis par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="301eb-178">Use [indexers](../../programming-guide/indexers/index.md) to support indexing with user-defined types.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="301eb-179">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="301eb-179">C# language specification</span></span>

<span data-ttu-id="301eb-180">Pour plus d’informations, consultez les sections suivantes de la [spécification du langage C#](~/_csharplang/spec/introduction.md) :</span><span class="sxs-lookup"><span data-stu-id="301eb-180">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="301eb-181">Accès aux membres</span><span class="sxs-lookup"><span data-stu-id="301eb-181">Member access</span></span>](~/_csharplang/spec/expressions.md#member-access)
- [<span data-ttu-id="301eb-182">Accès aux éléments</span><span class="sxs-lookup"><span data-stu-id="301eb-182">Element access</span></span>](~/_csharplang/spec/expressions.md#element-access)
- [<span data-ttu-id="301eb-183">Opérateur conditionnel Null</span><span class="sxs-lookup"><span data-stu-id="301eb-183">Null-conditional operator</span></span>](~/_csharplang/spec/expressions.md#null-conditional-operator)
- [<span data-ttu-id="301eb-184">Expressions d’appels</span><span class="sxs-lookup"><span data-stu-id="301eb-184">Invocation expressions</span></span>](~/_csharplang/spec/expressions.md#invocation-expressions)

## <a name="see-also"></a><span data-ttu-id="301eb-185">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="301eb-185">See also</span></span>

- [<span data-ttu-id="301eb-186">Informations de référence sur C#</span><span class="sxs-lookup"><span data-stu-id="301eb-186">C# reference</span></span>](../index.md)
- [<span data-ttu-id="301eb-187">Opérateurs C#</span><span class="sxs-lookup"><span data-stu-id="301eb-187">C# operators</span></span>](index.md)
- [<span data-ttu-id="301eb-188">?? (opérateur de fusion Null)</span><span class="sxs-lookup"><span data-stu-id="301eb-188">?? (null-coalescing operator)</span></span>](null-coalescing-operator.md)
- [<span data-ttu-id="301eb-189">:: opérateur</span><span class="sxs-lookup"><span data-stu-id="301eb-189">:: operator</span></span>](namespace-alias-qualifier.md)
