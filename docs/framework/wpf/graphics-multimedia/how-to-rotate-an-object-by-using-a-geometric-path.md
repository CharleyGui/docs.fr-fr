---
title: "Comment : faire pivoter un objet à l'aide d'un tracé géométrique"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- geometric paths [WPF], rotating objects by
- rotating objects by geometric paths [WPF]
ms.assetid: cb31ca4d-f05a-4c6b-9a18-4b6faaf38d45
ms.openlocfilehash: a351fdc936f634b7c57ba5a49e51501f7572a3c9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186877"
---
# <a name="how-to-rotate-an-object-by-using-a-geometric-path"></a><span data-ttu-id="75f0b-102">Comment : faire pivoter un objet à l'aide d'un tracé géométrique</span><span class="sxs-lookup"><span data-stu-id="75f0b-102">How to: Rotate an Object by Using a Geometric Path</span></span>
<span data-ttu-id="75f0b-103">Cet exemple montre comment faire pivoter (pivot) un objet <xref:System.Windows.Media.PathGeometry> le long d’un chemin géométrique défini par un objet.</span><span class="sxs-lookup"><span data-stu-id="75f0b-103">This example shows how to rotate (pivot) an object along a geometric path that is defined by a <xref:System.Windows.Media.PathGeometry> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="75f0b-104"> Exemple</span><span class="sxs-lookup"><span data-stu-id="75f0b-104">Example</span></span>  
 <span data-ttu-id="75f0b-105">L’exemple suivant <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> utilise trois objets pour déplacer un rectangle le long d’un chemin géométrique.</span><span class="sxs-lookup"><span data-stu-id="75f0b-105">The following example uses three <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> objects to move a rectangle along a geometric path.</span></span>  
  
- <span data-ttu-id="75f0b-106">Le <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> premier anime <xref:System.Windows.Media.RotateTransform> un qui est appliqué sur le rectangle.</span><span class="sxs-lookup"><span data-stu-id="75f0b-106">The first <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> animates a <xref:System.Windows.Media.RotateTransform> that is applied to the rectangle.</span></span> <span data-ttu-id="75f0b-107">L’animation génère des valeurs d’angle.</span><span class="sxs-lookup"><span data-stu-id="75f0b-107">The animation generates angle values.</span></span> <span data-ttu-id="75f0b-108">Le rectangle tourne (pivote) ainsi sur les contours du tracé.</span><span class="sxs-lookup"><span data-stu-id="75f0b-108">It makes the rectangle rotate (pivot) along the contours of the path.</span></span>  
  
- <span data-ttu-id="75f0b-109">Les deux autres objets <xref:System.Windows.Media.TranslateTransform.X%2A> animent les valeurs et <xref:System.Windows.Media.TranslateTransform.Y%2A> les valeurs d’un <xref:System.Windows.Media.TranslateTransform> qui est appliqué sur le rectangle.</span><span class="sxs-lookup"><span data-stu-id="75f0b-109">The other two objects animate the <xref:System.Windows.Media.TranslateTransform.X%2A> and <xref:System.Windows.Media.TranslateTransform.Y%2A> values of a <xref:System.Windows.Media.TranslateTransform> that is applied to the rectangle.</span></span> <span data-ttu-id="75f0b-110">Le rectangle se déplace alors horizontalement et verticalement sur le tracé.</span><span class="sxs-lookup"><span data-stu-id="75f0b-110">They make the rectangle move horizontally and vertically along the path.</span></span>  
  
 [!code-xaml[PathAnimationGallery_snippet#RotateAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/rotateanimationusingpathexample.xaml#rotateanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#RotateAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/RotateAnimationUsingPathExample.cs#rotateanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#RotateAnimationUsingPathWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/RotateAnimationUsingPathExample.vb#rotateanimationusingpathwholepage)]  
  
 <span data-ttu-id="75f0b-111">Une autre façon de faire pivoter un <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> objet en <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> utilisant `true`un chemin géométrique est d’utiliser un objet et de définir sa propriété à .</span><span class="sxs-lookup"><span data-stu-id="75f0b-111">Another way to rotate an object by using a geometric path is to use a <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> object and set its <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> property to `true`.</span></span> <span data-ttu-id="75f0b-112">Pour plus d’informations et un exemple, voir [Rotate an Object by Using a Geometric Path (Matrix Animation)](how-to-rotate-an-object-by-using-a-geometric-path-matrix-animation.md).</span><span class="sxs-lookup"><span data-stu-id="75f0b-112">For more information and an example, see [Rotate an Object by Using a Geometric Path (Matrix Animation)](how-to-rotate-an-object-by-using-a-geometric-path-matrix-animation.md).</span></span>  
  
 <span data-ttu-id="75f0b-113">Pour l’échantillon complet, voir [Échantillon d’animation Path](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations).</span><span class="sxs-lookup"><span data-stu-id="75f0b-113">For the complete sample, see [Path Animation Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75f0b-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="75f0b-114">See also</span></span>

- [<span data-ttu-id="75f0b-115">Vue d’ensemble de l’animation</span><span class="sxs-lookup"><span data-stu-id="75f0b-115">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="75f0b-116">Animation de tracés, exemple</span><span class="sxs-lookup"><span data-stu-id="75f0b-116">Path Animation Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations)
- [<span data-ttu-id="75f0b-117">Guides pratiques relatifs aux animations de tracés</span><span class="sxs-lookup"><span data-stu-id="75f0b-117">Path Animation How-to Topics</span></span>](path-animation-how-to-topics.md)
