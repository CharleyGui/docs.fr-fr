---
title: Trier le contenu d’un contrôle ComboBox, ListBox ou CheckedListBox
ms.date: 03/30/2017
helpviewer_keywords:
- CheckedListBox control [Windows Forms], sorting
- ComboBox control [Windows Forms], sorting contents
- combo boxes [Windows Forms], sorting contents
- list boxes [Windows Forms], sorting contents
- ListBox control [Windows Forms], sorting contents
ms.assetid: c268e387-3d1d-4d86-a940-19f6673c8d06
ms.openlocfilehash: dee969d777edf76434622fe632f7e934987a1dc3
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742954"
---
# <a name="how-to-sort-the-contents-of-a-windows-forms-combobox-listbox-or-checkedlistbox-control"></a>Comment : trier le contenu d'un contrôle ComboBox, CheckedListBox ou ListBox Windows Forms
Les contrôles Windows Forms ne sont pas triés lorsqu’ils sont liés aux données. Pour afficher les données triées, utilisez une source de données qui prend en charge le tri, puis faites-la Trier par la source de données. Les sources de données qui prennent en charge le tri sont les vues de données, les gestionnaires d’affichage de données et les tableaux triés.  
  
 Si le contrôle n’est pas lié aux données, vous pouvez le trier.  
  
### <a name="to-sort-the-list"></a>Pour trier la liste  
  
1. Affectez à la propriété `Sorted` la valeur `true`.  
  
     Ce paramètre repositionne tous les éléments de liste existants dans l’ordre de tri.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.ComboBox>
- <xref:System.Windows.Forms.ListBox>
- <xref:System.Windows.Forms.CheckedListBox>
- [Liaison de données Windows Forms](../windows-forms-data-binding.md)
- [Guide pratique pour ajouter et supprimer des éléments d'un contrôle ComboBox, ListBox ou CheckedListBox Windows Forms](add-and-remove-items-from-a-wf-combobox.md)
- [Utilisation d'un contrôle ComboBox Windows Forms à la place d'un contrôle ListBox](when-to-use-a-windows-forms-combobox-instead-of-a-listbox.md)
- [Contrôles Windows Forms utilisés pour l’affichage de listes d’options](windows-forms-controls-used-to-list-options.md)
