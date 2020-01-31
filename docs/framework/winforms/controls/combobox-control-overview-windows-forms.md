---
title: Vue d'ensemble du contrôle ComboBox
ms.date: 03/30/2017
f1_keywords:
- ComboBox
helpviewer_keywords:
- drop-down lists [Windows Forms], Windows Forms
- ComboBox control [Windows Forms], about ComboBox control
- drop-down lists [Windows Forms], ComboBox control
- combo boxes [Windows Forms], about combo boxes
ms.assetid: a58b393f-a614-45d1-8961-857a024b5acd
ms.openlocfilehash: 9fb270d7787902872a32a87c140316f756bd48aa
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743845"
---
# <a name="combobox-control-overview-windows-forms"></a>Vue d'ensemble du contrôle ComboBox (Windows Forms)
Le contrôle Windows Forms <xref:System.Windows.Forms.ComboBox> permet d’afficher des données dans une zone de liste déroulante. Par défaut, le contrôle <xref:System.Windows.Forms.ComboBox> apparaît en deux parties : la partie supérieure est une zone de texte qui permet à l’utilisateur de taper un élément de liste. La deuxième partie est une zone de liste qui affiche une liste d’éléments à partir desquels l’utilisateur peut en sélectionner une. Pour plus d’informations sur les autres styles de zone de liste déroulante, consultez [When to use a Windows Forms ComboBox au lieu d’un ListBox](when-to-use-a-windows-forms-combobox-instead-of-a-listbox.md).  
  
 La propriété <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A> retourne une valeur entière qui correspond à l’élément de liste sélectionné. Vous pouvez modifier par programmation l’élément sélectionné en modifiant la valeur <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A> dans le code ; l’élément correspondant dans la liste s’affiche dans la partie zone de texte de la zone de liste déroulante. Si aucun élément n’est sélectionné, la valeur <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A> est-1. Si le premier élément de la liste est sélectionné, la valeur <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A> est 0. La propriété <xref:System.Windows.Forms.ComboBox.SelectedItem%2A> est semblable à <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A>, mais retourne l’élément lui-même, généralement une valeur de chaîne. La propriété <xref:System.Windows.Forms.ComboBox.ObjectCollection.Count%2A> reflète le nombre d’éléments dans la liste, et la valeur de la propriété <xref:System.Windows.Forms.ComboBox.ObjectCollection.Count%2A> est toujours supérieure d’une unité à la plus grande valeur <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A> possible, car <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A> est de base zéro.  
  
 Pour ajouter ou supprimer des éléments dans un contrôle <xref:System.Windows.Forms.ComboBox>, utilisez la méthode <xref:System.Windows.Forms.ComboBox.ObjectCollection.Add%2A>, <xref:System.Windows.Forms.ComboBox.ObjectCollection.Insert%2A>, <xref:System.Windows.Forms.ComboBox.ObjectCollection.Clear%2A> ou <xref:System.Windows.Forms.ComboBox.ObjectCollection.Remove%2A>. Vous pouvez également ajouter des éléments à la liste à l’aide de la propriété <xref:System.Windows.Forms.ComboBox.Items%2A> dans le concepteur.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.ComboBox>
- [Vue d'ensemble du contrôle ListBox](listbox-control-overview-windows-forms.md)
- [Utilisation d'un contrôle ComboBox Windows Forms à la place d'un contrôle ListBox](when-to-use-a-windows-forms-combobox-instead-of-a-listbox.md)
- [Guide pratique pour ajouter et supprimer des éléments d'un contrôle ComboBox, ListBox ou CheckedListBox Windows Forms](add-and-remove-items-from-a-wf-combobox.md)
- [Guide pratique pour trier le contenu d'un contrôle ComboBox, CheckedListBox ou ListBox Windows Forms](sort-the-contents-of-a-wf-combobox-listbox-or-checkedlistbox-control.md)
- [Guide pratique pour accéder à des éléments spécifiques d'un contrôle ComboBox, ListBox ou CheckedListBox Windows Forms](access-specific-items-in-a-wf-combobox-listbox-or-checkedlistbox.md)
- [Guide pratique pour lier un contrôle ComboBox ou ListBox Windows Forms aux données](how-to-bind-a-windows-forms-combobox-or-listbox-control-to-data.md)
- [Contrôles Windows Forms utilisés pour l’affichage de listes d’options](windows-forms-controls-used-to-list-options.md)
- [Guide pratique pour créer une table de correspondance pour un contrôle ComboBox, ListBox ou CheckedListBox Windows Forms](create-a-lookup-table-for-a-wf-combobox-listbox.md)
