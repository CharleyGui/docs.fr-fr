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
ms.openlocfilehash: ad3a4af2474ace61bbf35ea1357a2a6037af039a
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67506239"
---
# <a name="brushes-and-filled-shapes-in-gdi"></a>Pinceaux et remplissage de formes dans GDI+
Une forme fermée, comme un rectangle ou une ellipse, se compose d’un plan et un intérieur. Le contour est dessiné avec un stylet et l’intérieur est rempli avec un pinceau. GDI + fournit plusieurs classes de pinceau pour remplir l’intérieur des formes fermées : <xref:System.Drawing.SolidBrush>, <xref:System.Drawing.Drawing2D.HatchBrush>, <xref:System.Drawing.TextureBrush>, <xref:System.Drawing.Drawing2D.LinearGradientBrush>, et <xref:System.Drawing.Drawing2D.PathGradientBrush>. Toutes ces classes héritent de la <xref:System.Drawing.Brush> classe. L’illustration suivante montre un rectangle rempli avec un pinceau uni et une ellipse remplie avec un pinceau de hachurage.  
  
 ![Formes pleines](./media/aboutgdip02-art17.gif "Aboutgdip02_art17")  
  
## <a name="solid-brushes"></a>Pinceaux solide  
 Pour remplir une forme fermée, vous avez besoin d’une instance de la <xref:System.Drawing.Graphics> classe et un <xref:System.Drawing.Brush>. L’instance de la <xref:System.Drawing.Graphics> classe fournit des méthodes, telles que <xref:System.Drawing.Graphics.FillRectangle%2A> et <xref:System.Drawing.Graphics.FillEllipse%2A>et le <xref:System.Drawing.Brush> stocke les attributs de remplissage, telles que la couleur et le motif. Le <xref:System.Drawing.Brush> est passé comme argument à la méthode de remplissage. L’exemple de code suivant montre comment remplir une ellipse avec une couleur rouge unie.  
  
 [!code-csharp[LinesCurvesAndShapes#121](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#121)]
 [!code-vb[LinesCurvesAndShapes#121](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#121)]  
  
> [!NOTE]
>  Dans l’exemple précédent, le pinceau est de type <xref:System.Drawing.SolidBrush>, qui hérite de <xref:System.Drawing.Brush>.  
  
## <a name="hatch-brushes"></a>Pinceaux à hachures  
 Lorsque vous remplissez une forme avec un pinceau de hachurage, vous spécifiez une couleur de premier plan, une couleur d’arrière-plan et un style de hachurage. La couleur de premier plan est la couleur des hachures.  
  
 [!code-csharp[LinesCurvesAndShapes#122](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#122)]
 [!code-vb[LinesCurvesAndShapes#122](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#122)]  
  
 GDI + offre plus de 50 styles de hachurage. les trois styles présentés dans l’illustration suivante sont <xref:System.Drawing.Drawing2D.HatchStyle.Horizontal>, <xref:System.Drawing.Drawing2D.HatchStyle.ForwardDiagonal>, et <xref:System.Drawing.Drawing2D.HatchStyle.Cross>.  
  
 ![Formes pleines](./media/aboutgdip02-art18.gif "Aboutgdip02_art18")  
  
## <a name="texture-brushes"></a>Pinceaux de texture  
 Avec un pinceau de la texture, vous pouvez remplir une forme avec un modèle stocké dans une bitmap. Par exemple, supposons que l’image suivante est stockée dans un fichier de disque nommé `MyTexture.bmp`.  
  
 ![Rempli forme](./media/aboutgdip02-art19.gif "Aboutgdip02_Art19")  
  
 L’exemple de code suivant montre comment remplir une ellipse en répétant l’image stockée dans `MyTexture.bmp`.  
  
 [!code-csharp[LinesCurvesAndShapes#123](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#123)]
 [!code-vb[LinesCurvesAndShapes#123](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#123)]  
  
 L’illustration suivante montre l’ellipse remplie.  
  
 ![Rempli forme](./media/aboutgdip02-art20.gif "AboutGdip02_Art20")  
  
## <a name="gradient-brushes"></a>Pinceaux de dégradé  
 GDI + offre deux types de pinceaux de dégradé : linéaire et chemin d’accès. Vous pouvez utiliser un pinceau dégradé linéaire pour remplir une forme avec une couleur qui change graduellement à mesure que vous déplacer entre la forme horizontalement, verticalement ou en diagonale. L’exemple de code suivant montre comment remplir une ellipse avec un pinceau de dégradé horizontal qui passe du bleu au vert lorsque vous déplacez le bord gauche de l’ellipse vers le bord droit.  
  
 [!code-csharp[LinesCurvesAndShapes#124](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#124)]
 [!code-vb[LinesCurvesAndShapes#124](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#124)]  
  
 L’illustration suivante montre l’ellipse remplie.  
  
 ![Rempli forme](./media/aboutgdip02-art21.gif "AboutGdip02_Art21")  
  
 Un pinceau de dégradé de chemin d’accès peut être configuré pour modifier la couleur à mesure que vous déplacez à partir du centre de la forme vers le bord.  
  
 ![Rempli forme](./media/aboutgdip02-art22.gif "AboutGdip02_Art22")  
  
 Pinceaux de dégradé de chemin d’accès est très souples. Pinceau de dégradé utilisé pour remplir le triangle dans les modifications suivantes d’illustration progressivement du rouge au centre à chacune des trois couleurs différentes sur les sommets.  
  
 ![Rempli forme](./media/aboutgdip02-art23.gif "AboutGdip02_Art23")  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Drawing.SolidBrush?displayProperty=nameWithType>
- <xref:System.Drawing.Drawing2D.HatchBrush?displayProperty=nameWithType>
- <xref:System.Drawing.TextureBrush?displayProperty=nameWithType>
- <xref:System.Drawing.Drawing2D.LinearGradientBrush?displayProperty=nameWithType>
- [Lignes, courbes et formes](lines-curves-and-shapes.md)
- [Guide pratique pour Dessiner un Rectangle rempli dans un formulaire Windows](how-to-draw-a-filled-rectangle-on-a-windows-form.md)
- [Guide pratique pour Dessiner une Ellipse remplie dans un formulaire Windows](how-to-draw-a-filled-ellipse-on-a-windows-form.md)
