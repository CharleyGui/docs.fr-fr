---
title: 'Comment : Animer une rotation 3D à l’aide de cadres clés (QuaternionAnimationUsingKeyFrames)'
ms.date: 03/30/2017
helpviewer_keywords:
- 3D translations [WPF], animating [WPF], with key frames (QuaternionAnimationUsingKeyFrames)
- key frames [WPF], QuaternionAnimationUsingKeyFrames
- animation [WPF], 3D translations [WPF], with key frames (QuaternionAnimationUsingKeyFrames)
ms.assetid: 09e5707b-7523-4a08-9aa7-bb13cbedccdf
ms.openlocfilehash: 5273183aaa49a743cc401dec0b4b16bae09e3129
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112295"
---
# <a name="how-to-animate-a-3d-rotation-using-key-frames-quaternionanimationusingkeyframes"></a><span data-ttu-id="4cead-102">Comment : Animer une rotation 3D à l’aide de cadres clés (QuaternionAnimationUsingKeyFrames)</span><span class="sxs-lookup"><span data-stu-id="4cead-102">How to: Animate a 3D Rotation Using Key Frames (QuaternionAnimationUsingKeyFrames)</span></span>
<span data-ttu-id="4cead-103">Dans l’exemple <xref:System.Windows.Media.Animation.QuaternionAnimationUsingKeyFrames> suivant, est utilisé pour faire tourner un objet 3D.</span><span class="sxs-lookup"><span data-stu-id="4cead-103">In the following example, <xref:System.Windows.Media.Animation.QuaternionAnimationUsingKeyFrames> is used to make a 3D object rotate.</span></span> <span data-ttu-id="4cead-104">Cette animation utilise les cadres clés suivants :</span><span class="sxs-lookup"><span data-stu-id="4cead-104">This animation uses the following key frames:</span></span>  
  
1. <span data-ttu-id="4cead-105"><xref:System.Windows.Media.Animation.LinearRotation3DKeyFrame>est utilisé pour créer une interpolation lisse et linéaire entre les valeurs.</span><span class="sxs-lookup"><span data-stu-id="4cead-105"><xref:System.Windows.Media.Animation.LinearRotation3DKeyFrame> is used to create a smooth, linear interpolation between values.</span></span>  
  
2. <span data-ttu-id="4cead-106"><xref:System.Windows.Media.Animation.DiscreteRotation3DKeyFrame>est utilisé pour créer des « sauts » soudains entre les valeurs (pas d’interpolation).</span><span class="sxs-lookup"><span data-stu-id="4cead-106"><xref:System.Windows.Media.Animation.DiscreteRotation3DKeyFrame> is used to create sudden "jumps" between values (no interpolation).</span></span>  
  
3. <span data-ttu-id="4cead-107"><xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame>est utilisé pour créer une transition <xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame.KeySpline%2A> variable entre les valeurs en fonction de la propriété.</span><span class="sxs-lookup"><span data-stu-id="4cead-107"><xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame> is used to create a variable transition between values depending on the <xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame.KeySpline%2A> property.</span></span> <span data-ttu-id="4cead-108">Dans l’exemple ci-dessous, cette partie de l’animation commence lentement mais vers la fin du segment de temps, accélère de façon exponentielle.</span><span class="sxs-lookup"><span data-stu-id="4cead-108">In the example below, this part of the animation starts off slow but toward the end of the time segment, speeds up exponentially.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4cead-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="4cead-109">Example</span></span>  
 [!code-xaml[Animation3DGallery_snip#QuaternionAnimationUsingKeyFramesExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/QuaternionAnimationUsingKeyFramesExample.xaml#quaternionanimationusingkeyframesexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="4cead-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4cead-110">See also</span></span>

- [<span data-ttu-id="4cead-111">Animer une rotation 3D à l’aide de storyboards</span><span class="sxs-lookup"><span data-stu-id="4cead-111">Animate a 3D Rotation Using Storyboards</span></span>](how-to-animate-a-3-d-rotation-using-storyboards.md)
- [<span data-ttu-id="4cead-112">Animer une rotation 3D à l’aide de Rotation3DAnimation</span><span class="sxs-lookup"><span data-stu-id="4cead-112">Animate a 3D Rotation Using Rotation3DAnimation</span></span>](how-to-animate-a-3-d-rotation-using-rotation3danimation.md)
- [<span data-ttu-id="4cead-113">Animer une rotation 3D à l’aide de quaternions</span><span class="sxs-lookup"><span data-stu-id="4cead-113">Animate a 3D Rotation Using Quaternions</span></span>](how-to-animate-a-3-d-rotation-using-quaternions.md)
- [<span data-ttu-id="4cead-114">Animez une rotation 3D à l’aide de cadres clés (Rotation3DAnimationUsingKeyFrames)</span><span class="sxs-lookup"><span data-stu-id="4cead-114">Animate a 3D Rotation Using Key Frames (Rotation3DAnimationUsingKeyFrames)</span></span>](how-to-animate-a-3-d-rotation-using-key-frames.md)
- [<span data-ttu-id="4cead-115">Aperçu graphique 3D</span><span class="sxs-lookup"><span data-stu-id="4cead-115">3D Graphics Overview</span></span>](3-d-graphics-overview.md)
- [<span data-ttu-id="4cead-116">Vue d'ensemble des animations d'image clé</span><span class="sxs-lookup"><span data-stu-id="4cead-116">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
