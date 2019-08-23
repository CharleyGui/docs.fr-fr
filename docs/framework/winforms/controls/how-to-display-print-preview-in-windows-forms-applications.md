---
title: 'Procédure : afficher l’aperçu avant impression dans des applications Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- print preview [Windows Forms], displaying
- printing [Windows Forms], print preview
- examples [Windows Forms], print preview
ms.assetid: e394134c-0886-4517-bd8d-edc4a3749eb5
ms.openlocfilehash: 8252906de9a574f49617609a4cb08a1e8aa6a992
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929009"
---
# <a name="how-to-display-print-preview-in-windows-forms-applications"></a>Procédure : afficher l’aperçu avant impression dans des applications Windows Forms
Vous pouvez utiliser le <xref:System.Windows.Forms.PrintPreviewDialog> contrôle pour permettre aux utilisateurs d’afficher un document, souvent avant qu’il ne soit imprimé.  
  
 Pour ce faire, vous devez spécifier une instance de la <xref:System.Drawing.Printing.PrintDocument> classe; il s’agit du document à imprimer. Pour plus d’informations sur l’utilisation de l' <xref:System.Drawing.Printing.PrintDocument> aperçu avant impression [avec le composant, consultez Procédure: Imprimer en Windows Forms à l’aide](../advanced/how-to-print-in-windows-forms-using-print-preview.md)de l’aperçu avant impression.  
  
> [!NOTE]
> Pour utiliser le <xref:System.Windows.Forms.PrintPreviewDialog> contrôle au moment de l’exécution, les utilisateurs doivent disposer d’une imprimante installée sur leur ordinateur, localement ou via un réseau, car il s' <xref:System.Windows.Forms.PrintPreviewDialog> agit en fait de la façon dont le composant détermine la façon dont un document doit être imprimé.  
  
 Le <xref:System.Windows.Forms.PrintPreviewDialog> contrôle utilise la <xref:System.Drawing.Printing.PrinterSettings> classe. En outre, le <xref:System.Windows.Forms.PrintPreviewDialog> contrôle utilise la <xref:System.Drawing.Printing.PageSettings> classe, tout comme le <xref:System.Windows.Forms.PrintPreviewDialog> fait le composant. Le document d’impression spécifié dans <xref:System.Windows.Forms.PrintPreviewDialog> la propriété <xref:System.Windows.Forms.PrintPreviewControl.Document%2A> du contrôle fait référence <xref:System.Drawing.Printing.PrinterSettings> aux instances des classes <xref:System.Drawing.Printing.PageSettings> et, et celles-ci sont utilisées pour restituer le document dans la fenêtre d’aperçu.  
  
### <a name="to-view-pages-using-the-printpreviewdialog-control"></a>Pour afficher les pages à l’aide du contrôle PrintPreviewDialog  
  
- Utilisez la méthode <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> pour afficher la boîte de dialogue, en spécifiant le <xref:System.Drawing.Printing.PrintDocument> à utiliser.  
  
     Dans l’exemple de code suivant, <xref:System.Windows.Forms.Button> le gestionnaire <xref:System.Windows.Forms.Control.Click> d’événements du contrôle <xref:System.Windows.Forms.PrintPreviewDialog> ouvre une instance du contrôle. Le document d’impression est spécifié dans <xref:System.Windows.Forms.PrintDialog.Document%2A> la propriété. Dans l’exemple ci-dessous, aucun document d’impression n’est spécifié.  
  
     L’exemple requiert que votre formulaire ait un <xref:System.Windows.Forms.Button> contrôle, un <xref:System.Drawing.Printing.PrintDocument> composant nommé `myDocument`et un <xref:System.Windows.Forms.PrintPreviewDialog> contrôle.  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, _  
       ByVal e As System.EventArgs) Handles Button1.Click  
       ' The print document 'myDocument' used below  
       ' is merely for an example.  
       ' You will have to specify your own print document.  
       PrintPreviewDialog1.Document = myDocument  
       PrintPreviewDialog1.ShowDialog()  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)  
    {  
       // The print document 'myDocument' used below  
       // is merely for an example.  
       // You will have to specify your own print document.  
       printPreviewDialog1.Document = myDocument;  
       printPreviewDialog1.ShowDialog();  
    }  
    ```  
  
    ```cpp  
    private:  
       void button1_Click(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          // The print document 'myDocument' used below  
          // is merely for an example.  
          // You will have to specify your own print document.  
          printPreviewDialog1->Document = myDocument;  
          printPreviewDialog1->ShowDialog();  
       }  
    ```  
  
     (Visuel C#, visuel C++) Placez le code suivant dans le constructeur du formulaire pour inscrire le gestionnaire d’événements.  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click += gcnew  
       System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## <a name="see-also"></a>Voir aussi

- [Composant PrintDocument](printdocument-component-windows-forms.md)
- [PrintPreviewDialog, contrôle](printpreviewdialog-control-windows-forms.md)
- [Prise en charge de l’impression dans les Windows Forms](../advanced/windows-forms-print-support.md)
- [Windows Forms](../index.md)
