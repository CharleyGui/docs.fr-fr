---
title: Héberger un contrôle ActiveX dans WPF
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ActiveX controls [WPF interoperability]
- hosting ActiveX controls [WPF]
ms.assetid: 1931d292-0dd1-434f-963c-dcda7638d75a
ms.openlocfilehash: 4ca40c0f6e62fd413e7f305649c5c01ddc152b2a
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794148"
---
# <a name="walkthrough-hosting-an-activex-control-in-wpf"></a><span data-ttu-id="a03e7-102">Procédure pas à pas : hébergement d'un contrôle ActiveX dans WPF</span><span class="sxs-lookup"><span data-stu-id="a03e7-102">Walkthrough: Hosting an ActiveX Control in WPF</span></span>
<span data-ttu-id="a03e7-103">Pour permettre une meilleure interaction avec les navigateurs, vous pouvez utiliser les contrôles Microsoft ActiveX dans votre application [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a03e7-103">To enable improved interaction with browsers, you can use Microsoft ActiveX controls in your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-based application.</span></span> <span data-ttu-id="a03e7-104">Cette procédure pas à pas montre comment vous pouvez héberger le lecteur Microsoft Windows Media comme un contrôle sur une page de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a03e7-104">This walkthrough demonstrates how you can host the Microsoft Windows Media Player as a control on a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] page.</span></span>

 <span data-ttu-id="a03e7-105">Cette procédure pas à pas décrit notamment les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="a03e7-105">Tasks illustrated in this walkthrough include:</span></span>

- <span data-ttu-id="a03e7-106">Création du projet.</span><span class="sxs-lookup"><span data-stu-id="a03e7-106">Creating the project.</span></span>

- <span data-ttu-id="a03e7-107">Création du contrôle ActiveX.</span><span class="sxs-lookup"><span data-stu-id="a03e7-107">Creating the ActiveX control.</span></span>

- <span data-ttu-id="a03e7-108">Hébergement du contrôle ActiveX sur une page WPF.</span><span class="sxs-lookup"><span data-stu-id="a03e7-108">Hosting the ActiveX control on a WPF Page.</span></span>

 <span data-ttu-id="a03e7-109">Une fois cette procédure pas à pas terminée, vous comprendrez comment utiliser les contrôles Microsoft ActiveX dans votre application [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a03e7-109">When you have completed this walkthrough, you will understand how to use Microsoft ActiveX controls in your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-based application.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="a03e7-110">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="a03e7-110">Prerequisites</span></span>
 <span data-ttu-id="a03e7-111">Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :</span><span class="sxs-lookup"><span data-stu-id="a03e7-111">You need the following components to complete this walkthrough:</span></span>

- <span data-ttu-id="a03e7-112">Lecteur Microsoft Windows Media installé sur l’ordinateur sur lequel Visual Studio est installé.</span><span class="sxs-lookup"><span data-stu-id="a03e7-112">Microsoft Windows Media Player installed on the computer where Visual Studio is installed.</span></span>

- <span data-ttu-id="a03e7-113">Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="a03e7-113">Visual Studio 2010.</span></span>

## <a name="creating-the-project"></a><span data-ttu-id="a03e7-114">Création du projet</span><span class="sxs-lookup"><span data-stu-id="a03e7-114">Creating the Project</span></span>

### <a name="to-create-and-set-up-the-project"></a><span data-ttu-id="a03e7-115">Pour créer et configurer le projet</span><span class="sxs-lookup"><span data-stu-id="a03e7-115">To create and set up the project</span></span>

1. <span data-ttu-id="a03e7-116">Créez un projet d’application WPF nommé `HostingAxInWpf`.</span><span class="sxs-lookup"><span data-stu-id="a03e7-116">Create a WPF Application project named `HostingAxInWpf`.</span></span>

2. <span data-ttu-id="a03e7-117">Ajoutez un projet de bibliothèque de contrôles Windows Forms à la solution et nommez le projet `WmpAxLib`.</span><span class="sxs-lookup"><span data-stu-id="a03e7-117">Add a Windows Forms Control Library project to the solution, and name the project `WmpAxLib`.</span></span>

3. <span data-ttu-id="a03e7-118">Dans le projet WmpAxLib, ajoutez une référence à l’assembly du lecteur Windows Media, nommé wmp. dll.</span><span class="sxs-lookup"><span data-stu-id="a03e7-118">In the WmpAxLib project, add a reference to the Windows Media Player assembly, which is named wmp.dll.</span></span>

4. <span data-ttu-id="a03e7-119">Ouvrez la **boîte à outils**.</span><span class="sxs-lookup"><span data-stu-id="a03e7-119">Open the **Toolbox**.</span></span>

5. <span data-ttu-id="a03e7-120">Cliquez avec le bouton droit dans la **boîte à outils**, puis cliquez sur **choisir les éléments**.</span><span class="sxs-lookup"><span data-stu-id="a03e7-120">Right-click in the **Toolbox**, and then click **Choose Items**.</span></span>

6. <span data-ttu-id="a03e7-121">Cliquez sur l’onglet **composants com** , sélectionnez le contrôle du **lecteur Windows Media** , puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="a03e7-121">Click the **COM Components** tab, select the **Windows Media Player** control, and then click **OK**.</span></span>

     <span data-ttu-id="a03e7-122">Le contrôle du lecteur Windows Media est ajouté à la **boîte à outils**.</span><span class="sxs-lookup"><span data-stu-id="a03e7-122">The Windows Media Player control is added to the **Toolbox**.</span></span>

7. <span data-ttu-id="a03e7-123">Dans Explorateur de solutions, cliquez avec le bouton droit sur le fichier **UserControl1** , puis cliquez sur **Renommer**.</span><span class="sxs-lookup"><span data-stu-id="a03e7-123">In Solution Explorer, right-click the **UserControl1** file, and then click **Rename**.</span></span>

8. <span data-ttu-id="a03e7-124">Remplacez le nom par `WmpAxControl.vb` ou `WmpAxControl.cs`, en fonction de la langue.</span><span class="sxs-lookup"><span data-stu-id="a03e7-124">Change the name to `WmpAxControl.vb` or `WmpAxControl.cs`, depending on the language.</span></span>

9. <span data-ttu-id="a03e7-125">Si vous êtes invité à renommer toutes les références, cliquez sur **Oui**.</span><span class="sxs-lookup"><span data-stu-id="a03e7-125">If you are prompted to rename all references, click **Yes**.</span></span>

## <a name="creating-the-activex-control"></a><span data-ttu-id="a03e7-126">Création du contrôle ActiveX</span><span class="sxs-lookup"><span data-stu-id="a03e7-126">Creating the ActiveX Control</span></span>
<span data-ttu-id="a03e7-127">Visual Studio génère automatiquement une classe wrapper <xref:System.Windows.Forms.AxHost> pour un contrôle Microsoft ActiveX lorsque le contrôle est ajouté à une aire de conception.</span><span class="sxs-lookup"><span data-stu-id="a03e7-127">Visual Studio automatically generates an <xref:System.Windows.Forms.AxHost> wrapper class for a Microsoft ActiveX control when the control is added to a design surface.</span></span> <span data-ttu-id="a03e7-128">La procédure suivante crée un assembly managé nommé AxInterop. WMPLib. dll.</span><span class="sxs-lookup"><span data-stu-id="a03e7-128">The following procedure creates a managed assembly named AxInterop.WMPLib.dll.</span></span>

### <a name="to-create-the-activex-control"></a><span data-ttu-id="a03e7-129">Pour créer le contrôle ActiveX</span><span class="sxs-lookup"><span data-stu-id="a03e7-129">To create the ActiveX control</span></span>

1. <span data-ttu-id="a03e7-130">Ouvrez WmpAxControl. vb ou WmpAxControl.cs dans le Concepteur Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="a03e7-130">Open WmpAxControl.vb or WmpAxControl.cs in the Windows Forms Designer.</span></span>

2. <span data-ttu-id="a03e7-131">À partir de la **boîte à outils**, ajoutez le contrôle du lecteur Windows Media à l’aire de conception.</span><span class="sxs-lookup"><span data-stu-id="a03e7-131">From the **Toolbox**, add the Windows Media Player control to the design surface.</span></span>

3. <span data-ttu-id="a03e7-132">Dans la Fenêtre Propriétés, définissez la valeur de la propriété <xref:System.Windows.Forms.Control.Dock%2A> du contrôle du lecteur Windows Media sur <xref:System.Windows.Forms.DockStyle.Fill>.</span><span class="sxs-lookup"><span data-stu-id="a03e7-132">In the Properties window, set the value of the Windows Media Player control's <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>

4. <span data-ttu-id="a03e7-133">Générez le projet de bibliothèque de contrôles WmpAxLib.</span><span class="sxs-lookup"><span data-stu-id="a03e7-133">Build the WmpAxLib control library project.</span></span>

## <a name="hosting-the-activex-control-on-a-wpf-page"></a><span data-ttu-id="a03e7-134">Hébergement du contrôle ActiveX sur une page WPF</span><span class="sxs-lookup"><span data-stu-id="a03e7-134">Hosting the ActiveX Control on a WPF Page</span></span>

### <a name="to-host-the-activex-control"></a><span data-ttu-id="a03e7-135">Pour héberger le contrôle ActiveX</span><span class="sxs-lookup"><span data-stu-id="a03e7-135">To host the ActiveX control</span></span>

1. <span data-ttu-id="a03e7-136">Dans le projet HostingAxInWpf, ajoutez une référence à l’assembly d’interopérabilité ActiveX généré.</span><span class="sxs-lookup"><span data-stu-id="a03e7-136">In the HostingAxInWpf project, add a reference to the generated ActiveX interoperability assembly.</span></span>

     <span data-ttu-id="a03e7-137">Cet assembly se nomme AxInterop. WMPLib. dll et a été ajouté au dossier de débogage du projet WmpAxLib lorsque vous avez importé le contrôle du lecteur Windows Media.</span><span class="sxs-lookup"><span data-stu-id="a03e7-137">This assembly is named AxInterop.WMPLib.dll and was added to the Debug folder of the WmpAxLib project when you imported the Windows Media Player control.</span></span>

2. <span data-ttu-id="a03e7-138">Ajoutez une référence à l’assembly WindowsFormsIntegration, nommé WindowsFormsIntegration. dll.</span><span class="sxs-lookup"><span data-stu-id="a03e7-138">Add a reference to the WindowsFormsIntegration assembly, which is named WindowsFormsIntegration.dll.</span></span>

3. <span data-ttu-id="a03e7-139">Ajoutez une référence à l’assembly Windows Forms, nommé System. Windows. Forms. dll.</span><span class="sxs-lookup"><span data-stu-id="a03e7-139">Add a reference to the Windows Forms assembly, which is named System.Windows.Forms.dll.</span></span>

4. <span data-ttu-id="a03e7-140">Ouvrez MainWindow. xaml dans le Concepteur WPF.</span><span class="sxs-lookup"><span data-stu-id="a03e7-140">Open MainWindow.xaml in the WPF Designer.</span></span>

5. <span data-ttu-id="a03e7-141">Nommez l’élément <xref:System.Windows.Controls.Grid> `grid1`.</span><span class="sxs-lookup"><span data-stu-id="a03e7-141">Name the <xref:System.Windows.Controls.Grid> element `grid1`.</span></span>

     [!code-xaml[HostingAxInWpf#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingAxInWpf/CSharp/HostingAxInWpf/window1.xaml#1)]

6. <span data-ttu-id="a03e7-142">En Mode Création ou en mode XAML, sélectionnez l’élément <xref:System.Windows.Window>.</span><span class="sxs-lookup"><span data-stu-id="a03e7-142">In Design view or XAML view, select the <xref:System.Windows.Window> element.</span></span>

7. <span data-ttu-id="a03e7-143">Dans l’Fenêtre Propriétés, cliquez sur l’onglet **événements** .</span><span class="sxs-lookup"><span data-stu-id="a03e7-143">In the Properties window, click the **Events** tab.</span></span>

8. <span data-ttu-id="a03e7-144">Double-cliquez sur l’événement <xref:System.Windows.FrameworkElement.Loaded>.</span><span class="sxs-lookup"><span data-stu-id="a03e7-144">Double-click the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span>

9. <span data-ttu-id="a03e7-145">Insérez le code suivant pour gérer l’événement <xref:System.Windows.FrameworkElement.Loaded>.</span><span class="sxs-lookup"><span data-stu-id="a03e7-145">Insert the following code to handle the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span>

     <span data-ttu-id="a03e7-146">Ce code crée une instance du contrôle <xref:System.Windows.Forms.Integration.WindowsFormsHost> et ajoute une instance du contrôle `AxWindowsMediaPlayer` en tant qu’enfant.</span><span class="sxs-lookup"><span data-stu-id="a03e7-146">This code creates an instance of the <xref:System.Windows.Forms.Integration.WindowsFormsHost> control and adds an instance of the `AxWindowsMediaPlayer` control as its child.</span></span>

     [!code-csharp[HostingAxInWpf#11](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingAxInWpf/CSharp/HostingAxInWpf/window1.xaml.cs#11)]
     [!code-vb[HostingAxInWpf#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HostingAxInWpf/VisualBasic/HostingAxInWpf/window1.xaml.vb#11)]  
  
10. <span data-ttu-id="a03e7-147">Appuyez sur F5 pour générer et exécuter l'application.</span><span class="sxs-lookup"><span data-stu-id="a03e7-147">Press F5 to build and run the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a03e7-148">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a03e7-148">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="a03e7-149">Concevoir en XAML dans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="a03e7-149">Design XAML in Visual Studio</span></span>](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [<span data-ttu-id="a03e7-150">Procédure pas à pas : hébergement d'un contrôle composite Windows Forms dans WPF</span><span class="sxs-lookup"><span data-stu-id="a03e7-150">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [<span data-ttu-id="a03e7-151">Procédure pas à pas : Hébergement d'un contrôle composite WPF dans Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a03e7-151">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
