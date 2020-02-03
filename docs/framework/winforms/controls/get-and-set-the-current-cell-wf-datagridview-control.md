---
title: Obtient et définit la cellule active dans le contrôle DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], getting current cell
- DataGridView control [Windows Forms], setting current cell
- cells [Windows Forms], getting and setting current
ms.assetid: b0e41e57-493a-4bd0-9376-a6f76723540c
ms.openlocfilehash: 0fb01d5392e02b53e0e5bf905c872dbeeb22fad9
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745663"
---
# <a name="how-to-get-and-set-the-current-cell-in-the-windows-forms-datagridview-control"></a>Comment : obtenir et définir la cellule active dans le contrôle DataGridView Windows Forms
L’interaction avec le <xref:System.Windows.Forms.DataGridView> nécessite souvent de découvrir par programmation la cellule actuellement active. Vous devrez peut-être également modifier la cellule active. Vous pouvez effectuer ces tâches avec la propriété <xref:System.Windows.Forms.DataGridView.CurrentCell%2A>.  
  
> [!NOTE]
> Vous ne pouvez pas définir la cellule active dans une ligne ou une colonne dont la propriété <xref:System.Windows.Forms.DataGridViewBand.Visible%2A> a la valeur `false`.  
  
 Selon le mode de sélection du contrôle <xref:System.Windows.Forms.DataGridView>, la modification de la cellule active peut modifier la sélection. Pour plus d’informations, consultez [modes de sélection dans le contrôle DataGridView Windows Forms](selection-modes-in-the-windows-forms-datagridview-control.md).  
  
### <a name="to-get-the-current-cell-programmatically"></a>Pour récupérer la cellule active par programmation  
  
- Utilisez la propriété <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> du contrôle <xref:System.Windows.Forms.DataGridView>.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#080](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#080)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#080](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#080)]  
  
### <a name="to-set-the-current-cell-programmatically"></a>Pour définir la cellule active par programmation  
  
- Définissez la propriété <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> du contrôle <xref:System.Windows.Forms.DataGridView>. Dans l’exemple de code suivant, la cellule active est définie sur la ligne 0, colonne 1.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#085](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#085)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#085](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#085)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Cet exemple nécessite :  
  
- <xref:System.Windows.Forms.Button> contrôles nommés `getCurrentCellButton` et `setCurrentCellButton`. En Visual C#, vous devez joindre les événements <xref:System.Windows.Forms.Control.Click> pour chaque bouton au gestionnaire d’événements associé dans l’exemple de code.  
  
- un contrôle <xref:System.Windows.Forms.DataGridView> nommé `dataGridView1` ;  
  
- des références aux assemblys <xref:System?displayProperty=nameWithType> et <xref:System.Windows.Forms?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.CurrentCell%2A?displayProperty=nameWithType>
- [Fonctionnalités de base liées aux colonnes, lignes et cellules dans le contrôle DataGridView Windows Forms](basic-column-row-and-cell-features-wf-datagridview-control.md)
- [Modes de sélection dans le contrôle DataGridView Windows Forms](selection-modes-in-the-windows-forms-datagridview-control.md)
