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
ms.openlocfilehash: e0e5e386b32425c87502d18a24e758193c14a5b6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186920"
---
# <a name="painting-with-images-drawings-and-visuals"></a>Peinture avec des objets d'image, de dessin et visuels
Ce sujet décrit comment <xref:System.Windows.Media.ImageBrush> <xref:System.Windows.Media.DrawingBrush>utiliser <xref:System.Windows.Media.VisualBrush> , , et les objets <xref:System.Windows.Media.Drawing>pour peindre <xref:System.Windows.Media.Visual>une zone avec une image, un , ou un .  

<a name="prereqs"></a>
## <a name="prerequisites"></a>Conditions préalables requises  
 Pour comprendre cette rubrique, vous devez connaître les différents types de pinceaux fournis par [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] et leurs fonctions de base. Pour une introduction, consultez [Vue d’ensemble des pinceaux WPF](wpf-brushes-overview.md).  
  
<a name="image"></a>
## <a name="paint-an-area-with-an-image"></a>Peindre une zone avec une image  
 Un <xref:System.Windows.Media.ImageBrush> peint une zone <xref:System.Windows.Media.ImageSource>avec un . Le type le <xref:System.Windows.Media.ImageSource> plus commun <xref:System.Windows.Media.ImageBrush> d’utiliser avec un est un <xref:System.Windows.Media.Imaging.BitmapImage>, qui décrit un graphique bitmap. Vous pouvez <xref:System.Windows.Media.DrawingImage> utiliser un <xref:System.Windows.Media.Drawing> pour peindre à l’aide <xref:System.Windows.Media.DrawingBrush> d’un objet, mais il est plus simple d’utiliser un à la place. Pour plus <xref:System.Windows.Media.ImageSource> d’informations sur les objets, voir [l’aperçu de l’imagerie](imaging-overview.md).  
  
 Pour peindre <xref:System.Windows.Media.ImageBrush>avec un <xref:System.Windows.Media.Imaging.BitmapImage> , créer un et l’utiliser pour charger la teneur en bitmap. Ensuite, utilisez <xref:System.Windows.Media.Imaging.BitmapImage> le <xref:System.Windows.Media.ImageBrush.ImageSource%2A> pour définir <xref:System.Windows.Media.ImageBrush>la propriété de la . Enfin, appliquez l’objet <xref:System.Windows.Media.ImageBrush> que vous souhaitez peindre.  En [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], vous pouvez <xref:System.Windows.Media.ImageBrush.ImageSource%2A> également simplement <xref:System.Windows.Media.ImageBrush> définir la propriété de la avec le chemin de l’image à charger.  
  
 Comme <xref:System.Windows.Media.Brush> tous les <xref:System.Windows.Media.ImageBrush> objets, un peut être utilisé pour peindre des objets tels que des formes, des panneaux, des commandes et du texte. L’illustration suivante montre quelques effets <xref:System.Windows.Media.ImageBrush>qui peuvent être atteints avec un .  
  
 ![Exemples de sortie ImageBrush](./media/wcpsdk-mmgraphics-imagebrushexamples.gif "wcpsdk_mmgraphics_imagebrushexamples")  
Objets peints par un élément ImageBrush  
  
 Par défaut, <xref:System.Windows.Media.ImageBrush> un étend son image pour remplir complètement la zone peinte, déformant éventuellement l’image si la zone peinte a un rapport d’aspect différent de l’image. Vous pouvez changer ce <xref:System.Windows.Media.TileBrush.Stretch%2A> comportement en changeant <xref:System.Windows.Media.Stretch.Fill> la <xref:System.Windows.Media.Stretch.None> <xref:System.Windows.Media.Stretch.Uniform>propriété <xref:System.Windows.Media.Stretch.UniformToFill>de sa valeur par défaut de , , ou . Parce <xref:System.Windows.Media.ImageBrush> que c’est un type de <xref:System.Windows.Media.TileBrush>, vous pouvez spécifier exactement comment une brosse d’image remplit la zone de sortie et même créer des motifs. Pour plus d’informations sur les fonctionnalités avancées, <xref:System.Windows.Media.TileBrush> voir le Aperçu de [TileBrush](tilebrush-overview.md).  
  
<a name="fillingpanelwithimage"></a>
## <a name="example-paint-an-object-with-a-bitmap-image"></a>Exemple : Peindre un objet avec une image bitmap  
 L’exemple suivant <xref:System.Windows.Media.ImageBrush> utilise <xref:System.Windows.Controls.Panel.Background%2A> un <xref:System.Windows.Controls.Canvas>pour peindre le d’un .  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMImageBrushAsCanvasBackgroundExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/ImageBrushExample.xaml#graphicsmmimagebrushascanvasbackgroundexamplewholepage)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMImageBrushAsCanvasBackgroundExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/ImageBrushExample.cs#graphicsmmimagebrushascanvasbackgroundexamplewholepage)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMImageBrushAsCanvasBackgroundExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/imagebrushexample.vb#graphicsmmimagebrushascanvasbackgroundexamplewholepage)]  
  
<a name="drawingbrushintro"></a>
## <a name="paint-an-area-with-a-drawing"></a>Peindre une zone avec un dessin  
 A <xref:System.Windows.Media.DrawingBrush> vous permet de peindre une zone avec des formes, du texte, des images et de la vidéo. Les formes à l’intérieur d’un pinceau de dessin peuvent <xref:System.Windows.Media.DrawingBrush>elles-mêmes être peintes avec une couleur solide, gradient, image, ou même un autre. L’illustration suivante démontre quelques <xref:System.Windows.Media.DrawingBrush>utilisations d’un .  
  
 ![Exemples de sortie DrawingBrush](./media/wcpsdk-mmgraphics-drawingbrushexamples.png "wcpsdk_mmgraphics_drawingbrushexamples")  
Objets peints par un élément DrawingBrush  
  
 Un <xref:System.Windows.Media.DrawingBrush> peint une zone <xref:System.Windows.Media.Drawing> avec un objet. Un <xref:System.Windows.Media.Drawing> objet décrit le contenu visible, comme une forme, une bitmap, une vidéo ou une ligne de texte. Différents types de dessins décrivent différents types de contenus. La liste suivante répertorie les différents types d’objets Drawing.  
  
- <xref:System.Windows.Media.GeometryDrawing>Dessine une forme.  
  
- <xref:System.Windows.Media.ImageDrawing>Dessine une image.  
  
- <xref:System.Windows.Media.GlyphRunDrawing>Dessine du texte.  
  
- <xref:System.Windows.Media.VideoDrawing>- Lecture d’un fichier audio ou vidéo.  
  
- <xref:System.Windows.Media.DrawingGroup>Dessine d’autres dessins. Utilisez un groupe de dessins pour faire de plusieurs dessins un seul et même dessin composite.  
  
 Pour plus <xref:System.Windows.Media.Drawing> d’informations sur les objets, voir le [Aperçu des objets de dessin](drawing-objects-overview.md).  
  
 Comme <xref:System.Windows.Media.ImageBrush>un <xref:System.Windows.Media.DrawingBrush> , <xref:System.Windows.Media.DrawingBrush.Drawing%2A> un s’étend son pour remplir sa zone de sortie. Vous pouvez remplacer ce comportement <xref:System.Windows.Media.TileBrush.Stretch%2A> en changeant la <xref:System.Windows.Media.Stretch.Fill>propriété de son paramètre par défaut de . Pour plus d'informations, consultez la propriété <xref:System.Windows.Media.TileBrush.Stretch%2A>.  
  
<a name="fillingareawithdrawingbrushexample"></a>
## <a name="example-paint-an-object-with-a-drawing"></a>Exemple : Peindre un objet avec un dessin  
 L’exemple suivant montre comment peindre un objet avec un dessin composé de trois ellipses. A <xref:System.Windows.Media.GeometryDrawing> est utilisé pour décrire les ellipses.  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMDrawingBrushAsButtonBackgroundExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/DrawingBrushExample.xaml#graphicsmmdrawingbrushasbuttonbackgroundexample)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMDrawingBrushAsButtonBackgroundExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/DrawingBrushExample.cs#graphicsmmdrawingbrushasbuttonbackgroundexample1)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMDrawingBrushAsButtonBackgroundExample1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/drawingbrushexample.vb#graphicsmmdrawingbrushasbuttonbackgroundexample1)]  
  
<a name="visualbrushsection"></a>
## <a name="paint-an-area-with-a-visual"></a>Peindre une zone avec un visuel  
 Le plus polyvalent et puissant de <xref:System.Windows.Media.VisualBrush> tous les pinceaux, les peintures d’une zone avec un <xref:System.Windows.Media.Visual>. A <xref:System.Windows.Media.Visual> est un type graphique de bas niveau qui sert d’ancêtre de nombreux composants graphiques utiles. Par exemple, <xref:System.Windows.Window> <xref:System.Windows.FrameworkElement>le <xref:System.Windows.Controls.Control> , , et <xref:System.Windows.Media.Visual> les classes sont tous les types d’objets. En <xref:System.Windows.Media.VisualBrush>utilisant un , vous [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] pouvez peindre des zones avec presque n’importe quel objet graphique.  
  
> [!NOTE]
> Bien <xref:System.Windows.Media.VisualBrush> qu’il <xref:System.Windows.Freezable> s’agit d’un type d’objet, il ne peut pas être congelé (fait lu uniquement) lorsque sa <xref:System.Windows.Media.VisualBrush.Visual%2A> propriété est réglée à une valeur autre que `null`.  
  
 Il existe deux façons <xref:System.Windows.Media.VisualBrush.Visual%2A> de <xref:System.Windows.Media.VisualBrush>spécifier le contenu d’un .  
  
- Créez un <xref:System.Windows.Media.Visual> nouveau et l’utiliser pour définir la <xref:System.Windows.Media.VisualBrush.Visual%2A> propriété de la <xref:System.Windows.Media.VisualBrush>. Pour obtenir un exemple, consultez la section [Exemple : Peindre un objet avec un objet visuel](#examplevisualbrush1) plus loin dans cette rubrique.  
  
- Utilisez un <xref:System.Windows.Media.Visual>existant , qui crée <xref:System.Windows.Media.Visual>une image en double de la cible . Vous pouvez ensuite <xref:System.Windows.Media.VisualBrush> utiliser le pour créer des effets intéressants, tels que la réflexion et le grossissement. Pour obtenir un exemple, consultez la section [Exemple : Créer une réflexion](#examplevisualbrush2).  
  
 Lorsque vous définissez <xref:System.Windows.Media.VisualBrush.Visual%2A> un nouveau pour <xref:System.Windows.Media.VisualBrush> un et qui <xref:System.Windows.Media.Visual> est un <xref:System.Windows.UIElement> (comme <xref:System.Windows.UIElement> un panneau ou <xref:System.Windows.Media.VisualBrush.AutoLayoutContent%2A> un contrôle), le système de mise en page fonctionne sur les éléments et son enfant lorsque la propriété est réglée à `true`. Cependant, la <xref:System.Windows.UIElement> racine est essentiellement isolée du reste du système: les styles, et la disposition externe ne peut pas impréger cette frontière. Par conséquent, vous devez spécifier explicitement la taille de la racine <xref:System.Windows.UIElement>, parce que son seul parent est le <xref:System.Windows.Media.VisualBrush> et donc il ne peut pas automatiquement se tailler à la zone peinte. Pour plus d’informations sur la disposition en [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], consultez [Disposition](../advanced/layout.md).  
  
 Comme <xref:System.Windows.Media.ImageBrush> <xref:System.Windows.Media.DrawingBrush>et <xref:System.Windows.Media.VisualBrush> , un étend son contenu pour remplir sa zone de sortie. Vous pouvez remplacer ce comportement <xref:System.Windows.Media.TileBrush.Stretch%2A> en changeant la <xref:System.Windows.Media.Stretch.Fill>propriété de son paramètre par défaut de . Pour plus d'informations, consultez la propriété <xref:System.Windows.Media.TileBrush.Stretch%2A>.  
  
<a name="examplevisualbrush1"></a>
## <a name="example-paint-an-object-with-a-visual"></a>Exemple : Peindre un objet avec un objet visuel  
 Dans l’exemple suivant, plusieurs contrôles et un panneau sont utilisés pour peindre un rectangle.  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMVisualBrushAsRectangleBackgroundExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/VisualBrushExample.xaml#graphicsmmvisualbrushasrectanglebackgroundexample)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMVisualBrushAsRectangleBackgroundExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/VisualBrushExample.cs#graphicsmmvisualbrushasrectanglebackgroundexample1)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMVisualBrushAsRectangleBackgroundExample1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/visualbrushexample.vb#graphicsmmvisualbrushasrectanglebackgroundexample1)]  
  
<a name="examplevisualbrush2"></a>
## <a name="example-create-a-reflection"></a>Exemple : Créer une réflexion  
 L’exemple précédent a montré <xref:System.Windows.Media.Visual> comment créer un nouveau pour une utilisation comme arrière-plan. Vous pouvez également <xref:System.Windows.Media.VisualBrush> utiliser un pour afficher un visuel existant; cette capacité vous permet de produire des effets visuels intéressants, tels que les réflexions et le grossissement. L’exemple suivant <xref:System.Windows.Media.VisualBrush> utilise un pour <xref:System.Windows.Controls.Border> créer un reflet d’un qui contient plusieurs éléments. L’illustration suivante montre la sortie que l’exemple génère.  
  
 ![Objet Visual réfléchi](./media/graphicsmm-visualbrush-reflection-small.jpg "graphicsmm_visualbrush_reflection_small")  
Objet Visual réfléchi  
  
 [!code-csharp[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/visualbrush_markup_snip/CSharp/ReflectionExample.cs#graphicsmmvisualbrushreflectionexamplewholepage)]
 [!code-vb[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/visualbrush_markup_snip/visualbasic/reflectionexample.vb#graphicsmmvisualbrushreflectionexamplewholepage)]
 [!code-xaml[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/visualbrush_markup_snip/XAML/ReflectionExample.xaml#graphicsmmvisualbrushreflectionexamplewholepage)]  
  
 Pour obtenir des exemples supplémentaires qui montrent comment agrandir des parties de l’écran et créer des réflexions, consultez [VisualBrush Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/VisualBrush) (Exemple de VisualBrush).  
  
<a name="tilebrush"></a>
## <a name="tilebrush-features"></a>Fonctionnalités de TileBrush  
 <xref:System.Windows.Media.ImageBrush>, <xref:System.Windows.Media.DrawingBrush>et <xref:System.Windows.Media.VisualBrush> sont <xref:System.Windows.Media.TileBrush> des types d’objets. <xref:System.Windows.Media.TileBrush>objets vous fournir un grand contrôle sur la façon dont une zone est peinte avec une image, un dessin ou un visuel. Par exemple, au lieu de simplement peindre une zone avec une seule image étirée, vous pouvez peindre une zone avec une série de mosaïques d’image qui créent un motif.  
  
 A <xref:System.Windows.Media.TileBrush> comporte trois composants principaux : le contenu, les tuiles et la zone de sortie.  
  
 ![Composants de TileBrush](./media/wcpsdk-mmgraphics-defaultcontentprojection2.png "wcpsdk_mmgraphics_defaultcontentprojection2")  
Composants d’un TileBrush avec une seule mosaïque  
  
 ![Composants d'un TileBrush en mosaïque](./media/graphicsmm-tiledprojection.png "graphicsmm_tiledprojection")  
Composants d’un élément TileBrush avec plusieurs mosaïques  
  
 Pour plus d’informations sur <xref:System.Windows.Media.TileBrush> les caractéristiques de carrelage des objets, voir le [Aperçu de TileBrush](tilebrush-overview.md).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Media.ImageBrush>
- <xref:System.Windows.Media.DrawingBrush>
- <xref:System.Windows.Media.VisualBrush>
- <xref:System.Windows.Media.TileBrush>
- [Vue d’ensemble de TileBrush](tilebrush-overview.md)
- [Vue d'ensemble des pinceaux WPF](wpf-brushes-overview.md)
- [Vue d’ensemble de la création d’images](imaging-overview.md)
- [Vue d'ensemble des objets Drawing](drawing-objects-overview.md)
- [Vue d’ensemble des masques d’opacité](opacity-masks-overview.md)
- [Vue d’ensemble du rendu graphique de WPF](wpf-graphics-rendering-overview.md)
- [ImageBrush Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ImageBrush) (Exemple d’ImageBrush)
- [VisualBrush Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/VisualBrush) (Exemple de VisualBrush)
