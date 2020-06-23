---
title: 'Comment : créer des objets graphiques pour le dessin'
description: Apprenez maintenant à créer un objet graphique dont vous avez besoin pour dessiner des lignes et des formes, pour afficher du texte ou pour afficher et manipuler des images avec GDI+.
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
ms.openlocfilehash: 1a0884c1e9956dc6f4608e32372deeea24ef4670
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84903205"
---
# <a name="how-to-create-graphics-objects-for-drawing"></a>Comment : créer des objets graphiques pour le dessin
Avant de pouvoir dessiner des lignes et des formes, de rendre du texte ou d’afficher et de manipuler des images avec GDI+, vous devez créer un <xref:System.Drawing.Graphics> objet. L' <xref:System.Drawing.Graphics> objet représente une surface de dessin GDI+ et est l’objet utilisé pour créer des images graphiques.  
  
 L’utilisation des graphiques s’exécute en deux étapes :  
  
1. Création d’un <xref:System.Drawing.Graphics> objet.  
  
2. Utilisation <xref:System.Drawing.Graphics> de l’objet pour dessiner des lignes et des formes, rendre du texte ou afficher et manipuler des images.  
  
## <a name="creating-a-graphics-object"></a>Création d’un objet Graphics  
 Un objet Graphics peut être créé de différentes façons.  
  
#### <a name="to-create-a-graphics-object"></a>Pour créer un objet Graphics  
  
- Recevoir une référence à un objet Graphics dans le cadre de l' <xref:System.Windows.Forms.PaintEventArgs> événement dans le <xref:System.Windows.Forms.Control.Paint> cas d’un formulaire ou d’un contrôle. Il s’agit généralement de la façon dont vous obtenez une référence à un objet Graphics lors de la création d’un code de peinture pour un contrôle. De même, vous pouvez également obtenir un objet Graphics en tant que propriété de lors de la <xref:System.Drawing.Printing.PrintPageEventArgs> gestion de l' <xref:System.Drawing.Printing.PrintDocument.PrintPage> événement pour <xref:System.Drawing.Printing.PrintDocument> .  
  
     -ou-  
  
- Appelez la <xref:System.Windows.Forms.Control.CreateGraphics%2A> méthode d’un contrôle ou d’un formulaire pour obtenir une référence à un <xref:System.Drawing.Graphics> objet qui représente la surface de dessin de ce contrôle ou formulaire. Utilisez cette méthode si vous souhaitez dessiner sur un formulaire ou un contrôle qui existe déjà.  
  
     -ou-  
  
- Créez un <xref:System.Drawing.Graphics> objet à partir de tout objet qui hérite de <xref:System.Drawing.Image> . Cette approche est utile lorsque vous souhaitez modifier une image déjà existante.  
  
     Les sections suivantes fournissent des détails sur chacun de ces processus.  
  
## <a name="painteventargs-in-the-paint-event-handler"></a>PaintEventArgs dans le gestionnaire d’événements Paint  
 Lors de la programmation <xref:System.Windows.Forms.PaintEventHandler> des contrôles for ou <xref:System.Drawing.Printing.PrintDocument.PrintPage> de <xref:System.Drawing.Printing.PrintDocument> , un objet Graphics est fourni comme l’une des propriétés de <xref:System.Windows.Forms.PaintEventArgs> ou <xref:System.Drawing.Printing.PrintPageEventArgs> .  
  
#### <a name="to-obtain-a-reference-to-a-graphics-object-from-the-painteventargs-in-the-paint-event"></a>Pour obtenir une référence à un objet Graphics à partir des PaintEventArgs dans l’événement Paint  
  
1. Déclarez l' <xref:System.Drawing.Graphics> objet.  
  
2. Assignez la variable pour faire référence à l' <xref:System.Drawing.Graphics> objet passé dans le cadre de <xref:System.Windows.Forms.PaintEventArgs> .  
  
3. Insérez du code pour peindre le formulaire ou le contrôle.  
  
     L’exemple suivant montre comment référencer un <xref:System.Drawing.Graphics> objet à partir de <xref:System.Windows.Forms.PaintEventArgs> dans l' <xref:System.Windows.Forms.Control.Paint> événement :  
  
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
 Vous pouvez également utiliser la <xref:System.Windows.Forms.Control.CreateGraphics%2A> méthode d’un contrôle ou d’un formulaire pour obtenir une référence à un <xref:System.Drawing.Graphics> objet qui représente la surface de dessin de ce contrôle ou formulaire.  
  
#### <a name="to-create-a-graphics-object-with-the-creategraphics-method"></a>Pour créer un objet Graphics avec la méthode CreateGraphics  
  
- Appelez la <xref:System.Windows.Forms.Control.CreateGraphics%2A> méthode du formulaire ou du contrôle sur lequel vous souhaitez afficher les graphiques.  
  
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
  
## <a name="create-from-an-image-object"></a>Créer à partir d’un objet image  
 En outre, vous pouvez créer un objet Graphics à partir de n’importe quel objet qui dérive de la <xref:System.Drawing.Image> classe.  
  
#### <a name="to-create-a-graphics-object-from-an-image"></a>Pour créer un objet Graphics à partir d’une image  
  
- Appelez la <xref:System.Drawing.Graphics.FromImage%2A?displayProperty=nameWithType> méthode, en fournissant le nom de la variable d’image à partir de laquelle vous souhaitez créer un <xref:System.Drawing.Graphics> objet.  
  
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
> Vous pouvez uniquement créer <xref:System.Drawing.Graphics> des objets à partir de fichiers. bmp non indexés, tels que des fichiers. bmp 16 bits, 24 bits et 32 bits. Chaque pixel de fichiers. bmp non indexés contient une couleur, contrairement aux pixels des fichiers. bmp indexés, qui contiennent un index dans une table des couleurs.  
  
## <a name="drawing-and-manipulating-shapes-and-images"></a>Dessin et manipulation de formes et d’images  
 Une fois créé, un <xref:System.Drawing.Graphics> objet peut être utilisé pour dessiner des lignes et des formes, pour restituer du texte ou pour afficher et manipuler des images. Les objets principal utilisés avec l' <xref:System.Drawing.Graphics> objet sont :  
  
- La <xref:System.Drawing.Pen> classe, utilisée pour dessiner des lignes, des formes en mode plan ou un rendu d’autres représentations géométriques.  
  
- La <xref:System.Drawing.Brush> classe, utilisée pour remplir des zones de graphiques, telles que des formes remplies, des images ou du texte.  
  
- La <xref:System.Drawing.Font> classe fournit une description des formes à utiliser lors du rendu du texte.  
  
- La <xref:System.Drawing.Color> structure : représente les différentes couleurs à afficher.  
  
#### <a name="to-use-the-graphics-object-you-have-created"></a>Pour utiliser l’objet Graphics que vous avez créé  
  
- Utilisez l’objet approprié indiqué ci-dessus pour dessiner ce dont vous avez besoin.  
  
     Pour plus d'informations, voir les rubriques suivantes :  
  
    |Pour effectuer le rendu|Consultez|  
    |---------------|---------|  
    |Lignes|[Guide pratique pour dessiner une ligne dans un Windows Form](how-to-draw-a-line-on-a-windows-form.md)|  
    |Formes|[Comment : dessiner une forme avec contour](how-to-draw-an-outlined-shape.md)|  
    |Texte|[Comment : dessiner du texte dans un Windows Form](how-to-draw-text-on-a-windows-form.md)|  
    |Images|[Guide pratique pour rendre des images avec GDI+](how-to-render-images-with-gdi.md)|  
  
## <a name="see-also"></a>Voir aussi

- [Mise en route de la programmation graphique](getting-started-with-graphics-programming.md)
- [Graphiques et dessins dans les Windows Forms](graphics-and-drawing-in-windows-forms.md)
- [Lignes, courbes et formes](lines-curves-and-shapes.md)
- [Guide pratique pour rendre des images avec GDI+](how-to-render-images-with-gdi.md)
