---
title: Return, instruction
ms.date: 07/20/2015
f1_keywords:
- vb.Return
helpviewer_keywords:
- Return statement [Visual Basic], syntax
- control flow [Visual Basic], returning control to expressions
- Return statement [Visual Basic]
- expressions [Visual Basic], returning control to
ms.assetid: ac86e7f0-5a67-42c3-9834-0e0381efa3ec
ms.openlocfilehash: efc85a3a844898345aa2d16926ba0e35d7346d1b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74333013"
---
# <a name="return-statement-visual-basic"></a><span data-ttu-id="ddfd5-102">Return, instruction (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ddfd5-102">Return Statement (Visual Basic)</span></span>
<span data-ttu-id="ddfd5-103">Returns control to the code that called a `Function`, `Sub`, `Get`, `Set`, or `Operator` procedure.</span><span class="sxs-lookup"><span data-stu-id="ddfd5-103">Returns control to the code that called a `Function`, `Sub`, `Get`, `Set`, or `Operator` procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ddfd5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ddfd5-104">Syntax</span></span>  
  
```vb  
Return  
' -or-  
Return expression  
```  
  
## <a name="part"></a><span data-ttu-id="ddfd5-105">Élément</span><span class="sxs-lookup"><span data-stu-id="ddfd5-105">Part</span></span>  
 `expression`  
 <span data-ttu-id="ddfd5-106">Required in a `Function`, `Get`, or `Operator` procedure.</span><span class="sxs-lookup"><span data-stu-id="ddfd5-106">Required in a `Function`, `Get`, or `Operator` procedure.</span></span> <span data-ttu-id="ddfd5-107">Expression that represents the value to be returned to the calling code.</span><span class="sxs-lookup"><span data-stu-id="ddfd5-107">Expression that represents the value to be returned to the calling code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ddfd5-108">Notes</span><span class="sxs-lookup"><span data-stu-id="ddfd5-108">Remarks</span></span>  
 <span data-ttu-id="ddfd5-109">In a `Sub` or `Set` procedure, the `Return` statement is equivalent to an `Exit Sub` or `Exit Property` statement, and `expression` must not be supplied.</span><span class="sxs-lookup"><span data-stu-id="ddfd5-109">In a `Sub` or `Set` procedure, the `Return` statement is equivalent to an `Exit Sub` or `Exit Property` statement, and `expression` must not be supplied.</span></span>  
  
 <span data-ttu-id="ddfd5-110">In a `Function`, `Get`, or `Operator` procedure, the `Return` statement must include `expression`, and `expression` must evaluate to a data type that is convertible to the return type of the procedure.</span><span class="sxs-lookup"><span data-stu-id="ddfd5-110">In a `Function`, `Get`, or `Operator` procedure, the `Return` statement must include `expression`, and `expression` must evaluate to a data type that is convertible to the return type of the procedure.</span></span> <span data-ttu-id="ddfd5-111">In a `Function` or `Get` procedure, you also have the alternative of assigning an expression to the procedure name to serve as the return value, and then executing an `Exit Function` or `Exit Property` statement.</span><span class="sxs-lookup"><span data-stu-id="ddfd5-111">In a `Function` or `Get` procedure, you also have the alternative of assigning an expression to the procedure name to serve as the return value, and then executing an `Exit Function` or `Exit Property` statement.</span></span> <span data-ttu-id="ddfd5-112">In an `Operator` procedure, you must use `Return expression`.</span><span class="sxs-lookup"><span data-stu-id="ddfd5-112">In an `Operator` procedure, you must use `Return expression`.</span></span>  
  
 <span data-ttu-id="ddfd5-113">You can include as many `Return` statements as appropriate in the same procedure.</span><span class="sxs-lookup"><span data-stu-id="ddfd5-113">You can include as many `Return` statements as appropriate in the same procedure.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ddfd5-114">The code in a `Finally` block runs after a `Return` statement in a `Try` or `Catch` block is encountered, but before that `Return` statement executes.</span><span class="sxs-lookup"><span data-stu-id="ddfd5-114">The code in a `Finally` block runs after a `Return` statement in a `Try` or `Catch` block is encountered, but before that `Return` statement executes.</span></span> <span data-ttu-id="ddfd5-115">A `Return` statement cannot be included in a `Finally` block.</span><span class="sxs-lookup"><span data-stu-id="ddfd5-115">A `Return` statement cannot be included in a `Finally` block.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ddfd5-116">Exemple</span><span class="sxs-lookup"><span data-stu-id="ddfd5-116">Example</span></span>  
 <span data-ttu-id="ddfd5-117">The following example uses the `Return` statement several times to return to the calling code when the procedure does not have to do anything else.</span><span class="sxs-lookup"><span data-stu-id="ddfd5-117">The following example uses the `Return` statement several times to return to the calling code when the procedure does not have to do anything else.</span></span>  
  
 [!code-vb[VbVbalrStatements#53](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#53)]  
  
## <a name="see-also"></a><span data-ttu-id="ddfd5-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ddfd5-118">See also</span></span>

- [<span data-ttu-id="ddfd5-119">Function (instruction)</span><span class="sxs-lookup"><span data-stu-id="ddfd5-119">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="ddfd5-120">Sub (instruction)</span><span class="sxs-lookup"><span data-stu-id="ddfd5-120">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="ddfd5-121">Get (instruction)</span><span class="sxs-lookup"><span data-stu-id="ddfd5-121">Get Statement</span></span>](../../../visual-basic/language-reference/statements/get-statement.md)
- [<span data-ttu-id="ddfd5-122">Set (instruction)</span><span class="sxs-lookup"><span data-stu-id="ddfd5-122">Set Statement</span></span>](../../../visual-basic/language-reference/statements/set-statement.md)
- [<span data-ttu-id="ddfd5-123">Operator (instruction)</span><span class="sxs-lookup"><span data-stu-id="ddfd5-123">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)
- [<span data-ttu-id="ddfd5-124">Property (instruction)</span><span class="sxs-lookup"><span data-stu-id="ddfd5-124">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)
- [<span data-ttu-id="ddfd5-125">Exit (instruction)</span><span class="sxs-lookup"><span data-stu-id="ddfd5-125">Exit Statement</span></span>](../../../visual-basic/language-reference/statements/exit-statement.md)
- [<span data-ttu-id="ddfd5-126">Try...Catch...Finally (instruction)</span><span class="sxs-lookup"><span data-stu-id="ddfd5-126">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
