---
title: Vue d'ensemble de Menu
ms.date: 03/30/2017
helpviewer_keywords:
- Menu control [WPF]
- controls [WPF], Menu
ms.assetid: 67df6de5-db96-4c71-b752-af90729a6537
ms.openlocfilehash: 53bc8f10e61b6e4e9e1f3b9a484340d9e2ec2a85
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186970"
---
# <a name="menu-overview"></a>Vue d'ensemble de Menu
La <xref:System.Windows.Controls.Menu> classe vous permet d’organiser des éléments associés aux commandes et aux gestionnaires d’événements dans un ordre hiérarchique. Chaque <xref:System.Windows.Controls.Menu> élément contient <xref:System.Windows.Controls.MenuItem> une collection d’éléments.  

<a name="menu_control"></a>
## <a name="menu-control"></a>Contrôle Menu  
 Le <xref:System.Windows.Controls.Menu> contrôle présente une liste d’éléments qui spécifient les commandes ou les options pour une application. Typiquement, en <xref:System.Windows.Controls.MenuItem> cliquant sur un ouvre un sous-présage ou provoque une application pour effectuer une commande.  
  
<a name="creating_menus"></a>
## <a name="creating-menus"></a>Création de menus  
 L’exemple suivant <xref:System.Windows.Controls.Menu> crée un <xref:System.Windows.Controls.TextBox>texte à manipuler dans un . Les <xref:System.Windows.Controls.Menu> <xref:System.Windows.Controls.MenuItem> objets contient <xref:System.Windows.Controls.MenuItem.Command%2A>qui <xref:System.Windows.Controls.MenuItem.IsCheckable%2A>utilisent <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> le <xref:System.Windows.Controls.MenuItem.Checked>, <xref:System.Windows.Controls.MenuItem.Unchecked>, <xref:System.Windows.Controls.MenuItem.Click> et les propriétés et le , et les événements.  
  
 [!code-xaml[MenuItemCommandsAndEvents#1](~/samples/snippets/csharp/VS_Snippets_Wpf/MenuItemCommandsAndEvents/CSharp/Window1.xaml#1)]  
  
 [!code-csharp[MenuItemCommandsAndEvents#2](~/samples/snippets/csharp/VS_Snippets_Wpf/MenuItemCommandsAndEvents/CSharp/Window1.xaml.cs#2)]
 [!code-vb[MenuItemCommandsAndEvents#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MenuItemCommandsAndEvents/VisualBasic/Window1.xaml.vb#2)]  
  
<a name="menus_with_shortcutkeys"></a>
## <a name="menuitems-with-keyboard-shortcuts"></a>MenuItems avec raccourcis clavier  
 Les raccourcis clavier sont des combinaisons de personnages <xref:System.Windows.Controls.Menu> qui peuvent être saisies avec le clavier pour invoquer des commandes. Par exemple, le raccourci clavier de la **copie** est CTRL+C. Il ya deux propriétés à utiliser avec<xref:System.Windows.Controls.MenuItem.InputGestureText%2A> des <xref:System.Windows.Controls.MenuItem.Command%2A>raccourcis clavier et des éléments de menu - ou .  
  
<a name="menus_inputgesturetext"></a>
### <a name="inputgesturetext"></a>InputGestureText  
 L’exemple suivant montre <xref:System.Windows.Controls.MenuItem.InputGestureText%2A> comment utiliser la propriété <xref:System.Windows.Controls.MenuItem> pour attribuer du texte raccourci clavier aux contrôles. Cette opération ne fait que placer le raccourci clavier dans l’élément de menu.  Il n’associe pas <xref:System.Windows.Controls.MenuItem>la commande avec le . L’application doit gérer l’entrée de l’utilisateur pour exécuter l’action.  
  
 [!code-xaml[MenuEvent#6](~/samples/snippets/csharp/VS_Snippets_Wpf/MenuEvent/CSharp/Pane1.xaml#6)]  
  
<a name="menus_commands"></a>
### <a name="command"></a>Commande  
 L’exemple suivant montre <xref:System.Windows.Controls.MenuItem.Command%2A> comment utiliser la propriété pour <xref:System.Windows.Controls.MenuItem> associer les commandes **Open** et **Save** avec des commandes. Non seulement la propriété de commande <xref:System.Windows.Controls.MenuItem>associe une commande à un, mais elle fournit également le texte de geste d’entrée à utiliser comme un raccourci.  
  
 [!code-xaml[MenuEvent#8](~/samples/snippets/csharp/VS_Snippets_Wpf/MenuEvent/CSharp/Pane1.xaml#8)]  
  
 La <xref:System.Windows.Controls.MenuItem> classe a <xref:System.Windows.Controls.MenuItem.CommandTarget%2A> également une propriété, qui spécifie l’élément où la commande se produit. Si <xref:System.Windows.Controls.MenuItem.CommandTarget%2A> ce n’est pas réglé, l’élément qui a la mise au point clavier reçoit la commande. Pour plus d’informations sur les commandes, consultez [Vue d’ensemble des commandes](../advanced/commanding-overview.md).  
  
<a name="menu_styling"></a>
## <a name="menu-styling"></a>Styles de menu  
 Avec le style de contrôle, vous pouvez <xref:System.Windows.Controls.Menu> changer radicalement l’apparence et le comportement des contrôles sans avoir à écrire un contrôle personnalisé. En plus de définir des propriétés <xref:System.Windows.Style> visuelles, vous pouvez également appliquer une à des parties individuelles d’un contrôle, modifier le comportement des parties du contrôle à travers les propriétés, ou ajouter des pièces supplémentaires ou modifier la disposition d’un contrôle. Les exemples suivants démontrent <xref:System.Windows.Style> plusieurs <xref:System.Windows.Controls.Menu> façons d’ajouter un contrôle.  
  
 Le premier exemple de <xref:System.Windows.Style> `Simple` code définit un appelé qui montre comment utiliser les paramètres du système actuel dans votre style. Le code assigne la couleur du pinceau `MenuHighlightBrush` comme couleur d’arrière-plan du menu et celle du pinceau `MenuTextBrush` comme couleur de premier plan du menu. Notez que vous utilisez des clés de ressource pour assigner les pinceaux.  
  
 [!code-xaml[MenuStylesSnippet#1](~/samples/snippets/csharp/VS_Snippets_Wpf/MenuStylesSnippet/CS/app.xaml#1)]  
  
 L’échantillon <xref:System.Windows.Trigger> suivant utilise des éléments qui <xref:System.Windows.Controls.MenuItem> vous permettent de modifier <xref:System.Windows.Controls.Menu>l’apparence d’une réponse aux événements qui se produisent sur le . Lorsque vous déplacez <xref:System.Windows.Controls.Menu>la souris sur la , la couleur au premier plan et les caractéristiques de police des éléments de menu changent.  
  
 [!code-xaml[MenuStylesSnippet#2](~/samples/snippets/csharp/VS_Snippets_Wpf/MenuStylesSnippet/CS/app.xaml#2)]  
  
## <a name="see-also"></a>Voir aussi

- [Exemple de galerie de contrôles WPF](https://github.com/Microsoft/WPF-Samples/tree/master/Getting%20Started/ControlsAndLayout)
