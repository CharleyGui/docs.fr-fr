---
title: Vue d'ensemble du contrôle DataGrid
ms.date: 03/30/2017
f1_keywords:
- DataGrid
helpviewer_keywords:
- datasets [Windows Forms], binding to DataGrid control
- data binding [Windows Forms], DataGrid control
- columns [Windows Forms], DataGrid control
- data sources [Windows Forms], binding to DataGrid control
- tables [Windows Forms], binding to DataGrid control
- DataGrid control [Windows Forms], data binding
- DataGrid control [Windows Forms], about DataGrid control
- parent tables in DataGrid control
- tables [Windows Forms], displaying in DataGrid control
- data grids [Windows Forms], about data grids
- multiple tables in DataGrid control
- data [Windows Forms], resorting
- data [Windows Forms], navigating
- parent table navigation in DataGrid
- child tables [Windows Forms], dataGrid control
ms.assetid: 85604bce-bc03-49d9-9030-dda8896c44b1
ms.openlocfilehash: df559926dbc9141276f0a03deb99e340fd7212da
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742567"
---
# <a name="datagrid-control-overview-windows-forms"></a>Vue d'ensemble du contrôle DataGrid (Windows Forms)

> [!NOTE]
> Le contrôle <xref:System.Windows.Forms.DataGridView> remplace le contrôle <xref:System.Windows.Forms.DataGrid> et lui ajoute des fonctionnalités ; toutefois, le contrôle <xref:System.Windows.Forms.DataGrid> est conservé pour la compatibilité descendante et l'utilisation future si tel est votre choix. Pour plus d’informations, consultez [Différences entre les contrôles DataGridView et DataGrid Windows Forms](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).

Le contrôle Windows Forms <xref:System.Windows.Forms.DataGrid> affiche des données dans une série de lignes et de colonnes. Le cas le plus simple est quand la grille est liée à une source de données avec une seule table ne contenant aucune relation. Dans ce cas, les données apparaissent dans des lignes et des colonnes simples, comme dans une feuille de calcul. Pour plus d’informations sur la liaison de données à d’autres contrôles, consultez [Liaison de données et Windows Forms](../data-binding-and-windows-forms.md).

Si l'objet <xref:System.Windows.Forms.DataGrid> est lié à des données avec plusieurs tables associées et que la navigation est activée dans la grille, celle-ci affiche des expanders sur chaque ligne. Avec un expander, l’utilisateur peut passer d’une table parente à une table enfant. Un clic sur un nœud affiche la table enfant et un clic sur un bouton Précédent affiche la table parente d'origine. De cette manière, la grille affiche les relations hiérarchiques entre les tables.

La capture d’écran suivante montre une grille DataGrid liée aux données avec plusieurs tables :

![Application WinForms présentant un DataGrid lié à des données avec plusieurs tables.](./media/datagrid-control-overview-windows-forms/datagrid-bound-multiple-tables.gif)

Le <xref:System.Windows.Forms.DataGrid> peut fournir une interface utilisateur pour un dataset, la navigation entre des tables associées et des fonctionnalités de mise en forme et d'édition enrichies.

L’affichage et la manipulation des données sont des fonctions distinctes : le contrôle gère l’interface utilisateur, tandis que les mises à jour des données sont gérées par l’architecture de liaison de données Windows Forms et par les fournisseurs de données .NET Framework. Ainsi, plusieurs contrôles liés à la même source de données resteront synchronisés.

> [!NOTE]
> Si vous connaissez le contrôle DataGrid dans Visual Basic 6.0, vous constaterez qu'il existe des différences importantes avec le contrôle Windows Forms <xref:System.Windows.Forms.DataGrid>.

Quand la grille est liée à un <xref:System.Data.DataSet>, les colonnes et les lignes sont créées, mises en forme et remplies automatiquement Pour plus d’informations, consultez [Liaison de données et Windows Forms](../data-binding-and-windows-forms.md). Une fois le contrôle <xref:System.Windows.Forms.DataGrid> généré, vous pouvez ajouter, supprimer, réorganiser et mettre en forme les colonnes et les lignes en fonction de vos besoins.

## <a name="binding-data-to-the-control"></a>Liaison de données au contrôle

Pour que le contrôle <xref:System.Windows.Forms.DataGrid> fonctionne, il doit être lié à une source de données à l'aide des propriétés <xref:System.Windows.Forms.DataGrid.DataSource%2A> et <xref:System.Windows.Forms.DataGrid.DataMember%2A> au moment du design ou à la méthode <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> au moment de l'exécution. Cette liaison pointe le <xref:System.Windows.Forms.DataGrid> vers un objet de source de données instancié, tel que <xref:System.Data.DataSet> ou <xref:System.Data.DataTable>). Le contrôle <xref:System.Windows.Forms.DataGrid> affiche les résultats des actions qui sont effectuées sur les données. La plupart des actions spécifiques aux données ne sont pas effectuées par l'intermédiaire de <xref:System.Windows.Forms.DataGrid>, mais plutôt via la source de données.

Si les données du dataset lié sont mises à jour via un mécanisme quelconque, le contrôle <xref:System.Windows.Forms.DataGrid> reflète les modifications. Si la propriété `ReadOnly` de la grille de données et de ses styles de table et de colonne a la valeur `false`, les données du DataSet peuvent être mises à jour via le contrôle <xref:System.Windows.Forms.DataGrid>.

Une seule table à la fois peut être affichée dans le <xref:System.Windows.Forms.DataGrid>. Si une relation parent-enfant est définie entre des tables, l'utilisateur peut se déplacer entre les tables associées pour sélectionner la table à afficher dans le contrôle <xref:System.Windows.Forms.DataGrid>. Pour plus d’informations sur la liaison d’un contrôle <xref:System.Windows.Forms.DataGrid> à une source de données ADO.NET au moment de la conception ou de l’exécution, consultez [Comment : lier le contrôle DataGrid Windows Forms à une source de données](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md).

Les sources de données valides pour <xref:System.Windows.Forms.DataGrid> sont les suivantes :

- Classe <xref:System.Data.DataTable>

- Classe <xref:System.Data.DataView>

- Classe <xref:System.Data.DataSet>

- Classe <xref:System.Data.DataViewManager>

Si votre source est un dataset, celui-ci peut être un objet dans le formulaire ou un objet passé au formulaire par un service web XML. Vous pouvez lier à des datasets typés ou non typés.

Vous pouvez également lier un contrôle <xref:System.Windows.Forms.DataGrid> à des structures supplémentaires si les objets de la structure, tels que les éléments d'un tableau, exposent des propriétés publiques. La grille affichera toutes les propriétés publiques des éléments de la structure. Par exemple, si vous liez le contrôle <xref:System.Windows.Forms.DataGrid> à un tableau d'objets Customer, la grille affichera toutes les propriétés publiques de ces objets Customer. Dans certains cas, cela signifie que bien que vous puissiez lier à la structure, la structure de liaison résultante peut ne pas avoir d'application pratique. Par exemple, vous pouvez lier à un tableau d'entiers, mais comme le type de données `Integer` ne prend pas en charge les propriétés publiques, la grille ne pourra pas afficher de données.

Vous pouvez lier aux structures suivantes si leurs éléments exposent des propriétés publiques :

- Tout composant qui implémente l'interface <xref:System.Collections.IList>. Cela comprend les tableaux unidimensionnels.

- Tout composant qui implémente l'interface <xref:System.ComponentModel.IListSource>.

- Tout composant qui implémente l'interface <xref:System.ComponentModel.IBindingList>.

 Pour plus d’informations sur les sources de données possibles, consultez [Sources de données prises en charge par les Windows Forms](../data-sources-supported-by-windows-forms.md).

## <a name="grid-display"></a>Affichage de la grille

Une utilisation courante du contrôle <xref:System.Windows.Forms.DataGrid> consiste à afficher une table de données à partir d'un dataset. Toutefois, ce contrôle peut également servir à afficher plusieurs tables, y compris des tables associées. L'affichage de la grille est ajustée automatiquement en fonction de la source de données. Le tableau suivant montre ce qui est affiché pour différentes configurations.

|Contenu du dataset|Ce qui est affiché|
|--------------------------|-----------------------|
|Une seule table.|La table est affichée dans une grille.|
|Plusieurs tables.|La grille peut afficher une arborescence à laquelle les utilisateurs peuvent accéder pour trouver la table qu'ils souhaitent afficher.|
|Plusieurs tables associées.|La grille peut afficher une arborescence dans laquelle sélectionner des tables ou vous pouvez spécifier que la grille affiche la table parente. Les enregistrements dans la table parente permettent aux utilisateurs d'accéder aux lignes enfants associées.|

> [!NOTE]
> Les tables dans un dataset sont associées à l'aide d'un <xref:System.Data.DataRelation>. Consultez également [créer des relations entre les jeux de données](/visualstudio/data-tools/relationships-in-datasets).

Quand le contrôle <xref:System.Windows.Forms.DataGrid> affiche une table et que la propriété <xref:System.Windows.Forms.DataGrid.AllowSorting%2A> a la valeur `true`, vous pouvez retrier les données en cliquant sur les en-têtes de colonnes. L'utilisateur peut aussi ajouter des lignes et modifier des cellules.

Les relations entre un ensemble de tables sont présentées aux utilisateurs à l'aide d'une structure de navigation parent/enfant. Les tables parentes constituent le niveau de données le plus élevé et les tables enfants sont celles qui sont dérivées des différentes entrées dans les tables parentes. Des expanders sont affichés sur chaque ligne parente qui contient une table enfant. Un clic sur un expander génère une liste de liens web vers les tables enfants. Quand l'utilisateur sélectionne un lien, la table enfant est affichée. En cliquant sur l’icône Afficher/masquer les lignes parentes (![Icône Afficher/masquer les lignes parentes](./media/datagrid-control-overview-windows-forms/show-hide-parent-rows.gif)) masque les informations relatives à la table parente ou le fait réapparaître si l’utilisateur l’a masquée précédemment. L'utilisateur peut cliquer sur un bouton Précédent pour revenir à la table affichée précédemment.

## <a name="columns-and-rows"></a>Colonnes et lignes

Le <xref:System.Windows.Forms.DataGrid> se compose d’une collection d’objets <xref:System.Windows.Forms.DataGridTableStyle> contenus dans la propriété <xref:System.Windows.Forms.DataGrid> du contrôle <xref:System.Windows.Forms.DataGrid.TableStyles%2A>. Un style de table peut contenir une collection d'objets <xref:System.Windows.Forms.DataGridColumnStyle> contenus dans la propriété <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> du <xref:System.Windows.Forms.DataGridTableStyle>. Vous pouvez modifier les propriétés <xref:System.Windows.Forms.DataGrid.TableStyles%2A> et <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> à l’aide d’éditeurs de collections accessibles via la fenêtre **Propriétés** .

Tout <xref:System.Windows.Forms.DataGridTableStyle> associé au contrôle <xref:System.Windows.Forms.DataGrid> est accessible via <xref:System.Windows.Forms.GridTableStylesCollection>. <xref:System.Windows.Forms.GridTableStylesCollection> peut être modifié dans le concepteur avec l’éditeur de collection <xref:System.Windows.Forms.DataGridTableStyle> ou par programmation via la propriété <xref:System.Windows.Forms.DataGrid> du contrôle <xref:System.Windows.Forms.DataGrid.TableStyles%2A>.

L’illustration suivante montre les objets inclus dans le contrôle DataGrid :

![Diagramme qui affiche des objets inclus dans le contrôle DataGrid.](./media/datagrid-control-overview-windows-forms/visual-basic-columns.gif)

Vous pouvez synchroniser les styles de table et de colonne avec les objets <xref:System.Data.DataTable> et <xref:System.Data.DataColumn> en définissant leurs propriétés `MappingName` sur les propriétés <xref:System.Data.DataTable.TableName%2A> et <xref:System.Data.DataColumn.ColumnName%2A> appropriées. Quand un <xref:System.Windows.Forms.DataGridTableStyle> qui n’a aucun style de colonne est ajouté à un contrôle <xref:System.Windows.Forms.DataGrid> lié à une source de données valide et que la propriété <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> de ce style de table est définie sur une propriété <xref:System.Data.DataTable.TableName%2A> valide, une collection d’objets <xref:System.Windows.Forms.DataGridColumnStyle> est créée pour ce style de table. Pour chaque <xref:System.Data.DataColumn> trouvé dans la collection <xref:System.Data.DataTable.Columns%2A> du <xref:System.Data.DataTable>, un <xref:System.Windows.Forms.DataGridColumnStyle> correspondant est ajouté à <xref:System.Windows.Forms.GridColumnStylesCollection>. <xref:System.Windows.Forms.GridColumnStylesCollection> est accessible à l'aide de la propriété <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> de <xref:System.Windows.Forms.DataGridTableStyle>. Vous pouvez ajouter ou supprimer des colonnes dans la grille en exécutant la méthode <xref:System.Windows.Forms.GridColumnStylesCollection.Add%2A> ou <xref:System.Windows.Forms.GridColumnStylesCollection.Remove%2A> sur le <xref:System.Windows.Forms.GridColumnStylesCollection>. Pour plus d’informations, consultez [Guide pratique pour ajouter des tables et des colonnes au contrôle DataGrid Windows Forms](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md) et [Guide pratique pour supprimer ou masquer des colonnes dans le contrôle DataGrid Windows Forms](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md).

Une collection de types de colonnes étend la classe <xref:System.Windows.Forms.DataGridColumnStyle> avec des fonctionnalités de mise en forme et d’édition enrichies. Tous les types de colonne héritent de la classe de base <xref:System.Windows.Forms.DataGridColumnStyle>. La classe créée dépend de la propriété <xref:System.Data.DataColumn.DataType%2A> du <xref:System.Data.DataColumn> sur lequel le <xref:System.Web.UI.WebControls.DataGridColumn> est basé. Par exemple, un <xref:System.Data.DataColumn> dont la propriété <xref:System.Data.DataColumn.DataType%2A> a la valeur <xref:System.Boolean> est associé au <xref:System.Windows.Forms.DataGridBoolColumn>. Le tableau suivant décrit chacun de ces types de colonnes.

|Type de colonne|Description|
|-----------------|-----------------|
|<xref:System.Windows.Forms.DataGridTextBoxColumn>|Accepte et affiche les données sous forme de chaînes mises en forme ou non mises en forme. Les fonctionnalités d'édition sont les mêmes que lors de la modification des données dans un simple <xref:System.Windows.Forms.TextBox>. Hérite de <xref:System.Windows.Forms.DataGridColumnStyle>.|
|<xref:System.Windows.Forms.DataGridBoolColumn>|Accepte et affiche des valeurs `true`, `false` et null. Hérite de <xref:System.Windows.Forms.DataGridColumnStyle>.|

Un double-clic sur le bord droit d'une colonne redimensionne la colonne pour afficher sa légende complète et son entrée la plus large.

## <a name="table-styles-and-column-styles"></a>Styles de table et de colonne

Dès que vous avez établi le format par défaut du contrôle <xref:System.Windows.Forms.DataGrid>, vous pouvez personnaliser les couleurs qui sont utilisées quand certaines tables sont affichées dans la grille de données.

Pour cela, vous devez créer des instances de la classe <xref:System.Windows.Forms.DataGridTableStyle>. Les styles de table spécifient la mise en forme de tables spécifiques, différente de la mise en forme par défaut du contrôle <xref:System.Windows.Forms.DataGrid> proprement dit. Vous ne pouvez définir qu'un seul style de table à la fois pour chaque table.

Parfois, vous souhaiterez donner à une colonne spécifique une apparence différente des autres colonnes d'une table de données particulière. Vous pouvez créer un jeu de styles de colonne personnalisé à l'aide de la propriété <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A>.

Les styles de colonne sont liés aux colonnes d'un dataset tout comme les styles de table sont liés aux tables de données. Vous ne pouvez définir qu'un seul style de colonne à la fois pour chaque colonne dans un style de table particulier. Cette relation est définie dans la propriété <xref:System.Windows.Forms.DataGridColumnStyle.MappingName%2A> de la colonne.

Si vous avez créé un style de table sans y ajouter de styles de colonne, Visual Studio ajoute des styles de colonne par défaut quand le formulaire et la grille sont créés au moment de l’exécution. Toutefois, si vous avez créé un style de table et que vous y avez ajouté des styles de colonne, Visual Studio ne crée pas de styles de colonne. De plus, vous devrez définir des styles de colonne et les assigner avec le nom de mappage pour afficher les colonnes de votre choix dans la grille.

Étant donné que vous spécifiez les colonnes à inclure dans la grille de données en leur assignant un style de colonne et qu'aucun style de colonne n'a été assigné aux colonnes, vous pouvez inclure dans le dataset des colonnes de données qui ne sont pas affichées dans la grille. Toutefois, comme la colonne de données est incluse dans le dataset, vous pouvez modifier par programmation les données qui ne sont pas affichées.

> [!NOTE]
> En général, vous devez créer des styles de colonne et les ajouter à la collection de styles de colonne avant d'ajouter des styles de tableau à la collection de styles de table. Quand vous ajoutez un style de table vide à la collection, des styles de colonne sont générés automatiquement pour vous. Par conséquent, une exception sera levée si vous essayez d'ajouter de nouveaux styles de colonne avec des valeurs <xref:System.Windows.Forms.DataGridColumnStyle.MappingName%2A> dupliquées à la collection de styles de colonne.
>
> Parfois, vous souhaiterez simplement ajuster une colonne parmi d'autres ; par exemple, il se peut que le dataset contienne 50 colonnes et que vous n'ayez besoin que de 49 d'entre elles. Dans ce cas, il est plus facile d'importer les 50 colonnes et de supprimer l'une d'elles par programmation, plutôt que d'ajouter par programmation chacune des 49 colonnes souhaitées.

## <a name="formatting"></a>Mise en forme

Vous pouvez appliquer une mise en forme au contrôle <xref:System.Windows.Forms.DataGrid>, par exemple des styles de bordure, des styles de quadrillage, des polices, des propriétés de légende, un alignement des données et des couleurs d'arrière-plan en alternance sur les lignes. Pour plus d’informations, consultez [Guide pratique pour mettre en forme le contrôle DataGrid Windows Forms](how-to-format-the-windows-forms-datagrid-control.md).

## <a name="events"></a>Événements

Outre les événements de contrôle courants tels que <xref:System.Windows.Forms.Control.MouseDown>, <xref:System.Windows.Forms.Control.Enter> et <xref:System.Windows.Forms.DataGrid.Scroll>, le contrôle <xref:System.Windows.Forms.DataGrid> prend en charge les événements associés à la modification et à la navigation dans la grille. La propriété <xref:System.Windows.Forms.DataGrid.CurrentCell%2A> détermine la cellule sélectionnée. L'événement <xref:System.Windows.Forms.DataGrid.CurrentCellChanged> est déclenché quand l'utilisateur navigue vers une nouvelle cellule. Quand l'utilisateur navigue vers une nouvelle table via des relations parent/enfant, l'événement <xref:System.Windows.Forms.DataGrid.Navigate> est déclenché. L'événement <xref:System.Windows.Forms.DataGrid.BackButtonClick> est déclenché quand l'utilisateur clique sur le bouton Précédent pendant qu'il visualise une table enfant et l'événement <xref:System.Windows.Forms.DataGrid.ShowParentDetailsButtonClick> est déclenché quand l'utilisateur clique sur l'icône Afficher/masquer les lignes parentes.

## <a name="see-also"></a>Voir aussi

- [DataGrid, contrôle](datagrid-control-windows-forms.md)
- [Guide pratique pour lier le contrôle DataGrid Windows Forms à une source de données](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)
- [Guide pratique pour ajouter des tables et des colonnes au contrôle DataGrid Windows Forms](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
- [Guide pratique pour supprimer ou masquer des colonnes dans le contrôle DataGrid Windows Forms](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
- [Guide pratique pour mettre en forme le contrôle DataGrid Windows Forms](how-to-format-the-windows-forms-datagrid-control.md)
