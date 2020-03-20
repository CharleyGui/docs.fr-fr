---
title: Vue d'ensemble de l'animation et du système de minutage
ms.date: 03/30/2017
helpviewer_keywords:
- timing system [WPF]
- animation [WPF]
ms.assetid: 172cd5a8-a333-4c81-9456-fafccc19f382
ms.openlocfilehash: d0ac2a8160a1e6f9bcdb333593ec207954b391aa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187717"
---
# <a name="animation-and-timing-system-overview"></a>Vue d'ensemble de l'animation et du système de minutage
Ce sujet décrit comment le système <xref:System.Windows.Media.Animation.Timeline>de <xref:System.Windows.Media.Animation.Clock> chronométrage utilise l’animation, et les classes pour animer les propriétés.  
  
<a name="prerequisites"></a>
## <a name="prerequisites"></a>Conditions préalables requises  
 Pour comprendre cette rubrique, vous devez être en mesure d’utiliser des animations [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pour animer des propriétés, comme décrit dans la [Vue d’ensemble de l’animation](animation-overview.md). Il est également conseillé de vous familiariser avec les propriétés de dépendance. Pour plus d’informations, consultez [Vue d’ensemble des propriétés de dépendance](../advanced/dependency-properties-overview.md).  
  
<a name="timelinesandclocks"></a>
## <a name="timelines-and-clocks"></a>Chronologies et horloges  
 [L’Aperçu d’animation](animation-overview.md) décrit comment un <xref:System.Windows.Media.Animation.Timeline> segment de temps <xref:System.Windows.Media.Animation.Timeline> représente un segment de temps, et une animation est un type qui produit des valeurs de sortie. En soi, <xref:System.Windows.Media.Animation.Timeline>a , ne fait rien d’autre que de simplement décrire un segment de temps. C’est l’objet <xref:System.Windows.Media.Animation.Clock> de la chronologie qui fait le vrai travail. De même, l’animation n’anime pas réellement les propriétés : une classe d’animation décrit comment les valeurs de sortie doivent être calculées, mais c’est ce <xref:System.Windows.Media.Animation.Clock> qui a été créé pour l’animation qui anime la sortie d’animation et l’applique aux propriétés.  
  
 A <xref:System.Windows.Media.Animation.Clock> est un type spécial d’objet qui maintient l’état de temps de course lié au calendrier pour le <xref:System.Windows.Media.Animation.Timeline>. Il fournit trois bits d’informations qui sont <xref:System.Windows.Media.Animation.Clock.CurrentTime%2A>essentiels au système d’animation et de synchronisation: , <xref:System.Windows.Media.Animation.Clock.CurrentProgress%2A>, et <xref:System.Windows.Media.Animation.Clock.CurrentState%2A>. A <xref:System.Windows.Media.Animation.Clock> détermine son temps actuel, ses progrès et son état <xref:System.Windows.Media.Animation.Timeline> <xref:System.Windows.Media.Animation.Timeline.Duration%2A>en <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>utilisant les comportements de chronométrage décrits par son : , , et ainsi de suite.  
  
 Dans la plupart <xref:System.Windows.Media.Animation.Clock> des cas, un est créé automatiquement pour votre journal. Lorsque vous animez en <xref:System.Windows.Media.Animation.Storyboard> utilisant <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> un ou la méthode, les horloges sont automatiquement créées pour vos chronologies et animations et appliquées à leurs propriétés ciblées. Vous pouvez également <xref:System.Windows.Media.Animation.Clock> créer un <xref:System.Windows.Media.Animation.Timeline.CreateClock%2A> explicitement <xref:System.Windows.Media.Animation.Timeline>en utilisant la méthode de votre . La <xref:System.Windows.Media.MediaTimeline.CreateClock%2A?displayProperty=nameWithType> méthode crée une horloge du <xref:System.Windows.Media.Animation.Timeline> type approprié pour laquelle elle est appelée. Si <xref:System.Windows.Media.Animation.Timeline> le contient des chronologies pour enfants, il crée des <xref:System.Windows.Media.Animation.Clock> objets pour eux aussi. Les <xref:System.Windows.Media.Animation.Clock> objets qui en résultent sont <xref:System.Windows.Media.Animation.Timeline> disposés dans des arbres qui correspondent à la structure de l’arbre d’objets à partir duquel ils sont créés.  
  
 Il existe différents types d’horloges pour différents types de chronologies. Le tableau suivant <xref:System.Windows.Media.Animation.Clock> montre les types qui <xref:System.Windows.Media.Animation.Timeline> correspondent à certains des différents types.  
  
|Type de chronologie|Type d’horloge|Objectif de l’horloge|  
|-------------------|----------------|-------------------|  
|Animation (hérite <xref:System.Windows.Media.Animation.AnimationTimeline>de )|<xref:System.Windows.Media.Animation.AnimationClock>|Génère les valeurs de sortie d’une propriété de dépendance.|  
|<xref:System.Windows.Media.MediaTimeline>|<xref:System.Windows.Media.MediaClock>|Traite un fichier multimédia.|  
|<xref:System.Windows.Media.Animation.ParallelTimeline>|<xref:System.Windows.Media.Animation.ClockGroup>|Regroupe et contrôle <xref:System.Windows.Media.Animation.Clock> ses objets pour enfants|  
|<xref:System.Windows.Media.Animation.Storyboard>|<xref:System.Windows.Media.Animation.ClockGroup>|Regroupe et contrôle <xref:System.Windows.Media.Animation.Clock> ses objets pour enfants|  
  
 Vous pouvez <xref:System.Windows.Media.Animation.AnimationClock> appliquer tous les objets que <xref:System.Windows.Media.Animation.IAnimatable.ApplyAnimationClock%2A> vous créez à des propriétés de dépendance compatibles en utilisant la méthode.  
  
 Dans les scénarios à forte intensité de performances, tels que <xref:System.Windows.Media.Animation.Clock> l’animation d’un grand nombre d’objets similaires, la gestion de votre propre utilisation peut fournir des avantages de performance.  
  
<a name="timemanager"></a>
## <a name="clocks-and-the-time-manager"></a>Horloges et gestionnaire de temps  
 Lorsque vous animez [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]des objets dans , c’est le gestionnaire de temps qui gère les <xref:System.Windows.Media.MediaPlayer.Clock%2A> objets créés pour vos chronologies. Le gestionnaire de temps est la racine d’une arborescence d’objets <xref:System.Windows.Media.MediaPlayer.Clock%2A> et contrôle le flux de temps dans cette arborescence.  Un gestionnaire de temps est créé automatiquement pour chaque application [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] et reste invisible au développeur d'applications. Le gestionnaire de temps a de nombreuses graduations par seconde. Le nombre réel de cycles qui se produisent à chaque seconde varie selon les ressources système disponibles. Au cours de chacune de ces tiques, le <xref:System.Windows.Media.Animation.ClockState.Active> <xref:System.Windows.Media.Animation.Clock> gestionnaire de temps calcule l’état de tous les objets dans l’arbre de chronométrage.  
  
 L’illustration suivante montre la relation <xref:System.Windows.Media.Animation.AnimationClock>entre le gestionnaire de temps, et , et une propriété de dépendance animée.  
  
 ![Composants du système de minutage](./media/graphicsmm-clocks-1clock1prop.png "graphicsmm_clocks_1clock1prop")  
Animation d’une propriété  
  
 Lorsque le gestionnaire de temps tic-tac, il met à jour le temps de chaque <xref:System.Windows.Media.Animation.ClockState.Active> <xref:System.Windows.Media.Animation.Clock> dans l’application. Si <xref:System.Windows.Media.Animation.Clock> le <xref:System.Windows.Media.Animation.AnimationClock>est un <xref:System.Windows.Media.Animation.AnimationTimeline.GetCurrentValue%2A> , il <xref:System.Windows.Media.Animation.AnimationTimeline> utilise la méthode de la à partir de laquelle il a été créé pour calculer sa valeur de sortie actuelle. Le <xref:System.Windows.Media.Animation.AnimationClock> fournit <xref:System.Windows.Media.Animation.AnimationTimeline> l’heure locale actuelle, une valeur d’entrée, qui est généralement la valeur de base de la propriété, et une valeur de destination par défaut. Lorsque vous récupérez la valeur d’un animé par propriété en utilisant <xref:System.Windows.DependencyObject.GetValue%2A> la <xref:System.Windows.Media.Animation.AnimationClock>méthode ou son accesseur CLR, vous obtenez la sortie de son .  
  
#### <a name="clock-groups"></a>Groupes d’horloges  
 La section précédente décrivait comment <xref:System.Windows.Media.Animation.Clock> il existe différents types d’objets pour différents types de calendriers. L’illustration suivante montre la relation <xref:System.Windows.Media.Animation.ClockGroup>entre <xref:System.Windows.Media.Animation.AnimationClock>le gestionnaire de temps, un , un , et une propriété de dépendance animée. A <xref:System.Windows.Media.Animation.ClockGroup> est créé pour les calendriers qui <xref:System.Windows.Media.Animation.Storyboard> regroupent d’autres calendriers, tels que la classe, qui regroupe les animations et autres calendriers.  
  
 ![Composants du système de minutage](./media/graphicsmm-clocks-2clock1clockgroup2prop.png "graphicsmm_clocks_2clock1clockgroup2prop")  
Un groupe d’horloges  
  
#### <a name="composition"></a>Composition  
 Il est possible d’associer plusieurs horloges à une seule propriété, auquel cas chaque l’horloge utilise la valeur de sortie de l’exemple d’horloge précédent comme valeur de base. L’illustration suivante <xref:System.Windows.Media.Animation.AnimationClock> montre trois objets appliqués à la même propriété. Clock1 utilise la valeur de base de la propriété animée comme entrée et l’utilise pour générer la sortie. Clock2 prend la sortie de Clock1 comme entrée et l’utilise pour générer la sortie. Clock3 prend la sortie de Clock2 comme entrée et l’utilise pour générer la sortie. Lorsque plusieurs horloges affectent la même propriété simultanément, on dit qu’elles font partie d’une chaîne de composition.  
  
 ![Composants du système de minutage](./media/graphicsmm-clocks-2clock1prop.png "graphicsmm_clocks_2clock1prop")  
Une chaîne de composition  
  
 Notez que bien qu’une relation soit <xref:System.Windows.Media.Animation.AnimationClock> créée entre l’entrée et la sortie des objets de la chaîne de composition, leurs comportements de synchronisation ne sont pas affectés ; <xref:System.Windows.Media.Animation.Clock> (y <xref:System.Windows.Media.Animation.AnimationClock> compris les objets) ont une <xref:System.Windows.Media.Animation.Clock> dépendance hiérarchique vis-à-vis de leurs objets parents.  
  
 Pour appliquer plusieurs horloges sur la <xref:System.Windows.Media.Animation.HandoffBehavior.Compose> <xref:System.Windows.Media.Animation.HandoffBehavior> même <xref:System.Windows.Media.Animation.Storyboard>propriété, utilisez <xref:System.Windows.Media.Animation.AnimationClock>le lors de l’application d’un , animation, ou .  
  
#### <a name="ticks-and-event-consolidation"></a>Graduations et consolidation des événements  
 En plus du calcul des valeurs de sortie, le gestionnaire de temps effectue un autre travail à chaque graduation : il détermine l’état de chaque horloge et déclenche des événements comme il convient.  
  
 Étant donné que ces cycles sont fréquents, beaucoup de choses peuvent se passer entre chaque cycle. Par exemple, <xref:System.Windows.Media.Animation.Clock> un peut être arrêté, commencé et <xref:System.Windows.Media.Animation.Clock.CurrentState%2A> arrêté à nouveau, auquel cas sa valeur aura changé trois fois. En théorie, <xref:System.Windows.Media.Animation.Clock.CurrentStateInvalidated> l’événement pourrait être soulevé plusieurs fois en une seule tique; cependant, le moteur de chronométrage <xref:System.Windows.Media.Animation.Clock.CurrentStateInvalidated> consolide les événements, de sorte que l’événement peut être soulevé au plus une fois par tique. Cela est vrai pour tous les événements de chronométrage: <xref:System.Windows.Media.Animation.Clock> tout au plus un événement de chaque type est soulevé pour un objet donné.  
  
 Lorsqu’un <xref:System.Windows.Media.Animation.Clock> commutateur indique et retourne à son état d’origine entre les tiques (comme le passage de <xref:System.Windows.Media.Animation.ClockState.Active> et <xref:System.Windows.Media.Animation.ClockState.Stopped> de retour à <xref:System.Windows.Media.Animation.ClockState.Active>), l’événement associé se produit toujours.  
  
 Pour plus d'informations sur les événements de minuterie, consultez [Vue d'ensemble des événements de minuterie](timing-events-overview.md).  
  
<a name="currentvaluesbasevaluesofproperties"></a>
## <a name="current-values-and-base-values-of-properties"></a>Valeurs actuelles et les valeurs de base des propriétés  
 Une propriété pouvant être animée peut avoir deux valeurs : une valeur de base et une valeur actuelle. Lorsque vous définissez la propriété à <xref:System.Windows.DependencyObject.SetValue%2A> l’aide de son accesseur CLR ou de la méthode, vous définissez sa valeur de base. Lorsqu’une propriété n’est pas animée, ses valeurs de base et actuelles sont identiques.  
  
 Lorsque vous animez une <xref:System.Windows.Media.Animation.AnimationClock> propriété, la valeur actuelle de la propriété définit la valeur *actuelle* de la propriété. La récupération de la valeur de la propriété par <xref:System.Windows.DependencyObject.GetValue%2A> l’intermédiaire de <xref:System.Windows.Media.Animation.AnimationClock> son <xref:System.Windows.Media.Animation.AnimationClock> <xref:System.Windows.Media.Animation.ClockState.Active> accesseur CLR ou de la méthode renvoie la sortie du moment où le est ou <xref:System.Windows.Media.Animation.ClockState.Filling>. Vous pouvez récupérer la valeur de <xref:System.Windows.Media.Animation.IAnimatable.GetAnimationBaseValue%2A> base de la propriété en utilisant la méthode.  
  
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble de l’animation](animation-overview.md)
- [Vue d'ensemble des événements de minutage](timing-events-overview.md)
- [Vue d'ensemble des comportements de minutage](timing-behaviors-overview.md)
