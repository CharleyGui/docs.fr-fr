---
title: Opérateurs et expressions d’accès aux membres - Référence C
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
ms.openlocfilehash: 4e213c92ae08edd8d537017e474c33200cb4c22c
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81738723"
---
# <a name="member-access-operators-and-expressions-c-reference"></a><span data-ttu-id="d98a4-103">Opérateurs et expressions d’accès aux membres (référence C)</span><span class="sxs-lookup"><span data-stu-id="d98a4-103">Member access operators and expressions (C# reference)</span></span>

<span data-ttu-id="d98a4-104">Vous pouvez utiliser les opérateurs et expressions suivants lorsque vous accédez à un membre type :</span><span class="sxs-lookup"><span data-stu-id="d98a4-104">You can use the following operators and expressions when you access a type member:</span></span>

- <span data-ttu-id="d98a4-105">(accès des membres) : accéder à un membre d’un espace de nom ou d’un type [ `.` ](#member-access-expression-)</span><span class="sxs-lookup"><span data-stu-id="d98a4-105">[`.` (member access)](#member-access-expression-): to access a member of a namespace or a type</span></span>
- <span data-ttu-id="d98a4-106">[(accès à l’élément de tableau ou à l’indexeur) : accéder à un élément de tableau ou à un indexeur de type `[]` ](#indexer-operator-)</span><span class="sxs-lookup"><span data-stu-id="d98a4-106">[`[]` (array element or indexer access)](#indexer-operator-): to access an array element or a type indexer</span></span>
- <span data-ttu-id="d98a4-107">[et `?[]` (opérateurs non conditionnels) : effectuer une opération d’accès à un membre ou à un élément uniquement si un opérande n’est pas `?.` ](#null-conditional-operators--and-)nul</span><span class="sxs-lookup"><span data-stu-id="d98a4-107">[`?.` and `?[]` (null-conditional operators)](#null-conditional-operators--and-): to perform a member or element access operation only if an operand is non-null</span></span>
- <span data-ttu-id="d98a4-108">(invocation) : appeler une méthode consultée ou invoquer un délégué [ `()` ](#invocation-expression-)</span><span class="sxs-lookup"><span data-stu-id="d98a4-108">[`()` (invocation)](#invocation-expression-): to call an accessed method or invoke a delegate</span></span>
- <span data-ttu-id="d98a4-109">[(index à partir de la fin) : indiquer que la position de l’élément est à partir de la fin d’une séquence `^` ](#index-from-end-operator-)</span><span class="sxs-lookup"><span data-stu-id="d98a4-109">[`^` (index from end)](#index-from-end-operator-): to indicate that the element position is from the end of a sequence</span></span>
- <span data-ttu-id="d98a4-110">(gamme) : pour spécifier une gamme d’indices que vous pouvez utiliser pour obtenir une gamme d’éléments séquences [ `..` ](#range-operator-)</span><span class="sxs-lookup"><span data-stu-id="d98a4-110">[`..` (range)](#range-operator-): to specify a range of indices that you can use to obtain a range of sequence elements</span></span>

## <a name="member-access-expression-"></a><span data-ttu-id="d98a4-111">Expression d’accès des membres .</span><span class="sxs-lookup"><span data-stu-id="d98a4-111">Member access expression .</span></span>

<span data-ttu-id="d98a4-112">Le jeton `.` sert à accéder à l’un des membres d’un espace de noms ou d’un type, comme le montrent les exemples suivants :</span><span class="sxs-lookup"><span data-stu-id="d98a4-112">You use the `.` token to access a member of a namespace or a type, as the following examples demonstrate:</span></span>

- <span data-ttu-id="d98a4-113">Utiliser `.` pour accéder à un espace nom imbriqué dans [ `using` ](../keywords/using-directive.md) un espace nom, comme le montre l’exemple suivant d’une directive :</span><span class="sxs-lookup"><span data-stu-id="d98a4-113">Use `.` to access a nested namespace within a namespace, as the following example of a [`using` directive](../keywords/using-directive.md) shows:</span></span>

  [!code-csharp[nested namespaces](snippets/MemberAccessOperators.cs#NestedNamespace)]

- <span data-ttu-id="d98a4-114">Utilisez `.` pour former un *nom qualifié* permettant d’accéder à un type dans un espace de noms, comme le montre le code suivant :</span><span class="sxs-lookup"><span data-stu-id="d98a4-114">Use `.` to form a *qualified name* to access a type within a namespace, as the following code shows:</span></span>

  [!code-csharp[qualified name](snippets/MemberAccessOperators.cs#QualifiedName)]

  <span data-ttu-id="d98a4-115">Utilisez [ `using` ](../keywords/using-directive.md) une directive pour rendre facultatif l’utilisation de noms qualifiés.</span><span class="sxs-lookup"><span data-stu-id="d98a4-115">Use a [`using` directive](../keywords/using-directive.md) to make the use of qualified names optional.</span></span>

- <span data-ttu-id="d98a4-116">Utilisez `.` pour accéder aux [membres de type](../../programming-guide/classes-and-structs/index.md#members), statiques et non statiques, comme le montre le code suivant :</span><span class="sxs-lookup"><span data-stu-id="d98a4-116">Use `.` to access [type members](../../programming-guide/classes-and-structs/index.md#members), static and non-static, as the following code shows:</span></span>

  [!code-csharp-interactive[type members](snippets/MemberAccessOperators.cs#TypeMemberAccess)]

<span data-ttu-id="d98a4-117">Vous pouvez également utiliser `.` pour accéder à une [méthode d’extension](../../programming-guide/classes-and-structs/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="d98a4-117">You can also use `.` to access an [extension method](../../programming-guide/classes-and-structs/extension-methods.md).</span></span>

## <a name="indexer-operator-"></a><span data-ttu-id="d98a4-118">Opérateur d’indexeur []</span><span class="sxs-lookup"><span data-stu-id="d98a4-118">Indexer operator []</span></span>

<span data-ttu-id="d98a4-119">Les crochets, `[]`, sont généralement utilisés pour l’accès à un élément tableau, indexeur ou pointeur.</span><span class="sxs-lookup"><span data-stu-id="d98a4-119">Square brackets, `[]`, are typically used for array, indexer, or pointer element access.</span></span>

### <a name="array-access"></a><span data-ttu-id="d98a4-120">Accès aux tableaux</span><span class="sxs-lookup"><span data-stu-id="d98a4-120">Array access</span></span>

<span data-ttu-id="d98a4-121">L’exemple suivant montre comment accéder à des éléments tableau :</span><span class="sxs-lookup"><span data-stu-id="d98a4-121">The following example demonstrates how to access array elements:</span></span>

[!code-csharp-interactive[array access](snippets/MemberAccessOperators.cs#Arrays)]

<span data-ttu-id="d98a4-122">Si un index de tableau est en dehors des limites de la dimension correspondante d’un tableau, une <xref:System.IndexOutOfRangeException> est levée.</span><span class="sxs-lookup"><span data-stu-id="d98a4-122">If an array index is outside the bounds of the corresponding dimension of an array, an <xref:System.IndexOutOfRangeException> is thrown.</span></span>

<span data-ttu-id="d98a4-123">Comme le montre l’exemple précédent, vous utilisez également des crochets quand vous déclarez un type tableau ou instanciez une instance de tableau.</span><span class="sxs-lookup"><span data-stu-id="d98a4-123">As the preceding example shows, you also use square brackets when you declare an array type or instantiate an array instance.</span></span>

<span data-ttu-id="d98a4-124">Pour plus d’informations sur les tableaux, consultez [Tableaux](../../programming-guide/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="d98a4-124">For more information about arrays, see [Arrays](../../programming-guide/arrays/index.md).</span></span>

### <a name="indexer-access"></a><span data-ttu-id="d98a4-125">Accès aux indexeurs</span><span class="sxs-lookup"><span data-stu-id="d98a4-125">Indexer access</span></span>

<span data-ttu-id="d98a4-126">L’exemple suivant utilise <xref:System.Collections.Generic.Dictionary%602> le type .NET pour démontrer l’accès à l’indexeur :</span><span class="sxs-lookup"><span data-stu-id="d98a4-126">The following example uses the .NET <xref:System.Collections.Generic.Dictionary%602> type to demonstrate indexer access:</span></span>

[!code-csharp-interactive[indexer access](snippets/MemberAccessOperators.cs#Indexers)]

<span data-ttu-id="d98a4-127">Les indexeurs vous permettent d’indexer des instances d’un type défini par l’utilisateur en procédant de la même façon que pour l’indexation de tableau.</span><span class="sxs-lookup"><span data-stu-id="d98a4-127">Indexers allow you to index instances of a user-defined type in the similar way as array indexing.</span></span> <span data-ttu-id="d98a4-128">Contrairement aux indices de tableau, qui doivent être integer, les paramètres de l’indexeur peuvent être déclarés être de n’importe quel type.</span><span class="sxs-lookup"><span data-stu-id="d98a4-128">Unlike array indices, which must be integer, the indexer parameters can be declared to be of any type.</span></span>

<span data-ttu-id="d98a4-129">Pour plus d’informations sur les indexeurs, consultez [Indexeurs](../../programming-guide/indexers/index.md).</span><span class="sxs-lookup"><span data-stu-id="d98a4-129">For more information about indexers, see [Indexers](../../programming-guide/indexers/index.md).</span></span>

### <a name="other-usages-of-"></a><span data-ttu-id="d98a4-130">Autres utilisations de []</span><span class="sxs-lookup"><span data-stu-id="d98a4-130">Other usages of []</span></span>

<span data-ttu-id="d98a4-131">Pour plus d’informations concernant l’accès à l’élément de pointeur, consultez la section [Opérateur d’accès à l’élément de pointeur []](pointer-related-operators.md#pointer-element-access-operator-) de l’article [Opérateurs associés au pointeur](pointer-related-operators.md).</span><span class="sxs-lookup"><span data-stu-id="d98a4-131">For information about pointer element access, see the [Pointer element access operator []](pointer-related-operators.md#pointer-element-access-operator-) section of the [Pointer related operators](pointer-related-operators.md) article.</span></span>

<span data-ttu-id="d98a4-132">Vous utilisez également des crochets pour spécifier des [attributs](../../programming-guide/concepts/attributes/index.md) :</span><span class="sxs-lookup"><span data-stu-id="d98a4-132">You also use square brackets to specify [attributes](../../programming-guide/concepts/attributes/index.md):</span></span>

```csharp
[System.Diagnostics.Conditional("DEBUG")]
void TraceMethod() {}
```

## <a name="null-conditional-operators--and-"></a><span data-ttu-id="d98a4-133">Opérateurs conditionnels Null ?.</span><span class="sxs-lookup"><span data-stu-id="d98a4-133">Null-conditional operators ?.</span></span> <span data-ttu-id="d98a4-134">et ?[]</span><span class="sxs-lookup"><span data-stu-id="d98a4-134">and ?[]</span></span>

<span data-ttu-id="d98a4-135">Disponible en C 6 et plus tard, un opérateur `?.`sans condition `?[]`applique un accès de [membre,](#member-access-expression-), ou [l’accès à l’élément](#indexer-operator-), , opération à son opérande seulement si cet opérand évalue à non-null; sinon, il `null`revient .</span><span class="sxs-lookup"><span data-stu-id="d98a4-135">Available in C# 6 and later, a null-conditional operator applies a [member access](#member-access-expression-), `?.`, or [element access](#indexer-operator-), `?[]`, operation to its operand only if that operand evaluates to non-null; otherwise, it returns `null`.</span></span> <span data-ttu-id="d98a4-136">C'est</span><span class="sxs-lookup"><span data-stu-id="d98a4-136">That is,</span></span>

- <span data-ttu-id="d98a4-137">Si `a` évalue `null`à , `a?.x` le `a?[x]` `null`résultat ou est .</span><span class="sxs-lookup"><span data-stu-id="d98a4-137">If `a` evaluates to `null`, the result of `a?.x` or `a?[x]` is `null`.</span></span>
- <span data-ttu-id="d98a4-138">Si `a` l’on évalue à non-null, le résultat `a?.x` ou `a?[x]` est le même que le résultat ou `a.x` `a[x]`, respectivement.</span><span class="sxs-lookup"><span data-stu-id="d98a4-138">If `a` evaluates to non-null, the result of `a?.x` or `a?[x]` is the same as the result of `a.x` or `a[x]`, respectively.</span></span>

  > [!NOTE]
  > <span data-ttu-id="d98a4-139">Si `a.x` `a[x]` ou jette une `a?.x` `a?[x]` exception, ou jetterait la `a`même exception pour non-null .</span><span class="sxs-lookup"><span data-stu-id="d98a4-139">If `a.x` or `a[x]` throws an exception, `a?.x` or `a?[x]` would throw the same exception for non-null `a`.</span></span> <span data-ttu-id="d98a4-140">Par exemple, `a` si est une instance `x` de tableau non-null et est en dehors des limites de `a`, `a?[x]` jetterait un <xref:System.IndexOutOfRangeException>.</span><span class="sxs-lookup"><span data-stu-id="d98a4-140">For example, if `a` is a non-null array instance and `x` is outside the bounds of `a`, `a?[x]` would throw an <xref:System.IndexOutOfRangeException>.</span></span>

<span data-ttu-id="d98a4-141">Les opérateurs conditionnels Null ont un effet de court-circuit.</span><span class="sxs-lookup"><span data-stu-id="d98a4-141">The null-conditional operators are short-circuiting.</span></span> <span data-ttu-id="d98a4-142">Autrement dit, si une opération dans une chaîne d’opérations d’accès au membre ou à l’élément conditionnelles retourne une valeur `null`, le reste de la chaîne ne s’exécute pas.</span><span class="sxs-lookup"><span data-stu-id="d98a4-142">That is, if one operation in a chain of conditional member or element access operations returns `null`, the rest of the chain doesn't execute.</span></span> <span data-ttu-id="d98a4-143">Dans l’exemple suivant, `B` n’est pas évalué si `A` prend la valeur `null` et `C` n’est pas évalué si `A` ou `B` prend la valeur `null` :</span><span class="sxs-lookup"><span data-stu-id="d98a4-143">In the following example, `B` is not evaluated if `A` evaluates to `null` and `C` is not evaluated if `A` or `B` evaluates to `null`:</span></span>

```csharp
A?.B?.Do(C);
A?.B?[C];
```

<span data-ttu-id="d98a4-144">L’exemple suivant illustre l’utilisation des opérateurs `?.` et `?[]` :</span><span class="sxs-lookup"><span data-stu-id="d98a4-144">The following example demonstrates the usage of the `?.` and `?[]` operators:</span></span>

[!code-csharp-interactive[null-conditional operators](snippets/MemberAccessOperators.cs#NullConditional)]

<span data-ttu-id="d98a4-145">L’exemple précédent utilise également [l’opérateur `??` de fusion nulle](null-coalescing-operator.md) pour spécifier une expression `null`alternative à évaluer au cas où le résultat d’une opération non conditionnelle est .</span><span class="sxs-lookup"><span data-stu-id="d98a4-145">The preceding example also uses the [null-coalescing operator `??`](null-coalescing-operator.md) to specify an alternative expression to evaluate in case the result of a null-conditional operation is `null`.</span></span>

<span data-ttu-id="d98a4-146">Si `a.x` `a[x]` ou est d’un type `T` `a?.x` de `a?[x]` valeur non-nullable , ou est du [type](../builtin-types/nullable-value-types.md) `T?`de valeur nulle correspondante .</span><span class="sxs-lookup"><span data-stu-id="d98a4-146">If `a.x` or `a[x]` is of a non-nullable value type `T`, `a?.x` or `a?[x]` is of the corresponding [nullable value type](../builtin-types/nullable-value-types.md) `T?`.</span></span> <span data-ttu-id="d98a4-147">Si vous avez besoin `T`d’une expression de type, appliquez l’opérateur `??` de fusion nulle à une expression non conditionnelle, comme le montre l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="d98a4-147">If you need an expression of type `T`, apply the null-coalescing operator `??` to a null-conditional expression, as the following example shows:</span></span>

[!code-csharp-interactive[null-conditional with null-coalescing](snippets/MemberAccessOperators.cs#NullConditionalWithNullCoalescing)]

<span data-ttu-id="d98a4-148">Dans l’exemple précédent, si vous `??` n’utilisez pas l’opérateur, `numbers?.Length < 2` évalue à `false` quand `numbers` est `null`.</span><span class="sxs-lookup"><span data-stu-id="d98a4-148">In the preceding example, if you don't use the `??` operator, `numbers?.Length < 2` evaluates to `false` when `numbers` is `null`.</span></span>

<span data-ttu-id="d98a4-149">L’opérateur d’accès aux membres conditionnels null `?.` est également appelé l’opérateur Elvis.</span><span class="sxs-lookup"><span data-stu-id="d98a4-149">The null-conditional member access operator `?.` is also known as the Elvis operator.</span></span>

### <a name="thread-safe-delegate-invocation"></a><span data-ttu-id="d98a4-150">Appel de délégué thread-safe</span><span class="sxs-lookup"><span data-stu-id="d98a4-150">Thread-safe delegate invocation</span></span>

<span data-ttu-id="d98a4-151">Utilisez l’opérateur `?.` pour vérifier si un délégué est non Null et l’appeler de manière thread-safe (par exemple, quand vous [déclenchez un événement](../../../standard/events/how-to-raise-and-consume-events.md)), comme illustré dans le code suivant :</span><span class="sxs-lookup"><span data-stu-id="d98a4-151">Use the `?.` operator to check if a delegate is non-null and invoke it in a thread-safe way (for example, when you [raise an event](../../../standard/events/how-to-raise-and-consume-events.md)), as the following code shows:</span></span>

```csharp
PropertyChanged?.Invoke(…)
```

<span data-ttu-id="d98a4-152">Ce code est équivalent au code suivant que vous utiliseriez dans C# 5 ou une version antérieure :</span><span class="sxs-lookup"><span data-stu-id="d98a4-152">That code is equivalent to the following code that you would use in C# 5 or earlier:</span></span>

```csharp
var handler = this.PropertyChanged;
if (handler != null)
{
    handler(…);
}
```

<span data-ttu-id="d98a4-153">C’est un moyen sûr de fil pour `handler` s’assurer que seul un non-null est invoqué.</span><span class="sxs-lookup"><span data-stu-id="d98a4-153">That is a thread-safe way to ensure that only a non-null `handler` is invoked.</span></span> <span data-ttu-id="d98a4-154">Étant donné que les instances des délégués sont immuables, aucun thread ne peut modifier la valeur référencée par la `handler` variable locale.</span><span class="sxs-lookup"><span data-stu-id="d98a4-154">Because delegate instances are immutable, no thread can change the value referenced by the `handler` local variable.</span></span> <span data-ttu-id="d98a4-155">En particulier, si le code exécuté par un autre `PropertyChanged` thread `PropertyChanged` `null` se `handler` désabonner de l’événement et devient avant est invoqué, la valeur référencée par `handler` reste inchangée.</span><span class="sxs-lookup"><span data-stu-id="d98a4-155">In particular, if the code executed by another thread unsubscribes from the `PropertyChanged` event and `PropertyChanged` becomes `null` before `handler` is invoked, the value referenced by `handler` remains unaffected.</span></span> <span data-ttu-id="d98a4-156">L’opérateur `?.` n’évalue son opératais gauche qu’une seule fois, garantissant qu’il ne peut pas être changé après `null` avoir été vérifié comme non nul.</span><span class="sxs-lookup"><span data-stu-id="d98a4-156">The `?.` operator evaluates its left-hand operand no more than once, guaranteeing that it cannot be changed to `null` after being verified as non-null.</span></span>

## <a name="invocation-expression-"></a><span data-ttu-id="d98a4-157">Expression d’invocation ()</span><span class="sxs-lookup"><span data-stu-id="d98a4-157">Invocation expression ()</span></span>

<span data-ttu-id="d98a4-158">Utilisez des parenthèses, `()`, pour appeler une [méthode](../../programming-guide/classes-and-structs/methods.md) ou un [délégué](../../programming-guide/delegates/index.md).</span><span class="sxs-lookup"><span data-stu-id="d98a4-158">Use parentheses, `()`, to call a [method](../../programming-guide/classes-and-structs/methods.md) or invoke a [delegate](../../programming-guide/delegates/index.md).</span></span>

<span data-ttu-id="d98a4-159">L’exemple suivant montre comment appeler une méthode, avec ou sans arguments, et un délégué :</span><span class="sxs-lookup"><span data-stu-id="d98a4-159">The following example demonstrates how to call a method, with or without arguments, and invoke a delegate:</span></span>

[!code-csharp-interactive[invocation with ()](snippets/MemberAccessOperators.cs#Invocation)]

<span data-ttu-id="d98a4-160">Vous utilisez également des parenthèses quand vous appelez un [constructeur](../../programming-guide/classes-and-structs/constructors.md) avec l’opérateur [`new`](new-operator.md).</span><span class="sxs-lookup"><span data-stu-id="d98a4-160">You also use parentheses when you invoke a [constructor](../../programming-guide/classes-and-structs/constructors.md) with the [`new`](new-operator.md) operator.</span></span>

### <a name="other-usages-of-"></a><span data-ttu-id="d98a4-161">Autres utilisations de ()</span><span class="sxs-lookup"><span data-stu-id="d98a4-161">Other usages of ()</span></span>

<span data-ttu-id="d98a4-162">Vous utilisez également des parenthèses pour ajuster l’ordre dans lequel évaluer les opérations dans une expression.</span><span class="sxs-lookup"><span data-stu-id="d98a4-162">You also use parentheses to adjust the order in which to evaluate operations in an expression.</span></span> <span data-ttu-id="d98a4-163">Pour plus d’informations, consultez [Opérateurs C#](index.md).</span><span class="sxs-lookup"><span data-stu-id="d98a4-163">For more information, see [C# operators](index.md).</span></span>

<span data-ttu-id="d98a4-164">[Les expressions cast](type-testing-and-cast.md#cast-expression), qui effectuent des conversions de type explicites, utilisent aussi des parenthèses.</span><span class="sxs-lookup"><span data-stu-id="d98a4-164">[Cast expressions](type-testing-and-cast.md#cast-expression), which perform explicit type conversions, also use parentheses.</span></span>

## <a name="index-from-end-operator-"></a><span data-ttu-id="d98a4-165">Indice de l’opérateur final</span><span class="sxs-lookup"><span data-stu-id="d98a4-165">Index from end operator ^</span></span>

<span data-ttu-id="d98a4-166">Disponible en C 8.0 et `^` plus tard, l’opérateur indique la position de l’élément à partir de la fin d’une séquence.</span><span class="sxs-lookup"><span data-stu-id="d98a4-166">Available in C# 8.0 and later, the `^` operator indicates the element position from the end of a sequence.</span></span> <span data-ttu-id="d98a4-167">Pour une séquence `length` `^n` de longueur, pointe `length - n` vers l’élément avec décalage dès le début d’une séquence.</span><span class="sxs-lookup"><span data-stu-id="d98a4-167">For a sequence of length `length`, `^n` points to the element with offset `length - n` from the start of a sequence.</span></span> <span data-ttu-id="d98a4-168">Par exemple, `^1` indique le dernier élément `^length` d’une séquence et pointe vers le premier élément d’une séquence.</span><span class="sxs-lookup"><span data-stu-id="d98a4-168">For example, `^1` points to the last element of a sequence and `^length` points to the first element of a sequence.</span></span>

[!code-csharp[index from end](snippets/MemberAccessOperators.cs#IndexFromEnd)]

<span data-ttu-id="d98a4-169">Comme le montre l’exemple <xref:System.Index?displayProperty=nameWithType> précédent, l’expression `^e` est du genre.</span><span class="sxs-lookup"><span data-stu-id="d98a4-169">As the preceding example shows, expression `^e` is of the <xref:System.Index?displayProperty=nameWithType> type.</span></span> <span data-ttu-id="d98a4-170">En `^e`expression , `e` le résultat de `int`doit être implicitement convertible à .</span><span class="sxs-lookup"><span data-stu-id="d98a4-170">In expression `^e`, the result of `e` must be implicitly convertible to `int`.</span></span>

<span data-ttu-id="d98a4-171">Vous pouvez également `^` utiliser l’opérateur avec l’opérateur [de la gamme](#range-operator-) pour créer une gamme d’indices.</span><span class="sxs-lookup"><span data-stu-id="d98a4-171">You can also use the `^` operator with the [range operator](#range-operator-) to create a range of indices.</span></span> <span data-ttu-id="d98a4-172">Pour plus d’informations, voir [Indices et gammes](../../tutorials/ranges-indexes.md).</span><span class="sxs-lookup"><span data-stu-id="d98a4-172">For more information, see [Indices and ranges](../../tutorials/ranges-indexes.md).</span></span>

## <a name="range-operator-"></a><span data-ttu-id="d98a4-173">Opérateur de gamme ..</span><span class="sxs-lookup"><span data-stu-id="d98a4-173">Range operator ..</span></span>

<span data-ttu-id="d98a4-174">Disponible en C 8.0 et `..` plus tard, l’opérateur spécifie le début et la fin d’une gamme d’indices comme ses opérands.</span><span class="sxs-lookup"><span data-stu-id="d98a4-174">Available in C# 8.0 and later, the `..` operator specifies the start and end of a range of indices as its operands.</span></span> <span data-ttu-id="d98a4-175">L’opéra de gauche est un début de gamme *inclusif.*</span><span class="sxs-lookup"><span data-stu-id="d98a4-175">The left-hand operand is an *inclusive* start of a range.</span></span> <span data-ttu-id="d98a4-176">L’opéra de droite est une fin *exclusive* d’une gamme.</span><span class="sxs-lookup"><span data-stu-id="d98a4-176">The right-hand operand is an *exclusive* end of a range.</span></span> <span data-ttu-id="d98a4-177">L’un ou l’autre des opérandes peut être un index dès le début ou à partir de la fin d’une séquence, comme le montre l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="d98a4-177">Either of operands can be an index from the start or from the end of a sequence, as the following example shows:</span></span>

[!code-csharp[range examples](snippets/MemberAccessOperators.cs#Ranges)]

<span data-ttu-id="d98a4-178">Comme le montre l’exemple <xref:System.Range?displayProperty=nameWithType> précédent, l’expression `a..b` est du genre.</span><span class="sxs-lookup"><span data-stu-id="d98a4-178">As the preceding example shows, expression `a..b` is of the <xref:System.Range?displayProperty=nameWithType> type.</span></span> <span data-ttu-id="d98a4-179">En `a..b`expression, les `a` `b` résultats et doivent `int` être <xref:System.Index>implicitement convertibles ou .</span><span class="sxs-lookup"><span data-stu-id="d98a4-179">In expression `a..b`, the results of `a` and `b` must be implicitly convertible to `int` or <xref:System.Index>.</span></span>

<span data-ttu-id="d98a4-180">Vous pouvez omettre l’un `..` des opérands de l’opérateur pour obtenir une gamme ouverte :</span><span class="sxs-lookup"><span data-stu-id="d98a4-180">You can omit any of the operands of the `..` operator to obtain an open-ended range:</span></span>

- <span data-ttu-id="d98a4-181">`a..` équivaut à `a..^0`</span><span class="sxs-lookup"><span data-stu-id="d98a4-181">`a..` is equivalent to `a..^0`</span></span>
- <span data-ttu-id="d98a4-182">`..b` équivaut à `0..b`</span><span class="sxs-lookup"><span data-stu-id="d98a4-182">`..b` is equivalent to `0..b`</span></span>
- <span data-ttu-id="d98a4-183">`..` équivaut à `0..^0`</span><span class="sxs-lookup"><span data-stu-id="d98a4-183">`..` is equivalent to `0..^0`</span></span>

[!code-csharp[ranges with omitted operands](snippets/MemberAccessOperators.cs#RangesOptional)]

<span data-ttu-id="d98a4-184">Pour plus d’informations, voir [Indices et gammes](../../tutorials/ranges-indexes.md).</span><span class="sxs-lookup"><span data-stu-id="d98a4-184">For more information, see [Indices and ranges](../../tutorials/ranges-indexes.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="d98a4-185">Capacité de surcharge de l’opérateur</span><span class="sxs-lookup"><span data-stu-id="d98a4-185">Operator overloadability</span></span>

<span data-ttu-id="d98a4-186">Le `.` `()`, `^`, `..` et les opérateurs ne peuvent pas être surchargés.</span><span class="sxs-lookup"><span data-stu-id="d98a4-186">The `.`, `()`, `^`, and `..` operators cannot be overloaded.</span></span> <span data-ttu-id="d98a4-187">L’opérateur `[]` est également considéré comme un opérateur non surchargeable.</span><span class="sxs-lookup"><span data-stu-id="d98a4-187">The `[]` operator is also considered a non-overloadable operator.</span></span> <span data-ttu-id="d98a4-188">Utilisez des [indexeurs](../../programming-guide/indexers/index.md) pour prendre en charge l’indexation avec des types définis par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="d98a4-188">Use [indexers](../../programming-guide/indexers/index.md) to support indexing with user-defined types.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="d98a4-189">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="d98a4-189">C# language specification</span></span>

<span data-ttu-id="d98a4-190">Pour plus d’informations, consultez les sections suivantes de la [spécification du langage C#](~/_csharplang/spec/introduction.md) :</span><span class="sxs-lookup"><span data-stu-id="d98a4-190">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="d98a4-191">Accès aux membres</span><span class="sxs-lookup"><span data-stu-id="d98a4-191">Member access</span></span>](~/_csharplang/spec/expressions.md#member-access)
- [<span data-ttu-id="d98a4-192">Accès aux éléments</span><span class="sxs-lookup"><span data-stu-id="d98a4-192">Element access</span></span>](~/_csharplang/spec/expressions.md#element-access)
- [<span data-ttu-id="d98a4-193">Opérateur conditionnel Null</span><span class="sxs-lookup"><span data-stu-id="d98a4-193">Null-conditional operator</span></span>](~/_csharplang/spec/expressions.md#null-conditional-operator)
- [<span data-ttu-id="d98a4-194">Expressions d’appels</span><span class="sxs-lookup"><span data-stu-id="d98a4-194">Invocation expressions</span></span>](~/_csharplang/spec/expressions.md#invocation-expressions)

<span data-ttu-id="d98a4-195">Pour plus d’informations sur les indices et les plages, voir la [note de proposition de fonctionnalité](~/_csharplang/proposals/csharp-8.0/ranges.md).</span><span class="sxs-lookup"><span data-stu-id="d98a4-195">For more information about indices and ranges, see the [feature proposal note](~/_csharplang/proposals/csharp-8.0/ranges.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d98a4-196">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d98a4-196">See also</span></span>

- [<span data-ttu-id="d98a4-197">Référence C#</span><span class="sxs-lookup"><span data-stu-id="d98a4-197">C# reference</span></span>](../index.md)
- [<span data-ttu-id="d98a4-198">Opérateurs CMD</span><span class="sxs-lookup"><span data-stu-id="d98a4-198">C# operators</span></span>](index.md)
- [<span data-ttu-id="d98a4-199">?? (opérateur de fusion Null)</span><span class="sxs-lookup"><span data-stu-id="d98a4-199">?? (null-coalescing operator)</span></span>](null-coalescing-operator.md)
- [<span data-ttu-id="d98a4-200">:: (opérateur)</span><span class="sxs-lookup"><span data-stu-id="d98a4-200">:: operator</span></span>](namespace-alias-qualifier.md)
