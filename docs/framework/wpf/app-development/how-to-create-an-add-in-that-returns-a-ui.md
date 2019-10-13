---
title: 'Procédure : Créer un complément qui retourne une interface utilisateur'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- creating an add-in that returns a UI [WPF]
- implementing add-in pipeline segments [WPF]
- add-in [WPF], returns a UI
ms.assetid: 57f274b7-4c66-4b72-92eb-81939a393776
ms.openlocfilehash: e32987355a6c7ad32b5e0e8522dc4daa63783fdd
ms.sourcegitcommit: 9c3a4f2d3babca8919a1e490a159c1500ba7a844
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2019
ms.locfileid: "72291245"
---
# <a name="how-to-create-an-add-in-that-returns-a-ui"></a><span data-ttu-id="657e3-102">Procédure : Créer un complément qui retourne une interface utilisateur</span><span class="sxs-lookup"><span data-stu-id="657e3-102">How to: Create an Add-In That Returns a UI</span></span>
<span data-ttu-id="657e3-103">Cet exemple montre comment créer un complément qui retourne une Windows Presentation Foundation (WPF) à une application hôte autonome WPF.</span><span class="sxs-lookup"><span data-stu-id="657e3-103">This example shows how to create an add-in that returns a Windows Presentation Foundation (WPF) to a host WPF standalone application.</span></span>  
  
 <span data-ttu-id="657e3-104">Le complément retourne une interface utilisateur qui est un contrôle utilisateur WPF.</span><span class="sxs-lookup"><span data-stu-id="657e3-104">The add-in returns a UI that is a WPF user control.</span></span> <span data-ttu-id="657e3-105">Le contenu du contrôle utilisateur est un bouton unique qui, quand on clique dessus, affiche une boîte de message.</span><span class="sxs-lookup"><span data-stu-id="657e3-105">The content of the user control is a single button that, when clicked, displays a message box.</span></span> <span data-ttu-id="657e3-106">L’application autonome WPF héberge le complément et affiche le contrôle utilisateur (retourné par le complément) en tant que contenu de la fenêtre principale de l’application.</span><span class="sxs-lookup"><span data-stu-id="657e3-106">The WPF standalone application hosts the add-in and displays the user control (returned by the add-in) as the content of the main application window.</span></span>  
  
 <span data-ttu-id="657e3-107">**Conditions préalables**</span><span class="sxs-lookup"><span data-stu-id="657e3-107">**Prerequisites**</span></span>  
  
 <span data-ttu-id="657e3-108">Cet exemple met en surbrillance les extensions WPF du modèle de complément .NET Framework qui active ce scénario et suppose ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="657e3-108">This example highlights the WPF extensions to the .NET Framework add-in model that enable this scenario, and assumes the following:</span></span>  
  
- <span data-ttu-id="657e3-109">Connaissance du modèle de complément .NET Framework, y compris le pipeline, le complément et le développement d’hôtes.</span><span class="sxs-lookup"><span data-stu-id="657e3-109">Knowledge of the .NET Framework add-in model, including pipeline, add-in, and host development.</span></span> <span data-ttu-id="657e3-110">Si vous n’êtes pas familiarisé avec ces concepts, consultez [compléments et extensibilité](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100)).</span><span class="sxs-lookup"><span data-stu-id="657e3-110">If you are unfamiliar with these concepts, see [Add-ins and Extensibility](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100)).</span></span> <span data-ttu-id="657e3-111">Pour obtenir un didacticiel qui illustre l’implémentation d’un pipeline, d’un complément et d’une application hôte, consultez [Walkthrough : Création d’une application extensible @ no__t-0.</span><span class="sxs-lookup"><span data-stu-id="657e3-111">For a tutorial that demonstrates the implementation of a pipeline, an add-in, and a host application, see [Walkthrough: Creating an Extensible Application](../../add-ins/walkthrough-create-extensible-app.md).</span></span>  
  
- <span data-ttu-id="657e3-112">Connaissance des extensions WPF du modèle de complément .NET Framework, qui se trouve ici : [Vue d’ensemble des compléments WPF](wpf-add-ins-overview.md).</span><span class="sxs-lookup"><span data-stu-id="657e3-112">Knowledge of the WPF extensions to the .NET Framework add-in model, which can be found here: [WPF Add-Ins Overview](wpf-add-ins-overview.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="657e3-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="657e3-113">Example</span></span>  
 <span data-ttu-id="657e3-114">La création d’un complément qui retourne une interface utilisateur WPF nécessite du code spécifique pour chaque segment de pipeline, le complément et l’application hôte.</span><span class="sxs-lookup"><span data-stu-id="657e3-114">To create an add-in that returns a WPF UI requires specific code for each pipeline segment, the add-in, and the host application.</span></span>  

<a name="Contract"></a>   
## <a name="implementing-the-contract-pipeline-segment"></a><span data-ttu-id="657e3-115">Implémentation du segment de pipeline de contrat</span><span class="sxs-lookup"><span data-stu-id="657e3-115">Implementing the Contract Pipeline Segment</span></span>  
 <span data-ttu-id="657e3-116">Une méthode doit être définie par le contrat pour retourner une interface utilisateur, et sa valeur de retour doit être de type <xref:System.AddIn.Contract.INativeHandleContract>.</span><span class="sxs-lookup"><span data-stu-id="657e3-116">A method must be defined by the contract for returning a UI, and its return value must be of type <xref:System.AddIn.Contract.INativeHandleContract>.</span></span> <span data-ttu-id="657e3-117">Cela est illustré par la méthode `GetAddInUI` du contrat `IWPFAddInContract` dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="657e3-117">This is demonstrated by the `GetAddInUI` method of the `IWPFAddInContract` contract in the following code.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#ContractCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/Contracts/IWPFAddInContract.cs#contractcode)]
 [!code-vb[SimpleAddInReturnsAUISample#ContractCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/Contracts/IWPFAddInContract.vb#contractcode)]  
  
<a name="AddInView"></a>   
## <a name="implementing-the-add-in-view-pipeline-segment"></a><span data-ttu-id="657e3-118">Implémentation du segment de pipeline de vue de complément</span><span class="sxs-lookup"><span data-stu-id="657e3-118">Implementing the Add-In View Pipeline Segment</span></span>  
 <span data-ttu-id="657e3-119">Étant donné que le complément implémente les interfaces utilisateur qu’il fournit en tant que sous-classes de <xref:System.Windows.FrameworkElement>, la méthode sur la vue de complément en corrélation avec `IWPFAddInView.GetAddInUI` doit retourner une valeur de type <xref:System.Windows.FrameworkElement>.</span><span class="sxs-lookup"><span data-stu-id="657e3-119">Because the add-in implements the UIs it provides as subclasses of <xref:System.Windows.FrameworkElement>, the method on the add-in view that correlates to `IWPFAddInView.GetAddInUI` must return a value of type <xref:System.Windows.FrameworkElement>.</span></span> <span data-ttu-id="657e3-120">Le code suivant illustre la vue de complément du contrat, implémentée en tant qu’interface.</span><span class="sxs-lookup"><span data-stu-id="657e3-120">The following code shows the add-in view of the contract, implemented as an interface.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInViewCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/AddInViews/IWPFAddInView.cs#addinviewcode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInViewCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/AddInViews/IWPFAddInView.vb#addinviewcode)]  
  
<a name="AddInSideAdapter"></a>   
## <a name="implementing-the-add-in-side-adapter-pipeline-segment"></a><span data-ttu-id="657e3-121">Implémentation du segment de pipeline d’adaptateur côté complément</span><span class="sxs-lookup"><span data-stu-id="657e3-121">Implementing the Add-In-Side Adapter Pipeline Segment</span></span>  
 <span data-ttu-id="657e3-122">La méthode de contrat retourne un <xref:System.AddIn.Contract.INativeHandleContract>, mais le complément retourne un <xref:System.Windows.FrameworkElement> (comme spécifié par la vue de complément).</span><span class="sxs-lookup"><span data-stu-id="657e3-122">The contract method returns an <xref:System.AddIn.Contract.INativeHandleContract>, but the add-in returns a <xref:System.Windows.FrameworkElement> (as specified by the add-in view).</span></span> <span data-ttu-id="657e3-123">Par conséquent, la <xref:System.Windows.FrameworkElement> doit être convertie en <xref:System.AddIn.Contract.INativeHandleContract> avant de traverser la limite d’isolation.</span><span class="sxs-lookup"><span data-stu-id="657e3-123">Consequently, the <xref:System.Windows.FrameworkElement> must be converted to an <xref:System.AddIn.Contract.INativeHandleContract> before crossing the isolation boundary.</span></span> <span data-ttu-id="657e3-124">Ce travail est effectué par l’adaptateur côté complément en appelant <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>, comme indiqué dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="657e3-124">This work is performed by the add-in-side adapter by calling <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>, as shown in the following code.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInSideAdapterCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.cs#addinsideadaptercode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInSideAdapterCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.vb#addinsideadaptercode)]  
  
<a name="HostView"></a>   
## <a name="implementing-the-host-view-pipeline-segment"></a><span data-ttu-id="657e3-125">Implémentation du segment de pipeline de vue hôte</span><span class="sxs-lookup"><span data-stu-id="657e3-125">Implementing the Host View Pipeline Segment</span></span>  
 <span data-ttu-id="657e3-126">Étant donné que l’application hôte affiche un <xref:System.Windows.FrameworkElement>, la méthode sur la vue hôte qui correspond à `IWPFAddInHostView.GetAddInUI` doit retourner une valeur de type <xref:System.Windows.FrameworkElement>.</span><span class="sxs-lookup"><span data-stu-id="657e3-126">Because the host application will display a <xref:System.Windows.FrameworkElement>, the method on the host view that correlates to `IWPFAddInHostView.GetAddInUI` must return a value of type <xref:System.Windows.FrameworkElement>.</span></span> <span data-ttu-id="657e3-127">Le code suivant illustre la vue hôte du contrat, implémentée en tant qu’interface.</span><span class="sxs-lookup"><span data-stu-id="657e3-127">The following code shows the host view of the contract, implemented as an interface.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#HostViewCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/HostViews/IWPFAddInHostView.cs#hostviewcode)]
 [!code-vb[SimpleAddInReturnsAUISample#HostViewCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/HostViews/IWPFAddInHostView.vb#hostviewcode)]  
  
<a name="HostSideAdapter"></a>   
## <a name="implementing-the-host-side-adapter-pipeline-segment"></a><span data-ttu-id="657e3-128">Implémentation du segment de pipeline d’adaptateur côté hôte</span><span class="sxs-lookup"><span data-stu-id="657e3-128">Implementing the Host-Side Adapter Pipeline Segment</span></span>  
 <span data-ttu-id="657e3-129">La méthode de contrat retourne un <xref:System.AddIn.Contract.INativeHandleContract>, mais l’application hôte attend une <xref:System.Windows.FrameworkElement> (comme spécifié par la vue hôte).</span><span class="sxs-lookup"><span data-stu-id="657e3-129">The contract method returns an <xref:System.AddIn.Contract.INativeHandleContract>, but the host application expects a <xref:System.Windows.FrameworkElement> (as specified by the host view).</span></span> <span data-ttu-id="657e3-130">Par conséquent, la <xref:System.AddIn.Contract.INativeHandleContract> doit être convertie en <xref:System.Windows.FrameworkElement> après avoir franchi la limite d’isolement.</span><span class="sxs-lookup"><span data-stu-id="657e3-130">Consequently, the <xref:System.AddIn.Contract.INativeHandleContract> must be converted to a <xref:System.Windows.FrameworkElement> after crossing the isolation boundary.</span></span> <span data-ttu-id="657e3-131">Ce travail est effectué par l’adaptateur côté hôte en appelant <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>, comme indiqué dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="657e3-131">This work is performed by the host-side adapter by calling <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>, as shown in the following code.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#HostSideAdapterCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.cs#hostsideadaptercode)]
 [!code-vb[SimpleAddInReturnsAUISample#HostSideAdapterCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.vb#hostsideadaptercode)]  
  
<a name="AddIn"></a>   
## <a name="implementing-the-add-in"></a><span data-ttu-id="657e3-132">Implémentation du complément</span><span class="sxs-lookup"><span data-stu-id="657e3-132">Implementing the Add-In</span></span>  
 <span data-ttu-id="657e3-133">Avec l’adaptateur côté complément et la vue de complément créés, le complément (`WPFAddIn1.AddIn`) doit implémenter la méthode `IWPFAddInView.GetAddInUI` pour retourner un objet <xref:System.Windows.FrameworkElement> (un <xref:System.Windows.Controls.UserControl> dans cet exemple).</span><span class="sxs-lookup"><span data-stu-id="657e3-133">With the add-in-side adapter and add-in view created, the add-in (`WPFAddIn1.AddIn`) must implement the `IWPFAddInView.GetAddInUI` method to return a <xref:System.Windows.FrameworkElement> object (a <xref:System.Windows.Controls.UserControl> in this example).</span></span> <span data-ttu-id="657e3-134">L’implémentation de l' <xref:System.Windows.Controls.UserControl>, `AddInUI`, est indiquée par le code suivant.</span><span class="sxs-lookup"><span data-stu-id="657e3-134">The implementation of the <xref:System.Windows.Controls.UserControl>, `AddInUI`, is shown by the following code.</span></span>  
  
 [!code-xaml[SimpleAddInReturnsAUISample#AddInUIMarkup](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddInUI.xaml#addinuimarkup)]  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInUICodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddInUI.xaml.cs#addinuicodebehind)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInUICodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/WPFAddIn1/AddInUI.xaml.vb#addinuicodebehind)]  
  
 <span data-ttu-id="657e3-135">L’implémentation de la `IWPFAddInView.GetAddInUI` par le complément doit simplement retourner une nouvelle instance de `AddInUI`, comme le montre le code suivant.</span><span class="sxs-lookup"><span data-stu-id="657e3-135">The implementation of the `IWPFAddInView.GetAddInUI` by the add-in simply needs to return a new instance of `AddInUI`, as shown by the following code.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddIn.cs#addincode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/WPFAddIn1/AddIn.vb#addincode)]  
  
<a name="App"></a>   
## <a name="implementing-the-host-application"></a><span data-ttu-id="657e3-136">Implémentation de l'application hôte.</span><span class="sxs-lookup"><span data-stu-id="657e3-136">Implementing the Host Application</span></span>  
 <span data-ttu-id="657e3-137">L’adaptateur côté hôte et la vue hôte étant créés, l’application hôte peut utiliser le modèle de complément .NET Framework pour ouvrir le pipeline, acquérir une vue hôte du complément et appeler la méthode `IWPFAddInHostView.GetAddInUI`.</span><span class="sxs-lookup"><span data-stu-id="657e3-137">With the host-side adapter and host view created, the host application can use the .NET Framework add-in model to open the pipeline, acquire a host view of the add-in, and call the `IWPFAddInHostView.GetAddInUI` method.</span></span> <span data-ttu-id="657e3-138">Ces étapes sont présentées dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="657e3-138">These steps are shown in the following code.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#GetUICode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/Host/MainWindow.xaml.cs#getuicode)]
 [!code-vb[SimpleAddInReturnsAUISample#GetUICode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/Host/MainWindow.xaml.vb#getuicode)]  
  
## <a name="see-also"></a><span data-ttu-id="657e3-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="657e3-139">See also</span></span>

- <span data-ttu-id="657e3-140">[Compléments et extensibilité](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))</span><span class="sxs-lookup"><span data-stu-id="657e3-140">[Add-ins and Extensibility](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))</span></span>
- [<span data-ttu-id="657e3-141">Vue d’ensemble des compléments WPF</span><span class="sxs-lookup"><span data-stu-id="657e3-141">WPF Add-Ins Overview</span></span>](wpf-add-ins-overview.md)
