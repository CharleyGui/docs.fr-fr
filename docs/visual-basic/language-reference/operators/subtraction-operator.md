---
title: '- opérateur'
ms.date: 07/20/2015
f1_keywords:
- vb.Negate
- vb.-
helpviewer_keywords:
- operator [Visual Basic]
- operators [Visual Basic], subtraction
- operators [Visual Basic], difference
- negation operator [Visual Basic]
- operators [Visual Basic], arithmetic
- subtraction operator [Visual Basic], syntax
- arithmetic operators [Visual Basic], subtraction
- difference operator [Visual Basic]
- math operators [Visual Basic]
- operators [Visual Basic], negation
- minus operator [Visual Basic]
ms.assetid: bff2c368-662d-4c92-ac87-1d9bdfd3426a
ms.openlocfilehash: 9687c366c5b23693c05ab5c6b34f50c04131dfda
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348224"
---
# <a name="--operator-visual-basic"></a><span data-ttu-id="669d9-102">-, opérateur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="669d9-102">- Operator (Visual Basic)</span></span>
<span data-ttu-id="669d9-103">Returns the difference between two numeric expressions or the negative value of a numeric expression.</span><span class="sxs-lookup"><span data-stu-id="669d9-103">Returns the difference between two numeric expressions or the negative value of a numeric expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="669d9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="669d9-104">Syntax</span></span>  
  
```vb  
expression1 – expression2
```
  
<span data-ttu-id="669d9-105">or</span><span class="sxs-lookup"><span data-stu-id="669d9-105">or</span></span>

```vb  
–expression1  
```  
  
## <a name="parts"></a><span data-ttu-id="669d9-106">Composants</span><span class="sxs-lookup"><span data-stu-id="669d9-106">Parts</span></span>  
 `expression1`  
 <span data-ttu-id="669d9-107">Requis.</span><span class="sxs-lookup"><span data-stu-id="669d9-107">Required.</span></span> <span data-ttu-id="669d9-108">Toute expression numérique.</span><span class="sxs-lookup"><span data-stu-id="669d9-108">Any numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="669d9-109">Required unless the `–` operator is calculating a negative value.</span><span class="sxs-lookup"><span data-stu-id="669d9-109">Required unless the `–` operator is calculating a negative value.</span></span> <span data-ttu-id="669d9-110">Toute expression numérique.</span><span class="sxs-lookup"><span data-stu-id="669d9-110">Any numeric expression.</span></span>  
  
## <a name="result"></a><span data-ttu-id="669d9-111">Résultat</span><span class="sxs-lookup"><span data-stu-id="669d9-111">Result</span></span>  
 <span data-ttu-id="669d9-112">The result is the difference between `expression1` and `expression2`, or the negated value of `expression1`.</span><span class="sxs-lookup"><span data-stu-id="669d9-112">The result is the difference between `expression1` and `expression2`, or the negated value of `expression1`.</span></span>  
  
 <span data-ttu-id="669d9-113">The result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span><span class="sxs-lookup"><span data-stu-id="669d9-113">The result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="669d9-114">See the "Integer Arithmetic" tables in [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span><span class="sxs-lookup"><span data-stu-id="669d9-114">See the "Integer Arithmetic" tables in [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="669d9-115">Types pris en charge</span><span class="sxs-lookup"><span data-stu-id="669d9-115">Supported Types</span></span>  
 <span data-ttu-id="669d9-116">tous les types numériques</span><span class="sxs-lookup"><span data-stu-id="669d9-116">All numeric types.</span></span> <span data-ttu-id="669d9-117">This includes the unsigned and floating-point types and `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="669d9-117">This includes the unsigned and floating-point types and `Decimal`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="669d9-118">Notes</span><span class="sxs-lookup"><span data-stu-id="669d9-118">Remarks</span></span>  
 <span data-ttu-id="669d9-119">In the first usage shown in the syntax shown previously, the `–` operator is the *binary* arithmetic subtraction operator for the difference between two numeric expressions.</span><span class="sxs-lookup"><span data-stu-id="669d9-119">In the first usage shown in the syntax shown previously, the `–` operator is the *binary* arithmetic subtraction operator for the difference between two numeric expressions.</span></span>  
  
 <span data-ttu-id="669d9-120">In the second usage shown in the syntax shown previously, the `–` operator is the *unary* negation operator for the negative value of an expression.</span><span class="sxs-lookup"><span data-stu-id="669d9-120">In the second usage shown in the syntax shown previously, the `–` operator is the *unary* negation operator for the negative value of an expression.</span></span> <span data-ttu-id="669d9-121">In this sense, the negation consists of reversing the sign of `expression1` so that the result is positive if `expression1` is negative.</span><span class="sxs-lookup"><span data-stu-id="669d9-121">In this sense, the negation consists of reversing the sign of `expression1` so that the result is positive if `expression1` is negative.</span></span>  
  
 <span data-ttu-id="669d9-122">If either expression evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md), the `–` operator treats it as zero.</span><span class="sxs-lookup"><span data-stu-id="669d9-122">If either expression evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md), the `–` operator treats it as zero.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="669d9-123">The `–` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span><span class="sxs-lookup"><span data-stu-id="669d9-123">The `–` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="669d9-124">If your code uses this operator on such a class or structure, make sure that you understand its redefined behavior.</span><span class="sxs-lookup"><span data-stu-id="669d9-124">If your code uses this operator on such a class or structure, make sure that you understand its redefined behavior.</span></span> <span data-ttu-id="669d9-125">Pour plus d'informations, consultez [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="669d9-125">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="669d9-126">Exemple</span><span class="sxs-lookup"><span data-stu-id="669d9-126">Example</span></span>  
 <span data-ttu-id="669d9-127">The following example uses the `–` operator to calculate and return the difference between two numbers, and then to negate a number.</span><span class="sxs-lookup"><span data-stu-id="669d9-127">The following example uses the `–` operator to calculate and return the difference between two numbers, and then to negate a number.</span></span>  
  
 [!code-vb[VbVbalrOperators#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#10)]  
  
 <span data-ttu-id="669d9-128">Following the execution of these statements, `binaryResult` contains 124.45 and `unaryResult` contains –334.90.</span><span class="sxs-lookup"><span data-stu-id="669d9-128">Following the execution of these statements, `binaryResult` contains 124.45 and `unaryResult` contains –334.90.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="669d9-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="669d9-129">See also</span></span>

- [<span data-ttu-id="669d9-130">-= Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="669d9-130">-= Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/subtraction-assignment-operator.md)
- [<span data-ttu-id="669d9-131">Opérateurs arithmétiques</span><span class="sxs-lookup"><span data-stu-id="669d9-131">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="669d9-132">Priorité des opérateurs en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="669d9-132">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="669d9-133">Opérateurs répertoriés par fonctionnalité</span><span class="sxs-lookup"><span data-stu-id="669d9-133">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="669d9-134">Arithmetic Operators in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="669d9-134">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
