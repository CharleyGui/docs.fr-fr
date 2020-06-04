---
title: Resume, instruction
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
ms.openlocfilehash: 3f49f05f1deb2027b03bbf3443ca44f30c44344e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404211"
---
# <a name="resume-statement"></a><span data-ttu-id="ca179-102">Resume, instruction</span><span class="sxs-lookup"><span data-stu-id="ca179-102">Resume Statement</span></span>
<span data-ttu-id="ca179-103">Reprend l’exécution après la fin d’une routine de gestion des erreurs.</span><span class="sxs-lookup"><span data-stu-id="ca179-103">Resumes execution after an error-handling routine is finished.</span></span>  
  
 <span data-ttu-id="ca179-104">Nous vous suggérons d’utiliser la gestion structurée des exceptions dans votre code dans la mesure du possible, au lieu d’utiliser la gestion non structurée des exceptions et les `On Error` `Resume` instructions et.</span><span class="sxs-lookup"><span data-stu-id="ca179-104">We suggest that you use structured exception handling in your code whenever possible, rather than using unstructured exception handling and the `On Error` and `Resume` statements.</span></span> <span data-ttu-id="ca179-105">Pour plus d’informations, consultez [Try...Catch...Finally, instruction](try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="ca179-105">For more information, see [Try...Catch...Finally Statement](try-catch-finally-statement.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca179-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ca179-106">Syntax</span></span>  
  
```vb  
Resume [ Next | line ]  
```  
  
## <a name="parts"></a><span data-ttu-id="ca179-107">Éléments</span><span class="sxs-lookup"><span data-stu-id="ca179-107">Parts</span></span>  
 `Resume`  
 <span data-ttu-id="ca179-108">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="ca179-108">Required.</span></span> <span data-ttu-id="ca179-109">Si l’erreur s’est produite dans la même procédure que le gestionnaire d’erreurs, l’exécution reprend avec l’instruction qui a provoqué l’erreur.</span><span class="sxs-lookup"><span data-stu-id="ca179-109">If the error occurred in the same procedure as the error handler, execution resumes with the statement that caused the error.</span></span> <span data-ttu-id="ca179-110">Si l’erreur s’est produite dans une procédure appelée, l’exécution reprend au niveau de l’instruction qui a appelé en dehors de la procédure qui contient la routine de gestion des erreurs.</span><span class="sxs-lookup"><span data-stu-id="ca179-110">If the error occurred in a called procedure, execution resumes at the statement that last called out of the procedure containing the error-handling routine.</span></span>  
  
 `Next`  
 <span data-ttu-id="ca179-111">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="ca179-111">Optional.</span></span> <span data-ttu-id="ca179-112">Si l’erreur s’est produite dans la même procédure que le gestionnaire d’erreurs, l’exécution reprend avec l’instruction qui suit immédiatement l’instruction qui a provoqué l’erreur.</span><span class="sxs-lookup"><span data-stu-id="ca179-112">If the error occurred in the same procedure as the error handler, execution resumes with the statement immediately following the statement that caused the error.</span></span> <span data-ttu-id="ca179-113">Si l’erreur s’est produite dans une procédure appelée, l’exécution reprend avec l’instruction qui suit immédiatement l’instruction qui a appelé en dehors de la procédure qui contient la routine de gestion des erreurs (ou l' `On Error Resume Next` instruction).</span><span class="sxs-lookup"><span data-stu-id="ca179-113">If the error occurred in a called procedure, execution resumes with the statement immediately following the statement that last called out of the procedure containing the error-handling routine (or `On Error Resume Next` statement).</span></span>  
  
 `line`  
 <span data-ttu-id="ca179-114">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="ca179-114">Optional.</span></span> <span data-ttu-id="ca179-115">L’exécution reprend à la ligne spécifiée dans l' `line` argument requis.</span><span class="sxs-lookup"><span data-stu-id="ca179-115">Execution resumes at the line specified in the required `line` argument.</span></span> <span data-ttu-id="ca179-116">L' `line` argument est une étiquette de ligne ou un numéro de ligne et doit être dans la même procédure que le gestionnaire d’erreurs.</span><span class="sxs-lookup"><span data-stu-id="ca179-116">The `line` argument is a line label or line number and must be in the same procedure as the error handler.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ca179-117">Notes</span><span class="sxs-lookup"><span data-stu-id="ca179-117">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ca179-118">Nous vous recommandons d’utiliser la gestion structurée des exceptions dans votre code dans la mesure du possible, au lieu d’utiliser la gestion des exceptions non structurées et les `On Error` `Resume` instructions et.</span><span class="sxs-lookup"><span data-stu-id="ca179-118">We recommend that you use structured exception handling in your code whenever possible, rather than using unstructured exception handling and the `On Error` and `Resume` statements.</span></span> <span data-ttu-id="ca179-119">Pour plus d’informations, consultez [Try...Catch...Finally, instruction](try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="ca179-119">For more information, see [Try...Catch...Finally Statement](try-catch-finally-statement.md).</span></span>  
  
 <span data-ttu-id="ca179-120">Si vous utilisez une `Resume` instruction n’importe où dans une routine de gestion des erreurs, une erreur se produit.</span><span class="sxs-lookup"><span data-stu-id="ca179-120">If you use a `Resume` statement anywhere other than in an error-handling routine, an error occurs.</span></span>  
  
 <span data-ttu-id="ca179-121">L' `Resume` instruction ne peut pas être utilisée dans une procédure qui contient une `Try...Catch...Finally` instruction.</span><span class="sxs-lookup"><span data-stu-id="ca179-121">The `Resume` statement cannot be used in any procedure that contains a `Try...Catch...Finally` statement.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ca179-122">Exemple</span><span class="sxs-lookup"><span data-stu-id="ca179-122">Example</span></span>  
 <span data-ttu-id="ca179-123">Cet exemple utilise l' `Resume` instruction pour terminer la gestion des erreurs dans une procédure, puis reprendre l’exécution avec l’instruction qui a provoqué l’erreur.</span><span class="sxs-lookup"><span data-stu-id="ca179-123">This example uses the `Resume` statement to end error handling in a procedure and then resume execution with the statement that caused the error.</span></span> <span data-ttu-id="ca179-124">L’erreur numéro 55 est générée pour illustrer l’utilisation de l' `Resume` instruction.</span><span class="sxs-lookup"><span data-stu-id="ca179-124">Error number 55 is generated to illustrate use of the `Resume` statement.</span></span>  
  
 [!code-vb[VbVbalrErrorHandling#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrErrorHandling/VB/Class1.vb#16)]  
  
## <a name="requirements"></a><span data-ttu-id="ca179-125">Spécifications</span><span class="sxs-lookup"><span data-stu-id="ca179-125">Requirements</span></span>  
 <span data-ttu-id="ca179-126">**Espace de noms :** [Microsoft. VisualBasic](../runtime-library-members.md)</span><span class="sxs-lookup"><span data-stu-id="ca179-126">**Namespace:** [Microsoft.VisualBasic](../runtime-library-members.md)</span></span>  
  
 <span data-ttu-id="ca179-127">**Assembly :** Visual Basic bibliothèque Runtime (dans Microsoft. VisualBasic. dll)</span><span class="sxs-lookup"><span data-stu-id="ca179-127">**Assembly:** Visual Basic Runtime Library (in Microsoft.VisualBasic.dll)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca179-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ca179-128">See also</span></span>

- [<span data-ttu-id="ca179-129">Try...Catch...Finally (instruction)</span><span class="sxs-lookup"><span data-stu-id="ca179-129">Try...Catch...Finally Statement</span></span>](try-catch-finally-statement.md)
- [<span data-ttu-id="ca179-130">Error, instruction</span><span class="sxs-lookup"><span data-stu-id="ca179-130">Error Statement</span></span>](error-statement.md)
- [<span data-ttu-id="ca179-131">On Error (instruction)</span><span class="sxs-lookup"><span data-stu-id="ca179-131">On Error Statement</span></span>](on-error-statement.md)
