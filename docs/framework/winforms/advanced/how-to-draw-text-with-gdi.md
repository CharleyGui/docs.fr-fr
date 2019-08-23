---
title: 'Procédure : dessiner du texte avec GDI'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- GDI [Windows Forms], drawing text [Windows Forms]
- text [Windows Forms], drawing with TextRenderer
- drawing [Windows Forms], text
- Windows Forms, drawing text with GDI
ms.assetid: 2a19fe5d-2ace-451c-94db-01cb1118ef7b
ms.openlocfilehash: 3ed2b5c94e4a38a5873a34e61287c4038cab5cbb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956540"
---
# <a name="how-to-draw-text-with-gdi"></a><span data-ttu-id="4d45d-102">Procédure : dessiner du texte avec GDI</span><span class="sxs-lookup"><span data-stu-id="4d45d-102">How to: Draw Text with GDI</span></span>
<span data-ttu-id="4d45d-103">Avec la <xref:System.Windows.Forms.TextRenderer.DrawText%2A> méthode de la <xref:System.Windows.Forms.TextRenderer> classe, vous pouvez accéder à la fonctionnalité GDI pour dessiner du texte sur un formulaire ou un contrôle.</span><span class="sxs-lookup"><span data-stu-id="4d45d-103">With the <xref:System.Windows.Forms.TextRenderer.DrawText%2A> method in the <xref:System.Windows.Forms.TextRenderer> class, you can access GDI functionality for drawing text on a form or control.</span></span> <span data-ttu-id="4d45d-104">Le rendu de texte GDI offre généralement de meilleures performances et une mesure de texte plus précise que GDI+.</span><span class="sxs-lookup"><span data-stu-id="4d45d-104">GDI text rendering typically offers better performance and more accurate text measuring than GDI+.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4d45d-105">Les <xref:System.Windows.Forms.TextRenderer.DrawText%2A> méthodes de la <xref:System.Windows.Forms.TextRenderer> classe ne sont pas prises en charge pour l’impression.</span><span class="sxs-lookup"><span data-stu-id="4d45d-105">The <xref:System.Windows.Forms.TextRenderer.DrawText%2A> methods of the <xref:System.Windows.Forms.TextRenderer> class are not supported for printing.</span></span> <span data-ttu-id="4d45d-106">Lors de l’impression, utilisez <xref:System.Drawing.Graphics.DrawString%2A> toujours les méthodes <xref:System.Drawing.Graphics> de la classe.</span><span class="sxs-lookup"><span data-stu-id="4d45d-106">When printing, always use the <xref:System.Drawing.Graphics.DrawString%2A> methods of the <xref:System.Drawing.Graphics> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4d45d-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="4d45d-107">Example</span></span>  
 <span data-ttu-id="4d45d-108">L’exemple de code suivant montre comment dessiner du texte sur plusieurs lignes au sein d’un <xref:System.Windows.Forms.TextRenderer.DrawText%2A> rectangle à l’aide de la méthode.</span><span class="sxs-lookup"><span data-stu-id="4d45d-108">The following code example demonstrates how to draw text on multiple lines within a rectangle using the <xref:System.Windows.Forms.TextRenderer.DrawText%2A> method.</span></span>  
  
 [!code-csharp[System.Windows.Forms.TextRendererExamples#7](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TextRendererExamples/CS/Form1.cs#7)]
 [!code-vb[System.Windows.Forms.TextRendererExamples#7](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TextRendererExamples/VB/Form1.vb#7)]  
  
 <span data-ttu-id="4d45d-109">Pour restituer le texte <xref:System.Windows.Forms.TextRenderer> avec la classe, vous <xref:System.Drawing.IDeviceContext>avez besoin d’un <xref:System.Drawing.Graphics> , <xref:System.Drawing.Font>tel que et un, d’un emplacement pour dessiner le texte et de la couleur dans laquelle il doit être dessiné.</span><span class="sxs-lookup"><span data-stu-id="4d45d-109">To render text with the <xref:System.Windows.Forms.TextRenderer> class, you need an <xref:System.Drawing.IDeviceContext>, such as a <xref:System.Drawing.Graphics> and a <xref:System.Drawing.Font>, a location to draw the text, and the color in which it should be drawn.</span></span> <span data-ttu-id="4d45d-110">Si vous le souhaitez, vous pouvez spécifier la mise en forme du <xref:System.Windows.Forms.TextFormatFlags> texte à l’aide de l’énumération.</span><span class="sxs-lookup"><span data-stu-id="4d45d-110">Optionally, you can specify the text formatting by using the <xref:System.Windows.Forms.TextFormatFlags> enumeration.</span></span>  
  
 <span data-ttu-id="4d45d-111">Pour plus d’informations sur l' <xref:System.Drawing.Graphics>obtention d' [un, consultez Procédure: Créez des objets graphiques pour](how-to-create-graphics-objects-for-drawing.md)le dessin.</span><span class="sxs-lookup"><span data-stu-id="4d45d-111">For more information about obtaining a <xref:System.Drawing.Graphics>, see [How to: Create Graphics Objects for Drawing](how-to-create-graphics-objects-for-drawing.md).</span></span> <span data-ttu-id="4d45d-112">Pour plus d’informations sur la construction <xref:System.Drawing.Font>d’un [, consultez Procédure: Construisez des familles de](how-to-construct-font-families-and-fonts.md)polices et des polices.</span><span class="sxs-lookup"><span data-stu-id="4d45d-112">For more information about constructing a <xref:System.Drawing.Font>, see [How to: Construct Font Families and Fonts](how-to-construct-font-families-and-fonts.md).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="4d45d-113">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="4d45d-113">Compiling the Code</span></span>  
 <span data-ttu-id="4d45d-114">L’exemple de code précédent est conçu pour être utilisé avec Windows Forms, et il <xref:System.Windows.Forms.PaintEventArgs> requiert `e`, qui est un paramètre <xref:System.Windows.Forms.PaintEventHandler>de.</span><span class="sxs-lookup"><span data-stu-id="4d45d-114">The preceding code example is designed for use with Windows Forms, and it requires the <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d45d-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4d45d-115">See also</span></span>

- <xref:System.Windows.Forms.TextRenderer>
- <xref:System.Drawing.Font>
- <xref:System.Drawing.Color>
- [<span data-ttu-id="4d45d-116">Utilisation de polices et de texte</span><span class="sxs-lookup"><span data-stu-id="4d45d-116">Using Fonts and Text</span></span>](using-fonts-and-text.md)
