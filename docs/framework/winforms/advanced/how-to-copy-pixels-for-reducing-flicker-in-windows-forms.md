---
title: 'Comment: Copier pixels pour réduire Flicker'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- bitblt
- graphics [Windows Forms], copying
- flicker [Windows Forms], reducing in Windows Forms
- graphics [Windows Forms], reducing flicker
- pixels [Windows Forms], copying
- flicker
- bit-block transfer
ms.assetid: 33b76910-13a3-4521-be98-5c097341ae3b
ms.openlocfilehash: a25295532d7123d92bcacc6828d3e8cfcc839d6e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182585"
---
# <a name="how-to-copy-pixels-for-reducing-flicker-in-windows-forms"></a><span data-ttu-id="52ad1-102">Comment : copier des pixels pour réduire le scintillement dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="52ad1-102">How to: Copy Pixels for Reducing Flicker in Windows Forms</span></span>
<span data-ttu-id="52ad1-103">Lorsque vous animez un graphique simple, les utilisateurs peuvent parfois rencontrer des scintillements ou d’autres effets visuels indésirables.</span><span class="sxs-lookup"><span data-stu-id="52ad1-103">When you animate a simple graphic, users can sometimes encounter flicker or other undesirable visual effects.</span></span> <span data-ttu-id="52ad1-104">Une façon de limiter ce problème est d’utiliser un processus "bitblt" sur le graphique.</span><span class="sxs-lookup"><span data-stu-id="52ad1-104">One way to limit this problem is to use a "bitblt" process on the graphic.</span></span> <span data-ttu-id="52ad1-105">Bitblt est le " transfert de bit-bloc " des données de couleur d’un rectangle d’origine de pixels à un rectangle de destination de pixels.</span><span class="sxs-lookup"><span data-stu-id="52ad1-105">Bitblt is the "bit-block transfer" of the color data from an origin rectangle of pixels to a destination rectangle of pixels.</span></span>  
  
 <span data-ttu-id="52ad1-106">Avec Windows Forms, bitblt <xref:System.Drawing.Graphics.CopyFromScreen%2A> est accompli <xref:System.Drawing.Graphics> en utilisant la méthode de la classe.</span><span class="sxs-lookup"><span data-stu-id="52ad1-106">With Windows Forms, bitblt is accomplished using the <xref:System.Drawing.Graphics.CopyFromScreen%2A> method of the <xref:System.Drawing.Graphics> class.</span></span> <span data-ttu-id="52ad1-107">Dans les paramètres de la méthode, vous spécifiez la source et la destination (en points), la taille de la zone à copier, et l’objet graphique utilisé pour dessiner la nouvelle forme.</span><span class="sxs-lookup"><span data-stu-id="52ad1-107">In the parameters of the method, you specify the source and destination (as points), the size of the area to be copied, and the graphics object used to draw the new shape.</span></span>  
  
 <span data-ttu-id="52ad1-108">Dans l’exemple ci-dessous, une forme <xref:System.Windows.Forms.Control.Paint> est dessinée sur la forme dans son gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="52ad1-108">In the example below, a shape is drawn on the form in its <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="52ad1-109">Ensuite, <xref:System.Drawing.Graphics.CopyFromScreen%2A> la méthode est utilisée pour dupliquer la forme.</span><span class="sxs-lookup"><span data-stu-id="52ad1-109">Then, the <xref:System.Drawing.Graphics.CopyFromScreen%2A> method is used to duplicate the shape.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="52ad1-110">La configuration de <xref:System.Windows.Forms.Control.DoubleBuffered%2A> la `true` propriété du formulaire pour <xref:System.Windows.Forms.Control.Paint> faire du code graphique en cas d’objet sera double tamponnée.</span><span class="sxs-lookup"><span data-stu-id="52ad1-110">Setting the form's <xref:System.Windows.Forms.Control.DoubleBuffered%2A> property to `true` will make graphics-based code in the <xref:System.Windows.Forms.Control.Paint> event be double-buffered.</span></span> <span data-ttu-id="52ad1-111">Bien que cela n’aura pas de gains de performances perceptibles lors de l’utilisation du code ci-dessous, il est quelque chose à garder à l’esprit lorsque vous travaillez avec des graphiques plus complexes code de manipulation.</span><span class="sxs-lookup"><span data-stu-id="52ad1-111">While this will not have any discernible performance gains when using the code below, it is something to keep in mind when working with more complex graphics-manipulation code.</span></span>  
  
## <a name="example"></a><span data-ttu-id="52ad1-112"> Exemple</span><span class="sxs-lookup"><span data-stu-id="52ad1-112">Example</span></span>  
  
```vb  
Private Sub Form1_Paint(ByVal sender As Object, ByVal e As _  
    System.Windows.Forms.PaintEventArgs) Handles MyBase.Paint  
    ' Draw a circle with a bar on top.  
        e.Graphics.FillEllipse(Brushes.DarkBlue, New Rectangle _  
             (10, 10, 60, 60))  
        e.Graphics.FillRectangle(Brushes.Khaki, New Rectangle _  
             (20, 30, 60, 10))  
    ' Copy the graphic to a new location.  
        e.Graphics.CopyFromScreen(New Point(10, 10), New Point _  
             (100, 100), New Size(70, 70))  
End Sub  
```  
  
```csharp  
private void Form1_Paint(System.Object sender,  
    System.Windows.Forms.PaintEventArgs e)  
        {  
        e.Graphics.FillEllipse(Brushes.DarkBlue, new  
            Rectangle(10,10,60,60));  
        e.Graphics.FillRectangle(Brushes.Khaki, new  
            Rectangle(20,30,60,10));  
        e.Graphics.CopyFromScreen(new Point(10, 10), new Point(100, 100),
            new Size(70, 70));  
}  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="52ad1-113">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="52ad1-113">Compiling the Code</span></span>  
 <span data-ttu-id="52ad1-114">Le code ci-dessus est <xref:System.Windows.Forms.Control.Paint> exécuté dans le gestionnaire d’événement du formulaire de sorte que les graphiques persistent lorsque le formulaire est redessiné.</span><span class="sxs-lookup"><span data-stu-id="52ad1-114">The code above is run in the form's <xref:System.Windows.Forms.Control.Paint> event handler so that the graphics persist when the form is redrawn.</span></span> <span data-ttu-id="52ad1-115">En tant que tel, n’appelez <xref:System.Windows.Forms.Form.Load> pas les méthodes graphiques liées dans le gestionnaire d’événement, parce que le contenu dessiné ne sera pas redessiné si le formulaire est redimensionné ou obscurci par une autre forme.</span><span class="sxs-lookup"><span data-stu-id="52ad1-115">As such, do not call graphics-related methods in the <xref:System.Windows.Forms.Form.Load> event handler, because the drawn content will not be redrawn if the form is resized or obscured by another form.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52ad1-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="52ad1-116">See also</span></span>

- <xref:System.Drawing.CopyPixelOperation>
- <xref:System.Drawing.Graphics.FillRectangle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.OnPaint%2A?displayProperty=nameWithType>
- [<span data-ttu-id="52ad1-117">Graphiques et dessins dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="52ad1-117">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="52ad1-118">Utilisation d'un stylet pour dessiner des lignes et des formes</span><span class="sxs-lookup"><span data-stu-id="52ad1-118">Using a Pen to Draw Lines and Shapes</span></span>](using-a-pen-to-draw-lines-and-shapes.md)
