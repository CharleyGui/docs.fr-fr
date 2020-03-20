---
title: 'Comment: Imprimer des graphiques'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- graphics [Windows Forms], printing
- printing [Windows Forms], graphics
ms.assetid: 32b891e6-52ff-4fea-a9ff-2ce5db20a4c6
ms.openlocfilehash: 15f3a507839430ce058302e7f5abd317ef84626f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182532"
---
# <a name="how-to-print-graphics-in-windows-forms"></a>Comment : imprimer des graphiques dans Windows Forms
Fréquemment, vous voudrez imprimer des graphiques dans votre application Windows. La <xref:System.Drawing.Graphics> classe fournit des méthodes pour dessiner des objets vers un appareil, comme un écran ou une imprimante.  
  
### <a name="to-print-graphics"></a>Pour imprimer des graphiques  
  
1. Ajoutez <xref:System.Drawing.Printing.PrintDocument> un composant à votre formulaire.  
  
2. Dans <xref:System.Drawing.Printing.PrintDocument.PrintPage> le gestionnaire d’événement, utilisez la <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> propriété de la <xref:System.Drawing.Printing.PrintPageEventArgs> classe pour instruire l’imprimante sur le type de graphiques à imprimer.  
  
     L’exemple de code suivant montre un gestionnaire d’événements utilisé pour créer une ellipse bleue dans un rectangle de délimitation. Le rectangle a l’emplacement et les dimensions suivants: à partir de 100, 150 avec une largeur de 250 et une hauteur de 250.  
  
    ```vb  
    Private Sub PrintDocument1_PrintPage(ByVal sender As Object, ByVal e As System.Drawing.Printing.PrintPageEventArgs) Handles PrintDocument1.PrintPage  
       e.Graphics.FillEllipse(Brushes.Blue, New Rectangle(100, 150, 250, 250))  
    End Sub  
    ```  
  
    ```csharp  
    private void printDocument1_PrintPage(object sender,
    System.Drawing.Printing.PrintPageEventArgs e)  
    {  
       e.Graphics.FillRectangle(Brushes.Blue,
         new Rectangle(100, 150, 250, 250));  
    }  
    ```  
  
    ```cpp  
    private:  
       void printDocument1_PrintPage(System::Object ^ sender,  
          System::Drawing::Printing::PrintPageEventArgs ^ e)  
       {  
          e->Graphics->FillRectangle(Brushes::Blue,  
             Rectangle(100, 150, 250, 250));  
       }  
    ```  
  
     (Visual C et Visual CMMD) Placez le code suivant dans le constructeur du formulaire pour enregistrer le gestionnaire de l’événement.  
  
    ```csharp  
    this.printDocument1.PrintPage += new  
       System.Drawing.Printing.PrintPageEventHandler  
       (this.printDocument1_PrintPage);  
    ```  
  
    ```cpp  
    this->printDocument1->PrintPage += gcnew  
       System::Drawing::Printing::PrintPageEventHandler  
       (this, &Form1::printDocument1_PrintPage);  
    ```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Drawing.Graphics>
- <xref:System.Drawing.Brush>
- [Prise en charge de l’impression dans les Windows Forms](windows-forms-print-support.md)
