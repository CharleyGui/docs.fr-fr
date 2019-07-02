---
title: Stylets, lignes et rectangles dans GDI+
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- lines
- GDI+, lines
- drawing [Windows Forms], rectangles
- rectangles
- drawing [Windows Forms], lines
- GDI+, pens
- examples [Windows Forms], drawing lines and shapes
- examples [Windows Forms], pens
- GDI+, rectangles
- examples [Windows Forms], GDI+
- lines [Windows Forms], dashed
ms.assetid: 30b25aae-e3eb-4479-bdb8-187cf651fc84
ms.openlocfilehash: 06d2351ffa7d7f009d7b049f4689df7038b4d202
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67505352"
---
# <a name="pens-lines-and-rectangles-in-gdi"></a>Stylets, lignes et rectangles dans GDI+
Pour dessiner des lignes avec GDI + vous devez créer un <xref:System.Drawing.Graphics> objet et un <xref:System.Drawing.Pen> objet. Le <xref:System.Drawing.Graphics> objet fournit les méthodes qui effectuent réellement le dessin, et le <xref:System.Drawing.Pen> objet stocke les attributs, tels que la couleur de ligne, la largeur et le style.  
  
## <a name="drawing-a-line"></a>Dessiner une ligne  
 Pour dessiner une ligne, appelez le <xref:System.Drawing.Graphics.DrawLine%2A> méthode de la <xref:System.Drawing.Graphics> objet. Le <xref:System.Drawing.Pen> objet est passé en tant qu’arguments à la <xref:System.Drawing.Graphics.DrawLine%2A> (méthode). L’exemple suivant dessine une ligne à partir du point (4, 2) au point (12, 6) :  
  
 [!code-csharp[LinesCurvesAndShapes#41](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#41)]
 [!code-vb[LinesCurvesAndShapes#41](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#41)]  
  
 <xref:System.Drawing.Graphics.DrawLine%2A> est une méthode surchargée de la <xref:System.Drawing.Graphics> classe, il existe plusieurs façons, vous pouvez lui fournir arguments. Par exemple, vous pouvez construire deux <xref:System.Drawing.Point> objets et passez le <xref:System.Drawing.Point> en tant qu’arguments à la <xref:System.Drawing.Graphics.DrawLine%2A> méthode :  
  
 [!code-csharp[LinesCurvesAndShapes#42](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#42)]
 [!code-vb[LinesCurvesAndShapes#42](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#42)]  
  
## <a name="constructing-a-pen"></a>Construction d’un stylet  
 Vous pouvez spécifier certains attributs lorsque vous construisez un <xref:System.Drawing.Pen> objet. Par exemple, un `Pen` constructeur vous permet de spécifier la couleur et la largeur. L’exemple suivant dessine une ligne bleue de largeur 2 à partir de (0, 0) à (60, 30) :  
  
 [!code-csharp[LinesCurvesAndShapes#43](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#43)]
 [!code-vb[LinesCurvesAndShapes#43](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#43)]  
  
## <a name="dashed-lines-and-line-caps"></a>Lignes en pointillés et embouts de ligne  
 Le <xref:System.Drawing.Pen> objet expose également des propriétés, telles que <xref:System.Drawing.Pen.DashStyle%2A>, que vous pouvez utiliser pour spécifier les fonctionnalités de la ligne. L’exemple suivant dessine une ligne en pointillés à partir de (100, 50) à (300, 80) :  
  
 [!code-csharp[LinesCurvesAndShapes#44](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#44)]
 [!code-vb[LinesCurvesAndShapes#44](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#44)]  
  
 Vous pouvez utiliser les propriétés de la <xref:System.Drawing.Pen> objet à définir beaucoup d’autres attributs de la ligne. Le <xref:System.Drawing.Pen.StartCap%2A> et <xref:System.Drawing.Pen.EndCap%2A> propriétés spécifient l’apparence des extrémités de la ligne ; les extrémités peuvent être plat, carré, arrondi, triangulaire, ou une forme personnalisée. Le <xref:System.Drawing.Pen.LineJoin%2A> propriété vous permet de spécifier si les lignes reliées entre elles forment (jointes avec des angles aigus), en relief, arrondis ou découpés. L’illustration suivante montre les lignes avec différents styles d’extrémité et de jointure.  
  
 ![Lines](./media/aboutgdip02-art04.gif "Aboutgdip02_art04")  
  
## <a name="drawing-a-rectangle"></a>Dessin d’un Rectangle  
 Dessiner des rectangles avec GDI + est similaire au dessin de lignes. Pour dessiner un rectangle, vous avez besoin une <xref:System.Drawing.Graphics> objet et un <xref:System.Drawing.Pen> objet. Le <xref:System.Drawing.Graphics> objet fournit un <xref:System.Drawing.Graphics.DrawRectangle%2A> (méthode) et le <xref:System.Drawing.Pen> objet stocke les attributs, tels que la largeur de ligne et la couleur. Le <xref:System.Drawing.Pen> objet est passé en tant qu’arguments à la <xref:System.Drawing.Graphics.DrawRectangle%2A> (méthode). L’exemple suivant dessine un rectangle avec son coin supérieur gauche à (100, 50), une largeur de 80 et une hauteur de 40 :  
  
 [!code-csharp[LinesCurvesAndShapes#45](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#45)]
 [!code-vb[LinesCurvesAndShapes#45](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#45)]  
  
 <xref:System.Drawing.Graphics.DrawRectangle%2A> est une méthode surchargée de la <xref:System.Drawing.Graphics> classe, il existe plusieurs façons, vous pouvez lui fournir arguments. Par exemple, vous pouvez construire un <xref:System.Drawing.Rectangle> de l’objet et de transmettre le <xref:System.Drawing.Rectangle> de l’objet à la <xref:System.Drawing.Graphics.DrawRectangle%2A> méthode en tant qu’argument :  
  
 [!code-csharp[LinesCurvesAndShapes#46](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#46)]
 [!code-vb[LinesCurvesAndShapes#46](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#46)]  
  
 Un <xref:System.Drawing.Rectangle> objet possède des méthodes et propriétés permettant de manipuler et de collecter des informations sur le rectangle. Par exemple, le <xref:System.Drawing.Rectangle.Inflate%2A> et <xref:System.Drawing.Rectangle.Offset%2A> les méthodes de modifier la taille et la position du rectangle. Le <xref:System.Drawing.Rectangle.IntersectsWith%2A> méthode vous indique si le rectangle coupe un rectangle donné et la <xref:System.Drawing.Rectangle.Contains%2A> méthode vous indique si un point donné se trouve à l’intérieur du rectangle.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Drawing.Graphics?displayProperty=nameWithType>
- <xref:System.Drawing.Pen?displayProperty=nameWithType>
- <xref:System.Drawing.Rectangle?displayProperty=nameWithType>
- [Guide pratique pour Créer un stylet](how-to-create-a-pen.md)
- [Guide pratique pour Dessiner une ligne dans un formulaire Windows](how-to-draw-a-line-on-a-windows-form.md)
- [Guide pratique pour Dessiner une forme avec contour](how-to-draw-an-outlined-shape.md)
