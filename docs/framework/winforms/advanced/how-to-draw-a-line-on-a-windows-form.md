---
title: 'Comment : dessiner une ligne dans un Windows Form'
description: Découvrez comment dessiner une ligne dans un formulaire en gérant l’événement Paint, puis effectuer le dessin à l’aide de la propriété Graphics de la fonction PaintEventArgs.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
f1_keywords:
- Graphics.DrawLine
helpviewer_keywords:
- examples [Windows Forms], drawing lines on forms
- drawing [Windows Forms], lines
- lines [Windows Forms], drawing
- drawing lines
ms.assetid: 55c1dbeb-75d0-430c-9814-a24b8971ad8c
ms.openlocfilehash: c8e92dc265c63413275561d0e2e3aa820eaec724
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621624"
---
# <a name="how-to-draw-a-line-on-a-windows-form"></a><span data-ttu-id="fa1e4-103">Comment : dessiner une ligne dans un Windows Form</span><span class="sxs-lookup"><span data-stu-id="fa1e4-103">How to: Draw a Line on a Windows Form</span></span>
<span data-ttu-id="fa1e4-104">Cet exemple dessine une ligne dans un formulaire.</span><span class="sxs-lookup"><span data-stu-id="fa1e4-104">This example draws a line on a form.</span></span> <span data-ttu-id="fa1e4-105">En général, lorsque vous dessinez sur un formulaire, vous gérez l' <xref:System.Windows.Forms.Control.Paint> événement du formulaire et effectuez le dessin à l’aide <xref:System.Windows.Forms.PaintEventArgs.Graphics%2A> de la propriété de <xref:System.Windows.Forms.PaintEventArgs> , comme illustré dans cet exemple.</span><span class="sxs-lookup"><span data-stu-id="fa1e4-105">Typically, when you draw on a form, you handle the form’s  <xref:System.Windows.Forms.Control.Paint> event and perform the drawing using the <xref:System.Windows.Forms.PaintEventArgs.Graphics%2A> property of the <xref:System.Windows.Forms.PaintEventArgs>, as shown in this example</span></span>  
  
## <a name="example"></a><span data-ttu-id="fa1e4-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="fa1e4-106">Example</span></span>  
 [!code-csharp[System.Drawing.UsingAPen#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.UsingAPen#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="fa1e4-107">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="fa1e4-107">Compiling the Code</span></span>  
 <span data-ttu-id="fa1e4-108">L'exemple précédent est conçu pour une utilisation avec Windows Forms et nécessite <xref:System.Windows.Forms.PaintEventArgs>`e`, qui est un paramètre du gestionnaire d'événements <xref:System.Windows.Forms.Control.Paint>.</span><span class="sxs-lookup"><span data-stu-id="fa1e4-108">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="fa1e4-109">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="fa1e4-109">Robust Programming</span></span>  
 <span data-ttu-id="fa1e4-110">Vous devez toujours appeler <xref:System.IDisposable.Dispose%2A> sur tous les objets qui consomment des ressources système, tels que les <xref:System.Drawing.Pen> objets.</span><span class="sxs-lookup"><span data-stu-id="fa1e4-110">You should always call <xref:System.IDisposable.Dispose%2A> on any objects that consume system resources, such as <xref:System.Drawing.Pen> objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa1e4-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fa1e4-111">See also</span></span>

- <xref:System.Drawing.Graphics.DrawLine%2A>
- <xref:System.Windows.Forms.Control.OnPaint%2A>
- [<span data-ttu-id="fa1e4-112">Mise en route de la programmation graphique</span><span class="sxs-lookup"><span data-stu-id="fa1e4-112">Getting Started with Graphics Programming</span></span>](getting-started-with-graphics-programming.md)
- [<span data-ttu-id="fa1e4-113">Utilisation d’un stylo pour tracer des lignes et des formes</span><span class="sxs-lookup"><span data-stu-id="fa1e4-113">Using a Pen to Draw Lines and Shapes</span></span>](using-a-pen-to-draw-lines-and-shapes.md)
- [<span data-ttu-id="fa1e4-114">Graphiques et dessins dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="fa1e4-114">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
