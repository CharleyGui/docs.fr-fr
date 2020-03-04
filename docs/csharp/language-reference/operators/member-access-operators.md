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
ms.openlocfilehash: ab69514e324c632f546957b2ddb58e073ca0154e
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/03/2020
ms.locfileid: "78239248"
---
# <a name="member-access-operators-c-reference"></a><span data-ttu-id="4729e-103">Opérateurs d’accès aux membres (référence C#)</span><span class="sxs-lookup"><span data-stu-id="4729e-103">Member access operators (C# reference)</span></span>

<span data-ttu-id="4729e-104">Vous pouvez utiliser les opérateurs suivants lorsque vous accédez à un membre de type :</span><span class="sxs-lookup"><span data-stu-id="4729e-104">You can use the following operators when you access a type member:</span></span>

- <span data-ttu-id="4729e-105">[`.` (accès aux membres)](#member-access-operator-) : accédez à un membre d’un espace de noms ou d’un type</span><span class="sxs-lookup"><span data-stu-id="4729e-105">[`.` (member access)](#member-access-operator-): to access a member of a namespace or a type</span></span>
- <span data-ttu-id="4729e-106">[`[]` (accès à un indexeur ou à un élément de tableau)](#indexer-operator-) : pour accéder à un élément de tableau ou à un indexeur de type</span><span class="sxs-lookup"><span data-stu-id="4729e-106">[`[]` (array element or indexer access)](#indexer-operator-): to access an array element or a type indexer</span></span>
- <span data-ttu-id="4729e-107">[`?.` et `?[]` (opérateurs conditionnels Null)](#null-conditional-operators--and-) : pour effectuer une opération d’accès à un membre ou élément uniquement si un opérande est non Null</span><span class="sxs-lookup"><span data-stu-id="4729e-107">[`?.` and `?[]` (null-conditional operators)](#null-conditional-operators--and-): to perform a member or element access operation only if an operand is non-null</span></span>
- <span data-ttu-id="4729e-108">[`()` (appel) ](#invocation-operator-) : pour appeler une méthode sollicitée ou appeler un délégué</span><span class="sxs-lookup"><span data-stu-id="4729e-108">[`()` (invocation)](#invocation-operator-): to call an accessed method or invoke a delegate</span></span>
- <span data-ttu-id="4729e-109">[`^` (index à partir de la fin)](#index-from-end-operator-): pour indiquer que la position de l’élément est à partir de la fin d’une séquence</span><span class="sxs-lookup"><span data-stu-id="4729e-109">[`^` (index from end)](#index-from-end-operator-): to indicate that the element position is from the end of a sequence</span></span>
- <span data-ttu-id="4729e-110">[`..` (plage)](#range-operator-): pour spécifier une plage d’index que vous pouvez utiliser pour obtenir une plage d’éléments de séquence</span><span class="sxs-lookup"><span data-stu-id="4729e-110">[`..` (range)](#range-operator-): to specify a range of indices that you can use to obtain a range of sequence elements</span></span>

## <a name="member-access-operator-"></a><span data-ttu-id="4729e-111">Opérateur d’accès aux membres .</span><span class="sxs-lookup"><span data-stu-id="4729e-111">Member access operator .</span></span>

<span data-ttu-id="4729e-112">Le jeton `.` sert à accéder à l’un des membres d’un espace de noms ou d’un type, comme le montrent les exemples suivants :</span><span class="sxs-lookup"><span data-stu-id="4729e-112">You use the `.` token to access a member of a namespace or a type, as the following examples demonstrate:</span></span>

- <span data-ttu-id="4729e-113">Utilisez `.` pour accéder à un espace de noms imbriqué dans un autre, comme le montre l’exemple suivant avec la [directive `using`](../keywords/using-directive.md) :</span><span class="sxs-lookup"><span data-stu-id="4729e-113">Use `.` to access a nested namespace within a namespace, as the following example of a [`using` directive](../keywords/using-directive.md) shows:</span></span>

  [!code-csharp[nested namespaces](~/samples/snippets/csharp/language-reference/operators/MemberAccessOperators.cs#NestedNamespace)]

- <span data-ttu-id="4729e-114">Utilisez `.` pour former un *nom qualifié* permettant d’accéder à un type dans un espace de noms, comme le montre le code suivant :</span><span class="sxs-lookup"><span data-stu-id="4729e-114">Use `.` to form a *qualified name* to access a type within a namespace, as the following code shows:</span></span>

  [!code-csharp[qualified name](~/samples/snippets/csharp/language-reference/operators/MemberAccessOperators.cs#QualifiedName)]

  <span data-ttu-id="4729e-115">Utilisez une [directive `using`](../keywords/using-directive.md) pour rendre facultative l’utilisation de noms qualifiés.</span><span class="sxs-lookup"><span data-stu-id="4729e-115">Use a [`using` directive](../keywords/using-directive.md) to make the use of qualified names optional.</span></span>

- <span data-ttu-id="4729e-116">Utilisez `.` pour accéder aux [membres de type](../../programming-guide/classes-and-structs/index.md#members), statiques et non statiques, comme le montre le code suivant :</span><span class="sxs-lookup"><span data-stu-id="4729e-116">Use `.` to access [type members](../../programming-guide/classes-and-structs/index.md#members), static and non-static, as the following code shows:</span></span>

  [!code-csharp-interactive[type members](~/samples/snippets/csharp/language-reference/operators/MemberAccessOperators.cs#TypeMemberAccess)]

<span data-ttu-id="4729e-117">Vous pouvez également utiliser `.` pour accéder à une [méthode d’extension](../../programming-guide/classes-and-structs/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="4729e-117">You can also use `.` to access an [extension method](../../programming-guide/classes-and-structs/extension-methods.md).</span></span>

## <a name="indexer-operator-"></a><span data-ttu-id="4729e-118">Opérateur d’indexeur []</span><span class="sxs-lookup"><span data-stu-id="4729e-118">Indexer operator []</span></span>

<span data-ttu-id="4729e-119">Les crochets, `[]`, sont généralement utilisés pour l’accès à un élément tableau, indexeur ou pointeur.</span><span class="sxs-lookup"><span data-stu-id="4729e-119">Square brackets, `[]`, are typically used for array, indexer, or pointer element access.</span></span>

### <a name="array-access"></a><span data-ttu-id="4729e-120">Accès aux tableaux</span><span class="sxs-lookup"><span data-stu-id="4729e-120">Array access</span></span>

<span data-ttu-id="4729e-121">L’exemple suivant montre comment accéder à des éléments tableau :</span><span class="sxs-lookup"><span data-stu-id="4729e-121">The following example demonstrates how to access array elements:</span></span>

[!code-csharp-interactive[array access](~/samples/snippets/csharp/language-reference/operators/MemberAccessOperators.cs#Arrays)]

<span data-ttu-id="4729e-122">Si un index de tableau est en dehors des limites de la dimension correspondante d’un tableau, une <xref:System.IndexOutOfRangeException> est levée.</span><span class="sxs-lookup"><span data-stu-id="4729e-122">If an array index is outside the bounds of the corresponding dimension of an array, an <xref:System.IndexOutOfRangeException> is thrown.</span></span>

<span data-ttu-id="4729e-123">Comme le montre l’exemple précédent, vous utilisez également des crochets quand vous déclarez un type tableau ou instanciez une instance de tableau.</span><span class="sxs-lookup"><span data-stu-id="4729e-123">As the preceding example shows, you also use square brackets when you declare an array type or instantiate an array instance.</span></span>

<span data-ttu-id="4729e-124">Pour plus d’informations sur les tableaux, consultez [Tableaux](../../programming-guide/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="4729e-124">For more information about arrays, see [Arrays](../../programming-guide/arrays/index.md).</span></span>

### <a name="indexer-access"></a><span data-ttu-id="4729e-125">Accès aux indexeurs</span><span class="sxs-lookup"><span data-stu-id="4729e-125">Indexer access</span></span>

<span data-ttu-id="4729e-126">L’exemple suivant utilise le type de <xref:System.Collections.Generic.Dictionary%602> .NET pour illustrer l’accès à l’indexeur :</span><span class="sxs-lookup"><span data-stu-id="4729e-126">The following example uses the .NET <xref:System.Collections.Generic.Dictionary%602> type to demonstrate indexer access:</span></span>

[!code-csharp-interactive[indexer access](~/samples/snippets/csharp/language-reference/operators/MemberAccessOperators.cs#Indexers)]

<span data-ttu-id="4729e-127">Les indexeurs vous permettent d’indexer des instances d’un type défini par l’utilisateur en procédant de la même façon que pour l’indexation de tableau.</span><span class="sxs-lookup"><span data-stu-id="4729e-127">Indexers allow you to index instances of a user-defined type in the similar way as array indexing.</span></span> <span data-ttu-id="4729e-128">Contrairement aux index de tableau, qui doivent être des entiers, les paramètres de l’indexeur peuvent être déclarés comme n’importe quel type.</span><span class="sxs-lookup"><span data-stu-id="4729e-128">Unlike array indices, which must be integer, the indexer parameters can be declared to be of any type.</span></span>

<span data-ttu-id="4729e-129">Pour plus d’informations sur les indexeurs, consultez [Indexeurs](../../programming-guide/indexers/index.md).</span><span class="sxs-lookup"><span data-stu-id="4729e-129">For more information about indexers, see [Indexers](../../programming-guide/indexers/index.md).</span></span>

### <a name="other-usages-of-"></a><span data-ttu-id="4729e-130">Autres utilisations de []</span><span class="sxs-lookup"><span data-stu-id="4729e-130">Other usages of []</span></span>

<span data-ttu-id="4729e-131">Pour plus d’informations concernant l’accès à l’élément de pointeur, consultez la section [Opérateur d’accès à l’élément de pointeur []](pointer-related-operators.md#pointer-element-access-operator-) de l’article [Opérateurs associés au pointeur](pointer-related-operators.md).</span><span class="sxs-lookup"><span data-stu-id="4729e-131">For information about pointer element access, see the [Pointer element access operator []](pointer-related-operators.md#pointer-element-access-operator-) section of the [Pointer related operators](pointer-related-operators.md) article.</span></span>

<span data-ttu-id="4729e-132">Vous utilisez également des crochets pour spécifier des [attributs](../../programming-guide/concepts/attributes/index.md) :</span><span class="sxs-lookup"><span data-stu-id="4729e-132">You also use square brackets to specify [attributes](../../programming-guide/concepts/attributes/index.md):</span></span>

```csharp
[System.Diagnostics.Conditional("DEBUG")]
void TraceMethod() {}
```

## <a name="null-conditional-operators--and-"></a><span data-ttu-id="4729e-133">Opérateurs conditionnels Null ?.</span><span class="sxs-lookup"><span data-stu-id="4729e-133">Null-conditional operators ?.</span></span> <span data-ttu-id="4729e-134">et ?[]</span><span class="sxs-lookup"><span data-stu-id="4729e-134">and ?[]</span></span>

<span data-ttu-id="4729e-135">Disponible dans C# 6 et versions ultérieures, un opérateur conditionnel null applique un accès au [membre](#member-access-operator-), `?.`ou un accès à l' [élément](#indexer-operator-), `?[]`, à son opérande uniquement si cet opérande a la valeur non null ; Sinon, elle retourne `null`.</span><span class="sxs-lookup"><span data-stu-id="4729e-135">Available in C# 6 and later, a null-conditional operator applies a [member access](#member-access-operator-), `?.`, or [element access](#indexer-operator-), `?[]`, operation to its operand only if that operand evaluates to non-null; otherwise, it returns `null`.</span></span> <span data-ttu-id="4729e-136">C'est</span><span class="sxs-lookup"><span data-stu-id="4729e-136">That is,</span></span>

- <span data-ttu-id="4729e-137">Si `a` prend la valeur `null`, le résultat de `a?.x` ou `a?[x]` est `null`.</span><span class="sxs-lookup"><span data-stu-id="4729e-137">If `a` evaluates to `null`, the result of `a?.x` or `a?[x]` is `null`.</span></span>
- <span data-ttu-id="4729e-138">Si `a` prend la valeur non null, le résultat de `a?.x` ou `a?[x]` est le même que le résultat de `a.x` ou de `a[x]`, respectivement.</span><span class="sxs-lookup"><span data-stu-id="4729e-138">If `a` evaluates to non-null, the result of `a?.x` or `a?[x]` is the same as the result of `a.x` or `a[x]`, respectively.</span></span>

  > [!NOTE]
  > <span data-ttu-id="4729e-139">Si `a.x` ou `a[x]` lève une exception, `a?.x` ou `a?[x]` lèvera la même exception pour les `a`non null.</span><span class="sxs-lookup"><span data-stu-id="4729e-139">If `a.x` or `a[x]` throws an exception, `a?.x` or `a?[x]` would throw the same exception for non-null `a`.</span></span> <span data-ttu-id="4729e-140">Par exemple, si `a` est une instance de tableau non null et que `x` se trouve en dehors des limites de `a`, `a?[x]` lèvera une <xref:System.IndexOutOfRangeException>.</span><span class="sxs-lookup"><span data-stu-id="4729e-140">For example, if `a` is a non-null array instance and `x` is outside the bounds of `a`, `a?[x]` would throw an <xref:System.IndexOutOfRangeException>.</span></span>

<span data-ttu-id="4729e-141">Les opérateurs conditionnels Null ont un effet de court-circuit.</span><span class="sxs-lookup"><span data-stu-id="4729e-141">The null-conditional operators are short-circuiting.</span></span> <span data-ttu-id="4729e-142">Autrement dit, si une opération dans une chaîne d’opérations d’accès au membre ou à l’élément conditionnelles retourne une valeur `null`, le reste de la chaîne ne s’exécute pas.</span><span class="sxs-lookup"><span data-stu-id="4729e-142">That is, if one operation in a chain of conditional member or element access operations returns `null`, the rest of the chain doesn't execute.</span></span> <span data-ttu-id="4729e-143">Dans l’exemple suivant, `B` n’est pas évalué si `A` prend la valeur `null` et `C` n’est pas évalué si `A` ou `B` prend la valeur `null` :</span><span class="sxs-lookup"><span data-stu-id="4729e-143">In the following example, `B` is not evaluated if `A` evaluates to `null` and `C` is not evaluated if `A` or `B` evaluates to `null`:</span></span>

```csharp
A?.B?.Do(C);
A?.B?[C];
```

<span data-ttu-id="4729e-144">L’exemple suivant illustre l’utilisation des opérateurs `?.` et `?[]` :</span><span class="sxs-lookup"><span data-stu-id="4729e-144">The following example demonstrates the usage of the `?.` and `?[]` operators:</span></span>

[!code-csharp-interactive[null-conditional operators](~/samples/snippets/csharp/language-reference/operators/MemberAccessOperators.cs#NullConditional)]

<span data-ttu-id="4729e-145">L’exemple précédent utilise également l' [opérateur de fusion null `??`](null-coalescing-operator.md) pour spécifier une autre expression à évaluer si le résultat d’une opération conditionnelle null est `null`.</span><span class="sxs-lookup"><span data-stu-id="4729e-145">The preceding example also uses the [null-coalescing operator `??`](null-coalescing-operator.md) to specify an alternative expression to evaluate in case the result of a null-conditional operation is `null`.</span></span>

<span data-ttu-id="4729e-146">L’opérateur d’accès aux membres conditionnels null `?.` est également appelé l’opérateur Elvis.</span><span class="sxs-lookup"><span data-stu-id="4729e-146">The null-conditional member access operator `?.` is also known as the Elvis operator.</span></span>

### <a name="thread-safe-delegate-invocation"></a><span data-ttu-id="4729e-147">Appel de délégué thread-safe</span><span class="sxs-lookup"><span data-stu-id="4729e-147">Thread-safe delegate invocation</span></span>

<span data-ttu-id="4729e-148">Utilisez l’opérateur `?.` pour vérifier si un délégué est non Null et l’appeler de manière thread-safe (par exemple, quand vous [déclenchez un événement](../../../standard/events/how-to-raise-and-consume-events.md)), comme illustré dans le code suivant :</span><span class="sxs-lookup"><span data-stu-id="4729e-148">Use the `?.` operator to check if a delegate is non-null and invoke it in a thread-safe way (for example, when you [raise an event](../../../standard/events/how-to-raise-and-consume-events.md)), as the following code shows:</span></span>

```csharp
PropertyChanged?.Invoke(…)
```

<span data-ttu-id="4729e-149">Ce code est équivalent au code suivant que vous utiliseriez dans C# 5 ou une version antérieure :</span><span class="sxs-lookup"><span data-stu-id="4729e-149">That code is equivalent to the following code that you would use in C# 5 or earlier:</span></span>

```csharp
var handler = this.PropertyChanged;
if (handler != null)
{
    handler(…);
}
```

## <a name="invocation-operator-"></a><span data-ttu-id="4729e-150">Opérateur d’appel ()</span><span class="sxs-lookup"><span data-stu-id="4729e-150">Invocation operator ()</span></span>

<span data-ttu-id="4729e-151">Utilisez des parenthèses, `()`, pour appeler une [méthode](../../programming-guide/classes-and-structs/methods.md) ou un [délégué](../../programming-guide/delegates/index.md).</span><span class="sxs-lookup"><span data-stu-id="4729e-151">Use parentheses, `()`, to call a [method](../../programming-guide/classes-and-structs/methods.md) or invoke a [delegate](../../programming-guide/delegates/index.md).</span></span>

<span data-ttu-id="4729e-152">L’exemple suivant montre comment appeler une méthode, avec ou sans arguments, et un délégué :</span><span class="sxs-lookup"><span data-stu-id="4729e-152">The following example demonstrates how to call a method, with or without arguments, and invoke a delegate:</span></span>

[!code-csharp-interactive[invocation with ()](~/samples/snippets/csharp/language-reference/operators/MemberAccessOperators.cs#Invocation)]

<span data-ttu-id="4729e-153">Vous utilisez également des parenthèses quand vous appelez un [constructeur](../../programming-guide/classes-and-structs/constructors.md) avec l’opérateur [`new`](new-operator.md).</span><span class="sxs-lookup"><span data-stu-id="4729e-153">You also use parentheses when you invoke a [constructor](../../programming-guide/classes-and-structs/constructors.md) with the [`new`](new-operator.md) operator.</span></span>

### <a name="other-usages-of-"></a><span data-ttu-id="4729e-154">Autres utilisations de ()</span><span class="sxs-lookup"><span data-stu-id="4729e-154">Other usages of ()</span></span>

<span data-ttu-id="4729e-155">Vous utilisez également des parenthèses pour ajuster l’ordre dans lequel évaluer les opérations dans une expression.</span><span class="sxs-lookup"><span data-stu-id="4729e-155">You also use parentheses to adjust the order in which to evaluate operations in an expression.</span></span> <span data-ttu-id="4729e-156">Pour plus d’informations, consultez [Opérateurs C#](index.md).</span><span class="sxs-lookup"><span data-stu-id="4729e-156">For more information, see [C# operators](index.md).</span></span>

<span data-ttu-id="4729e-157">[Les expressions cast](type-testing-and-cast.md#cast-operator-), qui effectuent des conversions de type explicites, utilisent aussi des parenthèses.</span><span class="sxs-lookup"><span data-stu-id="4729e-157">[Cast expressions](type-testing-and-cast.md#cast-operator-), which perform explicit type conversions, also use parentheses.</span></span>

## <a name="index-from-end-operator-"></a><span data-ttu-id="4729e-158">Index de fin d’opérateur ^</span><span class="sxs-lookup"><span data-stu-id="4729e-158">Index from end operator ^</span></span>

<span data-ttu-id="4729e-159">Disponible dans C# 8,0 et versions ultérieures, l’opérateur `^` indique la position de l’élément à partir de la fin d’une séquence.</span><span class="sxs-lookup"><span data-stu-id="4729e-159">Available in C# 8.0 and later, the `^` operator indicates the element position from the end of a sequence.</span></span> <span data-ttu-id="4729e-160">Pour une séquence de longueur `length`, `^n` pointe sur l’élément avec des `length - n` de décalage à partir du début d’une séquence.</span><span class="sxs-lookup"><span data-stu-id="4729e-160">For a sequence of length `length`, `^n` points to the element with offset `length - n` from the start of a sequence.</span></span> <span data-ttu-id="4729e-161">Par exemple, `^1` pointe vers le dernier élément d’une séquence et `^length` pointe vers le premier élément d’une séquence.</span><span class="sxs-lookup"><span data-stu-id="4729e-161">For example, `^1` points to the last element of a sequence and `^length` points to the first element of a sequence.</span></span>

[!code-csharp[index from end](~/samples/snippets/csharp/language-reference/operators/MemberAccessOperators.cs#IndexFromEnd)]

<span data-ttu-id="4729e-162">Comme le montre l’exemple précédent, expression `^e` est du type <xref:System.Index?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4729e-162">As the preceding example shows, expression `^e` is of the <xref:System.Index?displayProperty=nameWithType> type.</span></span> <span data-ttu-id="4729e-163">Dans expression `^e`, le résultat de `e` doit être implicitement convertible en `int`.</span><span class="sxs-lookup"><span data-stu-id="4729e-163">In expression `^e`, the result of `e` must be implicitly convertible to `int`.</span></span>

<span data-ttu-id="4729e-164">Vous pouvez également utiliser l’opérateur `^` avec l' [opérateur Range](#range-operator-) pour créer une plage d’index.</span><span class="sxs-lookup"><span data-stu-id="4729e-164">You also can use the `^` operator with the [range operator](#range-operator-) to create a range of indices.</span></span> <span data-ttu-id="4729e-165">Pour plus d’informations, consultez [index et plages](../../tutorials/ranges-indexes.md).</span><span class="sxs-lookup"><span data-stu-id="4729e-165">For more information, see [Indices and ranges](../../tutorials/ranges-indexes.md).</span></span>

## <a name="range-operator-"></a><span data-ttu-id="4729e-166">Opérateur de plage..</span><span class="sxs-lookup"><span data-stu-id="4729e-166">Range operator ..</span></span>

<span data-ttu-id="4729e-167">Disponible dans C# 8,0 et versions ultérieures, l’opérateur `..` spécifie le début et la fin d’une plage d’index comme opérandes.</span><span class="sxs-lookup"><span data-stu-id="4729e-167">Available in C# 8.0 and later, the `..` operator specifies the start and end of a range of indices as its operands.</span></span> <span data-ttu-id="4729e-168">L’opérande de gauche est un début *inclusif* d’une plage.</span><span class="sxs-lookup"><span data-stu-id="4729e-168">The left-hand operand is an *inclusive* start of a range.</span></span> <span data-ttu-id="4729e-169">L’opérande de droite est une extrémité *exclusive* d’une plage.</span><span class="sxs-lookup"><span data-stu-id="4729e-169">The right-hand operand is an *exclusive* end of a range.</span></span> <span data-ttu-id="4729e-170">L’un ou l’autre des opérandes peut être un index à partir du début ou de la fin d’une séquence, comme le montre l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="4729e-170">Either of operands can be an index from the start or from the end of a sequence, as the following example shows:</span></span>

[!code-csharp[range examples](~/samples/snippets/csharp/language-reference/operators/MemberAccessOperators.cs#Ranges)]

<span data-ttu-id="4729e-171">Comme le montre l’exemple précédent, expression `a..b` est du type <xref:System.Range?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4729e-171">As the preceding example shows, expression `a..b` is of the <xref:System.Range?displayProperty=nameWithType> type.</span></span> <span data-ttu-id="4729e-172">Dans expression `a..b`, les résultats de `a` et `b` doivent être implicitement convertibles en `int` ou <xref:System.Index>.</span><span class="sxs-lookup"><span data-stu-id="4729e-172">In expression `a..b`, the results of `a` and `b` must be implicitly convertible to `int` or <xref:System.Index>.</span></span>

<span data-ttu-id="4729e-173">Vous pouvez omettre l’un des opérandes de l’opérateur `..` pour obtenir une plage ouverte :</span><span class="sxs-lookup"><span data-stu-id="4729e-173">You can omit any of the operands of the `..` operator to obtain an open-ended range:</span></span>

- <span data-ttu-id="4729e-174">`a..` équivaut à `a..^0`</span><span class="sxs-lookup"><span data-stu-id="4729e-174">`a..` is equivalent to `a..^0`</span></span>
- <span data-ttu-id="4729e-175">`..b` équivaut à `0..b`</span><span class="sxs-lookup"><span data-stu-id="4729e-175">`..b` is equivalent to `0..b`</span></span>
- <span data-ttu-id="4729e-176">`..` équivaut à `0..^0`</span><span class="sxs-lookup"><span data-stu-id="4729e-176">`..` is equivalent to `0..^0`</span></span>

[!code-csharp[ranges with omitted operands](~/samples/snippets/csharp/language-reference/operators/MemberAccessOperators.cs#RangesOptional)]

<span data-ttu-id="4729e-177">Pour plus d’informations, consultez [index et plages](../../tutorials/ranges-indexes.md).</span><span class="sxs-lookup"><span data-stu-id="4729e-177">For more information, see [Indices and ranges](../../tutorials/ranges-indexes.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="4729e-178">Capacité de surcharge de l’opérateur</span><span class="sxs-lookup"><span data-stu-id="4729e-178">Operator overloadability</span></span>

<span data-ttu-id="4729e-179">Les opérateurs `.`, `()`, `^`et `..` ne peuvent pas être surchargés.</span><span class="sxs-lookup"><span data-stu-id="4729e-179">The `.`, `()`, `^`, and `..` operators cannot be overloaded.</span></span> <span data-ttu-id="4729e-180">L’opérateur `[]` est également considéré comme un opérateur non surchargeable.</span><span class="sxs-lookup"><span data-stu-id="4729e-180">The `[]` operator is also considered a non-overloadable operator.</span></span> <span data-ttu-id="4729e-181">Utilisez des [indexeurs](../../programming-guide/indexers/index.md) pour prendre en charge l’indexation avec des types définis par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="4729e-181">Use [indexers](../../programming-guide/indexers/index.md) to support indexing with user-defined types.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="4729e-182">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="4729e-182">C# language specification</span></span>

<span data-ttu-id="4729e-183">Pour plus d’informations, consultez les sections suivantes de la [spécification du langage C#](~/_csharplang/spec/introduction.md) :</span><span class="sxs-lookup"><span data-stu-id="4729e-183">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="4729e-184">Accès aux membres</span><span class="sxs-lookup"><span data-stu-id="4729e-184">Member access</span></span>](~/_csharplang/spec/expressions.md#member-access)
- [<span data-ttu-id="4729e-185">Accès aux éléments</span><span class="sxs-lookup"><span data-stu-id="4729e-185">Element access</span></span>](~/_csharplang/spec/expressions.md#element-access)
- [<span data-ttu-id="4729e-186">Opérateur conditionnel Null</span><span class="sxs-lookup"><span data-stu-id="4729e-186">Null-conditional operator</span></span>](~/_csharplang/spec/expressions.md#null-conditional-operator)
- [<span data-ttu-id="4729e-187">Expressions d’appels</span><span class="sxs-lookup"><span data-stu-id="4729e-187">Invocation expressions</span></span>](~/_csharplang/spec/expressions.md#invocation-expressions)

<span data-ttu-id="4729e-188">Pour plus d’informations sur les index et les plages, consultez la [Remarque relative](~/_csharplang/proposals/csharp-8.0/ranges.md)à la proposition de fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="4729e-188">For more information about indices and ranges, see the [feature proposal note](~/_csharplang/proposals/csharp-8.0/ranges.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4729e-189">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4729e-189">See also</span></span>

- [<span data-ttu-id="4729e-190">Informations de référence sur C#</span><span class="sxs-lookup"><span data-stu-id="4729e-190">C# reference</span></span>](../index.md)
- [<span data-ttu-id="4729e-191">Opérateurs C#</span><span class="sxs-lookup"><span data-stu-id="4729e-191">C# operators</span></span>](index.md)
- [<span data-ttu-id="4729e-192">?? (opérateur de fusion Null)</span><span class="sxs-lookup"><span data-stu-id="4729e-192">?? (null-coalescing operator)</span></span>](null-coalescing-operator.md)
- [<span data-ttu-id="4729e-193">:: opérateur</span><span class="sxs-lookup"><span data-stu-id="4729e-193">:: operator</span></span>](namespace-alias-qualifier.md)
