---
title: 'Comment : lier les données aux éléments Windows Presentation Foundation (services de données WCF)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding, WCF Data Services
- WCF Data Services, data binding
ms.assetid: d6538ab0-0abe-426a-b9d9-e6f3a5ca2016
ms.openlocfilehash: d6f50fb849d958ae1109324f1055b84451bde5a9
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91191630"
---
# <a name="how-to-bind-data-to-windows-presentation-foundation-elements-wcf-data-services"></a>Comment : lier les données aux éléments Windows Presentation Foundation (services de données WCF)

Avec WCF Data Services, vous pouvez lier des éléments Windows Presentation Foundation (WPF) tels qu’un <xref:System.Windows.Controls.ListBox> ou <xref:System.Windows.Controls.ComboBox> à une instance de <xref:System.Data.Services.Client.DataServiceCollection%601> , qui gère les événements déclenchés par les contrôles pour garder <xref:System.Data.Services.Client.DataServiceContext> synchronisé avec les modifications apportées aux données dans les contrôles. Pour plus d’informations, consultez [liaison de données à des contrôles](binding-data-to-controls-wcf-data-services.md).  
  
 L'exemple dans cette rubrique utilise l'exemple de service de données Northwind et des classes de service de données clientes générées automatiquement. Ce service et les classes de données clientes sont créés lorsque vous terminez le [démarrage rapide WCF Data Services](quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Exemple  

 L'exemple suivant provient de la page code-behind d'une page XAML (Extensible Application Markup Language) qui définit la fenêtre `SalesOrders` dans WPF. Lorsque la fenêtre est chargée, une <xref:System.Data.Services.Client.DataServiceCollection%601> est créée en fonction du résultat d’une requête qui retourne des clients, filtrée par pays/région. Toutes les pages de ce résultat paginé sont chargées ainsi que les ordres connexes, et sont liées à la propriété <xref:System.Windows.FrameworkElement.DataContext%2A> du <xref:System.Windows.Controls.StackPanel> qui est le contrôle de disposition racine pour la fenêtre WPF. Pour plus d’informations, consultez chargement d’un [contenu différé](loading-deferred-content-wcf-data-services.md).  
  
 [!code-csharp[Astoria Northwind Client#BindPagedData](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorderswpf3.xaml.cs#bindpageddata)]
 [!code-vb[Astoria Northwind Client#BindPagedData](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderswpf3.xaml.vb#bindpageddata)]  
  
## <a name="example"></a>Exemple  

 Le code XAML suivant définit la fenêtre `SalesOrders` dans WPF pour l'exemple précédent.  
  
 [!code-xaml[Astoria Northwind Client#BindPagedDataXaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderswpf3.xaml#bindpageddataxaml)]  
  
## <a name="example"></a>Exemple  

 L'exemple suivant provient de la page code-behind d'une page XAML (Extensible Application Markup Language) qui définit la fenêtre `SalesOrders` dans WPF. Lorsque la fenêtre est chargée, un <xref:System.Data.Services.Client.DataServiceCollection%601> est créé en fonction du résultat d’une requête qui retourne des clients avec des objets connexes, filtrés par pays/région. Ce résultat est lié à la propriété <xref:System.Windows.FrameworkElement.DataContext%2A> du <xref:System.Windows.Controls.StackPanel> qui est le contrôle de disposition racine pour la fenêtre WPF.  
  
 [!code-csharp[Astoria Northwind Client#WpfDataBinding](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorderswpf.xaml.cs#wpfdatabinding)]
 [!code-vb[Astoria Northwind Client#WpfDataBinding](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderswpf.xaml.vb#wpfdatabinding)]  
  
## <a name="example"></a>Exemple  

 Le code XAML suivant définit la fenêtre `SalesOrders` dans WPF pour l'exemple précédent.  
  
 [!code-xaml[Astoria Northwind Client#WpfDataBindingXaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderswpf.xaml#wpfdatabindingxaml)]
