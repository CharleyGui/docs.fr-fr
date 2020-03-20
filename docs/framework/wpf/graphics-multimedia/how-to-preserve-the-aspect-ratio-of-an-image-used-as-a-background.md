---
title: "Comment : conserver les proportions d'une image utilisée comme arrière-plan"
ms.date: 03/30/2017
helpviewer_keywords:
- aspect ratios of background images [WPF], preserving
- brushes [WPF], preserving aspect ratios of background images
- background images [WPF], preserving aspect ratios
ms.assetid: 28c39478-13d7-4011-80a3-8b9cc3e54478
ms.openlocfilehash: b467fcd353994faef19b5a997e03d6582789eac1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186029"
---
# <a name="how-to-preserve-the-aspect-ratio-of-an-image-used-as-a-background"></a>Comment : conserver les proportions d'une image utilisée comme arrière-plan
Cet exemple montre comment <xref:System.Windows.Media.TileBrush.Stretch%2A> utiliser <xref:System.Windows.Media.ImageBrush> la propriété d’un afin de préserver le rapport d’aspect de l’image.  
  
 Par défaut, lorsque <xref:System.Windows.Media.ImageBrush> vous utilisez un pour peindre une zone, son contenu s’étend pour remplir complètement la zone de sortie. Lorsque la zone de sortie et l’image ont des proportions différentes, l’image est déformée par cet étirement.  
  
 Pour préserver <xref:System.Windows.Media.ImageBrush> le rapport d’aspect de <xref:System.Windows.Media.TileBrush.Stretch%2A> son <xref:System.Windows.Media.Stretch.Uniform> <xref:System.Windows.Media.Stretch.UniformToFill>image, définissez la propriété à ou .  
  
## <a name="example"></a> Exemple  
 L’exemple suivant <xref:System.Windows.Media.ImageBrush> utilise deux objets pour peindre deux rectangles. Chaque rectangle est de 300 par 150 pixels et chacun contient une image de 300 par 300 pixels. La <xref:System.Windows.Media.TileBrush.Stretch%2A> propriété de la première <xref:System.Windows.Media.Stretch.Uniform>brosse <xref:System.Windows.Media.TileBrush.Stretch%2A> est réglée à , <xref:System.Windows.Media.Stretch.UniformToFill>et la propriété de la deuxième brosse est réglée à .  
  
 [!code-csharp[UsingImageBrush_snip#ImageBrushStretchModesExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/StretchModes.cs#imagebrushstretchmodesexamplewholepage)]  
  
 L’illustration suivante montre la sortie du <xref:System.Windows.Media.TileBrush.Stretch%2A> premier <xref:System.Windows.Media.Stretch.Uniform>pinceau, qui a un réglage de .  
  
 ![ImageBrush avec étirement Uniform](./media/graphicsmm-imagebrushuniformstretch.jpg "graphicsmm_ImageBrushUniformStretch")  
  
 L’illustration suivante montre la sortie du <xref:System.Windows.Media.TileBrush.Stretch%2A> deuxième <xref:System.Windows.Media.Stretch.UniformToFill>pinceau, qui a un réglage de .  
  
 ![ImageBrush avec étirement UniformToFill](./media/graphicsmm-imagebrushuniformtofillstretch.jpg "graphicsmm_ImageBrushUniformToFillStretch")  
  
 Notez <xref:System.Windows.Media.TileBrush.Stretch%2A> que la propriété se <xref:System.Windows.Media.TileBrush> comporte à l’identique pour les autres objets, c’est-à-dire, pour <xref:System.Windows.Media.DrawingBrush> et <xref:System.Windows.Media.VisualBrush>. Pour plus <xref:System.Windows.Media.ImageBrush> d’informations <xref:System.Windows.Media.TileBrush> sur et les autres objets, voir [Painting with Images, Drawings, and Visuals](painting-with-images-drawings-and-visuals.md).  
  
 Notez également que, bien que <xref:System.Windows.Media.TileBrush.Stretch%2A> <xref:System.Windows.Media.TileBrush> la propriété semble spécifier comment le <xref:System.Windows.Media.TileBrush> contenu s’étend pour s’adapter à sa zone de sortie, il spécifie en fait comment le contenu s’étend pour remplir sa tuile de base. Pour plus d’informations, consultez <xref:System.Windows.Media.TileBrush>.  
  
 Cet exemple de code fait partie d’un exemple plus large qui est fourni pour la <xref:System.Windows.Media.ImageBrush> classe. Pour l’échantillon complet, voir [ImageBrush Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ImageBrush).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Media.TileBrush>
- [Peinture avec des images, des dessins et des objets visuels](painting-with-images-drawings-and-visuals.md)
