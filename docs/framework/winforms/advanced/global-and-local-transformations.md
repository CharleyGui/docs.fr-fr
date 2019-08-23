---
title: Transformations globales et locales
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- matrices [Windows Forms], using transformations
- transformations [Windows Forms], global
- transformations [Windows Forms], local
ms.assetid: b601d66d-d572-4f11-9d2e-92f0dc8893f3
ms.openlocfilehash: f62efb31e95b0797272997fadbc28459579a0de0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69955192"
---
# <a name="global-and-local-transformations"></a>Transformations globales et locales
Une transformation globale est une transformation qui s’applique à chaque élément dessiné par un <xref:System.Drawing.Graphics> objet donné. En revanche, une transformation locale est une transformation qui s’applique à un élément spécifique à dessiner.  
  
## <a name="global-transformations"></a>Transformations globales  
 Pour créer une transformation globale, construisez <xref:System.Drawing.Graphics> un objet, puis manipulez <xref:System.Drawing.Graphics.Transform%2A> sa propriété. La <xref:System.Drawing.Graphics.Transform%2A> propriété étant un <xref:System.Drawing.Drawing2D.Matrix> objet, elle peut contenir n’importe quelle séquence de transformations affines. La transformation stockée dans <xref:System.Drawing.Graphics.Transform%2A> la propriété est appelée transformation universelle. La <xref:System.Drawing.Graphics> classe fournit plusieurs méthodes pour créer une transformation universelle composite: <xref:System.Drawing.Graphics.MultiplyTransform%2A>, <xref:System.Drawing.Graphics.RotateTransform%2A>, <xref:System.Drawing.Graphics.ScaleTransform%2A>et <xref:System.Drawing.Graphics.TranslateTransform%2A>. L’exemple suivant dessine une ellipse deux fois: une fois avant de créer une transformation universelle et une fois après. La transformation se met d’abord à l’échelle d’un facteur de 0,5 sur l’axe y, puis convertit 50 unités dans la direction x, puis pivote de 30 degrés.  
  
 [!code-csharp[System.Drawing.CoordinateSystems#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.CoordinateSystems#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#21)]  
  
 L’illustration suivante montre les matrices impliquées dans la transformation.  
  
 ![Transformations](./media/aboutgdip05-art14.gif "AboutGdip05_art14")  
  
> [!NOTE]
> Dans l’exemple précédent, l’ellipse est pivotée sur l’origine du système de coordonnées, qui se trouve dans le coin supérieur gauche de la zone cliente. Cela produit un résultat différent de la rotation de l’ellipse autour de son propre centre.  
  
## <a name="local-transformations"></a>Transformations locales  
 Une transformation locale s’applique à un élément spécifique à dessiner. Par exemple, un <xref:System.Drawing.Drawing2D.GraphicsPath> objet a une <xref:System.Drawing.Drawing2D.GraphicsPath.Transform%2A> méthode qui vous permet de transformer les points de données de ce chemin d’accès. L’exemple suivant dessine un rectangle sans transformation et un tracé avec une transformation de rotation. (Supposez qu’il n’y a pas de transformation universelle.)  
  
 [!code-csharp[System.Drawing.CoordinateSystems#22](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#22)]
 [!code-vb[System.Drawing.CoordinateSystems#22](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#22)]  
  
 Vous pouvez combiner la transformation universelle avec les transformations locales pour obtenir un grand nombre de résultats. Par exemple, vous pouvez utiliser la transformation universelle pour réviser le système de coordonnées et utiliser des transformations locales pour faire pivoter et mettre à l’échelle des objets dessinés sur le nouveau système de coordonnées.  
  
 Supposons que vous souhaitiez un système de coordonnées qui a son origine 200 pixels du bord gauche de la zone client et 150 pixels en haut de la zone cliente. En outre, supposons que vous souhaitiez que l’unité de mesure soit le pixel, l’axe des x pointant vers la droite et l’axe des y pointant vers le haut. Le système de coordonnées par défaut a l’axe des y pointant vers le dessous. vous devez donc effectuer une réflexion sur l’axe horizontal. L’illustration suivante montre la matrice d’une telle réflexion.  
  
 ![Transformations](./media/aboutgdip05-art15.gif "AboutGdip05_art15")  
  
 Supposons ensuite que vous deviez effectuer une translation de 200 unités à droite et de 150 unités.  
  
 L’exemple suivant établit le système de coordonnées qui vient d’être décrit en définissant <xref:System.Drawing.Graphics> la transformation universelle d’un objet.  
  
 [!code-csharp[System.Drawing.CoordinateSystems#23](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#23)]
 [!code-vb[System.Drawing.CoordinateSystems#23](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#23)]  
  
 Le code suivant (placé à la fin de l’exemple précédent) crée un tracé qui se compose d’un seul rectangle avec son angle inférieur gauche à l’origine du nouveau système de coordonnées. Le rectangle est rempli une seule fois sans transformation locale et une fois avec une transformation locale. La transformation locale se compose d’une mise à l’échelle horizontale d’un facteur de 2, suivi d’une rotation de 30 degrés.  
  
 [!code-csharp[System.Drawing.CoordinateSystems#24](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#24)]
 [!code-vb[System.Drawing.CoordinateSystems#24](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#24)]  
  
 L’illustration suivante montre le nouveau système de coordonnées et les deux rectangles.  
  
 ![Transformations](./media/aboutgdip05-art16.gif "AboutGdip05_art16")  
  
## <a name="see-also"></a>Voir aussi

- [Systèmes de coordonnées et transformations](coordinate-systems-and-transformations.md)
- [Utilisation des transformations dans GDI+ managé](using-transformations-in-managed-gdi.md)
