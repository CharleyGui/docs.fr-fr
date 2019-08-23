---
title: 'Procédure : créer un dégradé de tracé'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- path gradients [Windows Forms], creating
- gradients [Windows Forms], creating path
- graphics paths [Windows Forms], creating gradient
ms.assetid: 1948e834-e104-481c-b71d-d8aa9e4d106e
ms.openlocfilehash: 8399a56fca87704e10456a4cf8109d7c80d4db45
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964400"
---
# <a name="how-to-create-a-path-gradient"></a>Procédure : créer un dégradé de tracé
La <xref:System.Drawing.Drawing2D.PathGradientBrush> classe vous permet de personnaliser la façon dont vous remplissez une forme avec des couleurs à variation progressive. Par exemple, vous pouvez spécifier une couleur pour le centre d’un tracé et une autre couleur pour la limite d’un tracé. Vous pouvez également spécifier des couleurs distinctes pour chacun des points situés le long de la limite d’un tracé.  
  
> [!NOTE]
> Dans GDI+, un chemin d’accès est une séquence de lignes et de courbes <xref:System.Drawing.Drawing2D.GraphicsPath> gérée par un objet. Pour plus d’informations sur les chemins d’accès GDI+, consultez chemins d’accès [graphiques dans GDI+](graphics-paths-in-gdi.md) et [création et dessin de chemins d’accès](constructing-and-drawing-paths.md).  

Les exemples de cet article sont des méthodes qui sont appelées à partir <xref:System.Windows.Forms.Control.Paint> du gestionnaire d’événements d’un contrôle.  

### <a name="to-fill-an-ellipse-with-a-path-gradient"></a>Pour remplir une ellipse avec un dégradé de tracé  
  
- L’exemple suivant remplit une ellipse avec un pinceau de dégradé de tracé. La couleur centrale est définie sur bleu et la couleur limite est cyan. L’illustration suivante montre l’Ellipse remplie.  
  
     ![Le tracé du dégradé remplit une ellipse.](./media/how-to-create-a-path-gradient/gradient-path-filled-ellipse.png)  
  
     Par défaut, un pinceau de dégradé de tracé ne s’étend pas en dehors de la limite du tracé. Si vous utilisez le pinceau de dégradé de tracé pour remplir une figure qui s’étend au-delà de la limite du tracé, la zone de l’écran à l’extérieur du tracé n’est pas remplie.  
  
     L’illustration suivante montre ce qui se passe si vous <xref:System.Drawing.Graphics.FillEllipse%2A?displayProperty=nameWithType> remplacez l’appel dans le code `e.Graphics.FillRectangle(pthGrBrush, 0, 10, 200, 40)`suivant par:  
  
     ![Tracé de dégradé étendu au-delà de la limite du tracé.](./media/how-to-create-a-path-gradient/gradient-path-extended-beyond-boundary.png)  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#11)]
     [!code-vb[System.Drawing.UsingaGradientBrush#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#11)]  
  
     L’exemple de code précédent est conçu pour une utilisation avec Windows Forms et requiert l' <xref:System.Windows.Forms.PaintEventArgs> e, qui est un paramètre de <xref:System.Windows.Forms.PaintEventHandler>.  
  
### <a name="to-specify-points-on-the-boundary"></a>Pour spécifier des points sur la limite  
  
- L’exemple suivant construit un pinceau de dégradé de tracé à partir d’un tracé en forme d’étoile. Le code définit la <xref:System.Drawing.Drawing2D.PathGradientBrush.CenterColor%2A> propriété, qui définit la couleur du centre de l’étoile sur rouge. Ensuite, le code définit <xref:System.Drawing.Drawing2D.PathGradientBrush.SurroundColors%2A> la propriété pour spécifier différentes couleurs (stockées dans `colors` le tableau) aux points `points` individuels du tableau. L’instruction de code finale remplit le tracé en forme d’étoile avec le pinceau de dégradé du tracé.  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#12)]
     [!code-vb[System.Drawing.UsingaGradientBrush#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#12)]  
  
- L’exemple suivant dessine un dégradé de tracé <xref:System.Drawing.Drawing2D.GraphicsPath> sans objet dans le code. Le constructeur <xref:System.Drawing.Drawing2D.PathGradientBrush.%23ctor%2A> particulier de l’exemple reçoit un tableau de points, mais ne requiert pas <xref:System.Drawing.Drawing2D.GraphicsPath> d’objet. Notez également que <xref:System.Drawing.Drawing2D.PathGradientBrush> est utilisé pour remplir un rectangle, et non un tracé. Le rectangle est plus grand que le tracé fermé utilisé pour définir le pinceau. par conséquent, une partie du rectangle n’est pas peinte par le pinceau. L’illustration suivante montre le rectangle (ligne en pointillés) et la partie du rectangle peinte par le pinceau de dégradé de tracé: 
  
     ![Partie de dégradé peinte par le pinceau de dégradé de tracé.](./media/how-to-create-a-path-gradient/gradient-painted-path-gradient-brush.png)  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#13](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#13)]
     [!code-vb[System.Drawing.UsingaGradientBrush#13](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#13)]  
  
### <a name="to-customize-a-path-gradient"></a>Pour personnaliser un dégradé de tracé  
  
- Pour personnaliser un pinceau de dégradé de tracé, vous pouvez définir <xref:System.Drawing.Drawing2D.PathGradientBrush.FocusScales%2A> sa propriété. Les échelles de focus spécifient un chemin d’accès interne qui se trouve à l’intérieur du chemin d’accès principal. La couleur centrale est affichée partout à l’intérieur de ce tracé interne et non uniquement au point central.  
  
     L’exemple suivant crée un pinceau de dégradé de tracé basé sur un tracé elliptique. Le code définit la couleur de la limite sur bleu, définit la couleur centrale en cyan, puis utilise le pinceau de dégradé du tracé pour remplir le tracé elliptique.  
  
     Ensuite, le code définit les échelles de focus du pinceau de dégradé du tracé. L’échelle de focus x est définie sur 0,3, et l’échelle de focus y est définie sur 0,8. Le code appelle la <xref:System.Drawing.Graphics.TranslateTransform%2A> méthode d’un <xref:System.Drawing.Graphics> objet afin <xref:System.Drawing.Graphics.FillPath%2A> que l’appel suivant remplisse une ellipse qui se trouve à droite de la première ellipse.  
  
     Pour voir l’effet des échelles de focus, Imaginez une petite Ellipse qui partage son centre avec l’ellipse principale. La petite ellipse (interne) est l’ellipse principale mise à l’échelle (à propos de son centre) horizontalement par un facteur de 0,3 et verticalement par un facteur de 0,8. Lorsque vous passez de la limite de l’ellipse externe à la limite de l’ellipse interne, la couleur passe progressivement du bleu au cyan. Lorsque vous passez de la limite de l’ellipse interne au centre partagé, la couleur reste cyan.  
  
     L'illustration suivante montre la sortie du code suivant. L’ellipse sur la gauche est Aqua uniquement au point central. L’ellipse située à droite est Aqua partout dans le chemin interne.  
  
 ![Effet dégradé des échelles de focus](./media/how-to-create-a-path-gradient/focus-scales-aqua-inner-outer-ellipse.png)  
  
 [!code-csharp[System.Drawing.UsingaGradientBrush#14](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#14)]
 [!code-vb[System.Drawing.UsingaGradientBrush#14](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#14)]  
  
### <a name="to-customize-with-interpolation"></a>Pour personnaliser avec l’interpolation  
  
- Une autre façon de personnaliser un pinceau de dégradé de tracé consiste à spécifier un tableau de couleurs d’interpolation et un tableau de positions d’interpolation.  
  
     L’exemple suivant crée un pinceau de dégradé de tracé basé sur un triangle. Le code définit la <xref:System.Drawing.Drawing2D.PathGradientBrush.InterpolationColors%2A> propriété du pinceau de dégradé de tracé pour spécifier un tableau de couleurs d’interpolation (vert foncé, cyan, bleu) et un tableau de positions d’interpolation (0, 0,25, 1). Lorsque vous passez de la limite du triangle au point central, la couleur passe progressivement du vert foncé au cyan, puis de l’Aqua au bleu. Le changement du vert foncé au cyan se produit à 25% de la distance du vert foncé au bleu.  
  
     L’illustration suivante montre le triangle rempli avec le pinceau dégradé de tracé personnalisé.  
  
     ![Triangle rempli avec le pinceau dégradé de tracé personnalisé.](./media/how-to-create-a-path-gradient/gradient-brush-filled-triangle.png)  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#15](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#15)]
     [!code-vb[System.Drawing.UsingaGradientBrush#15](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#15)]  
  
### <a name="to-set-the-center-point"></a>Pour définir le point central  
  
- Par défaut, le point central d’un pinceau de dégradé de tracé est au centre de gravité du tracé utilisé pour construire le pinceau. Vous pouvez modifier l’emplacement du point central en définissant la <xref:System.Drawing.Drawing2D.PathGradientBrush.CenterPoint%2A> propriété de la <xref:System.Drawing.Drawing2D.PathGradientBrush> classe.  
  
     L’exemple suivant crée un pinceau de dégradé de tracé basé sur une ellipse. Le centre de l’ellipse est à (70, 35), mais le point central du pinceau de dégradé du tracé est défini sur (120, 40).  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#16](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#16)]
     [!code-vb[System.Drawing.UsingaGradientBrush#16](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#16)]  
  
     L’illustration suivante montre l’Ellipse remplie et le point central du pinceau de dégradé de tracé:  
  
     ![Tracé de dégradé avec Ellipse remplie et point central.](./media/how-to-create-a-path-gradient/gradient-path-filled-ellipse-center-point.png)  
  
- Vous pouvez définir le point central d’un pinceau de dégradé de tracé sur un emplacement en dehors du tracé utilisé pour construire le pinceau. L’exemple suivant remplace l’appel à la définition <xref:System.Drawing.Drawing2D.PathGradientBrush.CenterPoint%2A> de la propriété dans le code précédent.  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#17](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#17)]
     [!code-vb[System.Drawing.UsingaGradientBrush#17](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#17)]  
  
     L’illustration suivante montre la sortie avec cette modification:  
  
     ![Tracé du dégradé avec point central à l’extérieur du tracé.](./media/how-to-create-a-path-gradient/gradient-path-center-point-outside.png)  
  
     Dans l’illustration précédente, les points situés à l’extrême droite de l’ellipse ne sont pas des bleus purs (bien qu’ils soient très proches). Les couleurs du dégradé sont positionnées comme si le remplissage atteigne le point (145, 35) où la couleur serait le bleu pur (255 0,0). Mais le remplissage n’atteint jamais (145, 35), car un pinceau de dégradé de tracé peint uniquement à l’intérieur de son tracé.  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Les exemples précédents sont conçus pour être utilisés avec Windows Forms, et ils <xref:System.Windows.Forms.PaintEventArgs> requièrent `e`, qui <xref:System.Windows.Forms.Control.Paint> est un paramètre du gestionnaire d’événements.  
  
## <a name="see-also"></a>Voir aussi

- [Utilisation d'un pinceau à dégradé pour remplir des formes](using-a-gradient-brush-to-fill-shapes.md)
