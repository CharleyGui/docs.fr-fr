---
title: Vue d'ensemble du multimédia
ms.date: 03/30/2017
helpviewer_keywords:
- multimedia [WPF]
- media [WPF]
ms.assetid: feb25b15-d741-4ac3-818f-1b19f63a3562
ms.openlocfilehash: d4abf4d9fd324ffbf2737dc686c02e50ca1a8a5a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181887"
---
# <a name="multimedia-overview"></a>Vue d'ensemble du multimédia
Les fonctionnalités multimédias de [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] permettent d’intégrer des données audio et vidéo dans vos applications afin d’améliorer l’expérience utilisateur. Cette rubrique présente les fonctionnalités multimédias de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  

<a name="mediaapi"></a>
## <a name="media-api"></a>API Media  
 Les <xref:System.Windows.Controls.MediaElement> <xref:System.Windows.Media.MediaPlayer> cours et les classes sont utilisés pour présenter du contenu audio ou vidéo. Ces classes peuvent être contrôlées interactivement ou par une horloge. Ces classes peuvent être utilisées sur le contrôle Microsoft Windows Media Player 10 pour la lecture des médias. La classe que vous allez utiliser dépend du scénario.  
  
 <xref:System.Windows.Controls.MediaElement>est <xref:System.Windows.UIElement> un qui est pris en charge par la [mise en page](../advanced/layout.md) et peut être consommé comme le contenu de nombreux contrôles. Il est également utilisable en langage [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] ainsi que dans du code. <xref:System.Windows.Media.MediaPlayer>, d’autre part, <xref:System.Windows.Media.Drawing> est conçu pour les objets et manque de support de mise en page. Les médias <xref:System.Windows.Media.MediaPlayer> chargés à l’aide d’un ne peut être présenté qu’à l’aide d’un <xref:System.Windows.Media.VideoDrawing> ou en interagissant directement avec un <xref:System.Windows.Media.DrawingContext>. <xref:System.Windows.Media.MediaPlayer>ne peut pas être utilisé dans XAML.  
  
 Pour plus d’informations sur les objets de dessin et le contexte de dessin, consultez [Vue d’ensemble des objets Drawing](drawing-objects-overview.md).  
  
> [!NOTE]
> Lorsque vous distribuez un contenu multimédia avec votre application, vous ne pouvez pas utiliser de fichier multimédia comme ressource de projet. Dans votre fichier projet, vous devez plutôt définir le type de média sur `Content` et définir `CopyToOutputDirectory` sur `PreserveNewest` ou `Always`.  
  
<a name="mediaplaybackmodes"></a>
## <a name="media-playback-modes"></a>Modes de lecture de médias  
  
> [!NOTE]
> Les <xref:System.Windows.Controls.MediaElement> <xref:System.Windows.Media.MediaPlayer> deux et ont des membres similaires. Les liens de cette <xref:System.Windows.Controls.MediaElement> section se réfèrent aux membres de la classe. Sauf indication précise, les <xref:System.Windows.Controls.MediaElement> membres liés à la <xref:System.Windows.Media.MediaPlayer> classe peuvent également être trouvés dans la classe.  
  
 Pour comprendre la lecture de médias dans [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], il est nécessaire de comprendre les différents modes de lecture des médias. Les <xref:System.Windows.Controls.MediaElement> <xref:System.Windows.Media.MediaPlayer> deux et peuvent être utilisés dans deux modes multimédias différents, mode indépendant et mode d’horloge. Le mode média est <xref:System.Windows.Controls.MediaElement.Clock%2A> déterminé par la propriété. Quand <xref:System.Windows.Controls.MediaElement.Clock%2A> `null`est, l’objet multimédia est en mode indépendant. Lorsque <xref:System.Windows.Controls.MediaElement.Clock%2A> l’objet n’est pas nul, l’objet multimédia est en mode horloge. Par défaut, les objets médias sont en mode indépendant.  
  
### <a name="independent-mode"></a>Mode indépendant  
 En mode indépendant, le contenu du média déclenche la lecture du média. Le mode indépendant comprend les options suivantes :  
  
- Les médias <xref:System.Uri> peuvent être spécifiés directement.  
  
- La lecture du média peut être directement contrôlée.  
  
- Les médias <xref:System.Windows.Controls.MediaElement.Position%2A> <xref:System.Windows.Controls.MediaElement.SpeedRatio%2A> et les propriétés peuvent être modifiés.  
  
 Les médias sont chargés <xref:System.Windows.Controls.MediaElement> en <xref:System.Windows.Controls.MediaElement.Source%2A> définissant la <xref:System.Windows.Media.MediaPlayer> propriété de <xref:System.Windows.Media.MediaPlayer.Open%2A> l’objet ou en appelant la méthode de l’objet.  
  
 Pour contrôler la lecture du média en mode indépendant, les méthodes de contrôle de l’objet média peuvent être utilisées. Les méthodes de <xref:System.Windows.Controls.MediaElement.Play%2A> <xref:System.Windows.Controls.MediaElement.Pause%2A>contrôle <xref:System.Windows.Controls.MediaElement.Close%2A>disponibles sont , , , et <xref:System.Windows.Controls.MediaElement.Stop%2A>. Pour <xref:System.Windows.Controls.MediaElement>, le contrôle interactif en <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> utilisant ces <xref:System.Windows.Controls.MediaState.Manual>méthodes n’est disponible que lorsque l’est réglé à . Ces méthodes ne sont pas disponibles lorsque l’objet média est en mode horloge.  
  
 Consultez la page [Contrôler un MediaElement (lecture, pause, arrêt, volume et vitesse)](how-to-control-a-mediaelement-play-pause-stop-volume-and-speed.md) pour obtenir un exemple de mode indépendant.  
  
### <a name="clock-mode"></a>Mode horloge  
 En mode horloge, une <xref:System.Windows.Media.MediaTimeline> lecture multimédia lecteurs. Le mode horloge présente les caractéristiques suivantes :  
  
- Media <xref:System.Uri> est indirectement fixé à <xref:System.Windows.Media.MediaTimeline>travers un .  
  
- La lecture du média peut être contrôlée par l’horloge. Les méthodes de contrôle de l’objet média ne peuvent pas être utilisées.  
  
- Les médias sont <xref:System.Windows.Media.MediaTimeline> chargés en <xref:System.Windows.Media.MediaTimeline.Source%2A> définissant la propriété d’un objet, en créant l’horloge à partir de la chronologie et en attribuant l’horloge à l’objet multimédia. Les médias sont également <xref:System.Windows.Media.MediaTimeline> chargés <xref:System.Windows.Media.Animation.Storyboard> de <xref:System.Windows.Controls.MediaElement>cette façon quand un intérieur d’un objectif a .  
  
 Pour contrôler la lecture des <xref:System.Windows.Media.Animation.ClockController> médias en mode horloge, les méthodes de contrôle doivent être utilisées. A <xref:System.Windows.Media.Animation.ClockController> est obtenu <xref:System.Windows.Media.Animation.ClockController> à partir <xref:System.Windows.Media.MediaClock>de la propriété de la . Si vous essayez d’utiliser les <xref:System.Windows.Controls.MediaElement> <xref:System.Windows.Media.MediaPlayer> méthodes de contrôle d’un ou d’un objet en mode horloge, un <xref:System.InvalidOperationException> sera lancé.  
  
 Pour plus d’informations sur les horloges et les chronologies, consultez l’article [Vue d’ensemble de l’animation](animation-overview.md).  
  
 Pour obtenir un exemple du mode horloge, consultez la page [Contrôler un MediaElement à l’aide d’un Storyboard](how-to-control-a-mediaelement-by-using-a-storyboard.md).  
  
<a name="mediaelement"></a>
## <a name="mediaelement-class"></a>Classe MediaElement  
 L’ajout de médias à une <xref:System.Windows.Controls.MediaElement> application [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] est aussi simple <xref:System.Uri> que d’ajouter un contrôle à l’application et de fournir un aux médias que vous souhaitez inclure. Tous les types de médias pris en charge [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]par Microsoft Windows Media Player 10 sont pris en charge dans . L’exemple suivant montre une <xref:System.Windows.Controls.MediaElement> [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]simple utilisation de l’in .  
  
 [!code-xaml[MediaElement_snip#SimpleMediaElementUsageWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaElement_snip/CSharp/SimpleUsage.xaml#simplemediaelementusagewholepage)]  
  
 Dans cet exemple, le média est lu automatiquement dès qu’il est chargé. Une fois la lecture du média terminée, le média est fermé et toutes les ressources du média sont libérées (y compris la mémoire vidéo). Il s’agit du <xref:System.Windows.Controls.MediaElement> comportement par défaut <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> de <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> l’objet et est contrôlé par le et les propriétés.  
  
### <a name="controlling-a-mediaelement"></a>Contrôler un MediaElement  
 Les <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> propriétés et les <xref:System.Windows.Controls.MediaElement> <xref:System.Windows.FrameworkElement.IsLoaded%2A> propriétés contrôlent le comportement du moment `true` ou, `false`respectivement. Les <xref:System.Windows.Controls.MediaState> propriétés sont définies pour affecter le comportement de lecture des médias. Par exemple, <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> la <xref:System.Windows.Controls.MediaState.Play> valeur <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> par <xref:System.Windows.Controls.MediaState.Close>défaut est et la valeur par défaut est . Cela signifie que dès <xref:System.Windows.Controls.MediaElement> que le est chargé et le préroll est terminé, les médias commencent à jouer. Une fois la lecture terminée, le média est fermé et toutes les ressources du média sont libérées.  
  
 Les <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> propriétés et les propriétés ne sont pas le seul moyen de contrôler la lecture des médias. En mode horloge, l’horloge peut contrôler le <xref:System.Windows.Controls.MediaElement> et <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> <xref:System.Windows.Controls.MediaState.Manual>les méthodes de contrôle interactives ont le contrôle lorsque le est . <xref:System.Windows.Controls.MediaElement>gère ce concours pour le contrôle en évaluant les priorités suivantes.  
  
1. <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A>. Actif lorsque le média est déchargé. Cela garantit que toutes les ressources des médias <xref:System.Windows.Media.MediaClock> sont libérées par défaut, même lorsque l’a est associée à la <xref:System.Windows.Controls.MediaElement>.  
  
2. <xref:System.Windows.Media.MediaClock>. En place lorsque <xref:System.Windows.Controls.MediaElement.Clock%2A>les médias ont un . Si les médias sont <xref:System.Windows.Media.MediaClock> déchargés, le prendra <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> <xref:System.Windows.Controls.MediaState.Manual>effet aussi longtemps que le est . Mode horloge remplace toujours le comportement <xref:System.Windows.Controls.MediaElement>chargé de la .  
  
3. <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A>. Actif lorsque le média est chargé.  
  
4. Méthodes de contrôle interactives. En place <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> <xref:System.Windows.Controls.MediaState.Manual>quand est . Les méthodes de <xref:System.Windows.Controls.MediaElement.Play%2A> <xref:System.Windows.Controls.MediaElement.Pause%2A>contrôle <xref:System.Windows.Controls.MediaElement.Close%2A>disponibles sont , , , et <xref:System.Windows.Controls.MediaElement.Stop%2A>.  
  
### <a name="displaying-a-mediaelement"></a>Afficher un MediaElement  
 Pour afficher <xref:System.Windows.Controls.MediaElement> un, il doit avoir du <xref:System.Windows.FrameworkElement.ActualWidth%2A> <xref:System.Windows.FrameworkElement.ActualHeight%2A> contenu à rendre et il aura son et les propriétés définies à zéro jusqu’à ce que le contenu est chargé. Pour du contenu purement audio, ces propriétés sont toujours égales à zéro. Pour le contenu <xref:System.Windows.Controls.MediaElement.MediaOpened> vidéo, une <xref:System.Windows.FrameworkElement.ActualWidth%2A> fois <xref:System.Windows.FrameworkElement.ActualHeight%2A> que l’événement a été soulevé et rapportera la taille des supports chargés. Cela signifie que tant que <xref:System.Windows.Controls.MediaElement> les supports ne seront [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] pas <xref:System.Windows.FrameworkElement.Width%2A> chargés, le ne prendra pas d’espace physique à moins que les propriétés ou <xref:System.Windows.FrameworkElement.Height%2A> les propriétés ne soient définies.  
  
 La mise <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.FrameworkElement.Height%2A> en place et les propriétés amèneront <xref:System.Windows.Controls.MediaElement>les médias à s’étirer pour remplir la zone prévue pour le . Pour préserver le rapport d’aspect <xref:System.Windows.FrameworkElement.Width%2A> original <xref:System.Windows.FrameworkElement.Height%2A> des médias, le ou la propriété doit être défini, mais pas les deux. La mise <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.FrameworkElement.Height%2A> en place et les propriétés feront présenter les médias dans une taille d’élément fixe qui peut ne pas être souhaitable.  
  
 Pour éviter d’avoir un élément de taille fixe, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] peut effectuer un preroll du média. Cela se fait <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> en <xref:System.Windows.Controls.MediaState.Play> fixant l’un ou l’autre ou <xref:System.Windows.Controls.MediaState.Pause>. Dans <xref:System.Windows.Controls.MediaState.Pause> un état, les médias prérolleront et présenteront le premier cadre. Dans <xref:System.Windows.Controls.MediaState.Play> un état, les médias prérolleront et commenceront à jouer.  
  
<a name="mediaplayer"></a>
## <a name="mediaplayer-class"></a>Classe MediaPlayer  
 Lorsque la <xref:System.Windows.Controls.MediaElement> classe est un <xref:System.Windows.Media.MediaPlayer> élément-cadre, la <xref:System.Windows.Media.Drawing> classe est conçue pour être utilisée dans les objets. Les objets de dessin sont utilisés lorsque vous pouvez sacrifier <xref:System.Windows.Freezable> des fonctionnalités de niveau cadre pour obtenir des avantages de performance ou lorsque vous avez besoin de fonctionnalités. <xref:System.Windows.Media.MediaPlayer>vous permet de tirer parti de ces fonctionnalités tout en fournissant du contenu multimédia dans vos applications. Comme <xref:System.Windows.Controls.MediaElement> <xref:System.Windows.Media.MediaPlayer> , peut être utilisé en mode indépendant <xref:System.Windows.Controls.MediaElement> ou horloge, mais n’a pas les états déchargés et chargés de l’objet. Cela réduit la complexité de <xref:System.Windows.Media.MediaPlayer>contrôle de lecture de la .  
  
### <a name="controlling-mediaplayer"></a>Contrôler un MediaPlayer  
 Parce <xref:System.Windows.Media.MediaPlayer> qu’il est apatride, il n’y a que deux façons de contrôler la lecture des médias.  
  
1. Méthodes de contrôle interactives. En place lorsqu’il`null` <xref:System.Windows.Media.MediaPlayer.Clock%2A> est en mode indépendant (propriété).  
  
2. <xref:System.Windows.Media.MediaClock>. En place lorsque <xref:System.Windows.Media.MediaPlayer.Clock%2A>les médias ont un .  
  
### <a name="displaying-a-mediaplayer"></a>Afficher un MediaPlayer  
 Techniquement, <xref:System.Windows.Media.MediaPlayer> un ne peut pas être affiché puisqu’il n’a pas de représentation physique. Cependant, il peut être utilisé <xref:System.Windows.Media.Drawing> pour <xref:System.Windows.Media.VideoDrawing> présenter les médias dans une utilisation de la classe. L’exemple suivant montre l’utilisation d’un <xref:System.Windows.Media.VideoDrawing> support d’affichage.  
  
 [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline)]  
  
 Voir [l’aperçu des](drawing-objects-overview.md) objets <xref:System.Windows.Media.Drawing> de dessin pour plus d’informations sur les objets.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Media.DrawingGroup>
- [Disposition](../advanced/layout.md)
- [Sujets comment se passer](audio-and-video-how-to-topics.md)
