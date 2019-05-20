---
title: Opérateurs d’accès aux membres - Référence C#
description: Découvrez les opérateurs C# que vous pouvez utiliser pour accéder aux membres de type.
ms.date: 05/09/2019
author: pkulikov
f1_keywords:
- ._CSharpKeyword
- '[]_CSharpKeyword'
- ()_CSharpKeyword
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
- ?. operator [C#]
- ?[] operator [C#]
- invocation operator [C#]
- method call [C#]
- method invocation [C#]
- delegate invocation [C#]
- () operator [C#]
ms.openlocfilehash: 921d69e3deb7e5bb5115eb723727462839af9b6b
ms.sourcegitcommit: 4c10802ad003374641a2c2373b8a92e3c88babc8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2019
ms.locfileid: "65452891"
---
# <a name="member-access-operators"></a><span data-ttu-id="7828f-103">Opérateurs d’accès au membre</span><span class="sxs-lookup"><span data-stu-id="7828f-103">Member access operators</span></span>

<span data-ttu-id="7828f-104">Vous pouvez utiliser les opérateurs suivants quand vous accédez à un membre de type :</span><span class="sxs-lookup"><span data-stu-id="7828f-104">You might use the following operators when you access a type member:</span></span>

- <span data-ttu-id="7828f-105">[`.` (accès aux membres)](#member-access-operator-) : accédez à un membre d’un espace de noms ou d’un type</span><span class="sxs-lookup"><span data-stu-id="7828f-105">[`.` (member access)](#member-access-operator-): to access a member of a namespace or a type</span></span>
- <span data-ttu-id="7828f-106">[`[]` (accès à un indexeur ou à un élément de tableau)](#indexer-operator-) : pour accéder à un élément de tableau ou à un indexeur de type</span><span class="sxs-lookup"><span data-stu-id="7828f-106">[`[]` (array element or indexer access)](#indexer-operator-): to access an array element or a type indexer</span></span>
- <span data-ttu-id="7828f-107">[`?.` et `?[]` (opérateurs conditionnels Null)](#null-conditional-operators--and-) : pour effectuer une opération d’accès à un membre ou élément uniquement si un opérande est non Null</span><span class="sxs-lookup"><span data-stu-id="7828f-107">[`?.` and `?[]` (null-conditional operators)](#null-conditional-operators--and-): to perform a member or element access operation only if an operand is non-null</span></span>
- <span data-ttu-id="7828f-108">[`()` (appel) ](#invocation-operator-) : pour appeler une méthode sollicitée ou appeler un délégué</span><span class="sxs-lookup"><span data-stu-id="7828f-108">[`()` (invocation)](#invocation-operator-): to call an accessed method or invoke a delegate</span></span>

## <a name="member-access-operator-"></a><span data-ttu-id="7828f-109">Opérateur d’accès aux membres .</span><span class="sxs-lookup"><span data-stu-id="7828f-109">Member access operator .</span></span>

<span data-ttu-id="7828f-110">Le jeton `.` sert à accéder à l’un des membres d’un espace de noms ou d’un type, comme le montrent les exemples suivants :</span><span class="sxs-lookup"><span data-stu-id="7828f-110">You use the `.` token to access a member of a namespace or a type, as the following examples demonstrate:</span></span>

- <span data-ttu-id="7828f-111">Utilisez `.` pour accéder à un espace de noms imbriqué dans un autre, comme le montre l’exemple suivant avec la [directive `using`](../keywords/using-directive.md) :</span><span class="sxs-lookup"><span data-stu-id="7828f-111">Use `.` to access a nested namespace within a namespace, as the following example of a [`using` directive](../keywords/using-directive.md) shows:</span></span>

  [!code-csharp[nested namespaces](~/samples/snippets/csharp/language-reference/operators/MemberAccessOperators.cs#NestedNamespace)]

- <span data-ttu-id="7828f-112">Utilisez `.` pour former un *nom qualifié* permettant d’accéder à un type dans un espace de noms, comme le montre le code suivant :</span><span class="sxs-lookup"><span data-stu-id="7828f-112">Use `.` to form a *qualified name* to access a type within a namespace, as the following code shows:</span></span>

  [!code-csharp[qualified name](~/samples/snippets/csharp/language-reference/operators/MemberAccessOperators.cs#QualifiedName)]

  <span data-ttu-id="7828f-113">Utilisez une [directive `using`](../keywords/using-directive.md) pour rendre facultative l’utilisation de noms qualifiés.</span><span class="sxs-lookup"><span data-stu-id="7828f-113">Use a [`using` directive](../keywords/using-directive.md) to make the use of qualified names optional.</span></span>

- <span data-ttu-id="7828f-114">Utilisez `.` pour accéder aux [membres de type](../../programming-guide/classes-and-structs/index.md#members), statiques et non statiques, comme le montre le code suivant :</span><span class="sxs-lookup"><span data-stu-id="7828f-114">Use `.` to access [type members](../../programming-guide/classes-and-structs/index.md#members), static and non-static, as the following code shows:</span></span>

  [!code-csharp-interactive[type members](~/samples/snippets/csharp/language-reference/operators/MemberAccessOperators.cs#TypeMemberAccess)]

<span data-ttu-id="7828f-115">Vous pouvez également utiliser `.` pour accéder à une [méthode d’extension](../../programming-guide/classes-and-structs/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="7828f-115">You can also use `.` to access an [extension method](../../programming-guide/classes-and-structs/extension-methods.md).</span></span>

## <a name="indexer-operator-"></a><span data-ttu-id="7828f-116">Opérateur d’indexeur []</span><span class="sxs-lookup"><span data-stu-id="7828f-116">Indexer operator []</span></span>

<span data-ttu-id="7828f-117">Les crochets, `[]`, sont généralement utilisés pour l’accès à un élément tableau, indexeur ou pointeur.</span><span class="sxs-lookup"><span data-stu-id="7828f-117">Square brackets, `[]`, are typically used for array, indexer, or pointer element access.</span></span>

### <a name="array-access"></a><span data-ttu-id="7828f-118">Accès aux tableaux</span><span class="sxs-lookup"><span data-stu-id="7828f-118">Array access</span></span>

<span data-ttu-id="7828f-119">L’exemple suivant montre comment accéder à des éléments tableau :</span><span class="sxs-lookup"><span data-stu-id="7828f-119">The following example demonstrates how to access array elements:</span></span>

[!code-csharp-interactive[array access](~/samples/snippets/csharp/language-reference/operators/MemberAccessOperators.cs#Arrays)]

<span data-ttu-id="7828f-120">Si un index de tableau est en dehors des limites de la dimension correspondante d’un tableau, une <xref:System.IndexOutOfRangeException> est levée.</span><span class="sxs-lookup"><span data-stu-id="7828f-120">If an array index is outside the bounds of the corresponding dimension of an array, an <xref:System.IndexOutOfRangeException> is thrown.</span></span>

<span data-ttu-id="7828f-121">Comme le montre l’exemple précédent, vous utilisez également des crochets quand vous déclarez un type tableau ou instanciez une instance de tableau.</span><span class="sxs-lookup"><span data-stu-id="7828f-121">As the preceding example shows, you also use square brackets when you declare an array type or instantiate an array instance.</span></span>

<span data-ttu-id="7828f-122">Pour plus d’informations sur les tableaux, consultez [Tableaux](../../programming-guide/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="7828f-122">For more information about arrays, see [Arrays](../../programming-guide/arrays/index.md).</span></span>

### <a name="indexer-access"></a><span data-ttu-id="7828f-123">Accès aux indexeurs</span><span class="sxs-lookup"><span data-stu-id="7828f-123">Indexer access</span></span>

<span data-ttu-id="7828f-124">L’exemple suivant utilise le type .NET <xref:System.Collections.Generic.Dictionary%602> afin d’illustrer l’accès aux indexeurs :</span><span class="sxs-lookup"><span data-stu-id="7828f-124">The following example uses .NET <xref:System.Collections.Generic.Dictionary%602> type to demonstrate indexer access:</span></span>

[!code-csharp-interactive[indexer access](~/samples/snippets/csharp/language-reference/operators/MemberAccessOperators.cs#Indexers)]

<span data-ttu-id="7828f-125">Les indexeurs vous permettent d’indexer des instances d’un type défini par l’utilisateur en procédant de la même façon que pour l’indexation de tableau.</span><span class="sxs-lookup"><span data-stu-id="7828f-125">Indexers allow you to index instances of a user-defined type in the similar way as array indexing.</span></span> <span data-ttu-id="7828f-126">Contrairement aux index de tableau, qui doivent être des entiers, les arguments d’indexeur peuvent être déclarés comme étant de n’importe quel type.</span><span class="sxs-lookup"><span data-stu-id="7828f-126">Unlike array indices, which must be integer, the indexer arguments can be declared to be of any type.</span></span>

<span data-ttu-id="7828f-127">Pour plus d’informations sur les indexeurs, consultez [Indexeurs](../../programming-guide/indexers/index.md).</span><span class="sxs-lookup"><span data-stu-id="7828f-127">For more information about indexers, see [Indexers](../../programming-guide/indexers/index.md).</span></span>

### <a name="other-usages-of-"></a><span data-ttu-id="7828f-128">Autres utilisations de []</span><span class="sxs-lookup"><span data-stu-id="7828f-128">Other usages of []</span></span>

<span data-ttu-id="7828f-129">Pour plus d’informations sur l’accès aux éléments pointeur, consultez [Guide pratique pour accéder à un élément de tableau à l’aide d’un pointeur](../../programming-guide/unsafe-code-pointers/how-to-access-an-array-element-with-a-pointer.md).</span><span class="sxs-lookup"><span data-stu-id="7828f-129">For information about pointer element access, see [How to: access an array element with a pointer](../../programming-guide/unsafe-code-pointers/how-to-access-an-array-element-with-a-pointer.md).</span></span>

<span data-ttu-id="7828f-130">Vous utilisez également des crochets pour spécifier des [attributs](../../programming-guide/concepts/attributes/index.md) :</span><span class="sxs-lookup"><span data-stu-id="7828f-130">You also use square brackets to specify [attributes](../../programming-guide/concepts/attributes/index.md):</span></span>

```csharp
[System.Diagnostics.Conditional("DEBUG")]
void TraceMethod() {}
```

## <a name="null-conditional-operators--and-"></a><span data-ttu-id="7828f-131">Opérateurs conditionnels Null ?.</span><span class="sxs-lookup"><span data-stu-id="7828f-131">Null-conditional operators ?.</span></span> <span data-ttu-id="7828f-132">et ?[]</span><span class="sxs-lookup"><span data-stu-id="7828f-132">and ?[]</span></span>

<span data-ttu-id="7828f-133">Disponible dans C# 6 et versions ultérieures, un opérateur conditionnel Null applique une opération d’accès aux membres, `?.`, ou d’accès aux éléments, `?[]`, à son opérande uniquement si ce dernier a une valeur non Null.</span><span class="sxs-lookup"><span data-stu-id="7828f-133">Available in C# 6 and later, a null-conditional operator applies a member access, `?.`, or element access, `?[]`, operation to its operand only if that operand evaluates to non-null.</span></span> <span data-ttu-id="7828f-134">Si l’opérande a la valeur `null`, le résultat de l’application de l’opérateur est `null`.</span><span class="sxs-lookup"><span data-stu-id="7828f-134">If the operand evaluates to `null`, the result of applying the operator is `null`.</span></span>

<span data-ttu-id="7828f-135">Les opérateurs conditionnels Null ont un effet de court-circuit.</span><span class="sxs-lookup"><span data-stu-id="7828f-135">The null-conditional operators are short-circuiting.</span></span> <span data-ttu-id="7828f-136">Autrement dit, si une opération dans une chaîne d’opérations d’accès au membre ou à l’élément conditionnelles retourne une valeur `null`, le reste de la chaîne ne s’exécute pas.</span><span class="sxs-lookup"><span data-stu-id="7828f-136">That is, if one operation in a chain of conditional member or element access operations returns `null`, the rest of the chain doesn't execute.</span></span> <span data-ttu-id="7828f-137">Dans l’exemple suivant, `B` n’est pas évalué si `A` prend la valeur `null` et `C` n’est pas évalué si `A` ou `B` prend la valeur `null` :</span><span class="sxs-lookup"><span data-stu-id="7828f-137">In the following example, `B` is not evaluated if `A` evaluates to `null` and `C` is not evaluated if `A` or `B` evaluates to `null`:</span></span>

```csharp
A?.B?.Do(C);
A?.B?[C];
```

<span data-ttu-id="7828f-138">L’exemple suivant illustre l’utilisation des opérateurs `?.` et `?[]` :</span><span class="sxs-lookup"><span data-stu-id="7828f-138">The following example demonstrates the usage of the `?.` and `?[]` operators:</span></span>

[!code-csharp-interactive[null-conditional operators](~/samples/snippets/csharp/language-reference/operators/MemberAccessOperators.cs#NullConditional)]

<span data-ttu-id="7828f-139">L’exemple précédent illustre également l’utilisation de l’[opérateur de fusion Null](null-coalescing-operator.md).</span><span class="sxs-lookup"><span data-stu-id="7828f-139">The preceding example also shows the usage of the [null-coalescing operator](null-coalescing-operator.md).</span></span> <span data-ttu-id="7828f-140">Vous pouvez utiliser l’opérateur de fusion Null pour fournir une autre expression à évaluer au cas où le résultat de l’opération conditionnelle Null serait `null`.</span><span class="sxs-lookup"><span data-stu-id="7828f-140">You might use the null-coalescing operator to provide an alternative expression to evaluate in case the result of the null-conditional operation is `null`.</span></span>

### <a name="thread-safe-delegate-invocation"></a><span data-ttu-id="7828f-141">Appel de délégué thread-safe</span><span class="sxs-lookup"><span data-stu-id="7828f-141">Thread-safe delegate invocation</span></span>

<span data-ttu-id="7828f-142">Utilisez l’opérateur `?.` pour vérifier si un délégué est non Null et l’appeler de manière thread-safe (par exemple, quand vous [déclenchez un événement](../../../standard/events/how-to-raise-and-consume-events.md)), comme illustré dans le code suivant :</span><span class="sxs-lookup"><span data-stu-id="7828f-142">Use the `?.` operator to check if a delegate is non-null and invoke it in a thread-safe way (for example, when you [raise an event](../../../standard/events/how-to-raise-and-consume-events.md)), as the following code shows:</span></span>

```csharp
PropertyChanged?.Invoke(…)
```

<span data-ttu-id="7828f-143">Ce code est équivalent au code suivant que vous utiliseriez dans C# 5 ou une version antérieure :</span><span class="sxs-lookup"><span data-stu-id="7828f-143">That code is equivalent to the following code that you would use in C# 5 or earlier:</span></span>

```csharp
var handler = this.PropertyChanged;
if (handler != null)
{
    handler(…);
}
```

## <a name="invocation-operator-"></a><span data-ttu-id="7828f-144">Opérateur d’appel ()</span><span class="sxs-lookup"><span data-stu-id="7828f-144">Invocation operator ()</span></span>

<span data-ttu-id="7828f-145">Utilisez des parenthèses, `()`, pour appeler une [méthode](../../programming-guide/classes-and-structs/methods.md) ou un [délégué](../../programming-guide/delegates/index.md).</span><span class="sxs-lookup"><span data-stu-id="7828f-145">Use parentheses, `()`, to call a [method](../../programming-guide/classes-and-structs/methods.md) or invoke a [delegate](../../programming-guide/delegates/index.md).</span></span>

<span data-ttu-id="7828f-146">L’exemple suivant montre comment appeler une méthode, avec ou sans arguments, et un délégué :</span><span class="sxs-lookup"><span data-stu-id="7828f-146">The following example demonstrates how to call a method, with or without arguments, and invoke a delegate:</span></span>

[!code-csharp-interactive[invocation with ()](~/samples/snippets/csharp/language-reference/operators/MemberAccessOperators.cs#Invocation)]

<span data-ttu-id="7828f-147">Vous utilisez également des parenthèses quand vous appelez un [constructeur](../../programming-guide/classes-and-structs/constructors.md) avec un opérateur [`new`](../keywords/new-operator.md).</span><span class="sxs-lookup"><span data-stu-id="7828f-147">You also use parentheses when you invoke a [constructor](../../programming-guide/classes-and-structs/constructors.md) with a [`new`](../keywords/new-operator.md) operator.</span></span>

### <a name="other-usages-of-"></a><span data-ttu-id="7828f-148">Autres utilisations de ()</span><span class="sxs-lookup"><span data-stu-id="7828f-148">Other usages of ()</span></span>

<span data-ttu-id="7828f-149">Vous utilisez également des parenthèses pour spécifier l’ordre dans lequel évaluer les opérations dans une expression.</span><span class="sxs-lookup"><span data-stu-id="7828f-149">You also use parentheses to specify the order in which to evaluate operations in an expression.</span></span> <span data-ttu-id="7828f-150">Pour plus d’informations, consultez la section [Ajout de parenthèses](../../programming-guide/statements-expressions-operators/operators.md#adding-parentheses) de l’article [Opérateurs](../../programming-guide/statements-expressions-operators/operators.md).</span><span class="sxs-lookup"><span data-stu-id="7828f-150">For more information, see the [Adding parentheses](../../programming-guide/statements-expressions-operators/operators.md#adding-parentheses) section of the [Operators](../../programming-guide/statements-expressions-operators/operators.md) article.</span></span> <span data-ttu-id="7828f-151">Pour obtenir la liste des opérateurs classés par niveau de priorité, consultez [Opérateurs C#](index.md).</span><span class="sxs-lookup"><span data-stu-id="7828f-151">For the list of operators ordered by precedence level, see [C# operators](index.md).</span></span>

<span data-ttu-id="7828f-152">Les [expressions cast](invocation-operator.md#cast-expression), qui appellent un opérateur de conversion, utilisent également des parenthèses.</span><span class="sxs-lookup"><span data-stu-id="7828f-152">[Cast expressions](invocation-operator.md#cast-expression), which invoke a conversion operator, also use parentheses.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="7828f-153">Capacité de surcharge de l’opérateur</span><span class="sxs-lookup"><span data-stu-id="7828f-153">Operator overloadability</span></span>

<span data-ttu-id="7828f-154">Les opérateurs `.` et `()` ne peuvent pas être surchargés.</span><span class="sxs-lookup"><span data-stu-id="7828f-154">The `.` and `()` operators cannot be overloaded.</span></span> <span data-ttu-id="7828f-155">L’opérateur `[]` est également considéré comme un opérateur non surchargeable.</span><span class="sxs-lookup"><span data-stu-id="7828f-155">The `[]` operator is also considered a non-overloadable operator.</span></span> <span data-ttu-id="7828f-156">Utilisez des [indexeurs](../../programming-guide/indexers/index.md) pour prendre en charge l’indexation avec des types définis par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="7828f-156">Use [indexers](../../programming-guide/indexers/index.md) to support indexing with user-defined types.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="7828f-157">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="7828f-157">C# language specification</span></span>

<span data-ttu-id="7828f-158">Pour plus d’informations, consultez les sections suivantes de la [spécification du langage C#](~/_csharplang/spec/introduction.md) :</span><span class="sxs-lookup"><span data-stu-id="7828f-158">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="7828f-159">Accès aux membres</span><span class="sxs-lookup"><span data-stu-id="7828f-159">Member access</span></span>](~/_csharplang/spec/expressions.md#member-access)
- [<span data-ttu-id="7828f-160">Accès aux éléments</span><span class="sxs-lookup"><span data-stu-id="7828f-160">Element access</span></span>](~/_csharplang/spec/expressions.md#element-access)
- [<span data-ttu-id="7828f-161">Opérateur conditionnel Null</span><span class="sxs-lookup"><span data-stu-id="7828f-161">Null-conditional operator</span></span>](~/_csharplang/spec/expressions.md#null-conditional-operator)
- [<span data-ttu-id="7828f-162">Expressions d’appels</span><span class="sxs-lookup"><span data-stu-id="7828f-162">Invocation expressions</span></span>](~/_csharplang/spec/expressions.md#invocation-expressions)

## <a name="see-also"></a><span data-ttu-id="7828f-163">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7828f-163">See also</span></span>

- [<span data-ttu-id="7828f-164">Référence C#</span><span class="sxs-lookup"><span data-stu-id="7828f-164">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="7828f-165">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="7828f-165">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="7828f-166">Opérateurs C#</span><span class="sxs-lookup"><span data-stu-id="7828f-166">C# Operators</span></span>](index.md)
- [<span data-ttu-id="7828f-167">?? (opérateur de fusion Null)</span><span class="sxs-lookup"><span data-stu-id="7828f-167">?? (null-coalescing operator)</span></span>](null-coalescing-operator.md)
