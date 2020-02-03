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
# <a name="how-to-designate-a-windows-forms-button-as-the-cancel-button"></a><span data-ttu-id="3016c-102">Comment : désigner un contrôle Button Windows Forms en tant que bouton Annuler</span><span class="sxs-lookup"><span data-stu-id="3016c-102">How to: Designate a Windows Forms Button as the Cancel Button</span></span>
<span data-ttu-id="3016c-103">Sur un formulaire Windows, vous pouvez désigner un contrôle de <xref:System.Windows.Forms.Button> comme bouton Annuler.</span><span class="sxs-lookup"><span data-stu-id="3016c-103">On any Windows Form, you can designate a <xref:System.Windows.Forms.Button> control to be the cancel button.</span></span> <span data-ttu-id="3016c-104">Un clic est effectué sur un bouton Annuler chaque fois que l’utilisateur appuie sur la touche ÉCHAP, quel que soit le contrôle du formulaire actif.</span><span class="sxs-lookup"><span data-stu-id="3016c-104">A cancel button is clicked whenever the user presses the ESC key, regardless of which other control on the form has the focus.</span></span> <span data-ttu-id="3016c-105">Un tel bouton est généralement programmé pour permettre à l’utilisateur de quitter rapidement une opération sans valider aucune action.</span><span class="sxs-lookup"><span data-stu-id="3016c-105">Such a button is usually programmed to enable the user to quickly exit an operation without committing to any action.</span></span>  
  
### <a name="to-designate-the-cancel-button"></a><span data-ttu-id="3016c-106">Pour désigner le bouton Annuler</span><span class="sxs-lookup"><span data-stu-id="3016c-106">To designate the cancel button</span></span>  
  
1. <span data-ttu-id="3016c-107">Définissez la propriété <xref:System.Windows.Forms.Form.CancelButton%2A> du formulaire sur le contrôle <xref:System.Windows.Forms.Button> approprié.</span><span class="sxs-lookup"><span data-stu-id="3016c-107">Set the form's <xref:System.Windows.Forms.Form.CancelButton%2A> property to the appropriate <xref:System.Windows.Forms.Button> control.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3016c-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3016c-108">See also</span></span>

- <xref:System.Windows.Forms.Form.CancelButton%2A>
- [<span data-ttu-id="3016c-109">Vue d'ensemble du contrôle Button</span><span class="sxs-lookup"><span data-stu-id="3016c-109">Button Control Overview</span></span>](button-control-overview-windows-forms.md)
- [<span data-ttu-id="3016c-110">Méthodes de sélection du contrôle Button Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3016c-110">Ways to Select a Windows Forms Button Control</span></span>](ways-to-select-a-windows-forms-button-control.md)
- [<span data-ttu-id="3016c-111">Guide pratique pour répondre à un clic du contrôle Button Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3016c-111">How to: Respond to Windows Forms Button Clicks</span></span>](how-to-respond-to-windows-forms-button-clicks.md)
- [<span data-ttu-id="3016c-112">Guide pratique pour désigner un contrôle Button Windows Forms comme bouton Accepter</span><span class="sxs-lookup"><span data-stu-id="3016c-112">How to: Designate a Windows Forms Button as the Accept Button</span></span>](how-to-designate-a-windows-forms-button-as-the-accept-button.md)
- [<span data-ttu-id="3016c-113">Button, contrôle</span><span class="sxs-lookup"><span data-stu-id="3016c-113">Button Control</span></span>](button-control-windows-forms.md)
