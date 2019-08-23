---
title: 'Procédure : désigner un bouton Windows Forms comme bouton Accepter'
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
ms.openlocfilehash: 5b21ee7da7a666a391be3bc5be57855eaa7ec8b5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69967364"
---
# <a name="how-to-designate-a-windows-forms-button-as-the-accept-button"></a>Procédure : désigner un bouton Windows Forms comme bouton Accepter
Sur un formulaire Windows, vous pouvez désigner un <xref:System.Windows.Forms.Button> contrôle comme bouton d’acceptation, également appelé bouton par défaut. Chaque fois que l’utilisateur appuie sur la touche entrée, le bouton par défaut est activé, quel que soit l’autre contrôle sur le formulaire.  
  
> [!NOTE]
> Les exceptions sont les cas où le contrôle ayant le focus est un autre bouton, dans ce cas, le bouton sur lequel le focus sera activé, ou une zone de texte multiligne, ou un contrôle personnalisé qui intercepte la touche entrée.  
  
### <a name="to-designate-the-accept-button"></a>Pour désigner le bouton accepter  
  
1. Affectez à la <xref:System.Windows.Forms.Form.AcceptButton%2A> propriété du formulaire le <xref:System.Windows.Forms.Button> contrôle approprié.  
  
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
- [Guide pratique pour Répondre à Windows Forms clics de bouton](how-to-respond-to-windows-forms-button-clicks.md)
- [Guide pratique : Désigner un bouton de Windows Forms comme bouton Annuler](how-to-designate-a-windows-forms-button-as-the-cancel-button.md)
- [Button, contrôle](button-control-windows-forms.md)
