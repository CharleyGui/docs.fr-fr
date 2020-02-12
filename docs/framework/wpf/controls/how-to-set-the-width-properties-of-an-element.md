---
title: "Comment : définir les propriétés Width d'un élément"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- width properties [WPF]
- Panel control [WPF], width properties of elements
ms.assetid: 6ee04a9d-63f0-4f5b-a406-0a8cd4c35729
ms.openlocfilehash: 682929625612114d042e4619d8388617988b3c48
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77124271"
---
# <a name="how-to-set-the-width-properties-of-an-element"></a>Comment : définir les propriétés Width d'un élément
## <a name="example"></a>Exemple  
 Cet exemple montre visuellement les différences de comportement de rendu parmi les quatre propriétés relatives à la largeur dans [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  
  
 La classe <xref:System.Windows.FrameworkElement> expose quatre propriétés qui décrivent les caractéristiques de largeur d’un élément. Ces quatre propriétés peuvent entrer en conflit et, le cas échéant, la valeur qui est prioritaire est déterminée comme suit : la valeur de <xref:System.Windows.FrameworkElement.MinWidth%2A> est prioritaire sur la valeur de <xref:System.Windows.FrameworkElement.MaxWidth%2A>, qui à son tour est prioritaire sur la valeur de <xref:System.Windows.FrameworkElement.Width%2A>. Une quatrième propriété, <xref:System.Windows.FrameworkElement.ActualWidth%2A>, est en lecture seule et signale la largeur réelle telle qu’elle est déterminée par les interactions avec le processus de disposition.  
  
 Les exemples de [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] suivants dessinent un élément <xref:System.Windows.Shapes.Rectangle> (`rect1`) en tant qu’enfant de <xref:System.Windows.Controls.Canvas>. Vous pouvez modifier les propriétés de largeur d’un <xref:System.Windows.Shapes.Rectangle> à l’aide d’une série d’éléments <xref:System.Windows.Controls.ListBox> qui représentent les valeurs de propriété de <xref:System.Windows.FrameworkElement.MinWidth%2A>, <xref:System.Windows.FrameworkElement.MaxWidth%2A>et <xref:System.Windows.FrameworkElement.Width%2A>. De cette manière, la priorité de chaque propriété est affichée visuellement.  
  
 [!code-xaml[WidthMinWidthMaxWidth#1](~/samples/snippets/csharp/VS_Snippets_Wpf/WidthMinWidthMaxWidth/CSharp/Window1.xaml#1)]  
[!code-xaml[WidthMinWidthMaxWidth#2](~/samples/snippets/csharp/VS_Snippets_Wpf/WidthMinWidthMaxWidth/CSharp/Window1.xaml#2)]  
  
 Les exemples de code-behind suivants gèrent les événements déclenchés par l’événement <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged>. Chaque méthode personnalisée prend l’entrée de la <xref:System.Windows.Controls.ListBox>, analyse la valeur en tant que <xref:System.Double>et applique la valeur à la propriété relative à la largeur spécifiée. Les valeurs de largeur sont également converties en une chaîne et écrites dans différents éléments <xref:System.Windows.Controls.TextBlock> (la définition de ces éléments n’est pas affichée dans le XAML sélectionné).  
  
 [!code-csharp[WidthMinWidthMaxWidth#3](~/samples/snippets/csharp/VS_Snippets_Wpf/WidthMinWidthMaxWidth/CSharp/Window1.xaml.cs#3)]
 [!code-vb[WidthMinWidthMaxWidth#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WidthMinWidthMaxWidth/VisualBasic/Window1.xaml.vb#3)]  
  
 Pour obtenir l’exemple complet, consultez [exemple de comparaison des propriétés de largeur](https://github.com/Microsoft/WPF-Samples/tree/master/Elements/WidthProperties).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Controls.ListBox>
- <xref:System.Windows.FrameworkElement>
- <xref:System.Windows.FrameworkElement.ActualWidth%2A>
- <xref:System.Windows.FrameworkElement.MaxWidth%2A>
- <xref:System.Windows.FrameworkElement.MinWidth%2A>
- <xref:System.Windows.FrameworkElement.Width%2A>
- [Vue d’ensemble de Panel](panels-overview.md)
- [Définir les propriétés Height d’un élément](how-to-set-the-height-properties-of-an-element.md)
- [Exemple de comparaison des propriétés de largeur](https://github.com/Microsoft/WPF-Samples/tree/master/Elements/WidthProperties)
