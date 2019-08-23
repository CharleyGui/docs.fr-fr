---
title: 'Procédure : Créer et utiliser un canevas'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], Canvas
- Canvas control [WPF], creating
- Canvas control [WPF], using
ms.assetid: 420b9487-9a15-477c-9489-a22a4dec7779
ms.openlocfilehash: edef660b2da2f09e0a6edbc0a87f0d1f26eb03da
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964222"
---
# <a name="how-to-create-and-use-a-canvas"></a>Procédure : Créer et utiliser un canevas
Cet exemple montre comment créer et utiliser une instance de <xref:System.Windows.Controls.Canvas>.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant positionne explicitement deux <xref:System.Windows.Controls.TextBlock> éléments à <xref:System.Windows.Controls.Canvas.SetTop%2A> l’aide des <xref:System.Windows.Controls.Canvas.SetLeft%2A> méthodes et <xref:System.Windows.Controls.Canvas>de. L’exemple assigne également une <xref:System.Windows.Controls.Control.Background%2A> couleur de `LightSteelBlue` à <xref:System.Windows.Controls.Canvas>.  
  
> [!NOTE]
> Lorsque vous utilisez [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] pour positionner <xref:System.Windows.Controls.TextBlock> des éléments, utilisez <xref:System.Windows.Controls.Canvas.Top%2A> les <xref:System.Windows.Controls.Canvas.Left%2A> propriétés et.  
  
 [!code-csharp[CanvasCode#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CanvasCode/CSharp/Canvas_Code.cs#1)]
 [!code-vb[CanvasCode#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CanvasCode/VisualBasic/canvas_vb.vb#1)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Controls.Canvas>
- <xref:System.Windows.Controls.TextBlock>
- <xref:System.Windows.Controls.Canvas.SetTop%2A>
- <xref:System.Windows.Controls.Canvas.SetLeft%2A>
- <xref:System.Windows.Controls.Canvas.Top%2A>
- <xref:System.Windows.Controls.Canvas.Left%2A>
- [Vue d’ensemble de Panel](panels-overview.md)
- [Rubriques de guide pratique](canvas-how-to-topics.md)
