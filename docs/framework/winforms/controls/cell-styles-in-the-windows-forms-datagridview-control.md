---
title: Styles de cellules dans le contrôle DataGridView
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], cell styles
- cells [Windows Forms], styles
- data grids [Windows Forms], cell styles
ms.assetid: dbb75ed6-8804-4232-8382-f9920c2e380c
ms.openlocfilehash: fe56033a5adbe7719c64695c8f9ebc4f3644fc65
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746158"
---
# <a name="cell-styles-in-the-windows-forms-datagridview-control"></a>Styles de cellules dans le contrôle DataGridView Windows Forms
Chaque cellule dans le contrôle <xref:System.Windows.Forms.DataGridView> peut avoir son propre style, tel que le format de texte, la couleur d’arrière-plan, la couleur de premier plan et la police. En général, toutefois, plusieurs cellules partagent des caractéristiques de style particulières.  
  
 Les groupes de cellules qui partagent des styles peuvent inclure toutes les cellules dans des lignes ou des colonnes particulières, toutes les cellules qui contiennent des valeurs particulières ou toutes les cellules du contrôle. Comme ces groupes se chevauchent, chaque cellule peut obtenir ses informations de style à partir de plusieurs emplacements. Par exemple, vous souhaiterez peut-être que chaque cellule d’un contrôle de <xref:System.Windows.Forms.DataGridView> utilise la même police, mais uniquement les cellules des colonnes monétaires pour utiliser le format monétaire, et uniquement les cellules monétaires avec des nombres négatifs pour utiliser une couleur de premier plan rouge.  
  
## <a name="the-datagridviewcellstyle-class"></a>Classe DataGridViewCellStyle  
 La classe <xref:System.Windows.Forms.DataGridViewCellStyle> contient les propriétés suivantes relatives au style visuel :  
  
- <xref:System.Windows.Forms.DataGridViewCellStyle.BackColor%2A> et <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A>  
  
- <xref:System.Windows.Forms.DataGridViewCellStyle.SelectionBackColor%2A> et <xref:System.Windows.Forms.DataGridViewCellStyle.SelectionForeColor%2A>  
  
- <xref:System.Windows.Forms.DataGridViewCellStyle.Font%2A>  
  
 Cette classe contient également les propriétés suivantes relatives à la mise en forme :  
  
- <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> et <xref:System.Windows.Forms.DataGridViewCellStyle.FormatProvider%2A>  
  
- <xref:System.Windows.Forms.DataGridViewCellStyle.NullValue%2A> et <xref:System.Windows.Forms.DataGridViewCellStyle.DataSourceNullValue%2A>  
  
- <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A>  
  
- <xref:System.Windows.Forms.DataGridViewCellStyle.Alignment%2A>  
  
- <xref:System.Windows.Forms.DataGridViewCellStyle.Padding%2A>  
  
 Pour plus d’informations sur ces propriétés et d’autres propriétés de style de cellule, consultez la documentation de référence <xref:System.Windows.Forms.DataGridViewCellStyle> et les rubriques figurant dans la section Voir aussi ci-dessous.  
  
## <a name="using-datagridviewcellstyle-objects"></a>Utilisation d’objets DataGridViewCellStyle  
 Vous pouvez récupérer des objets <xref:System.Windows.Forms.DataGridViewCellStyle> à partir de différentes propriétés des classes <xref:System.Windows.Forms.DataGridView>, <xref:System.Windows.Forms.DataGridViewColumn>, <xref:System.Windows.Forms.DataGridViewRow>et <xref:System.Windows.Forms.DataGridViewCell> et leurs classes dérivées. Si l’une de ces propriétés n’a pas encore été définie, la récupération de sa valeur créera un nouvel objet <xref:System.Windows.Forms.DataGridViewCellStyle>. Vous pouvez également instancier vos propres objets <xref:System.Windows.Forms.DataGridViewCellStyle> et les assigner à ces propriétés.  
  
 Vous pouvez éviter la duplication inutile des informations de style en partageant des objets <xref:System.Windows.Forms.DataGridViewCellStyle> entre plusieurs éléments <xref:System.Windows.Forms.DataGridView>. Étant donné que les styles définis au niveau des niveaux de contrôle, de colonne et de ligne sont filtrés jusqu’au niveau de la cellule, vous pouvez également éviter la duplication de style en définissant uniquement les propriétés de style à chaque niveau qui diffèrent des niveaux ci-dessus. Cela est décrit plus en détail dans la section héritage de style qui suit.  
  
 Le tableau suivant répertorie les propriétés principales qui obtiennent ou définissent des objets <xref:System.Windows.Forms.DataGridViewCellStyle>.  
  
|Les|Classes|Description|  
|--------------|-------------|-----------------|  
|`DefaultCellStyle`|<xref:System.Windows.Forms.DataGridView>, <xref:System.Windows.Forms.DataGridViewColumn>, <xref:System.Windows.Forms.DataGridViewRow>et classes dérivées|Obtient ou définit les styles par défaut utilisés par toutes les cellules du contrôle entier (y compris les cellules d’en-tête), dans une colonne ou dans une ligne.|  
|<xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A>|<xref:System.Windows.Forms.DataGridView>|Obtient ou définit les styles de cellules par défaut utilisés par toutes les lignes du contrôle. Cela n’inclut pas les cellules d’en-tête.|  
|<xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A>|<xref:System.Windows.Forms.DataGridView>|Obtient ou définit les styles de cellules par défaut utilisés par les lignes en alternance dans le contrôle. Utilisé pour créer un effet de type comptabilité.|  
|<xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A>|<xref:System.Windows.Forms.DataGridView>|Obtient ou définit les styles de cellules par défaut utilisés par les en-têtes de lignes du contrôle. Remplacé par le thème actuel si les styles visuels sont activés.|  
|<xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A>|<xref:System.Windows.Forms.DataGridView>|Obtient ou définit les styles de cellules par défaut utilisés par les en-têtes de colonnes du contrôle. Remplacé par le thème actuel si les styles visuels sont activés.|  
|<xref:System.Windows.Forms.DataGridViewCell.Style%2A>|classes <xref:System.Windows.Forms.DataGridViewCell> et dérivées|Obtient ou définit les styles spécifiés au niveau de la cellule. Ces styles remplacent ceux hérités des niveaux supérieurs.|  
|`InheritedStyle`|<xref:System.Windows.Forms.DataGridViewCell>, <xref:System.Windows.Forms.DataGridViewRow>, <xref:System.Windows.Forms.DataGridViewColumn>et classes dérivées|Obtient tous les styles actuellement appliqués à la cellule, à la ligne ou à la colonne, y compris les styles hérités de niveaux supérieurs.|  
  
 Comme indiqué ci-dessus, l’obtention de la valeur d’une propriété de style instancie automatiquement un nouvel objet <xref:System.Windows.Forms.DataGridViewCellStyle> si la propriété n’a pas été définie précédemment. Pour éviter de créer ces objets inutilement, les classes de lignes et de colonnes ont une propriété <xref:System.Windows.Forms.DataGridViewBand.HasDefaultCellStyle%2A> que vous pouvez vérifier pour déterminer si la propriété <xref:System.Windows.Forms.DataGridViewBand.DefaultCellStyle%2A> a été définie. De même, les classes de cellule ont une propriété <xref:System.Windows.Forms.DataGridViewCell.HasStyle%2A> qui indique si la propriété <xref:System.Windows.Forms.DataGridViewCell.Style%2A> a été définie.  
  
 Chacune des propriétés de style a un événement *PropertyName*`Changed` correspondant sur le contrôle <xref:System.Windows.Forms.DataGridView>. Pour les propriétés de ligne, de colonne et de cellule, le nom de l’événement commence par «`Row`», «`Column`» ou «`Cell`» (par exemple, <xref:System.Windows.Forms.DataGridView.RowDefaultCellStyleChanged>). Chacun de ces événements se produit lorsque la propriété de style correspondante est définie sur un objet de <xref:System.Windows.Forms.DataGridViewCellStyle> différent. Ces événements ne se produisent pas lorsque vous récupérez un objet <xref:System.Windows.Forms.DataGridViewCellStyle> à partir d’une propriété de style et modifiez ses valeurs de propriété. Pour répondre aux modifications apportées aux objets de style de cellule eux-mêmes, gérez l’événement <xref:System.Windows.Forms.DataGridView.CellStyleContentChanged>.  
  
## <a name="style-inheritance"></a>Héritage de style  
 Chaque <xref:System.Windows.Forms.DataGridViewCell> obtient son apparence à partir de sa propriété <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A>. L’objet <xref:System.Windows.Forms.DataGridViewCellStyle> retourné par cette propriété hérite ses valeurs d’une hiérarchie de propriétés de type <xref:System.Windows.Forms.DataGridViewCellStyle>. Ces propriétés sont répertoriées ci-dessous dans l’ordre dans lequel les <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A> pour les cellules non-en-tête obtiennent ses valeurs.  
  
1. <xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=nameWithType>  
  
2. <xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
3. <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A?displayProperty=nameWithType> (uniquement pour les cellules des lignes avec des numéros d’index impairs)  
  
4. <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>  
  
5. <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
6. <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
 Pour les cellules d’en-tête de ligne et de colonne, la propriété <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A> est remplie par des valeurs de la liste suivante de propriétés sources dans l’ordre indiqué.  
  
1. <xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=nameWithType>  
  
2. <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A?displayProperty=nameWithType> ou <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A?displayProperty=nameWithType>  
  
3. <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
 Le diagramme suivant illustre ce processus.  
  
 ![Propriétés de type DataGridViewCellStyle](./media/cell-styles-in-the-windows-forms-datagridview-control/datagridviewcells-inheritance-diagram.gif "Diagramme d’héritage DataGridViewCells")  
  
 Vous pouvez également accéder aux styles hérités par des lignes et des colonnes spécifiques. La propriété Column <xref:System.Windows.Forms.DataGridViewColumn.InheritedStyle%2A> hérite ses valeurs des propriétés suivantes.  
  
1. <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
2. <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
 La propriété Row <xref:System.Windows.Forms.DataGridViewRow.InheritedStyle%2A> hérite ses valeurs des propriétés suivantes.  
  
1. <xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
2. <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A?displayProperty=nameWithType> (uniquement pour les cellules des lignes avec des numéros d’index impairs)  
  
3. <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>  
  
4. <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
 Pour chaque propriété d’un objet <xref:System.Windows.Forms.DataGridViewCellStyle> retourné par une propriété `InheritedStyle`, la valeur de la propriété est obtenue à partir du premier style de cellule dans la liste appropriée dont la propriété correspondante est définie sur une valeur autre que les valeurs par défaut de la classe <xref:System.Windows.Forms.DataGridViewCellStyle>.  
  
 Le tableau suivant illustre la façon dont la valeur de la propriété <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A> pour une cellule d’exemple est héritée de la colonne qui la contient.  
  
|Propriété de type `DataGridViewCellStyle`|Exemple de valeur `ForeColor` pour l’objet récupéré|  
|----------------------------------------------|----------------------------------------------------|  
|<xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.Empty?displayProperty=nameWithType>|  
|<xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.Red%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.Empty?displayProperty=nameWithType>|  
|<xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.Empty?displayProperty=nameWithType>|  
|<xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.DarkBlue%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.Black%2A?displayProperty=nameWithType>|  
  
 Dans ce cas, la valeur <xref:System.Drawing.Color.Red%2A?displayProperty=nameWithType> de la ligne de la cellule est la première valeur réelle de la liste. Cela devient la valeur de la propriété <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A> de la <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A>de la cellule.  
  
 Le diagramme suivant illustre comment différentes propriétés de <xref:System.Windows.Forms.DataGridViewCellStyle> peuvent hériter de leurs valeurs à partir de différents emplacements.  
  
 ![Héritage de&#45;la valeur de propriété DataGridView](./media/cell-styles-in-the-windows-forms-datagridview-control/datagridviewcells-value-inheritance-diagram.gif "Diagramme d’héritage de valeur DataGridViewCells")  
  
 En tirant parti de l’héritage de style, vous pouvez fournir les styles appropriés pour l’ensemble du contrôle sans avoir à spécifier les mêmes informations à plusieurs emplacements.  
  
 Bien que les cellules d’en-tête participent à l’héritage de style comme décrit, les objets retournés par les propriétés <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A> et <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A> du contrôle <xref:System.Windows.Forms.DataGridView> ont des valeurs de propriété initiales qui remplacent les valeurs de propriété de l’objet retourné par la propriété <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A>. Si vous souhaitez que les propriétés définies pour l’objet retourné par la propriété <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A> s’appliquent aux en-têtes de ligne et de colonne, vous devez définir les propriétés correspondantes des objets retournés par les propriétés <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A> et <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A> aux valeurs par défaut indiquées pour la classe <xref:System.Windows.Forms.DataGridViewCellStyle>.  
  
> [!NOTE]
> Si les styles visuels sont activés, les en-têtes de lignes et de colonnes (à l’exception de la <xref:System.Windows.Forms.DataGridView.TopLeftHeaderCell%2A>) sont automatiquement mis en forme par le thème actuel, en substituant les styles spécifiés par ces propriétés.  
  
 Les types <xref:System.Windows.Forms.DataGridViewButtonColumn>, <xref:System.Windows.Forms.DataGridViewImageColumn>et <xref:System.Windows.Forms.DataGridViewCheckBoxColumn> initialisent également certaines valeurs de l’objet retourné par la propriété <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> de la colonne. Pour plus d’informations, consultez la documentation de référence pour ces types.  
  
## <a name="setting-styles-dynamically"></a>Définir des styles de manière dynamique  
 Pour personnaliser les styles de cellules avec des valeurs particulières, implémentez un gestionnaire pour l’événement <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType>. Les gestionnaires de cet événement reçoivent un argument du type <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs>. Cet objet contient des propriétés qui vous permettent de déterminer la valeur de la cellule mise en forme, ainsi que son emplacement dans le contrôle de <xref:System.Windows.Forms.DataGridView>. Cet objet contient également une propriété <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs.CellStyle%2A> qui est initialisée à la valeur de la propriété <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A> de la cellule mise en forme. Vous pouvez modifier les propriétés de style de la cellule pour spécifier les informations de style appropriées à la valeur et à l’emplacement de la cellule.  
  
> [!NOTE]
> Les événements <xref:System.Windows.Forms.DataGridView.RowPrePaint> et <xref:System.Windows.Forms.DataGridView.RowPostPaint> reçoivent également un objet <xref:System.Windows.Forms.DataGridViewCellStyle> dans les données d’événement, mais dans le cas contraire, il s’agit d’une copie de la propriété Row <xref:System.Windows.Forms.DataGridViewRow.InheritedStyle%2A> à des fins de lecture seule, et les modifications apportées n’affectent pas le contrôle.  
  
 Vous pouvez également modifier dynamiquement les styles de cellules individuelles en réponse à des événements tels que les événements <xref:System.Windows.Forms.DataGridView.CellMouseEnter?displayProperty=nameWithType> et <xref:System.Windows.Forms.DataGridView.CellMouseLeave>. Par exemple, dans un gestionnaire pour l’événement <xref:System.Windows.Forms.DataGridView.CellMouseEnter>, vous pouvez stocker la valeur actuelle de la couleur d’arrière-plan de la cellule (récupérée via la propriété <xref:System.Windows.Forms.DataGridViewCell.Style%2A> de la cellule), puis lui attribuer une nouvelle couleur qui met en surbrillance la cellule lorsque la souris pointe sur celle-ci. Dans un gestionnaire pour l’événement <xref:System.Windows.Forms.DataGridView.CellMouseLeave>, vous pouvez restaurer la couleur d’arrière-plan à la valeur d’origine.  
  
> [!NOTE]
> La mise en cache des valeurs stockées dans la propriété <xref:System.Windows.Forms.DataGridViewCell.Style%2A> de la cellule est importante, qu’une valeur de style particulière soit définie ou non. Si vous remplacez temporairement un paramètre de style, le fait de le restaurer à son état d’origine « non défini » garantit que la cellule revient à hériter du paramètre de style d’un niveau supérieur. Si vous devez déterminer le style réel en vigueur pour une cellule, que le style soit hérité ou non, utilisez la propriété <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A> de la cellule.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewBand.InheritedStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewRow.InheritedStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.InheritedStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewBand.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.CellStyleContentChanged?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.RowPostPaint?displayProperty=nameWithType>
- [Mises en forme et styles de base dans le contrôle DataGridView Windows Forms](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
- [Guide pratique pour définir les styles de cellules par défaut pour le contrôle DataGridView Windows Forms](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md)
- [Mise en forme de données dans le contrôle DataGridView Windows Forms](data-formatting-in-the-windows-forms-datagridview-control.md)
