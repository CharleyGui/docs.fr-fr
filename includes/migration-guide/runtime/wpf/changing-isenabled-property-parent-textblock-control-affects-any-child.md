---
ms.openlocfilehash: 735278848cb7399e414a128afc650a0a1f882337
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67857552"
---
### <a name="changing-the-isenabled-property-of-the-parent-of-a-textblock-control-affects-any-child-controls"></a>La modification de la propriété IsEnabled du parent d’un contrôle TextBlock affecte tous les contrôles enfants

|   |   |
|---|---|
|Détails|À compter du.NET Framework 4.6.2, la modification de la propriété <xref:System.Windows.UIElement.IsEnabled?displayProperty=name> du parent d’un contrôle <xref:System.Windows.Controls.TextBlock?displayProperty=name> affecte tous les contrôles enfants (comme les liens hypertexte et les boutons) du contrôle <xref:System.Windows.Controls.TextBlock?displayProperty=name>. Dans le .NET Framework 4.6.1 et antérieur, les contrôles à l’intérieur d’une <xref:System.Windows.Controls.TextBlock?displayProperty=name> ne reflétaient pas toujours l’état de la propriété <xref:System.Windows.UIElement.IsEnabled?displayProperty=name> du parent de <xref:System.Windows.Controls.TextBlock?displayProperty=name>.|
|Suggestion|Aucun. Cette modification est conforme au comportement attendu pour les contrôles à l’intérieur d’un contrôle <xref:System.Windows.Controls.TextBlock?displayProperty=name>.|
|Étendue|Secondaire|
|Version|4.6.2|
|Type|Runtime|
|API affectées|<ul><li><xref:System.Windows.UIElement.IsEnabled?displayProperty=nameWithType></li></ul>|
