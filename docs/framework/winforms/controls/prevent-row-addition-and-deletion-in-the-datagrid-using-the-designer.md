---
title: 'Procédure : empêcher l’ajout et la suppression de lignes dans le contrôle DataGridView Windows Forms à l’aide du concepteur'
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], preventing row addition or deletion
ms.assetid: a17722bd-9400-41e6-8dcc-c9c151f0a749
ms.openlocfilehash: f47eb29bf9ae077555f352d10c667bac4ade9373
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968323"
---
# <a name="how-to-prevent-row-addition-and-deletion-in-the-windows-forms-datagridview-control-using-the-designer"></a><span data-ttu-id="293e0-102">Procédure : empêcher l’ajout et la suppression de lignes dans le contrôle DataGridView Windows Forms à l’aide du concepteur</span><span class="sxs-lookup"><span data-stu-id="293e0-102">How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control Using the Designer</span></span>
<span data-ttu-id="293e0-103">Vous pouvez vouloir empêcher les utilisateurs d'ajouter de nouvelles lignes de données à votre contrôle <xref:System.Windows.Forms.DataGridView> ou d'en supprimer des lignes existantes.</span><span class="sxs-lookup"><span data-stu-id="293e0-103">Sometimes you will want to prevent users from entering new rows of data or deleting existing rows in your <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="293e0-104">Les nouvelles lignes sont entrées dans la ligne spéciale pour les nouveaux enregistrements en bas du contrôle.</span><span class="sxs-lookup"><span data-stu-id="293e0-104">New rows are entered in the special row for new records at the bottom of the control.</span></span> <span data-ttu-id="293e0-105">Lorsque vous désactivez l’ajout de lignes, la ligne des nouveaux enregistrements n’est pas affichée.</span><span class="sxs-lookup"><span data-stu-id="293e0-105">When you disable row addition, the row for new records is not displayed.</span></span> <span data-ttu-id="293e0-106">Vous pouvez ensuite rendre le contrôle entièrement en lecture seule en désactivant la suppression de ligne et la modification de cellule.</span><span class="sxs-lookup"><span data-stu-id="293e0-106">You can then make the control entirely read-only by disabling row deletion and cell editing.</span></span>

 <span data-ttu-id="293e0-107">La procédure suivante requiert un projet d' **application Windows** avec un formulaire contenant <xref:System.Windows.Forms.DataGridView> un contrôle.</span><span class="sxs-lookup"><span data-stu-id="293e0-107">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="293e0-108">Pour plus d’informations sur la configuration d’un tel [projet, consultez Procédure: Créez un projet](/visualstudio/ide/step-1-create-a-windows-forms-application-project) d’application Windows Forms [et procédez comme suit: Ajoutez des contrôles à](how-to-add-controls-to-windows-forms.md)Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="293e0-108">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>

## <a name="to-prevent-row-addition-and-deletion"></a><span data-ttu-id="293e0-109">Pour empêcher l’ajout et la suppression de lignes</span><span class="sxs-lookup"><span data-stu-id="293e0-109">To prevent row addition and deletion</span></span>

- <span data-ttu-id="293e0-110">Cliquez sur le glyphe de balise active (![glyphe de balise active](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) dans le <xref:System.Windows.Forms.DataGridView> coin supérieur droit du contrôle, puis désactivez les cases à cocher Activer l' **Ajout** et **activer la suppression** .</span><span class="sxs-lookup"><span data-stu-id="293e0-110">Click the smart tag glyph (![Smart Tag Glyph](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) on the upper-right corner of the <xref:System.Windows.Forms.DataGridView> control, and then clear the **Enable Adding** and **Enable Deleting** check boxes.</span></span>

    > [!NOTE]
    > <span data-ttu-id="293e0-111">Pour rendre le contrôle entièrement en lecture seule, désactivez également la case à cocher **activer la modification** .</span><span class="sxs-lookup"><span data-stu-id="293e0-111">To make the control entirely read-only, clear the **Enable Editing** check box as well.</span></span>

## <a name="see-also"></a><span data-ttu-id="293e0-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="293e0-112">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A?displayProperty=nameWithType>
- [<span data-ttu-id="293e0-113">Guide pratique pour Créer un projet Application Windows Forms</span><span class="sxs-lookup"><span data-stu-id="293e0-113">How to: Create a Windows Forms application project</span></span>](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [<span data-ttu-id="293e0-114">Guide pratique pour Ajouter des contrôles à Windows Forms</span><span class="sxs-lookup"><span data-stu-id="293e0-114">How to: Add Controls to Windows Forms</span></span>](how-to-add-controls-to-windows-forms.md)
