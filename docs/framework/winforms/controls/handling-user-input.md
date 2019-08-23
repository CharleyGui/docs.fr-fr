---
title: Gestion des entrées utilisateur
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [Windows Forms], user input using code
- custom controls [Windows Forms], keyboard events using code
- custom controls [Windows Forms], mouse events using code
ms.assetid: d9b12787-86f6-4022-8e0f-e12d312c4af2
ms.openlocfilehash: f92b742c3f6feec72e5b3150204d7d984636281d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934094"
---
# <a name="handling-user-input"></a><span data-ttu-id="b265b-102">Gestion des entrées utilisateur</span><span class="sxs-lookup"><span data-stu-id="b265b-102">Handling User Input</span></span>
<span data-ttu-id="b265b-103">Cette rubrique décrit les principaux événements liés au clavier et à <xref:System.Windows.Forms.Control?displayProperty=nameWithType>la souris fournis par.</span><span class="sxs-lookup"><span data-stu-id="b265b-103">This topic describes the main keyboard and mouse events provided by <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span></span> <span data-ttu-id="b265b-104">Lors de la gestion d’un événement, les auteurs de contrôle doivent substituer la méthode protégée `On`*EventName* au lieu d’attacher un délégué à l’événement.</span><span class="sxs-lookup"><span data-stu-id="b265b-104">When handling an event, control authors should override the protected `On`*EventName* method rather than attaching a delegate to the event.</span></span> <span data-ttu-id="b265b-105">Pour un examen des événements, consultez [Déclenchement d’événements à partir d’un composant](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/sh2e3k5z(v=vs.120)).</span><span class="sxs-lookup"><span data-stu-id="b265b-105">For a review of events, see [Raising Events from a Component](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/sh2e3k5z(v=vs.120)).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b265b-106">Si aucune donnée n’est associée à un événement, une instance de la classe <xref:System.EventArgs> de base est passée comme argument à la `On`méthode *EventName* .</span><span class="sxs-lookup"><span data-stu-id="b265b-106">If there is no data associated with an event, an instance of the base class <xref:System.EventArgs> is passed as an argument to the `On`*EventName* method.</span></span>  
  
## <a name="keyboard-events"></a><span data-ttu-id="b265b-107">Événements de clavier</span><span class="sxs-lookup"><span data-stu-id="b265b-107">Keyboard Events</span></span>  
 <span data-ttu-id="b265b-108">Les événements de clavier courants que votre contrôle peut gérer <xref:System.Windows.Forms.Control.KeyDown>sont <xref:System.Windows.Forms.Control.KeyPress>, et <xref:System.Windows.Forms.Control.KeyUp>.</span><span class="sxs-lookup"><span data-stu-id="b265b-108">The common keyboard events that your control can handle are <xref:System.Windows.Forms.Control.KeyDown>, <xref:System.Windows.Forms.Control.KeyPress>, and <xref:System.Windows.Forms.Control.KeyUp>.</span></span>  
  
|<span data-ttu-id="b265b-109">Nom de l'événement</span><span class="sxs-lookup"><span data-stu-id="b265b-109">Event Name</span></span>|<span data-ttu-id="b265b-110">Méthode à substituer</span><span class="sxs-lookup"><span data-stu-id="b265b-110">Method to Override</span></span>|<span data-ttu-id="b265b-111">Description de l’événement</span><span class="sxs-lookup"><span data-stu-id="b265b-111">Description of Event</span></span>|  
|----------------|------------------------|--------------------------|  
|`KeyDown`|`void OnKeyDown(KeyEventArgs)`|<span data-ttu-id="b265b-112">Déclenché uniquement lorsque l’utilisateur appuie initialement sur une touche.</span><span class="sxs-lookup"><span data-stu-id="b265b-112">Raised only when a key is initially pressed.</span></span>|  
|`KeyPress`|`void OnKeyPress`<br /><br /> `(KeyPressEventArgs)`|<span data-ttu-id="b265b-113">Déclenché à chaque fois que l’utilisateur appuie sur une touche.</span><span class="sxs-lookup"><span data-stu-id="b265b-113">Raised every time a key is pressed.</span></span> <span data-ttu-id="b265b-114">Si une touche est maintenue enfoncée, un <xref:System.Windows.Forms.Control.KeyPress> événement est déclenché à la fréquence de répétition définie par le système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="b265b-114">If a key is held down, a <xref:System.Windows.Forms.Control.KeyPress> event is raised at the repeat rate defined by the operating system.</span></span>|  
|`KeyUp`|`void OnKeyUp(KeyEventArgs)`|<span data-ttu-id="b265b-115">Déclenché lors du relâchement d’une touche.</span><span class="sxs-lookup"><span data-stu-id="b265b-115">Raised when a key is released.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="b265b-116">La gestion des entrées sur le clavier est considérablement plus complexe que la substitution des événements dans le tableau précédent. Ce thème dépasse le cadre de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="b265b-116">Handling keyboard input is considerably more complex than overriding the events in the preceding table and is beyond the scope of this topic.</span></span> <span data-ttu-id="b265b-117">Pour plus d’informations, consultez [Entrée d’utilisateur dans Windows Forms](../user-input-in-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="b265b-117">For more information, see [User Input in Windows Forms](../user-input-in-windows-forms.md).</span></span>  
  
## <a name="mouse-events"></a><span data-ttu-id="b265b-118">Événements de souris</span><span class="sxs-lookup"><span data-stu-id="b265b-118">Mouse Events</span></span>  
 <span data-ttu-id="b265b-119">Les événements de souris que votre contrôle peut gérer <xref:System.Windows.Forms.Control.MouseDown>sont <xref:System.Windows.Forms.Control.MouseEnter> <xref:System.Windows.Forms.Control.MouseHover>, <xref:System.Windows.Forms.Control.MouseLeave> <xref:System.Windows.Forms.Control.MouseMove>,,, et <xref:System.Windows.Forms.Control.MouseUp>.</span><span class="sxs-lookup"><span data-stu-id="b265b-119">The mouse events that your control can handle are <xref:System.Windows.Forms.Control.MouseDown>, <xref:System.Windows.Forms.Control.MouseEnter>, <xref:System.Windows.Forms.Control.MouseHover>, <xref:System.Windows.Forms.Control.MouseLeave>, <xref:System.Windows.Forms.Control.MouseMove>, and <xref:System.Windows.Forms.Control.MouseUp>.</span></span>  
  
|<span data-ttu-id="b265b-120">Nom de l'événement</span><span class="sxs-lookup"><span data-stu-id="b265b-120">Event Name</span></span>|<span data-ttu-id="b265b-121">Méthode à substituer</span><span class="sxs-lookup"><span data-stu-id="b265b-121">Method to Override</span></span>|<span data-ttu-id="b265b-122">Description de l’événement</span><span class="sxs-lookup"><span data-stu-id="b265b-122">Description of Event</span></span>|  
|----------------|------------------------|--------------------------|  
|`MouseDown`|`void OnMouseDown(MouseEventArgs)`|<span data-ttu-id="b265b-123">Déclenché quand le bouton de la souris est enfoncé alors que le pointeur se trouve sur le contrôle.</span><span class="sxs-lookup"><span data-stu-id="b265b-123">Raised when the mouse button is pressed while the pointer is over the control.</span></span>|  
|`MouseEnter`|`void OnMouseEnter(EventArgs)`|<span data-ttu-id="b265b-124">Déclenché lorsque le pointeur pénètre la première fois dans la zone du contrôle.</span><span class="sxs-lookup"><span data-stu-id="b265b-124">Raised when the pointer first enters the region of the control.</span></span>|  
|`MouseHover`|`void OnMouseHover(EventArgs)`|<span data-ttu-id="b265b-125">Déclenché lorsque le pointeur pointe sur le contrôle.</span><span class="sxs-lookup"><span data-stu-id="b265b-125">Raised when the pointer hovers over the control.</span></span>|  
|`MouseLeave`|`void OnMouseLeave(EventArgs)`|<span data-ttu-id="b265b-126">Déclenché lorsque le pointeur quitte la zone du contrôle.</span><span class="sxs-lookup"><span data-stu-id="b265b-126">Raised when the pointer leaves the region of the control.</span></span>|  
|`MouseMove`|`void OnMouseMove(MouseEventArgs)`|<span data-ttu-id="b265b-127">Déclenché lorsque le pointeur se déplace dans la zone du contrôle.</span><span class="sxs-lookup"><span data-stu-id="b265b-127">Raised when the pointer moves in the region of the control.</span></span>|  
|`MouseUp`|`void OnMouseUp(MouseEventArgs)`|<span data-ttu-id="b265b-128">Déclenché lorsque le bouton de la souris est relâché alors que le pointeur se trouve sur le contrôle ou quitte la zone du contrôle.</span><span class="sxs-lookup"><span data-stu-id="b265b-128">Raised when the mouse button is released while the pointer is over the control or the pointer leaves the region of the control.</span></span>|  
  
 <span data-ttu-id="b265b-129">Le fragment de code suivant montre un exemple de substitution de <xref:System.Windows.Forms.Control.MouseDown> l’événement.</span><span class="sxs-lookup"><span data-stu-id="b265b-129">The following code fragment shows an example of overriding the <xref:System.Windows.Forms.Control.MouseDown> event.</span></span>  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#7](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#7)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#7](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#7)]  
  
 <span data-ttu-id="b265b-130">Le fragment de code suivant montre un exemple de substitution de <xref:System.Windows.Forms.Control.MouseMove> l’événement.</span><span class="sxs-lookup"><span data-stu-id="b265b-130">The following code fragment shows an example of overriding the <xref:System.Windows.Forms.Control.MouseMove> event.</span></span>  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#8](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#8)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#8](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#8)]  
  
 <span data-ttu-id="b265b-131">Le fragment de code suivant montre un exemple de substitution de <xref:System.Windows.Forms.Control.MouseUp> l’événement.</span><span class="sxs-lookup"><span data-stu-id="b265b-131">The following code fragment shows an example of overriding the <xref:System.Windows.Forms.Control.MouseUp> event.</span></span>  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#9](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#9)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#9](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#9)]  
  
 <span data-ttu-id="b265b-132">Pour obtenir le code source complet de `FlashTrackBar` l’exemple, [consultez Procédure: Créez un contrôle de Windows Forms qui affiche](how-to-create-a-windows-forms-control-that-shows-progress.md)la progression.</span><span class="sxs-lookup"><span data-stu-id="b265b-132">For the complete source code for the `FlashTrackBar` sample, see [How to: Create a Windows Forms Control That Shows Progress](how-to-create-a-windows-forms-control-that-shows-progress.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b265b-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b265b-133">See also</span></span>

- [<span data-ttu-id="b265b-134">Événements dans les contrôles Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b265b-134">Events in Windows Forms Controls</span></span>](events-in-windows-forms-controls.md)
- [<span data-ttu-id="b265b-135">Définition d’un événement</span><span class="sxs-lookup"><span data-stu-id="b265b-135">Defining an Event</span></span>](defining-an-event-in-windows-forms-controls.md)
- [<span data-ttu-id="b265b-136">Événements</span><span class="sxs-lookup"><span data-stu-id="b265b-136">Events</span></span>](../../../standard/events/index.md)
- [<span data-ttu-id="b265b-137">Entrées d’utilisateur dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b265b-137">User Input in Windows Forms</span></span>](../user-input-in-windows-forms.md)
