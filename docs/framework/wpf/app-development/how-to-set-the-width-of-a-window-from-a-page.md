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
# <a name="how-to-set-the-width-of-a-window-from-a-page"></a>Procédure : Définir la largeur d’une fenêtre à partir d’une page
Cet exemple montre comment définir la largeur de la fenêtre à partir d’un <xref:System.Windows.Controls.Page>.  
  
## <a name="example"></a>Exemple  
 Un <xref:System.Windows.Controls.Page> peut définir la largeur de la fenêtre hôte en définissant <xref:System.Windows.Controls.Page.WindowWidth%2A>. Cette propriété permet <xref:System.Windows.Controls.Page> au d’avoir une connaissance explicite du type de fenêtre qui l’héberge.  
  
> [!NOTE]
> Pour définir la largeur d’une fenêtre à <xref:System.Windows.Controls.Page.WindowWidth%2A>l’aide <xref:System.Windows.Controls.Page> de, un doit être l’enfant d’une fenêtre.  
  
 [!code-xaml[HOWTONavigationSnippets#SetPageWindowWidthXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/SetWindowWidthPage.xaml#setpagewindowwidthxaml)]
