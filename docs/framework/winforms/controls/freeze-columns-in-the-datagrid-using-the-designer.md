---
title: Figer les colonnes dans le contrôle DataGridView à l’aide du concepteur
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, columns
- columns [Windows Forms], freezing
- DataGridView control [Windows Forms], column freezing
- data [Windows Forms], displaying
ms.assetid: 87412dd2-478f-4751-af87-dafc591fc215
ms.openlocfilehash: af8e07d7b1b0524e33688fd9d879818aa13be041
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745682"
---
# <a name="how-to-freeze-columns-in-the-windows-forms-datagridview-control-using-the-designer"></a><span data-ttu-id="36e40-102">Comment : figer les colonnes du contrôle DataGridView Windows Forms à l'aide du concepteur</span><span class="sxs-lookup"><span data-stu-id="36e40-102">How to: Freeze Columns in the Windows Forms DataGridView Control Using the Designer</span></span>
<span data-ttu-id="36e40-103">Quand des utilisateurs consultent des données affichées dans un contrôle Windows Forms <xref:System.Windows.Forms.DataGridView>, ils doivent parfois faire fréquemment référence à une même colonne ou un même ensemble de colonnes.</span><span class="sxs-lookup"><span data-stu-id="36e40-103">When users view data displayed in a Windows Forms <xref:System.Windows.Forms.DataGridView> control, they sometimes need to refer to a single column or set of columns frequently.</span></span> <span data-ttu-id="36e40-104">Par exemple, lorsque vous affichez une table d’informations client qui contient de nombreuses colonnes, il est utile d’afficher le nom du client à tout moment, tout en permettant à d’autres colonnes de faire défiler la région visible.</span><span class="sxs-lookup"><span data-stu-id="36e40-104">For example, when you display a table of customer information that contains many columns, it is useful for you to display the customer name at all times while enabling other columns to scroll outside the visible region.</span></span>

 <span data-ttu-id="36e40-105">Pour obtenir ce comportement, vous pouvez figer des colonnes dans le contrôle.</span><span class="sxs-lookup"><span data-stu-id="36e40-105">To achieve this behavior, you can freeze columns in the control.</span></span> <span data-ttu-id="36e40-106">Quand vous figez une colonne, toutes les colonnes à sa gauche (ou à sa droite dans les scripts de droite à gauche) sont aussi figées.</span><span class="sxs-lookup"><span data-stu-id="36e40-106">When you freeze a column, all the columns to its left (or to its right in right-to-left language scripts) are frozen as well.</span></span> <span data-ttu-id="36e40-107">Les colonnes figées restent en place, tandis que toutes les autres colonnes peuvent défiler.</span><span class="sxs-lookup"><span data-stu-id="36e40-107">Frozen columns remain in place while all other columns can scroll.</span></span> <span data-ttu-id="36e40-108">Si la réorganisation des colonnes est activée, les colonnes figées sont traitées comme un groupe distinct des colonnes non figées.</span><span class="sxs-lookup"><span data-stu-id="36e40-108">If column reordering is enabled, the frozen columns are treated as a group distinct from the unfrozen columns.</span></span> <span data-ttu-id="36e40-109">Les utilisateurs peuvent repositionner des colonnes dans l'un ou l'autre groupe, mais ils ne peuvent pas déplacer une colonne d'un groupe à l'autre.</span><span class="sxs-lookup"><span data-stu-id="36e40-109">Users can reposition columns in either group, but they cannot move a column from one group to the other.</span></span>

 <span data-ttu-id="36e40-110">La procédure suivante requiert un projet d' **application Windows** avec un formulaire contenant un contrôle de <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="36e40-110">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="36e40-111">Pour plus d’informations sur la configuration d’un tel projet, consultez [Comment : créer un projet d’application Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project) et [Comment : ajouter des contrôles à des Windows Forms](how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="36e40-111">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>

## <a name="to-freeze-a-column-using-the-designer"></a><span data-ttu-id="36e40-112">Pour figer une colonne à l’aide du concepteur</span><span class="sxs-lookup"><span data-stu-id="36e40-112">To freeze a column using the designer</span></span>

1. <span data-ttu-id="36e40-113">Cliquez sur le glyphe de balise active (![glyphe de balise active](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) dans le coin supérieur droit du contrôle <xref:System.Windows.Forms.DataGridView>, puis sélectionnez **modifier les colonnes**.</span><span class="sxs-lookup"><span data-stu-id="36e40-113">Click the smart tag glyph (![Smart Tag Glyph](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) on the upper-right corner of the <xref:System.Windows.Forms.DataGridView> control, and then select **Edit Columns**.</span></span>

2. <span data-ttu-id="36e40-114">Sélectionnez une colonne dans la liste **colonnes sélectionnées** .</span><span class="sxs-lookup"><span data-stu-id="36e40-114">Select a column from the **Selected Columns** list.</span></span>

3. <span data-ttu-id="36e40-115">Dans la grille Propriétés de la **colonne** , affectez à la propriété <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A> la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="36e40-115">In the **Column Properties** grid, set the <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A> property to `true`.</span></span>

    > [!NOTE]
    > <span data-ttu-id="36e40-116">Vous pouvez également geler une colonne quand vous l’ajoutez en sélectionnant la zone **figée** dans la boîte de dialogue **Ajouter une colonne** .</span><span class="sxs-lookup"><span data-stu-id="36e40-116">You can also freeze a column when adding it by selecting the **Frozen** box in the **Add Column** dialog box.</span></span>

## <a name="see-also"></a><span data-ttu-id="36e40-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="36e40-117">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A?displayProperty=nameWithType>
- [<span data-ttu-id="36e40-118">Guide pratique pour ajouter et supprimer des colonnes dans le contrôle DataGridView Windows Forms à l'aide du concepteur</span><span class="sxs-lookup"><span data-stu-id="36e40-118">How to: Add and Remove Columns in the Windows Forms DataGridView Control Using the Designer</span></span>](add-and-remove-columns-in-the-datagrid-using-the-designer.md)
- [<span data-ttu-id="36e40-119">Guide pratique pour activer la réorganisation des colonnes dans le contrôle DataGridView Windows Forms à l'aide du concepteur</span><span class="sxs-lookup"><span data-stu-id="36e40-119">How to: Enable Column Reordering in the Windows Forms DataGridView Control Using the Designer</span></span>](enable-column-reordering-in-the-datagrid-using-the-designer.md)
- <span data-ttu-id="36e40-120">[Comment : afficher du texte de droite à gauche dans Windows Forms pour la globalisation](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/7d3337xw(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="36e40-120">[How to: Display Right-to-Left Text in Windows Forms for Globalization](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/7d3337xw(v=vs.100))</span></span>
- [<span data-ttu-id="36e40-121">Comment : créer un projet d’application Windows Forms</span><span class="sxs-lookup"><span data-stu-id="36e40-121">How to: Create a Windows Forms application project</span></span>](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [<span data-ttu-id="36e40-122">Comment : ajouter des contrôles à des Windows Forms</span><span class="sxs-lookup"><span data-stu-id="36e40-122">How to: Add Controls to Windows Forms</span></span>](how-to-add-controls-to-windows-forms.md)
