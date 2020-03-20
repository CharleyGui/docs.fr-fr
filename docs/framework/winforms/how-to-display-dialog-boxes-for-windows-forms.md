---
title: 'Comment: Afficher les boîtes de dialogue'
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
ms.openlocfilehash: 3625080c7c322e297a9de92e4f95a40c0caf3e72
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181975"
---
# <a name="how-to-display-dialog-boxes-for-windows-forms"></a>Comment : afficher des boîtes de dialogue pour les Windows Forms
Vous affichez une boîte de dialogue de la même manière que vous affichez n’importe quel autre formulaire dans une application. Le formulaire de démarrage se charge automatiquement lorsque l’application est exécutée. Pour faire apparaître un deuxième formulaire ou une boîte de dialogue dans l’application, écrivez du code pour le charger et l’afficher. De même, pour faire disparaître le formulaire ou la boîte de dialogue, écrivez du code pour le décharger ou le cacher.  
  
### <a name="to-display-a-dialog-box"></a>Pour afficher une boîte de dialogue  
  
1. Naviguez vers le gestionnaire d’événements avec lequel vous souhaitez ouvrir la boîte de dialogue. Cela peut se produire lorsqu’une commande de menu est sélectionnée, lorsqu’un bouton est cliqué, ou lorsque tout autre événement se produit.  
  
2. Dans le gestionnaire d’événement, ajoutez du code pour ouvrir la boîte de dialogue. Dans cet exemple, un événement bouton-clic est utilisé pour afficher la boîte de dialogue:  
  
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
