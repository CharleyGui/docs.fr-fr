---
title: 'Comment : peindre une zone avec une image'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- images [WPF], painting with
- painting [WPF], with images
- brushes [WPF], painting with images
ms.assetid: 3432c533-1fc7-492d-94ee-0b13d60125ae
ms.openlocfilehash: 92969778c04c6ac634a2964c402d6c3439b96b49
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186051"
---
# <a name="how-to-paint-an-area-with-an-image"></a><span data-ttu-id="c56e0-102">Comment : peindre une zone avec une image</span><span class="sxs-lookup"><span data-stu-id="c56e0-102">How to: Paint an Area with an Image</span></span>
<span data-ttu-id="c56e0-103">Cet exemple montre comment <xref:System.Windows.Media.ImageBrush> utiliser la classe pour peindre une zone avec une image.</span><span class="sxs-lookup"><span data-stu-id="c56e0-103">This example shows how to use the <xref:System.Windows.Media.ImageBrush> class to paint an area with an image.</span></span> <span data-ttu-id="c56e0-104">Une <xref:System.Windows.Media.ImageBrush> image unique, qui est <xref:System.Windows.Media.ImageBrush.ImageSource%2A> spécifiée par sa propriété.</span><span class="sxs-lookup"><span data-stu-id="c56e0-104">An <xref:System.Windows.Media.ImageBrush> displays a single image, which is specified by its <xref:System.Windows.Media.ImageBrush.ImageSource%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c56e0-105"> Exemple</span><span class="sxs-lookup"><span data-stu-id="c56e0-105">Example</span></span>  
 <span data-ttu-id="c56e0-106">L’exemple suivant <xref:System.Windows.Controls.Control.Background%2A> peint le bouton <xref:System.Windows.Media.ImageBrush>en utilisant un .</span><span class="sxs-lookup"><span data-stu-id="c56e0-106">The following example paints the <xref:System.Windows.Controls.Control.Background%2A> of a button by using an <xref:System.Windows.Media.ImageBrush>.</span></span>  
  
 [!code-csharp[UsingImageBrush_snip#ImageBrushExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/PaintingWithImagesExample.cs#imagebrushexamplewholepage)]  
  
 <span data-ttu-id="c56e0-107">Par défaut, <xref:System.Windows.Media.ImageBrush> un étend son image pour remplir complètement la zone que vous peignez.</span><span class="sxs-lookup"><span data-stu-id="c56e0-107">By default, an <xref:System.Windows.Media.ImageBrush> stretches its image to completely fill the area that you are painting.</span></span> <span data-ttu-id="c56e0-108">Dans l’exemple précédent, l’image est étirée pour remplir le bouton, ce qui peut éventuellement déformer l’image.</span><span class="sxs-lookup"><span data-stu-id="c56e0-108">In the preceding example, the image is stretched to fill the button, possibly distorting the image.</span></span> <span data-ttu-id="c56e0-109">Vous pouvez contrôler ce <xref:System.Windows.Media.TileBrush.Stretch%2A> comportement <xref:System.Windows.Media.TileBrush> en <xref:System.Windows.Media.Stretch.Uniform> <xref:System.Windows.Media.Stretch.UniformToFill>définissant la propriété de ou , ce qui provoque le pinceau pour préserver le rapport d’aspect de l’image.</span><span class="sxs-lookup"><span data-stu-id="c56e0-109">You can control this behavior by setting the <xref:System.Windows.Media.TileBrush.Stretch%2A> property of <xref:System.Windows.Media.TileBrush> to <xref:System.Windows.Media.Stretch.Uniform> or <xref:System.Windows.Media.Stretch.UniformToFill>, which causes the brush to preserve the aspect ratio of the image.</span></span>  
  
 <span data-ttu-id="c56e0-110">Si vous <xref:System.Windows.Media.TileBrush.Viewport%2A> définissez le et <xref:System.Windows.Media.TileBrush.TileMode%2A> les propriétés d’un <xref:System.Windows.Media.ImageBrush>, vous pouvez créer un modèle répétitif.</span><span class="sxs-lookup"><span data-stu-id="c56e0-110">If you set the <xref:System.Windows.Media.TileBrush.Viewport%2A> and <xref:System.Windows.Media.TileBrush.TileMode%2A> properties of an <xref:System.Windows.Media.ImageBrush>, you can create a repeating pattern.</span></span> <span data-ttu-id="c56e0-111">L’exemple suivant peint un bouton en utilisant un modèle créé à partir d’une image.</span><span class="sxs-lookup"><span data-stu-id="c56e0-111">The following example paints a button by using a pattern that is created from an image.</span></span>  
  
 [!code-csharp[UsingImageBrush_snip#TiledImageBrushExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/TiledImageBrushExample.cs#tiledimagebrushexamplewholepage)]
 [!code-vb[UsingImageBrush_snip#TiledImageBrushExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/UsingImageBrush_snip/VisualBasic/TiledImageBrushExample.vb#tiledimagebrushexamplewholepage)]  
  
 <span data-ttu-id="c56e0-112">Pour plus d’informations sur la <xref:System.Windows.Media.ImageBrush> classe, voir Painting with [Images, Drawings, and Visuals](painting-with-images-drawings-and-visuals.md).</span><span class="sxs-lookup"><span data-stu-id="c56e0-112">For more information about the <xref:System.Windows.Media.ImageBrush> class, see [Painting with Images, Drawings, and Visuals](painting-with-images-drawings-and-visuals.md).</span></span>  
  
 <span data-ttu-id="c56e0-113">Cet exemple de code fait partie d’un exemple plus large qui est fourni pour la <xref:System.Windows.Media.ImageBrush> classe.</span><span class="sxs-lookup"><span data-stu-id="c56e0-113">This code example is part of a larger example that is provided for the <xref:System.Windows.Media.ImageBrush> class.</span></span> <span data-ttu-id="c56e0-114">Pour l’échantillon complet, voir [ImageBrush Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ImageBrush).</span><span class="sxs-lookup"><span data-stu-id="c56e0-114">For the complete sample, see [ImageBrush Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ImageBrush).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c56e0-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c56e0-115">See also</span></span>

- [<span data-ttu-id="c56e0-116">Peinture avec des images, des dessins et des objets visuels</span><span class="sxs-lookup"><span data-stu-id="c56e0-116">Painting with Images, Drawings, and Visuals</span></span>](painting-with-images-drawings-and-visuals.md)
