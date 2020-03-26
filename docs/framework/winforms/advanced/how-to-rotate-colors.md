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
# <a name="how-to-rotate-colors"></a>Comment : faire pivoter des couleurs
La rotation dans un espace de couleur en quatre dimensions est difficile à visualiser. Nous pouvons faciliter la visualisation de la rotation en acceptant de garder l’un des composants de couleur fixe. Supposons que nous acceptions de maintenir le composant alpha fixé à 1 (entièrement opaque). Ensuite, nous pouvons visualiser un espace de couleur en trois dimensions avec des axes rouges, verts et bleus comme le montre l’illustration suivante.  
  
 ![Illustration qui montre la rotation avec des haches rouges, vertes et bleues.](./media/how-to-rotate-colors/rotation-red-green-blue-axes.gif)  
  
 Une couleur peut être considérée comme un point dans l’espace 3D. Par exemple, le point (1, 0, 0) dans l’espace représente la couleur rouge, et le point (0, 1, 0) dans l’espace représente la couleur verte.  
  
 L’illustration suivante montre ce que signifie faire pivoter la couleur (1, 0, 0) à travers un angle de 60 degrés dans le plan Rouge-Vert. La rotation dans un avion parallèle à l’avion Rouge-Vert peut être considérée comme une rotation sur l’axe bleu.  
  
 ![Illustration qui montre la rotation au sujet de l’axe bleu.](./media/how-to-rotate-colors/rotation-about-blue-axis.gif)  
  
 L’illustration suivante montre comment initialiser une matrice de couleurs pour effectuer des rotations sur chacun des trois axes de coordonnées (rouge, vert, bleu) :  
  
 ![Initialiser une matrice de couleur pour effectuer des rotations d’environ trois axes.](./media/how-to-rotate-colors/rotation-about-three-axes.gif)  
  
## <a name="example"></a>Exemple  
 L’exemple suivant prend une image qui est toute une couleur (1, 0, 0,6) et applique une rotation de 60 degrés sur l’axe bleu. L’angle de la rotation est balayé dans un avion parallèle au plan rouge-vert.  
  
 L’illustration suivante montre l’image originale à gauche et l’image en rotation des couleurs à droite :  
  
 ![Illustration qui montre l’image originale et l’image de couleur-rotation.](./media/how-to-rotate-colors/original-color-rotated-images.png)  
  
 L’illustration suivante montre une visualisation de la rotation des couleurs effectuée dans le code suivant :
  
 ![Illustration qui montre la visualisation de la rotation des couleurs.](./media/how-to-rotate-colors/visualization-color-rotation.gif)  
  
 [!code-csharp[System.Drawing.RotateColors#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RotateColors/CS/Form1.cs#1)]
 [!code-vb[System.Drawing.RotateColors#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RotateColors/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 L’exemple précédent est conçu pour une <xref:System.Windows.Forms.PaintEventArgs> `e`utilisation avec Windows Forms, et il nécessite , qui est un paramètre du gestionnaire d’événements. <xref:System.Windows.Forms.Control.Paint> Remplacez-le par `RotationInput.bmp` un nom de fichier d’image et un chemin valide sur votre système.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Drawing.Imaging.ColorMatrix>
- <xref:System.Drawing.Imaging.ImageAttributes>
- [Graphiques et dessins dans les Windows Forms](graphics-and-drawing-in-windows-forms.md)
- [Recoloriage des images](recoloring-images.md)
