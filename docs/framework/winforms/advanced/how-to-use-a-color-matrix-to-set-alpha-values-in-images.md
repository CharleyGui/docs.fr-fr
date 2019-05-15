---
title: 'Procédure : utiliser une matrice de couleurs pour définir des valeurs alpha dans des images'
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
ms.openlocfilehash: fd63380e04eeb4b7ec7ed7d59032309ea7446507
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65593170"
---
# <a name="how-to-use-a-color-matrix-to-set-alpha-values-in-images"></a><span data-ttu-id="75c4a-102">Procédure : utiliser une matrice de couleurs pour définir des valeurs alpha dans des images</span><span class="sxs-lookup"><span data-stu-id="75c4a-102">How to: Use a Color Matrix to Set Alpha Values in Images</span></span>
<span data-ttu-id="75c4a-103">Le <xref:System.Drawing.Bitmap> classe (qui hérite de la <xref:System.Drawing.Image> classe) et le <xref:System.Drawing.Imaging.ImageAttributes> classe fournit des fonctionnalités pour obtenir et définir des valeurs en pixels.</span><span class="sxs-lookup"><span data-stu-id="75c4a-103">The <xref:System.Drawing.Bitmap> class (which inherits from the <xref:System.Drawing.Image> class) and the <xref:System.Drawing.Imaging.ImageAttributes> class provide functionality for getting and setting pixel values.</span></span> <span data-ttu-id="75c4a-104">Vous pouvez utiliser la <xref:System.Drawing.Imaging.ImageAttributes> classe pour modifier la valeur alpha de valeurs pour l’intégralité d’une image, ou vous pouvez appeler la <xref:System.Drawing.Bitmap.SetPixel%2A> méthode de la <xref:System.Drawing.Bitmap> classe pour modifier les valeurs de pixel individuelles.</span><span class="sxs-lookup"><span data-stu-id="75c4a-104">You can use the <xref:System.Drawing.Imaging.ImageAttributes> class to modify the alpha values for an entire image, or you can call the <xref:System.Drawing.Bitmap.SetPixel%2A> method of the <xref:System.Drawing.Bitmap> class to modify individual pixel values.</span></span>  
  
## <a name="example"></a><span data-ttu-id="75c4a-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="75c4a-105">Example</span></span>  
 <span data-ttu-id="75c4a-106">Le <xref:System.Drawing.Imaging.ImageAttributes> classe comporte plusieurs propriétés que vous pouvez utiliser pour modifier les images pendant le rendu.</span><span class="sxs-lookup"><span data-stu-id="75c4a-106">The <xref:System.Drawing.Imaging.ImageAttributes> class has many properties that you can use to modify images during rendering.</span></span> <span data-ttu-id="75c4a-107">Dans l’exemple suivant, un <xref:System.Drawing.Imaging.ImageAttributes> objet est utilisé pour définir toutes les valeurs alphabétiques à 80 % de leur nature.</span><span class="sxs-lookup"><span data-stu-id="75c4a-107">In the following example, an <xref:System.Drawing.Imaging.ImageAttributes> object is used to set all the alpha values to 80 percent of what they were.</span></span> <span data-ttu-id="75c4a-108">Pour cela, en initialisant une matrice de couleurs et en définissant la valeur alpha de mise à l’échelle de la valeur de la matrice à 0,8.</span><span class="sxs-lookup"><span data-stu-id="75c4a-108">This is done by initializing a color matrix and setting the alpha scaling value in the matrix to 0.8.</span></span> <span data-ttu-id="75c4a-109">L’adresse de la matrice des couleurs est passé à la <xref:System.Drawing.Imaging.ImageAttributes.SetColorMatrix%2A> méthode de la <xref:System.Drawing.Imaging.ImageAttributes> objet et le <xref:System.Drawing.Imaging.ImageAttributes> objet est passé à la <xref:System.Drawing.Graphics.DrawString%2A> méthode de la <xref:System.Drawing.Graphics> objet.</span><span class="sxs-lookup"><span data-stu-id="75c4a-109">The address of the color matrix is passed to the <xref:System.Drawing.Imaging.ImageAttributes.SetColorMatrix%2A> method of the <xref:System.Drawing.Imaging.ImageAttributes> object, and the <xref:System.Drawing.Imaging.ImageAttributes> object is passed to the <xref:System.Drawing.Graphics.DrawString%2A> method of the <xref:System.Drawing.Graphics> object.</span></span>  
  
 <span data-ttu-id="75c4a-110">Pendant le rendu, les valeurs alphabétiques dans la bitmap sont converties à 80 % de leur nature.</span><span class="sxs-lookup"><span data-stu-id="75c4a-110">During rendering, the alpha values in the bitmap are converted to 80 percent of what they were.</span></span> <span data-ttu-id="75c4a-111">Cela entraîne une image qui est fusionnée avec l’arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="75c4a-111">This results in an image that is blended with the background.</span></span> <span data-ttu-id="75c4a-112">Comme le montre l’illustration suivante, l’image bitmap semble transparente ; Vous pouvez voir la ligne noire unie par son intermédiaire.</span><span class="sxs-lookup"><span data-stu-id="75c4a-112">As the following illustration shows, the bitmap image looks transparent; you can see the solid black line through it.</span></span>  
  
 <span data-ttu-id="75c4a-113">![Fusion alpha utilisant une matrice](./media/image2.png "image2")</span><span class="sxs-lookup"><span data-stu-id="75c4a-113">![Alpha Blending Using a Matrix](./media/image2.png "image2")</span></span>  
  
 <span data-ttu-id="75c4a-114">Où l’image est au-dessus de la partie blanche de l’arrière-plan, l’image a été fusionnée avec la couleur blanche.</span><span class="sxs-lookup"><span data-stu-id="75c4a-114">Where the image is over the white portion of the background, the image has been blended with the color white.</span></span> <span data-ttu-id="75c4a-115">L’image où l’image dépasse la ligne noire, est fusionnée avec la couleur noire.</span><span class="sxs-lookup"><span data-stu-id="75c4a-115">Where the image crosses the black line, the image is blended with the color black.</span></span>  
  
 [!code-csharp[System.Drawing.AlphaBlending#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.AlphaBlending#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="75c4a-116">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="75c4a-116">Compiling the Code</span></span>  
 <span data-ttu-id="75c4a-117">L’exemple précédent est conçu pour une utilisation avec Windows Forms et nécessite <xref:System.Windows.Forms.PaintEventArgs> `e`, qui est un paramètre de <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="75c4a-117">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75c4a-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="75c4a-118">See also</span></span>

- [<span data-ttu-id="75c4a-119">Graphiques et dessins dans Windows Forms</span><span class="sxs-lookup"><span data-stu-id="75c4a-119">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="75c4a-120">Fusion alpha de lignes et de remplissages</span><span class="sxs-lookup"><span data-stu-id="75c4a-120">Alpha Blending Lines and Fills</span></span>](alpha-blending-lines-and-fills.md)
