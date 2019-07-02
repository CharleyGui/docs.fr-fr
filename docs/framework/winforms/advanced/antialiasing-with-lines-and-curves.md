---
title: Anticrénelage avec des lignes et des courbes
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- antialiasing
- antialiasing [Windows Forms], smoothing modes
- GDI+, antialiasing
ms.assetid: 810da1a4-c136-4abf-88df-68e49efdd8d4
ms.openlocfilehash: 871c5cb3cd9356f677633acb04fe82021a9787c5
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67506141"
---
# <a name="antialiasing-with-lines-and-curves"></a>Anticrénelage avec des lignes et des courbes
Lorsque vous utilisez GDI + pour dessiner une ligne, vous fournissez le point de départ et le point de fin de la ligne, mais vous n’êtes pas obligé de fournir toutes les informations concernant les pixels individuels sur la ligne. GDI + fonctionne conjointement avec le logiciel de pilote d’affichage pour déterminer quels pixels seront activées pour afficher la ligne sur un périphérique d’affichage particulier.  
  
## <a name="aliasing"></a>Utilisation d’alias  
 Envisagez la ligne droites rouge qui va du point (4, 2) au point (16, 10). Supposons que le système de coordonnées a son origine dans le coin supérieur gauche et que l’unité de mesure est le pixel. Supposons également que l’axe des x pointant vers la droite et les points de l’axe des y vers le bas. L’illustration suivante montre une vue agrandie de la ligne rouge dessinée sur un arrière-plan multicolore.  
  
 ![Ligne, sans anticrénelage](./media/aboutgdip02-art33.gif "AboutGdip02_Art33")  
  
 Les pixels rouges utilisés pour afficher la ligne sont opaques. Il n’y a aucun pixel partiellement transparent dans la ligne. Ce type de rendu donne une apparence en escalier à la ligne et la ligne ressemble quelque peu à un escalier. Cette technique qui représente une ligne comme un escalier est appelée crénelage ; l’escalier est un alias pour la ligne théorique.  
  
## <a name="antialiasing"></a>anticrénelage  
 Une technique plus sophistiquée pour le rendu d’une ligne implique l’utilisation de pixels partiellement transparents et opaques pixels. Pixels sont définies sur rouge pure, ou à une fusion de rouge et la couleur d’arrière-plan, en fonction de leur proximité sont à la ligne. Ce type de rendu est appelé anticrénelage et donne une ligne qui le œil humain perçoit plus lisse. L’illustration suivante montre comment certains pixels sont fusionnés avec l’arrière-plan pour produire une ligne non crénelé.  
  
 ![Anticrénelage d’une ligne](./media/aboutgdip02-art34.gif "AboutGdip02_Art34")  
  
 L’anticrénelage, également appelée lissage, peut également être appliqué aux courbes. L’illustration suivante montre une vue agrandie d’une ellipse lissée.  
  
 ![Anticrénelage de courbes](./media/aboutgdip02-art35.gif "AboutGdip02_Art35")  
  
 L’illustration suivante montre la même ellipse en taille réelle, sans anticrénelage et avec anticrénelage.  
  
 ![Exemple d’anticrénelage](./media/aboutgdip02-art36.gif "AboutGdip02_Art36")  
  
 Pour dessiner des lignes et des courbes qui utilisent l’anticrénelage, créez une instance de la <xref:System.Drawing.Graphics> classe et définissez son <xref:System.Drawing.Graphics.SmoothingMode%2A> propriété <xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias> ou <xref:System.Drawing.Drawing2D.SmoothingMode.HighQuality>. Appelez ensuite l’une des méthodes de dessins de ce même <xref:System.Drawing.Graphics> classe.  
  
 [!code-csharp[LinesCurvesAndShapes#81](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#81)]
 [!code-vb[LinesCurvesAndShapes#81](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#81)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Drawing.Drawing2D.SmoothingMode?displayProperty=nameWithType>
- [Lignes, courbes et formes](lines-curves-and-shapes.md)
- [Guide pratique pour Utiliser l’anticrénelage avec du texte](how-to-use-antialiasing-with-text.md)
