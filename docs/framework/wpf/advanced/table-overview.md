---
title: Vue d'ensemble de Table
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- flow content elements [WPF], Table
- documents [WPF], tables
- tables [WPF]
ms.assetid: 5e1105f4-8fc4-473a-ba55-88c8e71386e6
ms.openlocfilehash: fa7106207c69f19b647ba80ab7e724e9aad174c1
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005078"
---
# <a name="table-overview"></a>Vue d'ensemble de Table
<xref:System.Windows.Documents.Table> est un élément de niveau bloc qui prend en charge la présentation basée sur la grille du contenu d’un document dynamique. La flexibilité de cet élément est très utile, mais rend plus difficiles sa compréhension et son utilisation.  
  
 Cette rubrique contient les sections suivantes.  
  
- [Principes de base de l’élément Table](#table_basics)  
  
- [Différences entre l’élément Table et l’élément Grid](#table_vs_Grid)  
  
- [Structure de base de l’élément Table](#basic_table_structure)  
  
- [Imbrication des tables](#table_containment)  
  
- [Regroupements de lignes](#row_groupings)  
  
- [Priorité du rendu en arrière-plan](#rendering_precedence)  
  
- [Étendue des lignes et des colonnes](#spanning_rows_or_columns)  
  
- [Génération d’une table avec du code](#building_a_table_with_code)  
  
- [Rubriques connexes] 
  
<a name="table_basics"></a>   
## <a name="table-basics"></a>Principes de base de l’élément Table  
  
<a name="table_vs_Grid"></a>   
### <a name="how-is-table-different-then-grid"></a>Différences entre l’élément Table et l’élément Grid  
 <xref:System.Windows.Documents.Table> et <xref:System.Windows.Controls.Grid> partagent des fonctionnalités communes, mais chacune convient mieux à différents scénarios. Un <xref:System.Windows.Documents.Table> est conçu pour être utilisé dans le contenu dynamique (pour plus d’informations sur le contenu dynamique, consultez [vue d’ensemble des documents dynamiques](flow-document-overview.md) ). Les éléments Grid sont mieux adaptés à une utilisation dans des formulaires (autrement dit, partout, sauf dans du contenu dynamique). Dans un <xref:System.Windows.Documents.FlowDocument>, <xref:System.Windows.Documents.Table> prend en charge les comportements de contenu de Flow tels que la pagination, le reformatage de colonne et la sélection de contenu, contrairement à un <xref:System.Windows.Controls.Grid>. Un <xref:System.Windows.Controls.Grid> en revanche est utilisé en dehors d’une <xref:System.Windows.Documents.FlowDocument> pour de nombreuses raisons, notamment <xref:System.Windows.Controls.Grid> ajoute des éléments basés sur un index de ligne et de colonne, <xref:System.Windows.Documents.Table>. L’élément <xref:System.Windows.Controls.Grid> permet la superposition de contenu enfant, ce qui permet à plusieurs éléments d’exister dans une même « cellule ». <xref:System.Windows.Documents.Table> ne prend pas en charge la superposition. Les éléments enfants d’un <xref:System.Windows.Controls.Grid> peuvent être positionnés de façon absolue par rapport à la zone de leurs limites de « cellule ». <xref:System.Windows.Documents.Table> ne prend pas en charge cette fonctionnalité. Enfin, un <xref:System.Windows.Controls.Grid> requiert moins de ressources qu’un <xref:System.Windows.Documents.Table>. envisagez donc d’utiliser un <xref:System.Windows.Controls.Grid> pour améliorer les performances.  
  
<a name="basic_table_structure"></a>   
### <a name="basic-table-structure"></a>Structure de base de l’élément Table  
 <xref:System.Windows.Documents.Table> fournit une présentation basée sur la grille, composée de colonnes (représentées par des éléments <xref:System.Windows.Documents.TableColumn>) et de lignes (représentées par des éléments <xref:System.Windows.Documents.TableRow>). les éléments <xref:System.Windows.Documents.TableColumn> n’hébergent pas de contenu ; elles définissent simplement les colonnes et les caractéristiques des colonnes. les éléments <xref:System.Windows.Documents.TableRow> doivent être hébergés dans un élément <xref:System.Windows.Documents.TableRowGroup>, qui définit un regroupement de lignes pour la table. les éléments <xref:System.Windows.Documents.TableCell>, qui contiennent le contenu réel à présenter par la table, doivent être hébergés dans un élément <xref:System.Windows.Documents.TableRow>. <xref:System.Windows.Documents.TableCell> peut contenir uniquement des éléments qui dérivent de <xref:System.Windows.Documents.Block>.  Les éléments enfants valides pour un <xref:System.Windows.Documents.TableCell> incluent.  
  
- <xref:System.Windows.Documents.BlockUIContainer>  
  
- <xref:System.Windows.Documents.List>  
  
- <xref:System.Windows.Documents.Paragraph>  
  
- <xref:System.Windows.Documents.Section>  
  
- <xref:System.Windows.Documents.Table>  
  
> [!NOTE]
> les éléments <xref:System.Windows.Documents.TableCell> ne peuvent pas héberger directement le contenu de texte. Pour plus d’informations sur les règles de relation contenant-contenu pour les éléments de contenu de Flow comme <xref:System.Windows.Documents.TableCell>, consultez [vue d’ensemble des documents dynamiques](flow-document-overview.md).  
  
> [!NOTE]
> <xref:System.Windows.Documents.Table> est semblable à l’élément <xref:System.Windows.Controls.Grid>, mais a plus de fonctionnalités et, par conséquent, nécessite une plus grande surcharge de ressources.  
  
 L’exemple suivant définit une simple table 2 x 3 avec XAML.  
  
 [!code-xaml[TableSnippets2#_Table_BasicLayout](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_basiclayout)]  
  
 La figure suivante montre le rendu de cet exemple.  
  
 ![Capture d’écran montrant le rendu d’un tableau de base.](./media/table-overview/basic-table-render-example.png)  
  
<a name="table_containment"></a>   
### <a name="table-containment"></a>Imbrication des tables  
 <xref:System.Windows.Documents.Table> dérive de l’élément <xref:System.Windows.Documents.Block> et adhère aux règles communes pour les éléments de niveau <xref:System.Windows.Documents.Block>.  Un élément <xref:System.Windows.Documents.Table> peut être contenu dans l’un des éléments suivants :  
  
- <xref:System.Windows.Documents.FlowDocument>  
  
- <xref:System.Windows.Documents.TableCell>  
  
- <xref:System.Windows.Controls.ListBoxItem>  
  
- <xref:System.Windows.Controls.ListViewItem>  
  
- <xref:System.Windows.Documents.Section>  
  
- <xref:System.Windows.Documents.Floater>  
  
- <xref:System.Windows.Documents.Figure>  
  
<a name="row_groupings"></a>   
### <a name="row-groupings"></a>Regroupements de lignes  
 L’élément <xref:System.Windows.Documents.TableRowGroup> offre un moyen de regrouper arbitrairement des lignes dans une table ; chaque ligne d’une table doit appartenir à un regroupement de lignes.  Les lignes qui sont regroupées ont souvent un but commun et il est donc possible d’appliquer un style à l’ensemble du regroupement.  Il est courant, pour les regroupements de lignes, de séparer les lignes spéciales, telles que les titres, les en-têtes et les pieds de page, du contenu principal de la table.  
  
 L’exemple suivant utilise XAML pour définir une table avec des lignes d’en-tête et de pied de page avec style.  
  
 [!code-xaml[TableSnippets2#_Table_RowGroups](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_rowgroups)]  
  
 La figure suivante montre le rendu de cet exemple.  
  
 @no__t 0Screenshot : Groupes de lignes de table @ no__t-0(./media/table-rowgroups.png "Table_RowGroups")  
  
<a name="rendering_precedence"></a>   
### <a name="background-rendering-precedence"></a>Priorité du rendu en arrière-plan  
 Les éléments de la table sont affichés dans l’ordre suivant (dans l’ordre de plan, du plus bas au plus haut). Cet ordre ne peut pas être modifié. Par exemple, il n’existe pas de propriété « Ordre de plan » que vous pourriez utiliser pour remplacer l’ordre établi.  
  
1. <xref:System.Windows.Documents.Table>  
  
2. <xref:System.Windows.Documents.TableColumn>  
  
3. <xref:System.Windows.Documents.TableRowGroup>  
  
4. <xref:System.Windows.Documents.TableRow>  
  
5. <xref:System.Windows.Documents.TableCell>  
  
 Prenons l’exemple suivant, qui définit des couleurs d’arrière-plan dans une table pour chacun de ces éléments.  
  
 [!code-xaml[TableSnippets2#_Table_ZOrder](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_zorder)]  
  
 La figure suivante montre comment s’affiche cet exemple (seules les couleurs d’arrière-plan sont affichées).  
  
 @no__t 0Screenshot : Table z&#45;Order @ no__t-1(./media/table-zorder.png "Table_ZOrder")  
  
<a name="spanning_rows_or_columns"></a>   
### <a name="spanning-rows-or-columns"></a>Étendue des lignes et des colonnes  
 Les cellules de table peuvent être configurées pour s’étendre sur plusieurs lignes ou colonnes à l’aide des attributs <xref:System.Windows.Documents.TableCell.RowSpan%2A> ou <xref:System.Windows.Documents.TableCell.ColumnSpan%2A>, respectivement.  
  
 Prenons l’exemple suivant, dans lequel une cellule s’étend sur trois colonnes.  
  
 [!code-xaml[TableSnippets2#_Table_ColumnSpan](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_columnspan)]  
  
 La figure suivante montre le rendu de cet exemple.  
  
 @no__t 0Screenshot : Cellule couvrant les trois colonnes @ no__t-0(./media/table-columnspan.png "Table_ColumnSpan")  
  
<a name="building_a_table_with_code"></a>   
## <a name="building-a-table-with-code"></a>Génération d’une table avec du code  
 Les exemples suivants montrent comment créer par programmation une <xref:System.Windows.Documents.Table> et la remplir avec du contenu. Le contenu de la table est réparti en cinq lignes (représentées par les objets <xref:System.Windows.Documents.TableRow> contenus dans un objet <xref:System.Windows.Documents.Table.RowGroups%2A>) et six colonnes (représentées par les objets <xref:System.Windows.Documents.TableColumn>). Les lignes sont utilisées pour différentes présentations, par exemple une ligne de titre prévue pour intituler l’ensemble de la table, une ligne d’en-tête pour décrire les colonnes de données d’une table ou une ligne de pied de page avec des informations de synthèse.  Notez que les lignes de titre, d’en-tête et de pied de page ne sont pas inhérentes à la table. Il s’agit simplement de lignes présentant des caractéristiques différentes. Les cellules de tableau contiennent le contenu réel, qui peut être composé de texte, d’images ou de presque n’importe quel autre élément [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)].  
  
 Tout d’abord, une <xref:System.Windows.Documents.FlowDocument> est créée pour héberger le <xref:System.Windows.Documents.Table>, et un nouveau <xref:System.Windows.Documents.Table> est créé et ajouté au contenu du <xref:System.Windows.Documents.FlowDocument>.  
  
 [!code-csharp[TableSnippets#_TableCreate](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreate)]
 [!code-vb[TableSnippets#_TableCreate](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreate)]  
  
 Ensuite, six objets <xref:System.Windows.Documents.TableColumn> sont créés et ajoutés à la collection <xref:System.Windows.Documents.Table.Columns%2A> de la table, avec une mise en forme appliquée.  
  
> [!NOTE]
> Notez que la collection <xref:System.Windows.Documents.Table.Columns%2A> de la table utilise l’indexation standard de base zéro.  
  
 [!code-csharp[TableSnippets#_TableCreateColumns](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreatecolumns)]
 [!code-vb[TableSnippets#_TableCreateColumns](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreatecolumns)]  
  
 Ensuite, une ligne de titre est créée, puis ajoutée à la table avec une mise en forme.  La ligne de titre contient une seule cellule qui s’étend sur les six colonnes de la table.  
  
 [!code-csharp[TableSnippets#_TableAddTitleRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddtitlerow)]
 [!code-vb[TableSnippets#_TableAddTitleRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddtitlerow)]  
  
 Ensuite, une ligne d’en-tête est créée, puis ajoutée à la table, et les cellules de la ligne d’en-tête sont créées, puis remplies avec le contenu.  
  
 [!code-csharp[TableSnippets#_TableAddHeaderRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddheaderrow)]
 [!code-vb[TableSnippets#_TableAddHeaderRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddheaderrow)]  
  
 Ensuite, une ligne de données est créée, puis ajoutée à la table, et les cellules de cette ligne sont créées, puis remplies avec le contenu.  La génération de cette ligne est similaire à la création de la ligne d’en-tête. Cependant, la mise en forme appliquée est légèrement différente.  
  
 [!code-csharp[TableSnippets#_TableAddDataRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableadddatarow)]
 [!code-vb[TableSnippets#_TableAddDataRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableadddatarow)]  
  
 Enfin, une ligne de pied de page est créée, ajoutée, puis mise en forme.  Tout comme la ligne de titre, le pied de page contient une seule cellule qui s’étend sur les six colonnes de la table.  
  
 [!code-csharp[TableSnippets#_TableAddFooterRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddfooterrow)]
 [!code-vb[TableSnippets#_TableAddFooterRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddfooterrow)]  
  
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble des documents dynamiques](flow-document-overview.md)
- [Définir une table avec XAML](how-to-define-a-table-with-xaml.md)
- [Documents dans WPF](documents-in-wpf.md)
- [Utiliser les éléments de contenu de flux](how-to-use-flow-content-elements.md)
