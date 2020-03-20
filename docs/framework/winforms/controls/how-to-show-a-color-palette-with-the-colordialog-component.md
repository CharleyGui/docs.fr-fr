---
title: "Comment : afficher une palette de couleurs à l'aide du composant ColorDialog"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- palettes [Windows Forms], showing color
- color dialog box [Windows Forms], showing color palettes
- colors [Windows Forms], allowing users to select
- color palettes [Windows Forms], dialog box
- ColorDialog component [Windows Forms], showing color palettes
- color palettes [Windows Forms], showing in ColorDialog component
- colors [Windows Forms], showing palettes
ms.assetid: ee050f61-dbc8-4436-ba22-51360981ab48
ms.openlocfilehash: 0406ef7a32678bd149c0024348a7adf1f0b72926
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141781"
---
# <a name="how-to-show-a-color-palette-with-the-colordialog-component"></a>Comment : afficher une palette de couleurs à l'aide du composant ColorDialog
Le composant [ColorDialog](colordialog-component-windows-forms.md) affiche une palette de couleurs et renvoie une propriété contenant la couleur choisie par l’utilisateur.  
  
### <a name="to-choose-a-color-using-the-colordialog-component"></a>Pour choisir une couleur à l’aide du composant ColorDialog  
  
1. Affichez la boîte <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> de dialogue à l’aide de la méthode.  
  
2. Utilisez <xref:System.Windows.Forms.DialogResult> la propriété pour déterminer comment la boîte de dialogue a été fermée.  
  
3. Utilisez <xref:System.Windows.Forms.ColorDialog.Color%2A> la propriété <xref:System.Windows.Forms.ColorDialog> du composant pour définir la couleur choisie.  
  
     Dans l’exemple <xref:System.Windows.Forms.Button> ci-dessous, le gestionnaire d’événements du <xref:System.Windows.Forms.Control.Click> contrôle ouvre un <xref:System.Windows.Forms.ColorDialog> composant. Lorsqu’une couleur est choisie et que <xref:System.Windows.Forms.Button> l’utilisateur clique **sur OK,** la couleur de fond du contrôle est réglée sur la couleur choisie. L’exemple suppose que <xref:System.Windows.Forms.Button> votre formulaire <xref:System.Windows.Forms.ColorDialog> a un contrôle et un composant.  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, _  
    ByVal e As System.EventArgs) Handles Button1.Click  
       If ColorDialog1.ShowDialog() = DialogResult.OK Then  
          Button1.BackColor = ColorDialog1.Color  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)  
    {  
       if(colorDialog1.ShowDialog() == DialogResult.OK)  
       {  
          button1.BackColor = colorDialog1.Color;  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       void button1_Click(System::Object ^ sender,
          System::EventArgs ^ e)  
       {  
          if(colorDialog1->ShowDialog() == DialogResult::OK)  
          {  
             button1->BackColor = colorDialog1->Color;  
          }  
       }  
    ```  
  
     (Visual C, Visual CMMD) Placez le code suivant dans le constructeur du formulaire pour enregistrer le gestionnaire de l’événement.  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click +=
       gcnew System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.ColorDialog>
- [ColorDialog, composant](colordialog-component-windows-forms.md)
