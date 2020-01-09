---
title: Vue d'ensemble des comportements de minutage
ms.date: 03/30/2017
helpviewer_keywords:
- timing behaviors [WPF]
- behaviors [WPF], timing
ms.assetid: 5b714d46-bd46-48b8-b467-b4be89ba3091
ms.openlocfilehash: a85f980a0cefaa282e9e92d533a2306a9009e3e7
ms.sourcegitcommit: f8c36054eab877de4d40a705aacafa2552ce70e9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/31/2019
ms.locfileid: "75559948"
---
# <a name="timing-behaviors-overview"></a>Vue d'ensemble des comportements de minutage
Cette rubrique décrit les comportements de minutage des animations et d’autres objets de <xref:System.Windows.Media.Animation.Timeline>.  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Configuration requise  
 Pour comprendre cette rubrique, vous devez connaître les fonctionnalités de base utilisées pour l’animation. Pour plus d’informations, consultez [vue d’ensemble](animation-overview.md)de l’animation.  
  
<a name="timelinetypes"></a>   
## <a name="timeline-types"></a>Types de chronologie  
 Un <xref:System.Windows.Media.Animation.Timeline> représente un segment de temps. Elle fournit des propriétés qui vous permettent de spécifier la longueur de ce segment, le moment où il doit démarrer, combien de fois il doit se répéter, à quelle vitesse le temps s’écoule dans ce segment et bien plus encore.  
  
 Les classes qui héritent de la classe de chronologie fournissent des fonctionnalités supplémentaires, comme la lecture de médias et d’animations. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fournit les types de <xref:System.Windows.Media.Animation.Timeline> suivants.  
  
|Type de chronologie|Description|  
|-------------------|-----------------|  
|<xref:System.Windows.Media.Animation.AnimationTimeline>|Classe de base abstraite pour les objets <xref:System.Windows.Media.Animation.Timeline> qui génèrent des valeurs de sortie pour animer des propriétés.|  
|<xref:System.Windows.Media.MediaTimeline>|Génère une sortie à partir d’un fichier multimédia.|  
|<xref:System.Windows.Media.Animation.ParallelTimeline>|Type de <xref:System.Windows.Media.Animation.TimelineGroup> qui regroupe et contrôle les objets de <xref:System.Windows.Media.Animation.Timeline> enfants.|  
|<xref:System.Windows.Media.Animation.Storyboard>|Type de <xref:System.Windows.Media.Animation.ParallelTimeline> qui fournit des informations de ciblage pour les objets Timeline qu’il contient.|  
|<xref:System.Windows.Media.Animation.Timeline>|Classe de base abstraite qui définit les comportements de minutage.|  
|<xref:System.Windows.Media.Animation.TimelineGroup>|Classe abstraite pour les objets <xref:System.Windows.Media.Animation.Timeline> qui peuvent contenir d’autres objets <xref:System.Windows.Media.Animation.Timeline>.|  
  
<a name="propertiesthatcontroltimelinelength"></a>   
## <a name="properties-that-control-the-length-of-a-timeline"></a>Propriétés qui contrôlent la longueur d’une chronologie  
 Une <xref:System.Windows.Media.Animation.Timeline> représente un segment de temps, et la longueur d’une chronologie peut être décrite de différentes façons. Le tableau suivant définit plusieurs termes servant à décrire la longueur d’une chronologie.  
  
|Terme|Description|Propriétés||||  
|----------|-----------------|----------------|-|-|-|  
|Durée simple|Le temps qu’une chronologie prend pour faire une seule itération vers l’avant.|<xref:System.Windows.Media.Animation.Timeline.Duration%2A>||||  
|Une répétition|Durée nécessaire à une chronologie pour s’exécuter une seule fois et, si la propriété <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> a la valeur true, lire une fois en arrière.|<xref:System.Windows.Media.Animation.Timeline.Duration%2A>, <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>||||  
|Période active|Durée nécessaire à une chronologie pour terminer toutes les répétitions spécifiées par sa propriété <xref:System.Windows.Media.Animation.RepeatBehavior>.|<xref:System.Windows.Media.Animation.Timeline.Duration%2A>, <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>, <xref:System.Windows.Media.Animation.RepeatBehavior>||||  
  
<a name="duration"></a>   
### <a name="the-duration-property"></a>La propriété Duration  
 Comme indiqué plus haut, une chronologie représente un segment de temps. La longueur de ce segment est déterminée par le <xref:System.Windows.Media.Animation.Timeline.Duration%2A>de la chronologie. Lorsqu’une chronologie atteint la fin de sa durée, elle s’arrête. Si la chronologie a des chronologies enfants, celles-ci s’arrêtent également. Dans le cas d’une animation, le <xref:System.Windows.Media.Animation.Timeline.Duration%2A> spécifie le temps nécessaire à l’animation pour passer de sa valeur de départ à sa valeur finale. La durée d’une chronologie est parfois appelée *durée simple*, pour faire la distinction entre la durée d’une itération unique et la durée totale pendant laquelle l’animation est lue, y compris les répétitions. Vous pouvez spécifier une durée à l’aide d’une valeur de temps finie ou des valeurs spéciales <xref:System.Windows.Duration.Automatic%2A> ou <xref:System.Windows.Duration.Forever%2A>. La durée d’une animation doit être résolue en une valeur <xref:System.Windows.Duration.TimeSpan%2A>, afin de permettre la transition entre les valeurs.  
  
 L’exemple suivant montre une <xref:System.Windows.Media.Animation.DoubleAnimation> avec une <xref:System.Windows.Media.Animation.Timeline.Duration%2A> de cinq secondes.  
  
 [!code-xaml[animation_ovws_snippet#AnimationWith5SecondDurationInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#animationwith5seconddurationinline)]  
  
 Les chronologies de conteneur, telles que <xref:System.Windows.Media.Animation.Storyboard> et <xref:System.Windows.Media.Animation.ParallelTimeline>, ont une durée par défaut de <xref:System.Windows.Duration.Automatic%2A>, ce qui signifie qu’elles se terminent automatiquement lorsque leur dernier enfant arrête de fonctionner. L’exemple suivant montre un <xref:System.Windows.Media.Animation.Storyboard> dont la <xref:System.Windows.Media.Animation.Timeline.Duration%2A> est résolue à cinq secondes, la durée pendant laquelle tous ses objets enfants <xref:System.Windows.Media.Animation.DoubleAnimation> sont exécutés.  
  
 [!code-xaml[animation_ovws_snippet#ContainerTimelineExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#containertimelineexampleinline)]  
  
 En définissant la <xref:System.Windows.Media.Animation.Timeline.Duration%2A> d’une chronologie de conteneur sur une valeur de <xref:System.Windows.Duration.TimeSpan%2A>, vous pouvez forcer à jouer une longueur plus longue ou plus petite que ses objets <xref:System.Windows.Media.Animation.Timeline> enfants. Si vous affectez à la <xref:System.Windows.Media.Animation.Timeline.Duration%2A> une valeur inférieure à la longueur des objets enfant <xref:System.Windows.Media.Animation.Timeline> enfants de la chronologie de conteneur, les objets <xref:System.Windows.Media.Animation.Timeline> enfants cessent de fonctionner lorsque la chronologie du conteneur le fait. L’exemple suivant définit la <xref:System.Windows.Media.Animation.Timeline.Duration%2A> du <xref:System.Windows.Media.Animation.Storyboard> des exemples précédents à trois secondes. Par conséquent, le premier <xref:System.Windows.Media.Animation.DoubleAnimation> arrête la progression au bout de trois secondes, lorsqu’il a animé la largeur du rectangle cible à 60.  
  
 [!code-xaml[animation_ovws_snippet#ContainerTimelineWithShorterDurationExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#containertimelinewithshorterdurationexampleinline)]  
  
<a name="repeatinganimations"></a>   
### <a name="the-repeatbehavior-property"></a>La propriété RepeatBehavior  
 La propriété <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> d’un <xref:System.Windows.Media.Animation.Timeline> contrôle le nombre de fois qu’il répète sa durée simple. À l’aide de la propriété <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>, vous pouvez spécifier le nombre de fois que la chronologie est jouée (une itération <xref:System.Windows.Media.Animation.RepeatBehavior.Count%2A>) ou la durée totale de lecture (une répétition <xref:System.Windows.Media.Animation.RepeatBehavior.Duration%2A>). Dans les deux cas, l’animation se répète de bout en bout autant de fois qu’il est nécessaire pour respecter la durée ou le nombre imposés. Par défaut, les chronologies ont un nombre d’itérations de `1.0`, ce qui signifie qu’elles jouent une seule fois et ne se répètent pas du tout.  
  
 L’exemple suivant utilise la propriété <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> pour rendre un <xref:System.Windows.Media.Animation.DoubleAnimation> lire deux fois sa durée simple en spécifiant un nombre d’itérations.  
  
 [!code-xaml[animation_ovws_snippet#TBRepeatBehavior2xExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbrepeatbehavior2xexampleinline)]  
  
 L’exemple suivant utilise la propriété <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> pour rendre le <xref:System.Windows.Media.Animation.DoubleAnimation> lu pendant la moitié de sa durée simple.  
  
 [!code-xaml[animation_ovws_snippet#TBRepeatBehavior05xExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbrepeatbehavior05xexampleinline)]  
  
 Si vous affectez à la propriété <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> d’un <xref:System.Windows.Media.Animation.Timeline> la valeur <xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>, le <xref:System.Windows.Media.Animation.Timeline> se répète jusqu’à ce qu’il soit arrêté de manière interactive ou par le système de minutage. L’exemple suivant utilise la propriété <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> pour faire en sorte que le <xref:System.Windows.Media.Animation.DoubleAnimation> s’exécute indéfiniment.  
  
 [!code-xaml[animation_ovws_snippet#TBRepeatBehaviorForeverExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbrepeatbehaviorforeverexampleinline)]  
  
 Pour obtenir un exemple supplémentaire, consultez [répéter une animation](how-to-repeat-an-animation.md).  
  
<a name="autoreverseproperty"></a>   
### <a name="the-autoreverse-property"></a>La propriété AutoReverse  
 La propriété <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> spécifie si un <xref:System.Windows.Media.Animation.Timeline> est lu vers l’arrière à la fin de chaque itération vers l’avant. L’exemple suivant affecte à la propriété <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> d’un <xref:System.Windows.Media.Animation.DoubleAnimation> la valeur `true`; par conséquent, il s’anime de zéro à 100, puis de 100 à zéro. Elle s’exécute pendant 10 secondes au total.  
  
 [!code-xaml[animation_ovws_snippet#TBAutoReverseExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbautoreverseexampleinline)]  
  
 Quand vous utilisez une valeur de <xref:System.Windows.Media.Animation.RepeatBehavior.Count%2A> pour spécifier le <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> d’un <xref:System.Windows.Media.Animation.Timeline> et que la propriété <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> de cette <xref:System.Windows.Media.Animation.Timeline> est `true`, une répétition unique se compose d’une itération directe suivie d’une itération vers l’arrière.  L’exemple suivant définit la <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> du <xref:System.Windows.Media.Animation.DoubleAnimation> de l’exemple précédent sur un <xref:System.Windows.Media.Animation.RepeatBehavior.Count%2A> de deux. Par conséquent, le <xref:System.Windows.Media.Animation.DoubleAnimation> est lu pendant 20 secondes : en avant pendant cinq secondes, en arrière pendant cinq secondes, en avant de 5 secondes, puis en arrière pendant cinq secondes.  
  
 [!code-xaml[animation_ovws_snippet#TBAutoReverseRepeatExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbautoreverserepeatexampleinline)]  
  
 Si une chronologie de conteneur a des objets enfants <xref:System.Windows.Media.Animation.Timeline>, ils sont inversés lorsque la chronologie du conteneur le fait. Pour obtenir des exemples supplémentaires, consultez [spécifier si une chronologie est automatiquement inversée](how-to-specify-whether-a-timeline-automatically-reverses.md).  
  
<a name="timelinebegin"></a>   
## <a name="the-begintime-property"></a>La propriété BeginTime  
 La propriété <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> vous permet de spécifier le début d’une chronologie.  Le temps de début d’une chronologie est relatif à la chronologie de son parent. Un temps de début de zéro seconde signifie que la chronologie démarre dès que son parent démarre ; toute autre valeur crée un décalage entre le démarrage de la chronologie parent et celui de la chronologie enfant. Par exemple, un temps de début de deux secondes signifie que la chronologie démarre quand son parent a atteint une durée de deux secondes. Par défaut, toutes les chronologies ont un temps de début de zéro seconde. Vous pouvez également définir l’heure de début d’une chronologie sur `null`, ce qui empêche le démarrage de la chronologie. Dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], vous spécifiez NULL à l’aide de l' [extension de balisage x :null](../../../desktop-wpf/xaml-services/xnull-markup-extension.md).  
  
 Notez que l’heure de début n’est pas appliquée à chaque fois qu’une chronologie se répète en raison de son paramètre <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>. Si vous deviez créer une animation avec une <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> de 10 secondes et une <xref:System.Windows.Media.Animation.RepeatBehavior> de <xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>, il y aura un délai de 10 secondes avant que l’animation ne soit jouée pour la première fois, mais pas pour chaque répétition successive. Toutefois, si la chronologie du parent de l’animation devait redémarrer ou se répéter, le délai de 10 secondes se produirait.  
  
 La propriété <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> est utile pour l’échelonnement des chronologies. L’exemple suivant crée un <xref:System.Windows.Media.Animation.Storyboard> qui a deux objets <xref:System.Windows.Media.Animation.DoubleAnimation> enfants. La première animation a une <xref:System.Windows.Media.Animation.Timeline.Duration%2A> de cinq secondes, tandis que la seconde a une <xref:System.Windows.Media.Animation.Timeline.Duration%2A> de 3 secondes. L’exemple définit la <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> du deuxième <xref:System.Windows.Media.Animation.DoubleAnimation> à 5 secondes, afin qu’il commence à s’exécuter après la fin du premier <xref:System.Windows.Media.Animation.DoubleAnimation>.  
  
 [!code-xaml[animation_ovws_snippet#TBBeginTimeExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbbegintimeexampleinline)]  
  
<a name="fillbehaviorproperty"></a>   
## <a name="the-fillbehavior-property"></a>La propriété FillBehavior  
 Lorsqu’un <xref:System.Windows.Media.Animation.Timeline> atteint la fin de sa durée active totale, la propriété <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> spécifie s’il s’arrête ou conserve sa dernière valeur. Une animation avec une <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> de <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd> « contient » sa valeur de sortie : la propriété animée conserve la dernière valeur de l’animation. Une valeur de <xref:System.Windows.Media.Animation.FillBehavior.Stop> indique que l’animation n’affecte pas sa propriété cible une fois qu’elle s’est terminée.  
  
 L’exemple suivant crée un <xref:System.Windows.Media.Animation.Storyboard> qui a deux objets <xref:System.Windows.Media.Animation.DoubleAnimation> enfants. Les deux objets <xref:System.Windows.Media.Animation.DoubleAnimation> animent le <xref:System.Windows.FrameworkElement.Width%2A> d’un <xref:System.Windows.Shapes.Rectangle> de 0 à 100. Les éléments de <xref:System.Windows.Shapes.Rectangle> ont des valeurs de <xref:System.Windows.FrameworkElement.Width%2A> non animées de 500 (device independent pixels).  
  
- La propriété <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> du premier <xref:System.Windows.Media.Animation.DoubleAnimation> est définie sur <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>, la valeur par défaut. Par conséquent, la largeur du rectangle reste à 100 après la fin de l' <xref:System.Windows.Media.Animation.DoubleAnimation>.  
  
- La propriété <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> du deuxième <xref:System.Windows.Media.Animation.DoubleAnimation> a la valeur <xref:System.Windows.Media.Animation.FillBehavior.Stop>. Par conséquent, le <xref:System.Windows.FrameworkElement.Width%2A> du deuxième <xref:System.Windows.Shapes.Rectangle> revient à 500 après la fin de l' <xref:System.Windows.Media.Animation.DoubleAnimation>.  
  
 [!code-xaml[animation_ovws_snippet#TBFillBehaviorExample](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbfillbehaviorexample)]  
  
<a name="speedproperties"></a>   
## <a name="properties-that-control-the-speed-of-a-timeline"></a>Propriétés qui contrôlent la vitesse d’une chronologie  
 La classe <xref:System.Windows.Media.Animation.Timeline> fournit trois propriétés pour spécifier sa vitesse :  
  
- <xref:System.Windows.Media.Animation.Timeline.SpeedRatio%2A> : spécifie ce taux, par rapport à son parent, à partir duquel la progression d’un <xref:System.Windows.Media.Animation.Timeline>est définie. Les valeurs supérieures à une augmentent la vitesse du <xref:System.Windows.Media.Animation.Timeline> et de ses objets <xref:System.Windows.Media.Animation.Timeline> enfants ; les valeurs comprises entre zéro et un le ralentissent. La valeur 1 indique que <xref:System.Windows.Media.Animation.Timeline> progresse à la même vitesse que son parent. Le paramètre <xref:System.Windows.Media.Animation.Timeline.SpeedRatio%2A> d’une chronologie de conteneur affecte également tous ses objets de <xref:System.Windows.Media.Animation.Timeline> enfants.  
  
- <xref:System.Windows.Media.Animation.Timeline.AccelerationRatio%2A> : spécifie le pourcentage de la <xref:System.Windows.Media.Animation.Timeline.Duration%2A> d’une chronologie consacrée à l’accélération. Pour obtenir un exemple, consultez [Comment : accélérer ou ralentir une animation](how-to-accelerate-or-decelerate-an-animation.md). 
  
- <xref:System.Windows.Media.Animation.Timeline.DecelerationRatio%2A> : spécifie le pourcentage de la <xref:System.Windows.Media.Animation.Timeline.Duration%2A> d’une chronologie consacrée à la décélération. Pour obtenir un exemple, consultez [Comment : accélérer ou ralentir une animation](how-to-accelerate-or-decelerate-an-animation.md).  
  
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble de l’animation](animation-overview.md)
- [Vue d'ensemble de l'animation et du système de minutage](animation-and-timing-system-overview.md)
- [Vue d'ensemble des événements de minuterie](timing-events-overview.md)
- [Guides pratiques](animation-and-timing-how-to-topics.md)
- [Comportement de minuterie d’animation exemple](https://go.microsoft.com/fwlink/?LinkID=159970)
