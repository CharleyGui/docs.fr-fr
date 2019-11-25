---
title: 'Comment : réduire et masquer des sections de code'
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic, code collapsing
- Visual Basic, code hiding
- Visual Basic code, collapsing and hiding
ms.assetid: b770e8f5-e07d-491a-ab4b-a977980f9ba2
ms.openlocfilehash: e7aacdc3f41199127b00d276b382ec4a5f258da0
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347407"
---
# <a name="how-to-collapse-and-hide-sections-of-code-visual-basic"></a><span data-ttu-id="68fc6-102">Comment : réduire et masquer des sections de code (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="68fc6-102">How to: Collapse and Hide Sections of Code (Visual Basic)</span></span>

<span data-ttu-id="68fc6-103">The `#Region` directive enables you to collapse and hide sections of code in Visual Basic files.</span><span class="sxs-lookup"><span data-stu-id="68fc6-103">The `#Region` directive enables you to collapse and hide sections of code in Visual Basic files.</span></span> <span data-ttu-id="68fc6-104">The `#Region` directive lets you specify a block of code that you can expand or collapse when using the Visual Studio code editor.</span><span class="sxs-lookup"><span data-stu-id="68fc6-104">The `#Region` directive lets you specify a block of code that you can expand or collapse when using the Visual Studio code editor.</span></span> <span data-ttu-id="68fc6-105">The ability to hide code selectively makes your files more manageable and easier to read.</span><span class="sxs-lookup"><span data-stu-id="68fc6-105">The ability to hide code selectively makes your files more manageable and easier to read.</span></span> <span data-ttu-id="68fc6-106">Pour plus d’informations, voir [Mode Plan](/visualstudio/ide/outlining).</span><span class="sxs-lookup"><span data-stu-id="68fc6-106">For more information, see [Outlining](/visualstudio/ide/outlining).</span></span>

<span data-ttu-id="68fc6-107">`#Region` directives support code block semantics such as `#If...#End If`.</span><span class="sxs-lookup"><span data-stu-id="68fc6-107">`#Region` directives support code block semantics such as `#If...#End If`.</span></span> <span data-ttu-id="68fc6-108">This means they cannot begin in one block and end in another; the start and end must be in the same block.</span><span class="sxs-lookup"><span data-stu-id="68fc6-108">This means they cannot begin in one block and end in another; the start and end must be in the same block.</span></span> <span data-ttu-id="68fc6-109">`#Region` directives are not supported within functions.</span><span class="sxs-lookup"><span data-stu-id="68fc6-109">`#Region` directives are not supported within functions.</span></span>

## <a name="to-collapse-and-hide-a-section-of-code"></a><span data-ttu-id="68fc6-110">To collapse and hide a section of code</span><span class="sxs-lookup"><span data-stu-id="68fc6-110">To collapse and hide a section of code</span></span>

<span data-ttu-id="68fc6-111">Place the section of code between the `#Region` and `#End Region` statements, as in the following example:</span><span class="sxs-lookup"><span data-stu-id="68fc6-111">Place the section of code between the `#Region` and `#End Region` statements, as in the following example:</span></span>

[!code-vb[VbVbalrConditionalComp#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#6)]

<span data-ttu-id="68fc6-112">The `#Region` block can be used multiple times in a code file; thus, users can define their own blocks of procedures and classes that can, in turn, be collapsed.</span><span class="sxs-lookup"><span data-stu-id="68fc6-112">The `#Region` block can be used multiple times in a code file; thus, users can define their own blocks of procedures and classes that can, in turn, be collapsed.</span></span> <span data-ttu-id="68fc6-113">`#Region` blocks can also be nested within other `#Region` blocks.</span><span class="sxs-lookup"><span data-stu-id="68fc6-113">`#Region` blocks can also be nested within other `#Region` blocks.</span></span>

> [!NOTE]
> <span data-ttu-id="68fc6-114">Hiding code does not prevent it from being compiled and does not affect `#If...#End If` statements.</span><span class="sxs-lookup"><span data-stu-id="68fc6-114">Hiding code does not prevent it from being compiled and does not affect `#If...#End If` statements.</span></span>

## <a name="see-also"></a><span data-ttu-id="68fc6-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="68fc6-115">See also</span></span>

- [<span data-ttu-id="68fc6-116">Compilation conditionnelle</span><span class="sxs-lookup"><span data-stu-id="68fc6-116">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
- [<span data-ttu-id="68fc6-117">#Region (directive)</span><span class="sxs-lookup"><span data-stu-id="68fc6-117">#Region Directive</span></span>](../../../visual-basic/language-reference/directives/region-directive.md)
- [<span data-ttu-id="68fc6-118">#If...Then...#Else, directives</span><span class="sxs-lookup"><span data-stu-id="68fc6-118">#If...Then...#Else Directives</span></span>](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
- [<span data-ttu-id="68fc6-119">Mode Plan</span><span class="sxs-lookup"><span data-stu-id="68fc6-119">Outlining</span></span>](/visualstudio/ide/outlining)
