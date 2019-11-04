---
title: DatePicker
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], DatePicker
- DatePicker control [WPF]
ms.assetid: 619765c8-8d25-4315-aec2-79aea08fed9f
ms.openlocfilehash: 3e66b2306c11c54db14eb05cc6860257635cc653
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460358"
---
# <a name="datepicker"></a>DatePicker
Le contrôle <xref:System.Windows.Controls.DatePicker> permet à l’utilisateur de sélectionner une date en la tapant dans un champ de texte ou en utilisant une liste déroulante <xref:System.Windows.Controls.Calendar> contrôle.  
  
 L’illustration suivante montre une <xref:System.Windows.Controls.DatePicker>.  
  
 ![Contrôle DatePicker](./media/ndp-datepicker.png "NDP_DatePicker")  
Contrôle DatePicker  
  
 La plupart des propriétés d’un contrôle <xref:System.Windows.Controls.DatePicker> sont pour gérer ses <xref:System.Windows.Controls.Calendar>intégrés et fonctionnent de la même façon que la propriété équivalente dans <xref:System.Windows.Controls.Calendar>. En particulier, les propriétés <xref:System.Windows.Controls.DatePicker.IsTodayHighlighted%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.FirstDayOfWeek%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.BlackoutDates%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.DisplayDateStart%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.DisplayDateEnd%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.DisplayDate%2A?displayProperty=nameWithType>et <xref:System.Windows.Controls.DatePicker.SelectedDate%2A?displayProperty=nameWithType> fonctionnent de la même façon que leurs équivalents <xref:System.Windows.Controls.Calendar>. Pour plus d'informations, consultez <xref:System.Windows.Controls.Calendar>.  
  
 Les utilisateurs peuvent taper une date directement dans un champ de texte, qui définit la propriété <xref:System.Windows.Controls.DatePicker.Text%2A>. Si la <xref:System.Windows.Controls.DatePicker> ne peut pas convertir la chaîne entrée en une date valide, l’événement <xref:System.Windows.Controls.DatePicker.DateValidationError> est déclenché. Par défaut, cela provoque une exception, mais un gestionnaire d’événements pour <xref:System.Windows.Controls.DatePicker.DateValidationError> peut affecter à la propriété <xref:System.Windows.Controls.DatePickerDateValidationErrorEventArgs.ThrowException%2A> la valeur `false` et empêcher la levée d’une exception.  
  
## <a name="see-also"></a>Voir aussi

- [Contrôles](index.md)
- [Application d’un style et création de modèles](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
