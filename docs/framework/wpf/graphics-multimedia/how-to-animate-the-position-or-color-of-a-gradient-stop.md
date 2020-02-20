---
title: "Comment : animer la position ou la couleur d'un point de dégradé"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- position [WPF], animating
- animation [WPF], position of GradientStop objects
- GradientStop objects [WPF], animating color of
- colors [WPF], animating
- animation [WPF], color of GradientStop objects
- GradientStop objects [WPF], animating position of
ms.assetid: 6f5b8b47-6c32-4b8e-98ee-fdf6515ec843
ms.openlocfilehash: aeae33f5f3c8016808988f58d61969e9b6f05039
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452842"
---
# <a name="how-to-animate-the-position-or-color-of-a-gradient-stop"></a><span data-ttu-id="96953-102">Comment : animer la position ou la couleur d'un point de dégradé</span><span class="sxs-lookup"><span data-stu-id="96953-102">How to: Animate the Position or Color of a Gradient Stop</span></span>
<span data-ttu-id="96953-103">Cet exemple montre comment animer les <xref:System.Windows.Media.GradientStop.Color%2A> et les <xref:System.Windows.Media.GradientStop.Offset%2A> d’objets <xref:System.Windows.Media.GradientStop>.</span><span class="sxs-lookup"><span data-stu-id="96953-103">This example shows how to animate the <xref:System.Windows.Media.GradientStop.Color%2A> and <xref:System.Windows.Media.GradientStop.Offset%2A> of <xref:System.Windows.Media.GradientStop> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="96953-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="96953-104">Example</span></span>  
 <span data-ttu-id="96953-105">L’exemple suivant anime trois points de dégradé à l’intérieur d’un <xref:System.Windows.Media.LinearGradientBrush>.</span><span class="sxs-lookup"><span data-stu-id="96953-105">The following example animates three gradient stops inside a <xref:System.Windows.Media.LinearGradientBrush>.</span></span> <span data-ttu-id="96953-106">L’exemple utilise trois animations, chacune qui anime un point de dégradé différent :</span><span class="sxs-lookup"><span data-stu-id="96953-106">The example uses three animations, each of which animates a different gradient stop:</span></span>  
  
- <span data-ttu-id="96953-107">La première animation, un <xref:System.Windows.Media.Animation.DoubleAnimation>, anime le <xref:System.Windows.Media.GradientStop.Offset%2A> du premier point de dégradé de 0,0 à 1,0, puis revient à 0,0.</span><span class="sxs-lookup"><span data-stu-id="96953-107">The first animation, a <xref:System.Windows.Media.Animation.DoubleAnimation>, animates the first gradient stop's <xref:System.Windows.Media.GradientStop.Offset%2A> from 0.0 to 1.0 and then back to 0.0.</span></span> <span data-ttu-id="96953-108">Par conséquent, la première couleur du dégradé se déplace du côté gauche vers le côté droit du rectangle, puis de nouveau vers le côté gauche.</span><span class="sxs-lookup"><span data-stu-id="96953-108">As a result, the first color in the gradient shifts from the left side to the right side of the rectangle and then back to the left side.</span></span>  
  
- <span data-ttu-id="96953-109">La deuxième animation, un <xref:System.Windows.Media.Animation.ColorAnimation>, anime le <xref:System.Windows.Media.GradientStop.Color%2A> du deuxième point de dégradé de <xref:System.Windows.Media.Colors.Purple%2A> à <xref:System.Windows.Media.Colors.Yellow%2A> puis revient à <xref:System.Windows.Media.Colors.Purple%2A>.</span><span class="sxs-lookup"><span data-stu-id="96953-109">The second animation, a <xref:System.Windows.Media.Animation.ColorAnimation>, animates the second gradient stop's <xref:System.Windows.Media.GradientStop.Color%2A> from <xref:System.Windows.Media.Colors.Purple%2A> to <xref:System.Windows.Media.Colors.Yellow%2A> and then back to <xref:System.Windows.Media.Colors.Purple%2A>.</span></span> <span data-ttu-id="96953-110">Par conséquent, la couleur intermédiaire du dégradé passe du violet au jaune, puis à la couleur violette.</span><span class="sxs-lookup"><span data-stu-id="96953-110">As a result, the middle color in the gradient changes from purple to yellow and back to purple.</span></span>  
  
- <span data-ttu-id="96953-111">La troisième animation, une autre <xref:System.Windows.Media.Animation.ColorAnimation>, anime l’opacité du troisième point de dégradé <xref:System.Windows.Media.GradientStop.Color%2A> de-1, puis de nouveau.</span><span class="sxs-lookup"><span data-stu-id="96953-111">The third animation, another <xref:System.Windows.Media.Animation.ColorAnimation>, animates the opacity of the third gradient stop's <xref:System.Windows.Media.GradientStop.Color%2A> by -1 and then back.</span></span> <span data-ttu-id="96953-112">En conséquence, la troisième couleur du dégradé disparaît, puis redevient opaque.</span><span class="sxs-lookup"><span data-stu-id="96953-112">As a result, the third color in the gradient fades away and then becomes opaque again.</span></span>  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMGradientAnimationExamplesWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/GradientStopAnimationExample.cs#graphicsmmgradientanimationexampleswholepage)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMGradientAnimationExamplesWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/gradientstopanimationexample.vb#graphicsmmgradientanimationexampleswholepage)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMGradientAnimationExamplesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/GradientStopAnimationExample.xaml#graphicsmmgradientanimationexampleswholepage)]  
  
 <span data-ttu-id="96953-113">Bien que cet exemple utilise un <xref:System.Windows.Media.LinearGradientBrush>, le processus est le même pour animer des objets <xref:System.Windows.Media.GradientStop> à l’intérieur d’un <xref:System.Windows.Media.RadialGradientBrush>.</span><span class="sxs-lookup"><span data-stu-id="96953-113">Although this example uses a <xref:System.Windows.Media.LinearGradientBrush>, the process is the same for animating <xref:System.Windows.Media.GradientStop> objects inside a <xref:System.Windows.Media.RadialGradientBrush>.</span></span>  
  
 <span data-ttu-id="96953-114">Pour obtenir des exemples supplémentaires, consultez l' [exemple pinceaux](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes).</span><span class="sxs-lookup"><span data-stu-id="96953-114">For additional examples, see the [Brushes Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96953-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="96953-115">See also</span></span>

- <xref:System.Windows.Media.GradientStop>
- [<span data-ttu-id="96953-116">Vue d’ensemble de l’animation</span><span class="sxs-lookup"><span data-stu-id="96953-116">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="96953-117">Vue d'ensemble des storyboards</span><span class="sxs-lookup"><span data-stu-id="96953-117">Storyboards Overview</span></span>](storyboards-overview.md)
