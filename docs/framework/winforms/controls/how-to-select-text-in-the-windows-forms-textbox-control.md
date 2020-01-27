---
title: Sélectionner du texte dans le contrôle TextBox
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- TextBox control [Windows Forms], selecting text programmatically
- text boxes [Windows Forms], selecting text programmatically
- text [Windows Forms], selecting in text boxes programmatically
ms.assetid: 8c591546-6a01-45c7-8e03-f78431f903b1
ms.openlocfilehash: 8a32e40f14ddae6f8ddcaa6d62337329df6fde26
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745317"
---
# <a name="how-to-select-text-in-the-windows-forms-textbox-control"></a>Comment : sélectionner du texte dans le contrôle TextBox Windows Forms
Vous pouvez sélectionner du texte par programmation dans le contrôle Windows Forms <xref:System.Windows.Forms.TextBox>. Par exemple, si vous créez une fonction qui recherche du texte pour une chaîne particulière, vous pouvez sélectionner le texte pour alerter visuellement le lecteur de la position de la chaîne trouvée.  
  
### <a name="to-select-text-programmatically"></a>Pour sélectionner du texte par programmation  
  
1. Définissez la propriété <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> au début du texte que vous souhaitez sélectionner.  
  
     La propriété <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> est un nombre qui indique le point d’insertion dans la chaîne de texte, 0 étant la position la plus à gauche. Si la propriété <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> est définie sur une valeur supérieure ou égale au nombre de caractères dans la zone de texte, le point d’insertion est placé après le dernier caractère.  
  
2. Affectez à la propriété <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> la longueur du texte que vous souhaitez sélectionner.  
  
     La propriété <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> est une valeur numérique qui définit la largeur du point d’insertion. La définition de la <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> sur un nombre supérieur à 0 provoque la sélection de ce nombre de caractères, en commençant par le point d’insertion actuel.  
  
3. Facultatif Accédez au texte sélectionné par le biais de la propriété <xref:System.Windows.Forms.TextBoxBase.SelectedText%2A>.  
  
     Le code ci-dessous sélectionne le contenu d’une zone de texte lorsque l’événement <xref:System.Windows.Forms.Control.Enter> du contrôle se produit. Cet exemple vérifie si la zone de texte a une valeur pour la propriété <xref:System.Windows.Forms.TextBox.Text%2A> qui n’est pas `null` ou une chaîne vide. Lorsque la zone de texte reçoit le focus, le texte actuel de la zone de texte est sélectionné. Le gestionnaire d’événements `TextBox1_Enter` doit être lié au contrôle ; Pour plus d’informations, consultez [Comment : créer des gestionnaires d’événements au moment de l’exécution pour Windows Forms](../how-to-create-event-handlers-at-run-time-for-windows-forms.md).  
  
     Pour tester cet exemple, appuyez sur la touche Tab jusqu’à ce que la zone de texte ait le focus. Si vous cliquez dans la zone de texte, le texte est désélectionné.  
  
    ```vb  
    Private Sub TextBox1_Enter(ByVal sender As Object, ByVal e As System.EventArgs) Handles TextBox1.Enter  
       If (Not String.IsNullOrEmpty(TextBox1.Text)) Then  
          TextBox1.SelectionStart = 0  
          TextBox1.SelectionLength = TextBox1.Text.Length  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void textBox1_Enter(object sender, System.EventArgs e){  
       if (!String.IsNullOrEmpty(textBox1.Text))  
       {  
          textBox1.SelectionStart = 0;  
          textBox1.SelectionLength = textBox1.Text.Length;  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       void textBox1_Enter(System::Object ^ sender,  
          System::EventArgs ^ e) {  
       if (!System::String::IsNullOrEmpty(textBox1->Text))  
       {  
          textBox1->SelectionStart = 0;  
          textBox1->SelectionLength = textBox1->Text->Length;  
       }  
    }  
    ```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.TextBox>
- [Vue d’ensemble du contrôle TextBox](textbox-control-overview-windows-forms.md)
- [Guide pratique pour contrôler le point d’insertion dans un contrôle TextBox Windows Forms](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [Guide pratique pour créer une zone de texte pour mot de passe avec le contrôle TextBox Windows Forms](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [Guide pratique pour créer une zone de texte en lecture seule](how-to-create-a-read-only-text-box-windows-forms.md)
- [Guide pratique pour insérer des guillemets dans une chaîne](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [Guide pratique pour afficher des lignes multiples dans le contrôle TextBox Windows Forms](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [TextBox, contrôle](textbox-control-windows-forms.md)
