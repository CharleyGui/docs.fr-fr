---
title: Afficher plus d’un mois dans le contrôle MonthCalendar
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- calendars [Windows Forms], formatting display
- examples [Windows Forms], calendar controls
- calendars [Windows Forms], multiple months
- MonthCalendar control [Windows Forms], formatting display
ms.assetid: d197caa2-38a5-4cb4-acc3-562130c2ace3
ms.openlocfilehash: 5d3925bc19ddcd67742f0ab8b5b2e45530820f38
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745901"
---
# <a name="how-to-display-more-than-one-month-in-the-windows-forms-monthcalendar-control"></a>Comment : afficher plusieurs mois dans le contrôle MonthCalendar Windows Forms
Le contrôle Windows Forms <xref:System.Windows.Forms.MonthCalendar> peut afficher jusqu’à 12 mois à la fois. Par défaut, le contrôle affiche un seul mois, mais vous pouvez spécifier le nombre de mois affichés et la façon dont ils sont organisés dans le contrôle. Lorsque vous modifiez les dimensions du calendrier, le contrôle est redimensionné. Assurez-vous qu’il y a suffisamment d’espace sur le formulaire pour les nouvelles dimensions.  
  
### <a name="to-display-multiple-months"></a>Pour afficher plusieurs mois  
  
- Définissez la propriété <xref:System.Windows.Forms.MonthCalendar.CalendarDimensions%2A> sur le nombre de mois à afficher horizontalement et verticalement.  
  
    ```vb  
    MonthCalendar1.CalendarDimensions = New System.Drawing.Size (3,2)  
    ```  
  
    ```csharp  
    monthCalendar1.CalendarDimensions = new System.Drawing.Size (3,2);  
    ```  
  
    ```cpp  
    monthCalendar1->CalendarDimensions = System::Drawing::Size (3,2);  
    ```  
  
## <a name="see-also"></a>Voir aussi

- [MonthCalendar, contrôle](monthcalendar-control-windows-forms.md)
- [Guide pratique pour sélectionner une plage de dates dans le contrôle MonthCalendar Windows Forms](how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control.md)
- [Guide pratique pour modifier l'apparence du contrôle MonthCalendar Windows Forms](how-to-change-monthcalendar-control-appearance.md)
