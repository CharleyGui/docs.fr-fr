---
title: "Comment : redimensionner un Canvas à l'aide d'un curseur"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- resizing Canvas control [WPF]
- controls [WPF], Thumb
- controls [WPF], Canvas
- Thumb control [WPF]
- Canvas control [WPF]
ms.assetid: 7dc9f435-726c-4d4d-be41-eb24cfe17bef
ms.openlocfilehash: 84f5ac2b53124b7f4d7c15741e94b40e7ee81526
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77124297"
---
# <a name="how-to-resize-a-canvas-by-using-a-thumb"></a>Comment : redimensionner un Canvas à l'aide d'un curseur
Cet exemple montre comment utiliser un contrôle <xref:System.Windows.Controls.Primitives.Thumb> pour redimensionner un contrôle <xref:System.Windows.Controls.Canvas>.  
  
## <a name="example"></a>Exemple  
 Le contrôle <xref:System.Windows.Controls.Primitives.Thumb> fournit des fonctionnalités de glissement qui peuvent être utilisées pour déplacer ou redimensionner des contrôles en surveillant les événements <xref:System.Windows.Controls.Primitives.Thumb.DragStarted>, <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> et <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted> de l' <xref:System.Windows.Controls.Primitives.Thumb>.  
  
 L’utilisateur commence une opération glisser en appuyant sur le bouton gauche de la souris lorsque le pointeur de la souris est suspendu sur le contrôle de <xref:System.Windows.Controls.Primitives.Thumb>. L’opération glisser se poursuit aussi longtemps que le bouton gauche de la souris reste enfoncé. Au cours de l’opération glisser, l' <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> peut se produire plusieurs fois. À chaque fois qu’il se produit, la classe <xref:System.Windows.Controls.Primitives.DragDeltaEventArgs> fournit la modification de position qui correspond à la modification de la position de la souris. Lorsque l’utilisateur relâche le bouton gauche de la souris, l’opération glisser est terminée. L’opération glisser fournit uniquement de nouvelles coordonnées ; elle ne repositionne pas automatiquement le <xref:System.Windows.Controls.Primitives.Thumb>.  
  
 L’exemple suivant montre un contrôle <xref:System.Windows.Controls.Primitives.Thumb> qui est l’élément enfant d’un contrôle <xref:System.Windows.Controls.Canvas>. Le gestionnaire d’événements pour son événement <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> fournit la logique pour déplacer le <xref:System.Windows.Controls.Primitives.Thumb> et redimensionner le <xref:System.Windows.Controls.Canvas>. Les gestionnaires d’événements pour l’événement <xref:System.Windows.Controls.Primitives.Thumb.DragStarted> et <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted> changent la couleur de la <xref:System.Windows.Controls.Primitives.Thumb> pendant une opération glisser. L’exemple suivant définit le <xref:System.Windows.Controls.Primitives.Thumb>.  
  
 [!code-xaml[Thumb#thumb](~/samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml#thumb)]  
  
 L’exemple suivant montre le gestionnaire d’événements <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> qui déplace le <xref:System.Windows.Controls.Primitives.Thumb> et redimensionne le <xref:System.Windows.Controls.Canvas> en réponse à un mouvement de la souris.  
  
 [!code-csharp[Thumb#2](~/samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml.cs#2)]  
  
 L’exemple suivant montre le gestionnaire d’événements <xref:System.Windows.Controls.Primitives.Thumb.DragStarted>.  
  
 [!code-csharp[Thumb#DragStartedHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml.cs#dragstartedhandler)]
 [!code-vb[Thumb#DragStartedHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Thumb/VisualBasic/Pane1.xaml.vb#dragstartedhandler)]  
  
 L’exemple suivant montre le gestionnaire d’événements <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted>.  
  
 [!code-csharp[Thumb#DragCompletedHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml.cs#dragcompletedhandler)]
 [!code-vb[Thumb#DragCompletedHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Thumb/VisualBasic/Pane1.xaml.vb#dragcompletedhandler)]  
  
 Pour obtenir l’exemple complet, consultez [exemple de fonctionnalités Thumb Drag](https://github.com/Microsoft/WPF-Samples/tree/master/Drag%20and%20Drop/DragDropThumbOps).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Controls.Primitives.Thumb>
- <xref:System.Windows.Controls.Primitives.Thumb.DragStarted>
- <xref:System.Windows.Controls.Primitives.Thumb.DragDelta>
- <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted>
