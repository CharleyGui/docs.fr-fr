---
title: 'Procédure : Définir une propriété après l’avoir animée avec une table de montage séquentiel'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], changing property values after
ms.assetid: 79466556-4dbf-40bd-9c1e-a77613b07077
ms.openlocfilehash: 593d3fcefe3bb81518d0886afde82f9a172874ba
ms.sourcegitcommit: e08b319358a8025cc6aa38737854f7bdb87183d6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/29/2019
ms.locfileid: "64912383"
---
# <a name="how-to-set-a-property-after-animating-it-with-a-storyboard"></a><span data-ttu-id="2d1a1-102">Procédure : Définir une propriété après l’avoir animée avec une table de montage séquentiel</span><span class="sxs-lookup"><span data-stu-id="2d1a1-102">How to: Set a Property After Animating It with a Storyboard</span></span>
<span data-ttu-id="2d1a1-103">Dans certains cas, il peut sembler que vous ne pouvez pas modifier la valeur d’une propriété après que qu’elle a été animée.</span><span class="sxs-lookup"><span data-stu-id="2d1a1-103">In some cases, it might appear that you can't change the value of a property after it has been animated.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2d1a1-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="2d1a1-104">Example</span></span>  
 <span data-ttu-id="2d1a1-105">Dans l’exemple suivant, un <xref:System.Windows.Media.Animation.Storyboard> est utilisé pour animer la couleur d’un <xref:System.Windows.Media.SolidColorBrush>.</span><span class="sxs-lookup"><span data-stu-id="2d1a1-105">In the following example, a <xref:System.Windows.Media.Animation.Storyboard> is used to animate the color of a <xref:System.Windows.Media.SolidColorBrush>.</span></span> <span data-ttu-id="2d1a1-106">La table de montage séquentiel est déclenchée lorsque le bouton est activé.</span><span class="sxs-lookup"><span data-stu-id="2d1a1-106">The storyboard is triggered when the button is clicked.</span></span> <span data-ttu-id="2d1a1-107">Le <xref:System.Windows.Media.Animation.Timeline.Completed> événement est géré afin que le programme est informé lorsque le <xref:System.Windows.Media.Animation.ColorAnimation> se termine.</span><span class="sxs-lookup"><span data-stu-id="2d1a1-107">The <xref:System.Windows.Media.Animation.Timeline.Completed> event is handled so that the program is notified when the <xref:System.Windows.Media.Animation.ColorAnimation> completes.</span></span>  
  
 [!code-xaml[timingbehaviors_snip#GraphicsMMButton1Declaration](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml#graphicsmmbutton1declaration)]  
  
## <a name="example"></a><span data-ttu-id="2d1a1-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="2d1a1-108">Example</span></span>  
 <span data-ttu-id="2d1a1-109">Une fois la <xref:System.Windows.Media.Animation.ColorAnimation> terminée, le programme tente de modifier la couleur du pinceau en bleu.</span><span class="sxs-lookup"><span data-stu-id="2d1a1-109">After the <xref:System.Windows.Media.Animation.ColorAnimation> completes, the program attempts to change the brush's color to blue.</span></span>  
  
 [!code-csharp[timingbehaviors_snip#GraphicsMMButton1Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml.cs#graphicsmmbutton1handler)]
 [!code-vb[timingbehaviors_snip#GraphicsMMButton1Handler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_snip/visualbasic/animatethensetpropertyexample.xaml.vb#graphicsmmbutton1handler)]  
  
 <span data-ttu-id="2d1a1-110">Le code précédent ne semble pas faire quelque chose : le pinceau reste jaune, qui est la valeur fournie par le <xref:System.Windows.Media.Animation.ColorAnimation> qui anime le pinceau.</span><span class="sxs-lookup"><span data-stu-id="2d1a1-110">The previous code doesn't appear to do anything: the brush remains yellow, which is the value supplied by the <xref:System.Windows.Media.Animation.ColorAnimation> that animated the brush.</span></span> <span data-ttu-id="2d1a1-111">La valeur de propriété sous-jacente (la valeur de base) est réellement modifiée bleu.</span><span class="sxs-lookup"><span data-stu-id="2d1a1-111">The underlying property value (the base value) is actually changed to blue.</span></span> <span data-ttu-id="2d1a1-112">Toutefois, la valeur effective, ou actuelle, reste jaune, car le <xref:System.Windows.Media.Animation.ColorAnimation> remplace toujours la valeur de base.</span><span class="sxs-lookup"><span data-stu-id="2d1a1-112">However, the effective, or current, value remains yellow because the <xref:System.Windows.Media.Animation.ColorAnimation> is still overriding the base value.</span></span> <span data-ttu-id="2d1a1-113">Si vous souhaitez que la valeur de base soit à la valeur effective nouveau, vous devez arrêter l’animation d’influencer la propriété.</span><span class="sxs-lookup"><span data-stu-id="2d1a1-113">If you want the base value to become the effective value again, you must stop the animation from influencing the property.</span></span> <span data-ttu-id="2d1a1-114">Il existe trois façons de le faire avec des animations de storyboard :</span><span class="sxs-lookup"><span data-stu-id="2d1a1-114">There are three ways to do this with storyboard animations:</span></span>  
  
- <span data-ttu-id="2d1a1-115">Définir l’animation <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> propriété <xref:System.Windows.Media.Animation.FillBehavior.Stop></span><span class="sxs-lookup"><span data-stu-id="2d1a1-115">Set the animation's <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> property to <xref:System.Windows.Media.Animation.FillBehavior.Stop></span></span>  
  
- <span data-ttu-id="2d1a1-116">Supprimer l’ensemble du Storyboard.</span><span class="sxs-lookup"><span data-stu-id="2d1a1-116">Remove the entire Storyboard.</span></span>  
  
- <span data-ttu-id="2d1a1-117">Supprimez l’animation de la propriété individuelle.</span><span class="sxs-lookup"><span data-stu-id="2d1a1-117">Remove the animation from the individual property.</span></span>  
  
## <a name="set-the-animations-fillbehavior-property-to-stop"></a><span data-ttu-id="2d1a1-118">FillBehavior (propriété) de l’animation la valeur Stop</span><span class="sxs-lookup"><span data-stu-id="2d1a1-118">Set the animation's FillBehavior property to Stop</span></span>  
 <span data-ttu-id="2d1a1-119">En définissant <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> à <xref:System.Windows.Media.Animation.FillBehavior.Stop>, vous dites à l’animation de cesser d’affecter sa propriété cible après avoir atteint la fin de sa période active.</span><span class="sxs-lookup"><span data-stu-id="2d1a1-119">By setting <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> to <xref:System.Windows.Media.Animation.FillBehavior.Stop>, you tell the animation to stop affecting its target property after it reaches the end of its active period.</span></span>  
  
 [!code-xaml[timingbehaviors_snip#GraphicsMMButton2Declaration](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml#graphicsmmbutton2declaration)]  
  
 [!code-csharp[timingbehaviors_snip#GraphicsMMButton2Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml.cs#graphicsmmbutton2handler)]
 [!code-vb[timingbehaviors_snip#GraphicsMMButton2Handler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_snip/visualbasic/animatethensetpropertyexample.xaml.vb#graphicsmmbutton2handler)]  
  
## <a name="remove-the-entire-storyboard"></a><span data-ttu-id="2d1a1-120">Supprimer l’ensemble du storyboard</span><span class="sxs-lookup"><span data-stu-id="2d1a1-120">Remove the entire storyboard</span></span>  
 <span data-ttu-id="2d1a1-121">En utilisant un <xref:System.Windows.Media.Animation.RemoveStoryboard> déclencheur ou la <xref:System.Windows.Media.Animation.Storyboard.Remove%2A?displayProperty=nameWithType> (méthode), que vous demandez aux animations de storyboard de cesser d’affecter leurs propriétés cibles.</span><span class="sxs-lookup"><span data-stu-id="2d1a1-121">By using a <xref:System.Windows.Media.Animation.RemoveStoryboard> trigger or the <xref:System.Windows.Media.Animation.Storyboard.Remove%2A?displayProperty=nameWithType> method, you tell the storyboard animations to stop affecting their target properties.</span></span> <span data-ttu-id="2d1a1-122">La différence entre cette approche et en définissant le <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> propriété est que vous pouvez supprimer la table de montage séquentiel à tout moment, tandis que le <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> propriété n’a d’effet que lorsque l’animation atteint la fin de sa période active.</span><span class="sxs-lookup"><span data-stu-id="2d1a1-122">The difference between this approach and setting the <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> property is that you can remove the storyboard at anytime, while the <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> property only has an effect when the animation reaches the end of its active period.</span></span>  
  
 [!code-xaml[timingbehaviors_snip#GraphicsMMButton3Declaration](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml#graphicsmmbutton3declaration)]  
  
 [!code-csharp[timingbehaviors_snip#GraphicsMMButton3Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml.cs#graphicsmmbutton3handler)]
 [!code-vb[timingbehaviors_snip#GraphicsMMButton3Handler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_snip/visualbasic/animatethensetpropertyexample.xaml.vb#graphicsmmbutton3handler)]  
  
## <a name="remove-an-animation-from-an-individual-property"></a><span data-ttu-id="2d1a1-123">Supprimer une animation d’une propriété individuelle</span><span class="sxs-lookup"><span data-stu-id="2d1a1-123">Remove an animation from an individual property</span></span>  
 <span data-ttu-id="2d1a1-124">Une autre technique pour empêcher une animation d’affecter une propriété consiste à utiliser le <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%28System.Windows.DependencyProperty%2CSystem.Windows.Media.Animation.AnimationTimeline%29> méthode de l’objet en cours d’animation.</span><span class="sxs-lookup"><span data-stu-id="2d1a1-124">Another technique to stop an animation from affecting a property is to use the <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%28System.Windows.DependencyProperty%2CSystem.Windows.Media.Animation.AnimationTimeline%29> method of the object being animated.</span></span> <span data-ttu-id="2d1a1-125">Spécifiez la propriété animée comme premier paramètre et `null` en tant que la seconde.</span><span class="sxs-lookup"><span data-stu-id="2d1a1-125">Specify the property being animated as the first parameter and `null` as the second.</span></span>  
  
 [!code-xaml[timingbehaviors_snip#GraphicsMMButton4Declaration](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml#graphicsmmbutton4declaration)]  
  
 [!code-csharp[timingbehaviors_snip#GraphicsMMButton4Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml.cs#graphicsmmbutton4handler)]
 [!code-vb[timingbehaviors_snip#GraphicsMMButton4Handler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_snip/visualbasic/animatethensetpropertyexample.xaml.vb#graphicsmmbutton4handler)]  
  
 <span data-ttu-id="2d1a1-126">Cette technique fonctionne également pour les animations table de montage séquentiel.</span><span class="sxs-lookup"><span data-stu-id="2d1a1-126">This technique also works for non-storyboard animations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d1a1-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2d1a1-127">See also</span></span>

- <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>
- <xref:System.Windows.Media.Animation.Storyboard.Remove%2A?displayProperty=nameWithType>
- <xref:System.Windows.Media.Animation.RemoveStoryboard>
- [<span data-ttu-id="2d1a1-128">Vue d’ensemble de l’animation</span><span class="sxs-lookup"><span data-stu-id="2d1a1-128">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="2d1a1-129">Vue d’ensemble des techniques d’animation de propriétés</span><span class="sxs-lookup"><span data-stu-id="2d1a1-129">Property Animation Techniques Overview</span></span>](property-animation-techniques-overview.md)
