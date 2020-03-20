---
title: 'Comment : créer des objets graphiques pour le dessin'
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
ms.openlocfilehash: d591d65904484e33285e5db7aa99760f3e1909d3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142431"
---
# <a name="how-to-create-graphics-objects-for-drawing"></a>Comment : créer des objets graphiques pour le dessin
Avant de pouvoir dessiner des lignes et des formes, rendre du texte, <xref:System.Drawing.Graphics> ou afficher et manipuler des images avec GDIMD, vous devez créer un objet. L’objet <xref:System.Drawing.Graphics> représente une surface de dessin GDIMD, et est l’objet qui est utilisé pour créer des images graphiques.  
  
 Il y a deux étapes dans le travail avec des graphiques :  
  
1. Création <xref:System.Drawing.Graphics> d’un objet.  
  
2. Utilisation <xref:System.Drawing.Graphics> de l’objet pour dessiner des lignes et des formes, rendre du texte, ou afficher et manipuler des images.  
  
## <a name="creating-a-graphics-object"></a>Création d’un objet graphique  
 Un objet graphique peut être créé de diverses façons.  
  
#### <a name="to-create-a-graphics-object"></a>Pour créer un objet graphique  
  
- Recevez une référence à un objet <xref:System.Windows.Forms.PaintEventArgs> graphique <xref:System.Windows.Forms.Control.Paint> dans le cadre de l’événement d’une forme ou d’un contrôle. C’est généralement ainsi que vous obtenez une référence à un objet graphique lors de la création de code de peinture pour un contrôle. De même, vous pouvez également obtenir un <xref:System.Drawing.Printing.PrintPageEventArgs> objet graphique <xref:System.Drawing.Printing.PrintDocument.PrintPage> comme <xref:System.Drawing.Printing.PrintDocument>une propriété de l’lors de la manipulation de l’événement pour un .  
  
     -ou-  
  
- Appelez <xref:System.Windows.Forms.Control.CreateGraphics%2A> la méthode d’un contrôle ou <xref:System.Drawing.Graphics> d’une forme pour obtenir une référence à un objet qui représente la surface de dessin de ce contrôle ou de cette forme. Utilisez cette méthode si vous voulez dessiner sur un formulaire ou un contrôle qui existe déjà.  
  
     -ou-  
  
- Créez <xref:System.Drawing.Graphics> un objet à partir <xref:System.Drawing.Image>de tout objet qui hérite de . Cette approche est utile lorsque vous souhaitez modifier une image déjà existante.  
  
     Les sections suivantes donnent des détails sur chacun de ces processus.  
  
## <a name="painteventargs-in-the-paint-event-handler"></a>PaintEventArgs dans le gestionnaire d’événements de peinture  
 Lors de <xref:System.Windows.Forms.PaintEventHandler> la programmation <xref:System.Drawing.Printing.PrintDocument.PrintPage> de <xref:System.Drawing.Printing.PrintDocument>la pour les contrôles ou le <xref:System.Windows.Forms.PaintEventArgs> pour <xref:System.Drawing.Printing.PrintPageEventArgs>un , un objet graphique est fourni comme l’une des propriétés de ou .  
  
#### <a name="to-obtain-a-reference-to-a-graphics-object-from-the-painteventargs-in-the-paint-event"></a>Pour obtenir une référence à un objet graphique de la PaintEventArgs dans l’événement Peinture  
  
1. Déclarez <xref:System.Drawing.Graphics> l’objet.  
  
2. Attribuer la variable pour <xref:System.Drawing.Graphics> se référer à <xref:System.Windows.Forms.PaintEventArgs>l’objet passé dans le cadre de la .  
  
3. Insérer du code pour peindre la forme ou le contrôle.  
  
     L’exemple suivant montre <xref:System.Drawing.Graphics> comment faire <xref:System.Windows.Forms.PaintEventArgs> référence <xref:System.Windows.Forms.Control.Paint> à un objet à partir de l’événement :  
  
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
 Vous pouvez également <xref:System.Windows.Forms.Control.CreateGraphics%2A> utiliser la méthode d’un contrôle <xref:System.Drawing.Graphics> ou d’une forme pour obtenir une référence à un objet qui représente la surface de dessin de ce contrôle ou de cette forme.  
  
#### <a name="to-create-a-graphics-object-with-the-creategraphics-method"></a>Créer un objet graphique avec la méthode CreateGraphics  
  
- Appelez <xref:System.Windows.Forms.Control.CreateGraphics%2A> la méthode du formulaire ou du contrôle sur lequel vous souhaitez rendre des graphiques.  
  
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
  
## <a name="create-from-an-image-object"></a>Créer à partir d’un objet d’image  
 En outre, vous pouvez créer un objet graphique <xref:System.Drawing.Image> à partir de n’importe quel objet qui dérive de la classe.  
  
#### <a name="to-create-a-graphics-object-from-an-image"></a>Créer un objet graphique à partir d’une image  
  
- Appelez <xref:System.Drawing.Graphics.FromImage%2A?displayProperty=nameWithType> la méthode, en fournissant le nom de la <xref:System.Drawing.Graphics> variable d’image à partir de laquelle vous souhaitez créer un objet.  
  
     L’exemple suivant montre <xref:System.Drawing.Bitmap> comment utiliser un objet :  
  
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
> Vous ne <xref:System.Drawing.Graphics> pouvez créer des objets qu’à partir de fichiers .bmp non indexés, tels que les fichiers 16 bits, 24 bits et 32 bits .bmp. Chaque pixel de fichiers .bmp non indexés contient une couleur, contrairement aux pixels des fichiers .bmp indexés, qui détiennent un index à une table de couleur.  
  
## <a name="drawing-and-manipulating-shapes-and-images"></a>Dessin et manipulation des formes et des images  
 Une fois créé, <xref:System.Drawing.Graphics> un objet peut être utilisé pour dessiner des lignes et des formes, rendre du texte, ou afficher et manipuler des images. Les principaux objets utilisés <xref:System.Drawing.Graphics> avec l’objet sont les principaux :  
  
- La <xref:System.Drawing.Pen> classe— Utilisée pour tracer des lignes, tracer des formes ou rendre d’autres représentations géométriques.  
  
- La <xref:System.Drawing.Brush> classe— Utilisée pour remplir des zones graphiques, telles que des formes remplies, des images ou du texte.  
  
- La <xref:System.Drawing.Font> classe — Fournit une description des formes à utiliser lors du rendu du texte.  
  
- La <xref:System.Drawing.Color> structure représente les différentes couleurs à afficher.  
  
#### <a name="to-use-the-graphics-object-you-have-created"></a>Pour utiliser l’objet Graphiques que vous avez créé  
  
- Travaillez avec l’objet approprié énuméré ci-dessus pour dessiner ce dont vous avez besoin.  
  
     Pour plus d'informations, voir les rubriques suivantes :  
  
    |Pour rendre|Consultez|  
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
