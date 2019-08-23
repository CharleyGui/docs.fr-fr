---
title: 'Procédure : créer du texte de taille variable dans un contrôle ComboBox'
ms.date: 03/30/2017
dev_langs:
- vb
helpviewer_keywords:
- text [Windows Forms], drawing in combo boxes
- examples [Windows Forms], ComboBox control
- combo boxes [Windows Forms], drawing text
- ComboBox control [Windows Forms], examples [C#]
- ComboBox control [Windows Forms], drawing custom text
ms.assetid: ce39b9ea-e626-49fe-bd5a-f567f6d157df
ms.openlocfilehash: 7c0dc40f6cac0af1f88e72089865caa3a17fcf2a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69914748"
---
# <a name="how-to-create-variable-sized-text-in-a-combobox-control"></a>Procédure : créer du texte de taille variable dans un contrôle ComboBox
Cet exemple illustre un dessin personnalisé de texte dans <xref:System.Windows.Forms.ComboBox> un contrôle. Lorsqu’un élément répond à un certain critère, il est dessiné dans une police plus grande et transformé en rouge.  
  
## <a name="example"></a>Exemples  
  
```vb  
Private Sub ComboBox1_MeasureItem(ByVal sender As Object, ByVal e As _  
System.Windows.Forms.MeasureItemEventArgs) Handles ComboBox1.MeasureItem  
    Dim bFont As New Font("Arial", 8, FontStyle.Bold)  
    Dim lFont As New Font("Arial", 12, FontStyle.Bold)  
    Dim siText As SizeF  
  
    If ComboBox1.Items().Item(e.Index) = "Two" Then  
        siText = e.Graphics.MeasureString(ComboBox1.Items().Item(e.Index), _  
lFont)  
    Else  
        siText = e.Graphics.MeasureString(ComboBox1.Items().Item(e.Index), bFont)  
    End If  
  
    e.ItemHeight = siText.Height  
    e.ItemWidth = siText.Width  
End Sub  
  
Private Sub ComboBox1_DrawItem(ByVal sender As Object, ByVal e As _  
System.Windows.Forms.DrawItemEventArgs) Handles ComboBox1.DrawItem  
    Dim g As Graphics = e.Graphics  
    Dim bFont As New Font("Arial", 8, FontStyle.Bold)  
    Dim lFont As New Font("Arial", 12, FontStyle.Bold)  
  
    If ComboBox1.Items().Item(e.Index) = "Two" Then  
        g.DrawString(ComboBox1.Items.Item(e.Index), lfont, Brushes.Red, _  
e.Bounds.X, e.Bounds.Y)  
    Else  
        g.DrawString(ComboBox1.Items.Item(e.Index), bFont, Brushes.Black, e.Bounds.X, e.Bounds.Y)  
    End If  
End Sub  
```  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Cet exemple nécessite :  
  
- Un Windows Form.  
  
- Contrôle nommé `ListBox1` avec trois éléments dans la <xref:System.Windows.Forms.ComboBox.Items%2A> propriété. <xref:System.Windows.Forms.ComboBox> Dans cet exemple, les trois éléments sont nommés `"One", Two", and Three"`. La <xref:System.Windows.Forms.ComboBox.DrawMode%2A> propriété de `ComboBox1` doit avoir la valeur <xref:System.Windows.Forms.DrawMode.OwnerDrawVariable>.  
  
    > [!NOTE]
    > Cette technique est également applicable au <xref:System.Windows.Forms.ListBox> contrôle: vous pouvez remplacer un <xref:System.Windows.Forms.ListBox> pour le <xref:System.Windows.Forms.ComboBox>.  
  
- Références aux espaces de noms <xref:System.Windows.Forms?displayProperty=nameWithType> et <xref:System.Drawing?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.ComboBox.DrawItem>
- <xref:System.Windows.Forms.DrawItemEventArgs>
- <xref:System.Windows.Forms.ComboBox.MeasureItem>
- [Contrôles avec prise en charge intégrée du dessin owner-drawn](controls-with-built-in-owner-drawing-support.md)
- [ListBox, contrôle](listbox-control-windows-forms.md)
- [ComboBox, contrôle](combobox-control-windows-forms.md)
