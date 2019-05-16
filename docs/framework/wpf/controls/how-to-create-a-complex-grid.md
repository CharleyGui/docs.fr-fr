---
title: Comment créer une grille complexe
description: Un exemple sur l’utilisation d’un contrôle de grille pour créer une disposition qui ressemble à un calendrier mensuel.
ms.date: 03/30/2017
helpviewer_keywords:
- calendar [WPF], creating
- monthly calendar [WPF], creating
- Grid control [WPF], creating [WPF], complex grid
ms.assetid: 4ce3040a-a156-4364-9596-98ca1eca5550
ms.openlocfilehash: ab5490d608b21fe8b29a078dc1f0147f038c27a3
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65645671"
---
# <a name="how-to-create-a-complex-grid"></a><span data-ttu-id="5b706-103">Comment créer une grille complexe</span><span class="sxs-lookup"><span data-stu-id="5b706-103">How to create a complex Grid</span></span>

<span data-ttu-id="5b706-104">Cet exemple montre comment utiliser un <xref:System.Windows.Controls.Grid> contrôle pour créer une disposition qui ressemble à un calendrier mensuel.</span><span class="sxs-lookup"><span data-stu-id="5b706-104">This example shows how to use a <xref:System.Windows.Controls.Grid> control to create a layout that looks like a monthly calendar.</span></span>

## <a name="example"></a><span data-ttu-id="5b706-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="5b706-105">Example</span></span>

<span data-ttu-id="5b706-106">L’exemple suivant définit huit lignes et huit colonnes à l’aide de la <xref:System.Windows.Controls.RowDefinition> et <xref:System.Windows.Controls.ColumnDefinition> classes.</span><span class="sxs-lookup"><span data-stu-id="5b706-106">The following example defines eight rows and eight columns by using the <xref:System.Windows.Controls.RowDefinition> and <xref:System.Windows.Controls.ColumnDefinition> classes.</span></span> <span data-ttu-id="5b706-107">Il utilise le <xref:System.Windows.Controls.Grid.ColumnSpan%2A?displayProperty=nameWithType> et <xref:System.Windows.Controls.Grid.RowSpan%2A?displayProperty=nameWithType> avec des propriétés, jointes <xref:System.Windows.Shapes.Rectangle> éléments qui remplissent les arrière-plans des différentes colonnes et lignes.</span><span class="sxs-lookup"><span data-stu-id="5b706-107">It uses the <xref:System.Windows.Controls.Grid.ColumnSpan%2A?displayProperty=nameWithType> and <xref:System.Windows.Controls.Grid.RowSpan%2A?displayProperty=nameWithType> attached properties, together with <xref:System.Windows.Shapes.Rectangle> elements, which fill the backgrounds of various columns and rows.</span></span> <span data-ttu-id="5b706-108">Cette conception est possible car plusieurs éléments peuvent exister dans chaque cellule dans un <xref:System.Windows.Controls.Grid>, une différence de principe entre <xref:System.Windows.Controls.Grid> et <xref:System.Windows.Documents.Table>.</span><span class="sxs-lookup"><span data-stu-id="5b706-108">This design is possible because more than one element can exist in each cell in a <xref:System.Windows.Controls.Grid>, a principle difference between <xref:System.Windows.Controls.Grid> and <xref:System.Windows.Documents.Table>.</span></span>

<span data-ttu-id="5b706-109">L’exemple utilise des dégradés verticaux pour <xref:System.Windows.Shapes.Shape.Fill%2A> les colonnes et les lignes afin d’améliorer la présentation visuelle et la lisibilité du calendrier.</span><span class="sxs-lookup"><span data-stu-id="5b706-109">The example uses vertical gradients to <xref:System.Windows.Shapes.Shape.Fill%2A> the columns and rows to improve the visual presentation and readability of the calendar.</span></span> <span data-ttu-id="5b706-110">Un style <xref:System.Windows.Controls.TextBlock> les éléments représentent les dates et les jours de la semaine.</span><span class="sxs-lookup"><span data-stu-id="5b706-110">Styled <xref:System.Windows.Controls.TextBlock> elements represent the dates and days of the week.</span></span> <span data-ttu-id="5b706-111"><xref:System.Windows.Controls.TextBlock> éléments sont positionnés dans leurs cellules à l’aide de la <xref:System.Windows.FrameworkElement.Margin%2A> propriété et les propriétés d’alignement qui sont définies dans le style de l’application.</span><span class="sxs-lookup"><span data-stu-id="5b706-111"><xref:System.Windows.Controls.TextBlock> elements are absolutely positioned within their cells by using the <xref:System.Windows.FrameworkElement.Margin%2A> property and alignment properties that are defined within the style for the application.</span></span>

[!code-xaml[GridComplex#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GridComplex/CS/default.xaml#1)]

<span data-ttu-id="5b706-112">L’illustration suivante montre le contrôle résultant, un calendrier personnalisable :</span><span class="sxs-lookup"><span data-stu-id="5b706-112">The following image shows the resulting control, a customizable calendar:</span></span>

![Capture d’écran du contrôle résultant](././media/how-to-create-a-complex-grid/wpf-manual-calendar.png)

## <a name="see-also"></a><span data-ttu-id="5b706-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5b706-114">See also</span></span>

- <xref:System.Windows.Controls.Grid?displayProperty=nameWithType>
- <xref:System.Windows.Documents.TableCell?displayProperty=nameWithType>
- [<span data-ttu-id="5b706-115">Vue d’ensemble de la peinture avec des couleurs unies ou des dégradés</span><span class="sxs-lookup"><span data-stu-id="5b706-115">Painting with Solid Colors and Gradients Overview</span></span>](../graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)
- [<span data-ttu-id="5b706-116">Vue d’ensemble de Panel</span><span class="sxs-lookup"><span data-stu-id="5b706-116">Panels Overview</span></span>](panels-overview.md)
- [<span data-ttu-id="5b706-117">Vue d’ensemble de Table</span><span class="sxs-lookup"><span data-stu-id="5b706-117">Table Overview</span></span>](../advanced/table-overview.md)
