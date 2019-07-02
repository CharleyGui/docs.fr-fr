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
ms.openlocfilehash: ce645133af35271fe1de969621907c53183d9a54
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67505594"
---
# <a name="managing-the-state-of-a-graphics-object"></a>Gestion de l'état d'un objet graphique
Le <xref:System.Drawing.Graphics> classe est au cœur de GDI +. Pour dessiner quoi que ce soit, vous obtenez un <xref:System.Drawing.Graphics> de l’objet, définissez ses propriétés et appeler ses méthodes <xref:System.Drawing.Graphics.DrawLine%2A>, <xref:System.Drawing.Graphics.DrawImage%2A>, <xref:System.Drawing.Graphics.DrawString%2A>, etc.).  
  
 L’exemple suivant appelle la <xref:System.Drawing.Graphics.DrawRectangle%2A> méthode d’un <xref:System.Drawing.Graphics> objet. Le premier argument passé à la <xref:System.Drawing.Graphics.DrawRectangle%2A> méthode est un <xref:System.Drawing.Pen> objet.  
  
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
 Un <xref:System.Drawing.Graphics> objet fournit plus de telles que les méthodes de dessin <xref:System.Drawing.Graphics.DrawLine%2A> et <xref:System.Drawing.Graphics.DrawRectangle%2A>. Un <xref:System.Drawing.Graphics> gère également l’état graphique qui peut être divisée selon les catégories suivantes :  
  
- Paramètres de qualité  
  
- Transformations  
  
- Zone de découpage  
  
### <a name="quality-settings"></a>Paramètres de qualité  
 Un <xref:System.Drawing.Graphics> objet possède plusieurs propriétés qui influencent la qualité des éléments qui sont dessinées. Par exemple, vous pouvez définir le <xref:System.Drawing.Graphics.TextRenderingHint%2A> propriété pour spécifier le type d’anticrénelage (le cas échéant) appliqué au texte. Les autres propriétés qui influencent la qualité sont <xref:System.Drawing.Graphics.SmoothingMode%2A>, <xref:System.Drawing.Graphics.CompositingMode%2A>, <xref:System.Drawing.Graphics.CompositingQuality%2A>, et <xref:System.Drawing.Graphics.InterpolationMode%2A>.  
  
 L’exemple suivant dessine deux ellipses, l’une avec le mode de lissage défini sur <xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias> et l’autre avec le mode de lissage défini sur <xref:System.Drawing.Drawing2D.SmoothingMode.HighSpeed>:  
  
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
 Un <xref:System.Drawing.Graphics> objet gère deux transformations (universelle et page) qui sont appliquées à tous les éléments dessinés par cet <xref:System.Drawing.Graphics> objet. Toutes les transformations affines peuvent être stockées dans la transformation universelle. Transformations affines incluent la mise à l’échelle, rotation, la réflexion, l’inclinaison et la traduction. La transformation de page peut être utilisée pour la mise à l’échelle et de modifier les unités (par exemple, des pixels en pouces). Pour plus d’informations, consultez [systèmes de coordonnées et Transformations](coordinate-systems-and-transformations.md).  
  
 L’exemple suivant définit les transformations universelles et de page d’un <xref:System.Drawing.Graphics> objet. La transformation universelle est définie sur une rotation de 30 degrés. La transformation de page est définie afin que les coordonnées passées à la seconde <xref:System.Drawing.Graphics.DrawEllipse%2A> sera traité comme millimètres au lieu des pixels. Le code effectue deux appels identiques à la <xref:System.Drawing.Graphics.DrawEllipse%2A> (méthode). La transformation universelle est appliquée au premier <xref:System.Drawing.Graphics.DrawEllipse%2A> appel et les deux transformations (universelles et pages) sont appliquées à la seconde <xref:System.Drawing.Graphics.DrawEllipse%2A> appeler.  
  
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
  
 L’illustration suivante montre les deux points de suspension. Notez que la rotation de 30 degrés est à l’origine du système de coordonnées (coin supérieur gauche de la zone cliente), mais pas sur les centres des ellipses. Notez également que la largeur du stylet de 1 signifie 1 pixel pour la première ellipse et 1 millimètre pour la seconde.  
  
 ![Illustration des deux points de suspension : largeur de rotation et d’un stylet.](./media/managing-the-state-of-a-graphics-object/set-rotation-pen-width-drawellipse-method.png)  
  
### <a name="clipping-region"></a>Zone de découpage  
 Un <xref:System.Drawing.Graphics> objet gère une région de découpage qui s’applique à tous les éléments dessinés par cet <xref:System.Drawing.Graphics> objet. Vous pouvez définir la zone de découpage en appelant le <xref:System.Drawing.Graphics.SetClip%2A> (méthode).  
  
 L’exemple suivant crée une région en forme de plus par l’union de deux rectangles. Cette région est désignée comme la zone de découpage d’un <xref:System.Drawing.Graphics> objet. Le code dessine ensuite deux lignes sont limitées à l’intérieur de la zone de découpage.  
  
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
  
 L’illustration suivante montre les lignes ajustées :  
  
 ![Diagramme illustrant la zone de découpage limitée.](./media/managing-the-state-of-a-graphics-object/set-clipping-region-setclip-method.png)  
  
## <a name="see-also"></a>Voir aussi

- [Graphiques et dessins dans Windows Forms](graphics-and-drawing-in-windows-forms.md)
- [Utilisation de conteneurs graphiques imbriqués](using-nested-graphics-containers.md)
