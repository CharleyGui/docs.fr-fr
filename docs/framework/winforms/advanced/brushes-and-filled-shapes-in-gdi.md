---
title: Pinceaux et remplissage de formes dans GDI+
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- brushes [Windows Forms], GDI+
- filled shapes [Windows Forms], GDI+
- shapes [Windows Forms], GDI+
- GDI+, brushes
- GDI+, filled shapes
- gradient brushes
- brushes [Windows Forms], gradient
ms.assetid: e863e2a7-0294-4130-99b6-f1ea3201e7cd
ms.openlocfilehash: 45ef0b5920e43300e047d363149ea10a7833477b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912228"
---
# <a name="brushes-and-filled-shapes-in-gdi"></a>Pinceaux et remplissage de formes dans GDI+
Une forme fermée, telle qu’un rectangle ou une ellipse, se compose d’un plan et d’un intérieur. Le contour est dessiné à l’aide d’un stylet et l’intérieur est rempli d’un pinceau. GDI+ fournit plusieurs classes de pinceau pour remplir l’intérieur des formes fermées: <xref:System.Drawing.SolidBrush>, <xref:System.Drawing.Drawing2D.HatchBrush>, <xref:System.Drawing.TextureBrush> <xref:System.Drawing.Drawing2D.LinearGradientBrush>, et <xref:System.Drawing.Drawing2D.PathGradientBrush>. Toutes ces classes héritent de la <xref:System.Drawing.Brush> classe. L’illustration suivante montre un rectangle rempli d’un pinceau plein et une Ellipse remplie avec un pinceau hachuré.  
  
 ![Formes remplies](./media/aboutgdip02-art17.gif "Aboutgdip02_art17")  
  
## <a name="solid-brushes"></a>Pinceaux solides  
 Pour remplir une forme fermée, vous avez besoin d’une instance <xref:System.Drawing.Graphics> de la classe <xref:System.Drawing.Brush>et d’un. L’instance de la <xref:System.Drawing.Graphics> classe fournit des méthodes, telles <xref:System.Drawing.Graphics.FillRectangle%2A> que <xref:System.Drawing.Graphics.FillEllipse%2A>et, et <xref:System.Drawing.Brush> les attributs de stockage du remplissage, tels que la couleur et le modèle. <xref:System.Drawing.Brush> Est passé comme l’un des arguments à la méthode Fill. L’exemple de code suivant montre comment remplir une ellipse avec une couleur rouge unie.  
  
 [!code-csharp[LinesCurvesAndShapes#121](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#121)]
 [!code-vb[LinesCurvesAndShapes#121](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#121)]  
  
> [!NOTE]
> Dans l’exemple précédent, le pinceau est de type <xref:System.Drawing.SolidBrush>, qui hérite de <xref:System.Drawing.Brush>.  
  
## <a name="hatch-brushes"></a>Pinceaux hachuré  
 Lorsque vous remplissez une forme avec un pinceau hachuré, vous spécifiez une couleur de premier plan, une couleur d’arrière-plan et un style de hachurage. La couleur de premier plan est la couleur de la hachure.  
  
 [!code-csharp[LinesCurvesAndShapes#122](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#122)]
 [!code-vb[LinesCurvesAndShapes#122](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#122)]  
  
 GDI+ fournit plus de 50 styles de hachurage. les trois styles indiqués dans l’illustration suivante sont <xref:System.Drawing.Drawing2D.HatchStyle.Horizontal>, <xref:System.Drawing.Drawing2D.HatchStyle.ForwardDiagonal>et <xref:System.Drawing.Drawing2D.HatchStyle.Cross>.  
  
 ![Formes remplies](./media/aboutgdip02-art18.gif "Aboutgdip02_art18")  
  
## <a name="texture-brushes"></a>Pinceaux de texture  
 Avec un pinceau de texture, vous pouvez remplir une forme à l’aide d’un modèle stocké dans une bitmap. Par exemple, supposons que l’image suivante soit stockée dans un `MyTexture.bmp`fichier de disque nommé.  
  
 ![Forme remplie](./media/aboutgdip02-art19.gif "Aboutgdip02_Art19")  
  
 L’exemple de code suivant montre comment remplir une ellipse en répétant l’image stockée `MyTexture.bmp`dans.  
  
 [!code-csharp[LinesCurvesAndShapes#123](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#123)]
 [!code-vb[LinesCurvesAndShapes#123](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#123)]  
  
 L’illustration suivante montre l’Ellipse remplie.  
  
 ![Forme remplie](./media/aboutgdip02-art20.gif "AboutGdip02_Art20")  
  
## <a name="gradient-brushes"></a>Pinceaux de dégradé  
 GDI+ fournit deux genres de pinceaux de dégradé: Linear et Path. Vous pouvez utiliser un pinceau de dégradé linéaire pour remplir une forme avec une couleur qui change graduellement à mesure que vous déplacez la forme horizontalement, verticalement ou en diagonale. L’exemple de code suivant montre comment remplir une ellipse avec un pinceau de dégradé horizontal qui passe du bleu au vert lorsque vous vous déplacez du bord gauche de l’ellipse vers le bord droit.  
  
 [!code-csharp[LinesCurvesAndShapes#124](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#124)]
 [!code-vb[LinesCurvesAndShapes#124](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#124)]  
  
 L’illustration suivante montre l’Ellipse remplie.  
  
 ![Forme remplie](./media/aboutgdip02-art21.gif "AboutGdip02_Art21")  
  
 Vous pouvez configurer un pinceau de dégradé de tracé pour modifier la couleur au fur et à mesure que vous déplacez du centre d’une forme vers le bord.  
  
 ![Forme remplie](./media/aboutgdip02-art22.gif "AboutGdip02_Art22")  
  
 Les pinceaux de dégradé de tracés sont relativement flexibles. Le pinceau de dégradé utilisé pour remplir le triangle dans l’illustration suivante change progressivement du rouge au centre de trois couleurs différentes aux sommets.  
  
 ![Forme remplie](./media/aboutgdip02-art23.gif "AboutGdip02_Art23")  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Drawing.SolidBrush?displayProperty=nameWithType>
- <xref:System.Drawing.Drawing2D.HatchBrush?displayProperty=nameWithType>
- <xref:System.Drawing.TextureBrush?displayProperty=nameWithType>
- <xref:System.Drawing.Drawing2D.LinearGradientBrush?displayProperty=nameWithType>
- [Lignes, courbes et formes](lines-curves-and-shapes.md)
- [Guide pratique pour Dessiner un rectangle rempli dans un Windows Form](how-to-draw-a-filled-rectangle-on-a-windows-form.md)
- [Guide pratique pour Dessiner une Ellipse remplie dans un Windows Form](how-to-draw-a-filled-ellipse-on-a-windows-form.md)
