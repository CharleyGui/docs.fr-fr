---
title: 'Procédure : joindre des lignes'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- miter line join style
- bevel line join style
- line join
- drawing [Windows Forms], joining lines
- GraphicsPath object
- round line join style
- lines [Windows Forms], joining
- graphics [Windows Forms], joining lines
ms.assetid: 9fc480c2-3c75-4fd1-8ab5-296a99e820e2
ms.openlocfilehash: 362ce0c701d6e5f640fecd143a60cf471045629c
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67505869"
---
# <a name="how-to-join-lines"></a>Procédure : joindre des lignes
Une jointure de la ligne est la zone commune qui est formée par deux lignes dont les extrémités se rencontrent ou se chevauchent. GDI + fournit trois styles de jonction de ligne : angle aigu, en biseau et arrondie. Style de ligne de jointure est une propriété de la <xref:System.Drawing.Pen> classe. Lorsque vous spécifiez un style de jointure de ligne pour un <xref:System.Drawing.Pen> que jointure style sera appliqué à toutes les lignes connectées dans un objet <xref:System.Drawing.Drawing2D.GraphicsPath> objet dessiné à l’aide de ce stylet.  
  
 L’illustration suivante montre les résultats de l’exemple de jointure de ligne en relief.  
  
 ![Illustration des lignes jointes.](./media/how-to-join-lines/joined-beveled-lines.gif)  
  
## <a name="example"></a>Exemple  
 Vous pouvez spécifier le style de ligne de jointure à l’aide de la <xref:System.Drawing.Pen.LineJoin%2A> propriété de la <xref:System.Drawing.Pen> classe. L’exemple montre une jointure de lignes biseautée entre une ligne horizontale et une ligne verticale. Dans le code suivant, la valeur <xref:System.Drawing.Drawing2D.LineJoin.Bevel> affectée à la <xref:System.Drawing.Pen.LineJoin%2A> propriété est un membre de la <xref:System.Drawing.Drawing2D.LineJoin> énumération. Les autres membres de la <xref:System.Drawing.Drawing2D.LineJoin> énumération sont <xref:System.Drawing.Drawing2D.LineJoin.Miter> et <xref:System.Drawing.Drawing2D.LineJoin.Round>.  
  
 [!code-csharp[System.Drawing.UsingAPen#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.UsingAPen#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 L’exemple précédent est conçu pour une utilisation avec Windows Forms et nécessite <xref:System.Windows.Forms.PaintEventArgs> `e`, qui est un paramètre de la <xref:System.Windows.Forms.Control.Paint> Gestionnaire d’événements.  
  
## <a name="see-also"></a>Voir aussi

- [Utilisation d'un stylet pour dessiner des lignes et des formes](using-a-pen-to-draw-lines-and-shapes.md)
