---
title: Événements de souris
description: Apprenez à obtenir l’emplacement de la souris à partir des événements de souris et à comprendre l’ordre dans lequel les événements de clic de souris sont déclenchés dans les contrôles Windows Forms.
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
ms.openlocfilehash: 640448109961ea5fdf3600ef9e72d7d10e8c9e49
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174378"
---
# <a name="mouse-events-in-windows-forms"></a><span data-ttu-id="2fa1c-103">Événements liés à la souris dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2fa1c-103">Mouse Events in Windows Forms</span></span>

<span data-ttu-id="2fa1c-104">Quand vous gérez l'entrée de souris, vous souhaitez habituellement connaître l'emplacement du pointeur de la souris et l'état de ses boutons.</span><span class="sxs-lookup"><span data-stu-id="2fa1c-104">When you handle mouse input, you usually want to know the location of the mouse pointer and the state of the mouse buttons.</span></span> <span data-ttu-id="2fa1c-105">Cette rubrique fournit des détails sur la façon d'obtenir des informations à partir des événements de souris et explique l'ordre dans lequel les événements de clic de souris sont déclenchés dans les contrôles Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="2fa1c-105">This topic provides details on how to get this information from mouse events, and explains the order in which mouse click events are raised in Windows Forms controls.</span></span> <span data-ttu-id="2fa1c-106">Pour obtenir la liste et la description de tous les événements de la souris, consultez [fonctionnement de l’entrée de la souris dans Windows Forms](how-mouse-input-works-in-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="2fa1c-106">For a list and description of all of the mouse events, see [How Mouse Input Works in Windows Forms](how-mouse-input-works-in-windows-forms.md).</span></span>  <span data-ttu-id="2fa1c-107">Consultez également [vue d’ensemble des gestionnaires d’événements (Windows Forms)](event-handlers-overview-windows-forms.md) et [vue d’ensemble des événements (Windows Forms)](events-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="2fa1c-107">Also see [Event Handlers Overview (Windows Forms)](event-handlers-overview-windows-forms.md) and [Events Overview (Windows Forms)](events-overview-windows-forms.md).</span></span>

## <a name="mouse-information"></a><span data-ttu-id="2fa1c-108">Informations sur la souris</span><span class="sxs-lookup"><span data-stu-id="2fa1c-108">Mouse Information</span></span>

<span data-ttu-id="2fa1c-109">Un <xref:System.Windows.Forms.MouseEventArgs> est envoyé aux gestionnaires d'événements de souris liés aux clics de souris et au suivi des mouvements de souris.</span><span class="sxs-lookup"><span data-stu-id="2fa1c-109">A <xref:System.Windows.Forms.MouseEventArgs> is sent to the handlers of mouse events related to clicking a mouse button and tracking mouse movements.</span></span> <span data-ttu-id="2fa1c-110"><xref:System.Windows.Forms.MouseEventArgs> fournit des informations sur l'état actuel de la souris, y compris l'emplacement du pointeur de la souris sous forme de coordonnées clientes, les boutons de souris qui sont enfoncés et si la roulette a défilé.</span><span class="sxs-lookup"><span data-stu-id="2fa1c-110"><xref:System.Windows.Forms.MouseEventArgs> provides information about the current state of the mouse, including the location of the mouse pointer in client coordinates, which mouse buttons are pressed, and whether the mouse wheel has scrolled.</span></span> <span data-ttu-id="2fa1c-111">Plusieurs événements de souris, tels que ceux qui indiquent simplement si le pointeur de souris pénétré ou quitté les limites d'un contrôle, envoient un <xref:System.EventArgs> au gestionnaire d'événements sans aucune information complémentaire.</span><span class="sxs-lookup"><span data-stu-id="2fa1c-111">Several mouse events, such as those that simply notify when the mouse pointer has entered or left the bounds of a control, send an <xref:System.EventArgs> to the event handler with no further information.</span></span>

<span data-ttu-id="2fa1c-112">Si vous souhaitez connaître l'état actuel des boutons de la souris ou l'emplacement du pointeur de la souris et que vous souhaitez éviter de gérer un événement de souris, vous pouvez aussi utiliser les propriétés <xref:System.Windows.Forms.Control.MouseButtons%2A> et <xref:System.Windows.Forms.Control.MousePosition%2A> de la classe <xref:System.Windows.Forms.Control>.</span><span class="sxs-lookup"><span data-stu-id="2fa1c-112">If you want to know the current state of the mouse buttons or the location of the mouse pointer, and you want to avoid handling a mouse event, you can also use the <xref:System.Windows.Forms.Control.MouseButtons%2A> and <xref:System.Windows.Forms.Control.MousePosition%2A> properties of the <xref:System.Windows.Forms.Control> class.</span></span> <span data-ttu-id="2fa1c-113"><xref:System.Windows.Forms.Control.MouseButtons%2A> retourne des informations sur les boutons de souris qui sont actuellement enfoncés.</span><span class="sxs-lookup"><span data-stu-id="2fa1c-113"><xref:System.Windows.Forms.Control.MouseButtons%2A> returns information about which mouse buttons are currently pressed.</span></span> <span data-ttu-id="2fa1c-114"><xref:System.Windows.Forms.Control.MousePosition%2A> retourne les coordonnées d'écran du pointeur de la souris et est équivalente à la valeur retournée par <xref:System.Windows.Forms.Cursor.Position%2A>.</span><span class="sxs-lookup"><span data-stu-id="2fa1c-114">The <xref:System.Windows.Forms.Control.MousePosition%2A> returns the screen coordinates of the mouse pointer and is equivalent to the value returned by <xref:System.Windows.Forms.Cursor.Position%2A>.</span></span>

## <a name="converting-between-screen-and-client-coordinates"></a><span data-ttu-id="2fa1c-115">Conversion entre les coordonnées clientes et d'écran</span><span class="sxs-lookup"><span data-stu-id="2fa1c-115">Converting Between Screen and Client Coordinates</span></span>

<span data-ttu-id="2fa1c-116">Étant donné que certaines informations sur l'emplacement de la souris sont spécifiées en coordonnées clientes et d'autres en coordonnées d'écran, vous devrez peut-être convertir un point d'un système de coordonnées en un autre.</span><span class="sxs-lookup"><span data-stu-id="2fa1c-116">Because some mouse location information is in client coordinates and some is in screen coordinates, you may need to convert a point from one coordinate system to the other.</span></span> <span data-ttu-id="2fa1c-117">Cette opération peut être effectuée facilement à l'aide des méthodes <xref:System.Windows.Forms.Control.PointToClient%2A> et <xref:System.Windows.Forms.Control.PointToScreen%2A> disponibles sur la classe <xref:System.Windows.Forms.Control>.</span><span class="sxs-lookup"><span data-stu-id="2fa1c-117">You can do this easily by using the <xref:System.Windows.Forms.Control.PointToClient%2A> and <xref:System.Windows.Forms.Control.PointToScreen%2A> methods available on the <xref:System.Windows.Forms.Control> class.</span></span>

## <a name="standard-click-event-behavior"></a><span data-ttu-id="2fa1c-118">Comportement d'événement de clic standard</span><span class="sxs-lookup"><span data-stu-id="2fa1c-118">Standard Click Event Behavior</span></span>

<span data-ttu-id="2fa1c-119">Si vous souhaitez gérer les événements de clic de souris dans l'ordre approprié, vous devez connaître l'ordre dans lequel les événements de clic sont déclenchés dans les contrôles Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="2fa1c-119">If you want to handle mouse click events in the proper order, you need to know the order in which click events are raised in Windows Forms controls.</span></span> <span data-ttu-id="2fa1c-120">Tous les contrôles Windows Forms déclenchent les événements de clic dans le même ordre quand un bouton de souris est enfoncé et relâché (quel que soit le bouton), sauf indication contraire mentionnée dans la liste suivante pour un contrôle spécifique.</span><span class="sxs-lookup"><span data-stu-id="2fa1c-120">All Windows Forms controls raise click events in the same order when a mouse button is pressed and released (regardless of which mouse button), except where noted in the following list for individual controls.</span></span> <span data-ttu-id="2fa1c-121">La liste ci-dessous indique l'ordre des événements déclenchés pour un clic sur un bouton de souris :</span><span class="sxs-lookup"><span data-stu-id="2fa1c-121">The following list shows the order of events raised for a single mouse-button click:</span></span>

1. <span data-ttu-id="2fa1c-122">Événement<xref:System.Windows.Forms.Control.MouseDown> .</span><span class="sxs-lookup"><span data-stu-id="2fa1c-122"><xref:System.Windows.Forms.Control.MouseDown> event.</span></span>

2. <span data-ttu-id="2fa1c-123">Événement<xref:System.Windows.Forms.Control.Click> .</span><span class="sxs-lookup"><span data-stu-id="2fa1c-123"><xref:System.Windows.Forms.Control.Click> event.</span></span>

3. <span data-ttu-id="2fa1c-124">Événement<xref:System.Windows.Forms.Control.MouseClick> .</span><span class="sxs-lookup"><span data-stu-id="2fa1c-124"><xref:System.Windows.Forms.Control.MouseClick> event.</span></span>

4. <span data-ttu-id="2fa1c-125">Événement<xref:System.Windows.Forms.Control.MouseUp> .</span><span class="sxs-lookup"><span data-stu-id="2fa1c-125"><xref:System.Windows.Forms.Control.MouseUp> event.</span></span>

<span data-ttu-id="2fa1c-126">Voici l’ordre des événements déclenchés pour un clic double-bouton de la souris :</span><span class="sxs-lookup"><span data-stu-id="2fa1c-126">The following is the order of events raised for a double mouse-button click:</span></span>

1. <span data-ttu-id="2fa1c-127">Événement<xref:System.Windows.Forms.Control.MouseDown> .</span><span class="sxs-lookup"><span data-stu-id="2fa1c-127"><xref:System.Windows.Forms.Control.MouseDown> event.</span></span>

2. <span data-ttu-id="2fa1c-128">Événement<xref:System.Windows.Forms.Control.Click> .</span><span class="sxs-lookup"><span data-stu-id="2fa1c-128"><xref:System.Windows.Forms.Control.Click> event.</span></span>

3. <span data-ttu-id="2fa1c-129">Événement<xref:System.Windows.Forms.Control.MouseClick> .</span><span class="sxs-lookup"><span data-stu-id="2fa1c-129"><xref:System.Windows.Forms.Control.MouseClick> event.</span></span>

4. <span data-ttu-id="2fa1c-130">Événement<xref:System.Windows.Forms.Control.MouseUp> .</span><span class="sxs-lookup"><span data-stu-id="2fa1c-130"><xref:System.Windows.Forms.Control.MouseUp> event.</span></span>

5. <span data-ttu-id="2fa1c-131">Événement<xref:System.Windows.Forms.Control.MouseDown> .</span><span class="sxs-lookup"><span data-stu-id="2fa1c-131"><xref:System.Windows.Forms.Control.MouseDown> event.</span></span>

6. <span data-ttu-id="2fa1c-132">Événement<xref:System.Windows.Forms.Control.DoubleClick> .</span><span class="sxs-lookup"><span data-stu-id="2fa1c-132"><xref:System.Windows.Forms.Control.DoubleClick> event.</span></span> <span data-ttu-id="2fa1c-133">(Cela peut varier, selon que le contrôle en question a la valeur <xref:System.Windows.Forms.ControlStyles.StandardDoubleClick> définie comme bit de style `true`.</span><span class="sxs-lookup"><span data-stu-id="2fa1c-133">(This can vary, depending on whether the control in question has the <xref:System.Windows.Forms.ControlStyles.StandardDoubleClick> style bit set to `true`.</span></span> <span data-ttu-id="2fa1c-134">Pour plus d'informations sur la façon de définir un bit <xref:System.Windows.Forms.ControlStyles>, consultez la méthode <xref:System.Windows.Forms.Control.SetStyle%2A>.)</span><span class="sxs-lookup"><span data-stu-id="2fa1c-134">For more information about how to set a <xref:System.Windows.Forms.ControlStyles> bit, see the <xref:System.Windows.Forms.Control.SetStyle%2A> method.)</span></span>

7. <span data-ttu-id="2fa1c-135">Événement<xref:System.Windows.Forms.Control.MouseDoubleClick> .</span><span class="sxs-lookup"><span data-stu-id="2fa1c-135"><xref:System.Windows.Forms.Control.MouseDoubleClick> event.</span></span>

8. <span data-ttu-id="2fa1c-136">Événement<xref:System.Windows.Forms.Control.MouseUp> .</span><span class="sxs-lookup"><span data-stu-id="2fa1c-136"><xref:System.Windows.Forms.Control.MouseUp> event.</span></span>

<span data-ttu-id="2fa1c-137">Pour obtenir un exemple de code illustrant l’ordre des événements de clic de souris, consultez [Comment : gérer des événements d’entrée d’utilisateur dans les contrôles de Windows Forms](how-to-handle-user-input-events-in-windows-forms-controls.md).</span><span class="sxs-lookup"><span data-stu-id="2fa1c-137">For a code example that demonstrates the order of the mouse click events, see [How to: Handle User Input Events in Windows Forms Controls](how-to-handle-user-input-events-in-windows-forms-controls.md).</span></span>

### <a name="individual-controls"></a><span data-ttu-id="2fa1c-138">Contrôles spécifiques</span><span class="sxs-lookup"><span data-stu-id="2fa1c-138">Individual Controls</span></span>

<span data-ttu-id="2fa1c-139">Les contrôles suivants n'ont pas le comportement d'événement de clic de souris standard :</span><span class="sxs-lookup"><span data-stu-id="2fa1c-139">The following controls do not conform to the standard mouse click event behavior:</span></span>

- <xref:System.Windows.Forms.Button>
- <xref:System.Windows.Forms.CheckBox>
- <xref:System.Windows.Forms.ComboBox>
- <xref:System.Windows.Forms.RadioButton>

  > [!NOTE]
  > <span data-ttu-id="2fa1c-140">Pour le contrôle <xref:System.Windows.Forms.ComboBox>, le comportement d'événement détaillé plus loin se produit si l'utilisateur clique sur le champ d'édition, le bouton ou un élément dans la liste.</span><span class="sxs-lookup"><span data-stu-id="2fa1c-140">For the <xref:System.Windows.Forms.ComboBox> control, the event behavior detailed later occurs if the user clicks on the edit field, the button, or on an item within the list.</span></span>

  - <span data-ttu-id="2fa1c-141">Clic gauche : <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span><span class="sxs-lookup"><span data-stu-id="2fa1c-141">Left click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span></span>

  - <span data-ttu-id="2fa1c-142">Clic droit : aucun événement de clic déclenché</span><span class="sxs-lookup"><span data-stu-id="2fa1c-142">Right click: No click events raised</span></span>

  - <span data-ttu-id="2fa1c-143">Double-clic gauche : <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick> ; <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span><span class="sxs-lookup"><span data-stu-id="2fa1c-143">Left double-click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span></span>

  - <span data-ttu-id="2fa1c-144">Double-clic droit : aucun événement de clic déclenché</span><span class="sxs-lookup"><span data-stu-id="2fa1c-144">Right double-click: No click events raised</span></span>

- <span data-ttu-id="2fa1c-145">Contrôles <xref:System.Windows.Forms.TextBox>, <xref:System.Windows.Forms.RichTextBox>, <xref:System.Windows.Forms.ListBox>, <xref:System.Windows.Forms.MaskedTextBox> et <xref:System.Windows.Forms.CheckedListBox></span><span class="sxs-lookup"><span data-stu-id="2fa1c-145"><xref:System.Windows.Forms.TextBox>, <xref:System.Windows.Forms.RichTextBox>, <xref:System.Windows.Forms.ListBox>, <xref:System.Windows.Forms.MaskedTextBox>, and <xref:System.Windows.Forms.CheckedListBox> controls</span></span>

  > [!NOTE]
  > <span data-ttu-id="2fa1c-146">Le comportement d'événement détaillé plus loin se produit quand l'utilisateur clique dans ces contrôles.</span><span class="sxs-lookup"><span data-stu-id="2fa1c-146">The event behavior detailed later occurs when the user clicks anywhere within these controls.</span></span>

  - <span data-ttu-id="2fa1c-147">Clic gauche : <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span><span class="sxs-lookup"><span data-stu-id="2fa1c-147">Left click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span></span>

  - <span data-ttu-id="2fa1c-148">Clic droit : aucun événement de clic déclenché</span><span class="sxs-lookup"><span data-stu-id="2fa1c-148">Right click: No click events raised</span></span>

  - <span data-ttu-id="2fa1c-149">Double-clic gauche : <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>, <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span><span class="sxs-lookup"><span data-stu-id="2fa1c-149">Left double-click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>, <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span></span>

  - <span data-ttu-id="2fa1c-150">Double-clic droit : aucun événement de clic déclenché</span><span class="sxs-lookup"><span data-stu-id="2fa1c-150">Right double-click: No click events raised</span></span>

- <span data-ttu-id="2fa1c-151">Contrôle <xref:System.Windows.Forms.ListView></span><span class="sxs-lookup"><span data-stu-id="2fa1c-151"><xref:System.Windows.Forms.ListView> control</span></span>

  > [!NOTE]
  > <span data-ttu-id="2fa1c-152">Le comportement d'événement détaillé plus loin se produit quand l'utilisateur clique sur les éléments dans le contrôle <xref:System.Windows.Forms.ListView>.</span><span class="sxs-lookup"><span data-stu-id="2fa1c-152">The event behavior detailed later occurs only when the user clicks on the items in the <xref:System.Windows.Forms.ListView> control.</span></span> <span data-ttu-id="2fa1c-153">Aucun événement n'est déclenché si l'utilisateur clique ailleurs sur le contrôle.</span><span class="sxs-lookup"><span data-stu-id="2fa1c-153">No events are raised for clicks anywhere else on the control.</span></span> <span data-ttu-id="2fa1c-154">Outre les événements décrits plus loin, il existe les événements <xref:System.Windows.Forms.ListView.BeforeLabelEdit> et <xref:System.Windows.Forms.ListView.AfterLabelEdit>, qui peuvent être utiles si vous souhaitez utiliser la validation avec le contrôle <xref:System.Windows.Forms.ListView>.</span><span class="sxs-lookup"><span data-stu-id="2fa1c-154">In addition to the events described later, there are the <xref:System.Windows.Forms.ListView.BeforeLabelEdit> and <xref:System.Windows.Forms.ListView.AfterLabelEdit> events, which may be of interest to you if you want to use validation with the <xref:System.Windows.Forms.ListView> control.</span></span>

  - <span data-ttu-id="2fa1c-155">Clic gauche : <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span><span class="sxs-lookup"><span data-stu-id="2fa1c-155">Left click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span></span>

  - <span data-ttu-id="2fa1c-156">Clic droit : <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span><span class="sxs-lookup"><span data-stu-id="2fa1c-156">Right click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span></span>

  - <span data-ttu-id="2fa1c-157">Double-clic gauche : <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick> ; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span><span class="sxs-lookup"><span data-stu-id="2fa1c-157">Left double-click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span></span>

  - <span data-ttu-id="2fa1c-158">Double-clic droit : <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick> ; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span><span class="sxs-lookup"><span data-stu-id="2fa1c-158">Right double-click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span></span>

- <span data-ttu-id="2fa1c-159">Contrôle <xref:System.Windows.Forms.TreeView></span><span class="sxs-lookup"><span data-stu-id="2fa1c-159"><xref:System.Windows.Forms.TreeView> control</span></span>

  > [!NOTE]
  > <span data-ttu-id="2fa1c-160">Le comportement d'événement détaillé plus loin se produit uniquement quand l'utilisateur clique sur les éléments proprement dits ou à droite des éléments dans le contrôle <xref:System.Windows.Forms.TreeView>.</span><span class="sxs-lookup"><span data-stu-id="2fa1c-160">The event behavior detailed later occurs only when the user clicks on the items themselves or to the right of the items in the <xref:System.Windows.Forms.TreeView> control.</span></span> <span data-ttu-id="2fa1c-161">Aucun événement n'est déclenché si l'utilisateur clique ailleurs sur le contrôle.</span><span class="sxs-lookup"><span data-stu-id="2fa1c-161">No events are raised for clicks anywhere else on the control.</span></span> <span data-ttu-id="2fa1c-162">Outre ceux décrits plus loin, il existe les événements <xref:System.Windows.Forms.TreeView.BeforeCheck>, <xref:System.Windows.Forms.TreeView.BeforeSelect>, <xref:System.Windows.Forms.TreeView.BeforeLabelEdit>, <xref:System.Windows.Forms.TreeView.AfterSelect>, <xref:System.Windows.Forms.TreeView.AfterCheck> et <xref:System.Windows.Forms.TreeView.AfterLabelEdit>, qui peuvent être utiles si vous souhaitez utiliser la validation avec le contrôle <xref:System.Windows.Forms.TreeView>.</span><span class="sxs-lookup"><span data-stu-id="2fa1c-162">In addition to those described later, there are the <xref:System.Windows.Forms.TreeView.BeforeCheck>, <xref:System.Windows.Forms.TreeView.BeforeSelect>, <xref:System.Windows.Forms.TreeView.BeforeLabelEdit>, <xref:System.Windows.Forms.TreeView.AfterSelect>, <xref:System.Windows.Forms.TreeView.AfterCheck>, and <xref:System.Windows.Forms.TreeView.AfterLabelEdit> events, which may be of interest to you if you want to use validation with the <xref:System.Windows.Forms.TreeView> control.</span></span>

  - <span data-ttu-id="2fa1c-163">Clic gauche : <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span><span class="sxs-lookup"><span data-stu-id="2fa1c-163">Left click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span></span>

  - <span data-ttu-id="2fa1c-164">Clic droit : <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span><span class="sxs-lookup"><span data-stu-id="2fa1c-164">Right click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span></span>

  - <span data-ttu-id="2fa1c-165">Double-clic gauche : <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick> ; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span><span class="sxs-lookup"><span data-stu-id="2fa1c-165">Left double-click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span></span>

  - <span data-ttu-id="2fa1c-166">Double-clic droit : <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick> ; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span><span class="sxs-lookup"><span data-stu-id="2fa1c-166">Right double-click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span></span>

### <a name="painting-behavior-of-toggle-controls"></a><span data-ttu-id="2fa1c-167">Comportement de peinture des contrôles Toggle</span><span class="sxs-lookup"><span data-stu-id="2fa1c-167">Painting behavior of toggle controls</span></span>

<span data-ttu-id="2fa1c-168">Les contrôles de basculement, tels que ceux dérivant de la classe <xref:System.Windows.Forms.ButtonBase>, présentent le comportement de peinture distinctif suivant en cas de combinaison avec des événements de clic de souris :</span><span class="sxs-lookup"><span data-stu-id="2fa1c-168">Toggle controls, such as the controls deriving from the <xref:System.Windows.Forms.ButtonBase> class, have the following distinctive painting behavior in combination with mouse click events:</span></span>

1. <span data-ttu-id="2fa1c-169">L'utilisateur appuie sur le bouton de la souris.</span><span class="sxs-lookup"><span data-stu-id="2fa1c-169">The user presses the mouse button.</span></span>

2. <span data-ttu-id="2fa1c-170">Le contrôle est peint à l'état enfoncé.</span><span class="sxs-lookup"><span data-stu-id="2fa1c-170">The control paints in the pressed state.</span></span>

3. <span data-ttu-id="2fa1c-171">L'événement <xref:System.Windows.Forms.Control.MouseDown> est déclenché.</span><span class="sxs-lookup"><span data-stu-id="2fa1c-171">The <xref:System.Windows.Forms.Control.MouseDown> event is raised.</span></span>

4. <span data-ttu-id="2fa1c-172">L’utilisateur relâche le bouton de la souris.</span><span class="sxs-lookup"><span data-stu-id="2fa1c-172">The user releases the mouse button.</span></span>

5. <span data-ttu-id="2fa1c-173">Le contrôle est peint à l'état déclenché.</span><span class="sxs-lookup"><span data-stu-id="2fa1c-173">The control paints in the raised state.</span></span>

6. <span data-ttu-id="2fa1c-174">L'événement <xref:System.Windows.Forms.Control.Click> est déclenché.</span><span class="sxs-lookup"><span data-stu-id="2fa1c-174">The <xref:System.Windows.Forms.Control.Click> event is raised.</span></span>

7. <span data-ttu-id="2fa1c-175">L'événement <xref:System.Windows.Forms.Control.MouseClick> est déclenché.</span><span class="sxs-lookup"><span data-stu-id="2fa1c-175">The <xref:System.Windows.Forms.Control.MouseClick> event is raised.</span></span>

8. <span data-ttu-id="2fa1c-176">L'événement <xref:System.Windows.Forms.Control.MouseUp> est déclenché.</span><span class="sxs-lookup"><span data-stu-id="2fa1c-176">The <xref:System.Windows.Forms.Control.MouseUp> event is raised.</span></span>

    > [!NOTE]
    > <span data-ttu-id="2fa1c-177">Si l'utilisateur déplace le pointeur hors du contrôle de basculement alors que le bouton de la souris est enfoncé (par exemple en cas de déplacement de la souris hors du contrôle <xref:System.Windows.Forms.Button> pendant qu'il est enfoncé), le contrôle de basculement est peint à l'état déclenché et seul l'événement <xref:System.Windows.Forms.Control.MouseUp> se produit.</span><span class="sxs-lookup"><span data-stu-id="2fa1c-177">If the user moves the pointer out of the toggle control while the mouse button is down (such as moving the mouse off the <xref:System.Windows.Forms.Button> control while it is pressed), the toggle control will paint in the raised state and only the <xref:System.Windows.Forms.Control.MouseUp> event occurs.</span></span> <span data-ttu-id="2fa1c-178">L'événement <xref:System.Windows.Forms.Control.Click> ou <xref:System.Windows.Forms.Control.MouseClick> ne se produira pas dans cette situation.</span><span class="sxs-lookup"><span data-stu-id="2fa1c-178">The <xref:System.Windows.Forms.Control.Click> or <xref:System.Windows.Forms.Control.MouseClick> events will not occur in this situation.</span></span>

## <a name="see-also"></a><span data-ttu-id="2fa1c-179">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2fa1c-179">See also</span></span>

- [<span data-ttu-id="2fa1c-180">Entrée de la souris dans une application Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2fa1c-180">Mouse Input in a Windows Forms Application</span></span>](mouse-input-in-a-windows-forms-application.md)
