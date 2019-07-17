---
title: Architecture de WPF
ms.date: 03/30/2017
helpviewer_keywords:
- properties [WPF], attached
- attached properties [WPF]
- architecture [WPF]
- unmanaged components [WPF]
- affinity thread [WPF]
- Storyboards [WPF]
- milcore [WPF]
- components [WPF], unmanaged
- painter's algorithm
- interfaces [WPF], INotifyPropertyChange
- CommandBindings [WPF]
- data templates [WPF]
- thread [WPF], affinity
ms.assetid: 8579c10b-76ab-4c52-9691-195ce02333c8
ms.openlocfilehash: 2fa2e039d73d079b6dacc9326c64fc2015eecc49
ms.sourcegitcommit: 4d8efe00f2e5ab42e598aff298d13b8c052d9593
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68238484"
---
# <a name="wpf-architecture"></a>Architecture de WPF
Cette rubrique fournit une visite guidée de la hiérarchie de classes de Windows Presentation Foundation (WPF). Elle couvre la plupart des principaux sous-systèmes de [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] et décrit leur mode d’interaction. Elle passe également en revue certains choix opérés par les architectes de [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].  

<a name="System_Object"></a>   
## <a name="systemobject"></a>System.Object  
 Le modèle de programmation [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] principal est exposé par le biais de code managé. Au début de la phase de conception de [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], l’une des questions que se posaient les architectes était de savoir où placer la limite entre les composants managés du système et les composants non managés. Le [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] fournit un ensemble de fonctionnalités qui rendent le développement plus productif et robuste (notamment la gestion de la mémoire, la gestion des erreurs, le système de type commun ou CTS, etc.), mais ces fonctionnalités ne sont pas sans coût.  
  
 Les principaux composants de [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] sont illustrés dans la figure ci-dessous. Les sections rouges du diagramme (PresentationFramework, PresentationCore et milcore) correspondent aux parties principales du code de [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]. Parmi celles-ci, milcore est le seul composant non managé. Milcore est écrit en code non managé pour permettre une intégration étroite avec [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)]. Tout l’affichage dans [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] s’effectue via le moteur [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] pour optimiser le rendu matériel et logiciel. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] nécessitait également un contrôle précis de la mémoire et de l’exécution. Le moteur de composition dans milcore est extrêmement dépendant des performances. Pour améliorer les performances, il fallait donc renoncer à de nombreux avantages de [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)].  
  
 ![Position de WPF dans le .NET Framework.](./media/wpf-architect1.PNG "wpf_architect1")  
  
 La communication entre les parties managées et non managées de [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] est présentée plus loin dans cette rubrique. Les autres aspects du modèle de programmation managé sont décrits ci-dessous.  
  
<a name="System_Threading_DispatcherObject"></a>   
## <a name="systemthreadingdispatcherobject"></a>System.Threading.DispatcherObject  
 La plupart des objets dans [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] dérivent <xref:System.Windows.Threading.DispatcherObject>, qui fournit les constructions de base pour le traitement avec l’accès concurrentiel et le threading. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] est basé sur un système de messagerie implémenté par le répartiteur. Le principe de fonctionnement est similaire à celui de la pompe de messages [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] : le répartiteur [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] utilise des messages User32 pour effectuer des appels entre les threads.  
  
 ll existe en fait deux concepts fondamentaux à comprendre au sujet de la concurrence dans [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] : le répartiteur et l’affinité de thread.  
  
 Pendant la phase de conception de [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], l’objectif était de passer à un modèle avec un seul thread d’exécution, mais sans affinité de thread. L’affinité de thread intervient quand un composant utilise l’identité du thread d’exécution pour stocker un type d’état. Sa forme la plus courante est l’utilisation du stockage local des threads (TLS) pour stocker l’état. L’affinité de thread nécessite que chaque thread logique d’exécution soit détenu par un seul thread physique dans le système d’exploitation, susceptible d’utiliser beaucoup de mémoire. Au final, les architectes ont opté pour un modèle de thread WPF semblable au modèle de thread User32 existant, basé sur un seul thread d’exécution avec affinité de thread. Ce choix a été principalement motivé par les besoins d’interopérabilité, du fait que des systèmes comme [!INCLUDE[TLA2#tla_ole2.0](../../../../includes/tla2sharptla-ole2-0-md.md)], le Presse-papiers et Internet Explorer utilisent tous le modèle d’exécution STA (Single Thread Affinity).  
  
 Étant donné que vous avez des objets avec des threads STA, vous devez prévoir un moyen de communiquer entre les threads et valider que vous êtes sur le thread approprié. C’est le rôle du répartiteur. Le répartiteur est un système de répartition de messages de base, avec plusieurs files d’attente de priorités différentes. Les messages concernés sont, par exemple, les notifications d’entrées brutes (déplacements de la souris), les fonctions de framework (disposition) ou les commandes utilisateur (exécuter cette méthode). En dérivant de <xref:System.Windows.Threading.DispatcherObject>, vous créez un [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] de l’objet qui a un comportement STA et recevra un pointeur vers un répartiteur au moment de la création.  
  
<a name="System_Windows_DependencyObject"></a>   
## <a name="systemwindowsdependencyobject"></a>System.Windows.DependencyObject  
 Lors de la conception de [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], l’une des principales philosophies suivies pour l’architecture était de privilégier les propriétés par rapport aux méthodes ou événements. Les propriétés, qui sont déclaratives, permettent plus facilement de spécifier l’intention au lieu de l’action. Cette approche permettait également la prise en charge d’un système piloté par un modèle, ou piloté par les données, pour afficher le contenu de l’interface utilisateur. Cette philosophie produisait l’effet recherché de créer davantage de propriétés qu’il n’en fallait pour établir des liaisons, afin de mieux contrôler le comportement d’une application.  
  
 Pour que le système soit davantage piloté par les propriétés, il fallait un système de propriétés plus complet que celui fourni par [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]. Les notifications de modification en sont un exemple simple. Pour permettre une liaison bidirectionnelle, les deux côtés de la liaison doivent prendre en charge la notification de modification. Pour que le comportement soit lié aux valeurs des propriétés, vous devez être notifié de chaque modification d’une valeur de propriété. Microsoft .NET Framework possède une interface, **INotifyPropertyChange**, ce qui permet à un objet de publier des notifications de modification, toutefois, il est facultatif.  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] fournit un système de propriétés plus riche, dérivé de la <xref:System.Windows.DependencyObject> type. Le système de propriétés est un vrai système de propriétés de « dépendance », car il effectue le suivi des dépendances entre les expressions de propriété et revalide automatiquement les valeurs de propriété après un changement des dépendances. Par exemple, si vous avez une propriété qui hérite (comme <xref:System.Windows.Controls.Control.FontSize%2A>), le système est automatiquement mis à jour si la propriété change sur un parent d’un élément qui hérite de la valeur.  
  
 Le système de propriétés de [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] repose sur le concept d’expression de propriété. Dans cette première version de [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], le système d’expressions de propriété est fermé et toutes les expressions font partie intégrante du framework. L’utilisation d’expressions explique pourquoi la liaison de données, les styles ou l’héritage ne sont pas codés en dur dans le système de propriétés, mais plutôt fournis par des couches supérieures dans le framework.  
  
 Le système de propriétés offre également un stockage fragmenté des valeurs de propriété. Étant donné que les objets peuvent avoir des dizaines (voire des centaines) de propriétés, et que la plupart des valeurs conservent leur état par défaut (héritée, définie par les styles, etc.), il n’est pas nécessaire de définir chacune de ces propriétés pour chaque instance d’un objet.  
  
 La notion de propriétés jointes est la dernière nouvelle fonctionnalité du système de propriétés. Les éléments [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] sont conçus sur le principe de composition et de réutilisation des composants. Il arrive souvent que certaines contenant l’élément (comme un <xref:System.Windows.Controls.Grid> élément de mise en page) a besoin de données supplémentaires sur les éléments enfants pour contrôler son comportement (par exemple, les informations de ligne/colonne). Au lieu d’associer toutes ces propriétés à chaque élément, les objets peuvent fournir des définitions de propriétés pour d’autres objets. Ceci est similaire aux fonctionnalités « expando » de JavaScript.  
  
<a name="System_Windows_Media_Visual"></a>   
## <a name="systemwindowsmediavisual"></a>System.Windows.Media.Visual  
 Une fois qu’un système a été défini, l’étape suivante est l’obtention des pixels dessinés à l’écran. Le <xref:System.Windows.Media.Visual> fournit des classes pour la création d’une arborescence d’objets visuels, chacun contenant éventuellement des instructions de dessin et des métadonnées relatives au rendu de ces instructions (découpage, transformation, etc.). <xref:System.Windows.Media.Visual> est conçu pour être extrêmement léger et flexible, afin que la plupart des fonctionnalités n’ont aucun accès API publique et reposent largement sur les fonctions de rappel protégées.  
  
 <xref:System.Windows.Media.Visual> est vraiment le point d’entrée pour le [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] système de composition. <xref:System.Windows.Media.Visual> est le point de connexion entre ces deux sous-systèmes, l’API managée et le milcore non managé.  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] affiche les données en parcourant les structures de données non managées qui sont managées par le milcore. Ces structures, appelées nœuds de composition, représentent une arborescence d’affichage hiérarchique, avec des instructions de rendu à chaque nœud. Cette arborescence, illustrée à droite de la figure ci-dessous, est accessible uniquement par le biais d’un protocole de messagerie.  
  
 Lors de la programmation [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], vous créez <xref:System.Windows.Media.Visual> éléments et les types dérivés, qui communiquent en interne à l’arborescence de composition via ce protocole de messagerie. Chaque <xref:System.Windows.Media.Visual> dans [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] peut créer un ou plusieurs nœuds de composition ou aucun.  
  
 ![Arborescence d’éléments visuels de Windows Presentation Foundation.](./media/wpf-architecture2.PNG "wpf_architecture2")  
  
 Il faut souligner un point important de cette architecture : toute l’arborescence des éléments visuels et des instructions de dessin est mise en cache. Sur le plan graphique, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] utilise un système de rendu en mode conservation. Le système peut ainsi actualiser les dessins à une fréquence élevée sans que cela entraîne un blocage du système de composition lors des rappels de code utilisateur. Cela aide à prévenir l’apparition d’une application qui ne répond pas.  
  
 Un autre point important à noter, que le diagramme ne montre pas vraiment, est la façon dont le système effectue réellement la composition.  
  
 Dans User32 et [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)], le système fonctionne selon un système de découpage en mode immédiat. Quand un composant doit être affiché, le système établit les limites de la zone de découpage en dehors de laquelle le composant n’est pas autorisé à manipuler les pixels, puis il demande au composant de dessiner les pixels dans cette zone. Cette approche est particulièrement efficace dans les systèmes à mémoire limitée, car lorsqu’un changement est effectué, vous avez uniquement à intervenir sur le composant concerné (la couleur d’un pixel étant toujours définie par un seul composant).  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] utilise le modèle de dessin « algorithme du peintre ». Cela signifie que chaque composant doit effectuer le rendu de l’arrière vers l’avant de l’affichage, au lieu de procéder par découpage. Chaque composant peut ainsi dessiner par-dessus l’affichage du composant précédent. L’avantage de ce modèle est que vous pouvez afficher des formes complexes partiellement transparentes. Avec les cartes graphiques actuelles, ce modèle est relativement rapide (ce qui n’était pas le cas quand les interfaces User32 et [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] ont été créées).  
  
 Comme mentionné plus haut, une philosophie essentielle de [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] est de passer à un modèle de programmation « axé sur les propriétés », davantage déclaratif. Cela s’observe à deux endroits intéressants du système visuel.  
  
 Tout d’abord, si vous réfléchissez au système graphique en mode conservation, cela revient en fait à passer d’un modèle de type DrawLine/DrawLine impératif à un modèle orienté données new Line()/new Line(). Cette évolution vers un rendu piloté par les données permet d’exprimer des opérations complexes sur les instructions de dessin à l’aide de propriétés. Les types dérivés de <xref:System.Windows.Media.Drawing> sont effectivement le modèle d’objet pour le rendu.  
  
 Ensuite, si vous examinez le système d’animation, vous verrez qu’il est presque entièrement déclaratif. Pour éviter au développeur d’avoir à calculer l’emplacement suivant, ou la couleur suivante, vous pouvez exprimer des animations dans un jeu de propriétés sur un objet animation. Ces animations peuvent alors exprimer l’intention du développeur ou du concepteur (par exemple, déplacer ce bouton d’ici à là dans cinq secondes), et le système peut déterminer le meilleur moyen d’y parvenir.  
  
<a name="System_Windows_UIElement"></a>   
## <a name="systemwindowsuielement"></a>System.Windows.UIElement  
 <xref:System.Windows.UIElement> définit les sous-systèmes de base, y compris Layout, Input et événements.  
  
 Layout est un concept fondamental dans [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]. Dans la plupart des systèmes, soit il y a un jeu fixe de modèles de disposition (HTML prend en charge trois modèles de disposition : fluide, absolu et tables), soit il n’y a aucun modèle de disposition (User32 prend réellement en charge uniquement le positionnement absolu). Aux débuts de [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], l’hypothèse était que les développeurs et concepteurs avaient besoin d’un modèle de disposition flexible et extensible, piloté par les valeurs de propriété plutôt que par une logique impérative. À la <xref:System.Windows.UIElement> niveau, le contrat de base de disposition est introduit, sous deux modèle avec la phase <xref:System.Windows.UIElement.Measure%2A> et <xref:System.Windows.UIElement.Arrange%2A> transmet.  
  
 <xref:System.Windows.UIElement.Measure%2A> permet à un composant déterminer la taille qu’il souhaite prendre. Il s’agit d’une phase distincte de <xref:System.Windows.UIElement.Arrange%2A> , car il existe de nombreuses situations où un élément parent demandera à un enfant de mesurer plusieurs fois afin de déterminer sa position optimale et la taille. Le fait que les éléments parents demandent aux éléments enfants d’effectuer les mesures illustre un autre point clé de la philosophie de [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], à savoir l’ajustement de la taille au contenu. Tous les contrôles dans [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] peuvent se redimensionner à la taille naturelle de leur contenu. Cela facilite la localisation et permet une disposition dynamique des éléments lors du redimensionnement. Le <xref:System.Windows.UIElement.Arrange%2A> phase permet à un parent de positionner et de déterminer la taille finale de chaque enfant.  
  
 Beaucoup de temps est souvent consacré aux discussions sur le côté sortie de [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] – <xref:System.Windows.Media.Visual> et les objets connexes. Toutefois, il existe aussi de nombreuses innovations côté entrée. Le changement le plus fondamental dans le modèle d’entrée pour [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] est probablement le modèle cohérent par lequel les événements d’entrée sont routés dans le système.  
  
 L’entrée est générée sous forme de signal sur un pilote de périphérique en mode noyau, puis elle est routée vers le processus et le thread appropriés selon un processus complexe impliquant User32 et le noyau Windows. Une fois que le message User32 correspondant à l’entrée a été routé vers [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], il est converti en message d’entrée brut [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] et envoyé au répartiteur. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] permet de convertir les événements d’entrée bruts en différents événements réels. Ainsi, certaines fonctionnalités telles que « MouseEnter » peuvent être implémentées à un niveau inférieur du système pour garantir leur transmission.  
  
 Chaque événement d’entrée est converti en deux événements au moins : un événement « preview » et l’événement réel. Tous les événements dans [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] suivent une stratégie de routage dans l’arborescence des éléments. Les événements sont appelés « propagation » si elles traversent à partir d’une cible de l’arborescence à la racine et sont dits « tunnel » si elles commencent à la racine et passent à une cible. Les événements preview d’entrée passent par un tunnel, ce qui permet aux éléments dans l’arborescence d’appliquer un filtre ou d’effectuer une action sur un événement. Les événements standard (non-preview) se propagent vers le haut de l’arborescence, de l’élément cible à la racine.  
  
 Grâce à cette distinction entre les phases de tunneling et de propagation, l’implémentation de fonctions comme les accélérateurs de clavier s’effectue de façon cohérente dans un environnement composite. Dans User32, vous pouvez implémenter les accélérateurs de clavier en utilisant une seule table globale qui contient tous les accélérateurs à prendre en charge (Ctrl+N correspondant à « Nouveau »). Dans le répartiteur de votre application, vous pouvez appeler **TranslateAccelerator** qui détecte les messages d’entrée dans User32 et détermine si l’un d’eux correspond à un accélérateur enregistré. Dans [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], cela ne fonctionne pas, car le système est entièrement « composable », c’est-à-dire que tout élément peut gérer et utiliser n’importe quel accélérateur de clavier. Avec ce modèle d’entrée à deux phases, les composants peuvent implémenter leur propre « TranslateAccelerator ».  
  
 Pour aller en outre, <xref:System.Windows.UIElement> également introduit la notion de CommandBindings. Le [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] commande système permet aux développeurs de définir les fonctionnalités en termes d’un point de terminaison de commande – quelque chose qui implémente <xref:System.Windows.Input.ICommand>. Avec les liaisons de commande, un élément peut définir un mappage entre un mouvement d’entrée (Ctrl+N) et une commande (Nouveau). Les mouvements d’entrée et les définitions de commande sont extensibles, et peuvent être liés ensemble au moment de l’utilisation. Vous pouvez alors facilement, par exemple, autoriser un utilisateur final à personnaliser les combinaisons de touches qu’il souhaite utiliser dans une application.  
  
 Jusqu’à présent, la rubrique a surtout abordé les fonctionnalités « clés » de [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], à savoir les fonctionnalités implémentées dans l’assembly PresentationCore. Lors de la génération [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], une séparation nette entre les éléments fondamentaux (comme le contrat de disposition avec **mesure** et **organiser**) et les éléments d’infrastructure (comme l’implémentation d’un spécifique disposition comme <xref:System.Windows.Controls.Grid>) a été le résultat souhaité. L’objectif était de fournir un point d’extensibilité en bas dans la pile qui permette aux développeurs externes de créer éventuellement leurs propres frameworks.  
  
<a name="System_Windows_FrameworkElement"></a>   
## <a name="systemwindowsframeworkelement"></a>System.Windows.FrameworkElement  
 <xref:System.Windows.FrameworkElement> peut être considéré de deux manières différentes. Il introduit un ensemble de stratégies et de personnalisations sur les sous-systèmes présents dans les couches inférieures de [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]. Il introduit également un ensemble de nouveaux sous-systèmes.  
  
 La stratégie principale introduite par <xref:System.Windows.FrameworkElement> est autour de la disposition de l’application. <xref:System.Windows.FrameworkElement> s’appuie sur le contrat de disposition de base introduit par <xref:System.Windows.UIElement> et ajoute la notion d’une « emplacement », ce qui rend plus facile pour les auteurs de disposition pour qu’un ensemble cohérent de sémantiques de disposition de pilotées par les propriétés de disposition. Propriétés, telles que <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>, <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>, <xref:System.Windows.FrameworkElement.MinWidth%2A>, et <xref:System.Windows.FrameworkElement.Margin%2A> (pour citer que quelques-unes) donner à tous les composants dérivés <xref:System.Windows.FrameworkElement> un comportement cohérent à l’intérieur de conteneurs de disposition.  
  
 <xref:System.Windows.FrameworkElement> fournit également une exposition de API plus facile à de nombreuses fonctionnalités trouvées dans les couches centrales de [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]. Par exemple, <xref:System.Windows.FrameworkElement> offre un accès direct à l’animation via la <xref:System.Windows.FrameworkElement.BeginStoryboard%2A> (méthode). Un <xref:System.Windows.Media.Animation.Storyboard> fournit un moyen de script de plusieurs animations par rapport à un ensemble de propriétés.  
  
 Les deux choses les plus critiques que <xref:System.Windows.FrameworkElement> introduit sont la liaison de données et styles.  
  
 Le sous-système de liaison de données dans [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] doit normalement vous être relativement familier si vous avez déjà utilisé [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ou [!INCLUDE[TLA#tla_aspnet](../../../../includes/tlasharptla-aspnet-md.md)] pour créer une [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] d’application. Chaque système offre un moyen simple d’exprimer votre intention de lier une ou plusieurs propriétés d’un élément spécifique à une donnée. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] prend totalement en charge la liaison de propriété, la transformation et la liaison de liste.  
  
 Les modèles de données sont l’une des fonctionnalités les plus intéressantes de la liaison de données dans [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]. Ils permettent de spécifier de manière déclarative comment afficher les données. Au lieu de créer une interface utilisateur personnalisée pouvant être liée à des données, vous pouvez contourner le problème et laisser les données déterminer l’affichage à créer.  
  
 Les styles constituent une forme légère de liaison de données. Vous pouvez utiliser les styles pour lier un jeu de propriétés d’une définition partagée à une ou plusieurs instances d’un élément. Les styles sont appliqués à un élément soit par référence explicite (en définissant le <xref:System.Windows.FrameworkElement.Style%2A> propriété) ou implicitement en associant un style avec le [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] type de l’élément.  
  
<a name="System_Windows_Controls_Control"></a>   
## <a name="systemwindowscontrolscontrol"></a>System.Windows.Controls.Control  
 La création de modèles est la fonctionnalité la plus importante du contrôle. Si vous considérez le système de composition de WPF comme un système de rendu en mode conservation, la création de modèles permet à un contrôle de décrire son rendu d’une manière déclarative et paramétrable. Un <xref:System.Windows.Controls.ControlTemplate> est vraiment rien de plus qu’un script pour créer des éléments, un jeu d’enfant avec des liaisons aux propriétés offertes par le contrôle.  
  
 <xref:System.Windows.Controls.Control> fournit un ensemble de propriétés stock, <xref:System.Windows.Controls.Control.Foreground%2A>, <xref:System.Windows.Controls.Control.Background%2A>, <xref:System.Windows.Controls.Control.Padding%2A>, pour en citer quelques-unes, que les créateurs de modèles peuvent utiliser pour personnaliser l’affichage d’un contrôle. L’implémentation d’un contrôle fournit un modèle de données et un modèle d’interaction. Le modèle d’interaction définit un jeu de commandes (Fermer une fenêtre, par exemple) et des liaisons aux mouvements d’entrée (comme le fait de cliquer sur le X rouge dans le coin supérieur d’une fenêtre). Le modèle de données fournit un jeu de propriétés pour personnaliser le modèle d’interaction ou l’affichage (déterminé par le modèle).  
  
 Cette distinction entre le modèle de données (propriétés), le modèle d’interaction (commandes et événements) et le modèle d’affichage (modèles) permet d’effectuer une personnalisation complète de l’apparence et du comportement d’un contrôle.  
  
 Le modèle de contenu est un aspect commun du modèle de données des contrôles. Si vous examinez un contrôle tel que <xref:System.Windows.Controls.Button>, vous verrez qu’il a une propriété nommée « Content » de type <xref:System.Object>. Dans [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] et [!INCLUDE[TLA#tla_aspnet](../../../../includes/tlasharptla-aspnet-md.md)], cette propriété est généralement une chaîne, mais cela limite le type de contenu que vous pouvez placer dans un bouton. Le contenu d’un bouton peut être une chaîne simple, un objet de données complexe ou une arborescence entière d’éléments. Dans le cas d’un objet de données, le modèle de données sert à créer un affichage.  
  
<a name="Summary"></a>   
## <a name="summary"></a>Récapitulatif  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] est conçu pour vous permettre de créer des systèmes de présentation dynamiques, pilotés par les données. Chaque partie du système est destinée à la création d’objets à l’aide de jeux de propriétés qui pilotent le comportement. La liaison de données est une fonctionnalité essentielle du système qui est intégrée au niveau de chaque couche.  
  
 Les applications standard créent un affichage, puis effectuent une liaison avec certaines données. Dans [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], tout ce qui concerne le contrôle, chaque aspect de l’affichage, est généré par un certain type de liaison de données. Le texte placé dans un bouton est affiché en créant un contrôle composé à l’intérieur du bouton et en liant son affichage à la propriété de contenu du bouton.  
  
 Quand vous commencerez à développer des applications basées sur [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], cela vous semblera déjà familier. En effet, vous pourrez définir les propriétés, utiliser les objets et lier les données à peu près de la même façon que dans [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ou [!INCLUDE[TLA#tla_aspnet](../../../../includes/tlasharptla-aspnet-md.md)]. Si vous étudiez l’architecture de [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] de manière plus approfondie, vous verrez que vous avez la possibilité de créer des applications plus riches qui traitent fondamentalement les données comme le pilote principal de l’application.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Media.Visual>
- <xref:System.Windows.UIElement>
- <xref:System.Windows.Input.ICommand>
- <xref:System.Windows.FrameworkElement>
- <xref:System.Windows.Threading.DispatcherObject>
- <xref:System.Windows.Input.CommandBinding>
- <xref:System.Windows.Controls.Control>
- [Vue d’ensemble de la liaison de données](../data/data-binding-overview.md)
- [Disposition](layout.md)
- [Vue d’ensemble de l’animation](../graphics-multimedia/animation-overview.md)
