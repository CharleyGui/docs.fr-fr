---
title: Guide pratique pour créer un complément qui est une interface utilisateur
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
ms.openlocfilehash: 339231031b9e57b9f00a2aeb6fbbde8ad66c1ad9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141027"
---
# <a name="how-to-create-an-add-in-that-is-a-ui"></a>Guide pratique pour créer un complément qui est une interface utilisateur
Cet exemple montre comment créer un add-in qui est une Fondation de présentation Windows (WPF) qui est hébergé par une application autonome WPF.  
  
 L’add-in est une interface utilisateur qui est un contrôle utilisateur WPF. Le contenu du contrôle utilisateur est un bouton unique qui, quand on clique dessus, affiche une boîte de message. L’application autonome WPF héberge l’interface utilisateur add-in comme le contenu de la fenêtre d’application principale.  
  
 **Conditions préalables**  
  
 Cet exemple met en évidence les extensions WPF au modèle d’add-in .NET Framework qui permettent ce scénario, et suppose ce qui suit :  
  
- Connaissance du modèle d’ajout du cadre .NET, y compris le pipeline, l’ajout et le développement de l’hôte. Si vous n’êtes pas familier avec ces concepts, voir [Add-ins et Extensibility](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100)). Pour un tutoriel qui démontre la mise en œuvre d’un pipeline, un add-in, et une application hôte, voir [Procédure pas à pas: Créer une application extensible](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb788290(v%3dvs.100)).  
  
- Connaissance des extensions WPF au modèle d’add-in .NET Framework. Voir [WPF Add-Ins Overview](wpf-add-ins-overview.md).  
  
## <a name="example"></a> Exemple  
 Pour créer un add-in qui est une interface utilisateur WPF nécessite un code spécifique pour chaque segment de pipeline, l’add-in, et l’application hôte.  

<a name="Contract"></a>
## <a name="implementing-the-contract-pipeline-segment"></a>Implémentation du segment de pipeline de contrat

Lorsqu’un add-in est une interface utilisateur, le <xref:System.AddIn.Contract.INativeHandleContract>contrat pour l’add-in doit mettre en œuvre . Dans `IWPFAddInContract` l’exemple, <xref:System.AddIn.Contract.INativeHandleContract>implémente , comme indiqué dans le code suivant.  
  
[!code-csharp[SimpleAddInIsAUISample#ContractCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/Contracts/IWPFAddInContract.cs#contractcode)]
[!code-vb[SimpleAddInIsAUISample#ContractCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInIsAUISample/VisualBasic/Contracts/IWPFAddInContract.vb#contractcode)]

<a name="AddInViewPipeline"></a>
## <a name="implementing-the-add-in-view-pipeline-segment"></a>Implémentation du segment de pipeline de vue de complément

Parce que l’add-in est mis <xref:System.Windows.FrameworkElement> en œuvre comme une <xref:System.Windows.FrameworkElement>sous-classe du type, l’add-in vue doit également sous-classe . Le code suivant montre l’add-in vue `WPFAddInView` du contrat, mis en œuvre comme la classe.  
  
[!code-csharp[SimpleAddInIsAUISample#AddInViewCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/AddInViews/WPFAddInView.cs#addinviewcode)]  
[!code-vb[SimpleAddInIsAUISample#AddInViewCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInIsAUISample/VisualBasic/AddInViews/WPFAddInView.vb#AddInViewCode)]  
  
Ici, la vue add-in <xref:System.Windows.Controls.UserControl>est dérivée de . Par conséquent, l’interface utilisateur add-in devrait également dériver de <xref:System.Windows.Controls.UserControl>.  
  
<a name="AddInSideAdapter"></a>
## <a name="implementing-the-add-in-side-adapter-pipeline-segment"></a>Implémentation du segment de pipeline d’adaptateur côté complément

Bien que le <xref:System.AddIn.Contract.INativeHandleContract>contrat soit un <xref:System.Windows.FrameworkElement> , l’add-in est un (comme spécifié par le segment de pipeline de vue add-in). Par conséquent, le <xref:System.Windows.FrameworkElement> doit <xref:System.AddIn.Contract.INativeHandleContract> être converti en un avant de traverser la limite d’isolement. Ce travail est effectué par l’adaptateur <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>add-in-side en appelant, comme indiqué dans le code suivant.  
  
[!code-csharp[SimpleAddInIsAUISample#AddInSideAdapterCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.cs#addinsideadaptercode)]  
[!code-vb[SimpleAddInIsAUISample#AddInSideAdapterCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInIsAUISample/VisualBasic/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.vb#addinsideadaptercode)]

Dans le modèle add-in où un add-in renvoie une interface utilisateur (voir [Créer un Add-In Qui renvoie une interface utilisateur](how-to-create-an-add-in-that-returns-a-ui.md)), l’adaptateur add-in converti le <xref:System.Windows.FrameworkElement> à un <xref:System.AddIn.Contract.INativeHandleContract> appel <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>. <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>doit également être appelé dans ce modèle, bien que vous ayez besoin de mettre en œuvre une méthode à partir de laquelle écrire le code pour l’appeler. Vous le faites en <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> dominant et en <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> implémentant le <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> code qui <xref:System.AddIn.Contract.INativeHandleContract>appelle si le code qui appelle s’attend à un . Dans ce cas, l’appelant sera l’adaptateur côté hôte, ce qui est traité dans une sous-section ultérieure.  
  
> [!NOTE]
> Vous devez également <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> remplacer ce modèle pour activer le tabbing entre l’interface utilisateur d’application hôte et l’interface utilisateur add-in. Pour plus d’informations, voir "WPF Add-In Limitations" dans [WPF Add-Ins Overview](wpf-add-ins-overview.md).  
  
Parce que l’adaptateur add-in-side implémente une <xref:System.AddIn.Contract.INativeHandleContract.GetHandle%2A>interface qui dérive <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> de , vous avez également besoin d’implémenter <xref:System.AddIn.Contract.INativeHandleContract>, bien que cela soit ignoré quand est annulé.  
  
<a name="HostViewPipeline"></a>
## <a name="implementing-the-host-view-pipeline-segment"></a>Implémentation du segment de pipeline de vue hôte

Dans ce modèle, l’application hôte s’attend généralement à ce que la vue de l’hôte soit une <xref:System.Windows.FrameworkElement> sous-classe. L’adaptateur côté hôte <xref:System.AddIn.Contract.INativeHandleContract> doit <xref:System.Windows.FrameworkElement> convertir <xref:System.AddIn.Contract.INativeHandleContract> le après la bordure d’isolement. Parce qu’une méthode n’est pas appelée <xref:System.Windows.FrameworkElement>par l’application hôte <xref:System.Windows.FrameworkElement> pour obtenir le , la vue hôte doit "retourner" le en le contenant. Par conséquent, la vue de l’hôte doit dériver d’une sous-classe de <xref:System.Windows.FrameworkElement> ce qui peut contenir d’autres IA, tels que <xref:System.Windows.Controls.UserControl>. Le code suivant montre la vue de `WPFAddInHostView` l’hôte du contrat, mis en œuvre comme la classe.  

[!code-csharp[WPFAddInHostView class](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/HostViews/WPFAddInHostView.cs#HostViewCode)]
[!code-vb[WPFAddInHostView class](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInIsAUISample/VisualBasic/HostViews/WPFAddInHostView.vb#HostViewCode)]

<a name="HostSideAdapter"></a>
## <a name="implementing-the-host-side-adapter-pipeline-segment"></a>Implémentation du segment de pipeline d’adaptateur côté hôte

Bien que le <xref:System.AddIn.Contract.INativeHandleContract>contrat soit un <xref:System.Windows.Controls.UserControl> , l’application hôte s’attend à un (comme spécifié par la vue hôte). Par conséquent, <xref:System.AddIn.Contract.INativeHandleContract> le doit être <xref:System.Windows.FrameworkElement> converti en un après avoir franchi la limite d’isolement, avant d’être défini comme contenu de la vue hôte (qui dérive de <xref:System.Windows.Controls.UserControl>).  
  
Cette opération est exécutée par l’adaptateur côté hôte, comme illustré dans le code suivant.  

[!code-csharp[Host-side adapter](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.cs#HostSideAdapterCode)]
[!code-vb[Host-side adapter](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInIsAUISample/VisualBasic/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.vb#HostSideAdapterCode)]

Comme vous pouvez le voir, l’adaptateur côté hôte acquiert <xref:System.AddIn.Contract.INativeHandleContract> <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> le en appelant la <xref:System.AddIn.Contract.INativeHandleContract> méthode de l’adaptateur add-in-side (c’est le point où les croisements de la limite d’isolement).  
  
L’adaptateur côté hôte <xref:System.AddIn.Contract.INativeHandleContract> convertit <xref:System.Windows.FrameworkElement> ensuite <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>le en un appel . Enfin, <xref:System.Windows.FrameworkElement> le est défini comme le contenu de la vue hôte.  
  
<a name="AddIn"></a>
## <a name="implementing-the-add-in"></a>Implémentation du complément

Avec l’adaptateur côté complément et la vue de complément en place, le complément peut être implémenté par dérivation de la vue de complément, comme illustré dans le code suivant.  

[!code-csharp[Add-in implementation](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/WPFAddIn1/AddInUI.xaml.cs#AddInCodeBehind)]
[!code-vb[Add-in implementation](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInIsAUISample/VisualBasic/WPFAddIn1/AddInUI.xaml.vb#AddInCodeBehind)]

De cet exemple, vous pouvez voir un avantage intéressant de ce modèle: les développeurs add-in seulement besoin de mettre en œuvre l’add-in (puisqu’il s’agit de l’interface utilisateur ainsi), plutôt que à la fois une classe add-in et une interface utilisateur add-in.  
  
<a name="HostApp"></a>
## <a name="implementing-the-host-application"></a>Implémentation de l'application hôte.

Avec l’adaptateur côté hôte et la vue d’hôte créée, l’application hôte peut utiliser le modèle d’add-in .NET Framework pour ouvrir le pipeline et acquérir une vue d’hôte de l’add-in. Ces étapes sont présentées dans le code suivant.  

[!code-csharp[Acquiring a host view of the add-in](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/Host/MainWindow.xaml.cs#GetUICode)]
[!code-vb[Acquiring a host view of the add-in](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInIsAUISample/VisualBasic/Host/MainWindow.xaml.vb#GetUICode)]

L’application hôte utilise le code modélatif typique .NET Framework pour activer l’add-in, qui renvoie implicitement la vue hôte à l’application hôte. L’application hôte affiche ensuite la <xref:System.Windows.Controls.UserControl>vue hôte <xref:System.Windows.Controls.Grid>(qui est a ) à partir d’un .  
  
 Le code pour traiter les interactions avec l’interface utilisateur add-in s’exécute dans le domaine de l’application add-in. Ces interactions incluent :  
  
- Gérer <xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.Primitives.ButtonBase.Click> l’événement.  
  
- Affichage <xref:System.Windows.MessageBox>de la .  
  
 Cette activité est complètement isolée de l’application hôte.  
  
## <a name="see-also"></a>Voir aussi

- [Compléments et extensibilité](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))
- [Vue d’ensemble des compléments WPF](wpf-add-ins-overview.md)
