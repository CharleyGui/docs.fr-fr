---
title: 'Comment : charger et afficher des métafichiers'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- examples [Windows Forms], metafiles
- metafiles [Windows Forms], displaying
ms.assetid: 60af1714-f148-4d85-a739-0557965ffa73
ms.openlocfilehash: 6c17e0b2d023ccf80b0d32301b7ee6765edcae9f
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424817"
---
# <a name="how-to-load-and-display-metafiles"></a><span data-ttu-id="cd133-102">Comment : charger et afficher des métafichiers</span><span class="sxs-lookup"><span data-stu-id="cd133-102">How to: Load and Display Metafiles</span></span>
<span data-ttu-id="cd133-103">La classe <xref:System.Drawing.Imaging.Metafile>, qui hérite de la classe <xref:System.Drawing.Image>, fournit des méthodes pour l’enregistrement, l’affichage et l’examen d’images vectorielles.</span><span class="sxs-lookup"><span data-stu-id="cd133-103">The <xref:System.Drawing.Imaging.Metafile> class, which inherits from the <xref:System.Drawing.Image> class, provides methods for recording, displaying, and examining vector images.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cd133-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="cd133-104">Example</span></span>  
 <span data-ttu-id="cd133-105">Pour afficher une image vectorielle (métafichier) sur l’écran, vous avez besoin d’un objet <xref:System.Drawing.Imaging.Metafile> et d’un objet <xref:System.Drawing.Graphics>.</span><span class="sxs-lookup"><span data-stu-id="cd133-105">To display a vector image (metafile) on the screen, you need a <xref:System.Drawing.Imaging.Metafile> object and a <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="cd133-106">Transmettez le nom d’un fichier (ou d’un flux) à un constructeur <xref:System.Drawing.Imaging.Metafile>.</span><span class="sxs-lookup"><span data-stu-id="cd133-106">Pass the name of a file (or a stream) to a <xref:System.Drawing.Imaging.Metafile> constructor.</span></span> <span data-ttu-id="cd133-107">Après avoir créé un objet <xref:System.Drawing.Imaging.Metafile>, transmettez cet objet <xref:System.Drawing.Imaging.Metafile> à la méthode <xref:System.Drawing.Graphics.DrawImage%2A> d’un objet <xref:System.Drawing.Graphics>.</span><span class="sxs-lookup"><span data-stu-id="cd133-107">After you have created a <xref:System.Drawing.Imaging.Metafile> object, pass that <xref:System.Drawing.Imaging.Metafile> object to the <xref:System.Drawing.Graphics.DrawImage%2A> method of a <xref:System.Drawing.Graphics> object.</span></span>  
  
 <span data-ttu-id="cd133-108">L’exemple crée un objet <xref:System.Drawing.Imaging.Metafile> à partir d’un fichier EMF (métafichier amélioré), puis dessine l’image avec son angle supérieur gauche à (60, 10).</span><span class="sxs-lookup"><span data-stu-id="cd133-108">The example creates a <xref:System.Drawing.Imaging.Metafile> object from an EMF (enhanced metafile) file and then draws the image with its upper-left corner at (60, 10).</span></span>  
  
 <span data-ttu-id="cd133-109">L’illustration suivante montre le métafichier dessiné à l’emplacement spécifié.</span><span class="sxs-lookup"><span data-stu-id="cd133-109">The following illustration shows the metafile drawn at the specified location.</span></span>  
  
 <span data-ttu-id="cd133-110">![Capture d’écran montrant la position de l’image.](./media/how-to-load-and-display-metafiles/metafile-drawn-specified-location.png "imageposition2")</span><span class="sxs-lookup"><span data-stu-id="cd133-110">![Screenshot showing image position.](./media/how-to-load-and-display-metafiles/metafile-drawn-specified-location.png "imageposition2")</span></span>  
  
 [!code-csharp[System.Drawing.WorkingWithImages#41](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.WorkingWithImages#41](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#41)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="cd133-111">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="cd133-111">Compiling the Code</span></span>  
 <span data-ttu-id="cd133-112">L’exemple précédent est conçu pour être utilisé avec Windows Forms, et il requiert <xref:System.Windows.Forms.PaintEventArgs> `e`, qui est un paramètre du gestionnaire d’événements <xref:System.Windows.Forms.Control.Paint>.</span><span class="sxs-lookup"><span data-stu-id="cd133-112">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd133-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cd133-113">See also</span></span>

- [<span data-ttu-id="cd133-114">Utilisation des images, bitmaps, icônes et métafichiers</span><span class="sxs-lookup"><span data-stu-id="cd133-114">Working with Images, Bitmaps, Icons, and Metafiles</span></span>](working-with-images-bitmaps-icons-and-metafiles.md)
