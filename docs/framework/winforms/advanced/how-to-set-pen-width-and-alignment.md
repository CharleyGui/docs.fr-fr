---
title: 'Procédure : définir la largeur et l’alignement du stylet'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- pens [Windows Forms], setting width
- pens [Windows Forms], setting alignment
ms.assetid: a202af36-4d31-4401-a126-b232f51db581
ms.openlocfilehash: 1f1ea6e8ef0b94aa46a4bf8177d59e59297d6e3f
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64605833"
---
# <a name="how-to-set-pen-width-and-alignment"></a>Procédure : définir la largeur et l’alignement du stylet
Lorsque vous créez un <xref:System.Drawing.Pen>, vous pouvez fournir la largeur du stylet comme l’un des arguments au constructeur. Vous pouvez également modifier la largeur du stylet avec le <xref:System.Drawing.Pen.Width%2A> propriété de la <xref:System.Drawing.Pen> classe.  
  
 Une ligne théorique a une largeur égale à 0. Lorsque vous dessinez une ligne qui est la largeur de 1 pixel, les pixels sont centrés sur la ligne théorique. Si vous dessinez une ligne qui est supérieure à un pixel de large, les pixels sont centrés sur la ligne théorique ou apparaissent à côté de la ligne théorique. Vous pouvez définir la propriété d’alignement d’un <xref:System.Drawing.Pen> pour déterminer comment les pixels dessinés avec ce stylet seront positionnés par rapport aux lignes théoriques.  
  
 Les valeurs <xref:System.Drawing.Drawing2D.PenAlignment.Center>, <xref:System.Drawing.Drawing2D.PenAlignment.Outset>, et <xref:System.Drawing.Drawing2D.PenAlignment.Inset> qui apparaissent dans l’exemple suivant les exemples de code sont des membres de la <xref:System.Drawing.Drawing2D.PenAlignment> énumération.  
  
 L’exemple de code suivant dessine une ligne deux fois : une fois avec un stylet noir d’une largeur de 1 et une fois avec un stylet vert d’une largeur de 10.  
  
### <a name="to-vary-the-width-of-a-pen"></a>Pour faire varier la largeur d’un stylet  
  
- Définissez la valeur de la <xref:System.Drawing.Pen.Alignment%2A> propriété <xref:System.Drawing.Drawing2D.PenAlignment.Center> (la valeur par défaut) pour spécifier que les pixels dessinés avec le stylet vert seront centrés sur la ligne théorique. L’illustration suivante montre la ligne résultante.  
  
     ![Une fine ligne noire avec mise en surbrillance verte.](./media/how-to-set-pen-width-and-alignment/green-pixels-centered-line.gif)  
  
     L’exemple de code suivant dessine un rectangle à deux reprises : une fois avec un stylet noir d’une largeur de 1 et une fois avec un stylet vert d’une largeur de 10.  
  
     [!code-csharp[System.Drawing.UsingAPen#41](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#41)]
     [!code-vb[System.Drawing.UsingAPen#41](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#41)]  
  
### <a name="to-change-the-alignment-of-a-pen"></a>Pour modifier l’alignement d’un stylet  
  
- Définissez la valeur de la <xref:System.Drawing.Pen.Alignment%2A> propriété <xref:System.Drawing.Drawing2D.PenAlignment.Center> pour spécifier que les pixels dessinés avec le stylet vert seront centrés sur la limite du rectangle.  
  
     L’illustration suivante montre le rectangle résultant :
  
     ![Un rectangle est dessiné avec des lignes fines noir avec mise en surbrillance verte.](./media/how-to-set-pen-width-and-alignment/green-pixels-centered-rectangle.gif)  
  
     [!code-csharp[System.Drawing.UsingAPen#42](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#42)]
     [!code-vb[System.Drawing.UsingAPen#42](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#42)]  
  
### <a name="to-create-an-inset-pen"></a>Pour créer un stylet d’incrustation  
  
- Modifier l’alignement du stylet vert en modifiant la troisième instruction dans l’exemple de code précédent comme suit :  
  
     [!code-csharp[System.Drawing.UsingAPen#43](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#43)]
     [!code-vb[System.Drawing.UsingAPen#43](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#43)]  
  
     Les pixels dans la ligne verte large apparaissent maintenant à l’intérieur du rectangle comme indiqué dans l’illustration suivante :
  
     ![Un rectangle est dessiné avec des lignes noires avec la ligne verte large à l’intérieur.](./media/how-to-set-pen-width-and-alignment/green-pixels-inside-rectangle.gif)  
  
## <a name="see-also"></a>Voir aussi

- [Utilisation d'un stylet pour dessiner des lignes et des formes](using-a-pen-to-draw-lines-and-shapes.md)
- [Graphiques et dessins dans Windows Forms](graphics-and-drawing-in-windows-forms.md)
