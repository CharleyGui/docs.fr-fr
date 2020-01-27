---
title: Définir les colonnes en lecture seule dans le contrôle DataGridView à l’aide du concepteur
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, columns
- DataGridView control [Windows Forms], read-only columns
- data [Windows Forms], displaying
- columns [Windows Forms], read-only
ms.assetid: b4ef7a75-ab33-4ee3-b2cf-201530e454e9
ms.openlocfilehash: 51d9488ef83f7d2c1c01c9ffd756edf8944d738d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744976"
---
# <a name="how-to-make-columns-read-only-in-the-windows-forms-datagridview-control-using-the-designer"></a><span data-ttu-id="45b16-102">Comment : définir une colonne en lecture seule dans le contrôle DataGridView Windows Forms à l'aide du concepteur</span><span class="sxs-lookup"><span data-stu-id="45b16-102">How to: Make Columns Read-Only in the Windows Forms DataGridView Control Using the Designer</span></span>
<span data-ttu-id="45b16-103">Par défaut, les utilisateurs peuvent modifier les données numériques et de texte affichées dans le contrôle Windows Forms <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="45b16-103">By default, users can modify text and numerical data displayed in the Windows Forms <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="45b16-104">Si vous souhaitez afficher des données qui ne sont pas destinées à être modifiées, vous devez faire en sorte que les colonnes qui contiennent les données soient en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="45b16-104">If you want to display data that is not meant for modification, you must make the columns that contain the data read-only.</span></span> <span data-ttu-id="45b16-105">Pour plus d’informations sur la façon de rendre le contrôle entièrement en lecture seule, consultez [Comment : empêcher l’ajout et la suppression de lignes dans le contrôle DataGridView Windows Forms à l’aide du concepteur](prevent-row-addition-and-deletion-in-the-datagrid-using-the-designer.md).</span><span class="sxs-lookup"><span data-stu-id="45b16-105">For information about how to make the control entirely read-only, see [How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control Using the Designer](prevent-row-addition-and-deletion-in-the-datagrid-using-the-designer.md).</span></span>

 <span data-ttu-id="45b16-106">La procédure suivante requiert un projet d' **application Windows** avec un formulaire contenant un contrôle de <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="45b16-106">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="45b16-107">Pour plus d’informations sur la configuration d’un tel projet, consultez [Comment : créer un projet d’application Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project) et [Comment : ajouter des contrôles à des Windows Forms](how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="45b16-107">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>

## <a name="to-make-a-column-read-only-by-using-the-designer"></a><span data-ttu-id="45b16-108">Pour définir une colonne en lecture seule à l’aide du concepteur</span><span class="sxs-lookup"><span data-stu-id="45b16-108">To make a column read-only by using the designer</span></span>

1. <span data-ttu-id="45b16-109">Cliquez sur le glyphe de balise active (![glyphe de balise active](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) dans le coin supérieur droit du contrôle <xref:System.Windows.Forms.DataGridView>, puis sélectionnez **modifier les colonnes**.</span><span class="sxs-lookup"><span data-stu-id="45b16-109">Click the smart tag glyph (![Smart Tag Glyph](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) on the upper-right corner of the <xref:System.Windows.Forms.DataGridView> control, and then select **Edit Columns**.</span></span>

2. <span data-ttu-id="45b16-110">Sélectionnez une colonne dans la liste **colonnes sélectionnées** .</span><span class="sxs-lookup"><span data-stu-id="45b16-110">Select a column from the **Selected Columns** list.</span></span>

3. <span data-ttu-id="45b16-111">Dans la grille Propriétés de la **colonne** , affectez à la propriété <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A> la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="45b16-111">In the **Column Properties** grid, set the <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A> property to `true`.</span></span>

    > [!NOTE]
    > <span data-ttu-id="45b16-112">Vous pouvez également définir une colonne en lecture seule lorsque vous l’ajoutez en activant la case à cocher **lecture seule** dans la boîte de dialogue **Ajouter une colonne** .</span><span class="sxs-lookup"><span data-stu-id="45b16-112">You can also make a column read-only when you add it by selecting the **Read Only** check box in the **Add Column** dialog box.</span></span>

## <a name="see-also"></a><span data-ttu-id="45b16-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="45b16-113">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=nameWithType>
- [<span data-ttu-id="45b16-114">Guide pratique pour ajouter et supprimer des colonnes dans le contrôle DataGridView Windows Forms à l'aide du concepteur</span><span class="sxs-lookup"><span data-stu-id="45b16-114">How to: Add and Remove Columns in the Windows Forms DataGridView Control Using the Designer</span></span>](add-and-remove-columns-in-the-datagrid-using-the-designer.md)
- [<span data-ttu-id="45b16-115">Guide pratique pour empêcher l'ajout et la suppression de lignes dans le contrôle DataGridView Windows Forms à l'aide du concepteur</span><span class="sxs-lookup"><span data-stu-id="45b16-115">How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control Using the Designer</span></span>](prevent-row-addition-and-deletion-in-the-datagrid-using-the-designer.md)
- [<span data-ttu-id="45b16-116">Comment : créer un projet d’application Windows Forms</span><span class="sxs-lookup"><span data-stu-id="45b16-116">How to: Create a Windows Forms application project</span></span>](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [<span data-ttu-id="45b16-117">Comment : ajouter des contrôles à des Windows Forms</span><span class="sxs-lookup"><span data-stu-id="45b16-117">How to: Add Controls to Windows Forms</span></span>](how-to-add-controls-to-windows-forms.md)
