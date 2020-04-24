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
ms.openlocfilehash: cdf4bfff8182b62d55f56b823c7ff129de4f9f1c
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646115"
---
# <a name="datagrid"></a>DataGrid
Le <xref:System.Windows.Controls.DataGrid> contrôle vous permet d’afficher et de modifier des données provenant de nombreuses sources différentes, comme à partir d’une base de données SQL, d’une requête LINQ ou de toute autre source de données liants. Pour plus d’informations, consultez [Vue d’ensemble de la liaison de ressources](../data/binding-sources-overview.md).  
  
 Les colonnes peuvent afficher du <xref:System.Windows.Controls.ComboBox>texte, des contrôles, tels qu’un contenu WPF, ou tout autre contenu WPF, tels que des images, des boutons ou tout contenu contenu contenu dans un modèle. Vous pouvez <xref:System.Windows.Controls.DataGridTemplateColumn> utiliser un pour afficher des données définies dans un modèle. Le tableau suivant répertorie les types de colonnes qui sont fournis par défaut.  
  
|Type de colonne généré|Type de données|  
|---------------------------|---------------|  
|<xref:System.Windows.Controls.DataGridTextColumn>|<xref:System.String>|  
|<xref:System.Windows.Controls.DataGridCheckBoxColumn>|<xref:System.Boolean>|  
|<xref:System.Windows.Controls.DataGridComboBoxColumn>|<xref:System.Enum>|  
|<xref:System.Windows.Controls.DataGridHyperlinkColumn>|<xref:System.Uri>|  
  
 <xref:System.Windows.Controls.DataGrid>peut être personnalisé en apparence, comme la police cellulaire, la couleur et la taille. <xref:System.Windows.Controls.DataGrid>prend en charge toutes les fonctionnalités de style et de templating d’autres commandes WPF. <xref:System.Windows.Controls.DataGrid>comprend également des comportements par défaut et personnalisables pour l’édition, le tri et la validation.  
  
 Le tableau suivant répertorie <xref:System.Windows.Controls.DataGrid> certaines des tâches courantes et comment les accomplir. En visualisant l’API connexe, vous pouvez trouver plus d’informations et de code d’échantillon.  
  
|Scénario|Approche|  
|--------------|--------------|  
|Alterner les couleurs de fond|Réglez <xref:System.Windows.Controls.ItemsControl.AlternationIndex%2A> la propriété à 2 <xref:System.Windows.Media.Brush> ou <xref:System.Windows.Controls.DataGrid.RowBackground%2A> plus, puis attribuez un à la et <xref:System.Windows.Controls.DataGrid.AlternatingRowBackground%2A> les propriétés.|  
|Définir le comportement de sélection des cellules et des rangées|Définissez les propriétés <xref:System.Windows.Controls.DataGrid.SelectionMode%2A> et <xref:System.Windows.Controls.DataGrid.SelectionUnit%2A>.|  
|Personnalisez l’apparence visuelle des en-têtes, des cellules et des rangées|Appliquer un <xref:System.Windows.Style> nouveau <xref:System.Windows.Controls.DataGrid.ColumnHeaderStyle%2A> <xref:System.Windows.Controls.DataGrid.RowHeaderStyle%2A>sur <xref:System.Windows.Controls.DataGrid.CellStyle%2A>le <xref:System.Windows.Controls.DataGrid.RowStyle%2A> , , , ou des propriétés.|  
|Définir des options de dimensionnement|Réglez <xref:System.Windows.FrameworkElement.MaxHeight%2A> <xref:System.Windows.FrameworkElement.MinHeight%2A>les <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.FrameworkElement.Height%2A> <xref:System.Windows.FrameworkElement.MaxWidth%2A>, <xref:System.Windows.FrameworkElement.MinWidth%2A> , , , ou les propriétés. Pour plus d’informations, voir [Options de dimensionnement dans le contrôle DataGrid](sizing-options-in-the-datagrid-control.md).|  
|Accédez à certains éléments|Vérifiez <xref:System.Windows.Controls.DataGrid.SelectedCells%2A> la propriété pour obtenir <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems%2A> les cellules sélectionnées et la propriété pour obtenir les rangées sélectionnées. Pour plus d’informations, consultez <xref:System.Windows.Controls.DataGrid.SelectedCells%2A>.|  
|Personnaliser les interactions utilisateur final|Réglez <xref:System.Windows.Controls.DataGrid.CanUserDeleteRows%2A> <xref:System.Windows.Controls.DataGrid.CanUserReorderColumns%2A>les <xref:System.Windows.Controls.DataGrid.CanUserResizeColumns%2A> <xref:System.Windows.Controls.DataGrid.CanUserAddRows%2A> <xref:System.Windows.Controls.DataGrid.CanUserResizeRows%2A>, <xref:System.Windows.Controls.DataGrid.CanUserSortColumns%2A> , , , et les propriétés.|  
|Annuler ou modifier les colonnes générées automatiquement|Gérer <xref:System.Windows.Controls.DataGrid.AutoGeneratingColumn> l’événement.|  
|Congeler une colonne|Réglez la <xref:System.Windows.Controls.DataGrid.FrozenColumnCount%2A> propriété à 1 et déplacez la <xref:System.Windows.Controls.DataGridColumn.DisplayIndex%2A> colonne à la position la plus à gauche en fixant la propriété à 0.|  
|Utilisez les données XML comme source de données|Lier <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> la <xref:System.Windows.Controls.DataGrid> requête sur la XPath qui représente la collection d’objets. Créez chaque colonne <xref:System.Windows.Controls.DataGrid>dans le . Lier chaque colonne en définissant le XPath sur la liaison à la requête qui obtient la propriété sur la source de l’élément. Pour obtenir un exemple, consultez <xref:System.Windows.Controls.DataGridTextColumn>.|  
  
## <a name="related-topics"></a>Rubriques connexes  
  
|Intitulé|Description|  
|-----------|-----------------|  
|[Procédure pas à pas : affichage de données d'une base de données SQL Server dans un contrôle DataGrid](walkthrough-display-data-from-a-sql-server-database-in-a-datagrid-control.md)|Décrit comment mettre en place un nouveau projet WPF, ajouter un élément cadre <xref:System.Windows.Controls.DataGrid>d’entité, définir la source, et afficher les données dans un .|  
|[Comment : ajouter des détails de ligne à un contrôle DataGrid](how-to-add-row-details-to-a-datagrid-control.md)|Décrit comment créer des détails <xref:System.Windows.Controls.DataGrid>de ligne pour un .|  
|[Comment : implémenter la validation avec le contrôle DataGrid](how-to-implement-validation-with-the-datagrid-control.md)|Décrit comment valider <xref:System.Windows.Controls.DataGrid> les valeurs dans les cellules et les lignes, et afficher la rétroaction de validation.|  
|[Comportement par défaut du clavier et de la souris dans le contrôle DataGrid](default-keyboard-and-mouse-behavior-in-the-datagrid-control.md)|Décrit comment interagir avec <xref:System.Windows.Controls.DataGrid> le contrôle en utilisant le clavier et la souris.|  
|[Comment : grouper, trier et filtrer des données dans le contrôle DataGrid](how-to-group-sort-and-filter-data-in-the-datagrid-control.md)|Décrit comment afficher les <xref:System.Windows.Controls.DataGrid> données de différentes façons en groupant, en triant et en filtrant les données.|  
|[Options de dimensionnement dans le contrôle DataGrid](sizing-options-in-the-datagrid-control.md)|Décrit comment contrôler le dimensionnement <xref:System.Windows.Controls.DataGrid>absolu et automatique dans le .|  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Controls.DataGrid>
- [Application d’un style et création de modèles](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [Aperçu de la liaison de données](../../../desktop-wpf/data/data-binding-overview.md)
- [Vue d'ensemble des modèles de données](../data/data-templating-overview.md)
- [Contrôles](index.md)
- [Modèle de contenu WPF](wpf-content-model.md)
