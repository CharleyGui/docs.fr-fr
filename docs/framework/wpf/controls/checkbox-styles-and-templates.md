---
title: Styles et modèles CheckBox
ms.date: 03/30/2017
helpviewer_keywords:
- states [WPF], CheckBox
- templates [WPF], CheckBox
- parts [WPF], CheckBox
- ControlTemplate [WPF], CheckBox
- CheckBox [WPF], styles and templates
- styles [WPF], CheckBox
ms.assetid: bfdaec96-d101-4d3d-864d-c27e6b621d03
ms.openlocfilehash: b9eee48c01f53e12bbe4a72f84c20eab68d5de23
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283818"
---
# <a name="checkbox-styles-and-templates"></a>Styles et modèles CheckBox
Cette rubrique décrit les styles et les modèles du contrôle <xref:System.Windows.Controls.CheckBox>. Vous pouvez modifier le <xref:System.Windows.Controls.ControlTemplate> par défaut pour attribuer une apparence unique au contrôle. Pour plus d’informations, consultez [créer un modèle pour un contrôle](../../../desktop-wpf/themes/how-to-create-apply-template.md).  
  
## <a name="checkbox-parts"></a>Parties de cases à cocher  
 Le contrôle <xref:System.Windows.Controls.CheckBox> n’a pas de parties nommées.  
  
## <a name="checkbox-states"></a>États des cases à cocher  
 Le tableau suivant répertorie les États visuels du contrôle <xref:System.Windows.Controls.CheckBox>.  
  
|Nom VisualState|Nom VisualStateGroup|Description|  
|----------------------|---------------------------|-----------------|  
|Normale|CommonStates|État par défaut.|  
|MouseOver|CommonStates|Le pointeur de souris est positionné sur le contrôle.|  
|Appuyé|CommonStates|Le contrôle est enfoncé.|  
|Désactivé|CommonStates|Le contrôle est désactivé.|  
|Avec focus|FocusStates|Le contrôle a le focus.|  
|Sans focus|FocusStates|Le contrôle n’a pas le focus.|  
|Activé|CheckStates|<xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> est `true`.|  
|Désactivée|CheckStates|<xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> est `false`.|  
|Déterminée|CheckStates|<xref:System.Windows.Controls.Primitives.ToggleButton.IsThreeState%2A> est `true`et <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> est `null`.|  
|Valide|ValidationStates|Le contrôle utilise la classe <xref:System.Windows.Controls.Validation> et la propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `false`.|  
|InvalidUnfocused|ValidationStates|La propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `true` a le focus.|  
|InvalidFocused|ValidationStates|La propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `true` a le contrôle n’a pas le focus.|  
  
## <a name="checkbox-controltemplate-example"></a>CheckBox, exemple de ControlTemplate  
 L’exemple suivant montre comment définir une <xref:System.Windows.Controls.ControlTemplate> pour le contrôle <xref:System.Windows.Controls.CheckBox>.  
  
 [!code-xaml[ControlTemplateExamples#CheckBox](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/checkbox.xaml#checkbox)]  
  
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
