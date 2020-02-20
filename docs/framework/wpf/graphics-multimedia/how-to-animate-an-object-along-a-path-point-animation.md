---
title: 'Comment : animer un objet sur un tracé (animation de point)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], objects along paths (point animation)
- point animation [WPF]
ms.assetid: 1fa3f817-35bc-41a1-b366-f5a20b70da0c
ms.openlocfilehash: eff0c24a9369ffaa0cfca1cc46af4eff39f58a38
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452894"
---
# <a name="how-to-animate-an-object-along-a-path-point-animation"></a><span data-ttu-id="4b88c-102">Comment : animer un objet sur un tracé (animation de point)</span><span class="sxs-lookup"><span data-stu-id="4b88c-102">How to: Animate an Object Along a Path (Point Animation)</span></span>
<span data-ttu-id="4b88c-103">Cet exemple montre comment utiliser un objet <xref:System.Windows.Media.Animation.PointAnimationUsingPath> pour animer une <xref:System.Windows.Point> le long d’un tracé courbé.</span><span class="sxs-lookup"><span data-stu-id="4b88c-103">This example shows how to use a <xref:System.Windows.Media.Animation.PointAnimationUsingPath> object to animate a <xref:System.Windows.Point> along a curved path.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4b88c-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="4b88c-104">Example</span></span>  
 <span data-ttu-id="4b88c-105">L’exemple suivant déplace un <xref:System.Windows.Media.EllipseGeometry> le long d’un chemin d’accès défini par un <xref:System.Windows.Media.PathGeometry>.</span><span class="sxs-lookup"><span data-stu-id="4b88c-105">The following example moves an <xref:System.Windows.Media.EllipseGeometry> along a path defined by a <xref:System.Windows.Media.PathGeometry>.</span></span> <span data-ttu-id="4b88c-106">La propriété de <xref:System.Windows.Media.EllipseGeometry.Center%2A> de la géométrie d’ellipse, qui prend une valeur de <xref:System.Windows.Point>, spécifie sa position ; pour déplacer la géométrie d’ellipse, vous animez sa propriété <xref:System.Windows.Media.EllipseGeometry.Center%2A>.</span><span class="sxs-lookup"><span data-stu-id="4b88c-106">The ellipse geometry's <xref:System.Windows.Media.EllipseGeometry.Center%2A> property, which takes a <xref:System.Windows.Point> value, specifies its position; to move the ellipse geometry, you animate its <xref:System.Windows.Media.EllipseGeometry.Center%2A> property.</span></span> <span data-ttu-id="4b88c-107">L’exemple utilise une <xref:System.Windows.Media.Animation.PointAnimationUsingPath> pour animer la propriété <xref:System.Windows.Media.EllipseGeometry.Center%2A> de l’objet <xref:System.Windows.Media.EllipseGeometry>.</span><span class="sxs-lookup"><span data-stu-id="4b88c-107">The example uses a <xref:System.Windows.Media.Animation.PointAnimationUsingPath> to animate the <xref:System.Windows.Media.EllipseGeometry> object's <xref:System.Windows.Media.EllipseGeometry.Center%2A> property.</span></span>  
  
 [!code-xaml[PathAnimationGallery_snippet#PointAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/pointanimationusingpathexample.xaml#pointanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#PointAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/PointAnimationUsingPathExample.cs#pointanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#PointAnimationUsingPathWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/PointAnimationUsingPathExample.vb#pointanimationusingpathwholepage)]  
  
 <span data-ttu-id="4b88c-108">Pour obtenir l’exemple complet, consultez [exemple d’animation de tracés](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations).</span><span class="sxs-lookup"><span data-stu-id="4b88c-108">For the complete sample, see [Path Animation Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations).</span></span>  
  
 <span data-ttu-id="4b88c-109">La version de code de l’exemple précédent utilisait une <xref:System.Windows.Media.Animation.Storyboard> pour animer le <xref:System.Windows.Media.EllipseGeometry>, même si une seule animation a été appliquée.</span><span class="sxs-lookup"><span data-stu-id="4b88c-109">The code version of the preceding sample used a <xref:System.Windows.Media.Animation.Storyboard> to animate the <xref:System.Windows.Media.EllipseGeometry>, even though only one animation was applied.</span></span> <span data-ttu-id="4b88c-110">Un <xref:System.Windows.Media.Animation.Storyboard> est souvent le moyen le plus simple d’appliquer plusieurs animations, car ces animations peuvent être contrôlées par le même <xref:System.Windows.Media.Animation.Storyboard>.</span><span class="sxs-lookup"><span data-stu-id="4b88c-110">A <xref:System.Windows.Media.Animation.Storyboard> is often the easiest way to apply multiple animations because these animations can be controlled by the same <xref:System.Windows.Media.Animation.Storyboard>.</span></span> <span data-ttu-id="4b88c-111">Toutefois, un moyen plus simple d’appliquer une seule animation à une propriété lors de l’utilisation du code consiste à utiliser la méthode <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>.</span><span class="sxs-lookup"><span data-stu-id="4b88c-111">However, an easier way to apply a single animation to a property when using code is to use the <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> method.</span></span> <span data-ttu-id="4b88c-112">Si vous voulez voir un exemple, consultez l’article [Comment : animer une propriété sans utiliser de storyboard](how-to-animate-a-property-without-using-a-storyboard.md).</span><span class="sxs-lookup"><span data-stu-id="4b88c-112">For an example, see [Animate a Property Without Using a Storyboard](how-to-animate-a-property-without-using-a-storyboard.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b88c-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4b88c-113">See also</span></span>

- [<span data-ttu-id="4b88c-114">Animation de tracés, exemple</span><span class="sxs-lookup"><span data-stu-id="4b88c-114">Path Animation Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations)
- [<span data-ttu-id="4b88c-115">Vue d’ensemble de l’animation</span><span class="sxs-lookup"><span data-stu-id="4b88c-115">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="4b88c-116">Guides pratiques relatifs aux animations de tracés</span><span class="sxs-lookup"><span data-stu-id="4b88c-116">Path Animation How-to Topics</span></span>](path-animation-how-to-topics.md)
