---
title: 'Procédure : utiliser le mode d’interpolation pour contrôler la qualité d’image pendant la mise à l’échelle'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- interpolation mode [Windows Forms], controlling image quality
- images [Windows Forms], scaling
- images [Windows Forms], controlling quality
ms.assetid: fde9bccf-8aa5-4b0d-ba4b-788740627b02
ms.openlocfilehash: ab0ff93b3ee26467c0de448efd31b698167f95c2
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67505713"
---
# <a name="how-to-use-interpolation-mode-to-control-image-quality-during-scaling"></a><span data-ttu-id="5d960-102">Procédure : utiliser le mode d’interpolation pour contrôler la qualité d’image pendant la mise à l’échelle</span><span class="sxs-lookup"><span data-stu-id="5d960-102">How to: Use Interpolation Mode to Control Image Quality During Scaling</span></span>
<span data-ttu-id="5d960-103">Le mode d’interpolation d’une <xref:System.Drawing.Graphics> objet influe sur les façon dont GDI + dimensionne (étire et réduit) les images.</span><span class="sxs-lookup"><span data-stu-id="5d960-103">The interpolation mode of a <xref:System.Drawing.Graphics> object influences the way GDI+ scales (stretches and shrinks) images.</span></span> <span data-ttu-id="5d960-104">Le <xref:System.Drawing.Drawing2D.InterpolationMode> énumération définit plusieurs modes d’interpolation, certains d'entre eux sont affichés dans la liste suivante :</span><span class="sxs-lookup"><span data-stu-id="5d960-104">The <xref:System.Drawing.Drawing2D.InterpolationMode> enumeration defines several interpolation modes, some of which are shown in the following list:</span></span>  
  
- <xref:System.Drawing.Drawing2D.InterpolationMode.NearestNeighbor>  
  
- <xref:System.Drawing.Drawing2D.InterpolationMode.Bilinear>  
  
- <xref:System.Drawing.Drawing2D.InterpolationMode.HighQualityBilinear>  
  
- <xref:System.Drawing.Drawing2D.InterpolationMode.Bicubic>  
  
- <xref:System.Drawing.Drawing2D.InterpolationMode.HighQualityBicubic>  
  
 <span data-ttu-id="5d960-105">Pour étirer une image, chaque pixel de l’image d’origine doit être mappé à un groupe de pixels dans l’image plus grande.</span><span class="sxs-lookup"><span data-stu-id="5d960-105">To stretch an image, each pixel in the original image must be mapped to a group of pixels in the larger image.</span></span> <span data-ttu-id="5d960-106">Pour réduire une image, des groupes de pixels dans l’image d’origine doivent être mappés en pixels individuels dans l’image plus petite.</span><span class="sxs-lookup"><span data-stu-id="5d960-106">To shrink an image, groups of pixels in the original image must be mapped to single pixels in the smaller image.</span></span> <span data-ttu-id="5d960-107">L’efficacité des algorithmes qui effectuent ces mappages détermine la qualité d’une image à l’échelle.</span><span class="sxs-lookup"><span data-stu-id="5d960-107">The effectiveness of the algorithms that perform these mappings determines the quality of a scaled image.</span></span> <span data-ttu-id="5d960-108">Les algorithmes qui produisent des images à l’échelle de qualité supérieure ont tendance à nécessiter plus de temps de traitement.</span><span class="sxs-lookup"><span data-stu-id="5d960-108">Algorithms that produce higher-quality scaled images tend to require more processing time.</span></span> <span data-ttu-id="5d960-109">Dans la liste précédente, <xref:System.Drawing.Drawing2D.InterpolationMode.NearestNeighbor> est le mode de qualité et <xref:System.Drawing.Drawing2D.InterpolationMode.HighQualityBicubic> est le mode de qualité optimale.</span><span class="sxs-lookup"><span data-stu-id="5d960-109">In the preceding list, <xref:System.Drawing.Drawing2D.InterpolationMode.NearestNeighbor> is the lowest-quality mode and <xref:System.Drawing.Drawing2D.InterpolationMode.HighQualityBicubic> is the highest-quality mode.</span></span>  
  
 <span data-ttu-id="5d960-110">Pour définir le mode d’interpolation, assignez un des membres de la <xref:System.Drawing.Drawing2D.InterpolationMode> énumération à la <xref:System.Drawing.Graphics.InterpolationMode%2A> propriété d’un <xref:System.Drawing.Graphics> objet.</span><span class="sxs-lookup"><span data-stu-id="5d960-110">To set the interpolation mode, assign one of the members of the <xref:System.Drawing.Drawing2D.InterpolationMode> enumeration to the <xref:System.Drawing.Graphics.InterpolationMode%2A> property of a <xref:System.Drawing.Graphics> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5d960-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="5d960-111">Example</span></span>  
 <span data-ttu-id="5d960-112">L’exemple suivant dessine une image, puis réduit l’image avec trois modes d’interpolation différent.</span><span class="sxs-lookup"><span data-stu-id="5d960-112">The following example draws an image and then shrinks the image with three different interpolation modes.</span></span>  
  
 <span data-ttu-id="5d960-113">L’illustration suivante montre l’image d’origine et les trois images plus petites.</span><span class="sxs-lookup"><span data-stu-id="5d960-113">The following illustration shows the original image and the three smaller images.</span></span>  
  
 ![Capture d’écran montrant une image avec paramètres d’interpolation variés.](./media/how-to-use-interpolation-mode-to-control-image-quality-during-scaling/varied-interpolation-settings.png)  
  
 [!code-csharp[System.Drawing.WorkingWithImages#81](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#81)]
 [!code-vb[System.Drawing.WorkingWithImages#81](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#81)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="5d960-115">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="5d960-115">Compiling the Code</span></span>  
 <span data-ttu-id="5d960-116">L’exemple précédent est conçu pour une utilisation avec Windows Forms et nécessite <xref:System.Windows.Forms.PaintEventArgs> `e`, qui est un paramètre de la <xref:System.Windows.Forms.Control.Paint> Gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="5d960-116">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d960-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5d960-117">See also</span></span>

- [<span data-ttu-id="5d960-118">Images, bitmaps et métafichiers</span><span class="sxs-lookup"><span data-stu-id="5d960-118">Images, Bitmaps, and Metafiles</span></span>](images-bitmaps-and-metafiles.md)
- [<span data-ttu-id="5d960-119">Utilisation des images, bitmaps, icônes et métafichiers</span><span class="sxs-lookup"><span data-stu-id="5d960-119">Working with Images, Bitmaps, Icons, and Metafiles</span></span>](working-with-images-bitmaps-icons-and-metafiles.md)
