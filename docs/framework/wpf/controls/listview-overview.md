---
title: Vue d'ensemble de ListView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], ListView
- ListView controls [WPF], about ListView control
ms.assetid: 989e12b0-260e-4570-95c6-489284003ce2
ms.openlocfilehash: 0148ded31f1c637f533f8e80427672a79ef05e02
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64621279"
---
# <a name="listview-overview"></a>Vue d'ensemble de ListView
Le <xref:System.Windows.Controls.ListView> contrôle fournit l’infrastructure pour afficher un ensemble d’éléments de données dans différentes dispositions ou différents affichages. Par exemple, un utilisateur peut souhaiter afficher des éléments de données dans un tableau et en trier les colonnes.  

<a name="WhatisaListView"></a>   
## <a name="what-is-a-listview"></a>Qu’est qu’un contrôle ListView ?  
 Le <xref:System.Windows.Controls.ListView> contrôle est un <xref:System.Windows.Controls.ItemsControl> qui est dérivée de <xref:System.Windows.Controls.ListBox>. En règle générale, ses éléments sont membres d’une collection de données et sont représentés en tant que <xref:System.Windows.Controls.ListViewItem> objets. Un <xref:System.Windows.Controls.ListViewItem> est un <xref:System.Windows.Controls.ContentControl> et peut contenir uniquement un seul élément enfant. Toutefois, cet élément enfant peut être n’importe quel élément visuel.  
  
<a name="DefiningaListViewView"></a>   
## <a name="defining-a-view-mode-for-a-listview"></a>Définition d’un mode d’affichage pour un ListView  
 Pour spécifier un mode d’affichage pour le contenu d’un <xref:System.Windows.Controls.ListView> contrôle, vous définissez le <xref:System.Windows.Controls.ListView.View%2A> propriété. Mode d’affichage qui [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] fournit est <xref:System.Windows.Controls.GridView>, qui affiche une collection d’éléments de données dans une table qui comporte des colonnes personnalisables.  
  
 L’exemple suivant montre comment définir un <xref:System.Windows.Controls.GridView> pour un <xref:System.Windows.Controls.ListView> contrôle qui affiche des informations sur les employés.  
  
 [!code-xaml[ListViewCode#ListViewEmployee](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#listviewemployee)]  
  
 L’illustration suivante montre le tableau créé par l’exemple précédent.  
  
 ![Capture d’écran montrant un ListView avec GridView sortie.](./media/gridview-overview/listview-gridview-output.jpg)  
  
 Vous pouvez créer un mode d’affichage personnalisé en définissant une classe qui hérite de la <xref:System.Windows.Controls.ViewBase> classe. Le <xref:System.Windows.Controls.ViewBase> classe fournit l’infrastructure dont vous avez besoin pour créer une vue personnalisée. Pour plus d’informations sur la création d’un affichage personnalisé, consultez la page [Créer un mode d’affichage personnalisé pour un ListView](how-to-create-a-custom-view-mode-for-a-listview.md).  
  
<a name="BindingDatatoaListView"></a>   
## <a name="binding-data-to-a-listview"></a>Liaison des données à un contrôle ListView  
 Utilisez le <xref:System.Windows.Controls.ItemsControl.Items%2A> et <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> propriétés pour spécifier des éléments pour un <xref:System.Windows.Controls.ListView> contrôle. L’exemple suivant définit la <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> propriété à une collection de données qui est appelée `EmployeeInfoDataSource`.  
  
 [!code-xaml[ListViewCode#ItemsSource](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#itemssource)]  
  
 Dans un <xref:System.Windows.Controls.GridView>, <xref:System.Windows.Controls.GridViewColumn> objets lier à des champs de données spécifié. L’exemple suivant lie un <xref:System.Windows.Controls.GridViewColumn> objet à un champ de données en spécifiant un <xref:System.Windows.Data.Binding> pour le <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> propriété.  
  
 [!code-csharp[ListViewCode#GridViewColumnProperties](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml.cs#gridviewcolumnproperties)]
 [!code-vb[ListViewCode#GridViewColumnProperties](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewCode/visualbasic/window1.xaml.vb#gridviewcolumnproperties)]
 [!code-xaml[ListViewCode#GridViewColumnProperties](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#gridviewcolumnproperties)]  
  
 Vous pouvez également spécifier un <xref:System.Windows.Data.Binding> en tant que partie d’un <xref:System.Windows.DataTemplate> définition que vous utilisez pour définir le style des cellules dans une colonne. Dans l’exemple suivant, le <xref:System.Windows.DataTemplate> qui est identifié avec un <xref:System.Windows.ResourceKey> définit le <xref:System.Windows.Data.Binding> pour un <xref:System.Windows.Controls.GridViewColumn>. Notez que cet exemple ne définit pas le <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> , car cette opération remplace par conséquent, la liaison est spécifiée par <xref:System.Windows.DataTemplate>.  
  
 [!code-xaml[ListViewTemplate#GridViewCellTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewcelltemplate)]  
  
 [!code-xaml[ListViewTemplate#CellTemplateProperty](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#celltemplateproperty)]  
  
<a name="StylingaListView"></a>   
## <a name="styling-a-listview-that-implements-a-gridview"></a>Appliquer un style à un ListView implémentant un GridView  
 Le <xref:System.Windows.Controls.ListView> contrôle contient <xref:System.Windows.Controls.ListViewItem> objets qui représentent les éléments de données qui sont affichés. Vous pouvez utiliser les propriétés suivantes pour définir le contenu et le style des éléments de données :  
  
- Sur le <xref:System.Windows.Controls.ListView> contrôler, utilisez le <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>, <xref:System.Windows.Controls.ItemsControl.ItemTemplateSelector%2A>, et <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> propriétés.  
  
- Sur le <xref:System.Windows.Controls.ListViewItem> contrôler, utilisez le <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> et <xref:System.Windows.Controls.ContentControl.ContentTemplateSelector%2A> propriétés.  
  
 Pour éviter les problèmes d’alignement entre les cellules d’un <xref:System.Windows.Controls.GridView>, n’utilisez pas le <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> pour définir des propriétés ou ajouter du contenu qui affecte la largeur d’un élément dans un <xref:System.Windows.Controls.ListView>. Par exemple, un problème d’alignement peut se produire lorsque vous définissez la <xref:System.Windows.FrameworkElement.Margin%2A> propriété dans le <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>. Pour spécifier des propriétés ou définir le contenu qui affecte la largeur des éléments dans un <xref:System.Windows.Controls.GridView>, utilisez les propriétés de la <xref:System.Windows.Controls.GridView> classe et ses classes connexes, tels que <xref:System.Windows.Controls.GridViewColumn>.  
  
 Pour plus d’informations sur l’utilisation <xref:System.Windows.Controls.GridView> et ses classes de prise en charge, consultez [vue d’ensemble de GridView](gridview-overview.md).  
  
 Si vous définissez un <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> pour un <xref:System.Windows.Controls.ListView> contrôlent et définissent un <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>, vous devez inclure un <xref:System.Windows.Controls.ContentPresenter> dans le style afin que le <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> fonctionne correctement.  
  
 N’utilisez pas le <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> et <xref:System.Windows.Controls.Control.VerticalContentAlignment%2A> propriétés pour <xref:System.Windows.Controls.ListView> contenu qui est affiché à l’aide un <xref:System.Windows.Controls.GridView>. Pour spécifier l’alignement du contenu dans une colonne d’un <xref:System.Windows.Controls.GridView>, définir un <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A>.  
  
<a name="UsingtheSameViewMoreThanOnce"></a>   
## <a name="sharing-the-same-view-mode"></a>Partage du mode d’affichage  
 Deux <xref:System.Windows.Controls.ListView> contrôles ne peuvent pas partager le même mode d’affichage en même temps. Si vous essayez d’utiliser le même mode d’affichage avec plusieurs <xref:System.Windows.Controls.ListView> contrôler, une exception se produit.  
  
 Pour spécifier un mode d’affichage qui peut être utilisé simultanément par plusieurs <xref:System.Windows.Controls.ListView>, utilisez des modèles ou des styles.
  
<a name="CreatingaCustomView"></a>   
## <a name="creating-a-custom-view-mode"></a>Créer un mode d’affichage personnalisé  
 Affichages personnalisés tels que <xref:System.Windows.Controls.GridView> sont dérivés de la <xref:System.Windows.Controls.ViewBase> classe, qui fournit les outils pour afficher les éléments de données qui sont représentées sous forme abstraite <xref:System.Windows.Controls.ListViewItem> objets.    
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Controls.GridView>
- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.ListViewItem>
- <xref:System.Windows.Data.Binding>
- [Vue d’ensemble de GridView](gridview-overview.md)
- [Rubriques de guide pratique](listview-how-to-topics.md)
- [Contrôles](../advanced/optimizing-performance-controls.md)
