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
# <a name="how-to-copy-pixels-for-reducing-flicker-in-windows-forms"></a>Comment : copier des pixels pour réduire le scintillement dans les Windows Forms
Lorsque vous animez un graphique simple, les utilisateurs peuvent parfois rencontrer des scintillements ou d’autres effets visuels indésirables. Une façon de limiter ce problème est d’utiliser un processus "bitblt" sur le graphique. Bitblt est le " transfert de bit-bloc " des données de couleur d’un rectangle d’origine de pixels à un rectangle de destination de pixels.  
  
 Avec Windows Forms, bitblt <xref:System.Drawing.Graphics.CopyFromScreen%2A> est accompli <xref:System.Drawing.Graphics> en utilisant la méthode de la classe. Dans les paramètres de la méthode, vous spécifiez la source et la destination (en points), la taille de la zone à copier, et l’objet graphique utilisé pour dessiner la nouvelle forme.  
  
 Dans l’exemple ci-dessous, une forme <xref:System.Windows.Forms.Control.Paint> est dessinée sur la forme dans son gestionnaire d’événements. Ensuite, <xref:System.Drawing.Graphics.CopyFromScreen%2A> la méthode est utilisée pour dupliquer la forme.  
  
> [!NOTE]
> La configuration de <xref:System.Windows.Forms.Control.DoubleBuffered%2A> la `true` propriété du formulaire pour <xref:System.Windows.Forms.Control.Paint> faire du code graphique en cas d’objet sera double tamponnée. Bien que cela n’aura pas de gains de performances perceptibles lors de l’utilisation du code ci-dessous, il est quelque chose à garder à l’esprit lorsque vous travaillez avec des graphiques plus complexes code de manipulation.  
  
## <a name="example"></a> Exemple  
  
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
  
## <a name="compiling-the-code"></a>Compilation du code  
 Le code ci-dessus est <xref:System.Windows.Forms.Control.Paint> exécuté dans le gestionnaire d’événement du formulaire de sorte que les graphiques persistent lorsque le formulaire est redessiné. En tant que tel, n’appelez <xref:System.Windows.Forms.Form.Load> pas les méthodes graphiques liées dans le gestionnaire d’événement, parce que le contenu dessiné ne sera pas redessiné si le formulaire est redimensionné ou obscurci par une autre forme.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Drawing.CopyPixelOperation>
- <xref:System.Drawing.Graphics.FillRectangle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.OnPaint%2A?displayProperty=nameWithType>
- [Graphiques et dessins dans les Windows Forms](graphics-and-drawing-in-windows-forms.md)
- [Utilisation d'un stylet pour dessiner des lignes et des formes](using-a-pen-to-draw-lines-and-shapes.md)
