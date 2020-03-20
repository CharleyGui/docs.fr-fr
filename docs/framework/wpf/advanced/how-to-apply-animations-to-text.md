---
title: 'Comment : appliquer des animations à du texte'
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], animations
- animation [WPF], text
ms.assetid: eec3d26c-0a21-420f-8012-671621c47089
ms.openlocfilehash: ed2f3beb904f724ac93e2c4033aa6b2eb3fa1290
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174626"
---
# <a name="how-to-apply-animations-to-text"></a><span data-ttu-id="d44e0-102">Comment : appliquer des animations à du texte</span><span class="sxs-lookup"><span data-stu-id="d44e0-102">How to: Apply Animations to Text</span></span>
<span data-ttu-id="d44e0-103">Les animations peuvent modifier l’affichage et l’apparence du texte dans votre application.</span><span class="sxs-lookup"><span data-stu-id="d44e0-103">Animations can alter the display and appearance of text in your application.</span></span> <span data-ttu-id="d44e0-104">Les exemples suivants utilisent différents types d’animations <xref:System.Windows.Controls.TextBlock> pour affecter l’affichage du texte dans un contrôle.</span><span class="sxs-lookup"><span data-stu-id="d44e0-104">The following examples use different types of animations to affect the display of text in a <xref:System.Windows.Controls.TextBlock> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d44e0-105"> Exemple</span><span class="sxs-lookup"><span data-stu-id="d44e0-105">Example</span></span>  
 <span data-ttu-id="d44e0-106">L’exemple suivant <xref:System.Windows.Media.Animation.DoubleAnimation> utilise un pour animer la largeur du bloc de texte.</span><span class="sxs-lookup"><span data-stu-id="d44e0-106">The following example uses a <xref:System.Windows.Media.Animation.DoubleAnimation> to animate the width of the text block.</span></span> <span data-ttu-id="d44e0-107">La valeur de largeur change pour passer de la largeur du bloc de texte à 0 sur une durée de 10 secondes, puis les valeurs de largeur sont inversées et la procédure continue.</span><span class="sxs-lookup"><span data-stu-id="d44e0-107">The width value changes from the width of the text block to 0 over a duration of 10 seconds, and then reverses the width values and continues.</span></span> <span data-ttu-id="d44e0-108">Ce type d’animation crée un effet de balayage.</span><span class="sxs-lookup"><span data-stu-id="d44e0-108">This type of animation creates a wipe effect.</span></span>  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample1](~/samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample1)]  
  
 <span data-ttu-id="d44e0-109">L’exemple suivant <xref:System.Windows.Media.Animation.DoubleAnimation> utilise un pour animer l’opacité du bloc de texte.</span><span class="sxs-lookup"><span data-stu-id="d44e0-109">The following example uses a <xref:System.Windows.Media.Animation.DoubleAnimation> to animate the opacity of the text block.</span></span> <span data-ttu-id="d44e0-110">La valeur d’opacité passe de 1.0 à 0 sur une durée de 5 secondes, puis les valeurs d’opacité sont inversées et la procédure continue.</span><span class="sxs-lookup"><span data-stu-id="d44e0-110">The opacity value changes from 1.0 to 0 over a duration of 5 seconds, and then reverses the opacity values and continues.</span></span>  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample2)]  
  
 <span data-ttu-id="d44e0-111">Le diagramme suivant montre <xref:System.Windows.Controls.TextBlock> l’effet du contrôle `1.00` `0.00` changeant son opacité de <xref:System.Windows.Media.Animation.Timeline.Duration%2A>à l’intervalle de 5 secondes défini par le .</span><span class="sxs-lookup"><span data-stu-id="d44e0-111">The following diagram shows the effect of the <xref:System.Windows.Controls.TextBlock> control changing its opacity from `1.00` to `0.00` during the 5-second interval defined by the <xref:System.Windows.Media.Animation.Timeline.Duration%2A>.</span></span>  
  
 ![Opacité changeant de texte de 1.00 à 0.00.](./media/how-to-apply-animations-to-text/faded-text-opacity-change.png)  

 <span data-ttu-id="d44e0-113">L’exemple suivant <xref:System.Windows.Media.Animation.ColorAnimation> utilise un pour animer la couleur de premier plan du bloc de texte.</span><span class="sxs-lookup"><span data-stu-id="d44e0-113">The following example uses a <xref:System.Windows.Media.Animation.ColorAnimation> to animate the foreground color of the text block.</span></span> <span data-ttu-id="d44e0-114">La valeur de la couleur de premier plan passe d’une couleur à une autre sur une durée de 5 secondes, puis les valeurs de couleur sont inversées et la procédure continue.</span><span class="sxs-lookup"><span data-stu-id="d44e0-114">The foreground color value changes from one color to a second color over a duration of 5 seconds, and then reverses the color values and continues.</span></span>  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample3](~/samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample3)]  
  
 <span data-ttu-id="d44e0-115">L’exemple suivant <xref:System.Windows.Media.Animation.DoubleAnimation> utilise un pour faire pivoter le bloc de texte.</span><span class="sxs-lookup"><span data-stu-id="d44e0-115">The following example uses a <xref:System.Windows.Media.Animation.DoubleAnimation> to rotate the text block.</span></span> <span data-ttu-id="d44e0-116">Le bloc de texte effectue une rotation complète sur une durée de 20 secondes, puis la procédure de rotation se répète.</span><span class="sxs-lookup"><span data-stu-id="d44e0-116">The text block performs a full rotation over a duration of 20 seconds, and then continues to repeat the rotation.</span></span>  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample4](~/samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample4)]  
  
## <a name="see-also"></a><span data-ttu-id="d44e0-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d44e0-117">See also</span></span>

- [<span data-ttu-id="d44e0-118">Vue d’ensemble de l’animation</span><span class="sxs-lookup"><span data-stu-id="d44e0-118">Animation Overview</span></span>](../graphics-multimedia/animation-overview.md)
