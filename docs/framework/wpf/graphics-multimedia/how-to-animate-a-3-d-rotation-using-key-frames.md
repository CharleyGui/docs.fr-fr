---
title: 'Comment : Animer une rotation 3D à l’aide de cadres clés'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], 3D translations [WPF], with key frames (Rotation3DAnimation)
- key frames [WPF], Rotation3DAnimation
- 3D translations [WPF], animating [WPF], with key frames (Rotation3DAnimation)
ms.assetid: 6f671b95-7f30-4836-9a4f-aeb7dc30121f
ms.openlocfilehash: 2b9059df079125c34c70237c0f600751020044c6
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112308"
---
# <a name="how-to-animate-a-3d-rotation-using-key-frames"></a><span data-ttu-id="e9211-102">Comment : Animer une rotation 3D à l’aide de cadres clés</span><span class="sxs-lookup"><span data-stu-id="e9211-102">How to: Animate a 3D Rotation Using Key Frames</span></span>
<span data-ttu-id="e9211-103">Dans l’exemple <xref:System.Windows.Media.Animation.Rotation3DAnimationUsingKeyFrames> suivant, est utilisé pour faire tourner un objet 3D tandis que son axe de rotation anime résultant en un "wobble".</span><span class="sxs-lookup"><span data-stu-id="e9211-103">In the following example, <xref:System.Windows.Media.Animation.Rotation3DAnimationUsingKeyFrames> is used to make a 3D object rotate while its axis of rotation animates resulting in a "wobble".</span></span> <span data-ttu-id="e9211-104">Cette animation utilise les cadres clés suivants :</span><span class="sxs-lookup"><span data-stu-id="e9211-104">This animation uses the following key frames:</span></span>  
  
1. <span data-ttu-id="e9211-105"><xref:System.Windows.Media.Animation.LinearRotation3DKeyFrame>est utilisé pour créer une interpolation lisse et linéaire entre les valeurs.</span><span class="sxs-lookup"><span data-stu-id="e9211-105"><xref:System.Windows.Media.Animation.LinearRotation3DKeyFrame> is used to create a smooth, linear interpolation between values.</span></span>  
  
2. <span data-ttu-id="e9211-106"><xref:System.Windows.Media.Animation.DiscreteRotation3DKeyFrame>est utilisé pour créer des « sauts » soudains entre les valeurs (pas d’interpolation).</span><span class="sxs-lookup"><span data-stu-id="e9211-106"><xref:System.Windows.Media.Animation.DiscreteRotation3DKeyFrame> is used to create sudden "jumps" between values (no interpolation).</span></span>  
  
3. <span data-ttu-id="e9211-107"><xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame>est utilisé pour créer une transition <xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame.KeySpline%2A> variable entre les valeurs en fonction de la propriété.</span><span class="sxs-lookup"><span data-stu-id="e9211-107"><xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame> is used to create a variable transition between values depending on the <xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame.KeySpline%2A> property.</span></span> <span data-ttu-id="e9211-108">Dans l’exemple ci-dessous, cette partie de l’animation commence lentement mais vers la fin du segment de temps, accélère de façon exponentielle.</span><span class="sxs-lookup"><span data-stu-id="e9211-108">In the example below, this part of the animation starts off slow but toward the end of the time segment, speeds up exponentially.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e9211-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="e9211-109">Example</span></span>  
 [!code-xaml[Animation3DGallery_snip#Rotation3DAnimationUsingKeyFramesExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Rotation3DAnimationUsingKeyFramesExample.xaml#rotation3danimationusingkeyframesexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="e9211-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e9211-110">See also</span></span>

- [<span data-ttu-id="e9211-111">Aperçu graphique 3D</span><span class="sxs-lookup"><span data-stu-id="e9211-111">3D Graphics Overview</span></span>](3-d-graphics-overview.md)
- [<span data-ttu-id="e9211-112">Vue d'ensemble des animations d'image clé</span><span class="sxs-lookup"><span data-stu-id="e9211-112">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="e9211-113">Animer une rotation 3D à l’aide de storyboards</span><span class="sxs-lookup"><span data-stu-id="e9211-113">Animate a 3D Rotation Using Storyboards</span></span>](how-to-animate-a-3-d-rotation-using-storyboards.md)
- [<span data-ttu-id="e9211-114">Animer une rotation 3D à l’aide de Rotation3DAnimation</span><span class="sxs-lookup"><span data-stu-id="e9211-114">Animate a 3D Rotation Using Rotation3DAnimation</span></span>](how-to-animate-a-3-d-rotation-using-rotation3danimation.md)
- [<span data-ttu-id="e9211-115">Animer une rotation 3D à l’aide de quaternions</span><span class="sxs-lookup"><span data-stu-id="e9211-115">Animate a 3D Rotation Using Quaternions</span></span>](how-to-animate-a-3-d-rotation-using-quaternions.md)
- [<span data-ttu-id="e9211-116">Animez une rotation 3D à l’aide de cadres clés (QuaternionAnimationUsingKeyFrames)</span><span class="sxs-lookup"><span data-stu-id="e9211-116">Animate a 3D Rotation Using Key Frames (QuaternionAnimationUsingKeyFrames)</span></span>](animate-a-3-d-rotation-quaternionanimationusingkeyframes.md)
