---
title: 'Procédure : Incliner un élément'
ms.date: 03/30/2017
helpviewer_keywords:
- skewing elements [WPF]
- graphics [WPF], skewing elements
- classes [WPF], SkewTransform
ms.assetid: 56b65f2f-dc6e-4238-923f-ca44ec53c52f
ms.openlocfilehash: cf770a284238826852e788e27f3b3f329ed0269f
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67664086"
---
# <a name="how-to-skew-an-element"></a><span data-ttu-id="789f5-102">Procédure : Incliner un élément</span><span class="sxs-lookup"><span data-stu-id="789f5-102">How to: Skew an Element</span></span>
<span data-ttu-id="789f5-103">Cet exemple montre comment utiliser un <xref:System.Windows.Media.SkewTransform> pour incliner un élément.</span><span class="sxs-lookup"><span data-stu-id="789f5-103">This example shows how to use a <xref:System.Windows.Media.SkewTransform> to skew an element.</span></span> <span data-ttu-id="789f5-104">Une inclinaison est une transformation qui étire l’espace de coordonnées de façon non uniforme.</span><span class="sxs-lookup"><span data-stu-id="789f5-104">A skew, which is also known as a shear, is a transformation that stretches the coordinate space in a non-uniform manner.</span></span> <span data-ttu-id="789f5-105">Une utilisation typique d’un <xref:System.Windows.Media.SkewTransform> est la simulation de profondeur 3D dans les objets 2D.</span><span class="sxs-lookup"><span data-stu-id="789f5-105">One typical use of a <xref:System.Windows.Media.SkewTransform> is for simulating 3-D depth in 2-D objects.</span></span>  
  
 <span data-ttu-id="789f5-106">Utilisez le <xref:System.Windows.Media.SkewTransform.CenterX%2A> et <xref:System.Windows.Media.SkewTransform.CenterY%2A> propriétés pour spécifier le centre du point de la <xref:System.Windows.Media.SkewTransform>.</span><span class="sxs-lookup"><span data-stu-id="789f5-106">Use the <xref:System.Windows.Media.SkewTransform.CenterX%2A> and <xref:System.Windows.Media.SkewTransform.CenterY%2A> properties to specify the center point of the <xref:System.Windows.Media.SkewTransform>.</span></span>  
  
 <span data-ttu-id="789f5-107">Utilisez le <xref:System.Windows.Media.SkewTransform.AngleX%2A> et <xref:System.Windows.Media.SkewTransform.AngleY%2A> propriétés pour spécifier l’angle d’inclinaison de l’axe des abscisses et l’axe des y et pour incliner le système de coordonnées actuel le long de ces axes.</span><span class="sxs-lookup"><span data-stu-id="789f5-107">Use the <xref:System.Windows.Media.SkewTransform.AngleX%2A> and <xref:System.Windows.Media.SkewTransform.AngleY%2A> properties to specify the skew angle of the x-axis and y-axis, and to skew the current coordinate system along these axes.</span></span>  
  
 <span data-ttu-id="789f5-108">Pour prévoir l’effet d’une transformation d’inclinaison, tenez compte des points <xref:System.Windows.Media.SkewTransform.AngleX%2A> incline les valeurs de l’axe x par rapport au système de coordonnées d’origine.</span><span class="sxs-lookup"><span data-stu-id="789f5-108">To predict the effect of a skew transformation, consider that <xref:System.Windows.Media.SkewTransform.AngleX%2A> skews x-axis values relative to the original coordinate system.</span></span> <span data-ttu-id="789f5-109">Par conséquent, pour un <xref:System.Windows.Media.SkewTransform.AngleX%2A> de 30, l’axe y pivote de 30 degrés via l’origine et incline les valeurs x-de 30 degrés à partir de cette origine.</span><span class="sxs-lookup"><span data-stu-id="789f5-109">Therefore, for an <xref:System.Windows.Media.SkewTransform.AngleX%2A> of 30, the y-axis rotates 30 degrees through the origin and skews the values in x- by 30 degrees from that origin.</span></span> <span data-ttu-id="789f5-110">De même, un <xref:System.Windows.Media.SkewTransform.AngleY%2A> de 30 incline les valeurs y de la forme de 30 degrés à partir de l’origine.</span><span class="sxs-lookup"><span data-stu-id="789f5-110">Likewise, an <xref:System.Windows.Media.SkewTransform.AngleY%2A> of 30 skews the y- values of the shape by 30 degrees from the origin.</span></span> <span data-ttu-id="789f5-111">Notez que l’effet produit est différent de celui obtenu lorsque l’on déplace le système de coordonnées de 30 degrés sur l’axe des x ou l’axe des y.</span><span class="sxs-lookup"><span data-stu-id="789f5-111">Note that this is not the same effect as translating (moving) the coordinate system by 30 degrees in x- or y-.</span></span>  
  
 <span data-ttu-id="789f5-112">L’exemple suivant applique une inclinaison horizontale de 45 degrés à un <xref:System.Windows.Shapes.Rectangle> à partir d’un point central de (0,0).</span><span class="sxs-lookup"><span data-stu-id="789f5-112">The following example applies a horizontal skew of 45 degrees to a <xref:System.Windows.Shapes.Rectangle> from a center point of (0,0).</span></span>  
  
## <a name="example"></a><span data-ttu-id="789f5-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="789f5-113">Example</span></span>  
 [!code-xaml[transformsSample#41](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#41)]  
  
 <span data-ttu-id="789f5-114">L’exemple suivant applique une inclinaison horizontale de 45 degrés à un <xref:System.Windows.Shapes.Rectangle> à partir d’un point central de (25,25).</span><span class="sxs-lookup"><span data-stu-id="789f5-114">The following example applies a horizontal skew of 45 degrees to a <xref:System.Windows.Shapes.Rectangle> from a center point of (25,25).</span></span>  
  
 [!code-xaml[transformsSample#42](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#42)]  
  
 <span data-ttu-id="789f5-115">L’exemple suivant applique une inclinaison verticale de 45 degrés à un <xref:System.Windows.Shapes.Rectangle> à partir d’un point central de (25,25).</span><span class="sxs-lookup"><span data-stu-id="789f5-115">The following example applies a vertical skew of 45 degrees to a <xref:System.Windows.Shapes.Rectangle> from a center point of (25,25).</span></span>  
  
 [!code-xaml[transformsSample#43](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#43)]  
  
 <span data-ttu-id="789f5-116">L’illustration suivante montre les différentes inclinaisons utilisées dans cet exemple.</span><span class="sxs-lookup"><span data-stu-id="789f5-116">The following illustration shows the different skews that are used in this example.</span></span>  
  
 <span data-ttu-id="789f5-117">![SkewTransform examples](./media/img-wcpsdk-graphicsmm-skewtransformexample.gif "img_wcpsdk_graphicsmm_skewtransformexample")</span><span class="sxs-lookup"><span data-stu-id="789f5-117">![SkewTransform examples](./media/img-wcpsdk-graphicsmm-skewtransformexample.gif "img_wcpsdk_graphicsmm_skewtransformexample")</span></span>  
<span data-ttu-id="789f5-118">Les trois exemples SkewTransform illustrés</span><span class="sxs-lookup"><span data-stu-id="789f5-118">The three SkewTransform examples illustrated</span></span>  
  
 <span data-ttu-id="789f5-119">Pour voir l’exemple complet, consultez la page [2-D Transforms Sample](https://go.microsoft.com/fwlink/?LinkID=158252) (Exemple de transformations 2D).</span><span class="sxs-lookup"><span data-stu-id="789f5-119">For the complete sample, see [2-D Transforms Sample](https://go.microsoft.com/fwlink/?LinkID=158252).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="789f5-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="789f5-120">See also</span></span>

- <xref:System.Windows.Media.Transform>
- <xref:System.Windows.Media.SkewTransform>
- [<span data-ttu-id="789f5-121">Vue d’ensemble des transformations</span><span class="sxs-lookup"><span data-stu-id="789f5-121">Transforms Overview</span></span>](transforms-overview.md)
- [<span data-ttu-id="789f5-122">Rubriques de guide pratique</span><span class="sxs-lookup"><span data-stu-id="789f5-122">How-to Topics</span></span>](transformations-how-to-topics.md)
