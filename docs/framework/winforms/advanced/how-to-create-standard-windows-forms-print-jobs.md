---
title: 'Procédure : créer des travaux d’impression Windows Forms standard'
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
ms.openlocfilehash: 44673e6b26f088e71813aaac26c4b9a03429597a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69938243"
---
# <a name="how-to-create-standard-windows-forms-print-jobs"></a>Procédure : créer des travaux d’impression Windows Forms standard
La base de l’impression dans Windows Forms est <xref:System.Drawing.Printing.PrintDocument> le composant, plus particulièrement l' <xref:System.Drawing.Printing.PrintDocument.PrintPage> événement. En écrivant du code pour <xref:System.Drawing.Printing.PrintDocument.PrintPage> gérer l’événement, vous pouvez spécifier ce qui doit être imprimé et comment l’imprimer.  
  
### <a name="to-create-a-print-job"></a>Pour créer un travail d’impression  
  
1. Ajoutez un <xref:System.Drawing.Printing.PrintDocument> composant à votre formulaire.  
  
2. Écrivez du code pour gérer l’événement <xref:System.Drawing.Printing.PrintDocument.PrintPage> .  
  
     Vous devrez coder votre propre logique d’impression. En outre, vous devrez spécifier le matériel à imprimer.  
  
     Dans l’exemple de code suivant, un exemple de graphique dans la forme d’un rectangle rouge est créé <xref:System.Drawing.Printing.PrintDocument.PrintPage> dans le gestionnaire d’événements pour agir en tant que matériau à imprimer.  
  
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
  
     Vous pouvez également écrire du code pour les <xref:System.Drawing.Printing.PrintDocument.BeginPrint> événements et <xref:System.Drawing.Printing.PrintDocument.EndPrint> , en incluant éventuellement un entier représentant le nombre total de pages à imprimer qui est décrémenté à mesure que chaque page s’imprime.  
  
    > [!NOTE]
    > Vous pouvez ajouter un <xref:System.Windows.Forms.PrintDialog> composant à votre formulaire pour fournir une interface utilisateur propre et efficace à vos utilisateurs. La définition <xref:System.Windows.Forms.PrintDialog.Document%2A> <xref:System.Windows.Forms.PrintDialog> de la propriété du composant vous permet de définir les propriétés relatives à l’impression du document que vous utilisez dans votre formulaire. Pour plus d’informations sur <xref:System.Windows.Forms.PrintDialog> le composant, consultez [PrintDialog Component](../controls/printdialog-component-windows-forms.md).  
  
     Pour plus d’informations sur les spécificités de Windows Forms travaux d’impression, notamment sur la création d’un travail d’impression par <xref:System.Drawing.Printing.PrintPageEventArgs>programme, consultez.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Drawing.Printing.PrintDocument>
- [Prise en charge de l’impression dans les Windows Forms](windows-forms-print-support.md)
