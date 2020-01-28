---
title: Vue d'ensemble du contrôle ListBox
ms.date: 03/30/2017
f1_keywords:
- ListBox
helpviewer_keywords:
- list boxes [Windows Forms], about list boxes
- ListBox control [Windows Forms], about ListBox control
ms.assetid: 37ea226b-6fc8-4c70-936a-c6af4e0cad4c
ms.openlocfilehash: 1abf8bea5c786f2ce326631370fa294ada09a92c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745184"
---
# <a name="listbox-control-overview-windows-forms"></a>Vue d'ensemble du contrôle ListBox (Windows Forms)
Un contrôle Windows Forms <xref:System.Windows.Forms.ListBox> affiche une liste à partir de laquelle l’utilisateur peut sélectionner un ou plusieurs éléments. Si le nombre total d’éléments est supérieur au nombre qui peut être affiché, une barre de défilement est automatiquement ajoutée au contrôle <xref:System.Windows.Forms.ListBox>. Lorsque la propriété <xref:System.Windows.Forms.ListBox.MultiColumn%2A> est définie sur `true`, la zone de liste affiche des éléments dans plusieurs colonnes et une barre de défilement horizontale s’affiche. Lorsque la propriété <xref:System.Windows.Forms.ListBox.MultiColumn%2A> est définie sur `false`, la zone de liste affiche les éléments dans une seule colonne et une barre de défilement verticale s’affiche. Lorsque <xref:System.Windows.Forms.ListBox.ScrollAlwaysVisible%2A> a la valeur `true`, la barre de défilement s’affiche quel que soit le nombre d’éléments. La propriété <xref:System.Windows.Forms.ListBox.SelectionMode%2A> détermine le nombre d’éléments de liste qui peuvent être sélectionnés à la fois.  
  
## <a name="ways-to-change-the-listbox-control"></a>Méthodes de modification du contrôle ListBox  
 La propriété <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> retourne une valeur entière qui correspond au premier élément sélectionné dans la zone de liste. Vous pouvez modifier par programmation l’élément sélectionné en modifiant la valeur <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> dans le code ; l’élément correspondant dans la liste apparaît en surbrillance dans le Windows Form. Si aucun élément n’est sélectionné, la valeur <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> est-1. Si le premier élément de la liste est sélectionné, la valeur <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> est 0. Lorsque plusieurs éléments sont sélectionnés, la valeur <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> reflète l’élément sélectionné qui apparaît en premier dans la liste. La propriété <xref:System.Windows.Forms.ListBox.SelectedItem%2A> est semblable à <xref:System.Windows.Forms.ListBox.SelectedIndex%2A>, mais retourne l’élément lui-même, généralement une valeur de chaîne. La propriété <xref:System.Windows.Forms.ListBox.ObjectCollection.Count%2A> reflète le nombre d’éléments dans la liste, et la valeur de la propriété <xref:System.Windows.Forms.ListBox.ObjectCollection.Count%2A> est toujours supérieure d’une unité à la plus grande valeur <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> possible, car <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> est de base zéro.  
  
 Pour ajouter ou supprimer des éléments dans un contrôle <xref:System.Windows.Forms.ListBox>, utilisez la méthode <xref:System.Windows.Forms.ListBox.ObjectCollection.Add%2A>, <xref:System.Windows.Forms.ListBox.ObjectCollection.Insert%2A>, <xref:System.Windows.Forms.ListBox.ObjectCollection.Clear%2A> ou <xref:System.Windows.Forms.ListBox.ObjectCollection.Remove%2A>. Vous pouvez également ajouter des éléments à la liste à l’aide de la propriété <xref:System.Windows.Forms.ListBox.Items%2A> au moment de la conception.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.ListBox>
- [Guide pratique pour ajouter et supprimer des éléments d'un contrôle ComboBox, ListBox ou CheckedListBox Windows Forms](add-and-remove-items-from-a-wf-combobox.md)
- [Guide pratique pour trier le contenu d'un contrôle ComboBox, CheckedListBox ou ListBox Windows Forms](sort-the-contents-of-a-wf-combobox-listbox-or-checkedlistbox-control.md)
- [Guide pratique pour lier un contrôle ComboBox ou ListBox Windows Forms aux données](how-to-bind-a-windows-forms-combobox-or-listbox-control-to-data.md)
- [Vue d'ensemble du contrôle ComboBox](combobox-control-overview-windows-forms.md)
- [Vue d'ensemble du contrôle CheckedListBox](checkedlistbox-control-overview-windows-forms.md)
- [Contrôles Windows Forms utilisés pour l’affichage de listes d’options](windows-forms-controls-used-to-list-options.md)
- [Guide pratique pour créer une table de correspondance pour un contrôle ComboBox, ListBox ou CheckedListBox Windows Forms](create-a-lookup-table-for-a-wf-combobox-listbox.md)
