---
title: 'Comment : dessiner un rectangle rempli dans un Windows Form'
description: Apprenez à dessiner par programmation un rectangle plein dans un Windows Form. En savoir plus sur la compilation de votre code.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- Graphics.FillRectangle
helpviewer_keywords:
- drawing [Windows Forms], rectangles
- rectangles [Windows Forms], drawing
- drawing rectangles
ms.assetid: d656a93c-987d-4809-aafd-493fe17450f0
ms.openlocfilehash: 0ad8ec97000e29b2194a9eda713aa43d5557b44c
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621637"
---
# <a name="how-to-draw-a-filled-rectangle-on-a-windows-form"></a>Comment : dessiner un rectangle rempli dans un Windows Form
Cet exemple dessine un rectangle plein dans un formulaire.  
  
## <a name="example"></a>Exemple  
 [!code-cpp[System.Drawing.ConceptualHowTos#2](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#2)]
 [!code-csharp[System.Drawing.ConceptualHowTos#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#2)]
 [!code-vb[System.Drawing.ConceptualHowTos#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#2)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Vous ne pouvez pas appeler cette méthode dans le <xref:System.Windows.Forms.Form.Load> Gestionnaire d’événements. Le contenu dessiné ne sera pas redessiné si le formulaire est redimensionné ou masqué par un autre formulaire. Pour que votre contenu se redessine automatiquement, vous devez remplacer la <xref:System.Windows.Forms.Control.OnPaint%2A> méthode.  
  
## <a name="robust-programming"></a>Programmation fiable  
 Vous devez toujours appeler <xref:System.IDisposable.Dispose%2A> sur tous les objets qui consomment des ressources système, tels que les <xref:System.Drawing.Brush> <xref:System.Drawing.Graphics> objets et.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Drawing.Graphics.FillRectangle%2A>
- <xref:System.Windows.Forms.Control.OnPaint%2A>
- [Mise en route de la programmation graphique](getting-started-with-graphics-programming.md)
- [Graphiques et dessins dans les Windows Forms](graphics-and-drawing-in-windows-forms.md)
- [Utilisation d’un stylo pour tracer des lignes et des formes](using-a-pen-to-draw-lines-and-shapes.md)
- [Pinceaux et remplissage de formes dans GDI+](brushes-and-filled-shapes-in-gdi.md)
