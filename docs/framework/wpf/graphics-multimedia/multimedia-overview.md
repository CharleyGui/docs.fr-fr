---
title: Vue d'ensemble du multimédia
ms.date: 03/30/2017
helpviewer_keywords:
- multimedia [WPF]
- media [WPF]
ms.assetid: feb25b15-d741-4ac3-818f-1b19f63a3562
ms.openlocfilehash: 42d0d388e859b556d23b7fc81931cd61470ba541
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039804"
---
# <a name="multimedia-overview"></a>Vue d'ensemble du multimédia
Les fonctionnalités multimédias de [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] permettent d’intégrer des données audio et vidéo dans vos applications afin d’améliorer l’expérience utilisateur. Cette rubrique présente les fonctionnalités multimédias de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  

<a name="mediaapi"></a>   
## <a name="media-api"></a>API Media  
 Les classes <xref:System.Windows.Controls.MediaElement> et <xref:System.Windows.Media.MediaPlayer> sont utilisées pour présenter le contenu audio ou vidéo. Ces classes peuvent être contrôlées interactivement ou par une horloge. Ces classes peuvent être utilisées sur le contrôle Microsoft Windows Media Player 10 pour la lecture du média. La classe que vous allez utiliser dépend du scénario.  
  
 <xref:System.Windows.Controls.MediaElement> est une <xref:System.Windows.UIElement> qui est prise en charge par la [disposition](../advanced/layout.md) et qui peut être utilisée comme contenu de nombreux contrôles. Il est également utilisable en langage [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] ainsi que dans du code. <xref:System.Windows.Media.MediaPlayer>, en revanche, est conçu pour les objets <xref:System.Windows.Media.Drawing> et ne prend pas en charge la disposition. Les supports chargés à l’aide d’un <xref:System.Windows.Media.MediaPlayer> peuvent être présentés uniquement à l’aide d’un <xref:System.Windows.Media.VideoDrawing> ou en interagissant directement avec un <xref:System.Windows.Media.DrawingContext>. <xref:System.Windows.Media.MediaPlayer> ne peut pas être utilisé en XAML.  
  
 Pour plus d’informations sur les objets de dessin et le contexte de dessin, consultez [Vue d’ensemble des objets Drawing](drawing-objects-overview.md).  
  
> [!NOTE]
> Lorsque vous distribuez un contenu multimédia avec votre application, vous ne pouvez pas utiliser de fichier multimédia comme ressource de projet. Dans votre fichier projet, vous devez plutôt définir le type de média sur `Content` et définir `CopyToOutputDirectory` sur `PreserveNewest` ou `Always`.  
  
<a name="mediaplaybackmodes"></a>   
## <a name="media-playback-modes"></a>Modes de lecture de médias  
  
> [!NOTE]
> Les <xref:System.Windows.Controls.MediaElement> et <xref:System.Windows.Media.MediaPlayer> avoir des membres similaires. Les liens de cette section font référence aux membres de la classe <xref:System.Windows.Controls.MediaElement>. Sauf mention spécifique, les membres liés dans la classe <xref:System.Windows.Controls.MediaElement> se trouvent également dans la classe <xref:System.Windows.Media.MediaPlayer>.  
  
 Pour comprendre la lecture de médias dans [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], il est nécessaire de comprendre les différents modes de lecture des médias. <xref:System.Windows.Controls.MediaElement> et <xref:System.Windows.Media.MediaPlayer> peuvent être utilisés dans deux modes de média différents, en mode indépendant et en mode horloge. Le mode support est déterminé par la propriété <xref:System.Windows.Controls.MediaElement.Clock%2A>. Lorsque <xref:System.Windows.Controls.MediaElement.Clock%2A> est `null`, l’objet multimédia est en mode indépendant. Lorsque le <xref:System.Windows.Controls.MediaElement.Clock%2A> est non null, l’objet média est en mode horloge. Par défaut, les objets médias sont en mode indépendant.  
  
### <a name="independent-mode"></a>Mode indépendant  
 En mode indépendant, le contenu du média déclenche la lecture du média. Le mode indépendant comprend les options suivantes :  
  
- Le <xref:System.Uri> du média peut être spécifié directement.  
  
- La lecture du média peut être directement contrôlée.  
  
- Les propriétés <xref:System.Windows.Controls.MediaElement.Position%2A> et <xref:System.Windows.Controls.MediaElement.SpeedRatio%2A> du média peuvent être modifiées.  
  
 Le média est chargé soit en définissant la propriété <xref:System.Windows.Controls.MediaElement.Source%2A> de l’objet <xref:System.Windows.Controls.MediaElement>, soit en appelant la méthode <xref:System.Windows.Media.MediaPlayer.Open%2A> de l’objet <xref:System.Windows.Media.MediaPlayer>.  
  
 Pour contrôler la lecture du média en mode indépendant, les méthodes de contrôle de l’objet média peuvent être utilisées. Les méthodes de contrôle disponibles sont <xref:System.Windows.Controls.MediaElement.Play%2A>, <xref:System.Windows.Controls.MediaElement.Pause%2A>, <xref:System.Windows.Controls.MediaElement.Close%2A>et <xref:System.Windows.Controls.MediaElement.Stop%2A>. Par <xref:System.Windows.Controls.MediaElement>, le contrôle interactif à l’aide de ces méthodes est disponible uniquement lorsque la <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> est définie sur <xref:System.Windows.Controls.MediaState.Manual>. Ces méthodes ne sont pas disponibles lorsque l’objet média est en mode horloge.  
  
 Consultez la page [Contrôler un MediaElement (lecture, pause, arrêt, volume et vitesse)](how-to-control-a-mediaelement-play-pause-stop-volume-and-speed.md) pour obtenir un exemple de mode indépendant.  
  
### <a name="clock-mode"></a>Mode horloge  
 En mode horloge, un <xref:System.Windows.Media.MediaTimeline> pilote la lecture du média. Le mode horloge présente les caractéristiques suivantes :  
  
- Le <xref:System.Uri> du média est défini indirectement par le biais d’une <xref:System.Windows.Media.MediaTimeline>.  
  
- La lecture du média peut être contrôlée par l’horloge. Les méthodes de contrôle de l’objet média ne peuvent pas être utilisées.  
  
- Le média est chargé en définissant la propriété de <xref:System.Windows.Media.MediaTimeline.Source%2A> d’un objet <xref:System.Windows.Media.MediaTimeline>, en créant l’horloge à partir de la chronologie et en assignant l’horloge à l’objet multimédia. Le média est également chargé de cette manière lorsqu’un <xref:System.Windows.Media.MediaTimeline> à l’intérieur d’un <xref:System.Windows.Media.Animation.Storyboard> cible un <xref:System.Windows.Controls.MediaElement>.  
  
 Pour contrôler la lecture du média en mode horloge, vous devez utiliser les méthodes de contrôle <xref:System.Windows.Media.Animation.ClockController>. Une <xref:System.Windows.Media.Animation.ClockController> est obtenue à partir de la propriété <xref:System.Windows.Media.Animation.ClockController> du <xref:System.Windows.Media.MediaClock>. Si vous tentez d’utiliser les méthodes de contrôle d’un objet <xref:System.Windows.Controls.MediaElement> ou <xref:System.Windows.Media.MediaPlayer> en mode horloge, une <xref:System.InvalidOperationException> sera levée.  
  
 Pour plus d’informations sur les horloges et les chronologies, consultez l’article [Vue d’ensemble de l’animation](animation-overview.md).  
  
 Pour obtenir un exemple du mode horloge, consultez la page [Contrôler un MediaElement à l’aide d’un Storyboard](how-to-control-a-mediaelement-by-using-a-storyboard.md).  
  
<a name="mediaelement"></a>   
## <a name="mediaelement-class"></a>Classe MediaElement  
 L’ajout d’un média à une application est aussi simple que l’ajout d’un contrôle de <xref:System.Windows.Controls.MediaElement> à la [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] de l’application et la fourniture d’un <xref:System.Uri> au média que vous souhaitez inclure. Tous les types de média pris en charge par le lecteur Microsoft Windows Media 10 sont pris en charge dans [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]. L’exemple suivant montre une utilisation simple de la <xref:System.Windows.Controls.MediaElement> dans [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].  
  
 [!code-xaml[MediaElement_snip#SimpleMediaElementUsageWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaElement_snip/CSharp/SimpleUsage.xaml#simplemediaelementusagewholepage)]  
  
 Dans cet exemple, le média est lu automatiquement dès qu’il est chargé. Une fois la lecture du média terminée, le média est fermé et toutes les ressources du média sont libérées (y compris la mémoire vidéo). Il s’agit du comportement par défaut de l’objet <xref:System.Windows.Controls.MediaElement> et il est contrôlé par les propriétés <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> et <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A>.  
  
### <a name="controlling-a-mediaelement"></a>Contrôler un MediaElement  
 Les propriétés <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> et <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> contrôlent le comportement de l' <xref:System.Windows.Controls.MediaElement> lorsque <xref:System.Windows.FrameworkElement.IsLoaded%2A> est `true` ou `false`, respectivement. La <xref:System.Windows.Controls.MediaState> les propriétés sont définies de manière à affecter le comportement de lecture du média. Par exemple, la <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> par défaut est <xref:System.Windows.Controls.MediaState.Play> et la <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> par défaut est <xref:System.Windows.Controls.MediaState.Close>. Cela signifie que dès que le <xref:System.Windows.Controls.MediaElement> est chargé et que le préroll est terminé, le média commence à fonctionner. Une fois la lecture terminée, le média est fermé et toutes les ressources du média sont libérées.  
  
 Les propriétés <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> et <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> ne sont pas la seule façon de contrôler la lecture du média. En mode horloge, l’horloge peut contrôler la <xref:System.Windows.Controls.MediaElement> et les méthodes de contrôle interactives contrôlent le moment où l' <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> est <xref:System.Windows.Controls.MediaState.Manual>. <xref:System.Windows.Controls.MediaElement> gère ce concours pour le contrôle en évaluant les priorités suivantes.  
  
1. <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A>., Actif lorsque le média est déchargé. Cela garantit que toutes les ressources de média sont libérées par défaut, même lorsqu’un <xref:System.Windows.Media.MediaClock> est associé à la <xref:System.Windows.Controls.MediaElement>.  
  
2. <xref:System.Windows.Media.MediaClock>., En place lorsque le média a un <xref:System.Windows.Controls.MediaElement.Clock%2A>. Si le média est déchargé, le <xref:System.Windows.Media.MediaClock> prend effet tant que le <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> est <xref:System.Windows.Controls.MediaState.Manual>. Le mode horloge remplace toujours le comportement chargé du <xref:System.Windows.Controls.MediaElement>.  
  
3. <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A>., Actif lorsque le média est chargé.  
  
4. Méthodes de contrôle interactives. En place lorsque <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> est <xref:System.Windows.Controls.MediaState.Manual>. Les méthodes de contrôle disponibles sont <xref:System.Windows.Controls.MediaElement.Play%2A>, <xref:System.Windows.Controls.MediaElement.Pause%2A>, <xref:System.Windows.Controls.MediaElement.Close%2A>et <xref:System.Windows.Controls.MediaElement.Stop%2A>.  
  
### <a name="displaying-a-mediaelement"></a>Afficher un MediaElement  
 Pour afficher un <xref:System.Windows.Controls.MediaElement> il doit disposer d’un contenu à restituer et ses propriétés <xref:System.Windows.FrameworkElement.ActualWidth%2A> et <xref:System.Windows.FrameworkElement.ActualHeight%2A> sont définies sur zéro jusqu’à ce que le contenu soit chargé. Pour du contenu purement audio, ces propriétés sont toujours égales à zéro. Pour le contenu vidéo, lorsque l’événement <xref:System.Windows.Controls.MediaElement.MediaOpened> a été déclenché, le <xref:System.Windows.FrameworkElement.ActualWidth%2A> et <xref:System.Windows.FrameworkElement.ActualHeight%2A> signale la taille du média chargé. Cela signifie que, tant que le support n’est pas chargé, les <xref:System.Windows.Controls.MediaElement> n’occupent aucun espace physique dans le [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] à moins que les propriétés <xref:System.Windows.FrameworkElement.Width%2A> ou <xref:System.Windows.FrameworkElement.Height%2A> soient définies.  
  
 La définition des propriétés <xref:System.Windows.FrameworkElement.Width%2A> et <xref:System.Windows.FrameworkElement.Height%2A> entraîne l’étirement du média pour remplir la zone prévue pour le <xref:System.Windows.Controls.MediaElement>. Pour conserver les proportions d’origine du média, la propriété <xref:System.Windows.FrameworkElement.Width%2A> ou <xref:System.Windows.FrameworkElement.Height%2A> doit être définie, mais pas les deux. Le fait de définir à la fois les propriétés <xref:System.Windows.FrameworkElement.Width%2A> et <xref:System.Windows.FrameworkElement.Height%2A> entraîne la présentation du média dans une taille d’élément fixe qui peut ne pas être souhaitable.  
  
 Pour éviter d’avoir un élément de taille fixe, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] peut effectuer un preroll du média. Pour ce faire, affectez la valeur <xref:System.Windows.Controls.MediaState.Play> ou <xref:System.Windows.Controls.MediaState.Pause>à la <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A>. Dans un État <xref:System.Windows.Controls.MediaState.Pause>, le média est préroll et présente le premier frame. Dans un État <xref:System.Windows.Controls.MediaState.Play>, le média est préroll et commence à fonctionner.  
  
<a name="mediaplayer"></a>   
## <a name="mediaplayer-class"></a>Classe MediaPlayer  
 Lorsque la classe <xref:System.Windows.Controls.MediaElement> est un élément d’infrastructure, la classe <xref:System.Windows.Media.MediaPlayer> est conçue pour être utilisée dans les objets <xref:System.Windows.Media.Drawing>. Les objets de dessin sont utilisés lorsque vous pouvez sacrifier des fonctionnalités au niveau du Framework pour obtenir des avantages en matière de performances ou lorsque vous avez besoin de fonctionnalités de <xref:System.Windows.Freezable>. <xref:System.Windows.Media.MediaPlayer> vous permet de tirer parti de ces fonctionnalités tout en fournissant du contenu multimédia dans vos applications. Comme <xref:System.Windows.Controls.MediaElement>, <xref:System.Windows.Media.MediaPlayer> peut être utilisé en mode indépendant ou en mode horloge, mais il n’a pas les États déchargés et chargés de l’objet <xref:System.Windows.Controls.MediaElement>. Cela réduit la complexité du contrôle de lecture du <xref:System.Windows.Media.MediaPlayer>.  
  
### <a name="controlling-mediaplayer"></a>Contrôler un MediaPlayer  
 Étant donné que <xref:System.Windows.Media.MediaPlayer> est sans État, il existe deux façons de contrôler la lecture du média.  
  
1. Méthodes de contrôle interactives. En place en mode indépendant (propriété`null`<xref:System.Windows.Media.MediaPlayer.Clock%2A>).  
  
2. <xref:System.Windows.Media.MediaClock>., En place lorsque le média a un <xref:System.Windows.Media.MediaPlayer.Clock%2A>.  
  
### <a name="displaying-a-mediaplayer"></a>Afficher un MediaPlayer  
 Techniquement, un <xref:System.Windows.Media.MediaPlayer> ne peut pas être affiché, car il n’a pas de représentation physique. Toutefois, il peut être utilisé pour présenter un média dans un <xref:System.Windows.Media.Drawing> à l’aide de la classe <xref:System.Windows.Media.VideoDrawing>. L’exemple suivant illustre l’utilisation d’un <xref:System.Windows.Media.VideoDrawing> pour afficher un média.  
  
 [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline)]  
  
 Pour plus d’informations sur les objets <xref:System.Windows.Media.Drawing>, consultez [vue d’ensemble des objets dessinés](drawing-objects-overview.md) .  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Media.DrawingGroup>
- [Disposition](../advanced/layout.md)
- [Rubriques de guide pratique](audio-and-video-how-to-topics.md)
