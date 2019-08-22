---
title: 'Procédure pas à pas : organiser le contenu WPF dans Windows Forms au moment du design'
ms.date: 03/30/2017
helpviewer_keywords:
- WPF user control [Windows Forms], hosting in a layout panel
- WPF content [Windows Forms], arranging at design time
- Windows Forms, arranging WPF content at design time
- WPF content [Windows Forms], hosting in Windows Forms
- Windows Forms, anchoring and docking WPF content
- interoperability [WPF]
ms.assetid: 5efb1c53-1484-43d6-aa8a-f4861b99bb8a
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 7858ffd708c78d6397d533f613ccc2ea78d6cbed
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69658527"
---
# <a name="walkthrough-arrange-wpf-content-on-windows-forms-at-design-time"></a><span data-ttu-id="2a02d-102">Procédure pas à pas : Organiser le contenu WPF sur Windows Forms au moment du design</span><span class="sxs-lookup"><span data-stu-id="2a02d-102">Walkthrough: Arrange WPF content on Windows Forms at design time</span></span>

<span data-ttu-id="2a02d-103">Cet article explique comment utiliser les fonctionnalités de disposition Windows Forms, telles que l’ancrage et les lignes d’alignement, pour réorganiser les contrôles Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="2a02d-103">This article shows you how to use the Windows Forms layout features, such as anchoring and snaplines, to arrange Windows Presentation Foundation (WPF) controls.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="2a02d-104">Prérequis</span><span class="sxs-lookup"><span data-stu-id="2a02d-104">Prerequisites</span></span>

<span data-ttu-id="2a02d-105">Cette procédure pas à pas nécessite Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2a02d-105">You need Visual Studio to complete this walkthrough.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="2a02d-106">Créer le projet</span><span class="sxs-lookup"><span data-stu-id="2a02d-106">Create the project</span></span>

<span data-ttu-id="2a02d-107">Ouvrez Visual Studio et créez un projet d’application Windows Forms dans Visual Basic ou un C# visuel `ArrangeElementHost`nommé.</span><span class="sxs-lookup"><span data-stu-id="2a02d-107">Open Visual Studio and create a new Windows Forms Application project in Visual Basic or Visual C# named `ArrangeElementHost`.</span></span>

> [!NOTE]
> <span data-ttu-id="2a02d-108">Lors de l'hébergement de contenu WPF, seuls les projets Visual Basic et C# sont pris en charge.</span><span class="sxs-lookup"><span data-stu-id="2a02d-108">When hosting WPF content, only C# and Visual Basic projects are supported.</span></span>

## <a name="create-the-wpf-control"></a><span data-ttu-id="2a02d-109">Créer le contrôle WPF</span><span class="sxs-lookup"><span data-stu-id="2a02d-109">Create the WPF control</span></span>

<span data-ttu-id="2a02d-110">Après avoir ajouté un contrôle WPF au projet, vous pouvez le disposer sur le formulaire.</span><span class="sxs-lookup"><span data-stu-id="2a02d-110">After you add a WPF control to the project, you can arrange it on the form.</span></span>

1. <span data-ttu-id="2a02d-111">Ajoutez un nouveau <xref:System.Windows.Controls.UserControl> WPF au projet.</span><span class="sxs-lookup"><span data-stu-id="2a02d-111">Add a new WPF <xref:System.Windows.Controls.UserControl> to the project.</span></span> <span data-ttu-id="2a02d-112">Utilisez le nom par défaut pour le type de contrôle, `UserControl1.xaml`.</span><span class="sxs-lookup"><span data-stu-id="2a02d-112">Use the default name for the control type, `UserControl1.xaml`.</span></span> <span data-ttu-id="2a02d-113">Pour plus d’informations, consultez [Procédure pas à pas : Création d’un contenu WPF sur Windows Forms au moment](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md)de la conception.</span><span class="sxs-lookup"><span data-stu-id="2a02d-113">For more information, see [Walkthrough: Creating New WPF Content on Windows Forms at Design Time](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span></span>

2. <span data-ttu-id="2a02d-114">En mode Design, assurez-vous que `UserControl1` est sélectionné.</span><span class="sxs-lookup"><span data-stu-id="2a02d-114">In Design view, make sure that `UserControl1` is selected.</span></span>

3. <span data-ttu-id="2a02d-115">Dans la fenêtre **Propriétés** , affectez à la valeur <xref:System.Windows.FrameworkElement.Width%2A> des <xref:System.Windows.FrameworkElement.Height%2A> propriétés et la valeur **200**.</span><span class="sxs-lookup"><span data-stu-id="2a02d-115">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties to **200**.</span></span>

4. <span data-ttu-id="2a02d-116">Affectez à la <xref:System.Windows.Controls.Control.Background%2A> propriété la valeur **Blue**.</span><span class="sxs-lookup"><span data-stu-id="2a02d-116">Set the value of the <xref:System.Windows.Controls.Control.Background%2A> property to **Blue**.</span></span>

5. <span data-ttu-id="2a02d-117">Générez le projet.</span><span class="sxs-lookup"><span data-stu-id="2a02d-117">Build the project.</span></span>

## <a name="host-wpf-controls-in-a-layout-panel"></a><span data-ttu-id="2a02d-118">Héberger des contrôles WPF dans un panneau de disposition</span><span class="sxs-lookup"><span data-stu-id="2a02d-118">Host WPF controls in a layout panel</span></span>

<span data-ttu-id="2a02d-119">Vous pouvez utiliser des contrôles WPF dans des panneaux de disposition de la même façon que vous utilisez d'autres contrôles Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="2a02d-119">You can use WPF controls in layout panels in the same way you use other Windows Forms controls.</span></span>

1. <span data-ttu-id="2a02d-120">Ouvrez `Form1` dans le Concepteur Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="2a02d-120">Open `Form1` in the Windows Forms Designer.</span></span>

2. <span data-ttu-id="2a02d-121">Dans la **boîte à outils**, <xref:System.Windows.Forms.TableLayoutPanel> faites glisser un contrôle sur le formulaire.</span><span class="sxs-lookup"><span data-stu-id="2a02d-121">In the **Toolbox**, drag a <xref:System.Windows.Forms.TableLayoutPanel> control onto the form.</span></span>

3. <span data-ttu-id="2a02d-122">Dans le <xref:System.Windows.Forms.TableLayoutPanel> panneau des balises actives du contrôle, sélectionnez **Supprimer la dernière ligne**.</span><span class="sxs-lookup"><span data-stu-id="2a02d-122">On the <xref:System.Windows.Forms.TableLayoutPanel> control's smart tag panel, select **Remove Last Row**.</span></span>

4. <span data-ttu-id="2a02d-123">Augmentez la largeur et la hauteur du contrôle <xref:System.Windows.Forms.TableLayoutPanel>.</span><span class="sxs-lookup"><span data-stu-id="2a02d-123">Resize the <xref:System.Windows.Forms.TableLayoutPanel> control to a larger width and height.</span></span>

5. <span data-ttu-id="2a02d-124">Dans la **boîte à outils**, double `UserControl1` -cliquez sur pour créer `UserControl1` une instance de dans la première <xref:System.Windows.Forms.TableLayoutPanel> cellule du contrôle.</span><span class="sxs-lookup"><span data-stu-id="2a02d-124">In the **Toolbox**, double-click `UserControl1` to create an instance of `UserControl1` in the first cell of the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>

   <span data-ttu-id="2a02d-125">L'instance de `UserControl1` est hébergée dans un nouveau contrôle <xref:System.Windows.Forms.Integration.ElementHost> nommé `elementHost1`.</span><span class="sxs-lookup"><span data-stu-id="2a02d-125">The instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost1`.</span></span>

6. <span data-ttu-id="2a02d-126">Dans la **boîte à outils**, double `UserControl1` -cliquez sur pour créer une autre instance dans la <xref:System.Windows.Forms.TableLayoutPanel> deuxième cellule du contrôle.</span><span class="sxs-lookup"><span data-stu-id="2a02d-126">In the **Toolbox**, double-click `UserControl1` to create another instance in the second cell of the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>

7. <span data-ttu-id="2a02d-127">Dans la fenêtre **structure du document** , `tableLayoutPanel1`sélectionnez.</span><span class="sxs-lookup"><span data-stu-id="2a02d-127">In the **Document Outline** window, select `tableLayoutPanel1`.</span></span>

8. <span data-ttu-id="2a02d-128">Dans la fenêtre **Propriétés** , affectez à la <xref:System.Windows.Forms.Control.Padding%2A> propriété la valeur **10, 10,** 10, 10.</span><span class="sxs-lookup"><span data-stu-id="2a02d-128">In the **Properties** window, set the value of the <xref:System.Windows.Forms.Control.Padding%2A> property to **10, 10, 10, 10**.</span></span>

   <span data-ttu-id="2a02d-129">Les deux contrôles <xref:System.Windows.Forms.Integration.ElementHost> sont redimensionnés pour s'adapter à la nouvelle disposition.</span><span class="sxs-lookup"><span data-stu-id="2a02d-129">Both <xref:System.Windows.Forms.Integration.ElementHost> controls are resized to fit into the new layout.</span></span>

## <a name="use-snaplines-to-align-wpf-controls"></a><span data-ttu-id="2a02d-130">Utiliser des lignes d’alignement pour aligner les contrôles WPF</span><span class="sxs-lookup"><span data-stu-id="2a02d-130">Use snaplines to align WPF controls</span></span>

<span data-ttu-id="2a02d-131">Les lignes d'alignement permettent d'aligner facilement les contrôles sur un formulaire.</span><span class="sxs-lookup"><span data-stu-id="2a02d-131">Snaplines enable easy alignment of controls on a form.</span></span> <span data-ttu-id="2a02d-132">Vous pouvez aussi utiliser des lignes d'alignement pour aligner vos contrôles WPF.</span><span class="sxs-lookup"><span data-stu-id="2a02d-132">You can use snaplines to align your WPF controls as well.</span></span> <span data-ttu-id="2a02d-133">Pour plus d’informations, consultez [Procédure pas à pas : Réorganisation des contrôles sur Windows Forms à](../controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)l’aide des lignes d’alignement.</span><span class="sxs-lookup"><span data-stu-id="2a02d-133">For more information, see [Walkthrough: Arranging Controls on Windows Forms Using Snaplines](../controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).</span></span>

1. <span data-ttu-id="2a02d-134">À partir de la **boîte à outils**, `UserControl1` faites glisser une instance de sur le formulaire, puis placez- <xref:System.Windows.Forms.TableLayoutPanel> la dans l’espace sous le contrôle.</span><span class="sxs-lookup"><span data-stu-id="2a02d-134">From the **Toolbox**, drag an instance of `UserControl1` onto the form, and place it in the space beneath the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>

   <span data-ttu-id="2a02d-135">L'instance de `UserControl1` est hébergée dans un nouveau contrôle <xref:System.Windows.Forms.Integration.ElementHost> nommé `elementHost3`.</span><span class="sxs-lookup"><span data-stu-id="2a02d-135">The instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost3`.</span></span>

2. <span data-ttu-id="2a02d-136">À l'aide des lignes d'alignement, alignez le bord gauche de `elementHost3` avec le bord gauche du contrôle <xref:System.Windows.Forms.TableLayoutPanel>.</span><span class="sxs-lookup"><span data-stu-id="2a02d-136">Using snaplines, align the left edge of `elementHost3` with the left edge of <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>

3. <span data-ttu-id="2a02d-137">À l'aide des lignes d'alignement, affectez à `elementHost3` la même largeur que celle du contrôle <xref:System.Windows.Forms.TableLayoutPanel>.</span><span class="sxs-lookup"><span data-stu-id="2a02d-137">Using snaplines, size `elementHost3` to the same width as the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>

4. <span data-ttu-id="2a02d-138">Déplacez `elementHost3` vers le contrôle <xref:System.Windows.Forms.TableLayoutPanel> jusqu'à ce qu'une ligne d'alignement centrale apparaisse entre les contrôles.</span><span class="sxs-lookup"><span data-stu-id="2a02d-138">Move `elementHost3` toward the <xref:System.Windows.Forms.TableLayoutPanel> control until a center snapline appears between the controls.</span></span>

5. <span data-ttu-id="2a02d-139">Dans la fenêtre **Propriétés** , affectez à la propriété Margin la valeur **20, 20, 20, 20**.</span><span class="sxs-lookup"><span data-stu-id="2a02d-139">In the **Properties** window, set the value of the Margin property to **20, 20, 20, 20**.</span></span>

6. <span data-ttu-id="2a02d-140">Déplacez le `elementHost3` hors du contrôle <xref:System.Windows.Forms.TableLayoutPanel> jusqu'à ce que la ligne d'alignement centrale réapparaisse.</span><span class="sxs-lookup"><span data-stu-id="2a02d-140">Move the `elementHost3` away from the <xref:System.Windows.Forms.TableLayoutPanel> control until the center snapline appears again.</span></span> <span data-ttu-id="2a02d-141">La ligne d'alignement centrale indique maintenant une marge de 20.</span><span class="sxs-lookup"><span data-stu-id="2a02d-141">The center snapline now indicates a margin of 20.</span></span>

7. <span data-ttu-id="2a02d-142">Se `elementHost3` déplacer vers la droite jusqu’à ce que son bord gauche s’aligne avec `elementHost1`le bord gauche de.</span><span class="sxs-lookup"><span data-stu-id="2a02d-142">Move `elementHost3` to the right until its left edge aligns with the left edge of `elementHost1`.</span></span>

8. <span data-ttu-id="2a02d-143">Modifiez la largeur de `elementHost3` jusqu'à ce que son bord droit soit aligné avec le bord droit de `elementHost2`.</span><span class="sxs-lookup"><span data-stu-id="2a02d-143">Change the width of `elementHost3` until its right edge aligns with the right edge of `elementHost2`.</span></span>

## <a name="anchor-and-dock-wpf-controls"></a><span data-ttu-id="2a02d-144">Ancrer et ancrer des contrôles WPF</span><span class="sxs-lookup"><span data-stu-id="2a02d-144">Anchor and dock WPF controls</span></span>

<span data-ttu-id="2a02d-145">Un contrôle WPF hébergé sur un formulaire a le même comportement d'ancrage que d'autres contrôles Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="2a02d-145">A WPF control hosted on a form has the same anchoring and docking behavior as other Windows Forms controls.</span></span>

1. <span data-ttu-id="2a02d-146">Sélectionnez `elementHost1`.</span><span class="sxs-lookup"><span data-stu-id="2a02d-146">Select `elementHost1`.</span></span>

2. <span data-ttu-id="2a02d-147">Dans la fenêtre **Propriétés** , affectez <xref:System.Windows.Forms.Control.Anchor%2A> à la propriété la valeur **haut, bas, gauche, droite**.</span><span class="sxs-lookup"><span data-stu-id="2a02d-147">In the **Properties** window, set the <xref:System.Windows.Forms.Control.Anchor%2A> property to **Top, Bottom, Left, Right**.</span></span>

3. <span data-ttu-id="2a02d-148">Agrandissez le contrôle <xref:System.Windows.Forms.TableLayoutPanel>.</span><span class="sxs-lookup"><span data-stu-id="2a02d-148">Resize the <xref:System.Windows.Forms.TableLayoutPanel> control to a larger size.</span></span>

   <span data-ttu-id="2a02d-149">Le contrôle `elementHost1` est redimensionné pour remplir la cellule.</span><span class="sxs-lookup"><span data-stu-id="2a02d-149">The `elementHost1` control resizes to fill the cell.</span></span>

4. <span data-ttu-id="2a02d-150">Sélectionnez `elementHost2`.</span><span class="sxs-lookup"><span data-stu-id="2a02d-150">Select `elementHost2`.</span></span>

5. <span data-ttu-id="2a02d-151">Dans la fenêtre **Propriétés** , affectez à <xref:System.Windows.Forms.Control.Dock%2A> <xref:System.Windows.Forms.DockStyle.Fill>la propriété la valeur.</span><span class="sxs-lookup"><span data-stu-id="2a02d-151">In the **Properties** window, set the value of the <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>

   <span data-ttu-id="2a02d-152">Le contrôle `elementHost2` est redimensionné pour remplir la cellule.</span><span class="sxs-lookup"><span data-stu-id="2a02d-152">The `elementHost2` control resizes to fill the cell.</span></span>

6. <span data-ttu-id="2a02d-153">Sélectionnez le contrôle <xref:System.Windows.Forms.TableLayoutPanel>.</span><span class="sxs-lookup"><span data-stu-id="2a02d-153">Select the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>

7. <span data-ttu-id="2a02d-154">Affectez à sa propriété <xref:System.Windows.Forms.Control.Dock%2A> la valeur <xref:System.Windows.Forms.DockStyle.Top>.</span><span class="sxs-lookup"><span data-stu-id="2a02d-154">Set the value of its <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Top>.</span></span>

8. <span data-ttu-id="2a02d-155">Sélectionnez `elementHost3`.</span><span class="sxs-lookup"><span data-stu-id="2a02d-155">Select `elementHost3`.</span></span>

9. <span data-ttu-id="2a02d-156">Affectez à sa propriété <xref:System.Windows.Forms.Control.Dock%2A> la valeur <xref:System.Windows.Forms.DockStyle.Fill>.</span><span class="sxs-lookup"><span data-stu-id="2a02d-156">Set the value of its <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>

   <span data-ttu-id="2a02d-157">Le contrôle `elementHost3` est redimensionné pour remplir l'espace restant sur le formulaire.</span><span class="sxs-lookup"><span data-stu-id="2a02d-157">The `elementHost3` control resizes to fill the remaining space on the form.</span></span>

10. <span data-ttu-id="2a02d-158">Redimensionnez le formulaire.</span><span class="sxs-lookup"><span data-stu-id="2a02d-158">Resize the form.</span></span>

    <span data-ttu-id="2a02d-159">Les trois contrôles <xref:System.Windows.Forms.Integration.ElementHost> sont redimensionnés correctement.</span><span class="sxs-lookup"><span data-stu-id="2a02d-159">All three <xref:System.Windows.Forms.Integration.ElementHost> controls resize appropriately.</span></span>

    <span data-ttu-id="2a02d-160">Pour plus d'informations, voir [Procédure : Ancrer et ancrer des contrôles enfants dans](../controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)un contrôle TableLayoutPanel.</span><span class="sxs-lookup"><span data-stu-id="2a02d-160">For more information, see [How to: Anchor and Dock Child Controls in a TableLayoutPanel Control](../controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2a02d-161">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2a02d-161">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="2a02d-162">Guide pratique pour Ancrer et ancrer des contrôles enfants dans un contrôle TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="2a02d-162">How to: Anchor and Dock Child Controls in a TableLayoutPanel Control</span></span>](../controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)
- [<span data-ttu-id="2a02d-163">Guide pratique pour Aligner un contrôle sur les bords des formulaires au moment du design</span><span class="sxs-lookup"><span data-stu-id="2a02d-163">How to: Align a Control to the Edges of Forms at Design Time</span></span>](../controls/how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)
- [<span data-ttu-id="2a02d-164">Procédure pas à pas : Réorganisation des contrôles sur Windows Forms à l’aide de lignes d’alignement</span><span class="sxs-lookup"><span data-stu-id="2a02d-164">Walkthrough: Arranging Controls on Windows Forms Using Snaplines</span></span>](../controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
- [<span data-ttu-id="2a02d-165">Migration et interopérabilité</span><span class="sxs-lookup"><span data-stu-id="2a02d-165">Migration and Interoperability</span></span>](../../wpf/advanced/migration-and-interoperability.md)
- [<span data-ttu-id="2a02d-166">Utilisation de contrôles WPF</span><span class="sxs-lookup"><span data-stu-id="2a02d-166">Using WPF Controls</span></span>](using-wpf-controls.md)
- [<span data-ttu-id="2a02d-167">Concevoir en XAML dans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="2a02d-167">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)
