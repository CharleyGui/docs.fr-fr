---
title: "Procédure : Modifier la couleur d'un élément à l'aide d'événements Focus"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- focus events [WPF], changing element color for
- colors of elements [WPF], changing
- elements [WPF], changing color of
ms.assetid: 7e246802-3625-47a7-ae9d-c8a2a40fd040
ms.openlocfilehash: 5c59dc5f2f8f26fac69933f9ef641a3a51306619
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004837"
---
# <a name="how-to-change-the-color-of-an-element-using-focus-events"></a>Procédure : Modifier la couleur d'un élément à l'aide d'événements Focus
Cet exemple montre comment modifier la couleur d’un élément quand il gagne et perd le focus à l’aide des événements <xref:System.Windows.UIElement.GotFocus> et <xref:System.Windows.UIElement.LostFocus>.  
  
 Cet exemple se compose d’un fichier [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] et d’un fichier code-behind.  
  
## <a name="example"></a>Exemple  
 Le code XAML suivant crée l’interface utilisateur, qui se compose de deux objets <xref:System.Windows.Controls.Button>, et attache des gestionnaires d’événements pour les événements <xref:System.Windows.UIElement.GotFocus> et <xref:System.Windows.UIElement.LostFocus> aux objets <xref:System.Windows.Controls.Button>.  
  
 [!code-xaml[gotfocusLostfocusEffectUsingEvent#GotLostFocusSampleXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/gotfocusLostfocusEffectUsingEvent/CSharp/Window1.xaml#gotlostfocussamplexaml)]  
  
 Le code-behind suivant crée les gestionnaires d’événements <xref:System.Windows.UIElement.GotFocus> et <xref:System.Windows.UIElement.LostFocus>.  Lorsque l' <xref:System.Windows.Controls.Button> obtient le focus clavier, la <xref:System.Windows.Controls.Control.Background%2A> de la <xref:System.Windows.Controls.Button> est remplacée par la couleur rouge.  Lorsque l' <xref:System.Windows.Controls.Button> perd le focus clavier, le <xref:System.Windows.Controls.Control.Background%2A> du <xref:System.Windows.Controls.Button> est rétabli en blanc.  
  
 [!code-csharp[gotfocusLostfocusEffectUsingEvent#GotLostFocusSampleEventHandlers](~/samples/snippets/csharp/VS_Snippets_Wpf/gotfocusLostfocusEffectUsingEvent/CSharp/Window1.xaml.cs#gotlostfocussampleeventhandlers)]
 [!code-vb[gotfocusLostfocusEffectUsingEvent#GotLostFocusSampleEventHandlers](~/samples/snippets/visualbasic/VS_Snippets_Wpf/gotfocusLostfocusEffectUsingEvent/VisualBasic/Window1.xaml.vb#gotlostfocussampleeventhandlers)]  
  
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble des entrées](input-overview.md)
