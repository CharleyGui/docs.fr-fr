---
title: "Comment : animer la position et la direction d'une caméra dans une scène 3D"
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], camera position in 3D scenes
- camera direction [WPF], animating in 3D scenes
- 3D scenes [WPF], animating camera position
- 3D scenes [WPF], animating camera direction
- camera position [WPF], animating in 3D scenes
- animation [WPF], camera direction in 3D scenes
ms.assetid: 480224b7-a5e5-4165-ba7f-ef760ddff94a
ms.openlocfilehash: 5ce94e154cd5aa29b59260f893ec2b63a08db0fc
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112207"
---
# <a name="how-to-animate-camera-position-and-direction-in-a-3d-scene"></a><span data-ttu-id="08810-102">Comment : animer la position et la direction d'une caméra dans une scène 3D</span><span class="sxs-lookup"><span data-stu-id="08810-102">How to: Animate Camera Position and Direction in a 3D Scene</span></span>
<span data-ttu-id="08810-103">L’exemple suivant montre comment animer la position d’une caméra et animer la direction qu’elle pointe dans une scène 3D.</span><span class="sxs-lookup"><span data-stu-id="08810-103">The following example shows how to animate the position of a camera and animate the direction it is pointing in a 3D scene.</span></span> <span data-ttu-id="08810-104">Ceci est fait <xref:System.Windows.Media.Animation.Point3DAnimation> <xref:System.Windows.Media.Animation.Vector3DAnimation> en utilisant et <xref:System.Windows.Media.Media3D.ProjectionCamera.Position%2A> <xref:System.Windows.Media.Media3D.ProjectionCamera.LookDirection%2A> pour animer <xref:System.Windows.Media.Media3D.PerspectiveCamera>le et les propriétés respectivement de la .</span><span class="sxs-lookup"><span data-stu-id="08810-104">This is done by using <xref:System.Windows.Media.Animation.Point3DAnimation> and <xref:System.Windows.Media.Animation.Vector3DAnimation> to animate the <xref:System.Windows.Media.Media3D.ProjectionCamera.Position%2A> and <xref:System.Windows.Media.Media3D.ProjectionCamera.LookDirection%2A> properties respectively of the <xref:System.Windows.Media.Media3D.PerspectiveCamera>.</span></span> <span data-ttu-id="08810-105">Vous pouvez utiliser une animation comme celle-ci pour changer la vue du spectateur d’une scène en réponse à un événement.</span><span class="sxs-lookup"><span data-stu-id="08810-105">You might use an animation like this to change the onlooker's view of a scene in response to an event.</span></span>  
  
## <a name="example"></a><span data-ttu-id="08810-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="08810-106">Example</span></span>  
 [!code-xaml[Animation3DGallery_snip#PointVector3DAnimationExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/PointVector3DAnimationExample.xaml#pointvector3danimationexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="08810-107">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="08810-107">See also</span></span>

- <xref:System.Windows.Media.Animation.Vector3DAnimation>
- <xref:System.Windows.Media.Animation.Point3DAnimation>
- [<span data-ttu-id="08810-108">Animer la position et la direction de la caméra à l’aide d’images clés</span><span class="sxs-lookup"><span data-stu-id="08810-108">Animate Camera Position and Direction Using Key Frames</span></span>](how-to-animate-camera-position-and-direction-using-key-frames.md)
- [<span data-ttu-id="08810-109">Aperçu graphique 3D</span><span class="sxs-lookup"><span data-stu-id="08810-109">3D Graphics Overview</span></span>](3-d-graphics-overview.md)
