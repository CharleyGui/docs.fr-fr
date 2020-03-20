---
title: 'Comment : incliner un élément'
ms.date: 03/30/2017
helpviewer_keywords:
- skewing elements [WPF]
- graphics [WPF], skewing elements
- classes [WPF], SkewTransform
ms.assetid: 56b65f2f-dc6e-4238-923f-ca44ec53c52f
ms.openlocfilehash: 370ac28b07427345b52822133b5414b45d4462eb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187660"
---
# <a name="how-to-skew-an-element"></a><span data-ttu-id="37656-102">Comment : incliner un élément</span><span class="sxs-lookup"><span data-stu-id="37656-102">How to: Skew an Element</span></span>
<span data-ttu-id="37656-103">Cet exemple montre comment <xref:System.Windows.Media.SkewTransform> utiliser un élément pour biaiser.</span><span class="sxs-lookup"><span data-stu-id="37656-103">This example shows how to use a <xref:System.Windows.Media.SkewTransform> to skew an element.</span></span> <span data-ttu-id="37656-104">Une inclinaison est une transformation qui étire l’espace de coordonnées de façon non uniforme.</span><span class="sxs-lookup"><span data-stu-id="37656-104">A skew, which is also known as a shear, is a transformation that stretches the coordinate space in a non-uniform manner.</span></span> <span data-ttu-id="37656-105">Une utilisation typique <xref:System.Windows.Media.SkewTransform> d’un est pour simuler la profondeur 3D dans des objets 2D.</span><span class="sxs-lookup"><span data-stu-id="37656-105">One typical use of a <xref:System.Windows.Media.SkewTransform> is for simulating 3-D depth in 2-D objects.</span></span>  
  
 <span data-ttu-id="37656-106">Utilisez <xref:System.Windows.Media.SkewTransform.CenterX%2A> le <xref:System.Windows.Media.SkewTransform.CenterY%2A> et les propriétés <xref:System.Windows.Media.SkewTransform>pour spécifier le point central de la .</span><span class="sxs-lookup"><span data-stu-id="37656-106">Use the <xref:System.Windows.Media.SkewTransform.CenterX%2A> and <xref:System.Windows.Media.SkewTransform.CenterY%2A> properties to specify the center point of the <xref:System.Windows.Media.SkewTransform>.</span></span>  
  
 <span data-ttu-id="37656-107">Utilisez <xref:System.Windows.Media.SkewTransform.AngleX%2A> l’angle et <xref:System.Windows.Media.SkewTransform.AngleY%2A> les propriétés pour spécifier l’angle de biais de l’axe x et de l’axe y, et pour fausser le système de coordonnées actuel le long de ces axes.</span><span class="sxs-lookup"><span data-stu-id="37656-107">Use the <xref:System.Windows.Media.SkewTransform.AngleX%2A> and <xref:System.Windows.Media.SkewTransform.AngleY%2A> properties to specify the skew angle of the x-axis and y-axis, and to skew the current coordinate system along these axes.</span></span>  
  
 <span data-ttu-id="37656-108">Pour prédire l’effet d’une <xref:System.Windows.Media.SkewTransform.AngleX%2A> transformation biaisée, considérez que les valeurs x-axe biaisées par rapport au système de coordonnées d’origine.</span><span class="sxs-lookup"><span data-stu-id="37656-108">To predict the effect of a skew transformation, consider that <xref:System.Windows.Media.SkewTransform.AngleX%2A> skews x-axis values relative to the original coordinate system.</span></span> <span data-ttu-id="37656-109">Par conséquent, <xref:System.Windows.Media.SkewTransform.AngleX%2A> pour un de 30, l’axe y tourne de 30 degrés à travers l’origine et fausse les valeurs en x- par 30 degrés de cette origine.</span><span class="sxs-lookup"><span data-stu-id="37656-109">Therefore, for an <xref:System.Windows.Media.SkewTransform.AngleX%2A> of 30, the y-axis rotates 30 degrees through the origin and skews the values in x- by 30 degrees from that origin.</span></span> <span data-ttu-id="37656-110">De même, un <xref:System.Windows.Media.SkewTransform.AngleY%2A> de 30 biaise les valeurs y de la forme de 30 degrés de l’origine.</span><span class="sxs-lookup"><span data-stu-id="37656-110">Likewise, an <xref:System.Windows.Media.SkewTransform.AngleY%2A> of 30 skews the y- values of the shape by 30 degrees from the origin.</span></span> <span data-ttu-id="37656-111">Notez que l’effet produit est différent de celui obtenu lorsque l’on déplace le système de coordonnées de 30 degrés sur l’axe des x ou l’axe des y.</span><span class="sxs-lookup"><span data-stu-id="37656-111">Note that this is not the same effect as translating (moving) the coordinate system by 30 degrees in x- or y-.</span></span>  
  
 <span data-ttu-id="37656-112">L’exemple suivant applique un biais horizontal <xref:System.Windows.Shapes.Rectangle> de 45 degrés à un point central de (0,0).</span><span class="sxs-lookup"><span data-stu-id="37656-112">The following example applies a horizontal skew of 45 degrees to a <xref:System.Windows.Shapes.Rectangle> from a center point of (0,0).</span></span>  
  
## <a name="example"></a><span data-ttu-id="37656-113"> Exemple</span><span class="sxs-lookup"><span data-stu-id="37656-113">Example</span></span>  
 [!code-xaml[transformsSample#41](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#41)]  
  
 <span data-ttu-id="37656-114">L’exemple suivant applique un biais horizontal <xref:System.Windows.Shapes.Rectangle> de 45 degrés à un point central de (25,25).</span><span class="sxs-lookup"><span data-stu-id="37656-114">The following example applies a horizontal skew of 45 degrees to a <xref:System.Windows.Shapes.Rectangle> from a center point of (25,25).</span></span>  
  
 [!code-xaml[transformsSample#42](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#42)]  
  
 <span data-ttu-id="37656-115">L’exemple suivant applique un biais vertical <xref:System.Windows.Shapes.Rectangle> de 45 degrés à un point central de (25,25).</span><span class="sxs-lookup"><span data-stu-id="37656-115">The following example applies a vertical skew of 45 degrees to a <xref:System.Windows.Shapes.Rectangle> from a center point of (25,25).</span></span>  
  
 [!code-xaml[transformsSample#43](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#43)]  
  
 <span data-ttu-id="37656-116">L’illustration suivante montre les différentes inclinaisons utilisées dans cet exemple.</span><span class="sxs-lookup"><span data-stu-id="37656-116">The following illustration shows the different skews that are used in this example.</span></span>  
  
 <span data-ttu-id="37656-117">![Exemples de SkewTransform](./media/img-wcpsdk-graphicsmm-skewtransformexample.gif "img_wcpsdk_graphicsmm_skewtransformexample")</span><span class="sxs-lookup"><span data-stu-id="37656-117">![SkewTransform examples](./media/img-wcpsdk-graphicsmm-skewtransformexample.gif "img_wcpsdk_graphicsmm_skewtransformexample")</span></span>  
<span data-ttu-id="37656-118">Les trois exemples SkewTransform illustrés</span><span class="sxs-lookup"><span data-stu-id="37656-118">The three SkewTransform examples illustrated</span></span>  
  
 <span data-ttu-id="37656-119">Pour voir l’exemple complet, consultez la page [2-D Transforms Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms) (Exemple de transformations 2D).</span><span class="sxs-lookup"><span data-stu-id="37656-119">For the complete sample, see [2-D Transforms Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37656-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="37656-120">See also</span></span>

- <xref:System.Windows.Media.Transform>
- <xref:System.Windows.Media.SkewTransform>
- [<span data-ttu-id="37656-121">Vue d'ensemble des transformations</span><span class="sxs-lookup"><span data-stu-id="37656-121">Transforms Overview</span></span>](transforms-overview.md)
- [<span data-ttu-id="37656-122">Sujets comment se passer</span><span class="sxs-lookup"><span data-stu-id="37656-122">How-to Topics</span></span>](transformations-how-to-topics.md)
