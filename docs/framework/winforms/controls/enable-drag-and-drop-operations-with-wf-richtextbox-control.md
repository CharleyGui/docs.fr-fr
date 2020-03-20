---
title: Activez les opérations drag-and-Drop avec le contrôle De RichTextBox
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- examples [Windows Forms], text boxes
- drag and drop [Windows Forms], richTextBox control
- text boxes [Windows Forms], drag-and-drop operations
- RichTextBox control [Windows Forms], drag-and-drop operations
ms.assetid: ca167d1c-2014-4cf0-96a0-20598470be3b
ms.openlocfilehash: 27e5c18598552c465ef17f5e58069bc10e401c09
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182352"
---
# <a name="how-to-enable-drag-and-drop-operations-with-the-windows-forms-richtextbox-control"></a>Comment : activer les opérations glisser-déplacer avec le contrôle RichTextBox Windows Forms
Les opérations glisser-déplacer avec le contrôle Windows Forms <xref:System.Windows.Forms.RichTextBox> s’effectuent en gérant les événements <xref:System.Windows.Forms.RichTextBox.DragEnter> et <xref:System.Windows.Forms.RichTextBox.DragDrop> . De ce fait, ces opérations sont extrêmement simples avec le contrôle <xref:System.Windows.Forms.RichTextBox> .  
  
### <a name="to-enable-drag-operations-in-a-richtextbox-control"></a>Pour permettre les opérations glisser dans un contrôle RichTextBox  
  
1. Affectez à la propriété <xref:System.Windows.Forms.RichTextBox.AllowDrop%2A> du contrôle <xref:System.Windows.Forms.RichTextBox> la valeur `true`.  
  
2. Écrivez du code dans le gestionnaire d’événements de l’événement <xref:System.Windows.Forms.RichTextBox.DragEnter> . Utilisez une instruction `if` pour vous assurer que les données glissées sont d’un type acceptable (dans ce cas, text). La valeur de la propriété <xref:System.Windows.Forms.DragEventArgs.Effect%2A?displayProperty=nameWithType> peut être n’importe quelle valeur de l’énumération <xref:System.Windows.Forms.DragDropEffects> .  
  
    ```vb  
    Private Sub RichTextBox1_DragEnter(ByVal sender As Object, _
       ByVal e As System.Windows.Forms.DragEventArgs) _
       Handles RichTextBox1.DragEnter  
       If (e.Data.GetDataPresent(DataFormats.Text)) Then  
          e.Effect = DragDropEffects.Copy  
       Else  
          e.Effect = DragDropEffects.None  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void richTextBox1_DragEnter(object sender,
    System.Windows.Forms.DragEventArgs e)  
    {  
       if (e.Data.GetDataPresent(DataFormats.Text))
          e.Effect = DragDropEffects.Copy;  
       else  
          e.Effect = DragDropEffects.None;  
    }  
    ```  
  
    ```cpp  
    private:  
       void richTextBox1_DragEnter(System::Object ^  sender,  
          System::Windows::Forms::DragEventArgs ^  e)  
       {  
          if (e->Data->GetDataPresent(DataFormats::Text))  
             e->Effect = DragDropEffects::Copy;  
          else  
             e->Effect = DragDropEffects::None;  
       }  
    ```  
  
     (Visual C et Visual CMMD) Placez le code suivant dans le constructeur du formulaire pour enregistrer le gestionnaire de l’événement.  
  
    ```csharp  
    this.richTextBox1.DragEnter += new  
        System.Windows.Forms.DragEventHandler  
        (this.richTextBox1_DragEnter);  
    ```  
  
    ```cpp  
    this->richTextBox1->DragEnter += gcnew  
       System::Windows::Forms::DragEventHandler  
       (this, &Form1::richTextBox1_DragEnter);  
    ```  
  
3. Écrivez du code pour gérer l’événement <xref:System.Windows.Forms.RichTextBox.DragDrop> . Utilisez la méthode <xref:System.Windows.Forms.DataObject.GetData%2A?displayProperty=nameWithType> pour récupérer les données glissées.  
  
     Dans l’exemple ci-dessous, le code définit la propriété <xref:System.Windows.Forms.RichTextBox.Text%2A> du contrôle <xref:System.Windows.Forms.RichTextBox> comme étant égale aux données glissées. Si le contrôle <xref:System.Windows.Forms.RichTextBox> contient déjà du texte, le texte glissé est inséré au point d’insertion.  
  
    ```vb  
    Private Sub RichTextBox1_DragDrop(ByVal sender As Object, _
       ByVal e As System.Windows.Forms.DragEventArgs) _
       Handles RichTextBox1.DragDrop  
       Dim i As Int16
       Dim s As String  
  
       ' Get start position to drop the text.  
       i = RichTextBox1.SelectionStart  
       s = RichTextBox1.Text.Substring(i)  
       RichTextBox1.Text = RichTextBox1.Text.Substring(0, i)  
  
       ' Drop the text on to the RichTextBox.  
       RichTextBox1.Text = RichTextBox1.Text + _  
          e.Data.GetData(DataFormats.Text).ToString()  
       RichTextBox1.Text = RichTextBox1.Text + s  
    End Sub  
    ```  
  
    ```csharp  
    private void richTextBox1_DragDrop(object sender,
    System.Windows.Forms.DragEventArgs e)  
    {  
       int i;  
       String s;  
  
       // Get start position to drop the text.  
       i = richTextBox1.SelectionStart;  
       s = richTextBox1.Text.Substring(i);  
       richTextBox1.Text = richTextBox1.Text.Substring(0,i);  
  
       // Drop the text on to the RichTextBox.  
       richTextBox1.Text = richTextBox1.Text +
          e.Data.GetData(DataFormats.Text).ToString();  
       richTextBox1.Text = richTextBox1.Text + s;  
    }  
    ```  
  
    ```cpp  
    private:  
       System::Void richTextBox1_DragDrop(System::Object ^  sender,  
          System::Windows::Forms::DragEventArgs ^  e)  
       {  
          int i;  
          String ^s;  
  
       // Get start position to drop the text.  
       i = richTextBox1->SelectionStart;  
       s = richTextBox1->Text->Substring(i);  
       richTextBox1->Text = richTextBox1->Text->Substring(0,i);  
  
       // Drop the text on to the RichTextBox.  
       String ^str = String::Concat(richTextBox1->Text, e->Data  
       ->GetData(DataFormats->Text)->ToString());
       richTextBox1->Text = String::Concat(str, s);  
       }  
    ```  
  
     (Visual C et Visual CMMD) Placez le code suivant dans le constructeur du formulaire pour enregistrer le gestionnaire de l’événement.  
  
    ```csharp  
    this.richTextBox1.DragDrop += new  
        System.Windows.Forms.DragEventHandler  
        (this.richTextBox1_DragDrop);  
    ```  
  
    ```cpp  
    this->richTextBox1->DragDrop += gcnew
       System::Windows::Forms::DragEventHandler  
       (this, &Form1::richTextBox1_DragDrop);  
    ```  
  
### <a name="to-test-the-drag-and-drop-functionality-in-your-application"></a>Pour tester la fonctionnalité de glisser-déplacer dans votre application  
  
1. Enregistrez et générez votre application. Pendant son exécution, exécutez WordPad.  
  
     WordPad est un éditeur de texte installé par Windows qui permet les opérations de glisser-déplacer. Pour y accéder, cliquez sur le bouton **Démarrer** , sélectionnez **Exécuter**, tapez `WordPad` dans la zone de texte de la boîte de dialogue **Exécuter** , puis cliquez sur **OK**.  
  
2. Une fois que WordPad est ouvert, tapez-y une chaîne de texte. À l’aide de la souris, sélectionnez le texte, puis faites-le glisser sur le contrôle <xref:System.Windows.Forms.RichTextBox> dans votre application Windows.  
  
     Notez que quand vous pointez la souris sur le contrôle <xref:System.Windows.Forms.RichTextBox> (et que donc vous déclenchez l’événement <xref:System.Windows.Forms.RichTextBox.DragEnter> ), le pointeur de la souris se transforme et vous pouvez déposer le texte sélectionné dans le contrôle <xref:System.Windows.Forms.RichTextBox> .  
  
     Quand vous relâchez le bouton de la souris, le texte sélectionné est déposé (autrement dit, l’événement <xref:System.Windows.Forms.RichTextBox.DragDrop> est déclenché) et inséré dans le contrôle <xref:System.Windows.Forms.RichTextBox> .  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.RichTextBox>
- [Comment : exécuter des opérations de glisser-déposer entre des applications](../advanced/how-to-perform-drag-and-drop-operations-between-applications.md)
- [RichTextBox, contrôle](richtextbox-control-windows-forms.md)
- [Contrôles à utiliser sur les formulaires Windows](controls-to-use-on-windows-forms.md)
