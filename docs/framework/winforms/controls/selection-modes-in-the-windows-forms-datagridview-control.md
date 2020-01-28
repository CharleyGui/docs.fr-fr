---
title: Modes de sélection dans le contrôle DataGridView
ms.date: 03/30/2017
helpviewer_keywords:
- selection [Windows Forms], modes in DataGridView control
- DataGridView control [Windows Forms], selection mode
ms.assetid: a3ebfd3d-0525-479d-9d96-d9e017289b36
ms.openlocfilehash: e20bf6307d77bf189b698e847c6b855c249dc3c1
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743041"
---
# <a name="selection-modes-in-the-windows-forms-datagridview-control"></a>Modes de sélection dans le contrôle DataGridView Windows Forms

Parfois, vous souhaitez que votre application effectue des actions en fonction des sélections de l’utilisateur au sein d’un contrôle de <xref:System.Windows.Forms.DataGridView>. Selon les actions, vous souhaiterez peut-être limiter les types de sélection possibles. Supposons, par exemple, que votre application peut imprimer un rapport pour l’enregistrement actuellement sélectionné. Dans ce cas, vous pouvez configurer le contrôle <xref:System.Windows.Forms.DataGridView> afin que le fait de cliquer n’importe où dans une ligne sélectionne toujours la ligne entière, et de sorte qu’une seule ligne à la fois peut être sélectionnée.

Vous pouvez spécifier les sélections autorisées en affectant à la propriété <xref:System.Windows.Forms.DataGridView.SelectionMode%2A?displayProperty=nameWithType> l’une des valeurs d’énumération <xref:System.Windows.Forms.DataGridViewSelectionMode> suivantes.

|Valeur DataGridViewSelectionMode|Description|
|-------------------------------------|-----------------|
|<xref:System.Windows.Forms.DataGridViewSelectionMode.CellSelect>|Cliquez sur une cellule pour la sélectionner. Les en-têtes de ligne et de colonne ne peuvent pas être utilisés pour la sélection.|
|<xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>|Cliquez sur une cellule pour la sélectionner. Cliquez sur un en-tête de colonne pour sélectionner la colonne entière. Les en-têtes de colonne ne peuvent pas être utilisés pour le tri.|
|<xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect>|Cliquer sur une cellule ou un en-tête de colonne sélectionne la colonne entière. Les en-têtes de colonne ne peuvent pas être utilisés pour le tri.|
|<xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect>|Cliquer sur une cellule ou un en-tête de ligne sélectionne la ligne entière.|
|<xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect>|Mode de sélection par défaut. Cliquez sur une cellule pour la sélectionner. Cliquer sur un en-tête de ligne sélectionne la ligne entière.|

> [!NOTE]
> La modification du mode de sélection au moment de l’exécution efface automatiquement la sélection actuelle.

Par défaut, les utilisateurs peuvent sélectionner plusieurs lignes, colonnes ou cellules en les faisant glisser avec la souris, en appuyant sur CTRL ou Maj tout en sélectionnant pour étendre ou modifier une sélection, ou en cliquant sur la cellule d’en-tête en haut à gauche pour sélectionner toutes les cellules du contrôle. Pour éviter ce comportement, affectez à la propriété <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> la valeur `false`.

Les modes <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect> et <xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect> permettent aux utilisateurs de supprimer des lignes en les sélectionnant et en appuyant sur la touche Suppr. Les utilisateurs peuvent supprimer des lignes uniquement lorsque la cellule active n’est pas en mode édition, que la propriété <xref:System.Windows.Forms.DataGridView.AllowUserToDeleteRows%2A> est définie sur `true`et que la source de données sous-jacente prend en charge la suppression de lignes pilotées par l’utilisateur. Notez que ces paramètres n’empêchent pas la suppression de lignes par programmation.

## <a name="programmatic-selection"></a>Sélection par programmation

Le mode de sélection actuel limite le comportement de sélection par programmation, ainsi que la sélection de l’utilisateur. Vous pouvez modifier la sélection actuelle par programme en définissant la propriété `Selected` des cellules, lignes ou colonnes présentes dans le contrôle <xref:System.Windows.Forms.DataGridView>. Vous pouvez également sélectionner toutes les cellules du contrôle à l’aide de la méthode <xref:System.Windows.Forms.DataGridView.SelectAll%2A>, selon le mode de sélection. Pour effacer la sélection, utilisez la méthode <xref:System.Windows.Forms.DataGridView.ClearSelection%2A>.

Si la propriété <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> est définie sur `true`, vous pouvez ajouter des éléments <xref:System.Windows.Forms.DataGridView> ou les supprimer de la sélection en modifiant la propriété `Selected` de l’élément. Sinon, si vous affectez à la propriété `Selected` la valeur `true` pour un élément, vous supprimez automatiquement d’autres éléments de la sélection.

Notez que la modification de la valeur de la propriété <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> ne modifie pas la sélection actuelle.

Vous pouvez récupérer une collection des cellules, lignes ou colonnes actuellement sélectionnées par le biais des propriétés <xref:System.Windows.Forms.DataGridView.SelectedCells%2A>, <xref:System.Windows.Forms.DataGridView.SelectedRows%2A>et <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> du contrôle <xref:System.Windows.Forms.DataGridView>. L’accès à ces propriétés est inefficace lorsque chaque cellule du contrôle est sélectionnée. Pour éviter une baisse des performances dans ce cas, utilisez d’abord la méthode <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A>. En outre, l’accès à ces collections pour déterminer le nombre de cellules, de lignes ou de colonnes sélectionnées peut être inefficace. Au lieu de cela, vous devez utiliser la méthode <xref:System.Windows.Forms.DataGridView.GetCellCount%2A>, <xref:System.Windows.Forms.DataGridViewRowCollection.GetRowCount%2A>ou <xref:System.Windows.Forms.DataGridViewColumnCollection.GetColumnCount%2A>, en passant la valeur <xref:System.Windows.Forms.DataGridViewElementStates.Selected>.

> [!TIP]
> Vous trouverez un exemple de code illustrant l’utilisation par programmation des cellules sélectionnées dans la <xref:System.Windows.Forms.DataGridView> vue d’ensemble de la classe.

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.MultiSelect%2A>
- <xref:System.Windows.Forms.DataGridView.SelectionMode%2A>
- <xref:System.Windows.Forms.DataGridViewSelectionMode>
- [Sélection et utilisation du Presse-papiers avec le contrôle DataGridView Windows Forms](selection-and-clipboard-use-with-the-windows-forms-datagridview-control.md)
- [Guide pratique pour définir le mode de sélection du contrôle DataGridView Windows Forms](how-to-set-the-selection-mode-of-the-windows-forms-datagridview-control.md)
