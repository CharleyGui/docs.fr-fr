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
ms.openlocfilehash: 4bd747cea43755116c56b16f1de9a6ffb59935ed
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187275"
---
# <a name="table-overview"></a>Vue d'ensemble de Table
<xref:System.Windows.Documents.Table>est un élément de niveau de bloc qui prend en charge la présentation en réseau du contenu du document Flow. La flexibilité de cet élément est très utile, mais rend plus difficiles sa compréhension et son utilisation.  
  
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
 <xref:System.Windows.Documents.Table>et <xref:System.Windows.Controls.Grid> partager certaines fonctionnalités communes, mais chacun est le mieux adapté pour différents scénarios. A <xref:System.Windows.Documents.Table> est conçu pour une utilisation dans le contenu du flux (voir [Flow Document Aperçu](flow-document-overview.md) pour plus d’informations sur le contenu du flux). Les grilles conviennent particulièrement aux formulaires (autrement dit, partout, sauf dans du contenu dynamique). Dans <xref:System.Windows.Documents.FlowDocument>un <xref:System.Windows.Documents.Table> , prend en charge les comportements de contenu de <xref:System.Windows.Controls.Grid> flux comme la pagination, le reflow de colonne, et la sélection de contenu tandis qu’un n’est pas. A <xref:System.Windows.Controls.Grid> d’autre part est mieux <xref:System.Windows.Documents.FlowDocument> utilisé en <xref:System.Windows.Controls.Grid> dehors d’un pour de <xref:System.Windows.Documents.Table> nombreuses raisons, y compris les éléments ajoutés basés sur une ligne et l’indice de colonne, ne. L’élément <xref:System.Windows.Controls.Grid> permet la superposition de contenu pour enfants, permettant à plus d’un élément d’exister dans une seule « cellule ». <xref:System.Windows.Documents.Table>ne prend pas en charge la superposition. Les éléments <xref:System.Windows.Controls.Grid> de l’enfant d’un peut être absolument positionné par rapport à la zone de leurs limites de « cellule ». <xref:System.Windows.Documents.Table>ne prend pas en charge cette fonctionnalité. Enfin, <xref:System.Windows.Controls.Grid> un nécessite moins <xref:System.Windows.Documents.Table> de ressources, <xref:System.Windows.Controls.Grid> puis un si envisager d’utiliser un pour améliorer les performances.  
  
<a name="basic_table_structure"></a>
### <a name="basic-table-structure"></a>Structure de base de l’élément Table  
 <xref:System.Windows.Documents.Table>fournit une présentation basée sur la grille <xref:System.Windows.Documents.TableColumn> composée de colonnes (représentées par des éléments) et de rangées (représentées par <xref:System.Windows.Documents.TableRow> des éléments). <xref:System.Windows.Documents.TableColumn>éléments n’hébergent pas de contenu; ils définissent simplement les colonnes et les caractéristiques des colonnes. <xref:System.Windows.Documents.TableRow>éléments doivent être hébergés dans un <xref:System.Windows.Documents.TableRowGroup> élément, qui définit un regroupement de rangées pour la table. <xref:System.Windows.Documents.TableCell>éléments, qui contiennent le contenu réel à présenter par le <xref:System.Windows.Documents.TableRow> tableau, doivent être hébergés dans un élément. <xref:System.Windows.Documents.TableCell>ne peuvent contenir que <xref:System.Windows.Documents.Block>des éléments qui dérivent de .  Éléments valables <xref:System.Windows.Documents.TableCell> pour enfants pour un inclure.  
  
- <xref:System.Windows.Documents.BlockUIContainer>  
  
- <xref:System.Windows.Documents.List>  
  
- <xref:System.Windows.Documents.Paragraph>  
  
- <xref:System.Windows.Documents.Section>  
  
- <xref:System.Windows.Documents.Table>  
  
> [!NOTE]
> <xref:System.Windows.Documents.TableCell>éléments peuvent ne pas héberger directement le contenu du texte. Pour plus d’informations sur les règles <xref:System.Windows.Documents.TableCell>de confinement pour les éléments de contenu de flux comme , voir [Flow Document Aperçu](flow-document-overview.md).  
  
> [!NOTE]
> <xref:System.Windows.Documents.Table>est similaire <xref:System.Windows.Controls.Grid> à l’élément, mais a plus de capacités et, par conséquent, nécessite une plus grande surcharge en ressources.  
  
 L’exemple suivant définit une simple table de 2 x 3 avec XAML.  
  
 [!code-xaml[TableSnippets2#_Table_BasicLayout](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_basiclayout)]  
  
 La figure suivante montre le rendu de cet exemple.  
  
 ![Capture d’écran qui montre comment une table de base rend.](./media/table-overview/basic-table-render-example.png)  
  
<a name="table_containment"></a>
### <a name="table-containment"></a>Imbrication des tables  
 <xref:System.Windows.Documents.Table>dérive de <xref:System.Windows.Documents.Block> l’élément et adhère aux <xref:System.Windows.Documents.Block> règles communes pour les éléments de niveau.  Un <xref:System.Windows.Documents.Table> élément peut être contenu par l’un des éléments suivants :  
  
- <xref:System.Windows.Documents.FlowDocument>  
  
- <xref:System.Windows.Documents.TableCell>  
  
- <xref:System.Windows.Controls.ListBoxItem>  
  
- <xref:System.Windows.Controls.ListViewItem>  
  
- <xref:System.Windows.Documents.Section>  
  
- <xref:System.Windows.Documents.Floater>  
  
- <xref:System.Windows.Documents.Figure>  
  
<a name="row_groupings"></a>
### <a name="row-groupings"></a>Regroupements de lignes  
 L’élément <xref:System.Windows.Documents.TableRowGroup> fournit un moyen de regrouper arbitrairement les rangées à l’intérieur d’une table; chaque rangée dans une table doit appartenir à un groupement de rangée.  Les lignes qui sont regroupées ont souvent un but commun et il est donc possible d’appliquer un style à l’ensemble du regroupement.  Il est courant, pour les regroupements de lignes, de séparer les lignes spéciales, telles que les titres, les en-têtes et les pieds de page, du contenu principal de la table.  
  
 L’exemple suivant utilise XAML pour définir une table avec des en-têtes et des rangées de pieds.  
  
 [!code-xaml[TableSnippets2#_Table_RowGroups](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_rowgroups)]  
  
 La figure suivante montre le rendu de cet exemple.  
  
 ![Capture d'écran : groupes de lignes de la table](./media/table-rowgroups.png "Table_RowGroups")  
  
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
  
 ![Capture d’écran: Table z&#45;commande](./media/table-zorder.png "Table_ZOrder")  
  
<a name="spanning_rows_or_columns"></a>
### <a name="spanning-rows-or-columns"></a>Étendue des lignes et des colonnes  
 Les cellules de table peuvent être configurées <xref:System.Windows.Documents.TableCell.RowSpan%2A> pour <xref:System.Windows.Documents.TableCell.ColumnSpan%2A> s’étendre sur plusieurs lignes ou colonnes en utilisant les ou les attributs, respectivement.  
  
 Prenons l’exemple suivant, dans lequel une cellule s’étend sur trois colonnes.  
  
 [!code-xaml[TableSnippets2#_Table_ColumnSpan](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_columnspan)]  
  
 La figure suivante montre le rendu de cet exemple.  
  
 ![Capture d'écran : cellule s'étendant sur les trois colonnes](./media/table-columnspan.png "Table_ColumnSpan")  
  
<a name="building_a_table_with_code"></a>
## <a name="building-a-table-with-code"></a>Génération d’une table avec du code  
 Les exemples suivants montrent comment <xref:System.Windows.Documents.Table> créer programmatiquement un et le peupler avec du contenu. Le contenu de la table est réparti en cinq <xref:System.Windows.Documents.TableRow> rangées <xref:System.Windows.Documents.Table.RowGroups%2A> (représentées par des objets <xref:System.Windows.Documents.TableColumn> contenus dans un objet) et six colonnes (représentées par des objets). Les lignes sont utilisées pour différentes présentations, par exemple, une ligne de titre prévue pour intituler l’ensemble de la table, une ligne d’en-tête pour décrire les colonnes de données d’une table ou une ligne de pied de page avec des informations de synthèse.  Notez que les lignes de titre, d’en-tête et de pied de page ne sont pas inhérentes à la table. Il s’agit simplement de lignes présentant des caractéristiques différentes. Les cellules de table contiennent le contenu réel, qui peut [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] être composé de texte, d’images, ou presque n’importe quel autre élément.  
  
 Tout d’abord, <xref:System.Windows.Documents.FlowDocument> a <xref:System.Windows.Documents.Table>est créé <xref:System.Windows.Documents.Table> pour accueillir le , <xref:System.Windows.Documents.FlowDocument>et un nouveau est créé et ajouté au contenu de la .  
  
 [!code-csharp[TableSnippets#_TableCreate](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreate)]
 [!code-vb[TableSnippets#_TableCreate](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreate)]  
  
 Ensuite, <xref:System.Windows.Documents.TableColumn> six objets sont créés et <xref:System.Windows.Documents.Table.Columns%2A> ajoutés à la collection de la table, avec un certain formatage appliqué.  
  
> [!NOTE]
> Notez que la <xref:System.Windows.Documents.Table.Columns%2A> collection du tableau utilise une indexation décondante standard.  
  
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
