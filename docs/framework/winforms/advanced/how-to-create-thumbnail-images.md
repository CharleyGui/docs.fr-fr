---
title: 'Procédure : créer des images miniatures'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- thumbnail images [Windows Forms], creating
- images [Windows Forms], creating thumbnails
ms.assetid: e956242a-1e5b-4217-a3cf-5f3fb45d00ba
ms.openlocfilehash: 786a92d99f5e7a0c27f502efa9a5fe617ac4d4d6
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923761"
---
# <a name="how-to-create-thumbnail-images"></a><span data-ttu-id="66436-102">Procédure : créer des images miniatures</span><span class="sxs-lookup"><span data-stu-id="66436-102">How to: Create Thumbnail Images</span></span>
<span data-ttu-id="66436-103">Une image miniature est une petite version d’une image.</span><span class="sxs-lookup"><span data-stu-id="66436-103">A thumbnail image is a small version of an image.</span></span> <span data-ttu-id="66436-104">Vous pouvez créer une image miniature en appelant la <xref:System.Drawing.Image.GetThumbnailImage%2A> méthode d’un <xref:System.Drawing.Image> objet.</span><span class="sxs-lookup"><span data-stu-id="66436-104">You can create a thumbnail image by calling the <xref:System.Drawing.Image.GetThumbnailImage%2A> method of an <xref:System.Drawing.Image> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="66436-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="66436-105">Example</span></span>  
 <span data-ttu-id="66436-106">L’exemple suivant construit un <xref:System.Drawing.Image> objet à partir d’un fichier jpg.</span><span class="sxs-lookup"><span data-stu-id="66436-106">The following example constructs an <xref:System.Drawing.Image> object from a JPG file.</span></span> <span data-ttu-id="66436-107">L’image d’origine a une largeur de 640 pixels et une hauteur de 479 pixels.</span><span class="sxs-lookup"><span data-stu-id="66436-107">The original image has a width of 640 pixels and a height of 479 pixels.</span></span> <span data-ttu-id="66436-108">Le code crée une image miniature qui a une largeur de 100 pixels et une hauteur de 100 pixels.</span><span class="sxs-lookup"><span data-stu-id="66436-108">The code creates a thumbnail image that has a width of 100 pixels and a height of 100 pixels.</span></span>  
  
 <span data-ttu-id="66436-109">L’illustration suivante montre l’image miniature:</span><span class="sxs-lookup"><span data-stu-id="66436-109">The following illustration shows the thumbnail image:</span></span>  
  
 ![Capture d’écran montrant la miniature de sortie.](./media/how-to-create-thumbnail-images/construct-thumbnail-image.png)  
  
> [!NOTE]
> <span data-ttu-id="66436-111">Dans cet exemple, une méthode de rappel est déclarée, mais jamais utilisée.</span><span class="sxs-lookup"><span data-stu-id="66436-111">In this example, a callback method is declared, but never used.</span></span> <span data-ttu-id="66436-112">Cela prend en charge toutes les versions de GDI+.</span><span class="sxs-lookup"><span data-stu-id="66436-112">This supports all versions of GDI+.</span></span>  
  
 [!code-csharp[System.Drawing.WorkingWithImages#71](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#71)]
 [!code-vb[System.Drawing.WorkingWithImages#71](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#71)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="66436-113">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="66436-113">Compiling the Code</span></span>  
 <span data-ttu-id="66436-114">L’exemple précédent est conçu pour être utilisé avec Windows Forms, et il <xref:System.Windows.Forms.PaintEventArgs> nécessite `e`, qui <xref:System.Windows.Forms.Control.Paint> est un paramètre du gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="66436-114">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="66436-115">Pour exécuter l’exemple, procédez comme suit:</span><span class="sxs-lookup"><span data-stu-id="66436-115">To run the example, follow these steps:</span></span>  
  
1. <span data-ttu-id="66436-116">Créez une application Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="66436-116">Create a new Windows Forms application.</span></span>  
  
2. <span data-ttu-id="66436-117">Ajoutez l’exemple de code au formulaire.</span><span class="sxs-lookup"><span data-stu-id="66436-117">Add the example code to the form.</span></span>  
  
3. <span data-ttu-id="66436-118">Créer un gestionnaire pour l’événement du <xref:System.Windows.Forms.Control.Paint> formulaire</span><span class="sxs-lookup"><span data-stu-id="66436-118">Create a handler for the form's <xref:System.Windows.Forms.Control.Paint> event</span></span>  
  
4. <span data-ttu-id="66436-119">Dans le <xref:System.Windows.Forms.Control.Paint> gestionnaire, appelez la `GetThumbnail` méthode et transmettez <xref:System.Windows.Forms.PaintEventArgs> `e` .</span><span class="sxs-lookup"><span data-stu-id="66436-119">In the <xref:System.Windows.Forms.Control.Paint> handler, call the `GetThumbnail` method and pass `e` for <xref:System.Windows.Forms.PaintEventArgs>.</span></span>  
  
5. <span data-ttu-id="66436-120">Recherchez un fichier image dont vous souhaitez créer une miniature.</span><span class="sxs-lookup"><span data-stu-id="66436-120">Find an image file that you want to make a thumbnail of.</span></span>  
  
6. <span data-ttu-id="66436-121">Dans la `GetThumbnail` méthode, spécifiez le chemin d’accès et le nom de fichier de votre image.</span><span class="sxs-lookup"><span data-stu-id="66436-121">In the `GetThumbnail` method, specify the path and file name to your image.</span></span>  
  
7. <span data-ttu-id="66436-122">Appuyez sur F5 pour exécuter l’exemple.</span><span class="sxs-lookup"><span data-stu-id="66436-122">Press F5 to run the example.</span></span>  
  
     <span data-ttu-id="66436-123">Une image miniature 100 par 100 apparaît sur le formulaire.</span><span class="sxs-lookup"><span data-stu-id="66436-123">A 100 by 100 thumbnail image appears on the form.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66436-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="66436-124">See also</span></span>

- [<span data-ttu-id="66436-125">Images, bitmaps et métafichiers</span><span class="sxs-lookup"><span data-stu-id="66436-125">Images, Bitmaps, and Metafiles</span></span>](images-bitmaps-and-metafiles.md)
- [<span data-ttu-id="66436-126">Utilisation des images, bitmaps, icônes et métafichiers</span><span class="sxs-lookup"><span data-stu-id="66436-126">Working with Images, Bitmaps, Icons, and Metafiles</span></span>](working-with-images-bitmaps-icons-and-metafiles.md)
