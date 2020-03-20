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
ms.openlocfilehash: 2f336d1eb8dcdfec3c3c8059ba865147c6b6c825
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187521"
---
# <a name="listview-overview"></a>Vue d'ensemble de ListView
Le <xref:System.Windows.Controls.ListView> contrôle fournit l’infrastructure pour afficher un ensemble d’éléments de données dans différentes mises en page ou vues. Par exemple, un utilisateur peut souhaiter afficher des éléments de données dans un tableau et en trier les colonnes.  

<a name="WhatisaListView"></a>
## <a name="what-is-a-listview"></a>Qu’est qu’un contrôle ListView ?  
 Le <xref:System.Windows.Controls.ListView> contrôle <xref:System.Windows.Controls.ItemsControl> est un <xref:System.Windows.Controls.ListBox>qui est dérivé de . En règle générale, ses éléments sont membres <xref:System.Windows.Controls.ListViewItem> d’une collecte de données et sont représentés comme des objets. A <xref:System.Windows.Controls.ListViewItem> est <xref:System.Windows.Controls.ContentControl> un et ne peut contenir qu’un seul élément enfant. Toutefois, cet élément enfant peut être n’importe quel élément visuel.  
  
<a name="DefiningaListViewView"></a>
## <a name="defining-a-view-mode-for-a-listview"></a>Définition d’un mode d’affichage pour un ListView  
 Pour spécifier un mode <xref:System.Windows.Controls.ListView> de vue <xref:System.Windows.Controls.ListView.View%2A> pour le contenu d’un contrôle, vous définissez la propriété. Un mode [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] de <xref:System.Windows.Controls.GridView>vue qui fournit est , qui affiche une collection d’éléments de données dans une table qui a des colonnes personnalisables.  
  
 L’exemple suivant montre <xref:System.Windows.Controls.GridView> comment <xref:System.Windows.Controls.ListView> définir un contrôle qui affiche les informations des employés.  
  
 [!code-xaml[ListViewCode#ListViewEmployee](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#listviewemployee)]  
  
 L’illustration suivante montre le tableau créé par l’exemple précédent.  
  
 ![Capture d’écran qui montre une listé avec la sortie GridView.](./media/gridview-overview/listview-gridview-output.jpg)  
  
 Vous pouvez créer un mode de vue personnalisé <xref:System.Windows.Controls.ViewBase> en définissant une classe qui hérite de la classe. La <xref:System.Windows.Controls.ViewBase> classe fournit l’infrastructure dont vous avez besoin pour créer une vue personnalisée. Pour plus d’informations sur la création d’un affichage personnalisé, consultez la page [Créer un mode d’affichage personnalisé pour un ListView](how-to-create-a-custom-view-mode-for-a-listview.md).  
  
<a name="BindingDatatoaListView"></a>
## <a name="binding-data-to-a-listview"></a>Liaison des données à un contrôle ListView  
 Utilisez <xref:System.Windows.Controls.ItemsControl.Items%2A> les <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> propriétés et <xref:System.Windows.Controls.ListView> les propriétés pour spécifier les éléments pour un contrôle. L’exemple suivant <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> donne la propriété à `EmployeeInfoDataSource`une collecte de données qui s’appelle .  
  
 [!code-xaml[ListViewCode#ItemsSource](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#itemssource)]  
  
 Dans <xref:System.Windows.Controls.GridView>un <xref:System.Windows.Controls.GridViewColumn> , les objets se lient à des champs de données spécifiés. L’exemple suivant <xref:System.Windows.Controls.GridViewColumn> lie un objet à un <xref:System.Windows.Data.Binding> champ <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> de données en spécifiant un pour la propriété.  
  
 [!code-csharp[ListViewCode#GridViewColumnProperties](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml.cs#gridviewcolumnproperties)]
 [!code-vb[ListViewCode#GridViewColumnProperties](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewCode/visualbasic/window1.xaml.vb#gridviewcolumnproperties)]
 [!code-xaml[ListViewCode#GridViewColumnProperties](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#gridviewcolumnproperties)]  
  
 Vous pouvez également <xref:System.Windows.Data.Binding> spécifier une <xref:System.Windows.DataTemplate> définition que vous utilisez pour coiffer les cellules dans une colonne. Dans l’exemple <xref:System.Windows.DataTemplate> suivant, celui <xref:System.Windows.ResourceKey> qui <xref:System.Windows.Data.Binding> est <xref:System.Windows.Controls.GridViewColumn>identifié avec un ensemble de la pour un . Notez que cet exemple <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> ne définit pas le parce que <xref:System.Windows.DataTemplate>cela l’emporte sur la liaison qui est spécifiée par .  
  
 [!code-xaml[ListViewTemplate#GridViewCellTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewcelltemplate)]  
  
 [!code-xaml[ListViewTemplate#CellTemplateProperty](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#celltemplateproperty)]  
  
<a name="StylingaListView"></a>
## <a name="styling-a-listview-that-implements-a-gridview"></a>Appliquer un style à un ListView implémentant un GridView  
 Le <xref:System.Windows.Controls.ListView> contrôle <xref:System.Windows.Controls.ListViewItem> contient des objets, qui représentent les éléments de données qui sont affichés. Vous pouvez utiliser les propriétés suivantes pour définir le contenu et le style des éléments de données :  
  
- Sur <xref:System.Windows.Controls.ListView> le contrôle, <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> <xref:System.Windows.Controls.ItemsControl.ItemTemplateSelector%2A>utilisez <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> le , , et les propriétés.  
  
- Sur <xref:System.Windows.Controls.ListViewItem> le contrôle, <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> <xref:System.Windows.Controls.ContentControl.ContentTemplateSelector%2A> utilisez le et les propriétés.  
  
 Pour éviter les problèmes <xref:System.Windows.Controls.GridView>d’alignement entre <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> les cellules dans un , n’utilisez <xref:System.Windows.Controls.ListView>pas les propriétés pour définir ou ajouter du contenu qui affecte la largeur d’un élément dans un . Par exemple, un problème d’alignement <xref:System.Windows.FrameworkElement.Margin%2A> peut <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>se produire lorsque vous définissez la propriété dans le . Pour spécifier les propriétés ou <xref:System.Windows.Controls.GridView>définir le contenu <xref:System.Windows.Controls.GridView> qui affecte la largeur <xref:System.Windows.Controls.GridViewColumn>des éléments dans un , utilisez les propriétés de la classe et de ses classes connexes, telles que .  
  
 Pour plus d’informations <xref:System.Windows.Controls.GridView> sur la façon d’utiliser et ses classes de soutien, voir [GridView Aperçu](gridview-overview.md).  
  
 Si vous <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> définissez <xref:System.Windows.Controls.ListView> un pour <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>un contrôle et <xref:System.Windows.Controls.ContentPresenter> définissez également un <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> , vous devez inclure un dans le style afin que le fonctionne correctement.  
  
 N’utilisez <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> pas <xref:System.Windows.Controls.Control.VerticalContentAlignment%2A> le <xref:System.Windows.Controls.ListView> et les propriétés <xref:System.Windows.Controls.GridView>pour le contenu qui est affiché en utilisant un . Pour spécifier l’alignement <xref:System.Windows.Controls.GridView>du contenu <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A>dans une colonne d’un , définir un .  
  
<a name="UsingtheSameViewMoreThanOnce"></a>
## <a name="sharing-the-same-view-mode"></a>Partage du mode d’affichage  
 Deux <xref:System.Windows.Controls.ListView> contrôles ne peuvent pas partager le même mode de vue en même temps. Si vous essayez d’utiliser le même <xref:System.Windows.Controls.ListView> mode de vue avec plus d’un contrôle, une exception se produit.  
  
 Pour spécifier un mode de vue <xref:System.Windows.Controls.ListView>qui peut être utilisé simultanément par plus d’un , utilisez des modèles ou des styles.
  
<a name="CreatingaCustomView"></a>
## <a name="creating-a-custom-view-mode"></a>Créer un mode d’affichage personnalisé  
 Des vues <xref:System.Windows.Controls.GridView> personnalisées comme <xref:System.Windows.Controls.ViewBase> sont dérivées de la classe abstraite, <xref:System.Windows.Controls.ListViewItem> qui fournit les outils pour afficher des éléments de données qui sont représentés comme des objets.
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Controls.GridView>
- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.ListViewItem>
- <xref:System.Windows.Data.Binding>
- [Vue d’ensemble de GridView](gridview-overview.md)
- [Sujets comment se passer](listview-how-to-topics.md)
- [Commandes](../advanced/optimizing-performance-controls.md)
