---
title: 'Comment : peindre une zone avec une image'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- images [WPF], painting with
- painting [WPF], with images
- brushes [WPF], painting with images
ms.assetid: 3432c533-1fc7-492d-94ee-0b13d60125ae
ms.openlocfilehash: 92969778c04c6ac634a2964c402d6c3439b96b49
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186051"
---
# <a name="how-to-paint-an-area-with-an-image"></a>Comment : peindre une zone avec une image
Cet exemple montre comment <xref:System.Windows.Media.ImageBrush> utiliser la classe pour peindre une zone avec une image. Une <xref:System.Windows.Media.ImageBrush> image unique, qui est <xref:System.Windows.Media.ImageBrush.ImageSource%2A> spécifiée par sa propriété.  
  
## <a name="example"></a> Exemple  
 L’exemple suivant <xref:System.Windows.Controls.Control.Background%2A> peint le bouton <xref:System.Windows.Media.ImageBrush>en utilisant un .  
  
 [!code-csharp[UsingImageBrush_snip#ImageBrushExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/PaintingWithImagesExample.cs#imagebrushexamplewholepage)]  
  
 Par défaut, <xref:System.Windows.Media.ImageBrush> un étend son image pour remplir complètement la zone que vous peignez. Dans l’exemple précédent, l’image est étirée pour remplir le bouton, ce qui peut éventuellement déformer l’image. Vous pouvez contrôler ce <xref:System.Windows.Media.TileBrush.Stretch%2A> comportement <xref:System.Windows.Media.TileBrush> en <xref:System.Windows.Media.Stretch.Uniform> <xref:System.Windows.Media.Stretch.UniformToFill>définissant la propriété de ou , ce qui provoque le pinceau pour préserver le rapport d’aspect de l’image.  
  
 Si vous <xref:System.Windows.Media.TileBrush.Viewport%2A> définissez le et <xref:System.Windows.Media.TileBrush.TileMode%2A> les propriétés d’un <xref:System.Windows.Media.ImageBrush>, vous pouvez créer un modèle répétitif. L’exemple suivant peint un bouton en utilisant un modèle créé à partir d’une image.  
  
 [!code-csharp[UsingImageBrush_snip#TiledImageBrushExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/TiledImageBrushExample.cs#tiledimagebrushexamplewholepage)]
 [!code-vb[UsingImageBrush_snip#TiledImageBrushExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/UsingImageBrush_snip/VisualBasic/TiledImageBrushExample.vb#tiledimagebrushexamplewholepage)]  
  
 Pour plus d’informations sur la <xref:System.Windows.Media.ImageBrush> classe, voir Painting with [Images, Drawings, and Visuals](painting-with-images-drawings-and-visuals.md).  
  
 Cet exemple de code fait partie d’un exemple plus large qui est fourni pour la <xref:System.Windows.Media.ImageBrush> classe. Pour l’échantillon complet, voir [ImageBrush Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ImageBrush).  
  
## <a name="see-also"></a>Voir aussi

- [Peinture avec des images, des dessins et des objets visuels](painting-with-images-drawings-and-visuals.md)
