---
title: 'Procédure : dessiner du texte à un emplacement spécifié'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text [Windows Forms], drawing at specified locations [Windows Forms]
- drawing text
- drawing text [Windows Forms], specified locations [Windows Forms]
- Windows Forms, drawing text at a specified location
ms.assetid: 60816423-1c38-465e-980d-2c2b64d74086
ms.openlocfilehash: 0c36b00e4f6f71f0ecf8042853bb8e99e57854da
ms.sourcegitcommit: e08b319358a8025cc6aa38737854f7bdb87183d6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/29/2019
ms.locfileid: "64912426"
---
# <a name="how-to-draw-text-at-a-specified-location"></a><span data-ttu-id="40ad7-102">Procédure : dessiner du texte à un emplacement spécifié</span><span class="sxs-lookup"><span data-stu-id="40ad7-102">How to: Draw Text at a Specified Location</span></span>
<span data-ttu-id="40ad7-103">Lorsque vous effectuez un dessin personnalisé, vous pouvez dessiner du texte dans une seule ligne horizontale, en commençant à un point spécifié.</span><span class="sxs-lookup"><span data-stu-id="40ad7-103">When you perform custom drawing, you can draw text in a single horizontal line starting at a specified point.</span></span> <span data-ttu-id="40ad7-104">Vous pouvez dessiner du texte de cette manière à l’aide de la <xref:System.Drawing.Graphics.DrawString%2A> surchargées de la <xref:System.Drawing.Graphics> classe qui prend un <xref:System.Drawing.Point> ou <xref:System.Drawing.PointF> paramètre.</span><span class="sxs-lookup"><span data-stu-id="40ad7-104">You can draw text in this manner by using the <xref:System.Drawing.Graphics.DrawString%2A> overloaded method of the <xref:System.Drawing.Graphics> class that takes a <xref:System.Drawing.Point> or <xref:System.Drawing.PointF> parameter.</span></span> <span data-ttu-id="40ad7-105">Le <xref:System.Drawing.Graphics.DrawString%2A> méthode requiert également un <xref:System.Drawing.Brush> et <xref:System.Drawing.Font></span><span class="sxs-lookup"><span data-stu-id="40ad7-105">The <xref:System.Drawing.Graphics.DrawString%2A> method also requires a <xref:System.Drawing.Brush> and <xref:System.Drawing.Font></span></span>  
  
 <span data-ttu-id="40ad7-106">Vous pouvez également utiliser le <xref:System.Windows.Forms.TextRenderer.DrawText%2A> surchargées de la <xref:System.Windows.Forms.TextRenderer> qui accepte un <xref:System.Drawing.Point>.</span><span class="sxs-lookup"><span data-stu-id="40ad7-106">You can also use the <xref:System.Windows.Forms.TextRenderer.DrawText%2A> overloaded method of the <xref:System.Windows.Forms.TextRenderer> that takes a <xref:System.Drawing.Point>.</span></span> <span data-ttu-id="40ad7-107"><xref:System.Windows.Forms.TextRenderer.DrawText%2A> requiert également un <xref:System.Drawing.Color> et un <xref:System.Drawing.Font>.</span><span class="sxs-lookup"><span data-stu-id="40ad7-107"><xref:System.Windows.Forms.TextRenderer.DrawText%2A> also requires a <xref:System.Drawing.Color> and a <xref:System.Drawing.Font>.</span></span>  
  
 <span data-ttu-id="40ad7-108">L’illustration suivante montre la sortie du texte dessiné à un point spécifié lorsque vous utilisez le <xref:System.Drawing.Graphics.DrawString%2A> la méthode surchargée.</span><span class="sxs-lookup"><span data-stu-id="40ad7-108">The following illustration shows the output of text drawn at a specified point when you use the <xref:System.Drawing.Graphics.DrawString%2A> overloaded method.</span></span>  
  
 ![Capture d’écran montrant la sortie de texte à un point spécifié.](./media/how-to-draw-text-at-a-specified-location/font-text-specified-point.png)  
  
### <a name="to-draw-a-line-of-text-with-gdi"></a><span data-ttu-id="40ad7-110">Pour dessiner une ligne de texte avec GDI +</span><span class="sxs-lookup"><span data-stu-id="40ad7-110">To draw a line of text with GDI+</span></span>  
  
1. <span data-ttu-id="40ad7-111">Utilisez le <xref:System.Drawing.Graphics.DrawString%2A> méthode, en passant le texte que vous le souhaitez, <xref:System.Drawing.Point> ou <xref:System.Drawing.PointF>, <xref:System.Drawing.Font>, et <xref:System.Drawing.Brush>.</span><span class="sxs-lookup"><span data-stu-id="40ad7-111">Use the <xref:System.Drawing.Graphics.DrawString%2A> method, passing the text you want, <xref:System.Drawing.Point> or <xref:System.Drawing.PointF>, <xref:System.Drawing.Font>, and <xref:System.Drawing.Brush>.</span></span>  
  
     [!code-csharp[System.Drawing.AlignDrawnText#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#30)]
     [!code-vb[System.Drawing.AlignDrawnText#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#30)]  
  
### <a name="to-draw-a-line-of-text-with-gdi"></a><span data-ttu-id="40ad7-112">Pour dessiner une ligne de texte avec GDI</span><span class="sxs-lookup"><span data-stu-id="40ad7-112">To draw a line of text with GDI</span></span>  
  
1. <span data-ttu-id="40ad7-113">Utilisez le <xref:System.Windows.Forms.TextRenderer.DrawText%2A> méthode, en passant le texte que vous le souhaitez, <xref:System.Drawing.Point>, <xref:System.Drawing.Font>, et <xref:System.Drawing.Color>.</span><span class="sxs-lookup"><span data-stu-id="40ad7-113">Use the <xref:System.Windows.Forms.TextRenderer.DrawText%2A> method, passing the text you want, <xref:System.Drawing.Point>, <xref:System.Drawing.Font>, and <xref:System.Drawing.Color>.</span></span>  
  
     [!code-csharp[System.Drawing.AlignDrawnText#40](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#40)]
     [!code-vb[System.Drawing.AlignDrawnText#40](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#40)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="40ad7-114">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="40ad7-114">Compiling the Code</span></span>  
 <span data-ttu-id="40ad7-115">Les exemples précédents nécessitent :</span><span class="sxs-lookup"><span data-stu-id="40ad7-115">The previous examples require:</span></span>  
  
- <span data-ttu-id="40ad7-116"><xref:System.Windows.Forms.PaintEventArgs>  `e`, qui est un paramètre de <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="40ad7-116"><xref:System.Windows.Forms.PaintEventArgs>  `e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40ad7-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="40ad7-117">See also</span></span>

- [<span data-ttu-id="40ad7-118">Guide pratique pour Dessiner du texte avec GDI</span><span class="sxs-lookup"><span data-stu-id="40ad7-118">How to: Draw Text with GDI</span></span>](how-to-draw-text-with-gdi.md)
- [<span data-ttu-id="40ad7-119">Utilisation de polices et de texte</span><span class="sxs-lookup"><span data-stu-id="40ad7-119">Using Fonts and Text</span></span>](using-fonts-and-text.md)
- [<span data-ttu-id="40ad7-120">Guide pratique pour Construire des familles de polices et des polices</span><span class="sxs-lookup"><span data-stu-id="40ad7-120">How to: Construct Font Families and Fonts</span></span>](how-to-construct-font-families-and-fonts.md)
- [<span data-ttu-id="40ad7-121">Guide pratique pour Dessiner du texte encapsulé dans un Rectangle</span><span class="sxs-lookup"><span data-stu-id="40ad7-121">How to: Draw Wrapped Text in a Rectangle</span></span>](how-to-draw-wrapped-text-in-a-rectangle.md)
