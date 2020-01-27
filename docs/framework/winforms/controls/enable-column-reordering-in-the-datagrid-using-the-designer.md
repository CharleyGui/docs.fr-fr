---
title: Activer la réorganisation des colonnes dans le contrôle DataGridView à l’aide du concepteur
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], column order
- Windows Forms, columns
- columns [Windows Forms], reordering
- data [Windows Forms], displaying
ms.assetid: d82bd69c-6799-4439-a32c-91139c5901d1
ms.openlocfilehash: 823c0064b2710ab5dfd0f67edf95374590d4490b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745840"
---
# <a name="how-to-enable-column-reordering-in-the-windows-forms-datagridview-control-using-the-designer"></a><span data-ttu-id="7f2f2-102">Comment : activer la réorganisation des colonnes dans le contrôle DataGridView Windows Forms à l'aide du concepteur</span><span class="sxs-lookup"><span data-stu-id="7f2f2-102">How to: Enable Column Reordering in the Windows Forms DataGridView Control Using the Designer</span></span>
<span data-ttu-id="7f2f2-103">Lorsque vous affichez les données affichées dans un contrôle de <xref:System.Windows.Forms.DataGridView> Windows Forms, les utilisateurs souhaitent parfois comparer les valeurs de colonnes spécifiques.</span><span class="sxs-lookup"><span data-stu-id="7f2f2-103">When viewing data displayed in a Windows Forms <xref:System.Windows.Forms.DataGridView> control, users sometimes want to compare the values in specific columns.</span></span> <span data-ttu-id="7f2f2-104">Cela peut être gênant si les colonnes sont très éloignées dans le contrôle, en particulier si les utilisateurs doivent faire défiler horizontalement vers l’avant pour voir toutes les colonnes qui les intéressent.</span><span class="sxs-lookup"><span data-stu-id="7f2f2-104">This can be inconvenient if the columns are widely separated in the control, especially if users must scroll back and forth horizontally in order to see all the columns they are interested in.</span></span> <span data-ttu-id="7f2f2-105">Vous pouvez faciliter la comparaison des valeurs de colonne en permettant à vos utilisateurs de réorganiser les colonnes.</span><span class="sxs-lookup"><span data-stu-id="7f2f2-105">You can make the task of comparing column values easier by enabling your users to reorder the columns.</span></span> <span data-ttu-id="7f2f2-106">Lorsque vous activez la réorganisation des colonnes, les utilisateurs peuvent déplacer une colonne vers une nouvelle position en faisant glisser l’en-tête de colonne avec la souris.</span><span class="sxs-lookup"><span data-stu-id="7f2f2-106">When you enable column reordering, users can move a column to a new position by dragging the column header with the mouse.</span></span>

 <span data-ttu-id="7f2f2-107">La procédure suivante requiert un projet d' **application Windows** avec un formulaire contenant un contrôle de <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="7f2f2-107">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="7f2f2-108">Pour plus d’informations sur la configuration d’un tel projet, consultez [Comment : créer un projet d’application Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project) et [Comment : ajouter des contrôles à des Windows Forms](how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="7f2f2-108">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>

## <a name="to-enable-column-reordering"></a><span data-ttu-id="7f2f2-109">Pour activer la réorganisation des colonnes</span><span class="sxs-lookup"><span data-stu-id="7f2f2-109">To enable column reordering</span></span>

- <span data-ttu-id="7f2f2-110">Cliquez sur le glyphe de balise active (![glyphe de balise active](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) dans le coin supérieur droit du contrôle <xref:System.Windows.Forms.DataGridView>, puis sélectionnez **activer la réorganisation des colonnes**.</span><span class="sxs-lookup"><span data-stu-id="7f2f2-110">Click the smart tag glyph (![Smart Tag Glyph](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) on the upper-right corner of the <xref:System.Windows.Forms.DataGridView> control, and then select **Enable Column Reordering**.</span></span>

## <a name="see-also"></a><span data-ttu-id="7f2f2-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7f2f2-111">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.AllowUserToOrderColumns%2A?displayProperty=nameWithType>
- [<span data-ttu-id="7f2f2-112">Guide pratique pour figer les colonnes du contrôle DataGridView Windows Forms à l'aide du concepteur</span><span class="sxs-lookup"><span data-stu-id="7f2f2-112">How to: Freeze Columns in the Windows Forms DataGridView Control Using the Designer</span></span>](freeze-columns-in-the-datagrid-using-the-designer.md)
- [<span data-ttu-id="7f2f2-113">Comment : créer un projet d’application Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7f2f2-113">How to: Create a Windows Forms application project</span></span>](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [<span data-ttu-id="7f2f2-114">Comment : ajouter des contrôles à des Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7f2f2-114">How to: Add Controls to Windows Forms</span></span>](how-to-add-controls-to-windows-forms.md)
