---
title: "Comment : définir les propriétés Height d'un élément"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- height properties [WPF]
- Panel control [WPF], height properties of elements
ms.assetid: 5ab9e781-dbb8-469a-a3c8-cf38ce312647
ms.openlocfilehash: 6500af3c637092820e538d79894d600d617953bf
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77124284"
---
# <a name="how-to-set-the-height-properties-of-an-element"></a>Comment : définir les propriétés Height d'un élément
## <a name="example"></a>Exemple  
 Cet exemple montre visuellement les différences de comportement de rendu parmi les quatre propriétés liées à la hauteur dans [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  
  
 La classe <xref:System.Windows.FrameworkElement> expose quatre propriétés qui décrivent les caractéristiques de la hauteur d’un élément. Ces quatre propriétés peuvent entrer en conflit et, le cas échéant, la valeur qui est prioritaire est déterminée comme suit : la valeur de <xref:System.Windows.FrameworkElement.MinHeight%2A> est prioritaire sur la valeur de <xref:System.Windows.FrameworkElement.MaxHeight%2A>, qui à son tour est prioritaire sur la valeur de <xref:System.Windows.FrameworkElement.Height%2A>. Une quatrième propriété, <xref:System.Windows.FrameworkElement.ActualHeight%2A>, est en lecture seule et signale la hauteur réelle telle qu’elle est déterminée par les interactions avec le processus de disposition.  
  
 Les exemples de [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] suivants dessinent un élément <xref:System.Windows.Shapes.Rectangle> (`rect1`) en tant qu’enfant de <xref:System.Windows.Controls.Canvas>. Vous pouvez modifier les propriétés de hauteur d’un <xref:System.Windows.Shapes.Rectangle> à l’aide d’une série d’éléments <xref:System.Windows.Controls.ListBox> qui représentent les valeurs de propriété de <xref:System.Windows.FrameworkElement.MinHeight%2A>, <xref:System.Windows.FrameworkElement.MaxHeight%2A>et <xref:System.Windows.FrameworkElement.Height%2A>. De cette manière, la priorité de chaque propriété est affichée visuellement.  
  
 [!code-xaml[HeightMinHeightMaxHeight#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HeightMinHeightMaxHeight/CSharp/Window1.xaml#1)]  
[!code-xaml[HeightMinHeightMaxHeight#2](~/samples/snippets/csharp/VS_Snippets_Wpf/HeightMinHeightMaxHeight/CSharp/Window1.xaml#2)]  
  
 Les exemples de code-behind suivants gèrent les événements déclenchés par l’événement <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged>. Chaque gestionnaire prend l’entrée de la <xref:System.Windows.Controls.ListBox>, analyse la valeur en tant que <xref:System.Double>et applique la valeur à la propriété relative à la hauteur spécifiée. Les valeurs de hauteur sont également converties en une chaîne et écrites dans différents éléments <xref:System.Windows.Controls.TextBlock> (la définition de ces éléments n’est pas affichée dans le XAML sélectionné).  
  
 [!code-csharp[HeightMinHeightMaxHeight#3](~/samples/snippets/csharp/VS_Snippets_Wpf/HeightMinHeightMaxHeight/CSharp/Window1.xaml.cs#3)]
 [!code-vb[HeightMinHeightMaxHeight#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HeightMinHeightMaxHeight/VisualBasic/Window1.xaml.vb#3)]  
  
 Pour obtenir l’exemple complet, consultez Propriétés de la [hauteur, exemple](https://github.com/microsoft/WPF-Samples/tree/master/Elements/HeightProperties).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.FrameworkElement>
- <xref:System.Windows.Controls.ListBox>
- <xref:System.Windows.FrameworkElement.ActualHeight%2A>
- <xref:System.Windows.FrameworkElement.MaxHeight%2A>
- <xref:System.Windows.FrameworkElement.MinHeight%2A>
- <xref:System.Windows.FrameworkElement.Height%2A>
- [Définir les propriétés Width d’un élément](how-to-set-the-width-properties-of-an-element.md)
- [Vue d’ensemble de Panel](panels-overview.md)
- [Exemple de propriétés Height](https://github.com/microsoft/WPF-Samples/tree/master/Elements/HeightProperties)
