---
title: 'Comment : Animer une rotation 3D à l’aide de quaternions'
ms.date: 03/30/2017
helpviewer_keywords:
- quaternions [WPF]
- animation [WPF], 3D translations [WPF], with quaternions
- 3D translations [WPF], animating [WPF], with quaternions
ms.assetid: adca9cb1-066b-4de8-abbb-6b4007579ee7
ms.openlocfilehash: 0d229b0a714cc53459943fae751ab4d4f787d7d8
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112243"
---
# <a name="how-to-animate-a-3d-rotation-using-quaternions"></a><span data-ttu-id="d8e06-102">Comment : Animer une rotation 3D à l’aide de quaternions</span><span class="sxs-lookup"><span data-stu-id="d8e06-102">How to: Animate a 3D Rotation Using Quaternions</span></span>
<span data-ttu-id="d8e06-103">Cet exemple montre comment animer une rotation d’un objet 3D à l’aide de quaternions.</span><span class="sxs-lookup"><span data-stu-id="d8e06-103">This example shows how to animate a rotation of a 3D object using quaternions.</span></span>  
  
 <span data-ttu-id="d8e06-104">Le code ci-dessous montre <xref:System.Windows.Media.Media3D.QuaternionRotation3D> une <xref:System.Windows.Media.Media3D.RotateTransform3D.Rotation%2A> utilisation <xref:System.Windows.Media.Media3D.RotateTransform3D>comme valeur pour la propriété d’un .</span><span class="sxs-lookup"><span data-stu-id="d8e06-104">The code below shows a <xref:System.Windows.Media.Media3D.QuaternionRotation3D> used as the value for the <xref:System.Windows.Media.Media3D.RotateTransform3D.Rotation%2A> property of a <xref:System.Windows.Media.Media3D.RotateTransform3D>.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#QuaternionAnimationExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/QuaternionAnimationExample.xaml#quaternionanimationexampleinline1)]  
  
 <span data-ttu-id="d8e06-105">Ceci <xref:System.Windows.Media.Media3D.QuaternionRotation3D> est animé <xref:System.Windows.Media.Animation.QuaternionAnimation> avec <xref:System.Windows.Media.Animation.Storyboard> un dans un en utilisant le code ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="d8e06-105">This <xref:System.Windows.Media.Media3D.QuaternionRotation3D> is animated with a <xref:System.Windows.Media.Animation.QuaternionAnimation> within a <xref:System.Windows.Media.Animation.Storyboard> using the code below.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#QuaternionAnimationExampleInline2](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/QuaternionAnimationExample.xaml#quaternionanimationexampleinline2)]  
  
## <a name="example"></a><span data-ttu-id="d8e06-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="d8e06-106">Example</span></span>  
 <span data-ttu-id="d8e06-107">Le code suivant affiche l’échantillon entier.</span><span class="sxs-lookup"><span data-stu-id="d8e06-107">The following code shows the entire sample.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#QuaternionAnimationExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/QuaternionAnimationExample.xaml#quaternionanimationexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="d8e06-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d8e06-108">See also</span></span>

- [<span data-ttu-id="d8e06-109">Vue d’ensemble de l’animation</span><span class="sxs-lookup"><span data-stu-id="d8e06-109">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="d8e06-110">Créer une scène 3D</span><span class="sxs-lookup"><span data-stu-id="d8e06-110">Create a 3D Scene</span></span>](how-to-create-a-3-d-scene.md)
- [<span data-ttu-id="d8e06-111">Aperçu graphique 3D</span><span class="sxs-lookup"><span data-stu-id="d8e06-111">3D Graphics Overview</span></span>](3-d-graphics-overview.md)
- [<span data-ttu-id="d8e06-112">Vue d'ensemble des transformations</span><span class="sxs-lookup"><span data-stu-id="d8e06-112">Transforms Overview</span></span>](transforms-overview.md)
- [<span data-ttu-id="d8e06-113">Animer une rotation 3D à l’aide de storyboards</span><span class="sxs-lookup"><span data-stu-id="d8e06-113">Animate a 3D Rotation Using Storyboards</span></span>](how-to-animate-a-3-d-rotation-using-storyboards.md)
- [<span data-ttu-id="d8e06-114">Animer une rotation 3D à l’aide de Rotation3DAnimation</span><span class="sxs-lookup"><span data-stu-id="d8e06-114">Animate a 3D Rotation Using Rotation3DAnimation</span></span>](how-to-animate-a-3-d-rotation-using-rotation3danimation.md)
