---
title: 'Optimisation des performances: Graphisme 2D et acquisition d’images'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [WPF], performance
- drawing [WPF], optimizing performance
- imaging [WPF], optimizing performance
- shapes [WPF], optimizing performance
- 2-D graphics [WPF]
- images [WPF], optimizing performance
ms.assetid: e335601e-28c8-4d64-ba27-778fffd55f72
ms.openlocfilehash: 764e7e802ccaff50b76229b9441380bfe77fefb5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933355"
---
# <a name="optimizing-performance-2d-graphics-and-imaging"></a>Optimisation des performances: Graphisme 2D et acquisition d’images
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fournit une large gamme de fonctionnalités graphiques 2D et d’acquisition d’images qui peuvent être optimisées pour répondre aux spécifications de votre application. Cette rubrique fournit des informations sur l’optimisation des performances dans ces domaines.  

<a name="Drawing_and_Shapes"></a>   
## <a name="drawing-and-shapes"></a>Dessin et formes  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]fournit les <xref:System.Windows.Media.Drawing> objets <xref:System.Windows.Shapes.Shape> et pour représenter le contenu de dessin graphique. Toutefois, <xref:System.Windows.Media.Drawing> les objets sont des constructions plus simples <xref:System.Windows.Shapes.Shape> que des objets et offrent de meilleures caractéristiques de performances.  
  
 Un <xref:System.Windows.Shapes.Shape> vous permet de dessiner une forme graphique à l’écran. Étant donné qu’ils sont dérivés de <xref:System.Windows.Shapes.Shape> la classe, les objets peuvent être utilisés dans les <xref:System.Windows.FrameworkElement> panneaux et la plupart des contrôles.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] offre plusieurs couches d’accès aux services graphiques et de rendu. Au niveau de la couche <xref:System.Windows.Shapes.Shape> supérieure, les objets sont faciles à utiliser et fournissent de nombreuses fonctionnalités utiles, telles que la disposition et la gestion des événements. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fournit un certain nombre d’objets de forme prêts à l’emploi. Tous les objets de forme héritent de la <xref:System.Windows.Shapes.Shape> classe. Les objets de forme <xref:System.Windows.Shapes.Ellipse>disponibles <xref:System.Windows.Shapes.Line>incluent <xref:System.Windows.Shapes.Path>, <xref:System.Windows.Shapes.Polygon>, <xref:System.Windows.Shapes.Polyline>,, <xref:System.Windows.Shapes.Rectangle>et.  
  
 <xref:System.Windows.Media.Drawing>en revanche, les objets ne dérivent pas de la <xref:System.Windows.FrameworkElement> classe et fournissent une implémentation plus légère pour le rendu des formes, des images et du texte.  
  
 Il existe quatre types d' <xref:System.Windows.Media.Drawing> objets:  
  
- <xref:System.Windows.Media.GeometryDrawing>Dessine une forme.  
  
- <xref:System.Windows.Media.ImageDrawing>Dessine une image.  
  
- <xref:System.Windows.Media.GlyphRunDrawing>Dessine du texte.  
  
- <xref:System.Windows.Media.DrawingGroup>Dessine d’autres dessins. Utilisez un groupe de dessins pour faire de plusieurs dessins un seul et même dessin composite.  
  
 L' <xref:System.Windows.Media.GeometryDrawing> objet est utilisé pour restituer le contenu géométrique. La <xref:System.Windows.Media.Geometry> classe et les classes concrètes qui dérivent de celle <xref:System.Windows.Media.CombinedGeometry>-ci, <xref:System.Windows.Media.PathGeometry>telles que, <xref:System.Windows.Media.EllipseGeometry>et, permettent de restituer des graphiques 2D, ainsi que de fournir un test de positionnement et une prise en charge du découpage. Les objets géométriques peuvent être utilisés pour définir la zone d’un contrôle, par exemple, ou pour définir la zone de détourage à appliquer à une image. Les objets géométriques peuvent être des zones simples, telles que des rectangles et des cercles, ou des zones composites créées à partir d’au moins deux objets géométriques. Des régions géométriques plus complexes peuvent être <xref:System.Windows.Media.PathSegment>créées en combinant des objets dérivés <xref:System.Windows.Media.BezierSegment>de, <xref:System.Windows.Media.QuadraticBezierSegment>tels que <xref:System.Windows.Media.ArcSegment>, et.  
  
 Sur la surface, la <xref:System.Windows.Media.Geometry> classe et la <xref:System.Windows.Shapes.Shape> classe sont assez similaires. Les deux sont utilisés dans le rendu des graphiques 2D et les deux ont des classes concrètes similaires qui dérivent <xref:System.Windows.Media.EllipseGeometry> de <xref:System.Windows.Shapes.Ellipse>celles-ci, par exemple et. Cependant, il existe des différences importantes entre ces deux ensembles de classes. Pour un, la <xref:System.Windows.Media.Geometry> classe ne dispose pas de certaines fonctionnalités de la <xref:System.Windows.Shapes.Shape> classe, telles que la possibilité de se dessiner lui-même. Pour dessiner un objet géométrique, une autre classe telle que DrawingContext, Drawing ou Path (il est important de noter que Path est une forme) doit être utilisée pour effectuer l’opération de dessin. Les propriétés de rendu telles que le remplissage, le trait et l’épaisseur de trait appartiennent à la classe qui dessine l’objet géométrique, alors qu’un objet de forme contient ces propriétés. Une façon de se figurer cette différence est de considérer qu’un objet géométrique définit une zone, par exemple un cercle, alors qu’un objet de forme définit une zone, définit son remplissage et son contour et participe au système de disposition.  
  
 Étant <xref:System.Windows.Shapes.Shape> donné que les objets <xref:System.Windows.FrameworkElement> dérivent de la classe, leur utilisation peut accroître considérablement la consommation de mémoire dans votre application. Si vous n’avez pas vraiment besoin <xref:System.Windows.FrameworkElement> des fonctionnalités pour votre contenu graphique, envisagez d’utiliser les <xref:System.Windows.Media.Drawing> objets légers.  
  
 Pour plus d’informations <xref:System.Windows.Media.Drawing> sur les objets, consultez [vue d’ensemble des objets de dessin](../graphics-multimedia/drawing-objects-overview.md).  
  
<a name="StreamGeometry_Objects"></a>   
## <a name="streamgeometry-objects"></a>Objets StreamGeometry  
 L' <xref:System.Windows.Media.StreamGeometry> objet est une alternative légère à <xref:System.Windows.Media.PathGeometry> pour créer des formes géométriques. Utilisez une <xref:System.Windows.Media.StreamGeometry> lorsque vous devez décrire une géométrie complexe. <xref:System.Windows.Media.StreamGeometry>est optimisé pour gérer de <xref:System.Windows.Media.PathGeometry> nombreux objets et est plus performant par rapport à l' <xref:System.Windows.Media.PathGeometry> utilisation de nombreux objets individuels.  
  
 L’exemple suivant utilise la syntaxe d’attribut pour créer un <xref:System.Windows.Media.StreamGeometry> triangulaire dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 [!code-xaml[GeometriesMiscSnippets_snip#StreamGeometryTriangleExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/GeometriesMiscSnippets_snip/XAML/StreamGeometryExample.xaml#streamgeometrytriangleexamplewholepage)]  
  
 Pour plus d’informations <xref:System.Windows.Media.StreamGeometry> sur les objets, consultez [créer une forme à l’aide d’un StreamGeometry](../graphics-multimedia/how-to-create-a-shape-using-a-streamgeometry.md).  
  
<a name="DrawingVisual_Objects"></a>   
## <a name="drawingvisual-objects"></a>Objets DrawingVisual  
 L' <xref:System.Windows.Media.DrawingVisual> objet est une classe de dessin légère qui est utilisée pour restituer des formes, des images ou du texte. Cette classe est dite légère, car elle n’assure pas la gestion des dispositions ni des événements, ce qui améliore ses performances. C’est pourquoi, les dessins de ce type sont idéaux pour les arrière-plans et les images clipart. Pour plus d’informations, consultez [Utilisation d’objets DrawingVisual](../graphics-multimedia/using-drawingvisual-objects.md).  
  
<a name="Images"></a>   
## <a name="images"></a>Images  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]l’acquisition d’images apporte une amélioration significative par rapport aux fonctionnalités de création d’images des versions précédentes de Windows. Les fonctionnalités liées aux images, telles que l’affichage d’une image bitmap ou l’utilisation d’une image sur un contrôle commun, étaient principalement gérées par l’interface de programmation d’application (API) Microsoft Windows Graphics Device Interface (GDI) ou Microsoft Windows GDI+. Si ces API proposaient des fonctionnalités de base en matière d’images, elles étaient dépourvues de certaines autres fonctionnalités telles que la prise en charge de l’extensibilité de codec et des images haute fidélité. Les API d’acquisition d’images WPF ont été repensées pour surmonter les lacunes de GDI et GDI+, et proposent un nouvel ensemble d’API pour afficher et utiliser des images dans vos applications.  
  
 Quand vous utilisez des images, tenez compte des recommandations suivantes pour obtenir de meilleures performances :  
  
- Si votre application vous impose d’afficher des images miniatures, envisagez de créer une version de taille réduite de l’image. Par défaut, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] charge votre image et la décode à sa taille maximale. Si vous voulez seulement une version miniature de l’image, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] décode inutilement l’image à sa taille maximale et la réduit ensuite à une taille miniature. Pour éviter ce traitement inutile, vous pouvez soit demander à [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] de décoder l’image en taille miniature, soit demander à [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] de charger une image de taille miniature.  
  
- Décodez toujours l’image à la taille souhaitée et non à la taille par défaut. Comme indiqué ci-dessus, demandez à [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] de décoder votre image à la taille souhaitée et non à la taille maximale par défaut. Vous réduirez non seulement la plage de travail de votre application, mais son exécution sera également plus rapide.  
  
- Si possible, combinez plusieurs images pour en faire une seule, comme une bande de film composée de plusieurs images.  
  
- Pour plus d’informations, consultez [Vue d’ensemble de la création d’images](../graphics-multimedia/imaging-overview.md).  
  
### <a name="bitmapscalingmode"></a>BitmapScalingMode  
 Quand vous animez l’échelle d’une image bitmap, l’algorithme de rééchantillonnage d’image haute qualité par défaut peut parfois consommer une quantité de ressources système telle que la fréquence d’images se dégrade et les animations deviennent saccadées. En affectant <xref:System.Windows.Media.RenderOptions.BitmapScalingMode%2A> à la propriété <xref:System.Windows.Media.RenderOptions> de l' <xref:System.Windows.Media.BitmapScalingMode.LowQuality> objet la valeur, vous pouvez créer une animation plus lisse lors de la mise à l’échelle d’une image bitmap. <xref:System.Windows.Media.BitmapScalingMode.LowQuality>le mode indique [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] au moteur de rendu de passer d’un algorithme optimisé pour la qualité à un algorithme optimisé pour la vitesse lors du traitement des images.  
  
 L’exemple suivant montre comment définir <xref:System.Windows.Media.BitmapScalingMode> pour un objet image.  
  
 [!code-csharp[RenderOptions#RenderOptionsSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/RenderOptions/CSharp/Window1.xaml.cs#renderoptionssnippet2)]
 [!code-vb[RenderOptions#RenderOptionsSnippet2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RenderOptions/visualbasic/window1.xaml.vb#renderoptionssnippet2)]  
  
### <a name="cachinghint"></a>CachingHint  
 Par défaut, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ne met pas en cache le contenu <xref:System.Windows.Media.TileBrush> rendu des objets, <xref:System.Windows.Media.DrawingBrush> tels <xref:System.Windows.Media.VisualBrush>que et. Dans les scénarios statiques où ni le contenu, ni <xref:System.Windows.Media.TileBrush> l’utilisation du dans la scène ne change, cela est logique, car il conserve la mémoire vidéo. Elle n’a pas de sens lorsqu’un <xref:System.Windows.Media.TileBrush> avec du contenu statique est utilisé de façon non statique (par exemple, lorsqu’un statique <xref:System.Windows.Media.DrawingBrush> ou <xref:System.Windows.Media.VisualBrush> est mappé à la surface d’un objet 3D en rotation). Le comportement par défaut [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] de est de restituer à nouveau le contenu entier <xref:System.Windows.Media.DrawingBrush> du <xref:System.Windows.Media.VisualBrush> ou de chaque frame, même si le contenu n’est pas modifié.  
  
 En affectant <xref:System.Windows.Media.RenderOptions.CachingHint%2A> la valeur à <xref:System.Windows.Media.RenderOptions> <xref:System.Windows.Media.CachingHint.Cache> la propriété de l’objet, vous pouvez améliorer les performances en utilisant les versions mises en cache des objets de pinceau en mosaïque.  
  
 Les <xref:System.Windows.Media.RenderOptions.CacheInvalidationThresholdMinimum%2A> valeurs <xref:System.Windows.Media.RenderOptions.CacheInvalidationThresholdMaximum%2A> de propriété et sont des valeurs de taille relative qui <xref:System.Windows.Media.TileBrush> déterminent le moment où l’objet doit être régénéré en raison des modifications apportées à l’échelle. Par exemple, en affectant <xref:System.Windows.Media.RenderOptions.CacheInvalidationThresholdMaximum%2A> à la propriété la valeur 2,0, le <xref:System.Windows.Media.TileBrush> cache du seul doit être régénéré lorsque sa taille dépasse le double de la taille du cache actuel.  
  
 L’exemple suivant montre comment utiliser l’option d’indicateur de mise en <xref:System.Windows.Media.DrawingBrush>cache pour un.  
  
 [!code-csharp[RenderOptions#RenderOptionsSnippet3](~/samples/snippets/csharp/VS_Snippets_Wpf/RenderOptions/CSharp/Window1.xaml.cs#renderoptionssnippet3)]
 [!code-vb[RenderOptions#RenderOptionsSnippet3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RenderOptions/visualbasic/window1.xaml.vb#renderoptionssnippet3)]  
  
## <a name="see-also"></a>Voir aussi

- [Optimisation des performances des applications WPF](optimizing-wpf-application-performance.md)
- [Planification des performances des applications](planning-for-application-performance.md)
- [Tirer parti du matériel](optimizing-performance-taking-advantage-of-hardware.md)
- [Disposition et conception](optimizing-performance-layout-and-design.md)
- [Comportement de l’objet](optimizing-performance-object-behavior.md)
- [Ressources d'application](optimizing-performance-application-resources.md)
- [Text](optimizing-performance-text.md)
- [Liaison de données](optimizing-performance-data-binding.md)
- [Autres recommandations relatives aux performances](optimizing-performance-other-recommendations.md)
- [Conseils et astuces sur les animations](../graphics-multimedia/animation-tips-and-tricks.md)
