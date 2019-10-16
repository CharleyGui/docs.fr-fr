---
title: 'Comment : remplir une forme avec un motif hachuré'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- patterns [Windows Forms], adding to shapes
- shapes [Windows Forms], filling with patterns
- brushes [Windows Forms], using hatch brushes
ms.assetid: 9c8300ff-187b-404f-af1f-ebd499f5b16f
ms.openlocfilehash: b80708f0ce722b1809fe49190639231e7e4c8329
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320055"
---
# <a name="how-to-fill-a-shape-with-a-hatch-pattern"></a>Comment : remplir une forme avec un motif hachuré
Un motif hachuré est constitué de deux couleurs : une pour l’arrière-plan et une pour les lignes qui forment le modèle sur l’arrière-plan. Pour remplir une forme fermée avec un motif hachuré, utilisez un objet <xref:System.Drawing.Drawing2D.HatchBrush>. L’exemple suivant montre comment remplir une ellipse avec un modèle de hachurage :  
  
## <a name="example"></a>Exemple  
 Le constructeur <xref:System.Drawing.Drawing2D.HatchBrush.%23ctor%2A> accepte trois arguments : le style de hachurage, la couleur de la ligne hachurée et la couleur de l’arrière-plan. L’argument de style de hachurage peut être n’importe quelle valeur de l’énumération <xref:System.Drawing.Drawing2D.HatchStyle>. Il y a plus de 50 éléments dans l’énumération <xref:System.Drawing.Drawing2D.HatchStyle> ; quelques-uns de ces éléments sont affichés dans la liste suivante :  
  
- <xref:System.Drawing.Drawing2D.HatchStyle.Horizontal>  
  
- <xref:System.Drawing.Drawing2D.HatchStyle.Vertical>  
  
- <xref:System.Drawing.Drawing2D.HatchStyle.ForwardDiagonal>  
  
- <xref:System.Drawing.Drawing2D.HatchStyle.BackwardDiagonal>  
  
- <xref:System.Drawing.Drawing2D.HatchStyle.Cross>  
  
- <xref:System.Drawing.Drawing2D.HatchStyle.DiagonalCross>  
  
 L’illustration suivante montre l’Ellipse remplie.  
  
  ![Capture d’écran de l’apparence d’une Ellipse remplie avec un hachurage.](./media/how-to-fill-a-shape-with-a-hatch-pattern/ellipse-filled-hatch.png "hatch1")
  
 [!code-csharp[System.Drawing.UsingABrush#41](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.UsingABrush#41](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#41)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 L'exemple précédent est conçu pour une utilisation avec Windows Forms et nécessite <xref:System.Windows.Forms.PaintEventArgs>`e`, qui est un paramètre du gestionnaire d'événements <xref:System.Windows.Forms.Control.Paint>.  
  
## <a name="see-also"></a>Voir aussi

- [Utilisation d'un pinceau pour remplir des formes](using-a-brush-to-fill-shapes.md)
