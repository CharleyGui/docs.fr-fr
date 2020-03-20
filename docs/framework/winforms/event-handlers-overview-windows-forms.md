---
title: Vue d’ensemble des gestionnaires d’événements
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
ms.openlocfilehash: ffec8a9f8e080dec78152e62e00e2dceefbdaab0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141690"
---
# <a name="event-handlers-overview-windows-forms"></a><span data-ttu-id="9ebc6-102">Vue d'ensemble des gestionnaires d'événements (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="9ebc6-102">Event Handlers Overview (Windows Forms)</span></span>
<span data-ttu-id="9ebc6-103">Un gestionnaire d’événements est une méthode qui est liée à un événement.</span><span class="sxs-lookup"><span data-stu-id="9ebc6-103">An event handler is a method that is bound to an event.</span></span> <span data-ttu-id="9ebc6-104">Lorsque l’événement est déclenché, le code dans le gestionnaire de l’événement est exécuté.</span><span class="sxs-lookup"><span data-stu-id="9ebc6-104">When the event is raised, the code within the event handler is executed.</span></span> <span data-ttu-id="9ebc6-105">Chaque gestionnaire d’événements fournit deux paramètres qui vous permettent de gérer l’événement correctement.</span><span class="sxs-lookup"><span data-stu-id="9ebc6-105">Each event handler provides two parameters that allow you to handle the event properly.</span></span> <span data-ttu-id="9ebc6-106">L’exemple suivant montre un <xref:System.Windows.Forms.Button> gestionnaire <xref:System.Windows.Forms.Control.Click> d’événements pour l’événement d’un contrôle.</span><span class="sxs-lookup"><span data-stu-id="9ebc6-106">The following example shows an event handler for a <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Click> event.</span></span>  
  
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
  
 <span data-ttu-id="9ebc6-107">Le premier`sender`paramètre, fournit une référence à l’objet qui a soulevé l’événement.</span><span class="sxs-lookup"><span data-stu-id="9ebc6-107">The first parameter,`sender`, provides a reference to the object that raised the event.</span></span> <span data-ttu-id="9ebc6-108">Le deuxième `e`paramètre, dans l’exemple ci-dessus, passe un objet spécifique à l’événement qui est manipulé.</span><span class="sxs-lookup"><span data-stu-id="9ebc6-108">The second parameter, `e`, in the example above, passes an object specific to the event that is being handled.</span></span> <span data-ttu-id="9ebc6-109">En faisant référence aux propriétés de l’objet (et, parfois, à ses méthodes), vous pouvez obtenir des informations telles que l’emplacement de la souris pour les événements de souris ou les données transférées lors d’événements de drag-and-drop.</span><span class="sxs-lookup"><span data-stu-id="9ebc6-109">By referencing the object's properties (and, sometimes, its methods), you can obtain information such as the location of the mouse for mouse events or data being transferred in drag-and-drop events.</span></span>  
  
 <span data-ttu-id="9ebc6-110">En règle générale, chaque événement produit un gestionnaire d’événements avec un type d’objet d’événement différent pour le deuxième paramètre.</span><span class="sxs-lookup"><span data-stu-id="9ebc6-110">Typically each event produces an event handler with a different event-object type for the second parameter.</span></span> <span data-ttu-id="9ebc6-111">Certains gestionnaires d’événements, comme <xref:System.Windows.Forms.Control.MouseDown> <xref:System.Windows.Forms.Control.MouseUp> ceux pour les événements et les événements, ont le même type d’objet pour leur deuxième paramètre.</span><span class="sxs-lookup"><span data-stu-id="9ebc6-111">Some event handlers, such as those for the <xref:System.Windows.Forms.Control.MouseDown> and <xref:System.Windows.Forms.Control.MouseUp> events, have the same object type for their second parameter.</span></span> <span data-ttu-id="9ebc6-112">Pour ce type d’événements, vous pouvez utiliser le même gestionnaire d’événements pour gérer les deux événements.</span><span class="sxs-lookup"><span data-stu-id="9ebc6-112">For these types of events, you can use the same event handler to handle both events.</span></span>  
  
 <span data-ttu-id="9ebc6-113">Vous pouvez également utiliser le même gestionnaire d’événements pour gérer le même événement pour différents contrôles.</span><span class="sxs-lookup"><span data-stu-id="9ebc6-113">You can also use the same event handler to handle the same event for different controls.</span></span> <span data-ttu-id="9ebc6-114">Par exemple, si vous <xref:System.Windows.Forms.RadioButton> avez un groupe de contrôles sur un <xref:System.Windows.Forms.Control.Click> formulaire, vous pouvez <xref:System.Windows.Forms.Control.Click> créer un gestionnaire d’événement unique pour l’événement et avoir l’événement de chaque contrôle lié au gestionnaire d’événement unique.</span><span class="sxs-lookup"><span data-stu-id="9ebc6-114">For example, if you have a group of <xref:System.Windows.Forms.RadioButton> controls on a form, you could create a single event handler for the <xref:System.Windows.Forms.Control.Click> event and have each control's <xref:System.Windows.Forms.Control.Click> event bound to the single event handler.</span></span> <span data-ttu-id="9ebc6-115">Pour plus d’informations, voir [Comment : Connectez plusieurs événements à un gestionnaire d’événements unique dans les formulaires Windows](how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="9ebc6-115">For more information, see [How to: Connect Multiple Events to a Single Event Handler in Windows Forms](how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ebc6-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9ebc6-116">See also</span></span>

- [<span data-ttu-id="9ebc6-117">Création de gestionnaires d’événements dans Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9ebc6-117">Creating Event Handlers in Windows Forms</span></span>](creating-event-handlers-in-windows-forms.md)
- [<span data-ttu-id="9ebc6-118">Vue d'ensemble des événements</span><span class="sxs-lookup"><span data-stu-id="9ebc6-118">Events Overview</span></span>](events-overview-windows-forms.md)
