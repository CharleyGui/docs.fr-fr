---
title: Return (instruction)
ms.date: 07/20/2015
f1_keywords:
- vb.Return
helpviewer_keywords:
- Return statement [Visual Basic], syntax
- control flow [Visual Basic], returning control to expressions
- Return statement [Visual Basic]
- expressions [Visual Basic], returning control to
ms.assetid: ac86e7f0-5a67-42c3-9834-0e0381efa3ec
ms.openlocfilehash: 3ca705409bc8233bc2562c64b8e7704f08dd7641
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90871806"
---
# <a name="return-statement-visual-basic"></a><span data-ttu-id="94392-102">Return, instruction (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="94392-102">Return Statement (Visual Basic)</span></span>

<span data-ttu-id="94392-103">Retourne le contrôle au code qui a appelé une `Function` procédure,,, `Sub` `Get` `Set` ou `Operator` .</span><span class="sxs-lookup"><span data-stu-id="94392-103">Returns control to the code that called a `Function`, `Sub`, `Get`, `Set`, or `Operator` procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94392-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="94392-104">Syntax</span></span>  
  
```vb  
Return  
' -or-  
Return expression  
```  
  
## <a name="part"></a><span data-ttu-id="94392-105">Élément</span><span class="sxs-lookup"><span data-stu-id="94392-105">Part</span></span>  

 `expression`  
 <span data-ttu-id="94392-106">Obligatoire dans une `Function` `Get` procédure, ou `Operator` .</span><span class="sxs-lookup"><span data-stu-id="94392-106">Required in a `Function`, `Get`, or `Operator` procedure.</span></span> <span data-ttu-id="94392-107">Expression qui représente la valeur à retourner au code appelant.</span><span class="sxs-lookup"><span data-stu-id="94392-107">Expression that represents the value to be returned to the calling code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="94392-108">Notes</span><span class="sxs-lookup"><span data-stu-id="94392-108">Remarks</span></span>  

 <span data-ttu-id="94392-109">Dans une `Sub` `Set` procédure ou, l' `Return` instruction est équivalente à `Exit Sub` une `Exit Property` instruction ou, et `expression` ne doit pas être fournie.</span><span class="sxs-lookup"><span data-stu-id="94392-109">In a `Sub` or `Set` procedure, the `Return` statement is equivalent to an `Exit Sub` or `Exit Property` statement, and `expression` must not be supplied.</span></span>  
  
 <span data-ttu-id="94392-110">Dans une `Function` `Get` procédure, ou `Operator` , l' `Return` instruction doit inclure `expression` , et `expression` doit correspondre à un type de données convertible en type de retour de la procédure.</span><span class="sxs-lookup"><span data-stu-id="94392-110">In a `Function`, `Get`, or `Operator` procedure, the `Return` statement must include `expression`, and `expression` must evaluate to a data type that is convertible to the return type of the procedure.</span></span> <span data-ttu-id="94392-111">Dans une `Function` `Get` procédure ou, vous avez également la possibilité d’attribuer une expression au nom de la procédure pour servir de valeur de retour, puis d’exécuter une `Exit Function` instruction ou `Exit Property` .</span><span class="sxs-lookup"><span data-stu-id="94392-111">In a `Function` or `Get` procedure, you also have the alternative of assigning an expression to the procedure name to serve as the return value, and then executing an `Exit Function` or `Exit Property` statement.</span></span> <span data-ttu-id="94392-112">Dans une `Operator` procédure, vous devez utiliser `Return expression` .</span><span class="sxs-lookup"><span data-stu-id="94392-112">In an `Operator` procedure, you must use `Return expression`.</span></span>  
  
 <span data-ttu-id="94392-113">Vous pouvez inclure autant `Return` d’instructions que nécessaire dans la même procédure.</span><span class="sxs-lookup"><span data-stu-id="94392-113">You can include as many `Return` statements as appropriate in the same procedure.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="94392-114">Le code d’un `Finally` bloc s’exécute après l’exécution d’une `Return` instruction dans un `Try` `Catch` bloc ou, mais avant l’exécution de cette `Return` instruction.</span><span class="sxs-lookup"><span data-stu-id="94392-114">The code in a `Finally` block runs after a `Return` statement in a `Try` or `Catch` block is encountered, but before that `Return` statement executes.</span></span> <span data-ttu-id="94392-115">Une `Return` instruction ne peut pas être incluse dans un `Finally` bloc.</span><span class="sxs-lookup"><span data-stu-id="94392-115">A `Return` statement cannot be included in a `Finally` block.</span></span>  
  
## <a name="example"></a><span data-ttu-id="94392-116">Exemple</span><span class="sxs-lookup"><span data-stu-id="94392-116">Example</span></span>  

 <span data-ttu-id="94392-117">L’exemple suivant utilise `Return` plusieurs fois l’instruction pour retourner au code appelant lorsque la procédure n’a pas à faire autre chose.</span><span class="sxs-lookup"><span data-stu-id="94392-117">The following example uses the `Return` statement several times to return to the calling code when the procedure does not have to do anything else.</span></span>  
  
 [!code-vb[VbVbalrStatements#53](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#53)]  
  
## <a name="see-also"></a><span data-ttu-id="94392-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="94392-118">See also</span></span>

- [<span data-ttu-id="94392-119">Function (instruction)</span><span class="sxs-lookup"><span data-stu-id="94392-119">Function Statement</span></span>](function-statement.md)
- [<span data-ttu-id="94392-120">Sub (instruction)</span><span class="sxs-lookup"><span data-stu-id="94392-120">Sub Statement</span></span>](sub-statement.md)
- [<span data-ttu-id="94392-121">Get, instruction</span><span class="sxs-lookup"><span data-stu-id="94392-121">Get Statement</span></span>](get-statement.md)
- [<span data-ttu-id="94392-122">Instruction Set</span><span class="sxs-lookup"><span data-stu-id="94392-122">Set Statement</span></span>](set-statement.md)
- [<span data-ttu-id="94392-123">Operator Statement</span><span class="sxs-lookup"><span data-stu-id="94392-123">Operator Statement</span></span>](operator-statement.md)
- [<span data-ttu-id="94392-124">Property Statement</span><span class="sxs-lookup"><span data-stu-id="94392-124">Property Statement</span></span>](property-statement.md)
- [<span data-ttu-id="94392-125">Exit (instruction)</span><span class="sxs-lookup"><span data-stu-id="94392-125">Exit Statement</span></span>](exit-statement.md)
- [<span data-ttu-id="94392-126">Try...Catch...Finally (instruction)</span><span class="sxs-lookup"><span data-stu-id="94392-126">Try...Catch...Finally Statement</span></span>](try-catch-finally-statement.md)
