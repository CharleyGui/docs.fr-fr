---
title: 'Comment : faire pivoter des couleurs'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- colors [Windows Forms], rotating
- examples [Windows Forms], rotating colors
ms.assetid: e2e4c300-159c-4f4a-9b56-103b0f7cbc05
ms.openlocfilehash: 8d2717dd7b819e963126072279b361fda02188bc
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80111333"
---
# <a name="how-to-rotate-colors"></a><span data-ttu-id="501ea-102">Comment : faire pivoter des couleurs</span><span class="sxs-lookup"><span data-stu-id="501ea-102">How to: Rotate Colors</span></span>
<span data-ttu-id="501ea-103">La rotation dans un espace de couleur en quatre dimensions est difficile à visualiser.</span><span class="sxs-lookup"><span data-stu-id="501ea-103">Rotation in a four-dimensional color space is difficult to visualize.</span></span> <span data-ttu-id="501ea-104">Nous pouvons faciliter la visualisation de la rotation en acceptant de garder l’un des composants de couleur fixe.</span><span class="sxs-lookup"><span data-stu-id="501ea-104">We can make it easier to visualize rotation by agreeing to keep one of the color components fixed.</span></span> <span data-ttu-id="501ea-105">Supposons que nous acceptions de maintenir le composant alpha fixé à 1 (entièrement opaque).</span><span class="sxs-lookup"><span data-stu-id="501ea-105">Suppose we agree to keep the alpha component fixed at 1 (fully opaque).</span></span> <span data-ttu-id="501ea-106">Ensuite, nous pouvons visualiser un espace de couleur en trois dimensions avec des axes rouges, verts et bleus comme le montre l’illustration suivante.</span><span class="sxs-lookup"><span data-stu-id="501ea-106">Then we can visualize a three-dimensional color space with red, green, and blue axes as shown in the following illustration.</span></span>  
  
 ![Illustration qui montre la rotation avec des haches rouges, vertes et bleues.](./media/how-to-rotate-colors/rotation-red-green-blue-axes.gif)  
  
 <span data-ttu-id="501ea-108">Une couleur peut être considérée comme un point dans l’espace 3D.</span><span class="sxs-lookup"><span data-stu-id="501ea-108">A color can be thought of as a point in 3D space.</span></span> <span data-ttu-id="501ea-109">Par exemple, le point (1, 0, 0) dans l’espace représente la couleur rouge, et le point (0, 1, 0) dans l’espace représente la couleur verte.</span><span class="sxs-lookup"><span data-stu-id="501ea-109">For example, the point (1, 0, 0) in space represents the color red, and the point (0, 1, 0) in space represents the color green.</span></span>  
  
 <span data-ttu-id="501ea-110">L’illustration suivante montre ce que signifie faire pivoter la couleur (1, 0, 0) à travers un angle de 60 degrés dans le plan Rouge-Vert.</span><span class="sxs-lookup"><span data-stu-id="501ea-110">The following illustration shows what it means to rotate the color (1, 0, 0) through an angle of 60 degrees in the Red-Green plane.</span></span> <span data-ttu-id="501ea-111">La rotation dans un avion parallèle à l’avion Rouge-Vert peut être considérée comme une rotation sur l’axe bleu.</span><span class="sxs-lookup"><span data-stu-id="501ea-111">Rotation in a plane parallel to the Red-Green plane can be thought of as rotation about the blue axis.</span></span>  
  
 ![Illustration qui montre la rotation au sujet de l’axe bleu.](./media/how-to-rotate-colors/rotation-about-blue-axis.gif)  
  
 <span data-ttu-id="501ea-113">L’illustration suivante montre comment initialiser une matrice de couleurs pour effectuer des rotations sur chacun des trois axes de coordonnées (rouge, vert, bleu) :</span><span class="sxs-lookup"><span data-stu-id="501ea-113">The following illustration shows how to initialize a color matrix to perform rotations about each of the three coordinate axes (red, green, blue):</span></span>  
  
 ![Initialiser une matrice de couleur pour effectuer des rotations d’environ trois axes.](./media/how-to-rotate-colors/rotation-about-three-axes.gif)  
  
## <a name="example"></a><span data-ttu-id="501ea-115">Exemple</span><span class="sxs-lookup"><span data-stu-id="501ea-115">Example</span></span>  
 <span data-ttu-id="501ea-116">L’exemple suivant prend une image qui est toute une couleur (1, 0, 0,6) et applique une rotation de 60 degrés sur l’axe bleu.</span><span class="sxs-lookup"><span data-stu-id="501ea-116">The following example takes an image that is all one color (1, 0, 0.6) and applies a 60-degree rotation about the blue axis.</span></span> <span data-ttu-id="501ea-117">L’angle de la rotation est balayé dans un avion parallèle au plan rouge-vert.</span><span class="sxs-lookup"><span data-stu-id="501ea-117">The angle of the rotation is swept out in a plane that is parallel to the red-green plane.</span></span>  
  
 <span data-ttu-id="501ea-118">L’illustration suivante montre l’image originale à gauche et l’image en rotation des couleurs à droite :</span><span class="sxs-lookup"><span data-stu-id="501ea-118">The following illustration shows the original image on the left and the color-rotated image on the right:</span></span>  
  
 ![Illustration qui montre l’image originale et l’image de couleur-rotation.](./media/how-to-rotate-colors/original-color-rotated-images.png)  
  
 <span data-ttu-id="501ea-120">L’illustration suivante montre une visualisation de la rotation des couleurs effectuée dans le code suivant :</span><span class="sxs-lookup"><span data-stu-id="501ea-120">The following illustration shows a visualization of the color rotation performed in the following code:</span></span>
  
 ![Illustration qui montre la visualisation de la rotation des couleurs.](./media/how-to-rotate-colors/visualization-color-rotation.gif)  
  
 [!code-csharp[System.Drawing.RotateColors#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RotateColors/CS/Form1.cs#1)]
 [!code-vb[System.Drawing.RotateColors#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RotateColors/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="501ea-122">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="501ea-122">Compiling the Code</span></span>  
 <span data-ttu-id="501ea-123">L’exemple précédent est conçu pour une <xref:System.Windows.Forms.PaintEventArgs> `e`utilisation avec Windows Forms, et il nécessite , qui est un paramètre du gestionnaire d’événements. <xref:System.Windows.Forms.Control.Paint></span><span class="sxs-lookup"><span data-stu-id="501ea-123">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="501ea-124">Remplacez-le par `RotationInput.bmp` un nom de fichier d’image et un chemin valide sur votre système.</span><span class="sxs-lookup"><span data-stu-id="501ea-124">Replace `RotationInput.bmp` with an image file name and path valid on your system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="501ea-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="501ea-125">See also</span></span>

- <xref:System.Drawing.Imaging.ColorMatrix>
- <xref:System.Drawing.Imaging.ImageAttributes>
- [<span data-ttu-id="501ea-126">Graphiques et dessins dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="501ea-126">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="501ea-127">Recoloriage des images</span><span class="sxs-lookup"><span data-stu-id="501ea-127">Recoloring Images</span></span>](recoloring-images.md)
