---
title: Mod, opérateur
ms.date: 04/24/2018
f1_keywords:
- vb.Mod
helpviewer_keywords:
- remainder (Mod operator)
- division operator [Visual Basic], Mod operator
- modulus operator [Visual Basic], Visual Basic
- Mod operator [Visual Basic]
- operators [Visual Basic], division
- arithmetic operators [Visual Basic], Mod
- math operators [Visual Basic]
ms.assetid: 6ff7e40e-cec8-4c77-bff6-8ddd2791c25b
ms.openlocfilehash: b7552550d4b0496d6ad7ee76a7327054d544b874
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350919"
---
# <a name="mod-operator-visual-basic"></a><span data-ttu-id="a4a9e-102">Mod operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a4a9e-102">Mod operator (Visual Basic)</span></span>

<span data-ttu-id="a4a9e-103">Divides two numbers and returns only the remainder.</span><span class="sxs-lookup"><span data-stu-id="a4a9e-103">Divides two numbers and returns only the remainder.</span></span>

## <a name="syntax"></a><span data-ttu-id="a4a9e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a4a9e-104">Syntax</span></span>

```vb
result = number1 Mod number2
```

## <a name="parts"></a><span data-ttu-id="a4a9e-105">Composants</span><span class="sxs-lookup"><span data-stu-id="a4a9e-105">Parts</span></span>

`result` \
<span data-ttu-id="a4a9e-106">Requis.</span><span class="sxs-lookup"><span data-stu-id="a4a9e-106">Required.</span></span> <span data-ttu-id="a4a9e-107">Any numeric variable or property.</span><span class="sxs-lookup"><span data-stu-id="a4a9e-107">Any numeric variable or property.</span></span>

`number1` \
<span data-ttu-id="a4a9e-108">Requis.</span><span class="sxs-lookup"><span data-stu-id="a4a9e-108">Required.</span></span> <span data-ttu-id="a4a9e-109">Toute expression numérique.</span><span class="sxs-lookup"><span data-stu-id="a4a9e-109">Any numeric expression.</span></span>

`number2` \
<span data-ttu-id="a4a9e-110">Requis.</span><span class="sxs-lookup"><span data-stu-id="a4a9e-110">Required.</span></span> <span data-ttu-id="a4a9e-111">Toute expression numérique.</span><span class="sxs-lookup"><span data-stu-id="a4a9e-111">Any numeric expression.</span></span>

## <a name="supported-types"></a><span data-ttu-id="a4a9e-112">Supported types</span><span class="sxs-lookup"><span data-stu-id="a4a9e-112">Supported types</span></span>

<span data-ttu-id="a4a9e-113">tous les types numériques</span><span class="sxs-lookup"><span data-stu-id="a4a9e-113">All numeric types.</span></span> <span data-ttu-id="a4a9e-114">This includes the unsigned and floating-point types and `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="a4a9e-114">This includes the unsigned and floating-point types and `Decimal`.</span></span>

## <a name="result"></a><span data-ttu-id="a4a9e-115">Résultat</span><span class="sxs-lookup"><span data-stu-id="a4a9e-115">Result</span></span>

<span data-ttu-id="a4a9e-116">The result is the remainder after `number1` is divided by `number2`.</span><span class="sxs-lookup"><span data-stu-id="a4a9e-116">The result is the remainder after `number1` is divided by `number2`.</span></span> <span data-ttu-id="a4a9e-117">For example, the expression `14 Mod 4` evaluates to 2.</span><span class="sxs-lookup"><span data-stu-id="a4a9e-117">For example, the expression `14 Mod 4` evaluates to 2.</span></span>

> [!NOTE]
> <span data-ttu-id="a4a9e-118">There is a difference between *remainder* and *modulus* in mathematics, with different results for negative numbers.</span><span class="sxs-lookup"><span data-stu-id="a4a9e-118">There is a difference between *remainder* and *modulus* in mathematics, with different results for negative numbers.</span></span> <span data-ttu-id="a4a9e-119">The `Mod` operator in Visual Basic, the .NET Framework `op_Modulus` operator, and the underlying [rem](<xref:System.Reflection.Emit.OpCodes.Rem>) IL instruction all perform a remainder operation.</span><span class="sxs-lookup"><span data-stu-id="a4a9e-119">The `Mod` operator in Visual Basic, the .NET Framework `op_Modulus` operator, and the underlying [rem](<xref:System.Reflection.Emit.OpCodes.Rem>) IL instruction all perform a remainder operation.</span></span>

<span data-ttu-id="a4a9e-120">The result of a `Mod` operation retains the sign of the dividend, `number1`, and so it may be positive or negative.</span><span class="sxs-lookup"><span data-stu-id="a4a9e-120">The result of a `Mod` operation retains the sign of the dividend, `number1`, and so it may be positive or negative.</span></span> <span data-ttu-id="a4a9e-121">The result is always in the range (-`number2`, `number2`), exclusive.</span><span class="sxs-lookup"><span data-stu-id="a4a9e-121">The result is always in the range (-`number2`, `number2`), exclusive.</span></span> <span data-ttu-id="a4a9e-122">Exemple :</span><span class="sxs-lookup"><span data-stu-id="a4a9e-122">For example:</span></span>

```vb
Public Module Example
   Public Sub Main()
      Console.WriteLine($" 8 Mod  3 = {8 Mod 3}")
      Console.WriteLine($"-8 Mod  3 = {-8 Mod 3}")
      Console.WriteLine($" 8 Mod -3 = {8 Mod -3}")
      Console.WriteLine($"-8 Mod -3 = {-8 Mod -3}")
   End Sub
End Module
' The example displays the following output:
'       8 Mod  3 = 2
'      -8 Mod  3 = -2
'       8 Mod -3 = 2
'      -8 Mod -3 = -2
```

## <a name="remarks"></a><span data-ttu-id="a4a9e-123">Notes</span><span class="sxs-lookup"><span data-stu-id="a4a9e-123">Remarks</span></span>

<span data-ttu-id="a4a9e-124">If either `number1` or `number2` is a floating-point value, the floating-point remainder of the division is returned.</span><span class="sxs-lookup"><span data-stu-id="a4a9e-124">If either `number1` or `number2` is a floating-point value, the floating-point remainder of the division is returned.</span></span> <span data-ttu-id="a4a9e-125">The data type of the result is the smallest data type that can hold all possible values that result from division with the data types of `number1` and `number2`.</span><span class="sxs-lookup"><span data-stu-id="a4a9e-125">The data type of the result is the smallest data type that can hold all possible values that result from division with the data types of `number1` and `number2`.</span></span>

<span data-ttu-id="a4a9e-126">If `number1` or `number2` evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md), it is treated as zero.</span><span class="sxs-lookup"><span data-stu-id="a4a9e-126">If `number1` or `number2` evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md), it is treated as zero.</span></span>

<span data-ttu-id="a4a9e-127">Related operators include the following:</span><span class="sxs-lookup"><span data-stu-id="a4a9e-127">Related operators include the following:</span></span>

- <span data-ttu-id="a4a9e-128">The [\ Operator (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md) returns the integer quotient of a division.</span><span class="sxs-lookup"><span data-stu-id="a4a9e-128">The [\ Operator (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md) returns the integer quotient of a division.</span></span> <span data-ttu-id="a4a9e-129">For example, the expression `14 \ 4` evaluates to 3.</span><span class="sxs-lookup"><span data-stu-id="a4a9e-129">For example, the expression `14 \ 4` evaluates to 3.</span></span>

- <span data-ttu-id="a4a9e-130">The [/ Operator (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) returns the full quotient, including the remainder, as a floating-point number.</span><span class="sxs-lookup"><span data-stu-id="a4a9e-130">The [/ Operator (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) returns the full quotient, including the remainder, as a floating-point number.</span></span> <span data-ttu-id="a4a9e-131">For example, the expression `14 / 4` evaluates to 3.5.</span><span class="sxs-lookup"><span data-stu-id="a4a9e-131">For example, the expression `14 / 4` evaluates to 3.5.</span></span>

## <a name="attempted-division-by-zero"></a><span data-ttu-id="a4a9e-132">Attempted division by zero</span><span class="sxs-lookup"><span data-stu-id="a4a9e-132">Attempted division by zero</span></span>

<span data-ttu-id="a4a9e-133">If `number2` evaluates to zero, the behavior of the `Mod` operator depends on the data type of the operands:</span><span class="sxs-lookup"><span data-stu-id="a4a9e-133">If `number2` evaluates to zero, the behavior of the `Mod` operator depends on the data type of the operands:</span></span>

- <span data-ttu-id="a4a9e-134">An integral division throws a <xref:System.DivideByZeroException> exception if `number2` cannot be determined in compile-time and generates a compile-time error `BC30542 Division by zero occurred while evaluating this expression` if `number2` is evaluated to zero at compile-time.</span><span class="sxs-lookup"><span data-stu-id="a4a9e-134">An integral division throws a <xref:System.DivideByZeroException> exception if `number2` cannot be determined in compile-time and generates a compile-time error `BC30542 Division by zero occurred while evaluating this expression` if `number2` is evaluated to zero at compile-time.</span></span>
- <span data-ttu-id="a4a9e-135">A floating-point division returns <xref:System.Double.NaN?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a4a9e-135">A floating-point division returns <xref:System.Double.NaN?displayProperty=nameWithType>.</span></span>

## <a name="equivalent-formula"></a><span data-ttu-id="a4a9e-136">Equivalent formula</span><span class="sxs-lookup"><span data-stu-id="a4a9e-136">Equivalent formula</span></span>

<span data-ttu-id="a4a9e-137">The expression `a Mod b` is equivalent to either of the following formulas:</span><span class="sxs-lookup"><span data-stu-id="a4a9e-137">The expression `a Mod b` is equivalent to either of the following formulas:</span></span>

`a - (b * (a \ b))`

`a - (b * Fix(a / b))`

## <a name="floating-point-imprecision"></a><span data-ttu-id="a4a9e-138">Floating-point imprecision</span><span class="sxs-lookup"><span data-stu-id="a4a9e-138">Floating-point imprecision</span></span>

<span data-ttu-id="a4a9e-139">When you work with floating-point numbers, remember that they do not always have a precise decimal representation in memory.</span><span class="sxs-lookup"><span data-stu-id="a4a9e-139">When you work with floating-point numbers, remember that they do not always have a precise decimal representation in memory.</span></span> <span data-ttu-id="a4a9e-140">This can lead to unexpected results from certain operations, such as value comparison and the `Mod` operator.</span><span class="sxs-lookup"><span data-stu-id="a4a9e-140">This can lead to unexpected results from certain operations, such as value comparison and the `Mod` operator.</span></span> <span data-ttu-id="a4a9e-141">For more information, see [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="a4a9e-141">For more information, see [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span></span>

## <a name="overloading"></a><span data-ttu-id="a4a9e-142">Surcharge</span><span class="sxs-lookup"><span data-stu-id="a4a9e-142">Overloading</span></span>

<span data-ttu-id="a4a9e-143">The `Mod` operator can be *overloaded*, which means that a class or structure can redefine its behavior.</span><span class="sxs-lookup"><span data-stu-id="a4a9e-143">The `Mod` operator can be *overloaded*, which means that a class or structure can redefine its behavior.</span></span> <span data-ttu-id="a4a9e-144">If your code applies `Mod` to an instance of a class or structure that includes such an overload, be sure you understand its redefined behavior.</span><span class="sxs-lookup"><span data-stu-id="a4a9e-144">If your code applies `Mod` to an instance of a class or structure that includes such an overload, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="a4a9e-145">Pour plus d'informations, consultez [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="a4a9e-145">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>

## <a name="example"></a><span data-ttu-id="a4a9e-146">Exemple</span><span class="sxs-lookup"><span data-stu-id="a4a9e-146">Example</span></span>

<span data-ttu-id="a4a9e-147">The following example uses the `Mod` operator to divide two numbers and return only the remainder.</span><span class="sxs-lookup"><span data-stu-id="a4a9e-147">The following example uses the `Mod` operator to divide two numbers and return only the remainder.</span></span> <span data-ttu-id="a4a9e-148">If either number is a floating-point number, the result is a floating-point number that represents the remainder.</span><span class="sxs-lookup"><span data-stu-id="a4a9e-148">If either number is a floating-point number, the result is a floating-point number that represents the remainder.</span></span>

[!code-vb[VbVbalrOperators#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#31)]

## <a name="example"></a><span data-ttu-id="a4a9e-149">Exemple</span><span class="sxs-lookup"><span data-stu-id="a4a9e-149">Example</span></span>

<span data-ttu-id="a4a9e-150">The following example demonstrates the potential imprecision of floating-point operands.</span><span class="sxs-lookup"><span data-stu-id="a4a9e-150">The following example demonstrates the potential imprecision of floating-point operands.</span></span> <span data-ttu-id="a4a9e-151">In the first statement, the operands are `Double`, and 0.2 is an infinitely repeating binary fraction with a stored value of 0.20000000000000001.</span><span class="sxs-lookup"><span data-stu-id="a4a9e-151">In the first statement, the operands are `Double`, and 0.2 is an infinitely repeating binary fraction with a stored value of 0.20000000000000001.</span></span> <span data-ttu-id="a4a9e-152">In the second statement, the literal type character `D` forces both operands to `Decimal`, and 0.2 has a precise representation.</span><span class="sxs-lookup"><span data-stu-id="a4a9e-152">In the second statement, the literal type character `D` forces both operands to `Decimal`, and 0.2 has a precise representation.</span></span>

[!code-vb[VbVbalrOperators#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#32)]

## <a name="see-also"></a><span data-ttu-id="a4a9e-153">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a4a9e-153">See also</span></span>

- <xref:Microsoft.VisualBasic.Conversion.Int%2A>
- <xref:Microsoft.VisualBasic.Conversion.Fix%2A>
- [<span data-ttu-id="a4a9e-154">Opérateurs arithmétiques</span><span class="sxs-lookup"><span data-stu-id="a4a9e-154">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="a4a9e-155">Priorité des opérateurs en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a4a9e-155">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="a4a9e-156">Opérateurs répertoriés par fonctionnalité</span><span class="sxs-lookup"><span data-stu-id="a4a9e-156">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="a4a9e-157">Dépannage des types de données</span><span class="sxs-lookup"><span data-stu-id="a4a9e-157">Troubleshooting Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [<span data-ttu-id="a4a9e-158">Arithmetic Operators in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a4a9e-158">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [<span data-ttu-id="a4a9e-159">\ Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a4a9e-159">\ Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/integer-division-operator.md)
