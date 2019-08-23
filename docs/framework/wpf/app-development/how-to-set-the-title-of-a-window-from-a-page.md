---
title: 'Procédure : Définir le titre d’une fenêtre à partir d’une page'
ms.date: 03/30/2017
helpviewer_keywords:
- windows [WPF], setting title from a page
- title of window [WPF], setting from a page
- pages [WPF], setting window title from
ms.assetid: fecf0d19-3eb6-4f8c-a44f-ff1b6f2b34b3
ms.openlocfilehash: 0f618af89965822b0df96a264997dabd9cae7608
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940784"
---
# <a name="how-to-set-the-title-of-a-window-from-a-page"></a>Procédure : Définir le titre d’une fenêtre à partir d’une page
Cet exemple montre comment définir le titre de la fenêtre dans laquelle un <xref:System.Windows.Controls.Page> est hébergé.  
  
## <a name="example"></a>Exemple  
 Une page peut modifier le titre de la fenêtre qui l’héberge en définissant la <xref:System.Windows.Controls.Page.WindowTitle%2A> propriété, comme suit:  
  
 [!code-xaml[HOWTONavigationSnippets#SetPageWindowTitleXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/SetWindowTitlePage.xaml#setpagewindowtitlexaml)]  
  
> [!NOTE]
> La définition <xref:System.Windows.Controls.Page.Title%2A> de la propriété d’une page ne change pas la valeur du titre de la fenêtre. Au lieu <xref:System.Windows.Controls.Page.Title%2A> de cela, spécifie le nom d’une entrée de page dans l’historique de navigation.
