---
ms.openlocfilehash: d0de1a262d57c67dd4dfb258d5ac013af5d8783d
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617229"
---
### <a name="wpf-textboxtext-can-be-out-of-sync-with-databinding"></a>Dans WPF, TextBox.Text et la liaison de données peuvent être désynchronisés

#### <a name="details"></a>Détails

Dans certains cas, la propriété <xref:System.Windows.Controls.TextBox.Text> reflète une valeur précédente de la propriété liée aux données si cette propriété est modifiée au cours d'une opération d'écriture de liaison de données.

#### <a name="suggestion"></a>Suggestion

Cela ne doit pas avoir d'impact négatif. Vous pouvez, cependant, restaurer le comportement précédent en affectant à la propriété <xref:System.Windows.FrameworkCompatibilityPreferences.KeepTextBoxDisplaySynchronizedWithTextProperty> la valeur `false`.

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   | Edge        |
| Version | 4,5         |
|Type|Reciblage

#### <a name="affected-apis"></a>API affectées

- <xref:System.Windows.Controls.TextBox.Text?displayProperty=nameWithType>
