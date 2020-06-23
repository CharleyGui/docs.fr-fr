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
# <a name="how-to-create-graphics-objects-for-drawing"></a><span data-ttu-id="3ad3f-103">Comment : créer des objets graphiques pour le dessin</span><span class="sxs-lookup"><span data-stu-id="3ad3f-103">How to: Create Graphics Objects for Drawing</span></span>
<span data-ttu-id="3ad3f-104">Avant de pouvoir dessiner des lignes et des formes, de rendre du texte ou d’afficher et de manipuler des images avec GDI+, vous devez créer un <xref:System.Drawing.Graphics> objet.</span><span class="sxs-lookup"><span data-stu-id="3ad3f-104">Before you can draw lines and shapes, render text, or display and manipulate images with GDI+, you need to create a <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="3ad3f-105">L' <xref:System.Drawing.Graphics> objet représente une surface de dessin GDI+ et est l’objet utilisé pour créer des images graphiques.</span><span class="sxs-lookup"><span data-stu-id="3ad3f-105">The <xref:System.Drawing.Graphics> object represents a GDI+ drawing surface, and is the object that is used to create graphical images.</span></span>  
  
 <span data-ttu-id="3ad3f-106">L’utilisation des graphiques s’exécute en deux étapes :</span><span class="sxs-lookup"><span data-stu-id="3ad3f-106">There are two steps in working with graphics:</span></span>  
  
1. <span data-ttu-id="3ad3f-107">Création d’un <xref:System.Drawing.Graphics> objet.</span><span class="sxs-lookup"><span data-stu-id="3ad3f-107">Creating a <xref:System.Drawing.Graphics> object.</span></span>  
  
2. <span data-ttu-id="3ad3f-108">Utilisation <xref:System.Drawing.Graphics> de l’objet pour dessiner des lignes et des formes, rendre du texte ou afficher et manipuler des images.</span><span class="sxs-lookup"><span data-stu-id="3ad3f-108">Using the <xref:System.Drawing.Graphics> object to draw lines and shapes, render text, or display and manipulate images.</span></span>  
  
## <a name="creating-a-graphics-object"></a><span data-ttu-id="3ad3f-109">Création d’un objet Graphics</span><span class="sxs-lookup"><span data-stu-id="3ad3f-109">Creating a Graphics Object</span></span>  
 <span data-ttu-id="3ad3f-110">Un objet Graphics peut être créé de différentes façons.</span><span class="sxs-lookup"><span data-stu-id="3ad3f-110">A graphics object can be created in a variety of ways.</span></span>  
  
#### <a name="to-create-a-graphics-object"></a><span data-ttu-id="3ad3f-111">Pour créer un objet Graphics</span><span class="sxs-lookup"><span data-stu-id="3ad3f-111">To create a graphics object</span></span>  
  
- <span data-ttu-id="3ad3f-112">Recevoir une référence à un objet Graphics dans le cadre de l' <xref:System.Windows.Forms.PaintEventArgs> événement dans le <xref:System.Windows.Forms.Control.Paint> cas d’un formulaire ou d’un contrôle.</span><span class="sxs-lookup"><span data-stu-id="3ad3f-112">Receive a reference to a graphics object as part of the <xref:System.Windows.Forms.PaintEventArgs> in the <xref:System.Windows.Forms.Control.Paint> event of a form or control.</span></span> <span data-ttu-id="3ad3f-113">Il s’agit généralement de la façon dont vous obtenez une référence à un objet Graphics lors de la création d’un code de peinture pour un contrôle.</span><span class="sxs-lookup"><span data-stu-id="3ad3f-113">This is usually how you obtain a reference to a graphics object when creating painting code for a control.</span></span> <span data-ttu-id="3ad3f-114">De même, vous pouvez également obtenir un objet Graphics en tant que propriété de lors de la <xref:System.Drawing.Printing.PrintPageEventArgs> gestion de l' <xref:System.Drawing.Printing.PrintDocument.PrintPage> événement pour <xref:System.Drawing.Printing.PrintDocument> .</span><span class="sxs-lookup"><span data-stu-id="3ad3f-114">Similarly, you can also obtain a graphics object as a property of the <xref:System.Drawing.Printing.PrintPageEventArgs> when handling the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event for a <xref:System.Drawing.Printing.PrintDocument>.</span></span>  
  
     <span data-ttu-id="3ad3f-115">-ou-</span><span class="sxs-lookup"><span data-stu-id="3ad3f-115">-or-</span></span>  
  
- <span data-ttu-id="3ad3f-116">Appelez la <xref:System.Windows.Forms.Control.CreateGraphics%2A> méthode d’un contrôle ou d’un formulaire pour obtenir une référence à un <xref:System.Drawing.Graphics> objet qui représente la surface de dessin de ce contrôle ou formulaire.</span><span class="sxs-lookup"><span data-stu-id="3ad3f-116">Call the <xref:System.Windows.Forms.Control.CreateGraphics%2A> method of a control or form to obtain a reference to a <xref:System.Drawing.Graphics> object that represents the drawing surface of that control or form.</span></span> <span data-ttu-id="3ad3f-117">Utilisez cette méthode si vous souhaitez dessiner sur un formulaire ou un contrôle qui existe déjà.</span><span class="sxs-lookup"><span data-stu-id="3ad3f-117">Use this method if you want to draw on a form or control that already exists.</span></span>  
  
     <span data-ttu-id="3ad3f-118">-ou-</span><span class="sxs-lookup"><span data-stu-id="3ad3f-118">-or-</span></span>  
  
- <span data-ttu-id="3ad3f-119">Créez un <xref:System.Drawing.Graphics> objet à partir de tout objet qui hérite de <xref:System.Drawing.Image> .</span><span class="sxs-lookup"><span data-stu-id="3ad3f-119">Create a <xref:System.Drawing.Graphics> object from any object that inherits from <xref:System.Drawing.Image>.</span></span> <span data-ttu-id="3ad3f-120">Cette approche est utile lorsque vous souhaitez modifier une image déjà existante.</span><span class="sxs-lookup"><span data-stu-id="3ad3f-120">This approach is useful when you want to alter an already existing image.</span></span>  
  
     <span data-ttu-id="3ad3f-121">Les sections suivantes fournissent des détails sur chacun de ces processus.</span><span class="sxs-lookup"><span data-stu-id="3ad3f-121">The following sections give details about each of these processes.</span></span>  
  
## <a name="painteventargs-in-the-paint-event-handler"></a><span data-ttu-id="3ad3f-122">PaintEventArgs dans le gestionnaire d’événements Paint</span><span class="sxs-lookup"><span data-stu-id="3ad3f-122">PaintEventArgs in the Paint Event Handler</span></span>  
 <span data-ttu-id="3ad3f-123">Lors de la programmation <xref:System.Windows.Forms.PaintEventHandler> des contrôles for ou <xref:System.Drawing.Printing.PrintDocument.PrintPage> de <xref:System.Drawing.Printing.PrintDocument> , un objet Graphics est fourni comme l’une des propriétés de <xref:System.Windows.Forms.PaintEventArgs> ou <xref:System.Drawing.Printing.PrintPageEventArgs> .</span><span class="sxs-lookup"><span data-stu-id="3ad3f-123">When programming the <xref:System.Windows.Forms.PaintEventHandler> for controls or the <xref:System.Drawing.Printing.PrintDocument.PrintPage> for a <xref:System.Drawing.Printing.PrintDocument>, a graphics object is provided as one of the properties of <xref:System.Windows.Forms.PaintEventArgs> or <xref:System.Drawing.Printing.PrintPageEventArgs>.</span></span>  
  
#### <a name="to-obtain-a-reference-to-a-graphics-object-from-the-painteventargs-in-the-paint-event"></a><span data-ttu-id="3ad3f-124">Pour obtenir une référence à un objet Graphics à partir des PaintEventArgs dans l’événement Paint</span><span class="sxs-lookup"><span data-stu-id="3ad3f-124">To obtain a reference to a Graphics object from the PaintEventArgs in the Paint event</span></span>  
  
1. <span data-ttu-id="3ad3f-125">Déclarez l' <xref:System.Drawing.Graphics> objet.</span><span class="sxs-lookup"><span data-stu-id="3ad3f-125">Declare the <xref:System.Drawing.Graphics> object.</span></span>  
  
2. <span data-ttu-id="3ad3f-126">Assignez la variable pour faire référence à l' <xref:System.Drawing.Graphics> objet passé dans le cadre de <xref:System.Windows.Forms.PaintEventArgs> .</span><span class="sxs-lookup"><span data-stu-id="3ad3f-126">Assign the variable to refer to the <xref:System.Drawing.Graphics> object passed as part of the <xref:System.Windows.Forms.PaintEventArgs>.</span></span>  
  
3. <span data-ttu-id="3ad3f-127">Insérez du code pour peindre le formulaire ou le contrôle.</span><span class="sxs-lookup"><span data-stu-id="3ad3f-127">Insert code to paint the form or control.</span></span>  
  
     <span data-ttu-id="3ad3f-128">L’exemple suivant montre comment référencer un <xref:System.Drawing.Graphics> objet à partir de <xref:System.Windows.Forms.PaintEventArgs> dans l' <xref:System.Windows.Forms.Control.Paint> événement :</span><span class="sxs-lookup"><span data-stu-id="3ad3f-128">The following example shows how to reference a <xref:System.Drawing.Graphics> object from the <xref:System.Windows.Forms.PaintEventArgs> in the <xref:System.Windows.Forms.Control.Paint> event:</span></span>  
  
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
  
## <a name="creategraphics-method"></a><span data-ttu-id="3ad3f-129">Méthode CreateGraphics</span><span class="sxs-lookup"><span data-stu-id="3ad3f-129">CreateGraphics Method</span></span>  
 <span data-ttu-id="3ad3f-130">Vous pouvez également utiliser la <xref:System.Windows.Forms.Control.CreateGraphics%2A> méthode d’un contrôle ou d’un formulaire pour obtenir une référence à un <xref:System.Drawing.Graphics> objet qui représente la surface de dessin de ce contrôle ou formulaire.</span><span class="sxs-lookup"><span data-stu-id="3ad3f-130">You can also use the <xref:System.Windows.Forms.Control.CreateGraphics%2A> method of a control or form to obtain a reference to a <xref:System.Drawing.Graphics> object that represents the drawing surface of that control or form.</span></span>  
  
#### <a name="to-create-a-graphics-object-with-the-creategraphics-method"></a><span data-ttu-id="3ad3f-131">Pour créer un objet Graphics avec la méthode CreateGraphics</span><span class="sxs-lookup"><span data-stu-id="3ad3f-131">To create a Graphics object with the CreateGraphics method</span></span>  
  
- <span data-ttu-id="3ad3f-132">Appelez la <xref:System.Windows.Forms.Control.CreateGraphics%2A> méthode du formulaire ou du contrôle sur lequel vous souhaitez afficher les graphiques.</span><span class="sxs-lookup"><span data-stu-id="3ad3f-132">Call the <xref:System.Windows.Forms.Control.CreateGraphics%2A> method of the form or control upon which you want to render graphics.</span></span>  
  
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
  
## <a name="create-from-an-image-object"></a><span data-ttu-id="3ad3f-133">Créer à partir d’un objet image</span><span class="sxs-lookup"><span data-stu-id="3ad3f-133">Create from an Image Object</span></span>  
 <span data-ttu-id="3ad3f-134">En outre, vous pouvez créer un objet Graphics à partir de n’importe quel objet qui dérive de la <xref:System.Drawing.Image> classe.</span><span class="sxs-lookup"><span data-stu-id="3ad3f-134">Additionally, you can create a graphics object from any object that derives from the <xref:System.Drawing.Image> class.</span></span>  
  
#### <a name="to-create-a-graphics-object-from-an-image"></a><span data-ttu-id="3ad3f-135">Pour créer un objet Graphics à partir d’une image</span><span class="sxs-lookup"><span data-stu-id="3ad3f-135">To create a Graphics object from an Image</span></span>  
  
- <span data-ttu-id="3ad3f-136">Appelez la <xref:System.Drawing.Graphics.FromImage%2A?displayProperty=nameWithType> méthode, en fournissant le nom de la variable d’image à partir de laquelle vous souhaitez créer un <xref:System.Drawing.Graphics> objet.</span><span class="sxs-lookup"><span data-stu-id="3ad3f-136">Call the <xref:System.Drawing.Graphics.FromImage%2A?displayProperty=nameWithType> method, supplying the name of the Image variable from which you want to create a <xref:System.Drawing.Graphics> object.</span></span>  
  
     <span data-ttu-id="3ad3f-137">L’exemple suivant montre comment utiliser un <xref:System.Drawing.Bitmap> objet :</span><span class="sxs-lookup"><span data-stu-id="3ad3f-137">The following example shows how to use a <xref:System.Drawing.Bitmap> object:</span></span>  
  
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
> <span data-ttu-id="3ad3f-138">Vous pouvez uniquement créer <xref:System.Drawing.Graphics> des objets à partir de fichiers. bmp non indexés, tels que des fichiers. bmp 16 bits, 24 bits et 32 bits.</span><span class="sxs-lookup"><span data-stu-id="3ad3f-138">You can only create <xref:System.Drawing.Graphics> objects from nonindexed .bmp files, such as 16-bit, 24-bit, and 32-bit .bmp files.</span></span> <span data-ttu-id="3ad3f-139">Chaque pixel de fichiers. bmp non indexés contient une couleur, contrairement aux pixels des fichiers. bmp indexés, qui contiennent un index dans une table des couleurs.</span><span class="sxs-lookup"><span data-stu-id="3ad3f-139">Each pixel of nonindexed .bmp files holds a color, in contrast to pixels of indexed .bmp files, which hold an index to a color table.</span></span>  
  
## <a name="drawing-and-manipulating-shapes-and-images"></a><span data-ttu-id="3ad3f-140">Dessin et manipulation de formes et d’images</span><span class="sxs-lookup"><span data-stu-id="3ad3f-140">Drawing and Manipulating Shapes and Images</span></span>  
 <span data-ttu-id="3ad3f-141">Une fois créé, un <xref:System.Drawing.Graphics> objet peut être utilisé pour dessiner des lignes et des formes, pour restituer du texte ou pour afficher et manipuler des images.</span><span class="sxs-lookup"><span data-stu-id="3ad3f-141">After it is created, a <xref:System.Drawing.Graphics> object may be used to draw lines and shapes, render text, or display and manipulate images.</span></span> <span data-ttu-id="3ad3f-142">Les objets principal utilisés avec l' <xref:System.Drawing.Graphics> objet sont :</span><span class="sxs-lookup"><span data-stu-id="3ad3f-142">The principal objects that are used with the <xref:System.Drawing.Graphics> object are:</span></span>  
  
- <span data-ttu-id="3ad3f-143">La <xref:System.Drawing.Pen> classe, utilisée pour dessiner des lignes, des formes en mode plan ou un rendu d’autres représentations géométriques.</span><span class="sxs-lookup"><span data-stu-id="3ad3f-143">The <xref:System.Drawing.Pen> class—Used for drawing lines, outlining shapes, or rendering other geometric representations.</span></span>  
  
- <span data-ttu-id="3ad3f-144">La <xref:System.Drawing.Brush> classe, utilisée pour remplir des zones de graphiques, telles que des formes remplies, des images ou du texte.</span><span class="sxs-lookup"><span data-stu-id="3ad3f-144">The <xref:System.Drawing.Brush> class—Used for filling areas of graphics, such as filled shapes, images, or text.</span></span>  
  
- <span data-ttu-id="3ad3f-145">La <xref:System.Drawing.Font> classe fournit une description des formes à utiliser lors du rendu du texte.</span><span class="sxs-lookup"><span data-stu-id="3ad3f-145">The <xref:System.Drawing.Font> class—Provides a description of what shapes to use when rendering text.</span></span>  
  
- <span data-ttu-id="3ad3f-146">La <xref:System.Drawing.Color> structure : représente les différentes couleurs à afficher.</span><span class="sxs-lookup"><span data-stu-id="3ad3f-146">The <xref:System.Drawing.Color> structure—Represents the different colors to display.</span></span>  
  
#### <a name="to-use-the-graphics-object-you-have-created"></a><span data-ttu-id="3ad3f-147">Pour utiliser l’objet Graphics que vous avez créé</span><span class="sxs-lookup"><span data-stu-id="3ad3f-147">To use the Graphics object you have created</span></span>  
  
- <span data-ttu-id="3ad3f-148">Utilisez l’objet approprié indiqué ci-dessus pour dessiner ce dont vous avez besoin.</span><span class="sxs-lookup"><span data-stu-id="3ad3f-148">Work with the appropriate object listed above to draw what you need.</span></span>  
  
     <span data-ttu-id="3ad3f-149">Pour plus d'informations, voir les rubriques suivantes :</span><span class="sxs-lookup"><span data-stu-id="3ad3f-149">For more information, see the following topics:</span></span>  
  
    |<span data-ttu-id="3ad3f-150">Pour effectuer le rendu</span><span class="sxs-lookup"><span data-stu-id="3ad3f-150">To render</span></span>|<span data-ttu-id="3ad3f-151">Consultez</span><span class="sxs-lookup"><span data-stu-id="3ad3f-151">See</span></span>|  
    |---------------|---------|  
    |<span data-ttu-id="3ad3f-152">Lignes</span><span class="sxs-lookup"><span data-stu-id="3ad3f-152">Lines</span></span>|[<span data-ttu-id="3ad3f-153">Guide pratique pour dessiner une ligne dans un Windows Form</span><span class="sxs-lookup"><span data-stu-id="3ad3f-153">How to: Draw a Line on a Windows Form</span></span>](how-to-draw-a-line-on-a-windows-form.md)|  
    |<span data-ttu-id="3ad3f-154">Formes</span><span class="sxs-lookup"><span data-stu-id="3ad3f-154">Shapes</span></span>|[<span data-ttu-id="3ad3f-155">Comment : dessiner une forme avec contour</span><span class="sxs-lookup"><span data-stu-id="3ad3f-155">How to: Draw an Outlined Shape</span></span>](how-to-draw-an-outlined-shape.md)|  
    |<span data-ttu-id="3ad3f-156">Texte</span><span class="sxs-lookup"><span data-stu-id="3ad3f-156">Text</span></span>|[<span data-ttu-id="3ad3f-157">Comment : dessiner du texte dans un Windows Form</span><span class="sxs-lookup"><span data-stu-id="3ad3f-157">How to: Draw Text on a Windows Form</span></span>](how-to-draw-text-on-a-windows-form.md)|  
    |<span data-ttu-id="3ad3f-158">Images</span><span class="sxs-lookup"><span data-stu-id="3ad3f-158">Images</span></span>|[<span data-ttu-id="3ad3f-159">Guide pratique pour rendre des images avec GDI+</span><span class="sxs-lookup"><span data-stu-id="3ad3f-159">How to: Render Images with GDI+</span></span>](how-to-render-images-with-gdi.md)|  
  
## <a name="see-also"></a><span data-ttu-id="3ad3f-160">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3ad3f-160">See also</span></span>

- [<span data-ttu-id="3ad3f-161">Mise en route de la programmation graphique</span><span class="sxs-lookup"><span data-stu-id="3ad3f-161">Getting Started with Graphics Programming</span></span>](getting-started-with-graphics-programming.md)
- [<span data-ttu-id="3ad3f-162">Graphiques et dessins dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3ad3f-162">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="3ad3f-163">Lignes, courbes et formes</span><span class="sxs-lookup"><span data-stu-id="3ad3f-163">Lines, Curves, and Shapes</span></span>](lines-curves-and-shapes.md)
- [<span data-ttu-id="3ad3f-164">Guide pratique pour rendre des images avec GDI+</span><span class="sxs-lookup"><span data-stu-id="3ad3f-164">How to: Render Images with GDI+</span></span>](how-to-render-images-with-gdi.md)
