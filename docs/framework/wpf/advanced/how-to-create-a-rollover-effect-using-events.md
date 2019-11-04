---
title: "Comment : créer un effet de substitution à l'aide d'événements"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- colors of elements [WPF], changing
- rollover effect [WPF]
- element colors [WPF], changing
ms.assetid: 3b20d028-6f1c-4b25-95d2-fa68cefbdb4c
ms.openlocfilehash: ccdc8aeb26b538814b2f9020e1e3a5b311fa5a99
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460159"
---
# <a name="how-to-create-a-rollover-effect-using-events"></a>Comment : créer un effet de substitution à l'aide d'événements
Cet exemple montre comment modifier la couleur d’un élément lorsque le pointeur de la souris entre dans la zone occupée par l’élément.  
  
 Cet exemple se compose d’un fichier de [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] et d’un fichier code-behind.  
  
> [!NOTE]
> Cet exemple montre comment utiliser des événements, mais la méthode recommandée pour obtenir ce même effet consiste à utiliser un <xref:System.Windows.Trigger> dans un style. Pour plus d’informations, consultez [Application d’un style et création de modèles](../../../desktop-wpf/fundamentals/styles-templates-overview.md).  
  
## <a name="example"></a>Exemple  
 Le code XAML suivant crée l’interface utilisateur, qui se compose d' <xref:System.Windows.Controls.Border> autour d’un <xref:System.Windows.Controls.TextBlock>, et associe les gestionnaires d’événements <xref:System.Windows.Input.Mouse.MouseEnter> et <xref:System.Windows.UIElement.MouseLeave> au <xref:System.Windows.Controls.Border>.  
  
 [!code-xaml[mouseenterMouseleave#MouseEnterLeaveSampleXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/mouseenterMouseleave/CSharp/Window1.xaml#mouseenterleavesamplexaml)]  
  
 Le code-behind suivant crée les gestionnaires d’événements <xref:System.Windows.UIElement.MouseEnter> et <xref:System.Windows.UIElement.MouseLeave>.  Lorsque le pointeur de la souris entre dans le <xref:System.Windows.Controls.Border>, l’arrière-plan du <xref:System.Windows.Controls.Border> devient rouge.  Lorsque le pointeur de la souris quitte le <xref:System.Windows.Controls.Border>, l’arrière-plan du <xref:System.Windows.Controls.Border> est rétabli en blanc.  
  
 [!code-csharp[mouseenterMouseleave#MouseEnterLeaveSampleEventHandlers](~/samples/snippets/csharp/VS_Snippets_Wpf/mouseenterMouseleave/CSharp/Window1.xaml.cs#mouseenterleavesampleeventhandlers)]
 [!code-vb[mouseenterMouseleave#MouseEnterLeaveSampleEventHandlers](~/samples/snippets/visualbasic/VS_Snippets_Wpf/mouseenterMouseleave/VisualBasic/Window1.xaml.vb#mouseenterleavesampleeventhandlers)]
