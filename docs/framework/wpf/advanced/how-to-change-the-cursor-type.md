---
title: 'Comment : modifier le type de curseur'
description: Modifiez le curseur du pointeur de la souris pour un élément et pour une application dans Windows Presentation Foundation. Cet exemple se compose de XAML et d’un fichier code-behind.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- mouse pointer [WPF], cursor type
- cursor (mouse pointer)
ms.assetid: 08c945a7-8ab0-4320-acf3-0b4955a344c2
ms.openlocfilehash: ce0bc290948a0e52e85f76ceb62a330b49fd87ea
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165971"
---
# <a name="how-to-change-the-cursor-type"></a>Comment : modifier le type de curseur
Cet exemple montre comment modifier le <xref:System.Windows.Input.Cursor> du pointeur de la souris pour un élément spécifique et pour l’application.  
  
 Cet exemple se compose d’un [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] fichier et d’un fichier code-behind.  
  
## <a name="example"></a>Exemple  
 L’interface utilisateur est créée, qui se compose d’un <xref:System.Windows.Controls.ComboBox> pour sélectionner le souhaité <xref:System.Windows.Input.Cursor> , d’une paire d' <xref:System.Windows.Controls.RadioButton> objets pour déterminer si la modification du curseur s’applique à un seul élément ou s’applique à l’application entière, et <xref:System.Windows.Controls.Border> qui est l’élément auquel le nouveau curseur est appliqué.  
  
 [!code-xaml[cursors#ChangeCursorsXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/cursors/CSharp/Window1.xaml#changecursorsxaml)]  
  
 Le code-behind suivant crée un <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> Gestionnaire d’événements qui est appelé lorsque le type de curseur est modifié dans le <xref:System.Windows.Controls.ComboBox> .  Une instruction switch filtre sur le nom du curseur et définit la <xref:System.Windows.FrameworkElement.Cursor%2A> propriété sur le <xref:System.Windows.Controls.Border> qui est nommé *DisplayArea*.  
  
 Si la modification du curseur est définie sur « application entière », la propriété <xref:System.Windows.Input.Mouse.OverrideCursor%2A> est définie sur la <xref:System.Windows.FrameworkElement.Cursor%2A> propriété du <xref:System.Windows.Controls.Border> contrôle.  Cela force le curseur à changer pour l’ensemble de l’application.  
  
 [!code-csharp[cursors#ChangeCursorsSample](~/samples/snippets/csharp/VS_Snippets_Wpf/cursors/CSharp/Window1.xaml.cs#changecursorssample)]
 [!code-vb[cursors#ChangeCursorsSample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/cursors/VisualBasic/Window1.xaml.vb#changecursorssample)]  
  
## <a name="see-also"></a>Voir aussi

- [Vue d'ensemble des entrées](input-overview.md)
