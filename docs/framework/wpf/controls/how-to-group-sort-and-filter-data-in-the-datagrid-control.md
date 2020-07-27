---
title: 'Comment : regrouper, trier et filtrer des données dans le contrôle DataGrid'
description: Découvrez comment lier un contrôle Windows Presentation Foundation DataGrid à un CollectionView qui prend en charge le regroupement, le tri et le filtrage des données dans les vues.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGrid [WPF], sort
- DataGrid [WPF], group
- DataGrid [WPF], filter
ms.assetid: 03345e85-89e3-4aec-9ed0-3b80759df770
ms.openlocfilehash: 072e5a104a91faa40bb54f2a3fc4ed6188e1112e
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87167664"
---
# <a name="how-to-group-sort-and-filter-data-in-the-datagrid-control"></a>Comment : regrouper, trier et filtrer des données dans le contrôle DataGrid

Il est souvent utile d’afficher les données d’un <xref:System.Windows.Controls.DataGrid> de différentes manières en regroupant, triant et filtrant les données. Pour regrouper, trier et filtrer les données d’un <xref:System.Windows.Controls.DataGrid> , vous devez les lier à un <xref:System.Windows.Data.CollectionView> qui prend en charge ces fonctions. Vous pouvez ensuite utiliser les données dans le <xref:System.Windows.Data.CollectionView> sans affecter les données sources sous-jacentes. Les modifications apportées à la vue de collection sont reflétées dans l' <xref:System.Windows.Controls.DataGrid> interface utilisateur.

La <xref:System.Windows.Data.CollectionView> classe fournit des fonctionnalités de regroupement et de tri pour une source de données qui implémente l' <xref:System.Collections.IEnumerable> interface. La <xref:System.Windows.Data.CollectionViewSource> classe vous permet de définir les propriétés d’un <xref:System.Windows.Data.CollectionView> à partir de XAML.

Dans cet exemple, une collection d' `Task` objets est liée à un <xref:System.Windows.Data.CollectionViewSource> . Le <xref:System.Windows.Data.CollectionViewSource> est utilisé comme <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> pour le <xref:System.Windows.Controls.DataGrid> . Le regroupement, le tri et le filtrage sont effectués sur le <xref:System.Windows.Data.CollectionViewSource> et sont affichés dans l' <xref:System.Windows.Controls.DataGrid> interface utilisateur.

![Données groupées dans un DataGrid](././media/wpf-datagridgroups.png "WPF_DataGridGroups") Données groupées dans un DataGrid

## <a name="using-a-collectionviewsource-as-an-itemssource"></a>Utilisation d’un CollectionViewSource comme ItemsSource

Pour regrouper, trier et filtrer des données dans un <xref:System.Windows.Controls.DataGrid> contrôle, vous devez lier le <xref:System.Windows.Controls.DataGrid> à un <xref:System.Windows.Data.CollectionView> qui prend en charge ces fonctions. Dans cet exemple, <xref:System.Windows.Controls.DataGrid> est lié à un <xref:System.Windows.Data.CollectionViewSource> qui fournit ces fonctions pour un <xref:System.Collections.Generic.List%601> d' `Task` objets.

### <a name="to-bind-a-datagrid-to-a-collectionviewsource"></a>Pour lier un DataGrid à un CollectionViewSource

1. Créez une collection de données qui implémente l' <xref:System.Collections.IEnumerable> interface.

    Si vous utilisez <xref:System.Collections.Generic.List%601> pour créer votre collection, vous devez créer une nouvelle classe qui hérite de <xref:System.Collections.Generic.List%601> au lieu d’instancier une instance de <xref:System.Collections.Generic.List%601> . Cela vous permet d’effectuer une liaison de données à la collection en XAML.

    > [!NOTE]
    > Les objets de la collection doivent implémenter l' <xref:System.ComponentModel.INotifyPropertyChanged> interface modifiée et l' <xref:System.ComponentModel.IEditableObject> interface afin que le <xref:System.Windows.Controls.DataGrid> réponde correctement aux modifications et modifications de propriété. Pour plus d’informations, consultez [Implémenter la notification des modifications de propriétés](../data/how-to-implement-property-change-notification.md).

    [!code-csharp[DataGrid_GroupSortFilter#101](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#101)]
    [!code-vb[DataGrid_GroupSortFilter#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#101)]

2. Dans XAML, créez une instance de la classe de collection et définissez la [directive x :Key](../../../desktop-wpf/xaml-services/xkey-directive.md).

3. Dans XAML, créez une instance de la <xref:System.Windows.Data.CollectionViewSource> classe, définissez la [directive x :Key](../../../desktop-wpf/xaml-services/xkey-directive.md)et définissez l’instance de votre classe de collection en tant que <xref:System.Windows.Data.CollectionViewSource.Source%2A> .

    [!code-xaml[DataGrid_GroupSortFilter#201](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/WindowSnips1.xaml#201)]

4. Créez une instance de la <xref:System.Windows.Controls.DataGrid> classe et affectez <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> à la propriété la valeur <xref:System.Windows.Data.CollectionViewSource> .

    [!code-xaml[DataGrid_GroupSortFilter#002](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#002)]

5. Pour accéder à <xref:System.Windows.Data.CollectionViewSource> à partir de votre code, utilisez la <xref:System.Windows.Data.CollectionViewSource.GetDefaultView%2A> méthode pour obtenir une référence à <xref:System.Windows.Data.CollectionViewSource> .

    [!code-csharp[DataGrid_GroupSortFilter#102](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#102)]
    [!code-vb[DataGrid_GroupSortFilter#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#102)]

## <a name="grouping-items-in-a-datagrid"></a>Regroupement d’éléments dans un DataGrid

Pour spécifier la façon dont les éléments sont regroupés dans un <xref:System.Windows.Controls.DataGrid> , vous utilisez le <xref:System.Windows.Data.PropertyGroupDescription> type pour regrouper les éléments dans la vue source.

### <a name="to-group-items-in-a-datagrid-using-xaml"></a>Pour regrouper des éléments dans un DataGrid à l’aide de XAML

1. Créez un <xref:System.Windows.Data.PropertyGroupDescription> qui spécifie la propriété à regrouper. Vous pouvez spécifier la propriété en XAML ou dans le code.

   1. En XAML, affectez au le <xref:System.Windows.Data.PropertyGroupDescription.PropertyName%2A> nom de la propriété à regrouper.

   2. Dans le code, transmettez le nom de la propriété à regrouper sur le constructeur.

2. Ajoutez <xref:System.Windows.Data.PropertyGroupDescription> à la <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A?displayProperty=nameWithType> collection.

3. Ajoutez des instances supplémentaires de <xref:System.Windows.Data.PropertyGroupDescription> à la <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A> collection pour ajouter d’autres niveaux de regroupement.

    [!code-xaml[DataGrid_GroupSortFilter#012](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#012)]
    [!code-csharp[DataGrid_GroupSortFilter#112](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#112)]
    [!code-vb[DataGrid_GroupSortFilter#112](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#112)]

4. Pour supprimer un groupe, supprimez <xref:System.Windows.Data.PropertyGroupDescription> de la <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A> collection.

5. Pour supprimer tous les groupes, appelez la <xref:System.Collections.ObjectModel.Collection%601.Clear%2A> méthode de la <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A> collection.

    [!code-csharp[DataGrid_GroupSortFilter#114](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#114)]
    [!code-vb[DataGrid_GroupSortFilter#114](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#114)]

Lorsque des éléments sont regroupés dans le <xref:System.Windows.Controls.DataGrid> , vous pouvez définir un <xref:System.Windows.Controls.GroupStyle> qui spécifie l’apparence de chaque groupe. Vous appliquez le <xref:System.Windows.Controls.GroupStyle> en l’ajoutant à la <xref:System.Windows.Controls.ItemsControl.GroupStyle%2A> collection du DataGrid. Si vous disposez de plusieurs niveaux de regroupement, vous pouvez appliquer différents styles à chaque niveau de groupe. Les styles sont appliqués dans l’ordre dans lequel ils sont définis. Par exemple, si vous définissez deux styles, le premier sera appliqué aux groupes de lignes de niveau supérieur. Le deuxième style est appliqué à tous les groupes de lignes au deuxième niveau et inférieur. Du <xref:System.Windows.FrameworkElement.DataContext%2A> <xref:System.Windows.Controls.GroupStyle> est le <xref:System.Windows.Data.CollectionViewGroup> que le groupe représente.

### <a name="to-change-the-appearance-of-row-group-headers"></a>Pour modifier l’apparence des en-têtes de groupe de lignes

1. Créez un <xref:System.Windows.Controls.GroupStyle> qui définit l’apparence du groupe de lignes.

2. Placez le <xref:System.Windows.Controls.GroupStyle> à l’intérieur des `<DataGrid.GroupStyle>` balises.

    [!code-xaml[DataGrid_GroupSortFilter#003](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#003)]

## <a name="sorting-items-in-a-datagrid"></a>Tri des éléments dans un DataGrid

Pour spécifier la façon dont les éléments sont triés dans un <xref:System.Windows.Controls.DataGrid> , vous utilisez le <xref:System.ComponentModel.SortDescription> type pour trier les éléments dans la vue source.

### <a name="to-sort-items-in-a-datagrid"></a>Pour trier des éléments dans un DataGrid

1. Créez un <xref:System.ComponentModel.SortDescription> qui spécifie la propriété selon laquelle effectuer le tri. Vous pouvez spécifier la propriété en XAML ou dans le code.

    1. En XAML, définissez <xref:System.ComponentModel.SortDescription.PropertyName%2A> sur le nom de la propriété sur laquelle effectuer le tri.

    2. Dans le code, transmettez le nom de la propriété à trier par et au <xref:System.ComponentModel.ListSortDirection> constructeur.

2. Ajoutez <xref:System.ComponentModel.SortDescription> à la <xref:System.Windows.Data.CollectionViewSource.SortDescriptions%2A?displayProperty=nameWithType> collection.

3. Ajoutez des instances supplémentaires de <xref:System.ComponentModel.SortDescription> à la <xref:System.Windows.Data.CollectionViewSource.SortDescriptions%2A> collection pour effectuer un tri par propriétés supplémentaires.

    [!code-xaml[DataGrid_GroupSortFilter#011](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#011)]
    [!code-csharp[DataGrid_GroupSortFilter#211](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/WindowSnips1.xaml.cs#211)]
    [!code-vb[DataGrid_GroupSortFilter#211](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#211)]

## <a name="filtering-items-in-a-datagrid"></a>Filtrage d’éléments dans un DataGrid

Pour filtrer des éléments dans un <xref:System.Windows.Controls.DataGrid> à l’aide d’un <xref:System.Windows.Data.CollectionViewSource> , vous fournissez la logique de filtrage dans le gestionnaire pour l' <xref:System.Windows.Data.CollectionViewSource.Filter?displayProperty=nameWithType> événement.

### <a name="to-filter-items-in-a-datagrid"></a>Pour filtrer des éléments dans un DataGrid

1. Ajoutez un gestionnaire pour l' <xref:System.Windows.Data.CollectionViewSource.Filter?displayProperty=nameWithType> événement.

2. Dans le <xref:System.Windows.Data.CollectionViewSource.Filter> Gestionnaire d’événements, définissez la logique de filtrage.

    Le filtre est appliqué chaque fois que la vue est actualisée.

    [!code-xaml[DataGrid_GroupSortFilter#013](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#013)]
    [!code-csharp[DataGrid_GroupSortFilter#113](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#113)]
    [!code-vb[DataGrid_GroupSortFilter#113](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#113)]

Vous pouvez également filtrer les éléments d’un <xref:System.Windows.Controls.DataGrid> en créant une méthode qui fournit la logique de filtrage et en définissant la <xref:System.Windows.Data.CollectionView.Filter%2A?displayProperty=nameWithType> propriété pour appliquer le filtre. Pour voir un exemple de cette méthode, consultez [filtrer des données dans une vue](../data/how-to-filter-data-in-a-view.md).

## <a name="example"></a>Exemple

L’exemple suivant illustre le regroupement, le tri et le filtrage des `Task` données dans un <xref:System.Windows.Data.CollectionViewSource> et l’affichage des données groupées, triées et filtrées `Task` dans un <xref:System.Windows.Controls.DataGrid> . Le <xref:System.Windows.Data.CollectionViewSource> est utilisé comme <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> pour le <xref:System.Windows.Controls.DataGrid> . Le regroupement, le tri et le filtrage sont effectués sur le <xref:System.Windows.Data.CollectionViewSource> et sont affichés dans l' <xref:System.Windows.Controls.DataGrid> interface utilisateur.

Pour tester cet exemple, vous devez ajuster le nom de DGGroupSortFilterExample pour qu’il corresponde au nom de votre projet. Si vous utilisez Visual Basic, vous devrez remplacer le nom de la classe par <xref:System.Windows.Window> ce qui suit.

`<Window x:Class="MainWindow"`

[!code-xaml[DataGrid_GroupSortFilter#000](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#000)]
[!code-csharp[DataGrid_GroupSortFilter#100](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#100)]
[!code-vb[DataGrid_GroupSortFilter#100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#100)]

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble de la liaison de données](../../../desktop-wpf/data/data-binding-overview.md)
- [Créer et effectuer une liaison à un ObservableCollection](../data/how-to-create-and-bind-to-an-observablecollection.md)
- [Filtrer des données dans une vue](../data/how-to-filter-data-in-a-view.md)
- [Trier des données dans une vue](../data/how-to-sort-data-in-a-view.md)
- [Trier et regrouper des données à l’aide d’une vue en XAML](../data/how-to-sort-and-group-data-using-a-view-in-xaml.md)
