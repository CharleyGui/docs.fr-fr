---
title: Empêcher l’ajout et la suppression de lignes dans le contrôle DataGridView à l’aide du concepteur
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], preventing row addition or deletion
ms.assetid: a17722bd-9400-41e6-8dcc-c9c151f0a749
ms.openlocfilehash: cc9aff0f15d1bd6de5c469ee7069a99f3360837a
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76728706"
---
# <a name="how-to-prevent-row-addition-and-deletion-in-the-windows-forms-datagridview-control-using-the-designer"></a><span data-ttu-id="120bd-102">Comment : empêcher l'ajout et la suppression de lignes dans le contrôle DataGridView Windows Forms à l'aide du concepteur</span><span class="sxs-lookup"><span data-stu-id="120bd-102">How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control Using the Designer</span></span>
<span data-ttu-id="120bd-103">Vous pouvez vouloir empêcher les utilisateurs d'ajouter de nouvelles lignes de données à votre contrôle <xref:System.Windows.Forms.DataGridView> ou d'en supprimer des lignes existantes.</span><span class="sxs-lookup"><span data-stu-id="120bd-103">Sometimes you will want to prevent users from entering new rows of data or deleting existing rows in your <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="120bd-104">Les nouvelles lignes sont entrées dans la ligne spéciale pour les nouveaux enregistrements en bas du contrôle.</span><span class="sxs-lookup"><span data-stu-id="120bd-104">New rows are entered in the special row for new records at the bottom of the control.</span></span> <span data-ttu-id="120bd-105">Lorsque vous désactivez l’ajout de lignes, la ligne des nouveaux enregistrements n’est pas affichée.</span><span class="sxs-lookup"><span data-stu-id="120bd-105">When you disable row addition, the row for new records is not displayed.</span></span> <span data-ttu-id="120bd-106">Vous pouvez ensuite rendre le contrôle entièrement en lecture seule en désactivant la suppression de ligne et la modification de cellule.</span><span class="sxs-lookup"><span data-stu-id="120bd-106">You can then make the control entirely read-only by disabling row deletion and cell editing.</span></span>

 <span data-ttu-id="120bd-107">La procédure suivante requiert un projet d' **application Windows** avec un formulaire contenant un contrôle de <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="120bd-107">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="120bd-108">Pour plus d’informations sur la configuration d’un tel projet, consultez [Comment : créer un projet d’application Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project) et [Comment : ajouter des contrôles à des Windows Forms](how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="120bd-108">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>

## <a name="to-prevent-row-addition-and-deletion"></a><span data-ttu-id="120bd-109">Pour empêcher l’ajout et la suppression de lignes</span><span class="sxs-lookup"><span data-stu-id="120bd-109">To prevent row addition and deletion</span></span>

- <span data-ttu-id="120bd-110">Cliquez sur le glyphe de balise active (![glyphe de balise active](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) dans le coin supérieur droit du contrôle <xref:System.Windows.Forms.DataGridView>, puis désactivez les cases à cocher **activer l’ajout** et **activer la suppression** .</span><span class="sxs-lookup"><span data-stu-id="120bd-110">Click the smart tag glyph (![Smart Tag Glyph](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) on the upper-right corner of the <xref:System.Windows.Forms.DataGridView> control, and then clear the **Enable Adding** and **Enable Deleting** check boxes.</span></span>

    > [!NOTE]
    > <span data-ttu-id="120bd-111">Pour rendre le contrôle entièrement en lecture seule, désactivez également la case à cocher **activer la modification** .</span><span class="sxs-lookup"><span data-stu-id="120bd-111">To make the control entirely read-only, clear the **Enable Editing** check box as well.</span></span>

## <a name="see-also"></a><span data-ttu-id="120bd-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="120bd-112">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A?displayProperty=nameWithType>
- [<span data-ttu-id="120bd-113">Comment : créer un projet d’application Windows Forms</span><span class="sxs-lookup"><span data-stu-id="120bd-113">How to: Create a Windows Forms application project</span></span>](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [<span data-ttu-id="120bd-114">Comment : ajouter des contrôles à des Windows Forms</span><span class="sxs-lookup"><span data-stu-id="120bd-114">How to: Add Controls to Windows Forms</span></span>](how-to-add-controls-to-windows-forms.md)
