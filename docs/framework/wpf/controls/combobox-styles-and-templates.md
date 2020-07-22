---
title: Styles et modèles ComboBox
ms.date: 03/30/2017
helpviewer_keywords:
- ComboBox [WPF], styles and templates
- states [WPF], ComboBox
- ControlTemplate [WPF], ComboBox
- styles [WPF], ComboBox
- templates [WPF], ComboBox
- parts [WPF], ComboBox
ms.assetid: b0662fa1-16d7-4320-b26b-c1804e565a44
ms.openlocfilehash: af7f8a544af5e9892a8f3f059048bbfd113d2491
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2020
ms.locfileid: "86865357"
---
# <a name="combobox-styles-and-templates"></a>Styles et modèles ComboBox
Cette rubrique décrit les styles et les modèles pour le <xref:System.Windows.Controls.ComboBox> contrôle. Vous pouvez modifier la valeur par défaut <xref:System.Windows.Controls.ControlTemplate> pour que le contrôle donne une apparence unique. Pour plus d’informations, consultez [créer un modèle pour un contrôle](../../../desktop-wpf/themes/how-to-create-apply-template.md).  
  
## <a name="combobox-parts"></a>Composants ComboBox  
 Le tableau suivant répertorie les parties nommées du <xref:System.Windows.Controls.ComboBox> contrôle.  
  
|Élément|Type|Description|  
|-|-|-|  
|PART_EditableTextBox|<xref:System.Windows.Controls.TextBox>|Contient le texte de <xref:System.Windows.Controls.ComboBox> .|  
|PART_Popup|<xref:System.Windows.Controls.Primitives.Popup>|Liste déroulante qui contient les éléments de la zone de liste déroulante.|  
  
 Lorsque vous créez un <xref:System.Windows.Controls.ControlTemplate> pour un <xref:System.Windows.Controls.ComboBox> , votre modèle peut contenir un <xref:System.Windows.Controls.ItemsPresenter> dans un <xref:System.Windows.Controls.ScrollViewer> . (Le <xref:System.Windows.Controls.ItemsPresenter> affiche chaque élément dans <xref:System.Windows.Controls.ComboBox> ; le <xref:System.Windows.Controls.ScrollViewer> permet de faire défiler le contrôle).  Si le <xref:System.Windows.Controls.ItemsPresenter> n’est pas l’enfant direct de <xref:System.Windows.Controls.ScrollViewer> , vous devez fournir le <xref:System.Windows.Controls.ItemsPresenter> nom, `ItemsPresenter` .  
  
## <a name="combobox-states"></a>États de ComboBox  
 Le tableau suivant répertorie les États du <xref:System.Windows.Controls.ComboBox> contrôle.  
  
|Nom VisualState|Nom VisualStateGroup|Description|  
|-|-|-|  
|Normal|CommonStates|État par défaut.|  
|Désactivé|CommonStates|Le contrôle est désactivé.|  
|MouseOver|CommonStates|Le pointeur de la souris se trouve sur le <xref:System.Windows.Controls.ComboBox> contrôle.|  
|Avec focus|FocusStates|Le contrôle a le focus.|  
|Sans focus|FocusStates|Le contrôle n’a pas le focus.|  
|FocusedDropDown|FocusStates|La liste déroulante de <xref:System.Windows.Controls.ComboBox> a le focus.|  
|Valide|ValidationStates|Le contrôle utilise la <xref:System.Windows.Controls.Validation> classe et la <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété jointe est `false` .|  
|InvalidFocused|ValidationStates|La <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété jointe est `true` et le contrôle a le focus.|  
|InvalidUnfocused|ValidationStates|La <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété jointe est `true` et le contrôle n’a pas le focus.|  
|Modifiable|EditStates|La propriété <xref:System.Windows.Controls.ComboBox.IsEditable%2A> a la valeur `true`.|  
|Alors impossibles|EditStates|La propriété <xref:System.Windows.Controls.ComboBox.IsEditable%2A> a la valeur `false`.|  
  
## <a name="comboboxitem-parts"></a>Composants de ComboBoxItem  
 Le <xref:System.Windows.Controls.ComboBoxItem> contrôle n’a pas de parties nommées.  
  
## <a name="comboboxitem-states"></a>États de ComboBoxItem  
 Le tableau suivant répertorie les États du <xref:System.Windows.Controls.ComboBoxItem> contrôle.  
  
|Nom VisualState|Nom VisualStateGroup|Description|  
|-|-|-|  
|Normal|CommonStates|État par défaut.|  
|Désactivé|CommonStates|Le contrôle est désactivé.|  
|MouseOver|CommonStates|Le pointeur de la souris se trouve sur le <xref:System.Windows.Controls.ComboBoxItem> contrôle.|  
|Avec focus|FocusStates|Le contrôle a le focus.|  
|Sans focus|FocusStates|Le contrôle n’a pas le focus.|  
|Sélectionné|SelectionStates|L’élément est actuellement sélectionné.|  
|Non sélectionné|SelectionStates|L’élément n’est pas sélectionné.|  
|SelectedUnfocused|SelectionStates|L’élément est sélectionné mais n’a pas le focus.|  
|Valide|ValidationStates|Le contrôle utilise la <xref:System.Windows.Controls.Validation> classe et la <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété jointe est `false` .|  
|InvalidFocused|ValidationStates|La <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété jointe est `true` et le contrôle a le focus.|  
|InvalidUnfocused|ValidationStates|La <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété jointe est `true` et le contrôle n’a pas le focus.|  
  
## <a name="combobox-controltemplate-example"></a>Exemple de ControlTemplate ComboBox  
 L’exemple suivant montre comment définir un <xref:System.Windows.Controls.ControlTemplate> pour le <xref:System.Windows.Controls.ComboBox> contrôle et les types associés.  
  
 [!code-xaml[ControlTemplateExamples#ComboBox](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/combobox.xaml#combobox)]  
  
 L’exemple précédent utilise une ou plusieurs des ressources suivantes.  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 Pour voir l’exemple complet, consultez [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating) (Exemple de style avec ControlTemplates).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [Styles et modèles Control](control-styles-and-templates.md)
- [Personnalisation des contrôles](control-customization.md)
- [Application d'un style et création de modèles](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [Créer un modèle pour un contrôle](../../../desktop-wpf/themes/how-to-create-apply-template.md)
