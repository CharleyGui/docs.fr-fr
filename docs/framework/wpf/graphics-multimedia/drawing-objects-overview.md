---
title: Vue d'ensemble des objets Drawing
description: Familiarisez-vous avec les objets et comment les utiliser pour dessiner efficacement des formes, des bitmaps, du texte et des médias dans Windows Presentation Foundation (WPF).
ms.date: 03/30/2017
helpviewer_keywords:
- ImageDrawing objects [WPF]
- GlyphRunDrawing objects [WPF]
- GeometryDrawing objects [WPF]
- drawings [WPF], about drawings
- Drawing objects [WPF]
- DrawingGroup objects [WPF]
ms.assetid: 9b5ce5c0-e204-4320-a7a8-0b2210d62f88
ms.openlocfilehash: f00a59cd6e799e57f238c5f9b72ecc48e8445475
ms.sourcegitcommit: b6a1869f97a37f11a68c90afde1a520a6887dcbc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85853838"
---
# <a name="drawing-objects-overview"></a>Vue d'ensemble des objets Drawing
Cette rubrique présente <xref:System.Windows.Media.Drawing> les objets et explique comment les utiliser pour dessiner efficacement des formes, des bitmaps, du texte et des médias. Utilisez <xref:System.Windows.Media.Drawing> des objets lorsque vous créez des images clipart, peignez avec un <xref:System.Windows.Media.DrawingBrush> ou utilisez des <xref:System.Windows.Media.Visual> objets.  

<a name="whatisadrawingsection"></a>
## <a name="what-is-a-drawing-object"></a>Qu’est-ce qu’un objet Drawing ?  
 Un <xref:System.Windows.Media.Drawing> objet décrit un contenu visible, tel qu’une forme, une image bitmap, une vidéo ou une ligne de texte. Différents types de dessins décrivent différents types de contenus. La liste suivante répertorie les différents types d’objets Drawing.  
  
- <xref:System.Windows.Media.GeometryDrawing>: Dessine une forme.  
  
- <xref:System.Windows.Media.ImageDrawing>: Dessine une image.  
  
- <xref:System.Windows.Media.GlyphRunDrawing>: Dessine le texte.  
  
- <xref:System.Windows.Media.VideoDrawing>: Lit un fichier audio ou vidéo.  
  
- <xref:System.Windows.Media.DrawingGroup>: Dessine d’autres dessins. Utilisez un groupe de dessins pour faire de plusieurs dessins un seul et même dessin composite.  
  
 <xref:System.Windows.Media.Drawing>les objets sont polyvalents ; vous pouvez utiliser un objet de plusieurs façons <xref:System.Windows.Media.Drawing> .  
  
- Vous pouvez l’afficher en tant qu’image à l’aide d’un <xref:System.Windows.Media.DrawingImage> et d’un <xref:System.Windows.Controls.Image> contrôle.  
  
- Vous pouvez l’utiliser avec un <xref:System.Windows.Media.DrawingBrush> pour peindre un objet, tel que le <xref:System.Windows.Controls.Page.Background%2A> d’un <xref:System.Windows.Controls.Page> .  
  
- Vous pouvez l’utiliser pour décrire l’apparence d’un <xref:System.Windows.Media.DrawingVisual> .  
  
- Vous pouvez l’utiliser pour énumérer le contenu d’un <xref:System.Windows.Media.Visual> .  
  
 WPF fournit d’autres types d’objets qui sont capables de dessiner des formes, des images bitmaps, du texte et des médias. Par exemple, vous pouvez également utiliser des <xref:System.Windows.Shapes.Shape> objets pour dessiner des formes, et le <xref:System.Windows.Controls.MediaElement> contrôle offre une autre façon d’ajouter de la vidéo à votre application. Quand faut-il utiliser des <xref:System.Windows.Media.Drawing> objets ? Lorsque vous pouvez sacrifier des fonctionnalités au niveau du Framework pour obtenir des avantages en matière de performances ou lorsque vous avez besoin de <xref:System.Windows.Freezable> fonctionnalités. Étant donné que les <xref:System.Windows.Media.Drawing> objets ne prennent pas en charge la [disposition](../advanced/layout.md), l’entrée et le focus, ils offrent des avantages en matière de performances qui les rendent idéaux pour décrire les arrière-plans, les images clipart et les dessins de bas niveau avec des <xref:System.Windows.Media.Visual> objets.  
  
 Étant donné qu’il s’agit d’un objet de type <xref:System.Windows.Freezable> , <xref:System.Windows.Media.Drawing> les objets ont plusieurs fonctionnalités spéciales, notamment les suivantes : ils peuvent être déclarés en tant que [ressources](../../../desktop-wpf/fundamentals/xaml-resources-define.md), partagés entre plusieurs objets, mis en lecture seule pour améliorer les performances, clonés et rendus thread-safe. Pour plus d’informations sur les différentes fonctionnalités fournies par les <xref:System.Windows.Freezable> objets, consultez la [vue d’ensemble des objets Freezable](../advanced/freezable-objects-overview.md).  
  
<a name="drawinggeometriessection"></a>
## <a name="draw-a-shape"></a>Dessiner une forme  
 Pour dessiner une forme, vous utilisez un <xref:System.Windows.Media.GeometryDrawing> . La propriété d’un dessin géométrique <xref:System.Windows.Media.GeometryDrawing.Geometry%2A> décrit la forme à dessiner, sa <xref:System.Windows.Media.GeometryDrawing.Brush%2A> propriété décrit comment l’intérieur de la forme doit être peint, et sa <xref:System.Windows.Media.GeometryDrawing.Pen%2A> propriété décrit comment son contour doit être dessiné.  
  
 L’exemple suivant utilise un <xref:System.Windows.Media.GeometryDrawing> pour dessiner une forme. La forme est décrite par un <xref:System.Windows.Media.GeometryGroup> et deux <xref:System.Windows.Media.EllipseGeometry> objets. L’intérieur de la forme est peint avec un <xref:System.Windows.Media.LinearGradientBrush> et son contour est dessiné avec un <xref:System.Windows.Media.Brushes.Black%2A> <xref:System.Windows.Media.Pen> .  
  
 Cet exemple crée ce qui suit <xref:System.Windows.Media.GeometryDrawing> .  
  
 ![GeometryDrawing de deux ellipses](./media/graphicsmm-geodraw.jpg "graphicsmm_geodraw")  
GeometryDrawing  
  
 [!code-csharp[DrawingMiscSnippets_snip#GeometryDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/GeometryDrawingExample.cs#geometrydrawingexampleinline)]
 [!code-xaml[DrawingMiscSnippets_snip#GeometryDrawingExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/GeometryDrawingExample.xaml#geometrydrawingexampleinline)]  
  
 Vous trouverez l’exemple complet sur la page [Créer un GeometryDrawing](how-to-create-a-geometrydrawing.md).  
  
 <xref:System.Windows.Media.Geometry>D’autres classes, telles que <xref:System.Windows.Media.PathGeometry> vous permettent de créer des formes plus complexes en créant des courbes et des arcs. Pour plus d’informations sur <xref:System.Windows.Media.Geometry> les objets, consultez [vue d’ensemble](geometry-overview.md)de la géométrie.  
  
 Pour plus d’informations sur d’autres façons de dessiner des formes qui n’utilisent pas <xref:System.Windows.Media.Drawing> d’objets, consultez [vue d’ensemble des formes et dessins de base dans WPF](shapes-and-basic-drawing-in-wpf-overview.md).  
  
<a name="drawingimagessection"></a>
## <a name="draw-an-image"></a>Dessiner une image  
 Pour dessiner une image, vous utilisez un <xref:System.Windows.Media.ImageDrawing> . La <xref:System.Windows.Media.ImageDrawing> propriété d’un objet <xref:System.Windows.Media.ImageDrawing.ImageSource%2A> décrit l’image à dessiner, et sa <xref:System.Windows.Media.ImageDrawing.Rect%2A> propriété définit la région dans laquelle l’image est dessinée.  
  
 L’exemple suivant dessine une image dans un rectangle situé à (75,75), de 100 par 100 pixels. L’illustration suivante montre le <xref:System.Windows.Media.ImageDrawing> créé par l’exemple. Une bordure grise a été ajoutée pour montrer les limites de <xref:System.Windows.Media.ImageDrawing> .  
  
 ![ImageDrawing 100 par 100 dessiné à &#40;75,75&#41;](./media/graphicsmm-simple-imagedrawing-offset.png "graphicsmm_simple_imagedrawing_offset")  
ImageDrawing 100 par 100  
  
 [!code-csharp[DrawingMiscSnippets_snip#ImageDrawing100by100Inline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/ImageDrawingExample.cs#imagedrawing100by100inline)]
 [!code-xaml[DrawingMiscSnippets_snip#ImageDrawing100by100Inline](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/ImageDrawingExample.xaml#imagedrawing100by100inline)]  
  
 Pour plus d’informations sur les images, consultez la [Vue d’ensemble de la création d’images](imaging-overview.md).  
  
<a name="playmedia"></a>
## <a name="play-media-code-only"></a>Lire un média (code uniquement)  
  
> [!NOTE]
> Bien que vous puissiez déclarer un <xref:System.Windows.Media.VideoDrawing> dans [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] , vous pouvez uniquement charger et lire son contenu multimédia à l’aide de code. Pour lire une vidéo dans [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] , utilisez à la <xref:System.Windows.Controls.MediaElement> place.  
  
 Pour lire un fichier audio ou vidéo, utilisez un <xref:System.Windows.Media.VideoDrawing> et un <xref:System.Windows.Media.MediaPlayer> . Il y a deux façons de charger et de lire des médias. La première consiste à utiliser un <xref:System.Windows.Media.MediaPlayer> et un <xref:System.Windows.Media.VideoDrawing> par eux-mêmes, et la deuxième consiste à créer votre propre <xref:System.Windows.Media.MediaTimeline> à utiliser avec <xref:System.Windows.Media.MediaPlayer> et <xref:System.Windows.Media.VideoDrawing> .  
  
> [!NOTE]
> Lorsque vous distribuez un contenu multimédia avec votre application, vous ne pouvez pas utiliser de fichier multimédia comme ressource de projet, comme pour une image. Dans votre fichier projet, vous devez plutôt définir le type de média sur `Content` et définir `CopyToOutputDirectory` sur `PreserveNewest` ou `Always`.  
  
 Pour lire un média sans créer les vôtres <xref:System.Windows.Media.MediaTimeline> , effectuez les étapes suivantes.  
  
1. Créez un objet <xref:System.Windows.Media.MediaPlayer>.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline1)]  
  
2. Utilisez la <xref:System.Windows.Media.MediaPlayer.Open%2A> méthode pour charger le fichier multimédia.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline2](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline2)]  
  
3. Créez un <xref:System.Windows.Media.VideoDrawing>.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline3](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline3)]  
  
4. Spécifiez la taille et l’emplacement de dessin du média en définissant la <xref:System.Windows.Media.VideoDrawing.Rect%2A> propriété de <xref:System.Windows.Media.VideoDrawing> .  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline4](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline4)]  
  
5. Définissez la <xref:System.Windows.Media.VideoDrawing.Player%2A> propriété de <xref:System.Windows.Media.VideoDrawing> avec le <xref:System.Windows.Media.MediaPlayer> que vous avez créé.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline5](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline5)]  
  
6. Utilisez la <xref:System.Windows.Media.MediaPlayer.Play%2A> méthode du <xref:System.Windows.Media.MediaPlayer> pour démarrer la diffusion du média.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline6](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline6)]  
  
 L’exemple suivant utilise un <xref:System.Windows.Media.VideoDrawing> et un <xref:System.Windows.Media.MediaPlayer> pour lire un fichier vidéo une seule fois.  
  
 [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline)]  
  
 Pour obtenir un contrôle de minutage supplémentaire sur le média, utilisez un <xref:System.Windows.Media.MediaTimeline> avec les <xref:System.Windows.Media.MediaPlayer> <xref:System.Windows.Media.VideoDrawing> objets et. <xref:System.Windows.Media.MediaTimeline>Vous permet de spécifier si la vidéo doit se répéter. Pour utiliser un <xref:System.Windows.Media.MediaTimeline> avec un <xref:System.Windows.Media.VideoDrawing> , vous devez effectuer les étapes suivantes :  
  
1. Déclarez <xref:System.Windows.Media.MediaTimeline> et définissez ses comportements de minutage.  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline1)]  
  
2. Créez un <xref:System.Windows.Media.MediaClock> à partir de <xref:System.Windows.Media.MediaTimeline> .  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline2](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline2)]  
  
3. Créez un <xref:System.Windows.Media.MediaPlayer> et utilisez le <xref:System.Windows.Media.MediaClock> pour définir sa <xref:System.Windows.Media.MediaPlayer.Clock%2A> propriété.  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline3](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline3)]  
  
4. Créez un <xref:System.Windows.Media.VideoDrawing> et assignez <xref:System.Windows.Media.MediaPlayer> à la <xref:System.Windows.Media.VideoDrawing.Player%2A> propriété de <xref:System.Windows.Media.VideoDrawing> .  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline4](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline4)]  
  
 L’exemple suivant utilise un <xref:System.Windows.Media.MediaTimeline> avec un <xref:System.Windows.Media.MediaPlayer> et un <xref:System.Windows.Media.VideoDrawing> pour lire une vidéo à plusieurs reprises.  
  
 [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline)]  
  
 Notez que, lorsque vous utilisez un <xref:System.Windows.Media.MediaTimeline> , vous utilisez le interactif <xref:System.Windows.Media.Animation.ClockController> retourné à partir de la <xref:System.Windows.Media.Animation.Clock.Controller%2A> propriété de <xref:System.Windows.Media.MediaClock> pour contrôler la lecture du média au lieu des méthodes interactives de <xref:System.Windows.Media.MediaPlayer> .  
  
<a name="drawtext"></a>
## <a name="draw-text"></a>Dessiner du texte  
 Pour dessiner du texte, vous utilisez un <xref:System.Windows.Media.GlyphRunDrawing> et un <xref:System.Windows.Media.GlyphRun> . L’exemple suivant utilise un <xref:System.Windows.Media.GlyphRunDrawing> pour dessiner le texte « Hello World ».  
  
 [!code-csharp[DrawingMiscSnippets_snip#GlyphRunDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/GlyphRunDrawingExample.cs#glyphrundrawingexampleinline)]
 [!code-xaml[DrawingMiscSnippets_snip#GlyphRunDrawingExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/GlyphRunExample.xaml#glyphrundrawingexampleinline)]  
  
 Un <xref:System.Windows.Media.GlyphRun> est un objet de bas niveau destiné à être utilisé avec des scénarios de présentation et d’impression de documents de format fixe. Un moyen plus simple de dessiner du texte à l’écran consiste à utiliser un <xref:System.Windows.Controls.Label> ou un <xref:System.Windows.Controls.TextBlock> . Pour plus d’informations sur <xref:System.Windows.Media.GlyphRun> , consultez l' [Introduction à l’objet GlyphRun et vue d’ensemble des éléments Glyphs](../advanced/introduction-to-the-glyphrun-object-and-glyphs-element.md) .  
  
<a name="compositedrawingssection"></a>
## <a name="composite-drawings"></a>Dessins composites  
 Un <xref:System.Windows.Media.DrawingGroup> vous permet de combiner plusieurs dessins en un seul dessin composite. À l’aide d’un <xref:System.Windows.Media.DrawingGroup> , vous pouvez combiner des formes, des images et du texte en un seul <xref:System.Windows.Media.Drawing> objet.  
  
 L’exemple suivant utilise un <xref:System.Windows.Media.DrawingGroup> pour combiner deux <xref:System.Windows.Media.GeometryDrawing> objets et un <xref:System.Windows.Media.ImageDrawing> objet. Cet exemple produit la sortie suivante.  
  
 ![DrawingGroup avec plusieurs dessins](./media/graphicsmm-simple.jpg "graphicsmm_simple")  
Un dessin composite  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMSimpleDrawingGroupExample](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingGroupExample.cs#graphicsmmsimpledrawinggroupexample)]
 [!code-xaml[DrawingMiscSnippets_snip#GraphicsMMSimpleDrawingGroupExample](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingGroupExample.xaml#graphicsmmsimpledrawinggroupexample)]  
  
 Un <xref:System.Windows.Media.DrawingGroup> vous permet également d’appliquer des masques d’opacité, des transformations, des effets bitmap et d’autres opérations à son contenu. <xref:System.Windows.Media.DrawingGroup>les opérations sont appliquées dans l’ordre suivant : <xref:System.Windows.Media.DrawingGroup.OpacityMask%2A> , <xref:System.Windows.Media.DrawingGroup.Opacity%2A> , <xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A> , <xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A> ,, puis <xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A> <xref:System.Windows.Media.DrawingGroup.Transform%2A> .  
  
 L’illustration suivante montre l’ordre dans lequel les <xref:System.Windows.Media.DrawingGroup> opérations sont appliquées.  
  
 ![Ordre des opérations DrawingGroup](./media/graphcismm-drawinggroup-order.png "graphcismm_drawinggroup_order")  
Ordre des opérations DrawingGroup  
  
 Le tableau suivant décrit les propriétés que vous pouvez utiliser pour manipuler le <xref:System.Windows.Media.DrawingGroup> contenu d’un objet.  
  
|Propriété|Description|Illustration|  
|--------------|-----------------|------------------|  
|<xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>|Modifie l’opacité des parties sélectionnées du <xref:System.Windows.Media.DrawingGroup> contenu. Vous trouverez un exemple sur la page [Guide pratique : contrôler l’opacité d’un dessin](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms748242(v=vs.90)).|![DrawingGroup avec un masque d'opacité](./media/graphicsmm-opmask.png "graphicsmm_opmask")|  
|<xref:System.Windows.Media.DrawingGroup.Opacity%2A>|Modifie uniformément l’opacité du <xref:System.Windows.Media.DrawingGroup> contenu. Utilisez cette propriété pour rendre transparent <xref:System.Windows.Media.Drawing> ou partiellement transparent. Vous trouverez un exemple sur la page [Guide pratique : appliquer un masque d’opacité à un dessin](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms753195(v=vs.90)).|![DrawingGroups avec différents paramètres d'opacité](./media/graphicsmm-opacity.png "graphicsmm_opacity")|  
|<xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>|Applique un <xref:System.Windows.Media.Effects.BitmapEffect> au <xref:System.Windows.Media.DrawingGroup> contenu. Vous trouverez un exemple sur la page [Guide pratique : appliquer un BitmapEffect à un dessin](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms752341(v=vs.90)).|![DrawingGroup avec BlurBitmapEffect](./media/graphicsmm-bitmap.png "graphicsmm_bitmap")|  
|<xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>|Découpe le <xref:System.Windows.Media.DrawingGroup> contenu d’une région que vous décrivez à l’aide d’un <xref:System.Windows.Media.Geometry> . Vous trouverez un exemple sur la page [Guide pratique : détourer un dessin](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms743068(v=vs.90)) .|![DrawingGroup avec une zone de découpage définie](./media/graphicsmm-clipgeom.png "graphicsmm_clipgeom")|  
|<xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A>|Aligne des pixels indépendants des appareils sur les pixels de l’appareil selon les instructions spécifiées. Cette propriété est utile pour s’assurer que les graphismes très détaillés s’affichent nettement sur les écrans basse résolution. Vous trouverez un exemple sur la page [Guide pratique : appliquer un GuidelineSet à un dessin](how-to-apply-a-guidelineset-to-a-drawing.md).|![DrawingGroup avec et sans GuidelineSet](./media/graphicsmm-drawinggroup-guidelineset.png "graphicsmm_drawinggroup_guidelineset")|  
|<xref:System.Windows.Media.DrawingGroup.Transform%2A>|Transforme le <xref:System.Windows.Media.DrawingGroup> contenu. Vous trouverez un exemple sur la page [Guide pratique : appliquer un Transform à un dessin](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms742304(v=vs.90)).|![DrawingGroup pivoté](./media/graphicsmm-rotate.png "graphicsmm_rotate")|  
  
<a name="usingimagedrawing"></a>
## <a name="display-a-drawing-as-an-image"></a>Afficher un dessin comme image  
 Pour afficher un <xref:System.Windows.Media.Drawing> avec un <xref:System.Windows.Controls.Image> contrôle, utilisez un <xref:System.Windows.Media.DrawingImage> comme le <xref:System.Windows.Controls.Image> du contrôle <xref:System.Windows.Controls.Image.Source%2A> et définissez la <xref:System.Windows.Media.DrawingImage> propriété de l’objet <xref:System.Windows.Media.DrawingImage.Drawing%2A?displayProperty=nameWithType> sur le dessin que vous souhaitez afficher.  
  
 L’exemple suivant utilise un <xref:System.Windows.Media.DrawingImage> et un <xref:System.Windows.Controls.Image> contrôle pour afficher un <xref:System.Windows.Media.GeometryDrawing> . Cet exemple produit la sortie suivante.  
  
 ![GeometryDrawing de deux ellipses](./media/graphicsmm-geodraw.jpg "graphicsmm_geodraw")  
DrawingImage  
  
 [!code-csharp[DrawingMiscSnippets_snip#DrawingImageExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingImageExample.cs#drawingimageexamplewholepage)]
 [!code-xaml[DrawingMiscSnippets_snip#DrawingImageExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingImageExample.xaml#drawingimageexamplewholepage)]  
  
<a name="renderingwithdrawingbrushsection"></a>
## <a name="paint-an-object-with-a-drawing"></a>Peindre un objet avec un dessin  
 Un <xref:System.Windows.Media.DrawingBrush> est un type de pinceau qui peint une zone avec un objet Drawing. Vous pouvez l’utiliser pour peindre n’importe quel objet graphique avec un dessin. La <xref:System.Windows.Media.Drawing> propriété d’un <xref:System.Windows.Media.DrawingBrush> décrit son <xref:System.Windows.Media.DrawingBrush.Drawing%2A> . Pour restituer un <xref:System.Windows.Media.Drawing> avec un <xref:System.Windows.Media.DrawingBrush> , ajoutez-le au pinceau à l’aide de la propriété du pinceau <xref:System.Windows.Media.Drawing> et utilisez le pinceau pour peindre un objet graphique, tel qu’un contrôle ou un panneau.  
  
 Les exemples suivants utilisent un <xref:System.Windows.Media.DrawingBrush> pour peindre le <xref:System.Windows.Shapes.Shape.Fill%2A> d’un <xref:System.Windows.Shapes.Rectangle> avec un modèle créé à partir d’un <xref:System.Windows.Media.GeometryDrawing> . Cet exemple produit la sortie suivante.  
  
 ![DrawingBrush en mosaïque](./media/graphicsmm-drawingbrush-geometrydrawing.png "graphicsmm_drawingbrush_geometrydrawing")  
GeometryDrawing utilisé avec un DrawingBrush  
  
 [!code-csharp[DrawingMiscSnippets_snip#DrawingBrushExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingBrushExample.cs#drawingbrushexamplewholepage)]
 [!code-xaml[DrawingMiscSnippets_snip#DrawingBrushExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingBrushExample.xaml#drawingbrushexamplewholepage)]  
  
 La <xref:System.Windows.Media.DrawingBrush> classe fournit diverses options d’étirement et de mosaïque de son contenu. Pour plus d’informations sur <xref:System.Windows.Media.DrawingBrush> , consultez la vue d’ensemble [de la peinture avec des images, des dessins et des visuels](painting-with-images-drawings-and-visuals.md) .  
  
<a name="renderingwithvisualsection"></a>
## <a name="render-a-drawing-with-a-visual"></a>Afficher un dessin avec un objet visuel  
 Un <xref:System.Windows.Media.DrawingVisual> est un type d’objet visuel conçu pour restituer un dessin. Les développeurs qui souhaitent créer un environnement graphique hautement personnalisé peuvent travailler directement sur la couche visuelle, qui n’est pas décrite dans cette vue d’ensemble. Pour plus d’informations, consultez la vue d’ensemble [Utiliser des objets DrawingVisual](using-drawingvisual-objects.md).  
  
<a name="drawingcontextobjects"></a>
## <a name="drawingcontext-objects"></a>Objets DrawingContext  
 La <xref:System.Windows.Media.DrawingContext> classe vous permet de remplir un <xref:System.Windows.Media.Visual> ou un <xref:System.Windows.Media.Drawing> avec du contenu visuel. De nombreux objets graphiques de niveau inférieur utilisent un <xref:System.Windows.Media.DrawingContext> , car il décrit très efficacement le contenu graphique.  
  
 Bien que les <xref:System.Windows.Media.DrawingContext> méthodes de dessin ressemblent aux méthodes Draw du <xref:System.Drawing.Graphics?displayProperty=nameWithType> type, elles sont en fait très différentes. <xref:System.Windows.Media.DrawingContext>est utilisé avec un système graphique en mode de conservation, tandis que le <xref:System.Drawing.Graphics?displayProperty=nameWithType> type est utilisé avec un système graphique en mode immédiat. Lorsque vous utilisez les <xref:System.Windows.Media.DrawingContext> commandes de dessin d’un objet, vous stockez en fait un ensemble d’instructions de rendu (bien que le mécanisme de stockage exact dépende du type d’objet qui fournit le <xref:System.Windows.Media.DrawingContext> ) qui sera utilisé par la suite par le système graphique. vous ne dessinez pas sur l’écran en temps réel. Pour plus d’informations sur le fonctionnement du système graphique Windows Presentation Foundation (WPF), consultez [vue d’ensemble du rendu graphique de WPF](wpf-graphics-rendering-overview.md).  
  
 Vous n’instanciez jamais directement un <xref:System.Windows.Media.DrawingContext> ; vous pouvez toutefois acquérir un contexte de dessin à partir de certaines méthodes, telles que <xref:System.Windows.Media.DrawingGroup.Open%2A?displayProperty=nameWithType> et <xref:System.Windows.Media.DrawingVisual.RenderOpen%2A?displayProperty=nameWithType> .  
  
<a name="enumeratevisualcontents"></a>
## <a name="enumerate-the-contents-of-a-visual"></a>Énumérer le contenu d’un objet visuel  
 En plus de leurs autres utilisations, les <xref:System.Windows.Media.Drawing> objets fournissent également un modèle objet pour énumérer le contenu d’un <xref:System.Windows.Media.Visual> .  
  
 L’exemple suivant utilise la <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A> méthode pour récupérer la <xref:System.Windows.Media.DrawingGroup> valeur d’un <xref:System.Windows.Media.Visual> et l’énumérer.  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMRetrieveDrawings](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/EnumerateDrawingsExample.xaml.cs#graphicsmmretrievedrawings)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Media.Drawing>
- <xref:System.Windows.Media.DrawingGroup>
- [Graphisme 2D et acquisition d’images](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [Peinture avec des objets d'image, de dessin et visuels](painting-with-images-drawings-and-visuals.md)
- [Vue d'ensemble de Geometry](geometry-overview.md)
- [Vue d'ensemble des formes et dessins de base dans WPF](shapes-and-basic-drawing-in-wpf-overview.md)
- [Vue d'ensemble du rendu graphique de WPF](wpf-graphics-rendering-overview.md)
- [Vue d'ensemble des objets Freezable](../advanced/freezable-objects-overview.md)
- [Rubriques de procédures](drawings-how-to-topics.md)
