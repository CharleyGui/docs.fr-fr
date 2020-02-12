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
ms.openlocfilehash: b973d47711632f4c0fe56f042545598272c79d2d
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77124362"
---
# <a name="contextmenu-overview"></a>Vue d'ensemble de ContextMenu
La classe <xref:System.Windows.Controls.ContextMenu> représente l’élément qui expose les fonctionnalités à l’aide d’un <xref:System.Windows.Controls.Menu>spécifique au contexte. En règle générale, un utilisateur expose les <xref:System.Windows.Controls.ContextMenu> dans le [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] en cliquant avec le bouton droit sur le bouton de la souris. Cette rubrique présente l’élément <xref:System.Windows.Controls.ContextMenu> et fournit des exemples de son utilisation dans [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] et dans du code.  

<a name="contextmenu_control"></a>   
## <a name="contextmenu-control"></a>Contrôle ContextMenu  
 Un <xref:System.Windows.Controls.ContextMenu> est attaché à un contrôle spécifique. L’élément <xref:System.Windows.Controls.ContextMenu> vous permet de présenter aux utilisateurs une liste d’éléments qui spécifient des commandes ou des options associées à un contrôle particulier, par exemple, un <xref:System.Windows.Controls.Button>. Les utilisateurs cliquent avec le bouton droit sur le contrôle pour afficher le menu. En général, le fait de cliquer sur un <xref:System.Windows.Controls.MenuItem> ouvre un sous-menu ou provoque l’exécution d’une commande par une application.  
  
<a name="creating_contextmenus"></a>   
## <a name="creating-contextmenus"></a>Création d’un ContextMenu  
 Les exemples suivants montrent comment créer un <xref:System.Windows.Controls.ContextMenu> avec des sous-menus. Les contrôles <xref:System.Windows.Controls.ContextMenu> sont attachés aux contrôles Button.  
  
 [!code-xaml[ContextMenu#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ContextMenu/CSharp/Pane1.xaml#1)]  
  
 [!code-csharp[ContextMenu#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ContextMenu/CSharp/Pane1.xaml.cs#2)]
 [!code-vb[ContextMenu#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ContextMenu/VisualBasic/Pane1.xaml.vb#2)]  
  
<a name="applying_styles_to_contextmenu"></a>   
## <a name="applying-styles-to-a-contextmenu"></a>Application de styles à un ContextMenu  
 En utilisant un contrôle <xref:System.Windows.Style>, vous pouvez modifier radicalement l’apparence et le comportement d’une <xref:System.Windows.Controls.ContextMenu> sans écrire de contrôle personnalisé. Outre la définition de propriétés visuelles, vous pouvez appliquer des styles aux parties d’un contrôle. Par exemple, vous pouvez modifier le comportement des parties du contrôle à l’aide de propriétés, ou vous pouvez ajouter des parties à ou modifier la disposition d’un <xref:System.Windows.Controls.ContextMenu>. Les exemples suivants illustrent plusieurs façons d’ajouter des styles à des contrôles <xref:System.Windows.Controls.ContextMenu>.  
  
 Le premier exemple définit un style appelé `SimpleSysResources`, qui explique comment utiliser les paramètres système actuels dans votre style. L’exemple assigne <xref:System.Windows.SystemColors.MenuHighlightBrushKey%2A> comme couleur de <xref:System.Windows.Controls.Control.Background%2A> et <xref:System.Windows.SystemColors.MenuTextBrushKey%2A> comme <xref:System.Windows.Controls.Control.Foreground%2A> couleur du <xref:System.Windows.Controls.ContextMenu>.  
  
```xaml  
<Style x:Key="SimpleSysResources" TargetType="{x:Type MenuItem}">  
  <Setter Property = "Background" Value=   
    "{DynamicResource {x:Static SystemColors.MenuHighlightBrushKey}}"/>  
  <Setter Property = "Foreground" Value=   
    "{DynamicResource {x:Static SystemColors.MenuTextBrushKey}}"/>  
</Style>  
```  
  
 L’exemple suivant utilise l’élément <xref:System.Windows.Trigger> pour modifier l’apparence d’un <xref:System.Windows.Controls.Menu> en réponse aux événements déclenchés sur le <xref:System.Windows.Controls.ContextMenu>. Quand un utilisateur déplace la souris sur le menu, l’apparence des éléments de <xref:System.Windows.Controls.ContextMenu> change.  
  
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
- [ContextMenu](contextmenu.md)
- [Styles et modèles ContextMenu](contextmenu-styles-and-templates.md)
- [Exemple de galerie de contrôles WPF](https://github.com/Microsoft/WPF-Samples/tree/master/Getting%20Started/ControlsAndLayout)
