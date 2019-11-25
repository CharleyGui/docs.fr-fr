---
title: Not, opérateur
ms.date: 07/20/2015
f1_keywords:
- vb.Not
helpviewer_keywords:
- Boolean expressions, negating
- operators [Visual Basic], bitwise
- negation operator [Visual Basic]
- inverse bit values in variables [Visual Basic]
- bitwise operators [Visual Basic], NOT operator
- bitwise comparison [Visual Basic]
- Not operator [Visual Basic]
- logical negation
- operators [Visual Basic], negation
ms.assetid: 8f2ea83c-d2ed-480a-a474-3042a1cad9b5
ms.openlocfilehash: 08b091ccf6c50438b5ad9d6c445510112abe7418
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348308"
---
# <a name="not-operator-visual-basic"></a><span data-ttu-id="1e423-102">Not, opérateur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1e423-102">Not Operator (Visual Basic)</span></span>
<span data-ttu-id="1e423-103">Performs logical negation on a `Boolean` expression, or bitwise negation on a numeric expression.</span><span class="sxs-lookup"><span data-stu-id="1e423-103">Performs logical negation on a `Boolean` expression, or bitwise negation on a numeric expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e423-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1e423-104">Syntax</span></span>  
  
```vb  
result = Not expression  
```  
  
## <a name="parts"></a><span data-ttu-id="1e423-105">Composants</span><span class="sxs-lookup"><span data-stu-id="1e423-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="1e423-106">Requis.</span><span class="sxs-lookup"><span data-stu-id="1e423-106">Required.</span></span> <span data-ttu-id="1e423-107">Any `Boolean` or numeric expression.</span><span class="sxs-lookup"><span data-stu-id="1e423-107">Any `Boolean` or numeric expression.</span></span>  
  
 `expression`  
 <span data-ttu-id="1e423-108">Requis.</span><span class="sxs-lookup"><span data-stu-id="1e423-108">Required.</span></span> <span data-ttu-id="1e423-109">Any `Boolean` or numeric expression.</span><span class="sxs-lookup"><span data-stu-id="1e423-109">Any `Boolean` or numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1e423-110">Notes</span><span class="sxs-lookup"><span data-stu-id="1e423-110">Remarks</span></span>  
 <span data-ttu-id="1e423-111">For `Boolean` expressions, the following table illustrates how `result` is determined.</span><span class="sxs-lookup"><span data-stu-id="1e423-111">For `Boolean` expressions, the following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="1e423-112">If `expression` is</span><span class="sxs-lookup"><span data-stu-id="1e423-112">If `expression` is</span></span>|<span data-ttu-id="1e423-113">The value of `result` is</span><span class="sxs-lookup"><span data-stu-id="1e423-113">The value of `result` is</span></span>|  
|------------------------|------------------------------|  
|`True`|`False`|  
|`False`|`True`|  
  
 <span data-ttu-id="1e423-114">For numeric expressions, the `Not` operator inverts the bit values of any numeric expression and sets the corresponding bit in `result` according to the following table.</span><span class="sxs-lookup"><span data-stu-id="1e423-114">For numeric expressions, the `Not` operator inverts the bit values of any numeric expression and sets the corresponding bit in `result` according to the following table.</span></span>  
  
|<span data-ttu-id="1e423-115">If bit in `expression` is</span><span class="sxs-lookup"><span data-stu-id="1e423-115">If bit in `expression` is</span></span>|<span data-ttu-id="1e423-116">The bit in `result` is</span><span class="sxs-lookup"><span data-stu-id="1e423-116">The bit in `result` is</span></span>|  
|-------------------------------|----------------------------|  
|<span data-ttu-id="1e423-117">1</span><span class="sxs-lookup"><span data-stu-id="1e423-117">1</span></span>|<span data-ttu-id="1e423-118">0</span><span class="sxs-lookup"><span data-stu-id="1e423-118">0</span></span>|  
|<span data-ttu-id="1e423-119">0</span><span class="sxs-lookup"><span data-stu-id="1e423-119">0</span></span>|<span data-ttu-id="1e423-120">1</span><span class="sxs-lookup"><span data-stu-id="1e423-120">1</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="1e423-121">Since the logical and bitwise operators have a lower precedence than other arithmetic and relational operators, any bitwise operations should be enclosed in parentheses to ensure accurate execution.</span><span class="sxs-lookup"><span data-stu-id="1e423-121">Since the logical and bitwise operators have a lower precedence than other arithmetic and relational operators, any bitwise operations should be enclosed in parentheses to ensure accurate execution.</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="1e423-122">Types de données</span><span class="sxs-lookup"><span data-stu-id="1e423-122">Data Types</span></span>  
 <span data-ttu-id="1e423-123">For a Boolean negation, the data type of the result is `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="1e423-123">For a Boolean negation, the data type of the result is `Boolean`.</span></span> <span data-ttu-id="1e423-124">For a bitwise negation, the result data type is the same as that of `expression`.</span><span class="sxs-lookup"><span data-stu-id="1e423-124">For a bitwise negation, the result data type is the same as that of `expression`.</span></span> <span data-ttu-id="1e423-125">However, if expression is `Decimal`, the result is `Long`.</span><span class="sxs-lookup"><span data-stu-id="1e423-125">However, if expression is `Decimal`, the result is `Long`.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="1e423-126">Surcharge</span><span class="sxs-lookup"><span data-stu-id="1e423-126">Overloading</span></span>  
 <span data-ttu-id="1e423-127">The `Not` operator can be *overloaded*, which means that a class or structure can redefine its behavior when its operand has the type of that class or structure.</span><span class="sxs-lookup"><span data-stu-id="1e423-127">The `Not` operator can be *overloaded*, which means that a class or structure can redefine its behavior when its operand has the type of that class or structure.</span></span> <span data-ttu-id="1e423-128">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span><span class="sxs-lookup"><span data-stu-id="1e423-128">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="1e423-129">Pour plus d'informations, consultez [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="1e423-129">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1e423-130">Exemple</span><span class="sxs-lookup"><span data-stu-id="1e423-130">Example</span></span>  
 <span data-ttu-id="1e423-131">The following example uses the `Not` operator to perform logical negation on a `Boolean` expression.</span><span class="sxs-lookup"><span data-stu-id="1e423-131">The following example uses the `Not` operator to perform logical negation on a `Boolean` expression.</span></span> <span data-ttu-id="1e423-132">The result is a `Boolean` value that represents the reverse of the value of the expression.</span><span class="sxs-lookup"><span data-stu-id="1e423-132">The result is a `Boolean` value that represents the reverse of the value of the expression.</span></span>  
  
 [!code-vb[VbVbalrOperators#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#33)]  
  
 <span data-ttu-id="1e423-133">The preceding example produces results of `False` and `True`, respectively.</span><span class="sxs-lookup"><span data-stu-id="1e423-133">The preceding example produces results of `False` and `True`, respectively.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1e423-134">Exemple</span><span class="sxs-lookup"><span data-stu-id="1e423-134">Example</span></span>  
 <span data-ttu-id="1e423-135">The following example uses the `Not` operator to perform logical negation of the individual bits of a numeric expression.</span><span class="sxs-lookup"><span data-stu-id="1e423-135">The following example uses the `Not` operator to perform logical negation of the individual bits of a numeric expression.</span></span> <span data-ttu-id="1e423-136">The bit in the result pattern is set to the reverse of the corresponding bit in the operand pattern, including the sign bit.</span><span class="sxs-lookup"><span data-stu-id="1e423-136">The bit in the result pattern is set to the reverse of the corresponding bit in the operand pattern, including the sign bit.</span></span>  
  
 [!code-vb[VbVbalrOperators#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#34)]  
  
 <span data-ttu-id="1e423-137">The preceding example produces results of –11, –9, and –7, respectively.</span><span class="sxs-lookup"><span data-stu-id="1e423-137">The preceding example produces results of –11, –9, and –7, respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e423-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1e423-138">See also</span></span>

- [<span data-ttu-id="1e423-139">Logical/Bitwise Operators (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1e423-139">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [<span data-ttu-id="1e423-140">Priorité des opérateurs en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1e423-140">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="1e423-141">Opérateurs répertoriés par fonctionnalité</span><span class="sxs-lookup"><span data-stu-id="1e423-141">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="1e423-142">Logical and Bitwise Operators in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1e423-142">Logical and Bitwise Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
