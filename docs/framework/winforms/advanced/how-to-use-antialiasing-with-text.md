---
title: 'Procédure : utiliser l’anticrénelage avec du texte'
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
ms.openlocfilehash: 080d946bd72da8b76ed846efdf149eb328d66336
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67505729"
---
# <a name="how-to-use-antialiasing-with-text"></a>Procédure : utiliser l’anticrénelage avec du texte
*Anticrénelage* fait référence au lissage de bords dentelés des graphiques dessinés et du texte pour améliorer leur apparence ou la lisibilité. Avec les classes GDI + managés, vous pouvez afficher le texte non crénelé de haute qualité, ainsi que le texte de qualité inférieure. En règle générale, un rendu de qualité supérieur prend plus de temps de traitement que le rendu de qualité inférieure. Pour définir le niveau de qualité de texte, définissez la <xref:System.Drawing.Graphics.TextRenderingHint%2A> propriété d’un <xref:System.Drawing.Graphics> à un des éléments de la <xref:System.Drawing.Text.TextRenderingHint> énumération  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant dessine du texte avec deux paramètres de qualité différents.  
  
 [!code-csharp[System.Drawing.FontsAndText#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.FontsAndText#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#21)]  
 
 L’illustration suivante montre la sortie de l’exemple de code :  
  
 ![Capture d’écran qui affiche le texte avec deux paramètres de qualité différents.](./media/how-to-use-antialiasing-with-text/antialiasing-text-quality-settings.png)  
  
## <a name="compiling-the-code"></a>Compilation du code  
 L’exemple de code précédent est conçu pour une utilisation avec Windows Forms et nécessite <xref:System.Windows.Forms.PaintEventArgs> `e`, qui est un paramètre de <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Voir aussi

- [Utilisation de polices et de texte](using-fonts-and-text.md)
