---
title: 'Comment : créer un dégradé de tracé'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- path gradients [Windows Forms], creating
- gradients [Windows Forms], creating path
- graphics paths [Windows Forms], creating gradient
ms.assetid: 1948e834-e104-481c-b71d-d8aa9e4d106e
ms.openlocfilehash: cf4dc558c008fb8adfc327a6a894a428e985df03
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182632"
---
# <a name="how-to-create-a-path-gradient"></a>Comment : créer un dégradé de tracé
La <xref:System.Drawing.Drawing2D.PathGradientBrush> classe vous permet de personnaliser la façon dont vous remplissez une forme avec des couleurs changeantes progressivement. Par exemple, vous pouvez spécifier une couleur pour le centre d’un chemin et une autre couleur pour la limite d’un chemin. Vous pouvez également spécifier des couleurs séparées pour chacun de plusieurs points le long de la limite d’un chemin.  
  
> [!NOTE]
> Dans GDIMD, un chemin est une séquence de <xref:System.Drawing.Drawing2D.GraphicsPath> lignes et de courbes maintenues par un objet. Pour plus d’informations sur les chemins GDIMD, voir [Graphics Paths in GDIMD](graphics-paths-in-gdi.md) et [Constructing and Drawing Paths](constructing-and-drawing-paths.md).  

Les exemples de cet article sont des <xref:System.Windows.Forms.Control.Paint> méthodes qui sont appelées à partir du gestionnaire d’événements d’un contrôle.  

### <a name="to-fill-an-ellipse-with-a-path-gradient"></a>Pour remplir une ellipse avec un gradient de chemin  
  
- L’exemple suivant remplit une ellipse d’un pinceau de gradient de chemin. La couleur centrale est réglée au bleu et la couleur limite est réglée à l’aqua. L’illustration suivante montre l’ellipse remplie.  
  
     ![Gradient Path remplit une ellipse.](./media/how-to-create-a-path-gradient/gradient-path-filled-ellipse.png)  
  
     Par défaut, une brosse de gradient de chemin ne s’étend pas à l’extérieur de la limite du chemin. Si vous utilisez la brosse de gradient de chemin pour remplir une figure qui s’étend au-delà de la limite du chemin, la zone de l’écran en dehors du chemin ne sera pas remplie.  
  
     L’illustration suivante montre ce <xref:System.Drawing.Graphics.FillEllipse%2A?displayProperty=nameWithType> qui se passe `e.Graphics.FillRectangle(pthGrBrush, 0, 10, 200, 40)`si vous modifiez l’appel dans le code suivant pour :  
  
     ![Chemin gradient étendu au-delà de la frontière du chemin.](./media/how-to-create-a-path-gradient/gradient-path-extended-beyond-boundary.png)  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#11)]
     [!code-vb[System.Drawing.UsingaGradientBrush#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#11)]  
  
     L’exemple de code précédent est conçu pour <xref:System.Windows.Forms.PaintEventArgs> une utilisation avec windows <xref:System.Windows.Forms.PaintEventHandler>Forms, et il nécessite le e, qui est un paramètre de .  
  
### <a name="to-specify-points-on-the-boundary"></a>Pour spécifier les points sur la limite  
  
- L’exemple suivant construit un pinceau de gradient de chemin à partir d’un chemin en forme d’étoile. Le code <xref:System.Drawing.Drawing2D.PathGradientBrush.CenterColor%2A> définit la propriété, qui définit la couleur au centroïde de l’étoile en rouge. Ensuite, le <xref:System.Drawing.Drawing2D.PathGradientBrush.SurroundColors%2A> code définit la propriété pour `colors` spécifier différentes `points` couleurs (stockées dans le tableau) aux points individuels dans le tableau. L’énoncé de code final remplit le chemin en forme d’étoile avec le pinceau de gradient de chemin.  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#12)]
     [!code-vb[System.Drawing.UsingaGradientBrush#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#12)]  
  
- L’exemple suivant dessine un <xref:System.Drawing.Drawing2D.GraphicsPath> gradient de chemin sans objet dans le code. Le <xref:System.Drawing.Drawing2D.PathGradientBrush.%23ctor%2A> constructeur particulier dans l’exemple reçoit un tableau <xref:System.Drawing.Drawing2D.GraphicsPath> de points, mais ne nécessite pas d’objet. Aussi, notez <xref:System.Drawing.Drawing2D.PathGradientBrush> que le est utilisé pour remplir un rectangle, pas un chemin. Le rectangle est plus grand que le chemin fermé utilisé pour définir le pinceau, de sorte qu’une partie du rectangle n’est pas peinte par le pinceau. L’illustration suivante montre le rectangle (ligne pointillée) et la partie du rectangle peinte par le pinceau de gradient de chemin :
  
     ![Partie gradient peinte par le pinceau de gradient de chemin.](./media/how-to-create-a-path-gradient/gradient-painted-path-gradient-brush.png)  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#13](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#13)]
     [!code-vb[System.Drawing.UsingaGradientBrush#13](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#13)]  
  
### <a name="to-customize-a-path-gradient"></a>Personnaliser un gradient de chemin  
  
- Une façon de personnaliser un pinceau de <xref:System.Drawing.Drawing2D.PathGradientBrush.FocusScales%2A> gradient de chemin est de régler sa propriété. Les échelles de mise au point spécifier un chemin intérieur qui se trouve à l’intérieur du chemin principal. La couleur centrale est affichée partout à l’intérieur de ce chemin intérieur plutôt qu’au point central.  
  
     L’exemple suivant crée un pinceau de gradient de chemin basé sur un chemin elliptique. Le code définit la couleur limite en bleu, définit la couleur centrale à l’aqua, puis utilise le pinceau de gradient de chemin pour remplir le chemin elliptique.  
  
     Ensuite, le code définit les échelles de mise au point de la brosse de gradient de chemin. L’échelle de mise au point x est réglée à 0,3, et l’échelle de mise au point y est réglée à 0,8. Le code <xref:System.Drawing.Graphics.TranslateTransform%2A> appelle la <xref:System.Drawing.Graphics> méthode d’un <xref:System.Drawing.Graphics.FillPath%2A> objet de sorte que l’appel suivant pour remplir une ellipse qui se trouve à droite de la première ellipse.  
  
     Pour voir l’effet des échelles de mise au point, imaginez une petite ellipse qui partage son centre avec l’ellipse principale. La petite ellipse (intérieure) est l’ellipse principale écaillée (environ son centre) horizontalement par un facteur de 0,3 et verticalement par un facteur de 0,8. Comme vous vous déplacez de la limite de l’ellipse externe à la limite de l’ellipse intérieure, la couleur change progressivement du bleu à l’aqua. Comme vous vous déplacez de la limite de l’ellipse intérieure au centre partagé, la couleur reste aqua.  
  
     L'illustration suivante montre la sortie du code suivant. L’ellipse sur la gauche est aqua seulement au point central. L’ellipse sur la droite est aqua partout à l’intérieur du chemin intérieur.  
  
 ![Effet gradient des échelles de mise au point](./media/how-to-create-a-path-gradient/focus-scales-aqua-inner-outer-ellipse.png)  
  
 [!code-csharp[System.Drawing.UsingaGradientBrush#14](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#14)]
 [!code-vb[System.Drawing.UsingaGradientBrush#14](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#14)]  
  
### <a name="to-customize-with-interpolation"></a>Personnaliser avec l’interpolation  
  
- Une autre façon de personnaliser un pinceau de gradient de chemin est de spécifier une gamme de couleurs d’interpolation et un tableau de positions d’interpolation.  
  
     L’exemple suivant crée un pinceau de gradient de chemin basé sur un triangle. Le code <xref:System.Drawing.Drawing2D.PathGradientBrush.InterpolationColors%2A> définit la propriété du pinceau de gradient de chemin pour spécifier un tableau de couleurs d’interpolation (vert foncé, aqua, bleu) et un tableau de positions d’interpolation (0, 0.25, 1). Comme vous vous déplacez de la limite du triangle au point central, la couleur change progressivement du vert foncé à l’aqua, puis de l’aqua au bleu. Le passage du vert foncé à l’aqua se produit dans 25 pour cent de la distance du vert foncé au bleu.  
  
     L’illustration suivante montre le triangle rempli de la brosse de gradient de chemin personnalisé.  
  
     ![Triangle rempli de brosse de gradient de chemin personnalisé.](./media/how-to-create-a-path-gradient/gradient-brush-filled-triangle.png)  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#15](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#15)]
     [!code-vb[System.Drawing.UsingaGradientBrush#15](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#15)]  
  
### <a name="to-set-the-center-point"></a>Pour définir le point central  
  
- Par défaut, le point central d’une brosse de gradient de chemin est au centroid du chemin utilisé pour construire la brosse. Vous pouvez modifier l’emplacement du <xref:System.Drawing.Drawing2D.PathGradientBrush.CenterPoint%2A> point central <xref:System.Drawing.Drawing2D.PathGradientBrush> en définissant la propriété de la classe.  
  
     L’exemple suivant crée un pinceau de gradient de chemin basé sur une ellipse. Le centre de l’ellipse est à (70, 35), mais le point central de la brosse de gradient de chemin est réglé à (120, 40).  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#16](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#16)]
     [!code-vb[System.Drawing.UsingaGradientBrush#16](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#16)]  
  
     L’illustration suivante montre l’ellipse remplie et le point central du pinceau de gradient de chemin :  
  
     ![Chemin gradient avec ellipse remplie et point central.](./media/how-to-create-a-path-gradient/gradient-path-filled-ellipse-center-point.png)  
  
- Vous pouvez définir le point central d’un pinceau de gradient de chemin à un endroit en dehors du chemin qui a été employé pour construire la brosse. L’exemple suivant remplace l’appel pour définir la <xref:System.Drawing.Drawing2D.PathGradientBrush.CenterPoint%2A> propriété dans le code précédent.  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#17](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#17)]
     [!code-vb[System.Drawing.UsingaGradientBrush#17](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#17)]  
  
     L’illustration suivante montre la sortie avec ce changement :  
  
     ![Chemin Gradient avec point central en dehors du chemin.](./media/how-to-create-a-path-gradient/gradient-path-center-point-outside.png)  
  
     Dans l’illustration précédente, les points à l’extrême droite de l’ellipse ne sont pas purs bleus (bien qu’ils soient très proches). Les couleurs du gradient sont positionnées comme si le remplissage atteignait le point (145, 35) où la couleur serait bleu pur (0, 0, 255). Mais le remplissage n’atteint jamais (145, 35) parce qu’un pinceau de gradient de chemin peint seulement à l’intérieur de son chemin.  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Les exemples précédents sont conçus pour une <xref:System.Windows.Forms.PaintEventArgs> `e`utilisation avec windows <xref:System.Windows.Forms.Control.Paint> Forms, et ils nécessitent , qui est un paramètre du gestionnaire d’événements.  
  
## <a name="see-also"></a>Voir aussi

- [Utilisation d'un pinceau à dégradé pour remplir des formes](using-a-gradient-brush-to-fill-shapes.md)
