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
ms.openlocfilehash: 24da407de24a924a68466e4301cc3f4a74cb2e94
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044251"
---
# <a name="matrix-representation-of-transformations"></a>Représentation matricielle des transformations
Une matrice m × n est un ensemble de nombres organisés en m lignes et n colonnes. L’illustration suivante montre plusieurs matrices.  
  
 ![Transformations](./media/aboutgdip05-art04.gif "AboutGdip05_art04")  
  
 Vous pouvez ajouter deux matrices de même taille en ajoutant des éléments individuels. L’illustration suivante montre deux exemples d’ajouts de matrice.  
  
 ![Transformations](./media/aboutgdip05-art05.gif "AboutGdip05_art05")  
  
 Une matrice m × n peut être multipliée par une matrice n × p, et le résultat est une matrice m × p. Le nombre de colonnes dans la première matrice doit être le même que le nombre de lignes dans la seconde matrice. Par exemple, une matrice 4 × 2 peut être multipliée par une matrice 2 × 3 pour produire une matrice 4 × 3.  
  
 Les points dans le plan et les lignes et les colonnes d’une matrice peuvent être considérés comme des vecteurs. Par exemple, (2, 5) est un vecteur avec deux composants, et (3, 7, 1) est un vecteur avec trois composants. Le produit scalaire de deux vecteurs est défini comme suit:  
  
 (a, b) • (c, d) = AC + BD  
  
 (a, b, c) • (d, e, f) = AD + is + cf  
  
 Par exemple, le produit scalaire de (2, 3) et (5, 4) est (2) (5) + (3) (4) = 22. Le produit scalaire de (2, 5, 1) et (4, 3, 1) est (2) (4) + (5) (3) + (1) (1) = 24. Notez que le produit scalaire de deux vecteurs est un nombre, et non un autre vecteur. Notez également que vous pouvez calculer le produit scalaire uniquement si les deux vecteurs ont le même nombre de composants.  
  
 LET A (i, j) est l’entrée de la matrice A dans la énième ligne et la colonne JTH. Par exemple, un (3, 2) est l’entrée de la matrice A sur la troisième ligne et la 2e colonne. Supposons que A, B et C sont des matrices, et AB = C. Les entrées de C sont calculées comme suit:  
  
 C (i, j) = (ligne i de A) • (colonne j sur B)  
  
 L’illustration suivante montre plusieurs exemples de multiplication de matrice.  
  
 ![Transformations](./media/aboutgdip05-art06.gif "AboutGdip05_art06")  
  
 Si vous considérez un point dans un plan comme une matrice 1 × 2, vous pouvez transformer ce point en le multipliant par une matrice 2 × 2. L’illustration suivante montre plusieurs transformations appliquées au point (2, 1).  
  
 ![Transformations](./media/aboutgdip05-art07.gif "AboutGdip05_art07")  
  
 Toutes les transformations présentées dans l’illustration précédente sont des transformations linéaires. Certaines autres transformations, telles que la translation, ne sont pas linéaires et ne peuvent pas être exprimées sous la forme d’une multiplication par une matrice 2 × 2. Supposons que vous souhaitiez commencer par le point (2, 1), le faire pivoter de 90 degrés, le convertir en 3 unités dans la direction x et traduire les unités informatiques 4 dans la direction y. Pour ce faire, vous pouvez utiliser une multiplication de matrice, suivie d’un ajout de matrice.  
  
 ![Transformations](./media/aboutgdip05-art08.gif "AboutGdip05_art08")  
  
 Une transformation linéaire (multiplication par une matrice 2 × 2) suivie d’une translation (ajout d’une matrice 1 × 2) est appelée une transformation affine. Une alternative au stockage d’une transformation affine dans une paire de matrices (une pour la partie linéaire et l’autre pour la translation) consiste à stocker l’intégralité de la transformation dans une matrice 3 × 3. Pour effectuer cette opération, un point dans le plan doit être stocké dans une matrice 1 × 3 avec une troisième coordonnée factice. La technique habituelle consiste à faire en sorte que toutes les 3 coordonnées soient égales à 1. Par exemple, le point (2, 1) est représenté par la matrice [2 1 1]. L’illustration suivante montre une transformation affine (rotation de 90 degrés; translation de 3 unités dans la direction x, 4 unités sur l’axe y), exprimées sous la forme d’une multiplication par une matrice 3 × 3 unique.  
  
 ![Transformations](./media/aboutgdip05-art09.gif "AboutGdip05_art09")  
  
 Dans l’exemple précédent, le point (2, 1) est mappé au point (2, 6). Notez que la troisième colonne de la matrice 3 × 3 contient les nombres 0, 0, 1. Ce sera toujours le cas pour la matrice 3 × 3 d’une transformation affine. Les nombres importants sont les six nombres des colonnes 1 et 2. La partie supérieure gauche 2 × 2 de la matrice représente la partie linéaire de la transformation, tandis que les deux premières entrées de la troisième ligne représentent la translation.  
  
 ![Transformations](./media/aboutgdip05-art10.gif "AboutGdip05_art10")  
  
 Dans GDI+, vous pouvez stocker une transformation affine <xref:System.Drawing.Drawing2D.Matrix> dans un objet. Étant donné que la troisième colonne d’une matrice qui représente une transformation affine est toujours (0, 0, 1), vous spécifiez uniquement les six nombres dans les deux premières colonnes <xref:System.Drawing.Drawing2D.Matrix> quand vous construisez un objet. L’instruction `Matrix myMatrix = new Matrix(0, 1, -1, 0, 3, 4)` construit la matrice présentée dans l’illustration précédente.  
  
## <a name="composite-transformations"></a>Transformations composites  
 Une transformation composite est une séquence de transformations, l’une suivie de l’autre. Tenez compte des matrices et des transformations figurant dans la liste suivante:  
  
|||  
|-|-|  
|Matrice A|Faire pivoter de 90 degrés|  
|Matrice B|Mise à l’échelle d’un facteur de 2 dans la direction x|  
|Matrice C|Translater 3 unités sur l’axe y|  
  
 Si nous commençons par le point (2, 1) (représenté par la matrice [2 1 1]) et si vous multipliez par A, puis B, puis C, le point (2, 1) subira les trois transformations dans l’ordre indiqué.  
  
 [2 1 1] ABC = [-2 5 1]  
  
 Au lieu de stocker les trois parties de la transformation composite dans trois matrices distinctes, vous pouvez multiplier A, B et C ensemble pour obtenir une matrice 3 × 3 unique qui stocke l’intégralité de la transformation composite. Supposons que ABC = D. Un point multiplié par D donne le même résultat qu’un point multiplié par A, puis B, puis C.  
  
 [2 1 1] D = [-2 5 1]  
  
 L’illustration suivante montre les matrices A, B, C et D.  
  
 ![Transformations](./media/aboutgdip05-art12.gif "AboutGdip05_art12")  
  
 Le fait que la matrice d’une transformation composite puisse être formée en multipliant les matrices de transformation individuelles signifie que toute séquence de transformations affinées peut être stockée dans un objet unique <xref:System.Drawing.Drawing2D.Matrix> .  
  
> [!CAUTION]
> L’ordre d’une transformation composite est important. En général, faire pivoter, puis mettre à l’échelle, puis translater n’est pas identique à l’échelle, faire pivoter, puis traduire. De même, l’ordre de multiplication des matrices est important. En général, ABC n’est pas le même que le BAA.  
  
 La <xref:System.Drawing.Drawing2D.Matrix> classe fournit plusieurs méthodes pour générer une transformation composite <xref:System.Drawing.Drawing2D.Matrix.Multiply%2A>: <xref:System.Drawing.Drawing2D.Matrix.Rotate%2A>, <xref:System.Drawing.Drawing2D.Matrix.RotateAt%2A>, <xref:System.Drawing.Drawing2D.Matrix.Scale%2A> <xref:System.Drawing.Drawing2D.Matrix.Shear%2A>,, et <xref:System.Drawing.Drawing2D.Matrix.Translate%2A>. L’exemple suivant crée la matrice d’une transformation composite qui fait pivoter d’abord 30 degrés, puis met à l’échelle d’un facteur de 2 sur l’axe y, puis convertit 5 unités dans la direction x:  
  
 [!code-csharp[System.Drawing.CoordinateSystems#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.CoordinateSystems#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#11)]  
  
 L’illustration suivante montre la matrice.  
  
 ![Transformations](./media/aboutgdip05-art13.gif "AboutGdip05_art13")  
  
## <a name="see-also"></a>Voir aussi

- [Systèmes de coordonnées et transformations](coordinate-systems-and-transformations.md)
- [Utilisation des transformations dans GDI+ managé](using-transformations-in-managed-gdi.md)
