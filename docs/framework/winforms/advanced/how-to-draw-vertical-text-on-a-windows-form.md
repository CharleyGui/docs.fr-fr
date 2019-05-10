---
title: 'Procédure : dessiner du texte vertical dans un formulaire Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- StringFormat.FormatFlags
- Graphics.DrawString
helpviewer_keywords:
- text [Windows Forms], drawing vertical
- strings [Windows Forms], drawing vertical
- text [Windows Forms], drawing
- text [Windows Forms], vertical text
ms.assetid: 717a6131-00f6-4373-b574-9894e8317799
ms.openlocfilehash: 660d7abae5463c976e60b7d9caeae8a798d122ca
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64626170"
---
# <a name="how-to-draw-vertical-text-on-a-windows-form"></a><span data-ttu-id="dfb9b-102">Procédure : dessiner du texte vertical dans un formulaire Windows</span><span class="sxs-lookup"><span data-stu-id="dfb9b-102">How to: Draw Vertical Text on a Windows Form</span></span>
<span data-ttu-id="dfb9b-103">L’exemple de code suivant montre comment dessiner du texte vertical dans un formulaire à l’aide de la <xref:System.Drawing.Graphics.DrawString%2A> méthode de <xref:System.Drawing.Graphics>.</span><span class="sxs-lookup"><span data-stu-id="dfb9b-103">The following code example shows how to draw vertical text on a form by using the <xref:System.Drawing.Graphics.DrawString%2A> method of <xref:System.Drawing.Graphics>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dfb9b-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="dfb9b-104">Example</span></span>  
 [!code-cpp[System.Drawing.ConceptualHowTos#8](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#8)]
 [!code-csharp[System.Drawing.ConceptualHowTos#8](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#8)]
 [!code-vb[System.Drawing.ConceptualHowTos#8](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#8)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="dfb9b-105">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="dfb9b-105">Compiling the Code</span></span>  
 <span data-ttu-id="dfb9b-106">Vous ne pouvez pas appeler cette méthode le <xref:System.Windows.Forms.Form.Load> Gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="dfb9b-106">You cannot call this method in the <xref:System.Windows.Forms.Form.Load> event handler.</span></span> <span data-ttu-id="dfb9b-107">Le contenu dessiné ne sera pas redessiné si le formulaire est redimensionné ou masqué par un autre formulaire.</span><span class="sxs-lookup"><span data-stu-id="dfb9b-107">The drawn content will not be redrawn if the form is resized or obscured by another form.</span></span> <span data-ttu-id="dfb9b-108">Pour que votre contenu repeindre automatiquement, vous devez substituer la <xref:System.Windows.Forms.Control.OnPaint%2A> (méthode).</span><span class="sxs-lookup"><span data-stu-id="dfb9b-108">To make your content automatically repaint, you should override the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="dfb9b-109">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="dfb9b-109">Robust Programming</span></span>  
 <span data-ttu-id="dfb9b-110">Les conditions ci-dessous peuvent générer une exception.</span><span class="sxs-lookup"><span data-stu-id="dfb9b-110">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="dfb9b-111">La police Arial n’est pas installée.</span><span class="sxs-lookup"><span data-stu-id="dfb9b-111">The Arial font is not installed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dfb9b-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dfb9b-112">See also</span></span>

- <xref:System.Drawing.Graphics.DrawString%2A>
- <xref:System.Drawing.StringFormat.FormatFlags%2A>
- <xref:System.Drawing.StringFormatFlags>
- <xref:System.Windows.Forms.Control.OnPaint%2A>
- [<span data-ttu-id="dfb9b-113">Mise en route de la programmation graphique</span><span class="sxs-lookup"><span data-stu-id="dfb9b-113">Getting Started with Graphics Programming</span></span>](getting-started-with-graphics-programming.md)
- [<span data-ttu-id="dfb9b-114">Utilisation de polices et de texte</span><span class="sxs-lookup"><span data-stu-id="dfb9b-114">Using Fonts and Text</span></span>](using-fonts-and-text.md)
