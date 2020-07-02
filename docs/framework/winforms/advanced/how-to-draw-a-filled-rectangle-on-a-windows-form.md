---
title: 'Comment : dessiner un rectangle rempli dans un Windows Form'
description: Apprenez à dessiner par programmation un rectangle plein dans un Windows Form. En savoir plus sur la compilation de votre code.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- Graphics.FillRectangle
helpviewer_keywords:
- drawing [Windows Forms], rectangles
- rectangles [Windows Forms], drawing
- drawing rectangles
ms.assetid: d656a93c-987d-4809-aafd-493fe17450f0
ms.openlocfilehash: 0ad8ec97000e29b2194a9eda713aa43d5557b44c
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621637"
---
# <a name="how-to-draw-a-filled-rectangle-on-a-windows-form"></a><span data-ttu-id="ae1ef-104">Comment : dessiner un rectangle rempli dans un Windows Form</span><span class="sxs-lookup"><span data-stu-id="ae1ef-104">How to: Draw a Filled Rectangle on a Windows Form</span></span>
<span data-ttu-id="ae1ef-105">Cet exemple dessine un rectangle plein dans un formulaire.</span><span class="sxs-lookup"><span data-stu-id="ae1ef-105">This example draws a filled rectangle on a form.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ae1ef-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="ae1ef-106">Example</span></span>  
 [!code-cpp[System.Drawing.ConceptualHowTos#2](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#2)]
 [!code-csharp[System.Drawing.ConceptualHowTos#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#2)]
 [!code-vb[System.Drawing.ConceptualHowTos#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#2)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ae1ef-107">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="ae1ef-107">Compiling the Code</span></span>  
 <span data-ttu-id="ae1ef-108">Vous ne pouvez pas appeler cette méthode dans le <xref:System.Windows.Forms.Form.Load> Gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="ae1ef-108">You cannot call this method in the <xref:System.Windows.Forms.Form.Load> event handler.</span></span> <span data-ttu-id="ae1ef-109">Le contenu dessiné ne sera pas redessiné si le formulaire est redimensionné ou masqué par un autre formulaire.</span><span class="sxs-lookup"><span data-stu-id="ae1ef-109">The drawn content will not be redrawn if the form is resized or obscured by another form.</span></span> <span data-ttu-id="ae1ef-110">Pour que votre contenu se redessine automatiquement, vous devez remplacer la <xref:System.Windows.Forms.Control.OnPaint%2A> méthode.</span><span class="sxs-lookup"><span data-stu-id="ae1ef-110">To make your content automatically repaint, you should override the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="ae1ef-111">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="ae1ef-111">Robust Programming</span></span>  
 <span data-ttu-id="ae1ef-112">Vous devez toujours appeler <xref:System.IDisposable.Dispose%2A> sur tous les objets qui consomment des ressources système, tels que les <xref:System.Drawing.Brush> <xref:System.Drawing.Graphics> objets et.</span><span class="sxs-lookup"><span data-stu-id="ae1ef-112">You should always call <xref:System.IDisposable.Dispose%2A> on any objects that consume system resources, such as <xref:System.Drawing.Brush> and <xref:System.Drawing.Graphics> objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae1ef-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ae1ef-113">See also</span></span>

- <xref:System.Drawing.Graphics.FillRectangle%2A>
- <xref:System.Windows.Forms.Control.OnPaint%2A>
- [<span data-ttu-id="ae1ef-114">Mise en route de la programmation graphique</span><span class="sxs-lookup"><span data-stu-id="ae1ef-114">Getting Started with Graphics Programming</span></span>](getting-started-with-graphics-programming.md)
- [<span data-ttu-id="ae1ef-115">Graphiques et dessins dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ae1ef-115">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="ae1ef-116">Utilisation d’un stylo pour tracer des lignes et des formes</span><span class="sxs-lookup"><span data-stu-id="ae1ef-116">Using a Pen to Draw Lines and Shapes</span></span>](using-a-pen-to-draw-lines-and-shapes.md)
- [<span data-ttu-id="ae1ef-117">Pinceaux et remplissage de formes dans GDI+</span><span class="sxs-lookup"><span data-stu-id="ae1ef-117">Brushes and Filled Shapes in GDI+</span></span>](brushes-and-filled-shapes-in-gdi.md)
