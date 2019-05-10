---
title: 'Procédure : remplir une forme avec un motif hachuré'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- patterns [Windows Forms], adding to shapes
- shapes [Windows Forms], filling with patterns
- brushes [Windows Forms], using hatch brushes
ms.assetid: 9c8300ff-187b-404f-af1f-ebd499f5b16f
ms.openlocfilehash: b9ecefb82aaaf896c4ed39733f1e8d7bd65c16d4
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64645461"
---
# <a name="how-to-fill-a-shape-with-a-hatch-pattern"></a>Procédure : remplir une forme avec un motif hachuré
Un motif hachuré est effectué à partir de deux couleurs : un pour l’arrière-plan et un pour les lignes qui forment le modèle sur l’arrière-plan. Pour remplir une forme fermée avec un motif hachuré, utilisez un <xref:System.Drawing.Drawing2D.HatchBrush> objet. L’exemple suivant montre comment remplir une ellipse avec un motif hachuré :  
  
## <a name="example"></a>Exemple  
 Le <xref:System.Drawing.Drawing2D.HatchBrush.%23ctor%2A> constructeur accepte trois arguments : le style de hachurage, la couleur de la ligne de hachurage et la couleur d’arrière-plan. L’argument de style de hachurage peut être n’importe quelle valeur à partir de la <xref:System.Drawing.Drawing2D.HatchStyle> énumération. Il y a plus de 50 éléments dans le <xref:System.Drawing.Drawing2D.HatchStyle> énumération ; quelques-uns de ces éléments sont affichés dans la liste suivante :  
  
- <xref:System.Drawing.Drawing2D.HatchStyle.Horizontal>  
  
- <xref:System.Drawing.Drawing2D.HatchStyle.Vertical>  
  
- <xref:System.Drawing.Drawing2D.HatchStyle.ForwardDiagonal>  
  
- <xref:System.Drawing.Drawing2D.HatchStyle.BackwardDiagonal>  
  
- <xref:System.Drawing.Drawing2D.HatchStyle.Cross>  
  
- <xref:System.Drawing.Drawing2D.HatchStyle.DiagonalCross>  
  
 L’illustration suivante montre l’ellipse remplie.  
  
 ![Le modèle de hachurage](./media/hatch1.png "hatch1")  
  
 [!code-csharp[System.Drawing.UsingABrush#41](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.UsingABrush#41](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#41)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 L'exemple précédent est conçu pour une utilisation avec Windows Forms et nécessite <xref:System.Windows.Forms.PaintEventArgs>`e`, qui est un paramètre du gestionnaire d'événements <xref:System.Windows.Forms.Control.Paint>.  
  
## <a name="see-also"></a>Voir aussi

- [Utilisation d'un pinceau pour remplir des formes](using-a-brush-to-fill-shapes.md)
