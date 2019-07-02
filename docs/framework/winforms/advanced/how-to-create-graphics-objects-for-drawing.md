---
title: 'Procédure : créer des objets de graphismes pour le dessin'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- graphics [Windows Forms], creating
- images [Windows Forms], creating
- GDI+, creating images
ms.assetid: 162861f9-f050-445e-8abb-b2c43a918b8b
ms.openlocfilehash: ee57b0409d7bb7574c965ff098e7f86c8332536d
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67505503"
---
# <a name="how-to-create-graphics-objects-for-drawing"></a>Procédure : créer des objets de graphismes pour le dessin
Avant que vous pouvez dessiner des lignes et des formes, rendre du texte ou afficher et manipuler des images avec GDI +, vous devez créer un <xref:System.Drawing.Graphics> objet. Le <xref:System.Drawing.Graphics> objet représente une surface de dessin GDI + et est l’objet qui est utilisé pour créer des images graphiques.  
  
 Il existe deux étapes dans l’utilisation de graphiques :  
  
1. Création d’un <xref:System.Drawing.Graphics> objet.  
  
2. À l’aide de la <xref:System.Drawing.Graphics> objet pour dessiner des lignes et des formes, de rendre du texte ou d’afficher et de manipuler des images.  
  
## <a name="creating-a-graphics-object"></a>Création d’un objet Graphics  
 Un objet graphics peut être créé de plusieurs façons.  
  
#### <a name="to-create-a-graphics-object"></a>Pour créer un objet graphics  
  
- Reçoivent une référence à un objet graphique dans le cadre de la <xref:System.Windows.Forms.PaintEventArgs> dans le <xref:System.Windows.Forms.Control.Paint> événement d’un formulaire ou contrôle. C’est généralement utilisée pour obtenir une référence à un objet graphique lors de la création du code de peinture d’un contrôle. De même, vous pouvez également obtenir un objet graphique en tant que propriété de la <xref:System.Drawing.Printing.PrintPageEventArgs> lors du traitement de la <xref:System.Drawing.Printing.PrintDocument.PrintPage> événement pour un <xref:System.Drawing.Printing.PrintDocument>.  
  
     ou  
  
- Appelez le <xref:System.Windows.Forms.Control.CreateGraphics%2A> méthode d’un contrôle ou un formulaire afin d’obtenir une référence à un <xref:System.Drawing.Graphics> objet qui représente la surface de dessin de ce contrôle ou formulaire. Utilisez cette méthode si vous souhaitez dessiner sur un formulaire ou un contrôle qui existe déjà.  
  
     ou  
  
- Créer un <xref:System.Drawing.Graphics> objet à partir de n’importe quel objet qui hérite de <xref:System.Drawing.Image>. Cette approche est utile lorsque vous souhaitez modifier une image existante.  
  
     Les sections suivantes fournissent plus d’informations sur chacun de ces processus.  
  
## <a name="painteventargs-in-the-paint-event-handler"></a>PaintEventArgs dans le Gestionnaire d’événements Paint  
 Lorsque vous programmez le <xref:System.Windows.Forms.PaintEventHandler> pour les contrôles ou le <xref:System.Drawing.Printing.PrintDocument.PrintPage> pour un <xref:System.Drawing.Printing.PrintDocument>, un objet graphics est fourni en tant qu’une des propriétés de <xref:System.Windows.Forms.PaintEventArgs> ou <xref:System.Drawing.Printing.PrintPageEventArgs>.  
  
#### <a name="to-obtain-a-reference-to-a-graphics-object-from-the-painteventargs-in-the-paint-event"></a>Pour obtenir une référence à un objet graphique de PaintEventArgs de l’événement Paint  
  
1. Déclarez le <xref:System.Drawing.Graphics> objet.  
  
2. Affectez la variable pour faire référence à la <xref:System.Drawing.Graphics> objet passé en tant que partie de la <xref:System.Windows.Forms.PaintEventArgs>.  
  
3. Insérer du code pour peindre le formulaire ou contrôle.  
  
     L’exemple suivant indique comment référencer un <xref:System.Drawing.Graphics> de l’objet à partir de la <xref:System.Windows.Forms.PaintEventArgs> dans le <xref:System.Windows.Forms.Control.Paint> événement :  
  
    ```vb  
    Private Sub Form1_Paint(sender As Object, pe As PaintEventArgs) Handles _  
       MyBase.Paint  
       ' Declares the Graphics object and sets it to the Graphics object  
       ' supplied in the PaintEventArgs.  
       Dim g As Graphics = pe.Graphics  
       ' Insert code to paint the form here.  
    End Sub  
    ```  
  
    ```csharp  
    private void Form1_Paint(object sender,   
       System.Windows.Forms.PaintEventArgs pe)   
    {  
       // Declares the Graphics object and sets it to the Graphics object  
       // supplied in the PaintEventArgs.  
       Graphics g = pe.Graphics;  
       // Insert code to paint the form here.  
    }  
    ```  
  
    ```cpp  
    private:  
       void Form1_Paint(System::Object ^ sender,  
          System::Windows::Forms::PaintEventArgs ^ pe)  
       {  
          // Declares the Graphics object and sets it to the Graphics object  
          // supplied in the PaintEventArgs.  
          Graphics ^ g = pe->Graphics;  
          // Insert code to paint the form here.  
       }  
    ```  
  
## <a name="creategraphics-method"></a>Méthode CreateGraphics  
 Vous pouvez également utiliser le <xref:System.Windows.Forms.Control.CreateGraphics%2A> méthode d’un contrôle ou un formulaire afin d’obtenir une référence à un <xref:System.Drawing.Graphics> objet qui représente la surface de dessin de ce contrôle ou formulaire.  
  
#### <a name="to-create-a-graphics-object-with-the-creategraphics-method"></a>Pour créer un objet Graphics avec la méthode CreateGraphics  
  
- Appelez le <xref:System.Windows.Forms.Control.CreateGraphics%2A> méthode du formulaire ou contrôle sur lequel vous souhaitez restituer des graphiques.  
  
    ```vb  
    Dim g as Graphics  
    ' Sets g to a Graphics object representing the drawing surface of the  
    ' control or form g is a member of.  
    g = Me.CreateGraphics  
    ```  
  
    ```csharp  
    Graphics g;  
    // Sets g to a graphics object representing the drawing surface of the  
    // control or form g is a member of.  
    g = this.CreateGraphics();  
    ```  
  
    ```cpp  
    Graphics ^ g;  
    // Sets g to a graphics object representing the drawing surface of the  
    // control or form g is a member of.  
    g = this->CreateGraphics();  
    ```  
  
## <a name="create-from-an-image-object"></a>Créer à partir d’un objet Image  
 En outre, vous pouvez créer un objet graphique à partir de n’importe quel objet qui dérive de la <xref:System.Drawing.Image> classe.  
  
#### <a name="to-create-a-graphics-object-from-an-image"></a>Pour créer un objet graphique à partir d’une Image  
  
- Appelez le <xref:System.Drawing.Graphics.FromImage%2A?displayProperty=nameWithType> méthode, en fournissant le nom de la variable de l’Image à partir de laquelle vous souhaitez créer un <xref:System.Drawing.Graphics> objet.  
  
     L’exemple suivant montre comment utiliser un <xref:System.Drawing.Bitmap> objet :  
  
    ```vb  
    Dim myBitmap as New Bitmap("C:\Documents and Settings\Joe\Pics\myPic.bmp")  
    Dim g as Graphics = Graphics.FromImage(myBitmap)  
    ```  
  
    ```csharp  
    Bitmap myBitmap = new Bitmap(@"C:\Documents and   
       Settings\Joe\Pics\myPic.bmp");  
    Graphics g = Graphics.FromImage(myBitmap);  
    ```  
  
    ```cpp  
    Bitmap ^ myBitmap = gcnew  
       Bitmap("D:\\Documents and Settings\\Joe\\Pics\\myPic.bmp");  
    Graphics ^ g = Graphics::FromImage(myBitmap);  
    ```  
  
> [!NOTE]
>  Vous pouvez uniquement créer <xref:System.Drawing.Graphics> objets à partir de fichiers .bmp non indexés, tels que des fichiers .bmp 16 bits, 24 bits et 32 bits. Chaque pixel de fichiers .bmp non indexée conserve une couleur, contrairement aux pixels des fichiers .bmp indexés, qui contiennent un index dans une table des couleurs.  
  
## <a name="drawing-and-manipulating-shapes-and-images"></a>Dessin et manipulation de formes et des Images  
 Après sa création, un <xref:System.Drawing.Graphics> objet peut être utilisé pour dessiner des lignes et des formes, de rendre du texte ou d’afficher et de manipuler des images. Les objets principal qui sont utilisés avec la <xref:System.Drawing.Graphics> objet sont :  
  
- Le <xref:System.Drawing.Pen> classe — utilisé pour dessiner des lignes, le mode plan des formes ou rendre d’autres représentations géométriques.  
  
- Le <xref:System.Drawing.Brush> classe — utilisée pour remplir des zones de graphiques, tels que le texte, des images ou des formes remplies.  
  
- Le <xref:System.Drawing.Font> classe — fournit une description les formes à utiliser lors du rendu de texte.  
  
- Le <xref:System.Drawing.Color> structure — représente les différentes couleurs à afficher.  
  
#### <a name="to-use-the-graphics-object-you-have-created"></a>Pour utiliser l’objet Graphics, vous avez créé  
  
- Travailler avec l’objet approprié répertoriée ci-dessus pour dessiner ce dont vous avez besoin.  
  
     Pour plus d’informations, consultez les rubriques suivantes :  
  
    |Pour effectuer le rendu|Voir|  
    |---------------|---------|  
    |Lignes|[Guide pratique pour Dessiner une ligne dans un formulaire Windows](how-to-draw-a-line-on-a-windows-form.md)|  
    |Shapes|[Guide pratique pour Dessiner une forme avec contour](how-to-draw-an-outlined-shape.md)|  
    |Texte|[Guide pratique pour Dessiner du texte dans un formulaire Windows](how-to-draw-text-on-a-windows-form.md)|  
    |Images|[Guide pratique pour Rendre des Images avec GDI +](how-to-render-images-with-gdi.md)|  
  
## <a name="see-also"></a>Voir aussi

- [Mise en route de la programmation graphique](getting-started-with-graphics-programming.md)
- [Graphiques et dessins dans Windows Forms](graphics-and-drawing-in-windows-forms.md)
- [Lignes, courbes et formes](lines-curves-and-shapes.md)
- [Guide pratique pour Rendre des Images avec GDI +](how-to-render-images-with-gdi.md)
