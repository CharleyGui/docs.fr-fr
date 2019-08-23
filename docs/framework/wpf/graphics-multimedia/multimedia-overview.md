---
title: Vue d'ensemble du multimédia
ms.date: 03/30/2017
helpviewer_keywords:
- multimedia [WPF]
- media [WPF]
ms.assetid: feb25b15-d741-4ac3-818f-1b19f63a3562
ms.openlocfilehash: 44059fe96a0deeda18f0abd9079100b55be98e77
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929619"
---
# <a name="multimedia-overview"></a>Vue d'ensemble du multimédia
Les fonctionnalités multimédias de [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] permettent d’intégrer des données audio et vidéo dans vos applications afin d’améliorer l’expérience utilisateur. Cette rubrique présente les fonctionnalités multimédias de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  

<a name="mediaapi"></a>   
## <a name="media-api"></a>API Media  
 Les <xref:System.Windows.Controls.MediaElement> classes <xref:System.Windows.Media.MediaPlayer> et sont utilisées pour présenter le contenu audio ou vidéo. Ces classes peuvent être contrôlées interactivement ou par une horloge. Ces classes peuvent être utilisées sur le contrôle [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)] 10 pour la lecture multimédia. La classe que vous allez utiliser dépend du scénario.  
  
 <xref:System.Windows.Controls.MediaElement>est un <xref:System.Windows.UIElement> qui est pris en charge par la [disposition](../advanced/layout.md) et qui peut être consommé en tant que contenu de nombreux contrôles. Il est également utilisable en langage [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] ainsi que dans du code. <xref:System.Windows.Media.MediaPlayer>en revanche, est conçu pour <xref:System.Windows.Media.Drawing> les objets et ne prend pas en charge la disposition. Le support chargé à <xref:System.Windows.Media.MediaPlayer> l’aide d’un ne peut <xref:System.Windows.Media.VideoDrawing> être présenté qu’à l’aide d' <xref:System.Windows.Media.DrawingContext>un ou en interagissant directement avec un. <xref:System.Windows.Media.MediaPlayer>ne peut pas être utilisé en XAML.  
  
 Pour plus d’informations sur les objets de dessin et le contexte de dessin, consultez [Vue d’ensemble des objets Drawing](drawing-objects-overview.md).  
  
> [!NOTE]
> Lorsque vous distribuez un contenu multimédia avec votre application, vous ne pouvez pas utiliser de fichier multimédia comme ressource de projet. Dans votre fichier projet, vous devez plutôt définir le type de média sur `Content` et définir `CopyToOutputDirectory` sur `PreserveNewest` ou `Always`.  
  
<a name="mediaplaybackmodes"></a>   
## <a name="media-playback-modes"></a>Modes de lecture de médias  
  
> [!NOTE]
> <xref:System.Windows.Controls.MediaElement> Et<xref:System.Windows.Media.MediaPlayer> ont des membres similaires. Les liens de cette section font référence aux <xref:System.Windows.Controls.MediaElement> membres de la classe. Sauf mention spécifique, les membres liés dans la <xref:System.Windows.Controls.MediaElement> classe peuvent également être trouvés dans la <xref:System.Windows.Media.MediaPlayer> classe.  
  
 Pour comprendre la lecture de médias dans [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], il est nécessaire de comprendre les différents modes de lecture des médias. <xref:System.Windows.Controls.MediaElement> Et<xref:System.Windows.Media.MediaPlayer> peuvent être utilisés dans deux modes de média différents, en mode indépendant et en mode horloge. Le mode de média est déterminé par <xref:System.Windows.Controls.MediaElement.Clock%2A> la propriété. Lorsque <xref:System.Windows.Controls.MediaElement.Clock%2A> est`null`, l’objet multimédia est en mode indépendant. Lorsque la <xref:System.Windows.Controls.MediaElement.Clock%2A> valeur n’est pas null, l’objet média est en mode horloge. Par défaut, les objets médias sont en mode indépendant.  
  
### <a name="independent-mode"></a>Mode indépendant  
 En mode indépendant, le contenu du média déclenche la lecture du média. Le mode indépendant comprend les options suivantes :  
  
- Les éléments multimédias peuvent être spécifiés directement. <xref:System.Uri>  
  
- La lecture du média peut être directement contrôlée.  
  
- Les propriétés et <xref:System.Windows.Controls.MediaElement.SpeedRatio%2A> le média peuvent être modifiés. <xref:System.Windows.Controls.MediaElement.Position%2A>  
  
 Le média est chargé en définissant <xref:System.Windows.Controls.MediaElement> la propriété <xref:System.Windows.Controls.MediaElement.Source%2A> de l’objet ou en <xref:System.Windows.Media.MediaPlayer> appelant la <xref:System.Windows.Media.MediaPlayer.Open%2A> méthode de l’objet.  
  
 Pour contrôler la lecture du média en mode indépendant, les méthodes de contrôle de l’objet média peuvent être utilisées. Les méthodes de contrôle disponibles <xref:System.Windows.Controls.MediaElement.Play%2A>sont <xref:System.Windows.Controls.MediaElement.Pause%2A>, <xref:System.Windows.Controls.MediaElement.Close%2A>, et <xref:System.Windows.Controls.MediaElement.Stop%2A>. Pour <xref:System.Windows.Controls.MediaElement>, le contrôle interactif à l’aide de ces méthodes est <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> disponible uniquement lorsque <xref:System.Windows.Controls.MediaState.Manual>a la valeur. Ces méthodes ne sont pas disponibles lorsque l’objet média est en mode horloge.  
  
 Consultez la page [Contrôler un MediaElement (lecture, pause, arrêt, volume et vitesse)](how-to-control-a-mediaelement-play-pause-stop-volume-and-speed.md) pour obtenir un exemple de mode indépendant.  
  
### <a name="clock-mode"></a>Mode horloge  
 En mode horloge, un <xref:System.Windows.Media.MediaTimeline> lecteur de média est lu. Le mode horloge présente les caractéristiques suivantes :  
  
- Le média <xref:System.Windows.Media.MediaTimeline>est défini indirectement via un. <xref:System.Uri>  
  
- La lecture du média peut être contrôlée par l’horloge. Les méthodes de contrôle de l’objet média ne peuvent pas être utilisées.  
  
- Le média est chargé en définissant la <xref:System.Windows.Media.MediaTimeline.Source%2A> propriété d’un <xref:System.Windows.Media.MediaTimeline> objet, en créant l’horloge à partir de la chronologie et en assignant l’horloge à l’objet multimédia. Le média est également chargé de cette façon <xref:System.Windows.Media.MediaTimeline> quand un <xref:System.Windows.Media.Animation.Storyboard> dans un <xref:System.Windows.Controls.MediaElement>cible un.  
  
 Pour contrôler la lecture du média en mode horloge <xref:System.Windows.Media.Animation.ClockController> , vous devez utiliser les méthodes de contrôle. Un <xref:System.Windows.Media.Animation.ClockController> est obtenu à partir <xref:System.Windows.Media.Animation.ClockController> de la propriété <xref:System.Windows.Media.MediaClock>de. Si vous tentez d’utiliser les méthodes de contrôle d' <xref:System.Windows.Controls.MediaElement> un <xref:System.Windows.Media.MediaPlayer> objet ou en mode horloge, une <xref:System.InvalidOperationException> est levée.  
  
 Pour plus d’informations sur les horloges et les chronologies, consultez l’article [Vue d’ensemble de l’animation](animation-overview.md).  
  
 Pour obtenir un exemple du mode horloge, consultez la page [Contrôler un MediaElement à l’aide d’un Storyboard](how-to-control-a-mediaelement-by-using-a-storyboard.md).  
  
<a name="mediaelement"></a>   
## <a name="mediaelement-class"></a>Classe MediaElement  
 L’ajout d’un média à une application est aussi simple <xref:System.Windows.Controls.MediaElement> que l’ajout [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] d’un contrôle au de l' <xref:System.Uri> application et la fourniture d’un au média que vous souhaitez inclure. Tous les types de média pris en charge par [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)] 10 sont pris en charge dans [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]. L’exemple suivant montre une utilisation simple de <xref:System.Windows.Controls.MediaElement> dans. [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]  
  
 [!code-xaml[MediaElement_snip#SimpleMediaElementUsageWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaElement_snip/CSharp/SimpleUsage.xaml#simplemediaelementusagewholepage)]  
  
 Dans cet exemple, le média est lu automatiquement dès qu’il est chargé. Une fois la lecture du média terminée, le média est fermé et toutes les ressources du média sont libérées (y compris la mémoire vidéo). Il s’agit du comportement par défaut <xref:System.Windows.Controls.MediaElement> de l’objet et est contrôlé <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> par <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> les propriétés et.  
  
### <a name="controlling-a-mediaelement"></a>Contrôler un MediaElement  
 Les <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> propriétés <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> et <xref:System.Windows.FrameworkElement.IsLoaded%2A> `true` contrôlent le comportement de `false`lorsque est ou, respectivement. <xref:System.Windows.Controls.MediaElement> <xref:System.Windows.Controls.MediaState> Les propriétés sont définies de manière à affecter le comportement de lecture du média. Par exemple, la valeur <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> par <xref:System.Windows.Controls.MediaState.Play> défaut est et <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> la <xref:System.Windows.Controls.MediaState.Close>valeur par défaut est. Cela signifie que dès que <xref:System.Windows.Controls.MediaElement> est chargé et que le préroll est terminé, le média commence à fonctionner. Une fois la lecture terminée, le média est fermé et toutes les ressources du média sont libérées.  
  
 Les <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> propriétés <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> et ne sont pas la seule façon de contrôler la lecture du média. En mode horloge, l’horloge peut contrôler <xref:System.Windows.Controls.MediaElement> et les méthodes de contrôle interactives contrôlent le <xref:System.Windows.Controls.MediaState.Manual> <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> moment où est. <xref:System.Windows.Controls.MediaElement>gère ce concours pour le contrôle en évaluant les priorités suivantes.  
  
1. <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A>. Actif lorsque le média est déchargé. Cela garantit que toutes les ressources de média sont libérées par défaut, <xref:System.Windows.Media.MediaClock> même lorsqu’un est <xref:System.Windows.Controls.MediaElement>associé à.  
  
2. <xref:System.Windows.Media.MediaClock>. En place lorsque le média a <xref:System.Windows.Controls.MediaElement.Clock%2A>un. Si le média est déchargé, le <xref:System.Windows.Media.MediaClock> prend effet tant que le a <xref:System.Windows.Controls.MediaState.Manual>la <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> valeur. Le mode horloge remplace toujours le comportement chargé de <xref:System.Windows.Controls.MediaElement>.  
  
3. <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A>. Actif lorsque le média est chargé.  
  
4. Méthodes de contrôle interactives. Sur place lorsque <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> est <xref:System.Windows.Controls.MediaState.Manual>. Les méthodes de contrôle disponibles <xref:System.Windows.Controls.MediaElement.Play%2A>sont <xref:System.Windows.Controls.MediaElement.Pause%2A>, <xref:System.Windows.Controls.MediaElement.Close%2A>, et <xref:System.Windows.Controls.MediaElement.Stop%2A>.  
  
### <a name="displaying-a-mediaelement"></a>Afficher un MediaElement  
 Pour afficher un <xref:System.Windows.Controls.MediaElement> , il doit disposer d’un contenu à restituer et <xref:System.Windows.FrameworkElement.ActualWidth%2A> ses <xref:System.Windows.FrameworkElement.ActualHeight%2A> propriétés et auront la valeur zéro jusqu’à ce que le contenu soit chargé. Pour du contenu purement audio, ces propriétés sont toujours égales à zéro. Pour le contenu vidéo, lorsque <xref:System.Windows.Controls.MediaElement.MediaOpened> l’événement a été <xref:System.Windows.FrameworkElement.ActualWidth%2A> déclenché et <xref:System.Windows.FrameworkElement.ActualHeight%2A> signale la taille du média chargé. Cela signifie que tant que le média est chargé <xref:System.Windows.Controls.MediaElement> , le n’occupe aucun espace physique dans le [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] , sauf <xref:System.Windows.FrameworkElement.Width%2A> si <xref:System.Windows.FrameworkElement.Height%2A> les propriétés ou sont définies.  
  
 La définition des <xref:System.Windows.FrameworkElement.Width%2A> propriétés <xref:System.Windows.FrameworkElement.Height%2A> et entraîne l’étirement du média pour remplir la zone prévue pour le <xref:System.Windows.Controls.MediaElement>. Pour conserver les proportions d’origine du média, <xref:System.Windows.FrameworkElement.Width%2A> la <xref:System.Windows.FrameworkElement.Height%2A> propriété ou doit être définie, mais pas les deux. La définition des <xref:System.Windows.FrameworkElement.Width%2A> propriétés <xref:System.Windows.FrameworkElement.Height%2A> et entraîne la présentation du média dans une taille d’élément fixe qui peut ne pas être souhaitable.  
  
 Pour éviter d’avoir un élément de taille fixe, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] peut effectuer un preroll du média. Pour ce faire, affectez <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> la valeur <xref:System.Windows.Controls.MediaState.Pause>ouà. <xref:System.Windows.Controls.MediaState.Play> Dans un <xref:System.Windows.Controls.MediaState.Pause> État, le média est préroll et présente le premier frame. Dans un <xref:System.Windows.Controls.MediaState.Play> État, le média est préroll et commence à fonctionner.  
  
<a name="mediaplayer"></a>   
## <a name="mediaplayer-class"></a>Classe MediaPlayer  
 Lorsque la <xref:System.Windows.Controls.MediaElement> classe est un élément d’infrastructure, la <xref:System.Windows.Media.MediaPlayer> classe est conçue pour être utilisée dans <xref:System.Windows.Media.Drawing> les objets. Les objets de dessin sont utilisés lorsque vous pouvez sacrifier des fonctionnalités au niveau du Framework pour obtenir <xref:System.Windows.Freezable> des avantages en matière de performances ou lorsque vous avez besoin de fonctionnalités. <xref:System.Windows.Media.MediaPlayer>vous permet de tirer parti de ces fonctionnalités tout en fournissant du contenu multimédia dans vos applications. Comme <xref:System.Windows.Controls.MediaElement> <xref:System.Windows.Controls.MediaElement> , <xref:System.Windows.Media.MediaPlayer> peut être utilisé en mode indépendant ou en mode horloge, mais n’a pas les États déchargés et chargés de l’objet. Cela réduit la complexité du contrôle de lecture <xref:System.Windows.Media.MediaPlayer>de.  
  
### <a name="controlling-mediaplayer"></a>Contrôler un MediaPlayer  
 Étant <xref:System.Windows.Media.MediaPlayer> donné que est sans État, il existe deux façons de contrôler la lecture du média.  
  
1. Méthodes de contrôle interactives. En place en mode indépendant (`null` <xref:System.Windows.Media.MediaPlayer.Clock%2A> propriété).  
  
2. <xref:System.Windows.Media.MediaClock>. En place lorsque le média a <xref:System.Windows.Media.MediaPlayer.Clock%2A>un.  
  
### <a name="displaying-a-mediaplayer"></a>Afficher un MediaPlayer  
 Techniquement, un <xref:System.Windows.Media.MediaPlayer> ne peut pas être affiché, car il n’a pas de représentation physique. Toutefois, il peut être utilisé pour présenter un média dans <xref:System.Windows.Media.Drawing> un à <xref:System.Windows.Media.VideoDrawing> l’aide de la classe. L’exemple suivant illustre l’utilisation d’un <xref:System.Windows.Media.VideoDrawing> pour afficher un média.  
  
 [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline)]  
  
 Pour plus d’informations sur <xref:System.Windows.Media.Drawing> les objets, consultez [vue d’ensemble des objets de dessin](drawing-objects-overview.md) .  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Media.DrawingGroup>
- [Disposition](../advanced/layout.md)
- [Rubriques de guide pratique](audio-and-video-how-to-topics.md)
