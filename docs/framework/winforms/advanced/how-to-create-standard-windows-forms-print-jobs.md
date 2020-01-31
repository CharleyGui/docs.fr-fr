---
title: Créer des travaux d’impression standard
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- printing [Windows Forms]
- printing [Windows Forms], creating print jobs
- printing [Visual Basic], in Windows applications
ms.assetid: 03342b90-9cfe-40b2-838b-b479a13c5dea
ms.openlocfilehash: 4850dc901630179cc44fefda7e25bbabcfb4725f
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741520"
---
# <a name="how-to-create-standard-windows-forms-print-jobs"></a>Comment : créer des travaux d'impression Windows Forms standard
La base de l’impression dans Windows Forms est le composant <xref:System.Drawing.Printing.PrintDocument>, plus particulièrement l’événement <xref:System.Drawing.Printing.PrintDocument.PrintPage>. En écrivant du code pour gérer l’événement <xref:System.Drawing.Printing.PrintDocument.PrintPage>, vous pouvez spécifier ce qui doit être imprimé et comment l’imprimer.  
  
### <a name="to-create-a-print-job"></a>Pour créer un travail d’impression  
  
1. Ajoutez un composant <xref:System.Drawing.Printing.PrintDocument> à votre formulaire.  
  
2. Écrivez du code pour gérer l’événement <xref:System.Drawing.Printing.PrintDocument.PrintPage> .  
  
     Vous devrez coder votre propre logique d’impression. En outre, vous devrez spécifier le matériel à imprimer.  
  
     Dans l’exemple de code suivant, un exemple de graphique dans la forme d’un rectangle rouge est créé dans le gestionnaire d’événements <xref:System.Drawing.Printing.PrintDocument.PrintPage> pour agir en tant que matériau à imprimer.  
  
    ```vb  
    Private Sub PrintDocument1_PrintPage(ByVal sender As Object, ByVal e As System.Drawing.Printing.PrintPageEventArgs) Handles PrintDocument1.PrintPage  
       e.Graphics.FillRectangle(Brushes.Red, New Rectangle(500, 500, 500, 500))  
    End Sub  
    ```  
  
    ```csharp  
    private void printDocument1_PrintPage(object sender,   
    System.Drawing.Printing.PrintPageEventArgs e)  
    {  
       e.Graphics.FillRectangle(Brushes.Red,   
         new Rectangle(500, 500, 500, 500));  
    }  
    ```  
  
    ```cpp  
    private:  
       void printDocument1_PrintPage(System::Object ^ sender,  
          System::Drawing::Printing::PrintPageEventArgs ^ e)  
       {  
          e->Graphics->FillRectangle(Brushes::Red,  
             Rectangle(500, 500, 500, 500));  
       }  
    ```  
  
     (Visuel C# et visuel C++) Placez le code suivant dans le constructeur du formulaire pour inscrire le gestionnaire d’événements.  
  
    ```csharp  
    this.printDocument1.PrintPage += new  
       System.Drawing.Printing.PrintPageEventHandler  
       (this.printDocument1_PrintPage);  
    ```  
  
    ```cpp  
    printDocument1->PrintPage += gcnew  
       System::Drawing::Printing::PrintPageEventHandler  
       (this, &Form1::printDocument1_PrintPage);  
    ```  
  
     Vous pouvez également écrire du code pour les événements <xref:System.Drawing.Printing.PrintDocument.BeginPrint> et <xref:System.Drawing.Printing.PrintDocument.EndPrint>, en incluant éventuellement un entier représentant le nombre total de pages à imprimer qui sont décrémenté à mesure que chaque page s’imprime.  
  
    > [!NOTE]
    > Vous pouvez ajouter un composant <xref:System.Windows.Forms.PrintDialog> à votre formulaire pour fournir une interface utilisateur propre et efficace à vos utilisateurs. La définition de la propriété <xref:System.Windows.Forms.PrintDialog.Document%2A> du composant <xref:System.Windows.Forms.PrintDialog> vous permet de définir les propriétés relatives à l’impression du document que vous utilisez dans votre formulaire. Pour plus d’informations sur le composant <xref:System.Windows.Forms.PrintDialog>, consultez [PrintDialog Component](../controls/printdialog-component-windows-forms.md).  
  
     Pour plus d’informations sur les spécificités de Windows Forms travaux d’impression, notamment sur la création d’un travail d’impression par programme, consultez <xref:System.Drawing.Printing.PrintPageEventArgs>.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Drawing.Printing.PrintDocument>
- [Prise en charge de l’impression dans les Windows Forms](windows-forms-print-support.md)
