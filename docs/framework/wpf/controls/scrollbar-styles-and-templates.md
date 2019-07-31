---
title: Styles et modèles ScrollBar
ms.date: 03/30/2017
helpviewer_keywords:
- styles [WPF], ScrollBar
- ControlTemplate [WPF], ScrollBar
- states [WPF], ScrollBar
- ScrollBar [WPF], styles and templates
- templates [WPF], ScrollBar
- parts [WPF], ScrollBar
ms.assetid: 066ea45a-e27d-43b0-adfe-cce6934c22f5
ms.openlocfilehash: 016556fb825ddf60af7dc572d6fda7323b9bb09d
ms.sourcegitcommit: 3eeea78f52ca771087a6736c23f74600cc662658
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/31/2019
ms.locfileid: "68671980"
---
# <a name="scrollbar-styles-and-templates"></a>Styles et modèles ScrollBar
Cette rubrique décrit les styles et les modèles pour <xref:System.Windows.Controls.Primitives.ScrollBar> le contrôle. Vous pouvez modifier la valeur <xref:System.Windows.Controls.ControlTemplate> par défaut pour que le contrôle donne une apparence unique. Pour plus d’informations, consultez [Personnalisation de l’apparence d’un contrôle existant en créant un ControlTemplate](customizing-the-appearance-of-an-existing-control.md).  
  
## <a name="scrollbar-parts"></a>Éléments ScrollBar  
 Le tableau suivant répertorie les parties <xref:System.Windows.Controls.Primitives.ScrollBar> nommées du contrôle.  
  
|Élément|Type|Description|  
|-|-|-|  
|PART_Track|<xref:System.Windows.Controls.Primitives.Track>|Conteneur de l’élément qui indique la position du <xref:System.Windows.Controls.Primitives.ScrollBar>.|  
  
## <a name="scrollbar-states"></a>États de la barre de défilement  
 Le tableau suivant répertorie les États <xref:System.Windows.Controls.Primitives.ScrollBar> visuels du contrôle.  
  
|Nom VisualState|Nom VisualStateGroup|Description|  
|----------------------|---------------------------|-----------------|  
|Normale|CommonStates|État par défaut.|  
|MouseOver|CommonStates|Le pointeur de souris est positionné sur le contrôle.|  
|Désactivé|CommonStates|Le contrôle est désactivé.|  
|Valide|ValidationStates|Le contrôle utilise la <xref:System.Windows.Controls.Validation> classe et la <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété jointe `false`est.|  
|InvalidFocused|ValidationStates|La <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété jointe `true` est et le contrôle a le focus.|  
|InvalidUnfocused|ValidationStates|La <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété jointe `true` est et le contrôle n’a pas le focus.|  
  
## <a name="scrollbar-controltemplate-example"></a>ScrollBar ControlTemplate, exemple  
 L’exemple suivant montre comment définir un <xref:System.Windows.Controls.ControlTemplate> pour le <xref:System.Windows.Controls.Primitives.ScrollBar> contrôle.  
  
 [!code-xaml[ControlTemplateExamples#ScrollBar](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/scrollbar.xaml#scrollbar)]  
  
 L’exemple précédent utilise une ou plusieurs des ressources suivantes.  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 Pour voir l’exemple complet, consultez [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating) (Exemple de style avec ControlTemplates).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [Styles et modèles Control](control-styles-and-templates.md)
- [Personnalisation des contrôles](control-customization.md)
- [Application d’un style et création de modèles](styling-and-templating.md)
- [Personnalisation de l’apparence d’un contrôle existant en créant un ControlTemplate](customizing-the-appearance-of-an-existing-control.md)
