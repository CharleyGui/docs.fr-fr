---
title: Travaux d’impression complets
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- print jobs [Windows Forms], completing in Windows Forms
- printing [Windows Forms], print jobs
ms.assetid: 23ec74f7-34c5-4710-82a0-ee2914518548
ms.openlocfilehash: 62f67002bfbaf46e73bae06fdaff26efde865c06
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182597"
---
# <a name="how-to-complete-windows-forms-print-jobs"></a>Comment : terminer des travaux d'impression Windows Forms
Fréquemment, les processeurs de texte et d’autres applications qui impliquent l’impression fourniront la possibilité d’afficher un message aux utilisateurs qu’un travail d’impression est terminé. Vous pouvez fournir cette fonctionnalité dans vos <xref:System.Drawing.Printing.PrintDocument.EndPrint> formulaires <xref:System.Drawing.Printing.PrintDocument> Windows en manipulant l’événement du composant.  
  
 La procédure suivante exige que vous ayez créé <xref:System.Drawing.Printing.PrintDocument> une application Windows avec un composant dessus, ce qui est le moyen standard d’autoriser l’impression à partir d’une application windows. Pour plus d’informations sur <xref:System.Drawing.Printing.PrintDocument> l’impression à partir de formulaires Windows à l’aide du composant, voir [Comment : Créer des formulaires Windows standard Imprimez des emplois](how-to-create-standard-windows-forms-print-jobs.md).  
  
### <a name="to-complete-a-print-job"></a>Pour terminer un travail d’impression  
  
1. Réglez <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> la <xref:System.Drawing.Printing.PrintDocument> propriété du composant.  
  
    ```vb  
    PrintDocument1.DocumentName = "MyTextFile"  
    ```  
  
    ```csharp  
    printDocument1.DocumentName = "MyTextFile";  
    ```  
  
    ```cpp  
    printDocument1->DocumentName = "MyTextFile";  
    ```  
  
2. Écrivez du code pour gérer l’événement <xref:System.Drawing.Printing.PrintDocument.EndPrint> .  
  
     Dans l’exemple de code suivant, une boîte de message est affichée, indiquant que le document a fini d’imprimer.  
  
    ```vb  
    Private Sub PrintDocument1_EndPrint(ByVal sender As Object, ByVal e As System.Drawing.Printing.PrintEventArgs) Handles PrintDocument1.EndPrint  
       MessageBox.Show(PrintDocument1.DocumentName + " has finished printing.")  
    End Sub  
    ```  
  
    ```csharp  
    private void printDocument1_EndPrint(object sender,
    System.Drawing.Printing.PrintEventArgs e)  
    {  
       MessageBox.Show(printDocument1.DocumentName +
          " has finished printing.");  
    }  
    ```  
  
    ```cpp  
    private:  
       void printDocument1_EndPrint(System::Object ^ sender,  
          System::Drawing::Printing::PrintEventArgs ^ e)  
       {  
          MessageBox::Show(String::Concat(printDocument1->DocumentName,  
             " has finished printing."));  
       }  
    ```  
  
     (Visual C et Visual CMMD) Placez le code suivant dans le constructeur du formulaire pour enregistrer le gestionnaire de l’événement.  
  
    ```csharp  
    this.printDocument1.EndPrint += new  
       System.Drawing.Printing.PrintEventHandler  
       (this.printDocument1_EndPrint);  
    ```  
  
    ```cpp  
    this->printDocument1->EndPrint += gcnew  
       System::Drawing::Printing::PrintEventHandler  
       (this, &Form1::printDocument1_EndPrint);  
    ```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Drawing.Printing.PrintDocument>
- [Prise en charge de l’impression dans les Windows Forms](windows-forms-print-support.md)
