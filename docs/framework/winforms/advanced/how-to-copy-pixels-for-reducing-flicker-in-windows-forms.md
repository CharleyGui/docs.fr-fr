---
title: 'Comment : copier des pixels pour réduire le scintillement'
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
ms.openlocfilehash: 299041e7038d5bd5b9824d668b3f47d842030ac7
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746488"
---
# <a name="how-to-copy-pixels-for-reducing-flicker-in-windows-forms"></a>Comment : copier des pixels pour réduire le scintillement dans les Windows Forms
Lorsque vous animez un graphique simple, les utilisateurs peuvent parfois rencontrer des effets de scintillement ou d’autres effets visuels indésirables. Pour limiter ce problème, il est possible d’utiliser un processus « BitBlt » sur le graphique. BitBlt est le « transfert de bloc de bits » des données de couleur d’un rectangle d’origine de pixels vers un rectangle de destination de pixels.  
  
 Avec Windows Forms, BitBlt s’effectue à l’aide de la méthode <xref:System.Drawing.Graphics.CopyFromScreen%2A> de la classe <xref:System.Drawing.Graphics>. Dans les paramètres de la méthode, vous spécifiez la source et la destination (en tant que points), la taille de la zone à copier et l’objet Graphics utilisé pour dessiner la nouvelle forme.  
  
 Dans l’exemple ci-dessous, une forme est dessinée sur le formulaire dans son gestionnaire d’événements <xref:System.Windows.Forms.Control.Paint>. Ensuite, la méthode <xref:System.Drawing.Graphics.CopyFromScreen%2A> est utilisée pour dupliquer la forme.  
  
> [!NOTE]
> La définition de la propriété <xref:System.Windows.Forms.Control.DoubleBuffered%2A> du formulaire sur `true` fera en sorte que le code basé sur des graphiques dans l’événement <xref:System.Windows.Forms.Control.Paint> soit double tampon. Bien qu’il ne soit pas possible d’obtenir des gains de performances perceptibles lorsque vous utilisez le code ci-dessous, il est à garder à l’esprit quand vous utilisez un code de manipulation graphique plus complexe.  
  
## <a name="example"></a>Exemple  
  
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
 Le code ci-dessus est exécuté dans le gestionnaire d’événements <xref:System.Windows.Forms.Control.Paint> du formulaire afin que les graphiques persistent lorsque le formulaire est redessiné. Par conséquent, n’appelez pas les méthodes graphiques dans le gestionnaire d’événements <xref:System.Windows.Forms.Form.Load>, car le contenu dessiné ne sera pas redessiné si le formulaire est redimensionné ou masqué par un autre formulaire.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Drawing.CopyPixelOperation>
- <xref:System.Drawing.Graphics.FillRectangle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.OnPaint%2A?displayProperty=nameWithType>
- [Graphiques et dessins dans Windows Forms](graphics-and-drawing-in-windows-forms.md)
- [Utilisation d'un stylet pour dessiner des lignes et des formes](using-a-pen-to-draw-lines-and-shapes.md)
