---
title: Vue d'ensemble de TreeView
ms.date: 03/30/2017
helpviewer_keywords:
- expanding node [WPF]
- TreeView control [WPF], about TreeView control
- Control class [WPF], TreeView
ms.assetid: 62212512-5a5c-4864-949e-b6a6a3a52c02
ms.openlocfilehash: 267e870e13d26439e4fbcbba3c5741ff84cabe3c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187368"
---
# <a name="treeview-overview"></a>Vue d'ensemble de TreeView
Le <xref:System.Windows.Controls.TreeView> contrôle fournit un moyen d’afficher des informations dans une structure hiérarchique en utilisant des nœuds pliables. Ce sujet introduit <xref:System.Windows.Controls.TreeView> <xref:System.Windows.Controls.TreeViewItem> le et contrôle, et fournit des exemples simples de leur utilisation.  

<a name="Simple_TreeView_Control"></a>
## <a name="what-is-a-treeview"></a>Qu’est-ce qu’un contrôle TreeView ?  
 <xref:System.Windows.Controls.TreeView>est <xref:System.Windows.Controls.ItemsControl> un qui niche les <xref:System.Windows.Controls.TreeViewItem> éléments en utilisant des contrôles. L’exemple suivant <xref:System.Windows.Controls.TreeView>crée un .  
  
 [!code-xaml[TreeViewSnips#EmbeddedTVIs](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSnips/CSharp/Window1.xaml#embeddedtvis)]  
  
<a name="Creating_a_TreeView"></a>
## <a name="creating-a-treeview"></a>Création d’un contrôle TreeView  
 Le <xref:System.Windows.Controls.TreeView> contrôle contient <xref:System.Windows.Controls.TreeViewItem> une hiérarchie de contrôles. Un <xref:System.Windows.Controls.TreeViewItem> contrôle <xref:System.Windows.Controls.HeaderedItemsControl> est un <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> qui <xref:System.Windows.Controls.ItemsControl.Items%2A> a un et une collection.  
  
 Si vous <xref:System.Windows.Controls.TreeView> définissez [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]un en utilisant, <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> vous <xref:System.Windows.Controls.TreeViewItem> pouvez définir explicitement le contenu d’un contrôle et les éléments qui composent sa collection. L’illustration précédente montre cette méthode.  
  
 Vous pouvez également <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> spécifier une <xref:System.Windows.Controls.HeaderedItemsControl.HeaderTemplate%2A> source <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> de <xref:System.Windows.Controls.TreeViewItem> données, puis spécifier un et définir le contenu.  
  
 Pour définir la <xref:System.Windows.Controls.TreeViewItem> disposition d’un <xref:System.Windows.HierarchicalDataTemplate> contrôle, vous pouvez également utiliser des objets. Pour plus d’informations illustrées par un exemple, consultez la page [Utiliser SelectedValue, SelectedValuePath et SelectedItem](how-to-use-selectedvalue-selectedvaluepath-and-selecteditem.md).  
  
 Si un élément <xref:System.Windows.Controls.TreeViewItem> n’est pas un contrôle, il est automatiquement inclus par un <xref:System.Windows.Controls.TreeViewItem> contrôle lorsque le <xref:System.Windows.Controls.TreeView> contrôle est affiché.  
  
<a name="Expanding_and_Collapsing_a_TreeViewItem"></a>
## <a name="expanding-and-collapsing-a-treeviewitem"></a>Développer et réduire un élément TreeViewItem  
 Si l’utilisateur <xref:System.Windows.Controls.TreeViewItem>élargit <xref:System.Windows.Controls.TreeViewItem.IsExpanded%2A> un , `true`la propriété est définie à . Vous pouvez également étendre <xref:System.Windows.Controls.TreeViewItem> ou s’effondrer sans <xref:System.Windows.Controls.TreeViewItem.IsExpanded%2A> aucune `true` action directe `false` de l’utilisateur en définissant la propriété à (élargir) ou (effondrement). Lorsque cette propriété <xref:System.Windows.Controls.TreeViewItem.Expanded> change, un ou <xref:System.Windows.Controls.TreeViewItem.Collapsed> un événement se produit.  
  
 Lorsque <xref:System.Windows.FrameworkElement.BringIntoView%2A> la méthode est <xref:System.Windows.Controls.TreeViewItem> appelée <xref:System.Windows.Controls.TreeViewItem> sur un <xref:System.Windows.Controls.TreeViewItem> contrôle, le contrôle et ses parents s’éteil. Si <xref:System.Windows.Controls.TreeViewItem> l’a n’est <xref:System.Windows.Controls.TreeView> pas visible ou partiellement visible, les rouleaux pour le rendre visible.  
  
<a name="TreeViewItem_Selection"></a>
## <a name="treeviewitem-selection"></a>Sélection d’un élément TreeViewItem  
 Lorsqu’un utilisateur <xref:System.Windows.Controls.TreeViewItem> clique sur un <xref:System.Windows.Controls.TreeViewItem.Selected> contrôle pour le <xref:System.Windows.Controls.TreeViewItem.IsSelected%2A> sélectionner, `true`l’événement se produit, et sa propriété est définie à . Le <xref:System.Windows.Controls.TreeViewItem> devient <xref:System.Windows.Controls.TreeView.SelectedItem%2A> aussi <xref:System.Windows.Controls.TreeView> le du contrôle. Inversement, lorsque la <xref:System.Windows.Controls.TreeViewItem> sélection change <xref:System.Windows.Controls.TreeViewItem.Unselected> d’un <xref:System.Windows.Controls.TreeViewItem.IsSelected%2A> contrôle, `false`son événement se produit et sa propriété est réglée à .  
  
 La <xref:System.Windows.Controls.TreeView.SelectedItem%2A> propriété <xref:System.Windows.Controls.TreeView> sur le contrôle est une propriété lue seulement; par conséquent, vous ne pouvez pas le définir explicitement. La <xref:System.Windows.Controls.TreeView.SelectedItem%2A> propriété est définie si l’utilisateur <xref:System.Windows.Controls.TreeViewItem> clique sur un contrôle ou lorsque <xref:System.Windows.Controls.TreeViewItem.IsSelected%2A> la propriété est réglée `true` sur le <xref:System.Windows.Controls.TreeViewItem> contrôle.  
  
 Utilisez <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> la propriété <xref:System.Windows.Controls.TreeView.SelectedValue%2A> pour <xref:System.Windows.Controls.TreeView.SelectedItem%2A>spécifier un de . Pour plus d’informations, consultez la page [Utiliser SelectedValue, SelectedValuePath et SelectedItem](how-to-use-selectedvalue-selectedvaluepath-and-selecteditem.md).  
  
 Vous pouvez inscrire un <xref:System.Windows.Controls.TreeView.SelectedItemChanged> gestionnaire d’événements sur <xref:System.Windows.Controls.TreeViewItem> l’événement afin de déterminer quand un changement sélectionné. Le <xref:System.Windows.RoutedPropertyChangedEventArgs%601> qui est fourni au gestionnaire <xref:System.Windows.RoutedPropertyChangedEventArgs%601.OldValue%2A>d’événement précise le , <xref:System.Windows.RoutedPropertyChangedEventArgs%601.NewValue%2A>qui est la sélection précédente, et le , qui est la sélection actuelle. Les deux valeurs peuvent être `null` si l’application ou l’utilisateur n’a effectué aucune sélection (aussi bien une sélection précédente qu’une sélection en cours).  
  
<a name="TreeView_Style"></a>
## <a name="treeview-style"></a>Style de TreeView  
 Le style par <xref:System.Windows.Controls.TreeView> défaut pour <xref:System.Windows.Controls.StackPanel> un contrôle <xref:System.Windows.Controls.ScrollViewer> le place à l’intérieur d’un objet qui contient un contrôle. Lorsque vous <xref:System.Windows.FrameworkElement.Width%2A> définissez le <xref:System.Windows.FrameworkElement.Height%2A> et les propriétés pour un <xref:System.Windows.Controls.TreeView>, ces valeurs sont utilisées pour tailler l’objet <xref:System.Windows.Controls.StackPanel> qui affiche le <xref:System.Windows.Controls.TreeView>. Si le contenu à afficher est plus <xref:System.Windows.Controls.ScrollViewer> grand que la zone d’affichage, un affichage automatiquement de sorte que l’utilisateur peut faire défiler le <xref:System.Windows.Controls.TreeView> contenu.  
  
 Pour personnaliser l’apparence <xref:System.Windows.Controls.TreeViewItem> d’un <xref:System.Windows.FrameworkElement.Style%2A> contrôle, <xref:System.Windows.Style>définissez la propriété sur une coutume.  
  
 L’exemple suivant montre <xref:System.Windows.Controls.Control.Foreground%2A> comment <xref:System.Windows.Controls.Control.FontSize%2A> définir les <xref:System.Windows.Controls.TreeViewItem> valeurs et <xref:System.Windows.FrameworkElement.Style%2A>les valeurs de propriété pour un contrôle en utilisant un .  
  
 [!code-xaml[TreeViewSimple#8](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#8)]  
  
<a name="Adding_Images_and_oOther_Content_to_TreeView_Items"></a>
## <a name="adding-images-and-other-content-to-treeview-items"></a>Ajouter des images et d’autres contenus à des éléments TreeView  
 Vous pouvez inclure plus d’un objet dans le <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> contenu d’un <xref:System.Windows.Controls.TreeViewItem>. Pour inclure plusieurs <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> objets dans le contenu, enfermez <xref:System.Windows.Controls.Panel> les <xref:System.Windows.Controls.StackPanel>objets à l’intérieur d’un contrôle de mise en page, tel que a ou .  
  
 L’exemple suivant montre <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> comment <xref:System.Windows.Controls.TreeViewItem> définir <xref:System.Windows.Controls.CheckBox> l’a comme un <xref:System.Windows.Controls.TextBlock> <xref:System.Windows.Controls.DockPanel> et qui sont tous deux enfermés dans un contrôle.  
  
 [!code-xaml[TreeViewSnips#TVIHeader](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSnips/CSharp/Window1.xaml#tviheader)]  
  
 L’exemple suivant montre <xref:System.Windows.DataTemplate> comment définir <xref:System.Windows.Controls.Image> un <xref:System.Windows.Controls.TextBlock> qui contient un <xref:System.Windows.Controls.DockPanel> et un qui sont enfermés dans un contrôle. Vous pouvez <xref:System.Windows.DataTemplate> utiliser un <xref:System.Windows.Controls.HeaderedItemsControl.HeaderTemplate%2A> <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> pour <xref:System.Windows.Controls.TreeViewItem>définir le ou pour un .  
  
 [!code-xaml[TreeViewDataBinding#6](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewDataBinding/CSharp/Window1.xaml#6)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Controls.TreeView>
- <xref:System.Windows.Controls.TreeViewItem>
- [Sujets comment se passer](treeview-how-to-topics.md)
- [Modèle de contenu WPF](wpf-content-model.md)
