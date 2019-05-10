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
ms.openlocfilehash: b09fed48912a9175ff34d5be4f783bdb06abf936
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64615424"
---
# <a name="drawing-objects-overview"></a>Vue d'ensemble des objets Drawing
Cette rubrique présente <xref:System.Windows.Media.Drawing> objets et explique comment les utiliser pour dessiner efficacement des formes, bitmaps, texte et média. Utilisez <xref:System.Windows.Media.Drawing> objets lorsque vous créez des images clipart, dessinez avec un <xref:System.Windows.Media.DrawingBrush>, ou utilisez <xref:System.Windows.Media.Visual> objets.  

<a name="whatisadrawingsection"></a>   
## <a name="what-is-a-drawing-object"></a>Qu’est-ce qu’un objet Drawing ?  
 Un <xref:System.Windows.Media.Drawing> objet décrit du contenu visible, comme une forme, bitmap, vidéo ou une ligne de texte. Différents types de dessins décrivent différents types de contenus. La liste suivante répertorie les différents types d’objets Drawing.  
  
- <xref:System.Windows.Media.GeometryDrawing> – Dessine une forme.  
  
- <xref:System.Windows.Media.ImageDrawing> – Dessine une image.  
  
- <xref:System.Windows.Media.GlyphRunDrawing> – Dessine du texte.  
  
- <xref:System.Windows.Media.VideoDrawing> – Lit un fichier audio ou vidéo.  
  
- <xref:System.Windows.Media.DrawingGroup> – Dessine d’autres dessins. Utilisez un groupe de dessins pour faire de plusieurs dessins un seul et même dessin composite.  
  
 <xref:System.Windows.Media.Drawing> les objets sont polyvalents. Il existe plusieurs façons, vous pouvez utiliser un <xref:System.Windows.Media.Drawing> objet.  
  
- Vous pouvez l’afficher en tant qu’image en utilisant un <xref:System.Windows.Media.DrawingImage> et un <xref:System.Windows.Controls.Image> contrôle.  
  
- Vous pouvez l’utiliser avec un <xref:System.Windows.Media.DrawingBrush> pour peindre un objet, tel que le <xref:System.Windows.Controls.Page.Background%2A> d’un <xref:System.Windows.Controls.Page>.  
  
- Vous pouvez l’utiliser pour décrire l’apparence d’un <xref:System.Windows.Media.DrawingVisual>.  
  
- Vous pouvez l’utiliser pour énumérer le contenu d’un <xref:System.Windows.Media.Visual>.  
  
 WPF fournit d’autres types d’objets qui sont capables de dessiner des formes, des images bitmaps, du texte et des médias. Par exemple, vous pouvez également utiliser <xref:System.Windows.Shapes.Shape> pour dessiner des formes, les objets et les <xref:System.Windows.Controls.MediaElement> contrôle fournit une autre façon d’ajouter une vidéo à votre application. Par conséquent, quand faut-il utiliser <xref:System.Windows.Media.Drawing> objets ? Lorsque vous pouvez sacrifier des fonctionnalités au niveau du framework pour optimiser les performances ou lorsque vous devez <xref:System.Windows.Freezable> fonctionnalités. Étant donné que <xref:System.Windows.Media.Drawing> objets ne prennent pas [disposition](../advanced/layout.md), d’entrée et le focus, ils fournissent de meilleures performances idéales pour décrire les arrière-plans et images clipart et pour le dessin de bas niveau avec <xref:System.Windows.Media.Visual> objets.  
  
 Étant un type <xref:System.Windows.Freezable> objet, <xref:System.Windows.Media.Drawing> objets disposent de plusieurs fonctionnalités spéciales qui sont les suivantes : elles peuvent être déclarées comme [ressources](../advanced/xaml-resources.md), partagés entre plusieurs objets, définis en lecture seule pour améliorer performances, clonés et rendus thread-safe. Pour plus d’informations sur les différentes fonctionnalités fournies par <xref:System.Windows.Freezable> , voir la [vue d’ensemble des objets Freezable](../advanced/freezable-objects-overview.md).  
  
<a name="drawinggeometriessection"></a>   
## <a name="draw-a-shape"></a>Dessiner une forme  
 Pour dessiner une forme, vous utilisez un <xref:System.Windows.Media.GeometryDrawing>. Un dessin géométrique <xref:System.Windows.Media.GeometryDrawing.Geometry%2A> propriété décrit la forme à dessiner, sa <xref:System.Windows.Media.GeometryDrawing.Brush%2A> propriété décrit comment peindre l’intérieur de la forme et son <xref:System.Windows.Media.GeometryDrawing.Pen%2A> propriété décrit comment dessiner son contour.  
  
 L’exemple suivant utilise un <xref:System.Windows.Media.GeometryDrawing> pour dessiner une forme. La forme est décrite par un <xref:System.Windows.Media.GeometryGroup> et deux <xref:System.Windows.Media.EllipseGeometry> objets. Intérieur de la forme est peint avec un <xref:System.Windows.Media.LinearGradientBrush> et son contour est dessiné avec un <xref:System.Windows.Media.Brushes.Black%2A> <xref:System.Windows.Media.Pen>.  
  
 Cet exemple crée les éléments suivants <xref:System.Windows.Media.GeometryDrawing>.  
  
 ![GeometryDrawing de deux ellipses](./media/graphicsmm-geodraw.jpg "graphicsmm_geodraw")  
GeometryDrawing  
  
 [!code-csharp[DrawingMiscSnippets_snip#GeometryDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/GeometryDrawingExample.cs#geometrydrawingexampleinline)]
 [!code-xaml[DrawingMiscSnippets_snip#GeometryDrawingExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/GeometryDrawingExample.xaml#geometrydrawingexampleinline)]  
  
 Vous trouverez l’exemple complet sur la page [Créer un GeometryDrawing](how-to-create-a-geometrydrawing.md).  
  
 Autres <xref:System.Windows.Media.Geometry> classes, telles que <xref:System.Windows.Media.PathGeometry> vous permettent de créer des formes plus complexes en créant des courbes et des arcs. Pour plus d’informations sur <xref:System.Windows.Media.Geometry> , voir la [vue d’ensemble de Geometry](geometry-overview.md).  
  
 Pour plus d’informations sur les autres méthodes pour dessiner des formes qui n’utilisent pas <xref:System.Windows.Media.Drawing> , consultez [formes et dessins de base dans WPF Overview](shapes-and-basic-drawing-in-wpf-overview.md).  
  
<a name="drawingimagessection"></a>   
## <a name="draw-an-image"></a>Dessiner une image  
 Pour dessiner une image, vous utilisez un <xref:System.Windows.Media.ImageDrawing>. Un <xref:System.Windows.Media.ImageDrawing> l’objet <xref:System.Windows.Media.ImageDrawing.ImageSource%2A> propriété décrit l’image à dessiner et son <xref:System.Windows.Media.ImageDrawing.Rect%2A> propriété définit la région où l’image est dessinée.  
  
 L’exemple suivant dessine une image dans un rectangle situé à (75,75), de 100 par 100 pixels. L’illustration suivante montre le <xref:System.Windows.Media.ImageDrawing> créé par l’exemple. Une bordure grise a été ajoutée pour montrer les limites de la <xref:System.Windows.Media.ImageDrawing>.  
  
 ![Un ImageDrawing 100 par 100 dessiné à &#40;75,75&#41;](./media/graphicsmm-simple-imagedrawing-offset.png "graphicsmm_simple_imagedrawing_offset")  
ImageDrawing 100 par 100  
  
 [!code-csharp[DrawingMiscSnippets_snip#ImageDrawing100by100Inline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/ImageDrawingExample.cs#imagedrawing100by100inline)]
 [!code-xaml[DrawingMiscSnippets_snip#ImageDrawing100by100Inline](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/ImageDrawingExample.xaml#imagedrawing100by100inline)]  
  
 Pour plus d’informations sur les images, consultez la [Vue d’ensemble de la création d’images](imaging-overview.md).  
  
<a name="playmedia"></a>   
## <a name="play-media-code-only"></a>Lire un média (code uniquement)  
  
> [!NOTE]
>  Bien que vous puissiez déclarer un <xref:System.Windows.Media.VideoDrawing> dans [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], vous pouvez uniquement charger et lire son média à l’aide de code. Pour lire une vidéo dans [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], utilisez un <xref:System.Windows.Controls.MediaElement> à la place.  
  
 Pour lire un fichier audio ou vidéo, vous utilisez un <xref:System.Windows.Media.VideoDrawing> et un <xref:System.Windows.Media.MediaPlayer>. Il y a deux façons de charger et de lire des médias. La première consiste à utiliser un <xref:System.Windows.Media.MediaPlayer> et un <xref:System.Windows.Media.VideoDrawing> par eux-mêmes et la seconde méthode consiste à créer votre propre <xref:System.Windows.Media.MediaTimeline> à utiliser avec le <xref:System.Windows.Media.MediaPlayer> et <xref:System.Windows.Media.VideoDrawing>.  
  
> [!NOTE]
>  Lorsque vous distribuez un contenu multimédia avec votre application, vous ne pouvez pas utiliser de fichier multimédia comme ressource de projet, comme pour une image. Dans votre fichier projet, vous devez plutôt définir le type de média sur `Content` et définir `CopyToOutputDirectory` sur `PreserveNewest` ou `Always`.  
  
 Pour lire un média sans créer votre propre <xref:System.Windows.Media.MediaTimeline>, vous procédez comme suit.  
  
1. Créez un objet <xref:System.Windows.Media.MediaPlayer>.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline1)]  
  
2. Utilisez le <xref:System.Windows.Media.MediaPlayer.Open%2A> méthode pour charger le fichier multimédia.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline2](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline2)]  
  
3. Créer un <xref:System.Windows.Media.VideoDrawing>.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline3](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline3)]  
  
4. Spécifiez la taille et l’emplacement où dessiner le média en définissant le <xref:System.Windows.Media.VideoDrawing.Rect%2A> propriété de la <xref:System.Windows.Media.VideoDrawing>.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline4](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline4)]  
  
5. Définir le <xref:System.Windows.Media.VideoDrawing.Player%2A> propriété de la <xref:System.Windows.Media.VideoDrawing> avec la <xref:System.Windows.Media.MediaPlayer> que vous avez créé.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline5](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline5)]  
  
6. Utilisez le <xref:System.Windows.Media.MediaPlayer.Play%2A> méthode de la <xref:System.Windows.Media.MediaPlayer> pour démarrer la lecture du média.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline6](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline6)]  
  
 L’exemple suivant utilise un <xref:System.Windows.Media.VideoDrawing> et un <xref:System.Windows.Media.MediaPlayer> pour lire un fichier vidéo une seule fois.  
  
 [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline)]  
  
 Pour optimiser le contrôle du minutage du média, utilisez un <xref:System.Windows.Media.MediaTimeline> avec la <xref:System.Windows.Media.MediaPlayer> et <xref:System.Windows.Media.VideoDrawing> objets. Le <xref:System.Windows.Media.MediaTimeline> vous permet de spécifier si la vidéo doit se répéter. Pour utiliser un <xref:System.Windows.Media.MediaTimeline> avec un <xref:System.Windows.Media.VideoDrawing>, vous procédez comme suit :  
  
1. Déclarez le <xref:System.Windows.Media.MediaTimeline> et définissez ses comportements de minutage.  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline1)]  
  
2. Créer un <xref:System.Windows.Media.MediaClock> à partir de la <xref:System.Windows.Media.MediaTimeline>.  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline2](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline2)]  
  
3. Créer un <xref:System.Windows.Media.MediaPlayer> et utiliser le <xref:System.Windows.Media.MediaClock> pour définir son <xref:System.Windows.Media.MediaPlayer.Clock%2A> propriété.  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline3](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline3)]  
  
4. Créer un <xref:System.Windows.Media.VideoDrawing> et affecter le <xref:System.Windows.Media.MediaPlayer> à la <xref:System.Windows.Media.VideoDrawing.Player%2A> propriété de la <xref:System.Windows.Media.VideoDrawing>.  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline4](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline4)]  
  
 L’exemple suivant utilise un <xref:System.Windows.Media.MediaTimeline> avec un <xref:System.Windows.Media.MediaPlayer> et un <xref:System.Windows.Media.VideoDrawing> pour lire une vidéo à plusieurs reprises.  
  
 [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline)]  
  
 Notez que, lorsque vous utilisez un <xref:System.Windows.Media.MediaTimeline>, vous utilisez la commande interactive <xref:System.Windows.Media.Animation.ClockController> retourné à partir de la <xref:System.Windows.Media.Animation.Clock.Controller%2A> propriété de la <xref:System.Windows.Media.MediaClock> pour contrôler la lecture média au lieu de méthodes interactives de <xref:System.Windows.Media.MediaPlayer>.  
  
<a name="drawtext"></a>   
## <a name="draw-text"></a>Dessiner du texte  
 Pour dessiner du texte, vous utilisez un <xref:System.Windows.Media.GlyphRunDrawing> et un <xref:System.Windows.Media.GlyphRun>. L’exemple suivant utilise un <xref:System.Windows.Media.GlyphRunDrawing> pour dessiner le texte « Hello World ».  
  
 [!code-csharp[DrawingMiscSnippets_snip#GlyphRunDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/GlyphRunDrawingExample.cs#glyphrundrawingexampleinline)]
 [!code-xaml[DrawingMiscSnippets_snip#GlyphRunDrawingExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/GlyphRunExample.xaml#glyphrundrawingexampleinline)]  
  
 Un <xref:System.Windows.Media.GlyphRun> est un objet de bas niveau prévu pour une utilisation avec la présentation de documents à format fixe et les scénarios d’impression. Dessiner du texte à l’écran le plus simple consiste à utiliser un <xref:System.Windows.Controls.Label> ou un <xref:System.Windows.Controls.TextBlock>. Pour plus d’informations sur <xref:System.Windows.Media.GlyphRun>, consultez le [Introduction à l’objet GlyphRun et l’élément Glyphs](../advanced/introduction-to-the-glyphrun-object-and-glyphs-element.md) vue d’ensemble.  
  
<a name="compositedrawingssection"></a>   
## <a name="composite-drawings"></a>Dessins composites  
 Un <xref:System.Windows.Media.DrawingGroup> vous permet de combiner plusieurs dessins en un seul dessin composite. En utilisant un <xref:System.Windows.Media.DrawingGroup>, vous pouvez combiner des formes, des images et du texte dans un seul <xref:System.Windows.Media.Drawing> objet.  
  
 L’exemple suivant utilise un <xref:System.Windows.Media.DrawingGroup> pour combiner deux <xref:System.Windows.Media.GeometryDrawing> objets et une <xref:System.Windows.Media.ImageDrawing> objet. Cet exemple produit la sortie suivante.  
  
 ![DrawingGroup avec plusieurs dessins](./media/graphicsmm-simple.jpg "graphicsmm_simple")  
Un dessin composite  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMSimpleDrawingGroupExample](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingGroupExample.cs#graphicsmmsimpledrawinggroupexample)]
 [!code-xaml[DrawingMiscSnippets_snip#GraphicsMMSimpleDrawingGroupExample](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingGroupExample.xaml#graphicsmmsimpledrawinggroupexample)]  
  
 Un <xref:System.Windows.Media.DrawingGroup> vous permet également d’appliquer des masques d’opacité, des transformations, des effets bitmap et d’autres opérations à son contenu. <xref:System.Windows.Media.DrawingGroup> les opérations sont appliquées dans l’ordre suivant : <xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>, <xref:System.Windows.Media.DrawingGroup.Opacity%2A>, <xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>, <xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>, <xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A>, puis <xref:System.Windows.Media.DrawingGroup.Transform%2A>.  
  
 L’illustration suivante montre l’ordre dans lequel <xref:System.Windows.Media.DrawingGroup> opérations sont appliquées.  
  
 ![Ordre des opérations DrawingGroup](./media/graphcismm-drawinggroup-order.png "graphcismm_drawinggroup_order")  
Ordre des opérations DrawingGroup  
  
 Le tableau suivant décrit les propriétés que vous pouvez utiliser pour manipuler un <xref:System.Windows.Media.DrawingGroup> contenu de l’objet.  
  
|Propriété|Description|Illustration|  
|--------------|-----------------|------------------|  
|<xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>|Modifie l’opacité de certaines parties de la <xref:System.Windows.Media.DrawingGroup> contenu. Pour voir un exemple, consultez [Comment : Contrôler l’opacité d’un dessin](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms748242(v=vs.90)).|![DrawingGroup avec un masque d’opacité](./media/graphicsmm-opmask.png "graphicsmm_opmask")|  
|<xref:System.Windows.Media.DrawingGroup.Opacity%2A>|Modifie uniformément l’opacité de le <xref:System.Windows.Media.DrawingGroup> contenu. Utilisez cette propriété pour rendre un <xref:System.Windows.Media.Drawing> transparents ou partiellement transparents. Pour voir un exemple, consultez [Comment : Appliquer un masque d’opacité à un dessin](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms753195(v=vs.90)).|![DrawingGroups avec différents paramètres d’opacité](./media/graphicsmm-opacity.png "graphicsmm_opacity")|  
|<xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>|Applique un <xref:System.Windows.Media.Effects.BitmapEffect> à la <xref:System.Windows.Media.DrawingGroup> contenu. Pour voir un exemple, consultez [Comment : Appliquer un BitmapEffect à un dessin](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms752341(v=vs.90)).|![DrawingGroup avec BlurBitmapEffect](./media/graphicsmm-bitmap.png "graphicsmm_bitmap")|  
|<xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>|Clips le <xref:System.Windows.Media.DrawingGroup> contenu dans une région de décrire à l’aide un <xref:System.Windows.Media.Geometry>. Pour voir un exemple, consultez [Comment : Détourer un dessin](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms743068(v=vs.90)) .|![DrawingGroup avec une zone de découpage définie](./media/graphicsmm-clipgeom.png "graphicsmm_clipgeom")|  
|<xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A>|Aligne des pixels indépendants des appareils sur les pixels de l’appareil selon les instructions spécifiées. Cette propriété est utile pour s’assurer que les graphismes très détaillés s’affichent nettement sur les écrans basse résolution. Vous trouverez un exemple sur la page [Guide pratique : appliquer un GuidelineSet à un dessin](how-to-apply-a-guidelineset-to-a-drawing.md).|![DrawingGroup avec et sans GuidelineSet](./media/graphicsmm-drawinggroup-guidelineset.png "graphicsmm_drawinggroup_guidelineset")|  
|<xref:System.Windows.Media.DrawingGroup.Transform%2A>|Transforme le <xref:System.Windows.Media.DrawingGroup> contenu. Pour voir un exemple, consultez [Comment : Appliquer une transformation à un dessin](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms742304(v=vs.90)).|![DrawingGroup avec rotation](./media/graphicsmm-rotate.png "graphicsmm_rotate")|  
  
<a name="usingimagedrawing"></a>   
## <a name="display-a-drawing-as-an-image"></a>Afficher un dessin comme image  
 Pour afficher un <xref:System.Windows.Media.Drawing> avec un <xref:System.Windows.Controls.Image> contrôler, utilisez un <xref:System.Windows.Media.DrawingImage> en tant que le <xref:System.Windows.Controls.Image> du contrôle <xref:System.Windows.Controls.Image.Source%2A> et définir le <xref:System.Windows.Media.DrawingImage> l’objet <xref:System.Windows.Media.DrawingImage.Drawing%2A?displayProperty=nameWithType> propriété sur le dessin que vous souhaitez afficher.  
  
 L’exemple suivant utilise un <xref:System.Windows.Media.DrawingImage> et un <xref:System.Windows.Controls.Image> contrôle pour afficher un <xref:System.Windows.Media.GeometryDrawing>. Cet exemple produit la sortie suivante.  
  
 ![GeometryDrawing de deux ellipses](./media/graphicsmm-geodraw.jpg "graphicsmm_geodraw")  
DrawingImage  
  
 [!code-csharp[DrawingMiscSnippets_snip#DrawingImageExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingImageExample.cs#drawingimageexamplewholepage)]
 [!code-xaml[DrawingMiscSnippets_snip#DrawingImageExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingImageExample.xaml#drawingimageexamplewholepage)]  
  
<a name="renderingwithdrawingbrushsection"></a>   
## <a name="paint-an-object-with-a-drawing"></a>Peindre un objet avec un dessin  
 Un <xref:System.Windows.Media.DrawingBrush> est un type de pinceau qui peint une zone avec un objet drawing. Vous pouvez l’utiliser pour peindre n’importe quel objet graphique avec un dessin. Le <xref:System.Windows.Media.Drawing> propriété d’un <xref:System.Windows.Media.DrawingBrush> décrit ses <xref:System.Windows.Media.DrawingBrush.Drawing%2A>. Pour restituer un <xref:System.Windows.Media.Drawing> avec un <xref:System.Windows.Media.DrawingBrush>, ajoutez-le au pinceau à l’aide du pinceau <xref:System.Windows.Media.Drawing> propriété et utilisez le pinceau pour peindre un graphique d’objet, tel qu’un contrôle ou du panneau.  
  
 Les exemples suivants utilisent une <xref:System.Windows.Media.DrawingBrush> pour peindre le <xref:System.Windows.Shapes.Shape.Fill%2A> d’un <xref:System.Windows.Shapes.Rectangle> avec un modèle créé à partir d’un <xref:System.Windows.Media.GeometryDrawing>. Cet exemple produit la sortie suivante.  
  
 ![DrawingBrush en mosaïque](./media/graphicsmm-drawingbrush-geometrydrawing.png "graphicsmm_drawingbrush_geometrydrawing")  
GeometryDrawing utilisé avec un DrawingBrush  
  
 [!code-csharp[DrawingMiscSnippets_snip#DrawingBrushExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingBrushExample.cs#drawingbrushexamplewholepage)]
 [!code-xaml[DrawingMiscSnippets_snip#DrawingBrushExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingBrushExample.xaml#drawingbrushexamplewholepage)]  
  
 Le <xref:System.Windows.Media.DrawingBrush> classe fournit une variété d’options pour étirer et de la mosaïque de son contenu. Pour plus d’informations sur <xref:System.Windows.Media.DrawingBrush>, consultez le [peinture avec des Images, de dessin et visuels](painting-with-images-drawings-and-visuals.md) vue d’ensemble.  
  
<a name="renderingwithvisualsection"></a>   
## <a name="render-a-drawing-with-a-visual"></a>Afficher un dessin avec un objet visuel  
 Un <xref:System.Windows.Media.DrawingVisual> est un type d’objet visuel conçu pour afficher un dessin. Les développeurs qui souhaitent créer un environnement graphique hautement personnalisé peuvent travailler directement sur la couche visuelle, qui n’est pas décrite dans cette vue d’ensemble. Pour plus d’informations, consultez la vue d’ensemble [Utiliser des objets DrawingVisual](using-drawingvisual-objects.md).  
  
<a name="drawingcontextobjects"></a>   
## <a name="drawingcontext-objects"></a>Objets DrawingContext  
 Le <xref:System.Windows.Media.DrawingContext> classe vous permet de remplir un <xref:System.Windows.Media.Visual> ou un <xref:System.Windows.Media.Drawing> avec un contenu visuel. Nombre d’objets graphiques de bas niveau utilisent un <xref:System.Windows.Media.DrawingContext> , car il décrit le contenu graphique très efficacement.  
  
 Bien que le <xref:System.Windows.Media.DrawingContext> les méthodes de dessin ressemblent aux méthodes de dessin de le <xref:System.Drawing.Graphics?displayProperty=nameWithType> type, ils sont en réalité très différentes. <xref:System.Windows.Media.DrawingContext> est utilisé avec un système de graphiques en mode retenu, tandis que le <xref:System.Drawing.Graphics?displayProperty=nameWithType> type est utilisé avec un système graphique à mode immédiat. Lorsque vous utilisez un <xref:System.Windows.Media.DrawingContext> commandes de dessin de l’objet, vous stockez réellement un ensemble d’instructions de rendu (bien que le mécanisme de stockage exact varie selon le type d’objet qui fournit le <xref:System.Windows.Media.DrawingContext>) qui seront utilisées ultérieurement par les graphiques système ; ne dessinez pas à l’écran en temps réel. Pour plus d’informations sur le fonctionnement du système graphique de Windows Presentation Foundation (WPF), consultez le [WPF Graphics Rendering Overview](wpf-graphics-rendering-overview.md).  
  
 Vous n’instanciez jamais directement un <xref:System.Windows.Media.DrawingContext>; vous pouvez toutefois acquérir un contexte de dessin de certaines méthodes, telles que <xref:System.Windows.Media.DrawingGroup.Open%2A?displayProperty=nameWithType> et <xref:System.Windows.Media.DrawingVisual.RenderOpen%2A?displayProperty=nameWithType>.  
  
<a name="enumeratevisualcontents"></a>   
## <a name="enumerate-the-contents-of-a-visual"></a>Énumérer le contenu d’un objet visuel  
 En plus de leurs autres utilisations, <xref:System.Windows.Media.Drawing> objets fournissent également un modèle d’objet pour énumérer le contenu d’un <xref:System.Windows.Media.Visual>.  
  
 L’exemple suivant utilise le <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A> méthode pour récupérer le <xref:System.Windows.Media.DrawingGroup> valeur d’un <xref:System.Windows.Media.Visual> et l’énumérer.  
  
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
