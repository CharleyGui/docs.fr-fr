---
title: Styles et modèles ToggleButton
ms.date: 03/30/2017
helpviewer_keywords:
- states [WPF], ToggleButton
- ToggleButton [WPF], styles and templates
- ControlTemplate [WPF], ToggleButton
- styles [WPF], ToggleButton
- templates [WPF], ToggleButton
- parts [WPF], ToggleButton
ms.assetid: 54f23f30-4bcb-4f09-8ce4-376a13a255a1
ms.openlocfilehash: e055dcbd557f9b90eb2fe99ad15a05b6f229fd28
ms.sourcegitcommit: f87ad41b8e62622da126aa928f7640108c4eff98
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/07/2020
ms.locfileid: "80805909"
---
# <a name="togglebutton-styles-and-templates"></a>Styles et modèles ToggleButton

Ce sujet décrit les styles et <xref:System.Windows.Controls.Primitives.ToggleButton> les modèles pour le contrôle. Vous pouvez modifier <xref:System.Windows.Controls.ControlTemplate> la valeur par défaut pour donner au contrôle une apparence unique. Pour plus d’informations, voir [Créer un modèle pour un contrôle](../../../desktop-wpf/themes/how-to-create-apply-template.md).

## <a name="togglebutton-parts"></a>Pièces ToggleButton

Le <xref:System.Windows.Controls.Primitives.ToggleButton> contrôle n’a pas de pièces nommées.

## <a name="togglebutton-states"></a>ToggleButton États

Le tableau suivant répertorie les états visuels pour le <xref:System.Windows.Controls.Primitives.ToggleButton> contrôle.

|Nom VisualState|Nom VisualStateGroup|Description|
|-|-|-|
|Normal|CommonStates|État par défaut.|
|MouseOver|CommonStates|Le pointeur de souris est positionné sur le contrôle.|
|Appuyé|CommonStates|Le contrôle est enfoncé.|
|Désactivé|CommonStates|Le contrôle est désactivé.|
|Avec focus|FocusStates|Le contrôle a le focus.|
|Sans focus|FocusStates|Le contrôle n’a pas le focus.|
|Activé|CheckStates (en)|<xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> a la valeur `true`.|
|Désactivé|CheckStates (en)|<xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> a la valeur `false`.|
|Indéterminé|CheckStates (en)|<xref:System.Windows.Controls.Primitives.ToggleButton.IsThreeState%2A> a la valeur `true` et <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> a la valeur `null`.|
|Valide|ValidationStates|Le contrôle <xref:System.Windows.Controls.Validation> utilise la <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> classe `false`et la propriété ci-jointe est .|
|InvalidFocused|ValidationStates|La <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété `true` ci-jointe est et le contrôle a mise au point.|
|InvalidUnfocused|ValidationStates|La <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété `true` ci-jointe est et le contrôle n’a pas de mise au point.|

> [!NOTE]
> Si l’état visuel indéterminé n’existe pas dans votre modèle de contrôle, alors l’état visuel non contrôlé sera utilisé comme état visuel par défaut.

## <a name="togglebutton-controltemplate-example"></a>ToggleButton ControlTemplate Exemple

L’exemple suivant montre <xref:System.Windows.Controls.ControlTemplate> comment <xref:System.Windows.Controls.Primitives.ToggleButton> définir un pour le contrôle.

[!code-xaml[ControlTemplateExamples#ToggleButton](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/combobox.xaml#togglebutton)]

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
