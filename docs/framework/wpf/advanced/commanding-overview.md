---
title: Vue d'ensemble des commandes
description: En savoir plus sur les commandes, un mécanisme d’entrée dans Windows Presentation Foundation qui fournit la gestion des entrées à un niveau plus sémantique que l’entrée d’appareil.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- interfaces [WPF], ICommandSource
- command library [WPF]
- commands [WPF], definition of
- CommandBindings [WPF]
- ICommandSource interfaces [WPF]
- commanding [WPF]
- CommandManager [WPF]
ms.assetid: bc208dfe-367d-426a-99de-52b7e7511e81
ms.openlocfilehash: 4f7d12fbf0de9b1546f15061ab7eb1318378bbbb
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168119"
---
# <a name="commanding-overview"></a>Vue d'ensemble des commandes
<a name="introduction"></a> L’exécution de commandes est un mécanisme d’entrée dans [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] qui fournit la gestion des entrées à un niveau plus sémantique que l’entrée de périphérique. Les opérations **Copier**, **Couper** et **Coller** sont des exemples de commandes figurant dans de nombreuses applications.  
  
 Cette vue d’ensemble explique ce qu’est une commande dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], quelles classes font partie du modèle d’exécution de commandes, et comment utiliser et créer des commandes dans vos applications.  
  
 Cette rubrique contient les sections suivantes :  
  
- [Qu’est-ce qu’une commande ?](#commands_at_10000_feet)  
  
- [Exemple de commande simple dans WPF](#simple_command)  
  
- [Quatre principaux concepts de l’exécution de commandes WPF](#Four_main_Concepts)  
  
- [Bibliothèque de commandes](#Command_Library)  
  
- [Création de commandes personnalisées](#creating_commands)  
  
<a name="commands_at_10000_feet"></a>
## <a name="what-are-commands"></a>Qu’est-ce qu’une commande ?  
 Les commandes ont plusieurs fonctions. La première est de séparer la sémantique et l’objet qui appelle une commande de la logique qui exécute la commande. Cela permet à des sources diverses d’appeler la même logique de commande, et permet de personnaliser celle-ci pour différentes cibles. Par exemple, les opérations d’édition **Copier**, **Couper** et **Coller**, qui figurent dans de nombreuses applications, peuvent être appelées à l’aide de différentes actions utilisateur si elles sont implémentées à l’aide de commandes. Une application peut permettre à un utilisateur de couper du texte ou des objets sélectionnés en cliquant sur un bouton, en choisissant un élément dans un menu ou en utilisant une combinaison de touches telle que Ctrl+X. Grâce aux commandes, vous pouvez lier chaque type d’action de l’utilisateur à la même logique.  
  
 Une autre fonction des commandes consiste à indiquer si une action est disponible. Si vous coupez un objet ou du texte, l’action n’a de sens que si quelque chose est sélectionné. Si un utilisateur essaie de couper un objet ou du texte sans rien avoir sélectionné, rien ne se passe. Pour indiquer cela à l’utilisateur, de nombreuses applications désactivent les boutons et les éléments de menu afin que l’utilisateur sache s’il est possible ou non d’exécuter une action. Une commande peut indiquer si une action est possible en implémentant la méthode <xref:System.Windows.Input.ICommand.CanExecute%2A>. Un bouton peut s’abonner à l’événement <xref:System.Windows.Input.ICommand.CanExecuteChanged> et être désactivé si <xref:System.Windows.Input.ICommand.CanExecute%2A> retourne `false`, ou être activé si <xref:System.Windows.Input.ICommand.CanExecute%2A> retourne `true`.  
  
 La sémantique d’une commande peut être cohérente parmi plusieurs applications et classes, mais la logique de l’action est propre à l’objet sur lequel elle est exécutée. La combinaison de touches Ctrl+X appelle la commande **Couper** dans les classes de texte, les classes d’image et les navigateurs web, mais la logique qui effectue réellement l’opération **Couper** est définie par l’application qui exécute cette opération. Un <xref:System.Windows.Input.RoutedCommand> permet aux clients d’implémenter la logique. Un objet texte peut couper le texte sélectionné dans le Presse-papiers, tandis qu’un objet image peut couper l’image sélectionnée. Quand une application gère l’événement <xref:System.Windows.Input.CommandManager.Executed>, elle a accès à la cible de la commande et peut entreprendre l’action appropriée en fonction du type de cible.  
  
<a name="simple_command"></a>
## <a name="simple-command-example-in-wpf"></a>Exemple de commande simple dans WPF  
 La façon la plus simple d’utiliser une commande dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] consiste à utiliser un <xref:System.Windows.Input.RoutedCommand> prédéfini à partir de l’une des classes de bibliothèque de commandes, à utiliser un contrôle qui offre une prise en charge native du traitement de la commande, et à utiliser un contrôle qui offre une prise en charge native de l’appel d’une commande.  La commande <xref:System.Windows.Input.ApplicationCommands.Paste%2A> est l’une des commandes prédéfinies de la classe <xref:System.Windows.Input.ApplicationCommands>.  Le contrôle <xref:System.Windows.Controls.TextBox> a une logique intégrée pour la gestion de la commande <xref:System.Windows.Input.ApplicationCommands.Paste%2A>.  Et la classe <xref:System.Windows.Controls.MenuItem> a une prise en charge native de l’appel des commandes.  
  
 L’exemple suivant montre comment configurer <xref:System.Windows.Controls.MenuItem> pour effectuer une action spécifique quand un utilisateur clique dessus, à savoir appeler la commande <xref:System.Windows.Input.ApplicationCommands.Paste%2A> sur <xref:System.Windows.Controls.TextBox>, en supposant que <xref:System.Windows.Controls.TextBox> ait le focus clavier.  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewSimpleCommand](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewsimplecommand)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcommandtargetcodebehind)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcommandtargetcodebehind)]  
  
<a name="Four_main_Concepts"></a>
## <a name="four-main-concepts-in-wpf-commanding"></a>Quatre principaux concepts de l’exécution de commandes WPF  
 Le modèle de commande routée dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] peut être divisé en quatre concepts principaux : la commande, la source de commande, la cible de commande et la liaison de commande.  
  
- La *commande* est l’action à exécuter.  
  
- La *source de la commande* est l’objet qui appelle la commande.  
  
- La *cible de la commande* est l’objet sur lequel la commande est exécutée.  
  
- La *liaison de commande* est l’objet qui mappe la logique de commande à la commande.  
  
 Dans l’exemple précédent, la commande <xref:System.Windows.Input.ApplicationCommands.Paste%2A> est la commande, <xref:System.Windows.Controls.MenuItem> est la source de commande, <xref:System.Windows.Controls.TextBox> est la cible de commande, et la liaison de commande est fournie par le contrôle <xref:System.Windows.Controls.TextBox>.  Il est important de noter que <xref:System.Windows.Input.CommandBinding> n’est pas toujours fourni par le contrôle qui représente la classe de la cible de commande.  Bien souvent, <xref:System.Windows.Input.CommandBinding> doit être créé par le développeur d’applications, ou <xref:System.Windows.Input.CommandBinding> peut être associé à un ancêtre de la cible de commande.  
  
<a name="Commands"></a>
### <a name="commands"></a>Commandes  
 Les commandes dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sont créées via l’implémentation de l’interface <xref:System.Windows.Input.ICommand>.  <xref:System.Windows.Input.ICommand> expose deux méthodes, <xref:System.Windows.Input.ICommand.Execute%2A> et <xref:System.Windows.Input.ICommand.CanExecute%2A>, ainsi qu’un événement, <xref:System.Windows.Input.ICommand.CanExecuteChanged>. <xref:System.Windows.Input.ICommand.Execute%2A> effectue les actions associées à la commande. <xref:System.Windows.Input.ICommand.CanExecute%2A> détermine si la commande peut s’exécuter sur la cible de commande actuelle. <xref:System.Windows.Input.ICommand.CanExecuteChanged> se déclenche si le gestionnaire de commandes qui centralise les opérations d’exécution de commandes détecte un changement dans la source de commande susceptible d’invalider une commande déclenchée mais pas encore exécutée par la liaison de commande.  L’implémentation [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] de <xref:System.Windows.Input.ICommand> est la classe <xref:System.Windows.Input.RoutedCommand> et fait l’objet de cette vue d’ensemble.  
  
 Les principales sources d’entrée dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sont la souris, le clavier, l’encre et les commandes routées.  Les entrées qui sont plus orientées appareil utilisent <xref:System.Windows.RoutedEvent> pour notifier aux objets d’une page d’application qu’un événement d’entrée s’est produit.  <xref:System.Windows.Input.RoutedCommand> n’est pas différent.  Les méthodes <xref:System.Windows.Input.RoutedCommand.Execute%2A> et <xref:System.Windows.Input.RoutedCommand.CanExecute%2A> de <xref:System.Windows.Input.RoutedCommand> ne contiennent pas la logique d’application de la commande. En revanche, elles déclenchent des événements routés qui se propagent dans l’arborescence des éléments jusqu’à ce qu’ils rencontrent un objet ayant <xref:System.Windows.Input.CommandBinding>.  <xref:System.Windows.Input.CommandBinding> contient les gestionnaires de ces événements. Ce sont les gestionnaires qui exécutent la commande.  Pour plus d’informations sur le routage d’événements dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], consultez [Vue d’ensemble des événements routés](routed-events-overview.md).  
  
 La méthode <xref:System.Windows.Input.RoutedCommand.Execute%2A> sur <xref:System.Windows.Input.RoutedCommand> déclenche les événements <xref:System.Windows.Input.CommandManager.PreviewExecuted> et <xref:System.Windows.Input.CommandManager.Executed> sur la cible de commande.  La méthode <xref:System.Windows.Input.RoutedCommand.CanExecute%2A> sur <xref:System.Windows.Input.RoutedCommand> déclenche les événements <xref:System.Windows.Input.CommandManager.CanExecute> et <xref:System.Windows.Input.CommandManager.PreviewCanExecute> sur la cible de commande.  Ces événements se propagent dans l’arborescence d’éléments jusqu’à ce qu’ils rencontrent un objet ayant <xref:System.Windows.Input.CommandBinding> pour cette commande particulière.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fournit un ensemble de commandes routées courantes réparties sur plusieurs classes : <xref:System.Windows.Input.MediaCommands>, <xref:System.Windows.Input.ApplicationCommands>, <xref:System.Windows.Input.NavigationCommands>, <xref:System.Windows.Input.ComponentCommands> et <xref:System.Windows.Documents.EditingCommands>.  Ces classes contiennent uniquement les objets <xref:System.Windows.Input.RoutedCommand>, et non la logique d’implémentation de la commande.  La logique d’implémentation incombe à l’objet sur lequel la commande est exécutée.  
  
<a name="Command_Sources"></a>
### <a name="command-sources"></a>Sources de commande  
 Une source de commande est l’objet qui appelle la commande.  Voici des exemples de sources de commande : <xref:System.Windows.Controls.MenuItem>, <xref:System.Windows.Controls.Button> et <xref:System.Windows.Input.KeyGesture>.  
  
 Les sources de commande dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] implémentent généralement l’interface <xref:System.Windows.Input.ICommandSource>.  
  
 <xref:System.Windows.Input.ICommandSource> expose trois propriétés : <xref:System.Windows.Input.ICommandSource.Command%2A>, <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> et <xref:System.Windows.Input.ICommandSource.CommandParameter%2A> :  
  
- <xref:System.Windows.Input.ICommandSource.Command%2A> est la commande à exécuter quand la source de commande est appelée.  
  
- <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> est l’objet sur lequel exécuter la commande.  Il est important de noter que dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], la propriété <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> sur <xref:System.Windows.Input.ICommandSource> est applicable uniquement quand <xref:System.Windows.Input.ICommand> est un <xref:System.Windows.Input.RoutedCommand>.  Si <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> est défini sur <xref:System.Windows.Input.ICommandSource> et si la commande correspondante n’est pas <xref:System.Windows.Input.RoutedCommand>, la cible de commande est ignorée. Si <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> n’est pas défini, l’élément qui a le focus clavier est la cible de commande.  
  
- <xref:System.Windows.Input.ICommandSource.CommandParameter%2A> est un type de données défini par l’utilisateur, qui permet de passer des informations aux gestionnaires implémentant la commande.  
  
 Les classes [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] qui implémentent <xref:System.Windows.Input.ICommandSource> sont <xref:System.Windows.Controls.Primitives.ButtonBase>, <xref:System.Windows.Controls.MenuItem>, <xref:System.Windows.Documents.Hyperlink> et <xref:System.Windows.Input.InputBinding>.  <xref:System.Windows.Controls.Primitives.ButtonBase>, <xref:System.Windows.Controls.MenuItem> et <xref:System.Windows.Documents.Hyperlink> appellent une commande quand l’utilisateur clique sur ces derniers, et <xref:System.Windows.Input.InputBinding> appelle une commande quand le <xref:System.Windows.Input.InputGesture> associé est exécuté.  
  
 L’exemple suivant montre comment utiliser <xref:System.Windows.Controls.MenuItem> dans <xref:System.Windows.Controls.ContextMenu> en tant que source de commande pour la commande <xref:System.Windows.Input.ApplicationCommands.Properties%2A>.  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewCmdSourceXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewcmdsourcexaml)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCmdSource](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcmdsource)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCmdSource](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcmdsource)]  
  
 En règle générale, une source de commande écoute l’événement <xref:System.Windows.Input.RoutedCommand.CanExecuteChanged>.  Cet événement signale à la source de commande que la capacité de la commande à s’exécuter sur la cible de commande actuelle a peut-être changé.  La source de commande peut interroger l’état actuel de <xref:System.Windows.Input.RoutedCommand> à l’aide de la méthode <xref:System.Windows.Input.RoutedCommand.CanExecute%2A>.  La source de commande peut ensuite se désactiver si la commande ne peut pas s’exécuter.  C’est le cas, par exemple, de <xref:System.Windows.Controls.MenuItem> qui devient grisé quand une commande ne peut pas s’exécuter.  
  
 <xref:System.Windows.Input.InputGesture> peut être utilisé en tant que source de commande.  Il existe deux types de mouvement d’entrée dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] : <xref:System.Windows.Input.KeyGesture> et <xref:System.Windows.Input.MouseGesture>.  Vous pouvez considérer un <xref:System.Windows.Input.KeyGesture> comme un raccourci clavier, par exemple Ctrl+C.  Un <xref:System.Windows.Input.KeyGesture> est composé de <xref:System.Windows.Input.Key> et d’un ensemble de <xref:System.Windows.Input.ModifierKeys>.  Un <xref:System.Windows.Input.MouseGesture> est composé de <xref:System.Windows.Input.MouseAction> et d’un ensemble facultatif de <xref:System.Windows.Input.ModifierKeys>.  
  
 Pour permettre à <xref:System.Windows.Input.InputGesture> de servir de source de commande, il doit être associé à une commande. Il existe plusieurs façons d’accomplir cela.  Une première approche consiste à utiliser <xref:System.Windows.Input.InputBinding>.  
  
 L’exemple suivant montre comment créer <xref:System.Windows.Input.KeyBinding> entre <xref:System.Windows.Input.KeyGesture> et <xref:System.Windows.Input.RoutedCommand>.  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewXAMLKeyBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewxamlkeybinding)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewKeyBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewkeybinding)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewKeyBinding](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewkeybinding)]  
  
 Une autre approche permettant d’associer <xref:System.Windows.Input.InputGesture> à <xref:System.Windows.Input.RoutedCommand> consiste à ajouter <xref:System.Windows.Input.InputGesture> à <xref:System.Windows.Input.InputGestureCollection> sur <xref:System.Windows.Input.RoutedCommand>.  
  
 L’exemple suivant montre comment ajouter <xref:System.Windows.Input.KeyGesture> à <xref:System.Windows.Input.InputGestureCollection> de <xref:System.Windows.Input.RoutedCommand>.  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewKeyGestureOnCmd](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewkeygestureoncmd)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewKeyGestureOnCmd](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewkeygestureoncmd)]  
  
<a name="Command_Binding"></a>
### <a name="commandbinding"></a>CommandBinding  
 <xref:System.Windows.Input.CommandBinding> associe une commande aux gestionnaires d’événements qui implémentent la commande.  
  
 La classe <xref:System.Windows.Input.CommandBinding> contient une propriété <xref:System.Windows.Input.CommandBinding.Command%2A>, ainsi que les événements <xref:System.Windows.Input.CommandBinding.PreviewExecuted>, <xref:System.Windows.Input.CommandBinding.Executed>, <xref:System.Windows.Input.CommandBinding.PreviewCanExecute> et <xref:System.Windows.Input.CommandBinding.CanExecute>.  
  
 <xref:System.Windows.Input.CommandBinding.Command%2A> est la commande à laquelle <xref:System.Windows.Input.CommandBinding> est associé.  Les gestionnaires d’événements attachés aux événements <xref:System.Windows.Input.CommandBinding.PreviewExecuted> et <xref:System.Windows.Input.CommandBinding.Executed> implémentent la logique de commande.  Les gestionnaires d’événements attachés aux événements <xref:System.Windows.Input.CommandBinding.PreviewCanExecute> et <xref:System.Windows.Input.CommandBinding.CanExecute> déterminent si la commande peut s’exécuter sur la cible de commande actuelle.  
  
 L’exemple suivant montre comment créer <xref:System.Windows.Input.CommandBinding> dans le <xref:System.Windows.Window> racine d’une application.  <xref:System.Windows.Input.CommandBinding> associe la commande <xref:System.Windows.Input.ApplicationCommands.Open%2A> aux gestionnaires <xref:System.Windows.Input.CommandManager.Executed> et <xref:System.Windows.Input.CommandBinding.CanExecute>.  
  
 [!code-xaml[commandwithhandler#CommandHandlerCommandBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml#commandhandlercommandbinding)]  
  
 [!code-csharp[CommandHandlerProcedural#CommandHandlerBindingInit](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandHandlerProcedural/CSharp/Window1.xaml.cs#commandhandlerbindinginit)]
 [!code-vb[CommandHandlerProcedural#CommandHandlerBindingInit](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandHandlerProcedural/visualbasic/window1.xaml.vb#commandhandlerbindinginit)]  
  
 <xref:System.Windows.Input.ExecutedRoutedEventHandler> et <xref:System.Windows.Input.CanExecuteRoutedEventHandler> sont ensuite créés.  <xref:System.Windows.Input.ExecutedRoutedEventHandler> ouvre un <xref:System.Windows.MessageBox> qui affiche une chaîne indiquant que la commande a été exécutée.  <xref:System.Windows.Input.CanExecuteRoutedEventHandler> affecte à la propriété <xref:System.Windows.Input.CanExecuteRoutedEventArgs.CanExecute%2A> la valeur `true`.  
  
 [!code-csharp[commandwithhandler#CommandHandlerExecutedHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml.cs#commandhandlerexecutedhandler)]
 [!code-vb[commandwithhandler#CommandHandlerExecutedHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/commandWithHandler/VisualBasic/Window1.xaml.vb#commandhandlerexecutedhandler)]  
  
 [!code-csharp[commandwithhandler#CommandHandlerCanExecuteHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml.cs#commandhandlercanexecutehandler)]
 [!code-vb[commandwithhandler#CommandHandlerCanExecuteHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/commandWithHandler/VisualBasic/Window1.xaml.vb#commandhandlercanexecutehandler)]  
  
 <xref:System.Windows.Input.CommandBinding> est attaché à un objet spécifique, par exemple le <xref:System.Windows.Window> racine de l’application ou un contrôle.  L’objet auquel <xref:System.Windows.Input.CommandBinding> est attaché définit la portée de la liaison.  Par exemple, un <xref:System.Windows.Input.CommandBinding> attaché à un ancêtre de la cible de commande est accessible à l’événement <xref:System.Windows.Input.CommandBinding.Executed>, mais un <xref:System.Windows.Input.CommandBinding> attaché à un descendant de la cible de commande est inaccessible.  Il s’agit d’une conséquence directe de la façon dont <xref:System.Windows.RoutedEvent> se propage à partir de l’objet qui déclenche l’événement.  
  
 Dans certaines situations, <xref:System.Windows.Input.CommandBinding> est attaché à la cible de commande elle-même, par exemple avec la classe <xref:System.Windows.Controls.TextBox> et les commandes <xref:System.Windows.Input.ApplicationCommands.Cut%2A>, <xref:System.Windows.Input.ApplicationCommands.Copy%2A> et <xref:System.Windows.Input.ApplicationCommands.Paste%2A>. Toutefois, il est bien souvent plus pratique d’attacher le <xref:System.Windows.Input.CommandBinding> à un ancêtre de la cible de commande, par exemple le <xref:System.Windows.Window> principal ou l’objet Application, en particulier si le même <xref:System.Windows.Input.CommandBinding> peut être utilisé pour plusieurs cibles de commande.  Il y a des décisions de conception à prendre en compte quand vous créez votre infrastructure de commandes.  
  
<a name="Commane_Target"></a>
### <a name="command-target"></a>Cible de commande  
 La cible de commande est l’élément sur lequel la commande est exécutée.  En ce qui concerne <xref:System.Windows.Input.RoutedCommand>, la cible de commande est l’élément à partir duquel le routage de <xref:System.Windows.Input.CommandManager.Executed> et <xref:System.Windows.Input.CommandManager.CanExecute> commence.  Comme cela a été indiqué, dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], la propriété <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> sur <xref:System.Windows.Input.ICommandSource> est applicable uniquement quand <xref:System.Windows.Input.ICommand> est un <xref:System.Windows.Input.RoutedCommand>.  Si <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> est défini sur <xref:System.Windows.Input.ICommandSource> et si la commande correspondante n’est pas <xref:System.Windows.Input.RoutedCommand>, la cible de commande est ignorée.  
  
 La source de commande peut définir explicitement la cible de commande.  Si la cible de commande n’est pas définie, l’élément ayant le focus clavier est utilisé comme cible de commande.  L’un des avantages liés à l’utilisation de l’élément ayant le focus clavier comme cible de commande est que cela permet au développeur de l’application d’utiliser la même source de commande pour appeler une commande sur plusieurs cibles sans avoir à effectuer le suivi de la cible de commande.  Par exemple, si <xref:System.Windows.Controls.MenuItem> appelle la commande **Coller** dans une application qui a un contrôle <xref:System.Windows.Controls.TextBox> et un contrôle <xref:System.Windows.Controls.PasswordBox>, la cible peut être <xref:System.Windows.Controls.TextBox> ou <xref:System.Windows.Controls.PasswordBox> en fonction du contrôle qui a le focus clavier.  
  
 L’exemple suivant montre comment définir explicitement la cible de commande dans le balisage et dans le code-behind.  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewXAMLCommandTarget](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewxamlcommandtarget)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcommandtargetcodebehind)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcommandtargetcodebehind)]  
  
<a name="Command_Manager"></a>
### <a name="the-commandmanager"></a>CommandManager  
 <xref:System.Windows.Input.CommandManager> remplit un certain nombre de fonctions associées aux commandes.  Il fournit un ensemble de méthodes statiques qui permettent d’ajouter et de supprimer les gestionnaires d’événements <xref:System.Windows.Input.CommandManager.PreviewExecuted>, <xref:System.Windows.Input.CommandManager.Executed>, <xref:System.Windows.Input.CommandManager.PreviewCanExecute> et <xref:System.Windows.Input.CommandManager.CanExecute> pour un élément spécifique.  Il permet d’inscrire des objets <xref:System.Windows.Input.CommandBinding> et <xref:System.Windows.Input.InputBinding> dans une classe spécifique.  <xref:System.Windows.Input.CommandManager> permet également, via l’événement <xref:System.Windows.Input.CommandManager.RequerySuggested>, de notifier à une commande le moment où elle doit déclencher l’événement <xref:System.Windows.Input.ICommand.CanExecuteChanged>.  
  
 La méthode <xref:System.Windows.Input.CommandManager.InvalidateRequerySuggested%2A> force <xref:System.Windows.Input.CommandManager> à déclencher l’événement <xref:System.Windows.Input.CommandManager.RequerySuggested>.  Cela est utile pour les conditions qui doivent désactiver/activer une commande, mais dont <xref:System.Windows.Input.CommandManager> n’a pas connaissance.  
  
<a name="Command_Library"></a>
## <a name="command-library"></a>Bibliothèque de commandes  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fournit un ensemble de commandes prédéfinies.  La bibliothèque de commandes comprend les classes suivantes : <xref:System.Windows.Input.ApplicationCommands>, <xref:System.Windows.Input.NavigationCommands>, <xref:System.Windows.Input.MediaCommands>, <xref:System.Windows.Documents.EditingCommands> et <xref:System.Windows.Input.ComponentCommands>.  Ces classes fournissent des commandes telles que <xref:System.Windows.Input.ApplicationCommands.Cut%2A>, <xref:System.Windows.Input.NavigationCommands.BrowseBack%2A> et <xref:System.Windows.Input.NavigationCommands.BrowseForward%2A>, <xref:System.Windows.Input.MediaCommands.Play%2A>, <xref:System.Windows.Input.MediaCommands.Stop%2A> et <xref:System.Windows.Input.MediaCommands.Pause%2A>.  
  
 Bon nombre de ces commandes incluent un jeu de liaisons d’entrée par défaut.  Par exemple, si vous spécifiez que votre application gère la commande de copie, vous recevez automatiquement la liaison de clavier « CTRL + C ». vous pouvez également obtenir des liaisons pour d’autres périphériques d’entrée, tels que des mouvements de stylet de Tablet PC et des informations vocales.  
  
 Quand vous référencez des commandes dans les différentes bibliothèques de commandes à l’aide de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], vous pouvez généralement omettre le nom de la classe de bibliothèque qui expose la propriété de commande statique. En général, les noms des commandes ne sont pas plus ambigus que des chaînes, et les types propriétaires existent pour fournir un regroupement logique de commandes, mais ne sont pas nécessaires pour éviter les ambiguïtés. Par exemple, vous pouvez spécifier `Command="Cut"` plutôt que la version plus détaillée `Command="ApplicationCommands.Cut"`. Il s’agit d’un mécanisme pratique qui est intégré au [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processeur pour les commandes (plus précisément, il s’agit d’un comportement de convertisseur de type de <xref:System.Windows.Input.ICommand> , que le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processeur référence au moment du chargement).  
  
<a name="creating_commands"></a>
## <a name="creating-custom-commands"></a>Création de commandes personnalisées  
 Si les commandes dans les classes de la bibliothèque de commandes ne répondent pas à vos besoins, vous pouvez créer vos propres commandes.  Il existe deux façons de créer une commande personnalisée.  La première consiste à partir de zéro et à implémenter l’interface <xref:System.Windows.Input.ICommand>.  La seconde, l’approche la plus courante, consiste à créer <xref:System.Windows.Input.RoutedCommand> ou <xref:System.Windows.Input.RoutedUICommand>.  
  
 Pour obtenir un exemple de création de <xref:System.Windows.Input.RoutedCommand> personnalisé, consultez [Créer un exemple RoutedCommand personnalisé](https://github.com/Microsoft/WPF-Samples/tree/master/Input%20and%20Commands/CustomRoutedCommand).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Input.RoutedCommand>
- <xref:System.Windows.Input.CommandBinding>
- <xref:System.Windows.Input.InputBinding>
- <xref:System.Windows.Input.CommandManager>
- [Vue d'ensemble des entrées](input-overview.md)
- [Vue d'ensemble des événements routés](routed-events-overview.md)
- [Implémenter ICommandSource](how-to-implement-icommandsource.md)
- [Guide pratique pour ajouter une commande à un MenuItem](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms741839(v=vs.90))
- [Créer un exemple RoutedCommand personnalisé](https://github.com/Microsoft/WPF-Samples/tree/master/Input%20and%20Commands/CustomRoutedCommand)
