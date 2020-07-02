---
title: 'Comment : dessiner une ligne dans un Windows Form'
description: Découvrez comment dessiner une ligne dans un formulaire en gérant l’événement Paint, puis effectuer le dessin à l’aide de la propriété Graphics de la fonction PaintEventArgs.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
f1_keywords:
- Graphics.DrawLine
helpviewer_keywords:
- examples [Windows Forms], drawing lines on forms
- drawing [Windows Forms], lines
- lines [Windows Forms], drawing
- drawing lines
ms.assetid: 55c1dbeb-75d0-430c-9814-a24b8971ad8c
ms.openlocfilehash: c8e92dc265c63413275561d0e2e3aa820eaec724
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621624"
---
# <a name="how-to-draw-a-line-on-a-windows-form"></a>Comment : dessiner une ligne dans un Windows Form
Cet exemple dessine une ligne dans un formulaire. En général, lorsque vous dessinez sur un formulaire, vous gérez l' <xref:System.Windows.Forms.Control.Paint> événement du formulaire et effectuez le dessin à l’aide <xref:System.Windows.Forms.PaintEventArgs.Graphics%2A> de la propriété de <xref:System.Windows.Forms.PaintEventArgs> , comme illustré dans cet exemple.  
  
## <a name="example"></a>Exemple  
 [!code-csharp[System.Drawing.UsingAPen#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.UsingAPen#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 L'exemple précédent est conçu pour une utilisation avec Windows Forms et nécessite <xref:System.Windows.Forms.PaintEventArgs>`e`, qui est un paramètre du gestionnaire d'événements <xref:System.Windows.Forms.Control.Paint>.  
  
## <a name="robust-programming"></a>Programmation fiable  
 Vous devez toujours appeler <xref:System.IDisposable.Dispose%2A> sur tous les objets qui consomment des ressources système, tels que les <xref:System.Drawing.Pen> objets.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Drawing.Graphics.DrawLine%2A>
- <xref:System.Windows.Forms.Control.OnPaint%2A>
- [Mise en route de la programmation graphique](getting-started-with-graphics-programming.md)
- [Utilisation d’un stylo pour tracer des lignes et des formes](using-a-pen-to-draw-lines-and-shapes.md)
- [Graphiques et dessins dans les Windows Forms](graphics-and-drawing-in-windows-forms.md)
