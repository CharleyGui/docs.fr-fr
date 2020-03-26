---
title: 'Comment : Animer une rotation 3D à l’aide de storyboards'
ms.date: 03/30/2017
helpviewer_keywords:
- Storyboards [WPF]
- 3D translations [WPF], animating [WPF], with Storyboards
- animation [WPF], 3D translations [WPF], with Storyboards
ms.assetid: 1020e44e-e21e-49a8-be53-53cbc1910e83
ms.openlocfilehash: 088f1a33cfc73a706ffed55ffff6494adaf8fca4
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112210"
---
# <a name="how-to-animate-a-3d-rotation-using-storyboards"></a><span data-ttu-id="e63f4-102">Comment : Animer une rotation 3D à l’aide de storyboards</span><span class="sxs-lookup"><span data-stu-id="e63f4-102">How to: Animate a 3D Rotation Using Storyboards</span></span>
<span data-ttu-id="e63f4-103">L’exemple suivant montre comment faire pivoter un objet 3D pendant <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Angle%2A> qu’il « vacille » en animant les propriétés et <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Axis%2A> les propriétés d’un <xref:System.Windows.Media.Media3D.AxisAngleRotation3D> objet.</span><span class="sxs-lookup"><span data-stu-id="e63f4-103">The following example shows how to make a 3D object rotate while it "wobbles" by animating the <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Angle%2A> and <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Axis%2A> properties of an <xref:System.Windows.Media.Media3D.AxisAngleRotation3D> object.</span></span> <span data-ttu-id="e63f4-104">Cet <xref:System.Windows.Media.Media3D.AxisAngleRotation3D> objet spécifie la rotation de l’objet 3D et ainsi l’animation de ses propriétés crée l’effet de rotation de désir.</span><span class="sxs-lookup"><span data-stu-id="e63f4-104">This <xref:System.Windows.Media.Media3D.AxisAngleRotation3D> object specifies the rotation transform of the 3D object and so animating its properties creates the desire rotation effect.</span></span> <span data-ttu-id="e63f4-105">Dans le <xref:System.Windows.Media.Animation.DoubleAnimation> Storyboard, est utilisé <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Angle%2A> pour <xref:System.Windows.Media.Animation.Vector3DAnimation> animer la propriété <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Axis%2A> tout en étant utilisé pour animer la propriété.</span><span class="sxs-lookup"><span data-stu-id="e63f4-105">Within the Storyboard, <xref:System.Windows.Media.Animation.DoubleAnimation> is used to animate the <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Angle%2A> property while <xref:System.Windows.Media.Animation.Vector3DAnimation> is used to animate the <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Axis%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e63f4-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="e63f4-106">Example</span></span>  
 [!code-xaml[Animation3DGallery_snip#Rotate3DUsingAxisAngleRotation3DExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Rotat3DUsingAxisAngleRotation3DExample.xaml#rotate3dusingaxisanglerotation3dexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="e63f4-107">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e63f4-107">See also</span></span>

- [<span data-ttu-id="e63f4-108">Animer une rotation 3D à l’aide de Rotation3DAnimation</span><span class="sxs-lookup"><span data-stu-id="e63f4-108">Animate a 3D Rotation Using Rotation3DAnimation</span></span>](how-to-animate-a-3-d-rotation-using-rotation3danimation.md)
- [<span data-ttu-id="e63f4-109">Animez une rotation 3D à l’aide de cadres clés (Rotation3DAnimationUsingKeyFrames)</span><span class="sxs-lookup"><span data-stu-id="e63f4-109">Animate a 3D Rotation Using Key Frames (Rotation3DAnimationUsingKeyFrames)</span></span>](how-to-animate-a-3-d-rotation-using-key-frames.md)
- [<span data-ttu-id="e63f4-110">Aperçu graphique 3D</span><span class="sxs-lookup"><span data-stu-id="e63f4-110">3D Graphics Overview</span></span>](3-d-graphics-overview.md)
- [<span data-ttu-id="e63f4-111">Vue d'ensemble des plans conceptuels</span><span class="sxs-lookup"><span data-stu-id="e63f4-111">Storyboards Overview</span></span>](storyboards-overview.md)
