---
ms.openlocfilehash: 9d960774161fc44810f90ca30f56eb98f98de3ff
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497595"
---
### <a name="wpf-textbox-defaults-to-undo-limit-of-100"></a>Le nombre maximal d’annulations d’opérations pour une zone de texte WPF est de 100 par défaut

#### <a name="details"></a>Détails

Dans .NET Framework 4.5, le nombre maximal d’annulations d’opérations pour une zone de texte WPF est de 100 par défaut (dans .NET Framework 4.0, ce nombre était illimité).

#### <a name="suggestion"></a>Suggestion

Si ce nombre n’est pas suffisant, vous pouvez définir explicitement cette valeur avec <xref:System.Windows.Controls.Primitives.TextBoxBase.UndoLimit>

| Name    | Valeur       |
|:--------|:------------|
| Étendue   |Edge|
|Version|4,5|
|Type|Runtime|

#### <a name="affected-apis"></a>API affectées

- <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType>

<!--

#### Affected APIs

- `T:System.Windows.Controls.TextBox`

-->
