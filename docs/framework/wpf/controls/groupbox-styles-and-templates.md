---
title: Styles et modèles GroupBox
ms.date: 03/30/2017
helpviewer_keywords:
- ControlTemplate [WPF], GroupBox
- parts [WPF], GroupBox
- GroupBox [WPF], styles and templates
- states [WPF], GroupBox
- styles [WPF], GroupBox
- templates [WPF], GroupBox
ms.assetid: 33df7037-0a1b-476f-b9d0-41566a777699
ms.openlocfilehash: 474cda0abc6a18c015836c749c78f4d33aa5abd8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187479"
---
# <a name="groupbox-styles-and-templates"></a>Styles et modèles GroupBox
<a name="introduction"></a>Ce sujet décrit les styles et <xref:System.Windows.Controls.GroupBox> les modèles pour le contrôle. Vous pouvez modifier <xref:System.Windows.Controls.ControlTemplate> la valeur par défaut pour donner au contrôle une apparence unique. Pour plus d’informations, voir [Créer un modèle pour un contrôle](../../../desktop-wpf/themes/how-to-create-apply-template.md).  
  
<a name="groupbox_parts"></a>
## <a name="groupbox-parts"></a>Pièces GroupBox  
 Le <xref:System.Windows.Controls.GroupBox> contrôle n’a pas de pièces nommées.  
  
<a name="groupbox_states"></a>
## <a name="groupbox-states"></a>États GroupBox  
 Le tableau suivant répertorie les états visuels pour le <xref:System.Windows.Controls.GroupBox> contrôle.  
  
|Nom VisualState|Nom VisualStateGroup|Description|  
|-|-|-|  
|Valide|ValidationStates|Le contrôle <xref:System.Windows.Controls.Validation> utilise la <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> classe `false`et la propriété ci-jointe est .|  
|InvalidFocused|ValidationStates|La <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété `true` ci-jointe est a le contrôle a mise au point.|  
|InvalidUnfocused|ValidationStates|La <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété `true` ci-jointe est a le contrôle n’a pas de mise au point.|  
  
<a name="groupbox_controltemplate_example"></a>
## <a name="groupbox-controltemplate-example"></a>GroupBox ControlTemplate Exemple  
 L’exemple suivant montre <xref:System.Windows.Controls.ControlTemplate> comment <xref:System.Windows.Controls.GroupBox> définir un pour le contrôle.  
  
 [!code-xaml[ControlTemplateExamples#GroupBox](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/groupbox.xaml#groupbox)]  
  
 L’utilisation <xref:System.Windows.Controls.ControlTemplate> d’une ou plusieurs des ressources suivantes.  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 Pour voir l’exemple complet, consultez [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating) (Exemple de style avec ControlTemplates).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [Styles et modèles Control](control-styles-and-templates.md)
- [Personnalisation des contrôles](control-customization.md)
- [Application d’un style et création de modèles](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [Créer un modèle pour un contrôle](../../../desktop-wpf/themes/how-to-create-apply-template.md)
