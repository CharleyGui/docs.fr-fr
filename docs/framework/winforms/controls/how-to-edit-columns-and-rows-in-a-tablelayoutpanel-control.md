---
title: 'Comment : modifier des colonnes et des lignes dans un contrôle TableLayoutPanel'
description: Découvrez comment utiliser la boîte de dialogue Styles de lignes et de colonnes pour modifier les lignes et les colonnes de vos contrôles Windows Forms.
ms.date: 03/30/2017
f1_keywords:
- net.ComponentModel.StyleCollectionEditor
helpviewer_keywords:
- columns [Windows Forms], editing
- TableLayoutPanel control [Windows Forms], editing
- rows [Windows Forms], editing
ms.assetid: c367ed43-40dc-49eb-9e0f-ba70e83dfec0
ms.openlocfilehash: cfd2ca4be5d5a2658a9a129d911f1dba9670ccfd
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619349"
---
# <a name="how-to-edit-columns-and-rows-in-a-tablelayoutpanel-control"></a><span data-ttu-id="ff681-103">Comment : modifier des colonnes et des lignes dans un contrôle TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="ff681-103">How to: Edit Columns and Rows in a TableLayoutPanel Control</span></span>

<span data-ttu-id="ff681-104">Vous pouvez utiliser l’éditeur de collections du <xref:System.Windows.Forms.TableLayoutPanel> contrôle, appelé boîte de dialogue **styles de colonne et de ligne** , pour modifier les lignes et les colonnes de vos contrôles.</span><span class="sxs-lookup"><span data-stu-id="ff681-104">You can use the collection editor of the <xref:System.Windows.Forms.TableLayoutPanel> control, called the **Column and Row Styles** dialog box, to edit the rows and columns of your controls.</span></span>

> [!NOTE]
> <span data-ttu-id="ff681-105">Si vous souhaitez qu’un contrôle s’étende sur plusieurs lignes ou colonnes, définissez les `RowSpan` `ColumnSpan` Propriétés et sur le contrôle.</span><span class="sxs-lookup"><span data-stu-id="ff681-105">If you want a control to span multiple rows or columns, set the `RowSpan` and `ColumnSpan` properties on the control.</span></span> <span data-ttu-id="ff681-106">Pour plus d'informations, consultez [Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).</span><span class="sxs-lookup"><span data-stu-id="ff681-106">For more information, see [Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).</span></span>
>
> <span data-ttu-id="ff681-107">Si vous souhaitez aligner un contrôle dans une cellule ou si vous souhaitez étirer un contrôle dans une cellule, utilisez la propriété du contrôle <xref:System.Windows.Forms.Control.Anchor%2A> .</span><span class="sxs-lookup"><span data-stu-id="ff681-107">If you want to align a control within a cell, or if you want a control to stretch within a cell, use the control's <xref:System.Windows.Forms.Control.Anchor%2A> property.</span></span> <span data-ttu-id="ff681-108">Pour plus d'informations, consultez [Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).</span><span class="sxs-lookup"><span data-stu-id="ff681-108">For more information, see [Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).</span></span>

## <a name="to-edit-rows-and-columns"></a><span data-ttu-id="ff681-109">Pour modifier des lignes et des colonnes</span><span class="sxs-lookup"><span data-stu-id="ff681-109">To edit rows and columns</span></span>

1. <span data-ttu-id="ff681-110">Faites glisser un contrôle <xref:System.Windows.Forms.TableLayoutPanel> de la **boîte à outils** vers le formulaire.</span><span class="sxs-lookup"><span data-stu-id="ff681-110">Drag a <xref:System.Windows.Forms.TableLayoutPanel> control from the **Toolbox** onto your form.</span></span>

2. <span data-ttu-id="ff681-111">Cliquez sur le <xref:System.Windows.Forms.TableLayoutPanel> glyphe actions du concepteur du contrôle ( ![ petite flèche noire ](./media/designer-actions-glyph.gif) ) et sélectionnez **modifier les lignes et les colonnes** pour ouvrir la boîte de dialogue Styles de ligne et de **colonne** .</span><span class="sxs-lookup"><span data-stu-id="ff681-111">Click the <xref:System.Windows.Forms.TableLayoutPanel> control's designer actions glyph (![Small black arrow](./media/designer-actions-glyph.gif)) and select **Edit Rows and Columns** to open the **Column and Row Styles** dialog box.</span></span> <span data-ttu-id="ff681-112">Vous pouvez également cliquer avec le bouton droit sur le <xref:System.Windows.Forms.TableLayoutPanel> contrôle et sélectionner **modifier les lignes et les colonnes** dans le menu contextuel.</span><span class="sxs-lookup"><span data-stu-id="ff681-112">You can also right click on the <xref:System.Windows.Forms.TableLayoutPanel> control and select **Edit Rows and Columns** from the shortcut menu.</span></span>

3. <span data-ttu-id="ff681-113">Pour ajouter ou supprimer des colonnes, sélectionnez **colonnes** dans la zone de liste déroulante **type de membre** .</span><span class="sxs-lookup"><span data-stu-id="ff681-113">To add or remove columns, select **Columns** from the **Member type** drop-down list box.</span></span>

4. <span data-ttu-id="ff681-114">Pour ajouter ou supprimer des lignes, sélectionnez **lignes** dans la zone de liste déroulante **type de membre** .</span><span class="sxs-lookup"><span data-stu-id="ff681-114">To add or remove rows, select **Rows** from the **Member type** drop-down list box.</span></span>

5. <span data-ttu-id="ff681-115">Cliquez sur le bouton **Ajouter** pour ajouter une ligne ou une colonne à la fin de la liste des **membres** .</span><span class="sxs-lookup"><span data-stu-id="ff681-115">Click the **Add** button to add a row or column to the end of the **Member** list.</span></span>

6. <span data-ttu-id="ff681-116">Cliquez sur le bouton **Insérer** pour ajouter une ligne ou une colonne avant l’élément actuellement sélectionné dans la liste.</span><span class="sxs-lookup"><span data-stu-id="ff681-116">Click the **Insert** button to add a row or column before the currently selected item in the list.</span></span>

7. <span data-ttu-id="ff681-117">Si vous ajoutez une ligne ou une colonne, sélectionnez le **type de taille** pour la nouvelle ligne ou colonne.</span><span class="sxs-lookup"><span data-stu-id="ff681-117">If you are adding a row or column, select the **Size Type** for the new row or column.</span></span> <span data-ttu-id="ff681-118">Pour plus d’informations, consultez <xref:System.Windows.Forms.SizeType>.</span><span class="sxs-lookup"><span data-stu-id="ff681-118">For more information, see <xref:System.Windows.Forms.SizeType>.</span></span>

8. <span data-ttu-id="ff681-119">Pour supprimer une ligne ou une colonne, cliquez sur le bouton **supprimer** pour supprimer l’élément actuellement sélectionné dans la liste des **membres** .</span><span class="sxs-lookup"><span data-stu-id="ff681-119">To remove a row or column, click the **Remove** button to delete the currently selected item in the **Member** list.</span></span>

## <a name="see-also"></a><span data-ttu-id="ff681-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ff681-120">See also</span></span>

- <xref:System.Windows.Forms.SizeType>
- [<span data-ttu-id="ff681-121">TableLayoutPanel, contrôle</span><span class="sxs-lookup"><span data-stu-id="ff681-121">TableLayoutPanel Control</span></span>](tablelayoutpanel-control-windows-forms.md)
