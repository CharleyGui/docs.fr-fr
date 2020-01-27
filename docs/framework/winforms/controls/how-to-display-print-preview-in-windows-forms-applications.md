---
title: Afficher l’aperçu avant impression dans les applications Windows Forms
titleSuffix: ''
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
ms.openlocfilehash: ac02339ad86e491cd047dcd4b0c8841374b3bb2e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745570"
---
# <a name="how-to-display-print-preview-in-windows-forms-applications"></a>Comment : afficher l'aperçu avant impression dans les applications Windows Forms
Vous pouvez utiliser le contrôle <xref:System.Windows.Forms.PrintPreviewDialog> pour permettre aux utilisateurs d’afficher un document, souvent avant qu’il ne soit imprimé.  
  
 Pour ce faire, vous devez spécifier une instance de la classe <xref:System.Drawing.Printing.PrintDocument> ; Il s’agit du document à imprimer. Pour plus d’informations sur l’utilisation de l’aperçu avant impression avec le composant <xref:System.Drawing.Printing.PrintDocument>, consultez [Comment : imprimer dans Windows Forms à l’aide de l’aperçu avant impression](../advanced/how-to-print-in-windows-forms-using-print-preview.md).  
  
> [!NOTE]
> Pour utiliser le contrôle <xref:System.Windows.Forms.PrintPreviewDialog> au moment de l’exécution, les utilisateurs doivent disposer d’une imprimante installée sur leur ordinateur, localement ou par le biais d’un réseau, car il s’agit en partie de la façon dont le composant <xref:System.Windows.Forms.PrintPreviewDialog> détermine la façon dont un document doit être imprimé.  
  
 Le contrôle <xref:System.Windows.Forms.PrintPreviewDialog> utilise la classe <xref:System.Drawing.Printing.PrinterSettings>. En outre, le contrôle <xref:System.Windows.Forms.PrintPreviewDialog> utilise la classe <xref:System.Drawing.Printing.PageSettings>, tout comme le fait le composant <xref:System.Windows.Forms.PrintPreviewDialog>. Le document d’impression spécifié dans la propriété <xref:System.Windows.Forms.PrintPreviewControl.Document%2A> du contrôle <xref:System.Windows.Forms.PrintPreviewDialog> fait référence aux instances des classes <xref:System.Drawing.Printing.PrinterSettings> et <xref:System.Drawing.Printing.PageSettings>, et celles-ci sont utilisées pour afficher le document dans la fenêtre d’aperçu.  
  
### <a name="to-view-pages-using-the-printpreviewdialog-control"></a>Pour afficher les pages à l’aide du contrôle PrintPreviewDialog  
  
- Utilisez la méthode <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> pour afficher la boîte de dialogue, en spécifiant le <xref:System.Drawing.Printing.PrintDocument> à utiliser.  
  
     Dans l’exemple de code suivant, le gestionnaire d’événements <xref:System.Windows.Forms.Control.Click> du contrôle <xref:System.Windows.Forms.Button> ouvre une instance du contrôle <xref:System.Windows.Forms.PrintPreviewDialog>. Le document d’impression est spécifié dans la propriété <xref:System.Windows.Forms.PrintDialog.Document%2A>. Dans l’exemple ci-dessous, aucun document d’impression n’est spécifié.  
  
     L’exemple requiert que votre formulaire ait un contrôle <xref:System.Windows.Forms.Button>, un <xref:System.Drawing.Printing.PrintDocument> composant nommé `myDocument`et un contrôle <xref:System.Windows.Forms.PrintPreviewDialog>.  
  
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
