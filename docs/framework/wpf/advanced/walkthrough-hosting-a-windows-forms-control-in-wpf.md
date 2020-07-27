---
title: Héberger un contrôle de Windows Forms dans WPF
description: Découvrez comment héberger des contrôles de Windows Forms dans Windows Presentation Foundation, qui fournit déjà de nombreux contrôles avec un ensemble de fonctionnalités enrichi.
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosting Windows Forms control in WPF [WPF]
ms.assetid: 9cb88415-39b0-4c46-80c4-ff325b674286
ms.openlocfilehash: ec67cf9fabaa5b7aadbb2a3c21ebf8dd828ee20f
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164975"
---
# <a name="walkthrough-hosting-a-windows-forms-control-in-wpf"></a><span data-ttu-id="182ff-103">Procédure pas à pas : hébergement d’un contrôle Windows Forms dans WPF</span><span class="sxs-lookup"><span data-stu-id="182ff-103">Walkthrough: Hosting a Windows Forms Control in WPF</span></span>

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <span data-ttu-id="182ff-104">fournit de nombreux contrôles avec un ensemble complet de fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="182ff-104">provides many controls with a rich feature set.</span></span> <span data-ttu-id="182ff-105">Toutefois, vous souhaiterez peut-être parfois utiliser des contrôles de Windows Forms dans vos [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pages.</span><span class="sxs-lookup"><span data-stu-id="182ff-105">However, you may sometimes want to use Windows Forms controls on your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pages.</span></span> <span data-ttu-id="182ff-106">Par exemple, vous pouvez avoir un investissement important dans les contrôles de Windows Forms existants, ou vous pouvez avoir un contrôle Windows Forms qui fournit des fonctionnalités uniques.</span><span class="sxs-lookup"><span data-stu-id="182ff-106">For example, you may have a substantial investment in existing Windows Forms controls, or you may have a Windows Forms control that provides unique functionality.</span></span>

<span data-ttu-id="182ff-107">Cette procédure pas à pas vous montre comment héberger un <xref:System.Windows.Forms.MaskedTextBox?displayProperty=nameWithType> contrôle de Windows Forms sur une [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] page à l’aide de code.</span><span class="sxs-lookup"><span data-stu-id="182ff-107">This walkthrough shows you how to host a Windows Forms <xref:System.Windows.Forms.MaskedTextBox?displayProperty=nameWithType> control on a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] page by using code.</span></span>

<span data-ttu-id="182ff-108">Pour obtenir le code complet des tâches illustrées dans cette procédure pas à pas, consultez [hébergement d’un contrôle de Windows Forms dans l’exemple WPF](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/HostingWfInWPF).</span><span class="sxs-lookup"><span data-stu-id="182ff-108">For a complete code listing of the tasks shown in this walkthrough, see [Hosting a Windows Forms Control in WPF Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/HostingWfInWPF).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="182ff-109">Prérequis</span><span class="sxs-lookup"><span data-stu-id="182ff-109">Prerequisites</span></span>

<span data-ttu-id="182ff-110">Cette procédure pas à pas nécessite Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="182ff-110">You need Visual Studio to complete this walkthrough.</span></span>

## <a name="hosting-the-windows-forms-control"></a><span data-ttu-id="182ff-111">Hébergement d’un contrôle Windows Forms</span><span class="sxs-lookup"><span data-stu-id="182ff-111">Hosting the Windows Forms Control</span></span>

### <a name="to-host-the-maskedtextbox-control"></a><span data-ttu-id="182ff-112">Pour héberger le contrôle MaskedTextBox</span><span class="sxs-lookup"><span data-stu-id="182ff-112">To host the MaskedTextBox control</span></span>

1. <span data-ttu-id="182ff-113">Créez un projet d’application WPF nommé `HostingWfInWpf` .</span><span class="sxs-lookup"><span data-stu-id="182ff-113">Create a WPF Application project named `HostingWfInWpf`.</span></span>

2. <span data-ttu-id="182ff-114">Ajoutez les références aux assemblys suivants.</span><span class="sxs-lookup"><span data-stu-id="182ff-114">Add references to the following assemblies.</span></span>

    - <span data-ttu-id="182ff-115">WindowsFormsIntegration</span><span class="sxs-lookup"><span data-stu-id="182ff-115">WindowsFormsIntegration</span></span>

    - <span data-ttu-id="182ff-116">System.Windows.Forms</span><span class="sxs-lookup"><span data-stu-id="182ff-116">System.Windows.Forms</span></span>

3. <span data-ttu-id="182ff-117">Ouvrez MainWindow. xaml dans le Concepteur WPF.</span><span class="sxs-lookup"><span data-stu-id="182ff-117">Open MainWindow.xaml in the WPF Designer.</span></span>

4. <span data-ttu-id="182ff-118">Nommez l' <xref:System.Windows.Controls.Grid> élément `grid1` .</span><span class="sxs-lookup"><span data-stu-id="182ff-118">Name the <xref:System.Windows.Controls.Grid> element `grid1`.</span></span>

     [!code-xaml[HostingWfInWPF#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWPF/CSharp/HostingWfInWPF/Window1.xaml#1)]

5. <span data-ttu-id="182ff-119">En Mode Création ou en mode XAML, sélectionnez l' <xref:System.Windows.Window> élément.</span><span class="sxs-lookup"><span data-stu-id="182ff-119">In Design view or XAML view, select the <xref:System.Windows.Window> element.</span></span>

6. <span data-ttu-id="182ff-120">Dans l’Fenêtre Propriétés, cliquez sur l’onglet **événements** .</span><span class="sxs-lookup"><span data-stu-id="182ff-120">In the Properties window, click the **Events** tab.</span></span>

7. <span data-ttu-id="182ff-121">Double-cliquez sur l' <xref:System.Windows.FrameworkElement.Loaded> événement.</span><span class="sxs-lookup"><span data-stu-id="182ff-121">Double-click the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span>

8. <span data-ttu-id="182ff-122">Insérez le code suivant pour gérer l' <xref:System.Windows.FrameworkElement.Loaded> événement.</span><span class="sxs-lookup"><span data-stu-id="182ff-122">Insert the following code to handle the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span>

     [!code-csharp[HostingWfInWPF#10](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWPF/CSharp/HostingWfInWPF/Window1.xaml.cs#10)]
     [!code-vb[HostingWfInWPF#10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWfInWPF/VisualBasic/HostingWfInWpf/Window1.xaml.vb#10)]

9. <span data-ttu-id="182ff-123">En haut du fichier, ajoutez l' `Imports` instruction ou suivante `using` .</span><span class="sxs-lookup"><span data-stu-id="182ff-123">At the top of the file, add the following `Imports` or `using` statement.</span></span>

     [!code-csharp[HostingWfInWPF#11](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWPF/CSharp/HostingWfInWPF/Window1.xaml.cs#11)]
     [!code-vb[HostingWfInWPF#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWfInWPF/VisualBasic/HostingWfInWpf/Window1.xaml.vb#11)]

10. <span data-ttu-id="182ff-124">Appuyez sur **F5** pour générer et exécuter l’application.</span><span class="sxs-lookup"><span data-stu-id="182ff-124">Press **F5** to build and run the application.</span></span>

## <a name="see-also"></a><span data-ttu-id="182ff-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="182ff-125">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="182ff-126">Concevoir en XAML dans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="182ff-126">Design XAML in Visual Studio</span></span>](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [<span data-ttu-id="182ff-127">Procédure pas à pas : hébergement d’un contrôle Windows Forms dans WPF à l’aide de XAML</span><span class="sxs-lookup"><span data-stu-id="182ff-127">Walkthrough: Hosting a Windows Forms Control in WPF by Using XAML</span></span>](walkthrough-hosting-a-windows-forms-control-in-wpf-by-using-xaml.md)
- [<span data-ttu-id="182ff-128">Procédure pas à pas : hébergement d’un contrôle composite Windows Forms dans WPF</span><span class="sxs-lookup"><span data-stu-id="182ff-128">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [<span data-ttu-id="182ff-129">Procédure pas à pas : hébergement d’un contrôle composite WPF dans Windows Forms</span><span class="sxs-lookup"><span data-stu-id="182ff-129">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
- [<span data-ttu-id="182ff-130">Contrôles Windows Forms et contrôles WPF équivalents</span><span class="sxs-lookup"><span data-stu-id="182ff-130">Windows Forms Controls and Equivalent WPF Controls</span></span>](windows-forms-controls-and-equivalent-wpf-controls.md)
- [<span data-ttu-id="182ff-131">Hébergement d’un contrôle Windows Forms dans WPF, exemple</span><span class="sxs-lookup"><span data-stu-id="182ff-131">Hosting a Windows Forms Control in WPF Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/HostingWfInWPF)
