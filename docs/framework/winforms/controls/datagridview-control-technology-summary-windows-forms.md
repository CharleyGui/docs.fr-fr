---
title: Résumé de la technologie du contrôle DataGridView
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], about DataGridView control
- data grids [Windows Forms], about data grids
ms.assetid: 094498c3-a126-4a3f-83fe-f69e96c7717b
ms.openlocfilehash: 18eebd067df9768e14cc81258184551d00dd1402
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742476"
---
# <a name="datagridview-control-technology-summary-windows-forms"></a>Résumé de la technologie du contrôle DataGridView (Windows Forms)
Cette rubrique rassemble des informations sur le contrôle `DataGridView` et les classes qui prennent en charge son utilisation.  
  
 L’affichage de données dans un format tabulaire est une tâche que vous êtes susceptible d’effectuer fréquemment. Le contrôle `DataGridView` est conçu pour être une solution complète pour la présentation de données dans une grille.  
  
## <a name="keywords"></a>Mots clés  
 DataGridView, BindingSource, table, cellule, liaison de données, mode virtuel  
  
## <a name="namespaces"></a>Espaces de noms  
 <xref:System.Windows.Forms?displayProperty=nameWithType>  
  
 <xref:System.Data?displayProperty=nameWithType>  
  
## <a name="related-technologies"></a>Technologies connexes  
 `BindingSource`  
  
## <a name="background"></a>Arrière-plan  
 Les concepteurs de l’interface utilisateur ont souvent besoin d’afficher des données tabulaires pour les utilisateurs. Le .NET Framework permet d’afficher des données dans une table ou une grille de plusieurs façons. Le contrôle `DataGridView` représente l’évolution la plus récente de cette technologie pour les applications Windows Forms.  
  
 Le contrôle `DataGridView` peut afficher des lignes de données à partir d’un magasin de données. De nombreux types de magasins de données sont pris en charge. Le magasin de données peut contenir des données simples et non typées, telles qu’un tableau unidimensionnel, ou peut contenir des données typées, telles qu’un <xref:System.Data.DataSet>. Pour plus d’informations, consultez [Comment : lier des données au contrôle DataGridView Windows Forms](how-to-bind-data-to-the-windows-forms-datagridview-control.md).  
  
 Le contrôle `DataGridView` offre un moyen puissant et flexible d'afficher des données sous forme de tableau. Vous pouvez utiliser le contrôle pour afficher des vues en lecture seule ou modifiables de petits ou très grands ensembles de données.  
  
 Vous pouvez étendre le contrôle `DataGridView` de plusieurs façons pour générer un comportement personnalisé dans vos applications. Par exemple, vous pouvez spécifier par programmation vos propres algorithmes de tri et vous pouvez créer vos propres types de cellules. Vous pouvez facilement personnaliser l'apparence du contrôle `DataGridView` en choisissant parmi plusieurs propriétés. De nombreux types de magasins de données peuvent être utilisés comme source de données, ou le contrôle `DataGridView` peut fonctionner sans source de données liée.  
  
## <a name="implementing-datagridview-classes"></a>Implémentation des classes DataGridView  
 Il existe plusieurs façons de tirer parti des fonctionnalités d’extensibilité du contrôle `DataGridView`. Vous pouvez personnaliser de nombreux aspects du contrôle par le biais des événements et des propriétés, mais certaines personnalisations nécessitent que vous dépuissiez créer des classes dérivées de classes de `DataGridView` existantes.  
  
 Les classes de base les plus utilisées sont `DataGridViewCell` et `DataGridViewColumn`. Vous pouvez dériver votre propre classe de cellule à partir de `DataGridViewCell` ou de l’une de ses classes enfants. Bien que vous puissiez ajouter n’importe quel type de cellule à n’importe quelle colonne, vous dériverez généralement une classe de colonne associée à partir de `DataGridViewColumn` qui héberge des cellules de votre type de cellule personnalisé par défaut.  
  
 Vous pouvez implémenter l’interface `IDataGridViewEditingCell` dans votre classe de cellule dérivée pour créer un type de cellule qui dispose d’une fonctionnalité d’édition, mais qui n’héberge pas de contrôle en mode édition. Pour créer un contrôle que vous pouvez héberger dans une cellule en mode édition, vous pouvez implémenter l’interface `IDataGridViewEditingControl` dans une classe dérivée de <xref:System.Windows.Forms.Control>.  
  
 Pour plus d’informations, consultez [Comment : personnaliser des cellules et des colonnes dans le contrôle DataGridView Windows Forms en étendant leur comportement et leur apparence](customize-cells-and-columns-in-the-datagrid-by-extending-behavior.md) et [Comment : héberger des contrôles dans Windows Forms des cellules DataGridView](how-to-host-controls-in-windows-forms-datagridview-cells.md).  
  
## <a name="datagridview-classes-at-a-glance"></a>Vue d’ensemble des classes DataGridView  
 <xref:System.Windows.Forms>  
  
|Zone technologique|Classes/interfaces/éléments de configuration|  
|---------------------|-------------------------------------------------|  
|Liaison de données|<xref:System.Windows.Forms.BindingSource>|  
|Présentation des données|<xref:System.Windows.Forms.DataGridView><br /><br /> classes <xref:System.Windows.Forms.DataGridViewCell> et dérivées<br /><br /> classes <xref:System.Windows.Forms.DataGridViewRow> et dérivées<br /><br /> classes <xref:System.Windows.Forms.DataGridViewColumn> et dérivées<br /><br /> <xref:System.Windows.Forms.DataGridViewCellStyle>|  
|Extensibilité <xref:System.Windows.Forms.DataGridView>|classes <xref:System.Windows.Forms.DataGridViewCell> et dérivées<br /><br /> classes <xref:System.Windows.Forms.DataGridViewColumn> et dérivées<br /><br /> <xref:System.Windows.Forms.IDataGridViewEditingCell><br /><br /> <xref:System.Windows.Forms.IDataGridViewEditingControl>|  
  
## <a name="whats-new"></a>Nouveautés  
 Le contrôle <xref:System.Windows.Forms.DataGridView> est conçu pour être une solution complète permettant d’afficher des données tabulaires avec Windows Forms. Vous devez envisager d’utiliser le contrôle <xref:System.Windows.Forms.DataGridView> avant d’autres solutions, comme <xref:System.Windows.Forms.DataGrid>, lorsque vous créez une nouvelle application. Pour plus d’informations, consultez [Différences entre les contrôles DataGridView et DataGrid Windows Forms](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Le contrôle <xref:System.Windows.Forms.DataGridView> peut fonctionner en étroite collaboration avec le composant <xref:System.Windows.Forms.BindingSource>. Ce composant est conçu pour être la source de données principale d’un formulaire. Il peut gérer l’interaction entre un contrôle de <xref:System.Windows.Forms.DataGridView> et sa source de données, quel que soit le type de source de données.  
  
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble du contrôle DataGridView](datagridview-control-overview-windows-forms.md)
- [Architecture du contrôle DataGridView](datagridview-control-architecture-windows-forms.md)
- [Protection des informations de connexion](../../data/adonet/protecting-connection-information.md)
