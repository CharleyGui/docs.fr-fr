---
title: Vue d'ensemble de TileBrush
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TileBrush [WPF]
- brushes [WPF], TileBrush
ms.assetid: aa4a7b7e-d09d-44c2-8d61-310c50e08d68
ms.openlocfilehash: 99bcc8695206030a381d71df2dda495867d3e9c7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187096"
---
# <a name="tilebrush-overview"></a>Vue d'ensemble de TileBrush
<xref:System.Windows.Media.TileBrush>objets vous fournir un grand contrôle sur la façon dont <xref:System.Windows.Media.Drawing>une <xref:System.Windows.Media.Visual>zone est peinte avec une image, , ou . Ce sujet décrit comment <xref:System.Windows.Media.TileBrush> utiliser les fonctionnalités <xref:System.Windows.Media.ImageBrush>pour <xref:System.Windows.Media.DrawingBrush>gagner <xref:System.Windows.Media.VisualBrush> plus de contrôle sur la façon dont un , , ou peint une zone.  

<a name="prerequisite"></a>
## <a name="prerequisites"></a>Conditions préalables requises  
 Pour comprendre ce sujet, il est utile de comprendre <xref:System.Windows.Media.ImageBrush>comment <xref:System.Windows.Media.DrawingBrush>utiliser <xref:System.Windows.Media.VisualBrush> les caractéristiques de base de la , , ou la classe. Pour une introduction à ces types, voir la [peinture avec des images, des dessins et des visuels](painting-with-images-drawings-and-visuals.md).  
  
<a name="tilebrush"></a>
## <a name="painting-an-area-with-tiles"></a>Peindre une zone avec des mosaïques  
 <xref:System.Windows.Media.ImageBrush>, <xref:System.Windows.Media.DrawingBrush>sont <xref:System.Windows.Media.VisualBrush> des <xref:System.Windows.Media.TileBrush> types d’objets. Les pinceaux mosaïque vous permettent de bien contrôler le remplissage d’une zone avec une image, un dessin ou un objet visuel. Par exemple, au lieu de simplement peindre une zone avec une seule image étirée, vous pouvez peindre une zone avec une série de mosaïques d’image qui créent un motif.  
  
 Peindre une zone avec un pinceau mosaïque implique trois composants : un contenu, une mosaïque de base et une zone de sortie.  
  
 ![Composants de TileBrush](./media/wcpsdk-mmgraphics-defaultcontentprojection2.png "wcpsdk_mmgraphics_defaultcontentprojection2")  
Composants d’un TileBrush avec une seule mosaïque  
  
 ![Composants d'un TileBrush en mosaïque](./media/graphicsmm-tiledprojection.png "graphicsmm_tiledprojection")  
Composants d’un TileBrush avec un TileMode de mosaïque  
  
 La zone de sortie est la <xref:System.Windows.Shapes.Shape.Fill%2A> zone <xref:System.Windows.Shapes.Ellipse> peinte, comme la d’un ou l’un <xref:System.Windows.Controls.Control.Background%2A> <xref:System.Windows.Controls.Button>. Les sections suivantes décrivent les deux <xref:System.Windows.Media.TileBrush>autres composantes d’un .  
  
<a name="brushcontent"></a>
## <a name="brush-content"></a>Contenu de pinceau  
 Il existe trois <xref:System.Windows.Media.TileBrush> types différents et chaque peint avec un type différent de contenu.  
  
- Si le pinceau <xref:System.Windows.Media.ImageBrush>est un , <xref:System.Windows.Media.ImageBrush.ImageSource%2A> ce contenu est une <xref:System.Windows.Media.ImageBrush>image La propriété spécifie le contenu de la .  
  
- Si le pinceau <xref:System.Windows.Media.DrawingBrush>est un , ce contenu est un dessin. La <xref:System.Windows.Media.DrawingBrush.Drawing%2A> propriété spécifie <xref:System.Windows.Media.DrawingBrush>le contenu de la .  
  
- Si le pinceau <xref:System.Windows.Media.VisualBrush>est un , ce contenu est un visuel. La <xref:System.Windows.Media.VisualBrush.Visual%2A> propriété spécifie <xref:System.Windows.Media.VisualBrush>le contenu de la .  
  
 Vous pouvez spécifier <xref:System.Windows.Media.TileBrush> la position <xref:System.Windows.Media.TileBrush.Viewbox%2A> et les dimensions du <xref:System.Windows.Media.TileBrush.Viewbox%2A> contenu en utilisant la propriété, bien qu’il soit courant de laisser l’ensemble à sa valeur par défaut. Par défaut, <xref:System.Windows.Media.TileBrush.Viewbox%2A> le est configuré pour contenir complètement le contenu de la brosse. Pour plus d’informations <xref:System.Windows.Controls.Viewbox>sur la <xref:System.Windows.Controls.Viewbox> configuration de la , voir la page de propriété.  
  
<a name="thebasetile"></a>
## <a name="the-base-tile"></a>La mosaïque de base  
 Un <xref:System.Windows.Media.TileBrush> projette son contenu sur une tuile de base. La <xref:System.Windows.Media.TileBrush.Stretch%2A> propriété <xref:System.Windows.Media.TileBrush> contrôle la façon dont le contenu est étiré pour remplir la tuile de base. Le <xref:System.Windows.Media.TileBrush.Stretch%2A> bien accepte les valeurs suivantes, définies par l’énumération <xref:System.Windows.Media.Stretch> :  
  
- <xref:System.Windows.Media.Stretch.None>: Le contenu du pinceau n’est pas étiré pour remplir la tuile.  
  
- <xref:System.Windows.Media.Stretch.Fill>: Le contenu du pinceau est mis à l’échelle pour s’adapter à la tuile. Étant donné que la hauteur et la largeur du contenu sont mis à l’échelle indépendamment, les proportions d’origine du contenu risquent de ne pas être conservées. Autrement dit, le contenu du pinceau peut être déformé pour remplir complètement la mosaïque de sortie.  
  
- <xref:System.Windows.Media.Stretch.Uniform>: Le contenu du pinceau est mis à l’échelle de sorte qu’il s’intègre complètement dans la tuile. Les proportions du contenu sont conservées.  
  
- <xref:System.Windows.Media.Stretch.UniformToFill>: Le contenu du pinceau est mis à l’échelle de sorte qu’il remplit complètement la zone de sortie tout en préservant le rapport d’aspect original du contenu.  
  
 L’image suivante illustre <xref:System.Windows.Media.TileBrush.Stretch%2A> les différents paramètres.  
  
 ![Différents paramètres d’étirement TileBrush](./media/img-mmgraphics-stretchenum.jpg "img_mmgraphics_stretchenum")  
  
 Dans l’exemple suivant, <xref:System.Windows.Media.ImageBrush> le contenu d’un est défini de sorte qu’il ne s’étend pas pour remplir la zone de sortie.  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMNoStretchExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/StretchExample.xaml#graphicsmmnostretchexample)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMNoStretchExample](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/StretchExample.cs#graphicsmmnostretchexample)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMNoStretchExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/stretchexample.vb#graphicsmmnostretchexample)]  
  
 Par défaut, <xref:System.Windows.Media.TileBrush> un génère une seule tuile (la tuile de base) et s’étire cette tuile pour remplir complètement la zone de sortie. Vous pouvez modifier la taille et la position <xref:System.Windows.Media.TileBrush.Viewport%2A> <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> de la tuile de base en définissant le et les propriétés.  
  
<a name="basetilesize"></a>
### <a name="base-tile-size"></a>Taille de la mosaïque de base  
 La <xref:System.Windows.Media.TileBrush.Viewport%2A> propriété détermine la taille et la position <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> de la tuile de base, et la propriété détermine si la propriété est spécifiée à l’aide <xref:System.Windows.Media.TileBrush.Viewport%2A> de coordonnées absolues ou relatives. Si les coordonnées sont relatives, elles sont relatives à la taille de la zone de sortie. Le point (0,0) représente le coin supérieur gauche de la zone de sortie et (1,1) représente le coin inférieur droit de la zone de sortie. Pour spécifier que la <xref:System.Windows.Media.TileBrush.Viewport%2A> propriété <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> utilise <xref:System.Windows.Media.BrushMappingMode.Absolute>des coordonnées absolues, définissez la propriété à .  
  
 L’illustration suivante montre la <xref:System.Windows.Media.TileBrush> différence de <xref:System.Windows.Media.TileBrush.ViewportUnits%2A>sortie entre un avec parent versus absolu . Notez que chaque illustration représente un motif en mosaïque ; la section suivante décrit comment spécifier un tel motif.  
  
 ![Unités de fenêtre d’affichage absolues et relatives](./media/absolute-and-relative-viewports.png "absolute_and_relative_viewports")  
  
 Dans l’exemple suivant, une image est utilisée pour créer une mosaïque ayant une largeur et une hauteur de 50 %. La mosaïque de base se trouve au point (0,0) de la zone de sortie.  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMRelativeViewportUnitsExample1](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/TileSizeExample.xaml#graphicsmmrelativeviewportunitsexample1)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMRelativeViewportUnitsExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/TileSizeExample.cs#graphicsmmrelativeviewportunitsexample1)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMRelativeViewportUnitsExample1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/tilesizeexample.vb#graphicsmmrelativeviewportunitsexample1)]  
  
 L’exemple suivant définit les <xref:System.Windows.Media.ImageBrush> tuiles d’un à 25 par 25 pixels indépendants de l’appareil. Parce <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> que les <xref:System.Windows.Media.ImageBrush> tuiles sont absolues, les tuiles sont toujours 25 par 25 pixels, quelle que soit la taille de la zone peinte.  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMAbsoluteViewportUnitsExample1](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/TileSizeExample.xaml#graphicsmmabsoluteviewportunitsexample1)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMAbsoluteViewportUnitsExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/TileSizeExample.cs#graphicsmmabsoluteviewportunitsexample1)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMAbsoluteViewportUnitsExample1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/tilesizeexample.vb#graphicsmmabsoluteviewportunitsexample1)]  
  
<a name="tilingbehavior"></a>
### <a name="tiling-behavior"></a>Comportement des mosaïques  
 A <xref:System.Windows.Media.TileBrush> produit un motif carrelé lorsque sa tuile de base ne <xref:System.Windows.Media.TileMode.None> remplit pas complètement la zone de sortie et un mode de carrelage autre est alors spécifié. Lorsque la tuile d’une brosse à tuiles ne <xref:System.Windows.Media.TileBrush.TileMode%2A> remplit pas complètement la zone de sortie, sa propriété précise si la tuile de base doit être dupliquée pour remplir la zone de sortie et, dans l’affirmative, comment la tuile de base doit être dupliquée. Le <xref:System.Windows.Media.TileBrush.TileMode%2A> bien accepte les valeurs suivantes, définies par l’énumération <xref:System.Windows.Media.TileMode> :  
  
- <xref:System.Windows.Media.TileMode.None>: Seule la tuile de base est dessinée.  
  
- <xref:System.Windows.Media.TileMode.Tile>: La tuile de base est dessinée et la zone restante est remplie en répétant la tuile de base de telle sorte que le bord droit d’une tuile est adjacent au bord gauche de la suivante, et de même pour le bas et le haut.  
  
- <xref:System.Windows.Media.TileMode.FlipX>: Les <xref:System.Windows.Media.TileMode.Tile>mêmes que , mais d’autres colonnes de tuiles sont retournées horizontalement.  
  
- <xref:System.Windows.Media.TileMode.FlipY>: La <xref:System.Windows.Media.TileMode.Tile>même chose que , mais d’autres rangées de tuiles sont retournées verticalement.  
  
- <xref:System.Windows.Media.TileMode.FlipXY>: Une <xref:System.Windows.Media.TileMode.FlipX> combinaison <xref:System.Windows.Media.TileMode.FlipY>de et .  
  
 Les images suivantes illustrent les différents modes de mosaïque.  
  
 ![Différents paramètres TileMode pour TileBrush](./media/img-mmgraphics-tilemodes.gif "img_mmgraphics_tilemodes")  
  
 Dans l’exemple suivant, une image est utilisée pour peindre un rectangle de 100 pixels de large et 100 pixels de haut. En fixant le <xref:System.Windows.Media.TileBrush.Viewport%2A> pinceau a été fixé à 0,0,0.25,0.25, la tuile de base de la brosse est faite pour être 1/4 de la zone de sortie. Le pinceau <xref:System.Windows.Media.TileBrush.TileMode%2A> est réglé <xref:System.Windows.Media.TileMode.FlipXY>pour . afin qu’il remplisse le rectangle de lignes de mosaïques.  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMFlipXYExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/TilingExample.xaml#graphicsmmflipxyexample)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMFlipXYExample](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/TilingExample.cs#graphicsmmflipxyexample)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMFlipXYExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/tilingexample.vb#graphicsmmflipxyexample)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Media.ImageBrush>
- <xref:System.Windows.Media.DrawingBrush>
- <xref:System.Windows.Media.VisualBrush>
- <xref:System.Windows.Media.TileBrush>
- [Peinture avec des images, des dessins et des objets visuels](painting-with-images-drawings-and-visuals.md)
- [Sujets comment se passer](brushes-how-to-topics.md)
- [Vue d’ensemble des objets Freezable](../advanced/freezable-objects-overview.md)
- [ImageBrush Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ImageBrush) (Exemple d’ImageBrush)
- [VisualBrush Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/VisualBrush) (Exemple de VisualBrush)
