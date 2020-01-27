---
title: Gestion par défaut du clavier et de la souris dans le contrôle DataGridView
ms.date: 02/13/2018
helpviewer_keywords:
- data grids [Windows Forms], mouse handling
- DataGridView control [Windows Forms], navigation keys
- keyboards [Windows Forms], default handling in DataGridView control
- DataGridView control [Windows Forms], keyboard handling
- mouse [Windows Forms], default handling in DataGridView control
- DataGridView control [Windows Forms], mouse handling
- navigation keys [Windows Forms], DataGridView control
ms.assetid: 4519b928-bfc8-4e8b-bb9c-b1e76a0ca552
ms.openlocfilehash: 36defff02450b40265c9b6801380cab78eabe5f3
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746117"
---
# <a name="default-keyboard-and-mouse-handling-in-the-windows-forms-datagridview-control"></a>Gestion par défaut du clavier et de la souris dans le contrôle DataGridView Windows Forms

Les tableaux suivants décrivent la manière dont les utilisateurs peuvent interagir avec le contrôle <xref:System.Windows.Forms.DataGridView> par le biais d’un clavier et d’une souris.  
  
> [!NOTE]
> Pour personnaliser le comportement du clavier, vous pouvez gérer les événements de clavier standard, tels que les <xref:System.Windows.Forms.Control.KeyDown>. Toutefois, en mode édition, le contrôle d’édition hébergé reçoit l’entrée au clavier et les événements de clavier ne se produisent pas pour le contrôle <xref:System.Windows.Forms.DataGridView>. Pour gérer les événements de contrôle d’édition, attachez vos gestionnaires au contrôle d’édition dans un gestionnaire d’événements <xref:System.Windows.Forms.DataGridView.EditingControlShowing>. Vous pouvez également personnaliser le comportement du clavier dans une sous-classe <xref:System.Windows.Forms.DataGridView> en remplaçant les méthodes <xref:System.Windows.Forms.DataGridView.ProcessDialogKey%2A> et <xref:System.Windows.Forms.DataGridView.ProcessDataGridViewKey%2A>.  
  
## <a name="default-keyboard-handling"></a>Gestion du clavier par défaut  
  
### <a name="basic-navigation-and-entry-keys"></a>Touches de navigation et de saisie de base  
  
|Touche ou combinaison de touches|Description|  
|----------------------------|-----------------|  
|BAS|Déplace le focus vers la cellule située juste en dessous de la cellule active. Si le focus se trouve sur la dernière ligne, ne fait rien.|  
|GAUCHE|Déplace le focus vers la cellule précédente dans la ligne. Si le focus se trouve dans la première cellule de la ligne, ne fait rien.|  
|Droite|Déplace le focus vers la cellule suivante dans la ligne. Si le focus se trouve dans la dernière cellule de la ligne, ne fait rien.|  
|Haut|Déplace le focus vers la cellule située juste au-dessus de la cellule active. Si le focus se trouve sur la première ligne, ne fait rien.|  
|Début|Déplace le focus vers la première cellule de la ligne actuelle.|  
|Fin|Déplace le focus vers la dernière cellule de la ligne actuelle.|  
|PAGE SUIVANTE|Fait défiler le contrôle vers le bas du nombre de lignes entièrement affichées. Déplace le focus vers la dernière ligne entièrement affichée sans modifier les colonnes.|  
|PAGE PRÉCÉDENTE|Fait défiler le contrôle vers le haut selon le nombre de lignes entièrement affichées. Déplace le focus sur la première ligne affichée sans modifier les colonnes.|  
|TAB|Si la valeur de la propriété <xref:System.Windows.Forms.DataGridView.StandardTab%2A> est `false`, déplace le focus vers la cellule suivante dans la ligne actuelle. Si le focus se trouve déjà dans la dernière cellule de la ligne, déplace le focus vers la première cellule de la ligne suivante. Si le focus se trouve dans la dernière cellule du contrôle, déplace le focus vers le contrôle suivant dans l’ordre de tabulation du conteneur parent.<br /><br /> Si la valeur de la propriété <xref:System.Windows.Forms.DataGridView.StandardTab%2A> est `true`, déplace le focus vers le contrôle suivant dans l’ordre de tabulation du conteneur parent.|  
|MAJ+TAB|Si la valeur de la propriété <xref:System.Windows.Forms.DataGridView.StandardTab%2A> est `false`, déplace le focus vers la cellule précédente dans la ligne actuelle. Si le focus se trouve déjà dans la première cellule de la ligne, déplace le focus vers la dernière cellule de la ligne précédente. Si le focus se trouve dans la première cellule du contrôle, déplace le focus vers le contrôle précédent dans l’ordre de tabulation du conteneur parent.<br /><br /> Si la valeur de la propriété <xref:System.Windows.Forms.DataGridView.StandardTab%2A> est `true`, déplace le focus sur le contrôle précédent dans l’ordre de tabulation du conteneur parent.|  
|CTRL + TAB|Si la valeur de la propriété <xref:System.Windows.Forms.DataGridView.StandardTab%2A> est `false`, déplace le focus vers le contrôle suivant dans l’ordre de tabulation du conteneur parent.<br /><br /> Si la valeur de la propriété <xref:System.Windows.Forms.DataGridView.StandardTab%2A> est `true`, déplace le focus vers la cellule suivante dans la ligne actuelle. Si le focus se trouve déjà dans la dernière cellule de la ligne, déplace le focus vers la première cellule de la ligne suivante. Si le focus se trouve dans la dernière cellule du contrôle, déplace le focus vers le contrôle suivant dans l’ordre de tabulation du conteneur parent.|  
|CTRL+MAJ+TAB|Si la valeur de la propriété <xref:System.Windows.Forms.DataGridView.StandardTab%2A> est `false`, déplace le focus sur le contrôle précédent dans l’ordre de tabulation du conteneur parent.<br /><br /> Si la valeur de la propriété <xref:System.Windows.Forms.DataGridView.StandardTab%2A> est `true`, déplace le focus vers la cellule précédente dans la ligne actuelle. Si le focus se trouve déjà dans la première cellule de la ligne, déplace le focus vers la dernière cellule de la ligne précédente. Si le focus se trouve dans la première cellule du contrôle, déplace le focus vers le contrôle précédent dans l’ordre de tabulation du conteneur parent.|  
|CTRL + Flèche|Déplace le focus vers la cellule la plus éloignée dans le sens de la flèche.|  
|Ctrl+Origine|Déplace le focus vers la première cellule du contrôle.|  
|CTRL+FIN|Déplace le focus vers la dernière cellule du contrôle.|  
|CTRL + PG. SUIV/HAUT|Identique à PAGE suivante ou PAGE précédente.|  
|F2|Met la cellule active en mode édition de cellule si la valeur de la propriété <xref:System.Windows.Forms.DataGridView.EditMode%2A> est <xref:System.Windows.Forms.DataGridViewEditMode.EditOnF2> ou <xref:System.Windows.Forms.DataGridViewEditMode.EditOnKeystrokeOrF2>.|
|F3|Trie la colonne actuelle si la valeur de la propriété <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType> est <xref:System.Windows.Forms.DataGridViewColumnSortMode.Automatic>. Cela revient à cliquer sur l’en-tête de colonne actuel. Disponible depuis .NET Framework 4.7.2. Pour activer cette fonctionnalité, les applications doivent cibler .NET Framework 4.7.2 ou versions ultérieures, ou opter explicitement pour les améliorations de l’accessibilité à l’aide de commutateurs AppContext.|  
|F4|Si la cellule active est un <xref:System.Windows.Forms.DataGridViewComboBoxCell>, place la cellule en mode édition et affiche la liste déroulante.|  
|ALT + FLÈCHE HAUT/BAS|Si la cellule active est un <xref:System.Windows.Forms.DataGridViewComboBoxCell>, place la cellule en mode édition et affiche la liste déroulante.|  
|ESPACE|Si la cellule active est un <xref:System.Windows.Forms.DataGridViewButtonCell>, <xref:System.Windows.Forms.DataGridViewLinkCell>ou <xref:System.Windows.Forms.DataGridViewCheckBoxCell>, déclenche les événements <xref:System.Windows.Forms.DataGridView.CellClick> et <xref:System.Windows.Forms.DataGridView.CellContentClick>. Si la cellule active est un <xref:System.Windows.Forms.DataGridViewButtonCell>, appuie également sur le bouton. Si la cellule active est un <xref:System.Windows.Forms.DataGridViewCheckBoxCell>, modifie également l’état d’activation.|  
|ENTRÉE|Valide toutes les modifications apportées à la cellule et à la ligne actuelles et déplace le focus vers la cellule située juste en dessous de la cellule active. Si le focus se trouve sur la dernière ligne, valide toutes les modifications sans déplacer le focus.|  
|ÉCHAP|Si le contrôle est en mode édition, annule la modification. Si le contrôle n’est pas en mode édition, rétablit toutes les modifications apportées à la ligne actuelle si le contrôle est lié à une source de données qui prend en charge l’édition ou le mode virtuel a été implémenté avec la portée de validation au niveau des lignes.|  
|Ret.arr|Supprime le caractère avant le point d’insertion lors de la modification d’une cellule.|  
|SUPPR|Supprime le caractère après le point d’insertion lors de la modification d’une cellule.|  
|CTRL+ENTRÉE|Valide toutes les modifications apportées à la cellule active sans déplacer le focus. Valide également toutes les modifications apportées à la ligne actuelle si le contrôle est lié à une source de données qui prend en charge la modification ou le mode virtuel a été implémenté avec la portée de validation au niveau des lignes.|  
|CTRL+0|Entre une <xref:System.DBNull.Value?displayProperty=nameWithType> valeur dans la cellule active si la cellule peut être modifiée. Par défaut, la valeur d’affichage d’une <xref:System.DBNull> valeur de cellule est la valeur de la propriété <xref:System.Windows.Forms.DataGridViewCellStyle.NullValue%2A> du <xref:System.Windows.Forms.DataGridViewCellStyle> en vigueur pour la cellule active.|  
  
### <a name="selection-keys"></a>Clés de sélection

 Si la propriété <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> est définie sur `false` et que la propriété <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> est définie sur <xref:System.Windows.Forms.DataGridViewSelectionMode.CellSelect>, la modification de la cellule active à l’aide des touches de navigation remplace la sélection par la nouvelle cellule. Les touches Maj, CTRL et ALT n’affectent pas ce comportement.  
  
 Si la <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> est définie sur <xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect> ou <xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>, le même comportement se produit, mais avec les ajouts suivants.  
  
|Touche ou combinaison de touches|Description|  
|----------------------------|-----------------|  
|Maj + barre d’espace|Sélectionne la ligne ou la colonne complète (comme si vous cliquiez sur l’en-tête de ligne ou de colonne).|  
|touche de navigation (touche de direction, PAGE vers le haut/bas, début, fin)|Si une ligne ou une colonne complète est sélectionnée, la modification de la cellule active en une nouvelle ligne ou colonne déplace la sélection vers la nouvelle ligne ou colonne complète (en fonction du mode de sélection).|  
  
 Si <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> a la valeur `false` et <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> a la valeur <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect> ou <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect>, la modification de la cellule active en une nouvelle ligne ou colonne à l’aide du clavier déplace la sélection vers la nouvelle ligne ou colonne complète. Les touches Maj, CTRL et ALT n’affectent pas ce comportement.  
  
 Si <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> a la valeur `true`, le comportement de navigation ne change pas, mais la navigation avec le clavier tout en appuyant sur Maj (y compris CTRL + MAJ) modifie une sélection de plusieurs cellules. Avant le début de la navigation, le contrôle marque la cellule active comme une cellule d’ancrage. Lorsque vous appuyez sur la touche Maj, la sélection comprend toutes les cellules entre la cellule d’ancrage et la cellule active. Les autres cellules du contrôle restent sélectionnées si elles étaient déjà sélectionnées, mais elles peuvent être désélectionnées si la navigation au clavier les place temporairement entre la cellule d’ancrage et la cellule active.  
  
 Si <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> a la valeur `true` et <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> a la valeur <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect> ou <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect>, le comportement de la cellule d’ancrage et de la cellule active est le même, mais seules les lignes ou colonnes complètes sont sélectionnées ou désélectionnées.  
  
## <a name="default-mouse-handling"></a>Gestion de la souris par défaut
  
### <a name="basic-mouse-handling"></a>Gestion de la souris de base
  
> [!NOTE]
> Le fait de cliquer sur une cellule avec le bouton gauche de la souris modifie toujours la cellule active. Cliquez sur une cellule avec le bouton droit de la souris pour ouvrir un menu contextuel, le cas échéant.  
  
|Action de la souris|Description|  
|------------------|-----------------|  
|Bouton gauche de la souris enfoncé|Fait de la cellule sur laquelle l’utilisateur clique la cellule active et déclenche l’événement <xref:System.Windows.Forms.DataGridView.CellMouseDown?displayProperty=nameWithType>.|  
|Bouton gauche de la souris vers le haut|Déclenche l'événement <xref:System.Windows.Forms.DataGridView.CellMouseUp?displayProperty=nameWithType>.|  
|Clic avec le bouton gauche de la souris|Déclenche les événements <xref:System.Windows.Forms.DataGridView.CellClick?displayProperty=nameWithType> et <xref:System.Windows.Forms.DataGridView.CellMouseClick?displayProperty=nameWithType>|  
|Bouton gauche de la souris enfoncé, puis faites glisser sur une cellule d’en-tête de colonne|Si la propriété <xref:System.Windows.Forms.DataGridView.AllowUserToOrderColumns%2A?displayProperty=nameWithType> est `true`, déplace la colonne afin qu’elle puisse être déplacée vers une nouvelle position.|  
  
### <a name="mouse-selection"></a>Sélection de la souris

 Aucun comportement de sélection n’est associé au bouton central de la souris ou à la roulette de la souris.  
  
 Si la propriété <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> est définie sur `false` et que la propriété <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> est définie sur <xref:System.Windows.Forms.DataGridViewSelectionMode.CellSelect>, le comportement suivant se produit.  
  
|Action de la souris|Description|  
|------------------|-----------------|  
|Cliquer sur le bouton gauche de la souris|Sélectionne uniquement la cellule active si l’utilisateur clique sur une cellule. Aucun comportement de sélection si l’utilisateur clique sur un en-tête de ligne ou de colonne.|  
|Cliquer sur le bouton droit de la souris|Affiche un menu contextuel s’il en existe un.|  
  
 Le même comportement se produit lorsque le <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> est défini sur <xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect> ou <xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>, sauf que, en fonction du mode de sélection, le fait de cliquer sur une ligne ou un en-tête de colonne sélectionne la ligne ou la colonne complète et définit la cellule active sur la première cellule de la ligne ou de la colonne.  
  
 Si <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> a la valeur <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect> ou <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect>, le fait de cliquer sur une cellule d’une ligne ou d’une colonne sélectionne la ligne ou la colonne complète.  
  
 Si <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> est défini sur `true`, le fait de cliquer sur une cellule tout en appuyant sur CTRL ou Maj modifie une sélection de plusieurs cellules.  
  
 Lorsque vous cliquez sur une cellule tout en appuyant sur CTRL, la cellule change d’état de sélection tandis que toutes les autres cellules conservent leur état de sélection actuel.  
  
 Lorsque vous cliquez sur une cellule ou une série de cellules tout en appuyant sur Maj, la sélection comprend toutes les cellules entre la cellule active et une cellule d’ancrage située à la position de la cellule active avant le premier clic. Lorsque vous cliquez et faites glisser le pointeur sur plusieurs cellules, la cellule d’ancrage est la cellule sur laquelle l’utilisateur clique au début de l’opération glisser. Les clics suivants tout en appuyant sur Maj modifient la cellule active, mais pas la cellule d’ancrage. Les autres cellules du contrôle restent sélectionnées si elles étaient déjà sélectionnées, mais elles peuvent être désélectionnées si la navigation de la souris les place temporairement entre la cellule d’ancrage et la cellule active.  
  
 Si <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> a la valeur `true` et <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> a la valeur <xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect> ou <xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>, le fait de cliquer sur un en-tête de ligne ou de colonne (selon le mode de sélection) tout en appuyant sur Maj modifie une sélection existante de lignes ou de colonnes complètes si une telle sélection existe. Sinon, elle efface la sélection et démarre une nouvelle sélection de lignes ou de colonnes entières. En cliquant sur un en-tête de ligne ou de colonne tout en appuyant sur CTRL, vous ajoutez ou supprimez la ligne ou la colonne sur laquelle l’utilisateur a cliqué dans la sélection actuelle sans modifier la sélection actuelle.  
  
 Si <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> a la valeur `true` et <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> a la valeur <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect> ou <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect>, le fait de cliquer sur une cellule tout en appuyant sur Maj ou CTRL se comporte de la même façon, sauf que seules les lignes et les colonnes complètes sont affectées.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.DataGridView>
- [DataGridView, contrôle](datagridview-control-windows-forms.md)
