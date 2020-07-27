---
title: Vue d'ensemble de TreeView
description: Découvrez comment le contrôle TreeView Windows Presentation Foundation affiche des informations dans une structure hiérarchique à l’aide de nœuds, y compris des exemples simples.
ms.date: 03/30/2017
helpviewer_keywords:
- expanding node [WPF]
- TreeView control [WPF], about TreeView control
- Control class [WPF], TreeView
ms.assetid: 62212512-5a5c-4864-949e-b6a6a3a52c02
ms.openlocfilehash: 6ef77febdd3facb7c7e1af566841c2a1aeaff810
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164537"
---
# <a name="treeview-overview"></a>Vue d'ensemble de TreeView
Le <xref:System.Windows.Controls.TreeView> contrôle offre un moyen d’afficher des informations dans une structure hiérarchique à l’aide de nœuds réductibles. Cette rubrique présente les <xref:System.Windows.Controls.TreeView> contrôles et et <xref:System.Windows.Controls.TreeViewItem> fournit des exemples simples de leur utilisation.  

<a name="Simple_TreeView_Control"></a>
## <a name="what-is-a-treeview"></a>Qu’est-ce qu’un contrôle TreeView ?  
 <xref:System.Windows.Controls.TreeView>est un <xref:System.Windows.Controls.ItemsControl> qui imbrique les éléments à l’aide de <xref:System.Windows.Controls.TreeViewItem> contrôles. L’exemple suivant crée un <xref:System.Windows.Controls.TreeView> .  
  
 [!code-xaml[TreeViewSnips#EmbeddedTVIs](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSnips/CSharp/Window1.xaml#embeddedtvis)]  
  
<a name="Creating_a_TreeView"></a>
## <a name="creating-a-treeview"></a>Création d’un contrôle TreeView  
 Le <xref:System.Windows.Controls.TreeView> contrôle contient une hiérarchie de <xref:System.Windows.Controls.TreeViewItem> contrôles. Un <xref:System.Windows.Controls.TreeViewItem> contrôle est un <xref:System.Windows.Controls.HeaderedItemsControl> qui a un <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> et une <xref:System.Windows.Controls.ItemsControl.Items%2A> collection.  
  
 Si vous définissez un <xref:System.Windows.Controls.TreeView> à l’aide de [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] , vous pouvez définir explicitement le <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> contenu d’un <xref:System.Windows.Controls.TreeViewItem> contrôle et les éléments qui composent sa collection. L’illustration précédente montre cette méthode.  
  
 Vous pouvez également spécifier un <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> comme source de données, puis spécifier un <xref:System.Windows.Controls.HeaderedItemsControl.HeaderTemplate%2A> et <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> pour définir le <xref:System.Windows.Controls.TreeViewItem> contenu.  
  
 Pour définir la disposition d’un <xref:System.Windows.Controls.TreeViewItem> contrôle, vous pouvez également utiliser des <xref:System.Windows.HierarchicalDataTemplate> objets. Pour plus d’informations illustrées par un exemple, consultez la page [Utiliser SelectedValue, SelectedValuePath et SelectedItem](how-to-use-selectedvalue-selectedvaluepath-and-selecteditem.md).  
  
 Si un élément n’est pas un <xref:System.Windows.Controls.TreeViewItem> contrôle, il est automatiquement entouré par un <xref:System.Windows.Controls.TreeViewItem> contrôle lorsque le <xref:System.Windows.Controls.TreeView> contrôle est affiché.  
  
<a name="Expanding_and_Collapsing_a_TreeViewItem"></a>
## <a name="expanding-and-collapsing-a-treeviewitem"></a>Développer et réduire un élément TreeViewItem  
 Si l’utilisateur développe un <xref:System.Windows.Controls.TreeViewItem> , la <xref:System.Windows.Controls.TreeViewItem.IsExpanded%2A> propriété a la valeur `true` . Vous pouvez également développer ou réduire un <xref:System.Windows.Controls.TreeViewItem> sans action directe de l’utilisateur en affectant à la propriété la valeur <xref:System.Windows.Controls.TreeViewItem.IsExpanded%2A> `true` (développer) ou `false` (réduire). Lorsque cette propriété change, un <xref:System.Windows.Controls.TreeViewItem.Expanded> <xref:System.Windows.Controls.TreeViewItem.Collapsed> événement ou se produit.  
  
 Lorsque la <xref:System.Windows.FrameworkElement.BringIntoView%2A> méthode est appelée sur un <xref:System.Windows.Controls.TreeViewItem> contrôle, le <xref:System.Windows.Controls.TreeViewItem> et ses contrôles parents sont <xref:System.Windows.Controls.TreeViewItem> développés. Si un <xref:System.Windows.Controls.TreeViewItem> n’est pas visible ou partiellement visible, le <xref:System.Windows.Controls.TreeView> défile pour le rendre visible.  
  
<a name="TreeViewItem_Selection"></a>
## <a name="treeviewitem-selection"></a>Sélection d’un élément TreeViewItem  
 Lorsqu’un utilisateur clique sur un <xref:System.Windows.Controls.TreeViewItem> contrôle pour le sélectionner, l' <xref:System.Windows.Controls.TreeViewItem.Selected> événement se produit et sa <xref:System.Windows.Controls.TreeViewItem.IsSelected%2A> propriété a la valeur `true` . <xref:System.Windows.Controls.TreeViewItem>Devient également le <xref:System.Windows.Controls.TreeView.SelectedItem%2A> du <xref:System.Windows.Controls.TreeView> contrôle. À l’inverse, lorsque la sélection est modifiée à partir d’un <xref:System.Windows.Controls.TreeViewItem> contrôle, son <xref:System.Windows.Controls.TreeViewItem.Unselected> événement se produit et sa <xref:System.Windows.Controls.TreeViewItem.IsSelected%2A> propriété a la valeur `false` .  
  
 La <xref:System.Windows.Controls.TreeView.SelectedItem%2A> propriété sur le <xref:System.Windows.Controls.TreeView> contrôle est une propriété en lecture seule ; par conséquent, vous ne pouvez pas la définir explicitement. La <xref:System.Windows.Controls.TreeView.SelectedItem%2A> propriété est définie si l’utilisateur clique sur un <xref:System.Windows.Controls.TreeViewItem> contrôle ou lorsque la <xref:System.Windows.Controls.TreeViewItem.IsSelected%2A> propriété a la valeur `true` sur le <xref:System.Windows.Controls.TreeViewItem> contrôle.  
  
 Utilisez la <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> propriété pour spécifier un <xref:System.Windows.Controls.TreeView.SelectedValue%2A> d’un <xref:System.Windows.Controls.TreeView.SelectedItem%2A> . Pour plus d’informations, consultez la page [Utiliser SelectedValue, SelectedValuePath et SelectedItem](how-to-use-selectedvalue-selectedvaluepath-and-selecteditem.md).  
  
 Vous pouvez inscrire un gestionnaire d’événements sur l' <xref:System.Windows.Controls.TreeView.SelectedItemChanged> événement afin de déterminer quand une sélection est <xref:System.Windows.Controls.TreeViewItem> modifiée. Le <xref:System.Windows.RoutedPropertyChangedEventArgs%601> fourni au gestionnaire d’événements spécifie <xref:System.Windows.RoutedPropertyChangedEventArgs%601.OldValue%2A> , qui est la sélection précédente, et <xref:System.Windows.RoutedPropertyChangedEventArgs%601.NewValue%2A> , qui correspond à la sélection actuelle. Les deux valeurs peuvent être `null` si l’application ou l’utilisateur n’a effectué aucune sélection (aussi bien une sélection précédente qu’une sélection en cours).  
  
<a name="TreeView_Style"></a>
## <a name="treeview-style"></a>Style de TreeView  
 Le style par défaut d’un <xref:System.Windows.Controls.TreeView> contrôle le place à l’intérieur d’un <xref:System.Windows.Controls.StackPanel> objet qui contient un <xref:System.Windows.Controls.ScrollViewer> contrôle. Lorsque vous définissez les <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.FrameworkElement.Height%2A> Propriétés et pour un <xref:System.Windows.Controls.TreeView> , ces valeurs sont utilisées pour dimensionner l' <xref:System.Windows.Controls.StackPanel> objet qui affiche <xref:System.Windows.Controls.TreeView> . Si le contenu à afficher est plus grand que la zone d’affichage, un <xref:System.Windows.Controls.ScrollViewer> s’affiche automatiquement afin que l’utilisateur puisse faire défiler le <xref:System.Windows.Controls.TreeView> contenu.  
  
 Pour personnaliser l’apparence d’un <xref:System.Windows.Controls.TreeViewItem> contrôle, affectez <xref:System.Windows.FrameworkElement.Style%2A> à la propriété une valeur personnalisée <xref:System.Windows.Style> .  
  
 L’exemple suivant montre comment définir les <xref:System.Windows.Controls.Control.Foreground%2A> <xref:System.Windows.Controls.Control.FontSize%2A> valeurs de propriété et pour un <xref:System.Windows.Controls.TreeViewItem> contrôle à l’aide d’un <xref:System.Windows.FrameworkElement.Style%2A> .  
  
 [!code-xaml[TreeViewSimple#8](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#8)]  
  
<a name="Adding_Images_and_oOther_Content_to_TreeView_Items"></a>
## <a name="adding-images-and-other-content-to-treeview-items"></a>Ajouter des images et d’autres contenus à des éléments TreeView  
 Vous pouvez inclure plusieurs objets dans le <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> contenu d’un <xref:System.Windows.Controls.TreeViewItem> . Pour inclure plusieurs objets dans <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> le contenu, mettez les objets à l’intérieur d’un contrôle Layout, tel que <xref:System.Windows.Controls.Panel> ou <xref:System.Windows.Controls.StackPanel> .  
  
 L’exemple suivant montre comment définir le <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> d’un <xref:System.Windows.Controls.TreeViewItem> en tant que <xref:System.Windows.Controls.CheckBox> et <xref:System.Windows.Controls.TextBlock> qui sont tous deux placés dans un <xref:System.Windows.Controls.DockPanel> contrôle.  
  
 [!code-xaml[TreeViewSnips#TVIHeader](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSnips/CSharp/Window1.xaml#tviheader)]  
  
 L’exemple suivant montre comment définir un <xref:System.Windows.DataTemplate> qui contient un <xref:System.Windows.Controls.Image> et un <xref:System.Windows.Controls.TextBlock> qui sont placés dans un <xref:System.Windows.Controls.DockPanel> contrôle. Vous pouvez utiliser un <xref:System.Windows.DataTemplate> pour définir <xref:System.Windows.Controls.HeaderedItemsControl.HeaderTemplate%2A> ou <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> pour un <xref:System.Windows.Controls.TreeViewItem> .  
  
 [!code-xaml[TreeViewDataBinding#6](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewDataBinding/CSharp/Window1.xaml#6)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Controls.TreeView>
- <xref:System.Windows.Controls.TreeViewItem>
- [Rubriques Comment](treeview-how-to-topics.md)
- [Modèle de contenu WPF](wpf-content-model.md)
