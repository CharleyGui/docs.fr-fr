---
title: Vue d'ensemble des entrées
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- commands [WPF]
- input [WPF], overview
- keyboard focus [WPF]
- keyboard input [WPF]
- touch events [WPF]
- event routing [WPF]
- touch input [WPF]
- manipulation [WPF]
- logical focus [WPF]
- stylus input [WPF]
- text input [WPF]
- input events [WPF], handling
- WPF [WPF], input overview
- manipulation events [WPF]
- mouse input [WPF]
- mouse capture [WPF]
- focus [WPF]
- mouse position [WPF]
ms.assetid: ee5258b7-6567-415a-9b1c-c0cbe46e79ef
ms.openlocfilehash: 8fa9f2dd668efca6a3108973ff792cc17b37b410
ms.sourcegitcommit: 10736f243dd2296212e677e207102c463e5f143e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/06/2019
ms.locfileid: "68818036"
---
# <a name="input-overview"></a>Vue d'ensemble des entrées
<a name="introduction"></a>Le [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] sous-système fournit une API puissante pour obtenir des entrées à partir d’un large éventail d’appareils, notamment la souris, le clavier, le toucher et le stylet. Cette rubrique décrit les services fournis par [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] et explique l’architecture des systèmes d’entrée.

<a name="input_api"></a>
## <a name="input-api"></a>API d’entrée
 L’exposition principale de l’API d’entrée se trouve dans les classes <xref:System.Windows.UIElement>d' <xref:System.Windows.ContentElement>éléments de base <xref:System.Windows.FrameworkContentElement>:,, <xref:System.Windows.FrameworkElement>et.  Pour plus d’informations sur les éléments de base, consultez [Vue d’ensemble des éléments de base](base-elements-overview.md).  Ces classes fournissent la fonctionnalité pour les événements d’entrée associés aux appuis sur les boutons, aux boutons de la souris, à la roulette de la souris, au déplacement de la souris, à la gestion du focus et à la capture de la souris, entre autres. En plaçant l’API d’entrée sur les éléments de base, au lieu de traiter tous les événements d’entrée en tant que service, l’architecture d’entrée permet de sourcer les événements d’entrée par un objet particulier dans l’interface utilisateur et de prendre en charge un schéma de routage d’événements dans lequel plusieurs éléments ont un élément opp. ortunity pour gérer un événement d’entrée. De nombreux événements d’entrée sont associés à une paire d’événements.  Par exemple, l’événement touche enfoncée est associé <xref:System.Windows.Input.Keyboard.KeyDown> aux <xref:System.Windows.Input.Keyboard.PreviewKeyDown> événements et.  La différence entre ces événements réside dans la façon dont ils sont acheminés vers l’élément cible.  Les événements Preview parcourent l’arborescence d’éléments de l’élément racine vers l’élément cible.  Les événements de propagation se propagent de l’élément cible vers l’élément racine.  Le routage d’événements dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] est discuté plus en détail plus loin dans cet article et dans la rubrique [Vue d’ensemble des événements routés](routed-events-overview.md).

### <a name="keyboard-and-mouse-classes"></a>Classes de souris et de clavier
 En plus de l’API d’entrée sur les classes d’éléments de <xref:System.Windows.Input.Keyboard> base, <xref:System.Windows.Input.Mouse> la classe et les classes fournissent une API supplémentaire pour l’utilisation de l’entrée au clavier et à la souris.

 Les exemples d’API d’entrée <xref:System.Windows.Input.Keyboard> sur la classe <xref:System.Windows.Input.Keyboard.Modifiers%2A> sont la propriété, qui <xref:System.Windows.Input.ModifierKeys> retourne le actuellement enfoncé et <xref:System.Windows.Input.Keyboard.IsKeyDown%2A> la méthode, qui détermine si une touche spécifiée est enfoncée.

 L’exemple suivant utilise la <xref:System.Windows.Input.Keyboard.GetKeyStates%2A> méthode pour déterminer si un <xref:System.Windows.Input.Key> est à l’état inactif.

 [!code-csharp[keyargssnippetsample#KeyEventArgsKeyBoardGetKeyStates](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyArgsSnippetSample/CSharp/Window1.xaml.cs#keyeventargskeyboardgetkeystates)]
 [!code-vb[keyargssnippetsample#KeyEventArgsKeyBoardGetKeyStates](~/samples/snippets/visualbasic/VS_Snippets_Wpf/KeyArgsSnippetSample/visualbasic/window1.xaml.vb#keyeventargskeyboardgetkeystates)]

 Les exemples d’API d’entrée <xref:System.Windows.Input.Mouse> sur la <xref:System.Windows.Input.Mouse.MiddleButton%2A>classe sont, qui obtiennent l’état du bouton central de la souris <xref:System.Windows.Input.Mouse.DirectlyOver%2A>, et, qui obtient l’élément sur lequel le pointeur de la souris se trouve actuellement.

 L’exemple suivant détermine si le <xref:System.Windows.Input.Mouse.LeftButton%2A> sur la souris est dans l' <xref:System.Windows.Input.MouseButtonState.Pressed> État.

 [!code-csharp[mouserelatedsnippets#MouseRelatedSnippetsGetLeftButtonMouse](~/samples/snippets/csharp/VS_Snippets_Wpf/MouseRelatedSnippets/CSharp/Window1.xaml.cs#mouserelatedsnippetsgetleftbuttonmouse)]
 [!code-vb[mouserelatedsnippets#MouseRelatedSnippetsGetLeftButtonMouse](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MouseRelatedSnippets/visualbasic/window1.xaml.vb#mouserelatedsnippetsgetleftbuttonmouse)]

 Les <xref:System.Windows.Input.Mouse> classes <xref:System.Windows.Input.Keyboard> et sont décrites plus en détail dans cette vue d’ensemble.

### <a name="stylus-input"></a>Entrée du stylet
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]a intégré la <xref:System.Windows.Input.Stylus>prise en charge de.  Est une entrée de stylet rendue populaire par [!INCLUDE[TLA#tla_tpc](../../../../includes/tlasharptla-tpc-md.md)]le. <xref:System.Windows.Input.Stylus>  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]les applications peuvent traiter le stylet comme une souris à l’aide de l’API [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Mouse, mais elle expose également une abstraction d’appareil de stylet qui utilise un modèle semblable au clavier et à la souris.  Toutes les API liées à Stylus contiennent le mot «Stylus».

 Étant donné que le stylet peut agir comme une souris, les applications qui prennent uniquement en charge l’entrée de la souris peuvent quand même bénéficier automatiquement d’un certain niveau de prise en charge du stylet. Quand le stylet est utilisé de cette manière, l’application a la possibilité de gérer l’événement de stylet approprié, et elle gère ensuite l’événement de souris correspondant. En outre, les services de niveau supérieur tels que l’entrée d’encre sont également disponibles grâce à l’abstraction du stylet.  Pour plus d’informations sur l’encre comme entrée, consultez [Débuter avec l’encre](getting-started-with-ink.md).

<a name="event_routing"></a>
## <a name="event-routing"></a>Routage d’événements
 Un <xref:System.Windows.FrameworkElement> peut contenir d’autres éléments en tant qu’éléments enfants dans son modèle de contenu, formant une arborescence d’éléments.  Dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], l’élément parent peut participer à l’entrée dirigée vers ses éléments enfants ou à d’autres descendants en gérant les événements. Ceci est particulièrement utile pour la création de contrôles à partir de contrôles plus petits, un processus appelé « composition de contrôle » ou simplement « composition ». Pour plus d’informations sur les arborescences d’éléments et sur les relations entre les arborescences d’éléments et les itinéraires des événements, consultez [Arborescences dans WPF](trees-in-wpf.md).

 Le routage d’événements est le processus qui consiste à transférer des événements à plusieurs éléments, afin qu’un objet ou un élément sur l’itinéraire puisse choisir de fournir une réponse significative (par l’intermédiaire de la gestion) à un événement ayant pu avoir comme source un autre élément.  Les événements routés utilisent l’un des trois mécanismes de routage suivants : direct, par propagation et par tunneling.  Avec le routage direct, l’élément source est le seul élément notifié, et l’événement n’est pas acheminé vers d’autres éléments. Toutefois, l’événement routé direct offre toujours des fonctionnalités supplémentaires qui sont uniquement présentes pour les événements routés, par opposition aux événements CLR standard. La propagation remonte l’arborescence d’éléments en notifiant d’abord l’élément à l’origine de l’événement, puis l’élément parent, et ainsi de suite.  Le tunneling commence à la racine de l’arborescence d’éléments puis descend, en finissant à l’élément source d’origine.  Pour plus d’informations sur les événements routés, consultez [Vue d’ensemble des événements routés](routed-events-overview.md).

 Les événements d’entrée [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] existent généralement par paires, constituées d’un événement de tunneling et d’un événement de propagation.  Les événements de tunneling se distinguent des événements de propagation par le préfixe « Preview ».  Par exemple, <xref:System.Windows.Input.Mouse.PreviewMouseMove> est la version de tunneling d’un événement de déplacement <xref:System.Windows.Input.Mouse.MouseMove> de la souris et est la version de propagation de cet événement. Cet appariement d’événements est une convention implémentée au niveau de l’élément. Ce n’est pas une fonctionnalité inhérente au système d’événements [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Pour plus d’informations, consultez la section Événements d’entrée WPF dans [Vue d’ensemble des événements routés](routed-events-overview.md).

<a name="handling_input_events"></a>
## <a name="handling-input-events"></a>Gestion des événements d’entrée
 Pour recevoir une entrée sur un élément, un gestionnaire d’événements doit être associé à cet événement particulier.  Dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], c’est simple : vous référencez le nom de l’événement en tant qu’attribut de l’élément qui écoute cet événement.  Ensuite, vous affectez comme valeur de l’attribut le nom du gestionnaire d’événements que vous définissez, en fonction d’un délégué.  Le gestionnaire d’événements doit être écrit dans du code C# tel que et peut être inclus dans un fichier code-behind.

 Les événements de clavier se produisent quand le système d’exploitation signale des actions de touches qui ont lieu pendant que le focus clavier se trouve sur un élément. Les événements de souris et de stylet appartiennent chacun à deux catégories : les événements qui signalent des changements de la position du pointeur par rapport à l’élément, et les événements qui signalent des changements d’état des boutons du périphérique.

### <a name="keyboard-input-event-example"></a>Exemple d’événement d’entrée de clavier
 L’exemple suivant détecte un appui sur la touche de direction gauche.  Un <xref:System.Windows.Controls.StackPanel> est créé avec un <xref:System.Windows.Controls.Button>.  Un gestionnaire d’événements pour écouter l’appui sur la touche de direction gauche est <xref:System.Windows.Controls.Button> attaché à l’instance.

 La première section de l’exemple crée le <xref:System.Windows.Controls.StackPanel> et le <xref:System.Windows.Controls.Button> et attache le gestionnaire d’événements pour le <xref:System.Windows.UIElement.KeyDown>.

 [!code-xaml[InputOvw#Input_OvwKeyboardExampleXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml#input_ovwkeyboardexamplexaml)]

 [!code-csharp[InputOvw#Input_OvwKeyboardExampleUICodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml.cs#input_ovwkeyboardexampleuicodebehind)]
 [!code-vb[InputOvw#Input_OvwKeyboardExampleUICodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InputOvw/VisualBasic/Page1.xaml.vb#input_ovwkeyboardexampleuicodebehind)]

 La deuxième section est écrite en code et définit le gestionnaire d’événements.  Quand la touche de direction gauche est enfoncée et que le a le <xref:System.Windows.Controls.Button> focus clavier, le gestionnaire s’exécute et la <xref:System.Windows.Controls.Control.Background%2A> couleur du <xref:System.Windows.Controls.Button> est modifiée.  Si la touche est enfoncée, mais qu’il ne s’agit pas de <xref:System.Windows.Controls.Control.Background%2A> la touche <xref:System.Windows.Controls.Button> de direction gauche, la couleur du est rétablie à sa couleur de départ.

 [!code-csharp[InputOvw#Input_OvwKeyboardExampleHandlerCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml.cs#input_ovwkeyboardexamplehandlercodebehind)]
 [!code-vb[InputOvw#Input_OvwKeyboardExampleHandlerCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InputOvw/VisualBasic/Page1.xaml.vb#input_ovwkeyboardexamplehandlercodebehind)]

### <a name="mouse-input-event-example"></a>Exemple d’événement d’entrée de souris
 Dans l’exemple suivant, la <xref:System.Windows.Controls.Control.Background%2A> couleur d’un <xref:System.Windows.Controls.Button> est modifiée lorsque le pointeur de la souris <xref:System.Windows.Controls.Button>entre dans le.  La <xref:System.Windows.Controls.Control.Background%2A> couleur est restaurée lorsque la souris quitte <xref:System.Windows.Controls.Button>le.

 La première section de l’exemple crée le <xref:System.Windows.Controls.StackPanel> et le <xref:System.Windows.Controls.Button> contrôle et attache les gestionnaires d’événements pour <xref:System.Windows.Controls.Button>les <xref:System.Windows.UIElement.MouseEnter> événements et <xref:System.Windows.UIElement.MouseLeave> à.

 [!code-xaml[InputOvw#Input_OvwMouseExampleXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml#input_ovwmouseexamplexaml)]

 [!code-csharp[InputOvw#Input_OvwMouseExampleUICodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml.cs#input_ovwmouseexampleuicodebehind)]
 [!code-vb[InputOvw#Input_OvwMouseExampleUICodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InputOvw/VisualBasic/Page1.xaml.vb#input_ovwmouseexampleuicodebehind)]

 La deuxième section est écrite en code et définit le gestionnaire d’événements.  <xref:System.Windows.Controls.Button>Lorsque la souris entre dans, la <xref:System.Windows.Controls.Control.Background%2A> couleur du <xref:System.Windows.Controls.Button> est remplacée par <xref:System.Windows.Media.Brushes.SlateGray%2A>.  Lorsque la souris quitte le <xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.Control.Background%2A> , la couleur du <xref:System.Windows.Controls.Button> est rétablie <xref:System.Windows.Media.Brushes.AliceBlue%2A>.

 [!code-csharp[InputOvw#Input_OvwMouseExampleEneterHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml.cs#input_ovwmouseexampleeneterhandler)]
 [!code-vb[InputOvw#Input_OvwMouseExampleEneterHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InputOvw/VisualBasic/Page1.xaml.vb#input_ovwmouseexampleeneterhandler)]

 [!code-csharp[InputOvw#Input_OvwMouseExampleLeaveHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml.cs#input_ovwmouseexampleleavehandler)]
 [!code-vb[InputOvw#Input_OvwMouseExampleLeaveHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InputOvw/VisualBasic/Page1.xaml.vb#input_ovwmouseexampleleavehandler)]

<a name="text_input"></a>
## <a name="text-input"></a>Entrée de texte
 L' <xref:System.Windows.ContentElement.TextInput> événement vous permet d’écouter l’entrée de texte d’une manière indépendante du périphérique. Le clavier est le principal moyen d’entrer du texte, mais la voix, l’écriture manuscrite et d’autres périphériques d’entrée peuvent aussi générer du texte.

 Pour les entrées au [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] clavier, envoie d' <xref:System.Windows.ContentElement.KeyDown> abord les événements appropriés /. <xref:System.Windows.ContentElement.KeyUp> Si ces événements ne sont pas gérés et que la clé est textuelle (au lieu d’une touche de contrôle telle que des flèches directionnelles ou <xref:System.Windows.ContentElement.TextInput> des touches de fonction), un événement est déclenché.  Il n’existe pas toujours un mappage un-à-un simple <xref:System.Windows.ContentElement.KeyDown> entre <xref:System.Windows.ContentElement.TextInput> / <xref:System.Windows.ContentElement.KeyUp> des événements et, car plusieurs séquences de touches peuvent générer un caractère unique d’entrée de texte et les séquences de touches peuvent générer plusieurs caractères celles.  Cela est particulièrement vrai pour les langues telles que le chinois, le japonais et le coréen qui utilisent des éditeurs de méthode d’entrée (IME) pour générer les milliers de caractères possibles dans les alphabets correspondants.

 Lorsque [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] envoie un <xref:System.Windows.ContentElement.KeyUp> <xref:System.Windows.Input.Key.System?displayProperty=nameWithType> <xref:System.Windows.ContentElement.TextInput> événement, a<xref:System.Windows.Input.KeyEventArgs.Key%2A> la valeur si les séquences de touches peuvent faire partie d’un événement (en appuyant sur ALT + S, par exemple). / <xref:System.Windows.ContentElement.KeyDown> Cela permet au code dans <xref:System.Windows.ContentElement.KeyDown> un gestionnaire d’événements de <xref:System.Windows.Input.Key.System?displayProperty=nameWithType> vérifier et, s’il existe, de conserver le traitement du gestionnaire de <xref:System.Windows.ContentElement.TextInput> l’événement déclenché par la suite. Dans ces cas, les différentes propriétés de l' <xref:System.Windows.Input.TextCompositionEventArgs> argument peuvent être utilisées pour déterminer les séquences de touches d’origine. De même, si un [!INCLUDE[TLA2#tla_ime](../../../../includes/tla2sharptla-ime-md.md)] est actif, <xref:System.Windows.Input.Key> a la valeur <xref:System.Windows.Input.Key.ImeProcessed?displayProperty=nameWithType>et <xref:System.Windows.Input.KeyEventArgs.ImeProcessedKey%2A> donne la séquence d’origine ou les séquences de touches.

 L’exemple suivant définit un gestionnaire pour l' <xref:System.Windows.Controls.Primitives.ButtonBase.Click> événement et un gestionnaire pour l' <xref:System.Windows.UIElement.KeyDown> événement.

 Le premier segment de code ou de balisage crée l’interface utilisateur.

 [!code-xaml[InputOvw#Input_OvwTextInputXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml#input_ovwtextinputxaml)]

 [!code-csharp[InputOvw#Input_OvwTextInputUICodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml.cs#input_ovwtextinputuicodebehind)]
 [!code-vb[InputOvw#Input_OvwTextInputUICodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InputOvw/VisualBasic/Page1.xaml.vb#input_ovwtextinputuicodebehind)]

 Le deuxième segment de code contient les gestionnaires d’événements.

 [!code-csharp[InputOvw#Input_OvwTextInputHandlersCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml.cs#input_ovwtextinputhandlerscodebehind)]
 [!code-vb[InputOvw#Input_OvwTextInputHandlersCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InputOvw/VisualBasic/Page1.xaml.vb#input_ovwtextinputhandlerscodebehind)]

 Étant donné que les événements d’entrée propagent <xref:System.Windows.Controls.StackPanel> l’itinéraire des événements, le reçoit l’entrée quel que soit l’élément qui a le focus clavier. Le <xref:System.Windows.Controls.TextBox> contrôle est notifié en premier et `OnTextInputKeyDown` le gestionnaire est appelé uniquement si <xref:System.Windows.Controls.TextBox> le n’a pas géré l’entrée. Si l' <xref:System.Windows.UIElement.PreviewKeyDown> événement est utilisé à la place <xref:System.Windows.UIElement.KeyDown> de l’événement `OnTextInputKeyDown` , le gestionnaire est appelé en premier.

 Dans cet exemple, la logique de gestion est écrite deux fois : une fois pour Ctrl+O et une autre fois pour l’événement de clic du bouton. Vous pouvez simplifier cela en utilisant des commandes, au lieu de traiter les événements d’entrée directement.  Les commandes sont traitées dans cet article et dans [Vue d’ensemble des commandes](commanding-overview.md).

<a name="touch_and_manipulation"></a>
## <a name="touch-and-manipulation"></a>Entrée tactile et manipulation
 Du nouveau matériel et une nouvelle API dans le système d’exploitation Windows 7 permettent aux applications de recevoir une entrée à partir de plusieurs entrées tactiles simultanément. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] permet aux applications de détecter et de répondre aux entrées tactiles d’une manière similaire à d’autres types d’entrée, tels que la souris ou le clavier, en déclenchant des événements quand les entrées tactiles se produisent.

 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] expose deux types d’événements quand des entrées tactiles se produisent : les événements tactiles et les événements de manipulation. Les événements tactiles fournissent des données brutes relatives à chaque doigt sur un écran tactile et à leur déplacement. Les événements de manipulation interprètent l’entrée comme des actions spécifiques. Les deux types d’événements sont présentés dans cette section.

### <a name="prerequisites"></a>Prérequis
 Vous devez disposer des composants suivants pour développer une application qui répond aux entrées tactiles.

- Visual Studio 2010.

- Windows 7.

- Un appareil, tel qu’un écran tactile, qui prend en charge l’interface tactile Windows.

### <a name="terminology"></a>Terminologie
 Les termes suivants sont utilisés quand l’entrée tactile est abordée.

- L’**entrée tactile** est un type d’entrée d’utilisateur reconnu par Windows 7. En règle générale, l’entrée tactile est démarrée en plaçant des doigts sur un écran tactile. Notez que les appareils tels que les pavés tactiles qui sont courants sur les ordinateurs portables ne gèrent pas l’entrée tactile si l’appareil ne fait que convertir la position et le déplacement du doigt en tant qu’entrée de la souris.

- L’**interaction tactile multipoint** est une entrée tactile qui se produit simultanément à partir de plusieurs points. Windows 7 et [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] prennent en charge l’interaction tactile multipoint. Chaque fois que l’entrée tactile est abordée dans la documentation [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], les concepts s’appliquent à l’interaction tactile multipoint.

- Une **manipulation** se produit quand l’entrée tactile est interprétée comme une action physique appliquée à un objet. Dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], les événements de manipulation interprètent l’entrée comme une manipulation de translation, d’expansion ou de rotation.

- Un `touch device` représente un périphérique qui génère une entrée tactile, par exemple un seul doigt sur un écran tactile.

### <a name="controls-that-respond-to-touch"></a>Contrôles qui répondent aux entrées tactiles
 Les contrôles suivants peuvent être parcourus en faisant glisser un doigt sur le contrôle, s’il a du contenu qui défile hors de l’affichage.

- <xref:System.Windows.Controls.ComboBox>

- <xref:System.Windows.Controls.ContextMenu>

- <xref:System.Windows.Controls.DataGrid>

- <xref:System.Windows.Controls.ListBox>

- <xref:System.Windows.Controls.ListView>

- <xref:System.Windows.Controls.MenuItem>

- <xref:System.Windows.Controls.TextBox>

- <xref:System.Windows.Controls.ToolBar>

- <xref:System.Windows.Controls.TreeView>

 Définit la propriété <xref:System.Windows.Controls.ScrollViewer.PanningMode%2A?displayProperty=nameWithType> jointe qui vous permet de spécifier si le panoramique tactile est activé horizontalement, verticalement, les deux ou aucune des deux. <xref:System.Windows.Controls.ScrollViewer> La <xref:System.Windows.Controls.ScrollViewer.PanningDeceleration%2A?displayProperty=nameWithType> propriété spécifie la vitesse de ralentissement du défilement lorsque l’utilisateur soulève le doigt de l’écran tactile. La <xref:System.Windows.Controls.ScrollViewer.PanningRatio%2A?displayProperty=nameWithType> propriété jointe spécifie le ratio de décalage de défilement pour traduire le décalage de manipulation.

### <a name="touch-events"></a>Événements tactiles
 Les classes de base <xref:System.Windows.UIElement>, <xref:System.Windows.UIElement3D>, et <xref:System.Windows.ContentElement>, définissent les événements auxquels vous pouvez vous abonner pour que votre application réponde à Touch. Les événements tactiles sont utiles quand votre application interprète l’entrée tactile comme autre chose que la manipulation d’un objet. Par exemple, une application qui permet à un utilisateur de dessiner avec un ou plusieurs doigts doit s’abonner aux événements tactiles.

 Les trois classes définissent les événements suivants, qui se comportent de la même manière quelle que soit la classe de définition.

- <xref:System.Windows.UIElement.TouchDown>

- <xref:System.Windows.UIElement.TouchMove>

- <xref:System.Windows.UIElement.TouchUp>

- <xref:System.Windows.UIElement.TouchEnter>

- <xref:System.Windows.UIElement.TouchLeave>

- <xref:System.Windows.UIElement.PreviewTouchDown>

- <xref:System.Windows.UIElement.PreviewTouchMove>

- <xref:System.Windows.UIElement.PreviewTouchUp>

- <xref:System.Windows.UIElement.GotTouchCapture>

- <xref:System.Windows.UIElement.LostTouchCapture>

 Comme les événements de clavier et de souris, les événements tactiles sont des événements routés. Les événements qui commencent par `Preview` sont des événements de tunneling et les événements qui commencent par `Touch` sont des événements de propagation. Pour plus d’informations sur les événements routés, consultez [Vue d’ensemble des événements routés](routed-events-overview.md). Lorsque vous gérez ces événements, vous pouvez récupérer la position de l’entrée, par rapport à tout élément, en appelant <xref:System.Windows.Input.TouchEventArgs.GetTouchPoint%2A> la <xref:System.Windows.Input.TouchEventArgs.GetIntermediateTouchPoints%2A> méthode ou.

 Pour comprendre l’interaction entre les événements tactiles, considérez le scénario où un utilisateur place un doigt sur un élément, déplace son doigt dans l’élément, puis retire son doigt de l’élément. L’illustration suivante montre l’exécution des événements de propagation (les événements de tunneling sont omis par souci de simplicité).

 ![Séquence d’événements tactiles.](./media/ndp-touchevents.png "NDP_TouchEvents") Événements tactiles

 La liste suivante décrit la séquence des événements dans l’illustration précédente.

1. L' <xref:System.Windows.UIElement.TouchEnter> événement se produit une fois lorsque l’utilisateur place un doigt sur l’élément.

2. L' <xref:System.Windows.UIElement.TouchDown> événement se produit une fois.

3. L' <xref:System.Windows.UIElement.TouchMove> événement se produit plusieurs fois lorsque l’utilisateur déplace le doigt dans l’élément.

4. L' <xref:System.Windows.UIElement.TouchUp> événement se produit une fois lorsque l’utilisateur soulève le doigt de l’élément.

5. L' <xref:System.Windows.UIElement.TouchLeave> événement se produit une fois.

 Quand plusieurs doigts sont utilisés, les événements se produisent pour chaque doigt.

### <a name="manipulation-events"></a>Événements de manipulation
 Dans les cas où une application permet à un utilisateur de manipuler un objet <xref:System.Windows.UIElement> , la classe définit des événements de manipulation. Contrairement aux événements tactiles qui signalent simplement la position de l’entrée tactile, les événements de manipulation signalent comment l’entrée peut être interprétée. Il existe trois types de manipulations : translation, expansion et rotation. La liste suivante décrit comment appeler les trois types de manipulations.

- Placez un doigt sur un objet et déplacez le doigt sur l’écran tactile pour appeler une manipulation de translation. Cela déplace habituellement l’objet.

- Placez deux doigts sur un objet et rapprochez ou éloignez les doigts pour appeler une manipulation d’expansion. Cela redimensionne habituellement l’objet.

- Placez deux doigts sur un objet et faites pivoter les doigts pour appeler une manipulation de rotation. Cela fait pivoter habituellement l’objet.

 Plusieurs types de manipulations peuvent se produire simultanément.

 Quand vous faites en sorte que des objets répondent à des manipulations, vous pouvez donner à l’objet une apparence d’inertie. Ainsi, vos objets peuvent simuler le monde physique. Par exemple, quand vous poussez un livre sur une table, si vous le poussez assez fort il continuera à se déplacer une fois que vous l’aurez relâché. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vous permet de simuler ce comportement en déclenchant des événements de manipulation après que les doigts de l’utilisateur ont relâché l’objet.

 Pour plus d’informations sur la création d’une application qui permet à l’utilisateur de déplacer, redimensionner et faire pivoter un objet, consultez [procédure pas à pas: Création de votre première application](walkthrough-creating-your-first-touch-application.md)Touch.

 <xref:System.Windows.UIElement> Définit les événements de manipulation suivants.

- <xref:System.Windows.UIElement.ManipulationStarting>

- <xref:System.Windows.UIElement.ManipulationStarted>

- <xref:System.Windows.UIElement.ManipulationDelta>

- <xref:System.Windows.UIElement.ManipulationInertiaStarting>

- <xref:System.Windows.UIElement.ManipulationCompleted>

- <xref:System.Windows.UIElement.ManipulationBoundaryFeedback>

 Par défaut, un <xref:System.Windows.UIElement> ne reçoit pas ces événements de manipulation. Pour recevoir des événements de manipulation <xref:System.Windows.UIElement>sur un <xref:System.Windows.UIElement.IsManipulationEnabled%2A?displayProperty=nameWithType> , `true`affectez à la valeur.

#### <a name="the-execution-path-of-manipulation-events"></a>Chemin d’exécution des événements de manipulation
 Imaginez un scénario où un utilisateur « jette » un objet. L’utilisateur place un doigt sur l’objet, déplace son doigt sur l’écran tactile sur une courte distance, puis retire son doigt pendant qu’il le déplace. La conséquence est que l’objet se déplace sous le doigt de l’utilisateur et continue à se déplacer après que l’utilisateur a retiré son doigt.

 L’illustration suivante montre le chemin d’exécution des événements de manipulation et des informations importantes sur chaque événement.

 ![Séquence des événements de manipulation.](./media/ndp-manipulationevents.png "NDP_ManipulationEvents") Événements de manipulation

 La liste suivante décrit la séquence des événements dans l’illustration précédente.

1. L' <xref:System.Windows.UIElement.ManipulationStarting> événement se produit lorsque l’utilisateur place un doigt sur l’objet. Entre autres choses, cet événement vous permet de définir la <xref:System.Windows.Input.ManipulationStartingEventArgs.ManipulationContainer%2A> propriété. Dans les événements suivants, la position de la manipulation sera relative à <xref:System.Windows.Input.ManipulationStartingEventArgs.ManipulationContainer%2A>. Dans les événements autres <xref:System.Windows.UIElement.ManipulationStarting>que, cette propriété est en lecture seule, l' <xref:System.Windows.UIElement.ManipulationStarting> événement est donc la seule heure à laquelle vous pouvez définir cette propriété.

2. L' <xref:System.Windows.UIElement.ManipulationStarted> événement se produit ensuite. Cet événement signale l’origine de la manipulation.

3. L' <xref:System.Windows.UIElement.ManipulationDelta> événement se produit plusieurs fois lorsque les doigts d’un utilisateur se déplacent sur un écran tactile. La <xref:System.Windows.Input.ManipulationDeltaEventArgs.DeltaManipulation%2A> propriété de la <xref:System.Windows.Input.ManipulationDeltaEventArgs> classe indique si la manipulation est interprétée comme un mouvement, une expansion ou une traduction. C’est là que vous effectuez la plupart du travail de manipulation d’un objet.

4. L' <xref:System.Windows.UIElement.ManipulationInertiaStarting> événement se produit lorsque les doigts de l’utilisateur perdent le contact avec l’objet. Cet événement vous permet de spécifier la décélération des manipulations pendant l’inertie, ceci afin que votre objet puisse émuler différents attributs ou espaces physiques si vous le souhaitez. Par exemple, supposez que votre application a deux objets qui représentent des éléments dans le monde physique, et que l’un d’eux a un poids supérieur à l’autre. Vous pouvez faire en sorte que l’objet le plus lourd décélère plus rapidement que l’objet plus léger.

5. L' <xref:System.Windows.UIElement.ManipulationDelta> événement se produit plusieurs fois pendant l’inertie. Notez que cet événement se produit quand les doigts de l’utilisateur se déplacent sur l’écran tactile et quand [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] simule l’inertie. En d’autres termes <xref:System.Windows.UIElement.ManipulationDelta> , se produit avant et <xref:System.Windows.UIElement.ManipulationInertiaStarting> après l’événement. La <xref:System.Windows.Input.ManipulationDeltaEventArgs.IsInertial%2A?displayProperty=nameWithType> propriété indique si l' <xref:System.Windows.UIElement.ManipulationDelta> événement se produit pendant l’inertie, ce qui vous permet de vérifier cette propriété et d’effectuer différentes actions, en fonction de sa valeur.

6. L' <xref:System.Windows.UIElement.ManipulationCompleted> événement se produit lorsque la manipulation et l’inertie se terminent. Autrement dit, une fois tous <xref:System.Windows.UIElement.ManipulationDelta> les événements survenus, l' <xref:System.Windows.UIElement.ManipulationCompleted> événement se produit pour signaler que la manipulation est terminée.

 Définit également l' <xref:System.Windows.UIElement.ManipulationBoundaryFeedback>événement. <xref:System.Windows.UIElement> Cet événement se produit lorsque <xref:System.Windows.Input.ManipulationDeltaEventArgs.ReportBoundaryFeedback%2A> la méthode est appelée dans <xref:System.Windows.UIElement.ManipulationDelta> l’événement. L' <xref:System.Windows.UIElement.ManipulationBoundaryFeedback> événement permet aux applications ou aux composants de fournir des commentaires visuels lorsqu’un objet atteint une limite. Par exemple, la <xref:System.Windows.Window> classe gère l' <xref:System.Windows.UIElement.ManipulationBoundaryFeedback> événement pour faire en sorte que la fenêtre se déplace légèrement lorsque son bord est rencontré.

 Vous pouvez annuler la manipulation en appelant la <xref:System.Windows.Input.ManipulationStartingEventArgs.Cancel%2A> méthode sur les arguments d’événement dans n’importe quel <xref:System.Windows.UIElement.ManipulationBoundaryFeedback> événement de manipulation, à l’exception de l’événement. Lorsque vous appelez <xref:System.Windows.Input.ManipulationStartingEventArgs.Cancel%2A>, les événements de manipulation ne sont plus déclenchés et les événements de souris se produisent pour les fonctions tactiles. Le tableau suivant décrit la relation entre le moment où la manipulation est annulée et les événements de souris qui se produisent.

|Événement pendant lequel Cancel est appelé|Événements de souris qui se produisent pour une entrée qui a déjà eu lieu|
|----------------------------------------|-----------------------------------------------------------------|
|<xref:System.Windows.UIElement.ManipulationStarting> et <xref:System.Windows.UIElement.ManipulationStarted>|Événements mouse down.|
|<xref:System.Windows.UIElement.ManipulationDelta>|Événements mouse down et mouse move.|
|<xref:System.Windows.UIElement.ManipulationInertiaStarting> et <xref:System.Windows.UIElement.ManipulationCompleted>|Événements mouse down, mouse move et mouse up.|

 Notez que si vous appelez <xref:System.Windows.Input.ManipulationStartingEventArgs.Cancel%2A> lorsque la manipulation est en inertie, la méthode `false` retourne et l’entrée ne déclenche pas d’événements de souris.

### <a name="the-relationship-between-touch-and-manipulation-events"></a>Relation entre les événements tactiles et les événements de manipulation
 Un <xref:System.Windows.UIElement> peut toujours recevoir des événements tactiles. Lorsque la <xref:System.Windows.UIElement.IsManipulationEnabled%2A> propriété a la valeur `true`, un <xref:System.Windows.UIElement> peut recevoir à la fois des événements tactiles et des événements de manipulation.  Si l' <xref:System.Windows.UIElement.TouchDown> événement n’est pas géré (autrement dit, <xref:System.Windows.RoutedEventArgs.Handled%2A> si la `false`propriété a la valeur), la logique de manipulation capture le toucher à l’élément et génère les événements de manipulation. Si la `true` propriété a la valeur dans l' <xref:System.Windows.UIElement.TouchDown> événement, la logique de manipulation ne génère pas d’événements de manipulation. <xref:System.Windows.RoutedEventArgs.Handled%2A> L’illustration suivante montre la relation entre les événements tactiles et les événements de manipulation.

 ![Relation entre les événements tactiles et les événements de manipulation](./media/ndp-touchmanipulateevents.png "NDP_TouchManipulateEvents") Événements tactiles et de manipulation

 La liste suivante décrit la relation entre les événements tactiles et les événements de manipulation indiquée dans l’illustration précédente.

- Lorsque le premier périphérique tactile génère un <xref:System.Windows.UIElement.TouchDown> événement sur un <xref:System.Windows.UIElement>, la logique de manipulation appelle <xref:System.Windows.UIElement.CaptureTouch%2A> la méthode, qui génère <xref:System.Windows.UIElement.GotTouchCapture> l’événement.

- Lorsque se produit, la logique de manipulation appelle <xref:System.Windows.Input.Manipulation.AddManipulator%2A?displayProperty=nameWithType> la méthode, qui génère <xref:System.Windows.UIElement.ManipulationStarting> l’événement. <xref:System.Windows.UIElement.GotTouchCapture>

- Lorsque les <xref:System.Windows.UIElement.TouchMove> événements se produisent, la logique de manipulation <xref:System.Windows.UIElement.ManipulationDelta> génère les événements qui se <xref:System.Windows.UIElement.ManipulationInertiaStarting> produisent avant l’événement.

- Lorsque le dernier appareil tactile de l’élément déclenche l' <xref:System.Windows.UIElement.TouchUp> événement, la logique de manipulation génère <xref:System.Windows.UIElement.ManipulationInertiaStarting> l’événement.

<a name="focus"></a>
## <a name="focus"></a>Focus
 Il existe deux concepts principaux associés au focus dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] : le focus clavier et le focus logique.

### <a name="keyboard-focus"></a>Focus clavier
 Le focus clavier fait référence à l’élément qui reçoit actuellement l’entrée au clavier.  Un seul élément de l’ordinateur peut avoir le focus clavier.  Dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], l’élément qui a le focus clavier <xref:System.Windows.IInputElement.IsKeyboardFocused%2A> aura la valeur `true`.  La méthode <xref:System.Windows.Input.Keyboard> <xref:System.Windows.Input.Keyboard.FocusedElement%2A> statique retourne l’élément qui a actuellement le focus clavier.

 Le focus clavier peut être obtenu par tabulation à un élément ou en cliquant avec la souris sur certains éléments, tels <xref:System.Windows.Controls.TextBox>qu’un.  Le focus clavier peut également être obtenu par programmation à l’aide <xref:System.Windows.Input.Keyboard.Focus%2A> de la méthode <xref:System.Windows.Input.Keyboard> sur la classe.  <xref:System.Windows.Input.Keyboard.Focus%2A>tente d’attribuer le focus clavier à l’élément spécifié.  L’élément retourné par <xref:System.Windows.Input.Keyboard.Focus%2A> est l’élément qui a actuellement le focus clavier.

 Pour qu’un élément obtienne le focus clavier, la <xref:System.Windows.UIElement.Focusable%2A> propriété et les <xref:System.Windows.UIElement.IsVisible%2A> propriétés doivent avoir la valeur **true**.  Certaines classes, telles que <xref:System.Windows.Controls.Panel>, ont <xref:System.Windows.UIElement.Focusable%2A> la valeur `false` par défaut; par conséquent, vous devrez peut-être définir cette `true` propriété sur si vous souhaitez que cet élément puisse obtenir le focus.

 L’exemple suivant utilise <xref:System.Windows.Input.Keyboard.Focus%2A> pour définir le focus clavier sur <xref:System.Windows.Controls.Button>un.  L’emplacement recommandé pour définir le focus initial dans une application se trouve <xref:System.Windows.FrameworkElement.Loaded> dans le gestionnaire d’événements.

 [!code-csharp[focussample#FocusSampleSetFocus](~/samples/snippets/csharp/VS_Snippets_Wpf/FocusSample/CSharp/Window1.xaml.cs#focussamplesetfocus)]
 [!code-vb[focussample#FocusSampleSetFocus](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSample/visualbasic/window1.xaml.vb#focussamplesetfocus)]

 Pour plus d’informations sur le focus clavier, consultez [Vue d’ensemble du focus](focus-overview.md).

### <a name="logical-focus"></a>Focus logique
 Le <xref:System.Windows.Input.FocusManager.FocusedElement%2A?displayProperty=nameWithType> focus logique fait référence à dans une portée de focus.  Plusieurs éléments d’une application peuvent avoir le focus logique, mais un seul élément peut avoir le focus logique dans une portée de focus donnée.

 Une portée de focus est un élément conteneur qui effectue le <xref:System.Windows.Input.FocusManager.FocusedElement%2A> suivi du dans sa portée.  Quand le focus quitte une portée de focus, l’élément ayant le focus perd le focus clavier, mais conserve le focus logique.  Quand le focus revient dans la portée de focus, l’élément ayant le focus obtient le focus clavier.  Cela permet au focus clavier de changer entre des portées de focus, et de s’assurer que l’élément ayant le focus dans la portée de focus demeure l’élément ayant le focus quand le focus revient.

 Un élément peut être converti en portée de focus dans [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] en affectant <xref:System.Windows.Input.FocusManager> à `true`la <xref:System.Windows.Input.FocusManager.IsFocusScope%2A> propriété jointe la valeur ou dans le code en définissant la <xref:System.Windows.Input.FocusManager.SetIsFocusScope%2A> propriété jointe à l’aide de la méthode.

 L’exemple suivant rend un <xref:System.Windows.Controls.StackPanel> en portée de focus en définissant <xref:System.Windows.Input.FocusManager.IsFocusScope%2A> la propriété jointe.

 [!code-xaml[MarkupSnippets#MarkupIsFocusScopeXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/MarkupSnippets/CSharp/Window1.xaml#markupisfocusscopexaml)]

 [!code-csharp[FocusSnippets#FocusSetIsFocusScope](~/samples/snippets/csharp/VS_Snippets_Wpf/FocusSnippets/CSharp/Window1.xaml.cs#focussetisfocusscope)]
 [!code-vb[FocusSnippets#FocusSetIsFocusScope](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSnippets/visualbasic/window1.xaml.vb#focussetisfocusscope)]

 Les classes [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dans lesquelles sont des portées de focus <xref:System.Windows.Window>par défaut <xref:System.Windows.Controls.ToolBar>sont, <xref:System.Windows.Controls.ContextMenu> <xref:System.Windows.Controls.Menu>, et.

 Un élément qui a le focus clavier aura également le focus logique pour la portée de focus à laquelle il appartient; par conséquent, le fait de définir le focus <xref:System.Windows.Input.Keyboard.Focus%2A> sur un élément <xref:System.Windows.Input.Keyboard> avec la méthode sur la classe ou les classes d’élément de base tente de fournir le focus clavier de l’élément et le focus logique.

 Pour déterminer l’élément ayant le focus dans une portée de <xref:System.Windows.Input.FocusManager.GetFocusedElement%2A>Focus, utilisez. Pour modifier l’élément ayant le focus pour une portée de <xref:System.Windows.Input.FocusManager.SetFocusedElement%2A>Focus, utilisez.

 Pour plus d’informations sur le focus logique, consultez [Vue d’ensemble du focus](focus-overview.md).

<a name="mouse_position"></a>
## <a name="mouse-position"></a>Position de la souris
 L' [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] API d’entrée fournit des informations utiles concernant les espaces de coordonnées.  Par exemple, la coordonnée `(0,0)` est la coordonnée de l’angle supérieur gauche, mais de quel élément dans l’arborescence ? L’élément qui est la cible d’entrée ? L’élément auquel vous avez attaché votre gestionnaire d’événements ? Ou un autre élément ? Pour éviter toute confusion, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] l’API d’entrée requiert que vous spécifiiez le cadre de référence lorsque vous travaillez avec des coordonnées obtenues à l’aide de la souris. La <xref:System.Windows.Input.Mouse.GetPosition%2A> méthode retourne la coordonnée du pointeur de la souris par rapport à l’élément spécifié.

<a name="mouse_capture"></a>
## <a name="mouse-capture"></a>Capture de la souris
 Les souris ont une caractéristique modale spécifique appelée capture de la souris. La capture de la souris sert à tenir à jour un état d’entrée transitionnel quand une opération de glisser-déplacer commence, afin que les autres opérations impliquant la position nominale à l’écran du pointeur de la souris ne se produisent pas nécessairement. Pendant l’opération glisser, l’utilisateur ne peut pas cliquer sans annuler le glisser-déplacer, ce qui rend la plupart des indices de survol de souris inappropriés pendant que la capture de la souris est détenue par l’origine de l’opération glisser. Le système d’entrée expose des API qui peuvent déterminer l’état de capture de la souris, ainsi que des API qui peuvent forcer la capture de la souris sur un élément spécifique ou effacer l’état de capture de la souris. Pour plus d’informations sur les opérations de glisser-déplacer, consultez [Vue d’ensemble du glisser-déplacer](drag-and-drop-overview.md).

<a name="commands"></a>
## <a name="commands"></a>Commandes
 Les commandes permettent de gérer les entrées à un niveau plus sémantique que l’entrée de périphérique.  Les commandes sont des directives simples, telles que `Cut`, `Copy`, `Paste` ou `Open`.  Elles sont utiles pour centraliser la logique de commande.  Il est possible d’accéder à la même <xref:System.Windows.Controls.Menu>commande à partir <xref:System.Windows.Controls.ToolBar>d’un, d’un ou d’un raccourci clavier. Les commandes fournissent également un mécanisme permettant de désactiver des contrôles quand la commande devient indisponible.

 <xref:System.Windows.Input.RoutedCommand>est l' [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] implémentation de <xref:System.Windows.Input.ICommand>.  Lorsqu’un <xref:System.Windows.Input.RoutedCommand> est exécuté, un <xref:System.Windows.Input.CommandManager.PreviewExecuted> et un <xref:System.Windows.Input.CommandManager.Executed> événement sont déclenchés sur la cible de commande, qui effectue un tunneling et effectue une propagation dans l’arborescence d’éléments comme une autre entrée.  Si une cible de commande n’est pas définie, l’élément qui a le focus clavier est la cible de commande.  La logique qui exécute la commande est attachée à <xref:System.Windows.Input.CommandBinding>un.  Lorsqu’un <xref:System.Windows.Input.CommandManager.Executed> événement atteint un <xref:System.Windows.Input.CommandBinding> pour cette <xref:System.Windows.Input.CommandBinding> commande spécifique, la <xref:System.Windows.Input.ExecutedRoutedEventHandler> sur est appelée.  Ce gestionnaire exécute l’action de la commande.

 Pour plus d’informations sur l’exécution des commandes, consultez [Vue d’ensemble des commandes](commanding-overview.md).

 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]fournit une bibliothèque de commandes courantes qui se compose <xref:System.Windows.Input.ApplicationCommands>de <xref:System.Windows.Input.MediaCommands>, <xref:System.Windows.Input.ComponentCommands>, <xref:System.Windows.Input.NavigationCommands>, et <xref:System.Windows.Documents.EditingCommands>, ou vous pouvez définir les vôtres.

 L’exemple suivant montre <xref:System.Windows.Controls.MenuItem> comment configurer un de sorte que, lorsque l’utilisateur clique dessus, il appelle la <xref:System.Windows.Input.ApplicationCommands.Paste%2A> commande sur <xref:System.Windows.Controls.TextBox>le, en supposant que a le <xref:System.Windows.Controls.TextBox> focus clavier.

 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewSimpleCommand](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewsimplecommand)]

 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcommandtargetcodebehind)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcommandtargetcodebehind)]

 Pour plus d’informations sur les commandes dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], consultez [Vue d’ensemble des commandes](commanding-overview.md).

<a name="the_input_system_and_base_elements"></a>
## <a name="the-input-system-and-base-elements"></a>Le système d’entrée et les éléments de base
 Les événements d’entrée tels que les événements attachés <xref:System.Windows.Input.Mouse>définis <xref:System.Windows.Input.Keyboard>par les <xref:System.Windows.Input.Stylus> classes, et sont déclenchés par le système d’entrée et injectés dans une position particulière dans le modèle objet en fonction du test d’atteinte de l’arborescence visuelle au moment de l’exécution.

 Chacun des événements qui <xref:System.Windows.Input.Mouse>, <xref:System.Windows.Input.Keyboard>et <xref:System.Windows.Input.Stylus> définis comme un événement attaché est également réexposé par les classes <xref:System.Windows.UIElement> d’élément de base et <xref:System.Windows.ContentElement> comme nouvel événement routé. Les événements routés d’éléments de base sont générés par des classes gérant l’événement attaché d’origine et réutilisant les données d’événements.

 Quand l’événement d’entrée est associé à un élément source particulier par l’intermédiaire de son implémentation d’événement d’entrée d’élément de base, il peut être routé le long du reste d’un itinéraire d’événement qui est basé sur une combinaison d’objets des arborescences visuelle et logique, et être géré par le code de l’application.  En règle générale, il est plus commode de gérer ces événements d’entrée liés à l’appareil à l' <xref:System.Windows.UIElement> aide <xref:System.Windows.ContentElement>des événements routés sur et, car vous pouvez utiliser une [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] syntaxe de gestionnaire d’événements plus intuitive à la fois dans et dans le code. Vous pouvez choisir à la place de gérer l’événement attaché qui a démarré le processus, mais vous serez alors confronté à plusieurs problèmes : l’événement attaché pourra être marqué comme géré par la gestion de classe d’élément de base, et vous devrez utiliser des méthodes d’accesseur plutôt qu’une réelle syntaxe d’événement pour attacher des gestionnaires pour les événements attachés.

<a name="whats_next"></a>
## <a name="whats-next"></a>Étapes suivantes
 Vous connaissez maintenant plusieurs techniques pour gérer les entrées dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  Vous devriez également mieux comprendre les différents types d’événements d’entrée et les mécanismes d’événements routés utilisés par [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].

 Si vous souhaitez en savoir plus, il existe des ressources supplémentaires qui expliquent les éléments de framework [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] et le routage d’événement plus en détail. Pour plus d’informations, consultez les vues d’ensemble suivantes : [Vue d’ensemble des commandes](commanding-overview.md), [Vue d’ensemble du focus](focus-overview.md), [Vue d’ensemble des éléments de base](base-elements-overview.md), [Arborescences dans WPF](trees-in-wpf.md) et [Vue d’ensemble des événements routés](routed-events-overview.md).

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble du focus](focus-overview.md)
- [Vue d’ensemble des commandes](commanding-overview.md)
- [Vue d’ensemble des événements routés](routed-events-overview.md)
- [Vue d’ensemble des éléments de base](base-elements-overview.md)
- [Propriétés](properties-wpf.md)
