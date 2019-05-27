---
title: 'Procédure : afficher la liste des polices avec le composant FontDialog'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- fonts [Windows Forms], showing list
- FontDialog component [Windows Forms]
- fonts [Windows Forms], attributes
- Font property [Windows Forms], setting with FontDialog component
- Font dialog box [Windows Forms], displaying
- fonts [Windows Forms], selecting
ms.assetid: 35692c1b-0937-4b7a-9207-1ae6bdc244a0
ms.openlocfilehash: 05e9b5e1280d0318354b0d47f4d78f7ec1c5f4e7
ms.sourcegitcommit: 7e129d879ddb42a8b4334eee35727afe3d437952
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66053449"
---
# <a name="how-to-show-a-font-list-with-the-fontdialog-component"></a>Procédure : afficher la liste des polices avec le composant FontDialog
Le [FontDialog](fontdialog-component-windows-forms.md) composant permet aux utilisateurs de sélectionner une police, mais aussi modifier ses aspects de l’affichage, telles que son poids et la taille.  
  
 La police sélectionnée dans la boîte de dialogue est retournée dans le <xref:System.Windows.Forms.FontDialog.Font%2A> propriété. Par conséquent, en tirant parti de la police sélectionnée par l’utilisateur est aussi simple que la lecture d’une propriété.  
  
### <a name="to-select-font-properties-using-the-fontdialog-component"></a>Pour sélectionner les propriétés de police à l’aide du composant FontDialog  
  
1. Afficher la boîte de dialogue à l’aide de la <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> (méthode).  
  
2. Utilisez le <xref:System.Windows.Forms.DialogResult> propriété afin de déterminer comment la boîte de dialogue a été fermée.  
  
3. Utilisez le <xref:System.Windows.Forms.FontDialog.Font%2A> propriété à définir la police souhaitée.  
  
     Dans l’exemple ci-dessous, le <xref:System.Windows.Forms.Button> du contrôle <xref:System.Windows.Forms.Control.Click> Gestionnaire d’événements ouvre un <xref:System.Windows.Forms.FontDialog> composant. Quand une police est sélectionné et l’utilisateur clique sur **OK**, le <xref:System.Windows.Forms.FontDialog.Font%2A> propriété d’un <xref:System.Windows.Forms.TextBox> contrôle qui se trouve sur le formulaire est défini sur la police choisie. L’exemple suppose que votre formulaire contient un <xref:System.Windows.Forms.Button> contrôle, un <xref:System.Windows.Forms.TextBox> contrôle et un <xref:System.Windows.Forms.FontDialog> composant.  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, _  
       ByVal e As System.EventArgs) Handles Button1.Click  
       If FontDialog1.ShowDialog() = DialogResult.OK Then  
          TextBox1.Font = FontDialog1.Font  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)  
    {  
       if(fontDialog1.ShowDialog() == DialogResult.OK)  
       {  
          textBox1.Font = fontDialog1.Font;  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       void button1_Click(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          if(fontDialog1->ShowDialog() == DialogResult::OK)  
          {  
             textBox1->Font = fontDialog1->Font;  
          }  
       }  
    ```  
  
     (Visual C# et Visual C++) Placez le code suivant dans le constructeur du formulaire pour inscrire le Gestionnaire d’événements.  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    button1->Click += gcnew System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.FontDialog>
- [FontDialog, composant](fontdialog-component-windows-forms.md)
