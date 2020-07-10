---
title: ComboBox et ListBox
description: En savoir plus sur l’utilisation de Windows Forms ComboBox et Windows Forms ListBox, et savoir comment savoir quand l’un ou l’autre est plus approprié pour une tâche.
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
ms.openlocfilehash: ca6ad6bec2dbc30128ea09808af2806687b17a8c
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174417"
---
# <a name="when-to-use-a-windows-forms-combobox-instead-of-a-listbox"></a>Utilisation d'un contrôle ComboBox Windows Forms à la place d'un contrôle ListBox
Les <xref:System.Windows.Forms.ComboBox> contrôles et <xref:System.Windows.Forms.ListBox> ont des comportements similaires et, dans certains cas, peuvent être interchangeables. Toutefois, il y a des cas où l’un ou l’autre est plus approprié à une tâche.  
  
 En règle générale, une zone de liste déroulante est appropriée lorsqu’il existe une liste de choix suggérés, et une zone de liste est appropriée lorsque vous souhaitez limiter l’entrée à ce qui se trouve dans la liste. Une zone de liste déroulante contient un champ de zone de texte. par conséquent, les choix qui ne sont pas dans la liste peuvent être tapés dans. L’exception est lorsque la <xref:System.Windows.Forms.ComboBox.DropDownStyle%2A> propriété a la valeur <xref:System.Windows.Forms.ComboBoxStyle.DropDownList> . Dans ce cas, le contrôle sélectionne un élément si vous tapez sa première lettre.  
  
 En outre, les zones de liste déroulante enregistrent de l’espace sur un formulaire. Étant donné que la liste complète n’est pas affichée tant que l’utilisateur n’a pas cliqué sur la flèche orientée vers le bas, une zone de liste modifiable peut facilement tenir dans un petit espace dans lequel une zone de liste ne s’ajuste pas. Une exception est quand la <xref:System.Windows.Forms.ComboBox.DropDownStyle%2A> propriété a la valeur <xref:System.Windows.Forms.ComboBoxStyle.Simple> : la liste complète s’affiche et la zone de liste déroulante occupe plus de place qu’une zone de liste.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.ComboBox>
- <xref:System.Windows.Forms.ListBox>
- [Guide pratique pour ajouter et supprimer des éléments d'un contrôle ComboBox, ListBox ou CheckedListBox Windows Forms](add-and-remove-items-from-a-wf-combobox.md)
- [Comment : trier le contenu d'un contrôle ComboBox, CheckedListBox ou ListBox Windows Forms](sort-the-contents-of-a-wf-combobox-listbox-or-checkedlistbox-control.md)
- [Contrôles Windows Forms utilisés pour l'affichage de listes d'options](windows-forms-controls-used-to-list-options.md)
