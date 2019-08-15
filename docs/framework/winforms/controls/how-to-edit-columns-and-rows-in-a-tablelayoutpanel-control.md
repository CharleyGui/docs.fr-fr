---
title: 'Procédure : modifier des colonnes et des lignes dans un contrôle TableLayoutPanel'
ms.date: 03/30/2017
f1_keywords:
- net.ComponentModel.StyleCollectionEditor
helpviewer_keywords:
- columns [Windows Forms], editing
- TableLayoutPanel control [Windows Forms], editing
- rows [Windows Forms], editing
ms.assetid: c367ed43-40dc-49eb-9e0f-ba70e83dfec0
ms.openlocfilehash: 99ff3286592da0a097835b8f35d687475ca54fb0
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040291"
---
# <a name="how-to-edit-columns-and-rows-in-a-tablelayoutpanel-control"></a><span data-ttu-id="fd11a-102">Procédure : modifier des colonnes et des lignes dans un contrôle TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="fd11a-102">How to: Edit Columns and Rows in a TableLayoutPanel Control</span></span>

<span data-ttu-id="fd11a-103">Vous pouvez utiliser l’éditeur de collections du <xref:System.Windows.Forms.TableLayoutPanel> contrôle, appelé boîte de dialogue **styles de colonne et de ligne** , pour modifier les lignes et les colonnes de vos contrôles.</span><span class="sxs-lookup"><span data-stu-id="fd11a-103">You can use the collection editor of the <xref:System.Windows.Forms.TableLayoutPanel> control, called the **Column and Row Styles** dialog box, to edit the rows and columns of your controls.</span></span>

> [!NOTE]
> <span data-ttu-id="fd11a-104">Si vous souhaitez qu’un contrôle s’étende sur plusieurs lignes ou colonnes `RowSpan` , `ColumnSpan` définissez les propriétés et sur le contrôle.</span><span class="sxs-lookup"><span data-stu-id="fd11a-104">If you want a control to span multiple rows or columns, set the `RowSpan` and `ColumnSpan` properties on the control.</span></span> <span data-ttu-id="fd11a-105">Pour plus d’informations, consultez [Procédure pas à pas : Réorganisation des contrôles sur Windows Forms à l'](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)aide d’un TableLayoutPanel.</span><span class="sxs-lookup"><span data-stu-id="fd11a-105">For more information, see [Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).</span></span>
>
> <span data-ttu-id="fd11a-106">Si vous souhaitez aligner un contrôle dans une cellule ou si vous souhaitez étirer un contrôle dans une cellule, utilisez la propriété du <xref:System.Windows.Forms.Control.Anchor%2A> contrôle.</span><span class="sxs-lookup"><span data-stu-id="fd11a-106">If you want to align a control within a cell, or if you want a control to stretch within a cell, use the control's <xref:System.Windows.Forms.Control.Anchor%2A> property.</span></span> <span data-ttu-id="fd11a-107">Pour plus d’informations, consultez [Procédure pas à pas : Réorganisation des contrôles sur Windows Forms à l'](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)aide d’un TableLayoutPanel.</span><span class="sxs-lookup"><span data-stu-id="fd11a-107">For more information, see [Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).</span></span>

## <a name="to-edit-rows-and-columns"></a><span data-ttu-id="fd11a-108">Pour modifier des lignes et des colonnes</span><span class="sxs-lookup"><span data-stu-id="fd11a-108">To edit rows and columns</span></span>

1. <span data-ttu-id="fd11a-109">Faites glisser un contrôle <xref:System.Windows.Forms.TableLayoutPanel> de la **boîte à outils** vers le formulaire.</span><span class="sxs-lookup"><span data-stu-id="fd11a-109">Drag a <xref:System.Windows.Forms.TableLayoutPanel> control from the **Toolbox** onto your form.</span></span>

2. <span data-ttu-id="fd11a-110">Cliquez sur <xref:System.Windows.Forms.TableLayoutPanel> le glyphe de balise active du contrôle (![glyphe de balise active](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) et sélectionnez **modifier les lignes et les colonnes** pour ouvrir la boîte de dialogue Styles de ligne et de **colonne** .</span><span class="sxs-lookup"><span data-stu-id="fd11a-110">Click the <xref:System.Windows.Forms.TableLayoutPanel> control's smart tag glyph (![Smart Tag Glyph](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) and select **Edit Rows and Columns** to open the **Column and Row Styles** dialog box.</span></span> <span data-ttu-id="fd11a-111">Vous pouvez également cliquer avec le bouton <xref:System.Windows.Forms.TableLayoutPanel> droit sur le contrôle et sélectionner **modifier les lignes et les colonnes** dans le menu contextuel.</span><span class="sxs-lookup"><span data-stu-id="fd11a-111">You can also right click on the <xref:System.Windows.Forms.TableLayoutPanel> control and select **Edit Rows and Columns** from the shortcut menu.</span></span>

3. <span data-ttu-id="fd11a-112">Pour ajouter ou supprimer des colonnes, sélectionnez **colonnes** dans la zone de liste déroulante **type de membre** .</span><span class="sxs-lookup"><span data-stu-id="fd11a-112">To add or remove columns, select **Columns** from the **Member type** drop-down list box.</span></span>

4. <span data-ttu-id="fd11a-113">Pour ajouter ou supprimer des lignes, sélectionnez **lignes** dans la zone de liste déroulante **type de membre** .</span><span class="sxs-lookup"><span data-stu-id="fd11a-113">To add or remove rows, select **Rows** from the **Member type** drop-down list box.</span></span>

5. <span data-ttu-id="fd11a-114">Cliquez sur le bouton **Ajouter** pour ajouter une ligne ou une colonne à la fin de la liste des **membres** .</span><span class="sxs-lookup"><span data-stu-id="fd11a-114">Click the **Add** button to add a row or column to the end of the **Member** list.</span></span>

6. <span data-ttu-id="fd11a-115">Cliquez sur le bouton **Insérer** pour ajouter une ligne ou une colonne avant l’élément actuellement sélectionné dans la liste.</span><span class="sxs-lookup"><span data-stu-id="fd11a-115">Click the **Insert** button to add a row or column before the currently selected item in the list.</span></span>

7. <span data-ttu-id="fd11a-116">Si vous ajoutez une ligne ou une colonne, sélectionnez le **type de taille** pour la nouvelle ligne ou colonne.</span><span class="sxs-lookup"><span data-stu-id="fd11a-116">If you are adding a row or column, select the **Size Type** for the new row or column.</span></span> <span data-ttu-id="fd11a-117">Pour plus d'informations, consultez <xref:System.Windows.Forms.SizeType>.</span><span class="sxs-lookup"><span data-stu-id="fd11a-117">For more information, see <xref:System.Windows.Forms.SizeType>.</span></span>

8. <span data-ttu-id="fd11a-118">Pour supprimer une ligne ou une colonne, cliquez sur le bouton **supprimer** pour supprimer l’élément actuellement sélectionné dans la liste des **membres** .</span><span class="sxs-lookup"><span data-stu-id="fd11a-118">To remove a row or column, click the **Remove** button to delete the currently selected item in the **Member** list.</span></span>

## <a name="see-also"></a><span data-ttu-id="fd11a-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fd11a-119">See also</span></span>

- <xref:System.Windows.Forms.SizeType>
- [<span data-ttu-id="fd11a-120">TableLayoutPanel, contrôle</span><span class="sxs-lookup"><span data-stu-id="fd11a-120">TableLayoutPanel Control</span></span>](tablelayoutpanel-control-windows-forms.md)
