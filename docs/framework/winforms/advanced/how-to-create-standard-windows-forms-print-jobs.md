---
title: Créer des emplois d’impression standard
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
ms.openlocfilehash: d9607de7c74132e0d7dce605b16d62c79b7dbccb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182569"
---
# <a name="how-to-create-standard-windows-forms-print-jobs"></a>Comment : créer des travaux d'impression Windows Forms standard
La base de l’impression <xref:System.Drawing.Printing.PrintDocument> dans Windows Forms <xref:System.Drawing.Printing.PrintDocument.PrintPage> est le composant, plus précisément, l’événement. En écrivant du <xref:System.Drawing.Printing.PrintDocument.PrintPage> code pour gérer l’événement, vous pouvez spécifier ce qu’il faut imprimer et comment l’imprimer.  
  
### <a name="to-create-a-print-job"></a>Pour créer un travail d’impression  
  
1. Ajoutez <xref:System.Drawing.Printing.PrintDocument> un composant à votre formulaire.  
  
2. Écrivez du code pour gérer l’événement <xref:System.Drawing.Printing.PrintDocument.PrintPage> .  
  
     Vous devrez coder votre propre logique d’impression. En outre, vous devrez spécifier le matériel à imprimer.  
  
     Dans l’exemple de code suivant, un graphique d’échantillon <xref:System.Drawing.Printing.PrintDocument.PrintPage> en forme de rectangle rouge est créé dans le gestionnaire d’événements pour agir comme matériel à imprimer.  
  
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
  
     (Visual C et Visual CMMD) Placez le code suivant dans le constructeur du formulaire pour enregistrer le gestionnaire de l’événement.  
  
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
  
     Vous pouvez également écrire du <xref:System.Drawing.Printing.PrintDocument.BeginPrint> <xref:System.Drawing.Printing.PrintDocument.EndPrint> code pour les événements et des événements, y compris peut-être un intégrier représentant le nombre total de pages à imprimer qui est décriée au fur et à mesure que chaque page est imprimée.  
  
    > [!NOTE]
    > Vous pouvez <xref:System.Windows.Forms.PrintDialog> ajouter un composant à votre formulaire pour fournir une interface utilisateur propre et efficace (interface utilisateur) à vos utilisateurs. La <xref:System.Windows.Forms.PrintDialog.Document%2A> configuration de <xref:System.Windows.Forms.PrintDialog> la propriété du composant vous permet de définir les propriétés liées au document d’impression avec lequel vous travaillez sur votre formulaire. Pour plus d’informations sur le <xref:System.Windows.Forms.PrintDialog> composant, voir [PrintDialog Component](../controls/printdialog-component-windows-forms.md).  
  
     Pour plus d’informations sur les spécificités des travaux d’impression Windows <xref:System.Drawing.Printing.PrintPageEventArgs>Forms, y compris la façon de créer un emploi d’impression programmatiquement, voir .  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Drawing.Printing.PrintDocument>
- [Prise en charge de l’impression dans les Windows Forms](windows-forms-print-support.md)
