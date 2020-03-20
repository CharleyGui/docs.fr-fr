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
# <a name="how-to-set-the-tile-size-for-a-tilebrush"></a>Comment : définir la taille de la mosaïque pour un TileBrush

Cet exemple montre comment définir la <xref:System.Windows.Media.TileBrush>taille de la tuile pour un . Par défaut, <xref:System.Windows.Media.TileBrush> un produit une seule tuile qui remplit complètement la zone que vous peignez. Vous pouvez remplacer ce comportement <xref:System.Windows.Media.TileBrush.Viewport%2A> <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> en définissant le et les propriétés.

La <xref:System.Windows.Media.TileBrush.Viewport%2A> propriété spécifie la <xref:System.Windows.Media.TileBrush>taille de la tuile pour un . Par défaut, la <xref:System.Windows.Media.TileBrush.Viewport%2A> valeur de la propriété est relative à la taille de la zone peinte. Pour que <xref:System.Windows.Media.TileBrush.Viewport%2A> la propriété spécifie <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> une <xref:System.Windows.Media.BrushMappingMode.Absolute>taille absolue de tuile, définissez la propriété à .

## <a name="example"></a> Exemple

L’exemple suivant <xref:System.Windows.Media.ImageBrush>utilise un <xref:System.Windows.Media.TileBrush>, un type de , pour peindre un rectangle avec des tuiles. L’exemple donne à chaque tuile à 50 pour cent par 50 pour cent de la zone de sortie (le rectangle). Le rectangle est donc peint avec quatre projections de l’image.

L’illustration suivante montre la sortie que l’exemple produit :

![Un rectangle avec quatre cerises démontrant le carrelage avec un pinceau d’image.](./media/how-to-set-the-tile-size-for-a-tilebrush/rectangle-tile-image-brush.png)

[!code-csharp[UsingImageBrush_snip#RelativeTileSizeExample](~/samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/TileSizeExample.cs#relativetilesizeexample)]

L’exemple suivant <xref:System.Windows.Media.ImageBrush>crée <xref:System.Windows.Media.TileBrush.Viewport%2A> un `0,0,25,25` , <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> <xref:System.Windows.Media.BrushMappingMode.Absolute>définit son à et son à , et l’utilise pour peindre un autre rectangle. Le pinceau produit ainsi des mosaïques d’une largeur de 25 pixels et d’une hauteur de 25 pixels.

L’illustration suivante montre la sortie que l’exemple produit :

![Un rectangle avec quarante-huit cerises démontrant un pinceau carrelé avec un Viewport.](./media/how-to-set-the-tile-size-for-a-tilebrush/25-x-25-viewport-tilebrush.png)

[!code-csharp[UsingImageBrush_snip#AbsoluteTileSizeExample](~/samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/TileSizeExample.cs#absolutetilesizeexample)]

Les exemples précédents font partie d’un exemple plus complet. Pour l’échantillon complet, voir [ImageBrush Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ImageBrush).

Bien que cet <xref:System.Windows.Media.ImageBrush> exemple <xref:System.Windows.Media.TileBrush.Viewport%2A> utilise <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> la classe, le <xref:System.Windows.Media.TileBrush> et les propriétés se comportent de façon identique pour les autres objets, c’est-à-dire, pour <xref:System.Windows.Media.DrawingBrush> et <xref:System.Windows.Media.VisualBrush>. Pour plus <xref:System.Windows.Media.ImageBrush> d’informations <xref:System.Windows.Media.TileBrush> sur et les autres objets, voir [Painting with Images, Drawings, and Visuals](painting-with-images-drawings-and-visuals.md).

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Media.TileBrush>
- [Peinture avec des images, des dessins et des objets visuels](painting-with-images-drawings-and-visuals.md)
- [Créer différents modèles de mosaïque avec un TileBrush](how-to-create-different-tile-patterns-with-a-tilebrush.md)
