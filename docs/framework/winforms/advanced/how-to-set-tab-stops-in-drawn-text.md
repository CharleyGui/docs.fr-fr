---
title: 'Procédure : définir des taquets de tabulation dans du texte dessiné'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text [Windows Forms], drawing with tab stops
- tabs [Windows Forms], drawn text
ms.assetid: 64878f98-39ba-4303-b63f-0859ab682eeb
ms.openlocfilehash: 8821f6170b8ba588e3197ef54eab14c2719a6cc3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69947820"
---
# <a name="how-to-set-tab-stops-in-drawn-text"></a>Procédure : définir des taquets de tabulation dans du texte dessiné
Vous pouvez définir des taquets de tabulation pour le <xref:System.Drawing.StringFormat.SetTabStops%2A> texte en appelant <xref:System.Drawing.StringFormat> la méthode d’un objet <xref:System.Drawing.StringFormat> , puis en <xref:System.Drawing.Graphics.DrawString%2A> passant cet objet <xref:System.Drawing.Graphics> à la méthode de la classe.  
  
> [!NOTE]
> Ne <xref:System.Windows.Forms.TextRenderer?displayProperty=nameWithType> prend pas en charge l’ajout de taquets de tabulation au texte dessiné, bien que vous puissiez <xref:System.Windows.Forms.TextFormatFlags.ExpandTabs?displayProperty=nameWithType> développer des taquets de tabulation existants à l’aide de l’indicateur.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant définit des taquets de tabulation à 150, 250 et 350. Ensuite, le code affiche une liste avec onglets de noms et de scores de test.  
  
 L’illustration suivante montre le texte avec onglets:  
  
 ![Capture d’écran montrant une liste avec onglets de noms et de scores.](./media/how-to-set-tab-stops-in-drawn-text/tab-list-names-test-scores.png)  
  
 Le code suivant passe deux arguments à la <xref:System.Drawing.StringFormat.SetTabStops%2A> méthode. Le deuxième argument est un tableau qui contient des décalages de tabulation. Le premier argument passé à <xref:System.Drawing.StringFormat.SetTabStops%2A> est 0, ce qui indique que le premier décalage dans le tableau est mesuré à partir de la position 0, le bord gauche du rectangle englobant.  
  
 [!code-csharp[System.Drawing.FontsAndText#41](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.FontsAndText#41](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#41)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
  
- L’exemple précédent est conçu pour une utilisation avec Windows Forms et nécessite <xref:System.Windows.Forms.PaintEventArgs> `e`, qui est un paramètre de <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Voir aussi

- [Utilisation de polices et de texte](using-fonts-and-text.md)
- [Guide pratique : Dessiner du texte avec GDI](how-to-draw-text-with-gdi.md)
