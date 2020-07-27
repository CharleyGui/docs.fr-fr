---
title: 'Comment : positionner le curseur au début ou à la fin du texte dans un contrôle TextBox'
description: Apprenez à positionner le curseur au début ou à la fin du texte contenu dans un contrôle Windows Presentation Foundation TextBox.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- positioning cursor [WPF]
- TextBox control [WPF], positioning cursor
- cursor [WPF], positioning
ms.assetid: c771a0b8-c6b4-4240-aecd-a21d0ba51a2e
ms.openlocfilehash: afe8b11d032b5d61fa91cbf324f02cd8415d2ea8
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87167513"
---
# <a name="how-to-position-the-cursor-at-the-beginning-or-end-of-text-in-a-textbox-control"></a>Comment : positionner le curseur au début ou à la fin du texte dans un contrôle TextBox
Cet exemple montre comment positionner le curseur au début ou à la fin du texte contenu dans un <xref:System.Windows.Controls.TextBox> contrôle.  
  
## <a name="example"></a>Exemple  
 Le [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] code suivant décrit un <xref:System.Windows.Controls.TextBox> contrôle et lui attribue un nom.  
  
 [!code-xaml[TextBox_MiscCode#_MoveCursorXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_movecursorxaml)]  
  
## <a name="example"></a>Exemple  
 Pour positionner le curseur au début du contenu d’un <xref:System.Windows.Controls.TextBox> contrôle, appelez la <xref:System.Windows.Controls.TextBox.Select%2A> méthode et spécifiez la position de début de la sélection 0 et une longueur de sélection de 0.  
  
 [!code-csharp[TextBox_MiscCode#_CursorToStart](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_cursortostart)]
 [!code-vb[TextBox_MiscCode#_CursorToStart](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_cursortostart)]  
  
## <a name="example"></a>Exemple  
 Pour positionner le curseur à la fin du contenu d’un <xref:System.Windows.Controls.TextBox> contrôle, appelez la <xref:System.Windows.Controls.TextBox.Select%2A> méthode et spécifiez la position de début de la sélection comme étant égale à la longueur du contenu de texte, et une longueur de sélection de 0.  
  
 [!code-csharp[TextBox_MiscCode#_CursorToEnd](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_cursortoend)]
 [!code-vb[TextBox_MiscCode#_CursorToEnd](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_cursortoend)]  
  
## <a name="see-also"></a>Voir aussi

- [Vue d'ensemble de TextBox](textbox-overview.md)
- [Vue d'ensemble de RichTextBox](richtextbox-overview.md)
