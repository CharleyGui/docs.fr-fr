---
title: Vue d'ensemble des graphismes vectoriels
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- inclusive-inclusive endpoints
- coordinate systems
- graphics [Windows Forms], vector graphics
ms.assetid: 0195df81-66be-452d-bb53-5a582ebfdc09
ms.openlocfilehash: 64bec47a186b08298a49c6f188795d1b51d234eb
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67505243"
---
# <a name="vector-graphics-overview"></a>Vue d'ensemble des graphismes vectoriels
GDI + dessine les lignes, rectangles et autres formes sur un système de coordonnées. Vous pouvez choisir parmi un éventail de systèmes de coordonnées, mais le système de coordonnées par défaut a l’origine dans le coin supérieur gauche avec l’axe des x pointant vers la droite et l’axe des y pointant vers le bas. L’unité de mesure dans le système de coordonnées par défaut est le pixel.  
  
## <a name="the-building-blocks-of-gdi"></a>Blocs de construction de GDI +  
 ![Graphique vectoriel](./media/aboutgdip02-art01.gif "AboutGdip02_Art01")  
  
 Un moniteur d’ordinateur crée son affichage sur un tableau rectangulaire de points appelés pixels. Le nombre de pixels qui apparaissent sur l’écran varie d’un moniteur à l’autre, et le nombre de pixels qui apparaissent sur un seul écran peut généralement être configuré dans une certaine mesure par l’utilisateur.  
  
 ![Graphique vectoriel](./media/aboutgdip02-art02.gif "AboutGdip02_Art02")  
  
 Lorsque vous utilisez GDI + pour dessiner une ligne, un rectangle ou une courbe, vous fournissez des informations essentielles sur l’élément à dessiner. Par exemple, vous pouvez spécifier une ligne en fournissant deux points, et vous pouvez spécifier un rectangle en fournissant un point, une hauteur et une largeur. GDI + fonctionne conjointement avec le logiciel de pilote d’affichage pour déterminer quels pixels doivent être activées pour afficher la ligne, un rectangle ou une courbe. L’illustration suivante montre les pixels qui sont sous tension pour afficher une ligne à partir du point (4, 2) au point (12, 8).  
  
 ![Graphique vectoriel](./media/aboutgdip02-art03.gif "AboutGdip02_Art03")  
  
 Au fil du temps, certains blocs de construction se sont avérées les plus utiles pour la création d’images à deux dimensions. Ces blocs de construction, qui sont toutes prises en charge par GDI +, sont indiqués dans la liste suivante :  
  
- Lignes  
  
- Rectangles  
  
- Points de suspension  
  
- Arcs  
  
- Polygones  
  
- Splines cardinales  
  
- splines de Bézier  
  
## <a name="methods-for-drawing-with-a-graphics-object"></a>Méthodes de dessin à un objet Graphics  
 Le <xref:System.Drawing.Graphics> classe dans GDI + fournit les méthodes suivantes pour dessiner les éléments de la liste précédente : <xref:System.Drawing.Graphics.DrawLine%2A>, <xref:System.Drawing.Graphics.DrawRectangle%2A>, <xref:System.Drawing.Graphics.DrawEllipse%2A>, <xref:System.Drawing.Graphics.DrawPolygon%2A>, <xref:System.Drawing.Graphics.DrawArc%2A>, <xref:System.Drawing.Graphics.DrawCurve%2A> (pour les splines cardinales) et <xref:System.Drawing.Graphics.DrawBezier%2A>. Chacune de ces méthodes est surchargée ; Autrement dit, chaque méthode prend en charge différentes listes de paramètres. Par exemple, une variante de la <xref:System.Drawing.Graphics.DrawLine%2A> méthode reçoit un <xref:System.Drawing.Pen> objet et quatre entiers, lors d’une autre variante de la <xref:System.Drawing.Graphics.DrawLine%2A> méthode reçoit un <xref:System.Drawing.Pen> objet et deux <xref:System.Drawing.Point> objets.  
  
 Les méthodes pour dessiner des lignes, des rectangles et des splines de Bézier ont des méthodes au pluriel qui dessinent plusieurs éléments dans un seul appel : <xref:System.Drawing.Graphics.DrawLines%2A>, <xref:System.Drawing.Graphics.DrawRectangles%2A>, et <xref:System.Drawing.Graphics.DrawBeziers%2A>. En outre, le <xref:System.Drawing.Graphics.DrawCurve%2A> méthode a une méthode d’accompagnement, <xref:System.Drawing.Graphics.DrawClosedCurve%2A>, que le point d’une courbe en connectant le point de fin de la courbe de début se ferme.  
  
 Toutes les méthodes de dessin de le <xref:System.Drawing.Graphics> classe fonctionnent conjointement avec un <xref:System.Drawing.Pen> objet. Pour dessiner quoi que ce soit, vous devez créer au moins deux objets : un <xref:System.Drawing.Graphics> objet et un <xref:System.Drawing.Pen> objet. Le <xref:System.Drawing.Pen> objet stocke les attributs, tels que la largeur de ligne et de couleur, de l’élément à dessiner. Le <xref:System.Drawing.Pen> objet est passé comme argument à la méthode de dessin. Par exemple, une variante de la <xref:System.Drawing.Graphics.DrawLine%2A> méthode reçoit un <xref:System.Drawing.Pen> objet et quatre entiers comme indiqué dans l’exemple suivant, qui dessine un rectangle avec une largeur de 100 et une hauteur de 50 un coin supérieur gauche de (20, 10) :  
  
 [!code-csharp[LinesCurvesAndShapes#11](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#11)]
 [!code-vb[LinesCurvesAndShapes#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#11)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Drawing.Graphics?displayProperty=nameWithType>
- <xref:System.Drawing.Pen?displayProperty=nameWithType>
- [Lignes, courbes et formes](lines-curves-and-shapes.md)
- [Guide pratique pour Créer des objets graphiques pour le dessin](how-to-create-graphics-objects-for-drawing.md)
