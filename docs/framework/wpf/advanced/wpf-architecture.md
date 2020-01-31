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
ms.openlocfilehash: 6d8dedafd4ffc582b529289d3583f90d81779762
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794042"
---
# <a name="wpf-architecture"></a>Architecture de WPF
Cette rubrique fournit une visite guidée de la hiérarchie de classes Windows Presentation Foundation (WPF). Il couvre la plupart des principaux sous-systèmes de WPF et décrit comment ils interagissent. Il détaille également certains des choix effectués par les architectes de WPF.  

<a name="System_Object"></a>   
## <a name="systemobject"></a>System.Object  
 Le modèle de programmation WPF principal est exposé via du code managé. Au début de la phase de conception de WPF, il y avait un certain nombre de débats sur l’endroit où la ligne devait être dessinée entre les composants gérés du système et les éléments non gérés. Le CLR fournit un certain nombre de fonctionnalités qui rendent le développement plus productif et plus robuste (y compris la gestion de la mémoire, la gestion des erreurs, le système de type commun, etc.), mais ils ont un coût.  
  
 Les principaux composants de WPF sont illustrés dans la figure ci-dessous. Les sections rouges du diagramme (PresentationFramework, PresentationCore et milcore) sont les principales parties de code de WPF. Parmi celles-ci, milcore est le seul composant non managé. Milcore est écrit en code non managé afin d’assurer une intégration étroite avec DirectX. Tous les affichages dans WPF s’effectuent via le moteur DirectX, ce qui permet un rendu efficace du matériel et des logiciels. WPF avait également besoin d’un contrôle précis sur la mémoire et l’exécution. Le moteur de composition dans milcore est extrêmement sensible aux performances et nécessite de nombreux avantages du CLR pour obtenir des performances.  
  
 ![Position de WPF dans le .NET Framework.](./media/wpf-architect1.PNG "wpf_architect1")  
  
 La communication entre les parties managées et non managées de WPF est décrite plus loin dans cette rubrique. Les autres aspects du modèle de programmation managé sont décrits ci-dessous.  
  
<a name="System_Threading_DispatcherObject"></a>   
## <a name="systemthreadingdispatcherobject"></a>System.Threading.DispatcherObject  
 La plupart des objets dans WPF dérivent de <xref:System.Windows.Threading.DispatcherObject>, qui fournit les constructions de base pour gérer l’accès concurrentiel et le Threading. WPF est basé sur un système de messagerie implémenté par le répartiteur. Cela fonctionne très bien comme la pompe de messages Win32 familière. en fait, le répartiteur WPF utilise des messages User32 pour effectuer des appels inter-threads.  
  
 Il existe en fait deux concepts fondamentaux à comprendre lors de la présentation de l’accès concurrentiel dans WPF : le répartiteur et l’affinité de thread.  
  
 Pendant la phase de conception de WPF, l’objectif était de passer à un seul thread d’exécution, mais un modèle « affinité » non thread. L’affinité de thread intervient quand un composant utilise l’identité du thread d’exécution pour stocker un type d’état. Sa forme la plus courante est l’utilisation du stockage local des threads (TLS) pour stocker l’état. L’affinité de thread nécessite que chaque thread logique d’exécution soit détenu par un seul thread physique dans le système d’exploitation, susceptible d’utiliser beaucoup de mémoire. Au final, les architectes ont opté pour un modèle de thread WPF semblable au modèle de thread User32 existant, basé sur un seul thread d’exécution avec affinité de thread. L’interopérabilité est principalement due au fait que les systèmes comme OLE 2,0, le presse-papiers et Internet Explorer requièrent tous une exécution STA (single thread Affinity).  
  
 Étant donné que vous avez des objets avec des threads STA, vous devez prévoir un moyen de communiquer entre les threads et valider que vous êtes sur le thread approprié. C’est le rôle du répartiteur. Le répartiteur est un système de répartition de messages de base, avec plusieurs files d’attente de priorités différentes. Les messages concernés sont, par exemple, les notifications d’entrées brutes (déplacements de la souris), les fonctions de framework (disposition) ou les commandes utilisateur (exécuter cette méthode). En dérivant de <xref:System.Windows.Threading.DispatcherObject>, vous créez un objet CLR qui a un comportement STA et recevrez un pointeur vers un répartiteur au moment de la création.  
  
<a name="System_Windows_DependencyObject"></a>   
## <a name="systemwindowsdependencyobject"></a>System.Windows.DependencyObject  
 L’une des philosophies architecturales principales utilisées dans la création de WPF était une préférence pour les propriétés sur les méthodes ou les événements. Les propriétés, qui sont déclaratives, permettent plus facilement de spécifier l’intention au lieu de l’action. Cette approche permettait également la prise en charge d’un système piloté par un modèle, ou piloté par les données, pour afficher le contenu de l’interface utilisateur. Cette philosophie produisait l’effet recherché de créer davantage de propriétés qu’il n’en fallait pour établir des liaisons, afin de mieux contrôler le comportement d’une application.  
  
 Pour que le système soit plus piloté par les propriétés, un système de propriétés plus riche que celui fourni par le CLR est nécessaire. Les notifications de modification en sont un exemple simple. Pour permettre une liaison bidirectionnelle, les deux côtés de la liaison doivent prendre en charge la notification de modification. Pour que le comportement soit lié aux valeurs des propriétés, vous devez être notifié de chaque modification d’une valeur de propriété. Le Microsoft .NET Framework a une interface, **INotifyPropertyChange**, qui permet à un objet de publier des notifications de modification, mais il est facultatif.  
  
 WPF fournit un système de propriétés plus riche, dérivé du type de <xref:System.Windows.DependencyObject>. Le système de propriétés est un vrai système de propriétés de « dépendance », car il effectue le suivi des dépendances entre les expressions de propriété et revalide automatiquement les valeurs de propriété après un changement des dépendances. Par exemple, si vous avez une propriété qui hérite (comme <xref:System.Windows.Controls.Control.FontSize%2A>), le système est automatiquement mis à jour si la propriété change sur le parent d’un élément qui hérite de la valeur.  
  
 La base du système de propriétés WPF est le concept d’une expression de propriété. Dans cette première version de WPF, le système d’expressions de la propriété est fermé et les expressions sont toutes fournies dans le cadre de l’infrastructure. L’utilisation d’expressions explique pourquoi la liaison de données, les styles ou l’héritage ne sont pas codés en dur dans le système de propriétés, mais plutôt fournis par des couches supérieures dans le framework.  
  
 Le système de propriétés offre également un stockage fragmenté des valeurs de propriété. Étant donné que les objets peuvent avoir des dizaines (voire des centaines) de propriétés, et que la plupart des valeurs conservent leur état par défaut (héritée, définie par les styles, etc.), il n’est pas nécessaire de définir chacune de ces propriétés pour chaque instance d’un objet.  
  
 La notion de propriétés jointes est la dernière nouvelle fonctionnalité du système de propriétés. Les éléments WPF sont basés sur le principe de la réutilisation des composants et de la composition. C’est souvent le cas, par exemple, qu’un élément conteneur (comme un élément <xref:System.Windows.Controls.Grid> Layout) a besoin de données supplémentaires sur les éléments enfants pour contrôler son comportement (comme les informations sur les lignes ou les colonnes). Au lieu d’associer toutes ces propriétés à chaque élément, les objets peuvent fournir des définitions de propriétés pour d’autres objets. Ceci est similaire aux fonctionnalités « expando » de JavaScript.  
  
<a name="System_Windows_Media_Visual"></a>   
## <a name="systemwindowsmediavisual"></a>System.Windows.Media.Visual  
 Une fois qu’un système a été défini, l’étape suivante est l’obtention des pixels dessinés à l’écran. La classe <xref:System.Windows.Media.Visual> permet de générer une arborescence d’objets visuels, chacun contenant éventuellement des instructions de dessin et des métadonnées relatives au rendu de ces instructions (découpage, transformation, etc.). <xref:System.Windows.Media.Visual> est conçu pour être extrêmement léger et flexible, la plupart des fonctionnalités n’ont pas d’exposition d’API publique et s’appuient fortement sur des fonctions de rappel protégées.  
  
 <xref:System.Windows.Media.Visual> est vraiment le point d’entrée du système de composition WPF. <xref:System.Windows.Media.Visual> est le point de connexion entre ces deux sous-systèmes, l’API managée et le milcore non managé.  
  
 WPF affiche les données en parcourant les structures de données non managées gérées par le milcore. Ces structures, appelées nœuds de composition, représentent une arborescence d’affichage hiérarchique, avec des instructions de rendu à chaque nœud. Cette arborescence, illustrée à droite de la figure ci-dessous, est accessible uniquement par le biais d’un protocole de messagerie.  
  
 Lors de la programmation de WPF, vous créez <xref:System.Windows.Media.Visual> éléments, et les types dérivés, qui communiquent en interne avec l’arborescence de composition par le biais de ce protocole de messagerie. Chaque <xref:System.Windows.Media.Visual> dans WPF peut créer un, aucun ou plusieurs nœuds de composition.  
  
 ![Arborescence d’éléments visuels Windows Presentation Foundation.](./media/wpf-architecture2.PNG "wpf_architecture2")  
  
 Il faut souligner un point important de cette architecture : toute l’arborescence des éléments visuels et des instructions de dessin est mise en cache. En termes graphiques, WPF utilise un système de rendu conservé. Le système peut ainsi actualiser les dessins à une fréquence élevée sans que cela entraîne un blocage du système de composition lors des rappels de code utilisateur. Cela aide à prévenir l’apparition d’une application qui ne répond pas.  
  
 Un autre point important à noter, que le diagramme ne montre pas vraiment, est la façon dont le système effectue réellement la composition.  
  
 Dans User32 et GDI, le système fonctionne sur un système de découpage en mode immédiat. Quand un composant doit être affiché, le système établit les limites de la zone de découpage en dehors de laquelle le composant n’est pas autorisé à manipuler les pixels, puis il demande au composant de dessiner les pixels dans cette zone. Cette approche est particulièrement efficace dans les systèmes à mémoire limitée, car lorsqu’un changement est effectué, vous avez uniquement à intervenir sur le composant concerné (la couleur d’un pixel étant toujours définie par un seul composant).  
  
 WPF utilise le modèle de peinture « algorithme d’un peintre ». Cela signifie que chaque composant doit effectuer le rendu de l’arrière vers l’avant de l’affichage, au lieu de procéder par découpage. Chaque composant peut ainsi dessiner par-dessus l’affichage du composant précédent. L’avantage de ce modèle est que vous pouvez afficher des formes complexes partiellement transparentes. Avec le matériel graphique moderne d’aujourd’hui, ce modèle est relativement rapide (ce qui n’était pas le cas lors de la création de User32/GDI).  
  
 Comme mentionné précédemment, une philosophie de base de WPF consiste à passer à un modèle de programmation « centré sur la propriété » plus déclaratif. Cela s’observe à deux endroits intéressants du système visuel.  
  
 Tout d’abord, si vous réfléchissez au système graphique en mode conservation, cela revient en fait à passer d’un modèle de type DrawLine/DrawLine impératif à un modèle orienté données new Line()/new Line(). Cette évolution vers un rendu piloté par les données permet d’exprimer des opérations complexes sur les instructions de dessin à l’aide de propriétés. Les types dérivant de <xref:System.Windows.Media.Drawing> sont effectivement le modèle objet pour le rendu.  
  
 Ensuite, si vous examinez le système d’animation, vous verrez qu’il est presque entièrement déclaratif. Pour éviter au développeur d’avoir à calculer l’emplacement suivant, ou la couleur suivante, vous pouvez exprimer des animations dans un jeu de propriétés sur un objet animation. Ces animations peuvent alors exprimer l’intention du développeur ou du concepteur (par exemple, déplacer ce bouton d’ici à là dans cinq secondes), et le système peut déterminer le meilleur moyen d’y parvenir.  
  
<a name="System_Windows_UIElement"></a>   
## <a name="systemwindowsuielement"></a>System.Windows.UIElement  
 <xref:System.Windows.UIElement> définit les sous-systèmes de base, y compris la disposition, les entrées et les événements.  
  
 La disposition est un concept fondamental dans WPF. Dans la plupart des systèmes, soit il y a un jeu fixe de modèles de disposition (HTML prend en charge trois modèles de disposition : fluide, absolu et tables), soit il n’y a aucun modèle de disposition (User32 prend réellement en charge uniquement le positionnement absolu). WPF a démarré en partant du principe que les développeurs et les concepteurs voulaient un modèle de disposition flexible et extensible, qui pouvait être piloté par les valeurs de propriété plutôt que la logique impérative. Au niveau de la <xref:System.Windows.UIElement>, le contrat de base pour la disposition est introduit : un modèle en deux phases avec <xref:System.Windows.UIElement.Measure%2A> et <xref:System.Windows.UIElement.Arrange%2A> passe.  
  
 <xref:System.Windows.UIElement.Measure%2A> permet à un composant de déterminer la taille qu’il souhaite prendre. Il s’agit d’une phase distincte de <xref:System.Windows.UIElement.Arrange%2A>, car il existe de nombreuses situations où un élément parent demande à un enfant de mesurer plusieurs fois pour déterminer sa position et sa taille optimales. Le fait que les éléments parents demandent des éléments enfants à mesurer illustre une autre philosophie clé de WPF : la taille du contenu. Tous les contrôles dans WPF prennent en charge la capacité à se dimensionner à la taille naturelle de leur contenu. Cela facilite la localisation et permet une disposition dynamique des éléments lors du redimensionnement. La phase <xref:System.Windows.UIElement.Arrange%2A> permet à un parent de se positionner et de déterminer la taille finale de chaque enfant.  
  
 Beaucoup de temps est souvent consacré au côté de la sortie de WPF – <xref:System.Windows.Media.Visual> et les objets connexes. Toutefois, il existe aussi de nombreuses innovations côté entrée. La modification la plus fondamentale dans le modèle d’entrée pour WPF est probablement le modèle cohérent par lequel les événements d’entrée sont acheminés via le système.  
  
 L’entrée est générée sous forme de signal sur un pilote de périphérique en mode noyau, puis elle est routée vers le processus et le thread appropriés selon un processus complexe impliquant User32 et le noyau Windows. Une fois que le message User32 correspondant à l’entrée est routé vers WPF, il est converti en message d’entrée brut WPF et envoyé au répartiteur. WPF permet de convertir des événements d’entrée brutes en plusieurs événements réels, ce qui permet d’implémenter des fonctionnalités telles que « MouseEnter » à un niveau inférieur du système avec une remise garantie.  
  
 Chaque événement d’entrée est converti en deux événements au moins : un événement « preview » et l’événement réel. Tous les événements dans WPF ont une notion de routage via l’arborescence d’éléments. Les événements sont dits « bulles » s’ils traversent une cible vers le haut de l’arborescence jusqu’à la racine. ils sont dits « tunneling » s’ils commencent à la racine et passent à une cible. Les événements preview d’entrée passent par un tunnel, ce qui permet aux éléments dans l’arborescence d’appliquer un filtre ou d’effectuer une action sur un événement. Les événements standard (non-preview) se propagent vers le haut de l’arborescence, de l’élément cible à la racine.  
  
 Grâce à cette distinction entre les phases de tunneling et de propagation, l’implémentation de fonctions comme les accélérateurs de clavier s’effectue de façon cohérente dans un environnement composite. Dans User32, vous pouvez implémenter les accélérateurs de clavier en utilisant une seule table globale qui contient tous les accélérateurs à prendre en charge (Ctrl+N correspondant à « Nouveau »). Dans le répartiteur de votre application, vous pouvez appeler **TranslateAccelerator** qui détecte les messages d’entrée dans User32 et détermine si l’un d’eux correspond à un accélérateur enregistré. Dans WPF, cela ne fonctionnerait pas, car le système est entièrement « composable » : tout élément peut gérer et utiliser n’importe quel accélérateur clavier. Avec ce modèle d’entrée à deux phases, les composants peuvent implémenter leur propre « TranslateAccelerator ».  
  
 Pour aller plus loin, <xref:System.Windows.UIElement> introduit également la notion de CommandBindings. Le système de commandes WPF permet aux développeurs de définir des fonctionnalités en termes de point de terminaison de commande, un composant qui implémente <xref:System.Windows.Input.ICommand>. Avec les liaisons de commande, un élément peut définir un mappage entre un mouvement d’entrée (Ctrl+N) et une commande (Nouveau). Les mouvements d’entrée et les définitions de commande sont extensibles, et peuvent être liés ensemble au moment de l’utilisation. Vous pouvez alors facilement, par exemple, autoriser un utilisateur final à personnaliser les combinaisons de touches qu’il souhaite utiliser dans une application.  
  
 À ce stade de la rubrique, les fonctionnalités « principales » de WPF, qui sont implémentées dans l’assembly PresentationCore, ont été concentrées. Lors de la création de WPF, une séparation nette entre les éléments fondamentaux (comme le contrat de disposition avec **mesure** et **organisation**) et les éléments de Framework (comme l’implémentation d’une disposition spécifique comme <xref:System.Windows.Controls.Grid>) était le résultat souhaité. L’objectif était de fournir un point d’extensibilité en bas dans la pile qui permette aux développeurs externes de créer éventuellement leurs propres frameworks.  
  
<a name="System_Windows_FrameworkElement"></a>   
## <a name="systemwindowsframeworkelement"></a>System.Windows.FrameworkElement  
 les <xref:System.Windows.FrameworkElement> peuvent être consultées de deux façons différentes. Il introduit un ensemble de stratégies et de personnalisations sur les sous-systèmes introduits dans des couches inférieures de WPF. Il introduit également un ensemble de nouveaux sous-systèmes.  
  
 La stratégie principale introduite par <xref:System.Windows.FrameworkElement> concerne la disposition de l’application. <xref:System.Windows.FrameworkElement> s’appuie sur le contrat de disposition de base introduit par <xref:System.Windows.UIElement> et ajoute la notion d’un « emplacement » de disposition qui permet aux auteurs de disposition d’avoir un ensemble cohérent de sémantiques de mise en page pilotées par les propriétés. Les propriétés telles que <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>, <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>, <xref:System.Windows.FrameworkElement.MinWidth%2A>et <xref:System.Windows.FrameworkElement.Margin%2A> (pour en nommer quelques-unes) donnent à tous les composants dérivés de <xref:System.Windows.FrameworkElement> comportement cohérent dans les conteneurs de disposition.  
  
 <xref:System.Windows.FrameworkElement> offre également une plus grande facilité d’utilisation des API pour de nombreuses fonctionnalités qui se trouvent dans les couches principales de WPF. Par exemple, <xref:System.Windows.FrameworkElement> fournit un accès direct à l’animation via la méthode <xref:System.Windows.FrameworkElement.BeginStoryboard%2A>. Une <xref:System.Windows.Media.Animation.Storyboard> permet de générer un script pour plusieurs animations sur un ensemble de propriétés.  
  
 Les deux éléments les plus importants que <xref:System.Windows.FrameworkElement> introduits sont la liaison de données et les styles.  
  
 Le sous-système de liaison de données dans WPF doit être relativement familier à toute personne qui a utilisé Windows Forms ou ASP.NET pour créer une application [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. Chaque système offre un moyen simple d’exprimer votre intention de lier une ou plusieurs propriétés d’un élément spécifique à une donnée. WPF prend entièrement en charge la liaison de propriété, la transformation et la liaison de liste.  
  
 L’une des fonctionnalités les plus intéressantes de la liaison de données dans WPF est l’introduction des modèles de données. Ils permettent de spécifier de manière déclarative comment afficher les données. Au lieu de créer une interface utilisateur personnalisée pouvant être liée à des données, vous pouvez contourner le problème et laisser les données déterminer l’affichage à créer.  
  
 Les styles constituent une forme légère de liaison de données. Vous pouvez utiliser les styles pour lier un jeu de propriétés d’une définition partagée à une ou plusieurs instances d’un élément. Les styles sont appliqués à un élément par référence explicite (en définissant la propriété <xref:System.Windows.FrameworkElement.Style%2A>) ou implicitement en associant un style au type CLR de l’élément.  
  
<a name="System_Windows_Controls_Control"></a>   
## <a name="systemwindowscontrolscontrol"></a>System.Windows.Controls.Control  
 La création de modèles est la fonctionnalité la plus importante du contrôle. Si vous considérez le système de composition de WPF comme un système de rendu en mode conservation, la création de modèles permet à un contrôle de décrire son rendu d’une manière déclarative et paramétrable. Un <xref:System.Windows.Controls.ControlTemplate> n’est rien de plus qu’un script pour créer un ensemble d’éléments enfants, avec des liaisons aux propriétés offertes par le contrôle.  
  
 <xref:System.Windows.Controls.Control> fournit un ensemble de propriétés stock, <xref:System.Windows.Controls.Control.Foreground%2A>, <xref:System.Windows.Controls.Control.Background%2A>, <xref:System.Windows.Controls.Control.Padding%2A>, pour n’en nommer que quelques-uns, que les auteurs de modèles peuvent ensuite utiliser pour personnaliser l’affichage d’un contrôle. L’implémentation d’un contrôle fournit un modèle de données et un modèle d’interaction. Le modèle d’interaction définit un jeu de commandes (Fermer une fenêtre, par exemple) et des liaisons aux mouvements d’entrée (comme le fait de cliquer sur le X rouge dans le coin supérieur d’une fenêtre). Le modèle de données fournit un jeu de propriétés pour personnaliser le modèle d’interaction ou l’affichage (déterminé par le modèle).  
  
 Cette distinction entre le modèle de données (propriétés), le modèle d’interaction (commandes et événements) et le modèle d’affichage (modèles) permet d’effectuer une personnalisation complète de l’apparence et du comportement d’un contrôle.  
  
 Le modèle de contenu est un aspect commun du modèle de données des contrôles. Si vous examinez un contrôle comme <xref:System.Windows.Controls.Button>, vous verrez qu’il a une propriété nommée « contenu » de type <xref:System.Object>. Dans Windows Forms et ASP.NET, cette propriété est généralement une chaîne, mais elle limite le type de contenu que vous pouvez placer dans un bouton. Le contenu d’un bouton peut être une chaîne simple, un objet de données complexe ou une arborescence entière d’éléments. Dans le cas d’un objet de données, le modèle de données sert à créer un affichage.  
  
<a name="Summary"></a>   
## <a name="summary"></a>Récapitulatif  
 WPF est conçu pour vous permettre de créer des systèmes de présentation dynamiques, pilotés par les données. Chaque partie du système est destinée à la création d’objets à l’aide de jeux de propriétés qui pilotent le comportement. La liaison de données est une fonctionnalité essentielle du système qui est intégrée au niveau de chaque couche.  
  
 Les applications standard créent un affichage, puis effectuent une liaison avec certaines données. Dans WPF, tout ce qui concerne le contrôle, tous les aspects de l’affichage, est généré par un certain type de liaison de données. Le texte placé dans un bouton est affiché en créant un contrôle composé à l’intérieur du bouton et en liant son affichage à la propriété de contenu du bouton.  
  
 Quand vous commencez à développer des applications basées sur WPF, vous devez vous sentir familier. Vous pouvez définir des propriétés, utiliser des objets et la liaison de données à peu près de la même façon que vous pouvez utiliser Windows Forms ou ASP.NET. Grâce à une investigation approfondie de l’architecture de WPF, vous constaterez qu’il existe une possibilité de créer des applications beaucoup plus riches qui traitent fondamentalement les données comme le pilote de base de l’application.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Media.Visual>
- <xref:System.Windows.UIElement>
- <xref:System.Windows.Input.ICommand>
- <xref:System.Windows.FrameworkElement>
- <xref:System.Windows.Threading.DispatcherObject>
- <xref:System.Windows.Input.CommandBinding>
- <xref:System.Windows.Controls.Control>
- [Vue d’ensemble de la liaison de données](../../../desktop-wpf/data/data-binding-overview.md)
- [Disposition](layout.md)
- [Vue d’ensemble de l’animation](../graphics-multimedia/animation-overview.md)
