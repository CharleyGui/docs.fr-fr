---
title: 'Procédure : Revenir en arrière dans l’historique de navigation'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- history [WPF], navigating back
- navigation [WPF], through navigation history (back)
ms.assetid: 9343234b-d864-441d-b8a7-d895cba80a87
ms.openlocfilehash: 53b32e145390d7052262042c7a793699c163b373
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69969351"
---
# <a name="how-to-navigate-back-through-navigation-history"></a>Procédure : Revenir en arrière dans l’historique de navigation
Cet exemple montre comment accéder aux entrées de l’historique de navigation arrière.  
  
## <a name="example"></a>Exemple  
 Le code qui s’exécute à partir du contenu hébergé dans <xref:System.Windows.Navigation.NavigationWindow>un <xref:System.Windows.Controls.Frame> , <xref:System.Windows.Navigation.NavigationService>à l’aide de ou d’Internet Explorer peut naviguer en arrière dans l’historique de navigation, une entrée à la fois.  
  
 Pour revenir à une entrée, vous devez d’abord vérifier qu’il existe des entrées dans l’historique de navigation arrière, en examinant la propriété **CanGoBack** , avant de revenir à une entrée, en appelant la méthode **GoBack** . Cela est illustré dans l’exemple suivant:  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateBackCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/HomePage.xaml.cs#navigatebackcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateBackCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/homepage.xaml.vb#navigatebackcode)]  
  
 **CanGoBack** et **GoBack** sont implémentés <xref:System.Windows.Navigation.NavigationWindow>par <xref:System.Windows.Controls.Frame>, et <xref:System.Windows.Navigation.NavigationService>.  
  
> [!NOTE]
> Si vous appelez **GoBack**et qu’il n’y a pas d’entrée dans l’historique <xref:System.InvalidOperationException> de navigation arrière, un est déclenché.
