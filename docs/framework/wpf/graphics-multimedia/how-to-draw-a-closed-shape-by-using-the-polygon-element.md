---
title: "Comment : dessiner une forme fermée à l'aide de l'élément Polygon"
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], Polygon elements
- closed shapes [WPF], drawing with Polygon elements
- Polygon elements [WPF]
- drawing [WPF], closed shapes with Polygon elements
ms.assetid: 4b0ca008-29ce-48dd-8bc3-f3a20ffca6a6
ms.openlocfilehash: 324a5623ee658789b8600a43a89ce26cab7cd6cd
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452972"
---
# <a name="how-to-draw-a-closed-shape-by-using-the-polygon-element"></a>Comment : dessiner une forme fermée à l'aide de l'élément Polygon
Cet exemple montre comment dessiner une forme fermée à l’aide de l’élément <xref:System.Windows.Shapes.Polygon>. Pour dessiner une forme fermée, créez un élément <xref:System.Windows.Shapes.Polygon> et utilisez sa propriété <xref:System.Windows.Shapes.Polygon.Points%2A> pour spécifier les vertex d’une forme. Une ligne est automatiquement dessinée qui connecte le premier et le dernier point. Enfin, spécifiez un <xref:System.Windows.Shapes.Shape.Fill%2A>, un <xref:System.Windows.Shapes.Shape.Stroke%2A>ou les deux.  
  
## <a name="example"></a>Exemple  
 Dans [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], la syntaxe valide pour points est une liste délimitée par des espaces de paires de coordonnées x et y séparées par des virgules.  
  
 [!code-xaml[drawingwithshapeelements#PolygonExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/polygonexample.xaml#polygonexample1)]  
  
 Bien que l’exemple utilise une <xref:System.Windows.Controls.Canvas> pour contenir les polygones, vous pouvez utiliser des éléments Polygon (et tous les autres éléments Shape) avec n’importe quel <xref:System.Windows.Controls.Panel> ou <xref:System.Windows.Controls.Control> qui prend en charge le contenu non textuel.  
  
 Cet exemple fait partie d’un exemple plus grand ; pour obtenir l’exemple complet, consultez [exemple d’éléments de forme](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).
