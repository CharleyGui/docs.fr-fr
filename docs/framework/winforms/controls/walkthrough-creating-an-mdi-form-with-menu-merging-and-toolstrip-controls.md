---
title: "Procédure pas à pas : création d'un formulaire MDI avec la fusion de menus et des contrôles ToolStrip"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toolbars [Windows Forms]
- ToolStripPanel control [Windows Forms]
- MDI [Windows Forms], creating forms
- multiple document interface forms
- MDI forms
- ToolStrip control [Windows Forms]
- MDI forms [Windows Forms], creating
- MDI forms [Windows Forms], walkthroughs
ms.assetid: fbab4221-74af-42d0-bbf4-3c97f7b2e544
ms.openlocfilehash: e0343b98cb71521b35418e70550a93e0bfe20fa8
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628785"
---
# <a name="walkthrough-creating-an-mdi-form-with-menu-merging-and-toolstrip-controls"></a><span data-ttu-id="a00c6-102">Procédure pas à pas : création d'un formulaire MDI avec la fusion de menus et des contrôles ToolStrip</span><span class="sxs-lookup"><span data-stu-id="a00c6-102">Walkthrough: Creating an MDI Form with Menu Merging and ToolStrip Controls</span></span>

<span data-ttu-id="a00c6-103">L'espace de noms <xref:System.Windows.Forms?displayProperty=nameWithType> prend en charge plusieurs applications MDI (Multiple Document Interface) et le contrôle <xref:System.Windows.Forms.MenuStrip> prend en charge la fusion de menus.</span><span class="sxs-lookup"><span data-stu-id="a00c6-103">The <xref:System.Windows.Forms?displayProperty=nameWithType> namespace supports multiple document interface (MDI) applications, and the <xref:System.Windows.Forms.MenuStrip> control supports menu merging.</span></span> <span data-ttu-id="a00c6-104">Les formulaires MDI peuvent également contenir des contrôles <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="a00c6-104">MDI forms can also <xref:System.Windows.Forms.ToolStrip> controls.</span></span>

<span data-ttu-id="a00c6-105">Cette procédure pas à pas montre comment utiliser des contrôles <xref:System.Windows.Forms.ToolStripPanel> avec un formulaire MDI.</span><span class="sxs-lookup"><span data-stu-id="a00c6-105">This walkthrough demonstrates how to use <xref:System.Windows.Forms.ToolStripPanel> controls with an MDI form.</span></span> <span data-ttu-id="a00c6-106">Le formulaire prend également en charge la fusion de menus avec les menus enfants.</span><span class="sxs-lookup"><span data-stu-id="a00c6-106">The form also supports menu merging with child menus.</span></span> <span data-ttu-id="a00c6-107">Les tâches suivantes sont illustrées dans cette procédure pas à pas :</span><span class="sxs-lookup"><span data-stu-id="a00c6-107">The following tasks are illustrated in this walkthrough:</span></span>

- <span data-ttu-id="a00c6-108">Création d’un projet de Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="a00c6-108">Creating a Windows Forms project.</span></span>

- <span data-ttu-id="a00c6-109">Création du menu principal de votre formulaire.</span><span class="sxs-lookup"><span data-stu-id="a00c6-109">Creating the main menu for your form.</span></span> <span data-ttu-id="a00c6-110">Le nom réel du menu varie.</span><span class="sxs-lookup"><span data-stu-id="a00c6-110">The actual name of the menu will vary.</span></span>

- <span data-ttu-id="a00c6-111">Ajout du contrôle <xref:System.Windows.Forms.ToolStripPanel> à la **boîte à outils**.</span><span class="sxs-lookup"><span data-stu-id="a00c6-111">Adding the <xref:System.Windows.Forms.ToolStripPanel> control to the **Toolbox**.</span></span>

- <span data-ttu-id="a00c6-112">Création d’un formulaire enfant.</span><span class="sxs-lookup"><span data-stu-id="a00c6-112">Creating a child form.</span></span>

- <span data-ttu-id="a00c6-113">Réorganisation des contrôles de <xref:System.Windows.Forms.ToolStripPanel> par ordre de plan.</span><span class="sxs-lookup"><span data-stu-id="a00c6-113">Arranging <xref:System.Windows.Forms.ToolStripPanel> controls by z-order.</span></span>

<span data-ttu-id="a00c6-114">Lorsque vous avez terminé, vous disposez d’un formulaire MDI qui prend en charge la fusion de menus et les contrôles <xref:System.Windows.Forms.ToolStrip> mobiles.</span><span class="sxs-lookup"><span data-stu-id="a00c6-114">When you are finished, you will have an MDI form that supports menu merging and movable <xref:System.Windows.Forms.ToolStrip> controls.</span></span>

<span data-ttu-id="a00c6-115">Pour copier le code dans cette rubrique sous la forme d’une liste unique, consultez [Comment : créer un formulaire MDI avec la fusion de menus et les contrôles ToolStrip](how-to-create-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).</span><span class="sxs-lookup"><span data-stu-id="a00c6-115">To copy the code in this topic as a single listing, see [How to: Create an MDI Form with Menu Merging and ToolStrip Controls](how-to-create-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="a00c6-116">Conditions préalables requises</span><span class="sxs-lookup"><span data-stu-id="a00c6-116">Prerequisites</span></span>

<span data-ttu-id="a00c6-117">Pour effectuer cette procédure pas à pas, vous avez besoin de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a00c6-117">You'll need Visual Studio to complete this walkthrough.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="a00c6-118">Créer le projet</span><span class="sxs-lookup"><span data-stu-id="a00c6-118">Create the project</span></span>

1. <span data-ttu-id="a00c6-119">Dans Visual Studio, créez un projet d’application Windows nommé **MDIForm** (**fichier** > nouveau **projet** >  \*\* > C# visuel\*\* ou **Visual Basic** > **application** > **de** **Bureau classique** ).</span><span class="sxs-lookup"><span data-stu-id="a00c6-119">In Visual Studio, create a Windows Application project called **MdiForm** (**File** > **New** > **Project** > **Visual C#** or **Visual Basic** > **Classic Desktop** > **Windows Forms Application**).</span></span>

2. <span data-ttu-id="a00c6-120">Dans le Concepteur Windows Forms, sélectionnez le formulaire.</span><span class="sxs-lookup"><span data-stu-id="a00c6-120">In the Windows Forms Designer, select the form.</span></span>

3. <span data-ttu-id="a00c6-121">Dans le Fenêtre Propriétés, définissez la valeur de la <xref:System.Windows.Forms.Form.IsMdiContainer%2A> sur `true`.</span><span class="sxs-lookup"><span data-stu-id="a00c6-121">In the Properties window, set the value of the <xref:System.Windows.Forms.Form.IsMdiContainer%2A> to `true`.</span></span>

## <a name="create-the-main-menu"></a><span data-ttu-id="a00c6-122">Créer le menu principal</span><span class="sxs-lookup"><span data-stu-id="a00c6-122">Create the main menu</span></span>

<span data-ttu-id="a00c6-123">Le formulaire MDI parent contient le menu principal.</span><span class="sxs-lookup"><span data-stu-id="a00c6-123">The parent MDI form contains the main menu.</span></span> <span data-ttu-id="a00c6-124">Le menu principal contient un élément de menu nommé **fenêtre**.</span><span class="sxs-lookup"><span data-stu-id="a00c6-124">The main menu has one menu item named **Window**.</span></span> <span data-ttu-id="a00c6-125">Avec l’élément de menu **fenêtre** , vous pouvez créer des formulaires enfants.</span><span class="sxs-lookup"><span data-stu-id="a00c6-125">With the **Window** menu item, you can create child forms.</span></span> <span data-ttu-id="a00c6-126">Les éléments de menu des formulaires enfants sont fusionnés dans le menu principal.</span><span class="sxs-lookup"><span data-stu-id="a00c6-126">Menu items from child forms are merged into the main menu.</span></span>

1. <span data-ttu-id="a00c6-127">À partir de la **boîte à outils**, faites glisser un contrôle <xref:System.Windows.Forms.MenuStrip> sur le formulaire.</span><span class="sxs-lookup"><span data-stu-id="a00c6-127">From the **Toolbox**, drag a <xref:System.Windows.Forms.MenuStrip> control onto the form.</span></span>

2. <span data-ttu-id="a00c6-128">Ajoutez une <xref:System.Windows.Forms.ToolStripMenuItem> au contrôle <xref:System.Windows.Forms.MenuStrip> et nommez-la **fenêtre**.</span><span class="sxs-lookup"><span data-stu-id="a00c6-128">Add a <xref:System.Windows.Forms.ToolStripMenuItem> to the <xref:System.Windows.Forms.MenuStrip> control and name it **Window**.</span></span>

3. <span data-ttu-id="a00c6-129">Sélectionnez le contrôle <xref:System.Windows.Forms.MenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="a00c6-129">Select the <xref:System.Windows.Forms.MenuStrip> control.</span></span>

4. <span data-ttu-id="a00c6-130">Dans le Fenêtre Propriétés, définissez la valeur de la propriété <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> sur `ToolStripMenuItem1`.</span><span class="sxs-lookup"><span data-stu-id="a00c6-130">In the Properties window, set the value of the <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> property to `ToolStripMenuItem1`.</span></span>

5. <span data-ttu-id="a00c6-131">Ajoutez un sous-élément à l’élément de menu **fenêtre** , puis nommez le sous-élément **nouveau**.</span><span class="sxs-lookup"><span data-stu-id="a00c6-131">Add a subitem to the **Window** menu item, and then name the subitem **New**.</span></span>

6. <span data-ttu-id="a00c6-132">Dans le Fenêtre Propriétés, cliquez sur **événements**.</span><span class="sxs-lookup"><span data-stu-id="a00c6-132">In the Properties window, click **Events**.</span></span>

7. <span data-ttu-id="a00c6-133">Double-cliquez sur l’événement <xref:System.Windows.Forms.ToolStripItem.Click>.</span><span class="sxs-lookup"><span data-stu-id="a00c6-133">Double-click the <xref:System.Windows.Forms.ToolStripItem.Click> event.</span></span>

     <span data-ttu-id="a00c6-134">Le Concepteur Windows Forms génère un gestionnaire d’événements pour l’événement <xref:System.Windows.Forms.ToolStripItem.Click>.</span><span class="sxs-lookup"><span data-stu-id="a00c6-134">The Windows Forms Designer generates an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event.</span></span>

8. <span data-ttu-id="a00c6-135">Insérez le code suivant dans le gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="a00c6-135">Insert the following code into the event handler.</span></span>

     [!code-csharp[System.Windows.Forms.ToolStrip.MdiForm#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.MdiForm/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.ToolStrip.MdiForm#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.MdiForm/VB/Form1.vb#2)]

## <a name="add-the-toolstrippanel-control-to-the-toolbox"></a><span data-ttu-id="a00c6-136">Ajouter le contrôle ToolStripPanel à la boîte à outils</span><span class="sxs-lookup"><span data-stu-id="a00c6-136">Add the ToolStripPanel control to the Toolbox</span></span>

<span data-ttu-id="a00c6-137">Lorsque vous utilisez des contrôles <xref:System.Windows.Forms.MenuStrip> avec un formulaire MDI, vous devez disposer du contrôle <xref:System.Windows.Forms.ToolStripPanel>.</span><span class="sxs-lookup"><span data-stu-id="a00c6-137">When you use <xref:System.Windows.Forms.MenuStrip> controls with an MDI form you must have the <xref:System.Windows.Forms.ToolStripPanel> control.</span></span> <span data-ttu-id="a00c6-138">Vous devez ajouter le contrôle <xref:System.Windows.Forms.ToolStripPanel> à la **boîte à outils** pour générer votre formulaire MDI dans le Concepteur Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="a00c6-138">You must add the <xref:System.Windows.Forms.ToolStripPanel> control to the **Toolbox** to build your MDI form in the Windows Forms Designer.</span></span>

1. <span data-ttu-id="a00c6-139">Ouvrez la **boîte à outils**, puis cliquez sur l’onglet **tous les Windows Forms** pour afficher les contrôles Windows Forms disponibles.</span><span class="sxs-lookup"><span data-stu-id="a00c6-139">Open the **Toolbox**, and then click the **All Windows Forms** tab to show the available Windows Forms controls.</span></span>

2. <span data-ttu-id="a00c6-140">Cliquez avec le bouton droit pour ouvrir le menu contextuel, puis sélectionnez **choisir les éléments**.</span><span class="sxs-lookup"><span data-stu-id="a00c6-140">Right-click to open the shortcut menu, and select **Choose Items**.</span></span>

3. <span data-ttu-id="a00c6-141">Dans la boîte de dialogue **choisir des éléments de boîte à outils** , faites défiler la colonne **nom** jusqu’à ce que vous trouviez **ToolStripPanel**.</span><span class="sxs-lookup"><span data-stu-id="a00c6-141">In the **Choose Toolbox Items** dialog box, scroll down the **Name** column until you find **ToolStripPanel**.</span></span>

4. <span data-ttu-id="a00c6-142">Activez la case à cocher par **ToolStripPanel**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="a00c6-142">Select the check box by **ToolStripPanel**, and then click **OK**.</span></span>

     <span data-ttu-id="a00c6-143">Le contrôle <xref:System.Windows.Forms.ToolStripPanel> s’affiche dans la **boîte à outils**.</span><span class="sxs-lookup"><span data-stu-id="a00c6-143">The <xref:System.Windows.Forms.ToolStripPanel> control appears in the **Toolbox**.</span></span>

## <a name="create-a-child-form"></a><span data-ttu-id="a00c6-144">Créer un formulaire enfant</span><span class="sxs-lookup"><span data-stu-id="a00c6-144">Create a child form</span></span>

<span data-ttu-id="a00c6-145">Dans cette procédure, vous allez définir une classe de formulaire enfant distincte qui possède son propre contrôle <xref:System.Windows.Forms.MenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="a00c6-145">In this procedure, you will define a separate child form class that has its own <xref:System.Windows.Forms.MenuStrip> control.</span></span> <span data-ttu-id="a00c6-146">Les éléments de menu de ce formulaire sont fusionnés avec ceux du formulaire parent.</span><span class="sxs-lookup"><span data-stu-id="a00c6-146">The menu items for this form are merged with those of the parent form.</span></span>

1. <span data-ttu-id="a00c6-147">Ajoutez un nouveau formulaire nommé `ChildForm` au projet.</span><span class="sxs-lookup"><span data-stu-id="a00c6-147">Add a new form named `ChildForm` to the project.</span></span>

     <span data-ttu-id="a00c6-148">Pour plus d’informations, consultez [Comment : ajouter des Windows Forms à un projet](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/y2xxdce3(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="a00c6-148">For more information, see [How to: Add Windows Forms to a Project](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/y2xxdce3(v=vs.100)).</span></span>

2. <span data-ttu-id="a00c6-149">À partir de la **boîte à outils**, faites glisser un contrôle <xref:System.Windows.Forms.MenuStrip> sur le formulaire enfant.</span><span class="sxs-lookup"><span data-stu-id="a00c6-149">From the **Toolbox**, drag a <xref:System.Windows.Forms.MenuStrip> control onto the child form.</span></span>

3. <span data-ttu-id="a00c6-150">Cliquez sur le glyphe actions du concepteur du contrôle <xref:System.Windows.Forms.MenuStrip> (![petite flèche noire](./media/designer-actions-glyph.gif)), puis sélectionnez **modifier les éléments**.</span><span class="sxs-lookup"><span data-stu-id="a00c6-150">Click the <xref:System.Windows.Forms.MenuStrip> control's designer actions glyph (![Small black arrow](./media/designer-actions-glyph.gif)), and then select **Edit Items**.</span></span>

4. <span data-ttu-id="a00c6-151">Dans la boîte de dialogue **éditeur de collections Items** , ajoutez une nouvelle <xref:System.Windows.Forms.ToolStripMenuItem> nommée **ChildMenuItem** au menu enfant.</span><span class="sxs-lookup"><span data-stu-id="a00c6-151">In the **Items Collection Editor** dialog box, add a new <xref:System.Windows.Forms.ToolStripMenuItem> named **ChildMenuItem** to the child menu.</span></span>

     <span data-ttu-id="a00c6-152">Pour plus d’informations, consultez [éditeur de collections d’éléments ToolStrip](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233643(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="a00c6-152">For more information, see [ToolStrip Items Collection Editor](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233643(v=vs.100)).</span></span>

## <a name="test-the-form"></a><span data-ttu-id="a00c6-153">Tester le formulaire</span><span class="sxs-lookup"><span data-stu-id="a00c6-153">Test the form</span></span>

1. <span data-ttu-id="a00c6-154">Appuyez sur **F5** pour compiler et exécuter votre formulaire.</span><span class="sxs-lookup"><span data-stu-id="a00c6-154">Press **F5** to compile and run your form.</span></span>

2. <span data-ttu-id="a00c6-155">Cliquez sur l’élément de menu **fenêtre** pour ouvrir le menu, puis cliquez sur **nouveau**.</span><span class="sxs-lookup"><span data-stu-id="a00c6-155">Click the **Window** menu item to open the menu, and then click **New**.</span></span>

     <span data-ttu-id="a00c6-156">Un nouveau formulaire enfant est créé dans la zone cliente MDI du formulaire.</span><span class="sxs-lookup"><span data-stu-id="a00c6-156">A new child form is created in the form's MDI client area.</span></span> <span data-ttu-id="a00c6-157">Le menu du formulaire enfant est fusionné avec le menu principal.</span><span class="sxs-lookup"><span data-stu-id="a00c6-157">The child form's menu is merged with the main menu.</span></span>

3. <span data-ttu-id="a00c6-158">Fermez le formulaire enfant.</span><span class="sxs-lookup"><span data-stu-id="a00c6-158">Close the child form.</span></span>

     <span data-ttu-id="a00c6-159">Le menu du formulaire enfant est supprimé du menu principal.</span><span class="sxs-lookup"><span data-stu-id="a00c6-159">The child form's menu is removed from the main menu.</span></span>

4. <span data-ttu-id="a00c6-160">Cliquez sur **nouveau** plusieurs fois.</span><span class="sxs-lookup"><span data-stu-id="a00c6-160">Click **New** several times.</span></span>

     <span data-ttu-id="a00c6-161">Les formulaires enfants sont automatiquement répertoriés sous l’élément de menu **fenêtre** , car la propriété <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> du contrôle <xref:System.Windows.Forms.MenuStrip> est assignée.</span><span class="sxs-lookup"><span data-stu-id="a00c6-161">The child forms are automatically listed under the **Window** menu item because the <xref:System.Windows.Forms.MenuStrip> control's <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> property is assigned.</span></span>

## <a name="add-toolstrip-support"></a><span data-ttu-id="a00c6-162">Ajouter la prise en charge ToolStrip</span><span class="sxs-lookup"><span data-stu-id="a00c6-162">Add ToolStrip support</span></span>

<span data-ttu-id="a00c6-163">Dans cette procédure, vous allez ajouter quatre <xref:System.Windows.Forms.ToolStrip> contrôles au formulaire parent MDI.</span><span class="sxs-lookup"><span data-stu-id="a00c6-163">In this procedure, you will add four <xref:System.Windows.Forms.ToolStrip> controls to the MDI parent form.</span></span> <span data-ttu-id="a00c6-164">Chaque contrôle <xref:System.Windows.Forms.ToolStrip> est ajouté à l’intérieur d’un contrôle <xref:System.Windows.Forms.ToolStripPanel>, qui est ancré au bord du formulaire.</span><span class="sxs-lookup"><span data-stu-id="a00c6-164">Each <xref:System.Windows.Forms.ToolStrip> control is added inside a <xref:System.Windows.Forms.ToolStripPanel> control, which is docked to the edge of the form.</span></span>

1. <span data-ttu-id="a00c6-165">À partir de la **boîte à outils**, faites glisser un contrôle <xref:System.Windows.Forms.ToolStripPanel> sur le formulaire.</span><span class="sxs-lookup"><span data-stu-id="a00c6-165">From the **Toolbox**, drag a <xref:System.Windows.Forms.ToolStripPanel> control onto the form.</span></span>

2. <span data-ttu-id="a00c6-166">Après avoir sélectionné le contrôle <xref:System.Windows.Forms.ToolStripPanel>, double-cliquez sur le contrôle <xref:System.Windows.Forms.ToolStrip> dans la **boîte à outils**.</span><span class="sxs-lookup"><span data-stu-id="a00c6-166">With the <xref:System.Windows.Forms.ToolStripPanel> control selected, double-click the <xref:System.Windows.Forms.ToolStrip> control in the **Toolbox**.</span></span>

     <span data-ttu-id="a00c6-167">Un contrôle <xref:System.Windows.Forms.ToolStrip> est créé dans le contrôle <xref:System.Windows.Forms.ToolStripPanel>.</span><span class="sxs-lookup"><span data-stu-id="a00c6-167">A <xref:System.Windows.Forms.ToolStrip> control is created in the <xref:System.Windows.Forms.ToolStripPanel> control.</span></span>

3. <span data-ttu-id="a00c6-168">Sélectionnez le contrôle <xref:System.Windows.Forms.ToolStripPanel>.</span><span class="sxs-lookup"><span data-stu-id="a00c6-168">Select the <xref:System.Windows.Forms.ToolStripPanel> control.</span></span>

4. <span data-ttu-id="a00c6-169">Dans le Fenêtre Propriétés, remplacez la valeur de la propriété <xref:System.Windows.Forms.Control.Dock%2A> du contrôle par <xref:System.Windows.Forms.DockStyle.Left>.</span><span class="sxs-lookup"><span data-stu-id="a00c6-169">In the Properties window, change the value of the control's <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Left>.</span></span>

     <span data-ttu-id="a00c6-170">Le contrôle <xref:System.Windows.Forms.ToolStripPanel> s’ancre sur le côté gauche du formulaire, sous le menu principal.</span><span class="sxs-lookup"><span data-stu-id="a00c6-170">The <xref:System.Windows.Forms.ToolStripPanel> control docks to the left side of the form, underneath the main menu.</span></span> <span data-ttu-id="a00c6-171">La zone cliente MDI se redimensionne en fonction du contrôle <xref:System.Windows.Forms.ToolStripPanel>.</span><span class="sxs-lookup"><span data-stu-id="a00c6-171">The MDI client area resizes to fit the <xref:System.Windows.Forms.ToolStripPanel> control.</span></span>

5. <span data-ttu-id="a00c6-172">Répétez les étapes 1 à 4.</span><span class="sxs-lookup"><span data-stu-id="a00c6-172">Repeat steps 1 through 4.</span></span>

     <span data-ttu-id="a00c6-173">Ancrez le nouveau contrôle <xref:System.Windows.Forms.ToolStripPanel> en haut du formulaire.</span><span class="sxs-lookup"><span data-stu-id="a00c6-173">Dock the new <xref:System.Windows.Forms.ToolStripPanel> control to the top of the form.</span></span>

     <span data-ttu-id="a00c6-174">Le contrôle <xref:System.Windows.Forms.ToolStripPanel> est ancré sous le menu principal, mais à droite du premier contrôle <xref:System.Windows.Forms.ToolStripPanel>.</span><span class="sxs-lookup"><span data-stu-id="a00c6-174">The <xref:System.Windows.Forms.ToolStripPanel> control is docked underneath the main menu, but to the right of the first <xref:System.Windows.Forms.ToolStripPanel> control.</span></span> <span data-ttu-id="a00c6-175">Cette étape illustre l’importance de l’ordre de plan pour positionner correctement les contrôles <xref:System.Windows.Forms.ToolStripPanel>.</span><span class="sxs-lookup"><span data-stu-id="a00c6-175">This step illustrates the importance of z-order in correctly positioning <xref:System.Windows.Forms.ToolStripPanel> controls.</span></span>

6. <span data-ttu-id="a00c6-176">Répétez les étapes 1 à 4 pour deux autres contrôles de <xref:System.Windows.Forms.ToolStripPanel>.</span><span class="sxs-lookup"><span data-stu-id="a00c6-176">Repeat steps 1 through 4 for two more <xref:System.Windows.Forms.ToolStripPanel> controls.</span></span>

     <span data-ttu-id="a00c6-177">Ancrez les nouveaux contrôles de <xref:System.Windows.Forms.ToolStripPanel> à droite et en bas du formulaire.</span><span class="sxs-lookup"><span data-stu-id="a00c6-177">Dock the new <xref:System.Windows.Forms.ToolStripPanel> controls to the right and bottom of the form.</span></span>

## <a name="arrange-toolstrippanel-controls-by-z-order"></a><span data-ttu-id="a00c6-178">Organiser les contrôles ToolStripPanel selon l’ordre de plan</span><span class="sxs-lookup"><span data-stu-id="a00c6-178">Arrange ToolStripPanel controls by Z-order</span></span>

<span data-ttu-id="a00c6-179">La position d’un contrôle <xref:System.Windows.Forms.ToolStripPanel> ancré sur votre formulaire MDI est déterminée par la position du contrôle dans l’ordre de plan.</span><span class="sxs-lookup"><span data-stu-id="a00c6-179">The position of a docked <xref:System.Windows.Forms.ToolStripPanel> control on your MDI form is determined by the control's position in the z-order.</span></span> <span data-ttu-id="a00c6-180">Vous pouvez facilement organiser l’ordre de plan de vos contrôles dans la fenêtre structure du document.</span><span class="sxs-lookup"><span data-stu-id="a00c6-180">You can easily arrange the z-order of your controls in the Document Outline window.</span></span>

1. <span data-ttu-id="a00c6-181">Dans le menu **affichage** , cliquez sur **autres fenêtres**, puis sur **structure du document**.</span><span class="sxs-lookup"><span data-stu-id="a00c6-181">In the **View** menu, click **Other Windows**, and then click **Document Outline**.</span></span>

     <span data-ttu-id="a00c6-182">La disposition de vos contrôles <xref:System.Windows.Forms.ToolStripPanel> de la procédure précédente est non standard.</span><span class="sxs-lookup"><span data-stu-id="a00c6-182">The arrangement of your <xref:System.Windows.Forms.ToolStripPanel> controls from the previous procedure is nonstandard.</span></span> <span data-ttu-id="a00c6-183">Cela est dû au fait que l’ordre de plan n’est pas correct.</span><span class="sxs-lookup"><span data-stu-id="a00c6-183">This is because the z-order is not correct.</span></span> <span data-ttu-id="a00c6-184">Utilisez la fenêtre structure du document pour modifier l’ordre de plan des contrôles.</span><span class="sxs-lookup"><span data-stu-id="a00c6-184">Use the Document Outline window to change the z-order of the controls.</span></span>

2. <span data-ttu-id="a00c6-185">Dans la fenêtre structure du document, sélectionnez **ToolStripPanel4**.</span><span class="sxs-lookup"><span data-stu-id="a00c6-185">In the Document Outline window, select **ToolStripPanel4**.</span></span>

3. <span data-ttu-id="a00c6-186">Cliquez sur le bouton fléché vers le bas à plusieurs reprises, jusqu’à ce que **ToolStripPanel4** se trouve en bas de la liste.</span><span class="sxs-lookup"><span data-stu-id="a00c6-186">Click the down-arrow button repeatedly, until **ToolStripPanel4** is at the bottom of the list.</span></span>

     <span data-ttu-id="a00c6-187">Le contrôle **ToolStripPanel4** est ancré au bas du formulaire, sous les autres contrôles.</span><span class="sxs-lookup"><span data-stu-id="a00c6-187">The **ToolStripPanel4** control is docked to the bottom of the form, underneath the other controls.</span></span>

4. <span data-ttu-id="a00c6-188">Sélectionnez **ToolStripPanel2**.</span><span class="sxs-lookup"><span data-stu-id="a00c6-188">Select **ToolStripPanel2**.</span></span>

5. <span data-ttu-id="a00c6-189">Cliquez sur le bouton fléché vers le bas une fois pour positionner le troisième contrôle dans la liste.</span><span class="sxs-lookup"><span data-stu-id="a00c6-189">Click the down-arrow button one time to position the control third in the list.</span></span>

     <span data-ttu-id="a00c6-190">Le contrôle **ToolStripPanel2** est ancré en haut du formulaire, sous le menu principal et au-dessus des autres contrôles.</span><span class="sxs-lookup"><span data-stu-id="a00c6-190">The **ToolStripPanel2** control is docked to the top of the form, underneath the main menu and above the other controls.</span></span>

6. <span data-ttu-id="a00c6-191">Sélectionnez différents contrôles dans la fenêtre **structure du document** et déplacez-les vers différentes positions dans l’ordre de plan.</span><span class="sxs-lookup"><span data-stu-id="a00c6-191">Select various controls in the **Document Outline** window and move them to different positions in the z-order.</span></span> <span data-ttu-id="a00c6-192">Notez l’effet de l’ordre de plan sur l’emplacement des contrôles ancrés.</span><span class="sxs-lookup"><span data-stu-id="a00c6-192">Note the effect of the z-order on the placement of docked controls.</span></span> <span data-ttu-id="a00c6-193">Utilisez CTRL + Z ou **Annuler** dans le menu **Edition** pour annuler vos modifications.</span><span class="sxs-lookup"><span data-stu-id="a00c6-193">Use CTRL-Z or **Undo** on the **Edit** menu to undo your changes.</span></span>

## <a name="checkpoint---test-your-form"></a><span data-ttu-id="a00c6-194">Point de contrôle-tester votre formulaire</span><span class="sxs-lookup"><span data-stu-id="a00c6-194">Checkpoint - test your form</span></span>

1. <span data-ttu-id="a00c6-195">Appuyez sur **F5** pour compiler et exécuter votre formulaire.</span><span class="sxs-lookup"><span data-stu-id="a00c6-195">Press **F5** to compile and run your form.</span></span>

2. <span data-ttu-id="a00c6-196">Cliquez sur la poignée d’un contrôle <xref:System.Windows.Forms.ToolStrip> et faites glisser le contrôle vers différentes positions sur le formulaire.</span><span class="sxs-lookup"><span data-stu-id="a00c6-196">Click the grip of a <xref:System.Windows.Forms.ToolStrip> control and drag the control to different positions on the form.</span></span>

     <span data-ttu-id="a00c6-197">Vous pouvez faire glisser un contrôle <xref:System.Windows.Forms.ToolStrip> d’un contrôle <xref:System.Windows.Forms.ToolStripPanel> vers un autre.</span><span class="sxs-lookup"><span data-stu-id="a00c6-197">You can drag a <xref:System.Windows.Forms.ToolStrip> control from one <xref:System.Windows.Forms.ToolStripPanel> control to another.</span></span>

## <a name="next-steps"></a><span data-ttu-id="a00c6-198">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="a00c6-198">Next steps</span></span>

<span data-ttu-id="a00c6-199">Dans cette procédure pas à pas, vous avez créé un formulaire MDI parent avec des contrôles de <xref:System.Windows.Forms.ToolStrip> et la fusion de menus.</span><span class="sxs-lookup"><span data-stu-id="a00c6-199">In this walkthrough, you have created an MDI parent form with <xref:System.Windows.Forms.ToolStrip> controls and menu merging.</span></span> <span data-ttu-id="a00c6-200">Vous pouvez utiliser la famille de contrôles <xref:System.Windows.Forms.ToolStrip> à de nombreuses autres fins :</span><span class="sxs-lookup"><span data-stu-id="a00c6-200">You can use the <xref:System.Windows.Forms.ToolStrip> family of controls for many other purposes:</span></span>

- <span data-ttu-id="a00c6-201">Créez des menus contextuels pour vos contrôles avec <xref:System.Windows.Forms.ContextMenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="a00c6-201">Create shortcut menus for your controls with <xref:System.Windows.Forms.ContextMenuStrip>.</span></span> <span data-ttu-id="a00c6-202">Pour plus d’informations, consultez [vue d’ensemble du composant ContextMenu](contextmenu-component-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="a00c6-202">For more information, see [ContextMenu Component Overview](contextmenu-component-overview-windows-forms.md).</span></span>

- <span data-ttu-id="a00c6-203">Créé un formulaire avec un menu standard rempli automatiquement.</span><span class="sxs-lookup"><span data-stu-id="a00c6-203">Created a form with an automatically populated standard menu.</span></span> <span data-ttu-id="a00c6-204">Pour plus d’informations, consultez [procédure pas à pas : ajout d’éléments de menu standard à un formulaire](walkthrough-providing-standard-menu-items-to-a-form.md).</span><span class="sxs-lookup"><span data-stu-id="a00c6-204">For more information, see [Walkthrough: Providing Standard Menu Items to a Form](walkthrough-providing-standard-menu-items-to-a-form.md).</span></span>

- <span data-ttu-id="a00c6-205">Donnez à vos <xref:System.Windows.Forms.ToolStrip> un aspect professionnel.</span><span class="sxs-lookup"><span data-stu-id="a00c6-205">Give your <xref:System.Windows.Forms.ToolStrip> controls a professional appearance.</span></span> <span data-ttu-id="a00c6-206">Pour plus d’informations, consultez [Comment : définir le convertisseur ToolStrip pour une application](how-to-set-the-toolstrip-renderer-for-an-application.md).</span><span class="sxs-lookup"><span data-stu-id="a00c6-206">For more information, see [How to: Set the ToolStrip Renderer for an Application](how-to-set-the-toolstrip-renderer-for-an-application.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a00c6-207">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a00c6-207">See also</span></span>

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.StatusStrip>
- [<span data-ttu-id="a00c6-208">Guide pratique pour créer des formulaires MDI parents</span><span class="sxs-lookup"><span data-stu-id="a00c6-208">How to: Create MDI Parent Forms</span></span>](../advanced/how-to-create-mdi-parent-forms.md)
- [<span data-ttu-id="a00c6-209">Guide pratique pour créer des formulaires MDI enfants</span><span class="sxs-lookup"><span data-stu-id="a00c6-209">How to: Create MDI Child Forms</span></span>](../advanced/how-to-create-mdi-child-forms.md)
- [<span data-ttu-id="a00c6-210">Guide pratique pour insérer un MenuStrip dans un menu déroulant MDI</span><span class="sxs-lookup"><span data-stu-id="a00c6-210">How to: Insert a MenuStrip into an MDI Drop-Down Menu</span></span>](how-to-insert-a-menustrip-into-an-mdi-drop-down-menu-windows-forms.md)
- [<span data-ttu-id="a00c6-211">Contrôle ToolStrip</span><span class="sxs-lookup"><span data-stu-id="a00c6-211">ToolStrip Control</span></span>](toolstrip-control-windows-forms.md)
