---
title: ComboBox et ListBox
ms.date: 03/30/2017
helpviewer_keywords:
- ListBox control [Windows Forms], adding and removing items
- ListBox control [Windows Forms], vs. ComboBox
- bound controls [Windows Forms], combo boxes
- Windows Forms controls, data binding
- ComboBox control [Windows Forms], compared to ListBox
- combo boxes [Windows Forms], compared to list boxes
- ListBox control [Windows Forms], accessing items
- ListCount property
ms.assetid: 7bcaea58-1cfa-46db-9baf-b75a69d8f9ec
ms.openlocfilehash: 7087760a393bb58d83d899c1741c745fb28585bb
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76739929"
---
# <a name="when-to-use-a-windows-forms-combobox-instead-of-a-listbox"></a><span data-ttu-id="e54c5-102">Utilisation d'un contrôle ComboBox Windows Forms à la place d'un contrôle ListBox</span><span class="sxs-lookup"><span data-stu-id="e54c5-102">When to Use a Windows Forms ComboBox Instead of a ListBox</span></span>
<span data-ttu-id="e54c5-103">Les contrôles <xref:System.Windows.Forms.ComboBox> et <xref:System.Windows.Forms.ListBox> ont des comportements similaires et, dans certains cas, peuvent être interchangeables.</span><span class="sxs-lookup"><span data-stu-id="e54c5-103">The <xref:System.Windows.Forms.ComboBox> and the <xref:System.Windows.Forms.ListBox> controls have similar behaviors, and in some cases may be interchangeable.</span></span> <span data-ttu-id="e54c5-104">Toutefois, il y a des cas où l’un ou l’autre est plus approprié à une tâche.</span><span class="sxs-lookup"><span data-stu-id="e54c5-104">There are times, however, when one or the other is more appropriate to a task.</span></span>  
  
 <span data-ttu-id="e54c5-105">En règle générale, une zone de liste déroulante est appropriée lorsqu’il existe une liste de choix suggérés, et une zone de liste est appropriée lorsque vous souhaitez limiter l’entrée à ce qui se trouve dans la liste.</span><span class="sxs-lookup"><span data-stu-id="e54c5-105">Generally, a combo box is appropriate when there is a list of suggested choices, and a list box is appropriate when you want to limit input to what is on the list.</span></span> <span data-ttu-id="e54c5-106">Une zone de liste déroulante contient un champ de zone de texte. par conséquent, les choix qui ne sont pas dans la liste peuvent être tapés dans.</span><span class="sxs-lookup"><span data-stu-id="e54c5-106">A combo box contains a text box field, so choices not on the list can be typed in.</span></span> <span data-ttu-id="e54c5-107">L’exception est lorsque la propriété <xref:System.Windows.Forms.ComboBox.DropDownStyle%2A> a la valeur <xref:System.Windows.Forms.ComboBoxStyle.DropDownList>.</span><span class="sxs-lookup"><span data-stu-id="e54c5-107">The exception is when the <xref:System.Windows.Forms.ComboBox.DropDownStyle%2A> property is set to <xref:System.Windows.Forms.ComboBoxStyle.DropDownList>.</span></span> <span data-ttu-id="e54c5-108">Dans ce cas, le contrôle sélectionne un élément si vous tapez sa première lettre.</span><span class="sxs-lookup"><span data-stu-id="e54c5-108">In that case, the control will select an item if you type its first letter.</span></span>  
  
 <span data-ttu-id="e54c5-109">En outre, les zones de liste déroulante enregistrent de l’espace sur un formulaire.</span><span class="sxs-lookup"><span data-stu-id="e54c5-109">In addition, combo boxes save space on a form.</span></span> <span data-ttu-id="e54c5-110">Étant donné que la liste complète n’est pas affichée tant que l’utilisateur n’a pas cliqué sur la flèche orientée vers le bas, une zone de liste modifiable peut facilement tenir dans un petit espace dans lequel une zone de liste ne s’ajuste pas.</span><span class="sxs-lookup"><span data-stu-id="e54c5-110">Because the full list is not displayed until the user clicks the down arrow, a combo box can easily fit in a small space where a list box would not fit.</span></span> <span data-ttu-id="e54c5-111">Une exception est quand la propriété <xref:System.Windows.Forms.ComboBox.DropDownStyle%2A> a la valeur <xref:System.Windows.Forms.ComboBoxStyle.Simple>: la liste complète s’affiche et la zone de liste déroulante occupe plus de place qu’une zone de liste.</span><span class="sxs-lookup"><span data-stu-id="e54c5-111">An exception is when the <xref:System.Windows.Forms.ComboBox.DropDownStyle%2A> property is set to <xref:System.Windows.Forms.ComboBoxStyle.Simple>: the full list is displayed, and the combo box takes up more room than a list box would.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e54c5-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e54c5-112">See also</span></span>

- <xref:System.Windows.Forms.ComboBox>
- <xref:System.Windows.Forms.ListBox>
- [<span data-ttu-id="e54c5-113">Guide pratique pour ajouter et supprimer des éléments d'un contrôle ComboBox, ListBox ou CheckedListBox Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e54c5-113">How to: Add and Remove Items from a Windows Forms ComboBox, ListBox, or CheckedListBox Control</span></span>](add-and-remove-items-from-a-wf-combobox.md)
- [<span data-ttu-id="e54c5-114">Guide pratique pour trier le contenu d'un contrôle ComboBox, CheckedListBox ou ListBox Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e54c5-114">How to: Sort the Contents of a Windows Forms ComboBox, ListBox, or CheckedListBox Control</span></span>](sort-the-contents-of-a-wf-combobox-listbox-or-checkedlistbox-control.md)
- [<span data-ttu-id="e54c5-115">Contrôles Windows Forms utilisés pour l’affichage de listes d’options</span><span class="sxs-lookup"><span data-stu-id="e54c5-115">Windows Forms Controls Used to List Options</span></span>](windows-forms-controls-used-to-list-options.md)
