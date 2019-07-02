---
title: Courbes ouvertes et fermées dans GDI+
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- curves [Windows Forms], filling
- GDI+, curves
- curves [Windows Forms], drawing
- curves
ms.assetid: 08d2cc9a-dc9d-4eed-bcbb-2c8e2ca5d3ae
ms.openlocfilehash: 06afdc4549f7c3c9b0636e5c7052dcca87a153f1
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67505456"
---
# <a name="open-and-closed-curves-in-gdi"></a>Courbes ouvertes et fermées dans GDI+
L’illustration suivante montre deux courbes : un seul est ouvert et l’autre fermée.  
  
 ![Courbes ouvertes et fermées](./media/aboutgdip02-art24.gif "Aboutgdip02_art24")  
  
## <a name="managed-interface-for-curves"></a>Interface managée pour les courbes  
 Courbes fermées ont un intérieur et qui peuvent être remplis avec un pinceau. Le <xref:System.Drawing.Graphics> classe dans GDI + fournit les méthodes suivantes pour remplir des formes fermées et courbes : <xref:System.Drawing.Graphics.FillRectangle%2A>, <xref:System.Drawing.Graphics.FillEllipse%2A>, <xref:System.Drawing.Graphics.FillPie%2A>, <xref:System.Drawing.Graphics.FillPolygon%2A>, <xref:System.Drawing.Graphics.FillClosedCurve%2A>, <xref:System.Drawing.Graphics.FillPath%2A>, et <xref:System.Drawing.Graphics.FillRegion%2A>. Chaque fois que vous appelez une de ces méthodes, vous devez passer un des types de pinceau spécifique (<xref:System.Drawing.SolidBrush>, <xref:System.Drawing.Drawing2D.HatchBrush>, <xref:System.Drawing.TextureBrush>, <xref:System.Drawing.Drawing2D.LinearGradientBrush>, ou <xref:System.Drawing.Drawing2D.PathGradientBrush>) en tant qu’argument.  
  
 Le <xref:System.Drawing.Graphics.FillPie%2A> méthode est un complément de la <xref:System.Drawing.Graphics.DrawArc%2A> (méthode). Tout comme le <xref:System.Drawing.Graphics.DrawArc%2A> méthode dessine une partie du contour d’une ellipse, le <xref:System.Drawing.Graphics.FillPie%2A> méthode remplit une portion de l’intérieur d’une ellipse. L’exemple suivant dessine un arc et remplit la partie correspondante de l’intérieur de l’ellipse :  
  
 [!code-csharp[LinesCurvesAndShapes#21](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#21)]
 [!code-vb[LinesCurvesAndShapes#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#21)]  
  
 L’illustration suivante montre l’arc et le secteur rempli.  
  
 ![Courbes ouvertes et fermées](./media/aboutgdip02-art25.gif "Aboutgdip02_art25")  
  
 Le <xref:System.Drawing.Graphics.FillClosedCurve%2A> méthode est un complément de la <xref:System.Drawing.Graphics.DrawClosedCurve%2A> (méthode). Les deux méthodes ferment automatiquement la courbe en connectant le point de fin au point de départ. L’exemple suivant dessine une courbe qui traverse (0, 0), (60, 20) et (40, 50). Ensuite, la courbe est fermée automatiquement en vous connectant (40, 50) au point de départ (0, 0), et l’intérieur est rempli avec une couleur unie.  
  
 [!code-csharp[LinesCurvesAndShapes#22](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#22)]
 [!code-vb[LinesCurvesAndShapes#22](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#22)]  
  
 Le <xref:System.Drawing.Graphics.FillPath%2A> méthode remplit l’intérieur des différents éléments d’un chemin d’accès. Si une partie d’un chemin d’accès ne forme pas une courbe fermée ou une forme, le <xref:System.Drawing.Graphics.FillPath%2A> méthode ferme automatiquement cet élément et le chemin d’accès avant de le remplir. L’exemple suivant dessine et remplit un chemin d’accès qui se compose d’un arc, une spline cardinale, une chaîne et un graphique en secteurs :  
  
 [!code-csharp[LinesCurvesAndShapes#23](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#23)]
 [!code-vb[LinesCurvesAndShapes#23](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#23)]  
  
 L’illustration suivante montre le chemin d’accès avec et sans le remplissage uni. Notez que le texte dans la chaîne est indiqué, mais ne remplit pas par le <xref:System.Drawing.Graphics.DrawPath%2A> (méthode). Il s’agit du <xref:System.Drawing.Graphics.FillPath%2A> (méthode) qui peint l’intérieur des caractères dans la chaîne.  
  
 ![Chaîne dans un chemin d’accès](./media/aboutgdip02-art26.gif "Aboutgdip02_art26")  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Drawing.Drawing2D.GraphicsPath?displayProperty=nameWithType>
- <xref:System.Drawing.Pen?displayProperty=nameWithType>
- <xref:System.Drawing.Point?displayProperty=nameWithType>
- [Lignes, courbes et formes](lines-curves-and-shapes.md)
- [Guide pratique pour Créer des objets graphiques pour le dessin](how-to-create-graphics-objects-for-drawing.md)
- [Génération et dessin de tracés](constructing-and-drawing-paths.md)
