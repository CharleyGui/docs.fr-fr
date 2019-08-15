---
title: 'Procédure : masquer des colonnes dans le contrôle DataGridView Windows Forms à l’aide du concepteur'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, columns
- columns [Windows Forms], hiding
- DataGridView control [Windows Forms], column hiding
- data [Windows Forms], displaying
ms.assetid: a81c38e6-2527-426a-bcb1-be691403be04
ms.openlocfilehash: d502a89913e108254848151e9058ac6ae83a9638
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039777"
---
# <a name="how-to-hide-columns-in-the-windows-forms-datagridview-control-using-the-designer"></a><span data-ttu-id="8c6e6-102">Procédure : masquer des colonnes dans le contrôle DataGridView Windows Forms à l’aide du concepteur</span><span class="sxs-lookup"><span data-stu-id="8c6e6-102">How to: Hide Columns in the Windows Forms DataGridView Control Using the Designer</span></span>
<span data-ttu-id="8c6e6-103">Parfois, vous souhaiterez afficher uniquement quelques-unes des colonnes qui sont disponibles dans un contrôle <xref:System.Windows.Forms.DataGridView> Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="8c6e6-103">Sometimes you will want to display only some of the columns that are available in a Windows Forms <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="8c6e6-104">Par exemple, vous souhaiterez peut-être afficher une colonne salaire employé pour les utilisateurs disposant d’informations d’identification de gestion, tout en les masquant aux autres utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="8c6e6-104">For example, you may want to show an employee salary column to users with management credentials while hiding it from other users.</span></span> <span data-ttu-id="8c6e6-105">Vous pouvez également lier le contrôle à une source de données qui contient de nombreuses colonnes, dont vous souhaitez afficher uniquement certaines.</span><span class="sxs-lookup"><span data-stu-id="8c6e6-105">Alternately, you may want to bind the control to a data source that contains many columns, only some of which you want to display.</span></span> <span data-ttu-id="8c6e6-106">Dans ce cas, vous supprimez généralement les colonnes que vous ne souhaitez pas afficher au lieu de les masquer.</span><span class="sxs-lookup"><span data-stu-id="8c6e6-106">In this case, you will typically remove the columns you are not interested in displaying rather than hiding them.</span></span> <span data-ttu-id="8c6e6-107">Pour plus d'informations, voir [Procédure : Ajoutez et supprimez des colonnes dans le contrôle DataGridView Windows Forms à](add-and-remove-columns-in-the-datagrid-using-the-designer.md)l’aide du concepteur.</span><span class="sxs-lookup"><span data-stu-id="8c6e6-107">For more information, see [How to: Add and Remove Columns in the Windows Forms DataGridView Control Using the Designer](add-and-remove-columns-in-the-datagrid-using-the-designer.md).</span></span>

 <span data-ttu-id="8c6e6-108">La procédure suivante requiert un projet d' **application Windows** avec un formulaire contenant <xref:System.Windows.Forms.DataGridView> un contrôle.</span><span class="sxs-lookup"><span data-stu-id="8c6e6-108">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="8c6e6-109">Pour plus d’informations sur la configuration d’un tel [projet, consultez Procédure: Créez un projet](/visualstudio/ide/step-1-create-a-windows-forms-application-project) d’application Windows Forms [et procédez comme suit: Ajoutez des contrôles à](how-to-add-controls-to-windows-forms.md)Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="8c6e6-109">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>

## <a name="to-hide-a-column-using-the-designer"></a><span data-ttu-id="8c6e6-110">Pour masquer une colonne à l’aide du concepteur</span><span class="sxs-lookup"><span data-stu-id="8c6e6-110">To hide a column using the designer</span></span>

1. <span data-ttu-id="8c6e6-111">Cliquez sur le glyphe de balise active (![glyphe de balise active](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) dans le <xref:System.Windows.Forms.DataGridView> coin supérieur droit du contrôle, puis sélectionnez Modifier les **colonnes**.</span><span class="sxs-lookup"><span data-stu-id="8c6e6-111">Click the smart tag glyph (![Smart Tag Glyph](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) on the upper-right corner of the <xref:System.Windows.Forms.DataGridView> control, and then select **Edit Columns**.</span></span>

2. <span data-ttu-id="8c6e6-112">Sélectionnez une colonne dans la liste **colonnes sélectionnées** .</span><span class="sxs-lookup"><span data-stu-id="8c6e6-112">Select a column from the **Selected Columns** list.</span></span>

3. <span data-ttu-id="8c6e6-113">Dans la grille Propriétés de la **colonne** , <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A> affectez `false`à la propriété la valeur.</span><span class="sxs-lookup"><span data-stu-id="8c6e6-113">In the **Column Properties** grid, set the <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A> property to `false`.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="8c6e6-114">Vous pouvez également masquer une colonne lors de son ajout en désactivant la case à cocher **visible** dans la boîte de dialogue **Ajouter une colonne** .</span><span class="sxs-lookup"><span data-stu-id="8c6e6-114">You can also hide a column when adding it by clearing the **Visible** check box in the **Add Column** dialog box.</span></span>

## <a name="see-also"></a><span data-ttu-id="8c6e6-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8c6e6-115">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A?displayProperty=nameWithType>
- [<span data-ttu-id="8c6e6-116">Guide pratique : Ajouter et supprimer des colonnes dans le contrôle DataGridView Windows Forms à l’aide du concepteur</span><span class="sxs-lookup"><span data-stu-id="8c6e6-116">How to: Add and Remove Columns in the Windows Forms DataGridView Control Using the Designer</span></span>](add-and-remove-columns-in-the-datagrid-using-the-designer.md)
- [<span data-ttu-id="8c6e6-117">Guide pratique : Créer un projet Application Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8c6e6-117">How to: Create a Windows Forms application project</span></span>](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [<span data-ttu-id="8c6e6-118">Guide pratique pour Ajouter des contrôles à Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8c6e6-118">How to: Add Controls to Windows Forms</span></span>](how-to-add-controls-to-windows-forms.md)
