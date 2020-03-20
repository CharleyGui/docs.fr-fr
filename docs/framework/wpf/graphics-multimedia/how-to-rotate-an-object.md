---
title: 'Comment : faire pivoter un objet'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [WPF], rotating objects [WPF]
- rotating objects [WPF]
ms.assetid: ee3466cd-e66f-4e8f-8a5a-71d77bc1e390
ms.openlocfilehash: 02d8144c28b7a4e54fb86fea5abb694cf7af34af
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185966"
---
# <a name="how-to-rotate-an-object"></a><span data-ttu-id="e423d-102">Comment : faire pivoter un objet</span><span class="sxs-lookup"><span data-stu-id="e423d-102">How to: Rotate an Object</span></span>
<span data-ttu-id="e423d-103">Cet exemple montre comment faire pivoter un objet.</span><span class="sxs-lookup"><span data-stu-id="e423d-103">This example shows how to rotate an object.</span></span> <span data-ttu-id="e423d-104">L’exemple crée <xref:System.Windows.Media.RotateTransform> d’abord un, puis spécifie son <xref:System.Windows.Media.RotateTransform.Angle%2A> en degrés.</span><span class="sxs-lookup"><span data-stu-id="e423d-104">The example first creates a <xref:System.Windows.Media.RotateTransform> and then specifies its <xref:System.Windows.Media.RotateTransform.Angle%2A> in degrees.</span></span>  
  
 <span data-ttu-id="e423d-105">L’exemple suivant <xref:System.Windows.Shapes.Polyline> fait pivoter un objet de 45 degrés sur son coin supérieur gauche.</span><span class="sxs-lookup"><span data-stu-id="e423d-105">The following example rotates a <xref:System.Windows.Shapes.Polyline> object 45 degrees about its upper-left corner.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e423d-106"> Exemple</span><span class="sxs-lookup"><span data-stu-id="e423d-106">Example</span></span>  
 [!code-xaml[Transforms_snip#RotatePolylineAboutTopLeft](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/RotateTransformExample.xaml#rotatepolylineabouttopleft)]  
  
 [!code-csharp[Transforms_Procedural_snip#RotatePolylineAboutTopLeft](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_Procedural_snip/CSharp/RotateTransformExample.cs#rotatepolylineabouttopleft)]
 [!code-vb[Transforms_Procedural_snip#RotatePolylineAboutTopLeft](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Transforms_Procedural_snip/VisualBasic/RotateTransformExample.vb#rotatepolylineabouttopleft)]  
  
 <span data-ttu-id="e423d-107">Les <xref:System.Windows.Media.RotateTransform.CenterX%2A> <xref:System.Windows.Media.RotateTransform.CenterY%2A> propriétés <xref:System.Windows.Media.RotateTransform> et les propriétés du point de rotation de l’objet.</span><span class="sxs-lookup"><span data-stu-id="e423d-107">The <xref:System.Windows.Media.RotateTransform.CenterX%2A> and <xref:System.Windows.Media.RotateTransform.CenterY%2A> properties of the <xref:System.Windows.Media.RotateTransform> specify the point about which the object is rotated.</span></span> <span data-ttu-id="e423d-108">Ce point central est exprimé dans l’espace de coordonnées de l’élément transformé.</span><span class="sxs-lookup"><span data-stu-id="e423d-108">This center point is expressed in the coordinate space of the element that is transformed.</span></span> <span data-ttu-id="e423d-109">Par défaut, la rotation est appliquée à (0,0), qui correspond à l’angle supérieur gauche de l’objet à transformer.</span><span class="sxs-lookup"><span data-stu-id="e423d-109">By default, the rotation is applied to (0,0), which is the upper-left corner of the object to transform.</span></span>  
  
 <span data-ttu-id="e423d-110">L’exemple suivant <xref:System.Windows.Shapes.Polyline> tourne un objet dans le sens des aiguilles d’une montre de 45 degrés sur le point (25,50).</span><span class="sxs-lookup"><span data-stu-id="e423d-110">The next example rotates a <xref:System.Windows.Shapes.Polyline> object clockwise 45 degrees about the point (25,50).</span></span>  
  
 [!code-xaml[Transforms_snip#RotatePolylineAboutCenter](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/RotateTransformExample.xaml#rotatepolylineaboutcenter)]  
  
 [!code-csharp[Transforms_Procedural_snip#RotatePolylineAboutCenter](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_Procedural_snip/CSharp/RotateTransformExample.cs#rotatepolylineaboutcenter)]
 [!code-vb[Transforms_Procedural_snip#RotatePolylineAboutCenter](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Transforms_Procedural_snip/VisualBasic/RotateTransformExample.vb#rotatepolylineaboutcenter)]  
  
 <span data-ttu-id="e423d-111">L’illustration suivante montre les <xref:System.Windows.Media.Transform> résultats de l’application d’un sur les deux objets.</span><span class="sxs-lookup"><span data-stu-id="e423d-111">The following illustration shows the results of applying a <xref:System.Windows.Media.Transform> to the two objects.</span></span>  
  
 <span data-ttu-id="e423d-112">![Rotations de 45 degrés avec différents points centraux](./media/wcpsdk-graphicsmm-rotatetransform45degrees.gif "wcpsdk_graphicsmm_rotatetransform45degrees")</span><span class="sxs-lookup"><span data-stu-id="e423d-112">![45 degree rotations with different center points](./media/wcpsdk-graphicsmm-rotatetransform45degrees.gif "wcpsdk_graphicsmm_rotatetransform45degrees")</span></span>  
<span data-ttu-id="e423d-113">Deux objets en rotation de 45 degrés à partir de différents centres de rotation</span><span class="sxs-lookup"><span data-stu-id="e423d-113">Two objects that rotate 45 degrees from different rotational centers</span></span>  
  
 <span data-ttu-id="e423d-114">Les <xref:System.Windows.Shapes.Polyline> exemples précédents <xref:System.Windows.UIElement>est un .</span><span class="sxs-lookup"><span data-stu-id="e423d-114">The <xref:System.Windows.Shapes.Polyline> in the previous examples is a <xref:System.Windows.UIElement>.</span></span> <span data-ttu-id="e423d-115">Lorsque vous <xref:System.Windows.Media.Transform> appliquez <xref:System.Windows.UIElement.RenderTransform%2A> un <xref:System.Windows.UIElement>à la propriété <xref:System.Windows.UIElement.RenderTransformOrigin%2A> d’un , <xref:System.Windows.Media.Transform> vous pouvez utiliser la propriété pour spécifier une origine pour chaque que vous appliquez à l’élément.</span><span class="sxs-lookup"><span data-stu-id="e423d-115">When you apply a <xref:System.Windows.Media.Transform> to the <xref:System.Windows.UIElement.RenderTransform%2A> property of a <xref:System.Windows.UIElement>, you can use the <xref:System.Windows.UIElement.RenderTransformOrigin%2A> property to specify an origin for every <xref:System.Windows.Media.Transform> that you apply to the element.</span></span> <span data-ttu-id="e423d-116">Parce <xref:System.Windows.UIElement.RenderTransformOrigin%2A> que la propriété utilise des coordonnées relatives, vous pouvez appliquer une transformation au centre de l’élément, même si vous ne connaissez pas sa taille.</span><span class="sxs-lookup"><span data-stu-id="e423d-116">Because the <xref:System.Windows.UIElement.RenderTransformOrigin%2A> property uses relative coordinates, you can apply a transformation to the center of the element even if you do not know its size.</span></span> <span data-ttu-id="e423d-117">Pour plus d’informations et par exemple, voir [Spécifier l’origine d’une transformation en utilisant des valeurs relatives](how-to-specify-the-origin-of-a-transform-by-using-relative-values.md).</span><span class="sxs-lookup"><span data-stu-id="e423d-117">For more information and for an example, see [Specify the Origin of a Transform by Using Relative Values](how-to-specify-the-origin-of-a-transform-by-using-relative-values.md).</span></span>  
  
 <span data-ttu-id="e423d-118">Pour voir l’exemple complet, consultez la page [2-D Transforms Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms) (Exemple de transformations 2D).</span><span class="sxs-lookup"><span data-stu-id="e423d-118">For the complete sample, see [2-D Transforms Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e423d-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e423d-119">See also</span></span>

- <xref:System.Windows.Media.Transform>
- [<span data-ttu-id="e423d-120">Vue d'ensemble des transformations</span><span class="sxs-lookup"><span data-stu-id="e423d-120">Transforms Overview</span></span>](transforms-overview.md)
- [<span data-ttu-id="e423d-121">Sujets comment se passer</span><span class="sxs-lookup"><span data-stu-id="e423d-121">How-to Topics</span></span>](transformations-how-to-topics.md)
