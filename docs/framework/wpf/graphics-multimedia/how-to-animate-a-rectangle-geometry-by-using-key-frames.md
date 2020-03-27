---
title: "Comment : animer une géométrie rectangle à l'aide d'images clés"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- key frames [WPF], animating RectangleGeometry objects with
- RectangleGeometry objects [WPF], animating with key frames
- animation [WPF], RectangleGeometry objects with key frames
ms.assetid: a8b45ceb-0e32-4ba1-928f-df6d30db17c6
ms.openlocfilehash: bcc9e7f198b8a20ffe13daf6508fb8a735937652
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344681"
---
# <a name="how-to-animate-a-rectangle-geometry-by-using-key-frames"></a><span data-ttu-id="20a23-102">Comment : animer une géométrie rectangle à l'aide d'images clés</span><span class="sxs-lookup"><span data-stu-id="20a23-102">How to: Animate a Rectangle Geometry by Using Key Frames</span></span>
<span data-ttu-id="20a23-103">Cet exemple montre comment animer <xref:System.Windows.Media.RectangleGeometry.Rect%2A> la <xref:System.Windows.Media.RectangleGeometry> propriété d’un en utilisant des cadres clés.</span><span class="sxs-lookup"><span data-stu-id="20a23-103">This example shows how to animate the <xref:System.Windows.Media.RectangleGeometry.Rect%2A> property of a <xref:System.Windows.Media.RectangleGeometry> by using key frames.</span></span>  
  
## <a name="example"></a><span data-ttu-id="20a23-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="20a23-104">Example</span></span>  
 <span data-ttu-id="20a23-105">L’exemple suivant <xref:System.Windows.Media.Animation.RectAnimationUsingKeyFrames> utilise la classe <xref:System.Windows.Media.RectangleGeometry.Rect%2A> pour <xref:System.Windows.Media.RectangleGeometry>animer la propriété d’un .</span><span class="sxs-lookup"><span data-stu-id="20a23-105">The following example uses the <xref:System.Windows.Media.Animation.RectAnimationUsingKeyFrames> class to animate the <xref:System.Windows.Media.RectangleGeometry.Rect%2A> property of a <xref:System.Windows.Media.RectangleGeometry>.</span></span> <span data-ttu-id="20a23-106">Cette animation utilise trois images clés de la manière suivante :</span><span class="sxs-lookup"><span data-stu-id="20a23-106">This animation uses three key frames in the following manner:</span></span>  
  
1. <span data-ttu-id="20a23-107">Pendant les deux premières secondes, <xref:System.Windows.Media.Animation.LinearRectKeyFrame> utilise un exemple de la classe pour animer un changement progressif de la position, la largeur et la hauteur d’un rectangle.</span><span class="sxs-lookup"><span data-stu-id="20a23-107">During the first two seconds, uses an instance of the <xref:System.Windows.Media.Animation.LinearRectKeyFrame> class to animate a gradual change in the position, width, and height of a rectangle.</span></span> <span data-ttu-id="20a23-108">Cadres de clés <xref:System.Windows.Media.Animation.LinearRectKeyFrame> linéaires comme créer une transition linéaire en douceur entre les valeurs.</span><span class="sxs-lookup"><span data-stu-id="20a23-108">Linear key frames like <xref:System.Windows.Media.Animation.LinearRectKeyFrame> create a smooth linear transition between values.</span></span>  
  
2. <span data-ttu-id="20a23-109">À la fin de la seconde suivante, <xref:System.Windows.Media.Animation.DiscreteRectKeyFrame> utilise un exemple de la classe pour diminuer soudainement la hauteur du rectangle.</span><span class="sxs-lookup"><span data-stu-id="20a23-109">During the end of the next half second, uses an instance of the <xref:System.Windows.Media.Animation.DiscreteRectKeyFrame> class to suddenly decrease the height of the rectangle.</span></span> <span data-ttu-id="20a23-110">Des cadres clés <xref:System.Windows.Media.Animation.DiscreteRectKeyFrame> discrets comme créer des changements soudains entre les valeurs, c’est-à-dire que la diminution de la hauteur se produit rapidement et n’est pas subtile.</span><span class="sxs-lookup"><span data-stu-id="20a23-110">Discrete key frames like <xref:System.Windows.Media.Animation.DiscreteRectKeyFrame> create sudden changes between values, that is, the decrease in height occurs quickly and is not subtle.</span></span>  
  
3. <span data-ttu-id="20a23-111">Pendant les deux dernières secondes, <xref:System.Windows.Media.Animation.SplineRectKeyFrame> utilise une instance de la classe pour changer le rectangle de nouveau à sa taille d’origine et la position.</span><span class="sxs-lookup"><span data-stu-id="20a23-111">During the final two seconds, uses an instance of the <xref:System.Windows.Media.Animation.SplineRectKeyFrame> class to change the rectangle back to its original size and position.</span></span> <span data-ttu-id="20a23-112">Les cadres clés <xref:System.Windows.Media.Animation.SplineRectKeyFrame> de Spline comme créer une transition <xref:System.Windows.Media.Animation.SplineRectKeyFrame.KeySpline%2A> variable entre les valeurs en fonction des valeurs de la propriété.</span><span class="sxs-lookup"><span data-stu-id="20a23-112">Spline key frames like <xref:System.Windows.Media.Animation.SplineRectKeyFrame> create a variable transition between values according to the values of the <xref:System.Windows.Media.Animation.SplineRectKeyFrame.KeySpline%2A> property.</span></span> <span data-ttu-id="20a23-113">Dans cet exemple, le changement commence lentement, puis accélère de façon exponentielle jusqu’à la fin du segment temporel.</span><span class="sxs-lookup"><span data-stu-id="20a23-113">In this example, the change begins slowly and speeds up exponentially toward the end of the time segment.</span></span>  
  
 [!code-csharp[keyframes_snip#RectAnimationUsingKeyFramesWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/RectAnimationUsingKeyFramesExample.cs#rectanimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#RectAnimationUsingKeyFramesWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/rectanimationusingkeyframesexample.vb#rectanimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#RectAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/RectAnimationUsingKeyFramesExample.xaml#rectanimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="20a23-114">Pour l’exemple complet, consultez la page [Animation d’image clé, exemple](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).</span><span class="sxs-lookup"><span data-stu-id="20a23-114">For the complete sample, see [KeyFrame Animation Sample](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20a23-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="20a23-115">See also</span></span>

- <xref:System.Windows.Media.RectangleGeometry>
- <xref:System.Windows.Media.RectangleGeometry.Rect%2A>
- <xref:System.Windows.Media.Animation.RectAnimationUsingKeyFrames>
- [<span data-ttu-id="20a23-116">Vue d'ensemble des animations d'image clé</span><span class="sxs-lookup"><span data-stu-id="20a23-116">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="20a23-117">Guides pratiques relatifs aux images clés</span><span class="sxs-lookup"><span data-stu-id="20a23-117">Key-Frame How-to Topics</span></span>](key-frame-animation-how-to-topics.md)
