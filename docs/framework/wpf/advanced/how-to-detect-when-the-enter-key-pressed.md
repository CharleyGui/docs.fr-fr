---
title: 'Procédure : Détecter quand la touche entrée est enfoncée'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Enter key [WPF], detecting
- keys [WPF], Enter
ms.assetid: a66f39d2-ef4a-43a5-b454-a4ea0fe88655
ms.openlocfilehash: e2337826077c836696937f91541d6d261f1270aa
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004823"
---
# <a name="how-to-detect-when-the-enter-key-pressed"></a>Procédure : Détecter quand la touche entrée est enfoncée
Cet exemple montre comment détecter quand la touche <xref:System.Windows.Input.Key.Enter> est enfoncée sur le clavier.  
  
 Cet exemple se compose d’un fichier [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] et d’un fichier code-behind.  
  
## <a name="example"></a>Exemple  
 Lorsque l’utilisateur appuie sur la touche <xref:System.Windows.Input.Key.Enter> dans la <xref:System.Windows.Controls.TextBox>, le texte entré s’affiche dans une autre zone de la [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)].  
  
 Le code XAML suivant crée l’interface utilisateur, qui se compose d’un <xref:System.Windows.Controls.StackPanel>, d’un <xref:System.Windows.Controls.TextBlock> et d’un <xref:System.Windows.Controls.TextBox>.  
  
 [!code-xaml[keydown#KeyDownUI](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyDown/CSharp/Window1.xaml#keydownui)]  
  
 Le code-behind suivant crée le <xref:System.Windows.UIElement.KeyDown> Gestionnaire d’événements.  Si la touche enfoncée est la touche <xref:System.Windows.Input.Key.Enter>, un message s’affiche dans le <xref:System.Windows.Controls.TextBlock>.  
  
 [!code-csharp[keydown#KeyDownSample](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyDown/CSharp/Window1.xaml.cs#keydownsample)]
 [!code-vb[keydown#KeyDownSample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/KeyDown/VisualBasic/Window1.xaml.vb#keydownsample)]  
  
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble des entrées](input-overview.md)
- [Vue d’ensemble des événements routés](routed-events-overview.md)
