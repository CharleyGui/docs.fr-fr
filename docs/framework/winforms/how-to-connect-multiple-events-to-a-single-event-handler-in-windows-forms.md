---
title: 'Comment : connecter plusieurs événements à un même gestionnaire d’événements'
description: Découvrez comment connecter plusieurs événements à un même gestionnaire d’événements dans Windows Forms à l’aide de la vue événements du Fenêtre Propriétés en C#.
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
ms.openlocfilehash: cca85c223b46d9a82dbc3e34e3377fb83c075959
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621884"
---
# <a name="how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms"></a><span data-ttu-id="01a70-103">Procédure : connecter plusieurs événements à un seul gestionnaire d’événements dans Windows Forms</span><span class="sxs-lookup"><span data-stu-id="01a70-103">How to: Connect Multiple Events to a Single Event Handler in Windows Forms</span></span>
<span data-ttu-id="01a70-104">Dans la conception de votre application, il peut s’avérer nécessaire d’utiliser un seul gestionnaire d’événements pour plusieurs événements ou de faire en sorte que plusieurs événements effectuent la même procédure.</span><span class="sxs-lookup"><span data-stu-id="01a70-104">In your application design, you may find it necessary to use a single event handler for multiple events or have multiple events perform the same procedure.</span></span> <span data-ttu-id="01a70-105">Par exemple, il est souvent plus efficace de faire en sorte qu’une commande de menu génère le même événement qu’un bouton de votre formulaire si elle expose la même fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="01a70-105">For example, it is often a powerful time-saver to have a menu command raise the same event as a button on your form does if they expose the same functionality.</span></span> <span data-ttu-id="01a70-106">Pour ce faire, vous pouvez utiliser la vue événements de l’Fenêtre Propriétés en C# ou le `Handles` mot clé et les zones de liste déroulante nom de la **classe** et nom de la **méthode** dans l’éditeur de code Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="01a70-106">You can do this by using the Events view of the Properties window in C# or using the `Handles` keyword and the **Class Name** and **Method Name** drop-down boxes in the Visual Basic Code Editor.</span></span>  
  
### <a name="to-connect-multiple-events-to-a-single-event-handler-in-visual-basic"></a><span data-ttu-id="01a70-107">Pour connecter plusieurs événements à un même gestionnaire d’événements dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="01a70-107">To connect multiple events to a single event handler in Visual Basic</span></span>  
  
1. <span data-ttu-id="01a70-108">Cliquez avec le bouton droit sur le formulaire, puis choisissez **afficher le code**.</span><span class="sxs-lookup"><span data-stu-id="01a70-108">Right-click the form and choose **View Code**.</span></span>  
  
2. <span data-ttu-id="01a70-109">Dans la zone de liste déroulante nom de la **classe** , sélectionnez l’un des contrôles dont vous souhaitez obtenir le handle de gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="01a70-109">From the **Class Name** drop-down box, select one of the controls that you want to have the event handler handle.</span></span>  
  
3. <span data-ttu-id="01a70-110">Dans la zone de liste déroulante nom de la **méthode** , sélectionnez l’un des événements que vous souhaitez que le gestionnaire d’événements gère.</span><span class="sxs-lookup"><span data-stu-id="01a70-110">From the **Method Name** drop-down box, select one of the events that you want the event handler to handle.</span></span>  
  
4. <span data-ttu-id="01a70-111">L’éditeur de code insère le gestionnaire d’événements approprié et positionne le point d’insertion dans la méthode.</span><span class="sxs-lookup"><span data-stu-id="01a70-111">The Code Editor inserts the appropriate event handler and positions the insertion point within the method.</span></span> <span data-ttu-id="01a70-112">Dans l’exemple ci-dessous, il s’agit <xref:System.Windows.Forms.Control.Click> de l’événement pour le <xref:System.Windows.Forms.Button> contrôle.</span><span class="sxs-lookup"><span data-stu-id="01a70-112">In the example below, it is the <xref:System.Windows.Forms.Control.Click> event for the <xref:System.Windows.Forms.Button> control.</span></span>  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
    ' Add event-handler code here.  
    End Sub  
    ```  
  
5. <span data-ttu-id="01a70-113">Ajoutez les autres événements que vous souhaitez gérer à la `Handles` clause.</span><span class="sxs-lookup"><span data-stu-id="01a70-113">Append the other events you would like handled to the `Handles` clause.</span></span>  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click, Button2.Click  
    ' Add event-handler code here.  
    End Sub  
    ```  
  
6. <span data-ttu-id="01a70-114">Ajoutez le code approprié au gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="01a70-114">Add the appropriate code to the event handler.</span></span>  
  
### <a name="to-connect-multiple-events-to-a-single-event-handler-in-c"></a><span data-ttu-id="01a70-115">Pour connecter plusieurs événements à un même gestionnaire d’événements en C\#</span><span class="sxs-lookup"><span data-stu-id="01a70-115">To connect multiple events to a single event handler in C\#</span></span>
  
1. <span data-ttu-id="01a70-116">Sélectionnez le contrôle auquel vous souhaitez connecter un gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="01a70-116">Select the control to which you want to connect an event handler.</span></span>  
  
2. <span data-ttu-id="01a70-117">Dans le Fenêtre Propriétés, cliquez sur le bouton **événements** (![bouton événements](./media/vxeventsbutton-propertieswindow.png "vxEventsButton_PropertiesWindow")).</span><span class="sxs-lookup"><span data-stu-id="01a70-117">In the Properties window, click the **Events** button (![Events Button](./media/vxeventsbutton-propertieswindow.png "vxEventsButton_PropertiesWindow")).</span></span>  
  
3. <span data-ttu-id="01a70-118">Cliquez sur le nom de l’événement que vous souhaitez gérer.</span><span class="sxs-lookup"><span data-stu-id="01a70-118">Click the name of the event that you want to handle.</span></span>  
  
4. <span data-ttu-id="01a70-119">Dans la section valeur en regard du nom de l’événement, cliquez sur le bouton déroulant pour afficher la liste des gestionnaires d’événements existants qui correspondent à la signature de la méthode de l’événement que vous souhaitez gérer.</span><span class="sxs-lookup"><span data-stu-id="01a70-119">In the value section next to the event name, click the drop-down button to display a list of existing event handlers that match the method signature of the event you want to handle.</span></span>  
  
5. <span data-ttu-id="01a70-120">Sélectionnez le gestionnaire d’événements approprié dans la liste.</span><span class="sxs-lookup"><span data-stu-id="01a70-120">Select the appropriate event handler from the list.</span></span>  
  
     <span data-ttu-id="01a70-121">Du code sera ajouté au formulaire pour lier l’événement au gestionnaire d’événements existant.</span><span class="sxs-lookup"><span data-stu-id="01a70-121">Code will be added to the form to bind the event to the existing event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01a70-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="01a70-122">See also</span></span>

- [<span data-ttu-id="01a70-123">Création de gestionnaires d'événements dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="01a70-123">Creating Event Handlers in Windows Forms</span></span>](creating-event-handlers-in-windows-forms.md)
- [<span data-ttu-id="01a70-124">Vue d’ensemble des gestionnaires d’événements</span><span class="sxs-lookup"><span data-stu-id="01a70-124">Event Handlers Overview</span></span>](event-handlers-overview-windows-forms.md)
