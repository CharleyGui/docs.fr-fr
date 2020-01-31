---
title: "Procédure pas à pas : mappage de propriétés à l'aide de l'élément WindowsFormsHost"
ms.date: 08/18/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- mapping properties [WPF]
- WindowsFormsHost element property mapping [WPF]
ms.assetid: 74809167-bf8e-48b7-a2e7-b4ea08bc7d8c
ms.openlocfilehash: c076937d6431adf1750793d47ece88dc82edf95c
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794098"
---
# <a name="walkthrough-mapping-properties-using-the-windowsformshost-element"></a><span data-ttu-id="31c2a-102">Procédure pas à pas : mappage de propriétés à l'aide de l'élément WindowsFormsHost</span><span class="sxs-lookup"><span data-stu-id="31c2a-102">Walkthrough: Mapping Properties Using the WindowsFormsHost Element</span></span>

<span data-ttu-id="31c2a-103">Cette procédure pas à pas vous montre comment utiliser la propriété <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A> pour mapper des propriétés [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] à des propriétés correspondantes sur un contrôle Windows Forms hébergé.</span><span class="sxs-lookup"><span data-stu-id="31c2a-103">This walkthrough shows you how to use the <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A> property to map [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] properties to corresponding properties on a hosted Windows Forms control.</span></span>

<span data-ttu-id="31c2a-104">Cette procédure pas à pas décrit notamment les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="31c2a-104">Tasks illustrated in this walkthrough include:</span></span>

- <span data-ttu-id="31c2a-105">Création du projet.</span><span class="sxs-lookup"><span data-stu-id="31c2a-105">Creating the project.</span></span>

- <span data-ttu-id="31c2a-106">Définition de la disposition de l’application.</span><span class="sxs-lookup"><span data-stu-id="31c2a-106">Defining the application layout.</span></span>

- <span data-ttu-id="31c2a-107">Définition d’un nouveau mappage de propriété.</span><span class="sxs-lookup"><span data-stu-id="31c2a-107">Defining a new property mapping.</span></span>

- <span data-ttu-id="31c2a-108">Suppression d’un mappage de propriété par défaut.</span><span class="sxs-lookup"><span data-stu-id="31c2a-108">Removing a default property mapping.</span></span>

- <span data-ttu-id="31c2a-109">Remplacement d’un mappage de propriété par défaut.</span><span class="sxs-lookup"><span data-stu-id="31c2a-109">Replacing a default property mapping.</span></span>

- <span data-ttu-id="31c2a-110">Extension d’un mappage de propriété par défaut.</span><span class="sxs-lookup"><span data-stu-id="31c2a-110">Extending a default property mapping.</span></span>

<span data-ttu-id="31c2a-111">Pour obtenir le code complet des tâches illustrées dans cette procédure pas à pas, consultez [mappage de propriétés à l’aide de l’exemple d’élément WindowsFormsHost](https://go.microsoft.com/fwlink/?LinkID=160019).</span><span class="sxs-lookup"><span data-stu-id="31c2a-111">For a complete code listing of the tasks illustrated in this walkthrough, see [Mapping Properties Using the WindowsFormsHost Element Sample](https://go.microsoft.com/fwlink/?LinkID=160019).</span></span>

<span data-ttu-id="31c2a-112">Lorsque vous avez terminé, vous pouvez mapper [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] propriétés aux propriétés correspondantes sur un contrôle Windows Forms hébergé.</span><span class="sxs-lookup"><span data-stu-id="31c2a-112">When you are finished, you will be able to map [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] properties to corresponding properties on a hosted Windows Forms control.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="31c2a-113">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="31c2a-113">Prerequisites</span></span>

<span data-ttu-id="31c2a-114">Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :</span><span class="sxs-lookup"><span data-stu-id="31c2a-114">You need the following components to complete this walkthrough:</span></span>

- <span data-ttu-id="31c2a-115">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="31c2a-115">Visual Studio 2017</span></span>

## <a name="create-and-set-up-the-project"></a><span data-ttu-id="31c2a-116">Créer et configurer le projet</span><span class="sxs-lookup"><span data-stu-id="31c2a-116">Create and set up the project</span></span>

1. <span data-ttu-id="31c2a-117">Créez un projet d' **application WPF** nommé `PropertyMappingWithWfhSample`.</span><span class="sxs-lookup"><span data-stu-id="31c2a-117">Create a **WPF App** project named `PropertyMappingWithWfhSample`.</span></span>

2. <span data-ttu-id="31c2a-118">Dans **Explorateur de solutions**, ajoutez une référence à l’assembly windowsformsintegration, nommé windowsformsintegration. dll.</span><span class="sxs-lookup"><span data-stu-id="31c2a-118">In **Solution Explorer**, add a reference to the WindowsFormsIntegration assembly, which is named WindowsFormsIntegration.dll.</span></span>

3. <span data-ttu-id="31c2a-119">Dans **Explorateur de solutions**, ajoutez des références aux assemblys System. Drawing et System. Windows. Forms.</span><span class="sxs-lookup"><span data-stu-id="31c2a-119">In **Solution Explorer**, add references to the System.Drawing and System.Windows.Forms assemblies.</span></span>

## <a name="defining-the-application-layout"></a><span data-ttu-id="31c2a-120">Définition de la disposition de l’application</span><span class="sxs-lookup"><span data-stu-id="31c2a-120">Defining the Application Layout</span></span>

<span data-ttu-id="31c2a-121">L’application basée sur [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]utilise l’élément <xref:System.Windows.Forms.Integration.WindowsFormsHost> pour héberger un contrôle Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="31c2a-121">The [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-based application uses the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element to host a Windows Forms control.</span></span>

### <a name="to-define-the-application-layout"></a><span data-ttu-id="31c2a-122">Pour définir la disposition de l’application</span><span class="sxs-lookup"><span data-stu-id="31c2a-122">To define the application layout</span></span>

1. <span data-ttu-id="31c2a-123">Ouvrez Window1. xaml dans le Concepteur WPF.</span><span class="sxs-lookup"><span data-stu-id="31c2a-123">Open Window1.xaml in the WPF Designer.</span></span>

2. <span data-ttu-id="31c2a-124">Remplacez le code existant par le code ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="31c2a-124">Replace the existing code with the following code.</span></span>

     [!code-xaml[PropertyMappingWithWfhSample#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml#1)]

3. <span data-ttu-id="31c2a-125">Ouvrez Window1.xaml.cs dans l’éditeur de code.</span><span class="sxs-lookup"><span data-stu-id="31c2a-125">Open Window1.xaml.cs in the Code Editor.</span></span>

4. <span data-ttu-id="31c2a-126">En haut du fichier, importez les espaces de noms suivants.</span><span class="sxs-lookup"><span data-stu-id="31c2a-126">At the top of the file, import the following namespaces.</span></span>

     [!code-csharp[PropertyMappingWithWfhSample#20](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#20)]
     [!code-vb[PropertyMappingWithWfhSample#20](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#20)]

## <a name="defining-a-new-property-mapping"></a><span data-ttu-id="31c2a-127">Définition d’un nouveau mappage de propriété</span><span class="sxs-lookup"><span data-stu-id="31c2a-127">Defining a New Property Mapping</span></span>

<span data-ttu-id="31c2a-128">L’élément <xref:System.Windows.Forms.Integration.WindowsFormsHost> fournit plusieurs mappages de propriété par défaut.</span><span class="sxs-lookup"><span data-stu-id="31c2a-128">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element provides several default property mappings.</span></span> <span data-ttu-id="31c2a-129">Vous ajoutez un nouveau mappage de propriété en appelant la méthode <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> sur le <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>de l’élément <xref:System.Windows.Forms.Integration.WindowsFormsHost>.</span><span class="sxs-lookup"><span data-stu-id="31c2a-129">You add a new property mapping by calling the <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> method on the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element's <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>.</span></span>

### <a name="to-define-a-new-property-mapping"></a><span data-ttu-id="31c2a-130">Pour définir un nouveau mappage de propriété</span><span class="sxs-lookup"><span data-stu-id="31c2a-130">To define a new property mapping</span></span>

- <span data-ttu-id="31c2a-131">Copiez le code suivant dans la définition de la classe `Window1`.</span><span class="sxs-lookup"><span data-stu-id="31c2a-131">Copy the following code into the definition for the `Window1` class.</span></span>

     [!code-csharp[PropertyMappingWithWfhSample#14](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#14)]
     [!code-vb[PropertyMappingWithWfhSample#14](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#14)]

     <span data-ttu-id="31c2a-132">La méthode `AddClipMapping` ajoute un nouveau mappage pour la propriété <xref:System.Windows.UIElement.Clip%2A>.</span><span class="sxs-lookup"><span data-stu-id="31c2a-132">The `AddClipMapping` method adds a new mapping for the <xref:System.Windows.UIElement.Clip%2A> property.</span></span>

     <span data-ttu-id="31c2a-133">La méthode `OnClipChange` convertit la propriété <xref:System.Windows.UIElement.Clip%2A> en propriété<xref:System.Windows.Forms.Control.Region%2A> Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="31c2a-133">The `OnClipChange` method translates the <xref:System.Windows.UIElement.Clip%2A> property to the Windows Forms<xref:System.Windows.Forms.Control.Region%2A> property.</span></span>

     <span data-ttu-id="31c2a-134">La méthode `Window1_SizeChanged` gère l’événement de <xref:System.Windows.FrameworkElement.SizeChanged> de la fenêtre et dimensionne la zone de découpage pour l’adapter à la fenêtre d’application.</span><span class="sxs-lookup"><span data-stu-id="31c2a-134">The `Window1_SizeChanged` method handles the window's <xref:System.Windows.FrameworkElement.SizeChanged> event and sizes the clipping region to fit the application window.</span></span>

## <a name="removing-a-default-property-mapping"></a><span data-ttu-id="31c2a-135">Suppression d’un mappage de propriété par défaut</span><span class="sxs-lookup"><span data-stu-id="31c2a-135">Removing a Default Property Mapping</span></span>

<span data-ttu-id="31c2a-136">Supprimez un mappage de propriété par défaut en appelant la méthode <xref:System.Windows.Forms.Integration.PropertyMap.Remove%2A> sur le <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>de l’élément <xref:System.Windows.Forms.Integration.WindowsFormsHost>.</span><span class="sxs-lookup"><span data-stu-id="31c2a-136">Remove a default property mapping by calling the <xref:System.Windows.Forms.Integration.PropertyMap.Remove%2A> method on the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element's <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>.</span></span>

### <a name="to-remove-a-default-property-mapping"></a><span data-ttu-id="31c2a-137">Pour supprimer un mappage de propriété par défaut</span><span class="sxs-lookup"><span data-stu-id="31c2a-137">To remove a default property mapping</span></span>

- <span data-ttu-id="31c2a-138">Copiez le code suivant dans la définition de la classe `Window1`.</span><span class="sxs-lookup"><span data-stu-id="31c2a-138">Copy the following code into the definition for the `Window1` class.</span></span>

     [!code-csharp[PropertyMappingWithWfhSample#13](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#13)]
     [!code-vb[PropertyMappingWithWfhSample#13](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#13)]

     <span data-ttu-id="31c2a-139">La méthode `RemoveCursorMapping` supprime le mappage par défaut pour la propriété <xref:System.Windows.FrameworkElement.Cursor%2A>.</span><span class="sxs-lookup"><span data-stu-id="31c2a-139">The `RemoveCursorMapping` method deletes the default mapping for the <xref:System.Windows.FrameworkElement.Cursor%2A> property.</span></span>

## <a name="replacing-a-default-property-mapping"></a><span data-ttu-id="31c2a-140">Remplacement d’un mappage de propriété par défaut</span><span class="sxs-lookup"><span data-stu-id="31c2a-140">Replacing a Default Property Mapping</span></span>

<span data-ttu-id="31c2a-141">Remplacez un mappage de propriété par défaut en supprimant le mappage par défaut et en appelant la méthode <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> sur le <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>de l’élément <xref:System.Windows.Forms.Integration.WindowsFormsHost>.</span><span class="sxs-lookup"><span data-stu-id="31c2a-141">Replace a default property mapping by removing the default mapping and calling the <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> method on the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element's <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>.</span></span>

### <a name="to-replace-a-default-property-mapping"></a><span data-ttu-id="31c2a-142">Pour remplacer un mappage de propriété par défaut</span><span class="sxs-lookup"><span data-stu-id="31c2a-142">To replace a default property mapping</span></span>

- <span data-ttu-id="31c2a-143">Copiez le code suivant dans la définition de la classe `Window1`.</span><span class="sxs-lookup"><span data-stu-id="31c2a-143">Copy the following code into the definition for the `Window1` class.</span></span>

     [!code-csharp[PropertyMappingWithWfhSample#12](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#12)]
     [!code-vb[PropertyMappingWithWfhSample#12](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#12)]

     <span data-ttu-id="31c2a-144">La méthode `ReplaceFlowDirectionMapping` remplace le mappage par défaut pour la propriété <xref:System.Windows.FrameworkElement.FlowDirection%2A>.</span><span class="sxs-lookup"><span data-stu-id="31c2a-144">The `ReplaceFlowDirectionMapping` method replaces the default mapping for the <xref:System.Windows.FrameworkElement.FlowDirection%2A> property.</span></span>

     <span data-ttu-id="31c2a-145">La méthode `OnFlowDirectionChange` convertit la propriété <xref:System.Windows.FrameworkElement.FlowDirection%2A> en propriété<xref:System.Windows.Forms.Control.RightToLeft%2A> Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="31c2a-145">The `OnFlowDirectionChange` method translates the <xref:System.Windows.FrameworkElement.FlowDirection%2A> property to the Windows Forms<xref:System.Windows.Forms.Control.RightToLeft%2A> property.</span></span>

     <span data-ttu-id="31c2a-146">La méthode `cb_CheckedChanged` gère l’événement <xref:System.Windows.Forms.CheckBox.CheckedChanged> sur le contrôle <xref:System.Windows.Forms.CheckBox>.</span><span class="sxs-lookup"><span data-stu-id="31c2a-146">The `cb_CheckedChanged` method handles the <xref:System.Windows.Forms.CheckBox.CheckedChanged> event on the <xref:System.Windows.Forms.CheckBox> control.</span></span> <span data-ttu-id="31c2a-147">Elle assigne la propriété <xref:System.Windows.FrameworkElement.FlowDirection%2A> en fonction de la valeur de la propriété <xref:System.Windows.Forms.CheckBox.CheckState%2A></span><span class="sxs-lookup"><span data-stu-id="31c2a-147">It assigns the <xref:System.Windows.FrameworkElement.FlowDirection%2A> property based on the value of the <xref:System.Windows.Forms.CheckBox.CheckState%2A> property</span></span>

## <a name="extending-a-default-property-mapping"></a><span data-ttu-id="31c2a-148">Extension d’un mappage de propriété par défaut</span><span class="sxs-lookup"><span data-stu-id="31c2a-148">Extending a Default Property Mapping</span></span>

<span data-ttu-id="31c2a-149">Vous pouvez utiliser un mappage de propriété par défaut et l’étendre avec votre propre mappage.</span><span class="sxs-lookup"><span data-stu-id="31c2a-149">You can use a default property mapping and also extend it with your own mapping.</span></span>

### <a name="to-extend-a-default-property-mapping"></a><span data-ttu-id="31c2a-150">Pour étendre un mappage de propriété par défaut</span><span class="sxs-lookup"><span data-stu-id="31c2a-150">To extend a default property mapping</span></span>

- <span data-ttu-id="31c2a-151">Copiez le code suivant dans la définition de la classe `Window1`.</span><span class="sxs-lookup"><span data-stu-id="31c2a-151">Copy the following code into the definition for the `Window1` class.</span></span>

     [!code-csharp[PropertyMappingWithWfhSample#15](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#15)]
     [!code-vb[PropertyMappingWithWfhSample#15](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#15)]

     <span data-ttu-id="31c2a-152">La méthode `ExtendBackgroundMapping` ajoute un traducteur de propriétés personnalisées au mappage de propriété de <xref:System.Windows.Controls.Control.Background%2A> existant.</span><span class="sxs-lookup"><span data-stu-id="31c2a-152">The `ExtendBackgroundMapping` method adds a custom property translator to the existing <xref:System.Windows.Controls.Control.Background%2A> property mapping.</span></span>

     <span data-ttu-id="31c2a-153">La méthode `OnBackgroundChange` assigne une image spécifique à la propriété <xref:System.Windows.Forms.Control.BackgroundImage%2A> du contrôle hébergé.</span><span class="sxs-lookup"><span data-stu-id="31c2a-153">The `OnBackgroundChange` method assigns a specific image to the hosted control's <xref:System.Windows.Forms.Control.BackgroundImage%2A> property.</span></span> <span data-ttu-id="31c2a-154">La méthode `OnBackgroundChange` est appelée après l’application du mappage de propriété par défaut.</span><span class="sxs-lookup"><span data-stu-id="31c2a-154">The `OnBackgroundChange` method is called after the default property mapping is applied.</span></span>

## <a name="initializing-your-property-mappings"></a><span data-ttu-id="31c2a-155">Initialisation de vos mappages de propriétés</span><span class="sxs-lookup"><span data-stu-id="31c2a-155">Initializing Your Property Mappings</span></span>

<span data-ttu-id="31c2a-156">Configurez vos mappages de propriétés en appelant les méthodes décrites précédemment dans le gestionnaire d’événements <xref:System.Windows.FrameworkElement.Loaded>.</span><span class="sxs-lookup"><span data-stu-id="31c2a-156">Set up your property mappings by calling the previously described methods in the <xref:System.Windows.FrameworkElement.Loaded> event handler.</span></span>

### <a name="to-initialize-your-property-mappings"></a><span data-ttu-id="31c2a-157">Pour initialiser vos mappages de propriétés</span><span class="sxs-lookup"><span data-stu-id="31c2a-157">To initialize your property mappings</span></span>

1. <span data-ttu-id="31c2a-158">Copiez le code suivant dans la définition de la classe `Window1`.</span><span class="sxs-lookup"><span data-stu-id="31c2a-158">Copy the following code into the definition for the `Window1` class.</span></span>

     [!code-csharp[PropertyMappingWithWfhSample#11](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#11)]
     [!code-vb[PropertyMappingWithWfhSample#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#11)]

     <span data-ttu-id="31c2a-159">La méthode `WindowLoaded` gère l’événement <xref:System.Windows.FrameworkElement.Loaded> et effectue l’initialisation suivante.</span><span class="sxs-lookup"><span data-stu-id="31c2a-159">The `WindowLoaded` method handles the <xref:System.Windows.FrameworkElement.Loaded> event and performs the following initialization.</span></span>

    - <span data-ttu-id="31c2a-160">Crée un contrôle de<xref:System.Windows.Forms.CheckBox> Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="31c2a-160">Creates a Windows Forms<xref:System.Windows.Forms.CheckBox> control.</span></span>

    - <span data-ttu-id="31c2a-161">Appelle les méthodes que vous avez définies précédemment dans la procédure pas à pas pour configurer les mappages de propriétés.</span><span class="sxs-lookup"><span data-stu-id="31c2a-161">Calls the methods you defined earlier in the walkthrough to set up the property mappings.</span></span>

    - <span data-ttu-id="31c2a-162">Assigne les valeurs initiales aux propriétés mappées.</span><span class="sxs-lookup"><span data-stu-id="31c2a-162">Assigns initial values to the mapped properties.</span></span>

2. <span data-ttu-id="31c2a-163">Appuyez sur **F5** pour générer et exécuter l’application.</span><span class="sxs-lookup"><span data-stu-id="31c2a-163">Press **F5** to build and run the application.</span></span> <span data-ttu-id="31c2a-164">Activez la case à cocher pour voir l’effet du mappage de <xref:System.Windows.FrameworkElement.FlowDirection%2A>.</span><span class="sxs-lookup"><span data-stu-id="31c2a-164">Click the check box to see the effect of the <xref:System.Windows.FrameworkElement.FlowDirection%2A> mapping.</span></span> <span data-ttu-id="31c2a-165">Quand vous cliquez sur la case à cocher, la disposition inverse son orientation de gauche à droite.</span><span class="sxs-lookup"><span data-stu-id="31c2a-165">When you click the check box, the layout reverses its left-right orientation.</span></span>

## <a name="see-also"></a><span data-ttu-id="31c2a-166">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="31c2a-166">See also</span></span>

- <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="31c2a-167">Mappage de propriétés Windows Forms et WPF</span><span class="sxs-lookup"><span data-stu-id="31c2a-167">Windows Forms and WPF Property Mapping</span></span>](windows-forms-and-wpf-property-mapping.md)
- [<span data-ttu-id="31c2a-168">Concevoir en XAML dans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="31c2a-168">Design XAML in Visual Studio</span></span>](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [<span data-ttu-id="31c2a-169">Procédure pas à pas : hébergement d’un contrôle Windows Forms dans WPF</span><span class="sxs-lookup"><span data-stu-id="31c2a-169">Walkthrough: Hosting a Windows Forms Control in WPF</span></span>](walkthrough-hosting-a-windows-forms-control-in-wpf.md)
