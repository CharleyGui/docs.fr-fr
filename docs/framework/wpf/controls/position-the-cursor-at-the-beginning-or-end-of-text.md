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
# <a name="how-to-position-the-cursor-at-the-beginning-or-end-of-text-in-a-textbox-control"></a><span data-ttu-id="2a7d4-103">Comment : positionner le curseur au début ou à la fin du texte dans un contrôle TextBox</span><span class="sxs-lookup"><span data-stu-id="2a7d4-103">How to: Position the Cursor at the Beginning or End of Text in a TextBox Control</span></span>
<span data-ttu-id="2a7d4-104">Cet exemple montre comment positionner le curseur au début ou à la fin du texte contenu dans un <xref:System.Windows.Controls.TextBox> contrôle.</span><span class="sxs-lookup"><span data-stu-id="2a7d4-104">This example shows how to position the cursor at the beginning or end of the text contents of a <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2a7d4-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="2a7d4-105">Example</span></span>  
 <span data-ttu-id="2a7d4-106">Le [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] code suivant décrit un <xref:System.Windows.Controls.TextBox> contrôle et lui attribue un nom.</span><span class="sxs-lookup"><span data-stu-id="2a7d4-106">The following [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] code describes a <xref:System.Windows.Controls.TextBox> control and assigns it a Name.</span></span>  
  
 [!code-xaml[TextBox_MiscCode#_MoveCursorXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_movecursorxaml)]  
  
## <a name="example"></a><span data-ttu-id="2a7d4-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="2a7d4-107">Example</span></span>  
 <span data-ttu-id="2a7d4-108">Pour positionner le curseur au début du contenu d’un <xref:System.Windows.Controls.TextBox> contrôle, appelez la <xref:System.Windows.Controls.TextBox.Select%2A> méthode et spécifiez la position de début de la sélection 0 et une longueur de sélection de 0.</span><span class="sxs-lookup"><span data-stu-id="2a7d4-108">To position the cursor at the beginning of the contents of a <xref:System.Windows.Controls.TextBox> control, call the <xref:System.Windows.Controls.TextBox.Select%2A> method and specify the selection start position of 0, and a selection length of 0.</span></span>  
  
 [!code-csharp[TextBox_MiscCode#_CursorToStart](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_cursortostart)]
 [!code-vb[TextBox_MiscCode#_CursorToStart](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_cursortostart)]  
  
## <a name="example"></a><span data-ttu-id="2a7d4-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="2a7d4-109">Example</span></span>  
 <span data-ttu-id="2a7d4-110">Pour positionner le curseur à la fin du contenu d’un <xref:System.Windows.Controls.TextBox> contrôle, appelez la <xref:System.Windows.Controls.TextBox.Select%2A> méthode et spécifiez la position de début de la sélection comme étant égale à la longueur du contenu de texte, et une longueur de sélection de 0.</span><span class="sxs-lookup"><span data-stu-id="2a7d4-110">To position the cursor at the end of the contents of a <xref:System.Windows.Controls.TextBox> control, call the <xref:System.Windows.Controls.TextBox.Select%2A> method and specify the selection start position equal to the  length of the text content, and a selection length of 0.</span></span>  
  
 [!code-csharp[TextBox_MiscCode#_CursorToEnd](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_cursortoend)]
 [!code-vb[TextBox_MiscCode#_CursorToEnd](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_cursortoend)]  
  
## <a name="see-also"></a><span data-ttu-id="2a7d4-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2a7d4-111">See also</span></span>

- [<span data-ttu-id="2a7d4-112">Vue d'ensemble de TextBox</span><span class="sxs-lookup"><span data-stu-id="2a7d4-112">TextBox Overview</span></span>](textbox-overview.md)
- [<span data-ttu-id="2a7d4-113">Vue d'ensemble de RichTextBox</span><span class="sxs-lookup"><span data-stu-id="2a7d4-113">RichTextBox Overview</span></span>](richtextbox-overview.md)
