---
title: Architecture
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
ms.openlocfilehash: b16be8470a47f3e8e362feb0b13e10aa901baacb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187132"
---
# <a name="wpf-architecture"></a>Architecture de WPF
Ce sujet offre une visite guidée de la hiérarchie de classe de la Windows Presentation Foundation (WPF). Il couvre la plupart des principaux sous-systèmes de WPF, et décrit comment ils interagissent. Il détaille également quelques-uns des choix faits par les architectes de WPF.  

<a name="System_Object"></a>
## <a name="systemobject"></a>System.Object  
 Le modèle de programmation WPF primaire est exposé par le code géré. Au début de la phase de conception du WPF, il y a eu un certain nombre de débats sur l’endroit où la ligne de démarcation devrait être tracée entre les composantes gérées du système et les éléments non gérés. Le CLR fournit un certain nombre de fonctionnalités qui rendent le développement plus productif et robuste (y compris la gestion de la mémoire, la gestion des erreurs, le système de type commun, etc.), mais elles ont un coût.  
  
 Les principales composantes du WPF sont illustrées dans la figure ci-dessous. Les sections rouges du diagramme (PresentationFramework, PresentationCore et milcore) sont les principales parties de code de WPF. Parmi celles-ci, milcore est le seul composant non managé. Milcore est écrit en code non managérré afin de permettre une intégration serrée avec DirectX. Tous les affichages dans WPF se fait via le moteur DirectX, permettant un rendu matériel et logiciel efficace. WPF a également exigé un contrôle fin sur la mémoire et l’exécution. Le moteur de composition en milcore est extrêmement sensible aux performances, et a nécessité de renoncer à de nombreux avantages de la CLR pour gagner des performances.  
  
 ![Position de WPF dans le .NET Framework.](./media/wpf-architect1.PNG "wpf_architect1")  
  
 La communication entre les parties gérées et non gérées de WPF est discutée plus tard dans ce sujet. Les autres aspects du modèle de programmation managé sont décrits ci-dessous.  
  
<a name="System_Threading_DispatcherObject"></a>
## <a name="systemthreadingdispatcherobject"></a>System.Threading.DispatcherObject  
 La plupart des objets <xref:System.Windows.Threading.DispatcherObject>dans WPF dérivent de , qui fournit les constructions de base pour faire face à la concurrence et le filetage. WPF est basé sur un système de messagerie mis en œuvre par le répartiteur. Cela fonctionne un peu comme la pompe de message familier Win32; en fait, le répartiteur WPF utilise des messages User32 pour effectuer des appels de fil croisé.  
  
 Il ya vraiment deux concepts de base à comprendre lors de la discussion de la concurrence dans WPF - le répartiteur et l’affinité de fil.  
  
 Pendant la phase de conception de WPF, l’objectif était de passer à un seul fil d’exécution, mais un modèle non-thread "affinitisé". L’affinité de thread intervient quand un composant utilise l’identité du thread d’exécution pour stocker un type d’état. Sa forme la plus courante est l’utilisation du stockage local des threads (TLS) pour stocker l’état. L’affinité de thread nécessite que chaque thread logique d’exécution soit détenu par un seul thread physique dans le système d’exploitation, susceptible d’utiliser beaucoup de mémoire. Au final, les architectes ont opté pour un modèle de thread WPF semblable au modèle de thread User32 existant, basé sur un seul thread d’exécution avec affinité de thread. La principale raison en était l’interopérabilité - des systèmes comme OLE 2.0, le presse-papiers, et Internet Explorer ont tous besoin d’une seule affinité de fil (STA) exécution.  
  
 Étant donné que vous avez des objets avec des threads STA, vous devez prévoir un moyen de communiquer entre les threads et valider que vous êtes sur le thread approprié. C’est le rôle du répartiteur. Le répartiteur est un système de répartition de messages de base, avec plusieurs files d’attente de priorités différentes. Les messages concernés sont, par exemple, les notifications d’entrées brutes (déplacements de la souris), les fonctions de framework (disposition) ou les commandes utilisateur (exécuter cette méthode). En dérivé de <xref:System.Windows.Threading.DispatcherObject>, vous créez un objet CLR qui a le comportement STA, et sera donné un pointeur à un répartiteur au moment de la création.  
  
<a name="System_Windows_DependencyObject"></a>
## <a name="systemwindowsdependencyobject"></a>System.Windows.DependencyObject  
 L’une des principales philosophies architecturales utilisées dans la construction de WPF était une préférence pour les propriétés par exemple par exemple en ce qui a eu lieu sur les méthodes ou les événements. Les propriétés, qui sont déclaratives, permettent plus facilement de spécifier l’intention au lieu de l’action. Cette approche permettait également la prise en charge d’un système piloté par un modèle, ou piloté par les données, pour afficher le contenu de l’interface utilisateur. Cette philosophie produisait l’effet recherché de créer davantage de propriétés qu’il n’en fallait pour établir des liaisons, afin de mieux contrôler le comportement d’une application.  
  
 Afin d’avoir plus de système conduit par des propriétés, un système de propriété plus riche que ce que le CLR fournit était nécessaire. Les notifications de modification en sont un exemple simple. Pour permettre une liaison bidirectionnelle, les deux côtés de la liaison doivent prendre en charge la notification de modification. Pour que le comportement soit lié aux valeurs des propriétés, vous devez être notifié de chaque modification d’une valeur de propriété. Le cadre Microsoft .NET dispose d’une interface, **INotifyPropertyChange**, qui permet à un objet de publier des notifications de modification, mais il est facultatif.  
  
 WPF fournit un système de <xref:System.Windows.DependencyObject> propriété plus riche, dérivé du type. Le système de propriétés est un vrai système de propriétés de « dépendance », car il effectue le suivi des dépendances entre les expressions de propriété et revalide automatiquement les valeurs de propriété après un changement des dépendances. Par exemple, si vous avez une <xref:System.Windows.Controls.Control.FontSize%2A>propriété qui hérite (comme), le système est automatiquement mis à jour si la propriété change sur un parent d’un élément qui hérite de la valeur.  
  
 Le fondement du système immobilier WPF est le concept d’expression de propriété. Dans cette première version de WPF, le système d’expression de propriété est fermé, et les expressions sont toutes fournies dans le cadre. L’utilisation d’expressions explique pourquoi la liaison de données, les styles ou l’héritage ne sont pas codés en dur dans le système de propriétés, mais plutôt fournis par des couches supérieures dans le framework.  
  
 Le système de propriétés offre également un stockage fragmenté des valeurs de propriété. Étant donné que les objets peuvent avoir des dizaines (voire des centaines) de propriétés, et que la plupart des valeurs conservent leur état par défaut (héritée, définie par les styles, etc.), il n’est pas nécessaire de définir chacune de ces propriétés pour chaque instance d’un objet.  
  
 La notion de propriétés jointes est la dernière nouvelle fonctionnalité du système de propriétés. Les éléments WPF sont construits sur le principe de la composition et de la réutilisation des composants. Il est souvent vrai que certains <xref:System.Windows.Controls.Grid> éléments contenant (comme un élément de mise en page) ont besoin de données supplémentaires sur les éléments de l’enfant pour contrôler son comportement (comme les informations Row/Column). Au lieu d’associer toutes ces propriétés à chaque élément, les objets peuvent fournir des définitions de propriétés pour d’autres objets. Ceci est similaire aux fonctionnalités « expando » de JavaScript.  
  
<a name="System_Windows_Media_Visual"></a>
## <a name="systemwindowsmediavisual"></a>System.Windows.Media.Visual  
 Une fois qu’un système a été défini, l’étape suivante est l’obtention des pixels dessinés à l’écran. La <xref:System.Windows.Media.Visual> classe prévoit la construction d’un arbre d’objets visuels, chacun contenant des instructions de dessin et des métadonnées sur la façon de rendre ces instructions (clipping, transformation, etc.). <xref:System.Windows.Media.Visual>est conçu pour être extrêmement léger et flexible, de sorte que la plupart des fonctionnalités n’ont pas d’exposition publique aPI et comptent fortement sur les fonctions de rappel protégés.  
  
 <xref:System.Windows.Media.Visual>est vraiment le point d’entrée du système de composition WPF. <xref:System.Windows.Media.Visual>est le point de connexion entre ces deux sous-systèmes, l’API géré et le milcore non géré.  
  
 WPF affiche des données en traversant les structures de données non gérées gérées par le milcore. Ces structures, appelées nœuds de composition, représentent une arborescence d’affichage hiérarchique, avec des instructions de rendu à chaque nœud. Cette arborescence, illustrée à droite de la figure ci-dessous, est accessible uniquement par le biais d’un protocole de messagerie.  
  
 Lors de la programmation <xref:System.Windows.Media.Visual> de WPF, vous créez des éléments, et des types dérivés, qui communiquent en interne à l’arbre de composition par le biais de ce protocole de messagerie. Chacun <xref:System.Windows.Media.Visual> dans WPF peut créer un, aucun, ou plusieurs nœuds de composition.  
  
 ![Arborescence d'éléments visuels de Windows Presentation Foundation.](./media/wpf-architecture2.PNG "wpf_architecture2")  
  
 Il faut souligner un point important de cette architecture : toute l’arborescence des éléments visuels et des instructions de dessin est mise en cache. En termes graphiques, WPF utilise un système de rendu retenu. Le système peut ainsi actualiser les dessins à une fréquence élevée sans que cela entraîne un blocage du système de composition lors des rappels de code utilisateur. Cela aide à prévenir l’apparition d’une application qui ne répond pas.  
  
 Un autre point important à noter, que le diagramme ne montre pas vraiment, est la façon dont le système effectue réellement la composition.  
  
 Dans User32 et GDI, le système fonctionne sur un système de coupure de mode immédiat. Quand un composant doit être affiché, le système établit les limites de la zone de découpage en dehors de laquelle le composant n’est pas autorisé à manipuler les pixels, puis il demande au composant de dessiner les pixels dans cette zone. Cette approche est particulièrement efficace dans les systèmes à mémoire limitée, car lorsqu’un changement est effectué, vous avez uniquement à intervenir sur le composant concerné (la couleur d’un pixel étant toujours définie par un seul composant).  
  
 WPF utilise un modèle de peinture « algorithme du peintre ». Cela signifie que chaque composant doit effectuer le rendu de l’arrière vers l’avant de l’affichage, au lieu de procéder par découpage. Chaque composant peut ainsi dessiner par-dessus l’affichage du composant précédent. L’avantage de ce modèle est que vous pouvez afficher des formes complexes partiellement transparentes. Avec le matériel graphique moderne d’aujourd’hui, ce modèle est relativement rapide (ce qui n’était pas le cas lors de la création de User32/GDI).  
  
 Comme mentionné précédemment, une philosophie de base de WPF est de passer à un plus déclaratif, "axé sur la propriété" modèle de programmation. Cela s’observe à deux endroits intéressants du système visuel.  
  
 Tout d’abord, si vous réfléchissez au système graphique en mode conservation, cela revient en fait à passer d’un modèle de type DrawLine/DrawLine impératif à un modèle orienté données new Line()/new Line(). Cette évolution vers un rendu piloté par les données permet d’exprimer des opérations complexes sur les instructions de dessin à l’aide de propriétés. Les types dérivés <xref:System.Windows.Media.Drawing> sont effectivement le modèle d’objet pour le rendu.  
  
 Ensuite, si vous examinez le système d’animation, vous verrez qu’il est presque entièrement déclaratif. Pour éviter au développeur d’avoir à calculer l’emplacement suivant, ou la couleur suivante, vous pouvez exprimer des animations dans un jeu de propriétés sur un objet animation. Ces animations peuvent alors exprimer l’intention du développeur ou du concepteur (par exemple, déplacer ce bouton d’ici à là dans cinq secondes), et le système peut déterminer le meilleur moyen d’y parvenir.  
  
<a name="System_Windows_UIElement"></a>
## <a name="systemwindowsuielement"></a>System.Windows.UIElement  
 <xref:System.Windows.UIElement>définit les sous-systèmes de base, y compris la mise en page, l’entrée et les événements.  
  
 La mise en page est un concept de base dans WPF. Dans la plupart des systèmes, soit il y a un jeu fixe de modèles de disposition (HTML prend en charge trois modèles de disposition : fluide, absolu et tables), soit il n’y a aucun modèle de disposition (User32 prend réellement en charge uniquement le positionnement absolu). WPF a commencé avec l’hypothèse que les développeurs et les concepteurs voulaient un modèle de mise en page flexible et extensible, qui pourrait être entraîné par les valeurs de propriété plutôt que la logique impérative. Au <xref:System.Windows.UIElement> niveau, le contrat de base pour la <xref:System.Windows.UIElement.Measure%2A> mise <xref:System.Windows.UIElement.Arrange%2A> en page est introduit - un modèle en deux phases avec et passe.  
  
 <xref:System.Windows.UIElement.Measure%2A>permet à un composant de déterminer la taille qu’il aimerait prendre. Il s’agit <xref:System.Windows.UIElement.Arrange%2A> d’une phase distincte de la situation où il y a de nombreuses situations où un élément parent demandera à un enfant de mesurer plusieurs fois pour déterminer sa position et sa taille optimales. Le fait que les éléments parentaux demandent des éléments à la mesure de l’enfant démontre une autre philosophie clé de WPF - la taille du contenu. Tous les contrôles dans WPF prennent en charge la possibilité de tailler à la taille naturelle de leur contenu. Cela facilite la localisation et permet une disposition dynamique des éléments lors du redimensionnement. La <xref:System.Windows.UIElement.Arrange%2A> phase permet à un parent de positionner et de déterminer la taille finale de chaque enfant.  
  
 Beaucoup de temps est souvent passé à parler <xref:System.Windows.Media.Visual> du côté de sortie de WPF - et des objets connexes. Toutefois, il existe aussi de nombreuses innovations côté entrée. Probablement le changement le plus fondamental dans le modèle d’entrée pour WPF est le modèle cohérent par lequel les événements d’entrée sont acheminés à travers le système.  
  
 L’entrée est générée sous forme de signal sur un pilote de périphérique en mode noyau, puis elle est routée vers le processus et le thread appropriés selon un processus complexe impliquant User32 et le noyau Windows. Une fois que le message User32 correspondant à l’entrée est acheminé vers WPF, il est converti en message d’entrée brut WPF et envoyé au répartiteur. WPF permet de convertir les événements d’entrée brutes en plusieurs événements réels, permettant de mettre en œuvre des fonctionnalités comme "MouseEnter" à un faible niveau du système avec une livraison garantie.  
  
 Chaque événement d’entrée est converti en deux événements au moins : un événement « preview » et l’événement réel. Tous les événements de WPF ont une idée de routage à travers l’arbre élément. On dit que les événements « bouillonnent » s’ils traversent d’une cible jusqu’à la racine, et sont dits de « tunnel » s’ils commencent à la racine et traversent vers le bas à une cible. Les événements preview d’entrée passent par un tunnel, ce qui permet aux éléments dans l’arborescence d’appliquer un filtre ou d’effectuer une action sur un événement. Les événements standard (non-preview) se propagent vers le haut de l’arborescence, de l’élément cible à la racine.  
  
 Grâce à cette distinction entre les phases de tunneling et de propagation, l’implémentation de fonctions comme les accélérateurs de clavier s’effectue de façon cohérente dans un environnement composite. Dans User32, vous pouvez implémenter les accélérateurs de clavier en utilisant une seule table globale qui contient tous les accélérateurs à prendre en charge (Ctrl+N correspondant à « Nouveau »). Dans le répartiteur de votre application, vous pouvez appeler **TranslateAccelerator** qui détecte les messages d’entrée dans User32 et détermine si l’un d’eux correspond à un accélérateur enregistré. Dans WPF cela ne fonctionnerait pas parce que le système est entièrement "composable" - n’importe quel élément peut manipuler et utiliser n’importe quel accélérateur de clavier. Avec ce modèle d’entrée à deux phases, les composants peuvent implémenter leur propre « TranslateAccelerator ».  
  
 Pour aller plus loin, <xref:System.Windows.UIElement> introduit également la notion de CommandBindings. Le système de commande WPF permet aux développeurs de définir les <xref:System.Windows.Input.ICommand>fonctionnalités en termes de point final de commande - quelque chose qui implémente . Avec les liaisons de commande, un élément peut définir un mappage entre un mouvement d’entrée (Ctrl+N) et une commande (Nouveau). Les mouvements d’entrée et les définitions de commande sont extensibles, et peuvent être liés ensemble au moment de l’utilisation. Vous pouvez alors facilement, par exemple, autoriser un utilisateur final à personnaliser les combinaisons de touches qu’il souhaite utiliser dans une application.  
  
 À ce stade du sujet, les caractéristiques « fondamentales » de WPF, caractéristiques mises en œuvre dans l’assemblage PresentationCore, ont été au centre de l’attention. Lors de la construction de WPF, une séparation nette entre les pièces de base (comme le <xref:System.Windows.Controls.Grid>contrat de mise en page avec **Measure** and **Arrange**) et les pièces-cadres (comme la mise en œuvre d’une disposition spécifique comme ) a été le résultat souhaité. L’objectif était de fournir un point d’extensibilité en bas dans la pile qui permette aux développeurs externes de créer éventuellement leurs propres frameworks.  
  
<a name="System_Windows_FrameworkElement"></a>
## <a name="systemwindowsframeworkelement"></a>System.Windows.FrameworkElement  
 <xref:System.Windows.FrameworkElement>peuvent être examinés de deux façons différentes. Il introduit un ensemble de politiques et de personnalisations sur les sous-systèmes introduits dans les couches inférieures de WPF. Il introduit également un ensemble de nouveaux sous-systèmes.  
  
 La politique principale <xref:System.Windows.FrameworkElement> introduite par est autour de la disposition des applications. <xref:System.Windows.FrameworkElement>s’appuie sur le contrat <xref:System.Windows.UIElement> de mise en page de base introduit par et ajoute la notion d’une mise en page "slot" qui rend plus facile pour les auteurs de mise en page d’avoir un ensemble cohérent de propriété conduit mise en page sémantique. Propriétés <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>comme <xref:System.Windows.FrameworkElement.MinWidth%2A>, <xref:System.Windows.FrameworkElement.Margin%2A> , et (pour n’en <xref:System.Windows.FrameworkElement> nommer que quelques-uns) donnent tous les composants dérivés d’un comportement cohérent à l’intérieur des conteneurs de mise en page.  
  
 <xref:System.Windows.FrameworkElement>fournit également une exposition plus facile à l’API à de nombreuses fonctionnalités trouvées dans les couches centrales de WPF. Par exemple, <xref:System.Windows.FrameworkElement> fournit un accès <xref:System.Windows.FrameworkElement.BeginStoryboard%2A> direct à l’animation par la méthode. A <xref:System.Windows.Media.Animation.Storyboard> fournit un moyen de script de multiples animations contre un ensemble de propriétés.  
  
 Les deux choses <xref:System.Windows.FrameworkElement> les plus critiques qui introduisent sont la liaison des données et les styles.  
  
 Le sous-système de liaison de données dans WPF devrait être relativement familier à [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]toute personne qui a utilisé windows Forms ou ASP.NET pour créer une application . Chaque système offre un moyen simple d’exprimer votre intention de lier une ou plusieurs propriétés d’un élément spécifique à une donnée. WPF bénéficie d’un soutien total pour l’établissement de l’obligation de propriété, la transformation et la fixation de la liste.  
  
 L’une des caractéristiques les plus intéressantes de la liaison de données dans WPF est l’introduction de modèles de données. Ils permettent de spécifier de manière déclarative comment afficher les données. Au lieu de créer une interface utilisateur personnalisée pouvant être liée à des données, vous pouvez contourner le problème et laisser les données déterminer l’affichage à créer.  
  
 Les styles constituent une forme légère de liaison de données. Vous pouvez utiliser les styles pour lier un jeu de propriétés d’une définition partagée à une ou plusieurs instances d’un élément. Les styles sont appliqués à un élément <xref:System.Windows.FrameworkElement.Style%2A> soit par référence explicite (en définissant la propriété) ou implicitement en associant un style avec le type CLR de l’élément.  
  
<a name="System_Windows_Controls_Control"></a>
## <a name="systemwindowscontrolscontrol"></a>System.Windows.Controls.Control  
 La création de modèles est la fonctionnalité la plus importante du contrôle. Si vous considérez le système de composition de WPF comme un système de rendu en mode conservation, la création de modèles permet à un contrôle de décrire son rendu d’une manière déclarative et paramétrable. A <xref:System.Windows.Controls.ControlTemplate> n’est vraiment rien de plus qu’un script pour créer un ensemble d’éléments pour enfants, avec des fixations aux propriétés offertes par le contrôle.  
  
 <xref:System.Windows.Controls.Control>fournit un ensemble de <xref:System.Windows.Controls.Control.Foreground%2A> <xref:System.Windows.Controls.Control.Background%2A>propriétés de stock, , , <xref:System.Windows.Controls.Control.Padding%2A>pour n’en nommer que quelques-uns, que les auteurs de modèles peuvent ensuite utiliser pour personnaliser l’affichage d’un contrôle. L’implémentation d’un contrôle fournit un modèle de données et un modèle d’interaction. Le modèle d’interaction définit un jeu de commandes (Fermer une fenêtre, par exemple) et des liaisons aux mouvements d’entrée (comme le fait de cliquer sur le X rouge dans le coin supérieur d’une fenêtre). Le modèle de données fournit un jeu de propriétés pour personnaliser le modèle d’interaction ou l’affichage (déterminé par le modèle).  
  
 Cette distinction entre le modèle de données (propriétés), le modèle d’interaction (commandes et événements) et le modèle d’affichage (modèles) permet d’effectuer une personnalisation complète de l’apparence et du comportement d’un contrôle.  
  
 Le modèle de contenu est un aspect commun du modèle de données des contrôles. Si vous regardez un <xref:System.Windows.Controls.Button>contrôle comme, vous verrez qu’il a <xref:System.Object>une propriété nommée "Contenu" de type . Dans Windows Forms et ASP.NET, cette propriété serait généralement une chaîne - mais cela limite le type de contenu que vous pouvez mettre dans un bouton. Le contenu d’un bouton peut être une chaîne simple, un objet de données complexe ou une arborescence entière d’éléments. Dans le cas d’un objet de données, le modèle de données sert à créer un affichage.  
  
<a name="Summary"></a>
## <a name="summary"></a>Résumé  
 WPF est conçu pour vous permettre de créer des systèmes de présentation dynamiques et axés sur les données. Chaque partie du système est destinée à la création d’objets à l’aide de jeux de propriétés qui pilotent le comportement. La liaison de données est une fonctionnalité essentielle du système qui est intégrée au niveau de chaque couche.  
  
 Les applications standard créent un affichage, puis effectuent une liaison avec certaines données. Dans WPF, tout ce qui concerne le contrôle, chaque aspect de l’écran, est généré par un certain type de liaison de données. Le texte placé dans un bouton est affiché en créant un contrôle composé à l’intérieur du bouton et en liant son affichage à la propriété de contenu du bouton.  
  
 Lorsque vous commencez à développer des applications basées sur WPF, il devrait se sentir très familier. Vous pouvez définir des propriétés, utiliser des objets et des données se lier de la même manière que vous pouvez utiliser des formulaires Windows ou ASP.NET. Avec une enquête plus approfondie sur l’architecture de WPF, vous constaterez que la possibilité existe pour créer des applications beaucoup plus riches qui traitent fondamentalement les données comme le moteur principal de l’application.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Media.Visual>
- <xref:System.Windows.UIElement>
- <xref:System.Windows.Input.ICommand>
- <xref:System.Windows.FrameworkElement>
- <xref:System.Windows.Threading.DispatcherObject>
- <xref:System.Windows.Input.CommandBinding>
- <xref:System.Windows.Controls.Control>
- [Aperçu de la liaison de données](../../../desktop-wpf/data/data-binding-overview.md)
- [Disposition](layout.md)
- [Vue d’ensemble de l’animation](../graphics-multimedia/animation-overview.md)
