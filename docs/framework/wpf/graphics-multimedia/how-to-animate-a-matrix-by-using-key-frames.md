---
title: "Comment : animer une matrice à l'aide d'images clés"
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], Matrix properties with key frames
- Matrix properties [WPF], animating with key frames
- key frames [WPF], animating Matrix properties with
ms.assetid: b851a4c7-ecb1-420e-9203-83e7afd037fd
ms.openlocfilehash: eb596cf728f8a7cc1964963b8509f42bdd7a392a
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344916"
---
# <a name="how-to-animate-a-matrix-by-using-key-frames"></a><span data-ttu-id="e1498-102">Comment : animer une matrice à l'aide d'images clés</span><span class="sxs-lookup"><span data-stu-id="e1498-102">How to: Animate a Matrix by Using Key Frames</span></span>
<span data-ttu-id="e1498-103">Cet exemple montre comment animer <xref:System.Windows.Media.MatrixTransform.Matrix%2A> la <xref:System.Windows.Media.MatrixTransform> propriété d’un en utilisant des cadres clés.</span><span class="sxs-lookup"><span data-stu-id="e1498-103">This example shows how to animate the <xref:System.Windows.Media.MatrixTransform.Matrix%2A> property of a <xref:System.Windows.Media.MatrixTransform> by using key frames.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e1498-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="e1498-104">Example</span></span>  
 <span data-ttu-id="e1498-105">L’exemple suivant <xref:System.Windows.Media.Animation.MatrixAnimationUsingKeyFrames> utilise la classe <xref:System.Windows.Media.MatrixTransform.Matrix%2A> pour <xref:System.Windows.Media.MatrixTransform>animer la propriété d’un .</span><span class="sxs-lookup"><span data-stu-id="e1498-105">The following example uses the <xref:System.Windows.Media.Animation.MatrixAnimationUsingKeyFrames> class to animate the <xref:System.Windows.Media.MatrixTransform.Matrix%2A> property of a <xref:System.Windows.Media.MatrixTransform>.</span></span> <span data-ttu-id="e1498-106">L’exemple <xref:System.Windows.Media.MatrixTransform> utilise l’objet pour transformer <xref:System.Windows.Controls.Button>l’apparence et la position d’un .</span><span class="sxs-lookup"><span data-stu-id="e1498-106">The example uses the <xref:System.Windows.Media.MatrixTransform> object to transform the appearance and position of a <xref:System.Windows.Controls.Button>.</span></span>  
  
 <span data-ttu-id="e1498-107">Cette animation <xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame> utilise la classe pour créer deux cadres clés et fait ce qui suit avec eux:</span><span class="sxs-lookup"><span data-stu-id="e1498-107">This animation uses the <xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame> class to create two key frames and does the following with them:</span></span>  
  
1. <span data-ttu-id="e1498-108">Animates le <xref:System.Windows.Media.Matrix> premier au cours des 0,2 premières secondes.</span><span class="sxs-lookup"><span data-stu-id="e1498-108">Animates the first <xref:System.Windows.Media.Matrix> during the first 0.2 seconds.</span></span> <span data-ttu-id="e1498-109">L’exemple <xref:System.Windows.Media.Matrix.M11%2A> change <xref:System.Windows.Media.Matrix.M12%2A> le <xref:System.Windows.Media.Matrix>et les propriétés de la .</span><span class="sxs-lookup"><span data-stu-id="e1498-109">The example changes the <xref:System.Windows.Media.Matrix.M11%2A> and <xref:System.Windows.Media.Matrix.M12%2A> properties of the <xref:System.Windows.Media.Matrix>.</span></span> <span data-ttu-id="e1498-110">Ce changement provoque l’étirement du bouton et devient biaisé.</span><span class="sxs-lookup"><span data-stu-id="e1498-110">This change causes the button to stretch and become skewed.</span></span> <span data-ttu-id="e1498-111">L’exemple modifie <xref:System.Windows.Media.Matrix.OffsetX%2A> <xref:System.Windows.Media.Matrix.OffsetY%2A> également les propriétés et les propriétés de sorte que le bouton change de position.</span><span class="sxs-lookup"><span data-stu-id="e1498-111">The example also changes the <xref:System.Windows.Media.Matrix.OffsetX%2A> and <xref:System.Windows.Media.Matrix.OffsetY%2A> properties so that the button changes position.</span></span>  
  
2. <span data-ttu-id="e1498-112">Animates la <xref:System.Windows.Media.Matrix> seconde à 1,0 seconde.</span><span class="sxs-lookup"><span data-stu-id="e1498-112">Animates the second <xref:System.Windows.Media.Matrix> at 1.0 seconds.</span></span> <span data-ttu-id="e1498-113">Le bouton se déplace vers une autre position tandis que le bouton n’est plus biaisé ou étiré.</span><span class="sxs-lookup"><span data-stu-id="e1498-113">The button moves to another position while the button is no longer skewed or stretched.</span></span>  
  
3. <span data-ttu-id="e1498-114">Répète l’animation indéfiniment.</span><span class="sxs-lookup"><span data-stu-id="e1498-114">Repeats the animation indefinitely.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e1498-115">Les cadres clés qui <xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame> dérivent de l’objet créent des sauts soudains entre les valeurs, c’est-à-dire que le mouvement de l’animation est saccadédant.</span><span class="sxs-lookup"><span data-stu-id="e1498-115">Key frames that derive from the <xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame> object create sudden jumps between values, that is, the movement of the animation is jerky.</span></span>  
  
 [!code-xaml[keyframes_snip#MatrixAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/MatrixAnimationUsingKeyFramesExample.xaml#matrixanimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="e1498-116">Pour l’exemple complet, consultez la page [Animation d’image clé, exemple](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).</span><span class="sxs-lookup"><span data-stu-id="e1498-116">For the complete sample, see [KeyFrame Animation Sample](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1498-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e1498-117">See also</span></span>

- <xref:System.Windows.Media.MatrixTransform.Matrix%2A>
- <xref:System.Windows.Media.MatrixTransform>
- [<span data-ttu-id="e1498-118">Vue d'ensemble des animations d'image clé</span><span class="sxs-lookup"><span data-stu-id="e1498-118">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="e1498-119">Guides pratiques relatifs aux images clés</span><span class="sxs-lookup"><span data-stu-id="e1498-119">Key-Frame How-to Topics</span></span>](key-frame-animation-how-to-topics.md)
