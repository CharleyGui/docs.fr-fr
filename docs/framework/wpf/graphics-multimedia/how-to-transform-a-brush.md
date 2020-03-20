---
title: 'Comment : transformer un pinceau'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- brushes [WPF], rotating contents
- brushes [WPF], Transform property
- rotating contents of brushes [WPF]
ms.assetid: ebada2f9-f01f-4863-9ea2-c2e4e51610f1
ms.openlocfilehash: b4484e2fc1ae3e969b02b1d8f3ae4ab2a035558e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187336"
---
# <a name="how-to-transform-a-brush"></a><span data-ttu-id="bc206-102">Comment : transformer un pinceau</span><span class="sxs-lookup"><span data-stu-id="bc206-102">How to: Transform a Brush</span></span>
<span data-ttu-id="bc206-103">Cet exemple montre <xref:System.Windows.Media.Brush> comment transformer les objets <xref:System.Windows.Media.Brush.RelativeTransform%2A> en <xref:System.Windows.Media.Brush.Transform%2A>utilisant leurs deux propriétés de transformation : et .</span><span class="sxs-lookup"><span data-stu-id="bc206-103">This example shows how to transform <xref:System.Windows.Media.Brush> objects by using their two transformation properties: <xref:System.Windows.Media.Brush.RelativeTransform%2A> and <xref:System.Windows.Media.Brush.Transform%2A>.</span></span>  
  
 <span data-ttu-id="bc206-104">Les exemples <xref:System.Windows.Media.RotateTransform> suivants utilisent un <xref:System.Windows.Media.ImageBrush> pour faire pivoter le contenu d’un de 45 degrés.</span><span class="sxs-lookup"><span data-stu-id="bc206-104">The following examples use a <xref:System.Windows.Media.RotateTransform> to rotate the content of an <xref:System.Windows.Media.ImageBrush> by 45 degrees.</span></span>  
  
 <span data-ttu-id="bc206-105">L’illustration suivante <xref:System.Windows.Media.ImageBrush> montre <xref:System.Windows.Media.RotateTransform>l’sans a <xref:System.Windows.Media.Brush.RelativeTransform%2A> , avec <xref:System.Windows.Media.RotateTransform> l’appliqué <xref:System.Windows.Media.Brush.Transform%2A> <xref:System.Windows.Media.RotateTransform> à la propriété, et avec l’appliqué à la propriété.</span><span class="sxs-lookup"><span data-stu-id="bc206-105">The following illustration shows the <xref:System.Windows.Media.ImageBrush> without a <xref:System.Windows.Media.RotateTransform>, with the <xref:System.Windows.Media.RotateTransform> applied to the <xref:System.Windows.Media.Brush.RelativeTransform%2A> property, and with the <xref:System.Windows.Media.RotateTransform> applied to the <xref:System.Windows.Media.Brush.Transform%2A> property.</span></span>  
  
 <span data-ttu-id="bc206-106">![Paramètres de Brush RelativeTransform et Transform](./media/wcpsdk-graphicsmm-transformandrelativetransform.png "wcpsdk_graphicsmm_transformandrelativetransform")</span><span class="sxs-lookup"><span data-stu-id="bc206-106">![Brush RelativeTransform and Transform settings](./media/wcpsdk-graphicsmm-transformandrelativetransform.png "wcpsdk_graphicsmm_transformandrelativetransform")</span></span>  
  
## <a name="example"></a><span data-ttu-id="bc206-107"> Exemple</span><span class="sxs-lookup"><span data-stu-id="bc206-107">Example</span></span>  
 <span data-ttu-id="bc206-108">Le premier exemple <xref:System.Windows.Media.RotateTransform> s’applique à la <xref:System.Windows.Media.Brush.RelativeTransform%2A> propriété d’un <xref:System.Windows.Media.ImageBrush>.</span><span class="sxs-lookup"><span data-stu-id="bc206-108">The first example applies a <xref:System.Windows.Media.RotateTransform> to the <xref:System.Windows.Media.Brush.RelativeTransform%2A> property of an <xref:System.Windows.Media.ImageBrush>.</span></span> <span data-ttu-id="bc206-109">Les <xref:System.Windows.Media.RotateTransform.CenterX%2A> <xref:System.Windows.Media.RotateTransform.CenterY%2A> propriétés <xref:System.Windows.Media.RotateTransform> et les propriétés d’un objet sont toutes deux réglées à 0,5, qui est la coordination relative du point central de ce contenu.</span><span class="sxs-lookup"><span data-stu-id="bc206-109">The <xref:System.Windows.Media.RotateTransform.CenterX%2A> and <xref:System.Windows.Media.RotateTransform.CenterY%2A> properties of a <xref:System.Windows.Media.RotateTransform> object are both set to 0.5, which is the relative coordinate of the center point of this content.</span></span> <span data-ttu-id="bc206-110">En conséquence, <xref:System.Windows.Media.ImageBrush> le contenu tourne autour de son centre.</span><span class="sxs-lookup"><span data-stu-id="bc206-110">As a result, the <xref:System.Windows.Media.ImageBrush> content rotates about its center.</span></span>  
  
 [!code-csharp[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTransformExample.cs#imagebrushrelativetransformexample)]
 [!code-vb[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtransformexample.vb#imagebrushrelativetransformexample)]
 [!code-xaml[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTransformExample.xaml#imagebrushrelativetransformexample)]  
  
 <span data-ttu-id="bc206-111">Le deuxième exemple <xref:System.Windows.Media.RotateTransform> s’applique également à un <xref:System.Windows.Media.ImageBrush>; cependant, cet exemple <xref:System.Windows.Media.Brush.Transform%2A> utilise la <xref:System.Windows.Media.Brush.RelativeTransform%2A> propriété au lieu de la propriété.</span><span class="sxs-lookup"><span data-stu-id="bc206-111">The second example also applies a <xref:System.Windows.Media.RotateTransform> to an <xref:System.Windows.Media.ImageBrush>; however, this example uses the <xref:System.Windows.Media.Brush.Transform%2A> property instead of the <xref:System.Windows.Media.Brush.RelativeTransform%2A> property.</span></span>  
  
 <span data-ttu-id="bc206-112">Pour faire pivoter le pinceau sur <xref:System.Windows.Media.RotateTransform.CenterX%2A> <xref:System.Windows.Media.RotateTransform.CenterY%2A> son centre, l’exemple définit les propriétés et les propriétés de l’objet <xref:System.Windows.Media.RotateTransform> à des coordonnées absolues.</span><span class="sxs-lookup"><span data-stu-id="bc206-112">To rotate the brush about its center, the example sets the <xref:System.Windows.Media.RotateTransform.CenterX%2A> and <xref:System.Windows.Media.RotateTransform.CenterY%2A> properties of the <xref:System.Windows.Media.RotateTransform> object to absolute coordinates.</span></span> <span data-ttu-id="bc206-113">Étant donné que le pinceau peint un rectangle de 175 par 90 pixels, le point central du rectangle est (87,5, 45).</span><span class="sxs-lookup"><span data-stu-id="bc206-113">Because the brush paints a rectangle that is 175 by 90 pixels, the center point of the rectangle is (87.5, 45).</span></span>  
  
 [!code-csharp[BrushesIntroduction_snip#ImageBrushTransformExample](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTransformExample.cs#imagebrushtransformexample)]
 [!code-vb[BrushesIntroduction_snip#ImageBrushTransformExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtransformexample.vb#imagebrushtransformexample)]
 [!code-xaml[BrushesIntroduction_snip#ImageBrushTransformExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTransformExample.xaml#imagebrushtransformexample)]  
  
 <span data-ttu-id="bc206-114">Pour une description <xref:System.Windows.Media.Brush.RelativeTransform%2A> du <xref:System.Windows.Media.Brush.Transform%2A> fonctionnement et des propriétés, consultez l’aperçu de la [transformation du pinceau.](brush-transformation-overview.md)</span><span class="sxs-lookup"><span data-stu-id="bc206-114">For a description of how the <xref:System.Windows.Media.Brush.RelativeTransform%2A> and <xref:System.Windows.Media.Brush.Transform%2A> properties work, see the [Brush Transformation Overview](brush-transformation-overview.md).</span></span>  
  
 <span data-ttu-id="bc206-115">Pour l’exemple complet, consultez [Exemples de pinceaux](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes).</span><span class="sxs-lookup"><span data-stu-id="bc206-115">For the complete sample, see [Brushes Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes).</span></span> <span data-ttu-id="bc206-116">Pour plus d’informations sur les pinceaux, consultez [Vue d’ensemble de la peinture avec des couleurs unies ou des dégradés](painting-with-solid-colors-and-gradients-overview.md).</span><span class="sxs-lookup"><span data-stu-id="bc206-116">For more information about brushes, see [Painting with Solid Colors and Gradients Overview](painting-with-solid-colors-and-gradients-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc206-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bc206-117">See also</span></span>

- [<span data-ttu-id="bc206-118">Vue d'ensemble des transformations du pinceau</span><span class="sxs-lookup"><span data-stu-id="bc206-118">Brush Transformation Overview</span></span>](brush-transformation-overview.md)
- [<span data-ttu-id="bc206-119">Vue d'ensemble de la peinture avec des couleurs unies ou des dégradés</span><span class="sxs-lookup"><span data-stu-id="bc206-119">Painting with Solid Colors and Gradients Overview</span></span>](painting-with-solid-colors-and-gradients-overview.md)
- [<span data-ttu-id="bc206-120">Vue d'ensemble des transformations</span><span class="sxs-lookup"><span data-stu-id="bc206-120">Transforms Overview</span></span>](transforms-overview.md)
