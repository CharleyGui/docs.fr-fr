---
title: Représentation matricielle des transformations
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- composite transformations
- transformations [Windows Forms], linear
- matrices
- translations in matrix representation
- transformations [Windows Forms], composite
- vectors
- linear transformations
- transformations [Windows Forms], matrix representation of
- transformations [Windows Forms], translation
- affine transformations
ms.assetid: 0659fe00-9e0c-41c4-9118-016f2404c905
ms.openlocfilehash: ceaad7b4bb5a70a890d261e39bc608becb388c17
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67505640"
---
# <a name="matrix-representation-of-transformations"></a>Représentation matricielle des transformations
Une matrice m × n est un ensemble de nombres organisés dans des millions de lignes et colonnes n. L’illustration suivante montre plusieurs matrices.  
  
 ![Transformations](./media/aboutgdip05-art04.gif "AboutGdip05_art04")  
  
 Vous pouvez ajouter deux matrices de même taille en ajoutant des éléments individuels. L’illustration suivante montre deux exemples d’ajout de la matrice.  
  
 ![Transformations](./media/aboutgdip05-art05.gif "AboutGdip05_art05")  
  
 Une matrice m × n peut être multipliée par une matrice de p × n, et le résultat est une matrice de p × m. Le nombre de colonnes dans la première matrice doit être le même que le nombre de lignes dans la deuxième matrice. Par exemple, une matrice 4 × 2 peut être multipliée par une matrice 2 × 3 pour produire une matrice 4 × 3.  
  
 Points dans le plan et les lignes et les colonnes d’une matrice peuvent être considérés comme des vecteurs. Par exemple, (2, 5) est un vecteur avec deux composants et (3, 7, 1) est un vecteur à trois composants. Le produit scalaire de deux vecteurs est défini comme suit :  
  
 (a, b) • (c, d) = ac + bd  
  
 (a, b, c) • (d, e, f) = ad + be + cf  
  
 Par exemple, le produit scalaire de (2, 3) et (5, 4) est (2)(5) + (3)(4) = 22. Le produit scalaire de (2, 5, 1) et (4, 3, 1) est (2)(4) + (5)(3) + (1)(1) = 24. Notez que le produit scalaire de deux vecteurs est un nombre, pas un autre vecteur. Notez également que vous pouvez calculer le produit scalaire uniquement si les deux vecteurs ont le même nombre de composants.  
  
 A(i, j) permettent d’être l’entrée de la matrice A dans la ligne i et la colonne j. Par exemple, A (3, 2) est l’entrée de la matrice A dans la ligne 3 et la 2e colonne. Supposons que A, B et C sont des matrices et AB = C. Les entrées de C sont calculées comme suit :  
  
 C (i, j) = (ligne i de A) • (colonne j de B)  
  
 L’illustration suivante montre plusieurs exemples de multiplication de matrice.  
  
 ![Transformations](./media/aboutgdip05-art06.gif "AboutGdip05_art06")  
  
 Si vous pensez que d’un point dans un plan est une 1 matrice × 2, vous pouvez transformer ce point en la multipliant par une matrice 2 × 2. L’illustration suivante montre plusieurs transformations appliquées au point (2, 1).  
  
 ![Transformations](./media/aboutgdip05-art07.gif "AboutGdip05_art07")  
  
 Toutes les transformations indiquées dans la figure précédente sont des transformations linéaires. Certaines transformations, telles que la traduction, ne sont pas linéaires et ne peuvent pas être exprimées en tant que la multiplication par une matrice 2 × 2. Supposons que vous vouliez pour commencer le point (2, 1), faire pivoter de 90 degrés, translation de 3 unités sur l’axe x et la traduire 4 unités sur l’axe y. Vous pouvez y parvenir à l’aide d’une multiplication de matrice suivie d’une addition de matrice.  
  
 ![Transformations](./media/aboutgdip05-art08.gif "AboutGdip05_art08")  
  
 Une transformation linéaire (multiplication par une matrice 2 × 2) suivie d’une traduction (ajout d’une 1 matrice × 2) est appelée une transformation affine. Une alternative au stockage d’une transformation affine dans une paire de matrices (une pour la partie linéaire) et une pour la traduction consiste à stocker la transformation ensemble dans une matrice 3 x 3. Pour que cela fonctionne, un point dans le plan doit être stocké dans une matrice 1 × 3 avec une coordonnée 3e factice. La technique habituelle consiste à rendre toutes les coordonnées 3e égal à 1. Par exemple, le point (2, 1) est représenté par la matrice [2 1 1]. L’illustration suivante montre une transformation affine (rotation de 90 degrés, translation de 3 unités sur l’axe x et 4 unités dans la direction y) exprimée sous la forme multiplication par une seule matrice 3 × 3.  
  
 ![Transformations](./media/aboutgdip05-art09.gif "AboutGdip05_art09")  
  
 Dans l’exemple précédent, le point (2, 1) est mappé au point (2, 6). Notez que la troisième colonne de la matrice 3 x 3 contient les nombres 0, 0, 1. Cela sera toujours le cas pour la matrice 3 x 3 d’une transformation affine. Les nombres importants sont les six nombres des colonnes 1 et 2. La partie supérieure gauche 2 × 2 de la matrice représente la partie linéaire de la transformation, et les deux premières entrées de la 3e ligne représentent la translation.  
  
 ![Transformations](./media/aboutgdip05-art10.gif "AboutGdip05_art10")  
  
 Dans GDI +, vous pouvez stocker une transformation affine dans un <xref:System.Drawing.Drawing2D.Matrix> objet. Étant donné que la troisième colonne d’une matrice qui représente une transformation affine est toujours (0, 0, 1), vous spécifiez uniquement les six nombres dans les deux premières colonnes lorsque vous construisez un <xref:System.Drawing.Drawing2D.Matrix> objet. L’instruction `Matrix myMatrix = new Matrix(0, 1, -1, 0, 3, 4)` construit la matrice affichée dans la figure précédente.  
  
## <a name="composite-transformations"></a>Transformations composites  
 Une transformation composite est une séquence de transformations, une après l’autre. Prenez en compte les matrices et les transformations dans la liste suivante :  
  
|||  
|-|-|  
|Matrice A|Faire pivoter de 90 degrés|  
|Matrix B|Mettre à l’échelle par un facteur de 2 sur l’axe x|  
|Matrice C|Translation de 3 unités dans la direction y|  
  
 Si nous commençons avec le point (2, 1), représenté par la matrice [2 1 1] et le multiplier par A, puis B, puis C, le point (2, 1) subiront les trois transformations dans l’ordre indiqué.  
  
 [2 1 1]ABC = [-2 5 1]  
  
 Au lieu de cela les trois parties de la transformation composite dans trois matrices distinctes, vous pouvez multiplier A, B et C entre elles pour obtenir une matrice 3 x 3 unique qui stocke la transformation composite entière. Supposons que ABC = D. Puis un point multiplié par D donne le même résultat qu’un point multiplié par A, puis B, puis sur C.  
  
 [2 1 1]D = [-2 5 1]  
  
 L’illustration suivante montre les matrices A, B, C et D.  
  
 ![Transformations](./media/aboutgdip05-art12.gif "AboutGdip05_art12")  
  
 Le fait que la matrice d’une transformation composite peut être formée en multipliant les matrices de transformation individuelles signifie que n’importe quelle séquence de transformations affines peut être stockée dans un seul <xref:System.Drawing.Drawing2D.Matrix> objet.  
  
> [!CAUTION]
>  L’ordre d’une transformation composite est important. En règle générale, faire pivoter, mettre à l’échelle, puis traduire n’est pas le même en tant que mise à l’échelle, faire pivoter, puis traduire. De même, l’ordre de multiplication de matrice est important. En général, ABC n’est pas identique à BAC.  
  
 Le <xref:System.Drawing.Drawing2D.Matrix> classe fournit plusieurs méthodes pour créer une transformation composite : <xref:System.Drawing.Drawing2D.Matrix.Multiply%2A>, <xref:System.Drawing.Drawing2D.Matrix.Rotate%2A>, <xref:System.Drawing.Drawing2D.Matrix.RotateAt%2A>, <xref:System.Drawing.Drawing2D.Matrix.Scale%2A>, <xref:System.Drawing.Drawing2D.Matrix.Shear%2A>, et <xref:System.Drawing.Drawing2D.Matrix.Translate%2A>. L’exemple suivant crée la matrice d’une transformation composite qui pivote tout d’abord de 30 degrés, puis met à l’échelle par un facteur de 2 sur l’axe y et traduit alors 5 unités dans la direction x :  
  
 [!code-csharp[System.Drawing.CoordinateSystems#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.CoordinateSystems#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#11)]  
  
 L’illustration suivante montre la matrice.  
  
 ![Transformations](./media/aboutgdip05-art13.gif "AboutGdip05_art13")  
  
## <a name="see-also"></a>Voir aussi

- [Systèmes de coordonnées et transformations](coordinate-systems-and-transformations.md)
- [Utilisation des transformations dans GDI+ managé](using-transformations-in-managed-gdi.md)
