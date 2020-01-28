---
title: 'Comment : connecter plusieurs événements à un même gestionnaire d’événements'
ms.date: 03/30/2017
dev_langs:
- vb
helpviewer_keywords:
- events [Windows Forms], connecting multiple to single event handler
- event handlers [Windows Forms], connecting events to
- menus [Windows Forms], event-handling methods for multiple menu items
- Windows Forms controls, events
- menu items [Windows Forms], multicasting event-handling methods
ms.assetid: 5a20749a-41b5-4acc-8eb1-9e5040b0a2c4
ms.openlocfilehash: 0591291522ab1da04fef90bf1c0a73cf33ba0518
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76739609"
---
# <a name="how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms"></a><span data-ttu-id="16e55-102">Comment : connecter plusieurs événements à un même gestionnaire d'événements dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="16e55-102">How to: Connect Multiple Events to a Single Event Handler in Windows Forms</span></span>
<span data-ttu-id="16e55-103">Dans la conception de votre application, il peut s’avérer nécessaire d’utiliser un seul gestionnaire d’événements pour plusieurs événements ou de faire en sorte que plusieurs événements effectuent la même procédure.</span><span class="sxs-lookup"><span data-stu-id="16e55-103">In your application design, you may find it necessary to use a single event handler for multiple events or have multiple events perform the same procedure.</span></span> <span data-ttu-id="16e55-104">Par exemple, il est souvent plus efficace de faire en sorte qu’une commande de menu génère le même événement qu’un bouton de votre formulaire si elle expose la même fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="16e55-104">For example, it is often a powerful time-saver to have a menu command raise the same event as a button on your form does if they expose the same functionality.</span></span> <span data-ttu-id="16e55-105">Pour ce faire, vous pouvez utiliser la vue événements de la Fenêtre Propriétés C# dans ou à l’aide du mot clé `Handles` et des zones de liste déroulante nom de la **classe** et nom de la **méthode** dans l’éditeur de code Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="16e55-105">You can do this by using the Events view of the Properties window in C# or using the `Handles` keyword and the **Class Name** and **Method Name** drop-down boxes in the Visual Basic Code Editor.</span></span>  
  
### <a name="to-connect-multiple-events-to-a-single-event-handler-in-visual-basic"></a><span data-ttu-id="16e55-106">Pour connecter plusieurs événements à un même gestionnaire d’événements dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="16e55-106">To connect multiple events to a single event handler in Visual Basic</span></span>  
  
1. <span data-ttu-id="16e55-107">Cliquez avec le bouton droit sur le formulaire, puis choisissez **afficher le code**.</span><span class="sxs-lookup"><span data-stu-id="16e55-107">Right-click the form and choose **View Code**.</span></span>  
  
2. <span data-ttu-id="16e55-108">Dans la zone de liste déroulante nom de la **classe** , sélectionnez l’un des contrôles dont vous souhaitez obtenir le handle de gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="16e55-108">From the **Class Name** drop-down box, select one of the controls that you want to have the event handler handle.</span></span>  
  
3. <span data-ttu-id="16e55-109">Dans la zone de liste déroulante nom de la **méthode** , sélectionnez l’un des événements que vous souhaitez que le gestionnaire d’événements gère.</span><span class="sxs-lookup"><span data-stu-id="16e55-109">From the **Method Name** drop-down box, select one of the events that you want the event handler to handle.</span></span>  
  
4. <span data-ttu-id="16e55-110">L’éditeur de code insère le gestionnaire d’événements approprié et positionne le point d’insertion dans la méthode.</span><span class="sxs-lookup"><span data-stu-id="16e55-110">The Code Editor inserts the appropriate event handler and positions the insertion point within the method.</span></span> <span data-ttu-id="16e55-111">Dans l’exemple ci-dessous, il s’agit de l’événement <xref:System.Windows.Forms.Control.Click> pour le contrôle <xref:System.Windows.Forms.Button>.</span><span class="sxs-lookup"><span data-stu-id="16e55-111">In the example below, it is the <xref:System.Windows.Forms.Control.Click> event for the <xref:System.Windows.Forms.Button> control.</span></span>  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
    ' Add event-handler code here.  
    End Sub  
    ```  
  
5. <span data-ttu-id="16e55-112">Ajoutez les autres événements que vous souhaitez gérer à la clause `Handles`.</span><span class="sxs-lookup"><span data-stu-id="16e55-112">Append the other events you would like handled to the `Handles` clause.</span></span>  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click, Button2.Click  
    ' Add event-handler code here.  
    End Sub  
    ```  
  
6. <span data-ttu-id="16e55-113">Ajoutez le code approprié au gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="16e55-113">Add the appropriate code to the event handler.</span></span>  
  
### <a name="to-connect-multiple-events-to-a-single-event-handler-in-c"></a><span data-ttu-id="16e55-114">Pour connecter plusieurs événements à un même gestionnaire d’événements en C\#</span><span class="sxs-lookup"><span data-stu-id="16e55-114">To connect multiple events to a single event handler in C\#</span></span>
  
1. <span data-ttu-id="16e55-115">Sélectionnez le contrôle auquel vous souhaitez connecter un gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="16e55-115">Select the control to which you want to connect an event handler.</span></span>  
  
2. <span data-ttu-id="16e55-116">Dans le Fenêtre Propriétés, cliquez sur le bouton **événements** (![bouton événements](./media/vxeventsbutton-propertieswindow.png "vxEventsButton_PropertiesWindow")).</span><span class="sxs-lookup"><span data-stu-id="16e55-116">In the Properties window, click the **Events** button (![Events Button](./media/vxeventsbutton-propertieswindow.png "vxEventsButton_PropertiesWindow")).</span></span>  
  
3. <span data-ttu-id="16e55-117">Cliquez sur le nom de l’événement que vous souhaitez gérer.</span><span class="sxs-lookup"><span data-stu-id="16e55-117">Click the name of the event that you want to handle.</span></span>  
  
4. <span data-ttu-id="16e55-118">Dans la section valeur en regard du nom de l’événement, cliquez sur le bouton déroulant pour afficher la liste des gestionnaires d’événements existants qui correspondent à la signature de la méthode de l’événement que vous souhaitez gérer.</span><span class="sxs-lookup"><span data-stu-id="16e55-118">In the value section next to the event name, click the drop-down button to display a list of existing event handlers that match the method signature of the event you want to handle.</span></span>  
  
5. <span data-ttu-id="16e55-119">Sélectionnez le gestionnaire d’événements approprié dans la liste.</span><span class="sxs-lookup"><span data-stu-id="16e55-119">Select the appropriate event handler from the list.</span></span>  
  
     <span data-ttu-id="16e55-120">Du code sera ajouté au formulaire pour lier l’événement au gestionnaire d’événements existant.</span><span class="sxs-lookup"><span data-stu-id="16e55-120">Code will be added to the form to bind the event to the existing event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16e55-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="16e55-121">See also</span></span>

- [<span data-ttu-id="16e55-122">Création de gestionnaires d’événements dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="16e55-122">Creating Event Handlers in Windows Forms</span></span>](creating-event-handlers-in-windows-forms.md)
- [<span data-ttu-id="16e55-123">Vue d'ensemble des gestionnaires d'événements</span><span class="sxs-lookup"><span data-stu-id="16e55-123">Event Handlers Overview</span></span>](event-handlers-overview-windows-forms.md)
