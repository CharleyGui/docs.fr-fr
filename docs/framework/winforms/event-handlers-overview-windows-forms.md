---
title: Vue d'ensemble des gestionnaires d'événements
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms, event handling
- event handling [Windows Forms], Windows Forms
- event handlers [Windows Forms], about event handlers
ms.assetid: 228112e1-1711-42ee-8ffa-ff3555bffe66
ms.openlocfilehash: 10ba458197973ede35849a86fec35003f139b8d2
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743494"
---
# <a name="event-handlers-overview-windows-forms"></a><span data-ttu-id="88571-102">Vue d'ensemble des gestionnaires d'événements (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="88571-102">Event Handlers Overview (Windows Forms)</span></span>
<span data-ttu-id="88571-103">Un gestionnaire d’événements est une méthode liée à un événement.</span><span class="sxs-lookup"><span data-stu-id="88571-103">An event handler is a method that is bound to an event.</span></span> <span data-ttu-id="88571-104">Lorsque l’événement est déclenché, le code dans le gestionnaire d’événements est exécuté.</span><span class="sxs-lookup"><span data-stu-id="88571-104">When the event is raised, the code within the event handler is executed.</span></span> <span data-ttu-id="88571-105">Chaque gestionnaire d’événements fournit deux paramètres qui vous permettent de gérer correctement l’événement.</span><span class="sxs-lookup"><span data-stu-id="88571-105">Each event handler provides two parameters that allow you to handle the event properly.</span></span> <span data-ttu-id="88571-106">L’exemple suivant montre un gestionnaire d’événements pour l’événement <xref:System.Windows.Forms.Control.Click> d’un contrôle <xref:System.Windows.Forms.Button>.</span><span class="sxs-lookup"><span data-stu-id="88571-106">The following example shows an event handler for a <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Click> event.</span></span>  
  
```vb  
Private Sub button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles button1.Click  
  
End Sub  
```  
  
```csharp  
private void button1_Click(object sender, System.EventArgs e)   
{  
  
}  
```  
  
```cpp  
private:  
  void button1_Click(System::Object ^ sender,  
    System::EventArgs ^ e)  
  {  
  
  }  
```  
  
 <span data-ttu-id="88571-107">Le premier paramètre,`sender`, fournit une référence à l’objet qui a déclenché l’événement.</span><span class="sxs-lookup"><span data-stu-id="88571-107">The first parameter,`sender`, provides a reference to the object that raised the event.</span></span> <span data-ttu-id="88571-108">Le deuxième paramètre, `e`, dans l’exemple ci-dessus, passe un objet spécifique à l’événement géré.</span><span class="sxs-lookup"><span data-stu-id="88571-108">The second parameter, `e`, in the example above, passes an object specific to the event that is being handled.</span></span> <span data-ttu-id="88571-109">En référençant les propriétés de l’objet (et, parfois, ses méthodes), vous pouvez obtenir des informations telles que l’emplacement de la souris pour les événements de souris ou les données transférées dans les événements de glisser-déplacer.</span><span class="sxs-lookup"><span data-stu-id="88571-109">By referencing the object's properties (and, sometimes, its methods), you can obtain information such as the location of the mouse for mouse events or data being transferred in drag-and-drop events.</span></span>  
  
 <span data-ttu-id="88571-110">En général, chaque événement produit un gestionnaire d’événements avec un type d’objet d’événement différent pour le deuxième paramètre.</span><span class="sxs-lookup"><span data-stu-id="88571-110">Typically each event produces an event handler with a different event-object type for the second parameter.</span></span> <span data-ttu-id="88571-111">Certains gestionnaires d’événements, tels que ceux des événements <xref:System.Windows.Forms.Control.MouseDown> et <xref:System.Windows.Forms.Control.MouseUp>, ont le même type d’objet pour leur deuxième paramètre.</span><span class="sxs-lookup"><span data-stu-id="88571-111">Some event handlers, such as those for the <xref:System.Windows.Forms.Control.MouseDown> and <xref:System.Windows.Forms.Control.MouseUp> events, have the same object type for their second parameter.</span></span> <span data-ttu-id="88571-112">Pour ces types d’événements, vous pouvez utiliser le même gestionnaire d’événements pour gérer les deux événements.</span><span class="sxs-lookup"><span data-stu-id="88571-112">For these types of events, you can use the same event handler to handle both events.</span></span>  
  
 <span data-ttu-id="88571-113">Vous pouvez également utiliser le même gestionnaire d’événements pour gérer le même événement pour différents contrôles.</span><span class="sxs-lookup"><span data-stu-id="88571-113">You can also use the same event handler to handle the same event for different controls.</span></span> <span data-ttu-id="88571-114">Par exemple, si vous avez un groupe de contrôles de <xref:System.Windows.Forms.RadioButton> sur un formulaire, vous pouvez créer un gestionnaire d’événements unique pour l’événement <xref:System.Windows.Forms.Control.Click> et faire en sorte que chaque événement du contrôle <xref:System.Windows.Forms.Control.Click> lié au gestionnaire d’événements unique.</span><span class="sxs-lookup"><span data-stu-id="88571-114">For example, if you have a group of <xref:System.Windows.Forms.RadioButton> controls on a form, you could create a single event handler for the <xref:System.Windows.Forms.Control.Click> event and have each control's <xref:System.Windows.Forms.Control.Click> event bound to the single event handler.</span></span> <span data-ttu-id="88571-115">Pour plus d’informations, consultez [Comment : connecter plusieurs événements à un même gestionnaire d’événements dans Windows Forms](how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="88571-115">For more information, see [How to: Connect Multiple Events to a Single Event Handler in Windows Forms](how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88571-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="88571-116">See also</span></span>

- [<span data-ttu-id="88571-117">Création de gestionnaires d’événements dans Windows Forms</span><span class="sxs-lookup"><span data-stu-id="88571-117">Creating Event Handlers in Windows Forms</span></span>](creating-event-handlers-in-windows-forms.md)
- [<span data-ttu-id="88571-118">Vue d'ensemble des événements</span><span class="sxs-lookup"><span data-stu-id="88571-118">Events Overview</span></span>](events-overview-windows-forms.md)
