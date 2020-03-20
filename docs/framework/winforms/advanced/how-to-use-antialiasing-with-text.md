---
title: 'Comment : utiliser l‘anticrénelage avec du texte'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- strings [Windows Forms], smoothing drawn
- antialiasing [Windows Forms], using with text
- text [Windows Forms], smoothing
- text [Windows Forms], antialiasing
- strings [Windows Forms], antialiasing when drawing
ms.assetid: 48fc34f3-f236-4b01-a0cb-f0752e6d22ae
ms.openlocfilehash: 632ed329173d134495a424b34ca7c71e402607bf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182485"
---
# <a name="how-to-use-antialiasing-with-text"></a>Comment : utiliser l‘anticrénelage avec du texte
*Antialiasing* fait référence au lissage des bords déchiquetés de graphiques et de textes dessinés pour améliorer leur apparence ou leur lisibilité. Avec les classes GDI GÉRÉEs, vous pouvez rendre du texte antialiased de haute qualité, ainsi que du texte de qualité inférieure. Typiquement, un rendu de meilleure qualité prend plus de temps de traitement que le rendu de qualité inférieure. Pour définir le niveau de <xref:System.Drawing.Graphics.TextRenderingHint%2A> qualité <xref:System.Drawing.Graphics> du texte, définissez <xref:System.Drawing.Text.TextRenderingHint> la propriété d’un élément de l’énumération  
  
## <a name="example"></a> Exemple  
 L’exemple de code suivant dessine du texte avec deux paramètres de qualité différents.  
  
 [!code-csharp[System.Drawing.FontsAndText#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.FontsAndText#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#21)]  

 L’illustration suivante montre la sortie du code d’exemple :  
  
 ![Capture d’écran qui montre le texte avec deux paramètres de qualité différents.](./media/how-to-use-antialiasing-with-text/antialiasing-text-quality-settings.png)  
  
## <a name="compiling-the-code"></a>Compilation du code  
 L’exemple de code précédent est conçu pour <xref:System.Windows.Forms.PaintEventArgs> `e`une utilisation avec <xref:System.Windows.Forms.PaintEventHandler>windows Forms, et il nécessite , qui est un paramètre de .  
  
## <a name="see-also"></a>Voir aussi

- [Utilisation de polices et de texte](using-fonts-and-text.md)
