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
# <a name="how-to-determine-if-a-page-is-browser-hosted"></a>Comment : déterminer si une page est hébergée par un navigateur
Cet exemple montre comment déterminer si un <xref:System.Windows.Controls.Page> est hébergé dans un navigateur.  
  
## <a name="example"></a>Exemple  
 Une <xref:System.Windows.Controls.Page> peut être indépendante de l’hôte et, par conséquent, peut être chargée dans plusieurs types d’hôtes différents, notamment un <xref:System.Windows.Controls.Frame>, un <xref:System.Windows.Navigation.NavigationWindow>ou un navigateur. Cela peut se produire quand vous avez un assembly de bibliothèque qui contient une ou plusieurs pages, et qui est référencé par plusieurs applications hôtes autonomes et consultables (XBAP).  
  
 L’exemple suivant montre comment utiliser <xref:System.Windows.Interop.BrowserInteropHelper.IsBrowserHosted%2A?displayProperty=nameWithType> pour déterminer si un <xref:System.Windows.Controls.Page> est hébergé dans un navigateur.  
  
 [!code-csharp[HOWTOBrowserInteropHelperSnippets#IsBrowserHostedCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOBrowserInteropHelperSnippets/CSharp/Page1.xaml.cs#isbrowserhostedcode)]
 [!code-vb[HOWTOBrowserInteropHelperSnippets#IsBrowserHostedCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOBrowserInteropHelperSnippets/visualbasic/page1.xaml.vb#isbrowserhostedcode)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Controls.Frame>
- <xref:System.Windows.Controls.Page>
