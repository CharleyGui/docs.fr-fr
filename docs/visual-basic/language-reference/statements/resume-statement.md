---
title: Resume, instruction (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Resume
- vb.ResumeNext
helpviewer_keywords:
- Next statement [Visual Basic], Resume
- Resume Next statement [Visual Basic]
- execution [Visual Basic], resuming
- run-time errors [Visual Basic], resuming after
- Resume statement [Visual Basic], syntax
- errors [Visual Basic], resuming after
- Error statement [Visual Basic], and Resume statement
- execution
- Resume statement [Visual Basic]
ms.assetid: e24d058b-1a5c-4274-acb9-7d295d3ea537
ms.openlocfilehash: 884bdaa0c19508b5a6bf6377568a53acc6880518
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957688"
---
# <a name="resume-statement"></a><span data-ttu-id="aa628-102">Resume, instruction</span><span class="sxs-lookup"><span data-stu-id="aa628-102">Resume Statement</span></span>
<span data-ttu-id="aa628-103">Reprend l’exécution après la fin d’une routine de gestion des erreurs.</span><span class="sxs-lookup"><span data-stu-id="aa628-103">Resumes execution after an error-handling routine is finished.</span></span>  
  
 <span data-ttu-id="aa628-104">Nous vous suggérons d’utiliser la gestion structurée des exceptions dans votre code dans la mesure du possible, au lieu d' `On Error` utiliser `Resume` la gestion non structurée des exceptions et les instructions et.</span><span class="sxs-lookup"><span data-stu-id="aa628-104">We suggest that you use structured exception handling in your code whenever possible, rather than using unstructured exception handling and the `On Error` and `Resume` statements.</span></span> <span data-ttu-id="aa628-105">Pour plus d’informations, consultez [Try...Catch...Finally, instruction](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="aa628-105">For more information, see [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa628-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="aa628-106">Syntax</span></span>  
  
```  
Resume [ Next | line ]  
```  
  
## <a name="parts"></a><span data-ttu-id="aa628-107">Composants</span><span class="sxs-lookup"><span data-stu-id="aa628-107">Parts</span></span>  
 `Resume`  
 <span data-ttu-id="aa628-108">Requis.</span><span class="sxs-lookup"><span data-stu-id="aa628-108">Required.</span></span> <span data-ttu-id="aa628-109">Si l’erreur s’est produite dans la même procédure que le gestionnaire d’erreurs, l’exécution reprend avec l’instruction qui a provoqué l’erreur.</span><span class="sxs-lookup"><span data-stu-id="aa628-109">If the error occurred in the same procedure as the error handler, execution resumes with the statement that caused the error.</span></span> <span data-ttu-id="aa628-110">Si l’erreur s’est produite dans une procédure appelée, l’exécution reprend au niveau de l’instruction qui a appelé en dehors de la procédure qui contient la routine de gestion des erreurs.</span><span class="sxs-lookup"><span data-stu-id="aa628-110">If the error occurred in a called procedure, execution resumes at the statement that last called out of the procedure containing the error-handling routine.</span></span>  
  
 `Next`  
 <span data-ttu-id="aa628-111">facultatif.</span><span class="sxs-lookup"><span data-stu-id="aa628-111">Optional.</span></span> <span data-ttu-id="aa628-112">Si l’erreur s’est produite dans la même procédure que le gestionnaire d’erreurs, l’exécution reprend avec l’instruction qui suit immédiatement l’instruction qui a provoqué l’erreur.</span><span class="sxs-lookup"><span data-stu-id="aa628-112">If the error occurred in the same procedure as the error handler, execution resumes with the statement immediately following the statement that caused the error.</span></span> <span data-ttu-id="aa628-113">Si l’erreur s’est produite dans une procédure appelée, l’exécution reprend avec l’instruction qui suit immédiatement l’instruction qui a appelé en dehors de la procédure qui contient la routine `On Error Resume Next` de gestion des erreurs (ou l’instruction).</span><span class="sxs-lookup"><span data-stu-id="aa628-113">If the error occurred in a called procedure, execution resumes with the statement immediately following the statement that last called out of the procedure containing the error-handling routine (or `On Error Resume Next` statement).</span></span>  
  
 `line`  
 <span data-ttu-id="aa628-114">facultatif.</span><span class="sxs-lookup"><span data-stu-id="aa628-114">Optional.</span></span> <span data-ttu-id="aa628-115">L’exécution reprend à la ligne spécifiée dans l’argument `line` requis.</span><span class="sxs-lookup"><span data-stu-id="aa628-115">Execution resumes at the line specified in the required `line` argument.</span></span> <span data-ttu-id="aa628-116">L' `line` argument est une étiquette de ligne ou un numéro de ligne et doit être dans la même procédure que le gestionnaire d’erreurs.</span><span class="sxs-lookup"><span data-stu-id="aa628-116">The `line` argument is a line label or line number and must be in the same procedure as the error handler.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aa628-117">Notes</span><span class="sxs-lookup"><span data-stu-id="aa628-117">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="aa628-118">Nous vous recommandons d’utiliser la gestion structurée des exceptions dans votre code dans la mesure du possible, au lieu d’utiliser `On Error` la `Resume` gestion des exceptions non structurées et les instructions et.</span><span class="sxs-lookup"><span data-stu-id="aa628-118">We recommend that you use structured exception handling in your code whenever possible, rather than using unstructured exception handling and the `On Error` and `Resume` statements.</span></span> <span data-ttu-id="aa628-119">Pour plus d’informations, consultez [Try...Catch...Finally, instruction](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="aa628-119">For more information, see [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
 <span data-ttu-id="aa628-120">Si vous utilisez une `Resume` instruction n’importe où dans une routine de gestion des erreurs, une erreur se produit.</span><span class="sxs-lookup"><span data-stu-id="aa628-120">If you use a `Resume` statement anywhere other than in an error-handling routine, an error occurs.</span></span>  
  
 <span data-ttu-id="aa628-121">L' `Resume` instruction ne peut pas être utilisée dans une procédure qui `Try...Catch...Finally` contient une instruction.</span><span class="sxs-lookup"><span data-stu-id="aa628-121">The `Resume` statement cannot be used in any procedure that contains a `Try...Catch...Finally` statement.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aa628-122">Exemple</span><span class="sxs-lookup"><span data-stu-id="aa628-122">Example</span></span>  
 <span data-ttu-id="aa628-123">Cet exemple utilise l' `Resume` instruction pour terminer la gestion des erreurs dans une procédure, puis reprendre l’exécution avec l’instruction qui a provoqué l’erreur.</span><span class="sxs-lookup"><span data-stu-id="aa628-123">This example uses the `Resume` statement to end error handling in a procedure and then resume execution with the statement that caused the error.</span></span> <span data-ttu-id="aa628-124">L’erreur numéro 55 est générée pour illustrer l' `Resume` utilisation de l’instruction.</span><span class="sxs-lookup"><span data-stu-id="aa628-124">Error number 55 is generated to illustrate use of the `Resume` statement.</span></span>  
  
 [!code-vb[VbVbalrErrorHandling#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrErrorHandling/VB/Class1.vb#16)]  
  
## <a name="requirements"></a><span data-ttu-id="aa628-125">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="aa628-125">Requirements</span></span>  
 <span data-ttu-id="aa628-126">**Espace de noms :** [Microsoft. VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span><span class="sxs-lookup"><span data-stu-id="aa628-126">**Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span></span>  
  
 <span data-ttu-id="aa628-127">**Chargeur** bibliothèque Visual Basic Runtime (dans Microsoft.VisualBasic.dll)</span><span class="sxs-lookup"><span data-stu-id="aa628-127">**Assembly:** Visual Basic Runtime Library (in Microsoft.VisualBasic.dll)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa628-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="aa628-128">See also</span></span>

- [<span data-ttu-id="aa628-129">Try...Catch...Finally (instruction)</span><span class="sxs-lookup"><span data-stu-id="aa628-129">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [<span data-ttu-id="aa628-130">Error (instruction)</span><span class="sxs-lookup"><span data-stu-id="aa628-130">Error Statement</span></span>](../../../visual-basic/language-reference/statements/error-statement.md)
- [<span data-ttu-id="aa628-131">On Error (instruction)</span><span class="sxs-lookup"><span data-stu-id="aa628-131">On Error Statement</span></span>](../../../visual-basic/language-reference/statements/on-error-statement.md)
