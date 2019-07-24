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
ms.openlocfilehash: 24fa283ec0c1fef2023845df0a05c3f1ebf5df06
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68400752"
---
# <a name="routed-events-overview"></a>Vue d'ensemble des événements routés

Cette rubrique explique le concept d’événements routés dans [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]. Elle définit les termes utilisés pour les événements routés, elle explique comment ces événements sont routés via une arborescence d’éléments, elle résume la façon dont sont gérés les événements routés et elle explique comment créer ses propres événements routés personnalisés.

<a name="prerequisites"></a>

## <a name="prerequisites"></a>Prérequis

Cette rubrique suppose que vous avez une connaissance de base des Common Language Runtime (CLR) et de la programmation orientée objet, ainsi que le concept de la manière dont [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] les relations entre les éléments peuvent être conceptuelles comme une arborescence. Pour pouvoir suivre les exemples de cette rubrique, vous devez également connaître le [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] et savoir écrire des applications ou des pages [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] rudimentaires. Pour plus d’informations, consultez [Procédure pas à pas : Ma première application](../getting-started/walkthrough-my-first-wpf-desktop-application.md) de bureau WPF et [vue d’ensemble du langage XAML (WPF)](xaml-overview-wpf.md).

<a name="routing"></a>

## <a name="what-is-a-routed-event"></a>Qu’est-ce qu’un événement routé ?

Les événements routés peuvent être compris d’un point de vue fonctionnel et du point de vue de l’implémentation. Les deux définitions sont présentées ici pour une meilleure compréhension du concept.

Définition fonctionnelle: Un événement routé est un type d’événement qui peut appeler des gestionnaires sur plusieurs écouteurs dans une arborescence d’éléments, plutôt que sur l’objet qui a déclenché l’événement.

Définition d’implémentation: Un événement routé est un événement CLR qui est stocké par une instance de la <xref:System.Windows.RoutedEvent> classe et qui est traité par le [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] système d’événements.

Une application [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] type contient de nombreux éléments. Qu’ils soient créés dans le code ou déclarés dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], ces éléments sont reliés entre eux au sein d’une arborescence d’éléments. L’itinéraire de l’événement peut prendre deux directions différentes, en fonction de la définition de l’événement. Toutefois, l’itinéraire part en général de l’élément source et se propage ensuite vers le haut dans l’arborescence d’éléments, jusqu’à atteindre la racine de l’arborescence d’éléments (en général, une page ou une fenêtre). Le concept de propagation peut vous être familier si vous avez déjà travaillé avec le modèle d’objet DHTML.

Prenons l’arborescence d’éléments suivante :

[!code-xaml[EventOvwSupport#GroupButton](~/samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml#groupbutton)]

Cette arborescence d’éléments produit ce qui suit :

![Boutons Oui, Non et Annuler](./media/routedevent-ovw-1.gif "RoutedEvent_ovw_1")

Dans cette arborescence d’éléments simplifiée, la source <xref:System.Windows.Controls.Primitives.ButtonBase.Click> d’un événement est l' <xref:System.Windows.Controls.Button> un des éléments et <xref:System.Windows.Controls.Button> l’élément sur lequel l’utilisateur a cliqué est le premier élément qui a la possibilité de gérer l’événement. Toutefois, si aucun gestionnaire attaché à <xref:System.Windows.Controls.Button> n’agit sur l’événement, l’événement se propage vers le <xref:System.Windows.Controls.Button> haut jusqu’au parent dans l’arborescence d’éléments, qui est <xref:System.Windows.Controls.StackPanel>le. Potentiellement, l’événement se propage <xref:System.Windows.Controls.Border>à, puis au-delà de la racine de la page de l’arborescence d’éléments (non affiché).

En d’autres termes, l’itinéraire d’événement <xref:System.Windows.Controls.Primitives.ButtonBase.Click> pour cet événement est le suivant:

Button-->StackPanel-->Border-->...

### <a name="top-level-scenarios-for-routed-events"></a>Scénarios de premier niveau pour les événements routés

Voici un bref résumé des scénarios qui ont motivé le concept d’événement routé et pourquoi un événement CLR typique n’était pas adapté à ces scénarios:

**Composition et encapsulation des contrôles:** Différents contrôles dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ont un modèle de contenu riche. Par exemple, vous pouvez placer une image à l’intérieur <xref:System.Windows.Controls.Button>d’un, ce qui étend efficacement l’arborescence d’éléments visuels du bouton. Toutefois, l’image ajoutée ne doit pas rompre le comportement de test d’atteinte qui provoque la réponse d' <xref:System.Windows.Controls.Primitives.ButtonBase.Click> un bouton à un de son contenu, même si l’utilisateur clique sur des pixels qui font techniquement partie de l’image.

**Points d’attachement du gestionnaire singuliers:** Dans [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)], vous devez attacher le même gestionnaire plusieurs fois pour traiter les événements qui peuvent être déclenchés à partir de plusieurs éléments. Les événements routés vous permettent d’attacher ce gestionnaire une seule fois, comme dans l’exemple précédent, et d’utiliser la logique du gestionnaire pour déterminer d’où provient l’événement, si nécessaire. Par exemple, ceci pourrait être le gestionnaire du [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] présenté précédemment :

[!code-csharp[EventOvwSupport#GroupButtonCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml.cs#groupbuttoncodebehind)]
[!code-vb[EventOvwSupport#GroupButtonCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/EventOvwSupport/visualbasic/default.xaml.vb#groupbuttoncodebehind)]

**Gestion des classes:** Les événements routés autorisent un gestionnaire statique qui est défini par la classe. Ce gestionnaire de classe a l’opportunité de gérer un événement avant les autres gestionnaires d’instance attachés.

**Référencement d’un événement sans réflexion:** Certaines techniques de code et de balisage requièrent un moyen d’identifier un événement spécifique. Un événement routé crée un <xref:System.Windows.RoutedEvent> champ en tant qu’identificateur, ce qui fournit une technique d’identification d’événement robuste qui ne nécessite pas de réflexion statique ou au moment de l’exécution.

### <a name="how-routed-events-are-implemented"></a>Implémentation des événements routés

Un événement routé est un événement CLR qui est stocké par une instance de la <xref:System.Windows.RoutedEvent> classe et inscrit auprès du [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] système d’événements. L' <xref:System.Windows.RoutedEvent> instance obtenue à partir de l’inscription est généralement `public` conservée `static` `readonly` en tant que membre de champ de la classe qui inscrit et, par conséquent, «possède» l’événement routé. La connexion à l’événement CLR portant un nom identique (qui est parfois appelé événement «Wrapper») s’effectue en substituant les `add` implémentations et `remove` pour l’événement CLR. En règle générale, `add` et `remove` sont conservés comme des valeurs implicites par défaut qui utilisent la syntaxe d’événement spécifique au langage pour ajouter et supprimer des gestionnaires de cet événement. Le mécanisme de connexion et de stockage des événements routés est conceptuellement similaire à la façon dont une propriété de dépendance est une propriété CLR qui <xref:System.Windows.DependencyProperty> est stockée par la [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] classe et inscrite auprès du système de propriétés.

L’exemple suivant illustre la déclaration d’un événement `Tap` routé personnalisé, y compris l’inscription et l’exposition <xref:System.Windows.RoutedEvent> du champ d' `add` identificateur et des implémentations et `remove` pour l' `Tap` événement CLR.

[!code-csharp[RoutedEventCustom#AddRemoveHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventCustom/CSharp/SDKSampleLibrary/class1.cs#addremovehandler)]
[!code-vb[RoutedEventCustom#AddRemoveHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventCustom/VB/SDKSampleLibrary/Class1.vb#addremovehandler)]

### <a name="routed-event-handlers-and-xaml"></a>Gestionnaires d’événements routés et XAML

Pour ajouter un gestionnaire à un événement à l’aide de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], déclarez le nom de l’événement en tant qu’attribut sur l’élément qui joue le rôle d’écouteur d’événements. La valeur de l’attribut est le nom de votre méthode de gestionnaire implémentée, qui doit se trouver dans la classe partielle du fichier code-behind.

[!code-xaml[EventOvwSupport#SimplestSyntax](~/samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml#simplestsyntax)]

La [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] syntaxe pour l’ajout de gestionnaires d’événements CLR standard est la même pour l’ajout de gestionnaires d’événements routés, car vous ajoutez véritablement des gestionnaires au wrapper d’événement CLR, qui a une implémentation d’événement routé sous-jacente. Pour plus d’informations sur l’ajout de gestionnaires d’événements dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], consultez [Vue d’ensemble du langage XAML (WPF)](xaml-overview-wpf.md).

<a name="routing_strategies"></a>

## <a name="routing-strategies"></a>Stratégies de routage

Les événements routés utilisent l’une des trois stratégies de routage suivantes :

- **Propagation** Les gestionnaires d’événements sur la source d’événements sont appelés. L’événement routé est acheminé ensuite vers des éléments parents successifs jusqu’à atteindre la racine de l’arborescence d’éléments. La plupart des événements routés utilisent la stratégie de routage par propagation. Les événements routés par propagation sont généralement utilisés pour signaler des entrées ou des changements d’état à partir de contrôles distincts ou d’autres éléments d’interface utilisateur.

- **Directe** Seul l’élément source lui-même a la possibilité d’appeler des gestionnaires en réponse. Cela s’apparente au « routage » que [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] utilise pour les événements. Toutefois, contrairement à un événement CLR standard, les événements routés directs prennent en charge la gestion de classe (la gestion de classe est expliquée dans <xref:System.Windows.EventSetter> une <xref:System.Windows.EventTrigger>section à venir) et peut être utilisée par et.

- **Tunneling** Initialement, les gestionnaires d’événements au niveau de la racine de l’arborescence d’éléments sont appelés. L’événement routé passe ensuite par des éléments enfants successifs pour aller vers l’élément de nœud correspondant à la source de l’événement routé (l’élément qui a déclenché l’événement routé). Les événements routés de tunneling sont souvent utilisés ou gérés dans le cadre de la composition d’un contrôle, de telle manière que les événements issus de parties composites peuvent être délibérément supprimés ou remplacés par des événements spécifiques au contrôle complet. Les événements d’entrée fournis dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sont souvent implémentés comme une paire tunneling/propagation. Les événements de tunneling sont parfois appelés événements Preview en raison d’une convention de nommage utilisée pour les paires.

<a name="why_use"></a>

## <a name="why-use-routed-events"></a>Pourquoi utiliser des événements routés ?

En tant que développeur d’applications, il n’est pas toujours nécessaire de savoir que l’événement que vous gérez est implémenté comme un événement routé. Les événements routés présentent un comportement particulier, mais ce comportement est en grande partie invisible si vous gérez l’événement sur l’élément à partir duquel il a été déclenché.

Les événements routés deviennent puissants lorsqu’ils sont utilisés dans l’un des scénarios suivants : définition de gestionnaires communs au niveau d’une racine commune, composition de votre propre contrôle ou définition de votre propre classe de contrôle personnalisé.

Les écouteurs et les sources d’événements routés n’ont pas besoin de partager un événement commun dans leur hiérarchie. Tout <xref:System.Windows.UIElement> ou<xref:System.Windows.ContentElement> peut être un écouteur d’événements pour n’importe quel événement routé. Par conséquent, vous pouvez utiliser l’ensemble des événements routés disponibles sur l’ensemble de l’API de travail comme une «interface» conceptuelle qui permet aux éléments disparates de l’application d’échanger des informations sur les événements. Ce concept d’« interface » pour les événements routés s’applique plus particulièrement aux événements d’entrée.

Les événements routés peuvent également servir à communiquer au sein de l’arborescence d’éléments, car les données de l’événement sont propagées vers chaque élément rencontré sur l’itinéraire. Si un élément change les données d’événement, ce changement est disponible pour l’élément suivant dans l’itinéraire.

Outre l’aspect de routage, il existe deux autres raisons pour lesquelles un [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] événement donné peut être implémenté comme un événement routé au lieu d’un événement CLR standard. Si vous implémentez vos propres événements, vous pouvez également prendre en compte ces principes :

- Certaines [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fonctionnalités de création de styles et de <xref:System.Windows.EventSetter> modèles <xref:System.Windows.EventTrigger> , telles que et, exigent que l’événement référencé soit un événement routé. Il s’agit du scénario d’identificateur d’événement mentionné précédemment.

- Les événements routés prennent en charge un mécanisme de gestion de classe par lequel la classe peut spécifier des méthodes statiques qui ont l’opportunité de gérer des événements routés avant que les gestionnaires d’instance inscrits puissent y accéder. Ceci est très utile pour la conception de contrôles, car la classe peut appliquer des comportements de classe pilotés par les événements qui ne peuvent pas être supprimés par inadvertance lorsque vous gérez un événement sur une instance.

Toutes les considérations ci-dessus sont abordées dans une autre section de cette rubrique.

<a name="event_handing"></a>

## <a name="adding-and-implementing-an-event-handler-for-a-routed-event"></a>Ajout et implémentation d’un gestionnaire d’événements pour un événement routé

Pour ajouter un gestionnaire d’événements dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], ajoutez le nom de l’événement à un élément en tant qu’attribut, et définissez la valeur de l’attribut sur le nom du gestionnaire d’événements qui implémente un délégué, comme dans l’exemple suivant.

[!code-xaml[EventOvwSupport#SimplestSyntax](~/samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml#simplestsyntax)]

`b1SetColor`nom du gestionnaire implémenté qui contient le code qui gère l' <xref:System.Windows.Controls.Primitives.ButtonBase.Click> événement. `b1SetColor`doit avoir la même signature que le <xref:System.Windows.RoutedEventHandler> délégué, qui est le délégué de gestionnaire d’événements <xref:System.Windows.Controls.Primitives.ButtonBase.Click> pour l’événement. Le premier paramètre de tous les délégués de gestionnaires d’événements routés spécifie l’élément auquel le gestionnaire d’événements est ajouté, et le deuxième paramètre spécifie les données de l’événement.

[!code-csharp[EventOvwSupport#SimpleHandlerA](~/samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml.cs#simplehandlera)]
[!code-vb[EventOvwSupport#SimpleHandlerA](~/samples/snippets/visualbasic/VS_Snippets_Wpf/EventOvwSupport/visualbasic/default.xaml.vb#simplehandlera)]

<xref:System.Windows.RoutedEventHandler>est le délégué de gestionnaire d’événements routés de base. Pour les événements routés qui conviennent spécialement à certains contrôles ou scénarios, les délégués à utiliser avec les gestionnaires d’événements routés peuvent également devenir plus spécialisés, de manière à pouvoir transmettre des données d’événement spécialisées. Par exemple, dans un scénario d’entrée courant, vous pouvez gérer <xref:System.Windows.UIElement.DragEnter> un événement routé. Votre gestionnaire doit implémenter <xref:System.Windows.DragEventHandler> le délégué. En utilisant le délégué le plus spécifique, vous pouvez traiter <xref:System.Windows.DragEventArgs> le dans le gestionnaire et lire <xref:System.Windows.DragEventArgs.Data%2A> la propriété, qui contient la charge utile du presse-papiers de l’opération glisser.

Pour un exemple complet montrant comment ajouter un gestionnaire d’événements à un élément à l’aide de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], consultez [Gérer un événement routé](how-to-handle-a-routed-event.md).

L’ajout d’un gestionnaire pour un événement routé dans une application créée dans du code est une opération simple. Les gestionnaires d’événements routés peuvent toujours être ajoutés par le biais d' <xref:System.Windows.UIElement.AddHandler%2A> une méthode d’assistance (qui est la même méthode que celle qui `add`est appelée par le stockage existant). Toutefois, les événements routés [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] existants disposent généralement d’implémentations de stockage de logique `add` et `remove` qui permettent aux gestionnaires d’événements routés d’être ajoutés à une syntaxe d’événement spécifique au langage, qui est une syntaxe plus intuitive que celle de la méthode d’assistance. Voici un exemple d’utilisation de la méthode d’assistance :

[!code-csharp[EventOvwSupport#AddHandlerCode](~/samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml.cs#addhandlercode)]
[!code-vb[EventOvwSupport#AddHandlerCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/EventOvwSupport/visualbasic/default.xaml.vb#addhandlercode)]

L’exemple suivant illustre la C# syntaxe de l’opérateur (Visual Basic a une syntaxe d’opérateur légèrement différente en raison de la gestion du déréférencement):

[!code-csharp[EventOvwSupport#AddHandlerPlusEquals](~/samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml.cs#addhandlerplusequals)]
[!code-vb[EventOvwSupport#AddHandlerPlusEquals](~/samples/snippets/visualbasic/VS_Snippets_Wpf/EventOvwSupport/visualbasic/default.xaml.vb#addhandlerplusequals)]

Pour obtenir un exemple montrant comment ajouter un gestionnaire d’événements dans le code, consultez [Ajouter un gestionnaire d’événements à l’aide de code](how-to-add-an-event-handler-using-code.md).

Si vous utilisez Visual Basic, vous pouvez également utiliser le `Handles` mot clé pour ajouter des gestionnaires dans le cadre des déclarations de gestionnaire. Pour plus d’informations, consultez [Gestion des événements Visual Basic et WPF](visual-basic-and-wpf-event-handling.md).

<a name="concept_handled"></a>

### <a name="the-concept-of-handled"></a>Concept du Handled

Tous les événements routés partagent une classe de base de données <xref:System.Windows.RoutedEventArgs>d’événements commune,. <xref:System.Windows.RoutedEventArgs>définit la <xref:System.Windows.RoutedEventArgs.Handled%2A> propriété, qui prend une valeur booléenne. L’objectif de la <xref:System.Windows.RoutedEventArgs.Handled%2A> propriété est de permettre à n’importe quel gestionnaire d’événements sur l’itinéraire de marquer l’événement routé comme *géré*, en <xref:System.Windows.RoutedEventArgs.Handled%2A> affectant `true`à la valeur. Après avoir été traitées par le gestionnaire au niveau d’un élément de l’itinéraire, les données d’événement partagées sont à nouveau signalées à chaque écouteur se trouvant sur l’itinéraire.

La valeur de <xref:System.Windows.RoutedEventArgs.Handled%2A> affecte la façon dont un événement routé est signalé ou traité à mesure qu’il traverse l’itinéraire. Si <xref:System.Windows.RoutedEventArgs.Handled%2A> se `true` trouve dans les données d’événement pour un événement routé, les gestionnaires qui écoutent cet événement routé sur d’autres éléments ne sont généralement plus appelés pour cette instance d’événement particulière. Ceci est vrai à la fois pour les gestionnaires attachés dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] et pour ceux ajoutés par des syntaxes d’attachement de gestionnaire d’événements spécifiques au langage, comme `+=` ou `Handles`. Pour les scénarios de gestionnaires les plus courants, le fait de marquer <xref:System.Windows.RoutedEventArgs.Handled%2A> un `true` événement comme géré en affectant à la valeur «arrêter» le routage pour un itinéraire de tunneling ou un itinéraire de propagation, ainsi que pour tout événement géré à un point de l’itinéraire par un gestionnaire de classe.

Toutefois, il existe un mécanisme «handledEventsToo» dans lequel les écouteurs peuvent toujours exécuter des gestionnaires en réponse à des événements routés `true` où <xref:System.Windows.RoutedEventArgs.Handled%2A> se trouve dans les données d’événement. En d’autres termes, l’itinéraire d’événement n’est pas réellement arrêté quand les données d’événement sont marquées comme gérées. Vous pouvez uniquement utiliser le mécanisme handledEventsToo dans le code ou dans un <xref:System.Windows.EventSetter>:

- Dans le code, au lieu d’utiliser une syntaxe d’événement spécifique au langage qui fonctionne pour les événements généraux [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] du <xref:System.Windows.UIElement.AddHandler%28System.Windows.RoutedEvent%2CSystem.Delegate%2CSystem.Boolean%29> CLR, appelez la méthode pour ajouter votre gestionnaire. Définissez la valeur de `handledEventsToo` sur `true`.

- Dans un <xref:System.Windows.EventSetter>, affectez <xref:System.Windows.EventSetter.HandledEventsToo%2A> à `true`l’attribut la valeur.

En plus du comportement que <xref:System.Windows.RoutedEventArgs.Handled%2A> l’État produit dans les événements routés, le concept de a des <xref:System.Windows.RoutedEventArgs.Handled%2A> implications quant à la façon dont vous devez concevoir votre application et écrire le code du gestionnaire d’événements. Vous pouvez conceptualiser <xref:System.Windows.RoutedEventArgs.Handled%2A> comme un protocole simple exposé par les événements routés. La façon dont vous utilisez ce protocole dépend de vous, mais la conception conceptuelle de la façon dont la <xref:System.Windows.RoutedEventArgs.Handled%2A> valeur de est destinée à être utilisée est la suivante:

- Si un événement routé est marqué comme géré, il n’a pas besoin d’être géré de nouveau par d’autres éléments sur l’itinéraire.

- Si un événement routé n’est pas marqué comme géré, alors les autres écouteurs qui étaient antérieurs le long de l’itinéraire ont choisi de ne pas inscrire de gestionnaire, ou les gestionnaires qui ont été inscrits choisissent de ne pas manipuler les <xref:System.Windows.RoutedEventArgs.Handled%2A> données `true`d’événement et de définir sur. Il est également possible que l’écouteur actuel soit le premier de l’itinéraire. Les gestionnaires de l’écouteur actuel ont maintenant trois possibilités :

  - Ne rien faire. L’événement reste non géré et l’événement est dirigé vers l’écouteur suivant.

  - Exécuter du code en réponse à l’événement, mais décider que l’action entreprise n’était pas suffisamment importante pour garantir le marquage de l’événement comme géré. L’événement est dirigé vers l’écouteur suivant.

  - Exécuter du code en réponse à l’événement. Marquer l’événement comme géré dans les données d’événement passées au gestionnaire, car l’action entreprise est jugée suffisamment importante pour garantir le marquage de l’événement comme géré. L’événement est encore routé vers l’écouteur suivant, mais <xref:System.Windows.RoutedEventArgs.Handled%2A> avec = `true` dans ses données d’événement, `handledEventsToo` seuls les écouteurs ont la possibilité d’appeler d’autres gestionnaires.

Cette conception conceptuelle est renforcée par le comportement de routage mentionné précédemment: il est plus difficile (bien que possible dans le code ou les styles) d’attacher des gestionnaires pour les événements routés qui sont appelés même si un gestionnaire précédent le long de l’itinéraire a déjà été défini <xref:System.Windows.RoutedEventArgs.Handled%2A> à`true`.

Pour plus d’informations <xref:System.Windows.RoutedEventArgs.Handled%2A>sur la gestion des classes des événements routés et des recommandations sur le moment où il convient de marquer un événement <xref:System.Windows.RoutedEventArgs.Handled%2A>routé comme, consultez [marquage des événements routés comme gérés et gestion de classe](marking-routed-events-as-handled-and-class-handling.md).

Dans les applications, il est assez courant de gérer un événement routé par propagation sur l’objet qui l’a déclenché, sans se soucier des caractéristiques de routage de l’événement. Toutefois, il est recommandé de toujours marquer l’événement routé comme géré (handled) dans les données d’événement, afin d’éviter des effets secondaires si un élément situé plus haut dans l’arborescence d’éléments comportait également un gestionnaire attaché pour le même événement routé.

<a name="class_handlers"></a>

## <a name="class-handlers"></a>Gestionnaires de classe

Si vous définissez une classe qui dérive d’une certaine manière de <xref:System.Windows.DependencyObject>, vous pouvez également définir et attacher un gestionnaire de classe pour un événement routé qui est un membre d’événement déclaré ou hérité de votre classe. Les gestionnaires de classe sont appelés avant les gestionnaires d’écouteur d’instance qui sont attachés à une instance de cette classe, chaque fois qu’un événement routé atteint une instance d’élément sur son itinéraire.

Certains contrôles [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] disposent d’une gestion de classe inhérente pour certains événements routés. Ceci peut donner l’apparence que l’événement routé n’a même pas été déclenché, alors qu’en réalité il est géré par la classe, et peut encore potentiellement être géré par vos gestionnaires d’instance si vous utilisez certaines techniques. En outre, plusieurs classes et contrôles de base exposent des méthodes virtuelles qui peuvent être utilisées pour substituer le comportement de gestion de classe. Pour plus d’informations sur la façon de contourner la gestion de classe et sur la définition de votre propre gestion de classe dans une classe personnalisée, consultez [Marquage des événements routés comme gérés et gestion de classe](marking-routed-events-as-handled-and-class-handling.md).

<a name="attached_events"></a>

## <a name="attached-events-in-wpf"></a>Événements attachés dans WPF

Le langage [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] définit également un type particulier d’événement appelé *événement attaché*. Un événement attaché permet d’ajouter le gestionnaire d’un événement particulier à un élément arbitraire. L’élément qui gère l’événement n’a pas besoin de définir ou d’hériter de l’événement attaché. En outre, ni l’objet qui déclenche potentiellement l’événement, ni l’instance de gestion de destination ne doivent définir ou « posséder » cet événement comme un membre de classe.

Le système d’entrée [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] utilise largement les événements attachés. Cependant, presque tous ces événements attachés sont transférés via des éléments de base. Les événements d’entrée apparaissent alors comme des événements routés non attachés équivalents qui sont membres de la classe d’élément de base. Par exemple <xref:System.Windows.Input.Mouse.MouseDown?displayProperty=nameWithType> , l’événement attaché sous-jacent peut être géré plus facilement sur tout donné <xref:System.Windows.UIElement.MouseDown> <xref:System.Windows.UIElement> en utilisant <xref:System.Windows.UIElement> sur, plutôt que de gérer la syntaxe de l' [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] événement attaché dans ou dans le code.

Pour plus d’informations sur les événements attachés dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], consultez [Vue d’ensemble des événements attachés](attached-events-overview.md).

<a name="Qualifying_Event_Names_in_XAML_for_Anticipated_Routing"></a>

## <a name="qualified-event-names-in-xaml"></a>Noms qualifiés d’événements en XAML

Une autre utilisation de la syntaxe qui ressemble à la syntaxe d’événement attaché *typename*.*eventname*, mais qui n’est pas à proprement parler une utilisation d’événement attaché est lorsque vous attachez des gestionnaires pour les événements routés qui sont déclenchés par des éléments enfants. Vous attachez les gestionnaires à un parent commun pour tirer parti du routage d’événements, même si le parent commun ne dispose pas de l’événement routé nécessaire comme membre. Regardons de nouveau cet exemple :

[!code-xaml[EventOvwSupport#GroupButton](~/samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml#groupbutton)]

Ici, l’écouteur d’élément parent où le gestionnaire est ajouté est <xref:System.Windows.Controls.StackPanel>un. Toutefois, il ajoute un gestionnaire pour un événement routé qui a été déclaré et sera déclenché par la classe ( <xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.Primitives.ButtonBase> en fait, mais disponible pour par <xref:System.Windows.Controls.Button> le biais de l’héritage). <xref:System.Windows.Controls.Button>l’événement «est propriétaire», mais le système d’événement routé autorise les gestionnaires pour tout événement routé à être attaché à n' <xref:System.Windows.UIElement> importe <xref:System.Windows.ContentElement> quel écouteur d’instance ou qui pourrait attacher des écouteurs pour un événement Common Language Runtime (CLR). L’espace de noms xmlns par défaut pour ces noms d’attributs d’événement qualifiés est généralement l’espace de noms xmlns [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] par défaut. Cependant, vous pouvez spécifier des espaces de noms avec préfixe pour les événements routés personnalisés. Pour plus d’informations sur xmlns, consultez [Espaces de noms XAML et mappage d’espace de noms pour XAML WPF](xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).

<a name="how_event_processing_works"></a>

## <a name="wpf-input-events"></a>Événements d’entrée WPF

Les événements routés sont fréquemment utilisés dans la plateforme [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pour les événements d’entrée. Par convention, dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], les noms d’événements routés par tunneling comprennent le préfixe « Preview ». Les événements d’entrée vont souvent par paires, l’un étant l’événement de propagation et l’autre, l’événement de tunneling. Par exemple, l' <xref:System.Windows.ContentElement.KeyDown> événement et l' <xref:System.Windows.ContentElement.PreviewKeyDown> événement ont la même signature, le premier étant l’événement d’entrée de propagation et le dernier étant l’événement d’entrée de tunneling. Parfois, les événements d’entrée ont uniquement une version par propagation, ou uniquement une version à routage direct. Dans la documentation, les rubriques relatives aux événements routés font référence à des événements routés similaires avec d’autres stratégies de routage, et les sections des pages concernant les références managées expliquent plus en détail la stratégie de routage de chaque événement routé.

Les événements d’entrée [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fournis par paires sont implémentés de telle sorte qu’une seule opération d’entrée, comme un clic de souris, déclenche les deux événements de la paire l’un après l’autre. Tout d’abord, l’événement de tunneling est déclenché et suit son itinéraire. Ensuite, l’événement de propagation est déclenché et suit son itinéraire. Les deux événements partagent littéralement la même instance de données d’événement, <xref:System.Windows.UIElement.RaiseEvent%2A> car l’appel de méthode dans la classe d’implémentation qui déclenche l’événement de propagation écoute les données d’événement à partir de l’événement de tunneling et les réutilise dans le nouvel événement déclenché. Les écouteurs qui comportent des gestionnaires pour l’événement de tunneling sont les premiers à pouvoir marquer l’événement routé comme géré (d’abord les gestionnaires de classe, ensuite les gestionnaires d’instance). Si un élément a marqué l’événement routé comme géré sur l’itinéraire de tunneling, les données d’événement déjà gérées sont envoyées à l’événement de propagation, et les gestionnaires standard attachés pour les événements d’entrée de propagation équivalents ne sont pas appelés. Vu de l’extérieur, il peut sembler que l’événement de propagation géré n’a pas encore été déclenché. Ce comportement de gestion est utile pour la composition de contrôles, où vous pouvez souhaiter que tous les événements d’entrée basés sur les tests d’atteinte ou le focus soient signalés par votre dernier contrôle, plutôt que par ses parties composites. Le dernier élément de contrôle est plus proche de la racine dans la composition et peut donc être le premier à gérer la classe de l’événement de tunneling et éventuellement à « remplacer » l’événement routé par un événement plus spécifique au contrôle dans le code qui stocke la classe de contrôle.

En guise d’illustration du traitement des événements d’entrée, prenez l’exemple d’événement d’entrée suivant. Dans l’illustration suivante, `leaf element #2` est la source d’un `PreviewMouseDown` événement, puis d’un `MouseDown` événement:

![Diagramme de routage d'événements](./media/routed-events-overview/input-event-routing.png)

L’ordre de traitement des événements est le suivant :

1. `PreviewMouseDown` (tunneling) sur l’élément racine.

2. `PreviewMouseDown` (tunneling) sur l’élément intermédiaire numéro 1.

3. `PreviewMouseDown` (tunneling) sur l’élément source numéro 2.

4. `MouseDown` (propagation) sur l’élément source numéro 2.

5. `MouseDown` (propagation) sur l’élément intermédiaire numéro 1.

6. `MouseDown` (propagation) sur l’élément racine.

Un délégué de gestionnaire d’événements routés fournit des références à deux objets : l’objet qui a déclenché l’événement et l’objet à partir duquel le gestionnaire a été appelé. L’objet à partir duquel le gestionnaire a été appelé est celui signalé par le paramètre `sender`. L’objet dans lequel l’événement a été déclenché pour la première <xref:System.Windows.RoutedEventArgs.Source%2A> fois est signalé par la propriété dans les données d’événement. Un événement routé peut toujours être déclenché et géré par le même objet, auquel cas `sender` et <xref:System.Windows.RoutedEventArgs.Source%2A> sont identiques (c’est le cas avec les étapes 3 et 4 dans la liste d’exemples de traitement des événements).

En raison du tunneling et de la propagation, les éléments parents reçoivent des <xref:System.Windows.RoutedEventArgs.Source%2A> événements d’entrée où est l’un de leurs éléments enfants. Lorsqu’il est important de connaître l’élément source, vous pouvez identifier l’élément source en accédant à la <xref:System.Windows.RoutedEventArgs.Source%2A> propriété.

En général, une fois que l’événement <xref:System.Windows.RoutedEventArgs.Handled%2A>d’entrée est marqué, les gestionnaires supplémentaires ne sont pas appelés. En outre, vous devez marquer les événements d’entrée comme gérés dès qu’un gestionnaire est appelé pour traiter votre gestion logique (et spécifique à l’application) de la signification de l’événement d’entrée.

L’exception à cette déclaration générale sur <xref:System.Windows.RoutedEventArgs.Handled%2A> l’État est que les gestionnaires d’événements d’entrée inscrits pour ignorer <xref:System.Windows.RoutedEventArgs.Handled%2A> délibérément l’état des données d’événement seraient toujours appelés le long de l’itinéraire. Pour plus d’informations, consultez [Événements Preview](preview-events.md) ou [Marquage des événements routés comme gérés et gestion de classe](marking-routed-events-as-handled-and-class-handling.md).

Le modèle de données d’événement partagé entre les événements de tunneling et de propagation, avec le déclenchement séquentiel de l’événement de tunneling puis de l’événement de propagation, est un concept qui n’est pas valable pour tous les événements routés. Ce comportement est implémenté selon la manière dont les périphériques d’entrée [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] choisissent de déclencher et de connecter les paires d’événements d’entrée. L’implémentation de vos propres événements d’entrée est un scénario avancé. Toutefois, vous pouvez choisir de suivre ce modèle pour vos propres événements d’entrée.

Certaines classes choisissent de gérer la classe de certains événements d’entrée, généralement dans le but de redéfinir la signification d’un événement d’entrée piloté par l’utilisateur dans le contrôle, et dans le but de déclencher un nouvel événement. Pour plus d’informations, consultez [Marquage des événements routés comme gérés et gestion de classe](marking-routed-events-as-handled-and-class-handling.md).

Pour plus d’informations sur les entrées et la façon dont elles interagissent avec les événements dans des scénarios d’application standard, consultez [Vue d’ensemble des entrées](input-overview.md).

<a name="events_styles"></a>

## <a name="eventsetters-and-eventtriggers"></a>EventSetters et EventTriggers

Dans les styles, vous pouvez inclure une syntaxe de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] gestion des événements pré-déclarés dans le <xref:System.Windows.EventSetter>balisage à l’aide d’un. Lorsque le style est appliqué, le gestionnaire référencé est ajouté à l’instance à laquelle est appliqué le style. Vous pouvez déclarer un <xref:System.Windows.EventSetter> uniquement pour un événement routé. Voici un exemple. Notez que la méthode `b1SetColor` référencée ici se trouve dans un fichier code-behind.

[!code-xaml[EventOvwSupport#XAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/page2.xaml#xaml2)]

L’avantage acquis ici est que le style est susceptible de contenir une grande quantité d’autres informations qui peuvent s’appliquer à n’importe quel bouton de votre application et <xref:System.Windows.EventSetter> que le fait de faire partie de ce style favorise la réutilisation du code, même au niveau du balisage. En outre, <xref:System.Windows.EventSetter> les noms de méthode abstraits pour les gestionnaires sont encore plus éloignés de l’application générale et du balisage de page.

Une autre syntaxe spécialisée qui combine l’événement routé et les fonctionnalités d' [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] animation de <xref:System.Windows.EventTrigger>est un. Comme avec <xref:System.Windows.EventSetter>, seuls les événements routés peuvent être utilisés pour <xref:System.Windows.EventTrigger>un. En général, <xref:System.Windows.EventTrigger> un est déclaré dans le cadre d’un style, <xref:System.Windows.EventTrigger> mais un peut également être déclaré sur des éléments au niveau de la <xref:System.Windows.FrameworkElement.Triggers%2A> page dans le cadre de <xref:System.Windows.Controls.ControlTemplate>la collection ou dans un. Vous permet de spécifier un <xref:System.Windows.Media.Animation.Storyboard> qui s’exécute chaque fois qu’un événement routé atteint un élément de son itinéraire qui déclare un <xref:System.Windows.EventTrigger> pour cet événement. <xref:System.Windows.EventTrigger> L’avantage d’un <xref:System.Windows.EventTrigger> surplus à gérer l’événement et le fait de démarrer une table de montage séquentiel <xref:System.Windows.EventTrigger> existante est qu’un offre un meilleur contrôle sur la table de montage séquentiel et son comportement au moment de l’exécution. Pour plus d’informations, consultez [Utiliser des déclencheurs d’événements pour contrôler un storyboard après son démarrage](../graphics-multimedia/how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md).

<a name="more_about"></a>

## <a name="more-about-routed-events"></a>Informations complémentaires sur les événements routés

Cette rubrique traite principalement des concepts de base relatifs aux événements routés, et explique comment et à quel moment répondre aux événements routés qui sont déjà présents dans les différents éléments et contrôles de base. Toutefois, vous pouvez créer vos propres événements routés dans votre classe personnalisée, ainsi que toute la prise en charge nécessaire, telle que les classes et les délégués spécialisés de données d’événement. Le propriétaire de l’événement routé peut être n’importe quelle classe, mais les événements routés doivent être déclenchés <xref:System.Windows.ContentElement> par et gérés par ou par <xref:System.Windows.UIElement> les classes dérivées afin d’être utiles. Pour plus d’informations sur les événements personnalisés, consultez [Créer un événement routé personnalisé](how-to-create-a-custom-routed-event.md).

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
