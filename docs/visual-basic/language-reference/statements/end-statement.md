---
title: End, instruction
ms.date: 07/20/2015
f1_keywords:
- vb.End
- End
helpviewer_keywords:
- execution [Visual Basic], ending
- files [Visual Basic], closing
- End keyword [Visual Basic], End statements
- programs [Visual Basic], quitting
- code, exiting
- program termination
- End statement [Visual Basic]
- execution [Visual Basic], stopping
ms.assetid: 0e64467c-0f34-4aab-9ddd-43f8b9d55d90
ms.openlocfilehash: cb2fb4abb21b7b9c6575cec4aca1374f63687607
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343722"
---
# <a name="end-statement"></a><span data-ttu-id="14448-102">End, instruction</span><span class="sxs-lookup"><span data-stu-id="14448-102">End Statement</span></span>
<span data-ttu-id="14448-103">Terminates execution immediately.</span><span class="sxs-lookup"><span data-stu-id="14448-103">Terminates execution immediately.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14448-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="14448-104">Syntax</span></span>  
  
```vb  
End  
```  
  
## <a name="remarks"></a><span data-ttu-id="14448-105">Notes</span><span class="sxs-lookup"><span data-stu-id="14448-105">Remarks</span></span>  
 <span data-ttu-id="14448-106">You can place the `End` statement anywhere in a procedure to force the entire application to stop running.</span><span class="sxs-lookup"><span data-stu-id="14448-106">You can place the `End` statement anywhere in a procedure to force the entire application to stop running.</span></span> <span data-ttu-id="14448-107">`End` closes any files opened with an `Open` statement and clears all the application's variables.</span><span class="sxs-lookup"><span data-stu-id="14448-107">`End` closes any files opened with an `Open` statement and clears all the application's variables.</span></span> <span data-ttu-id="14448-108">The application closes as soon as there are no other programs holding references to its objects and none of its code is running.</span><span class="sxs-lookup"><span data-stu-id="14448-108">The application closes as soon as there are no other programs holding references to its objects and none of its code is running.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="14448-109">The `End` statement stops code execution abruptly, and does not invoke the `Dispose` or `Finalize` method, or any other Visual Basic code.</span><span class="sxs-lookup"><span data-stu-id="14448-109">The `End` statement stops code execution abruptly, and does not invoke the `Dispose` or `Finalize` method, or any other Visual Basic code.</span></span> <span data-ttu-id="14448-110">Object references held by other programs are invalidated.</span><span class="sxs-lookup"><span data-stu-id="14448-110">Object references held by other programs are invalidated.</span></span> <span data-ttu-id="14448-111">If an `End` statement is encountered within a `Try` or `Catch` block, control does not pass to the corresponding `Finally` block.</span><span class="sxs-lookup"><span data-stu-id="14448-111">If an `End` statement is encountered within a `Try` or `Catch` block, control does not pass to the corresponding `Finally` block.</span></span>  
  
 <span data-ttu-id="14448-112">The `Stop` statement suspends execution, but unlike `End`, it does not close any files or clear any variables, unless it is encountered in a compiled executable (.exe) file.</span><span class="sxs-lookup"><span data-stu-id="14448-112">The `Stop` statement suspends execution, but unlike `End`, it does not close any files or clear any variables, unless it is encountered in a compiled executable (.exe) file.</span></span>  
  
 <span data-ttu-id="14448-113">Because `End` terminates your application without attending to any resources that might be open, you should try to close down cleanly before using it.</span><span class="sxs-lookup"><span data-stu-id="14448-113">Because `End` terminates your application without attending to any resources that might be open, you should try to close down cleanly before using it.</span></span> <span data-ttu-id="14448-114">For example, if your application has any forms open, you should close them before control reaches the `End` statement.</span><span class="sxs-lookup"><span data-stu-id="14448-114">For example, if your application has any forms open, you should close them before control reaches the `End` statement.</span></span>  
  
 <span data-ttu-id="14448-115">You should use `End` sparingly, and only when you need to stop immediately.</span><span class="sxs-lookup"><span data-stu-id="14448-115">You should use `End` sparingly, and only when you need to stop immediately.</span></span> <span data-ttu-id="14448-116">The normal ways to terminate a procedure ([Return Statement](../../../visual-basic/language-reference/statements/return-statement.md) and [Exit Statement](../../../visual-basic/language-reference/statements/exit-statement.md)) not only close down the procedure cleanly but also give the calling code the opportunity to close down cleanly.</span><span class="sxs-lookup"><span data-stu-id="14448-116">The normal ways to terminate a procedure ([Return Statement](../../../visual-basic/language-reference/statements/return-statement.md) and [Exit Statement](../../../visual-basic/language-reference/statements/exit-statement.md)) not only close down the procedure cleanly but also give the calling code the opportunity to close down cleanly.</span></span> <span data-ttu-id="14448-117">A console application, for example, can simply `Return` from the `Main` procedure.</span><span class="sxs-lookup"><span data-stu-id="14448-117">A console application, for example, can simply `Return` from the `Main` procedure.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="14448-118">The `End` statement calls the <xref:System.Environment.Exit%2A> method of the <xref:System.Environment> class in the <xref:System> namespace.</span><span class="sxs-lookup"><span data-stu-id="14448-118">The `End` statement calls the <xref:System.Environment.Exit%2A> method of the <xref:System.Environment> class in the <xref:System> namespace.</span></span> <span data-ttu-id="14448-119"><xref:System.Environment.Exit%2A> requires that you have `UnmanagedCode` permission.</span><span class="sxs-lookup"><span data-stu-id="14448-119"><xref:System.Environment.Exit%2A> requires that you have `UnmanagedCode` permission.</span></span> <span data-ttu-id="14448-120">If you do not, a <xref:System.Security.SecurityException> error occurs.</span><span class="sxs-lookup"><span data-stu-id="14448-120">If you do not, a <xref:System.Security.SecurityException> error occurs.</span></span>  
  
 <span data-ttu-id="14448-121">When followed by an additional keyword, [End \<keyword> Statement](../../../visual-basic/language-reference/statements/end-keyword-statement.md) delineates the end of the definition of the appropriate procedure or block.</span><span class="sxs-lookup"><span data-stu-id="14448-121">When followed by an additional keyword, [End \<keyword> Statement](../../../visual-basic/language-reference/statements/end-keyword-statement.md) delineates the end of the definition of the appropriate procedure or block.</span></span> <span data-ttu-id="14448-122">For example, `End Function` terminates the definition of a `Function` procedure.</span><span class="sxs-lookup"><span data-stu-id="14448-122">For example, `End Function` terminates the definition of a `Function` procedure.</span></span>  
  
## <a name="example"></a><span data-ttu-id="14448-123">Exemple</span><span class="sxs-lookup"><span data-stu-id="14448-123">Example</span></span>  
 <span data-ttu-id="14448-124">The following example uses the `End` statement to terminate code execution if the user requests it.</span><span class="sxs-lookup"><span data-stu-id="14448-124">The following example uses the `End` statement to terminate code execution if the user requests it.</span></span>  
  
 [!code-vb[VbVersHelp60Controls#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVersHelp60Controls/VB/Form1.vb#64)]  
  
## <a name="smart-device-developer-notes"></a><span data-ttu-id="14448-125">Smart Device Developer Notes</span><span class="sxs-lookup"><span data-stu-id="14448-125">Smart Device Developer Notes</span></span>  
 <span data-ttu-id="14448-126">This statement is not supported.</span><span class="sxs-lookup"><span data-stu-id="14448-126">This statement is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14448-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="14448-127">See also</span></span>

- <xref:System.Security.Permissions.SecurityPermissionFlag>
- [<span data-ttu-id="14448-128">Stop (instruction)</span><span class="sxs-lookup"><span data-stu-id="14448-128">Stop Statement</span></span>](../../../visual-basic/language-reference/statements/stop-statement.md)
- [<span data-ttu-id="14448-129">End \<keyword> Statement</span><span class="sxs-lookup"><span data-stu-id="14448-129">End \<keyword> Statement</span></span>](../../../visual-basic/language-reference/statements/end-keyword-statement.md)
