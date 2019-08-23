---
title: 'Procédure : Modifier l’extrémité de fin d’une ligne ou d’un segment'
ms.date: 03/30/2017
helpviewer_keywords:
- Shape elements [WPF], ends
- Shape elements [WPF], caps
- graphics [WPF], Shape caps
ms.assetid: f4bf3416-b3d8-4568-b98e-3eda8f6dbf7a
ms.openlocfilehash: 53487417636dae8d855fe70b7b9255351a2dfb1e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916131"
---
# <a name="how-to-modify-the-cap-at-the-end-of-a-line-or-segment"></a><span data-ttu-id="9a37f-102">Procédure : Modifier l’extrémité de fin d’une ligne ou d’un segment</span><span class="sxs-lookup"><span data-stu-id="9a37f-102">How to: Modify the Cap at the End of a Line or Segment</span></span>
<span data-ttu-id="9a37f-103">Cet exemple montre comment modifier la forme au début ou à la fin d’un élément <xref:System.Windows.Shapes.Shape> ouvert.</span><span class="sxs-lookup"><span data-stu-id="9a37f-103">This example shows how to modify the shape at the start or end of an open <xref:System.Windows.Shapes.Shape> element.</span></span> <span data-ttu-id="9a37f-104">Pour modifier l’extrémité au début d’une ouverture <xref:System.Windows.Shapes.Shape>, utilisez sa <xref:System.Windows.Shapes.Shape.StrokeStartLineCap%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="9a37f-104">To change the cap at the beginning of an open <xref:System.Windows.Shapes.Shape>, use its <xref:System.Windows.Shapes.Shape.StrokeStartLineCap%2A> property.</span></span> <span data-ttu-id="9a37f-105">Pour modifier l’extrémité à la fin d’une ouverture <xref:System.Windows.Shapes.Shape>, utilisez sa <xref:System.Windows.Shapes.Shape.StrokeEndLineCap%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="9a37f-105">To change the cap at the end of an open <xref:System.Windows.Shapes.Shape>, use its <xref:System.Windows.Shapes.Shape.StrokeEndLineCap%2A> property.</span></span> <span data-ttu-id="9a37f-106">Pour afficher les embouts de ligne disponibles <xref:System.Windows.Media.PenLineCap> , consultez l’énumération.</span><span class="sxs-lookup"><span data-stu-id="9a37f-106">To view the available line caps, see the <xref:System.Windows.Media.PenLineCap> enumeration.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9a37f-107">Cette propriété affecte uniquement une forme ouverte, telle qu’un <xref:System.Windows.Shapes.Line>, un <xref:System.Windows.Shapes.Polyline>ou un élément Open <xref:System.Windows.Shapes.Path> .</span><span class="sxs-lookup"><span data-stu-id="9a37f-107">This property only affects an open shape, such as a <xref:System.Windows.Shapes.Line>, a <xref:System.Windows.Shapes.Polyline>, or an open <xref:System.Windows.Shapes.Path> element.</span></span>  
  
 <span data-ttu-id="9a37f-108">L’exemple suivant dessine <xref:System.Windows.Shapes.Polyline> quatre éléments et utilise un ensemble de formes différent à la fin de chaque.</span><span class="sxs-lookup"><span data-stu-id="9a37f-108">The following example draws four <xref:System.Windows.Shapes.Polyline> elements and uses a different set of shapes on the ends of each.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9a37f-109">Exemples</span><span class="sxs-lookup"><span data-stu-id="9a37f-109">Example</span></span>  
 [!code-xaml[drawingwithshapeelements#ShapeLineCaps1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/linecapsandjoinsexample.xaml#shapelinecaps1)]  
  
 <span data-ttu-id="9a37f-110">Cet exemple fait partie d’un exemple plus grand; pour obtenir l’exemple complet, consultez [exemple d’éléments de forme](https://go.microsoft.com/fwlink/?LinkID=160037).</span><span class="sxs-lookup"><span data-stu-id="9a37f-110">This example is part of a larger sample; for the complete sample, see [Shape Elements Sample](https://go.microsoft.com/fwlink/?LinkID=160037).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a37f-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9a37f-111">See also</span></span>

- <xref:System.Windows.Shapes.Polyline>
- <xref:System.Windows.Media.PenLineCap>
