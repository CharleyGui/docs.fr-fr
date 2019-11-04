---
title: Styles et modèles Expander
ms.date: 03/30/2017
helpviewer_keywords:
- styles [WPF], Expander
- ControlTemplate [WPF], Expander
- templates [WPF], Expander
- Expander [WPF], styles and templates
- states [WPF], Expander
- parts [WPF], Expander
ms.assetid: da2e5a1c-5230-4c21-98a5-59c7895facd7
ms.openlocfilehash: 26989474f264161be12bcc14fed614fdc7f775b6
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460332"
---
# <a name="expander-styles-and-templates"></a>Styles et modèles Expander
Cette rubrique décrit les styles et les modèles du contrôle <xref:System.Windows.Controls.Expander>. Vous pouvez modifier le <xref:System.Windows.Controls.ControlTemplate> par défaut pour attribuer une apparence unique au contrôle. Pour plus d’informations, consultez [Personnalisation de l'apparence d'un contrôle existant en créant un ControlTemplate](customizing-the-appearance-of-an-existing-control.md).  
  
## <a name="expander-parts"></a>Parties de l’Expander  
 Le contrôle <xref:System.Windows.Controls.Expander> n’a pas de parties nommées.  
  
## <a name="expander-states"></a>États de l’Expander  
 Le tableau suivant répertorie les États visuels du contrôle <xref:System.Windows.Controls.Expander>.  
  
|Nom VisualState|Nom VisualStateGroup|Description|  
|-|-|-|  
|Normale|CommonStates|État par défaut.|  
|MouseOver|CommonStates|Le pointeur de souris est positionné sur le contrôle.|  
|Disabled|CommonStates|Le contrôle est désactivé.|  
|Avec focus|FocusStates|Le contrôle a le focus.|  
|Sans focus|FocusStates|Le contrôle n’a pas le focus.|  
|Étendu|ExpansionStates|Le contrôle est développé.|  
|Collapsed|ExpansionStates|Le contrôle n’est pas développé.|  
|ExpandDown|ExpandDirectionStates|Le contrôle se développe vers le PG.|  
|ExpandUp|ExpandDirectionStates|Le contrôle s’agrandit.|  
|ExpandLeft|ExpandDirectionStates|Le contrôle se développe à gauche.|  
|ExpandRight|ExpandDirectionStates|Le contrôle se développe à droite.|  
|Valide|ValidationStates|Le contrôle utilise la classe <xref:System.Windows.Controls.Validation> et la propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `false`.|  
|InvalidFocused|ValidationStates|La propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `true` a le focus.|  
|InvalidUnfocused|ValidationStates|La propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `true` a le contrôle n’a pas le focus.|  
  
## <a name="expander-controltemplate-example"></a>Expander ControlTemplate, exemple  
 L’exemple suivant montre comment définir une <xref:System.Windows.Controls.ControlTemplate> pour le contrôle <xref:System.Windows.Controls.Expander>.  
  
 [!code-xaml[ControlTemplateExamples#Expander](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/expander.xaml#expander)]  
  
 L’exemple précédent utilise une ou plusieurs des ressources suivantes.  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 Pour voir l’exemple complet, consultez [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating) (Exemple de style avec ControlTemplates).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [Styles et modèles Control](control-styles-and-templates.md)
- [Personnalisation des contrôles](control-customization.md)
- [Application d’un style et création de modèles](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [Personnalisation de l’apparence d’un contrôle existant en créant un ControlTemplate](customizing-the-appearance-of-an-existing-control.md)
