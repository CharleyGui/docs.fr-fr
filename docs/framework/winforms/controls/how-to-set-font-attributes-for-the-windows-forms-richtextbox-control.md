---
title: Définir les attributs de police du contrôle RichTextBox
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- .rtf files [Windows Forms], formatting in RichTextBox control
- fonts [Windows Forms], changing attributes in RichTextBox control
- RTF files [Windows Forms], formatting in RichTextBox control
- RichTextBox control [Windows Forms], setting font attributes
- text [Windows Forms]
- text boxes [Windows Forms], formatting text
- formatting [Windows Forms]
ms.assetid: 2bc23ddb-0529-4489-a1a2-ad253cb43f9a
ms.openlocfilehash: f27256c155223df576ee3c42e6bf65270c870b0f
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744854"
---
# <a name="how-to-set-font-attributes-for-the-windows-forms-richtextbox-control"></a>Guide pratique pour définir les attributs de police du contrôle RichTextBox Windows Forms
Le contrôle Windows Forms <xref:System.Windows.Forms.RichTextBox> propose de nombreuses options de mise en forme du texte qu’il affiche. Vous pouvez mettre les caractères sélectionnés en gras, soulignés ou en italiques à l’aide de la propriété <xref:System.Windows.Forms.RichTextBox.SelectionFont%2A>. Vous pouvez également utiliser cette propriété pour changer la taille et la police des caractères sélectionnés. La propriété <xref:System.Windows.Forms.RichTextBox.SelectionColor%2A> vous permet de modifier la couleur des caractères sélectionnés.  
  
### <a name="to-change-the-appearance-of-characters"></a>Pour changer l’apparence de caractères  
  
1. Affectez à la propriété <xref:System.Windows.Forms.RichTextBox.SelectionFont%2A> une police appropriée.  
  
     Pour permettre aux utilisateurs de définir la famille de polices, la taille et la police d’une application, vous devez généralement utiliser le composant <xref:System.Windows.Forms.FontDialog>. Pour une vue d’ensemble, consultez [Vue d’ensemble du composant FontDialog](fontdialog-component-overview-windows-forms.md).  
  
2. Définissez la propriété <xref:System.Windows.Forms.RichTextBox.SelectionColor%2A> sur une couleur appropriée.  
  
     Pour permettre aux utilisateurs de définir la couleur dans une application, vous devez généralement utiliser le composant <xref:System.Windows.Forms.ColorDialog>. Pour une vue d’ensemble, consultez [Vue d’ensemble du composant ColorDialog](colordialog-component-overview-windows-forms.md).  
  
    ```vb  
    RichTextBox1.SelectionFont = New Font("Tahoma", 12, FontStyle.Bold)  
    RichTextBox1.SelectionColor = System.Drawing.Color.Red  
    ```  
  
    ```csharp  
    richTextBox1.SelectionFont = new Font("Tahoma", 12, FontStyle.Bold);  
    richTextBox1.SelectionColor = System.Drawing.Color.Red;  
    ```  
  
    ```cpp  
    richTextBox1->SelectionFont =  
       gcnew System::Drawing::Font("Tahoma", 12, FontStyle::Bold);  
    richTextBox1->SelectionColor = System::Drawing::Color::Red;  
    ```  
  
    > [!NOTE]
    > Ces propriétés affectent uniquement le texte sélectionné ou, si aucun texte n’est sélectionné, le texte tapé à l’emplacement actif du point d’insertion. Pour plus d’informations sur la sélection de texte par programmation, consultez <xref:System.Windows.Forms.TextBoxBase.Select%2A>.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.RichTextBox>
- [RichTextBox, contrôle](richtextbox-control-windows-forms.md)
- [Contrôles à utiliser dans les Windows Forms](controls-to-use-on-windows-forms.md)
