---
ms.openlocfilehash: 13d3799aeede86b01aa81ce1cd69b3c4c22311ca
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620479"
---
### <a name="wpf-textbox-defaults-to-undo-limit-of-100"></a>Le nombre maximal d’annulations d’opérations pour une zone de texte WPF est de 100 par défaut

#### <a name="details"></a>Détails

Dans .NET Framework 4.5, le nombre maximal d’annulations d’opérations pour une zone de texte WPF est de 100 par défaut (dans .NET Framework 4.0, ce nombre était illimité).

#### <a name="suggestion"></a>Suggestion

Si ce nombre n’est pas suffisant, vous pouvez définir explicitement cette valeur avec <xref:System.Windows.Controls.Primitives.TextBoxBase.UndoLimit>

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   |Edge|
|Version|4,5|
|Type|Runtime

#### <a name="affected-apis"></a>API affectées

-<xref:System.Windows.Controls.TextBox?displayProperty=nameWithType></li></ul>|
