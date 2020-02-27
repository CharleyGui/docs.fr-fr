---
title: Modifier l’ordre des colonnes dans le contrôle DataGridView à l’aide du concepteur
ms.date: 03/30/2017
helpviewer_keywords:
- columns [Windows Forms], order of
- DataGridView control [Windows Forms], column order
- Windows Forms, columns
- data [Windows Forms], displaying
ms.assetid: 7fe52a98-75d6-448c-97a5-65ca2c568c1a
ms.openlocfilehash: 7540203fb1c0465caeb045275734d1a7c6f25ee8
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628746"
---
# <a name="how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control-using-the-designer"></a><span data-ttu-id="3042a-102">Comment : modifier l'ordre des colonnes dans le contrôle DataGridView Windows Forms à l'aide du concepteur</span><span class="sxs-lookup"><span data-stu-id="3042a-102">How to: Change the Order of Columns in the Windows Forms DataGridView Control Using the Designer</span></span>

<span data-ttu-id="3042a-103">Lorsque vous liez un contrôle Windows Forms <xref:System.Windows.Forms.DataGridView> à une source de données, l’ordre d’affichage des colonnes générées automatiquement est dicté par la source de données.</span><span class="sxs-lookup"><span data-stu-id="3042a-103">When you bind a Windows Forms <xref:System.Windows.Forms.DataGridView> control to a data source, the display order of the automatically generated columns is dictated by the data source.</span></span> <span data-ttu-id="3042a-104">Si cet ordre n’est pas celui que vous préférez, vous pouvez modifier l’ordre des colonnes à l’aide du concepteur.</span><span class="sxs-lookup"><span data-stu-id="3042a-104">If this order is not what you prefer, you can change the order of the columns using the designer.</span></span> <span data-ttu-id="3042a-105">Vous pouvez également ajouter des colonnes indépendantes au contrôle et modifier leur ordre d’affichage.</span><span class="sxs-lookup"><span data-stu-id="3042a-105">You may also want to add unbound columns to the control and change their display order.</span></span> <span data-ttu-id="3042a-106">Pour plus d’informations sur la modification de l’ordre des colonnes par programme, consultez [Comment : modifier l’ordre des colonnes dans le contrôle DataGridView Windows Forms](how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="3042a-106">For information about how to change the column order programmatically, see [How to: Change the Order of Columns in the Windows Forms DataGridView Control](how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control.md).</span></span>

<span data-ttu-id="3042a-107">La procédure suivante requiert un projet d' **application Windows** avec un formulaire contenant un contrôle de <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="3042a-107">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="3042a-108">Pour plus d’informations sur la configuration d’un tel projet, consultez [Comment : créer un projet d’application Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project) et [Comment : ajouter des contrôles à des Windows Forms](how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="3042a-108">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>

## <a name="to-change-the-column-order-using-the-designer"></a><span data-ttu-id="3042a-109">Pour modifier l’ordre des colonnes à l’aide du concepteur</span><span class="sxs-lookup"><span data-stu-id="3042a-109">To change the column order using the designer</span></span>

1. <span data-ttu-id="3042a-110">Cliquez sur le glyphe actions du concepteur (![petite flèche noire](./media/designer-actions-glyph.gif)) dans le coin supérieur droit du contrôle <xref:System.Windows.Forms.DataGridView>, puis sélectionnez **modifier les colonnes**.</span><span class="sxs-lookup"><span data-stu-id="3042a-110">Click the designer actions glyph (![Small black arrow](./media/designer-actions-glyph.gif)) on the upper-right corner of the <xref:System.Windows.Forms.DataGridView> control, and then select **Edit Columns**.</span></span>

2. <span data-ttu-id="3042a-111">Sélectionnez une colonne dans la liste **colonnes sélectionnées** .</span><span class="sxs-lookup"><span data-stu-id="3042a-111">Select a column from the **Selected Columns** list.</span></span>

3. <span data-ttu-id="3042a-112">Cliquez sur la flèche vers le haut ou vers le bas à droite de la liste **colonnes sélectionnées** jusqu’à ce que la colonne sélectionnée soit à la position de votre choix.</span><span class="sxs-lookup"><span data-stu-id="3042a-112">Click the up or down arrow to the right of the **Selected Columns** list until the selected column is in the position you want.</span></span>

## <a name="see-also"></a><span data-ttu-id="3042a-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3042a-113">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- [<span data-ttu-id="3042a-114">Guide pratique pour ajouter et supprimer des colonnes dans le contrôle DataGridView Windows Forms à l'aide du concepteur</span><span class="sxs-lookup"><span data-stu-id="3042a-114">How to: Add and Remove Columns in the Windows Forms DataGridView Control Using the Designer</span></span>](add-and-remove-columns-in-the-datagrid-using-the-designer.md)
- [<span data-ttu-id="3042a-115">Comment : créer un projet d’application Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3042a-115">How to: Create a Windows Forms application project</span></span>](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [<span data-ttu-id="3042a-116">Comment : ajouter des contrôles à des Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3042a-116">How to: Add Controls to Windows Forms</span></span>](how-to-add-controls-to-windows-forms.md)
