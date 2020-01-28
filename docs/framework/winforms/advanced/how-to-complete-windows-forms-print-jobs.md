---
title: Terminer les travaux d’impression
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- print jobs [Windows Forms], completing in Windows Forms
- printing [Windows Forms], print jobs
ms.assetid: 23ec74f7-34c5-4710-82a0-ee2914518548
ms.openlocfilehash: b8ef4fa05b2107247181e82b72389f9503507135
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746492"
---
# <a name="how-to-complete-windows-forms-print-jobs"></a>Comment : terminer des travaux d'impression Windows Forms
Souvent, les traitements de texte et d’autres applications qui impliquent l’impression offrent la possibilité d’afficher un message aux utilisateurs qu’un travail d’impression est terminé. Vous pouvez fournir cette fonctionnalité dans votre Windows Forms en gérant l’événement <xref:System.Drawing.Printing.PrintDocument.EndPrint> du composant <xref:System.Drawing.Printing.PrintDocument>.  
  
 La procédure suivante nécessite que vous ayez créé une application Windows avec un composant <xref:System.Drawing.Printing.PrintDocument>, qui est la méthode standard d’activation de l’impression à partir d’une application Windows. Pour plus d’informations sur l’impression à partir de Windows Forms à l’aide du composant <xref:System.Drawing.Printing.PrintDocument>, consultez [Comment : créer des travaux d’impression Windows Forms standard](how-to-create-standard-windows-forms-print-jobs.md).  
  
### <a name="to-complete-a-print-job"></a>Pour terminer un travail d’impression  
  
1. Définissez la propriété <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> du composant <xref:System.Drawing.Printing.PrintDocument>.  
  
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
  
     Dans l’exemple de code suivant, une boîte de message s’affiche, indiquant que l’impression du document est terminée.  
  
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
  
     (Visuel C# et visuel C++) Placez le code suivant dans le constructeur du formulaire pour inscrire le gestionnaire d’événements.  
  
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
