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
# <a name="how-to-edit-columns-and-rows-in-a-tablelayoutpanel-control"></a>Procédure : modifier des colonnes et des lignes dans un contrôle TableLayoutPanel

Vous pouvez utiliser l’éditeur de collections du <xref:System.Windows.Forms.TableLayoutPanel> contrôle, appelé boîte de dialogue **styles de colonne et de ligne** , pour modifier les lignes et les colonnes de vos contrôles.

> [!NOTE]
> Si vous souhaitez qu’un contrôle s’étende sur plusieurs lignes ou colonnes `RowSpan` , `ColumnSpan` définissez les propriétés et sur le contrôle. Pour plus d’informations, consultez [Procédure pas à pas : Réorganisation des contrôles sur Windows Forms à l'](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)aide d’un TableLayoutPanel.
>
> Si vous souhaitez aligner un contrôle dans une cellule ou si vous souhaitez étirer un contrôle dans une cellule, utilisez la propriété du <xref:System.Windows.Forms.Control.Anchor%2A> contrôle. Pour plus d’informations, consultez [Procédure pas à pas : Réorganisation des contrôles sur Windows Forms à l'](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)aide d’un TableLayoutPanel.

## <a name="to-edit-rows-and-columns"></a>Pour modifier des lignes et des colonnes

1. Faites glisser un contrôle <xref:System.Windows.Forms.TableLayoutPanel> de la **boîte à outils** vers le formulaire.

2. Cliquez sur <xref:System.Windows.Forms.TableLayoutPanel> le glyphe de balise active du contrôle (![glyphe de balise active](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) et sélectionnez **modifier les lignes et les colonnes** pour ouvrir la boîte de dialogue Styles de ligne et de **colonne** . Vous pouvez également cliquer avec le bouton <xref:System.Windows.Forms.TableLayoutPanel> droit sur le contrôle et sélectionner **modifier les lignes et les colonnes** dans le menu contextuel.

3. Pour ajouter ou supprimer des colonnes, sélectionnez **colonnes** dans la zone de liste déroulante **type de membre** .

4. Pour ajouter ou supprimer des lignes, sélectionnez **lignes** dans la zone de liste déroulante **type de membre** .

5. Cliquez sur le bouton **Ajouter** pour ajouter une ligne ou une colonne à la fin de la liste des **membres** .

6. Cliquez sur le bouton **Insérer** pour ajouter une ligne ou une colonne avant l’élément actuellement sélectionné dans la liste.

7. Si vous ajoutez une ligne ou une colonne, sélectionnez le **type de taille** pour la nouvelle ligne ou colonne. Pour plus d'informations, consultez <xref:System.Windows.Forms.SizeType>.

8. Pour supprimer une ligne ou une colonne, cliquez sur le bouton **supprimer** pour supprimer l’élément actuellement sélectionné dans la liste des **membres** .

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.SizeType>
- [TableLayoutPanel, contrôle](tablelayoutpanel-control-windows-forms.md)
