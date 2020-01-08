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
ms.openlocfilehash: ef59631663e6cf1c98adfed77a2dbdb6ca124fa1
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75636027"
---
# <a name="animation-tips-and-tricks"></a>Conseils et astuces sur les animations
Lorsque vous travaillez avec des animations dans WPF, il existe un certain nombre de trucs et astuces qui peuvent rendre vos animations plus performantes et vous faire gagner en frustration.  
  
<a name="generalissuessection"></a>   
## <a name="general-issues"></a>Problèmes généraux  
  
### <a name="animating-the-position-of-a-scroll-bar-or-slider-freezes-it"></a>L’animation de la position d’une barre de défilement ou d’un curseur bloque cet élément  
 Si vous animez la position d’une barre de défilement ou d’un curseur à l’aide d’une animation qui a une <xref:System.Windows.Media.Animation.FillBehavior> de <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd> (valeur par défaut), l’utilisateur ne pourra plus déplacer la barre de défilement ou le curseur. Cela survient car l’animation, même si elle est terminée, remplace toujours la valeur de base de la propriété cible. Pour empêcher l’animation de remplacer la valeur actuelle de la propriété, supprimez-la ou donnez-lui une <xref:System.Windows.Media.Animation.FillBehavior> de <xref:System.Windows.Media.Animation.FillBehavior.Stop>. Pour plus d’informations et pour obtenir un exemple, consultez [définir une propriété après l’avoir animée avec un Storyboard](how-to-set-a-property-after-animating-it-with-a-storyboard.md).  
  
### <a name="animating-the-output-of-an-animation-has-no-effect"></a>L’animation de la sortie d’une animation n’a aucun effet  
 Vous ne pouvez pas animer un objet qui est le résultat d’une autre animation. Par exemple, si vous utilisez un <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> pour animer la <xref:System.Windows.Shapes.Shape.Fill%2A> d’un <xref:System.Windows.Shapes.Rectangle> d’un <xref:System.Windows.Media.RadialGradientBrush> à un <xref:System.Windows.Media.SolidColorBrush>, vous ne pouvez animer aucune propriété du <xref:System.Windows.Media.RadialGradientBrush> ou <xref:System.Windows.Media.SolidColorBrush>.  
  
### <a name="cant-change-the-value-of-a-property-after-animating-it"></a>Impossible de modifier la valeur d’une propriété après l’avoir animée  
 Dans certains cas, il peut sembler que vous ne pouvez pas modifier la valeur d’une propriété une fois qu’elle a été animée, même une fois l’animation terminée. Cela survient car l’animation, même si elle est terminée, remplace toujours la valeur de base de la propriété. Pour empêcher l’animation de remplacer la valeur actuelle de la propriété, supprimez-la ou donnez-lui une <xref:System.Windows.Media.Animation.FillBehavior> de <xref:System.Windows.Media.Animation.FillBehavior.Stop>. Pour plus d’informations et pour obtenir un exemple, consultez [définir une propriété après l’avoir animée avec un Storyboard](how-to-set-a-property-after-animating-it-with-a-storyboard.md).  
  
### <a name="changing-a-timeline-has-no-effect"></a>La modification d’une chronologie n’a aucun effet  
 Bien que la plupart des <xref:System.Windows.Media.Animation.Timeline> propriétés puissent être animées et peuvent être liées aux données, la modification des valeurs de propriété d’un <xref:System.Windows.Media.Animation.Timeline> actif semble n’avoir aucun effet. En effet, lorsqu’un <xref:System.Windows.Media.Animation.Timeline> est commencé, le système de minuterie fait une copie du <xref:System.Windows.Media.Animation.Timeline> et l’utilise pour créer un objet <xref:System.Windows.Media.Animation.Clock>. La modification de l’original n’a aucun effet sur la copie du système.  
  
 Pour qu’un <xref:System.Windows.Media.Animation.Timeline> reflète les modifications, son horloge doit être régénérée et utilisée pour remplacer l’horloge créée précédemment. Les horloges ne sont pas régénérées automatiquement pour vous. Voici plusieurs façons d’appliquer des modifications de chronologie :  
  
- Si la chronologie est ou appartient à un <xref:System.Windows.Media.Animation.Storyboard>, vous pouvez faire en sorte qu’elle reflète les modifications en réappliquant son Storyboard à l’aide d’un <xref:System.Windows.Media.Animation.BeginStoryboard> ou de la méthode <xref:System.Windows.Media.Animation.Storyboard.Begin%2A>. Cela a pour effet secondaire de redémarrer également l’animation. Dans le code, vous pouvez utiliser la méthode <xref:System.Windows.Media.Animation.Storyboard.Seek%2A> pour faire avancer le Storyboard à sa position précédente.  
  
- Si vous avez appliqué une animation directement à une propriété à l’aide de la méthode <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>, appelez à nouveau la méthode <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> et transmettez-lui l’animation qui a été modifiée.  
  
- Si vous travaillez directement au niveau de l’horloge, créez et appliquez un nouveau jeu d’horloges et utilisez-le pour remplacer le précédent jeu d’horloges généré.  
  
 Pour plus d’informations sur les chronologies et les horloges, consultez [vue d’ensemble du système d’animation et de minutage](animation-and-timing-system-overview.md).  
  
### <a name="fillbehaviorstop-doesnt-work-as-expected"></a>FillBehavior.Stop ne fonctionne pas comme prévu  
 Dans certains cas, la définition de la propriété <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> sur <xref:System.Windows.Media.Animation.FillBehavior.Stop> semble n’avoir aucun effet, par exemple lorsqu’une animation est « mains » vers une autre, car elle a un paramètre <xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A> de <xref:System.Windows.Media.Animation.HandoffBehavior.SnapshotAndReplace>.  
  
 L’exemple suivant crée un <xref:System.Windows.Controls.Canvas>, un <xref:System.Windows.Shapes.Rectangle> et un <xref:System.Windows.Media.TranslateTransform>. Le <xref:System.Windows.Media.TranslateTransform> sera animé pour déplacer le <xref:System.Windows.Shapes.Rectangle> autour du <xref:System.Windows.Controls.Canvas>.  
  
 [!code-xaml[AnimationTipsAndTricksSample_snip#FillBehaviorTipAnimatedObject](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipanimatedobject)]  
  
 Les exemples de cette section utilisent les objets précédents pour illustrer plusieurs cas où la propriété <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> ne se comporte pas comme prévu.  
  
#### <a name="fillbehaviorstop-and-handoffbehavior-with-multiple-animations"></a>FillBehavior="Stop" et HandoffBehavior avec plusieurs animations  
 Parfois, il semble qu’une animation ignore sa propriété <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> lorsqu’elle est remplacée par une deuxième animation. Prenons l’exemple suivant, qui crée deux objets <xref:System.Windows.Media.Animation.Storyboard> et les utilise pour animer les mêmes <xref:System.Windows.Media.TranslateTransform> présentées dans l’exemple précédent.  
  
 La première <xref:System.Windows.Media.Animation.Storyboard>, `B1`, anime la propriété <xref:System.Windows.Media.TranslateTransform.X%2A> de la <xref:System.Windows.Media.TranslateTransform> de 0 à 350, ce qui déplace le rectangle de 350 pixels vers la droite. Lorsque l’animation atteint la fin de sa durée et cesse de s’exécuter, la propriété <xref:System.Windows.Media.TranslateTransform.X%2A> revient à sa valeur d’origine, 0. Par conséquent, le rectangle se déplace vers la droite de 350 pixels puis revient à sa position d’origine.  
  
 [!code-xaml[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardB1Button](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipstoryboardb1button)]  
  
 La deuxième <xref:System.Windows.Media.Animation.Storyboard>, `B2`, anime également la propriété <xref:System.Windows.Media.TranslateTransform.X%2A> de la même <xref:System.Windows.Media.TranslateTransform>. Étant donné que seule la propriété <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> de l’animation dans ce <xref:System.Windows.Media.Animation.Storyboard> est définie, l’animation utilise la valeur actuelle de la propriété qu’elle anime comme valeur de départ.  
  
 [!code-xaml[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardB2Button](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipstoryboardb2button)]  
  
 Si vous cliquez sur le deuxième bouton pendant que la première <xref:System.Windows.Media.Animation.Storyboard> est lue, vous pouvez vous attendre à ce que le comportement suivant se présente :  
  
1. Le premier Storyboard se termine et renvoie le rectangle à sa position d’origine, car l’animation a une <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> de <xref:System.Windows.Media.Animation.FillBehavior.Stop>.  
  
2. Le deuxième storyboard est appliqué et s’anime à partir de la position actuelle, qui est désormais 0, jusqu'à 500.  
  
 **Mais ce n’est pas ce qui se produit.** Au lieu de cela, le rectangle ne revient pas. Il continue à se déplacer vers la droite. Cela se produit car la deuxième animation utilise la valeur actuelle de la première animation comme valeur de départ, et anime à partir de cette valeur à 500. Lorsque la deuxième animation remplace la première en raison de l’utilisation de la <xref:System.Windows.Media.Animation.HandoffBehavior> <xref:System.Windows.Media.Animation.HandoffBehavior.SnapshotAndReplace>, le <xref:System.Windows.Media.Animation.FillBehavior> de la première animation n’a pas d’importance.  
  
#### <a name="fillbehavior-and-the-completed-event"></a>FillBehavior et l’événement terminé  
 Les exemples suivants illustrent un autre scénario dans lequel l' <xref:System.Windows.Media.Animation.FillBehavior.Stop><xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> semble n’avoir aucun effet. Là encore, l’exemple utilise une table de montage séquentiel pour animer la propriété <xref:System.Windows.Media.TranslateTransform.X%2A> du <xref:System.Windows.Media.TranslateTransform> de 0 à 350. Toutefois, cette fois, l’exemple s’inscrit pour l’événement <xref:System.Windows.Media.Animation.Timeline.Completed>.  
  
 [!code-xaml[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardCButton](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipstoryboardcbutton)]  
  
 Le gestionnaire d’événements <xref:System.Windows.Media.Animation.Timeline.Completed> démarre une autre <xref:System.Windows.Media.Animation.Storyboard> qui anime la même propriété de sa valeur actuelle à 500.  
  
 [!code-csharp[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardC1CompletedHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml.cs#fillbehaviortipstoryboardc1completedhandler)]
 [!code-vb[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardC1CompletedHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/VisualBasic/FillBehaviorTip.xaml.vb#fillbehaviortipstoryboardc1completedhandler)]  
  
 Voici le balisage qui définit le deuxième <xref:System.Windows.Media.Animation.Storyboard> en tant que ressource.  
  
 [!code-xaml[AnimationTipsAndTricksSample_snip#FillBehaviorTipResources](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipresources)]  
  
 Lorsque vous exécutez l' <xref:System.Windows.Media.Animation.Storyboard>, vous pouvez vous attendre à ce que la propriété <xref:System.Windows.Media.TranslateTransform.X%2A> de la <xref:System.Windows.Media.TranslateTransform> s’anime de 0 à 350, puis rétablir la valeur 0 à l’issue de l’opération (car elle a un paramètre <xref:System.Windows.Media.Animation.FillBehavior> de <xref:System.Windows.Media.Animation.FillBehavior.Stop>), puis s’animer de 0 à 500. Au lieu de cela, le <xref:System.Windows.Media.TranslateTransform> s’anime de 0 à 350, puis à 500.  
  
 En effet, dans l’ordre dans lequel WPF déclenche les événements et, les valeurs de propriété sont mises en cache et ne sont pas recalculées, sauf si la propriété est invalidée. L’événement <xref:System.Windows.Media.Animation.Timeline.Completed> est traité en premier, car il a été déclenché par la chronologie racine (le premier <xref:System.Windows.Media.Animation.Storyboard>). À ce stade, la propriété <xref:System.Windows.Media.TranslateTransform.X%2A> retourne toujours sa valeur animée, car elle n’a pas encore été invalidée. Le deuxième <xref:System.Windows.Media.Animation.Storyboard> utilise la valeur mise en cache comme valeur de départ et commence l’animation.  
  
<a name="performancesection"></a>   
## <a name="performance"></a>Performances  
  
### <a name="animations-continue-to-run-after-navigating-away-from-a-page"></a>Les animations continuent à s’exécuter après avoir quitté une page  
 Lorsque vous quittez un <xref:System.Windows.Controls.Page> qui contient des animations en cours d’exécution, ces animations continuent de fonctionner jusqu’à ce que la <xref:System.Windows.Controls.Page> soit récupérée par le garbage collector. Selon le système de navigation vous utilisez, une page que vous quittez peut rester en mémoire pendant une durée indéterminée tout en consommant des ressources avec ses animations. Cela est particulièrement visible lorsqu’une page contient des animations en exécution constante (« ambiantes »).  
  
 Pour cette raison, il est judicieux d’utiliser l’événement <xref:System.Windows.FrameworkElement.Unloaded> pour supprimer les animations lorsque vous quittez une page.  
  
 Il existe différentes manières de supprimer une animation. Les techniques suivantes peuvent être utilisées pour supprimer les animations qui appartiennent à un <xref:System.Windows.Media.Animation.Storyboard>.  
  
- Pour supprimer une <xref:System.Windows.Media.Animation.Storyboard> vous avez démarré avec un déclencheur d’événements, consultez [Comment : supprimer une table de montage séquentiel](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms749412(v=vs.90)).  
  
- Pour utiliser du code pour supprimer une <xref:System.Windows.Media.Animation.Storyboard>, consultez la méthode <xref:System.Windows.Media.Animation.Storyboard.Remove%2A>.  
  
 La technique suivante peut être utilisée, quelle que soit la façon dont l’animation a été démarrée.  
  
- Pour supprimer des animations d’une propriété spécifique, utilisez la méthode <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%28System.Windows.DependencyProperty%2CSystem.Windows.Media.Animation.AnimationTimeline%29>. Spécifiez la propriété animée comme premier paramètre et `null` comme deuxième paramètre. Cela supprimera toutes les horloges d’animation de la propriété.  
  
 Pour plus d’informations sur les différentes façons d’animer des propriétés, consultez [vue d’ensemble des techniques d’animation de propriétés](property-animation-techniques-overview.md).  
  
### <a name="using-the-compose-handoffbehavior-consumes-system-resources"></a>L’utilisation de la composition HandoffBehavior consomme des ressources système  
 Lorsque vous appliquez une <xref:System.Windows.Media.Animation.Storyboard>, <xref:System.Windows.Media.Animation.AnimationTimeline>ou <xref:System.Windows.Media.Animation.AnimationClock> à une propriété à l’aide de la <xref:System.Windows.Media.Animation.HandoffBehavior><xref:System.Windows.Media.Animation.HandoffBehavior.Compose>, tous les objets <xref:System.Windows.Media.Animation.Clock> précédemment associés à cette propriété continuent à consommer des ressources système. le système de minutage ne supprime pas automatiquement ces horloges.  
  
 Pour éviter les problèmes de performances lorsque vous appliquez un grand nombre d’horloges à l’aide de <xref:System.Windows.Media.Animation.HandoffBehavior.Compose>, vous devez supprimer la composition des horloges de la propriété animée une fois qu’elles sont terminées. Il existe plusieurs manières de supprimer une horloge.  
  
- Pour supprimer toutes les horloges d’une propriété, utilisez la méthode <xref:System.Windows.Media.Animation.Animatable.ApplyAnimationClock%28System.Windows.DependencyProperty%2CSystem.Windows.Media.Animation.AnimationClock%29> ou <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%28System.Windows.DependencyProperty%2CSystem.Windows.Media.Animation.AnimationTimeline%29> de l’objet animé. Spécifiez la propriété animée comme premier paramètre et `null` comme deuxième paramètre. Cela supprimera toutes les horloges d’animation de la propriété.  
  
- Pour supprimer un <xref:System.Windows.Media.Animation.AnimationClock> spécifique d’une liste d’horloges, utilisez la propriété <xref:System.Windows.Media.Animation.Clock.Controller%2A> du <xref:System.Windows.Media.Animation.AnimationClock> pour récupérer un <xref:System.Windows.Media.Animation.ClockController>, puis appelez la méthode <xref:System.Windows.Media.Animation.ClockController.Remove%2A> de l' <xref:System.Windows.Media.Animation.ClockController>. Cela s’effectue généralement dans le gestionnaire d’événements <xref:System.Windows.Media.Animation.Clock.Completed> pour une horloge. Notez que seules les horloges racine peuvent être contrôlées par un <xref:System.Windows.Media.Animation.ClockController>; la propriété <xref:System.Windows.Media.Animation.Clock.Controller%2A> d’une horloge enfant retourne `null`. Notez également que l’événement <xref:System.Windows.Media.Animation.Clock.Completed> n’est pas appelé si la durée effective de l’horloge est illimitée.  Dans ce cas, l’utilisateur doit déterminer quand appeler <xref:System.Windows.Media.Animation.ClockController.Remove%2A>.  
  
 Il s’agit principalement d’un problème pour les animations sur des objets qui ont une durée de vie longue.  Lorsqu’un objet est récupéré par le garbage collector, ses horloges sont également déconnectées et récupérées.  
  
 Pour plus d’informations sur les objets Clock, consultez [vue d’ensemble du système d’animation et de minutage](animation-and-timing-system-overview.md).  
  
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble de l’animation](animation-overview.md)
