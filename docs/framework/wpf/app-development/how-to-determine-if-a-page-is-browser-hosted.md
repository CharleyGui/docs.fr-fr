---
title: 'Comment : déterminer si une page est hébergée par un navigateur'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosted pages in browser [WPF]
- pages [WPF], hosted in browser
ms.assetid: 737e0f26-8371-49b4-9579-70879e51e1aa
ms.openlocfilehash: c4cb1065807d16c1d1f5a95c8ac9c9cbe5a0fdab
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424687"
---
# <a name="how-to-determine-if-a-page-is-browser-hosted"></a><span data-ttu-id="792f3-102">Comment : déterminer si une page est hébergée par un navigateur</span><span class="sxs-lookup"><span data-stu-id="792f3-102">How to: Determine If a Page is Browser Hosted</span></span>
<span data-ttu-id="792f3-103">Cet exemple montre comment déterminer si un <xref:System.Windows.Controls.Page> est hébergé dans un navigateur.</span><span class="sxs-lookup"><span data-stu-id="792f3-103">This example demonstrates how to determine if a <xref:System.Windows.Controls.Page> is hosted in a browser.</span></span>  
  
## <a name="example"></a><span data-ttu-id="792f3-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="792f3-104">Example</span></span>  
 <span data-ttu-id="792f3-105">Une <xref:System.Windows.Controls.Page> peut être indépendante de l’hôte et, par conséquent, peut être chargée dans plusieurs types d’hôtes différents, notamment un <xref:System.Windows.Controls.Frame>, un <xref:System.Windows.Navigation.NavigationWindow>ou un navigateur.</span><span class="sxs-lookup"><span data-stu-id="792f3-105">A <xref:System.Windows.Controls.Page> can be host agnostic and, consequently, can be loaded into several different types of hosts, including a <xref:System.Windows.Controls.Frame>, a <xref:System.Windows.Navigation.NavigationWindow>, or a browser.</span></span> <span data-ttu-id="792f3-106">Cela peut se produire quand vous avez un assembly de bibliothèque qui contient une ou plusieurs pages, et qui est référencé par plusieurs applications hôtes autonomes et consultables (XBAP).</span><span class="sxs-lookup"><span data-stu-id="792f3-106">This can happen when you have a library assembly that contains one or more pages, and which is referenced by multiple standalone and browsable (XAML browser application (XBAP)) host applications.</span></span>  
  
 <span data-ttu-id="792f3-107">L’exemple suivant montre comment utiliser <xref:System.Windows.Interop.BrowserInteropHelper.IsBrowserHosted%2A?displayProperty=nameWithType> pour déterminer si un <xref:System.Windows.Controls.Page> est hébergé dans un navigateur.</span><span class="sxs-lookup"><span data-stu-id="792f3-107">The following example demonstrates how to use <xref:System.Windows.Interop.BrowserInteropHelper.IsBrowserHosted%2A?displayProperty=nameWithType> to determine if a <xref:System.Windows.Controls.Page> is hosted in a browser.</span></span>  
  
 [!code-csharp[HOWTOBrowserInteropHelperSnippets#IsBrowserHostedCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOBrowserInteropHelperSnippets/CSharp/Page1.xaml.cs#isbrowserhostedcode)]
 [!code-vb[HOWTOBrowserInteropHelperSnippets#IsBrowserHostedCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOBrowserInteropHelperSnippets/visualbasic/page1.xaml.vb#isbrowserhostedcode)]  
  
## <a name="see-also"></a><span data-ttu-id="792f3-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="792f3-108">See also</span></span>

- <xref:System.Windows.Controls.Frame>
- <xref:System.Windows.Controls.Page>
