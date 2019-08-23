---
title: Options de dimensionnement dans le contrôle DataGridView Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], row sizing
- data grids [Windows Forms], column sizing
- DataGridView control [Windows Forms], column sizing
- DataGridView control [Windows Forms], sizing options
- data grids [Windows Forms], row sizing
- data grids [Windows Forms], sizing options
ms.assetid: a5620a9c-0d06-41e3-8934-c25ddb16c9e6
ms.openlocfilehash: a8e2e05877746dfb043b7e8ac2a6c2b7017883c3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960415"
---
# <a name="sizing-options-in-the-windows-forms-datagridview-control"></a>Options de dimensionnement dans le contrôle DataGridView Windows Forms
<xref:System.Windows.Forms.DataGridView>les lignes, les colonnes et les en-têtes peuvent changer de taille à la suite de nombreuses occurrences différentes. Le tableau suivant présente ces occurrences.  
  
|Occurrence|Description|  
|----------------|-----------------|  
|Redimensionnement de l’utilisateur|Les utilisateurs peuvent effectuer des ajustements de taille en faisant glisser ou en double-cliquant sur des séparateurs de ligne, de colonne ou d’en-tête.|  
|Redimensionnement du contrôle|En mode de remplissage de colonne, les largeurs de colonne changent lorsque la largeur du contrôle change; par exemple, lorsque le contrôle est ancré à son formulaire parent et que l’utilisateur redimensionne le formulaire.|  
|Modification de la valeur de la cellule|En mode de dimensionnement automatique basé sur le contenu, les tailles changent en fonction des nouvelles valeurs d’affichage.|  
|Appel de méthode|Le redimensionnement basé sur le contenu par programme vous permet d’effectuer des ajustements de taille opportunistes en fonction des valeurs de cellule au moment de l’appel de la méthode.|  
|Paramètre de propriété|Vous pouvez également définir des valeurs de hauteur et de largeur spécifiques.|  
  
 Par défaut, le redimensionnement de l’utilisateur est activé, le dimensionnement automatique est désactivé et les valeurs de cellule qui sont plus larges que leurs colonnes sont découpées.  
  
 Le tableau suivant répertorie les scénarios que vous pouvez utiliser pour ajuster le comportement par défaut ou pour utiliser des options de dimensionnement spécifiques afin d’obtenir des effets particuliers.  
  
|Scénario|Implémentation|  
|--------------|--------------------|  
|Utilisez le mode de remplissage de colonne pour afficher des données de taille similaire dans un nombre relativement faible de colonnes qui occupent toute la largeur du contrôle sans afficher la barre de défilement horizontale.|Affectez à la propriété <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A> la valeur <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode.Fill>.|  
|Utilisez le mode de remplissage de colonne avec des valeurs d’affichage de tailles différentes.|Affectez à la propriété <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A> la valeur <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode.Fill>. Initialisez les largeurs de colonne relatives en définissant les propriétés de colonne <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> ou en appelant la méthode de contrôle <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A> après avoir rempli le contrôle avec des données.|  
|Utilisez le mode de remplissage de colonne avec des valeurs d’importance variable.|Affectez à la propriété <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A> la valeur <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode.Fill>. Définissez des <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> valeurs élevées pour les colonnes qui doivent toujours afficher certaines de leurs données ou utilisez une option de dimensionnement autre que le mode de remplissage pour des colonnes spécifiques.|  
|Utilisez le mode de remplissage de colonne pour éviter d’afficher l’arrière-plan du contrôle.|Affectez <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> à <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.Fill> la propriété de la dernière colonne la valeur et utilisez d’autres options de dimensionnement pour les autres colonnes. Si les autres colonnes utilisent une trop grande partie de l’espace disponible, <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> définissez la propriété de la dernière colonne.|  
|Affichez une colonne de largeur fixe, telle qu’une colonne d’icône ou d’ID.|Affectez <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.None> à <xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A> la <xref:System.Windows.Forms.DataGridViewTriState.False> valeur <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> et à pour la colonne. Initialisez sa largeur en définissant <xref:System.Windows.Forms.DataGridViewColumn.Width%2A> la propriété ou en appelant la <xref:System.Windows.Forms.DataGridView.AutoResizeColumn%2A> méthode de contrôle après avoir rempli le contrôle avec des données.|  
|Ajustez les tailles automatiquement chaque fois que le contenu des cellules change pour éviter le découpage et pour optimiser l’utilisation de l’espace.|Affectez à une propriété de dimensionnement automatique une valeur qui représente un mode de dimensionnement basé sur le contenu. Pour éviter une altération des performances lorsque vous travaillez avec de grandes quantités de données, utilisez un mode de dimensionnement qui calcule uniquement les lignes affichées.|  
|Ajustez les tailles pour ajuster les valeurs aux lignes affichées afin d’éviter des pénalités en matière de performances lorsque vous travaillez avec de nombreuses lignes.|Utilisez les valeurs d’énumération du mode de redimensionnement appropriées avec un redimensionnement automatique ou par programme. Pour ajuster les tailles en fonction des valeurs des lignes récemment affichées lors du défilement, appelez une méthode de redimensionnement dans un <xref:System.Windows.Forms.DataGridView.Scroll> gestionnaire d’événements. Pour personnaliser le redimensionnement du double-clic de l’utilisateur afin que seules les valeurs des lignes affichées déterminent les nouvelles tailles, <xref:System.Windows.Forms.DataGridView.RowDividerDoubleClick> appelez <xref:System.Windows.Forms.DataGridView.ColumnDividerDoubleClick> une méthode de redimensionnement dans un gestionnaire d’événements ou.|  
|Ajustez les tailles en fonction du contenu des cellules uniquement à des moments précis pour éviter des pénalités en matière de performances ou pour permettre le redimensionnement de l’utilisateur.|Appeler une méthode de redimensionnement basée sur le contenu dans un gestionnaire d’événements. Par exemple, utilisez l' <xref:System.Windows.Forms.DataGridView.DataBindingComplete> événement pour initialiser les tailles après la liaison, et <xref:System.Windows.Forms.DataGridView.CellValidated> gérez <xref:System.Windows.Forms.DataGridView.CellValueChanged> l’événement ou pour ajuster les tailles afin de compenser les modifications utilisateur ou les modifications apportées à une source de données liée.|  
|Ajustez les hauteurs de lignes pour le contenu des cellules multiligne.|Veillez à ce que les largeurs de colonne soient appropriées pour afficher des paragraphes de texte et utilisez le dimensionnement de ligne automatique ou par programme pour ajuster les hauteurs. Assurez-vous également que les cellules avec du contenu <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A> multiligne sont affichées à <xref:System.Windows.Forms.DataGridViewTriState.True>l’aide d’une valeur de style de cellule.<br /><br /> En général, vous allez utiliser un mode de redimensionnement de colonne automatique pour conserver les largeurs de colonne ou les définir sur des largeurs spécifiques avant que les hauteurs de lignes soient ajustées.|  
  
## <a name="resizing-with-the-mouse"></a>Redimensionnement avec la souris  
 Par défaut, les utilisateurs peuvent redimensionner des lignes, des colonnes et des en-têtes qui n’utilisent pas de mode de dimensionnement automatique en fonction des valeurs de cellule. Pour empêcher les utilisateurs de redimensionner avec d’autres modes, tels que le mode de remplissage de colonne, définissez <xref:System.Windows.Forms.DataGridView> une ou plusieurs des propriétés suivantes:  
  
- <xref:System.Windows.Forms.DataGridView.AllowUserToResizeColumns%2A>  
  
- <xref:System.Windows.Forms.DataGridView.AllowUserToResizeRows%2A>  
  
- <xref:System.Windows.Forms.DataGridView.ColumnHeadersHeightSizeMode%2A>  
  
- <xref:System.Windows.Forms.DataGridView.RowHeadersWidthSizeMode%2A>  
  
 Vous pouvez également empêcher les utilisateurs de redimensionner des lignes ou des colonnes <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A> individuelles en définissant leurs propriétés. Par défaut, la <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A> valeur de la propriété est basée <xref:System.Windows.Forms.DataGridView.AllowUserToResizeColumns%2A> sur la valeur de la propriété <xref:System.Windows.Forms.DataGridView.AllowUserToResizeRows%2A> pour les colonnes et sur la valeur de la propriété pour les lignes. Toutefois, si vous <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A> définissez <xref:System.Windows.Forms.DataGridViewTriState.True> explicitement <xref:System.Windows.Forms.DataGridViewTriState.False>sur ou, la valeur spécifiée remplace la valeur du contrôle pour cette ligne ou cette colonne. Affectez la valeur <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A> pourrestaurerl’héritage.<xref:System.Windows.Forms.DataGridViewTriState.NotSet>  
  
 Comme <xref:System.Windows.Forms.DataGridViewTriState.NotSet> restaure l’héritage de valeur, la <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A> propriété ne retourne jamais de <xref:System.Windows.Forms.DataGridViewTriState.NotSet> valeur, sauf si la ligne ou la colonne n’a pas <xref:System.Windows.Forms.DataGridView> été ajoutée à un contrôle. Si vous devez déterminer si la <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A> valeur de propriété d’une ligne ou d’une colonne est héritée, examinez sa <xref:System.Windows.Forms.DataGridViewElement.State%2A> propriété. Si la <xref:System.Windows.Forms.DataGridViewElement.State%2A> valeur comprend l' <xref:System.Windows.Forms.DataGridViewElementStates.ResizableSet> indicateur, la <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A> valeur de la propriété n’est pas héritée.  
  
## <a name="automatic-sizing"></a>Dimensionnement automatique  
 Il existe deux types de dimensionnement automatique dans <xref:System.Windows.Forms.DataGridView> le contrôle: le mode de remplissage de colonne et le dimensionnement automatique basé sur le contenu.  
  
 En mode de remplissage de colonne, les colonnes visibles dans le contrôle remplissent la largeur de la zone d’affichage du contrôle. Pour plus d’informations sur ce mode, consultez [mode de remplissage des colonnes dans le contrôle DataGridView Windows Forms](column-fill-mode-in-the-windows-forms-datagridview-control.md).  
  
 Vous pouvez également configurer des lignes, des colonnes et des en-têtes pour ajuster automatiquement leur taille en fonction du contenu de leurs cellules. Dans ce cas, l’ajustement de la taille se produit chaque fois que le contenu de la cellule change.  
  
> [!NOTE]
> Si vous conservez des valeurs de cellule dans un cache de données personnalisé à l’aide du mode virtuel, le dimensionnement automatique se produit lorsque l’utilisateur modifie une valeur de cellule, mais ne se <xref:System.Windows.Forms.DataGridView.CellValuePushed> produit pas lorsque vous modifiez une valeur mise en cache en dehors d’un gestionnaire d’événements. Dans ce cas, appelez la <xref:System.Windows.Forms.DataGridView.UpdateCellValue%2A> méthode pour forcer le contrôle à mettre à jour l’affichage de la cellule et à appliquer les modes de dimensionnement automatique actuels.  
  
 Si le dimensionnement automatique basé sur le contenu est activé pour une seule dimension, c’est-à-dire pour les lignes mais pas pour les colonnes, ou pour les colonnes <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A> mais pas pour les lignes, et est également activé, le réglage de la taille se produit également lorsque l’autre dimension change. Par exemple, si les lignes mais pas les colonnes sont configurées pour <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A> le dimensionnement automatique et sont activées, les utilisateurs peuvent faire glisser les séparateurs de colonne pour modifier la largeur d’une colonne et les hauteurs de lignes s’ajustent automatiquement afin que le contenu des cellules soit toujours affiché entièrement.  
  
 Si vous configurez les lignes et les colonnes pour le dimensionnement <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A> automatique basé sur le <xref:System.Windows.Forms.DataGridView> contenu et que est activé, le contrôle ajuste la taille chaque fois que le contenu de la cellule est modifié et utilise un rapport hauteur/largeur de cellule idéal pour calculer les nouvelles tailles.  
  
 Pour configurer le mode de dimensionnement pour les en-têtes et les lignes et pour les colonnes qui ne substituent pas la valeur du contrôle, <xref:System.Windows.Forms.DataGridView> définissez une ou plusieurs des propriétés suivantes:  
  
- <xref:System.Windows.Forms.DataGridView.ColumnHeadersHeightSizeMode%2A>  
  
- <xref:System.Windows.Forms.DataGridView.RowHeadersWidthSizeMode%2A>  
  
- <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A>  
  
- <xref:System.Windows.Forms.DataGridView.AutoSizeRowsMode%2A>  
  
 Pour remplacer le mode de redimensionnement de colonne du contrôle pour une colonne individuelle <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> , affectez à sa propriété <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.NotSet>une valeur autre que. Le mode de dimensionnement d’une colonne est effectivement déterminé <xref:System.Windows.Forms.DataGridViewColumn.InheritedAutoSizeMode%2A> par sa propriété. La valeur de cette propriété est basée sur la valeur de <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> la propriété de la colonne, <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.NotSet>sauf si cette valeur est, auquel <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A> cas la valeur du contrôle est héritée.  
  
 Utilisez le redimensionnement automatique basé sur le contenu avec précaution lorsque vous travaillez avec de grandes quantités de données. Pour éviter des pénalités en matière de performances, utilisez les modes de dimensionnement automatique qui calculent les tailles en fonction uniquement des lignes affichées au lieu d’analyser chaque ligne du contrôle. Pour des performances optimales, utilisez le redimensionnement par programme à la place afin de pouvoir le redimensionner à des moments spécifiques, par exemple immédiatement après le chargement de nouvelles données.  
  
 Les modes de dimensionnement automatique basés sur le contenu n’affectent pas les lignes, les colonnes ou les en-têtes que vous avez <xref:System.Windows.Forms.DataGridViewBand.Visible%2A> masqués en définissant la propriété `false`de ligne ou de colonne ou <xref:System.Windows.Forms.DataGridView.RowHeadersVisible%2A> le ou les <xref:System.Windows.Forms.DataGridView.ColumnHeadersVisible%2A> propriétés sur. Par exemple, si une colonne est masquée après avoir été automatiquement dimensionnée pour s’ajuster à une grande valeur de cellule, la colonne masquée ne modifie pas sa taille si la ligne contenant la valeur de cellule volumineuse est supprimée. Le dimensionnement automatique ne se produit pas lorsque la visibilité change. <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A> par conséquent, `true` la modification de la propriété de colonne en ne force pas le calcul de la taille en fonction de son contenu actuel.  
  
 Le redimensionnement basé sur le contenu par programme affecte les lignes, les colonnes et les en-têtes, quelle que soit leur visibilité.  
  
## <a name="programmatic-resizing"></a>Redimensionnement par programmation  
 Lorsque le dimensionnement automatique est désactivé, vous pouvez définir par programmation la largeur ou la hauteur exacte des lignes, des colonnes ou des en-têtes à l’aide des propriétés suivantes:  
  
- <xref:System.Windows.Forms.DataGridView.RowHeadersWidth%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.DataGridView.ColumnHeadersHeight%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.DataGridViewRow.Height%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.DataGridViewColumn.Width%2A?displayProperty=nameWithType>  
  
 Vous pouvez également redimensionner par programmation des lignes, des colonnes et des en-têtes pour les adapter à leur contenu à l’aide des méthodes suivantes:  
  
- <xref:System.Windows.Forms.DataGridView.AutoResizeColumn%2A>  
  
- <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A>  
  
- <xref:System.Windows.Forms.DataGridView.AutoResizeColumnHeadersHeight%2A>  
  
- <xref:System.Windows.Forms.DataGridView.AutoResizeRow%2A>  
  
- <xref:System.Windows.Forms.DataGridView.AutoResizeRows%2A>  
  
- <xref:System.Windows.Forms.DataGridView.AutoResizeRowHeadersWidth%2A>  
  
 Ces méthodes redimensionnent les lignes, les colonnes ou les en-têtes une seule fois, au lieu de les configurer pour un redimensionnement continu. Les nouvelles tailles sont calculées automatiquement pour afficher tout le contenu des cellules sans découpage. Lorsque vous redimensionnez des colonnes qui ont <xref:System.Windows.Forms.DataGridViewColumn.InheritedAutoSizeMode%2A> des valeurs de propriété de, toutefois, les largeurs calculées par le contenu sont utilisées pour ajuster proportionnellement les valeurs de propriété de <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.Fill>colonne <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> , et les largeurs de colonnes en fait ensuite calculé en fonction de ces nouvelles proportions afin que toutes les colonnes remplissent la zone d’affichage disponible du contrôle.  
  
 Le redimensionnement par programmation est utile pour éviter des pénalités en matière de performances avec redimensionnement continu. Il est également utile de fournir des tailles initiales pour les lignes, les colonnes et les en-têtes redimensionnables par l’utilisateur, ainsi que pour le mode de remplissage de colonne.  
  
 En général, vous appelez les méthodes de redimensionnement par programmation à des moments spécifiques. Par exemple, vous pouvez redimensionner par programmation toutes les colonnes immédiatement après le chargement des données, ou vous pouvez redimensionner par programmation une ligne spécifique après la modification d’une valeur de cellule particulière.  
  
## <a name="customizing-content-based-sizing-behavior"></a>Personnalisation du comportement de dimensionnement basé sur le contenu  
 Vous pouvez personnaliser les comportements de dimensionnement lorsque vous <xref:System.Windows.Forms.DataGridView> travaillez avec des types de cellules, de lignes et de <xref:System.Windows.Forms.DataGridViewCell.GetPreferredSize%2A?displayProperty=nameWithType>colonnes <xref:System.Windows.Forms.DataGridViewRow.GetPreferredHeight%2A?displayProperty=nameWithType>dérivés <xref:System.Windows.Forms.DataGridViewColumn.GetPreferredWidth%2A?displayProperty=nameWithType> en substituant les méthodes, ou en appelant des surcharges de <xref:System.Windows.Forms.DataGridView> méthode de redimensionnement protégées dans un dérivé régulation. Les surcharges de méthode de redimensionnement protégées sont conçues pour fonctionner par paires afin d’obtenir un rapport hauteur/largeur de cellule idéal, évitant les cellules trop larges ou de hauteur. Par exemple, si vous appelez la `AutoResizeRows(DataGridViewAutoSizeRowsMode,Boolean)` surcharge de la <xref:System.Windows.Forms.DataGridView.AutoResizeRows%2A> méthode et que vous `false` transmettez une valeur pour <xref:System.Boolean> le paramètre, la surcharge calcule la hauteur et la largeur idéales pour les cellules de la ligne, mais elle ajuste les hauteurs de lignes ne. Vous devez ensuite appeler la <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A> méthode pour ajuster les largeurs de colonne à l’idéal calculé.  
  
## <a name="content-based-sizing-options"></a>Options de dimensionnement basées sur le contenu  
 Les énumérations utilisées par les propriétés et les méthodes de dimensionnement ont des valeurs similaires pour le dimensionnement basé sur le contenu. Avec ces valeurs, vous pouvez limiter les cellules qui sont utilisées pour calculer les tailles préférées. Pour toutes les énumérations de dimensionnement, les valeurs dont les noms font référence aux cellules affichées limitent leurs calculs aux cellules des lignes affichées. L’exclusion de lignes est utile pour éviter une altération des performances lorsque vous travaillez avec une grande quantité de lignes. Vous pouvez également limiter les calculs aux valeurs de cellule dans les cellules d’en-tête ou autres.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.AllowUserToResizeColumns%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AllowUserToResizeRows%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.ColumnHeadersHeightSizeMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.RowHeadersWidthSizeMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AutoSizeRowsMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.InheritedAutoSizeMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.RowHeadersWidth%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.ColumnHeadersHeight%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewRow.Height%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.Width%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AutoResizeColumn%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AutoResizeColumnHeadersHeight%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AutoResizeRow%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AutoResizeRows%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AutoResizeRowHeadersWidth%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewAutoSizeRowMode>
- <xref:System.Windows.Forms.DataGridViewAutoSizeRowsMode>
- <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode>
- <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode>
- <xref:System.Windows.Forms.DataGridViewColumnHeadersHeightSizeMode>
- <xref:System.Windows.Forms.DataGridViewRowHeadersWidthSizeMode>
- [Redimensionnement des colonnes et des lignes dans le contrôle DataGridView Windows Forms](resizing-columns-and-rows-in-the-windows-forms-datagridview-control.md)
- [Mode Remplissage des colonnes dans le contrôle DataGridView Windows Forms](column-fill-mode-in-the-windows-forms-datagridview-control.md)
- [Guide pratique : Définir les modes de redimensionnement du contrôle DataGridView Windows Forms](how-to-set-the-sizing-modes-of-the-windows-forms-datagridview-control.md)
