---
title: "Comment : modifier l'embout à la fin d'une ligne ou d'un segment"
ms.date: 03/30/2017
helpviewer_keywords:
- Shape elements [WPF], ends
- Shape elements [WPF], caps
- graphics [WPF], Shape caps
ms.assetid: f4bf3416-b3d8-4568-b98e-3eda8f6dbf7a
ms.openlocfilehash: 5f755d7b4d1682755ea461121f91c0666d450ad1
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452777"
---
# <a name="how-to-modify-the-cap-at-the-end-of-a-line-or-segment"></a><span data-ttu-id="42501-102">Comment : modifier l'embout à la fin d'une ligne ou d'un segment</span><span class="sxs-lookup"><span data-stu-id="42501-102">How to: Modify the Cap at the End of a Line or Segment</span></span>
<span data-ttu-id="42501-103">Cet exemple montre comment modifier la forme au début ou à la fin d’un élément <xref:System.Windows.Shapes.Shape> ouvert.</span><span class="sxs-lookup"><span data-stu-id="42501-103">This example shows how to modify the shape at the start or end of an open <xref:System.Windows.Shapes.Shape> element.</span></span> <span data-ttu-id="42501-104">Pour modifier l’extrémité au début d’un <xref:System.Windows.Shapes.Shape>ouvert, utilisez sa propriété <xref:System.Windows.Shapes.Shape.StrokeStartLineCap%2A>.</span><span class="sxs-lookup"><span data-stu-id="42501-104">To change the cap at the beginning of an open <xref:System.Windows.Shapes.Shape>, use its <xref:System.Windows.Shapes.Shape.StrokeStartLineCap%2A> property.</span></span> <span data-ttu-id="42501-105">Pour modifier l’extrémité à la fin d’un <xref:System.Windows.Shapes.Shape>ouvert, utilisez sa propriété <xref:System.Windows.Shapes.Shape.StrokeEndLineCap%2A>.</span><span class="sxs-lookup"><span data-stu-id="42501-105">To change the cap at the end of an open <xref:System.Windows.Shapes.Shape>, use its <xref:System.Windows.Shapes.Shape.StrokeEndLineCap%2A> property.</span></span> <span data-ttu-id="42501-106">Pour afficher les embouts de ligne disponibles, consultez l’énumération <xref:System.Windows.Media.PenLineCap>.</span><span class="sxs-lookup"><span data-stu-id="42501-106">To view the available line caps, see the <xref:System.Windows.Media.PenLineCap> enumeration.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="42501-107">Cette propriété affecte uniquement une forme ouverte, telle qu’une <xref:System.Windows.Shapes.Line>, un <xref:System.Windows.Shapes.Polyline>ou un élément <xref:System.Windows.Shapes.Path> ouvert.</span><span class="sxs-lookup"><span data-stu-id="42501-107">This property only affects an open shape, such as a <xref:System.Windows.Shapes.Line>, a <xref:System.Windows.Shapes.Polyline>, or an open <xref:System.Windows.Shapes.Path> element.</span></span>  
  
 <span data-ttu-id="42501-108">L’exemple suivant dessine quatre <xref:System.Windows.Shapes.Polyline> éléments et utilise un ensemble de formes différent à la fin de chacune d’elles.</span><span class="sxs-lookup"><span data-stu-id="42501-108">The following example draws four <xref:System.Windows.Shapes.Polyline> elements and uses a different set of shapes on the ends of each.</span></span>  
  
## <a name="example"></a><span data-ttu-id="42501-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="42501-109">Example</span></span>  
 [!code-xaml[drawingwithshapeelements#ShapeLineCaps1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/linecapsandjoinsexample.xaml#shapelinecaps1)]  
  
 <span data-ttu-id="42501-110">Cet exemple fait partie d’un exemple plus grand ; pour obtenir l’exemple complet, consultez [exemple d’éléments de forme](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).</span><span class="sxs-lookup"><span data-stu-id="42501-110">This example is part of a larger sample; for the complete sample, see [Shape Elements Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42501-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="42501-111">See also</span></span>

- <xref:System.Windows.Shapes.Polyline>
- <xref:System.Windows.Media.PenLineCap>
