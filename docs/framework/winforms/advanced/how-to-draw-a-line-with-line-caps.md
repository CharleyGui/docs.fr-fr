---
title: 'Procédure : dessiner une ligne avec des extrémités de fin'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- drawing [Windows Forms], lines
- lines [Windows Forms], drawing
- pens [Windows Forms], drawing lines
- drawing lines [Windows Forms], line caps
ms.assetid: eb68c3e1-c400-4886-8a04-76978a429cb6
ms.openlocfilehash: 34abfc86e980a24ebb835cfd88d2522f8372c68d
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67506025"
---
# <a name="how-to-draw-a-line-with-line-caps"></a>Procédure : dessiner une ligne avec des extrémités de fin
Vous pouvez dessiner le début ou la fin d’une ligne dans plusieurs formes appelé embouts de ligne. GDI + prend en charge plusieurs embouts de ligne, tels que round, carré, losange et pointe de flèche.  
  
## <a name="example"></a>Exemple  
 Vous pouvez spécifier des embouts de ligne pour le début d’une ligne (extrémité de début), la fin d’une ligne (extrémité de fin) ou les tirets d’une ligne en pointillés (cap dash).  
  
 L’exemple suivant dessine une ligne avec une pointe de flèche à une extrémité et une extrémité arrondie à l’autre extrémité. L’illustration montre la ligne résultante :  
  
 ![Illustration qui montre une ligne avec une extrémité arrondie.](./media/how-to-draw-a-line-with-line-caps/line-cap-arrowhead-example.gif)  
  
 [!code-csharp[System.Drawing.UsingAPen#71](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#71)]
 [!code-vb[System.Drawing.UsingAPen#71](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#71)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
  
- Créer un formulaire Windows et de gérer le formulaire <xref:System.Windows.Forms.Control.Paint> événement. Collez l’exemple de code dans le <xref:System.Windows.Forms.Control.Paint> Gestionnaire d’événements en passant `e` comme <xref:System.Windows.Forms.PaintEventArgs>.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Drawing.Pen?displayProperty=nameWithType>
- <xref:System.Drawing.Drawing2D.LineCap?displayProperty=nameWithType>
- [Graphiques et dessins dans Windows Forms](graphics-and-drawing-in-windows-forms.md)
- [Utilisation d'un stylet pour dessiner des lignes et des formes](using-a-pen-to-draw-lines-and-shapes.md)
