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
# <a name="how-to-navigate-forward-or-back-through-navigation-history"></a><span data-ttu-id="57de4-102">Procédure : Naviguer en avant ou en arrière dans l’historique de navigation</span><span class="sxs-lookup"><span data-stu-id="57de4-102">How to: Navigate Forward or Back Through Navigation History</span></span>
<span data-ttu-id="57de4-103">Cet exemple montre comment naviguer vers l’avant ou vers l’arrière dans les entrées de l’historique de navigation.</span><span class="sxs-lookup"><span data-stu-id="57de4-103">This example illustrates how to navigate forward or back to entries in navigation history.</span></span>  
  
## <a name="example"></a><span data-ttu-id="57de4-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="57de4-104">Example</span></span>  
 <span data-ttu-id="57de4-105">Le code qui s’exécute à partir du contenu des hôtes suivants peut naviguer vers l’avant ou vers l’arrière dans l’historique de navigation, une entrée à la fois.</span><span class="sxs-lookup"><span data-stu-id="57de4-105">Code that runs from content in the following hosts can navigate forward or back through navigation history, one entry at a time.</span></span>  
  
- <span data-ttu-id="57de4-106"><xref:System.Windows.Navigation.NavigationWindow>à<xref:System.Windows.Navigation.NavigationService></span><span class="sxs-lookup"><span data-stu-id="57de4-106"><xref:System.Windows.Navigation.NavigationWindow> using <xref:System.Windows.Navigation.NavigationService></span></span>  
  
- <span data-ttu-id="57de4-107"><xref:System.Windows.Controls.Frame>à<xref:System.Windows.Navigation.NavigationService></span><span class="sxs-lookup"><span data-stu-id="57de4-107"><xref:System.Windows.Controls.Frame> using <xref:System.Windows.Navigation.NavigationService></span></span>  
  
- <span data-ttu-id="57de4-108">Internet Explorer</span><span class="sxs-lookup"><span data-stu-id="57de4-108">Internet Explorer</span></span>  
  
 <span data-ttu-id="57de4-109">Avant de pouvoir naviguer vers l’avant d’une entrée, vous devez d’abord vérifier qu’il existe des entrées dans l’historique de navigation avant en examinant la propriété **CanGoForward** .</span><span class="sxs-lookup"><span data-stu-id="57de4-109">Before you can navigate forward one entry, you must first check that there are entries in forward navigation history by inspecting the **CanGoForward** property.</span></span> <span data-ttu-id="57de4-110">Pour naviguer vers l’avant d’une entrée, vous appelez la méthode **GoForward** .</span><span class="sxs-lookup"><span data-stu-id="57de4-110">To navigate forward one entry, you call the **GoForward** method.</span></span> <span data-ttu-id="57de4-111">Cela est illustré dans l’exemple suivant:</span><span class="sxs-lookup"><span data-stu-id="57de4-111">This is illustrated in the following example:</span></span>  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateForwardCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/HomePage.xaml.cs#navigateforwardcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateForwardCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/homepage.xaml.vb#navigateforwardcode)]  
  
 <span data-ttu-id="57de4-112">Avant de pouvoir revenir à une entrée, vous devez d’abord vérifier qu’il existe des entrées dans l’historique de navigation arrière en examinant la propriété **CanGoBack** .</span><span class="sxs-lookup"><span data-stu-id="57de4-112">Before you can navigate back one entry, you must first check that there are entries in back navigation history by inspecting the **CanGoBack** property.</span></span> <span data-ttu-id="57de4-113">Pour revenir en arrière d’une entrée, vous devez appeler la méthode **GoBack** .</span><span class="sxs-lookup"><span data-stu-id="57de4-113">To navigate back one entry, you call the **GoBack** method.</span></span> <span data-ttu-id="57de4-114">Cela est illustré dans l’exemple suivant:</span><span class="sxs-lookup"><span data-stu-id="57de4-114">This is illustrated in the following example:</span></span>  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateBackCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/HomePage.xaml.cs#navigatebackcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateBackCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/homepage.xaml.vb#navigatebackcode)]  
  
 <span data-ttu-id="57de4-115">**CanGoForward**, **GoForward**, **CanGoBack**et **GoBack** sont implémentés par <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Frame>et <xref:System.Windows.Navigation.NavigationService>.</span><span class="sxs-lookup"><span data-stu-id="57de4-115">**CanGoForward**, **GoForward**, **CanGoBack**, and **GoBack** are implemented by <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Frame>, and <xref:System.Windows.Navigation.NavigationService>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="57de4-116">Si vous appelez **GoForward**et qu’il n’y a pas d’entrée dans l’historique de navigation avant, ou si vous appelez **GoBack**et qu’il n’y a pas <xref:System.InvalidOperationException> d’entrée dans l’historique de navigation arrière, une exception est levée.</span><span class="sxs-lookup"><span data-stu-id="57de4-116">If you call **GoForward**, and there are no entries in forward navigation history, or if you call **GoBack**, and there are no entries in back navigation history, an <xref:System.InvalidOperationException> is thrown.</span></span>
