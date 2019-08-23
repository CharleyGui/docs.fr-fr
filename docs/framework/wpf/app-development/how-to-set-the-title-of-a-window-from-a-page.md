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
# <a name="how-to-set-the-title-of-a-window-from-a-page"></a><span data-ttu-id="adec4-102">Procédure : Définir le titre d’une fenêtre à partir d’une page</span><span class="sxs-lookup"><span data-stu-id="adec4-102">How to: Set the Title of a Window from a Page</span></span>
<span data-ttu-id="adec4-103">Cet exemple montre comment définir le titre de la fenêtre dans laquelle un <xref:System.Windows.Controls.Page> est hébergé.</span><span class="sxs-lookup"><span data-stu-id="adec4-103">This example shows how to set the title of the window in which a <xref:System.Windows.Controls.Page> is hosted.</span></span>  
  
## <a name="example"></a><span data-ttu-id="adec4-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="adec4-104">Example</span></span>  
 <span data-ttu-id="adec4-105">Une page peut modifier le titre de la fenêtre qui l’héberge en définissant la <xref:System.Windows.Controls.Page.WindowTitle%2A> propriété, comme suit:</span><span class="sxs-lookup"><span data-stu-id="adec4-105">A page can change the title of the window that is hosting it by setting the <xref:System.Windows.Controls.Page.WindowTitle%2A> property, like so:</span></span>  
  
 [!code-xaml[HOWTONavigationSnippets#SetPageWindowTitleXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/SetWindowTitlePage.xaml#setpagewindowtitlexaml)]  
  
> [!NOTE]
> <span data-ttu-id="adec4-106">La définition <xref:System.Windows.Controls.Page.Title%2A> de la propriété d’une page ne change pas la valeur du titre de la fenêtre.</span><span class="sxs-lookup"><span data-stu-id="adec4-106">Setting the <xref:System.Windows.Controls.Page.Title%2A> property of a page does not change the value of the window title.</span></span> <span data-ttu-id="adec4-107">Au lieu <xref:System.Windows.Controls.Page.Title%2A> de cela, spécifie le nom d’une entrée de page dans l’historique de navigation.</span><span class="sxs-lookup"><span data-stu-id="adec4-107">Instead, <xref:System.Windows.Controls.Page.Title%2A> specifies the name of a page entry in navigation history.</span></span>
