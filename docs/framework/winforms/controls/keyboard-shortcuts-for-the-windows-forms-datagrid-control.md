---
title: Raccourcis clavier pour le contrôle DataGrid
ms.date: 03/30/2017
helpviewer_keywords:
- keyboard shortcuts [Windows Forms], DataGrid control
- DataGrid control [Windows Forms], navigation keys
ms.assetid: a01780f9-20d5-4f5f-808f-c790c9a007a5
ms.openlocfilehash: 6693531b8d0e820a68d75bf5da40f4169fd244f2
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745037"
---
# <a name="keyboard-shortcuts-for-the-windows-forms-datagrid-control"></a>Raccourcis clavier du contrôle DataGrid Windows Forms
> [!NOTE]
> Le contrôle <xref:System.Windows.Forms.DataGridView> remplace le contrôle <xref:System.Windows.Forms.DataGrid> et lui ajoute des fonctionnalités ; toutefois, le contrôle <xref:System.Windows.Forms.DataGrid> est conservé pour la compatibilité descendante et l'utilisation future si tel est votre choix. Pour plus d’informations, consultez [Différences entre les contrôles DataGridView et DataGrid Windows Forms](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Le tableau suivant répertorie les raccourcis clavier qui peuvent être utilisés pour la navigation au sein du contrôle Windows Forms <xref:System.Windows.Forms.DataGrid> :  
  
|Action|Raccourci|  
|------------|--------------|  
|Complétez une entrée de cellule et descendez jusqu’à la cellule suivante.<br /><br /> Si le focus est sur un lien de table enfant, accédez à cette table.|ENTRÉE|  
|Annule la modification de cellule en mode édition de cellule.<br /><br /> Si vous sélectionnez une sélection dans le texte défilant, annulez la modification sur la ligne.|ÉCHAP|  
|Supprimer le caractère avant le point d’insertion lors de la modification d’une cellule.|Ret.arr|  
|Supprimer le caractère après le point d’insertion lors de la modification d’une cellule.|SUPPR|  
|Permet de passer à la première cellule de la ligne actuelle.|Début|  
|Déplacer vers la dernière cellule de la ligne actuelle.|Fin|  
|Mettre en surbrillance les caractères dans la cellule active et placer le point d’insertion à la fin de la ligne. Même comportement que le double-clic sur une cellule.|F2|  
|Si le focus se trouve sur une cellule, passez à la cellule suivante dans la ligne.<br /><br /> Si le focus se trouve sur la dernière cellule d’une ligne, accédez au premier lien de la table enfant de la ligne et développez-le.<br /><br /> Si le focus est sur un lien enfant, passer au lien enfant suivant.<br /><br /> Si le focus se trouve sur le dernier lien enfant, déplacez-vous vers la première cellule de la ligne suivante.|TAB|  
|Si le focus se trouve sur une cellule, passez à la cellule précédente dans la ligne.<br /><br /> Si le focus se trouve sur la première cellule d’une ligne, accédez au dernier lien de la table enfant développée de la ligne précédente ou à la dernière cellule de la ligne précédente.<br /><br /> Si le focus est sur un lien enfant, accédez au lien enfant précédent.<br /><br /> Si le focus se trouve sur le premier lien enfant, déplacez-vous vers la dernière cellule de la ligne précédente.|MAJ+TAB|  
|Accéder au contrôle suivant dans l’ordre de tabulation.|CTRL + TAB|  
|Accédez au contrôle précédent dans l’ordre de tabulation.|CTRL+MAJ+TAB|  
|Déplacer vers le haut jusqu’à la table parente dans une table enfant. Même comportement que lorsque vous cliquez sur le bouton précédent.|ALT + FLÈCHE GAUCHE|  
|Développez liens de la table enfant. ALT + flèche bas développe tous les liens, pas seulement ceux qui sont sélectionnés.|ALT + flèche bas ou CTRL + SIGNE PLUS|  
|Réduit les liens de la table enfant. ALT + flèche haut réduit tous les liens, pas seulement ceux sélectionnés.|ALT + flèche haut ou CTRL + signe moins|  
|Permet de passer à la cellule non vide la plus éloignée dans le sens de la flèche.|CTRL + Flèche|  
|Étendre la sélection d’une ligne dans le sens de la flèche (à l’exception des liens de la table enfant).|MAJ + FLÈCHE VERS LE HAUT/BAS|  
|Étend la sélection à la ligne non vide la plus lointaine dans le sens de la flèche (à l’exception des liens de la table enfant).|CTRL + MAJ + FLÈCHE HAUT/BAS|  
|Déplacer vers la cellule supérieure gauche.|Ctrl+Origine|  
|Déplacer vers la cellule inférieure droite.|CTRL+FIN|  
|Étendre la sélection à la ligne supérieure.|CTRL + MAJ + début|  
|Étendre la sélection à la ligne inférieure.|CTRL+MAJ+FIN|  
|Sélectionnez la ligne actuelle (à l’exception des liens de la table enfant).|Maj + barre d’espace|  
|Sélectionnez l’intégralité de la grille (à l’exception des liens de la table enfant).|CTRL+A|  
|Affiche la ligne parente dans une table enfant.|CTRL+PAGE SUIVANTE|  
|Masquer la ligne parente dans une table enfant.|CTRL+PG.PRÉC|  
|Étend la sélection d’un écran vers le dessous (à l’exception des liens de la table enfant).|MAJ+PG.SUIV|  
|Étendre la sélection d’un écran vers le haut (à l’exception des liens de la table enfant).|MAJ+PG.PRÉC|  
|Appelez la méthode <xref:System.Windows.Forms.DataGrid.EndEdit%2A> pour la ligne actuelle.|CTRL+ENTRÉE|  
|Entrez une valeur de <xref:System.DBNull.Value?displayProperty=nameWithType> dans une cellule en mode édition.|CTRL+0|  
  
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble du contrôle DataGrid](datagrid-control-overview-windows-forms.md)
- [DataGrid, contrôle](datagrid-control-windows-forms.md)
