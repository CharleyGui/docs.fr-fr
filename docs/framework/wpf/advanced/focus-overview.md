---
title: Vue d'ensemble du focus
description: 'En savoir plus sur les deux principaux concepts de Windows Presentation Foundation qui concernent le focus : le focus clavier et le focus logique.'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- applications [WPF], focus
- focus in applications [WPF]
ms.assetid: 0230c4eb-0c8a-462b-ac4b-ae3e511659f4
ms.openlocfilehash: 71aeb577cccd2c3b16df1c5a3cb772dd1f5479e2
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165104"
---
# <a name="focus-overview"></a>Vue d'ensemble du focus
Dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], il existe deux concepts principaux associés au focus : le focus clavier et le focus logique.  Le focus clavier fait référence à l’élément qui reçoit une entrée au clavier, tandis que le focus logique fait référence à l’élément d’une portée de focus qui a le focus.  Ces concepts sont présentés en détail dans cette vue d’ensemble.  Il est important de bien comprendre les différences entre ces concepts lors de la création d’applications complexes qui comportent plusieurs régions où le focus peut être obtenu.  
  
 Les classes principales qui participent à la gestion du focus sont la <xref:System.Windows.Input.Keyboard> classe, la <xref:System.Windows.Input.FocusManager> classe et les classes d’éléments de base, telles que <xref:System.Windows.UIElement> et <xref:System.Windows.ContentElement> .  Pour plus d’informations sur les éléments de base, consultez [Vue d’ensemble des éléments de base](base-elements-overview.md).  
  
 La <xref:System.Windows.Input.Keyboard> classe s’intéresse principalement au focus clavier et le <xref:System.Windows.Input.FocusManager> s’intéresse principalement au focus logique, mais il ne s’agit pas d’une distinction absolue.  En effet, un élément qui a le focus clavier possède également le focus logique, tandis qu’un élément qui a le focus logique ne possède pas nécessairement le focus clavier.  Cela est évident lorsque vous utilisez la <xref:System.Windows.Input.Keyboard> classe pour définir l’élément qui a le focus clavier, pour cela définit également le focus logique sur l’élément.  

<a name="Keyboard_Focus"></a>
## <a name="keyboard-focus"></a>Focus clavier  
 Le focus clavier fait référence à l’élément qui reçoit l’entrée au clavier.  Un seul élément de l’ordinateur peut avoir le focus clavier.  Dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] , l’élément qui a le focus clavier aura la <xref:System.Windows.IInputElement.IsKeyboardFocused%2A> valeur `true` .  La propriété statique <xref:System.Windows.Input.Keyboard.FocusedElement%2A> de la <xref:System.Windows.Input.Keyboard> classe obtient l’élément qui a actuellement le focus clavier.  
  
 Pour qu’un élément obtienne le focus clavier, les <xref:System.Windows.UIElement.Focusable%2A> <xref:System.Windows.UIElement.IsVisible%2A> Propriétés et sur les éléments de base doivent avoir la valeur `true` .  Certaines classes, telles que la <xref:System.Windows.Controls.Panel> classe de base, ont la <xref:System.Windows.UIElement.Focusable%2A> valeur `false` par défaut ; par conséquent, vous devez définir <xref:System.Windows.UIElement.Focusable%2A> sur `true` si vous souhaitez que ce type d’élément soit en mesure d’obtenir le focus clavier.  
  
 Le focus clavier peut être obtenu par interaction de l’utilisateur avec l’[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] (tabulation vers un élément ou clic de souris sur certains éléments, par exemple).  Le focus clavier peut également être obtenu par programmation à l’aide de la <xref:System.Windows.Input.Keyboard.Focus%2A> méthode sur la <xref:System.Windows.Input.Keyboard> classe.  La <xref:System.Windows.Input.Keyboard.Focus%2A> méthode tente d’attribuer le focus clavier à l’élément spécifié.  L’élément retourné correspond à l’élément qui a le focus clavier. Il peut s’agir d’un autre élément que celui demandé si l’objet de focus précédent ou nouveau bloque la demande.  
  
 L’exemple suivant utilise la <xref:System.Windows.Input.Keyboard.Focus%2A> méthode pour définir le focus clavier sur un <xref:System.Windows.Controls.Button> .  
  
 [!code-csharp[focussample#FocusSampleSetFocus](~/samples/snippets/csharp/VS_Snippets_Wpf/FocusSample/CSharp/Window1.xaml.cs#focussamplesetfocus)]
 [!code-vb[focussample#FocusSampleSetFocus](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSample/visualbasic/window1.xaml.vb#focussamplesetfocus)]  
  
 La <xref:System.Windows.UIElement.IsKeyboardFocused%2A> propriété sur les classes d’éléments de base obtient une valeur indiquant si l’élément a le focus clavier.  La <xref:System.Windows.UIElement.IsKeyboardFocusWithin%2A> propriété sur les classes d’éléments de base obtient une valeur indiquant si l’élément ou l’un de ses éléments enfants visuels a le focus clavier.  
  
 Lors du paramétrage du focus initial au démarrage de l’application, l’élément devant recevoir le focus doit se trouver dans l’arborescence d’éléments visuels de la fenêtre initiale chargée par l’application, et l’élément doit avoir et avoir la <xref:System.Windows.UIElement.Focusable%2A> <xref:System.Windows.UIElement.IsVisible%2A> valeur `true` .  L’emplacement recommandé pour définir le focus initial se trouve dans le <xref:System.Windows.FrameworkElement.Loaded> Gestionnaire d’événements.  Un <xref:System.Windows.Threading.Dispatcher> rappel peut également être utilisé en appelant <xref:System.Windows.Threading.Dispatcher.Invoke%2A> ou <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> .  
  
<a name="Logical_Focus"></a>
## <a name="logical-focus"></a>Focus logique  
 Le focus logique fait référence à <xref:System.Windows.Input.FocusManager.FocusedElement%2A?displayProperty=nameWithType> dans une portée de focus.  Une portée de focus est un élément qui effectue le suivi du <xref:System.Windows.Input.FocusManager.FocusedElement%2A> dans sa portée.  Quand le focus clavier quitte une portée de focus, l’élément ayant le focus perd le focus clavier, mais conserve le focus logique.  Quand le focus clavier revient dans la portée de focus, l’élément ayant le focus obtient le focus clavier.  Cela permet au focus clavier de changer entre des portées de focus et de s’assurer que l’élément ayant le focus dans la portée de focus retrouve le focus clavier quand le focus revient dans la portée de focus.  
  
 Plusieurs éléments d’une application peuvent avoir le focus logique, mais un seul élément peut avoir le focus logique dans une portée de focus donnée.  
  
 Un élément ayant le focus clavier a également le focus logique pour la portée de focus à laquelle il appartient.  
  
 Un élément peut être converti en portée de focus dans [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] en affectant <xref:System.Windows.Input.FocusManager> à la propriété jointe la valeur <xref:System.Windows.Input.FocusManager.IsFocusScope%2A> `true` .  Dans le code, un élément peut être converti en portée de focus en appelant <xref:System.Windows.Input.FocusManager.SetIsFocusScope%2A> .  
  
 L’exemple suivant rend un <xref:System.Windows.Controls.StackPanel> en portée de focus en définissant la <xref:System.Windows.Input.FocusManager.IsFocusScope%2A> propriété jointe.  
  
 [!code-xaml[MarkupSnippets#MarkupIsFocusScopeXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/MarkupSnippets/CSharp/Window1.xaml#markupisfocusscopexaml)]  
  
 [!code-csharp[FocusSnippets#FocusSetIsFocusScope](~/samples/snippets/csharp/VS_Snippets_Wpf/FocusSnippets/CSharp/Window1.xaml.cs#focussetisfocusscope)]
 [!code-vb[FocusSnippets#FocusSetIsFocusScope](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSnippets/visualbasic/window1.xaml.vb#focussetisfocusscope)]  
  
 <xref:System.Windows.Input.FocusManager.GetFocusScope%2A>retourne la portée de focus pour l’élément spécifié.  
  
 Les classes dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] lesquelles sont des portées de focus par défaut sont <xref:System.Windows.Window> ,, <xref:System.Windows.Controls.MenuItem> <xref:System.Windows.Controls.ToolBar> et <xref:System.Windows.Controls.ContextMenu> .  
  
 <xref:System.Windows.Input.FocusManager.GetFocusedElement%2A>Obtient l’élément ayant le focus pour la portée de focus spécifiée.  <xref:System.Windows.Input.FocusManager.SetFocusedElement%2A>définit l’élément ayant le focus dans la portée de focus spécifiée.  <xref:System.Windows.Input.FocusManager.SetFocusedElement%2A>est généralement utilisé pour définir l’élément ayant le focus initial.  
  
 L’exemple suivant définit l’élément ayant le focus dans une portée de focus et obtient l’élément ayant le focus d’une portée de focus.  
  
 [!code-csharp[FocusSnippets#FocusGetSetFocusedElement](~/samples/snippets/csharp/VS_Snippets_Wpf/FocusSnippets/CSharp/Window1.xaml.cs#focusgetsetfocusedelement)]
 [!code-vb[FocusSnippets#FocusGetSetFocusedElement](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSnippets/visualbasic/window1.xaml.vb#focusgetsetfocusedelement)]  
  
<a name="Keyboard_Navigation"></a>
## <a name="keyboard-navigation"></a>Navigation au clavier  
 La <xref:System.Windows.Input.KeyboardNavigation> classe est chargée d’implémenter la navigation par défaut du focus clavier lorsque l’une des touches de navigation est enfoncée.  Les touches de navigation sont les suivantes : TAB, MAJ+TAB, CTRL+TAB, CTRL+MAJ+TAB, FLÈCHE HAUT, FLÈCHE BAS, FLÈCHE GAUCHE et FLÈCHE DROITE.  
  
 Le comportement de navigation d’un conteneur de navigation peut être modifié en définissant les propriétés jointes <xref:System.Windows.Input.KeyboardNavigation> <xref:System.Windows.Input.KeyboardNavigation.TabNavigation%2A> , <xref:System.Windows.Input.KeyboardNavigation.ControlTabNavigation%2A> et <xref:System.Windows.Input.KeyboardNavigation.DirectionalNavigation%2A> .  Ces propriétés sont de type <xref:System.Windows.Input.KeyboardNavigationMode> et les valeurs possibles sont <xref:System.Windows.Input.KeyboardNavigationMode.Continue> , <xref:System.Windows.Input.KeyboardNavigationMode.Local> ,,, <xref:System.Windows.Input.KeyboardNavigationMode.Contained> <xref:System.Windows.Input.KeyboardNavigationMode.Cycle> <xref:System.Windows.Input.KeyboardNavigationMode.Once> et <xref:System.Windows.Input.KeyboardNavigationMode.None> .  La valeur par défaut est <xref:System.Windows.Input.KeyboardNavigationMode.Continue> , ce qui signifie que l’élément n’est pas un conteneur de navigation.  
  
 L’exemple suivant crée un <xref:System.Windows.Controls.Menu> avec un certain nombre d' <xref:System.Windows.Controls.MenuItem> objets.  La <xref:System.Windows.Input.KeyboardNavigation.TabNavigation%2A> propriété jointe a la valeur <xref:System.Windows.Input.KeyboardNavigationMode.Cycle> sur <xref:System.Windows.Controls.Menu> .  Lorsque le focus est modifié à l’aide de la touche TAB dans le <xref:System.Windows.Controls.Menu> , le focus se déplace à partir de chaque élément et, lorsque le dernier élément est atteint, le focus retourne au premier élément.  
  
 [!code-xaml[MarkupSnippets#MarkupKeyboardNavigationTabNavigationXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/MarkupSnippets/CSharp/Window1.xaml#markupkeyboardnavigationtabnavigationxaml)]  
  
 [!code-csharp[MarkupSnippets#MarkupKeyboardNavigationTabNavigationCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/MarkupSnippets/CSharp/Window1.xaml.cs#markupkeyboardnavigationtabnavigationcode)]
 [!code-vb[MarkupSnippets#MarkupKeyboardNavigationTabNavigationCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MarkupSnippets/visualbasic/window1.xaml.vb#markupkeyboardnavigationtabnavigationcode)]  
  
<a name="Manipulating_Focus_Programmatically"></a>
## <a name="navigating-focus-programmatically"></a>Navigation du focus par programmation  
 L’API supplémentaire pour travailler avec le focus est <xref:System.Windows.UIElement.MoveFocus%2A> et <xref:System.Windows.UIElement.PredictFocus%2A> .  
  
 <xref:System.Windows.FrameworkElement.MoveFocus%2A>modifie le focus sur l’élément suivant dans l’application.  Un <xref:System.Windows.Input.TraversalRequest> est utilisé pour spécifier la direction.   Le <xref:System.Windows.Input.FocusNavigationDirection> passé à <xref:System.Windows.UIElement.MoveFocus%2A> spécifie le focus des directions différentes peut être déplacé, par exemple <xref:System.Windows.Input.FocusNavigationDirection.First> , <xref:System.Windows.Input.FocusNavigationDirection.Last> <xref:System.Windows.Input.FocusNavigationDirection.Up> et <xref:System.Windows.Input.FocusNavigationDirection.Down> .  
  
 L’exemple suivant utilise <xref:System.Windows.FrameworkElement.MoveFocus%2A> pour modifier l’élément ayant le focus.  
  
 [!code-csharp[focussample#FocusSampleMoveFocus](~/samples/snippets/csharp/VS_Snippets_Wpf/FocusSample/CSharp/Window1.xaml.cs#focussamplemovefocus)]
 [!code-vb[focussample#FocusSampleMoveFocus](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSample/visualbasic/window1.xaml.vb#focussamplemovefocus)]  
  
 <xref:System.Windows.FrameworkElement.PredictFocus%2A>retourne l’objet qui recevrait le focus si le focus devait être modifié.  Actuellement, seuls,, <xref:System.Windows.Input.FocusNavigationDirection.Up> <xref:System.Windows.Input.FocusNavigationDirection.Down> <xref:System.Windows.Input.FocusNavigationDirection.Left> et <xref:System.Windows.Input.FocusNavigationDirection.Right> sont pris en charge par <xref:System.Windows.FrameworkElement.PredictFocus%2A> .  
  
<a name="Focus_Events"></a>
## <a name="focus-events"></a>Événements de focus  
 Les événements liés au focus clavier sont <xref:System.Windows.Input.Keyboard.PreviewGotKeyboardFocus> , <xref:System.Windows.Input.Keyboard.GotKeyboardFocus> et <xref:System.Windows.Input.Keyboard.PreviewLostKeyboardFocus> <xref:System.Windows.Input.Keyboard.LostKeyboardFocus> .  Les événements sont définis en tant qu’événements attachés sur la <xref:System.Windows.Input.Keyboard> classe, mais sont plus facilement accessibles en tant qu’événements routés équivalents sur les classes d’éléments de base.  Pour plus d’informations sur les événements, consultez [Vue d’ensemble des événements routés](routed-events-overview.md).  
  
 <xref:System.Windows.Input.Keyboard.GotKeyboardFocus>est déclenché lorsque l’élément obtient le focus clavier.  <xref:System.Windows.Input.Keyboard.LostKeyboardFocus>est déclenché lorsque l’élément perd le focus clavier.  Si l' <xref:System.Windows.Input.Keyboard.PreviewGotKeyboardFocus> événement ou l' <xref:System.Windows.Input.Keyboard.PreviewLostKeyboardFocusEvent> événement est géré et <xref:System.Windows.RoutedEventArgs.Handled%2A> a la valeur `true` , le focus ne change pas.  
  
 L’exemple suivant attache <xref:System.Windows.UIElement.GotKeyboardFocus> des <xref:System.Windows.UIElement.LostKeyboardFocus> gestionnaires d’événements et à un <xref:System.Windows.Controls.TextBox> .  
  
 [!code-xaml[keyboardsample#KeyboardSampleXAMLHandlerHookup](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyboardSample/CSharp/Window1.xaml#keyboardsamplexamlhandlerhookup)]  
  
 Lorsque <xref:System.Windows.Controls.TextBox> obtient le focus clavier, la <xref:System.Windows.Controls.Control.Background%2A> propriété du <xref:System.Windows.Controls.TextBox> est remplacée par <xref:System.Windows.Media.Brushes.LightBlue%2A> .  
  
 [!code-csharp[keyboardsample#KeyboardSampleGotFocus](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyboardSample/CSharp/Window1.xaml.cs#keyboardsamplegotfocus)]
 [!code-vb[keyboardsample#KeyboardSampleGotFocus](~/samples/snippets/visualbasic/VS_Snippets_Wpf/KeyboardSample/visualbasic/window1.xaml.vb#keyboardsamplegotfocus)]  
  
 Lorsque le <xref:System.Windows.Controls.TextBox> perd le focus clavier, la <xref:System.Windows.Controls.Control.Background%2A> propriété du <xref:System.Windows.Controls.TextBox> est rétablie en blanc.  
  
 [!code-csharp[keyboardsample#KeyboardSampleLostFocus](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyboardSample/CSharp/Window1.xaml.cs#keyboardsamplelostfocus)]
 [!code-vb[keyboardsample#KeyboardSampleLostFocus](~/samples/snippets/visualbasic/VS_Snippets_Wpf/KeyboardSample/visualbasic/window1.xaml.vb#keyboardsamplelostfocus)]  
  
 Les événements liés au focus logique sont <xref:System.Windows.UIElement.GotFocus> et <xref:System.Windows.UIElement.LostFocus> .  Ces événements sont définis sur les <xref:System.Windows.Input.FocusManager> événements As attachés, mais le <xref:System.Windows.Input.FocusManager> n’expose pas les wrappers d’événements CLR.  <xref:System.Windows.UIElement>et <xref:System.Windows.ContentElement> exposent ces événements plus facilement.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Input.FocusManager>
- <xref:System.Windows.UIElement>
- <xref:System.Windows.ContentElement>
- [Vue d'ensemble des entrées](input-overview.md)
- [Vue d'ensemble des éléments de base](base-elements-overview.md)
