---
title: 'Comment : créer des formulaires MDI enfants'
description: Découvrez comment utiliser Visual Studio pour créer un formulaire enfant MDI (multiple-document interface) qui affiche un contrôle RichTextBox.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- MDI [Windows Forms], creating forms
- child forms
ms.assetid: 164b69bb-2eca-4339-ada3-0679eb2c6dda
ms.openlocfilehash: 7fe5cde342f0f5ee078f888b7492cd4618bea5c4
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84903179"
---
# <a name="how-to-create-mdi-child-forms"></a><span data-ttu-id="d3308-103">Comment : créer des formulaires MDI enfants</span><span class="sxs-lookup"><span data-stu-id="d3308-103">How to: Create MDI child forms</span></span>

<span data-ttu-id="d3308-104">Les formulaires enfants MDI sont un élément essentiel des [applications d’interface multidocument (MDI, multiple-document interface)](multiple-document-interface-mdi-applications.md), car ces formulaires représentent le centre de l’interaction de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="d3308-104">MDI child forms are an essential element of [Multiple-Document Interface (MDI) applications](multiple-document-interface-mdi-applications.md), as these forms are the center of user interaction.</span></span>

<span data-ttu-id="d3308-105">Dans la procédure suivante, vous allez utiliser Visual Studio pour créer un formulaire MDI enfant qui affiche un <xref:System.Windows.Forms.RichTextBox> contrôle, semblable à la plupart des applications de traitement de texte.</span><span class="sxs-lookup"><span data-stu-id="d3308-105">In the following procedure, you'll use Visual Studio to create an MDI child form that displays a <xref:System.Windows.Forms.RichTextBox> control, similar to most word-processing applications.</span></span> <span data-ttu-id="d3308-106">En remplaçant le <xref:System.Windows.Forms> contrôle par d’autres contrôles, tels que le <xref:System.Windows.Forms.DataGridView> contrôle ou un mélange de contrôles, vous pouvez créer des fenêtres MDI enfants (et, par extension, des applications MDI) avec diverses possibilités.</span><span class="sxs-lookup"><span data-stu-id="d3308-106">By substituting the <xref:System.Windows.Forms> control with other controls, such as the <xref:System.Windows.Forms.DataGridView> control, or a mixture of controls, you can create MDI child windows (and, by extension, MDI applications) with diverse possibilities.</span></span>

## <a name="create-mdi-child-forms"></a><span data-ttu-id="d3308-107">Créer des formulaires MDI enfants</span><span class="sxs-lookup"><span data-stu-id="d3308-107">Create MDI child forms</span></span>

1. <span data-ttu-id="d3308-108">Créez un nouveau Windows Forms projet d’application dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d3308-108">Create a new Windows Forms application project in Visual Studio.</span></span> <span data-ttu-id="d3308-109">Dans la fenêtre **Propriétés** du formulaire, affectez à sa propriété la valeur <xref:System.Windows.Forms.Form.IsMdiContainer%2A> `true` et à sa propriété la valeur `WindowsState` `Maximized` .</span><span class="sxs-lookup"><span data-stu-id="d3308-109">In the **Properties** window for the form, set its <xref:System.Windows.Forms.Form.IsMdiContainer%2A> property to `true` and its `WindowsState` property to `Maximized`.</span></span>

   <span data-ttu-id="d3308-110">Ainsi, vous désignez le formulaire comme le conteneur MDI des fenêtres enfants.</span><span class="sxs-lookup"><span data-stu-id="d3308-110">This designates the form as an MDI container for child windows.</span></span>

2. <span data-ttu-id="d3308-111">Faites glisser un contrôle <xref:System.Windows.Forms.MenuStrip> de la `Toolbox` vers le formulaire.</span><span class="sxs-lookup"><span data-stu-id="d3308-111">From the `Toolbox`, drag a <xref:System.Windows.Forms.MenuStrip> control to the form.</span></span> <span data-ttu-id="d3308-112">Affectez `Text` à sa propriété la valeur **file**.</span><span class="sxs-lookup"><span data-stu-id="d3308-112">Set its `Text` property to **File**.</span></span>

3. <span data-ttu-id="d3308-113">Cliquez sur les points de suspension (...) en regard de la propriété **Items** , puis cliquez sur **Ajouter** pour ajouter deux éléments de menu de la barre d’outils enfants.</span><span class="sxs-lookup"><span data-stu-id="d3308-113">Click the ellipsis (…) next to the **Items** property, and click **Add** to add two child tool strip menu items.</span></span> <span data-ttu-id="d3308-114">Définissez la `Text` propriété pour ces éléments sur **nouveau** et **fenêtre**.</span><span class="sxs-lookup"><span data-stu-id="d3308-114">Set the `Text` property for these items to **New** and **Window**.</span></span>

4. <span data-ttu-id="d3308-115">Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le projet, puis sélectionnez **Ajouter** > **Nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="d3308-115">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

5. <span data-ttu-id="d3308-116">Dans la boîte de dialogue **Ajouter un nouvel élément** , sélectionnez **Windows Form** (en Visual Basic ou en Visual C#) ou **Windows Forms application (.net)** (dans Visual C++) à partir du volet **modèles** .</span><span class="sxs-lookup"><span data-stu-id="d3308-116">In the **Add New Item** dialog box, select **Windows Form** (in Visual Basic or in Visual C#) or **Windows Forms Application (.NET)** (in Visual C++) from the **Templates** pane.</span></span> <span data-ttu-id="d3308-117">Dans la zone **nom** , nommez le formulaire **Form2**.</span><span class="sxs-lookup"><span data-stu-id="d3308-117">In the **Name** box, name the form **Form2**.</span></span> <span data-ttu-id="d3308-118">Sélectionnez **ouvrir** pour ajouter le formulaire au projet.</span><span class="sxs-lookup"><span data-stu-id="d3308-118">Select **Open** to add the form to the project.</span></span>

    > [!NOTE]
    > <span data-ttu-id="d3308-119">Le formulaire MDI enfant que vous avez créé lors de cette étape est un Windows Form standard.</span><span class="sxs-lookup"><span data-stu-id="d3308-119">The MDI child form you created in this step is a standard Windows Form.</span></span> <span data-ttu-id="d3308-120">Il a donc une propriété <xref:System.Windows.Forms.Form.Opacity%2A>, ce qui vous permet de contrôler la transparence du formulaire.</span><span class="sxs-lookup"><span data-stu-id="d3308-120">As such, it has an <xref:System.Windows.Forms.Form.Opacity%2A> property, which enables you to control the transparency of the form.</span></span> <span data-ttu-id="d3308-121">Cependant, la propriété <xref:System.Windows.Forms.Form.Opacity%2A> a été conçue pour les fenêtres de niveau supérieur.</span><span class="sxs-lookup"><span data-stu-id="d3308-121">However, the <xref:System.Windows.Forms.Form.Opacity%2A> property was designed for top-level windows.</span></span> <span data-ttu-id="d3308-122">Ne l'utilisez pas avec des formulaires MDI enfants, car des problèmes de peinture peuvent survenir.</span><span class="sxs-lookup"><span data-stu-id="d3308-122">Do not use it with MDI child forms, as painting problems can occur.</span></span>

     <span data-ttu-id="d3308-123">Ce formulaire sera le modèle pour vos formulaires MDI enfants.</span><span class="sxs-lookup"><span data-stu-id="d3308-123">This form will be the template for your MDI child forms.</span></span>

     <span data-ttu-id="d3308-124">Le **Concepteur Windows Forms** s’ouvre et affiche **Form2**.</span><span class="sxs-lookup"><span data-stu-id="d3308-124">The **Windows Forms Designer** opens, displaying **Form2**.</span></span>

6. <span data-ttu-id="d3308-125">À partir de la **boîte à outils**, faites glisser un contrôle **RichTextBox** vers le formulaire.</span><span class="sxs-lookup"><span data-stu-id="d3308-125">From the **Toolbox**, drag a **RichTextBox** control to the form.</span></span>

7. <span data-ttu-id="d3308-126">Dans la fenêtre **Propriétés** , affectez `Anchor` à la propriété la valeur **Top, à gauche** et à la propriété la valeur `Dock` **Fill**.</span><span class="sxs-lookup"><span data-stu-id="d3308-126">In the **Properties** window, set the `Anchor` property to **Top, Left** and the `Dock` property to **Fill**.</span></span>

   <span data-ttu-id="d3308-127">Ainsi, le contrôle <xref:System.Windows.Forms.RichTextBox> remplit complètement la zone de formulaire MDI enfant, même quand le formulaire est redimensionné.</span><span class="sxs-lookup"><span data-stu-id="d3308-127">This causes the <xref:System.Windows.Forms.RichTextBox> control to completely fill the area of the MDI child form, even when the form is resized.</span></span>

8. <span data-ttu-id="d3308-128">Double-cliquez sur l’élément de menu **nouveau** pour créer un <xref:System.Windows.Forms.Control.Click> Gestionnaire d’événements pour celui-ci.</span><span class="sxs-lookup"><span data-stu-id="d3308-128">Double click the **New** menu item to create a <xref:System.Windows.Forms.Control.Click> event handler for it.</span></span>

9. <span data-ttu-id="d3308-129">Insérez un code semblable au suivant pour créer un nouveau formulaire MDI enfant lorsque l’utilisateur clique sur l’élément **de menu nouveau** .</span><span class="sxs-lookup"><span data-stu-id="d3308-129">Insert code similar to the following to create a new MDI child form when the user clicks the **New** menu item.</span></span>

   > [!NOTE]
   > <span data-ttu-id="d3308-130">Dans l'exemple suivant, le gestionnaire d'événements gère l'événement <xref:System.Windows.Forms.Control.Click> pour `MenuItem2`.</span><span class="sxs-lookup"><span data-stu-id="d3308-130">In the following example, the event handler handles the <xref:System.Windows.Forms.Control.Click> event for `MenuItem2`.</span></span> <span data-ttu-id="d3308-131">Notez que, selon les spécificités de votre architecture d’application, votre **nouvel** élément de menu peut ne pas être `MenuItem2` .</span><span class="sxs-lookup"><span data-stu-id="d3308-131">Be aware that, depending on the specifics of your application architecture, your **New** menu item may not be `MenuItem2`.</span></span>

    ```vb
    Protected Sub MDIChildNew_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles MenuItem2.Click
       Dim NewMDIChild As New Form2()
       'Set the Parent Form of the Child window.
       NewMDIChild.MdiParent = Me
       'Display the new form.
       NewMDIChild.Show()
    End Sub
    ```

    ```csharp
    protected void MDIChildNew_Click(object sender, System.EventArgs e){
       Form2 newMDIChild = new Form2();
       // Set the Parent Form of the Child window.
       newMDIChild.MdiParent = this;
       // Display the new form.
       newMDIChild.Show();
    }
    ```

    ```cpp
    private:
       void menuItem2_Click(System::Object ^ sender,
          System::EventArgs ^ e)
       {
          Form2^ newMDIChild = gcnew Form2();
          // Set the Parent Form of the Child window.
          newMDIChild->MdiParent = this;
          // Display the new form.
          newMDIChild->Show();
       }
    ```

   <span data-ttu-id="d3308-132">En C++, ajoutez la `#include` directive suivante en haut de Form1. h :</span><span class="sxs-lookup"><span data-stu-id="d3308-132">In C++, add the following `#include` directive at the top of Form1.h:</span></span>

   ```cpp
   #include "Form2.h"
   ```

10. <span data-ttu-id="d3308-133">Dans la liste déroulante en haut de la fenêtre **Propriétés** , sélectionnez la bande de menus qui correspond à la bande de menu **fichier** , puis affectez à la propriété la valeur de la <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> fenêtre <xref:System.Windows.Forms.ToolStripMenuItem> .</span><span class="sxs-lookup"><span data-stu-id="d3308-133">In the drop-down list at the top of the **Properties** window, select the menu strip that corresponds to the **File** menu strip and set the <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> property to the Window <xref:System.Windows.Forms.ToolStripMenuItem>.</span></span>

    <span data-ttu-id="d3308-134">Cela permet au menu **fenêtre** de conserver une liste des fenêtres MDI enfants ouvertes avec une coche en regard de la fenêtre enfant active.</span><span class="sxs-lookup"><span data-stu-id="d3308-134">This enables the **Window** menu to maintain a list of open MDI child windows with a check mark next to the active child window.</span></span>

11. <span data-ttu-id="d3308-135">Appuyez sur **F5** pour exécuter l'application.</span><span class="sxs-lookup"><span data-stu-id="d3308-135">Press **F5** to run the application.</span></span> <span data-ttu-id="d3308-136">En sélectionnant **nouveau** dans le menu **fichier** , vous pouvez créer des formulaires enfants MDI, qui sont suivis de dans l’élément de menu **fenêtre** .</span><span class="sxs-lookup"><span data-stu-id="d3308-136">By selecting **New** from the **File** menu, you can create new MDI child forms, which are kept track of in the **Window** menu item.</span></span>

    > [!NOTE]
    > <span data-ttu-id="d3308-137">Quand un formulaire MDI enfant a un composant <xref:System.Windows.Forms.MainMenu> (avec, généralement, une structure d'éléments de menu) et qu'il est ouvert dans un formulaire MDI parent qui a un composant <xref:System.Windows.Forms.MainMenu> (avec, généralement, une structure d'éléments de menu), les éléments de menu fusionnent automatiquement si vous avez défini la propriété <xref:System.Windows.Forms.MenuItem.MergeType%2A> (et, éventuellement, la propriété <xref:System.Windows.Forms.MenuItem.MergeOrder%2A>).</span><span class="sxs-lookup"><span data-stu-id="d3308-137">When an MDI child form has a <xref:System.Windows.Forms.MainMenu> component (with, usually, a menu structure of menu items) and it is opened within an MDI parent form that has a <xref:System.Windows.Forms.MainMenu> component (with, usually, a menu structure of menu items), the menu items will merge automatically if you have set the <xref:System.Windows.Forms.MenuItem.MergeType%2A> property (and optionally, the <xref:System.Windows.Forms.MenuItem.MergeOrder%2A> property).</span></span> <span data-ttu-id="d3308-138">Affectez la valeur <xref:System.Windows.Forms.MenuMerge.MergeItems> à la propriété <xref:System.Windows.Forms.MenuItem.MergeType%2A> des deux composants <xref:System.Windows.Forms.MainMenu> et à tous les éléments de menu du formulaire enfant.</span><span class="sxs-lookup"><span data-stu-id="d3308-138">Set the <xref:System.Windows.Forms.MenuItem.MergeType%2A> property of both <xref:System.Windows.Forms.MainMenu> components and all of the menu items of the child form to <xref:System.Windows.Forms.MenuMerge.MergeItems>.</span></span> <span data-ttu-id="d3308-139">Définissez aussi la propriété <xref:System.Windows.Forms.MenuItem.MergeOrder%2A> pour que les éléments de menu des deux menus apparaissent dans l'ordre souhaité.</span><span class="sxs-lookup"><span data-stu-id="d3308-139">Additionally, set the <xref:System.Windows.Forms.MenuItem.MergeOrder%2A> property so that the menu items from both menus appear in the desired order.</span></span> <span data-ttu-id="d3308-140">De plus, sachez que quand vous fermez un formulaire MDI parent, chaque formulaire MDI enfant déclenche un événement <xref:System.Windows.Forms.Form.Closing> avant que l'événement <xref:System.Windows.Forms.Form.Closing> pour le parent MDI soit déclenché.</span><span class="sxs-lookup"><span data-stu-id="d3308-140">Moreover, keep in mind that when you close an MDI parent form, each of the MDI child forms raises a <xref:System.Windows.Forms.Form.Closing> event before the <xref:System.Windows.Forms.Form.Closing> event for the MDI parent is raised.</span></span> <span data-ttu-id="d3308-141">L’annulation de l’événement <xref:System.Windows.Forms.Form.Closing> d’un enfant MDI n’empêchera pas le déclenchement de l’événement <xref:System.Windows.Forms.Form.Closing> du MDI parent. Toutefois, l’argument <xref:System.ComponentModel.CancelEventArgs> pour l’événement <xref:System.Windows.Forms.Form.Closing> du MDI parent prendra la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="d3308-141">Canceling an MDI child's <xref:System.Windows.Forms.Form.Closing> event will not prevent the MDI parent's <xref:System.Windows.Forms.Form.Closing> event from being raised; however, the <xref:System.ComponentModel.CancelEventArgs> argument for the MDI parent's <xref:System.Windows.Forms.Form.Closing> event will now be set to `true`.</span></span> <span data-ttu-id="d3308-142">Vous pouvez forcer la fermeture du MDI parent et de tous les formulaires MDI enfants en affectant la valeur `false` à l'argument <xref:System.ComponentModel.CancelEventArgs>.</span><span class="sxs-lookup"><span data-stu-id="d3308-142">You can force the MDI parent and all MDI child forms to close by setting the <xref:System.ComponentModel.CancelEventArgs> argument to `false`.</span></span>

## <a name="see-also"></a><span data-ttu-id="d3308-143">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d3308-143">See also</span></span>

- [<span data-ttu-id="d3308-144">Applications d’interface multidocument (MDI, Multiple Document Interface)</span><span class="sxs-lookup"><span data-stu-id="d3308-144">Multiple-Document Interface (MDI) Applications</span></span>](multiple-document-interface-mdi-applications.md)
- [<span data-ttu-id="d3308-145">Guide pratique pour créer des formulaires MDI parents</span><span class="sxs-lookup"><span data-stu-id="d3308-145">How to: Create MDI Parent Forms</span></span>](how-to-create-mdi-parent-forms.md)
- [<span data-ttu-id="d3308-146">Comment : déterminer l'enfant MDI actif</span><span class="sxs-lookup"><span data-stu-id="d3308-146">How to: Determine the Active MDI Child</span></span>](how-to-determine-the-active-mdi-child.md)
- [<span data-ttu-id="d3308-147">Comment : envoyer des données à l'enfant MDI actif</span><span class="sxs-lookup"><span data-stu-id="d3308-147">How to: Send Data to the Active MDI Child</span></span>](how-to-send-data-to-the-active-mdi-child.md)
- [<span data-ttu-id="d3308-148">Guide pratique pour réorganiser des formulaires MDI enfants</span><span class="sxs-lookup"><span data-stu-id="d3308-148">How to: Arrange MDI Child Forms</span></span>](how-to-arrange-mdi-child-forms.md)
