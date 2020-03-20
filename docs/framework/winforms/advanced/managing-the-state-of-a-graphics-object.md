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
# <a name="managing-the-state-of-a-graphics-object"></a><span data-ttu-id="218f5-102">Gestion de l'état d'un objet graphique</span><span class="sxs-lookup"><span data-stu-id="218f5-102">Managing the State of a Graphics Object</span></span>
<span data-ttu-id="218f5-103">La <xref:System.Drawing.Graphics> classe est au cœur de GDI.</span><span class="sxs-lookup"><span data-stu-id="218f5-103">The <xref:System.Drawing.Graphics> class is at the heart of GDI+.</span></span> <span data-ttu-id="218f5-104">Pour dessiner quoi que <xref:System.Drawing.Graphics> ce soit, vous obtenez <xref:System.Drawing.Graphics.DrawLine%2A>un <xref:System.Drawing.Graphics.DrawImage%2A> <xref:System.Drawing.Graphics.DrawString%2A>objet, définissez ses propriétés, et appelez ses méthodes, , , et autres).</span><span class="sxs-lookup"><span data-stu-id="218f5-104">To draw anything, you obtain a <xref:System.Drawing.Graphics> object, set its properties, and call its methods <xref:System.Drawing.Graphics.DrawLine%2A>, <xref:System.Drawing.Graphics.DrawImage%2A>, <xref:System.Drawing.Graphics.DrawString%2A>, and the like).</span></span>  
  
 <span data-ttu-id="218f5-105">L’exemple suivant <xref:System.Drawing.Graphics.DrawRectangle%2A> appelle <xref:System.Drawing.Graphics> la méthode d’un objet.</span><span class="sxs-lookup"><span data-stu-id="218f5-105">The following example calls the <xref:System.Drawing.Graphics.DrawRectangle%2A> method of a <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="218f5-106">Le premier argument <xref:System.Drawing.Graphics.DrawRectangle%2A> transmis à <xref:System.Drawing.Pen> la méthode est un objet.</span><span class="sxs-lookup"><span data-stu-id="218f5-106">The first argument passed to the <xref:System.Drawing.Graphics.DrawRectangle%2A> method is a <xref:System.Drawing.Pen> object.</span></span>  
  
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
  
## <a name="graphics-state"></a><span data-ttu-id="218f5-107">État graphique</span><span class="sxs-lookup"><span data-stu-id="218f5-107">Graphics State</span></span>  
 <span data-ttu-id="218f5-108">Un <xref:System.Drawing.Graphics> objet fait plus que fournir <xref:System.Drawing.Graphics.DrawLine%2A> <xref:System.Drawing.Graphics.DrawRectangle%2A>des méthodes de dessin, telles que et .</span><span class="sxs-lookup"><span data-stu-id="218f5-108">A <xref:System.Drawing.Graphics> object does more than provide drawing methods, such as <xref:System.Drawing.Graphics.DrawLine%2A> and <xref:System.Drawing.Graphics.DrawRectangle%2A>.</span></span> <span data-ttu-id="218f5-109">Un <xref:System.Drawing.Graphics> objet maintient également l’état graphique, qui peut être divisé en catégories suivantes :</span><span class="sxs-lookup"><span data-stu-id="218f5-109">A <xref:System.Drawing.Graphics> object also maintains graphics state, which can be divided into the following categories:</span></span>  
  
- <span data-ttu-id="218f5-110">Paramètres de qualité</span><span class="sxs-lookup"><span data-stu-id="218f5-110">Quality settings</span></span>  
  
- <span data-ttu-id="218f5-111">Transformations</span><span class="sxs-lookup"><span data-stu-id="218f5-111">Transformations</span></span>  
  
- <span data-ttu-id="218f5-112">Région de clipping</span><span class="sxs-lookup"><span data-stu-id="218f5-112">Clipping region</span></span>  
  
### <a name="quality-settings"></a><span data-ttu-id="218f5-113">Paramètres de qualité</span><span class="sxs-lookup"><span data-stu-id="218f5-113">Quality Settings</span></span>  
 <span data-ttu-id="218f5-114">Un <xref:System.Drawing.Graphics> objet a plusieurs propriétés qui influencent la qualité des éléments qui sont dessinés.</span><span class="sxs-lookup"><span data-stu-id="218f5-114">A <xref:System.Drawing.Graphics> object has several properties that influence the quality of the items that are drawn.</span></span> <span data-ttu-id="218f5-115">Par exemple, vous <xref:System.Drawing.Graphics.TextRenderingHint%2A> pouvez définir la propriété pour spécifier le type d’anti-application (le cas échéant) appliqué au texte.</span><span class="sxs-lookup"><span data-stu-id="218f5-115">For example, you can set the <xref:System.Drawing.Graphics.TextRenderingHint%2A> property to specify the type of antialiasing (if any) applied to text.</span></span> <span data-ttu-id="218f5-116">D’autres propriétés <xref:System.Drawing.Graphics.SmoothingMode%2A> <xref:System.Drawing.Graphics.CompositingMode%2A>qui <xref:System.Drawing.Graphics.CompositingQuality%2A>influencent la qualité sont , , , et <xref:System.Drawing.Graphics.InterpolationMode%2A>.</span><span class="sxs-lookup"><span data-stu-id="218f5-116">Other properties that influence quality are <xref:System.Drawing.Graphics.SmoothingMode%2A>, <xref:System.Drawing.Graphics.CompositingMode%2A>, <xref:System.Drawing.Graphics.CompositingQuality%2A>, and <xref:System.Drawing.Graphics.InterpolationMode%2A>.</span></span>  
  
 <span data-ttu-id="218f5-117">L’exemple suivant attire deux ellipses, l’une avec le mode de lissage réglé <xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias> et l’autre avec le mode de lissage réglé pour <xref:System.Drawing.Drawing2D.SmoothingMode.HighSpeed>:</span><span class="sxs-lookup"><span data-stu-id="218f5-117">The following example draws two ellipses, one with the smoothing mode set to <xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias> and one with the smoothing mode set to <xref:System.Drawing.Drawing2D.SmoothingMode.HighSpeed>:</span></span>  
  
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
  
### <a name="transformations"></a><span data-ttu-id="218f5-118">Transformations</span><span class="sxs-lookup"><span data-stu-id="218f5-118">Transformations</span></span>  
 <span data-ttu-id="218f5-119">Un <xref:System.Drawing.Graphics> objet maintient deux transformations (monde et page) qui <xref:System.Drawing.Graphics> sont appliquées à tous les éléments dessinés par cet objet.</span><span class="sxs-lookup"><span data-stu-id="218f5-119">A <xref:System.Drawing.Graphics> object maintains two transformations (world and page) that are applied to all items drawn by that <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="218f5-120">Toute transformation affine peut être stockée dans la transformation du monde.</span><span class="sxs-lookup"><span data-stu-id="218f5-120">Any affine transformation can be stored in the world transformation.</span></span> <span data-ttu-id="218f5-121">Les transformations d’affine incluent l’échelle, la rotation, le reflet, la biais et la traduction.</span><span class="sxs-lookup"><span data-stu-id="218f5-121">Affine transformations include scaling, rotating, reflecting, skewing, and translating.</span></span> <span data-ttu-id="218f5-122">La transformation de la page peut être utilisée pour la mise à l’échelle et pour changer d’unités (par exemple, pixels en pouces).</span><span class="sxs-lookup"><span data-stu-id="218f5-122">The page transformation can be used for scaling and for changing units (for example, pixels to inches).</span></span> <span data-ttu-id="218f5-123">Pour plus d’informations, voir [Systèmes de coordination et transformations](coordinate-systems-and-transformations.md).</span><span class="sxs-lookup"><span data-stu-id="218f5-123">For more information, see [Coordinate Systems and Transformations](coordinate-systems-and-transformations.md).</span></span>  
  
 <span data-ttu-id="218f5-124">L’exemple suivant définit le monde <xref:System.Drawing.Graphics> et les transformations de page d’un objet.</span><span class="sxs-lookup"><span data-stu-id="218f5-124">The following example sets the world and page transformations of a <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="218f5-125">La transformation mondiale est définie à une rotation de 30 degrés.</span><span class="sxs-lookup"><span data-stu-id="218f5-125">The world transformation is set to a 30-degree rotation.</span></span> <span data-ttu-id="218f5-126">La transformation de la page est définie <xref:System.Drawing.Graphics.DrawEllipse%2A> de sorte que les coordonnées passées à la seconde seront traitées comme millimètres au lieu de pixels.</span><span class="sxs-lookup"><span data-stu-id="218f5-126">The page transformation is set so that the coordinates passed to the second <xref:System.Drawing.Graphics.DrawEllipse%2A> will be treated as millimeters instead of pixels.</span></span> <span data-ttu-id="218f5-127">Le code fait deux <xref:System.Drawing.Graphics.DrawEllipse%2A> appels identiques à la méthode.</span><span class="sxs-lookup"><span data-stu-id="218f5-127">The code makes two identical calls to the <xref:System.Drawing.Graphics.DrawEllipse%2A> method.</span></span> <span data-ttu-id="218f5-128">La transformation du monde <xref:System.Drawing.Graphics.DrawEllipse%2A> est appliquée au premier appel, et les deux <xref:System.Drawing.Graphics.DrawEllipse%2A> transformations (monde et page) sont appliquées au deuxième appel.</span><span class="sxs-lookup"><span data-stu-id="218f5-128">The world transformation is applied to the first <xref:System.Drawing.Graphics.DrawEllipse%2A> call, and both transformations (world and page) are applied to the second <xref:System.Drawing.Graphics.DrawEllipse%2A> call.</span></span>  
  
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
  
 <span data-ttu-id="218f5-129">L’illustration suivante montre les deux ellipses.</span><span class="sxs-lookup"><span data-stu-id="218f5-129">The following illustration shows the two ellipses.</span></span> <span data-ttu-id="218f5-130">Notez que la rotation de 30 degrés concerne l’origine du système de coordonnées (coin supérieur gauche de la zone cliente), et non sur les centres des ellipses.</span><span class="sxs-lookup"><span data-stu-id="218f5-130">Note that the 30-degree rotation is about the origin of the coordinate system (upper-left corner of the client area), not about the centers of the ellipses.</span></span> <span data-ttu-id="218f5-131">Notez également que la largeur du stylo de 1 signifie 1 pixel pour la première ellipse et 1 millimètre pour la deuxième ellipse.</span><span class="sxs-lookup"><span data-stu-id="218f5-131">Also note that the pen width of 1 means 1 pixel for the first ellipse and 1 millimeter for the second ellipse.</span></span>  
  
 ![Illustration qui montre deux ellipses : rotation et largeur de stylo.](./media/managing-the-state-of-a-graphics-object/set-rotation-pen-width-drawellipse-method.png)  
  
### <a name="clipping-region"></a><span data-ttu-id="218f5-133">Région de clipping</span><span class="sxs-lookup"><span data-stu-id="218f5-133">Clipping Region</span></span>  
 <span data-ttu-id="218f5-134">Un <xref:System.Drawing.Graphics> objet maintient une région de coupure qui <xref:System.Drawing.Graphics> s’applique à tous les éléments dessinés par cet objet.</span><span class="sxs-lookup"><span data-stu-id="218f5-134">A <xref:System.Drawing.Graphics> object maintains a clipping region that applies to all items drawn by that <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="218f5-135">Vous pouvez définir la région <xref:System.Drawing.Graphics.SetClip%2A> de coupure en appelant la méthode.</span><span class="sxs-lookup"><span data-stu-id="218f5-135">You can set the clipping region by calling the <xref:System.Drawing.Graphics.SetClip%2A> method.</span></span>  
  
 <span data-ttu-id="218f5-136">L’exemple suivant crée une région en forme de plus en formant l’union de deux rectangles.</span><span class="sxs-lookup"><span data-stu-id="218f5-136">The following example creates a plus-shaped region by forming the union of two rectangles.</span></span> <span data-ttu-id="218f5-137">Cette région est désignée comme la <xref:System.Drawing.Graphics> région de coupure d’un objet.</span><span class="sxs-lookup"><span data-stu-id="218f5-137">That region is designated as the clipping region of a <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="218f5-138">Ensuite, le code trace deux lignes qui sont limitées à l’intérieur de la région de coupure.</span><span class="sxs-lookup"><span data-stu-id="218f5-138">Then the code draws two lines that are restricted to the interior of the clipping region.</span></span>  
  
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
  
 <span data-ttu-id="218f5-139">L’illustration suivante montre les lignes coupées :</span><span class="sxs-lookup"><span data-stu-id="218f5-139">The following illustration shows the clipped lines:</span></span>  
  
 ![Diagramme qui montre la région limitée de clip.](./media/managing-the-state-of-a-graphics-object/set-clipping-region-setclip-method.png)  
  
## <a name="see-also"></a><span data-ttu-id="218f5-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="218f5-141">See also</span></span>

- [<span data-ttu-id="218f5-142">Graphiques et dessins dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="218f5-142">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="218f5-143">Utilisation de conteneurs graphiques imbriqués</span><span class="sxs-lookup"><span data-stu-id="218f5-143">Using Nested Graphics Containers</span></span>](using-nested-graphics-containers.md)
