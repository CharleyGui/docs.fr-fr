---
title: Vue d'ensemble de Menu
ms.date: 03/30/2017
helpviewer_keywords:
- Menu control [WPF]
- controls [WPF], Menu
ms.assetid: 67df6de5-db96-4c71-b752-af90729a6537
ms.openlocfilehash: 3d5cfba0734e684349f7d73b7242f4b69089b94d
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77124648"
---
# <a name="menu-overview"></a>Vue d'ensemble de Menu
La classe <xref:System.Windows.Controls.Menu> vous permet d’organiser les éléments associés aux commandes et aux gestionnaires d’événements dans un ordre hiérarchique. Chaque élément <xref:System.Windows.Controls.Menu> contient une collection d’éléments <xref:System.Windows.Controls.MenuItem>.  

<a name="menu_control"></a>   
## <a name="menu-control"></a>Contrôle Menu  
 Le contrôle <xref:System.Windows.Controls.Menu> présente une liste d’éléments qui spécifient des commandes ou des options pour une application. En général, le fait de cliquer sur un <xref:System.Windows.Controls.MenuItem> ouvre un sous-menu ou provoque l’exécution d’une commande par une application.  
  
<a name="creating_menus"></a>   
## <a name="creating-menus"></a>Création de menus  
 L’exemple suivant crée une <xref:System.Windows.Controls.Menu> pour manipuler du texte dans une <xref:System.Windows.Controls.TextBox>. Le <xref:System.Windows.Controls.Menu> contient des objets <xref:System.Windows.Controls.MenuItem> qui utilisent les propriétés <xref:System.Windows.Controls.MenuItem.Command%2A>, <xref:System.Windows.Controls.MenuItem.IsCheckable%2A>et <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> et les événements <xref:System.Windows.Controls.MenuItem.Checked>, <xref:System.Windows.Controls.MenuItem.Unchecked>et <xref:System.Windows.Controls.MenuItem.Click>.  
  
 [!code-xaml[MenuItemCommandsAndEvents#1](~/samples/snippets/csharp/VS_Snippets_Wpf/MenuItemCommandsAndEvents/CSharp/Window1.xaml#1)]  
  
 [!code-csharp[MenuItemCommandsAndEvents#2](~/samples/snippets/csharp/VS_Snippets_Wpf/MenuItemCommandsAndEvents/CSharp/Window1.xaml.cs#2)]
 [!code-vb[MenuItemCommandsAndEvents#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MenuItemCommandsAndEvents/VisualBasic/Window1.xaml.vb#2)]  
  
<a name="menus_with_shortcutkeys"></a>   
## <a name="menuitems-with-keyboard-shortcuts"></a>MenuItems avec raccourcis clavier  
 Les raccourcis clavier sont des combinaisons de caractères qui peuvent être entrées à l’aide du clavier pour appeler des commandes <xref:System.Windows.Controls.Menu>. Par exemple, le raccourci clavier de la **copie** est CTRL+C. Il existe deux propriétés à utiliser avec les raccourcis clavier et les éléments de menu :<xref:System.Windows.Controls.MenuItem.InputGestureText%2A> ou <xref:System.Windows.Controls.MenuItem.Command%2A>.  
  
<a name="menus_inputgesturetext"></a>   
### <a name="inputgesturetext"></a>InputGestureText  
 L’exemple suivant montre comment utiliser la propriété <xref:System.Windows.Controls.MenuItem.InputGestureText%2A> pour assigner un texte de raccourci clavier à des contrôles <xref:System.Windows.Controls.MenuItem>. Cette opération ne fait que placer le raccourci clavier dans l’élément de menu.  Elle n’associe pas la commande à l' <xref:System.Windows.Controls.MenuItem>. L’application doit gérer l’entrée de l’utilisateur pour exécuter l’action.  
  
 [!code-xaml[MenuEvent#6](~/samples/snippets/csharp/VS_Snippets_Wpf/MenuEvent/CSharp/Pane1.xaml#6)]  
  
<a name="menus_commands"></a>   
### <a name="command"></a>Commande  
 L’exemple suivant montre comment utiliser la propriété <xref:System.Windows.Controls.MenuItem.Command%2A> pour associer les commandes **ouvrir** et **Enregistrer** à des contrôles <xref:System.Windows.Controls.MenuItem>. Non seulement la propriété Command associe une commande à un <xref:System.Windows.Controls.MenuItem>, mais elle fournit également le texte de mouvement d’entrée à utiliser comme raccourci.  
  
 [!code-xaml[MenuEvent#8](~/samples/snippets/csharp/VS_Snippets_Wpf/MenuEvent/CSharp/Pane1.xaml#8)]  
  
 La classe <xref:System.Windows.Controls.MenuItem> a également une propriété <xref:System.Windows.Controls.MenuItem.CommandTarget%2A>, qui spécifie l’élément où la commande se produit. Si <xref:System.Windows.Controls.MenuItem.CommandTarget%2A> n’est pas défini, l’élément qui a le focus clavier reçoit la commande. Pour plus d’informations sur les commandes, consultez [Vue d’ensemble des commandes](../advanced/commanding-overview.md).  
  
<a name="menu_styling"></a>   
## <a name="menu-styling"></a>Styles de menu  
 Avec le style de contrôle, vous pouvez modifier radicalement l’apparence et le comportement des contrôles <xref:System.Windows.Controls.Menu> sans avoir à écrire de contrôle personnalisé. Outre la définition des propriétés visuelles, vous pouvez également appliquer une <xref:System.Windows.Style> à des parties individuelles d’un contrôle, modifier le comportement des parties du contrôle par le biais des propriétés, ou ajouter des parties supplémentaires ou modifier la disposition d’un contrôle. Les exemples suivants illustrent plusieurs façons d’ajouter un <xref:System.Windows.Style> à un contrôle <xref:System.Windows.Controls.Menu>.  
  
 Le premier exemple de code définit une <xref:System.Windows.Style> appelée `Simple` qui montre comment utiliser les paramètres système actuels dans votre style. Le code assigne la couleur du pinceau `MenuHighlightBrush` comme couleur d’arrière-plan du menu et celle du pinceau `MenuTextBrush` comme couleur de premier plan du menu. Notez que vous utilisez des clés de ressource pour assigner les pinceaux.  
  
 [!code-xaml[MenuStylesSnippet#1](~/samples/snippets/csharp/VS_Snippets_Wpf/MenuStylesSnippet/CS/app.xaml#1)]  
  
 L’exemple suivant utilise <xref:System.Windows.Trigger> éléments qui vous permettent de modifier l’apparence d’un <xref:System.Windows.Controls.MenuItem> en réponse à des événements qui se produisent sur le <xref:System.Windows.Controls.Menu>. Lorsque vous déplacez la souris sur le <xref:System.Windows.Controls.Menu>, la couleur de premier plan et les caractéristiques de police des éléments de menu changent.  
  
 [!code-xaml[MenuStylesSnippet#2](~/samples/snippets/csharp/VS_Snippets_Wpf/MenuStylesSnippet/CS/app.xaml#2)]  
  
## <a name="see-also"></a>Voir aussi

- [Exemple de galerie de contrôles WPF](https://github.com/Microsoft/WPF-Samples/tree/master/Getting%20Started/ControlsAndLayout)
