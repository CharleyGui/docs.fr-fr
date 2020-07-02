---
title: Sélectionner du texte dans le contrôle TextBox
description: Découvrez comment sélectionner du texte par programmation dans le contrôle Windows Forms TextBox. Découvrez également comment alerter visuellement le lecteur de la position de la chaîne trouvée.
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
ms.openlocfilehash: b8fdaff76461c4d6766dfc6afaef5e814d982834
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621559"
---
# <a name="how-to-select-text-in-the-windows-forms-textbox-control"></a>Comment : sélectionner du texte dans le contrôle TextBox Windows Forms
Vous pouvez sélectionner du texte par programmation dans le <xref:System.Windows.Forms.TextBox> contrôle Windows Forms. Par exemple, si vous créez une fonction qui recherche du texte pour une chaîne particulière, vous pouvez sélectionner le texte pour alerter visuellement le lecteur de la position de la chaîne trouvée.  
  
### <a name="to-select-text-programmatically"></a>Pour sélectionner du texte par programmation  
  
1. Définissez la <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> propriété au début du texte que vous souhaitez sélectionner.  
  
     La <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> propriété est un nombre qui indique le point d’insertion dans la chaîne de texte, 0 étant la position la plus à gauche. Si la <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> propriété est définie sur une valeur supérieure ou égale au nombre de caractères dans la zone de texte, le point d’insertion est placé après le dernier caractère.  
  
2. Affectez <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> à la propriété la longueur du texte que vous souhaitez sélectionner.  
  
     La <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> propriété est une valeur numérique qui définit la largeur du point d’insertion. La définition <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> de sur un nombre supérieur à 0 provoque la sélection du nombre de caractères, en commençant par le point d’insertion actuel.  
  
3. Facultatif Accédez au texte sélectionné par le biais de la <xref:System.Windows.Forms.TextBoxBase.SelectedText%2A> propriété.  
  
     Le code ci-dessous sélectionne le contenu d’une zone de texte lorsque l’événement du contrôle <xref:System.Windows.Forms.Control.Enter> se produit. Cet exemple vérifie si la zone de texte a une valeur pour la <xref:System.Windows.Forms.TextBox.Text%2A> propriété qui n’est pas `null` ou une chaîne vide. Lorsque la zone de texte reçoit le focus, le texte actuel de la zone de texte est sélectionné. Le `TextBox1_Enter` Gestionnaire d’événements doit être lié au contrôle. pour plus d’informations, consultez [Comment : créer des gestionnaires d’événements au moment de l’exécution pour Windows Forms](../how-to-create-event-handlers-at-run-time-for-windows-forms.md).  
  
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
- [Vue d'ensemble du contrôle TextBox](textbox-control-overview-windows-forms.md)
- [Guide pratique pour contrôler le point d’insertion dans un contrôle TextBox Windows Forms](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [Comment : créer une zone de texte pour mot de passe avec le contrôle TextBox Windows Forms](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [Comment : créer une zone de texte en lecture seule](how-to-create-a-read-only-text-box-windows-forms.md)
- [Comment : insérer des guillemets dans une chaîne](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [Comment : afficher des lignes multiples dans le contrôle TextBox Windows Forms](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [TextBox, contrôle](textbox-control-windows-forms.md)
