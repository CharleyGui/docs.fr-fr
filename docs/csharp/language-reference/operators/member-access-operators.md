---
title: Opérateurs d’accès aux membres et expressions-référence C#
description: Découvrez les opérateurs C# que vous pouvez utiliser pour accéder aux membres de type.
ms.date: 04/17/2020
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
ms.openlocfilehash: 37a6cb7cd32a9d60607aec51b1994e4717c5349a
ms.sourcegitcommit: e09dbff13f0b21b569a101f3b3c5efa174aec204
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/01/2020
ms.locfileid: "82624863"
---
# <a name="member-access-operators-and-expressions-c-reference"></a><span data-ttu-id="7059e-103">Opérateurs et expressions d’accès aux membres (référence C#)</span><span class="sxs-lookup"><span data-stu-id="7059e-103">Member access operators and expressions (C# reference)</span></span>

<span data-ttu-id="7059e-104">Vous pouvez utiliser les opérateurs et expressions suivants lorsque vous accédez à un membre de type :</span><span class="sxs-lookup"><span data-stu-id="7059e-104">You can use the following operators and expressions when you access a type member:</span></span>

- <span data-ttu-id="7059e-105">[(accès aux membres) : pour accéder à un membre d’un espace de noms ou d’un type `.` ](#member-access-expression-)</span><span class="sxs-lookup"><span data-stu-id="7059e-105">[`.` (member access)](#member-access-expression-): to access a member of a namespace or a type</span></span>
- <span data-ttu-id="7059e-106">[(élément de tableau ou accès à l’indexeur) : pour accéder à un élément de tableau ou à un indexeur de type `[]` ](#indexer-operator-)</span><span class="sxs-lookup"><span data-stu-id="7059e-106">[`[]` (array element or indexer access)](#indexer-operator-): to access an array element or a type indexer</span></span>
- <span data-ttu-id="7059e-107">[et `?[]` opérateurs conditionnels null) : pour effectuer une opération d’accès de membre ou d’élément uniquement si un opérande n’est `?.` ](#null-conditional-operators--and-)pas null</span><span class="sxs-lookup"><span data-stu-id="7059e-107">[`?.` and `?[]` (null-conditional operators)](#null-conditional-operators--and-): to perform a member or element access operation only if an operand is non-null</span></span>
- <span data-ttu-id="7059e-108">(appel) : pour appeler une méthode accédée ou appeler un délégué [ `()` ](#invocation-expression-)</span><span class="sxs-lookup"><span data-stu-id="7059e-108">[`()` (invocation)](#invocation-expression-): to call an accessed method or invoke a delegate</span></span>
- <span data-ttu-id="7059e-109">[(index à partir de la fin) : pour indiquer que la position de l’élément est à partir de la fin d’une séquence `^` ](#index-from-end-operator-)</span><span class="sxs-lookup"><span data-stu-id="7059e-109">[`^` (index from end)](#index-from-end-operator-): to indicate that the element position is from the end of a sequence</span></span>
- <span data-ttu-id="7059e-110">(plage) : pour spécifier une plage d’index que vous pouvez utiliser pour obtenir une plage d’éléments de séquence [ `..` ](#range-operator-)</span><span class="sxs-lookup"><span data-stu-id="7059e-110">[`..` (range)](#range-operator-): to specify a range of indices that you can use to obtain a range of sequence elements</span></span>

## <a name="member-access-expression-"></a><span data-ttu-id="7059e-111">Expression d’accès au membre.</span><span class="sxs-lookup"><span data-stu-id="7059e-111">Member access expression .</span></span>

<span data-ttu-id="7059e-112">Le jeton `.` sert à accéder à l’un des membres d’un espace de noms ou d’un type, comme le montrent les exemples suivants :</span><span class="sxs-lookup"><span data-stu-id="7059e-112">You use the `.` token to access a member of a namespace or a type, as the following examples demonstrate:</span></span>

- <span data-ttu-id="7059e-113">Utilisez `.` pour accéder à un espace de noms imbriqué dans un espace de noms, comme le montre l’exemple suivant d’une [ `using` directive](../keywords/using-directive.md) :</span><span class="sxs-lookup"><span data-stu-id="7059e-113">Use `.` to access a nested namespace within a namespace, as the following example of a [`using` directive](../keywords/using-directive.md) shows:</span></span>

  [!code-csharp[nested namespaces](snippets/MemberAccessOperators.cs#NestedNamespace)]

- <span data-ttu-id="7059e-114">Utilisez `.` pour former un *nom qualifié* permettant d’accéder à un type dans un espace de noms, comme le montre le code suivant :</span><span class="sxs-lookup"><span data-stu-id="7059e-114">Use `.` to form a *qualified name* to access a type within a namespace, as the following code shows:</span></span>

  [!code-csharp[qualified name](snippets/MemberAccessOperators.cs#QualifiedName)]

  <span data-ttu-id="7059e-115">Utilisez une [ `using` directive](../keywords/using-directive.md) pour rendre l’utilisation des noms qualifiés facultative.</span><span class="sxs-lookup"><span data-stu-id="7059e-115">Use a [`using` directive](../keywords/using-directive.md) to make the use of qualified names optional.</span></span>

- <span data-ttu-id="7059e-116">Utilisez `.` pour accéder aux [membres de type](../../programming-guide/classes-and-structs/index.md#members), statiques et non statiques, comme le montre le code suivant :</span><span class="sxs-lookup"><span data-stu-id="7059e-116">Use `.` to access [type members](../../programming-guide/classes-and-structs/index.md#members), static and non-static, as the following code shows:</span></span>

  [!code-csharp-interactive[type members](snippets/MemberAccessOperators.cs#TypeMemberAccess)]

<span data-ttu-id="7059e-117">Vous pouvez également utiliser `.` pour accéder à une [méthode d’extension](../../programming-guide/classes-and-structs/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="7059e-117">You can also use `.` to access an [extension method](../../programming-guide/classes-and-structs/extension-methods.md).</span></span>

## <a name="indexer-operator-"></a><span data-ttu-id="7059e-118">Opérateur d’indexeur []</span><span class="sxs-lookup"><span data-stu-id="7059e-118">Indexer operator []</span></span>

<span data-ttu-id="7059e-119">Les crochets, `[]`, sont généralement utilisés pour l’accès à un élément tableau, indexeur ou pointeur.</span><span class="sxs-lookup"><span data-stu-id="7059e-119">Square brackets, `[]`, are typically used for array, indexer, or pointer element access.</span></span>

### <a name="array-access"></a><span data-ttu-id="7059e-120">Accès aux tableaux</span><span class="sxs-lookup"><span data-stu-id="7059e-120">Array access</span></span>

<span data-ttu-id="7059e-121">L’exemple suivant montre comment accéder à des éléments tableau :</span><span class="sxs-lookup"><span data-stu-id="7059e-121">The following example demonstrates how to access array elements:</span></span>

[!code-csharp-interactive[array access](snippets/MemberAccessOperators.cs#Arrays)]

<span data-ttu-id="7059e-122">Si un index de tableau est en dehors des limites de la dimension correspondante d’un tableau, une <xref:System.IndexOutOfRangeException> est levée.</span><span class="sxs-lookup"><span data-stu-id="7059e-122">If an array index is outside the bounds of the corresponding dimension of an array, an <xref:System.IndexOutOfRangeException> is thrown.</span></span>

<span data-ttu-id="7059e-123">Comme le montre l’exemple précédent, vous utilisez également des crochets quand vous déclarez un type tableau ou instanciez une instance de tableau.</span><span class="sxs-lookup"><span data-stu-id="7059e-123">As the preceding example shows, you also use square brackets when you declare an array type or instantiate an array instance.</span></span>

<span data-ttu-id="7059e-124">Pour plus d’informations sur les tableaux, consultez [Tableaux](../../programming-guide/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="7059e-124">For more information about arrays, see [Arrays](../../programming-guide/arrays/index.md).</span></span>

### <a name="indexer-access"></a><span data-ttu-id="7059e-125">Accès aux indexeurs</span><span class="sxs-lookup"><span data-stu-id="7059e-125">Indexer access</span></span>

<span data-ttu-id="7059e-126">L’exemple suivant utilise le type <xref:System.Collections.Generic.Dictionary%602> .net pour illustrer l’accès à l’indexeur :</span><span class="sxs-lookup"><span data-stu-id="7059e-126">The following example uses the .NET <xref:System.Collections.Generic.Dictionary%602> type to demonstrate indexer access:</span></span>

[!code-csharp-interactive[indexer access](snippets/MemberAccessOperators.cs#Indexers)]

<span data-ttu-id="7059e-127">Les indexeurs vous permettent d’indexer des instances d’un type défini par l’utilisateur en procédant de la même façon que pour l’indexation de tableau.</span><span class="sxs-lookup"><span data-stu-id="7059e-127">Indexers allow you to index instances of a user-defined type in the similar way as array indexing.</span></span> <span data-ttu-id="7059e-128">Contrairement aux index de tableau, qui doivent être des entiers, les paramètres de l’indexeur peuvent être déclarés comme n’importe quel type.</span><span class="sxs-lookup"><span data-stu-id="7059e-128">Unlike array indices, which must be integer, the indexer parameters can be declared to be of any type.</span></span>

<span data-ttu-id="7059e-129">Pour plus d’informations sur les indexeurs, consultez [Indexeurs](../../programming-guide/indexers/index.md).</span><span class="sxs-lookup"><span data-stu-id="7059e-129">For more information about indexers, see [Indexers](../../programming-guide/indexers/index.md).</span></span>

### <a name="other-usages-of-"></a><span data-ttu-id="7059e-130">Autres utilisations de []</span><span class="sxs-lookup"><span data-stu-id="7059e-130">Other usages of []</span></span>

<span data-ttu-id="7059e-131">Pour plus d’informations concernant l’accès à l’élément de pointeur, consultez la section [Opérateur d’accès à l’élément de pointeur []](pointer-related-operators.md#pointer-element-access-operator-) de l’article [Opérateurs associés au pointeur](pointer-related-operators.md).</span><span class="sxs-lookup"><span data-stu-id="7059e-131">For information about pointer element access, see the [Pointer element access operator []](pointer-related-operators.md#pointer-element-access-operator-) section of the [Pointer related operators](pointer-related-operators.md) article.</span></span>

<span data-ttu-id="7059e-132">Vous utilisez également des crochets pour spécifier des [attributs](../../programming-guide/concepts/attributes/index.md) :</span><span class="sxs-lookup"><span data-stu-id="7059e-132">You also use square brackets to specify [attributes](../../programming-guide/concepts/attributes/index.md):</span></span>

```csharp
[System.Diagnostics.Conditional("DEBUG")]
void TraceMethod() {}
```

## <a name="null-conditional-operators--and-"></a><span data-ttu-id="7059e-133">Opérateurs conditionnels Null ?.</span><span class="sxs-lookup"><span data-stu-id="7059e-133">Null-conditional operators ?.</span></span> <span data-ttu-id="7059e-134">et ?[]</span><span class="sxs-lookup"><span data-stu-id="7059e-134">and ?[]</span></span>

<span data-ttu-id="7059e-135">Disponible en C# 6 et versions ultérieures, un opérateur conditionnel null applique [member access](#member-access-expression-)un accès de `?.`membre, ou d’accès `?[]`à l' [élément](#indexer-operator-),, à son opérande uniquement si cet opérande a la valeur non null ; Sinon, elle retourne `null`.</span><span class="sxs-lookup"><span data-stu-id="7059e-135">Available in C# 6 and later, a null-conditional operator applies a [member access](#member-access-expression-), `?.`, or [element access](#indexer-operator-), `?[]`, operation to its operand only if that operand evaluates to non-null; otherwise, it returns `null`.</span></span> <span data-ttu-id="7059e-136">C'est</span><span class="sxs-lookup"><span data-stu-id="7059e-136">That is,</span></span>

- <span data-ttu-id="7059e-137">Si `a` prend la valeur `null`, le résultat de `a?.x` ou `a?[x]` est `null`.</span><span class="sxs-lookup"><span data-stu-id="7059e-137">If `a` evaluates to `null`, the result of `a?.x` or `a?[x]` is `null`.</span></span>
- <span data-ttu-id="7059e-138">Si `a` prend la valeur non null, le résultat `a?.x` de ou `a?[x]` est le même que le résultat de `a.x` ou `a[x]`, respectivement.</span><span class="sxs-lookup"><span data-stu-id="7059e-138">If `a` evaluates to non-null, the result of `a?.x` or `a?[x]` is the same as the result of `a.x` or `a[x]`, respectively.</span></span>

  > [!NOTE]
  > <span data-ttu-id="7059e-139">Si `a.x` ou `a[x]` lèvent une exception, `a?.x` ou `a?[x]` lèvent la même exception pour la valeur non `a`null.</span><span class="sxs-lookup"><span data-stu-id="7059e-139">If `a.x` or `a[x]` throws an exception, `a?.x` or `a?[x]` would throw the same exception for non-null `a`.</span></span> <span data-ttu-id="7059e-140">Par exemple, si `a` est une instance de tableau non null et `x` se trouve en dehors des limites `a`de `a?[x]` , lèvera un <xref:System.IndexOutOfRangeException>.</span><span class="sxs-lookup"><span data-stu-id="7059e-140">For example, if `a` is a non-null array instance and `x` is outside the bounds of `a`, `a?[x]` would throw an <xref:System.IndexOutOfRangeException>.</span></span>

<span data-ttu-id="7059e-141">Les opérateurs conditionnels Null ont un effet de court-circuit.</span><span class="sxs-lookup"><span data-stu-id="7059e-141">The null-conditional operators are short-circuiting.</span></span> <span data-ttu-id="7059e-142">Autrement dit, si une opération dans une chaîne d’opérations d’accès au membre ou à l’élément conditionnelles retourne une valeur `null`, le reste de la chaîne ne s’exécute pas.</span><span class="sxs-lookup"><span data-stu-id="7059e-142">That is, if one operation in a chain of conditional member or element access operations returns `null`, the rest of the chain doesn't execute.</span></span> <span data-ttu-id="7059e-143">Dans l’exemple suivant, `B` n’est pas évalué si `A` prend la valeur `null` et `C` n’est pas évalué si `A` ou `B` prend la valeur `null` :</span><span class="sxs-lookup"><span data-stu-id="7059e-143">In the following example, `B` is not evaluated if `A` evaluates to `null` and `C` is not evaluated if `A` or `B` evaluates to `null`:</span></span>

```csharp
A?.B?.Do(C);
A?.B?[C];
```

<span data-ttu-id="7059e-144">L’exemple suivant illustre l’utilisation des opérateurs `?.` et `?[]` :</span><span class="sxs-lookup"><span data-stu-id="7059e-144">The following example demonstrates the usage of the `?.` and `?[]` operators:</span></span>

[!code-csharp-interactive[null-conditional operators](snippets/MemberAccessOperators.cs#NullConditional)]

<span data-ttu-id="7059e-145">L’exemple précédent utilise également l' [ `??` opérateur de fusion Null](null-coalescing-operator.md) pour spécifier une autre expression à évaluer si le résultat d’une opération conditionnelle null est. `null`</span><span class="sxs-lookup"><span data-stu-id="7059e-145">The preceding example also uses the [null-coalescing operator `??`](null-coalescing-operator.md) to specify an alternative expression to evaluate in case the result of a null-conditional operation is `null`.</span></span>

<span data-ttu-id="7059e-146">Si `a.x` ou `a[x]` est un type `T`valeur n’acceptant pas les `a?.x` valeurs `a?[x]` null, ou est du [type](../builtin-types/nullable-value-types.md) `T?`valeur Nullable correspondant.</span><span class="sxs-lookup"><span data-stu-id="7059e-146">If `a.x` or `a[x]` is of a non-nullable value type `T`, `a?.x` or `a?[x]` is of the corresponding [nullable value type](../builtin-types/nullable-value-types.md) `T?`.</span></span> <span data-ttu-id="7059e-147">Si vous avez besoin d’une expression `T`de type, appliquez l’opérateur `??` de fusion Null à une expression conditionnelle null, comme le montre l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="7059e-147">If you need an expression of type `T`, apply the null-coalescing operator `??` to a null-conditional expression, as the following example shows:</span></span>

[!code-csharp-interactive[null-conditional with null-coalescing](snippets/MemberAccessOperators.cs#NullConditionalWithNullCoalescing)]

<span data-ttu-id="7059e-148">Dans l’exemple précédent, si vous n’utilisez pas `??` l’opérateur `numbers?.Length < 2` , prend la `false` valeur `numbers` lorsque `null`est.</span><span class="sxs-lookup"><span data-stu-id="7059e-148">In the preceding example, if you don't use the `??` operator, `numbers?.Length < 2` evaluates to `false` when `numbers` is `null`.</span></span>

<span data-ttu-id="7059e-149">L’opérateur d’accès aux membres conditionnels null `?.` est également appelé l’opérateur Elvis.</span><span class="sxs-lookup"><span data-stu-id="7059e-149">The null-conditional member access operator `?.` is also known as the Elvis operator.</span></span>

> [!NOTE]
> <span data-ttu-id="7059e-150">En C# 8, l' [opérateur null-indulgent avec](null-forgiving.md) met fin à la liste des opérations conditionnelles null précédentes.</span><span class="sxs-lookup"><span data-stu-id="7059e-150">In C# 8, the [null-forgiving operator](null-forgiving.md) terminates the list of preceding null-conditional operations.</span></span> <span data-ttu-id="7059e-151">Par exemple, l’expression `x?.y!.z` est analysée comme `(x?.y)!.z`.</span><span class="sxs-lookup"><span data-stu-id="7059e-151">For example, the expression `x?.y!.z` is parsed as `(x?.y)!.z`.</span></span> <span data-ttu-id="7059e-152">En raison de cette interprétation `z` , est évalué même `x` si `null`est, ce qui peut entraîner <xref:System.NullReferenceException>un.</span><span class="sxs-lookup"><span data-stu-id="7059e-152">Due to this interpretation, `z` is evaluated even if `x` is `null`, which may result in a <xref:System.NullReferenceException>.</span></span>

### <a name="thread-safe-delegate-invocation"></a><span data-ttu-id="7059e-153">Appel de délégué thread-safe</span><span class="sxs-lookup"><span data-stu-id="7059e-153">Thread-safe delegate invocation</span></span>

<span data-ttu-id="7059e-154">Utilisez l’opérateur `?.` pour vérifier si un délégué est non Null et l’appeler de manière thread-safe (par exemple, quand vous [déclenchez un événement](../../../standard/events/how-to-raise-and-consume-events.md)), comme illustré dans le code suivant :</span><span class="sxs-lookup"><span data-stu-id="7059e-154">Use the `?.` operator to check if a delegate is non-null and invoke it in a thread-safe way (for example, when you [raise an event](../../../standard/events/how-to-raise-and-consume-events.md)), as the following code shows:</span></span>

```csharp
PropertyChanged?.Invoke(…)
```

<span data-ttu-id="7059e-155">Ce code est équivalent au code suivant que vous utiliseriez dans C# 5 ou une version antérieure :</span><span class="sxs-lookup"><span data-stu-id="7059e-155">That code is equivalent to the following code that you would use in C# 5 or earlier:</span></span>

```csharp
var handler = this.PropertyChanged;
if (handler != null)
{
    handler(…);
}
```

<span data-ttu-id="7059e-156">C’est une façon thread-safe de s’assurer que seule une valeur non `handler` null est appelée.</span><span class="sxs-lookup"><span data-stu-id="7059e-156">That is a thread-safe way to ensure that only a non-null `handler` is invoked.</span></span> <span data-ttu-id="7059e-157">Étant donné que les instances de délégué sont immuables, aucun thread ne peut modifier la `handler` valeur référencée par la variable locale.</span><span class="sxs-lookup"><span data-stu-id="7059e-157">Because delegate instances are immutable, no thread can change the value referenced by the `handler` local variable.</span></span> <span data-ttu-id="7059e-158">En particulier, si le code exécuté par un autre thread annule son abonnement `PropertyChanged` à l' `PropertyChanged` événement `null` et `handler` devient avant l’appel de, la valeur référencée par `handler` reste inchangée.</span><span class="sxs-lookup"><span data-stu-id="7059e-158">In particular, if the code executed by another thread unsubscribes from the `PropertyChanged` event and `PropertyChanged` becomes `null` before `handler` is invoked, the value referenced by `handler` remains unaffected.</span></span> <span data-ttu-id="7059e-159">L' `?.` opérateur évalue son opérande de gauche un peu plus d' `null` une fois, ce qui garantit qu’il ne peut pas être modifié après avoir été vérifié comme non null.</span><span class="sxs-lookup"><span data-stu-id="7059e-159">The `?.` operator evaluates its left-hand operand no more than once, guaranteeing that it cannot be changed to `null` after being verified as non-null.</span></span>

## <a name="invocation-expression-"></a><span data-ttu-id="7059e-160">Expression d’appel ()</span><span class="sxs-lookup"><span data-stu-id="7059e-160">Invocation expression ()</span></span>

<span data-ttu-id="7059e-161">Utilisez des parenthèses, `()`, pour appeler une [méthode](../../programming-guide/classes-and-structs/methods.md) ou un [délégué](../../programming-guide/delegates/index.md).</span><span class="sxs-lookup"><span data-stu-id="7059e-161">Use parentheses, `()`, to call a [method](../../programming-guide/classes-and-structs/methods.md) or invoke a [delegate](../../programming-guide/delegates/index.md).</span></span>

<span data-ttu-id="7059e-162">L’exemple suivant montre comment appeler une méthode, avec ou sans arguments, et un délégué :</span><span class="sxs-lookup"><span data-stu-id="7059e-162">The following example demonstrates how to call a method, with or without arguments, and invoke a delegate:</span></span>

[!code-csharp-interactive[invocation with ()](snippets/MemberAccessOperators.cs#Invocation)]

<span data-ttu-id="7059e-163">Vous utilisez également des parenthèses quand vous appelez un [constructeur](../../programming-guide/classes-and-structs/constructors.md) avec l’opérateur [`new`](new-operator.md).</span><span class="sxs-lookup"><span data-stu-id="7059e-163">You also use parentheses when you invoke a [constructor](../../programming-guide/classes-and-structs/constructors.md) with the [`new`](new-operator.md) operator.</span></span>

### <a name="other-usages-of-"></a><span data-ttu-id="7059e-164">Autres utilisations de ()</span><span class="sxs-lookup"><span data-stu-id="7059e-164">Other usages of ()</span></span>

<span data-ttu-id="7059e-165">Vous utilisez également des parenthèses pour ajuster l’ordre dans lequel évaluer les opérations dans une expression.</span><span class="sxs-lookup"><span data-stu-id="7059e-165">You also use parentheses to adjust the order in which to evaluate operations in an expression.</span></span> <span data-ttu-id="7059e-166">Pour plus d’informations, consultez [Opérateurs C#](index.md).</span><span class="sxs-lookup"><span data-stu-id="7059e-166">For more information, see [C# operators](index.md).</span></span>

<span data-ttu-id="7059e-167">[Les expressions cast](type-testing-and-cast.md#cast-expression), qui effectuent des conversions de type explicites, utilisent aussi des parenthèses.</span><span class="sxs-lookup"><span data-stu-id="7059e-167">[Cast expressions](type-testing-and-cast.md#cast-expression), which perform explicit type conversions, also use parentheses.</span></span>

## <a name="index-from-end-operator-"></a><span data-ttu-id="7059e-168">Index de fin d’opérateur ^</span><span class="sxs-lookup"><span data-stu-id="7059e-168">Index from end operator ^</span></span>

<span data-ttu-id="7059e-169">Disponible en C# 8,0 et versions ultérieures `^` , l’opérateur indique la position de l’élément à partir de la fin d’une séquence.</span><span class="sxs-lookup"><span data-stu-id="7059e-169">Available in C# 8.0 and later, the `^` operator indicates the element position from the end of a sequence.</span></span> <span data-ttu-id="7059e-170">Pour une séquence de longueur `length`, `^n` pointe vers l’élément avec décalage `length - n` à partir du début d’une séquence.</span><span class="sxs-lookup"><span data-stu-id="7059e-170">For a sequence of length `length`, `^n` points to the element with offset `length - n` from the start of a sequence.</span></span> <span data-ttu-id="7059e-171">Par exemple, `^1` pointe vers le dernier élément d’une séquence et `^length` pointe vers le premier élément d’une séquence.</span><span class="sxs-lookup"><span data-stu-id="7059e-171">For example, `^1` points to the last element of a sequence and `^length` points to the first element of a sequence.</span></span>

[!code-csharp[index from end](snippets/MemberAccessOperators.cs#IndexFromEnd)]

<span data-ttu-id="7059e-172">Comme le montre l’exemple précédent, `^e` expression est du <xref:System.Index?displayProperty=nameWithType> type.</span><span class="sxs-lookup"><span data-stu-id="7059e-172">As the preceding example shows, expression `^e` is of the <xref:System.Index?displayProperty=nameWithType> type.</span></span> <span data-ttu-id="7059e-173">Dans Expression `^e`, le résultat de `e` doit être implicitement convertible en `int`.</span><span class="sxs-lookup"><span data-stu-id="7059e-173">In expression `^e`, the result of `e` must be implicitly convertible to `int`.</span></span>

<span data-ttu-id="7059e-174">Vous pouvez également utiliser l' `^` opérateur avec l' [opérateur Range](#range-operator-) pour créer une plage d’index.</span><span class="sxs-lookup"><span data-stu-id="7059e-174">You can also use the `^` operator with the [range operator](#range-operator-) to create a range of indices.</span></span> <span data-ttu-id="7059e-175">Pour plus d’informations, consultez [index et plages](../../tutorials/ranges-indexes.md).</span><span class="sxs-lookup"><span data-stu-id="7059e-175">For more information, see [Indices and ranges](../../tutorials/ranges-indexes.md).</span></span>

## <a name="range-operator-"></a><span data-ttu-id="7059e-176">Opérateur de plage..</span><span class="sxs-lookup"><span data-stu-id="7059e-176">Range operator ..</span></span>

<span data-ttu-id="7059e-177">Disponible en C# 8,0 et versions ultérieures `..` , l’opérateur spécifie le début et la fin d’une plage d’index comme opérandes.</span><span class="sxs-lookup"><span data-stu-id="7059e-177">Available in C# 8.0 and later, the `..` operator specifies the start and end of a range of indices as its operands.</span></span> <span data-ttu-id="7059e-178">L’opérande de gauche est un début *inclusif* d’une plage.</span><span class="sxs-lookup"><span data-stu-id="7059e-178">The left-hand operand is an *inclusive* start of a range.</span></span> <span data-ttu-id="7059e-179">L’opérande de droite est une extrémité *exclusive* d’une plage.</span><span class="sxs-lookup"><span data-stu-id="7059e-179">The right-hand operand is an *exclusive* end of a range.</span></span> <span data-ttu-id="7059e-180">L’un ou l’autre des opérandes peut être un index à partir du début ou de la fin d’une séquence, comme le montre l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="7059e-180">Either of operands can be an index from the start or from the end of a sequence, as the following example shows:</span></span>

[!code-csharp[range examples](snippets/MemberAccessOperators.cs#Ranges)]

<span data-ttu-id="7059e-181">Comme le montre l’exemple précédent, `a..b` expression est du <xref:System.Range?displayProperty=nameWithType> type.</span><span class="sxs-lookup"><span data-stu-id="7059e-181">As the preceding example shows, expression `a..b` is of the <xref:System.Range?displayProperty=nameWithType> type.</span></span> <span data-ttu-id="7059e-182">Dans Expression `a..b`, les résultats de `a` et `b` doivent être implicitement convertibles `int` en <xref:System.Index>ou.</span><span class="sxs-lookup"><span data-stu-id="7059e-182">In expression `a..b`, the results of `a` and `b` must be implicitly convertible to `int` or <xref:System.Index>.</span></span>

<span data-ttu-id="7059e-183">Vous pouvez omettre l’un des opérandes de l' `..` opérateur pour obtenir une plage ouverte :</span><span class="sxs-lookup"><span data-stu-id="7059e-183">You can omit any of the operands of the `..` operator to obtain an open-ended range:</span></span>

- <span data-ttu-id="7059e-184">`a..` équivaut à `a..^0`</span><span class="sxs-lookup"><span data-stu-id="7059e-184">`a..` is equivalent to `a..^0`</span></span>
- <span data-ttu-id="7059e-185">`..b` équivaut à `0..b`</span><span class="sxs-lookup"><span data-stu-id="7059e-185">`..b` is equivalent to `0..b`</span></span>
- <span data-ttu-id="7059e-186">`..` équivaut à `0..^0`</span><span class="sxs-lookup"><span data-stu-id="7059e-186">`..` is equivalent to `0..^0`</span></span>

[!code-csharp[ranges with omitted operands](snippets/MemberAccessOperators.cs#RangesOptional)]

<span data-ttu-id="7059e-187">Pour plus d’informations, consultez [index et plages](../../tutorials/ranges-indexes.md).</span><span class="sxs-lookup"><span data-stu-id="7059e-187">For more information, see [Indices and ranges](../../tutorials/ranges-indexes.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="7059e-188">Capacité de surcharge de l’opérateur</span><span class="sxs-lookup"><span data-stu-id="7059e-188">Operator overloadability</span></span>

<span data-ttu-id="7059e-189">Les `.`opérateurs `()`, `^`, et `..` ne peuvent pas être surchargés.</span><span class="sxs-lookup"><span data-stu-id="7059e-189">The `.`, `()`, `^`, and `..` operators cannot be overloaded.</span></span> <span data-ttu-id="7059e-190">L’opérateur `[]` est également considéré comme un opérateur non surchargeable.</span><span class="sxs-lookup"><span data-stu-id="7059e-190">The `[]` operator is also considered a non-overloadable operator.</span></span> <span data-ttu-id="7059e-191">Utilisez des [indexeurs](../../programming-guide/indexers/index.md) pour prendre en charge l’indexation avec des types définis par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="7059e-191">Use [indexers](../../programming-guide/indexers/index.md) to support indexing with user-defined types.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="7059e-192">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="7059e-192">C# language specification</span></span>

<span data-ttu-id="7059e-193">Pour plus d’informations, consultez les sections suivantes de la [spécification du langage C#](~/_csharplang/spec/introduction.md) :</span><span class="sxs-lookup"><span data-stu-id="7059e-193">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="7059e-194">Accès aux membres</span><span class="sxs-lookup"><span data-stu-id="7059e-194">Member access</span></span>](~/_csharplang/spec/expressions.md#member-access)
- [<span data-ttu-id="7059e-195">Accès aux éléments</span><span class="sxs-lookup"><span data-stu-id="7059e-195">Element access</span></span>](~/_csharplang/spec/expressions.md#element-access)
- [<span data-ttu-id="7059e-196">Opérateur conditionnel Null</span><span class="sxs-lookup"><span data-stu-id="7059e-196">Null-conditional operator</span></span>](~/_csharplang/spec/expressions.md#null-conditional-operator)
- [<span data-ttu-id="7059e-197">Expressions d’appels</span><span class="sxs-lookup"><span data-stu-id="7059e-197">Invocation expressions</span></span>](~/_csharplang/spec/expressions.md#invocation-expressions)

<span data-ttu-id="7059e-198">Pour plus d’informations sur les index et les plages, consultez la [Remarque relative](~/_csharplang/proposals/csharp-8.0/ranges.md)à la proposition de fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="7059e-198">For more information about indices and ranges, see the [feature proposal note](~/_csharplang/proposals/csharp-8.0/ranges.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7059e-199">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7059e-199">See also</span></span>

- [<span data-ttu-id="7059e-200">Référence C#</span><span class="sxs-lookup"><span data-stu-id="7059e-200">C# reference</span></span>](../index.md)
- [<span data-ttu-id="7059e-201">Opérateurs C#</span><span class="sxs-lookup"><span data-stu-id="7059e-201">C# operators</span></span>](index.md)
- [<span data-ttu-id="7059e-202">?? (opérateur de fusion Null)</span><span class="sxs-lookup"><span data-stu-id="7059e-202">?? (null-coalescing operator)</span></span>](null-coalescing-operator.md)
- [<span data-ttu-id="7059e-203">::, opérateur</span><span class="sxs-lookup"><span data-stu-id="7059e-203">:: operator</span></span>](namespace-alias-qualifier.md)
