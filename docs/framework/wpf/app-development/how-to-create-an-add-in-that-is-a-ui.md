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
ms.openlocfilehash: b0213ddfd8197ffabcbeb1cd5fc78e517920b8fe
ms.sourcegitcommit: d8ebe0ee198f5d38387a80ba50f395386779334f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66690449"
---
# <a name="how-to-create-an-add-in-that-is-a-ui"></a>Procédure : Créer un complément qui est une interface utilisateur
Cet exemple montre comment créer un complément qui est un Windows Presentation Foundation (WPF) qui est hébergé par une application autonome WPF.  
  
 Le complément est une interface utilisateur qui est un contrôle utilisateur WPF. Le contenu du contrôle utilisateur est un bouton unique qui, quand on clique dessus, affiche une boîte de message. L’application autonome WPF héberge l’interface utilisateur Ajouter en tant que le contenu de la fenêtre principale de l’application.  
  
 **Composants requis**  
  
 Cet exemple met en évidence les extensions WPF pour le modèle de complément .NET Framework qui permettent ce scénario et suppose ce qui suit :  
  
- Base de connaissances du .NET Framework dans modèle, y compris le pipeline de complément et développement de l’hôte. Si vous n’êtes pas familiarisé avec ces concepts, consultez [des compléments et extensibilité](/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100)). Pour obtenir un didacticiel qui montre l’implémentation d’un pipeline, un complément et une application hôte, consultez [procédure pas à pas : Création d’une Application Extensible](/previous-versions/dotnet/netframework-4.0/bb788290(v%3dvs.100)).  
  
- Connaissance des extensions de WPF pour le modèle de complément .NET Framework. Consultez [vue d’ensemble des compléments WPF](wpf-add-ins-overview.md).  
  
## <a name="example"></a>Exemple  
 Pour créer un complément qui est une UI WPF nécessite du code spécifique pour chaque segment de pipeline, le complément et l’application hôte.  

<a name="Contract"></a>   
## <a name="implementing-the-contract-pipeline-segment"></a>Implémentation du segment de pipeline de contrat

Lorsqu’un complément est une interface utilisateur, le contrat pour le complément doit implémenter <xref:System.AddIn.Contract.INativeHandleContract>. Dans l’exemple, `IWPFAddInContract` implémente <xref:System.AddIn.Contract.INativeHandleContract>, comme illustré dans le code suivant.  
  
[!code-csharp[SimpleAddInIsAUISample#ContractCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/Contracts/IWPFAddInContract.cs#contractcode)]
[!code-vb[SimpleAddInIsAUISample#ContractCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInIsAUISample/VisualBasic/Contracts/IWPFAddInContract.vb#contractcode)]

<a name="AddInViewPipeline"></a>   
## <a name="implementing-the-add-in-view-pipeline-segment"></a>Implémentation du segment de pipeline de vue de complément

Étant donné que le complément est implémenté comme une sous-classe de la <xref:System.Windows.FrameworkElement> type, la vue de complément doit également sous-classer <xref:System.Windows.FrameworkElement>. Le code suivant montre la vue de complément du contrat, implémentée en tant que la `WPFAddInView` classe.  
  
[!code-csharp[SimpleAddInIsAUISample#AddInViewCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/AddInViews/WPFAddInView.cs#addinviewcode)]  
[!code-vb[SimpleAddInIsAUISample#AddInViewCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInIsAUISample/VisualBasic/AddInViews/WPFAddInView.vb#AddInViewCode)]  
  
Ici, la vue de complément est dérivée de <xref:System.Windows.Controls.UserControl>. Par conséquent, l’interface utilisateur complément doit également dériver de <xref:System.Windows.Controls.UserControl>.  
  
<a name="AddInSideAdapter"></a>
## <a name="implementing-the-add-in-side-adapter-pipeline-segment"></a>Implémentation du segment de pipeline d’adaptateur côté complément

Bien que le contrat soit un <xref:System.AddIn.Contract.INativeHandleContract>, le complément est une <xref:System.Windows.FrameworkElement> (comme spécifié par le segment de pipeline de vue complément). Par conséquent, le <xref:System.Windows.FrameworkElement> doit être converti en un <xref:System.AddIn.Contract.INativeHandleContract> avant de traverser la limite d’isolation. Cette opération est exécutée par l’adaptateur côté complément en appelant <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>, comme illustré dans le code suivant.  
  
[!code-csharp[SimpleAddInIsAUISample#AddInSideAdapterCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.cs#addinsideadaptercode)]  
[!code-vb[SimpleAddInIsAUISample#AddInSideAdapterCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInIsAUISample/VisualBasic/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.vb#addinsideadaptercode)]

Dans le modèle de complément où un complément retourne une interface utilisateur (consultez [créer un complément que retourne une interface utilisateur](how-to-create-an-add-in-that-returns-a-ui.md)), l’adaptateur de complément converti le <xref:System.Windows.FrameworkElement> à un <xref:System.AddIn.Contract.INativeHandleContract> en appelant <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>. <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> doit également être appelée dans ce modèle, bien que vous devez implémenter une méthode à partir de laquelle écrire le code pour l’appeler. Pour cela, substituez <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> et implémentez le code qui appelle <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> si le code qui appelle <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> attend un <xref:System.AddIn.Contract.INativeHandleContract>. Dans ce cas, l’appelant sera l’adaptateur côté hôte, ce qui est traité dans une sous-section ultérieure.  
  
> [!NOTE]
>  Vous devez également substituer <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> dans ce modèle pour permettre la tabulation entre l’interface utilisateur d’application hôte et l’interface utilisateur du complément. Pour plus d’informations, consultez « Limitations des Add-In WPF » dans [vue d’ensemble des compléments WPF](wpf-add-ins-overview.md).  
  
Étant donné que l’adaptateur côté complément implémente une interface qui dérive de <xref:System.AddIn.Contract.INativeHandleContract>, vous devez également implémenter <xref:System.AddIn.Contract.INativeHandleContract.GetHandle%2A>, bien que cela soit ignoré quand <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> est remplacée.  
  
<a name="HostViewPipeline"></a>   
## <a name="implementing-the-host-view-pipeline-segment"></a>Implémentation du segment de pipeline de vue hôte

Dans ce modèle, l’application hôte attend généralement la vue hôte soit une <xref:System.Windows.FrameworkElement> sous-classe. L’adaptateur côté hôte doit convertir le <xref:System.AddIn.Contract.INativeHandleContract> à un <xref:System.Windows.FrameworkElement> après le <xref:System.AddIn.Contract.INativeHandleContract> dépasse la limite d’isolation. Car une méthode n’est pas appelée par l’application hôte pour obtenir le <xref:System.Windows.FrameworkElement>, la vue hôte doit « retourner » le <xref:System.Windows.FrameworkElement> par qui la contient. Par conséquent, la vue hôte doit dériver d’une sous-classe de <xref:System.Windows.FrameworkElement> qui peut contenir des autres interfaces utilisateur, tel que <xref:System.Windows.Controls.UserControl>. Le code suivant montre la vue hôte du contrat, implémentée en tant que la `WPFAddInHostView` classe.  

[!code-csharp[WPFAddInHostView class](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/HostViews/WPFAddInHostView.cs#HostViewCode)]
[!code-vb[WPFAddInHostView class](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInIsAUISample/VisualBasic/HostViews/WPFAddInHostView.vb#HostViewCode)]

<a name="HostSideAdapter"></a>   
## <a name="implementing-the-host-side-adapter-pipeline-segment"></a>Implémentation du segment de pipeline d’adaptateur côté hôte

Bien que le contrat soit un <xref:System.AddIn.Contract.INativeHandleContract>, l’application hôte attend un <xref:System.Windows.Controls.UserControl> (comme spécifié par la vue hôte). Par conséquent, le <xref:System.AddIn.Contract.INativeHandleContract> doit être converti en un <xref:System.Windows.FrameworkElement> après avoir traversé la limite d’isolation, avant d’être définie en tant que contenu de la vue hôte (qui dérive à son <xref:System.Windows.Controls.UserControl>).  
  
Cette opération est exécutée par l’adaptateur côté hôte, comme illustré dans le code suivant.  

[!code-csharp[Host-side adapter](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.cs#HostSideAdapterCode)]
[!code-vb[Host-side adapter](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInIsAUISample/VisualBasic/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.vb#HostSideAdapterCode)]

Comme vous pouvez le voir, l’adaptateur côté hôte acquiert le <xref:System.AddIn.Contract.INativeHandleContract> en appelant l’adaptateur côté complément <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> (méthode) (il s’agit du point où la <xref:System.AddIn.Contract.INativeHandleContract> dépasse la limite d’isolation).  
  
L’adaptateur côté hôte convertit ensuite le <xref:System.AddIn.Contract.INativeHandleContract> à un <xref:System.Windows.FrameworkElement> en appelant <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>. Enfin, le <xref:System.Windows.FrameworkElement> est défini comme le contenu de la vue hôte.  
  
<a name="AddIn"></a>   
## <a name="implementing-the-add-in"></a>Implémentation du complément

Avec l’adaptateur côté complément et la vue de complément en place, le complément peut être implémenté par dérivation de la vue de complément, comme illustré dans le code suivant.  

[!code-csharp[Add-in implementation](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/WPFAddIn1/AddInUI.xaml.cs#AddInCodeBehind)]
[!code-vb[Add-in implementation](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInIsAUISample/VisualBasic/WPFAddIn1/AddInUI.xaml.vb#AddInCodeBehind)]

Dans cet exemple, vous pouvez constater un avantage intéressant de ce modèle : complément développeurs doivent uniquement implémenter le complément (dans la mesure où il s’agit de l’interface utilisateur également), et non une classe de complément et une interface utilisateur complément.  
  
<a name="HostApp"></a>
## <a name="implementing-the-host-application"></a>Implémentation de l'application hôte.

Avec l’adaptateur côté hôte et la vue hôte étant créés, l’application hôte peut utiliser le modèle de complément .NET Framework pour ouvrir le pipeline et acquérir une vue hôte du complément. Ces étapes sont présentées dans le code suivant.  

[!code-csharp[Acquiring a host view of the add-in](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/Host/MainWindow.xaml.cs#GetUICode)]
[!code-vb[Acquiring a host view of the add-in](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInIsAUISample/VisualBasic/Host/MainWindow.xaml.vb#GetUICode)]

L’application hôte utilise le code de modèle de complément .NET Framework classique pour activer le complément, ce qui implicitement retourne la vue hôte à l’application hôte. L’application hôte affiche ensuite la vue hôte (qui est un <xref:System.Windows.Controls.UserControl>) à partir d’un <xref:System.Windows.Controls.Grid>.  
  
 Le code de traitement des interactions avec l’interface utilisateur complément s’exécute dans domaine d’application du complément. Ces interactions incluent :  
  
- Gérer le <xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.Primitives.ButtonBase.Click> événement.  
  
- Affichant le <xref:System.Windows.MessageBox>.  
  
 Cette activité est complètement isolée de l’application hôte.  
  
## <a name="see-also"></a>Voir aussi

- [Compléments et extensibilité](/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))
- [Vue d’ensemble des compléments WPF](wpf-add-ins-overview.md)
