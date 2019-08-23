---
title: 'Procédure : mettre les colonnes en lecture seule dans le contrôle DataGridView Windows Forms à l’aide du concepteur'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, columns
- DataGridView control [Windows Forms], read-only columns
- data [Windows Forms], displaying
- columns [Windows Forms], read-only
ms.assetid: b4ef7a75-ab33-4ee3-b2cf-201530e454e9
ms.openlocfilehash: 82be9d31ff6bb3f2f5dd8a55b4426103d466bdd6
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69952093"
---
# <a name="how-to-make-columns-read-only-in-the-windows-forms-datagridview-control-using-the-designer"></a><span data-ttu-id="aded5-102">Procédure : mettre les colonnes en lecture seule dans le contrôle DataGridView Windows Forms à l’aide du concepteur</span><span class="sxs-lookup"><span data-stu-id="aded5-102">How to: Make Columns Read-Only in the Windows Forms DataGridView Control Using the Designer</span></span>
<span data-ttu-id="aded5-103">Par défaut, les utilisateurs peuvent modifier les données numériques et de texte affichées <xref:System.Windows.Forms.DataGridView> dans le contrôle Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="aded5-103">By default, users can modify text and numerical data displayed in the Windows Forms <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="aded5-104">Si vous souhaitez afficher des données qui ne sont pas destinées à être modifiées, vous devez faire en sorte que les colonnes qui contiennent les données soient en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="aded5-104">If you want to display data that is not meant for modification, you must make the columns that contain the data read-only.</span></span> <span data-ttu-id="aded5-105">Pour plus d’informations sur la façon de rendre le contrôle entièrement accessible en [lecture seule, consultez Procédure: Empêcher l’ajout et la suppression de lignes dans le contrôle DataGridView Windows Forms](prevent-row-addition-and-deletion-in-the-datagrid-using-the-designer.md)à l’aide du concepteur.</span><span class="sxs-lookup"><span data-stu-id="aded5-105">For information about how to make the control entirely read-only, see [How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control Using the Designer](prevent-row-addition-and-deletion-in-the-datagrid-using-the-designer.md).</span></span>

 <span data-ttu-id="aded5-106">La procédure suivante requiert un projet d' **application Windows** avec un formulaire contenant <xref:System.Windows.Forms.DataGridView> un contrôle.</span><span class="sxs-lookup"><span data-stu-id="aded5-106">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="aded5-107">Pour plus d’informations sur la configuration d’un tel [projet, consultez Procédure: Créez un projet](/visualstudio/ide/step-1-create-a-windows-forms-application-project) d’application Windows Forms [et procédez comme suit: Ajoutez des contrôles à](how-to-add-controls-to-windows-forms.md)Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="aded5-107">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>

## <a name="to-make-a-column-read-only-by-using-the-designer"></a><span data-ttu-id="aded5-108">Pour définir une colonne en lecture seule à l’aide du concepteur</span><span class="sxs-lookup"><span data-stu-id="aded5-108">To make a column read-only by using the designer</span></span>

1. <span data-ttu-id="aded5-109">Cliquez sur le glyphe de balise active (![glyphe de balise active](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) dans le <xref:System.Windows.Forms.DataGridView> coin supérieur droit du contrôle, puis sélectionnez Modifier les **colonnes**.</span><span class="sxs-lookup"><span data-stu-id="aded5-109">Click the smart tag glyph (![Smart Tag Glyph](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) on the upper-right corner of the <xref:System.Windows.Forms.DataGridView> control, and then select **Edit Columns**.</span></span>

2. <span data-ttu-id="aded5-110">Sélectionnez une colonne dans la liste **colonnes sélectionnées** .</span><span class="sxs-lookup"><span data-stu-id="aded5-110">Select a column from the **Selected Columns** list.</span></span>

3. <span data-ttu-id="aded5-111">Dans la grille Propriétés de la **colonne** , <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A> affectez `true`à la propriété la valeur.</span><span class="sxs-lookup"><span data-stu-id="aded5-111">In the **Column Properties** grid, set the <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A> property to `true`.</span></span>

    > [!NOTE]
    > <span data-ttu-id="aded5-112">Vous pouvez également définir une colonne en lecture seule lorsque vous l’ajoutez en activant la case à cocher **lecture seule** dans la boîte de dialogue **Ajouter une colonne** .</span><span class="sxs-lookup"><span data-stu-id="aded5-112">You can also make a column read-only when you add it by selecting the **Read Only** check box in the **Add Column** dialog box.</span></span>

## <a name="see-also"></a><span data-ttu-id="aded5-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="aded5-113">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=nameWithType>
- [<span data-ttu-id="aded5-114">Guide pratique : Ajouter et supprimer des colonnes dans le contrôle DataGridView Windows Forms à l’aide du concepteur</span><span class="sxs-lookup"><span data-stu-id="aded5-114">How to: Add and Remove Columns in the Windows Forms DataGridView Control Using the Designer</span></span>](add-and-remove-columns-in-the-datagrid-using-the-designer.md)
- [<span data-ttu-id="aded5-115">Guide pratique pour Empêcher l’ajout et la suppression de lignes dans le contrôle DataGridView Windows Forms à l’aide du concepteur</span><span class="sxs-lookup"><span data-stu-id="aded5-115">How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control Using the Designer</span></span>](prevent-row-addition-and-deletion-in-the-datagrid-using-the-designer.md)
- [<span data-ttu-id="aded5-116">Guide pratique : Créer un projet Application Windows Forms</span><span class="sxs-lookup"><span data-stu-id="aded5-116">How to: Create a Windows Forms application project</span></span>](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [<span data-ttu-id="aded5-117">Guide pratique pour Ajouter des contrôles à Windows Forms</span><span class="sxs-lookup"><span data-stu-id="aded5-117">How to: Add Controls to Windows Forms</span></span>](how-to-add-controls-to-windows-forms.md)
