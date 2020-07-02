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
# <a name="how-to-get-and-set-the-current-cell-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="61c61-103">Comment : obtenir et définir la cellule active dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="61c61-103">How to: Get and Set the Current Cell in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="61c61-104">L’interaction avec <xref:System.Windows.Forms.DataGridView> vous oblige souvent à détecter par programmation la cellule actuellement active.</span><span class="sxs-lookup"><span data-stu-id="61c61-104">Interaction with the <xref:System.Windows.Forms.DataGridView> often requires that you programmatically discover which cell is currently active.</span></span> <span data-ttu-id="61c61-105">Vous devrez peut-être également modifier la cellule active.</span><span class="sxs-lookup"><span data-stu-id="61c61-105">You may also need to change the current cell.</span></span> <span data-ttu-id="61c61-106">Vous pouvez effectuer ces tâches avec la <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="61c61-106">You can perform these tasks with the <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> property.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="61c61-107">Vous ne pouvez pas définir la cellule active dans une ligne ou une colonne dont la propriété a la <xref:System.Windows.Forms.DataGridViewBand.Visible%2A> valeur `false` .</span><span class="sxs-lookup"><span data-stu-id="61c61-107">You cannot set the current cell in a row or column that has its <xref:System.Windows.Forms.DataGridViewBand.Visible%2A> property set to `false`.</span></span>  
  
 <span data-ttu-id="61c61-108">En fonction du <xref:System.Windows.Forms.DataGridView> mode de sélection du contrôle, la modification de la cellule active peut modifier la sélection.</span><span class="sxs-lookup"><span data-stu-id="61c61-108">Depending on the <xref:System.Windows.Forms.DataGridView> control's selection mode, changing the current cell can change the selection.</span></span> <span data-ttu-id="61c61-109">Pour plus d’informations, consultez [modes de sélection dans le contrôle DataGridView Windows Forms](selection-modes-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="61c61-109">For more information, see [Selection Modes in the Windows Forms DataGridView Control](selection-modes-in-the-windows-forms-datagridview-control.md).</span></span>  
  
### <a name="to-get-the-current-cell-programmatically"></a><span data-ttu-id="61c61-110">Pour récupérer la cellule active par programmation</span><span class="sxs-lookup"><span data-stu-id="61c61-110">To get the current cell programmatically</span></span>  
  
- <span data-ttu-id="61c61-111">Utilisez la <xref:System.Windows.Forms.DataGridView> propriété du contrôle <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> .</span><span class="sxs-lookup"><span data-stu-id="61c61-111">Use the <xref:System.Windows.Forms.DataGridView> control's <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> property.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#080](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#080)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#080](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#080)]  
  
### <a name="to-set-the-current-cell-programmatically"></a><span data-ttu-id="61c61-112">Pour définir la cellule active par programmation</span><span class="sxs-lookup"><span data-stu-id="61c61-112">To set the current cell programmatically</span></span>  
  
- <span data-ttu-id="61c61-113">Définissez la <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> propriété du <xref:System.Windows.Forms.DataGridView> contrôle.</span><span class="sxs-lookup"><span data-stu-id="61c61-113">Set the <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> property of the <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="61c61-114">Dans l’exemple de code suivant, la cellule active est définie sur la ligne 0, colonne 1.</span><span class="sxs-lookup"><span data-stu-id="61c61-114">In the following code example, the current cell is set to row 0, column 1.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#085](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#085)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#085](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#085)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="61c61-115">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="61c61-115">Compiling the Code</span></span>  
 <span data-ttu-id="61c61-116">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="61c61-116">This example requires:</span></span>  
  
- <span data-ttu-id="61c61-117"><xref:System.Windows.Forms.Button>contrôles nommés `getCurrentCellButton` et `setCurrentCellButton` .</span><span class="sxs-lookup"><span data-stu-id="61c61-117"><xref:System.Windows.Forms.Button> controls named `getCurrentCellButton` and `setCurrentCellButton`.</span></span> <span data-ttu-id="61c61-118">En Visual C#, vous devez joindre les <xref:System.Windows.Forms.Control.Click> événements pour chaque bouton au gestionnaire d’événements associé dans l’exemple de code.</span><span class="sxs-lookup"><span data-stu-id="61c61-118">In Visual C#, you must attach the <xref:System.Windows.Forms.Control.Click> events for each button to the associated event handler in the example code.</span></span>  
  
- <span data-ttu-id="61c61-119">un contrôle <xref:System.Windows.Forms.DataGridView> nommé `dataGridView1` ;</span><span class="sxs-lookup"><span data-stu-id="61c61-119">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
- <span data-ttu-id="61c61-120">des références aux assemblys <xref:System?displayProperty=nameWithType> et <xref:System.Windows.Forms?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="61c61-120">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61c61-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="61c61-121">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.CurrentCell%2A?displayProperty=nameWithType>
- [<span data-ttu-id="61c61-122">Fonctionnalités de base liées aux colonnes, lignes et cellules dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="61c61-122">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](basic-column-row-and-cell-features-wf-datagridview-control.md)
- [<span data-ttu-id="61c61-123">Modes de sélection dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="61c61-123">Selection Modes in the Windows Forms DataGridView Control</span></span>](selection-modes-in-the-windows-forms-datagridview-control.md)
