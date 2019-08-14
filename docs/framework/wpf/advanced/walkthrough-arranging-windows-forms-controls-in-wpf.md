---
title: 'Procédure pas à pas : organisation des contrôles Windows Forms dans WPF'
ms.date: 04/03/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hybrid applications [WPF interoperability]
- arranging controls [WPF]
ms.assetid: a1db8049-15c7-45d6-ae3d-36a6735cb848
ms.openlocfilehash: fa0181e95a03324c4cfa9395ae57439c260d1c23
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68972305"
---
# <a name="walkthrough-arranging-windows-forms-controls-in-wpf"></a><span data-ttu-id="07f12-102">Procédure pas à pas : organisation des contrôles Windows Forms dans WPF</span><span class="sxs-lookup"><span data-stu-id="07f12-102">Walkthrough: Arranging Windows Forms Controls in WPF</span></span>

<span data-ttu-id="07f12-103">Cette procédure pas à pas vous montre [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] comment utiliser les fonctionnalités [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] de disposition pour organiser les contrôles dans une application hybride.</span><span class="sxs-lookup"><span data-stu-id="07f12-103">This walkthrough shows you how to use [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layout features to arrange [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls in a hybrid application.</span></span>

<span data-ttu-id="07f12-104">Cette procédure pas à pas décrit notamment les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="07f12-104">Tasks illustrated in this walkthrough include:</span></span>

- <span data-ttu-id="07f12-105">Création du projet</span><span class="sxs-lookup"><span data-stu-id="07f12-105">Creating the project.</span></span>

- <span data-ttu-id="07f12-106">Utilisation des paramètres de disposition par défaut</span><span class="sxs-lookup"><span data-stu-id="07f12-106">Using default layout settings.</span></span>

- <span data-ttu-id="07f12-107">Dimensionnement en fonction du contenu</span><span class="sxs-lookup"><span data-stu-id="07f12-107">Sizing to content.</span></span>

- <span data-ttu-id="07f12-108">Utilisation du positionnement absolu</span><span class="sxs-lookup"><span data-stu-id="07f12-108">Using absolute positioning.</span></span>

- <span data-ttu-id="07f12-109">Spécification explicite de la taille</span><span class="sxs-lookup"><span data-stu-id="07f12-109">Specifying size explicitly.</span></span>

- <span data-ttu-id="07f12-110">Définition des propriétés de disposition</span><span class="sxs-lookup"><span data-stu-id="07f12-110">Setting layout properties.</span></span>

- <span data-ttu-id="07f12-111">Présentation des limitations dans l’ordre de plan</span><span class="sxs-lookup"><span data-stu-id="07f12-111">Understanding z-order limitations.</span></span>

- <span data-ttu-id="07f12-112">Ancrage</span><span class="sxs-lookup"><span data-stu-id="07f12-112">Docking.</span></span>

- <span data-ttu-id="07f12-113">Définition de la visibilité</span><span class="sxs-lookup"><span data-stu-id="07f12-113">Setting visibility.</span></span>

- <span data-ttu-id="07f12-114">Hébergement d’un contrôle qui ne s’étire pas</span><span class="sxs-lookup"><span data-stu-id="07f12-114">Hosting a control that does not stretch.</span></span>

- <span data-ttu-id="07f12-115">Mise à l’échelle</span><span class="sxs-lookup"><span data-stu-id="07f12-115">Scaling.</span></span>

- <span data-ttu-id="07f12-116">Rotation</span><span class="sxs-lookup"><span data-stu-id="07f12-116">Rotating.</span></span>

- <span data-ttu-id="07f12-117">Définition d’une marge intérieure et de marges</span><span class="sxs-lookup"><span data-stu-id="07f12-117">Setting padding and margins.</span></span>

- <span data-ttu-id="07f12-118">Utilisation de conteneurs de présentation dynamiques</span><span class="sxs-lookup"><span data-stu-id="07f12-118">Using dynamic layout containers.</span></span>

<span data-ttu-id="07f12-119">Pour obtenir le code complet des tâches illustrées dans cette procédure pas à pas, consultez réorganisation des [contrôles de Windows Forms dans l’exemple WPF](https://go.microsoft.com/fwlink/?LinkID=159971).</span><span class="sxs-lookup"><span data-stu-id="07f12-119">For a complete code listing of the tasks illustrated in this walkthrough, see [Arranging Windows Forms Controls in WPF Sample](https://go.microsoft.com/fwlink/?LinkID=159971).</span></span>

<span data-ttu-id="07f12-120">Lorsque vous aurez terminé, vous aurez une compréhension des [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] fonctionnalités de disposition dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]les applications.</span><span class="sxs-lookup"><span data-stu-id="07f12-120">When you are finished, you will have an understanding of [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] layout features in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-based applications.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="07f12-121">Prérequis</span><span class="sxs-lookup"><span data-stu-id="07f12-121">Prerequisites</span></span>

<span data-ttu-id="07f12-122">Cette procédure pas à pas nécessite Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="07f12-122">You need Visual Studio to complete this walkthrough.</span></span>

## <a name="creating-the-project"></a><span data-ttu-id="07f12-123">Création du projet</span><span class="sxs-lookup"><span data-stu-id="07f12-123">Creating the Project</span></span>

### <a name="to-create-and-set-up-the-project"></a><span data-ttu-id="07f12-124">Pour créer et configurer le projet</span><span class="sxs-lookup"><span data-stu-id="07f12-124">To create and set up the project</span></span>

1. <span data-ttu-id="07f12-125">Créez un projet d’application WPF `WpfLayoutHostingWf`nommé.</span><span class="sxs-lookup"><span data-stu-id="07f12-125">Create a WPF Application project named `WpfLayoutHostingWf`.</span></span>

2. <span data-ttu-id="07f12-126">Dans l’Explorateur de solutions, ajoutez des références aux assemblys suivants.</span><span class="sxs-lookup"><span data-stu-id="07f12-126">In Solution Explorer, add references to the following assemblies.</span></span>

    - <span data-ttu-id="07f12-127">WindowsFormsIntegration</span><span class="sxs-lookup"><span data-stu-id="07f12-127">WindowsFormsIntegration</span></span>

    - <span data-ttu-id="07f12-128">System.Windows.Forms</span><span class="sxs-lookup"><span data-stu-id="07f12-128">System.Windows.Forms</span></span>

    - <span data-ttu-id="07f12-129">System.Drawing</span><span class="sxs-lookup"><span data-stu-id="07f12-129">System.Drawing</span></span>

3. <span data-ttu-id="07f12-130">Double-cliquez sur MainWindow.xaml pour l’ouvrir dans la vue XAML.</span><span class="sxs-lookup"><span data-stu-id="07f12-130">Double-click MainWindow.xaml to open it in XAML view.</span></span>

4. <span data-ttu-id="07f12-131">Dans l' <xref:System.Windows.Window> élément, ajoutez le mappage [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] d’espace de noms suivant.</span><span class="sxs-lookup"><span data-stu-id="07f12-131">In the <xref:System.Windows.Window> element, add the following [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] namespace mapping.</span></span>

    ```xaml
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"
    ```

5. <span data-ttu-id="07f12-132">Dans l' <xref:System.Windows.Controls.Grid> élément, affectez à `true` la propriété la <xref:System.Windows.Controls.Grid.ShowGridLines%2A> valeur et définissez cinq lignes et trois colonnes.</span><span class="sxs-lookup"><span data-stu-id="07f12-132">In the <xref:System.Windows.Controls.Grid> element set the <xref:System.Windows.Controls.Grid.ShowGridLines%2A> property to `true` and define five rows and three columns.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#2](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#2)]

## <a name="using-default-layout-settings"></a><span data-ttu-id="07f12-133">Utilisation des paramètres de disposition par défaut</span><span class="sxs-lookup"><span data-stu-id="07f12-133">Using Default Layout Settings</span></span>

<span data-ttu-id="07f12-134">Par défaut, l' <xref:System.Windows.Forms.Integration.WindowsFormsHost> élément gère la disposition du contrôle hébergé [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="07f12-134">By default, the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element handles the layout for the hosted [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control.</span></span>

### <a name="to-use-default-layout-settings"></a><span data-ttu-id="07f12-135">Pour utiliser les paramètres de disposition par défaut</span><span class="sxs-lookup"><span data-stu-id="07f12-135">To use default layout settings</span></span>

1. <span data-ttu-id="07f12-136">Copiez le code XAML suivant <xref:System.Windows.Controls.Grid> dans l’élément.</span><span class="sxs-lookup"><span data-stu-id="07f12-136">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#3](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#3)]

2. <span data-ttu-id="07f12-137">Appuyez sur F5 pour générer et exécuter l'application.</span><span class="sxs-lookup"><span data-stu-id="07f12-137">Press F5 to build and run the application.</span></span> <span data-ttu-id="07f12-138"><xref:System.Windows.Controls.Canvas>Le [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] contrôles'<xref:System.Windows.Forms.Button?displayProperty=nameWithType> affiche dans le.</span><span class="sxs-lookup"><span data-stu-id="07f12-138">The [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<xref:System.Windows.Forms.Button?displayProperty=nameWithType> control appears in the <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="07f12-139">Le contrôle hébergé est dimensionné en fonction de son contenu, et <xref:System.Windows.Forms.Integration.WindowsFormsHost> l’élément est dimensionné pour s’adapter au contrôle hébergé.</span><span class="sxs-lookup"><span data-stu-id="07f12-139">The hosted control is sized based on its content, and the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is sized to accommodate the hosted control.</span></span>

## <a name="sizing-to-content"></a><span data-ttu-id="07f12-140">Dimensionnement en fonction du contenu</span><span class="sxs-lookup"><span data-stu-id="07f12-140">Sizing to Content</span></span>

<span data-ttu-id="07f12-141">L' <xref:System.Windows.Forms.Integration.WindowsFormsHost> élément garantit que le contrôle hébergé est dimensionné pour afficher correctement son contenu.</span><span class="sxs-lookup"><span data-stu-id="07f12-141">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element ensures that the hosted control is sized to display its content properly.</span></span>

### <a name="to-size-to-content"></a><span data-ttu-id="07f12-142">Pour dimensionner en fonction du contenu</span><span class="sxs-lookup"><span data-stu-id="07f12-142">To size to content</span></span>

1. <span data-ttu-id="07f12-143">Copiez le code XAML suivant <xref:System.Windows.Controls.Grid> dans l’élément.</span><span class="sxs-lookup"><span data-stu-id="07f12-143">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#4](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#4)]

2. <span data-ttu-id="07f12-144">Appuyez sur F5 pour générer et exécuter l'application.</span><span class="sxs-lookup"><span data-stu-id="07f12-144">Press F5 to build and run the application.</span></span> <span data-ttu-id="07f12-145">Les deux contrôles de bouton sont dimensionnés pour afficher la chaîne de texte la plus longue et la taille de <xref:System.Windows.Forms.Integration.WindowsFormsHost> police supérieure correctement, et les éléments sont redimensionnés pour s’adapter aux contrôles hébergés.</span><span class="sxs-lookup"><span data-stu-id="07f12-145">The two new button controls are sized to display the longer text string and larger font size properly, and the <xref:System.Windows.Forms.Integration.WindowsFormsHost> elements are resized to accommodate the hosted controls.</span></span>

## <a name="using-absolute-positioning"></a><span data-ttu-id="07f12-146">Utilisation du positionnement absolu</span><span class="sxs-lookup"><span data-stu-id="07f12-146">Using Absolute Positioning</span></span>

<span data-ttu-id="07f12-147">Vous pouvez utiliser le positionnement absolu pour placer <xref:System.Windows.Forms.Integration.WindowsFormsHost> l’élément n’importe où dans l’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="07f12-147">You can use absolute positioning to place the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element anywhere in the user interface (UI).</span></span>

### <a name="to-use-absolute-positioning"></a><span data-ttu-id="07f12-148">Pour utiliser le positionnement absolu</span><span class="sxs-lookup"><span data-stu-id="07f12-148">To use absolute positioning</span></span>

1. <span data-ttu-id="07f12-149">Copiez le code XAML suivant <xref:System.Windows.Controls.Grid> dans l’élément.</span><span class="sxs-lookup"><span data-stu-id="07f12-149">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#5](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#5)]

2. <span data-ttu-id="07f12-150">Appuyez sur F5 pour générer et exécuter l'application.</span><span class="sxs-lookup"><span data-stu-id="07f12-150">Press F5 to build and run the application.</span></span> <span data-ttu-id="07f12-151">L' <xref:System.Windows.Forms.Integration.WindowsFormsHost> élément est placé à 20 pixels du bord supérieur de la cellule de la grille et à 20 pixels à partir de la gauche.</span><span class="sxs-lookup"><span data-stu-id="07f12-151">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is placed 20 pixels from the top side of the grid cell and 20 pixels from the left.</span></span>

## <a name="specifying-size-explicitly"></a><span data-ttu-id="07f12-152">Spécification explicite de la taille</span><span class="sxs-lookup"><span data-stu-id="07f12-152">Specifying Size Explicitly</span></span>

<span data-ttu-id="07f12-153">Vous pouvez spécifier la taille de l' <xref:System.Windows.Forms.Integration.WindowsFormsHost> élément <xref:System.Windows.FrameworkElement.Width%2A> à l’aide <xref:System.Windows.FrameworkElement.Height%2A> des propriétés et.</span><span class="sxs-lookup"><span data-stu-id="07f12-153">You can specify the size of the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element using the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties.</span></span>

### <a name="to-specify-size-explicitly"></a><span data-ttu-id="07f12-154">Pour spécifier explicitement la taille</span><span class="sxs-lookup"><span data-stu-id="07f12-154">To specify size explicitly</span></span>

1. <span data-ttu-id="07f12-155">Copiez le code XAML suivant <xref:System.Windows.Controls.Grid> dans l’élément.</span><span class="sxs-lookup"><span data-stu-id="07f12-155">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#6](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#6)]

2. <span data-ttu-id="07f12-156">Appuyez sur F5 pour générer et exécuter l'application.</span><span class="sxs-lookup"><span data-stu-id="07f12-156">Press F5 to build and run the application.</span></span> <span data-ttu-id="07f12-157">L' <xref:System.Windows.Forms.Integration.WindowsFormsHost> élément est défini sur une taille de 50 pixels de large par 70 pixels de haut, ce qui est plus petit que les paramètres de disposition par défaut.</span><span class="sxs-lookup"><span data-stu-id="07f12-157">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is set to a size of 50 pixels wide by 70 pixels high, which is smaller than the default layout settings.</span></span> <span data-ttu-id="07f12-158">Le contenu du [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] contrôle est réorganisé en conséquence.</span><span class="sxs-lookup"><span data-stu-id="07f12-158">The content of the [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control is rearranged accordingly.</span></span>

## <a name="setting-layout-properties"></a><span data-ttu-id="07f12-159">Définition des propriétés de disposition</span><span class="sxs-lookup"><span data-stu-id="07f12-159">Setting Layout Properties</span></span>

<span data-ttu-id="07f12-160">Définissez toujours les propriétés relatives à la disposition sur le contrôle hébergé à l’aide des <xref:System.Windows.Forms.Integration.WindowsFormsHost> propriétés de l’élément.</span><span class="sxs-lookup"><span data-stu-id="07f12-160">Always set layout-related properties on the hosted control by using the properties of the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span> <span data-ttu-id="07f12-161">Si vous définissez les propriétés de disposition directement sur le contrôle hébergé, vous obtiendrez des résultats inattendus.</span><span class="sxs-lookup"><span data-stu-id="07f12-161">Setting layout properties directly on the hosted control will yield unintended results.</span></span>

 <span data-ttu-id="07f12-162">La définition des propriétés relatives à la disposition sur le [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] contrôle hébergé dans n’a aucun effet.</span><span class="sxs-lookup"><span data-stu-id="07f12-162">Setting layout-related properties on the hosted control in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] has no effect.</span></span>

### <a name="to-see-the-effects-of-setting-properties-on-the-hosted-control"></a><span data-ttu-id="07f12-163">Pour afficher les effets de la définition des propriétés sur le contrôle hébergé</span><span class="sxs-lookup"><span data-stu-id="07f12-163">To see the effects of setting properties on the hosted control</span></span>

1. <span data-ttu-id="07f12-164">Copiez le code XAML suivant <xref:System.Windows.Controls.Grid> dans l’élément.</span><span class="sxs-lookup"><span data-stu-id="07f12-164">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#7](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#7)]

2. <span data-ttu-id="07f12-165">Dans l’Explorateur de solutions, double-cliquez sur MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="07f12-165">In Solution Explorer, double-click MainWindow.xaml.</span></span> <span data-ttu-id="07f12-166">vb ou MainWindow.xaml.cs pour l’ouvrir dans l’éditeur de code.</span><span class="sxs-lookup"><span data-stu-id="07f12-166">vb or MainWindow.xaml.cs to open it in the Code Editor.</span></span>

3. <span data-ttu-id="07f12-167">Copiez le code suivant dans `MainWindow` la définition de classe.</span><span class="sxs-lookup"><span data-stu-id="07f12-167">Copy the following code into the `MainWindow` class definition.</span></span>

     [!code-csharp[WpfLayoutHostingWfWithXaml#101](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#101)]
     [!code-vb[WpfLayoutHostingWfWithXaml#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#101)]

4. <span data-ttu-id="07f12-168">Appuyez sur F5 pour générer et exécuter l'application.</span><span class="sxs-lookup"><span data-stu-id="07f12-168">Press F5 to build and run the application.</span></span>

5. <span data-ttu-id="07f12-169">Cliquez sur le bouton **cliquez sur moi** .</span><span class="sxs-lookup"><span data-stu-id="07f12-169">Click the **Click me** button.</span></span> <span data-ttu-id="07f12-170">Le `button1_Click` gestionnaire d’événements définit <xref:System.Windows.Forms.Control.Top%2A> les <xref:System.Windows.Forms.Control.Left%2A> propriétés et sur le contrôle hébergé.</span><span class="sxs-lookup"><span data-stu-id="07f12-170">The `button1_Click` event handler sets the <xref:System.Windows.Forms.Control.Top%2A> and <xref:System.Windows.Forms.Control.Left%2A> properties on the hosted control.</span></span> <span data-ttu-id="07f12-171">Le contrôle hébergé est alors repositionné dans l' <xref:System.Windows.Forms.Integration.WindowsFormsHost> élément.</span><span class="sxs-lookup"><span data-stu-id="07f12-171">This causes the hosted control to be repositioned within the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span> <span data-ttu-id="07f12-172">L’hôte conserve la même zone d’écran, mais le contrôle hébergé est découpé.</span><span class="sxs-lookup"><span data-stu-id="07f12-172">The host maintains the same screen area, but the hosted control is clipped.</span></span> <span data-ttu-id="07f12-173">Au lieu de cela, le contrôle hébergé doit <xref:System.Windows.Forms.Integration.WindowsFormsHost> toujours remplir l’élément.</span><span class="sxs-lookup"><span data-stu-id="07f12-173">Instead, the hosted control should always fill the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span>

## <a name="understanding-z-order-limitations"></a><span data-ttu-id="07f12-174">Présentation des limitations dans l’ordre de plan</span><span class="sxs-lookup"><span data-stu-id="07f12-174">Understanding Z-Order Limitations</span></span>

<span data-ttu-id="07f12-175">Les <xref:System.Windows.Forms.Integration.WindowsFormsHost> éléments visibles sont toujours dessinés par-dessus d’autres éléments WPF, et ils ne sont pas affectés par l’ordre de plan.</span><span class="sxs-lookup"><span data-stu-id="07f12-175">Visible <xref:System.Windows.Forms.Integration.WindowsFormsHost> elements are always drawn on top of other WPF elements, and they are unaffected by z-order.</span></span> <span data-ttu-id="07f12-176">Pour voir ce comportement de l’ordre de plan, procédez comme suit:</span><span class="sxs-lookup"><span data-stu-id="07f12-176">To see this z-order behavior, do the following:</span></span>

1. <span data-ttu-id="07f12-177">Copiez le code XAML suivant <xref:System.Windows.Controls.Grid> dans l’élément.</span><span class="sxs-lookup"><span data-stu-id="07f12-177">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#8](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#8)]

2. <span data-ttu-id="07f12-178">Appuyez sur F5 pour générer et exécuter l'application.</span><span class="sxs-lookup"><span data-stu-id="07f12-178">Press F5 to build and run the application.</span></span> <span data-ttu-id="07f12-179">L' <xref:System.Windows.Forms.Integration.WindowsFormsHost> élément est peint sur l’élément label.</span><span class="sxs-lookup"><span data-stu-id="07f12-179">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is painted over the label element.</span></span>

## <a name="docking"></a><span data-ttu-id="07f12-180">Ancrage</span><span class="sxs-lookup"><span data-stu-id="07f12-180">Docking</span></span>

<span data-ttu-id="07f12-181"><xref:System.Windows.Forms.Integration.WindowsFormsHost>l’élément [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] prend en charge l’ancrage.</span><span class="sxs-lookup"><span data-stu-id="07f12-181"><xref:System.Windows.Forms.Integration.WindowsFormsHost> element supports [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] docking.</span></span> <span data-ttu-id="07f12-182">Définissez la <xref:System.Windows.Controls.DockPanel.Dock%2A> propriété jointe pour ancrer le contrôle hébergé <xref:System.Windows.Controls.DockPanel> dans un élément.</span><span class="sxs-lookup"><span data-stu-id="07f12-182">Set the <xref:System.Windows.Controls.DockPanel.Dock%2A> attached property to dock the hosted control in a <xref:System.Windows.Controls.DockPanel> element.</span></span>

### <a name="to-dock-a-hosted-control"></a><span data-ttu-id="07f12-183">Pour ancrer un contrôle hébergé</span><span class="sxs-lookup"><span data-stu-id="07f12-183">To dock a hosted control</span></span>

1. <span data-ttu-id="07f12-184">Copiez le code XAML suivant <xref:System.Windows.Controls.Grid> dans l’élément.</span><span class="sxs-lookup"><span data-stu-id="07f12-184">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#9](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#9)]

2. <span data-ttu-id="07f12-185">Appuyez sur F5 pour générer et exécuter l'application.</span><span class="sxs-lookup"><span data-stu-id="07f12-185">Press F5 to build and run the application.</span></span> <span data-ttu-id="07f12-186">L' <xref:System.Windows.Forms.Integration.WindowsFormsHost> élément est ancré à droite de l' <xref:System.Windows.Controls.DockPanel> élément.</span><span class="sxs-lookup"><span data-stu-id="07f12-186">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is docked to the right side of the <xref:System.Windows.Controls.DockPanel> element.</span></span>

## <a name="setting-visibility"></a><span data-ttu-id="07f12-187">Définition de la visibilité</span><span class="sxs-lookup"><span data-stu-id="07f12-187">Setting Visibility</span></span>

<span data-ttu-id="07f12-188">Vous pouvez rendre votre [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] contrôle invisible ou le réduire en définissant <xref:System.Windows.UIElement.Visibility%2A> la propriété sur <xref:System.Windows.Forms.Integration.WindowsFormsHost> l’élément.</span><span class="sxs-lookup"><span data-stu-id="07f12-188">You can make your [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control invisible or collapse it by setting the <xref:System.Windows.UIElement.Visibility%2A> property on the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span> <span data-ttu-id="07f12-189">Quand un contrôle est invisible, il n’est pas affiché, mais il occupe l’espace de disposition.</span><span class="sxs-lookup"><span data-stu-id="07f12-189">When a control is invisible, it is not displayed, but it occupies layout space.</span></span> <span data-ttu-id="07f12-190">Quand un contrôle est réduit, il n’est pas affiché et n’occupe pas l’espace de disposition.</span><span class="sxs-lookup"><span data-stu-id="07f12-190">When a control is collapsed, it is not displayed, nor does it occupy layout space.</span></span>

### <a name="to-set-the-visibility-of-a-hosted-control"></a><span data-ttu-id="07f12-191">Pour définir la visibilité d’un contrôle hébergé</span><span class="sxs-lookup"><span data-stu-id="07f12-191">To set the visibility of a hosted control</span></span>

1. <span data-ttu-id="07f12-192">Copiez le code XAML suivant <xref:System.Windows.Controls.Grid> dans l’élément.</span><span class="sxs-lookup"><span data-stu-id="07f12-192">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#10](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#10)]

2. <span data-ttu-id="07f12-193">Dans MainWindow.xaml.vb ou MainWindow.xaml.cs, copiez le code suivant dans la définition de classe.</span><span class="sxs-lookup"><span data-stu-id="07f12-193">In MainWindow.xaml.vb or MainWindow.xaml.cs, copy the following code into the class definition.</span></span>

     [!code-csharp[WpfLayoutHostingWfWithXaml#102](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#102)]
     [!code-vb[WpfLayoutHostingWfWithXaml#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#102)]

3. <span data-ttu-id="07f12-194">Appuyez sur F5 pour générer et exécuter l'application.</span><span class="sxs-lookup"><span data-stu-id="07f12-194">Press F5 to build and run the application.</span></span>

4. <span data-ttu-id="07f12-195">Cliquez sur le bouton **Cliquer pour rendre invisible** pour rendre <xref:System.Windows.Forms.Integration.WindowsFormsHost> l’élément invisible.</span><span class="sxs-lookup"><span data-stu-id="07f12-195">Click the **Click to make invisible** button to make the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element invisible.</span></span>

5. <span data-ttu-id="07f12-196">Cliquez sur le bouton **Cliquer pour réduire** pour masquer <xref:System.Windows.Forms.Integration.WindowsFormsHost> complètement l’élément de la disposition.</span><span class="sxs-lookup"><span data-stu-id="07f12-196">Click the **Click to collapse** button to hide the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element from the layout entirely.</span></span> <span data-ttu-id="07f12-197">Lorsque le [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] contrôle est réduit, les éléments environnants sont réorganisés pour occuper l’espace.</span><span class="sxs-lookup"><span data-stu-id="07f12-197">When the [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control is collapsed, the surrounding elements are rearranged to occupy its space.</span></span>

## <a name="hosting-a-control-that-does-not-stretch"></a><span data-ttu-id="07f12-198">Hébergement d’un contrôle qui ne s’étire pas</span><span class="sxs-lookup"><span data-stu-id="07f12-198">Hosting a Control That Does Not Stretch</span></span>

<span data-ttu-id="07f12-199">Certains [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] contrôles ont une taille fixe et ne sont pas étirés pour remplir l’espace disponible dans la disposition.</span><span class="sxs-lookup"><span data-stu-id="07f12-199">Some [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls have a fixed size and do not stretch to fill available space in the layout.</span></span> <span data-ttu-id="07f12-200">Par exemple, le <xref:System.Windows.Forms.MonthCalendar> contrôle affiche un mois dans un espace fixe.</span><span class="sxs-lookup"><span data-stu-id="07f12-200">For example, the <xref:System.Windows.Forms.MonthCalendar> control displays a month in a fixed space.</span></span>

### <a name="to-host-a-control-that-does-not-stretch"></a><span data-ttu-id="07f12-201">Pour héberger un contrôle qui ne s’étire pas</span><span class="sxs-lookup"><span data-stu-id="07f12-201">To host a control that does not stretch</span></span>

1. <span data-ttu-id="07f12-202">Copiez le code XAML suivant <xref:System.Windows.Controls.Grid> dans l’élément.</span><span class="sxs-lookup"><span data-stu-id="07f12-202">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#11](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#11)]

2. <span data-ttu-id="07f12-203">Appuyez sur F5 pour générer et exécuter l'application.</span><span class="sxs-lookup"><span data-stu-id="07f12-203">Press F5 to build and run the application.</span></span> <span data-ttu-id="07f12-204">L' <xref:System.Windows.Forms.Integration.WindowsFormsHost> élément est centré dans la ligne de la grille, mais il n’est pas étiré pour remplir l’espace disponible.</span><span class="sxs-lookup"><span data-stu-id="07f12-204">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is centered in the grid row, but it is not stretched to fill the available space.</span></span> <span data-ttu-id="07f12-205">Si la fenêtre est suffisamment grande, vous pouvez voir deux mois ou plus affichés par le contrôle <xref:System.Windows.Forms.MonthCalendar> hébergé, mais ceux-ci sont centrés sur la ligne.</span><span class="sxs-lookup"><span data-stu-id="07f12-205">If the window is large enough, you may see two or more months displayed by the hosted <xref:System.Windows.Forms.MonthCalendar> control, but these are centered in the row.</span></span> <span data-ttu-id="07f12-206">Le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] moteur de disposition Centre les éléments qui ne peuvent pas être dimensionnés pour remplir l’espace disponible.</span><span class="sxs-lookup"><span data-stu-id="07f12-206">The [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layout engine centers elements that cannot be sized to fill the available space.</span></span>

## <a name="scaling"></a><span data-ttu-id="07f12-207">Mise à l'échelle</span><span class="sxs-lookup"><span data-stu-id="07f12-207">Scaling</span></span>

<span data-ttu-id="07f12-208">Contrairement aux éléments WPF, la plupart des contrôles Windows Forms ne sont pas continuellement évolutifs.</span><span class="sxs-lookup"><span data-stu-id="07f12-208">Unlike WPF elements, most Windows Forms controls are not continuously scalable.</span></span> <span data-ttu-id="07f12-209">Pour fournir une mise à l’échelle personnalisée, vous <xref:System.Windows.Forms.Integration.WindowsFormsHost.ScaleChild%2A?displayProperty=nameWithType> devez substituer la méthode.</span><span class="sxs-lookup"><span data-stu-id="07f12-209">To provide custom scaling, you override the <xref:System.Windows.Forms.Integration.WindowsFormsHost.ScaleChild%2A?displayProperty=nameWithType> method.</span></span>

### <a name="to-scale-a-hosted-control-by-using-the-default-behavior"></a><span data-ttu-id="07f12-210">Pour mettre à l’échelle un contrôle hébergé selon le comportement par défaut</span><span class="sxs-lookup"><span data-stu-id="07f12-210">To scale a hosted control by using the default behavior</span></span>

1. <span data-ttu-id="07f12-211">Copiez le code XAML suivant <xref:System.Windows.Controls.Grid> dans l’élément.</span><span class="sxs-lookup"><span data-stu-id="07f12-211">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#12](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#12)]

2. <span data-ttu-id="07f12-212">Appuyez sur F5 pour générer et exécuter l'application.</span><span class="sxs-lookup"><span data-stu-id="07f12-212">Press F5 to build and run the application.</span></span> <span data-ttu-id="07f12-213">Le contrôle hébergé et ses éléments voisins sont mis à l’échelle par un facteur de 0,5.</span><span class="sxs-lookup"><span data-stu-id="07f12-213">The hosted control and its surrounding elements are scaled by a factor of 0.5.</span></span> <span data-ttu-id="07f12-214">Toutefois, la police du contrôle hébergé n’est pas mise à l’échelle.</span><span class="sxs-lookup"><span data-stu-id="07f12-214">However, the hosted control's font is not scaled.</span></span>

<!-- This could use an example of custom scaling. -->

## <a name="rotating"></a><span data-ttu-id="07f12-215">Rotation</span><span class="sxs-lookup"><span data-stu-id="07f12-215">Rotating</span></span>

<span data-ttu-id="07f12-216">Contrairement aux éléments WPF, les contrôles Windows Forms ne prennent pas en charge la rotation.</span><span class="sxs-lookup"><span data-stu-id="07f12-216">Unlike WPF elements, Windows Forms controls do not support rotation.</span></span> <span data-ttu-id="07f12-217">L' <xref:System.Windows.Forms.Integration.WindowsFormsHost> élément ne pivote pas avec d’autres éléments WPF lorsqu’une transformation de rotation est appliquée.</span><span class="sxs-lookup"><span data-stu-id="07f12-217">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element does not rotate with other WPF elements when a rotation transformation is applied.</span></span> <span data-ttu-id="07f12-218">Toute valeur de rotation autre que 180 degrés déclenche <xref:System.Windows.Forms.Integration.WindowsFormsHost.LayoutError> l’événement.</span><span class="sxs-lookup"><span data-stu-id="07f12-218">Any rotation value other than 180 degrees raises the <xref:System.Windows.Forms.Integration.WindowsFormsHost.LayoutError> event.</span></span>

### <a name="to-see-the-effect-of-rotation-in-a-hybrid-application"></a><span data-ttu-id="07f12-219">Pour voir l’effet de la rotation dans une application hybride</span><span class="sxs-lookup"><span data-stu-id="07f12-219">To see the effect of rotation in a hybrid application</span></span>

1. <span data-ttu-id="07f12-220">Copiez le code XAML suivant <xref:System.Windows.Controls.Grid> dans l’élément.</span><span class="sxs-lookup"><span data-stu-id="07f12-220">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#13](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#13)]

2. <span data-ttu-id="07f12-221">Appuyez sur F5 pour générer et exécuter l'application.</span><span class="sxs-lookup"><span data-stu-id="07f12-221">Press F5 to build and run the application.</span></span> <span data-ttu-id="07f12-222">Le contrôle hébergé ne pivote pas, mais ses éléments voisins subissent une rotation de 180 degrés.</span><span class="sxs-lookup"><span data-stu-id="07f12-222">The hosted control is not rotated, but its surrounding elements are rotated by an angle of 180 degrees.</span></span> <span data-ttu-id="07f12-223">Vous devrez peut-être redimensionner la fenêtre pour apercevoir les éléments.</span><span class="sxs-lookup"><span data-stu-id="07f12-223">You may have to resize the window to see the elements.</span></span>

## <a name="setting-padding-and-margins"></a><span data-ttu-id="07f12-224">Définition d’une marge intérieure et de marges</span><span class="sxs-lookup"><span data-stu-id="07f12-224">Setting Padding and Margins</span></span>

<span data-ttu-id="07f12-225">Le remplissage et les marges dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] la disposition sont similaires aux marges intérieures et aux marges dans. [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]</span><span class="sxs-lookup"><span data-stu-id="07f12-225">Padding and margins in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layout are similar to padding and margins in [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span></span> <span data-ttu-id="07f12-226">Définissez simplement les <xref:System.Windows.Controls.Control.Padding%2A> propriétés <xref:System.Windows.FrameworkElement.Margin%2A> et sur l' <xref:System.Windows.Forms.Integration.WindowsFormsHost> élément.</span><span class="sxs-lookup"><span data-stu-id="07f12-226">Simply set the <xref:System.Windows.Controls.Control.Padding%2A> and <xref:System.Windows.FrameworkElement.Margin%2A> properties on the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span>

### <a name="to-set-padding-and-margins-for-a-hosted-control"></a><span data-ttu-id="07f12-227">Pour définir la marge intérieure et les marges d’un contrôle hébergé</span><span class="sxs-lookup"><span data-stu-id="07f12-227">To set padding and margins for a hosted control</span></span>

1. <span data-ttu-id="07f12-228">Copiez le code XAML suivant <xref:System.Windows.Controls.Grid> dans l’élément.</span><span class="sxs-lookup"><span data-stu-id="07f12-228">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#14](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#14)]
    [!code-xaml[WpfLayoutHostingWfWithXaml#15](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#15)]

2. <span data-ttu-id="07f12-229">Appuyez sur F5 pour générer et exécuter l'application.</span><span class="sxs-lookup"><span data-stu-id="07f12-229">Press F5 to build and run the application.</span></span> <span data-ttu-id="07f12-230">Les paramètres de marge intérieure et de marge sont appliqués aux [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] contrôles hébergés de la même façon que dans. [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]</span><span class="sxs-lookup"><span data-stu-id="07f12-230">The padding and margin settings are applied to the hosted [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls in the same way they would be applied in [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span></span>

## <a name="using-dynamic-layout-containers"></a><span data-ttu-id="07f12-231">Utilisation de conteneurs de disposition dynamiques</span><span class="sxs-lookup"><span data-stu-id="07f12-231">Using Dynamic Layout Containers</span></span>

[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<span data-ttu-id="07f12-232">fournit deux conteneurs de disposition dynamique <xref:System.Windows.Forms.FlowLayoutPanel> , <xref:System.Windows.Forms.TableLayoutPanel>et.</span><span class="sxs-lookup"><span data-stu-id="07f12-232">provides two dynamic layout containers, <xref:System.Windows.Forms.FlowLayoutPanel> and <xref:System.Windows.Forms.TableLayoutPanel>.</span></span> <span data-ttu-id="07f12-233">Vous pouvez également utiliser ces conteneurs dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] des dispositions.</span><span class="sxs-lookup"><span data-stu-id="07f12-233">You can also use these containers in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layouts.</span></span>

### <a name="to-use-a-dynamic-layout-container"></a><span data-ttu-id="07f12-234">Pour utiliser un conteneur de disposition dynamique</span><span class="sxs-lookup"><span data-stu-id="07f12-234">To use a dynamic layout container</span></span>

1. <span data-ttu-id="07f12-235">Copiez le code XAML suivant <xref:System.Windows.Controls.Grid> dans l’élément.</span><span class="sxs-lookup"><span data-stu-id="07f12-235">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#16](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#16)]

2. <span data-ttu-id="07f12-236">Dans MainWindow.xaml.vb ou MainWindow.xaml.cs, copiez le code suivant dans la définition de classe.</span><span class="sxs-lookup"><span data-stu-id="07f12-236">In MainWindow.xaml.vb or MainWindow.xaml.cs copy the following code into the class definition.</span></span>

     [!code-csharp[WpfLayoutHostingWfWithXaml#103](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#103)]
     [!code-vb[WpfLayoutHostingWfWithXaml#103](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#103)]

3. <span data-ttu-id="07f12-237">Ajoutez un appel à la méthode `InitializeFlowLayoutPanel` dans le constructeur.</span><span class="sxs-lookup"><span data-stu-id="07f12-237">Add a call to the `InitializeFlowLayoutPanel` method in the constructor.</span></span>

     [!code-csharp[WpfLayoutHostingWfWithXaml#104](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#104)]
     [!code-vb[WpfLayoutHostingWfWithXaml#104](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#104)]

4. <span data-ttu-id="07f12-238">Appuyez sur F5 pour générer et exécuter l'application.</span><span class="sxs-lookup"><span data-stu-id="07f12-238">Press F5 to build and run the application.</span></span> <span data-ttu-id="07f12-239">L' <xref:System.Windows.Forms.Integration.WindowsFormsHost> élément remplit le <xref:System.Windows.Controls.DockPanel>et <xref:System.Windows.Forms.FlowLayoutPanel> réorganise ses contrôles enfants dans la valeur par défaut <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A>.</span><span class="sxs-lookup"><span data-stu-id="07f12-239">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element fills the <xref:System.Windows.Controls.DockPanel>, and <xref:System.Windows.Forms.FlowLayoutPanel> arranges its child controls in the default <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A>.</span></span>

## <a name="see-also"></a><span data-ttu-id="07f12-240">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="07f12-240">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="07f12-241">Concevoir en XAML dans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="07f12-241">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)
- [<span data-ttu-id="07f12-242">Considérations sur la disposition de l’élément WindowsFormsHost</span><span class="sxs-lookup"><span data-stu-id="07f12-242">Layout Considerations for the WindowsFormsHost Element</span></span>](layout-considerations-for-the-windowsformshost-element.md)
- [<span data-ttu-id="07f12-243">Organiser des contrôles de Windows Forms dans WPF, exemple</span><span class="sxs-lookup"><span data-stu-id="07f12-243">Arranging Windows Forms Controls in WPF Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=159971)
- [<span data-ttu-id="07f12-244">Procédure pas à pas : Hébergement d’un contrôle composite Windows Forms dans WPF</span><span class="sxs-lookup"><span data-stu-id="07f12-244">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [<span data-ttu-id="07f12-245">Procédure pas à pas : Hébergement d’un contrôle composite WPF dans Windows Forms</span><span class="sxs-lookup"><span data-stu-id="07f12-245">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
