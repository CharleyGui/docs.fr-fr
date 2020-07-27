---
title: DataGrid
description: Découvrez comment le contrôle DataGrid vous permet d’afficher et de modifier des données de différentes sources, telles qu’une base de données, une requête LINQ ou toute autre source de données pouvant être liée.
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
ms.openlocfilehash: 3db49c12fcb363ef7f99e5c69beae09ab05addcf
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168319"
---
# <a name="datagrid"></a>DataGrid
Le <xref:System.Windows.Controls.DataGrid> contrôle vous permet d’afficher et de modifier des données à partir de nombreuses sources différentes, par exemple à partir d’une base de données SQL, d’une requête LINQ ou de toute autre source de données pouvant être liée. Pour plus d’informations, consultez [Vue d’ensemble de la liaison de ressources](../data/binding-sources-overview.md).  
  
 Les colonnes peuvent afficher du texte, des contrôles, tels qu’un <xref:System.Windows.Controls.ComboBox> ou tout autre contenu WPF, comme des images, des boutons ou tout contenu contenu dans un modèle. Vous pouvez utiliser un <xref:System.Windows.Controls.DataGridTemplateColumn> pour afficher les données définies dans un modèle. Le tableau suivant répertorie les types de colonnes qui sont fournis par défaut.  
  
|Type de colonne généré|Type de données|  
|---------------------------|---------------|  
|<xref:System.Windows.Controls.DataGridTextColumn>|<xref:System.String>|  
|<xref:System.Windows.Controls.DataGridCheckBoxColumn>|<xref:System.Boolean>|  
|<xref:System.Windows.Controls.DataGridComboBoxColumn>|<xref:System.Enum>|  
|<xref:System.Windows.Controls.DataGridHyperlinkColumn>|<xref:System.Uri>|  
  
 <xref:System.Windows.Controls.DataGrid>peut être personnalisée en apparence, telle que la police, la couleur et la taille des cellules. <xref:System.Windows.Controls.DataGrid>prend en charge toutes les fonctionnalités de création de styles et de création de modèles d’autres contrôles WPF. <xref:System.Windows.Controls.DataGrid>comprend également les comportements par défaut et personnalisables pour la modification, le tri et la validation.  
  
 Le tableau suivant répertorie quelques-unes des tâches courantes pour <xref:System.Windows.Controls.DataGrid> et comment les accomplir. En affichant l’API associée, vous trouverez plus d’informations et des exemples de code.  
  
|Scénario|Approche|  
|--------------|--------------|  
|Alternance des couleurs d’arrière-plan|Affectez <xref:System.Windows.Controls.ItemsControl.AlternationIndex%2A> à la propriété la valeur 2 ou plus, puis affectez <xref:System.Windows.Media.Brush> à les <xref:System.Windows.Controls.DataGrid.RowBackground%2A> <xref:System.Windows.Controls.DataGrid.AlternatingRowBackground%2A> Propriétés et.|  
|Définir le comportement de sélection de cellule et de ligne|Définissez les propriétés <xref:System.Windows.Controls.DataGrid.SelectionMode%2A> et <xref:System.Windows.Controls.DataGrid.SelectionUnit%2A>.|  
|Personnaliser l’apparence visuelle des en-têtes, des cellules et des lignes|Appliquez un nouveau <xref:System.Windows.Style> aux <xref:System.Windows.Controls.DataGrid.ColumnHeaderStyle%2A> Propriétés, <xref:System.Windows.Controls.DataGrid.RowHeaderStyle%2A> , <xref:System.Windows.Controls.DataGrid.CellStyle%2A> ou <xref:System.Windows.Controls.DataGrid.RowStyle%2A> .|  
|Définir les options de dimensionnement|Définissez les <xref:System.Windows.FrameworkElement.Height%2A> <xref:System.Windows.FrameworkElement.MaxHeight%2A> Propriétés,, <xref:System.Windows.FrameworkElement.MinHeight%2A> ,, <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.FrameworkElement.MaxWidth%2A> ou <xref:System.Windows.FrameworkElement.MinWidth%2A> . Pour plus d’informations, consultez [options de dimensionnement dans le contrôle DataGrid](sizing-options-in-the-datagrid-control.md).|  
|Accéder aux éléments sélectionnés|Vérifiez la <xref:System.Windows.Controls.DataGrid.SelectedCells%2A> propriété pour récupérer les cellules sélectionnées et la <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems%2A> propriété pour récupérer les lignes sélectionnées. Pour plus d’informations, consultez <xref:System.Windows.Controls.DataGrid.SelectedCells%2A>.|  
|Personnaliser les interactions de l’utilisateur final|Définissez les <xref:System.Windows.Controls.DataGrid.CanUserAddRows%2A> <xref:System.Windows.Controls.DataGrid.CanUserDeleteRows%2A> Propriétés,, <xref:System.Windows.Controls.DataGrid.CanUserReorderColumns%2A> ,, <xref:System.Windows.Controls.DataGrid.CanUserResizeColumns%2A> <xref:System.Windows.Controls.DataGrid.CanUserResizeRows%2A> et <xref:System.Windows.Controls.DataGrid.CanUserSortColumns%2A> .|  
|Annuler ou modifier les colonnes générées automatiquement|Gérez l' <xref:System.Windows.Controls.DataGrid.AutoGeneratingColumn> événement.|  
|Figer une colonne|Affectez la valeur <xref:System.Windows.Controls.DataGrid.FrozenColumnCount%2A> 1 à la propriété et déplacez la colonne à la position la plus à gauche en affectant à la propriété la valeur <xref:System.Windows.Controls.DataGridColumn.DisplayIndex%2A> 0.|  
|Utiliser des données XML comme source de données|Liez le <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> sur le <xref:System.Windows.Controls.DataGrid> à la requête XPath qui représente la collection d’éléments. Créez chaque colonne dans le <xref:System.Windows.Controls.DataGrid> . Liez chaque colonne en définissant le XPath sur la liaison à la requête qui obtient la propriété sur la source de l’élément. Pour obtenir un exemple, consultez <xref:System.Windows.Controls.DataGridTextColumn>.|  
  
## <a name="related-topics"></a>Rubriques connexes  
  
|Titre|Description|  
|-----------|-----------------|  
|[Procédure pas à pas : afficher des données à partir d’une base de données SQL Server dans un contrôle DataGrid](walkthrough-display-data-from-a-sql-server-database-in-a-datagrid-control.md)|Décrit comment configurer un nouveau projet WPF, ajouter un élément Entity Framework, définir la source et afficher les données dans un <xref:System.Windows.Controls.DataGrid> .|  
|[Procédure : ajouter des détails de ligne à un contrôle DataGrid](how-to-add-row-details-to-a-datagrid-control.md)|Décrit comment créer des détails de ligne pour un <xref:System.Windows.Controls.DataGrid> .|  
|[Procédure : implémenter la validation avec le contrôle DataGrid](how-to-implement-validation-with-the-datagrid-control.md)|Décrit comment valider des valeurs dans des <xref:System.Windows.Controls.DataGrid> cellules et des lignes et comment afficher des commentaires de validation.|  
|[Comportement par défaut du clavier et de la souris dans le contrôle DataGrid](default-keyboard-and-mouse-behavior-in-the-datagrid-control.md)|Décrit comment interagir avec le <xref:System.Windows.Controls.DataGrid> contrôle à l’aide du clavier et de la souris.|  
|[Procédure : regrouper, trier et filtrer des données dans le contrôle DataGrid](how-to-group-sort-and-filter-data-in-the-datagrid-control.md)|Décrit comment afficher des données d’un <xref:System.Windows.Controls.DataGrid> de différentes manières en regroupant, triant et filtrant les données.|  
|[Options de dimensionnement dans le contrôle DataGrid](sizing-options-in-the-datagrid-control.md)|Décrit comment contrôler le dimensionnement absolu et automatique dans le <xref:System.Windows.Controls.DataGrid> .|  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Controls.DataGrid>
- [Application d'un style et création de modèles](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [Vue d’ensemble de la liaison de données](../../../desktop-wpf/data/data-binding-overview.md)
- [Vue d'ensemble des modèles de données](../data/data-templating-overview.md)
- [Contrôles](index.md)
- [Modèle de contenu WPF](wpf-content-model.md)
