---
title: "Comment : effectuer une détection en cas d'appui sur la touche Entrée"
description: Détectez quand la touche entrée est sélectionnée sur le clavier dans Windows Presentation Foundation. Cet exemple se compose de XAML et d’un fichier code-behind.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Enter key [WPF], detecting
- keys [WPF], Enter
ms.assetid: a66f39d2-ef4a-43a5-b454-a4ea0fe88655
ms.openlocfilehash: a955f52ec7bf93b32c70259b27fb51747664ac2e
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87163186"
---
# <a name="how-to-detect-when-the-enter-key-pressed"></a>Comment : effectuer une détection en cas d'appui sur la touche Entrée
Cet exemple montre comment détecter le moment où la <xref:System.Windows.Input.Key.Enter> touche est enfoncée sur le clavier.  
  
 Cet exemple se compose d’un [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] fichier et d’un fichier code-behind.  
  
## <a name="example"></a>Exemple  
 Quand l’utilisateur appuie sur la <xref:System.Windows.Input.Key.Enter> touche dans le <xref:System.Windows.Controls.TextBox> , l’entrée dans la zone de texte apparaît dans une autre zone du [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] .  
  
 Le code XAML suivant crée l’interface utilisateur, qui se compose d’un, d’un <xref:System.Windows.Controls.StackPanel> <xref:System.Windows.Controls.TextBlock> et d’un <xref:System.Windows.Controls.TextBox> .  
  
 [!code-xaml[keydown#KeyDownUI](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyDown/CSharp/Window1.xaml#keydownui)]  
  
 Le code-behind suivant crée le <xref:System.Windows.UIElement.KeyDown> Gestionnaire d’événements.  Si la touche enfoncée est la <xref:System.Windows.Input.Key.Enter> clé, un message s’affiche dans la <xref:System.Windows.Controls.TextBlock> .  
  
 [!code-csharp[keydown#KeyDownSample](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyDown/CSharp/Window1.xaml.cs#keydownsample)]
 [!code-vb[keydown#KeyDownSample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/KeyDown/VisualBasic/Window1.xaml.vb#keydownsample)]  
  
## <a name="see-also"></a>Voir aussi

- [Vue d'ensemble des entrées](input-overview.md)
- [Vue d'ensemble des événements routés](routed-events-overview.md)
