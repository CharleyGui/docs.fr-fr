---
title: Vue d'ensemble des comportements de minutage
ms.date: 03/30/2017
helpviewer_keywords:
- timing behaviors [WPF]
- behaviors [WPF], timing
ms.assetid: 5b714d46-bd46-48b8-b467-b4be89ba3091
ms.openlocfilehash: 3bb42ddd991d3ae1221cc794afdd4aafc74a6046
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79145395"
---
# <a name="timing-behaviors-overview"></a>Vue d'ensemble des comportements de minutage
Ce sujet décrit les comportements de synchronisation <xref:System.Windows.Media.Animation.Timeline> des animations et autres objets.  
  
<a name="prerequisites"></a>
## <a name="prerequisites"></a>Conditions préalables requises  
 Pour comprendre cette rubrique, vous devez connaître les fonctionnalités de base utilisées pour l’animation. Pour plus d’informations, voir [l’Aperçu de l’animation](animation-overview.md).  
  
<a name="timelinetypes"></a>
## <a name="timeline-types"></a>Types de chronologie  
 A <xref:System.Windows.Media.Animation.Timeline> représente un segment de temps. Elle fournit des propriétés qui vous permettent de spécifier la longueur de ce segment, le moment où il doit démarrer, combien de fois il doit se répéter, à quelle vitesse le temps s’écoule dans ce segment et bien plus encore.  
  
 Les classes qui héritent de la classe de chronologie fournissent des fonctionnalités supplémentaires, comme la lecture de médias et d’animations. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]fournit les <xref:System.Windows.Media.Animation.Timeline> types suivants.  
  
|Type de chronologie|Description|  
|-------------------|-----------------|  
|<xref:System.Windows.Media.Animation.AnimationTimeline>|Classe de <xref:System.Windows.Media.Animation.Timeline> base abstraite pour les objets qui génèrent des valeurs de sortie pour l’animation des propriétés.|  
|<xref:System.Windows.Media.MediaTimeline>|Génère une sortie à partir d’un fichier multimédia.|  
|<xref:System.Windows.Media.Animation.ParallelTimeline>|Un type <xref:System.Windows.Media.Animation.TimelineGroup> de ce <xref:System.Windows.Media.Animation.Timeline> groupe et contrôle les objets pour enfants.|  
|<xref:System.Windows.Media.Animation.Storyboard>|Un type <xref:System.Windows.Media.Animation.ParallelTimeline> qui fournit des informations de ciblage pour les objets Timeline qu’il contient.|  
|<xref:System.Windows.Media.Animation.Timeline>|Classe de base abstraite qui définit les comportements de minutage.|  
|<xref:System.Windows.Media.Animation.TimelineGroup>|Classe abstraite pour <xref:System.Windows.Media.Animation.Timeline> les <xref:System.Windows.Media.Animation.Timeline> objets qui peuvent contenir d’autres objets.|  
  
<a name="propertiesthatcontroltimelinelength"></a>
## <a name="properties-that-control-the-length-of-a-timeline"></a>Propriétés qui contrôlent la longueur d’une chronologie  
 A <xref:System.Windows.Media.Animation.Timeline> représente un segment de temps, et la durée d’une chronologie peut être décrite de différentes façons. Le tableau suivant définit plusieurs termes servant à décrire la longueur d’une chronologie.  
  
|Terme|Description|Propriétés||||  
|----------|-----------------|----------------|-|-|-|  
|Durée simple|Le temps qu’une chronologie prend pour faire une seule itération vers l’avant.|<xref:System.Windows.Media.Animation.Timeline.Duration%2A>||||  
|Une répétition|La durée du temps qu’il faut pour qu’une chronologie joue vers l’avant une fois et, si la <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> propriété est vraie, jouer à l’envers une fois.|<xref:System.Windows.Media.Animation.Timeline.Duration%2A>, <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>||||  
|Période active|Le temps qu’il faut pour un calendrier pour <xref:System.Windows.Media.Animation.RepeatBehavior> compléter toutes les répétitions spécifiées par sa propriété.|<xref:System.Windows.Media.Animation.Timeline.Duration%2A>, <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>, <xref:System.Windows.Media.Animation.RepeatBehavior>||||  
  
<a name="duration"></a>
### <a name="the-duration-property"></a>La propriété Duration  
 Comme indiqué plus haut, une chronologie représente un segment de temps. La longueur de ce segment est <xref:System.Windows.Media.Animation.Timeline.Duration%2A>déterminée par la chronologie . Lorsqu’une chronologie atteint la fin de sa durée, elle s’arrête. Si la chronologie a des chronologies enfants, celles-ci s’arrêtent également. Dans le cas d’une animation, l’animation <xref:System.Windows.Media.Animation.Timeline.Duration%2A> précise combien de temps l’animation prend pour passer de sa valeur de départ à sa valeur de fin. La durée d’une chronologie est parfois appelée sa *durée simple,* pour distinguer entre la durée d’une seule itération et la durée totale de l’animation joue, y compris les répétitions. Vous pouvez spécifier une durée en <xref:System.Windows.Duration.Automatic%2A> utilisant <xref:System.Windows.Duration.Forever%2A>une valeur de temps finie ou les valeurs spéciales ou . La durée d’une animation <xref:System.Windows.Duration.TimeSpan%2A> doit se résoudre à une valeur, de sorte qu’elle peut passer d’une valeur à l’autre.  
  
 L’exemple suivant <xref:System.Windows.Media.Animation.DoubleAnimation> montre <xref:System.Windows.Media.Animation.Timeline.Duration%2A> un avec un de cinq secondes.  
  
 [!code-xaml[animation_ovws_snippet#AnimationWith5SecondDurationInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#animationwith5seconddurationinline)]  
  
 Les délais de <xref:System.Windows.Media.Animation.Storyboard> conteneurs, tels que et, <xref:System.Windows.Media.Animation.ParallelTimeline>ont une durée par défaut de , ce qui signifie qu’ils <xref:System.Windows.Duration.Automatic%2A>se terminent automatiquement lorsque leur dernier enfant cesse de jouer. L’exemple suivant <xref:System.Windows.Media.Animation.Storyboard> <xref:System.Windows.Media.Animation.Timeline.Duration%2A> montre un dont la résolution à cinq secondes, la durée qu’il faut à tous ses objets pour enfants. <xref:System.Windows.Media.Animation.DoubleAnimation>  
  
 [!code-xaml[animation_ovws_snippet#ContainerTimelineExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#containertimelineexampleinline)]  
  
 En définissant la <xref:System.Windows.Media.Animation.Timeline.Duration%2A> chronologie <xref:System.Windows.Duration.TimeSpan%2A> d’un conteneur à une valeur, <xref:System.Windows.Media.Animation.Timeline> vous pouvez forcer à jouer plus longtemps ou moins que ses objets d’enfant joueraient. Si vous <xref:System.Windows.Media.Animation.Timeline.Duration%2A> définissez la valeur qui est plus petite que <xref:System.Windows.Media.Animation.Timeline> la longueur <xref:System.Windows.Media.Animation.Timeline> des objets pour enfants de la chronologie du conteneur, les objets de l’enfant cessent de jouer lorsque la chronologie du conteneur le fait. L’exemple suivant <xref:System.Windows.Media.Animation.Timeline.Duration%2A> définit <xref:System.Windows.Media.Animation.Storyboard> les exemples précédents à trois secondes. En conséquence, les <xref:System.Windows.Media.Animation.DoubleAnimation> premiers arrêts progressent après trois secondes, quand il a animé la largeur du rectangle cible à 60.  
  
 [!code-xaml[animation_ovws_snippet#ContainerTimelineWithShorterDurationExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#containertimelinewithshorterdurationexampleinline)]  
  
<a name="repeatinganimations"></a>
### <a name="the-repeatbehavior-property"></a>La propriété RepeatBehavior  
 La <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> propriété <xref:System.Windows.Media.Animation.Timeline> d’un contrôle combien de fois il répète sa durée simple. En <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> utilisant la propriété, vous pouvez spécifier <xref:System.Windows.Media.Animation.RepeatBehavior.Count%2A>combien de fois la chronologie joue (une itération ) ou la durée totale de jeu (une répétition <xref:System.Windows.Media.Animation.RepeatBehavior.Duration%2A>). Dans les deux cas, l’animation se répète de bout en bout autant de fois qu’il est nécessaire pour respecter la durée ou le nombre imposés. Par défaut, les délais ont un `1.0`nombre d’itération de , ce qui signifie qu’ils jouent une fois et ne répètent pas du tout.  
  
 L’exemple suivant <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> utilise la <xref:System.Windows.Media.Animation.DoubleAnimation> propriété pour faire un jeu pour deux fois sa durée simple en spécifiant un nombre d’itération.  
  
 [!code-xaml[animation_ovws_snippet#TBRepeatBehavior2xExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbrepeatbehavior2xexampleinline)]  
  
 L’exemple suivant <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> utilise la <xref:System.Windows.Media.Animation.DoubleAnimation> propriété pour faire le jeu pour la moitié de sa durée simple.  
  
 [!code-xaml[animation_ovws_snippet#TBRepeatBehavior05xExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbrepeatbehavior05xexampleinline)]  
  
 Si vous <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> définissez <xref:System.Windows.Media.Animation.Timeline> la <xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>propriété <xref:System.Windows.Media.Animation.Timeline> d’un à , les répétitions jusqu’à ce qu’ils soient arrêtés de manière interactive ou par le système de chronométrage. L’exemple suivant <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> utilise la <xref:System.Windows.Media.Animation.DoubleAnimation> propriété pour faire la pièce indéfiniment.  
  
 [!code-xaml[animation_ovws_snippet#TBRepeatBehaviorForeverExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbrepeatbehaviorforeverexampleinline)]  
  
 Pour un autre exemple, voir [Répéter une animation](how-to-repeat-an-animation.md).  
  
<a name="autoreverseproperty"></a>
### <a name="the-autoreverse-property"></a>La propriété AutoReverse  
 La <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> propriété précise si <xref:System.Windows.Media.Animation.Timeline> un jeu à l’envers à la fin de chaque itération vers l’avant. L’exemple suivant <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> donne à <xref:System.Windows.Media.Animation.DoubleAnimation> `true`la propriété d’un à ; en conséquence, il anime de zéro à 100, puis de 100 à zéro. Elle s’exécute pendant 10 secondes au total.  
  
 [!code-xaml[animation_ovws_snippet#TBAutoReverseExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbautoreverseexampleinline)]  
  
 Lorsque vous <xref:System.Windows.Media.Animation.RepeatBehavior.Count%2A> utilisez une <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> valeur <xref:System.Windows.Media.Animation.Timeline> pour <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> spécifier le d’un et la propriété de cela <xref:System.Windows.Media.Animation.Timeline> est `true`, une seule répétition se compose d’une itération vers l’avant suivie d’une itération vers l’arrière.  L’exemple suivant <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> définit <xref:System.Windows.Media.Animation.DoubleAnimation> l’exemple précédent <xref:System.Windows.Media.Animation.RepeatBehavior.Count%2A> à un de deux. En conséquence, <xref:System.Windows.Media.Animation.DoubleAnimation> les jeux pendant 20 secondes: en avant pendant cinq secondes, en arrière pendant cinq secondes, en avant pendant 5 secondes à nouveau, puis à l’envers pendant cinq secondes.  
  
 [!code-xaml[animation_ovws_snippet#TBAutoReverseRepeatExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbautoreverserepeatexampleinline)]  
  
 Si une chronologie <xref:System.Windows.Media.Animation.Timeline> de conteneur a des objets d’enfant, ils s’inversent lorsque la chronologie du conteneur le fait. Pour d’autres exemples, voir [spécifier si une chronologie s’inverse automatiquement](how-to-specify-whether-a-timeline-automatically-reverses.md).  
  
<a name="timelinebegin"></a>
## <a name="the-begintime-property"></a>La propriété BeginTime  
 La <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> propriété vous permet de spécifier quand une chronologie commence.  Le temps de début d’une chronologie est relatif à la chronologie de son parent. Un temps de début de zéro seconde signifie que la chronologie démarre dès que son parent démarre ; toute autre valeur crée un décalage entre le démarrage de la chronologie parent et celui de la chronologie enfant. Par exemple, un temps de début de deux secondes signifie que la chronologie démarre quand son parent a atteint une durée de deux secondes. Par défaut, toutes les chronologies ont un temps de début de zéro seconde. Vous pouvez également définir l’heure `null`de début d’une chronologie à , ce qui empêche la chronologie de commencer. Dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], vous spécifiez nul en utilisant [l’extension de balisage x:Null](../../../desktop-wpf/xaml-services/xnull-markup-extension.md).  
  
 Notez que l’heure de début n’est <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> pas appliquée chaque fois qu’une chronologie se répète en raison de son réglage. Si vous devait créer <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> une animation avec un <xref:System.Windows.Media.Animation.RepeatBehavior> <xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>de 10 secondes et un de , il y aurait un délai de 10 secondes avant l’animation jouée pour la première fois, mais pas pour chaque répétition successive. Toutefois, si la chronologie du parent de l’animation devait redémarrer ou se répéter, le délai de 10 secondes se produirait.  
  
 La <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> propriété est utile pour les chronologies stupéfiantes. L’exemple suivant <xref:System.Windows.Media.Animation.Storyboard> crée un <xref:System.Windows.Media.Animation.DoubleAnimation> qui a deux objets pour enfants. La première animation <xref:System.Windows.Media.Animation.Timeline.Duration%2A> a une de cinq <xref:System.Windows.Media.Animation.Timeline.Duration%2A> secondes, et la seconde a un de 3 secondes. L’exemple <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> définit la <xref:System.Windows.Media.Animation.DoubleAnimation> seconde à 5 secondes, de <xref:System.Windows.Media.Animation.DoubleAnimation> sorte qu’il commence à jouer après les premières extrémités.  
  
 [!code-xaml[animation_ovws_snippet#TBBeginTimeExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbbegintimeexampleinline)]  
  
<a name="fillbehaviorproperty"></a>
## <a name="the-fillbehavior-property"></a>La propriété FillBehavior  
 Lorsqu’une limite <xref:System.Windows.Media.Animation.Timeline> totale de sa <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> durée active atteint la fin de sa durée totale, la propriété précise si elle s’arrête ou détient sa dernière valeur. Une animation <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> avec <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd> un de "holds" sa valeur de sortie: la propriété animée conserve la dernière valeur de l’animation. Une valeur <xref:System.Windows.Media.Animation.FillBehavior.Stop> de causes que l’animation cesse d’affecter sa propriété cible après sa fin.  
  
 L’exemple suivant <xref:System.Windows.Media.Animation.Storyboard> crée un <xref:System.Windows.Media.Animation.DoubleAnimation> qui a deux objets pour enfants. Les <xref:System.Windows.Media.Animation.DoubleAnimation> deux objets <xref:System.Windows.FrameworkElement.Width%2A> animent <xref:System.Windows.Shapes.Rectangle> le de 0 à 100. Les <xref:System.Windows.Shapes.Rectangle> éléments ont <xref:System.Windows.FrameworkElement.Width%2A> des valeurs non-animées de 500 [pixels indépendants de l’appareil].  
  
- La <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> propriété de <xref:System.Windows.Media.Animation.DoubleAnimation> la <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>première est définie à , la valeur par défaut. En conséquence, la largeur du rectangle reste à <xref:System.Windows.Media.Animation.DoubleAnimation> 100 après la fin.  
  
- La <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> propriété de <xref:System.Windows.Media.Animation.DoubleAnimation> la <xref:System.Windows.Media.Animation.FillBehavior.Stop>seconde est réglée à . En conséquence, <xref:System.Windows.FrameworkElement.Width%2A> le second <xref:System.Windows.Shapes.Rectangle> revient à 500 après la <xref:System.Windows.Media.Animation.DoubleAnimation> fin.  
  
 [!code-xaml[animation_ovws_snippet#TBFillBehaviorExample](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbfillbehaviorexample)]  
  
<a name="speedproperties"></a>
## <a name="properties-that-control-the-speed-of-a-timeline"></a>Propriétés qui contrôlent la vitesse d’une chronologie  
 La <xref:System.Windows.Media.Animation.Timeline> classe fournit trois propriétés pour spécifier sa vitesse :  
  
- <xref:System.Windows.Media.Animation.Timeline.SpeedRatio%2A>- Précise ce taux, par rapport à son parent, <xref:System.Windows.Media.Animation.Timeline>à ce moment-là progresse pour un . Des valeurs supérieures à une <xref:System.Windows.Media.Animation.Timeline> augmentent <xref:System.Windows.Media.Animation.Timeline> la vitesse des objets et de ses objets pour enfants; valeurs entre zéro et un le ralentir. Une valeur de <xref:System.Windows.Media.Animation.Timeline> l’un indique que progresse au même rythme que son parent. Le <xref:System.Windows.Media.Animation.Timeline.SpeedRatio%2A> réglage d’une chronologie des <xref:System.Windows.Media.Animation.Timeline> conteneurs affecte également tous ses objets pour enfants.  
  
- <xref:System.Windows.Media.Animation.Timeline.AccelerationRatio%2A>Specifie le pourcentage <xref:System.Windows.Media.Animation.Timeline.Duration%2A> de la chronologie passée à accélérer. Par exemple, voir [Comment : Accélérer ou décélérer une animation.](how-to-accelerate-or-decelerate-an-animation.md)
  
- <xref:System.Windows.Media.Animation.Timeline.DecelerationRatio%2A>- Précise le pourcentage <xref:System.Windows.Media.Animation.Timeline.Duration%2A> de la chronologie passée à décélérer. Par exemple, voir [Comment : Accélérer ou décélérer une animation.](how-to-accelerate-or-decelerate-an-animation.md)  
  
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble de l’animation](animation-overview.md)
- [Vue d’ensemble de l'animation et du système de minutage](animation-and-timing-system-overview.md)
- [Vue d'ensemble des événements de minutage](timing-events-overview.md)
- [Sujets comment se passer](animation-and-timing-how-to-topics.md)
- [Comportement de minuterie d’animation exemple](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/AnimationTiming)
