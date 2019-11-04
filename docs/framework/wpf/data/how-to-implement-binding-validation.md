---
title: 'Comment : implémenter la validation de la liaison'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- validation of binding [WPF]
- data binding [WPF], validation of binding
- binding [WPF], validation of
ms.assetid: eb98b33d-9866-49ae-b981-bc5ff20d607a
ms.openlocfilehash: 245b05d9cfa7ca66dec310bd9a5291def0101d19
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459107"
---
# <a name="how-to-implement-binding-validation"></a>Comment : implémenter la validation de la liaison

Cet exemple montre comment utiliser un <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> et un déclencheur de style pour fournir des commentaires visuels afin d’informer l’utilisateur lorsqu’une valeur non valide est entrée, en fonction d’une règle de validation personnalisée.

## <a name="example"></a>Exemple

Le contenu de texte de l' <xref:System.Windows.Controls.TextBox> dans l’exemple suivant est lié à la propriété `Age` (de type int) d’un objet de source de liaison nommé `ods`. La liaison est configurée pour utiliser une règle de validation nommée `AgeRangeRule` afin que si l’utilisateur entre des caractères non numériques ou une valeur inférieure à 21 ou supérieure à 130, un point d’exclamation rouge apparaisse en regard de la zone de texte et une info-bulle contenant le message d’erreur s’affiche lorsque l’utilisateur déplace la souris sur la zone de texte.

[!code-xaml[BindValidation#2](~/samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml#2)]

L’exemple suivant illustre l’implémentation de `AgeRangeRule`, qui hérite de <xref:System.Windows.Controls.ValidationRule> et substitue la méthode <xref:System.Windows.Controls.ValidationRule.Validate%2A>. La méthode `Int32.Parse` est appelée sur la valeur pour s’assurer qu’elle ne contient pas de caractères non valides. La méthode <xref:System.Windows.Controls.ValidationRule.Validate%2A> retourne une <xref:System.Windows.Controls.ValidationResult> qui indique si la valeur est valide selon qu’une exception est interceptée pendant l’analyse et si la valeur d’âge est en dehors des limites inférieure et supérieure.

[!code-csharp[BindValidation#3](~/samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/AgeRangeRule.cs#3)]
[!code-vb[BindValidation#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BindValidation/VisualBasic/AgeRangeRule.vb#3)]

L’exemple suivant montre le `validationTemplate` <xref:System.Windows.Controls.ControlTemplate> personnalisé qui crée un point d’exclamation rouge pour notifier l’utilisateur d’une erreur de validation. Les modèles de contrôle sont utilisés pour redéfinir l’apparence d’un contrôle.

[!code-xaml[BindValidation#4](~/samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml#4)]

Comme indiqué dans l’exemple suivant, la <xref:System.Windows.Controls.ToolTip> qui affiche le message d’erreur est créée à l’aide du style nommé `textBoxInError`. Si la valeur de <xref:System.Windows.Controls.Validation.HasError%2A> est `true`, le déclencheur affecte à l’info-bulle de la <xref:System.Windows.Controls.TextBox> actuelle la première erreur de validation. La <xref:System.Windows.Data.Binding.RelativeSource%2A> est définie sur <xref:System.Windows.Data.RelativeSourceMode.Self>, en faisant référence à l’élément actuel.

[!code-xaml[BindValidation#5](~/samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml#5)]

Pour obtenir un exemple complet, consultez [exemple de validation de liaison](https://github.com/Microsoft/WPF-Samples/tree/master/Data%20Binding/BindValidation).
  
Notez que si vous ne fournissez pas de <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> personnalisé, le modèle d’erreur par défaut apparaît pour fournir des commentaires visuels à l’utilisateur en cas d’erreur de validation. Pour plus d’informations, consultez la section relative à la validation de données de la rubrique [Vue d’ensemble de la liaison de données](../../../desktop-wpf/data/data-binding-overview.md). En outre, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fournit une règle de validation intégrée qui capte les exceptions levées pendant la mise à jour de la propriété de source de liaison. Pour plus d'informations, consultez <xref:System.Windows.Controls.ExceptionValidationRule>.

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble de la liaison de données](../../../desktop-wpf/data/data-binding-overview.md)
- [Rubriques de guide pratique](data-binding-how-to-topics.md)
