---
title: 'Comment : naviguer vers une page'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- pages [WPF], navigating to
- navigation [WPF], to page
ms.assetid: 2a556fc0-748b-417f-a58a-0d05a7afb66f
ms.openlocfilehash: 25a0dbbc609c7b6f8f2878d2068e61e492a59c7e
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582540"
---
# <a name="how-to-navigate-to-a-page"></a>Comment : naviguer vers une page
Cet exemple illustre plusieurs manières de naviguer dans une page à partir d’une <xref:System.Windows.Navigation.NavigationWindow>.  
  
## <a name="example"></a>Exemple  
 Une <xref:System.Windows.Navigation.NavigationWindow> peut accéder à une page à l’aide d’un des éléments suivants :  
  
- La propriété <xref:System.Windows.Navigation.NavigationWindow.Source%2A>.  
  
- Méthode <xref:System.Windows.Navigation.NavigationWindow.Navigate%2A>  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateToPageCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/MainWindow.xaml.cs#navigatetopagecode)]
 [!code-vb[HOWTONavigationSnippets#NavigateToPageCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/mainwindow.xaml.vb#navigatetopagecode)]  
  
> [!NOTE]
> Les URI (Uniform Resource Identifiers) peuvent être relatifs ou absolus. Pour plus d’informations, consultez [URI à en-tête pack dans WPF](pack-uris-in-wpf.md).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Controls.Frame>
- <xref:System.Windows.Controls.Page>
- <xref:System.Windows.Navigation.NavigationService>
