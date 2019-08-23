---
title: 'Procédure : Définir la hauteur d’une fenêtre à partir d’une page'
ms.date: 03/30/2017
helpviewer_keywords:
- windows [WPF], setting height from a page
- pages [WPF], setting window height from
- height of window [WPF], setting from a page
ms.assetid: 4e4488ff-ab5c-4ee9-81a4-e1addb55c5cc
ms.openlocfilehash: c1041af88241011b51c96d7b61423344a32b25ca
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940802"
---
# <a name="how-to-set-the-height-of-a-window-from-a-page"></a>Procédure : Définir la hauteur d’une fenêtre à partir d’une page
Cet exemple montre comment définir la hauteur de la fenêtre à partir d’un <xref:System.Windows.Controls.Page>.  
  
## <a name="example"></a>Exemple  
 Un <xref:System.Windows.Controls.Page> peut définir la hauteur de sa fenêtre hôte en définissant <xref:System.Windows.Controls.Page.WindowHeight%2A>. Cette propriété permet <xref:System.Windows.Controls.Page> au d’avoir une connaissance explicite du type de fenêtre qui l’héberge.  
  
> [!NOTE]
> Pour définir la hauteur d’une fenêtre à <xref:System.Windows.Controls.Page.WindowHeight%2A>l’aide <xref:System.Windows.Controls.Page> de, un doit être l’enfant d’une fenêtre.  
  
 [!code-xaml[HOWTONavigationSnippets#SetPageWindowHeightXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/SetWindowHeightPage.xaml#setpagewindowheightxaml)]
