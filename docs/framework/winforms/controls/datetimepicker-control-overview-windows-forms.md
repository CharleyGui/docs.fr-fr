---
title: Vue d'ensemble du contrôle DateTimePicker
ms.date: 03/30/2017
f1_keywords:
- DateTimePicker
helpviewer_keywords:
- DateTimePicker control [Windows Forms], about
- date and time picker controls
ms.assetid: 501af106-e9fc-4efc-b9b3-c9d8dcaf8c5c
ms.openlocfilehash: 63271dd91116c1f68d426f3ed5aa710644ded928
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746940"
---
# <a name="datetimepicker-control-overview-windows-forms"></a>Vue d'ensemble du contrôle DateTimePicker (Windows Forms)
Le contrôle Windows Forms <xref:System.Windows.Forms.DateTimePicker> permet à l’utilisateur de sélectionner un seul élément dans une liste de dates ou d’heures. Lorsqu’il est utilisé pour représenter une date, il apparaît en deux parties : une liste déroulante avec une date représentée dans le texte et une grille qui s’affiche lorsque vous cliquez sur la flèche vers le bas en regard de la liste. La grille ressemble au contrôle <xref:System.Windows.Forms.MonthCalendar>, qui peut être utilisé pour sélectionner plusieurs dates. Pour plus d’informations sur le contrôle <xref:System.Windows.Forms.MonthCalendar>, consultez [vue d’ensemble du contrôle MonthCalendar](monthcalendar-control-overview-windows-forms.md).  
  
## <a name="key-properties"></a>Propriétés de clé  
 Si vous souhaitez que le <xref:System.Windows.Forms.DateTimePicker> apparaisse comme un contrôle pour le choix ou la modification des heures au lieu des dates, affectez à la propriété <xref:System.Windows.Forms.DateTimePicker.ShowUpDown%2A> la valeur `true` et à la propriété <xref:System.Windows.Forms.DateTimePicker.Format%2A> la valeur <xref:System.Windows.Forms.DateTimePickerFormat.Time>. Pour plus d’informations, consultez [Comment : afficher l’heure avec le contrôle DateTimePicker](how-to-display-time-with-the-datetimepicker-control.md).  
  
 Lorsque la propriété <xref:System.Windows.Forms.DateTimePicker.ShowCheckBox%2A> est définie sur `true`, une case à cocher s’affiche en regard de la date sélectionnée dans le contrôle. Lorsque la case à cocher est activée, la valeur date-heure sélectionnée peut être mise à jour. Lorsque la case à cocher est vide, la valeur apparaît comme non disponible.  
  
 Les propriétés <xref:System.Windows.Forms.DateTimePicker.MaxDate%2A> et <xref:System.Windows.Forms.DateTimePicker.MinDate%2A> du contrôle déterminent la plage de dates et d’heures. La propriété <xref:System.Windows.Forms.DateTimePicker.Value%2A> contient la date et l’heure actuelles auxquelles le contrôle a la valeur. Pour plus d’informations, consultez [Comment : définir et retourner des dates avec le contrôle Windows Forms DateTimePicker](how-to-set-and-return-dates-with-the-windows-forms-datetimepicker-control.md). Les valeurs peuvent être affichées dans quatre formats, qui sont définis par la propriété <xref:System.Windows.Forms.DateTimePicker.Format%2A> : <xref:System.Windows.Forms.DateTimePickerFormat.Long>, <xref:System.Windows.Forms.DateTimePickerFormat.Short>, <xref:System.Windows.Forms.DateTimePickerFormat.Time>ou <xref:System.Windows.Forms.DateTimePickerFormat.Custom>. Si un format personnalisé est sélectionné, vous devez définir la propriété <xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A> sur une chaîne appropriée. Pour plus d’informations, consultez [Comment : afficher une date dans un format personnalisé avec le contrôle Windows Forms DateTimePicker](display-a-date-in-a-custom-format-with-wf-datetimepicker-control.md).  
  
## <a name="see-also"></a>Voir aussi

- [Guide pratique pour afficher une date dans un format personnalisé à l'aide du contrôle DateTimePicker Windows Forms](display-a-date-in-a-custom-format-with-wf-datetimepicker-control.md)
- [Guide pratique pour définir et retourner des dates à l'aide du contrôle DateTimePicker Windows Forms](how-to-set-and-return-dates-with-the-windows-forms-datetimepicker-control.md)
