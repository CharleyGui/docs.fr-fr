---
title: 'Comment : créer un complément qui retourne une interface utilisateur'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- creating an add-in that returns a UI [WPF]
- implementing add-in pipeline segments [WPF]
- add-in [WPF], returns a UI
ms.assetid: 57f274b7-4c66-4b72-92eb-81939a393776
ms.openlocfilehash: f8323fe35555a56d39c1efed649c2aa3fcf17e43
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174587"
---
# <a name="how-to-create-an-add-in-that-returns-a-ui"></a><span data-ttu-id="38012-102">Comment : créer un complément qui retourne une interface utilisateur</span><span class="sxs-lookup"><span data-stu-id="38012-102">How to: Create an Add-In That Returns a UI</span></span>
<span data-ttu-id="38012-103">Cet exemple montre comment créer un add-in qui renvoie une Fondation de présentation Windows (WPF) à une application autonome WPF hôte.</span><span class="sxs-lookup"><span data-stu-id="38012-103">This example shows how to create an add-in that returns a Windows Presentation Foundation (WPF) to a host WPF standalone application.</span></span>  
  
 <span data-ttu-id="38012-104">L’add-in renvoie une interface utilisateur qui est un contrôle utilisateur WPF.</span><span class="sxs-lookup"><span data-stu-id="38012-104">The add-in returns a UI that is a WPF user control.</span></span> <span data-ttu-id="38012-105">Le contenu du contrôle utilisateur est un bouton unique qui, quand on clique dessus, affiche une boîte de message.</span><span class="sxs-lookup"><span data-stu-id="38012-105">The content of the user control is a single button that, when clicked, displays a message box.</span></span> <span data-ttu-id="38012-106">L’application autonome WPF héberge l’add-in et affiche le contrôle de l’utilisateur (retourné par l’add-in) comme le contenu de la fenêtre d’application principale.</span><span class="sxs-lookup"><span data-stu-id="38012-106">The WPF standalone application hosts the add-in and displays the user control (returned by the add-in) as the content of the main application window.</span></span>  
  
 <span data-ttu-id="38012-107">**Conditions préalables**</span><span class="sxs-lookup"><span data-stu-id="38012-107">**Prerequisites**</span></span>  
  
 <span data-ttu-id="38012-108">Cet exemple met en évidence les extensions WPF au modèle d’add-in .NET Framework qui permettent ce scénario, et suppose ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="38012-108">This example highlights the WPF extensions to the .NET Framework add-in model that enable this scenario, and assumes the following:</span></span>  
  
- <span data-ttu-id="38012-109">Connaissance du modèle d’ajout du cadre .NET, y compris le pipeline, l’ajout et le développement de l’hôte.</span><span class="sxs-lookup"><span data-stu-id="38012-109">Knowledge of the .NET Framework add-in model, including pipeline, add-in, and host development.</span></span> <span data-ttu-id="38012-110">Si vous n’êtes pas familier avec ces concepts, voir [Add-ins et Extensibility](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100)).</span><span class="sxs-lookup"><span data-stu-id="38012-110">If you are unfamiliar with these concepts, see [Add-ins and Extensibility](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100)).</span></span> <span data-ttu-id="38012-111">Pour un tutoriel qui démontre la mise en œuvre d’un pipeline, un add-in, et une application hôte, voir [Procédure pas à pas: Créer une application extensible](/previous-versions/dotnet/netframework-4.0/bb788290(v%3dvs.100)).</span><span class="sxs-lookup"><span data-stu-id="38012-111">For a tutorial that demonstrates the implementation of a pipeline, an add-in, and a host application, see [Walkthrough: Creating an Extensible Application](/previous-versions/dotnet/netframework-4.0/bb788290(v%3dvs.100)).</span></span>  
  
- <span data-ttu-id="38012-112">Connaissance des extensions WPF au modèle d’add-in .NET Framework, qui peut être trouvé ici: [WPF Add-Ins Aperçu](wpf-add-ins-overview.md).</span><span class="sxs-lookup"><span data-stu-id="38012-112">Knowledge of the WPF extensions to the .NET Framework add-in model, which can be found here: [WPF Add-Ins Overview](wpf-add-ins-overview.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="38012-113"> Exemple</span><span class="sxs-lookup"><span data-stu-id="38012-113">Example</span></span>  
 <span data-ttu-id="38012-114">Pour créer un add-in qui renvoie une interface utilisateur WPF nécessite un code spécifique pour chaque segment de pipeline, l’add-in, et l’application hôte.</span><span class="sxs-lookup"><span data-stu-id="38012-114">To create an add-in that returns a WPF UI requires specific code for each pipeline segment, the add-in, and the host application.</span></span>  

<a name="Contract"></a>
## <a name="implementing-the-contract-pipeline-segment"></a><span data-ttu-id="38012-115">Implémentation du segment de pipeline de contrat</span><span class="sxs-lookup"><span data-stu-id="38012-115">Implementing the Contract Pipeline Segment</span></span>  
 <span data-ttu-id="38012-116">Une méthode doit être définie par le contrat de retour d’une assurance-chômage, et sa valeur de retour doit être de type <xref:System.AddIn.Contract.INativeHandleContract>.</span><span class="sxs-lookup"><span data-stu-id="38012-116">A method must be defined by the contract for returning a UI, and its return value must be of type <xref:System.AddIn.Contract.INativeHandleContract>.</span></span> <span data-ttu-id="38012-117">Cela est démontré `GetAddInUI` par `IWPFAddInContract` la méthode du contrat dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="38012-117">This is demonstrated by the `GetAddInUI` method of the `IWPFAddInContract` contract in the following code.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#ContractCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/Contracts/IWPFAddInContract.cs#contractcode)]
 [!code-vb[SimpleAddInReturnsAUISample#ContractCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/Contracts/IWPFAddInContract.vb#contractcode)]  
  
<a name="AddInView"></a>
## <a name="implementing-the-add-in-view-pipeline-segment"></a><span data-ttu-id="38012-118">Implémentation du segment de pipeline de vue de complément</span><span class="sxs-lookup"><span data-stu-id="38012-118">Implementing the Add-In View Pipeline Segment</span></span>  
 <span data-ttu-id="38012-119">Parce que l’add-in implémente les <xref:System.Windows.FrameworkElement>IA qu’il fournit comme sous-classes `IWPFAddInView.GetAddInUI` de , la <xref:System.Windows.FrameworkElement>méthode sur l’add-in vue qui se corrèle à doit retourner une valeur de type .</span><span class="sxs-lookup"><span data-stu-id="38012-119">Because the add-in implements the UIs it provides as subclasses of <xref:System.Windows.FrameworkElement>, the method on the add-in view that correlates to `IWPFAddInView.GetAddInUI` must return a value of type <xref:System.Windows.FrameworkElement>.</span></span> <span data-ttu-id="38012-120">Le code suivant illustre la vue de complément du contrat, implémentée en tant qu’interface.</span><span class="sxs-lookup"><span data-stu-id="38012-120">The following code shows the add-in view of the contract, implemented as an interface.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInViewCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/AddInViews/IWPFAddInView.cs#addinviewcode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInViewCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/AddInViews/IWPFAddInView.vb#addinviewcode)]  
  
<a name="AddInSideAdapter"></a>
## <a name="implementing-the-add-in-side-adapter-pipeline-segment"></a><span data-ttu-id="38012-121">Implémentation du segment de pipeline d’adaptateur côté complément</span><span class="sxs-lookup"><span data-stu-id="38012-121">Implementing the Add-In-Side Adapter Pipeline Segment</span></span>  
 <span data-ttu-id="38012-122">La méthode du <xref:System.AddIn.Contract.INativeHandleContract>contrat renvoie un <xref:System.Windows.FrameworkElement> , mais l’add-in renvoie un (comme spécifié par la vue add-in).</span><span class="sxs-lookup"><span data-stu-id="38012-122">The contract method returns an <xref:System.AddIn.Contract.INativeHandleContract>, but the add-in returns a <xref:System.Windows.FrameworkElement> (as specified by the add-in view).</span></span> <span data-ttu-id="38012-123">Par conséquent, <xref:System.Windows.FrameworkElement> le doit être <xref:System.AddIn.Contract.INativeHandleContract> converti en un avant de traverser la limite d’isolement.</span><span class="sxs-lookup"><span data-stu-id="38012-123">Consequently, the <xref:System.Windows.FrameworkElement> must be converted to an <xref:System.AddIn.Contract.INativeHandleContract> before crossing the isolation boundary.</span></span> <span data-ttu-id="38012-124">Ce travail est effectué par l’adaptateur <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>add-in-side en appelant, comme indiqué dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="38012-124">This work is performed by the add-in-side adapter by calling <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>, as shown in the following code.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInSideAdapterCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.cs#addinsideadaptercode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInSideAdapterCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.vb#addinsideadaptercode)]  
  
<a name="HostView"></a>
## <a name="implementing-the-host-view-pipeline-segment"></a><span data-ttu-id="38012-125">Implémentation du segment de pipeline de vue hôte</span><span class="sxs-lookup"><span data-stu-id="38012-125">Implementing the Host View Pipeline Segment</span></span>  
 <span data-ttu-id="38012-126">Parce que l’application <xref:System.Windows.FrameworkElement>hôte affichera un , la `IWPFAddInHostView.GetAddInUI` méthode sur la <xref:System.Windows.FrameworkElement>vue hôte qui est corrélée à doit retourner une valeur de type .</span><span class="sxs-lookup"><span data-stu-id="38012-126">Because the host application will display a <xref:System.Windows.FrameworkElement>, the method on the host view that correlates to `IWPFAddInHostView.GetAddInUI` must return a value of type <xref:System.Windows.FrameworkElement>.</span></span> <span data-ttu-id="38012-127">Le code suivant illustre la vue hôte du contrat, implémentée en tant qu’interface.</span><span class="sxs-lookup"><span data-stu-id="38012-127">The following code shows the host view of the contract, implemented as an interface.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#HostViewCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/HostViews/IWPFAddInHostView.cs#hostviewcode)]
 [!code-vb[SimpleAddInReturnsAUISample#HostViewCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/HostViews/IWPFAddInHostView.vb#hostviewcode)]  
  
<a name="HostSideAdapter"></a>
## <a name="implementing-the-host-side-adapter-pipeline-segment"></a><span data-ttu-id="38012-128">Implémentation du segment de pipeline d’adaptateur côté hôte</span><span class="sxs-lookup"><span data-stu-id="38012-128">Implementing the Host-Side Adapter Pipeline Segment</span></span>  
 <span data-ttu-id="38012-129">La méthode du <xref:System.AddIn.Contract.INativeHandleContract>contrat renvoie un <xref:System.Windows.FrameworkElement> , mais l’application hôte s’attend à un (comme spécifié par la vue hôte).</span><span class="sxs-lookup"><span data-stu-id="38012-129">The contract method returns an <xref:System.AddIn.Contract.INativeHandleContract>, but the host application expects a <xref:System.Windows.FrameworkElement> (as specified by the host view).</span></span> <span data-ttu-id="38012-130">Par conséquent, <xref:System.AddIn.Contract.INativeHandleContract> le doit être <xref:System.Windows.FrameworkElement> converti en après avoir franchi la limite d’isolement.</span><span class="sxs-lookup"><span data-stu-id="38012-130">Consequently, the <xref:System.AddIn.Contract.INativeHandleContract> must be converted to a <xref:System.Windows.FrameworkElement> after crossing the isolation boundary.</span></span> <span data-ttu-id="38012-131">Ce travail est effectué par l’adaptateur côté hôte en appelant, <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>comme indiqué dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="38012-131">This work is performed by the host-side adapter by calling <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>, as shown in the following code.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#HostSideAdapterCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.cs#hostsideadaptercode)]
 [!code-vb[SimpleAddInReturnsAUISample#HostSideAdapterCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.vb#hostsideadaptercode)]  
  
<a name="AddIn"></a>
## <a name="implementing-the-add-in"></a><span data-ttu-id="38012-132">Implémentation du complément</span><span class="sxs-lookup"><span data-stu-id="38012-132">Implementing the Add-In</span></span>  
 <span data-ttu-id="38012-133">Avec l’adaptateur add-in-side et add-in vue`WPFAddIn1.AddIn`créée, `IWPFAddInView.GetAddInUI` l’add-in ( ) doit implémenter la méthode pour retourner un <xref:System.Windows.FrameworkElement> objet (un <xref:System.Windows.Controls.UserControl> dans cet exemple).</span><span class="sxs-lookup"><span data-stu-id="38012-133">With the add-in-side adapter and add-in view created, the add-in (`WPFAddIn1.AddIn`) must implement the `IWPFAddInView.GetAddInUI` method to return a <xref:System.Windows.FrameworkElement> object (a <xref:System.Windows.Controls.UserControl> in this example).</span></span> <span data-ttu-id="38012-134">La mise <xref:System.Windows.Controls.UserControl>en `AddInUI`œuvre du , , est indiquée par le code suivant.</span><span class="sxs-lookup"><span data-stu-id="38012-134">The implementation of the <xref:System.Windows.Controls.UserControl>, `AddInUI`, is shown by the following code.</span></span>  
  
 [!code-xaml[SimpleAddInReturnsAUISample#AddInUIMarkup](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddInUI.xaml#addinuimarkup)]  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInUICodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddInUI.xaml.cs#addinuicodebehind)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInUICodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/WPFAddIn1/AddInUI.xaml.vb#addinuicodebehind)]  
  
 <span data-ttu-id="38012-135">La mise `IWPFAddInView.GetAddInUI` en œuvre de l’add-in `AddInUI`doit simplement retourner une nouvelle instance de , comme le montre le code suivant.</span><span class="sxs-lookup"><span data-stu-id="38012-135">The implementation of the `IWPFAddInView.GetAddInUI` by the add-in simply needs to return a new instance of `AddInUI`, as shown by the following code.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddIn.cs#addincode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/WPFAddIn1/AddIn.vb#addincode)]  
  
<a name="App"></a>
## <a name="implementing-the-host-application"></a><span data-ttu-id="38012-136">Implémentation de l'application hôte.</span><span class="sxs-lookup"><span data-stu-id="38012-136">Implementing the Host Application</span></span>  
 <span data-ttu-id="38012-137">Avec l’adaptateur côté hôte et la vue d’hôte créée, l’application hôte peut utiliser le modèle d’add-in .NET Framework pour ouvrir le pipeline, acquérir une vue d’hôte de l’add-in, et appeler la `IWPFAddInHostView.GetAddInUI` méthode.</span><span class="sxs-lookup"><span data-stu-id="38012-137">With the host-side adapter and host view created, the host application can use the .NET Framework add-in model to open the pipeline, acquire a host view of the add-in, and call the `IWPFAddInHostView.GetAddInUI` method.</span></span> <span data-ttu-id="38012-138">Ces étapes sont présentées dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="38012-138">These steps are shown in the following code.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#GetUICode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/Host/MainWindow.xaml.cs#getuicode)]
 [!code-vb[SimpleAddInReturnsAUISample#GetUICode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/Host/MainWindow.xaml.vb#getuicode)]  
  
## <a name="see-also"></a><span data-ttu-id="38012-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="38012-139">See also</span></span>

- <span data-ttu-id="38012-140">[Compléments et extensibilité](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))</span><span class="sxs-lookup"><span data-stu-id="38012-140">[Add-ins and Extensibility](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))</span></span>
- [<span data-ttu-id="38012-141">Vue d’ensemble des compléments WPF</span><span class="sxs-lookup"><span data-stu-id="38012-141">WPF Add-Ins Overview</span></span>](wpf-add-ins-overview.md)
