---
title: Styles et modèles Calendar
ms.date: 03/30/2017
helpviewer_keywords:
- styles [WPF], Calendar
- templates [WPF], Calendar
- states [WPF], Calendar
- parts [WPF], Calendar
- Calendar [WPF], styles and templates
- ControlTemplate [WPF], Calendar
ms.assetid: f4fcf046-7a8f-41b8-b5a8-534b64e0345c
ms.openlocfilehash: 64cb62a3459a3eeea6aa5e91b433a58a88ab08ea
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283559"
---
# <a name="calendar-styles-and-templates"></a>Styles et modèles Calendar
Cette rubrique décrit les styles et les modèles du contrôle <xref:System.Windows.Controls.Calendar>. Vous pouvez modifier le <xref:System.Windows.Controls.ControlTemplate> par défaut pour attribuer une apparence unique au contrôle. Pour plus d’informations, consultez [créer un modèle pour un contrôle](../../../desktop-wpf/themes/how-to-create-apply-template.md).  
  
## <a name="calendar-parts"></a>Composants de calendrier  
 Le tableau suivant répertorie les parties nommées du contrôle <xref:System.Windows.Controls.Calendar>.  
  
|Élément|Type|Description|  
|-|-|-|  
|PART_CalendarItem|<xref:System.Windows.Controls.Primitives.CalendarItem>|Mois ou année actuellement affiché sur le <xref:System.Windows.Controls.Calendar>.|  
|PART_Root|<xref:System.Windows.Controls.Panel>|Panneau qui contient le <xref:System.Windows.Controls.Primitives.CalendarItem>.|  
  
## <a name="calendar-states"></a>États du calendrier  
 Le tableau suivant répertorie les États visuels du contrôle <xref:System.Windows.Controls.Calendar>.  
  
|Nom VisualState|Nom VisualStateGroup|Description|  
|----------------------|---------------------------|-----------------|  
|Valide|ValidationStates|Le contrôle utilise la classe <xref:System.Windows.Controls.Validation> et la propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `false`.|  
|InvalidFocused|ValidationStates|La propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `true` a le focus.|  
|InvalidUnfocused|ValidationStates|La propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `true` a le contrôle n’a pas le focus.|  
  
## <a name="calendaritem-parts"></a>Composants CalendarItem  
 Le tableau suivant répertorie les parties nommées du contrôle <xref:System.Windows.Controls.Primitives.CalendarItem>.  
  
|Élément|Type|Description|  
|-|-|-|  
|PART_Root|<xref:System.Windows.FrameworkElement>|Racine du contrôle.|  
|PART_PreviousButton|<xref:System.Windows.Controls.Button>|Bouton qui affiche la page précédente du calendrier quand l’utilisateur clique dessus.|  
|PART_NextButton|<xref:System.Windows.Controls.Button>|Bouton qui affiche la page suivante du calendrier quand l’utilisateur clique dessus.|  
|PART_HeaderButton|<xref:System.Windows.Controls.Button>|Bouton qui autorise le basculement entre le mode mois, le mode année et le mode décennie.|  
|PART_MonthView|<xref:System.Windows.Controls.Grid>|Héberge le contenu en mode mois.|  
|PART_YearView|<xref:System.Windows.Controls.Grid>|Héberge le contenu en mode année ou décennie.|  
|PART_DisabledVisual|<xref:System.Windows.FrameworkElement>|Superposition de l’état désactivé.|  
|DayTitleTemplate|<xref:System.Windows.DataTemplate>|<xref:System.Windows.DataTemplate> qui décrit la structure visuelle.|  
  
## <a name="calendaritem-states"></a>États CalendarItem  
 Le tableau suivant répertorie les États visuels du contrôle <xref:System.Windows.Controls.Primitives.CalendarItem>.  
  
|Nom VisualState|Nom VisualStateGroup|Description|  
|-|-|-|  
|État normal|CommonStates|État par défaut.|  
|État désactivé|CommonStates|État du calendrier lorsque la propriété <xref:System.Windows.UIElement.IsEnabled%2A> est `false`.|  
|Valide|ValidationStates|Le contrôle utilise la classe <xref:System.Windows.Controls.Validation> et la propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `false`.|  
|InvalidFocused|ValidationStates|La propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `true` a le focus.|  
|InvalidUnfocused|ValidationStates|La propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `true` a le contrôle n’a pas le focus.|  
|Valide|ValidationStates|Le contrôle utilise la classe <xref:System.Windows.Controls.Validation> et la propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `false`.|  
|InvalidFocused|ValidationStates|La propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `true` a le focus.|  
|InvalidUnfocused|ValidationStates|La propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `true` a le contrôle n’a pas le focus.|  
  
## <a name="calendardaybutton-parts"></a>Composants CalendarDayButton  
 Le contrôle <xref:System.Windows.Controls.Primitives.CalendarDayButton> n’a pas de parties nommées.  
  
## <a name="calendardaybutton-states"></a>États CalendarDayButton  
 Le tableau suivant répertorie les États visuels du contrôle <xref:System.Windows.Controls.Primitives.CalendarDayButton>.  
  
|Nom VisualState|Nom VisualStateGroup|Description|  
|-|-|-|  
|Normal|CommonStates|État par défaut.|  
|Désactivé|CommonStates|Le <xref:System.Windows.Controls.Primitives.CalendarDayButton> est désactivé.|  
|MouseOver|CommonStates|Le pointeur de la souris est positionné sur le <xref:System.Windows.Controls.Primitives.CalendarDayButton>.|  
|Appuyé|CommonStates|Le <xref:System.Windows.Controls.Primitives.CalendarDayButton> est enfoncé.|  
|Selected|SelectionStates|Le bouton est sélectionné.|  
|Non sélectionné|SelectionStates|Le bouton n’est pas sélectionné.|  
|CalendarButtonFocused|CalendarButtonFocusStates|Le bouton a le focus.|  
|CalendarButtonUnfocused|CalendarButtonFocusStates|Le bouton n’a pas le focus.|  
|Avec focus|FocusStates|Le bouton a le focus.|  
|Sans focus|FocusStates|Le bouton n’a pas le focus.|  
|Active|ActiveStates|Le bouton est actif.|  
|Inactive|ActiveStates|Le bouton est inactif.|  
|RegularDay|DayStates|Le bouton ne représente pas <xref:System.DateTime.Today%2A?displayProperty=nameWithType>.|  
|Aujourd'hui|DayStates|Le bouton représente <xref:System.DateTime.Today%2A?displayProperty=nameWithType>.|  
|NormalDay|BlackoutDayStates|Le bouton représente un jour qui peut être sélectionné.|  
|BlackoutDay|BlackoutDayStates|Le bouton représente un jour qui ne peut pas être sélectionné.|  
|Valide|ValidationStates|Le contrôle utilise la classe <xref:System.Windows.Controls.Validation> et la propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `false`.|  
|InvalidFocused|ValidationStates|La propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `true` a le focus.|  
|InvalidUnfocused|ValidationStates|La propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `true` a le contrôle n’a pas le focus.|  
  
## <a name="calendarbutton-parts"></a>Composants CalendarButton  
 Le contrôle <xref:System.Windows.Controls.Primitives.CalendarButton> n’a pas de parties nommées.  
  
## <a name="calendarbutton-states"></a>États CalendarButton  
 Le tableau suivant répertorie les États visuels du contrôle <xref:System.Windows.Controls.Primitives.CalendarButton>.  
  
|Nom VisualState|Nom VisualStateGroup|Description|  
|-|-|-|  
|Normal|CommonStates|État par défaut.|  
|Désactivé|CommonStates|Le <xref:System.Windows.Controls.Primitives.CalendarButton> est désactivé.|  
|MouseOver|CommonStates|Le pointeur de la souris est positionné sur le <xref:System.Windows.Controls.Primitives.CalendarButton>.|  
|Appuyé|CommonStates|Le <xref:System.Windows.Controls.Primitives.CalendarButton> est enfoncé.|  
|Selected|SelectionStates|Le bouton est sélectionné.|  
|Non sélectionné|SelectionStates|Le bouton n’est pas sélectionné.|  
|CalendarButtonFocused|CalendarButtonFocusStates|Le bouton a le focus.|  
|CalendarButtonUnfocused|CalendarButtonFocusStates|Le bouton n’a pas le focus.|  
|Avec focus|FocusStates|Le bouton a le focus.|  
|Sans focus|FocusStates|Le bouton n’a pas le focus.|  
|Active|ActiveStates|Le bouton est actif.|  
|Inactive|ActiveStates|Le bouton est inactif.|  
|Valide|ValidationStates|Le contrôle utilise la classe <xref:System.Windows.Controls.Validation> et la propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `false`.|  
|InvalidFocused|ValidationStates|La propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `true` a le focus.|  
|InvalidUnfocused|ValidationStates|La propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `true` a le contrôle n’a pas le focus.|  
  
## <a name="calendar-controltemplate-example"></a>Exemple de ControlTemplate Calendar  
 L’exemple suivant montre comment définir une <xref:System.Windows.Controls.ControlTemplate> pour le contrôle <xref:System.Windows.Controls.Calendar> et les types associés.  
  
 [!code-xaml[ControlTemplateExamples#Calendar](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/calendar.xaml#calendar)]  
  
 L’exemple précédent utilise une ou plusieurs des ressources suivantes.  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 Pour voir l’exemple complet, consultez [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating) (Exemple de style avec ControlTemplates).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [Styles et modèles Control](control-styles-and-templates.md)
- [Personnalisation des contrôles](control-customization.md)
- [Application d’un style et création de modèles](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [Créer un modèle pour un contrôle](../../../desktop-wpf/themes/how-to-create-apply-template.md)
