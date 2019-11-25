---
title: Styles et modèles PasswordBox
ms.date: 03/30/2017
helpviewer_keywords:
- styles [WPF], PasswordBox
- templates [WPF], PasswordBox
- ControlTemplate [WPF], PasswordBox
- states [WPF], PasswordBox
- PasswordBox [WPF], styles and templates
- parts [WPF], PasswordBox
ms.assetid: deb52107-959f-4a60-b303-d21a0a933060
ms.openlocfilehash: 4ba90182468466773644c7375059f0cc01675b33
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283464"
---
# <a name="passwordbox-styles-and-templates"></a>Styles et modèles PasswordBox

Cette rubrique décrit les styles et les modèles du contrôle <xref:System.Windows.Controls.PasswordBox>. Vous pouvez modifier le <xref:System.Windows.Controls.ControlTemplate> par défaut pour attribuer une apparence unique au contrôle. Pour plus d’informations, consultez [créer un modèle pour un contrôle](../../../desktop-wpf/themes/how-to-create-apply-template.md).

## <a name="passwordbox-parts"></a>Parties de PasswordBox

Le tableau suivant répertorie les parties nommées du contrôle <xref:System.Windows.Controls.PasswordBox>.

|Élément|Type|Description|
|-|-|-|
|PART_ContentHost|<xref:System.Windows.FrameworkElement>|Élément visuel qui peut contenir un <xref:System.Windows.FrameworkElement>. Le texte de la <xref:System.Windows.Controls.PasswordBox> s’affiche dans cet élément.|

## <a name="passwordbox-states"></a>États de PasswordBox

Le tableau suivant répertorie les États visuels du contrôle <xref:System.Windows.Controls.PasswordBox>.

|Nom VisualState|Nom VisualStateGroup|Description|
|-|-|-|
|Normale|CommonStates|État par défaut.|
|MouseOver|CommonStates|Le pointeur de souris est positionné sur le contrôle.|
|Désactivé|CommonStates|Le contrôle est désactivé.|
|Avec focus|FocusStates|Le contrôle a le focus.|
|Sans focus|FocusStates|Le contrôle n’a pas le focus.|
|Valide|ValidationStates|Le contrôle utilise la classe <xref:System.Windows.Controls.Validation> et la propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `false`.|
|InvalidFocused|ValidationStates|La propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `true` a le focus.|
|InvalidUnfocused|ValidationStates|La propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `true` a le contrôle n’a pas le focus.|

## <a name="passwordbox-controltemplate-example"></a>Exemple de ControlTemplate de PasswordBox

L’exemple suivant montre comment définir une <xref:System.Windows.Controls.ControlTemplate> pour le contrôle <xref:System.Windows.Controls.PasswordBox>.

[!code-xaml[ControlTemplateExamples#PasswordBox](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/textbox.xaml#passwordbox)]

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
