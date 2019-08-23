---
title: Styles de cellules dans le contrôle DataGridView Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], cell styles
- cells [Windows Forms], styles
- data grids [Windows Forms], cell styles
ms.assetid: dbb75ed6-8804-4232-8382-f9920c2e380c
ms.openlocfilehash: be4c47db5c56685a84153a9ae4a9a2fe14c6adad
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917767"
---
# <a name="cell-styles-in-the-windows-forms-datagridview-control"></a>Styles de cellules dans le contrôle DataGridView Windows Forms
Chaque cellule dans le <xref:System.Windows.Forms.DataGridView> contrôle peut avoir son propre style, tel que le format de texte, la couleur d’arrière-plan, la couleur de premier plan et la police. En général, toutefois, plusieurs cellules partagent des caractéristiques de style particulières.  
  
 Les groupes de cellules qui partagent des styles peuvent inclure toutes les cellules dans des lignes ou des colonnes particulières, toutes les cellules qui contiennent des valeurs particulières ou toutes les cellules du contrôle. Comme ces groupes se chevauchent, chaque cellule peut obtenir ses informations de style à partir de plusieurs emplacements. Par exemple, vous souhaiterez peut-être que <xref:System.Windows.Forms.DataGridView> chaque cellule d’un contrôle utilise la même police, mais uniquement les cellules des colonnes monétaires pour utiliser le format monétaire, et uniquement les cellules monétaires avec des nombres négatifs pour utiliser une couleur de premier plan rouge.  
  
## <a name="the-datagridviewcellstyle-class"></a>Classe DataGridViewCellStyle  
 La <xref:System.Windows.Forms.DataGridViewCellStyle> classe contient les propriétés suivantes relatives au style visuel:  
  
- <xref:System.Windows.Forms.DataGridViewCellStyle.BackColor%2A> et <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A>  
  
- <xref:System.Windows.Forms.DataGridViewCellStyle.SelectionBackColor%2A> et <xref:System.Windows.Forms.DataGridViewCellStyle.SelectionForeColor%2A>  
  
- <xref:System.Windows.Forms.DataGridViewCellStyle.Font%2A>  
  
 Cette classe contient également les propriétés suivantes relatives à la mise en forme:  
  
- <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> et <xref:System.Windows.Forms.DataGridViewCellStyle.FormatProvider%2A>  
  
- <xref:System.Windows.Forms.DataGridViewCellStyle.NullValue%2A> et <xref:System.Windows.Forms.DataGridViewCellStyle.DataSourceNullValue%2A>  
  
- <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A>  
  
- <xref:System.Windows.Forms.DataGridViewCellStyle.Alignment%2A>  
  
- <xref:System.Windows.Forms.DataGridViewCellStyle.Padding%2A>  
  
 Pour plus d’informations sur ces propriétés et d’autres propriétés de style de cellule <xref:System.Windows.Forms.DataGridViewCellStyle> , consultez la documentation de référence et les rubriques figurant dans la section Voir aussi ci-dessous.  
  
## <a name="using-datagridviewcellstyle-objects"></a>Utilisation d’objets DataGridViewCellStyle  
 Vous pouvez récupérer <xref:System.Windows.Forms.DataGridViewCellStyle> des objets à partir de différentes <xref:System.Windows.Forms.DataGridView>propriétés <xref:System.Windows.Forms.DataGridViewColumn>des <xref:System.Windows.Forms.DataGridViewRow> <xref:System.Windows.Forms.DataGridViewCell> classes,, et et de leurs classes dérivées. Si l’une de ces propriétés n’a pas encore été définie, la récupération de sa valeur créera un nouvel <xref:System.Windows.Forms.DataGridViewCellStyle> objet. Vous pouvez également instancier vos <xref:System.Windows.Forms.DataGridViewCellStyle> propres objets et les assigner à ces propriétés.  
  
 Vous pouvez éviter la duplication inutile des informations de style <xref:System.Windows.Forms.DataGridViewCellStyle> en partageant <xref:System.Windows.Forms.DataGridView> des objets entre plusieurs éléments. Étant donné que les styles définis au niveau des niveaux de contrôle, de colonne et de ligne sont filtrés jusqu’au niveau de la cellule, vous pouvez également éviter la duplication de style en définissant uniquement les propriétés de style à chaque niveau qui diffèrent des niveaux ci-dessus. Cela est décrit plus en détail dans la section héritage de style qui suit.  
  
 Le tableau suivant répertorie les propriétés principales qui obtiennent ou <xref:System.Windows.Forms.DataGridViewCellStyle> définissent des objets.  
  
|Propriété|Classes|Description|  
|--------------|-------------|-----------------|  
|`DefaultCellStyle`|<xref:System.Windows.Forms.DataGridView>classes dérivées, <xref:System.Windows.Forms.DataGridViewColumn>,et <xref:System.Windows.Forms.DataGridViewRow>|Obtient ou définit les styles par défaut utilisés par toutes les cellules du contrôle entier (y compris les cellules d’en-tête), dans une colonne ou dans une ligne.|  
|<xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A>|<xref:System.Windows.Forms.DataGridView>|Obtient ou définit les styles de cellules par défaut utilisés par toutes les lignes du contrôle. Cela n’inclut pas les cellules d’en-tête.|  
|<xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A>|<xref:System.Windows.Forms.DataGridView>|Obtient ou définit les styles de cellules par défaut utilisés par les lignes en alternance dans le contrôle. Utilisé pour créer un effet de type comptabilité.|  
|<xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A>|<xref:System.Windows.Forms.DataGridView>|Obtient ou définit les styles de cellules par défaut utilisés par les en-têtes de lignes du contrôle. Remplacé par le thème actuel si les styles visuels sont activés.|  
|<xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A>|<xref:System.Windows.Forms.DataGridView>|Obtient ou définit les styles de cellules par défaut utilisés par les en-têtes de colonnes du contrôle. Remplacé par le thème actuel si les styles visuels sont activés.|  
|<xref:System.Windows.Forms.DataGridViewCell.Style%2A>|<xref:System.Windows.Forms.DataGridViewCell>et classes dérivées|Obtient ou définit les styles spécifiés au niveau de la cellule. Ces styles remplacent ceux hérités des niveaux supérieurs.|  
|`InheritedStyle`|<xref:System.Windows.Forms.DataGridViewCell>classes dérivées, <xref:System.Windows.Forms.DataGridViewRow>,et <xref:System.Windows.Forms.DataGridViewColumn>|Obtient tous les styles actuellement appliqués à la cellule, à la ligne ou à la colonne, y compris les styles hérités de niveaux supérieurs.|  
  
 Comme indiqué ci-dessus, l’obtention de la valeur d’une propriété de style <xref:System.Windows.Forms.DataGridViewCellStyle> instancie automatiquement un nouvel objet si la propriété n’a pas été définie précédemment. Pour éviter de créer ces objets inutilement, les classes de lignes et <xref:System.Windows.Forms.DataGridViewBand.HasDefaultCellStyle%2A> de colonnes ont une propriété que vous pouvez vérifier <xref:System.Windows.Forms.DataGridViewBand.DefaultCellStyle%2A> pour déterminer si la propriété a été définie. De même, les classes de cellule ont <xref:System.Windows.Forms.DataGridViewCell.HasStyle%2A> une propriété qui indique si <xref:System.Windows.Forms.DataGridViewCell.Style%2A> la propriété a été définie.  
  
 Chacune des propriétés de style a un événement *NomPropriété* `Changed` correspondant sur le <xref:System.Windows.Forms.DataGridView> contrôle. Pour les propriétés de ligne, de colonne et de cellule, le nom de l’événement`Row`commence par «`Column`», «»`Cell`ou «» (par <xref:System.Windows.Forms.DataGridView.RowDefaultCellStyleChanged>exemple,). Chacun de ces événements se produit lorsque la propriété de style correspondante est définie sur <xref:System.Windows.Forms.DataGridViewCellStyle> un autre objet. Ces événements ne se produisent pas lorsque vous récupérez un <xref:System.Windows.Forms.DataGridViewCellStyle> objet à partir d’une propriété de style et modifiez ses valeurs de propriété. Pour répondre aux modifications apportées aux objets de style de cellule <xref:System.Windows.Forms.DataGridView.CellStyleContentChanged> eux-mêmes, gérez l’événement.  
  
## <a name="style-inheritance"></a>Héritage de style  
 Chaque <xref:System.Windows.Forms.DataGridViewCell> obtient son apparence à partir <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A> de sa propriété. L' <xref:System.Windows.Forms.DataGridViewCellStyle> objet retourné par cette propriété hérite ses valeurs d’une hiérarchie de propriétés de type <xref:System.Windows.Forms.DataGridViewCellStyle>. Ces propriétés sont répertoriées ci-dessous dans l’ordre <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A> dans lequel le pour les cellules qui n’ont pas d’en-tête obtient ses valeurs.  
  
1. <xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=nameWithType>  
  
2. <xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
3. <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A?displayProperty=nameWithType>(uniquement pour les cellules des lignes avec des numéros d’index impair)  
  
4. <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>  
  
5. <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
6. <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
 Pour les cellules d’en-tête de <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A> ligne et de colonne, la propriété est remplie par des valeurs de la liste suivante de propriétés sources dans l’ordre donné.  
  
1. <xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=nameWithType>  
  
2. <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A?displayProperty=nameWithType> ou <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A?displayProperty=nameWithType>  
  
3. <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
 Le diagramme suivant illustre ce processus.  
  
 ![Propriétés de type DataGridViewCellStyle](./media/cell-styles-in-the-windows-forms-datagridview-control/datagridviewcells-inheritance-diagram.gif "Diagramme d’héritage DataGridViewCells")  
  
 Vous pouvez également accéder aux styles hérités par des lignes et des colonnes spécifiques. La propriété <xref:System.Windows.Forms.DataGridViewColumn.InheritedStyle%2A> de colonne hérite ses valeurs des propriétés suivantes.  
  
1. <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
2. <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
 La propriété <xref:System.Windows.Forms.DataGridViewRow.InheritedStyle%2A> Row hérite ses valeurs des propriétés suivantes.  
  
1. <xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
2. <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A?displayProperty=nameWithType>(uniquement pour les cellules des lignes avec des numéros d’index impair)  
  
3. <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>  
  
4. <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
 Pour chaque propriété d’un <xref:System.Windows.Forms.DataGridViewCellStyle> objet retourné par une `InheritedStyle` propriété, la valeur de la propriété est obtenue à partir du style de la première cellule dans la liste appropriée dont la propriété correspondante est définie sur <xref:System.Windows.Forms.DataGridViewCellStyle> une valeur autre que les valeurs par défaut de la classe.  
  
 Le tableau suivant illustre la façon dont <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A> la valeur de la propriété d’un exemple de cellule est héritée de la colonne qui la contient.  
  
|Propriété de type`DataGridViewCellStyle`|Exemple `ForeColor` de valeur pour l’objet récupéré|  
|----------------------------------------------|----------------------------------------------------|  
|<xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.Empty?displayProperty=nameWithType>|  
|<xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.Red%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.Empty?displayProperty=nameWithType>|  
|<xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.Empty?displayProperty=nameWithType>|  
|<xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.DarkBlue%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.Black%2A?displayProperty=nameWithType>|  
  
 Dans ce cas, la <xref:System.Drawing.Color.Red%2A?displayProperty=nameWithType> valeur de la ligne de la cellule est la première valeur réelle de la liste. Cela devient la <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A> valeur de la propriété de la <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A>cellule.  
  
 Le diagramme suivant illustre la façon dont <xref:System.Windows.Forms.DataGridViewCellStyle> les différentes propriétés peuvent hériter de leurs valeurs à partir de différents emplacements.  
  
 ![Héritage de&#45;la valeur de propriété DataGridView](./media/cell-styles-in-the-windows-forms-datagridview-control/datagridviewcells-value-inheritance-diagram.gif "Diagramme d’héritage de valeur DataGridViewCells")  
  
 En tirant parti de l’héritage de style, vous pouvez fournir les styles appropriés pour l’ensemble du contrôle sans avoir à spécifier les mêmes informations à plusieurs emplacements.  
  
 Bien que les cellules d’en-tête participent à l’héritage de style comme <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A> décrit <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A> , les objets <xref:System.Windows.Forms.DataGridView> retournés par les propriétés et du contrôle ont des valeurs de propriété initiales qui remplacent les valeurs de propriété de l’objet retourné par la <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A> propriété. Si vous souhaitez que les propriétés définies pour l’objet retourné par <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A> la propriété s’appliquent aux en-têtes de ligne et de colonne, vous devez définir les propriétés correspondantes <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A> des <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A> objets retournés par les propriétés et aux valeurs par défaut indiquées pour la <xref:System.Windows.Forms.DataGridViewCellStyle> classe.  
  
> [!NOTE]
> Si les styles visuels sont activés, les en-têtes de lignes et de <xref:System.Windows.Forms.DataGridView.TopLeftHeaderCell%2A>colonnes (à l’exception de) sont automatiquement mis en forme par le thème actuel, en remplaçant les styles spécifiés par ces propriétés.  
  
 Les <xref:System.Windows.Forms.DataGridViewButtonColumn>types <xref:System.Windows.Forms.DataGridViewImageColumn>, <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> et <xref:System.Windows.Forms.DataGridViewCheckBoxColumn> initialisent également certaines valeurs de l’objet retourné par la propriété de colonne. Pour plus d’informations, consultez la documentation de référence pour ces types.  
  
## <a name="setting-styles-dynamically"></a>Définir des styles de manière dynamique  
 Pour personnaliser les styles de cellules avec des valeurs particulières, implémentez un gestionnaire <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> pour l’événement. Les <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs> gestionnaires de cet événement reçoivent un argument du type. Cet objet contient des propriétés qui vous permettent de déterminer la valeur de la cellule mise en forme, ainsi que <xref:System.Windows.Forms.DataGridView> son emplacement dans le contrôle. Cet objet contient également une <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs.CellStyle%2A> propriété qui est initialisée à la valeur de la <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A> propriété de la cellule mise en forme. Vous pouvez modifier les propriétés de style de la cellule pour spécifier les informations de style appropriées à la valeur et à l’emplacement de la cellule.  
  
> [!NOTE]
> Les <xref:System.Windows.Forms.DataGridView.RowPrePaint> événements <xref:System.Windows.Forms.DataGridView.RowPostPaint> et reçoivent également un <xref:System.Windows.Forms.DataGridViewCellStyle> objet dans les données d’événement, mais dans leur cas, il s’agit d’une copie <xref:System.Windows.Forms.DataGridViewRow.InheritedStyle%2A> de la propriété de ligne à des fins de lecture seule, et les modifications apportées à ce dernier n’affectent pas le contrôle.  
  
 Vous pouvez également modifier dynamiquement les styles de cellules individuelles en réponse à des événements tels que <xref:System.Windows.Forms.DataGridView.CellMouseEnter?displayProperty=nameWithType> les <xref:System.Windows.Forms.DataGridView.CellMouseLeave> événements et. Par exemple, dans un gestionnaire pour l' <xref:System.Windows.Forms.DataGridView.CellMouseEnter> événement, vous pouvez stocker la valeur actuelle de la couleur d’arrière-plan de la cellule ( <xref:System.Windows.Forms.DataGridViewCell.Style%2A> récupérée via la propriété de la cellule), puis lui affecter une nouvelle couleur qui met en surbrillance la cellule lorsque la souris pointe sur celle-ci. Dans un gestionnaire pour l' <xref:System.Windows.Forms.DataGridView.CellMouseLeave> événement, vous pouvez restaurer la couleur d’arrière-plan à la valeur d’origine.  
  
> [!NOTE]
> La mise en cache des valeurs stockées dans <xref:System.Windows.Forms.DataGridViewCell.Style%2A> la propriété de la cellule est importante, qu’une valeur de style particulière soit définie ou non. Si vous remplacez temporairement un paramètre de style, le fait de le restaurer à son état d’origine «non défini» garantit que la cellule revient à hériter du paramètre de style d’un niveau supérieur. Si vous devez déterminer le style réel en vigueur pour une cellule, que le style soit hérité ou non, utilisez la propriété de <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A> la cellule.  
  
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
- [Guide pratique : Définir les styles de cellules par défaut pour le contrôle DataGridView Windows Forms](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md)
- [Mise en forme de données dans le contrôle DataGridView Windows Forms](data-formatting-in-the-windows-forms-datagridview-control.md)
