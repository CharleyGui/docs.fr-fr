---
title: 'Comment : définir la taille de la mosaïque pour un TileBrush'
ms.date: 03/30/2017
helpviewer_keywords:
- TileBrush [WPF], size of tile properties
- Viewport property of TileBrush [WPF]
ms.assetid: 04f41090-1b46-4e36-832f-d27d28708b8c
ms.openlocfilehash: af7bab59a292549b29dad9b6a7417f22b1b84e48
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186837"
---
# <a name="how-to-set-the-tile-size-for-a-tilebrush"></a><span data-ttu-id="33fd9-102">Comment : définir la taille de la mosaïque pour un TileBrush</span><span class="sxs-lookup"><span data-stu-id="33fd9-102">How to: Set the Tile Size for a TileBrush</span></span>

<span data-ttu-id="33fd9-103">Cet exemple montre comment définir la <xref:System.Windows.Media.TileBrush>taille de la tuile pour un .</span><span class="sxs-lookup"><span data-stu-id="33fd9-103">This example shows how to set the tile size for a <xref:System.Windows.Media.TileBrush>.</span></span> <span data-ttu-id="33fd9-104">Par défaut, <xref:System.Windows.Media.TileBrush> un produit une seule tuile qui remplit complètement la zone que vous peignez.</span><span class="sxs-lookup"><span data-stu-id="33fd9-104">By default, a <xref:System.Windows.Media.TileBrush> produces a single tile that completely fills the area that you are painting.</span></span> <span data-ttu-id="33fd9-105">Vous pouvez remplacer ce comportement <xref:System.Windows.Media.TileBrush.Viewport%2A> <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> en définissant le et les propriétés.</span><span class="sxs-lookup"><span data-stu-id="33fd9-105">You can override this behavior by setting the <xref:System.Windows.Media.TileBrush.Viewport%2A> and <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> properties.</span></span>

<span data-ttu-id="33fd9-106">La <xref:System.Windows.Media.TileBrush.Viewport%2A> propriété spécifie la <xref:System.Windows.Media.TileBrush>taille de la tuile pour un .</span><span class="sxs-lookup"><span data-stu-id="33fd9-106">The <xref:System.Windows.Media.TileBrush.Viewport%2A> property specifies the tile size for a <xref:System.Windows.Media.TileBrush>.</span></span> <span data-ttu-id="33fd9-107">Par défaut, la <xref:System.Windows.Media.TileBrush.Viewport%2A> valeur de la propriété est relative à la taille de la zone peinte.</span><span class="sxs-lookup"><span data-stu-id="33fd9-107">By default, the value of the <xref:System.Windows.Media.TileBrush.Viewport%2A> property is relative to the size of the area being painted.</span></span> <span data-ttu-id="33fd9-108">Pour que <xref:System.Windows.Media.TileBrush.Viewport%2A> la propriété spécifie <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> une <xref:System.Windows.Media.BrushMappingMode.Absolute>taille absolue de tuile, définissez la propriété à .</span><span class="sxs-lookup"><span data-stu-id="33fd9-108">To make the <xref:System.Windows.Media.TileBrush.Viewport%2A> property specify an absolute tile size, set the <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> property to <xref:System.Windows.Media.BrushMappingMode.Absolute>.</span></span>

## <a name="example"></a><span data-ttu-id="33fd9-109"> Exemple</span><span class="sxs-lookup"><span data-stu-id="33fd9-109">Example</span></span>

<span data-ttu-id="33fd9-110">L’exemple suivant <xref:System.Windows.Media.ImageBrush>utilise un <xref:System.Windows.Media.TileBrush>, un type de , pour peindre un rectangle avec des tuiles.</span><span class="sxs-lookup"><span data-stu-id="33fd9-110">The following example uses an <xref:System.Windows.Media.ImageBrush>, a type of <xref:System.Windows.Media.TileBrush>, to paint a rectangle with tiles.</span></span> <span data-ttu-id="33fd9-111">L’exemple donne à chaque tuile à 50 pour cent par 50 pour cent de la zone de sortie (le rectangle).</span><span class="sxs-lookup"><span data-stu-id="33fd9-111">The example sets each tile to 50 percent by 50 percent of the output area (the rectangle).</span></span> <span data-ttu-id="33fd9-112">Le rectangle est donc peint avec quatre projections de l’image.</span><span class="sxs-lookup"><span data-stu-id="33fd9-112">As a result, the rectangle is painted with four projections of the image.</span></span>

<span data-ttu-id="33fd9-113">L’illustration suivante montre la sortie que l’exemple produit :</span><span class="sxs-lookup"><span data-stu-id="33fd9-113">The following illustration shows the output that the example produces:</span></span>

![Un rectangle avec quatre cerises démontrant le carrelage avec un pinceau d’image.](./media/how-to-set-the-tile-size-for-a-tilebrush/rectangle-tile-image-brush.png)

[!code-csharp[UsingImageBrush_snip#RelativeTileSizeExample](~/samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/TileSizeExample.cs#relativetilesizeexample)]

<span data-ttu-id="33fd9-115">L’exemple suivant <xref:System.Windows.Media.ImageBrush>crée <xref:System.Windows.Media.TileBrush.Viewport%2A> un `0,0,25,25` , <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> <xref:System.Windows.Media.BrushMappingMode.Absolute>définit son à et son à , et l’utilise pour peindre un autre rectangle.</span><span class="sxs-lookup"><span data-stu-id="33fd9-115">The next example creates an <xref:System.Windows.Media.ImageBrush>, sets its <xref:System.Windows.Media.TileBrush.Viewport%2A> to `0,0,25,25` and its <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> to <xref:System.Windows.Media.BrushMappingMode.Absolute>, and uses it to paint another rectangle.</span></span> <span data-ttu-id="33fd9-116">Le pinceau produit ainsi des mosaïques d’une largeur de 25 pixels et d’une hauteur de 25 pixels.</span><span class="sxs-lookup"><span data-stu-id="33fd9-116">As a result, the brush produces tiles that have a width of 25  pixels and a height of 25 pixels .</span></span>

<span data-ttu-id="33fd9-117">L’illustration suivante montre la sortie que l’exemple produit :</span><span class="sxs-lookup"><span data-stu-id="33fd9-117">The following illustration shows the output that the example produces:</span></span>

![Un rectangle avec quarante-huit cerises démontrant un pinceau carrelé avec un Viewport.](./media/how-to-set-the-tile-size-for-a-tilebrush/25-x-25-viewport-tilebrush.png)

[!code-csharp[UsingImageBrush_snip#AbsoluteTileSizeExample](~/samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/TileSizeExample.cs#absolutetilesizeexample)]

<span data-ttu-id="33fd9-119">Les exemples précédents font partie d’un exemple plus complet.</span><span class="sxs-lookup"><span data-stu-id="33fd9-119">The preceding examples are part of a larger sample.</span></span> <span data-ttu-id="33fd9-120">Pour l’échantillon complet, voir [ImageBrush Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ImageBrush).</span><span class="sxs-lookup"><span data-stu-id="33fd9-120">For the complete sample, see [ImageBrush Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ImageBrush).</span></span>

<span data-ttu-id="33fd9-121">Bien que cet <xref:System.Windows.Media.ImageBrush> exemple <xref:System.Windows.Media.TileBrush.Viewport%2A> utilise <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> la classe, le <xref:System.Windows.Media.TileBrush> et les propriétés se comportent de façon identique pour les autres objets, c’est-à-dire, pour <xref:System.Windows.Media.DrawingBrush> et <xref:System.Windows.Media.VisualBrush>.</span><span class="sxs-lookup"><span data-stu-id="33fd9-121">Although this example uses the <xref:System.Windows.Media.ImageBrush> class, the <xref:System.Windows.Media.TileBrush.Viewport%2A> and <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> properties behave identically for the other <xref:System.Windows.Media.TileBrush> objects, that is, for <xref:System.Windows.Media.DrawingBrush> and <xref:System.Windows.Media.VisualBrush>.</span></span> <span data-ttu-id="33fd9-122">Pour plus <xref:System.Windows.Media.ImageBrush> d’informations <xref:System.Windows.Media.TileBrush> sur et les autres objets, voir [Painting with Images, Drawings, and Visuals](painting-with-images-drawings-and-visuals.md).</span><span class="sxs-lookup"><span data-stu-id="33fd9-122">For more information about <xref:System.Windows.Media.ImageBrush> and the other <xref:System.Windows.Media.TileBrush> objects, see [Painting with Images, Drawings, and Visuals](painting-with-images-drawings-and-visuals.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="33fd9-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="33fd9-123">See also</span></span>

- <xref:System.Windows.Media.TileBrush>
- [<span data-ttu-id="33fd9-124">Peinture avec des images, des dessins et des objets visuels</span><span class="sxs-lookup"><span data-stu-id="33fd9-124">Painting with Images, Drawings, and Visuals</span></span>](painting-with-images-drawings-and-visuals.md)
- [<span data-ttu-id="33fd9-125">Créer différents modèles de mosaïque avec un TileBrush</span><span class="sxs-lookup"><span data-stu-id="33fd9-125">Create Different Tile Patterns with a TileBrush</span></span>](how-to-create-different-tile-patterns-with-a-tilebrush.md)
