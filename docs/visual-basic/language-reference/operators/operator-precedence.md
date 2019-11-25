---
title: Priorité des opérateurs
ms.date: 07/20/2015
helpviewer_keywords:
- arithmetic operators [Visual Basic], precedence
- operator precedence
- logical operators [Visual Basic], precedence
- operators [Visual Basic], associativity
- operators [Visual Basic], resolution
- associativity of operators [Visual Basic]
- operators [Visual Basic], precedence
- precedence [Visual Basic], of operators
- comparison operators [Visual Basic], precedence
- math operators [Visual Basic]
- order of precedence
ms.assetid: cbbdb282-f572-458e-a520-008a675f8063
ms.openlocfilehash: 318fcc3f35276ba0b2061ba9677c5fde29429f6f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348282"
---
# <a name="operator-precedence-in-visual-basic"></a><span data-ttu-id="f50f0-102">Priorité des opérateurs en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f50f0-102">Operator Precedence in Visual Basic</span></span>
<span data-ttu-id="f50f0-103">When several operations occur in an expression, each part is evaluated and resolved in a predetermined order called *operator precedence*.</span><span class="sxs-lookup"><span data-stu-id="f50f0-103">When several operations occur in an expression, each part is evaluated and resolved in a predetermined order called *operator precedence*.</span></span>

## <a name="precedence-rules"></a><span data-ttu-id="f50f0-104">Precedence Rules</span><span class="sxs-lookup"><span data-stu-id="f50f0-104">Precedence Rules</span></span>
 <span data-ttu-id="f50f0-105">When expressions contain operators from more than one category, they are evaluated according to the following rules:</span><span class="sxs-lookup"><span data-stu-id="f50f0-105">When expressions contain operators from more than one category, they are evaluated according to the following rules:</span></span>

- <span data-ttu-id="f50f0-106">The arithmetic and concatenation operators have the order of precedence described in the following section, and all have greater precedence than the comparison, logical, and bitwise operators.</span><span class="sxs-lookup"><span data-stu-id="f50f0-106">The arithmetic and concatenation operators have the order of precedence described in the following section, and all have greater precedence than the comparison, logical, and bitwise operators.</span></span>

- <span data-ttu-id="f50f0-107">All comparison operators have equal precedence, and all have greater precedence than the logical and bitwise operators, but lower precedence than the arithmetic and concatenation operators.</span><span class="sxs-lookup"><span data-stu-id="f50f0-107">All comparison operators have equal precedence, and all have greater precedence than the logical and bitwise operators, but lower precedence than the arithmetic and concatenation operators.</span></span>

- <span data-ttu-id="f50f0-108">The logical and bitwise operators have the order of precedence described in the following section, and all have lower precedence than the arithmetic, concatenation, and comparison operators.</span><span class="sxs-lookup"><span data-stu-id="f50f0-108">The logical and bitwise operators have the order of precedence described in the following section, and all have lower precedence than the arithmetic, concatenation, and comparison operators.</span></span>

- <span data-ttu-id="f50f0-109">Operators with equal precedence are evaluated left to right in the order in which they appear in the expression.</span><span class="sxs-lookup"><span data-stu-id="f50f0-109">Operators with equal precedence are evaluated left to right in the order in which they appear in the expression.</span></span>

## <a name="precedence-order"></a><span data-ttu-id="f50f0-110">Precedence Order</span><span class="sxs-lookup"><span data-stu-id="f50f0-110">Precedence Order</span></span>
 <span data-ttu-id="f50f0-111">Operators are evaluated in the following order of precedence:</span><span class="sxs-lookup"><span data-stu-id="f50f0-111">Operators are evaluated in the following order of precedence:</span></span>

### <a name="await-operator"></a><span data-ttu-id="f50f0-112">Await, opérateur</span><span class="sxs-lookup"><span data-stu-id="f50f0-112">Await Operator</span></span>
 <span data-ttu-id="f50f0-113">Await</span><span class="sxs-lookup"><span data-stu-id="f50f0-113">Await</span></span>

### <a name="arithmetic-and-concatenation-operators"></a><span data-ttu-id="f50f0-114">Arithmetic and Concatenation Operators</span><span class="sxs-lookup"><span data-stu-id="f50f0-114">Arithmetic and Concatenation Operators</span></span>
 <span data-ttu-id="f50f0-115">Exponentiation (`^`)</span><span class="sxs-lookup"><span data-stu-id="f50f0-115">Exponentiation (`^`)</span></span>

 <span data-ttu-id="f50f0-116">Unary identity and negation (`+`, `–`)</span><span class="sxs-lookup"><span data-stu-id="f50f0-116">Unary identity and negation (`+`, `–`)</span></span>

 <span data-ttu-id="f50f0-117">Multiplication and floating-point division (`*`, `/`)</span><span class="sxs-lookup"><span data-stu-id="f50f0-117">Multiplication and floating-point division (`*`, `/`)</span></span>

 <span data-ttu-id="f50f0-118">Integer division (`\`)</span><span class="sxs-lookup"><span data-stu-id="f50f0-118">Integer division (`\`)</span></span>

 <span data-ttu-id="f50f0-119">Modular arithmetic (`Mod`)</span><span class="sxs-lookup"><span data-stu-id="f50f0-119">Modular arithmetic (`Mod`)</span></span>

 <span data-ttu-id="f50f0-120">Addition and subtraction (`+`, `–`)</span><span class="sxs-lookup"><span data-stu-id="f50f0-120">Addition and subtraction (`+`, `–`)</span></span>

 <span data-ttu-id="f50f0-121">String concatenation (`&`)</span><span class="sxs-lookup"><span data-stu-id="f50f0-121">String concatenation (`&`)</span></span>

 <span data-ttu-id="f50f0-122">Arithmetic bit shift (`<<`, `>>`)</span><span class="sxs-lookup"><span data-stu-id="f50f0-122">Arithmetic bit shift (`<<`, `>>`)</span></span>

### <a name="comparison-operators"></a><span data-ttu-id="f50f0-123">Opérateurs de comparaison</span><span class="sxs-lookup"><span data-stu-id="f50f0-123">Comparison Operators</span></span>
 <span data-ttu-id="f50f0-124">All comparison operators (`=`, `<>`, `<`, `<=`, `>`, `>=`, `Is`, `IsNot`, `Like`, `TypeOf`...`Is`)</span><span class="sxs-lookup"><span data-stu-id="f50f0-124">All comparison operators (`=`, `<>`, `<`, `<=`, `>`, `>=`, `Is`, `IsNot`, `Like`, `TypeOf`...`Is`)</span></span>

### <a name="logical-and-bitwise-operators"></a><span data-ttu-id="f50f0-125">Opérateurs de bits et opérateurs logiques</span><span class="sxs-lookup"><span data-stu-id="f50f0-125">Logical and Bitwise Operators</span></span>
 <span data-ttu-id="f50f0-126">Negation (`Not`)</span><span class="sxs-lookup"><span data-stu-id="f50f0-126">Negation (`Not`)</span></span>

 <span data-ttu-id="f50f0-127">Conjunction (`And`, `AndAlso`)</span><span class="sxs-lookup"><span data-stu-id="f50f0-127">Conjunction (`And`, `AndAlso`)</span></span>

 <span data-ttu-id="f50f0-128">Inclusive disjunction (`Or`, `OrElse`)</span><span class="sxs-lookup"><span data-stu-id="f50f0-128">Inclusive disjunction (`Or`, `OrElse`)</span></span>

 <span data-ttu-id="f50f0-129">Exclusive disjunction (`Xor`)</span><span class="sxs-lookup"><span data-stu-id="f50f0-129">Exclusive disjunction (`Xor`)</span></span>

### <a name="comments"></a><span data-ttu-id="f50f0-130">Comments</span><span class="sxs-lookup"><span data-stu-id="f50f0-130">Comments</span></span>
 <span data-ttu-id="f50f0-131">The `=` operator is only the equality comparison operator, not the assignment operator.</span><span class="sxs-lookup"><span data-stu-id="f50f0-131">The `=` operator is only the equality comparison operator, not the assignment operator.</span></span>

 <span data-ttu-id="f50f0-132">The string concatenation operator (`&`) is not an arithmetic operator, but in precedence it is grouped with the arithmetic operators.</span><span class="sxs-lookup"><span data-stu-id="f50f0-132">The string concatenation operator (`&`) is not an arithmetic operator, but in precedence it is grouped with the arithmetic operators.</span></span>

 <span data-ttu-id="f50f0-133">The `Is` and `IsNot` operators are object reference comparison operators.</span><span class="sxs-lookup"><span data-stu-id="f50f0-133">The `Is` and `IsNot` operators are object reference comparison operators.</span></span> <span data-ttu-id="f50f0-134">They do not compare the values of two objects; they check only to determine whether two object variables refer to the same object instance.</span><span class="sxs-lookup"><span data-stu-id="f50f0-134">They do not compare the values of two objects; they check only to determine whether two object variables refer to the same object instance.</span></span>

## <a name="associativity"></a><span data-ttu-id="f50f0-135">Associativité</span><span class="sxs-lookup"><span data-stu-id="f50f0-135">Associativity</span></span>
 <span data-ttu-id="f50f0-136">When operators of equal precedence appear together in an expression, for example multiplication and division, the compiler evaluates each operation as it encounters it from left to right.</span><span class="sxs-lookup"><span data-stu-id="f50f0-136">When operators of equal precedence appear together in an expression, for example multiplication and division, the compiler evaluates each operation as it encounters it from left to right.</span></span> <span data-ttu-id="f50f0-137">L'exemple suivant illustre ce comportement.</span><span class="sxs-lookup"><span data-stu-id="f50f0-137">The following example illustrates this.</span></span>

```vb
Dim n1 As Integer = 96 / 8 / 4
Dim n2 As Integer = (96 / 8) / 4
Dim n3 As Integer = 96 / (8 / 4)
```

 <span data-ttu-id="f50f0-138">The first expression evaluates the division 96 / 8 (which results in 12) and then the division 12 / 4, which results in three.</span><span class="sxs-lookup"><span data-stu-id="f50f0-138">The first expression evaluates the division 96 / 8 (which results in 12) and then the division 12 / 4, which results in three.</span></span> <span data-ttu-id="f50f0-139">Because the compiler evaluates the operations for `n1` from left to right, the evaluation is the same when that order is explicitly indicated for `n2`.</span><span class="sxs-lookup"><span data-stu-id="f50f0-139">Because the compiler evaluates the operations for `n1` from left to right, the evaluation is the same when that order is explicitly indicated for `n2`.</span></span> <span data-ttu-id="f50f0-140">Both `n1` and `n2` have a result of three.</span><span class="sxs-lookup"><span data-stu-id="f50f0-140">Both `n1` and `n2` have a result of three.</span></span> <span data-ttu-id="f50f0-141">By contrast, `n3` has a result of 48, because the parentheses force the compiler to evaluate 8 / 4 first.</span><span class="sxs-lookup"><span data-stu-id="f50f0-141">By contrast, `n3` has a result of 48, because the parentheses force the compiler to evaluate 8 / 4 first.</span></span>

 <span data-ttu-id="f50f0-142">Because of this behavior, operators are said to be *left associative* in Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="f50f0-142">Because of this behavior, operators are said to be *left associative* in Visual Basic.</span></span>

## <a name="overriding-precedence-and-associativity"></a><span data-ttu-id="f50f0-143">Overriding Precedence and Associativity</span><span class="sxs-lookup"><span data-stu-id="f50f0-143">Overriding Precedence and Associativity</span></span>
 <span data-ttu-id="f50f0-144">You can use parentheses to force some parts of an expression to be evaluated before others.</span><span class="sxs-lookup"><span data-stu-id="f50f0-144">You can use parentheses to force some parts of an expression to be evaluated before others.</span></span> <span data-ttu-id="f50f0-145">This can override both the order of precedence and the left associativity.</span><span class="sxs-lookup"><span data-stu-id="f50f0-145">This can override both the order of precedence and the left associativity.</span></span> <span data-ttu-id="f50f0-146">Visual Basic always performs operations that are enclosed in parentheses before those outside.</span><span class="sxs-lookup"><span data-stu-id="f50f0-146">Visual Basic always performs operations that are enclosed in parentheses before those outside.</span></span> <span data-ttu-id="f50f0-147">However, within parentheses, it maintains ordinary precedence and associativity, unless you use parentheses within the parentheses.</span><span class="sxs-lookup"><span data-stu-id="f50f0-147">However, within parentheses, it maintains ordinary precedence and associativity, unless you use parentheses within the parentheses.</span></span> <span data-ttu-id="f50f0-148">L'exemple suivant illustre ce comportement.</span><span class="sxs-lookup"><span data-stu-id="f50f0-148">The following example illustrates this.</span></span>

```vb
Dim a, b, c, d, e, f, g As Double
a = 8.0
b = 3.0
c = 4.0
d = 2.0
e = 1.0
f = a - b + c / d * e
' The preceding line sets f to 7.0. Because of natural operator
' precedence and associativity, it is exactly equivalent to the
' following line.
f = (a - b) + ((c / d) * e)
' The following line overrides the natural operator precedence
' and left associativity.
g = (a - (b + c)) / (d * e)
' The preceding line sets g to 0.5.
```

## <a name="see-also"></a><span data-ttu-id="f50f0-149">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f50f0-149">See also</span></span>

- [<span data-ttu-id="f50f0-150">= (opérateur)</span><span class="sxs-lookup"><span data-stu-id="f50f0-150">= Operator</span></span>](../../../visual-basic/language-reference/operators/assignment-operator.md)
- [<span data-ttu-id="f50f0-151">Is (opérateur)</span><span class="sxs-lookup"><span data-stu-id="f50f0-151">Is Operator</span></span>](../../../visual-basic/language-reference/operators/is-operator.md)
- [<span data-ttu-id="f50f0-152">IsNot (opérateur)</span><span class="sxs-lookup"><span data-stu-id="f50f0-152">IsNot Operator</span></span>](../../../visual-basic/language-reference/operators/isnot-operator.md)
- [<span data-ttu-id="f50f0-153">Like (opérateur)</span><span class="sxs-lookup"><span data-stu-id="f50f0-153">Like Operator</span></span>](../../../visual-basic/language-reference/operators/like-operator.md)
- [<span data-ttu-id="f50f0-154">TypeOf (opérateur)</span><span class="sxs-lookup"><span data-stu-id="f50f0-154">TypeOf Operator</span></span>](../../../visual-basic/language-reference/operators/typeof-operator.md)
- [<span data-ttu-id="f50f0-155">Await (opérateur)</span><span class="sxs-lookup"><span data-stu-id="f50f0-155">Await Operator</span></span>](../../../visual-basic/language-reference/operators/await-operator.md)
- [<span data-ttu-id="f50f0-156">Opérateurs répertoriés par fonctionnalité</span><span class="sxs-lookup"><span data-stu-id="f50f0-156">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="f50f0-157">Opérateurs et expressions</span><span class="sxs-lookup"><span data-stu-id="f50f0-157">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
