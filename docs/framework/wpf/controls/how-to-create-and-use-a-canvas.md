---
title: 'Procédure : Créer et utiliser un canevas'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], Canvas
- Canvas control [WPF], creating
- Canvas control [WPF], using
ms.assetid: 420b9487-9a15-477c-9489-a22a4dec7779
ms.openlocfilehash: edef660b2da2f09e0a6edbc0a87f0d1f26eb03da
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964222"
---
# <a name="how-to-create-and-use-a-canvas"></a><span data-ttu-id="2ccc9-102">Procédure : Créer et utiliser un canevas</span><span class="sxs-lookup"><span data-stu-id="2ccc9-102">How to: Create and Use a Canvas</span></span>
<span data-ttu-id="2ccc9-103">Cet exemple montre comment créer et utiliser une instance de <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="2ccc9-103">This example shows how to create and use an instance of <xref:System.Windows.Controls.Canvas>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2ccc9-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="2ccc9-104">Example</span></span>  
 <span data-ttu-id="2ccc9-105">L’exemple suivant positionne explicitement deux <xref:System.Windows.Controls.TextBlock> éléments à <xref:System.Windows.Controls.Canvas.SetTop%2A> l’aide des <xref:System.Windows.Controls.Canvas.SetLeft%2A> méthodes et <xref:System.Windows.Controls.Canvas>de.</span><span class="sxs-lookup"><span data-stu-id="2ccc9-105">The following example explicitly positions two <xref:System.Windows.Controls.TextBlock> elements by using the <xref:System.Windows.Controls.Canvas.SetTop%2A> and <xref:System.Windows.Controls.Canvas.SetLeft%2A> methods of <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="2ccc9-106">L’exemple assigne également une <xref:System.Windows.Controls.Control.Background%2A> couleur de `LightSteelBlue` à <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="2ccc9-106">The example also assigns a <xref:System.Windows.Controls.Control.Background%2A> color of `LightSteelBlue` to the <xref:System.Windows.Controls.Canvas>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2ccc9-107">Lorsque vous utilisez [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] pour positionner <xref:System.Windows.Controls.TextBlock> des éléments, utilisez <xref:System.Windows.Controls.Canvas.Top%2A> les <xref:System.Windows.Controls.Canvas.Left%2A> propriétés et.</span><span class="sxs-lookup"><span data-stu-id="2ccc9-107">When you use [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] to position <xref:System.Windows.Controls.TextBlock> elements, use the <xref:System.Windows.Controls.Canvas.Top%2A> and <xref:System.Windows.Controls.Canvas.Left%2A> properties.</span></span>  
  
 [!code-csharp[CanvasCode#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CanvasCode/CSharp/Canvas_Code.cs#1)]
 [!code-vb[CanvasCode#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CanvasCode/VisualBasic/canvas_vb.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="2ccc9-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2ccc9-108">See also</span></span>

- <xref:System.Windows.Controls.Canvas>
- <xref:System.Windows.Controls.TextBlock>
- <xref:System.Windows.Controls.Canvas.SetTop%2A>
- <xref:System.Windows.Controls.Canvas.SetLeft%2A>
- <xref:System.Windows.Controls.Canvas.Top%2A>
- <xref:System.Windows.Controls.Canvas.Left%2A>
- [<span data-ttu-id="2ccc9-109">Vue d’ensemble de Panel</span><span class="sxs-lookup"><span data-stu-id="2ccc9-109">Panels Overview</span></span>](panels-overview.md)
- [<span data-ttu-id="2ccc9-110">Rubriques de guide pratique</span><span class="sxs-lookup"><span data-stu-id="2ccc9-110">How-to Topics</span></span>](canvas-how-to-topics.md)
