---
title: Meilleures pratiques pour la mise à l’échelle du contrôle DataGridView
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], row sharing
- data grids [Windows Forms], best practices
- DataGridView control [Windows Forms], shared rows
- DataGridView control [Windows Forms], best practices
- best practices [Windows Forms], dataGridView control
- DataGridView control [Windows Forms], scaling
ms.assetid: 8321a8a6-6340-4fd1-b475-fa090b905aaf
ms.openlocfilehash: 63500a79def89510b4bc7a436abc4620a7265a79
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744124"
---
# <a name="best-practices-for-scaling-the-windows-forms-datagridview-control"></a>Meilleures pratiques pour la mise à l'échelle du contrôle DataGridView Windows Forms

Le contrôle <xref:System.Windows.Forms.DataGridView> est conçu pour offrir une évolutivité maximale. Si vous avez besoin d’afficher de grandes quantités de données, vous devez suivre les instructions décrites dans cette rubrique pour éviter de consommer de grandes quantités de mémoire ou de dégrader la réactivité de l’interface utilisateur. Cette rubrique présente les problèmes suivants :

- Utilisation efficace des styles de cellule

- Utilisation efficace des menus contextuels

- Utilisation efficace du redimensionnement automatique

- Utilisation efficace des collections de cellules, de lignes et de colonnes sélectionnées

- Utilisation de lignes partagées

- Empêcher le partage de lignes

Si vous avez des besoins spécifiques en matière de performances, vous pouvez implémenter le mode virtuel et fournir vos propres opérations de gestion de données. Pour plus d’informations, consultez [modes d’affichage des données dans le contrôle DataGridView Windows Forms](data-display-modes-in-the-windows-forms-datagridview-control.md).

## <a name="using-cell-styles-efficiently"></a>Utilisation efficace des styles de cellule

Chaque cellule, ligne et colonne peut avoir ses propres informations de style. Les informations de style sont stockées dans des objets <xref:System.Windows.Forms.DataGridViewCellStyle>. La création d’objets de style de cellule pour de nombreux éléments de <xref:System.Windows.Forms.DataGridView> individuels peut être inefficace, en particulier lors de l’utilisation de grandes quantités de données. Pour éviter un impact sur les performances, suivez les instructions ci-dessous :

- Évitez de définir des propriétés de style de cellule pour des objets <xref:System.Windows.Forms.DataGridViewCell> ou <xref:System.Windows.Forms.DataGridViewRow>. Cela comprend l’objet Row spécifié par la propriété <xref:System.Windows.Forms.DataGridView.RowTemplate%2A>. Chaque nouvelle ligne clonée à partir du modèle de ligne reçoit sa propre copie de l’objet de style de cellule du modèle. Pour une extensibilité maximale, définissez les propriétés de style de cellule au niveau de la <xref:System.Windows.Forms.DataGridView>. Par exemple, définissez la propriété <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> plutôt que la propriété <xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=nameWithType>.

- Si certaines cellules nécessitent une mise en forme autre que la mise en forme par défaut, utilisez la même instance de <xref:System.Windows.Forms.DataGridViewCellStyle> entre des groupes de cellules, de lignes ou de colonnes. Évitez de définir directement les propriétés de type <xref:System.Windows.Forms.DataGridViewCellStyle> sur des cellules, des lignes et des colonnes spécifiques. Pour obtenir un exemple de partage de style de cellule, consultez [Comment : définir des styles de cellules par défaut pour le contrôle DataGridView Windows Forms](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md). Vous pouvez également éviter une altération des performances lors de la définition individuelle des styles de cellule en gérant le gestionnaire d’événements <xref:System.Windows.Forms.DataGridView.CellFormatting>. Pour obtenir un exemple, consultez [Comment : personnaliser la mise en forme des données dans le contrôle DataGridView Windows Forms](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).

- Lorsque vous déterminez le style d’une cellule, utilisez la propriété <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A?displayProperty=nameWithType> plutôt que la propriété <xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=nameWithType>. L’accès à la propriété <xref:System.Windows.Forms.DataGridViewCell.Style%2A> crée une nouvelle instance de la classe <xref:System.Windows.Forms.DataGridViewCellStyle> si la propriété n’a pas déjà été utilisée. En outre, cet objet peut ne pas contenir les informations de style complètes pour la cellule si certains styles sont hérités de la ligne, de la colonne ou du contrôle. Pour plus d’informations sur l’héritage de style de cellule, consultez [styles de cellule dans le contrôle DataGridView Windows Forms](cell-styles-in-the-windows-forms-datagridview-control.md).

## <a name="using-shortcut-menus-efficiently"></a>Utilisation efficace des menus contextuels

Chaque cellule, ligne et colonne peut avoir son propre menu contextuel. Les menus contextuels du contrôle <xref:System.Windows.Forms.DataGridView> sont représentés par des contrôles <xref:System.Windows.Forms.ContextMenuStrip>. Tout comme avec les objets de style de cellule, la création de menus contextuels pour de nombreux éléments de <xref:System.Windows.Forms.DataGridView> individuel aura un impact négatif sur les performances. Pour éviter cette pénalité, suivez les instructions ci-dessous :

- Évitez de créer des menus contextuels pour des cellules et des lignes individuelles. Cela comprend le modèle de ligne, qui est cloné avec son menu contextuel lorsque de nouvelles lignes sont ajoutées au contrôle. Pour une extensibilité maximale, utilisez uniquement la propriété <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> du contrôle pour spécifier un menu contextuel unique pour l’ensemble du contrôle.

- Si vous avez besoin de plusieurs menus contextuels pour plusieurs lignes ou cellules, gérez les événements <xref:System.Windows.Forms.DataGridView.CellContextMenuStripNeeded> ou <xref:System.Windows.Forms.DataGridView.RowContextMenuStripNeeded>. Ces événements vous permettent de gérer les objets de menu contextuel vous-même, ce qui vous permet de régler les performances.

## <a name="using-automatic-resizing-efficiently"></a>Utilisation efficace du redimensionnement automatique

Les lignes, les colonnes et les en-têtes peuvent être redimensionnés automatiquement à mesure que le contenu des cellules change afin que le contenu entier des cellules soit affiché sans découpage. La modification des modes de dimensionnement peut également redimensionner des lignes, des colonnes et des en-têtes. Pour déterminer la taille correcte, le contrôle de <xref:System.Windows.Forms.DataGridView> doit examiner la valeur de chaque cellule qu’il doit prendre en charge. Lors de l’utilisation de jeux de données volumineux, cette analyse peut avoir un impact négatif sur les performances du contrôle lorsque le redimensionnement automatique se produit. Pour éviter des pénalités en matière de performances, suivez les instructions ci-dessous :

- Évitez d’utiliser le dimensionnement automatique sur un contrôle de <xref:System.Windows.Forms.DataGridView> avec un grand ensemble de lignes. Si vous utilisez le dimensionnement automatique, redimensionnez uniquement en fonction des lignes affichées. Utilisez également uniquement les lignes affichées en mode virtuel.

  - Pour les lignes et les colonnes, utilisez le champ `DisplayedCells` ou `DisplayedCellsExceptHeaders` des énumérations <xref:System.Windows.Forms.DataGridViewAutoSizeRowsMode>, <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode>et <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode>.

  - Pour les en-têtes de lignes, utilisez le champ <xref:System.Windows.Forms.DataGridViewRowHeadersWidthSizeMode.AutoSizeToDisplayedHeaders> ou <xref:System.Windows.Forms.DataGridViewRowHeadersWidthSizeMode.AutoSizeToFirstHeader> de l’énumération <xref:System.Windows.Forms.DataGridViewRowHeadersWidthSizeMode>.

- Pour une extensibilité maximale, désactivez le dimensionnement automatique et utilisez le redimensionnement par programmation.

Pour plus d’informations, consultez [options de dimensionnement dans le contrôle DataGridView Windows Forms](sizing-options-in-the-windows-forms-datagridview-control.md).

## <a name="using-the-selected-cells-rows-and-columns-collections-efficiently"></a>Utilisation efficace des collections de cellules, de lignes et de colonnes sélectionnées

La collection <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> ne fonctionne pas efficacement avec de grandes sélections. Les collections <xref:System.Windows.Forms.DataGridView.SelectedRows%2A> et <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> peuvent également être inefficaces, bien qu’à un degré moindre, car il y a beaucoup moins de lignes que de cellules dans un contrôle <xref:System.Windows.Forms.DataGridView> classique, et beaucoup moins de colonnes que de lignes. Pour éviter des pénalités en matière de performances lors de l’utilisation de ces regroupements, suivez les instructions suivantes :

- Pour déterminer si toutes les cellules de la <xref:System.Windows.Forms.DataGridView> ont été sélectionnées avant d’accéder au contenu de la collection de <xref:System.Windows.Forms.DataGridView.SelectedCells%2A>, vérifiez la valeur de retour de la méthode <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A>. Notez, toutefois, que cette méthode peut provoquer le non-partage de lignes. Pour plus d'informations, consultez la section suivante.

- Évitez d’utiliser la propriété <xref:System.Collections.ICollection.Count%2A> du <xref:System.Windows.Forms.DataGridViewSelectedCellCollection?displayProperty=nameWithType> pour déterminer le nombre de cellules sélectionnées. Au lieu de cela, utilisez la méthode <xref:System.Windows.Forms.DataGridView.GetCellCount%2A?displayProperty=nameWithType> et transmettez la valeur <xref:System.Windows.Forms.DataGridViewElementStates.Selected?displayProperty=nameWithType>. De même, utilisez les méthodes <xref:System.Windows.Forms.DataGridViewRowCollection.GetRowCount%2A?displayProperty=nameWithType> et <xref:System.Windows.Forms.DataGridViewColumnCollection.GetColumnCount%2A?displayProperty=nameWithType> pour déterminer le nombre d’éléments sélectionnés, plutôt que d’accéder aux collections de lignes et de colonnes sélectionnées.

- Évitez les modes de sélection basés sur des cellules. Au lieu de cela, affectez à la propriété <xref:System.Windows.Forms.DataGridView.SelectionMode%2A?displayProperty=nameWithType> la valeur <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect?displayProperty=nameWithType> ou <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect?displayProperty=nameWithType>.

## <a name="using-shared-rows"></a>Utilisation de lignes partagées

Une utilisation efficace de la mémoire est obtenue dans le contrôle <xref:System.Windows.Forms.DataGridView> par le biais de lignes partagées. Les lignes partageront la plus grande quantité d’informations sur leur apparence et leur comportement possible en partageant des instances de la classe <xref:System.Windows.Forms.DataGridViewRow>.

Tandis que le partage d’instances de ligne permet d’économiser de la mémoire, les lignes peuvent facilement devenir non partagées. Par exemple, chaque fois qu’un utilisateur interagit directement avec une cellule, sa ligne devient non partagée. Étant donné que cela ne peut pas être évité, les instructions de cette rubrique sont utiles uniquement lorsque vous travaillez avec de très grandes quantités de données et uniquement lorsque les utilisateurs interagissent avec une partie relativement réduite des données chaque fois que votre programme est exécuté.

Une ligne ne peut pas être partagée dans un contrôle de <xref:System.Windows.Forms.DataGridView> indépendant si l’une de ses cellules contient des valeurs. Lorsque le contrôle de <xref:System.Windows.Forms.DataGridView> est lié à une source de données externe ou lorsque vous implémentez le mode virtuel et fournissez votre propre source de données, les valeurs des cellules sont stockées en dehors du contrôle plutôt que dans des objets de cellule, ce qui permet de partager les lignes.

Un objet Row peut être partagé uniquement si l’état de toutes ses cellules peut être déterminé à partir de l’état de la ligne et des États des colonnes contenant les cellules. Si vous modifiez l’état d’une cellule afin qu’elle ne puisse plus être déduite de l’état de sa ligne et de sa colonne, la ligne ne peut pas être partagée.

Par exemple, une ligne ne peut pas être partagée dans l’une des situations suivantes :

- La ligne contient une seule cellule sélectionnée qui ne se trouve pas dans une colonne sélectionnée.

- La ligne contient une cellule dont les propriétés <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A> ou <xref:System.Windows.Forms.DataGridViewCell.ContextMenuStrip%2A> sont définies.

- La ligne contient un <xref:System.Windows.Forms.DataGridViewComboBoxCell> dont la propriété <xref:System.Windows.Forms.DataGridViewComboBoxCell.Items%2A> est définie.

En mode dépendant ou en mode virtuel, vous pouvez fournir des info-bulles et des menus contextuels pour des cellules individuelles en gérant les événements <xref:System.Windows.Forms.DataGridView.CellToolTipTextNeeded> et <xref:System.Windows.Forms.DataGridView.CellContextMenuStripNeeded>.

Le contrôle <xref:System.Windows.Forms.DataGridView> tente automatiquement d’utiliser des lignes partagées à chaque fois que des lignes sont ajoutées à la <xref:System.Windows.Forms.DataGridViewRowCollection>. Suivez les indications ci-dessous pour vous assurer que les lignes sont partagées :

- Évitez d’appeler la surcharge `Add(Object[])` de la méthode <xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A> et la surcharge `Insert(Object[])` de la méthode <xref:System.Windows.Forms.DataGridViewRowCollection.Insert%2A> de la collection <xref:System.Windows.Forms.DataGridView.Rows%2A?displayProperty=nameWithType>. Ces surcharges créent automatiquement des lignes non partagées.

- Assurez-vous que la ligne spécifiée dans la propriété <xref:System.Windows.Forms.DataGridView.RowTemplate%2A?displayProperty=nameWithType> peut être partagée dans les cas suivants :

  - Lors de l’appel de la `Add()` ou `Add(Int32)` des surcharges de la méthode <xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A> ou de la surcharge `Insert(Int32,Int32)` de la méthode <xref:System.Windows.Forms.DataGridViewRowCollection.Insert%2A> de la collection <xref:System.Windows.Forms.DataGridView.Rows%2A?displayProperty=nameWithType>.

  - Lors de l’incrémentation de la valeur de la propriété <xref:System.Windows.Forms.DataGridView.RowCount%2A?displayProperty=nameWithType>.

  - Lors de la définition de la propriété <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType>.

- Assurez-vous que la ligne indiquée par le paramètre `indexSource` peut être partagée lors de l’appel des méthodes <xref:System.Windows.Forms.DataGridViewRowCollection.AddCopy%2A>, <xref:System.Windows.Forms.DataGridViewRowCollection.AddCopies%2A>, <xref:System.Windows.Forms.DataGridViewRowCollection.InsertCopy%2A>et <xref:System.Windows.Forms.DataGridViewRowCollection.InsertCopies%2A> de la collection <xref:System.Windows.Forms.DataGridView.Rows%2A?displayProperty=nameWithType>.

- Assurez-vous que la ou les lignes spécifiées peuvent être partagées lors de l’appel de la surcharge `Add(DataGridViewRow)` de la méthode <xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A>, de la méthode <xref:System.Windows.Forms.DataGridViewRowCollection.AddRange%2A>, de la surcharge `Insert(Int32,DataGridViewRow)` de la méthode <xref:System.Windows.Forms.DataGridViewRowCollection.Insert%2A> et de la méthode <xref:System.Windows.Forms.DataGridViewRowCollection.InsertRange%2A> de la collection <xref:System.Windows.Forms.DataGridView.Rows%2A?displayProperty=nameWithType>.

Pour déterminer si une ligne est partagée, utilisez la méthode <xref:System.Windows.Forms.DataGridViewRowCollection.SharedRow%2A?displayProperty=nameWithType> pour récupérer l’objet Row, puis vérifiez la propriété <xref:System.Windows.Forms.DataGridViewBand.Index%2A> de l’objet. Les lignes partagées ont toujours une valeur de propriété <xref:System.Windows.Forms.DataGridViewBand.Index%2A> de – 1.

## <a name="preventing-rows-from-becoming-unshared"></a>Empêcher le partage de lignes

Les lignes partagées peuvent devenir non partagées suite à une action de l’utilisateur ou du code. Pour éviter un impact sur les performances, vous devez éviter de rendre les lignes non partagées. Pendant le développement d’applications, vous pouvez gérer l’événement <xref:System.Windows.Forms.DataGridView.RowUnshared> pour déterminer quand les lignes deviennent non partagées. Cela est utile lors du débogage de problèmes de partage de lignes.

Pour empêcher le partage de lignes, suivez les instructions ci-dessous :

- Évitez d’indexer la collection <xref:System.Windows.Forms.DataGridView.Rows%2A> ou d’effectuer une itération à l’aide d’une boucle `foreach`. En général, vous n’avez pas besoin d’accéder directement aux lignes. <xref:System.Windows.Forms.DataGridView> méthodes qui opèrent sur des lignes prennent des arguments d’index de ligne plutôt que des instances de ligne. En outre, les gestionnaires des événements liés aux lignes reçoivent des objets d’argument d’événement avec des propriétés de ligne que vous pouvez utiliser pour manipuler des lignes sans les rendre non partagées.

- Si vous devez accéder à un objet Row, utilisez la méthode <xref:System.Windows.Forms.DataGridViewRowCollection.SharedRow%2A?displayProperty=nameWithType> et transmettez l’index réel de la ligne. Notez, toutefois, que la modification d’un objet de ligne partagé récupéré via cette méthode modifiera toutes les lignes qui partagent cet objet. Toutefois, la ligne des nouveaux enregistrements n’est pas partagée avec d’autres lignes. par conséquent, elle n’est pas affectée lorsque vous modifiez une autre ligne. Notez également que les différentes lignes représentées par une ligne partagée peuvent avoir des menus contextuels différents. Pour récupérer le menu contextuel approprié à partir d’une instance de ligne partagée, utilisez la méthode <xref:System.Windows.Forms.DataGridViewRow.GetContextMenuStrip%2A> et transmettez l’index réel de la ligne. Si vous accédez à la propriété <xref:System.Windows.Forms.DataGridViewRow.ContextMenuStrip%2A> de la ligne partagée à la place, elle utilise l’index de ligne partagé-1 et ne récupère pas le menu contextuel approprié.

- Évitez d’indexer la collection <xref:System.Windows.Forms.DataGridViewRow.Cells%2A?displayProperty=nameWithType>. L’accès direct à une cellule entraîne le non-partage de sa ligne parente, l’instanciation d’un nouveau <xref:System.Windows.Forms.DataGridViewRow>. Les gestionnaires pour les événements liés aux cellules reçoivent des objets d’argument d’événement avec des propriétés de cellule que vous pouvez utiliser pour manipuler des cellules sans entraîner le partage de lignes. Vous pouvez également utiliser la propriété <xref:System.Windows.Forms.DataGridView.CurrentCellAddress%2A> pour récupérer les index de ligne et de colonne de la cellule active sans accéder directement à la cellule.

- Évitez les modes de sélection basés sur des cellules. Ces modes entraînent le non-partage des lignes. Au lieu de cela, affectez à la propriété <xref:System.Windows.Forms.DataGridView.SelectionMode%2A?displayProperty=nameWithType> la valeur <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect?displayProperty=nameWithType> ou <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect?displayProperty=nameWithType>.

- Ne gérez pas les événements <xref:System.Windows.Forms.DataGridViewRowCollection.CollectionChanged?displayProperty=nameWithType> ou <xref:System.Windows.Forms.DataGridView.RowStateChanged?displayProperty=nameWithType>. Ces événements entraînent le non-partage des lignes. En outre, n’appelez pas les méthodes <xref:System.Windows.Forms.DataGridViewRowCollection.OnCollectionChanged%2A?displayProperty=nameWithType> ou <xref:System.Windows.Forms.DataGridView.OnRowStateChanged%2A?displayProperty=nameWithType>, qui déclenchent ces événements.

- N’accédez pas à la collection <xref:System.Windows.Forms.DataGridView.SelectedCells%2A?displayProperty=nameWithType> lorsque la valeur de la propriété <xref:System.Windows.Forms.DataGridView.SelectionMode%2A?displayProperty=nameWithType> est <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect>, <xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>, <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect>ou <xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect>. Toutes les lignes sélectionnées ne sont alors plus partagées.

- N’appelez pas la méthode <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A?displayProperty=nameWithType>. Cette méthode peut provoquer le non-partage de lignes.

- N’appelez pas la méthode <xref:System.Windows.Forms.DataGridView.SelectAll%2A?displayProperty=nameWithType> lorsque la valeur de la propriété <xref:System.Windows.Forms.DataGridView.SelectionMode%2A?displayProperty=nameWithType> est <xref:System.Windows.Forms.DataGridViewSelectionMode.CellSelect>. Toutes les lignes deviennent alors non partagées.

- Ne définissez pas la propriété <xref:System.Windows.Forms.DataGridViewCell.ReadOnly%2A> ou <xref:System.Windows.Forms.DataGridViewCell.Selected%2A> d’une cellule sur `false` lorsque la propriété correspondante dans sa colonne est définie sur `true`. Toutes les lignes deviennent alors non partagées.

- N’accédez pas à la propriété <xref:System.Windows.Forms.DataGridViewRowCollection.List%2A?displayProperty=nameWithType>. Toutes les lignes deviennent alors non partagées.

- N’appelez pas la surcharge `Sort(IComparer)` de la méthode <xref:System.Windows.Forms.DataGridView.Sort%2A>. Si vous triez avec un comparateur personnalisé, toutes les lignes deviennent non partagées.

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.DataGridView>
- [Réglage des performances dans le contrôle DataGridView Windows Forms](performance-tuning-in-the-windows-forms-datagridview-control.md)
- [Mode virtuel dans le contrôle DataGridView Windows Forms](virtual-mode-in-the-windows-forms-datagridview-control.md)
- [Modes d’affichage des données dans le contrôle DataGridView Windows Forms](data-display-modes-in-the-windows-forms-datagridview-control.md)
- [Styles de cellules dans le contrôle DataGridView Windows Forms](cell-styles-in-the-windows-forms-datagridview-control.md)
- [Guide pratique pour définir les styles de cellules par défaut pour le contrôle DataGridView Windows Forms](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md)
- [Options de dimensionnement dans le contrôle DataGridView Windows Forms](sizing-options-in-the-windows-forms-datagridview-control.md)
