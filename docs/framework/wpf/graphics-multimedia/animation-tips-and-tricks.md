---
title: Conseils et astuces sur les animations
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- troubleshooting [WPF], animation
- animations [WPF], FillBehavior property
- troubleshooting animation [WPF]
- animating objects [WPF], troubleshooting
- animation tips and tricks [WPF]
- tips and tricks [WPF], animation
- performance troubleshooting [WPF], animation
- animations [WPF], use of system resources
ms.assetid: e467796b-d5d4-45a6-a108-8c5d7ff69a0f
ms.openlocfilehash: 6b540448599c1e1083ed367a312ef60fceacd0d5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187652"
---
# <a name="animation-tips-and-tricks"></a>Conseils et astuces sur les animations
Lorsque vous travaillez avec des animations dans WPF, il ya un certain nombre de trucs et astuces qui peuvent rendre vos animations plus performantes et vous faire économiser de la frustration.  
  
<a name="generalissuessection"></a>
## <a name="general-issues"></a>Problèmes généraux  
  
### <a name="animating-the-position-of-a-scroll-bar-or-slider-freezes-it"></a>L’animation de la position d’une barre de défilement ou d’un curseur bloque cet élément  
 Si vous animez la position d’une barre de défilement ou d’un curseur à l’aide d’une animation qui a une <xref:System.Windows.Media.Animation.FillBehavior> (valeur par défaut), l’utilisateur ne sera plus en mesure de <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd> déplacer la barre de défilement ou le curseur. Cela survient car l’animation, même si elle est terminée, remplace toujours la valeur de base de la propriété cible. Pour empêcher l’animation de dépasser la valeur actuelle de la <xref:System.Windows.Media.Animation.FillBehavior> propriété, l’enlever, ou lui donner un de <xref:System.Windows.Media.Animation.FillBehavior.Stop>. Pour plus d’informations et un exemple, voir [Set a Property After Animating It with a Storyboard](how-to-set-a-property-after-animating-it-with-a-storyboard.md).  
  
### <a name="animating-the-output-of-an-animation-has-no-effect"></a>L’animation de la sortie d’une animation n’a aucun effet  
 Vous ne pouvez pas animer un objet qui est le résultat d’une autre animation. Par exemple, si <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> vous utilisez un <xref:System.Windows.Shapes.Shape.Fill%2A> pour <xref:System.Windows.Shapes.Rectangle> animer le <xref:System.Windows.Media.RadialGradientBrush> d’un à un <xref:System.Windows.Media.SolidColorBrush>, <xref:System.Windows.Media.RadialGradientBrush> vous <xref:System.Windows.Media.SolidColorBrush>ne pouvez pas animer les propriétés de la ou .  
  
### <a name="cant-change-the-value-of-a-property-after-animating-it"></a>Impossible de modifier la valeur d’une propriété après l’avoir animée  
 Dans certains cas, il peut sembler que vous ne pouvez pas modifier la valeur d’une propriété une fois qu’elle a été animée, même une fois l’animation terminée. Cela survient car l’animation, même si elle est terminée, remplace toujours la valeur de base de la propriété. Pour empêcher l’animation de dépasser la valeur actuelle de la <xref:System.Windows.Media.Animation.FillBehavior> propriété, l’enlever, ou lui donner un de <xref:System.Windows.Media.Animation.FillBehavior.Stop>. Pour plus d’informations et un exemple, voir [Set a Property After Animating It with a Storyboard](how-to-set-a-property-after-animating-it-with-a-storyboard.md).  
  
### <a name="changing-a-timeline-has-no-effect"></a>La modification d’une chronologie n’a aucun effet  
 Bien <xref:System.Windows.Media.Animation.Timeline> que la plupart des propriétés soient animatables <xref:System.Windows.Media.Animation.Timeline> et puissent être liées aux données, changer la valeur de propriété d’un actif semble n’avoir aucun effet. C’est parce que, quand un <xref:System.Windows.Media.Animation.Timeline> est commencé, <xref:System.Windows.Media.Animation.Timeline> le système de <xref:System.Windows.Media.Animation.Clock> synchronisation fait une copie de la et l’utilise pour créer un objet. La modification de l’original n’a aucun effet sur la copie du système.  
  
 Pour <xref:System.Windows.Media.Animation.Timeline> qu’un à refléter les changements, son horloge doit être régénérée et utilisée pour remplacer l’horloge précédemment créée. Les horloges ne sont pas régénérées automatiquement pour vous. Voici plusieurs façons d’appliquer des modifications de chronologie :  
  
- Si la chronologie est <xref:System.Windows.Media.Animation.Storyboard>ou appartient à un , vous pouvez le faire <xref:System.Windows.Media.Animation.BeginStoryboard> refléter <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> les modifications en réappliquer son storyboard en utilisant un ou la méthode. Cela a pour effet secondaire de redémarrer également l’animation. Dans le code, <xref:System.Windows.Media.Animation.Storyboard.Seek%2A> vous pouvez utiliser la méthode pour faire avancer le storyboard de retour à sa position précédente.  
  
- Si vous avez appliqué une animation <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> directement sur <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> une propriété en utilisant la méthode, appelez la méthode à nouveau et passez-la l’animation qui a été modifiée.  
  
- Si vous travaillez directement au niveau de l’horloge, créez et appliquez un nouveau jeu d’horloges et utilisez-le pour remplacer le précédent jeu d’horloges généré.  
  
 Pour plus d’informations sur les chronologies et les horloges, voir [Animation et Timing System Overview](animation-and-timing-system-overview.md).  
  
### <a name="fillbehaviorstop-doesnt-work-as-expected"></a>FillBehavior.Stop ne fonctionne pas comme prévu  
 Il ya des <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> moments <xref:System.Windows.Media.Animation.FillBehavior.Stop> où la mise en place de la propriété semble n’avoir aucun effet, comme quand une animation "mains off" à l’autre parce qu’il a un <xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A> réglage de <xref:System.Windows.Media.Animation.HandoffBehavior.SnapshotAndReplace>.  
  
 L’exemple suivant <xref:System.Windows.Controls.Canvas>crée <xref:System.Windows.Shapes.Rectangle> un <xref:System.Windows.Media.TranslateTransform>, a et a . Le <xref:System.Windows.Media.TranslateTransform> sera animé pour <xref:System.Windows.Shapes.Rectangle> déplacer <xref:System.Windows.Controls.Canvas>le autour de la .  
  
 [!code-xaml[AnimationTipsAndTricksSample_snip#FillBehaviorTipAnimatedObject](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipanimatedobject)]  
  
 Les exemples de cette section utilisent les <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> objets précédents pour démontrer plusieurs cas où la propriété ne se comporte pas comme vous pouvez vous y attendre.  
  
#### <a name="fillbehaviorstop-and-handoffbehavior-with-multiple-animations"></a>FillBehavior="Stop" et HandoffBehavior avec plusieurs animations  
 Parfois, il semble qu’une <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> animation ignore sa propriété quand elle est remplacée par une deuxième animation. Prenons l’exemple suivant, <xref:System.Windows.Media.Animation.Storyboard> qui crée deux objets et <xref:System.Windows.Media.TranslateTransform> les utilise pour animer le même indiqué dans l’exemple précédent.  
  
 Le <xref:System.Windows.Media.Animation.Storyboard>premier `B1`, anime <xref:System.Windows.Media.TranslateTransform.X%2A> la propriété <xref:System.Windows.Media.TranslateTransform> de la de 0 à 350, qui déplace le rectangle 350 pixels vers la droite. Lorsque l’animation atteint la fin de <xref:System.Windows.Media.TranslateTransform.X%2A> sa durée et cesse de jouer, la propriété revient à sa valeur d’origine, 0. Par conséquent, le rectangle se déplace vers la droite de 350 pixels puis revient à sa position d’origine.  
  
 [!code-xaml[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardB1Button](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipstoryboardb1button)]  
  
 Le <xref:System.Windows.Media.Animation.Storyboard>second `B2`, , anime <xref:System.Windows.Media.TranslateTransform.X%2A> également la <xref:System.Windows.Media.TranslateTransform>propriété de la même . Parce que <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> seule la propriété <xref:System.Windows.Media.Animation.Storyboard> de l’animation dans cet ensemble, l’animation utilise la valeur actuelle de la propriété qu’elle anime comme valeur de départ.  
  
 [!code-xaml[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardB2Button](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipstoryboardb2button)]  
  
 Si vous cliquez sur le <xref:System.Windows.Media.Animation.Storyboard> deuxième bouton pendant que le premier joue, vous pouvez vous attendre au comportement suivant :  
  
1. Le premier storyboard se termine et renvoie le rectangle <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> à <xref:System.Windows.Media.Animation.FillBehavior.Stop>sa position d’origine, parce que l’animation a un de .  
  
2. Le deuxième storyboard est appliqué et s’anime à partir de la position actuelle, qui est désormais 0, jusqu'à 500.  
  
 **Mais ce n’est pas ce qui se produit.** Au lieu de cela, le rectangle ne revient pas. Il continue à se déplacer vers la droite. Cela se produit car la deuxième animation utilise la valeur actuelle de la première animation comme valeur de départ, et anime à partir de cette valeur à 500. Lorsque la deuxième animation remplace <xref:System.Windows.Media.Animation.HandoffBehavior.SnapshotAndReplace> <xref:System.Windows.Media.Animation.HandoffBehavior> la première <xref:System.Windows.Media.Animation.FillBehavior> parce que la est utilisée, la première animation n’a pas d’importance.  
  
#### <a name="fillbehavior-and-the-completed-event"></a>FillBehavior et l’événement terminé  
 Les exemples suivants démontrent <xref:System.Windows.Media.Animation.FillBehavior.Stop> <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> un autre scénario dans lequel le semble n’avoir aucun effet. Encore une fois, l’exemple utilise <xref:System.Windows.Media.TranslateTransform.X%2A> un Storyboard pour animer la propriété de la <xref:System.Windows.Media.TranslateTransform> de 0 à 350. Cependant, cette fois, l’exemple s’inscrit à l’événement. <xref:System.Windows.Media.Animation.Timeline.Completed>  
  
 [!code-xaml[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardCButton](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipstoryboardcbutton)]  
  
 Le <xref:System.Windows.Media.Animation.Timeline.Completed> gestionnaire d’événements commence un autre <xref:System.Windows.Media.Animation.Storyboard> qui anime la même propriété de sa valeur actuelle à 500.  
  
 [!code-csharp[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardC1CompletedHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml.cs#fillbehaviortipstoryboardc1completedhandler)]
 [!code-vb[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardC1CompletedHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/VisualBasic/FillBehaviorTip.xaml.vb#fillbehaviortipstoryboardc1completedhandler)]  
  
 Ce qui suit est la majoration qui définit la seconde <xref:System.Windows.Media.Animation.Storyboard> comme une ressource.  
  
 [!code-xaml[AnimationTipsAndTricksSample_snip#FillBehaviorTipResources](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipresources)]  
  
 Lorsque vous <xref:System.Windows.Media.Animation.Storyboard>exécutez le <xref:System.Windows.Media.TranslateTransform.X%2A> , vous <xref:System.Windows.Media.TranslateTransform> pouvez vous attendre à la propriété de la à animer de 0 <xref:System.Windows.Media.Animation.FillBehavior> à <xref:System.Windows.Media.Animation.FillBehavior.Stop>350, puis revenir à 0 après qu’il se termine (parce qu’il a un réglage de ), puis animer de 0 à 500. Au lieu <xref:System.Windows.Media.TranslateTransform> de cela, les animations de 0 à 350, puis à 500.  
  
 C’est à cause de l’ordre dans lequel WPF soulève des événements et parce que la valeur des propriétés sont mises en cache et ne sont pas recalculées à moins que la propriété est invalidée. L’événement <xref:System.Windows.Media.Animation.Timeline.Completed> est traité d’abord parce qu’il a été déclenché par la chronologie des racines (le premier <xref:System.Windows.Media.Animation.Storyboard>). Pour l’instant, la <xref:System.Windows.Media.TranslateTransform.X%2A> propriété retourne toujours sa valeur animée parce qu’elle n’a pas encore été invalidée. Le <xref:System.Windows.Media.Animation.Storyboard> second utilise la valeur mise en cache comme valeur de départ et commence à animer.  
  
<a name="performancesection"></a>
## <a name="performance"></a>Performances  
  
### <a name="animations-continue-to-run-after-navigating-away-from-a-page"></a>Les animations continuent à s’exécuter après avoir quitté une page  
 Lorsque vous naviguez <xref:System.Windows.Controls.Page> loin d’un qui contient des animations <xref:System.Windows.Controls.Page> en cours d’exécution, ces animations continueront à jouer jusqu’à ce que les ordures recueillies. Selon le système de navigation vous utilisez, une page que vous quittez peut rester en mémoire pendant une durée indéterminée tout en consommant des ressources avec ses animations. Cela est particulièrement visible lorsqu’une page contient des animations en exécution constante (« ambiantes »).  
  
 Pour cette raison, c’est une <xref:System.Windows.FrameworkElement.Unloaded> bonne idée d’utiliser l’événement pour supprimer les animations lorsque vous naviguez loin d’une page.  
  
 Il existe différentes manières de supprimer une animation. Les techniques suivantes peuvent être utilisées pour <xref:System.Windows.Media.Animation.Storyboard>supprimer les animations qui appartiennent à un .  
  
- Pour supprimer <xref:System.Windows.Media.Animation.Storyboard> un vous avez commencé avec un déclencheur d’événement, voir [comment: Supprimer un storyboard](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms749412(v=vs.90)).  
  
- Pour utiliser le <xref:System.Windows.Media.Animation.Storyboard>code pour <xref:System.Windows.Media.Animation.Storyboard.Remove%2A> supprimer un , voir la méthode.  
  
 La technique suivante peut être utilisée, quelle que soit la façon dont l’animation a été démarrée.  
  
- Pour supprimer les animations d’une propriété spécifique, utilisez la <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%28System.Windows.DependencyProperty%2CSystem.Windows.Media.Animation.AnimationTimeline%29> méthode. Spécifiez la propriété étant `null` animée comme le premier paramètre, et comme le second. Cela supprimera toutes les horloges d’animation de la propriété.  
  
 Pour plus d’informations sur les différentes façons d’animer les propriétés, voir [Property Animation Techniques Aperçu](property-animation-techniques-overview.md).  
  
### <a name="using-the-compose-handoffbehavior-consumes-system-resources"></a>L’utilisation de la composition HandoffBehavior consomme des ressources système  
 Lorsque vous <xref:System.Windows.Media.Animation.Storyboard>appliquez un , <xref:System.Windows.Media.Animation.AnimationTimeline>, <xref:System.Windows.Media.Animation.HandoffBehavior.Compose> <xref:System.Windows.Media.Animation.HandoffBehavior>ou <xref:System.Windows.Media.Animation.Clock> <xref:System.Windows.Media.Animation.AnimationClock> à une propriété en utilisant le , tous les objets précédemment associés à cette propriété continuent à consommer des ressources système; le système de chronométrage ne supprimera pas automatiquement ces horloges.  
  
 Pour éviter les problèmes de performance lorsque <xref:System.Windows.Media.Animation.HandoffBehavior.Compose>vous appliquez un grand nombre d’horloges à l’aide, vous devez supprimer les horloges de composition de la propriété animée après qu’ils ont terminé. Il existe plusieurs manières de supprimer une horloge.  
  
- Pour supprimer toutes les horloges <xref:System.Windows.Media.Animation.Animatable.ApplyAnimationClock%28System.Windows.DependencyProperty%2CSystem.Windows.Media.Animation.AnimationClock%29> d’une propriété, utilisez l’objet animé ou <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%28System.Windows.DependencyProperty%2CSystem.Windows.Media.Animation.AnimationTimeline%29> la méthode. Spécifiez la propriété étant `null` animée comme le premier paramètre, et comme le second. Cela supprimera toutes les horloges d’animation de la propriété.  
  
- Pour supprimer <xref:System.Windows.Media.Animation.AnimationClock> un spécifique d’une liste <xref:System.Windows.Media.Animation.Clock.Controller%2A> d’horloges, <xref:System.Windows.Media.Animation.ClockController>utilisez la <xref:System.Windows.Media.Animation.ClockController.Remove%2A> propriété <xref:System.Windows.Media.Animation.ClockController>de la <xref:System.Windows.Media.Animation.AnimationClock> pour récupérer un , puis appelez la méthode de la . Cela se fait <xref:System.Windows.Media.Animation.Clock.Completed> généralement dans le gestionnaire d’événements pour une horloge. Notez que seules les horloges <xref:System.Windows.Media.Animation.ClockController>à racines peuvent être contrôlées par un ; la <xref:System.Windows.Media.Animation.Clock.Controller%2A> propriété d’une `null`horloge enfant reviendra . Notez également <xref:System.Windows.Media.Animation.Clock.Completed> que l’événement ne sera pas appelé si la durée effective de l’horloge est pour toujours.  Dans ce cas, l’utilisateur devra <xref:System.Windows.Media.Animation.ClockController.Remove%2A>déterminer quand appeler .  
  
 Il s’agit principalement d’un problème pour les animations sur des objets qui ont une durée de vie longue.  Lorsqu’un objet est récupéré par le garbage collector, ses horloges sont également déconnectées et récupérées.  
  
 Pour plus d’informations sur les objets de l’horloge, voir [Animation et Timing System Overview](animation-and-timing-system-overview.md).  
  
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble de l’animation](animation-overview.md)
