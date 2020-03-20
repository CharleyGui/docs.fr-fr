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
# <a name="how-to-create-an-add-in-that-returns-a-ui"></a>Comment : créer un complément qui retourne une interface utilisateur
Cet exemple montre comment créer un add-in qui renvoie une Fondation de présentation Windows (WPF) à une application autonome WPF hôte.  
  
 L’add-in renvoie une interface utilisateur qui est un contrôle utilisateur WPF. Le contenu du contrôle utilisateur est un bouton unique qui, quand on clique dessus, affiche une boîte de message. L’application autonome WPF héberge l’add-in et affiche le contrôle de l’utilisateur (retourné par l’add-in) comme le contenu de la fenêtre d’application principale.  
  
 **Conditions préalables**  
  
 Cet exemple met en évidence les extensions WPF au modèle d’add-in .NET Framework qui permettent ce scénario, et suppose ce qui suit :  
  
- Connaissance du modèle d’ajout du cadre .NET, y compris le pipeline, l’ajout et le développement de l’hôte. Si vous n’êtes pas familier avec ces concepts, voir [Add-ins et Extensibility](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100)). Pour un tutoriel qui démontre la mise en œuvre d’un pipeline, un add-in, et une application hôte, voir [Procédure pas à pas: Créer une application extensible](/previous-versions/dotnet/netframework-4.0/bb788290(v%3dvs.100)).  
  
- Connaissance des extensions WPF au modèle d’add-in .NET Framework, qui peut être trouvé ici: [WPF Add-Ins Aperçu](wpf-add-ins-overview.md).  
  
## <a name="example"></a> Exemple  
 Pour créer un add-in qui renvoie une interface utilisateur WPF nécessite un code spécifique pour chaque segment de pipeline, l’add-in, et l’application hôte.  

<a name="Contract"></a>
## <a name="implementing-the-contract-pipeline-segment"></a>Implémentation du segment de pipeline de contrat  
 Une méthode doit être définie par le contrat de retour d’une assurance-chômage, et sa valeur de retour doit être de type <xref:System.AddIn.Contract.INativeHandleContract>. Cela est démontré `GetAddInUI` par `IWPFAddInContract` la méthode du contrat dans le code suivant.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#ContractCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/Contracts/IWPFAddInContract.cs#contractcode)]
 [!code-vb[SimpleAddInReturnsAUISample#ContractCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/Contracts/IWPFAddInContract.vb#contractcode)]  
  
<a name="AddInView"></a>
## <a name="implementing-the-add-in-view-pipeline-segment"></a>Implémentation du segment de pipeline de vue de complément  
 Parce que l’add-in implémente les <xref:System.Windows.FrameworkElement>IA qu’il fournit comme sous-classes `IWPFAddInView.GetAddInUI` de , la <xref:System.Windows.FrameworkElement>méthode sur l’add-in vue qui se corrèle à doit retourner une valeur de type . Le code suivant illustre la vue de complément du contrat, implémentée en tant qu’interface.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInViewCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/AddInViews/IWPFAddInView.cs#addinviewcode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInViewCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/AddInViews/IWPFAddInView.vb#addinviewcode)]  
  
<a name="AddInSideAdapter"></a>
## <a name="implementing-the-add-in-side-adapter-pipeline-segment"></a>Implémentation du segment de pipeline d’adaptateur côté complément  
 La méthode du <xref:System.AddIn.Contract.INativeHandleContract>contrat renvoie un <xref:System.Windows.FrameworkElement> , mais l’add-in renvoie un (comme spécifié par la vue add-in). Par conséquent, <xref:System.Windows.FrameworkElement> le doit être <xref:System.AddIn.Contract.INativeHandleContract> converti en un avant de traverser la limite d’isolement. Ce travail est effectué par l’adaptateur <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>add-in-side en appelant, comme indiqué dans le code suivant.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInSideAdapterCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.cs#addinsideadaptercode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInSideAdapterCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.vb#addinsideadaptercode)]  
  
<a name="HostView"></a>
## <a name="implementing-the-host-view-pipeline-segment"></a>Implémentation du segment de pipeline de vue hôte  
 Parce que l’application <xref:System.Windows.FrameworkElement>hôte affichera un , la `IWPFAddInHostView.GetAddInUI` méthode sur la <xref:System.Windows.FrameworkElement>vue hôte qui est corrélée à doit retourner une valeur de type . Le code suivant illustre la vue hôte du contrat, implémentée en tant qu’interface.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#HostViewCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/HostViews/IWPFAddInHostView.cs#hostviewcode)]
 [!code-vb[SimpleAddInReturnsAUISample#HostViewCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/HostViews/IWPFAddInHostView.vb#hostviewcode)]  
  
<a name="HostSideAdapter"></a>
## <a name="implementing-the-host-side-adapter-pipeline-segment"></a>Implémentation du segment de pipeline d’adaptateur côté hôte  
 La méthode du <xref:System.AddIn.Contract.INativeHandleContract>contrat renvoie un <xref:System.Windows.FrameworkElement> , mais l’application hôte s’attend à un (comme spécifié par la vue hôte). Par conséquent, <xref:System.AddIn.Contract.INativeHandleContract> le doit être <xref:System.Windows.FrameworkElement> converti en après avoir franchi la limite d’isolement. Ce travail est effectué par l’adaptateur côté hôte en appelant, <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>comme indiqué dans le code suivant.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#HostSideAdapterCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.cs#hostsideadaptercode)]
 [!code-vb[SimpleAddInReturnsAUISample#HostSideAdapterCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.vb#hostsideadaptercode)]  
  
<a name="AddIn"></a>
## <a name="implementing-the-add-in"></a>Implémentation du complément  
 Avec l’adaptateur add-in-side et add-in vue`WPFAddIn1.AddIn`créée, `IWPFAddInView.GetAddInUI` l’add-in ( ) doit implémenter la méthode pour retourner un <xref:System.Windows.FrameworkElement> objet (un <xref:System.Windows.Controls.UserControl> dans cet exemple). La mise <xref:System.Windows.Controls.UserControl>en `AddInUI`œuvre du , , est indiquée par le code suivant.  
  
 [!code-xaml[SimpleAddInReturnsAUISample#AddInUIMarkup](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddInUI.xaml#addinuimarkup)]  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInUICodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddInUI.xaml.cs#addinuicodebehind)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInUICodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/WPFAddIn1/AddInUI.xaml.vb#addinuicodebehind)]  
  
 La mise `IWPFAddInView.GetAddInUI` en œuvre de l’add-in `AddInUI`doit simplement retourner une nouvelle instance de , comme le montre le code suivant.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddIn.cs#addincode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/WPFAddIn1/AddIn.vb#addincode)]  
  
<a name="App"></a>
## <a name="implementing-the-host-application"></a>Implémentation de l'application hôte.  
 Avec l’adaptateur côté hôte et la vue d’hôte créée, l’application hôte peut utiliser le modèle d’add-in .NET Framework pour ouvrir le pipeline, acquérir une vue d’hôte de l’add-in, et appeler la `IWPFAddInHostView.GetAddInUI` méthode. Ces étapes sont présentées dans le code suivant.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#GetUICode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/Host/MainWindow.xaml.cs#getuicode)]
 [!code-vb[SimpleAddInReturnsAUISample#GetUICode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/Host/MainWindow.xaml.vb#getuicode)]  
  
## <a name="see-also"></a>Voir aussi

- [Compléments et extensibilité](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))
- [Vue d’ensemble des compléments WPF](wpf-add-ins-overview.md)
