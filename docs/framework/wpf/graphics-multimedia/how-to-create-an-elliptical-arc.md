---
title: 'Comment : créer un arc elliptique'
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], elliptical arcs
- elliptical arcs [WPF], creating
- arcs [WPF], elliptical
ms.assetid: 3dcfe502-3485-45de-99fb-d53a1367c484
ms.openlocfilehash: d0fffbb25f3c5aaceb2cd80af4f1093e44111200
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77453063"
---
# <a name="how-to-create-an-elliptical-arc"></a>Comment : créer un arc elliptique
Cet exemple montre comment dessiner un arc elliptique. Pour créer un arc elliptique, utilisez les classes <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure>et <xref:System.Windows.Media.ArcSegment>.  
  
## <a name="example"></a>Exemple  
 Dans les exemples suivants, un arc elliptique est dessiné de (10 100) à (200 100). L’ARC a une <xref:System.Windows.Media.ArcSegment.Size%2A> de 100 par 50 pixels indépendants du périphérique, un <xref:System.Windows.Media.ArcSegment.RotationAngle%2A> de 45 degrés, un paramètre de <xref:System.Windows.Media.ArcSegment.IsLargeArc%2A> de `true`et un <xref:System.Windows.Media.ArcSegment.SweepDirection%2A> de <xref:System.Windows.Media.SweepDirection.Counterclockwise>.  
  
 [xaml]  
  
 Dans [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], vous pouvez utiliser la syntaxe d’attribut pour décrire un chemin d’accès.  
  
 [!code-xaml[GeometrySample#56](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/geometryattributesyntaxexample.xaml#56)]  
  
 [xaml]  
  
 (Notez que cette syntaxe d’attribut crée en fait un <xref:System.Windows.Media.StreamGeometry>, une version plus légère d’une <xref:System.Windows.Media.PathGeometry>. (Pour plus d’informations, consultez la page [Syntaxe XAML pour les tracés](path-markup-syntax.md).)  
  
 Dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], vous pouvez également dessiner un arc elliptique en utilisant explicitement des balises d’objet. Les éléments suivants sont équivalents à la balise [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] précédente.  
  
 [!code-xaml[GeometrySample#36](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#36)]  
  
 Cet exemple fait partie d’un exemple plus complet. Pour obtenir l’exemple complet, consultez l' [exemple Geometries](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry).  
  
## <a name="see-also"></a>Voir aussi

- [Créer une courbe de Bézier quadratique](how-to-create-a-quadratic-bezier-curve.md)
- [Créer une courbe de Bézier cubique](how-to-create-a-cubic-bezier-curve.md)
