---
title: "Comment : réduire le scintillement des graphiques à l'aide du mécanisme de double tampon pour les formulaires et les contrôles"
description: Découvrez comment réduire le scintillement des graphiques avec la double mise en mémoire tampon pour Windows Forms et utiliser les contrôles pour résoudre les problèmes de scintillement associés aux opérations de peinture.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- flicker [Windows Forms], reducing in Windows Forms
- graphics [Windows Forms], reducing double-buffered flicker
ms.assetid: 91083d3a-653f-4f15-a467-0f37b2aa39d6
ms.openlocfilehash: f7c0425729f8a1a780124621788a1c49e06e0c4e
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85618127"
---
# <a name="how-to-reduce-graphics-flicker-with-double-buffering-for-forms-and-controls"></a>Comment : réduire le scintillement des graphiques à l'aide du mécanisme de double tampon pour les formulaires et les contrôles
La double mise en mémoire tampon utilise une mémoire tampon pour résoudre les problèmes de scintillement associés aux opérations de dessin multiples. Quand la double mise en mémoire tampon est activée, toutes les opérations de dessin sont d’abord rendues dans une mémoire tampon au lieu de l’être sur la surface de dessin à l’écran. Une fois que toutes les opérations de dessin sont terminées, la mémoire tampon est copiée directement sur la surface de dessin qui y est associée. Étant donné qu’une seule opération Graphics est exécutée sur l’écran, le scintillement d’image associé aux opérations de dessin complexes est éliminé. Pour la plupart des applications, la double mise en mémoire tampon par défaut fournie par l' .NET Framework fournira les meilleurs résultats. Les contrôles de Windows Forms standard sont doubles mis en mémoire tampon par défaut. Vous pouvez activer la double mise en mémoire tampon par défaut dans vos formulaires et contrôles créés de deux manières. Vous pouvez affecter la valeur à la <xref:System.Windows.Forms.Control.DoubleBuffered%2A> propriété `true` ou appeler la <xref:System.Windows.Forms.Control.SetStyle%2A> méthode pour affecter la valeur à l' <xref:System.Windows.Forms.ControlStyles.OptimizedDoubleBuffer> indicateur `true` . Les deux méthodes activent la double mise en mémoire tampon par défaut pour votre formulaire ou contrôle et fournissent un rendu graphique sans scintillement. L’appel de la <xref:System.Windows.Forms.Control.SetStyle%2A> méthode est recommandé uniquement pour les contrôles personnalisés pour lesquels vous avez écrit l’ensemble du code de rendu.  
  
 Pour les scénarios de double mise en mémoire tampon plus avancés, tels que l’animation ou la gestion de mémoire avancée, vous pouvez implémenter votre propre logique de mise en mémoire tampon double. Pour plus d’informations, consultez [Comment : gérer manuellement des graphiques mis en mémoire tampon](how-to-manually-manage-buffered-graphics.md).  
  
### <a name="to-reduce-flicker"></a>Pour réduire le scintillement  
  
- Attribuez à la propriété <xref:System.Windows.Forms.Control.DoubleBuffered%2A> la valeur `true`.  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#31)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#31)]  
  
 \- ou -  
  
- Appelez la <xref:System.Windows.Forms.Control.SetStyle%2A> méthode pour affecter la valeur <xref:System.Windows.Forms.ControlStyles.OptimizedDoubleBuffer> à l’indicateur `true` .  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#32](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#32)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#32](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#32)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.Control.DoubleBuffered%2A>
- <xref:System.Windows.Forms.Control.SetStyle%2A>
- [Graphiques mis deux fois en mémoire tampon](double-buffered-graphics.md)
- [Graphiques et dessins dans les Windows Forms](graphics-and-drawing-in-windows-forms.md)
