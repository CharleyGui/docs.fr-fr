---
title: "Optimisation des performances : graphiques 2D et acquisition d'images"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [WPF], performance
- drawing [WPF], optimizing performance
- imaging [WPF], optimizing performance
- shapes [WPF], optimizing performance
- 2D graphics [WPF]
- images [WPF], optimizing performance
ms.assetid: e335601e-28c8-4d64-ba27-778fffd55f72
ms.openlocfilehash: eb3686367873276587572addda436471cd1abf27
ms.sourcegitcommit: e48a54ebe62e874500a7043f6ee0b77a744d55b4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/26/2020
ms.locfileid: "80291799"
---
# <a name="optimizing-performance-2d-graphics-and-imaging"></a>Optimisation des performances : graphiques 2D et acquisition d'images
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fournit une large gamme de fonctionnalités graphiques 2D et d’acquisition d’images qui peuvent être optimisées pour répondre aux spécifications de votre application. Cette rubrique fournit des informations sur l’optimisation des performances dans ces domaines.  

<a name="Drawing_and_Shapes"></a>
## <a name="drawing-and-shapes"></a>Dessin et formes  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]fournit <xref:System.Windows.Media.Drawing> à <xref:System.Windows.Shapes.Shape> la fois et des objets pour représenter le contenu graphique de dessin. Cependant, <xref:System.Windows.Media.Drawing> les objets sont <xref:System.Windows.Shapes.Shape> des constructions plus simples que les objets et offrent de meilleures caractéristiques de performance.  
  
 A <xref:System.Windows.Shapes.Shape> vous permet de dessiner une forme graphique à l’écran. Parce qu’ils <xref:System.Windows.FrameworkElement> sont <xref:System.Windows.Shapes.Shape> dérivés de la classe, les objets peuvent être utilisés à l’intérieur des panneaux et la plupart des contrôles.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] offre plusieurs couches d’accès aux services graphiques et de rendu. À la couche <xref:System.Windows.Shapes.Shape> supérieure, les objets sont faciles à utiliser et fournissent de nombreuses fonctionnalités utiles, telles que la mise en page et la manipulation d’événements. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fournit un certain nombre d’objets de forme prêts à l’emploi. Tous les objets <xref:System.Windows.Shapes.Shape> de forme héritent de la classe. Les objets <xref:System.Windows.Shapes.Ellipse>de <xref:System.Windows.Shapes.Line> <xref:System.Windows.Shapes.Path>forme <xref:System.Windows.Shapes.Polygon> <xref:System.Windows.Shapes.Polyline>disponibles <xref:System.Windows.Shapes.Rectangle>incluent , , , , et .  
  
 <xref:System.Windows.Media.Drawing>les objets, d’autre part, <xref:System.Windows.FrameworkElement> ne dérivent pas de la classe et fournissent une implémentation plus légère pour le rendu des formes, des images et du texte.  
  
 Il existe quatre <xref:System.Windows.Media.Drawing> types d’objets :  
  
- <xref:System.Windows.Media.GeometryDrawing>Dessine une forme.  
  
- <xref:System.Windows.Media.ImageDrawing>Dessine une image.  
  
- <xref:System.Windows.Media.GlyphRunDrawing>Dessine du texte.  
  
- <xref:System.Windows.Media.DrawingGroup>Dessine d’autres dessins. Utilisez un groupe de dessins pour faire de plusieurs dessins un seul et même dessin composite.  
  
 L’objet <xref:System.Windows.Media.GeometryDrawing> est utilisé pour rendre la géométrie. La <xref:System.Windows.Media.Geometry> classe et les classes de béton <xref:System.Windows.Media.CombinedGeometry> <xref:System.Windows.Media.EllipseGeometry>qui <xref:System.Windows.Media.PathGeometry>en dérivent, telles que , , et , fournissent un moyen de rendre les graphiques 2D et de fournir des délits de frappe et de soutien de coupure. Les objets géométriques peuvent être utilisés pour définir la zone d’un contrôle, par exemple, ou pour définir la zone de détourage à appliquer à une image. Les objets géométriques peuvent être des zones simples, telles que des rectangles et des cercles, ou des zones composites créées à partir d’au moins deux objets géométriques. Des régions géométriques plus <xref:System.Windows.Media.PathSegment>complexes peuvent <xref:System.Windows.Media.ArcSegment>être <xref:System.Windows.Media.BezierSegment>créées <xref:System.Windows.Media.QuadraticBezierSegment>en combinant des objets dérivés, tels que , , et .  
  
 À première vue, <xref:System.Windows.Media.Geometry> la <xref:System.Windows.Shapes.Shape> classe et la classe sont similaires. Les deux sont utilisés dans le rendu des graphiques 2D et les <xref:System.Windows.Media.EllipseGeometry> deux <xref:System.Windows.Shapes.Ellipse>ont des classes de béton similaires qui en dérivent, par exemple, et . Cependant, il existe des différences importantes entre ces deux ensembles de classes. D’une <xref:System.Windows.Media.Geometry> part, la classe manque de <xref:System.Windows.Shapes.Shape> certaines fonctionnalités de la classe, comme la capacité de se dessiner. Pour dessiner un objet géométrique, une autre classe telle que DrawingContext, Drawing ou Path (il est important de noter que Path est une forme) doit être utilisée pour effectuer l’opération de dessin. Les propriétés de rendu telles que le remplissage, le trait, et l’épaisseur de course sont sur la classe qui dessine l’objet de géométrie, tandis qu’un objet de forme contient ces propriétés. Une façon de penser à cette différence est qu’un objet de géométrie définit une région, par exemple, un cercle, tandis qu’un objet de forme définit une région, définit la façon dont cette région est remplie et décrite, et participe au système de mise en page.  
  
 Étant <xref:System.Windows.Shapes.Shape> donné que <xref:System.Windows.FrameworkElement> les objets dérivent de la classe, les utiliser peut ajouter beaucoup plus de consommation de mémoire dans votre application. Si vous n’avez <xref:System.Windows.FrameworkElement> vraiment pas besoin des fonctionnalités de <xref:System.Windows.Media.Drawing> votre contenu graphique, envisagez d’utiliser les objets plus légers.  
  
 Pour plus <xref:System.Windows.Media.Drawing> d’informations sur les objets, voir [Aperçu des objets de dessin](../graphics-multimedia/drawing-objects-overview.md).  
  
<a name="StreamGeometry_Objects"></a>
## <a name="streamgeometry-objects"></a>Objets StreamGeometry  
 L’objet <xref:System.Windows.Media.StreamGeometry> est une <xref:System.Windows.Media.PathGeometry> alternative légère à la création de formes géométriques. Utilisez <xref:System.Windows.Media.StreamGeometry> un lorsque vous avez besoin de décrire une géométrie complexe. <xref:System.Windows.Media.StreamGeometry>est optimisé pour <xref:System.Windows.Media.PathGeometry> la manipulation de nombreux objets et <xref:System.Windows.Media.PathGeometry> fonctionne mieux par rapport à l’utilisation de nombreux objets individuels.  
  
 L’exemple suivant utilise la syntaxe <xref:System.Windows.Media.StreamGeometry> [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]d’attribut pour créer une triangulaire dans .  
  
 [!code-xaml[GeometriesMiscSnippets_snip#StreamGeometryTriangleExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/GeometriesMiscSnippets_snip/XAML/StreamGeometryExample.xaml#streamgeometrytriangleexamplewholepage)]  
  
 Pour plus <xref:System.Windows.Media.StreamGeometry> d’informations sur les objets, voir [Créer une forme à l’aide d’une streamGeometry](../graphics-multimedia/how-to-create-a-shape-using-a-streamgeometry.md).  
  
<a name="DrawingVisual_Objects"></a>
## <a name="drawingvisual-objects"></a>Objets DrawingVisual  
 L’objet <xref:System.Windows.Media.DrawingVisual> est une classe de dessin léger qui est utilisé pour rendre des formes, des images ou du texte. Cette classe est dite légère, car elle n’assure pas la gestion des dispositions ni des événements, ce qui améliore ses performances. C’est pourquoi, les dessins de ce type sont idéaux pour les arrière-plans et les images clipart. Pour plus d’informations, consultez [Utilisation d’objets DrawingVisual](../graphics-multimedia/using-drawingvisual-objects.md).  
  
<a name="Images"></a>
## <a name="images"></a>Images  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]l’imagerie fournit une amélioration significative par rapport aux capacités d’imagerie dans les versions précédentes de Windows. Les capacités d’imagerie, telles que l’affichage d’un bitmap ou l’utilisation d’une image sur un contrôle commun, ont été principalement gérées par microsoft Windows Graphics Device Interface (GDI) ou Microsoft Windows GDIMD interface de programmation d’application (API). Ces API fournissaient des fonctionnalités d’imagerie de base, mais manquaient de fonctionnalités telles que le support de l’extéabilité codec et le support d’image haute fidélité. Les API D’imagerie WPF ont été redessinés pour surmonter les lacunes de GDI et GDIMD et fournir un nouvel ensemble d’API pour afficher et utiliser des images dans vos applications.  
  
 Quand vous utilisez des images, tenez compte des recommandations suivantes pour obtenir de meilleures performances :  
  
- Si votre application vous impose d’afficher des images miniatures, envisagez de créer une version de taille réduite de l’image. Par défaut, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] charge votre image et la décode à sa taille maximale. Si vous voulez seulement une version miniature de l’image, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] décode inutilement l’image à sa taille maximale et la réduit ensuite à une taille miniature. Pour éviter ce traitement inutile, vous pouvez soit demander à [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] de décoder l’image en taille miniature, soit demander à [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] de charger une image de taille miniature.  
  
- Décodez toujours l’image à la taille souhaitée et non à la taille par défaut. Comme indiqué ci-dessus, demandez à [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] de décoder votre image à la taille souhaitée et non à la taille maximale par défaut. Vous réduirez non seulement la plage de travail de votre application, mais son exécution sera également plus rapide.  
  
- Si possible, combinez plusieurs images pour en faire une seule, comme une bande de film composée de plusieurs images.  
  
- Pour plus d’informations, voir [Aperçu de l’imagerie](../graphics-multimedia/imaging-overview.md).  
  
### <a name="bitmapscalingmode"></a>BitmapScalingMode  
 Lors de l’animation de l’échelle de n’importe quelle bitmap, l’algorithme de rééchantillonnement d’image par défaut de haute qualité peut parfois consommer suffisamment de ressources système pour provoquer une dégradation des taux d’images, ce qui provoque efficacement des animations à bégayer. En définissant <xref:System.Windows.Media.RenderOptions.BitmapScalingMode%2A> la <xref:System.Windows.Media.RenderOptions> propriété <xref:System.Windows.Media.BitmapScalingMode.LowQuality>de l’objet à , vous pouvez créer une animation plus lisse lors de l’échelle d’un bitmap. <xref:System.Windows.Media.BitmapScalingMode.LowQuality>le mode [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] indique au moteur de rendu de passer d’un algorithme optimisé pour la qualité à un algorithme optimisé en vitesse lors du traitement des images.  
  
 L’exemple suivant montre <xref:System.Windows.Media.BitmapScalingMode> comment définir le pour un objet d’image.  
  
 [!code-csharp[RenderOptions#RenderOptionsSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/RenderOptions/CSharp/Window1.xaml.cs#renderoptionssnippet2)]
 [!code-vb[RenderOptions#RenderOptionsSnippet2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RenderOptions/visualbasic/window1.xaml.vb#renderoptionssnippet2)]  
  
### <a name="cachinghint"></a>CachingHint  
 Par [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] défaut, ne cache pas <xref:System.Windows.Media.TileBrush> le contenu <xref:System.Windows.Media.DrawingBrush> rendu <xref:System.Windows.Media.VisualBrush>des objets, tels que et . Dans les scénarios statiques où <xref:System.Windows.Media.TileBrush> le contenu ou l’utilisation de la scène ne changent pas, cela est logique, car il conserve la mémoire vidéo. Il n’a pas autant <xref:System.Windows.Media.TileBrush> de sens lorsqu’un contenu statique est utilisé d’une manière non statique, par exemple, lorsqu’un objet statique <xref:System.Windows.Media.DrawingBrush> ou <xref:System.Windows.Media.VisualBrush> est cartographié à la surface d’un objet 3D rotatif. Le comportement [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] par défaut est de re-rendre l’ensemble du contenu de la <xref:System.Windows.Media.DrawingBrush> ou <xref:System.Windows.Media.VisualBrush> pour chaque image, même si le contenu est immuable.  
  
 En définissant <xref:System.Windows.Media.RenderOptions.CachingHint%2A> la <xref:System.Windows.Media.RenderOptions> propriété <xref:System.Windows.Media.CachingHint.Cache>de l’objet à , vous pouvez augmenter les performances en utilisant des versions mises en cache des objets de brosse carrelés.  
  
 La <xref:System.Windows.Media.RenderOptions.CacheInvalidationThresholdMinimum%2A> <xref:System.Windows.Media.RenderOptions.CacheInvalidationThresholdMaximum%2A> valeur et la propriété sont <xref:System.Windows.Media.TileBrush> des valeurs de taille relative qui déterminent quand l’objet doit être régénéré en raison de changements d’échelle. Par exemple, en <xref:System.Windows.Media.RenderOptions.CacheInvalidationThresholdMaximum%2A> fixant la propriété à 2.0, le cache pour le <xref:System.Windows.Media.TileBrush> seul doit être régénéré lorsque sa taille dépasse le double de la taille du cache actuel.  
  
 L’exemple suivant montre comment utiliser l’option d’indice de mise en cache pour un <xref:System.Windows.Media.DrawingBrush>.  
  
 [!code-csharp[RenderOptions#RenderOptionsSnippet3](~/samples/snippets/csharp/VS_Snippets_Wpf/RenderOptions/CSharp/Window1.xaml.cs#renderoptionssnippet3)]
 [!code-vb[RenderOptions#RenderOptionsSnippet3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RenderOptions/visualbasic/window1.xaml.vb#renderoptionssnippet3)]  
  
## <a name="see-also"></a>Voir aussi

- [Optimisation des performances des applications WPF](optimizing-wpf-application-performance.md)
- [Planification des performances des applications](planning-for-application-performance.md)
- [Tirer parti du matériel](optimizing-performance-taking-advantage-of-hardware.md)
- [Disposition et conception](optimizing-performance-layout-and-design.md)
- [Comportement de l’objet](optimizing-performance-object-behavior.md)
- [Ressources d’application](optimizing-performance-application-resources.md)
- [Texte](optimizing-performance-text.md)
- [Liaison de données](optimizing-performance-data-binding.md)
- [Autres recommandations relatives aux performances](optimizing-performance-other-recommendations.md)
- [Conseils et astuces sur les animations](../graphics-multimedia/animation-tips-and-tricks.md)
