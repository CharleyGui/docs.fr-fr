---
title: Opérateurs associés au pointeur - Référence C#
description: Découvrez les opérateurs C# que vous pouvez utiliser avec les pointeurs.
ms.date: 05/20/2019
author: pkulikov
f1_keywords:
- ->_CSharpKeyword
helpviewer_keywords:
- pointer related operators [C#]
- address-of operator [C#]
- '& operator [C#]'
- pointer indirection operator [C#]
- dereference operator [C#]
- '* operator [C#]'
- pointer member access operator [C#]
- -> operator [C#]
- pointer element access [C#]
- '[] operator [C#]'
- pointer arithmetic [C#]
- pointer increment [C#]
- pointer decrement [C#]
- pointer comparison [C#]
ms.openlocfilehash: 51e6aeda7699d9e2fe3c46ced93e1783a52e6743
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/03/2020
ms.locfileid: "78238960"
---
# <a name="pointer-related-operators-c-reference"></a><span data-ttu-id="44ec2-103">Opérateurs associés au pointeur (référence C#)</span><span class="sxs-lookup"><span data-stu-id="44ec2-103">Pointer related operators (C# reference)</span></span>

<span data-ttu-id="44ec2-104">Vous pouvez utiliser les opérateurs suivants avec les pointeurs :</span><span class="sxs-lookup"><span data-stu-id="44ec2-104">You can use the following operators to work with pointers:</span></span>

- <span data-ttu-id="44ec2-105">Opérateur unaire [`&` (address-of)](#address-of-operator-) : pour obtenir l’adresse d’une variable</span><span class="sxs-lookup"><span data-stu-id="44ec2-105">Unary [`&` (address-of)](#address-of-operator-) operator: to get the address of a variable</span></span>
- <span data-ttu-id="44ec2-106">Opérateur unaire [`*` (indirection du pointeur)](#pointer-indirection-operator-) : pour obtenir la variable pointée par un pointeur</span><span class="sxs-lookup"><span data-stu-id="44ec2-106">Unary [`*` (pointer indirection)](#pointer-indirection-operator-) operator: to obtain the variable pointed by a pointer</span></span>
- <span data-ttu-id="44ec2-107">Opérateurs [`->` (accès aux membres)](#pointer-member-access-operator--) et [`[]` (accès aux éléments)](#pointer-element-access-operator-)</span><span class="sxs-lookup"><span data-stu-id="44ec2-107">The [`->` (member access)](#pointer-member-access-operator--) and [`[]` (element access)](#pointer-element-access-operator-) operators</span></span>
- <span data-ttu-id="44ec2-108">Opérateurs arithmétiques [`+`, `-`, `++` et `--`](#pointer-arithmetic-operators)</span><span class="sxs-lookup"><span data-stu-id="44ec2-108">Arithmetic operators [`+`, `-`, `++`, and `--`](#pointer-arithmetic-operators)</span></span>
- <span data-ttu-id="44ec2-109">Opérateurs de comparaison [`==`, `!=`, `<`, `>`, `<=` et `>=`](#pointer-comparison-operators)</span><span class="sxs-lookup"><span data-stu-id="44ec2-109">Comparison operators [`==`, `!=`, `<`, `>`, `<=`, and `>=`](#pointer-comparison-operators)</span></span>

<span data-ttu-id="44ec2-110">Pour plus d’informations sur les types de pointeurs, consultez [Types pointeur](../../programming-guide/unsafe-code-pointers/pointer-types.md).</span><span class="sxs-lookup"><span data-stu-id="44ec2-110">For information about pointer types, see [Pointer types](../../programming-guide/unsafe-code-pointers/pointer-types.md).</span></span>

> [!NOTE]
> <span data-ttu-id="44ec2-111">Toutes les opérations impliquant des pointeurs nécessitent un contexte [unsafe](../keywords/unsafe.md).</span><span class="sxs-lookup"><span data-stu-id="44ec2-111">Any operation with pointers requires an [unsafe](../keywords/unsafe.md) context.</span></span> <span data-ttu-id="44ec2-112">Le code qui contient des blocs unsafe doit être compilé avec l’option de compilateur [`-unsafe`](../compiler-options/unsafe-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="44ec2-112">The code that contains unsafe blocks must be compiled with the [`-unsafe`](../compiler-options/unsafe-compiler-option.md) compiler option.</span></span>

## <a name="address-of-operator-"></a> <span data-ttu-id="44ec2-113">Opérateur address-of &amp;</span><span class="sxs-lookup"><span data-stu-id="44ec2-113">Address-of operator &amp;</span></span>

<span data-ttu-id="44ec2-114">L’opérateur unaire `&` retourne l’adresse de son opérande :</span><span class="sxs-lookup"><span data-stu-id="44ec2-114">The unary `&` operator returns the address of its operand:</span></span>

[!code-csharp[address of local](~/samples/snippets/csharp/language-reference/operators/PointerOperators.cs#AddressOf)]

<span data-ttu-id="44ec2-115">L’opérande de l’opérateur `&` doit être une variable fixe.</span><span class="sxs-lookup"><span data-stu-id="44ec2-115">The operand of the `&` operator must be a fixed variable.</span></span> <span data-ttu-id="44ec2-116">Les variables *fixes* se trouvent dans des emplacements de stockage qui ne sont pas affectés par le [récupérateur de mémoire](../../../standard/garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="44ec2-116">*Fixed* variables are variables that reside in storage locations that are unaffected by operation of the [garbage collector](../../../standard/garbage-collection/index.md).</span></span> <span data-ttu-id="44ec2-117">Dans l’exemple précédent, la variable locale `number` est une variable fixe, car elle se trouve dans la pile.</span><span class="sxs-lookup"><span data-stu-id="44ec2-117">In the preceding example, the local variable `number` is a fixed variable, because it resides on the stack.</span></span> <span data-ttu-id="44ec2-118">Les variables qui se trouvent dans des emplacements de stockage pouvant être affectés par le récupérateur de mémoire (par exemple, en étant déplacés) sont appelées variables *déplaçables*.</span><span class="sxs-lookup"><span data-stu-id="44ec2-118">Variables that reside in storage locations that can be affected by the garbage collector (for example, relocated) are called *movable* variables.</span></span> <span data-ttu-id="44ec2-119">Les champs d’objet et les éléments de tableau sont des exemples de variables déplaçables.</span><span class="sxs-lookup"><span data-stu-id="44ec2-119">Object fields and array elements are examples of movable variables.</span></span> <span data-ttu-id="44ec2-120">Vous pouvez obtenir l’adresse d’une variable déplaçable si vous « corrigez », ou « épinglez », avec une [instruction`fixed`](../keywords/fixed-statement.md).</span><span class="sxs-lookup"><span data-stu-id="44ec2-120">You can get the address of a movable variable if you "fix", or "pin", it with a [`fixed` statement](../keywords/fixed-statement.md).</span></span> <span data-ttu-id="44ec2-121">L’adresse obtenue est valide uniquement à l’intérieur du bloc d’une instruction `fixed`.</span><span class="sxs-lookup"><span data-stu-id="44ec2-121">The obtained address is valid only inside the block of a `fixed` statement.</span></span> <span data-ttu-id="44ec2-122">L’exemple suivant montre comment utiliser une instruction `fixed` et l’opérateur `&` :</span><span class="sxs-lookup"><span data-stu-id="44ec2-122">The following example shows how to use a `fixed` statement and the `&` operator:</span></span>

[!code-csharp[address of fixed](~/samples/snippets/csharp/language-reference/operators/PointerOperators.cs#AddressOfFixed)]

<span data-ttu-id="44ec2-123">Vous ne pouvez pas obtenir l’adresse d’une constante ou d’une valeur.</span><span class="sxs-lookup"><span data-stu-id="44ec2-123">You can't get the address of a constant or a value.</span></span>

<span data-ttu-id="44ec2-124">Pour plus d’informations sur les variables fixes et déplaçables, consultez la section [Variables fixes et déplaçables](~/_csharplang/spec/unsafe-code.md#fixed-and-moveable-variables) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="44ec2-124">For more information about fixed and movable variables, see the [Fixed and moveable variables](~/_csharplang/spec/unsafe-code.md#fixed-and-moveable-variables) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="44ec2-125">L’opérateur binaire `&` calcule la [logique AND](boolean-logical-operators.md#logical-and-operator-) de ses opérandes booléens, ou la [logique AND au niveau du bit](bitwise-and-shift-operators.md#logical-and-operator-) de ses opérandes de type intégral.</span><span class="sxs-lookup"><span data-stu-id="44ec2-125">The binary `&` operator computes the [logical AND](boolean-logical-operators.md#logical-and-operator-) of its Boolean operands or the [bitwise logical AND](bitwise-and-shift-operators.md#logical-and-operator-) of its integral operands.</span></span>

## <a name="pointer-indirection-operator-"></a><span data-ttu-id="44ec2-126">Opérateur d’indirection de pointeur \*</span><span class="sxs-lookup"><span data-stu-id="44ec2-126">Pointer indirection operator \*</span></span>

<span data-ttu-id="44ec2-127">L’opérateur unaire d’indirection de pointeur `*` permet d’obtenir la variable vers laquelle pointe son opérande.</span><span class="sxs-lookup"><span data-stu-id="44ec2-127">The unary pointer indirection operator `*` obtains the variable to which its operand points.</span></span> <span data-ttu-id="44ec2-128">Il est également appelé « opérateur de déréférence ».</span><span class="sxs-lookup"><span data-stu-id="44ec2-128">It's also known as the dereference operator.</span></span> <span data-ttu-id="44ec2-129">L’opérande de l’opérateur `*` doit être un type de pointeur.</span><span class="sxs-lookup"><span data-stu-id="44ec2-129">The operand of the `*` operator must be of a pointer type.</span></span>

[!code-csharp[pointer indirection](~/samples/snippets/csharp/language-reference/operators/PointerOperators.cs#PointerIndirection)]

<span data-ttu-id="44ec2-130">Vous ne pouvez pas appliquer l’opérateur `*` à une expression de type `void*`.</span><span class="sxs-lookup"><span data-stu-id="44ec2-130">You cannot apply the `*` operator to an expression of type `void*`.</span></span>

<span data-ttu-id="44ec2-131">L’opérateur binaire `*` calcule le [produit](arithmetic-operators.md#multiplication-operator-) de ses opérandes numériques.</span><span class="sxs-lookup"><span data-stu-id="44ec2-131">The binary `*` operator computes the [product](arithmetic-operators.md#multiplication-operator-) of its numeric operands.</span></span>

## <a name="pointer-member-access-operator--"></a><span data-ttu-id="44ec2-132">Opérateur d’accès aux membres de pointeur -></span><span class="sxs-lookup"><span data-stu-id="44ec2-132">Pointer member access operator -></span></span>

<span data-ttu-id="44ec2-133">L’opérateur `->` associe l’[indirection de pointeur](#pointer-indirection-operator-) à l’[accès aux membres](member-access-operators.md#member-access-operator-).</span><span class="sxs-lookup"><span data-stu-id="44ec2-133">The `->` operator combines [pointer indirection](#pointer-indirection-operator-) and [member access](member-access-operators.md#member-access-operator-).</span></span> <span data-ttu-id="44ec2-134">Autrement dit, si `x` est un pointeur de type `T*` et `y` est un membre accessible de type `T`, une expression de la forme</span><span class="sxs-lookup"><span data-stu-id="44ec2-134">That is, if `x` is a pointer of type `T*` and `y` is an accessible member of type `T`, an expression of the form</span></span>

```csharp
x->y
```

<span data-ttu-id="44ec2-135">équivaut à :</span><span class="sxs-lookup"><span data-stu-id="44ec2-135">is equivalent to</span></span>

```csharp
(*x).y
```

<span data-ttu-id="44ec2-136">L’exemple suivant illustre l’utilisation de l’opérateur `->` :</span><span class="sxs-lookup"><span data-stu-id="44ec2-136">The following example demonstrates the usage of the `->` operator:</span></span>

[!code-csharp[pointer member access](~/samples/snippets/csharp/language-reference/operators/PointerOperators.cs#MemberAccess)]

<span data-ttu-id="44ec2-137">Vous ne pouvez pas appliquer l’opérateur `->` à une expression de type `void*`.</span><span class="sxs-lookup"><span data-stu-id="44ec2-137">You cannot apply the `->` operator to an expression of type `void*`.</span></span>

## <a name="pointer-element-access-operator-"></a><span data-ttu-id="44ec2-138">Opérateur d’accès aux éléments de pointeur []</span><span class="sxs-lookup"><span data-stu-id="44ec2-138">Pointer element access operator []</span></span>

<span data-ttu-id="44ec2-139">Pour une expression `p` d’un type pointeur, l’accès à un élément de pointeur au format `p[n]` est évalué comme `*(p + n)`, où `n` doit être d’un type implicitement convertible en `int`, `uint`, `long` ou `ulong`.</span><span class="sxs-lookup"><span data-stu-id="44ec2-139">For an expression `p` of a pointer type, a pointer element access of the form `p[n]` is evaluated as `*(p + n)`, where `n` must be of a type implicitly convertible to `int`, `uint`, `long`, or `ulong`.</span></span> <span data-ttu-id="44ec2-140">Pour plus d’informations sur le comportement de l’opérateur `+` avec les pointeurs, consultez la section [Addition ou soustraction d’une valeur intégrale dans un pointeur](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer).</span><span class="sxs-lookup"><span data-stu-id="44ec2-140">For information about the behavior of the `+` operator with pointers, see the [Addition or subtraction of an integral value to or from a pointer](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer) section.</span></span>

<span data-ttu-id="44ec2-141">L’exemple suivant montre comment accéder à des éléments tableau avec un pointeur et l’opérateur `[]` :</span><span class="sxs-lookup"><span data-stu-id="44ec2-141">The following example demonstrates how to access array elements with a pointer and the `[]` operator:</span></span>

[!code-csharp[pointer element access](~/samples/snippets/csharp/language-reference/operators/PointerOperators.cs#ElementAccess)]

<span data-ttu-id="44ec2-142">L’exemple utilise l’[opérateur `stackalloc`](stackalloc.md) pour allouer un bloc de mémoire à la pile.</span><span class="sxs-lookup"><span data-stu-id="44ec2-142">The example uses the [`stackalloc` operator](stackalloc.md) to allocate a block of memory on the stack.</span></span>

> [!NOTE]
> <span data-ttu-id="44ec2-143">L’opérateur d’accès aux éléments de pointeur ne recherche pas les erreurs de dépassement des limites.</span><span class="sxs-lookup"><span data-stu-id="44ec2-143">The pointer element access operator doesn't check for out-of-bounds errors.</span></span>

<span data-ttu-id="44ec2-144">Vous ne pouvez pas utiliser `[]` pour l’accès aux éléments de pointeur avec une expression de type `void*`.</span><span class="sxs-lookup"><span data-stu-id="44ec2-144">You cannot use `[]` for pointer element access with an expression of type `void*`.</span></span>

<span data-ttu-id="44ec2-145">Vous pouvez également utiliser l’opérateur `[]` pour l’[accès aux éléments de tableau ou à l’indexeur](member-access-operators.md#indexer-operator-).</span><span class="sxs-lookup"><span data-stu-id="44ec2-145">You also can use the `[]` operator for [array element or indexer access](member-access-operators.md#indexer-operator-).</span></span>

## <a name="pointer-arithmetic-operators"></a><span data-ttu-id="44ec2-146">Opérateurs arithmétiques de pointeur</span><span class="sxs-lookup"><span data-stu-id="44ec2-146">Pointer arithmetic operators</span></span>

<span data-ttu-id="44ec2-147">Vous pouvez effectuer les opérations arithmétiques suivantes avec des pointeurs :</span><span class="sxs-lookup"><span data-stu-id="44ec2-147">You can perform the following arithmetic operations with pointers:</span></span>

- <span data-ttu-id="44ec2-148">Ajouter ou soustraire une valeur intégrale dans un pointeur</span><span class="sxs-lookup"><span data-stu-id="44ec2-148">Add or subtract an integral value to or from a pointer</span></span>
- <span data-ttu-id="44ec2-149">Soustraire deux pointeurs</span><span class="sxs-lookup"><span data-stu-id="44ec2-149">Subtract two pointers</span></span>
- <span data-ttu-id="44ec2-150">Incrémenter ou décrémenter un pointeur</span><span class="sxs-lookup"><span data-stu-id="44ec2-150">Increment or decrement a pointer</span></span>

<span data-ttu-id="44ec2-151">Vous ne pouvez pas effectuer ces opérations avec des pointeurs de type `void*`.</span><span class="sxs-lookup"><span data-stu-id="44ec2-151">You cannot perform those operations with pointers of type `void*`.</span></span>

<span data-ttu-id="44ec2-152">Pour plus d’informations sur les opérations arithmétiques prises en charge avec les types numériques, consultez [Opérateurs arithmétiques](arithmetic-operators.md).</span><span class="sxs-lookup"><span data-stu-id="44ec2-152">For information about supported arithmetic operations with numeric types, see [Arithmetic operators](arithmetic-operators.md).</span></span>

### <a name="addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer"></a><span data-ttu-id="44ec2-153">Ajout ou soustraction d’une valeur intégrale dans un pointeur</span><span class="sxs-lookup"><span data-stu-id="44ec2-153">Addition or subtraction of an integral value to or from a pointer</span></span>

<span data-ttu-id="44ec2-154">Pour un pointeur `p` de type `T*` et une expression `n` d’un type implicitement convertible en `int`, `uint`, `long` ou `ulong`, l’addition et la soustraction sont définies de la façon suivante :</span><span class="sxs-lookup"><span data-stu-id="44ec2-154">For a pointer `p` of type `T*` and an expression `n` of a type implicitly convertible to `int`, `uint`, `long`, or `ulong`, addition and subtraction are defined as follows:</span></span>

- <span data-ttu-id="44ec2-155">Les expressions `p + n` et `n + p` produisent un pointeur de type `T*` qui est obtenu en ajoutant `n * sizeof(T)` à l’adresse fournie par `p`.</span><span class="sxs-lookup"><span data-stu-id="44ec2-155">Both `p + n` and `n + p` expressions produce a pointer of type `T*` that results from adding `n * sizeof(T)` to the address given by `p`.</span></span>
- <span data-ttu-id="44ec2-156">L’expression `p - n` produit un pointeur de type `T*` qui est obtenu en soustrayant `n * sizeof(T)` de l’adresse fournie par `p`.</span><span class="sxs-lookup"><span data-stu-id="44ec2-156">The `p - n` expression produces a pointer of type `T*` that results from subtracting `n * sizeof(T)` from the address given by `p`.</span></span>

<span data-ttu-id="44ec2-157">L’[opérateur `sizeof`](sizeof.md) permet d’obtenir la taille d’un type en octets.</span><span class="sxs-lookup"><span data-stu-id="44ec2-157">The [`sizeof` operator](sizeof.md) obtains the size of a type in bytes.</span></span>

<span data-ttu-id="44ec2-158">L’exemple suivant illustre l’utilisation de l’opérateur `+` avec un pointeur :</span><span class="sxs-lookup"><span data-stu-id="44ec2-158">The following example demonstrates the usage of the `+` operator with a pointer:</span></span>

[!code-csharp[pointer addition](~/samples/snippets/csharp/language-reference/operators/PointerOperators.cs#AddNumber)]

### <a name="pointer-subtraction"></a><span data-ttu-id="44ec2-159">Soustraction de pointeur</span><span class="sxs-lookup"><span data-stu-id="44ec2-159">Pointer subtraction</span></span>

<span data-ttu-id="44ec2-160">Pour deux pointeurs `p1` et `p2` de type `T*`, l’expression `p1 - p2` produit la différence entre les adresses fournies par `p1` et `p2`, divisée par `sizeof(T)`.</span><span class="sxs-lookup"><span data-stu-id="44ec2-160">For two pointers `p1` and `p2` of type `T*`, the expression `p1 - p2` produces the difference between the addresses given by `p1` and `p2` divided by `sizeof(T)`.</span></span> <span data-ttu-id="44ec2-161">Le type du résultat est `long`.</span><span class="sxs-lookup"><span data-stu-id="44ec2-161">The type of the result is `long`.</span></span> <span data-ttu-id="44ec2-162">C’est -à-dire que `p1 - p2`est calculé en tant que `((long)(p1) - (long)(p2)) / sizeof(T)`.</span><span class="sxs-lookup"><span data-stu-id="44ec2-162">That is, `p1 - p2` is computed as `((long)(p1) - (long)(p2)) / sizeof(T)`.</span></span>

<span data-ttu-id="44ec2-163">L’exemple suivant montre la soustraction d’un pointeur :</span><span class="sxs-lookup"><span data-stu-id="44ec2-163">The following example demonstrates the pointer subtraction:</span></span>

[!code-csharp[pointer subtraction](~/samples/snippets/csharp/language-reference/operators/PointerOperators.cs#SubtractPointers)]

### <a name="pointer-increment-and-decrement"></a><span data-ttu-id="44ec2-164">Incrémenter et décrémenter des pointeurs</span><span class="sxs-lookup"><span data-stu-id="44ec2-164">Pointer increment and decrement</span></span>

<span data-ttu-id="44ec2-165">L’opérateur d’incrémentation `++`[ajoute](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer) 1 à son opérande de pointeur.</span><span class="sxs-lookup"><span data-stu-id="44ec2-165">The `++` increment operator [adds](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer) 1 to its pointer operand.</span></span> <span data-ttu-id="44ec2-166">L’opérateur de décrémentation `--`[soustrait](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer) 1 de son opérande de pointeur.</span><span class="sxs-lookup"><span data-stu-id="44ec2-166">The `--` decrement operator [subtracts](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer) 1 from its pointer operand.</span></span>

<span data-ttu-id="44ec2-167">Les deux opérateurs sont pris en charge sous deux formes : suffixée (`p++` et `p--`) et préfixée (`++p` et `--p`).</span><span class="sxs-lookup"><span data-stu-id="44ec2-167">Both operators are supported in two forms: postfix (`p++` and `p--`) and prefix (`++p` and `--p`).</span></span> <span data-ttu-id="44ec2-168">Le résultat de `p++` et `p--` est la valeur de `p` *avant* l’opération.</span><span class="sxs-lookup"><span data-stu-id="44ec2-168">The result of `p++` and `p--` is the value of `p` *before* the operation.</span></span> <span data-ttu-id="44ec2-169">Le résultat de `++p` et `--p` est la valeur de `p` *après* l’opération.</span><span class="sxs-lookup"><span data-stu-id="44ec2-169">The result of `++p` and `--p` is the value of `p` *after* the operation.</span></span>

<span data-ttu-id="44ec2-170">L’exemple suivant montre le comportement des opérateurs d’incrémentation suffixés et préfixés :</span><span class="sxs-lookup"><span data-stu-id="44ec2-170">The following example demonstrates the behavior of both postfix and prefix increment operators:</span></span>

[!code-csharp[pointer increment](~/samples/snippets/csharp/language-reference/operators/PointerOperators.cs#Increment)]

## <a name="pointer-comparison-operators"></a><span data-ttu-id="44ec2-171">Opérateurs de comparaison de pointeur</span><span class="sxs-lookup"><span data-stu-id="44ec2-171">Pointer comparison operators</span></span>

<span data-ttu-id="44ec2-172">Vous pouvez utiliser les opérateurs `==`, `!=`, `<`, `>`, `<=` et `>=` pour comparer des opérandes de tout type de pointeur, y compris `void*`.</span><span class="sxs-lookup"><span data-stu-id="44ec2-172">You can use the `==`, `!=`, `<`, `>`, `<=`, and `>=` operators to compare operands of any pointer type, including `void*`.</span></span> <span data-ttu-id="44ec2-173">Ces opérateurs comparent les adresses fournies par les deux opérandes comme s’il s’agissait d’entiers non signés.</span><span class="sxs-lookup"><span data-stu-id="44ec2-173">Those operators compare the addresses given by the two operands as if they were unsigned integers.</span></span>

<span data-ttu-id="44ec2-174">Pour plus d’informations sur le comportement de ces opérateurs pour les opérandes d’autres types, consultez les articles [Opérateurs d’égalité](equality-operators.md) et [Opérateurs de comparaison](comparison-operators.md).</span><span class="sxs-lookup"><span data-stu-id="44ec2-174">For information about the behavior of those operators for operands of other types, see the [Equality operators](equality-operators.md) and [Comparison operators](comparison-operators.md) articles.</span></span>

## <a name="operator-precedence"></a><span data-ttu-id="44ec2-175">Priorité des opérateurs</span><span class="sxs-lookup"><span data-stu-id="44ec2-175">Operator precedence</span></span>

<span data-ttu-id="44ec2-176">La liste suivante présente les opérateurs relatifs aux pointeurs par ordre de précédence, de la plus élevée à la plus basse :</span><span class="sxs-lookup"><span data-stu-id="44ec2-176">The following list orders pointer related operators starting from the highest precedence to the lowest:</span></span>

- <span data-ttu-id="44ec2-177">Opérateurs suffixés d’incrémentation`x++` et de décrémentation `x--`, ainsi que les opérateurs `->` et `[]`</span><span class="sxs-lookup"><span data-stu-id="44ec2-177">Postfix increment `x++` and decrement `x--` operators and the `->` and `[]` operators</span></span>
- <span data-ttu-id="44ec2-178">Opérateurs préfixés d’incrémentation`++x` et de décrémentation `--x`, ainsi que les opérateurs `&` et `*`</span><span class="sxs-lookup"><span data-stu-id="44ec2-178">Prefix increment `++x` and decrement `--x` operators and the `&` and `*` operators</span></span>
- <span data-ttu-id="44ec2-179">Opérateurs additifs `+` et `-`</span><span class="sxs-lookup"><span data-stu-id="44ec2-179">Additive `+` and `-` operators</span></span>
- <span data-ttu-id="44ec2-180">Opérateurs de comparaison `<`, `>`, `<=` et `>=`</span><span class="sxs-lookup"><span data-stu-id="44ec2-180">Comparison `<`, `>`, `<=`, and `>=` operators</span></span>
- <span data-ttu-id="44ec2-181">Opérateurs d’égalité `==` et `!=`</span><span class="sxs-lookup"><span data-stu-id="44ec2-181">Equality `==` and `!=` operators</span></span>

<span data-ttu-id="44ec2-182">Utilisez des parenthèses (`()`) pour modifier l’ordre d’évaluation imposé par la précédence des opérateurs.</span><span class="sxs-lookup"><span data-stu-id="44ec2-182">Use parentheses, `()`, to change the order of evaluation imposed by operator precedence.</span></span>

<span data-ttu-id="44ec2-183">Pour obtenir la liste complète C# des opérateurs classés par niveau de priorité, consultez la section priorité d' [ C# ](index.md) [opérateur](index.md#operator-precedence) de l’article opérateurs.</span><span class="sxs-lookup"><span data-stu-id="44ec2-183">For the complete list of C# operators ordered by precedence level, see the [Operator precedence](index.md#operator-precedence) section of the [C# operators](index.md) article.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="44ec2-184">Capacité de surcharge de l’opérateur</span><span class="sxs-lookup"><span data-stu-id="44ec2-184">Operator overloadability</span></span>

<span data-ttu-id="44ec2-185">Un type défini par l’utilisateur ne peut pas surcharger les opérateurs de pointeur `&`, `*`, `->` et `[]`.</span><span class="sxs-lookup"><span data-stu-id="44ec2-185">A user-defined type cannot overload the pointer related operators `&`, `*`, `->`, and `[]`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="44ec2-186">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="44ec2-186">C# language specification</span></span>

<span data-ttu-id="44ec2-187">Pour plus d’informations, consultez les sections suivantes de la [spécification du langage C#](~/_csharplang/spec/introduction.md) :</span><span class="sxs-lookup"><span data-stu-id="44ec2-187">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="44ec2-188">Variables fixes et déplaçables</span><span class="sxs-lookup"><span data-stu-id="44ec2-188">Fixed and moveable variables</span></span>](~/_csharplang/spec/unsafe-code.md#fixed-and-moveable-variables)
- [<span data-ttu-id="44ec2-189">address-of, opérateur</span><span class="sxs-lookup"><span data-stu-id="44ec2-189">The address-of operator</span></span>](~/_csharplang/spec/unsafe-code.md#the-address-of-operator)
- [<span data-ttu-id="44ec2-190">Indirection de pointeur</span><span class="sxs-lookup"><span data-stu-id="44ec2-190">Pointer indirection</span></span>](~/_csharplang/spec/unsafe-code.md#pointer-indirection)
- [<span data-ttu-id="44ec2-191">Accès aux membres de pointeur</span><span class="sxs-lookup"><span data-stu-id="44ec2-191">Pointer member access</span></span>](~/_csharplang/spec/unsafe-code.md#pointer-member-access)
- [<span data-ttu-id="44ec2-192">Accès aux éléments de pointeur</span><span class="sxs-lookup"><span data-stu-id="44ec2-192">Pointer element access</span></span>](~/_csharplang/spec/unsafe-code.md#pointer-element-access)
- [<span data-ttu-id="44ec2-193">Arithmétique sur les pointeurs</span><span class="sxs-lookup"><span data-stu-id="44ec2-193">Pointer arithmetic</span></span>](~/_csharplang/spec/unsafe-code.md#pointer-arithmetic)
- [<span data-ttu-id="44ec2-194">Incrémentation et décrémentation des pointeurs</span><span class="sxs-lookup"><span data-stu-id="44ec2-194">Pointer increment and decrement</span></span>](~/_csharplang/spec/unsafe-code.md#pointer-increment-and-decrement)
- [<span data-ttu-id="44ec2-195">Comparaison de pointeurs</span><span class="sxs-lookup"><span data-stu-id="44ec2-195">Pointer comparison</span></span>](~/_csharplang/spec/unsafe-code.md#pointer-comparison)

## <a name="see-also"></a><span data-ttu-id="44ec2-196">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="44ec2-196">See also</span></span>

- [<span data-ttu-id="44ec2-197">Informations de référence sur C#</span><span class="sxs-lookup"><span data-stu-id="44ec2-197">C# reference</span></span>](../index.md)
- [<span data-ttu-id="44ec2-198">Opérateurs C#</span><span class="sxs-lookup"><span data-stu-id="44ec2-198">C# operators</span></span>](index.md)
- [<span data-ttu-id="44ec2-199">Types de pointeur</span><span class="sxs-lookup"><span data-stu-id="44ec2-199">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="44ec2-200">mot clé unsafe</span><span class="sxs-lookup"><span data-stu-id="44ec2-200">unsafe keyword</span></span>](../keywords/unsafe.md)
- [<span data-ttu-id="44ec2-201">Mot clé fixed</span><span class="sxs-lookup"><span data-stu-id="44ec2-201">fixed keyword</span></span>](../keywords/fixed-statement.md)
- [<span data-ttu-id="44ec2-202">Opérateur stackalloc</span><span class="sxs-lookup"><span data-stu-id="44ec2-202">stackalloc operator</span></span>](stackalloc.md)
- [<span data-ttu-id="44ec2-203">Opérateur sizeof</span><span class="sxs-lookup"><span data-stu-id="44ec2-203">sizeof operator</span></span>](sizeof.md)
