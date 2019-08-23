---
title: 'Procédure : Créer un effet de substitution à l’aide d’événements'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- colors of elements [WPF], changing
- rollover effect [WPF]
- element colors [WPF], changing
ms.assetid: 3b20d028-6f1c-4b25-95d2-fa68cefbdb4c
ms.openlocfilehash: 3996a3b9bb976dd5f2e5b675de3894bbaba7d9d3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960386"
---
# <a name="how-to-create-a-rollover-effect-using-events"></a>Procédure : Créer un effet de substitution à l’aide d’événements
Cet exemple montre comment modifier la couleur d’un élément lorsque le pointeur de la souris entre dans la zone occupée par l’élément.  
  
 Cet exemple se compose d' [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] un fichier et d’un fichier code-behind.  
  
> [!NOTE]
> Cet exemple montre comment utiliser des événements, mais la méthode recommandée pour obtenir ce même effet consiste à utiliser un <xref:System.Windows.Trigger> dans un style. Pour plus d’informations, consultez [Application d’un style et création de modèles](../controls/styling-and-templating.md).  
  
## <a name="example"></a>Exemple  
 Le code [!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)] suivant crée l’interface utilisateur, qui se <xref:System.Windows.Controls.Border> compose de <xref:System.Windows.Controls.TextBlock>autour d’un et attache <xref:System.Windows.Input.Mouse.MouseEnter> les <xref:System.Windows.UIElement.MouseLeave> gestionnaires d’événements et à <xref:System.Windows.Controls.Border>.  
  
 [!code-xaml[mouseenterMouseleave#MouseEnterLeaveSampleXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/mouseenterMouseleave/CSharp/Window1.xaml#mouseenterleavesamplexaml)]  
  
 Le code-behind suivant crée <xref:System.Windows.UIElement.MouseEnter> les <xref:System.Windows.UIElement.MouseLeave> gestionnaires d’événements et.  Lorsque le pointeur <xref:System.Windows.Controls.Border> de la souris <xref:System.Windows.Controls.Border>entre dans, l’arrière-plan de est remplacé par le rouge.  Lorsque le pointeur <xref:System.Windows.Controls.Border> de la souris <xref:System.Windows.Controls.Border>quitte le, l’arrière-plan du est rétabli en blanc.  
  
 [!code-csharp[mouseenterMouseleave#MouseEnterLeaveSampleEventHandlers](~/samples/snippets/csharp/VS_Snippets_Wpf/mouseenterMouseleave/CSharp/Window1.xaml.cs#mouseenterleavesampleeventhandlers)]
 [!code-vb[mouseenterMouseleave#MouseEnterLeaveSampleEventHandlers](~/samples/snippets/visualbasic/VS_Snippets_Wpf/mouseenterMouseleave/VisualBasic/Window1.xaml.vb#mouseenterleavesampleeventhandlers)]
