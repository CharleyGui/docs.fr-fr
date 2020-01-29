---
title: Vue d'ensemble du contrôle MonthCalendar
ms.date: 03/30/2017
f1_keywords:
- MonthCalendar
helpviewer_keywords:
- calendars [Windows Forms], Windows Forms controls
- calendar controls [Windows Forms], Windows Forms
- MonthCalendar control [Windows Forms], setting the first day of the week
ms.assetid: 788c5325-b721-44ec-95bf-9b680ba0f6a2
ms.openlocfilehash: a9b56164339d03b380a564b21855f6d94ec06af5
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76734942"
---
# <a name="monthcalendar-control-overview-windows-forms"></a>Vue d'ensemble du contrôle MonthCalendar (Windows Forms)
Le contrôle Windows Forms <xref:System.Windows.Forms.MonthCalendar> présente une interface graphique intuitive permettant aux utilisateurs d’afficher et de définir des informations de date. Le contrôle affiche un calendrier : une grille contenant les jours numérotés du mois, organisés en colonnes sous les jours de la semaine, la plage de dates sélectionnée étant mise en surbrillance. Vous pouvez sélectionner un autre mois en cliquant sur les flèches situées de chaque côté de la légende du mois. Contrairement au contrôle <xref:System.Windows.Forms.DateTimePicker> similaire, vous pouvez sélectionner plusieurs dates avec ce contrôle. Pour plus d’informations sur le contrôle <xref:System.Windows.Forms.DateTimePicker>, consultez [DateTimePicker, contrôle](datetimepicker-control-windows-forms.md).  
  
## <a name="configuring-the-monthcalendar-control"></a>Configuration du contrôle MonthCalendar  
 L’apparence du contrôle de <xref:System.Windows.Forms.MonthCalendar> est hautement configurable. Par défaut, la date du jour est affichée sous la forme d’un cercle et est également notée en bas de la grille. Vous pouvez modifier cette fonctionnalité en définissant les propriétés <xref:System.Windows.Forms.MonthCalendar.ShowToday%2A> et <xref:System.Windows.Forms.MonthCalendar.ShowTodayCircle%2A> sur `false`. Vous pouvez également ajouter des numéros de semaine au calendrier en affectant à la propriété <xref:System.Windows.Forms.MonthCalendar.ShowWeekNumbers%2A> la valeur `true`. En définissant la propriété <xref:System.Windows.Forms.MonthCalendar.CalendarDimensions%2A>, vous pouvez afficher plusieurs mois horizontalement et verticalement. Par défaut, le dimanche est affiché comme premier jour de la semaine, mais n’importe quel jour peut être désigné à l’aide de la propriété <xref:System.Windows.Forms.MonthCalendar.FirstDayOfWeek%2A>.  
  
 Vous pouvez également définir des dates à afficher en gras sur une base ponctuelle, annuelle ou mensuelle, en ajoutant des objets <xref:System.DateTime> aux propriétés <xref:System.Windows.Forms.MonthCalendar.BoldedDates%2A>, <xref:System.Windows.Forms.MonthCalendar.AnnuallyBoldedDates%2A>et <xref:System.Windows.Forms.MonthCalendar.MonthlyBoldedDates%2A>. Pour plus d’informations, consultez [Comment : afficher des jours spécifiques en gras avec le contrôle Windows Forms MonthCalendar](display-specific-days-in-bold-with-wf-monthcalendar-control.md).  
  
 La propriété de clé du contrôle <xref:System.Windows.Forms.MonthCalendar> est <xref:System.Windows.Forms.MonthCalendar.SelectionRange%2A>, la plage de dates sélectionnée dans le contrôle. La valeur de <xref:System.Windows.Forms.MonthCalendar.SelectionRange%2A> ne peut pas dépasser le nombre maximal de jours pouvant être sélectionnés, défini dans la propriété <xref:System.Windows.Forms.MonthCalendar.MaxSelectionCount%2A>. Les dates les plus anciennes et les plus récentes que l’utilisateur peut sélectionner sont déterminées par les propriétés <xref:System.Windows.Forms.MonthCalendar.MaxDate%2A> et <xref:System.Windows.Forms.MonthCalendar.MinDate%2A>.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.MonthCalendar>
- [MonthCalendar, contrôle](monthcalendar-control-windows-forms.md)
