---
title: Modes de tri des colonnes du contrôle DataGridView Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- data grids [Windows Forms], sort modes
- DataGridView control [Windows Forms], sort mode
ms.assetid: 43715887-2df9-4da7-bcf1-b9c7c842b2bf
ms.openlocfilehash: d0d743ccae38d101eda5bb9780b33ae18dfb608a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918450"
---
# <a name="column-sort-modes-in-the-windows-forms-datagridview-control"></a>Modes de tri des colonnes du contrôle DataGridView Windows Forms
<xref:System.Windows.Forms.DataGridView>les colonnes ont trois modes de tri. Le mode de tri de chaque colonne est spécifié par <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> le biais de la propriété de la colonne, qui peut être définie sur <xref:System.Windows.Forms.DataGridViewColumnSortMode> l’une des valeurs d’énumération suivantes.  
  
|Valeur`DataGridViewColumnSortMode`|Description|  
|----------------------------------------|-----------------|  
|<xref:System.Windows.Forms.DataGridViewColumnSortMode.Automatic>|Valeur par défaut pour les colonnes de zone de texte. À moins que les en-têtes de colonne soient utilisés pour la sélection, un <xref:System.Windows.Forms.DataGridView> clic sur l’en-tête de colonne trie automatiquement le par cette colonne et affiche un glyphe indiquant l’ordre de tri.|  
|<xref:System.Windows.Forms.DataGridViewColumnSortMode.NotSortable>|Valeur par défaut pour les colonnes non-zone de texte. Vous pouvez trier cette colonne par programme. Toutefois, il n’est pas destiné au tri, donc aucun espace n’est réservé pour le glyphe de tri.|  
|<xref:System.Windows.Forms.DataGridViewColumnSortMode.Programmatic>|Vous pouvez trier cette colonne par programme, et l’espace est réservé pour le glyphe de tri.|  
  
 Vous pouvez modifier le mode de tri d’une colonne dont la valeur par défaut <xref:System.Windows.Forms.DataGridViewColumnSortMode.NotSortable> est si elle contient des valeurs qui peuvent être triées de manière significative. Par exemple, si vous avez une colonne de base de données qui contient des nombres qui représentent des États d’élément, vous pouvez afficher ces nombres en tant qu’icônes correspondantes en liant une colonne d’image à la colonne de base de données. Vous pouvez ensuite modifier les valeurs de cellule numériques en valeurs d’affichage d’image dans un <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> gestionnaire pour l’événement. Dans ce cas, l’affectation <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> de la <xref:System.Windows.Forms.DataGridViewColumnSortMode.Automatic> valeur à la propriété permet à vos utilisateurs de trier la colonne. Le tri automatique permet à vos utilisateurs de regrouper les éléments qui ont le même État même si les États correspondant aux nombres n’ont pas de séquence naturelle. Les colonnes de case à cocher sont un autre exemple où le tri automatique est utile pour regrouper des éléments dans le même État.  
  
 Vous pouvez trier un <xref:System.Windows.Forms.DataGridView> par un par programme selon les valeurs d’une colonne ou de plusieurs colonnes, quels que <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> soient les paramètres. Le tri par programmation est utile lorsque vous souhaitez fournir votre propre interface utilisateur pour le tri ou lorsque vous souhaitez implémenter un tri personnalisé. Fournir votre propre interface utilisateur de tri est utile, par exemple, lorsque vous <xref:System.Windows.Forms.DataGridView> définissez le mode de sélection pour activer la sélection d’en-tête de colonne. Dans ce cas, bien que les en-têtes de colonnes ne puissent pas être utilisés pour le tri, vous souhaitez toujours que les en-têtes affichent le glyphe <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> de tri <xref:System.Windows.Forms.DataGridViewColumnSortMode.Programmatic>approprié. vous devez donc définir la propriété avec la valeur.  
  
 Les colonnes définies sur le mode de tri par programmation n’affichent pas automatiquement un glyphe de tri. Pour ces colonnes, vous devez afficher le glyphe vous-même en <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.SortGlyphDirection%2A?displayProperty=nameWithType> définissant la propriété. Cela est nécessaire si vous souhaitez bénéficier d’une flexibilité dans le tri personnalisé. Par exemple, si vous triez le <xref:System.Windows.Forms.DataGridView> par plusieurs colonnes, vous souhaiterez peut-être afficher plusieurs glyphes de tri ou aucun glyphe de tri.  
  
 Bien que vous puissiez trier par programme un <xref:System.Windows.Forms.DataGridView> par colonne, certaines colonnes, telles que les colonnes de bouton, peuvent ne pas contenir des valeurs qui peuvent être triées de manière significative. Pour ces colonnes, le <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> paramètre de <xref:System.Windows.Forms.DataGridViewColumnSortMode.NotSortable> propriété indiquant qu’il ne sera jamais utilisé pour le tri, il n’est donc pas nécessaire de réserver de l’espace dans l’en-tête pour le glyphe de tri.  
  
 Lorsqu’un <xref:System.Windows.Forms.DataGridView> est trié, vous pouvez déterminer la colonne <xref:System.Windows.Forms.DataGridView.SortedColumn%2A> de tri et l’ordre de tri en vérifiant les valeurs des <xref:System.Windows.Forms.DataGridView.SortOrder%2A> propriétés et. Ces valeurs ne sont pas significatives après une opération de tri personnalisée. Pour plus d’informations sur le tri personnalisé, consultez la section tri personnalisé plus loin dans cette rubrique.  
  
 Lorsqu’un <xref:System.Windows.Forms.DataGridView> contrôle contenant à la fois des colonnes dépendantes et indépendantes est trié, les valeurs des colonnes indépendantes ne peuvent pas être gérées automatiquement. Pour conserver ces valeurs, vous devez implémenter le mode virtuel en <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> affectant `true` à la propriété <xref:System.Windows.Forms.DataGridView.CellValueNeeded> la <xref:System.Windows.Forms.DataGridView.CellValuePushed> valeur et en gérant les événements et. Pour plus d'informations, voir [Procédure : Implémentez le mode virtuel dans le contrôle](how-to-implement-virtual-mode-in-the-windows-forms-datagridview-control.md)DataGridView Windows Forms. Le tri par colonnes indépendantes en mode dépendant n’est pas pris en charge.  
  
## <a name="programmatic-sorting"></a>Tri par programmation  
 Vous pouvez trier <xref:System.Windows.Forms.DataGridView> par programme en appelant sa <xref:System.Windows.Forms.DataGridView.Sort%2A> méthode.  
  
 La `Sort(DataGridViewColumn,ListSortDirection)` surcharge de la <xref:System.Windows.Forms.DataGridView.Sort%2A> méthode prend un <xref:System.Windows.Forms.DataGridViewColumn> et une <xref:System.ComponentModel.ListSortDirection> valeur d’énumération en tant que paramètres. Cette surcharge est utile lors du tri par colonnes avec des valeurs qui peuvent être triées de manière significative, mais que vous ne souhaitez pas configurer pour le tri automatique. Lorsque vous appelez cette surcharge et transmettez une colonne avec une <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> valeur de propriété <xref:System.Windows.Forms.DataGridViewColumnSortMode.Automatic?displayProperty=nameWithType>égale à <xref:System.Windows.Forms.DataGridView.SortedColumn%2A> , <xref:System.Windows.Forms.DataGridView.SortOrder%2A> les propriétés et sont définies automatiquement et le glyphe de tri approprié apparaît dans l’en-tête de colonne.  
  
> [!NOTE]
> Lorsque le <xref:System.Windows.Forms.DataGridView> contrôle est lié à une source de données externe en définissant la <xref:System.Windows.Forms.DataGridView.DataSource%2A> propriété `Sort(DataGridViewColumn,ListSortDirection)` , la surcharge de la méthode ne fonctionne pas pour les colonnes indépendantes. En outre, lorsque la <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> propriété est `true`, vous pouvez appeler cette surcharge uniquement pour les colonnes dépendantes. Pour déterminer si une colonne est liée aux données, vérifiez la <xref:System.Windows.Forms.DataGridViewColumn.IsDataBound%2A> valeur de la propriété. Le tri des colonnes indépendantes en mode dépendant n’est pas pris en charge.  
  
## <a name="custom-sorting"></a>Tri personnalisé  
 Vous pouvez personnaliser <xref:System.Windows.Forms.DataGridView> à l’aide `Sort(IComparer)` de la surcharge <xref:System.Windows.Forms.DataGridView.Sort%2A> de la méthode ou en <xref:System.Windows.Forms.DataGridView.SortCompare> gérant l’événement.  
  
 La `Sort(IComparer)` surcharge de méthode prend une instance d’une classe qui implémente <xref:System.Collections.IComparer> l’interface en tant que paramètre. Cette surcharge est utile lorsque vous souhaitez fournir un tri personnalisé. par exemple, lorsque les valeurs d’une colonne n’ont pas d’ordre de tri naturel ou lorsque l’ordre de tri naturel n’est pas approprié. Dans ce cas, vous ne pouvez pas utiliser le tri automatique, mais vous pouvez toujours souhaiter que vos utilisateurs puissent effectuer un tri en cliquant sur les en-têtes de colonne. Vous pouvez appeler cette surcharge dans un gestionnaire pour l' <xref:System.Windows.Forms.DataGridView.ColumnHeaderMouseClick> événement si vous n’utilisez pas d’en-têtes de colonne pour la sélection.  
  
> [!NOTE]
> La `Sort(IComparer)` surcharge de méthode fonctionne uniquement lorsque <xref:System.Windows.Forms.DataGridView> le contrôle n’est pas lié à une source de données <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> externe et que `false`la valeur de la propriété est. Pour personnaliser le tri des colonnes liées à une source de données externe, vous devez utiliser les opérations de tri fournies par la source de données. En mode virtuel, vous devez fournir vos propres opérations de tri pour les colonnes indépendantes.  
  
 Pour utiliser la `Sort(IComparer)` surcharge de méthode, vous devez créer votre propre classe qui implémente <xref:System.Collections.IComparer> l’interface. Cette interface requiert que votre classe implémente <xref:System.Collections.IComparer.Compare%2A?displayProperty=nameWithType> la méthode, à laquelle <xref:System.Windows.Forms.DataGridView> le <xref:System.Windows.Forms.DataGridViewRow> passe des objets comme entrée `Sort(IComparer)` lorsque la surcharge de méthode est appelée. Cela vous permet de calculer l’ordre correct des lignes en fonction des valeurs d’une colonne.  
  
 La `Sort(IComparer)` surcharge de méthode ne définissant <xref:System.Windows.Forms.DataGridView.SortedColumn%2A> pas <xref:System.Windows.Forms.DataGridView.SortOrder%2A> les propriétés et, vous devez toujours définir <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.SortGlyphDirection%2A?displayProperty=nameWithType> la propriété pour afficher le glyphe de tri.  
  
 Comme alternative à la `Sort(IComparer)` surcharge de méthode, vous pouvez fournir un tri personnalisé en implémentant un gestionnaire pour l' <xref:System.Windows.Forms.DataGridView.SortCompare> événement. Cet événement se produit lorsque les utilisateurs cliquent sur les en-têtes de colonnes configurés pour le `Sort(DataGridViewColumn,ListSortDirection)` tri automatique ou <xref:System.Windows.Forms.DataGridView.Sort%2A> lorsque vous appelez la surcharge de la méthode. L’événement se produit pour chaque paire de lignes dans le contrôle, ce qui vous permet de calculer le bon ordre.  
  
> [!NOTE]
> L' <xref:System.Windows.Forms.DataGridView.SortCompare> événement ne se produit pas lorsque <xref:System.Windows.Forms.DataGridView.DataSource%2A> la propriété est définie ou lorsque <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> la valeur de `true`la propriété est.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.Sort%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.SortedColumn%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.SortOrder%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.SortGlyphDirection%2A?displayProperty=nameWithType>
- [Tri des données dans le contrôle DataGridView Windows Forms](sorting-data-in-the-windows-forms-datagridview-control.md)
- [Guide pratique pour Définir les modes de tri des colonnes dans le contrôle DataGridView Windows Forms](set-the-sort-modes-for-columns-wf-datagridview-control.md)
- [Guide pratique pour Personnaliser le tri dans le contrôle DataGridView Windows Forms](how-to-customize-sorting-in-the-windows-forms-datagridview-control.md)
