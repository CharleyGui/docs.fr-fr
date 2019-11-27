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
ms.openlocfilehash: a4c449a561017659db7f54fd3cdb8964742650de
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283675"
---
# <a name="togglebutton-styles-and-templates"></a>Styles et modèles ToggleButton

Cette rubrique décrit les styles et les modèles du contrôle <xref:System.Windows.Controls.Primitives.ToggleButton>. Vous pouvez modifier le <xref:System.Windows.Controls.ControlTemplate> par défaut pour attribuer une apparence unique au contrôle. Pour plus d’informations, consultez [créer un modèle pour un contrôle](../../../desktop-wpf/themes/how-to-create-apply-template.md).

## <a name="togglebutton-parts"></a>Éléments ToggleButton

Le contrôle <xref:System.Windows.Controls.Primitives.ToggleButton> n’a pas de parties nommées.

## <a name="togglebutton-states"></a>États ToggleButton

Le tableau suivant répertorie les États visuels du contrôle <xref:System.Windows.Controls.Primitives.ToggleButton>.

|Nom VisualState|Nom VisualStateGroup|Description|
|-|-|-|
|Normal|CommonStates|État par défaut.|
|MouseOver|CommonStates|Le pointeur de souris est positionné sur le contrôle.|
|Appuyé|CommonStates|Le contrôle est enfoncé.|
|Désactivé|CommonStates|Le contrôle est désactivé.|
|Avec focus|FocusStates|Le contrôle a le focus.|
|Sans focus|FocusStates|Le contrôle n’a pas le focus.|
|Activé|CheckStates|<xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> est `true`.|
|Désactivée|CheckStates|<xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> est `false`.|
|Déterminée|CheckStates|<xref:System.Windows.Controls.Primitives.ToggleButton.IsThreeState%2A> est `true`et <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> est `null`.|
|Valide|ValidationStates|Le contrôle utilise la classe <xref:System.Windows.Controls.Validation> et la propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `false`.|
|InvalidFocused|ValidationStates|La propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `true` a le focus.|
|InvalidUnfocused|ValidationStates|La propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `true` a le contrôle n’a pas le focus.|

> [!NOTE]
> Si l’état visuel indéterminé n’existe pas dans votre modèle de contrôle, l’état visuel non vérifié sera utilisé comme état visuel par défaut.

## <a name="togglebutton-controltemplate-example"></a>Exemple de ControlTemplate ToggleButton

L’exemple suivant montre comment définir une <xref:System.Windows.Controls.ControlTemplate> pour le contrôle <xref:System.Windows.Controls.Primitives.ToggleButton>.

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
