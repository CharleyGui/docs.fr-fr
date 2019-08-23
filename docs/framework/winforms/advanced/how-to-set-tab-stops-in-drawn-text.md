---
title: 'Procédure : définir des taquets de tabulation dans du texte dessiné'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text [Windows Forms], drawing with tab stops
- tabs [Windows Forms], drawn text
ms.assetid: 64878f98-39ba-4303-b63f-0859ab682eeb
ms.openlocfilehash: 8821f6170b8ba588e3197ef54eab14c2719a6cc3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69947820"
---
# <a name="how-to-set-tab-stops-in-drawn-text"></a><span data-ttu-id="37753-102">Procédure : définir des taquets de tabulation dans du texte dessiné</span><span class="sxs-lookup"><span data-stu-id="37753-102">How to: Set Tab Stops in Drawn Text</span></span>
<span data-ttu-id="37753-103">Vous pouvez définir des taquets de tabulation pour le <xref:System.Drawing.StringFormat.SetTabStops%2A> texte en appelant <xref:System.Drawing.StringFormat> la méthode d’un objet <xref:System.Drawing.StringFormat> , puis en <xref:System.Drawing.Graphics.DrawString%2A> passant cet objet <xref:System.Drawing.Graphics> à la méthode de la classe.</span><span class="sxs-lookup"><span data-stu-id="37753-103">You can set tab stops for text by calling the <xref:System.Drawing.StringFormat.SetTabStops%2A> method of a <xref:System.Drawing.StringFormat> object and then passing that <xref:System.Drawing.StringFormat> object to the <xref:System.Drawing.Graphics.DrawString%2A> method of the <xref:System.Drawing.Graphics> class.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="37753-104">Ne <xref:System.Windows.Forms.TextRenderer?displayProperty=nameWithType> prend pas en charge l’ajout de taquets de tabulation au texte dessiné, bien que vous puissiez <xref:System.Windows.Forms.TextFormatFlags.ExpandTabs?displayProperty=nameWithType> développer des taquets de tabulation existants à l’aide de l’indicateur.</span><span class="sxs-lookup"><span data-stu-id="37753-104">The <xref:System.Windows.Forms.TextRenderer?displayProperty=nameWithType> does not support adding tab stops to drawn text, although you can expand existing tab stops using the <xref:System.Windows.Forms.TextFormatFlags.ExpandTabs?displayProperty=nameWithType> flag.</span></span>  
  
## <a name="example"></a><span data-ttu-id="37753-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="37753-105">Example</span></span>  
 <span data-ttu-id="37753-106">L’exemple suivant définit des taquets de tabulation à 150, 250 et 350.</span><span class="sxs-lookup"><span data-stu-id="37753-106">The following example sets tab stops at 150, 250, and 350.</span></span> <span data-ttu-id="37753-107">Ensuite, le code affiche une liste avec onglets de noms et de scores de test.</span><span class="sxs-lookup"><span data-stu-id="37753-107">Then, the code displays a tabbed list of names and test scores.</span></span>  
  
 <span data-ttu-id="37753-108">L’illustration suivante montre le texte avec onglets:</span><span class="sxs-lookup"><span data-stu-id="37753-108">The following illustration shows the tabbed text:</span></span>  
  
 ![Capture d’écran montrant une liste avec onglets de noms et de scores.](./media/how-to-set-tab-stops-in-drawn-text/tab-list-names-test-scores.png)  
  
 <span data-ttu-id="37753-110">Le code suivant passe deux arguments à la <xref:System.Drawing.StringFormat.SetTabStops%2A> méthode.</span><span class="sxs-lookup"><span data-stu-id="37753-110">The following code passes two arguments to the <xref:System.Drawing.StringFormat.SetTabStops%2A> method.</span></span> <span data-ttu-id="37753-111">Le deuxième argument est un tableau qui contient des décalages de tabulation.</span><span class="sxs-lookup"><span data-stu-id="37753-111">The second argument is an array that contains tab offsets.</span></span> <span data-ttu-id="37753-112">Le premier argument passé à <xref:System.Drawing.StringFormat.SetTabStops%2A> est 0, ce qui indique que le premier décalage dans le tableau est mesuré à partir de la position 0, le bord gauche du rectangle englobant.</span><span class="sxs-lookup"><span data-stu-id="37753-112">The first argument passed to <xref:System.Drawing.StringFormat.SetTabStops%2A> is 0, which indicates that the first offset in the array is measured from position 0, the left edge of the bounding rectangle.</span></span>  
  
 [!code-csharp[System.Drawing.FontsAndText#41](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.FontsAndText#41](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#41)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="37753-113">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="37753-113">Compiling the Code</span></span>  
  
- <span data-ttu-id="37753-114">L’exemple précédent est conçu pour une utilisation avec Windows Forms et nécessite <xref:System.Windows.Forms.PaintEventArgs> `e`, qui est un paramètre de <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="37753-114">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37753-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="37753-115">See also</span></span>

- [<span data-ttu-id="37753-116">Utilisation de polices et de texte</span><span class="sxs-lookup"><span data-stu-id="37753-116">Using Fonts and Text</span></span>](using-fonts-and-text.md)
- [<span data-ttu-id="37753-117">Guide pratique : Dessiner du texte avec GDI</span><span class="sxs-lookup"><span data-stu-id="37753-117">How to: Draw Text with GDI</span></span>](how-to-draw-text-with-gdi.md)
