---
title: Afficher des jours spécifiques en gras avec le contrôle MonthCalendar
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- calendars [Windows Forms], displaying dates in bold
- examples [Windows Forms], calendar controls
- GetDayBold event
- MonthCalendar control [Windows Forms], dates displayed in bold
ms.assetid: 8b20db5b-8118-4825-90e8-2c45c186ac7d
ms.openlocfilehash: 377eb76f562fff20aae2136ddb7130516d2d76f7
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745882"
---
# <a name="how-to-display-specific-days-in-bold-with-the-windows-forms-monthcalendar-control"></a>Comment : afficher en gras certains jours à l'aide du contrôle MonthCalendar Windows Forms
Le contrôle Windows Forms <xref:System.Windows.Forms.MonthCalendar> peut afficher des jours en gras, soit en tant que dates singulières, soit sur une base répétée. Vous pouvez effectuer cette opération pour attirer l’attention sur des dates spéciales, telles que les vacances et les week-ends.  
  
 Trois propriétés contrôlent cette fonctionnalité. La propriété <xref:System.Windows.Forms.MonthCalendar.BoldedDates%2A> contient des dates uniques. La propriété <xref:System.Windows.Forms.MonthCalendar.AnnuallyBoldedDates%2A> contient des dates qui s’affichent en gras chaque année. La propriété <xref:System.Windows.Forms.MonthCalendar.MonthlyBoldedDates%2A> contient des dates qui s’affichent en gras chaque mois. Chacune de ces propriétés contient un tableau d’objets <xref:System.DateTime>. Pour ajouter ou supprimer une date de l’une de ces listes, vous devez ajouter ou supprimer un objet <xref:System.DateTime>.  
  
### <a name="to-make-a-date-appear-in-bold-type"></a>Pour faire apparaître une date en gras  
  
1. Créez les objets <xref:System.DateTime>.  
  
    ```vb  
    Dim myVacation1 As Date = New DateTime(2001, 6, 10)  
    Dim myVacation2 As Date = New DateTime(2001, 6, 17)  
    ```  
  
    ```csharp  
    DateTime myVacation1 = new DateTime(2001, 6, 10);  
    DateTime myVacation2 = new DateTime(2001, 6, 17);  
    ```  
  
    ```cpp  
    DateTime myVacation1 = DateTime(2001, 6, 10);  
    DateTime myVacation2 = DateTime(2001, 6, 17);  
    ```  
  
2. Faites apparaître une seule date en gras en appelant la méthode <xref:System.Windows.Forms.MonthCalendar.AddBoldedDate%2A>, <xref:System.Windows.Forms.MonthCalendar.AddAnnuallyBoldedDate%2A>ou <xref:System.Windows.Forms.MonthCalendar.AddMonthlyBoldedDate%2A> du contrôle <xref:System.Windows.Forms.MonthCalendar>.  
  
    ```vb  
    MonthCalendar1.AddBoldedDate(myVacation1)  
    MonthCalendar1.AddBoldedDate(myVacation2)  
    ```  
  
    ```csharp  
    monthCalendar1.AddBoldedDate(myVacation1);  
    monthCalendar1.AddBoldedDate(myVacation2);  
    ```  
  
    ```cpp  
    monthCalendar1->AddBoldedDate(myVacation1);  
    monthCalendar1->AddBoldedDate(myVacation2);  
    ```  
  
     \- ou -  
  
     Créez un ensemble de dates en gras en créant un tableau d’objets <xref:System.DateTime> et en l’assignant à l’une des propriétés.  
  
    ```vb  
    Dim VacationDates As DateTime() = {myVacation1, myVacation2}  
    MonthCalendar1.BoldedDates = VacationDates  
    ```  
  
    ```csharp  
    DateTime[] VacationDates = {myVacation1, myVacation2};  
    monthCalendar1.BoldedDates = VacationDates;  
    ```  
  
    ```cpp  
    Array<DateTime>^ VacationDates = {myVacation1, myVacation2};  
    monthCalendar1->BoldedDates = VacationDates;  
    ```  
  
### <a name="to-make-a-date-appear-in-the-regular-font"></a>Pour faire apparaître une date dans la police normale  
  
1. Faites apparaître une date en gras unique dans la police normale en appelant la méthode <xref:System.Windows.Forms.MonthCalendar.RemoveBoldedDate%2A>, <xref:System.Windows.Forms.MonthCalendar.RemoveAnnuallyBoldedDate%2A>ou <xref:System.Windows.Forms.MonthCalendar.RemoveMonthlyBoldedDate%2A>.  
  
    ```vb  
    MonthCalendar1.RemoveBoldedDate(myVacation1)  
    MonthCalendar1.RemoveBoldedDate(myVacation2)  
    ```  
  
    ```csharp  
    monthCalendar1.RemoveBoldedDate(myVacation1);  
    monthCalendar1.RemoveBoldedDate(myVacation2);  
    ```  
  
    ```cpp  
    monthCalendar1->RemoveBoldedDate(myVacation1);  
    monthCalendar1->RemoveBoldedDate(myVacation2);  
    ```  
  
     \- ou -  
  
     Supprimez toutes les dates en gras de l’une des trois listes en appelant la méthode <xref:System.Windows.Forms.MonthCalendar.RemoveAllBoldedDates%2A>, <xref:System.Windows.Forms.MonthCalendar.RemoveAllAnnuallyBoldedDates%2A>ou <xref:System.Windows.Forms.MonthCalendar.RemoveAllMonthlyBoldedDates%2A>.  
  
    ```vb  
    MonthCalendar1.RemoveAllBoldedDates()  
    ```  
  
    ```csharp  
    monthCalendar1.RemoveAllBoldedDates();  
    ```  
  
    ```cpp  
    monthCalendar1->RemoveAllBoldedDates();  
    ```  
  
2. Mettez à jour l’apparence de la police en appelant la méthode <xref:System.Windows.Forms.MonthCalendar.UpdateBoldedDates%2A>.  
  
    ```vb  
    MonthCalendar1.UpdateBoldedDates()  
    ```  
  
    ```csharp  
    monthCalendar1.UpdateBoldedDates();  
    ```  
  
    ```cpp  
    monthCalendar1->UpdateBoldedDates();  
    ```  
  
## <a name="see-also"></a>Voir aussi

- [MonthCalendar, contrôle](monthcalendar-control-windows-forms.md)
- [Guide pratique pour sélectionner une plage de dates dans le contrôle MonthCalendar Windows Forms](how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control.md)
- [Guide pratique pour modifier l'apparence du contrôle MonthCalendar Windows Forms](how-to-change-monthcalendar-control-appearance.md)
- [Guide pratique pour afficher plusieurs mois dans le contrôle MonthCalendar Windows Forms](display-more-than-one-month-wf-monthcalendar-control.md)
