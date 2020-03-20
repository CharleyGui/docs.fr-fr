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
# <a name="contextmenu-overview"></a><span data-ttu-id="0b9cd-102">Vue d'ensemble de ContextMenu</span><span class="sxs-lookup"><span data-stu-id="0b9cd-102">ContextMenu Overview</span></span>
<span data-ttu-id="0b9cd-103">La <xref:System.Windows.Controls.ContextMenu> classe représente l’élément qui expose la <xref:System.Windows.Controls.Menu>fonctionnalité en utilisant un contexte spécifique .</span><span class="sxs-lookup"><span data-stu-id="0b9cd-103">The <xref:System.Windows.Controls.ContextMenu> class represents the element that exposes functionality by using a context-specific <xref:System.Windows.Controls.Menu>.</span></span> <span data-ttu-id="0b9cd-104">Typiquement, un utilisateur <xref:System.Windows.Controls.ContextMenu> expose [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] le dans le en cliquant sur le bouton de la souris.</span><span class="sxs-lookup"><span data-stu-id="0b9cd-104">Typically, a user exposes the <xref:System.Windows.Controls.ContextMenu> in the [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] by right-clicking the mouse button.</span></span> <span data-ttu-id="0b9cd-105">Ce sujet introduit <xref:System.Windows.Controls.ContextMenu> l’élément et fournit des [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] exemples de la façon de l’utiliser et de coder.</span><span class="sxs-lookup"><span data-stu-id="0b9cd-105">This topic introduces the <xref:System.Windows.Controls.ContextMenu> element and provides examples of how to use it in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] and code.</span></span>  

<a name="contextmenu_control"></a>
## <a name="contextmenu-control"></a><span data-ttu-id="0b9cd-106">Contrôle ContextMenu</span><span class="sxs-lookup"><span data-stu-id="0b9cd-106">ContextMenu Control</span></span>  
 <span data-ttu-id="0b9cd-107">A <xref:System.Windows.Controls.ContextMenu> est attaché à un contrôle spécifique.</span><span class="sxs-lookup"><span data-stu-id="0b9cd-107">A <xref:System.Windows.Controls.ContextMenu> is attached to a specific control.</span></span> <span data-ttu-id="0b9cd-108">L’élément <xref:System.Windows.Controls.ContextMenu> vous permet de présenter aux utilisateurs une liste d’éléments qui spécifient des commandes ou des options qui sont associées à un contrôle particulier, par exemple, un <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="0b9cd-108">The <xref:System.Windows.Controls.ContextMenu> element enables you to present users with a list of items that specify commands or options that are associated with a particular control, for example, a <xref:System.Windows.Controls.Button>.</span></span> <span data-ttu-id="0b9cd-109">Les utilisateurs cliquent avec le bouton droit sur le contrôle pour afficher le menu.</span><span class="sxs-lookup"><span data-stu-id="0b9cd-109">Users right-click the control to make the menu appear.</span></span> <span data-ttu-id="0b9cd-110">Typiquement, en <xref:System.Windows.Controls.MenuItem> cliquant sur un ouvre un sous-présage ou provoque une application pour effectuer une commande.</span><span class="sxs-lookup"><span data-stu-id="0b9cd-110">Typically, clicking a <xref:System.Windows.Controls.MenuItem> opens a submenu or causes an application to carry out a command.</span></span>  
  
<a name="creating_contextmenus"></a>
## <a name="creating-contextmenus"></a><span data-ttu-id="0b9cd-111">Création d’un ContextMenu</span><span class="sxs-lookup"><span data-stu-id="0b9cd-111">Creating ContextMenus</span></span>  
 <span data-ttu-id="0b9cd-112">Les exemples suivants montrent <xref:System.Windows.Controls.ContextMenu> comment créer un sous-genre avec.</span><span class="sxs-lookup"><span data-stu-id="0b9cd-112">The following examples show how to create a <xref:System.Windows.Controls.ContextMenu> with submenus.</span></span> <span data-ttu-id="0b9cd-113">Les <xref:System.Windows.Controls.ContextMenu> commandes sont fixées aux commandes de boutons.</span><span class="sxs-lookup"><span data-stu-id="0b9cd-113">The <xref:System.Windows.Controls.ContextMenu> controls are attached to button controls.</span></span>  
  
 [!code-xaml[ContextMenu#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ContextMenu/CSharp/Pane1.xaml#1)]  
  
 [!code-csharp[ContextMenu#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ContextMenu/CSharp/Pane1.xaml.cs#2)]
 [!code-vb[ContextMenu#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ContextMenu/VisualBasic/Pane1.xaml.vb#2)]  
  
<a name="applying_styles_to_contextmenu"></a>
## <a name="applying-styles-to-a-contextmenu"></a><span data-ttu-id="0b9cd-114">Application de styles à un ContextMenu</span><span class="sxs-lookup"><span data-stu-id="0b9cd-114">Applying Styles to a ContextMenu</span></span>  
 <span data-ttu-id="0b9cd-115">En utilisant <xref:System.Windows.Style>un contrôle , vous pouvez changer <xref:System.Windows.Controls.ContextMenu> radicalement l’apparence et le comportement d’un sans écrire un contrôle personnalisé.</span><span class="sxs-lookup"><span data-stu-id="0b9cd-115">By using a control <xref:System.Windows.Style>, you can dramatically change the appearance and behavior of a <xref:System.Windows.Controls.ContextMenu> without writing a custom control.</span></span> <span data-ttu-id="0b9cd-116">Outre la définition de propriétés visuelles, vous pouvez appliquer des styles aux parties d’un contrôle.</span><span class="sxs-lookup"><span data-stu-id="0b9cd-116">In addition to setting visual properties, you can also apply styles to parts of a control.</span></span> <span data-ttu-id="0b9cd-117">Par exemple, vous pouvez modifier le comportement des parties du contrôle en utilisant des propriétés, ou vous pouvez ajouter des pièces à, ou modifier la disposition de, a <xref:System.Windows.Controls.ContextMenu>.</span><span class="sxs-lookup"><span data-stu-id="0b9cd-117">For example, you can change the behavior of parts of the control by using properties, or you can add parts to, or change the layout of, a <xref:System.Windows.Controls.ContextMenu>.</span></span> <span data-ttu-id="0b9cd-118">Les exemples suivants montrent plusieurs <xref:System.Windows.Controls.ContextMenu> façons d’ajouter des styles aux contrôles.</span><span class="sxs-lookup"><span data-stu-id="0b9cd-118">The following examples show several ways to add styles to <xref:System.Windows.Controls.ContextMenu> controls.</span></span>  
  
 <span data-ttu-id="0b9cd-119">Le premier exemple définit un style appelé `SimpleSysResources`, qui explique comment utiliser les paramètres système actuels dans votre style.</span><span class="sxs-lookup"><span data-stu-id="0b9cd-119">The first example defines a style called `SimpleSysResources`, which shows how to use the current system settings in your style.</span></span> <span data-ttu-id="0b9cd-120">L’exemple <xref:System.Windows.SystemColors.MenuHighlightBrushKey%2A> attribue <xref:System.Windows.Controls.Control.Background%2A> comme <xref:System.Windows.SystemColors.MenuTextBrushKey%2A> la <xref:System.Windows.Controls.Control.Foreground%2A> couleur et <xref:System.Windows.Controls.ContextMenu>comme la couleur de la .</span><span class="sxs-lookup"><span data-stu-id="0b9cd-120">The example assigns <xref:System.Windows.SystemColors.MenuHighlightBrushKey%2A> as the <xref:System.Windows.Controls.Control.Background%2A> color and <xref:System.Windows.SystemColors.MenuTextBrushKey%2A> as the <xref:System.Windows.Controls.Control.Foreground%2A> color of the <xref:System.Windows.Controls.ContextMenu>.</span></span>  
  
```xaml  
<Style x:Key="SimpleSysResources" TargetType="{x:Type MenuItem}">  
  <Setter Property = "Background" Value=
    "{DynamicResource {x:Static SystemColors.MenuHighlightBrushKey}}"/>  
  <Setter Property = "Foreground" Value=
    "{DynamicResource {x:Static SystemColors.MenuTextBrushKey}}"/>  
</Style>  
```  
  
 <span data-ttu-id="0b9cd-121">L’exemple suivant <xref:System.Windows.Trigger> utilise l’élément <xref:System.Windows.Controls.Menu> pour changer l’apparence d’une réponse aux événements qui sont soulevés sur le <xref:System.Windows.Controls.ContextMenu>.</span><span class="sxs-lookup"><span data-stu-id="0b9cd-121">The following example uses the <xref:System.Windows.Trigger> element to change the appearance of a <xref:System.Windows.Controls.Menu> in response to events that are raised on the <xref:System.Windows.Controls.ContextMenu>.</span></span> <span data-ttu-id="0b9cd-122">Lorsqu’un utilisateur déplace la souris sur <xref:System.Windows.Controls.ContextMenu> le menu, l’apparence des éléments change.</span><span class="sxs-lookup"><span data-stu-id="0b9cd-122">When a user moves the mouse over the menu, the appearance of the <xref:System.Windows.Controls.ContextMenu> items changes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0b9cd-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0b9cd-123">See also</span></span>

- <xref:System.Windows.Controls.ContextMenu>
- <xref:System.Windows.Style>
- <xref:System.Windows.Controls.Menu>
- <xref:System.Windows.Controls.MenuItem>
- [<span data-ttu-id="0b9cd-124">Contextmenu</span><span class="sxs-lookup"><span data-stu-id="0b9cd-124">ContextMenu</span></span>](contextmenu.md)
- [<span data-ttu-id="0b9cd-125">Styles et modèles ContextMenu</span><span class="sxs-lookup"><span data-stu-id="0b9cd-125">ContextMenu Styles and Templates</span></span>](contextmenu-styles-and-templates.md)
- [<span data-ttu-id="0b9cd-126">Exemple de galerie de contrôles WPF</span><span class="sxs-lookup"><span data-stu-id="0b9cd-126">WPF Controls Gallery Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Getting%20Started/ControlsAndLayout)
