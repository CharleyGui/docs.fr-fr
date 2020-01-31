---
title: Désigner un bouton comme bouton Annuler
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- buttons [Windows Forms], cancel buttons
- Button control [Windows Forms], designating as cancel button
ms.assetid: 252f0834-e54b-44d9-96f7-ee5f50e94f2c
ms.openlocfilehash: 123b3e275065efadd24815320ea7d855808e60b9
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743261"
---
# <a name="how-to-designate-a-windows-forms-button-as-the-cancel-button"></a>Comment : désigner un contrôle Button Windows Forms en tant que bouton Annuler
Sur un formulaire Windows, vous pouvez désigner un contrôle de <xref:System.Windows.Forms.Button> comme bouton Annuler. Un clic est effectué sur un bouton Annuler chaque fois que l’utilisateur appuie sur la touche ÉCHAP, quel que soit le contrôle du formulaire actif. Un tel bouton est généralement programmé pour permettre à l’utilisateur de quitter rapidement une opération sans valider aucune action.  
  
### <a name="to-designate-the-cancel-button"></a>Pour désigner le bouton Annuler  
  
1. Définissez la propriété <xref:System.Windows.Forms.Form.CancelButton%2A> du formulaire sur le contrôle <xref:System.Windows.Forms.Button> approprié.  
  
    ```vb  
    Private Sub SetCancelButton(ByVal myCancelBtn As Button)  
       Me.CancelButton = myCancelBtn  
    End Sub  
    ```  
  
    ```csharp  
    private void SetCancelButton(Button myCancelBtn)  
    {  
       this.CancelButton = myCancelBtn;  
    }  
    ```  
  
    ```cpp  
    private:  
       void SetCancelButton(Button ^ myCancelBtn)  
       {  
          this->CancelButton = myCancelBtn;  
       }  
    ```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.Form.CancelButton%2A>
- [Vue d'ensemble du contrôle Button](button-control-overview-windows-forms.md)
- [Méthodes de sélection du contrôle Button Windows Forms](ways-to-select-a-windows-forms-button-control.md)
- [Guide pratique pour répondre à un clic du contrôle Button Windows Forms](how-to-respond-to-windows-forms-button-clicks.md)
- [Guide pratique pour désigner un contrôle Button Windows Forms comme bouton Accepter](how-to-designate-a-windows-forms-button-as-the-accept-button.md)
- [Button, contrôle](button-control-windows-forms.md)
