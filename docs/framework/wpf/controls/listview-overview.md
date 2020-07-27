---
title: Vue d'ensemble de ListView
description: En savoir plus sur le contrôle ListView Windows Presentation Foundation, qui fournit l’infrastructure permettant d’afficher des éléments de données dans différentes dispositions ou vues.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], ListView
- ListView controls [WPF], about ListView control
ms.assetid: 989e12b0-260e-4570-95c6-489284003ce2
ms.openlocfilehash: 419c6216f0af696ec71e7607c79c2db637caa785
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164556"
---
# <a name="listview-overview"></a>Vue d'ensemble de ListView
Le <xref:System.Windows.Controls.ListView> contrôle fournit l’infrastructure pour afficher un ensemble d’éléments de données dans différentes dispositions ou vues. Par exemple, un utilisateur peut souhaiter afficher des éléments de données dans un tableau et en trier les colonnes.  

<a name="WhatisaListView"></a>
## <a name="what-is-a-listview"></a>Qu’est qu’un contrôle ListView ?  
 Le <xref:System.Windows.Controls.ListView> contrôle est un <xref:System.Windows.Controls.ItemsControl> dérivé de <xref:System.Windows.Controls.ListBox> . En règle générale, ses éléments sont membres d’une collection de données et sont représentés en tant qu' <xref:System.Windows.Controls.ListViewItem> objets. Un <xref:System.Windows.Controls.ListViewItem> est un <xref:System.Windows.Controls.ContentControl> et ne peut contenir qu’un seul élément enfant. Toutefois, cet élément enfant peut être n’importe quel élément visuel.  
  
<a name="DefiningaListViewView"></a>
## <a name="defining-a-view-mode-for-a-listview"></a>Définition d’un mode d’affichage pour un ListView  
 Pour spécifier un mode d’affichage pour le contenu d’un <xref:System.Windows.Controls.ListView> contrôle, vous définissez la <xref:System.Windows.Controls.ListView.View%2A> propriété. Un mode d’affichage [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] fourni par est <xref:System.Windows.Controls.GridView> , qui affiche une collection d’éléments de données dans une table qui a des colonnes personnalisables.  
  
 L’exemple suivant montre comment définir un <xref:System.Windows.Controls.GridView> pour un <xref:System.Windows.Controls.ListView> contrôle qui affiche des informations sur les employés.  
  
 [!code-xaml[ListViewCode#ListViewEmployee](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#listviewemployee)]  
  
 L’illustration suivante montre le tableau créé par l’exemple précédent.  
  
 ![Capture d’écran montrant une sortie de contrôle ListView avec GridView.](./media/gridview-overview/listview-gridview-output.jpg)  
  
 Vous pouvez créer un mode d’affichage personnalisé en définissant une classe qui hérite de la <xref:System.Windows.Controls.ViewBase> classe. La <xref:System.Windows.Controls.ViewBase> classe fournit l’infrastructure dont vous avez besoin pour créer une vue personnalisée. Pour plus d’informations sur la création d’un affichage personnalisé, consultez la page [Créer un mode d’affichage personnalisé pour un ListView](how-to-create-a-custom-view-mode-for-a-listview.md).  
  
<a name="BindingDatatoaListView"></a>
## <a name="binding-data-to-a-listview"></a>Liaison des données à un contrôle ListView  
 Utilisez les <xref:System.Windows.Controls.ItemsControl.Items%2A> <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> Propriétés et pour spécifier des éléments pour un <xref:System.Windows.Controls.ListView> contrôle. L’exemple suivant affecte <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> à la propriété une collection de données appelée `EmployeeInfoDataSource` .  
  
 [!code-xaml[ListViewCode#ItemsSource](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#itemssource)]  
  
 Dans un <xref:System.Windows.Controls.GridView> , les <xref:System.Windows.Controls.GridViewColumn> objets sont liés à des champs de données spécifiés. L’exemple suivant lie un <xref:System.Windows.Controls.GridViewColumn> objet à un champ de données en spécifiant un <xref:System.Windows.Data.Binding> pour la <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> propriété.  
  
 [!code-csharp[ListViewCode#GridViewColumnProperties](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml.cs#gridviewcolumnproperties)]
 [!code-vb[ListViewCode#GridViewColumnProperties](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewCode/visualbasic/window1.xaml.vb#gridviewcolumnproperties)]
 [!code-xaml[ListViewCode#GridViewColumnProperties](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#gridviewcolumnproperties)]  
  
 Vous pouvez également spécifier un dans <xref:System.Windows.Data.Binding> le cadre d’une <xref:System.Windows.DataTemplate> définition que vous utilisez pour appliquer un style aux cellules d’une colonne. Dans l’exemple suivant, le <xref:System.Windows.DataTemplate> identifié avec un <xref:System.Windows.ResourceKey> définit le <xref:System.Windows.Data.Binding> pour un <xref:System.Windows.Controls.GridViewColumn> . Notez que cet exemple ne définit pas la <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> , car cela remplace la liaison spécifiée par <xref:System.Windows.DataTemplate> .  
  
 [!code-xaml[ListViewTemplate#GridViewCellTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewcelltemplate)]  
  
 [!code-xaml[ListViewTemplate#CellTemplateProperty](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#celltemplateproperty)]  
  
<a name="StylingaListView"></a>
## <a name="styling-a-listview-that-implements-a-gridview"></a>Appliquer un style à un ListView implémentant un GridView  
 Le <xref:System.Windows.Controls.ListView> contrôle contient des <xref:System.Windows.Controls.ListViewItem> objets qui représentent les éléments de données affichés. Vous pouvez utiliser les propriétés suivantes pour définir le contenu et le style des éléments de données :  
  
- Sur le <xref:System.Windows.Controls.ListView> contrôle, utilisez les <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> <xref:System.Windows.Controls.ItemsControl.ItemTemplateSelector%2A> Propriétés, et <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> .  
  
- Sur le <xref:System.Windows.Controls.ListViewItem> contrôle, utilisez les <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> <xref:System.Windows.Controls.ContentControl.ContentTemplateSelector%2A> Propriétés et.  
  
 Pour éviter les problèmes d’alignement entre les cellules d’un <xref:System.Windows.Controls.GridView> , n’utilisez pas le <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> pour définir des propriétés ou ajouter du contenu qui affecte la largeur d’un élément dans un <xref:System.Windows.Controls.ListView> . Par exemple, un problème d’alignement peut se produire lorsque vous définissez la <xref:System.Windows.FrameworkElement.Margin%2A> propriété dans <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> . Pour spécifier des propriétés ou définir le contenu qui affecte la largeur des éléments dans un <xref:System.Windows.Controls.GridView> , utilisez les propriétés de la <xref:System.Windows.Controls.GridView> classe et de ses classes connexes, telles que <xref:System.Windows.Controls.GridViewColumn> .  
  
 Pour plus d’informations sur l’utilisation de <xref:System.Windows.Controls.GridView> et de ses classes de prise en charge, consultez [vue d’ensemble de GridView](gridview-overview.md).  
  
 Si vous définissez un <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> pour un <xref:System.Windows.Controls.ListView> contrôle et que vous définissez également un <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> , vous devez inclure un <xref:System.Windows.Controls.ContentPresenter> dans le style afin que le <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> fonctionne correctement.  
  
 N’utilisez pas les <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> <xref:System.Windows.Controls.Control.VerticalContentAlignment%2A> Propriétés et pour <xref:System.Windows.Controls.ListView> le contenu qui s’affiche à l’aide d’un <xref:System.Windows.Controls.GridView> . Pour spécifier l’alignement du contenu dans une colonne d’un <xref:System.Windows.Controls.GridView> , définissez un <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A> .  
  
<a name="UsingtheSameViewMoreThanOnce"></a>
## <a name="sharing-the-same-view-mode"></a>Partage du mode d’affichage  
 Deux <xref:System.Windows.Controls.ListView> contrôles ne peuvent pas partager le même mode d’affichage en même temps. Si vous essayez d’utiliser le même mode d’affichage avec plusieurs <xref:System.Windows.Controls.ListView> contrôles, une exception se produit.  
  
 Pour spécifier un mode d’affichage qui peut être utilisé simultanément par plusieurs <xref:System.Windows.Controls.ListView> , utilisez des modèles ou des styles.
  
<a name="CreatingaCustomView"></a>
## <a name="creating-a-custom-view-mode"></a>Créer un mode d’affichage personnalisé  
 Les vues personnalisées comme <xref:System.Windows.Controls.GridView> sont dérivées de la <xref:System.Windows.Controls.ViewBase> classe abstraite, qui fournit les outils permettant d’afficher les éléments de données représentés en tant qu' <xref:System.Windows.Controls.ListViewItem> objets.
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Controls.GridView>
- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.ListViewItem>
- <xref:System.Windows.Data.Binding>
- [Vue d'ensemble de GridView](gridview-overview.md)
- [Rubriques Comment](listview-how-to-topics.md)
- [Contrôles](../advanced/optimizing-performance-controls.md)
