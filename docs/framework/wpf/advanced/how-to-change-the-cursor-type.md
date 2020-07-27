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
# <a name="how-to-change-the-cursor-type"></a><span data-ttu-id="a6922-104">Comment : modifier le type de curseur</span><span class="sxs-lookup"><span data-stu-id="a6922-104">How to: Change the Cursor Type</span></span>
<span data-ttu-id="a6922-105">Cet exemple montre comment modifier le <xref:System.Windows.Input.Cursor> du pointeur de la souris pour un élément spécifique et pour l’application.</span><span class="sxs-lookup"><span data-stu-id="a6922-105">This example shows how to change the <xref:System.Windows.Input.Cursor> of the mouse pointer for a specific element and for the application.</span></span>  
  
 <span data-ttu-id="a6922-106">Cet exemple se compose d’un [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] fichier et d’un fichier code-behind.</span><span class="sxs-lookup"><span data-stu-id="a6922-106">This example consists of a [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file and a code behind file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a6922-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="a6922-107">Example</span></span>  
 <span data-ttu-id="a6922-108">L’interface utilisateur est créée, qui se compose d’un <xref:System.Windows.Controls.ComboBox> pour sélectionner le souhaité <xref:System.Windows.Input.Cursor> , d’une paire d' <xref:System.Windows.Controls.RadioButton> objets pour déterminer si la modification du curseur s’applique à un seul élément ou s’applique à l’application entière, et <xref:System.Windows.Controls.Border> qui est l’élément auquel le nouveau curseur est appliqué.</span><span class="sxs-lookup"><span data-stu-id="a6922-108">The user interface is created, which consists of a <xref:System.Windows.Controls.ComboBox> to select the desired <xref:System.Windows.Input.Cursor>, a pair of <xref:System.Windows.Controls.RadioButton> objects to determine if the cursor change applies to only a single element or applies to the entire application, and a <xref:System.Windows.Controls.Border> which is the element that the new cursor is applied to.</span></span>  
  
 [!code-xaml[cursors#ChangeCursorsXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/cursors/CSharp/Window1.xaml#changecursorsxaml)]  
  
 <span data-ttu-id="a6922-109">Le code-behind suivant crée un <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> Gestionnaire d’événements qui est appelé lorsque le type de curseur est modifié dans le <xref:System.Windows.Controls.ComboBox> .</span><span class="sxs-lookup"><span data-stu-id="a6922-109">The following code behind creates a <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> event handler which is called when the cursor type is changed in the <xref:System.Windows.Controls.ComboBox>.</span></span>  <span data-ttu-id="a6922-110">Une instruction switch filtre sur le nom du curseur et définit la <xref:System.Windows.FrameworkElement.Cursor%2A> propriété sur le <xref:System.Windows.Controls.Border> qui est nommé *DisplayArea*.</span><span class="sxs-lookup"><span data-stu-id="a6922-110">A switch statement filters on the cursor name and sets the <xref:System.Windows.FrameworkElement.Cursor%2A> property on the <xref:System.Windows.Controls.Border> which is named *DisplayArea*.</span></span>  
  
 <span data-ttu-id="a6922-111">Si la modification du curseur est définie sur « application entière », la propriété <xref:System.Windows.Input.Mouse.OverrideCursor%2A> est définie sur la <xref:System.Windows.FrameworkElement.Cursor%2A> propriété du <xref:System.Windows.Controls.Border> contrôle.</span><span class="sxs-lookup"><span data-stu-id="a6922-111">If the cursor change is set to "Entire Application", the <xref:System.Windows.Input.Mouse.OverrideCursor%2A> property is set to the <xref:System.Windows.FrameworkElement.Cursor%2A> property of the <xref:System.Windows.Controls.Border> control.</span></span>  <span data-ttu-id="a6922-112">Cela force le curseur à changer pour l’ensemble de l’application.</span><span class="sxs-lookup"><span data-stu-id="a6922-112">This forces the cursor to change for the whole application.</span></span>  
  
 [!code-csharp[cursors#ChangeCursorsSample](~/samples/snippets/csharp/VS_Snippets_Wpf/cursors/CSharp/Window1.xaml.cs#changecursorssample)]
 [!code-vb[cursors#ChangeCursorsSample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/cursors/VisualBasic/Window1.xaml.vb#changecursorssample)]  
  
## <a name="see-also"></a><span data-ttu-id="a6922-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a6922-113">See also</span></span>

- [<span data-ttu-id="a6922-114">Vue d'ensemble des entrées</span><span class="sxs-lookup"><span data-stu-id="a6922-114">Input Overview</span></span>](input-overview.md)
