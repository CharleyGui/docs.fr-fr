---
title: "Procédure : Créer un effet de substitution à l'aide d'événements"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- colors of elements [WPF], changing
- rollover effect [WPF]
- element colors [WPF], changing
ms.assetid: 3b20d028-6f1c-4b25-95d2-fa68cefbdb4c
ms.openlocfilehash: 806056397200fa5c567e83227499ba721544f523
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005178"
---
# <a name="how-to-create-a-rollover-effect-using-events"></a>Procédure : Créer un effet de substitution à l'aide d'événements
Cet exemple montre comment modifier la couleur d’un élément lorsque le pointeur de la souris entre dans la zone occupée par l’élément.  
  
 Cet exemple se compose d’un fichier [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] et d’un fichier code-behind.  
  
> [!NOTE]
> Cet exemple montre comment utiliser des événements, mais la méthode recommandée pour obtenir ce même effet consiste à utiliser un <xref:System.Windows.Trigger> dans un style. Pour plus d’informations, consultez [Application d’un style et création de modèles](../controls/styling-and-templating.md).  
  
## <a name="example"></a>Exemple  
 Le code XAML suivant crée l’interface utilisateur, qui se compose de <xref:System.Windows.Controls.Border> autour d’une <xref:System.Windows.Controls.TextBlock>, et associe les gestionnaires d’événements <xref:System.Windows.Input.Mouse.MouseEnter> et <xref:System.Windows.UIElement.MouseLeave> au <xref:System.Windows.Controls.Border>.  
  
 [!code-xaml[mouseenterMouseleave#MouseEnterLeaveSampleXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/mouseenterMouseleave/CSharp/Window1.xaml#mouseenterleavesamplexaml)]  
  
 Le code-behind suivant crée les gestionnaires d’événements <xref:System.Windows.UIElement.MouseEnter> et <xref:System.Windows.UIElement.MouseLeave>.  Lorsque le pointeur de la souris entre dans le <xref:System.Windows.Controls.Border>, l’arrière-plan de la <xref:System.Windows.Controls.Border> est remplacé par le rouge.  Lorsque le pointeur de la souris quitte le <xref:System.Windows.Controls.Border>, l’arrière-plan du <xref:System.Windows.Controls.Border> est rétabli en blanc.  
  
 [!code-csharp[mouseenterMouseleave#MouseEnterLeaveSampleEventHandlers](~/samples/snippets/csharp/VS_Snippets_Wpf/mouseenterMouseleave/CSharp/Window1.xaml.cs#mouseenterleavesampleeventhandlers)]
 [!code-vb[mouseenterMouseleave#MouseEnterLeaveSampleEventHandlers](~/samples/snippets/visualbasic/VS_Snippets_Wpf/mouseenterMouseleave/VisualBasic/Window1.xaml.vb#mouseenterleavesampleeventhandlers)]
