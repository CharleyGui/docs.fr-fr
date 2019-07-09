---
title: Vue d'ensemble des événements routés
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- attached events [WPF]
- grouped button set [WPF]
- routed events [WPF]
- events [WPF], routed
- tunneling [WPF]
- events [WPF], attached
- routing strategies for events [WPF]
- button set [WPF], grouped
- bubbling [WPF]
ms.assetid: 1a2189ae-13b4-45b0-b12c-8de2e49c29d2
ms.openlocfilehash: e1e092e3dac481f28e2a355a22218cf86500b40e
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67660821"
---
# <a name="routed-events-overview"></a>Vue d'ensemble des événements routés

Cette rubrique explique le concept d’événements routés dans [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]. Elle définit les termes utilisés pour les événements routés, elle explique comment ces événements sont routés via une arborescence d’éléments, elle résume la façon dont sont gérés les événements routés et elle explique comment créer ses propres événements routés personnalisés.

<a name="prerequisites"></a>

## <a name="prerequisites"></a>Prérequis

Cette rubrique suppose que vous avez une connaissance élémentaire du [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] et de la programmation orientée objet, ainsi que de la façon dont les relations entre les éléments [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] peuvent être conceptualisées sous forme d’arborescence. Pour pouvoir suivre les exemples de cette rubrique, vous devez également connaître le [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] et savoir écrire des applications ou des pages [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] rudimentaires. Pour plus d’informations, consultez [Procédure pas à pas : Ma première application de bureau WPF](../getting-started/walkthrough-my-first-wpf-desktop-application.md) et [vue d’ensemble de XAML (WPF)](xaml-overview-wpf.md).

<a name="routing"></a>

## <a name="what-is-a-routed-event"></a>Qu’est-ce qu’un événement routé ?

Les événements routés peuvent être compris d’un point de vue fonctionnel et du point de vue de l’implémentation. Les deux définitions sont présentées ici pour une meilleure compréhension du concept.

Définition fonctionnelle : Un événement routé est un type d’événement qui peut appeler des gestionnaires sur plusieurs écouteurs dans une arborescence d’éléments, plutôt que simplement sur l’objet qui a déclenché l’événement.

Définition d’implémentation : Un événement routé est un [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] événement qui est stocké par une instance de la <xref:System.Windows.RoutedEvent> classe et est traitée par le [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] système d’événements.

Une application [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] type contient de nombreux éléments. Qu’ils soient créés dans le code ou déclarés dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], ces éléments sont reliés entre eux au sein d’une arborescence d’éléments. L’itinéraire de l’événement peut prendre deux directions différentes, en fonction de la définition de l’événement. Toutefois, l’itinéraire part en général de l’élément source et se propage ensuite vers le haut dans l’arborescence d’éléments, jusqu’à atteindre la racine de l’arborescence d’éléments (en général, une page ou une fenêtre). Le concept de propagation peut vous être familier si vous avez déjà travaillé avec le modèle d’objet DHTML.

Prenons l’arborescence d’éléments suivante :

[!code-xaml[EventOvwSupport#GroupButton](~/samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml#groupbutton)]

Cette arborescence d’éléments produit ce qui suit :

![Boutons Oui, Non et Annuler](./media/routedevent-ovw-1.gif "RoutedEvent_ovw_1")

Dans cette arborescence d’éléments simplifiée, la source d’un <xref:System.Windows.Controls.Primitives.ButtonBase.Click> événement est un de la <xref:System.Windows.Controls.Button> éléments et selon la <xref:System.Windows.Controls.Button> utilisateur a cliqué sur est le premier élément qui a la possibilité de gérer l’événement. Toutefois, si aucun gestionnaire n’attaché à la <xref:System.Windows.Controls.Button> agit sur l’événement, puis l’événement se propage vers le haut à la <xref:System.Windows.Controls.Button> parent dans l’arborescence d’éléments, qui est le <xref:System.Windows.Controls.StackPanel>. Potentiellement, à l’événement se propage à <xref:System.Windows.Controls.Border>et au-delà de la racine de la page de l’arborescence d’éléments (non illustré).

En d’autres termes, l’itinéraire d’événement pour ce <xref:System.Windows.Controls.Primitives.ButtonBase.Click> événement est :

Button-->StackPanel-->Border-->...

### <a name="top-level-scenarios-for-routed-events"></a>Scénarios de premier niveau pour les événements routés

Voici un récapitulatif des scénarios qui justifient l’utilisation des événements routés, et la raison pour laquelle un événement [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] type n’était pas adapté à ces scénarios :

**Composition de contrôle et l’encapsulation :** Divers contrôles dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ont un modèle de contenu riche. Par exemple, vous pouvez placer une image à l’intérieur d’un <xref:System.Windows.Controls.Button>, qui étend l’arborescence d’éléments visuels du bouton. Toutefois, l’image ajoutée ne doit pas perturber le comportement de test d’atteinte qui permet à un bouton répondre à une <xref:System.Windows.Controls.Primitives.ButtonBase.Click> de son contenu, même si l’utilisateur clique sur des pixels qui font techniquement partie de l’image.

**Points d’attachement de gestionnaire :** Dans [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)], vous seriez obligé d’attacher le même gestionnaire plusieurs fois pour traiter les événements qui peuvent être déclenchés à partir de plusieurs éléments. Les événements routés vous permettent d’attacher ce gestionnaire une seule fois, comme dans l’exemple précédent, et d’utiliser la logique du gestionnaire pour déterminer d’où provient l’événement, si nécessaire. Par exemple, ceci pourrait être le gestionnaire du [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] présenté précédemment :

[!code-csharp[EventOvwSupport#GroupButtonCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml.cs#groupbuttoncodebehind)]
[!code-vb[EventOvwSupport#GroupButtonCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/EventOvwSupport/visualbasic/default.xaml.vb#groupbuttoncodebehind)]

**Gestion de classe :** Acheminé permis un gestionnaire statique qui est défini par la classe d’événements. Ce gestionnaire de classe a l’opportunité de gérer un événement avant les autres gestionnaires d’instance attachés.

**Référencement d’un événement sans réflexion :** Certaines techniques de code et le balisage nécessitent un moyen d’identifier un événement spécifique. Un événement routé crée un <xref:System.Windows.RoutedEvent> champ en tant qu’identificateur, qui fournit une technique d’identification d’événement fiable ne nécessitant pas de réflexion statique ou d’exécution.

### <a name="how-routed-events-are-implemented"></a>Implémentation des événements routés

Un événement routé est un [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] événement qui est stocké par une instance de la <xref:System.Windows.RoutedEvent> classe et l’inscrit avec le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] système d’événements. Le <xref:System.Windows.RoutedEvent> instance obtenue à partir de l’inscription est généralement conservée comme un `public` `static` `readonly` membre de champ de la classe qui inscrit et donc « possède » l’événement routé. La connexion à l’événement [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] portant le même nom (qui est parfois appelé « événement wrapper ») est réalisée en substituant les implémentations `add` et `remove` pour l’événement [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]. En règle générale, `add` et `remove` sont conservés comme des valeurs implicites par défaut qui utilisent la syntaxe d’événement spécifique au langage pour ajouter et supprimer des gestionnaires de cet événement. Le mécanisme de connexion et de stockage des événements routés est conceptuellement semblable à la façon dont une propriété de dépendance est un [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] propriété qui est sauvegardée par le <xref:System.Windows.DependencyProperty> classe et l’inscrit avec le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] système de propriétés.

L’exemple suivant illustre la déclaration personnalisé `Tap` événement routé, y compris l’inscription et l’exposition de la <xref:System.Windows.RoutedEvent> champ d’identificateur et le `add` et `remove` implémentations pour les `Tap` [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] événement.

[!code-csharp[RoutedEventCustom#AddRemoveHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventCustom/CSharp/SDKSampleLibrary/class1.cs#addremovehandler)]
[!code-vb[RoutedEventCustom#AddRemoveHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventCustom/VB/SDKSampleLibrary/Class1.vb#addremovehandler)]

### <a name="routed-event-handlers-and-xaml"></a>Gestionnaires d’événements routés et XAML

Pour ajouter un gestionnaire à un événement à l’aide de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], déclarez le nom de l’événement en tant qu’attribut sur l’élément qui joue le rôle d’écouteur d’événements. La valeur de l’attribut est le nom de votre méthode de gestionnaire implémentée, qui doit se trouver dans la classe partielle du fichier code-behind.

[!code-xaml[EventOvwSupport#SimplestSyntax](~/samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml#simplestsyntax)]

La syntaxe [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] permettant d’ajouter des gestionnaires d’événements [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] standard est identique à celle utilisée pour ajouter des gestionnaires d’événements routés, car vous ajoutez des gestionnaires au wrapper d’événement [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)], sous lequel se trouve une implémentation d’événement routé. Pour plus d’informations sur l’ajout de gestionnaires d’événements dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], consultez [Vue d’ensemble du langage XAML (WPF)](xaml-overview-wpf.md).

<a name="routing_strategies"></a>

## <a name="routing-strategies"></a>Stratégies de routage

Les événements routés utilisent l’une des trois stratégies de routage suivantes :

- **Propagation :** Gestionnaires d’événements sur la source d’événements sont appelés. L’événement routé est acheminé ensuite vers des éléments parents successifs jusqu’à atteindre la racine de l’arborescence d’éléments. La plupart des événements routés utilisent la stratégie de routage par propagation. Les événements routés par propagation sont généralement utilisés pour signaler des entrées ou des changements d’état à partir de contrôles distincts ou d’autres éléments d’interface utilisateur.

- **Direct :** Seul l’élément de source est la possibilité d’appeler des gestionnaires en réponse. Cela s’apparente au « routage » que [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] utilise pour les événements. Toutefois, contrairement à une norme [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] événement, diriger les événements routés prennent en charge la gestion de classe (gestion de classe est expliquée dans une section à venir) et peut être utilisé par <xref:System.Windows.EventSetter> et <xref:System.Windows.EventTrigger>.

- **Tunneling :** Initialement, les gestionnaires d’événements à la racine d’arborescence des éléments sont appelés. L’événement routé passe ensuite par des éléments enfants successifs pour aller vers l’élément de nœud correspondant à la source de l’événement routé (l’élément qui a déclenché l’événement routé). Les événements routés de tunneling sont souvent utilisés ou gérés dans le cadre de la composition d’un contrôle, de telle manière que les événements issus de parties composites peuvent être délibérément supprimés ou remplacés par des événements spécifiques au contrôle complet. Les événements d’entrée fournis dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sont souvent implémentés comme une paire tunneling/propagation. Les événements de tunneling sont parfois appelés événements Preview en raison d’une convention de nommage utilisée pour les paires.

<a name="why_use"></a>

## <a name="why-use-routed-events"></a>Pourquoi utiliser des événements routés ?

En tant que développeur d’applications, il n’est pas toujours nécessaire de savoir que l’événement que vous gérez est implémenté comme un événement routé. Les événements routés présentent un comportement particulier, mais ce comportement est en grande partie invisible si vous gérez l’événement sur l’élément à partir duquel il a été déclenché.

Les événements routés deviennent puissants lorsqu’ils sont utilisés dans l’un des scénarios suivants : définition de gestionnaires communs au niveau d’une racine commune, composition de votre propre contrôle ou définition de votre propre classe de contrôle personnalisé.

Les écouteurs et les sources d’événements routés n’ont pas besoin de partager un événement commun dans leur hiérarchie. N’importe quel <xref:System.Windows.UIElement> ou <xref:System.Windows.ContentElement> peut être un écouteur d’événements pour tout événement routé. Par conséquent, vous pouvez utiliser l’ensemble des événements routés disponibles dans l’API de travail définie comme conceptuelle « interface » différents éléments dans l’application peuvent échanger des informations sur les événements. Ce concept d’« interface » pour les événements routés s’applique plus particulièrement aux événements d’entrée.

Les événements routés peuvent également servir à communiquer au sein de l’arborescence d’éléments, car les données de l’événement sont propagées vers chaque élément rencontré sur l’itinéraire. Si un élément change les données d’événement, ce changement est disponible pour l’élément suivant dans l’itinéraire.

Outre l’aspect du routage, il existe deux autres raisons pour lesquelles un événement [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] peut être implémenté comme un événement routé au lieu d’un événement [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] standard. Si vous implémentez vos propres événements, vous pouvez également prendre en compte ces principes :

- Certains [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fonctionnalités telles que des styles et modèles <xref:System.Windows.EventSetter> et <xref:System.Windows.EventTrigger> l’événement référencé doit être un événement routé. Il s’agit du scénario d’identificateur d’événement mentionné précédemment.

- Les événements routés prennent en charge un mécanisme de gestion de classe par lequel la classe peut spécifier des méthodes statiques qui ont l’opportunité de gérer des événements routés avant que les gestionnaires d’instance inscrits puissent y accéder. Ceci est très utile pour la conception de contrôles, car la classe peut appliquer des comportements de classe pilotés par les événements qui ne peuvent pas être supprimés par inadvertance lorsque vous gérez un événement sur une instance.

Toutes les considérations ci-dessus sont abordées dans une autre section de cette rubrique.

<a name="event_handing"></a>

## <a name="adding-and-implementing-an-event-handler-for-a-routed-event"></a>Ajout et implémentation d’un gestionnaire d’événements pour un événement routé

Pour ajouter un gestionnaire d’événements dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], ajoutez le nom de l’événement à un élément en tant qu’attribut, et définissez la valeur de l’attribut sur le nom du gestionnaire d’événements qui implémente un délégué, comme dans l’exemple suivant.

[!code-xaml[EventOvwSupport#SimplestSyntax](~/samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml#simplestsyntax)]

`b1SetColor` est le nom du gestionnaire implémenté qui contient le code qui gère la <xref:System.Windows.Controls.Primitives.ButtonBase.Click> événement. `b1SetColor` doit avoir la même signature que le <xref:System.Windows.RoutedEventHandler> délégué, qui est le délégué de gestionnaire d’événements pour le <xref:System.Windows.Controls.Primitives.ButtonBase.Click> événement. Le premier paramètre de tous les délégués de gestionnaires d’événements routés spécifie l’élément auquel le gestionnaire d’événements est ajouté, et le deuxième paramètre spécifie les données de l’événement.

[!code-csharp[EventOvwSupport#SimpleHandlerA](~/samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml.cs#simplehandlera)]
[!code-vb[EventOvwSupport#SimpleHandlerA](~/samples/snippets/visualbasic/VS_Snippets_Wpf/EventOvwSupport/visualbasic/default.xaml.vb#simplehandlera)]

<xref:System.Windows.RoutedEventHandler> est le délégué de gestionnaire d’événements routés de base. Pour les événements routés qui conviennent spécialement à certains contrôles ou scénarios, les délégués à utiliser avec les gestionnaires d’événements routés peuvent également devenir plus spécialisés, de manière à pouvoir transmettre des données d’événement spécialisées. Par exemple, dans un scénario d’entrée courant, vous pouvez gérer un <xref:System.Windows.UIElement.DragEnter> événement routé. Le gestionnaire doit implémenter le <xref:System.Windows.DragEventHandler> déléguer. À l’aide du délégué le plus spécifique, vous pouvez traiter la <xref:System.Windows.DragEventArgs> dans le gestionnaire et lire le <xref:System.Windows.DragEventArgs.Data%2A> propriété, qui contient la charge utile de Presse-papiers de l’opération glisser.

Pour un exemple complet montrant comment ajouter un gestionnaire d’événements à un élément à l’aide de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], consultez [Gérer un événement routé](how-to-handle-a-routed-event.md).

L’ajout d’un gestionnaire pour un événement routé dans une application créée dans du code est une opération simple. Gestionnaires d’événements routés peuvent toujours être ajoutés via une méthode d’assistance <xref:System.Windows.UIElement.AddHandler%2A> (qui est la même méthode que le stockage appelle pour `add`.) Toutefois, les événements routés [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] existants disposent généralement d’implémentations de stockage de logique `add` et `remove` qui permettent aux gestionnaires d’événements routés d’être ajoutés à une syntaxe d’événement spécifique au langage, qui est une syntaxe plus intuitive que celle de la méthode d’assistance. Voici un exemple d’utilisation de la méthode d’assistance :

[!code-csharp[EventOvwSupport#AddHandlerCode](~/samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml.cs#addhandlercode)]
[!code-vb[EventOvwSupport#AddHandlerCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/EventOvwSupport/visualbasic/default.xaml.vb#addhandlercode)]

L’exemple suivant montre le C# syntaxe d’opérateur (Visual Basic a une syntaxe d’opérateur légèrement différente en raison de la gestion du déréférencement) :

[!code-csharp[EventOvwSupport#AddHandlerPlusEquals](~/samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml.cs#addhandlerplusequals)]
[!code-vb[EventOvwSupport#AddHandlerPlusEquals](~/samples/snippets/visualbasic/VS_Snippets_Wpf/EventOvwSupport/visualbasic/default.xaml.vb#addhandlerplusequals)]

Pour obtenir un exemple montrant comment ajouter un gestionnaire d’événements dans le code, consultez [Ajouter un gestionnaire d’événements à l’aide de code](how-to-add-an-event-handler-using-code.md).

Si vous utilisez Visual Basic, vous pouvez également utiliser le `Handles` mot clé pour ajouter des gestionnaires dans le cadre des déclarations du gestionnaire. Pour plus d’informations, consultez [Gestion des événements Visual Basic et WPF](visual-basic-and-wpf-event-handling.md).

<a name="concept_handled"></a>

### <a name="the-concept-of-handled"></a>Concept du Handled

Tous les événements routés partagent une événement données classe de base commune, <xref:System.Windows.RoutedEventArgs>. <xref:System.Windows.RoutedEventArgs> définit le <xref:System.Windows.RoutedEventArgs.Handled%2A> propriété, qui prend une valeur booléenne. L’objectif de la <xref:System.Windows.RoutedEventArgs.Handled%2A> propriété consiste à activer n’importe quel gestionnaire d’événements sur l’itinéraire de marquer l’événement routé comme *gérée*, en définissant la valeur de <xref:System.Windows.RoutedEventArgs.Handled%2A> à `true`. Après avoir été traitées par le gestionnaire au niveau d’un élément de l’itinéraire, les données d’événement partagées sont à nouveau signalées à chaque écouteur se trouvant sur l’itinéraire.

La valeur de <xref:System.Windows.RoutedEventArgs.Handled%2A> affecte comment un événement routé est signalé ou traité lorsqu’il parcourt plus loin sur l’itinéraire. Si <xref:System.Windows.RoutedEventArgs.Handled%2A> est `true` de l’événement données pour un événement routé, les gestionnaires qui écoutent cet événement routé sur d’autres éléments sont généralement plus appelées pour cette instance d’événement particulier. Ceci est vrai à la fois pour les gestionnaires attachés dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] et pour ceux ajoutés par des syntaxes d’attachement de gestionnaire d’événements spécifiques au langage, comme `+=` ou `Handles`. Pour les scénarios courants impliquant des gestionnaires, marquer un événement comme géré en définissant <xref:System.Windows.RoutedEventArgs.Handled%2A> à `true` sera « arrêter » de routage pour un itinéraire de tunneling ou un itinéraire de propagation et également pour tout événement qui est géré à un point dans l’itinéraire par un gestionnaire de classe.

Toutefois, il existe un mécanisme « handledEventsToo » par laquelle écouteurs d’exécuter des gestionnaires en réponse aux événements routés où <xref:System.Windows.RoutedEventArgs.Handled%2A> est `true` dans les données d’événement. En d’autres termes, l’itinéraire d’événement n’est pas réellement arrêté quand les données d’événement sont marquées comme gérées. Vous pouvez uniquement utiliser le mécanisme handledEventsToo dans le code ou dans un <xref:System.Windows.EventSetter>:

- Dans le code, au lieu d’utiliser une syntaxe d’événement spécifique au langage qui fonctionne pour général [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] événements, appelez le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] méthode <xref:System.Windows.UIElement.AddHandler%28System.Windows.RoutedEvent%2CSystem.Delegate%2CSystem.Boolean%29> pour ajouter votre gestionnaire. Définissez la valeur de `handledEventsToo` sur `true`.

- Dans un <xref:System.Windows.EventSetter>, définissez le <xref:System.Windows.EventSetter.HandledEventsToo%2A> attribut soit `true`.

Outre le comportement qui <xref:System.Windows.RoutedEventArgs.Handled%2A> état se produit dans les événements routés, le concept de <xref:System.Windows.RoutedEventArgs.Handled%2A> a des conséquences sur la façon dont vous devez concevoir votre application et écrire le code de gestionnaire d’événements. Vous pouvez conceptualiser <xref:System.Windows.RoutedEventArgs.Handled%2A> comme étant un protocole simple qui est exposé par les événements routés. Exactement comment vous utilisez ce protocole est à vous, mais le modèle conceptuel d’une façon la valeur de <xref:System.Windows.RoutedEventArgs.Handled%2A> est destinée à être utilisée est la suivante :

- Si un événement routé est marqué comme géré, il n’a pas besoin d’être géré de nouveau par d’autres éléments sur l’itinéraire.

- Si un événement routé n’est pas marqué comme géré, alors que les autres écouteurs situés en amont sur l’itinéraire ont choisi ne pas inscrire de gestionnaire ou les gestionnaires inscrits ont choisi de pas à manipuler les données d’événement et de définir <xref:System.Windows.RoutedEventArgs.Handled%2A> à `true`. Il est également possible que l’écouteur actuel soit le premier de l’itinéraire. Les gestionnaires de l’écouteur actuel ont maintenant trois possibilités :

  - Ne rien faire. L’événement reste non géré et l’événement est dirigé vers l’écouteur suivant.

  - Exécuter du code en réponse à l’événement, mais décider que l’action entreprise n’était pas suffisamment importante pour garantir le marquage de l’événement comme géré. L’événement est dirigé vers l’écouteur suivant.

  - Exécuter du code en réponse à l’événement. Marquer l’événement comme géré dans les données d’événement passées au gestionnaire, car l’action entreprise est jugée suffisamment importante pour garantir le marquage de l’événement comme géré. L’événement est encore dirigé vers l’écouteur suivant, mais avec <xref:System.Windows.RoutedEventArgs.Handled%2A> = `true` dans ses données d’événement, afin que seuls `handledEventsToo` écouteurs ont la possibilité d’appeler les gestionnaires.

Cette étude conceptuelle est renforcée par le comportement de routage mentionné précédemment : il est plus difficile (bien que possible dans le code ou les styles) pour joindre des gestionnaires pour les événements routés qui sont appelés même si un gestionnaire précédent le long de l’itinéraire a déjà défini <xref:System.Windows.RoutedEventArgs.Handled%2A>à `true`.

Pour plus d’informations sur <xref:System.Windows.RoutedEventArgs.Handled%2A>, classe qui gère les événements routés, et des recommandations sur le moment où il est approprié pour marquer un événement routé comme <xref:System.Windows.RoutedEventArgs.Handled%2A>, consultez [marquage des événements routés comme gérés et gestion de classe](marking-routed-events-as-handled-and-class-handling.md).

Dans les applications, il est assez courant de gérer un événement routé par propagation sur l’objet qui l’a déclenché, sans se soucier des caractéristiques de routage de l’événement. Toutefois, il est recommandé de toujours marquer l’événement routé comme géré (handled) dans les données d’événement, afin d’éviter des effets secondaires si un élément situé plus haut dans l’arborescence d’éléments comportait également un gestionnaire attaché pour le même événement routé.

<a name="class_handlers"></a>

## <a name="class-handlers"></a>Gestionnaires de classe

Si vous définissez une classe qui dérive d’une certaine façon à partir de <xref:System.Windows.DependencyObject>, vous pouvez également définir et attacher un gestionnaire de classe pour un événement routé qui est un membre d’événement déclaré ou hérité de votre classe. Les gestionnaires de classe sont appelés avant les gestionnaires d’écouteur d’instance qui sont attachés à une instance de cette classe, chaque fois qu’un événement routé atteint une instance d’élément sur son itinéraire.

Certains contrôles [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] disposent d’une gestion de classe inhérente pour certains événements routés. Ceci peut donner l’apparence que l’événement routé n’a même pas été déclenché, alors qu’en réalité il est géré par la classe, et peut encore potentiellement être géré par vos gestionnaires d’instance si vous utilisez certaines techniques. En outre, plusieurs classes et contrôles de base exposent des méthodes virtuelles qui peuvent être utilisées pour substituer le comportement de gestion de classe. Pour plus d’informations sur la façon de contourner la gestion de classe et sur la définition de votre propre gestion de classe dans une classe personnalisée, consultez [Marquage des événements routés comme gérés et gestion de classe](marking-routed-events-as-handled-and-class-handling.md).

<a name="attached_events"></a>

## <a name="attached-events-in-wpf"></a>Événements attachés dans WPF

Le langage [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] définit également un type particulier d’événement appelé *événement attaché*. Un événement attaché permet d’ajouter le gestionnaire d’un événement particulier à un élément arbitraire. L’élément qui gère l’événement n’a pas besoin de définir ou d’hériter de l’événement attaché. En outre, ni l’objet qui déclenche potentiellement l’événement, ni l’instance de gestion de destination ne doivent définir ou « posséder » cet événement comme un membre de classe.

Le système d’entrée [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] utilise largement les événements attachés. Cependant, presque tous ces événements attachés sont transférés via des éléments de base. Les événements d’entrée apparaissent alors comme des événements routés non attachés équivalents qui sont membres de la classe d’élément de base. Par exemple, de la sous-jacent d’un événement attaché <xref:System.Windows.Input.Mouse.MouseDown?displayProperty=nameWithType> peuvent être plus facilement géré sur n’importe quel donné <xref:System.Windows.UIElement> à l’aide de <xref:System.Windows.UIElement.MouseDown> sur qui <xref:System.Windows.UIElement> plutôt que le traitement soit avec la syntaxe de l’événement attaché dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ou du code.

Pour plus d’informations sur les événements attachés dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], consultez [Vue d’ensemble des événements attachés](attached-events-overview.md).

<a name="Qualifying_Event_Names_in_XAML_for_Anticipated_Routing"></a>

## <a name="qualified-event-names-in-xaml"></a>Noms qualifiés d’événements en XAML

Une autre utilisation de la syntaxe qui ressemble à la syntaxe d’événement attaché *typename*.*eventname*, mais qui n’est pas à proprement parler une utilisation d’événement attaché est lorsque vous attachez des gestionnaires pour les événements routés qui sont déclenchés par des éléments enfants. Vous attachez les gestionnaires à un parent commun pour tirer parti du routage d’événements, même si le parent commun ne dispose pas de l’événement routé nécessaire comme membre. Regardons de nouveau cet exemple :

[!code-xaml[EventOvwSupport#GroupButton](~/samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml#groupbutton)]

Ici, l’écouteur d’élément parent dans lequel le gestionnaire est ajouté est un <xref:System.Windows.Controls.StackPanel>. Toutefois, il ajoute un gestionnaire pour un événement routé qui a été déclaré et sera déclenché par la <xref:System.Windows.Controls.Button> classe (<xref:System.Windows.Controls.Primitives.ButtonBase> en réalité, mais disponible pour <xref:System.Windows.Controls.Button> par héritage). <xref:System.Windows.Controls.Button> « possède » l’événement, mais les système d’événements routés autorise des gestionnaires pour tout événement routé d’être attaché à aucun <xref:System.Windows.UIElement> ou <xref:System.Windows.ContentElement> écouteur d’instance qui pourrait attacher des écouteurs pour un [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] événement. L’espace de noms xmlns par défaut pour ces noms d’attributs d’événement qualifiés est généralement l’espace de noms xmlns [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] par défaut. Cependant, vous pouvez spécifier des espaces de noms avec préfixe pour les événements routés personnalisés. Pour plus d’informations sur xmlns, consultez [Espaces de noms XAML et mappage d’espace de noms pour XAML WPF](xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).

<a name="how_event_processing_works"></a>

## <a name="wpf-input-events"></a>Événements d’entrée WPF

Les événements routés sont fréquemment utilisés dans la plateforme [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pour les événements d’entrée. Par convention, dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], les noms d’événements routés par tunneling comprennent le préfixe « Preview ». Les événements d’entrée vont souvent par paires, l’un étant l’événement de propagation et l’autre, l’événement de tunneling. Par exemple, le <xref:System.Windows.ContentElement.KeyDown> événement et le <xref:System.Windows.ContentElement.PreviewKeyDown> événements ont la même signature, le premier étant l’événement d’entrée de propagation et cette dernière étant le tunneling des événements d’entrée. Parfois, les événements d’entrée ont uniquement une version par propagation, ou uniquement une version à routage direct. Dans la documentation, les rubriques relatives aux événements routés font référence à des événements routés similaires avec d’autres stratégies de routage, et les sections des pages concernant les références managées expliquent plus en détail la stratégie de routage de chaque événement routé.

Les événements d’entrée [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fournis par paires sont implémentés de telle sorte qu’une seule opération d’entrée, comme un clic de souris, déclenche les deux événements de la paire l’un après l’autre. Tout d’abord, l’événement de tunneling est déclenché et suit son itinéraire. Ensuite, l’événement de propagation est déclenché et suit son itinéraire. Les deux événements partagent littéralement la même instance de données de l’événement, car le <xref:System.Windows.UIElement.RaiseEvent%2A> appel de méthode dans la classe d’implémentation qui déclenche l’événement de propagation écoute pour les données d’événement à partir de l’événement de tunneling et les réutilise dans le nouvel événement déclenché. Les écouteurs qui comportent des gestionnaires pour l’événement de tunneling sont les premiers à pouvoir marquer l’événement routé comme géré (d’abord les gestionnaires de classe, ensuite les gestionnaires d’instance). Si un élément a marqué l’événement routé comme géré sur l’itinéraire de tunneling, les données d’événement déjà gérées sont envoyées à l’événement de propagation, et les gestionnaires standard attachés pour les événements d’entrée de propagation équivalents ne sont pas appelés. Vu de l’extérieur, il peut sembler que l’événement de propagation géré n’a pas encore été déclenché. Ce comportement de gestion est utile pour la composition de contrôles, où vous pouvez souhaiter que tous les événements d’entrée basés sur les tests d’atteinte ou le focus soient signalés par votre dernier contrôle, plutôt que par ses parties composites. Le dernier élément de contrôle est plus proche de la racine dans la composition et peut donc être le premier à gérer la classe de l’événement de tunneling et éventuellement à « remplacer » l’événement routé par un événement plus spécifique au contrôle dans le code qui stocke la classe de contrôle.

En guise d’illustration du traitement des événements d’entrée, prenez l’exemple d’événement d’entrée suivant. Dans l’illustration suivante de l’arborescence, `leaf element #2` est la source d’un `PreviewMouseDown` , puis un `MouseDown` événement :

![Diagramme de routage d'événements](./media/routed-events-overview/input-event-routing.png)

L’ordre de traitement des événements est le suivant :

1. `PreviewMouseDown` (tunneling) sur l’élément racine.

2. `PreviewMouseDown` (tunneling) sur l’élément intermédiaire numéro 1.

3. `PreviewMouseDown` (tunneling) sur l’élément source numéro 2.

4. `MouseDown` (propagation) sur l’élément source numéro 2.

5. `MouseDown` (propagation) sur l’élément intermédiaire numéro 1.

6. `MouseDown` (propagation) sur l’élément racine.

Un délégué de gestionnaire d’événements routés fournit des références à deux objets : l’objet qui a déclenché l’événement et l’objet à partir duquel le gestionnaire a été appelé. L’objet à partir duquel le gestionnaire a été appelé est celui signalé par le paramètre `sender`. L’objet où l’événement a été déclenché pour la première est signalée par le <xref:System.Windows.RoutedEventArgs.Source%2A> propriété dans les données d’événement. Un événement routé peut toujours être déclenché et géré par le même objet, auquel cas `sender` et <xref:System.Windows.RoutedEventArgs.Source%2A> sont identiques (ce qui est le cas avec les étapes 3 et 4 de l’événement de traitement d’exemple de liste).

En raison de tunneling et de propagation, les éléments parents reçoivent des événements d’entrée où la <xref:System.Windows.RoutedEventArgs.Source%2A> est un de leurs enfants éléments. Lorsqu’il est important de savoir qui est l’élément source, vous pouvez identifier l’élément source en accédant à la <xref:System.Windows.RoutedEventArgs.Source%2A> propriété.

En règle générale, une fois que l’événement d’entrée est marqué comme <xref:System.Windows.RoutedEventArgs.Handled%2A>, plus les gestionnaires ne sont pas appelés. En outre, vous devez marquer les événements d’entrée comme gérés dès qu’un gestionnaire est appelé pour traiter votre gestion logique (et spécifique à l’application) de la signification de l’événement d’entrée.

L’exception à cette déclaration générale sur <xref:System.Windows.RoutedEventArgs.Handled%2A> état est que les gestionnaires d’événements qui sont inscrits pour ignorer délibérément l’entrée <xref:System.Windows.RoutedEventArgs.Handled%2A> état des données d’événement peuvent encore être appelé sur l’itinéraire. Pour plus d’informations, consultez [Événements Preview](preview-events.md) ou [Marquage des événements routés comme gérés et gestion de classe](marking-routed-events-as-handled-and-class-handling.md).

Le modèle de données d’événement partagé entre les événements de tunneling et de propagation, avec le déclenchement séquentiel de l’événement de tunneling puis de l’événement de propagation, est un concept qui n’est pas valable pour tous les événements routés. Ce comportement est implémenté selon la manière dont les périphériques d’entrée [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] choisissent de déclencher et de connecter les paires d’événements d’entrée. L’implémentation de vos propres événements d’entrée est un scénario avancé. Toutefois, vous pouvez choisir de suivre ce modèle pour vos propres événements d’entrée.

Certaines classes choisissent de gérer la classe de certains événements d’entrée, généralement dans le but de redéfinir la signification d’un événement d’entrée piloté par l’utilisateur dans le contrôle, et dans le but de déclencher un nouvel événement. Pour plus d’informations, consultez [Marquage des événements routés comme gérés et gestion de classe](marking-routed-events-as-handled-and-class-handling.md).

Pour plus d’informations sur les entrées et la façon dont elles interagissent avec les événements dans des scénarios d’application standard, consultez [Vue d’ensemble des entrées](input-overview.md).

<a name="events_styles"></a>

## <a name="eventsetters-and-eventtriggers"></a>EventSetters et EventTriggers

Dans les styles, vous pouvez inclure certains prédéclarés [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] gestion de syntaxe dans le balisage à l’aide d’événements un <xref:System.Windows.EventSetter>. Lorsque le style est appliqué, le gestionnaire référencé est ajouté à l’instance à laquelle est appliqué le style. Vous pouvez déclarer un <xref:System.Windows.EventSetter> uniquement pour un événement routé. Voici un exemple. Notez que la méthode `b1SetColor` référencée ici se trouve dans un fichier code-behind.

[!code-xaml[EventOvwSupport#XAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/page2.xaml#xaml2)]

L’avantage est que le style est susceptible de contenir un grand nombre d’autres informations qui peuvent s’appliquer à n’importe quel bouton dans votre application, et avoir le <xref:System.Windows.EventSetter> faire partie de ce style favorise la réutilisation de code même au niveau du balisage. En outre, un <xref:System.Windows.EventSetter> isole les noms de méthode pour les gestionnaires encore plus loin en dehors de la balise d’application et de la page générale.

Une autre syntaxe spéciale qui combine les fonctionnalités d’animation et les événements routées de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] est un <xref:System.Windows.EventTrigger>. Comme avec <xref:System.Windows.EventSetter>, uniquement les événements routés peuvent être utilisés pour un <xref:System.Windows.EventTrigger>. En règle générale, un <xref:System.Windows.EventTrigger> est déclaré en tant que partie d’un style, mais un <xref:System.Windows.EventTrigger> peuvent également être déclarées sur des éléments de page dans le cadre de la <xref:System.Windows.FrameworkElement.Triggers%2A> collection, ou dans un <xref:System.Windows.Controls.ControlTemplate>. Un <xref:System.Windows.EventTrigger> vous permet de spécifier un <xref:System.Windows.Media.Animation.Storyboard> que s’exécute chaque fois qu’un événement routé atteint un élément sur son itinéraire qui déclare un <xref:System.Windows.EventTrigger> pour cet événement. L’avantage d’un <xref:System.Windows.EventTrigger> sur simplement gérant l’événement et au démarrage un storyboard existant qui est un <xref:System.Windows.EventTrigger> offre un meilleur contrôle sur la table de montage séquentiel et son comportement au moment de l’exécution. Pour plus d’informations, consultez [Utiliser des déclencheurs d’événements pour contrôler un storyboard après son démarrage](../graphics-multimedia/how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md).

<a name="more_about"></a>

## <a name="more-about-routed-events"></a>Informations complémentaires sur les événements routés

Cette rubrique traite principalement des concepts de base relatifs aux événements routés, et explique comment et à quel moment répondre aux événements routés qui sont déjà présents dans les différents éléments et contrôles de base. Toutefois, vous pouvez créer vos propres événements routés dans votre classe personnalisée, ainsi que toute la prise en charge nécessaire, telle que les classes et les délégués spécialisés de données d’événement. Le propriétaire de l’événement routé peut être n’importe quelle classe, mais les événements routés doivent être déclenchés par et gérées par <xref:System.Windows.UIElement> ou <xref:System.Windows.ContentElement> classes dérivées pour pouvoir être utiles. Pour plus d’informations sur les événements personnalisés, consultez [Créer un événement routé personnalisé](how-to-create-a-custom-routed-event.md).

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.EventManager>
- <xref:System.Windows.RoutedEvent>
- <xref:System.Windows.RoutedEventArgs>
- [Marquage des événements routés comme gérés et gestion de classe](marking-routed-events-as-handled-and-class-handling.md)
- [Vue d’ensemble des entrées](input-overview.md)
- [Vue d’ensemble des commandes](commanding-overview.md)
- [Propriétés de dépendance personnalisées](custom-dependency-properties.md)
- [Arborescences dans WPF](trees-in-wpf.md)
- [Modèles d’événement faible](weak-event-patterns.md)
