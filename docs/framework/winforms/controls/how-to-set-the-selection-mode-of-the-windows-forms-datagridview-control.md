---
title: Définir le mode de sélection du contrôle DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- selection [Windows Forms], modes in DataGridView control
- DataGridView control [Windows Forms], selection mode
- data grids [Windows Forms], selection mode
ms.assetid: 2f241643-7f82-4583-8757-03494f63b465
ms.openlocfilehash: da866aac3ac5b08a06ec71744aadb4260bd0cfc4
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743504"
---
# <a name="how-to-set-the-selection-mode-of-the-windows-forms-datagridview-control"></a>Comment : définir le mode de sélection du contrôle DataGridView Windows Forms
L’exemple de code suivant montre comment configurer un contrôle <xref:System.Windows.Forms.DataGridView> afin que le fait de cliquer n’importe où dans une ligne sélectionne automatiquement la ligne entière, et de sorte qu’une seule ligne à la fois peut être sélectionnée.  
  
## <a name="example"></a>Exemple  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#065](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#065)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#065](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#065)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Cet exemple nécessite :  
  
- un contrôle <xref:System.Windows.Forms.DataGridView> nommé `dataGridView1` ;  
  
- des références aux assemblys <xref:System?displayProperty=nameWithType> et <xref:System.Windows.Forms?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.MultiSelect%2A>
- <xref:System.Windows.Forms.DataGridView.SelectionMode%2A>
- <xref:System.Windows.Forms.DataGridViewSelectionMode>
- [Sélection et utilisation du Presse-papiers avec le contrôle DataGridView Windows Forms](selection-and-clipboard-use-with-the-windows-forms-datagridview-control.md)
- [Modes de sélection dans le contrôle DataGridView Windows Forms](selection-modes-in-the-windows-forms-datagridview-control.md)
