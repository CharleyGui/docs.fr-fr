---
title: Styles et modèles DatePicker
ms.date: 03/30/2017
helpviewer_keywords:
- ControlTemplate [WPF], DatePicker
- DatePicker [WPF], styles and templates
- templates [WPF], DatePicker
- parts [WPF], DatePicker
- styles [WPF], DatePicker
- states [WPF], DatePicker
ms.assetid: c430a657-692f-44bd-a549-2341f92d6115
ms.openlocfilehash: 002d1c3271827239dcd3a319621f66fb5bc68d4e
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283774"
---
# <a name="datepicker-styles-and-templates"></a>Styles et modèles DatePicker
Cette rubrique décrit les styles et les modèles du contrôle <xref:System.Windows.Controls.DatePicker>. Vous pouvez modifier le <xref:System.Windows.Controls.ControlTemplate> par défaut pour attribuer une apparence unique au contrôle. Pour plus d’informations, consultez [créer un modèle pour un contrôle](../../../desktop-wpf/themes/how-to-create-apply-template.md).  
  
## <a name="datepicker-parts"></a>Composants DatePicker  
 Le tableau suivant répertorie les parties nommées du contrôle <xref:System.Windows.Controls.DatePicker>.  
  
|Élément|Type|Description|  
|-|-|-|  
|PART_Root|<xref:System.Windows.Controls.Grid>|Racine du contrôle.|  
|PART_Button|<xref:System.Windows.Controls.Button>|Bouton qui ouvre et ferme le <xref:System.Windows.Controls.Calendar>.|  
|PART_TextBox|<xref:System.Windows.Controls.Primitives.DatePickerTextBox>|Zone de texte qui vous permet d’entrer une date.|  
|PART_Popup|<xref:System.Windows.Controls.Primitives.Popup>|Popup pour le contrôle de <xref:System.Windows.Controls.DatePicker>.|  
  
## <a name="datepicker-states"></a>États DatePicker  
 Le tableau suivant répertorie les États visuels du contrôle <xref:System.Windows.Controls.DatePicker>.  
  
|Nom VisualState|Nom VisualStateGroup|Description|  
|-|-|-|  
|Normal|CommonStates|État par défaut.|  
|Désactivé|CommonStates|Le <xref:System.Windows.Controls.DatePicker> est désactivé.|  
|Valide|ValidationStates|Le contrôle utilise la classe <xref:System.Windows.Controls.Validation> et la propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `false`.|  
|InvalidFocused|ValidationStates|La propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `true` a le focus.|  
|InvalidUnfocused|ValidationStates|La propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `true` a le contrôle n’a pas le focus.|  
  
## <a name="datepickertextbox-parts"></a>Composants DatePickerTextBox  
 Le tableau suivant répertorie les parties nommées du contrôle <xref:System.Windows.Controls.Primitives.DatePickerTextBox>.  
  
|Élément|Type|Description|  
|-|-|-|  
|PART_Watermark|<xref:System.Windows.Controls.ContentControl>|Élément qui contient le texte initial dans le <xref:System.Windows.Controls.DatePicker>.|  
|PART_ContentElement|<xref:System.Windows.FrameworkElement>|Élément visuel qui peut contenir un <xref:System.Windows.FrameworkElement>. Le texte de la <xref:System.Windows.Controls.TextBox> s’affiche dans cet élément.|  
  
## <a name="datepickertextbox-states"></a>États DatePickerTextBox  
 Le tableau suivant répertorie les États visuels du contrôle <xref:System.Windows.Controls.Primitives.DatePickerTextBox>.  
  
|Nom VisualState|Nom VisualStateGroup|Description|  
|-|-|-|  
|Normal|CommonStates|État par défaut.|  
|Désactivé|CommonStates|Le <xref:System.Windows.Controls.Primitives.DatePickerTextBox> est désactivé.|  
|MouseOver|CommonStates|Le pointeur de la souris est positionné sur le <xref:System.Windows.Controls.Primitives.DatePickerTextBox>.|  
|ReadOnly|CommonStates|L’utilisateur ne peut pas modifier le texte dans la <xref:System.Windows.Controls.Primitives.DatePickerTextBox>.|  
|Avec focus|FocusStates|Le contrôle a le focus.|  
|Sans focus|FocusStates|Le contrôle n’a pas le focus.|  
|Filigrane|WatermarkStates|Le contrôle affiche son texte initial.  La <xref:System.Windows.Controls.Primitives.DatePickerTextBox> est dans l’État lorsque l’utilisateur n’a pas entré de texte ou sélectionné une date.|  
|Pas de filigrane|WatermarkStates|L’utilisateur a entré du texte dans le <xref:System.Windows.Controls.Primitives.DatePickerTextBox> ou sélectionné une date dans le <xref:System.Windows.Controls.DatePicker>.|  
|Valide|ValidationStates|Le contrôle utilise la classe <xref:System.Windows.Controls.Validation> et la propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `false`.|  
|InvalidFocused|ValidationStates|La propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `true` et le contrôle a le focus.|  
|InvalidUnfocused|ValidationStates|La <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété jointe est `true` et le contrôle n’a pas le focus.|  
  
## <a name="datepicker-controltemplate-example"></a>DatePicker ControlTemplate, exemple  
 L’exemple suivant montre comment définir une <xref:System.Windows.Controls.ControlTemplate> pour le contrôle <xref:System.Windows.Controls.DatePicker>.  
  
 [!code-xaml[ControlTemplateExamples#DatePicker](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/datepicker.xaml#datepicker)]  
  
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
