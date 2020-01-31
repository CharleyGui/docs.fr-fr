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
# <a name="how-to-display-dialog-boxes-for-windows-forms"></a><span data-ttu-id="aec0d-102">Comment : afficher des boîtes de dialogue pour les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="aec0d-102">How to: Display Dialog Boxes for Windows Forms</span></span>
<span data-ttu-id="aec0d-103">Vous affichez une boîte de dialogue de la même façon que n’importe quel autre formulaire dans une application.</span><span class="sxs-lookup"><span data-stu-id="aec0d-103">You display a dialog box in the same way you display any other form in an application.</span></span> <span data-ttu-id="aec0d-104">Le formulaire de démarrage se charge automatiquement lors de l’exécution de l’application.</span><span class="sxs-lookup"><span data-stu-id="aec0d-104">The startup form loads automatically when the application is run.</span></span> <span data-ttu-id="aec0d-105">Pour faire apparaître une deuxième boîte de dialogue ou un second formulaire dans l’application, écrivez le code permettant de le charger et de l’afficher.</span><span class="sxs-lookup"><span data-stu-id="aec0d-105">To make a second form or dialog box appear in the application, write code to load and display it.</span></span> <span data-ttu-id="aec0d-106">De même, pour faire disparaître le formulaire ou la boîte de dialogue, écrivez le code permettant de le décharger ou de le masquer.</span><span class="sxs-lookup"><span data-stu-id="aec0d-106">Similarly, to make the form or dialog box disappear, write code to unload or hide it.</span></span>  
  
### <a name="to-display-a-dialog-box"></a><span data-ttu-id="aec0d-107">Pour afficher une boîte de dialogue</span><span class="sxs-lookup"><span data-stu-id="aec0d-107">To display a dialog box</span></span>  
  
1. <span data-ttu-id="aec0d-108">Accédez au gestionnaire d’événements avec lequel vous souhaitez ouvrir la boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="aec0d-108">Navigate to the event handler with which you want to open the dialog box.</span></span> <span data-ttu-id="aec0d-109">Cela peut se produire lorsqu’une commande de menu est sélectionnée, lorsque l’utilisateur clique sur un bouton ou lorsqu’un autre événement se produit.</span><span class="sxs-lookup"><span data-stu-id="aec0d-109">This can happen when a menu command is selected, when a button is clicked, or when any other event occurs.</span></span>  
  
2. <span data-ttu-id="aec0d-110">Dans le gestionnaire d’événements, ajoutez du code pour ouvrir la boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="aec0d-110">In the event handler, add code to open the dialog box.</span></span> <span data-ttu-id="aec0d-111">Dans cet exemple, un événement de clic de bouton est utilisé pour afficher la boîte de dialogue :</span><span class="sxs-lookup"><span data-stu-id="aec0d-111">In this example, a button-click event is used to show the dialog box:</span></span>  
  
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
