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
# <a name="managing-the-state-of-a-graphics-object"></a><span data-ttu-id="df24c-102">Gestion de l'état d'un objet graphique</span><span class="sxs-lookup"><span data-stu-id="df24c-102">Managing the State of a Graphics Object</span></span>
<span data-ttu-id="df24c-103">Le <xref:System.Drawing.Graphics> classe est au cœur de GDI +.</span><span class="sxs-lookup"><span data-stu-id="df24c-103">The <xref:System.Drawing.Graphics> class is at the heart of GDI+.</span></span> <span data-ttu-id="df24c-104">Pour dessiner quoi que ce soit, vous obtenez un <xref:System.Drawing.Graphics> de l’objet, définissez ses propriétés et appeler ses méthodes <xref:System.Drawing.Graphics.DrawLine%2A>, <xref:System.Drawing.Graphics.DrawImage%2A>, <xref:System.Drawing.Graphics.DrawString%2A>, etc.).</span><span class="sxs-lookup"><span data-stu-id="df24c-104">To draw anything, you obtain a <xref:System.Drawing.Graphics> object, set its properties, and call its methods <xref:System.Drawing.Graphics.DrawLine%2A>, <xref:System.Drawing.Graphics.DrawImage%2A>, <xref:System.Drawing.Graphics.DrawString%2A>, and the like).</span></span>  
  
 <span data-ttu-id="df24c-105">L’exemple suivant appelle la <xref:System.Drawing.Graphics.DrawRectangle%2A> méthode d’un <xref:System.Drawing.Graphics> objet.</span><span class="sxs-lookup"><span data-stu-id="df24c-105">The following example calls the <xref:System.Drawing.Graphics.DrawRectangle%2A> method of a <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="df24c-106">Le premier argument passé à la <xref:System.Drawing.Graphics.DrawRectangle%2A> méthode est un <xref:System.Drawing.Pen> objet.</span><span class="sxs-lookup"><span data-stu-id="df24c-106">The first argument passed to the <xref:System.Drawing.Graphics.DrawRectangle%2A> method is a <xref:System.Drawing.Pen> object.</span></span>  
  
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
  
## <a name="graphics-state"></a><span data-ttu-id="df24c-107">État graphique</span><span class="sxs-lookup"><span data-stu-id="df24c-107">Graphics State</span></span>  
 <span data-ttu-id="df24c-108">Un <xref:System.Drawing.Graphics> objet fournit plus de telles que les méthodes de dessin <xref:System.Drawing.Graphics.DrawLine%2A> et <xref:System.Drawing.Graphics.DrawRectangle%2A>.</span><span class="sxs-lookup"><span data-stu-id="df24c-108">A <xref:System.Drawing.Graphics> object does more than provide drawing methods, such as <xref:System.Drawing.Graphics.DrawLine%2A> and <xref:System.Drawing.Graphics.DrawRectangle%2A>.</span></span> <span data-ttu-id="df24c-109">Un <xref:System.Drawing.Graphics> gère également l’état graphique qui peut être divisée selon les catégories suivantes :</span><span class="sxs-lookup"><span data-stu-id="df24c-109">A <xref:System.Drawing.Graphics> object also maintains graphics state, which can be divided into the following categories:</span></span>  
  
- <span data-ttu-id="df24c-110">Paramètres de qualité</span><span class="sxs-lookup"><span data-stu-id="df24c-110">Quality settings</span></span>  
  
- <span data-ttu-id="df24c-111">Transformations</span><span class="sxs-lookup"><span data-stu-id="df24c-111">Transformations</span></span>  
  
- <span data-ttu-id="df24c-112">Zone de découpage</span><span class="sxs-lookup"><span data-stu-id="df24c-112">Clipping region</span></span>  
  
### <a name="quality-settings"></a><span data-ttu-id="df24c-113">Paramètres de qualité</span><span class="sxs-lookup"><span data-stu-id="df24c-113">Quality Settings</span></span>  
 <span data-ttu-id="df24c-114">Un <xref:System.Drawing.Graphics> objet possède plusieurs propriétés qui influencent la qualité des éléments qui sont dessinées.</span><span class="sxs-lookup"><span data-stu-id="df24c-114">A <xref:System.Drawing.Graphics> object has several properties that influence the quality of the items that are drawn.</span></span> <span data-ttu-id="df24c-115">Par exemple, vous pouvez définir le <xref:System.Drawing.Graphics.TextRenderingHint%2A> propriété pour spécifier le type d’anticrénelage (le cas échéant) appliqué au texte.</span><span class="sxs-lookup"><span data-stu-id="df24c-115">For example, you can set the <xref:System.Drawing.Graphics.TextRenderingHint%2A> property to specify the type of antialiasing (if any) applied to text.</span></span> <span data-ttu-id="df24c-116">Les autres propriétés qui influencent la qualité sont <xref:System.Drawing.Graphics.SmoothingMode%2A>, <xref:System.Drawing.Graphics.CompositingMode%2A>, <xref:System.Drawing.Graphics.CompositingQuality%2A>, et <xref:System.Drawing.Graphics.InterpolationMode%2A>.</span><span class="sxs-lookup"><span data-stu-id="df24c-116">Other properties that influence quality are <xref:System.Drawing.Graphics.SmoothingMode%2A>, <xref:System.Drawing.Graphics.CompositingMode%2A>, <xref:System.Drawing.Graphics.CompositingQuality%2A>, and <xref:System.Drawing.Graphics.InterpolationMode%2A>.</span></span>  
  
 <span data-ttu-id="df24c-117">L’exemple suivant dessine deux ellipses, l’une avec le mode de lissage défini sur <xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias> et l’autre avec le mode de lissage défini sur <xref:System.Drawing.Drawing2D.SmoothingMode.HighSpeed>:</span><span class="sxs-lookup"><span data-stu-id="df24c-117">The following example draws two ellipses, one with the smoothing mode set to <xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias> and one with the smoothing mode set to <xref:System.Drawing.Drawing2D.SmoothingMode.HighSpeed>:</span></span>  
  
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
  
### <a name="transformations"></a><span data-ttu-id="df24c-118">Transformations</span><span class="sxs-lookup"><span data-stu-id="df24c-118">Transformations</span></span>  
 <span data-ttu-id="df24c-119">Un <xref:System.Drawing.Graphics> objet gère deux transformations (universelle et page) qui sont appliquées à tous les éléments dessinés par cet <xref:System.Drawing.Graphics> objet.</span><span class="sxs-lookup"><span data-stu-id="df24c-119">A <xref:System.Drawing.Graphics> object maintains two transformations (world and page) that are applied to all items drawn by that <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="df24c-120">Toutes les transformations affines peuvent être stockées dans la transformation universelle.</span><span class="sxs-lookup"><span data-stu-id="df24c-120">Any affine transformation can be stored in the world transformation.</span></span> <span data-ttu-id="df24c-121">Transformations affines incluent la mise à l’échelle, rotation, la réflexion, l’inclinaison et la traduction.</span><span class="sxs-lookup"><span data-stu-id="df24c-121">Affine transformations include scaling, rotating, reflecting, skewing, and translating.</span></span> <span data-ttu-id="df24c-122">La transformation de page peut être utilisée pour la mise à l’échelle et de modifier les unités (par exemple, des pixels en pouces).</span><span class="sxs-lookup"><span data-stu-id="df24c-122">The page transformation can be used for scaling and for changing units (for example, pixels to inches).</span></span> <span data-ttu-id="df24c-123">Pour plus d’informations, consultez [systèmes de coordonnées et Transformations](coordinate-systems-and-transformations.md).</span><span class="sxs-lookup"><span data-stu-id="df24c-123">For more information, see [Coordinate Systems and Transformations](coordinate-systems-and-transformations.md).</span></span>  
  
 <span data-ttu-id="df24c-124">L’exemple suivant définit les transformations universelles et de page d’un <xref:System.Drawing.Graphics> objet.</span><span class="sxs-lookup"><span data-stu-id="df24c-124">The following example sets the world and page transformations of a <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="df24c-125">La transformation universelle est définie sur une rotation de 30 degrés.</span><span class="sxs-lookup"><span data-stu-id="df24c-125">The world transformation is set to a 30-degree rotation.</span></span> <span data-ttu-id="df24c-126">La transformation de page est définie afin que les coordonnées passées à la seconde <xref:System.Drawing.Graphics.DrawEllipse%2A> sera traité comme millimètres au lieu des pixels.</span><span class="sxs-lookup"><span data-stu-id="df24c-126">The page transformation is set so that the coordinates passed to the second <xref:System.Drawing.Graphics.DrawEllipse%2A> will be treated as millimeters instead of pixels.</span></span> <span data-ttu-id="df24c-127">Le code effectue deux appels identiques à la <xref:System.Drawing.Graphics.DrawEllipse%2A> (méthode).</span><span class="sxs-lookup"><span data-stu-id="df24c-127">The code makes two identical calls to the <xref:System.Drawing.Graphics.DrawEllipse%2A> method.</span></span> <span data-ttu-id="df24c-128">La transformation universelle est appliquée au premier <xref:System.Drawing.Graphics.DrawEllipse%2A> appel et les deux transformations (universelles et pages) sont appliquées à la seconde <xref:System.Drawing.Graphics.DrawEllipse%2A> appeler.</span><span class="sxs-lookup"><span data-stu-id="df24c-128">The world transformation is applied to the first <xref:System.Drawing.Graphics.DrawEllipse%2A> call, and both transformations (world and page) are applied to the second <xref:System.Drawing.Graphics.DrawEllipse%2A> call.</span></span>  
  
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
  
 <span data-ttu-id="df24c-129">L’illustration suivante montre les deux points de suspension.</span><span class="sxs-lookup"><span data-stu-id="df24c-129">The following illustration shows the two ellipses.</span></span> <span data-ttu-id="df24c-130">Notez que la rotation de 30 degrés est à l’origine du système de coordonnées (coin supérieur gauche de la zone cliente), mais pas sur les centres des ellipses.</span><span class="sxs-lookup"><span data-stu-id="df24c-130">Note that the 30-degree rotation is about the origin of the coordinate system (upper-left corner of the client area), not about the centers of the ellipses.</span></span> <span data-ttu-id="df24c-131">Notez également que la largeur du stylet de 1 signifie 1 pixel pour la première ellipse et 1 millimètre pour la seconde.</span><span class="sxs-lookup"><span data-stu-id="df24c-131">Also note that the pen width of 1 means 1 pixel for the first ellipse and 1 millimeter for the second ellipse.</span></span>  
  
 ![Illustration des deux points de suspension : largeur de rotation et d’un stylet.](./media/managing-the-state-of-a-graphics-object/set-rotation-pen-width-drawellipse-method.png)  
  
### <a name="clipping-region"></a><span data-ttu-id="df24c-133">Zone de découpage</span><span class="sxs-lookup"><span data-stu-id="df24c-133">Clipping Region</span></span>  
 <span data-ttu-id="df24c-134">Un <xref:System.Drawing.Graphics> objet gère une région de découpage qui s’applique à tous les éléments dessinés par cet <xref:System.Drawing.Graphics> objet.</span><span class="sxs-lookup"><span data-stu-id="df24c-134">A <xref:System.Drawing.Graphics> object maintains a clipping region that applies to all items drawn by that <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="df24c-135">Vous pouvez définir la zone de découpage en appelant le <xref:System.Drawing.Graphics.SetClip%2A> (méthode).</span><span class="sxs-lookup"><span data-stu-id="df24c-135">You can set the clipping region by calling the <xref:System.Drawing.Graphics.SetClip%2A> method.</span></span>  
  
 <span data-ttu-id="df24c-136">L’exemple suivant crée une région en forme de plus par l’union de deux rectangles.</span><span class="sxs-lookup"><span data-stu-id="df24c-136">The following example creates a plus-shaped region by forming the union of two rectangles.</span></span> <span data-ttu-id="df24c-137">Cette région est désignée comme la zone de découpage d’un <xref:System.Drawing.Graphics> objet.</span><span class="sxs-lookup"><span data-stu-id="df24c-137">That region is designated as the clipping region of a <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="df24c-138">Le code dessine ensuite deux lignes sont limitées à l’intérieur de la zone de découpage.</span><span class="sxs-lookup"><span data-stu-id="df24c-138">Then the code draws two lines that are restricted to the interior of the clipping region.</span></span>  
  
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
  
 <span data-ttu-id="df24c-139">L’illustration suivante montre les lignes ajustées :</span><span class="sxs-lookup"><span data-stu-id="df24c-139">The following illustration shows the clipped lines:</span></span>  
  
 ![Diagramme illustrant la zone de découpage limitée.](./media/managing-the-state-of-a-graphics-object/set-clipping-region-setclip-method.png)  
  
## <a name="see-also"></a><span data-ttu-id="df24c-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="df24c-141">See also</span></span>

- [<span data-ttu-id="df24c-142">Graphiques et dessins dans Windows Forms</span><span class="sxs-lookup"><span data-stu-id="df24c-142">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="df24c-143">Utilisation de conteneurs graphiques imbriqués</span><span class="sxs-lookup"><span data-stu-id="df24c-143">Using Nested Graphics Containers</span></span>](using-nested-graphics-containers.md)
