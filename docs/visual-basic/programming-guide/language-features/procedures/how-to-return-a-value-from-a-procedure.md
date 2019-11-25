---
title: "Comment : retourner une valeur d'une procédure"
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], returning from
- procedures [Visual Basic], returning a value
ms.assetid: 4bcc4724-2b4e-4df8-9b4b-16054607f87d
ms.openlocfilehash: 1371e4ed0ff28f9caf56eabf2a1bb9290edbe75c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346025"
---
# <a name="how-to-return-a-value-from-a-procedure-visual-basic"></a><span data-ttu-id="f0783-102">Comment : retourner une valeur d'une procédure (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f0783-102">How to: Return a Value from a Procedure (Visual Basic)</span></span>
<span data-ttu-id="f0783-103">A `Function` procedure returns a value to the calling code either by executing a `Return` statement or by encountering an `Exit Function` or `End Function` statement.</span><span class="sxs-lookup"><span data-stu-id="f0783-103">A `Function` procedure returns a value to the calling code either by executing a `Return` statement or by encountering an `Exit Function` or `End Function` statement.</span></span>  
  
### <a name="to-return-a-value-using-the-return-statement"></a><span data-ttu-id="f0783-104">To return a value using the Return statement</span><span class="sxs-lookup"><span data-stu-id="f0783-104">To return a value using the Return statement</span></span>  
  
1. <span data-ttu-id="f0783-105">Put a `Return` statement at the point where the procedure's task is completed.</span><span class="sxs-lookup"><span data-stu-id="f0783-105">Put a `Return` statement at the point where the procedure's task is completed.</span></span>  
  
2. <span data-ttu-id="f0783-106">Follow the `Return` keyword with an expression that yields the value you want to return to the calling code.</span><span class="sxs-lookup"><span data-stu-id="f0783-106">Follow the `Return` keyword with an expression that yields the value you want to return to the calling code.</span></span>  
  
3. <span data-ttu-id="f0783-107">Vous pouvez utiliser plusieurs instructions `Return` dans la même procédure.</span><span class="sxs-lookup"><span data-stu-id="f0783-107">You can have more than one `Return` statement in the same procedure.</span></span>  
  
     <span data-ttu-id="f0783-108">The following `Function` procedure calculates the longest side, or hypotenuse, of a right triangle, and returns it to the calling code.</span><span class="sxs-lookup"><span data-stu-id="f0783-108">The following `Function` procedure calculates the longest side, or hypotenuse, of a right triangle, and returns it to the calling code.</span></span>  
  
     [!code-vb[VbVbcnProcedures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#1)]  
  
     <span data-ttu-id="f0783-109">The following example shows a typical call to `hypotenuse`, which stores the returned value.</span><span class="sxs-lookup"><span data-stu-id="f0783-109">The following example shows a typical call to `hypotenuse`, which stores the returned value.</span></span>  
  
     [!code-vb[VbVbcnProcedures#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#6)]  
  
### <a name="to-return-a-value-using-exit-function-or-end-function"></a><span data-ttu-id="f0783-110">To return a value using Exit Function or End Function</span><span class="sxs-lookup"><span data-stu-id="f0783-110">To return a value using Exit Function or End Function</span></span>  
  
1. <span data-ttu-id="f0783-111">In at least one place in the `Function` procedure, assign a value to the procedure's name.</span><span class="sxs-lookup"><span data-stu-id="f0783-111">In at least one place in the `Function` procedure, assign a value to the procedure's name.</span></span>  
  
2. <span data-ttu-id="f0783-112">When you execute an `Exit Function` or `End Function` statement, Visual Basic returns the value most recently assigned to the procedure's name.</span><span class="sxs-lookup"><span data-stu-id="f0783-112">When you execute an `Exit Function` or `End Function` statement, Visual Basic returns the value most recently assigned to the procedure's name.</span></span>  
  
3. <span data-ttu-id="f0783-113">Vous pouvez utiliser plusieurs instructions `Exit Function` dans la même procédure et combiner des instructions `Return` et `Exit Function` dans la même procédure.</span><span class="sxs-lookup"><span data-stu-id="f0783-113">You can have more than one `Exit Function` statement in the same procedure, and you can mix `Return` and `Exit Function` statements in the same procedure.</span></span>  
  
4. <span data-ttu-id="f0783-114">You can have only one `End Function` statement in a `Function` procedure.</span><span class="sxs-lookup"><span data-stu-id="f0783-114">You can have only one `End Function` statement in a `Function` procedure.</span></span>  
  
     <span data-ttu-id="f0783-115">For more information and an example, see "Return Value" in [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="f0783-115">For more information and an example, see "Return Value" in [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0783-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f0783-116">See also</span></span>

- [<span data-ttu-id="f0783-117">Procédures</span><span class="sxs-lookup"><span data-stu-id="f0783-117">Procedures</span></span>](./index.md)
- [<span data-ttu-id="f0783-118">Procédures Sub</span><span class="sxs-lookup"><span data-stu-id="f0783-118">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="f0783-119">Procédures de propriété</span><span class="sxs-lookup"><span data-stu-id="f0783-119">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="f0783-120">Procédures d’opérateur</span><span class="sxs-lookup"><span data-stu-id="f0783-120">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="f0783-121">Paramètres et arguments d’une procédure</span><span class="sxs-lookup"><span data-stu-id="f0783-121">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="f0783-122">Function (instruction)</span><span class="sxs-lookup"><span data-stu-id="f0783-122">Function Statement</span></span>](../../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="f0783-123">Return (instruction)</span><span class="sxs-lookup"><span data-stu-id="f0783-123">Return Statement</span></span>](../../../../visual-basic/language-reference/statements/return-statement.md)
- [<span data-ttu-id="f0783-124">Guide pratique : créer une procédure qui retourne une valeur</span><span class="sxs-lookup"><span data-stu-id="f0783-124">How to: Create a Procedure that Returns a Value</span></span>](./how-to-create-a-procedure-that-returns-a-value.md)
- [<span data-ttu-id="f0783-125">Guide pratique : appeler une procédure qui retourne une valeur</span><span class="sxs-lookup"><span data-stu-id="f0783-125">How to: Call a Procedure That Returns a Value</span></span>](./how-to-call-a-procedure-that-returns-a-value.md)
