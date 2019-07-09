---
title: Meilleures pratiques pour la mise à l'échelle du contrôle DataGridView Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], row sharing
- data grids [Windows Forms], best practices
- DataGridView control [Windows Forms], shared rows
- DataGridView control [Windows Forms], best practices
- best practices [Windows Forms], dataGridView control
- DataGridView control [Windows Forms], scaling
ms.assetid: 8321a8a6-6340-4fd1-b475-fa090b905aaf
ms.openlocfilehash: 65afd73c166332f08003c3b3bfcc70e488d0373a
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67663555"
---
# <a name="best-practices-for-scaling-the-windows-forms-datagridview-control"></a>Meilleures pratiques pour la mise à l'échelle du contrôle DataGridView Windows Forms

Le <xref:System.Windows.Forms.DataGridView> contrôle est conçu pour fournir une extensibilité maximale. Si vous avez besoin afficher de grandes quantités de données, vous devez suivre les instructions décrites dans cette rubrique afin d’éviter de consommer de grandes quantités de mémoire ou d’affecter la réactivité de l’interface utilisateur (IU). Cette rubrique présente les problèmes suivants :

- Utilisation efficace de styles de cellules

- Utilisation efficace des menus contextuels

- Utilisation efficace du redimensionnement automatique

- Utilisation efficace des collections de cellules, lignes et colonnes sélectionnées

- À l’aide de lignes partagées

- Empêcher les lignes de devenir non partagées

Si vous avez besoin de performances spéciales, vous pouvez implémenter le mode virtuel et fournir vos propres opérations de gestion de données. Pour plus d’informations, consultez [Modes d’affichage de données dans le contrôle DataGridView Windows Forms](data-display-modes-in-the-windows-forms-datagridview-control.md).

## <a name="using-cell-styles-efficiently"></a>Utilisation efficace de Styles de cellules

Chaque cellule, la ligne et la colonne peuvent avoir ses propres informations de style. Les informations de style sont stockées dans <xref:System.Windows.Forms.DataGridViewCellStyle> objets. Créer des objets de style de cellule pour les nombreux <xref:System.Windows.Forms.DataGridView> éléments peuvent être inefficaces, en particulier lorsque vous travaillez avec grandes quantités de données. Pour éviter un impact sur les performances, utilisez les instructions suivantes :

- Évitez de définir les propriétés de style de cellule pour personne <xref:System.Windows.Forms.DataGridViewCell> ou <xref:System.Windows.Forms.DataGridViewRow> objets. Cela inclut l’objet de ligne spécifié par le <xref:System.Windows.Forms.DataGridView.RowTemplate%2A> propriété. Chaque nouvelle ligne est cloné à partir du modèle de ligne recevra sa propre copie d’objet de style de cellule du modèle. Pour optimiser l’évolutivité, définissez les propriétés de style de cellule à le <xref:System.Windows.Forms.DataGridView> niveau. Par exemple, définissez la <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> propriété plutôt que <xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=nameWithType> propriété.

- Si certaines cellules nécessitent une mise en forme autre que la mise en forme par défaut, utilisez le même <xref:System.Windows.Forms.DataGridViewCellStyle> instance entre des groupes de cellules, lignes ou colonnes. Évitez de définir directement les propriétés de type <xref:System.Windows.Forms.DataGridViewCellStyle> sur des cellules, lignes et colonnes. Pour obtenir un exemple de partage de style de cellule, consultez [Comment : Définir des Styles de cellules par défaut pour les Windows Forms DataGridView Control](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md). Vous pouvez également éviter une baisse des performances lors de la définition des styles de cellules individuellement en gérant le <xref:System.Windows.Forms.DataGridView.CellFormatting> Gestionnaire d’événements. Pour voir un exemple, consultez [Comment : Personnaliser la mise en forme des données dans le contrôle de DataGridView Windows Forms](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).

- Lorsque vous déterminez le style d’une cellule, utilisez la <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A?displayProperty=nameWithType> propriété plutôt que <xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=nameWithType> propriété. L’accès à la <xref:System.Windows.Forms.DataGridViewCell.Style%2A> propriété crée une nouvelle instance de la <xref:System.Windows.Forms.DataGridViewCellStyle> classe si la propriété n’a pas déjà été utilisée. En outre, cet objet ne peut pas contenir les informations de style complètes pour la cellule si certains styles sont héritées à partir de la ligne, la colonne ou le contrôle. Pour plus d’informations sur l’héritage de style de cellule, consultez [Styles de cellules dans le contrôle DataGridView Windows Forms](cell-styles-in-the-windows-forms-datagridview-control.md).

## <a name="using-shortcut-menus-efficiently"></a>Utilisation efficace des Menus contextuels

Chaque cellule, la ligne et la colonne peuvent avoir son propre menu contextuel. Menus contextuels dans le <xref:System.Windows.Forms.DataGridView> contrôle sont représentées par <xref:System.Windows.Forms.ContextMenuStrip> contrôles. Comme avec les objets de style de cellule, création de menus contextuels de chaque nombre <xref:System.Windows.Forms.DataGridView> éléments affecte négativement les performances. Pour éviter cet inconvénient, utilisez les instructions suivantes :

- Évitez de créer des menus contextuels pour des cellules et des lignes. Cela inclut le modèle de ligne qui est cloné, ainsi que son menu contextuel lorsque de nouvelles lignes sont ajoutées au contrôle. Pour optimiser l’évolutivité, utilisez uniquement du contrôle <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> propriété pour spécifier un menu contextuel unique pour l’ensemble du contrôle.

- Si vous avez besoin de plusieurs menus contextuels pour plusieurs lignes ou cellules, gérez les <xref:System.Windows.Forms.DataGridView.CellContextMenuStripNeeded> ou <xref:System.Windows.Forms.DataGridView.RowContextMenuStripNeeded> événements. Ces événements vous permettent de gérer les objets de menu contextuel vous-même, ce qui vous permet d’optimiser les performances.

## <a name="using-automatic-resizing-efficiently"></a>Utilisation efficace du redimensionnement automatique

Lignes, colonnes et en-têtes peuvent être automatiquement redimensionnées en tant que les modifications de contenu de cellule afin que tout le contenu des cellules est affiché sans découpage. Modification des modes de dimensionnement pouvez également redimensionner les lignes, colonnes et en-têtes. Pour déterminer la taille correcte, le <xref:System.Windows.Forms.DataGridView> contrôle doit examiner la valeur de chaque cellule qu’il doit prendre en charge. Lorsque vous travaillez avec grands jeux de données, cette analyse peut un impact négatif sur les performances du contrôle lorsque le redimensionnement automatique se produit. Pour éviter une dégradation des performances, utilisez les instructions suivantes :

- Évitez d’utiliser le dimensionnement automatique sur un <xref:System.Windows.Forms.DataGridView> contrôle avec un grand nombre de lignes. Si vous utilisez le dimensionnement automatique, redimensionnez uniquement selon les lignes affichées. Utiliser uniquement les lignes affichées en mode virtuel également.

  - Pour les lignes et colonnes, utilisez le `DisplayedCells` ou `DisplayedCellsExceptHeaders` champ la <xref:System.Windows.Forms.DataGridViewAutoSizeRowsMode>, <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode>, et <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode> énumérations.

  - Pour les en-têtes de ligne, utilisez le <xref:System.Windows.Forms.DataGridViewRowHeadersWidthSizeMode.AutoSizeToDisplayedHeaders> ou <xref:System.Windows.Forms.DataGridViewRowHeadersWidthSizeMode.AutoSizeToFirstHeader> champ la <xref:System.Windows.Forms.DataGridViewRowHeadersWidthSizeMode> énumération.

- Pour optimiser l’évolutivité, désactivez le dimensionnement automatique et utilisez le redimensionnement par programmation.

Pour plus d’informations, consultez [les Options de dimensionnement dans le contrôle de DataGridView Windows Forms](sizing-options-in-the-windows-forms-datagridview-control.md).

## <a name="using-the-selected-cells-rows-and-columns-collections-efficiently"></a>Utilisation efficace des Collections de colonnes, lignes et cellules sélectionnées

Le <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> collection n’effectue pas efficacement avec les grandes sélections. Le <xref:System.Windows.Forms.DataGridView.SelectedRows%2A> et <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> collections peuvent également être inefficaces, bien qu’à un degré moindre, car il existe beaucoup moins de lignes que de cellules dans un type <xref:System.Windows.Forms.DataGridView> contrôle et beaucoup moins de colonnes que de lignes. Pour éviter la dégradation des performances lorsque vous travaillez avec ces collections, utilisez les instructions suivantes :

- Pour déterminer si toutes les cellules de la <xref:System.Windows.Forms.DataGridView> ont été sélectionnées avant de vous accéder au contenu de la <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> collection, vérifiez la valeur de retour de la <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A> (méthode). Toutefois, notez que cette méthode peut entraîner des lignes deviennent non partagées. Pour plus d'informations, consultez la section suivante.

- Évitez d’utiliser le <xref:System.Collections.ICollection.Count%2A> propriété de la <xref:System.Windows.Forms.DataGridViewSelectedCellCollection?displayProperty=nameWithType> pour déterminer le nombre de cellules sélectionnées. Au lieu de cela, utilisez le <xref:System.Windows.Forms.DataGridView.GetCellCount%2A?displayProperty=nameWithType> (méthode) et passez le <xref:System.Windows.Forms.DataGridViewElementStates.Selected?displayProperty=nameWithType> valeur. De même, utilisez le <xref:System.Windows.Forms.DataGridViewRowCollection.GetRowCount%2A?displayProperty=nameWithType> et <xref:System.Windows.Forms.DataGridViewColumnCollection.GetColumnCount%2A?displayProperty=nameWithType> méthodes pour déterminer le nombre d’éléments sélectionnés, plutôt que d’accéder aux collections de lignes et de colonnes sélectionnées.

- Évitez les modes de sélection basée sur la cellule. Au lieu de cela, définissez la <xref:System.Windows.Forms.DataGridView.SelectionMode%2A?displayProperty=nameWithType> propriété <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect?displayProperty=nameWithType> ou <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect?displayProperty=nameWithType>.

## <a name="using-shared-rows"></a>À l’aide de partagé des lignes

Utilisation de la mémoire efficace s’effectue dans le <xref:System.Windows.Forms.DataGridView> contrôle lignes partagées. Lignes partageront autant d’informations sur leur apparence et leur comportement que possible en partageant des instances de la <xref:System.Windows.Forms.DataGridViewRow> classe.

Alors que le partage des instances de ligne économise de la mémoire, les lignes peuvent facilement devenir non partagées. Par exemple, chaque fois qu’un utilisateur interagit directement avec une cellule, sa ligne n’est partagée ou non. Étant donné que cela ne peut pas être évité, les instructions de cette rubrique sont utiles uniquement lorsque vous travaillez avec très grandes quantités de données et uniquement lorsque les utilisateurs interagissent avec une relativement petite partie des données chaque fois que votre programme est exécuté.

Une ligne ne peut pas être partagée dans un indépendant <xref:System.Windows.Forms.DataGridView> contrôler si l’un de ses cellules contient des valeurs. Lorsque le <xref:System.Windows.Forms.DataGridView> contrôle est lié à une source de données externe ou lorsque vous implémentez le mode virtuel et fournissez votre propre source de données, les valeurs de cellule sont stockées en dehors du contrôle plutôt que dans les objets cell, permettant aux lignes d’être partagées.

Un objet ligne peut uniquement être partagé si l’état de toutes ses cellules peut être déterminé à partir de l’état de la ligne et les États des colonnes contenant les cellules. Si vous modifiez l’état d’une cellule afin qu’il n’est plus peut être déduit qu’à partir de l’état de sa ligne et de colonne, la ligne ne peut pas être partagée.

Par exemple, une ligne ne peut pas être partagée dans les situations suivantes :

- La ligne contient une seule cellule sélectionnée qui n’est pas dans une colonne sélectionnée.

- La ligne contient une cellule avec son <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A> ou <xref:System.Windows.Forms.DataGridViewCell.ContextMenuStrip%2A> jeu de propriétés.

- La ligne contient un <xref:System.Windows.Forms.DataGridViewComboBoxCell> avec son <xref:System.Windows.Forms.DataGridViewComboBoxCell.Items%2A> jeu de propriétés.

En mode dépendant ou virtuel, vous pouvez fournir des info-bulles et des menus contextuels pour les cellules individuelles en gérant la <xref:System.Windows.Forms.DataGridView.CellToolTipTextNeeded> et <xref:System.Windows.Forms.DataGridView.CellContextMenuStripNeeded> événements.

Le <xref:System.Windows.Forms.DataGridView> contrôle tente automatiquement d’utiliser des lignes partagées chaque fois que les lignes sont ajoutées à la <xref:System.Windows.Forms.DataGridViewRowCollection>. Utilisez les instructions suivantes pour vous assurer que les lignes sont partagés :

- Évitez d’appeler le `Add(Object[])` surcharge de la <xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A> (méthode) et le `Insert(Object[])` surcharge de la <xref:System.Windows.Forms.DataGridViewRowCollection.Insert%2A> méthode de la <xref:System.Windows.Forms.DataGridView.Rows%2A?displayProperty=nameWithType> collection. Ces surcharges créent automatiquement des lignes non partagées.

- Veillez à ce que la ligne spécifiée dans le <xref:System.Windows.Forms.DataGridView.RowTemplate%2A?displayProperty=nameWithType> propriété peut être partagée dans les cas suivants :

  - Lors de l’appel le `Add()` ou `Add(Int32)` des surcharges de la <xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A> (méthode) ou le `Insert(Int32,Int32)` surcharge de la <xref:System.Windows.Forms.DataGridViewRowCollection.Insert%2A> méthode de la <xref:System.Windows.Forms.DataGridView.Rows%2A?displayProperty=nameWithType> collection.

  - Lorsque vous augmentez la valeur de la <xref:System.Windows.Forms.DataGridView.RowCount%2A?displayProperty=nameWithType> propriété.

  - Lors de la définition du <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType> propriété.

- Également vous assurer que la ligne indiquée par le `indexSource` paramètre peut être partagé lors de l’appel le <xref:System.Windows.Forms.DataGridViewRowCollection.AddCopy%2A>, <xref:System.Windows.Forms.DataGridViewRowCollection.AddCopies%2A>, <xref:System.Windows.Forms.DataGridViewRowCollection.InsertCopy%2A>, et <xref:System.Windows.Forms.DataGridViewRowCollection.InsertCopies%2A> méthodes de la <xref:System.Windows.Forms.DataGridView.Rows%2A?displayProperty=nameWithType> collection.

- N’oubliez pas que l’ou les lignes spécifiées peuvent être partagées lors de l’appel le `Add(DataGridViewRow)` surcharge de la <xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A> (méthode), le <xref:System.Windows.Forms.DataGridViewRowCollection.AddRange%2A> (méthode), le `Insert(Int32,DataGridViewRow)` surcharge de la <xref:System.Windows.Forms.DataGridViewRowCollection.Insert%2A> (méthode) et le <xref:System.Windows.Forms.DataGridViewRowCollection.InsertRange%2A> procédé de la <xref:System.Windows.Forms.DataGridView.Rows%2A?displayProperty=nameWithType>collection.

Pour déterminer si une ligne est partagée, utilisez la <xref:System.Windows.Forms.DataGridViewRowCollection.SharedRow%2A?displayProperty=nameWithType> méthode pour récupérer l’objet de ligne, puis vérifiez l’objet <xref:System.Windows.Forms.DataGridViewBand.Index%2A> propriété. Lignes partagées ont toujours une <xref:System.Windows.Forms.DataGridViewBand.Index%2A> valeur de propriété de -1.

## <a name="preventing-rows-from-becoming-unshared"></a>Empêcher les lignes de devenir non partagées

Lignes partagées peuvent devenir non partagées à la suite de code ou une action utilisateur. Pour éviter un impact sur les performances, vous devez éviter que les lignes deviennent non partagées. Au cours de développement d’applications, vous pouvez gérer le <xref:System.Windows.Forms.DataGridView.RowUnshared> événement pour déterminer quand les lignes deviennent non partagées. Cela est utile lors du débogage des problèmes de partage de lignes.

Pour empêcher les lignes de devenir non partagées, procédez comme suit :

- Évitez d’indexer le <xref:System.Windows.Forms.DataGridView.Rows%2A> collection ou itérer avec un `foreach` boucle. Il est généralement inutile d’accéder directement aux lignes. <xref:System.Windows.Forms.DataGridView> méthodes qui fonctionnent sur les lignes prennent des arguments d’index de ligne plutôt que des instances de ligne. En outre, gestionnaires d’événements de ligne de recevoir des objets d’argument d’événement avec les propriétés de ligne que vous pouvez utiliser pour manipuler les lignes sans qu’elles deviennent non partagées.

- Si vous avez besoin pour accéder à un objet de ligne, utilisez le <xref:System.Windows.Forms.DataGridViewRowCollection.SharedRow%2A?displayProperty=nameWithType> (méthode) et passez l’index de la ligne réelle. Toutefois, notez que la modification d’un objet de ligne partagé récupéré via cette méthode modifiera toutes les lignes qui partagent cet objet. La ligne des nouveaux enregistrements n’est pas partagée avec d’autres lignes, toutefois, pour qu’elle ne sera pas affectée lorsque vous modifiez des autres lignes. Notez également que différentes lignes représentées par une ligne partagée peuvent avoir des menus contextuels différents. Pour récupérer le menu contextuel correct à partir d’une instance de ligne partagée, utilisez la <xref:System.Windows.Forms.DataGridViewRow.GetContextMenuStrip%2A> (méthode) et passez l’index de la ligne réelle. Si vous accédez à la ligne partagée <xref:System.Windows.Forms.DataGridViewRow.ContextMenuStrip%2A> propriété au lieu de cela, il utilisera l’index de ligne partagé-1 et ne récupérera pas le menu contextuel correct.

- Évitez d’indexer le <xref:System.Windows.Forms.DataGridViewRow.Cells%2A?displayProperty=nameWithType> collection. Accéder directement à une cellule entraîne sa ligne parente devient non partagée, l’instanciation d’un nouvel <xref:System.Windows.Forms.DataGridViewRow>. Gestionnaires d’événements de la cellule de recevoir des objets d’argument d’événement avec les propriétés de cellule que vous pouvez utiliser pour manipuler des cellules sans que les lignes deviennent non partagées. Vous pouvez également utiliser le <xref:System.Windows.Forms.DataGridView.CurrentCellAddress%2A> propriété à récupérer l’index de ligne et colonne de la cellule active sans accéder directement à la cellule.

- Évitez les modes de sélection basée sur la cellule. Ces modes, les lignes deviennent non partagées. Au lieu de cela, définissez la <xref:System.Windows.Forms.DataGridView.SelectionMode%2A?displayProperty=nameWithType> propriété <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect?displayProperty=nameWithType> ou <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect?displayProperty=nameWithType>.

- Ne gèrent pas la <xref:System.Windows.Forms.DataGridViewRowCollection.CollectionChanged?displayProperty=nameWithType> ou <xref:System.Windows.Forms.DataGridView.RowStateChanged?displayProperty=nameWithType> événements. Ces événements, les lignes deviennent non partagées. En outre, n’appelez pas la <xref:System.Windows.Forms.DataGridViewRowCollection.OnCollectionChanged%2A?displayProperty=nameWithType> ou <xref:System.Windows.Forms.DataGridView.OnRowStateChanged%2A?displayProperty=nameWithType> méthodes qui déclenchent ces événements.

- N’accèdent pas à la <xref:System.Windows.Forms.DataGridView.SelectedCells%2A?displayProperty=nameWithType> collection lorsque le <xref:System.Windows.Forms.DataGridView.SelectionMode%2A?displayProperty=nameWithType> valeur de propriété est <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect>, <xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>, <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect>, ou <xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect>. Cela entraîne de toutes les lignes sélectionnées deviennent non partagées.

- N’appelez pas la <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A?displayProperty=nameWithType> (méthode). Cette méthode peut entraîner des lignes deviennent non partagées.

- N’appelez pas la <xref:System.Windows.Forms.DataGridView.SelectAll%2A?displayProperty=nameWithType> méthode lorsque le <xref:System.Windows.Forms.DataGridView.SelectionMode%2A?displayProperty=nameWithType> valeur de propriété est <xref:System.Windows.Forms.DataGridViewSelectionMode.CellSelect>. Toutes les lignes deviennent non partagées.

- Ne définissez pas la <xref:System.Windows.Forms.DataGridViewCell.ReadOnly%2A> ou <xref:System.Windows.Forms.DataGridViewCell.Selected%2A> propriété d’une cellule à `false` lorsque la propriété correspondante dans sa colonne est définie `true`. Toutes les lignes deviennent non partagées.

- N’accédez pas à la <xref:System.Windows.Forms.DataGridViewRowCollection.List%2A?displayProperty=nameWithType> propriété. Toutes les lignes deviennent non partagées.

- N’appelez pas la `Sort(IComparer)` surcharge de la <xref:System.Windows.Forms.DataGridView.Sort%2A> (méthode). Tri avec un comparateur personnalisé provoque toutes les lignes deviennent non partagées.

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.DataGridView>
- [Réglage des performances dans le contrôle DataGridView Windows Forms](performance-tuning-in-the-windows-forms-datagridview-control.md)
- [Mode virtuel dans le contrôle DataGridView Windows Forms](virtual-mode-in-the-windows-forms-datagridview-control.md)
- [Modes d’affichage des données dans le contrôle DataGridView Windows Forms](data-display-modes-in-the-windows-forms-datagridview-control.md)
- [Styles de cellules dans le contrôle DataGridView Windows Forms](cell-styles-in-the-windows-forms-datagridview-control.md)
- [Guide pratique pour Définir des Styles de cellules par défaut pour le contrôle de DataGridView Windows Forms](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md)
- [Options de dimensionnement dans le contrôle DataGridView Windows Forms](sizing-options-in-the-windows-forms-datagridview-control.md)
