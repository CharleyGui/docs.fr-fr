---
title: "Comment : animer la position et la direction d'une caméra à l'aide d'images clés"
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], camera direction with key frames
- key frames [WPF], animating camera direction
- animation [WPF], camera position with key frames
- camera position [WPF], animating with key frames
- key frames [WPF], animating camera position
- camera direction [WPF], animating with key frames
ms.assetid: 5753024e-0057-454d-947f-43ea686879c7
ms.openlocfilehash: 28471f9b42140a6c75b043d33939503528b63194
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112165"
---
# <a name="how-to-animate-camera-position-and-direction-using-key-frames"></a><span data-ttu-id="08842-102">Comment : animer la position et la direction d'une caméra à l'aide d'images clés</span><span class="sxs-lookup"><span data-stu-id="08842-102">How to: Animate Camera Position and Direction Using Key Frames</span></span>
<span data-ttu-id="08842-103">Dans l’exemple <xref:System.Windows.Media.Animation.Point3DAnimationUsingKeyFrames> suivant, est utilisé pour <xref:System.Windows.Media.Media3D.PerspectiveCamera> animer la position d’une scène 3D.</span><span class="sxs-lookup"><span data-stu-id="08842-103">In the following example, <xref:System.Windows.Media.Animation.Point3DAnimationUsingKeyFrames> is used to animate the position of a <xref:System.Windows.Media.Media3D.PerspectiveCamera> in a 3D scene.</span></span> <span data-ttu-id="08842-104">En outre, <xref:System.Windows.Media.Animation.Vector3DAnimationUsingKeyFrames> est utilisé pour animer la direction de la caméra est pointant dans la scène 3D.</span><span class="sxs-lookup"><span data-stu-id="08842-104">In addition, <xref:System.Windows.Media.Animation.Vector3DAnimationUsingKeyFrames> is used to animate the direction the camera is pointing in the 3D scene.</span></span> <span data-ttu-id="08842-105">Ces deux animations utilisent plusieurs cadres clés qui créent une série d’effets d’animation :</span><span class="sxs-lookup"><span data-stu-id="08842-105">Both of these animations use several key frames which create a series of animation effects:</span></span>  
  
1. <span data-ttu-id="08842-106"><xref:System.Windows.Media.Animation.LinearPoint3DKeyFrame>et <xref:System.Windows.Media.Animation.LinearVector3DKeyFrame> sont utilisés pour créer une interpolation lisse et linéaire entre les valeurs.</span><span class="sxs-lookup"><span data-stu-id="08842-106"><xref:System.Windows.Media.Animation.LinearPoint3DKeyFrame> and <xref:System.Windows.Media.Animation.LinearVector3DKeyFrame> are used to create a smooth, linear interpolation between values.</span></span>  
  
2. <span data-ttu-id="08842-107"><xref:System.Windows.Media.Animation.DiscretePoint3DKeyFrame>et <xref:System.Windows.Media.Animation.DiscreteVector3DKeyFrame> sont utilisés pour créer des « sauts » soudains entre les valeurs (pas d’interpolation).</span><span class="sxs-lookup"><span data-stu-id="08842-107"><xref:System.Windows.Media.Animation.DiscretePoint3DKeyFrame> and <xref:System.Windows.Media.Animation.DiscreteVector3DKeyFrame> are used to create sudden "jumps" between values (no interpolation).</span></span>  
  
3. <span data-ttu-id="08842-108"><xref:System.Windows.Media.Animation.SplinePoint3DKeyFrame>et <xref:System.Windows.Media.Animation.SplineVector3DKeyFrame> sont utilisés pour créer une transition <xref:System.Windows.Media.Animation.SplinePoint3DKeyFrame.KeySpline%2A> variable entre les valeurs en fonction de la propriété.</span><span class="sxs-lookup"><span data-stu-id="08842-108"><xref:System.Windows.Media.Animation.SplinePoint3DKeyFrame> and <xref:System.Windows.Media.Animation.SplineVector3DKeyFrame> are used to create a variable transition between values depending on the <xref:System.Windows.Media.Animation.SplinePoint3DKeyFrame.KeySpline%2A> property.</span></span> <span data-ttu-id="08842-109">Dans l’exemple ci-dessous, l’animation commence lentement, mais vers la fin du segment de temps, accélère de façon exponentielle.</span><span class="sxs-lookup"><span data-stu-id="08842-109">In the example below, the animation starts off slow but toward the end of the time segment, speeds up exponentially.</span></span>  
  
## <a name="example"></a><span data-ttu-id="08842-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="08842-110">Example</span></span>  
 [!code-xaml[Animation3DGallery_snip#PointVector3DAnimationUsingKeyFramesExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/PointVector3DAnimationUsingKeyFramesExample.xaml#pointvector3danimationusingkeyframesexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="08842-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="08842-111">See also</span></span>

- [<span data-ttu-id="08842-112">Animer la position et la direction de la caméra d’une scène 3D</span><span class="sxs-lookup"><span data-stu-id="08842-112">Animate Camera Position and Direction in a 3D Scene</span></span>](how-to-animate-camera-position-and-direction-in-a-3d-scene.md)
- [<span data-ttu-id="08842-113">Aperçu graphique 3D</span><span class="sxs-lookup"><span data-stu-id="08842-113">3D Graphics Overview</span></span>](3-d-graphics-overview.md)
