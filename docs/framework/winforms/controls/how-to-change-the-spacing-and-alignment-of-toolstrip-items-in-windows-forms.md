---
title: 'Comment : Modifier l’espacement et l’alignement des éléments ToolStrip'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStrip control [Windows Forms], aligning items
- examples [Windows Forms], toolbars
- toolbars [Windows Forms], aligning items
ms.assetid: cd483466-0f49-43df-addf-e2b5fcd64027
ms.openlocfilehash: 550ac1660a077e8d766a01bfa8d102c07f0fbfeb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182228"
---
# <a name="how-to-change-the-spacing-and-alignment-of-toolstrip-items-in-windows-forms"></a>Comment : modifier l'espacement et l'alignement d'éléments ToolStrip dans les Windows Forms
Le <xref:System.Windows.Forms.ToolStrip> contrôle prend pleinement en charge les caractéristiques <xref:System.Windows.Forms.ToolStripItem> de mise en page telles que <xref:System.Windows.Forms.ToolStrip>le dimensionnement, l’espacement des contrôles par rapport aux autres, l’agencement des contrôles sur le , et l’espacement des contrôles par rapport à la <xref:System.Windows.Forms.ToolStrip>.  
  
 Parce que la <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> valeur `true`par défaut de la propriété <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> est `false`, les contrôles sont dimensionnés automatiquement à moins que vous définissez la propriété à .  
  
### <a name="to-manually-size-a-toolstripitem"></a>Pour taille manueller un ToolStripItem  
  
1. Définissez <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> la `false` propriété pour le contrôle associé.  
  
    ```vb  
    ToolStripButton1.AutoSize = False  
    ```  
  
    ```csharp  
    toolStripButton1.AutoSize = false;  
    ```  
  
2. Réglez la <xref:System.Windows.Forms.ToolStripItem.Size%2A> propriété comme <xref:System.Windows.Forms.ToolStripItem>vous le souhaitez pour l’associé .  
  
### <a name="to-set-the-spacing-of-a-toolstripitem"></a>Pour définir l’espacement d’un ToolStripItem  
  
1. Insérez les valeurs souhaitées, en pixels, dans la <xref:System.Windows.Forms.ToolStripItem.Margin%2A> propriété du contrôle associé.  
  
     Les valeurs <xref:System.Windows.Forms.ToolStripItem.Margin%2A> de la propriété spécifient l’espacement entre l’élément et les éléments adjacents dans cet ordre: Gauche, Haut, Droite et En bas.  
  
    ```vb  
    ToolStripTextBox1.Margin = New System.Windows.Forms.Padding _  
        (3, 0, 3, 0)  
    ```  
  
    ```csharp  
    toolStripTextBox1.Margin = new System.Windows.Forms.Padding
        (3, 0, 3, 0);  
    ```  
  
### <a name="to-align-a-toolstripitem-to-the-right-side-of-the-toolstrip"></a>Pour aligner un ToolStripItem sur le côté droit de la piste d’outils  
  
1. Définissez <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> la <xref:System.Windows.Forms.ToolStripItemAlignment.Right> propriété pour le contrôle associé. Par défaut, <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> est <xref:System.Windows.Forms.ToolStripItemAlignment.Left>réglé à , qui aligne <xref:System.Windows.Forms.ToolStrip>les contrôles sur le côté gauche de la .  
  
    ```vb  
    ToolStripSplitButton1.Alignment = _  
        System.Windows.Forms.ToolStripItemAlignment.Right  
    ```  
  
    ```csharp  
    toolStripSplitButton1.Alignment =
        System.Windows.Forms.ToolStripItemAlignment.Right;  
    ```  
  
### <a name="to-arrange-toolstrip-items-on-the-toolstrip"></a>Pour organiser des articles ToolStrip sur le ToolStrip  
  
- Définissez <xref:System.Windows.Forms.ToolStrip.LayoutStyle%2A> la propriété <xref:System.Windows.Forms.ToolStripLayoutStyle> à la valeur de ce que vous voulez.  
  
    ```vb  
    ToolStripDropDown1.LayoutStyle = _  
        System.Windows.Forms.ToolStripLayoutStyle.Flow  
    ```  
  
    ```csharp  
    toolStripDropDown1.LayoutStyle =
        System.Windows.Forms.ToolStripLayoutStyle.Flow;  
    ```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.Control.Layout>
- <xref:System.Windows.Forms.ToolStrip.LayoutCompleted>
- <xref:System.Windows.Forms.ToolStrip.LayoutSettings%2A>
- <xref:System.Windows.Forms.ToolStripItem.TextImageRelation%2A>
- <xref:System.Windows.Forms.ToolStripItem.Placement%2A>
- <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A>
- [Vue d’ensemble du contrôle ToolStrip](toolstrip-control-overview-windows-forms.md)
- [Architecture du contrôle ToolStrip](toolstrip-control-architecture.md)
- [Résumé de la technologie ToolStrip](toolstrip-technology-summary.md)
