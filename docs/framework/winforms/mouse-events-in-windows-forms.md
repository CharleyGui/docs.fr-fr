---
title: Événements de souris
ms.date: 03/30/2017
helpviewer_keywords:
- MouseLeave event [Windows Forms]
- events [Windows Forms], mouse
- Click event [Windows Forms], raising order
- Windows Forms controls, click events
- MouseDoubleClick event [Windows Forms]
- MouseEnter event [Windows Forms]
- MouseHover event [Windows Forms]
- MouseDown event [Windows Forms]
- MouseClick event [Windows Forms]
- MouseMove event [Windows Forms]
- mouse [Windows Forms], events
- MouseUp event
ms.assetid: 8cf0070d-793b-4876-b09e-d20d28280fab
ms.openlocfilehash: 4909f56fc3935848fd18bc35c1cb56b5407a24c8
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76740965"
---
# <a name="mouse-events-in-windows-forms"></a><span data-ttu-id="a5783-102">Événements liés à la souris dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a5783-102">Mouse Events in Windows Forms</span></span>

<span data-ttu-id="a5783-103">Quand vous gérez l'entrée de souris, vous souhaitez habituellement connaître l'emplacement du pointeur de la souris et l'état de ses boutons.</span><span class="sxs-lookup"><span data-stu-id="a5783-103">When you handle mouse input, you usually want to know the location of the mouse pointer and the state of the mouse buttons.</span></span> <span data-ttu-id="a5783-104">Cette rubrique fournit des détails sur la façon d'obtenir des informations à partir des événements de souris et explique l'ordre dans lequel les événements de clic de souris sont déclenchés dans les contrôles Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="a5783-104">This topic provides details on how to get this information from mouse events, and explains the order in which mouse click events are raised in Windows Forms controls.</span></span> <span data-ttu-id="a5783-105">Pour obtenir la liste et la description de tous les événements de la souris, consultez [fonctionnement de l’entrée de la souris dans Windows Forms](how-mouse-input-works-in-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="a5783-105">For a list and description of all of the mouse events, see [How Mouse Input Works in Windows Forms](how-mouse-input-works-in-windows-forms.md).</span></span>  <span data-ttu-id="a5783-106">Consultez également [vue d’ensemble des gestionnaires d’événements (Windows Forms)](event-handlers-overview-windows-forms.md) et [vue d’ensemble des événements (Windows Forms)](events-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="a5783-106">Also see [Event Handlers Overview (Windows Forms)](event-handlers-overview-windows-forms.md) and [Events Overview (Windows Forms)](events-overview-windows-forms.md).</span></span>

## <a name="mouse-information"></a><span data-ttu-id="a5783-107">Informations sur la souris</span><span class="sxs-lookup"><span data-stu-id="a5783-107">Mouse Information</span></span>

<span data-ttu-id="a5783-108">Un <xref:System.Windows.Forms.MouseEventArgs> est envoyé aux gestionnaires d'événements de souris liés aux clics de souris et au suivi des mouvements de souris.</span><span class="sxs-lookup"><span data-stu-id="a5783-108">A <xref:System.Windows.Forms.MouseEventArgs> is sent to the handlers of mouse events related to clicking a mouse button and tracking mouse movements.</span></span> <span data-ttu-id="a5783-109"><xref:System.Windows.Forms.MouseEventArgs> fournit des informations sur l'état actuel de la souris, y compris l'emplacement du pointeur de la souris sous forme de coordonnées clientes, les boutons de souris qui sont enfoncés et si la roulette a défilé.</span><span class="sxs-lookup"><span data-stu-id="a5783-109"><xref:System.Windows.Forms.MouseEventArgs> provides information about the current state of the mouse, including the location of the mouse pointer in client coordinates, which mouse buttons are pressed, and whether the mouse wheel has scrolled.</span></span> <span data-ttu-id="a5783-110">Plusieurs événements de souris, tels que ceux qui indiquent simplement si le pointeur de souris pénétré ou quitté les limites d'un contrôle, envoient un <xref:System.EventArgs> au gestionnaire d'événements sans aucune information complémentaire.</span><span class="sxs-lookup"><span data-stu-id="a5783-110">Several mouse events, such as those that simply notify when the mouse pointer has entered or left the bounds of a control, send an <xref:System.EventArgs> to the event handler with no further information.</span></span>

<span data-ttu-id="a5783-111">Si vous souhaitez connaître l'état actuel des boutons de la souris ou l'emplacement du pointeur de la souris et que vous souhaitez éviter de gérer un événement de souris, vous pouvez aussi utiliser les propriétés <xref:System.Windows.Forms.Control.MouseButtons%2A> et <xref:System.Windows.Forms.Control.MousePosition%2A> de la classe <xref:System.Windows.Forms.Control>.</span><span class="sxs-lookup"><span data-stu-id="a5783-111">If you want to know the current state of the mouse buttons or the location of the mouse pointer, and you want to avoid handling a mouse event, you can also use the <xref:System.Windows.Forms.Control.MouseButtons%2A> and <xref:System.Windows.Forms.Control.MousePosition%2A> properties of the <xref:System.Windows.Forms.Control> class.</span></span> <span data-ttu-id="a5783-112"><xref:System.Windows.Forms.Control.MouseButtons%2A> retourne des informations sur les boutons de souris qui sont actuellement enfoncés.</span><span class="sxs-lookup"><span data-stu-id="a5783-112"><xref:System.Windows.Forms.Control.MouseButtons%2A> returns information about which mouse buttons are currently pressed.</span></span> <span data-ttu-id="a5783-113"><xref:System.Windows.Forms.Control.MousePosition%2A> retourne les coordonnées d'écran du pointeur de la souris et est équivalente à la valeur retournée par <xref:System.Windows.Forms.Cursor.Position%2A>.</span><span class="sxs-lookup"><span data-stu-id="a5783-113">The <xref:System.Windows.Forms.Control.MousePosition%2A> returns the screen coordinates of the mouse pointer and is equivalent to the value returned by <xref:System.Windows.Forms.Cursor.Position%2A>.</span></span>

## <a name="converting-between-screen-and-client-coordinates"></a><span data-ttu-id="a5783-114">Conversion entre les coordonnées clientes et d'écran</span><span class="sxs-lookup"><span data-stu-id="a5783-114">Converting Between Screen and Client Coordinates</span></span>

<span data-ttu-id="a5783-115">Étant donné que certaines informations sur l'emplacement de la souris sont spécifiées en coordonnées clientes et d'autres en coordonnées d'écran, vous devrez peut-être convertir un point d'un système de coordonnées en un autre.</span><span class="sxs-lookup"><span data-stu-id="a5783-115">Because some mouse location information is in client coordinates and some is in screen coordinates, you may need to convert a point from one coordinate system to the other.</span></span> <span data-ttu-id="a5783-116">Cette opération peut être effectuée facilement à l'aide des méthodes <xref:System.Windows.Forms.Control.PointToClient%2A> et <xref:System.Windows.Forms.Control.PointToScreen%2A> disponibles sur la classe <xref:System.Windows.Forms.Control>.</span><span class="sxs-lookup"><span data-stu-id="a5783-116">You can do this easily by using the <xref:System.Windows.Forms.Control.PointToClient%2A> and <xref:System.Windows.Forms.Control.PointToScreen%2A> methods available on the <xref:System.Windows.Forms.Control> class.</span></span>

## <a name="standard-click-event-behavior"></a><span data-ttu-id="a5783-117">Comportement d'événement de clic standard</span><span class="sxs-lookup"><span data-stu-id="a5783-117">Standard Click Event Behavior</span></span>

<span data-ttu-id="a5783-118">Si vous souhaitez gérer les événements de clic de souris dans l'ordre approprié, vous devez connaître l'ordre dans lequel les événements de clic sont déclenchés dans les contrôles Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="a5783-118">If you want to handle mouse click events in the proper order, you need to know the order in which click events are raised in Windows Forms controls.</span></span> <span data-ttu-id="a5783-119">Tous les contrôles Windows Forms déclenchent les événements de clic dans le même ordre quand un bouton de souris est enfoncé et relâché (quel que soit le bouton), sauf indication contraire mentionnée dans la liste suivante pour un contrôle spécifique.</span><span class="sxs-lookup"><span data-stu-id="a5783-119">All Windows Forms controls raise click events in the same order when a mouse button is pressed and released (regardless of which mouse button), except where noted in the following list for individual controls.</span></span> <span data-ttu-id="a5783-120">La liste ci-dessous indique l'ordre des événements déclenchés pour un clic sur un bouton de souris :</span><span class="sxs-lookup"><span data-stu-id="a5783-120">The following list shows the order of events raised for a single mouse-button click:</span></span>

1. <span data-ttu-id="a5783-121">Événement<xref:System.Windows.Forms.Control.MouseDown> .</span><span class="sxs-lookup"><span data-stu-id="a5783-121"><xref:System.Windows.Forms.Control.MouseDown> event.</span></span>

2. <span data-ttu-id="a5783-122">Événement<xref:System.Windows.Forms.Control.Click> .</span><span class="sxs-lookup"><span data-stu-id="a5783-122"><xref:System.Windows.Forms.Control.Click> event.</span></span>

3. <span data-ttu-id="a5783-123">Événement<xref:System.Windows.Forms.Control.MouseClick> .</span><span class="sxs-lookup"><span data-stu-id="a5783-123"><xref:System.Windows.Forms.Control.MouseClick> event.</span></span>

4. <span data-ttu-id="a5783-124">Événement<xref:System.Windows.Forms.Control.MouseUp> .</span><span class="sxs-lookup"><span data-stu-id="a5783-124"><xref:System.Windows.Forms.Control.MouseUp> event.</span></span>

<span data-ttu-id="a5783-125">Voici l’ordre des événements déclenchés pour un clic double-bouton de la souris :</span><span class="sxs-lookup"><span data-stu-id="a5783-125">The following is the order of events raised for a double mouse-button click:</span></span>

1. <span data-ttu-id="a5783-126">Événement<xref:System.Windows.Forms.Control.MouseDown> .</span><span class="sxs-lookup"><span data-stu-id="a5783-126"><xref:System.Windows.Forms.Control.MouseDown> event.</span></span>

2. <span data-ttu-id="a5783-127">Événement<xref:System.Windows.Forms.Control.Click> .</span><span class="sxs-lookup"><span data-stu-id="a5783-127"><xref:System.Windows.Forms.Control.Click> event.</span></span>

3. <span data-ttu-id="a5783-128">Événement<xref:System.Windows.Forms.Control.MouseClick> .</span><span class="sxs-lookup"><span data-stu-id="a5783-128"><xref:System.Windows.Forms.Control.MouseClick> event.</span></span>

4. <span data-ttu-id="a5783-129">Événement<xref:System.Windows.Forms.Control.MouseUp> .</span><span class="sxs-lookup"><span data-stu-id="a5783-129"><xref:System.Windows.Forms.Control.MouseUp> event.</span></span>

5. <span data-ttu-id="a5783-130">Événement<xref:System.Windows.Forms.Control.MouseDown> .</span><span class="sxs-lookup"><span data-stu-id="a5783-130"><xref:System.Windows.Forms.Control.MouseDown> event.</span></span>

6. <span data-ttu-id="a5783-131">Événement<xref:System.Windows.Forms.Control.DoubleClick> .</span><span class="sxs-lookup"><span data-stu-id="a5783-131"><xref:System.Windows.Forms.Control.DoubleClick> event.</span></span> <span data-ttu-id="a5783-132">(Cela peut varier, selon que le contrôle en question a la valeur <xref:System.Windows.Forms.ControlStyles.StandardDoubleClick> définie comme bit de style `true`.</span><span class="sxs-lookup"><span data-stu-id="a5783-132">(This can vary, depending on whether the control in question has the <xref:System.Windows.Forms.ControlStyles.StandardDoubleClick> style bit set to `true`.</span></span> <span data-ttu-id="a5783-133">Pour plus d'informations sur la façon de définir un bit <xref:System.Windows.Forms.ControlStyles>, consultez la méthode <xref:System.Windows.Forms.Control.SetStyle%2A>.)</span><span class="sxs-lookup"><span data-stu-id="a5783-133">For more information about how to set a <xref:System.Windows.Forms.ControlStyles> bit, see the <xref:System.Windows.Forms.Control.SetStyle%2A> method.)</span></span>

7. <span data-ttu-id="a5783-134">Événement<xref:System.Windows.Forms.Control.MouseDoubleClick> .</span><span class="sxs-lookup"><span data-stu-id="a5783-134"><xref:System.Windows.Forms.Control.MouseDoubleClick> event.</span></span>

8. <span data-ttu-id="a5783-135">Événement<xref:System.Windows.Forms.Control.MouseUp> .</span><span class="sxs-lookup"><span data-stu-id="a5783-135"><xref:System.Windows.Forms.Control.MouseUp> event.</span></span>

<span data-ttu-id="a5783-136">Pour obtenir un exemple de code illustrant l’ordre des événements de clic de souris, consultez [Comment : gérer des événements d’entrée d’utilisateur dans les contrôles de Windows Forms](how-to-handle-user-input-events-in-windows-forms-controls.md).</span><span class="sxs-lookup"><span data-stu-id="a5783-136">For a code example that demonstrates the order of the mouse click events, see [How to: Handle User Input Events in Windows Forms Controls](how-to-handle-user-input-events-in-windows-forms-controls.md).</span></span>

### <a name="individual-controls"></a><span data-ttu-id="a5783-137">Contrôles spécifiques</span><span class="sxs-lookup"><span data-stu-id="a5783-137">Individual Controls</span></span>

<span data-ttu-id="a5783-138">Les contrôles suivants n'ont pas le comportement d'événement de clic de souris standard :</span><span class="sxs-lookup"><span data-stu-id="a5783-138">The following controls do not conform to the standard mouse click event behavior:</span></span>

- <xref:System.Windows.Forms.Button>
- <xref:System.Windows.Forms.CheckBox>
- <xref:System.Windows.Forms.ComboBox>
- <xref:System.Windows.Forms.RadioButton>

  > [!NOTE]
  > <span data-ttu-id="a5783-139">Pour le contrôle <xref:System.Windows.Forms.ComboBox>, le comportement d'événement détaillé plus loin se produit si l'utilisateur clique sur le champ d'édition, le bouton ou un élément dans la liste.</span><span class="sxs-lookup"><span data-stu-id="a5783-139">For the <xref:System.Windows.Forms.ComboBox> control, the event behavior detailed later occurs if the user clicks on the edit field, the button, or on an item within the list.</span></span>

  - <span data-ttu-id="a5783-140">Clic gauche : <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span><span class="sxs-lookup"><span data-stu-id="a5783-140">Left click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span></span>

  - <span data-ttu-id="a5783-141">Clic droit : aucun événement de clic déclenché</span><span class="sxs-lookup"><span data-stu-id="a5783-141">Right click: No click events raised</span></span>

  - <span data-ttu-id="a5783-142">Double-clic gauche : <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick> ; <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span><span class="sxs-lookup"><span data-stu-id="a5783-142">Left double-click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span></span>

  - <span data-ttu-id="a5783-143">Double-clic droit : aucun événement de clic déclenché</span><span class="sxs-lookup"><span data-stu-id="a5783-143">Right double-click: No click events raised</span></span>

- <span data-ttu-id="a5783-144">Contrôles <xref:System.Windows.Forms.TextBox>, <xref:System.Windows.Forms.RichTextBox>, <xref:System.Windows.Forms.ListBox>, <xref:System.Windows.Forms.MaskedTextBox> et <xref:System.Windows.Forms.CheckedListBox></span><span class="sxs-lookup"><span data-stu-id="a5783-144"><xref:System.Windows.Forms.TextBox>, <xref:System.Windows.Forms.RichTextBox>, <xref:System.Windows.Forms.ListBox>, <xref:System.Windows.Forms.MaskedTextBox>, and <xref:System.Windows.Forms.CheckedListBox> controls</span></span>

  > [!NOTE]
  > <span data-ttu-id="a5783-145">Le comportement d'événement détaillé plus loin se produit quand l'utilisateur clique dans ces contrôles.</span><span class="sxs-lookup"><span data-stu-id="a5783-145">The event behavior detailed later occurs when the user clicks anywhere within these controls.</span></span>

  - <span data-ttu-id="a5783-146">Clic gauche : <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span><span class="sxs-lookup"><span data-stu-id="a5783-146">Left click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span></span>

  - <span data-ttu-id="a5783-147">Clic droit : aucun événement de clic déclenché</span><span class="sxs-lookup"><span data-stu-id="a5783-147">Right click: No click events raised</span></span>

  - <span data-ttu-id="a5783-148">Double-clic gauche : <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>, <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span><span class="sxs-lookup"><span data-stu-id="a5783-148">Left double-click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>, <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span></span>

  - <span data-ttu-id="a5783-149">Double-clic droit : aucun événement de clic déclenché</span><span class="sxs-lookup"><span data-stu-id="a5783-149">Right double-click: No click events raised</span></span>

- <span data-ttu-id="a5783-150">Contrôle <xref:System.Windows.Forms.ListView></span><span class="sxs-lookup"><span data-stu-id="a5783-150"><xref:System.Windows.Forms.ListView> control</span></span>

  > [!NOTE]
  > <span data-ttu-id="a5783-151">Le comportement d'événement détaillé plus loin se produit quand l'utilisateur clique sur les éléments dans le contrôle <xref:System.Windows.Forms.ListView>.</span><span class="sxs-lookup"><span data-stu-id="a5783-151">The event behavior detailed later occurs only when the user clicks on the items in the <xref:System.Windows.Forms.ListView> control.</span></span> <span data-ttu-id="a5783-152">Aucun événement n'est déclenché si l'utilisateur clique ailleurs sur le contrôle.</span><span class="sxs-lookup"><span data-stu-id="a5783-152">No events are raised for clicks anywhere else on the control.</span></span> <span data-ttu-id="a5783-153">Outre les événements décrits plus loin, il existe les événements <xref:System.Windows.Forms.ListView.BeforeLabelEdit> et <xref:System.Windows.Forms.ListView.AfterLabelEdit>, qui peuvent être utiles si vous souhaitez utiliser la validation avec le contrôle <xref:System.Windows.Forms.ListView>.</span><span class="sxs-lookup"><span data-stu-id="a5783-153">In addition to the events described later, there are the <xref:System.Windows.Forms.ListView.BeforeLabelEdit> and <xref:System.Windows.Forms.ListView.AfterLabelEdit> events, which may be of interest to you if you want to use validation with the <xref:System.Windows.Forms.ListView> control.</span></span>

  - <span data-ttu-id="a5783-154">Clic gauche : <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span><span class="sxs-lookup"><span data-stu-id="a5783-154">Left click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span></span>

  - <span data-ttu-id="a5783-155">Clic droit : <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span><span class="sxs-lookup"><span data-stu-id="a5783-155">Right click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span></span>

  - <span data-ttu-id="a5783-156">Double-clic gauche : <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick> ; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span><span class="sxs-lookup"><span data-stu-id="a5783-156">Left double-click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span></span>

  - <span data-ttu-id="a5783-157">Double-clic droit : <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick> ; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span><span class="sxs-lookup"><span data-stu-id="a5783-157">Right double-click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span></span>

- <span data-ttu-id="a5783-158">Contrôle <xref:System.Windows.Forms.TreeView></span><span class="sxs-lookup"><span data-stu-id="a5783-158"><xref:System.Windows.Forms.TreeView> control</span></span>

  > [!NOTE]
  > <span data-ttu-id="a5783-159">Le comportement d'événement détaillé plus loin se produit uniquement quand l'utilisateur clique sur les éléments proprement dits ou à droite des éléments dans le contrôle <xref:System.Windows.Forms.TreeView>.</span><span class="sxs-lookup"><span data-stu-id="a5783-159">The event behavior detailed later occurs only when the user clicks on the items themselves or to the right of the items in the <xref:System.Windows.Forms.TreeView> control.</span></span> <span data-ttu-id="a5783-160">Aucun événement n'est déclenché si l'utilisateur clique ailleurs sur le contrôle.</span><span class="sxs-lookup"><span data-stu-id="a5783-160">No events are raised for clicks anywhere else on the control.</span></span> <span data-ttu-id="a5783-161">Outre ceux décrits plus loin, il existe les événements <xref:System.Windows.Forms.TreeView.BeforeCheck>, <xref:System.Windows.Forms.TreeView.BeforeSelect>, <xref:System.Windows.Forms.TreeView.BeforeLabelEdit>, <xref:System.Windows.Forms.TreeView.AfterSelect>, <xref:System.Windows.Forms.TreeView.AfterCheck> et <xref:System.Windows.Forms.TreeView.AfterLabelEdit>, qui peuvent être utiles si vous souhaitez utiliser la validation avec le contrôle <xref:System.Windows.Forms.TreeView>.</span><span class="sxs-lookup"><span data-stu-id="a5783-161">In addition to those described later, there are the <xref:System.Windows.Forms.TreeView.BeforeCheck>, <xref:System.Windows.Forms.TreeView.BeforeSelect>, <xref:System.Windows.Forms.TreeView.BeforeLabelEdit>, <xref:System.Windows.Forms.TreeView.AfterSelect>, <xref:System.Windows.Forms.TreeView.AfterCheck>, and <xref:System.Windows.Forms.TreeView.AfterLabelEdit> events, which may be of interest to you if you want to use validation with the <xref:System.Windows.Forms.TreeView> control.</span></span>

  - <span data-ttu-id="a5783-162">Clic gauche : <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span><span class="sxs-lookup"><span data-stu-id="a5783-162">Left click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span></span>

  - <span data-ttu-id="a5783-163">Clic droit : <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span><span class="sxs-lookup"><span data-stu-id="a5783-163">Right click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span></span>

  - <span data-ttu-id="a5783-164">Double-clic gauche : <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick> ; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span><span class="sxs-lookup"><span data-stu-id="a5783-164">Left double-click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span></span>

  - <span data-ttu-id="a5783-165">Double-clic droit : <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick> ; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span><span class="sxs-lookup"><span data-stu-id="a5783-165">Right double-click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span></span>

### <a name="painting-behavior-of-toggle-controls"></a><span data-ttu-id="a5783-166">Comportement de peinture des contrôles Toggle</span><span class="sxs-lookup"><span data-stu-id="a5783-166">Painting behavior of toggle controls</span></span>

<span data-ttu-id="a5783-167">Les contrôles de basculement, tels que ceux dérivant de la classe <xref:System.Windows.Forms.ButtonBase>, présentent le comportement de peinture distinctif suivant en cas de combinaison avec des événements de clic de souris :</span><span class="sxs-lookup"><span data-stu-id="a5783-167">Toggle controls, such as the controls deriving from the <xref:System.Windows.Forms.ButtonBase> class, have the following distinctive painting behavior in combination with mouse click events:</span></span>

1. <span data-ttu-id="a5783-168">L'utilisateur appuie sur le bouton de la souris.</span><span class="sxs-lookup"><span data-stu-id="a5783-168">The user presses the mouse button.</span></span>

2. <span data-ttu-id="a5783-169">Le contrôle est peint à l'état enfoncé.</span><span class="sxs-lookup"><span data-stu-id="a5783-169">The control paints in the pressed state.</span></span>

3. <span data-ttu-id="a5783-170">L'événement <xref:System.Windows.Forms.Control.MouseDown> est déclenché.</span><span class="sxs-lookup"><span data-stu-id="a5783-170">The <xref:System.Windows.Forms.Control.MouseDown> event is raised.</span></span>

4. <span data-ttu-id="a5783-171">L’utilisateur relâche le bouton de la souris.</span><span class="sxs-lookup"><span data-stu-id="a5783-171">The user releases the mouse button.</span></span>

5. <span data-ttu-id="a5783-172">Le contrôle est peint à l'état déclenché.</span><span class="sxs-lookup"><span data-stu-id="a5783-172">The control paints in the raised state.</span></span>

6. <span data-ttu-id="a5783-173">L'événement <xref:System.Windows.Forms.Control.Click> est déclenché.</span><span class="sxs-lookup"><span data-stu-id="a5783-173">The <xref:System.Windows.Forms.Control.Click> event is raised.</span></span>

7. <span data-ttu-id="a5783-174">L'événement <xref:System.Windows.Forms.Control.MouseClick> est déclenché.</span><span class="sxs-lookup"><span data-stu-id="a5783-174">The <xref:System.Windows.Forms.Control.MouseClick> event is raised.</span></span>

8. <span data-ttu-id="a5783-175">L'événement <xref:System.Windows.Forms.Control.MouseUp> est déclenché.</span><span class="sxs-lookup"><span data-stu-id="a5783-175">The <xref:System.Windows.Forms.Control.MouseUp> event is raised.</span></span>

    > [!NOTE]
    > <span data-ttu-id="a5783-176">Si l'utilisateur déplace le pointeur hors du contrôle de basculement alors que le bouton de la souris est enfoncé (par exemple en cas de déplacement de la souris hors du contrôle <xref:System.Windows.Forms.Button> pendant qu'il est enfoncé), le contrôle de basculement est peint à l'état déclenché et seul l'événement <xref:System.Windows.Forms.Control.MouseUp> se produit.</span><span class="sxs-lookup"><span data-stu-id="a5783-176">If the user moves the pointer out of the toggle control while the mouse button is down (such as moving the mouse off the <xref:System.Windows.Forms.Button> control while it is pressed), the toggle control will paint in the raised state and only the <xref:System.Windows.Forms.Control.MouseUp> event occurs.</span></span> <span data-ttu-id="a5783-177">L'événement <xref:System.Windows.Forms.Control.Click> ou <xref:System.Windows.Forms.Control.MouseClick> ne se produira pas dans cette situation.</span><span class="sxs-lookup"><span data-stu-id="a5783-177">The <xref:System.Windows.Forms.Control.Click> or <xref:System.Windows.Forms.Control.MouseClick> events will not occur in this situation.</span></span>

## <a name="see-also"></a><span data-ttu-id="a5783-178">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a5783-178">See also</span></span>

- [<span data-ttu-id="a5783-179">Entrée de la souris dans une application Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a5783-179">Mouse Input in a Windows Forms Application</span></span>](mouse-input-in-a-windows-forms-application.md)
