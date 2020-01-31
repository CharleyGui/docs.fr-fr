---
title: Contrôler le point d’insertion dans le contrôle TextBox
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- TextBox control [Windows Forms], insertion point
- insertion points [Windows Forms], TextBox controls
- text boxes [Windows Forms], controlling insertion point
ms.assetid: 5bee7d34-5121-429e-ab1f-d8ff67bc74c1
ms.openlocfilehash: fd4803820921f0c922a4ce885f809abee8fd4c6c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742207"
---
# <a name="how-to-control-the-insertion-point-in-a-windows-forms-textbox-control"></a>Comment : contrôler le point d'insertion dans un contrôle TextBox Windows Forms
Lorsqu’un contrôle Windows Forms <xref:System.Windows.Forms.TextBox> reçoit d’abord le focus, l’insertion par défaut dans la zone de texte est à gauche du texte existant. L’utilisateur peut déplacer le point d’insertion à l’aide du clavier ou de la souris. Si la zone de texte perd, puis reprend le focus, le point d’insertion est l’endroit où l’utilisateur l’a placé pour la dernière fois.  
  
 Dans certains cas, ce comportement peut être déconcerté pour l’utilisateur. Dans une application de traitement de texte, l’utilisateur peut s’attendre à ce que de nouveaux caractères apparaissent après n’importe quel texte existant. Dans une application de saisie de données, l’utilisateur peut s’attendre à ce que de nouveaux caractères remplacent toute entrée existante. Les propriétés <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> et <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> vous permettent de modifier le comportement en fonction de vos besoins.  
  
### <a name="to-control-the-insertion-point-in-a-textbox-control"></a>Pour contrôler le point d’insertion dans un contrôle TextBox  
  
1. Affectez à la propriété <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> une valeur appropriée. Zéro place le point d’insertion immédiatement à gauche du premier caractère.  
  
2. Facultatif Affectez à la propriété <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> la longueur du texte que vous souhaitez sélectionner.  
  
     Le code ci-dessous retourne toujours le point d’insertion à 0. Le gestionnaire d’événements `TextBox1_Enter` doit être lié au contrôle ; Pour plus d’informations, consultez [création de gestionnaires d’événements dans Windows Forms](../creating-event-handlers-in-windows-forms.md).  
  
    ```vb  
    Private Sub TextBox1_Enter(ByVal sender As Object, ByVal e As System.EventArgs) Handles TextBox1.Enter  
       TextBox1.SelectionStart = 0  
       TextBox1.SelectionLength = 0  
    End Sub  
    ```  
  
    ```csharp  
    private void textBox1_Enter(Object sender, System.EventArgs e) {  
       textBox1.SelectionStart = 0;  
       textBox1.SelectionLength = 0;  
    }  
    ```  
  
    ```cpp  
    private:  
       void textBox1_Enter(System::Object ^  sender,  
          System::EventArgs ^  e)  
       {  
          textBox1->SelectionStart = 0;  
          textBox1->SelectionLength = 0;  
       }  
    ```  
  
## <a name="making-the-insertion-point-visible-by-default"></a>Rendre le point d’insertion visible par défaut  
 Le point d’insertion <xref:System.Windows.Forms.TextBox> est visible par défaut dans un nouveau formulaire uniquement si le contrôle <xref:System.Windows.Forms.TextBox> est d’abord dans l’ordre de tabulation. Dans le cas contraire, le point d’insertion s’affiche uniquement si vous donnez au <xref:System.Windows.Forms.TextBox> le focus à l’aide du clavier ou de la souris.  
  
#### <a name="to-make-the-text-box-insertion-point-visible-by-default-on-a-new-form"></a>Pour que le point d’insertion de la zone de texte soit visible par défaut sur un nouveau formulaire  
  
- Affectez à la propriété <xref:System.Windows.Forms.Control.TabIndex%2A> du contrôle <xref:System.Windows.Forms.TextBox> la valeur `0`.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.TextBox>
- [Vue d’ensemble du contrôle TextBox](textbox-control-overview-windows-forms.md)
- [Guide pratique pour créer une zone de texte pour mot de passe avec le contrôle TextBox Windows Forms](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [Guide pratique pour créer une zone de texte en lecture seule](how-to-create-a-read-only-text-box-windows-forms.md)
- [Guide pratique pour insérer des guillemets dans une chaîne](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [Guide pratique pour sélectionner du texte dans le contrôle TextBox Windows Forms](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [Guide pratique pour afficher des lignes multiples dans le contrôle TextBox Windows Forms](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [TextBox, contrôle](textbox-control-windows-forms.md)
