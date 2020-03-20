---
title: "Comment : déterminer les propriétés de la page à l'aide du composant PageSetupDialog"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- page properties
- page setup
- PageSetupDialog component
ms.assetid: 6dae05bc-c0fd-4357-bb93-841a1631d98f
ms.openlocfilehash: 8a015c199193dfd9c43bec53cc93cbf9dc201413
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142041"
---
# <a name="how-to-determine-page-properties-using-the-pagesetupdialog-component"></a>Comment : déterminer les propriétés de la page à l'aide du composant PageSetupDialog
Le composant [PageSetupDialog](pagesetupdialog-component-windows-forms.md) présente des options de disposition, de format du papier et d’autres choix de mise en page à l’utilisateur pour un document.  
  
 Vous devez spécifier une instance de la classe <xref:System.Drawing.Printing.PrintDocument> ; il s’agit du document à imprimer. De plus, les utilisateurs doivent avoir une imprimante installée sur leur ordinateur, localement ou sur un réseau, car c’est en partie comme cela que le composant <xref:System.Windows.Forms.PageSetupDialog> détermine les choix de mise en page présentés à l’utilisateur.  
  
 L’interaction entre le composant <xref:System.Windows.Forms.PageSetupDialog> et la classe <xref:System.Drawing.Printing.PageSettings> constitue l’un des aspects importants de son utilisation. La classe <xref:System.Drawing.Printing.PageSettings> sert à spécifier des paramètres qui modifient la façon dont une page est imprimée, comme l’orientation du papier, le format de la page et les marges. Chacun de ces paramètres est représenté en tant que propriété de la classe <xref:System.Drawing.Printing.PageSettings> . La classe <xref:System.Windows.Forms.PageSetupDialog> modifie ces valeurs de propriétés pour une instance donnée de la classe <xref:System.Drawing.Printing.PageSettings> associée au document (et représentée en tant que propriété <xref:System.Drawing.Printing.PrintDocument.DefaultPageSettings%2A> ).  
  
### <a name="to-set-page-properties-using-the-pagesetupdialog-component"></a>Pour définir les propriétés de la page à l’aide du composant PageSetupDialog  
  
1. Utilisez la méthode <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> pour afficher la boîte de dialogue, en spécifiant le <xref:System.Drawing.Printing.PrintDocument> à utiliser.  
  
     Dans l’exemple ci-dessous, le gestionnaire d’événements <xref:System.Windows.Forms.Button> du contrôle <xref:System.Windows.Forms.Control.Click> ouvre une instance du composant <xref:System.Windows.Forms.PageSetupDialog> . Un document existant est spécifié dans la propriété <xref:System.Windows.Forms.PageSetupDialog.Document%2A> , et sa propriété <xref:System.Drawing.Printing.PageSettings.Color%2A?displayProperty=nameWithType> prend la valeur `false`.  
  
     L’exemple suppose que <xref:System.Windows.Forms.Button> votre formulaire <xref:System.Drawing.Printing.PrintDocument> a `myDocument`un <xref:System.Windows.Forms.PageSetupDialog> contrôle, un composant nommé, et un composant.  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, _  
    ByVal e As System.EventArgs) Handles Button1.Click  
       ' The print document 'myDocument' used below  
       ' is merely for an example.  
       'You will have to specify your own print document.  
       PageSetupDialog1.Document = myDocument  
       ' Sets the print document's color setting to false,  
       ' so that the page will not be printed in color.  
       PageSetupDialog1.Document.DefaultPageSettings.Color = False  
       PageSetupDialog1.ShowDialog()  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)  
    {  
       // The print document 'myDocument' used below  
       // is merely for an example.  
       // You will have to specify your own print document.  
       pageSetupDialog1.Document = myDocument;  
       // Sets the print document's color setting to false,  
       // so that the page will not be printed in color.  
       pageSetupDialog1.Document.DefaultPageSettings.Color = false;  
       pageSetupDialog1.ShowDialog();  
    }  
    ```  
  
    ```cpp  
    private:  
       System::Void button1_Click(System::Object ^  sender,  
          System::EventArgs ^  e)  
       {  
          // The print document 'myDocument' used below  
          // is merely for an example.  
          // You will have to specify your own print document.  
          pageSetupDialog1->Document = myDocument;  
          // Sets the print document's color setting to false,  
          // so that the page will not be printed in color.  
          pageSetupDialog1->Document->DefaultPageSettings->Color = false;  
          pageSetupDialog1->ShowDialog();  
       }  
    ```  
  
     (Visual C et Visual CMMD) Placez le code suivant dans le constructeur du formulaire pour enregistrer le gestionnaire de l’événement.  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click += gcnew
       System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.PageSetupDialog>
- [Guide pratique pour créer des travaux d’impression Windows Forms standard](../advanced/how-to-create-standard-windows-forms-print-jobs.md)
- [PageSetupDialog Component](pagesetupdialog-component-windows-forms.md)
