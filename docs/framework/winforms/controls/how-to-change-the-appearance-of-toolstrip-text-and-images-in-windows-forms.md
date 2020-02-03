---
title: 'Comment : modifier l’apparence du texte et des images ToolStrip'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStrip control [Windows Forms], appearance
- toolbars [Windows Forms], images
- examples [Windows Forms], toolbars
- toolbars [Windows Forms], appearance
- ToolStrip control [Windows Forms], images
- ToolStrip control [Windows Forms], text
- toolbars [Windows Forms], text
ms.assetid: d62dc9d1-2edd-4dfa-aed7-1335d6e13d86
ms.openlocfilehash: 7816e138e44554683c201895ece1f886ace8bfa6
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746596"
---
# <a name="how-to-change-the-appearance-of-toolstrip-text-and-images-in-windows-forms"></a>Comment : modifier l'apparence du texte et des images de ToolStrip dans les Windows Forms
Vous pouvez contrôler si le texte et les images sont affichés sur un <xref:System.Windows.Forms.ToolStripItem> et comment ils sont alignés les uns par rapport aux autres et le <xref:System.Windows.Forms.ToolStrip>.  
  
### <a name="to-define-what-is-displayed-on-a-toolstripitem"></a>Pour définir ce qui est affiché sur un ToolStripItem  
  
- Affectez à la propriété <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> la valeur souhaitée. Les possibilités sont `Image`, `ImageAndText`, `None`et `Text`. Par défaut, il s’agit de `ImageAndText`.  
  
    ```vb  
    ToolStripButton2.DisplayStyle = _  
        System.Windows.Forms.ToolStripItemDisplayStyle.Image  
    ```  
  
    ```csharp  
    toolStripButton2.DisplayStyle = System.Windows.Forms.ToolStripItemDisplayStyle.Image;  
    ```  
  
### <a name="to-align-text-on-a-toolstripitem"></a>Pour aligner du texte sur un ToolStripItem  
  
- Affectez à la propriété <xref:System.Windows.Forms.ToolStripItem.TextAlign%2A> la valeur souhaitée. Les possibilités sont n’importe quelle combinaison des touches haut, milieu et bas avec gauche, Centre et droite. Par défaut, il s’agit de `MiddleCenter`.  
  
    ```vb  
    ToolStripSplitButton1.TextAlign = _  
        System.Drawing.ContentAlignment.MiddleRight  
    ```  
  
    ```csharp  
    toolStripSplitButton1.TextAlign = System.Drawing.ContentAlignment.MiddleRight;  
    ```  
  
### <a name="to-align-an-image-on-a-toolstripitem"></a>Pour aligner une image sur un ToolStripItem  
  
- Affectez à la propriété <xref:System.Windows.Forms.ToolStripItem.ImageAlign%2A> la valeur souhaitée. Les possibilités sont n’importe quelle combinaison des touches haut, milieu et bas avec gauche, Centre et droite. Par défaut, il s’agit de `MiddleLeft`.  
  
    ```vb  
    ToolStripSplitButton1.ImageAlign = _  
        System.Drawing.ContentAlignment.MiddleRight  
    ```  
  
    ```csharp  
    toolStripSplitButton1.ImageAlign = System.Drawing.ContentAlignment.MiddleRight;  
    ```  
  
### <a name="to-define-how-toolstripitem-text-and-images-are-displayed-relative-to-each-other"></a>Pour définir le mode d’affichage du texte et des images ToolStripItem les unes par rapport aux autres  
  
- Affectez à la propriété <xref:System.Windows.Forms.ToolStripItem.TextImageRelation%2A> la valeur souhaitée. Les possibilités sont `ImageAboveText`, `ImageBeforeText`, `Overlay`, `TextAboveImage` et `TextBeforeImage`. Par défaut, il s’agit de `ImageBeforeText`.  
  
    ```vb  
    ToolStripButton1.TextImageRelation = _  
        System.Windows.Forms.TextImageRelation.ImageAboveText  
    ```  
  
    ```csharp  
    toolStripButton1.TextImageRelation = System.Windows.Forms.TextImageRelation.ImageAboveText;  
    ```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.ToolStrip>
- [Vue d’ensemble du contrôle ToolStrip](toolstrip-control-overview-windows-forms.md)
- [Architecture du contrôle ToolStrip](toolstrip-control-architecture.md)
- [Résumé de la technologie ToolStrip](toolstrip-technology-summary.md)
