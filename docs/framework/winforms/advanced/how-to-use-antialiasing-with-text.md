---
title: 'Procédure : utiliser l’anticrénelage avec du texte'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- strings [Windows Forms], smoothing drawn
- antialiasing [Windows Forms], using with text
- text [Windows Forms], smoothing
- text [Windows Forms], antialiasing
- strings [Windows Forms], antialiasing when drawing
ms.assetid: 48fc34f3-f236-4b01-a0cb-f0752e6d22ae
ms.openlocfilehash: 080d946bd72da8b76ed846efdf149eb328d66336
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67505729"
---
# <a name="how-to-use-antialiasing-with-text"></a><span data-ttu-id="69386-102">Procédure : utiliser l’anticrénelage avec du texte</span><span class="sxs-lookup"><span data-stu-id="69386-102">How to: Use Antialiasing with Text</span></span>
<span data-ttu-id="69386-103">*Anticrénelage* fait référence au lissage de bords dentelés des graphiques dessinés et du texte pour améliorer leur apparence ou la lisibilité.</span><span class="sxs-lookup"><span data-stu-id="69386-103">*Antialiasing* refers to the smoothing of jagged edges of drawn graphics and text to improve their appearance or readability.</span></span> <span data-ttu-id="69386-104">Avec les classes GDI + managés, vous pouvez afficher le texte non crénelé de haute qualité, ainsi que le texte de qualité inférieure.</span><span class="sxs-lookup"><span data-stu-id="69386-104">With the managed GDI+ classes, you can render high quality antialiased text, as well as lower quality text.</span></span> <span data-ttu-id="69386-105">En règle générale, un rendu de qualité supérieur prend plus de temps de traitement que le rendu de qualité inférieure.</span><span class="sxs-lookup"><span data-stu-id="69386-105">Typically, higher quality rendering takes more processing time than lower quality rendering.</span></span> <span data-ttu-id="69386-106">Pour définir le niveau de qualité de texte, définissez la <xref:System.Drawing.Graphics.TextRenderingHint%2A> propriété d’un <xref:System.Drawing.Graphics> à un des éléments de la <xref:System.Drawing.Text.TextRenderingHint> énumération</span><span class="sxs-lookup"><span data-stu-id="69386-106">To set the text quality level, set the <xref:System.Drawing.Graphics.TextRenderingHint%2A> property of a <xref:System.Drawing.Graphics> to one of the elements of the <xref:System.Drawing.Text.TextRenderingHint> enumeration</span></span>  
  
## <a name="example"></a><span data-ttu-id="69386-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="69386-107">Example</span></span>  
 <span data-ttu-id="69386-108">L’exemple de code suivant dessine du texte avec deux paramètres de qualité différents.</span><span class="sxs-lookup"><span data-stu-id="69386-108">The following code example draws text with two different quality settings.</span></span>  
  
 [!code-csharp[System.Drawing.FontsAndText#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.FontsAndText#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#21)]  
 
 <span data-ttu-id="69386-109">L’illustration suivante montre la sortie de l’exemple de code :</span><span class="sxs-lookup"><span data-stu-id="69386-109">The following illustration shows the output of the example code:</span></span>  
  
 ![Capture d’écran qui affiche le texte avec deux paramètres de qualité différents.](./media/how-to-use-antialiasing-with-text/antialiasing-text-quality-settings.png)  
  
## <a name="compiling-the-code"></a><span data-ttu-id="69386-111">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="69386-111">Compiling the Code</span></span>  
 <span data-ttu-id="69386-112">L’exemple de code précédent est conçu pour une utilisation avec Windows Forms et nécessite <xref:System.Windows.Forms.PaintEventArgs> `e`, qui est un paramètre de <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="69386-112">The preceding code example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69386-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="69386-113">See also</span></span>

- [<span data-ttu-id="69386-114">Utilisation de polices et de texte</span><span class="sxs-lookup"><span data-stu-id="69386-114">Using Fonts and Text</span></span>](using-fonts-and-text.md)
