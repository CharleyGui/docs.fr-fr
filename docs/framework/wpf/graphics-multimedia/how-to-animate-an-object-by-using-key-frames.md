---
title: 'Procédure : Animer un objet à l’aide d’images clés'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], objects with key frames
- key frames [WPF], animating objects with
ms.assetid: b1f15ba9-cac7-4cea-8699-5c6b55c05c5e
ms.openlocfilehash: ffbe1845b634c8f94eb6a10dfa44fcf9903e0cd5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933905"
---
# <a name="how-to-animate-an-object-by-using-key-frames"></a><span data-ttu-id="832f3-102">Procédure : Animer un objet à l’aide d’images clés</span><span class="sxs-lookup"><span data-stu-id="832f3-102">How to: Animate an Object by Using Key Frames</span></span>
<span data-ttu-id="832f3-103">Cet exemple montre comment animer un objet, qui, dans cet exemple, <xref:System.Windows.Controls.Page.Background%2A> est la propriété <xref:System.Windows.Controls.Page> d’un contrôle, à l’aide d’images clés.</span><span class="sxs-lookup"><span data-stu-id="832f3-103">This example shows how to animate an object, which in this example is the <xref:System.Windows.Controls.Page.Background%2A> property of a <xref:System.Windows.Controls.Page> control, by using key frames.</span></span>  
  
## <a name="example"></a><span data-ttu-id="832f3-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="832f3-104">Example</span></span>  
 <span data-ttu-id="832f3-105">L’exemple suivant utilise la <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> classe pour animer des modifications de <xref:System.Windows.Controls.Page.Background%2A> couleur pour la <xref:System.Windows.Controls.Page> propriété d’un contrôle.</span><span class="sxs-lookup"><span data-stu-id="832f3-105">The following example uses the <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> class to animate color changes for the <xref:System.Windows.Controls.Page.Background%2A> property of a <xref:System.Windows.Controls.Page> control.</span></span> <span data-ttu-id="832f3-106">L’exemple d’animation change en un pinceau d’arrière-plan différent à intervalles réguliers.</span><span class="sxs-lookup"><span data-stu-id="832f3-106">The example animation changes to a different background brush at regular intervals.</span></span> <span data-ttu-id="832f3-107">Cette animation utilise la <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> classe pour créer trois images clés différentes.</span><span class="sxs-lookup"><span data-stu-id="832f3-107">This animation uses the <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> class to create three different key frames.</span></span> <span data-ttu-id="832f3-108">L’animation utilise des images clés de la manière suivante:</span><span class="sxs-lookup"><span data-stu-id="832f3-108">The animation uses key frames in the following manner:</span></span>  
  
1. <span data-ttu-id="832f3-109">À la fin de la première seconde, anime une instance de la <xref:System.Windows.Media.LinearGradientBrush> classe.</span><span class="sxs-lookup"><span data-stu-id="832f3-109">At the end of the first second, animates an instance of the <xref:System.Windows.Media.LinearGradientBrush> class.</span></span> <span data-ttu-id="832f3-110">Cette section de l’exemple applique un dégradé linéaire à la couleur d’arrière-plan afin que la couleur passe du jaune au rouge.</span><span class="sxs-lookup"><span data-stu-id="832f3-110">This section of the example applies a linear gradient to the background color so that the color transitions from yellow to orange to red.</span></span>  
  
2. <span data-ttu-id="832f3-111">À la fin de la seconde suivante, anime une instance de la <xref:System.Windows.Media.RadialGradientBrush> classe.</span><span class="sxs-lookup"><span data-stu-id="832f3-111">At the end of the next second, animates an instance of the <xref:System.Windows.Media.RadialGradientBrush> class.</span></span> <span data-ttu-id="832f3-112">Cette section de l’exemple applique un dégradé radial à la couleur d’arrière-plan afin que la couleur passe du blanc au bleu et au noir.</span><span class="sxs-lookup"><span data-stu-id="832f3-112">This section of the example applies a radial gradient to the background color so that the color transitions from white to blue to black.</span></span>  
  
3. <span data-ttu-id="832f3-113">À la fin de la troisième seconde, anime une instance de la <xref:System.Windows.Media.DrawingBrush> classe.</span><span class="sxs-lookup"><span data-stu-id="832f3-113">At the end of the third second, animates an instance of the <xref:System.Windows.Media.DrawingBrush> class.</span></span> <span data-ttu-id="832f3-114">Cette section de l’exemple applique un modèle de damier à l’arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="832f3-114">This section of the example applies a checkerboard pattern to the background.</span></span>  
  
4. <span data-ttu-id="832f3-115">L’animation recommence et se répète indéfiniment.</span><span class="sxs-lookup"><span data-stu-id="832f3-115">The animation begins again and repeats indefinitely.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="832f3-116"><xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame>est le seul type d’image clé que vous pouvez utiliser avec la <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> classe.</span><span class="sxs-lookup"><span data-stu-id="832f3-116"><xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> is the only type of key frame that you can use with the <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> class.</span></span> <span data-ttu-id="832f3-117">Les images clés <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> telles que créent des changements soudains dans les valeurs, autrement dit, les modifications de couleur dans cet exemple se produisent soudainement.</span><span class="sxs-lookup"><span data-stu-id="832f3-117">Key frames like <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> create sudden changes in values, that is, the color changes in this example occur suddenly.</span></span>  
  
 [!code-xaml[keyframes_snip#ObjectAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/ObjectAnimationUsingKeyFramesExample.xaml#objectanimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="832f3-118">Pour l’exemple complet, consultez la page [Animation d’image clé, exemple](https://go.microsoft.com/fwlink/?LinkID=160012).</span><span class="sxs-lookup"><span data-stu-id="832f3-118">For the complete sample, see [KeyFrame Animation Sample](https://go.microsoft.com/fwlink/?LinkID=160012).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="832f3-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="832f3-119">See also</span></span>

- <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames>
- <xref:System.Windows.Controls.Page.Background%2A>
- <xref:System.Windows.Controls.Page>
- <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame>
- <xref:System.Windows.Media.LinearGradientBrush>
- <xref:System.Windows.Media.RadialGradientBrush>
- <xref:System.Windows.Media.DrawingBrush>
- [<span data-ttu-id="832f3-120">Vue d'ensemble des animations d'image clé</span><span class="sxs-lookup"><span data-stu-id="832f3-120">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="832f3-121">Guides pratiques relatifs aux images clés</span><span class="sxs-lookup"><span data-stu-id="832f3-121">Key-Frame How-to Topics</span></span>](key-frame-animation-how-to-topics.md)
