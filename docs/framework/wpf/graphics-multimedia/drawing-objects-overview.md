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
ms.openlocfilehash: 7a5d00eb2fb7c66e5e42d40893806e13717e1d2e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186537"
---
# <a name="drawing-objects-overview"></a>Vue d'ensemble des objets Drawing
Ce sujet <xref:System.Windows.Media.Drawing> introduit des objets et décrit comment les utiliser pour dessiner efficacement les formes, les bitmaps, le texte et les médias. Utilisez <xref:System.Windows.Media.Drawing> des objets lorsque vous créez <xref:System.Windows.Media.DrawingBrush>du <xref:System.Windows.Media.Visual> clip art, peignez avec un , ou utilisez des objets.  

<a name="whatisadrawingsection"></a>
## <a name="what-is-a-drawing-object"></a>Qu’est-ce qu’un objet Drawing ?  
 Un <xref:System.Windows.Media.Drawing> objet décrit le contenu visible, comme une forme, une bitmap, une vidéo ou une ligne de texte. Différents types de dessins décrivent différents types de contenus. La liste suivante répertorie les différents types d’objets Drawing.  
  
- <xref:System.Windows.Media.GeometryDrawing>Dessine une forme.  
  
- <xref:System.Windows.Media.ImageDrawing>Dessine une image.  
  
- <xref:System.Windows.Media.GlyphRunDrawing>Dessine du texte.  
  
- <xref:System.Windows.Media.VideoDrawing>- Lecture d’un fichier audio ou vidéo.  
  
- <xref:System.Windows.Media.DrawingGroup>Dessine d’autres dessins. Utilisez un groupe de dessins pour faire de plusieurs dessins un seul et même dessin composite.  
  
 <xref:System.Windows.Media.Drawing>les objets sont polyvalents; il existe de nombreuses <xref:System.Windows.Media.Drawing> façons d’utiliser un objet.  
  
- Vous pouvez l’afficher comme <xref:System.Windows.Media.DrawingImage> une <xref:System.Windows.Controls.Image> image en utilisant un contrôle et un contrôle.  
  
- Vous pouvez l’utiliser avec un <xref:System.Windows.Media.DrawingBrush> pour <xref:System.Windows.Controls.Page.Background%2A> peindre <xref:System.Windows.Controls.Page>un objet, comme le d’un .  
  
- Vous pouvez l’utiliser pour <xref:System.Windows.Media.DrawingVisual>décrire l’apparence d’un .  
  
- Vous pouvez l’utiliser pour énumérer <xref:System.Windows.Media.Visual>le contenu d’un .  
  
 WPF fournit d’autres types d’objets qui sont capables de dessiner des formes, des images bitmaps, du texte et des médias. Par exemple, vous <xref:System.Windows.Shapes.Shape> pouvez également utiliser des <xref:System.Windows.Controls.MediaElement> objets pour dessiner des formes, et le contrôle fournit une autre façon d’ajouter de la vidéo à votre application. Alors, quand <xref:System.Windows.Media.Drawing> devriez-vous utiliser des objets? Lorsque vous pouvez sacrifier des fonctionnalités de <xref:System.Windows.Freezable> niveau cadre pour obtenir des avantages de performance ou lorsque vous avez besoin de fonctionnalités. Parce <xref:System.Windows.Media.Drawing> que les objets manquent de soutien pour [la mise en page,](../advanced/layout.md)l’entrée et la mise <xref:System.Windows.Media.Visual> au point, ils fournissent des avantages de performance qui les rendent idéales pour décrire les arrière-plans, clip art, et pour le dessin de bas niveau avec des objets.  
  
 Parce qu’ils <xref:System.Windows.Freezable> sont <xref:System.Windows.Media.Drawing> un objet de type, les objets gagnent plusieurs caractéristiques spéciales, qui comprennent ce qui suit: ils peuvent être déclarés comme [des ressources](../../../desktop-wpf/fundamentals/xaml-resources-define.md), partagés entre plusieurs objets, faits lecture-seulement pour améliorer les performances, cloné, et fait thread-safe. Pour plus d’informations sur <xref:System.Windows.Freezable> les différentes fonctionnalités fournies par les objets, voir le [Aperçu des objets freezable](../advanced/freezable-objects-overview.md).  
  
<a name="drawinggeometriessection"></a>
## <a name="draw-a-shape"></a>Dessiner une forme  
 Pour dessiner une forme, <xref:System.Windows.Media.GeometryDrawing>vous utilisez un . La propriété d’un <xref:System.Windows.Media.GeometryDrawing.Geometry%2A> dessin de géométrie décrit <xref:System.Windows.Media.GeometryDrawing.Brush%2A> la forme à dessiner, sa propriété décrit <xref:System.Windows.Media.GeometryDrawing.Pen%2A> comment l’intérieur de la forme doit être peint, et sa propriété décrit comment son contour doit être dessiné.  
  
 L’exemple suivant <xref:System.Windows.Media.GeometryDrawing> utilise un pour dessiner une forme. La forme est <xref:System.Windows.Media.GeometryGroup> décrite <xref:System.Windows.Media.EllipseGeometry> par un et deux objets. L’intérieur de la forme <xref:System.Windows.Media.LinearGradientBrush> est peint avec <xref:System.Windows.Media.Brushes.Black%2A> <xref:System.Windows.Media.Pen>un et son contour est dessiné avec un .  
  
 Cet exemple crée <xref:System.Windows.Media.GeometryDrawing>ce qui suit .  
  
 ![GeometryDrawing de deux ellipses](./media/graphicsmm-geodraw.jpg "graphicsmm_geodraw")  
GeometryDrawing  
  
 [!code-csharp[DrawingMiscSnippets_snip#GeometryDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/GeometryDrawingExample.cs#geometrydrawingexampleinline)]
 [!code-xaml[DrawingMiscSnippets_snip#GeometryDrawingExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/GeometryDrawingExample.xaml#geometrydrawingexampleinline)]  
  
 Vous trouverez l’exemple complet sur la page [Créer un GeometryDrawing](how-to-create-a-geometrydrawing.md).  
  
 D’autres <xref:System.Windows.Media.Geometry> classes, telles que <xref:System.Windows.Media.PathGeometry> vous permettent de créer des formes plus complexes en créant des courbes et des arcs. Pour plus <xref:System.Windows.Media.Geometry> d’informations sur les objets, voir la [vue d’ensemble de](geometry-overview.md)géométrie .  
  
 Pour plus d’informations sur d’autres <xref:System.Windows.Media.Drawing> façons de dessiner des formes qui n’utilisent pas d’objets, voir [Formes et dessin de base dans WPF Aperçu](shapes-and-basic-drawing-in-wpf-overview.md).  
  
<a name="drawingimagessection"></a>
## <a name="draw-an-image"></a>Dessiner une image  
 Pour dessiner une image, <xref:System.Windows.Media.ImageDrawing>vous utilisez un . La <xref:System.Windows.Media.ImageDrawing> propriété <xref:System.Windows.Media.ImageDrawing.ImageSource%2A> d’un objet décrit l’image à dessiner, et sa <xref:System.Windows.Media.ImageDrawing.Rect%2A> propriété définit la région où l’image est dessinée.  
  
 L’exemple suivant dessine une image dans un rectangle situé à (75,75), de 100 par 100 pixels. L’illustration suivante <xref:System.Windows.Media.ImageDrawing> montre la création par l’exemple. Une bordure grise a été ajoutée <xref:System.Windows.Media.ImageDrawing>pour montrer les limites de la .  
  
 ![ImageDrawing 100 par 100 dessiné à &#40;75,75&#41;](./media/graphicsmm-simple-imagedrawing-offset.png "graphicsmm_simple_imagedrawing_offset")  
ImageDrawing 100 par 100  
  
 [!code-csharp[DrawingMiscSnippets_snip#ImageDrawing100by100Inline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/ImageDrawingExample.cs#imagedrawing100by100inline)]
 [!code-xaml[DrawingMiscSnippets_snip#ImageDrawing100by100Inline](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/ImageDrawingExample.xaml#imagedrawing100by100inline)]  
  
 Pour plus d’informations sur les images, consultez la [Vue d’ensemble de la création d’images](imaging-overview.md).  
  
<a name="playmedia"></a>
## <a name="play-media-code-only"></a>Lire un média (code uniquement)  
  
> [!NOTE]
> Bien que vous <xref:System.Windows.Media.VideoDrawing> [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]puissiez déclarer un in, vous ne pouvez charger et lire ses médias en utilisant le code. Pour lire [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]la vidéo, utilisez un <xref:System.Windows.Controls.MediaElement> à la place.  
  
 Pour lire un fichier audio ou <xref:System.Windows.Media.VideoDrawing> vidéo, vous utilisez un et un <xref:System.Windows.Media.MediaPlayer>. Il y a deux façons de charger et de lire des médias. La première est <xref:System.Windows.Media.MediaPlayer> d’utiliser a et <xref:System.Windows.Media.VideoDrawing> un par eux-mêmes, et la deuxième façon est de créer votre propre <xref:System.Windows.Media.MediaTimeline> à utiliser avec <xref:System.Windows.Media.MediaPlayer> et <xref:System.Windows.Media.VideoDrawing>.  
  
> [!NOTE]
> Lorsque vous distribuez un contenu multimédia avec votre application, vous ne pouvez pas utiliser de fichier multimédia comme ressource de projet, comme pour une image. Dans votre fichier projet, vous devez plutôt définir le type de média sur `Content` et définir `CopyToOutputDirectory` sur `PreserveNewest` ou `Always`.  
  
 Pour jouer aux médias <xref:System.Windows.Media.MediaTimeline>sans créer le vôtre, vous effectuez les étapes suivantes.  
  
1. Créez un objet <xref:System.Windows.Media.MediaPlayer>.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline1)]  
  
2. Utilisez <xref:System.Windows.Media.MediaPlayer.Open%2A> la méthode pour charger le fichier multimédia.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline2](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline2)]  
  
3. Créez un <xref:System.Windows.Media.VideoDrawing>.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline3](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline3)]  
  
4. Spécifier la taille et l’emplacement pour dessiner les médias en fixant la <xref:System.Windows.Media.VideoDrawing.Rect%2A> propriété de la <xref:System.Windows.Media.VideoDrawing>.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline4](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline4)]  
  
5. Définissez <xref:System.Windows.Media.VideoDrawing.Player%2A> la <xref:System.Windows.Media.VideoDrawing> propriété <xref:System.Windows.Media.MediaPlayer> de la avec le vous avez créé.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline5](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline5)]  
  
6. Utilisez <xref:System.Windows.Media.MediaPlayer.Play%2A> la méthode <xref:System.Windows.Media.MediaPlayer> de la pour commencer à jouer les médias.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline6](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline6)]  
  
 L’exemple suivant <xref:System.Windows.Media.VideoDrawing> utilise <xref:System.Windows.Media.MediaPlayer> un et un pour lire un fichier vidéo une fois.  
  
 [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline)]  
  
 Pour obtenir un contrôle de synchronisation <xref:System.Windows.Media.MediaTimeline> supplémentaire <xref:System.Windows.Media.MediaPlayer> <xref:System.Windows.Media.VideoDrawing> sur les médias, utilisez un avec le et les objets. La <xref:System.Windows.Media.MediaTimeline> vidéo vous permet de spécifier si la vidéo doit se répéter. Pour utiliser <xref:System.Windows.Media.MediaTimeline> un <xref:System.Windows.Media.VideoDrawing>avec un , vous effectuez les étapes suivantes:  
  
1. Déclarez <xref:System.Windows.Media.MediaTimeline> le et définissez ses comportements de synchronisation.  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline1)]  
  
2. Créer <xref:System.Windows.Media.MediaClock> un <xref:System.Windows.Media.MediaTimeline>à partir de la .  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline2](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline2)]  
  
3. Créez <xref:System.Windows.Media.MediaPlayer> un et <xref:System.Windows.Media.MediaClock> utilisez <xref:System.Windows.Media.MediaPlayer.Clock%2A> le pour définir sa propriété.  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline3](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline3)]  
  
4. Créer <xref:System.Windows.Media.VideoDrawing> un et <xref:System.Windows.Media.MediaPlayer> attribuer <xref:System.Windows.Media.VideoDrawing.Player%2A> la <xref:System.Windows.Media.VideoDrawing>propriété de la .  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline4](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline4)]  
  
 L’exemple suivant <xref:System.Windows.Media.MediaTimeline> utilise <xref:System.Windows.Media.MediaPlayer> un <xref:System.Windows.Media.VideoDrawing> avec un et un pour lire une vidéo à plusieurs reprises.  
  
 [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline)]  
  
 Notez que, lorsque <xref:System.Windows.Media.MediaTimeline>vous utilisez <xref:System.Windows.Media.Animation.ClockController> un , <xref:System.Windows.Media.Animation.Clock.Controller%2A> vous <xref:System.Windows.Media.MediaClock> utilisez l’interactif retourné de la <xref:System.Windows.Media.MediaPlayer>propriété de la pour contrôler la lecture des médias au lieu des méthodes interactives de .  
  
<a name="drawtext"></a>
## <a name="draw-text"></a>Dessiner du texte  
 Pour dessiner du texte, vous utilisez un <xref:System.Windows.Media.GlyphRunDrawing> et un <xref:System.Windows.Media.GlyphRun>. L’exemple suivant <xref:System.Windows.Media.GlyphRunDrawing> utilise un pour dessiner le texte "Bonjour monde".  
  
 [!code-csharp[DrawingMiscSnippets_snip#GlyphRunDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/GlyphRunDrawingExample.cs#glyphrundrawingexampleinline)]
 [!code-xaml[DrawingMiscSnippets_snip#GlyphRunDrawingExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/GlyphRunExample.xaml#glyphrundrawingexampleinline)]  
  
 A <xref:System.Windows.Media.GlyphRun> est un objet de bas niveau destiné à être utilisé avec des scénarios de présentation de documents et d’impression à format fixe. Une façon plus simple de dessiner du <xref:System.Windows.Controls.Label> texte <xref:System.Windows.Controls.TextBlock>à l’écran est d’utiliser un ou un . Pour plus <xref:System.Windows.Media.GlyphRun>d’informations sur , voir [l’introduction à l’objet GlyphRun et Glyphs Element](../advanced/introduction-to-the-glyphrun-object-and-glyphs-element.md) aperçu.  
  
<a name="compositedrawingssection"></a>
## <a name="composite-drawings"></a>Dessins composites  
 A <xref:System.Windows.Media.DrawingGroup> vous permet de combiner plusieurs dessins en un seul dessin composite. En utilisant <xref:System.Windows.Media.DrawingGroup>un , vous pouvez combiner les <xref:System.Windows.Media.Drawing> formes, les images et le texte en un seul objet.  
  
 L’exemple suivant <xref:System.Windows.Media.DrawingGroup> utilise <xref:System.Windows.Media.GeometryDrawing> un pour <xref:System.Windows.Media.ImageDrawing> combiner deux objets et un objet. Cet exemple produit la sortie suivante.  
  
 ![DrawingGroup avec plusieurs dessins](./media/graphicsmm-simple.jpg "graphicsmm_simple")  
Un dessin composite  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMSimpleDrawingGroupExample](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingGroupExample.cs#graphicsmmsimpledrawinggroupexample)]
 [!code-xaml[DrawingMiscSnippets_snip#GraphicsMMSimpleDrawingGroupExample](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingGroupExample.xaml#graphicsmmsimpledrawinggroupexample)]  
  
 A <xref:System.Windows.Media.DrawingGroup> vous permet également d’appliquer des masques d’opacité, des transformations, des effets de bitmap et d’autres opérations à son contenu. <xref:System.Windows.Media.DrawingGroup>les opérations sont appliquées <xref:System.Windows.Media.DrawingGroup.OpacityMask%2A> <xref:System.Windows.Media.DrawingGroup.Opacity%2A>dans <xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A> <xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>l’ordre suivant: , , , , <xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A>, et puis <xref:System.Windows.Media.DrawingGroup.Transform%2A>.  
  
 L’illustration suivante montre <xref:System.Windows.Media.DrawingGroup> l’ordre dans lequel les opérations sont appliquées.  
  
 ![Ordre des opérations DrawingGroup](./media/graphcismm-drawinggroup-order.png "graphcismm_drawinggroup_order")  
Ordre des opérations DrawingGroup  
  
 Le tableau suivant décrit les propriétés <xref:System.Windows.Media.DrawingGroup> que vous pouvez utiliser pour manipuler le contenu d’un objet.  
  
|Propriété|Description|Illustration|  
|--------------|-----------------|------------------|  
|<xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>|Modifie l’opacité de certaines <xref:System.Windows.Media.DrawingGroup> parties du contenu. Vous trouverez un exemple sur la page [Guide pratique : contrôler l’opacité d’un dessin](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms748242(v=vs.90)).|![DrawingGroup avec un masque d'opacité](./media/graphicsmm-opmask.png "graphicsmm_opmask")|  
|<xref:System.Windows.Media.DrawingGroup.Opacity%2A>|Modifie uniformément l’opacité <xref:System.Windows.Media.DrawingGroup> du contenu. Utilisez cette propriété <xref:System.Windows.Media.Drawing> pour rendre transparente ou partiellement transparente. Vous trouverez un exemple sur la page [Guide pratique : appliquer un masque d’opacité à un dessin](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms753195(v=vs.90)).|![DrawingGroups avec différents paramètres d'opacité](./media/graphicsmm-opacity.png "graphicsmm_opacity")|  
|<xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>|Applique <xref:System.Windows.Media.Effects.BitmapEffect> un <xref:System.Windows.Media.DrawingGroup> sur le contenu. Vous trouverez un exemple sur la page [Guide pratique : appliquer un BitmapEffect à un dessin](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms752341(v=vs.90)).|![DrawingGroup avec BlurBitmapEffect](./media/graphicsmm-bitmap.png "graphicsmm_bitmap")|  
|<xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>|Clips <xref:System.Windows.Media.DrawingGroup> le contenu à une <xref:System.Windows.Media.Geometry>région que vous décrivez à l’aide d’un . Vous trouverez un exemple sur la page [Guide pratique : détourer un dessin](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms743068(v=vs.90)) .|![DrawingGroup avec une zone de découpage définie](./media/graphicsmm-clipgeom.png "graphicsmm_clipgeom")|  
|<xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A>|Aligne des pixels indépendants des appareils sur les pixels de l’appareil selon les instructions spécifiées. Cette propriété est utile pour s’assurer que les graphismes très détaillés s’affichent nettement sur les écrans basse résolution. Vous trouverez un exemple sur la page [Guide pratique : appliquer un GuidelineSet à un dessin](how-to-apply-a-guidelineset-to-a-drawing.md).|![DrawingGroup avec et sans GuidelineSet](./media/graphicsmm-drawinggroup-guidelineset.png "graphicsmm_drawinggroup_guidelineset")|  
|<xref:System.Windows.Media.DrawingGroup.Transform%2A>|Transforme le <xref:System.Windows.Media.DrawingGroup> contenu. Vous trouverez un exemple sur la page [Guide pratique : appliquer un Transform à un dessin](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms742304(v=vs.90)).|![DrawingGroup pivoté](./media/graphicsmm-rotate.png "graphicsmm_rotate")|  
  
<a name="usingimagedrawing"></a>
## <a name="display-a-drawing-as-an-image"></a>Afficher un dessin comme image  
 Pour afficher <xref:System.Windows.Media.Drawing> un <xref:System.Windows.Controls.Image> avec un <xref:System.Windows.Media.DrawingImage> contrôle, utilisez un comme <xref:System.Windows.Controls.Image> le contrôle <xref:System.Windows.Controls.Image.Source%2A> et définissez la propriété de <xref:System.Windows.Media.DrawingImage> <xref:System.Windows.Media.DrawingImage.Drawing%2A?displayProperty=nameWithType> l’objet au dessin que vous souhaitez afficher.  
  
 L’exemple suivant <xref:System.Windows.Media.DrawingImage> utilise <xref:System.Windows.Controls.Image> un et <xref:System.Windows.Media.GeometryDrawing>un contrôle pour afficher un . Cet exemple produit la sortie suivante.  
  
 ![GeometryDrawing de deux ellipses](./media/graphicsmm-geodraw.jpg "graphicsmm_geodraw")  
DrawingImage  
  
 [!code-csharp[DrawingMiscSnippets_snip#DrawingImageExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingImageExample.cs#drawingimageexamplewholepage)]
 [!code-xaml[DrawingMiscSnippets_snip#DrawingImageExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingImageExample.xaml#drawingimageexamplewholepage)]  
  
<a name="renderingwithdrawingbrushsection"></a>
## <a name="paint-an-object-with-a-drawing"></a>Peindre un objet avec un dessin  
 A <xref:System.Windows.Media.DrawingBrush> est un type de pinceau qui peint une zone avec un objet de dessin. Vous pouvez l’utiliser pour peindre n’importe quel objet graphique avec un dessin. La <xref:System.Windows.Media.Drawing> propriété <xref:System.Windows.Media.DrawingBrush> d’un <xref:System.Windows.Media.DrawingBrush.Drawing%2A>décrit son . Pour rendre <xref:System.Windows.Media.Drawing> un <xref:System.Windows.Media.DrawingBrush>avec un , l’ajouter <xref:System.Windows.Media.Drawing> à la brosse à l’aide de la propriété de la brosse et utiliser le pinceau pour peindre un objet graphique, comme un contrôle ou un panneau.  
  
 Les exemples <xref:System.Windows.Media.DrawingBrush> suivants utilise <xref:System.Windows.Shapes.Shape.Fill%2A> un <xref:System.Windows.Shapes.Rectangle> pour peindre le <xref:System.Windows.Media.GeometryDrawing>d’un avec un motif créé à partir d’un . Cet exemple produit la sortie suivante.  
  
 ![DrawingBrush en mosaïque](./media/graphicsmm-drawingbrush-geometrydrawing.png "graphicsmm_drawingbrush_geometrydrawing")  
GeometryDrawing utilisé avec un DrawingBrush  
  
 [!code-csharp[DrawingMiscSnippets_snip#DrawingBrushExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingBrushExample.cs#drawingbrushexamplewholepage)]
 [!code-xaml[DrawingMiscSnippets_snip#DrawingBrushExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingBrushExample.xaml#drawingbrushexamplewholepage)]  
  
 La <xref:System.Windows.Media.DrawingBrush> classe offre une variété d’options pour étirer et carreler son contenu. Pour plus <xref:System.Windows.Media.DrawingBrush>d’informations sur , voir la [peinture avec des images, des dessins et des visuels](painting-with-images-drawings-and-visuals.md) aperçu.  
  
<a name="renderingwithvisualsection"></a>
## <a name="render-a-drawing-with-a-visual"></a>Afficher un dessin avec un objet visuel  
 A <xref:System.Windows.Media.DrawingVisual> est un type d’objet visuel conçu pour rendre un dessin. Les développeurs qui souhaitent créer un environnement graphique hautement personnalisé peuvent travailler directement sur la couche visuelle, qui n’est pas décrite dans cette vue d’ensemble. Pour plus d’informations, consultez la vue d’ensemble [Utiliser des objets DrawingVisual](using-drawingvisual-objects.md).  
  
<a name="drawingcontextobjects"></a>
## <a name="drawingcontext-objects"></a>Objets DrawingContext  
 La <xref:System.Windows.Media.DrawingContext> classe vous permet <xref:System.Windows.Media.Visual> de <xref:System.Windows.Media.Drawing> remplir un ou un avec un contenu visuel. Beaucoup de ces objets graphiques <xref:System.Windows.Media.DrawingContext> de niveau inférieur utilisent un parce qu’il décrit le contenu graphique très efficacement.  
  
 Bien <xref:System.Windows.Media.DrawingContext> que les méthodes de tirage <xref:System.Drawing.Graphics?displayProperty=nameWithType> semblent similaires aux méthodes de tirage du type, ils sont en fait très différents. <xref:System.Windows.Media.DrawingContext>est utilisé avec un système graphique <xref:System.Drawing.Graphics?displayProperty=nameWithType> de mode conservé, tandis que le type est utilisé avec un système graphique en mode immédiat. Lorsque vous <xref:System.Windows.Media.DrawingContext> utilisez les commandes de tirage d’un objet, vous stockez en fait un ensemble d’instructions de rendu (bien que le mécanisme de stockage exact dépend du type d’objet qui fournit le <xref:System.Windows.Media.DrawingContext>) qui sera plus tard utilisé par le système graphique; vous ne dessinez pas à l’écran en temps réel. Pour plus d’informations sur le fonctionnement du système graphique de la Windows Presentation Foundation (WPF), consultez le [WPF Graphics Rendering Overview](wpf-graphics-rendering-overview.md).  
  
 Vous n’avez jamais <xref:System.Windows.Media.DrawingContext>directement instantané un ; vous pouvez, cependant, acquérir un contexte de <xref:System.Windows.Media.DrawingGroup.Open%2A?displayProperty=nameWithType> <xref:System.Windows.Media.DrawingVisual.RenderOpen%2A?displayProperty=nameWithType>dessin à partir de certaines méthodes, telles que et .  
  
<a name="enumeratevisualcontents"></a>
## <a name="enumerate-the-contents-of-a-visual"></a>Énumérer le contenu d’un objet visuel  
 En plus de leurs <xref:System.Windows.Media.Drawing> autres utilisations, les objets fournissent également <xref:System.Windows.Media.Visual>un modèle d’objet pour énumérer le contenu d’un .  
  
 L’exemple suivant <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A> utilise la <xref:System.Windows.Media.DrawingGroup> méthode <xref:System.Windows.Media.Visual> pour récupérer la valeur d’un et l’énumérer.  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMRetrieveDrawings](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/EnumerateDrawingsExample.xaml.cs#graphicsmmretrievedrawings)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Media.Drawing>
- <xref:System.Windows.Media.DrawingGroup>
- [Graphisme 2D et acquisition d’images](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [Peinture avec des images, des dessins et des objets visuels](painting-with-images-drawings-and-visuals.md)
- [Vue d’ensemble de Geometry](geometry-overview.md)
- [Vue d’ensemble des formes et dessins de base dans WPF](shapes-and-basic-drawing-in-wpf-overview.md)
- [Vue d’ensemble du rendu graphique de WPF](wpf-graphics-rendering-overview.md)
- [Vue d’ensemble des objets Freezable](../advanced/freezable-objects-overview.md)
- [Sujets comment se passer](drawings-how-to-topics.md)
