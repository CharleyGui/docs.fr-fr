---
title: Vue d'ensemble des objets Drawing
ms.date: 03/30/2017
helpviewer_keywords:
- ImageDrawing objects [WPF]
- GlyphRunDrawing objects [WPF]
- GeometryDrawing objects [WPF]
- drawings [WPF], about drawings
- Drawing objects [WPF]
- DrawingGroup objects [WPF]
ms.assetid: 9b5ce5c0-e204-4320-a7a8-0b2210d62f88
ms.openlocfilehash: d4527c331308ff6cd517705212e09428216d2378
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459735"
---
# <a name="drawing-objects-overview"></a>Vue d'ensemble des objets Drawing
Cette rubrique présente <xref:System.Windows.Media.Drawing> objets et décrit comment les utiliser pour dessiner efficacement des formes, des bitmaps, du texte et des médias. Utilisez <xref:System.Windows.Media.Drawing> objets lorsque vous créez des images clipart, peignez avec un <xref:System.Windows.Media.DrawingBrush>ou utilisez des objets <xref:System.Windows.Media.Visual>.  

<a name="whatisadrawingsection"></a>   
## <a name="what-is-a-drawing-object"></a>Qu’est-ce qu’un objet Drawing ?  
 Un objet <xref:System.Windows.Media.Drawing> décrit un contenu visible, tel qu’une forme, une image bitmap, une vidéo ou une ligne de texte. Différents types de dessins décrivent différents types de contenus. La liste suivante répertorie les différents types d’objets Drawing.  
  
- <xref:System.Windows.Media.GeometryDrawing> : dessine une forme.  
  
- <xref:System.Windows.Media.ImageDrawing> : dessine une image.  
  
- <xref:System.Windows.Media.GlyphRunDrawing> : dessine le texte.  
  
- <xref:System.Windows.Media.VideoDrawing> : lit un fichier audio ou vidéo.  
  
- <xref:System.Windows.Media.DrawingGroup> : dessine d’autres dessins. Utilisez un groupe de dessins pour faire de plusieurs dessins un seul et même dessin composite.  
  
 les objets <xref:System.Windows.Media.Drawing> sont polyvalents ; vous pouvez utiliser un objet <xref:System.Windows.Media.Drawing> de plusieurs façons.  
  
- Vous pouvez l’afficher en tant qu’image à l’aide d’un <xref:System.Windows.Media.DrawingImage> et d’un contrôle <xref:System.Windows.Controls.Image>.  
  
- Vous pouvez l’utiliser avec un <xref:System.Windows.Media.DrawingBrush> pour peindre un objet, tel que le <xref:System.Windows.Controls.Page.Background%2A> d’un <xref:System.Windows.Controls.Page>.  
  
- Vous pouvez l’utiliser pour décrire l’apparence d’un <xref:System.Windows.Media.DrawingVisual>.  
  
- Vous pouvez l’utiliser pour énumérer le contenu d’un <xref:System.Windows.Media.Visual>.  
  
 WPF fournit d’autres types d’objets qui sont capables de dessiner des formes, des images bitmaps, du texte et des médias. Par exemple, vous pouvez également utiliser des objets <xref:System.Windows.Shapes.Shape> pour dessiner des formes, et le contrôle <xref:System.Windows.Controls.MediaElement> offre une autre façon d’ajouter de la vidéo à votre application. Quand devez-vous utiliser des objets <xref:System.Windows.Media.Drawing> ? Lorsque vous pouvez sacrifier des fonctionnalités au niveau du Framework pour obtenir des avantages en matière de performances ou lorsque vous avez besoin de fonctionnalités de <xref:System.Windows.Freezable>. Étant donné que les objets <xref:System.Windows.Media.Drawing> ne prennent pas en charge la [disposition](../advanced/layout.md), l’entrée et le focus, ils offrent des avantages en matière de performances qui les rendent idéaux pour décrire les arrière-plans, les images clipart et les dessins de bas niveau avec des objets <xref:System.Windows.Media.Visual>.  
  
 Étant donné qu’il s’agit d’un objet de type <xref:System.Windows.Freezable>, <xref:System.Windows.Media.Drawing> objets bénéficient de plusieurs fonctionnalités spéciales, notamment les suivantes : ils peuvent être déclarés en tant que [ressources](../../../desktop-wpf/fundamentals/xaml-resources-define.md), partagés entre plusieurs objets, mis en lecture seule pour améliorer les performances, clonés et créés thread-safe. Pour plus d’informations sur les différentes fonctionnalités fournies par les objets <xref:System.Windows.Freezable>, consultez la [vue d’ensemble des objets Freezable](../advanced/freezable-objects-overview.md).  
  
<a name="drawinggeometriessection"></a>   
## <a name="draw-a-shape"></a>Dessiner une forme  
 Pour dessiner une forme, vous utilisez un <xref:System.Windows.Media.GeometryDrawing>. La propriété <xref:System.Windows.Media.GeometryDrawing.Geometry%2A> d’un dessin géométrique décrit la forme à dessiner, sa propriété <xref:System.Windows.Media.GeometryDrawing.Brush%2A> décrit comment l’intérieur de la forme doit être peint, et sa propriété <xref:System.Windows.Media.GeometryDrawing.Pen%2A> décrit comment son contour doit être dessiné.  
  
 L’exemple suivant utilise une <xref:System.Windows.Media.GeometryDrawing> pour dessiner une forme. La forme est décrite par un <xref:System.Windows.Media.GeometryGroup> et deux objets <xref:System.Windows.Media.EllipseGeometry>. L’intérieur de la forme est peint avec un <xref:System.Windows.Media.LinearGradientBrush> et son contour est dessiné à l’aide d’un <xref:System.Windows.Media.Pen><xref:System.Windows.Media.Brushes.Black%2A>.  
  
 Cet exemple crée la <xref:System.Windows.Media.GeometryDrawing>suivante.  
  
 ![GeometryDrawing de deux ellipses](./media/graphicsmm-geodraw.jpg "graphicsmm_geodraw")  
GeometryDrawing  
  
 [!code-csharp[DrawingMiscSnippets_snip#GeometryDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/GeometryDrawingExample.cs#geometrydrawingexampleinline)]
 [!code-xaml[DrawingMiscSnippets_snip#GeometryDrawingExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/GeometryDrawingExample.xaml#geometrydrawingexampleinline)]  
  
 Vous trouverez l’exemple complet sur la page [Créer un GeometryDrawing](how-to-create-a-geometrydrawing.md).  
  
 D’autres classes de <xref:System.Windows.Media.Geometry>, telles que <xref:System.Windows.Media.PathGeometry> vous permettent de créer des formes plus complexes en créant des courbes et des arcs. Pour plus d’informations sur les objets <xref:System.Windows.Media.Geometry>, consultez [vue d’ensemble](geometry-overview.md)de la géométrie.  
  
 Pour plus d’informations sur d’autres façons de dessiner des formes qui n’utilisent pas d’objets <xref:System.Windows.Media.Drawing>, consultez [vue d’ensemble des formes et des dessins de base dans WPF](shapes-and-basic-drawing-in-wpf-overview.md).  
  
<a name="drawingimagessection"></a>   
## <a name="draw-an-image"></a>Dessiner une image  
 Pour dessiner une image, vous utilisez un <xref:System.Windows.Media.ImageDrawing>. La propriété <xref:System.Windows.Media.ImageDrawing.ImageSource%2A> d’un objet <xref:System.Windows.Media.ImageDrawing> décrit l’image à dessiner, et sa propriété <xref:System.Windows.Media.ImageDrawing.Rect%2A> définit la région dans laquelle l’image est dessinée.  
  
 L’exemple suivant dessine une image dans un rectangle situé à (75,75), de 100 par 100 pixels. L’illustration suivante montre les <xref:System.Windows.Media.ImageDrawing> créés par l’exemple. Une bordure grise a été ajoutée pour montrer les limites du <xref:System.Windows.Media.ImageDrawing>.  
  
 ![ImageDrawing 100 par 100 dessiné à &#40;75,75&#41;](./media/graphicsmm-simple-imagedrawing-offset.png "graphicsmm_simple_imagedrawing_offset")  
ImageDrawing 100 par 100  
  
 [!code-csharp[DrawingMiscSnippets_snip#ImageDrawing100by100Inline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/ImageDrawingExample.cs#imagedrawing100by100inline)]
 [!code-xaml[DrawingMiscSnippets_snip#ImageDrawing100by100Inline](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/ImageDrawingExample.xaml#imagedrawing100by100inline)]  
  
 Pour plus d’informations sur les images, consultez la [Vue d’ensemble de la création d’images](imaging-overview.md).  
  
<a name="playmedia"></a>   
## <a name="play-media-code-only"></a>Lire un média (code uniquement)  
  
> [!NOTE]
> Bien que vous puissiez déclarer un <xref:System.Windows.Media.VideoDrawing> dans [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], vous pouvez uniquement charger et lire son contenu multimédia à l’aide de code. Pour lire une vidéo dans [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], utilisez un <xref:System.Windows.Controls.MediaElement> à la place.  
  
 Pour lire un fichier audio ou vidéo, vous utilisez un <xref:System.Windows.Media.VideoDrawing> et un <xref:System.Windows.Media.MediaPlayer>. Il y a deux façons de charger et de lire des médias. La première consiste à utiliser un <xref:System.Windows.Media.MediaPlayer> et un <xref:System.Windows.Media.VideoDrawing> à eux-mêmes, et la deuxième consiste à créer votre propre <xref:System.Windows.Media.MediaTimeline> à utiliser avec les <xref:System.Windows.Media.MediaPlayer> et les <xref:System.Windows.Media.VideoDrawing>.  
  
> [!NOTE]
> Lorsque vous distribuez un contenu multimédia avec votre application, vous ne pouvez pas utiliser de fichier multimédia comme ressource de projet, comme pour une image. Dans votre fichier projet, vous devez plutôt définir le type de média sur `Content` et définir `CopyToOutputDirectory` sur `PreserveNewest` ou `Always`.  
  
 Pour lire un média sans créer votre propre <xref:System.Windows.Media.MediaTimeline>, procédez comme suit.  
  
1. Créez un objet <xref:System.Windows.Media.MediaPlayer>.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline1)]  
  
2. Utilisez la méthode <xref:System.Windows.Media.MediaPlayer.Open%2A> pour charger le fichier multimédia.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline2](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline2)]  
  
3. Créer un <xref:System.Windows.Media.VideoDrawing>.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline3](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline3)]  
  
4. Spécifiez la taille et l’emplacement de dessin du média en définissant la propriété <xref:System.Windows.Media.VideoDrawing.Rect%2A> du <xref:System.Windows.Media.VideoDrawing>.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline4](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline4)]  
  
5. Définissez la propriété <xref:System.Windows.Media.VideoDrawing.Player%2A> du <xref:System.Windows.Media.VideoDrawing> avec la <xref:System.Windows.Media.MediaPlayer> que vous avez créée.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline5](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline5)]  
  
6. Utilisez la méthode <xref:System.Windows.Media.MediaPlayer.Play%2A> de la <xref:System.Windows.Media.MediaPlayer> pour démarrer la diffusion du média.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline6](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline6)]  
  
 L’exemple suivant utilise une <xref:System.Windows.Media.VideoDrawing> et un <xref:System.Windows.Media.MediaPlayer> pour lire un fichier vidéo une seule fois.  
  
 [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline)]  
  
 Pour obtenir un contrôle de minutage supplémentaire sur le média, utilisez une <xref:System.Windows.Media.MediaTimeline> avec les objets <xref:System.Windows.Media.MediaPlayer> et <xref:System.Windows.Media.VideoDrawing>. Le <xref:System.Windows.Media.MediaTimeline> vous permet de spécifier si la vidéo doit se répéter. Pour utiliser un <xref:System.Windows.Media.MediaTimeline> avec un <xref:System.Windows.Media.VideoDrawing>, procédez comme suit :  
  
1. Déclarez le <xref:System.Windows.Media.MediaTimeline> et définissez ses comportements de minutage.  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline1)]  
  
2. Créez un <xref:System.Windows.Media.MediaClock> à partir du <xref:System.Windows.Media.MediaTimeline>.  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline2](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline2)]  
  
3. Créez un <xref:System.Windows.Media.MediaPlayer> et utilisez la <xref:System.Windows.Media.MediaClock> pour définir sa propriété <xref:System.Windows.Media.MediaPlayer.Clock%2A>.  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline3](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline3)]  
  
4. Créez un <xref:System.Windows.Media.VideoDrawing> et affectez le <xref:System.Windows.Media.MediaPlayer> à la propriété <xref:System.Windows.Media.VideoDrawing.Player%2A> de l' <xref:System.Windows.Media.VideoDrawing>.  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline4](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline4)]  
  
 L’exemple suivant utilise un <xref:System.Windows.Media.MediaTimeline> avec un <xref:System.Windows.Media.MediaPlayer> et un <xref:System.Windows.Media.VideoDrawing> pour lire une vidéo à plusieurs reprises.  
  
 [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline)]  
  
 Notez que, lorsque vous utilisez une <xref:System.Windows.Media.MediaTimeline>, vous utilisez le <xref:System.Windows.Media.Animation.ClockController> interactif retourné par la propriété <xref:System.Windows.Media.Animation.Clock.Controller%2A> de la <xref:System.Windows.Media.MediaClock> pour contrôler la lecture du média au lieu des méthodes interactives de <xref:System.Windows.Media.MediaPlayer>.  
  
<a name="drawtext"></a>   
## <a name="draw-text"></a>Dessiner du texte  
 Pour dessiner du texte, vous utilisez un <xref:System.Windows.Media.GlyphRunDrawing> et un <xref:System.Windows.Media.GlyphRun>. L’exemple suivant utilise un <xref:System.Windows.Media.GlyphRunDrawing> pour dessiner le texte « Hello World ».  
  
 [!code-csharp[DrawingMiscSnippets_snip#GlyphRunDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/GlyphRunDrawingExample.cs#glyphrundrawingexampleinline)]
 [!code-xaml[DrawingMiscSnippets_snip#GlyphRunDrawingExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/GlyphRunExample.xaml#glyphrundrawingexampleinline)]  
  
 Un <xref:System.Windows.Media.GlyphRun> est un objet de bas niveau destiné à être utilisé avec des scénarios de présentation et d’impression de documents de format fixe. Un moyen plus simple de dessiner du texte à l’écran consiste à utiliser un <xref:System.Windows.Controls.Label> ou un <xref:System.Windows.Controls.TextBlock>. Pour plus d’informations sur <xref:System.Windows.Media.GlyphRun>, consultez la présentation [de l’objet GlyphRun et](../advanced/introduction-to-the-glyphrun-object-and-glyphs-element.md) de la vue d’ensemble des éléments Glyphs.  
  
<a name="compositedrawingssection"></a>   
## <a name="composite-drawings"></a>Dessins composites  
 Une <xref:System.Windows.Media.DrawingGroup> vous permet de combiner plusieurs dessins en un seul dessin composite. À l’aide d’un <xref:System.Windows.Media.DrawingGroup>, vous pouvez combiner des formes, des images et du texte en un seul objet <xref:System.Windows.Media.Drawing>.  
  
 L’exemple suivant utilise un <xref:System.Windows.Media.DrawingGroup> pour combiner deux objets <xref:System.Windows.Media.GeometryDrawing> et un objet <xref:System.Windows.Media.ImageDrawing>. Cet exemple produit la sortie suivante.  
  
 ![DrawingGroup avec plusieurs dessins](./media/graphicsmm-simple.jpg "graphicsmm_simple")  
Un dessin composite  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMSimpleDrawingGroupExample](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingGroupExample.cs#graphicsmmsimpledrawinggroupexample)]
 [!code-xaml[DrawingMiscSnippets_snip#GraphicsMMSimpleDrawingGroupExample](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingGroupExample.xaml#graphicsmmsimpledrawinggroupexample)]  
  
 Un <xref:System.Windows.Media.DrawingGroup> vous permet également d’appliquer des masques d’opacité, des transformations, des effets bitmap et d’autres opérations à son contenu. <xref:System.Windows.Media.DrawingGroup> opérations sont appliquées dans l’ordre suivant : <xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>, <xref:System.Windows.Media.DrawingGroup.Opacity%2A>, <xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>, <xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>, <xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A>, puis <xref:System.Windows.Media.DrawingGroup.Transform%2A>.  
  
 L’illustration suivante montre l’ordre dans lequel les opérations de <xref:System.Windows.Media.DrawingGroup> sont appliquées.  
  
 ![Ordre des opérations DrawingGroup](./media/graphcismm-drawinggroup-order.png "graphcismm_drawinggroup_order")  
Ordre des opérations DrawingGroup  
  
 Le tableau suivant décrit les propriétés que vous pouvez utiliser pour manipuler le contenu d’un objet <xref:System.Windows.Media.DrawingGroup>.  
  
|Property|Description|Illustration|  
|--------------|-----------------|------------------|  
|<xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>|Modifie l’opacité des parties sélectionnées du contenu de <xref:System.Windows.Media.DrawingGroup>. Vous trouverez un exemple sur la page [Guide pratique : contrôler l’opacité d’un dessin](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms748242(v=vs.90)).|![DrawingGroup avec un masque d’opacité](./media/graphicsmm-opmask.png "graphicsmm_opmask")|  
|<xref:System.Windows.Media.DrawingGroup.Opacity%2A>|Modifie uniformément l’opacité du contenu <xref:System.Windows.Media.DrawingGroup>. Utilisez cette propriété pour rendre un <xref:System.Windows.Media.Drawing> transparent ou partiellement transparent. Vous trouverez un exemple sur la page [Guide pratique : appliquer un masque d’opacité à un dessin](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms753195(v=vs.90)).|![DrawingGroups avec différents paramètres d’opacité](./media/graphicsmm-opacity.png "graphicsmm_opacity")|  
|<xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>|Applique une <xref:System.Windows.Media.Effects.BitmapEffect> au contenu <xref:System.Windows.Media.DrawingGroup>. Vous trouverez un exemple sur la page [Guide pratique : appliquer un BitmapEffect à un dessin](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms752341(v=vs.90)).|![DrawingGroup avec un BlurBitmapEffect](./media/graphicsmm-bitmap.png "graphicsmm_bitmap")|  
|<xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>|Découpe le contenu du <xref:System.Windows.Media.DrawingGroup> dans une région que vous décrivez à l’aide d’un <xref:System.Windows.Media.Geometry>. Vous trouverez un exemple sur la page [Guide pratique : détourer un dessin](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms743068(v=vs.90)) .|![DrawingGroup avec une zone de découpage définie](./media/graphicsmm-clipgeom.png "graphicsmm_clipgeom")|  
|<xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A>|Aligne des pixels indépendants des appareils sur les pixels de l’appareil selon les instructions spécifiées. Cette propriété est utile pour s’assurer que les graphismes très détaillés s’affichent nettement sur les écrans basse résolution. Vous trouverez un exemple sur la page [Guide pratique : appliquer un GuidelineSet à un dessin](how-to-apply-a-guidelineset-to-a-drawing.md).|![DrawingGroup avec et sans GuidelineSet](./media/graphicsmm-drawinggroup-guidelineset.png "graphicsmm_drawinggroup_guidelineset")|  
|<xref:System.Windows.Media.DrawingGroup.Transform%2A>|Transforme le contenu du <xref:System.Windows.Media.DrawingGroup>. Vous trouverez un exemple sur la page [Guide pratique : appliquer un Transform à un dessin](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms742304(v=vs.90)).|![DrawingGroup pivoté](./media/graphicsmm-rotate.png "graphicsmm_rotate")|  
  
<a name="usingimagedrawing"></a>   
## <a name="display-a-drawing-as-an-image"></a>Afficher un dessin comme image  
 Pour afficher un <xref:System.Windows.Media.Drawing> avec un contrôle <xref:System.Windows.Controls.Image>, utilisez un <xref:System.Windows.Media.DrawingImage> comme <xref:System.Windows.Controls.Image.Source%2A> du contrôle <xref:System.Windows.Controls.Image> et définissez la propriété <xref:System.Windows.Media.DrawingImage> de l’objet <xref:System.Windows.Media.DrawingImage.Drawing%2A?displayProperty=nameWithType> sur le dessin que vous souhaitez afficher.  
  
 L’exemple suivant utilise un <xref:System.Windows.Media.DrawingImage> et un contrôle <xref:System.Windows.Controls.Image> pour afficher un <xref:System.Windows.Media.GeometryDrawing>. Cet exemple produit la sortie suivante.  
  
 ![GeometryDrawing de deux ellipses](./media/graphicsmm-geodraw.jpg "graphicsmm_geodraw")  
DrawingImage  
  
 [!code-csharp[DrawingMiscSnippets_snip#DrawingImageExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingImageExample.cs#drawingimageexamplewholepage)]
 [!code-xaml[DrawingMiscSnippets_snip#DrawingImageExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingImageExample.xaml#drawingimageexamplewholepage)]  
  
<a name="renderingwithdrawingbrushsection"></a>   
## <a name="paint-an-object-with-a-drawing"></a>Peindre un objet avec un dessin  
 Un <xref:System.Windows.Media.DrawingBrush> est un type de pinceau qui peint une zone avec un objet Drawing. Vous pouvez l’utiliser pour peindre n’importe quel objet graphique avec un dessin. La propriété <xref:System.Windows.Media.Drawing> d’un <xref:System.Windows.Media.DrawingBrush> décrit son <xref:System.Windows.Media.DrawingBrush.Drawing%2A>. Pour afficher un <xref:System.Windows.Media.Drawing> avec un <xref:System.Windows.Media.DrawingBrush>, ajoutez-le au pinceau à l’aide de la propriété <xref:System.Windows.Media.Drawing> du pinceau et utilisez le pinceau pour peindre un objet graphique, tel qu’un contrôle ou un panneau.  
  
 Les exemples suivants utilisent une <xref:System.Windows.Media.DrawingBrush> pour peindre l' <xref:System.Windows.Shapes.Shape.Fill%2A> d’un <xref:System.Windows.Shapes.Rectangle> avec un modèle créé à partir d’un <xref:System.Windows.Media.GeometryDrawing>. Cet exemple produit la sortie suivante.  
  
 ![DrawingBrush en mosaïque](./media/graphicsmm-drawingbrush-geometrydrawing.png "graphicsmm_drawingbrush_geometrydrawing")  
GeometryDrawing utilisé avec un DrawingBrush  
  
 [!code-csharp[DrawingMiscSnippets_snip#DrawingBrushExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingBrushExample.cs#drawingbrushexamplewholepage)]
 [!code-xaml[DrawingMiscSnippets_snip#DrawingBrushExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingBrushExample.xaml#drawingbrushexamplewholepage)]  
  
 La classe <xref:System.Windows.Media.DrawingBrush> fournit diverses options pour l’étirement et la mosaïque de son contenu. Pour plus d’informations sur <xref:System.Windows.Media.DrawingBrush>, consultez vue d’ensemble [de la peinture avec des images, des dessins et](painting-with-images-drawings-and-visuals.md) des éléments visuels.  
  
<a name="renderingwithvisualsection"></a>   
## <a name="render-a-drawing-with-a-visual"></a>Afficher un dessin avec un objet visuel  
 Un <xref:System.Windows.Media.DrawingVisual> est un type d’objet visuel conçu pour restituer un dessin. Les développeurs qui souhaitent créer un environnement graphique hautement personnalisé peuvent travailler directement sur la couche visuelle, qui n’est pas décrite dans cette vue d’ensemble. Pour plus d’informations, consultez la vue d’ensemble [Utiliser des objets DrawingVisual](using-drawingvisual-objects.md).  
  
<a name="drawingcontextobjects"></a>   
## <a name="drawingcontext-objects"></a>Objets DrawingContext  
 La classe <xref:System.Windows.Media.DrawingContext> vous permet de remplir un <xref:System.Windows.Media.Visual> ou un <xref:System.Windows.Media.Drawing> avec un contenu visuel. De nombreux objets graphiques de niveau inférieur utilisent un <xref:System.Windows.Media.DrawingContext>, car il décrit très efficacement le contenu graphique.  
  
 Bien que les méthodes de dessin <xref:System.Windows.Media.DrawingContext> apparaissent comme les méthodes Draw du type <xref:System.Drawing.Graphics?displayProperty=nameWithType>, elles sont en fait très différentes. <xref:System.Windows.Media.DrawingContext> est utilisé avec un système graphique en mode de conservation, tandis que le type de <xref:System.Drawing.Graphics?displayProperty=nameWithType> est utilisé avec un système graphique en mode immédiat. Lorsque vous utilisez les commandes de dessin d’un objet <xref:System.Windows.Media.DrawingContext>, vous stockez en fait un jeu d’instructions de rendu (bien que le mécanisme de stockage exact dépende du type d’objet qui fournit la <xref:System.Windows.Media.DrawingContext>) qui sera utilisé par la suite par le système graphique. vous n’effectuez pas de dessin à l’écran en temps réel. Pour plus d’informations sur le fonctionnement du système graphique Windows Presentation Foundation (WPF), consultez [vue d’ensemble du rendu graphique de WPF](wpf-graphics-rendering-overview.md).  
  
 Vous n’instanciez jamais directement un <xref:System.Windows.Media.DrawingContext>; Toutefois, vous pouvez acquérir un contexte de dessin à partir de certaines méthodes, telles que <xref:System.Windows.Media.DrawingGroup.Open%2A?displayProperty=nameWithType> et <xref:System.Windows.Media.DrawingVisual.RenderOpen%2A?displayProperty=nameWithType>.  
  
<a name="enumeratevisualcontents"></a>   
## <a name="enumerate-the-contents-of-a-visual"></a>Énumérer le contenu d’un objet visuel  
 En plus de leurs autres utilisations, les objets <xref:System.Windows.Media.Drawing> fournissent également un modèle objet pour énumérer le contenu d’une <xref:System.Windows.Media.Visual>.  
  
 L’exemple suivant utilise la méthode <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A> pour récupérer la valeur <xref:System.Windows.Media.DrawingGroup> d’un <xref:System.Windows.Media.Visual> et l’énumérer.  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMRetrieveDrawings](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/EnumerateDrawingsExample.xaml.cs#graphicsmmretrievedrawings)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Media.Drawing>
- <xref:System.Windows.Media.DrawingGroup>
- [Graphiques 2D et acquisition d'images](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [Peinture avec des images, des dessins et des objets visuels](painting-with-images-drawings-and-visuals.md)
- [Vue d’ensemble de Geometry](geometry-overview.md)
- [Vue d’ensemble des formes et dessins de base dans WPF](shapes-and-basic-drawing-in-wpf-overview.md)
- [Vue d’ensemble du rendu graphique de WPF](wpf-graphics-rendering-overview.md)
- [Vue d’ensemble des objets Freezable](../advanced/freezable-objects-overview.md)
- [Rubriques de guide pratique](drawings-how-to-topics.md)
