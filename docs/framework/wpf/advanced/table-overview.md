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
ms.openlocfilehash: 01a5233a5436688caee3783cb26d344284df52e9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964297"
---
# <a name="table-overview"></a>Vue d'ensemble de Table
<xref:System.Windows.Documents.Table>est un élément de niveau bloc qui prend en charge la présentation basée sur la grille du contenu d’un document dynamique. La flexibilité de cet élément est très utile, mais rend plus difficiles sa compréhension et son utilisation.  
  
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
 <xref:System.Windows.Documents.Table>et <xref:System.Windows.Controls.Grid> partagent des fonctionnalités communes, mais chacune convient mieux à différents scénarios. Un <xref:System.Windows.Documents.Table> est conçu pour être utilisé dans le contenu dynamique (pour plus d’informations sur le contenu dynamique, consultez [vue d’ensemble des documents dynamiques](flow-document-overview.md) ). Les éléments Grid sont mieux adaptés à une utilisation dans des formulaires (autrement dit, partout, sauf dans du contenu dynamique). Dans un <xref:System.Windows.Documents.FlowDocument>, <xref:System.Windows.Documents.Table> prend en charge les comportements de contenu de workflow tels que la pagination, le rechargement <xref:System.Windows.Controls.Grid> de colonnes et la sélection de contenu alors qu’un ne le fait pas. En revanche, il est préférable de l’utiliser en dehors <xref:System.Windows.Documents.FlowDocument> d’un pour de <xref:System.Windows.Controls.Grid> nombreuses raisons, <xref:System.Windows.Documents.Table> notamment l’ajout d’éléments basés sur un index de ligne et de colonne. <xref:System.Windows.Controls.Grid> L' <xref:System.Windows.Controls.Grid> élément permet la superposition de contenu enfant, ce qui permet à plusieurs éléments d’exister dans une même «cellule». <xref:System.Windows.Documents.Table>ne prend pas en charge la superposition. Les éléments enfants d' <xref:System.Windows.Controls.Grid> un peuvent être positionnés de façon absolue par rapport à la zone de leurs limites de «cellule». <xref:System.Windows.Documents.Table>ne prend pas en charge cette fonctionnalité. Enfin, un <xref:System.Windows.Controls.Grid> requiert moins de ressources, <xref:System.Windows.Documents.Table> alors envisagez <xref:System.Windows.Controls.Grid> d’utiliser un pour améliorer les performances.  
  
<a name="basic_table_structure"></a>   
### <a name="basic-table-structure"></a>Structure de base de l’élément Table  
 <xref:System.Windows.Documents.Table>fournit une présentation basée sur la grille composée de colonnes (représentées par <xref:System.Windows.Documents.TableColumn> des éléments) et de lignes (représentées par <xref:System.Windows.Documents.TableRow> des éléments). <xref:System.Windows.Documents.TableColumn>les éléments n’hébergent pas de contenu; elles définissent simplement les colonnes et les caractéristiques des colonnes. <xref:System.Windows.Documents.TableRow>les éléments doivent être hébergés <xref:System.Windows.Documents.TableRowGroup> dans un élément, qui définit un regroupement de lignes pour la table. <xref:System.Windows.Documents.TableCell>les éléments, qui contiennent le contenu réel à présenter dans la table, doivent être hébergés dans <xref:System.Windows.Documents.TableRow> un élément. <xref:System.Windows.Documents.TableCell>peut contenir uniquement des éléments qui dérivent de <xref:System.Windows.Documents.Block>.  Éléments enfants valides pour <xref:System.Windows.Documents.TableCell> un include.  
  
- <xref:System.Windows.Documents.BlockUIContainer>  
  
- <xref:System.Windows.Documents.List>  
  
- <xref:System.Windows.Documents.Paragraph>  
  
- <xref:System.Windows.Documents.Section>  
  
- <xref:System.Windows.Documents.Table>  
  
> [!NOTE]
> <xref:System.Windows.Documents.TableCell>les éléments ne peuvent pas héberger directement le contenu de texte. Pour plus d’informations sur les règles de relation contenant-contenu pour <xref:System.Windows.Documents.TableCell>les éléments de contenu de Flow comme, consultez [vue d’ensemble des documents dynamiques](flow-document-overview.md).  
  
> [!NOTE]
> <xref:System.Windows.Documents.Table>est semblable à l' <xref:System.Windows.Controls.Grid> élément, mais a plus de fonctionnalités et, par conséquent, nécessite une plus grande surcharge de ressources.  
  
 L’exemple suivant définit une simple table 2 x 3 avec [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)].  
  
 [!code-xaml[TableSnippets2#_Table_BasicLayout](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_basiclayout)]  
  
 La figure suivante montre le rendu de cet exemple.  
  
 ![Capture d’écran montrant le rendu d’un tableau de base.](./media/table-overview/basic-table-render-example.png)  
  
<a name="table_containment"></a>   
### <a name="table-containment"></a>Imbrication des tables  
 <xref:System.Windows.Documents.Table>dérive de l' <xref:System.Windows.Documents.Block> élément et adhère aux règles communes pour les éléments de <xref:System.Windows.Documents.Block> niveau.  Un <xref:System.Windows.Documents.Table> élément peut être contenu dans l’un des éléments suivants:  
  
- <xref:System.Windows.Documents.FlowDocument>  
  
- <xref:System.Windows.Documents.TableCell>  
  
- <xref:System.Windows.Controls.ListBoxItem>  
  
- <xref:System.Windows.Controls.ListViewItem>  
  
- <xref:System.Windows.Documents.Section>  
  
- <xref:System.Windows.Documents.Floater>  
  
- <xref:System.Windows.Documents.Figure>  
  
<a name="row_groupings"></a>   
### <a name="row-groupings"></a>Regroupements de lignes  
 L' <xref:System.Windows.Documents.TableRowGroup> élément fournit un moyen de regrouper arbitrairement des lignes dans une table; chaque ligne d’une table doit appartenir à un regroupement de lignes.  Les lignes qui sont regroupées ont souvent un but commun et il est donc possible d’appliquer un style à l’ensemble du regroupement.  Il est courant, pour les regroupements de lignes, de séparer les lignes spéciales, telles que les titres, les en-têtes et les pieds de page, du contenu principal de la table.  
  
 L’exemple suivant utilise [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] pour définir une table avec des lignes d’en-tête et de pied de page avec style.  
  
 [!code-xaml[TableSnippets2#_Table_RowGroups](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_rowgroups)]  
  
 La figure suivante montre le rendu de cet exemple.  
  
 ![Capture d’écran Groupes]de lignes de table(./media/table-rowgroups.png "Table_RowGroups")  
  
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
  
 ![Capture d’écran Table z&#45;ordre](./media/table-zorder.png "Table_ZOrder")  
  
<a name="spanning_rows_or_columns"></a>   
### <a name="spanning-rows-or-columns"></a>Étendue des lignes et des colonnes  
 Les <xref:System.Windows.Documents.TableCell.RowSpan%2A> cellules de table peuvent être configurées pour s’étendre sur plusieurs lignes ou <xref:System.Windows.Documents.TableCell.ColumnSpan%2A> colonnes à l’aide des attributs ou, respectivement.  
  
 Prenons l’exemple suivant, dans lequel une cellule s’étend sur trois colonnes.  
  
 [!code-xaml[TableSnippets2#_Table_ColumnSpan](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_columnspan)]  
  
 La figure suivante montre le rendu de cet exemple.  
  
 ![Capture d’écran Cellule couvrant les trois colonnes](./media/table-columnspan.png "Table_ColumnSpan")  
  
<a name="building_a_table_with_code"></a>   
## <a name="building-a-table-with-code"></a>Génération d’une table avec du code  
 Les exemples suivants montrent comment créer un <xref:System.Windows.Documents.Table> et le remplir par programmation avec du contenu. Le contenu de la table est réparti en cinq lignes (représentées <xref:System.Windows.Documents.TableRow> par les objets contenus <xref:System.Windows.Documents.Table.RowGroups%2A> dans un objet) et six colonnes ( <xref:System.Windows.Documents.TableColumn> représentées par des objets). Les lignes sont utilisées pour différentes présentations, par exemple une ligne de titre prévue pour intituler l’ensemble de la table, une ligne d’en-tête pour décrire les colonnes de données d’une table ou une ligne de pied de page avec des informations de synthèse.  Notez que les lignes de titre, d’en-tête et de pied de page ne sont pas inhérentes à la table. Il s’agit simplement de lignes présentant des caractéristiques différentes. Les cellules de tableau contiennent le contenu réel, qui peut être composé de texte, d’images ou de presque [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] tout autre élément.  
  
 Tout d’abord <xref:System.Windows.Documents.FlowDocument> , un est créé pour <xref:System.Windows.Documents.Table>héberger le, <xref:System.Windows.Documents.Table> et un nouveau est <xref:System.Windows.Documents.FlowDocument>créé et ajouté au contenu du.  
  
 [!code-csharp[TableSnippets#_TableCreate](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreate)]
 [!code-vb[TableSnippets#_TableCreate](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreate)]  
  
 Ensuite, six <xref:System.Windows.Documents.TableColumn> objets sont créés et ajoutés à la collection de <xref:System.Windows.Documents.Table.Columns%2A> la table, avec une mise en forme appliquée.  
  
> [!NOTE]
> Notez que la collection de <xref:System.Windows.Documents.Table.Columns%2A> la table utilise l’indexation standard de base zéro.  
  
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
