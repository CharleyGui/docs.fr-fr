---
ms.openlocfilehash: 12a26030a9a336d887ae9d53994a9daf13356618
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496201"
---
### <a name="changing-the-isenabled-property-of-the-parent-of-a-textblock-control-affects-any-child-controls"></a>La modification de la propriété IsEnabled du parent d’un contrôle TextBlock affecte tous les contrôles enfants

#### <a name="details"></a>Détails

À compter du.NET Framework 4.6.2, la modification de la propriété <xref:System.Windows.UIElement.IsEnabled?displayProperty=fullName> du parent d’un contrôle <xref:System.Windows.Controls.TextBlock?displayProperty=fullName> affecte tous les contrôles enfants (comme les liens hypertexte et les boutons) du contrôle <xref:System.Windows.Controls.TextBlock?displayProperty=fullName>. Dans le .NET Framework 4.6.1 et antérieur, les contrôles à l’intérieur d’une <xref:System.Windows.Controls.TextBlock?displayProperty=fullName> ne reflétaient pas toujours l’état de la propriété <xref:System.Windows.UIElement.IsEnabled?displayProperty=fullName> du parent de <xref:System.Windows.Controls.TextBlock?displayProperty=fullName>.

#### <a name="suggestion"></a>Suggestion

Aucun. Cette modification est conforme au comportement attendu pour les contrôles à l’intérieur d’un contrôle <xref:System.Windows.Controls.TextBlock?displayProperty=fullName>.

| Name    | Valeur       |
|:--------|:------------|
| Étendue   |Secondaire|
|Version|4.6.2|
|Type|Runtime|

#### <a name="affected-apis"></a>API affectées

- <xref:System.Windows.UIElement.IsEnabled?displayProperty=nameWithType>

<!--

#### Affected APIs

- `P:System.Windows.UIElement.IsEnabled`

-->
