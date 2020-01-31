---
title: Options de dimensionnement dans le contrôle DataGridView
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], row sizing
- data grids [Windows Forms], column sizing
- DataGridView control [Windows Forms], column sizing
- DataGridView control [Windows Forms], sizing options
- data grids [Windows Forms], row sizing
- data grids [Windows Forms], sizing options
ms.assetid: a5620a9c-0d06-41e3-8934-c25ddb16c9e6
ms.openlocfilehash: bf1be699a18608bb452bd9fb98cbca1e99f7a9e4
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742982"
---
# <a name="sizing-options-in-the-windows-forms-datagridview-control"></a>Options de dimensionnement dans le contrôle DataGridView Windows Forms
<xref:System.Windows.Forms.DataGridView> lignes, colonnes et en-têtes peuvent changer de taille à la suite de nombreuses occurrences différentes. Le tableau suivant présente ces occurrences.  
  
|Occurrence|Description|  
|----------------|-----------------|  
|Redimensionnement de l’utilisateur|Les utilisateurs peuvent effectuer des ajustements de taille en faisant glisser ou en double-cliquant sur des séparateurs de ligne, de colonne ou d’en-tête.|  
|Redimensionnement du contrôle|En mode de remplissage de colonne, les largeurs de colonne changent lorsque la largeur du contrôle change ; par exemple, lorsque le contrôle est ancré à son formulaire parent et que l’utilisateur redimensionne le formulaire.|  
|Modification de la valeur de la cellule|En mode de dimensionnement automatique basé sur le contenu, les tailles changent en fonction des nouvelles valeurs d’affichage.|  
|Appel de méthode|Le redimensionnement basé sur le contenu par programme vous permet d’effectuer des ajustements de taille opportunistes en fonction des valeurs de cellule au moment de l’appel de la méthode.|  
|Paramètre de propriété|Vous pouvez également définir des valeurs de hauteur et de largeur spécifiques.|  
  
 Par défaut, le redimensionnement de l’utilisateur est activé, le dimensionnement automatique est désactivé et les valeurs de cellule qui sont plus larges que leurs colonnes sont découpées.  
  
 Le tableau suivant répertorie les scénarios que vous pouvez utiliser pour ajuster le comportement par défaut ou pour utiliser des options de dimensionnement spécifiques afin d’obtenir des effets particuliers.  
  
|Scénario|Implémentation|  
|--------------|--------------------|  
|Utilisez le mode de remplissage de colonne pour afficher des données de taille similaire dans un nombre relativement faible de colonnes qui occupent toute la largeur du contrôle sans afficher la barre de défilement horizontale.|Affectez à la propriété <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A> la valeur <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode.Fill>.|  
|Utilisez le mode de remplissage de colonne avec des valeurs d’affichage de tailles différentes.|Affectez à la propriété <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A> la valeur <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode.Fill>. Initialisez les largeurs de colonne relatives en définissant les propriétés de <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> de colonne ou en appelant la méthode de <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A> de contrôle après avoir rempli le contrôle avec des données.|  
|Utilisez le mode de remplissage de colonne avec des valeurs d’importance variable.|Affectez à la propriété <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A> la valeur <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode.Fill>. Définissez de grandes valeurs de <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> pour les colonnes qui doivent toujours afficher certaines de leurs données ou utilisez une option de dimensionnement autre que le mode de remplissage pour des colonnes spécifiques.|  
|Utilisez le mode de remplissage de colonne pour éviter d’afficher l’arrière-plan du contrôle.|Affectez à la propriété <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> de la dernière colonne la valeur <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.Fill> et utilisez d’autres options de dimensionnement pour les autres colonnes. Si les autres colonnes utilisent une trop grande partie de l’espace disponible, définissez la propriété <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> de la dernière colonne.|  
|Affichez une colonne de largeur fixe, telle qu’une colonne d’icône ou d’ID.|Définissez <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> sur <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.None> et <xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A> pour <xref:System.Windows.Forms.DataGridViewTriState.False> pour la colonne. Initialisez sa largeur en définissant la propriété <xref:System.Windows.Forms.DataGridViewColumn.Width%2A> ou en appelant la méthode <xref:System.Windows.Forms.DataGridView.AutoResizeColumn%2A> de contrôle après avoir rempli le contrôle avec des données.|  
|Ajustez les tailles automatiquement chaque fois que le contenu des cellules change pour éviter le découpage et pour optimiser l’utilisation de l’espace.|Affectez à une propriété de dimensionnement automatique une valeur qui représente un mode de dimensionnement basé sur le contenu. Pour éviter une altération des performances lorsque vous travaillez avec de grandes quantités de données, utilisez un mode de dimensionnement qui calcule uniquement les lignes affichées.|  
|Ajustez les tailles pour ajuster les valeurs aux lignes affichées afin d’éviter des pénalités en matière de performances lorsque vous travaillez avec de nombreuses lignes.|Utilisez les valeurs d’énumération du mode de redimensionnement appropriées avec un redimensionnement automatique ou par programme. Pour ajuster les tailles en fonction des valeurs des lignes récemment affichées lors du défilement, appelez une méthode de redimensionnement dans un gestionnaire d’événements <xref:System.Windows.Forms.DataGridView.Scroll>. Pour personnaliser le redimensionnement du double-clic de l’utilisateur afin que seules les valeurs des lignes affichées déterminent les nouvelles tailles, appelez une méthode de redimensionnement dans un <xref:System.Windows.Forms.DataGridView.RowDividerDoubleClick> ou <xref:System.Windows.Forms.DataGridView.ColumnDividerDoubleClick> gestionnaire d’événements.|  
|Ajustez les tailles en fonction du contenu des cellules uniquement à des moments précis pour éviter des pénalités en matière de performances ou pour permettre le redimensionnement de l’utilisateur.|Appeler une méthode de redimensionnement basée sur le contenu dans un gestionnaire d’événements. Par exemple, utilisez l’événement <xref:System.Windows.Forms.DataGridView.DataBindingComplete> pour initialiser les tailles après la liaison et gérer l’événement <xref:System.Windows.Forms.DataGridView.CellValidated> ou <xref:System.Windows.Forms.DataGridView.CellValueChanged> pour ajuster les tailles afin de compenser les modifications ou modifications apportées par l’utilisateur dans une source de données liée.|  
|Ajustez les hauteurs de lignes pour le contenu des cellules multiligne.|Veillez à ce que les largeurs de colonne soient appropriées pour afficher des paragraphes de texte et utilisez le dimensionnement de ligne automatique ou par programme pour ajuster les hauteurs. Assurez-vous également que les cellules avec du contenu multiligne sont affichées à l’aide d’une <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A> valeur de style de cellule de <xref:System.Windows.Forms.DataGridViewTriState.True>.<br /><br /> En général, vous allez utiliser un mode de redimensionnement de colonne automatique pour conserver les largeurs de colonne ou les définir sur des largeurs spécifiques avant que les hauteurs de lignes soient ajustées.|  
  
## <a name="resizing-with-the-mouse"></a>Redimensionnement avec la souris  
 Par défaut, les utilisateurs peuvent redimensionner des lignes, des colonnes et des en-têtes qui n’utilisent pas de mode de dimensionnement automatique en fonction des valeurs de cellule. Pour empêcher les utilisateurs de redimensionner avec d’autres modes, tels que le mode de remplissage de colonne, définissez une ou plusieurs des propriétés de <xref:System.Windows.Forms.DataGridView> suivantes :  
  
- <xref:System.Windows.Forms.DataGridView.AllowUserToResizeColumns%2A>  
  
- <xref:System.Windows.Forms.DataGridView.AllowUserToResizeRows%2A>  
  
- <xref:System.Windows.Forms.DataGridView.ColumnHeadersHeightSizeMode%2A>  
  
- <xref:System.Windows.Forms.DataGridView.RowHeadersWidthSizeMode%2A>  
  
 Vous pouvez également empêcher les utilisateurs de redimensionner des lignes ou des colonnes individuelles en définissant leurs propriétés <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A>. Par défaut, la valeur de la propriété <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A> est basée sur la valeur de la propriété <xref:System.Windows.Forms.DataGridView.AllowUserToResizeColumns%2A> pour les colonnes et sur la valeur de la propriété <xref:System.Windows.Forms.DataGridView.AllowUserToResizeRows%2A> pour les lignes. Toutefois, si vous définissez explicitement <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A> sur <xref:System.Windows.Forms.DataGridViewTriState.True> ou <xref:System.Windows.Forms.DataGridViewTriState.False>, la valeur spécifiée remplace la valeur du contrôle pour cette ligne ou cette colonne. Définissez <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A> sur <xref:System.Windows.Forms.DataGridViewTriState.NotSet> pour restaurer l’héritage.  
  
 Étant donné que <xref:System.Windows.Forms.DataGridViewTriState.NotSet> restaure l’héritage de valeur, la propriété <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A> ne retourne jamais de valeur <xref:System.Windows.Forms.DataGridViewTriState.NotSet>, sauf si la ligne ou la colonne n’a pas été ajoutée à un contrôle <xref:System.Windows.Forms.DataGridView>. Si vous devez déterminer si la valeur de la propriété <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A> d’une ligne ou d’une colonne est héritée, examinez sa propriété <xref:System.Windows.Forms.DataGridViewElement.State%2A>. Si la valeur <xref:System.Windows.Forms.DataGridViewElement.State%2A> comprend l’indicateur <xref:System.Windows.Forms.DataGridViewElementStates.ResizableSet>, la valeur de la propriété <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A> n’est pas héritée.  
  
## <a name="automatic-sizing"></a>Dimensionnement automatique  
 Il existe deux types de dimensionnement automatique dans le contrôle de <xref:System.Windows.Forms.DataGridView> : le mode de remplissage de colonne et le dimensionnement automatique basé sur le contenu.  
  
 En mode de remplissage de colonne, les colonnes visibles dans le contrôle remplissent la largeur de la zone d’affichage du contrôle. Pour plus d’informations sur ce mode, consultez [mode de remplissage des colonnes dans le contrôle DataGridView Windows Forms](column-fill-mode-in-the-windows-forms-datagridview-control.md).  
  
 Vous pouvez également configurer des lignes, des colonnes et des en-têtes pour ajuster automatiquement leur taille en fonction du contenu de leurs cellules. Dans ce cas, l’ajustement de la taille se produit chaque fois que le contenu de la cellule change.  
  
> [!NOTE]
> Si vous conservez des valeurs de cellule dans un cache de données personnalisé à l’aide du mode virtuel, le dimensionnement automatique se produit lorsque l’utilisateur modifie une valeur de cellule, mais ne se produit pas lorsque vous modifiez une valeur mise en cache en dehors d’un gestionnaire d’événements <xref:System.Windows.Forms.DataGridView.CellValuePushed>. Dans ce cas, appelez la méthode <xref:System.Windows.Forms.DataGridView.UpdateCellValue%2A> pour forcer le contrôle à mettre à jour l’affichage de la cellule et à appliquer les modes de dimensionnement automatique actuels.  
  
 Si le dimensionnement automatique basé sur le contenu est activé pour une seule dimension, c’est-à-dire pour les lignes mais pas pour les colonnes, ou pour les colonnes mais pas pour les lignes, et si <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A> est également activé, le réglage de la taille se produit également lorsque l’autre dimension change. Par exemple, si les lignes mais pas les colonnes sont configurées pour le dimensionnement automatique et que <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A> est activé, les utilisateurs peuvent faire glisser les séparateurs de colonne pour modifier la largeur d’une colonne et les hauteurs de lignes s’ajustent automatiquement afin que le contenu des cellules soit toujours entièrement affiché.  
  
 Si vous configurez les lignes et les colonnes pour le dimensionnement automatique basé sur le contenu et que <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A> est activé, le contrôle <xref:System.Windows.Forms.DataGridView> ajuste les tailles chaque fois que le contenu des cellules change et utilise un rapport hauteur/largeur de cellule idéal pour le calcul de nouvelles tailles.  
  
 Pour configurer le mode de dimensionnement pour les en-têtes et les lignes et pour les colonnes qui ne substituent pas la valeur du contrôle, définissez une ou plusieurs des propriétés de <xref:System.Windows.Forms.DataGridView> suivantes :  
  
- <xref:System.Windows.Forms.DataGridView.ColumnHeadersHeightSizeMode%2A>  
  
- <xref:System.Windows.Forms.DataGridView.RowHeadersWidthSizeMode%2A>  
  
- <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A>  
  
- <xref:System.Windows.Forms.DataGridView.AutoSizeRowsMode%2A>  
  
 Pour remplacer le mode de dimensionnement de colonne du contrôle pour une colonne individuelle, définissez sa propriété <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> sur une valeur autre que <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.NotSet>. Le mode de dimensionnement d’une colonne est effectivement déterminé par sa propriété <xref:System.Windows.Forms.DataGridViewColumn.InheritedAutoSizeMode%2A>. La valeur de cette propriété est basée sur la valeur de la propriété <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> de la colonne, sauf si cette valeur est <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.NotSet>, auquel cas la valeur <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A> du contrôle est héritée.  
  
 Utilisez le redimensionnement automatique basé sur le contenu avec précaution lorsque vous travaillez avec de grandes quantités de données. Pour éviter des pénalités en matière de performances, utilisez les modes de dimensionnement automatique qui calculent les tailles en fonction uniquement des lignes affichées au lieu d’analyser chaque ligne du contrôle. Pour des performances optimales, utilisez le redimensionnement par programme à la place afin de pouvoir le redimensionner à des moments spécifiques, par exemple immédiatement après le chargement de nouvelles données.  
  
 Les modes de redimensionnement automatique basés sur le contenu n’affectent pas les lignes, les colonnes ou les en-têtes que vous avez masqués en définissant la propriété ligne ou colonne <xref:System.Windows.Forms.DataGridViewBand.Visible%2A> ou les propriétés <xref:System.Windows.Forms.DataGridView.RowHeadersVisible%2A> ou <xref:System.Windows.Forms.DataGridView.ColumnHeadersVisible%2A> de contrôle sur `false`. Par exemple, si une colonne est masquée après avoir été automatiquement dimensionnée pour s’ajuster à une grande valeur de cellule, la colonne masquée ne modifie pas sa taille si la ligne contenant la valeur de cellule volumineuse est supprimée. Le dimensionnement automatique ne se produit pas lorsque la visibilité change. par conséquent, la modification de la colonne <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A> propriété sur `true` ne force pas ce dernier à recalculer sa taille en fonction de son contenu actuel.  
  
 Le redimensionnement basé sur le contenu par programme affecte les lignes, les colonnes et les en-têtes, quelle que soit leur visibilité.  
  
## <a name="programmatic-resizing"></a>Redimensionnement par programmation  
 Lorsque le dimensionnement automatique est désactivé, vous pouvez définir par programmation la largeur ou la hauteur exacte des lignes, des colonnes ou des en-têtes à l’aide des propriétés suivantes :  
  
- <xref:System.Windows.Forms.DataGridView.RowHeadersWidth%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.DataGridView.ColumnHeadersHeight%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.DataGridViewRow.Height%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.DataGridViewColumn.Width%2A?displayProperty=nameWithType>  
  
 Vous pouvez également redimensionner par programmation des lignes, des colonnes et des en-têtes pour les adapter à leur contenu à l’aide des méthodes suivantes :  
  
- <xref:System.Windows.Forms.DataGridView.AutoResizeColumn%2A>  
  
- <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A>  
  
- <xref:System.Windows.Forms.DataGridView.AutoResizeColumnHeadersHeight%2A>  
  
- <xref:System.Windows.Forms.DataGridView.AutoResizeRow%2A>  
  
- <xref:System.Windows.Forms.DataGridView.AutoResizeRows%2A>  
  
- <xref:System.Windows.Forms.DataGridView.AutoResizeRowHeadersWidth%2A>  
  
 Ces méthodes redimensionnent les lignes, les colonnes ou les en-têtes une seule fois, au lieu de les configurer pour un redimensionnement continu. Les nouvelles tailles sont calculées automatiquement pour afficher tout le contenu des cellules sans découpage. Toutefois, lorsque vous redimensionnez des colonnes qui ont <xref:System.Windows.Forms.DataGridViewColumn.InheritedAutoSizeMode%2A> valeurs de propriété de <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.Fill>, toutefois, les largeurs calculées à base de contenu sont utilisées pour ajuster proportionnellement la colonne <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> valeurs de propriété, et les largeurs de colonne sont ensuite calculées en fonction de ces nouvelles proportions afin que toutes les colonnes remplissent la zone d’affichage disponible du contrôle.  
  
 Le redimensionnement par programmation est utile pour éviter des pénalités en matière de performances avec redimensionnement continu. Il est également utile de fournir des tailles initiales pour les lignes, les colonnes et les en-têtes redimensionnables par l’utilisateur, ainsi que pour le mode de remplissage de colonne.  
  
 En général, vous appelez les méthodes de redimensionnement par programmation à des moments spécifiques. Par exemple, vous pouvez redimensionner par programmation toutes les colonnes immédiatement après le chargement des données, ou vous pouvez redimensionner par programmation une ligne spécifique après la modification d’une valeur de cellule particulière.  
  
## <a name="customizing-content-based-sizing-behavior"></a>Personnalisation du comportement de dimensionnement basé sur le contenu  
 Vous pouvez personnaliser les comportements de dimensionnement lorsque vous travaillez avec des types dérivés <xref:System.Windows.Forms.DataGridView> de cellules, de lignes et de colonnes en substituant les méthodes <xref:System.Windows.Forms.DataGridViewCell.GetPreferredSize%2A?displayProperty=nameWithType>, <xref:System.Windows.Forms.DataGridViewRow.GetPreferredHeight%2A?displayProperty=nameWithType>ou <xref:System.Windows.Forms.DataGridViewColumn.GetPreferredWidth%2A?displayProperty=nameWithType> ou en appelant des surcharges de méthode de redimensionnement protégées dans un contrôle <xref:System.Windows.Forms.DataGridView> dérivé. Les surcharges de méthode de redimensionnement protégées sont conçues pour fonctionner par paires afin d’obtenir un rapport hauteur/largeur de cellule idéal, évitant les cellules trop larges ou de hauteur. Par exemple, si vous appelez la surcharge `AutoResizeRows(DataGridViewAutoSizeRowsMode,Boolean)` de la méthode <xref:System.Windows.Forms.DataGridView.AutoResizeRows%2A> et que vous transmettez une valeur de `false` pour le paramètre <xref:System.Boolean>, la surcharge calcule les hauteurs et les largeurs idéals pour les cellules de la ligne, mais elle ajuste uniquement les hauteurs de lignes. Vous devez ensuite appeler la méthode <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A> pour ajuster les largeurs de colonne à l’idéal calculé.  
  
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
- [Guide pratique pour définir les modes de redimensionnement du contrôle DataGridView Windows Forms](how-to-set-the-sizing-modes-of-the-windows-forms-datagridview-control.md)
