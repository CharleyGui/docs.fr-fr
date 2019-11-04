---
title: DataGrid
ms.date: 03/30/2017
helpviewer_keywords:
- DataGrid column types [WPF]
- DataGrid scenarios [WPF]
- DataGrid control [WPF]
- controls [WPF], DataGrid
- DataGrid [WPF], common tasks for
- DataGrid [WPF], customizing the appearance of
- DataGrid columns [WPF], using
ms.assetid: bf89ea63-79b6-422b-bc9f-0485ad803216
ms.openlocfilehash: f0887f36990de483139a9fde1472a78737cb7b72
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460389"
---
# <a name="datagrid"></a>DataGrid
Le contrôle <xref:System.Windows.Controls.DataGrid> vous permet d’afficher et de modifier des données de nombreuses sources différentes, par exemple à partir d’une base de données SQL, d’une requête LINQ ou de toute autre source de données pouvant être liée. Pour plus d’informations, consultez [Vue d’ensemble de la liaison de ressources](../data/binding-sources-overview.md).  
  
 Les colonnes peuvent afficher du texte, des contrôles, tels qu’un <xref:System.Windows.Controls.ComboBox>ou tout autre contenu WPF, comme des images, des boutons ou tout contenu contenu dans un modèle. Vous pouvez utiliser un <xref:System.Windows.Controls.DataGridTemplateColumn> pour afficher les données définies dans un modèle. Le tableau suivant répertorie les types de colonnes qui sont fournis par défaut.  
  
|Type de colonne généré|Type de données|  
|---------------------------|---------------|  
|<xref:System.Windows.Controls.DataGridTextColumn>|<xref:System.String>|  
|<xref:System.Windows.Controls.DataGridCheckBoxColumn>|<xref:System.Boolean>|  
|<xref:System.Windows.Controls.DataGridComboBoxColumn>|<xref:System.Enum>|  
|<xref:System.Windows.Controls.DataGridHyperlinkColumn>|<xref:System.Uri>|  
  
 les <xref:System.Windows.Controls.DataGrid> peuvent être personnalisées en apparence, telles que la police, la couleur et la taille des cellules. <xref:System.Windows.Controls.DataGrid> prend en charge toutes les fonctionnalités de création de styles et de modèles d’autres contrôles WPF. <xref:System.Windows.Controls.DataGrid> comprend également des comportements par défaut et personnalisables pour la modification, le tri et la validation.  
  
 Le tableau suivant répertorie quelques-unes des tâches courantes pour <xref:System.Windows.Controls.DataGrid> et comment les accomplir. En affichant l’API associée, vous trouverez plus d’informations et des exemples de code.  
  
|Scénario|Approche|  
|--------------|--------------|  
|Alternance des couleurs d’arrière-plan|Affectez à la propriété <xref:System.Windows.Controls.ItemsControl.AlternationIndex%2A> la valeur 2 ou plus, puis affectez une <xref:System.Windows.Media.Brush> aux propriétés <xref:System.Windows.Controls.DataGrid.RowBackground%2A> et <xref:System.Windows.Controls.DataGrid.AlternatingRowBackground%2A>.|  
|Définir le comportement de sélection de cellule et de ligne|Définissez les propriétés <xref:System.Windows.Controls.DataGrid.SelectionMode%2A> et <xref:System.Windows.Controls.DataGrid.SelectionUnit%2A>.|  
|Personnaliser l’apparence visuelle des en-têtes, des cellules et des lignes|Appliquez une nouvelle <xref:System.Windows.Style> aux propriétés <xref:System.Windows.Controls.DataGrid.ColumnHeaderStyle%2A>, <xref:System.Windows.Controls.DataGrid.RowHeaderStyle%2A>, <xref:System.Windows.Controls.DataGrid.CellStyle%2A>ou <xref:System.Windows.Controls.DataGrid.RowStyle%2A>.|  
|Définir les options de dimensionnement|Définissez les propriétés <xref:System.Windows.FrameworkElement.Height%2A>, <xref:System.Windows.FrameworkElement.MaxHeight%2A>, <xref:System.Windows.FrameworkElement.MinHeight%2A>, <xref:System.Windows.FrameworkElement.Width%2A>, <xref:System.Windows.FrameworkElement.MaxWidth%2A>ou <xref:System.Windows.FrameworkElement.MinWidth%2A>. Pour plus d’informations, consultez [options de dimensionnement dans le contrôle DataGrid](sizing-options-in-the-datagrid-control.md).|  
|Accéder aux éléments sélectionnés|Vérifiez la propriété <xref:System.Windows.Controls.DataGrid.SelectedCells%2A> pour récupérer les cellules sélectionnées et la propriété <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems%2A> pour récupérer les lignes sélectionnées. Pour plus d'informations, consultez <xref:System.Windows.Controls.DataGrid.SelectedCells%2A>.|  
|Personnaliser les interactions de l’utilisateur final|Définissez les propriétés <xref:System.Windows.Controls.DataGrid.CanUserAddRows%2A>, <xref:System.Windows.Controls.DataGrid.CanUserDeleteRows%2A>, <xref:System.Windows.Controls.DataGrid.CanUserReorderColumns%2A>, <xref:System.Windows.Controls.DataGrid.CanUserResizeColumns%2A>, <xref:System.Windows.Controls.DataGrid.CanUserResizeRows%2A>et <xref:System.Windows.Controls.DataGrid.CanUserSortColumns%2A>.|  
|Annuler ou modifier les colonnes générées automatiquement|Gérez l’événement <xref:System.Windows.Controls.DataGrid.AutoGeneratingColumn>.|  
|Figer une colonne|Affectez la valeur 1 à la propriété <xref:System.Windows.Controls.DataGrid.FrozenColumnCount%2A> et déplacez la colonne à la position la plus à gauche en affectant à la propriété <xref:System.Windows.Controls.DataGridColumn.DisplayIndex%2A> la valeur 0.|  
|Utiliser des données XML comme source de données|Liez le <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> sur le <xref:System.Windows.Controls.DataGrid> à la requête XPath qui représente la collection d’éléments. Créez chaque colonne dans la <xref:System.Windows.Controls.DataGrid>. Liez chaque colonne en définissant le XPath sur la liaison à la requête qui obtient la propriété sur la source de l’élément. Pour obtenir un exemple, consultez <xref:System.Windows.Controls.DataGridTextColumn>.|  
  
## <a name="related-topics"></a>Rubriques connexes  
  
|Titre|Description|  
|-----------|-----------------|  
|[Procédure pas à pas : affichage de données d'une base de données SQL Server dans un contrôle DataGrid](walkthrough-display-data-from-a-sql-server-database-in-a-datagrid-control.md)|Décrit comment configurer un nouveau projet WPF, ajouter un élément Entity Framework, définir la source et afficher les données dans une <xref:System.Windows.Controls.DataGrid>.|  
|[Guide pratique pour ajouter des détails de ligne à un contrôle DataGrid](how-to-add-row-details-to-a-datagrid-control.md)|Décrit comment créer des détails de ligne pour un <xref:System.Windows.Controls.DataGrid>.|  
|[Guide pratique pour implémenter la validation avec le contrôle DataGrid](how-to-implement-validation-with-the-datagrid-control.md)|Décrit comment valider des valeurs dans <xref:System.Windows.Controls.DataGrid> des cellules et des lignes, et comment afficher des commentaires de validation.|  
|[Comportement par défaut du clavier et de la souris dans le contrôle DataGrid](default-keyboard-and-mouse-behavior-in-the-datagrid-control.md)|Décrit comment interagir avec le contrôle <xref:System.Windows.Controls.DataGrid> à l’aide du clavier et de la souris.|  
|[Guide pratique pour grouper, trier et filtrer des données dans le contrôle DataGrid](how-to-group-sort-and-filter-data-in-the-datagrid-control.md)|Décrit comment afficher des données dans un <xref:System.Windows.Controls.DataGrid> de différentes manières en regroupant, triant et filtrant les données.|  
|[Options de dimensionnement dans le contrôle DataGrid](sizing-options-in-the-datagrid-control.md)|Décrit comment contrôler le dimensionnement absolu et automatique dans le <xref:System.Windows.Controls.DataGrid>.|  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Controls.DataGrid>
- [Application d’un style et création de modèles](styling-and-templating.md)
- [Vue d’ensemble de la liaison de données](../../../desktop-wpf/data/data-binding-overview.md)
- [Vue d’ensemble des modèles de données](../data/data-templating-overview.md)
- [Contrôles](index.md)
- [Modèle de contenu WPF](wpf-content-model.md)
