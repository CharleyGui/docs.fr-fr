---
title: "Comment : faire pivoter un objet à l'aide d'un tracé géométrique (animation de matrice)"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- geometric paths [WPF], rotating objects by
- rotating objects by geometric paths [WPF]
- matrix animation [WPF]
ms.assetid: 877dc9aa-6bdc-4beb-8772-3efaec32c0f0
ms.openlocfilehash: 63dc873a2b840ea3f870a8c60c5691ab271c1c9f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187413"
---
# <a name="how-to-rotate-an-object-by-using-a-geometric-path-matrix-animation"></a><span data-ttu-id="45607-102">Comment : faire pivoter un objet à l'aide d'un tracé géométrique (animation de matrice)</span><span class="sxs-lookup"><span data-stu-id="45607-102">How to: Rotate an Object by Using a Geometric Path (Matrix Animation)</span></span>
<span data-ttu-id="45607-103">Cet exemple montre comment <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> utiliser <xref:System.Windows.Media.MatrixTransform> un et un pour faire pivoter <xref:System.Windows.Media.PathGeometry> (pivot) un objet le long d’un chemin géométrique défini par un objet.</span><span class="sxs-lookup"><span data-stu-id="45607-103">This example shows how to use a <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> and a <xref:System.Windows.Media.MatrixTransform> to rotate (pivot) an object along a geometric path defined by a <xref:System.Windows.Media.PathGeometry> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="45607-104"> Exemple</span><span class="sxs-lookup"><span data-stu-id="45607-104">Example</span></span>  
 <span data-ttu-id="45607-105">L’exemple suivant <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> utilise l’objet <xref:System.Windows.Media.MatrixTransform.Matrix%2A> pour <xref:System.Windows.Media.MatrixTransform>animer la propriété d’un .</span><span class="sxs-lookup"><span data-stu-id="45607-105">The following example uses the <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> object to animate the <xref:System.Windows.Media.MatrixTransform.Matrix%2A> property of a <xref:System.Windows.Media.MatrixTransform>.</span></span> <span data-ttu-id="45607-106">Le <xref:System.Windows.Media.MatrixTransform> est appliqué sur un bouton et le fait se déplacer le long d’un chemin incurvé.</span><span class="sxs-lookup"><span data-stu-id="45607-106">The <xref:System.Windows.Media.MatrixTransform> is applied to a button and causes it to move along a curved path.</span></span> <span data-ttu-id="45607-107">Parce <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> que la `true`propriété est réglée à , le rectangle tourne le long de la tangente du chemin.</span><span class="sxs-lookup"><span data-stu-id="45607-107">Because the <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> property is set to `true`, the rectangle rotates along the tangent of the path.</span></span>  
  
 [!code-xaml[PathAnimationGallery_snippet#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/matrixanimationusingpathdoesrotatewithtangentexample.xaml#matrixanimationusingpathdoesrotatewithtangentwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/MatrixAnimationUsingPathDoesRotateWithTangentExample.cs#matrixanimationusingpathdoesrotatewithtangentwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/MatrixAnimationUsingPathDoesRotateWithTangentExample.vb#matrixanimationusingpathdoesrotatewithtangentwholepage)]  
  
 <span data-ttu-id="45607-108">Pour l’échantillon complet, voir [Échantillon d’animation Path](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations).</span><span class="sxs-lookup"><span data-stu-id="45607-108">For the complete sample, see [Path Animation Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations).</span></span>  
  
 <span data-ttu-id="45607-109">La version de code de <xref:System.Windows.Media.Animation.Storyboard> l’échantillon <xref:System.Windows.Media.EllipseGeometry>précédent a utilisé un pour animer le , même si une seule animation a été appliquée.</span><span class="sxs-lookup"><span data-stu-id="45607-109">The code version of the preceding sample used a <xref:System.Windows.Media.Animation.Storyboard> to animate the <xref:System.Windows.Media.EllipseGeometry>, even though only one animation was applied.</span></span> <span data-ttu-id="45607-110">Un moyen plus facile d’appliquer une seule animation <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> à une propriété en code est d’utiliser la méthode.</span><span class="sxs-lookup"><span data-stu-id="45607-110">An easier way to apply a single animation to a property in code is to use the <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> method.</span></span> <span data-ttu-id="45607-111">Par exemple, voir [Animate une propriété sans utiliser un storyboard](how-to-animate-a-property-without-using-a-storyboard.md).</span><span class="sxs-lookup"><span data-stu-id="45607-111">For an example, see [Animate a Property Without Using a Storyboard](how-to-animate-a-property-without-using-a-storyboard.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45607-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="45607-112">See also</span></span>

- [<span data-ttu-id="45607-113">Vue d’ensemble de l’animation</span><span class="sxs-lookup"><span data-stu-id="45607-113">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="45607-114">Guides pratiques relatifs aux animations de tracés</span><span class="sxs-lookup"><span data-stu-id="45607-114">Path Animation How-to Topics</span></span>](path-animation-how-to-topics.md)
- [<span data-ttu-id="45607-115">Animation de tracés, exemple</span><span class="sxs-lookup"><span data-stu-id="45607-115">Path Animation Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations)
