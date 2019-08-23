---
title: 'Procédure : Animer une matrice à l’aide d’images clés'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], Matrix properties with key frames
- Matrix properties [WPF], animating with key frames
- key frames [WPF], animating Matrix properties with
ms.assetid: b851a4c7-ecb1-420e-9203-83e7afd037fd
ms.openlocfilehash: 6aa3e27cdfda7597c9b6acbf2980a2774f2b667b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963026"
---
# <a name="how-to-animate-a-matrix-by-using-key-frames"></a><span data-ttu-id="62d31-102">Procédure : Animer une matrice à l’aide d’images clés</span><span class="sxs-lookup"><span data-stu-id="62d31-102">How to: Animate a Matrix by Using Key Frames</span></span>
<span data-ttu-id="62d31-103">Cet exemple montre comment animer la <xref:System.Windows.Media.MatrixTransform.Matrix%2A> propriété d’un <xref:System.Windows.Media.MatrixTransform> à l’aide d’images clés.</span><span class="sxs-lookup"><span data-stu-id="62d31-103">This example shows how to animate the <xref:System.Windows.Media.MatrixTransform.Matrix%2A> property of a <xref:System.Windows.Media.MatrixTransform> by using key frames.</span></span>  
  
## <a name="example"></a><span data-ttu-id="62d31-104">Exemples</span><span class="sxs-lookup"><span data-stu-id="62d31-104">Example</span></span>  
 <span data-ttu-id="62d31-105">L’exemple suivant utilise la <xref:System.Windows.Media.Animation.MatrixAnimationUsingKeyFrames> classe pour animer <xref:System.Windows.Media.MatrixTransform.Matrix%2A> la propriété d' <xref:System.Windows.Media.MatrixTransform>un.</span><span class="sxs-lookup"><span data-stu-id="62d31-105">The following example uses the <xref:System.Windows.Media.Animation.MatrixAnimationUsingKeyFrames> class to animate the <xref:System.Windows.Media.MatrixTransform.Matrix%2A> property of a <xref:System.Windows.Media.MatrixTransform>.</span></span> <span data-ttu-id="62d31-106">L’exemple utilise l' <xref:System.Windows.Media.MatrixTransform> objet pour transformer l’apparence et la position d' <xref:System.Windows.Controls.Button>un.</span><span class="sxs-lookup"><span data-stu-id="62d31-106">The example uses the <xref:System.Windows.Media.MatrixTransform> object to transform the appearance and position of a <xref:System.Windows.Controls.Button>.</span></span>  
  
 <span data-ttu-id="62d31-107">Cette animation utilise la <xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame> classe pour créer deux images clés et effectue les opérations suivantes:</span><span class="sxs-lookup"><span data-stu-id="62d31-107">This animation uses the <xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame> class to create two key frames and does the following with them:</span></span>  
  
1. <span data-ttu-id="62d31-108">Anime le premier <xref:System.Windows.Media.Matrix> pendant les 0,2 premières secondes.</span><span class="sxs-lookup"><span data-stu-id="62d31-108">Animates the first <xref:System.Windows.Media.Matrix> during the first 0.2 seconds.</span></span> <span data-ttu-id="62d31-109">L’exemple modifie les <xref:System.Windows.Media.Matrix.M11%2A> propriétés <xref:System.Windows.Media.Matrix.M12%2A> et de <xref:System.Windows.Media.Matrix>.</span><span class="sxs-lookup"><span data-stu-id="62d31-109">The example changes the <xref:System.Windows.Media.Matrix.M11%2A> and <xref:System.Windows.Media.Matrix.M12%2A> properties of the <xref:System.Windows.Media.Matrix>.</span></span> <span data-ttu-id="62d31-110">Cette modification entraîne l’étirement et l’inclinaison du bouton.</span><span class="sxs-lookup"><span data-stu-id="62d31-110">This change causes the button to stretch and become skewed.</span></span> <span data-ttu-id="62d31-111">L’exemple modifie également les <xref:System.Windows.Media.Matrix.OffsetX%2A> propriétés <xref:System.Windows.Media.Matrix.OffsetY%2A> et afin que le bouton change de position.</span><span class="sxs-lookup"><span data-stu-id="62d31-111">The example also changes the <xref:System.Windows.Media.Matrix.OffsetX%2A> and <xref:System.Windows.Media.Matrix.OffsetY%2A> properties so that the button changes position.</span></span>  
  
2. <span data-ttu-id="62d31-112">Anime la seconde <xref:System.Windows.Media.Matrix> à 1,0 secondes.</span><span class="sxs-lookup"><span data-stu-id="62d31-112">Animates the second <xref:System.Windows.Media.Matrix> at 1.0 seconds.</span></span> <span data-ttu-id="62d31-113">Le bouton se déplace vers une autre position lorsque le bouton n’est plus incliné ou étiré.</span><span class="sxs-lookup"><span data-stu-id="62d31-113">The button moves to another position while the button is no longer skewed or stretched.</span></span>  
  
3. <span data-ttu-id="62d31-114">Répète l’animation indéfiniment.</span><span class="sxs-lookup"><span data-stu-id="62d31-114">Repeats the animation indefinitely.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="62d31-115">Les images clés qui dérivent de l' <xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame> objet créent des sauts soudains entre les valeurs, autrement dit, le mouvement de l’animation est saccadé.</span><span class="sxs-lookup"><span data-stu-id="62d31-115">Key frames that derive from the <xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame> object create sudden jumps between values, that is, the movement of the animation is jerky.</span></span>  
  
 [!code-xaml[keyframes_snip#MatrixAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/MatrixAnimationUsingKeyFramesExample.xaml#matrixanimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="62d31-116">Pour l’exemple complet, consultez la page [Animation d’image clé, exemple](https://go.microsoft.com/fwlink/?LinkID=160012).</span><span class="sxs-lookup"><span data-stu-id="62d31-116">For the complete sample, see [KeyFrame Animation Sample](https://go.microsoft.com/fwlink/?LinkID=160012).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62d31-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="62d31-117">See also</span></span>

- <xref:System.Windows.Media.MatrixTransform.Matrix%2A>
- <xref:System.Windows.Media.MatrixTransform>
- [<span data-ttu-id="62d31-118">Vue d'ensemble des animations d'image clé</span><span class="sxs-lookup"><span data-stu-id="62d31-118">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="62d31-119">Guides pratiques relatifs aux images clés</span><span class="sxs-lookup"><span data-stu-id="62d31-119">Key-Frame How-to Topics</span></span>](key-frame-animation-how-to-topics.md)
