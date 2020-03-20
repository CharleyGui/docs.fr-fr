---
title: 'Comment : créer du texte vertical'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text [Windows Forms], drawing vertical
- Windows Forms, drawing vertical text
- strings [Windows Forms], drawing vertical
- vertical text [Windows Forms], drawing
ms.assetid: 50c69046-4188-47d9-b949-cc2610ffd337
ms.openlocfilehash: 86401342625f593945b801f7619ef9ca9681317c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182557"
---
# <a name="how-to-create-vertical-text"></a>Comment : créer du texte vertical
Vous pouvez <xref:System.Drawing.StringFormat> utiliser un objet pour spécifier que le texte soit dessiné verticalement plutôt qu’horizontalement.  
  
## <a name="example"></a> Exemple  
 L’exemple suivant attribue <xref:System.Drawing.StringFormatFlags.DirectionVertical> la <xref:System.Drawing.StringFormat.FormatFlags%2A> valeur <xref:System.Drawing.StringFormat> à la propriété d’un objet. Cet <xref:System.Drawing.StringFormat> objet est <xref:System.Drawing.Graphics.DrawString%2A> transmis à <xref:System.Drawing.Graphics> la méthode de la classe. La <xref:System.Drawing.StringFormatFlags.DirectionVertical> valeur est un <xref:System.Drawing.StringFormatFlags> membre de l’énumération.  
  
 L’illustration suivante montre le texte vertical :
  
 ![Graphique qui montre le texte vertical de police.](./media/how-to-create-vertical-text/vertical-font-text-graphic.png)  
  
 [!code-csharp[System.Drawing.FontsAndText#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.FontsAndText#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
  
- L’exemple précédent est conçu pour une <xref:System.Windows.Forms.PaintEventArgs> `e` utilisation avec windows <xref:System.Windows.Forms.PaintEventHandler>Forms, et il nécessite , qui est un paramètre de .  
  
## <a name="see-also"></a>Voir aussi

- [Comment : écrire du texte avec GDI](how-to-draw-text-with-gdi.md)
