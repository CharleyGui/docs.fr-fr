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
# <a name="brushes-and-filled-shapes-in-gdi"></a><span data-ttu-id="d7eb6-102">Pinceaux et remplissage de formes dans GDI+</span><span class="sxs-lookup"><span data-stu-id="d7eb6-102">Brushes and Filled Shapes in GDI+</span></span>
<span data-ttu-id="d7eb6-103">Une forme fermée, comme un rectangle ou une ellipse, se compose d’un plan et un intérieur.</span><span class="sxs-lookup"><span data-stu-id="d7eb6-103">A closed shape, such as a rectangle or an ellipse, consists of an outline and an interior.</span></span> <span data-ttu-id="d7eb6-104">Le contour est dessiné avec un stylet et l’intérieur est rempli avec un pinceau.</span><span class="sxs-lookup"><span data-stu-id="d7eb6-104">The outline is drawn with a pen and the interior is filled with a brush.</span></span> <span data-ttu-id="d7eb6-105">GDI + fournit plusieurs classes de pinceau pour remplir l’intérieur des formes fermées : <xref:System.Drawing.SolidBrush>, <xref:System.Drawing.Drawing2D.HatchBrush>, <xref:System.Drawing.TextureBrush>, <xref:System.Drawing.Drawing2D.LinearGradientBrush>, et <xref:System.Drawing.Drawing2D.PathGradientBrush>.</span><span class="sxs-lookup"><span data-stu-id="d7eb6-105">GDI+ provides several brush classes for filling the interiors of closed shapes: <xref:System.Drawing.SolidBrush>, <xref:System.Drawing.Drawing2D.HatchBrush>, <xref:System.Drawing.TextureBrush>, <xref:System.Drawing.Drawing2D.LinearGradientBrush>, and <xref:System.Drawing.Drawing2D.PathGradientBrush>.</span></span> <span data-ttu-id="d7eb6-106">Toutes ces classes héritent de la <xref:System.Drawing.Brush> classe.</span><span class="sxs-lookup"><span data-stu-id="d7eb6-106">All of these classes inherit from the <xref:System.Drawing.Brush> class.</span></span> <span data-ttu-id="d7eb6-107">L’illustration suivante montre un rectangle rempli avec un pinceau uni et une ellipse remplie avec un pinceau de hachurage.</span><span class="sxs-lookup"><span data-stu-id="d7eb6-107">The following illustration shows a rectangle filled with a solid brush and an ellipse filled with a hatch brush.</span></span>  
  
 <span data-ttu-id="d7eb6-108">![Formes pleines](./media/aboutgdip02-art17.gif "Aboutgdip02_art17")</span><span class="sxs-lookup"><span data-stu-id="d7eb6-108">![Filled Shapes](./media/aboutgdip02-art17.gif "Aboutgdip02_art17")</span></span>  
  
## <a name="solid-brushes"></a><span data-ttu-id="d7eb6-109">Pinceaux solide</span><span class="sxs-lookup"><span data-stu-id="d7eb6-109">Solid Brushes</span></span>  
 <span data-ttu-id="d7eb6-110">Pour remplir une forme fermée, vous avez besoin d’une instance de la <xref:System.Drawing.Graphics> classe et un <xref:System.Drawing.Brush>.</span><span class="sxs-lookup"><span data-stu-id="d7eb6-110">To fill a closed shape, you need an instance of the <xref:System.Drawing.Graphics> class and a <xref:System.Drawing.Brush>.</span></span> <span data-ttu-id="d7eb6-111">L’instance de la <xref:System.Drawing.Graphics> classe fournit des méthodes, telles que <xref:System.Drawing.Graphics.FillRectangle%2A> et <xref:System.Drawing.Graphics.FillEllipse%2A>et le <xref:System.Drawing.Brush> stocke les attributs de remplissage, telles que la couleur et le motif.</span><span class="sxs-lookup"><span data-stu-id="d7eb6-111">The instance of the <xref:System.Drawing.Graphics> class provides methods, such as <xref:System.Drawing.Graphics.FillRectangle%2A> and <xref:System.Drawing.Graphics.FillEllipse%2A>, and the <xref:System.Drawing.Brush> stores attributes of the fill, such as color and pattern.</span></span> <span data-ttu-id="d7eb6-112">Le <xref:System.Drawing.Brush> est passé comme argument à la méthode de remplissage.</span><span class="sxs-lookup"><span data-stu-id="d7eb6-112">The <xref:System.Drawing.Brush> is passed as one of the arguments to the fill method.</span></span> <span data-ttu-id="d7eb6-113">L’exemple de code suivant montre comment remplir une ellipse avec une couleur rouge unie.</span><span class="sxs-lookup"><span data-stu-id="d7eb6-113">The following code example shows how to fill an ellipse with a solid red color.</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#121](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#121)]
 [!code-vb[LinesCurvesAndShapes#121](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#121)]  
  
> [!NOTE]
>  <span data-ttu-id="d7eb6-114">Dans l’exemple précédent, le pinceau est de type <xref:System.Drawing.SolidBrush>, qui hérite de <xref:System.Drawing.Brush>.</span><span class="sxs-lookup"><span data-stu-id="d7eb6-114">In the preceding example, the brush is of type <xref:System.Drawing.SolidBrush>, which inherits from <xref:System.Drawing.Brush>.</span></span>  
  
## <a name="hatch-brushes"></a><span data-ttu-id="d7eb6-115">Pinceaux à hachures</span><span class="sxs-lookup"><span data-stu-id="d7eb6-115">Hatch Brushes</span></span>  
 <span data-ttu-id="d7eb6-116">Lorsque vous remplissez une forme avec un pinceau de hachurage, vous spécifiez une couleur de premier plan, une couleur d’arrière-plan et un style de hachurage.</span><span class="sxs-lookup"><span data-stu-id="d7eb6-116">When you fill a shape with a hatch brush, you specify a foreground color, a background color, and a hatch style.</span></span> <span data-ttu-id="d7eb6-117">La couleur de premier plan est la couleur des hachures.</span><span class="sxs-lookup"><span data-stu-id="d7eb6-117">The foreground color is the color of the hatching.</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#122](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#122)]
 [!code-vb[LinesCurvesAndShapes#122](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#122)]  
  
 <span data-ttu-id="d7eb6-118">GDI + offre plus de 50 styles de hachurage. les trois styles présentés dans l’illustration suivante sont <xref:System.Drawing.Drawing2D.HatchStyle.Horizontal>, <xref:System.Drawing.Drawing2D.HatchStyle.ForwardDiagonal>, et <xref:System.Drawing.Drawing2D.HatchStyle.Cross>.</span><span class="sxs-lookup"><span data-stu-id="d7eb6-118">GDI+ provides more than 50 hatch styles; the three styles shown in the following illustration are <xref:System.Drawing.Drawing2D.HatchStyle.Horizontal>, <xref:System.Drawing.Drawing2D.HatchStyle.ForwardDiagonal>, and <xref:System.Drawing.Drawing2D.HatchStyle.Cross>.</span></span>  
  
 <span data-ttu-id="d7eb6-119">![Formes pleines](./media/aboutgdip02-art18.gif "Aboutgdip02_art18")</span><span class="sxs-lookup"><span data-stu-id="d7eb6-119">![Filled Shapes](./media/aboutgdip02-art18.gif "Aboutgdip02_art18")</span></span>  
  
## <a name="texture-brushes"></a><span data-ttu-id="d7eb6-120">Pinceaux de texture</span><span class="sxs-lookup"><span data-stu-id="d7eb6-120">Texture Brushes</span></span>  
 <span data-ttu-id="d7eb6-121">Avec un pinceau de la texture, vous pouvez remplir une forme avec un modèle stocké dans une bitmap.</span><span class="sxs-lookup"><span data-stu-id="d7eb6-121">With a texture brush, you can fill a shape with a pattern stored in a bitmap.</span></span> <span data-ttu-id="d7eb6-122">Par exemple, supposons que l’image suivante est stockée dans un fichier de disque nommé `MyTexture.bmp`.</span><span class="sxs-lookup"><span data-stu-id="d7eb6-122">For example, suppose the following picture is stored in a disk file named `MyTexture.bmp`.</span></span>  
  
 <span data-ttu-id="d7eb6-123">![Rempli forme](./media/aboutgdip02-art19.gif "Aboutgdip02_Art19")</span><span class="sxs-lookup"><span data-stu-id="d7eb6-123">![Filled Shape](./media/aboutgdip02-art19.gif "Aboutgdip02_Art19")</span></span>  
  
 <span data-ttu-id="d7eb6-124">L’exemple de code suivant montre comment remplir une ellipse en répétant l’image stockée dans `MyTexture.bmp`.</span><span class="sxs-lookup"><span data-stu-id="d7eb6-124">The following code example shows how to fill an ellipse by repeating the picture stored in `MyTexture.bmp`.</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#123](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#123)]
 [!code-vb[LinesCurvesAndShapes#123](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#123)]  
  
 <span data-ttu-id="d7eb6-125">L’illustration suivante montre l’ellipse remplie.</span><span class="sxs-lookup"><span data-stu-id="d7eb6-125">The following illustration shows the filled ellipse.</span></span>  
  
 <span data-ttu-id="d7eb6-126">![Rempli forme](./media/aboutgdip02-art20.gif "AboutGdip02_Art20")</span><span class="sxs-lookup"><span data-stu-id="d7eb6-126">![Filled Shape](./media/aboutgdip02-art20.gif "AboutGdip02_Art20")</span></span>  
  
## <a name="gradient-brushes"></a><span data-ttu-id="d7eb6-127">Pinceaux de dégradé</span><span class="sxs-lookup"><span data-stu-id="d7eb6-127">Gradient Brushes</span></span>  
 <span data-ttu-id="d7eb6-128">GDI + offre deux types de pinceaux de dégradé : linéaire et chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="d7eb6-128">GDI+ provides two kinds of gradient brushes: linear and path.</span></span> <span data-ttu-id="d7eb6-129">Vous pouvez utiliser un pinceau dégradé linéaire pour remplir une forme avec une couleur qui change graduellement à mesure que vous déplacer entre la forme horizontalement, verticalement ou en diagonale.</span><span class="sxs-lookup"><span data-stu-id="d7eb6-129">You can use a linear gradient brush to fill a shape with color that changes gradually as you move across the shape horizontally, vertically, or diagonally.</span></span> <span data-ttu-id="d7eb6-130">L’exemple de code suivant montre comment remplir une ellipse avec un pinceau de dégradé horizontal qui passe du bleu au vert lorsque vous déplacez le bord gauche de l’ellipse vers le bord droit.</span><span class="sxs-lookup"><span data-stu-id="d7eb6-130">The following code example shows how to fill an ellipse with a horizontal gradient brush that changes from blue to green as you move from the left edge of the ellipse to the right edge.</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#124](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#124)]
 [!code-vb[LinesCurvesAndShapes#124](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#124)]  
  
 <span data-ttu-id="d7eb6-131">L’illustration suivante montre l’ellipse remplie.</span><span class="sxs-lookup"><span data-stu-id="d7eb6-131">The following illustration shows the filled ellipse.</span></span>  
  
 <span data-ttu-id="d7eb6-132">![Rempli forme](./media/aboutgdip02-art21.gif "AboutGdip02_Art21")</span><span class="sxs-lookup"><span data-stu-id="d7eb6-132">![Filled Shape](./media/aboutgdip02-art21.gif "AboutGdip02_Art21")</span></span>  
  
 <span data-ttu-id="d7eb6-133">Un pinceau de dégradé de chemin d’accès peut être configuré pour modifier la couleur à mesure que vous déplacez à partir du centre de la forme vers le bord.</span><span class="sxs-lookup"><span data-stu-id="d7eb6-133">A path gradient brush can be configured to change color as you move from the center of a shape toward the edge.</span></span>  
  
 <span data-ttu-id="d7eb6-134">![Rempli forme](./media/aboutgdip02-art22.gif "AboutGdip02_Art22")</span><span class="sxs-lookup"><span data-stu-id="d7eb6-134">![Filled Shape](./media/aboutgdip02-art22.gif "AboutGdip02_Art22")</span></span>  
  
 <span data-ttu-id="d7eb6-135">Pinceaux de dégradé de chemin d’accès est très souples.</span><span class="sxs-lookup"><span data-stu-id="d7eb6-135">Path gradient brushes are quite flexible.</span></span> <span data-ttu-id="d7eb6-136">Pinceau de dégradé utilisé pour remplir le triangle dans les modifications suivantes d’illustration progressivement du rouge au centre à chacune des trois couleurs différentes sur les sommets.</span><span class="sxs-lookup"><span data-stu-id="d7eb6-136">The gradient brush used to fill the triangle in the following illustration changes gradually from red at the center to each of three different colors at the vertices.</span></span>  
  
 <span data-ttu-id="d7eb6-137">![Rempli forme](./media/aboutgdip02-art23.gif "AboutGdip02_Art23")</span><span class="sxs-lookup"><span data-stu-id="d7eb6-137">![Filled Shape](./media/aboutgdip02-art23.gif "AboutGdip02_Art23")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7eb6-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d7eb6-138">See also</span></span>

- <xref:System.Drawing.SolidBrush?displayProperty=nameWithType>
- <xref:System.Drawing.Drawing2D.HatchBrush?displayProperty=nameWithType>
- <xref:System.Drawing.TextureBrush?displayProperty=nameWithType>
- <xref:System.Drawing.Drawing2D.LinearGradientBrush?displayProperty=nameWithType>
- [<span data-ttu-id="d7eb6-139">Lignes, courbes et formes</span><span class="sxs-lookup"><span data-stu-id="d7eb6-139">Lines, Curves, and Shapes</span></span>](lines-curves-and-shapes.md)
- [<span data-ttu-id="d7eb6-140">Guide pratique pour Dessiner un Rectangle rempli dans un formulaire Windows</span><span class="sxs-lookup"><span data-stu-id="d7eb6-140">How to: Draw a Filled Rectangle on a Windows Form</span></span>](how-to-draw-a-filled-rectangle-on-a-windows-form.md)
- [<span data-ttu-id="d7eb6-141">Guide pratique pour Dessiner une Ellipse remplie dans un formulaire Windows</span><span class="sxs-lookup"><span data-stu-id="d7eb6-141">How to: Draw a Filled Ellipse on a Windows Form</span></span>](how-to-draw-a-filled-ellipse-on-a-windows-form.md)
