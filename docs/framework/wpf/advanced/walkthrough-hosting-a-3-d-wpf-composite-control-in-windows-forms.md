---
title: 'Procédure pas à pas : hébergement d’un contrôle composite WPF 3D dans Windows Forms'
ms.date: 08/18/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosting WPF content in Windows Forms [WPF]
- composite controls [WPF], hosting WPF in
ms.assetid: 486369a9-606a-4a3b-b086-a06f2119c7b0
ms.openlocfilehash: a35f2b4062edb18914c55046a69dcd9b8825d778
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71353843"
---
# <a name="walkthrough-hosting-a-3-d-wpf-composite-control-in-windows-forms"></a><span data-ttu-id="1c012-102">Procédure pas à pas : hébergement d’un contrôle composite WPF 3D dans Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1c012-102">Walkthrough: Hosting a 3-D WPF Composite Control in Windows Forms</span></span>

<span data-ttu-id="1c012-103">Cette procédure pas à pas montre comment vous pouvez créer un contrôle composite [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] et l’héberger dans des contrôles et des formulaires [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] à l’aide du contrôle <xref:System.Windows.Forms.Integration.ElementHost>.</span><span class="sxs-lookup"><span data-stu-id="1c012-103">This walkthrough demonstrates how you can create a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] composite control and host it in [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls and forms by using the <xref:System.Windows.Forms.Integration.ElementHost> control.</span></span>

<span data-ttu-id="1c012-104">Dans cette procédure pas à pas, vous allez implémenter une [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> qui contient deux contrôles enfants.</span><span class="sxs-lookup"><span data-stu-id="1c012-104">In this walkthrough, you will implement a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> that contains two child controls.</span></span> <span data-ttu-id="1c012-105">La <xref:System.Windows.Controls.UserControl> affiche un cône tridimensionnel (3d).</span><span class="sxs-lookup"><span data-stu-id="1c012-105">The <xref:System.Windows.Controls.UserControl> displays a three-dimensional (3-D) cone.</span></span> <span data-ttu-id="1c012-106">Le rendu des objets 3D est beaucoup plus facile avec le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] qu’avec [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1c012-106">Rendering 3-D objects is much easier with the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] than with [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span></span> <span data-ttu-id="1c012-107">Par conséquent, il est logique d’héberger une classe [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> pour créer des graphiques 3D dans [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1c012-107">Therefore, it makes sense to host a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> class to create 3-D graphics in [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span></span>

<span data-ttu-id="1c012-108">Cette procédure pas à pas décrit notamment les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="1c012-108">Tasks illustrated in this walkthrough include:</span></span>

- <span data-ttu-id="1c012-109">Création du [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl>.</span><span class="sxs-lookup"><span data-stu-id="1c012-109">Creating the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl>.</span></span>

- <span data-ttu-id="1c012-110">Création du projet Windows Forms Host.</span><span class="sxs-lookup"><span data-stu-id="1c012-110">Creating the Windows Forms host project.</span></span>

- <span data-ttu-id="1c012-111">Hébergement du [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl>.</span><span class="sxs-lookup"><span data-stu-id="1c012-111">Hosting the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl>.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="1c012-112">Prérequis</span><span class="sxs-lookup"><span data-stu-id="1c012-112">Prerequisites</span></span>

<span data-ttu-id="1c012-113">Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :</span><span class="sxs-lookup"><span data-stu-id="1c012-113">You need the following components to complete this walkthrough:</span></span>

- <span data-ttu-id="1c012-114">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="1c012-114">Visual Studio 2017</span></span>

<a name="To_Create_the_UserControl"></a>
## <a name="create-the-usercontrol"></a><span data-ttu-id="1c012-115">Créer le UserControl</span><span class="sxs-lookup"><span data-stu-id="1c012-115">Create the UserControl</span></span>

1. <span data-ttu-id="1c012-116">Créez un projet de **bibliothèque de contrôles utilisateur WPF** nommé `HostingWpfUserControlInWf`.</span><span class="sxs-lookup"><span data-stu-id="1c012-116">Create a **WPF User Control Library** project named `HostingWpfUserControlInWf`.</span></span>

2. <span data-ttu-id="1c012-117">Ouvrez UserControl1. xaml dans le [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1c012-117">Open UserControl1.xaml in the [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span></span>

3. <span data-ttu-id="1c012-118">Remplacez le code généré par le code suivant :</span><span class="sxs-lookup"><span data-stu-id="1c012-118">Replace the generated code with the following code:</span></span>

     [!code-xaml[HostingWpfUserControlInWf#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWpfUserControlInWf/CSharp/HostingWpfUserControlInWf/ConeControl.xaml#1)]

     <span data-ttu-id="1c012-119">Ce code définit un <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType> qui contient deux contrôles enfants.</span><span class="sxs-lookup"><span data-stu-id="1c012-119">This code defines a <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType> that contains two child controls.</span></span> <span data-ttu-id="1c012-120">Le premier contrôle enfant est un contrôle <xref:System.Windows.Controls.Label?displayProperty=nameWithType> ; le deuxième est un contrôle <xref:System.Windows.Controls.Viewport3D> qui affiche un cône 3D.</span><span class="sxs-lookup"><span data-stu-id="1c012-120">The first child control is a <xref:System.Windows.Controls.Label?displayProperty=nameWithType> control; the second is a <xref:System.Windows.Controls.Viewport3D> control that displays a 3-D cone.</span></span>

<a name="To_Create_the_Windows_Forms_Host_Project"></a>
## <a name="create-the-host-project"></a><span data-ttu-id="1c012-121">Créer le projet hôte</span><span class="sxs-lookup"><span data-stu-id="1c012-121">Create the host project</span></span>

1. <span data-ttu-id="1c012-122">Ajoutez un projet **Windows Forms App (.NET Framework)** nommé `WpfUserControlHost` à la solution.</span><span class="sxs-lookup"><span data-stu-id="1c012-122">Add a **Windows Forms App (.NET Framework)** project named `WpfUserControlHost` to the solution.</span></span>

2. <span data-ttu-id="1c012-123">Dans **Explorateur de solutions**, ajoutez une référence à l’assembly windowsformsintegration, nommé windowsformsintegration. dll.</span><span class="sxs-lookup"><span data-stu-id="1c012-123">In **Solution Explorer**, add a reference to the WindowsFormsIntegration assembly, which is named WindowsFormsIntegration.dll.</span></span>

3. <span data-ttu-id="1c012-124">Ajoutez des références aux assemblys [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] suivants :</span><span class="sxs-lookup"><span data-stu-id="1c012-124">Add references to the following [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] assemblies:</span></span>

    - <span data-ttu-id="1c012-125">PresentationCore</span><span class="sxs-lookup"><span data-stu-id="1c012-125">PresentationCore</span></span>

    - <span data-ttu-id="1c012-126">PresentationFramework</span><span class="sxs-lookup"><span data-stu-id="1c012-126">PresentationFramework</span></span>

    - <span data-ttu-id="1c012-127">WindowsBase</span><span class="sxs-lookup"><span data-stu-id="1c012-127">WindowsBase</span></span>

4. <span data-ttu-id="1c012-128">Ajoutez au projet une référence à `HostingWpfUserControlInWf`.</span><span class="sxs-lookup"><span data-stu-id="1c012-128">Add a reference to the `HostingWpfUserControlInWf` project.</span></span>

5. <span data-ttu-id="1c012-129">Dans Explorateur de solutions, définissez le projet `WpfUserControlHost` comme projet de démarrage.</span><span class="sxs-lookup"><span data-stu-id="1c012-129">In Solution Explorer, set the `WpfUserControlHost` project to be the startup project.</span></span>

<a name="To_Host_the_Windows_Presentation_Foundation"></a>
## <a name="host-the-usercontrol"></a><span data-ttu-id="1c012-130">Héberger le UserControl</span><span class="sxs-lookup"><span data-stu-id="1c012-130">Host the UserControl</span></span>

1. <span data-ttu-id="1c012-131">Dans le Concepteur Windows Forms, ouvrez Form1.</span><span class="sxs-lookup"><span data-stu-id="1c012-131">In the Windows Forms Designer, open Form1.</span></span>

2. <span data-ttu-id="1c012-132">Dans l’Fenêtre Propriétés, cliquez sur **événements**, puis double-cliquez sur l’événement <xref:System.Windows.Forms.Form.Load> pour créer un gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="1c012-132">In the Properties window, click **Events**, and then double-click the <xref:System.Windows.Forms.Form.Load> event to create an event handler.</span></span>

     <span data-ttu-id="1c012-133">L’éditeur de code s’ouvre sur le gestionnaire d’événements `Form1_Load` qui vient d’être généré.</span><span class="sxs-lookup"><span data-stu-id="1c012-133">The Code Editor opens to the newly generated `Form1_Load` event handler.</span></span>

3. <span data-ttu-id="1c012-134">Remplacez le code dans Form1.cs par le code suivant.</span><span class="sxs-lookup"><span data-stu-id="1c012-134">Replace the code in Form1.cs with the following code.</span></span>

     <span data-ttu-id="1c012-135">Le gestionnaire d’événements `Form1_Load` crée une instance de `UserControl1` et ajoute afin à la collection de contrôles enfants du contrôle <xref:System.Windows.Forms.Integration.ElementHost>.</span><span class="sxs-lookup"><span data-stu-id="1c012-135">The `Form1_Load` event handler creates an instance of `UserControl1` and adds itto the <xref:System.Windows.Forms.Integration.ElementHost> control's collection of child controls.</span></span> <span data-ttu-id="1c012-136">Le contrôle <xref:System.Windows.Forms.Integration.ElementHost> est ajouté à la collection de contrôles enfants du formulaire.</span><span class="sxs-lookup"><span data-stu-id="1c012-136">The <xref:System.Windows.Forms.Integration.ElementHost> control is added to the form's collection of child controls.</span></span>

     [!code-csharp[HostingWpfUserControlInWf#10](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWpfUserControlInWf/CSharp/WpfUserControlHost/Form1.cs#10)]
     [!code-vb[HostingWpfUserControlInWf#10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWpfUserControlInWf/VisualBasic/WpfUserControlHost/Form1.vb#10)]

4. <span data-ttu-id="1c012-137">Appuyez sur **F5** pour générer et exécuter l’application.</span><span class="sxs-lookup"><span data-stu-id="1c012-137">Press **F5** to build and run the application.</span></span>

## <a name="see-also"></a><span data-ttu-id="1c012-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1c012-138">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="1c012-139">Concevoir en XAML dans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="1c012-139">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)
- [<span data-ttu-id="1c012-140">Procédure pas à pas : Hébergement d’un contrôle composite WPF dans Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1c012-140">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
- [<span data-ttu-id="1c012-141">Procédure pas à pas : Hébergement d’un contrôle composite Windows Forms dans WPF</span><span class="sxs-lookup"><span data-stu-id="1c012-141">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [<span data-ttu-id="1c012-142">Hébergement d’un contrôle composite WPF dans Windows Forms exemple</span><span class="sxs-lookup"><span data-stu-id="1c012-142">Hosting a WPF Composite Control in Windows Forms Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=160001)
