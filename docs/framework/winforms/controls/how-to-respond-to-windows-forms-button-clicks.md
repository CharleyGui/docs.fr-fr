---
title: répondre aux clics de bouton
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- buttons [Windows Forms], responding to Click events
- events [Windows Forms], Click events
- Click event [Windows Forms], Button control
- MouseDown event
- Button control [Windows Forms], click response
- double-clicks
- examples [Windows Forms], controls
- Click event [Windows Forms], responding to
ms.assetid: 7a4951bd-369c-4662-b246-28ad83eda484
ms.openlocfilehash: dd6cf75a316257c86a23b44a818422336c12aa67
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76735718"
---
# <a name="how-to-respond-to-windows-forms-button-clicks"></a><span data-ttu-id="e434c-102">Comment : répondre à un clic du contrôle Button Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e434c-102">How to: Respond to Windows Forms Button Clicks</span></span>
<span data-ttu-id="e434c-103">L’utilisation la plus simple d’un contrôle de Windows Forms <xref:System.Windows.Forms.Button> consiste à exécuter du code suite à un clic sur le bouton.</span><span class="sxs-lookup"><span data-stu-id="e434c-103">The most basic use of a Windows Forms <xref:System.Windows.Forms.Button> control is to run some code when the button is clicked.</span></span>  
  
 <span data-ttu-id="e434c-104">En cliquant sur un contrôle <xref:System.Windows.Forms.Button>, vous générez également un certain nombre d’autres événements, tels que les événements <xref:System.Windows.Forms.Control.MouseEnter>, <xref:System.Windows.Forms.Control.MouseDown>et <xref:System.Windows.Forms.Control.MouseUp>.</span><span class="sxs-lookup"><span data-stu-id="e434c-104">Clicking a <xref:System.Windows.Forms.Button> control also generates a number of other events, such as the <xref:System.Windows.Forms.Control.MouseEnter>, <xref:System.Windows.Forms.Control.MouseDown>, and <xref:System.Windows.Forms.Control.MouseUp> events.</span></span> <span data-ttu-id="e434c-105">Si vous envisagez d’attacher des gestionnaires d’événements pour ces événements connexes, assurez-vous que leurs actions ne sont pas en conflit.</span><span class="sxs-lookup"><span data-stu-id="e434c-105">If you intend to attach event handlers for these related events, be sure that their actions do not conflict.</span></span> <span data-ttu-id="e434c-106">Par exemple, si le fait de cliquer sur le bouton efface les informations que l’utilisateur a tapées dans une zone de texte, la suspension du pointeur de la souris sur le bouton ne doit pas afficher d’info-bulle avec des informations qui sont maintenant inexistantes.</span><span class="sxs-lookup"><span data-stu-id="e434c-106">For example, if clicking the button clears information that the user has typed in a text box, pausing the mouse pointer over the button should not display a tool tip with that now-nonexistent information.</span></span>  
  
 <span data-ttu-id="e434c-107">Si l’utilisateur tente de double-cliquer sur le contrôle <xref:System.Windows.Forms.Button>, chaque clic est traité séparément. autrement dit, le contrôle ne prend pas en charge l’événement de double-clic.</span><span class="sxs-lookup"><span data-stu-id="e434c-107">If the user attempts to double-click the <xref:System.Windows.Forms.Button> control, each click will be processed separately; that is, the control does not support the double-click event.</span></span>  
  
### <a name="to-respond-to-a-button-click"></a><span data-ttu-id="e434c-108">Pour répondre à un clic sur un bouton</span><span class="sxs-lookup"><span data-stu-id="e434c-108">To respond to a button click</span></span>  
  
- <span data-ttu-id="e434c-109">Dans le `Click` du bouton <xref:System.EventHandler> écrivez le code à exécuter.</span><span class="sxs-lookup"><span data-stu-id="e434c-109">In the button's `Click` <xref:System.EventHandler> write the code to run.</span></span> <span data-ttu-id="e434c-110">`Button1_Click` doit être lié au contrôle.</span><span class="sxs-lookup"><span data-stu-id="e434c-110">`Button1_Click` must be bound to the control.</span></span> <span data-ttu-id="e434c-111">Pour plus d’informations, consultez [Comment : créer des gestionnaires d’événements au moment de l’exécution pour Windows Forms](../how-to-create-event-handlers-at-run-time-for-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="e434c-111">For more information, see [How to: Create Event Handlers at Run Time for Windows Forms](../how-to-create-event-handlers-at-run-time-for-windows-forms.md).</span></span>  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
       MessageBox.Show("Button1 was clicked")  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)  
    {  
       MessageBox.Show("button1 was clicked");  
    }  
    ```  
  
    ```cpp  
    private:  
       void button1_Click(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          MessageBox::Show("button1 was clicked");  
       }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="e434c-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e434c-112">See also</span></span>

- [<span data-ttu-id="e434c-113">Vue d'ensemble du contrôle Button</span><span class="sxs-lookup"><span data-stu-id="e434c-113">Button Control Overview</span></span>](button-control-overview-windows-forms.md)
- [<span data-ttu-id="e434c-114">Méthodes de sélection du contrôle Button Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e434c-114">Ways to Select a Windows Forms Button Control</span></span>](ways-to-select-a-windows-forms-button-control.md)
- [<span data-ttu-id="e434c-115">Button, contrôle</span><span class="sxs-lookup"><span data-stu-id="e434c-115">Button Control</span></span>](button-control-windows-forms.md)
