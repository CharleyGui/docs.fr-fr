---
title: 'Procédure : Créer un complément qui est une interface utilisateur'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- creating an add-in that is a UI [WPF]
- add-ins [WPF], UI
- creating UI add-ins [WPF]
- UI add-ins [WPF], creating
- implementing UI add-ins [WPF]
- pipeline segments [WPF], creating add-ins
ms.assetid: 86375525-282b-4039-8352-8680051a10ea
ms.openlocfilehash: b0e847061a30e93d36997ab603c52715e2730765
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71182638"
---
# <a name="how-to-create-an-add-in-that-is-a-ui"></a>Procédure : Créer un complément qui est une interface utilisateur
Cet exemple montre comment créer un complément qui est un Windows Presentation Foundation (WPF) qui est hébergé par une application WPF autonome.  
  
 Le complément est une interface utilisateur qui est un contrôle utilisateur WPF. Le contenu du contrôle utilisateur est un bouton unique qui, quand on clique dessus, affiche une boîte de message. L’application autonome WPF héberge l’interface utilisateur du complément en tant que contenu de la fenêtre principale de l’application.  
  
 **Composants requis**  
  
 Cet exemple met en surbrillance les extensions WPF du modèle de complément .NET Framework qui active ce scénario et suppose ce qui suit :  
  
- Connaissance du modèle de complément .NET Framework, y compris le pipeline, le complément et le développement d’hôtes. Si vous n’êtes pas familiarisé avec ces concepts, consultez [compléments et extensibilité](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100)). Pour obtenir un didacticiel qui illustre l’implémentation d’un pipeline, d’un complément et d’une application hôte, [consultez Procédure pas à pas : Création d’une application](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb788290(v%3dvs.100))extensible.  
  
- Connaissance des extensions WPF du modèle de complément .NET Framework. Consultez [vue d’ensemble des compléments WPF](wpf-add-ins-overview.md).  
  
## <a name="example"></a>Exemple  
 Pour créer un complément qui est une interface utilisateur WPF nécessite du code spécifique pour chaque segment de pipeline, le complément et l’application hôte.  

<a name="Contract"></a>   
## <a name="implementing-the-contract-pipeline-segment"></a>Implémentation du segment de pipeline de contrat

Quand un complément est une interface utilisateur, le contrat pour le complément doit implémenter <xref:System.AddIn.Contract.INativeHandleContract>. Dans l’exemple, `IWPFAddInContract` <xref:System.AddIn.Contract.INativeHandleContract>implémente, comme indiqué dans le code suivant.  
  
[!code-csharp[SimpleAddInIsAUISample#ContractCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/Contracts/IWPFAddInContract.cs#contractcode)]
[!code-vb[SimpleAddInIsAUISample#ContractCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInIsAUISample/VisualBasic/Contracts/IWPFAddInContract.vb#contractcode)]

<a name="AddInViewPipeline"></a>   
## <a name="implementing-the-add-in-view-pipeline-segment"></a>Implémentation du segment de pipeline de vue de complément

Étant donné que le complément est implémenté en tant que sous-classe <xref:System.Windows.FrameworkElement> du type, la vue du complément doit également être sous <xref:System.Windows.FrameworkElement>-classe. Le code suivant illustre la vue de complément du contrat, implémentée en tant que `WPFAddInView` classe.  
  
[!code-csharp[SimpleAddInIsAUISample#AddInViewCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/AddInViews/WPFAddInView.cs#addinviewcode)]  
[!code-vb[SimpleAddInIsAUISample#AddInViewCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInIsAUISample/VisualBasic/AddInViews/WPFAddInView.vb#AddInViewCode)]  
  
Ici, la vue du complément est dérivée de <xref:System.Windows.Controls.UserControl>. Par conséquent, l’interface utilisateur du complément doit également dériver de <xref:System.Windows.Controls.UserControl>.  
  
<a name="AddInSideAdapter"></a>
## <a name="implementing-the-add-in-side-adapter-pipeline-segment"></a>Implémentation du segment de pipeline d’adaptateur côté complément

Si le contrat est un <xref:System.AddIn.Contract.INativeHandleContract>, le complément est un <xref:System.Windows.FrameworkElement> (comme spécifié par le segment de pipeline de la vue de complément). Par conséquent, <xref:System.Windows.FrameworkElement> doit être converti en un <xref:System.AddIn.Contract.INativeHandleContract> avant de traverser la limite d’isolation. Ce travail est effectué par l’adaptateur côté complément en appelant <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>, comme illustré dans le code suivant.  
  
[!code-csharp[SimpleAddInIsAUISample#AddInSideAdapterCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.cs#addinsideadaptercode)]  
[!code-vb[SimpleAddInIsAUISample#AddInSideAdapterCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInIsAUISample/VisualBasic/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.vb#addinsideadaptercode)]

Dans le modèle de complément où un complément retourne une interface utilisateur (consultez [créer un complément qui retourne une interface utilisateur](how-to-create-an-add-in-that-returns-a-ui.md)), l’adaptateur de complément convertit <xref:System.Windows.FrameworkElement> <xref:System.AddIn.Contract.INativeHandleContract> en en appelant <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>. <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>doit également être appelé dans ce modèle, bien que vous deviez implémenter une méthode à partir de laquelle écrire le code pour l’appeler. Pour ce faire, vous devez <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> substituer et implémenter le <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> code qui appelle si le code <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> appelant attend un <xref:System.AddIn.Contract.INativeHandleContract>. Dans ce cas, l’appelant sera l’adaptateur côté hôte, ce qui est traité dans une sous-section ultérieure.  
  
> [!NOTE]
> Vous devez également remplacer <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> dans ce modèle pour permettre la tabulation entre l’interface utilisateur de l’application hôte et l’interface utilisateur du complément. Pour plus d’informations, consultez « Limitations des compléments WPF » dans [vue d’ensemble des compléments WPF](wpf-add-ins-overview.md).  
  
Étant donné que l’adaptateur côté complément implémente une interface qui dérive de <xref:System.AddIn.Contract.INativeHandleContract>, vous devez également implémenter <xref:System.AddIn.Contract.INativeHandleContract.GetHandle%2A>, bien que cela soit ignoré lorsque <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> est substitué.  
  
<a name="HostViewPipeline"></a>   
## <a name="implementing-the-host-view-pipeline-segment"></a>Implémentation du segment de pipeline de vue hôte

Dans ce modèle, l’application hôte s’attend généralement à ce que la vue hôte <xref:System.Windows.FrameworkElement> soit une sous-classe. L’adaptateur côté hôte doit convertir <xref:System.AddIn.Contract.INativeHandleContract> en un <xref:System.Windows.FrameworkElement> après <xref:System.AddIn.Contract.INativeHandleContract> l’intersection de la limite d’isolation. Étant donné qu’une méthode n’est pas appelée par l’application hôte <xref:System.Windows.FrameworkElement>pour obtenir le, la vue hôte doit « <xref:System.Windows.FrameworkElement> retourner » en la contenant. Par conséquent, la vue hôte doit dériver d’une sous <xref:System.Windows.FrameworkElement> -classe de qui peut contenir d’autres <xref:System.Windows.Controls.UserControl>interfaces utilisateur, telles que. Le code suivant illustre la vue hôte du contrat, implémentée en tant `WPFAddInHostView` que classe.  

[!code-csharp[WPFAddInHostView class](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/HostViews/WPFAddInHostView.cs#HostViewCode)]
[!code-vb[WPFAddInHostView class](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInIsAUISample/VisualBasic/HostViews/WPFAddInHostView.vb#HostViewCode)]

<a name="HostSideAdapter"></a>   
## <a name="implementing-the-host-side-adapter-pipeline-segment"></a>Implémentation du segment de pipeline d’adaptateur côté hôte

Si le contrat est un <xref:System.AddIn.Contract.INativeHandleContract>, l’application hôte attend un <xref:System.Windows.Controls.UserControl> (comme spécifié par la vue hôte). Par conséquent, <xref:System.AddIn.Contract.INativeHandleContract> doit être converti en un <xref:System.Windows.FrameworkElement> après avoir franchi la limite d’isolation, avant d’être défini en tant que contenu de la vue hôte <xref:System.Windows.Controls.UserControl>(qui dérive de).  
  
Cette opération est exécutée par l’adaptateur côté hôte, comme illustré dans le code suivant.  

[!code-csharp[Host-side adapter](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.cs#HostSideAdapterCode)]
[!code-vb[Host-side adapter](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInIsAUISample/VisualBasic/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.vb#HostSideAdapterCode)]

Comme vous pouvez le voir, l’adaptateur côté hôte acquiert le <xref:System.AddIn.Contract.INativeHandleContract> en appelant la méthode de <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> l’adaptateur côté complément (il s’agit du point où le <xref:System.AddIn.Contract.INativeHandleContract> franchit la limite d’isolation).  
  
L’adaptateur côté hôte convertit ensuite le <xref:System.AddIn.Contract.INativeHandleContract> <xref:System.Windows.FrameworkElement> en en appelant <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>. Enfin, le <xref:System.Windows.FrameworkElement> est défini en tant que contenu de la vue hôte.  
  
<a name="AddIn"></a>   
## <a name="implementing-the-add-in"></a>Implémentation du complément

Avec l’adaptateur côté complément et la vue de complément en place, le complément peut être implémenté par dérivation de la vue de complément, comme illustré dans le code suivant.  

[!code-csharp[Add-in implementation](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/WPFAddIn1/AddInUI.xaml.cs#AddInCodeBehind)]
[!code-vb[Add-in implementation](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInIsAUISample/VisualBasic/WPFAddIn1/AddInUI.xaml.vb#AddInCodeBehind)]

Dans cet exemple, vous pouvez voir un avantage intéressant de ce modèle : les développeurs de compléments doivent uniquement implémenter le complément (puisqu’il s’agit également de l’interface utilisateur), plutôt qu’une classe de complément et une interface utilisateur de complément.  
  
<a name="HostApp"></a>
## <a name="implementing-the-host-application"></a>Implémentation de l'application hôte.

L’adaptateur côté hôte et la vue hôte étant créés, l’application hôte peut utiliser le modèle de complément .NET Framework pour ouvrir le pipeline et acquérir une vue hôte du complément. Ces étapes sont présentées dans le code suivant.  

[!code-csharp[Acquiring a host view of the add-in](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/Host/MainWindow.xaml.cs#GetUICode)]
[!code-vb[Acquiring a host view of the add-in](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInIsAUISample/VisualBasic/Host/MainWindow.xaml.vb#GetUICode)]

L’application hôte utilise le code de modèle de complément .NET Framework typique pour activer le complément, qui retourne implicitement la vue hôte à l’application hôte. L’application hôte affiche ensuite la vue hôte (qui est un <xref:System.Windows.Controls.UserControl>) à partir <xref:System.Windows.Controls.Grid>d’un.  
  
 Le code pour le traitement des interactions avec l’interface utilisateur du complément s’exécute dans le domaine d’application du complément. Ces interactions incluent :  
  
- Gestion de <xref:System.Windows.Controls.Button> l' <xref:System.Windows.Controls.Primitives.ButtonBase.Click> événement.  
  
- Qui présente <xref:System.Windows.MessageBox>le.  
  
 Cette activité est complètement isolée de l’application hôte.  
  
## <a name="see-also"></a>Voir aussi

- [Compléments et extensibilité](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))
- [Vue d’ensemble des compléments WPF](wpf-add-ins-overview.md)
