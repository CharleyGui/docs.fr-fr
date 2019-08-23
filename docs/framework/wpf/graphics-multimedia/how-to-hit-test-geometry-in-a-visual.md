---
title: 'Procédure : Effectuer un test de positionnement avec Geometry dans un Visual'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hit tests [WPF], on visual objects comprising Geometry objects [WPF]
- visual objects [WPF], hit tests on
- Geometry objects [WPF], visual objects comprising
ms.assetid: 8bf2643f-d7f9-4cb4-9ea6-5b893c23200d
ms.openlocfilehash: 52b9b99b0af38d797e4a3c98dc0979211c930c1f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923379"
---
# <a name="how-to-hit-test-geometry-in-a-visual"></a>Procédure : Effectuer un test de positionnement avec Geometry dans un Visual
Cet exemple montre comment effectuer un test de positionnement sur un objet visuel composé d’un ou de plusieurs <xref:System.Windows.Media.Geometry> objets.  
  
## <a name="example"></a>Exemples  
 L’exemple suivant montre comment récupérer <xref:System.Windows.Media.DrawingGroup> à partir d’un objet visuel qui utilise la <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A> méthode. Un test de positionnement est ensuite effectué sur le contenu rendu de chaque dessin dans <xref:System.Windows.Media.DrawingGroup> le pour déterminer la géométrie qui a été atteinte.  
  
> [!NOTE]
> Dans la plupart des cas, vous utiliseriez la <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> méthode pour déterminer si un point croise n’importe quel contenu rendu d’un visuel.  
  
 [!code-csharp[VisualsOverview#VisualsOverviewSnippet4](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml.cs#visualsoverviewsnippet4)]
 [!code-vb[VisualsOverview#VisualsOverviewSnippet4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsOverview/visualbasic/window1.xaml.vb#visualsoverviewsnippet4)]  
  
 La <xref:System.Windows.Media.Geometry.FillContains%2A> méthode est une méthode surchargée qui vous permet d’effectuer un test de positionnement à <xref:System.Windows.Point> l' <xref:System.Windows.Media.Geometry>aide d’un ou d’un spécifié. Si une géométrie est barrée, le trait peut s’étendre en dehors des limites du remplissage. Dans ce cas, vous souhaiterez peut- <xref:System.Windows.Media.Geometry.StrokeContains%2A> être appeler en <xref:System.Windows.Media.Geometry.FillContains%2A>plus de.  
  
 Vous pouvez également fournir un <xref:System.Windows.Media.ToleranceType> utilisé dans le cadre de l’aplatissement de Bézier.  
  
> [!NOTE]
> Cet exemple ne prend pas en compte les transformations ou les découpages qui peuvent être appliqués à la géométrie. En outre, cet exemple ne fonctionnera pas avec un contrôle sur lequel est appliqué un style, car aucun dessin ne lui est directement associé.  
  
## <a name="see-also"></a>Voir aussi

- [Test de positionnement dans la couche visuelle](hit-testing-in-the-visual-layer.md)
- [Effectuer un test de positionnement avec Geometry comme paramètre](how-to-hit-test-using-geometry-as-a-parameter.md)
