---
ms.openlocfilehash: 395463225e3c1f1d168dd019ea75966ad54e5a8a
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621110"
---
### <a name="changing-the-isenabled-property-of-the-parent-of-a-textblock-control-affects-any-child-controls"></a>La modification de la propriété IsEnabled du parent d’un contrôle TextBlock affecte tous les contrôles enfants

#### <a name="details"></a>Détails

À compter du.NET Framework 4.6.2, la modification de la propriété <xref:System.Windows.UIElement.IsEnabled?displayProperty=fullName> du parent d’un contrôle <xref:System.Windows.Controls.TextBlock?displayProperty=fullName> affecte tous les contrôles enfants (comme les liens hypertexte et les boutons) du contrôle <xref:System.Windows.Controls.TextBlock?displayProperty=fullName>. Dans le .NET Framework 4.6.1 et antérieur, les contrôles à l’intérieur d’une <xref:System.Windows.Controls.TextBlock?displayProperty=fullName> ne reflétaient pas toujours l’état de la propriété <xref:System.Windows.UIElement.IsEnabled?displayProperty=fullName> du parent de <xref:System.Windows.Controls.TextBlock?displayProperty=fullName>.

#### <a name="suggestion"></a>Suggestion

Aucun. Cette modification est conforme au comportement attendu pour les contrôles à l’intérieur d’un contrôle <xref:System.Windows.Controls.TextBlock?displayProperty=fullName>.

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   |Secondaire|
|Version|4.6.2|
|Type|Runtime

#### <a name="affected-apis"></a>API affectées

-<xref:System.Windows.UIElement.IsEnabled?displayProperty=nameWithType></li></ul>|
