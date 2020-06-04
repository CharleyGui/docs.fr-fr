---
title: 'Procédure : Réduire et masquer des sections de code'
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic, code collapsing
- Visual Basic, code hiding
- Visual Basic code, collapsing and hiding
ms.assetid: b770e8f5-e07d-491a-ab4b-a977980f9ba2
ms.openlocfilehash: c11affe9c4dd4251ba8ff4b87029d314970b5fcb
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404847"
---
# <a name="how-to-collapse-and-hide-sections-of-code-visual-basic"></a><span data-ttu-id="83577-102">Comment : réduire et masquer des sections de code (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="83577-102">How to: Collapse and Hide Sections of Code (Visual Basic)</span></span>

<span data-ttu-id="83577-103">La `#Region` directive vous permet de réduire et de masquer des sections de code dans des fichiers de Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="83577-103">The `#Region` directive enables you to collapse and hide sections of code in Visual Basic files.</span></span> <span data-ttu-id="83577-104">La `#Region` directive vous permet de spécifier un bloc de code que vous pouvez développer ou réduire lors de l’utilisation de l’éditeur de code Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="83577-104">The `#Region` directive lets you specify a block of code that you can expand or collapse when using the Visual Studio code editor.</span></span> <span data-ttu-id="83577-105">La possibilité de masquer le code de manière sélective rend vos fichiers plus gérables et plus faciles à lire.</span><span class="sxs-lookup"><span data-stu-id="83577-105">The ability to hide code selectively makes your files more manageable and easier to read.</span></span> <span data-ttu-id="83577-106">Pour plus d’informations, voir [Mode Plan](/visualstudio/ide/outlining).</span><span class="sxs-lookup"><span data-stu-id="83577-106">For more information, see [Outlining](/visualstudio/ide/outlining).</span></span>

<span data-ttu-id="83577-107">`#Region`les directives prennent en charge la sémantique de bloc de code telle que `#If...#End If` .</span><span class="sxs-lookup"><span data-stu-id="83577-107">`#Region` directives support code block semantics such as `#If...#End If`.</span></span> <span data-ttu-id="83577-108">Cela signifie qu’ils ne peuvent pas commencer dans un bloc et se terminer dans un autre ; le début et la fin doivent se trouver dans le même bloc.</span><span class="sxs-lookup"><span data-stu-id="83577-108">This means they cannot begin in one block and end in another; the start and end must be in the same block.</span></span> <span data-ttu-id="83577-109">`#Region`les directives ne sont pas prises en charge dans les fonctions.</span><span class="sxs-lookup"><span data-stu-id="83577-109">`#Region` directives are not supported within functions.</span></span>

## <a name="to-collapse-and-hide-a-section-of-code"></a><span data-ttu-id="83577-110">Pour réduire et masquer une section de code</span><span class="sxs-lookup"><span data-stu-id="83577-110">To collapse and hide a section of code</span></span>

<span data-ttu-id="83577-111">Placez la section de code entre les `#Region` `#End Region` instructions et, comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="83577-111">Place the section of code between the `#Region` and `#End Region` statements, as in the following example:</span></span>

[!code-vb[VbVbalrConditionalComp#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#6)]

<span data-ttu-id="83577-112">Le `#Region` bloc peut être utilisé plusieurs fois dans un fichier de code. ainsi, les utilisateurs peuvent définir leurs propres blocs de procédures et de classes qui peuvent, à leur tour, être réduits.</span><span class="sxs-lookup"><span data-stu-id="83577-112">The `#Region` block can be used multiple times in a code file; thus, users can define their own blocks of procedures and classes that can, in turn, be collapsed.</span></span> <span data-ttu-id="83577-113">`#Region`les blocs peuvent également être imbriqués dans d’autres `#Region` blocs.</span><span class="sxs-lookup"><span data-stu-id="83577-113">`#Region` blocks can also be nested within other `#Region` blocks.</span></span>

> [!NOTE]
> <span data-ttu-id="83577-114">Le masquage du code ne l’empêche pas de le compiler et n’affecte pas les `#If...#End If` instructions.</span><span class="sxs-lookup"><span data-stu-id="83577-114">Hiding code does not prevent it from being compiled and does not affect `#If...#End If` statements.</span></span>

## <a name="see-also"></a><span data-ttu-id="83577-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="83577-115">See also</span></span>

- [<span data-ttu-id="83577-116">Compilation conditionnelle</span><span class="sxs-lookup"><span data-stu-id="83577-116">Conditional Compilation</span></span>](conditional-compilation.md)
- [<span data-ttu-id="83577-117">#Region directive</span><span class="sxs-lookup"><span data-stu-id="83577-117">#Region Directive</span></span>](../../language-reference/directives/region-directive.md)
- [<span data-ttu-id="83577-118">#If... Then... #Else directives</span><span class="sxs-lookup"><span data-stu-id="83577-118">#If...Then...#Else Directives</span></span>](../../language-reference/directives/if-then-else-directives.md)
- [<span data-ttu-id="83577-119">mode Plan</span><span class="sxs-lookup"><span data-stu-id="83577-119">Outlining</span></span>](/visualstudio/ide/outlining)
