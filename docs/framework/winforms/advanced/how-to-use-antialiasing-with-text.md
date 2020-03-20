---
title: 'Comment : utiliser l‘anticrénelage avec du texte'
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
ms.openlocfilehash: 632ed329173d134495a424b34ca7c71e402607bf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182485"
---
# <a name="how-to-use-antialiasing-with-text"></a><span data-ttu-id="95bf2-102">Comment : utiliser l‘anticrénelage avec du texte</span><span class="sxs-lookup"><span data-stu-id="95bf2-102">How to: Use Antialiasing with Text</span></span>
<span data-ttu-id="95bf2-103">*Antialiasing* fait référence au lissage des bords déchiquetés de graphiques et de textes dessinés pour améliorer leur apparence ou leur lisibilité.</span><span class="sxs-lookup"><span data-stu-id="95bf2-103">*Antialiasing* refers to the smoothing of jagged edges of drawn graphics and text to improve their appearance or readability.</span></span> <span data-ttu-id="95bf2-104">Avec les classes GDI GÉRÉEs, vous pouvez rendre du texte antialiased de haute qualité, ainsi que du texte de qualité inférieure.</span><span class="sxs-lookup"><span data-stu-id="95bf2-104">With the managed GDI+ classes, you can render high quality antialiased text, as well as lower quality text.</span></span> <span data-ttu-id="95bf2-105">Typiquement, un rendu de meilleure qualité prend plus de temps de traitement que le rendu de qualité inférieure.</span><span class="sxs-lookup"><span data-stu-id="95bf2-105">Typically, higher quality rendering takes more processing time than lower quality rendering.</span></span> <span data-ttu-id="95bf2-106">Pour définir le niveau de <xref:System.Drawing.Graphics.TextRenderingHint%2A> qualité <xref:System.Drawing.Graphics> du texte, définissez <xref:System.Drawing.Text.TextRenderingHint> la propriété d’un élément de l’énumération</span><span class="sxs-lookup"><span data-stu-id="95bf2-106">To set the text quality level, set the <xref:System.Drawing.Graphics.TextRenderingHint%2A> property of a <xref:System.Drawing.Graphics> to one of the elements of the <xref:System.Drawing.Text.TextRenderingHint> enumeration</span></span>  
  
## <a name="example"></a><span data-ttu-id="95bf2-107"> Exemple</span><span class="sxs-lookup"><span data-stu-id="95bf2-107">Example</span></span>  
 <span data-ttu-id="95bf2-108">L’exemple de code suivant dessine du texte avec deux paramètres de qualité différents.</span><span class="sxs-lookup"><span data-stu-id="95bf2-108">The following code example draws text with two different quality settings.</span></span>  
  
 [!code-csharp[System.Drawing.FontsAndText#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.FontsAndText#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#21)]  

 <span data-ttu-id="95bf2-109">L’illustration suivante montre la sortie du code d’exemple :</span><span class="sxs-lookup"><span data-stu-id="95bf2-109">The following illustration shows the output of the example code:</span></span>  
  
 ![Capture d’écran qui montre le texte avec deux paramètres de qualité différents.](./media/how-to-use-antialiasing-with-text/antialiasing-text-quality-settings.png)  
  
## <a name="compiling-the-code"></a><span data-ttu-id="95bf2-111">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="95bf2-111">Compiling the Code</span></span>  
 <span data-ttu-id="95bf2-112">L’exemple de code précédent est conçu pour <xref:System.Windows.Forms.PaintEventArgs> `e`une utilisation avec <xref:System.Windows.Forms.PaintEventHandler>windows Forms, et il nécessite , qui est un paramètre de .</span><span class="sxs-lookup"><span data-stu-id="95bf2-112">The preceding code example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95bf2-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="95bf2-113">See also</span></span>

- [<span data-ttu-id="95bf2-114">Utilisation de polices et de texte</span><span class="sxs-lookup"><span data-stu-id="95bf2-114">Using Fonts and Text</span></span>](using-fonts-and-text.md)
