---
title: Personnaliser le contrôle DataGridView
ms.date: 03/30/2017
helpviewer_keywords:
- data grids [Windows Forms], customization
- DataGridView control [Windows Forms], customization
ms.assetid: 01ea5d4c-a736-4596-b0e9-a67a1b86e15f
ms.openlocfilehash: 348c78d091679418f2452326555d49229bd2a8ea
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744025"
---
# <a name="customizing-the-windows-forms-datagridview-control"></a>Personnalisation du contrôle DataGridView Windows Forms
Le contrôle `DataGridView` fournit plusieurs propriétés que vous pouvez utiliser pour ajuster l’apparence et le comportement de base (apparence) de ses cellules, lignes et colonnes. Toutefois, si vous avez des besoins spécifiques qui vont au-delà des capacités de la classe <xref:System.Windows.Forms.DataGridViewCellStyle>, vous pouvez également implémenter le dessin owner-drawn pour le contrôle ou étendre ses fonctionnalités en créant des cellules, des colonnes et des lignes personnalisées.  
  
 Pour peindre vous-même des cellules et des lignes, vous pouvez gérer plusieurs événements de dessin `DataGridView`. Pour modifier des fonctionnalités existantes ou fournir de nouvelles fonctionnalités, vous pouvez créer vos propres types dérivés des types `DataGridViewCell`, `DataGridViewColumn`et `DataGridViewRow` existants. Vous pouvez également fournir de nouvelles fonctionnalités de modification en créant des types dérivés qui affichent un contrôle de votre choix lorsqu’une cellule est en mode édition.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Guide pratique pour personnaliser l’apparence des cellules du contrôle DataGridView Windows Forms](customize-the-appearance-of-cells-in-the-datagrid.md)  
 Décrit comment gérer l’événement <xref:System.Windows.Forms.DataGridView.CellPainting> pour peindre des cellules manuellement.  
  
 [Guide pratique pour personnaliser l’apparence des lignes du contrôle DataGridView Windows Forms](customize-the-appearance-of-rows-in-the-datagrid.md)  
 Décrit comment gérer les événements <xref:System.Windows.Forms.DataGridView.RowPrePaint> et <xref:System.Windows.Forms.DataGridView.RowPostPaint> pour peindre des lignes avec un arrière-plan dégradé personnalisé et un contenu qui s’étend sur plusieurs colonnes.  
  
 [Guide pratique pour personnaliser les cellules et les colonnes du contrôle DataGridView Windows Forms en étendant leur comportement et leur apparence](customize-cells-and-columns-in-the-datagrid-by-extending-behavior.md)  
 Décrit comment créer des types personnalisés dérivés de `DataGridViewCell` et `DataGridViewColumn` afin de mettre en surbrillance des cellules lorsque le pointeur de la souris se trouve sur ceux-ci.  
  
 [Guide pratique pour désactiver des boutons d'une colonne de boutons dans le contrôle DataGridView Windows Forms](disable-buttons-in-a-button-column-in-the-datagrid.md)  
 Décrit comment créer des types personnalisés dérivés de <xref:System.Windows.Forms.DataGridViewButtonCell> et <xref:System.Windows.Forms.DataGridViewButtonColumn> afin d’afficher les boutons désactivés dans une colonne de bouton.  
  
 [Guide pratique pour héberger des contrôles dans des cellules DataGridView Windows Forms](how-to-host-controls-in-windows-forms-datagridview-cells.md)  
 Décrit comment implémenter l’interface `IDataGridViewEditingControl` et créer des types personnalisés dérivés de `DataGridViewCell` et `DataGridViewColumn` afin d’afficher un contrôle <xref:System.Windows.Forms.DateTimePicker> quand une cellule est en mode édition.  
  
## <a name="reference"></a>Reference  
 <xref:System.Windows.Forms.DataGridView>  
 Fournit une documentation de référence pour le contrôle <xref:System.Windows.Forms.DataGridView>.  
  
 <xref:System.Windows.Forms.DataGridViewCell>  
 Fournit une documentation de référence pour la classe <xref:System.Windows.Forms.DataGridViewCell>.  
  
 <xref:System.Windows.Forms.DataGridViewRow>  
 Fournit une documentation de référence pour la classe <xref:System.Windows.Forms.DataGridViewRow>.  
  
 <xref:System.Windows.Forms.DataGridViewColumn>  
 Fournit une documentation de référence pour la classe <xref:System.Windows.Forms.DataGridViewColumn>.  
  
 <xref:System.Windows.Forms.IDataGridViewEditingControl>  
 Fournit une documentation de référence pour l’interface <xref:System.Windows.Forms.IDataGridViewEditingControl>.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Mises en forme et styles de base dans le contrôle DataGridView Windows Forms](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)  
 Fournit des rubriques qui décrivent comment modifier l'apparence de base du contrôle et le format d'affichage des données de cellules.  
  
## <a name="see-also"></a>Voir aussi

- [DataGridView, contrôle](datagridview-control-windows-forms.md)
- [Types de colonnes dans le contrôle DataGridView Windows Forms](column-types-in-the-windows-forms-datagridview-control.md)
