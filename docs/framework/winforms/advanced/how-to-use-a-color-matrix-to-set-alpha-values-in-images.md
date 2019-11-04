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
# <a name="how-to-use-a-color-matrix-to-set-alpha-values-in-images"></a>Comment : utiliser une matrice de couleurs pour définir des valeurs alpha dans des images
La classe <xref:System.Drawing.Bitmap> (qui hérite de la classe <xref:System.Drawing.Image>) et la classe <xref:System.Drawing.Imaging.ImageAttributes> fournissent des fonctionnalités permettant d’obtenir et de définir des valeurs de pixel. Vous pouvez utiliser la classe <xref:System.Drawing.Imaging.ImageAttributes> pour modifier les valeurs alpha pour une image entière, ou vous pouvez appeler la méthode <xref:System.Drawing.Bitmap.SetPixel%2A> de la classe <xref:System.Drawing.Bitmap> pour modifier des valeurs de pixel individuelles.  
  
## <a name="example"></a>Exemple  
 La classe <xref:System.Drawing.Imaging.ImageAttributes> possède de nombreuses propriétés que vous pouvez utiliser pour modifier des images pendant le rendu. Dans l’exemple suivant, un objet <xref:System.Drawing.Imaging.ImageAttributes> est utilisé pour définir toutes les valeurs alpha à 80% de ce qu’ils étaient. Pour ce faire, initialisez une matrice de couleurs et définissez la valeur de mise à l’échelle alpha dans la matrice sur 0,8. L’adresse de la matrice de couleurs est transmise à la méthode <xref:System.Drawing.Imaging.ImageAttributes.SetColorMatrix%2A> de l’objet <xref:System.Drawing.Imaging.ImageAttributes>, et l’objet <xref:System.Drawing.Imaging.ImageAttributes> est passé à la méthode <xref:System.Drawing.Graphics.DrawString%2A> de l’objet <xref:System.Drawing.Graphics>.  
  
 Pendant le rendu, les valeurs alpha dans le bitmap sont converties en 80 pour cent de ce qu’elles étaient. Une image est alors fusionnée avec l’arrière-plan. Comme le montre l’illustration suivante, l’image bitmap semble transparente ; vous pouvez voir la ligne noire pleine.  
  
 ![Capture d’écran de la fusion alpha à l’aide d’une matrice.](./media/how-to-use-a-color-matrix-to-set-alpha-values-in-images/alpha-blending-matrix.png "image2")  
  
 Lorsque l’image se trouve sur la partie blanche de l’arrière-plan, l’image a été fusionnée avec la couleur blanche. Lorsque l’image dépasse la ligne noire, l’image est fusionnée avec la couleur noire.  
  
 [!code-csharp[System.Drawing.AlphaBlending#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.AlphaBlending#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 L’exemple précédent est conçu pour être utilisé avec Windows Forms, et il requiert <xref:System.Windows.Forms.PaintEventArgs> `e`, qui est un paramètre de <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Voir aussi

- [Graphiques et dessins dans Windows Forms](graphics-and-drawing-in-windows-forms.md)
- [Fusion alpha de lignes et de remplissages](alpha-blending-lines-and-fills.md)
