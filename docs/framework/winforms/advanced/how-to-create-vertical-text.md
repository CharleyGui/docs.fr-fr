---
title: 'Comment : créer du texte vertical'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text [Windows Forms], drawing vertical
- Windows Forms, drawing vertical text
- strings [Windows Forms], drawing vertical
- vertical text [Windows Forms], drawing
ms.assetid: 50c69046-4188-47d9-b949-cc2610ffd337
ms.openlocfilehash: 86401342625f593945b801f7619ef9ca9681317c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182557"
---
# <a name="how-to-create-vertical-text"></a><span data-ttu-id="d74db-102">Comment : créer du texte vertical</span><span class="sxs-lookup"><span data-stu-id="d74db-102">How to: Create Vertical Text</span></span>
<span data-ttu-id="d74db-103">Vous pouvez <xref:System.Drawing.StringFormat> utiliser un objet pour spécifier que le texte soit dessiné verticalement plutôt qu’horizontalement.</span><span class="sxs-lookup"><span data-stu-id="d74db-103">You can use a <xref:System.Drawing.StringFormat> object to specify that text be drawn vertically rather than horizontally.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d74db-104"> Exemple</span><span class="sxs-lookup"><span data-stu-id="d74db-104">Example</span></span>  
 <span data-ttu-id="d74db-105">L’exemple suivant attribue <xref:System.Drawing.StringFormatFlags.DirectionVertical> la <xref:System.Drawing.StringFormat.FormatFlags%2A> valeur <xref:System.Drawing.StringFormat> à la propriété d’un objet.</span><span class="sxs-lookup"><span data-stu-id="d74db-105">The following example assigns the value <xref:System.Drawing.StringFormatFlags.DirectionVertical> to the <xref:System.Drawing.StringFormat.FormatFlags%2A> property of a <xref:System.Drawing.StringFormat> object.</span></span> <span data-ttu-id="d74db-106">Cet <xref:System.Drawing.StringFormat> objet est <xref:System.Drawing.Graphics.DrawString%2A> transmis à <xref:System.Drawing.Graphics> la méthode de la classe.</span><span class="sxs-lookup"><span data-stu-id="d74db-106">That <xref:System.Drawing.StringFormat> object is passed to the <xref:System.Drawing.Graphics.DrawString%2A> method of the <xref:System.Drawing.Graphics> class.</span></span> <span data-ttu-id="d74db-107">La <xref:System.Drawing.StringFormatFlags.DirectionVertical> valeur est un <xref:System.Drawing.StringFormatFlags> membre de l’énumération.</span><span class="sxs-lookup"><span data-stu-id="d74db-107">The value <xref:System.Drawing.StringFormatFlags.DirectionVertical> is a member of the <xref:System.Drawing.StringFormatFlags> enumeration.</span></span>  
  
 <span data-ttu-id="d74db-108">L’illustration suivante montre le texte vertical :</span><span class="sxs-lookup"><span data-stu-id="d74db-108">The following illustration shows the vertical text:</span></span>
  
 ![Graphique qui montre le texte vertical de police.](./media/how-to-create-vertical-text/vertical-font-text-graphic.png)  
  
 [!code-csharp[System.Drawing.FontsAndText#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.FontsAndText#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d74db-110">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="d74db-110">Compiling the Code</span></span>  
  
- <span data-ttu-id="d74db-111">L’exemple précédent est conçu pour une <xref:System.Windows.Forms.PaintEventArgs> `e` utilisation avec windows <xref:System.Windows.Forms.PaintEventHandler>Forms, et il nécessite , qui est un paramètre de .</span><span class="sxs-lookup"><span data-stu-id="d74db-111">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e` , which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d74db-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d74db-112">See also</span></span>

- [<span data-ttu-id="d74db-113">Comment : écrire du texte avec GDI</span><span class="sxs-lookup"><span data-stu-id="d74db-113">How to: Draw Text with GDI</span></span>](how-to-draw-text-with-gdi.md)
