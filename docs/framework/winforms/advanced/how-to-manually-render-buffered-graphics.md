---
title: 'Procédure : afficher manuellement les graphismes mis en mémoire tampon'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- flicker [Windows Forms], reducing by manually rendering graphics
- graphics [Windows Forms], rendering
ms.assetid: 5192295e-bd8e-45f7-8bd6-5c4f6bd21e61
ms.openlocfilehash: a6655652a7c5dedb8e183356688972c07a705cbc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931839"
---
# <a name="how-to-manually-render-buffered-graphics"></a>Procédure : afficher manuellement les graphismes mis en mémoire tampon
Si vous gérez vos propres graphismes mis en mémoire tampon, vous devez pouvoir créer et restituer des mémoires tampon de graphiques. Vous pouvez créer des instances de la classe <xref:System.Drawing.BufferedGraphics> associée aux surfaces de dessin sur votre écran en appelant la méthode <xref:System.Drawing.BufferedGraphicsContext.Allocate%2A>. Cette méthode crée une instance de <xref:System.Drawing.BufferedGraphics> associée à une surface de rendu particulière, comme un formulaire ou un contrôle. Après avoir créé une instance de <xref:System.Drawing.BufferedGraphics>, vous pouvez dessiner des graphismes dans la mémoire tampon qu'elle représente par le biais de la propriété <xref:System.Drawing.BufferedGraphics.Graphics%2A>. Après avoir effectué toutes les opérations graphiques, vous pouvez copier le contenu de la mémoire tampon à l'écran en appelant la méthode <xref:System.Drawing.BufferedGraphics.Render%2A>.  
  
> [!NOTE]
> Si vous effectuez votre propre rendu, la consommation de mémoire augmentera, bien que cette augmentation puisse être très légère.  
  
### <a name="to-manually-display-buffered-graphics"></a>Pour afficher manuellement des graphismes mis en mémoire tampon  
  
1. Obtenez une référence à une instance de la classe <xref:System.Drawing.BufferedGraphicsContext>. Pour plus d’informations, consultez [Guide pratique pour Gérer manuellement les graphiques](how-to-manually-manage-buffered-graphics.md)mis en mémoire tampon.  
  
2. Créez une instance de la classe <xref:System.Drawing.BufferedGraphics> en appelant la méthode <xref:System.Drawing.BufferedGraphicsContext.Allocate%2A>, comme indiqué dans l'exemple de code suivant.  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#21)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#21)]  
  
3. Dessinez des graphismes dans la mémoire tampon de graphiques en définissant la propriété <xref:System.Drawing.BufferedGraphics.Graphics%2A>. Par exemple :  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#22](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#22)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#22](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#22)]  
  
4. Quand vous avez terminé toutes vos opérations de dessin dans la mémoire tampon de graphiques, appelez la méthode <xref:System.Drawing.BufferedGraphics.Render%2A> pour restituer la mémoire tampon, soit sur la surface de dessin associée à cette mémoire tampon, soit sur une surface de dessin spécifiée, comme illustré dans l'exemple de code suivant.  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#23](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#23)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#23](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#23)]  
  
5. Quand vous avez terminé d'afficher les graphismes, appelez la méthode `Dispose` sur l'instance de <xref:System.Drawing.BufferedGraphics> pour libérer les ressources système.  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#24](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#24)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#24](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#24)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Drawing.BufferedGraphicsContext>
- <xref:System.Drawing.BufferedGraphics>
- [Graphiques mis deux fois en mémoire tampon](double-buffered-graphics.md)
- [Guide pratique : Gérer manuellement les graphiques mis en mémoire tampon](how-to-manually-manage-buffered-graphics.md)
