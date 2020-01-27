---
title: Héberger un contrôle de Windows Forms dans WPF à l’aide de XAML
titleSuffix: ''
ms.date: 03/30/2017
helpviewer_keywords:
- hosting Windows Forms control in WPF [WPF]
ms.assetid: 1aef42cb-4cfb-44b4-9a7a-c02632d3d9c7
ms.openlocfilehash: a0a88c39a25e5292365a6447cefdd8f31db5e5c3
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744922"
---
# <a name="walkthrough-hosting-a-windows-forms-control-in-wpf-by-using-xaml"></a><span data-ttu-id="770e4-102">Procédure pas à pas : hébergement d'un contrôle Windows Forms dans WPF avec XAML</span><span class="sxs-lookup"><span data-stu-id="770e4-102">Walkthrough: Hosting a Windows Forms Control in WPF by Using XAML</span></span>
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <span data-ttu-id="770e4-103">fournit de nombreux contrôles avec un ensemble complet de fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="770e4-103">provides many controls with a rich feature set.</span></span> <span data-ttu-id="770e4-104">Toutefois, vous souhaiterez peut-être parfois utiliser des contrôles de [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] sur vos pages [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="770e4-104">However, you may sometimes want to use [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls on your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pages.</span></span> <span data-ttu-id="770e4-105">Par exemple, vous pouvez avoir un investissement important dans les contrôles de [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] existants, ou vous pouvez avoir un contrôle [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] qui fournit des fonctionnalités uniques.</span><span class="sxs-lookup"><span data-stu-id="770e4-105">For example, you may have a substantial investment in existing [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls, or you may have a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control that provides unique functionality.</span></span>  
  
 <span data-ttu-id="770e4-106">Cette procédure pas à pas vous montre comment héberger un contrôle Windows Forms <xref:System.Windows.Forms.MaskedTextBox?displayProperty=nameWithType> sur une page [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] à l’aide de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="770e4-106">This walkthrough shows you how to host a Windows Forms <xref:System.Windows.Forms.MaskedTextBox?displayProperty=nameWithType> control on a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] page by using [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span>  
  
 <span data-ttu-id="770e4-107">Pour obtenir le code complet des tâches illustrées dans cette procédure pas à pas, consultez [hébergement d’un contrôle de Windows Forms dans WPF à l’aide de l’exemple XAML](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/HostingWfInWpfWithXaml).</span><span class="sxs-lookup"><span data-stu-id="770e4-107">For a complete code listing of the tasks shown in this walkthrough, see [Hosting a Windows Forms Control in WPF by Using XAML Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/HostingWfInWpfWithXaml).</span></span>
  
## <a name="prerequisites"></a><span data-ttu-id="770e4-108">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="770e4-108">Prerequisites</span></span>  

<span data-ttu-id="770e4-109">Cette procédure pas à pas nécessite Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="770e4-109">You need Visual Studio to complete this walkthrough.</span></span>  
  
## <a name="hosting-the-windows-forms-control"></a><span data-ttu-id="770e4-110">Hébergement d’un contrôle Windows Forms</span><span class="sxs-lookup"><span data-stu-id="770e4-110">Hosting the Windows Forms Control</span></span>  
  
#### <a name="to-host-the-maskedtextbox-control"></a><span data-ttu-id="770e4-111">Pour héberger le contrôle MaskedTextBox</span><span class="sxs-lookup"><span data-stu-id="770e4-111">To host the MaskedTextBox control</span></span>  
  
1. <span data-ttu-id="770e4-112">Créez un projet d’application WPF nommé `HostingWfInWpfWithXaml`.</span><span class="sxs-lookup"><span data-stu-id="770e4-112">Create a WPF Application project named `HostingWfInWpfWithXaml`.</span></span>  
  
2. <span data-ttu-id="770e4-113">Ajoutez les références aux assemblys suivants.</span><span class="sxs-lookup"><span data-stu-id="770e4-113">Add references to the following assemblies.</span></span>  
  
    - <span data-ttu-id="770e4-114">WindowsFormsIntegration</span><span class="sxs-lookup"><span data-stu-id="770e4-114">WindowsFormsIntegration</span></span>  
  
    - <span data-ttu-id="770e4-115">System.Windows.Forms</span><span class="sxs-lookup"><span data-stu-id="770e4-115">System.Windows.Forms</span></span>  
  
3. <span data-ttu-id="770e4-116">Ouvrez MainWindow. xaml dans le Concepteur WPF.</span><span class="sxs-lookup"><span data-stu-id="770e4-116">Open MainWindow.xaml in the WPF Designer.</span></span>  
  
4. <span data-ttu-id="770e4-117">Dans l’élément <xref:System.Windows.Window>, ajoutez le mappage d’espace de noms suivant.</span><span class="sxs-lookup"><span data-stu-id="770e4-117">In the <xref:System.Windows.Window> element, add the following namespace mapping.</span></span> <span data-ttu-id="770e4-118">Le mappage d’espace de noms `wf` établit une référence à l’assembly qui contient le contrôle Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="770e4-118">The `wf` namespace mapping establishes a reference to the assembly that contains the Windows Forms control.</span></span>  
  
    ```xaml  
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"  
    ```  
  
5. <span data-ttu-id="770e4-119">Dans l’élément <xref:System.Windows.Controls.Grid>, ajoutez le code XAML suivant.</span><span class="sxs-lookup"><span data-stu-id="770e4-119">In the <xref:System.Windows.Controls.Grid> element add the following XAML.</span></span>  
  
     <span data-ttu-id="770e4-120">Le contrôle <xref:System.Windows.Forms.MaskedTextBox> est créé en tant qu’enfant du contrôle <xref:System.Windows.Forms.Integration.WindowsFormsHost>.</span><span class="sxs-lookup"><span data-stu-id="770e4-120">The <xref:System.Windows.Forms.MaskedTextBox> control is created as a child of the <xref:System.Windows.Forms.Integration.WindowsFormsHost> control.</span></span>  
  
     [!code-xaml[HostingWfInWpfWithXaml#3](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWpfWithXaml/CSharp/HostingWfInWpf/Window1.xaml#3)]  
  
6. <span data-ttu-id="770e4-121">Appuyez sur F5 pour générer et exécuter l'application.</span><span class="sxs-lookup"><span data-stu-id="770e4-121">Press F5 to build and run the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="770e4-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="770e4-122">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="770e4-123">Concevoir en XAML dans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="770e4-123">Design XAML in Visual Studio</span></span>](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [<span data-ttu-id="770e4-124">Procédure pas à pas : hébergement d’un contrôle Windows Forms dans WPF</span><span class="sxs-lookup"><span data-stu-id="770e4-124">Walkthrough: Hosting a Windows Forms Control in WPF</span></span>](walkthrough-hosting-a-windows-forms-control-in-wpf.md)
- [<span data-ttu-id="770e4-125">Procédure pas à pas : hébergement d'un contrôle composite Windows Forms dans WPF</span><span class="sxs-lookup"><span data-stu-id="770e4-125">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [<span data-ttu-id="770e4-126">Procédure pas à pas : Hébergement d'un contrôle composite WPF dans Windows Forms</span><span class="sxs-lookup"><span data-stu-id="770e4-126">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
- [<span data-ttu-id="770e4-127">Contrôles Windows Forms et contrôles WPF équivalents</span><span class="sxs-lookup"><span data-stu-id="770e4-127">Windows Forms Controls and Equivalent WPF Controls</span></span>](windows-forms-controls-and-equivalent-wpf-controls.md)
- [<span data-ttu-id="770e4-128">Hébergement d’un contrôle de Windows Forms dans WPF à l’aide de XAML, exemple</span><span class="sxs-lookup"><span data-stu-id="770e4-128">Hosting a Windows Forms Control in WPF by Using XAML Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=160000)
