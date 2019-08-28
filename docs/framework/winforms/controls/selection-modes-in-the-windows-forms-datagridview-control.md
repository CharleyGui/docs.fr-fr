---
title: Modes de sélection dans le contrôle DataGridView Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- selection [Windows Forms], modes in DataGridView control
- DataGridView control [Windows Forms], selection mode
ms.assetid: a3ebfd3d-0525-479d-9d96-d9e017289b36
ms.openlocfilehash: cfe80d5ccb73208f1c61a2ac6c9963343d398bcb
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046419"
---
# <a name="selection-modes-in-the-windows-forms-datagridview-control"></a>Modes de sélection dans le contrôle DataGridView Windows Forms

Parfois, vous souhaitez que votre application effectue des actions en fonction des sélections de l’utilisateur dans un <xref:System.Windows.Forms.DataGridView> contrôle. Selon les actions, vous souhaiterez peut-être limiter les types de sélection possibles. Supposons, par exemple, que votre application peut imprimer un rapport pour l’enregistrement actuellement sélectionné. Dans ce cas, vous pouvez configurer le <xref:System.Windows.Forms.DataGridView> contrôle afin que le fait de cliquer n’importe où dans une ligne sélectionne toujours la ligne entière, et de sorte qu’une seule ligne à la fois peut être sélectionnée.

Vous pouvez spécifier les sélections autorisées en affectant à la <xref:System.Windows.Forms.DataGridView.SelectionMode%2A?displayProperty=nameWithType> propriété l’une des valeurs d’énumération suivantes. <xref:System.Windows.Forms.DataGridViewSelectionMode>

|Valeur DataGridViewSelectionMode|Description|
|-------------------------------------|-----------------|
|<xref:System.Windows.Forms.DataGridViewSelectionMode.CellSelect>|Cliquez sur une cellule pour la sélectionner. Les en-têtes de ligne et de colonne ne peuvent pas être utilisés pour la sélection.|
|<xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>|Cliquez sur une cellule pour la sélectionner. Cliquez sur un en-tête de colonne pour sélectionner la colonne entière. Les en-têtes de colonne ne peuvent pas être utilisés pour le tri.|
|<xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect>|Cliquer sur une cellule ou un en-tête de colonne sélectionne la colonne entière. Les en-têtes de colonne ne peuvent pas être utilisés pour le tri.|
|<xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect>|Cliquer sur une cellule ou un en-tête de ligne sélectionne la ligne entière.|
|<xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect>|Mode de sélection par défaut. Cliquez sur une cellule pour la sélectionner. Cliquer sur un en-tête de ligne sélectionne la ligne entière.|

> [!NOTE]
> La modification du mode de sélection au moment de l’exécution efface automatiquement la sélection actuelle.

Par défaut, les utilisateurs peuvent sélectionner plusieurs lignes, colonnes ou cellules en les faisant glisser avec la souris, en appuyant sur CTRL ou Maj tout en sélectionnant pour étendre ou modifier une sélection, ou en cliquant sur la cellule d’en-tête en haut à gauche pour sélectionner toutes les cellules du contrôle. Pour éviter ce comportement, affectez <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> à `false`la propriété la valeur.

Les <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect> modes <xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect> et permettent aux utilisateurs de supprimer des lignes en les sélectionnant et en appuyant sur la touche Suppr. Les utilisateurs peuvent supprimer des lignes uniquement lorsque la cellule active n’est pas en mode <xref:System.Windows.Forms.DataGridView.AllowUserToDeleteRows%2A> édition, que la `true`propriété a la valeur et que la source de données sous-jacente prend en charge la suppression de lignes pilotées par l’utilisateur. Notez que ces paramètres n’empêchent pas la suppression de lignes par programmation.

## <a name="programmatic-selection"></a>Sélection par programmation

Le mode de sélection actuel limite le comportement de sélection par programmation, ainsi que la sélection de l’utilisateur. Vous pouvez modifier la sélection actuelle par programme en définissant la `Selected` propriété des cellules, des lignes ou des colonnes présentes dans le <xref:System.Windows.Forms.DataGridView> contrôle. Vous pouvez également sélectionner toutes les cellules du contrôle à l' <xref:System.Windows.Forms.DataGridView.SelectAll%2A> aide de la méthode, en fonction du mode de sélection. Pour effacer la sélection, utilisez la <xref:System.Windows.Forms.DataGridView.ClearSelection%2A> méthode.

Si la <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> propriété a la `true`valeur, vous pouvez ajouter <xref:System.Windows.Forms.DataGridView> ou supprimer des éléments de la sélection en modifiant la `Selected` propriété de l’élément. Sinon, si vous `Selected` affectez `true` à la propriété la valeur pour un élément, vous supprimez automatiquement les autres éléments de la sélection.

Notez que la modification de la valeur <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> de la propriété ne modifie pas la sélection actuelle.

Vous pouvez récupérer une collection des cellules, lignes ou colonnes <xref:System.Windows.Forms.DataGridView.SelectedCells%2A>sélectionnées à l’aide des propriétés, <xref:System.Windows.Forms.DataGridView.SelectedRows%2A>et <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> du <xref:System.Windows.Forms.DataGridView> contrôle. L’accès à ces propriétés est inefficace lorsque chaque cellule du contrôle est sélectionnée. Pour éviter une altération des performances dans ce cas, utilisez <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A> d’abord la méthode. En outre, l’accès à ces collections pour déterminer le nombre de cellules, de lignes ou de colonnes sélectionnées peut être inefficace. Au lieu de cela, vous <xref:System.Windows.Forms.DataGridView.GetCellCount%2A>devez <xref:System.Windows.Forms.DataGridViewRowCollection.GetRowCount%2A>utiliser la <xref:System.Windows.Forms.DataGridViewColumnCollection.GetColumnCount%2A> méthode, ou, en <xref:System.Windows.Forms.DataGridViewElementStates.Selected> passant la valeur.

> [!TIP]
> Vous trouverez un exemple de code illustrant l’utilisation par programmation des cellules sélectionnées <xref:System.Windows.Forms.DataGridView> dans la vue d’ensemble de la classe.

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.MultiSelect%2A>
- <xref:System.Windows.Forms.DataGridView.SelectionMode%2A>
- <xref:System.Windows.Forms.DataGridViewSelectionMode>
- [Sélection et utilisation du Presse-papiers avec le contrôle DataGridView Windows Forms](selection-and-clipboard-use-with-the-windows-forms-datagridview-control.md)
- [Guide pratique pour Définir le mode de sélection du contrôle DataGridView Windows Forms](how-to-set-the-selection-mode-of-the-windows-forms-datagridview-control.md)
