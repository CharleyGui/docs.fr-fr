---
title: 'Comment : dessiner avec des pinceaux opaques et translucides'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- semi-transparent shapes [Windows Forms], drawing
- transparency [Windows Forms], semi-transparent shapes
- alpha blending [Windows Forms], brush
- brushes [Windows Forms], using semi-transparent
ms.assetid: a4f6f6b8-3bc8-440a-84af-d62ef0f8ff40
ms.openlocfilehash: 1e48bbd563f6377380848949325962b568fa432c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142405"
---
# <a name="how-to-draw-with-opaque-and-semitransparent-brushes"></a>Comment : dessiner avec des pinceaux opaques et translucides
Quand vous remplissez une forme, vous devez passer un objet <xref:System.Drawing.Brush> à l'une des méthodes de remplissage de la classe <xref:System.Drawing.Graphics>. L'unique paramètre du constructeur <xref:System.Drawing.SolidBrush.%23ctor%2A> est un objet <xref:System.Drawing.Color>. Pour remplir une forme opaque, affectez au composant alpha de la couleur la valeur 255. Pour remplir une forme translucide, affectez au composant alpha n'importe quelle valeur comprise entre 1 et 254.  
  
 Quand vous remplissez une forme translucide, la couleur de la forme est fusionnée avec les couleurs d'arrière-plan. Le composant alpha spécifie comment les couleurs de forme et d'arrière-plan sont mélangées ; les valeurs alpha proches de 0 favorisent les couleurs d'arrière-plan, tandis que les valeurs alpha proches de 255 favorisent la couleur de forme.  
  
## <a name="example"></a> Exemple  
 L'exemple suivant dessine une bitmap, puis remplit trois ellipses qui chevauchent la bitmap. La première ellipse utilise un composant alpha de 255. Elle est donc opaque. Les deuxième et troisième ellipses utilisent un composant alpha de 128 et sont donc translucides. Vous pouvez voir l'image d'arrière-plan à travers les ellipses. L'appel qui définit la propriété <xref:System.Drawing.Graphics.CompositingQuality%2A> fait en sorte que la fusion pour la troisième ellipse s'effectue parallèlement à une correction gamma.  

 [!code-csharp[System.Drawing.AlphaBlending#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.AlphaBlending#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#31)]  

 L’illustration suivante montre la sortie du code suivant :
  
 ![Illustration qui montre la sortie opaque et semi-transparente.](./media/how-to-draw-with-opaque-and-semitransparent-brushes/compositingquality-ellipse-semitransparent.png)  
  
## <a name="compiling-the-code"></a>Compilation du code  
 L’exemple précédent est conçu pour une <xref:System.Windows.Forms.PaintEventArgs> `e`utilisation avec windows <xref:System.Windows.Forms.PaintEventHandler>Forms, et il nécessite , qui est un paramètre de .  
  
## <a name="see-also"></a>Voir aussi

- [Graphiques et dessins dans les Windows Forms](graphics-and-drawing-in-windows-forms.md)
- [Fusion alpha de lignes et de remplissages](alpha-blending-lines-and-fills.md)
- [Comment : affecter un arrière-plan transparent à votre contrôle](../controls/how-to-give-your-control-a-transparent-background.md)
- [Comment : dessiner des lignes opaques et translucides](how-to-draw-opaque-and-semitransparent-lines.md)
