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
ms.openlocfilehash: 86590c2794339ac22cbc8ec5e11224736133e870
ms.sourcegitcommit: 10736f243dd2296212e677e207102c463e5f143e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/06/2019
ms.locfileid: "68817981"
---
# <a name="how-to-navigate-back-through-navigation-history"></a><span data-ttu-id="3c2bd-102">Procédure : Revenir en arrière dans l’historique de navigation</span><span class="sxs-lookup"><span data-stu-id="3c2bd-102">How to: Navigate Back Through Navigation History</span></span>
<span data-ttu-id="3c2bd-103">Cet exemple montre comment accéder aux entrées de l’historique de navigation arrière.</span><span class="sxs-lookup"><span data-stu-id="3c2bd-103">This example illustrates how to navigate to entries in back navigation history.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3c2bd-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="3c2bd-104">Example</span></span>  
 <span data-ttu-id="3c2bd-105">Le code qui s’exécute à partir du contenu hébergé dans <xref:System.Windows.Navigation.NavigationWindow>un <xref:System.Windows.Controls.Frame> , <xref:System.Windows.Navigation.NavigationService>à l’aide de ou d’Internet Explorer peut naviguer en arrière dans l’historique de navigation, une entrée à la fois.</span><span class="sxs-lookup"><span data-stu-id="3c2bd-105">Code that is running from content that is hosted in a <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Frame> using <xref:System.Windows.Navigation.NavigationService>, or Internet Explorer can navigate back through navigation history, one entry at a time.</span></span>  
  
 <span data-ttu-id="3c2bd-106">Pour revenir à une entrée, vous devez d’abord vérifier qu’il existe des entrées dans l’historique de navigation arrière, en examinant la propriété **CanGoBack** , avant de revenir à une entrée, en appelant la méthode **GoBack** .</span><span class="sxs-lookup"><span data-stu-id="3c2bd-106">Navigating back one entry requires first checking that there are entries in back navigation history, by inspecting the **CanGoBack** property, before navigating back one entry, by calling the **GoBack** method.</span></span> <span data-ttu-id="3c2bd-107">Cela est illustré dans l’exemple suivant:</span><span class="sxs-lookup"><span data-stu-id="3c2bd-107">This is illustrated in the following example:</span></span>  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateBackCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/HomePage.xaml.cs#navigatebackcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateBackCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/homepage.xaml.vb#navigatebackcode)]  
  
 <span data-ttu-id="3c2bd-108">**CanGoBack** et **GoBack** sont implémentés <xref:System.Windows.Navigation.NavigationWindow>par <xref:System.Windows.Controls.Frame>, et <xref:System.Windows.Navigation.NavigationService>.</span><span class="sxs-lookup"><span data-stu-id="3c2bd-108">**CanGoBack** and **GoBack** are implemented by <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Frame>, and <xref:System.Windows.Navigation.NavigationService>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3c2bd-109">Si vous appelez **GoBack**et qu’il n’y a pas d’entrée dans l’historique <xref:System.InvalidOperationException> de navigation arrière, un est déclenché.</span><span class="sxs-lookup"><span data-stu-id="3c2bd-109">If you call **GoBack**, and there are no entries in back navigation history, an <xref:System.InvalidOperationException> is raised.</span></span>
