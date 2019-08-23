---
title: 'Procédure : Définir la largeur d’une fenêtre à partir d’une page'
ms.date: 03/30/2017
helpviewer_keywords:
- width of windows [WPF], setting from a page
- windows [WPF], setting width from a page
- pages [WPF], setting window width from
ms.assetid: 31601c92-7889-472a-b07e-bf675ad21c92
ms.openlocfilehash: 1e16b75ecb85550facdf24a5b9e341cf0c061178
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940777"
---
# <a name="how-to-set-the-width-of-a-window-from-a-page"></a><span data-ttu-id="f6ade-102">Procédure : Définir la largeur d’une fenêtre à partir d’une page</span><span class="sxs-lookup"><span data-stu-id="f6ade-102">How to: Set the Width of a Window from a Page</span></span>
<span data-ttu-id="f6ade-103">Cet exemple montre comment définir la largeur de la fenêtre à partir d’un <xref:System.Windows.Controls.Page>.</span><span class="sxs-lookup"><span data-stu-id="f6ade-103">This example illustrates how to set the width of the window from a <xref:System.Windows.Controls.Page>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f6ade-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="f6ade-104">Example</span></span>  
 <span data-ttu-id="f6ade-105">Un <xref:System.Windows.Controls.Page> peut définir la largeur de la fenêtre hôte en définissant <xref:System.Windows.Controls.Page.WindowWidth%2A>.</span><span class="sxs-lookup"><span data-stu-id="f6ade-105">A <xref:System.Windows.Controls.Page> can set the width of its host window by setting <xref:System.Windows.Controls.Page.WindowWidth%2A>.</span></span> <span data-ttu-id="f6ade-106">Cette propriété permet <xref:System.Windows.Controls.Page> au d’avoir une connaissance explicite du type de fenêtre qui l’héberge.</span><span class="sxs-lookup"><span data-stu-id="f6ade-106">This property allows the <xref:System.Windows.Controls.Page> to not have explicit knowledge of the type of window that hosts it.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f6ade-107">Pour définir la largeur d’une fenêtre à <xref:System.Windows.Controls.Page.WindowWidth%2A>l’aide <xref:System.Windows.Controls.Page> de, un doit être l’enfant d’une fenêtre.</span><span class="sxs-lookup"><span data-stu-id="f6ade-107">To set the width of a window using <xref:System.Windows.Controls.Page.WindowWidth%2A>, a <xref:System.Windows.Controls.Page> must be the child of a window.</span></span>  
  
 [!code-xaml[HOWTONavigationSnippets#SetPageWindowWidthXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/SetWindowWidthPage.xaml#setpagewindowwidthxaml)]
