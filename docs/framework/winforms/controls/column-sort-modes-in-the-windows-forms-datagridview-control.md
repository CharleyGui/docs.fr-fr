---
title: Modes de tri des colonnes dans le contrôle DataGridView
ms.date: 03/30/2017
helpviewer_keywords:
- data grids [Windows Forms], sort modes
- DataGridView control [Windows Forms], sort mode
ms.assetid: 43715887-2df9-4da7-bcf1-b9c7c842b2bf
ms.openlocfilehash: d1e2f582c9759332e0ed963cb7f88ee052616c45
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744193"
---
# <a name="column-sort-modes-in-the-windows-forms-datagridview-control"></a>Modes de tri des colonnes du contrôle DataGridView Windows Forms
les colonnes <xref:System.Windows.Forms.DataGridView> ont trois modes de tri. Le mode de tri de chaque colonne est spécifié par le biais de la propriété <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> de la colonne, qui peut être définie sur l’une des <xref:System.Windows.Forms.DataGridViewColumnSortMode> valeurs d’énumération suivantes.  
  
|Valeur de `DataGridViewColumnSortMode`|Description|  
|----------------------------------------|-----------------|  
|<xref:System.Windows.Forms.DataGridViewColumnSortMode.Automatic>|Valeur par défaut pour les colonnes de zone de texte. À moins que les en-têtes de colonne soient utilisés pour la sélection, le simple clic sur l’en-tête de colonne trie automatiquement les <xref:System.Windows.Forms.DataGridView> par cette colonne et affiche un glyphe indiquant l’ordre de tri.|  
|<xref:System.Windows.Forms.DataGridViewColumnSortMode.NotSortable>|Valeur par défaut pour les colonnes non-zone de texte. Vous pouvez trier cette colonne par programme. Toutefois, il n’est pas destiné au tri, donc aucun espace n’est réservé pour le glyphe de tri.|  
|<xref:System.Windows.Forms.DataGridViewColumnSortMode.Programmatic>|Vous pouvez trier cette colonne par programme, et l’espace est réservé pour le glyphe de tri.|  
  
 Vous souhaiterez peut-être modifier le mode de tri d’une colonne dont la valeur par défaut est <xref:System.Windows.Forms.DataGridViewColumnSortMode.NotSortable> si elle contient des valeurs qui peuvent être triées de manière significative. Par exemple, si vous avez une colonne de base de données qui contient des nombres qui représentent des États d’élément, vous pouvez afficher ces nombres en tant qu’icônes correspondantes en liant une colonne d’image à la colonne de base de données. Vous pouvez ensuite modifier les valeurs de cellule numériques en valeurs d’affichage d’image dans un gestionnaire pour l’événement <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType>. Dans ce cas, la définition de la propriété <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> sur <xref:System.Windows.Forms.DataGridViewColumnSortMode.Automatic> permettra à vos utilisateurs de trier la colonne. Le tri automatique permet à vos utilisateurs de regrouper les éléments qui ont le même État même si les États correspondant aux nombres n’ont pas de séquence naturelle. Les colonnes de case à cocher sont un autre exemple où le tri automatique est utile pour regrouper des éléments dans le même État.  
  
 Vous pouvez trier un <xref:System.Windows.Forms.DataGridView> par programme selon les valeurs d’une colonne ou de plusieurs colonnes, quels que soient les paramètres de <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A>. Le tri par programmation est utile lorsque vous souhaitez fournir votre propre interface utilisateur pour le tri ou lorsque vous souhaitez implémenter un tri personnalisé. Fournir votre propre interface utilisateur de tri est utile, par exemple, lorsque vous définissez le mode de sélection <xref:System.Windows.Forms.DataGridView> pour activer la sélection d’en-tête de colonne. Dans ce cas, bien que les en-têtes de colonnes ne puissent pas être utilisés pour le tri, vous souhaitez toujours que les en-têtes affichent le glyphe de tri approprié. vous devez donc définir la propriété <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> sur <xref:System.Windows.Forms.DataGridViewColumnSortMode.Programmatic>.  
  
 Les colonnes définies sur le mode de tri par programmation n’affichent pas automatiquement un glyphe de tri. Pour ces colonnes, vous devez afficher le glyphe vous-même en définissant la propriété <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.SortGlyphDirection%2A?displayProperty=nameWithType>. Cela est nécessaire si vous souhaitez bénéficier d’une flexibilité dans le tri personnalisé. Par exemple, si vous triez le <xref:System.Windows.Forms.DataGridView> par plusieurs colonnes, vous souhaiterez peut-être afficher plusieurs glyphes de tri ou aucun glyphe de tri.  
  
 Bien que vous puissiez trier par programme un <xref:System.Windows.Forms.DataGridView> par n’importe quelle colonne, certaines colonnes, telles que les colonnes de bouton, peuvent ne pas contenir des valeurs qui peuvent être triées de manière significative. Pour ces colonnes, le paramètre de propriété <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> de <xref:System.Windows.Forms.DataGridViewColumnSortMode.NotSortable> indique qu’il ne sera jamais utilisé pour le tri. il n’est donc pas nécessaire de réserver de l’espace dans l’en-tête pour le glyphe de tri.  
  
 Lorsqu’un <xref:System.Windows.Forms.DataGridView> est trié, vous pouvez déterminer la colonne de tri et l’ordre de tri en vérifiant les valeurs des propriétés <xref:System.Windows.Forms.DataGridView.SortedColumn%2A> et <xref:System.Windows.Forms.DataGridView.SortOrder%2A>. Ces valeurs ne sont pas significatives après une opération de tri personnalisée. Pour plus d’informations sur le tri personnalisé, consultez la section tri personnalisé plus loin dans cette rubrique.  
  
 Lorsqu’un contrôle de <xref:System.Windows.Forms.DataGridView> contenant des colonnes dépendantes et indépendantes est trié, les valeurs des colonnes indépendantes ne peuvent pas être gérées automatiquement. Pour conserver ces valeurs, vous devez implémenter le mode virtuel en affectant à la propriété <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> la valeur `true` et en gérant les événements <xref:System.Windows.Forms.DataGridView.CellValueNeeded> et <xref:System.Windows.Forms.DataGridView.CellValuePushed>. Pour plus d’informations, consultez [Comment : implémenter le mode virtuel dans le contrôle DataGridView Windows Forms](how-to-implement-virtual-mode-in-the-windows-forms-datagridview-control.md). Le tri par colonnes indépendantes en mode dépendant n’est pas pris en charge.  
  
## <a name="programmatic-sorting"></a>Tri par programmation  
 Vous pouvez trier une <xref:System.Windows.Forms.DataGridView> par programmation en appelant sa méthode <xref:System.Windows.Forms.DataGridView.Sort%2A>.  
  
 La surcharge `Sort(DataGridViewColumn,ListSortDirection)` de la méthode <xref:System.Windows.Forms.DataGridView.Sort%2A> prend un <xref:System.Windows.Forms.DataGridViewColumn> et une valeur d’énumération <xref:System.ComponentModel.ListSortDirection> en tant que paramètres. Cette surcharge est utile lors du tri par colonnes avec des valeurs qui peuvent être triées de manière significative, mais que vous ne souhaitez pas configurer pour le tri automatique. Lorsque vous appelez cette surcharge et transmettez une colonne avec une valeur de propriété <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> de <xref:System.Windows.Forms.DataGridViewColumnSortMode.Automatic?displayProperty=nameWithType>, les propriétés <xref:System.Windows.Forms.DataGridView.SortedColumn%2A> et <xref:System.Windows.Forms.DataGridView.SortOrder%2A> sont définies automatiquement et le glyphe de tri approprié apparaît dans l’en-tête de colonne.  
  
> [!NOTE]
> Lorsque le contrôle <xref:System.Windows.Forms.DataGridView> est lié à une source de données externe en définissant la propriété <xref:System.Windows.Forms.DataGridView.DataSource%2A>, la surcharge de la méthode `Sort(DataGridViewColumn,ListSortDirection)` ne fonctionne pas pour les colonnes indépendantes. En outre, lorsque la propriété <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> est `true`, vous pouvez appeler cette surcharge uniquement pour les colonnes dépendantes. Pour déterminer si une colonne est liée aux données, vérifiez la valeur de la propriété <xref:System.Windows.Forms.DataGridViewColumn.IsDataBound%2A>. Le tri des colonnes indépendantes en mode dépendant n’est pas pris en charge.  
  
## <a name="custom-sorting"></a>Tri personnalisé  
 Vous pouvez personnaliser <xref:System.Windows.Forms.DataGridView> à l’aide de la surcharge `Sort(IComparer)` de la méthode <xref:System.Windows.Forms.DataGridView.Sort%2A> ou en gérant l’événement <xref:System.Windows.Forms.DataGridView.SortCompare>.  
  
 La surcharge de méthode `Sort(IComparer)` prend une instance d’une classe qui implémente l’interface <xref:System.Collections.IComparer> en tant que paramètre. Cette surcharge est utile lorsque vous souhaitez fournir un tri personnalisé. par exemple, lorsque les valeurs d’une colonne n’ont pas d’ordre de tri naturel ou lorsque l’ordre de tri naturel n’est pas approprié. Dans ce cas, vous ne pouvez pas utiliser le tri automatique, mais vous pouvez toujours souhaiter que vos utilisateurs puissent effectuer un tri en cliquant sur les en-têtes de colonne. Vous pouvez appeler cette surcharge dans un gestionnaire pour l’événement <xref:System.Windows.Forms.DataGridView.ColumnHeaderMouseClick> si vous n’utilisez pas d’en-têtes de colonne pour la sélection.  
  
> [!NOTE]
> La surcharge de méthode `Sort(IComparer)` fonctionne uniquement lorsque le contrôle <xref:System.Windows.Forms.DataGridView> n’est pas lié à une source de données externe et que la valeur de la propriété <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> est `false`. Pour personnaliser le tri des colonnes liées à une source de données externe, vous devez utiliser les opérations de tri fournies par la source de données. En mode virtuel, vous devez fournir vos propres opérations de tri pour les colonnes indépendantes.  
  
 Pour utiliser la surcharge de méthode `Sort(IComparer)`, vous devez créer votre propre classe qui implémente l’interface <xref:System.Collections.IComparer>. Cette interface requiert que votre classe implémente la méthode <xref:System.Collections.IComparer.Compare%2A?displayProperty=nameWithType>, à laquelle le <xref:System.Windows.Forms.DataGridView> passe <xref:System.Windows.Forms.DataGridViewRow> objets comme entrée lorsque la surcharge de méthode `Sort(IComparer)` est appelée. Cela vous permet de calculer l’ordre correct des lignes en fonction des valeurs d’une colonne.  
  
 La surcharge de méthode `Sort(IComparer)` ne définit pas les propriétés <xref:System.Windows.Forms.DataGridView.SortedColumn%2A> et <xref:System.Windows.Forms.DataGridView.SortOrder%2A>. vous devez donc toujours définir la propriété <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.SortGlyphDirection%2A?displayProperty=nameWithType> pour afficher le glyphe de tri.  
  
 Comme alternative à la surcharge de méthode `Sort(IComparer)`, vous pouvez fournir un tri personnalisé en implémentant un gestionnaire pour l’événement <xref:System.Windows.Forms.DataGridView.SortCompare>. Cet événement se produit lorsque les utilisateurs cliquent sur les en-têtes de colonnes configurés pour le tri automatique ou lorsque vous appelez la surcharge `Sort(DataGridViewColumn,ListSortDirection)` de la méthode <xref:System.Windows.Forms.DataGridView.Sort%2A>. L’événement se produit pour chaque paire de lignes dans le contrôle, ce qui vous permet de calculer le bon ordre.  
  
> [!NOTE]
> L’événement <xref:System.Windows.Forms.DataGridView.SortCompare> ne se produit pas lorsque la propriété <xref:System.Windows.Forms.DataGridView.DataSource%2A> est définie ou lorsque la valeur de la propriété <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> est `true`.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.Sort%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.SortedColumn%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.SortOrder%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.SortGlyphDirection%2A?displayProperty=nameWithType>
- [Tri des données dans le contrôle DataGridView Windows Forms](sorting-data-in-the-windows-forms-datagridview-control.md)
- [Comment : définir les modes de tri des colonnes du contrôle DataGridView Windows Forms](set-the-sort-modes-for-columns-wf-datagridview-control.md)
- [Guide pratique pour personnaliser le tri dans le contrôle DataGridView Windows Forms](how-to-customize-sorting-in-the-windows-forms-datagridview-control.md)
