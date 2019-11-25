---
title: "Comment : appeler une procédure d'opérateur"
ms.date: 07/20/2015
helpviewer_keywords:
- operator procedures [Visual Basic], calling
- procedures [Visual Basic], operator
- procedure calls [Visual Basic], operator overloading
- syntax [Visual Basic], Operator procedures
- operators [Visual Basic], overloading
- return values [Visual Basic], Operator procedures
- overloaded operators [Visual Basic], calling
- operator overloading
ms.assetid: 0dce42cc-f0b0-4c14-9f62-018b21f33497
ms.openlocfilehash: a685be7cc3b346b271413e2c29faae5a839313f4
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74340242"
---
# <a name="how-to-call-an-operator-procedure-visual-basic"></a><span data-ttu-id="635c7-102">Comment : appeler une procédure d'opérateur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="635c7-102">How to: Call an Operator Procedure (Visual Basic)</span></span>
<span data-ttu-id="635c7-103">You call an operator procedure by using the operator symbol in an expression.</span><span class="sxs-lookup"><span data-stu-id="635c7-103">You call an operator procedure by using the operator symbol in an expression.</span></span> <span data-ttu-id="635c7-104">In the case of a conversion operator, you call the [CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md) to convert a value from one data type to another.</span><span class="sxs-lookup"><span data-stu-id="635c7-104">In the case of a conversion operator, you call the [CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md) to convert a value from one data type to another.</span></span>  
  
 <span data-ttu-id="635c7-105">You do not call operator procedures explicitly.</span><span class="sxs-lookup"><span data-stu-id="635c7-105">You do not call operator procedures explicitly.</span></span> <span data-ttu-id="635c7-106">You just use the operator, or the `CType` function, in an assignment statement or an expression, the same way you ordinarily use an operator.</span><span class="sxs-lookup"><span data-stu-id="635c7-106">You just use the operator, or the `CType` function, in an assignment statement or an expression, the same way you ordinarily use an operator.</span></span> <span data-ttu-id="635c7-107">Visual Basic makes the call to the operator procedure.</span><span class="sxs-lookup"><span data-stu-id="635c7-107">Visual Basic makes the call to the operator procedure.</span></span>  
  
 <span data-ttu-id="635c7-108">Defining an operator on a class or structure is also called *overloading* the operator.</span><span class="sxs-lookup"><span data-stu-id="635c7-108">Defining an operator on a class or structure is also called *overloading* the operator.</span></span>  
  
### <a name="to-call-an-operator-procedure"></a><span data-ttu-id="635c7-109">To call an operator procedure</span><span class="sxs-lookup"><span data-stu-id="635c7-109">To call an operator procedure</span></span>  
  
1. <span data-ttu-id="635c7-110">Use the operator symbol in an expression in the ordinary way.</span><span class="sxs-lookup"><span data-stu-id="635c7-110">Use the operator symbol in an expression in the ordinary way.</span></span>  
  
2. <span data-ttu-id="635c7-111">Be sure the data types of the operands are appropriate for the operator, and in the correct order.</span><span class="sxs-lookup"><span data-stu-id="635c7-111">Be sure the data types of the operands are appropriate for the operator, and in the correct order.</span></span>  
  
3. <span data-ttu-id="635c7-112">The operator contributes to the value of the expression as expected.</span><span class="sxs-lookup"><span data-stu-id="635c7-112">The operator contributes to the value of the expression as expected.</span></span>  
  
### <a name="to-call-a-conversion-operator-procedure"></a><span data-ttu-id="635c7-113">To call a conversion operator procedure</span><span class="sxs-lookup"><span data-stu-id="635c7-113">To call a conversion operator procedure</span></span>  
  
1. <span data-ttu-id="635c7-114">Use `CType` inside an expression.</span><span class="sxs-lookup"><span data-stu-id="635c7-114">Use `CType` inside an expression.</span></span>  
  
2. <span data-ttu-id="635c7-115">Be sure the data types of the operands are appropriate for the conversion, and in the correct order.</span><span class="sxs-lookup"><span data-stu-id="635c7-115">Be sure the data types of the operands are appropriate for the conversion, and in the correct order.</span></span>  
  
3. <span data-ttu-id="635c7-116">`CType` calls the conversion operator procedure and returns the converted value.</span><span class="sxs-lookup"><span data-stu-id="635c7-116">`CType` calls the conversion operator procedure and returns the converted value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="635c7-117">Exemple</span><span class="sxs-lookup"><span data-stu-id="635c7-117">Example</span></span>  
 <span data-ttu-id="635c7-118">The following example creates two <xref:System.TimeSpan> structures, adds them together, and stores the result in a third <xref:System.TimeSpan> structure.</span><span class="sxs-lookup"><span data-stu-id="635c7-118">The following example creates two <xref:System.TimeSpan> structures, adds them together, and stores the result in a third <xref:System.TimeSpan> structure.</span></span> <span data-ttu-id="635c7-119">The <xref:System.TimeSpan> structure defines operator procedures to overload several standard operators.</span><span class="sxs-lookup"><span data-stu-id="635c7-119">The <xref:System.TimeSpan> structure defines operator procedures to overload several standard operators.</span></span>  
  
 [!code-vb[VbVbcnProcedures#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#29)]  
  
 <span data-ttu-id="635c7-120">Because <xref:System.TimeSpan> overloads the standard `+` operator, the previous example calls an operator procedure when it calculates the value of `combinedSpan`.</span><span class="sxs-lookup"><span data-stu-id="635c7-120">Because <xref:System.TimeSpan> overloads the standard `+` operator, the previous example calls an operator procedure when it calculates the value of `combinedSpan`.</span></span>  
  
 <span data-ttu-id="635c7-121">For an example of calling a conversation operator procedure, see [How to: Use a Class that Defines Operators](./how-to-use-a-class-that-defines-operators.md).</span><span class="sxs-lookup"><span data-stu-id="635c7-121">For an example of calling a conversation operator procedure, see [How to: Use a Class that Defines Operators](./how-to-use-a-class-that-defines-operators.md).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="635c7-122">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="635c7-122">Compiling the Code</span></span>  
 <span data-ttu-id="635c7-123">Be sure the class or structure you are using defines the operator you want to use.</span><span class="sxs-lookup"><span data-stu-id="635c7-123">Be sure the class or structure you are using defines the operator you want to use.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="635c7-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="635c7-124">See also</span></span>

- [<span data-ttu-id="635c7-125">Procédures d’opérateur</span><span class="sxs-lookup"><span data-stu-id="635c7-125">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="635c7-126">Guide pratique : définir un opérateur</span><span class="sxs-lookup"><span data-stu-id="635c7-126">How to: Define an Operator</span></span>](./how-to-define-an-operator.md)
- [<span data-ttu-id="635c7-127">Guide pratique : définir un opérateur de conversion</span><span class="sxs-lookup"><span data-stu-id="635c7-127">How to: Define a Conversion Operator</span></span>](./how-to-define-a-conversion-operator.md)
- [<span data-ttu-id="635c7-128">Operator (instruction)</span><span class="sxs-lookup"><span data-stu-id="635c7-128">Operator Statement</span></span>](../../../../visual-basic/language-reference/statements/operator-statement.md)
- [<span data-ttu-id="635c7-129">Widening</span><span class="sxs-lookup"><span data-stu-id="635c7-129">Widening</span></span>](../../../../visual-basic/language-reference/modifiers/widening.md)
- [<span data-ttu-id="635c7-130">Narrowing</span><span class="sxs-lookup"><span data-stu-id="635c7-130">Narrowing</span></span>](../../../../visual-basic/language-reference/modifiers/narrowing.md)
- [<span data-ttu-id="635c7-131">Structure (instruction)</span><span class="sxs-lookup"><span data-stu-id="635c7-131">Structure Statement</span></span>](../../../../visual-basic/language-reference/statements/structure-statement.md)
- [<span data-ttu-id="635c7-132">Guide pratique : déclarer une structure</span><span class="sxs-lookup"><span data-stu-id="635c7-132">How to: Declare a Structure</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [<span data-ttu-id="635c7-133">Conversions implicites et explicites</span><span class="sxs-lookup"><span data-stu-id="635c7-133">Implicit and Explicit Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [<span data-ttu-id="635c7-134">Conversions étendues et restrictives</span><span class="sxs-lookup"><span data-stu-id="635c7-134">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
