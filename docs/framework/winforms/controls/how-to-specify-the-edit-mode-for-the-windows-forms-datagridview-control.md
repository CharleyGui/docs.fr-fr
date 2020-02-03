---
title: Spécifier le mode d’édition pour le contrôle DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], edit mode
- data grids [Windows Forms], edit mode
ms.assetid: 93e117e8-94c4-411b-ba31-645e475ed85c
ms.openlocfilehash: c0318202a80f9a43f1b656201732ef032f430b5b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743765"
---
# <a name="how-to-specify-the-edit-mode-for-the-windows-forms-datagridview-control"></a><span data-ttu-id="b031a-102">Comment : spécifier le mode édition pour le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b031a-102">How to: Specify the Edit Mode for the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="b031a-103">Par défaut, les utilisateurs peuvent modifier le contenu de la cellule de zone de texte <xref:System.Windows.Forms.DataGridView> en cours en le tapant ou en appuyant sur F2.</span><span class="sxs-lookup"><span data-stu-id="b031a-103">By default, users can edit the contents of the current <xref:System.Windows.Forms.DataGridView> text box cell by typing in it or pressing F2.</span></span> <span data-ttu-id="b031a-104">Cette commande met la cellule en mode édition si toutes les conditions suivantes sont remplies :</span><span class="sxs-lookup"><span data-stu-id="b031a-104">This puts the cell in edit mode if all of the following conditions are met:</span></span>  
  
- <span data-ttu-id="b031a-105">La source de données sous-jacente prend en charge la modification.</span><span class="sxs-lookup"><span data-stu-id="b031a-105">The underlying data source supports editing.</span></span>  
  
- <span data-ttu-id="b031a-106">Le contrôle <xref:System.Windows.Forms.DataGridView> est activé.</span><span class="sxs-lookup"><span data-stu-id="b031a-106">The <xref:System.Windows.Forms.DataGridView> control is enabled.</span></span>  
  
- <span data-ttu-id="b031a-107">La valeur de propriété <xref:System.Windows.Forms.DataGridView.EditMode%2A> n'est pas <xref:System.Windows.Forms.DataGridViewEditMode.EditProgrammatically>.</span><span class="sxs-lookup"><span data-stu-id="b031a-107">The <xref:System.Windows.Forms.DataGridView.EditMode%2A> property value is not <xref:System.Windows.Forms.DataGridViewEditMode.EditProgrammatically>.</span></span>  
  
- <span data-ttu-id="b031a-108">Les propriétés `ReadOnly` de la cellule, de la ligne, de la colonne et du contrôle ont toutes la valeur `false`.</span><span class="sxs-lookup"><span data-stu-id="b031a-108">The `ReadOnly` properties of the cell, row, column, and control are all set to `false`.</span></span>  
  
 <span data-ttu-id="b031a-109">En mode édition, l’utilisateur peut modifier la valeur de la cellule et appuyer sur entrée pour valider la modification ou sur ÉCHAP pour rétablir la valeur d’origine de la cellule.</span><span class="sxs-lookup"><span data-stu-id="b031a-109">In edit mode, the user can change the cell value and press ENTER to commit the change or ESC to revert the cell to its original value.</span></span>  
  
 <span data-ttu-id="b031a-110">Vous pouvez configurer un contrôle de <xref:System.Windows.Forms.DataGridView> afin qu’une cellule passe en mode édition dès qu’elle devient la cellule active.</span><span class="sxs-lookup"><span data-stu-id="b031a-110">You can configure a <xref:System.Windows.Forms.DataGridView> control so that a cell enters edit mode as soon as it becomes the current cell.</span></span> <span data-ttu-id="b031a-111">Le comportement des touches entrée et Échap est inchangé dans ce cas, mais la cellule reste en mode édition après que la valeur a été validée ou annulée.</span><span class="sxs-lookup"><span data-stu-id="b031a-111">The behavior of the ENTER and ESC keys is unchanged in this case, but the cell remains in edit mode after the value is committed or reverted.</span></span> <span data-ttu-id="b031a-112">Vous pouvez également configurer le contrôle afin que les cellules entrent en mode édition uniquement lorsque les utilisateurs tapent dans la cellule ou uniquement quand les utilisateurs appuient sur F2.</span><span class="sxs-lookup"><span data-stu-id="b031a-112">You can also configure the control so that cells enter edit mode only when users type in the cell or only when users press F2.</span></span> <span data-ttu-id="b031a-113">Enfin, vous pouvez empêcher les cellules d’entrer en mode édition, sauf lorsque vous appelez la méthode <xref:System.Windows.Forms.DataGridView.BeginEdit%2A>.</span><span class="sxs-lookup"><span data-stu-id="b031a-113">Finally, you can prevent cells from entering edit mode except when you call the <xref:System.Windows.Forms.DataGridView.BeginEdit%2A> method.</span></span>  
  
### <a name="to-change-the-edit-mode-of-a-datagridview-control"></a><span data-ttu-id="b031a-114">Pour modifier le mode d’édition d’un contrôle DataGridView</span><span class="sxs-lookup"><span data-stu-id="b031a-114">To change the edit mode of a DataGridView control</span></span>  
  
- <span data-ttu-id="b031a-115">Affectez à la propriété <xref:System.Windows.Forms.DataGridView.EditMode%2A?displayProperty=nameWithType> l’énumération <xref:System.Windows.Forms.DataGridViewEditMode> appropriée.</span><span class="sxs-lookup"><span data-stu-id="b031a-115">Set the <xref:System.Windows.Forms.DataGridView.EditMode%2A?displayProperty=nameWithType> property to the appropriate <xref:System.Windows.Forms.DataGridViewEditMode> enumeration.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#067](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#067)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#067](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#067)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b031a-116">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="b031a-116">Compiling the Code</span></span>  
 <span data-ttu-id="b031a-117">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="b031a-117">This example requires:</span></span>  
  
- <span data-ttu-id="b031a-118">un contrôle <xref:System.Windows.Forms.DataGridView> nommé `dataGridView1` ;</span><span class="sxs-lookup"><span data-stu-id="b031a-118">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
- <span data-ttu-id="b031a-119">des références aux assemblys <xref:System> et <xref:System.Windows.Forms>.</span><span class="sxs-lookup"><span data-stu-id="b031a-119">References to the <xref:System> and <xref:System.Windows.Forms> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b031a-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b031a-120">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.EditMode%2A?displayProperty=nameWithType>
- [<span data-ttu-id="b031a-121">Saisie de données dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b031a-121">Data Entry in the Windows Forms DataGridView Control</span></span>](data-entry-in-the-windows-forms-datagridview-control.md)
