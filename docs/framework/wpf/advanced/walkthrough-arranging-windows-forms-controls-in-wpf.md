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
ms.openlocfilehash: 3a94ef65be99b01a9511f37872cbcacd6ec12264
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/09/2019
ms.locfileid: "72179433"
---
# <a name="walkthrough-arranging-windows-forms-controls-in-wpf"></a><span data-ttu-id="512d9-102">Procédure pas à pas : organisation des contrôles Windows Forms dans WPF</span><span class="sxs-lookup"><span data-stu-id="512d9-102">Walkthrough: Arranging Windows Forms Controls in WPF</span></span>

<span data-ttu-id="512d9-103">Cette procédure pas à pas vous montre comment utiliser les fonctionnalités de disposition [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pour réorganiser les contrôles [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] dans une application hybride.</span><span class="sxs-lookup"><span data-stu-id="512d9-103">This walkthrough shows you how to use [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layout features to arrange [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls in a hybrid application.</span></span>

<span data-ttu-id="512d9-104">Cette procédure pas à pas décrit notamment les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="512d9-104">Tasks illustrated in this walkthrough include:</span></span>

- <span data-ttu-id="512d9-105">Création du projet</span><span class="sxs-lookup"><span data-stu-id="512d9-105">Creating the project.</span></span>
- <span data-ttu-id="512d9-106">Utilisation des paramètres de disposition par défaut</span><span class="sxs-lookup"><span data-stu-id="512d9-106">Using default layout settings.</span></span>
- <span data-ttu-id="512d9-107">Dimensionnement en fonction du contenu</span><span class="sxs-lookup"><span data-stu-id="512d9-107">Sizing to content.</span></span>
- <span data-ttu-id="512d9-108">Utilisation du positionnement absolu</span><span class="sxs-lookup"><span data-stu-id="512d9-108">Using absolute positioning.</span></span>
- <span data-ttu-id="512d9-109">Spécification explicite de la taille</span><span class="sxs-lookup"><span data-stu-id="512d9-109">Specifying size explicitly.</span></span>
- <span data-ttu-id="512d9-110">Définition des propriétés de disposition</span><span class="sxs-lookup"><span data-stu-id="512d9-110">Setting layout properties.</span></span>
- <span data-ttu-id="512d9-111">Présentation des limitations dans l’ordre de plan</span><span class="sxs-lookup"><span data-stu-id="512d9-111">Understanding z-order limitations.</span></span>
- <span data-ttu-id="512d9-112">Ancrage</span><span class="sxs-lookup"><span data-stu-id="512d9-112">Docking.</span></span>
- <span data-ttu-id="512d9-113">Définition de la visibilité</span><span class="sxs-lookup"><span data-stu-id="512d9-113">Setting visibility.</span></span>
- <span data-ttu-id="512d9-114">Hébergement d’un contrôle qui ne s’étire pas</span><span class="sxs-lookup"><span data-stu-id="512d9-114">Hosting a control that does not stretch.</span></span>
- <span data-ttu-id="512d9-115">Mise à l’échelle</span><span class="sxs-lookup"><span data-stu-id="512d9-115">Scaling.</span></span>
- <span data-ttu-id="512d9-116">Rotation</span><span class="sxs-lookup"><span data-stu-id="512d9-116">Rotating.</span></span>
- <span data-ttu-id="512d9-117">Définition d’une marge intérieure et de marges</span><span class="sxs-lookup"><span data-stu-id="512d9-117">Setting padding and margins.</span></span>
- <span data-ttu-id="512d9-118">Utilisation de conteneurs de présentation dynamiques</span><span class="sxs-lookup"><span data-stu-id="512d9-118">Using dynamic layout containers.</span></span>

<span data-ttu-id="512d9-119">Pour obtenir le code complet des tâches illustrées dans cette procédure pas à pas, consultez [réorganisation des contrôles de Windows Forms dans l’exemple WPF](https://go.microsoft.com/fwlink/?LinkID=159971).</span><span class="sxs-lookup"><span data-stu-id="512d9-119">For a complete code listing of the tasks illustrated in this walkthrough, see [Arranging Windows Forms Controls in WPF Sample](https://go.microsoft.com/fwlink/?LinkID=159971).</span></span>

<span data-ttu-id="512d9-120">Une fois que vous avez terminé, vous aurez une compréhension des fonctionnalités de disposition [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] dans @no__t applications de base 1.</span><span class="sxs-lookup"><span data-stu-id="512d9-120">When you are finished, you will have an understanding of [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] layout features in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-based applications.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="512d9-121">Prérequis</span><span class="sxs-lookup"><span data-stu-id="512d9-121">Prerequisites</span></span>

<span data-ttu-id="512d9-122">Cette procédure pas à pas nécessite Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="512d9-122">You need Visual Studio to complete this walkthrough.</span></span>

## <a name="creating-the-project"></a><span data-ttu-id="512d9-123">Création du projet</span><span class="sxs-lookup"><span data-stu-id="512d9-123">Creating the Project</span></span>

<span data-ttu-id="512d9-124">Pour créer et configurer le projet, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="512d9-124">To create and set up the project, follow these steps:</span></span>

1. <span data-ttu-id="512d9-125">Créez un projet d’application WPF nommé `WpfLayoutHostingWf`.</span><span class="sxs-lookup"><span data-stu-id="512d9-125">Create a WPF Application project named `WpfLayoutHostingWf`.</span></span>

2. <span data-ttu-id="512d9-126">Dans Explorateur de solutions, ajoutez des références aux assemblys suivants :</span><span class="sxs-lookup"><span data-stu-id="512d9-126">In Solution Explorer, add references to the following assemblies:</span></span>

    - <span data-ttu-id="512d9-127">WindowsFormsIntegration</span><span class="sxs-lookup"><span data-stu-id="512d9-127">WindowsFormsIntegration</span></span>
    - <span data-ttu-id="512d9-128">System.Windows.Forms</span><span class="sxs-lookup"><span data-stu-id="512d9-128">System.Windows.Forms</span></span>
    - <span data-ttu-id="512d9-129">System.Drawing</span><span class="sxs-lookup"><span data-stu-id="512d9-129">System.Drawing</span></span>

3. <span data-ttu-id="512d9-130">Double-cliquez sur *MainWindow. Xaml* pour l’ouvrir en mode XAML.</span><span class="sxs-lookup"><span data-stu-id="512d9-130">Double-click *MainWindow.xaml* to open it in XAML view.</span></span>

4. <span data-ttu-id="512d9-131">Dans l’élément <xref:System.Windows.Window>, ajoutez le mappage d’espace de noms [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] suivant.</span><span class="sxs-lookup"><span data-stu-id="512d9-131">In the <xref:System.Windows.Window> element, add the following [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] namespace mapping.</span></span>

    ```xaml
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"
    ```

5. <span data-ttu-id="512d9-132">Dans l’élément <xref:System.Windows.Controls.Grid>, affectez à la propriété <xref:System.Windows.Controls.Grid.ShowGridLines%2A> la valeur `true` et définissez cinq lignes et trois colonnes.</span><span class="sxs-lookup"><span data-stu-id="512d9-132">In the <xref:System.Windows.Controls.Grid> element set the <xref:System.Windows.Controls.Grid.ShowGridLines%2A> property to `true` and define five rows and three columns.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#2](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#2)]

## <a name="using-default-layout-settings"></a><span data-ttu-id="512d9-133">Utilisation des paramètres de disposition par défaut</span><span class="sxs-lookup"><span data-stu-id="512d9-133">Using Default Layout Settings</span></span>

<span data-ttu-id="512d9-134">Par défaut, l’élément <xref:System.Windows.Forms.Integration.WindowsFormsHost> gère la disposition du contrôle [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] hébergé.</span><span class="sxs-lookup"><span data-stu-id="512d9-134">By default, the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element handles the layout for the hosted [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control.</span></span>

<span data-ttu-id="512d9-135">Pour utiliser les paramètres de disposition par défaut, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="512d9-135">To use default layout settings, follow these steps:</span></span>

1. <span data-ttu-id="512d9-136">Copiez le code XAML suivant dans l’élément <xref:System.Windows.Controls.Grid> :</span><span class="sxs-lookup"><span data-stu-id="512d9-136">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element:</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#3](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#3)]

2. <span data-ttu-id="512d9-137">Appuyez sur <kbd>F5</kbd> pour générer et exécuter l’application.</span><span class="sxs-lookup"><span data-stu-id="512d9-137">Press <kbd>F5</kbd> to build and run the application.</span></span> <span data-ttu-id="512d9-138">Le contrôle [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.Button?displayProperty=nameWithType> apparaît dans le <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="512d9-138">The [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.Button?displayProperty=nameWithType> control appears in the <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="512d9-139">Le contrôle hébergé est dimensionné en fonction de son contenu, et l’élément <xref:System.Windows.Forms.Integration.WindowsFormsHost> est dimensionné pour s’adapter au contrôle hébergé.</span><span class="sxs-lookup"><span data-stu-id="512d9-139">The hosted control is sized based on its content, and the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is sized to accommodate the hosted control.</span></span>

## <a name="sizing-to-content"></a><span data-ttu-id="512d9-140">Dimensionnement en fonction du contenu</span><span class="sxs-lookup"><span data-stu-id="512d9-140">Sizing to Content</span></span>

<span data-ttu-id="512d9-141">L’élément <xref:System.Windows.Forms.Integration.WindowsFormsHost> garantit que le contrôle hébergé est dimensionné pour afficher correctement son contenu.</span><span class="sxs-lookup"><span data-stu-id="512d9-141">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element ensures that the hosted control is sized to display its content properly.</span></span>

<span data-ttu-id="512d9-142">Pour ajuster au contenu, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="512d9-142">To size to content, follow these steps:</span></span>

1. <span data-ttu-id="512d9-143">Copiez le code XAML suivant dans l’élément <xref:System.Windows.Controls.Grid> :</span><span class="sxs-lookup"><span data-stu-id="512d9-143">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element:</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#4](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#4)]

2. <span data-ttu-id="512d9-144">Appuyez sur <kbd>F5</kbd> pour générer et exécuter l’application.</span><span class="sxs-lookup"><span data-stu-id="512d9-144">Press <kbd>F5</kbd> to build and run the application.</span></span> <span data-ttu-id="512d9-145">Les deux nouveaux contrôles Button sont dimensionnés pour afficher la chaîne de texte la plus longue et la taille de police supérieure correctement, et les éléments <xref:System.Windows.Forms.Integration.WindowsFormsHost> sont redimensionnés pour s’adapter aux contrôles hébergés.</span><span class="sxs-lookup"><span data-stu-id="512d9-145">The two new button controls are sized to display the longer text string and larger font size properly, and the <xref:System.Windows.Forms.Integration.WindowsFormsHost> elements are resized to accommodate the hosted controls.</span></span>

## <a name="using-absolute-positioning"></a><span data-ttu-id="512d9-146">Utilisation du positionnement absolu</span><span class="sxs-lookup"><span data-stu-id="512d9-146">Using Absolute Positioning</span></span>

<span data-ttu-id="512d9-147">Vous pouvez utiliser le positionnement absolu pour placer l’élément <xref:System.Windows.Forms.Integration.WindowsFormsHost> n’importe où dans l’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="512d9-147">You can use absolute positioning to place the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element anywhere in the user interface (UI).</span></span>

<span data-ttu-id="512d9-148">Pour utiliser le positionnement absolu, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="512d9-148">To use absolute positioning, follow these steps:</span></span>

1. <span data-ttu-id="512d9-149">Copiez le code XAML suivant dans l’élément <xref:System.Windows.Controls.Grid> :</span><span class="sxs-lookup"><span data-stu-id="512d9-149">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element:</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#5](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#5)]

2. <span data-ttu-id="512d9-150">Appuyez sur <kbd>F5</kbd> pour générer et exécuter l’application.</span><span class="sxs-lookup"><span data-stu-id="512d9-150">Press <kbd>F5</kbd> to build and run the application.</span></span> <span data-ttu-id="512d9-151">L’élément <xref:System.Windows.Forms.Integration.WindowsFormsHost> est placé à 20 pixels du bord supérieur de la cellule de la grille et à 20 pixels à partir de la gauche.</span><span class="sxs-lookup"><span data-stu-id="512d9-151">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is placed 20 pixels from the top side of the grid cell and 20 pixels from the left.</span></span>

## <a name="specifying-size-explicitly"></a><span data-ttu-id="512d9-152">Spécification explicite de la taille</span><span class="sxs-lookup"><span data-stu-id="512d9-152">Specifying Size Explicitly</span></span>

<span data-ttu-id="512d9-153">Vous pouvez spécifier la taille de l’élément <xref:System.Windows.Forms.Integration.WindowsFormsHost> à l’aide des propriétés <xref:System.Windows.FrameworkElement.Width%2A> et <xref:System.Windows.FrameworkElement.Height%2A>.</span><span class="sxs-lookup"><span data-stu-id="512d9-153">You can specify the size of the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element using the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties.</span></span>

<span data-ttu-id="512d9-154">Pour spécifier explicitement la taille, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="512d9-154">To specify size explicitly, follow these steps:</span></span>

1. <span data-ttu-id="512d9-155">Copiez le code XAML suivant dans l’élément <xref:System.Windows.Controls.Grid> :</span><span class="sxs-lookup"><span data-stu-id="512d9-155">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element:</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#6](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#6)]

2. <span data-ttu-id="512d9-156">Appuyez sur <kbd>F5</kbd> pour générer et exécuter l’application.</span><span class="sxs-lookup"><span data-stu-id="512d9-156">Press <kbd>F5</kbd> to build and run the application.</span></span> <span data-ttu-id="512d9-157">L’élément <xref:System.Windows.Forms.Integration.WindowsFormsHost> est défini sur une taille de 50 pixels de large par 70 pixels de haut, ce qui est plus petit que les paramètres de disposition par défaut.</span><span class="sxs-lookup"><span data-stu-id="512d9-157">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is set to a size of 50 pixels wide by 70 pixels high, which is smaller than the default layout settings.</span></span> <span data-ttu-id="512d9-158">Le contenu du contrôle [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] est réorganisé en conséquence.</span><span class="sxs-lookup"><span data-stu-id="512d9-158">The content of the [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control is rearranged accordingly.</span></span>

## <a name="setting-layout-properties"></a><span data-ttu-id="512d9-159">Définition des propriétés de disposition</span><span class="sxs-lookup"><span data-stu-id="512d9-159">Setting Layout Properties</span></span>

<span data-ttu-id="512d9-160">Définissez toujours les propriétés relatives à la disposition sur le contrôle hébergé à l’aide des propriétés de l’élément <xref:System.Windows.Forms.Integration.WindowsFormsHost>.</span><span class="sxs-lookup"><span data-stu-id="512d9-160">Always set layout-related properties on the hosted control by using the properties of the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span> <span data-ttu-id="512d9-161">Si vous définissez les propriétés de disposition directement sur le contrôle hébergé, vous obtiendrez des résultats inattendus.</span><span class="sxs-lookup"><span data-stu-id="512d9-161">Setting layout properties directly on the hosted control will yield unintended results.</span></span>

 <span data-ttu-id="512d9-162">La définition des propriétés relatives à la disposition sur le contrôle hébergé dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] n’a aucun effet.</span><span class="sxs-lookup"><span data-stu-id="512d9-162">Setting layout-related properties on the hosted control in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] has no effect.</span></span>

<span data-ttu-id="512d9-163">Pour voir les effets de la définition des propriétés sur le contrôle hébergé, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="512d9-163">To see the effects of setting properties on the hosted control, follow these steps:</span></span>

1. <span data-ttu-id="512d9-164">Copiez le code XAML suivant dans l’élément <xref:System.Windows.Controls.Grid> :</span><span class="sxs-lookup"><span data-stu-id="512d9-164">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element:</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#7](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#7)]

2. <span data-ttu-id="512d9-165">Dans **Explorateur de solutions**, double-cliquez sur *MainWindow. Xaml. vb* ou *MainWindow.Xaml.cs* pour l’ouvrir dans l’éditeur de code.</span><span class="sxs-lookup"><span data-stu-id="512d9-165">In **Solution Explorer**, double-click *MainWindow.xaml.vb* or *MainWindow.xaml.cs* to open it in the Code Editor.</span></span>

3. <span data-ttu-id="512d9-166">Copiez le code suivant dans la définition de classe `MainWindow` :</span><span class="sxs-lookup"><span data-stu-id="512d9-166">Copy the following code into the `MainWindow` class definition:</span></span>

     [!code-csharp[WpfLayoutHostingWfWithXaml#101](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#101)]
     [!code-vb[WpfLayoutHostingWfWithXaml#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#101)]

4. <span data-ttu-id="512d9-167">Appuyez sur <kbd>F5</kbd> pour générer et exécuter l’application.</span><span class="sxs-lookup"><span data-stu-id="512d9-167">Press <kbd>F5</kbd> to build and run the application.</span></span>

5. <span data-ttu-id="512d9-168">Cliquez sur le bouton **cliquez sur moi** .</span><span class="sxs-lookup"><span data-stu-id="512d9-168">Click the **Click me** button.</span></span> <span data-ttu-id="512d9-169">Le gestionnaire d’événements `button1_Click` définit les propriétés <xref:System.Windows.Forms.Control.Top%2A> et <xref:System.Windows.Forms.Control.Left%2A> sur le contrôle hébergé.</span><span class="sxs-lookup"><span data-stu-id="512d9-169">The `button1_Click` event handler sets the <xref:System.Windows.Forms.Control.Top%2A> and <xref:System.Windows.Forms.Control.Left%2A> properties on the hosted control.</span></span> <span data-ttu-id="512d9-170">Le contrôle hébergé est alors repositionné dans l’élément <xref:System.Windows.Forms.Integration.WindowsFormsHost>.</span><span class="sxs-lookup"><span data-stu-id="512d9-170">This causes the hosted control to be repositioned within the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span> <span data-ttu-id="512d9-171">L’hôte conserve la même zone d’écran, mais le contrôle hébergé est découpé.</span><span class="sxs-lookup"><span data-stu-id="512d9-171">The host maintains the same screen area, but the hosted control is clipped.</span></span> <span data-ttu-id="512d9-172">Au lieu de cela, le contrôle hébergé doit toujours remplir l’élément <xref:System.Windows.Forms.Integration.WindowsFormsHost>.</span><span class="sxs-lookup"><span data-stu-id="512d9-172">Instead, the hosted control should always fill the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span>

## <a name="understanding-z-order-limitations"></a><span data-ttu-id="512d9-173">Présentation des limitations dans l’ordre de plan</span><span class="sxs-lookup"><span data-stu-id="512d9-173">Understanding Z-Order Limitations</span></span>

<span data-ttu-id="512d9-174">Les éléments <xref:System.Windows.Forms.Integration.WindowsFormsHost> visibles sont toujours dessinés par-dessus d’autres éléments WPF, et ils ne sont pas affectés par l’ordre de plan.</span><span class="sxs-lookup"><span data-stu-id="512d9-174">Visible <xref:System.Windows.Forms.Integration.WindowsFormsHost> elements are always drawn on top of other WPF elements, and they are unaffected by z-order.</span></span> <span data-ttu-id="512d9-175">Pour voir ce comportement de l’ordre de plan, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="512d9-175">To see this z-order behavior, do the following:</span></span>

1. <span data-ttu-id="512d9-176">Copiez le code XAML suivant dans l’élément <xref:System.Windows.Controls.Grid> :</span><span class="sxs-lookup"><span data-stu-id="512d9-176">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element:</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#8](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#8)]

2. <span data-ttu-id="512d9-177">Appuyez sur <kbd>F5</kbd> pour générer et exécuter l’application.</span><span class="sxs-lookup"><span data-stu-id="512d9-177">Press <kbd>F5</kbd> to build and run the application.</span></span> <span data-ttu-id="512d9-178">L’élément <xref:System.Windows.Forms.Integration.WindowsFormsHost> est peint sur l’élément label.</span><span class="sxs-lookup"><span data-stu-id="512d9-178">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is painted over the label element.</span></span>

## <a name="docking"></a><span data-ttu-id="512d9-179">Ancrage</span><span class="sxs-lookup"><span data-stu-id="512d9-179">Docking</span></span>

<span data-ttu-id="512d9-180">l’élément <xref:System.Windows.Forms.Integration.WindowsFormsHost> prend en charge l’ancrage [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="512d9-180"><xref:System.Windows.Forms.Integration.WindowsFormsHost> element supports [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] docking.</span></span> <span data-ttu-id="512d9-181">Définissez la propriété jointe <xref:System.Windows.Controls.DockPanel.Dock%2A> pour ancrer le contrôle hébergé dans un élément <xref:System.Windows.Controls.DockPanel>.</span><span class="sxs-lookup"><span data-stu-id="512d9-181">Set the <xref:System.Windows.Controls.DockPanel.Dock%2A> attached property to dock the hosted control in a <xref:System.Windows.Controls.DockPanel> element.</span></span>

<span data-ttu-id="512d9-182">Pour ancrer un contrôle hébergé, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="512d9-182">To dock a hosted control, follow these steps:</span></span>

1. <span data-ttu-id="512d9-183">Copiez le code XAML suivant dans l’élément <xref:System.Windows.Controls.Grid> :</span><span class="sxs-lookup"><span data-stu-id="512d9-183">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element:</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#9](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#9)]

2. <span data-ttu-id="512d9-184">Appuyez sur <kbd>F5</kbd> pour générer et exécuter l’application.</span><span class="sxs-lookup"><span data-stu-id="512d9-184">Press <kbd>F5</kbd> to build and run the application.</span></span> <span data-ttu-id="512d9-185">L’élément <xref:System.Windows.Forms.Integration.WindowsFormsHost> est ancré à droite de l’élément <xref:System.Windows.Controls.DockPanel>.</span><span class="sxs-lookup"><span data-stu-id="512d9-185">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is docked to the right side of the <xref:System.Windows.Controls.DockPanel> element.</span></span>

## <a name="setting-visibility"></a><span data-ttu-id="512d9-186">Définition de la visibilité</span><span class="sxs-lookup"><span data-stu-id="512d9-186">Setting Visibility</span></span>

<span data-ttu-id="512d9-187">Vous pouvez rendre votre contrôle [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] invisible ou le réduire en définissant la propriété <xref:System.Windows.UIElement.Visibility%2A> sur l’élément <xref:System.Windows.Forms.Integration.WindowsFormsHost>.</span><span class="sxs-lookup"><span data-stu-id="512d9-187">You can make your [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control invisible or collapse it by setting the <xref:System.Windows.UIElement.Visibility%2A> property on the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span> <span data-ttu-id="512d9-188">Quand un contrôle est invisible, il n’est pas affiché, mais il occupe l’espace de disposition.</span><span class="sxs-lookup"><span data-stu-id="512d9-188">When a control is invisible, it is not displayed, but it occupies layout space.</span></span> <span data-ttu-id="512d9-189">Quand un contrôle est réduit, il n’est pas affiché et n’occupe pas l’espace de disposition.</span><span class="sxs-lookup"><span data-stu-id="512d9-189">When a control is collapsed, it is not displayed, nor does it occupy layout space.</span></span>

<span data-ttu-id="512d9-190">Pour définir la visibilité d’un contrôle hébergé, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="512d9-190">To set the visibility of a hosted control, follow these steps:</span></span>

1. <span data-ttu-id="512d9-191">Copiez le code XAML suivant dans l’élément <xref:System.Windows.Controls.Grid> :</span><span class="sxs-lookup"><span data-stu-id="512d9-191">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element:</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#10](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#10)]

2. <span data-ttu-id="512d9-192">Dans *MainWindow. Xaml. vb* ou *MainWindow.Xaml.cs*, copiez le code suivant dans la définition de classe :</span><span class="sxs-lookup"><span data-stu-id="512d9-192">In *MainWindow.xaml.vb* or *MainWindow.xaml.cs*, copy the following code into the class definition:</span></span>

     [!code-csharp[WpfLayoutHostingWfWithXaml#102](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#102)]
     [!code-vb[WpfLayoutHostingWfWithXaml#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#102)]

3. <span data-ttu-id="512d9-193">Appuyez sur <kbd>F5</kbd> pour générer et exécuter l’application.</span><span class="sxs-lookup"><span data-stu-id="512d9-193">Press <kbd>F5</kbd> to build and run the application.</span></span>

4. <span data-ttu-id="512d9-194">Cliquez sur le bouton **Cliquer pour rendre invisible** pour rendre l’élément <xref:System.Windows.Forms.Integration.WindowsFormsHost> invisible.</span><span class="sxs-lookup"><span data-stu-id="512d9-194">Click the **Click to make invisible** button to make the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element invisible.</span></span>

5. <span data-ttu-id="512d9-195">Cliquez sur le bouton **Cliquer pour réduire** pour masquer complètement l’élément <xref:System.Windows.Forms.Integration.WindowsFormsHost> dans la disposition.</span><span class="sxs-lookup"><span data-stu-id="512d9-195">Click the **Click to collapse** button to hide the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element from the layout entirely.</span></span> <span data-ttu-id="512d9-196">Lorsque le contrôle [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] est réduit, les éléments environnants sont réorganisés pour occuper l’espace.</span><span class="sxs-lookup"><span data-stu-id="512d9-196">When the [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control is collapsed, the surrounding elements are rearranged to occupy its space.</span></span>

## <a name="hosting-a-control-that-does-not-stretch"></a><span data-ttu-id="512d9-197">Hébergement d’un contrôle qui ne s’étire pas</span><span class="sxs-lookup"><span data-stu-id="512d9-197">Hosting a Control That Does Not Stretch</span></span>

<span data-ttu-id="512d9-198">Certains contrôles [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ont une taille fixe et ne sont pas étirés pour remplir l’espace disponible dans la disposition.</span><span class="sxs-lookup"><span data-stu-id="512d9-198">Some [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls have a fixed size and do not stretch to fill available space in the layout.</span></span> <span data-ttu-id="512d9-199">Par exemple, le contrôle <xref:System.Windows.Forms.MonthCalendar> affiche un mois dans un espace fixe.</span><span class="sxs-lookup"><span data-stu-id="512d9-199">For example, the <xref:System.Windows.Forms.MonthCalendar> control displays a month in a fixed space.</span></span>

<span data-ttu-id="512d9-200">Pour héberger un contrôle qui ne s’étire pas, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="512d9-200">To host a control that does not stretch, follow these steps:</span></span>

1. <span data-ttu-id="512d9-201">Copiez le code XAML suivant dans l’élément <xref:System.Windows.Controls.Grid> :</span><span class="sxs-lookup"><span data-stu-id="512d9-201">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element:</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#11](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#11)]

2. <span data-ttu-id="512d9-202">Appuyez sur <kbd>F5</kbd> pour générer et exécuter l’application.</span><span class="sxs-lookup"><span data-stu-id="512d9-202">Press <kbd>F5</kbd> to build and run the application.</span></span> <span data-ttu-id="512d9-203">L’élément <xref:System.Windows.Forms.Integration.WindowsFormsHost> est centré dans la ligne de la grille, mais il n’est pas étiré pour remplir l’espace disponible.</span><span class="sxs-lookup"><span data-stu-id="512d9-203">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is centered in the grid row, but it is not stretched to fill the available space.</span></span> <span data-ttu-id="512d9-204">Si la fenêtre est suffisamment grande, vous pouvez voir deux mois ou plus affichés par le contrôle <xref:System.Windows.Forms.MonthCalendar> hébergé, mais ceux-ci sont centrés sur la ligne.</span><span class="sxs-lookup"><span data-stu-id="512d9-204">If the window is large enough, you may see two or more months displayed by the hosted <xref:System.Windows.Forms.MonthCalendar> control, but these are centered in the row.</span></span> <span data-ttu-id="512d9-205">Le moteur de disposition [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Centre les éléments qui ne peuvent pas être dimensionnés pour remplir l’espace disponible.</span><span class="sxs-lookup"><span data-stu-id="512d9-205">The [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layout engine centers elements that cannot be sized to fill the available space.</span></span>

## <a name="scaling"></a><span data-ttu-id="512d9-206">Mise à l'échelle</span><span class="sxs-lookup"><span data-stu-id="512d9-206">Scaling</span></span>

<span data-ttu-id="512d9-207">Contrairement aux éléments WPF, la plupart des contrôles Windows Forms ne sont pas continuellement évolutifs.</span><span class="sxs-lookup"><span data-stu-id="512d9-207">Unlike WPF elements, most Windows Forms controls are not continuously scalable.</span></span> <span data-ttu-id="512d9-208">Pour fournir une mise à l’échelle personnalisée, vous devez substituer la méthode <xref:System.Windows.Forms.Integration.WindowsFormsHost.ScaleChild%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="512d9-208">To provide custom scaling, you override the <xref:System.Windows.Forms.Integration.WindowsFormsHost.ScaleChild%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="512d9-209">Pour mettre à l’échelle un contrôle hébergé à l’aide du comportement par défaut, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="512d9-209">To scale a hosted control by using the default behavior, follow these steps:</span></span>

1. <span data-ttu-id="512d9-210">Copiez le code XAML suivant dans l’élément <xref:System.Windows.Controls.Grid> :</span><span class="sxs-lookup"><span data-stu-id="512d9-210">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element:</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#12](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#12)]

2. <span data-ttu-id="512d9-211">Appuyez sur <kbd>F5</kbd> pour générer et exécuter l’application.</span><span class="sxs-lookup"><span data-stu-id="512d9-211">Press <kbd>F5</kbd> to build and run the application.</span></span> <span data-ttu-id="512d9-212">Le contrôle hébergé et ses éléments voisins sont mis à l’échelle par un facteur de 0,5.</span><span class="sxs-lookup"><span data-stu-id="512d9-212">The hosted control and its surrounding elements are scaled by a factor of 0.5.</span></span> <span data-ttu-id="512d9-213">Toutefois, la police du contrôle hébergé n’est pas mise à l’échelle.</span><span class="sxs-lookup"><span data-stu-id="512d9-213">However, the hosted control's font is not scaled.</span></span>

<!-- This could use an example of custom scaling. -->

## <a name="rotating"></a><span data-ttu-id="512d9-214">Rotation</span><span class="sxs-lookup"><span data-stu-id="512d9-214">Rotating</span></span>

<span data-ttu-id="512d9-215">Contrairement aux éléments WPF, les contrôles Windows Forms ne prennent pas en charge la rotation.</span><span class="sxs-lookup"><span data-stu-id="512d9-215">Unlike WPF elements, Windows Forms controls do not support rotation.</span></span> <span data-ttu-id="512d9-216">L’élément <xref:System.Windows.Forms.Integration.WindowsFormsHost> ne pivote pas avec d’autres éléments WPF lorsqu’une transformation de rotation est appliquée.</span><span class="sxs-lookup"><span data-stu-id="512d9-216">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element does not rotate with other WPF elements when a rotation transformation is applied.</span></span> <span data-ttu-id="512d9-217">Toute valeur de rotation autre que 180 degrés déclenche l’événement <xref:System.Windows.Forms.Integration.WindowsFormsHost.LayoutError>.</span><span class="sxs-lookup"><span data-stu-id="512d9-217">Any rotation value other than 180 degrees raises the <xref:System.Windows.Forms.Integration.WindowsFormsHost.LayoutError> event.</span></span>

<span data-ttu-id="512d9-218">Pour voir l’effet de la rotation dans une application hybride, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="512d9-218">To see the effect of rotation in a hybrid application, follow these steps:</span></span>

1. <span data-ttu-id="512d9-219">Copiez le code XAML suivant dans l’élément <xref:System.Windows.Controls.Grid> :</span><span class="sxs-lookup"><span data-stu-id="512d9-219">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element:</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#13](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#13)]

2. <span data-ttu-id="512d9-220">Appuyez sur <kbd>F5</kbd> pour générer et exécuter l’application.</span><span class="sxs-lookup"><span data-stu-id="512d9-220">Press <kbd>F5</kbd> to build and run the application.</span></span> <span data-ttu-id="512d9-221">Le contrôle hébergé ne pivote pas, mais ses éléments voisins subissent une rotation de 180 degrés.</span><span class="sxs-lookup"><span data-stu-id="512d9-221">The hosted control is not rotated, but its surrounding elements are rotated by an angle of 180 degrees.</span></span> <span data-ttu-id="512d9-222">Vous devrez peut-être redimensionner la fenêtre pour apercevoir les éléments.</span><span class="sxs-lookup"><span data-stu-id="512d9-222">You may have to resize the window to see the elements.</span></span>

## <a name="setting-padding-and-margins"></a><span data-ttu-id="512d9-223">Définition d’une marge intérieure et de marges</span><span class="sxs-lookup"><span data-stu-id="512d9-223">Setting Padding and Margins</span></span>

<span data-ttu-id="512d9-224">La marge intérieure et les marges dans la disposition [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sont similaires à la marge intérieure et aux marges dans [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span><span class="sxs-lookup"><span data-stu-id="512d9-224">Padding and margins in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layout are similar to padding and margins in [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span></span> <span data-ttu-id="512d9-225">Il vous suffit de définir les propriétés <xref:System.Windows.Controls.Control.Padding%2A> et <xref:System.Windows.FrameworkElement.Margin%2A> sur l’élément <xref:System.Windows.Forms.Integration.WindowsFormsHost>.</span><span class="sxs-lookup"><span data-stu-id="512d9-225">Simply set the <xref:System.Windows.Controls.Control.Padding%2A> and <xref:System.Windows.FrameworkElement.Margin%2A> properties on the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span>

<span data-ttu-id="512d9-226">Pour définir le remplissage et les marges d’un contrôle hébergé, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="512d9-226">To set padding and margins for a hosted control, follow these steps:</span></span>

1. <span data-ttu-id="512d9-227">Copiez le code XAML suivant dans l’élément <xref:System.Windows.Controls.Grid> :</span><span class="sxs-lookup"><span data-stu-id="512d9-227">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element:</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#14](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#14)]
    [!code-xaml[WpfLayoutHostingWfWithXaml#15](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#15)]

2. <span data-ttu-id="512d9-228">Appuyez sur <kbd>F5</kbd> pour générer et exécuter l’application.</span><span class="sxs-lookup"><span data-stu-id="512d9-228">Press <kbd>F5</kbd> to build and run the application.</span></span> <span data-ttu-id="512d9-229">Les paramètres de marge intérieure et de marge sont appliqués aux contrôles [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] hébergés de la même façon que dans [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span><span class="sxs-lookup"><span data-stu-id="512d9-229">The padding and margin settings are applied to the hosted [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls in the same way they would be applied in [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span></span>

## <a name="using-dynamic-layout-containers"></a><span data-ttu-id="512d9-230">Utilisation de conteneurs de disposition dynamiques</span><span class="sxs-lookup"><span data-stu-id="512d9-230">Using Dynamic Layout Containers</span></span>

[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <span data-ttu-id="512d9-231">fournit deux conteneurs de disposition dynamique, <xref:System.Windows.Forms.FlowLayoutPanel> et <xref:System.Windows.Forms.TableLayoutPanel>.</span><span class="sxs-lookup"><span data-stu-id="512d9-231">provides two dynamic layout containers, <xref:System.Windows.Forms.FlowLayoutPanel> and <xref:System.Windows.Forms.TableLayoutPanel>.</span></span> <span data-ttu-id="512d9-232">Vous pouvez également utiliser ces conteneurs dans des dispositions @no__t 0.</span><span class="sxs-lookup"><span data-stu-id="512d9-232">You can also use these containers in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layouts.</span></span>

<span data-ttu-id="512d9-233">Pour utiliser un conteneur de disposition dynamique, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="512d9-233">To use a dynamic layout container, follow these steps:</span></span>

1. <span data-ttu-id="512d9-234">Copiez le code XAML suivant dans l’élément <xref:System.Windows.Controls.Grid> :</span><span class="sxs-lookup"><span data-stu-id="512d9-234">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element:</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#16](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#16)]

2. <span data-ttu-id="512d9-235">Dans *MainWindow. Xaml. vb* ou *MainWindow.Xaml.cs*, copiez le code suivant dans la définition de classe :</span><span class="sxs-lookup"><span data-stu-id="512d9-235">In *MainWindow.xaml.vb* or *MainWindow.xaml.cs*, copy the following code into the class definition:</span></span>

     [!code-csharp[WpfLayoutHostingWfWithXaml#103](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#103)]
     [!code-vb[WpfLayoutHostingWfWithXaml#103](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#103)]

3. <span data-ttu-id="512d9-236">Ajoutez un appel à la méthode `InitializeFlowLayoutPanel` dans le constructeur :</span><span class="sxs-lookup"><span data-stu-id="512d9-236">Add a call to the `InitializeFlowLayoutPanel` method in the constructor:</span></span>

     [!code-csharp[WpfLayoutHostingWfWithXaml#104](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#104)]
     [!code-vb[WpfLayoutHostingWfWithXaml#104](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#104)]

4. <span data-ttu-id="512d9-237">Appuyez sur <kbd>F5</kbd> pour générer et exécuter l’application.</span><span class="sxs-lookup"><span data-stu-id="512d9-237">Press <kbd>F5</kbd> to build and run the application.</span></span> <span data-ttu-id="512d9-238">L’élément <xref:System.Windows.Forms.Integration.WindowsFormsHost> remplit la <xref:System.Windows.Controls.DockPanel>, et <xref:System.Windows.Forms.FlowLayoutPanel> réorganise ses contrôles enfants dans le @no__t par défaut.</span><span class="sxs-lookup"><span data-stu-id="512d9-238">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element fills the <xref:System.Windows.Controls.DockPanel>, and <xref:System.Windows.Forms.FlowLayoutPanel> arranges its child controls in the default <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A>.</span></span>

## <a name="see-also"></a><span data-ttu-id="512d9-239">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="512d9-239">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="512d9-240">Concevoir en XAML dans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="512d9-240">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)
- [<span data-ttu-id="512d9-241">Considérations sur la disposition de l’élément WindowsFormsHost</span><span class="sxs-lookup"><span data-stu-id="512d9-241">Layout Considerations for the WindowsFormsHost Element</span></span>](layout-considerations-for-the-windowsformshost-element.md)
- [<span data-ttu-id="512d9-242">Organiser des contrôles de Windows Forms dans WPF, exemple</span><span class="sxs-lookup"><span data-stu-id="512d9-242">Arranging Windows Forms Controls in WPF Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=159971)
- <span data-ttu-id="512d9-243">[Procédure pas à pas : Hébergement d’un contrôle composite Windows Forms dans WPF @ no__t-0</span><span class="sxs-lookup"><span data-stu-id="512d9-243">[Walkthrough: Hosting a Windows Forms Composite Control in WPF](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)</span></span>
- <span data-ttu-id="512d9-244">[Procédure pas à pas : Hébergement d’un contrôle composite WPF dans Windows Forms @ no__t-0</span><span class="sxs-lookup"><span data-stu-id="512d9-244">[Walkthrough: Hosting a WPF Composite Control in Windows Forms](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)</span></span>
