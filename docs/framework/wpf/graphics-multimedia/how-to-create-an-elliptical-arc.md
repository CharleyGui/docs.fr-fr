---
title: 'Comment : créer un arc elliptique'
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], elliptical arcs
- elliptical arcs [WPF], creating
- arcs [WPF], elliptical
ms.assetid: 3dcfe502-3485-45de-99fb-d53a1367c484
ms.openlocfilehash: d0fffbb25f3c5aaceb2cd80af4f1093e44111200
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77453063"
---
# <a name="how-to-create-an-elliptical-arc"></a><span data-ttu-id="0bf19-102">Comment : créer un arc elliptique</span><span class="sxs-lookup"><span data-stu-id="0bf19-102">How to: Create an Elliptical Arc</span></span>
<span data-ttu-id="0bf19-103">Cet exemple montre comment dessiner un arc elliptique. Pour créer un arc elliptique, utilisez les classes <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure>et <xref:System.Windows.Media.ArcSegment>.</span><span class="sxs-lookup"><span data-stu-id="0bf19-103">This example shows how to draw an elliptical arc. To create an elliptical arc, use the <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure>, and <xref:System.Windows.Media.ArcSegment> classes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0bf19-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="0bf19-104">Example</span></span>  
 <span data-ttu-id="0bf19-105">Dans les exemples suivants, un arc elliptique est dessiné de (10 100) à (200 100).</span><span class="sxs-lookup"><span data-stu-id="0bf19-105">In the following examples, an elliptical arc is drawn from (10,100) to (200,100).</span></span> <span data-ttu-id="0bf19-106">L’ARC a une <xref:System.Windows.Media.ArcSegment.Size%2A> de 100 par 50 pixels indépendants du périphérique, un <xref:System.Windows.Media.ArcSegment.RotationAngle%2A> de 45 degrés, un paramètre de <xref:System.Windows.Media.ArcSegment.IsLargeArc%2A> de `true`et un <xref:System.Windows.Media.ArcSegment.SweepDirection%2A> de <xref:System.Windows.Media.SweepDirection.Counterclockwise>.</span><span class="sxs-lookup"><span data-stu-id="0bf19-106">The arc has a <xref:System.Windows.Media.ArcSegment.Size%2A> of 100 by 50 device-independent pixels, a <xref:System.Windows.Media.ArcSegment.RotationAngle%2A> of 45 degrees, an <xref:System.Windows.Media.ArcSegment.IsLargeArc%2A> setting of `true`, and a <xref:System.Windows.Media.ArcSegment.SweepDirection%2A> of <xref:System.Windows.Media.SweepDirection.Counterclockwise>.</span></span>  
  
 <span data-ttu-id="0bf19-107">[xaml]</span><span class="sxs-lookup"><span data-stu-id="0bf19-107">[xaml]</span></span>  
  
 <span data-ttu-id="0bf19-108">Dans [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], vous pouvez utiliser la syntaxe d’attribut pour décrire un chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="0bf19-108">In [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], you can use attribute syntax to describe a path.</span></span>  
  
 [!code-xaml[GeometrySample#56](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/geometryattributesyntaxexample.xaml#56)]  
  
 <span data-ttu-id="0bf19-109">[xaml]</span><span class="sxs-lookup"><span data-stu-id="0bf19-109">[xaml]</span></span>  
  
 <span data-ttu-id="0bf19-110">(Notez que cette syntaxe d’attribut crée en fait un <xref:System.Windows.Media.StreamGeometry>, une version plus légère d’une <xref:System.Windows.Media.PathGeometry>.</span><span class="sxs-lookup"><span data-stu-id="0bf19-110">(Note that this attribute syntax actually creates a <xref:System.Windows.Media.StreamGeometry>, a lighter-weight version of a <xref:System.Windows.Media.PathGeometry>.</span></span> <span data-ttu-id="0bf19-111">(Pour plus d’informations, consultez la page [Syntaxe XAML pour les tracés](path-markup-syntax.md).)</span><span class="sxs-lookup"><span data-stu-id="0bf19-111">For more information, see the [Path Markup Syntax](path-markup-syntax.md) page.)</span></span>  
  
 <span data-ttu-id="0bf19-112">Dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], vous pouvez également dessiner un arc elliptique en utilisant explicitement des balises d’objet.</span><span class="sxs-lookup"><span data-stu-id="0bf19-112">In [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], you can also draw an elliptical arc by explicitly using object tags.</span></span> <span data-ttu-id="0bf19-113">Les éléments suivants sont équivalents à la balise [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] précédente.</span><span class="sxs-lookup"><span data-stu-id="0bf19-113">The following is equivalent to the preceding [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup.</span></span>  
  
 [!code-xaml[GeometrySample#36](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#36)]  
  
 <span data-ttu-id="0bf19-114">Cet exemple fait partie d’un exemple plus complet.</span><span class="sxs-lookup"><span data-stu-id="0bf19-114">This example is part of a larger sample.</span></span> <span data-ttu-id="0bf19-115">Pour obtenir l’exemple complet, consultez l' [exemple Geometries](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry).</span><span class="sxs-lookup"><span data-stu-id="0bf19-115">For the complete sample, see the [Geometries Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0bf19-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0bf19-116">See also</span></span>

- [<span data-ttu-id="0bf19-117">Créer une courbe de Bézier quadratique</span><span class="sxs-lookup"><span data-stu-id="0bf19-117">Create a Quadratic Bezier Curve</span></span>](how-to-create-a-quadratic-bezier-curve.md)
- [<span data-ttu-id="0bf19-118">Créer une courbe de Bézier cubique</span><span class="sxs-lookup"><span data-stu-id="0bf19-118">Create a Cubic Bezier Curve</span></span>](how-to-create-a-cubic-bezier-curve.md)
