---
title: 'Procédure : utiliser une matrice de couleurs pour transformer une seule couleur'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- image colors [Windows Forms], transforming
- color matrices [Windows Forms], using
ms.assetid: 44df4556-a433-49c0-ac0f-9a12063a5860
ms.openlocfilehash: 2df74e022b842f7e5c9ff80f6aeddfce51af5eab
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67505820"
---
# <a name="how-to-use-a-color-matrix-to-transform-a-single-color"></a>Procédure : utiliser une matrice de couleurs pour transformer une seule couleur
GDI + offre la <xref:System.Drawing.Image> et <xref:System.Drawing.Bitmap> classes pour stocker et manipuler des images. <xref:System.Drawing.Image> et <xref:System.Drawing.Bitmap> objets stockent la couleur de chaque pixel comme un nombre 32 bits : 8 bits pour chaque rouge, vert, bleu et alpha. Chacun des quatre composants est un nombre compris entre 0 et 255, 0 représentant aucune intensité et une intensité maximale de 255. Le composant alpha spécifie la transparence de la couleur : 0 est totalement transparent et 255 est entièrement opaque.  
  
 Un vecteur de couleur est un tuple de 4 du formulaire (rouge, vert, bleu, alpha). Par exemple, le vecteur de couleur (0, 255, 0, 255) représente une couleur opaque qui comporte aucune rouge ou bleu, mais a vert à intensité complète.  
  
 Une autre convention pour représenter des couleurs utilise le numéro 1 pour l’intensité maximale. À l’aide de cette convention, la couleur décrite dans le paragraphe précédent va être représentée par le vecteur (0, 1, 0, 1). GDI + utilise la convention de 1 comme intensité complète lorsqu’il effectue des transformations de couleur.  
  
 Vous pouvez appliquer des transformations linéaires (rotation, mise à l’échelle et autres) aux vecteurs de couleurs en multipliant ces vecteurs par une matrice 4 × 4. Toutefois, vous ne pouvez pas utiliser une matrice 4 × 4 pour effectuer une traduction (non linéaire). Si vous ajoutez une cinquième coordonnée fictive (par exemple, le nombre 1) à chaque vecteur de couleur, vous pouvez utiliser une matrice 5 x 5 pour appliquer n’importe quelle combinaison de transformations linéaires et traductions. Une transformation comprenant une transformation linéaire suivie d’une traduction est appelée une transformation affine.  
  
 Par exemple, supposons que vous souhaitez commencer par la couleur (0.2, 0.0, 0.4, 1.0) et appliquer les transformations suivantes :  
  
1. Doubler la composante rouge  
  
2. Ajouter 0,2 aux composants rouges, vert et bleus  
  
 La multiplication de matrice suivante effectue la paire de transformations dans l’ordre indiqué.  
  
 ![Capture d’écran d’une matrice de multiplication de transformation.](./media/how-to-use-a-color-matrix-to-transform-a-single-color/multiplication-color-matrix.gif)
  
 Les éléments d’une matrice de couleurs sont indexés (base zéro) en ligne et de colonne. Par exemple, l’entrée dans la cinquième ligne et la troisième colonne de matrice M est représentée par M [4] [2].  
  
 La matrice d’identité 5 × 5 (indiqué dans l’illustration suivante) a 1 sur la diagonale et 0 partout ailleurs. Si vous multipliez un vecteur de couleur par la matrice d’identité, le vecteur de couleur ne change pas. Un moyen pratique pour former la matrice d’une transformation de couleur consiste à commencer par la matrice d’identité et apportez une petite modification qui produit la transformation souhaitée.  
  
 ![Capture d’écran d’une matrice d’identité 5 x 5 pour la transformation de couleur.](./media/how-to-use-a-color-matrix-to-transform-a-single-color/5x5-identity-matrix-color-transformation.gif)  
  
 Pour obtenir une présentation plus détaillée des matrices et des transformations, consultez [systèmes de coordonnées et Transformations](coordinate-systems-and-transformations.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant prend une image qui est une couleur (0.2, 0.0, 0.4, 1.0) et applique la transformation décrite dans les paragraphes précédents.  
  
 L’illustration suivante montre l’image d’origine sur la gauche et l’image transformée sur la droite.  
  
 ![Un carré violet sur la gauche et un carré magenta sur la droite.](./media/how-to-use-a-color-matrix-to-transform-a-single-color/color-transformation.png)  
  
 Le code dans l’exemple suivant utilise les étapes suivantes pour effectuer le recoloriage :  
  
1. Initialiser un <xref:System.Drawing.Imaging.ColorMatrix> objet.  
  
2. Créer un <xref:System.Drawing.Imaging.ImageAttributes> de l’objet et de transmettre le <xref:System.Drawing.Imaging.ColorMatrix> de l’objet à la <xref:System.Drawing.Imaging.ImageAttributes.SetColorMatrix%2A> méthode de la <xref:System.Drawing.Imaging.ImageAttributes> objet.  
  
3. Passer le <xref:System.Drawing.Imaging.ImageAttributes> de l’objet à la <xref:System.Drawing.Graphics.DrawImage%2A> méthode d’un <xref:System.Drawing.Graphics> objet.  
  
 [!code-csharp[System.Drawing.RecoloringImages#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.RecoloringImages#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 L’exemple précédent est conçu pour une utilisation avec Windows Forms et nécessite <xref:System.Windows.Forms.PaintEventArgs> `e`, qui est un paramètre de la <xref:System.Windows.Forms.Control.Paint> Gestionnaire d’événements.  
  
## <a name="see-also"></a>Voir aussi

- [Recoloriage des images](recoloring-images.md)
- [Systèmes de coordonnées et transformations](coordinate-systems-and-transformations.md)
