---
title: Héberger un contrôle de Windows Forms dans WPF
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosting Windows Forms control in WPF [WPF]
ms.assetid: 9cb88415-39b0-4c46-80c4-ff325b674286
ms.openlocfilehash: 5e994f65c0665a5726c4c8c19141da5ea3f5e6f6
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794182"
---
# <a name="walkthrough-hosting-a-windows-forms-control-in-wpf"></a><span data-ttu-id="035d0-102">Procédure pas à pas : hébergement d'un contrôle Windows Forms dans WPF</span><span class="sxs-lookup"><span data-stu-id="035d0-102">Walkthrough: Hosting a Windows Forms Control in WPF</span></span>

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <span data-ttu-id="035d0-103">fournit de nombreux contrôles avec un ensemble complet de fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="035d0-103">provides many controls with a rich feature set.</span></span> <span data-ttu-id="035d0-104">Toutefois, vous souhaiterez peut-être parfois utiliser des contrôles de Windows Forms sur vos pages [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="035d0-104">However, you may sometimes want to use Windows Forms controls on your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pages.</span></span> <span data-ttu-id="035d0-105">Par exemple, vous pouvez avoir un investissement important dans les contrôles de Windows Forms existants, ou vous pouvez avoir un contrôle Windows Forms qui fournit des fonctionnalités uniques.</span><span class="sxs-lookup"><span data-stu-id="035d0-105">For example, you may have a substantial investment in existing Windows Forms controls, or you may have a Windows Forms control that provides unique functionality.</span></span>

<span data-ttu-id="035d0-106">Cette procédure pas à pas vous montre comment héberger un contrôle Windows Forms <xref:System.Windows.Forms.MaskedTextBox?displayProperty=nameWithType> sur une page [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] à l’aide de code.</span><span class="sxs-lookup"><span data-stu-id="035d0-106">This walkthrough shows you how to host a Windows Forms <xref:System.Windows.Forms.MaskedTextBox?displayProperty=nameWithType> control on a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] page by using code.</span></span>

<span data-ttu-id="035d0-107">Pour obtenir le code complet des tâches illustrées dans cette procédure pas à pas, consultez [hébergement d’un contrôle de Windows Forms dans l’exemple WPF](https://go.microsoft.com/fwlink/?LinkID=160057).</span><span class="sxs-lookup"><span data-stu-id="035d0-107">For a complete code listing of the tasks shown in this walkthrough, see [Hosting a Windows Forms Control in WPF Sample](https://go.microsoft.com/fwlink/?LinkID=160057).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="035d0-108">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="035d0-108">Prerequisites</span></span>

<span data-ttu-id="035d0-109">Cette procédure pas à pas nécessite Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="035d0-109">You need Visual Studio to complete this walkthrough.</span></span>

## <a name="hosting-the-windows-forms-control"></a><span data-ttu-id="035d0-110">Hébergement d’un contrôle Windows Forms</span><span class="sxs-lookup"><span data-stu-id="035d0-110">Hosting the Windows Forms Control</span></span>

### <a name="to-host-the-maskedtextbox-control"></a><span data-ttu-id="035d0-111">Pour héberger le contrôle MaskedTextBox</span><span class="sxs-lookup"><span data-stu-id="035d0-111">To host the MaskedTextBox control</span></span>

1. <span data-ttu-id="035d0-112">Créez un projet d’application WPF nommé `HostingWfInWpf`.</span><span class="sxs-lookup"><span data-stu-id="035d0-112">Create a WPF Application project named `HostingWfInWpf`.</span></span>

2. <span data-ttu-id="035d0-113">Ajoutez les références aux assemblys suivants.</span><span class="sxs-lookup"><span data-stu-id="035d0-113">Add references to the following assemblies.</span></span>

    - <span data-ttu-id="035d0-114">WindowsFormsIntegration</span><span class="sxs-lookup"><span data-stu-id="035d0-114">WindowsFormsIntegration</span></span>

    - <span data-ttu-id="035d0-115">System.Windows.Forms</span><span class="sxs-lookup"><span data-stu-id="035d0-115">System.Windows.Forms</span></span>

3. <span data-ttu-id="035d0-116">Ouvrez MainWindow. xaml dans le Concepteur WPF.</span><span class="sxs-lookup"><span data-stu-id="035d0-116">Open MainWindow.xaml in the WPF Designer.</span></span>

4. <span data-ttu-id="035d0-117">Nommez l’élément <xref:System.Windows.Controls.Grid> `grid1`.</span><span class="sxs-lookup"><span data-stu-id="035d0-117">Name the <xref:System.Windows.Controls.Grid> element `grid1`.</span></span>

     [!code-xaml[HostingWfInWPF#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWPF/CSharp/HostingWfInWPF/Window1.xaml#1)]

5. <span data-ttu-id="035d0-118">En Mode Création ou en mode XAML, sélectionnez l’élément <xref:System.Windows.Window>.</span><span class="sxs-lookup"><span data-stu-id="035d0-118">In Design view or XAML view, select the <xref:System.Windows.Window> element.</span></span>

6. <span data-ttu-id="035d0-119">Dans l’Fenêtre Propriétés, cliquez sur l’onglet **événements** .</span><span class="sxs-lookup"><span data-stu-id="035d0-119">In the Properties window, click the **Events** tab.</span></span>

7. <span data-ttu-id="035d0-120">Double-cliquez sur l’événement <xref:System.Windows.FrameworkElement.Loaded>.</span><span class="sxs-lookup"><span data-stu-id="035d0-120">Double-click the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span>

8. <span data-ttu-id="035d0-121">Insérez le code suivant pour gérer l’événement <xref:System.Windows.FrameworkElement.Loaded>.</span><span class="sxs-lookup"><span data-stu-id="035d0-121">Insert the following code to handle the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span>

     [!code-csharp[HostingWfInWPF#10](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWPF/CSharp/HostingWfInWPF/Window1.xaml.cs#10)]
     [!code-vb[HostingWfInWPF#10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWfInWPF/VisualBasic/HostingWfInWpf/Window1.xaml.vb#10)]

9. <span data-ttu-id="035d0-122">En haut du fichier, ajoutez l’instruction `Imports` ou `using` suivante.</span><span class="sxs-lookup"><span data-stu-id="035d0-122">At the top of the file, add the following `Imports` or `using` statement.</span></span>

     [!code-csharp[HostingWfInWPF#11](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWPF/CSharp/HostingWfInWPF/Window1.xaml.cs#11)]
     [!code-vb[HostingWfInWPF#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWfInWPF/VisualBasic/HostingWfInWpf/Window1.xaml.vb#11)]

10. <span data-ttu-id="035d0-123">Appuyez sur **F5** pour générer et exécuter l’application.</span><span class="sxs-lookup"><span data-stu-id="035d0-123">Press **F5** to build and run the application.</span></span>

## <a name="see-also"></a><span data-ttu-id="035d0-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="035d0-124">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="035d0-125">Concevoir en XAML dans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="035d0-125">Design XAML in Visual Studio</span></span>](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [<span data-ttu-id="035d0-126">Procédure pas à pas : hébergement d’un contrôle Windows Forms dans WPF avec XAML</span><span class="sxs-lookup"><span data-stu-id="035d0-126">Walkthrough: Hosting a Windows Forms Control in WPF by Using XAML</span></span>](walkthrough-hosting-a-windows-forms-control-in-wpf-by-using-xaml.md)
- [<span data-ttu-id="035d0-127">Procédure pas à pas : hébergement d'un contrôle composite Windows Forms dans WPF</span><span class="sxs-lookup"><span data-stu-id="035d0-127">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [<span data-ttu-id="035d0-128">Procédure pas à pas : Hébergement d'un contrôle composite WPF dans Windows Forms</span><span class="sxs-lookup"><span data-stu-id="035d0-128">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
- [<span data-ttu-id="035d0-129">Contrôles Windows Forms et contrôles WPF équivalents</span><span class="sxs-lookup"><span data-stu-id="035d0-129">Windows Forms Controls and Equivalent WPF Controls</span></span>](windows-forms-controls-and-equivalent-wpf-controls.md)
- [<span data-ttu-id="035d0-130">Hébergement d’un contrôle Windows Forms dans WPF, exemple</span><span class="sxs-lookup"><span data-stu-id="035d0-130">Hosting a Windows Forms Control in WPF Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=160057)
