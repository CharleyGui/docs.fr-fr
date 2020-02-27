---
title: "Procédure pas à pas : mise à disposition d'éléments de menu standard pour un formulaire"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- menu items [Windows Forms], standard
- toolbars [Windows Forms], walkthroughs
- StatusStrip control [Windows Forms]
- ToolStrip control [Windows Forms]
ms.assetid: dac37d98-589e-4d6d-9673-6437e8943122
ms.openlocfilehash: ee80aad445c00bb4b98b49c80495fa512150bcef
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628772"
---
# <a name="walkthrough-providing-standard-menu-items-to-a-form"></a><span data-ttu-id="2672a-102">Procédure pas à pas : mise à disposition d'éléments de menu standard pour un formulaire</span><span class="sxs-lookup"><span data-stu-id="2672a-102">Walkthrough: Providing Standard Menu Items to a Form</span></span>

<span data-ttu-id="2672a-103">Vous pouvez fournir un menu standard pour vos formulaires avec le contrôle <xref:System.Windows.Forms.MenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="2672a-103">You can provide a standard menu for your forms with the <xref:System.Windows.Forms.MenuStrip> control.</span></span>

<span data-ttu-id="2672a-104">Cette procédure pas à pas montre comment utiliser un contrôle <xref:System.Windows.Forms.MenuStrip> pour créer un menu standard.</span><span class="sxs-lookup"><span data-stu-id="2672a-104">This walkthrough demonstrates how to use a <xref:System.Windows.Forms.MenuStrip> control to create a standard menu.</span></span> <span data-ttu-id="2672a-105">Le formulaire répond également lorsqu’un utilisateur sélectionne un élément de menu.</span><span class="sxs-lookup"><span data-stu-id="2672a-105">The form also responds when a user selects a menu item.</span></span> <span data-ttu-id="2672a-106">Les tâches suivantes sont illustrées dans cette procédure pas à pas :</span><span class="sxs-lookup"><span data-stu-id="2672a-106">The following tasks are illustrated in this walkthrough:</span></span>

- <span data-ttu-id="2672a-107">Création d’un projet de Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="2672a-107">Creating a Windows Forms project.</span></span>

- <span data-ttu-id="2672a-108">Création d’un menu standard.</span><span class="sxs-lookup"><span data-stu-id="2672a-108">Creating a standard menu.</span></span>

- <span data-ttu-id="2672a-109">Création d’un contrôle de <xref:System.Windows.Forms.StatusStrip>.</span><span class="sxs-lookup"><span data-stu-id="2672a-109">Creating a <xref:System.Windows.Forms.StatusStrip> control.</span></span>

- <span data-ttu-id="2672a-110">Gestion de la sélection des éléments de menu.</span><span class="sxs-lookup"><span data-stu-id="2672a-110">Handling menu item selection.</span></span>

<span data-ttu-id="2672a-111">Lorsque vous avez terminé, vous disposez d’un formulaire avec un menu standard qui affiche des sélections d’éléments de menu dans un contrôle de <xref:System.Windows.Forms.StatusStrip>.</span><span class="sxs-lookup"><span data-stu-id="2672a-111">When you are finished, you will have a form with a standard menu that displays menu item selections in a <xref:System.Windows.Forms.StatusStrip> control.</span></span>

<span data-ttu-id="2672a-112">Pour copier le code dans cette rubrique sous la forme d’une liste unique, consultez [Comment : fournir des éléments de menu standard à un formulaire](how-to-provide-standard-menu-items-to-a-form.md).</span><span class="sxs-lookup"><span data-stu-id="2672a-112">To copy the code in this topic as a single listing, see [How to: Provide Standard Menu Items to a Form](how-to-provide-standard-menu-items-to-a-form.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="2672a-113">Conditions préalables requises</span><span class="sxs-lookup"><span data-stu-id="2672a-113">Prerequisites</span></span>

<span data-ttu-id="2672a-114">Pour effectuer cette procédure pas à pas, vous avez besoin de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2672a-114">You'll need Visual Studio to complete this walkthrough.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="2672a-115">Créer le projet</span><span class="sxs-lookup"><span data-stu-id="2672a-115">Create the project</span></span>

1. <span data-ttu-id="2672a-116">Dans Visual Studio, créez un projet d’application Windows appelé **StandardMenuForm** (**fichier** > nouveau **projet** >  \*\* > C# visuel\*\* ou **Visual Basic** > **application** > **de** **Bureau classique** ).</span><span class="sxs-lookup"><span data-stu-id="2672a-116">In Visual Studio, create a Windows application project called **StandardMenuForm** (**File** > **New** > **Project** > **Visual C#** or **Visual Basic** > **Classic Desktop** > **Windows Forms Application**).</span></span>

2. <span data-ttu-id="2672a-117">Dans le Concepteur Windows Forms, sélectionnez le formulaire.</span><span class="sxs-lookup"><span data-stu-id="2672a-117">In the Windows Forms Designer, select the form.</span></span>

## <a name="create-a-standard-menu"></a><span data-ttu-id="2672a-118">Créer un menu standard</span><span class="sxs-lookup"><span data-stu-id="2672a-118">Create a standard menu</span></span>

<span data-ttu-id="2672a-119">La Concepteur Windows Forms peut remplir automatiquement un contrôle <xref:System.Windows.Forms.MenuStrip> avec des éléments de menu standard.</span><span class="sxs-lookup"><span data-stu-id="2672a-119">The Windows Forms Designer can automatically populate a <xref:System.Windows.Forms.MenuStrip> control with standard menu items.</span></span>

1. <span data-ttu-id="2672a-120">À partir de la **boîte à outils**, faites glisser un contrôle <xref:System.Windows.Forms.MenuStrip> sur votre formulaire.</span><span class="sxs-lookup"><span data-stu-id="2672a-120">From the **Toolbox**, drag a <xref:System.Windows.Forms.MenuStrip> control onto your form.</span></span>

2. <span data-ttu-id="2672a-121">Cliquez sur le glyphe actions du concepteur du contrôle <xref:System.Windows.Forms.MenuStrip> (![petite flèche noire](./media/designer-actions-glyph.gif)) et sélectionnez **Insérer les éléments standard**.</span><span class="sxs-lookup"><span data-stu-id="2672a-121">Click the <xref:System.Windows.Forms.MenuStrip> control's designer actions glyph (![Small black arrow](./media/designer-actions-glyph.gif)) and select **Insert Standard Items**.</span></span>

     <span data-ttu-id="2672a-122">Le contrôle <xref:System.Windows.Forms.MenuStrip> est rempli avec les éléments de menu standard.</span><span class="sxs-lookup"><span data-stu-id="2672a-122">The <xref:System.Windows.Forms.MenuStrip> control is populated with the standard menu items.</span></span>

3. <span data-ttu-id="2672a-123">Cliquez sur l’élément de menu **fichier** pour afficher ses éléments de menu par défaut et les icônes correspondantes.</span><span class="sxs-lookup"><span data-stu-id="2672a-123">Click the **File** menu item to see its default menu items and corresponding icons.</span></span>

## <a name="create-a-statusstrip-control"></a><span data-ttu-id="2672a-124">Créer un contrôle StatusStrip</span><span class="sxs-lookup"><span data-stu-id="2672a-124">Create a StatusStrip control</span></span>

<span data-ttu-id="2672a-125">Utilisez le contrôle <xref:System.Windows.Forms.StatusStrip> pour afficher l’état de vos applications Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="2672a-125">Use the <xref:System.Windows.Forms.StatusStrip> control to display status for your Windows Forms applications.</span></span> <span data-ttu-id="2672a-126">Dans l’exemple actuel, les éléments de menu sélectionnés par l’utilisateur sont affichés dans un contrôle de <xref:System.Windows.Forms.StatusStrip>.</span><span class="sxs-lookup"><span data-stu-id="2672a-126">In the current example, menu items selected by the user are displayed in a <xref:System.Windows.Forms.StatusStrip> control.</span></span>

1. <span data-ttu-id="2672a-127">À partir de la **boîte à outils**, faites glisser un contrôle <xref:System.Windows.Forms.StatusStrip> sur votre formulaire.</span><span class="sxs-lookup"><span data-stu-id="2672a-127">From the **Toolbox**, drag a <xref:System.Windows.Forms.StatusStrip> control onto your form.</span></span>

     <span data-ttu-id="2672a-128">Le contrôle <xref:System.Windows.Forms.StatusStrip> s’ancre automatiquement au bas du formulaire.</span><span class="sxs-lookup"><span data-stu-id="2672a-128">The <xref:System.Windows.Forms.StatusStrip> control automatically docks to the bottom of the form.</span></span>

2. <span data-ttu-id="2672a-129">Cliquez sur le bouton déroulant du contrôle <xref:System.Windows.Forms.StatusStrip> et sélectionnez **StatusLabel** pour ajouter un contrôle <xref:System.Windows.Forms.ToolStripStatusLabel> au contrôle <xref:System.Windows.Forms.StatusStrip>.</span><span class="sxs-lookup"><span data-stu-id="2672a-129">Click the <xref:System.Windows.Forms.StatusStrip> control's drop-down button and select **StatusLabel** to add a <xref:System.Windows.Forms.ToolStripStatusLabel> control to the <xref:System.Windows.Forms.StatusStrip> control.</span></span>

## <a name="handle-item-selection"></a><span data-ttu-id="2672a-130">Gérer la sélection des éléments</span><span class="sxs-lookup"><span data-stu-id="2672a-130">Handle item selection</span></span>

<span data-ttu-id="2672a-131">Gérez l’événement <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> pour répondre lorsque l’utilisateur sélectionne un élément de menu.</span><span class="sxs-lookup"><span data-stu-id="2672a-131">Handle the <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> event to respond when the user selects a menu item.</span></span>

1. <span data-ttu-id="2672a-132">Cliquez sur l’élément de menu **fichier** que vous avez créé dans la section création d’un menu standard.</span><span class="sxs-lookup"><span data-stu-id="2672a-132">Click the **File** menu item that you created in the Creating a Standard Menu section.</span></span>

2. <span data-ttu-id="2672a-133">Dans la fenêtre **Propriétés**, cliquez sur **Événements**.</span><span class="sxs-lookup"><span data-stu-id="2672a-133">In the **Properties** window, click **Events**.</span></span>

3. <span data-ttu-id="2672a-134">Double-cliquez sur l’événement <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked>.</span><span class="sxs-lookup"><span data-stu-id="2672a-134">Double-click the <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> event.</span></span>

     <span data-ttu-id="2672a-135">Le Concepteur Windows Forms génère un gestionnaire d’événements pour l’événement <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked>.</span><span class="sxs-lookup"><span data-stu-id="2672a-135">The Windows Forms Designer generates an event handler for the <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> event.</span></span>

4. <span data-ttu-id="2672a-136">Insérez le code suivant dans le gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="2672a-136">Insert the following code into the event handler.</span></span>

     [!code-csharp[System.Windows.Forms.ToolStrip.StandardMenu#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.ToolStrip.StandardMenu#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/VB/Form1.vb#3)]

5. <span data-ttu-id="2672a-137">Insérez la définition de la méthode de l’utilitaire `UpdateStatus` dans le formulaire.</span><span class="sxs-lookup"><span data-stu-id="2672a-137">Insert the `UpdateStatus` utility method definition into the form.</span></span>

     [!code-csharp[System.Windows.Forms.ToolStrip.StandardMenu#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.ToolStrip.StandardMenu#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/VB/Form1.vb#2)]

## <a name="checkpoint--test-your-form"></a><span data-ttu-id="2672a-138">Point de contrôle-tester votre formulaire</span><span class="sxs-lookup"><span data-stu-id="2672a-138">Checkpoint -test your form</span></span>

1. <span data-ttu-id="2672a-139">Appuyez sur **F5** pour compiler et exécuter votre formulaire.</span><span class="sxs-lookup"><span data-stu-id="2672a-139">Press **F5** to compile and run your form.</span></span>

2. <span data-ttu-id="2672a-140">Cliquez sur l’élément de menu **fichier** pour ouvrir le menu.</span><span class="sxs-lookup"><span data-stu-id="2672a-140">Click the **File** menu item to open the menu.</span></span>

3. <span data-ttu-id="2672a-141">Dans le menu **fichier** , cliquez sur l’un des éléments pour le sélectionner.</span><span class="sxs-lookup"><span data-stu-id="2672a-141">On the **File** menu, click one of the items to select it.</span></span>

     <span data-ttu-id="2672a-142">Le contrôle <xref:System.Windows.Forms.StatusStrip> affiche l’élément sélectionné.</span><span class="sxs-lookup"><span data-stu-id="2672a-142">The <xref:System.Windows.Forms.StatusStrip> control displays the selected item.</span></span>

## <a name="next-steps"></a><span data-ttu-id="2672a-143">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="2672a-143">Next steps</span></span>

<span data-ttu-id="2672a-144">Dans cette procédure pas à pas, vous avez créé un formulaire avec un menu standard.</span><span class="sxs-lookup"><span data-stu-id="2672a-144">In this walkthrough, you have created a form with a standard menu.</span></span> <span data-ttu-id="2672a-145">Vous pouvez utiliser la famille de contrôles <xref:System.Windows.Forms.ToolStrip> à de nombreuses autres fins :</span><span class="sxs-lookup"><span data-stu-id="2672a-145">You can use the <xref:System.Windows.Forms.ToolStrip> family of controls for many other purposes:</span></span>

- <span data-ttu-id="2672a-146">Créez des menus contextuels pour vos contrôles avec <xref:System.Windows.Forms.ContextMenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="2672a-146">Create shortcut menus for your controls with <xref:System.Windows.Forms.ContextMenuStrip>.</span></span> <span data-ttu-id="2672a-147">Pour plus d’informations, consultez [vue d’ensemble du composant ContextMenu](contextmenu-component-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="2672a-147">For more information, see [ContextMenu Component Overview](contextmenu-component-overview-windows-forms.md).</span></span>

- <span data-ttu-id="2672a-148">Créez un formulaire d’interface multidocument (MDI) avec des contrôles d’ancrage <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="2672a-148">Create a multiple document interface (MDI) form with docking <xref:System.Windows.Forms.ToolStrip> controls.</span></span> <span data-ttu-id="2672a-149">Pour plus d’informations, consultez [procédure pas à pas : création d’un formulaire MDI avec la fusion de menus et les contrôles ToolStrip](walkthrough-creating-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).</span><span class="sxs-lookup"><span data-stu-id="2672a-149">For more information, see [Walkthrough: Creating an MDI Form with Menu Merging and ToolStrip Controls](walkthrough-creating-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).</span></span>

- <span data-ttu-id="2672a-150">Donnez à vos <xref:System.Windows.Forms.ToolStrip> un aspect professionnel.</span><span class="sxs-lookup"><span data-stu-id="2672a-150">Give your <xref:System.Windows.Forms.ToolStrip> controls a professional appearance.</span></span> <span data-ttu-id="2672a-151">Pour plus d’informations, consultez [Comment : définir le convertisseur ToolStrip pour une application](how-to-set-the-toolstrip-renderer-for-an-application.md).</span><span class="sxs-lookup"><span data-stu-id="2672a-151">For more information, see [How to: Set the ToolStrip Renderer for an Application](how-to-set-the-toolstrip-renderer-for-an-application.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2672a-152">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2672a-152">See also</span></span>

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.StatusStrip>
- [<span data-ttu-id="2672a-153">MenuStrip, contrôle</span><span class="sxs-lookup"><span data-stu-id="2672a-153">MenuStrip Control</span></span>](menustrip-control-windows-forms.md)
