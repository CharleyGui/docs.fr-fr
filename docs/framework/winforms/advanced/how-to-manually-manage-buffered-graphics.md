---
title: 'Procédure : gérer manuellement les graphismes mis en mémoire tampon'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- flicker [Windows Forms], reducing by manually managing graphics
- graphics [Windows Forms], managing buffered
ms.assetid: 4c2a90ee-bbbe-4ff6-9170-1b06c195c918
ms.openlocfilehash: 6010d52750b20c07db51917621f8643e9d9b47d7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968603"
---
# <a name="how-to-manually-manage-buffered-graphics"></a>Procédure : gérer manuellement les graphismes mis en mémoire tampon
Pour les scénarios de double mise en mémoire tampon plus avancés, vous pouvez utiliser les classes .NET Framework pour implémenter votre propre logique de double mise en mémoire tampon. La classe responsable de l’allocation et de la gestion de mémoires tampons de graphiques individuelles est la <xref:System.Drawing.BufferedGraphicsContext> classe. Chaque application possède sa propre valeur <xref:System.Drawing.BufferedGraphicsContext> par défaut qui gère l’ensemble de la double mise en mémoire tampon par défaut pour cette application. Vous pouvez récupérer une référence à cette instance en appelant <xref:System.Drawing.BufferedGraphicsManager.Current%2A>.  
  
### <a name="to-obtain-a-reference-to-the-default-bufferedgraphicscontext"></a>Pour obtenir une référence au BufferedGraphicsContext par défaut  
  
- Définissez la <xref:System.Drawing.BufferedGraphicsManager.Current%2A> propriété, comme indiqué dans l’exemple de code suivant.  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#11)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#11)]  
  
    > [!NOTE]
    > Vous n’avez pas besoin d’appeler `Dispose` la méthode sur <xref:System.Drawing.BufferedGraphicsContext> la référence que vous recevez de <xref:System.Drawing.BufferedGraphicsManager> la classe. Le <xref:System.Drawing.BufferedGraphicsManager> gère l’ensemble de l’allocation et de la distribution <xref:System.Drawing.BufferedGraphicsContext> de la mémoire pour les instances par défaut.  
  
     Pour les applications gourmandes en graphique, telles que l’animation, vous pouvez parfois améliorer les <xref:System.Drawing.BufferedGraphicsContext> <xref:System.Drawing.BufferedGraphicsContext> performances à l’aide d’un <xref:System.Drawing.BufferedGraphicsManager>dédié au lieu du fourni par le. Cela vous permet de créer et de gérer des mémoires tampons de graphiques individuellement, sans entraîner la surcharge de performances de la gestion de tous les autres graphiques mis en mémoire tampon associés à votre application, bien que la mémoire consommée par l’application soit supérieure.  
  
### <a name="to-create-a-dedicated-bufferedgraphicscontext"></a>Pour créer un BufferedGraphicsContext dédié  
  
- Déclarez et créez une nouvelle instance de <xref:System.Drawing.BufferedGraphicsContext> la classe, comme indiqué dans l’exemple de code suivant.  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#12)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#12)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Drawing.BufferedGraphicsContext>
- [Graphiques mis deux fois en mémoire tampon](double-buffered-graphics.md)
- [Guide pratique : Rendu manuel des graphiques mis en mémoire tampon](how-to-manually-render-buffered-graphics.md)
