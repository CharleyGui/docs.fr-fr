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
# <a name="how-to-designate-a-windows-forms-button-as-the-accept-button"></a><span data-ttu-id="128c8-102">Comment : désigner un contrôle Button Windows Forms comme bouton Accepter</span><span class="sxs-lookup"><span data-stu-id="128c8-102">How to: Designate a Windows Forms Button as the Accept Button</span></span>
<span data-ttu-id="128c8-103">Sur n’importe quel formulaire <xref:System.Windows.Forms.Button> Windows, vous pouvez désigner un contrôle pour être le bouton d’acceptation, également connu sous le nom de bouton par défaut.</span><span class="sxs-lookup"><span data-stu-id="128c8-103">On any Windows Form, you can designate a <xref:System.Windows.Forms.Button> control to be the accept button, also known as the default button.</span></span> <span data-ttu-id="128c8-104">Chaque fois que l’utilisateur appuie sur la touche ENTER, le bouton par défaut est cliqué quel que soit le contrôle du formulaire.</span><span class="sxs-lookup"><span data-stu-id="128c8-104">Whenever the user presses the ENTER key, the default button is clicked regardless of which other control on the form has the focus.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="128c8-105">Les exceptions à cela sont lorsque le contrôle avec mise au point est un autre bouton - dans ce cas, le bouton avec la mise au point sera cliqué - ou une boîte de texte multiline, ou un contrôle personnalisé qui piège la touche ENTER.</span><span class="sxs-lookup"><span data-stu-id="128c8-105">The exceptions to this are when the control with focus is another button — in that case, the button with the focus will be clicked — or a multiline text box, or a custom control that traps the ENTER key.</span></span>  
  
### <a name="to-designate-the-accept-button"></a><span data-ttu-id="128c8-106">Pour désigner le bouton accepter</span><span class="sxs-lookup"><span data-stu-id="128c8-106">To designate the accept button</span></span>  
  
1. <span data-ttu-id="128c8-107">Définissez la <xref:System.Windows.Forms.Form.AcceptButton%2A> propriété du <xref:System.Windows.Forms.Button> formulaire au contrôle approprié.</span><span class="sxs-lookup"><span data-stu-id="128c8-107">Set the form's <xref:System.Windows.Forms.Form.AcceptButton%2A> property to the appropriate <xref:System.Windows.Forms.Button> control.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="128c8-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="128c8-108">See also</span></span>

- <xref:System.Windows.Forms.Form.AcceptButton%2A>
- [<span data-ttu-id="128c8-109">Vue d'ensemble du contrôle Button</span><span class="sxs-lookup"><span data-stu-id="128c8-109">Button Control Overview</span></span>](button-control-overview-windows-forms.md)
- [<span data-ttu-id="128c8-110">Méthodes de sélection du contrôle Button Windows Forms</span><span class="sxs-lookup"><span data-stu-id="128c8-110">Ways to Select a Windows Forms Button Control</span></span>](ways-to-select-a-windows-forms-button-control.md)
- [<span data-ttu-id="128c8-111">Comment : répondre à un clic du contrôle Button Windows Forms</span><span class="sxs-lookup"><span data-stu-id="128c8-111">How to: Respond to Windows Forms Button Clicks</span></span>](how-to-respond-to-windows-forms-button-clicks.md)
- [<span data-ttu-id="128c8-112">Comment : désigner un contrôle Button Windows Forms en tant que bouton Annuler</span><span class="sxs-lookup"><span data-stu-id="128c8-112">How to: Designate a Windows Forms Button as the Cancel Button</span></span>](how-to-designate-a-windows-forms-button-as-the-cancel-button.md)
- [<span data-ttu-id="128c8-113">Button, contrôle</span><span class="sxs-lookup"><span data-stu-id="128c8-113">Button Control</span></span>](button-control-windows-forms.md)
