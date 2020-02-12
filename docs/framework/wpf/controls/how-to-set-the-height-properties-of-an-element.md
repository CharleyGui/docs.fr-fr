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
# <a name="how-to-set-the-height-properties-of-an-element"></a><span data-ttu-id="65b20-102">Comment : définir les propriétés Height d'un élément</span><span class="sxs-lookup"><span data-stu-id="65b20-102">How to: Set the Height Properties of an Element</span></span>
## <a name="example"></a><span data-ttu-id="65b20-103">Exemple</span><span class="sxs-lookup"><span data-stu-id="65b20-103">Example</span></span>  
 <span data-ttu-id="65b20-104">Cet exemple montre visuellement les différences de comportement de rendu parmi les quatre propriétés liées à la hauteur dans [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="65b20-104">This example visually shows the differences in rendering behavior among the four height-related properties in [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].</span></span>  
  
 <span data-ttu-id="65b20-105">La classe <xref:System.Windows.FrameworkElement> expose quatre propriétés qui décrivent les caractéristiques de la hauteur d’un élément.</span><span class="sxs-lookup"><span data-stu-id="65b20-105">The <xref:System.Windows.FrameworkElement> class exposes four properties that describe the height characteristics of an element.</span></span> <span data-ttu-id="65b20-106">Ces quatre propriétés peuvent entrer en conflit et, le cas échéant, la valeur qui est prioritaire est déterminée comme suit : la valeur de <xref:System.Windows.FrameworkElement.MinHeight%2A> est prioritaire sur la valeur de <xref:System.Windows.FrameworkElement.MaxHeight%2A>, qui à son tour est prioritaire sur la valeur de <xref:System.Windows.FrameworkElement.Height%2A>.</span><span class="sxs-lookup"><span data-stu-id="65b20-106">These four properties can conflict, and when they do, the value that takes precedence is determined as follows: the <xref:System.Windows.FrameworkElement.MinHeight%2A> value takes precedence over the <xref:System.Windows.FrameworkElement.MaxHeight%2A> value, which in turn takes precedence over the <xref:System.Windows.FrameworkElement.Height%2A> value.</span></span> <span data-ttu-id="65b20-107">Une quatrième propriété, <xref:System.Windows.FrameworkElement.ActualHeight%2A>, est en lecture seule et signale la hauteur réelle telle qu’elle est déterminée par les interactions avec le processus de disposition.</span><span class="sxs-lookup"><span data-stu-id="65b20-107">A fourth property, <xref:System.Windows.FrameworkElement.ActualHeight%2A>, is read-only, and reports the actual height as determined by interactions with the layout process.</span></span>  
  
 <span data-ttu-id="65b20-108">Les exemples de [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] suivants dessinent un élément <xref:System.Windows.Shapes.Rectangle> (`rect1`) en tant qu’enfant de <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="65b20-108">The following [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] examples draw a <xref:System.Windows.Shapes.Rectangle> element (`rect1`) as a child of <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="65b20-109">Vous pouvez modifier les propriétés de hauteur d’un <xref:System.Windows.Shapes.Rectangle> à l’aide d’une série d’éléments <xref:System.Windows.Controls.ListBox> qui représentent les valeurs de propriété de <xref:System.Windows.FrameworkElement.MinHeight%2A>, <xref:System.Windows.FrameworkElement.MaxHeight%2A>et <xref:System.Windows.FrameworkElement.Height%2A>.</span><span class="sxs-lookup"><span data-stu-id="65b20-109">You can change the height properties of a <xref:System.Windows.Shapes.Rectangle> by using a series of <xref:System.Windows.Controls.ListBox> elements that represent the property values of <xref:System.Windows.FrameworkElement.MinHeight%2A>, <xref:System.Windows.FrameworkElement.MaxHeight%2A>, and <xref:System.Windows.FrameworkElement.Height%2A>.</span></span> <span data-ttu-id="65b20-110">De cette manière, la priorité de chaque propriété est affichée visuellement.</span><span class="sxs-lookup"><span data-stu-id="65b20-110">In this manner, the precedence of each property is visually displayed.</span></span>  
  
 [!code-xaml[HeightMinHeightMaxHeight#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HeightMinHeightMaxHeight/CSharp/Window1.xaml#1)]  
[!code-xaml[HeightMinHeightMaxHeight#2](~/samples/snippets/csharp/VS_Snippets_Wpf/HeightMinHeightMaxHeight/CSharp/Window1.xaml#2)]  
  
 <span data-ttu-id="65b20-111">Les exemples de code-behind suivants gèrent les événements déclenchés par l’événement <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged>.</span><span class="sxs-lookup"><span data-stu-id="65b20-111">The following code-behind examples handle the events that the <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> event raises.</span></span> <span data-ttu-id="65b20-112">Chaque gestionnaire prend l’entrée de la <xref:System.Windows.Controls.ListBox>, analyse la valeur en tant que <xref:System.Double>et applique la valeur à la propriété relative à la hauteur spécifiée.</span><span class="sxs-lookup"><span data-stu-id="65b20-112">Each handler takes the input from the <xref:System.Windows.Controls.ListBox>, parses the value as a <xref:System.Double>, and applies the value to the specified height-related property.</span></span> <span data-ttu-id="65b20-113">Les valeurs de hauteur sont également converties en une chaîne et écrites dans différents éléments <xref:System.Windows.Controls.TextBlock> (la définition de ces éléments n’est pas affichée dans le XAML sélectionné).</span><span class="sxs-lookup"><span data-stu-id="65b20-113">The height values are also converted to a string and written to various <xref:System.Windows.Controls.TextBlock> elements (definition of those elements is not shown in the selected XAML).</span></span>  
  
 [!code-csharp[HeightMinHeightMaxHeight#3](~/samples/snippets/csharp/VS_Snippets_Wpf/HeightMinHeightMaxHeight/CSharp/Window1.xaml.cs#3)]
 [!code-vb[HeightMinHeightMaxHeight#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HeightMinHeightMaxHeight/VisualBasic/Window1.xaml.vb#3)]  
  
 <span data-ttu-id="65b20-114">Pour obtenir l’exemple complet, consultez Propriétés de la [hauteur, exemple](https://github.com/microsoft/WPF-Samples/tree/master/Elements/HeightProperties).</span><span class="sxs-lookup"><span data-stu-id="65b20-114">For the complete sample, see [Height Properties Sample](https://github.com/microsoft/WPF-Samples/tree/master/Elements/HeightProperties).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65b20-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="65b20-115">See also</span></span>

- <xref:System.Windows.FrameworkElement>
- <xref:System.Windows.Controls.ListBox>
- <xref:System.Windows.FrameworkElement.ActualHeight%2A>
- <xref:System.Windows.FrameworkElement.MaxHeight%2A>
- <xref:System.Windows.FrameworkElement.MinHeight%2A>
- <xref:System.Windows.FrameworkElement.Height%2A>
- [<span data-ttu-id="65b20-116">Définir les propriétés Width d’un élément</span><span class="sxs-lookup"><span data-stu-id="65b20-116">Set the Width Properties of an Element</span></span>](how-to-set-the-width-properties-of-an-element.md)
- [<span data-ttu-id="65b20-117">Vue d’ensemble de Panel</span><span class="sxs-lookup"><span data-stu-id="65b20-117">Panels Overview</span></span>](panels-overview.md)
- [<span data-ttu-id="65b20-118">Exemple de propriétés Height</span><span class="sxs-lookup"><span data-stu-id="65b20-118">Height Properties Sample</span></span>](https://github.com/microsoft/WPF-Samples/tree/master/Elements/HeightProperties)
