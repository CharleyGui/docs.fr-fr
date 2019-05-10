---
title: 'Procédure : définir le mode de sélection du contrôle DataGridView Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- selection [Windows Forms], modes in DataGridView control
- DataGridView control [Windows Forms], selection mode
- data grids [Windows Forms], selection mode
ms.assetid: 2f241643-7f82-4583-8757-03494f63b465
ms.openlocfilehash: 22db5c1438405fc830202ec7baac6b6fcd631b41
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64620800"
---
# <a name="how-to-set-the-selection-mode-of-the-windows-forms-datagridview-control"></a><span data-ttu-id="7a0c3-102">Procédure : définir le mode de sélection du contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7a0c3-102">How to: Set the Selection Mode of the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="7a0c3-103">L’exemple de code suivant montre comment configurer un <xref:System.Windows.Forms.DataGridView> contrôle afin qu’automatiquement de cliquer n’importe où dans une ligne sélectionne la ligne entière, et par conséquent, ce qu’une seule ligne à la fois peut être sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="7a0c3-103">The following code example demonstrates how to configure a <xref:System.Windows.Forms.DataGridView> control so that clicking anywhere within a row automatically selects the entire row, and so that only one row at a time can be selected.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7a0c3-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="7a0c3-104">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#065](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#065)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#065](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#065)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="7a0c3-105">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="7a0c3-105">Compiling the Code</span></span>  
 <span data-ttu-id="7a0c3-106">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="7a0c3-106">This example requires:</span></span>  
  
- <span data-ttu-id="7a0c3-107">un contrôle <xref:System.Windows.Forms.DataGridView> nommé `dataGridView1` ;</span><span class="sxs-lookup"><span data-stu-id="7a0c3-107">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
- <span data-ttu-id="7a0c3-108">des références aux assemblys <xref:System?displayProperty=nameWithType> et <xref:System.Windows.Forms?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="7a0c3-108">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a0c3-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7a0c3-109">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.MultiSelect%2A>
- <xref:System.Windows.Forms.DataGridView.SelectionMode%2A>
- <xref:System.Windows.Forms.DataGridViewSelectionMode>
- [<span data-ttu-id="7a0c3-110">Sélection et utilisation du Presse-papiers avec le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7a0c3-110">Selection and Clipboard Use with the Windows Forms DataGridView Control</span></span>](selection-and-clipboard-use-with-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="7a0c3-111">Modes de sélection dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7a0c3-111">Selection Modes in the Windows Forms DataGridView Control</span></span>](selection-modes-in-the-windows-forms-datagridview-control.md)
