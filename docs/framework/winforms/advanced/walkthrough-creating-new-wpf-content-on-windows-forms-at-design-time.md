---
title: Créer un contenu WPF sur Windows Forms
titleSuffix: ''
ms.date: 08/18/2018
helpviewer_keywords:
- interoperability [Windows Forms], WPF and Windows Forms
- WPF content [Windows Forms], hosting in Windows Forms
- hosting WPF content in Windows Forms
- ElementHost control
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: 2e92d8e8-f0e4-4df7-9f07-2acf35cd798c
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 69a0598b05d1b2bff84b203317d6d5a166ce109d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746390"
---
# <a name="walkthrough-create-new-wpf-content-on-windows-forms-at-design-time"></a><span data-ttu-id="1bde1-102">Procédure pas à pas : création d’un contenu WPF sur Windows Forms au moment du design</span><span class="sxs-lookup"><span data-stu-id="1bde1-102">Walkthrough: Create new WPF content on Windows Forms at design time</span></span>

<span data-ttu-id="1bde1-103">Cet article vous montre comment créer un contrôle Windows Presentation Foundation (WPF) à utiliser dans vos applications basées sur Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="1bde1-103">This article shows you how to create a Windows Presentation Foundation (WPF) control for use in your Windows Forms-based applications.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="1bde1-104">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="1bde1-104">Prerequisites</span></span>

<span data-ttu-id="1bde1-105">Cette procédure pas à pas nécessite Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1bde1-105">You need Visual Studio to complete this walkthrough.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="1bde1-106">Créer le projet</span><span class="sxs-lookup"><span data-stu-id="1bde1-106">Create the project</span></span>

<span data-ttu-id="1bde1-107">Ouvrez Visual Studio et créez un projet d' **application Windows Forms (.NET Framework)** dans Visual Basic ou visual C# nommé `HostingWpf`.</span><span class="sxs-lookup"><span data-stu-id="1bde1-107">Open Visual Studio and create a new **Windows Forms App (.NET Framework)** project in Visual Basic or Visual C# named `HostingWpf`.</span></span>

> [!NOTE]
> <span data-ttu-id="1bde1-108">Lors de l'hébergement de contenu WPF, seuls les projets Visual Basic et C# sont pris en charge.</span><span class="sxs-lookup"><span data-stu-id="1bde1-108">When hosting WPF content, only C# and Visual Basic projects are supported.</span></span>

## <a name="create-a-new-wpf-control"></a><span data-ttu-id="1bde1-109">Créer un contrôle WPF</span><span class="sxs-lookup"><span data-stu-id="1bde1-109">Create a new WPF control</span></span>

<span data-ttu-id="1bde1-110">La création d'un contrôle WPF et son ajout à votre projet sont des tâches aussi simples que l'ajout de tout autre élément à votre projet.</span><span class="sxs-lookup"><span data-stu-id="1bde1-110">Creating a new WPF control and adding it to your project is as easy as adding any other item to your project.</span></span> <span data-ttu-id="1bde1-111">Le Concepteur Windows Forms fonctionne avec un type particulier de contrôle nommé contrôle *composite*ou *contrôle utilisateur*.</span><span class="sxs-lookup"><span data-stu-id="1bde1-111">The Windows Forms Designer works with a particular kind of control named *composite control*, or *user control*.</span></span> <span data-ttu-id="1bde1-112">Pour plus d'informations sur les contrôles utilisateur WPF, consultez <xref:System.Windows.Controls.UserControl>.</span><span class="sxs-lookup"><span data-stu-id="1bde1-112">For more information about WPF user controls, see <xref:System.Windows.Controls.UserControl>.</span></span>

> [!NOTE]
> <span data-ttu-id="1bde1-113">Le type <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType> pour WPF est distinct du type de contrôle utilisateur fourni par Windows Forms, également nommé <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1bde1-113">The <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType> type for WPF is distinct from the user control type provided by Windows Forms, which is also named <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="1bde1-114">Pour créer un contrôle WPF :</span><span class="sxs-lookup"><span data-stu-id="1bde1-114">To create a new WPF control:</span></span>

1. <span data-ttu-id="1bde1-115">Dans **Explorateur de solutions**, ajoutez un nouveau projet de **bibliothèque de contrôles utilisateur (.NET Framework) WPF** à la solution.</span><span class="sxs-lookup"><span data-stu-id="1bde1-115">In **Solution Explorer**, add a new **WPF User Control Library (.NET Framework)** project to the solution.</span></span> <span data-ttu-id="1bde1-116">Utilisez le nom par défaut pour la bibliothèque de contrôles, `WpfControlLibrary1`.</span><span class="sxs-lookup"><span data-stu-id="1bde1-116">Use the default name for the control library, `WpfControlLibrary1`.</span></span> <span data-ttu-id="1bde1-117">Le nom du contrôle par défaut est `UserControl1.xaml`.</span><span class="sxs-lookup"><span data-stu-id="1bde1-117">The default control name is `UserControl1.xaml`.</span></span>

   <span data-ttu-id="1bde1-118">L’ajout du nouveau contrôle a les effets suivants :</span><span class="sxs-lookup"><span data-stu-id="1bde1-118">Adding the new control has the following effects:</span></span>

   - <span data-ttu-id="1bde1-119">Le fichier UserControl1.xaml est ajouté.</span><span class="sxs-lookup"><span data-stu-id="1bde1-119">File UserControl1.xaml is added.</span></span>

   - <span data-ttu-id="1bde1-120">Le fichier UserControl1.xaml.cs (ou UserControl1. Xaml. vb) est ajouté.</span><span class="sxs-lookup"><span data-stu-id="1bde1-120">File UserControl1.xaml.cs (or UserControl1.xaml.vb) is added.</span></span> <span data-ttu-id="1bde1-121">Ce fichier contient le code-behind pour les gestionnaires d'événements et autre implémentation.</span><span class="sxs-lookup"><span data-stu-id="1bde1-121">This file contains the code-behind for event handlers and other implementation.</span></span>

   - <span data-ttu-id="1bde1-122">Les références aux assemblys WPF sont ajoutées.</span><span class="sxs-lookup"><span data-stu-id="1bde1-122">References to WPF assemblies are added.</span></span>

   - <span data-ttu-id="1bde1-123">Le fichier UserControl1. xaml s’ouvre dans le Concepteur WPF pour Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1bde1-123">File UserControl1.xaml opens in the WPF Designer for Visual Studio.</span></span>

2. <span data-ttu-id="1bde1-124">En mode Design, assurez-vous que `UserControl1` est sélectionné.</span><span class="sxs-lookup"><span data-stu-id="1bde1-124">In Design view, make sure that `UserControl1` is selected.</span></span>

3. <span data-ttu-id="1bde1-125">Dans la fenêtre **Propriétés** , affectez la valeur **200**aux propriétés <xref:System.Windows.FrameworkElement.Width%2A> et <xref:System.Windows.FrameworkElement.Height%2A>.</span><span class="sxs-lookup"><span data-stu-id="1bde1-125">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties to **200**.</span></span>

4. <span data-ttu-id="1bde1-126">À partir de la **boîte à outils**, faites glisser un contrôle <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> sur l’aire de conception.</span><span class="sxs-lookup"><span data-stu-id="1bde1-126">From the **Toolbox**, drag a <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> control onto the design surface.</span></span>

5. <span data-ttu-id="1bde1-127">Dans la fenêtre **Propriétés** , affectez la valeur **contenu hébergé**à la propriété <xref:System.Windows.Controls.TextBox.Text%2A>.</span><span class="sxs-lookup"><span data-stu-id="1bde1-127">In the **Properties** window, set the value of the <xref:System.Windows.Controls.TextBox.Text%2A> property to **Hosted Content**.</span></span>

   > [!NOTE]
   > <span data-ttu-id="1bde1-128">En général, vous devez héberger du contenu WPF plus sophistiqué.</span><span class="sxs-lookup"><span data-stu-id="1bde1-128">In general, you should host more sophisticated WPF content.</span></span> <span data-ttu-id="1bde1-129">Le contrôle <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> est utilisé ici uniquement à titre d'illustration.</span><span class="sxs-lookup"><span data-stu-id="1bde1-129">The <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> control is used here for illustrative purposes only.</span></span>

6. <span data-ttu-id="1bde1-130">créer le projet ;</span><span class="sxs-lookup"><span data-stu-id="1bde1-130">Build the project.</span></span>

## <a name="add-a-wpf-control-to-a-windows-form"></a><span data-ttu-id="1bde1-131">Ajouter un contrôle WPF à un Windows Form</span><span class="sxs-lookup"><span data-stu-id="1bde1-131">Add a WPF control to a Windows Form</span></span>

<span data-ttu-id="1bde1-132">Votre nouveau contrôle WPF est prêt à être utilisé sur le formulaire.</span><span class="sxs-lookup"><span data-stu-id="1bde1-132">Your new WPF control is ready for use on the form.</span></span> <span data-ttu-id="1bde1-133">Windows Forms utilise le contrôle <xref:System.Windows.Forms.Integration.ElementHost> pour héberger du contenu WPF.</span><span class="sxs-lookup"><span data-stu-id="1bde1-133">Windows Forms uses the <xref:System.Windows.Forms.Integration.ElementHost> control to host WPF content.</span></span>

<span data-ttu-id="1bde1-134">Pour ajouter un contrôle WPF à un Windows Form :</span><span class="sxs-lookup"><span data-stu-id="1bde1-134">To add a WPF control to a Windows Form:</span></span>

1. <span data-ttu-id="1bde1-135">Ouvrez `Form1` dans le Concepteur Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="1bde1-135">Open `Form1` in the Windows Forms Designer.</span></span>

2. <span data-ttu-id="1bde1-136">Dans la **boîte à outils**, recherchez l’onglet nommé **contrôles utilisateur WPF WPFUserControlLibrary**.</span><span class="sxs-lookup"><span data-stu-id="1bde1-136">In the **Toolbox**, find the tab labeled **WPFUserControlLibrary WPF User Controls**.</span></span>

3. <span data-ttu-id="1bde1-137">Faites glisser une instance de `UserControl1` sur le formulaire.</span><span class="sxs-lookup"><span data-stu-id="1bde1-137">Drag an instance of `UserControl1` onto the form.</span></span>

    - <span data-ttu-id="1bde1-138">Un contrôle <xref:System.Windows.Forms.Integration.ElementHost> est créé automatiquement sur le formulaire pour héberger le contrôle WPF.</span><span class="sxs-lookup"><span data-stu-id="1bde1-138">An <xref:System.Windows.Forms.Integration.ElementHost> control is created automatically on the form to host the WPF control.</span></span>

    - <span data-ttu-id="1bde1-139">Le contrôle <xref:System.Windows.Forms.Integration.ElementHost> est nommé `elementHost1` et, dans la fenêtre **Propriétés** , vous pouvez voir que sa propriété <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> est définie sur **UserControl1**.</span><span class="sxs-lookup"><span data-stu-id="1bde1-139">The <xref:System.Windows.Forms.Integration.ElementHost> control is named `elementHost1` and in the **Properties** window, you can see its <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> property is set to **UserControl1**.</span></span>

    - <span data-ttu-id="1bde1-140">des références aux assemblys WPF sont ajoutées au projet.</span><span class="sxs-lookup"><span data-stu-id="1bde1-140">References to WPF assemblies are added to the project.</span></span>

    - <span data-ttu-id="1bde1-141">Le contrôle `elementHost1` a un panneau de Smart Tags qui affiche les options d’hébergement disponibles.</span><span class="sxs-lookup"><span data-stu-id="1bde1-141">The `elementHost1` control has a smart tag panel that shows the available hosting options.</span></span>

4. <span data-ttu-id="1bde1-142">Dans le panneau des balises actives des **Tâches ElementHost** , sélectionnez **ancrer dans le conteneur parent**.</span><span class="sxs-lookup"><span data-stu-id="1bde1-142">In the **ElementHost Tasks** smart tag panel, select **Dock in parent container**.</span></span>

5. <span data-ttu-id="1bde1-143">Appuyez sur **F5** pour générer et exécuter l’application.</span><span class="sxs-lookup"><span data-stu-id="1bde1-143">Press **F5** to build and run the application.</span></span>

## <a name="next-steps"></a><span data-ttu-id="1bde1-144">Étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="1bde1-144">Next steps</span></span>

<span data-ttu-id="1bde1-145">Windows Forms et WPF sont des technologies différentes, mais elles sont conçues pour interagir étroitement.</span><span class="sxs-lookup"><span data-stu-id="1bde1-145">Windows Forms and WPF are different technologies, but they are designed to interoperate closely.</span></span> <span data-ttu-id="1bde1-146">Pour fournir une apparence et un comportement plus riches dans vos applications, essayez ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="1bde1-146">To provide richer appearance and behavior in your applications, try the following:</span></span>

- <span data-ttu-id="1bde1-147">Hébergez un contrôle Windows Forms dans une page WPF.</span><span class="sxs-lookup"><span data-stu-id="1bde1-147">Host a Windows Forms control in a WPF page.</span></span> <span data-ttu-id="1bde1-148">Pour plus d’informations, consultez [procédure pas à pas : Hébergement d’un contrôle de Windows Forms dans WPF](../../wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="1bde1-148">For more information, see [Walkthrough: Hosting a Windows Forms Control in WPF](../../wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md).</span></span>

- <span data-ttu-id="1bde1-149">Appliquez des styles visuels Windows Forms à votre contenu WPF.</span><span class="sxs-lookup"><span data-stu-id="1bde1-149">Apply Windows Forms visual styles to your WPF content.</span></span> <span data-ttu-id="1bde1-150">Pour plus d’informations, consultez [Guide pratique pour activer des styles visuels dans une application hybride](../../wpf/advanced/how-to-enable-visual-styles-in-a-hybrid-application.md).</span><span class="sxs-lookup"><span data-stu-id="1bde1-150">For more information, see [How to: Enable Visual Styles in a Hybrid Application](../../wpf/advanced/how-to-enable-visual-styles-in-a-hybrid-application.md).</span></span>

- <span data-ttu-id="1bde1-151">Modifiez le style de votre contenu WPF.</span><span class="sxs-lookup"><span data-stu-id="1bde1-151">Change the style of your WPF content.</span></span> <span data-ttu-id="1bde1-152">Pour plus d’informations, consultez [procédure pas à pas : stylisation du contenu WPF](walkthrough-styling-wpf-content.md).</span><span class="sxs-lookup"><span data-stu-id="1bde1-152">For more information, see [Walkthrough: Styling WPF Content](walkthrough-styling-wpf-content.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1bde1-153">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1bde1-153">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="1bde1-154">Migration et interopérabilité</span><span class="sxs-lookup"><span data-stu-id="1bde1-154">Migration and Interoperability</span></span>](../../wpf/advanced/migration-and-interoperability.md)
- [<span data-ttu-id="1bde1-155">Utilisation de contrôles WPF</span><span class="sxs-lookup"><span data-stu-id="1bde1-155">Using WPF Controls</span></span>](using-wpf-controls.md)
- [<span data-ttu-id="1bde1-156">Concevoir en XAML dans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="1bde1-156">Design XAML in Visual Studio</span></span>](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
