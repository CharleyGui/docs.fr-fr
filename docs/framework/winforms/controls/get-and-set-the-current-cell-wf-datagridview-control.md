---
title: 'Procédure : obtenir et définir la cellule active dans le contrôle DataGridView Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], getting current cell
- DataGridView control [Windows Forms], setting current cell
- cells [Windows Forms], getting and setting current
ms.assetid: b0e41e57-493a-4bd0-9376-a6f76723540c
ms.openlocfilehash: 670708f342e1cd1ac495c215b7508093349ac2e4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933698"
---
# <a name="how-to-get-and-set-the-current-cell-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="04001-102">Procédure : obtenir et définir la cellule active dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="04001-102">How to: Get and Set the Current Cell in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="04001-103">L' <xref:System.Windows.Forms.DataGridView> interaction avec vous oblige souvent à détecter par programmation la cellule actuellement active.</span><span class="sxs-lookup"><span data-stu-id="04001-103">Interaction with the <xref:System.Windows.Forms.DataGridView> often requires that you programmatically discover which cell is currently active.</span></span> <span data-ttu-id="04001-104">Vous devrez peut-être également modifier la cellule active.</span><span class="sxs-lookup"><span data-stu-id="04001-104">You may also need to change the current cell.</span></span> <span data-ttu-id="04001-105">Vous pouvez effectuer ces tâches avec la <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="04001-105">You can perform these tasks with the <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> property.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="04001-106">Vous ne pouvez pas définir la cellule active dans une ligne ou une colonne <xref:System.Windows.Forms.DataGridViewBand.Visible%2A> dont la propriété `false`a la valeur.</span><span class="sxs-lookup"><span data-stu-id="04001-106">You cannot set the current cell in a row or column that has its <xref:System.Windows.Forms.DataGridViewBand.Visible%2A> property set to `false`.</span></span>  
  
 <span data-ttu-id="04001-107">En fonction du <xref:System.Windows.Forms.DataGridView> mode de sélection du contrôle, la modification de la cellule active peut modifier la sélection.</span><span class="sxs-lookup"><span data-stu-id="04001-107">Depending on the <xref:System.Windows.Forms.DataGridView> control's selection mode, changing the current cell can change the selection.</span></span> <span data-ttu-id="04001-108">Pour plus d’informations, consultez [modes de sélection dans le contrôle DataGridView Windows Forms](selection-modes-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="04001-108">For more information, see [Selection Modes in the Windows Forms DataGridView Control](selection-modes-in-the-windows-forms-datagridview-control.md).</span></span>  
  
### <a name="to-get-the-current-cell-programmatically"></a><span data-ttu-id="04001-109">Pour récupérer la cellule active par programmation</span><span class="sxs-lookup"><span data-stu-id="04001-109">To get the current cell programmatically</span></span>  
  
- <span data-ttu-id="04001-110">Utilisez la <xref:System.Windows.Forms.DataGridView> propriété du <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> contrôle.</span><span class="sxs-lookup"><span data-stu-id="04001-110">Use the <xref:System.Windows.Forms.DataGridView> control's <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> property.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#080](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#080)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#080](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#080)]  
  
### <a name="to-set-the-current-cell-programmatically"></a><span data-ttu-id="04001-111">Pour définir la cellule active par programmation</span><span class="sxs-lookup"><span data-stu-id="04001-111">To set the current cell programmatically</span></span>  
  
- <span data-ttu-id="04001-112">Définissez la <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> propriété <xref:System.Windows.Forms.DataGridView> du contrôle.</span><span class="sxs-lookup"><span data-stu-id="04001-112">Set the <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> property of the <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="04001-113">Dans l’exemple de code suivant, la cellule active est définie sur la ligne 0, colonne 1.</span><span class="sxs-lookup"><span data-stu-id="04001-113">In the following code example, the current cell is set to row 0, column 1.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#085](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#085)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#085](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#085)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="04001-114">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="04001-114">Compiling the Code</span></span>  
 <span data-ttu-id="04001-115">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="04001-115">This example requires:</span></span>  
  
- <span data-ttu-id="04001-116"><xref:System.Windows.Forms.Button>contrôles nommés `getCurrentCellButton` et `setCurrentCellButton`.</span><span class="sxs-lookup"><span data-stu-id="04001-116"><xref:System.Windows.Forms.Button> controls named `getCurrentCellButton` and `setCurrentCellButton`.</span></span> <span data-ttu-id="04001-117">En Visual C#, vous devez joindre les <xref:System.Windows.Forms.Control.Click> événements pour chaque bouton au gestionnaire d’événements associé dans l’exemple de code.</span><span class="sxs-lookup"><span data-stu-id="04001-117">In Visual C#, you must attach the <xref:System.Windows.Forms.Control.Click> events for each button to the associated event handler in the example code.</span></span>  
  
- <span data-ttu-id="04001-118">un contrôle <xref:System.Windows.Forms.DataGridView> nommé `dataGridView1` ;</span><span class="sxs-lookup"><span data-stu-id="04001-118">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
- <span data-ttu-id="04001-119">des références aux assemblys <xref:System?displayProperty=nameWithType> et <xref:System.Windows.Forms?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="04001-119">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04001-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="04001-120">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.CurrentCell%2A?displayProperty=nameWithType>
- [<span data-ttu-id="04001-121">Fonctionnalités de base liées aux colonnes, lignes et cellules dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="04001-121">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](basic-column-row-and-cell-features-wf-datagridview-control.md)
- [<span data-ttu-id="04001-122">Modes de sélection dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="04001-122">Selection Modes in the Windows Forms DataGridView Control</span></span>](selection-modes-in-the-windows-forms-datagridview-control.md)
