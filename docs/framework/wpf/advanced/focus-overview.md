---
title: Vue d'ensemble du focus
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- applications [WPF], focus
- focus in applications [WPF]
ms.assetid: 0230c4eb-0c8a-462b-ac4b-ae3e511659f4
ms.openlocfilehash: de788ec3f0628ff2f7c422c76c73ff7985424113
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186668"
---
# <a name="focus-overview"></a>Vue d'ensemble du focus
Dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], il existe deux concepts principaux associés au focus : le focus clavier et le focus logique.  Le focus clavier fait référence à l’élément qui reçoit une entrée au clavier, tandis que le focus logique fait référence à l’élément d’une portée de focus qui a le focus.  Ces concepts sont présentés en détail dans cette vue d’ensemble.  Il est important de bien comprendre les différences entre ces concepts lors de la création d’applications complexes qui comportent plusieurs régions où le focus peut être obtenu.  
  
 Les classes principales qui participent <xref:System.Windows.Input.Keyboard> à la <xref:System.Windows.Input.FocusManager> gestion de mise au point <xref:System.Windows.UIElement> <xref:System.Windows.ContentElement>sont la classe, la classe, et les classes d’éléments de base, telles que et .  Pour plus d’informations sur les éléments de base, consultez [Vue d’ensemble des éléments de base](base-elements-overview.md).  
  
 La <xref:System.Windows.Input.Keyboard> classe est principalement concernée <xref:System.Windows.Input.FocusManager> par l’orientation du clavier et le est concerné principalement avec l’accent logique, mais ce n’est pas une distinction absolue.  En effet, un élément qui a le focus clavier possède également le focus logique, tandis qu’un élément qui a le focus logique ne possède pas nécessairement le focus clavier.  Ceci est évident lorsque <xref:System.Windows.Input.Keyboard> vous utilisez la classe pour définir l’élément qui a la mise au point clavier, car il définit également l’accent logique sur l’élément.  

<a name="Keyboard_Focus"></a>
## <a name="keyboard-focus"></a>Focus clavier  
 Le focus clavier fait référence à l’élément qui reçoit l’entrée au clavier.  Un seul élément de l’ordinateur peut avoir le focus clavier.  Dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], l’élément qui <xref:System.Windows.IInputElement.IsKeyboardFocused%2A> a `true`la mise au point clavier aura mis à .  La propriété <xref:System.Windows.Input.Keyboard.FocusedElement%2A> statique <xref:System.Windows.Input.Keyboard> sur la classe obtient l’élément qui a actuellement la mise au point clavier.  
  
 Pour qu’un élément obtienne la <xref:System.Windows.UIElement.Focusable%2A> mise <xref:System.Windows.UIElement.IsVisible%2A> au point du clavier, `true`les propriétés et les propriétés sur les éléments de base doivent être définies à .  Certaines classes, comme <xref:System.Windows.Controls.Panel> la classe <xref:System.Windows.UIElement.Focusable%2A> de `false` base, se sont définies par défaut; par conséquent, <xref:System.Windows.UIElement.Focusable%2A> vous `true` devez définir si vous voulez un tel élément pour être en mesure d’obtenir la mise au point clavier.  
  
 Le focus clavier peut être obtenu par interaction de l’utilisateur avec l’[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] (tabulation vers un élément ou clic de souris sur certains éléments, par exemple).  La mise au point du clavier peut <xref:System.Windows.Input.Keyboard.Focus%2A> également <xref:System.Windows.Input.Keyboard> être obtenue de façon programmatique en utilisant la méthode sur la classe.  La <xref:System.Windows.Input.Keyboard.Focus%2A> méthode tente de donner la mise au point du clavier d’élément spécifié.  L’élément retourné correspond à l’élément qui a le focus clavier. Il peut s’agir d’un autre élément que celui demandé si l’objet de focus précédent ou nouveau bloque la demande.  
  
 L’exemple suivant <xref:System.Windows.Input.Keyboard.Focus%2A> utilise la méthode <xref:System.Windows.Controls.Button>pour mettre l’accent clavier sur un .  
  
 [!code-csharp[focussample#FocusSampleSetFocus](~/samples/snippets/csharp/VS_Snippets_Wpf/FocusSample/CSharp/Window1.xaml.cs#focussamplesetfocus)]
 [!code-vb[focussample#FocusSampleSetFocus](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSample/visualbasic/window1.xaml.vb#focussamplesetfocus)]  
  
 La <xref:System.Windows.UIElement.IsKeyboardFocused%2A> propriété sur les classes d’élément de base obtient une valeur indiquant si l’élément a la mise au point du clavier.  La <xref:System.Windows.UIElement.IsKeyboardFocusWithin%2A> propriété sur les classes d’élément de base obtient une valeur indiquant si l’élément ou l’un de ses éléments visuels d’enfant a la mise au point de clavier.  
  
 Lors de la mise au point initiale au démarrage de l’application, l’élément pour recevoir <xref:System.Windows.UIElement.Focusable%2A> la <xref:System.Windows.UIElement.IsVisible%2A> mise `true`au point doit être dans l’arbre visuel de la fenêtre initiale chargée par l’application, et l’élément doit avoir et réglé à .  L’endroit recommandé pour définir <xref:System.Windows.FrameworkElement.Loaded> l’accent initial est dans le gestionnaire d’événement.  Un <xref:System.Windows.Threading.Dispatcher> rappel peut également être <xref:System.Windows.Threading.Dispatcher.Invoke%2A> <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A>utilisé en appelant ou .  
  
<a name="Logical_Focus"></a>
## <a name="logical-focus"></a>Focus logique  
 L’accent logique <xref:System.Windows.Input.FocusManager.FocusedElement%2A?displayProperty=nameWithType> se réfère à la portée dans une portée de mise au point.  Une portée de mise au point <xref:System.Windows.Input.FocusManager.FocusedElement%2A> est un élément qui suit le cadre de son champ d’application.  Quand le focus clavier quitte une portée de focus, l’élément ayant le focus perd le focus clavier, mais conserve le focus logique.  Quand le focus clavier revient dans la portée de focus, l’élément ayant le focus obtient le focus clavier.  Cela permet au focus clavier de changer entre des portées de focus et de s’assurer que l’élément ayant le focus dans la portée de focus retrouve le focus clavier quand le focus revient dans la portée de focus.  
  
 Plusieurs éléments d’une application peuvent avoir le focus logique, mais un seul élément peut avoir le focus logique dans une portée de focus donnée.  
  
 Un élément ayant le focus clavier a également le focus logique pour la portée de focus à laquelle il appartient.  
  
 Un élément peut être transformé [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] en une <xref:System.Windows.Input.FocusManager> portée <xref:System.Windows.Input.FocusManager.IsFocusScope%2A> `true`de mise au point en fixant la propriété ci-jointe à .  Dans le code, un élément peut être <xref:System.Windows.Input.FocusManager.SetIsFocusScope%2A>transformé en une portée de mise au point en appelant .  
  
 L’exemple suivant <xref:System.Windows.Controls.StackPanel> fait une portée <xref:System.Windows.Input.FocusManager.IsFocusScope%2A> de mise au point en fixant la propriété ci-jointe.  
  
 [!code-xaml[MarkupSnippets#MarkupIsFocusScopeXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/MarkupSnippets/CSharp/Window1.xaml#markupisfocusscopexaml)]  
  
 [!code-csharp[FocusSnippets#FocusSetIsFocusScope](~/samples/snippets/csharp/VS_Snippets_Wpf/FocusSnippets/CSharp/Window1.xaml.cs#focussetisfocusscope)]
 [!code-vb[FocusSnippets#FocusSetIsFocusScope](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSnippets/visualbasic/window1.xaml.vb#focussetisfocusscope)]  
  
 <xref:System.Windows.Input.FocusManager.GetFocusScope%2A>retourne la portée de mise au point de l’élément spécifié.  
  
 Les [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] classes dans lesquelles sont <xref:System.Windows.Window>des <xref:System.Windows.Controls.MenuItem> <xref:System.Windows.Controls.ToolBar>portées <xref:System.Windows.Controls.ContextMenu>de mise au point par défaut sont , , , et .  
  
 <xref:System.Windows.Input.FocusManager.GetFocusedElement%2A>obtient l’élément ciblé pour la portée de mise au point spécifiée.  <xref:System.Windows.Input.FocusManager.SetFocusedElement%2A>définit l’élément focalisé dans la portée de mise au point spécifiée.  <xref:System.Windows.Input.FocusManager.SetFocusedElement%2A>est généralement utilisé pour définir l’élément initial ciblé.  
  
 L’exemple suivant définit l’élément ayant le focus dans une portée de focus et obtient l’élément ayant le focus d’une portée de focus.  
  
 [!code-csharp[FocusSnippets#FocusGetSetFocusedElement](~/samples/snippets/csharp/VS_Snippets_Wpf/FocusSnippets/CSharp/Window1.xaml.cs#focusgetsetfocusedelement)]
 [!code-vb[FocusSnippets#FocusGetSetFocusedElement](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSnippets/visualbasic/window1.xaml.vb#focusgetsetfocusedelement)]  
  
<a name="Keyboard_Navigation"></a>
## <a name="keyboard-navigation"></a>Navigation au clavier  
 La <xref:System.Windows.Input.KeyboardNavigation> classe est responsable de la mise en œuvre de la navigation de mise au point du clavier par défaut lorsque l’une des clés de navigation est pressée.  Les touches de navigation sont les suivantes : TAB, MAJ+TAB, CTRL+TAB, CTRL+MAJ+TAB, FLÈCHE HAUT, FLÈCHE BAS, FLÈCHE GAUCHE et FLÈCHE DROITE.  
  
 Le comportement de navigation d’un conteneur <xref:System.Windows.Input.KeyboardNavigation> de <xref:System.Windows.Input.KeyboardNavigation.TabNavigation%2A> <xref:System.Windows.Input.KeyboardNavigation.ControlTabNavigation%2A>navigation <xref:System.Windows.Input.KeyboardNavigation.DirectionalNavigation%2A>peut être modifié en définissant les propriétés ci-jointes, et .  Ces propriétés <xref:System.Windows.Input.KeyboardNavigationMode> sont de type <xref:System.Windows.Input.KeyboardNavigationMode.Continue> <xref:System.Windows.Input.KeyboardNavigationMode.Local>et <xref:System.Windows.Input.KeyboardNavigationMode.Contained> <xref:System.Windows.Input.KeyboardNavigationMode.Cycle>les <xref:System.Windows.Input.KeyboardNavigationMode.Once>valeurs <xref:System.Windows.Input.KeyboardNavigationMode.None>possibles sont , , , , et .  La valeur <xref:System.Windows.Input.KeyboardNavigationMode.Continue>par défaut est , ce qui signifie que l’élément n’est pas un conteneur de navigation.  
  
 L’exemple suivant <xref:System.Windows.Controls.Menu> crée un <xref:System.Windows.Controls.MenuItem> avec un certain nombre d’objets.  La <xref:System.Windows.Input.KeyboardNavigation.TabNavigation%2A> propriété ci-jointe est réglée <xref:System.Windows.Input.KeyboardNavigationMode.Cycle> sur le <xref:System.Windows.Controls.Menu>.  Lorsque la mise au point <xref:System.Windows.Controls.Menu>est modifiée à l’aide de la clé de l’onglet dans le , la mise au point se déplacera de chaque élément et quand le dernier élément est atteint mise au point reviendra au premier élément.  
  
 [!code-xaml[MarkupSnippets#MarkupKeyboardNavigationTabNavigationXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/MarkupSnippets/CSharp/Window1.xaml#markupkeyboardnavigationtabnavigationxaml)]  
  
 [!code-csharp[MarkupSnippets#MarkupKeyboardNavigationTabNavigationCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/MarkupSnippets/CSharp/Window1.xaml.cs#markupkeyboardnavigationtabnavigationcode)]
 [!code-vb[MarkupSnippets#MarkupKeyboardNavigationTabNavigationCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MarkupSnippets/visualbasic/window1.xaml.vb#markupkeyboardnavigationtabnavigationcode)]  
  
<a name="Manipulating_Focus_Programmatically"></a>
## <a name="navigating-focus-programmatically"></a>Navigation du focus par programmation  
 API supplémentaires pour travailler <xref:System.Windows.UIElement.MoveFocus%2A> <xref:System.Windows.UIElement.PredictFocus%2A>avec mise au point sont et .  
  
 <xref:System.Windows.FrameworkElement.MoveFocus%2A>changements se concentrent sur l’élément suivant de l’application.  A <xref:System.Windows.Input.TraversalRequest> est utilisé pour spécifier la direction.   Le <xref:System.Windows.Input.FocusNavigationDirection> passé <xref:System.Windows.UIElement.MoveFocus%2A> pour spécifier les différentes directions <xref:System.Windows.Input.FocusNavigationDirection.First> <xref:System.Windows.Input.FocusNavigationDirection.Last>de <xref:System.Windows.Input.FocusNavigationDirection.Up> <xref:System.Windows.Input.FocusNavigationDirection.Down>mise au point peut être déplacé, tels que , , et .  
  
 L’exemple <xref:System.Windows.FrameworkElement.MoveFocus%2A> suivant sert à modifier l’élément ciblé.  
  
 [!code-csharp[focussample#FocusSampleMoveFocus](~/samples/snippets/csharp/VS_Snippets_Wpf/FocusSample/CSharp/Window1.xaml.cs#focussamplemovefocus)]
 [!code-vb[focussample#FocusSampleMoveFocus](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSample/visualbasic/window1.xaml.vb#focussamplemovefocus)]  
  
 <xref:System.Windows.FrameworkElement.PredictFocus%2A>retourne l’objet qui recevrait la mise au point si l’accent devait être modifié.  Actuellement, <xref:System.Windows.Input.FocusNavigationDirection.Up>seulement <xref:System.Windows.Input.FocusNavigationDirection.Down> <xref:System.Windows.Input.FocusNavigationDirection.Left>, <xref:System.Windows.Input.FocusNavigationDirection.Right> , et <xref:System.Windows.FrameworkElement.PredictFocus%2A>sont pris en charge par .  
  
<a name="Focus_Events"></a>
## <a name="focus-events"></a>Événements de focus  
 Les événements liés à <xref:System.Windows.Input.Keyboard.PreviewGotKeyboardFocus> <xref:System.Windows.Input.Keyboard.GotKeyboardFocus> la <xref:System.Windows.Input.Keyboard.PreviewLostKeyboardFocus> <xref:System.Windows.Input.Keyboard.LostKeyboardFocus>mise au point clavier sont , et , .  Les événements sont définis <xref:System.Windows.Input.Keyboard> comme des événements ci-joints sur la classe, mais sont plus facilement accessibles en tant qu’événements itinéraires équivalents sur les classes d’éléments de base.  Pour plus d’informations sur les événements, consultez [Vue d’ensemble des événements routés](routed-events-overview.md).  
  
 <xref:System.Windows.Input.Keyboard.GotKeyboardFocus>est soulevé lorsque l’élément obtient la mise au point du clavier.  <xref:System.Windows.Input.Keyboard.LostKeyboardFocus>est soulevé lorsque l’élément perd la mise au point du clavier.  Si <xref:System.Windows.Input.Keyboard.PreviewGotKeyboardFocus> l’événement <xref:System.Windows.Input.Keyboard.PreviewLostKeyboardFocusEvent> ou l’événement est géré et <xref:System.Windows.RoutedEventArgs.Handled%2A> est réglé à `true`, alors la mise au point ne changera pas.  
  
 L’exemple suivant <xref:System.Windows.UIElement.GotKeyboardFocus> <xref:System.Windows.UIElement.LostKeyboardFocus> se fixe et <xref:System.Windows.Controls.TextBox>les gestionnaires d’événements à un .  
  
 [!code-xaml[keyboardsample#KeyboardSampleXAMLHandlerHookup](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyboardSample/CSharp/Window1.xaml#keyboardsamplexamlhandlerhookup)]  
  
 Lorsque <xref:System.Windows.Controls.TextBox> le clavier obtient <xref:System.Windows.Controls.Control.Background%2A> la mise <xref:System.Windows.Controls.TextBox> au <xref:System.Windows.Media.Brushes.LightBlue%2A>point, la propriété de la est changée pour .  
  
 [!code-csharp[keyboardsample#KeyboardSampleGotFocus](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyboardSample/CSharp/Window1.xaml.cs#keyboardsamplegotfocus)]
 [!code-vb[keyboardsample#KeyboardSampleGotFocus](~/samples/snippets/visualbasic/VS_Snippets_Wpf/KeyboardSample/visualbasic/window1.xaml.vb#keyboardsamplegotfocus)]  
  
 Lorsque <xref:System.Windows.Controls.TextBox> le clavier perd <xref:System.Windows.Controls.Control.Background%2A> la <xref:System.Windows.Controls.TextBox> mise au point, la propriété de la est changée en blanc.  
  
 [!code-csharp[keyboardsample#KeyboardSampleLostFocus](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyboardSample/CSharp/Window1.xaml.cs#keyboardsamplelostfocus)]
 [!code-vb[keyboardsample#KeyboardSampleLostFocus](~/samples/snippets/visualbasic/VS_Snippets_Wpf/KeyboardSample/visualbasic/window1.xaml.vb#keyboardsamplelostfocus)]  
  
 Les événements liés à <xref:System.Windows.UIElement.GotFocus> <xref:System.Windows.UIElement.LostFocus>l’accent logique sont et .  Ces événements sont <xref:System.Windows.Input.FocusManager> définis sur les <xref:System.Windows.Input.FocusManager> événements ci-joints, mais le ne révèle pas les emballages d’événements CLR.  <xref:System.Windows.UIElement>et <xref:System.Windows.ContentElement> exposer ces événements plus commodément.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Input.FocusManager>
- <xref:System.Windows.UIElement>
- <xref:System.Windows.ContentElement>
- [Vue d’ensemble des entrées](input-overview.md)
- [Vue d’ensemble des éléments de base](base-elements-overview.md)
