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
# <a name="how-to-create-graphics-objects-for-drawing"></a><span data-ttu-id="859b6-102">Comment : créer des objets graphiques pour le dessin</span><span class="sxs-lookup"><span data-stu-id="859b6-102">How to: Create Graphics Objects for Drawing</span></span>
<span data-ttu-id="859b6-103">Avant de pouvoir dessiner des lignes et des formes, rendre du texte, <xref:System.Drawing.Graphics> ou afficher et manipuler des images avec GDIMD, vous devez créer un objet.</span><span class="sxs-lookup"><span data-stu-id="859b6-103">Before you can draw lines and shapes, render text, or display and manipulate images with GDI+, you need to create a <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="859b6-104">L’objet <xref:System.Drawing.Graphics> représente une surface de dessin GDIMD, et est l’objet qui est utilisé pour créer des images graphiques.</span><span class="sxs-lookup"><span data-stu-id="859b6-104">The <xref:System.Drawing.Graphics> object represents a GDI+ drawing surface, and is the object that is used to create graphical images.</span></span>  
  
 <span data-ttu-id="859b6-105">Il y a deux étapes dans le travail avec des graphiques :</span><span class="sxs-lookup"><span data-stu-id="859b6-105">There are two steps in working with graphics:</span></span>  
  
1. <span data-ttu-id="859b6-106">Création <xref:System.Drawing.Graphics> d’un objet.</span><span class="sxs-lookup"><span data-stu-id="859b6-106">Creating a <xref:System.Drawing.Graphics> object.</span></span>  
  
2. <span data-ttu-id="859b6-107">Utilisation <xref:System.Drawing.Graphics> de l’objet pour dessiner des lignes et des formes, rendre du texte, ou afficher et manipuler des images.</span><span class="sxs-lookup"><span data-stu-id="859b6-107">Using the <xref:System.Drawing.Graphics> object to draw lines and shapes, render text, or display and manipulate images.</span></span>  
  
## <a name="creating-a-graphics-object"></a><span data-ttu-id="859b6-108">Création d’un objet graphique</span><span class="sxs-lookup"><span data-stu-id="859b6-108">Creating a Graphics Object</span></span>  
 <span data-ttu-id="859b6-109">Un objet graphique peut être créé de diverses façons.</span><span class="sxs-lookup"><span data-stu-id="859b6-109">A graphics object can be created in a variety of ways.</span></span>  
  
#### <a name="to-create-a-graphics-object"></a><span data-ttu-id="859b6-110">Pour créer un objet graphique</span><span class="sxs-lookup"><span data-stu-id="859b6-110">To create a graphics object</span></span>  
  
- <span data-ttu-id="859b6-111">Recevez une référence à un objet <xref:System.Windows.Forms.PaintEventArgs> graphique <xref:System.Windows.Forms.Control.Paint> dans le cadre de l’événement d’une forme ou d’un contrôle.</span><span class="sxs-lookup"><span data-stu-id="859b6-111">Receive a reference to a graphics object as part of the <xref:System.Windows.Forms.PaintEventArgs> in the <xref:System.Windows.Forms.Control.Paint> event of a form or control.</span></span> <span data-ttu-id="859b6-112">C’est généralement ainsi que vous obtenez une référence à un objet graphique lors de la création de code de peinture pour un contrôle.</span><span class="sxs-lookup"><span data-stu-id="859b6-112">This is usually how you obtain a reference to a graphics object when creating painting code for a control.</span></span> <span data-ttu-id="859b6-113">De même, vous pouvez également obtenir un <xref:System.Drawing.Printing.PrintPageEventArgs> objet graphique <xref:System.Drawing.Printing.PrintDocument.PrintPage> comme <xref:System.Drawing.Printing.PrintDocument>une propriété de l’lors de la manipulation de l’événement pour un .</span><span class="sxs-lookup"><span data-stu-id="859b6-113">Similarly, you can also obtain a graphics object as a property of the <xref:System.Drawing.Printing.PrintPageEventArgs> when handling the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event for a <xref:System.Drawing.Printing.PrintDocument>.</span></span>  
  
     <span data-ttu-id="859b6-114">-ou-</span><span class="sxs-lookup"><span data-stu-id="859b6-114">-or-</span></span>  
  
- <span data-ttu-id="859b6-115">Appelez <xref:System.Windows.Forms.Control.CreateGraphics%2A> la méthode d’un contrôle ou <xref:System.Drawing.Graphics> d’une forme pour obtenir une référence à un objet qui représente la surface de dessin de ce contrôle ou de cette forme.</span><span class="sxs-lookup"><span data-stu-id="859b6-115">Call the <xref:System.Windows.Forms.Control.CreateGraphics%2A> method of a control or form to obtain a reference to a <xref:System.Drawing.Graphics> object that represents the drawing surface of that control or form.</span></span> <span data-ttu-id="859b6-116">Utilisez cette méthode si vous voulez dessiner sur un formulaire ou un contrôle qui existe déjà.</span><span class="sxs-lookup"><span data-stu-id="859b6-116">Use this method if you want to draw on a form or control that already exists.</span></span>  
  
     <span data-ttu-id="859b6-117">-ou-</span><span class="sxs-lookup"><span data-stu-id="859b6-117">-or-</span></span>  
  
- <span data-ttu-id="859b6-118">Créez <xref:System.Drawing.Graphics> un objet à partir <xref:System.Drawing.Image>de tout objet qui hérite de .</span><span class="sxs-lookup"><span data-stu-id="859b6-118">Create a <xref:System.Drawing.Graphics> object from any object that inherits from <xref:System.Drawing.Image>.</span></span> <span data-ttu-id="859b6-119">Cette approche est utile lorsque vous souhaitez modifier une image déjà existante.</span><span class="sxs-lookup"><span data-stu-id="859b6-119">This approach is useful when you want to alter an already existing image.</span></span>  
  
     <span data-ttu-id="859b6-120">Les sections suivantes donnent des détails sur chacun de ces processus.</span><span class="sxs-lookup"><span data-stu-id="859b6-120">The following sections give details about each of these processes.</span></span>  
  
## <a name="painteventargs-in-the-paint-event-handler"></a><span data-ttu-id="859b6-121">PaintEventArgs dans le gestionnaire d’événements de peinture</span><span class="sxs-lookup"><span data-stu-id="859b6-121">PaintEventArgs in the Paint Event Handler</span></span>  
 <span data-ttu-id="859b6-122">Lors de <xref:System.Windows.Forms.PaintEventHandler> la programmation <xref:System.Drawing.Printing.PrintDocument.PrintPage> de <xref:System.Drawing.Printing.PrintDocument>la pour les contrôles ou le <xref:System.Windows.Forms.PaintEventArgs> pour <xref:System.Drawing.Printing.PrintPageEventArgs>un , un objet graphique est fourni comme l’une des propriétés de ou .</span><span class="sxs-lookup"><span data-stu-id="859b6-122">When programming the <xref:System.Windows.Forms.PaintEventHandler> for controls or the <xref:System.Drawing.Printing.PrintDocument.PrintPage> for a <xref:System.Drawing.Printing.PrintDocument>, a graphics object is provided as one of the properties of <xref:System.Windows.Forms.PaintEventArgs> or <xref:System.Drawing.Printing.PrintPageEventArgs>.</span></span>  
  
#### <a name="to-obtain-a-reference-to-a-graphics-object-from-the-painteventargs-in-the-paint-event"></a><span data-ttu-id="859b6-123">Pour obtenir une référence à un objet graphique de la PaintEventArgs dans l’événement Peinture</span><span class="sxs-lookup"><span data-stu-id="859b6-123">To obtain a reference to a Graphics object from the PaintEventArgs in the Paint event</span></span>  
  
1. <span data-ttu-id="859b6-124">Déclarez <xref:System.Drawing.Graphics> l’objet.</span><span class="sxs-lookup"><span data-stu-id="859b6-124">Declare the <xref:System.Drawing.Graphics> object.</span></span>  
  
2. <span data-ttu-id="859b6-125">Attribuer la variable pour <xref:System.Drawing.Graphics> se référer à <xref:System.Windows.Forms.PaintEventArgs>l’objet passé dans le cadre de la .</span><span class="sxs-lookup"><span data-stu-id="859b6-125">Assign the variable to refer to the <xref:System.Drawing.Graphics> object passed as part of the <xref:System.Windows.Forms.PaintEventArgs>.</span></span>  
  
3. <span data-ttu-id="859b6-126">Insérer du code pour peindre la forme ou le contrôle.</span><span class="sxs-lookup"><span data-stu-id="859b6-126">Insert code to paint the form or control.</span></span>  
  
     <span data-ttu-id="859b6-127">L’exemple suivant montre <xref:System.Drawing.Graphics> comment faire <xref:System.Windows.Forms.PaintEventArgs> référence <xref:System.Windows.Forms.Control.Paint> à un objet à partir de l’événement :</span><span class="sxs-lookup"><span data-stu-id="859b6-127">The following example shows how to reference a <xref:System.Drawing.Graphics> object from the <xref:System.Windows.Forms.PaintEventArgs> in the <xref:System.Windows.Forms.Control.Paint> event:</span></span>  
  
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
  
## <a name="creategraphics-method"></a><span data-ttu-id="859b6-128">Méthode CreateGraphics</span><span class="sxs-lookup"><span data-stu-id="859b6-128">CreateGraphics Method</span></span>  
 <span data-ttu-id="859b6-129">Vous pouvez également <xref:System.Windows.Forms.Control.CreateGraphics%2A> utiliser la méthode d’un contrôle <xref:System.Drawing.Graphics> ou d’une forme pour obtenir une référence à un objet qui représente la surface de dessin de ce contrôle ou de cette forme.</span><span class="sxs-lookup"><span data-stu-id="859b6-129">You can also use the <xref:System.Windows.Forms.Control.CreateGraphics%2A> method of a control or form to obtain a reference to a <xref:System.Drawing.Graphics> object that represents the drawing surface of that control or form.</span></span>  
  
#### <a name="to-create-a-graphics-object-with-the-creategraphics-method"></a><span data-ttu-id="859b6-130">Créer un objet graphique avec la méthode CreateGraphics</span><span class="sxs-lookup"><span data-stu-id="859b6-130">To create a Graphics object with the CreateGraphics method</span></span>  
  
- <span data-ttu-id="859b6-131">Appelez <xref:System.Windows.Forms.Control.CreateGraphics%2A> la méthode du formulaire ou du contrôle sur lequel vous souhaitez rendre des graphiques.</span><span class="sxs-lookup"><span data-stu-id="859b6-131">Call the <xref:System.Windows.Forms.Control.CreateGraphics%2A> method of the form or control upon which you want to render graphics.</span></span>  
  
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
  
## <a name="create-from-an-image-object"></a><span data-ttu-id="859b6-132">Créer à partir d’un objet d’image</span><span class="sxs-lookup"><span data-stu-id="859b6-132">Create from an Image Object</span></span>  
 <span data-ttu-id="859b6-133">En outre, vous pouvez créer un objet graphique <xref:System.Drawing.Image> à partir de n’importe quel objet qui dérive de la classe.</span><span class="sxs-lookup"><span data-stu-id="859b6-133">Additionally, you can create a graphics object from any object that derives from the <xref:System.Drawing.Image> class.</span></span>  
  
#### <a name="to-create-a-graphics-object-from-an-image"></a><span data-ttu-id="859b6-134">Créer un objet graphique à partir d’une image</span><span class="sxs-lookup"><span data-stu-id="859b6-134">To create a Graphics object from an Image</span></span>  
  
- <span data-ttu-id="859b6-135">Appelez <xref:System.Drawing.Graphics.FromImage%2A?displayProperty=nameWithType> la méthode, en fournissant le nom de la <xref:System.Drawing.Graphics> variable d’image à partir de laquelle vous souhaitez créer un objet.</span><span class="sxs-lookup"><span data-stu-id="859b6-135">Call the <xref:System.Drawing.Graphics.FromImage%2A?displayProperty=nameWithType> method, supplying the name of the Image variable from which you want to create a <xref:System.Drawing.Graphics> object.</span></span>  
  
     <span data-ttu-id="859b6-136">L’exemple suivant montre <xref:System.Drawing.Bitmap> comment utiliser un objet :</span><span class="sxs-lookup"><span data-stu-id="859b6-136">The following example shows how to use a <xref:System.Drawing.Bitmap> object:</span></span>  
  
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
> <span data-ttu-id="859b6-137">Vous ne <xref:System.Drawing.Graphics> pouvez créer des objets qu’à partir de fichiers .bmp non indexés, tels que les fichiers 16 bits, 24 bits et 32 bits .bmp.</span><span class="sxs-lookup"><span data-stu-id="859b6-137">You can only create <xref:System.Drawing.Graphics> objects from nonindexed .bmp files, such as 16-bit, 24-bit, and 32-bit .bmp files.</span></span> <span data-ttu-id="859b6-138">Chaque pixel de fichiers .bmp non indexés contient une couleur, contrairement aux pixels des fichiers .bmp indexés, qui détiennent un index à une table de couleur.</span><span class="sxs-lookup"><span data-stu-id="859b6-138">Each pixel of nonindexed .bmp files holds a color, in contrast to pixels of indexed .bmp files, which hold an index to a color table.</span></span>  
  
## <a name="drawing-and-manipulating-shapes-and-images"></a><span data-ttu-id="859b6-139">Dessin et manipulation des formes et des images</span><span class="sxs-lookup"><span data-stu-id="859b6-139">Drawing and Manipulating Shapes and Images</span></span>  
 <span data-ttu-id="859b6-140">Une fois créé, <xref:System.Drawing.Graphics> un objet peut être utilisé pour dessiner des lignes et des formes, rendre du texte, ou afficher et manipuler des images.</span><span class="sxs-lookup"><span data-stu-id="859b6-140">After it is created, a <xref:System.Drawing.Graphics> object may be used to draw lines and shapes, render text, or display and manipulate images.</span></span> <span data-ttu-id="859b6-141">Les principaux objets utilisés <xref:System.Drawing.Graphics> avec l’objet sont les principaux :</span><span class="sxs-lookup"><span data-stu-id="859b6-141">The principal objects that are used with the <xref:System.Drawing.Graphics> object are:</span></span>  
  
- <span data-ttu-id="859b6-142">La <xref:System.Drawing.Pen> classe— Utilisée pour tracer des lignes, tracer des formes ou rendre d’autres représentations géométriques.</span><span class="sxs-lookup"><span data-stu-id="859b6-142">The <xref:System.Drawing.Pen> class—Used for drawing lines, outlining shapes, or rendering other geometric representations.</span></span>  
  
- <span data-ttu-id="859b6-143">La <xref:System.Drawing.Brush> classe— Utilisée pour remplir des zones graphiques, telles que des formes remplies, des images ou du texte.</span><span class="sxs-lookup"><span data-stu-id="859b6-143">The <xref:System.Drawing.Brush> class—Used for filling areas of graphics, such as filled shapes, images, or text.</span></span>  
  
- <span data-ttu-id="859b6-144">La <xref:System.Drawing.Font> classe — Fournit une description des formes à utiliser lors du rendu du texte.</span><span class="sxs-lookup"><span data-stu-id="859b6-144">The <xref:System.Drawing.Font> class—Provides a description of what shapes to use when rendering text.</span></span>  
  
- <span data-ttu-id="859b6-145">La <xref:System.Drawing.Color> structure représente les différentes couleurs à afficher.</span><span class="sxs-lookup"><span data-stu-id="859b6-145">The <xref:System.Drawing.Color> structure—Represents the different colors to display.</span></span>  
  
#### <a name="to-use-the-graphics-object-you-have-created"></a><span data-ttu-id="859b6-146">Pour utiliser l’objet Graphiques que vous avez créé</span><span class="sxs-lookup"><span data-stu-id="859b6-146">To use the Graphics object you have created</span></span>  
  
- <span data-ttu-id="859b6-147">Travaillez avec l’objet approprié énuméré ci-dessus pour dessiner ce dont vous avez besoin.</span><span class="sxs-lookup"><span data-stu-id="859b6-147">Work with the appropriate object listed above to draw what you need.</span></span>  
  
     <span data-ttu-id="859b6-148">Pour plus d'informations, voir les rubriques suivantes :</span><span class="sxs-lookup"><span data-stu-id="859b6-148">For more information, see the following topics:</span></span>  
  
    |<span data-ttu-id="859b6-149">Pour rendre</span><span class="sxs-lookup"><span data-stu-id="859b6-149">To render</span></span>|<span data-ttu-id="859b6-150">Consultez</span><span class="sxs-lookup"><span data-stu-id="859b6-150">See</span></span>|  
    |---------------|---------|  
    |<span data-ttu-id="859b6-151">Lignes</span><span class="sxs-lookup"><span data-stu-id="859b6-151">Lines</span></span>|[<span data-ttu-id="859b6-152">Guide pratique pour dessiner une ligne dans un Windows Form</span><span class="sxs-lookup"><span data-stu-id="859b6-152">How to: Draw a Line on a Windows Form</span></span>](how-to-draw-a-line-on-a-windows-form.md)|  
    |<span data-ttu-id="859b6-153">Formes</span><span class="sxs-lookup"><span data-stu-id="859b6-153">Shapes</span></span>|[<span data-ttu-id="859b6-154">Comment : dessiner une forme avec contour</span><span class="sxs-lookup"><span data-stu-id="859b6-154">How to: Draw an Outlined Shape</span></span>](how-to-draw-an-outlined-shape.md)|  
    |<span data-ttu-id="859b6-155">Texte</span><span class="sxs-lookup"><span data-stu-id="859b6-155">Text</span></span>|[<span data-ttu-id="859b6-156">Comment : dessiner du texte dans un Windows Form</span><span class="sxs-lookup"><span data-stu-id="859b6-156">How to: Draw Text on a Windows Form</span></span>](how-to-draw-text-on-a-windows-form.md)|  
    |<span data-ttu-id="859b6-157">Images</span><span class="sxs-lookup"><span data-stu-id="859b6-157">Images</span></span>|[<span data-ttu-id="859b6-158">Guide pratique pour rendre des images avec GDI+</span><span class="sxs-lookup"><span data-stu-id="859b6-158">How to: Render Images with GDI+</span></span>](how-to-render-images-with-gdi.md)|  
  
## <a name="see-also"></a><span data-ttu-id="859b6-159">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="859b6-159">See also</span></span>

- [<span data-ttu-id="859b6-160">Mise en route de la programmation graphique</span><span class="sxs-lookup"><span data-stu-id="859b6-160">Getting Started with Graphics Programming</span></span>](getting-started-with-graphics-programming.md)
- [<span data-ttu-id="859b6-161">Graphiques et dessins dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="859b6-161">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="859b6-162">Lignes, courbes et formes</span><span class="sxs-lookup"><span data-stu-id="859b6-162">Lines, Curves, and Shapes</span></span>](lines-curves-and-shapes.md)
- [<span data-ttu-id="859b6-163">Guide pratique pour rendre des images avec GDI+</span><span class="sxs-lookup"><span data-stu-id="859b6-163">How to: Render Images with GDI+</span></span>](how-to-render-images-with-gdi.md)
