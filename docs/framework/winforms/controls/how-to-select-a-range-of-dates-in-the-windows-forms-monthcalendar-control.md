---
title: Sélectionner une plage de dates dans le contrôle MonthCalendar
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- dates [Windows Forms], selecting range in calendar controls
- examples [Windows Forms], calendar controls
- calendars [Windows Forms], selecting date range
- MonthCalendar control [Windows Forms], selecting date range
ms.assetid: 95d9ab95-b0f8-4c19-9f63-b5cd4593a5d0
ms.openlocfilehash: bda96af21a8f86a54d5c0fe0204546b980076d26
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76732898"
---
# <a name="how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control"></a>Comment : sélectionner une plage de dates dans le contrôle MonthCalendar Windows Forms
Une fonctionnalité importante du contrôle Windows Forms <xref:System.Windows.Forms.MonthCalendar> est que l’utilisateur peut sélectionner une plage de dates. Cette fonctionnalité est une amélioration par rapport à la fonctionnalité de sélection de dates du contrôle <xref:System.Windows.Forms.DateTimePicker>, qui permet uniquement à l’utilisateur de sélectionner une seule valeur de date/heure. Vous pouvez définir une plage de dates ou obtenir une plage de sélection définie par l’utilisateur à l’aide des propriétés du contrôle <xref:System.Windows.Forms.MonthCalendar>. L’exemple de code suivant montre comment définir une plage de sélection.  
  
### <a name="to-select-a-range-of-dates"></a>Pour sélectionner une plage de dates  
  
1. Créez <xref:System.DateTime> objets qui représentent la première et la dernière date d’une plage.  
  
    ```vb  
    Dim projectStart As Date = New DateTime(2001, 2, 13)  
    Dim projectEnd As Date = New DateTime(2001, 2, 28)  
    ```  
  
    ```csharp  
    DateTime projectStart = new DateTime(2001, 2, 13);  
    DateTime projectEnd = new DateTime(2001, 2, 28);  
    ```  
  
    ```cpp  
    DateTime projectStart = DateTime(2001, 2, 13);  
    DateTime projectEnd = DateTime(2001, 2, 28);  
    ```  
  
2. définir la propriété <xref:System.Windows.Forms.MonthCalendar.SelectionRange%2A> ;  
  
    ```vb  
    MonthCalendar1.SelectionRange = New SelectionRange(projectStart, projectEnd)  
    ```  
  
    ```csharp  
    monthCalendar1.SelectionRange = new SelectionRange(projectStart, projectEnd);  
    ```  
  
    ```cpp  
    monthCalendar1->SelectionRange = gcnew  
       SelectionRange(projectStart, projectEnd);  
    ```  
  
     \- ou -  
  
     Définissez les propriétés <xref:System.Windows.Forms.MonthCalendar.SelectionStart%2A> et <xref:System.Windows.Forms.MonthCalendar.SelectionEnd%2A>.  
  
    ```vb  
    MonthCalendar1.SelectionStart = projectStart  
    MonthCalendar1.SelectionEnd = projectEnd  
    ```  
  
    ```csharp  
    monthCalendar1.SelectionStart = projectStart;  
    monthCalendar1.SelectionEnd = projectEnd;  
    ```  
  
    ```cpp  
    monthCalendar1->SelectionStart = projectStart;  
    monthCalendar1->SelectionEnd = projectEnd;  
    ```  
  
## <a name="see-also"></a>Voir aussi

- [MonthCalendar, contrôle](monthcalendar-control-windows-forms.md)
- [Guide pratique pour modifier l'apparence du contrôle MonthCalendar Windows Forms](how-to-change-monthcalendar-control-appearance.md)
- [Guide pratique pour afficher en gras certains jours à l'aide du contrôle MonthCalendar Windows Forms](display-specific-days-in-bold-with-wf-monthcalendar-control.md)
- [Guide pratique pour afficher plusieurs mois dans le contrôle MonthCalendar Windows Forms](display-more-than-one-month-wf-monthcalendar-control.md)
