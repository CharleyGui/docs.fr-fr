---
title: 'Comment : afficher des boîtes de dialogue'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms, displaying
- Windows Forms dialog boxes [Windows Forms], displaying
- Windows Forms, calling one form from another
- dialog boxes [Windows Forms], displaying for Windows Forms
ms.assetid: aaac1b38-c651-495a-8d3d-5a9bfb32fee3
ms.openlocfilehash: dd04a06eaa0dd7583ef2f72edb4cffa99aaaa60c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76739460"
---
# <a name="how-to-display-dialog-boxes-for-windows-forms"></a>Comment : afficher des boîtes de dialogue pour les Windows Forms
Vous affichez une boîte de dialogue de la même façon que n’importe quel autre formulaire dans une application. Le formulaire de démarrage se charge automatiquement lors de l’exécution de l’application. Pour faire apparaître une deuxième boîte de dialogue ou un second formulaire dans l’application, écrivez le code permettant de le charger et de l’afficher. De même, pour faire disparaître le formulaire ou la boîte de dialogue, écrivez le code permettant de le décharger ou de le masquer.  
  
### <a name="to-display-a-dialog-box"></a>Pour afficher une boîte de dialogue  
  
1. Accédez au gestionnaire d’événements avec lequel vous souhaitez ouvrir la boîte de dialogue. Cela peut se produire lorsqu’une commande de menu est sélectionnée, lorsque l’utilisateur clique sur un bouton ou lorsqu’un autre événement se produit.  
  
2. Dans le gestionnaire d’événements, ajoutez du code pour ouvrir la boîte de dialogue. Dans cet exemple, un événement de clic de bouton est utilisé pour afficher la boîte de dialogue :  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
       Dim dlg1 as new Form()  
       dlg1.ShowDialog()  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)   
    {  
       Form dlg1 = new Form();  
       dlg1.ShowDialog();  
    }  
    ```  
  
    ```cpp  
    private:   
      void button1_Click(System::Object ^ sender,  
        System::EventArgs ^ e)  
      {  
        Form ^ dlg1 = gcnew Form();  
        dlg1->ShowDialog();  
      }  
    ```
