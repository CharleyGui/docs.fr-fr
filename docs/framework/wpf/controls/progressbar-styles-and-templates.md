---
title: Styles et modèles ProgressBar
ms.date: 03/30/2017
helpviewer_keywords:
- parts [WPF], ProgressBar
- ProgressBar [WPF], styles and templates
- styles [WPF], ProgressBar
- ControlTemplate [WPF], ProgressBar
- templates [WPF], ProgressBar
- states [WPF], ProgressBar
ms.assetid: 935aa600-16e6-4947-a905-37a189a583dd
ms.openlocfilehash: 3a1bea39ba9b6d2cff9937a3fee1d1de41daf16b
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459874"
---
# <a name="progressbar-styles-and-templates"></a>Styles et modèles ProgressBar
Cette rubrique décrit les styles et les modèles du contrôle <xref:System.Windows.Controls.ProgressBar>. Vous pouvez modifier le <xref:System.Windows.Controls.ControlTemplate> par défaut pour attribuer une apparence unique au contrôle. Pour plus d’informations, consultez [Personnalisation de l'apparence d'un contrôle existant en créant un ControlTemplate](customizing-the-appearance-of-an-existing-control.md).  
  
## <a name="progressbar-parts"></a>Composants ProgressBar  
 Le tableau suivant répertorie les parties nommées du contrôle <xref:System.Windows.Controls.ProgressBar>.  
  
|Élément|Tapez|Description|  
|-|-|-|  
|PART_Indicator|<xref:System.Windows.FrameworkElement>|Objet qui indique la progression.|  
|PART_Track|<xref:System.Windows.FrameworkElement>|Objet qui définit le chemin d’accès de l’indicateur de progression.|  
|PART_GlowRect|<xref:System.Windows.FrameworkElement>|Objet qui embellit la barre de progression.|  
  
## <a name="progressbar-states"></a>États de ProgressBar  
 Le tableau suivant répertorie les États visuels du contrôle <xref:System.Windows.Controls.ProgressBar>.  
  
|Nom VisualState|Nom VisualStateGroup|Description|  
|----------------------|---------------------------|-----------------|  
|Déterminée|CommonStates|<xref:System.Windows.Controls.ProgressBar> signale la progression en fonction de la propriété <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A>.|  
|Déterminée|CommonStates|<xref:System.Windows.Controls.ProgressBar> signale la progression générique avec un modèle répétitif.|  
|Valide|ValidationStates|Le contrôle utilise la classe <xref:System.Windows.Controls.Validation> et la propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `false`.|  
|InvalidFocused|ValidationStates|La propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `true` a le focus.|  
|InvalidUnfocused|ValidationStates|La propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `true` a le contrôle n’a pas le focus.|  
  
## <a name="progressbar-controltemplate-example"></a>ProgressBar ControlTemplate, exemple  
 L’exemple suivant montre comment définir une <xref:System.Windows.Controls.ControlTemplate> pour le contrôle <xref:System.Windows.Controls.ProgressBar>.  
  
 [!code-xaml[ControlTemplateExamples#ProgressBar](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/progressbar.xaml#progressbar)]  
  
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
