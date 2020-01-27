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
# <a name="how-to-get-and-set-the-current-cell-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="8ed42-102">Comment : obtenir et définir la cellule active dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8ed42-102">How to: Get and Set the Current Cell in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="8ed42-103">L’interaction avec le <xref:System.Windows.Forms.DataGridView> nécessite souvent de découvrir par programmation la cellule actuellement active.</span><span class="sxs-lookup"><span data-stu-id="8ed42-103">Interaction with the <xref:System.Windows.Forms.DataGridView> often requires that you programmatically discover which cell is currently active.</span></span> <span data-ttu-id="8ed42-104">Vous devrez peut-être également modifier la cellule active.</span><span class="sxs-lookup"><span data-stu-id="8ed42-104">You may also need to change the current cell.</span></span> <span data-ttu-id="8ed42-105">Vous pouvez effectuer ces tâches avec la propriété <xref:System.Windows.Forms.DataGridView.CurrentCell%2A>.</span><span class="sxs-lookup"><span data-stu-id="8ed42-105">You can perform these tasks with the <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> property.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8ed42-106">Vous ne pouvez pas définir la cellule active dans une ligne ou une colonne dont la propriété <xref:System.Windows.Forms.DataGridViewBand.Visible%2A> a la valeur `false`.</span><span class="sxs-lookup"><span data-stu-id="8ed42-106">You cannot set the current cell in a row or column that has its <xref:System.Windows.Forms.DataGridViewBand.Visible%2A> property set to `false`.</span></span>  
  
 <span data-ttu-id="8ed42-107">Selon le mode de sélection du contrôle <xref:System.Windows.Forms.DataGridView>, la modification de la cellule active peut modifier la sélection.</span><span class="sxs-lookup"><span data-stu-id="8ed42-107">Depending on the <xref:System.Windows.Forms.DataGridView> control's selection mode, changing the current cell can change the selection.</span></span> <span data-ttu-id="8ed42-108">Pour plus d’informations, consultez [modes de sélection dans le contrôle DataGridView Windows Forms](selection-modes-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="8ed42-108">For more information, see [Selection Modes in the Windows Forms DataGridView Control](selection-modes-in-the-windows-forms-datagridview-control.md).</span></span>  
  
### <a name="to-get-the-current-cell-programmatically"></a><span data-ttu-id="8ed42-109">Pour récupérer la cellule active par programmation</span><span class="sxs-lookup"><span data-stu-id="8ed42-109">To get the current cell programmatically</span></span>  
  
- <span data-ttu-id="8ed42-110">Utilisez la propriété <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> du contrôle <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="8ed42-110">Use the <xref:System.Windows.Forms.DataGridView> control's <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> property.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#080](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#080)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#080](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#080)]  
  
### <a name="to-set-the-current-cell-programmatically"></a><span data-ttu-id="8ed42-111">Pour définir la cellule active par programmation</span><span class="sxs-lookup"><span data-stu-id="8ed42-111">To set the current cell programmatically</span></span>  
  
- <span data-ttu-id="8ed42-112">Définissez la propriété <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> du contrôle <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="8ed42-112">Set the <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> property of the <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="8ed42-113">Dans l’exemple de code suivant, la cellule active est définie sur la ligne 0, colonne 1.</span><span class="sxs-lookup"><span data-stu-id="8ed42-113">In the following code example, the current cell is set to row 0, column 1.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#085](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#085)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#085](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#085)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="8ed42-114">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="8ed42-114">Compiling the Code</span></span>  
 <span data-ttu-id="8ed42-115">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="8ed42-115">This example requires:</span></span>  
  
- <span data-ttu-id="8ed42-116"><xref:System.Windows.Forms.Button> contrôles nommés `getCurrentCellButton` et `setCurrentCellButton`.</span><span class="sxs-lookup"><span data-stu-id="8ed42-116"><xref:System.Windows.Forms.Button> controls named `getCurrentCellButton` and `setCurrentCellButton`.</span></span> <span data-ttu-id="8ed42-117">En Visual C#, vous devez joindre les événements <xref:System.Windows.Forms.Control.Click> pour chaque bouton au gestionnaire d’événements associé dans l’exemple de code.</span><span class="sxs-lookup"><span data-stu-id="8ed42-117">In Visual C#, you must attach the <xref:System.Windows.Forms.Control.Click> events for each button to the associated event handler in the example code.</span></span>  
  
- <span data-ttu-id="8ed42-118">un contrôle <xref:System.Windows.Forms.DataGridView> nommé `dataGridView1` ;</span><span class="sxs-lookup"><span data-stu-id="8ed42-118">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
- <span data-ttu-id="8ed42-119">des références aux assemblys <xref:System?displayProperty=nameWithType> et <xref:System.Windows.Forms?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8ed42-119">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ed42-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8ed42-120">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.CurrentCell%2A?displayProperty=nameWithType>
- [<span data-ttu-id="8ed42-121">Fonctionnalités de base liées aux colonnes, lignes et cellules dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8ed42-121">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](basic-column-row-and-cell-features-wf-datagridview-control.md)
- [<span data-ttu-id="8ed42-122">Modes de sélection dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8ed42-122">Selection Modes in the Windows Forms DataGridView Control</span></span>](selection-modes-in-the-windows-forms-datagridview-control.md)
