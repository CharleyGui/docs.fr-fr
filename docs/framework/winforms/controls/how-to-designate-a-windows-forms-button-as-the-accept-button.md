---
title: Désigner un bouton comme bouton accepter
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
ms.openlocfilehash: 1063f649768cac2c866390718b261a21e18ec4d3
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743270"
---
# <a name="how-to-designate-a-windows-forms-button-as-the-accept-button"></a>Comment : désigner un contrôle Button Windows Forms comme bouton Accepter
Sur un formulaire Windows, vous pouvez désigner un contrôle de <xref:System.Windows.Forms.Button> comme bouton accepter, également appelé bouton par défaut. Chaque fois que l’utilisateur appuie sur la touche entrée, le bouton par défaut est activé, quel que soit l’autre contrôle sur le formulaire.  
  
> [!NOTE]
> Les exceptions sont les cas où le contrôle ayant le focus est un autre bouton, dans ce cas, le bouton sur lequel le focus sera activé, ou une zone de texte multiligne, ou un contrôle personnalisé qui intercepte la touche entrée.  
  
### <a name="to-designate-the-accept-button"></a>Pour désigner le bouton accepter  
  
1. Définissez la propriété <xref:System.Windows.Forms.Form.AcceptButton%2A> du formulaire sur le contrôle <xref:System.Windows.Forms.Button> approprié.  
  
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
- [Guide pratique pour répondre à un clic du contrôle Button Windows Forms](how-to-respond-to-windows-forms-button-clicks.md)
- [Guide pratique pour désigner un contrôle Button Windows Forms en tant que bouton Annuler](how-to-designate-a-windows-forms-button-as-the-cancel-button.md)
- [Button, contrôle](button-control-windows-forms.md)
