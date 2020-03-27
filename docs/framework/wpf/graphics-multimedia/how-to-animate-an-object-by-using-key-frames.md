---
title: "Comment : animer un objet à l'aide d'images clés"
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], objects with key frames
- key frames [WPF], animating objects with
ms.assetid: b1f15ba9-cac7-4cea-8699-5c6b55c05c5e
ms.openlocfilehash: 0bc33b189fd856dbe8106c1db35bc18e27ea131e
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344704"
---
# <a name="how-to-animate-an-object-by-using-key-frames"></a><span data-ttu-id="0d486-102">Comment : animer un objet à l'aide d'images clés</span><span class="sxs-lookup"><span data-stu-id="0d486-102">How to: Animate an Object by Using Key Frames</span></span>
<span data-ttu-id="0d486-103">Cet exemple montre comment animer un objet, qui <xref:System.Windows.Controls.Page.Background%2A> dans <xref:System.Windows.Controls.Page> cet exemple est la propriété d’un contrôle, en utilisant des cadres clés.</span><span class="sxs-lookup"><span data-stu-id="0d486-103">This example shows how to animate an object, which in this example is the <xref:System.Windows.Controls.Page.Background%2A> property of a <xref:System.Windows.Controls.Page> control, by using key frames.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0d486-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="0d486-104">Example</span></span>  
 <span data-ttu-id="0d486-105">L’exemple suivant <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> utilise la classe pour <xref:System.Windows.Controls.Page.Background%2A> animer <xref:System.Windows.Controls.Page> les changements de couleur pour la propriété d’un contrôle.</span><span class="sxs-lookup"><span data-stu-id="0d486-105">The following example uses the <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> class to animate color changes for the <xref:System.Windows.Controls.Page.Background%2A> property of a <xref:System.Windows.Controls.Page> control.</span></span> <span data-ttu-id="0d486-106">L’exemple de l’animation change à un pinceau d’arrière-plan différent à intervalles réguliers.</span><span class="sxs-lookup"><span data-stu-id="0d486-106">The example animation changes to a different background brush at regular intervals.</span></span> <span data-ttu-id="0d486-107">Cette animation <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> utilise la classe pour créer trois cadres clés différents.</span><span class="sxs-lookup"><span data-stu-id="0d486-107">This animation uses the <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> class to create three different key frames.</span></span> <span data-ttu-id="0d486-108">L’animation utilise des cadres clés de la manière suivante :</span><span class="sxs-lookup"><span data-stu-id="0d486-108">The animation uses key frames in the following manner:</span></span>  
  
1. <span data-ttu-id="0d486-109">À la fin de la première seconde, <xref:System.Windows.Media.LinearGradientBrush> anime un exemple de la classe.</span><span class="sxs-lookup"><span data-stu-id="0d486-109">At the end of the first second, animates an instance of the <xref:System.Windows.Media.LinearGradientBrush> class.</span></span> <span data-ttu-id="0d486-110">Cette section de l’exemple applique un gradient linéaire à la couleur de fond de sorte que la couleur passe du jaune à l’orange au rouge.</span><span class="sxs-lookup"><span data-stu-id="0d486-110">This section of the example applies a linear gradient to the background color so that the color transitions from yellow to orange to red.</span></span>  
  
2. <span data-ttu-id="0d486-111">À la fin de la seconde suivante, <xref:System.Windows.Media.RadialGradientBrush> anime un exemple de la classe.</span><span class="sxs-lookup"><span data-stu-id="0d486-111">At the end of the next second, animates an instance of the <xref:System.Windows.Media.RadialGradientBrush> class.</span></span> <span data-ttu-id="0d486-112">Cette section de l’exemple applique un gradient radial à la couleur de fond de sorte que la couleur passe du blanc au bleu au noir.</span><span class="sxs-lookup"><span data-stu-id="0d486-112">This section of the example applies a radial gradient to the background color so that the color transitions from white to blue to black.</span></span>  
  
3. <span data-ttu-id="0d486-113">À la fin de la troisième seconde, <xref:System.Windows.Media.DrawingBrush> anime un exemple de la classe.</span><span class="sxs-lookup"><span data-stu-id="0d486-113">At the end of the third second, animates an instance of the <xref:System.Windows.Media.DrawingBrush> class.</span></span> <span data-ttu-id="0d486-114">Cette section de l’exemple applique un modèle de damier à l’arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="0d486-114">This section of the example applies a checkerboard pattern to the background.</span></span>  
  
4. <span data-ttu-id="0d486-115">L’animation recommence et se répète indéfiniment.</span><span class="sxs-lookup"><span data-stu-id="0d486-115">The animation begins again and repeats indefinitely.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0d486-116"><xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame>est le seul type de cadre clé <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> que vous pouvez utiliser avec la classe.</span><span class="sxs-lookup"><span data-stu-id="0d486-116"><xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> is the only type of key frame that you can use with the <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> class.</span></span> <span data-ttu-id="0d486-117">Les cadres <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> clés comme créer des changements soudains dans les valeurs, c’est-à-dire, les changements de couleur dans cet exemple se produisent soudainement.</span><span class="sxs-lookup"><span data-stu-id="0d486-117">Key frames like <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> create sudden changes in values, that is, the color changes in this example occur suddenly.</span></span>  
  
 [!code-xaml[keyframes_snip#ObjectAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/ObjectAnimationUsingKeyFramesExample.xaml#objectanimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="0d486-118">Pour l’exemple complet, consultez la page [Animation d’image clé, exemple](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).</span><span class="sxs-lookup"><span data-stu-id="0d486-118">For the complete sample, see [KeyFrame Animation Sample](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d486-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0d486-119">See also</span></span>

- <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames>
- <xref:System.Windows.Controls.Page.Background%2A>
- <xref:System.Windows.Controls.Page>
- <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame>
- <xref:System.Windows.Media.LinearGradientBrush>
- <xref:System.Windows.Media.RadialGradientBrush>
- <xref:System.Windows.Media.DrawingBrush>
- [<span data-ttu-id="0d486-120">Vue d'ensemble des animations d'image clé</span><span class="sxs-lookup"><span data-stu-id="0d486-120">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="0d486-121">Guides pratiques relatifs aux images clés</span><span class="sxs-lookup"><span data-stu-id="0d486-121">Key-Frame How-to Topics</span></span>](key-frame-animation-how-to-topics.md)
