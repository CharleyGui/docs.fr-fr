---
title: 'Comment : modifier l’espacement et l’alignement des éléments ToolStrip'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStrip control [Windows Forms], aligning items
- examples [Windows Forms], toolbars
- toolbars [Windows Forms], aligning items
ms.assetid: cd483466-0f49-43df-addf-e2b5fcd64027
ms.openlocfilehash: 805fbac5fe33071006f29692d503e5c57eacd765
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746565"
---
# <a name="how-to-change-the-spacing-and-alignment-of-toolstrip-items-in-windows-forms"></a>Comment : modifier l'espacement et l'alignement d'éléments ToolStrip dans les Windows Forms
Le contrôle <xref:System.Windows.Forms.ToolStrip> prend entièrement en charge les fonctionnalités de disposition, telles que le dimensionnement, l’espacement des contrôles <xref:System.Windows.Forms.ToolStripItem> l’un par rapport à l’autre, la disposition des contrôles sur le <xref:System.Windows.Forms.ToolStrip>et l’espacement des contrôles par rapport au <xref:System.Windows.Forms.ToolStrip>.  
  
 Étant donné que la valeur par défaut de la propriété <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> est `true`, les contrôles sont dimensionnés automatiquement, sauf si vous affectez à la propriété <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> la valeur `false`.  
  
### <a name="to-manually-size-a-toolstripitem"></a>Pour dimensionner manuellement un ToolStripItem  
  
1. Affectez à la propriété <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> la valeur `false` pour le contrôle associé.  
  
    ```vb  
    ToolStripButton1.AutoSize = False  
    ```  
  
    ```csharp  
    toolStripButton1.AutoSize = false;  
    ```  
  
2. Définissez la propriété <xref:System.Windows.Forms.ToolStripItem.Size%2A> comme vous le souhaitez pour le <xref:System.Windows.Forms.ToolStripItem>associé.  
  
### <a name="to-set-the-spacing-of-a-toolstripitem"></a>Pour définir l’espacement d’un ToolStripItem  
  
1. Insérez les valeurs souhaitées, en pixels, dans la propriété <xref:System.Windows.Forms.ToolStripItem.Margin%2A> du contrôle associé.  
  
     Les valeurs de la propriété <xref:System.Windows.Forms.ToolStripItem.Margin%2A> spécifient l’espacement entre l’élément et les éléments adjacents dans l’ordre suivant : gauche, haut, droite et bas.  
  
    ```vb  
    ToolStripTextBox1.Margin = New System.Windows.Forms.Padding _  
        (3, 0, 3, 0)  
    ```  
  
    ```csharp  
    toolStripTextBox1.Margin = new System.Windows.Forms.Padding   
        (3, 0, 3, 0);  
    ```  
  
### <a name="to-align-a-toolstripitem-to-the-right-side-of-the-toolstrip"></a>Pour aligner un ToolStripItem sur le côté droit du ToolStrip  
  
1. Affectez à la propriété <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> la valeur <xref:System.Windows.Forms.ToolStripItemAlignment.Right> pour le contrôle associé. Par défaut, <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> a la valeur <xref:System.Windows.Forms.ToolStripItemAlignment.Left>, qui aligne les contrôles sur le côté gauche du <xref:System.Windows.Forms.ToolStrip>.  
  
    ```vb  
    ToolStripSplitButton1.Alignment = _  
        System.Windows.Forms.ToolStripItemAlignment.Right  
    ```  
  
    ```csharp  
    toolStripSplitButton1.Alignment =   
        System.Windows.Forms.ToolStripItemAlignment.Right;  
    ```  
  
### <a name="to-arrange-toolstrip-items-on-the-toolstrip"></a>Pour réorganiser des éléments ToolStrip sur le ToolStrip  
  
- Affectez à la propriété <xref:System.Windows.Forms.ToolStrip.LayoutStyle%2A> la valeur de <xref:System.Windows.Forms.ToolStripLayoutStyle> souhaitée.  
  
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
