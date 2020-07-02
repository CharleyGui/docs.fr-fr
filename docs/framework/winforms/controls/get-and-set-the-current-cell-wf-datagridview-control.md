---
title: Obtient et définit la cellule active dans le contrôle DataGridView
description: Découvrez comment découvrir par programmation la cellule actuellement active en obtenant et en définissant la cellule active dans le contrôle DataGridView Windows Forms.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], getting current cell
- DataGridView control [Windows Forms], setting current cell
- cells [Windows Forms], getting and setting current
ms.assetid: b0e41e57-493a-4bd0-9376-a6f76723540c
ms.openlocfilehash: 1651ca9c8fa0329f9435a70ce777bce68f15ff63
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622209"
---
# <a name="how-to-get-and-set-the-current-cell-in-the-windows-forms-datagridview-control"></a>Comment : obtenir et définir la cellule active dans le contrôle DataGridView Windows Forms
L’interaction avec <xref:System.Windows.Forms.DataGridView> vous oblige souvent à détecter par programmation la cellule actuellement active. Vous devrez peut-être également modifier la cellule active. Vous pouvez effectuer ces tâches avec la <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> propriété.  
  
> [!NOTE]
> Vous ne pouvez pas définir la cellule active dans une ligne ou une colonne dont la propriété a la <xref:System.Windows.Forms.DataGridViewBand.Visible%2A> valeur `false` .  
  
 En fonction du <xref:System.Windows.Forms.DataGridView> mode de sélection du contrôle, la modification de la cellule active peut modifier la sélection. Pour plus d’informations, consultez [modes de sélection dans le contrôle DataGridView Windows Forms](selection-modes-in-the-windows-forms-datagridview-control.md).  
  
### <a name="to-get-the-current-cell-programmatically"></a>Pour récupérer la cellule active par programmation  
  
- Utilisez la <xref:System.Windows.Forms.DataGridView> propriété du contrôle <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> .  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#080](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#080)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#080](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#080)]  
  
### <a name="to-set-the-current-cell-programmatically"></a>Pour définir la cellule active par programmation  
  
- Définissez la <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> propriété du <xref:System.Windows.Forms.DataGridView> contrôle. Dans l’exemple de code suivant, la cellule active est définie sur la ligne 0, colonne 1.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#085](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#085)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#085](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#085)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Cet exemple nécessite :  
  
- <xref:System.Windows.Forms.Button>contrôles nommés `getCurrentCellButton` et `setCurrentCellButton` . En Visual C#, vous devez joindre les <xref:System.Windows.Forms.Control.Click> événements pour chaque bouton au gestionnaire d’événements associé dans l’exemple de code.  
  
- un contrôle <xref:System.Windows.Forms.DataGridView> nommé `dataGridView1` ;  
  
- des références aux assemblys <xref:System?displayProperty=nameWithType> et <xref:System.Windows.Forms?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.CurrentCell%2A?displayProperty=nameWithType>
- [Fonctionnalités de base liées aux colonnes, lignes et cellules dans le contrôle DataGridView Windows Forms](basic-column-row-and-cell-features-wf-datagridview-control.md)
- [Modes de sélection dans le contrôle DataGridView Windows Forms](selection-modes-in-the-windows-forms-datagridview-control.md)
