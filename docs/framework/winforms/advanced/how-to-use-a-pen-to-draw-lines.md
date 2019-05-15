---
title: 'Procédure : utiliser un stylet pour dessiner des lignes'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- lines [Windows Forms], drawing
- pens [Windows Forms], drawing lines
ms.assetid: 0828c331-a438-4bdd-a4d6-3ef1e59e8795
ms.openlocfilehash: 263c0fbda377e64753cd2d607f633117b4b44253
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65593147"
---
# <a name="how-to-use-a-pen-to-draw-lines"></a>Procédure : utiliser un stylet pour dessiner des lignes
Pour dessiner des lignes, vous devez un <xref:System.Drawing.Graphics> objet et un <xref:System.Drawing.Pen> objet. Le <xref:System.Drawing.Graphics> objet fournit les <xref:System.Drawing.Graphics.DrawLine%2A> (méthode) et le <xref:System.Drawing.Pen> objet stocke les fonctionnalités de la ligne, telles que la couleur et la largeur.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant dessine une ligne à partir de (20, 10) à (300, 100). La première instruction utilise le <xref:System.Drawing.Pen.%23ctor%2A> constructeur de classe pour créer un stylet noir. L’argument passé à la <xref:System.Drawing.Pen.%23ctor%2A> constructeur est un <xref:System.Drawing.Color> objet créé avec le <xref:System.Drawing.Color.FromArgb%2A> (méthode). Les valeurs utilisées pour créer le <xref:System.Drawing.Color> objet — (255, 0, 0, 0), correspondent aux composants alphabétiques, rouges, vert et bleus de la couleur. Ces valeurs définissent un stylet noir opaque.  
  
 [!code-csharp[System.Drawing.UsingAPen#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.UsingAPen#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 L’exemple précédent est conçu pour une utilisation avec Windows Forms et nécessite <xref:System.Windows.Forms.PaintEventArgs> `e`, qui est un paramètre de la <xref:System.Windows.Forms.Control.Paint> Gestionnaire d’événements.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Drawing.Pen>
- [Utilisation d'un stylet pour dessiner des lignes et des formes](using-a-pen-to-draw-lines-and-shapes.md)
- [Stylets, lignes et rectangles dans GDI+](pens-lines-and-rectangles-in-gdi.md)
