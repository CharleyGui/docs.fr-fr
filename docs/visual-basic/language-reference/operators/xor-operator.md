---
title: Xor, opérateur
ms.date: 07/20/2015
f1_keywords:
- vb.Xor
helpviewer_keywords:
- exclusive OR operator [Visual Basic]
- logical exclusion
- operators [Visual Basic], exclusive or
- exclusion operator [Visual Basic]
- operators [Visual Basic], bitwise
- bitwise operators [Visual Basic], XOR operator
- Xor operator [Visual Basic]
- Xor keyword [Visual Basic]
- bitwise comparison [Visual Basic]
ms.assetid: 036000a9-3934-4e7f-a9d0-a816de3d84a6
ms.openlocfilehash: c5c7ec87bc173f724f8c670395bc3b0458444df6
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74335397"
---
# <a name="xor-operator-visual-basic"></a><span data-ttu-id="09aae-102">Xor, opérateur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="09aae-102">Xor Operator (Visual Basic)</span></span>
<span data-ttu-id="09aae-103">Performs a logical exclusion on two `Boolean` expressions, or a bitwise exclusion on two numeric expressions.</span><span class="sxs-lookup"><span data-stu-id="09aae-103">Performs a logical exclusion on two `Boolean` expressions, or a bitwise exclusion on two numeric expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09aae-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="09aae-104">Syntax</span></span>  
  
```vb  
result = expression1 Xor expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="09aae-105">Composants</span><span class="sxs-lookup"><span data-stu-id="09aae-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="09aae-106">Requis.</span><span class="sxs-lookup"><span data-stu-id="09aae-106">Required.</span></span> <span data-ttu-id="09aae-107">Any `Boolean` or numeric variable.</span><span class="sxs-lookup"><span data-stu-id="09aae-107">Any `Boolean` or numeric variable.</span></span> <span data-ttu-id="09aae-108">For Boolean comparison, `result` is the logical exclusion (exclusive logical disjunction) of two `Boolean` values.</span><span class="sxs-lookup"><span data-stu-id="09aae-108">For Boolean comparison, `result` is the logical exclusion (exclusive logical disjunction) of two `Boolean` values.</span></span> <span data-ttu-id="09aae-109">For bitwise operations, `result` is a numeric value that represents the bitwise exclusion (exclusive bitwise disjunction) of two numeric bit patterns.</span><span class="sxs-lookup"><span data-stu-id="09aae-109">For bitwise operations, `result` is a numeric value that represents the bitwise exclusion (exclusive bitwise disjunction) of two numeric bit patterns.</span></span>  
  
 `expression1`  
 <span data-ttu-id="09aae-110">Requis.</span><span class="sxs-lookup"><span data-stu-id="09aae-110">Required.</span></span> <span data-ttu-id="09aae-111">Any `Boolean` or numeric expression.</span><span class="sxs-lookup"><span data-stu-id="09aae-111">Any `Boolean` or numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="09aae-112">Requis.</span><span class="sxs-lookup"><span data-stu-id="09aae-112">Required.</span></span> <span data-ttu-id="09aae-113">Any `Boolean` or numeric expression.</span><span class="sxs-lookup"><span data-stu-id="09aae-113">Any `Boolean` or numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="09aae-114">Notes</span><span class="sxs-lookup"><span data-stu-id="09aae-114">Remarks</span></span>  
 <span data-ttu-id="09aae-115">For Boolean comparison, `result` is `True` if and only if exactly one of `expression1` and `expression2` evaluates to `True`.</span><span class="sxs-lookup"><span data-stu-id="09aae-115">For Boolean comparison, `result` is `True` if and only if exactly one of `expression1` and `expression2` evaluates to `True`.</span></span> <span data-ttu-id="09aae-116">That is, if and only if `expression1` and `expression2` evaluate to opposite `Boolean` values.</span><span class="sxs-lookup"><span data-stu-id="09aae-116">That is, if and only if `expression1` and `expression2` evaluate to opposite `Boolean` values.</span></span> <span data-ttu-id="09aae-117">The following table illustrates how `result` is determined.</span><span class="sxs-lookup"><span data-stu-id="09aae-117">The following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="09aae-118">If `expression1` is</span><span class="sxs-lookup"><span data-stu-id="09aae-118">If `expression1` is</span></span>|<span data-ttu-id="09aae-119">And `expression2` is</span><span class="sxs-lookup"><span data-stu-id="09aae-119">And `expression2` is</span></span>|<span data-ttu-id="09aae-120">The value of `result` is</span><span class="sxs-lookup"><span data-stu-id="09aae-120">The value of `result` is</span></span>|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`False`|  
|`True`|`False`|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
> <span data-ttu-id="09aae-121">In a Boolean comparison, the `Xor` operator always evaluates both expressions, which could include making procedure calls.</span><span class="sxs-lookup"><span data-stu-id="09aae-121">In a Boolean comparison, the `Xor` operator always evaluates both expressions, which could include making procedure calls.</span></span> <span data-ttu-id="09aae-122">There is no short-circuiting counterpart to `Xor`, because the result always depends on both operands.</span><span class="sxs-lookup"><span data-stu-id="09aae-122">There is no short-circuiting counterpart to `Xor`, because the result always depends on both operands.</span></span> <span data-ttu-id="09aae-123">For *short-circuiting* logical operators, see [AndAlso Operator](../../../visual-basic/language-reference/operators/andalso-operator.md) and [OrElse Operator](../../../visual-basic/language-reference/operators/orelse-operator.md).</span><span class="sxs-lookup"><span data-stu-id="09aae-123">For *short-circuiting* logical operators, see [AndAlso Operator](../../../visual-basic/language-reference/operators/andalso-operator.md) and [OrElse Operator](../../../visual-basic/language-reference/operators/orelse-operator.md).</span></span>  
  
 <span data-ttu-id="09aae-124">For bitwise operations, the `Xor` operator performs a bitwise comparison of identically positioned bits in two numeric expressions and sets the corresponding bit in `result` according to the following table.</span><span class="sxs-lookup"><span data-stu-id="09aae-124">For bitwise operations, the `Xor` operator performs a bitwise comparison of identically positioned bits in two numeric expressions and sets the corresponding bit in `result` according to the following table.</span></span>  
  
|<span data-ttu-id="09aae-125">If bit in `expression1` is</span><span class="sxs-lookup"><span data-stu-id="09aae-125">If bit in `expression1` is</span></span>|<span data-ttu-id="09aae-126">And bit in `expression2` is</span><span class="sxs-lookup"><span data-stu-id="09aae-126">And bit in `expression2` is</span></span>|<span data-ttu-id="09aae-127">The bit in `result` is</span><span class="sxs-lookup"><span data-stu-id="09aae-127">The bit in `result` is</span></span>|  
|--------------------------------|---------------------------------|----------------------------|  
|<span data-ttu-id="09aae-128">1</span><span class="sxs-lookup"><span data-stu-id="09aae-128">1</span></span>|<span data-ttu-id="09aae-129">1</span><span class="sxs-lookup"><span data-stu-id="09aae-129">1</span></span>|<span data-ttu-id="09aae-130">0</span><span class="sxs-lookup"><span data-stu-id="09aae-130">0</span></span>|  
|<span data-ttu-id="09aae-131">1</span><span class="sxs-lookup"><span data-stu-id="09aae-131">1</span></span>|<span data-ttu-id="09aae-132">0</span><span class="sxs-lookup"><span data-stu-id="09aae-132">0</span></span>|<span data-ttu-id="09aae-133">1</span><span class="sxs-lookup"><span data-stu-id="09aae-133">1</span></span>|  
|<span data-ttu-id="09aae-134">0</span><span class="sxs-lookup"><span data-stu-id="09aae-134">0</span></span>|<span data-ttu-id="09aae-135">1</span><span class="sxs-lookup"><span data-stu-id="09aae-135">1</span></span>|<span data-ttu-id="09aae-136">1</span><span class="sxs-lookup"><span data-stu-id="09aae-136">1</span></span>|  
|<span data-ttu-id="09aae-137">0</span><span class="sxs-lookup"><span data-stu-id="09aae-137">0</span></span>|<span data-ttu-id="09aae-138">0</span><span class="sxs-lookup"><span data-stu-id="09aae-138">0</span></span>|<span data-ttu-id="09aae-139">0</span><span class="sxs-lookup"><span data-stu-id="09aae-139">0</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="09aae-140">Since the logical and bitwise operators have a lower precedence than other arithmetic and relational operators, any bitwise operations should be enclosed in parentheses to ensure accurate execution.</span><span class="sxs-lookup"><span data-stu-id="09aae-140">Since the logical and bitwise operators have a lower precedence than other arithmetic and relational operators, any bitwise operations should be enclosed in parentheses to ensure accurate execution.</span></span>  
  
 <span data-ttu-id="09aae-141">For example, 5 `Xor` 3 is 6.</span><span class="sxs-lookup"><span data-stu-id="09aae-141">For example, 5 `Xor` 3 is 6.</span></span> <span data-ttu-id="09aae-142">To see why this is so, convert 5 and 3 to their binary representations, 101 and 011.</span><span class="sxs-lookup"><span data-stu-id="09aae-142">To see why this is so, convert 5 and 3 to their binary representations, 101 and 011.</span></span> <span data-ttu-id="09aae-143">Then use the previous table to determine that 101 Xor 011 is 110, which is the binary representation of the decimal number 6.</span><span class="sxs-lookup"><span data-stu-id="09aae-143">Then use the previous table to determine that 101 Xor 011 is 110, which is the binary representation of the decimal number 6.</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="09aae-144">Types de données</span><span class="sxs-lookup"><span data-stu-id="09aae-144">Data Types</span></span>  
 <span data-ttu-id="09aae-145">If the operands consist of one `Boolean` expression and one numeric expression, Visual Basic converts the `Boolean` expression to a numeric value (–1 for `True` and 0 for `False`) and performs a bitwise operation.</span><span class="sxs-lookup"><span data-stu-id="09aae-145">If the operands consist of one `Boolean` expression and one numeric expression, Visual Basic converts the `Boolean` expression to a numeric value (–1 for `True` and 0 for `False`) and performs a bitwise operation.</span></span>  
  
 <span data-ttu-id="09aae-146">For a `Boolean` comparison, the data type of the result is `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="09aae-146">For a `Boolean` comparison, the data type of the result is `Boolean`.</span></span> <span data-ttu-id="09aae-147">For a bitwise comparison, the result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span><span class="sxs-lookup"><span data-stu-id="09aae-147">For a bitwise comparison, the result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="09aae-148">See the "Relational and Bitwise Comparisons" table in [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span><span class="sxs-lookup"><span data-stu-id="09aae-148">See the "Relational and Bitwise Comparisons" table in [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="09aae-149">Surcharge</span><span class="sxs-lookup"><span data-stu-id="09aae-149">Overloading</span></span>  
 <span data-ttu-id="09aae-150">The `Xor` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span><span class="sxs-lookup"><span data-stu-id="09aae-150">The `Xor` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="09aae-151">If your code uses this operator on such a class or structure, make sure you understand its redefined behavior.</span><span class="sxs-lookup"><span data-stu-id="09aae-151">If your code uses this operator on such a class or structure, make sure you understand its redefined behavior.</span></span> <span data-ttu-id="09aae-152">Pour plus d'informations, consultez [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="09aae-152">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="09aae-153">Exemple</span><span class="sxs-lookup"><span data-stu-id="09aae-153">Example</span></span>  
 <span data-ttu-id="09aae-154">The following example uses the `Xor` operator to perform logical exclusion (exclusive logical disjunction) on two expressions.</span><span class="sxs-lookup"><span data-stu-id="09aae-154">The following example uses the `Xor` operator to perform logical exclusion (exclusive logical disjunction) on two expressions.</span></span> <span data-ttu-id="09aae-155">The result is a `Boolean` value that represents whether exactly one of the expressions is `True`.</span><span class="sxs-lookup"><span data-stu-id="09aae-155">The result is a `Boolean` value that represents whether exactly one of the expressions is `True`.</span></span>  
  
 [!code-vb[VbVbalrOperators#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#40)]  
  
 <span data-ttu-id="09aae-156">The previous example produces results of `False`, `True`, and `False`, respectively.</span><span class="sxs-lookup"><span data-stu-id="09aae-156">The previous example produces results of `False`, `True`, and `False`, respectively.</span></span>  
  
## <a name="example"></a><span data-ttu-id="09aae-157">Exemple</span><span class="sxs-lookup"><span data-stu-id="09aae-157">Example</span></span>  
 <span data-ttu-id="09aae-158">The following example uses the `Xor` operator to perform logical exclusion (exclusive logical disjunction) on the individual bits of two numeric expressions.</span><span class="sxs-lookup"><span data-stu-id="09aae-158">The following example uses the `Xor` operator to perform logical exclusion (exclusive logical disjunction) on the individual bits of two numeric expressions.</span></span> <span data-ttu-id="09aae-159">The bit in the result pattern is set if exactly one of the corresponding bits in the operands is set to 1.</span><span class="sxs-lookup"><span data-stu-id="09aae-159">The bit in the result pattern is set if exactly one of the corresponding bits in the operands is set to 1.</span></span>  
  
 [!code-vb[VbVbalrOperators#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#41)]  
  
 <span data-ttu-id="09aae-160">The previous example produces results of 2, 12, and 14, respectively.</span><span class="sxs-lookup"><span data-stu-id="09aae-160">The previous example produces results of 2, 12, and 14, respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09aae-161">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="09aae-161">See also</span></span>

- [<span data-ttu-id="09aae-162">Logical/Bitwise Operators (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="09aae-162">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [<span data-ttu-id="09aae-163">Priorité des opérateurs en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="09aae-163">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="09aae-164">Opérateurs répertoriés par fonctionnalité</span><span class="sxs-lookup"><span data-stu-id="09aae-164">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="09aae-165">Logical and Bitwise Operators in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="09aae-165">Logical and Bitwise Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
