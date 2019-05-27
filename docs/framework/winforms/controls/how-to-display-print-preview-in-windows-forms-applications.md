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
ms.openlocfilehash: 9efccc220bb27706448ae555db8958afb0ccd9fa
ms.sourcegitcommit: 7e129d879ddb42a8b4334eee35727afe3d437952
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66053605"
---
# <a name="how-to-display-print-preview-in-windows-forms-applications"></a>Procédure : afficher l’aperçu avant impression dans des applications Windows Forms
Vous pouvez utiliser la <xref:System.Windows.Forms.PrintPreviewDialog> contrôle pour permettre aux utilisateurs d’afficher un document, souvent avant qu’il soit à imprimer.  
  
 Pour ce faire, vous devez spécifier une instance de la <xref:System.Drawing.Printing.PrintDocument> classe ; il s’agit du document à imprimer. Pour plus d’informations sur l’utilisation de l’aperçu avant impression avec le <xref:System.Drawing.Printing.PrintDocument> composant, consultez [Comment : Impression dans les formulaires de Windows à l’aide de l’aperçu avant impression](../advanced/how-to-print-in-windows-forms-using-print-preview.md).  
  
> [!NOTE]
>  Pour utiliser le <xref:System.Windows.Forms.PrintPreviewDialog> contrôle en cours d’exécution, les utilisateurs doivent avoir une imprimante installée sur leur ordinateur, localement ou via un réseau, car il s’agit en partie comment la <xref:System.Windows.Forms.PrintPreviewDialog> composant détermine l’aspect d’un document imprimé.  
  
 Le <xref:System.Windows.Forms.PrintPreviewDialog> de contrôles utilise la <xref:System.Drawing.Printing.PrinterSettings> classe. En outre, le <xref:System.Windows.Forms.PrintPreviewDialog> de contrôles utilise le <xref:System.Drawing.Printing.PageSettings> (classe), tout comme le <xref:System.Windows.Forms.PrintPreviewDialog> composant. Le document d’impression spécifié dans le <xref:System.Windows.Forms.PrintPreviewDialog> du contrôle <xref:System.Windows.Forms.PrintPreviewControl.Document%2A> propriété fait référence à des instances des deux le <xref:System.Drawing.Printing.PrinterSettings> et <xref:System.Drawing.Printing.PageSettings> classes et ceux-ci sont utilisés pour afficher le document dans la fenêtre d’aperçu.  
  
### <a name="to-view-pages-using-the-printpreviewdialog-control"></a>Pour afficher des pages à l’aide du contrôle PrintPreviewDialog  
  
- Utilisez la méthode <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> pour afficher la boîte de dialogue, en spécifiant le <xref:System.Drawing.Printing.PrintDocument> à utiliser.  
  
     Dans l’exemple de code suivant, le <xref:System.Windows.Forms.Button> du contrôle <xref:System.Windows.Forms.Control.Click> Gestionnaire d’événements ouvre une instance de la <xref:System.Windows.Forms.PrintPreviewDialog> contrôle. Le document d’impression est spécifié dans le <xref:System.Windows.Forms.PrintDialog.Document%2A> propriété. Dans l’exemple ci-dessous, aucun document d’impression n’est spécifié.  
  
     L’exemple suppose que votre formulaire contient un <xref:System.Windows.Forms.Button> contrôle, un <xref:System.Drawing.Printing.PrintDocument> composant nommé `myDocument`et un <xref:System.Windows.Forms.PrintPreviewDialog> contrôle.  
  
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
  
     (Visual C#, Visual C++) Placez le code suivant dans le constructeur du formulaire pour inscrire le Gestionnaire d’événements.  
  
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
