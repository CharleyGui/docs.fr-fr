---
title: "Procédure pas à pas : mappage de propriété à l'aide du contrôle ElementHost"
ms.date: 08/18/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- mapping properties [WPF]
- ElementHost control [WPF], mapping properties
ms.assetid: bccd6e0d-2272-4924-9107-ff8ed58b88aa
ms.openlocfilehash: 7ff4ff607ab70b55cda1e2c4736ff773d4907a22
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794115"
---
# <a name="walkthrough-mapping-properties-using-the-elementhost-control"></a><span data-ttu-id="eed69-102">Procédure pas à pas : mappage de propriété à l'aide du contrôle ElementHost</span><span class="sxs-lookup"><span data-stu-id="eed69-102">Walkthrough: Mapping Properties Using the ElementHost Control</span></span>

<span data-ttu-id="eed69-103">Cette procédure pas à pas vous montre comment utiliser la propriété <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A> pour mapper des propriétés Windows Forms à des propriétés correspondantes sur un élément [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] hébergé.</span><span class="sxs-lookup"><span data-stu-id="eed69-103">This walkthrough shows you how to use the <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A> property to map Windows Forms properties to corresponding properties on a hosted [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] element.</span></span>

<span data-ttu-id="eed69-104">Cette procédure pas à pas décrit notamment les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="eed69-104">Tasks illustrated in this walkthrough include:</span></span>

- <span data-ttu-id="eed69-105">Création du projet.</span><span class="sxs-lookup"><span data-stu-id="eed69-105">Creating the project.</span></span>

- <span data-ttu-id="eed69-106">Définition d’un nouveau mappage de propriété.</span><span class="sxs-lookup"><span data-stu-id="eed69-106">Defining a new property mapping.</span></span>

- <span data-ttu-id="eed69-107">Suppression d’un mappage de propriété par défaut.</span><span class="sxs-lookup"><span data-stu-id="eed69-107">Removing a default property mapping.</span></span>

- <span data-ttu-id="eed69-108">Extension d’un mappage de propriété par défaut.</span><span class="sxs-lookup"><span data-stu-id="eed69-108">Extending a default property mapping.</span></span>

<span data-ttu-id="eed69-109">Pour obtenir le code complet des tâches illustrées dans cette procédure pas à pas, consultez [mappage de propriétés à l’aide de l’exemple de contrôle ElementHost](https://go.microsoft.com/fwlink/?LinkID=160018).</span><span class="sxs-lookup"><span data-stu-id="eed69-109">For a complete code listing of the tasks illustrated in this walkthrough, see [Mapping Properties Using the ElementHost Control Sample](https://go.microsoft.com/fwlink/?LinkID=160018).</span></span>

<span data-ttu-id="eed69-110">Lorsque vous avez terminé, vous pouvez mapper les propriétés de Windows Forms aux propriétés de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] correspondantes sur un élément hébergé.</span><span class="sxs-lookup"><span data-stu-id="eed69-110">When you are finished, you will be able to map Windows Forms properties to corresponding [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] properties on a hosted element.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="eed69-111">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="eed69-111">Prerequisites</span></span>

<span data-ttu-id="eed69-112">Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :</span><span class="sxs-lookup"><span data-stu-id="eed69-112">You need the following components to complete this walkthrough:</span></span>

- <span data-ttu-id="eed69-113">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="eed69-113">Visual Studio 2017</span></span>

## <a name="creating-the-project"></a><span data-ttu-id="eed69-114">Création du projet</span><span class="sxs-lookup"><span data-stu-id="eed69-114">Creating the Project</span></span>

### <a name="to-create-the-project"></a><span data-ttu-id="eed69-115">Pour créer le projet</span><span class="sxs-lookup"><span data-stu-id="eed69-115">To create the project</span></span>

1. <span data-ttu-id="eed69-116">Créez un projet d' **application Windows Forms** nommé `PropertyMappingWithElementHost`.</span><span class="sxs-lookup"><span data-stu-id="eed69-116">Create a **Windows Forms App** project named `PropertyMappingWithElementHost`.</span></span>

2. <span data-ttu-id="eed69-117">Dans **Explorateur de solutions**, ajoutez des références aux assemblys de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] suivants.</span><span class="sxs-lookup"><span data-stu-id="eed69-117">In **Solution Explorer**, add references to the following [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] assemblies.</span></span>

    - <span data-ttu-id="eed69-118">PresentationCore</span><span class="sxs-lookup"><span data-stu-id="eed69-118">PresentationCore</span></span>

    - <span data-ttu-id="eed69-119">PresentationFramework</span><span class="sxs-lookup"><span data-stu-id="eed69-119">PresentationFramework</span></span>

    - <span data-ttu-id="eed69-120">WindowsBase</span><span class="sxs-lookup"><span data-stu-id="eed69-120">WindowsBase</span></span>

    - <span data-ttu-id="eed69-121">WindowsFormsIntegration</span><span class="sxs-lookup"><span data-stu-id="eed69-121">WindowsFormsIntegration</span></span>

3. <span data-ttu-id="eed69-122">Copiez le code suivant en haut du fichier de code `Form1`.</span><span class="sxs-lookup"><span data-stu-id="eed69-122">Copy the following code into the top of the `Form1` code file.</span></span>

     [!code-csharp[PropertyMappingWithElementHost#10](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#10)]
     [!code-vb[PropertyMappingWithElementHost#10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#10)]

4. <span data-ttu-id="eed69-123">Ouvrez `Form1` dans le Concepteur Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="eed69-123">Open `Form1` in the Windows Forms Designer.</span></span> <span data-ttu-id="eed69-124">Double-cliquez sur le formulaire pour ajouter un gestionnaire d’événements pour l’événement <xref:System.Windows.Forms.Form.Load>.</span><span class="sxs-lookup"><span data-stu-id="eed69-124">Double-click the form to add an event handler for the <xref:System.Windows.Forms.Form.Load> event.</span></span>

5. <span data-ttu-id="eed69-125">Revenez à la Concepteur Windows Forms et ajoutez un gestionnaire d’événements pour l’événement <xref:System.Windows.Forms.Control.Resize> du formulaire.</span><span class="sxs-lookup"><span data-stu-id="eed69-125">Return to the Windows Forms Designer and add an event handler for the form's <xref:System.Windows.Forms.Control.Resize> event.</span></span> <span data-ttu-id="eed69-126">Pour plus d’informations, consultez [Comment : créer des gestionnaires d’événements à l’aide du concepteur](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/zwwsdtbk(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="eed69-126">For more information, see [How to: Create Event Handlers Using the Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/zwwsdtbk(v=vs.100)).</span></span>

6. <span data-ttu-id="eed69-127">Déclarez un champ <xref:System.Windows.Forms.Integration.ElementHost> dans la classe `Form1`.</span><span class="sxs-lookup"><span data-stu-id="eed69-127">Declare an <xref:System.Windows.Forms.Integration.ElementHost> field in the `Form1` class.</span></span>

     [!code-csharp[PropertyMappingWithElementHost#16](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#16)]
     [!code-vb[PropertyMappingWithElementHost#16](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#16)]

## <a name="defining-new-property-mappings"></a><span data-ttu-id="eed69-128">Définition de nouveaux mappages de propriétés</span><span class="sxs-lookup"><span data-stu-id="eed69-128">Defining New Property Mappings</span></span>

<span data-ttu-id="eed69-129">Le contrôle <xref:System.Windows.Forms.Integration.ElementHost> fournit plusieurs mappages de propriété par défaut.</span><span class="sxs-lookup"><span data-stu-id="eed69-129">The <xref:System.Windows.Forms.Integration.ElementHost> control provides several default property mappings.</span></span> <span data-ttu-id="eed69-130">Vous ajoutez un nouveau mappage de propriété en appelant la méthode <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> sur le <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A>du contrôle <xref:System.Windows.Forms.Integration.ElementHost>.</span><span class="sxs-lookup"><span data-stu-id="eed69-130">You add a new property mapping by calling the <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> method on the <xref:System.Windows.Forms.Integration.ElementHost> control's <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A>.</span></span>

### <a name="to-define-new-property-mappings"></a><span data-ttu-id="eed69-131">Pour définir de nouveaux mappages de propriétés</span><span class="sxs-lookup"><span data-stu-id="eed69-131">To define new property mappings</span></span>

1. <span data-ttu-id="eed69-132">Copiez le code suivant dans la définition de la classe `Form1`.</span><span class="sxs-lookup"><span data-stu-id="eed69-132">Copy the following code into the definition for the `Form1` class.</span></span>

     [!code-csharp[PropertyMappingWithElementHost#12](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#12)]
     [!code-vb[PropertyMappingWithElementHost#12](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#12)]

     <span data-ttu-id="eed69-133">La méthode `AddMarginMapping` ajoute un nouveau mappage pour la propriété <xref:System.Windows.Forms.Control.Margin%2A>.</span><span class="sxs-lookup"><span data-stu-id="eed69-133">The `AddMarginMapping` method adds a new mapping for the <xref:System.Windows.Forms.Control.Margin%2A> property.</span></span>

     <span data-ttu-id="eed69-134">La méthode `OnMarginChange` convertit la propriété <xref:System.Windows.Forms.Control.Margin%2A> en propriété <xref:System.Windows.FrameworkElement.Margin%2A> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="eed69-134">The `OnMarginChange` method translates the <xref:System.Windows.Forms.Control.Margin%2A> property to the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.FrameworkElement.Margin%2A> property.</span></span>

2. <span data-ttu-id="eed69-135">Copiez le code suivant dans la définition de la classe `Form1`.</span><span class="sxs-lookup"><span data-stu-id="eed69-135">Copy the following code into the definition for the `Form1` class.</span></span>

     [!code-csharp[PropertyMappingWithElementHost#14](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#14)]
     [!code-vb[PropertyMappingWithElementHost#14](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#14)]

     <span data-ttu-id="eed69-136">La méthode `AddRegionMapping` ajoute un nouveau mappage pour la propriété <xref:System.Windows.Forms.Control.Region%2A>.</span><span class="sxs-lookup"><span data-stu-id="eed69-136">The `AddRegionMapping` method adds a new mapping for the <xref:System.Windows.Forms.Control.Region%2A> property.</span></span>

     <span data-ttu-id="eed69-137">La méthode `OnRegionChange` convertit la propriété <xref:System.Windows.Forms.Control.Region%2A> en propriété <xref:System.Windows.UIElement.Clip%2A> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="eed69-137">The `OnRegionChange` method translates the <xref:System.Windows.Forms.Control.Region%2A> property to the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.UIElement.Clip%2A> property.</span></span>

     <span data-ttu-id="eed69-138">La méthode `Form1_Resize` gère l’événement <xref:System.Windows.Forms.Control.Resize> du formulaire et dimensionne la zone de découpage pour l’adapter à l’élément hébergé.</span><span class="sxs-lookup"><span data-stu-id="eed69-138">The `Form1_Resize` method handles the form's <xref:System.Windows.Forms.Control.Resize> event and sizes the clipping region to fit the hosted element.</span></span>

## <a name="removing-a-default-property-mapping"></a><span data-ttu-id="eed69-139">Suppression d’un mappage de propriété par défaut</span><span class="sxs-lookup"><span data-stu-id="eed69-139">Removing a Default Property Mapping</span></span>

<span data-ttu-id="eed69-140">Supprimez un mappage de propriété par défaut en appelant la méthode <xref:System.Windows.Forms.Integration.PropertyMap.Remove%2A> sur le <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A>du contrôle <xref:System.Windows.Forms.Integration.ElementHost>.</span><span class="sxs-lookup"><span data-stu-id="eed69-140">Remove a default property mapping by calling the <xref:System.Windows.Forms.Integration.PropertyMap.Remove%2A> method on the <xref:System.Windows.Forms.Integration.ElementHost> control's <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A>.</span></span>

### <a name="to-remove-a-default-property-mapping"></a><span data-ttu-id="eed69-141">Pour supprimer un mappage de propriété par défaut</span><span class="sxs-lookup"><span data-stu-id="eed69-141">To remove a default property mapping</span></span>

- <span data-ttu-id="eed69-142">Copiez le code suivant dans la définition de la classe `Form1`.</span><span class="sxs-lookup"><span data-stu-id="eed69-142">Copy the following code into the definition for the `Form1` class.</span></span>

     [!code-csharp[PropertyMappingWithElementHost#13](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#13)]
     [!code-vb[PropertyMappingWithElementHost#13](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#13)]

     <span data-ttu-id="eed69-143">La méthode `RemoveCursorMapping` supprime le mappage par défaut pour la propriété <xref:System.Windows.Forms.Control.Cursor%2A>.</span><span class="sxs-lookup"><span data-stu-id="eed69-143">The `RemoveCursorMapping` method deletes the default mapping for the <xref:System.Windows.Forms.Control.Cursor%2A> property.</span></span>

## <a name="extending-a-default-property-mapping"></a><span data-ttu-id="eed69-144">Extension d’un mappage de propriété par défaut</span><span class="sxs-lookup"><span data-stu-id="eed69-144">Extending a Default Property Mapping</span></span>

<span data-ttu-id="eed69-145">Vous pouvez utiliser un mappage de propriété par défaut et l’étendre avec votre propre mappage.</span><span class="sxs-lookup"><span data-stu-id="eed69-145">You can use a default property mapping and also extend it with your own mapping.</span></span>

### <a name="to-extend-a-default-property-mapping"></a><span data-ttu-id="eed69-146">Pour étendre un mappage de propriété par défaut</span><span class="sxs-lookup"><span data-stu-id="eed69-146">To extend a default property mapping</span></span>

- <span data-ttu-id="eed69-147">Copiez le code suivant dans la définition de la classe `Form1`.</span><span class="sxs-lookup"><span data-stu-id="eed69-147">Copy the following code into the definition for the `Form1` class.</span></span>

     [!code-csharp[PropertyMappingWithElementHost#15](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#15)]
     [!code-vb[PropertyMappingWithElementHost#15](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#15)]

     <span data-ttu-id="eed69-148">La méthode `ExtendBackColorMapping` ajoute un traducteur de propriétés personnalisées au mappage de propriété de <xref:System.Windows.Forms.Control.BackColor%2A> existant.</span><span class="sxs-lookup"><span data-stu-id="eed69-148">The `ExtendBackColorMapping` method adds a custom property translator to the existing <xref:System.Windows.Forms.Control.BackColor%2A> property mapping.</span></span>

     <span data-ttu-id="eed69-149">La méthode `OnBackColorChange` assigne une image spécifique à la propriété <xref:System.Windows.Controls.Control.Background%2A> du contrôle hébergé.</span><span class="sxs-lookup"><span data-stu-id="eed69-149">The `OnBackColorChange` method assigns a specific image to the hosted control's <xref:System.Windows.Controls.Control.Background%2A> property.</span></span> <span data-ttu-id="eed69-150">La méthode `OnBackColorChange` est appelée après l’application du mappage de propriété par défaut.</span><span class="sxs-lookup"><span data-stu-id="eed69-150">The `OnBackColorChange` method is called after the default property mapping is applied.</span></span>

## <a name="initialize-your-property-mappings"></a><span data-ttu-id="eed69-151">Initialiser vos mappages de propriétés</span><span class="sxs-lookup"><span data-stu-id="eed69-151">Initialize your property mappings</span></span>

1. <span data-ttu-id="eed69-152">Copiez le code suivant dans la définition de la classe `Form1`.</span><span class="sxs-lookup"><span data-stu-id="eed69-152">Copy the following code into the definition for the `Form1` class.</span></span>

     [!code-csharp[PropertyMappingWithElementHost#11](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#11)]
     [!code-vb[PropertyMappingWithElementHost#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#11)]

     <span data-ttu-id="eed69-153">La méthode `Form1_Load` gère l’événement <xref:System.Windows.Forms.Form.Load> et effectue l’initialisation suivante.</span><span class="sxs-lookup"><span data-stu-id="eed69-153">The `Form1_Load` method handles the <xref:System.Windows.Forms.Form.Load> event and performs the following initialization.</span></span>

    - <span data-ttu-id="eed69-154">Crée un élément [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="eed69-154">Creates a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Button> element.</span></span>

    - <span data-ttu-id="eed69-155">Appelle les méthodes que vous avez définies précédemment dans la procédure pas à pas pour configurer les mappages de propriétés.</span><span class="sxs-lookup"><span data-stu-id="eed69-155">Calls the methods you defined earlier in the walkthrough to set up the property mappings.</span></span>

    - <span data-ttu-id="eed69-156">Assigne les valeurs initiales aux propriétés mappées.</span><span class="sxs-lookup"><span data-stu-id="eed69-156">Assigns initial values to the mapped properties.</span></span>

2. <span data-ttu-id="eed69-157">Appuyez sur F5 pour générer et exécuter l'application.</span><span class="sxs-lookup"><span data-stu-id="eed69-157">Press F5 to build and run the application.</span></span>

## <a name="see-also"></a><span data-ttu-id="eed69-158">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="eed69-158">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="eed69-159">Mappage de propriétés Windows Forms et WPF</span><span class="sxs-lookup"><span data-stu-id="eed69-159">Windows Forms and WPF Property Mapping</span></span>](windows-forms-and-wpf-property-mapping.md)
- [<span data-ttu-id="eed69-160">Concevoir en XAML dans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="eed69-160">Design XAML in Visual Studio</span></span>](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [<span data-ttu-id="eed69-161">Procédure pas à pas : Hébergement d'un contrôle composite WPF dans Windows Forms</span><span class="sxs-lookup"><span data-stu-id="eed69-161">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
