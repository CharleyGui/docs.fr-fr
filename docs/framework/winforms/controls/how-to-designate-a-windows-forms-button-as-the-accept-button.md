---
title: Désigner un bouton comme bouton Accept
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- buttons [Windows Forms], default on Windows Forms
- Accept button on Windows Forms
- Button control [Windows Forms], designating as default
- Windows Forms controls, default button on form
ms.assetid: 22cc9da6-b913-4e04-9554-dee443ac5c3a
ms.openlocfilehash: ca5f691fb26db5c4adcb48405c9600b54827104c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142145"
---
# <a name="how-to-designate-a-windows-forms-button-as-the-accept-button"></a>Comment : désigner un contrôle Button Windows Forms comme bouton Accepter
Sur n’importe quel formulaire <xref:System.Windows.Forms.Button> Windows, vous pouvez désigner un contrôle pour être le bouton d’acceptation, également connu sous le nom de bouton par défaut. Chaque fois que l’utilisateur appuie sur la touche ENTER, le bouton par défaut est cliqué quel que soit le contrôle du formulaire.  
  
> [!NOTE]
> Les exceptions à cela sont lorsque le contrôle avec mise au point est un autre bouton - dans ce cas, le bouton avec la mise au point sera cliqué - ou une boîte de texte multiline, ou un contrôle personnalisé qui piège la touche ENTER.  
  
### <a name="to-designate-the-accept-button"></a>Pour désigner le bouton accepter  
  
1. Définissez la <xref:System.Windows.Forms.Form.AcceptButton%2A> propriété du <xref:System.Windows.Forms.Button> formulaire au contrôle approprié.  
  
    ```vb  
    Private Sub SetDefault(ByVal myDefaultBtn As Button)  
      Me.AcceptButton = myDefaultBtn
    End Sub  
    ```  
  
    ```csharp  
    private void SetDefault(Button myDefaultBtn)  
    {  
       this.AcceptButton = myDefaultBtn;  
    }  
    ```  
  
    ```cpp  
    private:  
       void SetDefault(Button ^ myDefaultBtn)  
       {  
          this->AcceptButton = myDefaultBtn;  
       }  
    ```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.Form.AcceptButton%2A>
- [Vue d'ensemble du contrôle Button](button-control-overview-windows-forms.md)
- [Méthodes de sélection du contrôle Button Windows Forms](ways-to-select-a-windows-forms-button-control.md)
- [Comment : répondre à un clic du contrôle Button Windows Forms](how-to-respond-to-windows-forms-button-clicks.md)
- [Comment : désigner un contrôle Button Windows Forms en tant que bouton Annuler](how-to-designate-a-windows-forms-button-as-the-cancel-button.md)
- [Button, contrôle](button-control-windows-forms.md)
