---
title: 'Procédure : définir des attributs de police pour le contrôle RichTextBox Windows Forms'
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
ms.openlocfilehash: 4919e94c23b1a67680ea0f360304ee0f75c7f425
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963221"
---
# <a name="how-to-set-font-attributes-for-the-windows-forms-richtextbox-control"></a>Procédure : définir des attributs de police pour le contrôle RichTextBox Windows Forms
Le contrôle <xref:System.Windows.Forms.RichTextBox> Windows Forms possède de nombreuses options de mise en forme du texte qu’il affiche. Vous pouvez mettre les caractères sélectionnés en gras, soulignés ou en italiques à l' <xref:System.Windows.Forms.RichTextBox.SelectionFont%2A> aide de la propriété. Vous pouvez également utiliser cette propriété pour changer la taille et la police des caractères sélectionnés. La <xref:System.Windows.Forms.RichTextBox.SelectionColor%2A> propriété vous permet de modifier la couleur des caractères sélectionnés.  
  
### <a name="to-change-the-appearance-of-characters"></a>Pour changer l’apparence de caractères  
  
1. Affectez <xref:System.Windows.Forms.RichTextBox.SelectionFont%2A> à la propriété une police appropriée.  
  
     Pour permettre aux utilisateurs de définir la famille de polices, la taille et la police d’une application, vous devez <xref:System.Windows.Forms.FontDialog> généralement utiliser le composant. Pour une vue d’ensemble, consultez [Vue d’ensemble du composant FontDialog](fontdialog-component-overview-windows-forms.md).  
  
2. Affectez <xref:System.Windows.Forms.RichTextBox.SelectionColor%2A> à la propriété une couleur appropriée.  
  
     Pour permettre aux utilisateurs de définir la couleur dans une application, vous devez généralement utiliser <xref:System.Windows.Forms.ColorDialog> le composant. Pour une vue d’ensemble, consultez [Vue d’ensemble du composant ColorDialog](colordialog-component-overview-windows-forms.md).  
  
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
    > Ces propriétés affectent uniquement le texte sélectionné ou, si aucun texte n’est sélectionné, le texte tapé à l’emplacement actif du point d’insertion. Pour plus d’informations sur la sélection de texte par <xref:System.Windows.Forms.TextBoxBase.Select%2A>programmation, consultez.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.RichTextBox>
- [RichTextBox, contrôle](richtextbox-control-windows-forms.md)
- [Contrôles à utiliser dans les Windows Forms](controls-to-use-on-windows-forms.md)
