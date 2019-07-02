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
# <a name="how-to-create-graphics-objects-for-drawing"></a><span data-ttu-id="4965a-102">Procédure : créer des objets de graphismes pour le dessin</span><span class="sxs-lookup"><span data-stu-id="4965a-102">How to: Create Graphics Objects for Drawing</span></span>
<span data-ttu-id="4965a-103">Avant que vous pouvez dessiner des lignes et des formes, rendre du texte ou afficher et manipuler des images avec GDI +, vous devez créer un <xref:System.Drawing.Graphics> objet.</span><span class="sxs-lookup"><span data-stu-id="4965a-103">Before you can draw lines and shapes, render text, or display and manipulate images with GDI+, you need to create a <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="4965a-104">Le <xref:System.Drawing.Graphics> objet représente une surface de dessin GDI + et est l’objet qui est utilisé pour créer des images graphiques.</span><span class="sxs-lookup"><span data-stu-id="4965a-104">The <xref:System.Drawing.Graphics> object represents a GDI+ drawing surface, and is the object that is used to create graphical images.</span></span>  
  
 <span data-ttu-id="4965a-105">Il existe deux étapes dans l’utilisation de graphiques :</span><span class="sxs-lookup"><span data-stu-id="4965a-105">There are two steps in working with graphics:</span></span>  
  
1. <span data-ttu-id="4965a-106">Création d’un <xref:System.Drawing.Graphics> objet.</span><span class="sxs-lookup"><span data-stu-id="4965a-106">Creating a <xref:System.Drawing.Graphics> object.</span></span>  
  
2. <span data-ttu-id="4965a-107">À l’aide de la <xref:System.Drawing.Graphics> objet pour dessiner des lignes et des formes, de rendre du texte ou d’afficher et de manipuler des images.</span><span class="sxs-lookup"><span data-stu-id="4965a-107">Using the <xref:System.Drawing.Graphics> object to draw lines and shapes, render text, or display and manipulate images.</span></span>  
  
## <a name="creating-a-graphics-object"></a><span data-ttu-id="4965a-108">Création d’un objet Graphics</span><span class="sxs-lookup"><span data-stu-id="4965a-108">Creating a Graphics Object</span></span>  
 <span data-ttu-id="4965a-109">Un objet graphics peut être créé de plusieurs façons.</span><span class="sxs-lookup"><span data-stu-id="4965a-109">A graphics object can be created in a variety of ways.</span></span>  
  
#### <a name="to-create-a-graphics-object"></a><span data-ttu-id="4965a-110">Pour créer un objet graphics</span><span class="sxs-lookup"><span data-stu-id="4965a-110">To create a graphics object</span></span>  
  
- <span data-ttu-id="4965a-111">Reçoivent une référence à un objet graphique dans le cadre de la <xref:System.Windows.Forms.PaintEventArgs> dans le <xref:System.Windows.Forms.Control.Paint> événement d’un formulaire ou contrôle.</span><span class="sxs-lookup"><span data-stu-id="4965a-111">Receive a reference to a graphics object as part of the <xref:System.Windows.Forms.PaintEventArgs> in the <xref:System.Windows.Forms.Control.Paint> event of a form or control.</span></span> <span data-ttu-id="4965a-112">C’est généralement utilisée pour obtenir une référence à un objet graphique lors de la création du code de peinture d’un contrôle.</span><span class="sxs-lookup"><span data-stu-id="4965a-112">This is usually how you obtain a reference to a graphics object when creating painting code for a control.</span></span> <span data-ttu-id="4965a-113">De même, vous pouvez également obtenir un objet graphique en tant que propriété de la <xref:System.Drawing.Printing.PrintPageEventArgs> lors du traitement de la <xref:System.Drawing.Printing.PrintDocument.PrintPage> événement pour un <xref:System.Drawing.Printing.PrintDocument>.</span><span class="sxs-lookup"><span data-stu-id="4965a-113">Similarly, you can also obtain a graphics object as a property of the <xref:System.Drawing.Printing.PrintPageEventArgs> when handling the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event for a <xref:System.Drawing.Printing.PrintDocument>.</span></span>  
  
     <span data-ttu-id="4965a-114">ou</span><span class="sxs-lookup"><span data-stu-id="4965a-114">-or-</span></span>  
  
- <span data-ttu-id="4965a-115">Appelez le <xref:System.Windows.Forms.Control.CreateGraphics%2A> méthode d’un contrôle ou un formulaire afin d’obtenir une référence à un <xref:System.Drawing.Graphics> objet qui représente la surface de dessin de ce contrôle ou formulaire.</span><span class="sxs-lookup"><span data-stu-id="4965a-115">Call the <xref:System.Windows.Forms.Control.CreateGraphics%2A> method of a control or form to obtain a reference to a <xref:System.Drawing.Graphics> object that represents the drawing surface of that control or form.</span></span> <span data-ttu-id="4965a-116">Utilisez cette méthode si vous souhaitez dessiner sur un formulaire ou un contrôle qui existe déjà.</span><span class="sxs-lookup"><span data-stu-id="4965a-116">Use this method if you want to draw on a form or control that already exists.</span></span>  
  
     <span data-ttu-id="4965a-117">ou</span><span class="sxs-lookup"><span data-stu-id="4965a-117">-or-</span></span>  
  
- <span data-ttu-id="4965a-118">Créer un <xref:System.Drawing.Graphics> objet à partir de n’importe quel objet qui hérite de <xref:System.Drawing.Image>.</span><span class="sxs-lookup"><span data-stu-id="4965a-118">Create a <xref:System.Drawing.Graphics> object from any object that inherits from <xref:System.Drawing.Image>.</span></span> <span data-ttu-id="4965a-119">Cette approche est utile lorsque vous souhaitez modifier une image existante.</span><span class="sxs-lookup"><span data-stu-id="4965a-119">This approach is useful when you want to alter an already existing image.</span></span>  
  
     <span data-ttu-id="4965a-120">Les sections suivantes fournissent plus d’informations sur chacun de ces processus.</span><span class="sxs-lookup"><span data-stu-id="4965a-120">The following sections give details about each of these processes.</span></span>  
  
## <a name="painteventargs-in-the-paint-event-handler"></a><span data-ttu-id="4965a-121">PaintEventArgs dans le Gestionnaire d’événements Paint</span><span class="sxs-lookup"><span data-stu-id="4965a-121">PaintEventArgs in the Paint Event Handler</span></span>  
 <span data-ttu-id="4965a-122">Lorsque vous programmez le <xref:System.Windows.Forms.PaintEventHandler> pour les contrôles ou le <xref:System.Drawing.Printing.PrintDocument.PrintPage> pour un <xref:System.Drawing.Printing.PrintDocument>, un objet graphics est fourni en tant qu’une des propriétés de <xref:System.Windows.Forms.PaintEventArgs> ou <xref:System.Drawing.Printing.PrintPageEventArgs>.</span><span class="sxs-lookup"><span data-stu-id="4965a-122">When programming the <xref:System.Windows.Forms.PaintEventHandler> for controls or the <xref:System.Drawing.Printing.PrintDocument.PrintPage> for a <xref:System.Drawing.Printing.PrintDocument>, a graphics object is provided as one of the properties of <xref:System.Windows.Forms.PaintEventArgs> or <xref:System.Drawing.Printing.PrintPageEventArgs>.</span></span>  
  
#### <a name="to-obtain-a-reference-to-a-graphics-object-from-the-painteventargs-in-the-paint-event"></a><span data-ttu-id="4965a-123">Pour obtenir une référence à un objet graphique de PaintEventArgs de l’événement Paint</span><span class="sxs-lookup"><span data-stu-id="4965a-123">To obtain a reference to a Graphics object from the PaintEventArgs in the Paint event</span></span>  
  
1. <span data-ttu-id="4965a-124">Déclarez le <xref:System.Drawing.Graphics> objet.</span><span class="sxs-lookup"><span data-stu-id="4965a-124">Declare the <xref:System.Drawing.Graphics> object.</span></span>  
  
2. <span data-ttu-id="4965a-125">Affectez la variable pour faire référence à la <xref:System.Drawing.Graphics> objet passé en tant que partie de la <xref:System.Windows.Forms.PaintEventArgs>.</span><span class="sxs-lookup"><span data-stu-id="4965a-125">Assign the variable to refer to the <xref:System.Drawing.Graphics> object passed as part of the <xref:System.Windows.Forms.PaintEventArgs>.</span></span>  
  
3. <span data-ttu-id="4965a-126">Insérer du code pour peindre le formulaire ou contrôle.</span><span class="sxs-lookup"><span data-stu-id="4965a-126">Insert code to paint the form or control.</span></span>  
  
     <span data-ttu-id="4965a-127">L’exemple suivant indique comment référencer un <xref:System.Drawing.Graphics> de l’objet à partir de la <xref:System.Windows.Forms.PaintEventArgs> dans le <xref:System.Windows.Forms.Control.Paint> événement :</span><span class="sxs-lookup"><span data-stu-id="4965a-127">The following example shows how to reference a <xref:System.Drawing.Graphics> object from the <xref:System.Windows.Forms.PaintEventArgs> in the <xref:System.Windows.Forms.Control.Paint> event:</span></span>  
  
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
  
## <a name="creategraphics-method"></a><span data-ttu-id="4965a-128">Méthode CreateGraphics</span><span class="sxs-lookup"><span data-stu-id="4965a-128">CreateGraphics Method</span></span>  
 <span data-ttu-id="4965a-129">Vous pouvez également utiliser le <xref:System.Windows.Forms.Control.CreateGraphics%2A> méthode d’un contrôle ou un formulaire afin d’obtenir une référence à un <xref:System.Drawing.Graphics> objet qui représente la surface de dessin de ce contrôle ou formulaire.</span><span class="sxs-lookup"><span data-stu-id="4965a-129">You can also use the <xref:System.Windows.Forms.Control.CreateGraphics%2A> method of a control or form to obtain a reference to a <xref:System.Drawing.Graphics> object that represents the drawing surface of that control or form.</span></span>  
  
#### <a name="to-create-a-graphics-object-with-the-creategraphics-method"></a><span data-ttu-id="4965a-130">Pour créer un objet Graphics avec la méthode CreateGraphics</span><span class="sxs-lookup"><span data-stu-id="4965a-130">To create a Graphics object with the CreateGraphics method</span></span>  
  
- <span data-ttu-id="4965a-131">Appelez le <xref:System.Windows.Forms.Control.CreateGraphics%2A> méthode du formulaire ou contrôle sur lequel vous souhaitez restituer des graphiques.</span><span class="sxs-lookup"><span data-stu-id="4965a-131">Call the <xref:System.Windows.Forms.Control.CreateGraphics%2A> method of the form or control upon which you want to render graphics.</span></span>  
  
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
  
## <a name="create-from-an-image-object"></a><span data-ttu-id="4965a-132">Créer à partir d’un objet Image</span><span class="sxs-lookup"><span data-stu-id="4965a-132">Create from an Image Object</span></span>  
 <span data-ttu-id="4965a-133">En outre, vous pouvez créer un objet graphique à partir de n’importe quel objet qui dérive de la <xref:System.Drawing.Image> classe.</span><span class="sxs-lookup"><span data-stu-id="4965a-133">Additionally, you can create a graphics object from any object that derives from the <xref:System.Drawing.Image> class.</span></span>  
  
#### <a name="to-create-a-graphics-object-from-an-image"></a><span data-ttu-id="4965a-134">Pour créer un objet graphique à partir d’une Image</span><span class="sxs-lookup"><span data-stu-id="4965a-134">To create a Graphics object from an Image</span></span>  
  
- <span data-ttu-id="4965a-135">Appelez le <xref:System.Drawing.Graphics.FromImage%2A?displayProperty=nameWithType> méthode, en fournissant le nom de la variable de l’Image à partir de laquelle vous souhaitez créer un <xref:System.Drawing.Graphics> objet.</span><span class="sxs-lookup"><span data-stu-id="4965a-135">Call the <xref:System.Drawing.Graphics.FromImage%2A?displayProperty=nameWithType> method, supplying the name of the Image variable from which you want to create a <xref:System.Drawing.Graphics> object.</span></span>  
  
     <span data-ttu-id="4965a-136">L’exemple suivant montre comment utiliser un <xref:System.Drawing.Bitmap> objet :</span><span class="sxs-lookup"><span data-stu-id="4965a-136">The following example shows how to use a <xref:System.Drawing.Bitmap> object:</span></span>  
  
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
>  <span data-ttu-id="4965a-137">Vous pouvez uniquement créer <xref:System.Drawing.Graphics> objets à partir de fichiers .bmp non indexés, tels que des fichiers .bmp 16 bits, 24 bits et 32 bits.</span><span class="sxs-lookup"><span data-stu-id="4965a-137">You can only create <xref:System.Drawing.Graphics> objects from nonindexed .bmp files, such as 16-bit, 24-bit, and 32-bit .bmp files.</span></span> <span data-ttu-id="4965a-138">Chaque pixel de fichiers .bmp non indexée conserve une couleur, contrairement aux pixels des fichiers .bmp indexés, qui contiennent un index dans une table des couleurs.</span><span class="sxs-lookup"><span data-stu-id="4965a-138">Each pixel of nonindexed .bmp files holds a color, in contrast to pixels of indexed .bmp files, which hold an index to a color table.</span></span>  
  
## <a name="drawing-and-manipulating-shapes-and-images"></a><span data-ttu-id="4965a-139">Dessin et manipulation de formes et des Images</span><span class="sxs-lookup"><span data-stu-id="4965a-139">Drawing and Manipulating Shapes and Images</span></span>  
 <span data-ttu-id="4965a-140">Après sa création, un <xref:System.Drawing.Graphics> objet peut être utilisé pour dessiner des lignes et des formes, de rendre du texte ou d’afficher et de manipuler des images.</span><span class="sxs-lookup"><span data-stu-id="4965a-140">After it is created, a <xref:System.Drawing.Graphics> object may be used to draw lines and shapes, render text, or display and manipulate images.</span></span> <span data-ttu-id="4965a-141">Les objets principal qui sont utilisés avec la <xref:System.Drawing.Graphics> objet sont :</span><span class="sxs-lookup"><span data-stu-id="4965a-141">The principal objects that are used with the <xref:System.Drawing.Graphics> object are:</span></span>  
  
- <span data-ttu-id="4965a-142">Le <xref:System.Drawing.Pen> classe — utilisé pour dessiner des lignes, le mode plan des formes ou rendre d’autres représentations géométriques.</span><span class="sxs-lookup"><span data-stu-id="4965a-142">The <xref:System.Drawing.Pen> class—Used for drawing lines, outlining shapes, or rendering other geometric representations.</span></span>  
  
- <span data-ttu-id="4965a-143">Le <xref:System.Drawing.Brush> classe — utilisée pour remplir des zones de graphiques, tels que le texte, des images ou des formes remplies.</span><span class="sxs-lookup"><span data-stu-id="4965a-143">The <xref:System.Drawing.Brush> class—Used for filling areas of graphics, such as filled shapes, images, or text.</span></span>  
  
- <span data-ttu-id="4965a-144">Le <xref:System.Drawing.Font> classe — fournit une description les formes à utiliser lors du rendu de texte.</span><span class="sxs-lookup"><span data-stu-id="4965a-144">The <xref:System.Drawing.Font> class—Provides a description of what shapes to use when rendering text.</span></span>  
  
- <span data-ttu-id="4965a-145">Le <xref:System.Drawing.Color> structure — représente les différentes couleurs à afficher.</span><span class="sxs-lookup"><span data-stu-id="4965a-145">The <xref:System.Drawing.Color> structure—Represents the different colors to display.</span></span>  
  
#### <a name="to-use-the-graphics-object-you-have-created"></a><span data-ttu-id="4965a-146">Pour utiliser l’objet Graphics, vous avez créé</span><span class="sxs-lookup"><span data-stu-id="4965a-146">To use the Graphics object you have created</span></span>  
  
- <span data-ttu-id="4965a-147">Travailler avec l’objet approprié répertoriée ci-dessus pour dessiner ce dont vous avez besoin.</span><span class="sxs-lookup"><span data-stu-id="4965a-147">Work with the appropriate object listed above to draw what you need.</span></span>  
  
     <span data-ttu-id="4965a-148">Pour plus d’informations, consultez les rubriques suivantes :</span><span class="sxs-lookup"><span data-stu-id="4965a-148">For more information, see the following topics:</span></span>  
  
    |<span data-ttu-id="4965a-149">Pour effectuer le rendu</span><span class="sxs-lookup"><span data-stu-id="4965a-149">To render</span></span>|<span data-ttu-id="4965a-150">Voir</span><span class="sxs-lookup"><span data-stu-id="4965a-150">See</span></span>|  
    |---------------|---------|  
    |<span data-ttu-id="4965a-151">Lignes</span><span class="sxs-lookup"><span data-stu-id="4965a-151">Lines</span></span>|[<span data-ttu-id="4965a-152">Guide pratique pour Dessiner une ligne dans un formulaire Windows</span><span class="sxs-lookup"><span data-stu-id="4965a-152">How to: Draw a Line on a Windows Form</span></span>](how-to-draw-a-line-on-a-windows-form.md)|  
    |<span data-ttu-id="4965a-153">Shapes</span><span class="sxs-lookup"><span data-stu-id="4965a-153">Shapes</span></span>|[<span data-ttu-id="4965a-154">Guide pratique pour Dessiner une forme avec contour</span><span class="sxs-lookup"><span data-stu-id="4965a-154">How to: Draw an Outlined Shape</span></span>](how-to-draw-an-outlined-shape.md)|  
    |<span data-ttu-id="4965a-155">Texte</span><span class="sxs-lookup"><span data-stu-id="4965a-155">Text</span></span>|[<span data-ttu-id="4965a-156">Guide pratique pour Dessiner du texte dans un formulaire Windows</span><span class="sxs-lookup"><span data-stu-id="4965a-156">How to: Draw Text on a Windows Form</span></span>](how-to-draw-text-on-a-windows-form.md)|  
    |<span data-ttu-id="4965a-157">Images</span><span class="sxs-lookup"><span data-stu-id="4965a-157">Images</span></span>|[<span data-ttu-id="4965a-158">Guide pratique pour Rendre des Images avec GDI +</span><span class="sxs-lookup"><span data-stu-id="4965a-158">How to: Render Images with GDI+</span></span>](how-to-render-images-with-gdi.md)|  
  
## <a name="see-also"></a><span data-ttu-id="4965a-159">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4965a-159">See also</span></span>

- [<span data-ttu-id="4965a-160">Mise en route de la programmation graphique</span><span class="sxs-lookup"><span data-stu-id="4965a-160">Getting Started with Graphics Programming</span></span>](getting-started-with-graphics-programming.md)
- [<span data-ttu-id="4965a-161">Graphiques et dessins dans Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4965a-161">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="4965a-162">Lignes, courbes et formes</span><span class="sxs-lookup"><span data-stu-id="4965a-162">Lines, Curves, and Shapes</span></span>](lines-curves-and-shapes.md)
- [<span data-ttu-id="4965a-163">Guide pratique pour Rendre des Images avec GDI +</span><span class="sxs-lookup"><span data-stu-id="4965a-163">How to: Render Images with GDI+</span></span>](how-to-render-images-with-gdi.md)
