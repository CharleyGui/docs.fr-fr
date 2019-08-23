---
title: Peinture avec des objets d'image, de dessin et visuels
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- brushes [WPF], painting with drawings
- painting [WPF], with drawings
- painting [WPF], with images
- painting with visuals [WPF]
- brushes [WPF], painting with images
- brushes [WPF], painting with visuals
ms.assetid: 779aac3f-8d41-49d8-8130-768244aa2240
ms.openlocfilehash: e80132a5467f932e5569787f43427044ba2be256
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929609"
---
# <a name="painting-with-images-drawings-and-visuals"></a>Peinture avec des objets d'image, de dessin et visuels
Cette rubrique explique comment <xref:System.Windows.Media.ImageBrush>utiliser les objets, <xref:System.Windows.Media.DrawingBrush>et <xref:System.Windows.Media.VisualBrush> pour peindre une zone avec une image, un <xref:System.Windows.Media.Drawing>ou un <xref:System.Windows.Media.Visual>.  

<a name="prereqs"></a>   
## <a name="prerequisites"></a>Prérequis  
 Pour comprendre cette rubrique, vous devez connaître les différents types de pinceaux fournis par [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] et leurs fonctions de base. Pour une introduction, consultez [Vue d’ensemble des pinceaux WPF](wpf-brushes-overview.md).  
  
<a name="image"></a>   
## <a name="paint-an-area-with-an-image"></a>Peindre une zone avec une image  
 Peint une zone avec un <xref:System.Windows.Media.ImageSource>. <xref:System.Windows.Media.ImageBrush> Le type le plus courant <xref:System.Windows.Media.ImageSource> de à utiliser avec <xref:System.Windows.Media.ImageBrush> un est <xref:System.Windows.Media.Imaging.BitmapImage>un, qui décrit un graphique bitmap. Vous pouvez utiliser un <xref:System.Windows.Media.DrawingImage> pour peindre à l' <xref:System.Windows.Media.Drawing> aide d’un objet, mais il est plus simple <xref:System.Windows.Media.DrawingBrush> d’utiliser à la place. Pour plus d’informations <xref:System.Windows.Media.ImageSource> sur les objets, consultez [vue d’ensemble de la création d’images](imaging-overview.md).  
  
 Pour peindre avec un <xref:System.Windows.Media.ImageBrush>, créez un <xref:System.Windows.Media.Imaging.BitmapImage> et utilisez-le pour charger le contenu de la bitmap. Utilisez <xref:System.Windows.Media.Imaging.BitmapImage> ensuite pour définir la <xref:System.Windows.Media.ImageBrush.ImageSource%2A> propriété de <xref:System.Windows.Media.ImageBrush>. Enfin, appliquez le <xref:System.Windows.Media.ImageBrush> à l’objet que vous souhaitez peindre.  Dans [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], vous pouvez également définir simplement la <xref:System.Windows.Media.ImageBrush.ImageSource%2A> propriété de <xref:System.Windows.Media.ImageBrush> avec le chemin d’accès de l’image à charger.  
  
 Comme tous <xref:System.Windows.Media.Brush> les objets, <xref:System.Windows.Media.ImageBrush> un peut être utilisé pour peindre des objets tels que des formes, des panneaux, des contrôles et du texte. L’illustration suivante montre certains effets pouvant être obtenus avec un <xref:System.Windows.Media.ImageBrush>.  
  
 ![Exemples de sortie ImageBrush](./media/wcpsdk-mmgraphics-imagebrushexamples.gif "wcpsdk_mmgraphics_imagebrushexamples")  
Objets peints par un élément ImageBrush  
  
 Par défaut, un <xref:System.Windows.Media.ImageBrush> étire son image pour remplir complètement la zone qui est peinte, ce qui peut éventuellement déformer l’image si la zone peinte a des proportions différentes de celles de l’image. Vous pouvez modifier ce comportement en affectant <xref:System.Windows.Media.TileBrush.Stretch%2A> à la propriété sa <xref:System.Windows.Media.Stretch.Fill> valeur <xref:System.Windows.Media.Stretch.None>par défaut, <xref:System.Windows.Media.Stretch.Uniform>ou <xref:System.Windows.Media.Stretch.UniformToFill>. Étant <xref:System.Windows.Media.ImageBrush> donné que est un <xref:System.Windows.Media.TileBrush>type de, vous pouvez spécifier exactement comment un pinceau d’image remplit la zone de sortie et même créer des modèles. Pour plus d’informations sur <xref:System.Windows.Media.TileBrush> les fonctionnalités avancées, consultez la [vue d’ensemble de TileBrush](tilebrush-overview.md).  
  
<a name="fillingpanelwithimage"></a>   
## <a name="example-paint-an-object-with-a-bitmap-image"></a>Exemple : Peindre un objet avec une image bitmap  
 L’exemple suivant utilise un <xref:System.Windows.Media.ImageBrush> pour peindre le <xref:System.Windows.Controls.Panel.Background%2A> d’un <xref:System.Windows.Controls.Canvas>.  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMImageBrushAsCanvasBackgroundExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/ImageBrushExample.xaml#graphicsmmimagebrushascanvasbackgroundexamplewholepage)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMImageBrushAsCanvasBackgroundExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/ImageBrushExample.cs#graphicsmmimagebrushascanvasbackgroundexamplewholepage)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMImageBrushAsCanvasBackgroundExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/imagebrushexample.vb#graphicsmmimagebrushascanvasbackgroundexamplewholepage)]  
  
<a name="drawingbrushintro"></a>   
## <a name="paint-an-area-with-a-drawing"></a>Peindre une zone avec un dessin  
 Un <xref:System.Windows.Media.DrawingBrush> vous permet de peindre une zone avec des formes, du texte, des images et des vidéos. Les formes à l’intérieur d’un pinceau de dessin peuvent elles-mêmes être peintes avec une couleur unie <xref:System.Windows.Media.DrawingBrush>, un dégradé, une image ou même une autre. L’illustration suivante montre certaines utilisations d’un <xref:System.Windows.Media.DrawingBrush>.  
  
 ![Exemples de sortie DrawingBrush](./media/wcpsdk-mmgraphics-drawingbrushexamples.png "wcpsdk_mmgraphics_drawingbrushexamples")  
Objets peints par un élément DrawingBrush  
  
 Peint une zone avec un <xref:System.Windows.Media.Drawing> objet. <xref:System.Windows.Media.DrawingBrush> Un <xref:System.Windows.Media.Drawing> objet décrit un contenu visible, tel qu’une forme, une image bitmap, une vidéo ou une ligne de texte. Différents types de dessins décrivent différents types de contenus. La liste suivante répertorie les différents types d’objets Drawing.  
  
- <xref:System.Windows.Media.GeometryDrawing>: Dessine une forme.  
  
- <xref:System.Windows.Media.ImageDrawing>: Dessine une image.  
  
- <xref:System.Windows.Media.GlyphRunDrawing>: Dessine le texte.  
  
- <xref:System.Windows.Media.VideoDrawing>: Lit un fichier audio ou vidéo.  
  
- <xref:System.Windows.Media.DrawingGroup>: Dessine d’autres dessins. Utilisez un groupe de dessins pour faire de plusieurs dessins un seul et même dessin composite.  
  
 Pour plus d’informations <xref:System.Windows.Media.Drawing> sur les objets, consultez [vue d’ensemble des objets dessinés](drawing-objects-overview.md).  
  
 Comme un <xref:System.Windows.Media.ImageBrush>, un <xref:System.Windows.Media.DrawingBrush> étire son <xref:System.Windows.Media.DrawingBrush.Drawing%2A> pour remplir sa zone de sortie. Vous pouvez substituer ce comportement en modifiant la <xref:System.Windows.Media.TileBrush.Stretch%2A> propriété de sa <xref:System.Windows.Media.Stretch.Fill>valeur par défaut. Pour plus d'informations, consultez la propriété <xref:System.Windows.Media.TileBrush.Stretch%2A>.  
  
<a name="fillingareawithdrawingbrushexample"></a>   
## <a name="example-paint-an-object-with-a-drawing"></a>Exemple : Peindre un objet avec un dessin  
 L’exemple suivant montre comment peindre un objet avec un dessin composé de trois ellipses. Un <xref:System.Windows.Media.GeometryDrawing> est utilisé pour décrire les ellipses.  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMDrawingBrushAsButtonBackgroundExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/DrawingBrushExample.xaml#graphicsmmdrawingbrushasbuttonbackgroundexample)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMDrawingBrushAsButtonBackgroundExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/DrawingBrushExample.cs#graphicsmmdrawingbrushasbuttonbackgroundexample1)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMDrawingBrushAsButtonBackgroundExample1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/drawingbrushexample.vb#graphicsmmdrawingbrushasbuttonbackgroundexample1)]  
  
<a name="visualbrushsection"></a>   
## <a name="paint-an-area-with-a-visual"></a>Peindre une zone avec un visuel  
 Le plus polyvalent et le plus puissant de tous les pinceaux, le <xref:System.Windows.Media.VisualBrush> peint une zone avec un. <xref:System.Windows.Media.Visual> Un <xref:System.Windows.Media.Visual> est un type graphique de bas niveau qui sert d’ancêtre de nombreux composants graphiques utiles. Par exemple, les <xref:System.Windows.Window>classes <xref:System.Windows.FrameworkElement>, et <xref:System.Windows.Controls.Control> sont tous des types d' <xref:System.Windows.Media.Visual> objets. À l' <xref:System.Windows.Media.VisualBrush>aide d’un, vous pouvez peindre des [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] zones avec presque n’importe quel objet graphique.  
  
> [!NOTE]
> Bien <xref:System.Windows.Media.VisualBrush> que soit un type <xref:System.Windows.Freezable> d’objet, il ne peut pas être figé (en lecture seule) <xref:System.Windows.Media.VisualBrush.Visual%2A> quand sa propriété est définie sur une valeur `null`autre que.  
  
 Il existe deux façons de spécifier le <xref:System.Windows.Media.VisualBrush.Visual%2A> contenu d’un <xref:System.Windows.Media.VisualBrush>.  
  
- Créez un nouveau <xref:System.Windows.Media.Visual> et utilisez-le pour définir <xref:System.Windows.Media.VisualBrush.Visual%2A> la propriété de <xref:System.Windows.Media.VisualBrush>. Pour obtenir un exemple, consultez [l’exemple: Peignez un objet avec une](#examplevisualbrush1) section visuelle qui suit.  
  
- Utilisez un existant <xref:System.Windows.Media.Visual>, qui crée une image dupliquée de la <xref:System.Windows.Media.Visual>cible. Vous pouvez ensuite utiliser le <xref:System.Windows.Media.VisualBrush> pour créer des effets intéressants, tels que la réflexion et le grossissement. Pour obtenir un exemple, consultez [l’exemple: Créer une section](#examplevisualbrush2) réflexion.  
  
 Quand vous définissez un nouveau <xref:System.Windows.Media.VisualBrush.Visual%2A> pour un <xref:System.Windows.Media.VisualBrush> et qu' <xref:System.Windows.Media.Visual> il s' <xref:System.Windows.UIElement> agit d’un (tel qu’un panneau ou un contrôle), le système <xref:System.Windows.UIElement> de disposition s’exécute sur `true`le <xref:System.Windows.Media.VisualBrush.AutoLayoutContent%2A> et ses éléments enfants lorsque la propriété a la valeur. Toutefois, la racine <xref:System.Windows.UIElement> est isolée essentiellement du reste du système: les styles et la disposition externe ne peuvent pas faire la perméation de cette limite. Par conséquent, vous devez spécifier explicitement la taille de la <xref:System.Windows.UIElement>racine, car son seul parent est <xref:System.Windows.Media.VisualBrush> le et, par conséquent, il ne peut pas se redimensionner automatiquement à la zone qui est peinte. Pour plus d’informations sur la disposition en [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], consultez [Disposition](../advanced/layout.md).  
  
 Comme <xref:System.Windows.Media.ImageBrush> et <xref:System.Windows.Media.DrawingBrush>, un<xref:System.Windows.Media.VisualBrush> étire son contenu pour remplir sa zone de sortie. Vous pouvez substituer ce comportement en modifiant la <xref:System.Windows.Media.TileBrush.Stretch%2A> propriété de sa <xref:System.Windows.Media.Stretch.Fill>valeur par défaut. Pour plus d'informations, consultez la propriété <xref:System.Windows.Media.TileBrush.Stretch%2A>.  
  
<a name="examplevisualbrush1"></a>   
## <a name="example-paint-an-object-with-a-visual"></a>Exemple : Peindre un objet avec un visuel  
 Dans l’exemple suivant, plusieurs contrôles et un panneau sont utilisés pour peindre un rectangle.  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMVisualBrushAsRectangleBackgroundExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/VisualBrushExample.xaml#graphicsmmvisualbrushasrectanglebackgroundexample)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMVisualBrushAsRectangleBackgroundExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/VisualBrushExample.cs#graphicsmmvisualbrushasrectanglebackgroundexample1)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMVisualBrushAsRectangleBackgroundExample1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/visualbrushexample.vb#graphicsmmvisualbrushasrectanglebackgroundexample1)]  
  
<a name="examplevisualbrush2"></a>   
## <a name="example-create-a-reflection"></a>Exemple : Créer une réflexion  
 L’exemple précédent a montré comment créer un nouveau <xref:System.Windows.Media.Visual> pour l’utiliser en tant qu’arrière-plan. Vous pouvez également utiliser un <xref:System.Windows.Media.VisualBrush> pour afficher un visuel existant; cette fonctionnalité vous permet de produire des effets visuels intéressants, tels que des réflexions et un grossissement. L’exemple suivant utilise un <xref:System.Windows.Media.VisualBrush> pour créer la réflexion d’un <xref:System.Windows.Controls.Border> qui contient plusieurs éléments. L’illustration suivante montre la sortie que l’exemple génère.  
  
 ![Objet visuel réfléchi](./media/graphicsmm-visualbrush-reflection-small.jpg "graphicsmm_visualbrush_reflection_small")  
Objet Visual réfléchi  
  
 [!code-csharp[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/visualbrush_markup_snip/CSharp/ReflectionExample.cs#graphicsmmvisualbrushreflectionexamplewholepage)]
 [!code-vb[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/visualbrush_markup_snip/visualbasic/reflectionexample.vb#graphicsmmvisualbrushreflectionexamplewholepage)]
 [!code-xaml[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/visualbrush_markup_snip/XAML/ReflectionExample.xaml#graphicsmmvisualbrushreflectionexamplewholepage)]  
  
 Pour obtenir des exemples supplémentaires qui montrent comment agrandir des parties de l’écran et créer des réflexions, consultez [VisualBrush Sample](https://go.microsoft.com/fwlink/?LinkID=160049) (Exemple de VisualBrush).  
  
<a name="tilebrush"></a>   
## <a name="tilebrush-features"></a>Fonctionnalités de TileBrush  
 <xref:System.Windows.Media.ImageBrush>, <xref:System.Windows.Media.DrawingBrush> <xref:System.Windows.Media.TileBrush> et <xref:System.Windows.Media.VisualBrush> sont des types d’objets. <xref:System.Windows.Media.TileBrush>les objets vous fournissent un grand contrôle sur la façon dont une zone est peinte avec une image, un dessin ou un visuel. Par exemple, au lieu de simplement peindre une zone avec une seule image étirée, vous pouvez peindre une zone avec une série de mosaïques d’image qui créent un motif.  
  
 Un <xref:System.Windows.Media.TileBrush> a trois composants principaux: le contenu, les vignettes et la zone de sortie.  
  
 ![Composants TileBrush](./media/wcpsdk-mmgraphics-defaultcontentprojection2.png "wcpsdk_mmgraphics_defaultcontentprojection2")  
Composants d’un TileBrush avec une seule mosaïque  
  
 ![Composants d’un TileBrush en mosaïque](./media/graphicsmm-tiledprojection.png "graphicsmm_tiledprojection")  
Composants d’un élément TileBrush avec plusieurs mosaïques  
  
 Pour plus d’informations sur les fonctionnalités de <xref:System.Windows.Media.TileBrush> mosaïque des objets, consultez la [vue d’ensemble de TileBrush](tilebrush-overview.md).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Media.ImageBrush>
- <xref:System.Windows.Media.DrawingBrush>
- <xref:System.Windows.Media.VisualBrush>
- <xref:System.Windows.Media.TileBrush>
- [Vue d’ensemble de TileBrush](tilebrush-overview.md)
- [Vue d’ensemble des pinceaux WPF](wpf-brushes-overview.md)
- [Vue d’ensemble de la création d’images](imaging-overview.md)
- [Vue d’ensemble des objets de dessin](drawing-objects-overview.md)
- [Vue d'ensemble des masques d'opacité](opacity-masks-overview.md)
- [Vue d’ensemble du rendu graphique de WPF](wpf-graphics-rendering-overview.md)
- [ImageBrush, exemple](https://go.microsoft.com/fwlink/?LinkID=160005)
- [VisualBrush Sample](https://go.microsoft.com/fwlink/?LinkID=160049) (Exemple de VisualBrush)
