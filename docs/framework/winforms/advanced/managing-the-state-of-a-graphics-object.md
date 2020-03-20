---
title: Gestion de l'état d'un objet graphique
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [Windows Forms], managing state
- graphics [Windows Forms], clipping
ms.assetid: 6207cad1-7a34-4bd6-bfc1-db823ca7a73e
ms.openlocfilehash: d1e7e6eac775ca779fb68605adcc9bc2b9915e49
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182455"
---
# <a name="managing-the-state-of-a-graphics-object"></a>Gestion de l'état d'un objet graphique
La <xref:System.Drawing.Graphics> classe est au cœur de GDI. Pour dessiner quoi que <xref:System.Drawing.Graphics> ce soit, vous obtenez <xref:System.Drawing.Graphics.DrawLine%2A>un <xref:System.Drawing.Graphics.DrawImage%2A> <xref:System.Drawing.Graphics.DrawString%2A>objet, définissez ses propriétés, et appelez ses méthodes, , , et autres).  
  
 L’exemple suivant <xref:System.Drawing.Graphics.DrawRectangle%2A> appelle <xref:System.Drawing.Graphics> la méthode d’un objet. Le premier argument <xref:System.Drawing.Graphics.DrawRectangle%2A> transmis à <xref:System.Drawing.Pen> la méthode est un objet.  
  
```vb  
Dim graphics As Graphics = e.Graphics  
Dim pen As New Pen(Color.Blue) ' Opaque blue  
graphics.DrawRectangle(pen, 10, 10, 200, 100)  
```  
  
```csharp  
Graphics graphics = e.Graphics;  
Pen pen = new Pen(Color.Blue);  // Opaque blue  
graphics.DrawRectangle(pen, 10, 10, 200, 100);  
```  
  
## <a name="graphics-state"></a>État graphique  
 Un <xref:System.Drawing.Graphics> objet fait plus que fournir <xref:System.Drawing.Graphics.DrawLine%2A> <xref:System.Drawing.Graphics.DrawRectangle%2A>des méthodes de dessin, telles que et . Un <xref:System.Drawing.Graphics> objet maintient également l’état graphique, qui peut être divisé en catégories suivantes :  
  
- Paramètres de qualité  
  
- Transformations  
  
- Région de clipping  
  
### <a name="quality-settings"></a>Paramètres de qualité  
 Un <xref:System.Drawing.Graphics> objet a plusieurs propriétés qui influencent la qualité des éléments qui sont dessinés. Par exemple, vous <xref:System.Drawing.Graphics.TextRenderingHint%2A> pouvez définir la propriété pour spécifier le type d’anti-application (le cas échéant) appliqué au texte. D’autres propriétés <xref:System.Drawing.Graphics.SmoothingMode%2A> <xref:System.Drawing.Graphics.CompositingMode%2A>qui <xref:System.Drawing.Graphics.CompositingQuality%2A>influencent la qualité sont , , , et <xref:System.Drawing.Graphics.InterpolationMode%2A>.  
  
 L’exemple suivant attire deux ellipses, l’une avec le mode de lissage réglé <xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias> et l’autre avec le mode de lissage réglé pour <xref:System.Drawing.Drawing2D.SmoothingMode.HighSpeed>:  
  
```vb  
Dim graphics As Graphics = e.Graphics  
Dim pen As New Pen(Color.Blue)  
  
graphics.SmoothingMode = SmoothingMode.AntiAlias  
graphics.DrawEllipse(pen, 0, 0, 200, 100)  
graphics.SmoothingMode = SmoothingMode.HighSpeed  
graphics.DrawEllipse(pen, 0, 150, 200, 100)  
```  
  
```csharp  
Graphics graphics = e.Graphics;  
Pen pen = new Pen(Color.Blue);  
  
graphics.SmoothingMode = SmoothingMode.AntiAlias;  
graphics.DrawEllipse(pen, 0, 0, 200, 100);  
graphics.SmoothingMode = SmoothingMode.HighSpeed;  
graphics.DrawEllipse(pen, 0, 150, 200, 100);  
```  
  
### <a name="transformations"></a>Transformations  
 Un <xref:System.Drawing.Graphics> objet maintient deux transformations (monde et page) qui <xref:System.Drawing.Graphics> sont appliquées à tous les éléments dessinés par cet objet. Toute transformation affine peut être stockée dans la transformation du monde. Les transformations d’affine incluent l’échelle, la rotation, le reflet, la biais et la traduction. La transformation de la page peut être utilisée pour la mise à l’échelle et pour changer d’unités (par exemple, pixels en pouces). Pour plus d’informations, voir [Systèmes de coordination et transformations](coordinate-systems-and-transformations.md).  
  
 L’exemple suivant définit le monde <xref:System.Drawing.Graphics> et les transformations de page d’un objet. La transformation mondiale est définie à une rotation de 30 degrés. La transformation de la page est définie <xref:System.Drawing.Graphics.DrawEllipse%2A> de sorte que les coordonnées passées à la seconde seront traitées comme millimètres au lieu de pixels. Le code fait deux <xref:System.Drawing.Graphics.DrawEllipse%2A> appels identiques à la méthode. La transformation du monde <xref:System.Drawing.Graphics.DrawEllipse%2A> est appliquée au premier appel, et les deux <xref:System.Drawing.Graphics.DrawEllipse%2A> transformations (monde et page) sont appliquées au deuxième appel.  
  
```vb  
Dim graphics As Graphics = e.Graphics  
Dim pen As New Pen(Color.Red)  
  
graphics.ResetTransform()  
graphics.RotateTransform(30) ' world transformation  
graphics.DrawEllipse(pen, 0, 0, 100, 50)  
graphics.PageUnit = GraphicsUnit.Millimeter ' page transformation  
graphics.DrawEllipse(pen, 0, 0, 100, 50)  
```  
  
```csharp  
Graphics graphics = e.Graphics;  
Pen pen = new Pen(Color.Red);
  
graphics.ResetTransform();  
graphics.RotateTransform(30);                    // world transformation  
graphics.DrawEllipse(pen, 0, 0, 100, 50);  
graphics.PageUnit = GraphicsUnit.Millimeter;     // page transformation  
graphics.DrawEllipse(pen, 0, 0, 100, 50);  
```  
  
 L’illustration suivante montre les deux ellipses. Notez que la rotation de 30 degrés concerne l’origine du système de coordonnées (coin supérieur gauche de la zone cliente), et non sur les centres des ellipses. Notez également que la largeur du stylo de 1 signifie 1 pixel pour la première ellipse et 1 millimètre pour la deuxième ellipse.  
  
 ![Illustration qui montre deux ellipses : rotation et largeur de stylo.](./media/managing-the-state-of-a-graphics-object/set-rotation-pen-width-drawellipse-method.png)  
  
### <a name="clipping-region"></a>Région de clipping  
 Un <xref:System.Drawing.Graphics> objet maintient une région de coupure qui <xref:System.Drawing.Graphics> s’applique à tous les éléments dessinés par cet objet. Vous pouvez définir la région <xref:System.Drawing.Graphics.SetClip%2A> de coupure en appelant la méthode.  
  
 L’exemple suivant crée une région en forme de plus en formant l’union de deux rectangles. Cette région est désignée comme la <xref:System.Drawing.Graphics> région de coupure d’un objet. Ensuite, le code trace deux lignes qui sont limitées à l’intérieur de la région de coupure.  
  
```vb  
Dim graphics As Graphics = e.Graphics  
  
' Opaque red, width 5  
Dim pen As New Pen(Color.Red, 5)  
  
' Opaque aqua  
Dim brush As New SolidBrush(Color.FromArgb(255, 180, 255, 255))  
  
' Create a plus-shaped region by forming the union of two rectangles.  
Dim [region] As New [Region](New Rectangle(50, 0, 50, 150))  
[region].Union(New Rectangle(0, 50, 150, 50))  
graphics.FillRegion(brush, [region])  
  
' Set the clipping region.  
graphics.SetClip([region], CombineMode.Replace)  
  
' Draw two clipped lines.  
graphics.DrawLine(pen, 0, 30, 150, 160)  
graphics.DrawLine(pen, 40, 20, 190, 150)  
```  
  
```csharp  
Graphics graphics = e.Graphics;  
  
// Opaque red, width 5  
Pen pen = new Pen(Color.Red, 5);
  
// Opaque aqua  
SolidBrush brush = new SolidBrush(Color.FromArgb(255, 180, 255, 255));
  
// Create a plus-shaped region by forming the union of two rectangles.  
Region region = new Region(new Rectangle(50, 0, 50, 150));  
region.Union(new Rectangle(0, 50, 150, 50));  
graphics.FillRegion(brush, region);  
  
// Set the clipping region.  
graphics.SetClip(region, CombineMode.Replace);  
  
// Draw two clipped lines.  
graphics.DrawLine(pen, 0, 30, 150, 160);  
graphics.DrawLine(pen, 40, 20, 190, 150);  
```  
  
 L’illustration suivante montre les lignes coupées :  
  
 ![Diagramme qui montre la région limitée de clip.](./media/managing-the-state-of-a-graphics-object/set-clipping-region-setclip-method.png)  
  
## <a name="see-also"></a>Voir aussi

- [Graphiques et dessins dans les Windows Forms](graphics-and-drawing-in-windows-forms.md)
- [Utilisation de conteneurs graphiques imbriqués](using-nested-graphics-containers.md)
