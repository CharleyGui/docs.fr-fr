---
title: 'Comment : rendre des images avec GDI+'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- images [Windows Forms], creating
- GDI+, rendering existing images
ms.assetid: c128b79a-3e31-47d8-9e66-3470f570a056
ms.openlocfilehash: fffe1f1052d7323d234985b7e752866f2e89657d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182501"
---
# <a name="how-to-render-images-with-gdi"></a><span data-ttu-id="6e6e4-102">Comment : rendre des images avec GDI+</span><span class="sxs-lookup"><span data-stu-id="6e6e4-102">How to: Render Images with GDI+</span></span>
<span data-ttu-id="6e6e4-103">Vous pouvez utiliser GDIMD pour rendre les images qui existent sous forme de fichiers dans vos applications.</span><span class="sxs-lookup"><span data-stu-id="6e6e4-103">You can use GDI+ to render images that exist as files in your applications.</span></span> <span data-ttu-id="6e6e4-104">Vous le faites en créant <xref:System.Drawing.Image> un nouvel <xref:System.Drawing.Bitmap>objet d’une classe (comme), en créant un <xref:System.Drawing.Graphics> objet <xref:System.Drawing.Graphics.DrawImage%2A> qui <xref:System.Drawing.Graphics> se réfère à la surface de dessin que vous voulez utiliser, et en appelant la méthode de l’objet.</span><span class="sxs-lookup"><span data-stu-id="6e6e4-104">You do this by creating a new object of an <xref:System.Drawing.Image> class (such as <xref:System.Drawing.Bitmap>), creating a <xref:System.Drawing.Graphics> object that refers to the drawing surface you want to use, and calling the <xref:System.Drawing.Graphics.DrawImage%2A> method of the <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="6e6e4-105">L’image est peinte sur la surface de dessin représentée par la classe graphics.</span><span class="sxs-lookup"><span data-stu-id="6e6e4-105">The image will be painted onto the drawing surface represented by the graphics class.</span></span> <span data-ttu-id="6e6e4-106">Vous pouvez utiliser l’éditeur d’images pour créer et modifier des fichiers d’images au moment de la conception, et les rendre avec GDIMD au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="6e6e4-106">You can use the Image Editor to create and edit image files at design time, and render them with GDI+ at run time.</span></span> <span data-ttu-id="6e6e4-107">Pour plus d’informations, consultez [Éditeur d’images pour les icônes](/cpp/windows/image-editor-for-icons).</span><span class="sxs-lookup"><span data-stu-id="6e6e4-107">For more information, see [Image Editor for Icons](/cpp/windows/image-editor-for-icons).</span></span>  
  
### <a name="to-render-an-image-with-gdi"></a><span data-ttu-id="6e6e4-108">Pour afficher une image avec GDI+</span><span class="sxs-lookup"><span data-stu-id="6e6e4-108">To render an image with GDI+</span></span>  
  
1. <span data-ttu-id="6e6e4-109">Créez un objet qui représente l’image à afficher.</span><span class="sxs-lookup"><span data-stu-id="6e6e4-109">Create an object representing the image you want to display.</span></span> <span data-ttu-id="6e6e4-110">Cet objet doit être membre d’une <xref:System.Drawing.Image>classe <xref:System.Drawing.Bitmap> qui <xref:System.Drawing.Imaging.Metafile>hérite de , comme ou .</span><span class="sxs-lookup"><span data-stu-id="6e6e4-110">This object must be a member of a class that inherits from <xref:System.Drawing.Image>, such as <xref:System.Drawing.Bitmap> or <xref:System.Drawing.Imaging.Metafile>.</span></span> <span data-ttu-id="6e6e4-111">Voici un exemple :</span><span class="sxs-lookup"><span data-stu-id="6e6e4-111">An example is shown:</span></span>  
  
    ```vb  
    ' Uses the System.Environment.GetFolderPath to get the path to the
    ' current user's MyPictures folder.  
    Dim myBitmap as New Bitmap _  
       (System.Environment.GetFolderPath _  
          (System.Environment.SpecialFolder.MyPictures))  
    ```  
  
    ```csharp  
    // Uses the System.Environment.GetFolderPath to get the path to the
    // current user's MyPictures folder.  
    Bitmap myBitmap = new Bitmap  
       (System.Environment.GetFolderPath  
          (System.Environment.SpecialFolder.MyPictures));  
    ```  
  
    ```cpp  
    // Uses the System.Environment.GetFolderPath to get the path to the
    // current user's MyPictures folder.  
    Bitmap^ myBitmap = gcnew Bitmap  
       (System::Environment::GetFolderPath  
          (System::Environment::SpecialFolder::MyPictures));  
    ```  
  
2. <span data-ttu-id="6e6e4-112">Créez <xref:System.Drawing.Graphics> un objet qui représente la surface de dessin que vous souhaitez utiliser.</span><span class="sxs-lookup"><span data-stu-id="6e6e4-112">Create a <xref:System.Drawing.Graphics> object that represents the drawing surface you want to use.</span></span> <span data-ttu-id="6e6e4-113">Pour plus d’informations, consultez [Guide pratique pour créer des objets graphiques pour le dessin](how-to-create-graphics-objects-for-drawing.md).</span><span class="sxs-lookup"><span data-stu-id="6e6e4-113">For more information, see [How to: Create Graphics Objects for Drawing](how-to-create-graphics-objects-for-drawing.md).</span></span>  
  
    ```vb  
    ' Creates a Graphics object that represents the drawing surface of
    ' Button1.  
    Dim g as Graphics = Button1.CreateGraphics  
    ```  
  
    ```csharp  
    // Creates a Graphics object that represents the drawing surface of
    // Button1.  
    Graphics g = Button1.CreateGraphics();  
    ```  
  
    ```cpp  
    // Creates a Graphics object that represents the drawing surface of
    // Button1.  
    Graphics^ g = button1->CreateGraphics();  
    ```  
  
3. <span data-ttu-id="6e6e4-114">Appelez <xref:System.Drawing.Graphics.DrawImage%2A> l’objet graphique de votre objet graphique pour rendre l’image.</span><span class="sxs-lookup"><span data-stu-id="6e6e4-114">Call the <xref:System.Drawing.Graphics.DrawImage%2A> of your graphics object to render the image.</span></span> <span data-ttu-id="6e6e4-115">Vous devez spécifier l’image à dessiner et ses coordonnées.</span><span class="sxs-lookup"><span data-stu-id="6e6e4-115">You must specify both the image to be drawn, and the coordinates where it is to be drawn.</span></span>  
  
    ```vb  
    g.DrawImage(myBitmap, 1, 1)  
    ```  
  
    ```csharp  
    g.DrawImage(myBitmap, 1, 1);  
    ```  
  
    ```cpp  
    g->DrawImage(myBitmap, 1, 1);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="6e6e4-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6e6e4-116">See also</span></span>

- [<span data-ttu-id="6e6e4-117">Mise en route de la programmation graphique</span><span class="sxs-lookup"><span data-stu-id="6e6e4-117">Getting Started with Graphics Programming</span></span>](getting-started-with-graphics-programming.md)
- [<span data-ttu-id="6e6e4-118">Comment : créer des objets graphiques pour le dessin</span><span class="sxs-lookup"><span data-stu-id="6e6e4-118">How to: Create Graphics Objects for Drawing</span></span>](how-to-create-graphics-objects-for-drawing.md)
- [<span data-ttu-id="6e6e4-119">Stylets, lignes et rectangles dans GDI+</span><span class="sxs-lookup"><span data-stu-id="6e6e4-119">Pens, Lines, and Rectangles in GDI+</span></span>](pens-lines-and-rectangles-in-gdi.md)
- [<span data-ttu-id="6e6e4-120">Comment : dessiner du texte dans un Windows Form</span><span class="sxs-lookup"><span data-stu-id="6e6e4-120">How to: Draw Text on a Windows Form</span></span>](how-to-draw-text-on-a-windows-form.md)
- [<span data-ttu-id="6e6e4-121">Graphiques et dessins dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6e6e4-121">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="6e6e4-122">Dessin de ligne ou de figures fermées</span><span class="sxs-lookup"><span data-stu-id="6e6e4-122">Drawing Lines or Closed Figures</span></span>](/cpp/windows/drawing-lines-or-closed-figures-image-editor-for-icons)
- [<span data-ttu-id="6e6e4-123">Éditeur d’images pour les icônes</span><span class="sxs-lookup"><span data-stu-id="6e6e4-123">Image Editor for Icons</span></span>](/cpp/windows/image-editor-for-icons)
