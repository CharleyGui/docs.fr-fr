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
ms.openlocfilehash: 3728778b31a4b4adc51933e8fdc6287f28e03d83
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/07/2020
ms.locfileid: "87916711"
---
# <a name="pointer-related-operators-c-reference"></a><span data-ttu-id="181fd-103">Opérateurs associés au pointeur (référence C#)</span><span class="sxs-lookup"><span data-stu-id="181fd-103">Pointer related operators (C# reference)</span></span>

<span data-ttu-id="181fd-104">Vous pouvez utiliser les opérateurs suivants avec les pointeurs :</span><span class="sxs-lookup"><span data-stu-id="181fd-104">You can use the following operators to work with pointers:</span></span>

- <span data-ttu-id="181fd-105">Opérateur unaire [ `&` (adresse-of)](#address-of-operator-) : pour obtenir l’adresse d’une variable</span><span class="sxs-lookup"><span data-stu-id="181fd-105">Unary [`&` (address-of)](#address-of-operator-) operator: to get the address of a variable</span></span>
- <span data-ttu-id="181fd-106">Opérateur unaire [ `*` (pointeur d’indirection)](#pointer-indirection-operator-) : pour obtenir la variable pointée par un pointeur</span><span class="sxs-lookup"><span data-stu-id="181fd-106">Unary [`*` (pointer indirection)](#pointer-indirection-operator-) operator: to obtain the variable pointed by a pointer</span></span>
- <span data-ttu-id="181fd-107">Opérateurs [ `->` (accès aux membres)](#pointer-member-access-operator--) et [ `[]` (accès à l’élément)](#pointer-element-access-operator-)</span><span class="sxs-lookup"><span data-stu-id="181fd-107">The [`->` (member access)](#pointer-member-access-operator--) and [`[]` (element access)](#pointer-element-access-operator-) operators</span></span>
- <span data-ttu-id="181fd-108">Opérateurs arithmétiques [ `+` ,, `-` `++` et `--` ](#pointer-arithmetic-operators)</span><span class="sxs-lookup"><span data-stu-id="181fd-108">Arithmetic operators [`+`, `-`, `++`, and `--`](#pointer-arithmetic-operators)</span></span>
- <span data-ttu-id="181fd-109">Opérateurs de comparaison [ `==` ,,,, `!=` `<` `>` `<=` et `>=` ](#pointer-comparison-operators)</span><span class="sxs-lookup"><span data-stu-id="181fd-109">Comparison operators [`==`, `!=`, `<`, `>`, `<=`, and `>=`](#pointer-comparison-operators)</span></span>

<span data-ttu-id="181fd-110">Pour plus d’informations sur les types de pointeurs, consultez [Types pointeur](../../programming-guide/unsafe-code-pointers/pointer-types.md).</span><span class="sxs-lookup"><span data-stu-id="181fd-110">For information about pointer types, see [Pointer types](../../programming-guide/unsafe-code-pointers/pointer-types.md).</span></span>

> [!NOTE]
> <span data-ttu-id="181fd-111">Toutes les opérations impliquant des pointeurs nécessitent un contexte [unsafe](../keywords/unsafe.md).</span><span class="sxs-lookup"><span data-stu-id="181fd-111">Any operation with pointers requires an [unsafe](../keywords/unsafe.md) context.</span></span> <span data-ttu-id="181fd-112">Le code qui contient des blocs unsafe doit être compilé avec l' [`-unsafe`](../compiler-options/unsafe-compiler-option.md) option de compilateur.</span><span class="sxs-lookup"><span data-stu-id="181fd-112">The code that contains unsafe blocks must be compiled with the [`-unsafe`](../compiler-options/unsafe-compiler-option.md) compiler option.</span></span>

## <a name="address-of-operator-amp"></a><a name="address-of-operator-"></a><span data-ttu-id="181fd-113">Opérateur d’adresse&amp;</span><span class="sxs-lookup"><span data-stu-id="181fd-113">Address-of operator &amp;</span></span>

<span data-ttu-id="181fd-114">L’opérateur unaire `&` retourne l’adresse de son opérande :</span><span class="sxs-lookup"><span data-stu-id="181fd-114">The unary `&` operator returns the address of its operand:</span></span>

[!code-csharp[address of local](snippets/shared/PointerOperators.cs#AddressOf)]

<span data-ttu-id="181fd-115">L’opérande de l’opérateur `&` doit être une variable fixe.</span><span class="sxs-lookup"><span data-stu-id="181fd-115">The operand of the `&` operator must be a fixed variable.</span></span> <span data-ttu-id="181fd-116">Les variables *fixes* se trouvent dans des emplacements de stockage qui ne sont pas affectés par le [récupérateur de mémoire](../../../standard/garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="181fd-116">*Fixed* variables are variables that reside in storage locations that are unaffected by operation of the [garbage collector](../../../standard/garbage-collection/index.md).</span></span> <span data-ttu-id="181fd-117">Dans l’exemple précédent, la variable locale `number` est une variable fixe, car elle se trouve dans la pile.</span><span class="sxs-lookup"><span data-stu-id="181fd-117">In the preceding example, the local variable `number` is a fixed variable, because it resides on the stack.</span></span> <span data-ttu-id="181fd-118">Les variables qui se trouvent dans des emplacements de stockage pouvant être affectés par le récupérateur de mémoire (par exemple, en étant déplacés) sont appelées variables *déplaçables*.</span><span class="sxs-lookup"><span data-stu-id="181fd-118">Variables that reside in storage locations that can be affected by the garbage collector (for example, relocated) are called *movable* variables.</span></span> <span data-ttu-id="181fd-119">Les champs d’objet et les éléments de tableau sont des exemples de variables déplaçables.</span><span class="sxs-lookup"><span data-stu-id="181fd-119">Object fields and array elements are examples of movable variables.</span></span> <span data-ttu-id="181fd-120">Vous pouvez obtenir l’adresse d’une variable déplaçable si vous « corrigez », ou « épinglez », avec une [ `fixed` instruction](../keywords/fixed-statement.md).</span><span class="sxs-lookup"><span data-stu-id="181fd-120">You can get the address of a movable variable if you "fix", or "pin", it with a [`fixed` statement](../keywords/fixed-statement.md).</span></span> <span data-ttu-id="181fd-121">L’adresse obtenue est valide uniquement à l’intérieur du bloc d’une `fixed` instruction.</span><span class="sxs-lookup"><span data-stu-id="181fd-121">The obtained address is valid only inside the block of a `fixed` statement.</span></span> <span data-ttu-id="181fd-122">L’exemple suivant montre comment utiliser une `fixed` instruction et l' `&` opérateur :</span><span class="sxs-lookup"><span data-stu-id="181fd-122">The following example shows how to use a `fixed` statement and the `&` operator:</span></span>

[!code-csharp[address of fixed](snippets/shared/PointerOperators.cs#AddressOfFixed)]

<span data-ttu-id="181fd-123">Vous ne pouvez pas obtenir l’adresse d’une constante ou d’une valeur.</span><span class="sxs-lookup"><span data-stu-id="181fd-123">You can't get the address of a constant or a value.</span></span>

<span data-ttu-id="181fd-124">Pour plus d’informations sur les variables fixes et déplaçables, consultez la section [Variables fixes et déplaçables](~/_csharplang/spec/unsafe-code.md#fixed-and-moveable-variables) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="181fd-124">For more information about fixed and movable variables, see the [Fixed and moveable variables](~/_csharplang/spec/unsafe-code.md#fixed-and-moveable-variables) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="181fd-125">L’opérateur binaire `&` calcule la [logique AND](boolean-logical-operators.md#logical-and-operator-) de ses opérandes booléens, ou la [logique AND au niveau du bit](bitwise-and-shift-operators.md#logical-and-operator-) de ses opérandes de type intégral.</span><span class="sxs-lookup"><span data-stu-id="181fd-125">The binary `&` operator computes the [logical AND](boolean-logical-operators.md#logical-and-operator-) of its Boolean operands or the [bitwise logical AND](bitwise-and-shift-operators.md#logical-and-operator-) of its integral operands.</span></span>

## <a name="pointer-indirection-operator-"></a><span data-ttu-id="181fd-126">Opérateur d’indirection de pointeur \*</span><span class="sxs-lookup"><span data-stu-id="181fd-126">Pointer indirection operator \*</span></span>

<span data-ttu-id="181fd-127">L’opérateur unaire d’indirection de pointeur `*` permet d’obtenir la variable vers laquelle pointe son opérande.</span><span class="sxs-lookup"><span data-stu-id="181fd-127">The unary pointer indirection operator `*` obtains the variable to which its operand points.</span></span> <span data-ttu-id="181fd-128">Il est également appelé « opérateur de déréférence ».</span><span class="sxs-lookup"><span data-stu-id="181fd-128">It's also known as the dereference operator.</span></span> <span data-ttu-id="181fd-129">L’opérande de l’opérateur `*` doit être un type de pointeur.</span><span class="sxs-lookup"><span data-stu-id="181fd-129">The operand of the `*` operator must be of a pointer type.</span></span>

[!code-csharp[pointer indirection](snippets/shared/PointerOperators.cs#PointerIndirection)]

<span data-ttu-id="181fd-130">Vous ne pouvez pas appliquer l’opérateur `*` à une expression de type `void*`.</span><span class="sxs-lookup"><span data-stu-id="181fd-130">You cannot apply the `*` operator to an expression of type `void*`.</span></span>

<span data-ttu-id="181fd-131">L’opérateur binaire `*` calcule le [produit](arithmetic-operators.md#multiplication-operator-) de ses opérandes numériques.</span><span class="sxs-lookup"><span data-stu-id="181fd-131">The binary `*` operator computes the [product](arithmetic-operators.md#multiplication-operator-) of its numeric operands.</span></span>

## <a name="pointer-member-access-operator--"></a><span data-ttu-id="181fd-132">Opérateur d’accès aux membres de pointeur -></span><span class="sxs-lookup"><span data-stu-id="181fd-132">Pointer member access operator -></span></span>

<span data-ttu-id="181fd-133">L’opérateur `->` associe l’[indirection de pointeur](#pointer-indirection-operator-) à l’[accès aux membres](member-access-operators.md#member-access-expression-).</span><span class="sxs-lookup"><span data-stu-id="181fd-133">The `->` operator combines [pointer indirection](#pointer-indirection-operator-) and [member access](member-access-operators.md#member-access-expression-).</span></span> <span data-ttu-id="181fd-134">Autrement dit, si `x` est un pointeur de type `T*` et `y` est un membre accessible de type `T` , une expression de la forme</span><span class="sxs-lookup"><span data-stu-id="181fd-134">That is, if `x` is a pointer of type `T*` and `y` is an accessible member of type `T`, an expression of the form</span></span>

```csharp
x->y
```

<span data-ttu-id="181fd-135">équivaut à :</span><span class="sxs-lookup"><span data-stu-id="181fd-135">is equivalent to</span></span>

```csharp
(*x).y
```

<span data-ttu-id="181fd-136">L’exemple suivant illustre l’utilisation de l’opérateur `->` :</span><span class="sxs-lookup"><span data-stu-id="181fd-136">The following example demonstrates the usage of the `->` operator:</span></span>

[!code-csharp[pointer member access](snippets/shared/PointerOperators.cs#MemberAccess)]

<span data-ttu-id="181fd-137">Vous ne pouvez pas appliquer l’opérateur `->` à une expression de type `void*`.</span><span class="sxs-lookup"><span data-stu-id="181fd-137">You cannot apply the `->` operator to an expression of type `void*`.</span></span>

## <a name="pointer-element-access-operator-"></a><span data-ttu-id="181fd-138">Opérateur d’accès aux éléments de pointeur []</span><span class="sxs-lookup"><span data-stu-id="181fd-138">Pointer element access operator []</span></span>

<span data-ttu-id="181fd-139">Pour une expression `p` d’un type pointeur, l’accès à un élément de pointeur au format `p[n]` est évalué comme `*(p + n)`, où `n` doit être d’un type implicitement convertible en `int`, `uint`, `long` ou `ulong`.</span><span class="sxs-lookup"><span data-stu-id="181fd-139">For an expression `p` of a pointer type, a pointer element access of the form `p[n]` is evaluated as `*(p + n)`, where `n` must be of a type implicitly convertible to `int`, `uint`, `long`, or `ulong`.</span></span> <span data-ttu-id="181fd-140">Pour plus d’informations sur le comportement de l’opérateur `+` avec les pointeurs, consultez la section [Addition ou soustraction d’une valeur intégrale dans un pointeur](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer).</span><span class="sxs-lookup"><span data-stu-id="181fd-140">For information about the behavior of the `+` operator with pointers, see the [Addition or subtraction of an integral value to or from a pointer](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer) section.</span></span>

<span data-ttu-id="181fd-141">L’exemple suivant montre comment accéder à des éléments tableau avec un pointeur et l’opérateur `[]` :</span><span class="sxs-lookup"><span data-stu-id="181fd-141">The following example demonstrates how to access array elements with a pointer and the `[]` operator:</span></span>

[!code-csharp[pointer element access](snippets/shared/PointerOperators.cs#ElementAccess)]

<span data-ttu-id="181fd-142">Dans l’exemple précédent, une [ `stackalloc` expression](stackalloc.md) alloue un bloc de mémoire sur la pile.</span><span class="sxs-lookup"><span data-stu-id="181fd-142">In the preceding example, a [`stackalloc` expression](stackalloc.md) allocates a block of memory on the stack.</span></span>

> [!NOTE]
> <span data-ttu-id="181fd-143">L’opérateur d’accès aux éléments de pointeur ne recherche pas les erreurs de dépassement des limites.</span><span class="sxs-lookup"><span data-stu-id="181fd-143">The pointer element access operator doesn't check for out-of-bounds errors.</span></span>

<span data-ttu-id="181fd-144">Vous ne pouvez pas utiliser `[]` pour l’accès aux éléments de pointeur avec une expression de type `void*`.</span><span class="sxs-lookup"><span data-stu-id="181fd-144">You cannot use `[]` for pointer element access with an expression of type `void*`.</span></span>

<span data-ttu-id="181fd-145">Vous pouvez également utiliser l' `[]` opérateur pour l’accès à un [élément ou un indexeur de tableau](member-access-operators.md#indexer-operator-).</span><span class="sxs-lookup"><span data-stu-id="181fd-145">You can also use the `[]` operator for [array element or indexer access](member-access-operators.md#indexer-operator-).</span></span>

## <a name="pointer-arithmetic-operators"></a><span data-ttu-id="181fd-146">Opérateurs arithmétiques de pointeur</span><span class="sxs-lookup"><span data-stu-id="181fd-146">Pointer arithmetic operators</span></span>

<span data-ttu-id="181fd-147">Vous pouvez effectuer les opérations arithmétiques suivantes avec des pointeurs :</span><span class="sxs-lookup"><span data-stu-id="181fd-147">You can perform the following arithmetic operations with pointers:</span></span>

- <span data-ttu-id="181fd-148">Ajouter ou soustraire une valeur intégrale dans un pointeur</span><span class="sxs-lookup"><span data-stu-id="181fd-148">Add or subtract an integral value to or from a pointer</span></span>
- <span data-ttu-id="181fd-149">Soustraire deux pointeurs</span><span class="sxs-lookup"><span data-stu-id="181fd-149">Subtract two pointers</span></span>
- <span data-ttu-id="181fd-150">Incrémenter ou décrémenter un pointeur</span><span class="sxs-lookup"><span data-stu-id="181fd-150">Increment or decrement a pointer</span></span>

<span data-ttu-id="181fd-151">Vous ne pouvez pas effectuer ces opérations avec des pointeurs de type `void*`.</span><span class="sxs-lookup"><span data-stu-id="181fd-151">You cannot perform those operations with pointers of type `void*`.</span></span>

<span data-ttu-id="181fd-152">Pour plus d’informations sur les opérations arithmétiques prises en charge avec les types numériques, consultez [Opérateurs arithmétiques](arithmetic-operators.md).</span><span class="sxs-lookup"><span data-stu-id="181fd-152">For information about supported arithmetic operations with numeric types, see [Arithmetic operators](arithmetic-operators.md).</span></span>

### <a name="addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer"></a><span data-ttu-id="181fd-153">Ajout ou soustraction d’une valeur intégrale dans un pointeur</span><span class="sxs-lookup"><span data-stu-id="181fd-153">Addition or subtraction of an integral value to or from a pointer</span></span>

<span data-ttu-id="181fd-154">Pour un pointeur `p` de type `T*` et une expression `n` d’un type implicitement convertible en `int`, `uint`, `long` ou `ulong`, l’addition et la soustraction sont définies de la façon suivante :</span><span class="sxs-lookup"><span data-stu-id="181fd-154">For a pointer `p` of type `T*` and an expression `n` of a type implicitly convertible to `int`, `uint`, `long`, or `ulong`, addition and subtraction are defined as follows:</span></span>

- <span data-ttu-id="181fd-155">Les expressions `p + n` et `n + p` produisent un pointeur de type `T*` qui est obtenu en ajoutant `n * sizeof(T)` à l’adresse fournie par `p`.</span><span class="sxs-lookup"><span data-stu-id="181fd-155">Both `p + n` and `n + p` expressions produce a pointer of type `T*` that results from adding `n * sizeof(T)` to the address given by `p`.</span></span>
- <span data-ttu-id="181fd-156">L’expression `p - n` produit un pointeur de type `T*` qui est obtenu en soustrayant `n * sizeof(T)` de l’adresse fournie par `p`.</span><span class="sxs-lookup"><span data-stu-id="181fd-156">The `p - n` expression produces a pointer of type `T*` that results from subtracting `n * sizeof(T)` from the address given by `p`.</span></span>

<span data-ttu-id="181fd-157">L' [ `sizeof` opérateur](sizeof.md) obtient la taille d’un type en octets.</span><span class="sxs-lookup"><span data-stu-id="181fd-157">The [`sizeof` operator](sizeof.md) obtains the size of a type in bytes.</span></span>

<span data-ttu-id="181fd-158">L’exemple suivant illustre l’utilisation de l’opérateur `+` avec un pointeur :</span><span class="sxs-lookup"><span data-stu-id="181fd-158">The following example demonstrates the usage of the `+` operator with a pointer:</span></span>

[!code-csharp[pointer addition](snippets/shared/PointerOperators.cs#AddNumber)]

### <a name="pointer-subtraction"></a><span data-ttu-id="181fd-159">Soustraction de pointeur</span><span class="sxs-lookup"><span data-stu-id="181fd-159">Pointer subtraction</span></span>

<span data-ttu-id="181fd-160">Pour deux pointeurs `p1` et `p2` de type `T*`, l’expression `p1 - p2` produit la différence entre les adresses fournies par `p1` et `p2`, divisée par `sizeof(T)`.</span><span class="sxs-lookup"><span data-stu-id="181fd-160">For two pointers `p1` and `p2` of type `T*`, the expression `p1 - p2` produces the difference between the addresses given by `p1` and `p2` divided by `sizeof(T)`.</span></span> <span data-ttu-id="181fd-161">Le type du résultat est `long`.</span><span class="sxs-lookup"><span data-stu-id="181fd-161">The type of the result is `long`.</span></span> <span data-ttu-id="181fd-162">C’est -à-dire que `p1 - p2`est calculé en tant que `((long)(p1) - (long)(p2)) / sizeof(T)`.</span><span class="sxs-lookup"><span data-stu-id="181fd-162">That is, `p1 - p2` is computed as `((long)(p1) - (long)(p2)) / sizeof(T)`.</span></span>

<span data-ttu-id="181fd-163">L’exemple suivant montre la soustraction d’un pointeur :</span><span class="sxs-lookup"><span data-stu-id="181fd-163">The following example demonstrates the pointer subtraction:</span></span>

[!code-csharp[pointer subtraction](snippets/shared/PointerOperators.cs#SubtractPointers)]

### <a name="pointer-increment-and-decrement"></a><span data-ttu-id="181fd-164">Incrémenter et décrémenter des pointeurs</span><span class="sxs-lookup"><span data-stu-id="181fd-164">Pointer increment and decrement</span></span>

<span data-ttu-id="181fd-165">L’opérateur d’incrémentation `++`[ajoute](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer) 1 à son opérande de pointeur.</span><span class="sxs-lookup"><span data-stu-id="181fd-165">The `++` increment operator [adds](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer) 1 to its pointer operand.</span></span> <span data-ttu-id="181fd-166">L’opérateur de décrémentation `--`[soustrait](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer) 1 de son opérande de pointeur.</span><span class="sxs-lookup"><span data-stu-id="181fd-166">The `--` decrement operator [subtracts](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer) 1 from its pointer operand.</span></span>

<span data-ttu-id="181fd-167">Les deux opérateurs sont pris en charge sous deux formes : suffixée (`p++` et `p--`) et préfixée (`++p` et `--p`).</span><span class="sxs-lookup"><span data-stu-id="181fd-167">Both operators are supported in two forms: postfix (`p++` and `p--`) and prefix (`++p` and `--p`).</span></span> <span data-ttu-id="181fd-168">Le résultat de `p++` et `p--` correspond à la valeur de `p` *avant* l’opération.</span><span class="sxs-lookup"><span data-stu-id="181fd-168">The result of `p++` and `p--` is the value of `p` *before* the operation.</span></span> <span data-ttu-id="181fd-169">Le résultat de `++p` et `--p` correspond à la valeur de `p` *après* l’opération.</span><span class="sxs-lookup"><span data-stu-id="181fd-169">The result of `++p` and `--p` is the value of `p` *after* the operation.</span></span>

<span data-ttu-id="181fd-170">L’exemple suivant montre le comportement des opérateurs d’incrémentation suffixés et préfixés :</span><span class="sxs-lookup"><span data-stu-id="181fd-170">The following example demonstrates the behavior of both postfix and prefix increment operators:</span></span>

[!code-csharp[pointer increment](snippets/shared/PointerOperators.cs#Increment)]

## <a name="pointer-comparison-operators"></a><span data-ttu-id="181fd-171">Opérateurs de comparaison de pointeur</span><span class="sxs-lookup"><span data-stu-id="181fd-171">Pointer comparison operators</span></span>

<span data-ttu-id="181fd-172">Vous pouvez utiliser les opérateurs `==`, `!=`, `<`, `>`, `<=` et `>=` pour comparer des opérandes de tout type de pointeur, y compris `void*`.</span><span class="sxs-lookup"><span data-stu-id="181fd-172">You can use the `==`, `!=`, `<`, `>`, `<=`, and `>=` operators to compare operands of any pointer type, including `void*`.</span></span> <span data-ttu-id="181fd-173">Ces opérateurs comparent les adresses fournies par les deux opérandes comme s’il s’agissait d’entiers non signés.</span><span class="sxs-lookup"><span data-stu-id="181fd-173">Those operators compare the addresses given by the two operands as if they were unsigned integers.</span></span>

<span data-ttu-id="181fd-174">Pour plus d’informations sur le comportement de ces opérateurs pour les opérandes d’autres types, consultez les articles [Opérateurs d’égalité](equality-operators.md) et [Opérateurs de comparaison](comparison-operators.md).</span><span class="sxs-lookup"><span data-stu-id="181fd-174">For information about the behavior of those operators for operands of other types, see the [Equality operators](equality-operators.md) and [Comparison operators](comparison-operators.md) articles.</span></span>

## <a name="operator-precedence"></a><span data-ttu-id="181fd-175">Précédence des opérateurs</span><span class="sxs-lookup"><span data-stu-id="181fd-175">Operator precedence</span></span>

<span data-ttu-id="181fd-176">La liste suivante présente les opérateurs relatifs aux pointeurs par ordre de précédence, de la plus élevée à la plus basse :</span><span class="sxs-lookup"><span data-stu-id="181fd-176">The following list orders pointer related operators starting from the highest precedence to the lowest:</span></span>

- <span data-ttu-id="181fd-177">Opérateurs suffixés d’incrémentation`x++` et de décrémentation `x--`, ainsi que les opérateurs `->` et `[]`</span><span class="sxs-lookup"><span data-stu-id="181fd-177">Postfix increment `x++` and decrement `x--` operators and the `->` and `[]` operators</span></span>
- <span data-ttu-id="181fd-178">Opérateurs préfixés d’incrémentation`++x` et de décrémentation `--x`, ainsi que les opérateurs `&` et `*`</span><span class="sxs-lookup"><span data-stu-id="181fd-178">Prefix increment `++x` and decrement `--x` operators and the `&` and `*` operators</span></span>
- <span data-ttu-id="181fd-179">Opérateurs additifs `+` et `-`</span><span class="sxs-lookup"><span data-stu-id="181fd-179">Additive `+` and `-` operators</span></span>
- <span data-ttu-id="181fd-180">Opérateurs de comparaison `<`, `>`, `<=` et `>=`</span><span class="sxs-lookup"><span data-stu-id="181fd-180">Comparison `<`, `>`, `<=`, and `>=` operators</span></span>
- <span data-ttu-id="181fd-181">Opérateurs d’égalité `==` et `!=`</span><span class="sxs-lookup"><span data-stu-id="181fd-181">Equality `==` and `!=` operators</span></span>

<span data-ttu-id="181fd-182">Utilisez des parenthèses (`()`) pour modifier l’ordre d’évaluation imposé par la précédence des opérateurs.</span><span class="sxs-lookup"><span data-stu-id="181fd-182">Use parentheses, `()`, to change the order of evaluation imposed by operator precedence.</span></span>

<span data-ttu-id="181fd-183">Pour obtenir la liste complète des opérateurs C# classés par niveau de priorité, consultez la section [priorité d’opérateur](index.md#operator-precedence) de l’article [opérateurs c#](index.md) .</span><span class="sxs-lookup"><span data-stu-id="181fd-183">For the complete list of C# operators ordered by precedence level, see the [Operator precedence](index.md#operator-precedence) section of the [C# operators](index.md) article.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="181fd-184">Capacité de surcharge de l’opérateur</span><span class="sxs-lookup"><span data-stu-id="181fd-184">Operator overloadability</span></span>

<span data-ttu-id="181fd-185">Un type défini par l’utilisateur ne peut pas surcharger les opérateurs de pointeur `&`, `*`, `->` et `[]`.</span><span class="sxs-lookup"><span data-stu-id="181fd-185">A user-defined type cannot overload the pointer related operators `&`, `*`, `->`, and `[]`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="181fd-186">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="181fd-186">C# language specification</span></span>

<span data-ttu-id="181fd-187">Pour plus d’informations, consultez les sections suivantes de la [spécification du langage C#](~/_csharplang/spec/introduction.md) :</span><span class="sxs-lookup"><span data-stu-id="181fd-187">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="181fd-188">Variables fixes et déplaçables</span><span class="sxs-lookup"><span data-stu-id="181fd-188">Fixed and moveable variables</span></span>](~/_csharplang/spec/unsafe-code.md#fixed-and-moveable-variables)
- [<span data-ttu-id="181fd-189">address-of, opérateur</span><span class="sxs-lookup"><span data-stu-id="181fd-189">The address-of operator</span></span>](~/_csharplang/spec/unsafe-code.md#the-address-of-operator)
- [<span data-ttu-id="181fd-190">Indirection de pointeur</span><span class="sxs-lookup"><span data-stu-id="181fd-190">Pointer indirection</span></span>](~/_csharplang/spec/unsafe-code.md#pointer-indirection)
- [<span data-ttu-id="181fd-191">Accès aux membres de pointeur</span><span class="sxs-lookup"><span data-stu-id="181fd-191">Pointer member access</span></span>](~/_csharplang/spec/unsafe-code.md#pointer-member-access)
- [<span data-ttu-id="181fd-192">Accès aux éléments de pointeur</span><span class="sxs-lookup"><span data-stu-id="181fd-192">Pointer element access</span></span>](~/_csharplang/spec/unsafe-code.md#pointer-element-access)
- [<span data-ttu-id="181fd-193">Arithmétique des pointeurs</span><span class="sxs-lookup"><span data-stu-id="181fd-193">Pointer arithmetic</span></span>](~/_csharplang/spec/unsafe-code.md#pointer-arithmetic)
- [<span data-ttu-id="181fd-194">Incrémentation et décrémentation des pointeurs</span><span class="sxs-lookup"><span data-stu-id="181fd-194">Pointer increment and decrement</span></span>](~/_csharplang/spec/unsafe-code.md#pointer-increment-and-decrement)
- [<span data-ttu-id="181fd-195">Comparaison de pointeurs</span><span class="sxs-lookup"><span data-stu-id="181fd-195">Pointer comparison</span></span>](~/_csharplang/spec/unsafe-code.md#pointer-comparison)

## <a name="see-also"></a><span data-ttu-id="181fd-196">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="181fd-196">See also</span></span>

- [<span data-ttu-id="181fd-197">Informations de référence sur C#</span><span class="sxs-lookup"><span data-stu-id="181fd-197">C# reference</span></span>](../index.md)
- [<span data-ttu-id="181fd-198">Opérateurs et expressions C#</span><span class="sxs-lookup"><span data-stu-id="181fd-198">C# operators and expressions</span></span>](index.md)
- [<span data-ttu-id="181fd-199">Types de pointeur</span><span class="sxs-lookup"><span data-stu-id="181fd-199">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="181fd-200">mot clé unsafe</span><span class="sxs-lookup"><span data-stu-id="181fd-200">unsafe keyword</span></span>](../keywords/unsafe.md)
- [<span data-ttu-id="181fd-201">mot clé Fixed</span><span class="sxs-lookup"><span data-stu-id="181fd-201">fixed keyword</span></span>](../keywords/fixed-statement.md)
- [<span data-ttu-id="181fd-202">stackalloc</span><span class="sxs-lookup"><span data-stu-id="181fd-202">stackalloc</span></span>](stackalloc.md)
- [<span data-ttu-id="181fd-203">Opérateur sizeof</span><span class="sxs-lookup"><span data-stu-id="181fd-203">sizeof operator</span></span>](sizeof.md)
