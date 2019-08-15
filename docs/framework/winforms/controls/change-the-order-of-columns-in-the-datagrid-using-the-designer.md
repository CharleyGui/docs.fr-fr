---
title: 'Procédure : modifier l’ordre des colonnes dans le contrôle DataGridView Windows Forms à l’aide du concepteur'
ms.date: 03/30/2017
helpviewer_keywords:
- columns [Windows Forms], order of
- DataGridView control [Windows Forms], column order
- Windows Forms, columns
- data [Windows Forms], displaying
ms.assetid: 7fe52a98-75d6-448c-97a5-65ca2c568c1a
ms.openlocfilehash: bf77cf3705a470bbe00be383f6a5cb2d28bda34d
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039631"
---
# <a name="how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control-using-the-designer"></a><span data-ttu-id="5137a-102">Procédure : modifier l’ordre des colonnes dans le contrôle DataGridView Windows Forms à l’aide du concepteur</span><span class="sxs-lookup"><span data-stu-id="5137a-102">How to: Change the Order of Columns in the Windows Forms DataGridView Control Using the Designer</span></span>

<span data-ttu-id="5137a-103">Lorsque vous liez un contrôle <xref:System.Windows.Forms.DataGridView> de Windows Forms à une source de données, l’ordre d’affichage des colonnes générées automatiquement est dicté par la source de données.</span><span class="sxs-lookup"><span data-stu-id="5137a-103">When you bind a Windows Forms <xref:System.Windows.Forms.DataGridView> control to a data source, the display order of the automatically generated columns is dictated by the data source.</span></span> <span data-ttu-id="5137a-104">Si cet ordre n’est pas celui que vous préférez, vous pouvez modifier l’ordre des colonnes à l’aide du concepteur.</span><span class="sxs-lookup"><span data-stu-id="5137a-104">If this order is not what you prefer, you can change the order of the columns using the designer.</span></span> <span data-ttu-id="5137a-105">Vous pouvez également ajouter des colonnes indépendantes au contrôle et modifier leur ordre d’affichage.</span><span class="sxs-lookup"><span data-stu-id="5137a-105">You may also want to add unbound columns to the control and change their display order.</span></span> <span data-ttu-id="5137a-106">Pour plus d’informations sur la modification de l’ordre des colonnes par programme [, consultez Procédure: Modifiez l’ordre des colonnes dans le contrôle](how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control.md)DataGridView Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="5137a-106">For information about how to change the column order programmatically, see [How to: Change the Order of Columns in the Windows Forms DataGridView Control](how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control.md).</span></span>

<span data-ttu-id="5137a-107">La procédure suivante requiert un projet d' **application Windows** avec un formulaire contenant <xref:System.Windows.Forms.DataGridView> un contrôle.</span><span class="sxs-lookup"><span data-stu-id="5137a-107">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="5137a-108">Pour plus d’informations sur la configuration d’un tel [projet, consultez Procédure: Créez un projet](/visualstudio/ide/step-1-create-a-windows-forms-application-project) d’application Windows Forms [et procédez comme suit: Ajoutez des contrôles à](how-to-add-controls-to-windows-forms.md)Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="5137a-108">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>

## <a name="to-change-the-column-order-using-the-designer"></a><span data-ttu-id="5137a-109">Pour modifier l’ordre des colonnes à l’aide du concepteur</span><span class="sxs-lookup"><span data-stu-id="5137a-109">To change the column order using the designer</span></span>

1. <span data-ttu-id="5137a-110">Cliquez sur le glyphe de balise active (![glyphe de balise active](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) dans le <xref:System.Windows.Forms.DataGridView> coin supérieur droit du contrôle, puis sélectionnez Modifier les **colonnes**.</span><span class="sxs-lookup"><span data-stu-id="5137a-110">Click the smart tag glyph (![Smart Tag Glyph](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) on the upper-right corner of the <xref:System.Windows.Forms.DataGridView> control, and then select **Edit Columns**.</span></span>

2. <span data-ttu-id="5137a-111">Sélectionnez une colonne dans la liste **colonnes sélectionnées** .</span><span class="sxs-lookup"><span data-stu-id="5137a-111">Select a column from the **Selected Columns** list.</span></span>

3. <span data-ttu-id="5137a-112">Cliquez sur la flèche vers le haut ou vers le bas à droite de la liste **colonnes sélectionnées** jusqu’à ce que la colonne sélectionnée soit à la position de votre choix.</span><span class="sxs-lookup"><span data-stu-id="5137a-112">Click the up or down arrow to the right of the **Selected Columns** list until the selected column is in the position you want.</span></span>

## <a name="see-also"></a><span data-ttu-id="5137a-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5137a-113">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- [<span data-ttu-id="5137a-114">Guide pratique pour Ajouter et supprimer des colonnes dans le contrôle DataGridView Windows Forms à l’aide du concepteur</span><span class="sxs-lookup"><span data-stu-id="5137a-114">How to: Add and Remove Columns in the Windows Forms DataGridView Control Using the Designer</span></span>](add-and-remove-columns-in-the-datagrid-using-the-designer.md)
- [<span data-ttu-id="5137a-115">Guide pratique pour Créer un projet Application Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5137a-115">How to: Create a Windows Forms application project</span></span>](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [<span data-ttu-id="5137a-116">Guide pratique : Ajouter des contrôles à Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5137a-116">How to: Add Controls to Windows Forms</span></span>](how-to-add-controls-to-windows-forms.md)
