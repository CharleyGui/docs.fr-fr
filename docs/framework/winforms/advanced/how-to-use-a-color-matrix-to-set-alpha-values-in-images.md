---
title: 'Comment : utiliser une matrice de couleurs pour définir des valeurs alpha dans des images'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- images [Windows Forms], using color matrices for semi-transparent
- transparency [Windows Forms], color matrices
- matrices [Windows Forms], alpha values
- bitmaps [Windows Forms], using color matrices for semi-transparent
ms.assetid: a27121e6-f7e9-4c09-84e2-f05aa9d2a1bb
ms.openlocfilehash: 73e820845d040856a0ae367da8b9371ad6afa142
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73423737"
---
# <a name="how-to-use-a-color-matrix-to-set-alpha-values-in-images"></a><span data-ttu-id="373fe-102">Comment : utiliser une matrice de couleurs pour définir des valeurs alpha dans des images</span><span class="sxs-lookup"><span data-stu-id="373fe-102">How to: Use a Color Matrix to Set Alpha Values in Images</span></span>
<span data-ttu-id="373fe-103">La classe <xref:System.Drawing.Bitmap> (qui hérite de la classe <xref:System.Drawing.Image>) et la classe <xref:System.Drawing.Imaging.ImageAttributes> fournissent des fonctionnalités permettant d’obtenir et de définir des valeurs de pixel.</span><span class="sxs-lookup"><span data-stu-id="373fe-103">The <xref:System.Drawing.Bitmap> class (which inherits from the <xref:System.Drawing.Image> class) and the <xref:System.Drawing.Imaging.ImageAttributes> class provide functionality for getting and setting pixel values.</span></span> <span data-ttu-id="373fe-104">Vous pouvez utiliser la classe <xref:System.Drawing.Imaging.ImageAttributes> pour modifier les valeurs alpha pour une image entière, ou vous pouvez appeler la méthode <xref:System.Drawing.Bitmap.SetPixel%2A> de la classe <xref:System.Drawing.Bitmap> pour modifier des valeurs de pixel individuelles.</span><span class="sxs-lookup"><span data-stu-id="373fe-104">You can use the <xref:System.Drawing.Imaging.ImageAttributes> class to modify the alpha values for an entire image, or you can call the <xref:System.Drawing.Bitmap.SetPixel%2A> method of the <xref:System.Drawing.Bitmap> class to modify individual pixel values.</span></span>  
  
## <a name="example"></a><span data-ttu-id="373fe-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="373fe-105">Example</span></span>  
 <span data-ttu-id="373fe-106">La classe <xref:System.Drawing.Imaging.ImageAttributes> possède de nombreuses propriétés que vous pouvez utiliser pour modifier des images pendant le rendu.</span><span class="sxs-lookup"><span data-stu-id="373fe-106">The <xref:System.Drawing.Imaging.ImageAttributes> class has many properties that you can use to modify images during rendering.</span></span> <span data-ttu-id="373fe-107">Dans l’exemple suivant, un objet <xref:System.Drawing.Imaging.ImageAttributes> est utilisé pour définir toutes les valeurs alpha à 80% de ce qu’ils étaient.</span><span class="sxs-lookup"><span data-stu-id="373fe-107">In the following example, an <xref:System.Drawing.Imaging.ImageAttributes> object is used to set all the alpha values to 80 percent of what they were.</span></span> <span data-ttu-id="373fe-108">Pour ce faire, initialisez une matrice de couleurs et définissez la valeur de mise à l’échelle alpha dans la matrice sur 0,8.</span><span class="sxs-lookup"><span data-stu-id="373fe-108">This is done by initializing a color matrix and setting the alpha scaling value in the matrix to 0.8.</span></span> <span data-ttu-id="373fe-109">L’adresse de la matrice de couleurs est transmise à la méthode <xref:System.Drawing.Imaging.ImageAttributes.SetColorMatrix%2A> de l’objet <xref:System.Drawing.Imaging.ImageAttributes>, et l’objet <xref:System.Drawing.Imaging.ImageAttributes> est passé à la méthode <xref:System.Drawing.Graphics.DrawString%2A> de l’objet <xref:System.Drawing.Graphics>.</span><span class="sxs-lookup"><span data-stu-id="373fe-109">The address of the color matrix is passed to the <xref:System.Drawing.Imaging.ImageAttributes.SetColorMatrix%2A> method of the <xref:System.Drawing.Imaging.ImageAttributes> object, and the <xref:System.Drawing.Imaging.ImageAttributes> object is passed to the <xref:System.Drawing.Graphics.DrawString%2A> method of the <xref:System.Drawing.Graphics> object.</span></span>  
  
 <span data-ttu-id="373fe-110">Pendant le rendu, les valeurs alpha dans le bitmap sont converties en 80 pour cent de ce qu’elles étaient.</span><span class="sxs-lookup"><span data-stu-id="373fe-110">During rendering, the alpha values in the bitmap are converted to 80 percent of what they were.</span></span> <span data-ttu-id="373fe-111">Une image est alors fusionnée avec l’arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="373fe-111">This results in an image that is blended with the background.</span></span> <span data-ttu-id="373fe-112">Comme le montre l’illustration suivante, l’image bitmap semble transparente ; vous pouvez voir la ligne noire pleine.</span><span class="sxs-lookup"><span data-stu-id="373fe-112">As the following illustration shows, the bitmap image looks transparent; you can see the solid black line through it.</span></span>  
  
 <span data-ttu-id="373fe-113">![Capture d’écran de la fusion alpha à l’aide d’une matrice.](./media/how-to-use-a-color-matrix-to-set-alpha-values-in-images/alpha-blending-matrix.png "image2")</span><span class="sxs-lookup"><span data-stu-id="373fe-113">![Screenshot of alpha blending using a matrix.](./media/how-to-use-a-color-matrix-to-set-alpha-values-in-images/alpha-blending-matrix.png "image2")</span></span>  
  
 <span data-ttu-id="373fe-114">Lorsque l’image se trouve sur la partie blanche de l’arrière-plan, l’image a été fusionnée avec la couleur blanche.</span><span class="sxs-lookup"><span data-stu-id="373fe-114">Where the image is over the white portion of the background, the image has been blended with the color white.</span></span> <span data-ttu-id="373fe-115">Lorsque l’image dépasse la ligne noire, l’image est fusionnée avec la couleur noire.</span><span class="sxs-lookup"><span data-stu-id="373fe-115">Where the image crosses the black line, the image is blended with the color black.</span></span>  
  
 [!code-csharp[System.Drawing.AlphaBlending#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.AlphaBlending#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="373fe-116">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="373fe-116">Compiling the Code</span></span>  
 <span data-ttu-id="373fe-117">L’exemple précédent est conçu pour être utilisé avec Windows Forms, et il requiert <xref:System.Windows.Forms.PaintEventArgs> `e`, qui est un paramètre de <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="373fe-117">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="373fe-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="373fe-118">See also</span></span>

- [<span data-ttu-id="373fe-119">Graphiques et dessins dans Windows Forms</span><span class="sxs-lookup"><span data-stu-id="373fe-119">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="373fe-120">Fusion alpha de lignes et de remplissages</span><span class="sxs-lookup"><span data-stu-id="373fe-120">Alpha Blending Lines and Fills</span></span>](alpha-blending-lines-and-fills.md)
