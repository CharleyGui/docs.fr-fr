---
title: 'Procédure : Naviguer en avant ou en arrière dans l’historique de navigation'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- history [WPF], navigating forward
- navigation [WPF], through navigation history (forward)
ms.assetid: 5939d574-5f53-469e-85f5-1f2b13607caa
ms.openlocfilehash: 85d3562246170901d83d6314caec5747d52fb9a0
ms.sourcegitcommit: 10736f243dd2296212e677e207102c463e5f143e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/06/2019
ms.locfileid: "68817968"
---
# <a name="how-to-navigate-forward-or-back-through-navigation-history"></a>Procédure : Naviguer en avant ou en arrière dans l’historique de navigation
Cet exemple montre comment naviguer vers l’avant ou vers l’arrière dans les entrées de l’historique de navigation.  
  
## <a name="example"></a>Exemple  
 Le code qui s’exécute à partir du contenu des hôtes suivants peut naviguer vers l’avant ou vers l’arrière dans l’historique de navigation, une entrée à la fois.  
  
- <xref:System.Windows.Navigation.NavigationWindow>à<xref:System.Windows.Navigation.NavigationService>  
  
- <xref:System.Windows.Controls.Frame>à<xref:System.Windows.Navigation.NavigationService>  
  
- Internet Explorer  
  
 Avant de pouvoir naviguer vers l’avant d’une entrée, vous devez d’abord vérifier qu’il existe des entrées dans l’historique de navigation avant en examinant la propriété **CanGoForward** . Pour naviguer vers l’avant d’une entrée, vous appelez la méthode **GoForward** . Cela est illustré dans l’exemple suivant:  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateForwardCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/HomePage.xaml.cs#navigateforwardcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateForwardCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/homepage.xaml.vb#navigateforwardcode)]  
  
 Avant de pouvoir revenir à une entrée, vous devez d’abord vérifier qu’il existe des entrées dans l’historique de navigation arrière en examinant la propriété **CanGoBack** . Pour revenir en arrière d’une entrée, vous devez appeler la méthode **GoBack** . Cela est illustré dans l’exemple suivant:  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateBackCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/HomePage.xaml.cs#navigatebackcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateBackCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/homepage.xaml.vb#navigatebackcode)]  
  
 **CanGoForward**, **GoForward**, **CanGoBack**et **GoBack** sont implémentés par <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Frame>et <xref:System.Windows.Navigation.NavigationService>.  
  
> [!NOTE]
>  Si vous appelez **GoForward**et qu’il n’y a pas d’entrée dans l’historique de navigation avant, ou si vous appelez **GoBack**et qu’il n’y a pas <xref:System.InvalidOperationException> d’entrée dans l’historique de navigation arrière, une exception est levée.
