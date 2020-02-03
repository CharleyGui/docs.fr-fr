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
# <a name="how-to-designate-a-windows-forms-button-as-the-accept-button"></a><span data-ttu-id="8b93f-102">Comment : désigner un contrôle Button Windows Forms comme bouton Accepter</span><span class="sxs-lookup"><span data-stu-id="8b93f-102">How to: Designate a Windows Forms Button as the Accept Button</span></span>
<span data-ttu-id="8b93f-103">Sur un formulaire Windows, vous pouvez désigner un contrôle de <xref:System.Windows.Forms.Button> comme bouton accepter, également appelé bouton par défaut.</span><span class="sxs-lookup"><span data-stu-id="8b93f-103">On any Windows Form, you can designate a <xref:System.Windows.Forms.Button> control to be the accept button, also known as the default button.</span></span> <span data-ttu-id="8b93f-104">Chaque fois que l’utilisateur appuie sur la touche entrée, le bouton par défaut est activé, quel que soit l’autre contrôle sur le formulaire.</span><span class="sxs-lookup"><span data-stu-id="8b93f-104">Whenever the user presses the ENTER key, the default button is clicked regardless of which other control on the form has the focus.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8b93f-105">Les exceptions sont les cas où le contrôle ayant le focus est un autre bouton, dans ce cas, le bouton sur lequel le focus sera activé, ou une zone de texte multiligne, ou un contrôle personnalisé qui intercepte la touche entrée.</span><span class="sxs-lookup"><span data-stu-id="8b93f-105">The exceptions to this are when the control with focus is another button — in that case, the button with the focus will be clicked — or a multiline text box, or a custom control that traps the ENTER key.</span></span>  
  
### <a name="to-designate-the-accept-button"></a><span data-ttu-id="8b93f-106">Pour désigner le bouton accepter</span><span class="sxs-lookup"><span data-stu-id="8b93f-106">To designate the accept button</span></span>  
  
1. <span data-ttu-id="8b93f-107">Définissez la propriété <xref:System.Windows.Forms.Form.AcceptButton%2A> du formulaire sur le contrôle <xref:System.Windows.Forms.Button> approprié.</span><span class="sxs-lookup"><span data-stu-id="8b93f-107">Set the form's <xref:System.Windows.Forms.Form.AcceptButton%2A> property to the appropriate <xref:System.Windows.Forms.Button> control.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8b93f-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8b93f-108">See also</span></span>

- <xref:System.Windows.Forms.Form.AcceptButton%2A>
- [<span data-ttu-id="8b93f-109">Vue d'ensemble du contrôle Button</span><span class="sxs-lookup"><span data-stu-id="8b93f-109">Button Control Overview</span></span>](button-control-overview-windows-forms.md)
- [<span data-ttu-id="8b93f-110">Méthodes de sélection du contrôle Button Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8b93f-110">Ways to Select a Windows Forms Button Control</span></span>](ways-to-select-a-windows-forms-button-control.md)
- [<span data-ttu-id="8b93f-111">Guide pratique pour répondre à un clic du contrôle Button Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8b93f-111">How to: Respond to Windows Forms Button Clicks</span></span>](how-to-respond-to-windows-forms-button-clicks.md)
- [<span data-ttu-id="8b93f-112">Guide pratique pour désigner un contrôle Button Windows Forms en tant que bouton Annuler</span><span class="sxs-lookup"><span data-stu-id="8b93f-112">How to: Designate a Windows Forms Button as the Cancel Button</span></span>](how-to-designate-a-windows-forms-button-as-the-cancel-button.md)
- [<span data-ttu-id="8b93f-113">Button, contrôle</span><span class="sxs-lookup"><span data-stu-id="8b93f-113">Button Control</span></span>](button-control-windows-forms.md)
