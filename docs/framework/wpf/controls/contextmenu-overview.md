---
title: Vue d'ensemble de ContextMenu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], ContextMenu
- ContextMenu controls [WPF], about ContextMenu controls
ms.assetid: 16909c42-799a-4561-91e0-7d69dcfeea91
ms.openlocfilehash: 4d2d8db0f614b5240705146dbe91432b96b46dd6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185918"
---
# <a name="contextmenu-overview"></a>Vue d'ensemble de ContextMenu
La <xref:System.Windows.Controls.ContextMenu> classe représente l’élément qui expose la <xref:System.Windows.Controls.Menu>fonctionnalité en utilisant un contexte spécifique . Typiquement, un utilisateur <xref:System.Windows.Controls.ContextMenu> expose [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] le dans le en cliquant sur le bouton de la souris. Ce sujet introduit <xref:System.Windows.Controls.ContextMenu> l’élément et fournit des [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] exemples de la façon de l’utiliser et de coder.  

<a name="contextmenu_control"></a>
## <a name="contextmenu-control"></a>Contrôle ContextMenu  
 A <xref:System.Windows.Controls.ContextMenu> est attaché à un contrôle spécifique. L’élément <xref:System.Windows.Controls.ContextMenu> vous permet de présenter aux utilisateurs une liste d’éléments qui spécifient des commandes ou des options qui sont associées à un contrôle particulier, par exemple, un <xref:System.Windows.Controls.Button>. Les utilisateurs cliquent avec le bouton droit sur le contrôle pour afficher le menu. Typiquement, en <xref:System.Windows.Controls.MenuItem> cliquant sur un ouvre un sous-présage ou provoque une application pour effectuer une commande.  
  
<a name="creating_contextmenus"></a>
## <a name="creating-contextmenus"></a>Création d’un ContextMenu  
 Les exemples suivants montrent <xref:System.Windows.Controls.ContextMenu> comment créer un sous-genre avec. Les <xref:System.Windows.Controls.ContextMenu> commandes sont fixées aux commandes de boutons.  
  
 [!code-xaml[ContextMenu#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ContextMenu/CSharp/Pane1.xaml#1)]  
  
 [!code-csharp[ContextMenu#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ContextMenu/CSharp/Pane1.xaml.cs#2)]
 [!code-vb[ContextMenu#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ContextMenu/VisualBasic/Pane1.xaml.vb#2)]  
  
<a name="applying_styles_to_contextmenu"></a>
## <a name="applying-styles-to-a-contextmenu"></a>Application de styles à un ContextMenu  
 En utilisant <xref:System.Windows.Style>un contrôle , vous pouvez changer <xref:System.Windows.Controls.ContextMenu> radicalement l’apparence et le comportement d’un sans écrire un contrôle personnalisé. Outre la définition de propriétés visuelles, vous pouvez appliquer des styles aux parties d’un contrôle. Par exemple, vous pouvez modifier le comportement des parties du contrôle en utilisant des propriétés, ou vous pouvez ajouter des pièces à, ou modifier la disposition de, a <xref:System.Windows.Controls.ContextMenu>. Les exemples suivants montrent plusieurs <xref:System.Windows.Controls.ContextMenu> façons d’ajouter des styles aux contrôles.  
  
 Le premier exemple définit un style appelé `SimpleSysResources`, qui explique comment utiliser les paramètres système actuels dans votre style. L’exemple <xref:System.Windows.SystemColors.MenuHighlightBrushKey%2A> attribue <xref:System.Windows.Controls.Control.Background%2A> comme <xref:System.Windows.SystemColors.MenuTextBrushKey%2A> la <xref:System.Windows.Controls.Control.Foreground%2A> couleur et <xref:System.Windows.Controls.ContextMenu>comme la couleur de la .  
  
```xaml  
<Style x:Key="SimpleSysResources" TargetType="{x:Type MenuItem}">  
  <Setter Property = "Background" Value=
    "{DynamicResource {x:Static SystemColors.MenuHighlightBrushKey}}"/>  
  <Setter Property = "Foreground" Value=
    "{DynamicResource {x:Static SystemColors.MenuTextBrushKey}}"/>  
</Style>  
```  
  
 L’exemple suivant <xref:System.Windows.Trigger> utilise l’élément <xref:System.Windows.Controls.Menu> pour changer l’apparence d’une réponse aux événements qui sont soulevés sur le <xref:System.Windows.Controls.ContextMenu>. Lorsqu’un utilisateur déplace la souris sur <xref:System.Windows.Controls.ContextMenu> le menu, l’apparence des éléments change.  
  
```xaml  
<Style x:Key="Triggers" TargetType="{x:Type MenuItem}">  
  <Style.Triggers>  
    <Trigger Property="MenuItem.IsMouseOver" Value="true">  
      <Setter Property = "FontSize" Value="16"/>  
      <Setter Property = "FontStyle" Value="Italic"/>  
      <Setter Property = "Foreground" Value="Red"/>  
    </Trigger>  
  </Style.Triggers>  
</Style>  
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Controls.ContextMenu>
- <xref:System.Windows.Style>
- <xref:System.Windows.Controls.Menu>
- <xref:System.Windows.Controls.MenuItem>
- [Contextmenu](contextmenu.md)
- [Styles et modèles ContextMenu](contextmenu-styles-and-templates.md)
- [Exemple de galerie de contrôles WPF](https://github.com/Microsoft/WPF-Samples/tree/master/Getting%20Started/ControlsAndLayout)
