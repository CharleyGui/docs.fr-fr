---
title: 'Procédure pas à pas : hébergement d’un contrôle ActiveX dans WPF'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ActiveX controls [WPF interoperability]
- hosting ActiveX controls [WPF]
ms.assetid: 1931d292-0dd1-434f-963c-dcda7638d75a
ms.openlocfilehash: f19186380b0cbc71cdd64013ca5e49361ba26cda
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778382"
---
# <a name="walkthrough-hosting-an-activex-control-in-wpf"></a><span data-ttu-id="3a01b-102">Procédure pas à pas : hébergement d’un contrôle ActiveX dans WPF</span><span class="sxs-lookup"><span data-stu-id="3a01b-102">Walkthrough: Hosting an ActiveX Control in WPF</span></span>
<span data-ttu-id="3a01b-103">Pour permettre une interaction améliorée avec les navigateurs, vous pouvez utiliser [!INCLUDE[TLA#tla_actx](../../../../includes/tlasharptla-actx-md.md)] des contrôles dans votre [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-application basée sur.</span><span class="sxs-lookup"><span data-stu-id="3a01b-103">To enable improved interaction with browsers, you can use [!INCLUDE[TLA#tla_actx](../../../../includes/tlasharptla-actx-md.md)] controls in your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-based application.</span></span> <span data-ttu-id="3a01b-104">Cette procédure pas à pas montre comment vous pouvez héberger le [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)] en tant que contrôle sur une [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] page.</span><span class="sxs-lookup"><span data-stu-id="3a01b-104">This walkthrough demonstrates how you can host the [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)] as a control on a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] page.</span></span>

 <span data-ttu-id="3a01b-105">Cette procédure pas à pas décrit notamment les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="3a01b-105">Tasks illustrated in this walkthrough include:</span></span>

- <span data-ttu-id="3a01b-106">Création du projet</span><span class="sxs-lookup"><span data-stu-id="3a01b-106">Creating the project.</span></span>

- <span data-ttu-id="3a01b-107">Création du contrôle ActiveX.</span><span class="sxs-lookup"><span data-stu-id="3a01b-107">Creating the ActiveX control.</span></span>

- <span data-ttu-id="3a01b-108">Hébergement du contrôle ActiveX sur une Page WPF.</span><span class="sxs-lookup"><span data-stu-id="3a01b-108">Hosting the ActiveX control on a WPF Page.</span></span>

 <span data-ttu-id="3a01b-109">Lorsque vous avez terminé cette procédure pas à pas, vous comprendrez comment utiliser [!INCLUDE[TLA#tla_actx](../../../../includes/tlasharptla-actx-md.md)] des contrôles dans votre [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-application basée sur.</span><span class="sxs-lookup"><span data-stu-id="3a01b-109">When you have completed this walkthrough, you will understand how to use [!INCLUDE[TLA#tla_actx](../../../../includes/tlasharptla-actx-md.md)] controls in your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-based application.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="3a01b-110">Prérequis</span><span class="sxs-lookup"><span data-stu-id="3a01b-110">Prerequisites</span></span>
 <span data-ttu-id="3a01b-111">Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :</span><span class="sxs-lookup"><span data-stu-id="3a01b-111">You need the following components to complete this walkthrough:</span></span>

- [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)] <span data-ttu-id="3a01b-112">installé sur l’ordinateur où Visual Studio est installé.</span><span class="sxs-lookup"><span data-stu-id="3a01b-112">installed on the computer where Visual Studio is installed.</span></span>

- <span data-ttu-id="3a01b-113">Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="3a01b-113">Visual Studio 2010.</span></span>

## <a name="creating-the-project"></a><span data-ttu-id="3a01b-114">Création du projet</span><span class="sxs-lookup"><span data-stu-id="3a01b-114">Creating the Project</span></span>

### <a name="to-create-and-set-up-the-project"></a><span data-ttu-id="3a01b-115">Pour créer et configurer le projet</span><span class="sxs-lookup"><span data-stu-id="3a01b-115">To create and set up the project</span></span>

1. <span data-ttu-id="3a01b-116">Créez un projet d’Application WPF nommé `HostingAxInWpf`.</span><span class="sxs-lookup"><span data-stu-id="3a01b-116">Create a WPF Application project named `HostingAxInWpf`.</span></span>

2. <span data-ttu-id="3a01b-117">Ajouter un projet de bibliothèque de contrôles Windows Forms à la solution, puis nommez le projet `WmpAxLib`.</span><span class="sxs-lookup"><span data-stu-id="3a01b-117">Add a Windows Forms Control Library project to the solution, and name the project `WmpAxLib`.</span></span>

3. <span data-ttu-id="3a01b-118">Dans le projet WmpAxLib, ajoutez une référence à l’assembly Windows Media Player, nommé wmp.dll.</span><span class="sxs-lookup"><span data-stu-id="3a01b-118">In the WmpAxLib project, add a reference to the Windows Media Player assembly, which is named wmp.dll.</span></span>

4. <span data-ttu-id="3a01b-119">Ouvrez le **boîte à outils**.</span><span class="sxs-lookup"><span data-stu-id="3a01b-119">Open the **Toolbox**.</span></span>

5. <span data-ttu-id="3a01b-120">Avec le bouton droit dans le **boîte à outils**, puis cliquez sur **choisir des éléments de**.</span><span class="sxs-lookup"><span data-stu-id="3a01b-120">Right-click in the **Toolbox**, and then click **Choose Items**.</span></span>

6. <span data-ttu-id="3a01b-121">Cliquez sur le **composants COM** onglet, sélectionnez le **Windows Media Player** contrôler, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="3a01b-121">Click the **COM Components** tab, select the **Windows Media Player** control, and then click **OK**.</span></span>

     <span data-ttu-id="3a01b-122">Le contrôle Windows Media Player est ajouté à la **boîte à outils**.</span><span class="sxs-lookup"><span data-stu-id="3a01b-122">The Windows Media Player control is added to the **Toolbox**.</span></span>

7. <span data-ttu-id="3a01b-123">Dans l’Explorateur de solutions, cliquez sur le **UserControl1** de fichiers, puis cliquez sur **renommer**.</span><span class="sxs-lookup"><span data-stu-id="3a01b-123">In Solution Explorer, right-click the **UserControl1** file, and then click **Rename**.</span></span>

8. <span data-ttu-id="3a01b-124">Remplacez le nom par `WmpAxControl.vb` ou `WmpAxControl.cs`, selon le langage.</span><span class="sxs-lookup"><span data-stu-id="3a01b-124">Change the name to `WmpAxControl.vb` or `WmpAxControl.cs`, depending on the language.</span></span>

9. <span data-ttu-id="3a01b-125">Si vous êtes invité à renommer toutes les références, cliquez sur **Oui**.</span><span class="sxs-lookup"><span data-stu-id="3a01b-125">If you are prompted to rename all references, click **Yes**.</span></span>

## <a name="creating-the-activex-control"></a><span data-ttu-id="3a01b-126">Création du contrôle ActiveX</span><span class="sxs-lookup"><span data-stu-id="3a01b-126">Creating the ActiveX Control</span></span>
 [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] <span data-ttu-id="3a01b-127">génère automatiquement un <xref:System.Windows.Forms.AxHost> classe wrapper pour un [!INCLUDE[TLA#tla_actx](../../../../includes/tlasharptla-actx-md.md)] contrôler quand le contrôle est ajouté à une aire de conception.</span><span class="sxs-lookup"><span data-stu-id="3a01b-127">automatically generates an <xref:System.Windows.Forms.AxHost> wrapper class for a [!INCLUDE[TLA#tla_actx](../../../../includes/tlasharptla-actx-md.md)] control when the control is added to a design surface.</span></span> <span data-ttu-id="3a01b-128">La procédure suivante crée un assembly managé nommé AxInterop.WMPLib.dll.</span><span class="sxs-lookup"><span data-stu-id="3a01b-128">The following procedure creates a managed assembly named AxInterop.WMPLib.dll.</span></span>

### <a name="to-create-the-activex-control"></a><span data-ttu-id="3a01b-129">Pour créer le contrôle ActiveX</span><span class="sxs-lookup"><span data-stu-id="3a01b-129">To create the ActiveX control</span></span>

1. <span data-ttu-id="3a01b-130">Ouvrez WmpAxControl.cs ou WmpAxControl.vb dans le Concepteur de formulaires Windows.</span><span class="sxs-lookup"><span data-stu-id="3a01b-130">Open WmpAxControl.vb or WmpAxControl.cs in the Windows Forms Designer.</span></span>

2. <span data-ttu-id="3a01b-131">À partir de la **boîte à outils**, ajoutez le contrôle Windows Media Player à l’aire de conception.</span><span class="sxs-lookup"><span data-stu-id="3a01b-131">From the **Toolbox**, add the Windows Media Player control to the design surface.</span></span>

3. <span data-ttu-id="3a01b-132">Dans la fenêtre Propriétés, définissez la valeur du contrôle Windows Media Player <xref:System.Windows.Forms.Control.Dock%2A> propriété <xref:System.Windows.Forms.DockStyle.Fill>.</span><span class="sxs-lookup"><span data-stu-id="3a01b-132">In the Properties window, set the value of the Windows Media Player control's <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>

4. <span data-ttu-id="3a01b-133">Générez le projet de bibliothèque de contrôle WmpAxLib.</span><span class="sxs-lookup"><span data-stu-id="3a01b-133">Build the WmpAxLib control library project.</span></span>

## <a name="hosting-the-activex-control-on-a-wpf-page"></a><span data-ttu-id="3a01b-134">Hébergement du contrôle ActiveX sur une Page WPF</span><span class="sxs-lookup"><span data-stu-id="3a01b-134">Hosting the ActiveX Control on a WPF Page</span></span>

### <a name="to-host-the-activex-control"></a><span data-ttu-id="3a01b-135">Pour héberger le contrôle ActiveX</span><span class="sxs-lookup"><span data-stu-id="3a01b-135">To host the ActiveX control</span></span>

1. <span data-ttu-id="3a01b-136">Dans le projet HostingAxInWpf, ajoutez une référence à la generated [!INCLUDE[TLA2#tla_actx](../../../../includes/tla2sharptla-actx-md.md)] assembly d’interopérabilité.</span><span class="sxs-lookup"><span data-stu-id="3a01b-136">In the HostingAxInWpf project, add a reference to the generated [!INCLUDE[TLA2#tla_actx](../../../../includes/tla2sharptla-actx-md.md)] interoperability assembly.</span></span>

     <span data-ttu-id="3a01b-137">Cet assembly est nommé AxInterop.WMPLib.dll et a été ajouté au dossier Debug du projet WmpAxLib lorsque vous avez importé le contrôle Windows Media Player.</span><span class="sxs-lookup"><span data-stu-id="3a01b-137">This assembly is named AxInterop.WMPLib.dll and was added to the Debug folder of the WmpAxLib project when you imported the Windows Media Player control.</span></span>

2. <span data-ttu-id="3a01b-138">Ajoutez une référence à l’assembly WindowsFormsIntegration, nommé WindowsFormsIntegration.dll.</span><span class="sxs-lookup"><span data-stu-id="3a01b-138">Add a reference to the WindowsFormsIntegration assembly, which is named WindowsFormsIntegration.dll.</span></span>

3. <span data-ttu-id="3a01b-139">Ajoutez une référence à la [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] assembly nommé System.Windows.Forms.dll.</span><span class="sxs-lookup"><span data-stu-id="3a01b-139">Add a reference to the [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] assembly, which is named System.Windows.Forms.dll.</span></span>

4. <span data-ttu-id="3a01b-140">Ouvrez MainWindow.xaml dans le Concepteur WPF.</span><span class="sxs-lookup"><span data-stu-id="3a01b-140">Open MainWindow.xaml in the WPF Designer.</span></span>

5. <span data-ttu-id="3a01b-141">Nom de la <xref:System.Windows.Controls.Grid> élément `grid1`.</span><span class="sxs-lookup"><span data-stu-id="3a01b-141">Name the <xref:System.Windows.Controls.Grid> element `grid1`.</span></span>

     [!code-xaml[HostingAxInWpf#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingAxInWpf/CSharp/HostingAxInWpf/window1.xaml#1)]

6. <span data-ttu-id="3a01b-142">Dans le mode Création ou XAML, sélectionnez le <xref:System.Windows.Window> élément.</span><span class="sxs-lookup"><span data-stu-id="3a01b-142">In Design view or XAML view, select the <xref:System.Windows.Window> element.</span></span>

7. <span data-ttu-id="3a01b-143">Dans la fenêtre Propriétés, cliquez sur le **événements** onglet.</span><span class="sxs-lookup"><span data-stu-id="3a01b-143">In the Properties window, click the **Events** tab.</span></span>

8. <span data-ttu-id="3a01b-144">Double-cliquez sur le <xref:System.Windows.FrameworkElement.Loaded> événement.</span><span class="sxs-lookup"><span data-stu-id="3a01b-144">Double-click the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span>

9. <span data-ttu-id="3a01b-145">Insérez le code suivant pour gérer les <xref:System.Windows.FrameworkElement.Loaded> événement.</span><span class="sxs-lookup"><span data-stu-id="3a01b-145">Insert the following code to handle the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span>

     <span data-ttu-id="3a01b-146">Ce code crée une instance de la <xref:System.Windows.Forms.Integration.WindowsFormsHost> contrôler et ajoute une instance de la `AxWindowsMediaPlayer` contrôle en tant qu’enfant.</span><span class="sxs-lookup"><span data-stu-id="3a01b-146">This code creates an instance of the <xref:System.Windows.Forms.Integration.WindowsFormsHost> control and adds an instance of the `AxWindowsMediaPlayer` control as its child.</span></span>

     [!code-csharp[HostingAxInWpf#11](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingAxInWpf/CSharp/HostingAxInWpf/window1.xaml.cs#11)]
     [!code-vb[HostingAxInWpf#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HostingAxInWpf/VisualBasic/HostingAxInWpf/window1.xaml.vb#11)]  
  
10. <span data-ttu-id="3a01b-147">Appuyez sur F5 pour générer et exécuter l'application.</span><span class="sxs-lookup"><span data-stu-id="3a01b-147">Press F5 to build and run the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a01b-148">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3a01b-148">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="3a01b-149">Concevoir en XAML dans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="3a01b-149">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)
- [<span data-ttu-id="3a01b-150">Procédure pas à pas : Hébergement d’un contrôle Composite de formulaires Windows dans WPF</span><span class="sxs-lookup"><span data-stu-id="3a01b-150">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [<span data-ttu-id="3a01b-151">Procédure pas à pas : Hébergement d’un contrôle Composite WPF dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3a01b-151">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
