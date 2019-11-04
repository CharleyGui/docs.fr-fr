---
title: Calendrier
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], Calendar
- Calendar control [WPF]
ms.assetid: ee844e4a-eefe-48e2-bd0d-1d82cc5e960b
ms.openlocfilehash: e99a716e7ca8f7b2c9ed11543f37e0b8cb7422a6
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460811"
---
# <a name="calendar"></a>Calendrier
Un calendrier permet à un utilisateur de sélectionner une date à l’aide d’un affichage de calendrier visuel.  
  
 Un contrôle <xref:System.Windows.Controls.Calendar> peut être utilisé seul ou en tant que partie déroulante d’un contrôle <xref:System.Windows.Controls.DatePicker>. Pour plus d'informations, consultez <xref:System.Windows.Controls.DatePicker>.  
  
 L’illustration suivante montre deux contrôles <xref:System.Windows.Controls.Calendar>, l’un avec les sélections et les dates d’indisponibilité, et l’autre sans.  
  
 ![Contrôles Calendar](./media/ndp-calendarcontrols.png "NDP_CalendarControls")  
Contrôles Calendar  
  
 Le tableau suivant fournit des informations sur les tâches qui sont généralement associées au <xref:System.Windows.Controls.Calendar>.  
  
|Tâche|Implémentation|  
|----------|--------------------|  
|Spécifiez les dates qui ne peuvent pas être sélectionnées.|Utilisez la propriété <xref:System.Windows.Controls.Calendar.BlackoutDates%2A>.|  
|Affichez le <xref:System.Windows.Controls.Calendar> un mois, une année entière ou une décennie.|Définissez la propriété <xref:System.Windows.Controls.Calendar.DisplayMode%2A> sur mois, année ou décennie.|  
|Spécifiez si l’utilisateur peut sélectionner une date, une plage de dates ou plusieurs plages de dates.|Utilisez l' <xref:System.Windows.Controls.Calendar.SelectionMode%2A>.|  
|Spécifiez la plage de dates que le <xref:System.Windows.Controls.Calendar> affiche.|Utilisez les propriétés <xref:System.Windows.Controls.Calendar.DisplayDateStart%2A> et <xref:System.Windows.Controls.Calendar.DisplayDateEnd%2A>.|  
|Spécifiez si la date actuelle est mise en surbrillance.|Utilisez la propriété <xref:System.Windows.Controls.Calendar.IsTodayHighlighted%2A>. Par défaut, <xref:System.Windows.Controls.Calendar.IsTodayHighlighted%2A> est `true`.|  
|Modifiez la taille de la <xref:System.Windows.Controls.Calendar>.|Utilisez un <xref:System.Windows.Controls.Viewbox> ou affectez à la propriété <xref:System.Windows.FrameworkElement.LayoutTransform%2A> la valeur d’un <xref:System.Windows.Media.ScaleTransform>. Notez que si vous définissez les propriétés <xref:System.Windows.FrameworkElement.Width%2A> et <xref:System.Windows.FrameworkElement.Height%2A> d’un <xref:System.Windows.Controls.Calendar>, le calendrier réel ne change pas sa taille.|  
  
 Le contrôle <xref:System.Windows.Controls.Calendar> fournit une navigation de base à l’aide de la souris ou du clavier. Le tableau suivant résume la navigation au clavier.  
  
|Combinaison de touches|<xref:System.Windows.Controls.Calendar.DisplayMode%2A>|Action|  
|---------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------|------------|  
|FLÈCHE|<xref:System.Windows.Controls.CalendarMode.Month>|Modifie la propriété <xref:System.Windows.Controls.Calendar.SelectedDate%2A> si la propriété <xref:System.Windows.Controls.Calendar.SelectionMode%2A> n’a pas la valeur <xref:System.Windows.Controls.CalendarSelectionMode.None>.|  
|FLÈCHE|<xref:System.Windows.Controls.CalendarMode.Year>|Modifie le mois de la propriété de <xref:System.Windows.Controls.Calendar.DisplayDate%2A>. Notez que le <xref:System.Windows.Controls.Calendar.SelectedDate%2A> ne change pas.|  
|FLÈCHE|<xref:System.Windows.Controls.CalendarMode.Decade>|Modifie l’année de la <xref:System.Windows.Controls.Calendar.DisplayDate%2A>. Notez que le <xref:System.Windows.Controls.Calendar.SelectedDate%2A> ne change pas.|  
|Maj + Flèche|<xref:System.Windows.Controls.CalendarMode.Month>|Si <xref:System.Windows.Controls.Calendar.SelectionMode%2A> n’a pas la valeur <xref:System.Windows.Controls.CalendarSelectionMode.SingleDate> ou <xref:System.Windows.Controls.CalendarSelectionMode.None>, étend la plage de dates sélectionnées.|  
|ORIGINE|<xref:System.Windows.Controls.CalendarMode.Month>|Remplace le <xref:System.Windows.Controls.Calendar.SelectedDate%2A> par le premier jour du mois en cours.|  
|ORIGINE|<xref:System.Windows.Controls.CalendarMode.Year>|Modifie le mois de la <xref:System.Windows.Controls.Calendar.DisplayDate%2A> au premier mois de l’année. Le <xref:System.Windows.Controls.Calendar.SelectedDate%2A> ne change pas.|  
|ORIGINE|<xref:System.Windows.Controls.CalendarMode.Decade>|Modifie l’année de la <xref:System.Windows.Controls.Calendar.DisplayDate%2A> à la première année de la décennie. Le <xref:System.Windows.Controls.Calendar.SelectedDate%2A> ne change pas.|  
|FIN|<xref:System.Windows.Controls.CalendarMode.Month>|Remplace le <xref:System.Windows.Controls.Calendar.SelectedDate%2A> par le dernier jour du mois en cours.|  
|FIN|<xref:System.Windows.Controls.CalendarMode.Year>|Modifie le mois de la <xref:System.Windows.Controls.Calendar.DisplayDate%2A> au dernier mois de l’année. Le <xref:System.Windows.Controls.Calendar.SelectedDate%2A> ne change pas.|  
|FIN|<xref:System.Windows.Controls.CalendarMode.Decade>|Modifie l’année de la <xref:System.Windows.Controls.Calendar.DisplayDate%2A> à la dernière année de la décennie. Le <xref:System.Windows.Controls.Calendar.SelectedDate%2A> ne change pas.|  
|CTRL+HAUT|Any|Bascule vers la <xref:System.Windows.Controls.Calendar.DisplayMode%2A>supérieure suivante. Si <xref:System.Windows.Controls.Calendar.DisplayMode%2A> est déjà <xref:System.Windows.Controls.CalendarMode.Decade>, aucune action n’est effectuée.|  
|CTRL+BAS|Any|Bascule vers la <xref:System.Windows.Controls.Calendar.DisplayMode%2A>inférieure suivante. Si <xref:System.Windows.Controls.Calendar.DisplayMode%2A> est déjà <xref:System.Windows.Controls.CalendarMode.Month>, aucune action n’est effectuée.|  
|BARRE d’espace ou entrée|<xref:System.Windows.Controls.CalendarMode.Year> ou <xref:System.Windows.Controls.CalendarMode.Decade>|Bascule <xref:System.Windows.Controls.Calendar.DisplayMode%2A> vers le <xref:System.Windows.Controls.CalendarMode.Month> ou le <xref:System.Windows.Controls.CalendarMode.Year> représenté par l’élément ayant le focus.|  
  
## <a name="see-also"></a>Voir aussi

- [Contrôles](index.md)
- [Application d’un style et création de modèles](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
